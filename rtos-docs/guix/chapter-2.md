---
title: Kapitel 2 – installation och användning av GUIX
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av HighPerformance-GUIX för användar gränssnittet.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6527227062fc667b3f527a798d6621914c374c5c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826391"
---
# <a name="chapter-2---installation-and-use-of-guix"></a><span data-ttu-id="981a6-103">Kapitel 2 – installation och användning av GUIX</span><span class="sxs-lookup"><span data-stu-id="981a6-103">Chapter 2 - Installation and Use of GUIX</span></span>

<span data-ttu-id="981a6-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av HighPerformance-GUIX för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="981a6-104">This chapter contains a description of various issues related to installation, setup, and use of the highperformance user interface product GUIX.</span></span>  

## <a name="host-considerations"></a><span data-ttu-id="981a6-105">Värd överväganden</span><span class="sxs-lookup"><span data-stu-id="981a6-105">Host Considerations</span></span>

<span data-ttu-id="981a6-106">Inbäddad utveckling utförs vanligt vis på Windows-eller Linux-värddatorer (UNIX).</span><span class="sxs-lookup"><span data-stu-id="981a6-106">Embedded development is usually performed on Windows or Linux (Unix) host computers.</span></span> <span data-ttu-id="981a6-107">När programmet har kompilerats, länkats och den körbara filen genereras på värden laddas den ned till mål maskin varan för körning.</span><span class="sxs-lookup"><span data-stu-id="981a6-107">After the application is compiled, linked, and the executable is generated on the host, it is downloaded to the target hardware for execution.</span></span>

<span data-ttu-id="981a6-108">Normalt görs mål hämtningen från utvecklings verktygets fel sökare.</span><span class="sxs-lookup"><span data-stu-id="981a6-108">Usually the target download is done from within the development tool's debugger.</span></span> <span data-ttu-id="981a6-109">Efter nedladdningen ansvarar fel sökaren för att tillhandahålla mål körnings kontroll (gå till, stoppa, Bryt punkt osv.) samt åtkomst till minne och processor register.</span><span class="sxs-lookup"><span data-stu-id="981a6-109">After download, the debugger is responsible for providing target execution control (go, halt, breakpoint, etc.) as well as access to memory and processor registers.</span></span>

<span data-ttu-id="981a6-110">De flesta utvecklings verktyg för fel sökning kommunicerar med mål maskin varan via OCD-anslutningar (on-chip debug) som JTAG (IEEE 1149,1) och fel söknings läge för bakgrunden (BDM).</span><span class="sxs-lookup"><span data-stu-id="981a6-110">Most development tool debuggers communicate with the target hardware via on-chip debug (OCD) connections such as JTAG (IEEE 1149.1) and Background Debug Mode (BDM).</span></span> <span data-ttu-id="981a6-111">Fel sökare kommunicerar också med mål maskin vara via ICE-anslutningar (In-Circuit emulation).</span><span class="sxs-lookup"><span data-stu-id="981a6-111">Debuggers also communicate with target hardware through In-Circuit Emulation (ICE) connections.</span></span> <span data-ttu-id="981a6-112">Både OCD-och ICE-anslutningar ger robusta lösningar med minimalt intrång på den inhemske program varan.</span><span class="sxs-lookup"><span data-stu-id="981a6-112">Both OCD and ICE connections provide robust solutions with minimal intrusion on the target resident software.</span></span>

<span data-ttu-id="981a6-113">För resurser som används på värden levereras käll koden för GUXI i ASCII-format och kräver cirka 30 MB utrymme på värddatorns hård disk.</span><span class="sxs-lookup"><span data-stu-id="981a6-113">As for resources used on the host, the source code for GUXI is delivered in ASCII format and requires approximately 30 Mbytes of space on the host computer’s hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="981a6-114">Mål överväganden</span><span class="sxs-lookup"><span data-stu-id="981a6-114">Target Considerations</span></span>

<span data-ttu-id="981a6-115">GUIX kräver mellan 5 KByte och 80 KB Read-Only minne (ROM) på målet.</span><span class="sxs-lookup"><span data-stu-id="981a6-115">GUIX requires between 5 KBytes and 80 Kbytes of Read-Only Memory (ROM) on the target.</span></span> <span data-ttu-id="981a6-116">En annan 5 till 10KBytes av målets RAM-minne (Random Access Memory) krävs för GUIX-trådens stack och andra globala data strukturer.</span><span class="sxs-lookup"><span data-stu-id="981a6-116">Another 5 to 10KBytes of the target’s Random Access Memory (RAM) are required for the GUIX thread stack and other global data structures.</span></span>

