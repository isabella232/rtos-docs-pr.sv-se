---
title: Resurser för GUIX Studio
description: GUIX Studio tillhandahåller hantering av alla användar gränssnitts resurser som programmet kommer att använda för färger, teckensnitt, pixel-kartor och strängar. I avsnitten som följer beskrivs hur du lägger till, ändrar och tar bort resurser i GRÄNSSNITTs skärmens design.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3c3769c3ddf0eef73546627f1f50fa3d11b16948
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827156"
---
# <a name="chapter-4-guix-studio-resources"></a>Kapitel 4: resurser för GUIX Studio

GUIX Studio tillhandahåller hantering av alla användar gränssnitts resurser som programmet kommer att använda för färger, teckensnitt, pixel-kartor och strängar. I avsnitten som följer beskrivs hur du lägger till, ändrar och tar bort resurser i GRÄNSSNITTs skärmens design. 

All resurs hantering görs inom ***vyn resurser** _ i användar gränssnittet för GUIX Studio, som du ser nedan i _ *_bild 8_* *.

![Skärm bild av GUIX Studio-Vyn Resurser.](./media/guix-studio/image38.jpg)

**Figur 8**

## <a name="color-resources"></a>Färg resurser

I avsnittet ***färger** _ i _*_vyn resurser_*_ kan du hantera dina färg resurser. Du kan expandera den här vyn genom att klicka på *+* fältet _ * i vyns rubrik, vilket resulterar i vyn som visas nedan i **_bild 9_**:

![Skärm bild av avsnittet färger i Vyn Resurser](./media/guix-studio/image_39.png)

**Bild 9**

Färg resurser består av en eller flera färger, var och en med ett unikt logiskt namn. I **bild 9** är till exempel den logiska namn **arbets ytan,** som är system färg-ID för bakgrundens fyllnings färg, kopplad till den fysiska färgen svart. Den här färg resursen används när programmet anger **GX_COLOR_ID_CANVAS** som färg i objekt egenskaperna.

Färg remsan som anger färg-RGB-värdet visas till vänster följt av färg-ID-namnet. Du kan ändra det RGB-värde som är associerat med ett ID-namn när som helst. Du kan inte ändra de fördefinierade ID-namnen för systemfärgen eftersom de används internt av GUIX-biblioteket. Du kan dock ändra färg värden. Att ändra ett system färg värde är en **Global förändring**. Det innebär att alla widgetar som inte har en speciell färg tilldelning tar på det nya systemets färg värde.

Du kan ändra både färg namn och färg värde för anpassade färger som du har lagt till i temat.

Om du vill ändra en färg resurs dubbelklickar du på (eller högerklickar och väljer menyn) på färg resursen. Den här åtgärden öppnar dialog rutan färg definition. I den här dialog rutan kan du ändra färg resursen så att den matchar programmets GRÄNSSNITTs behov. ***Figur 10** _ visar ändrings dialog rutan när _ *arbets yta** dubbelklickas. Hur den här dialog rutan ser ut ändras baserat på inställningarna för mål visningens inställningar för färg format.

![Skärm bild av dialog rutan Redigera färg.](./media/guix-studio/edit_color.png)

**Bild 10**

Utseendet på dialog rutan Redigera färg ändras beroende på färg djupet och färg formats konfigurationen för den aktuella visningen.

Om du vill lägga till en ny färg resurs går du till avsnittet ***Colors** _ i mappen _ *_vyn resurser_** och väljer följande knapp:

![Knappen Lägg till ny färg](./media/guix-studio/image41.jpg)

Använd dialog rutan med resulterande färger för att lägga till en ny färg resurs, som du ser nedan i ***Bild 11**:*

![Skärm bild av den nya färgen i dialog rutan Redigera färg.](./media/guix-studio/new_color.png)

**Bild 11**

När du har slutfört de här stegen kan du välja **Spara** en ny färg resurs med namnet **NEW_COLOR** med den fysiska färgen grönt som är tillgänglig för det program som ska användas.

**Särskilda överväganden vid ändring av inställningarna för visnings färg format:**

När du skapar ett nytt projekt uppmanas du automatiskt att konfigurera projektets visning och färg formatet på varje skärm. Oftast kommer du att göra dessa val en stund och du behöver inte ändra dessa konfigurations inställningar.

