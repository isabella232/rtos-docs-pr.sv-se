---
title: Kapitel 1 – Översikt
author: philmea
description: Den här artikeln är en översikt över Azure återställnings tider ThreadX-moduler
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0c9698086468d7bb41c33ebe9fa9d1ebb61b5f1f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825497"
---
# <a name="chapter-1-overview"></a>Kapitel 1: översikt

ThreadX module-komponenten innehåller en infrastruktur för program för att dynamiskt läsa in moduler som skapats separat från den inhemska delen av programmet. Detta är särskilt användbart i situationer där program kod storleken överskrider tillgängligt minne. Det kan också hjälpa när nya funktioner måste läggas till när kärn avbildningen har distribuerats. Dessutom kan modulerna för dynamisk inläsning användas när en partiell uppdatering av den inbyggda program varan krävs.

Minnes skydd för den inlästa modulen är valfritt, baserat på de egenskaper som anges i modulen inledning. När du har angett minnes skydd är processorns minnes hanterings maskin vara konfigurerad så att alla trådar i modulen endast beviljas åtkomst till modulens kod och data minne. Eventuell ovidkommande minnes åtkomst eller körning resulterar i ett minnes fel och den felaktiga modulens tråd avbryts. Om programmet registrerar ett återanrop för minnes Fels meddelanden kallas detta även för att varna programmet för minnes felet.

ThreadX module-komponenten använder programmet för att tillhandahålla ett minnes utrymme där moduler kan läsas in. Instruktions området i varje modul kan köras på plats eller kopieras till minnes området RAM-modul för körning. I samtliga fall allokeras data minnets krav från modulens minnes yta.

Det finns ingen gräns för hur många moduler som kan läsas in samtidigt (utöver mängden tillgängligt minne), medan det bara finns en kopia av den inhemska modul Manager-koden. Bild 1 illustrerar förhållandet mellan modul hanteraren och själva moduler.

![Moduler och modul Manager-relation](media/image2.png)

**Bild 1** Moduler och modul Manager

Varje modul måste ha ett eget minnes område, vilket är programmets ansvar att definiera. Modulen och modul hanteraren interagerar med en program varu sändnings funktion via fördefinierade fråge-ID: n som motsvarar ThreadX-tjänster som begärts av modulen. Dessutom krävs modulen för att tillhandahålla en enda tråd start punkt samt den nödvändiga stack storleken, prioritet, modul-ID, återanrops stackens storlek/prioritet osv. Den här informationen definieras i varje moduls inledning.

Module manager ansvarar för att skapa den första modulens tråd och initiera körningen. När modulens första tråd körs ansvarar module Manager för att ange alla ThreadX API-begäranden som gjorts av modulen. En modul har fullständig åtkomst till ThreadX-API: et, inklusive möjligheten att skapa ytterligare trådar i modulen.  
  
Namngivnings konventionerna för modulens käll kod är enkla: alla källfiler för module-hanteraren heter ***txm_module_manager_ \**** och alla filer som associeras exklusivt med modulen utelämnar delen "**_chef_*_" i namnet. Huvud include-filen _*_txm_module. h_** delas av käll koden Manager och module.
