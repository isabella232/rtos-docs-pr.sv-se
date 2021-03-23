---
title: Kapitel 4 – prestanda analys för Azure återställnings tider-TraceX
description: I det här kapitlet beskrivs prestanda analys verktyget Azure återställnings tider TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 6cf1b5bd5349efd97c3afc8a9e7f57f477f06f8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827537"
---
# <a name="chapter-4---azure-rtos-tracex-performance-analysis"></a><span data-ttu-id="bb4b9-103">Kapitel 4 – prestanda analys för Azure återställnings tider-TraceX</span><span class="sxs-lookup"><span data-stu-id="bb4b9-103">Chapter 4 - Azure RTOS TraceX performance analysis</span></span>

<span data-ttu-id="bb4b9-104">I det här kapitlet beskrivs prestanda analys verktyget Azure återställnings tider TraceX:</span><span class="sxs-lookup"><span data-stu-id="bb4b9-104">This chapter describes the Azure RTOS TraceX performance analysis tool:</span></span>

## <a name="performance-analysis"></a><span data-ttu-id="bb4b9-105">Prestandaanalys</span><span class="sxs-lookup"><span data-stu-id="bb4b9-105">Performance Analysis</span></span>

<span data-ttu-id="bb4b9-106">TraceX tillhandahåller inbyggd prestanda analys av spårningsfiler.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-106">TraceX provides built-in performance analysis of trace files.</span></span> <span data-ttu-id="bb4b9-107">Information som *körnings profil*, *populära tjänster*, *tråds tack användning* och olika *prestanda statistik,* inklusive FileX-och netx *-statistik,* är enkelt att komma åt.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-107">Information such as the *execution profile*, *popular services*, *thread stack usage*, and various *performance statistics,* including FileX and NetX statistics *,* are readily available.</span></span> <span data-ttu-id="bb4b9-108">Den här informationen är tillgänglig via meny alternativet ***Visa*** .</span><span class="sxs-lookup"><span data-stu-id="bb4b9-108">This information is available via the ***View*** menu item.</span></span> 


## <a name="execution-profile"></a><span data-ttu-id="bb4b9-109">Körnings profil</span><span class="sxs-lookup"><span data-stu-id="bb4b9-109">Execution Profile</span></span>

<span data-ttu-id="bb4b9-110">Om du väljer knappen ***skapa körnings profil** _ eller _*_Visa körnings profil_\*_ visas den TraceX körnings profilen för den aktuella inlästa spårnings filen.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-110">Selecting the ***Generate Execution Profile** _ button or _*_View -Execution Profile_\*_ presents the TraceX execution profile for the currently loaded trace file.</span></span> <span data-ttu-id="bb4b9-111">Körnings profilen som är kopplad till exempel demonstrations spårningen för ThreadX visas i _ \* bild 19 \* \*.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-111">The execution profile associated with the sample ThreadX demonstration trace is shown in _\*Figure 19\*\*.</span></span>

![Skärm bild av körnings profilen som är kopplad till exempel demonstrations spårningen för ThreadX.](./media/user-guide/execution_profile.png)

<span data-ttu-id="bb4b9-113">**BILD 19**</span><span class="sxs-lookup"><span data-stu-id="bb4b9-113">**FIGURE 19**</span></span>

<span data-ttu-id="bb4b9-114">Exemplet som visas i **bild 19** visar att nästan 45% av bearbetnings tiden är inuti **_tråd 2_*_ och nästan 51% av bearbetnings tiden är inuti _*_tråd 1_ .** detta är logiskt eftersom Mass spårningen visar dessa trådar som skickar och tar emot meddelanden.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-114">The example shown in **Figure 19** indicates that nearly 45% of the processing time is inside of **_thread 2_*_ and nearly 51% of the processing time is inside of _*_thread 1_** This is logical since the bulk of the trace shows these threads sending and receiving messages.</span></span> <span data-ttu-id="bb4b9-115">De återstående körnings kontexterna har bara en liten mängd körnings tid i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-115">The remaining execution contexts have only a small amount of execution time in this example.</span></span>

## <a name="popular-services"></a><span data-ttu-id="bb4b9-116">Populära tjänster</span><span class="sxs-lookup"><span data-stu-id="bb4b9-116">Popular Services</span></span>

