---
title: Kapitel 4 – Azure RTOS TraceX-prestandaanalys
description: I det här kapitlet beskrivs Azure RTOS traceX-prestandaanalysverktyget.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 719f27ef54091e2db9eefa982ce0c27561079b5b3a254d3fd09cc46d8f66f252
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788729"
---
# <a name="chapter-4---azure-rtos-tracex-performance-analysis"></a>Kapitel 4 – Azure RTOS TraceX-prestandaanalys

I det här kapitlet beskrivs Azure RTOS TraceX-prestandaanalysverktyget:

## <a name="performance-analysis"></a>Prestandaanalys

TraceX tillhandahåller inbyggd prestandaanalys av spårningsfiler. Information som *körningsprofilen,* *populära* tjänster, användning av *trådstackar* och olika *prestandastatistik,* inklusive FileX- och NetX-statistik, är tillgängliga. Den här informationen är tillgänglig via ***menyalternativet*** Visa. 


## <a name="execution-profile"></a>Körningsprofil

Om du väljer knappen ***Generera körningsprofil** _ eller _*_Visa -Körningsprofil_*_ visas TraceX-körningsprofilen för den aktuella inlästa spårningsfilen. Körningsprofilen som är associerad med ThreadX-exempeldemonstrationspårningen visas i _*Bild 19**.

![Skärmbild av körningsprofilen som är associerad med ThreadX-exempeldemonstrationsspårningen.](./media/user-guide/execution_profile.png)

**BILD 19**

Exemplet som visas i bild **19** visar att nästan 45 % av bearbetningstiden ligger inuti tråd **_2_ _ och *nästan 51 %* av bearbetningstiden är inuti _ tråd _1_** Det här är logiskt eftersom merparten av spårningen visar att dessa trådar skickar och tar emot meddelanden. De återstående körningskontexterna har bara en liten mängd körningstid i det här exemplet.

## <a name="popular-services"></a>Populära tjänster

Om du **väljer * Visa ->Populära tjänster** _ visas de populära tjänsterna i den inlästa spårningsfilen. Som standard visas den här informationen för hela systemet. De populära tjänsterna för specifika trådar är dock också tillgängliga. De populära tjänsterna i ThreadX-exempeldemonstrationspårningen visas i _*Bild 20**.

![Skärmbild av de populära tjänsterna i ThreadX-exempeldemonstrationsspårningen.](./media/user-guide/popular_services.png)

**BILD 20**

Exemplet som visas i **bild 20** anger **_att tx_queue_send_ _ och *_*_tx_queue_receive_** är de två mest populära tjänsterna i den här spårningen. Detta är konsekvent med beteendet för ThreadX-standarddemonstrationen som spårningen har avbildats från.

Specifika trådar kan väljas för den här analysen med hjälp av listrutan för val längst upp i det här fönstret. **Bild 21** visar den här analysen för **_tråd 3_**.

![Skärmbild av analysen för populära TraceX-tjänster.](./media/user-guide/popular_services_thread3.png)

**BILD 21**

## <a name="thread-stack-usage-analysis-for-thread-3"></a>Användning av trådstack ![Analys för tråd 3.](./media/user-guide/screen_shot_17.png)

Om du väljer knappen ***Generate Thread Stack Usage** _ (Generera användning av trådstack) eller View -> Thread Stack Usage (Visa _*_-> Thread Stack-användning)_*_ visas stackanvändningen för varje tråd i spårningsfilen. Detta åstadkoms av ThreadX, inklusive den aktuella trådstack-pekaren i många av spårningsposterna i filen. En stackanvändning på 100 % anger att stacken har spillts över och måste korrigeras i programmet. Om det inte finns någon trådkörning i den här spårningsfilen visas stackanvändningen för den tråden på 0 %. Trådstackanvändningen i ThreadX-exempeldemonstrationsspårningen visas i _*Bild 22**.

![Skärmbild av TraceX-trådstackanvändningen.](./media/user-guide/thread_stack_usage.png)

**BILD 22**

