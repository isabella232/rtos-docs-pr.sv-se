---
title: Kapitel 3 – Köra UDP-överföringstestet
description: Det här kapitlet innehåller instruktioner för att köra Iperf-exemplet.
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2a68ba3ddb71adc424002c815fd023f50b552997
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/20/2021
ms.locfileid: "122610021"
---
# <a name="chapter-3-running-the-demonstration"></a>Kapitel 3 som kör demonstrationen

Förutsatt att värdwebbläsaren visar NetX Duo Iperf Demonstration-webbsidan som visades tidigare och Jperf körs på värden, beskriver det här kapitlet hur du kör varje Iperf-test.

## <a name="running-the-udp-transmit-test"></a>Köra UDP-överföringstestet

UDP-överföringstestet avgör prestanda för NetX Duo UDP-överföring till värden. I det här testet är NetX Duo-målet klienten och Jperf-värden är servern. Välj först **Server** och **UDP** i Jperf IDE. Välj sedan **Kör IPerf!** för att initiera Iperf-servern enligt nedan.

![Köra UDP-överföringstestet.](media/picture3.jpg)

Från webbplatsen NetX Duo Iperf Demonstration väljer du knappen **Starta UDP-överföringstest** för att starta testet. Du bör nu se prestandastatistik i Jperf IDE och NetX Duo-webbsidan har uppdaterats, enligt nedan.

![Teststatistik för UDP-överföring.](media/picture4.jpg)

Slutför testet genom att välja **länken** här på webbsidan NetX Duo Iperf Demonstration. Nu bör du se prestandaresultaten för testet. I det här exemplet var UDP-överföringsprestanda för NetX Duo-målet till Iperf-värden 94 Mbit/s på NetX Duo-målet, enligt nedan.

![Testresultat för UDP-överföring.](media/picture5.jpg)

## <a name="running-the-udp-receive-test"></a>Köra UDP-mottagningstestet

UDP-mottagningstestet avgör prestanda för NetX Duo UDP-mottagning på NetX Duo-målet. I det här testet är NetX Duo-målet servern och Jperf-värden är klienten. Välj först **Klient och** **UDP** i Jperf IDE. Välj sedan **Start UDP Receive Test (Starta UDP-mottagningstest)** på webbsidan NetX Duo Iperf Demonstration (Iperf-demonstration) enligt följande bild.

![Köra UDP-mottagningstestet.](media/picture6.jpg)

Välj kör **IPerf!** från Jperf IDE och observera statistik i Jperf IDE, enligt nedan.

![UDP tar emot teststatistik.](media/picture7.jpg)

Slutför testet genom att välja länken **här** på webbsidan NetX Duo Iperf Demonstration. Nu bör du se prestandaresultaten för testet. I det här exemplet var UDP-mottagningsprestandan på NetX Duo-målet 95 Mbit/s, enligt nedan.

![UDP-mottagning av testresultat](media/picture8.jpg)

## <a name="running-the-tcp-transmit-test"></a>Köra TCP-överföringstestet

TCP-överföringstestet avgör prestanda för NetX Duo TCP-överföring till värden. I det här testet är NetX Duo-målet klienten och Jperf-värden är servern. Välj först **Server** och **TCP** i Jperf IDE. Välj sedan **Kör IPerf!** för att initiera Iperf-servern enligt nedan.

![Köra TCP-överföringstestet.](media/picture9.jpg)

Från webbplatsen NetX Duo Iperf Demonstration väljer du knappen **Starta TCP-överföringstest** för att starta testet. Du bör nu se prestandastatistik i Jperf IDE och netX Duo Iperf Demonstration-webbsidan uppdaterade, enligt nedan.

![TCP-överföringsteststatistik.](media/picture10.jpg)

Slutför testet genom att välja länken ***här*** på webbsidan NetX Duo Iperf Demonstration. Nu bör du se prestandaresultaten för testet. I det här exemplet var TCP-överföringsprestanda för NetX Duo-målet 91 Mbit/s, enligt nedan.

![TCP-överföringstestresultat.](media/picture11.jpg)

## <a name="running-the-tcp-receive-test"></a>Köra TCP-mottagningstestet

TCP-mottagningstestet avgör prestanda för NetX Duo TCP-mottagning på NetX Duo-målet. I det här testet är NetX Duo-målet servern och Jperf-värden är klienten. Välj först **Klient och** **TCP** i Jperf IDE. Välj sedan **Starta TCP-mottagningstest** på NetX Duo-webbsidan enligt bilden.

![Köra TCP-mottagningstestet](media/picture12.jpg)

Välj kör **IPerf!** från Jperf IDE och observera statistik i Jperf IDE, enligt nedan.

![TCP-mottagningsteststatistik.](media/picture13.jpg)

Slutför testet genom att välja länken ***här*** på webbsidan NetX Duo Iperf Demonstration. Nu bör du se prestandaresultaten för testet. I det här exemplet var TCP-mottagningsprestandan på NetX Duo-målet 71 Mbit/s, enligt nedan.

![TCP-mottagningstestresultat.](media/picture14.jpg)
