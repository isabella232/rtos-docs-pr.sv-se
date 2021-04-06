---
title: Kapitel 1 – Introduktion till Azure återställnings tider ThreadX for ARMv8-M.
description: Det här kapitlet är start punkten för läsning av Azure återställnings tider ThreadX-tillägget för ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 486466f41e64adb9e32ebbd21a22629221ffa9c1
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377627"
---
# <a name="chapter-1--overview"></a><span data-ttu-id="2f159-103">Översikt över kapitel 1</span><span class="sxs-lookup"><span data-stu-id="2f159-103">Chapter 1  Overview</span></span>

<span data-ttu-id="2f159-104">ARMv8-M-arkitekturen introducerar nya säkerhetsfunktioner, inklusive TrustZone, vilket gör att minnet kan taggas som säkert eller osäkert.</span><span class="sxs-lookup"><span data-stu-id="2f159-104">The ARMv8-M architecture introduces new security features, including TrustZone, which allows memory to be tagged as secure or non-secure.</span></span> <span data-ttu-id="2f159-105">Följande ARM-rikt linjer, ThreadX (och användar programmet) har utformats för att köras i icke-säkert läge.</span><span class="sxs-lookup"><span data-stu-id="2f159-105">Following ARM's guidelines, ThreadX (and the user application) is designed to be run in non-secure mode.</span></span> <span data-ttu-id="2f159-106">ThreadX (och användar programmet) kan också köras i säkert läge.</span><span class="sxs-lookup"><span data-stu-id="2f159-106">ThreadX (and the user application) can also be run in secure mode.</span></span> <span data-ttu-id="2f159-107">Vissa nya ThreadX-API: er krävs för att gränssnittet ska kunna hanteras med program vara i Secure Mode.</span><span class="sxs-lookup"><span data-stu-id="2f159-107">In order to interface with secure mode software, some new ThreadX APIs are necessary.</span></span> <span data-ttu-id="2f159-108">Det här dokumentet beskriver de här ThreadX-tjänsterna som är speciella för ARMv8-M-arkitekturen, inklusive cortex-M23, cortex-M33, cortex-M35P och cortex-M55.</span><span class="sxs-lookup"><span data-stu-id="2f159-108">This document describes these ThreadX services that are specific to the ARMv8-M architecture, including the Cortex-M23, Cortex-M33, Cortex-M35P, and Cortex-M55.</span></span>
