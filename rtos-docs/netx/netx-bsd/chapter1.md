---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX BSD
description: 'Azure återställnings tider NetX BSD Sockets API kompatibilitet-omslutningen har stöd för några av de grundläggande BSD-API: erna med vissa begränsningar och använder NetX-primitiver under.'
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fce781ac97ae75c4148614453eeb35c3064f8849
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825608"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX BSD

NetX BSD Sockets API kompatibilitet-omslutningen stöder vissa av de grundläggande BSD-API: erna med vissa begränsningar och använder NetX-primitiver under. Detta BSD-skikt i BSD Sockets-API: n ska fungera lika snabb eller något snabbare än vanliga BSD-implementeringar, eftersom den här omslutningen använder interna NetX-primitiver och kringgår grundläggande NetX fel kontroll.

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a>BSD Sockets API kompatibilitet wrapper-källa

Käll koden för BSD-omslutningen är utformad för enkelhet och består bara av två filer, *nx_bsd. h* och *nx_bsd. c*. Filen *nx_bsd. h* definierar alla nödvändiga BSD-konstanter och subrutin-prototyper för BSD-Sockets-API, medan *nx_bsd. c* innehåller den faktiska käll koden för BSD Sockets-API-kompatibilitet. Dessa filer för BSD-omslutningen är gemensamma för alla NetX-support paket.

Paketet består av:

- **nx_bsd. c**: gränssnitts käll kod
- **nx_bsd. h**: huvud rubrik fil

Exempel på demo program:

- **bsd_demo_tcp. c**: *demo med en enda TCP-server och-klient*
- **bsd_demo_udp. c**: *demo med två UDP-klienter och en UDP-Server*
