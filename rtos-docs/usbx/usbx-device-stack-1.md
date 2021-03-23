---
title: Kapitel 1 – Introduktion till Azure återställnings tider USBX Device stack
description: USBX är en USB-stack med full funktionalitet för djupt inbäddade program. I det här kapitlet introduceras USBX som beskriver dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6965303f1fbf19212b9f7ff20f811a71fb207f54
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828623"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a>Kapitel 1 – Introduktion till Azure återställnings tider USBX Device stack

USBX är en USB-stack med full funktionalitet för djupt inbäddade program. I det här kapitlet introduceras USBX, som beskriver program och förmåner 

## <a name="usbx-features"></a>USBX-funktioner

USBX stöder de tre befintliga USB-specifikationerna: 1,1, 2,0 och OTG. Den är utformad för att vara skalbar och kommer att kunna hantera enkla USB-topologier med bara en ansluten enhet samt komplexa topologier med flera enheter och sammanhängande nav. USBX stöder alla data överförings typer för USB-protokollen: kontroll, Mass, avbrott och isokrona.

USBX stöder både värd sidan och enhets sidan. Varje sida består av tre lager.

- Styrenhets skikt
- Stack skikt
- Klass skikt

Relationen mellan USB-skikten är följande:

![USB-skikt](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>Produkt höjd punkter

- Slutför support för ThreadX-processor
- Ingen royalties
- Fullständig ANSI C-källkod
- Real tids prestanda
- Teknisk support som svarar
- Stöd för flera klasser
- Flera klass instanser
- Integrering av klasser med ThreadX, FileX och NetX
- Stöd för USB-enheter med flera konfigurationer
- Stöd för USB-sammansatta enheter
- Stöd för USB-energihantering
- Stöd för USB-OTG
- Exportera spårnings händelser för TraceX

## <a name="powerful-services-of-usbx"></a>Kraftfulla tjänster av USBX

### <a name="complete-usb-device-framework-support"></a>Fullständigt stöd för USB-enhets ramverk

USBX kan stödja de mest krävande USB-enheterna, inklusive flera konfigurationer, flera gränssnitt och flera alternativa inställningar.

### <a name="easy-to-use-apis"></a>Lättanvända API: er

USBX tillhandahåller den bästa inbäddade USB-stacken på ett sätt som är lätt att förstå och använda. USBX-API: n gör tjänsterna intuitiva och konsekventa. Genom att använda de tillhandahållna USBX klass-API: erna behöver inte användar programmet förstå USB-protokollens komplexitet.
