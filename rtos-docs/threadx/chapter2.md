---
title: Kapitel 2 – installation och användning av Azure återställnings tider ThreadX
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider ThreadX-kärnan med höga prestanda.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e1bf85d363b07c81f226d494107eae9ba18114a7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825455"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a><span data-ttu-id="8974e-103">Kapitel 2 – installation och användning av Azure återställnings tider ThreadX</span><span class="sxs-lookup"><span data-stu-id="8974e-103">Chapter 2 - Installation and Use of Azure RTOS ThreadX</span></span>

<span data-ttu-id="8974e-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider ThreadX-kärnan med höga prestanda.</span><span class="sxs-lookup"><span data-stu-id="8974e-104">This chapter contains a description of various issues related to installation, setup, and usage of the high-performance Azure RTOS ThreadX kernel.</span></span>

## <a name="host-considerations"></a><span data-ttu-id="8974e-105">Värd överväganden</span><span class="sxs-lookup"><span data-stu-id="8974e-105">Host Considerations</span></span>

<span data-ttu-id="8974e-106">Inbäddad program vara utvecklas vanligt vis på Windows-eller Linux-värddatorer (UNIX).</span><span class="sxs-lookup"><span data-stu-id="8974e-106">Embedded software is usually developed on Windows or Linux (Unix) host computers.</span></span> <span data-ttu-id="8974e-107">När programmet har kompilerats, länkats och finns på värden laddas den ned till mål maskin varan för körning.</span><span class="sxs-lookup"><span data-stu-id="8974e-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

<span data-ttu-id="8974e-108">Normalt görs mål hämtningen från utvecklings verktygets fel sökare.</span><span class="sxs-lookup"><span data-stu-id="8974e-108">Usually the target download is done from within the development tool debugger.</span></span> <span data-ttu-id="8974e-109">När nedladdningen är klar ansvarar fel söknings programmet för att tillhandahålla mål körnings kontroll (gå till, stoppa, Bryt punkt osv.) samt åtkomst till minne och processor register.</span><span class="sxs-lookup"><span data-stu-id="8974e-109">After the download has completed, the debugger is responsible for providing target execution control (go, halt, breakpoint, etc.) as well as access to memory and processor registers.</span></span>

<span data-ttu-id="8974e-110">De flesta utvecklings verktyg för fel sökning kommunicerar med mål maskin varan via OCD-anslutningar (on-chip debug) som JTAG (IEEE 1149,1) och fel söknings läge för bakgrunden (BDM).</span><span class="sxs-lookup"><span data-stu-id="8974e-110">Most development tool debuggers communicate with the target hardware via on-chip debug (OCD) connections such as JTAG (IEEE 1149.1) and Background Debug Mode (BDM).</span></span> <span data-ttu-id="8974e-111">Fel sökare kommunicerar också med mål maskin vara via ICE-anslutningar (In-Circuit emulation).</span><span class="sxs-lookup"><span data-stu-id="8974e-111">Debuggers also communicate with target hardware through In-Circuit Emulation (ICE) connections.</span></span> <span data-ttu-id="8974e-112">Både OCD-och ICE-anslutningar ger robusta lösningar med minimalt intrång på den inhemske program varan.</span><span class="sxs-lookup"><span data-stu-id="8974e-112">Both OCD and ICE connections provide robust solutions with minimal intrusion on the target resident software.</span></span>

<span data-ttu-id="8974e-113">För resurser som används på värden levereras käll koden för ThreadX i ASCII-format och kräver cirka 1 MB utrymme på värddatorns hård disk.</span><span class="sxs-lookup"><span data-stu-id="8974e-113">As for resources used on the host, the source code for ThreadX is delivered in ASCII format and requires approximately 1 MByte of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="8974e-114">Mål överväganden</span><span class="sxs-lookup"><span data-stu-id="8974e-114">Target Considerations</span></span>

<span data-ttu-id="8974e-115">ThreadX kräver mellan 2 KByte och 20 KB skrivskyddat minne (ROM) på målet.</span><span class="sxs-lookup"><span data-stu-id="8974e-115">ThreadX requires between 2 KBytes and 20 KBytes of Read Only Memory (ROM) on the target.</span></span> <span data-ttu-id="8974e-116">Det kräver också ytterligare 1 till 2 KByte av målets RAM-minne (Random Access Memory) för ThreadX system stack och andra globala data strukturer.</span><span class="sxs-lookup"><span data-stu-id="8974e-116">It also requires another 1 to 2 KBytes of the target's Random Access Memory (RAM) for the ThreadX system stack and other global data structures.</span></span>

<span data-ttu-id="8974e-117">För timer-relaterade funktioner som tids gränser för tjänst anrop, tids segmentering och programtimers för att fungera, måste den underliggande mål maskin varan tillhandahålla en regelbunden avbrotts källa.</span><span class="sxs-lookup"><span data-stu-id="8974e-117">For timer-related functions like service call time-outs, time-slicing, and application timers to function, the underlying target hardware must provide a periodic interrupt source.</span></span> <span data-ttu-id="8974e-118">Om processorn har den här funktionen används den av ThreadX.</span><span class="sxs-lookup"><span data-stu-id="8974e-118">If the processor has this capability, it is utilized by ThreadX.</span></span> <span data-ttu-id="8974e-119">Annars, om mål processorn inte har möjlighet att generera ett periodiskt avbrott måste användarens maskin vara tillhandahålla den.</span><span class="sxs-lookup"><span data-stu-id="8974e-119">Otherwise, if the target processor does not have the ability to generate a periodic interrupt, the user's hardware must provide it.</span></span> <span data-ttu-id="8974e-120">Installationen och konfigurationen av det tidsinställda avbrottet finns vanligt vis i ***tx_initialize_low_level*** sammansättnings filen i ThreadX-distributionen.</span><span class="sxs-lookup"><span data-stu-id="8974e-120">Setup and configuration of the timer interrupt is typically located in the ***tx_initialize_low_level*** assembly file in the ThreadX distribution.</span></span>

