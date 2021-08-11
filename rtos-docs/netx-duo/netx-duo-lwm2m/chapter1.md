---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo LWM2M Client
description: Det här kapitlet innehåller en introduktion till Azure RTOS NetX Duo Lightweight Machine to Machine-protokollklienten.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a2722daac76632e492d0f9345103c45da9ba1b321e91c9c04e04c76463984c3a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783483"
---
# <a name="chapter-1--introduction-to-lwm2m-client"></a>Kapitel 1 Introduktion till LWM2M-klient

Den Azure RTOS NetX Duo LWM2M-klientprotokollet implementerar klientdelen av lightweight machine to Machine-protokollstandarden. (LWM2M 1.0-20170208A)

## <a name="netx-lwm2m-client-requirements"></a>NetX LWM2M-klientkrav

För att fungera korrekt kräver LWM2M-klientens körningsbibliotek att en NetX IP-instans redan har skapats. NetX LWM2M-klientpaketet har inga ytterligare krav.

## <a name="netx-lwm2m-client-rfcs"></a>NetX LWM2M-klient-RFC:er

LWM2M-klienten är kompatibel med OMA-TS-LightweightM2M-V1 \_ 0-20170208-A och följande RFC:er relaterade till det begränsade programprotokollet (CoAP).

* RFC 7252 Det begränsade programprotokollet (CoAP)

* RFC 7641 observationsresurser i det begränsade programprotokollet (CoAP)

* RFC 6690-begränsat RESTful-miljölänkformat (CoRE)

Mer information finns i [OMA-TS-LightweightM2M-V1 \_ 0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).