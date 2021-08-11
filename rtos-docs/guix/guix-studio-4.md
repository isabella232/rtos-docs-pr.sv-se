---
title: GUIX Studio-resurser
description: GUIX Studio tillhandahåller hantering av alla gränssnittsresurser som programmet kommer att använda för färger, teckensnitt, pixelkartor och strängar. Avsnitten nedan beskriver hur du lägger till, ändrar och tar bort resurser i gränssnittets skärmdesign.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dd694cb7d34df7ecae206c3dcaf7d75a20bd4bd4e26471bb94da4129897ef727
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786152"
---
# <a name="chapter-4-guix-studio-resources"></a>Kapitel 4: GUIX Studio-resurser

GUIX Studio tillhandahåller hantering av alla gränssnittsresurser som programmet kommer att använda för färger, teckensnitt, pixelkartor och strängar. Avsnitten nedan beskriver hur du lägger till, ändrar och tar bort resurser i gränssnittets skärmdesign. 

All resurshantering sker inom ***Vyn Resurser** _ i ANVÄNDArgränssnittet för GUIX Studio, enligt bilden nedan i _*_bild 8_**.

![Skärmbild av GUIX Studio-Vyn Resurser.](./media/guix-studio/image38.jpg)

**Bild 8**

## <a name="color-resources"></a>Färgresurser

I avsnittet ***Colors** _ i _*_Vyn Resurser_*_ du hantera dina färgresurser. Du kan expandera den här vyn genom att klicka på fältet _ * i sidhuvudet, vilket resulterar i vyn som *+* visas nedan i bild **_9:_**

![Skärmbild av avsnittet Färger i Vyn Resurser](./media/guix-studio/image_39.png)

**Bild 9**

Färgresurser består av en eller flera färger, var och en med ett unikt logiskt namn. I bild **9 är till exempel det** logiska namnet **CANVAS,** som är systemfärgs-ID för skärmens bakgrundsfärg, associerat med den fysiska färgen svart. Den här färgresursen används när programmet **GX_COLOR_ID_CANVAS** som färg i objektegenskaperna.

Färgen "swatch" som anger RGB-värdet för färg visas till vänster, följt av namnet på färg-ID:t. Du kan när som helst ändra RGB-värdet som är associerat med ett ID-namn. Du kan inte ändra de fördefinierade systemfärg-ID-namnen eftersom de används internt av GUIX-biblioteket. Du kan dock ändra något av färgvärdena. Att ändra ett systemfärgvärde är en **global ändring.** Det innebär att alla widgetar som inte har en specifik färgtilldelning får det nya systemfärgvärdet.

Du kan ändra både färgnamnet och färgvärdet för anpassade färger som du har lagt till i temat.

Om du vill ändra en färgresurs dubbelklickar du (eller högerklickar och väljer meny) på färgresursen. Den här åtgärden tar fram dialogrutan för färgdefinition. Från den här dialogrutan kan färgresursen ändras så att den matchar programmets användargränssnittsbehov. ***Bild 10** _ visar ändringsdialogrutan när _ *CANVAS** dubbelklickas. Utseendet på den här dialogrutan ändras baserat på målvisningens färgformatinställningar.

![Skärmbild av dialogrutan Redigera färg.](./media/guix-studio/edit_color.png)

**Bild 10**

Utseendet på dialogrutan Redigera färg ändras beroende på färgdjupet och färgformatkonfigurationen för den aktuella visningen.

Om du vill lägga till en ny färgresurs går du till avsnittet ***Colors** _ i _ *_Vyn Resurser_** och väljer följande knapp:

![Knappen Lägg till ny färg](./media/guix-studio/image41.jpg)

Använd den resulterande färgdialogrutan för att lägga till en ny färgresurs, som du ser nedan i ***bild 11**:*

![Skärmbild av Ny färg i dialogrutan Redigera färg.](./media/guix-studio/new_color.png)

**Bild 11**

När du har slutfört de här stegen **väljer** du Spara en ny färgresurs **med namnet NEW_COLOR** med den fysiska färgen grön så att programmet kan använda den.

**Särskilda överväganden när du ändrar inställningarna för visningsfärgformat:**

När du skapar ett nytt projekt uppmanas du automatiskt att konfigurera projektets skärmar och färgformatet för varje visning. Oftast gör du dessa val en gång och du behöver inte ändra dessa konfigurationsinställningar.

