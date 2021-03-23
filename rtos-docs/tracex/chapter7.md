---
title: Kapitel 7 – Azure återställnings tider FileX trace Events
description: Det här kapitlet innehåller en beskrivning av Azure återställnings tider FileX-händelser.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: c3cbc945e33b87b6759c56ec1429d6bf57259bd9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827492"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a><span data-ttu-id="f9a9f-103">Kapitel 7 – Azure återställnings tider FileX trace Events</span><span class="sxs-lookup"><span data-stu-id="f9a9f-103">Chapter 7 - Azure RTOS FileX trace events</span></span>

<span data-ttu-id="f9a9f-104">Det här kapitlet innehåller en beskrivning av Azure återställnings tider FileX-händelser.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-104">This chapter contains a description of the Azure RTOS FileX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="f9a9f-105">Lista över händelser och ikoner</span><span class="sxs-lookup"><span data-stu-id="f9a9f-105">List of Events and Icons</span></span>

<span data-ttu-id="f9a9f-106">**Följande är en lista över FileX-händelser som visas av TraceX.**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-106">**The following is a list of FileX events displayed by TraceX.**</span></span>

<span data-ttu-id="f9a9f-107">Följande beskriver varje händelse:</span><span class="sxs-lookup"><span data-stu-id="f9a9f-107">The following describes each event:</span></span>