Du kan se att det är nödvändigt att ändra inställningarna för bildskärms färg format vid ett senare tillfälle. I så fall kommer GUIX Studio att göra en bästa anpassning av dina aktuella system-och användar färgs RGB-värden från det gamla färg formatet till det nya färg formatet. Den här konverteringen följer några logiska regler.

För användardefinierade färger försöker GUIX Studio alltid konvertera den tidigare färgen till den närmaste matchande färgen i det nya färg formatet. Om du konverterar från ett högt färgdjup som 16 BPP 5:6:5-färgformat till ett grått skal eller monokromt färg format, kan den här ändringen leda till oönskade färg konverteringar. När du gör en stor ändring i inställningarna för visnings färgs djup kan det krävas en del manuella uppdateringar av den nya användardefinierade färg tabellen.

För fördefinierade system färger definierar GUIX Studio internt tre unika standard färg tabeller. En standard färg tabell används för alla färgdjup som är större än 4-BPP grått, en andra standard färg tabell används för grå Skale färg format (1 BPP < display_color_format <= 4bpp) och slutligen en tredje standard system färg tabell används för monokromt färg format.

När du växlar visnings färg formatet med hjälp av dialog rutan projekt konfiguration tillämpas följande regler:

1) Om det gamla och nya visnings färgs formatet använder olika standard färg tabeller för systemet som definieras ovan, så återställs system färgerna till de fördefinierade standard färgerna. Med andra ord, om du växlar från färg till gråskala eller från gråskala till monokromt färgdjup, återställs systemets färger till de internt definierade standardvärdena för det nya färg djupet. Detta kan leda till förlust av viss anpassad färg information, men den här lösningen ger dig en bra start punkt när du gör en dramatisk ändring av inställningarna för visnings färg format.

2) Om de gamla och nya färg formaten använder samma standard färg tabell, vilket innebär att du har en mindre dramatisk färg format ändring, kommer GUIX Studio att testa varje system färg för att avgöra om du har ändrat system färgens RGB-värde från standardvärdet. Om system färgens RGB-värde har ändrats, kommer GUIX Studio att göra en bästa matchning från det gamla färg formatet till det nya färg formatet. Om system färgen inte har ändrats kommer den att återställas till standard färgen för det nya färg formatet.

**Särskilda överväganden för åtgärden i bitmappsläge:**

När ett projekt har kon figurer ATS för färg formatet 256 i färgpalett, kan användaren konfigurera hur paletten ska installeras och användas definieras. Du kan komma åt och redigera definitionen av paletten med hjälp av konfigurera | Dialog rutan teman och om ditt projekt har angetts till 8 BPP bör du se knappen Redigera palett. Klicka på den här knappen för att öppna dialog rutan Redigera palett:

![Skärm bild av dialog rutan Redigera palett.](./media/guix-studio/edit_palette.png)

GUIX Studio delar upp paletten i två delar: avsnittet "användardefinierad" och avsnittet "automatiskt genererad". GUIX Studio kör en sofistikerad algoritm för optimalt skapande av palett för att skapa den bästa paletten för att visa de bilder som ingår i varje tema. Du kan dela ett valfritt antal paletter som du måste definiera genom att skriva ett tal i fältet "fördefinierade paletter" och ange eventuella RGB-värden som du vill för någon av dessa platser. De återstående platserna allokeras till Studio för att skapa en optimal färgpalett för att visa dina bilder.

Om du kör i det här läget kan du, om du vill redigera en färg som definierats i resursvyn, bara välja från de fördefinierade valda paletterna som du har definierat. Detta beror på att de återstående paletterna automatiskt genereras av GUIX Studio och kommer att ändras när de bilder som läggs till i projektet ändras.

Om du behöver Visa kantbaserade teckensnitt när du kör i 8bpp-läge, måste du definiera en matris med paletter som skapar en övertoning för varje förgrunds-/bakgrunds färg som används för att visa din anti-aliasad text. Du kan använda antingen åtta paletter för toningen för varje färg kombination eller 16-palettens poster för en mjukare övertoning. Det här antalet poster i paletten som används bestäms av kryss rutan "antal alternativ för att färgkopplade text färger i paletten" i dialog rutan för projekt konfiguration. Du kan använda en övertoning med endast åtta poster för att minimera de palettiska poster som används för varje färg kombination, eller använda 16-starttoningar för att ge det smidigaste text utseendet.

