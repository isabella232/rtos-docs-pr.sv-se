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
# <a name="chapter-1--overview"></a>Översikt över kapitel 1

ARMv8-M-arkitekturen introducerar nya säkerhetsfunktioner, inklusive TrustZone, vilket gör att minnet kan taggas som säkert eller osäkert. Följande ARM-rikt linjer, ThreadX (och användar programmet) har utformats för att köras i icke-säkert läge. ThreadX (och användar programmet) kan också köras i säkert läge. Vissa nya ThreadX-API: er krävs för att gränssnittet ska kunna hanteras med program vara i Secure Mode. Det här dokumentet beskriver de här ThreadX-tjänsterna som är speciella för ARMv8-M-arkitekturen, inklusive cortex-M23, cortex-M33, cortex-M35P och cortex-M55.
