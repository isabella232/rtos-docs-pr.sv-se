---
title: Kapitel 2 – Azure återställnings tider USBX Host stack-installation
description: Lär dig hur du installerar USBX-värds Tacken.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 4c33f95b8ac268c557fd947a1303ec3af315a37e
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377092"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a><span data-ttu-id="c7456-103">Kapitel 2 – Azure återställnings tider USBX Host stack-installation</span><span class="sxs-lookup"><span data-stu-id="c7456-103">Chapter 2 - Azure RTOS USBX Host Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="c7456-104">Värd överväganden</span><span class="sxs-lookup"><span data-stu-id="c7456-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="c7456-105">Typ av dator</span><span class="sxs-lookup"><span data-stu-id="c7456-105">Computer Type</span></span>

<span data-ttu-id="c7456-106">Inbäddad utveckling utförs vanligt vis på Windows-datorer eller UNIX-värddatorer.</span><span class="sxs-lookup"><span data-stu-id="c7456-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="c7456-107">När programmet har kompilerats, länkats och finns på värden laddas den ned till mål maskin varan för körning.</span><span class="sxs-lookup"><span data-stu-id="c7456-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="c7456-108">Hämta gränssnitt</span><span class="sxs-lookup"><span data-stu-id="c7456-108">Download Interfaces</span></span>

<span data-ttu-id="c7456-109">Normalt görs mål nedladdningen via ett seriellt RS-232-gränssnitt, även om Parallel Interfaces, USB och Ethernet blir mer populära.</span><span class="sxs-lookup"><span data-stu-id="c7456-109">Usually, the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="c7456-110">I utvecklings verktygets dokumentation finns tillgängliga alternativ.</span><span class="sxs-lookup"><span data-stu-id="c7456-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="c7456-111">Fel söknings verktyg</span><span class="sxs-lookup"><span data-stu-id="c7456-111">Debugging Tools</span></span>

<span data-ttu-id="c7456-112">Fel sökning sker vanligt vis via samma länk som nedladdningen av program avbildningen.</span><span class="sxs-lookup"><span data-stu-id="c7456-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="c7456-113">Det finns en mängd olika fel söknings program som sträcker sig från små övervakningsprogram som körs på målet genom BDM-verktyg (Background debug Monitor) och In-Circuit emulator (ICE).</span><span class="sxs-lookup"><span data-stu-id="c7456-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="c7456-114">Verktyget ICE ger den mest robusta fel sökningen av faktisk mål maskin vara.</span><span class="sxs-lookup"><span data-stu-id="c7456-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="c7456-115">Nödvändigt hårddisk utrymme</span><span class="sxs-lookup"><span data-stu-id="c7456-115">Required Hard Disk Space</span></span>

<span data-ttu-id="c7456-116">Käll koden för USBX levereras i ASCII-format och kräver cirka 500 KB utrymme på värddatorns hård disk.</span><span class="sxs-lookup"><span data-stu-id="c7456-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="c7456-117">Mål överväganden</span><span class="sxs-lookup"><span data-stu-id="c7456-117">Target Considerations</span></span>

<span data-ttu-id="c7456-118">USBX kräver mellan 24 och 64 KB av skrivskyddat minne (ROM) på målet i värd läge.</span><span class="sxs-lookup"><span data-stu-id="c7456-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="c7456-119">Mängden minne som krävs beror på vilken typ av styrenhet som används och vilka USB-klasser som är kopplade till USBX.</span><span class="sxs-lookup"><span data-stu-id="c7456-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="c7456-120">En annan 32 KByte av målets RAM-minne (Random Access Memory) krävs för USBX globala data strukturer och minneskonfigurationer.</span><span class="sxs-lookup"><span data-stu-id="c7456-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="c7456-121">Den här mediepoolen kan också justeras beroende på det förväntade antalet enheter på USB-enheten och typen av USB-styrenhet.</span><span class="sxs-lookup"><span data-stu-id="c7456-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="c7456-122">Enhets sidan för USBX kräver ungefär 10-12 kB ROM beroende på typ av enhets styrenhet.</span><span class="sxs-lookup"><span data-stu-id="c7456-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="c7456-123">Användningen av RAM-minnet beror på vilken typ av klass som emuleras av enheten.</span><span class="sxs-lookup"><span data-stu-id="c7456-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="c7456-124">USBX förlitar sig även på ThreadX-semaforer, mutexer och trådar för flera tråd skydd och I/O-inskjutningar och regelbunden bearbetning för övervakning av USB-bussens topologi.</span><span class="sxs-lookup"><span data-stu-id="c7456-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="c7456-125">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="c7456-125">Product Distribution</span></span>

<span data-ttu-id="c7456-126">Azure återställnings tider-USBX kan hämtas från vår offentliga käll kods lagrings plats på <https://github.com/azure-rtos/usbx/> .</span><span class="sxs-lookup"><span data-stu-id="c7456-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="c7456-127">Följande är en lista över flera viktiga filer i lagrings platsen:</span><span class="sxs-lookup"><span data-stu-id="c7456-127">The following is a list of several important files in the repository:</span></span>