<span data-ttu-id="981a6-117">Dessutom kräver GUIX användningen av en ThreadX-timer och ett ThreadX mutex-objekt.</span><span class="sxs-lookup"><span data-stu-id="981a6-117">In addition, GUIX requires the use of a ThreadX timer and a ThreadX mutex object.</span></span> <span data-ttu-id="981a6-118">Dessa funktioner används för periodiska bearbetnings behov och tråd skydd i GUIX.</span><span class="sxs-lookup"><span data-stu-id="981a6-118">These facilities are used for periodic processing needs and thread protection inside GUIX.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="981a6-119">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="981a6-119">Product Distribution</span></span>

<span data-ttu-id="981a6-120">Azure återställnings tider-GUIX kan hämtas från vår offentliga käll kods lagrings plats på <https://github.com/azure-rtos/guix/> .</span><span class="sxs-lookup"><span data-stu-id="981a6-120">Azure RTOS GUIX can be obtained from our public source code repository at <https://github.com/azure-rtos/guix/>.</span></span>

<span data-ttu-id="981a6-121">Följande är en lista över viktiga filer som är vanliga för de flesta produkt distributioner:</span><span class="sxs-lookup"><span data-stu-id="981a6-121">The following is a list of the important files common to most product distributions:</span></span>

| <span data-ttu-id="981a6-122">Sökväg&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="981a6-122">Filename&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></span>| <span data-ttu-id="981a6-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="981a6-123">Description</span></span>   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="981a6-124">gx_api. h</span><span class="sxs-lookup"><span data-stu-id="981a6-124">gx_api.h</span></span>        | <span data-ttu-id="981a6-125">Den här C-huvudfilen innehåller alla system likställda, data strukturer och tjänst prototyper.</span><span class="sxs-lookup"><span data-stu-id="981a6-125">This C header file contains all system equates, data structures, and service prototypes.</span></span> |
| <span data-ttu-id="981a6-126">gx_port. h</span><span class="sxs-lookup"><span data-stu-id="981a6-126">gx_port.h</span></span>       | <span data-ttu-id="981a6-127">Den här C-huvudfilen innehåller alla språkspecifika och utvecklingsverktyg specifika data definitioner och strukturer.</span><span class="sxs-lookup"><span data-stu-id="981a6-127">This C header file contains all target-specific and development tool-specific data definitions and structures.</span></span>                                                                                                                                         |
| <span data-ttu-id="981a6-128">GX. a (eller GX. lib)</span><span class="sxs-lookup"><span data-stu-id="981a6-128">gx.a (or gx.lib)</span></span> | <span data-ttu-id="981a6-129">Det här är den binära versionen av GUIX C-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="981a6-129">This is the binary version of the GUIX C library.</span></span> <span data-ttu-id="981a6-130">Detta skapas vanligt vis genom att kompilera och arkivera den tillhandahållna GUIX biblioteks-källfilerna, men det här biblioteket kan finnas i fördefinierat format beroende på maskin varu mål och licens typ.</span><span class="sxs-lookup"><span data-stu-id="981a6-130">This is normally built by compiling and archiving the provided GUIX library source files, however this library may be provided in pre-built form depending on your hardware target and license type.</span></span> |
|

> [!IMPORTANT]
> <span data-ttu-id="981a6-131">*Alla filer är i gemener, vilket gör det enkelt att konvertera kommandon till plattforms utvecklings plattformarna för Linux (UNIX).*</span><span class="sxs-lookup"><span data-stu-id="981a6-131">*All files are in lower-case, making it easy to convert the commands to Linux (Unix) development platforms.*</span></span>

## <a name="guix-installation"></a><span data-ttu-id="981a6-132">GUIX-installation</span><span class="sxs-lookup"><span data-stu-id="981a6-132">GUIX Installation</span></span>

<span data-ttu-id="981a6-133">GUIX installeras genom att klona GitHub-lagringsplatsen till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="981a6-133">GUIX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="981a6-134">Följande är en typisk syntax för att skapa en klon av GUIX-lagringsplatsen på din dator:</span><span class="sxs-lookup"><span data-stu-id="981a6-134">The following is typical syntax for creating a clone of the GUIX repository on your PC:</span></span>