För att förenkla definitionen av en färg toning för visning av kantutjämna text, eller för att skapa en färg toning för egen användning, innehåller dialog rutan Redigera palett en knappen Skapa övertoning. Om du vill använda den här funktionen ska du först tilldela r:g: b-värdena för start-och slut tonings färgerna.

Om du till exempel vill visa kantad röd text på en medels grå bakgrund med åtta paletter som börjar med index 50, tilldelar du r:g: b värdet 255:0:0 till Palette index 50 och r:g: b-värdet 128:128:128 till Palette index 57. Ange dessa palettens index värden i fälten Start-index och slut index i den här dialog rutan och klicka på knappen generera övertoning. Paletterna 51 till 56 kommer att initieras för att definiera en jämn tonings över gång mellan dina markerings färger.

## <a name="font-resources"></a>Teckensnitts resurser

För att kunna hantera teckensnitts resurser måste avsnittet ***fonts** _ i _*_vyn resurser_*_ först expanderas genom att klicka på fältet _ *+* * som visas i dialog rutan nedan i **_figur 12_**:

![Skärm bild av avsnittet fonts i Vyn Resurser.](./media/guix-studio/image44.jpg)

**Figur 12**

Teckensnitts resurser består av ett eller flera teckensnitt, var och en med ett unikt logiskt namn. I **figur 12** är exempelvis det logiska namn **systemet** associerat med ett särskilt teckensnitt. Den här teckensnitts resursen används när programmet anger **system** som teckensnitt i objekt egenskaperna. I teckensnitts gruppen visas en WYSIWYG-förhandsgranskning av teckensnitts tecknen till vänster, teckensnitts höjden i bild punkter, teckensnitts-ID-namn och tecken storlek (i KB).

I vyn ovan är de första fyra teckensnitten de fördefinierade standard teckensnitt som krävs av GUIX-biblioteket. Du kan ändra teckensnitts data som är associerade med dessa teckensnitt, men du kan inte ändra dessa teckensnitts-ID-namn.

Det sista teckensnittet som visas ovan, med namnet "kursiv", är ett anpassat teckensnitt som har lagts till i projektet av användaren.

Om du vill ändra en teckensnitts resurs dubbelklickar du på (eller högerklickar och väljer menyn) på teckensnitts resursen. I den här dialog rutan kan teckensnitts resursen ändras för att matcha programmets GRÄNSSNITTs behov. ***Figur 13** _ visar ändrings dialog rutan när _ *system** dubbelklickas på.

