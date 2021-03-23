---
title: Kapitel 2 – installation och användning av Azure återställnings tider TraceX
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av system analys verktyget för Azure återställnings tider-TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 05d7fe3df38c7e8a3480c8ea0d4922a109de9ede
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827573"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a><span data-ttu-id="f296b-103">Kapitel 2 – installation och användning av Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="f296b-103">Chapter 2 - Installation and use of Azure RTOS TraceX</span></span>

<span data-ttu-id="f296b-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av system analys verktyget för Azure återställnings tider-TraceX.</span><span class="sxs-lookup"><span data-stu-id="f296b-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS TraceX system analysis tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="f296b-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="f296b-105">Product Distribution</span></span>

<span data-ttu-id="f296b-106">Du kan hämta TraceX-appen från [Microsoft App Store](https://microsoft.com/store/apps) genom att söka efter TraceX, eller genom att gå direkt till [TraceX-sidan](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab).</span><span class="sxs-lookup"><span data-stu-id="f296b-106">You can obtain the TraceX app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for TraceX, or by going directly to [the TraceX page](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="f296b-107">Gör sedan följande.</span><span class="sxs-lookup"><span data-stu-id="f296b-107">Then do the following.</span></span>

1. <span data-ttu-id="f296b-108">På sidan TraceX i App Store klickar du på knappen **Hämta** eller **Installera** för att installera TraceX.</span><span class="sxs-lookup"><span data-stu-id="f296b-108">From the TraceX page in the App Store, click the **Get** or **Install** button to install TraceX.</span></span>

1. <span data-ttu-id="f296b-109">Webbläsaren kan visa ett meddelande som frågar om du vill öppna Microsoft Store, som du ser i bilden nedan.</span><span class="sxs-lookup"><span data-stu-id="f296b-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="f296b-110">Om det gör det väljer du knappen **Öppna** .</span><span class="sxs-lookup"><span data-stu-id="f296b-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="f296b-111">![Välj öppna för att installera TraceX.](../guix/media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="f296b-111">![Choose Open to install TraceX.](../guix/media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="f296b-112">När installationen är klar väljer du knappen **Starta** .</span><span class="sxs-lookup"><span data-stu-id="f296b-112">When the install finishes, choose the **Launch** button.</span></span> 

## <a name="using-tracex"></a><span data-ttu-id="f296b-113">Använda TraceX</span><span class="sxs-lookup"><span data-stu-id="f296b-113">Using TraceX</span></span>

<span data-ttu-id="f296b-114">Att använda TraceX är lika enkelt som att öppna en spårnings fil i TraceX!</span><span class="sxs-lookup"><span data-stu-id="f296b-114">Using TraceX is as easy as opening a trace file inside TraceX!</span></span> <span data-ttu-id="f296b-115">Kör TraceX via knappen \***Start** _.</span><span class="sxs-lookup"><span data-stu-id="f296b-115">Run TraceX via the \***Start** _ button.</span></span> <span data-ttu-id="f296b-116">Nu kommer du att titta på användar gränssnittet för TraceX (GUI).</span><span class="sxs-lookup"><span data-stu-id="f296b-116">At this point you will observe the TraceX graphic user interface (GUI).</span></span> <span data-ttu-id="f296b-117">Du är nu redo att använda TraceX för att grafiskt visa en befintlig mål spårnings-buffert.</span><span class="sxs-lookup"><span data-stu-id="f296b-117">You are now ready to use TraceX to graphically view an existing target trace buffer.</span></span> <span data-ttu-id="f296b-118">Det gör du enkelt genom att klicka på _ *_fil-> öppna,_*\* sedan ange den binära spårnings filen.</span><span class="sxs-lookup"><span data-stu-id="f296b-118">This is easily done by clicking _ *_File -> Open,_*\* then entering the binary trace file.</span></span>

>[!IMPORTANT]
><span data-ttu-id="f296b-119">*Du kan också dubbelklicka på en spårnings fil med en utökning av **TRX,** som automatiskt startar TraceX.*</span><span class="sxs-lookup"><span data-stu-id="f296b-119">*You can also double-click on any trace file with an extension of **trx,** which will automatically launch TraceX.*</span></span>

![Skärm bild av TraceX-ANVÄNDARGRÄNSSNITTET.](./media/user-guide/screen_shot_8.png)

<span data-ttu-id="f296b-121">**BILD 1**</span><span class="sxs-lookup"><span data-stu-id="f296b-121">**FIGURE 1**</span></span>

>[!IMPORTANT]
><span data-ttu-id="f296b-122">*Se **kapitel 5** för instruktioner om hur du genererar ThreadX i målet med hjälp av.*</span><span class="sxs-lookup"><span data-stu-id="f296b-122">*Refer to **Chapter 5** for instructions on how to generate trace buffers on the target using ThreadX.*</span></span>

## <a name="tracex-examples"></a><span data-ttu-id="f296b-123">TraceX-exempel</span><span class="sxs-lookup"><span data-stu-id="f296b-123">TraceX Examples</span></span>

<span data-ttu-id="f296b-124">Första gången du kör TraceX-programmet eller när TraceX-programmet uppdateras uppmanas du att installera TraceX-exemplen och filen custom_events. trxc i en användardefinierad katalog på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f296b-124">The first time you run the TraceX application, or when the TraceX application is updated, you will be prompted to install the TraceX example trace files and the custom_events.trxc file to a user-defined directory on your local machine.</span></span>

<span data-ttu-id="f296b-125">När det här installations steget har slutförts visas exemplet med tillägget **TRX** i undermappen **TraceFiles** i installationsmappen.</span><span class="sxs-lookup"><span data-stu-id="f296b-125">After this installation step in completed, the example trace files with the extension **trx** are found in the **TraceFiles** subdirectory of your installation folder.</span></span> <span data-ttu-id="f296b-126">De här fördefinierade exemplen hjälper dig att komma igång med att använda TraceX på de spårningsfiler som genereras av ThreadX som körs med ditt program.</span><span class="sxs-lookup"><span data-stu-id="f296b-126">These pre-built examples will help you get comfortable with using TraceX on the trace buffers generated by ThreadX running with your application.</span></span>

<span data-ttu-id="f296b-127">Ett exempel på en spårnings fil är filen \***demo_threadx. trx** _.</span><span class="sxs-lookup"><span data-stu-id="f296b-127">One example trace file always present is the file \***demo_threadx.trx** _.</span></span> <span data-ttu-id="f296b-128">I den här exempel spårnings filen visas körningen av standard demonstrationen av ThreadX, enligt beskrivningen i kapitel 6 i _ThreadX Användar handbok \*.</span><span class="sxs-lookup"><span data-stu-id="f296b-128">This example trace file shows the execution of the standard ThreadX demo, as described in Chapter 6 of the _ThreadX User Guide\*.</span></span>

![Skärm bild av dialog rutan Öppna i TraceX.](./media/user-guide/screen_shot_9.png)

<span data-ttu-id="f296b-130">**BILD 2**</span><span class="sxs-lookup"><span data-stu-id="f296b-130">**FIGURE 2**</span></span>