- <span data-ttu-id="c7456-128">***ux_api. h***: den här C-huvudfilen innehåller alla system likställda, data strukturer och tjänst prototyper.</span><span class="sxs-lookup"><span data-stu-id="c7456-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
- <span data-ttu-id="c7456-129">***ux_port. h***: den här C-huvudfilen innehåller alla data definitioner och strukturer för utveckling-verktyg.</span><span class="sxs-lookup"><span data-stu-id="c7456-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
- <span data-ttu-id="c7456-130">***UX. lib***: det här är den binära versionen av USBX C-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="c7456-130">***ux.lib***: This is the binary version of the USBX C library.</span></span> <span data-ttu-id="c7456-131">Den distribueras med standard paketet.</span><span class="sxs-lookup"><span data-stu-id="c7456-131">It is distributed with the standard package.</span></span>
- <span data-ttu-id="c7456-132">***demo_usbx. c***: c-filen som innehåller en enkel USBX-demo</span><span class="sxs-lookup"><span data-stu-id="c7456-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="c7456-133">Alla fil namn är i gemener.</span><span class="sxs-lookup"><span data-stu-id="c7456-133">All filenames are in lower-case.</span></span> <span data-ttu-id="c7456-134">Den här namngivnings konventionen gör det lättare att konvertera kommandon till UNIX-utvecklings plattformar.</span><span class="sxs-lookup"><span data-stu-id="c7456-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="c7456-135">USBX-installation</span><span class="sxs-lookup"><span data-stu-id="c7456-135">USBX Installation</span></span>

<span data-ttu-id="c7456-136">USBX installeras genom att klona GitHub-lagringsplatsen till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c7456-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="c7456-137">Följande är en typisk syntax för att skapa en klon av USBX-lagringsplatsen på din dator:</span><span class="sxs-lookup"><span data-stu-id="c7456-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```powershell
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="c7456-138">Alternativt kan du ladda ned en kopia av lagrings platsen med hjälp av knappen Ladda ned på GitHub-huvud sidan.</span><span class="sxs-lookup"><span data-stu-id="c7456-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="c7456-139">Du hittar också instruktioner för att skapa USBX-biblioteket på den första sidan i online-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="c7456-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="c7456-140">Följande allmänna instruktioner gäller för i princip vilken installation som helst:</span><span class="sxs-lookup"><span data-stu-id="c7456-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="c7456-141">Använd samma katalog som du tidigare installerade ThreadX på värd hård disken.</span><span class="sxs-lookup"><span data-stu-id="c7456-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="c7456-142">Alla USBX namn är unika och påverkar inte den tidigare USBX-installationen.</span><span class="sxs-lookup"><span data-stu-id="c7456-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
2. <span data-ttu-id="c7456-143">Lägg till ett anrop till \***ux_system_initialize** _ i eller nära början av _ *_tx_application_define_.* \* Det är här som USBX-resurserna initieras.</span><span class="sxs-lookup"><span data-stu-id="c7456-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _ *_tx_application_define_.** This is where the USBX resources are initialized.</span></span>
3. <span data-ttu-id="c7456-144">Lägg till ett anrop till \*\**ux_host_stack_initialize *.**</span><span class="sxs-lookup"><span data-stu-id="c7456-144">Add a call to \***ux_host_stack_initialize\*.**</span></span>
4. <span data-ttu-id="c7456-145">Lägg till ett eller flera anrop för att initiera nödvändiga USBX.</span><span class="sxs-lookup"><span data-stu-id="c7456-145">Add one or more calls to initialize the required USBX.</span></span>
5. <span data-ttu-id="c7456-146">Lägg till ett eller flera anrop för att initiera de värd styrenheter som är tillgängliga i systemet.</span><span class="sxs-lookup"><span data-stu-id="c7456-146">Add one or more calls to initialize the host controllers available in the system.</span></span>
6. <span data-ttu-id="c7456-147">Du kan behöva ändra filen tx_low_level_initialize. c för att kunna lägga till maskin varu initiering på låg nivå och avbryta vektor routning.</span><span class="sxs-lookup"><span data-stu-id="c7456-147">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="c7456-148">Detta är särskilt för maskin varu plattformen och kommer inte att diskuteras här.</span><span class="sxs-lookup"><span data-stu-id="c7456-148">This is specific to the hardware platform and will not be discussed here.</span></span>
7. <span data-ttu-id="c7456-149">Kompilera program käll koden och länka med USBX-och ThreadX-körnings biblioteken (FileX och/eller netx kan också krävas om klassen för USB-lagring och/eller USB-nätverksanslutningar ska kompileras), UX. a (eller UX. lib) och TX. a (eller TX. lib).</span><span class="sxs-lookup"><span data-stu-id="c7456-149">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="c7456-150">Resultatet kan hämtas till målet och köras.</span><span class="sxs-lookup"><span data-stu-id="c7456-150">The resulting can be downloaded to the target and executed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="c7456-151">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="c7456-151">Configuration Options</span></span>

