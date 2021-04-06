---
title: Kapitel 1 – Introduktion till körnings profil paketet
description: Det här kapitlet innehåller en introduktion till Azure återställnings tider ThreadX Execution Profile Kit (EPK).
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d30676437535229ad5bdbca10dcc9ca009d6e74
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377654"
---
# <a name="chapter-1--introduction-to-the-execution-profile-kit"></a><span data-ttu-id="ab132-103">Kapitel 1 Introduktion till körnings profil paketet</span><span class="sxs-lookup"><span data-stu-id="ab132-103">Chapter 1  Introduction to the Execution Profile Kit</span></span>

<span data-ttu-id="ab132-104">ThreadX Execution Profile Kit (EPK) innehåller en infrastruktur för program för att dynamiskt spåra körnings tid för trådar, avbryta tjänst rutiner (ISR: er) och inaktiva system förhållanden.</span><span class="sxs-lookup"><span data-stu-id="ab132-104">The ThreadX Execution Profile Kit (EPK) provides an infrastructure for applications to dynamically track execution time for threads, Interrupt Service Routines (ISRs), and idle system conditions.</span></span> <span data-ttu-id="ab132-105">Detta är särskilt användbart för optimering och justering av programmet för högsta prestanda.</span><span class="sxs-lookup"><span data-stu-id="ab132-105">This is especially useful for optimization and tuning the application for maximum performance.</span></span> <span data-ttu-id="ab132-106">Men det är också ett värdefullt fel söknings stöd.</span><span class="sxs-lookup"><span data-stu-id="ab132-106">However, it is also a valuable debug aid.</span></span>

<span data-ttu-id="ab132-107">EPK förlitar \" sig på hookar \" som är inbyggda i ThreadX-schemaläggnings logiken i en sammansättnings kod som anropas för tråd post, tråd avslutning, ISR-post och ISR-utgång.</span><span class="sxs-lookup"><span data-stu-id="ab132-107">The EPK relies on \"hooks\" built into the ThreadX scheduling logic in assembly code that are called on thread entry, thread exit, ISR entry, and ISR exit.</span></span> <span data-ttu-id="ab132-108">EPK-rutinerna beräknar tiden i mellan sådana händelser och lagrar delta tiden i globala variabler samt medlemmar i kontroll blocket för **TX_THREAD** .</span><span class="sxs-lookup"><span data-stu-id="ab132-108">The EPK routines calculate the time in between such events and store the delta time in global variables as well as members of the **TX_THREAD** control block.</span></span>

> [!NOTE]
> <span data-ttu-id="ab132-109">*Utvecklaren är kostnads fri att ändra eller till och med ersätta dessa Hook-funktioner med sin egen logik för att växla i/O-PIN-kod för att tillhandahålla maskin varu synlighet till ett ThreadX program som körs*.</span><span class="sxs-lookup"><span data-stu-id="ab132-109">*The developer is free to modify or even replace these hook functions with their own logic to toggle I/O pins in order to provide hardware visibility to a running ThreadX application*.</span></span>

## 

## <a name="epk-requirements"></a><span data-ttu-id="ab132-110">Krav för EPK</span><span class="sxs-lookup"><span data-stu-id="ab132-110">EPK Requirements</span></span>

