---
title: Kapitel 1 – Introduktion till GUIX
description: GUIX är en högpresterande realtidsimplementering av ett (GUI) som utformats exklusivt för inbäddade Azure RTOS ThreadX-baserade program.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e85aab43ba803212875f1fef3ba0bee8484c25b015e400d3b927d492177202b8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784128"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a>Kapitel 1 – Introduktion till Azure RTOS GUIX

Azure RTOS GUIX (GUIX) är en högpresterande realtidsimplementering av ett ramverk för grafiskt gränssnitt som utformats exklusivt för inbäddade ThreadX-baserade program. Det här kapitlet innehåller en introduktion till GUIX och en beskrivning av dess program och fördelar.

## <a name="guix-feature-overview"></a>Översikt över GUIX-funktioner

Till skillnad från många andra GUI-implementeringar är GUIX utformat för att vara flexibelt – enkelt att skala från små mikrostyrenhetsbaserade program till de som använder kraftfulla RISC- och DSP-processorer. Detta står i stark kontrast till den offentliga domänen eller andra kommersiella implementeringar som ursprungligen var avsedda för arbetsstationsmiljöer, men som sedan integrerades i inbäddade designer. En översikt över GUIX-funktioner följer:

- Lätt att använda med värdbaserat designverktyg GUIX Studio

- Win32 GUIX-körningsmiljö för fullständiga värdbaserade prototyper

- Stöder de flesta processorer som stöds av ThreadX

- Skrivs exklusivt i ANSI C

- Endiansk neutral

- Minsta, fast inbäddade guidning

- Körtid kan konfigureras, antal objekt, skärmstorlek osv.

- Lätt att skriva gränssnittet för visningsdrivrutiner

- Färg (upp till 32 bpp-färgdjup), grått och stöd för gråskala

- Stöd för flera språk via UTF8-strängkodning och strängresurser

- Standardfria teckensnitt och enkelt att lägga till nya teckensnitt

- Flera arbetsyteritningar som stöds, av olika storlekar

- Flera skärmar med olika storlekar och färgdjup stöds

- Stöd för skärmövergång (tona in, tona ut, svepa osv.)

- Stöd för pekskärm, gest och virtuellt tangentbord

- Bitmappkomprimering

- Alpha Blending-stöd

- Dither-stöd

- Stöd för antialias

- Hudning och teman

- Blandning av arbetsyta

- Fullständig fönsterhantering

  - Överordnad/underordnad relation

  - Dynamiskt skapande, borttagning, storleksändring, flytt
  - Separat händelsehantering och ritning 
  - Z-ordning
  - Urklipp och vyer

- Omfattande uppsättning widgetar

  - Olika knapptyper, skjutreglage och uppringningar

  - Rullgardinsmenyn
  
  - Prompt

  - Flerradstextvy
  
  - Textinmatning med en rad och flera linjer
  
  - Numeriska och textbaserade rullningshjul
  
  - Windows och rullningslister
  
  - Radiell förloppsstapel
  
  - Sprite

### <a name="ansi-c-source-code"></a>ANSI C-källkod

GUIX är helt skrivet i ANSI C och portabel direkt till praktiskt taget alla processorarkitekturer som har ett ANSI C-kompilator- och ThreadX-stöd. Även om GUIX är skrivet i ANSI C används en objektorienterad modell och arv.

### <a name="not-a-black-box"></a>Inte en svart låda

De flesta distributioner av GUIX innehåller den fullständiga C-källkoden. Detta eliminerar de "black-box"-problem som uppstår med många kommersiella GUI-implementeringar. Med hjälp av GUIX kan programutvecklare se exakt vad det grafiska användargränssnittet gör – det finns inga problem!

Källkoden möjliggör även programspecifika ändringar. Även om det inte rekommenderas är det verkligen fördelaktigt att ha möjlighet att ändra det grafiska användargränssnittet om det behövs. De här funktionerna är särskilt bekväma för utvecklare som är vana vid att arbeta med produkter i lokal eller offentlig domän. De förväntar sig att ha källkod och möjlighet att ändra den. GUIX är den ultimata GUI-programvaran för sådana utvecklare.

