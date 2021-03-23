---
title: Användar handbok för Azure återställnings tider TraceX
description: Den här guiden innehåller omfattande information om Azure återställnings tider TraceX, Microsoft Windows-baserade system analys verktyg från Microsoft.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 92d886b19a0c67292cd4f6a5f8bd7f9d3106374b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827870"
---
# <a name="about-this-guide"></a><span data-ttu-id="2d1f5-103">Om den här guiden</span><span class="sxs-lookup"><span data-stu-id="2d1f5-103">About this guide</span></span>

<span data-ttu-id="2d1f5-104">Den här guiden innehåller omfattande information om Azure återställnings tider TraceX, Microsoft Windows-baserade system analys verktyg för Microsoft Azure återställnings tider.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-104">This guide contains comprehensive information about Azure RTOS TraceX, the Microsoft Windows-based system analysis tool for Microsoft Azure RTOS.</span></span>

<span data-ttu-id="2d1f5-105">Den är avsedd för den inbäddade programutvecklaren i real tid med Azure återställnings tider ThreadX Real-Time Opera ting system (återställnings tider) och tilläggs komponenter.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-105">It is intended for the embedded real-time software developer using Azure RTOS ThreadX Real-Time Operating System (RTOS) and add-on components.</span></span> <span data-ttu-id="2d1f5-106">Utvecklaren bör vara bekant med Azure återställnings tider-ThreadX Azure återställnings tider-FileX och Azure återställnings tider NetX-koncept.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-106">The developer should be familiar with standard Azure RTOS ThreadX Azure RTOS FileX, and Azure RTOS NetX concepts.</span></span>

## <a name="organization"></a><span data-ttu-id="2d1f5-107">Organisation</span><span class="sxs-lookup"><span data-stu-id="2d1f5-107">Organization</span></span>

