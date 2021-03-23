---
title: Genererad kod i GUIX Studio
description: När du är klar med att redigera dina skärmar och resurser skapar GUIX Studio en uppsättning utdatafiler som kan införlivas i det inbäddade programmet.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: f8868ec770aa8f7f35d2866b99e3eb8f501281a8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827129"
---
# <a name="chapter-6-guix-studio-generated-code"></a>Kapitel 6: genererad kod i GUIX Studio

När du är klar med att redigera dina skärmar och resurser skapar GUIX Studio en uppsättning utdatafiler som kan införlivas i det inbäddade programmet. Utdatafilerna genereras genom att välja ***generera resursfiler** _ och _ *_generera specifikationer_** från meny alternativet projekt. GUIX för "c"-språket som genereras av Studio är avsedda att kompileras och länkas till käll koden för det inbäddade programmet. Om en resurs fil för binärformat skapas, ska den här filen programmeras i ett beständigt lagrings utrymme på målet och GUIX API-funktionen gx_binres_theme_install ska användas för att installera de binära resurserna vid körning.

Användarens inbäddade program kod gör referenser till den kod som genereras av GUIX Studio. Dessutom förväntas den genererade koden i GUIX Studio att alla funktioner för anpassad widget, händelse hantering och allokering av minne som anges i projektet definieras i användarens inbäddade program kod. Om de inte är det visas länk felen när du skapar programmet.

> [!NOTE]
> Användaren bör aldrig behöva ändra koden som genererats av GUIX Studio och bör motstå detta. Alla ändringar i gränssnittet bör göras i det associerade GUIX Studio-projektet. Detta håller projektet synkroniserat med det inbäddade programmet.

## <a name="generating-resource-files"></a>Genererar resursfiler

Resursfiler som genereras av GUIX Studio innehåller förinställda data strukturer som definierar alla GUIX Studio-resurser (färger, teckensnitt, pixelmaps och strängar), vilket i praktiken är alla de resurser som definierats i projektets ***vyn resurser*** . Dessa resursfiler kan skapas i käll kod eller binära formulär.

Som standard har två filer skapats, en fil är en standard-C-källkod och den andra är en C-huvudfil som tillhandahåller externa referenser och konstanter som krävs för att program koden ska kunna komma åt de GUIX-resurser som definierats i projektet. Fil namnen är av typen:

**{*Project-Name*} _resources. h**

**{*Project-Name*} _resources. c**

Till exempel är resursfiler som skapats för det "***enkla***" GUIX Studio-projektet:

**simple_resources. h**

**simple_resources. c**

Skapa resursfiler genom att välja ***skapa resursfiler** _ alternativ i meny alternativet _*_projekt_*_ . Målet för resursfiler anges i dialog rutan _*_Konfigurera projekt_*_ som går att komma åt via alternativet _*_Konfigurera projekt/Visa_*_ på meny alternativet _ *_Konfigurera_**.

För Pixelmap-och teckensnitts resurser kan du ange ett anpassat utdata-filnamn för varje Pixelmap och teckensnitt i de tillhör ande dialog rutorna för redigering av resurser. Med den här funktionen kan du placera mycket stora resurser i distinkta filer i stället för att lägga till alla resurser i en gemensam utdatafil. Om du inte anger ett åsidosatt fil namn för en teckensnitts-eller Pixelmap-resurs, skrivs dessa resurser till den gemensamma resurs filen.

Om du föredrar att använda binära resurser kan du ange antingen RAW-eller standard s-Record-utdataformat. Binära resurser kompileras eller länkas inte till program koden, utan läses i stället in vid körning med hjälp av API: et gx_binres_them_load (). Den här API-tjänsten skapar resurs tabeller som pekar på dina resurser som lagras i beständigt minne. Du kan sedan installera dessa resurser med en viss bildskärm med hjälp av gx_display_theme_install ();

## <a name="generating-specification-code"></a>Genererar Specifikations kod

De Specifikations filer som genereras av GUIX Studio innehåller all C-kod för att skapa gränssnittet som är utformat i GUIX Studio. Den här koden refererar också till de resursfiler som genereras för det här projektet. Användarens program kod kommer att anropa den här koden för att skapa de GRÄNSSNITTs objekt som definierats i projektet. Dessutom innehåller användarens program kod all anpassad widget, händelse hantering och funktioner för minnesallokering som anges i projektet. Som standard har två filer skapats, en fil är en standard-C-källkod och den andra är en C-huvudfil som tillhandahåller externa referenser och konstanter som krävs för att program koden ska få åtkomst till GUIX Studio-specifikationerna. Fil namnen är av typen:

**{*Project-Name*} _specifications. h**

**{*Project-Name*} _specifications. c**

Till exempel är de Specification-filer som skapats för det "***enkla***" GUIX Studio-projektet:

**simple_specifications. h**

**simple_specifications. c**

Du gör det genom att välja ***skapa Specification-filer** _ i meny alternativet för _*_projektet_*_ . Målet för Specification-filerna anges i dialog rutan _*_Konfigurera projekt_*_ som går att komma åt via alternativet _*_Konfigurera projekt/Visa_*_ på meny alternativet _ *_Konfigurera_**.

## <a name="integrating-with-user-code"></a>Integrera med användar kod

Att integrera de resurs-och Specifikations filer som genereras av GUIX Studio är enkelt, Följ bara dessa steg:

1. Kopiera eller gör resurs-och Specifikations filerna tillgängliga via Sök vägs inställningar till den inbäddade build-miljön
2. Lägg till alla resurs-och Specifikations filer till inbäddade IDE-projekt eller make
3. Se till att programmets inbäddade kod anropar de nödvändiga funktionerna för att initiera och skapa användar gränssnittet som finns i resurs-och Specifikations filen
4. Se till att programmets inbäddade kod innehåller alla nödvändiga funktioner för anpassad widget, händelse hantering och minnesallokering
5. Bygg programmet (kompilera och länka)
6. Kör programmet!