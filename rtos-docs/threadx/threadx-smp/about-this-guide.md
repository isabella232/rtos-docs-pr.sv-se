---
title: Om den här guiden
description: Den här guiden innehåller omfattande information om Azure återställnings tider ThreadX SMP, den inbyggda real tids kärnan i real tid i Microsoft.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2399666b5b4d7c34db50d539e200c90f06f7235f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825446"
---
# <a name="about-this-guide"></a>Om den här guiden

Den här guiden innehåller omfattande information om Azure återställnings tider ThreadX SMP, den inbyggda real tids kärnan i real tid i Microsoft.

Den är avsedd för den inbäddade programutvecklaren i real tid. Utvecklaren bör vara bekant med vanliga operativ system funktioner i real tid och programmeringsspråket C.

## <a name="organization"></a>Organisation

| Kapitel       | Översikt                    |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| **Kapitel 1** | Innehåller en grundläggande översikt över ThreadX SMP och dess relation till inbäddad real tids utveckling.           |
| **Kapitel 2** | Innehåller grundläggande steg för att installera och använda ThreadX SMP i ditt program direkt från *lådan*.           |
| **Kapitel 3** | Beskriver i detalj den funktionella driften av ThreadX SMP, den högpresterande SMP-kärnan i real tid.    |
| **Kapitel 4** | Information om programmets gränssnitt till ThreadX SMP.                                                        |
| **Kapitel 5** | Beskriver hur du skriver I/O-drivrutiner för ThreadX SMP-program.                                                |
| **Kapitel 6** | Beskriver det demonstrations program som medföljer varje ThreadX SMP-processors support paket. |
| **Bilaga A** | ThreadX SMP-API        |
| **Bilaga B** | ThreadX SMP-konstanter  |
| **Bilaga C** | ThreadX SMP-datatyper |
| **Bilaga D** | ASCII-diagram            |

## <a name="guide-conventions"></a>Guide konventioner

- *Kursiv stil*  -  *teckensnittet anger bok titlar, betonar viktiga ord och indikerar variabler.*
- **Fetstil**  -  **teckensnittet anger fil namn, viktiga ord och betonar viktiga ord och variabler.**

> [!IMPORTANT]
> Informations symboler drar uppmärksamheten till viktig eller ytterligare information som kan påverka prestandan eller funktionen.

> [!WARNING]
> Varnings symboler drar uppmärksamhet till situationer där utvecklare bör ta hand om att undvika att de kan orsaka allvarliga fel.

## <a name="threadx-smp-data-types"></a>ThreadX SMP-datatyper

Förutom de anpassade data typerna för SMP-ThreadX, finns det en serie särskilda data typer som används i ThreadX SMP-tjänstens anrops gränssnitt. Dessa särskilda data typer mappar direkt till data typer för den underliggande C-kompilatorn. Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer. Du hittar den exakta implementeringen i filen ***tx_port. h*** som finns på distributions disken.

Följande är en lista över ThreadX-data typer för SMP-tjänsten och deras associerade betydelser:

| Datatyp          | Innebörd                                                          |
| --------- | --------------------------------------------------------- |
| **UINT**  | Basic-osignerat heltal. Den här typen måste ha stöd för 8-bitars osignerade data. den är dock mappad till den mest användbara osignerade data typen. |
| **ULONG** | Osignerad lång typ. Den här typen måste ha stöd för 32-bitars osignerade data.                                                                     |
| **VOID**  | Nästan alltid ekvivalent med kompilatorns void-typ.                                                                                |
| **HÄNGANDE**  | Oftast en vanlig 8-bitars tecken typ.                                                                                          |

Ytterligare data typer används i ThreadX SMP-källa. De finns också i filen ***tx_port. h*** .

## <a name="customer-support-center"></a>Kund Support Center

Support-e-post: [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) webb sida: Azure.com/RTOS

### <a name="latest-product-information"></a>Senaste produkt information

Besök azure.com/rtos-webbplatsen och välj meny alternativet support för att hitta den senaste informationen om onlinesupport, inklusive information om de senaste ThreadX SMP-produktsortimenten.

### <a name="what-we-need-from-you"></a>Vad vi behöver från dig

Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:

1. En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller ThreadX-SMP som föregåde problemet.
3. Innehållet i ***_tx_version_id** _-strängen som finns i filen _ *_tx_port. h_** i distributionen. Den här strängen ger oss värdefull information om din kör tids miljö.
4. Innehållet i RAM-minnet för ***_tx_build_options*** ulong-variabeln. Den här variabeln ger oss information om hur ditt ThreadX SMP-bibliotek byggdes.

### <a name="where-to-send-comments-about-this-guide"></a>Var du ska skicka kommentarer om den här guiden

Skicka kommentarer och förslag till kund Support Center vid [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Skriv "THREADX SMP user guide" på ämnes raden.
