---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo LWM2M-klienten
description: Det här kapitlet innehåller en introduktion till Machine Protocol-klienten med Azure återställnings tider NetX Duo Lightweight Machine.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 12f13c154668b3cadfae0924e59b55631dc27424
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825956"
---
# <a name="chapter-1--introduction-to-lwm2m-client"></a>Kapitel 1 Introduktion till LWM2M-klienten

Klient protokollet Azure återställnings tider NetX Duo LWM2M implementerar klient delen av den lätta datorn till Machine Protocol standard. (LWM2M 1.0-20170208A)

## <a name="netx-lwm2m-client-requirements"></a>NetX LWM2M-klient krav

För att kunna fungera korrekt kräver LWM2M-klientens kör tids bibliotek att en NetX-IP-instans redan har skapats. NetX LWM2M-klient paketet innehåller inga ytterligare krav.

## <a name="netx-lwm2m-client-rfcs"></a>NetX LWM2M-klientens RFC

LWM2M-klienten är kompatibel med OMA-TS-LightweightM2M-v1 \_ 0-20170208-A och följande RFC: er relaterade till det begränsade applikations protokollet (CoAP).

* RFC 7252-CoAP (begränsat program protokoll)

* RFC 7641 om att observera resurser i det begränsade applikations protokollet (CoAP)

* RFC 6690-länk format för begränsat RESTful-miljöer (CoRE)

Mer information finns i [OMA-TS-LightweightM2M-V1 \_ 0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).