> [!NOTE]
> <span data-ttu-id="8974e-121">*ThreadX fungerar fortfarande även om ingen återkommande timer-källa för avbrott är tillgänglig. Men ingen av de timer-relaterade tjänsterna fungerar.*</span><span class="sxs-lookup"><span data-stu-id="8974e-121">*ThreadX is still functional even if no periodic timer interrupt source is available. However, none of the timer-related services are functional.*</span></span>

## <a name="product-distribution"></a><span data-ttu-id="8974e-122">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="8974e-122">Product Distribution</span></span>

<span data-ttu-id="8974e-123">Azure återställnings tider-ThreadX kan hämtas från vår offentliga käll kods lagrings plats på <https://github.com/azure-rtos/threadx/> .</span><span class="sxs-lookup"><span data-stu-id="8974e-123">Azure RTOS ThreadX can be obtained from our public source code repository at <https://github.com/azure-rtos/threadx/>.</span></span>

<span data-ttu-id="8974e-124">Följande är en lista över flera viktiga filer i lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="8974e-124">The following is a list of several important files in the repository.</span></span>

| <span data-ttu-id="8974e-125">Sökväg</span><span class="sxs-lookup"><span data-stu-id="8974e-125">Filename</span></span> | <span data-ttu-id="8974e-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8974e-126">Description</span></span> |
|------------------- | ----------- |
| <span data-ttu-id="8974e-127">**tx_api. h**</span><span class="sxs-lookup"><span data-stu-id="8974e-127">**tx_api.h**</span></span>                      | <span data-ttu-id="8974e-128">C-huvudfilen som innehåller alla system likställda, data strukturer och tjänst prototyper.</span><span class="sxs-lookup"><span data-stu-id="8974e-128">C header file containing all system equates, data structures, and service prototypes.</span></span>                                                             |
| <span data-ttu-id="8974e-129">**tx_port. h**</span><span class="sxs-lookup"><span data-stu-id="8974e-129">**tx_port.h**</span></span>                     | <span data-ttu-id="8974e-130">C-huvudfil som innehåller alla utvecklings verktyg och targetspecific data definitioner och strukturer.</span><span class="sxs-lookup"><span data-stu-id="8974e-130">C header file containing all development-tool and targetspecific data definitions and structures.</span></span>                                                 |
| <span data-ttu-id="8974e-131">**demo_threadx. c**</span><span class="sxs-lookup"><span data-stu-id="8974e-131">**demo_threadx.c**</span></span>                | <span data-ttu-id="8974e-132">C-fil som innehåller ett litet demo program.</span><span class="sxs-lookup"><span data-stu-id="8974e-132">C file containing a small demo application.</span></span>                                                                                                       |
| <span data-ttu-id="8974e-133">**TX. a (eller TX. lib)**</span><span class="sxs-lookup"><span data-stu-id="8974e-133">**tx.a (or tx.lib)**</span></span>              | <span data-ttu-id="8974e-134">Binär version av ThreadX C-biblioteket som distribueras med *standard* paketet.</span><span class="sxs-lookup"><span data-stu-id="8974e-134">Binary version of the ThreadX C library that is distributed with the *standard* package.</span></span>                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
><span data-ttu-id="8974e-135">*Alla fil namn är i gemener. Med den här namngivnings konventionen blir det enklare att konvertera kommandon till plattformar med Linux (UNIX).*</span><span class="sxs-lookup"><span data-stu-id="8974e-135">*All file names are in lower-case. This naming convention makes it easier to convert the commands to Linux (Unix) development platforms.*</span></span>

## <a name="threadx-installation"></a><span data-ttu-id="8974e-136">ThreadX-installation</span><span class="sxs-lookup"><span data-stu-id="8974e-136">ThreadX Installation</span></span>

<span data-ttu-id="8974e-137">ThreadX installeras genom att klona GitHub-lagringsplatsen till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8974e-137">ThreadX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="8974e-138">Följande är en typisk syntax för att skapa en klon av ThreadX-lagringsplatsen på din dator.</span><span class="sxs-lookup"><span data-stu-id="8974e-138">The following is typical syntax for creating a clone of the ThreadX repository on your PC.</span></span>

```c
    git clone https://github.com/azure-rtos/threadx
```

<span data-ttu-id="8974e-139">Alternativt kan du ladda ned en kopia av lagrings platsen med hjälp av knappen Ladda ned på GitHub-huvud sidan.</span><span class="sxs-lookup"><span data-stu-id="8974e-139">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="8974e-140">Du hittar också instruktioner för att skapa ThreadX-biblioteket på den första sidan i online-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="8974e-140">You will also find instructions for building the ThreadX library on the front page of the online repository.</span></span>

> [!NOTE]
> <span data-ttu-id="8974e-141">\* Program varan behöver åtkomst till biblioteks filen ThreadX (vanligt vis **TX. a** eller **TX. lib**) och C include-filerna **_tx_api. h_* _ och _*_tx_port. h_\*_.</span><span class="sxs-lookup"><span data-stu-id="8974e-141">*Application software needs access to the ThreadX library file (usually **tx.a** or **tx.lib**) and the C include files **_tx_api.h_* _ and _*_tx_port.h_*_.</span></span> <span data-ttu-id="8974e-142">Detta åstadkommer du genom att ange lämplig sökväg för utvecklingsverktyg eller genom att kopiera filerna till program utvecklingen area._</span><span class="sxs-lookup"><span data-stu-id="8974e-142">This is accomplished either by setting the appropriate path for the development tools or by copying these files into the application development area._</span></span>

## <a name="using-threadx"></a><span data-ttu-id="8974e-143">Använda ThreadX</span><span class="sxs-lookup"><span data-stu-id="8974e-143">Using ThreadX</span></span>

