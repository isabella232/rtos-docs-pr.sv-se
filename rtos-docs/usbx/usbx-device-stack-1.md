---
title: Kapitel 1 – Introduktion till Azure RTOS USBX-enhetsstack
description: USBX är en fullständig USB-stack för djupt inbäddade program. Det här kapitlet introducerar USBX, som beskriver dess fördelar och program.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 0ec49e88c8dcb8ca200bc376da2f33eb5ddac340bf3693368dc3508f68220765
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791473"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a>Kapitel 1 – Introduktion till Azure RTOS USBX-enhetsstack

USBX är en fullständig USB-stack för djupt inbäddade program. Det här kapitlet introducerar USBX, som beskriver dess program och fördelar 

## <a name="usbx-features"></a>USBX-funktioner

USBX stöder de tre befintliga USB-specifikationerna: 1.1, 2.0 och OTG. Den är utformad för att vara skalbar och kommer att hantera enkla USB-topologier med endast en ansluten enhet samt komplexa topologier med flera enheter och sammanhängande hubbar. USBX stöder alla dataöverföringstyper för USB-protokoll: kontroll, bulk, avbrott och isokron.

USBX stöder både värdsidan och enhetssidan. Varje sida består av tre lager.

- Kontrollantskikt
- Stackskikt
- Klassskikt

Relationen mellan USB-lagren är följande:

![USB-lager](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>Produkthöjdpunkter

- Fullständigt stöd för ThreadX-processor
- Inga problem
- Slutför ANSI C-källkoden
- Prestanda i realtid
- Dynamisk teknisk support
- Stöd för flera klasser
- Flera klassinstanser
- Integrering av klasser med ThreadX, FileX och NetX
- Stöd för USB-enheter med flera konfigurationer
- Stöd för USB-sammansatta enheter
- Stöd för USB-energisparhantering
- Stöd för USB OTG
- Exportera spårningshändelser för TraceX

## <a name="powerful-services-of-usbx"></a>Kraftfulla USBX-tjänster

### <a name="complete-usb-device-framework-support"></a>Fullständigt stöd för RAMVERK FÖR USB-enheter

USBX har stöd för de mest krävande USB-enheterna, inklusive flera konfigurationer, flera gränssnitt och flera alternativa inställningar.

### <a name="easy-to-use-apis"></a>Lättanvända API:er

USBX ger den bästa djupt inbäddade USB-stacken på ett sätt som är lätt att förstå och använda. USBX-API:et gör tjänsterna intuitiva och konsekventa. Genom att använda de tillhandahållna USBX-klass-API:erna behöver inte användarprogrammet förstå komplexiteten i USB-protokollen.