<span data-ttu-id="ab132-111">EPK kräver ThreadX 6,0 (eller senare) för att kunna fungera.</span><span class="sxs-lookup"><span data-stu-id="ab132-111">The EPK requires ThreadX 6.0 (or above) in order to operate.</span></span> <span data-ttu-id="ab132-112">EPK kräver också en \" rimlig \" lösning, vilket ökar maskin varu tids källan.</span><span class="sxs-lookup"><span data-stu-id="ab132-112">The EPK also requires a \"reasonable\" resolution, incrementing hardware time source.</span></span> <span data-ttu-id="ab132-113">Den mest rimliga lösningen skulle vanligt vis vara något på en andra skala.</span><span class="sxs-lookup"><span data-stu-id="ab132-113">The most reasonable resolution would typically be something on a microsecond scale.</span></span> <span data-ttu-id="ab132-114">Om upplösningen är för fantastisk, kommer EPK-räknarna att max gränsen för snabbt.</span><span class="sxs-lookup"><span data-stu-id="ab132-114">If the resolution is too great, the EPK counters will max out too quickly.</span></span> <span data-ttu-id="ab132-115">Om upplösningen är för liten går det inte att göra något korrekt.</span><span class="sxs-lookup"><span data-stu-id="ab132-115">Conversely, if the resolution is too small, accurate timing is not possible.</span></span> <span data-ttu-id="ab132-116">Programmets tids källa definieras i \***tx_execution_profile. h** _ av makrot _ \* TX_EXECUTION_TIME_SOURCE \* \*.</span><span class="sxs-lookup"><span data-stu-id="ab132-116">The application time source is defined in ***tx_execution_profile.h** _ by the macro _*TX_EXECUTION_TIME_SOURCE\*\*.</span></span>

<span data-ttu-id="ab132-117">C-kompilatorn måste ha stöd för \" signerad typ som är lång \" för osignerade 64-bitars räknare.</span><span class="sxs-lookup"><span data-stu-id="ab132-117">The C compiler must support the type \"unsigned long long\" for unsigned 64-bit total counters.</span></span> <span data-ttu-id="ab132-118">Dessutom antar EPK att de globala variablerna initieras av kompilatorns start kod för körning.</span><span class="sxs-lookup"><span data-stu-id="ab132-118">Furthermore, the EPK assumes the global variables are initialized by the compiler run-time startup code.</span></span> <span data-ttu-id="ab132-119">Om detta inte är fallet måste de globala variabler som definieras i ***tx_execution_profile. c*** initieras till 0 av programmet.</span><span class="sxs-lookup"><span data-stu-id="ab132-119">If this is not the case, the global variables defined in ***tx_execution_profile.c*** must be initialized to 0 by the application.</span></span>

## <a name="epk-installation"></a><span data-ttu-id="ab132-120">EPK-installation</span><span class="sxs-lookup"><span data-stu-id="ab132-120">EPK Installation</span></span>

<span data-ttu-id="ab132-121">Installera ThreadX-EPK genom att följa stegen nedan och återskapa hela ThreadX-biblioteket och programmet.</span><span class="sxs-lookup"><span data-stu-id="ab132-121">To install the ThreadX EPK, follow the steps below and rebuild the entire ThreadX library and application.</span></span>