<span data-ttu-id="8974e-144">Om du vill använda ThreadX måste program koden innehålla ***tx_api. h** _ under kompileringen och länka med ThreadX för kör tids biblioteket _*_TX. a_\*_ (eller _ *_TX. lib_* \*).</span><span class="sxs-lookup"><span data-stu-id="8974e-144">To use ThreadX, the application code must include ***tx_api.h** _ during compilation and link with the ThreadX run-time library _*_tx.a_*_ (or _*_tx.lib_\*\*).</span></span>

<span data-ttu-id="8974e-145">Det krävs fyra steg för att bygga ett ThreadX-program.</span><span class="sxs-lookup"><span data-stu-id="8974e-145">There are four steps required to build a ThreadX application.</span></span>

1. <span data-ttu-id="8974e-146">Inkludera filen ***tx_api. h*** i alla filer som använder ThreadX Services eller data strukturer.</span><span class="sxs-lookup"><span data-stu-id="8974e-146">Include the ***tx_api.h*** file in all application files that use ThreadX services or data structures.</span></span>

1. <span data-ttu-id="8974e-147">Skapa standard C \*-funktionen **main** _.</span><span class="sxs-lookup"><span data-stu-id="8974e-147">Create the standard C \***main** _ function.</span></span> <span data-ttu-id="8974e-148">Den här funktionen måste slutligen anropa _ *_tx_kernel_enter_*\* för att starta ThreadX.</span><span class="sxs-lookup"><span data-stu-id="8974e-148">This function must eventually call _ *_tx_kernel_enter_*\* to start ThreadX.</span></span> <span data-ttu-id="8974e-149">Programspecifik initiering som inte omfattar ThreadX kan läggas till innan du anger kärnan.</span><span class="sxs-lookup"><span data-stu-id="8974e-149">Application-specific initialization that does not involve ThreadX may be added prior to entering the kernel.</span></span>

      > [!IMPORTANT]
      > <span data-ttu-id="8974e-150">\* ThreadX-inmatnings funktionen \***tx_kernel_enter** _ returnerar inte.</span><span class="sxs-lookup"><span data-stu-id="8974e-150">\*The ThreadX entry function \***tx_kernel_enter** _ does not return.</span></span> <span data-ttu-id="8974e-151">Se därför till att inte placera några bearbetnings-eller funktions anrop efter it._</span><span class="sxs-lookup"><span data-stu-id="8974e-151">So be sure not to place any processing or function calls after it._</span></span>

1. <span data-ttu-id="8974e-152">Skapa funktionen ***tx_application_define*** .</span><span class="sxs-lookup"><span data-stu-id="8974e-152">Create the ***tx_application_define*** function.</span></span> <span data-ttu-id="8974e-153">Det är här som de ursprungliga system resurserna skapas.</span><span class="sxs-lookup"><span data-stu-id="8974e-153">This is where the initial system resources are created.</span></span> <span data-ttu-id="8974e-154">Exempel på system resurser är trådar, köer, minnesmoduler, händelse flaggor grupper, mutexer och semaforer.</span><span class="sxs-lookup"><span data-stu-id="8974e-154">Examples of system resources include threads, queues, memory pools, event flags groups, mutexes, and semaphores.</span></span>

1. <span data-ttu-id="8974e-155">Kompilera program källan och länka med ThreadX körnings bibliotekets ***TX. lib***.</span><span class="sxs-lookup"><span data-stu-id="8974e-155">Compile application source and link with the ThreadX run-time library ***tx.lib***.</span></span> <span data-ttu-id="8974e-156">Den resulterande bilden kan laddas ned till målet och köras!</span><span class="sxs-lookup"><span data-stu-id="8974e-156">The resulting image can be downloaded to the target and executed!</span></span>

## <a name="small-example-system"></a><span data-ttu-id="8974e-157">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="8974e-157">Small Example System</span></span>

<span data-ttu-id="8974e-158">I det lilla exempel systemet i bild 1 visas skapandet av en enskild tråd med prioritet 3.</span><span class="sxs-lookup"><span data-stu-id="8974e-158">The small example system in Figure 1 shows the creation of a single thread with a priority of 3.</span></span> <span data-ttu-id="8974e-159">Tråden körs, ökar en räknare och sedan vilo läge för ett klock streck.</span><span class="sxs-lookup"><span data-stu-id="8974e-159">The thread executes, increments a counter, then sleeps for one clock tick.</span></span>
<span data-ttu-id="8974e-160">Den här processen fortsätter för alltid.</span><span class="sxs-lookup"><span data-stu-id="8974e-160">This process continues forever.</span></span>

```c
#include "tx_api.h"
unsigned long my_thread_counter = 0;
TX_THREAD my_thread;
main( )
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter( );
}
void tx_application_define(void *first_unused_memory)
{
    /* Create my_thread! */
    tx_thread_create(&my_thread, "My Thread",
    my_thread_entry, 0x1234, first_unused_memory, 1024,
    3, 3, TX_NO_TIME_SLICE, TX_AUTO_START);
}
void my_thread_entry(ULONG thread_input)
{
    /* Enter into a forever loop. */
    while(1)
    {
        /* Increment thread counter. */
        my_thread_counter++;
        /* Sleep for 1 tick. */
        tx_thread_sleep(1);
    }
}
```

<span data-ttu-id="8974e-161">**BILD 1. Mall för program utveckling**</span><span class="sxs-lookup"><span data-stu-id="8974e-161">**FIGURE 1. Template for Application Development**</span></span>

<span data-ttu-id="8974e-162">Även om det här är ett enkelt exempel ger det en lämplig mall för verklig program utveckling.</span><span class="sxs-lookup"><span data-stu-id="8974e-162">Although this is a simple example, it provides a good template for real application development.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="8974e-163">Felsökning</span><span class="sxs-lookup"><span data-stu-id="8974e-163">Troubleshooting</span></span>

