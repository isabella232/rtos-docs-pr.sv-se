---
title: Skärm design för GUIX Studio
description: Att utforma program skärmar är det främsta syftet med GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 318e68ab5ab7d841057d65565dfda263597d03e4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826331"
---
# <a name="chapter-5-guix-studio-screen-designer"></a>Kapitel 5: GUIX Studio-skärm designern

Att utforma program skärmar är det främsta syftet med GUIX Studio. Skärm design utförs genom alla de olika vyer som beskrivs ovan i kapitel 3. Huvud delen av skärm design i GUIX Studio är dock ***standardvyn***, där alla skärm element visas visuellt och på exakt samma sätt som de visas på den inbäddade mål visningen. Dessa skärm element kan väljas, flyttas, storleks änd ras osv via enkla mus-och knapp åtgärder. Dessutom är knapparna justering och Z-ordning tillgängliga för valda objekt. I följande underavsnitt beskrivs olika funktioner i GUIX Studio-skärm design. 

## <a name="creatingconfiguring-projects"></a>Skapa/konfigurera projekt

Det är enkelt att skapa projekt i GUIX Studio – du behöver bara klicka på knappen ***nytt projekt** _ eller meny val _*_projektet, nytt projekt_*_. Sedan presenterar GUIX Studio dialog rutan _ *_Konfigurera projekt_**. I den här dialog rutan anges grundläggande visnings inställningar, samt information om sökvägar för var du hittar kod som genererats av GUIX Studio.

När ett nytt projekt skapas visas dialog rutan konfigurera projekt. Det är här som utvecklaren anger hur många maskin varu visningar som är tillgängliga på målet och vilka egenskaper som visas. Egenskaperna inkluderar visnings programmets logiska namn, x/y-upplösning, färgdjup och format och andra visnings egenskaper. GUIX Studio stöder flera skärmar i samma projekt. Om det krävs ytterligare visningar måste fältet ***antal visas** _ ändras för att matcha antalet skärmar på den inbäddade enheten. Det maximala antalet skärmar i ett projekt är 4. _ *_Bild 21_** visar dialog rutan konfigurera projekt.

Att ändra projekt-och/eller visnings inställningarna görs genom att antingen meny alternativet ***Konfigurera, projekt/Visa** _ eller genom att välja projektet eller visningen, högerklicka och välja _*_Konfigurera, projekt/Visa_*_. I båda fallen presenteras dialog rutan _ *_Konfigurera projekt_** för att under lätta ändringar i projekt inställningarna och/eller visnings alternativen.

![Skärm bild av dialog rutan konfigurera projekt.](./media/guix-studio/config_project.png)

**Bild 21**

I gruppen kataloger kan du ange standardutdata-kataloger för C-käll-och Huvudfilerna som produceras av Studio. Dessa kataloger sparas vanligt vis i förhållande till projekt platsen för att göra det enkelt att flytta projekt från en dator till en annan eller från ett fil system till ett annat.

I fältet ytterligare rubriker kan du ange anpassade meddelandehuvuden. Om fler än en rubrik fil behövs använder du semikolon för att avgränsa listan.

När du anropar kommandona Studio "generera program" eller "generera resurser" är dessa de standard kataloger som källfilerna skrivs till. Naturligtvis kan du när som helst åsidosätta dessa katalog platser genom att ange nya platser i dialog rutan utmatnings katalog.

## <a name="selecting-widgets"></a>Välja widgetar

Du väljer widgetar genom att antingen klicka på widgeten i ***projektvyn**, i widgeten i vyn * projektvyn eller genom att klicka på widgeten synlig i _*_mål visnings_*_ ytan. När en enskild widget väljs visas dess egenskaper i _*_egenskaps visnings_*_ ytan. _*_Bild 22_*_ visar widgeten "_ *_Button_* *" vald.

![Skärm bild av den valda widgeten.](./media/guix-studio/select_button.png)

**Bild 22**

## <a name="using-properties"></a>Använda egenskaper

Som tidigare nämnts visas egenskaperna för en vald widget i ***egenskapsvyn Visa** _. Alla widgetar har en gemensam uppsättning egenskaper samt vissa egenskaper som är specifika för den aktuella widgeten. En knapp widget har till exempel egenskapen _ *_pushd_** medan en fönster-widget inte gör det. Följande är en gemensam uppsättning egenskaper för widget:

