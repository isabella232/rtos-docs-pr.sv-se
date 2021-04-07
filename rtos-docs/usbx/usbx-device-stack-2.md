---
title: Kapitel 2 – installation av enhets stack för Azure återställnings tider USBX
description: Lär dig hur du installerar Azure återställnings tider USBX Device stack och de viktiga överväganden som du behöver tänka på innan du installerar.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dd58f77130fa252be9163bd70c29f7deee400d30
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549784"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a><span data-ttu-id="431aa-103">Kapitel 2 – installation av enhets stack för Azure återställnings tider USBX</span><span class="sxs-lookup"><span data-stu-id="431aa-103">Chapter 2 - Azure RTOS USBX Device Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="431aa-104">Värd överväganden</span><span class="sxs-lookup"><span data-stu-id="431aa-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="431aa-105">Typ av dator</span><span class="sxs-lookup"><span data-stu-id="431aa-105">Computer Type</span></span>

<span data-ttu-id="431aa-106">Inbäddad utveckling utförs vanligt vis på Windows-datorer eller UNIX-värddatorer.</span><span class="sxs-lookup"><span data-stu-id="431aa-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="431aa-107">När programmet har kompilerats, länkats och finns på värden laddas den ned till mål maskin varan för körning.</span><span class="sxs-lookup"><span data-stu-id="431aa-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="431aa-108">Hämta gränssnitt</span><span class="sxs-lookup"><span data-stu-id="431aa-108">Download Interfaces</span></span>

<span data-ttu-id="431aa-109">Normalt görs mål hämtningen via ett seriellt RS-232-gränssnitt, även om Parallel Interfaces, USB och Ethernet blir mer populära.</span><span class="sxs-lookup"><span data-stu-id="431aa-109">Usually the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="431aa-110">I utvecklings verktygets dokumentation finns tillgängliga alternativ.</span><span class="sxs-lookup"><span data-stu-id="431aa-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="431aa-111">Fel söknings verktyg</span><span class="sxs-lookup"><span data-stu-id="431aa-111">Debugging Tools</span></span>

<span data-ttu-id="431aa-112">Fel sökning sker vanligt vis via samma länk som nedladdningen av program avbildningen.</span><span class="sxs-lookup"><span data-stu-id="431aa-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="431aa-113">Det finns en mängd olika fel söknings program som sträcker sig från små övervakningsprogram som körs på målet genom BDM-verktyg (Background debug Monitor) och In-Circuit emulator (ICE).</span><span class="sxs-lookup"><span data-stu-id="431aa-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="431aa-114">Verktyget ICE ger den mest robusta fel sökningen av faktisk mål maskin vara.</span><span class="sxs-lookup"><span data-stu-id="431aa-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="431aa-115">Nödvändigt hårddisk utrymme</span><span class="sxs-lookup"><span data-stu-id="431aa-115">Required Hard Disk Space</span></span>

<span data-ttu-id="431aa-116">Käll koden för USBX levereras i ASCII-format och kräver cirka 500 KB utrymme på värddatorns hård disk.</span><span class="sxs-lookup"><span data-stu-id="431aa-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

### <a name="target-considerations"></a><span data-ttu-id="431aa-117">Mål överväganden</span><span class="sxs-lookup"><span data-stu-id="431aa-117">Target Considerations</span></span>