Exemplet som visas i **bild 22 visar** att de flesta trådar i den här spårningen har mellan 9 % och 12 % stackanvändning.

## <a name="performance-statistics"></a>Prestandastatistik

Om du väljer knappen ***Generera prestandastatistik** _ eller _ *_Visa -> Prestandastatistik_** visas prestandastatistiken för den inlästa spårningsfilen. Som standard visas den här informationen för hela systemet. Prestandastatistiken är dock också tillgänglig för varje specifik tråd.

Prestandastatistiken för ThreadX-exempeldemonstrationspårningen visas i **bild 23**.

![Skärmbild av TraceX-prestandastatistiken.](./media/user-guide/performance_statistics.png)

**BILD 23**

Exemplet som visas i bild **23** visar att det fanns 18 kontextväxlar i den här spårningsfilen, samt fem trådavstängningar, 16 trådavstängningar, 19 trådupptdragningar och tre avbrott. Inga prioritetsinversioner hittades i den här spårningsfilen. Observera att det finns två kategorier av prioritetsinversioner, *nämligen deterministisk* och *icke-deterministisk*. Deterministiska prioritetsinversioner är prioritetsinversion där en tråd blockeras på en mutex som ägs av en tråd med lägre prioritet. En icke-deterministisk prioritetsinversion är när en annan tråd med lägre prioritet körs under en deterministisk prioritetsinversion. Senare kan orsaka oförutsedda timing-beteenden i programmet och bör undersökas noggrant.

## <a name="filex-statistics"></a>FileX-statistik

Om du **väljer * Visa -> FileX Statistics** _ visas FileX-prestandastatistiken för den inlästa spårningsfilen. Den här informationen visas för hela systemet på alla öppna .. /media objects. Prestandastatistiken för FileX-exempeldemonstrationspårningen visas i _*Bild 24**.

![Skärmbild av FileX-statistik.](./media/user-guide/filex_statistics.png)

**BILD 24**

Exemplet som visas på **bild 27 visar** att det fanns 19 .. /media öppnas, 19 .. /media closes, 19 .. /media flushes, 18 directory reads, 19 directory writes och 18 directory cache misses. Ytterligare information kan visas genom att rulla nedåt i statistikfönstret.

## <a name="netx-statistics"></a>NetX-statistik

Om du **väljer * Visa -NetX Statistics** _ visas NetX-prestandastatistiken för den aktuella inlästa spårningsfilen. Den här informationen visas för hela systemet. Prestandastatistiken för NetX-exempeldemonstrationspårningen visas i _*Bild 25**.

![Skärmbild av NetX-statistik.](./media/user-guide/netx_statistics.png)

**BILD 25**

Exemplet som visas i bild **25** visar att det inte fanns några ARP-, Ping- eller UDP-händelser, men 30 IP-paket skickades, 1 368 IP-byte skickades, 30 IP-paket togs emot och 1 360 IP-byte togs emot.

## <a name="trace-file-information"></a>Information om spårningsfil

Om du **väljer * Visa -> Information om spårningsfil** _ visas grundläggande information om den öppnade spårningsfilen. Den här informationen omfattar byteordningen för filen, tidskällans storlek, maximalt antal byte för varje objektnamn och basadressen för alla spårningsfilspekare. _ *Bild 26** visar spårningsfilens information för spårningsfilen **_demo_threadx.trx._**

![Skärmbild av TraceX-filinformationen.](./media/user-guide/trace_file_info.png)

**BILD 26**

## <a name="raw-trace-dump"></a>Rå spårningsdump

Om du väljer *** Visa -> Raw Trace Dump** _ visas en dialogruta för att namnge filen som innehåller den råa spårningsdumpen. När filnamnet och sökvägen har _*_angetts_*_ skapar TraceX den råa spårningsfilen i textformat och startarnotepad.exeatt visa den. _ *Bild 27** visar den råa spårningsfildumpen **_för standardspårningsfilen demo_threadx.trx._**

![Skärmbild av den råa spårningsdumpen.](./media/user-guide/raw_trace_dump.png)

**BILD 27**
