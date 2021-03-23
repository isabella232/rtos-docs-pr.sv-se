---
title: Kapitel 1 – Introduktion till Azure återställnings tider TraceX
description: Azure återställnings tider TraceX är ett Microsoft System Analysis-verktyg som visar information om system händelser som samlats in av ThreadX som körs på ett inbäddat mål.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 3009d13388b3b7e8eca041dc6ede569a5caf5e9b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827684"
---
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a><span data-ttu-id="bbe44-103">Kapitel 1 – Introduktion till Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="bbe44-103">Chapter 1 - Introduction to Azure RTOS TraceX</span></span>

<span data-ttu-id="bbe44-104">Azure återställnings tider TraceX är ett Microsoft System Analysis-verktyg som visar information om system händelser som samlats in av ThreadX som körs på ett inbäddat mål.</span><span class="sxs-lookup"><span data-stu-id="bbe44-104">Azure RTOS TraceX is a Microsoft system analysis tool that displays system event information gathered by ThreadX running on an embedded target.</span></span> <span data-ttu-id="bbe44-105">Användaren ansvarar för att överföra den sökta kommandobufferten som lagras i RAM-minnet i det inbäddade målet till en binär fil på värddatorn.</span><span class="sxs-lookup"><span data-stu-id="bbe44-105">The user is responsible for transferring the trace buffer stored in RAM in the embedded target to a binary file on the host computer.</span></span> <span data-ttu-id="bbe44-106">Användaren kan sedan öppna den här filen med TraceX och analysera mål händelserna grafiskt, diagnostisera system problem och justera ett fungerande program för att förbättra prestanda och resurs hantering.</span><span class="sxs-lookup"><span data-stu-id="bbe44-106">The user can then open this file with TraceX and graphically analyze the target events, diagnosing system problems and tuning a working application to improve performance and resource management.</span></span>

## <a name="tracex-requirements"></a><span data-ttu-id="bbe44-107">Krav för TraceX</span><span class="sxs-lookup"><span data-stu-id="bbe44-107">TraceX Requirements</span></span>

<span data-ttu-id="bbe44-108">TraceX kräver Windows XP (eller senare).</span><span class="sxs-lookup"><span data-stu-id="bbe44-108">TraceX requires Windows XP (or above).</span></span> <span data-ttu-id="bbe44-109">Systemet bör ha minst 192 MB RAM-minne, 2 GB ledigt hårddisk utrymme och en minimal visning av 1024x768 med 256-färger.</span><span class="sxs-lookup"><span data-stu-id="bbe44-109">The system should have a minimum of 192 MB of RAM, 2 GB of available hard-disk space, and a minimum display of 1024x768 with 256 colors.</span></span> <span data-ttu-id="bbe44-110">Dessutom måste programmet köras på ThreadX V 5.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="bbe44-110">In addition, the application must be running on ThreadX V5.0 or later.</span></span>

<span data-ttu-id="bbe44-111">TraceX kräver också att Microsoft .NET Framework installeras, vilket innebär att installations programmet för TraceX sker automatiskt.</span><span class="sxs-lookup"><span data-stu-id="bbe44-111">TraceX also requires the Microsoft .NET framework be installed, which the TraceX installer does automatically.</span></span>

## <a name="tracex-constraints"></a><span data-ttu-id="bbe44-112">TraceX-begränsningar</span><span class="sxs-lookup"><span data-stu-id="bbe44-112">TraceX Constraints</span></span>

<span data-ttu-id="bbe44-113">TraceX har följande begränsningar:</span><span class="sxs-lookup"><span data-stu-id="bbe44-113">TraceX has the following constraints:</span></span>

- <span data-ttu-id="bbe44-114">TraceX-filer är begränsade till högst 32 768 händelser (ungefär 1 MB).</span><span class="sxs-lookup"><span data-stu-id="bbe44-114">TraceX files are limited to a maximum of 32,768 events (roughly 1 MB ).</span></span>
- <span data-ttu-id="bbe44-115">Tids stämplings källan måste ha en rimlig lösning.</span><span class="sxs-lookup"><span data-stu-id="bbe44-115">The time-stamp source must have reasonable resolution.</span></span> <span data-ttu-id="bbe44-116">Om lösningen är för låg, överlappas händelserna.</span><span class="sxs-lookup"><span data-stu-id="bbe44-116">If the resolution is too low, the events will overlap.</span></span> <span data-ttu-id="bbe44-117">Om upplösningen är för hög kan det uppstå långa luckor mellan händelserna.</span><span class="sxs-lookup"><span data-stu-id="bbe44-117">If the resolution is too high, there is potential for long gaps between events.</span></span>
- <span data-ttu-id="bbe44-118">TraceX kan inte korrekt mäta intervall mellan händelser som är större än timer-perioden.</span><span class="sxs-lookup"><span data-stu-id="bbe44-118">TraceX cannot accurately measure intervals between events greater than the timer period.</span></span>