| <span data-ttu-id="f9a9f-108">**Ikon**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-108">**Icon**</span></span>                         | <span data-ttu-id="f9a9f-109">**Innebörd**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-109">**Meaning**</span></span>                               |
| -------------------------------- | ----------------------------------------- |
| ![Intern logisk sektor cache missar ikon](./media/user-guide/fx-events/image1.png)    | <span data-ttu-id="f9a9f-111">Intern logisk sektor cache missar</span><span class="sxs-lookup"><span data-stu-id="f9a9f-111">Internal Logical Sector Cache Miss</span></span> |
| ![Ikon för internt katalog-Cachemissar](./media/user-guide/fx-events/image2.png)    | <span data-ttu-id="f9a9f-113">Intern katalog-Cachemissar</span><span class="sxs-lookup"><span data-stu-id="f9a9f-113">Internal Directory Cache Miss</span></span> |
| ![Ikon för internt medie tömning](./media/user-guide/fx-events/image3.png)    | <span data-ttu-id="f9a9f-115">Intern medie tömning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-115">Internal Media Flush</span></span> |
| ![Läs ikon för intern katalog post](./media/user-guide/fx-events/image4.png)    | <span data-ttu-id="f9a9f-117">Läsning av intern katalog post</span><span class="sxs-lookup"><span data-stu-id="f9a9f-117">Internal Directory Entry Read</span></span> |
| ![Skriv ikon för intern katalog post](./media/user-guide/fx-events/image5.png)    | <span data-ttu-id="f9a9f-119">Skrivning av intern katalog post</span><span class="sxs-lookup"><span data-stu-id="f9a9f-119">Internal Directory Entry Write</span></span> |
| ![Läs ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image6.png)    | <span data-ttu-id="f9a9f-121">Läst intern I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="f9a9f-121">Internal I/O Driver Read</span></span> |
| ![Skriv ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image7.png)    | <span data-ttu-id="f9a9f-123">Intern I/O-drivrutin skrivning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-123">Internal I/O Driver Write</span></span> |
| ![Intern I/O-drivrutin för driv Rutins tömning](./media/user-guide/fx-events/image8.png)    | <span data-ttu-id="f9a9f-125">Intern I/O-drivrutins tömning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-125">Internal I/O Driver Flush</span></span> |
| ![Avbrotts ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image9.png)    | <span data-ttu-id="f9a9f-127">Intern I/O-drivrutin avbryts</span><span class="sxs-lookup"><span data-stu-id="f9a9f-127">Internal I/O Driver Abort</span></span> |
| ![Initiera ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image10.png)    | <span data-ttu-id="f9a9f-129">Intern I/O-drivrutin initieras</span><span class="sxs-lookup"><span data-stu-id="f9a9f-129">Internal I/O Driver Initialize</span></span> |
| ![Intern I/O driv rutin start Läs ikon](./media/user-guide/fx-events/image11.png)    | <span data-ttu-id="f9a9f-131">Start läsning av intern I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="f9a9f-131">Internal I/O Driver Boot Read</span></span> |
| ![Intern I/O driv Rutins ikon för versions sektorer](./media/user-guide/fx-events/image12.png)    | <span data-ttu-id="f9a9f-133">Interna I/O driv Rutins versions sektorer</span><span class="sxs-lookup"><span data-stu-id="f9a9f-133">Internal I/O Driver Release Sectors</span></span> |
| ![Start Skriv ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image13.png)    | <span data-ttu-id="f9a9f-135">Intern I/O driv Rutins Start Skriv</span><span class="sxs-lookup"><span data-stu-id="f9a9f-135">Internal I/O Driver Boot Write</span></span> |
| ![Intern I/O driv rutin driv rutin driv rutin avinitiera ikon](./media/user-guide/fx-events/image14.png)    | <span data-ttu-id="f9a9f-137">Intern I/O driv rutin driv rutin avinitieras</span><span class="sxs-lookup"><span data-stu-id="f9a9f-137">Internal I / O Driver Driver Un-initialize</span></span> |
| ![Läs ikon för katalogattribut](./media/user-guide/fx-events/image15.png)    | <span data-ttu-id="f9a9f-139">**Lästa katalogattribut** (*fx_directory_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-139">**Directory Attributes Read** (*fx_directory_attributes_read*)</span></span> |
| ![Ikon för ange katalogattribut](./media/user-guide/fx-events/image16.png)    | <span data-ttu-id="f9a9f-141">**Katalog-attribut har angetts** (*fx_directory_attributes_set*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-141">**Directory Attributes Set** (*fx_directory_attributes_set*)</span></span> |
| ![Ikon för att skapa katalog](./media/user-guide/fx-events/image17.png)    | <span data-ttu-id="f9a9f-143">**Skapa katalog** (*fx_directory_create*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-143">**Directory Create** (*fx_directory_create*)</span></span> |
| ![Hämta ikon för katalog standard](./media/user-guide/fx-events/image18.png)    | <span data-ttu-id="f9a9f-145">**Hämta katalog standard** (*fx_directory_default_get*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-145">**Directory Default Get** (*fx_directory_default_get*)</span></span> |
| ![Ikon för katalog standard uppsättning](./media/user-guide/fx-events/image19.png)    | <span data-ttu-id="f9a9f-147">**Katalog standard uppsättning** (*fx_directory_default_set*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-147">**Directory Default Set** (*fx_directory_default_set*)</span></span> |
| ![Ikonen Ta bort katalog](./media/user-guide/fx-events/image20.png)    | <span data-ttu-id="f9a9f-149">**Ta bort katalog** (*fx_directory_delete*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-149">**Directory Delete** (*fx_directory_delete*)</span></span> |
| ![Hitta ikon för första katalog posten](./media/user-guide/fx-events/image21.png)    | <span data-ttu-id="f9a9f-151">**Sök efter katalog första posten** (*fx_directory_first_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-151">**Directory First Entry Find** (*fx_directory_first_entry_find*)</span></span> |
| ![Hitta ikon för första katalog start posten](./media/user-guide/fx-events/image22.png)    | <span data-ttu-id="f9a9f-153">**Katalog-första fullständiga post Sök** (*fx_directory_first_full_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-153">**Directory First Full Entry Find** (*fx_directory_first_full_entry_find*)</span></span> |
| ![Ikon för Hämta katalog information](./media/user-guide/fx-events/image23.png)    | <span data-ttu-id="f9a9f-155">**Hämta katalog information** (*fx_directory_information_get*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-155">**Directory Information Get** (*fx_directory_information_get*)</span></span> |
| ![Ikon för lokal sökväg för katalog](./media/user-guide/fx-events/image24.png)    | <span data-ttu-id="f9a9f-157">**Rensa katalogens lokala sökväg** (*fx_directory_local_path_clear*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-157">**Directory Local Path Clear** (*fx_directory_local_path_clear*)</span></span> |
| ![Hämta ikon för lokal sökväg för katalog](./media/user-guide/fx-events/image25.png)    | <span data-ttu-id="f9a9f-159">**Lokal sökväg för katalog hämtning** (*fx_directory_local_path_get*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-159">**Directory Local Path Get** (*fx_directory_local_path_get*)</span></span> |
| ![Ikon för återställning av lokal sökväg för katalog](./media/user-guide/fx-events/image26.png)    | <span data-ttu-id="f9a9f-161">**Återställning av lokal sökväg för katalog** (*fx_directory_local_path_restore*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-161">**Directory Local Path Restore** (*fx_directory_local_path_restore*)</span></span> |
| ![Ikon för lokal sökväg för katalog](./media/user-guide/fx-events/image27.png)    | <span data-ttu-id="f9a9f-163">**Lokal sökväg till katalog** (*fx_directory_local_path_set*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-163">**Directory Local Path Set** (*fx_directory_local_path_set*)</span></span> |
| ![Hämta ikon för katalogens långa namn](./media/user-guide/fx-events/image28.png)    | <span data-ttu-id="f9a9f-165">**Katalogens långa namn get** (*fx_directory_long_name_get*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-165">**Directory Long Name Get** (*fx_directory_long_name_get*)</span></span> |
| ![Ikon för katalog namns test](./media/user-guide/fx-events/image29.png)    | <span data-ttu-id="f9a9f-167">**Katalog namns test** (*fx_directory_name_test*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-167">**Directory Name Test** (*fx_directory_name_test*)</span></span> |
| ![Sök ikon för katalog nästa post](./media/user-guide/fx-events/image30.png)    | <span data-ttu-id="f9a9f-169">**Sök i katalog nästa post** (*fx_directory_next_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-169">**Directory Next Entry Find** (*fx_directory_next_entry_find*)</span></span> |
| ![Sök ikon för nästa fullständiga post-katalog](./media/user-guide/fx-events/image31.png)    | <span data-ttu-id="f9a9f-171">**Sök i katalog nästa fullständiga post** (*fx_directory_next_full_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-171">**Directory Next Full Entry Find** (*fx_directory_next_full_entry_find*)</span></span> |
| ![Ikon för katalog namn](./media/user-guide/fx-events/image32.png)    | <span data-ttu-id="f9a9f-173">**Byt namn på katalog** (*fx_directory_rename*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-173">**Directory Rename** (*fx_directory_rename*)</span></span> |
| ![Katalog kort namn Hämta ikon](./media/user-guide/fx-events/image33.png)    | <span data-ttu-id="f9a9f-175">**Katalog kort namn Hämta** (*fx_directory_short_name_get*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-175">**Directory Short Name Get** (*fx_directory_short_name_get*)</span></span> |
| ![Fil tilldelnings ikon](./media/user-guide/fx-events/image34.png)    | <span data-ttu-id="f9a9f-177">**Fil tilldelning** (*fx_file_allocate*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-177">**File Allocate** (*fx_file_allocate*)</span></span> |
| ![Läs ikon för filattribut](./media/user-guide/fx-events/image35.png)    | <span data-ttu-id="f9a9f-179">**Lästa filattribut** (*fx_file_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-179">**File Attributes Read** (*fx_file_attributes_read*)</span></span> |
| ![Ikonen filattribut ange](./media/user-guide/fx-events/image36.png)    | <span data-ttu-id="f9a9f-181">**Angett filattribut** (*fx_file_attributes_set*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-181">**File Attributes Set** (*fx_file_attributes_set*)</span></span> |
| ![Ikon för att allokera bästa ansträngning](./media/user-guide/fx-events/image37.png)    | <span data-ttu-id="f9a9f-183">**Bästa fördelar för fil** (*fx_file_best_effort_allocate*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-183">**File Best Effort Allocate** (*fx_file_best_effort_allocate*)</span></span> |
| ![Fil stängnings ikon](./media/user-guide/fx-events/image38.png)    | <span data-ttu-id="f9a9f-185">**Stäng fil** (*fx_file_close*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-185">**File Close** (*fx_file_close*)</span></span> |
| ![Ikon för fil skapande](./media/user-guide/fx-events/image39.png)    | <span data-ttu-id="f9a9f-187">**Skapa fil** (*fx_file_create*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-187">**File Create** (*fx_file_create*)</span></span> |
| ![Ikon för datum/tid för fil uppsättning](./media/user-guide/fx-events/image40.png)    | <span data-ttu-id="f9a9f-189">**Datum tid för filen** (*fx_file_date_time_set*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-189">**File Date Time Set** (*fx_file_date_time_set*)</span></span> |
| ![Fil borttagnings ikon](./media/user-guide/fx-events/image41.png)    | <span data-ttu-id="f9a9f-191">**Ta bort fil** (*fx_file_delete*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-191">**File Delete** (*fx_file_delete*)</span></span> |
| ![Fil öppnings ikon](./media/user-guide/fx-events/image42.png)    | <span data-ttu-id="f9a9f-193">**Öppna fil** (*fx_file_open*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-193">**File Open** (*fx_file_open*)</span></span> |
| ![Fil läsnings ikon](./media/user-guide/fx-events/image43.png)    | <span data-ttu-id="f9a9f-195">**Fil läsning** (*fx_file_read*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-195">**File Read** (*fx_file_read*)</span></span> |
| ![Ikon för fil relativ sökning](./media/user-guide/fx-events/image44.png)    | <span data-ttu-id="f9a9f-197">**Relativ sökning av filer** (*fx_file_relative_seek*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-197">**File Relative Seek** (*fx_file_relative_seek*)</span></span> |
| ![Ikon för fil namn](./media/user-guide/fx-events/image45.png)    | <span data-ttu-id="f9a9f-199">**Byt namn på fil** (*fx_file_rename*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-199">**File Rename** (*fx_file_rename*)</span></span> |
| ![Fil Sök ikon](./media/user-guide/fx-events/image46.png)    | <span data-ttu-id="f9a9f-201">**Fil sökning** (*fx_file_seek*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-201">**File Seek** (*fx_file_seek*)</span></span> |
| ![Ikon för fil trunkering](./media/user-guide/fx-events/image47.png)    | <span data-ttu-id="f9a9f-203">**Filen trunkeras** (*fx_file_truncate*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-203">**File Truncate** (*fx_file_truncate*)</span></span> |
| ![Ikonen för att trunkera en fil](./media/user-guide/fx-events/image48.png)    | <span data-ttu-id="f9a9f-205">**Fil trunkerad version** (*fx_file_truncate_release*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-205">**File Truncate Release** (*fx_file_truncate_release*)</span></span> |
| ![Fil skrivnings ikon](./media/user-guide/fx-events/image49.png)    | <span data-ttu-id="f9a9f-207">**Fil skrivning** (*fx_file_write*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-207">**File Write** (*fx_file_write*)</span></span> |
| ![Ikon för medie avbrott](./media/user-guide/fx-events/image50.png)    | <span data-ttu-id="f9a9f-209">**Medie avbrott** (*fx_media_abort*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-209">**Media Abort** (*fx_media_abort*)</span></span> |
| ![Ikon för att verifiera medie cache](./media/user-guide/fx-events/image51.png)    | <span data-ttu-id="f9a9f-211">**Ogiltig cachelagring av media** (*fx_media_cache_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-211">**Media Cache Invalidate** (*fx_media_cache_invalidate*)</span></span> |
| ![Ikon för medie kontroll](./media/user-guide/fx-events/image52.png)    | <span data-ttu-id="f9a9f-213">**Medie kontroll** (*fx_media_check*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-213">**Media Check** (*fx_media_check*)</span></span> |
| ![\* Ikon för medie stängning](./media/user-guide/fx-events/image53.png)    | <span data-ttu-id="f9a9f-215">**Medie stängning** (*fx_media_close*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-215">**Media Close** (*fx_media_close*)</span></span> |
| ![Ikon för medie tömning](./media/user-guide/fx-events/image54.png)    | <span data-ttu-id="f9a9f-217">**Medie tömning** (*fx_media_flush*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-217">**Media Flush** (*fx_media_flush*)</span></span> |
| ![Ikon för medie format](./media/user-guide/fx-events/image55.png)    | <span data-ttu-id="f9a9f-219">**Medie format** (*fx_media_format*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-219">**Media Format** (*fx_media_format*)</span></span> |
| ![Medie öppnings ikon](./media/user-guide/fx-events/image56.png)    | <span data-ttu-id="f9a9f-221">**Öppna Media** (*fx_media_open*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-221">**Media Open** (*fx_media_open*)</span></span> |
| ![Medie läsnings ikon](./media/user-guide/fx-events/image57.png)    | <span data-ttu-id="f9a9f-223">**Läsning av media** (*fx_media_read*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-223">**Media Read** (*fx_media_read*)</span></span> |
| ![Ikon för tillgängligt medie utrymme](./media/user-guide/fx-events/image58.png)    | <span data-ttu-id="f9a9f-225">**Tillgängligt medie utrymme** (*fx_media_space_available*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-225">**Media Space Available** (*fx_media_space_available*)</span></span> |
| ![Ikon för Hämta medie volym](./media/user-guide/fx-events/image59.png)    | <span data-ttu-id="f9a9f-227">**Hämta medie volym** (*fx_media_volume_get*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-227">**Media Volume Get** (*fx_media_volume_get*)</span></span> |
| ![Ikon för medie volym uppsättning](./media/user-guide/fx-events/image60.png)    | <span data-ttu-id="f9a9f-229">**Medie volym uppsättning** (*fx_media_volume_set*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-229">**Media Volume Set** (*fx_media_volume_set*)</span></span> |
| ![Ikon för medie skrivning](./media/user-guide/fx-events/image61.png)    | <span data-ttu-id="f9a9f-231">**Medie skrivning** (*fx_media_write*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-231">**Media Write** (*fx_media_write*)</span></span> |
| ![Ikonen system datum get](./media/user-guide/fx-events/image62.png)    | <span data-ttu-id="f9a9f-233">**System datum get** (*fx_system_date_get*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-233">**System Date Get** (*fx_system_date_get*)</span></span> |
| ![Ikon för system datum uppsättning](./media/user-guide/fx-events/image63.png)    | <span data-ttu-id="f9a9f-235">**System datum uppsättning** (*fx_system_date_set*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-235">**System Date Set** (*fx_system_date_set*)</span></span> |
| ![Ikon för system initiering](./media/user-guide/fx-events/image64.png)    | <span data-ttu-id="f9a9f-237">**System initiering** (*fx_system_initialize*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-237">**System Initialize** (*fx_system_initialize*)</span></span> |
| ![Ikonen system tid get](./media/user-guide/fx-events/image65.png)    | <span data-ttu-id="f9a9f-239">**System tid get** (*fx_system_time_get*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-239">**System Time Get** (*fx_system_time_get*)</span></span> |
| ![Ikon för system tids uppsättning](./media/user-guide/fx-events/image66.png)    | <span data-ttu-id="f9a9f-241">**System tids uppsättning** (*fx_system_time_set*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-241">**System Time Set** (*fx_system_time_set*)</span></span> |
| ![Ikon för att skapa Unicode-katalogen](./media/user-guide/fx-events/image67.png)    | <span data-ttu-id="f9a9f-243">**Skapa Unicode-katalog** (*fx_unicode_directory_create*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-243">**Unicode Directory Create** (*fx_unicode_directory_create*)</span></span> |
| ![Ikon för byte i Unicode-katalog](./media/user-guide/fx-events/image68.png)    | <span data-ttu-id="f9a9f-245">**Byt namn på Unicode-katalogen** (*fx_unicode_directory_rename*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-245">**Unicode Directory Rename** (*fx_unicode_directory_rename*)</span></span> |
| ![Ikon för att skapa Unicode-fil](./media/user-guide/fx-events/image69.png)    | <span data-ttu-id="f9a9f-247">**Skapa Unicode-fil** (*fx_unicode_file_create*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-247">**Unicode File Create** (*fx_unicode_file_create*)</span></span> |
| ![Ikon för byte av Unicode-fil](./media/user-guide/fx-events/image70.png)    | <span data-ttu-id="f9a9f-249">**Byt namn på Unicode-filen** (*fx_unicode_file_rename*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-249">**Unicode File Rename** (*fx_unicode_file_rename*)</span></span> |
| ![Hämta ikon för Unicode-längden](./media/user-guide/fx-events/image71.png)    | <span data-ttu-id="f9a9f-251">**Unicode-längden get** (*fx_unicode_length_get*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-251">**Unicode Lenght Get** (*fx_unicode_length_get*)</span></span> |
| ![Ikon för att hämta Unicode-namn](./media/user-guide/fx-events/image72.png)    | <span data-ttu-id="f9a9f-253">**Unicode-namn get** (*fx_unicode_name_get*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-253">**Unicode Name Get** (*fx_unicode_name_get*)</span></span> |
| ![Ikon för kort namn för Unicode-namn](./media/user-guide/fx-events/image73.png)    | <span data-ttu-id="f9a9f-255">**Unicode-kort namn Hämta** (*fx_unicode_short_name_get*)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-255">**Unicode Short Name Get** (*fx_unicode_short_name_get*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="f9a9f-256">Händelse beskrivningar</span><span class="sxs-lookup"><span data-stu-id="f9a9f-256">Event Descriptions</span></span>

<span data-ttu-id="f9a9f-257">Följande beskriver varje enskild händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-257">The following describes each individual event.</span></span>

### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="f9a9f-258">Intern logisk sektor cache missar</span><span class="sxs-lookup"><span data-stu-id="f9a9f-258">Internal Logical Sector Cache Miss</span></span> 

#### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="f9a9f-259">Intern logisk sektor cache missar</span><span class="sxs-lookup"><span data-stu-id="f9a9f-259">Internal logical sector cache miss</span></span>

<span data-ttu-id="f9a9f-260">**Ikonen** ![ Intern logisk sektor cache missar ikon](./media/user-guide/fx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-260">**Icon** ![Internal logical sector cache miss icon](./media/user-guide/fx-events/image1.png)</span></span>

<span data-ttu-id="f9a9f-261">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-261">**Description**</span></span>

<span data-ttu-id="f9a9f-262">Den här händelsen representerar en intern FileX-cache för logisk sektor.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-262">This event represents an internal FileX logical sector cache miss.</span></span>

<span data-ttu-id="f9a9f-263">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-263">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-264">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-264">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-265">Info fält 2: sektor.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-265">Info Field 2: Sector.</span></span>
- <span data-ttu-id="f9a9f-266">Info-fält 3: totalt antal Cachemissar.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-266">Info Field 3: Total misses.</span></span>
- <span data-ttu-id="f9a9f-267">Info fält 4: cachestorlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-267">Info Field 4: Cache size.</span></span>

### <a name="internal-directory-cache-miss"></a><span data-ttu-id="f9a9f-268">Intern katalog-Cachemissar</span><span class="sxs-lookup"><span data-stu-id="f9a9f-268">Internal Directory Cache Miss</span></span>

#### <a name="internal-directory-cache-miss"></a><span data-ttu-id="f9a9f-269">Intern katalog-Cachemissar</span><span class="sxs-lookup"><span data-stu-id="f9a9f-269">Internal directory cache miss</span></span>

<span data-ttu-id="f9a9f-270">**Ikonen** ![ Ikon för internt katalog-Cachemissar](./media/user-guide/fx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-270">**Icon** ![Internal directory cache miss icon](./media/user-guide/fx-events/image2.png)</span></span>

<span data-ttu-id="f9a9f-271">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-271">**Description**</span></span> 

<span data-ttu-id="f9a9f-272">Den här händelsen representerar ett internt FileX Directory-Cachemissar.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-272">This event represents an internal FileX directory cache miss.</span></span>

<span data-ttu-id="f9a9f-273">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-273">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-274">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-274">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-275">Info fält 2: totalt antal Cachemissar.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-275">Info Field 2: Total misses.</span></span>
- <span data-ttu-id="f9a9f-276">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-276">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-277">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-277">Info Field 4: Not used.</span></span>

### <a name="internal-media-flush"></a><span data-ttu-id="f9a9f-278">Intern medie tömning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-278">Internal Media Flush</span></span> 

#### <a name="internal-media-flush"></a><span data-ttu-id="f9a9f-279">Intern medie tömning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-279">Internal media flush</span></span>

<span data-ttu-id="f9a9f-280">**Ikonen** ![ Ikon för internt medie tömning](./media/user-guide/fx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-280">**Icon** ![Internal media flush icon](./media/user-guide/fx-events/image3.png)</span></span>

<span data-ttu-id="f9a9f-281">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-281">**Description**</span></span>

<span data-ttu-id="f9a9f-282">Den här händelsen representerar en intern FileX medie tömning.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-282">This event represents an internal FileX media flush.</span></span>

<span data-ttu-id="f9a9f-283">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-283">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-284">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-284">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-285">Informations fält 2: antal skadade sektorer.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-285">Info Field 2: Number of dirty sectors.</span></span>
- <span data-ttu-id="f9a9f-286">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-286">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-287">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-287">Info Field 4: Not used.</span></span>


### <a name="internal-directory-entry-read"></a><span data-ttu-id="f9a9f-288">Läsning av intern katalog post</span><span class="sxs-lookup"><span data-stu-id="f9a9f-288">Internal Directory Entry Read</span></span> 

#### <a name="internal-directory-entry-read"></a><span data-ttu-id="f9a9f-289">Läsning av intern katalog post</span><span class="sxs-lookup"><span data-stu-id="f9a9f-289">Internal directory entry read</span></span>

<span data-ttu-id="f9a9f-290">**Ikonen** ![ Läs ikon för intern katalog post](./media/user-guide/fx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-290">**Icon** ![Internal directory entry read icon](./media/user-guide/fx-events/image4.png)</span></span>

<span data-ttu-id="f9a9f-291">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-291">**Description**</span></span>

<span data-ttu-id="f9a9f-292">Den här händelsen representerar en intern FileX-katalog post-händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-292">This event represents an internal FileX directory entry read event.</span></span>

<span data-ttu-id="f9a9f-293">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-293">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-294">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-294">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-295">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-295">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f9a9f-296">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-296">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-297">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-297">Info Field 4: Not used.</span></span>

### <a name="internal-directory-entry-write"></a><span data-ttu-id="f9a9f-298">Skrivning av intern katalog post</span><span class="sxs-lookup"><span data-stu-id="f9a9f-298">Internal Directory Entry Write</span></span>

#### <a name="internal-directory-entry-write"></a><span data-ttu-id="f9a9f-299">Skrivning av intern katalog post</span><span class="sxs-lookup"><span data-stu-id="f9a9f-299">Internal directory entry write</span></span>

<span data-ttu-id="f9a9f-300">**Ikonen** ![ Skriv ikon för intern katalog post](./media/user-guide/fx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-300">**Icon** ![Internal directory entry write icon](./media/user-guide/fx-events/image5.png)</span></span>

<span data-ttu-id="f9a9f-301">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-301">**Description**</span></span>

<span data-ttu-id="f9a9f-302">Den här händelsen representerar ett internt FileX för katalog poster.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-302">This event represents an internal FileX directory entry write event.</span></span>

<span data-ttu-id="f9a9f-303">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-303">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-304">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-304">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-305">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-305">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f9a9f-306">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-306">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-307">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-307">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-read"></a><span data-ttu-id="f9a9f-308">Läst intern I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="f9a9f-308">Internal I/O Driver Read</span></span> 

#### <a name="internal-io-driver-read"></a><span data-ttu-id="f9a9f-309">Läst intern I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="f9a9f-309">Internal I/O driver read</span></span> 

<span data-ttu-id="f9a9f-310">**Ikonen** ![ Läs ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-310">**Icon** ![Internal I / O driver read icon](./media/user-guide/fx-events/image6.png)</span></span>

<span data-ttu-id="f9a9f-311">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-311">**Description**</span></span> 

<span data-ttu-id="f9a9f-312">Den här händelsen representerar en intern FileX I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-312">This event represents an internal FileX I/O driver read event.</span></span>

<span data-ttu-id="f9a9f-313">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-313">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-314">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-314">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-315">Info fält 2: sektor.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-315">Info Field 2: Sector.</span></span>
- <span data-ttu-id="f9a9f-316">Informations fält 3: antal sektorer.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-316">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="f9a9f-317">Info fält 4: buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-317">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-write"></a><span data-ttu-id="f9a9f-318">Intern I/O-drivrutin skrivning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-318">Internal I/O Driver Write</span></span> 

#### <a name="internal-io-driver-write"></a><span data-ttu-id="f9a9f-319">Intern I/O-drivrutin skrivning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-319">Internal I/O driver write</span></span> 

<span data-ttu-id="f9a9f-320">**Ikonen** ![ Skriv ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-320">**Icon** ![Internal I / O driver write icon](./media/user-guide/fx-events/image7.png)</span></span>

<span data-ttu-id="f9a9f-321">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-321">**Description**</span></span> 

<span data-ttu-id="f9a9f-322">Den här händelsen representerar en intern skrivnings händelse för FileX I/O-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-322">This event represents an internal FileX I/O driver write event.</span></span>

<span data-ttu-id="f9a9f-323">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-323">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-324">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-324">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-325">Info fält 2: sektor.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-325">Info Field 2: Sector.</span></span>
- <span data-ttu-id="f9a9f-326">Informations fält 3: antal sektorer.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-326">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="f9a9f-327">Info fält 4: buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-327">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-flush"></a><span data-ttu-id="f9a9f-328">Intern I/O-drivrutins tömning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-328">Internal I/O Driver Flush</span></span> 

#### <a name="internal-io-driver-flush"></a><span data-ttu-id="f9a9f-329">Intern I/O-drivrutins tömning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-329">Internal I/O driver flush</span></span> 

<span data-ttu-id="f9a9f-330">**Ikonen** ![ Intern I/O-drivrutin för driv rutins tömning](./media/user-guide/fx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-330">**Icon** ![Internal I / O driver flush icon](./media/user-guide/fx-events/image8.png)</span></span>

<span data-ttu-id="f9a9f-331">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-331">**Description**</span></span> 

<span data-ttu-id="f9a9f-332">Den här händelsen representerar en intern händelse av FileX I/O-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-332">This event represents an internal FileX I/O driver flush event.</span></span>

<span data-ttu-id="f9a9f-333">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-333">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-334">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-334">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-335">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-335">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f9a9f-336">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-336">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-337">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-337">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-abort"></a><span data-ttu-id="f9a9f-338">Intern I/O-drivrutin avbryts</span><span class="sxs-lookup"><span data-stu-id="f9a9f-338">Internal I/O Driver Abort</span></span> 

#### <a name="internal-io-dirver-abort"></a><span data-ttu-id="f9a9f-339">Internt I/O-dirver Avbryt</span><span class="sxs-lookup"><span data-stu-id="f9a9f-339">Internal I/O dirver abort</span></span>

<span data-ttu-id="f9a9f-340">**Ikonen** ![ Avbrotts ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-340">**Icon** ![Internal I / O driver abort icon](./media/user-guide/fx-events/image9.png)</span></span>

<span data-ttu-id="f9a9f-341">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-341">**Description**</span></span>

<span data-ttu-id="f9a9f-342">Den här händelsen representerar en intern FileX I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-342">This event represents an internal FileX I/O driver abort event.</span></span>

<span data-ttu-id="f9a9f-343">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-343">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-344">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-344">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-345">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-345">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f9a9f-346">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-346">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-347">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-347">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="f9a9f-348">Intern I/O-drivrutin initieras</span><span class="sxs-lookup"><span data-stu-id="f9a9f-348">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="f9a9f-349">Intern I/O-drivrutin initieras</span><span class="sxs-lookup"><span data-stu-id="f9a9f-349">Internal I/O driver initialize</span></span> 

<span data-ttu-id="f9a9f-350">**Ikonen** ![ Initiera ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-350">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/fx-events/image10.png)</span></span>

<span data-ttu-id="f9a9f-351">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-351">**Description**</span></span> 

<span data-ttu-id="f9a9f-352">Den här händelsen representerar en intern händelse för FileX I/O-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-352">This event represents an internal FileX I/O driver initialize event.</span></span>

<span data-ttu-id="f9a9f-353">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-353">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-354">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-354">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-355">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-355">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f9a9f-356">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-356">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-357">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-357">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="f9a9f-358">Läs start sektor för intern I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="f9a9f-358">Internal I/O Driver Boot Sector Read</span></span> 

#### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="f9a9f-359">Läs start sektor för intern I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="f9a9f-359">Internal I/O driver boot sector read</span></span> 

<span data-ttu-id="f9a9f-360">**Ikonen** ![ Läs ikon för intern I/O-drivrutinens start sektor](./media/user-guide/fx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-360">**Icon** ![Internal I / O driver boot sector read icon](./media/user-guide/fx-events/image11.png)</span></span>

<span data-ttu-id="f9a9f-361">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-361">**Description**</span></span> 

<span data-ttu-id="f9a9f-362">Den här händelsen representerar en intern FileX I/O driv rutins start sektor.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-362">This event represents an internal FileX I/O driver boot sector read event.</span></span>

<span data-ttu-id="f9a9f-363">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-363">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-364">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-364">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-365">Info fält 2: buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-365">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="f9a9f-366">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-366">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-367">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-367">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="f9a9f-368">Interna I/O driv Rutins versions sektorer</span><span class="sxs-lookup"><span data-stu-id="f9a9f-368">Internal I/O Driver Release Sectors</span></span> 

#### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="f9a9f-369">Interna I/O driv rutins versions sektorer</span><span class="sxs-lookup"><span data-stu-id="f9a9f-369">Internal I/O driver release sectors</span></span> 

<span data-ttu-id="f9a9f-370">**Ikonen** ![ Intern I/O driv rutins ikon för versions sektorer](./media/user-guide/fx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-370">**Icon** ![Internal I / O driver release sectors icon](./media/user-guide/fx-events/image12.png)</span></span>

<span data-ttu-id="f9a9f-371">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-371">**Description**</span></span> 

<span data-ttu-id="f9a9f-372">Den här händelsen representerar en intern händelse för FileX I/O-drivrutiner.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-372">This event represents an internal FileX I/O driver release sectors event.</span></span>

<span data-ttu-id="f9a9f-373">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-373">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-374">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-374">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-375">Info fält 2: sektor.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-375">Info Field 2: Sector.</span></span>
- <span data-ttu-id="f9a9f-376">Informations fält 3: antal sektorer.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-376">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="f9a9f-377">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-377">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="f9a9f-378">Skriv åtgärd för intern I/O-drivrutins start sektor</span><span class="sxs-lookup"><span data-stu-id="f9a9f-378">Internal I/O Driver Boot Sector Write</span></span>

#### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="f9a9f-379">Skriv åtgärd för intern I/O-drivrutins start sektor</span><span class="sxs-lookup"><span data-stu-id="f9a9f-379">Internal I/O driver boot sector write</span></span> 

<span data-ttu-id="f9a9f-380">**Ikonen** ![ Skriv ikon för intern I/O-drivrutinens start sektor](./media/user-guide/fx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-380">**Icon** ![Internal I / O driver boot sector write icon](./media/user-guide/fx-events/image13.png)</span></span>

<span data-ttu-id="f9a9f-381">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-381">**Description**</span></span> 

<span data-ttu-id="f9a9f-382">Den här händelsen representerar en intern Skriv händelse för FileX I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-382">This event represents an internal FileX I/O driver boot sector write event.</span></span>

<span data-ttu-id="f9a9f-383">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-383">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-384">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-384">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-385">Info fält 2: buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-385">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="f9a9f-386">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-386">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-387">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-387">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="f9a9f-388">Intern I/O-drivrutin avinitieras</span><span class="sxs-lookup"><span data-stu-id="f9a9f-388">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="f9a9f-389">Intern I/O-drivrutin avinitieras</span><span class="sxs-lookup"><span data-stu-id="f9a9f-389">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="f9a9f-390">**Ikonen** ![ Ikon för intern I/O-drivrutin för avinitiering](./media/user-guide/fx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-390">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/fx-events/image14.png)</span></span>

<span data-ttu-id="f9a9f-391">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-391">**Description**</span></span> 

<span data-ttu-id="f9a9f-392">Den här händelsen representerar en intern FileX I/O-drivrutin som avinitieras.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-392">This event represents an internal FileX I/O driver un-initialize event.</span></span>

<span data-ttu-id="f9a9f-393">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-393">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-394">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-394">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-395">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-395">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f9a9f-396">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-396">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-397">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-397">Info Field 4: Not used.</span></span>
</blockquote></td>

### <a name="directory-attributes-read"></a><span data-ttu-id="f9a9f-398">Lästa katalogattribut</span><span class="sxs-lookup"><span data-stu-id="f9a9f-398">Directory Attributes Read</span></span> 

#### <a name="fx_directory_attributes_read"></a><span data-ttu-id="f9a9f-399">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="f9a9f-399">fx_directory_attributes_read</span></span> 

<span data-ttu-id="f9a9f-400">**Ikonen** ![ Läs ikon för katalogattribut](./media/user-guide/fx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-400">**Icon** ![Directory attributes read icon](./media/user-guide/fx-events/image15.png)</span></span>

<span data-ttu-id="f9a9f-401">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-401">**Description**</span></span> 

<span data-ttu-id="f9a9f-402">Den här händelsen representerar en Read-händelse för katalogattribut.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-402">This event represents a directory attributes read event.</span></span>

<span data-ttu-id="f9a9f-403">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-403">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-404">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-404">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-405">Info fält 2: pekare till katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-405">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="f9a9f-406">Informations fält 3: bitmapp för attribut:</span><span class="sxs-lookup"><span data-stu-id="f9a9f-406">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="f9a9f-407">Attribut</span><span class="sxs-lookup"><span data-stu-id="f9a9f-407">Attribute</span></span>                         | <span data-ttu-id="f9a9f-408">Värde</span><span class="sxs-lookup"><span data-stu-id="f9a9f-408">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="f9a9f-409">Skrivskydd</span><span class="sxs-lookup"><span data-stu-id="f9a9f-409">Read Only</span></span>                        | <span data-ttu-id="f9a9f-410">0x01</span><span class="sxs-lookup"><span data-stu-id="f9a9f-410">(0x01)</span></span>  |
  |  <span data-ttu-id="f9a9f-411">Dold</span><span class="sxs-lookup"><span data-stu-id="f9a9f-411">Hidden</span></span>                           | <span data-ttu-id="f9a9f-412">protokollnumret 0x02</span><span class="sxs-lookup"><span data-stu-id="f9a9f-412">(0x02)</span></span>  |
  |  <span data-ttu-id="f9a9f-413">System</span><span class="sxs-lookup"><span data-stu-id="f9a9f-413">System</span></span>                           | <span data-ttu-id="f9a9f-414">(0x04)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-414">(0x04)</span></span>  |
  |  <span data-ttu-id="f9a9f-415">Volym</span><span class="sxs-lookup"><span data-stu-id="f9a9f-415">Volume</span></span>                           | <span data-ttu-id="f9a9f-416">(0x08)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-416">(0x08)</span></span>  |
  |  <span data-ttu-id="f9a9f-417">Katalog</span><span class="sxs-lookup"><span data-stu-id="f9a9f-417">Directory</span></span>                        | <span data-ttu-id="f9a9f-418">0x10</span><span class="sxs-lookup"><span data-stu-id="f9a9f-418">(0x10)</span></span>  |
  |  <span data-ttu-id="f9a9f-419">Arkiv</span><span class="sxs-lookup"><span data-stu-id="f9a9f-419">Archive</span></span>                          | <span data-ttu-id="f9a9f-420">0x20</span><span class="sxs-lookup"><span data-stu-id="f9a9f-420">(0x20)</span></span>  |
- <span data-ttu-id="f9a9f-421">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-421">Info Field 4: Not used.</span></span>

### <a name="directory-attributes-set"></a><span data-ttu-id="f9a9f-422">Katalog-attribut har angetts</span><span class="sxs-lookup"><span data-stu-id="f9a9f-422">Directory Attributes Set</span></span> 

#### <a name="fx_directory_attributes_set"></a><span data-ttu-id="f9a9f-423">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="f9a9f-423">fx_directory_attributes_set</span></span> 

<span data-ttu-id="f9a9f-424">**Ikonen** ![ Ikon för attribut uppsättning](./media/user-guide/fx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-424">**Icon** ![Attributes set icon](./media/user-guide/fx-events/image16.png)</span></span>

<span data-ttu-id="f9a9f-425">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-425">**Description**</span></span> 

<span data-ttu-id="f9a9f-426">Den här händelsen representerar en katalog som anger ett katalog-attribut.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-426">This event represents a directory a directory attributes set event.</span></span>

<span data-ttu-id="f9a9f-427">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-427">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-428">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-428">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-429">Info fält 2: pekare till katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-429">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="f9a9f-430">Informations fält 3: bitmapp för attribut:</span><span class="sxs-lookup"><span data-stu-id="f9a9f-430">Info Field 3: Attributes bit map:</span></span>

  |  <span data-ttu-id="f9a9f-431">Attribut</span><span class="sxs-lookup"><span data-stu-id="f9a9f-431">Attribute</span></span>                        | <span data-ttu-id="f9a9f-432">Värde</span><span class="sxs-lookup"><span data-stu-id="f9a9f-432">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="f9a9f-433">Skrivskydd</span><span class="sxs-lookup"><span data-stu-id="f9a9f-433">Read Only</span></span>                        | <span data-ttu-id="f9a9f-434">0x01</span><span class="sxs-lookup"><span data-stu-id="f9a9f-434">(0x01)</span></span>  |
  |  <span data-ttu-id="f9a9f-435">Dold</span><span class="sxs-lookup"><span data-stu-id="f9a9f-435">Hidden</span></span>                           | <span data-ttu-id="f9a9f-436">protokollnumret 0x02</span><span class="sxs-lookup"><span data-stu-id="f9a9f-436">(0x02)</span></span>  |
  |  <span data-ttu-id="f9a9f-437">System</span><span class="sxs-lookup"><span data-stu-id="f9a9f-437">System</span></span>                           | <span data-ttu-id="f9a9f-438">(0x04)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-438">(0x04)</span></span>  |
  |  <span data-ttu-id="f9a9f-439">Arkiv</span><span class="sxs-lookup"><span data-stu-id="f9a9f-439">Archive</span></span>                          | <span data-ttu-id="f9a9f-440">0x20</span><span class="sxs-lookup"><span data-stu-id="f9a9f-440">(0x20)</span></span>  |
- <span data-ttu-id="f9a9f-441">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-441">Info Field 4: Not used.</span></span>

### <a name="directory-create"></a><span data-ttu-id="f9a9f-442">Skapa katalog</span><span class="sxs-lookup"><span data-stu-id="f9a9f-442">Directory Create</span></span> 

#### <a name="fx_directory_create"></a><span data-ttu-id="f9a9f-443">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="f9a9f-443">fx_directory_create</span></span>

<span data-ttu-id="f9a9f-444">**Ikonen** ![ Ikon för att skapa katalog](./media/user-guide/fx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-444">**Icon** ![Directory create icon](./media/user-guide/fx-events/image17.png)</span></span>

<span data-ttu-id="f9a9f-445">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-445">**Description**</span></span> 

<span data-ttu-id="f9a9f-446">Den här händelsen representerar en händelse för katalog skapande.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-446">This event represents a directory create event.</span></span>

<span data-ttu-id="f9a9f-447">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-447">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-448">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-448">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-449">Info fält 2: pekare till katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-449">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="f9a9f-450">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-451">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-451">Info Field 4: Not used.</span></span>

### <a name="directory-default-get"></a><span data-ttu-id="f9a9f-452">Hämta katalog standard</span><span class="sxs-lookup"><span data-stu-id="f9a9f-452">Directory Default Get</span></span> 

#### <a name="fx_directory_default_get"></a><span data-ttu-id="f9a9f-453">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="f9a9f-453">fx_directory_default_get</span></span> 

<span data-ttu-id="f9a9f-454">**Ikonen** ![ Hämta ikon för katalog standard](./media/user-guide/fx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-454">**Icon** ![Directory default get icon](./media/user-guide/fx-events/image18.png)</span></span>

<span data-ttu-id="f9a9f-455">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-455">**Description**</span></span> 

<span data-ttu-id="f9a9f-456">Den här händelsen representerar en händelse för katalog standard uppsättning.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-456">This event represents a directory default set event.</span></span>

<span data-ttu-id="f9a9f-457">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-457">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-458">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-458">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-459">Info fält 2: en pekare till retur Sök vägs namnet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-459">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="f9a9f-460">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-461">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-461">Info Field 4: Not used.</span></span>

### <a name="directory-default-set"></a><span data-ttu-id="f9a9f-462">Katalog standard uppsättning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-462">Directory Default Set</span></span> 

#### <a name="fx_directory_default_set"></a><span data-ttu-id="f9a9f-463">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="f9a9f-463">fx_directory_default_set</span></span> 

<span data-ttu-id="f9a9f-464">**Ikonen** ![ Ikon för katalog standard uppsättning](./media/user-guide/fx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-464">**Icon** ![Directory default set icon](./media/user-guide/fx-events/image19.png)</span></span>

<span data-ttu-id="f9a9f-465">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-465">**Description**</span></span> 

<span data-ttu-id="f9a9f-466">Den här händelsen representerar en händelse för katalog standard uppsättning.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-466">This event represents a directory default set event.</span></span>

<span data-ttu-id="f9a9f-467">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-467">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-468">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-468">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-469">Info fält 2: pekar mot nytt standard Sök vägs namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-469">Info Field 2: Pointer to new default path name.</span></span>
- <span data-ttu-id="f9a9f-470">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-471">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-471">Info Field 4: Not used.</span></span>

### <a name="directory-delete"></a><span data-ttu-id="f9a9f-472">Ta bort katalog</span><span class="sxs-lookup"><span data-stu-id="f9a9f-472">Directory Delete</span></span> 

#### <a name="fx_directory_delete"></a><span data-ttu-id="f9a9f-473">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="f9a9f-473">fx_directory_delete</span></span>

<span data-ttu-id="f9a9f-474">**Ikonen** ![ Ikonen Ta bort katalog](./media/user-guide/fx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-474">**Icon** ![Directory delete icon](./media/user-guide/fx-events/image20.png)</span></span>

<span data-ttu-id="f9a9f-475">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-475">**Description**</span></span> 

<span data-ttu-id="f9a9f-476">Den här händelsen representerar en katalog borttagnings händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-476">This event represents a directory delete event.</span></span>

<span data-ttu-id="f9a9f-477">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-477">**Information Fields**</span></span>
- <span data-ttu-id="f9a9f-478">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-478">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-479">Info fält 2: pekare till katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-479">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="f9a9f-480">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-481">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-481">Info Field 4: Not used.</span></span>

### <a name="directory-first-entry-find"></a><span data-ttu-id="f9a9f-482">Hitta katalog första posten</span><span class="sxs-lookup"><span data-stu-id="f9a9f-482">Directory First Entry Find</span></span> 

#### <a name="fx_directory_first_entry_find"></a><span data-ttu-id="f9a9f-483">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="f9a9f-483">fx_directory_first_entry_find</span></span>

<span data-ttu-id="f9a9f-484">**Ikonen** ![ Hitta ikon för första katalog posten](./media/user-guide/fx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-484">**Icon** ![Directory first entry find icon](./media/user-guide/fx-events/image21.png)</span></span>

<span data-ttu-id="f9a9f-485">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-485">**Description**</span></span> 

<span data-ttu-id="f9a9f-486">Den här händelsen representerar en händelse för katalog första posten.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-486">This event represents a directory first entry find event.</span></span>

<span data-ttu-id="f9a9f-487">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-487">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-488">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-488">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-489">Info fält 2: pekare till katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-489">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="f9a9f-490">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-491">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-491">Info Field 4: Not used.</span></span>

### <a name="directory-first-full-entry-find"></a><span data-ttu-id="f9a9f-492">Katalog-första fullständiga post Sök</span><span class="sxs-lookup"><span data-stu-id="f9a9f-492">Directory First Full Entry Find</span></span> 

#### <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="f9a9f-493">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="f9a9f-493">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="f9a9f-494">**Ikonen** ![ Hitta ikon för första katalog start posten](./media/user-guide/fx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-494">**Icon** ![Directory first full entry find icon](./media/user-guide/fx-events/image22.png)</span></span>

<span data-ttu-id="f9a9f-495">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-495">**Description**</span></span> 

<span data-ttu-id="f9a9f-496">Den här händelsen representerar en katalog för första posten för att hitta en katalog.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-496">This event represents a directory first full entry find event.</span></span>

<span data-ttu-id="f9a9f-497">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-497">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-498">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-498">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-499">Info fält 2: pekare till katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-499">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="f9a9f-500">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-501">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-501">Info Field 4: Not used.</span></span>

### <a name="directory-information-get"></a><span data-ttu-id="f9a9f-502">Hämta katalog information</span><span class="sxs-lookup"><span data-stu-id="f9a9f-502">Directory Information Get</span></span> 

#### <a name="fx_directory_information_get"></a><span data-ttu-id="f9a9f-503">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="f9a9f-503">fx_directory_information_get</span></span>

<span data-ttu-id="f9a9f-504">**Ikonen** ![ Ikon för Hämta katalog information](./media/user-guide/fx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-504">**Icon** ![Directory information get icon](./media/user-guide/fx-events/image23.png)</span></span>

<span data-ttu-id="f9a9f-505">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-505">**Description**</span></span> 

<span data-ttu-id="f9a9f-506">Den här händelsen representerar en händelse för att hämta katalog information.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-506">This event represents a directory information get event.</span></span>

<span data-ttu-id="f9a9f-507">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-507">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-508">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-508">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-509">Info fält 2: pekare till katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-509">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="f9a9f-510">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-510">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-511">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-511">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-clear"></a><span data-ttu-id="f9a9f-512">Rensa katalogens lokala sökväg</span><span class="sxs-lookup"><span data-stu-id="f9a9f-512">Directory Local Path Clear</span></span> 

#### <a name="fx_directory_local_path_clear"></a><span data-ttu-id="f9a9f-513">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="f9a9f-513">fx_directory_local_path_clear</span></span>

<span data-ttu-id="f9a9f-514">**Ikonen** ![ Ikon för lokal sökväg för katalog](./media/user-guide/fx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-514">**Icon** ![Directory local path clear icon](./media/user-guide/fx-events/image24.png)</span></span>

<span data-ttu-id="f9a9f-515">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-515">**Description**</span></span> 

<span data-ttu-id="f9a9f-516">Den här händelsen representerar en händelse av en lokal katalog Sök väg.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-516">This event represents a directory local path clear event.</span></span>

<span data-ttu-id="f9a9f-517">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-517">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-518">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-518">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-519">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f9a9f-520">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-521">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-521">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-get"></a><span data-ttu-id="f9a9f-522">Hämta lokal sökväg för katalog</span><span class="sxs-lookup"><span data-stu-id="f9a9f-522">Directory Local Path Get</span></span> 

#### <a name="fx_directory_local_path_get"></a><span data-ttu-id="f9a9f-523">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="f9a9f-523">fx_directory_local_path_get</span></span>

<span data-ttu-id="f9a9f-524">**Ikonen** ![ Hämta ikon för lokal sökväg för katalog](./media/user-guide/fx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-524">**Icon** ![Directory local path get icon](./media/user-guide/fx-events/image25.png)</span></span>

<span data-ttu-id="f9a9f-525">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-525">**Description**</span></span> 

<span data-ttu-id="f9a9f-526">Den här händelsen representerar en händelse för en lokal katalog Sök väg.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-526">This event represents a directory local path get event.</span></span>

<span data-ttu-id="f9a9f-527">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-527">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-528">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-528">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-529">Info fält 2: en pekare till retur Sök vägs namnet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-529">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="f9a9f-530">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-531">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-531">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-restore"></a><span data-ttu-id="f9a9f-532">Återställning av lokal sökväg för katalog</span><span class="sxs-lookup"><span data-stu-id="f9a9f-532">Directory Local Path Restore</span></span> 

#### <a name="fx_directory_local_path_restore"></a><span data-ttu-id="f9a9f-533">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="f9a9f-533">fx_directory_local_path_restore</span></span>

<span data-ttu-id="f9a9f-534">**Ikonen** ![ Ikon för återställning av lokal sökväg för katalog](./media/user-guide/fx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-534">**Icon** ![Directory local path restore icon](./media/user-guide/fx-events/image26.png)</span></span>

<span data-ttu-id="f9a9f-535">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-535">**Description**</span></span> 

<span data-ttu-id="f9a9f-536">Den här händelsen representerar en händelse för återställning av lokal katalog Sök väg.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-536">This event represents a directory local path restore event.</span></span>

<span data-ttu-id="f9a9f-537">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-537">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-538">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-538">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-539">Info fält 2: pekar mot lokal sökväg.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-539">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="f9a9f-540">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-540">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-541">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-541">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-set"></a><span data-ttu-id="f9a9f-542">Lokal katalog Sök väg uppsättning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-542">Directory Local Path Set</span></span> 

#### <a name="fx_directory_local_path_set"></a><span data-ttu-id="f9a9f-543">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="f9a9f-543">fx_directory_local_path_set</span></span>

<span data-ttu-id="f9a9f-544">**Ikonen** ![ Ikon för lokal sökväg för katalog](./media/user-guide/fx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-544">**Icon** ![Directory local path set icon](./media/user-guide/fx-events/image27.png)</span></span>

<span data-ttu-id="f9a9f-545">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-545">**Description**</span></span> 

<span data-ttu-id="f9a9f-546">Den här händelsen representerar en händelse för lokal katalog Sök väg.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-546">This event represents a directory local path set event.</span></span>

<span data-ttu-id="f9a9f-547">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-547">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-548">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-548">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-549">Info fält 2: pekar mot lokal sökväg.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-549">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="f9a9f-550">Info-fält 3: pekar mot nytt Sök vägs namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-550">Info Field 3: Pointer to new path name.</span></span>
- <span data-ttu-id="f9a9f-551">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-551">Info Field 4: Not used.</span></span>

### <a name="directory-long-name-get"></a><span data-ttu-id="f9a9f-552">Katalogens långa namn Hämta</span><span class="sxs-lookup"><span data-stu-id="f9a9f-552">Directory Long Name Get</span></span> 

#### <a name="fx_directory_long_name_get"></a><span data-ttu-id="f9a9f-553">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="f9a9f-553">fx_directory_long_name_get</span></span>

<span data-ttu-id="f9a9f-554">**Ikonen** ![ Hämta ikon för katalogens långa namn](./media/user-guide/fx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-554">**Icon** ![Directory long name get icon](./media/user-guide/fx-events/image28.png)</span></span>

<span data-ttu-id="f9a9f-555">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-555">**Description**</span></span> 

<span data-ttu-id="f9a9f-556">Den här händelsen representerar en händelse för katalog långa namn get.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-556">This event represents a directory long name get event.</span></span>

<span data-ttu-id="f9a9f-557">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-557">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-558">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-558">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-559">Info fält 2: pekar mot kort fil namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-559">Info Field 2: Pointer to short file name.</span></span>
- <span data-ttu-id="f9a9f-560">Info-fält 3: pekar på långt fil namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-560">Info Field 3: Pointer to long file name.</span></span>
- <span data-ttu-id="f9a9f-561">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-561">Info Field 4: Not used.</span></span>

### <a name="directory-name-test"></a><span data-ttu-id="f9a9f-562">Katalog namns test</span><span class="sxs-lookup"><span data-stu-id="f9a9f-562">Directory Name Test</span></span> 

#### <a name="fx_directory_name_test"></a><span data-ttu-id="f9a9f-563">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="f9a9f-563">fx_directory_name_test</span></span>

<span data-ttu-id="f9a9f-564">**Ikonen** ![ Ikon för katalog namns test](./media/user-guide/fx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-564">**Icon** ![Directory name test icon](./media/user-guide/fx-events/image29.png)</span></span>

<span data-ttu-id="f9a9f-565">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-565">**Description**</span></span> 

<span data-ttu-id="f9a9f-566">Den här händelsen representerar ett test händelse för katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-566">This event represents a directory name test event.</span></span>

<span data-ttu-id="f9a9f-567">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-567">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-568">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-568">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-569">Info fält 2: pekare till katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-569">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="f9a9f-570">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-570">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-571">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-571">Info Field 4: Not used.</span></span>

### <a name="directory-next-entry-find"></a><span data-ttu-id="f9a9f-572">Sök efter katalog nästa post</span><span class="sxs-lookup"><span data-stu-id="f9a9f-572">Directory Next Entry Find</span></span> 

#### <a name="fx_directory_next_entry_find"></a><span data-ttu-id="f9a9f-573">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="f9a9f-573">fx_directory_next_entry_find</span></span>

<span data-ttu-id="f9a9f-574">**Ikonen** ![ Sök ikon för katalog nästa post](./media/user-guide/fx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-574">**Icon** ![Directory next entry find icon](./media/user-guide/fx-events/image30.png)</span></span>

<span data-ttu-id="f9a9f-575">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-575">**Description**</span></span> 

<span data-ttu-id="f9a9f-576">Den här händelsen representerar en katalog nästa post hitta händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-576">This event represents a directory next entry find event.</span></span>

<span data-ttu-id="f9a9f-577">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-577">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-578">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-578">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-579">Info fält 2: pekare till katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-579">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="f9a9f-580">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-580">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-581">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-581">Info Field 4: Not used.</span></span>

### <a name="directory-next-full-entry-find"></a><span data-ttu-id="f9a9f-582">Sök i katalog nästa fullständiga post</span><span class="sxs-lookup"><span data-stu-id="f9a9f-582">Directory Next Full Entry Find</span></span> 

#### <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="f9a9f-583">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="f9a9f-583">fx_directory_next_full_entry_find</span></span>

<span data-ttu-id="f9a9f-584">**Ikonen** ![ Sök ikon för nästa fullständiga post-katalog](./media/user-guide/fx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-584">**Icon** ![Directory next full entry find icon](./media/user-guide/fx-events/image31.png)</span></span>

<span data-ttu-id="f9a9f-585">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-585">**Description**</span></span>

<span data-ttu-id="f9a9f-586">Den här händelsen representerar en katalog nästa post hitta händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-586">This event represents a directory next full entry find event.</span></span>

<span data-ttu-id="f9a9f-587">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-587">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-588">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-588">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-589">Info fält 2: pekare till katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-589">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="f9a9f-590">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-590">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-591">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-591">Info Field 4: Not used.</span></span>

### <a name="directory-rename"></a><span data-ttu-id="f9a9f-592">Byt namn på katalog</span><span class="sxs-lookup"><span data-stu-id="f9a9f-592">Directory Rename</span></span> 

#### <a name="fx_directory_rename-event"></a><span data-ttu-id="f9a9f-593">fx_directory_rename händelse</span><span class="sxs-lookup"><span data-stu-id="f9a9f-593">fx_directory_rename event</span></span>

<span data-ttu-id="f9a9f-594">**Ikonen** ![ Ikon för katalog namn](./media/user-guide/fx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-594">**Icon** ![Directory rename icon](./media/user-guide/fx-events/image32.png)</span></span>

<span data-ttu-id="f9a9f-595">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-595">**Description**</span></span>

<span data-ttu-id="f9a9f-596">Den här händelsen representerar en händelse för katalog namnbyte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-596">This event represents a directory rename event.</span></span>

<span data-ttu-id="f9a9f-597">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-597">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-598">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-598">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-599">Info fält 2: pekar på gammalt katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-599">Info Field 2: Pointer to old directory name.</span></span>
- <span data-ttu-id="f9a9f-600">Info-fält 3: pekar på nytt katalog namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-600">Info Field 3: Pointer to new directory name.</span></span>
- <span data-ttu-id="f9a9f-601">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-601">Info Field 4: Not used.</span></span>

### <a name="directory-short-name-get"></a><span data-ttu-id="f9a9f-602">Katalog kort namn Hämta</span><span class="sxs-lookup"><span data-stu-id="f9a9f-602">Directory Short Name Get</span></span> 

#### <a name="fx_directory_short_name_get"></a><span data-ttu-id="f9a9f-603">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="f9a9f-603">fx_directory_short_name_get</span></span>

<span data-ttu-id="f9a9f-604">**Ikonen** ![ Katalog kort namn Hämta ikon](./media/user-guide/fx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-604">**Icon** ![Directory short name get icon](./media/user-guide/fx-events/image33.png)</span></span>

<span data-ttu-id="f9a9f-605">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-605">**Description**</span></span>

<span data-ttu-id="f9a9f-606">Den här händelsen representerar en händelse för kort för katalog kort namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-606">This event represents a directory short name get event.</span></span>

<span data-ttu-id="f9a9f-607">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-607">**Information Fields**</span></span> 

- <span data-ttu-id="f9a9f-608">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-608">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-609">Info fält 2: pekar mot långt fil namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-609">Info Field 2: Pointer to long file name.</span></span>
- <span data-ttu-id="f9a9f-610">Info-fält 3: pekar mot kort fil namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-610">Info Field 3: Pointer to short file name.</span></span>
- <span data-ttu-id="f9a9f-611">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-611">Info Field 4: Not used.</span></span>

### <a name="file-allocate"></a><span data-ttu-id="f9a9f-612">Fil tilldelning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-612">File Allocate</span></span> 

#### <a name="fx_file_allocate"></a><span data-ttu-id="f9a9f-613">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="f9a9f-613">fx_file_allocate</span></span>

<span data-ttu-id="f9a9f-614">**Ikonen** ![ Fil tilldelnings ikon](./media/user-guide/fx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-614">**Icon** ![File allocate icon](./media/user-guide/fx-events/image34.png)</span></span>

<span data-ttu-id="f9a9f-615">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-615">**Description**</span></span>

<span data-ttu-id="f9a9f-616">Den här händelsen representerar en fil tilldelnings händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-616">This event represents a file allocate event.</span></span>

<span data-ttu-id="f9a9f-617">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-617">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-618">Info fält 1: pekar mot filen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-618">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="f9a9f-619">Informations fält 2: begärd storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-619">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="f9a9f-620">Info-fält 3: aktuell storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-620">Info Field 3: Current size.</span></span>
- <span data-ttu-id="f9a9f-621">Info fält 4: ny storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-621">Info Field 4: New size.</span></span>

### <a name="file-attributes-read"></a><span data-ttu-id="f9a9f-622">Lästa filattribut</span><span class="sxs-lookup"><span data-stu-id="f9a9f-622">File Attributes Read</span></span> 

#### <a name="fx_file_attributes_read"></a><span data-ttu-id="f9a9f-623">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="f9a9f-623">fx_file_attributes_read</span></span>

<span data-ttu-id="f9a9f-624">**Ikonen** ![ Läs ikon för filattribut](./media/user-guide/fx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-624">**Icon** ![File attributes read icon](./media/user-guide/fx-events/image35.png)</span></span>

<span data-ttu-id="f9a9f-625">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-625">**Description**</span></span>

<span data-ttu-id="f9a9f-626">Den här händelsen representerar filattributen Read event.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-626">This event represents a file attributes read event.</span></span>

<span data-ttu-id="f9a9f-627">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-627">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-628">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-628">Info Field 1: Pointer to the media.</span></span> 
- <span data-ttu-id="f9a9f-629">Info fält 2: bitmapp för attribut:</span><span class="sxs-lookup"><span data-stu-id="f9a9f-629">Info Field 2: Attributes bit map:</span></span>

  |  <span data-ttu-id="f9a9f-630">Behörighet</span><span class="sxs-lookup"><span data-stu-id="f9a9f-630">Attribut</span></span>                         | <span data-ttu-id="f9a9f-631">Värde</span><span class="sxs-lookup"><span data-stu-id="f9a9f-631">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="f9a9f-632">Skrivskydd</span><span class="sxs-lookup"><span data-stu-id="f9a9f-632">Read Only</span></span>                        | <span data-ttu-id="f9a9f-633">0x01</span><span class="sxs-lookup"><span data-stu-id="f9a9f-633">(0x01)</span></span>  |
  |  <span data-ttu-id="f9a9f-634">Dold</span><span class="sxs-lookup"><span data-stu-id="f9a9f-634">Hidden</span></span>                           | <span data-ttu-id="f9a9f-635">protokollnumret 0x02</span><span class="sxs-lookup"><span data-stu-id="f9a9f-635">(0x02)</span></span>  |
  |  <span data-ttu-id="f9a9f-636">System</span><span class="sxs-lookup"><span data-stu-id="f9a9f-636">System</span></span>                           | <span data-ttu-id="f9a9f-637">(0x04)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-637">(0x04)</span></span>  |
  |  <span data-ttu-id="f9a9f-638">Volym</span><span class="sxs-lookup"><span data-stu-id="f9a9f-638">Volume</span></span>                           | <span data-ttu-id="f9a9f-639">(0x08)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-639">(0x08)</span></span>  |
  |  <span data-ttu-id="f9a9f-640">Katalog</span><span class="sxs-lookup"><span data-stu-id="f9a9f-640">Directory</span></span>                        | <span data-ttu-id="f9a9f-641">0x10</span><span class="sxs-lookup"><span data-stu-id="f9a9f-641">(0x10)</span></span>  |
  |  <span data-ttu-id="f9a9f-642">Arkiv</span><span class="sxs-lookup"><span data-stu-id="f9a9f-642">Archive</span></span>                          | <span data-ttu-id="f9a9f-643">0x20</span><span class="sxs-lookup"><span data-stu-id="f9a9f-643">(0x20)</span></span>  |
- <span data-ttu-id="f9a9f-644">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-644">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-645">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-645">Info Field 4: Not used.</span></span>

### <a name="file-attributes-set"></a><span data-ttu-id="f9a9f-646">Angivna filattribut</span><span class="sxs-lookup"><span data-stu-id="f9a9f-646">File Attributes Set</span></span> 

#### <a name="fx_file_attributes_set"></a><span data-ttu-id="f9a9f-647">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="f9a9f-647">fx_file_attributes_set</span></span>

<span data-ttu-id="f9a9f-648">**Ikonen** ![ Ikonen filattribut ange](./media/user-guide/fx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-648">**Icon** ![File attributes set icon](./media/user-guide/fx-events/image36.png)</span></span>

<span data-ttu-id="f9a9f-649">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-649">**Description**</span></span> 

<span data-ttu-id="f9a9f-650">Den här händelsen representerar en händelse som anger filattribut.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-650">This event represents a file attributes set event.</span></span>

<span data-ttu-id="f9a9f-651">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-651">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-652">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-652">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-653">Info fält 2: pekar på fil namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-653">Info Field 2: Pointer to file name.</span></span> 
- <span data-ttu-id="f9a9f-654">Informations fält 3: bitmapp för attribut:</span><span class="sxs-lookup"><span data-stu-id="f9a9f-654">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="f9a9f-655">Attribut</span><span class="sxs-lookup"><span data-stu-id="f9a9f-655">Attribute</span></span>                         | <span data-ttu-id="f9a9f-656">Värde</span><span class="sxs-lookup"><span data-stu-id="f9a9f-656">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="f9a9f-657">Skrivskydd</span><span class="sxs-lookup"><span data-stu-id="f9a9f-657">Read Only</span></span>                        | <span data-ttu-id="f9a9f-658">0x01</span><span class="sxs-lookup"><span data-stu-id="f9a9f-658">(0x01)</span></span>  |
  |  <span data-ttu-id="f9a9f-659">Dold</span><span class="sxs-lookup"><span data-stu-id="f9a9f-659">Hidden</span></span>                           | <span data-ttu-id="f9a9f-660">protokollnumret 0x02</span><span class="sxs-lookup"><span data-stu-id="f9a9f-660">(0x02)</span></span>  |
  |  <span data-ttu-id="f9a9f-661">System</span><span class="sxs-lookup"><span data-stu-id="f9a9f-661">System</span></span>                           | <span data-ttu-id="f9a9f-662">(0x04)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-662">(0x04)</span></span>  |
  |  <span data-ttu-id="f9a9f-663">Arkiv</span><span class="sxs-lookup"><span data-stu-id="f9a9f-663">Archive</span></span>                          | <span data-ttu-id="f9a9f-664">0x20</span><span class="sxs-lookup"><span data-stu-id="f9a9f-664">(0x20)</span></span>  |
- <span data-ttu-id="f9a9f-665">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-665">Info Field 4: Not used.</span></span>

### <a name="file-best-effort-allocate"></a><span data-ttu-id="f9a9f-666">Bästa fördelar med fil arbete</span><span class="sxs-lookup"><span data-stu-id="f9a9f-666">File Best Effort Allocate</span></span> 

#### <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="f9a9f-667">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="f9a9f-667">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="f9a9f-668">**Ikonen** ![ Ikon för att allokera bästa ansträngning](./media/user-guide/fx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-668">**Icon** ![File best effort allocate icon](./media/user-guide/fx-events/image37.png)</span></span>

<span data-ttu-id="f9a9f-669">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-669">**Description**</span></span> 

<span data-ttu-id="f9a9f-670">Den här händelsen representerar en metod för att allokera en fil.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-670">This event represents a file best effort allocate event.</span></span>

<span data-ttu-id="f9a9f-671">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-671">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-672">Info fält 1: pekar mot filen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-672">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="f9a9f-673">Informations fält 2: begärd storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-673">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="f9a9f-674">Info-fält 3: den faktiska storlek som har tilldelats.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-674">Info Field 3: Actual size allocated.</span></span>
- <span data-ttu-id="f9a9f-675">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-675">Info Field 4: Not used.</span></span>

### <a name="file-close"></a><span data-ttu-id="f9a9f-676">Stäng fil</span><span class="sxs-lookup"><span data-stu-id="f9a9f-676">File Close</span></span> 

#### <a name="fx_file_close"></a><span data-ttu-id="f9a9f-677">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="f9a9f-677">fx_file_close</span></span>

<span data-ttu-id="f9a9f-678">**Ikonen** ![ Fil stängnings ikon](./media/user-guide/fx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-678">**Icon** ![File close icon](./media/user-guide/fx-events/image38.png)</span></span>

<span data-ttu-id="f9a9f-679">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-679">**Description**</span></span> 

<span data-ttu-id="f9a9f-680">Den här händelsen representerar en fil stängnings händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-680">This event represents a file close event.</span></span>

<span data-ttu-id="f9a9f-681">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-681">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-682">Info fält 1: pekar mot filen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-682">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="f9a9f-683">Info fält 2: fil storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-683">Info Field 2: File size.</span></span>
- <span data-ttu-id="f9a9f-684">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-684">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-685">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-685">Info Field 4: Not used.</span></span>

### <a name="file-create"></a><span data-ttu-id="f9a9f-686">Skapa fil</span><span class="sxs-lookup"><span data-stu-id="f9a9f-686">File Create</span></span>

#### <a name="fx_file_create"></a><span data-ttu-id="f9a9f-687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="f9a9f-687">fx_file_create</span></span>

<span data-ttu-id="f9a9f-688">**Ikonen** ![ Ikon för fil skapande](./media/user-guide/fx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-688">**Icon** ![File create icon](./media/user-guide/fx-events/image39.png)</span></span>

<span data-ttu-id="f9a9f-689">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-689">**Description**</span></span>

<span data-ttu-id="f9a9f-690">Den här händelsen representerar en händelse för att skapa en fil.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-690">This event represents a file create event.</span></span>

<span data-ttu-id="f9a9f-691">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-691">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-692">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-692">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-693">Info fält 2: pekar på fil namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-693">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="f9a9f-694">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-694">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-695">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-695">Info Field 4: Not used.</span></span>

### <a name="file-date-time-set"></a><span data-ttu-id="f9a9f-696">Datum och tid för filen</span><span class="sxs-lookup"><span data-stu-id="f9a9f-696">File Date Time Set</span></span> 

#### <a name="fx_file_date_time_set"></a><span data-ttu-id="f9a9f-697">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="f9a9f-697">fx_file_date_time_set</span></span>

<span data-ttu-id="f9a9f-698">**Ikonen** ![ Ikon för datum/tid för fil uppsättning](./media/user-guide/fx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-698">**Icon** ![File date time set icon](./media/user-guide/fx-events/image40.png)</span></span>

<span data-ttu-id="f9a9f-699">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-699">**Description**</span></span>

<span data-ttu-id="f9a9f-700">Den här händelsen representerar en händelse för fil datum/tids uppsättning.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-700">This event represents a file date/time set event.</span></span>

<span data-ttu-id="f9a9f-701">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-701">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-702">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-702">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-703">Info fält 2: pekar på fil namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-703">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="f9a9f-704">Info-fält 3: år.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-704">Info Field 3: Year.</span></span>
- <span data-ttu-id="f9a9f-705">Info fält 4: månad.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-705">Info Field 4: Month.</span></span>

### <a name="file-delete"></a><span data-ttu-id="f9a9f-706">Ta bort fil</span><span class="sxs-lookup"><span data-stu-id="f9a9f-706">File Delete</span></span> 

#### <a name="fx_file_delete"></a><span data-ttu-id="f9a9f-707">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="f9a9f-707">fx_file_delete</span></span>

<span data-ttu-id="f9a9f-708">**Ikonen** ![ Fil borttagnings ikon](./media/user-guide/fx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-708">**Icon** ![File delete icon](./media/user-guide/fx-events/image41.png)</span></span>

<span data-ttu-id="f9a9f-709">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-709">**Description**</span></span>

<span data-ttu-id="f9a9f-710">Den här händelsen representerar en fil borttagnings händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-710">This event represents a file delete event.</span></span>

<span data-ttu-id="f9a9f-711">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-711">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-712">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-712">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-713">Info fält 2: pekar på fil namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-713">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="f9a9f-714">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-714">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-715">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-715">Info Field 4: Not used.</span></span>

### <a name="file-open"></a><span data-ttu-id="f9a9f-716">Öppna fil</span><span class="sxs-lookup"><span data-stu-id="f9a9f-716">File Open</span></span> 

#### <a name="fx_file_open"></a><span data-ttu-id="f9a9f-717">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="f9a9f-717">fx_file_open</span></span>

<span data-ttu-id="f9a9f-718">**Ikonen** ![ Fil öppnings ikon](./media/user-guide/fx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-718">**Icon** ![File open icon](./media/user-guide/fx-events/image42.png)</span></span>

<span data-ttu-id="f9a9f-719">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-719">**Description**</span></span>

<span data-ttu-id="f9a9f-720">Den här händelsen representerar en fil öppnings händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-720">This event represents a file open event.</span></span>

<span data-ttu-id="f9a9f-721">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-721">**Information Fields**</span></span> 

- <span data-ttu-id="f9a9f-722">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-722">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-723">Info fält 2: pekar mot fil kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-723">Info Field 2: Pointer to the file control block.</span></span>
- <span data-ttu-id="f9a9f-724">Info fält 3: pekar på fil namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-724">Info Field 3: Pointer to file name.</span></span>
- <span data-ttu-id="f9a9f-725">Info-fält 4: öppen typ:</span><span class="sxs-lookup"><span data-stu-id="f9a9f-725">Info Field 4: Open type:</span></span>

  |  <span data-ttu-id="f9a9f-726">Öppen typ</span><span class="sxs-lookup"><span data-stu-id="f9a9f-726">Open Type</span></span>                        | <span data-ttu-id="f9a9f-727">Värde</span><span class="sxs-lookup"><span data-stu-id="f9a9f-727">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="f9a9f-728">Öppna för läsning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-728">Open for Read</span></span>                    | <span data-ttu-id="f9a9f-729">0x00</span><span class="sxs-lookup"><span data-stu-id="f9a9f-729">(0x00)</span></span>  |
  |  <span data-ttu-id="f9a9f-730">Öppna för skrivning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-730">Open for Write</span></span>                   | <span data-ttu-id="f9a9f-731">0x01</span><span class="sxs-lookup"><span data-stu-id="f9a9f-731">(0x01)</span></span>  |
  |  <span data-ttu-id="f9a9f-732">Snabb öppen för läsning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-732">Fast Open for Read</span></span>               | <span data-ttu-id="f9a9f-733">protokollnumret 0x02</span><span class="sxs-lookup"><span data-stu-id="f9a9f-733">(0x02)</span></span>  |

### <a name="file-read"></a><span data-ttu-id="f9a9f-734">Fil läsning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-734">File Read</span></span> 

#### <a name="fx_file_read"></a><span data-ttu-id="f9a9f-735">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="f9a9f-735">fx_file_read</span></span>

<span data-ttu-id="f9a9f-736">**Ikonen** ![ Fil läsnings ikon](./media/user-guide/fx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-736">**Icon** ![File read icon](./media/user-guide/fx-events/image43.png)</span></span>

<span data-ttu-id="f9a9f-737">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-737">**Description**</span></span>

<span data-ttu-id="f9a9f-738">Den här händelsen representerar en fil läsnings händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-738">This event represents a file read event.</span></span>

<span data-ttu-id="f9a9f-739">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-739">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-740">Info fält 1: pekar mot filen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-740">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="f9a9f-741">Info fält 2: buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-741">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="f9a9f-742">Info-fält 3: begär ande storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-742">Info Field 3: Request size.</span></span>
- <span data-ttu-id="f9a9f-743">Info fält 4: verklig storlek läst.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-743">Info Field 4: Actual size read.</span></span>

### <a name="file-relative-seek"></a><span data-ttu-id="f9a9f-744">Fil relativ sökning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-744">File Relative Seek</span></span> 

#### <a name="fx_file_relative_seek"></a><span data-ttu-id="f9a9f-745">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="f9a9f-745">fx_file_relative_seek</span></span>

<span data-ttu-id="f9a9f-746">**Ikonen** ![ Ikon för fil relativ sökning](./media/user-guide/fx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-746">**Icon** ![File relative seek icon](./media/user-guide/fx-events/image44.png)</span></span>

<span data-ttu-id="f9a9f-747">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-747">**Description**</span></span>

<span data-ttu-id="f9a9f-748">Den här händelsen representerar en fil relativ sökning-händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-748">This event represents a file relative seek event.</span></span>

<span data-ttu-id="f9a9f-749">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-749">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-750">Info fält 1: pekar mot filen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-750">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="f9a9f-751">Informations fält 2: byte förskjutning.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-751">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="f9a9f-752">Informations fält 3: Sök från:</span><span class="sxs-lookup"><span data-stu-id="f9a9f-752">Info Field 3: Seek from:</span></span>

  | <span data-ttu-id="f9a9f-753">Händelse</span><span class="sxs-lookup"><span data-stu-id="f9a9f-753">Event</span></span>                             | <span data-ttu-id="f9a9f-754">Värde</span><span class="sxs-lookup"><span data-stu-id="f9a9f-754">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="f9a9f-755">Från början</span><span class="sxs-lookup"><span data-stu-id="f9a9f-755">From Beginning</span></span>                   | <span data-ttu-id="f9a9f-756">0x00</span><span class="sxs-lookup"><span data-stu-id="f9a9f-756">(0x00)</span></span>  |
  |  <span data-ttu-id="f9a9f-757">Från slut</span><span class="sxs-lookup"><span data-stu-id="f9a9f-757">From End</span></span>                         | <span data-ttu-id="f9a9f-758">0x01</span><span class="sxs-lookup"><span data-stu-id="f9a9f-758">(0x01)</span></span>  | 
  |  <span data-ttu-id="f9a9f-759">Vidarebefordra</span><span class="sxs-lookup"><span data-stu-id="f9a9f-759">Forward</span></span>                          | <span data-ttu-id="f9a9f-760">protokollnumret 0x02</span><span class="sxs-lookup"><span data-stu-id="f9a9f-760">(0x02)</span></span>  |
  |  <span data-ttu-id="f9a9f-761">Bakåt</span><span class="sxs-lookup"><span data-stu-id="f9a9f-761">Backward</span></span>                         | <span data-ttu-id="f9a9f-762">(0x03)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-762">(0x03)</span></span>  |
- <span data-ttu-id="f9a9f-763">Info fält 4: föregående offset.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-763">Info Field 4: Previous offset.</span></span>

### <a name="file-rename"></a><span data-ttu-id="f9a9f-764">Byt namn på fil</span><span class="sxs-lookup"><span data-stu-id="f9a9f-764">File Rename</span></span> 

#### <a name="fx_file_rename"></a><span data-ttu-id="f9a9f-765">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="f9a9f-765">fx_file_rename</span></span>

<span data-ttu-id="f9a9f-766">**Ikonen** ![ Ikon för fil namn](./media/user-guide/fx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-766">**Icon** ![File rename icon](./media/user-guide/fx-events/image45.png)</span></span>

<span data-ttu-id="f9a9f-767">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-767">**Description**</span></span>

<span data-ttu-id="f9a9f-768">Den här händelsen representerar en händelsen fil namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-768">This event represents a file rename event.</span></span>

<span data-ttu-id="f9a9f-769">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-769">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-770">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-770">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-771">Info fält 2: pekar mot gammalt fil namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-771">Info Field 2: Pointer to old file name.</span></span>
- <span data-ttu-id="f9a9f-772">Info-fält 3: pekar på nytt fil namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-772">Info Field 3: Pointer to new file name.</span></span>
- <span data-ttu-id="f9a9f-773">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-773">Info Field 4: Not used.</span></span>

### <a name="file-seek"></a><span data-ttu-id="f9a9f-774">Fil sökning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-774">File Seek</span></span> 

#### <a name="fx_file_seek"></a><span data-ttu-id="f9a9f-775">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="f9a9f-775">fx_file_seek</span></span>

<span data-ttu-id="f9a9f-776">**Ikonen** ![ Fil Sök ikon](./media/user-guide/fx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-776">**Icon** ![File seek icon](./media/user-guide/fx-events/image46.png)</span></span>

<span data-ttu-id="f9a9f-777">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-777">**Description**</span></span>

<span data-ttu-id="f9a9f-778">Den här händelsen representerar en fil söknings händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-778">This event represents a file seek event.</span></span>

<span data-ttu-id="f9a9f-779">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-779">**Information Fields**</span></span> 

- <span data-ttu-id="f9a9f-780">Info fält 1: pekar mot filen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-780">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="f9a9f-781">Informations fält 2: byte förskjutning.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-781">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="f9a9f-782">Info-fält 3: föregående offset.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-782">Info Field 3: Previous offset.</span></span>
- <span data-ttu-id="f9a9f-783">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-783">Info Field 4: Not used.</span></span>

### <a name="file-truncate"></a><span data-ttu-id="f9a9f-784">Filen trunkeras</span><span class="sxs-lookup"><span data-stu-id="f9a9f-784">File Truncate</span></span> 

#### <a name="fx_file_truncate"></a><span data-ttu-id="f9a9f-785">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="f9a9f-785">fx_file_truncate</span></span>

<span data-ttu-id="f9a9f-786">**Ikonen** ![ Ikon för fil trunkering](./media/user-guide/fx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-786">**Icon** ![File truncate icon](./media/user-guide/fx-events/image47.png)</span></span>

<span data-ttu-id="f9a9f-787">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-787">**Description**</span></span>

<span data-ttu-id="f9a9f-788">Den här händelsen representerar en fil trunkerar händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-788">This event represents a file truncate event.</span></span>

<span data-ttu-id="f9a9f-789">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-789">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-790">Info fält 1: pekar mot filen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-790">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="f9a9f-791">Informations fält 2: begärd storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-791">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="f9a9f-792">Info-fält 3: föregående storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-792">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="f9a9f-793">Info fält 4: ny storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-793">Info Field 4: New size.</span></span>

### <a name="file-truncate-release"></a><span data-ttu-id="f9a9f-794">Frigör fil trunkerad</span><span class="sxs-lookup"><span data-stu-id="f9a9f-794">File Truncate Release</span></span> 

#### <a name="fx_file_truncate_release"></a><span data-ttu-id="f9a9f-795">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="f9a9f-795">fx_file_truncate_release</span></span> 

<span data-ttu-id="f9a9f-796">**Ikonen** ![ Ikonen för att trunkera en fil](./media/user-guide/fx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-796">**Icon** ![File truncate release icon](./media/user-guide/fx-events/image48.png)</span></span>

<span data-ttu-id="f9a9f-797">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-797">**Description**</span></span>

<span data-ttu-id="f9a9f-798">Den här händelsen representerar en fil trunkerar händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-798">This event represents a file truncate release event.</span></span>

<span data-ttu-id="f9a9f-799">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-799">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-800">Info fält 1: pekar mot filen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-800">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="f9a9f-801">Informations fält 2: begärd storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-801">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="f9a9f-802">Info-fält 3: föregående storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-802">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="f9a9f-803">Info fält 4: ny storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-803">Info Field 4: New size.</span></span>

### <a name="file-write"></a><span data-ttu-id="f9a9f-804">Fil skrivning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-804">File Write</span></span> 

#### <a name="fx_file_write"></a><span data-ttu-id="f9a9f-805">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="f9a9f-805">fx_file_write</span></span> 

<span data-ttu-id="f9a9f-806">**Ikonen** ![ Fil skrivnings ikon](./media/user-guide/fx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-806">**Icon** ![File write icon](./media/user-guide/fx-events/image49.png)</span></span>

<span data-ttu-id="f9a9f-807">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-807">**Description**</span></span>

<span data-ttu-id="f9a9f-808">Den här händelsen representerar en fil skrivnings händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-808">This event represents a file write event.</span></span>

<span data-ttu-id="f9a9f-809">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-809">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-810">Info fält 1: pekar mot filen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-810">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="f9a9f-811">Info fält 2: buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-811">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="f9a9f-812">Info-fält 3: begär ande storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-812">Info Field 3: Request size.</span></span>
- <span data-ttu-id="f9a9f-813">Info fält 4: den faktiska storlek som skrivits.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-813">Info Field 4: Actual size written.</span></span>

### <a name="media-abort"></a><span data-ttu-id="f9a9f-814">Medie avbrott</span><span class="sxs-lookup"><span data-stu-id="f9a9f-814">Media Abort</span></span> 

#### <a name="fx_media_abort"></a><span data-ttu-id="f9a9f-815">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="f9a9f-815">fx_media_abort</span></span> 

<span data-ttu-id="f9a9f-816">**Ikonen** ![ Ikon för medie avbrott](./media/user-guide/fx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-816">**Icon** ![Media abort icon](./media/user-guide/fx-events/image50.png)</span></span>

<span data-ttu-id="f9a9f-817">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-817">**Description**</span></span>

<span data-ttu-id="f9a9f-818">Den här händelsen representerar ett avbrotts händelse för media.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-818">This event represents a media abort event.</span></span>

<span data-ttu-id="f9a9f-819">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-819">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-820">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-820">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-821">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-821">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f9a9f-822">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-822">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-823">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-823">Info Field 4: Not used.</span></span>

### <a name="media-cache-invalidate"></a><span data-ttu-id="f9a9f-824">Ogiltig cachelagring av media</span><span class="sxs-lookup"><span data-stu-id="f9a9f-824">Media Cache Invalidate</span></span>

#### <a name="fx_media_cache_invalidate"></a><span data-ttu-id="f9a9f-825">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="f9a9f-825">fx_media_cache_invalidate</span></span>

<span data-ttu-id="f9a9f-826">**Ikonen** ![ Ikon för att verifiera medie cache](./media/user-guide/fx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-826">**Icon** ![Media cache invalidate icon](./media/user-guide/fx-events/image51.png)</span></span>

<span data-ttu-id="f9a9f-827">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-827">**Description**</span></span>

<span data-ttu-id="f9a9f-828">Den här händelsen representerar en händelse i medie cachen som är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-828">This event represents a media cache invalidate event.</span></span>

<span data-ttu-id="f9a9f-829">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-829">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-830">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-830">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-831">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-831">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f9a9f-832">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-832">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-833">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-833">Info Field 4: Not used.</span></span>

### <a name="media-check"></a><span data-ttu-id="f9a9f-834">Medie kontroll</span><span class="sxs-lookup"><span data-stu-id="f9a9f-834">Media Check</span></span> 

#### <a name="fx_media_check"></a><span data-ttu-id="f9a9f-835">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="f9a9f-835">fx_media_check</span></span>

<span data-ttu-id="f9a9f-836">**Ikonen** ![ Ikon för medie kontroll](./media/user-guide/fx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-836">**Icon** ![Media check icon](./media/user-guide/fx-events/image52.png)</span></span>

<span data-ttu-id="f9a9f-837">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-837">**Description**</span></span>

<span data-ttu-id="f9a9f-838">Den här händelsen representerar en medie kontroll händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-838">This event represents a media check event.</span></span>

<span data-ttu-id="f9a9f-839">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-839">**Information Fields**</span></span> 

- <span data-ttu-id="f9a9f-840">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-840">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-841">Info fält 2: Scratch-minnes pekare.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-841">Info Field 2: Scratch memory pointer.</span></span>
- <span data-ttu-id="f9a9f-842">Info fält 3: minnes storlek för virtuellt minne.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-842">Info Field 3: Scratch memory size.</span></span>
- <span data-ttu-id="f9a9f-843">Informations fält 4: fel-bitars mappning:</span><span class="sxs-lookup"><span data-stu-id="f9a9f-843">Info Field 4: Errors bit map:</span></span>

  | <span data-ttu-id="f9a9f-844">Typ av fel</span><span class="sxs-lookup"><span data-stu-id="f9a9f-844">Error type</span></span>                        | <span data-ttu-id="f9a9f-845">Värde</span><span class="sxs-lookup"><span data-stu-id="f9a9f-845">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="f9a9f-846">Fel i FAT-kedja</span><span class="sxs-lookup"><span data-stu-id="f9a9f-846">FAT Chain Error</span></span>                  | <span data-ttu-id="f9a9f-847">0x01</span><span class="sxs-lookup"><span data-stu-id="f9a9f-847">(0x01)</span></span>  |
  |  <span data-ttu-id="f9a9f-848">Katalog fel</span><span class="sxs-lookup"><span data-stu-id="f9a9f-848">Directory Error</span></span>                  | <span data-ttu-id="f9a9f-849">protokollnumret 0x02</span><span class="sxs-lookup"><span data-stu-id="f9a9f-849">(0x02)</span></span>  |
  |  <span data-ttu-id="f9a9f-850">Fel i förlorad kluster</span><span class="sxs-lookup"><span data-stu-id="f9a9f-850">Lost Cluster Error</span></span>               | <span data-ttu-id="f9a9f-851">(0x04)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-851">(0x04)</span></span>  |
  |  <span data-ttu-id="f9a9f-852">Fil storleks fel</span><span class="sxs-lookup"><span data-stu-id="f9a9f-852">File Size Error</span></span>                  | <span data-ttu-id="f9a9f-853">(0x08)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-853">(0x08)</span></span>  |

### <a name="media-close"></a><span data-ttu-id="f9a9f-854">Medie stängning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-854">Media Close</span></span> 

#### <a name="fx_media_close"></a><span data-ttu-id="f9a9f-855">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="f9a9f-855">fx_media_close</span></span>

<span data-ttu-id="f9a9f-856">**Ikonen** ![ Ikon för medie stängning](./media/user-guide/fx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-856">**Icon** ![Media Close icon](./media/user-guide/fx-events/image53.png)</span></span>

<span data-ttu-id="f9a9f-857">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-857">**Description**</span></span>

<span data-ttu-id="f9a9f-858">Den här händelsen representerar en medie stängnings händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-858">This event represents a media close event.</span></span>

<span data-ttu-id="f9a9f-859">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-859">**Information Fields**</span></span> 

- <span data-ttu-id="f9a9f-860">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-860">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-861">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-861">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f9a9f-862">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-862">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-863">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-863">Info Field 4: Not used.</span></span>

### <a name="media-flush"></a><span data-ttu-id="f9a9f-864">Medie tömning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-864">Media Flush</span></span> 

#### <a name="fx_media_flush"></a><span data-ttu-id="f9a9f-865">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="f9a9f-865">fx_media_flush</span></span>

<span data-ttu-id="f9a9f-866">**Ikonen** ![ Ikon för medie tömning](./media/user-guide/fx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-866">**Icon** ![Media flush icon](./media/user-guide/fx-events/image54.png)</span></span>

<span data-ttu-id="f9a9f-867">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-867">**Description**</span></span>

<span data-ttu-id="f9a9f-868">Den här händelsen representerar en händelse för medie tömning.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-868">This event represents a media flush event.</span></span>

<span data-ttu-id="f9a9f-869">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-869">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-870">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-870">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-871">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-871">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f9a9f-872">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-872">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-873">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-873">Info Field 4: Not used.</span></span>

### <a name="media-format"></a><span data-ttu-id="f9a9f-874">Medie format</span><span class="sxs-lookup"><span data-stu-id="f9a9f-874">Media Format</span></span> 

#### <a name="fx_media_format"></a><span data-ttu-id="f9a9f-875">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="f9a9f-875">fx_media_format</span></span>

<span data-ttu-id="f9a9f-876">**Ikonen** ![ Ikon för medie format](./media/user-guide/fx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-876">**Icon** ![Media format icon](./media/user-guide/fx-events/image55.png)</span></span>

<span data-ttu-id="f9a9f-877">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-877">**Description**</span></span>

<span data-ttu-id="f9a9f-878">Den här händelsen representerar en medie format händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-878">This event represents a media format event.</span></span>

<span data-ttu-id="f9a9f-879">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-879">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-880">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-880">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-881">Informations fält 2: antal rot poster.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-881">Info Field 2: Number of root entries.</span></span>
- <span data-ttu-id="f9a9f-882">Info-fält 3: sektorer.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-882">Info Field 3: Sectors.</span></span>
- <span data-ttu-id="f9a9f-883">Info fält 4: sektorer per kluster.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-883">Info Field 4: Sectors per cluster.</span></span>

### <a name="media-open"></a><span data-ttu-id="f9a9f-884">Mediet är öppet</span><span class="sxs-lookup"><span data-stu-id="f9a9f-884">Media Open</span></span> 

#### <a name="fx_media_open"></a><span data-ttu-id="f9a9f-885">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="f9a9f-885">fx_media_open</span></span>

<span data-ttu-id="f9a9f-886">**Ikonen** ![ Medie öppnings ikon](./media/user-guide/fx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-886">**Icon** ![Media open icon](./media/user-guide/fx-events/image56.png)</span></span>

<span data-ttu-id="f9a9f-887">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-887">**Description**</span></span>

<span data-ttu-id="f9a9f-888">Den här händelsen representerar en medie öppnings händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-888">This event represents a media open event.</span></span>

<span data-ttu-id="f9a9f-889">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-889">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-890">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-890">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-891">Info fält 2: pekare till medie driv rutins post.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-891">Info Field 2: Pointer to media driver entry.</span></span>
- <span data-ttu-id="f9a9f-892">Informations fält 3: minnes pekare.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-892">Info Field 3: Memory pointer.</span></span>
- <span data-ttu-id="f9a9f-893">Info fält 4: minnes storlek.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-893">Info Field 4: Memory size.</span></span>

### <a name="media-read-media-read"></a><span data-ttu-id="f9a9f-894">Läst Media läsning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-894">Media Read Media Read</span></span> 

#### <a name="fx_media_read"></a><span data-ttu-id="f9a9f-895">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="f9a9f-895">fx_media_read</span></span>

<span data-ttu-id="f9a9f-896">**Ikonen** ![ Medie läsnings ikon](./media/user-guide/fx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-896">**Icon** ![Media read icon](./media/user-guide/fx-events/image57.png)</span></span>

<span data-ttu-id="f9a9f-897">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-897">**Description**</span></span>

<span data-ttu-id="f9a9f-898">Den här händelsen representerar en medie läsnings händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-898">This event represents a media read event.</span></span>

<span data-ttu-id="f9a9f-899">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-899">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-900">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-900">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-901">Info fält 2: logisk sektor.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-901">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="f9a9f-902">Info-fält 3: buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-902">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="f9a9f-903">Info fält 4: lästa byte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-903">Info Field 4: Bytes read.</span></span>

### <a name="media-space-available"></a><span data-ttu-id="f9a9f-904">Tillgängligt medie utrymme</span><span class="sxs-lookup"><span data-stu-id="f9a9f-904">Media Space Available</span></span> 

#### <a name="fx_media_space_available"></a><span data-ttu-id="f9a9f-905">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="f9a9f-905">fx_media_space_available</span></span>

<span data-ttu-id="f9a9f-906">**Ikonen** ![ Ikon för tillgängligt medie utrymme](./media/user-guide/fx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-906">**Icon** ![Media space available icon](./media/user-guide/fx-events/image58.png)</span></span>

<span data-ttu-id="f9a9f-907">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-907">**Description**</span></span>

<span data-ttu-id="f9a9f-908">Den här händelsen representerar en händelse för medie utrymme som är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-908">This event represents a media space available event.</span></span>

<span data-ttu-id="f9a9f-909">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-909">**Information Fields**</span></span> 

- <span data-ttu-id="f9a9f-910">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-910">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-911">Informations fält 2: tillgängliga byte-pekare.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-911">Info Field 2: Available bytes pointer.</span></span>
- <span data-ttu-id="f9a9f-912">Informations fält 3: antal lediga kluster.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-912">Info Field 3: Number of free clusters.</span></span>
- <span data-ttu-id="f9a9f-913">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-913">Info Field 4: Not used.</span></span>

### <a name="media-volume-get"></a><span data-ttu-id="f9a9f-914">Hämta medie volym</span><span class="sxs-lookup"><span data-stu-id="f9a9f-914">Media Volume Get</span></span> 

#### <a name="fx_media_volume_get"></a><span data-ttu-id="f9a9f-915">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="f9a9f-915">fx_media_volume_get</span></span>

<span data-ttu-id="f9a9f-916">**Ikonen** ![ Ikon för Hämta medie volym](./media/user-guide/fx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-916">**Icon** ![Media volume get icon](./media/user-guide/fx-events/image59.png)</span></span>

<span data-ttu-id="f9a9f-917">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-917">**Description**</span></span>

<span data-ttu-id="f9a9f-918">Den här händelsen representerar en händelse för medie volym get.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-918">This event represents a media volume get event.</span></span>

<span data-ttu-id="f9a9f-919">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-919">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-920">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-920">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-921">Info fält 2: pekar på volym namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-921">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="f9a9f-922">Info-fält 3: volym källa.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-922">Info Field 3: Volume source.</span></span>
- <span data-ttu-id="f9a9f-923">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-923">Info Field 4: Not used.</span></span>

### <a name="media-volume-set"></a><span data-ttu-id="f9a9f-924">Medie volym uppsättning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-924">Media Volume Set</span></span> 

#### <a name="fx_media_volume_set"></a><span data-ttu-id="f9a9f-925">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="f9a9f-925">fx_media_volume_set</span></span>

<span data-ttu-id="f9a9f-926">**Ikonen** ![ Ikon för medie volym uppsättning](./media/user-guide/fx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-926">**Icon** ![Media volume set icon](./media/user-guide/fx-events/image60.png)</span></span>

<span data-ttu-id="f9a9f-927">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-927">**Description**</span></span>

<span data-ttu-id="f9a9f-928">Den här händelsen representerar en händelse för en medie volym uppsättning.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-928">This event represents a media volume set event.</span></span>

<span data-ttu-id="f9a9f-929">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-929">**Information Fields**</span></span> 
- <span data-ttu-id="f9a9f-930">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-930">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-931">Info fält 2: pekar på volym namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-931">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="f9a9f-932">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-932">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-933">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-933">Info Field 4: Not used.</span></span>

### <a name="media-write"></a><span data-ttu-id="f9a9f-934">Medie skrivning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-934">Media Write</span></span> 

#### <a name="fx_media_write"></a><span data-ttu-id="f9a9f-935">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="f9a9f-935">fx_media_write</span></span>

<span data-ttu-id="f9a9f-936">**Ikonen** ![ Ikon för medie skrivning](./media/user-guide/fx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-936">**Icon** ![Media write icon](./media/user-guide/fx-events/image61.png)</span></span>

<span data-ttu-id="f9a9f-937">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-937">**Description**</span></span>

<span data-ttu-id="f9a9f-938">Den här händelsen representerar en medie Skriv händelse.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-938">This event represents a media write event.</span></span>

<span data-ttu-id="f9a9f-939">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-939">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-940">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-940">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-941">Info fält 2: logisk sektor.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-941">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="f9a9f-942">Info-fält 3: buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-942">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="f9a9f-943">Info fält 4: skrivna byte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-943">Info Field 4: Bytes written.</span></span>

### <a name="system-date-get"></a><span data-ttu-id="f9a9f-944">System datum get</span><span class="sxs-lookup"><span data-stu-id="f9a9f-944">System Date Get</span></span> 

#### <a name="fx_system_date_get"></a><span data-ttu-id="f9a9f-945">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="f9a9f-945">fx_system_date_get</span></span> 

<span data-ttu-id="f9a9f-946">**Ikonen** ![ Ikonen system datum get](./media/user-guide/fx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-946">**Icon** ![System date get icon](./media/user-guide/fx-events/image62.png)</span></span>

<span data-ttu-id="f9a9f-947">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-947">**Description**</span></span>

<span data-ttu-id="f9a9f-948">Den här händelsen representerar en händelse för system datum get.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-948">This event represents a system date get event.</span></span>

<span data-ttu-id="f9a9f-949">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-949">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-950">Informations fält 1: år.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-950">Info Field 1: Year.</span></span>
- <span data-ttu-id="f9a9f-951">Info fält 2: månad.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-951">Info Field 2: Month.</span></span>
- <span data-ttu-id="f9a9f-952">Info-fält 3: dag.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-952">Info Field 3: Day.</span></span>
- <span data-ttu-id="f9a9f-953">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-953">Info Field 4: Not used.</span></span>

### <a name="system-date-set"></a><span data-ttu-id="f9a9f-954">System datum uppsättning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-954">System Date Set</span></span> 

#### <a name="fx_system_date_set"></a><span data-ttu-id="f9a9f-955">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="f9a9f-955">fx_system_date_set</span></span> 

<span data-ttu-id="f9a9f-956">**Ikonen** ![ Ikon för system datum uppsättning](./media/user-guide/fx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-956">**Icon** ![System date set icon](./media/user-guide/fx-events/image63.png)</span></span>

<span data-ttu-id="f9a9f-957">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-957">**Description**</span></span>

<span data-ttu-id="f9a9f-958">Den här händelsen representerar en händelse för system datum uppsättning.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-958">This event represents a system date set event.</span></span>

<span data-ttu-id="f9a9f-959">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-959">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-960">Informations fält 1: år.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-960">Info Field 1: Year.</span></span>
- <span data-ttu-id="f9a9f-961">Info fält 2: månad.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-961">Info Field 2: Month.</span></span>
- <span data-ttu-id="f9a9f-962">Info-fält 3: dag.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-962">Info Field 3: Day.</span></span>
- <span data-ttu-id="f9a9f-963">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-963">Info Field 4: Not used.</span></span>

### <a name="system-initialize"></a><span data-ttu-id="f9a9f-964">System initiering</span><span class="sxs-lookup"><span data-stu-id="f9a9f-964">System Initialize</span></span> 

#### <a name="fx_system_initialize"></a><span data-ttu-id="f9a9f-965">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="f9a9f-965">fx_system_initialize</span></span> 

<span data-ttu-id="f9a9f-966">**Ikonen** ![ Ikon för system initiering](./media/user-guide/fx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-966">**Icon** ![System initialize icon](./media/user-guide/fx-events/image64.png)</span></span>

<span data-ttu-id="f9a9f-967">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-967">**Description**</span></span>

<span data-ttu-id="f9a9f-968">Den här händelsen representerar en händelse som startar om systemet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-968">This event represents a system initialize event.</span></span>

<span data-ttu-id="f9a9f-969">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-969">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-970">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-970">Info Field 1: Not used.</span></span>
- <span data-ttu-id="f9a9f-971">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-971">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f9a9f-972">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-972">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-973">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-973">Info Field 4: Not used.</span></span>

### <a name="system-time-get"></a><span data-ttu-id="f9a9f-974">Hämta system tid</span><span class="sxs-lookup"><span data-stu-id="f9a9f-974">System Time Get</span></span> 

#### <a name="fx_system_time_get"></a><span data-ttu-id="f9a9f-975">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="f9a9f-975">fx_system_time_get</span></span> 

<span data-ttu-id="f9a9f-976">**Ikonen** ![ Ikonen system tid get](./media/user-guide/fx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-976">**Icon** ![System time get icon](./media/user-guide/fx-events/image65.png)</span></span>

<span data-ttu-id="f9a9f-977">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-977">**Description**</span></span>

<span data-ttu-id="f9a9f-978">Den här händelsen representerar en händelse för system tid get.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-978">This event represents a system time get event.</span></span>

<span data-ttu-id="f9a9f-979">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-979">**Information Fields**</span></span> 

- <span data-ttu-id="f9a9f-980">Informations fält 1: timme.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-980">Info Field 1: Hour.</span></span>
- <span data-ttu-id="f9a9f-981">Info fält 2: minute.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-981">Info Field 2: Minute.</span></span>
- <span data-ttu-id="f9a9f-982">Info-fält 3: sekund.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-982">Info Field 3: Second.</span></span>
- <span data-ttu-id="f9a9f-983">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-983">Info Field 4: Not used.</span></span>

### <a name="system-time-set"></a><span data-ttu-id="f9a9f-984">System tids uppsättning</span><span class="sxs-lookup"><span data-stu-id="f9a9f-984">System Time Set</span></span> 

#### <a name="fx_system_time_set"></a><span data-ttu-id="f9a9f-985">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="f9a9f-985">fx_system_time_set</span></span> 

<span data-ttu-id="f9a9f-986">**Ikonen** ![ Ikon för system tids uppsättning](./media/user-guide/fx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-986">**Icon** ![System time set icon](./media/user-guide/fx-events/image66.png)</span></span>

<span data-ttu-id="f9a9f-987">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-987">**Description**</span></span>

<span data-ttu-id="f9a9f-988">Den här händelsen representerar en händelse för system tids uppsättning.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-988">This event represents a system time set event.</span></span>

<span data-ttu-id="f9a9f-989">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-989">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-990">Informations fält 1: timme.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-990">Info Field 1: Hour.</span></span>
- <span data-ttu-id="f9a9f-991">Info fält 2: minute.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-991">Info Field 2: Minute.</span></span>
- <span data-ttu-id="f9a9f-992">Info-fält 3: sekund.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-992">Info Field 3: Second.</span></span>
- <span data-ttu-id="f9a9f-993">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-993">Info Field 4: Not used.</span></span>

### <a name="unicode-directory-create"></a><span data-ttu-id="f9a9f-994">Skapa Unicode-katalog</span><span class="sxs-lookup"><span data-stu-id="f9a9f-994">Unicode Directory Create</span></span> 

#### <a name="fx_unicode_directory_create"></a><span data-ttu-id="f9a9f-995">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="f9a9f-995">fx_unicode_directory_create</span></span> 

<span data-ttu-id="f9a9f-996">**Ikonen** ![ Ikon för att skapa Unicode-katalogen](./media/user-guide/fx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-996">**Icon** ![Unicode directory create icon](./media/user-guide/fx-events/image67.png)</span></span>

<span data-ttu-id="f9a9f-997">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-997">**Description**</span></span>

<span data-ttu-id="f9a9f-998">Den här händelsen representerar en händelse för att skapa Unicode-katalogen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-998">This event represents a Unicode directory create event.</span></span>

<span data-ttu-id="f9a9f-999">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-999">**Information Fields**</span></span> 

- <span data-ttu-id="f9a9f-1000">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1000">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-1001">Info fält 2: pekar mot Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1001">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="f9a9f-1002">Informations fält 3: storlek på Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1002">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="f9a9f-1003">Info fält 4: pekar mot kort namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1003">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-directory-rename"></a><span data-ttu-id="f9a9f-1004">Byt namn på Unicode-katalog</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1004">Unicode Directory Rename</span></span> 

#### <a name="fx_unicode_directory_rename"></a><span data-ttu-id="f9a9f-1005">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1005">fx_unicode_directory_rename</span></span>

<span data-ttu-id="f9a9f-1006">**Ikonen** ![ Ikon för byte i Unicode-katalog](./media/user-guide/fx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1006">**Icon** ![Unicode directory rename icon](./media/user-guide/fx-events/image68.png)</span></span>

<span data-ttu-id="f9a9f-1007">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1007">**Description**</span></span>

<span data-ttu-id="f9a9f-1008">Den här händelsen representerar en byte-händelse i Unicode-katalogen.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1008">This event represents a Unicode directory rename event.</span></span>

<span data-ttu-id="f9a9f-1009">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1009">**Information Fields**</span></span> 

- <span data-ttu-id="f9a9f-1010">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1010">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-1011">Info fält 2: pekar mot Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1011">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="f9a9f-1012">Informations fält 3: storlek på Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1012">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="f9a9f-1013">Info fält 4: pekar mot kort namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1013">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-create"></a><span data-ttu-id="f9a9f-1014">Skapa Unicode-fil</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1014">Unicode File Create</span></span> 

#### <a name="fx_unicode_file_create"></a><span data-ttu-id="f9a9f-1015">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1015">fx_unicode_file_create</span></span>

<span data-ttu-id="f9a9f-1016">**Ikonen** ![ Ikon för att skapa Unicode-fil](./media/user-guide/fx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1016">**Icon** ![Unicode file create icon](./media/user-guide/fx-events/image69.png)</span></span>

<span data-ttu-id="f9a9f-1017">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1017">**Description**</span></span>

<span data-ttu-id="f9a9f-1018">Den här händelsen representerar en händelse för att skapa Unicode-filer.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1018">This event represents a Unicode file create event.</span></span>

<span data-ttu-id="f9a9f-1019">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1019">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-1020">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1020">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-1021">Info fält 2: pekar mot Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1021">Info Field 2: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="f9a9f-1022">Informations fält 3: storlek på Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1022">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="f9a9f-1023">Info fält 4: pekar mot kort namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1023">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-rename"></a><span data-ttu-id="f9a9f-1024">Byt namn på Unicode-fil</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1024">Unicode File Rename</span></span> 

#### <a name="fx_unicode_file_rename"></a><span data-ttu-id="f9a9f-1025">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1025">fx_unicode_file_rename</span></span>

<span data-ttu-id="f9a9f-1026">**Ikonen** ![ Ikon för byte av Unicode-fil](./media/user-guide/fx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1026">**Icon** ![Unicode file rename icon](./media/user-guide/fx-events/image70.png)</span></span>

<span data-ttu-id="f9a9f-1027">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1027">**Description**</span></span>

<span data-ttu-id="f9a9f-1028">Den här händelsen representerar en händelse för byte av Unicode-fil.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1028">This event represents a Unicode file rename event.</span></span>

<span data-ttu-id="f9a9f-1029">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1029">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-1030">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1030">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-1031">Info fält 2: pekar mot Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1031">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="f9a9f-1032">Informations fält 3: storlek på Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1032">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="f9a9f-1033">Info fält 4: pekar mot kort namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1033">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-length-get"></a><span data-ttu-id="f9a9f-1034">Unicode-längd Hämta</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1034">Unicode Length Get</span></span> 

#### <a name="fx_unicode_length_get"></a><span data-ttu-id="f9a9f-1035">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1035">fx_unicode_length_get</span></span>

<span data-ttu-id="f9a9f-1036">**Ikonen** ![ Hämta ikon för Unicode-längd](./media/user-guide/fx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1036">**Icon** ![Unicode length get icon](./media/user-guide/fx-events/image71.png)</span></span>

<span data-ttu-id="f9a9f-1037">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1037">**Description**</span></span>

<span data-ttu-id="f9a9f-1038">Den här händelsen representerar en händelse med Unicode-längd.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1038">This event represents a Unicode length get event.</span></span>

<span data-ttu-id="f9a9f-1039">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1039">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-1040">Informations fält 1: pekar mot Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1040">Info Field 1: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="f9a9f-1041">Informations fält 2: längd.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1041">Info Field 2: Length.</span></span>
- <span data-ttu-id="f9a9f-1042">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1042">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f9a9f-1043">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1043">Info Field 4: Not used.</span></span>

### <a name="unicode-name-get"></a><span data-ttu-id="f9a9f-1044">Hämta Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1044">Unicode Name Get</span></span> 

#### <a name="fx_unicode_name_get"></a><span data-ttu-id="f9a9f-1045">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1045">fx_unicode_name_get</span></span>

<span data-ttu-id="f9a9f-1046">**Ikonen** ![ Ikon för att hämta Unicode-namn](./media/user-guide/fx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1046">**Icon** ![Unicode name get icon](./media/user-guide/fx-events/image72.png)</span></span>

<span data-ttu-id="f9a9f-1047">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1047">**Description**</span></span>

<span data-ttu-id="f9a9f-1048">Den här händelsen representerar en händelse av Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1048">This event represents a Unicode name get event.</span></span>

<span data-ttu-id="f9a9f-1049">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1049">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-1050">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1050">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-1051">Info-fält 2: kort källans namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1051">Info Field 2: Source short name.</span></span>
- <span data-ttu-id="f9a9f-1052">Info-fält 3: målets Unicode-namn pekare.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1052">Info Field 3: Destination Unicode name pointer.</span></span>
- <span data-ttu-id="f9a9f-1053">Info-fält 4: målets Unicode-namn längd.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1053">Info Field 4: Destination Unicode name length.</span></span>

### <a name="unicode-short-name-get"></a><span data-ttu-id="f9a9f-1054">Korta Unicode-namn Hämta</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1054">Unicode Short Name Get</span></span> 

#### <a name="fx_unicode_short_name_get"></a><span data-ttu-id="f9a9f-1055">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1055">fx_unicode_short_name_get</span></span>

<span data-ttu-id="f9a9f-1056">**Ikonen** ![ Ikon för kort namn för Unicode-namn](./media/user-guide/fx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1056">**Icon** ![Unicode short name get icon](./media/user-guide/fx-events/image73.png)</span></span>

<span data-ttu-id="f9a9f-1057">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1057">**Description**</span></span>

<span data-ttu-id="f9a9f-1058">Den här händelsen representerar en händelse för ett kort för att hämta Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1058">This event represents a Unicode short name get event.</span></span>

<span data-ttu-id="f9a9f-1059">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1059">**Information Fields**</span></span>

- <span data-ttu-id="f9a9f-1060">Informations fält 1: pekar mot mediet.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1060">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="f9a9f-1061">Info fält 2: pekare till käll-Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1061">Info Field 2: Pointer to source Unicode name.</span></span>
- <span data-ttu-id="f9a9f-1062">Informations fält 3: längd på Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1062">Info Field 3: Length of Unicode name.</span></span>
- <span data-ttu-id="f9a9f-1063">Info fält 4: pekar mot kort namn.</span><span class="sxs-lookup"><span data-stu-id="f9a9f-1063">Info Field 4: Pointer to short name.</span></span>