---
title: Kapitel 1 – Introduktion till Azure RTOS TraceX
description: Azure RTOS TraceX är ett Microsoft-verktyg för systemanalys som visar systemhändelseinformation som samlats in av ThreadX och körs på ett inbäddat mål.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 70eb06341e5d57f59c74888046bda3bbf95dc88cac56332be640d9576551796f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785064"
---
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a>Kapitel 1 – Introduktion till Azure RTOS TraceX

Azure RTOS TraceX är ett Microsoft-verktyg för systemanalys som visar systemhändelseinformation som samlats in av ThreadX och körs på ett inbäddat mål. Användaren ansvarar för att överföra spårningsbufferten som lagras i RAM-minnet i det inbäddade målet till en binär fil på värddatorn. Användaren kan sedan öppna den här filen med TraceX och grafiskt analysera målhändelserna, diagnostisera systemproblem och justera ett fungerande program för att förbättra prestanda- och resurshanteringen.

## <a name="tracex-requirements"></a>TraceX-krav

TraceX kräver Windows XP (eller högre). Systemet ska ha minst 192 MB RAM-minne, 2 GB tillgängligt hårddiskutrymme och en minsta skärm på 1 024 x 768 med 256 färger. Dessutom måste programmet köras på ThreadX V5.0 eller senare.

TraceX kräver också Microsoft .NET ramverket installeras, vilket Installationsprogrammet för TraceX gör automatiskt.

## <a name="tracex-constraints"></a>TraceX-begränsningar

TraceX har följande begränsningar:

- TraceX-filer är begränsade till högst 32 768 händelser (cirka 1 MB).
- Tidsstämpelkällan måste ha en rimlig lösning. Om lösningen är för låg överlappar händelserna varandra. Om upplösningen är för hög finns det risk för långa luckor mellan händelser.
- TraceX kan inte korrekt mäta intervall mellan händelser som är större än timerperioden.