| Egenskap         | Innebörd                                                                               |
| ---------------- | ------------------------------------------------------------------------------------- |
| Typ av widget    | Typ av widget, som referens                                                                               |
| Namn på widget      | Namnet på widgeten skickades till funktionen Skapa widget och används för variabel namngivning i de genererade källfilerna.               |
| Widgets-ID        | ID för widgeten. Detta ID-värde används för att generera signaler från underordnade widgetar till sina överordnade skärmar.                            |
| Vänster             | Längst till vänster-koordinaten för widgeten                                                                                                 |
| Överkant              | Topp-koordinaten för widgeten                                                                                                  |
| Bredd            | Bredd på widgeten i bild punkter                                                                                                      |
| Höjd           | Widgetens höjd i bild punkter                                                                                                     |
| Kantlinje           | Typ av widget-kantlinje                                                                                                          |
| Genomskinlig      | Bör kontrol leras om widgeten är delvis transparent                                                                       |
| Rita valt    | Bör kontrol leras om widgeten först ska rita sig själv i det valda läget.                                            |
| Aktivera           | Bör kontrol leras om widgeten kan väljas eller klickas av slutanvändaren.                                                    |
| Accepterar fokus    | Bör kontrol leras om widgeten accepterar fokus.                                                                                 |
| Runtime-allokering | Bör kontrol leras om widgeten kontroll block ska tilldelas dynamiskt.                                                 |
| Normal fyllning      | Resurs-ID för normal fyllnings färg                                                                                                  |
| Vald fyllning    | Resurs-ID för vald fyllnings färg                                                                                                |
| Rita funktion    | Användardefinierat namn för anpassad ritnings funktion. Om det här fältet är tomt används standard ritnings funktionen för widgeten. |
| Händelse funktion   | Användardefinierat namn för anpassad händelse hanterings funktion. Om detta är tomt används standard händelse hanteringen för denna widget.          |

***Bild 23*** visar egenskaperna för en enkel fönster-widget.

![Skärm bild av egenskaperna för en enkel fönster-widget.](./media/guix-studio/image57.jpg)

**Figur 23**

Många typer av widgetar har ytterligare egenskaper som är speciella för varje widget.

I Figur 23 ovan stöder till exempel fönster-widgeten typ av Skriv bords Pixelmap-ID och en format inställning som anger om Skriv bords underlägget ska centreras eller placeras sida vid sida.

Text-widgetar har stöd för ett sträng-ID-fält, tillsammans med text justerings format och en teckensnitts specifikation. De ytterligare egenskaperna i widgeten är vanligt vis intuitiva när du har läst beskrivningen av varje widget och de tillgängliga formaten och skapar funktions parametrar för widgeten.

## <a name="manipulating-widgets"></a>Ändra widgetar

Om du vill ändra en widget måste du först markera den. Detta görs genom att antingen klicka direkt på widgeten i ***target-vyn** _ eller genom att markera den i vyn _ *_projektvyn_** i widgeten. När den har valts får widgeten en streckad kontur. I det här läget kan den flyttas genom att du bara klickar på widgeten och drar den till önskad plats på den överordnade platsen. Om widgeten är en widget på översta nivån, ställer du in widgetens första position på mål skärmen genom att dra widgeten. Naturligtvis är det alltid möjligt att flytta eller ändra storlek på alla widgetar när som helst med hjälp av GUIX-API: et.

Om du vill ändra storlek på widgetens höjd placerar du musen på den övre kanten av widgeten och väntar tills mus pekaren ändras till en UPPIL. Nu kan du ändra widgetens höjd genom att helt enkelt flytta musen medan den högra mus knappen är nedtryckt. Bredden på musen kan ändra storlek på liknande sätt genom att placera mus pekaren på den vänstra kanten av widgeten. ***Bild 24** _ visar widgeten "_ *_Button_* *" och har storleksändrats och flyttats till vänster/övre yta i det överordnade fönstret.

![Skärm bild av knapp-widgeten.](./media/guix-studio/resize_button.png)

**Bild 24**

## <a name="manipulating-multiple-widgets"></a>Ändra flera widgetar

