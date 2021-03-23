---
title: Om Azure återställnings tider ThreadX-guiden
description: Den här guiden innehåller omfattande information om Azure återställnings tider ThreadX, Microsoft Real-Performance-kärnan i real tid.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ad9f782942bcdbb2dc49a9c841d865d97bcb1d4e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826592"
---
# <a name="about-the-azure-rtos-threadx-guide"></a>Om Azure återställnings tider ThreadX-guiden

Den här guiden innehåller omfattande information om Azure återställnings tider ThreadX, Microsoft Real-Performance-kärnan i real tid. 

Den är avsedd för den inbäddade programutvecklaren i real tid. Utvecklaren bör vara bekant med vanliga operativ system funktioner i real tid och programmeringsspråket C.

## <a name="organization"></a>Organisation

[Kapitel 1](chapter1.md) – innehåller en grundläggande översikt över Azure återställnings tider-ThreadX och dess relation till inbäddad real tids utveckling

[Kapitel 2](chapter2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider-ThreadX i ditt program direkt från *lådan*

[Kapitel 3](chapter3.md) – beskrivs i detalj den funktionella driften av Azure återställnings tider ThreadX, real tids kärnan i real tid

[Kapitel 4](chapter4.md) – information om programmets gränssnitt till Azure återställnings tider ThreadX

[Kapitel 5](chapter5.md) – beskriver hur du skriver I/O-drivrutiner för Azure återställnings tider ThreadX-program

[Kapitel 6](chapter6.md) – beskriver demonstrations programmet som medföljer varje Azure återställnings tider ThreadX processor support paket

[Bilaga A](appendix-a.md) – Azure återställnings tider THREADX-API

[Bilaga B](appendix-b.md) – Azure återställnings tider ThreadX-konstanter

[Bilaga C](appendix-c.md) – data typer för Azure återställnings tider-ThreadX

[Bilaga D](appendix-d.md) – ASCII-diagram

## <a name="guide-conventions"></a>Guide konventioner

*Kursiv stil* -teckensnitt anger bok titlar, betonar viktiga ord och indikerar parametrar.

**Fetstil** – typsnitt anger nyckelord, konstanter, typ namn, gränssnitts element, variabel namn och betonar viktiga ord.

***Kursiv stil och fetstil*** – typsnitt anger fil namn och funktions namn.

> [!IMPORTANT]
> Informations symboler drar uppmärksamheten till viktig eller ytterligare information som kan påverka prestandan eller funktionen.

> [!WARNING]
> Varnings symboler drar uppmärksamhet till situationer där utvecklare bör ta hand om att undvika att de kan orsaka allvarliga fel.

## <a name="azure-rtos-threadx-data-types"></a>Data typer för Azure dataåterställnings tiders-ThreadX

Förutom de anpassade data typerna för kontroll strukturen i Azure återställnings tider-ThreadX finns det en serie särskilda data typer som används i Azure återställnings tider ThreadX service Call-gränssnitt. Dessa särskilda data typer mappar direkt till data typer för den underliggande C-kompilatorn. Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer. Du hittar den exakta implementeringen i filen ***tx_port. h*** som ingår i källan.

Följande är en lista över data typer för Azure återställnings tider ThreadX service Call och deras associerade betydelser:

| Datatyp  | Beskrivning |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **UINT** | Basic-osignerat heltal. Den här typen måste ha stöd för 8-bitars osignerade data. den är dock mappad till den mest användbara osignerade data typen. |
| **ULONG** | Osignerad lång typ. Den här typen måste ha stöd för 32-bitars osignerade data. |
| **VOID** | Nästan alltid ekvivalent med kompilatorns void-typ. |
| **HÄNGANDE** | Oftast en vanlig 8-bitars tecken typ. |
|  |  |

Ytterligare data typer används i Azure återställnings tider ThreadX-källan. De finns också i filen ***tx_port. h*** .

## <a name="customer-support-center"></a>Kund Support Center

Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här. Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:

1. En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider-ThreadX som föregåde problemet.
3. Innehållet i den *_tx_version_id* strängen som finns i filen *tx_port. h* i distributionen. Den här strängen ger oss värdefull information om din kör tids miljö.
4. Innehållet i RAM-minnet för **_tx_build_options** **ulong** -variabeln. Den här variabeln ger oss information om hur ditt Azure återställnings tider ThreadX-bibliotek har skapats.
