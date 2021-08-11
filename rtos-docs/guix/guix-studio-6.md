---
title: GUIX Studio-genererad kod
description: När du är klar med redigeringen av skärmar och resurser skapar GUIX Studio en uppsättning utdatafiler som kan införlivas i ditt inbäddade program.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 78b1ec1eea3ec2fcae48c64ad15931f44f34538c876dc8a267c2b1a84234320a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785710"
---
# <a name="chapter-6-guix-studio-generated-code"></a>Kapitel 6: GUIX Studio-genererad kod

När du är klar med redigeringen av skärmar och resurser skapar GUIX Studio en uppsättning utdatafiler som kan införlivas i ditt inbäddade program. Utdatafilerna genereras genom att välja ***Generera resursfiler** _ och _ *_Generera specifikationer_** från Project menyalternativet. C-språkets källkodsfiler som genereras av GUIX Studio är avsedda att kompileras och länkas till den inbäddade programkällkoden. Om en resursfil för binärt format skapas ska den här filen programmeras till ett icke-beständigt lagringsområde på målet och GUIX API-funktionen gx_binres_theme_install ska användas för att installera de binära resurserna vid körning.

Användarens inbäddade programkod refererar till den kod som genereras av GUIX Studio. Dessutom förväntar sig DEN GUIX Studio-genererade koden att alla funktioner för ritning av anpassade widgetar, händelsehantering och minnesallokering som anges i projektet definieras i användarens inbäddade programkod. Om de inte är det visas länkfel när du skapar programmet.

> [!NOTE]
> Användaren bör aldrig behöva ändra koden som genereras av GUIX Studio och bör stå emot att göra det. Alla gränssnittsändringar bör göras i det associerade GUIX Studio-projektet. Detta håller projektet synkroniserat med det inbäddade programmet.

## <a name="generating-resource-files"></a>Generera resursfiler

Resursfiler som genereras av GUIX Studio innehåller förinställda datastrukturer som definierar alla GUIX Studio-resurser (färger, teckensnitt, pixelkartor och strängar), vilket i praktiken är alla resurser som definieras ***i Vyn Resurser*** i projektet. Dessa resursfiler kan genereras i källkod eller binära formulär.

Som standard genereras två filer, en fil är en C-standardkällkodfil och den andra är en C-huvudfil som innehåller externa referenser och konstanter som krävs för att programkoden ska få åtkomst till DE GUIX-resurser som definierats i projektet. Filnamnen har följande format:

**{*project-name*}_resources.h**

**{*project-name*}_resources.c**

Resursfilerna som skapats för det ***"*** enkla " GUIX Studio-projektet är till exempel:

**simple_resources.h**

**simple_resources.c**

Du genererar resursfilerna genom att välja alternativet ***Generera** resursfiler _ _*_i Project_*_ menyalternativet. Målet för resursfilerna anges i _*_dialogrutan Konfigurera Project_*_ som är tillgänglig via alternativet Konfigurera _*_Project/visar_*_ i menyalternativet _ *_Konfigurera_** .

För pixelkarta- och teckensnittsresurser kan du ange ett anpassat utdatafilnamn för varje pixelkarta och teckensnitt i de associerade dialogrutorna för resursredigering. Med den här funktionen kan du placera mycket stora resurser i distinkta filer i stället för att placera alla resurser i en gemensam utdatafil. Om du inte anger ett åsidosättt filnamn för en teckensnitts- eller pixelkarta-resurs skrivs dessa resurser till den gemensamma resursfilen.

Om du föredrar att använda binära resurser kan du ange rå- eller standardutdataformat för s-post. Binära resurser kompileras inte eller länkas inte med programkoden, utan läses i stället in vid körning med hjälp av API:gx_binres_them_load(). Den här API-tjänsten skapar resurstabeller som pekar på dina resurser som lagras i beständigt minne. Du kan sedan installera dessa resurser med en viss visning med hjälp av gx_display_theme_install();

## <a name="generating-specification-code"></a>Generera specifikationskod

Specifikationsfilerna som genereras av GUIX Studio innehåller all C-kod för att skapa användargränssnittet som utformats i GUIX Studio. Den här koden refererar även till resursfilerna som genererats för projektet. Användarens programkod gör anrop till den här koden för att skapa ui-objekt som definierats i projektet. Dessutom innehåller användarens programkod alla anpassade widgetritningsfunktioner, händelsehantering och minnesallokeringsfunktioner som anges i projektet. Som standard genereras två filer, en fil är en C-standardkällkodfil och den andra är en C-huvudfil som innehåller externa referenser och konstanter som krävs för att programkoden ska få åtkomst till GUIX Studio-specifikationerna. Filnamnen har följande format:

**{*project-name*}_specifications.h**

**{*project-name*}_specifications.c**

Till exempel är de specifikationsfiler som skapats för det "***enkla***" GUIX Studio-projektet:

**simple_specifications.h**

**simple_specifications.c**

Du genererar specifikationsfilerna genom att välja alternativet ***Generera** specifikationsfiler _ _*_i Project_*_ menyalternativet. Målet för specifikationsfilerna anges i _*_dialogrutan Konfigurera Project_*_ som är tillgänglig via alternativet Konfigurera _*_Project/visar_*_ i menyalternativet _ *_Konfigurera_** .

## <a name="integrating-with-user-code"></a>Integrera med användarkod

Det är enkelt att integrera resurs- och specifikationsfilerna som genereras av GUIX Studio. Följ bara dessa steg:

1. Kopiera eller gör filerna Resurs och Specifikation tillgängliga via sökvägsinställningar till den inbäddade byggmiljön
2. Lägga till alla resurs- och specifikationsfiler i inbäddat IDE-projekt eller makefile
3. Se till att programmets inbäddade kod anropar de nödvändiga funktionerna för att initiera och skapa användargränssnittet som finns i resurs- och specifikationsfilerna
4. Se till att programmets inbäddade kod innehåller alla nödvändiga anpassade widgetritningsfunktioner, händelsehantering och minnesallokeringsfunktioner
5. Skapa programmet (kompilera och länka)
6. Kör programmet!