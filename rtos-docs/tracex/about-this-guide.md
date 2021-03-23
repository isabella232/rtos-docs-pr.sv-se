---
title: Användar handbok för Azure återställnings tider TraceX
description: Den här guiden innehåller omfattande information om Azure återställnings tider TraceX, Microsoft Windows-baserade system analys verktyg från Microsoft.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 92d886b19a0c67292cd4f6a5f8bd7f9d3106374b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827870"
---
# <a name="about-this-guide"></a>Om den här guiden

Den här guiden innehåller omfattande information om Azure återställnings tider TraceX, Microsoft Windows-baserade system analys verktyg för Microsoft Azure återställnings tider.

Den är avsedd för den inbäddade programutvecklaren i real tid med Azure återställnings tider ThreadX Real-Time Opera ting system (återställnings tider) och tilläggs komponenter. Utvecklaren bör vara bekant med Azure återställnings tider-ThreadX Azure återställnings tider-FileX och Azure återställnings tider NetX-koncept.

## <a name="organization"></a>Organisation

- [Kapitel 1](chapter1.md) – innehåller en grundläggande översikt över Azure återställnings tider-TraceX och beskriver relationen till utveckling i real tid.
- [Kapitel 2](chapter2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider-TraceX för att analysera ditt program direkt från lådan.
- [Kapitel 3](chapter3.md) – beskriver huvud funktionerna i Azure återställnings tider TraceX.
- [Kapitel 4](chapter4.md) – detaljerade prestanda analys funktioner i Azure återställnings tider TraceX.
- [Kapitel 5](chapter5.md) – beskriver hur du konfigurerar Azure återställnings tider ThreadX, Azure återställnings tider FileX och Azure återställnings tider netx för att generera en spårningssession som kan visas av Azure återställnings tider TraceX.
- [Kapitel 6](chapter6.md) – beskriver Azure återställnings tider TraceX-händelser i detalj.
- [Kapitel 7](chapter7.md) – beskriver Azure återställnings tider FileX-händelser i detalj.
- [Kapitel 8](chapter8.md) – beskriver Azure återställnings tider netx-händelser i detalj.
- [Kapitel 9](chapter9.md) – beskriver Azure återställnings tider USBX-händelser i detalj.
- [Kapitel 10](chapter10.md) – beskriver hur du skapar anpassade användar händelser i detalj.
- [Kapitel 11](chapter11.md) – beskriver den interna spårningssessionen i detalj.
- [Bilaga A](appendix-a.md) – Azure återställnings tider ThreadX-portbaserad fil med en tidsstämpel-källa för att samla in spårnings händelser.
- [Bilaga B](appendix-b.md) – Azure återställnings tider ThreadX *tx_trace. h* -filen som visar implementerings information om bufferten för händelse spårning.
- [Bilaga C](appendix-c.md) – sammanfattar kommando rads verktyg för att konvertera olika fil format till rätt TraceX-binärfiler i Azure återställnings tider.
- [Bilaga D](appendix-d.md) – exempel på dumpnings spårning av filer från olika utvecklingsverktyg.

## <a name="guide-conventions"></a>Guide konventioner

*Kursiv stil* – teckensnittet noterar bok titlar, betonar viktiga ord och indikerar variabler.

**Fetstil** – typsnitt anger fil namn, viktiga ord och betonar viktiga ord och variabler.

> [!NOTE]
> Anger information om anmärkning.

## <a name="customer-support-center"></a>Kund Support Center

Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här. Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:

1. En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider-ThreadX som föregåde problemet.
3. Innehållet i den *_tx_version_id* strängen som finns i filen *tx_port. h* i distributionen. Den här strängen ger oss värdefull information om din kör tids miljö.
4. Innehållet i RAM-minnet för *_tx_build_options* ulong-variabeln. Den här variabeln ger oss information om hur ditt Azure återställnings tider ThreadX-bibliotek har skapats.