<span data-ttu-id="c7456-152">Det finns flera konfigurations alternativ för att skapa USBX-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="c7456-152">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="c7456-153">Alla alternativ finns i ***ux_user. h***.</span><span class="sxs-lookup"><span data-stu-id="c7456-153">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="c7456-154">I listan nedan beskrivs varje konfigurations alternativ.</span><span class="sxs-lookup"><span data-stu-id="c7456-154">The list below details each configuration option.</span></span>


- <span data-ttu-id="c7456-155">**UX_PERIODIC_RATE**: det här värdet anger hur många Tick per sekund för en viss maskin varu plattform.</span><span class="sxs-lookup"><span data-stu-id="c7456-155">**UX_PERIODIC_RATE**: This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="c7456-156">Standardvärdet är 1000 som anger ett Tick per millisekund.</span><span class="sxs-lookup"><span data-stu-id="c7456-156">The default is 1000 indicating one tick per millisecond.</span></span>
- <span data-ttu-id="c7456-157">**UX_MAX_CLASS_DRIVER**: det här värdet är det maximala antalet klasser som kan läsas in av USBX.</span><span class="sxs-lookup"><span data-stu-id="c7456-157">**UX_MAX_CLASS_DRIVER**: This value is the maximum number of classes that can be loaded by USBX.</span></span> <span data-ttu-id="c7456-158">Det här värdet representerar klass behållaren och inte antalet instanser av en klass.</span><span class="sxs-lookup"><span data-stu-id="c7456-158">This value represents the class container and not the number of instances of a class.</span></span> <span data-ttu-id="c7456-159">Om till exempel en viss implementering av USBX behöver klassen Hub, klassen skrivare och lagrings klassen, kan UX_MAX_CLASS_DRIVER svärdet anges till 3 oavsett hur många enheter som tillhör dessa klasser.</span><span class="sxs-lookup"><span data-stu-id="c7456-159">For instance, if a particular implementation of USBX needs the hub class, the printer class, and the storage class, then the UX_MAX_CLASS_DRIVER value can be set to 3 regardless of the number of devices that belong to these classes.</span></span>
- <span data-ttu-id="c7456-160">**UX_MAX_HCD**: det här värdet representerar antalet olika värd styrenheter som är tillgängliga i systemet.</span><span class="sxs-lookup"><span data-stu-id="c7456-160">**UX_MAX_HCD**: This value represents the number of different host controllers that are available in the system.</span></span> <span data-ttu-id="c7456-161">För USB 1,1-stöd blir det här värdet 1.</span><span class="sxs-lookup"><span data-stu-id="c7456-161">For USB 1.1 support, this value will mostly be 1.</span></span> <span data-ttu-id="c7456-162">För USB 2,0-stöd kan det här värdet vara större än 1.</span><span class="sxs-lookup"><span data-stu-id="c7456-162">For USB 2.0 support this value can be more than 1.</span></span> <span data-ttu-id="c7456-163">Det här värdet representerar antalet samtidiga värd styrenheter som körs på samma gång.</span><span class="sxs-lookup"><span data-stu-id="c7456-163">This value represents the number of concurrent host controllers running at the same time.</span></span> <span data-ttu-id="c7456-164">Om det till exempel finns två instanser av OHCI som körs eller en EHCI och en OHCI-styrenhet som kör, ska UX_MAX_HCD vara inställd på 2.</span><span class="sxs-lookup"><span data-stu-id="c7456-164">If for instance, there are two instances of OHCI running or one EHCI and one OHCI controllers running, the UX_MAX_HCD should be set to 2.</span></span> 
- <span data-ttu-id="c7456-165">**UX_MAX_DEVICES**: det här värdet representerar det maximala antalet enheter som kan kopplas till USB-enheten.</span><span class="sxs-lookup"><span data-stu-id="c7456-165">**UX_MAX_DEVICES**: This value represents the maximum number of devices that can be attached to the USB.</span></span> <span data-ttu-id="c7456-166">Normalt är det teoretiska maximala antalet på en enda USB 127-enheter.</span><span class="sxs-lookup"><span data-stu-id="c7456-166">Normally, the theoretical maximum number on a single USB is 127 devices.</span></span> <span data-ttu-id="c7456-167">Det här värdet kan skalas ned för att spara minne.</span><span class="sxs-lookup"><span data-stu-id="c7456-167">This value can be scaled down to conserve memory.</span></span> <span data-ttu-id="c7456-168">Det bör noteras att det här värdet representerar det totala antalet enheter oavsett antalet USB-bussar i systemet.</span><span class="sxs-lookup"><span data-stu-id="c7456-168">It should be noted that this value represents the total number of devices regardless of the number of USB buses in the system.</span></span>
- <span data-ttu-id="c7456-169">**UX_MAX_ED**: det här värdet representerar det maximala antalet EDs i Controller-poolen.</span><span class="sxs-lookup"><span data-stu-id="c7456-169">**UX_MAX_ED**: This value represents the maximum number of EDs in the controller pool.</span></span> <span data-ttu-id="c7456-170">Det här numret tilldelas endast en kontrollant.</span><span class="sxs-lookup"><span data-stu-id="c7456-170">This number is assigned to one controller only.</span></span> <span data-ttu-id="c7456-171">Om det finns flera instanser av kontrollanter används det här värdet av varje enskild kontrollant.</span><span class="sxs-lookup"><span data-stu-id="c7456-171">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="c7456-172">**UX_MAX_TD och UX_MAX_ISO_TD**: det här värdet representerar det maximala antalet vanliga och isokrona TDS i Controller-poolen.</span><span class="sxs-lookup"><span data-stu-id="c7456-172">**UX_MAX_TD and UX_MAX_ISO_TD**: This value represents the maximum number of regular and isochronous TDs in the controller pool.</span></span> <span data-ttu-id="c7456-173">Det här numret tilldelas endast en kontrollant.</span><span class="sxs-lookup"><span data-stu-id="c7456-173">This number is assigned to one controller only.</span></span> <span data-ttu-id="c7456-174">Om det finns flera instanser av kontrollanter används det här värdet av varje enskild kontrollant.</span><span class="sxs-lookup"><span data-stu-id="c7456-174">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="c7456-175">**UX_THREAD_STACK_SIZE**: det här värdet är storleken på stacken i byte för USBX-trådar.</span><span class="sxs-lookup"><span data-stu-id="c7456-175">**UX_THREAD_STACK_SIZE**: This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="c7456-176">Det kan vara vanligt vis 1024 byte eller 2048 byte beroende på vilken processor som används och värd styrenheten.</span><span class="sxs-lookup"><span data-stu-id="c7456-176">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span>
- <span data-ttu-id="c7456-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: det här värdet är stack storleken för uppräknings tråden för USB-värden.</span><span class="sxs-lookup"><span data-stu-id="c7456-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: This value is the stack size of the USB host enumeration thread.</span></span> <span data-ttu-id="c7456-178">Om den här symbolen inte är inställd anges USBX som **UX_THREAD_STACK_SIZE**.</span><span class="sxs-lookup"><span data-stu-id="c7456-178">If this symbol I not set, the USBX host enumeration thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span> 
- <span data-ttu-id="c7456-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: det här värdet är stack storleken för USB-VÄRDENS HCD-tråd.</span><span class="sxs-lookup"><span data-stu-id="c7456-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: This value is the stack size of the USB host HCD thread.</span></span> <span data-ttu-id="c7456-180">Om den här symbolen inte är inställd, anges USBX Host HCD tråd stack-storlek till **UX_THREAD_STACK_SIZE**.</span><span class="sxs-lookup"><span data-stu-id="c7456-180">If this symbol I not set, the USBX host HCD thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span>
- <span data-ttu-id="c7456-181">**UX_THREAD_PRIORITY_ENUM**: det här är prioritet svärdet för THREADX för USBX-uppräknings trådar som övervakar buss sto pol Ogin.</span><span class="sxs-lookup"><span data-stu-id="c7456-181">**UX_THREAD_PRIORITY_ENUM**: This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span>
- <span data-ttu-id="c7456-182">**UX_THREAD_PRIORITY_CLASS**: det här är prioritet svärdet för ThreadX för standard trådarna för USBX.</span><span class="sxs-lookup"><span data-stu-id="c7456-182">**UX_THREAD_PRIORITY_CLASS**: This is the ThreadX priority value for the standard USBX threads.</span></span>
- <span data-ttu-id="c7456-183">**UX_THREAD_PRIORITY_KEYBOARD**: det här är prioritet svärdet för THREADX för HID-tangentbordet för USBX.</span><span class="sxs-lookup"><span data-stu-id="c7456-183">**UX_THREAD_PRIORITY_KEYBOARD**: This is the ThreadX priority value for the USBX HID keyboard class.</span></span>
- <span data-ttu-id="c7456-184">**UX_THREAD_PRIORITY_HCD**: Detta är prioritet svärdet för ThreadX för värd styrenhets tråden.</span><span class="sxs-lookup"><span data-stu-id="c7456-184">**UX_THREAD_PRIORITY_HCD**: This is the ThreadX priority value for the host controller thread.</span></span>
- <span data-ttu-id="c7456-185">**UX_NO_TIME_SLICE**: det här värdet definierar i själva verket den tids sektor som ska användas för trådar.</span><span class="sxs-lookup"><span data-stu-id="c7456-185">**UX_NO_TIME_SLICE**: This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="c7456-186">Om t. ex. har definierats till 0 används inte tids segment i ThreadX Target-porten.</span><span class="sxs-lookup"><span data-stu-id="c7456-186">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span>
- <span data-ttu-id="c7456-187">**UX_MAX_HOST_LUN**: det här värdet representerar det maximala antalet SCSI-logiska enheter som representeras i värd lagrings klass driv rutinen.</span><span class="sxs-lookup"><span data-stu-id="c7456-187">**UX_MAX_HOST_LUN**: This value represents the maximum number of SCSI logical units represented in the host storage class driver.</span></span>
- <span data-ttu-id="c7456-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: om det här värdet är definierat innehåller det här värdet kod för hantering av lagrings enheter som använder CB-eller CBI-protokollet (t. ex. disketter).</span><span class="sxs-lookup"><span data-stu-id="c7456-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: If defined, this value includes code to handle storage devices that use the CB or CBI protocol (such as floppy disks).</span></span> <span data-ttu-id="c7456-189">Den är inaktive rad som standard eftersom dessa protokoll är föråldrade och ersätts av protokollet enbart Mass transport (BOT), vilket praktiskt taget alla moderna lagrings enheter använder.</span><span class="sxs-lookup"><span data-stu-id="c7456-189">It is off by default because these protocols are obsolete, being superseded by the Bulk Only Transport (BOT protocol, which virtually all modern storage devices use.</span></span>
- <span data-ttu-id="c7456-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: om det här värdet har definierats gör det här värdet ux_host_class_hid_keyboard_key_get till att bara rapportera viktiga ändringar, tangenttryckningar och viktiga versioner.</span><span class="sxs-lookup"><span data-stu-id="c7456-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: If defined, this value causes ux_host_class_hid_keyboard_key_get to only report key changes that is, key presses and key releases.</span></span> <span data-ttu-id="c7456-191">Som standard rapporteras den bara när en nyckel är nere.</span><span class="sxs-lookup"><span data-stu-id="c7456-191">By default, it only reports when a key is down.</span></span>
- <span data-ttu-id="c7456-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: används endast om **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** har definierats.</span><span class="sxs-lookup"><span data-stu-id="c7456-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="c7456-193">Om det här är definierat, gör ux_host_class_hid_keyboard_key_get till att bara rapportera tangenter nedtryckt/ned-ändringar. viktiga uppdateringar/uppdateringar rapporteras inte.</span><span class="sxs-lookup"><span data-stu-id="c7456-193">If defined, causes ux_host_class_hid_keyboard_key_get to only report key pressed/down changes; key released/up changes are not reported.</span></span>
- <span data-ttu-id="c7456-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: används endast om **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** har definierats.</span><span class="sxs-lookup"><span data-stu-id="c7456-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="c7456-195">Om det här är definierat, gör ux_host_class_hid_keyboard_key_get att rapportera lås nyckel ändringar (CapsLock/NumLock/ScrollLock).</span><span class="sxs-lookup"><span data-stu-id="c7456-195">If defined, causes ux_host_class_hid_keyboard_key_get to report lock key (CapsLock/NumLock/ScrollLock) changes.</span></span>
- <span data-ttu-id="c7456-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: används endast om **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** har definierats.</span><span class="sxs-lookup"><span data-stu-id="c7456-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="c7456-197">Om det här är definierat, gör ux_host_class_hid_keyboard_key_get att rapportens ändrings nyckel (Ctrl/Alt/Shift/GUI) ändras.</span><span class="sxs-lookup"><span data-stu-id="c7456-197">If defined, causes ux_host_class_hid_keyboard_key_get to report modifier key (Ctrl/Alt/Shift/GUI) changes.</span></span>
- <span data-ttu-id="c7456-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: om det här värdet är definierat representerar det här värdet antalet paket i värd klassen CDC-ECM.</span><span class="sxs-lookup"><span data-stu-id="c7456-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: If defined, this value represents the number of packets in the CDC-ECM host class.</span></span> <span data-ttu-id="c7456-199">Standardvärdet är 16.</span><span class="sxs-lookup"><span data-stu-id="c7456-199">The default is 16.</span></span>

## <a name="source-code-tree"></a><span data-ttu-id="c7456-200">Käll kods träd</span><span class="sxs-lookup"><span data-stu-id="c7456-200">Source Code Tree</span></span>

<span data-ttu-id="c7456-201">USBX-filerna finns i flera kataloger.</span><span class="sxs-lookup"><span data-stu-id="c7456-201">The USBX files are provided in several directories.</span></span>

![Käll kods träd](media/usbx-host-stack/source-code-tree.png)

<span data-ttu-id="c7456-203">Följande konvention har antagits för att göra filerna identifierbara med deras namn:</span><span class="sxs-lookup"><span data-stu-id="c7456-203">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="c7456-204">Namnsuffix</span><span class="sxs-lookup"><span data-stu-id="c7456-204">File Suffix Name</span></span> | <span data-ttu-id="c7456-205">Fil Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7456-205">File description</span></span>                          |
| ---------------- | ----------------------------------------- |
| <span data-ttu-id="c7456-206">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="c7456-206">ux_host_stack</span></span>    | <span data-ttu-id="c7456-207">USBX Host stack core-filer</span><span class="sxs-lookup"><span data-stu-id="c7456-207">usbx host stack core files</span></span>                |
| <span data-ttu-id="c7456-208">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="c7456-208">ux_host_class</span></span>    | <span data-ttu-id="c7456-209">USBX värd stack klasser filer</span><span class="sxs-lookup"><span data-stu-id="c7456-209">usbx host stack classes files</span></span>             |
| <span data-ttu-id="c7456-210">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="c7456-210">ux_hcd</span></span>           | <span data-ttu-id="c7456-211">USBX för värd stack kontrollant</span><span class="sxs-lookup"><span data-stu-id="c7456-211">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="c7456-212">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="c7456-212">ux_device_stack</span></span>  | <span data-ttu-id="c7456-213">USBX Device stack core-filer</span><span class="sxs-lookup"><span data-stu-id="c7456-213">usbx device stack core files</span></span>              |
| <span data-ttu-id="c7456-214">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="c7456-214">ux_device_class</span></span>  | <span data-ttu-id="c7456-215">filer för USBX Device stack-klasser</span><span class="sxs-lookup"><span data-stu-id="c7456-215">usbx device stack classes files</span></span>           |
| <span data-ttu-id="c7456-216">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="c7456-216">ux_dcd</span></span>           | <span data-ttu-id="c7456-217">USBX enhets stack Controller-drivrutinsfiler</span><span class="sxs-lookup"><span data-stu-id="c7456-217">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="c7456-218">ux_otg</span><span class="sxs-lookup"><span data-stu-id="c7456-218">ux_otg</span></span>           | <span data-ttu-id="c7456-219">USBX OTG Controller-relaterade filer</span><span class="sxs-lookup"><span data-stu-id="c7456-219">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="c7456-220">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="c7456-220">ux_pictbridge</span></span>    | <span data-ttu-id="c7456-221">USBX PictBridge-filer</span><span class="sxs-lookup"><span data-stu-id="c7456-221">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="c7456-222">ux_utility</span><span class="sxs-lookup"><span data-stu-id="c7456-222">ux_utility</span></span>       | <span data-ttu-id="c7456-223">USBX verktygs funktioner</span><span class="sxs-lookup"><span data-stu-id="c7456-223">usbx utility functions</span></span>                    |
| <span data-ttu-id="c7456-224">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="c7456-224">demo_usbx</span></span>        | <span data-ttu-id="c7456-225">demonstrations filer för USBX</span><span class="sxs-lookup"><span data-stu-id="c7456-225">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="c7456-226">Initiering av USBX-resurser</span><span class="sxs-lookup"><span data-stu-id="c7456-226">Initialization of USBX resources</span></span>

<span data-ttu-id="c7456-227">USBX har en egen minnes hanterare.</span><span class="sxs-lookup"><span data-stu-id="c7456-227">USBX has its own memory manager.</span></span> <span data-ttu-id="c7456-228">Minnet måste allokeras till USBX innan värden eller enhets sidan på USBX initieras.</span><span class="sxs-lookup"><span data-stu-id="c7456-228">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="c7456-229">USBX minnes hanteraren kan hantera system där minnet kan cachelagras.</span><span class="sxs-lookup"><span data-stu-id="c7456-229">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="c7456-230">Följande funktion initierar USBX minnes resurser med 128 kB av vanligt minne och ingen separat pool för cache-säkert minne:</span><span class="sxs-lookup"><span data-stu-id="c7456-230">The following function initializes USBX memory resources with 128K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="c7456-231">Prototypen för ux_system_initialize är som följer.</span><span class="sxs-lookup"><span data-stu-id="c7456-231">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a><span data-ttu-id="c7456-232">Indataparametrar:</span><span class="sxs-lookup"><span data-stu-id="c7456-232">Input parameters:</span></span>

- <span data-ttu-id="c7456-233">**regular_memory_pool_start** Början av den vanliga mediepoolen.</span><span class="sxs-lookup"><span data-stu-id="c7456-233">**regular_memory_pool_start** Beginning of the regular memory pool.</span></span>
- <span data-ttu-id="c7456-234">**regular_memory_size** Storlek på den vanliga mediepoolen.</span><span class="sxs-lookup"><span data-stu-id="c7456-234">**regular_memory_size** Size of the regular memory pool.</span></span>
- <span data-ttu-id="c7456-235">**cache_safe_memory_pool_start** Början av cacheminnet för säker cache.</span><span class="sxs-lookup"><span data-stu-id="c7456-235">**cache_safe_memory_pool_start** Beginning of the cache safe memory pool.</span></span>
- <span data-ttu-id="c7456-236">**cache_safe_memory_size** Storlek på cachen för säkert minne.</span><span class="sxs-lookup"><span data-stu-id="c7456-236">**cache_safe_memory_size** Size of the cache safe memory pool.</span></span>    |

<span data-ttu-id="c7456-237">Inte alla system kräver definitionen av cache-säkert minne.</span><span class="sxs-lookup"><span data-stu-id="c7456-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="c7456-238">I ett sådant system kommer värdena som skickas under initieringen av minnes pekaren att anges till UX_NULL och storleken på poolen till 0.</span><span class="sxs-lookup"><span data-stu-id="c7456-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="c7456-239">USBX kommer sedan att använda den vanliga lagringspoolen i stället för den betrodda cache-poolen.</span><span class="sxs-lookup"><span data-stu-id="c7456-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="c7456-240">I ett system där det normala minnet inte är cache-säkert och en styrenhet kräver DMA-minne (till exempel OHCI, EHCI-styrenheter bland andra) måste du definiera en minnesbuffert i en säker cache-zon.</span><span class="sxs-lookup"><span data-stu-id="c7456-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory (like OHCI, EHCI controllers amongst others) it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="c7456-241">Avinitiering av USBX-resurser</span><span class="sxs-lookup"><span data-stu-id="c7456-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="c7456-242">USBX kan avbrytas genom att frisläppa sina resurser.</span><span class="sxs-lookup"><span data-stu-id="c7456-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="c7456-243">Innan du avslutar USBX måste alla klasser och styrenhets resurser avbrytas korrekt.</span><span class="sxs-lookup"><span data-stu-id="c7456-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="c7456-244">Följande funktion avinitierar USBX minnes resurser:</span><span class="sxs-lookup"><span data-stu-id="c7456-244">The following function uninitializes USBX memory resources :</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="c7456-245">Prototypen för ux_system_initialize är som följer.</span><span class="sxs-lookup"><span data-stu-id="c7456-245">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a><span data-ttu-id="c7456-246">Definition av USB-värdstyrenheter</span><span class="sxs-lookup"><span data-stu-id="c7456-246">Definition of USB Host Controllers</span></span>

<span data-ttu-id="c7456-247">Du måste definiera minst en USB-värdstyrenhet för att USBX ska kunna köras i värd läge.</span><span class="sxs-lookup"><span data-stu-id="c7456-247">It is required to define at least one USB host controller for USBX to operate in host mode.</span></span> <span data-ttu-id="c7456-248">Programmets initierings fil ska innehålla den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="c7456-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="c7456-249">Följande rad utför definitionen av en allmän värd styrenhet.</span><span class="sxs-lookup"><span data-stu-id="c7456-249">The following line performs the definition of a generic host controller.</span></span>

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

<span data-ttu-id="c7456-250">Ux_host_stack_hcd_register har följande prototyp.</span><span class="sxs-lookup"><span data-stu-id="c7456-250">The ux_host_stack_hcd_register has the following prototype.</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

<span data-ttu-id="c7456-251">Funktionen ux_host_stack_hcd_register har följande parametrar.</span><span class="sxs-lookup"><span data-stu-id="c7456-251">The ux_host_stack_hcd_register function has the following parameters.</span></span>

- <span data-ttu-id="c7456-252">**hcd_name**: sträng för kontroll enhetens namn</span><span class="sxs-lookup"><span data-stu-id="c7456-252">**hcd_name**: string of the controller name</span></span>
- <span data-ttu-id="c7456-253">**hcd_initialize_function**: initierings funktionen för kontrollanten</span><span class="sxs-lookup"><span data-stu-id="c7456-253">**hcd_initialize_function**: initialization function of the controller</span></span>
- <span data-ttu-id="c7456-254">**hcd_param1**: vanligt vis det IO-värde eller minne som används av kontrollanten</span><span class="sxs-lookup"><span data-stu-id="c7456-254">**hcd_param1**: usually the IO value or Memory used by the controller</span></span>
- <span data-ttu-id="c7456-255">**hcd_param2**: vanligt vis IRQ som används av kontrollanten</span><span class="sxs-lookup"><span data-stu-id="c7456-255">**hcd_param2**: usually the IRQ used by the controller</span></span>

<span data-ttu-id="c7456-256">I vårt föregående exempel:</span><span class="sxs-lookup"><span data-stu-id="c7456-256">In our previous example:</span></span>

- <span data-ttu-id="c7456-257">"ux_hcd_controller" är namnet på kontrollanten</span><span class="sxs-lookup"><span data-stu-id="c7456-257">"ux_hcd_controller" is the name of the controller</span></span>
- <span data-ttu-id="c7456-258">"ux_hcd_controller_initialize" är initierings rutinen för värd styrenheten</span><span class="sxs-lookup"><span data-stu-id="c7456-258">"ux_hcd_controller_initialize" is the initialization routine for the host controller</span></span>
- <span data-ttu-id="c7456-259">0xd0000 är den adress där värd styrenhetens register visas i minnet</span><span class="sxs-lookup"><span data-stu-id="c7456-259">0xd0000 is the address at which the host controller registers are visible in memory</span></span>
- <span data-ttu-id="c7456-260">och 0x0A är den IRQ som används av värd styrenheten.</span><span class="sxs-lookup"><span data-stu-id="c7456-260">and 0x0a is the IRQ used by the host controller.</span></span>

<span data-ttu-id="c7456-261">Följande är ett exempel på initiering av USBX i värd läge med en värd styrenhet och flera klasser.</span><span class="sxs-lookup"><span data-stu-id="c7456-261">Following is an example of the initialization of USBX in host mode with one host controller and several classes.</span></span>

```c
UINT status;

/* Initialize USBX. */
ux_system_initialize(memory_ptr, (128*1024),0,0);

/* The code below is required for installing the USBX host stack. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, host stack has been initialized. */

/* Register all the host classes for this USBX implementation. */
status = ux_host_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_storage", ux_host_class_storage_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_printer", ux_host_class_printer_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_audio", ux_host_class_audio_entry);

/* If status equals UX_SUCCESS, host class has been registered. */

/* Register all the USB host controllers available in this system. */ 
status = ux_host_stack_hcd_register("ux_hcd_controller", ux_hcd_controller_initialize, 0x300000, 0x0a);

/* If status equals UX_SUCCESS, USB host controllers have been registered. */
```

## <a name="definition-of-host-classes"></a><span data-ttu-id="c7456-262">Definition av värd klasser</span><span class="sxs-lookup"><span data-stu-id="c7456-262">Definition of Host Classes</span></span>

<span data-ttu-id="c7456-263">Det krävs för att definiera en eller flera värd klasser med USBX.</span><span class="sxs-lookup"><span data-stu-id="c7456-263">It is required to define one or more host classes with USBX.</span></span> <span data-ttu-id="c7456-264">En USB-klass krävs för att köra en USB-enhet när USB-stacken har konfigurerat USB-enheten.</span><span class="sxs-lookup"><span data-stu-id="c7456-264">A USB class is required to drive a USB device after the USB stack has configured the USB device.</span></span> <span data-ttu-id="c7456-265">En USB-klass är speciell för enheten.</span><span class="sxs-lookup"><span data-stu-id="c7456-265">A USB class is specific to the device.</span></span> <span data-ttu-id="c7456-266">En eller flera klasser kan krävas för att köra en USB-enhet beroende på antalet gränssnitt som finns i USB-enhetens beskrivningar.</span><span class="sxs-lookup"><span data-stu-id="c7456-266">One or more classes may be required to drive a USB device depending on the number of interfaces contained in the USB device descriptors.</span></span>

<span data-ttu-id="c7456-267">Detta är ett exempel på registreringen av HUB-klassen.</span><span class="sxs-lookup"><span data-stu-id="c7456-267">This is an example of the registration of the HUB class.</span></span>

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

<span data-ttu-id="c7456-268">Funktionen ux_host_class_register har följande prototyp.</span><span class="sxs-lookup"><span data-stu-id="c7456-268">The function ux_host_class_register has the following prototype.</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- <span data-ttu-id="c7456-269">**class_name** är namnet på klassen</span><span class="sxs-lookup"><span data-stu-id="c7456-269">**class_name** is the name of the class</span></span>
- <span data-ttu-id="c7456-270">**class_entry_address** är start punkten för klassen</span><span class="sxs-lookup"><span data-stu-id="c7456-270">**class_entry_address** is the entry point of the class</span></span>

<span data-ttu-id="c7456-271">I exemplet på initiering av HUB-klassen:</span><span class="sxs-lookup"><span data-stu-id="c7456-271">In the example of the HUB class initialization:</span></span>

- <span data-ttu-id="c7456-272">"ux_host_class_hub" är namnet på NAV klassen</span><span class="sxs-lookup"><span data-stu-id="c7456-272">"ux_host_class_hub" is the name of the hub class</span></span>
- <span data-ttu-id="c7456-273">ux_host_class_hub_entry är start punkten för NAV klassen.</span><span class="sxs-lookup"><span data-stu-id="c7456-273">ux_host_class_hub_entry is the entry point of the HUB class.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="c7456-274">Felsökning</span><span class="sxs-lookup"><span data-stu-id="c7456-274">Troubleshooting</span></span>

<span data-ttu-id="c7456-275">USBX levereras med en demonstrations fil och en simulerings miljö.</span><span class="sxs-lookup"><span data-stu-id="c7456-275">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="c7456-276">Det är alltid en bra idé att få demonstrations plattformen igång först – antingen på mål maskin varan eller en speciell demonstrations plattform.</span><span class="sxs-lookup"><span data-stu-id="c7456-276">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

<span data-ttu-id="c7456-277">Om demonstrations systemet inte fungerar kan du prova följande saker för att begränsa problemet.</span><span class="sxs-lookup"><span data-stu-id="c7456-277">If the demonstration system does not work, try the following things to narrow the problem.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="c7456-278">USBX versions-ID</span><span class="sxs-lookup"><span data-stu-id="c7456-278">USBX Version ID</span></span>

<span data-ttu-id="c7456-279">Den aktuella versionen av USBX är tillgänglig både för användaren och program varan under körnings tillfället.</span><span class="sxs-lookup"><span data-stu-id="c7456-279">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="c7456-280">Programmerare kan hämta USBX-versionen från undersökningen av filen \***ux_port. h** _.</span><span class="sxs-lookup"><span data-stu-id="c7456-280">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="c7456-281">Dessutom innehåller den här filen även en versions historik för motsvarande port.</span><span class="sxs-lookup"><span data-stu-id="c7456-281">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="c7456-282">Program varan kan hämta USBX-versionen genom att undersöka den globala strängen _ *_ _ux_version_id_* _, som definieras i _ *_ux_port. h_* \*.</span><span class="sxs-lookup"><span data-stu-id="c7456-282">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