Du kan välja flera widgetar genom att klicka på flera widgetar i vyn mål samtidigt som du håller ned ***CTRL*** -tangenten. Då visas var och en av de widgetar som har marker ATS med en streckad kontur runt den. Observera att när du väljer flera widgetar varje widget i urvals gruppen måste ha ett underordnat objekt till samma överordnade.

När du har valt flera widgetar kan de flyttas samtidigt genom att klicka inuti en på de valda widgetarna och flytta musen med höger musknapp nedtryckt. Dessutom kan justerings knapparna i *-**verktygsfältet** användas för att justera gruppen med valda widgetar. I _*_bild 25_*_ visas widgetarna "_*_knapp_*_" och "_*_ny knapp_*_" markerade och _*_bild 26_*_ visar resultatet av alternativet _ *_Justera-vänster_** och när dessa widgetar är markerade.

![Skärm bild av widgeten knapp och ny knapp som valts](./media/guix-studio/multiple_select.png)

**Bild 25**

![Skärm bild av resultatet av knappen Align-Left.](./media/guix-studio/align_left.png)

**Bild 26**

## <a name="cutcopypaste-operations"></a>Åtgärder för att klippa ut/kopiera/klistra in

En vald widget i ***target-vyn** _ kan klippas ut, kopieras och klistras in som standard. Widgetar och skärmar kan kopieras i ett projekt eller kopieras från ett projekt och klistras in i ett annat. _*_Verktygsfältet_*_ innehåller knappar för klipp ut, kopiera och klistra in. Det finns också samma alternativ i meny alternativet Redigera. Observera att när du klistrar in en widget bör den överordnade widgeten väljas innan du klistrar in den nya widgeten. _*_Bild 27_*_ visar resultatet av att välja widgeten "_ *_Button_* *", kopiera den och klistra in kopian i samma fönster.

![Skärm bild av åtgärderna klipp ut/kopiera/klistra in.](./media/guix-studio/copy_paste_button.png)

**Bild 27**

Kopiera/klistra in i ett projekt är i allmänhet enkelt att de resurser som kan krävas av de kopierade widgetarna alltid är tillgängliga när du arbetar i ett projekt. Men om du kopierar en widget från projekt A och klistrar in widgeten i Project B kan vissa problem med resurs beroenden uppstå.

När du kopierar widget (er) i Studio, gör Studio-programmet en lista över de resurser som krävs av de kopierade widgetarna och genererar en portabel resurs beroende tabell i XML-format som kopieras till Urklipp i Windows, tillsammans med den faktiska kopierade informationen om widgeten. När du klistrar in widgeten i ett annat projekt undersöker Studio först resurs beroende listan och lägger till nödvändiga resurser i det öppna projektet om de inte redan finns. Studio identifierar matchande resurser med resurs-ID-namnen och för sträng resurser jämförs även sträng innehållet. Om matchande resurser hittas uppdaterar Studio resurs-ID för de inklistrade widgetarna för att kunna använda resurserna i det nya projektet. Om resurserna inte hittas läggs de till.

När Studio lägger till en resurs i projektet som en del av en widget för att klistra in, lägger Studio i själva verket till en länk till resursen när det gäller teckensnitts-och Pixelmap resurser. Den här länken genereras från käll projektet och du får varnings meddelanden om dessa resurser inte finns i förhållande till projekt platsen för projektet som du klistrar in i. Resurs länkarna läggs till i projektet oberoende av, men du kan behöva kopiera teckensnitt och bildfiler manuellt till rätt platser under det nya projekt trädet för att eliminera resurs inläsnings fel. Studio kopierar inte. ttf-,. png-eller. jpg-filer från en plats till en annan.

Det enkla sättet att undvika problem i detta hänseende är att behålla en konsekvent katalog struktur mellan projekt som du vill dela. Om du enkelt vill flytta saker från Project A till Project B, behåller du bilder och teckensnitt som används av båda projekten i en konsekvent under katalog för varje projektmapp.

## <a name="changing-z-order"></a>Ändra Z-ordning

Widgetar kan enkelt flyttas framför eller bakom andra widgetar. Detta åstadkommer du genom att välja widgeten och välja antingen ***Flytta till** start _ eller _*_Flytta till bak_*_ -knapparna i _*_verktygsfältet_*_. _ *_Bild 28_** visar knappen flytta den andra till föregående.

