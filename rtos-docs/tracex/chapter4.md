---
title: Kapitel 4 – prestanda analys för Azure återställnings tider-TraceX
description: I det här kapitlet beskrivs prestanda analys verktyget Azure återställnings tider TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 6cf1b5bd5349efd97c3afc8a9e7f57f477f06f8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827537"
---
# <a name="chapter-4---azure-rtos-tracex-performance-analysis"></a>Kapitel 4 – prestanda analys för Azure återställnings tider-TraceX

I det här kapitlet beskrivs prestanda analys verktyget Azure återställnings tider TraceX:

## <a name="performance-analysis"></a>Prestandaanalys

TraceX tillhandahåller inbyggd prestanda analys av spårningsfiler. Information som *körnings profil*, *populära tjänster*, *tråds tack användning* och olika *prestanda statistik,* inklusive FileX-och netx *-statistik,* är enkelt att komma åt. Den här informationen är tillgänglig via meny alternativet ***Visa*** . 


## <a name="execution-profile"></a>Körnings profil

Om du väljer knappen ***skapa körnings profil** _ eller _*_Visa körnings profil_*_ visas den TraceX körnings profilen för den aktuella inlästa spårnings filen. Körnings profilen som är kopplad till exempel demonstrations spårningen för ThreadX visas i _ * bild 19 * *.

![Skärm bild av körnings profilen som är kopplad till exempel demonstrations spårningen för ThreadX.](./media/user-guide/execution_profile.png)

**BILD 19**

Exemplet som visas i **bild 19** visar att nästan 45% av bearbetnings tiden är inuti **_tråd 2_*_ och nästan 51% av bearbetnings tiden är inuti _*_tråd 1_ .** detta är logiskt eftersom Mass spårningen visar dessa trådar som skickar och tar emot meddelanden. De återstående körnings kontexterna har bara en liten mängd körnings tid i det här exemplet.

## <a name="popular-services"></a>Populära tjänster

Om du väljer ***visa >populära tjänster** _ presenteras de populära tjänsterna i den just nu inlästa spårnings filen. Som standard visas den här informationen för hela systemet. De populära tjänsterna för vissa trådar är dock också tillgängliga. De populära tjänsterna i exempel ThreadX demonstrations spårning visas i _ * bild 20 * *.

![Skärm bild av populära tjänster i exemplet ThreadX demo trace.](./media/user-guide/popular_services.png)

**BILD 20**

Exemplet som visas i **bild 20** visar att **_tx_queue_send_*_ och _*_tx_queue_receive_** är de två populäraste tjänsterna i den här spårningen. Detta är konsekvent med beteendet för standard-ThreadX-demonstrationen som den här spårningen fångas från.

Du kan välja vissa trådar för den här analysen genom att använda List rutan längst upp i fönstret. **Bild 21** visar den här analysen för **_tråd 3_**.

![Skärm bild av analysen av TraceX populära tjänster.](./media/user-guide/popular_services_thread3.png)

**BILD 21**

## <a name="thread-stack-usage-analysis-for-thread-3"></a>Användning av tråds Tacken ![Analys av tråd 3.](./media/user-guide/screen_shot_17.png)

Om du väljer ***generera tråds tack användning** _ knappen eller _*_Visa > tråds tack användningen används_*_ stack användningen för varje tråd i spårnings filen. Detta åstadkoms av ThreadX, inklusive den aktuella tråds Tacken i många av spårnings posterna i filen. En stack användning på 100% anger att stacken har spillat och måste korrigeras i programmet. Om det inte finns någon tråd körning i den här spårnings filen visas stack användningen för den tråden vid 0%. Användningen av tråds Tacken i exempel ThreadX demonstrations spårning visas i _ * bild 22 * *.

![Skärm bild av TraceX Thread stack-användning.](./media/user-guide/thread_stack_usage.png)

**BILD 22**

Exemplet som visas i **bild 22** visar att de flesta trådar i den här spårningen har mellan 9% och 12% stack användning.