<span data-ttu-id="431aa-118">USBX kräver mellan 24 och 64 KB av skrivskyddat minne (ROM) på målet i värd läge.</span><span class="sxs-lookup"><span data-stu-id="431aa-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="431aa-119">Mängden minne som krävs beror på vilken typ av styrenhet som används och vilka USB-klasser som är kopplade till USBX.</span><span class="sxs-lookup"><span data-stu-id="431aa-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="431aa-120">En annan 32 KByte av målets RAM-minne (Random Access Memory) krävs för USBX globala data strukturer och minneskonfigurationer.</span><span class="sxs-lookup"><span data-stu-id="431aa-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="431aa-121">Den här mediepoolen kan också justeras beroende på det förväntade antalet enheter på USB-enheten och typen av USB-styrenhet.</span><span class="sxs-lookup"><span data-stu-id="431aa-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="431aa-122">Enhets sidan för USBX kräver ungefär 10-12 kB ROM beroende på typ av enhets styrenhet.</span><span class="sxs-lookup"><span data-stu-id="431aa-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="431aa-123">Användningen av RAM-minnet beror på vilken typ av klass som emuleras av enheten.</span><span class="sxs-lookup"><span data-stu-id="431aa-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="431aa-124">USBX förlitar sig även på ThreadX-semaforer, mutexer och trådar för flera tråd skydd och I/O-inskjutningar och regelbunden bearbetning för övervakning av USB-bussens topologi.</span><span class="sxs-lookup"><span data-stu-id="431aa-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="431aa-125">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="431aa-125">Product Distribution</span></span>

<span data-ttu-id="431aa-126">Azure återställnings tider-USBX kan hämtas från vår offentliga käll kods lagrings plats på <https://github.com/azure-rtos/usbx/> .</span><span class="sxs-lookup"><span data-stu-id="431aa-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="431aa-127">Följande är en lista över flera viktiga filer i lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="431aa-127">The following is a list of several important files in the repository.</span></span>

* <span data-ttu-id="431aa-128">***ux_api. h***: den här C-huvudfilen innehåller alla system likställda, data strukturer och tjänst prototyper.</span><span class="sxs-lookup"><span data-stu-id="431aa-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
* <span data-ttu-id="431aa-129">***ux_port. h***: den här C-huvudfilen innehåller alla data definitioner och strukturer för utveckling-verktyg.</span><span class="sxs-lookup"><span data-stu-id="431aa-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
* <span data-ttu-id="431aa-130">***UX. lib***: det här är den binära versionen av USBX C-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="431aa-130">***ux.lib***:  This is the binary version of the USBX C library.</span></span> <span data-ttu-id="431aa-131">Den distribueras med standard paketet.</span><span class="sxs-lookup"><span data-stu-id="431aa-131">It is distributed with the standard package.</span></span>
* <span data-ttu-id="431aa-132">***demo_usbx. c***: c-filen som innehåller en enkel USBX-demo</span><span class="sxs-lookup"><span data-stu-id="431aa-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="431aa-133">Alla fil namn är i gemener.</span><span class="sxs-lookup"><span data-stu-id="431aa-133">All filenames are in lower-case.</span></span> <span data-ttu-id="431aa-134">Den här namngivnings konventionen gör det lättare att konvertera kommandon till UNIX-utvecklings plattformar.</span><span class="sxs-lookup"><span data-stu-id="431aa-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="431aa-135">USBX-installation</span><span class="sxs-lookup"><span data-stu-id="431aa-135">USBX Installation</span></span>

