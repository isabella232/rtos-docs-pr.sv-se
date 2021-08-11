---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo BSD
description: BSD Socket API Compliancy Wrapper stöder några av de grundläggande BSD Socket API-anropen, med vissa begränsningar och använder Azure RTOS NetX Duo-primitiver under.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: caf8d5374204bc553ac903f4720d3db402d9a10da5c26caa0fa67c4b5d340049
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790504"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo BSD

BSD Socket API Compliancy Wrapper stöder några av de grundläggande BSD Socket API-anropen, med vissa begränsningar och använder Azure RTOS NetX Duo-primitiver under.

## <a name="bsd-socket-api-compliancy-wrapper-source"></a>BSD Socket API-kompatibel wrapper-källa

Källkoden för wrapper är utformad för enkelhetens skull och består av två filer, *nämligen nxd_bsd.h* *och nxd_bsd.c*. Filen *nxd_bsd.h* definierar alla nödvändiga BSD Socket API-omslutningskonstanter och subrutinprototyper, medan *nxd_bsd.c* innehåller den faktiska källkoden för BSD Socket API-kompatibilitet. Dessa wrapper-källfiler är gemensamma för alla NetX Duo-supportpaket.

Paketet består av:

- **nxd_bsd.c**: Källkod för omslutningskod
- **nxd_bsd.h:** Huvudhuvudfil

Exempel på demoprogram:

- **bsd_demo_udp.c:** Demo *med två UDP-peers (endast IPv4)*
- **bsd_demo_tcp.c:** Demo *med en enda TCP-server och klient*
- **bsd_demo_raw.c:** Demo *med två RAW-peers*