---
title: Om användar handboken för Azure återställnings tider NetX Duo
description: Den här guiden innehåller omfattande information om Azure återställnings tider NetX Duo, Microsofts högpresterande IPv4/IPv6-stack med dubbla nätverk.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b1eef5bfa28f13d7a6b627792f96039b252f2355
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826238"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a>Om användar handboken för Azure återställnings tider NetX Duo

Den här guiden innehåller omfattande information om Azure återställnings tider NetX Duo, Microsofts högpresterande IPv4/IPv6-stack med dubbla nätverk. 

Den är avsedd för inbäddade program varu utvecklare i real tid som är bekanta med grundläggande nätverks koncept, Azure återställnings tider-ThreadX och programmeringsspråket C.

## <a name="organization"></a>Organisation

[Kapitel 1](chapter1.md) – introducerar Azure återställnings tider netx Duo

[Kapitel 2](chapter2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider netx Duo med ditt ThreadX-program

[Kapitel 3](chapter3.md) – innehåller en funktionell översikt över Azure återställnings tider netx Duo-systemet och grundläggande information om TCP/IP nätverks standarder

[Kapitel 4](chapter4.md) – information om programmets gränssnitt till Azure återställnings tider netx Duo

[Kapitel 5](chapter5.md) – beskriver nätverks driv rutiner för Azure återställnings tider netx Duo

[Bilaga A](appendix-a.md) – Azure återställnings tider netx Duo-tjänster

[Bilaga B](appendix-b.md) – Azure återställnings tider netx Duo-konstanter

[Bilaga C](appendix-c.md) – Azure återställnings tider netx Duo-datatyper

[Bilaga D](appendix-d.md) – BSD-Compatible socket-API

[Bilaga E](appendix-e.md) -ASCII-diagram

## <a name="guide-conventions"></a>Guide konventioner

Kursiv stil – teckensnittet noterar bok titlar, betonar viktiga ord och indikerar variabler.

**Fetstil** – typsnitt anger fil namn, viktiga ord och betonar viktiga ord och variabler.

> [!IMPORTANT]
> Informations symboler drar uppmärksamheten till viktig eller ytterligare information som kan påverka prestandan eller funktionen.
 
> [!WARNING]
> Varnings symboler drar uppmärksamhet till situationer som utvecklare bör undvika eftersom de kan orsaka allvarliga fel.

## <a name="azure-rtos-netx-duo-data-types"></a>Data typer för Azure återställnings tider-NetX Duo

Förutom de anpassade data typerna för Azure återställnings tider NetX Duo-kontrollen finns det flera särskilda data typer som används i Azure återställnings tider NetX Duo-tjänstens anrops gränssnitt. Dessa särskilda data typer mappar direkt till data typer för den underliggande C-kompilatorn. Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer. Den exakta implementeringen ärvs från ThreadX och kan hittas i filen ***tx_port. h*** som ingår i ThreadX-distributionen.

Följande är en lista över data typerna för Azure återställnings tider NetX Duo-tjänstens anrop och deras associerade betydelser:

**Uint**: Basic-osignerat heltal. Den här typen måste ha stöd för 32-bitars osignerade data. den är dock mappad till den mest användbara osignerade data typen.  
**Ulong**: osignerad lång typ. Den här typen måste ha stöd för 32-bitars osignerade data.
**Void**: nästan alltid likvärdigt med kompilatorns void-typ.  
**Char**: oftast en vanlig 8-bitars tecken typ.  

Ytterligare data typer används i Azure återställnings tider-NetX Duo-källan. De finns antingen i ***tx_port. h** _ eller _ *_nx_port. h_** filer.

## <a name="customer-support-center"></a>Kund Support Center

Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här. Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:

1. En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider NetX Duo som föregåde problemet.
3. Innehållet i _tx_version_id-och _nx_version_id-strängar som finns i tx_port. h-och nx_port. h-filerna för distributionen. De här strängarna ger oss värdefull information om din kör tids miljö.
4. Innehållet i RAM-minnet för följande ULONG-variabler:

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    Dessa variabler ger oss information om hur dina Azure återställnings tider ThreadX-och Azure återställnings tider NetX Duo-bibliotek skapades.

5. En spårnings-buffert som samlats in omedelbart efter det att problemet upptäcktes. Detta åstadkommer du genom att skapa Azure återställnings tider-ThreadX och Azure återställnings tider NetX Duo-bibliotek med TX_ENABLE_EVENT_TRACE och anropa tx_trace_enable med information om spårnings-bufferten.
