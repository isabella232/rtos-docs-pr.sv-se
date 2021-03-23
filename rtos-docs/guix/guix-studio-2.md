---
title: Installation och användning av GUIX Studio
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av GUIX Studio UI system design Tool.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d7b5f94c26842b408ea1b00aeeb78e111bea3623
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827168"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a><span data-ttu-id="98d0a-103">Kapitel 2: installation och användning av GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="98d0a-103">Chapter 2: Installation and Use of GUIX Studio</span></span>

<span data-ttu-id="98d0a-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av GUIX Studio UI system design Tool.</span><span class="sxs-lookup"><span data-stu-id="98d0a-104">This chapter contains a description of various issues related to installation, setup, and usage of the GUIX Studio UI system design tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="98d0a-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="98d0a-105">Product Distribution</span></span>

<span data-ttu-id="98d0a-106">Du kan hämta GUIX Studio-appen från [Microsoft App Store](https://microsoft.com/store/apps) genom att söka efter GUIX Studio, eller genom att gå direkt till [sidan GUIX Studio](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab).</span><span class="sxs-lookup"><span data-stu-id="98d0a-106">You can obtain the GUIX Studio app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for GUIX Studio, or by going directly to [the GUIX Studio page](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="98d0a-107">Gör sedan följande.</span><span class="sxs-lookup"><span data-stu-id="98d0a-107">Then do the following.</span></span>

1. <span data-ttu-id="98d0a-108">Från sidan GUIX Studio i App Store klickar du på knappen **Hämta** eller **Installera** för att ladda ned GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="98d0a-108">From the GUIX Studio page in the App Store, click the **Get** or **Install** button to download GUIX Studio.</span></span>

1. <span data-ttu-id="98d0a-109">Webbläsaren kan visa ett meddelande som frågar om du vill öppna Microsoft Store, som du ser i bilden nedan.</span><span class="sxs-lookup"><span data-stu-id="98d0a-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="98d0a-110">Om det gör det väljer du knappen **Öppna** .</span><span class="sxs-lookup"><span data-stu-id="98d0a-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="98d0a-111">![Välj öppna för att installera GUIX Studio.](./media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="98d0a-111">![Choose Open to install GUIX Studio.](./media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="98d0a-112">När installationen är klar väljer du knappen **Starta** .</span><span class="sxs-lookup"><span data-stu-id="98d0a-112">When the install finishes, choose the **Launch** button.</span></span>

1. <span data-ttu-id="98d0a-113">Första gången som GUIX Studio startar visas en dialog ruta där du tillfrågas om du vill klona GUIX-lagrings platsen till din lokala dator.</span><span class="sxs-lookup"><span data-stu-id="98d0a-113">The first time that GUIX Studio launches, it displays a dialog box asking if you want to clone the GUIX repo to your local computer.</span></span> <span data-ttu-id="98d0a-114">Du kan antingen välja att klona lagrings platsen, peka på där du redan har klonat lagrings platsen eller välja att inte klona lagrings platsen (i så fall är ett exempel projekt installerat på datorn).</span><span class="sxs-lookup"><span data-stu-id="98d0a-114">You can either choose to clone the repository, point to where you have already cloned the repo, or choose not to clone the repo at all (in which case, one example project is installed on your computer).</span></span>
<span data-ttu-id="98d0a-115">![Välj att klona lagrings platsen, peka på en redan klonad lagrings platsen eller hoppa över.](./media/guix-studio/clone-repo.png)</span><span class="sxs-lookup"><span data-stu-id="98d0a-115">![Choose to clone the repo, point to an already-cloned repo, or skip.](./media/guix-studio/clone-repo.png)</span></span>

> <span data-ttu-id="98d0a-116">!</span><span class="sxs-lookup"><span data-stu-id="98d0a-116">!</span></span>[!NOTE]
> <span data-ttu-id="98d0a-117">Du kan gå tillbaka till den här dialog rutan när som helst genom att välja **Konfigurera** från huvud menyn i GUIX Stuido, följt av **GUIX-lagringsplatsen**.</span><span class="sxs-lookup"><span data-stu-id="98d0a-117">You can return to this dialog box at any time by choosing **Configure** from the main menu of GUIX Stuido, followed by **GUIX Repository**.</span></span>

<span data-ttu-id="98d0a-118">När Start processen är klar kan du använda GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="98d0a-118">After the startup process is finished, you will be ready to use GUIX Studio.</span></span>

## <a name="using-guix-studio"></a><span data-ttu-id="98d0a-119">Använda GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="98d0a-119">Using GUIX Studio</span></span>

<span data-ttu-id="98d0a-120">Att använda GUIX Studio är ett enkelt sätt att köra GUIX Studio via knappen "***Starta***".</span><span class="sxs-lookup"><span data-stu-id="98d0a-120">Using GUIX Studio is easy - simply run GUIX Studio via the "***Start***" button.</span></span> <span data-ttu-id="98d0a-121">Nu kommer du att gå med i användar gränssnittet för GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="98d0a-121">At this point you will observe the GUIX Studio UI.</span></span> <span data-ttu-id="98d0a-122">Du är nu redo att använda GUIX Studio för att grafiskt skapa ditt inbäddade användar gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="98d0a-122">You are now ready to use GUIX Studio to graphically create your embedded UI.</span></span> <span data-ttu-id="98d0a-123">Härifrån kan du skapa ett nytt projekt eller öppna ett befintligt projekt, inklusive GUIX-exempel projekt.</span><span class="sxs-lookup"><span data-stu-id="98d0a-123">From here you create a new project or open an existing project, including the GUIX example projects.</span></span>

> [!NOTE]
> <span data-ttu-id="98d0a-124">Du kan också dubbelklicka på en GUIX Studio-projektfil med tillägget "**GXP",** som automatiskt startar GUIX Studio och öppnar det refererade projektet.</span><span class="sxs-lookup"><span data-stu-id="98d0a-124">You can also double-click on any GUIX Studio project file with an extension of "**gxp,**" which will automatically launch GUIX Studio and open the referenced project.</span></span>

## <a name="guix-studio-project-samples"></a><span data-ttu-id="98d0a-125">Projekt exempel för GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="98d0a-125">GUIX Studio Project Samples</span></span>

<span data-ttu-id="98d0a-126">Ett antal exempel på GUIX Studio-projektfiler med tillägget "\***GXP**_" finns i_ \* under katalogen "_samples_\* \*" i installationen.</span><span class="sxs-lookup"><span data-stu-id="98d0a-126">A series of example GUIX Studio project files with the extension "\***gxp**_" are found in the "_\*_Samples_\*\*" sub-directory of your installation.</span></span> <span data-ttu-id="98d0a-127">Dessa färdiga exempel projekt hjälper dig att bli van vid att använda GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="98d0a-127">These pre-built example projects will help you get comfortable with using GUIX Studio.</span></span>

<span data-ttu-id="98d0a-128">En exempel projekt fil som alltid finns är filen \***samples/demo_guix_simple/guix_simple. GXP** _.</span><span class="sxs-lookup"><span data-stu-id="98d0a-128">One example project file that is always present is the file \***samples/demo_guix_simple/guix_simple.gxp** _.</span></span> <span data-ttu-id="98d0a-129">I den här exempel projekt filen visas definitionen av ett enkelt GUIX-gränssnitt, enligt beskrivningen i _ *_kapitel 7_*\* i det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="98d0a-129">This example project file shows the definition of a simple GUIX UI, as described in _ *_Chapter 7_*\* of this document.</span></span>

![Skärm bild av användar gränssnittet för GUIX Studio.](./media/guix-studio/image_10.png)

<span data-ttu-id="98d0a-131">**Bild 1**</span><span class="sxs-lookup"><span data-stu-id="98d0a-131">**Figure 1**</span></span>

## <a name="keyboard-shortcuts"></a><span data-ttu-id="98d0a-132">Kortkommandon</span><span class="sxs-lookup"><span data-stu-id="98d0a-132">Keyboard Shortcuts</span></span>

- <span data-ttu-id="98d0a-133">**CTRL + N:** Nytt projekt</span><span class="sxs-lookup"><span data-stu-id="98d0a-133">**Ctrl + N:** New Project</span></span>
- <span data-ttu-id="98d0a-134">**CTRL + O:** Öppna projekt</span><span class="sxs-lookup"><span data-stu-id="98d0a-134">**Ctrl + O:** Open Project</span></span>
- <span data-ttu-id="98d0a-135">**CTRL + S:** Spara projekt</span><span class="sxs-lookup"><span data-stu-id="98d0a-135">**Ctrl + S:** Save Project</span></span>
- <span data-ttu-id="98d0a-136">**CTRL + SHIFT + S:** Spara projektet som</span><span class="sxs-lookup"><span data-stu-id="98d0a-136">**Ctrl + Shift + S:** Save Project As</span></span>
- <span data-ttu-id="98d0a-137">**Alt + F4:** Programmet</span><span class="sxs-lookup"><span data-stu-id="98d0a-137">**Alt + F4:** Exit</span></span>