```c
    git clone https://github.com/azure-rtos/guix
```

<span data-ttu-id="981a6-135">Alternativt kan du ladda ned en kopia av lagrings platsen med hjälp av knappen Ladda ned på GitHub-huvud sidan.</span><span class="sxs-lookup"><span data-stu-id="981a6-135">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="981a6-136">Du hittar också instruktioner för att skapa GUIX-biblioteket på den första sidan i online-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="981a6-136">You will also find instructions for building the GUIX library on the front page of the online repository.</span></span>

>[!NOTE]  
> <span data-ttu-id="981a6-137">*Program varan behöver åtkomst till biblioteks filen GUIX, vanligt vis kallad **GX. a** (eller **GX. lib**) och C include-filerna **gx_api. h** och **gx_port. h**. Detta åstadkommer du genom att ange lämplig sökväg för utvecklingsverktyg eller genom att kopiera filerna till program utvecklings ytan.*</span><span class="sxs-lookup"><span data-stu-id="981a6-137">*Application software needs access to the GUIX library file, usually called **gx.a** (or **gx.lib**), and the C include files **gx_api.h** and **gx_port.h**. This is accomplished either by setting the appropriate path for the development tools or by copying these files into the application development area.*</span></span>

## <a name="using-guix"></a><span data-ttu-id="981a6-138">Använda GUIX</span><span class="sxs-lookup"><span data-stu-id="981a6-138">Using GUIX</span></span>

<span data-ttu-id="981a6-139">Det är enkelt att använda GUIX.</span><span class="sxs-lookup"><span data-stu-id="981a6-139">Using GUIX is easy.</span></span> <span data-ttu-id="981a6-140">I princip måste program koden innehålla ***gx_api. h** _ under kompilering och länk med GUIX-biblioteket _*_GX. a_\*_ (eller _ *_GX. lib_*) \*.</span><span class="sxs-lookup"><span data-stu-id="981a6-140">Basically, the application code must include ***gx_api.h** _ during compilation and link with the GUIX library _*_gx.a_*_ (or _ *_gx.lib_*)*.</span></span>

<span data-ttu-id="981a6-141">Det finns fyra enkla steg som krävs för att bygga ett GUIX-program:</span><span class="sxs-lookup"><span data-stu-id="981a6-141">There are four easy steps required to build a GUIX application:</span></span>

| <span data-ttu-id="981a6-142">Steg</span><span class="sxs-lookup"><span data-stu-id="981a6-142">Steps</span></span>   | <span data-ttu-id="981a6-143">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="981a6-143">Description</span></span>    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="981a6-144">Steg &nbsp; 1:</span><span class="sxs-lookup"><span data-stu-id="981a6-144">Step&nbsp;1:</span></span> | <span data-ttu-id="981a6-145">Inkludera filen ***gx_api. h*** i alla filer som använder GUIX Services eller data strukturer.</span><span class="sxs-lookup"><span data-stu-id="981a6-145">Include the ***gx_api.h*** file in all application files that use GUIX services or data structures.</span></span>                                                               |
| <span data-ttu-id="981a6-146">Steg &nbsp; 2:</span><span class="sxs-lookup"><span data-stu-id="981a6-146">Step&nbsp;2:</span></span> | <span data-ttu-id="981a6-147">Initiera GUIX-systemet genom att anropa ***gx_system_initialize** _ från funktionen _ *_tx_application_define_** eller en program tråd.</span><span class="sxs-lookup"><span data-stu-id="981a6-147">Initialize the GUIX system by calling ***gx_system_initialize** _ from the _ *_tx_application_define_** function or an application thread.</span></span>                       |
| <span data-ttu-id="981a6-148">Steg &nbsp; 3:</span><span class="sxs-lookup"><span data-stu-id="981a6-148">Step&nbsp;3:</span></span> | <span data-ttu-id="981a6-149">Skapa en visnings instans, skapa en arbets yta för visningen och skapa rot fönstret och alla andra Windows-och widgetar som behövs.</span><span class="sxs-lookup"><span data-stu-id="981a6-149">Create a display instance, create a canvas for the display, and create the root window and any other windows or widgets necessary.</span></span>                                 |
| <span data-ttu-id="981a6-150">Steg &nbsp; 4:</span><span class="sxs-lookup"><span data-stu-id="981a6-150">Step&nbsp;4:</span></span> | <span data-ttu-id="981a6-151">Kompilera program källan och länka med GUIX runtime library \***GX. a** _ (eller _ *_GX. lib_* \*).</span><span class="sxs-lookup"><span data-stu-id="981a6-151">Compile application source and link with the GUIX runtime library ***gx.a** _ (or _*_gx.lib_\*\*).</span></span> <span data-ttu-id="981a6-152">Den resulterande bilden kan laddas ned till målet och köras!</span><span class="sxs-lookup"><span data-stu-id="981a6-152">The resulting image can be downloaded to the target and executed!</span></span> |