![Skärm bild av knappen z-ordning.](./media/guix-studio/change_z_order.png)

**Bild 28**

## <a name="assigning-colors-fonts-and-pixelmaps"></a>Tilldela färger, teckensnitt och Pixelmaps

Förutom att välja färger, teckensnitt och pixelmaps i egenskapsvyn för en vald widget, stöds också ett stenografiska drag-och-släpp-metod för att tilldela resurser till widgetar. Om du vill använda den här funktionen, vänsterklickar du bara på en resurs, till exempel en färg på teckensnittet i resursvyn och drar resursen över önskad widget i vyn mål. Släpp resursen genom att släppa den vänstra mus knappen över widgeten.

Färg resurser tilldelas alltid widgeten normal bakgrunds färg när du använder dra och släpp-metoden. Andra färger som vald färg eller markerad textfärg måste tilldelas med egenskapsvyn.

På samma sätt tilldelas Pixelmap-resurser fältet "normal" eller "Fill" i en widget som stöder Pixelmap-visning. Om du vill tilldela andra fält till en widget som stöder flera pixelmaps måste du använda egenskapsvyn.

## <a name="using-templates"></a>Använda mallar

En skärm eller samling av underordnade widgetar som du utformar i Studio kan användas som mall för nya skärmar och nya underordnade kontroller. Att använda en mall är liknande att kopiera och klistra in en widget, förutom att allt som härletts från en mall ändras automatiskt när mallen som den baseras på ändras. Du får inte ändra egenskaperna för mallens widget när du arbetar med en härledd skärm eller ärvd instans av mallen. Men när du ändrar mallens egenskaper på något sätt uppdateras alla instanser som refererar till mallen automatiskt, eftersom de härleds från mallen.

En annan fördel med att använda mallar för upprepade objekt är att filen med Studio-genererade specifikationer vanligt vis är mindre i storlek än om du återskapar de upprepade objekten varje gång de används.

Om du vill ange att en skärm eller samling av underordnade widgetar ska användas som mall, aktiverar du kryss rutan "mall" i vyn Egenskaper för widgeten. När du har aktiverat kryss rutan mall visas mallens widget i ***Infoga | Mallens*** List meny (er).

Som ett exempel på hur du använder en mall kan du definiera ett fönster som används som ett knapp fält. Det här fönstret kan innehålla flera underordnade knappar och det här knapp fältet används ofta på olika skärmar. Du kan definiera ett litet fristående fönster i Studio-projektet som innehåller de underordnade knapparna som krävs, och ge fönstret namnet "button_bar". Välj sedan det här fönstret och aktivera egenskapen "mall". Välj sedan en skärm som du vill lägga till det här knapp fältet på. Använd infoga | Mall | button_bar meny kommando för att infoga en instans av button_bars fönstret på skärmen. Observera att du kan flytta knapp fältet, men du har inte behörighet att ändra de flesta egenskaperna. Du kan dock använda widgeten button_bar (och alla underordnade) precis som andra fördefinierade widgetar av typen GUIX. Om du vill ändra button_bar måste du välja button_bars mal len för att göra dina ändringar.

Ett annat exempel på en typisk mall användning är ett program som innehåller många liknande skärmar. Programmet kan till exempel ha 10 olika skärmar som alla delar en gemensam namn List, fyllnings färg, storlek osv. I det här fallet kan du definiera en mall som innehåller dina underordnade widgetar för namn list och konfigurerar skärm storlek, fyllnings färg och andra egenskaper. När den här mallens skärm har definierats kan du sedan härleda dina 10 olika skärmar från den här mallen. När du använder Infoga | Mall | \<base_screen> meny kommandot kommer skärmen att börja visas med alla underordnad widget och inställningar för din mall-skärm. Observera att varje skärm som du härleder från mallens skärm inte är en kopia av mallen, men är verkligen en härledd instans av mallens skärm. Du kan sedan anpassa varje härledd skärm så att den innehåller allt ytterligare innehåll som krävs.