<span data-ttu-id="8974e-164">Varje ThreadX-port levereras med ett demonstrations program.</span><span class="sxs-lookup"><span data-stu-id="8974e-164">Each ThreadX port is delivered with a demonstration application.</span></span> <span data-ttu-id="8974e-165">Det är alltid en bra idé att först se till att demonstrations systemet körs, antingen på faktiskt mål maskin vara eller simulerad miljö.</span><span class="sxs-lookup"><span data-stu-id="8974e-165">It is always a good idea to first get the demonstration system running—either on actual target hardware or simulated environment.</span></span>

<span data-ttu-id="8974e-166">Om demonstrations systemet inte körs korrekt är följande fel söknings tips.</span><span class="sxs-lookup"><span data-stu-id="8974e-166">If the demonstration system does not execute properly, the following are some troubleshooting tips.</span></span>

1. <span data-ttu-id="8974e-167">Ta reda på hur mycket av demonstrationen som körs.</span><span class="sxs-lookup"><span data-stu-id="8974e-167">Determine how much of the demonstration is running.</span></span>
1. <span data-ttu-id="8974e-168">Öka stack storlekarna (detta är mer viktigt i den faktiska program koden än för demonstrationen).</span><span class="sxs-lookup"><span data-stu-id="8974e-168">Increase stack sizes (this is more important in actual application code than it is for the demonstration).</span></span>
1. <span data-ttu-id="8974e-169">Återskapa ThreadX-biblioteket med TX_ENABLE_STACK_CHECKING definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-169">Rebuild the ThreadX library with TX_ENABLE_STACK_CHECKING defined.</span></span> <span data-ttu-id="8974e-170">Detta aktiverar den inbyggda ThreadX stack-kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8974e-170">This enables the built-in ThreadX stack checking.</span></span>
1. <span data-ttu-id="8974e-171">Kringgå tillfälligt eventuella nyligen gjorda ändringar för att se om problemet försvinner eller ändras.</span><span class="sxs-lookup"><span data-stu-id="8974e-171">Temporarily bypass any recent changes to see if the problem disappears or changes.</span></span> <span data-ttu-id="8974e-172">Sådan information bör vara användbar för support tekniker.</span><span class="sxs-lookup"><span data-stu-id="8974e-172">Such information should prove useful to support engineers.</span></span>

<span data-ttu-id="8974e-173">Följ de procedurer som beskrivs i "[kund Support Center](about-this-guide.md#customer-support-center)" för att skicka den information som samlas in från fel söknings stegen.</span><span class="sxs-lookup"><span data-stu-id="8974e-173">Follow the procedures outlined in "[Customer Support Center](about-this-guide.md#customer-support-center)" to send the information gathered from the troubleshooting steps.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="8974e-174">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="8974e-174">Configuration Options</span></span>

<span data-ttu-id="8974e-175">Det finns flera konfigurations alternativ när du skapar ThreadX-biblioteket och programmet med ThreadX.</span><span class="sxs-lookup"><span data-stu-id="8974e-175">There are several configuration options when building the ThreadX library and the application using ThreadX.</span></span> <span data-ttu-id="8974e-176">Alternativen nedan kan definieras i program källan, på kommando raden eller i filen ***tx_user. h*** include.</span><span class="sxs-lookup"><span data-stu-id="8974e-176">The options below can be defined in the application source, on the command line, or within the ***tx_user.h*** include file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8974e-177">\* Alternativ som definieras i ***tx_user. h** _ används endast om program-och ThreadX-biblioteket har skapats med _ *TX_INCLUDE_USER_DEFINE_FILE** definierat.\*</span><span class="sxs-lookup"><span data-stu-id="8974e-177">*Options defined in ***tx_user.h** _ are applied only if the application and ThreadX library are built with _ *TX_INCLUDE_USER_DEFINE_FILE** defined.*</span></span>

### <a name="smallest-configuration"></a><span data-ttu-id="8974e-178">Minsta konfiguration</span><span class="sxs-lookup"><span data-stu-id="8974e-178">Smallest Configuration</span></span>

<span data-ttu-id="8974e-179">För den minsta tecken storleken bör följande konfigurations alternativ för ThreadX anses vara (i avsaknad av alla andra alternativ).</span><span class="sxs-lookup"><span data-stu-id="8974e-179">For the smallest code size, the following ThreadX configuration options should be considered (in absence of all other options).</span></span>

```c
TX_DISABLE_ERROR_CHECKING
TX_DISABLE_PREEMPTION_THRESHOLD
TX_DISABLE_NOTIFY_CALLBACKS
TX_DISABLE_REDUNDANT_CLEARING
TX_DISABLE_STACK_FILLING
TX_NOT_INTERRUPTABLE
TX_TIMER_PROCESS_IN_ISR
```

### <a name="fastest-configuration"></a><span data-ttu-id="8974e-180">Snabbast konfiguration</span><span class="sxs-lookup"><span data-stu-id="8974e-180">Fastest Configuration</span></span>

<span data-ttu-id="8974e-181">För den snabbaste körningen har samma konfigurations alternativ som används för den minsta konfigurationen, men med dessa alternativ beaktas även.</span><span class="sxs-lookup"><span data-stu-id="8974e-181">For the fastest execution, the same configuration options used for the Smallest Configuration previously, but with these options also considered.</span></span>

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

