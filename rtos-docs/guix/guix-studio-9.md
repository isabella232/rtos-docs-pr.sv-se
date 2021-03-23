---
title: Kommando rad för GUIX Studio
description: GUIX Studio tillhandahåller kommando rads anrop som är användbart för att skapa pipelines som krävs för att uppdatera de Studio-genererade utdatafilerna.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9f9bfc67c524a77b5bf736407bf2ca372ce98308
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826292"
---
# <a name="chapter-9-guix-studio-command-line"></a><span data-ttu-id="635a8-103">Kapitel 9: kommando rads kommando rad för GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="635a8-103">Chapter 9: GUIX Studio Command Line</span></span>

<span data-ttu-id="635a8-104">GUIX Studio stöder kommando rads anrop, vilket är användbart för att skapa pipelines som krävs för att uppdatera de Studio-genererade utdatafilerna.</span><span class="sxs-lookup"><span data-stu-id="635a8-104">GUIX Studio supports command-line invocation,  which is useful for build pipelines that are required to update of the Studio-generated output files.</span></span>

## <a name="command-line-usage"></a><span data-ttu-id="635a8-105">Command-Line användning</span><span class="sxs-lookup"><span data-stu-id="635a8-105">Command-Line Usage</span></span>

<span data-ttu-id="635a8-106">**Användning:** guix_studio \[ alternativ \] \[ argument\]</span><span class="sxs-lookup"><span data-stu-id="635a8-106">**Usage:** guix_studio \[OPTION\] \[ARGUMENT\]</span></span>

<span data-ttu-id="635a8-107">Öppna *. GXP* -projektet.</span><span class="sxs-lookup"><span data-stu-id="635a8-107">Open the *.gxp* project.</span></span>

<span data-ttu-id="635a8-108">Öppna Studio-projektet och generera önskade utdatafiler.</span><span class="sxs-lookup"><span data-stu-id="635a8-108">Open the Studio project and generate desired output files.</span></span>


<span data-ttu-id="635a8-109">**Exempel:**</span><span class="sxs-lookup"><span data-stu-id="635a8-109">**Examples:**</span></span>

`guix_studio demo.gxp`  
<span data-ttu-id="635a8-110">Öppna "demo. GXP"-projekt</span><span class="sxs-lookup"><span data-stu-id="635a8-110">Open "demo.gxp" project</span></span>


`guix_studio.exe –p demo.gxp`  
<span data-ttu-id="635a8-111">Öppna "demo. GXP"-projekt</span><span class="sxs-lookup"><span data-stu-id="635a8-111">Open "demo.gxp" project</span></span>


`guix_studio.exe –n –p demo.gxp`  
<span data-ttu-id="635a8-112">Generera alla utdatafiler för demo. GXP-projektet.</span><span class="sxs-lookup"><span data-stu-id="635a8-112">Generate all output files of demo.gxp project.</span></span>

`guix_studio.exe –n –r –p demo.gxp`  
<span data-ttu-id="635a8-113">Generera resursfiler för demo. GXP-projekt</span><span class="sxs-lookup"><span data-stu-id="635a8-113">Generate resource files of demo.gxp project</span></span>


## <a name="command-line-options"></a><span data-ttu-id="635a8-114">Command-Line alternativ</span><span class="sxs-lookup"><span data-stu-id="635a8-114">Command-Line Options</span></span>

```C
***-n --nogui***  
```

<span data-ttu-id="635a8-115">Alternativet "nogui".</span><span class="sxs-lookup"><span data-stu-id="635a8-115">The "nogui" option.</span></span> <span data-ttu-id="635a8-116">Berätta för GUIX Studio att köra utan att starta GRÄNSSNITTs gränssnittet för Windowing.</span><span class="sxs-lookup"><span data-stu-id="635a8-116">Tell GUIX Studio to run without starting the windowing UI interface.</span></span>

```C
***-o pathname***  
***--log***  
```

<span data-ttu-id="635a8-117">Logg alternativ, ange en loggfil.</span><span class="sxs-lookup"><span data-stu-id="635a8-117">Log option, specify a log file.</span></span>

```C
***-b***  
***--binary***  
```

