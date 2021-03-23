---
title: Kapitel 1 – Introduktion till GUIX
description: GUIX är en real tids implementering av en (GUI) som är utformad exklusivt för inbäddade Azure återställnings tider ThreadX-baserade program.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b90da988a03d59b1bca3f5584164d641bef96454
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827204"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a>Kapitel 1 – Introduktion till Azure återställnings tider GUIX

Azure återställnings tider GUIX (GUIX) är en real tids implementering i real tid av ett grafiskt gränssnitts ramverk som utformats exklusivt för inbäddade ThreadX-baserade program. Det här kapitlet innehåller en introduktion till GUIX och en beskrivning av dess program och fördelar.

## <a name="guix-feature-overview"></a>Översikt över GUIX-funktioner

Till skillnad från många andra GUI-implementeringar har GUIX utformats för att vara flexibelt, vilket enkelt kan skalas från små mikrokontrollantbaserade program till dem som använder kraftfulla RISC-och DSP-processorer. Detta är i skarpt kontrast i den offentliga domänen eller andra kommersiella implementeringar som ursprungligen är avsedda för arbets Stations miljöer, men som sedan är inkapslade i inbäddade modeller. En översikt över GUIX-funktionerna finns här:

- Lätt att använda med värdbaserade design verktyg GUIX Studio

- Win32-GUIX kör tids miljö för fullständig, värdbaserad prototyp

- Stöder de flesta processorer som stöds av ThreadX

- Skrivet exklusivt i ANSI C

- Endian-neutral

- Minsta, snabba inbäddade GUI

- Konfigurations Bart kör tid, antal objekt, skärm storlek osv.

- Lätt att skriva visnings driv rutins gränssnitt

- Färg (upp till 32-BPP färg djup), monokromt och stöd för gråskala

- Flerspråkig support via UTF8-sträng kodning och sträng resurser

- Standard teckensnitt som är standard och lätt att lägga till nya teckensnitt

- Flera arbets ytor som stöds av olika storlekar

- Flera skärmar av olika storlekar och färgdjup stöds

- Stöd för skärm över gång (tona in, tona ut, svep osv.)

- Stöd för pekskärm, gest och virtuellt tangent bord

- Bitmapps komprimering

- Stöd för alpha-mixer

- Stöd för rastrering

- Stöd för kant utjämning

- Skalning och teman

- Kombination av arbets yta

- Slutför fönster hantering

  - Överordnad/underordnad relation

  - Dynamisk generering, borttagning, storleks ändring, flyttning
  - Separat hantering och ritning av händelser 
  - Z-ordning
  - Urklipp och vyer

- Omfattande uppsättning widgetar

  - Olika knapp typer, skjutreglage och uppringningar

  - Nedrullningsbar listruta
  
  - Prompt

  - Vy med flera rader
  
  - Enkel text inspelning med flera rader
  
  - Tal-och text rullnings hjul
  
  - Fönster och rullnings lister
  
  - Förlopps indikator för radiell
  
  - Sprit

### <a name="ansi-c-source-code"></a>ANSI C-källkod

GUIX skrivs helt i ANSI C och är direkt portabel till praktiskt taget vilken processor arkitektur som helst som har stöd för ANSI C-kompilator och ThreadX. Även om det är skrivet i ANSI C, använder GUIX en objektorienterad modell och arv.

### <a name="not-a-black-box"></a>Inte en svart ruta

De flesta distributioner av GUIX innehåller den fullständiga C-källkoden. Detta eliminerar "svarta box"-problem som uppstår med många kommersiella GUI-implementeringar. Genom att använda GUIX kan programutvecklare se exakt vad användar gränssnittet gör – det finns inga Mysteries!

