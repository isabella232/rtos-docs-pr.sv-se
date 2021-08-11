---
title: Kapitel 1 – Översikt
author: philmea
description: Den här artikeln är en översikt över Azure RTOS ThreadX-moduler
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9018c10e6fe92b2237ec94b633f2f0030ad1cef4bcbcb7afa5ace20548f012ed
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799444"
---
# <a name="chapter-1-overview"></a>Kapitel 1: Översikt

Komponenten ThreadX-modul tillhandahåller en infrastruktur för program som dynamiskt kan läsa in moduler som är byggda separat från den inbyggda delen av programmet. Detta är särskilt användbart i situationer där programkodstorleken överskrider det tillgängliga minnet. Det kan också vara till hjälp när nya funktioner måste läggas till när kärnavbildningen har distribuerats. Dessutom kan moduler med dynamisk inläsning användas när partiella uppdateringar av inbyggd programvara krävs.

Minnesskydd för den inlästa modulen är valfritt baserat på de egenskaper som anges i modulens ingress. När minnesskydd anges konfigureras processorns maskinvara för minneshantering så att alla trådar i modulen endast tillåts åtkomst till modulens kod och dataminne. Eventuell överflödig minnesåtkomst eller körning resulterar i ett minnesfel och den felaktiga modultråden avslutas. Om programmet registrerar ett återanrop av minnesfelsaviseringar anropas detta också för att varna om minnesfelet.

Komponenten ThreadX-modul förlitar sig på programmet för att tillhandahålla ett minnesområde där moduler kan läsas in. Instruktionsområdet för varje modul kan köras på plats eller kopieras till RAM-modulens minnesområde för körning. I samtliga fall allokeras minneskraven för moduldata från modulens minnesområde.

Det finns inga begränsningar för hur många moduler som kan läsas in samtidigt (förutom mängden tillgängligt minne), medan det bara finns en kopia av den lokala Module Manager-koden. Bild 1 illustrerar modulhanterarens relation och själva modulerna.

![Relationer mellan moduler och modulhanterare](media/image2.png)

**Bild 1** Moduler och modulhanterare

Varje modul måste ha ett eget minnesområde, vilket är programmets ansvar att definiera. Modulen och modulhanteraren interagerar via en funktion för programsändning via fördefinierade begärande-ID:er som motsvarar ThreadX-tjänster som begärs av modulen. Dessutom krävs modulen för att tillhandahålla en enda tråd-startpunkt samt den stackstorlek, prioritet, modul-ID, storlek/prioritet för återanropstrådstacken som krävs. Den här informationen definieras i varje moduls ingress.

Modulhanteraren ansvarar för att skapa den första modultråden och initiera körningen. När modulens inledande tråd körs ansvarar modulhanteraren för att sätta in alla ThreadX API-begäranden som görs av modulen. En modul har fullständig åtkomst till ThreadX-API:et, inklusive möjligheten att skapa ytterligare trådar i modulen.  
  
Namngivningskonventionerna för källkod för modulen är enkla: alla modulhanterarens källfiler heter ***txm_module_manager_ \**** och alla filer som är associerade med modulen utelämnar **_"manager_*_"-delen av namnet. Den huvudsakliga include-filen _*_txm_module.h_** delas av källkoden för ansvarig och modul.
