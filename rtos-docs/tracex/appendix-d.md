---
title: Bilaga D – dumpning och spårning av spårning
description: Dumpning av den sökta bufferten som skapades av Azure återställnings tider-ThreadX till en fil på värddatorn görs via kommandon och/eller verktyg som tillhandahålls av det verktyg som används för att använda verktyget.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 30f6b5e329feeb2dca37dda391fd738aba587c9a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827723"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a><span data-ttu-id="6165a-103">Bilaga D – dumpning och spårning av spårning</span><span class="sxs-lookup"><span data-stu-id="6165a-103">Appendix D - Dumping and trace buffer</span></span>

<span data-ttu-id="6165a-104">Dumpning av den sökta bufferten som skapades av Azure återställnings tider-ThreadX till en fil på värddatorn görs via kommandon och/eller verktyg som tillhandahålls av det verktyg som används för att använda verktyget.</span><span class="sxs-lookup"><span data-stu-id="6165a-104">Dumping the trace buffer created by Azure RTOS ThreadX to a file on the host computer is done via commands and/or utilities provided by the specific development tool being used.</span></span> <span data-ttu-id="6165a-105">Den här bilagan innehåller exempel på dumpning av en spårningssession till en värd fil i några av de populäraste utvecklingsverktyg som används med ThreadX.</span><span class="sxs-lookup"><span data-stu-id="6165a-105">This appendix contains examples of dumping a trace buffer to a host file in some of the more popular development tools used with ThreadX.</span></span> 

## <a name="benchx-tools"></a><span data-ttu-id="6165a-106">BenchX-verktyg</span><span class="sxs-lookup"><span data-stu-id="6165a-106">BenchX Tools</span></span>

<span data-ttu-id="6165a-107">Det går att dumpa kommandobufferten till en värd fil enkelt med BenchX-verktygen genom att välja \***lagra minne till fil** _ i vyn _ *_Memory_* \*, enligt nedan:</span><span class="sxs-lookup"><span data-stu-id="6165a-107">The trace buffer can be dumped to a host file easily with the BenchX tools by selecting the ***Store Memory To File** _ button within the _*_Memory View_\*\*, as shown below:</span></span>

![Skärm bild av vyn minne i BenchX-verktygen.](./media/user-guide/image642.jpg)

<span data-ttu-id="6165a-109">I det här läget anger du adressen till spårningsprovider, storlek, mål fil namn (inklusive sökväg) och väljer knappen ***Spara*** som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="6165a-109">At this point, specify the trace buffer address, size, destination file name (including path), and select the ***Save*** button as shown below.</span></span> <span data-ttu-id="6165a-110">Då skapas den binära spårnings filen för visning i TraceX.</span><span class="sxs-lookup"><span data-stu-id="6165a-110">This will create the binary trace file for viewing within TraceX.</span></span>

