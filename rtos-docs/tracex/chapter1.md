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
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a>Kapitel 1 – Introduktion till Azure återställnings tider TraceX

Azure återställnings tider TraceX är ett Microsoft System Analysis-verktyg som visar information om system händelser som samlats in av ThreadX som körs på ett inbäddat mål. Användaren ansvarar för att överföra den sökta kommandobufferten som lagras i RAM-minnet i det inbäddade målet till en binär fil på värddatorn. Användaren kan sedan öppna den här filen med TraceX och analysera mål händelserna grafiskt, diagnostisera system problem och justera ett fungerande program för att förbättra prestanda och resurs hantering.

## <a name="tracex-requirements"></a>Krav för TraceX

TraceX kräver Windows XP (eller senare). Systemet bör ha minst 192 MB RAM-minne, 2 GB ledigt hårddisk utrymme och en minimal visning av 1024x768 med 256-färger. Dessutom måste programmet köras på ThreadX V 5.0 eller senare.

TraceX kräver också att Microsoft .NET Framework installeras, vilket innebär att installations programmet för TraceX sker automatiskt.

## <a name="tracex-constraints"></a>TraceX-begränsningar

TraceX har följande begränsningar:

- TraceX-filer är begränsade till högst 32 768 händelser (ungefär 1 MB).
- Tids stämplings källan måste ha en rimlig lösning. Om lösningen är för låg, överlappas händelserna. Om upplösningen är för hög kan det uppstå långa luckor mellan händelserna.
- TraceX kan inte korrekt mäta intervall mellan händelser som är större än timer-perioden.
