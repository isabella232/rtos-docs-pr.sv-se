---
title: Kapitel 3 – NAT-konfigurationsalternativ
description: Följande lista innehåller alla alternativ och deras funktion beskrivs i detalj
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c7f2de88b5d70646284d946fdb6fbc743f08b3486430befb4fcda1d7e23e9b9
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797291"
---
# <a name="chapter-3---nat-configuration-options"></a>Kapitel 3 – NAT-konfigurationsalternativ

Konfigurerbara alternativ för NETX Duo NAT API finns i *nx_nat.h* med undantag för den första, **NX_DISABLE_ERROR_CHECKING** som finns *i nx_nat.c*. Följande lista innehåller alla alternativ och deras funktion beskrivs i detalj:

- **NX_NAT_DISABLE_ERROR_CHECKING** Det här alternativet tar bort den grundläggande NAT-felkontrollen om det definieras. Det används vanligtvis när programmet har felsökts. Standardinställningen för NETX Duo NAT-status är definierad (aktiverad).
- **NX_NAT_ENABLE_REPLACEMENT** Det här alternativet om det definieras aktiverar automatisk ersättning när NAT-cachen är full.
  > [!NOTE]
  > Ersätt endast den äldsta icke-TCP-sessionen.
- **NX_NAT_MIN_ENTRY_COUNT** Det här alternativet anger det minsta antalet för översättningsposten. Standardantalet är 3.
- **NX_NAT_TCP_SESSION_TIMEOUT** Det här alternativet anger tidsgränsen för översättningsposten för TCP-sessioner. Standardtidsinställningen är 24 timmar.
- **NX_NAT_NON_TCP_SESSION_TIMEOUT** Det här alternativet anger tidsgränsen för översättningsposten för icke-TCP-sessioner. Standardvärdet för timeout är 240 sekunder.
- **NX_NAT_START_TCP_PORT** Det här alternativet anger startvärdet för att hitta en oanvänd TCP-port för att tilldela ett utgående TCP-paket. Standardvärdet är 20000.
- **NX_NAT_END_TCP_PORT** Det här alternativet anger den övre gränsen för TCP-porten för att tilldela ett utgående TCP-paket. Standardvärdet är 30000.
- **NX_NAT_START_UDP_PORT** Det här alternativet anger startvärdet för att hitta en oanvänd UDP-port för att tilldela ett utgående UDP-paket. Standardvärdet är 20000.
- **NX_NAT_END_UDP_PORT** Det här alternativet anger den övre gränsen för UDP-porten för att tilldela ett utgående UDP-paket. Standardvärdet är 30000.
- **NX_NAT_START_ICMP_QUERY_ID** Det här alternativet anger startvärdet för att hitta ett oanvänt fråge-ID för att tilldela ett utgående ICMP-frågepaket. Standardvärdet är 20000.
- **NX_NAT_END_ICMP_QUERY_ID** Det här alternativet anger den övre gränsen för fråge-ID:er för att tilldela ett utgående ICMP-frågepaket. Standardvärdet är 30000.
