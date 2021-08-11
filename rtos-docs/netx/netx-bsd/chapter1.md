---
title: Kapitel 1 – Introduktion till Azure RTOS NetX BSD
description: Den Azure RTOS NetX BSD Sockets API Compliancy Wrapper stöder några av de grundläggande BSD Sockets API-anropen med vissa begränsningar och använder NetX-primitiver under.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b58283a38a25ffdd438d7853999f3b6e390f280a947aa45101d8df86447bf3dd
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796729"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a>Kapitel 1 – Introduktion till Azure RTOS NetX BSD

NetX BSD Sockets API Compliancy Wrapper stöder några av de grundläggande BSD Sockets API-anropen med vissa begränsningar och använder NetX-primitiver under. Det här BSD Sockets API-kompatibilitetslagret bör fungera lika snabbt eller något snabbare än typiska BSD-implementeringar, eftersom den här omslutningen använder interna NetX-primitiver och kringgår grundläggande NetX-felkontroll.

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a>BSD Sockets API-kompatibel wrapper-källa

Källkoden för BSD Wrapper är utformad för enkelhetens skull och består av endast två filer, *nx_bsd.h* *och nx_bsd.c*. Filen *nx_bsd.h* definierar alla nödvändiga BSD Sockets API Wrapper-konstanter och subrutinprototyper, medan *nx_bsd.c* innehåller den faktiska källkoden för BSD Sockets API-kompatibilitet. Dessa BSD Wrapper-källfiler är gemensamma för alla NetX-supportpaket.

Paketet består av:

- **nx_bsd.c:** Källkod för wrapper
- **nx_bsd.h:** Huvudhuvudfil

Exempel på demoprogram:

- **bsd_demo_tcp.c:** Demo *med en enda TCP-server och klient*
- **bsd_demo_udp.c:** Demo *med två UDP-klienter och en UDP-server*