## <a name="troubleshooting"></a><span data-ttu-id="981a6-153">Felsökning</span><span class="sxs-lookup"><span data-stu-id="981a6-153">Troubleshooting</span></span>

<span data-ttu-id="981a6-154">Varje GUIX-port levereras med ett demonstrations program som körs på specifik skärm maskin vara.</span><span class="sxs-lookup"><span data-stu-id="981a6-154">Each GUIX port is delivered with a demonstration application that executes on specific display hardware.</span></span> <span data-ttu-id="981a6-155">Samma grundläggande demonstration levereras med alla versioner av GUIX.</span><span class="sxs-lookup"><span data-stu-id="981a6-155">The same basic demonstration is delivered with all versions of GUIX.</span></span> <span data-ttu-id="981a6-156">Det är alltid en bra idé att få demonstrations systemet igång först.</span><span class="sxs-lookup"><span data-stu-id="981a6-156">It is always a good idea to get the demonstration system running first.</span></span>

<span data-ttu-id="981a6-157">Om demonstrations systemet inte körs korrekt utför du följande åtgärder för att begränsa problemet:</span><span class="sxs-lookup"><span data-stu-id="981a6-157">If the demonstration system does not run properly, perform the following operations to narrow the problem:</span></span>

1. <span data-ttu-id="981a6-158">Ta reda på hur mycket av demonstrationen som körs.</span><span class="sxs-lookup"><span data-stu-id="981a6-158">Determine how much of the demonstration is running.</span></span>

2. <span data-ttu-id="981a6-159">Öka stack storleken för GUIX-tråden genom att ändra den konstant **GX_THREAD_STACK_SIZE** och kompilera om GUIX-biblioteket</span><span class="sxs-lookup"><span data-stu-id="981a6-159">Increase the stack size of the GUIX thread by changing the  compile-time constant **GX_THREAD_STACK_SIZE** and recompiling  the GUIX library</span></span>

3. <span data-ttu-id="981a6-160">Kompilera om biblioteket GUIX med lämpliga fel söknings alternativ som anges i avsnittet konfigurations alternativ.</span><span class="sxs-lookup"><span data-stu-id="981a6-160">Recompile the GUIX library with the appropriate debug options listed  in the configuration option section.</span></span>

4. <span data-ttu-id="981a6-161">Granska retur status från alla API-anrop.</span><span class="sxs-lookup"><span data-stu-id="981a6-161">Examine the return status from all API calls.</span></span>

5. <span data-ttu-id="981a6-162">Ta reda på om det finns ett internt systemfel genom att ange en Bryt punkt i funktionen ***_gx_system_error_process***.</span><span class="sxs-lookup"><span data-stu-id="981a6-162">Determine if there is an internal system error by setting a breakpoint at the function ***_gx_system_error_process***.</span></span> <span data-ttu-id="981a6-163">Felkoden och anroparen bör ge LED trådar för vad som kan gå fel.</span><span class="sxs-lookup"><span data-stu-id="981a6-163">There error code and caller should give clues as to what might be going wrong.</span></span>

6. <span data-ttu-id="981a6-164">Kringgå tillfälligt eventuella nyligen gjorda ändringar för att se om problemet försvinner eller ändras.</span><span class="sxs-lookup"><span data-stu-id="981a6-164">Temporarily bypass any recent changes to see if the problem disappears or changes.</span></span> <span data-ttu-id="981a6-165">Sådan information bör vara användbar för Microsofts support tekniker.</span><span class="sxs-lookup"><span data-stu-id="981a6-165">Such information should prove useful to Microsoft support engineers.</span></span>

<span data-ttu-id="981a6-166">Följ de procedurer som beskrivs i avsnittet "vad vi behöver från dig" för att skicka den information som samlas in från fel söknings stegen.</span><span class="sxs-lookup"><span data-stu-id="981a6-166">Follow the procedures outlined in the section titled “What We Need From You” to send the information gathered from the troubleshooting steps.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="981a6-167">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="981a6-167">Configuration Options</span></span>