## <a name="embedded-gui-applications"></a>Inbäddade GUI-program

Inbäddade GUI-program är program som har ett användargränssnittskrav och körs på mikroprocessorer som är dolda i produkter som mobiltelefoner, kommunikationsutrustning, bilmotorer, skrivare för bärbara datorer, medicinska enheter och så vidare. Sådana program har nästan alltid vissa minnes- och prestandabegränsningar. En annan skillnad i inbäddat grafiskt användargränssnitt är att deras programvara och maskinvara har ett särskilt syfte.

### <a name="real-time-gui-software"></a>Realtids-GUI Software

I princip kallas GUI-programvara som måste utföra sin bearbetning inom en exakt tidsperiod för gui-programvara i realtid och när tidsbegränsningar tillämpas på *GUI-program* klassificeras de som realtidsprogram. Inbäddade GUI-program är nästan alltid realtid på grund av deras inbyggda interaktion med den externa världen.

## <a name="guix-benefits"></a>GUIX-fördelar

De främsta fördelarna med att använda GUIX för inbäddade program är höga prestanda, funktionsrika och mycket små minneskrav. GUIX är också helt integrerat med högpresterande, Azure RTOS ThreadX realtidsoperativsystemet.

### <a name="improved-responsiveness"></a>Förbättrad svarstid

Guix-produkten med höga prestanda gör att program kan svara snabbare än någonsin tidigare. Detta är särskilt viktigt för inbäddade program som antingen har en stor mängd visuell information eller strikta tidskrav för att visa sådan information.

### <a name="software-maintenance"></a>Programvaruunderhåll

Med GUIX kan utvecklare enkelt partitionera GUI-aspekterna av sina inbäddade program. Den här partitionering gör hela utvecklingsprocessen enkel och förbättrar avsevärt framtida programvaruunderhåll.

### <a name="increased-throughput"></a>Ökat dataflöde

GUIX ger det grafiska användargränssnittet med högsta möjliga prestanda, som överförs direkt till det inbäddade programmet. GUIX-program kan bearbeta gränssnittsinformation snabbare än icke-GUIX-program!

### <a name="processor-isolation"></a>Processorisolering

GUIX ger ett robust, processoroberoende gränssnitt mellan programmet och den underliggande processor- och visningsmaskinvaran. På så sätt kan utvecklare koncentrera sig på de avancerade aspekterna av användargränssnittet i stället för att lägga extra tid på att hantera problem med visningsmaskinvara.

### <a name="ease-of-use"></a>Användarvänlighet

GUIX är utformat med programutvecklaren i åtanke. GUIX-arkitekturen och gränssnittet för tjänstanrop är lätta att förstå. Därför kan GUIX-utvecklare snabbt använda sina avancerade funktioner.

### <a name="improve-time-to-market"></a>Förbättra tiden till marknad

De kraftfulla funktionerna i GUIX påskyndar programutvecklingsprocessen. GUIX abstraherar de flesta processor- och maskinvaruproblem, vilket tar bort dessa problem från en majoritet av implementeringen av användargränssnittet för programmet. Den här funktionen, tillsammans med den lättanvända och avancerade funktionsuppsättningen, resulterar i en snabbare tid till marknad!

### <a name="protecting-the-software-investment"></a>Skydda programvaruinvesteringen

GUIX skrivs exklusivt i ANSI C och är helt integrerat med Azure RTOS ThreadX-operativsystemet i realtid. Det innebär att GUIX-program är direkt portabla till alla ThreadX-processorer som stöds. Ännu bättre är att en helt ny processorarkitektur kan stödjas med ThreadX på bara några veckor. Därför säkerställer användningen av GUIX programmets migreringsväg och skyddar den ursprungliga utvecklingsinvesteringen.