Du kan komma fram till att det är nödvändigt att ändra inställningarna för visningsfärgformatet vid ett senare tillfälle. I så fall gör GUIX Studio en konvertering som passar bäst för ditt aktuella system och dina RGB-värden för användarfärg från det gamla färgformatet till det nya färgformatet. Den här konverteringen följer några logiska regler.

För användardefinierade färger försöker GUIX Studio alltid konvertera föregående färg till närmaste matchande färg i det nya färgformatet. Om du konverterar från ett högt färgdjup, till exempel färgformatet 16 bpp 5:6:5 till en grå skala eller färgformat för färg som inte är det, kan den här ändringen resultera i oönskade färgkonverteringar. När du gör stora ändringar i inställningarna för visningsfärgdjup kan vissa manuella uppdateringar av den nya användardefinierade färgtabellen krävas.

För fördefinierade systemfärger definierar GUIX Studio internt tre unika standardfärgtabeller. En standardfärgtabell används för alla färgdjup som är större än 4 bpp gråskala, en andra standardfärgtabell används för gråskalningsfärgformat (1 bpp < display_color_format <= 4bpp) och slutligen används en tredje standardtabell för systemfärg för färgformat.

När du byter visningsfärgformat med hjälp Project dialogrutan Konfiguration tillämpas följande regler:

1) Om de gamla och nya visningsfärgformaten använder olika standardsystemfärgtabeller enligt definitionen ovan återställs systemfärgerna till de fördefinierade standardfärgerna. Med andra ord, om du växlar från färg till grå skala eller från grå skala till färgdjup återställs systemfärgerna till de internt definierade standardvärdena för det nya färgdjupet. Detta kan orsaka förlust av anpassad färginformation, men den här lösningen ger dig en rimlig startpunkt när du gör en dramatisk ändring i inställningarna för visningsfärgformatet.

2) Om de gamla och nya färgformaten använder samma standardfärgtabell, vilket innebär att du gör en mindre dramatisk ändring av färgformatet, testar GUIX Studio varje systemfärg för att avgöra om du har ändrat RGB-värdet för systemfärgen från dess standardvärde. Om RGB-värdet för systemfärgen har ändrats gör GUIX Studio en konvertering med bästa matchning från det gamla färgformatet till det nya färgformatet. Om systemfärgen inte har ändrats återställs den till standardfärgen för det nya färgformatet.

**Särskilda överväganden för palettelägesåtgärd:**

När ett projekt har konfigurerats för färgformatet 256 färgpalettläge kan användaren konfigurera hur paletten ska installeras och användas definieras. Du kan komma åt och redigera palettedefinitionen med hjälp av konfigurera| Dialogrutan Teman, och om ditt projekt är inställt på 8 bpp bör du se knappen "Redigera paletten". Klicka på den här knappen för att öppna dialogrutan Redigera paletten:

![Skärmbild av dialogrutan Redigera paletten.](./media/guix-studio/edit_palette.png)

GUIX Studio delar in paletten i två delar: avsnittet "användardefinierad" och avsnittet "genereras automatiskt". GUIX Studio kör en avancerad optimal algoritm för palettegenerering för att skapa den bästa paletten för att visa de bilder som ingår i varje tema. Du kan minska antalet paletteposter som du behöver definiera genom att skriva ett tal i fältet "Fördefinierade paletteposter" och ange ett RGB-värde som du vill för någon av dessa platser. De återstående platserna allokeras till Studio för att skapa en optimal färgpalett för att visa dina bilder.

Om du vill redigera en färg som definierats i resursvyn när du kör i det här läget kan du bara välja färgredigeraren från de fördefinierade paletteposter som du har definierat. Det beror på att de återstående paletteposterna genereras automatiskt av GUIX Studio och ändras när bilderna som läggs till i projektet ändras.

Om du behöver visning av antialiasade teckensnitt när du kör i 8bpp-paletteläge måste du definiera en matris med paletteposter som skapar en toning för varje förgrunds-/bakgrundsfärg för att visa den antialiasade texten. Du kan använda 8 paletteposter för toningen för varje färgkombination eller 16 paletteposter för en jämnare toning. Det här antalet paletteposter som används bestäms av kryssrutan "Number of Palette Mode Anti-Aliased Text Colors" (Antal antialiasade textfärger i paletteläge) i dialogrutan Project för konfiguration. Du kan använda en toning med bara åtta poster för att minimera de paletteposter som används för varje färgkombination, eller använda 16 inmatningstoningar för att ge det jämnaste antialiasade textutseendet.