![Skärm bild av dialog rutan Spara BenchX-verktyg.](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a><span data-ttu-id="6165a-112">RealView-verktyg</span><span class="sxs-lookup"><span data-stu-id="6165a-112">RealView Tools</span></span>

<span data-ttu-id="6165a-113">Det går lätt att dumpa kommandobufferten till en värd fil med ARM RealView-verktygen genom att ange följande kommando i kommando tolken i RealView:</span><span class="sxs-lookup"><span data-stu-id="6165a-113">The trace buffer can be dumped to a host file easily with the ARM RealView tools by entering the following command at the command-line prompt in RealView:</span></span>

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

<span data-ttu-id="6165a-114">När åtgärden har slutförts innehåller filen ***trace_file. trx*** den sökta bufferten som börjar på adressen 0x6860 och går upp för att adressera 0xE560.</span><span class="sxs-lookup"><span data-stu-id="6165a-114">Upon completion, the file ***trace_file.trx*** will contain the trace buffer that is located starting at the address 0x6860 and goes up to address 0xE560.</span></span> <span data-ttu-id="6165a-115">Den här filen är klar för visning av TraceX.</span><span class="sxs-lookup"><span data-stu-id="6165a-115">This file is ready for viewing by TraceX.</span></span>

## <a name="iar-tools"></a><span data-ttu-id="6165a-116">IAR-verktyg</span><span class="sxs-lookup"><span data-stu-id="6165a-116">IAR Tools</span></span>

<span data-ttu-id="6165a-117">Spårningssessionen kan dumpas till en värd fil enkelt med IAR-verktygen genom att helt enkelt Högerklicka i vyn minne och välja ***minnet Spara...***</span><span class="sxs-lookup"><span data-stu-id="6165a-117">The trace buffer can be dumped to a host file easily with the IAR tools by simply right-clicking in the memory view and selecting the ***Memory Save…***</span></span> <span data-ttu-id="6165a-118">alternativ, som du ser nedan.</span><span class="sxs-lookup"><span data-stu-id="6165a-118">option, as shown below.</span></span>

![Skärm bild av alternativet för minnes sparande i IAR-verktygen.](./media/user-guide/image0_311.jpg)

<span data-ttu-id="6165a-120">Detta resulterar i att dialog rutan \***minne Spara** _ visas.</span><span class="sxs-lookup"><span data-stu-id="6165a-120">This results in the \***Memory Save** _ dialog to be displayed.</span></span> <span data-ttu-id="6165a-121">Ange start-och slut adress och spårnings filens namn och välj sedan knappen _*_Spara_*_ .</span><span class="sxs-lookup"><span data-stu-id="6165a-121">Enter the starting and ending address and the trace file name, then select the _*_Save_*_ button.</span></span> <span data-ttu-id="6165a-122">I det exempel som visas nedan sparar IAR-verktygen den angivna spårningssessionen i Intel HEX-poster i filen _ *_trace_file. hex_* \*.</span><span class="sxs-lookup"><span data-stu-id="6165a-122">In the example shown below, the IAR tools save the specified trace buffer into Intel HEX records in the file _\*_trace_file.hex_\*\*.</span></span>

![Skärm bild av dialog rutan för att spara IAR-verktyg.](./media/user-guide/image648.jpg)

<span data-ttu-id="6165a-124">Nu har vi en spårnings-buffert Sparad i ***trace_file. hex*** -filen på värden och är klar för visning med TraceX.</span><span class="sxs-lookup"><span data-stu-id="6165a-124">At this point, we have the trace buffer saved in the ***trace_file.hex*** file on the host and is ready for viewing with TraceX.</span></span>

## <a name="codewarrior-tools"></a><span data-ttu-id="6165a-125">CodeWarrior-verktyg</span><span class="sxs-lookup"><span data-stu-id="6165a-125">CodeWarrior Tools</span></span>

<span data-ttu-id="6165a-126">Det går lätt att dumpa kommandobufferten till en värd fil med CodeWarrior-verktygen genom att ange \***Save** _-kommandot i kommando fönstret.</span><span class="sxs-lookup"><span data-stu-id="6165a-126">The trace buffer can be dumped to a host file easily with the CodeWarrior tools by entering the \***save** _ command in the Command Window.</span></span> <span data-ttu-id="6165a-127">I följande exempel _ \*_Save_\*\*-kommando förutsätter att spårningssessionen börjar vid 0x102200 och slutar på 0x109F00:</span><span class="sxs-lookup"><span data-stu-id="6165a-127">The following example _ *_save_*\* command assumes the trace buffer starts at 0x102200 and ends at 0x109F00:</span></span>

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

<span data-ttu-id="6165a-128">Detta resulterar i att den sökta kommandobufferten sparas i filen ***trace_file. trx*** på värden.</span><span class="sxs-lookup"><span data-stu-id="6165a-128">This results in the trace buffer being saved in the file ***trace_file.trx*** on the host.</span></span>

## <a name="mplab-tools"></a><span data-ttu-id="6165a-129">MPLAB-verktyg</span><span class="sxs-lookup"><span data-stu-id="6165a-129">MPLAB Tools</span></span>

<span data-ttu-id="6165a-130">MPLAB kan skapa en TraceX-kompatibel spårnings fil via verktyget export Table, som tillåter export av alla minnes intervall till en värd fil.</span><span class="sxs-lookup"><span data-stu-id="6165a-130">MPLAB can create a TraceX-compatible trace file through its Export Table utility, which allows the export of any range of memory to a host file.</span></span> <span data-ttu-id="6165a-131">Fortsätt enligt följande om du vill använda det här verktyget för att skapa en spårnings fil för TraceX:</span><span class="sxs-lookup"><span data-stu-id="6165a-131">To use this utility to create a trace file for TraceX, proceed as follows:</span></span>

<span data-ttu-id="6165a-132">**Steg 1** Öppna ett minnes fönster genom att välja Visa > minne.</span><span class="sxs-lookup"><span data-stu-id="6165a-132">**Step 1** Open a memory window by selecting View -> Memory.</span></span>

![Skärm bild av det valda minnet på menyn Visa.](./media/user-guide/image0_316.jpg)

<span data-ttu-id="6165a-134">**Steg 2** Högerklicka i **vyn minne** om du vill visa en lista med alternativ.</span><span class="sxs-lookup"><span data-stu-id="6165a-134">**Step 2** Right-click within the **Memory View** to display a list of options.</span></span> <span data-ttu-id="6165a-135">Ange **visnings format – 1 byte** för att välja byte-visning..</span><span class="sxs-lookup"><span data-stu-id="6165a-135">Specify **Display Format -1 Byte** to select byte display..</span></span>

![Skärm bild av vyn minne med alternativet visnings format markerat.](./media/user-guide/image650.png)

![Skärm bild av dialog rutan gå till.](./media/user-guide/image651.jpg)

<span data-ttu-id="6165a-138">**Steg 3** Högerklicka igen i fönstret **minnes visning** och välj **gå till**, så öppnas en dialog ruta där du kan ange adressen till händelsesessionen.</span><span class="sxs-lookup"><span data-stu-id="6165a-138">**Step 3** Right-click again within the **Memory View** Window and select **Go To**, which opens a dialog box that enables you to specify the address of the event buffer.</span></span> <span data-ttu-id="6165a-139">I det här exemplet visas **_event_buffer_** visas.</span><span class="sxs-lookup"><span data-stu-id="6165a-139">This example shows **_event_buffer_** being displayed.</span></span>

![Skärm bild av minnes visning med alternativet gå till valt.](./media/user-guide/image0_312.jpg)

![Skärm bild av ett exempel som visar event_buffer som visas.](./media/user-guide/image653.png)

<span data-ttu-id="6165a-142">**Steg 4** Detta markerar innehållet på den första platsen i spårningssessionen, som alltid är strängen BTXT....</span><span class="sxs-lookup"><span data-stu-id="6165a-142">**Step 4** This highlights the contents of the first location of the trace buffer, which is always the string BTXT….</span></span>

![Skärm bild av den första platsen i den sökta kommandobufferten.](./media/user-guide/image0_313.jpg)

<span data-ttu-id="6165a-144">**Steg 5** Högerklicka sedan igen för att öppna menyn Alternativ och välj **Exportera tabell**.</span><span class="sxs-lookup"><span data-stu-id="6165a-144">**Step 5** Now, right-click again to bring up the options menu, and select **Export Table**.</span></span>

![Skärm bild av vyn minne med alternativet Exportera tabell markerat.](./media/user-guide/image0_314.jpg)

<span data-ttu-id="6165a-146">**Steg 6** Dialog rutan **Exportera tabell** visas, som du ser.</span><span class="sxs-lookup"><span data-stu-id="6165a-146">**Step 6** This brings up the **Export Table** dialog, as shown.</span></span> <span data-ttu-id="6165a-147">Ange det adress intervall som ska exporteras.</span><span class="sxs-lookup"><span data-stu-id="6165a-147">Specify the range of addresses to export.</span></span> <span data-ttu-id="6165a-148">För en 8K-spårningssession, som är fallet i det här exemplet, anger du intervallet 0xA00006AC till 0xA00026AC och anger ett namn för den värd fil som ska skapas (demo_threadx. trx i det här exemplet).</span><span class="sxs-lookup"><span data-stu-id="6165a-148">For an 8K trace buffer, as is the case in this example, specify the range 0xA00006AC to 0xA00026AC, and enter a name for the host file to be created (demo_threadx.trx in this example).</span></span>

<span data-ttu-id="6165a-149">! [[Skärm bild av dialog rutan exportera som.](./media/user-guide/image656.jpg)</span><span class="sxs-lookup"><span data-stu-id="6165a-149">![[Screenshot of the Export As dialog.](./media/user-guide/image656.jpg)</span></span>

<span data-ttu-id="6165a-150">**Steg 7** En fil med namnet **demo_threadx. trx** kommer att skapas på värden och den här filen kan öppnas av TraceX.</span><span class="sxs-lookup"><span data-stu-id="6165a-150">**Step 7** A file named **demo_threadx.trx** will be created on the host, and this file can be opened by TraceX.</span></span>

## <a name="ghs-tools"></a><span data-ttu-id="6165a-151">GHS-verktyg</span><span class="sxs-lookup"><span data-stu-id="6165a-151">GHS Tools</span></span>

<span data-ttu-id="6165a-152">Spårningssessionen kan dumpas till en värd fil enkelt med GHS-verktygen genom att ange följande kommando i kommando tolken i fel söknings kommando fönstret:</span><span class="sxs-lookup"><span data-stu-id="6165a-152">The trace buffer can be dumped to a host file easily with the GHS tools by entering the following command at the command-line prompt in the debug command window:</span></span>

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

<span data-ttu-id="6165a-153">Vid slut för Ande kommer filen **demo_threadx. trx** att innehålla den spårningsprovider som finns i event_buffer med en storlek på 32 768 byte och är klar för visning av TraceX.</span><span class="sxs-lookup"><span data-stu-id="6165a-153">Upon completion, the file **demo_threadx.trx** will contain the trace buffer that is located in the event_buffer with a size of 32,768 bytes and is ready for viewing by TraceX.</span></span>

## <a name="renesas-hew"></a><span data-ttu-id="6165a-154">Renesas HEW</span><span class="sxs-lookup"><span data-stu-id="6165a-154">Renesas HEW</span></span>

<span data-ttu-id="6165a-155">Det går lätt att dumpa kommandobufferten till en värd fil med Renasas HEW-verktygen genom att följa de tre stegen (och under stegen) nedan:</span><span class="sxs-lookup"><span data-stu-id="6165a-155">The trace buffer can be dumped to a host file easily with the Renasas HEW tools by following the three steps (and substeps) below:</span></span>

<span data-ttu-id="6165a-156">**Steg 1** Öppna minnes fönstret.</span><span class="sxs-lookup"><span data-stu-id="6165a-156">**Step 1** Open Memory Window.</span></span>

<span data-ttu-id="6165a-157">! [[Skärm bild av minnes fönstret.](./media/user-guide/image657.jpg)</span><span class="sxs-lookup"><span data-stu-id="6165a-157">![[Screenshot of the Memory Window.](./media/user-guide/image657.jpg)</span></span>

<span data-ttu-id="6165a-158">**Steg 2** Placera markören i minnes fönstret och högerklicka.</span><span class="sxs-lookup"><span data-stu-id="6165a-158">**Step 2** Place cursor within memory window and right click.</span></span>

![Skärm bild av minnes fönstret med alternativet Spara valt.](./media/user-guide/image0_315.jpg)

<span data-ttu-id="6165a-160">**Steg 3** Välj Spara och gör följande i fönstret Spara minne som:</span><span class="sxs-lookup"><span data-stu-id="6165a-160">**Step 3** Select Save, then in the Save Memory As window do the following:</span></span>

- <span data-ttu-id="6165a-161">Välj fil format: Binary.</span><span class="sxs-lookup"><span data-stu-id="6165a-161">Select File format: Binary.</span></span>
- <span data-ttu-id="6165a-162">Ange fil namn: efter behov</span><span class="sxs-lookup"><span data-stu-id="6165a-162">Specify Filename: As Desired</span></span>
- <span data-ttu-id="6165a-163">Ange start adress: trace_buffer</span><span class="sxs-lookup"><span data-stu-id="6165a-163">Specify Start address: trace_buffer</span></span>
- <span data-ttu-id="6165a-164">Ange slut adress: (trace_buffer + storlek)</span><span class="sxs-lookup"><span data-stu-id="6165a-164">Specify End address: (trace_buffer+size)</span></span>
- <span data-ttu-id="6165a-165">Ange åtkomst storlek: 1</span><span class="sxs-lookup"><span data-stu-id="6165a-165">Specify Access size: 1</span></span>
- <span data-ttu-id="6165a-166">Klicka på Spara</span><span class="sxs-lookup"><span data-stu-id="6165a-166">Click Save</span></span>

![Skärm bild av dialog rutan Spara minne som.](./media/user-guide/image659.jpg)