1. <span data-ttu-id="ab132-122">Inkludera källfilerna för EPK (***tx_execution_profile. h** _ och _*_tx_execution_profile. c_\*_) i ditt ThreadX Library build-projekt.</span><span class="sxs-lookup"><span data-stu-id="ab132-122">Include the EPK source files (***tx_execution_profile.h** _ and _*_tx_execution_profile.c_\*_) in your ThreadX library build project.</span></span> <span data-ttu-id="ab132-123">Dessa filer kan finnas i [Azure återställnings tider ThreadX-lagrings platsen](<https://github.com/azure-rtos/threadx>) under mappen _ \*_Utility/Execution_Profile_\*\*.</span><span class="sxs-lookup"><span data-stu-id="ab132-123">These files can be in the [Azure RTOS ThreadX repo](<https://github.com/azure-rtos/threadx>) under the _ *_utility/Execution_Profile_*\* folder).</span></span>

1. <span data-ttu-id="ab132-124">I ***tx_port. h** _ definierar du \*TX_THREAD_EXTENSION_3*\* makrot på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="ab132-124">In ***tx_port.h** _, define the _ *TX_THREAD_EXTENSION_3** macro as follows.</span></span>
```
    #define TX_THREAD_EXTENSION_3 unsigned long long tx_thread_execution_time_total; \
    unsigned long tx_thread_execution_time_last_start;
```

3. <span data-ttu-id="ab132-125">Definiera **TX_EXECUTION_TIME_SOURCE** makro i **_tx_execution_profile. h_** för att mappa till din maskin varu tids källa.</span><span class="sxs-lookup"><span data-stu-id="ab132-125">Define the **TX_EXECUTION_TIME_SOURCE** macro in **_tx_execution_profile.h_** to map to your hardware time source.</span></span>

1. <span data-ttu-id="ab132-126">Se till att build-miljön definierar **TX_ENABLE_EXECUTION_CHANGE_NOTIFY** så att schemaläggnings-hookarna anropas från sammansättnings koden för ThreadX.</span><span class="sxs-lookup"><span data-stu-id="ab132-126">Ensure that the build environment defines **TX_ENABLE_EXECUTION_CHANGE_NOTIFY** so that the scheduling hooks are called from the ThreadX assembly code.</span></span>

1. <span data-ttu-id="ab132-127">Om du vill använda 64-bitars tids källa läser du filen ***tx_execution_profile. h*** för instruktioner om hur du kan göra detta.</span><span class="sxs-lookup"><span data-stu-id="ab132-127">If you wish to use 64-bit time source, please review the ***tx_execution_profile.h*** file for instructions on how to accomplish this.</span></span>

1. <span data-ttu-id="ab132-128">Återskapa hela biblioteket och programmet så att alla dessa alternativ är korrekt kompilerade.</span><span class="sxs-lookup"><span data-stu-id="ab132-128">Rebuild the entire library and application so that all of these options are properly compiled-in.</span></span>

<span data-ttu-id="ab132-129">Du är nu redo att använda EPK med ditt program.</span><span class="sxs-lookup"><span data-stu-id="ab132-129">You are now ready to use EPK with your application.</span></span>

##  <a name="epk-example"></a><span data-ttu-id="ab132-130">EPK-exempel</span><span class="sxs-lookup"><span data-stu-id="ab132-130">EPK Example</span></span> 

<span data-ttu-id="ab132-131">Följande är ett exempel på EPK som används i en vanlig ThreadX-demonstration, som kon figurer ATS med en 32-bitars timer-källa som ökar 7,2 gånger per mikrosekund.</span><span class="sxs-lookup"><span data-stu-id="ab132-131">The following is an example of EPK being used on a standard ThreadX demonstration, configured with a 32-bit timer source that increments 7.2 times per microsecond.</span></span> 

<span data-ttu-id="ab132-132">**TX_EXECUTION_TIME_SOURCE** makrot har definierats för att hämta den Minnesmappat timer-registreringen på 0xE0001004 enligt följande.</span><span class="sxs-lookup"><span data-stu-id="ab132-132">The **TX_EXECUTION_TIME_SOURCE** macro is defined to pick up the memory-mapped timer register at 0xE0001004, as follows.</span></span>
```
(EXECUTION_TIME_SOURCE_TYPE) \*((ULONG \*) 0xE0001004)
```

<span data-ttu-id="ab132-133">Att låta demonstrationen köras i fem sekunder ger följande resultat.</span><span class="sxs-lookup"><span data-stu-id="ab132-133">Letting the demonstration run for five seconds yields the following results.</span></span>

![Resultat för att köra demonstrations körningen.](media/demo_results.png)

<span data-ttu-id="ab132-135">Eftersom standard demonstrationen av ThreadX inte har någon inaktiv tid (trådar 1 och 2 körs kontinuerligt), rapporterar EPK på rätt sätt noll för inaktivitet.</span><span class="sxs-lookup"><span data-stu-id="ab132-135">Since the standard ThreadX demonstration has no idle time (threads 1 and 2 run continuously), the EPK correctly reports zero for idle time.</span></span> <span data-ttu-id="ab132-136">Den totala ISR-tiden och tråd värden kan divideras med 7,2 för att kunna härleda mikrosekunderna för varje körnings kategori.</span><span class="sxs-lookup"><span data-stu-id="ab132-136">The ISR total time and thread values may be divided by 7.2 in order to derive the microseconds for each execution category.</span></span> <span data-ttu-id="ab132-137">EPK tillhandahåller också API: er för att få åtkomst till den här informationen (se mer information finns i [kapitel 2](chapter2.md)).</span><span class="sxs-lookup"><span data-stu-id="ab132-137">The EPK also provides APIs to access this information (please see please see [Chapter 2](chapter2.md)).</span></span>