<span data-ttu-id="bb4b9-117">Om du väljer \***visa >populära tjänster** _ presenteras de populära tjänsterna i den just nu inlästa spårnings filen.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-117">Selecting \***View ->Popular Services** _ presents the popular services in the currently loaded trace file.</span></span> <span data-ttu-id="bb4b9-118">Som standard visas den här informationen för hela systemet.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-118">By default, this information is displayed for the entire system.</span></span> <span data-ttu-id="bb4b9-119">De populära tjänsterna för vissa trådar är dock också tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-119">However, the popular services for specific threads are also available.</span></span> <span data-ttu-id="bb4b9-120">De populära tjänsterna i exempel ThreadX demonstrations spårning visas i _ \* bild 20 \* \*.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-120">The popular services in the sample ThreadX demonstration trace are shown in _\*Figure 20\*\*.</span></span>

![Skärm bild av populära tjänster i exemplet ThreadX demo trace.](./media/user-guide/popular_services.png)

<span data-ttu-id="bb4b9-122">**BILD 20**</span><span class="sxs-lookup"><span data-stu-id="bb4b9-122">**FIGURE 20**</span></span>

<span data-ttu-id="bb4b9-123">Exemplet som visas i **bild 20** visar att **_tx_queue_send_*_ och _*_tx_queue_receive_** är de två populäraste tjänsterna i den här spårningen.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-123">The example shown in **Figure 20** indicates that **_tx_queue_send_*_ and _*_tx_queue_receive_** are the two most popular services in this trace.</span></span> <span data-ttu-id="bb4b9-124">Detta är konsekvent med beteendet för standard-ThreadX-demonstrationen som den här spårningen fångas från.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-124">This is consistent with the behavior of the standard ThreadX demonstration from which this trace was captured.</span></span>

<span data-ttu-id="bb4b9-125">Du kan välja vissa trådar för den här analysen genom att använda List rutan längst upp i fönstret.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-125">Specific threads can be selected for this analysis by using the drop down selection list at the top of this window.</span></span> <span data-ttu-id="bb4b9-126">**Bild 21** visar den här analysen för **_tråd 3_**.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-126">**Figure 21** shows this analysis for **_thread 3_**.</span></span>

![Skärm bild av analysen av TraceX populära tjänster.](./media/user-guide/popular_services_thread3.png)

<span data-ttu-id="bb4b9-128">**BILD 21**</span><span class="sxs-lookup"><span data-stu-id="bb4b9-128">**FIGURE 21**</span></span>

## <a name="thread-stack-usage-analysis-for-thread-3"></a><span data-ttu-id="bb4b9-129">Användning av tråds Tacken</span><span class="sxs-lookup"><span data-stu-id="bb4b9-129">Thread Stack Usage</span></span> ![Analys av tråd 3.](./media/user-guide/screen_shot_17.png)

<span data-ttu-id="bb4b9-131">Om du väljer ***generera tråds tack användning** _ knappen eller _*_Visa > tråds tack användningen används_\*_ stack användningen för varje tråd i spårnings filen.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-131">Selecting the ***Generate Thread Stack Usage** _ button or _*_View -> Thread Stack Usage_\*_ presents the stack usage for each thread in the trace file.</span></span> <span data-ttu-id="bb4b9-132">Detta åstadkoms av ThreadX, inklusive den aktuella tråds Tacken i många av spårnings posterna i filen.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-132">This is accomplished by ThreadX including the current thread stack pointer in many of the trace entries in the file.</span></span> <span data-ttu-id="bb4b9-133">En stack användning på 100% anger att stacken har spillat och måste korrigeras i programmet.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-133">A stack usage of 100% indicates the stack has overflowed and must be corrected in the application.</span></span> <span data-ttu-id="bb4b9-134">Om det inte finns någon tråd körning i den här spårnings filen visas stack användningen för den tråden vid 0%.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-134">If there is no thread execution within this trace file, the stack usage for that thread is shown at 0%.</span></span> <span data-ttu-id="bb4b9-135">Användningen av tråds Tacken i exempel ThreadX demonstrations spårning visas i _ \* bild 22 \* \*.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-135">The thread stack usage in the sample ThreadX demonstration trace is shown in _\*Figure 22\*\*.</span></span>

![Skärm bild av TraceX Thread stack-användning.](./media/user-guide/thread_stack_usage.png)

<span data-ttu-id="bb4b9-137">**BILD 22**</span><span class="sxs-lookup"><span data-stu-id="bb4b9-137">**FIGURE 22**</span></span>

<span data-ttu-id="bb4b9-138">Exemplet som visas i **bild 22** visar att de flesta trådar i den här spårningen har mellan 9% och 12% stack användning.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-138">The example shown in **Figure 22** indicates that most threads in this trace have between 9% and 12% stack usage.</span></span>

## <a name="performance-statistics"></a><span data-ttu-id="bb4b9-139">Prestanda statistik</span><span class="sxs-lookup"><span data-stu-id="bb4b9-139">Performance Statistics</span></span>

