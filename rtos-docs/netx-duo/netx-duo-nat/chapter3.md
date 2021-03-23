---
title: Kapitel 3 – konfigurations alternativ för NAT
description: I följande lista finns alla alternativ och deras funktion beskrivs i detalj
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9c10d6f0d2f36d2794ab1229081799f0032cada8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825860"
---
# <a name="chapter-3---nat-configuration-options"></a>Kapitel 3 – konfigurations alternativ för NAT

Konfigurerbara alternativ för NetX Duo NAT API finns i *nx_nat. h* med undantag för det första, **NX_DISABLE_ERROR_CHECKING** som finns i *nx_nat. c*. I följande lista finns alla alternativ och deras funktion beskrivs i detalj:

- **NX_NAT_DISABLE_ERROR_CHECKING** Om det här alternativet är definierat tas grundläggande fel sökning i NAT bort. Den används vanligt vis när programmet har felsökts. Standard status för NetX Duo NAT är definierad (aktive rad).
- **NX_NAT_ENABLE_REPLACEMENT** Det här alternativet om definierad aktiverar automatisk ersättning när NAT-cachen är full.
  > [!NOTE]
  > Ersätt endast den äldsta icke-TCP-sessionen.
- **NX_NAT_MIN_ENTRY_COUNT** Med det här alternativet anges det minsta antalet för översättnings post. Standardvärdet är 3.
- **NX_NAT_TCP_SESSION_TIMEOUT** Med det här alternativet anges tids gränsen för översättnings posten för TCP-sessioner. Standardvärdet för timeout är 24 timmar.
- **NX_NAT_NON_TCP_SESSION_TIMEOUT** Det här alternativet anger tids gränsen för översättnings poster för icke-TCP-sessioner. Standardvärdet för timeout är 240 sekunder.
- **NX_NAT_START_TCP_PORT** Med det här alternativet anges startvärdet för att hitta en oanvänd TCP-port för att tilldela ett utgående TCP-paket. Standardvärdet är 20000.
- **NX_NAT_END_TCP_PORT** Det här alternativet anger UpperLimit för TCP-port för att tilldela ett utgående TCP-paket. Standardvärdet är 30000.
- **NX_NAT_START_UDP_PORT** Med det här alternativet anges startvärdet för att hitta en oanvänd UDP-port för att tilldela ett utgående UDP-paket. Standardvärdet är 20000.
- **NX_NAT_END_UDP_PORT** Det här alternativet anger UpperLimit för UDP-porten för att tilldela ett utgående UDP-paket. Standardvärdet är 30000.
- **NX_NAT_START_ICMP_QUERY_ID** Med det här alternativet anges startvärdet för att hitta ett oanvänt fråge-ID för att tilldela ett utgående ICMP-frågeuttryck. Standardvärdet är 20000.
- **NX_NAT_END_ICMP_QUERY_ID** Det här alternativet anger UpperLimit för fråge-ID: n för att tilldela ett utgående ICMP-frågeuttryck. Standardvärdet är 30000.
