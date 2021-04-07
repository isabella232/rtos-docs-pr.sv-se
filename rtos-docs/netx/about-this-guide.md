---
title: Om användar handboken för Azure återställnings tider NetX
description: Den här guiden innehåller omfattande information om Azure återställnings tider NetX, Microsofts högpresterande nätverks stack.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 01077e3315e87b918cdfd47423d8e0c1b6bbdbbd
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550277"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a>Om användar handboken för Azure återställnings tider NetX

Den här guiden innehåller omfattande information om Azure återställnings tider NetX, Microsofts högpresterande nätverks stack.

Den är avsedd för inbäddade program varu utvecklare i real tid som är bekanta med grundläggande nätverks koncept, Azure återställnings tider-ThreadX och programmeringsspråket C.

## <a name="organization"></a>Organisation

[Kapitel 1](chapter1.md) – introducerar Azure återställnings tider netx

[Kapitel 2](chapter2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider-netx med ditt ThreadX-program.

[Kapitel 3](chapter3.md) – innehåller en funktionell översikt över Azure återställnings tider netx-systemet och grundläggande information om TCP/IP-nätverksfunktioner.

[Kapitel 4](chapter4.md) – information om programmets gränssnitt till Azure återställnings tider netx.

[Kapitel 5](chapter5.md) – beskriver nätverks driv rutiner för Azure återställnings tider netx.

[Bilaga A](appendix-a.md) – Azure återställnings tider netx-tjänster

[Bilaga B](appendix-b.md) – Azure återställnings tider netx-konstanter

[Bilaga C](appendix-c.md) – data typer för Azure återställnings tider-netx

[Bilaga D](appendix-d.md) – BSD-Compatible socket-API

[Bilaga E](appendix-e.md) -ASCII-diagram

## <a name="azure-rtos-netx-data-types"></a>Data typer för Azure dataåterställnings tiders-NetX

Förutom de anpassade data typerna för kontroll strukturen i Azure återställnings tider-NetX, finns det flera särskilda data typer som används i Azure återställnings tider NetX service Call-gränssnitt. Dessa särskilda data typer mappar direkt till data typer för den underliggande C-kompilatorn. Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer. Den exakta implementeringen ärvs från ThreadX och kan hittas i filen ***tx_port. h*** som ingår i ThreadX-distributionen.

Följande är en lista över data typer för Azure återställnings tider NetX service Call och deras associerade betydelser:

| Datatyper | Description  |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **UINT**  | Basic-osignerat heltal. Den här typen måste ha stöd för 32-bitars osignerade data. den är dock mappad till den mest användbara osignerade data typen. |
| **ULONG** | Osignerad lång typ. Den här typen måste ha stöd för 32-bitars osignerade data.                                                                      |
| **VOID**  | Nästan alltid ekvivalent med kompilatorns void-typ.                                                                                 |
| **HÄNGANDE**  | Oftast en vanlig 8-bitars tecken typ.                                                                                           |

Ytterligare data typer används i Azure återställnings tider NetX-källan. De finns antingen i ***tx_port. h** _ eller _ *_nx_port. h_** filer.

## <a name="customer-support-center"></a>Kund Support Center

Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här. Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:

1. En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.

2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider-NetX som föregåde problemet.

3. Innehållet i **_tx_version_id** -och **_nx_version_id** -strängar som finns i **_tx_port. h_*_-och _*_nx_port. h_** -filerna för distributionen. De här strängarna ger oss värdefull information om din kör tids miljö.

4. Innehållet i RAM-minnet för följande **ulong** -variabler:

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    Dessa variabler ger oss information om hur dina Azure återställnings tider ThreadX-och Azure återställnings tider NetX-bibliotek skapades.

5. En spårnings-buffert som samlats in omedelbart efter det att problemet upptäcktes. Detta åstadkommer du genom att skapa Azure återställnings tider-ThreadX och Azure återställnings tider NetX-biblioteken med **TX_ENABLE_EVENT_TRACE** och anropa **tx_trace_enable** med information om spårnings-bufferten. Mer information finns i användar handboken för Azure återställnings tider TraceX.
