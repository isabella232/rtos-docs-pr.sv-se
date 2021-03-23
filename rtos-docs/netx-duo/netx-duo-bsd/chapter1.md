---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo BSD
description: BSD socket API kompatibilitet-omslutningen har stöd för några av de grundläggande BSD-API-anropen, med vissa begränsningar och använder Azure återställnings tider NetX Duo-primitiver under.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e89018dffd2f9f9065efab2ecabdf4364c4f89a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826160"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo BSD

BSD socket API kompatibilitet-omslutningen har stöd för några av de grundläggande BSD-API-anropen, med vissa begränsningar och använder Azure återställnings tider NetX Duo-primitiver under.

## <a name="bsd-socket-api-compliancy-wrapper-source"></a>BSD socket API kompatibilitet omslutnings källa

Omslutnings käll koden är utformad för enkelhet och består av två filer, nämligen *nxd_bsd. h* och *nxd_bsd. c*. Filen *nxd_bsd. h* definierar alla nödvändiga gränssnitts konstanter och underrutins prototyper för BSD-socket-API, medan *nxd_bsd. c* innehåller den faktiska BSD-källans källkod för BSD socket API. Dessa omslutnings-källfiler är gemensamma för alla NetX Duo-support paket.

Paketet består av:

- **nxd_bsd. c**: gränssnitts käll kod
- **nxd_bsd. h**: huvud rubrik fil

Exempel på demo program:

- **bsd_demo_udp. c**: *demo med två UDP-peer-datorer (endast IPv4)*
- **bsd_demo_tcp. c**: *demo med en enda TCP-server och-klient*
- **bsd_demo_raw. c**: *demo med två obearbetade peer-datorer*