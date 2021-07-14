---
title: Förstå Azure RTOS GUIX och Azure RTOS GUIX Studio
description: Azure RTOS GUIX är ett paket av professionell kvalitet som skapats för att uppfylla behoven hos utvecklare av inbäddade system.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a6ac2c7a76893d516b9beae9b893c9764de60ba
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754938"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a>Översikt över Azure RTOS GUIX och Azure RTOS GUIX Studio

Azure GUIX embedded GUI är Microsofts avancerade GUI-lösning i branschklass som utformats specifikt för djupt inbäddade, realtids- och IoT-program. Microsoft tillhandahåller också ett komplett WYSIWYG-skrivbordsdesignverktyg med namnet Azure RTOS GUIX Studio, som gör att utvecklare kan utforma sitt GUI på skrivbordet och generera Azure RTOS GUIX-inbäddad GUI-kod som sedan kan exporteras till målet. Azure RTOS GUIX är helt integrerat med Azure RTOS ThreadX RTOS och är tillgängligt för många av de processorer som stöds av Azure RTOS ThreadX. Allt detta i kombination med ett mycket litet fotavtryck, snabb körning och överlägsen användarvänlighet gör Azure RTOS GUIX till det perfekta valet för de mest krävande inbäddade IoT-programmen som kräver ett användargränssnitt. 

## <a name="azure-rtos-guix-api"></a>Azure RTOS GUIX API

### <a name="powerful-apis"></a>Kraftfulla API:er

* Fullständigt stöd för direkt arbetsyteritning vid behov
* Enkelt att interagera med Azure RTOS GUIX Studio-genererad kod
* API:er för linje, rektangel, polygon osv.
* API:er för cirkel, båge, cirkel, ellips osv.
* API:er för textritning och placering
* Antialias, strukturfyllningar och heldragna fyllningar
* API:er för att skapa och ändra skärmar och widgetar

### <a name="azure-rtos-guix-studio-generated-files"></a>Azure RTOS GUIX Studio-genererade filer

* Automatiskt genererade ANSI C-källfiler
* Isolerar programprogramvara från layoutinformation
* Innehåller teckensnitt och bilder som krävs av ui-designen
* Genererade filer som kompilerats med programkod
* Skärmlayouten kan uppdateras utan att programlogiken påverkas
* Resurs-ID:er skapar språk- och temaoberoende
* Anpassade funktioner för ritning och händelsebearbetning som tillhandahålls av användaren

### <a name="widget-library"></a>Widgetbibliotek

* Fördefinierad men anpassningsbar uppsättning gemensamma gränssnittselement
* Extremt liten, kompakt och effektiv
* Biblioteket innehåller knapp, mätare, lista, fönster, rullningsreglage, skjutreglage, förloppsfält, prompt och mycket mer
* Helt anpassningsbar ritning och utseende
* Helt anpassningsbar åtgärd och händelsehantering
* Endast de widgetar som används är länkade med programprogramvaran

### <a name="math-and-utilities"></a>Matematik och hjälpmedel

* Funktioner för sin, cos, arcsin, arccos, tangens, kvadratrot
* Funktioner för att manipulera skärmregioner
* Systemkonfiguration och start
* Minnespoolsdefinition (valfritt)
* Timerhantering
* Animeringshantering
* Underhåll av en dirty-lista

### <a name="image-processing"></a>Bearbetning av avbildning

* Funktioner för körningsavkodning av jpeg- och png-bilder
* Använda dithering och konvertering av färgutrymme
* Bildrotation
* Avbildningsskalning
* Bildblandning

### <a name="event-processing"></a>Händelsebearbetning

* Pausar automatiskt Azure RTOS GUIX-tråd vid inaktivitet
* Händelsedriven programmeringsmodell som är populär i UI-design
* Isolerar indatadrivrutiner från Azure RTOS GUIX-ritningstråd
* Funktioner för att skicka och ta emot händelser
* Fördefinierade händelsetyper för alla typer Azure RTOS GUIX-widget
* Användardefinierade anpassade händelser som stöds

### <a name="canvas-processing"></a>Bearbetning av arbetsyta

