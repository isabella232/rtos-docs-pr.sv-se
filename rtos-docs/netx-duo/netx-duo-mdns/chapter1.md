---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo mDNS/DNS-SD
description: Azure återställnings tider NetX Duo mDNS/DNS-SD ökar den traditionella DNS-tjänsten.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b46539ee4d502fa4c90fb3392e25cd3bee40dc5b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825926"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo mDNS/DNS-SD

MDNS och DNS-SD är protokoll som har utformats för att utöka den traditionella DNS-tjänsten. mDNS tillhandahåller värd namn och tjänsts ökning till noderna i det lokala nätverket. Varje nod använder IPv4-eller IPv6-multicast-kanal för att meddela tjänster som den erbjuder för sina grannar, svarar på frågor från sina grannar och skickar frågor om sina program. MDNS körs i en distribuerad miljö, vilket eliminerar en centraliserad funktion.

DNS-SD byggts ovanpå mDNS. DNS-SD tillåter noder att meddela tjänster som de tillhandahåller till det lokala nätverket eller för att identifiera tjänster som erbjuds av andra noder i det lokala nätverket. I hela dokumentet refererar termen *mdns* till tjänsterna som omfattar både mdns-specifikationen och DNS-SD-specifikationen.

## <a name="mdns-standard"></a>mDNS standard

NetX Duo-mDNS/DNS-SD-implementering följer följande RFC: er:

- RFC 6762: mDNS-specifikation
- RFC 6763: DNS-SD-specifikation