Med käll koden kan du också göra programspecifika ändringar. Även om det inte rekommenderas, är det verkligen fördelaktigt att ha möjlighet att ändra GUI om det behövs. Dessa funktioner är särskilt praktiska för utvecklare som är vana vid att arbeta med interna eller offentliga domän produkter. De förväntar sig ha källkod och möjlighet att ändra den. GUIX är den ultimata GUI-programvaran för sådana utvecklare.

## <a name="embedded-gui-applications"></a>Inbäddade GUI-program

Inbäddade GUI-program är program som har ett användar gränssnitts krav och körs på mikroprocessorer som är dolda i produkter som mobil telefoner, kommunikations utrustning, fordons motorer, laser skrivare, medicinska enheter och så vidare. Sådana program har nästan alltid vissa minnes-och prestanda begränsningar. En annan skillnad på inbäddat GUI är att deras program vara och maskin vara har ett dedikerat syfte.

### <a name="real-time-gui-software"></a>GUI-programvara i real tid

I princip kallas GUI-programvara som måste utföra bearbetningen inom en exakt tids period. i *real tid kallas GUI-programvara i real tid* och när tids begränsningar införs i GUI-program klassificeras de som real tids program. Inbäddade GUI-program är nästan alltid real tids på grund av deras inbyggda interaktion med den externa världen.

## <a name="guix-benefits"></a>GUIX-förmåner

De främsta fördelarna med att använda GUIX för inbäddade program är högpresterande, funktions rika och mycket små minnes krav. GUIX är också helt integrerat med högpresterande, multitasking Azure återställnings tider ThreadXs operativ system i real tid.

### <a name="improved-responsiveness"></a>Förbättrad svars tid

Med den GUIX produkten med höga prestanda kan program svara snabbare än någonsin tidigare. Detta är särskilt viktigt för inbäddade program som antingen har en betydande mängd visuell information eller strikt tids krav för att visa sådan information.

### <a name="software-maintenance"></a>Program varu underhåll

Med hjälp av GUIX kan utvecklare enkelt partitionera GUI-aspekterna av sina inbäddade program. Den här partitionerings processen gör hela utvecklings processen enkel och förbättrar det framtida program varu underhållet.

### <a name="increased-throughput"></a>Ökat data flöde

GUIX tillhandahåller det högsta tillgängliga användar gränssnittet, som direkt överför till det inbäddade programmet. GUIX-program kan bearbeta användar gränssnitts information snabbare än icke-GUIX program!

### <a name="processor-isolation"></a>Processor isolering

GUIX tillhandahåller ett robust, processor oberoende gränssnitt mellan programmet och den underliggande processor-och visnings maskin varan. På så sätt kan utvecklare koncentrera sig på högnivå aspekterna i användar gränssnittet i stället för att ägna extra tid åt att hantera maskin varu problem.

### <a name="ease-of-use"></a>Lätt att använda

GUIX är utformad med program utvecklaren i åtanke. GUIX-arkitekturen och tjänst anrops gränssnittet är lätta att förstå. Därför kan GUIX-utvecklare snabbt använda sina avancerade funktioner.

### <a name="improve-time-to-market"></a>Förbättra tiden till marknaden

De kraftfulla funktionerna i GUIX påskyndar program utvecklings processen. GUIX sammanfattar de flesta processor problem och visar maskin varu problem och tar därmed bort dessa problem från en majoritet av program användar gränssnittets implementering. Den här funktionen, tillsammans med funktionen för enkel användning och avancerad funktion, resulterar i en snabbare tid till marknaden!

### <a name="protecting-the-software-investment"></a>Skydda program investeringen

GUIX skrivs exklusivt i ANSI C och är helt integrerad med Azure återställnings tider-ThreadX operativ systemet i real tid. Det innebär att GUIX-program är direkt bärbara till alla ThreadX-processorer som stöds. Ännu bättre kan en helt ny processor arkitektur stödjas med ThreadX på bara några veckor. Det innebär att du kan använda GUIX för att säkerställa programmets migrations Sök väg och skyddar den ursprungliga utvecklings investeringen.
