---
title: Bilaga C – DOS-kommandoradsverktyg
description: Det finns tre DOS-kommandoradsverktyg i Azure RTOS TraceX-installationen under underkatalogen Verktyg.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 1a89f8be7e21e416659b904f0ec5b2a3a8f666cdb9a861786e652a38564db48f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791558"
---
# <a name="appendix-c---dos-command-line-utilities"></a>Bilaga C – DOS-kommandoradsverktyg

Det finns tre DOS-kommandoradsverktyg i TraceX-installationen under ***underkatalogen*** Utilities (Verktyg).

De verktyg som anges visas nedan:

| **Verktyg**                              | **Syfte**                               | **Kommandoradsdefinitioner** |
| -------------------------------- | ----------------------------------------- | ---------------------------- |
| **ea2tracex.exe**                | Konverterar spårningsfilen ea2tracex som genererats av ThreadX i original_file med GHS-verktygen converted_file till TraceX-spårningsfilformatet. ThreadX för GHS-verktygen skapar ett annat spårningsformat än ThreadX för icke-GHS-verktyg, vilket är anledningen till att det här konverteringsverktyget behövs. | ``` > eatracex original_file converted_file <cr> ``` | 
**hex2tracex.exe** | Konverterar en spårningsfil som genererats av ThreadX men som avförts från utvecklingsverktyget i Intel HEX-format till det binära TraceX-spårningsfilformatet. TraceX V5 och högre kan öppna HEX-filer utan att konvertera dem. | ``` hex2tracex hex_file converted_file <cr> ``` | 
**mot2tracex.exe** | Konverterar en spårningsfil som genererats av ThreadX men som har avbildts från utvecklingsverktyget i Format för Samsung S-Record till det binära TraceX-spårningsfilformatet. TraceX V5 och högre kan öppna S-Record-filer utan att konvertera dem. | ``` > mot2tracex mot_file converted_file <cr> ```|