* Cklippning och Z-orderunderhåll
* Isolerar widgetbibliotek från maskinvaruinformation
* Isolerar program från maskinvaruinformation
* Automatisk bakgrundsuppdatering av dirty areas
* Flera arbetsyta med skiktning och blandning som stöds
* Kan anropas direkt av programprogramvaran

### <a name="input-device-drivers"></a>Inmatning av enhetsdrivrutiner

* Maskinvaruspecifikt stöd, Azure RTOS GUIX och program som isolerats från maskinvaruinformation
* Stöd för Resistive Touch, Cap Touch och keypad
* Indatahändelser som skickas Azure RTOS GUIX-händelsekö

### <a name="display-drivers"></a>Visa drivrutiner

* Maskinvaruspecifikt stöd
* Allmänna drivrutiner för alla färgdjup och format
* Anpassad för att använda tillgängliga grafikacceleratorer

### <a name="target-hardware"></a>Målmaskinvara

* Nästan vilken maskinvara som helst som kan grafisk utdata är kompatibel med GUIX
* Flera fysiska skärmar stöds
* Minimala krav för RAM och Flash

## <a name="create-elegant-user-interfaces"></a>Skapa elegant användargränssnitt

Azure RTOS GUIX och Azure RTOS GUIX Studio innehåller alla funktioner som behövs för att skapa unikt elegant användargränssnitt. STANDARD-AZURE RTOS GUIX-paketet innehåller olika exempelanvändargränssnitt, inklusive en referens för medicinska enheter, en referens för smart klocka, en referens för hemautomatisering, en referens för industriell kontroll, en fordonsreferens och olika exempel på personer och animering. Klicka på de referensexempel som visas nedan.

### <a name="home-automation"></a>Hemautomatisering

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a>Medicinsk

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a>Konsument

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a>Vitvaror

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a>Fordon

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a>Industriella

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

Varje Azure RTOS GUIX-referens har ett Azure RTOS GUIX Studio-projekt som definierar alla grafiska element i referensdesignen. Det är enkelt att ändra en referensdesign. Öppna bara motsvarande AZURE RTOS GUIX-projekt, gör önskade ändringar, spara projektet och välj sedan *Project*.

Generera Alla utdatafiler för att generera C-koden för Azure RTOS GUIX. Återskapa sedan målprogrammet och kör för att observera den ändrade referensdesignen.

### <a name="guix-memory-footprint"></a>GUIX-minnesfotavtryck

Azure RTOS GUIX har ett mycket litet minimalt fotavtryck på 13,2 kB FLASH och 4 kB RAM för grundläggande stöd, inte det minne som krävs för en arbetsyta.

För en visning med intern GRAM och självuppdateringsteknik krävs inget arbetsyteminne. Men för att förbättra ritningsprestanda eller för en visningskonfiguration som inte använder GRAM lokalt på skärmen definieras ett arbetsyteminne av programmet.

Minneskrav för arbetsyta är en funktion av arbetsytans storlek samt färgdjupet och definieras av formeln:

<i>RAM för arbetsyta (byte) = (x * y * (bpp/8))</i>

Där "x" och "y" är arbetsytans dimensioner (visning).

De flesta program använder också grafiska resurser, som inte ingår i Azure RTOS krav för GUIX-bibliotekslagring. Dessa resurser omfattar teckensnitt, grafiska ikoner (pixelkartor) och statiska strängar. Dessa data kan lagras i avsnittet const memory (t.ex. FLASH).

Storleken på det här minnesområdet beror på ett antal faktorer, inklusive antalet och storleken på de unika teckensnitt som används, antalet och storleken på de grafiska ikoner som används, utdatafärgformatet och huruvida varje resurs använder komprimerade data, eftersom Azure RTOS GUIX stöder RLE-komprimering av både teckensnitts- och pixelkarta-data. Lagringskraven för varje resurs visas i Azure RTOS GUIX Studio-programmet, så att användaren kan spåra och övervaka mängden flashminne som kommer att förbrukas av programresurserna.

Precis Azure RTOS ThreadX skalas storleken på Azure RTOS GUIX automatiskt baserat på de tjänster som faktiskt används av programmet. Detta eliminerar praktiskt taget behovet av komplicerad konfiguration och byggparametrar, vilket gör det enklare för utvecklaren.

#### <a name="simple-easy-to-use"></a>Enkelt och lätt att använda