<span data-ttu-id="431aa-136">USBX installeras genom att klona GitHub-lagringsplatsen till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="431aa-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="431aa-137">Följande är en typisk syntax för att skapa en klon av USBX-lagringsplatsen på din dator:</span><span class="sxs-lookup"><span data-stu-id="431aa-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```c
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="431aa-138">Alternativt kan du ladda ned en kopia av lagrings platsen med hjälp av knappen Ladda ned på GitHub-huvud sidan.</span><span class="sxs-lookup"><span data-stu-id="431aa-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="431aa-139">Du hittar också instruktioner för att skapa USBX-biblioteket på den första sidan i online-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="431aa-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="431aa-140">Följande allmänna instruktioner gäller för i princip vilken installation som helst:</span><span class="sxs-lookup"><span data-stu-id="431aa-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="431aa-141">Använd samma katalog som du tidigare installerade ThreadX på värd hård disken.</span><span class="sxs-lookup"><span data-stu-id="431aa-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="431aa-142">Alla USBX namn är unika och påverkar inte den tidigare USBX-installationen.</span><span class="sxs-lookup"><span data-stu-id="431aa-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
1. <span data-ttu-id="431aa-143">Lägg till ett anrop till \***ux_system_initialize** _ i eller nära början av _ *_tx_application_define_* \*.</span><span class="sxs-lookup"><span data-stu-id="431aa-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _*_tx_application_define_\*\*.</span></span> <span data-ttu-id="431aa-144">Det är här som USBX-resurserna initieras.</span><span class="sxs-lookup"><span data-stu-id="431aa-144">This is where the USBX resources are initialized.</span></span>
1. <span data-ttu-id="431aa-145">Lägg till ett anrop till \*\**ux_device_stack_initialize *.**</span><span class="sxs-lookup"><span data-stu-id="431aa-145">Add a call to \***ux_device_stack_initialize\*.**</span></span>
1. <span data-ttu-id="431aa-146">Lägg till ett eller flera anrop för att initiera nödvändiga USBX-klasser (antingen värd-och/eller enhets klasser)</span><span class="sxs-lookup"><span data-stu-id="431aa-146">Add one or more calls to initialize the required USBX classes (either host and/or devices classes)</span></span>
1. <span data-ttu-id="431aa-147">Lägg till ett eller flera anrop för att initiera den tillgängliga enhets styrenheten i systemet.</span><span class="sxs-lookup"><span data-stu-id="431aa-147">Add one or more calls to initialize the device controller available in the system.</span></span>
1. <span data-ttu-id="431aa-148">Du kan behöva ändra filen tx_low_level_initialize. c för att kunna lägga till maskin varu initiering på låg nivå och avbryta vektor routning.</span><span class="sxs-lookup"><span data-stu-id="431aa-148">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="431aa-149">Detta är särskilt för maskin varu plattformen och beskrivs inte här. |</span><span class="sxs-lookup"><span data-stu-id="431aa-149">This is specific to the hardware platform and will not be discussed here.|</span></span>
1. <span data-ttu-id="431aa-150">Kompilera program käll koden och länka med USBX-och ThreadX-körnings biblioteken (FileX och/eller netx kan också krävas om klassen för USB-lagring och/eller USB-nätverksanslutningar ska kompileras), UX. a (eller UX. lib) och TX. a (eller TX. lib).</span><span class="sxs-lookup"><span data-stu-id="431aa-150">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="431aa-151">Resultatet kan hämtas till målet och köras!</span><span class="sxs-lookup"><span data-stu-id="431aa-151">The resulting can be downloaded to the target and executed!</span></span>

## <a name="configuration-options"></a><span data-ttu-id="431aa-152">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="431aa-152">Configuration Options</span></span>

<span data-ttu-id="431aa-153">Det finns flera konfigurations alternativ för att skapa USBX-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="431aa-153">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="431aa-154">Alla alternativ finns i ***ux_user. h***.</span><span class="sxs-lookup"><span data-stu-id="431aa-154">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="431aa-155">I listan nedan beskrivs varje konfigurations alternativ.</span><span class="sxs-lookup"><span data-stu-id="431aa-155">The list below details each configuration option.</span></span>

| <span data-ttu-id="431aa-156">Konfigurations &nbsp; alternativ</span><span class="sxs-lookup"><span data-stu-id="431aa-156">Configuration&nbsp;Option</span></span> | <span data-ttu-id="431aa-157">Description</span><span class="sxs-lookup"><span data-stu-id="431aa-157">Description</span></span> |
| --- | --- |
| <span data-ttu-id="431aa-158">**UX_PERIODIC_RATE**</span><span class="sxs-lookup"><span data-stu-id="431aa-158">**UX_PERIODIC_RATE**</span></span> | <span data-ttu-id="431aa-159">Det här värdet anger hur många Tick per sekund för en viss maskin varu plattform.</span><span class="sxs-lookup"><span data-stu-id="431aa-159">This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="431aa-160">Standardvärdet är 1000 som anger 1 Tick per millisekund.</span><span class="sxs-lookup"><span data-stu-id="431aa-160">The default is 1000 indicating 1 tick per millisecond.</span></span> |
| <span data-ttu-id="431aa-161">**UX_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="431aa-161">**UX_THREAD_STACK_SIZE**</span></span> | <span data-ttu-id="431aa-162">Det här värdet är storleken på stacken i byte för USBX-trådarna.</span><span class="sxs-lookup"><span data-stu-id="431aa-162">This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="431aa-163">Det kan vara vanligt vis 1024 byte eller 2048 byte beroende på vilken processor som används och värd styrenheten.</span><span class="sxs-lookup"><span data-stu-id="431aa-163">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span> |
| <span data-ttu-id="431aa-164">**UX_THREAD_PRIORITY_ENUM**</span><span class="sxs-lookup"><span data-stu-id="431aa-164">**UX_THREAD_PRIORITY_ENUM**</span></span> | <span data-ttu-id="431aa-165">Detta är prioritet svärdet för ThreadX för USBX-uppräknings trådar som övervakar buss sto pol Ogin.</span><span class="sxs-lookup"><span data-stu-id="431aa-165">This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span> |
| <span data-ttu-id="431aa-166">**UX_THREAD_PRIORITY_CLASS**</span><span class="sxs-lookup"><span data-stu-id="431aa-166">**UX_THREAD_PRIORITY_CLASS**</span></span> | <span data-ttu-id="431aa-167">Detta är prioritet svärdet för ThreadX för standard trådarna för USBX.</span><span class="sxs-lookup"><span data-stu-id="431aa-167">This is the ThreadX priority value for the standard USBX threads.</span></span> |
| <span data-ttu-id="431aa-168">**UX_THREAD_PRIORITY_KEYBOARD**</span><span class="sxs-lookup"><span data-stu-id="431aa-168">**UX_THREAD_PRIORITY_KEYBOARD**</span></span> | <span data-ttu-id="431aa-169">Detta är ThreadX prioritets värde för HID-tangentbordet för USBX.</span><span class="sxs-lookup"><span data-stu-id="431aa-169">This is the ThreadX priority value for the USBX HID keyboard class.</span></span> |
| <span data-ttu-id="431aa-170">**UX_THREAD_PRIORITY_DCD**</span><span class="sxs-lookup"><span data-stu-id="431aa-170">**UX_THREAD_PRIORITY_DCD**</span></span> | <span data-ttu-id="431aa-171">Detta är ThreadX prioritets värde för enhets styrenhetens tråd.</span><span class="sxs-lookup"><span data-stu-id="431aa-171">This is the ThreadX priority value for the device controller thread.</span></span> |
| <span data-ttu-id="431aa-172">**UX_NO_TIME_SLICE**</span><span class="sxs-lookup"><span data-stu-id="431aa-172">**UX_NO_TIME_SLICE**</span></span> | <span data-ttu-id="431aa-173">Det här värdet definierar i själva verket den tids sektor som ska användas för trådar.</span><span class="sxs-lookup"><span data-stu-id="431aa-173">This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="431aa-174">Om t. ex. har definierats till 0 används inte tids segment i ThreadX Target-porten.</span><span class="sxs-lookup"><span data-stu-id="431aa-174">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span> |
| <span data-ttu-id="431aa-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span><span class="sxs-lookup"><span data-stu-id="431aa-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span></span> | <span data-ttu-id="431aa-176">Detta är det maximala antalet USBX-klasser som kan registreras via ux_device_stack_class_register.</span><span class="sxs-lookup"><span data-stu-id="431aa-176">This is the maximum number of USBX classes that can be registered via ux_device_stack_class_register.</span></span> |
| <span data-ttu-id="431aa-177">**UX_MAX_SLAVE_LUN**</span><span class="sxs-lookup"><span data-stu-id="431aa-177">**UX_MAX_SLAVE_LUN**</span></span> | <span data-ttu-id="431aa-178">Värdet representerar det aktuella antalet SCSI-logiska enheter som representeras i enhetens lagrings klass driv rutin.</span><span class="sxs-lookup"><span data-stu-id="431aa-178">This value represents the current number of SCSI logical units represented in the device storage class driver.</span></span> |
| <span data-ttu-id="431aa-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span><span class="sxs-lookup"><span data-stu-id="431aa-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span></span> | <span data-ttu-id="431aa-180">Om den har definierats hanterar lagrings klassen multi-media-kommandon (MMC), som är DVD-ROM.</span><span class="sxs-lookup"><span data-stu-id="431aa-180">If defined, the storage class will handle Multi-Media Commands (MMC) that is, DVD-ROM.</span></span> |
| <span data-ttu-id="431aa-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span><span class="sxs-lookup"><span data-stu-id="431aa-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span></span> | <span data-ttu-id="431aa-182">Det här värdet representerar antalet NetX-paket i CDC-ECM-klassen ' Packet pool.</span><span class="sxs-lookup"><span data-stu-id="431aa-182">This value represents the number of NetX packets in the CDC-ECM class' packet pool.</span></span> <span data-ttu-id="431aa-183">Standardvärdet är 16.</span><span class="sxs-lookup"><span data-stu-id="431aa-183">The default is 16.</span></span> |
| <span data-ttu-id="431aa-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="431aa-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span></span> | <span data-ttu-id="431aa-185">Det här värdet representerar det maximala antalet byte som tagits emot på en kontroll slut punkt i enhets stacken.</span><span class="sxs-lookup"><span data-stu-id="431aa-185">This value represents the maximum number of bytes received on a control endpoint in the device stack.</span></span> <span data-ttu-id="431aa-186">Standardvärdet är 256 byte, men kan minskas i miljöer med minnes begränsning.</span><span class="sxs-lookup"><span data-stu-id="431aa-186">The default is 256 bytes but can be reduced in memory constraint environments.</span></span> |
| <span data-ttu-id="431aa-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="431aa-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span></span> | <span data-ttu-id="431aa-188">Det här värdet representerar den maximala längden i byte för en HID-rapport.</span><span class="sxs-lookup"><span data-stu-id="431aa-188">This value represents the maximum length in bytes of a HID report.</span></span> |
| <span data-ttu-id="431aa-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span><span class="sxs-lookup"><span data-stu-id="431aa-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span></span> | <span data-ttu-id="431aa-190">Det här värdet representerar det maximala antalet HID-rapporter som kan köas samtidigt.</span><span class="sxs-lookup"><span data-stu-id="431aa-190">This value represents the maximum number of HID reports that can be queued at once.</span></span> |
| <span data-ttu-id="431aa-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="431aa-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span></span> | <span data-ttu-id="431aa-192">Det här värdet representerar det maximala antalet byte som tagits emot på en Mass slut punkt i enhets stacken.</span><span class="sxs-lookup"><span data-stu-id="431aa-192">This value represents the maximum number of bytes received on a bulk endpoint in the device stack.</span></span> <span data-ttu-id="431aa-193">Standardvärdet är 4096 byte, men kan minskas i miljöer med minnes begränsning.</span><span class="sxs-lookup"><span data-stu-id="431aa-193">The default is 4096 bytes but can be reduced in memory constraint environments.</span></span> |

## <a name="source-code-tree"></a><span data-ttu-id="431aa-194">Käll kods träd</span><span class="sxs-lookup"><span data-stu-id="431aa-194">Source Code Tree</span></span>

<span data-ttu-id="431aa-195">USBX-filerna finns i flera kataloger.</span><span class="sxs-lookup"><span data-stu-id="431aa-195">The USBX files are provided in several directories.</span></span>

![Käll kods träd](media/usbx-device-stack/source-code-tree.png)

<span data-ttu-id="431aa-197">Följande konvention har antagits för att göra filerna identifierbara med deras namn:</span><span class="sxs-lookup"><span data-stu-id="431aa-197">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="431aa-198">Namnsuffix</span><span class="sxs-lookup"><span data-stu-id="431aa-198">File Suffix Name</span></span>  | <span data-ttu-id="431aa-199">Fil Beskrivning</span><span class="sxs-lookup"><span data-stu-id="431aa-199">File description</span></span>                          |
| ----------------- | ----------------------------------------- |
| <span data-ttu-id="431aa-200">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="431aa-200">ux_host_stack</span></span>   | <span data-ttu-id="431aa-201">USBX Host stack core-filer</span><span class="sxs-lookup"><span data-stu-id="431aa-201">usbx host stack core files</span></span>                |
| <span data-ttu-id="431aa-202">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="431aa-202">ux_host_class</span></span>   | <span data-ttu-id="431aa-203">USBX värd stack klasser filer</span><span class="sxs-lookup"><span data-stu-id="431aa-203">usbx host stack classes files</span></span>             |
| <span data-ttu-id="431aa-204">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="431aa-204">ux_hcd</span></span>           | <span data-ttu-id="431aa-205">USBX för värd stack kontrollant</span><span class="sxs-lookup"><span data-stu-id="431aa-205">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="431aa-206">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="431aa-206">ux_device_stack</span></span> | <span data-ttu-id="431aa-207">USBX Device stack core-filer</span><span class="sxs-lookup"><span data-stu-id="431aa-207">usbx device stack core files</span></span>              |
| <span data-ttu-id="431aa-208">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="431aa-208">ux_device_class</span></span> | <span data-ttu-id="431aa-209">filer för USBX Device stack-klasser</span><span class="sxs-lookup"><span data-stu-id="431aa-209">usbx device stack classes files</span></span>           |
| <span data-ttu-id="431aa-210">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="431aa-210">ux_dcd</span></span>           | <span data-ttu-id="431aa-211">USBX enhets stack Controller-drivrutinsfiler</span><span class="sxs-lookup"><span data-stu-id="431aa-211">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="431aa-212">ux_otg</span><span class="sxs-lookup"><span data-stu-id="431aa-212">ux_otg</span></span>           | <span data-ttu-id="431aa-213">USBX OTG Controller-relaterade filer</span><span class="sxs-lookup"><span data-stu-id="431aa-213">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="431aa-214">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="431aa-214">ux_pictbridge</span></span>    | <span data-ttu-id="431aa-215">USBX PictBridge-filer</span><span class="sxs-lookup"><span data-stu-id="431aa-215">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="431aa-216">ux_utility</span><span class="sxs-lookup"><span data-stu-id="431aa-216">ux_utility</span></span>       | <span data-ttu-id="431aa-217">USBX verktygs funktioner</span><span class="sxs-lookup"><span data-stu-id="431aa-217">usbx utility functions</span></span>                    |
| <span data-ttu-id="431aa-218">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="431aa-218">demo_usbx</span></span>        | <span data-ttu-id="431aa-219">demonstrations filer för USBX</span><span class="sxs-lookup"><span data-stu-id="431aa-219">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="431aa-220">Initiering av USBX-resurser</span><span class="sxs-lookup"><span data-stu-id="431aa-220">Initialization of USBX resources</span></span>

<span data-ttu-id="431aa-221">USBX har en egen minnes hanterare.</span><span class="sxs-lookup"><span data-stu-id="431aa-221">USBX has its own memory manager.</span></span> <span data-ttu-id="431aa-222">Minnet måste allokeras till USBX innan värden eller enhets sidan på USBX initieras.</span><span class="sxs-lookup"><span data-stu-id="431aa-222">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="431aa-223">USBX minnes hanteraren kan hantera system där minnet kan cachelagras.</span><span class="sxs-lookup"><span data-stu-id="431aa-223">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="431aa-224">Följande funktion initierar USBX minnes resurser med 128 kB reguljärt minne och ingen separat pool för cache-säkert minne:</span><span class="sxs-lookup"><span data-stu-id="431aa-224">The following function initializes USBX memory resources with 128 K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="431aa-225">Prototypen för ux_system_initialize är följande:</span><span class="sxs-lookup"><span data-stu-id="431aa-225">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

<span data-ttu-id="431aa-226">Indataparametrar:</span><span class="sxs-lookup"><span data-stu-id="431aa-226">Input parameters:</span></span>

| <span data-ttu-id="431aa-227">Parameter</span><span class="sxs-lookup"><span data-stu-id="431aa-227">Parameter</span></span>                          | <span data-ttu-id="431aa-228">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="431aa-228">Description</span></span>                             |
| ---------------------------------- | --------------------------------------- |
| <span data-ttu-id="431aa-229">VOID \* regular_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="431aa-229">VOID \*regular_memory_pool_start</span></span>    | <span data-ttu-id="431aa-230">Början av den vanliga mediepoolen</span><span class="sxs-lookup"><span data-stu-id="431aa-230">Beginning of the regular memory pool</span></span>    |
| <span data-ttu-id="431aa-231">ULONG regular_memory_size</span><span class="sxs-lookup"><span data-stu-id="431aa-231">ULONG regular_memory_size</span></span>          | <span data-ttu-id="431aa-232">Storlek på den ordinarie lagringspoolen</span><span class="sxs-lookup"><span data-stu-id="431aa-232">Size of the regular memory pool</span></span>         |
| <span data-ttu-id="431aa-233">VOID \* cache_safe_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="431aa-233">VOID \*cache_safe_memory_pool_start</span></span> | <span data-ttu-id="431aa-234">Början av cacheminnet för säker cache</span><span class="sxs-lookup"><span data-stu-id="431aa-234">Beginning of the cache safe memory pool</span></span> |
| <span data-ttu-id="431aa-235">ULONG cache_safe_memory_size</span><span class="sxs-lookup"><span data-stu-id="431aa-235">ULONG cache_safe_memory_size</span></span>       | <span data-ttu-id="431aa-236">Storlek på cachen för cache-säker pool</span><span class="sxs-lookup"><span data-stu-id="431aa-236">Size of the cache safe memory pool</span></span>      |

<span data-ttu-id="431aa-237">Inte alla system kräver definitionen av cache-säkert minne.</span><span class="sxs-lookup"><span data-stu-id="431aa-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="431aa-238">I ett sådant system kommer värdena som skickas under initieringen av minnes pekaren att anges till UX_NULL och storleken på poolen till 0.</span><span class="sxs-lookup"><span data-stu-id="431aa-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="431aa-239">USBX kommer sedan att använda den vanliga lagringspoolen i stället för den betrodda cache-poolen.</span><span class="sxs-lookup"><span data-stu-id="431aa-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="431aa-240">I ett system där det normala minnet inte är cache-säkert och en styrenhet kräver DMA-minne är det nödvändigt att definiera en minnesbuffert i en säker cache-zon.</span><span class="sxs-lookup"><span data-stu-id="431aa-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="431aa-241">Avinitiering av USBX-resurser</span><span class="sxs-lookup"><span data-stu-id="431aa-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="431aa-242">USBX kan avbrytas genom att frisläppa sina resurser.</span><span class="sxs-lookup"><span data-stu-id="431aa-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="431aa-243">Innan du avslutar USBX måste alla klasser och styrenhets resurser avbrytas korrekt.</span><span class="sxs-lookup"><span data-stu-id="431aa-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="431aa-244">Följande funktion avinitierar USBX minnes resurser:</span><span class="sxs-lookup"><span data-stu-id="431aa-244">The following function uninitializes USBX memory resources:</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="431aa-245">Prototypen för ux_system_initialize är följande:</span><span class="sxs-lookup"><span data-stu-id="431aa-245">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a><span data-ttu-id="431aa-246">Definition av USB-enhets styrenhet</span><span class="sxs-lookup"><span data-stu-id="431aa-246">Definition of USB Device Controller</span></span>

<span data-ttu-id="431aa-247">Endast en USB-enhets styrenhet kan definieras när som helst för att köras i enhets läge.</span><span class="sxs-lookup"><span data-stu-id="431aa-247">Only one USB device controller can be defined at any time to operate in device mode.</span></span> <span data-ttu-id="431aa-248">Programmets initierings fil ska innehålla den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="431aa-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="431aa-249">Följande rad utför definitionen av en allmän USB-styrenhet:</span><span class="sxs-lookup"><span data-stu-id="431aa-249">The following line performs the definition of a generic usb controller:</span></span>

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

<span data-ttu-id="431aa-250">Initieringen av USB-enheten har följande prototyp:</span><span class="sxs-lookup"><span data-stu-id="431aa-250">The USB device initialization has the following prototype:</span></span>

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

<span data-ttu-id="431aa-251">med följande parametrar:</span><span class="sxs-lookup"><span data-stu-id="431aa-251">with the following parameters:</span></span>

| <span data-ttu-id="431aa-252">Pararmeter</span><span class="sxs-lookup"><span data-stu-id="431aa-252">Pararmeter</span></span>               | <span data-ttu-id="431aa-253">Description</span><span class="sxs-lookup"><span data-stu-id="431aa-253">Description</span></span>                      |
| ------------------------ | -------------------------------- |
| <span data-ttu-id="431aa-254">ULONG dcd_io</span><span class="sxs-lookup"><span data-stu-id="431aa-254">ULONG dcd_io</span></span>            | <span data-ttu-id="431aa-255">Adress till styrenhetens IO</span><span class="sxs-lookup"><span data-stu-id="431aa-255">Address of the controller IO</span></span>     |
| <span data-ttu-id="431aa-256">ULONG dcd_irq</span><span class="sxs-lookup"><span data-stu-id="431aa-256">ULONG dcd_irq</span></span>           | <span data-ttu-id="431aa-257">Avbrott som används av kontrollanten</span><span class="sxs-lookup"><span data-stu-id="431aa-257">Interrupt used by the controller</span></span> |
| <span data-ttu-id="431aa-258">ULONG dcd_vbus_address</span><span class="sxs-lookup"><span data-stu-id="431aa-258">ULONG dcd_vbus_address</span></span> | <span data-ttu-id="431aa-259">Adressen för VBUS-GPIO</span><span class="sxs-lookup"><span data-stu-id="431aa-259">Address of the VBUS GPIO</span></span>         |

<span data-ttu-id="431aa-260">Följande exempel är initieringen av USBX i enhets läge med lagrings enhets klassen och en allmän styrenhet:</span><span class="sxs-lookup"><span data-stu-id="431aa-260">The following example is the initialization of USBX in device mode with the storage device class and a generic controller:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a><span data-ttu-id="431aa-261">Felsökning</span><span class="sxs-lookup"><span data-stu-id="431aa-261">Troubleshooting</span></span>

<span data-ttu-id="431aa-262">USBX levereras med en demonstrations fil och en simulerings miljö.</span><span class="sxs-lookup"><span data-stu-id="431aa-262">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="431aa-263">Det är alltid en bra idé att få demonstrations plattformen igång först – antingen på mål maskin varan eller en speciell demonstrations plattform.</span><span class="sxs-lookup"><span data-stu-id="431aa-263">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="431aa-264">USBX versions-ID</span><span class="sxs-lookup"><span data-stu-id="431aa-264">USBX Version ID</span></span>

<span data-ttu-id="431aa-265">Den aktuella versionen av USBX är tillgänglig både för användaren och program varan under körnings tillfället.</span><span class="sxs-lookup"><span data-stu-id="431aa-265">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="431aa-266">Programmerare kan hämta USBX-versionen från undersökningen av filen \***ux_port. h** _.</span><span class="sxs-lookup"><span data-stu-id="431aa-266">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="431aa-267">Dessutom innehåller den här filen även en versions historik för motsvarande port.</span><span class="sxs-lookup"><span data-stu-id="431aa-267">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="431aa-268">Program varan kan hämta USBX-versionen genom att undersöka den globala strängen _ *_ _ux_version_id_* _, som definieras i _ *_ux_port. h_* \*.</span><span class="sxs-lookup"><span data-stu-id="431aa-268">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