- <span data-ttu-id="2d1f5-108">[Kapitel 1](chapter1.md) – innehåller en grundläggande översikt över Azure återställnings tider-TraceX och beskriver relationen till utveckling i real tid.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-108">[Chapter 1](chapter1.md) - contains an basic overview of Azure RTOS TraceX and describes its relationship to real-time development.</span></span>
- <span data-ttu-id="2d1f5-109">[Kapitel 2](chapter2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider-TraceX för att analysera ditt program direkt från lådan.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-109">[Chapter 2](chapter2.md) - gives the basic steps to install and use Azure RTOS TraceX to analyze your application right out of the box.</span></span>
- <span data-ttu-id="2d1f5-110">[Kapitel 3](chapter3.md) – beskriver huvud funktionerna i Azure återställnings tider TraceX.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-110">[Chapter 3](chapter3.md) - describes the main features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="2d1f5-111">[Kapitel 4](chapter4.md) – detaljerade prestanda analys funktioner i Azure återställnings tider TraceX.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-111">[Chapter 4](chapter4.md) - details performance analysis features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="2d1f5-112">[Kapitel 5](chapter5.md) – beskriver hur du konfigurerar Azure återställnings tider ThreadX, Azure återställnings tider FileX och Azure återställnings tider netx för att generera en spårningssession som kan visas av Azure återställnings tider TraceX.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-112">[Chapter 5](chapter5.md) - describes how to set up Azure RTOS ThreadX, Azure RTOS FileX, and Azure RTOS NetX in order to generate a trace buffer that is viewable by Azure RTOS TraceX.</span></span>
- <span data-ttu-id="2d1f5-113">[Kapitel 6](chapter6.md) – beskriver Azure återställnings tider TraceX-händelser i detalj.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-113">[Chapter 6](chapter6.md) - describes Azure RTOS TraceX events in detail.</span></span>
- <span data-ttu-id="2d1f5-114">[Kapitel 7](chapter7.md) – beskriver Azure återställnings tider FileX-händelser i detalj.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-114">[Chapter 7](chapter7.md) - describes Azure RTOS FileX events in detail.</span></span>
- <span data-ttu-id="2d1f5-115">[Kapitel 8](chapter8.md) – beskriver Azure återställnings tider netx-händelser i detalj.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-115">[Chapter 8](chapter8.md) - describes Azure RTOS NetX events in detail.</span></span>
- <span data-ttu-id="2d1f5-116">[Kapitel 9](chapter9.md) – beskriver Azure återställnings tider USBX-händelser i detalj.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-116">[Chapter 9](chapter9.md) - describes Azure RTOS USBX events in detail.</span></span>
- <span data-ttu-id="2d1f5-117">[Kapitel 10](chapter10.md) – beskriver hur du skapar anpassade användar händelser i detalj.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-117">[Chapter 10](chapter10.md) - describes creating custom user events in detail.</span></span>
- <span data-ttu-id="2d1f5-118">[Kapitel 11](chapter11.md) – beskriver den interna spårningssessionen i detalj.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-118">[Chapter 11](chapter11.md) - describes the internal trace buffer in detail.</span></span>
- <span data-ttu-id="2d1f5-119">[Bilaga A](appendix-a.md) – Azure återställnings tider ThreadX-portbaserad fil med en tidsstämpel-källa för att samla in spårnings händelser.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-119">[Appendix A](appendix-a.md) - Azure RTOS ThreadX port-specific file with its time-stamp source for gathering trace events.</span></span>
- <span data-ttu-id="2d1f5-120">[Bilaga B](appendix-b.md) – Azure återställnings tider ThreadX *tx_trace. h* -filen som visar implementerings information om bufferten för händelse spårning.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-120">[Appendix B](appendix-b.md) - Azure RTOS ThreadX *tx_trace.h* file that shows implementation details regarding the event trace buffer.</span></span>
- <span data-ttu-id="2d1f5-121">[Bilaga C](appendix-c.md) – sammanfattar kommando rads verktyg för att konvertera olika fil format till rätt TraceX-binärfiler i Azure återställnings tider.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-121">[Appendix C](appendix-c.md) - Summarizes command line utilities for converting various file formats into proper Azure RTOS TraceX binary files.</span></span>
- <span data-ttu-id="2d1f5-122">[Bilaga D](appendix-d.md) – exempel på dumpnings spårning av filer från olika utvecklingsverktyg.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-122">[Appendix D](appendix-d.md) - Examples of dumping trace files from various development tools.</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="2d1f5-123">Guide konventioner</span><span class="sxs-lookup"><span data-stu-id="2d1f5-123">Guide Conventions</span></span>

<span data-ttu-id="2d1f5-124">*Kursiv stil* – teckensnittet noterar bok titlar, betonar viktiga ord och indikerar variabler.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-124">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="2d1f5-125">**Fetstil** – typsnitt anger fil namn, viktiga ord och betonar viktiga ord och variabler.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-125">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="2d1f5-126">Anger information om anmärkning.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-126">Indicates information of note.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="2d1f5-127">Kund Support Center</span><span class="sxs-lookup"><span data-stu-id="2d1f5-127">Customer Support Center</span></span>

<span data-ttu-id="2d1f5-128">Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-128">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="2d1f5-129">Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:</span><span class="sxs-lookup"><span data-stu-id="2d1f5-129">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="2d1f5-130">En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-130">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="2d1f5-131">En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider-ThreadX som föregåde problemet.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-131">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="2d1f5-132">Innehållet i den *_tx_version_id* strängen som finns i filen *tx_port. h* i distributionen.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-132">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="2d1f5-133">Den här strängen ger oss värdefull information om din kör tids miljö.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-133">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="2d1f5-134">Innehållet i RAM-minnet för *_tx_build_options* ulong-variabeln.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-134">The contents in RAM of the *_tx_build_options* ULONG variable.</span></span> <span data-ttu-id="2d1f5-135">Den här variabeln ger oss information om hur ditt Azure återställnings tider ThreadX-bibliotek har skapats.</span><span class="sxs-lookup"><span data-stu-id="2d1f5-135">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