För att förenkla definition av en färgtoning för att visa antialiastext, eller för att generera en färgtoning för din egen användning, innehåller dialogrutan Redigera paletten knappen Generera toning. Om du vill använda den här funktionen måste du först tilldela r:g:b-värdena för start- och slutfärgerna.

Om du till exempel vill visa antialiasad röd text på en medelgrå bakgrund med hjälp av åtta paletteposter som börjar vid index 50 tilldelar du värdet r:g:b för 255:0:0 till paletteindex 50 och värdet r:g:b 128:128:128 till paletteindex 57. Ange dessa paletteindexvärden i fälten start-index och slutindex i den här dialogrutan och klicka på knappen Generera toning. Paletteposterna 51 till 56 initieras för att definiera en jämn toningsövergång mellan dina avgränsade färger.

## <a name="font-resources"></a>Teckensnittsresurser

För att hantera teckensnittsresurser måste avsnittet ***Font** _ _*_i Vyn Resurser_*_ först expanderas genom att klicka på fältet _ * , vilket resulterar i dialogrutan som visas nedan i *+* bild **_12:_**

![Skärmbild av avsnittet Teckensnitt i Vyn Resurser.](./media/guix-studio/image44.jpg)

**Bild 12**

Teckensnittsresurser består av en eller flera teckensnitt, var och en med ett unikt logiskt namn. I bild **12 associeras** till exempel det logiska **namnet SYSTEM** med ett specifikt teckensnitt. Den här teckensnittsresursen används när programmet **anger SYSTEM** som teckensnitt i objektegenskaperna. Teckensnittsgruppen visar en WYSIWYG-förhandsgranskning av teckenfraserna till vänster, teckenhöjden i bildpunkter, namnet på teckensnitts-ID:t och teckenstorleken (i kb).

I vyn ovan är de fyra första teckensnitten de fördefinierade standardtyper som krävs av GUIX-biblioteket. Du kan ändra teckensnittsdata som är associerade med dessa teckensnitt, men du kan inte ändra dessa teckensnitts-ID-namn.

Det sista teckensnittet som visas ovan, med namnet "Kursiv", är ett anpassat teckensnitt som har lagts till i projektet av användaren.

Om du vill ändra en teckensnittsresurs dubbelklickar du (eller högerklickar och väljer meny) på teckensnittsresursen. I den här dialogrutan kan teckensnittsresursen ändras så att den matchar programmets användargränssnittsbehov. ***Bild 13** _ visar dialogrutan för ändring när _ *SYSTEM** dubbelklickas.

