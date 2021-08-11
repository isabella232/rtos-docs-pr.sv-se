---
title: Om användarhandboken Azure RTOS NetX Duo
description: Den här guiden innehåller omfattande information om Azure RTOS NetX Duo, Microsofts högpresterande IPv4/IPv6 dubbla nätverksstack.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 032cca3ccdaa7600732d52894d63e5bef366010abaa1145417201f48cb034ab5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790181"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a>Om användarhandboken Azure RTOS NetX Duo

Den här guiden innehåller omfattande information om Azure RTOS NetX Duo, Microsofts högpresterande IPv4/IPv6 dubbla nätverksstack. 

Den är avsedd för inbäddade realtidsutvecklare som är bekanta med grundläggande nätverksbegrepp, Azure RTOS ThreadX och programmeringsspråket C.

## <a name="organization"></a>Organisation

[Kapitel 1](chapter1.md) – Introducerar Azure RTOS NetX Duo

[Kapitel 2](chapter2.md) – Ger grundläggande steg för att installera och använda Azure RTOS NetX Duo med ditt ThreadX-program

[Kapitel 3](chapter3.md) – Ger en funktionell översikt över Azure RTOS NetX Duo-systemet och grundläggande information om TCP/IP-nätverksstandarder

[Kapitel 4](chapter4.md) – Beskriver programmets gränssnitt för att Azure RTOS NetX Duo

[Kapitel 5](chapter5.md) – Beskriver nätverksdrivrutiner för Azure RTOS NetX Duo

[Bilaga A](appendix-a.md) – Azure RTOS NetX Duo Services

[Bilaga B](appendix-b.md) – Azure RTOS NetX Duo-konstanter

[Bilaga C](appendix-c.md) – Azure RTOS NetX Duo-datatyper

[Bilaga D](appendix-d.md) – BSD-Compatible Socket API

[Bilaga E](appendix-e.md) – ASCII-diagram

## <a name="guide-conventions"></a>Guidekonventioner

Italics – Typeface anger boktitlar, betonar viktiga ord och anger variabler.

**Boldface** – Typeface anger filnamn, nyckelord och betonar viktiga ord och variabler ytterligare.

> [!IMPORTANT]
> Informationssymboler uppmärksammar viktig eller ytterligare information som kan påverka prestanda eller funktion.
 
> [!WARNING]
> Varningssymboler uppmärksammar situationer som utvecklare bör undvika eftersom de kan orsaka allvarliga fel.

## <a name="azure-rtos-netx-duo-data-types"></a>Azure RTOS NetX Duo-datatyper

Förutom de anpassade datatyperna Azure RTOS NetX Duo-kontrollstruktur finns det flera särskilda datatyper som används i Azure RTOS Anropsgränssnitt för NetX Duo-tjänsten. Dessa särskilda datatyper mappar direkt till datatyper för den underliggande C-kompilatorn. Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer. Den exakta implementeringen ärvs från ThreadX och finns i ***filen tx_port.h*** som ingår i ThreadX-distributionen.

Följande är en lista över datatyper Azure RTOS NetX Duo-tjänstens anrop och deras associerade betydelser:

**UINT:** Grundläggande osignerat heltal. Den här typen måste ha stöd för 32-bitars osignerade data. Den mappas dock till den mest praktiska osignerade datatypen.  
**ULONG:** Osignerad lång typ. Den här typen måste ha stöd för 32-bitars osignerade data.
**VOID:** Nästan alltid likvärdigt med kompilatorns void-typ.  
**CHAR:** Är oftast en standardtyp med 8 bitar.  

Ytterligare datatyper används i Azure RTOS NetX Duo-källa. De finns antingen i filerna ***tx_port.h** _ eller _ *_nx_port.h_** .

## <a name="customer-support-center"></a>Kundsupport

Skicka en supportbiljett via Azure-portalen för frågor eller hjälp med att följa stegen här. Ange följande information i ett e-postmeddelande så att vi kan lösa din supportbegäran mer effektivt:

1. En detaljerad beskrivning av problemet, inklusive förekomstfrekvens och huruvida det kan återskapas på ett tillförlitligt sätt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure RTOS NetX Duo som föregick problemet.
3. Innehållet i de _tx_version_id och _nx_version_id som finns i tx_port.h- och nx_port.h-filerna för distributionen. Dessa strängar ger oss värdefull information om din körningsmiljö.
4. Innehållet i RAM-minnet för följande ULONG-variabler:

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    Dessa variabler ger oss information om hur dina Azure RTOS ThreadX- och Azure RTOS NetX Duo-bibliotek har skapats.

5. En spårningsbuffert avbildas omedelbart efter att problemet har identifierats. Detta åstadkoms genom att skapa Azure RTOS ThreadX- och Azure RTOS NetX Duo-bibliotek med TX_ENABLE_EVENT_TRACE och anropa tx_trace_enable med spårningsbuffertinformationen.
