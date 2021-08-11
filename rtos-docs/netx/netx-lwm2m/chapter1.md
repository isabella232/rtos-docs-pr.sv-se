---
title: Kapitel 1 – Introduktion till Azure RTOS NetX LWM2M
description: Den Azure RTOS NetX LWM2M Protocol implementerar klientdelen av protokollstandarden Lightweight Machine to Machine.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fe9c90ec10b241c72c71882b28b5fe0e3e60e3913435ec27f797eade4ca4eca5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784928"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a>Kapitel 1 – Introduktion till Azure RTOS NetX LWM2M

Den Azure RTOS NetX LWM2M Protocol implementerar klientdelen av protokollstandarden Lightweight Machine to Machine.

## <a name="netx-lwm2m-requirements"></a>Krav för NetX LWM2M

För att netX LWM2M-körningsbiblioteket ska fungera korrekt måste en NetX IP-instans redan ha skapats. NetX LWM2M-paketet har inga ytterligare krav.

## <a name="netx-lwm2m-rfcs"></a>NetX LWM2M RFC

NetX LWM2M är kompatibel med OMA-TS-LightweightM2M-V1_0-20170208-A och följande RFC:er relaterade till CoAP (Constrained Application Protocol):

- **RFC 7252:** Det begränsade programprotokollet (CoAP)

- **RFC 7641:** Observera resurser i det begränsade programprotokollet (CoAP)

- **RFC 6690:** Begränsad RESTful-miljölänkformat (CoRE)