Observera att förutom att spara storleken på filen med de genererade specifikationerna kan du göra det enklare att hantera ändringar i programmets utseende med hjälp av mallar. I exemplet ovan antar vi att du måste ändra bakgrunds färgen för dina 10 liknande skärmar. I stället för att behöva välja varje skärm och ändra fyllnings färg inställningarna behöver du bara välja bas mal len och ändra fyllnings färgen, så kommer den här ändringen att visas direkt i alla härledda skärmar.

Ytterligare en kommentar om mallar: du måste se till att flödet för händelse bearbetning upprätthålls, vilket innebär att om du anger en händelse hanterare för både en grundläggande skärm (för att hantera vanliga widgets händelser) och för en härledd skärm, bör händelse hanteraren för härledd skärm anropa base_screen händelse hanteraren i standard fallet. På så sätt kan händelse hanteraren på grund skärmen bearbeta händelser som genererats av widgetar som är gemensamma för alla skärmar som härleds från den här mall basen.

## <a name="record-and-playback-macro"></a>Spela in och spela upp makro

Med makro inspelnings-och uppspelnings funktioner kan du registrera och spela upp tangent nedslag och mus händelser.

Du kan spela in till en makro fil genom att välja knappen ***spela in makro** _ _ verktygsfält eller menyn och välja _*_Redigera, spela in makro_*_. GUIX Studio visar dialog rutan _*_spela in makro_*_ som gör att du kan ange sökvägen till makro filen. När du har gjort det här valet klickar du på knappen _*_spela in_*_ för att starta inspelningen. När du är klar med inspelningen väljer du knappen _*_spela in makro_*_ i verktygsfältet eller använder den nedrullningsbara menyn och väljer _ *_Redigera, avsluta makro_** för att avsluta makro inspelningen.

Uppspelning av en makro fil görs genom att klicka på knappen ***uppspelnings makrot** _ med hjälp av den huvudsakliga nedrullningsbara menyn för att välja kommandot _*_Redigera, spela upp makro_*_ . GUIX Studio visar dialog rutan _ *_uppspelnings makro_** som gör att du kan ange den tidigare inspelade makro filen som ska köras.

När du registrerar makron som väljer indata-eller utdatafiler, till exempel att lägga till ett teckensnitt eller en bild, är det viktigt att använda tangent bordet för att skriva fil namnet, i stället för att använda musen för att välja från fil läsaren. Eftersom makro inspelningen registrerar mus-och tangent bords händelser, och eftersom fil läsaren kan ändras med tiden, är det mer tillförlitligt att ange fil namnet än att välja filen grafiskt.

## <a name="zooming-target-view"></a>Zooma vyn mål

Funktionen zooma in hjälper dig att få en närbild av mål skärmen.

Du kan välja den procentuella zoomnings inställningen som du vill ha i ***Konfigurera | Mål visning |** Meny alternativet zooma _. *_Verktygsfältet_* _ _ * innehåller också knappar för att zooma in och ut.

## <a name="gridsnap-settings"></a>Inställningar för rutnät/Snap

Dialog rutan ***Grid och Snap Settings** _ innehåller vissa inställningar och alternativ för rutnät och fäst. _*_Bild 29_*_ visar dialog rutan för _*_Rutnäts-och Snap-inställningar_*_ när menyn _ *_Congigure | Mål visning | Grid/Snap_** är markerat.

![Skärm bild av inställningarna för rutnät och fäst.](./media/guix-studio/image63.jpg)

**Bild 29**

Aktivera * alternativet för att **Visa rutnät** _ visar rutnät på mål skärmen. du kan ange ökning av rutnät (i bild punkter) i fältet _*_Rutnäts avstånd_*_ . Alternativet _ *_Fäst mot rutnät_** hjälper dig att få rätt position en widget, aktivera det här alternativet aktive ras.

När ***rutnät och fäst*** alternativ är aktiverat:

- Om du drar ett objekt med musen i vyn mål flyttas objektet genom att öka rutnätet.
- Om du drar kanten på ett objekt för att ändra storlek fästs kanten som du drar till rutnäts läget.
- Om du väljer ett objekt och använder upp-/vänster-/ned-/till höger-nycklar flyttas den valda widgeten med hjälp av Snap-steg. du kan ange öknings ökningen (i bild punkter) i fältet ***Snap-avstånd*** .
