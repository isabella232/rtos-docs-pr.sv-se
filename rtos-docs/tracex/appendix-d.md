---
title: Bilaga D – Dumpning och spårningsbuffert
description: Dumpning av spårningsbufferten som skapats av Azure RTOS ThreadX till en fil på värddatorn görs via kommandon och/eller verktyg som tillhandahålls av det specifika utvecklingsverktyg som används.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: afbbabbd04ac4c33a747bb0cce4a9f36ca2d197a819cb48d834429e29fe5572c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802403"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a>Bilaga D – Dumpning och spårningsbuffert

Dumpning av spårningsbufferten som skapats av Azure RTOS ThreadX till en fil på värddatorn görs via kommandon och/eller verktyg som tillhandahålls av det specifika utvecklingsverktyg som används. Den här bilagan innehåller exempel på att dumpa en spårningsbuffert till en värdfil i några av de populäraste utvecklingsverktygen som används med ThreadX. 

## <a name="benchx-tools"></a>Brax-verktyg

Du kan enkelt ta spårningsbufferten till en värdfil med Verktyg för programflöde genom att välja knappen ***Lagra** minne till fil _ i vyn _*_Minne_**, enligt nedan:

![Skärmbild av minnesvyn i Verktyg för beredskap.](./media/user-guide/image642.jpg)

Nu anger du spårningsbuffertens adress, storlek, målfilnamn (inklusive sökväg) och väljer ***knappen*** Spara enligt nedan. Detta skapar den binära spårningsfilen för visning i TraceX.

![Skärmbild av dialogrutan För att spara verktyg för uppläckning.](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a>RealView-verktyg

Du kan enkelt ta spårningsbufferten till en värdfil med ARM RealView-verktygen genom att ange följande kommando i kommandotolken i RealView:

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

När det är klart ***innehåller filen trace_file.trx*** spårningsbufferten som finns med början vid 0x6860 och går upp till 0xE560. Den här filen är klar för visning av TraceX.

## <a name="iar-tools"></a>IAR-verktyg

Du kan enkelt ta spårningsbufferten till en värdfil med IAR-verktygen genom att helt enkelt högerklicka i minnesvyn och välja ***Minnessläcka...*** som du ser nedan.

![Skärmbild av alternativet Minnessläcka i IAR-verktygen.](./media/user-guide/image0_311.jpg)

Detta resulterar i dialogrutan ***Minnessläcka** _ som ska visas. Ange start- och slutadressen och spårningsfilens namn och välj _*_sedan knappen_*_ Spara. I exemplet nedan sparar IAR-verktygen den angivna spårningsbufferten i Intel HEX-poster i filen _*_trace_file.hex_**.

![Skärmbild av dialogrutan Minnessläcka i IAR-verktyg.](./media/user-guide/image648.jpg)

Nu har vi spårningsbufferten sparad ***i trace_file.hex-filen*** på värden och är redo att visas med TraceX.

## <a name="codewarrior-tools"></a>CodeWarrior Tools

Du kan enkelt ta spårningsbufferten till en värdfil med CodeWarrior-verktygen genom att ange kommandot ***save** _ i kommandofönstret. I följande exempel _ *_save_** förutsätter kommandot att spårningsbufferten börjar vid 0x102200 slutar vid 0x109F00:

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

Detta resulterar i att spårningsbufferten ***sparas i filen trace_file.trx*** på värden.

## <a name="mplab-tools"></a>MPLAB-verktyg

MPLAB kan skapa en TraceX-kompatibel spårningsfil via verktyget Exportera tabell, som tillåter export av alla minnesintervall till en värdfil. Om du vill använda det här verktyget för att skapa en spårningsfil för TraceX fortsätter du på följande sätt:

**Steg 1** Öppna ett minnesfönster genom att välja Visa -> minne.

![Skärmbild av valt minne på menyn Visa.](./media/user-guide/image0_316.jpg)

**Steg 2** Högerklicka i minnesvyn **för att** visa en lista med alternativ. Ange **Visningsformat -1 Byte för** att välja bytevisning..

![Skärmbild av minnesvyn med alternativet Visningsformat valt.](./media/user-guide/image650.png)

![Skärmbild av dialogrutan Gå till.](./media/user-guide/image651.jpg)

**Steg 3** Högerklicka igen i fönstret **Minnesvy** och välj **Gå till**, vilket öppnar en dialogruta där du kan ange adressen till händelsebufferten. Det här exemplet **_event_buffer_** visas.

![Skärmbild av minnesvyn med alternativet Gå till valt.](./media/user-guide/image0_312.jpg)

![Skärmbild av ett exempel som visar event_buffer visas.](./media/user-guide/image653.png)

**Steg 4** Då markeras innehållet på den första platsen i spårningsbufferten, som alltid är strängen BTXT....

![Skärmbild av den första platsen i spårningsbufferten.](./media/user-guide/image0_313.jpg)

**Steg 5** Högerklicka nu igen för att öppna alternativmenyn och välj **Exportera tabell.**

![Skärmbild av minnesvyn med alternativet Exportera tabell valt.](./media/user-guide/image0_314.jpg)

**Steg 6** Nu öppnas dialogrutan **Exportera** tabell, som du ser i bilden. Ange adressintervallet som ska exporteras. För en 8K-spårningsbuffert, vilket är fallet i det här exemplet, anger du intervallet 0xA00006AC till 0xA00026AC och anger ett namn för den värdfil som ska skapas (demo_threadx.trx i det här exemplet).

! [[Skärmbild av dialogrutan Exportera som.](./media/user-guide/image656.jpg)

**Steg 7** En fil **med demo_threadx.trx** skapas på värden och den här filen kan öppnas av TraceX.

## <a name="ghs-tools"></a>GHS-verktyg

Du kan enkelt ta spårningsbufferten till en värdfil med GHS-verktygen genom att ange följande kommando i kommandotolken i kommandofönstret för felsökning:

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

När det är klart **innehåller filen demo_threadx.trx** spårningsbufferten som finns i event_buffer med en storlek på 32 768 byte och är redo att visas av TraceX.

## <a name="renesas-hew"></a>Renesas HEW

Du kan enkelt ta spårningsbufferten till en värdfil med Renasas HEW-verktygen genom att följa de tre stegen (och understegen) nedan:

**Steg 1** Öppna fönstret Minne.

! [[Skärmbild av fönstret Minne.](./media/user-guide/image657.jpg)

**Steg 2** Placera markören i minnesfönstret och högerklicka.

![Skärmbild av fönstret Minne med alternativet Spara valt.](./media/user-guide/image0_315.jpg)

**Steg 3** Välj Spara och gör sedan följande i fönstret Spara minne som:

- Välj Filformat: Binär.
- Ange filnamn: Efter behov
- Ange Startadress: trace_buffer
- Ange slutadress: (trace_buffer+storlek)
- Ange åtkomststorlek: 1
- Klicka på Spara

![Skärmbild av dialogrutan Spara minne som.](./media/user-guide/image659.jpg)