Azure RTOS GUIX är mycket enkelt att använda och Azure RTOS GUIX Studio gör det ännu enklare för utvecklare att designa visuellt på skrivbordet och generera C-kod som körs på det faktiska målet. Program kan sedan lägga till egna anpassade händelsehanterings- och ritningsfunktioner för att slutföra det grafiska användargränssnittet.

Det är enkelt Azure RTOS GUIX-API:et. DET Azure RTOS GUIX-API:et är både intuitivt och mycket funktionellt. API-namnen består av verkliga ord och inte "alfabetet" och/eller de mycket förkortade namn som är så vanliga i andra filsystemprodukter. Alla Azure RTOS GUIX-API:er *har en gx_* och följer en namngivningskonvention med substantivverb. Dessutom finns det en funktionell konsekvens i hela API:et. Till exempel har alla API:er som initierar ett widgetkontrollblock namnet widget_type _create, och funktionsparametrarna create för varje widgettyp definieras alltid i &lt; &gt; samma ordning.

### <a name="comprehensive-set-of-built-in-widgets"></a>Omfattande uppsättning inbyggda widgetar

* Azure RTOS GUIX innehåller en omfattande uppsättning inbyggda widgetar, inklusive:
* Överensstämmelsemeny
* Button (Knapp)
* Checkbox
* Cirkelmätare
* Rullgardinsmenyn
* Vågrät lista
* Vågrätt rullningslistfönster
* Ikon
* Ikonknapp
* Linjediagram
* Meny
* Knappen Flerradstext
* Textinmatning med flera linjer
* Textvy med flera linjer
* Fråga om numerisk pixelkarta
* Numerisk prompt
* Numeriskt rullningshjul
* Knappen Pixelkarta
* Uppmaning om pixelkarta
* Skjutreglage för bildpunktskarta
* Pixelkarta Företr
* Förloppsindikator
* Prompt
* Radiell förloppsstapel
* Alternativknapp
* Rullningshjul
* Textinmatning med en rad
* Slider
* Rullningshjul för strängar
* Textknapp
* Trädvy
* Lodrät lista
* Lodrät rullningslist

Det är enkelt för programmet att skapa sina egna kundwidgetar också.

### <a name="complete-low-level-drawing-api"></a>Slutföra api för lågnivåritning

Azure RTOS GUIX ger ett robust API för arbetsyteritning, så att programmet kan rendera komplexa grafiska former.

Alla funktioner stöder antialias för högfärgsdjupmål, och alla former kan fyllas i våra konturer, inklusive heldragen fyllning och pixelkarta. Alla ritningsprimititit har stöd för pensel-alfa vid körning med 16 bpp och högre färgdjup. Ritningsfunktioner är:

* Arc-rita
* Cirkeldrag
* Linjedragning
* Cirkeldiagram
* Pixelkarta med blandning
* Bildpunktskarta-panel
* Polygon Draw
* Text Draw
* Draw -et-et-
* Ellips draw
* Pixel Draw
* Bildpunktskarta
* Pixelkarta – rotera
* Rektangeldrag
* Text Blend

### <a name="default-free-fonts-and-easy-to-add-more"></a>Standardfria teckensnitt och enkelt att lägga till fler

Azure RTOS GUIX innehåller en kostnadsfri uppsättning TrueType-teckensnitt. Utvecklare kan lägga till ytterligare TrueType-teckensnitt efter behov.

Teckensnittsformatet Azure RTOS GUIX stöder 8bpp-antialias, 4bpp-antialias och 1bpp teckensnitt. För de mest resursbegränsade programmen återger GUIX Azure RTOS TrueType-teckensnitten i ett komprimerat format med hjälp av vårt GUIX Studio-skrivbordsverktyg.

### <a name="custom-jpg-and-png-decoder-implementation"></a>Anpassad implementering av JPG- och PNG-avkodare

Anpassad implementering av JPG- och PNG-avkodare för JPG- och PNG-filavkodare. Den här implementeringen stöder konvertering av färgutrymme, dithering och körning av Azure RTOS GUIX-kompatibla bildpunktskarteformatbilder.

### <a name="extensive-display-and-touchscreen-support"></a>Omfattande stöd för visning och pekskärm