! [[Skärmbild av dialogrutan för ändring när SYSTEM dubbelklickas.](./media/guix-studio/edit_system_font.png)

**Bild 13**

Om du vill lägga till en ny teckensnittsresurs går du till avsnittet ***Font** _ i _ *_Vyn Resurser_** och väljer följande knapp:

![Knappen Lägg till nytt teckensnitt](./media/guix-studio/image46.jpg)

Dialogrutan anropas för `Font Edit` att lägga till en ny teckensnittsresurs, som du ser nedan på bild ***14***:

![Skärmbild av dialogrutan Ändring för att lägga till en ny teckensnittsresurs.](./media/guix-studio/add_new_font.png)

**Bild 14**

Nya GUIX-teckensnitt skapas av GUIX Studio som återger ett valt TrueType-teckensnitt med en viss storlek. Därför kräver dialogrutan ovan först en TrueType-teckensökväg. Du kan använda bläddringsknappen för att bläddra till en katalog som innehåller teckensnittsfiler i utvecklingssystemet. Flera TrueType-teckensnitt ingår också i undermappen GUIX/fonts, oavsett var du har installerat GUIX Studio.

Om möjligt lagras platsen för TrueType-teckensnittsfilen internt med hjälp av en projekt relativ sökväg. Därför är det viktigt att ha alla teckensnittsfiler på en gemensam plats och använda en gemensam katalogträdstruktur för dina projekt och teckensnittsfiler så att du kan flytta GUIX Studio-projekt från en utvecklingsstation till en annan.

I fältet Teckensnittsnamn kan du ange namnet på teckensnittsresurs-ID:t. Det här är resurs-ID:t som ska användas i koden som genereras av GUIX Studio och som även används av ditt program när teckensnittet refereras till. Det här namnet måste följa syntaxkraven för C-variabelnamngivning.

När du har valt en TrueType-teckensnittsfil som ska användas som indata anger du ett logiskt teckensnittsnamn.

Kryssrutan **"Generate Kerning Info"**(Generera Kerning-information) instruerar GUIX Studio att inkludera kerningsinformation i det genererade teckensnittet, som används för att justera de relativa positionerna för efterföljande glyphs i en sträng. Om du vill använda kerning med dina strängar måste du använda ett teckensnitt som innehåller kerningsinformation och aktivera den här kryssrutan. Du måste också definiera GUIX-biblioteksbyggealternativet "GX_FONT_KERNING_SUPPORT" för att stödja rendering av text med kerningsinformation.

Kryssrutan " Include **character set defined by String Table**" instruerar GUIX Studio att inkludera de glyphs som refereras av den statiska strängtabellen i det genererade teckensnittet. Du kan inkludera ytterligare tecken genom att välja och redigera de teckenintervall som anges nedan, men det här alternativet kan väljas för att snabbt generera den minsta teckenuppsättning som behövs för att visa de strängar som definierats i strängtabellen. Om strängtabellen använder glyphs som inte finns i truetype-källteckensnittet är dessa tecken inte tillgängliga i ditt GUIX-teckensnitt och visas inte i målsystemet.

Om du vill generera ett mer komplett teckensnitt eller ett teckensnitt som innehåller tecken som inte får användas i den statiskt definierade strängtabellen kan du också välja teckenintervall i listan nedan. Observera att du kan välja val av antal teckenintervall och att du kan redigera den faktiska start- och slutteckenkoden som ska inkluderas i varje valt intervall.

De fördefinierade teckenintervallen och sidnamnen är bara förslag som gör att du enkelt kan välja den teckenuppsättning som behövs för de aktiva språk som används i dag. De angivna språknamnen har ingen effekt på det genererade GUIX-teckensnittet och du kan skriva in valfritt hexteckenintervall som du vill för alla aktiverade eller valda teckenintervall.

Om du till exempel vill generera ett teckensnitt som bara innehåller de numeriska tecknen kan du välja teckensidan "Ascii", men ange startvärdet 0030 och slutvärdet 0039 för att generera ett teckensnitt som endast innehåller de numeriska tecknen. Observera att teckenintervallvärdena kodas i Hexadecimal, vilket är den normala notationen för Unicode-teckentabeller.

Som standard stöder GUIX Studio och GUIX-biblioteket teckenkoder 0x0000 via 0xffff, som omfattar alla aktiva språk, matematiska formulär och andra symboler som används i dag. Om du behöver använda teckenkoder ovanför värdet för 0xffff, inklusive vissa privata användningsområden, måste du aktivera kryssrutan "Stöd utökat teckenintervall". När den här kryssrutan är markerad tillåter GUIX Studio att användaren anger teckenintervall från 0x0000 till 0x10ffff, vilket innehåller teckenintervallen för Privat Unicode-användning. Om du behöver det här utökade teckenintervallet måste du också definiera GUIX-biblioteksbyggalternativet "GX_EXTENDED_UNICODE_SUPPORT" så att GUIX-biblioteket internt stöder 32-bitars teckenkoder, i stället för standardkonfigurationen som stöder 16-bitars teckenkoder.

Om du markerar kryssrutan "Inkludera teckenuppsättning definierad av strängtabell" och ett eller flera av teckenintervallen i listan nedan, kombinerar GUIX Studio dessa val till supermängden för både de valda intervallen och de tecken som används i strängtabellen. Naturligtvis måste det valda TrueType-källteckensnittet också innehålla de tecken som behövs för att GUIX Studio ska kunna skapa meningsfulla glyphs för varje begärt teckenvärde.

När teckenintervallet har fastställts anger du teckenhöjden i bildpunkter och teckensnittsformatet. Både antialias och binära teckensnitt stöds. Binära teckensnitt kräver mindre statiskt datalagringsområde, men antialias-teckensnitt ger det bästa utseendet på mål som körs med 4 bpp gråskala eller högre färgdjup.

>[!NOTE]  
> *"Teckenhöjden" avser teckensnittets EM Square. I traditionell metalltyp var EM Square lika med radhöjden för den metallkropp som varje bokstav ökar från, och varje metallkropp hade samma storlek. I metaltyp kunde den fysiska storleken på en bokstav normalt inte överskrida EM-kvadraten. I digital typ är EM ett rutnät med godtycklig upplösning som används som designutrymme för ett digitalt teckensnitt. För dessa digitala teckensnitt är det vanligt att vissa glyph-funktioner, till exempel accenter och härkomster, kan sträcka sig utanför gränserna för EM-kvadraten. Slutresultatet är att widgethöjden som krävs för att helt visa ett visst teckensnitt ofta behöver vara något större än den begärda teckenpunktshöjden.*

När alla fält för teckensnittskonfiguration har slutförts klickar du på knappen OK för att skapa en ny teckensnittsresurs. GUIX Studio genererar ett GUIX-kompatibelt teckensnitt med de valda egenskaperna, lägger till teckensnittet i projektresurserna och gör teckensnittet tillgängligt för programmet att använda.

## <a name="pixel-map-resources"></a>Pixelkartresurser

För att kunna hantera pixelmappningsresurser måste avsnittet ***Pixel-maps** _ i _*_Vyn Resurser_*_ först expanderas genom att klicka på fältet _ * , vilket resulterar i dialogrutan som visas nedan i *+* bild **_15:_**

När gruppen `Pixelmap` har expanderats bör du se en förhandsgranskning som ser ut ungefär så här:

![Skärmbild av avsnittet Pixelkartor i Vyn Resurser.](./media/guix-studio/pixelmap_view.png)

**Bild 15**

Pixelkarta-resurser består av en eller flera pixelkartor, var och en med en förhandsgranskning av bildpunktskartan till vänster, pixelkartan i bildpunkter, ett unikt logiskt namn och lagringsstorleken för pixelkartan i utdataresursfilen (i kb).

Den första gruppen med pixelkartor består av de fördefinierade systemets pixelkartor som krävs av GUIX-widgetar, till exempel alternativknappar och kryssrutor. Du kan ändra pixelkartan som är associerad med systemets pixelkartor, men du kan inte ändra dessa pixelkartas ID-namn. Ovan visas även flera anpassade pixelkartor med namn som "BACKGROUND" och "BUTTON_ACTIVE". Det här är exempel på pixelkartor som en användare har lagt till i projektet och som kan användas för att rendera en GX_PIXELMAP_BUTTON widget.

Eftersom många projekt innehåller ett stort antal bildpunktskartor kan du med pixelkartan definiera val annat antal mappar för pixelkartan för att organisera dina bildpunktskartbilder. 

Du lägger till en ny mapp för pixelkartan genom att högerklicka på `Pixelmaps` ***avsnittsrubriken i Vyn Resurser*** välja "Lägg till mapp".

Om du vill ändra en pixelkarta-resurs dubbelklickar du (eller högerklickar och väljer meny) på pixelmappningsresursen. Från den här dialogrutan kan pixelmappningsresursen ändras så att den matchar programmets användargränssnittsbehov. ***Bild 16** _ visar dialogrutan för ändring när _ *RADIO_ON** dubbelklickas.

![Skärmbild av dialogrutan Redigera pixelkartor.](./media/guix-studio/image49.jpg)

**Bild 16**

I `Edit Pixelmap` dialogrutan kan du definiera en ny pixelkarta eller ändra innehållet i en befintlig pixelkarta. GUIX Studio läser indatabilden i bakgrunden och konverterar bilden till det format som `GUIX GX_PIXELMAP` kan användas av GUIX-biblioteket. GUIX Studio konverterar även färgrymden för den inkommande bilden till färgrymden på skärmen där pixelkartan ska användas.

Det första fältet i den här dialogrutan är sökvägen till källavbildningen. GUIX Studio stöder indata från PNG-bildfiler (.png) eller JPEG-format (.jpg). Du kan använda knappen "bläddra" för att hitta önskad indatafil i ditt lokala filsystem.

Om möjligt lagras platsen för indatabildfilen internt med hjälp av en projekt relativ sökväg. Därför är det viktigt att ha alla avbildningsfiler på en gemensam plats och använda en gemensam katalogträdstruktur för dina projekt och avbildningsfiler så att du kan flytta GUIX Studio-projekt från en utvecklingsstation till en annan och inte förlora spår av inmatade bilddata.

Med `Pixelmap ID` fälten kan du ange det logiska namnet på pixelmappningsresursen. Det här namnet måste vara unikt och måste följa C-syntaxregler för variabelnamn.

Med kryssrutan Ange utdatafil kan du ange en unik utdatafil för varje pixelkarta. Om den här kryssrutan inte är markerad skrivs pixelkartan till standardresursfilen för den här visningen. Om kryssrutan är markerad kan du ange ett specifikt filnamn där data för den här pixelkartan ska skrivas. Syftet med det här alternativet är att du ska kunna dela upp pixelkartan, som kan vara mycket stora C-matriser, i flera utdatafiler. Vissa kompilatorer har svårt att hantera C-filer som är hundratusentals källrader.

Med kryssrutan "Komprimera utdata" kan du ange om utdata för pixelkartan ska använda en upphovsrättsskyddad GUIX-komprimeringsalgoritm. Komprimerade utdatafiler är vanligtvis mindre, men de kräver också processortid för att renderas på målet. Oftast väljer du komprimering för dina stora pixelkartor och använder icke-komprimerat format för dina mindre pixelkartor.

Kryssrutan `Include Alpha Channel` avgör hur GUIX Studio använder alfakanalinformation som ibland finns i .png indatafiler. Om den här kryssrutan är markerad och visningen körs med 16 bpp-färgdjup eller högre bevarar GUIX Studio fullständiga inkommande alfadata i utdatafilen. Om den här kryssrutan inte är markerad skapar GUIX en något mindre utdatafil. Den här utdatafilen kan innehålla transparens, men den innehåller inte fullständig alfablandningsinformation.

Kryssrutan instruerar GUIX Studio att använda en avancerad ditheringsalgoritm när indatabilden konverteras för användning med `Dither` en lägre färgdjupvisning. Dithering är vanligtvis aktiverat, men kan orsaka större utdatafiler om komprimering används eftersom det blir färre upprepade bildpunkter.

När alla alternativ har angetts klickar du på knappen OK för att skapa en ny pixelmappningsresurs. GUIX Studio läser indatabildfilen, dekomprimerar den, utför färgrymdskonvertering och dithering, komprimerar om data och sparar data i GUIX-kompatibelt format om du `GX_PIXELMAP` vill. Den nya pixelkartan läggs till i projektresurserna och görs tillgänglig för programmet att använda.

Om du vill lägga till en ny pixelmappningsresurs går du Vyn Resurser i avsnittet `Pixelmaps` i Vyn Resurser på följande knapp: 

![Lägg till knappen New Pixel-map (Lägg till ny pixelkarta).](./media/guix-studio/image50.jpg)

**Redigera batch-pixelkarta**

Om du vill ändra egenskaperna för en massa pixelkartor högerklickar du på pixelkartan eller  mappen och väljer redigera **pixelkarta(s)-menyn** för att anropa dialogrutan Redigera bildpunktskarta.

![Skärmbild av dialogrutan Redigera flera bildpunktskartor.](./media/guix-studio/batch_pixelmap_edit.jpg)

Statusbeskrivning för kryssruta:

![Markerad knapp.](./media/guix-studio/checkbox_checked.jpg)
Den här statusen innebär att alla pixelkartor har egenskapen markerad. Du kan avmarkera knappen för att ändra egenskapen för alla pixelkartor.

![Omarkerad knapp.](./media/guix-studio/checkbox_unchecked.jpg)
Den här statusen innebär att alla pixelkartor har egenskapen avmarkerad. Du kan markera knappen för att ändra egenskapen för alla pixelkartor.

![Knappen Obestämt.](./media/guix-studio/checkbox_undetermined.jpg)
Den här statusen innebär att pixelkartor har en annan status för egenskapen. Du kan markera eller avmarkera knappen för att ändra egenskapen för alla pixelkartor, annars förblir egenskapen oförändrad.


## <a name="string-resources"></a>Strängresurser

När gruppen Strängar expanderas bör du se en förhandsgranskning av projektsträngstabellen enligt nedan:

![Skärmbild av den expanderade gruppen Strängar.](./media/guix-studio/string_res_view.png)

**Bild 17**

Strängresurser består av en eller flera strängar, var och en med ett unikt logiskt namn. I bild **17 är till** exempel det logiska namnet "PATIENT_LIST" associerat med strängen "Patientlista" som visas till höger. Den här strängresursen används när programmet PATIENT_LIST som strängen i objektegenskaperna.

Kom alltid ihåg att dina ID-namn för alla resurstyper måste vara C-syntaxkompatibla variabelnamn. Dessa namn kommer att användas i stor utsträckning när dina projektresursfiler och specifikationsfiler produceras av Studio.

Om du vill ändra en strängresurs dubbelklickar du (eller högerklickar och väljer meny) på strängresursen för att anropa dialogrutan ***String Table Editor** _. I dialogrutan _*_String Table Editor_*_ (Redigerare för strängtabell) kan strängresursen ändras så att den matchar programmets användargränssnittsbehov. _*_Bild 18_*_ visar ändringsdialogrutan när _ *STRING_13** dubbelklickas.

I det här fallet visas sträng-ID-namnet till vänster, där stränginnehållet för det första språket eller referensspråket visas till höger. Naturligtvis är det exakta stränginnehållet mycket specifikt för ditt program, men layouten för förhandsgranskningen av stränggruppen är konsekvent.

GUIX Studio stöder statisk text och flerspråkiga program genom att definiera och underhålla en strängtabell. Strängtabellen definierar ett sträng-ID för varje post och en strängkonstant för varje post för varje språk som stöds.

De språk som stöds av ditt program definieras med hjälp av dialogrutan Språkkonfiguration. Här visas:

![Skärmbild av dialogrutan Språkkonfiguration.](./media/guix-studio/config_languages.png)

**Bild 18**

Dialogrutan För språkkonfiguration anropas med hjälp av | Språkkommandot på programmenyn. I den här dialogrutan kan du definiera hur många språk som ska stödjas av ditt program och det namn eller språk-ID som ska associeras med varje språk. De språk som stöds kan ändras när projektet har skapats, men om ett språk tas bort bör du vara medveten om att strängdata som är associerade med det språket också tas bort och inte kan hämtas.

Kryssrutan Statiskt **definierad anger att** det valda språket kommer att statiskt definieras i källkodsformat i den genererade resursfilen. Om inga språk har definierats statiskt anges pekaren för språktabellen till NULL i den genererade visningstabellen och ett språk måste läsas in och installeras av programmet med hjälp av API:erna för binär resursinläsare som tillhandahålls av GUIX-biblioteket.

Kryssrutan **"Support Bidi Text"** instruerar GUIX Studio att aktivera dubbelriktat stöd för textåtergivning. Du bör aktivera den här kryssrutan om de strängar som du ska ange för det här språket kräver dubbelriktad textåtergivning.

Kryssrutan **"Generate Bidi Text in Display Order"**(Generera bidi-text i visningsordning) instruerar GUIX Studio att generera dubbelriktad text till utdatafilen i visningsordningen. Om det här alternativet är markerat krävs ingen körningsbearbetning i GUIX-biblioteket för att korrekt rendera dubbelriktad text. När det här alternativet är markerat ska dubbelriktad textåtergivning INTE aktiveras i GUIX-biblioteket. Den här konfigurationen ger bästa möjliga körningsprestanda, men stöder inte återgivning av dynamiskt definierade dubbelriktade textsträngar.

Det första språket eller "Index 1"-språket kallas "referensspråk". Det här är det språk som GUIX Studio använder när du definierar och redigerar ui-designen. Alla andra språk i strängtabellen kallas översättningsspråk. GUIX Studio stöder export och import av strängtabelldata i branschstandard-XLIFF- eller CSV-formatdatafiler, vilket är praktiskt för att utbyta stränginformation med translators som kan hjälpa programutvecklare med att lägga till översättningar för de språk som ska stödjas förutom referensspråket. När du exporterar GUIX-strängtabellen till en XLIFF- eller CSV-fil, inkluderas referensspråket tillsammans med ett översättningsspråk i XLIFF- eller CSV-strängdatautbytesfilen. När du importerar en XLIFF- eller CSV-fil används på samma sätt importerade data för att fylla i ett översättningsspråk i GUIX-strängtabellen.

![Skärmbild av Redigerare för strängtabell.](./media/guix-studio/image53.jpg)

**Bild 19**

Dialogrutan String Table Editor (Redigerare för strängtabell) visar först en lista med sträng-ID:er till vänster, följt av strängdata för referensspråket. Om mer än ett språk har definierats visar en tredje kolumn något av de översättningsspråk som stöds. Du kan öppna och stänga den tredje kolumnen genom att klicka på den lilla pilen längst upp till höger i referensspråkkolumnen.

När kolumnen för översättningsspråk visas kan du gå igenom översättningsspråken i projektet genom att klicka på de små pilarna längst upp till höger i kolumnen för översättningsspråk i stränglistan.

Du kan redigera en strängpost genom att klicka på posten i tabellen för att markera den. När du väljer en post visas postens sträng-ID och stränginnehåll i fälten under tabellvyn. Du kan skriva nya värden i dessa fält för att ändra sträng-ID och stränginnehåll.

Rutan till höger i tabellvyn visar förhandsgranskningar av widgetar som refererar till den valda strängen. Detta är användbart för att se om en redigerad sträng kommer att överskrida ett visst widgetområde.

Fälten till höger om stränginnehållet är:

- "Antal referenser": Det här fältet anger hur ofta ett visst sträng-ID används i GUIX Studio-projektet. Om referensantalet är 0 kan den här strängen vara inaktuell och kan eventuellt tas bort av användaren.
- Strängbredd (bildpunkter) anger visningsbredden för strängen med det angivna teckensnittet.
- Fältet "Anteckningar" är ett valfritt kommentarsfält där du kan lägga till information om syftet med eller användningen av varje sträng. Dessa anteckningar ingår i alla exporterade XLIFF-strängdatafiler för att hjälpa translators att göra korrekta och meningsfulla strängöversättningar.

Varje gång du har ***dialogrutan Redigerare*** för strängtabell öppen kan du lägga till ytterligare strängar i projektet genom att klicka på knappen Lägg till sträng högst upp i dialogrutan. Föråldrade eller oanvända strängar kan tas bort från projektet genom att först välja strängen och sedan klicka på knappen Ta bort sträng högst upp i dialogrutan.

Förutom att manuellt lägga till nya strängar i projektet med hjälp av dialogrutan String Table Editor kan du också lägga till nya strängar indirekt genom att helt enkelt skriva stränginnehåll i fältet "Text" i egenskapsvyn för en widget som stöder text. Med andra ord, när du lägger till nya widgetar i målvyn eller skriver textinformation i egenskapsvyn, skapar dessa åtgärder automatiskt nya poster i projektsträngtabellen.

## <a name="adding-language-translations"></a>Lägga till språköversättningar

GUIX Studio-redigeraren för strängtabeller stöder ett arbetsflöde för språkdefinition som gör att utvecklaren kan skapa ett program med sitt primära språk och sedan exportera strängdata till en XML- eller CSV-standardfil som ska skickas till en expert på språköversättning. Översättningsfilen returneras sedan till utvecklaren, som kan importera språköversättningarna tillbaka till sitt Studio-projekt och därmed lägga till stöd för ett nytt språk i sitt program.

Den här funktionen anropas med hjälp av knapparna Exportera (för att skriva strängdata till en fil) och Importera (för att läsa de översatta strängarna) överst i redigerare för strängtabell. Knappen Exportera används för att skapa en XML- eller CSV-fil för XLIFF-schema som innehåller dina referensspråkssträngar. Den här filen kan användas av en translator med hjälp av verktyg och redigerare som stöder standardfilformatet XLIFF eller CSV.

När en översättningsexpert returnerar XLIFF-filen till dig med de nya strängöversättningarna kan du använda knappen Importera för att läsa data från den här XLIFF- eller CSV-filen. Om XLIFF- eller CSV-filen innehåller ett nytt språk läggs det nya språket till i projektet. Om XLIFF-filen innehåller nya strängdata för ett befintligt språk importeras dessa nya data till projektet. Referensspråkssträngarna ändras inte av importåtgärden.

När du klickar på knappen Exportera visas dialogrutan XLIFF/CSV-exportkontroll, som visas nedan:

![Skärmbild av dialogrutan XLIFF/CSV-exportkontroll.](./media/guix-studio/image54.jpg)

**Bild 20**

Fälten Källspråk och Målspråk anger vilka strängtabellkolumner som ska skrivas till XLIFF- eller CSV-filen som referensspråk och översättningsspråk. Källspråket är referenssträngarna och målspråket är det språk som översättningsspråket tillhandahåller översatta strängdata för.

Fältet XLIFF-version anger en av två huvudsakliga XLIFF-filformatversioner, antingen version 1.2 eller version 2.0 (och senare). Dessa formatstandarder för XLIFF är inkompatibla och du måste veta vilken version dina verktyg använder innan du använder XLIFF-kommandona för export/import. Mer information om XLIFF-schemat och XLIFF-standarderna finns här:

- version 1.2: [https://docs.oasis-open.org/xliff/xliff-core/xliff-core.html](https://docs.oasis-open.org/xliff/xliff-core/xliff-core.html)
- version 2.0: [https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0os.pdf](https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0-os.pdf)

Med fälten för utdatafilnamn och utdatasökväg kan du ange filnamn och plats som utdatafilen ska skrivas till. Filnamnet är helt upp till användaren, men vi rekommenderar att du använder namn som anger käll- och målspråken i den exporterade filen.
