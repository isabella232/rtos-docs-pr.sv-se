---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX-LWM2M
description: Azure återställnings tider NetX LWM2M-protokollet implementerar klient delen av den lätta datorn till Machine Protocol standard.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c29af430975266eed684bd1de38d9e5d7e2586a6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826709"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX-LWM2M

Azure återställnings tider NetX LWM2M-protokollet implementerar klient delen av den lätta datorn till Machine Protocol standard.

## <a name="netx-lwm2m-requirements"></a>NetX LWM2M-krav

För att fungera korrekt, kräver NetX-LWM2M kör tids bibliotek att en NetX-IP-instans redan har skapats. NetX LWM2M-paketet har inga ytterligare krav.

## <a name="netx-lwm2m-rfcs"></a>NetX LWM2M-rapporter

NetX LWM2M är kompatibel med OMA-TS-LightweightM2M-V1_0 -20170208-A och följande RFC: er relaterade till det begränsade applikations protokollet (CoAP):

- **RFC 7252**: det begränsade applikations protokollet (CoAP)

- **RFC 7641**: att observera resurser i det begränsade program protokollet (CoAP)

- **RFC 6690**: begränsat RESTful miljöer (Core) länk format