! [[Skärm bild av dialog rutan för ändringar när systemet dubbelklickar på.](./media/guix-studio/edit_system_font.png)

**Figur 13**

Om du vill lägga till en ny teckensnitts resurs går du till avsnittet ***font** _ i avsnittet _ *_vyn resurser_** och väljer följande knapp:

![Knappen Lägg till nytt teckensnitt](./media/guix-studio/image46.jpg)

Då startas dialog rutan `Font Edit` för att lägga till en ny teckensnitts resurs, som du ser nedan i ***Bild 14***:

![Skärm bild av dialog rutan Ändra för att lägga till en ny teckensnitts resurs.](./media/guix-studio/add_new_font.png)

**Bild 14**

Nya GUIX-teckensnitt skapas av GUIX Studio och återger ett valt TrueType-teckensnitt i en viss storlek. Därför kräver dialog rutan ovan först en sökväg med TrueType-teckensnitt. Du kan använda knappen Bläddra för att bläddra till en katalog som innehåller teckensnittsfiler i utvecklings systemet. Flera TrueType-teckensnitt ingår också i undermappen GUIX/fonts när du har installerat GUIX Studio.

Om möjligt lagras platsen för TrueType-teckensnitts filen internt med en projekt relativ sökväg. Av den anledningen är det viktigt att du behåller alla dina teckensnittsfiler på en gemensam plats och använder en gemensam katalog träd struktur för dina projekt och teckensnittsfiler så att du kan flytta GUIX Studio-projekt från en utvecklings station till en annan.

I fältet teckensnitts namn kan du ange teckensnitts resursens ID-namn. Detta är resurs-ID: t som används i koden som genereras av GUIX Studio och som också används av programmet vid hänvisning till teckensnittet. Namnet måste följa kraven för namngivnings-och namngivnings syntax för variabeln.

När du har valt en TrueType-teckensnitts fil som ska användas som indata anger du ett logiskt namn för teckensnitt.

Kryss rutan "**generera kernings information**" instruerar GUIX Studio att ta med kerning från det genererade teckensnittet, som används för att justera de relativa positionerna för efterföljande tecken i en sträng. Om du vill använda kerning med dina strängar måste du använda ett teckensnitt som innehåller kernings information och aktivera den här kryss rutan. Du måste också definiera GUIX-bibliotekets build-alternativ "GX_FONT_KERNING_SUPPORT" för att stödja text åter givning med KERNING-information.

Kryss rutan **ta med den teckenuppsättning som definieras av sträng tabellen**"instruerar GUIX Studio att ta med de glyfer som en statisk sträng tabell refererar till i det genererade teckensnittet. Du kan lägga till ytterligare specialtecken genom att markera och redigera de tecken intervall som anges nedan, men det här alternativet kan väljas för att snabbt skapa den minsta teckenuppsättning som krävs för att Visa strängarna som definierats i din sträng tabell. Om din sträng tabell använder glyfer som inte finns i TrueType-teckensnittet, kommer dessa tecken inte att vara tillgängliga i ditt GUIX-teckensnitt och visas inte i mål systemet.

Om du vill generera ett mer fullständigt teckensnitt eller ett teckensnitt som innehåller tecken som inte kan användas i statiskt definierade sträng tabeller, kan du också välja tecken intervall i listan nedan. Observera att du kan välja valfritt antal tecken intervall och du kan redigera den faktiska start-och slut tecken koden som ska ingå i varje valt intervall.

De fördefinierade tecknen och sid namnen är bara förslag som gör det enkelt att välja den teckenuppsättning som behövs för de aktiva språk som används idag. De listade språk namnen har ingen inverkan på det genererade GUIX-teckensnittet, och du kan ange ett hexadecimalt tecken intervall som du vill använda för alla aktiverade eller markerade tecken intervall.

Om du till exempel vill generera ett teckensnitt som bara innehåller numeriska tecken kan du välja "ASCII"-kod sidan, men Ange startvärdet 0030 och slut värde 0039 för att generera ett teckensnitt som bara innehåller de numeriska tecknen. Observera att tecken intervalls värden kodade i hexadecimalt format, som är den normala notationen för Unicode-tecken tabeller.

Som standard stöder GUIX Studio och GUIX-biblioteket tecken koderna 0x0000 genom 0xffff, som omfattar alla aktiva språk, matematiska formulär och andra symboler som används idag. Om du behöver använda Character-koderna ovanför värdet 0xFFFFFFFF, inklusive vissa privata användnings områden, måste du aktivera kryss rutan "stöd för utökade teckenuppsättningar". När den här kryss rutan är markerad kan användaren ange tecken intervall från 0x0000 via 0x10ffff i GUIX Studio, som innehåller tecken intervallen för det privata Unicode-use. Om du behöver det här utökade Character-intervallet måste du också definiera GUIX-bibliotekets build-alternativ "GX_EXTENDED_UNICODE_SUPPORT" så att GUIX-biblioteket internt stöder 32-bitars Character Codes, i stället för standard konfigurationen som stöder 16-bitars Character-koder.

Om du markerar kryss rutan "inkludera teckenuppsättning definieras av sträng tabell" och ett eller flera av tecken intervallen i listan nedan, kommer GUIX Studio att kombinera dessa markeringar till supermängden för båda valda intervall och de tecken som används i din sträng tabell. Den valda TrueType-käll typsnittet måste också innehålla de tecken som behövs för att GUIX Studio ska kunna producera meningsfulla glyfer för varje begärt tecken värde.

När du har bestämt tecken intervallet anger du teckensnitts höjden i bild punkter och teckensnitts format. Både kantbaserade och binära teckensnitt stöds. Binära teckensnitt kräver mindre statiskt data lagrings utrymme, men med mellanliggande teckensnitt får du det bästa utseendet på mål som körs med 4-BPP gråskala eller högre färg djup.

>[!NOTE]  
> *"Font height" syftar på teckensnittets fyrkant. I traditionell typ av metall var EM-fyr kanten lika med rad höjden för den metall kropp från vilken varje bokstav stiger, och varje metall kropp har samma storlek. I typ av metall kunde en brevs fysiska storlek normalt inte överskrida fyr kanten. I digital typ är EM ett rutnät med godtycklig upplösning som används som design utrymme för ett digitalt teckensnitt. För de här digitala teckensnitten är det vanligt att vissa glyf-funktioner, till exempel accenter och Descents, kan sträcka sig utanför fyr kantens gränser. Slut resultatet är att den widget som krävs för att helt Visa ett visst teckensnitt ofta måste vara något större än det begärda bild punkts höjden.*

När alla fält för teckensnitts konfiguration har slutförts klickar du på knappen OK för att skapa en ny teckensnitts resurs. GUIX Studio genererar ett GUIX kompatibelt teckensnitt med de valda egenskaperna, lägger till det teckensnittet i projekt resurserna och gör teckensnittet tillgängligt för programmet som ska användas.

## <a name="pixel-map-resources"></a>Pixel – mappa resurser

För att kunna hantera pixel kart resurser visas avsnittet ***pixel-Maps** _ i _*_vyn resurser_*_ först genom att klicka på *+* fältet _ * som visas i dialog rutan nedan i **_Bild 15_**:

När `Pixelmap` gruppen expanderas bör du se en förhands granskning som liknar detta:

![Skärm bild av avsnittet pixel – Maps i Vyn Resurser.](./media/guix-studio/pixelmap_view.png)

**Bild 15**

Pixel – kart resurser består av en eller flera pixel-Maps, var och en med en förhands granskning av bild punkts kart bilden till vänster, pixel-Map-dimensionerna i bild punkter, ett unikt logiskt namn och lagrings storleken för pixel kartan i resurs filen för utdata (i KB).

Den första gruppen av pixel-Maps består av fördefinierad system pixel – Maps som krävs av GUIX-widgetar som alternativ knappar och kryss rutor. Du kan ändra de pixel kart data som är associerade med system pixeln – Maps, men du kan inte ändra dessa ID-namn för pixlar. Det som visas ovan är flera anpassade pixel kartor med namn som "bakgrund" och "BUTTON_ACTIVE". Dessa är exempel på pixel – Maps en användare har lagt till i projektet som kan användas för att återge en GX_PIXELMAP_BUTTON widget.

Eftersom många projekt innehåller ett stort antal pixel-kartor kan du med pixel kartan definiera ett valfritt antal mappar för pixel kartor för att ordna bild punkts kart bilder. 

Du lägger till en ny mapp för bild punkts karta genom att högerklicka på `Pixelmaps` avsnitts rubriken för ***vyn resurser*** att välja Lägg till mapp.

Om du vill ändra en pixel kart resurs dubbelklickar du (eller högerklickar och väljer menyn) på pixel-kart resursen. I den här dialog rutan kan pixel kart resursen ändras så att den matchar programmets GRÄNSSNITTs behov. ***Figur 16** _ visar ändrings dialog rutan när _ *RADIO_ON** dubbelklickas.

![Skärm bild av dialog rutan Redigera pixel – kartor.](./media/guix-studio/image49.jpg)

**Bild 16**

I `Edit Pixelmap` dialog rutan kan du definiera en ny pixel – mappa eller ändra innehållet i en befintlig pixel karta. GUIX Studio läser in bilden i bakgrunden och konverterar bilden till det `GUIX GX_PIXELMAP` format som kan användas av GUIX-biblioteket. GUIX Studio konverterar också färg området för den inkommande bilden till färg rymden för den bildskärm som den här pixel kartan använder.

Det första fältet i den här dialog rutan är sökvägen till käll bilden. GUIX Studio stöder indata från formatet PNG (. png) eller JPEG (. jpg). Du kan använda knappen Bläddra för att hitta önskad indatafil i det lokala fil systemet.

Om möjligt lagras platsen för den inmatade avbildnings filen internt med en projekt relativ sökväg. Av den anledningen är det viktigt att du behåller alla bildfiler på en gemensam plats och använder en gemensam katalog struktur för dina projekt och bildfiler så att du kan flytta GUIX Studio-projekt från en utvecklings station till en annan och inte förlora spår av indata från indatabilden.

Med `Pixelmap ID` fälten kan du ange det logiska namnet för pixel-Map-resursen. Namnet som anges här måste vara unikt och måste följa reglerna för namngivnings regler för C-variabel.

Med kryss rutan Ange utdatafil kan du ange en unik utdatafil för varje pixel karta. Om den här kryss rutan inte är markerad skrivs pixel data till standard resurs filen för den här visningen. Om kryss rutan är markerad kan du ange ett angivet fil namn där data för den här pixel kartan ska skrivas. Syftet med det här alternativet är att du ska kunna dela upp dina pixel kart data, vilket kan vara mycket stora C-matriser i flera utdatafiler. Vissa kompilatorer kan vara svårt att hantera C-filer som är hundratals tusentals käll rader.

Med kryss rutan komprimera utdata kan du ange om pixelns utdata ska använda en patentskyddad GUIX Compression-algoritm. Komprimerade utdatafiler är vanligt vis mindre, men de kräver också processor tid för att återge målet. Oftast väljer du komprimering för din stora pixel – kartor och använder icke-komprimerat format för dina mindre pixel-kartor.

`Include Alpha Channel`Kryss rutan avgör hur GUIX Studio använder information om alpha-kanaler som ibland finns i. png-format indatafiler. Om den här kryss rutan är markerad och visningen körs med 16-BPP färgdjup eller högre, bevarar GUIX Studio hela inkommande alpha-data i utdatafilen. Om den här kryss rutan inte är markerad kommer GUIX att skapa en något mindre utdatafil. Den här utdatafilen kan innehålla genomskinlighet, men innehåller inte fullständig information om alpha-Blender.

`Dither`Kryss rutan instruerar GUIX Studio att använda en avancerad gitter när du konverterar indatabilden för användning med ett lägre färgdjup visas. Rastrering är vanligt vis aktiverat, men kan orsaka större utdatafiler om komprimering används eftersom det kommer att bli färre upprepade bild punkter.

När du har angett alla alternativ som du vill, klickar du på knappen OK för att skapa en ny pixel kart resurs. GUIX Studio läser in avbildnings filen för indata, expanderar den, utför konvertering av färg område och gitter, om du vill omkomprimera data och spara data i GUIX-kompatibelt `GX_PIXELMAP` format. Den nya pixel kartan läggs till i projekt resurserna och görs tillgänglig för det program som ska användas.

Om du vill lägga till en ny pixel kart resurs, från `Pixelmaps` avsnittet av ***vyn resurser*** väljer du följande knapp:

![Lägg till ny pixel – Map-knapp.](./media/guix-studio/image50.jpg)

## <a name="string-resources"></a>Sträng resurser

När sträng gruppen expanderas bör du se en förhands granskning av tabellen med projekt strängar, enligt nedan:

![Skärm bild av den expanderade sträng gruppen.](./media/guix-studio/string_res_view.png)

**Bild 17**

Sträng resurser består av en eller flera strängar, var och en med ett unikt logiskt namn. Till exempel, i **bild 17** , är det logiska namnet "PATIENT_LIST" associerat med strängen "patient lista" som visas till höger. Den här sträng resursen används när programmet anger PATIENT_LIST som sträng i objekt egenskaperna.

Kom alltid ihåg att dina ID-namn för alla resurs typer måste vara C syntax-kompatibla variabel namn. Dessa namn kommer att användas i stor utsträckning när dina projektfiler och specifikationer för projekt skapas av Studio.

Om du vill ändra en sträng resurs dubbelklickar du (eller högerklickar och väljer på menyn) på sträng resursen för att anropa dialog rutan ***sträng tabell redigeraren** _. I dialog rutan _*_sträng tabell redigeraren_*_ kan sträng resursen ändras så att den matchar programmets gränssnitts behov. _*_Bild 18_*_ visar dialog rutan för ändringar när _ *STRING_13** dubbelklickas.

I det här fallet visas sträng-ID-namnet till vänster, vilket sträng innehållet för det första eller referens språket som visas till höger. Självklart är det exakta sträng innehållet särskilt för ditt program, men layouten för förhands granskning av sträng gruppen är konsekvent.

GUIX Studio stöder statisk text och flerspråkiga program genom att definiera och underhålla en sträng tabell. Sträng tabellen definierar ett sträng-ID för varje post och en strängkonstant för varje post för varje språk som stöds.

De språk som ska stödjas av ditt program definieras med hjälp av dialog rutan språk konfiguration, som visas här:

![Skärm bild av dialog rutan språk konfiguration.](./media/guix-studio/config_languages.png)

**Bild 18**

Dialog rutan språk konfiguration anropas med hjälp av konfigurera | Kommandot språk på program-menyn. Med den här dialog rutan kan du definiera antalet språk som ska stödjas av ditt program och det namn eller språk-ID som ska associeras med varje språk. De språk som stöds kan ändras när projektet har skapats, men om ett språk tas bort bör du vara medveten om att sträng data som är associerade med språket också tas bort och inte kan hämtas.

Kryss rutan "**statiskt definierad**" anger att det valda språket ska definieras statiskt i käll kod formatet i den genererade resurs filen. Om inga språk har definierats statiskt anges språk tabell pekaren till NULL i den genererade visnings tabellen och ett språk måste läsas in och installeras av programmet med hjälp av de binära Resource Loader-API: erna som tillhandahålls av GUIX-biblioteket.

Kryss rutan "**stöd för dubbelriktad text**" instruerar GUIX Studio att aktivera stöd för dubbelriktad text åter givning. Du måste aktivera den här kryss rutan om de strängar som du ska ange för det här språket kräver dubbelriktad text åter givning.

Kryss rutan "**generera dubbelriktad text i visnings ordning**" instruerar GUIX Studio att generera dubbelriktad text till utdatafilen i dess visnings ordning. Om det här alternativet är markerat krävs ingen körnings bearbetning i GUIX-biblioteket för att kunna återge dubbelriktad text. När det här alternativet är markerat ska dubbelriktad text åter givning inte aktive ras i GUIX-biblioteket. Den här konfigurationen ger bästa prestanda för körning, men stöder inte åter givning av dynamiskt definierade dubbelriktade text strängar.

Det första språket eller "index 1"-språket kallas "referens språk". Detta är det språk som GUIX Studio använder när du definierar och redigerar användar gränssnitts design. Alla andra språk i din sträng tabell kallas för översättnings språk. GUIX Studio har stöd för export och import av sträng tabell data i standardfilerna för XLIFF-eller CSV-format i bransch standard, bekvämt för att utbyta sträng information med översättare som kan hjälpa programutvecklaren att lägga till översättningar för språk som ska stödjas annat än referens språket. När du exporterar GUIX-sträng tabellen till en XLIFF-eller CSV-fil ingår referens språket tillsammans med ett översättnings språk i XLIFF-eller CSV-strängens data utbytes fil. När du importerar en XLIFF-eller CSV-fil används de importerade data på samma sätt för att fylla ett översättnings språk i GUIX String-tabellen.

![Skärm bild av sträng tabell redigeraren.](./media/guix-studio/image53.jpg)

**Bild 19**

Dialog rutan sträng tabell redigerare visar först en lista med sträng-ID: n till vänster, följt av referens språk sträng data. Om fler än ett språk definieras visar en tredje kolumn något av de översättnings språk som stöds. Du kan öppna och stänga den tredje kolumnen genom att klicka på den lilla pilen längst upp till höger i kolumnen referens språk.

När kolumnen översättnings språk är synlig kan du gå igenom de översättnings språk som finns i projektet genom att klicka på de små pilarna längst upp till höger i kolumnen för översättnings språk i sträng listan.

Du kan redigera en sträng post genom att klicka på posten i tabellen för att markera den. När en post väljs visas post Strängs-ID och sträng innehåll i fälten under tabellvy. Du kan ange nya värden i de här fälten om du vill ändra sträng-ID och sträng innehåll.

I rutan till höger i vyn tabell visas för hands versionerna av widgetar som refererar till den valda strängen. Detta är användbart för att se om en redige rad sträng kommer att överskrida ett särskilt widgets områden.

Fälten till höger om sträng innehållet är:

- "Antal referenser": det här fältet anger hur ofta ett visst sträng-ID används i GUIX Studio-projektet. Om referens antalet är 0 kan den här strängen vara föråldrad och eventuellt tas bort av användaren.
- Sträng bredden (bild punkter) anger visnings bredden för strängen med det angivna teckensnittet.
- Fältet "Anteckningar" är ett valfritt kommentar fält som gör att du kan lägga till information om syftet eller användningen av varje sträng. Dessa anteckningar ingår i exporterade XLIFF-strängens datafiler för att hjälpa översättare att göra korrekta och meningsfulla sträng översättningar.

När du har redigerat dialog rutan för ***sträng tabell*** öppna kan du lägga till ytterligare strängar i projektet genom att klicka på knappen Lägg till sträng överst i dialog rutan. Föråldrade eller oanvända strängar kan tas bort från projektet genom att först markera strängen och sedan klicka på knappen Ta bort sträng överst i dialog rutan.

Förutom att manuellt lägga till nya strängar i ditt projekt med hjälp av dialog rutan sträng tabell redigerare, kan du också lägga till nya strängar som är indirekt genom att skriva sträng innehåll i fältet "text" i egenskapsvyn för alla widgetar som stöder text. Det innebär att när du lägger till nya widgetar i vyn mål eller skriver text information i egenskapsvyn, skapas automatiskt nya poster i tabellen med projekt strängar.

## <a name="adding-language-translations"></a>Lägga till språk översättningar

GUIX Studio sträng tabell Redigeraren stöder ett språk definitions arbets flöde som gör det möjligt för utvecklare att skapa ett program med hjälp av sitt primära språk, och sedan exportera sträng data till en standard schema-XML-eller CSV-fil som ska skickas till en språk översättnings expert. Översättnings filen returneras sedan till utvecklaren, som kan importera språk översättningarna tillbaka till sitt Studio-projekt och därmed lägga till stöd för ett nytt språk i sitt program.

Den här funktionen anropas med hjälp av export (för att skriva sträng data till en fil) och importera (för att läsa de översatta strängarna) knappar överst i sträng tabell redigeraren. Knappen Exportera används för att skapa en XML-eller CSV-fil för XLIFF-scheman som innehåller dina referens språk strängar. Den här filen kan användas av en översättare med verktyg och redigerare som har stöd för standard-eller CSV-filformat.

När en översättnings expert returnerar XLIFF-filen till dig med de nya sträng översättningarna kan du använda knappen Importera för att läsa data från den här XLIFF-eller CSV-filen. Om XLIFF-eller CSV-filen innehåller ett nytt språk läggs det nya språket till i projektet. Om XLIFF-filen innehåller nya sträng data för ett befintligt språk, importeras dessa nya data till projektet. Referens språk strängarna ändras inte av import åtgärden.

När du klickar på Exportera visas dialog rutan för export kontroll i XLIFF/CSV, Visa nedan:

![Skärm bild av dialog rutan export kontroll för XLIFF/CSV.](./media/guix-studio/image54.jpg)

**Bild 20**

I fälten käll språk och mål språk anger du vilka tabell kolumner i strängen som ska skrivas till XLIFF-eller CSV-filen som referens språk och översättnings språk. Käll språket är referens strängarna och mål språket är det språk som översättaren kommer att tillhandahålla översatta sträng data till.

I fältet XLIFF-version anges en av två huvud versioner av XLIFF-filformatet, antingen version 1,2 eller version 2,0 (och senare). Dessa XLIFF-filformat är inkompatibla och du måste veta vilken version dina verktyg använder innan du använder kommandot XLIFF export/import. Mer information om XLIFF-schemat och XLIFF-standarder hittar du här:

- version 1,2: [https://docs.oasis-open.org/xliff/xliff-core/xliff-core.html](https://docs.oasis-open.org/xliff/xliff-core/xliff-core.html)
- version 2,0: [https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0os.pdf](https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0-os.pdf)

Med fälten utdata filename och sökväg för utdata kan du ange det fil namn och den plats som utdatafilen ska skrivas till. Fil namnet är helt upp för användaren, men vi föreslår att du använder namn som anger käll-och mål språk som finns i den exporterade filen.
