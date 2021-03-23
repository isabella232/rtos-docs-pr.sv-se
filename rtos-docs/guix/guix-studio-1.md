---
title: Användar guide för GUIX Studio
description: Den här guiden innehåller omfattande information om GUIX Studio, den Microsoft Windows-baserade Rapid UI utvecklings miljön som är särskilt utformad för GUIX runtime-biblioteket från Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6a5d628581d4c6b44ff093bac45790d6e2755349
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827171"
---
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a><span data-ttu-id="8d69c-103">Kapitel 1: Introduktion till Azure återställnings tider GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="8d69c-103">Chapter 1: Introduction to Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="8d69c-104">Azure återställnings tider GUIX Studio är en Microsoft Windows-baserad snabb utvecklings miljö som är särskilt utformad för GUIX runtime-biblioteket från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8d69c-104">Azure RTOS GUIX Studio is a Microsoft Windows-based rapid UI development environment specifically designed for the GUIX runtime library from Microsoft.</span></span>

<span data-ttu-id="8d69c-105">Inbäddade UI-utvecklare kan använda WYSIWYG-skärmbilden i GUIX Studio för att snabbt skapa och uppdatera sitt inbäddade användar gränssnitt med hjälp av GUIX-körnings miljön.</span><span class="sxs-lookup"><span data-stu-id="8d69c-105">Embedded UI Developers can utilize the GUIX Studio WYSIWYG screen designer to quickly create and update their embedded UI using the GUIX run-time environment.</span></span> <span data-ttu-id="8d69c-106">GUIX Studio-design sparas och bevaras i en GUIX Studio-projektfil som har fil namns tillägget. GXP.</span><span class="sxs-lookup"><span data-stu-id="8d69c-106">GUIX Studio designs are saved and maintained in a GUIX Studio project file, which has the extension .gxp.</span></span> <span data-ttu-id="8d69c-107">När designen är klar för körning på målet genererar GUIX Studio C-kod som innehåller all nödvändig GRÄNSSNITTs information och kod.</span><span class="sxs-lookup"><span data-stu-id="8d69c-107">When your design is ready for execution on the target, GUIX Studio generates C code that contains all the necessary UI information and code.</span></span>

## <a name="guix-studio-requirements"></a><span data-ttu-id="8d69c-108">Krav för GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="8d69c-108">GUIX Studio Requirements</span></span>

<span data-ttu-id="8d69c-109">För att fungera korrekt kräver Microsofts GUIX Studio *Windows XP* (eller senare).</span><span class="sxs-lookup"><span data-stu-id="8d69c-109">In order to function properly, Microsoft's GUIX Studio requires *Windows XP* (or above).</span></span> <span data-ttu-id="8d69c-110">Systemet bör ha minst 200 MB RAM-minne, 2 GB ledigt hårddisk utrymme och minst 1024x768 med 256 färger.</span><span class="sxs-lookup"><span data-stu-id="8d69c-110">The system should have a minimum of 200MB of RAM, 2GB of available hard-disk space, and a minimum display of 1024x768 with 256 colors.</span></span> <span data-ttu-id="8d69c-111">Dessutom måste det inbäddade programmet köras på *ThreadX/GUIX v 6.0* eller senare.</span><span class="sxs-lookup"><span data-stu-id="8d69c-111">In addition, the embedded application must be running on *ThreadX/GUIX V6.0* or later.</span></span>

<span data-ttu-id="8d69c-112">Om du vill kunna skapa och köra det inbäddade GRÄNSSNITTs programmet som en fristående Microsoft Windows-körbar fil, behöver du också en kompilerare eller en build-miljö som kan kompilera C-källkod för att skapa en Microsoft Windows-körbar fil.</span><span class="sxs-lookup"><span data-stu-id="8d69c-112">If you would like to be able to build and run the embedded UI application as a stand-alone Microsoft Windows executable, you will also need a compiler or build environment capable of compiling C source code to produce a Microsoft Windows executable.</span></span> <span data-ttu-id="8d69c-113">I utvärderings paketet som ingår i GUIX Studio ingår även Visual Studio 2019-kompatibla projektfiler och lösningar för vart och ett av de tillhandahållna exempel programmen.</span><span class="sxs-lookup"><span data-stu-id="8d69c-113">The evaluation package included with GUIX Studio also includes Visual Studio 2019 compatible project files and solutions for each of the provided example applications.</span></span> <span data-ttu-id="8d69c-114">Om du använder en annan kompilator måste du skapa dina egna projektfiler eller skapa filer för att skapa dina exempel program eller kontakta supporten på https://aka.ms/azrtos-support .</span><span class="sxs-lookup"><span data-stu-id="8d69c-114">If you are using a different compiler, you will need to create your own project files or make files for the purposes of building your example applications, or contact support at https://aka.ms/azrtos-support.</span></span>

## <a name="guix-studio-constraints"></a><span data-ttu-id="8d69c-115">GUIX Studio-begränsningar</span><span class="sxs-lookup"><span data-stu-id="8d69c-115">GUIX Studio Constraints</span></span>

<span data-ttu-id="8d69c-116">Design verktyget GUIX Studio UI design verktyg har flera begränsningar, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8d69c-116">The GUIX Studio UI design tool has several constraints, as follows:</span></span>

- <span data-ttu-id="8d69c-117">Högst 4 visningar per projekt.</span><span class="sxs-lookup"><span data-stu-id="8d69c-117">A maximum of 4 displays per project.</span></span>
- <span data-ttu-id="8d69c-118">Högst 100 000 widgetar per GUIX Studio-projekt.</span><span class="sxs-lookup"><span data-stu-id="8d69c-118">A maximum of 100,000 widgets per GUIX Studio project.</span></span>
- <span data-ttu-id="8d69c-119">Högst 100 000 distinkta resurser, t. ex. färger, teckensnitt, pixelmaps, strängar osv.</span><span class="sxs-lookup"><span data-stu-id="8d69c-119">A maximum of 100,000 distinct resources, e.g., colors, fonts, pixelmaps, strings, etc.</span></span>