<span data-ttu-id="bb4b9-140">Om du väljer fliken ***generera prestanda statistik** _ eller _ *_Visa-> prestanda statistik_** visas prestanda statistiken för den aktuella inlästa spårnings filen.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-140">Selecting the ***Generate Performance Statistics** _ button or _ *_View -> Performance Statistics_** presents the performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="bb4b9-141">Som standard visas den här informationen för hela systemet.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-141">By default, this information is displayed for the entire system.</span></span> <span data-ttu-id="bb4b9-142">Prestanda statistiken är dock också tillgänglig för varje enskild tråd.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-142">However, the performance statistics are also available for each specific thread.</span></span>

<span data-ttu-id="bb4b9-143">Prestanda statistiken för exempel ThreadX demonstrations spårning visas i **bild 23**.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-143">The performance statistics of the sample ThreadX demonstration trace are shown in **Figure 23**.</span></span>

![Skärm bild av TraceX prestanda statistik.](./media/user-guide/performance_statistics.png)

<span data-ttu-id="bb4b9-145">**FIGUR 23**</span><span class="sxs-lookup"><span data-stu-id="bb4b9-145">**FIGURE 23**</span></span>

<span data-ttu-id="bb4b9-146">Exemplet som visas i **bild 23** visar att det fanns 18 kontext växlar i den här spårnings filen, samt fem tråds preemptions, 16 tråds pensioner, 19 trådar återupptas och tre avbrott.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-146">The example shown in **Figure 23** indicates that there were 18 context switches in this trace file, as well as five thread preemptions, 16 thread suspensions, 19 thread resumptions, and three interrupts.</span></span> <span data-ttu-id="bb4b9-147">Det gick inte att hitta någon prioritets version i den här spårnings filen.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-147">There were no priority inversions found in this trace file.</span></span> <span data-ttu-id="bb4b9-148">Observera att det finns två kategorier av prioritets versioner, nämligen *deterministiska* och icke *deterministiska*.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-148">Notice there are two categories of priority inversions, namely, *deterministic* and *nondeterministic*.</span></span> <span data-ttu-id="bb4b9-149">Den deterministiska prioritets versionen är en prioritets version där en tråd blockeras på en mutex som ägs av en tråd med lägre prioritet.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-149">Deterministic priority inversions are priority inversion in which a thread is blocked on a mutex owned by a lower priority thread.</span></span> <span data-ttu-id="bb4b9-150">En icke-deterministisk prioritets version är där en annan tråd med lägre prioritet körs under en deterministisk prioritets version.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-150">An nondeterministic priority inversion is where a different lower priority thread runs during a deterministic priority inversion.</span></span> <span data-ttu-id="bb4b9-151">Senare kan orsaka oförutsedd tids beteende i programmet och bör undersökas noggrant.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-151">The later can cause unforeseen timing behavior in the application and should be studied carefully.</span></span>

## <a name="filex-statistics"></a><span data-ttu-id="bb4b9-152">FileX-statistik</span><span class="sxs-lookup"><span data-stu-id="bb4b9-152">FileX Statistics</span></span>

<span data-ttu-id="bb4b9-153">Om du väljer \***visa > FileX statistik** _ visas prestanda statistiken för den aktuella inlästa spårnings filen.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-153">Selecting \***View -> FileX Statistics** _ presents the FileX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="bb4b9-154">Den här informationen visas för hela systemet, på alla öppna... /Media-objekt.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-154">This information is displayed for the entire system, on all opened ../media objects.</span></span> <span data-ttu-id="bb4b9-155">Prestanda statistiken för exempel FileX demonstrations spårning visas i _ \* bild 24 \* \*.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-155">The performance statistics of the sample FileX demonstration trace are shown in _\*Figure 24\*\*.</span></span>

![Skärm bild av FileX-statistiken.](./media/user-guide/filex_statistics.png)

<span data-ttu-id="bb4b9-157">**BILD 24**</span><span class="sxs-lookup"><span data-stu-id="bb4b9-157">**FIGURE 24**</span></span>

<span data-ttu-id="bb4b9-158">Exemplet som visas i **bild 27** visar att det var 19... /media öppnas, 19... /Media stängs, 19... /Media-tömningar, 18 katalog läsningar, 19 katalog skrivningar och 18 katalog-Cachemissar.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-158">The example shown in **Figure 27** indicates there were 19 ../media opens, 19 ../media closes, 19 ../media flushes, 18 directory reads, 19 directory writes, and 18 directory cache misses.</span></span> <span data-ttu-id="bb4b9-159">Ytterligare information kan visas genom att rulla nedåt i statistik fönstret.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-159">Additonal information can be viewed by scrolling down in the statistics window.</span></span>