<span data-ttu-id="981a6-168">Det finns flera konfigurations alternativ när du skapar GUIX-biblioteket och programmet med GUIX.</span><span class="sxs-lookup"><span data-stu-id="981a6-168">There are several configuration options when building the GUIX library and the application using GUIX.</span></span> <span data-ttu-id="981a6-169">De här alternativen används för att justera bibliotekets storlek och funktions sätt för att passa dina program krav bäst.</span><span class="sxs-lookup"><span data-stu-id="981a6-169">These options are used to tune the library size and feature set to best fit your application requirements.</span></span> <span data-ttu-id="981a6-170">Om ditt program till exempel bara har en tråd som använder GUIX API-tjänster, bör konfigurations flaggan **GX_DISABLE_MULTITHREAD_SUPPORT** definieras för att eliminera den kostnad som är kopplad till att skydda viktiga kod avsnitt från Rekvirering av flera trådar.</span><span class="sxs-lookup"><span data-stu-id="981a6-170">For example, if your application will have only one thread utilizing the GUIX API services, the configuration flag **GX_DISABLE_MULTITHREAD_SUPPORT** should be defined to eliminate the overhead associated with protecting critical code sections from pre-emption by multiple threads.</span></span> <span data-ttu-id="981a6-171">De olika konfigurations flaggorna kan definieras i program källan, på kommando raden eller i filen **_gx_user. h_** include.</span><span class="sxs-lookup"><span data-stu-id="981a6-171">The various configuration flags can be defined in the application source, on the command line, or within the **_gx_user.h_** include file.</span></span>

<span data-ttu-id="981a6-172">När GUIX-bibliotekets konfigurations flaggor ändras måste du återskapa både GUIX-biblioteket och programmodulerna för att konfigurations ändringarna ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="981a6-172">Whenever the GUIX library configuration flags are modified, it is required to rebuild both the GUIX library and your application modules for the configuration changes to take effect.</span></span>

<span data-ttu-id="981a6-173">Den fullständiga listan över konfigurations flaggor finns dokumenterad i bilaga H: GUIX Build-Time konfigurations flaggor.</span><span class="sxs-lookup"><span data-stu-id="981a6-173">The complete list of configuration flags is documented in Appendix H: GUIX Build-Time Configuration Flags.</span></span>

## <a name="guix-version-id"></a><span data-ttu-id="981a6-174">GUIX versions-ID</span><span class="sxs-lookup"><span data-stu-id="981a6-174">GUIX Version ID</span></span>

<span data-ttu-id="981a6-175">Den aktuella versionen av GUIX är tillgänglig för både användaren och program varan under körning.</span><span class="sxs-lookup"><span data-stu-id="981a6-175">The current version of GUIX is available to both the user and the application software during runtime.</span></span> <span data-ttu-id="981a6-176">Programmerare kan hämta GUIX-versionen från undersökningen av filen \***gx_port. h** _.</span><span class="sxs-lookup"><span data-stu-id="981a6-176">The programmer can obtain the GUIX version from examination of the \***gx_port.h** _ file.</span></span> <span data-ttu-id="981a6-177">Dessutom innehåller den här filen även en versions historik för motsvarande program program för port program som kan hämta GUIX-versionen genom att undersöka den globala strängen _ *_ _gx_version_id_* _ i _ *_gx_port. h_* \*.</span><span class="sxs-lookup"><span data-stu-id="981a6-177">In addition, this file also contains a version history of the corresponding port Application software can obtain the GUIX version by examining the global string _ *_ _gx_version_id_* _ in _\*_gx_port.h_\*\*.</span></span>

<span data-ttu-id="981a6-178">Program varan kan också hämta versions information från de konstanter som visas nedan definierade i \***gx_api. h**. \* Dessa konstanter identifierar den aktuella produkt versionen efter namn och produktens huvud-och del version.</span><span class="sxs-lookup"><span data-stu-id="981a6-178">Application software can also obtain release information from the constants shown below defined in \***gx_api.h**.\* These constants identify the current product release by name and the product major and minor version.</span></span>

```C
#define __PRODUCT_GUIX__

#define __GUIX_MAJOR_VERSION__

#define __GUIX_MINOR_VERSION__
```
