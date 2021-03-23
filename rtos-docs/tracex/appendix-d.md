---
title: Bilaga D – dumpning och spårning av spårning
description: Dumpning av den sökta bufferten som skapades av Azure återställnings tider-ThreadX till en fil på värddatorn görs via kommandon och/eller verktyg som tillhandahålls av det verktyg som används för att använda verktyget.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 30f6b5e329feeb2dca37dda391fd738aba587c9a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827723"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a>Bilaga D – dumpning och spårning av spårning

Dumpning av den sökta bufferten som skapades av Azure återställnings tider-ThreadX till en fil på värddatorn görs via kommandon och/eller verktyg som tillhandahålls av det verktyg som används för att använda verktyget. Den här bilagan innehåller exempel på dumpning av en spårningssession till en värd fil i några av de populäraste utvecklingsverktyg som används med ThreadX. 

## <a name="benchx-tools"></a>BenchX-verktyg

Det går att dumpa kommandobufferten till en värd fil enkelt med BenchX-verktygen genom att välja ***lagra minne till fil** _ i vyn _ *_Memory_* *, enligt nedan:

![Skärm bild av vyn minne i BenchX-verktygen.](./media/user-guide/image642.jpg)

I det här läget anger du adressen till spårningsprovider, storlek, mål fil namn (inklusive sökväg) och väljer knappen ***Spara*** som visas nedan. Då skapas den binära spårnings filen för visning i TraceX.

![Skärm bild av dialog rutan Spara BenchX-verktyg.](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a>RealView-verktyg

Det går lätt att dumpa kommandobufferten till en värd fil med ARM RealView-verktygen genom att ange följande kommando i kommando tolken i RealView:

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

När åtgärden har slutförts innehåller filen ***trace_file. trx*** den sökta bufferten som börjar på adressen 0x6860 och går upp för att adressera 0xE560. Den här filen är klar för visning av TraceX.

## <a name="iar-tools"></a>IAR-verktyg

Spårningssessionen kan dumpas till en värd fil enkelt med IAR-verktygen genom att helt enkelt Högerklicka i vyn minne och välja ***minnet Spara...*** alternativ, som du ser nedan.

![Skärm bild av alternativet för minnes sparande i IAR-verktygen.](./media/user-guide/image0_311.jpg)

Detta resulterar i att dialog rutan ***minne Spara** _ visas. Ange start-och slut adress och spårnings filens namn och välj sedan knappen _*_Spara_*_ . I det exempel som visas nedan sparar IAR-verktygen den angivna spårningssessionen i Intel HEX-poster i filen _ *_trace_file. hex_* *.

![Skärm bild av dialog rutan för att spara IAR-verktyg.](./media/user-guide/image648.jpg)

Nu har vi en spårnings-buffert Sparad i ***trace_file. hex*** -filen på värden och är klar för visning med TraceX.

## <a name="codewarrior-tools"></a>CodeWarrior-verktyg

Det går lätt att dumpa kommandobufferten till en värd fil med CodeWarrior-verktygen genom att ange ***Save** _-kommandot i kommando fönstret. I följande exempel _ *_Save_**-kommando förutsätter att spårningssessionen börjar vid 0x102200 och slutar på 0x109F00:

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

Detta resulterar i att den sökta kommandobufferten sparas i filen ***trace_file. trx*** på värden.

## <a name="mplab-tools"></a>MPLAB-verktyg

MPLAB kan skapa en TraceX-kompatibel spårnings fil via verktyget export Table, som tillåter export av alla minnes intervall till en värd fil. Fortsätt enligt följande om du vill använda det här verktyget för att skapa en spårnings fil för TraceX:

**Steg 1** Öppna ett minnes fönster genom att välja Visa > minne.

![Skärm bild av det valda minnet på menyn Visa.](./media/user-guide/image0_316.jpg)

**Steg 2** Högerklicka i **vyn minne** om du vill visa en lista med alternativ. Ange **visnings format – 1 byte** för att välja byte-visning..

![Skärm bild av vyn minne med alternativet visnings format markerat.](./media/user-guide/image650.png)

![Skärm bild av dialog rutan gå till.](./media/user-guide/image651.jpg)

**Steg 3** Högerklicka igen i fönstret **minnes visning** och välj **gå till**, så öppnas en dialog ruta där du kan ange adressen till händelsesessionen. I det här exemplet visas **_event_buffer_** visas.

![Skärm bild av minnes visning med alternativet gå till valt.](./media/user-guide/image0_312.jpg)

![Skärm bild av ett exempel som visar event_buffer som visas.](./media/user-guide/image653.png)

**Steg 4** Detta markerar innehållet på den första platsen i spårningssessionen, som alltid är strängen BTXT....

![Skärm bild av den första platsen i den sökta kommandobufferten.](./media/user-guide/image0_313.jpg)

**Steg 5** Högerklicka sedan igen för att öppna menyn Alternativ och välj **Exportera tabell**.

![Skärm bild av vyn minne med alternativet Exportera tabell markerat.](./media/user-guide/image0_314.jpg)

**Steg 6** Dialog rutan **Exportera tabell** visas, som du ser. Ange det adress intervall som ska exporteras. För en 8K-spårningssession, som är fallet i det här exemplet, anger du intervallet 0xA00006AC till 0xA00026AC och anger ett namn för den värd fil som ska skapas (demo_threadx. trx i det här exemplet).

! [[Skärm bild av dialog rutan exportera som.](./media/user-guide/image656.jpg)

**Steg 7** En fil med namnet **demo_threadx. trx** kommer att skapas på värden och den här filen kan öppnas av TraceX.

## <a name="ghs-tools"></a>GHS-verktyg

Spårningssessionen kan dumpas till en värd fil enkelt med GHS-verktygen genom att ange följande kommando i kommando tolken i fel söknings kommando fönstret:

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

Vid slut för Ande kommer filen **demo_threadx. trx** att innehålla den spårningsprovider som finns i event_buffer med en storlek på 32 768 byte och är klar för visning av TraceX.

## <a name="renesas-hew"></a>Renesas HEW

Det går lätt att dumpa kommandobufferten till en värd fil med Renasas HEW-verktygen genom att följa de tre stegen (och under stegen) nedan:

**Steg 1** Öppna minnes fönstret.

! [[Skärm bild av minnes fönstret.](./media/user-guide/image657.jpg)

**Steg 2** Placera markören i minnes fönstret och högerklicka.

![Skärm bild av minnes fönstret med alternativet Spara valt.](./media/user-guide/image0_315.jpg)

**Steg 3** Välj Spara och gör följande i fönstret Spara minne som:

- Välj fil format: Binary.
- Ange fil namn: efter behov
- Ange start adress: trace_buffer
- Ange slut adress: (trace_buffer + storlek)
- Ange åtkomst storlek: 1
- Klicka på Spara

![Skärm bild av dialog rutan Spara minne som.](./media/user-guide/image659.jpg)