## <a name="netx-statistics"></a><span data-ttu-id="bb4b9-160">NetX-statistik</span><span class="sxs-lookup"><span data-stu-id="bb4b9-160">NetX Statistics</span></span>

<span data-ttu-id="bb4b9-161">Om du väljer \***Visa netx statistik** _ visas prestanda statistiken för den aktuella inlästa spårnings filen.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-161">Selecting \***View -NetX Statistics** _ presents the NetX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="bb4b9-162">Den här informationen visas för hela systemet.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-162">This information is displayed for the entire system.</span></span> <span data-ttu-id="bb4b9-163">Prestanda statistiken för exempel NetX demonstrations spårning visas i _ \* bild 25 \* \*.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-163">The performance statistics of the sample NetX demonstration trace are shown in _\*Figure 25\*\*.</span></span>

![Skärm bild av NetX-statistiken.](./media/user-guide/netx_statistics.png)

<span data-ttu-id="bb4b9-165">**BILD 25**</span><span class="sxs-lookup"><span data-stu-id="bb4b9-165">**FIGURE 25**</span></span>

<span data-ttu-id="bb4b9-166">Exemplet som visas i **bild 25** anger att det inte fanns några ARP-, ping-eller UDP-händelser, men det fanns 30 IP-paket skickade, 1 368 IP-byte skickade, 30 IP-paket togs emot och 1 360 IP-byte mottogs.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-166">The example shown in **Figure 25** indicates there were no ARP, Ping, or UDP events, but there were 30 IP packets sent, 1,368 IP bytes sent, 30 IP packets received, and 1,360 IP bytes received.</span></span>

## <a name="trace-file-information"></a><span data-ttu-id="bb4b9-167">Spårnings fil information</span><span class="sxs-lookup"><span data-stu-id="bb4b9-167">Trace File Information</span></span>

<span data-ttu-id="bb4b9-168">Om du väljer \***visa > spårnings fil information** _ visar viss grundläggande information om den öppna spårnings filen.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-168">Selecting \***View -> Trace File Information** _ presents some basic information about the opened trace file.</span></span> <span data-ttu-id="bb4b9-169">Den här informationen omfattar filens byte ordning, storlek på tids källan, maximalt antal byte för varje objekt namn och bas adressen för alla spårnings fil pekare.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-169">This information includes the byte order of the file, size of the time source, maximum number of bytes for each object name, and the base address of all trace file pointers.</span></span> <span data-ttu-id="bb4b9-170">_ *Bild 26*\* visar spårnings fil informationen för spårnings filen standard **_demo_threadx. trx_** .</span><span class="sxs-lookup"><span data-stu-id="bb4b9-170">_ *Figure 26*\* shows the trace file information for the standard **_demo_threadx.trx_** trace file.</span></span>

![Skärm bild av fil informationen för TraceX.](./media/user-guide/trace_file_info.png)

<span data-ttu-id="bb4b9-172">**BILD 26**</span><span class="sxs-lookup"><span data-stu-id="bb4b9-172">**FIGURE 26**</span></span>

## <a name="raw-trace-dump"></a><span data-ttu-id="bb4b9-173">Rå stackdump</span><span class="sxs-lookup"><span data-stu-id="bb4b9-173">Raw Trace Dump</span></span>

<span data-ttu-id="bb4b9-174">Om du väljer \***visa > rå spårning dump _ visas** en dialog ruta där du kan namnge filen som innehåller rå stackdump.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-174">Selecting \***View -> Raw Trace Dump** _ presents a dialog to name the file containing the raw trace dump.</span></span> <span data-ttu-id="bb4b9-175">När fil namnet och sökvägen har angetts skapar TraceX den obehandlade spårnings filen i text format och startar _*_notepad.exe_*_ för att visa den.</span><span class="sxs-lookup"><span data-stu-id="bb4b9-175">After the file name and path are entered, TraceX builds the raw trace file in text format and launches _*_notepad.exe_*_ to display it.</span></span> <span data-ttu-id="bb4b9-176">_ *Bild 27*\* visar den obehandlade spårnings fils dumpningen för spårnings filen standard **_demo_threadx. trx_** .</span><span class="sxs-lookup"><span data-stu-id="bb4b9-176">_ *Figure 27*\* shows the raw trace file dump for the standard **_demo_threadx.trx_** trace file.</span></span>

![Skärm bild av rå spårnings dumpning.](./media/user-guide/raw_trace_dump.png)

<span data-ttu-id="bb4b9-178">**BILD 27**</span><span class="sxs-lookup"><span data-stu-id="bb4b9-178">**FIGURE 27**</span></span>
