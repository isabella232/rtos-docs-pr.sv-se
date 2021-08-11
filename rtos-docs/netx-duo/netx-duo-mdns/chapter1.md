---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo mDNS/DNS-SD
description: Azure RTOS NetX Duo mDNS/DNS-SD utökar den traditionella DNS-tjänsten.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7cde8e81809dcc74ee5d0b09d8e7a8d2ae96850cd84250a5bf003fdd5763925a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796454"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo mDNS/DNS-SD

mDNS och DNS-SD är protokoll som utformats för att utöka den traditionella DNS-tjänsten. mDNS tillhandahåller värdnamn och tjänstuppslag till noderna i det lokala nätverket. Varje nod använder multicast-kanalen IPv4 eller IPv6 för att meddela tjänster som den erbjuder sina grannar, svarar på frågor från grannarna och skickar frågor om fungerar för sina program. MDNS fungerar i en distribuerad miljö, vilket eliminerar en centraliserad tjänst.

DNS-SD bygger på mDNS. DNS-SD gör att noder kan meddela tjänster som de tillhandahåller till det lokala nätverket eller identifiera tjänster som erbjuds av andra noder i det lokala nätverket. I hela dokumentet refererar *termen mDNS* till de tjänster som omfattar både mDNS-specifikationen och DNS-SD-specifikationen.

## <a name="mdns-standard"></a>mDNS Standard

NetX Duo mDNS/DNS-SD-implementeringen följer följande RFC:er:

- RFC 6762: mDNS-specifikation
- RFC 6763: DNS-SD-specifikation