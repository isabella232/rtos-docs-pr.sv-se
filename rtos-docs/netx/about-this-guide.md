---
title: Om Azure RTOS NetX
description: Den här guiden innehåller omfattande information om Azure RTOS NetX, Microsofts nätverksstack med höga prestanda.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d77997e8c5bac598f382e1169a56727af09ab108f57c90cc6265df0691b5926
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796420"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a>Om Azure RTOS NetX

Den här guiden innehåller omfattande information om Azure RTOS NetX, Microsofts nätverksstack med höga prestanda.

Den är avsedd för inbäddade realtidsutvecklare som är bekanta med grundläggande nätverksbegrepp, Azure RTOS ThreadX och programmeringsspråket C.

## <a name="organization"></a>Organisation

[Kapitel 1](chapter1.md) – Introducerar Azure RTOS NetX

[Kapitel 2](chapter2.md) – Ger grundläggande steg för att installera och använda Azure RTOS NetX med ditt ThreadX-program.

[Kapitel 3](chapter3.md) – Ger en funktionell översikt över Azure RTOS NetX-systemet och grundläggande information om TCP/IP-nätverksstandarder.

[Kapitel 4](chapter4.md) – Beskriver programmets gränssnitt för att Azure RTOS NetX.

[Kapitel 5](chapter5.md) – Beskriver nätverksdrivrutiner för Azure RTOS NetX.

[Bilaga A](appendix-a.md) – Azure RTOS NetX Services

[Bilaga B](appendix-b.md) – Azure RTOS NetX-konstanter

[Bilaga C](appendix-c.md) – Azure RTOS NetX-datatyper

[Bilaga D](appendix-d.md) – BSD-Compatible Socket API

[Bilaga E](appendix-e.md) – ASCII-diagram

## <a name="azure-rtos-netx-data-types"></a>Azure RTOS NetX-datatyper

Förutom de anpassade datatyperna Azure RTOS NetX-kontrollstruktur finns det flera särskilda datatyper som används i Azure RTOS NetX-tjänstens anropsgränssnitt. Dessa särskilda datatyper mappar direkt till datatyperna i den underliggande C-kompilatorn. Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer. Den exakta implementeringen ärvs från ThreadX och finns i ***filen tx_port.h*** som ingår i ThreadX-distributionen.

Följande är en lista över de Azure RTOS netx-tjänstens anropsdatatyper och deras associerade betydelser:

| Datatyper | Description  |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **Uint**  | Grundläggande heltal utansignering. Den här typen måste ha stöd för 32-bitars osignerade data. Den mappas dock till den mest praktiska osignerade datatypen. |
| **ULONG** | Osignerad lång typ. Den här typen måste ha stöd för 32-bitars osignerade data.                                                                      |
| **Void**  | Nästan alltid likvärdigt med kompilatorns void-typ.                                                                                 |
| **Char**  | Oftast en standardtyp med 8 bitar.                                                                                           |

Ytterligare datatyper används i Azure RTOS NetX-källan. De finns antingen i filerna ***tx_port.h** _ eller _ *_nx_port.h_** .

## <a name="customer-support-center"></a>Customer Support Center

Skicka en supportbiljett via Azure-portalen för frågor eller hjälp med att följa stegen här. Ange följande information i ett e-postmeddelande så att vi kan lösa din supportbegäran mer effektivt:

1. En detaljerad beskrivning av problemet, inklusive förekomstfrekvens och om det kan återskapas på ett tillförlitligt sätt.

2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure RTOS NetX som föregick problemet.

3. Innehållet i de **_tx_version_id**  _nx_version_id strängarna som finns i **_filerna tx_port.h_ _ och *_*_nx_port.h_** i distributionen. Dessa strängar ger oss värdefull information om din körningsmiljö.

4. Innehållet i RAM-minnet för följande **ULONG-variabler:**

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    Dessa variabler ger oss information om hur dina Azure RTOS ThreadX- och Azure RTOS NetX-bibliotek har skapats.

5. En spårningsbuffert avbildas omedelbart efter att problemet har identifierats. Detta åstadkoms genom att Azure RTOS ThreadX- och Azure RTOS NetX-bibliotek med TX_ENABLE_EVENT_TRACE och **anropa** **tx_trace_enable** med spårningsbuffertinformationen. Se användarhandboken Azure RTOS TraceX för mer information.
