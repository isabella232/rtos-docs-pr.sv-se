---
title: Förstå Azure återställnings tider-FileX
description: Azure återställnings tider FileX är ett FAT-kompatibelt (File Allocation Table)-kompatibelt fil system som är fullständigt integrerat med Azure återställnings tider-ThreadX och är tillgängligt för alla processorer som stöds. Precis som med Azure återställnings tider-ThreadX är Azure återställnings tider FileX utformad för att ha ett litet utrymme och höga prestanda, vilket gör det perfekt för dagens djupt inbäddade program som kräver fil hanterings åtgärder. FileX stöder de flesta fysiska media, inklusive RAM-, Azure återställnings tider-USBX, SD-kort och NAND/eller Flash-minnen via Azure återställnings tider LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a3a20c8ced3426399ceedf6994c872ce7aec93c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827321"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="0441a-105">Översikt över Azure återställnings tider-FileX</span><span class="sxs-lookup"><span data-stu-id="0441a-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="0441a-106">Azure återställnings tider FileX Embedded File System är Azure återställnings TIDERs Advanced, lösning för industriella klasser för Microsoft FAT-filformat, särskilt utformad för djupt inbäddade, real tids-och IoT-program.</span><span class="sxs-lookup"><span data-stu-id="0441a-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="0441a-107">Azure återställnings tider-FileX har stöd för alla Microsofts fil format, inklusive FAT12, FAT16, FAT32 och exFAT.</span><span class="sxs-lookup"><span data-stu-id="0441a-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="0441a-108">FileX erbjuder också valfri fel tolerans och blixt slitage via en tilläggs produkt som kallas [Azure återställnings tider LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span><span class="sxs-lookup"><span data-stu-id="0441a-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="0441a-109">Allt detta kombinerat med en liten storlek, snabb körning och överlägsen enkel användning, gör Azure återställnings tider FileX det idealiska valet för de mest krävande inbäddade IoT-programmen.</span><span class="sxs-lookup"><span data-stu-id="0441a-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="0441a-110">API-protokoll</span><span class="sxs-lookup"><span data-stu-id="0441a-110">API protocols</span></span>

### <a name="azure-rtos-filex-api"></a><span data-ttu-id="0441a-111">Azure återställnings tider FileX-API</span><span class="sxs-lookup"><span data-stu-id="0441a-111">Azure RTOS FileX API</span></span>

- <span data-ttu-id="0441a-112">Intuitiv och konsekvent API</span><span class="sxs-lookup"><span data-stu-id="0441a-112">Intuitive and consistent API</span></span>
- <span data-ttu-id="0441a-113">Substantiv-namn konvention för verb</span><span class="sxs-lookup"><span data-stu-id="0441a-113">Noun-verb naming convention</span></span>
- <span data-ttu-id="0441a-114">Alla API: er har ledande *fx_* för att enkelt identifiera som FileX</span><span class="sxs-lookup"><span data-stu-id="0441a-114">All APIs have leading *fx_* to easily identify as FileX</span></span>
- <span data-ttu-id="0441a-115">Blockering av API: er har valfri tråd-timeout</span><span class="sxs-lookup"><span data-stu-id="0441a-115">Blocking APIs have optional thread timeout</span></span>
- <span data-ttu-id="0441a-116">Valfria återanrop för användar meddelanden för medie-och fil åtgärder</span><span class="sxs-lookup"><span data-stu-id="0441a-116">Optional user-notification callbacks for media and file operations</span></span>
- <span data-ttu-id="0441a-117">Mer information finns i [användar handboken för Azure återställnings tider FileX](about-this-guide.md) .</span><span class="sxs-lookup"><span data-stu-id="0441a-117">Please see [Azure RTOS FileX User Guide](about-this-guide.md) for more details</span></span>

### <a name="media-services"></a><span data-ttu-id="0441a-118">Media Services</span><span class="sxs-lookup"><span data-stu-id="0441a-118">Media Services</span></span>

- <span data-ttu-id="0441a-119">Stöd för FAT 12/16/32 och exFAT</span><span class="sxs-lookup"><span data-stu-id="0441a-119">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="0441a-120">Minimalt 6KB FLASH, 2,5 KB RAM</span><span class="sxs-lookup"><span data-stu-id="0441a-120">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="0441a-121">Slutför Media Access Services</span><span class="sxs-lookup"><span data-stu-id="0441a-121">Complete media access services</span></span>
- <span data-ttu-id="0441a-122">Obegränsat antal medie instanser</span><span class="sxs-lookup"><span data-stu-id="0441a-122">Unlimited number of media instance</span></span>
- <span data-ttu-id="0441a-123">Enkelt Läs/skriv-gränssnitt för logisk sektor driv rutin</span><span class="sxs-lookup"><span data-stu-id="0441a-123">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="0441a-124">Stöd för flera partitioner</span><span class="sxs-lookup"><span data-stu-id="0441a-124">Multiple partition support</span></span>
- <span data-ttu-id="0441a-125">Logisk sektor cache</span><span class="sxs-lookup"><span data-stu-id="0441a-125">Logical sector cache</span></span>
- <span data-ttu-id="0441a-126">Cache för FAT-post</span><span class="sxs-lookup"><span data-stu-id="0441a-126">FAT entry cache</span></span>
- <span data-ttu-id="0441a-127">Tillval fel tolerans support</span><span class="sxs-lookup"><span data-stu-id="0441a-127">Optional fault tolerance support</span></span>
- <span data-ttu-id="0441a-128">Uppskjuten sekundär FAT-uppdatering</span><span class="sxs-lookup"><span data-stu-id="0441a-128">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="0441a-129">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="0441a-129">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="0441a-130">Intuitiva API: er för medie åtkomst, inklusive:</span><span class="sxs-lookup"><span data-stu-id="0441a-130">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="0441a-131">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="0441a-131">fx_media_open</span></span>
  - <span data-ttu-id="0441a-132">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="0441a-132">fx_media_close</span></span>
  - <span data-ttu-id="0441a-133">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="0441a-133">fx_media_format</span></span>
  - <span data-ttu-id="0441a-134">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="0441a-134">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="0441a-135">Katalog tjänster</span><span class="sxs-lookup"><span data-stu-id="0441a-135">Directory Services</span></span>

- <span data-ttu-id="0441a-136">Upp till 256 byte-sökvägar</span><span class="sxs-lookup"><span data-stu-id="0441a-136">Up to 256 byte paths</span></span>
- <span data-ttu-id="0441a-137">Långa och 8,3 Katalog namn stöds</span><span class="sxs-lookup"><span data-stu-id="0441a-137">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="0441a-138">Ta bort katalog skapa &</span><span class="sxs-lookup"><span data-stu-id="0441a-138">Directory create & delete</span></span>
- <span data-ttu-id="0441a-139">Katalog navigering och-Traversal</span><span class="sxs-lookup"><span data-stu-id="0441a-139">Directory navigation and traversal</span></span>
- <span data-ttu-id="0441a-140">Hantering av katalogattribut</span><span class="sxs-lookup"><span data-stu-id="0441a-140">Directory attributes management</span></span>
- <span data-ttu-id="0441a-141">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="0441a-141">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="0441a-142">Intuitiva API: er för katalog åtkomst, inklusive:</span><span class="sxs-lookup"><span data-stu-id="0441a-142">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="0441a-143">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="0441a-143">fx_directory_create</span></span>
  - <span data-ttu-id="0441a-144">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="0441a-144">fx_directory_delete</span></span>
  - <span data-ttu-id="0441a-145">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="0441a-145">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="0441a-146">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="0441a-146">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="0441a-147">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="0441a-147">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="0441a-148">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="0441a-148">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="0441a-149">Filtjänster</span><span class="sxs-lookup"><span data-stu-id="0441a-149">File Services</span></span>

- <span data-ttu-id="0441a-150">Minimalt 3,3 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="0441a-150">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="0441a-151">Obegränsade öppna filer</span><span class="sxs-lookup"><span data-stu-id="0441a-151">Unlimited open files</span></span>
- <span data-ttu-id="0441a-152">Skrivskyddade filer kan öppnas flera gånger</span><span class="sxs-lookup"><span data-stu-id="0441a-152">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="0441a-153">Långa och 8,3 Katalog namn stöds</span><span class="sxs-lookup"><span data-stu-id="0441a-153">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="0441a-154">Stöd för sammanhängande filer</span><span class="sxs-lookup"><span data-stu-id="0441a-154">Contiguous file support</span></span>
- <span data-ttu-id="0441a-155">Snabb söknings logik</span><span class="sxs-lookup"><span data-stu-id="0441a-155">Fast seek logic</span></span>
- <span data-ttu-id="0441a-156">För tilldelning av kluster</span><span class="sxs-lookup"><span data-stu-id="0441a-156">Pre-allocation of clusters</span></span>
- <span data-ttu-id="0441a-157">Skapa, ta bort och Byt namn på filen</span><span class="sxs-lookup"><span data-stu-id="0441a-157">File create, delete, and rename</span></span>
- <span data-ttu-id="0441a-158">Läsa, skriva och se fil</span><span class="sxs-lookup"><span data-stu-id="0441a-158">File read, write, and see</span></span>
- <span data-ttu-id="0441a-159">Hantering av filattribut</span><span class="sxs-lookup"><span data-stu-id="0441a-159">File attributes management</span></span>
- <span data-ttu-id="0441a-160">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="0441a-160">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="0441a-161">Intuitiva API: er för fil åtkomst, inklusive:</span><span class="sxs-lookup"><span data-stu-id="0441a-161">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="0441a-162">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="0441a-162">fx_file_create</span></span>
  - <span data-ttu-id="0441a-163">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="0441a-163">fx_file_delete</span></span>
  - <span data-ttu-id="0441a-164">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="0441a-164">fx_file_attributes_set</span></span>
  - <span data-ttu-id="0441a-165">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="0441a-165">fx_file_attributes_read</span></span>
  - <span data-ttu-id="0441a-166">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="0441a-166">fx_file_read</span></span>
  - <span data-ttu-id="0441a-167">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="0441a-167">fx_file_seek</span></span>
  - <span data-ttu-id="0441a-168">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="0441a-168">fx_file_write</span></span>

## <a name="small-footprint"></a><span data-ttu-id="0441a-169">Små</span><span class="sxs-lookup"><span data-stu-id="0441a-169">Small-footprint</span></span>

<span data-ttu-id="0441a-170">Azure återställnings tider FileX Embedded File System har ett remarkably litet minimalt utrymme på 8,6 KB till 12 KB för grundläggande läsning/skrivning av filer.</span><span class="sxs-lookup"><span data-stu-id="0441a-170">Azure RTOS FileX embedded file system has a remarkably small minimal footprint of 8.6 KB to 12 KB for basic file read/write support.</span></span> <span data-ttu-id="0441a-171">Minimalt antal Azure återställnings tider FileX RAM-användning är i ordningen 1,8 KB för en Media instans och endast en 512-byte logisk sektor cache.</span><span class="sxs-lookup"><span data-stu-id="0441a-171">Minimal Azure RTOS FileX RAM usage is on the order of 1.8 KB for one media instance and with only a 512-byte logical sector cache.</span></span> <span data-ttu-id="0441a-172">Precis som Azure återställnings tider ThreadX skalas storleken på Azure återställnings tider-FileX automatiskt utifrån de tjänster som används av programmet.</span><span class="sxs-lookup"><span data-stu-id="0441a-172">Like Azure RTOS ThreadX, the size of Azure RTOS FileX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="0441a-173">Detta eliminerar behovet av komplicerade konfigurations-och build-parametrar, vilket gör det lättare för utvecklaren att göra något.</span><span class="sxs-lookup"><span data-stu-id="0441a-173">This virtually eliminates the need for complicated configuration and builds parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="0441a-174">Snabb körning</span><span class="sxs-lookup"><span data-stu-id="0441a-174">Fast execution</span></span>

<span data-ttu-id="0441a-175">Azure återställnings tider FileX tillhandahåller en logisk sektor och cache för FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="0441a-175">Azure RTOS FileX provides a logical sector cache as well as a FAT entry cache.</span></span> <span data-ttu-id="0441a-176">Storlekarna för båda är direkt kontroll över programmet.</span><span class="sxs-lookup"><span data-stu-id="0441a-176">The sizes of both are under direct control of the application.</span></span> <span data-ttu-id="0441a-177">Dessutom tillhandahåller Azure återställnings tider-FileX sammanhängande kluster tilldelning och direkt kluster läsning och skrivning i följd.</span><span class="sxs-lookup"><span data-stu-id="0441a-177">In addition, Azure RTOS FileX provides contiguous cluster allocation and direct consecutive cluster reading and writing.</span></span> <span data-ttu-id="0441a-178">Läs-och skriv förfrågningar för hela sektorer görs direkt mellan programbufferten och mediet, vilket innebär att ingen mellanlagring görs.</span><span class="sxs-lookup"><span data-stu-id="0441a-178">Read/write requests of whole sectors are done directly between the application buffer and the media – that is, no intermediate buffering is done.</span></span> <span data-ttu-id="0441a-179">Allt detta och en allmän prestanda orienterad design filosofi hjälper Azure återställnings tider FileX att uppnå snabbast möjliga prestanda.</span><span class="sxs-lookup"><span data-stu-id="0441a-179">All of this and a general performance-oriented design philosophy helps Azure RTOS FileX achieve the fastest possible performance.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="0441a-180">Avancerad teknik</span><span class="sxs-lookup"><span data-stu-id="0441a-180">Advanced technology</span></span>

<span data-ttu-id="0441a-181">Azure återställnings tider-FileX är avancerad teknik, inklusive följande.</span><span class="sxs-lookup"><span data-stu-id="0441a-181">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="0441a-182">Stöd för FAT 12/16/32 och exFAT</span><span class="sxs-lookup"><span data-stu-id="0441a-182">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="0441a-183">Stöd för flera partitioner</span><span class="sxs-lookup"><span data-stu-id="0441a-183">Multiple partition support</span></span>
- <span data-ttu-id="0441a-184">Automatisk skalning</span><span class="sxs-lookup"><span data-stu-id="0441a-184">Automatic scaling</span></span>
- <span data-ttu-id="0441a-185">Endian-neutral</span><span class="sxs-lookup"><span data-stu-id="0441a-185">Endian neutral</span></span>
- <span data-ttu-id="0441a-186">Långt fil namn och 8,3-stöd</span><span class="sxs-lookup"><span data-stu-id="0441a-186">Long file name and 8.3 support</span></span>
- <span data-ttu-id="0441a-187">Tillval fel tolerans support</span><span class="sxs-lookup"><span data-stu-id="0441a-187">Optional fault tolerance support</span></span>
- <span data-ttu-id="0441a-188">Logisk sektor cache</span><span class="sxs-lookup"><span data-stu-id="0441a-188">Logical sector cache</span></span>
- <span data-ttu-id="0441a-189">Cache för FAT-post</span><span class="sxs-lookup"><span data-stu-id="0441a-189">FAT entry cache</span></span>
- <span data-ttu-id="0441a-190">För tilldelning av kluster</span><span class="sxs-lookup"><span data-stu-id="0441a-190">Pre-allocation of clusters</span></span>
- <span data-ttu-id="0441a-191">Stöd för sammanhängande filer</span><span class="sxs-lookup"><span data-stu-id="0441a-191">Contiguous file support</span></span>
- <span data-ttu-id="0441a-192">Valfria prestanda mått</span><span class="sxs-lookup"><span data-stu-id="0441a-192">Optional performance metrics</span></span>
- <span data-ttu-id="0441a-193">Azure återställnings tider TraceX system Analysis support</span><span class="sxs-lookup"><span data-stu-id="0441a-193">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="0441a-194">ELLER/NAND slitage (Azure återställnings tider LevelX)</span><span class="sxs-lookup"><span data-stu-id="0441a-194">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="0441a-195">Azure återställnings tider-LevelX är Microsofts eller/NAND FLASH slitage-produkt.</span><span class="sxs-lookup"><span data-stu-id="0441a-195">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="0441a-196">Azure återställnings tider LevelX kan användas tillsammans med FileX eller som ett fristående, direkt Läs-och skrivbart FLASH sektor bibliotek för programmet.</span><span class="sxs-lookup"><span data-stu-id="0441a-196">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="0441a-197">Snabbast tid till marknad</span><span class="sxs-lookup"><span data-stu-id="0441a-197">Fastest time-to-market</span></span>

<span data-ttu-id="0441a-198">Azure återställnings tider FileX är enkelt att installera, lära sig, använda, felsöka, verifiera, certifiera och underhålla.</span><span class="sxs-lookup"><span data-stu-id="0441a-198">Azure RTOS FileX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="0441a-199">Därför är Azure återställnings tider FileX ett av de mest populära FAT-filsystemen för inbäddade IoT-enheter.</span><span class="sxs-lookup"><span data-stu-id="0441a-199">As a result, Azure RTOS FileX is one of the most popular FAT file systems for embedded IoT devices.</span></span> <span data-ttu-id="0441a-200">Följande är några av orsakerna till vår konsekventa tids-till-marknad-fördel:</span><span class="sxs-lookup"><span data-stu-id="0441a-200">The following are some reasons for our consistent time-to-market advantage:</span></span>

- <span data-ttu-id="0441a-201">Kvalitets dokumentation – Läs vår [Användar handbok för Azure återställnings tider FileX](about-this-guide.md) och se själv!</span><span class="sxs-lookup"><span data-stu-id="0441a-201">Quality Documentation – please review our [Azure RTOS FileX User Guide](about-this-guide.md) and see for yourself!</span></span>
- <span data-ttu-id="0441a-202">Fullständig käll kods tillgänglighet</span><span class="sxs-lookup"><span data-stu-id="0441a-202">Complete Source Code Availability</span></span>
- <span data-ttu-id="0441a-203">Lätt att använda API</span><span class="sxs-lookup"><span data-stu-id="0441a-203">Easy-to-use API</span></span>
- <span data-ttu-id="0441a-204">Omfattande och avancerad funktions uppsättning</span><span class="sxs-lookup"><span data-stu-id="0441a-204">Comprehensive and Advanced Feature Set</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="0441a-205">Förcertifierat av TUV och UL till många säkerhets standarder</span><span class="sxs-lookup"><span data-stu-id="0441a-205">Pre-certified  by TUV and UL to many safety standards</span></span>

![SGS – TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

<span data-ttu-id="0441a-207">Azure återställnings tider FileX har certifierats av SGS-TUV Saar för användning i säkerhets kritiska system, enligt IEC-61508 SIL 4, IEC-62304 SW säkerhets klass C, ISO 26262 ASIL D och EN 50128.</span><span class="sxs-lookup"><span data-stu-id="0441a-207">Azure RTOS FileX has been certified by SGS-TUV Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="0441a-208">Certifieringen bekräftar att FileX kan användas i utvecklingen av säkerhetsrelaterad program vara för högsta säkerhets integritets nivå för IEC-61508, IEC-62304, ISO 26262 och EN 50128 för "fungerande säkerhet för elektriska, elektroniska och programmerbara elektroniskt säkerhetsrelaterade system".</span><span class="sxs-lookup"><span data-stu-id="0441a-208">The certification confirms that FileX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="0441a-209">SGS – TUV Saar, som bildas genom ett gemensamt venture i Tyskland SGS-Group och TUV Saarland, har blivit det ledande ackrediterade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad program vara för säkerhetsrelaterade system i hela världen.</span><span class="sxs-lookup"><span data-stu-id="0441a-209">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="0441a-210">Den industriella säkerhets standarden IEC 61508, och alla standarder som är härledda från IT, inklusive IEC-62304, ISO 26262 och EN 50128, används för att säkerställa den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, process kontroll system, industriella maskiner, bilar och järnvägs styrnings system.</span><span class="sxs-lookup"><span data-stu-id="0441a-210">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles, and railway control systems.</span></span>

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="CRU UL-certifiering":::

<span data-ttu-id="0441a-212">Azure återställnings tider FileX har erkänts av UL för att följa UL 60730-1 bilaga H, CSA E60730-1 bilaga H, IEC 60730-1 bilaga H, UL 60335-1 Bilaga R, IEC 60335-1 Bilaga R och UL 1998 säkerhets standarder för program vara i programmerbara komponenter.</span><span class="sxs-lookup"><span data-stu-id="0441a-212">Azure RTOS FileX has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="0441a-213">UL är ett globalt, oberoende, säkerhets vetenskaps företag med mer än en Century av expertis som förnyar säkerhetslösningar, från det offentliga införandet av elektricitet till genombrott i hållbarhet, förnybar energi och Nanotechnology.</span><span class="sxs-lookup"><span data-stu-id="0441a-213">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

<span data-ttu-id="0441a-214">Artefakter (certifikat, säkerhets hand bok, test rapport osv.) som är associerade med TUV och UL-certifieringar är tillgängliga för försäljning.</span><span class="sxs-lookup"><span data-stu-id="0441a-214">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="0441a-215">I de fall där programmet behöver ytterligare certifiering, är en certifierings tjänst tillgänglig via Microsoft för att tillhandahålla certifierings certifiering till olika standarder med hjälp av den aktuella maskin varu plattformen och till och med program koden.</span><span class="sxs-lookup"><span data-stu-id="0441a-215">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="0441a-216">En enkel licens</span><span class="sxs-lookup"><span data-stu-id="0441a-216">One Simple License</span></span>

<span data-ttu-id="0441a-217">Det kostar inget att använda och testa käll koden och ingen kostnad för produktions licenser när de distribueras till förinstallerade enheter, men alla andra enheter behöver en enkel årlig licens.</span><span class="sxs-lookup"><span data-stu-id="0441a-217">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="0441a-218">Fullständig käll kod med högsta kvalitet</span><span class="sxs-lookup"><span data-stu-id="0441a-218">Full, highest-quality source code</span></span>

<span data-ttu-id="0441a-219">Under åren har FileX-källkod angett kvalitet och enkel förståelse.</span><span class="sxs-lookup"><span data-stu-id="0441a-219">Throughout the years, FileX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="0441a-220">Dessutom tillhandahåller konventionen om en funktion per fil för enkel käll navigering.</span><span class="sxs-lookup"><span data-stu-id="0441a-220">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="0441a-221">Har stöd för de flesta populära arkitekturerna</span><span class="sxs-lookup"><span data-stu-id="0441a-221">Supports most popular architectures</span></span>

<span data-ttu-id="0441a-222">Azure återställnings tider-FileX körs på de flesta populära 32/64-bitars mikroprocessorer, färdiga, fullständigt testade och fullt stödda, inklusive följande:</span><span class="sxs-lookup"><span data-stu-id="0441a-222">Azure RTOS FileX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="0441a-223">**Analoga enheter**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="0441a-223">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="0441a-224">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="0441a-224">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="0441a-225">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="0441a-225">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="0441a-226">**Arm**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitars/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="0441a-226">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="0441a-227">**Takt**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="0441a-227">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="0441a-228">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="0441a-228">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="0441a-229">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="0441a-229">**Cypress**: RISC-V</span></span>

<span data-ttu-id="0441a-230">**Kiseldioxid**: ESI – RISC</span><span class="sxs-lookup"><span data-stu-id="0441a-230">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="0441a-231">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="0441a-231">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="0441a-232">**Intel**; **Intel FPGA**: X36/Pentium, XSCALE, Nios II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="0441a-232">**Intel**; **Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="0441a-233">**Mikrochip**: avr32, ARM7, ARM9, cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/sa, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="0441a-233">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="0441a-234">**Mikrohalv**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="0441a-234">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="0441a-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, coldfire, Kinetis cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="0441a-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="0441a-236">**Renesas**: SH, HS, V850, RX, RZ, synergieffekt</span><span class="sxs-lookup"><span data-stu-id="0441a-236">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="0441a-237">**Silicon** Labb: EFM32</span><span class="sxs-lookup"><span data-stu-id="0441a-237">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="0441a-238">**Sammanfattning**: båge 600, 700, båge EM, båg HS</span><span class="sxs-lookup"><span data-stu-id="0441a-238">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="0441a-239">**St**: STM32, ARM7, ARM9, cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="0441a-239">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="0441a-240">**TL**: C5xxx, C6xxx, Stellaris, Sitara, tiva-C</span><span class="sxs-lookup"><span data-stu-id="0441a-240">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="0441a-241">**Wave-bearbetning**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="0441a-241">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="0441a-242">**Xilinx**: mikroblixt, powerpc 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="0441a-242">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="0441a-243">*Alla tids gränser och storleks värden i listan är uppskattningar och kan skilja sig åt på din utvecklings plattform.*</span><span class="sxs-lookup"><span data-stu-id="0441a-243">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