<span data-ttu-id="8974e-182">[Detaljerade konfigurations alternativ](#detailed-configuration-options) beskrivs.</span><span class="sxs-lookup"><span data-stu-id="8974e-182">[Detailed configuration options](#detailed-configuration-options) are described.</span></span>

### <a name="global-time-source"></a><span data-ttu-id="8974e-183">Global tids källa</span><span class="sxs-lookup"><span data-stu-id="8974e-183">Global Time Source</span></span>

<span data-ttu-id="8974e-184">För andra Microsoft Azure återställnings tider-produkter (FileX, NetX, GUIX, USBX osv.) definierar ThreadX antalet ThreadX timer-Tick som motsvarar en sekund.</span><span class="sxs-lookup"><span data-stu-id="8974e-184">For other Microsoft Azure RTOS products (FileX, NetX, GUIX, USBX, etc.), ThreadX defines the number of ThreadX timer ticks that represents one second.</span></span> <span data-ttu-id="8974e-185">Andra uppfyller sina tids krav baserat på denna konstant.</span><span class="sxs-lookup"><span data-stu-id="8974e-185">Others derive their time requirements based on this constant.</span></span> <span data-ttu-id="8974e-186">Som standard är värdet 100, vilket förutsätter ett periodiskt avbrott i 10ms.</span><span class="sxs-lookup"><span data-stu-id="8974e-186">By default, the value is 100, assuming a 10ms periodic interrupt.</span></span> <span data-ttu-id="8974e-187">Användaren kan åsidosätta det här värdet genom att definiera TX_TIMER_TICKS_PER_SECOND med det önskade värdet i ***tx_port. h*** eller i IDE-eller kommando raden.</span><span class="sxs-lookup"><span data-stu-id="8974e-187">The user may override this value by defining TX_TIMER_TICKS_PER_SECOND with the desired value in ***tx_port.h*** or within the IDE or command line.</span></span>

### <a name="detailed-configuration-options"></a><span data-ttu-id="8974e-188">Detaljerade konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="8974e-188">Detailed Configuration Options</span></span>

<span data-ttu-id="8974e-189">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="8974e-189">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="8974e-190">När det här alternativet är definierat aktiverar det här alternativet insamling av prestanda information i byte-pooler.</span><span class="sxs-lookup"><span data-stu-id="8974e-190">When defined, this option enables the gathering of performance information on byte pools.</span></span> <span data-ttu-id="8974e-191">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-191">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-192">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="8974e-192">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="8974e-193">När det här alternativet är definierat aktiverar det här alternativet insamling av prestanda information i byte-pooler.</span><span class="sxs-lookup"><span data-stu-id="8974e-193">When defined, this option enables the gathering of performance information on byte pools.</span></span> <span data-ttu-id="8974e-194">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-194">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-195">**TX_DISABLE_ERROR_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="8974e-195">**TX_DISABLE_ERROR_CHECKING**</span></span>

<span data-ttu-id="8974e-196">Hoppar över grundläggande fel kontroll av tjänst anrop.</span><span class="sxs-lookup"><span data-stu-id="8974e-196">Bypasses basic service call error checking.</span></span> <span data-ttu-id="8974e-197">När den är definierad i program källan är all grundläggande parameter fel kontroll inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="8974e-197">When defined in the application source, all basic parameter error checking is disabled.</span></span> <span data-ttu-id="8974e-198">Detta kan förbättra prestandan med så mycket som 30% och kan också minska bild storleken.</span><span class="sxs-lookup"><span data-stu-id="8974e-198">This may improve performance by as much as 30% and may also reduce the image size.</span></span>

> [!NOTE]
> <span data-ttu-id="8974e-199">*Det är bara säkert att inaktivera fel kontrollen om programmet kan vara absolut garantera att alla indataparametrar alltid är giltiga under alla omständigheter, inklusive indataparametrar härledda från externa ingångar. Om ogiltiga indata har angetts i API: et med fel kontrollen inaktive rad, är det resulterande beteendet odefinierat och kan leda till minnes skada eller system krasch.*</span><span class="sxs-lookup"><span data-stu-id="8974e-199">*It is only safe to disable error checking if the application can absolutely guarantee all input parameters are always valid under all circumstances, including input parameters derived from external input. If invalid input is supplied to the API with error checking disabled, the resulting behavior is undefined and could result in memory corruption or system crash.*</span></span>

> [!NOTE]
> <span data-ttu-id="8974e-200">*ThreadX API-retur värden påverkas inte genom inaktive ring av fel kontroll visas i fetstil i avsnittet "retur värden" i varje API-beskrivning i kapitel 4. Retur värden i fet stil är ogiltiga om fel kontrollen har inaktiverats med alternativet TX_DISABLE_ERROR_CHECKING.*</span><span class="sxs-lookup"><span data-stu-id="8974e-200">*ThreadX API return values not affected by disabling error checking are listed in bold in the “Return Values” section of each API description in Chapter 4. The nonbold return values are void if error checking is disabled by using the TX_DISABLE_ERROR_CHECKING option.*</span></span>

<span data-ttu-id="8974e-201">**TX_DISABLE_NOTIFY_CALLBACKS**</span><span class="sxs-lookup"><span data-stu-id="8974e-201">**TX_DISABLE_NOTIFY_CALLBACKS**</span></span>

<span data-ttu-id="8974e-202">När det här alternativet är definierat inaktive ras aviserings återanrop för olika ThreadX-objekt.</span><span class="sxs-lookup"><span data-stu-id="8974e-202">When defined, disables the notify callbacks for various ThreadX objects.</span></span> <span data-ttu-id="8974e-203">Genom att använda det här alternativet minskar du kodens storlek och förbättrar prestandan.</span><span class="sxs-lookup"><span data-stu-id="8974e-203">Using this option slightly reduces code size and improves performance.</span></span> <span data-ttu-id="8974e-204">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-204">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-205">**TX_DISABLE_PREEMPTION_THRESHOLD**</span><span class="sxs-lookup"><span data-stu-id="8974e-205">**TX_DISABLE_PREEMPTION_THRESHOLD**</span></span>

<span data-ttu-id="8974e-206">När det här alternativet är definierat inaktive ras avstängningen-tröskelvärdet, vilket minskar kod storleken och ökar prestandan.</span><span class="sxs-lookup"><span data-stu-id="8974e-206">When defined, disables the preemption-threshold feature and slightly reduces code size and improves performance.</span></span> <span data-ttu-id="8974e-207">Naturligtvis är avstängningen-tröskeln inte längre tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="8974e-207">Of course, the preemption-threshold capabilities are no longer available.</span></span> <span data-ttu-id="8974e-208">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-208">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-209">**TX_DISABLE_REDUNDANT_CLEARING**</span><span class="sxs-lookup"><span data-stu-id="8974e-209">**TX_DISABLE_REDUNDANT_CLEARING**</span></span>

<span data-ttu-id="8974e-210">När den är definierad tas logiken bort för att initiera ThreadX globala C-datastrukturer till noll.</span><span class="sxs-lookup"><span data-stu-id="8974e-210">When defined, removes the logic for initializing ThreadX global C data structures to zero.</span></span> <span data-ttu-id="8974e-211">Detta bör endast användas om kompilatorns initierings kod anger alla oinitierade C globala data till noll.</span><span class="sxs-lookup"><span data-stu-id="8974e-211">This should only be used if the compiler's initialization code sets all un-initialized C global data to zero.</span></span> <span data-ttu-id="8974e-212">Genom att använda det här alternativet minskar du kodens storlek och förbättrar prestandan under initieringen.</span><span class="sxs-lookup"><span data-stu-id="8974e-212">Using this option slightly reduces code size and improves performance during initialization.</span></span> <span data-ttu-id="8974e-213">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-213">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-214">**TX_DISABLE_STACK_FILLING**</span><span class="sxs-lookup"><span data-stu-id="8974e-214">**TX_DISABLE_STACK_FILLING**</span></span>

<span data-ttu-id="8974e-215">När det här alternativet är definierat inaktive ras 0xEF-värdet i varje byte av varje tråds stack när de skapas.</span><span class="sxs-lookup"><span data-stu-id="8974e-215">When defined, disables placing the 0xEF value in each byte of each thread's stack when created.</span></span> <span data-ttu-id="8974e-216">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-216">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-217">**TX_ENABLE_EVENT_TRACE**</span><span class="sxs-lookup"><span data-stu-id="8974e-217">**TX_ENABLE_EVENT_TRACE**</span></span>

<span data-ttu-id="8974e-218">När det är definierat aktiverar ThreadX händelse insamlings koden för att skapa en TraceX-spårningssession.</span><span class="sxs-lookup"><span data-stu-id="8974e-218">When defined, ThreadX enables the event gathering code for creating a TraceX trace buffer.</span></span>

<span data-ttu-id="8974e-219">**TX_ENABLE_STACK_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="8974e-219">**TX_ENABLE_STACK_CHECKING**</span></span>

<span data-ttu-id="8974e-220">När det är definierat aktiverar ThreadX körning av stack-kontroll, vilket innefattar analys av hur mycket stack som har använts och granskning av data mönster "avgränsningar" före och efter stackområdet.</span><span class="sxs-lookup"><span data-stu-id="8974e-220">When defined, enables ThreadX run-time stack checking, which includes analysis of how much stack has been used and examination of data pattern "fences" before and after the stack area.</span></span> <span data-ttu-id="8974e-221">Om ett stack fel upptäcks, anropas den registrerade program stackens fel hanterare.</span><span class="sxs-lookup"><span data-stu-id="8974e-221">If a stack error is detected, the registered application stack error handler is called.</span></span> <span data-ttu-id="8974e-222">Det här alternativet resulterar i en något ökad omkostnader och kod storlek.</span><span class="sxs-lookup"><span data-stu-id="8974e-222">This option does result in slightly increased overhead and code size.</span></span> <span data-ttu-id="8974e-223">Läs ***tx_thread_stack_error_notify*** API-funktionen för mer information.</span><span class="sxs-lookup"><span data-stu-id="8974e-223">Review the ***tx_thread_stack_error_notify*** API function for more information.</span></span> <span data-ttu-id="8974e-224">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-224">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-225">**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="8974e-225">**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="8974e-226">När det är definierat aktiverar insamling av prestanda information på händelse flaggor grupper.</span><span class="sxs-lookup"><span data-stu-id="8974e-226">When defined, enables the gathering of performance information on event flags groups.</span></span> <span data-ttu-id="8974e-227">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-227">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-228">**TX_INLINE_THREAD_RESUME_SUSPEND**</span><span class="sxs-lookup"><span data-stu-id="8974e-228">**TX_INLINE_THREAD_RESUME_SUSPEND**</span></span>

<span data-ttu-id="8974e-229">När det här alternativet har definierats förbättrar ThreadX ***tx_thread_resume** _ och _ *_tx_thread_suspend_** API-anrop via kod i rad.</span><span class="sxs-lookup"><span data-stu-id="8974e-229">When defined, ThreadX improves the ***tx_thread_resume** _ and _ *_tx_thread_suspend_** API calls via in-line code.</span></span> <span data-ttu-id="8974e-230">Detta ökar kod storleken men förbättrar prestandan för dessa två API-anrop.</span><span class="sxs-lookup"><span data-stu-id="8974e-230">This increases code size but enhances performance of these two API calls.</span></span>

<span data-ttu-id="8974e-231">**TX_MAX_PRIORITIES**</span><span class="sxs-lookup"><span data-stu-id="8974e-231">**TX_MAX_PRIORITIES**</span></span>

<span data-ttu-id="8974e-232">Definierar prioritets nivåer för ThreadX.</span><span class="sxs-lookup"><span data-stu-id="8974e-232">Defines the priority levels for ThreadX.</span></span> <span data-ttu-id="8974e-233">Giltiga värden är mellan 32 och 1024 (inklusive) och *måste* vara jämnt delbar med 32.</span><span class="sxs-lookup"><span data-stu-id="8974e-233">Legal values range from 32 through 1024 (inclusive) and *must* be evenly divisible by 32.</span></span> <span data-ttu-id="8974e-234">Om antalet tillåtna nivåer ökar ökar RAM-användningen med 128 byte för varje grupp med 32 prioriteter.</span><span class="sxs-lookup"><span data-stu-id="8974e-234">Increasing the number of priority levels supported increases the RAM usage by 128 bytes for every group of 32 priorities.</span></span> <span data-ttu-id="8974e-235">Det finns dock bara en försumbar effekt på prestanda.</span><span class="sxs-lookup"><span data-stu-id="8974e-235">However, there is only a negligible effect on performance.</span></span> <span data-ttu-id="8974e-236">Som standard är det här värdet inställt på 32 prioritets nivåer.</span><span class="sxs-lookup"><span data-stu-id="8974e-236">By default, this value is set to 32 priority levels.</span></span>

<span data-ttu-id="8974e-237">**TX_MINIMUM_STACK**</span><span class="sxs-lookup"><span data-stu-id="8974e-237">**TX_MINIMUM_STACK**</span></span>

<span data-ttu-id="8974e-238">Definierar den minsta stack storleken (i byte).</span><span class="sxs-lookup"><span data-stu-id="8974e-238">Defines the minimum stack size (in bytes).</span></span> <span data-ttu-id="8974e-239">Den används för fel kontroll när trådar skapas.</span><span class="sxs-lookup"><span data-stu-id="8974e-239">It is used for error checking when threads are created.</span></span> <span data-ttu-id="8974e-240">Standardvärdet är port-Specific och finns i ***tx_port. h***.</span><span class="sxs-lookup"><span data-stu-id="8974e-240">The default value is port-specific and is found in ***tx_port.h***.</span></span>

<span data-ttu-id="8974e-241">**TX_MISRA_ENABLE**</span><span class="sxs-lookup"><span data-stu-id="8974e-241">**TX_MISRA_ENABLE**</span></span>

<span data-ttu-id="8974e-242">När det är definierat använder ThreadX MISRA C-kompatibla konventioner.</span><span class="sxs-lookup"><span data-stu-id="8974e-242">When defined, ThreadX utilizes MISRA C compliant conventions.</span></span> <span data-ttu-id="8974e-243">Mer information finns i  ***ThreadX_MISRA_Compliance.pdf*** .</span><span class="sxs-lookup"><span data-stu-id="8974e-243">Refer to  ***ThreadX_MISRA_Compliance.pdf*** for details.</span></span>

<span data-ttu-id="8974e-244">**TX_MUTEX_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="8974e-244">**TX_MUTEX_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="8974e-245">När det är definierat aktiverar insamling av prestanda information på mutexer.</span><span class="sxs-lookup"><span data-stu-id="8974e-245">When defined, enables the gathering of performance information on mutexes.</span></span> <span data-ttu-id="8974e-246">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-246">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-247">**TX_NO_TIMER**</span><span class="sxs-lookup"><span data-stu-id="8974e-247">**TX_NO_TIMER**</span></span>

<span data-ttu-id="8974e-248">När det är definierat är ThreadX timer-logiken helt inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="8974e-248">When defined, the ThreadX timer logic is completely disabled.</span></span> <span data-ttu-id="8974e-249">Detta är användbart i de fall där ThreadX timer-funktioner (tråd ström spar läge, API-tidsgräns, tids segmentering och program timers) inte används.</span><span class="sxs-lookup"><span data-stu-id="8974e-249">This is useful in cases where the ThreadX timer features (thread sleep, API timeouts, time-slicing, and application timers) are not utilized.</span></span> <span data-ttu-id="8974e-250">Om **TX_NO_TIMER** anges måste alternativet **TX_TIMER_PROCESS_IN_ISR** också definieras.</span><span class="sxs-lookup"><span data-stu-id="8974e-250">If **TX_NO_TIMER** is specified, the option **TX_TIMER_PROCESS_IN_ISR** must also be defined.</span></span>

<span data-ttu-id="8974e-251">**TX_NOT_INTERRUPTABLE**</span><span class="sxs-lookup"><span data-stu-id="8974e-251">**TX_NOT_INTERRUPTABLE**</span></span>

<span data-ttu-id="8974e-252">När det här är definierat försöker ThreadX inte minimera avbrotts utelåsnings tiden.</span><span class="sxs-lookup"><span data-stu-id="8974e-252">When defined, ThreadX does not attempt to minimize interrupt lockout time.</span></span> <span data-ttu-id="8974e-253">Detta resulterar i snabbare körning men ökar snabbt avbrotts utelåsnings tiden.</span><span class="sxs-lookup"><span data-stu-id="8974e-253">This results in faster execution but does slightly increase interrupt lockout time.</span></span>

<span data-ttu-id="8974e-254">**TX_QUEUE_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="8974e-254">**TX_QUEUE_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="8974e-255">När det är definierat aktiverar insamling av prestanda information i köer.</span><span class="sxs-lookup"><span data-stu-id="8974e-255">When defined, enables the gathering of performance information on queues.</span></span> <span data-ttu-id="8974e-256">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-256">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-257">**TX_REACTIVATE_INLINE**</span><span class="sxs-lookup"><span data-stu-id="8974e-257">**TX_REACTIVATE_INLINE**</span></span>

<span data-ttu-id="8974e-258">När det här definieras utförs återaktivering av ThreadX timers infogade timers i stället för att använda ett funktions anrop.</span><span class="sxs-lookup"><span data-stu-id="8974e-258">When defined, performs reactivation of ThreadX timers inline instead of using a function call.</span></span> <span data-ttu-id="8974e-259">Detta förbättrar prestandan, men ökar kod storleken något.</span><span class="sxs-lookup"><span data-stu-id="8974e-259">This improves performance but slightly increases code size.</span></span> <span data-ttu-id="8974e-260">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-260">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-261">**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="8974e-261">**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="8974e-262">När det är definierat aktiverar insamling av prestanda information för semaforer.</span><span class="sxs-lookup"><span data-stu-id="8974e-262">When defined, enables the gathering of performance information on semaphores.</span></span> <span data-ttu-id="8974e-263">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-263">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-264">**TX_THREAD_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="8974e-264">**TX_THREAD_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="8974e-265">När det är definierat aktiverar insamling av prestanda information på trådar.</span><span class="sxs-lookup"><span data-stu-id="8974e-265">When defined, enables the gathering of performance information on threads.</span></span> <span data-ttu-id="8974e-266">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-266">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-267">**TX_TIMER_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="8974e-267">**TX_TIMER_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="8974e-268">När det är definierat aktiverar insamling av prestanda information för timers.</span><span class="sxs-lookup"><span data-stu-id="8974e-268">When defined, enables the gathering of performance information on timers.</span></span> <span data-ttu-id="8974e-269">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-269">By default, this option is not defined.</span></span>

<span data-ttu-id="8974e-270">**TX_TIMER_PROCESS_IN_ISR**</span><span class="sxs-lookup"><span data-stu-id="8974e-270">**TX_TIMER_PROCESS_IN_ISR**</span></span>

<span data-ttu-id="8974e-271">När det här alternativet är definierat elimineras den interna systemets timer-tråd för ThreadX.</span><span class="sxs-lookup"><span data-stu-id="8974e-271">When defined, eliminates the internal system timer thread for ThreadX.</span></span> <span data-ttu-id="8974e-272">Detta resulterar i bättre prestanda vid timer-händelser och mindre RAM-krav eftersom timer-stacken och kontroll blocket inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="8974e-272">This results in improved performance on timer events and smaller RAM requirements because the timer stack and control block are no longer needed.</span></span> <span data-ttu-id="8974e-273">Om du använder det här alternativet flyttas all timer för förfallo tid till ISR-nivå.</span><span class="sxs-lookup"><span data-stu-id="8974e-273">However, using this option moves all the timer expiration processing to the timer ISR level.</span></span> <span data-ttu-id="8974e-274">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="8974e-274">By default, this option is not defined.</span></span>

> [!NOTE]
> <span data-ttu-id="8974e-275">*Tjänster som tillåts från timers är kanske inte tillåtna från ISR: er och kan därför inte användas när du använder det här alternativet.*</span><span class="sxs-lookup"><span data-stu-id="8974e-275">*Services allowed from timers may not be allowed from ISRs and thus might not be allowed when using this option.*</span></span>

<span data-ttu-id="8974e-276">**TX_TIMER_THREAD_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="8974e-276">**TX_TIMER_THREAD_PRIORITY**</span></span>

<span data-ttu-id="8974e-277">Definierar prioriteten för den interna ThreadX system timer-tråden.</span><span class="sxs-lookup"><span data-stu-id="8974e-277">Defines the priority of the internal ThreadX system timer thread.</span></span> <span data-ttu-id="8974e-278">Standardvärdet är Priority 0, högst prioritet i ThreadX.</span><span class="sxs-lookup"><span data-stu-id="8974e-278">The default value is priority 0—the highest priority in ThreadX.</span></span> <span data-ttu-id="8974e-279">Standardvärdet är definierat i ***tx_port. h***.</span><span class="sxs-lookup"><span data-stu-id="8974e-279">The default value is defined in ***tx_port.h***.</span></span>

<span data-ttu-id="8974e-280">**TX_TIMER_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="8974e-280">**TX_TIMER_THREAD_STACK_SIZE**</span></span>

<span data-ttu-id="8974e-281">Definierar stack storleken (i byte) för den interna ThreadX system timer-tråden.</span><span class="sxs-lookup"><span data-stu-id="8974e-281">Defines the stack size (in bytes) of the internal ThreadX system timer thread.</span></span> <span data-ttu-id="8974e-282">Den här tråden bearbetar alla tråd Ströms begär Anden och alla tids gränser för tjänst anrop.</span><span class="sxs-lookup"><span data-stu-id="8974e-282">This thread processes all thread sleep requests as well as all service call timeouts.</span></span> <span data-ttu-id="8974e-283">Dessutom anropas alla rutiner för återanrop från program timer från den här kontexten.</span><span class="sxs-lookup"><span data-stu-id="8974e-283">In addition, all application timer callback routines are invoked from this context.</span></span> <span data-ttu-id="8974e-284">Standardvärdet är port-Specific och finns i ***tx_port. h***.</span><span class="sxs-lookup"><span data-stu-id="8974e-284">The default value is port-specific and is found in ***tx_port.h***.</span></span>

## <a name="threadx-version-id"></a><span data-ttu-id="8974e-285">ThreadX versions-ID</span><span class="sxs-lookup"><span data-stu-id="8974e-285">ThreadX Version ID</span></span>

<span data-ttu-id="8974e-286">Programmerare kan hämta ThreadX-versionen från undersökningen av filen \***tx_port. h** _.</span><span class="sxs-lookup"><span data-stu-id="8974e-286">The programmer can obtain the ThreadX version from examination of the \***tx_port.h** _ file.</span></span> <span data-ttu-id="8974e-287">Dessutom innehåller den här filen även en versions historik för motsvarande port.</span><span class="sxs-lookup"><span data-stu-id="8974e-287">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="8974e-288">Program varan kan hämta ThreadX-versionen genom att undersöka den globala strängen _ \* _tx_version_id \* \*.</span><span class="sxs-lookup"><span data-stu-id="8974e-288">Application software can obtain the ThreadX version by examining the global string _\*_tx_version_id\*\*.</span></span>
