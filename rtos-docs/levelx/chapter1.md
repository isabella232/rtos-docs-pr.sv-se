---
title: Kapitel 1 – Översikt över Azure återställnings tider-LevelX
description: Azure återställnings tider-LevelX innehåller NAND och eller Flash slitage-funktioner till inbäddade program.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 045446fec74164f125bc0ad27e8b7a904be14ab2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826274"
---
# <a name="chapter-1---overview-of-azure-rtos-levelx"></a>Kapitel 1 – Översikt över Azure återställnings tider-LevelX

Azure återställnings tider-LevelX innehåller NAND och eller Flash slitage-funktioner till inbäddade program. Eftersom både NAND och eller Flash-minne bara kan raderas ett visst antal gånger är det viktigt att distribuera Flash-minnet jämnt. Detta kallas vanligt vis "slitages utjämning" och är syftet bakom LevelX.

Algoritmen som väljer vilket Flash-block som ska återanvändas huvudsakligen baseras på antalet rader, men inte helt. Det går inte att välja blocket med det lägsta antalet raderingar om det finns ett annat block som har ett antal rader i en acceptabel delta från det minsta antalet raderingar och som har ett större antal föråldrade mappningar. I sådana fall raderas blocket med det högsta antalet föråldrade mappningar och återanvänds, vilket innebär att det går att flytta giltiga mappnings poster.

LevelX stöder flera instanser av NAND och/eller delar, d.v.s. programmet kan använda separata instanser av LevelX i samma program. Varje instans kräver ett eget kontroll block som tillhandahålls av programmet samt dess egna Flash-drivrutin.

LevelX presenterar användaren en matris med logiska sektorer som är mappade till det fysiska Flash-minnet inuti LevelX. För att förbättra prestanda tillhandahåller LevelX också en cache med de senaste logiska sektor mappningarna. Storleken på den här cachen definieras av programmeraren. Program kan använda LevelX tillsammans med FileX eller kan läsa/skriva logiska sektorer direkt. LevelX har inget beroende av FileX och mycket litet beroende av ThreadX (endast primitiva ThreadX-datatyper används).

LevelX är utformad för fel tolerans. Flash-uppdateringar utförs i en process med flera steg som kan avbrytas i varje steg. LevelX återställs automatiskt till det optimala läget under nästa åtgärd.

LevelX kräver en Flash-drivrutin för fysisk åtkomst till det underliggande Flash-minnet. Exempel på NAND och eller simulerade driv rutiner tillhandahålls och kan användas som en lämplig start punkt för att implementera faktiska LevelX-drivrutiner. Dessutom beskrivs driv rutins kraven längre fram i den här dokumentationen.

I följande kapitel beskrivs funktions åtgärden för NAND-och-och-LevelX-stöd.