## <a name="performance-statistics"></a>Prestanda statistik

Om du väljer fliken ***generera prestanda statistik** _ eller _ *_Visa-> prestanda statistik_** visas prestanda statistiken för den aktuella inlästa spårnings filen. Som standard visas den här informationen för hela systemet. Prestanda statistiken är dock också tillgänglig för varje enskild tråd.

Prestanda statistiken för exempel ThreadX demonstrations spårning visas i **bild 23**.

![Skärm bild av TraceX prestanda statistik.](./media/user-guide/performance_statistics.png)

**FIGUR 23**

Exemplet som visas i **bild 23** visar att det fanns 18 kontext växlar i den här spårnings filen, samt fem tråds preemptions, 16 tråds pensioner, 19 trådar återupptas och tre avbrott. Det gick inte att hitta någon prioritets version i den här spårnings filen. Observera att det finns två kategorier av prioritets versioner, nämligen *deterministiska* och icke *deterministiska*. Den deterministiska prioritets versionen är en prioritets version där en tråd blockeras på en mutex som ägs av en tråd med lägre prioritet. En icke-deterministisk prioritets version är där en annan tråd med lägre prioritet körs under en deterministisk prioritets version. Senare kan orsaka oförutsedd tids beteende i programmet och bör undersökas noggrant.

## <a name="filex-statistics"></a>FileX-statistik

Om du väljer ***visa > FileX statistik** _ visas prestanda statistiken för den aktuella inlästa spårnings filen. Den här informationen visas för hela systemet, på alla öppna... /Media-objekt. Prestanda statistiken för exempel FileX demonstrations spårning visas i _ * bild 24 * *.

![Skärm bild av FileX-statistiken.](./media/user-guide/filex_statistics.png)

**BILD 24**

Exemplet som visas i **bild 27** visar att det var 19... /media öppnas, 19... /Media stängs, 19... /Media-tömningar, 18 katalog läsningar, 19 katalog skrivningar och 18 katalog-Cachemissar. Ytterligare information kan visas genom att rulla nedåt i statistik fönstret.

## <a name="netx-statistics"></a>NetX-statistik

Om du väljer ***Visa netx statistik** _ visas prestanda statistiken för den aktuella inlästa spårnings filen. Den här informationen visas för hela systemet. Prestanda statistiken för exempel NetX demonstrations spårning visas i _ * bild 25 * *.

![Skärm bild av NetX-statistiken.](./media/user-guide/netx_statistics.png)

**BILD 25**

Exemplet som visas i **bild 25** anger att det inte fanns några ARP-, ping-eller UDP-händelser, men det fanns 30 IP-paket skickade, 1 368 IP-byte skickade, 30 IP-paket togs emot och 1 360 IP-byte mottogs.

## <a name="trace-file-information"></a>Spårnings fil information

Om du väljer ***visa > spårnings fil information** _ visar viss grundläggande information om den öppna spårnings filen. Den här informationen omfattar filens byte ordning, storlek på tids källan, maximalt antal byte för varje objekt namn och bas adressen för alla spårnings fil pekare. _ *Bild 26** visar spårnings fil informationen för spårnings filen standard **_demo_threadx. trx_** .

![Skärm bild av fil informationen för TraceX.](./media/user-guide/trace_file_info.png)

**BILD 26**

## <a name="raw-trace-dump"></a>Rå stackdump

Om du väljer ***visa > rå spårning dump _ visas** en dialog ruta där du kan namnge filen som innehåller rå stackdump. När fil namnet och sökvägen har angetts skapar TraceX den obehandlade spårnings filen i text format och startar _*_notepad.exe_*_ för att visa den. _ *Bild 27** visar den obehandlade spårnings fils dumpningen för spårnings filen standard **_demo_threadx. trx_** .

![Skärm bild av rå spårnings dumpning.](./media/user-guide/raw_trace_dump.png)

**BILD 27**
