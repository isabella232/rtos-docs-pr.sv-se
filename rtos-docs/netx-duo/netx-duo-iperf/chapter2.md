---
title: Kapitel 2 – Installera och använda Azure RTOS NetX Duo Iperf
description: Det här kapitlet innehåller instruktioner för att installera och använda Iperf-exemplet.
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7e80d89a334ceec3467b23574ab5c231a15f68a1
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/20/2021
ms.locfileid: "122610020"
---
# <a name="chapter-2-installation-and-use"></a>Kapitel 2 Installation och användning

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av NetX Duo Iperf-demonstrationen.

## <a name="installing-the-demonstration"></a>Installera demonstrationen

Följ de plattformsspecifika installationsanvisningar som anges i distributionen.

## <a name="installing-iperf"></a>Installera Iperf

Det finns en mängd olika Iperf-program som du kan använda. Exemplen i det här dokumentet baseras dock på Java-baserad ***Jperf 2.0.2***, som är tillgänglig från flera källor på Internet.

> [Obs] *Jperf kräver att Java är installerat på värddatorn.*

## <a name="setting-the-ip-address"></a>Ange IP-adressen

Ip-adressen för NetX Duo Iperf Demonstration är som standard inställd på **192.2.2.149**. Detta anges i filen **_demo_netx_duo_iperf.c_*_ som en parameter för anropet till _*_nx_ip_create_**.

## <a name="network-assumptions"></a>Nätverksantaganden

Den här demonstrationen förutsätter att Iperf-värddatorn och måltavlan som kör NetX Duo Iperf Demonstration är anslutna till en 100Mbps full duplex Ethernet-växel. För att uppnå bästa prestanda bör det inte finnas någon annan trafik i testnätverket.

Det är också möjligt att ansluta Iperf-värden och NetX Duo-målkortet tillbaka till bakåt med en cross-over Ethernet-kabel.

## <a name="running-the-demonstration"></a>Köra demonstrationen

Det är enkelt att köra demonstrationen. läs bara in, skapa och kör NetX Duo Iperf Demonstration-projektet – vanligtvis ***demo_netx_duo_iperf***.

## <a name="browse-to-the-demonstration"></a>Bläddra till demonstrationen

Bläddra till måltavlan via en webbläsare på Iperf-värdplattformen. Förutsatt att måltavlan HAR IP-adressen **192.2.2.149** är följande ett exempel på den första webbsidan NetX Duo Iperf Demonstration.

![Ett exempel på den ursprungliga webbsidan Iperf](media/Picture1.jpg)

## <a name="running-jperf"></a>Köra Jperf

Det är enkelt att köra Jperf. Dubbelklicka bara på Windows batch-fil ***jperf.bat** _. Detta startar Jperf IDE enligt nedan. När Jperf IDE visas måste fältet _ *Serveradress** anges till IP-adressen för NetX Duo Iperf Demonstration-måltavlan. I det här exemplet är NETX Duo-måltavlan IP-adressen **192.2.2.149**. Det är också värt att notera fälten **UDP-bandbredd** **och UDP-paketstorlek.** Dessa måste konfigureras för optimala UDP-mottagningsprestanda, enligt nedan.

![Optimera UDP-prestanda.](media/Picture2.jpg)