Azure RTOS GUIX innehåller allmänna visningsdrivrutiner för nästan alla färgformat, inklusive 1bpp-färgad, 8 bpp-palette, 8 bpp 3:3:2-format,

16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format och 32 bpp a:r:g:b format. Dessutom är Azure RTOS GUIX integrerat med många av de mest populäraSTYRENHETs- och maskinvaruacceleratorerna (ST ChromeArt, Renesas Controller osv.).

Azure RTOS GUIX har fullständigt stöd för pekskärm (inklusive gesterstöd), pennenheter och indataenheter för virtuella tangentbord.

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a>Azure RTOS GUIX Studio-skrivbordsverktyget WYSIWYG

Azure RTOS GUIX Studio har en komplett WYSIWYG-skärmdesignmiljö där användaren kan dra och släppa grafiska element som används för att skapa GUI-skärmarna. Azure RTOS GUIX Studio genererar automatiskt C-kod som är kompatibel med Azure RTOS GUIX-biblioteket, redo att kompileras och köras på målet. Utvecklare kan skapa för renderade teckensnitt för användning i ett program med hjälp av det integrerade Azure RTOS GUIX Studio-verktyget för teckengenerering. Teckensnitt kan genereras i oreda eller antialiasformat och optimeras för att spara utrymme på målet. Teckensnitt kan innehålla valfri uppsättning tecken, inklusive Unicode-tecken för flerspråkiga program.

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

Azure RTOS GUIX Studio underlättar import av grafik från PNG- eller JPG-filer med konvertering till komprimerade Azure RTOS GUIX Pixelmaps för användning i målsystemet. Många av de Azure RTOS GUIX-widgettyperna är utformade för att införliva användargrafik för ett anpassat utseende. Dessutom tillåter Azure RTOS GUIX Studio anpassning av standardfärger och ritningsformat som används av Azure RTOS GUIX-widgetar, vilket gör det enkelt för utvecklare att finjustera utseendet på Azure RTOS GUIX. Generering och underhåll av programsträngar är en annan inbyggd funktion Azure RTOS GUIX Studio. På så sätt kan utvecklare utforma ett program med ett språk för utveckling och snabbt och enkelt lägga till stöd för ytterligare språk när produkten har släppts. Ett komplett Azure RTOS GUIX-program kan köras på en stationär dator i Azure RTOS GUIX Studio-miljön, vilket möjliggör en snabb och enkel generering och demonstration av GUI-begrepp, testning av skärmflöden och visning av skärmövergångar och animeringar. När det är klart kan en design exporteras som målklara C-datastrukturer som är redo att kompileras och länkas till Azure RTOS GUIX- och Azure RTOS ThreadX-biblioteken.

Azure RTOS GUIX och Azure RTOS GUIX Studio har stöd för flera resursteman, så att ett program enkelt kan installeras om vid körning. Teckensnitt, färger och pixelkartor kan ändras vid körning med ett enkelt API.

Läs mer om GUIX Studio

### <a name="complete-win32-simulation"></a>Slutför Win32-simulering

Azure RTOS GUIX körs på Windows dator med exakt samma ritningsbibliotek som körs på måltavlan. Med Azure RTOS GUIX kan du skapa och köra ett GUI-program på datorn och använda samma programkod på målet för felsökning, snabba prototyper, demonstration och WYSIWYG-målåtgärd.

### <a name="advanced-technology"></a>Avancerad teknik

* Azure RTOS GUIX avancerade teknik omfattar:
* Alfablandning
* Antialias
* Automatisk skalning
* Bitmappkomprimering
* Blandning av arbetsyta
* Stöd för anpassad widget
* Stöd för uppskjuten ritning
* Stöd för dithering
* Endiansk neutral programmering
* Stöd för maskinvaruacceleratorer
* Stöd för flera språk och UTF-8-kodning
* Stöd för flera skärmar och arbetsyta
* Optimerad urklippning, ritning och händelsehantering
* Runtime JPEG- och PNG-avkodare
* Hudning och teman
* Har stöd för 32-bitars true-color med alfagrafikformat
* Stöd för övergångar, figurer och animering
* Win32-simulering
* Fönsterhantering inklusive viewports- och Z-orderunderhåll
