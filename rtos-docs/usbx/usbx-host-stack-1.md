---
title: Kapitel 1 – Introduktion till att Azure RTOS USBX-värdstack
description: I det här kapitlet introduceras USBX-värdstacken som beskriver dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: abe9b3e4f36a50af9c1267b2e6285b77feecd946660bf23691e70cb66f8bc042
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791008"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a>Kapitel 1 – Introduktion till att Azure RTOS USBX-värdstack

USBX är en fullständig USB-stack för djupt inbäddade program. Det här kapitlet introducerar USBX, som beskriver dess program och fördelar.

## <a name="usbx-features"></a>USBX-funktioner

USBX stöder de tre befintliga USB-specifikationerna: 1.1, 2.0 och OTG. Den är utformad för att vara skalbar och kommer att hantera enkla USB-topologier med endast en ansluten enhet samt komplexa topologier med flera enheter och sammanhängande hubbar. USBX stöder alla dataöverföringstyper för USB-protokoll: kontroll, bulk, avbrott och isokron.

USBX stöder både värdsidan och enhetssidan. Varje sida består av tre lager.

- Kontrollantskikt
- Stackskikt
- Klassskikt

Relationen mellan USB-lagren är följande.

![USB-lager](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>Produkthöjdpunkter

- Fullständigt stöd för ThreadX-processor
- Inga problem
- Slutför ANSI C-källkoden
- Prestanda i realtid
- Dynamisk teknisk support
- Stöd för flera värdstyrenheter
- Stöd för flera klasser
- Flera klassinstanser
- Integrering av klasser med ThreadX, FileX och NetX
- Stöd för USB-enheter med flera konfigurationer
- Stöd för USB-sammansatta enheter
- Stöd för sammanhängande hubbar
- Stöd för USB-energisparhantering
- Stöd för USB OTG
- Exportera spårningshändelser för TraceX

## <a name="powerful-services-of-usbx"></a>Kraftfulla USBX-tjänster

### <a name="multiple-host-controller-support"></a>Stöd för flera värdstyrenheter

USBX har stöd för flera USB-värdstyrenheter som körs samtidigt. Med den här funktionen kan USBX stödja USB 2.0-standarden med hjälp av det bakåtkompatibilitetsschema som är associerat med de flesta USB 2.0-värdkontroller på marknaden idag.

### <a name="usb-software-scheduler"></a>USB-programvaruschema

USBX innehåller en USB-programvaruschema som behövs för att stödja USB-styrenheter som inte har någon bearbetning av maskinvarulistan. USBX-programvaruschemat ordnar USB-överföringar med rätt frekvens och prioritet och instruerar USB-styrenheten att köra varje överföring.

### <a name="complete-usb-device-framework-support"></a>Slutför stöd för RAMVERK FÖR USB-enheter

USBX har stöd för de mest krävande USB-enheterna, inklusive flera konfigurationer, flera gränssnitt och flera alternativa inställningar.

### <a name="easy-to-use-apis"></a>Lättanvända API:er

USBX ger den allra bästa djupt inbäddade USB-stacken på ett sätt som är lätt att förstå och använda. USBX-API:et gör tjänsterna intuitiva och konsekventa. Genom att använda de tillhandahållna USBX-klass-API:erna behöver inte användarprogrammet förstå komplexiteten i USB-protokollen.
