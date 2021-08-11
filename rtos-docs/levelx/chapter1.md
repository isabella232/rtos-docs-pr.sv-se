---
title: Kapitel 1 – Översikt över Azure RTOS LevelX
description: Azure RTOS LevelX tillhandahåller FÖRSämnings- och FLASH-förslitning för inbäddade program.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73c06d48b98081291d83635e049e6cf8641714c87efe815f9399f3fbab3a6211
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790606"
---
# <a name="chapter-1---overview-of-azure-rtos-levelx"></a>Kapitel 1 – Översikt över Azure RTOS LevelX

Azure RTOS LevelX tillhandahåller FÖRSämnings- och FLASH-förslitning för inbäddade program. Eftersom både GRAFD- och NOR-flashminnet bara kan raderas ett begränsat antal gånger är det viktigt att distribuera flashminnet jämnt. Detta kallas vanligtvis för "utslitning" och är syftet bakom LevelX.

Algoritmen som väljer vilket flash-block som ska återanvändas baseras främst på raderingsantalet, men inte helt. Blocket med det lägsta antalet radering kanske inte väljs om det finns ett annat block som har ett raderingsantal inom ett acceptabelt delta från det minsta antalet radering och som har ett större antal föråldrade mappningar. I sådana fall kommer blocket med det största antalet föråldrade mappningar att raderas och återanvändas, vilket sparar kostnader vid flytt av giltiga mappningsposter.

LevelX har stöd för flera instanser avPLAD- och/eller NOR-delar, det vill säga att programmet kan använda separata instanser av LevelX i samma program. Varje instans kräver ett eget kontrollblock som tillhandahålls av programmet samt en egen flash-drivrutin.

LevelX visar för användaren en matris med logiska sektorer som mappas till fysiskt flashminne i LevelX. För att förbättra prestandan tillhandahåller LevelX även en cache med de senaste mappningarna för logiska sektorer. Storleken på cacheminnet definieras av programmeraren. Program kan använda LevelX tillsammans med FileX eller läsa/skriva logiska sektorer direkt. LevelX är inte beroende av FileX och är mycket litet beroende av ThreadX (endast primitiva ThreadX-datatyper används).

LevelX är utformat för feltolerans. Flash-uppdateringar utförs i en process med flera steg som kan avbrytas i varje steg. LevelX återställs automatiskt till det optimala tillståndet under nästa åtgärd.

LevelX kräver en flash-drivrutin för fysisk åtkomst till det underliggande flashminnet. Exempel PÅ SIMULERAD och NOR-simulerade drivrutiner tillhandahålls och kan användas som en bra utgångspunkt för implementering av faktiska LevelX-drivrutiner. Dessutom beskrivs drivrutinskraven senare i den här dokumentationen.

I följande kapitel beskrivs funktionsåtgärden för STÖD FÖR MAND och NOR LevelX.