<span data-ttu-id="635a8-118">Alternativ för binär resurs.</span><span class="sxs-lookup"><span data-stu-id="635a8-118">Binary resource option.</span></span> <span data-ttu-id="635a8-119">Skapar en binär resurs fil i stället för en C-fil.</span><span class="sxs-lookup"><span data-stu-id="635a8-119">Produces a binary resource file rather than a C file.</span></span>

```C
***-d display1, display2***  
***--display***  
```

<span data-ttu-id="635a8-120">Alternativet visnings namn.</span><span class="sxs-lookup"><span data-stu-id="635a8-120">Display names option.</span></span> <span data-ttu-id="635a8-121">Om det här alternativet används inkluderas bara de angivna visnings namnen i alla genererade resurs-eller Specifikations filer.</span><span class="sxs-lookup"><span data-stu-id="635a8-121">If this option is used, then only the specified display names are included in any generated resource or specification files.</span></span> <span data-ttu-id="635a8-122">Om det här alternativet inte används tas alla visningar med.</span><span class="sxs-lookup"><span data-stu-id="635a8-122">If this option is not used,  all displays are included.</span></span>

```C
***-t theme1, theme2***  
***--theme***  
```

<span data-ttu-id="635a8-123">Tema namn (n).</span><span class="sxs-lookup"><span data-stu-id="635a8-123">Theme name(s) option.</span></span> <span data-ttu-id="635a8-124">Om det här alternativet används inkluderas bara de angivna temanamn i alla genererade resurs-eller Specifikations filer.</span><span class="sxs-lookup"><span data-stu-id="635a8-124">If this option is used, then only the specified theme names are included in any generated resource or specification files.</span></span> <span data-ttu-id="635a8-125">Om det här alternativet inte används ingår alla teman.</span><span class="sxs-lookup"><span data-stu-id="635a8-125">If this option is not used, all themes are included.</span></span>

```C
***-l langage1, language2***  
***--language***  
```

<span data-ttu-id="635a8-126">Alternativ för språk namn.</span><span class="sxs-lookup"><span data-stu-id="635a8-126">Language name(s) option.</span></span> <span data-ttu-id="635a8-127">Om det här alternativet används inkluderas de angivna språk namnen i de genererade resurs-eller Specifikations filerna.</span><span class="sxs-lookup"><span data-stu-id="635a8-127">If this option is used,  the specified language names are included in the generated resource or specification files.</span></span> <span data-ttu-id="635a8-128">Annars ingår alla språk namn.</span><span class="sxs-lookup"><span data-stu-id="635a8-128">Otherwise all language names are included.</span></span>

```C
***-r [filename]***  
***--resource***  
```

<span data-ttu-id="635a8-129">Alternativet resurs anger att Studio ska skapa en resurs fil för tidigare angivna visnings alternativ, teman och språk.</span><span class="sxs-lookup"><span data-stu-id="635a8-129">The resource option, specifies that Studio should produce a resource file for previously designated display(s), theme(s), and language(s).</span></span>

```C
***-s [filename]***  
***--specification***  
```

<span data-ttu-id="635a8-130">Alternativet specifikation anger att Studio ska skapa en Specifikations fil för angivna visnings alternativ, teman och språk.</span><span class="sxs-lookup"><span data-stu-id="635a8-130">The specification option, specify that studio should produce a specification file for designated display(s), theme(s), and language(s).</span></span>

```C
***-p project_pathname***  
***--project***  
```

<span data-ttu-id="635a8-131">Alternativet projekt Sök väg anger du det exempel projekt som ska läsas in.</span><span class="sxs-lookup"><span data-stu-id="635a8-131">Project pathname option, specify the example project to be loaded.</span></span>

```C
***-i [pathname]***  
***--import***  
```

<span data-ttu-id="635a8-132">Importera sträng från XLIFF-eller CSV-format fil.</span><span class="sxs-lookup"><span data-stu-id="635a8-132">Import string from xliff or csv format file.</span></span>

<span data-ttu-id="635a8-133">***--big_endian***</span><span class="sxs-lookup"><span data-stu-id="635a8-133">***--big_endian***</span></span>  
<span data-ttu-id="635a8-134">Generera resurs data i big-endian-format.</span><span class="sxs-lookup"><span data-stu-id="635a8-134">Generate resource data in big-endian format.</span></span>
