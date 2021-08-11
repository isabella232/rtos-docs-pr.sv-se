---
title: Kapitel 1 – Introduktion till Azure RTOS ThreadX för ARMv8-M.
description: Det här kapitlet är startpunkten för läsning om Azure RTOS ThreadX-tillägget för ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f0d87ec562c7fcfa6af5d2240655ef526f6e0611d509fe60c745436371413d7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798256"
---
# <a name="chapter-1--overview"></a>Översikt över kapitel 1

ARMv8-M-arkitekturen introducerar nya säkerhetsfunktioner, inklusive TrustZone, som gör att minne kan taggas som säkert eller icke-säkert. Enligt ARM:s riktlinjer är ThreadX (och användarprogrammet) utformat för att köras i icke-säkert läge. ThreadX (och användarprogrammet) kan också köras i säkert läge. För att kunna samverka med programvara i säkert läge krävs vissa nya ThreadX-API:er. Det här dokumentet beskriver dessa ThreadX-tjänster som är specifika för ARMv8-M-arkitekturen, inklusive Cortex-M23, Cortex-M33, Cortex-M35P och Cortex-M55.
