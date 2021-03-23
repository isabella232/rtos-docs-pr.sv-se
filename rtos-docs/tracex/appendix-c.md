---
title: Bilaga C – DOS-kommando rads verktyg
description: Det finns tre DOS kommando rads verktyg som finns i Azure återställnings tider TraceX-installationen under katalogen verktyg.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: e1ec852a97a6735a4a055706f55283950d3f8d6b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827822"
---
# <a name="appendix-c---dos-command-line-utilities"></a>Bilaga C – DOS-kommando rads verktyg

Det finns tre DOS kommando rads verktyg som finns i TraceX-installationen under katalogen ***verktyg*** .

De verktyg som anges visas nedan:

| **Verktyg**                              | **Syfte**                               | **Kommando rads definitioner** |
| -------------------------------- | ----------------------------------------- | ---------------------------- |
| **ea2tracex.exe**                | Konverterar spårnings filen ea2tracex som genereras av ThreadX i original_file-associationen med GHS-verktygen converted_file till det TraceX spårnings fil formatet. ThreadX för GHS-verktyg genererar ett annat spårnings format än ThreadX för icke-GHS-verktyg, vilket är orsaken till att konverterings verktyget behövs. | ``` > eatracex original_file converted_file <cr> ``` | 
**hex2tracex.exe** | Konverterar en spårnings fil som genererats av ThreadX men som dumpas från utvecklingsverktyg i Intel HEX-format till fil formatet för binär TraceX-spårning. TraceX V5 och senare kan öppna HEX-filer utan att konvertera dem. | ``` hex2tracex hex_file converted_file <cr> ``` | 
**mot2tracex.exe** | Konverterar en spårnings fil som genererats av ThreadX, men som dumpas från utvecklingsverktyg i Motorola S-Record-format till fil formatet för binär TraceX-spårning. TraceX V5 och senare kan öppna filer med en post utan att konvertera dem. | ``` > mot2tracex mot_file converted_file <cr> ```|