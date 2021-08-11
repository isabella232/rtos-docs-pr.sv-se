---
title: GUIX Studio-skärmdesigner
description: Design av programskärmar är det primära syftet med GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d7a4ffca7d49a82b75ed756fc360a2f543faa8a9fe9d31e5a5ace39087c96568
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785789"
---
# <a name="chapter-5-guix-studio-screen-designer"></a>Kapitel 5: GUIX Studio-skärmdesigner

Design av programskärmar är det primära syftet med GUIX Studio. Skärmdesignen åstadkoms genom alla de olika vyer som beskrivs tidigare i kapitel 3. Huvudelementet i skärmdesignen i GUIX Studio är dock målvyn ***,*** där alla skärmelement visas visuellt och på exakt samma sätt som de visas på den inbäddade målskärmen. Dessa skärmelement kan väljas, flyttas, ändra storlek osv. via enkla mus- och knappåtgärder. Dessutom är knappåtgärderna justering och Z-ordning tillgängliga för valda objekt. I följande underavsnitt beskrivs olika funktioner i GUIX Studio-skärmdesignen. 

## <a name="creatingconfiguring-projects"></a>Skapa/konfigurera projekt

Det är enkelt att skapa projekt i GUIX Studio . Välj bara knappen ***Nytt Project** _ eller menyvalet _*_Project, Ny Project_*_. Därefter visar GUIX Studio dialogrutan _ *_Konfigurera Project_** . I den här dialogrutan anges grundläggande visningsinställningar samt sökvägsinformation för var du hittar kod som genererats av GUIX Studio.

När ett nytt projekt skapas visas dialogrutan Konfigurera projekt. Här anger utvecklaren hur många maskinvaruenheter som visas på målet och vilka egenskaper som visas. Egenskaperna omfattar visningens logiska namn, x/y-upplösning, färgdjup och format och andra visningsegenskaper. GUIX Studio stöder flera skärmar i samma projekt. Om ytterligare visningar krävs bör fältet ***Antal visningar** _ ändras så att det matchar antalet visningar på den inbäddade enheten. Det maximala antalet visningar i ett projekt är 4. _ *_Bild 21_** visar dialogrutan Project konfigurationsinställningar.

Du ändrar inställningarna för projektet och/eller visningen genom att antingen menyalternativet ***Konfigurera, Project/Display** _ eller genom att välja projektet eller visningen, högerklicka och välja _*_Konfigurera, Project/Visa._*_ I båda fallen visas dialogrutan _ *_Konfigurera Project_** för att underlätta ändringar av projektinställningar och/eller visning.

![Skärmbild av dialogrutan Project konfigurationsinställningar.](./media/guix-studio/config_project.png)

**Bild 21**

I gruppen Kataloger kan du ange standardkatalogerna för utdata för C-käll- och huvudfiler som skapas av Studio. Dessa kataloger sparas normalt i förhållande till projektplatsen för att göra det enkelt att flytta projekt från en dator till en annan eller från ett filsystem till ett annat.

I fältet Ytterligare rubriker kan du ange anpassade rubrikfiler. Om du behöver mer än en huvudfil använder du semikolon för att avgränsa listan.

När du anropar kommandona "Generera program" eller "Generera resurser" i Studio är dessa standardkataloger som källfilerna ska skrivas till. Naturligtvis kan du åsidosätta dessa katalogplatser när som helst genom att ange nya platser i dialogrutan Utdatakatalog.

## <a name="selecting-widgets"></a>Välja widgetar

Du väljer widgetar genom att antingen klicka på widgeten i trädet ***Project Visa** _ widget eller genom att klicka på widgeten som visas i _*_området Målvy._*_ När en enskild widget har valts visas dess egenskaper i området _*_Egenskapsvy._*_ _*_Bild 22 visar_*_ widgeten "_*_knappen_**" vald.

![Skärmbild av den valda widgeten.](./media/guix-studio/select_button.png)

**Bild 22**

## <a name="using-properties"></a>Använda egenskaper

Som tidigare nämnts visas egenskaperna för en vald widget i ***Egenskapsvy** _. Alla widgetar har en gemensam uppsättning egenskaper samt vissa egenskaper som är specifika för den specifika widgettypen. En knappwidget har till exempel egenskapen _ *_Push-push_** medan en fönsterwidget inte har det. Följande är den vanliga uppsättningen widgetegenskaper:

| Egenskap         | Innebörd                                                                               |
| ---------------- | ------------------------------------------------------------------------------------- |
| Widgettyp    | Typ av widget, som referens                                                                               |
| Widgetnamn      | Namnet på widgeten, som skickas till widgetens create-funktion och används för variabelnamngivning i de genererade källfilerna.               |
| Widget-ID        | ID för widget. Det här ID-värdet används för att generera signaler från underordnade widgetar till sina överordnade skärmar.                            |
| Vänster             | Widgetens vänstra koordinat                                                                                                 |
| Överkant              | Översta koordinaten för widgeten                                                                                                  |
| Bredd            | Bredden på widgeten i bildpunkter                                                                                                      |
| Höjd           | Widgetens höjd i bildpunkter                                                                                                     |
| Kantlinje           | Typ av widgetkantlinje                                                                                                          |
| Genomskinlig      | Bör kontrolleras om widgeten är delvis transparent                                                                       |
| Rita valda    | Bör kontrolleras om widgeten ursprungligen ska rita sig själv i det valda tillståndet.                                            |
| Aktivera           | Bör kontrolleras om widgeten kan väljas eller klickas av slutanvändaren.                                                    |
| Accepterar fokus    | Bör kontrolleras om widgeten accepterar fokus.                                                                                 |
| Allokera körning | Bör kontrolleras om widgetkontrollblocket ska allokeras dynamiskt.                                                 |
| Normal fyllning      | Resurs-ID för normal fyllningsfärg                                                                                                  |
| Vald fyllning    | Resurs-ID för markerad fyllningsfärg                                                                                                |
| Draw-funktion    | Användardefinierad anpassad ritningsfunktionsnamn. Om det här fältet är tomt används standardritningsfunktionen för den widgettypen. |
| Händelsefunktion   | Funktionsnamn för användardefinierad anpassad händelsehantering. Om det är tomt används standardhändelsehanteringen för den här widgettypen.          |

***Bild 23 visar*** egenskaperna för en enkel fönsterwidget.

![Skärmbild av egenskaperna för en enkel fönsterwidget.](./media/guix-studio/image57.jpg)

**Bild 23**

Många widgettyper har ytterligare egenskaper som är specifika för varje widgettyp.

I bild 23 ovan stöder till exempel widgettypen Fönster ett pixelkarta-ID för bakgrundsbild och en formatinställning som anger om skrivbordsunderlägget ska centreras eller vara panelerat.

Textwidgetar stöder ett sträng-ID-fält, tillsammans med textjusteringsformat och en teckensnittsspecifikation. De ytterligare widgetegenskaperna är vanligtvis mycket intuitiva när du har läst beskrivningen av varje widgettyp och tillgängliga format och skapa funktionsparametrar för den widgettypen.

## <a name="manipulating-widgets"></a>Manipulera widgetar

Om du vill ändra en widget måste du först markera den. Det gör du genom att antingen klicka direkt på widgeten i ***** Målvy _ eller genom att välja den i widgetträdet _ *_Project Visa_** . När widgeten har valts får den en streckad kontur. I det här tillståndet kan den flyttas genom att helt enkelt klicka på widgeten och dra den till önskad plats på dess överordnade plats. Om widgeten är en widget på den översta nivån, ställer du effektivt in widgetens inledande position på målskärmen genom att dra widgeten. Naturligtvis är det alltid möjligt att flytta eller ändra storlek på en widget när som helst med hjälp av GUIX-API:et.

Om du vill ändra storlek på widgetens höjd placerar du musen på widgetens övre kant och väntar på att muspekaren ändras till en uppåtpil. I det här läget kan widgetens höjd ändras genom att helt enkelt flytta musen medan höger musknapp är nedtryckt. Musens bredd kan ändras på liknande sätt genom att placera muspekaren på widgetens vänstra kant. ***Bild 24** _ visar att widgeten "_*_**"_ har ändrat storlek och flyttats till vänster/övre delen av det överordnade fönstret.

![Skärmbild av knappwidgeten.](./media/guix-studio/resize_button.png)

**Bild 24**

## <a name="manipulating-multiple-widgets"></a>Manipulera flera widgetar

Du kan välja flera widgetar genom att klicka på flera widgetar i målvyn samtidigt som du håller Ned Ctrl-tangenten.  Om du gör detta visas var och en av widgetarna som valts med en streckad kontur runt den. Observera att när du väljer flera widgetar måste varje widget i urvalsgruppen vara underordnad samma överordnade.

När flera widgetar har valts kan de flyttas samtidigt genom att klicka inuti en på de valda widgetarna och flytta musen med höger musknapp nedtryckt. Dessutom kan justeringsknapparna i ***Verktygsfältet** _ användas för att justera gruppen med valda widgetar. _*_Bild 25_*_ visar _*_både widgetarna_*_" knapp " och _*_"ny_*_ knapp" valda och bild _*_26_*_ visar resultatet av knappvalet _ *_Align-Left_** medan dessa widgetar är markerade.

![Skärmbild av knappen och nya knappwidgetar valda](./media/guix-studio/multiple_select.png)

**Bild 25**

![Skärmbild av resultatet av Align-Left knappval.](./media/guix-studio/align_left.png)

**Bild 26**

## <a name="cutcopypaste-operations"></a>Klipp ut/kopiera/klistra in

En vald widget i ***Målvy** _ kan klippas ut, kopieras och klistras in på standard sätt. Widgetar och skärmar kan kopieras i ett projekt eller kopieras från ett projekt och klistras in i ett annat. _*_Verktygsfältet_*_ har knappar för klipp ut, kopiera och klistra in. Det finns också samma alternativ i menyalternativet Redigera. Observera att när du klistrar in en widget bör den överordnade widgeten väljas innan du klistrar in den nya widgeten. _*_Bild 27_*_ visar resultatet av att välja widgeten "_*_knapp_**" och kopiera den och klistra in kopian i samma fönster.

![Skärmbild av åtgärderna klipp ut/kopiera/klistra in.](./media/guix-studio/copy_paste_button.png)

**Bild 27**

Kopiera/klistra in i ett projekt är vanligtvis enkelt eftersom de resurser som kan krävas av den kopierade widgeten alltid finns när du arbetar i ett projekt. Men om du kopierar en widget från projekt A och klistrar in widgeten i projekt B kan det uppstå problem med resursberoenden.

När du kopierar widgetar i Studio skapar Studio-programmet en lista över de resurser som krävs av de kopierade widgetarna och genererar en portabel resursberoende tabell i form av XML som kopieras till Urklipp, tillsammans med den faktiska kopierade widgetinformationen. När du klistrar in widgetarna i ett annat projekt undersöker Studio först listan över resursberoenden och lägger till nödvändiga resurser i det öppna projektet om de inte redan finns. Studio identifierar matchande resurser efter resurs-ID-namn, och för strängresurser jämför Studio även stränginnehållet. Om matchande resurser hittas uppdaterar Studio resurs-ID:erna för de klistrade widgetarna så att resurserna i det nya projektet används korrekt. Om resurserna inte hittas läggs de till.

När Studio lägger till en resurs i projektet som en del av en widgetklistringsåtgärd lägger Studio verkligen till en länk till resursen när det gäller teckensnitts- och pixelkarta-resurser. Den här länken genereras från källprojektet och du får varningsmeddelanden om dessa resurser inte kan hittas i förhållande till projektplatsen för projektet som du klistrar in i. Resurslänkarna läggs till i projektet oavsett, men du kan behöva kopiera teckensnitt och bildfiler manuellt till rätt platser under det nya projektträdet för att undvika resursbelastningsfel. Studio kopierar inte .ttf-, .png- eller .jpg filer från en plats till en annan.

Det enkla sättet att undvika problem i detta avseende är att hålla en konsekvent katalogstruktur mellan projekt som du vill dela. Om du enkelt vill flytta saker från Project A till Project B behåller du de grafikbilder och teckensnitt som används av båda projekten i en konsekvent underkatalog för varje projektmapp.

## <a name="changing-z-order"></a>Ändra Z-ordning

Widgetar kan enkelt flyttas framför eller bakom andra widgetar. Detta åstadkoms genom att välja widgeten och antingen knapparna ***Flytta** till front _ eller Flytta till _*_bakåt_*_ i _*_verktygsfältet._*_ _ *_Bild 28_** visar att den andra knappen flyttas bakåt.

![Skärmbild av knappen z-order.](./media/guix-studio/change_z_order.png)

**Bild 28**

## <a name="assigning-colors-fonts-and-pixelmaps"></a>Tilldela färger, teckensnitt och pixelkartor

Förutom att välja färger, teckensnitt och pixelkartor i egenskapsvyn för en vald widget, stöds även en kort dra och släpp-metod för att tilldela resurser till widgetar. Om du vill använda den här funktionen vänsterklickar du bara på en resurs, till exempel en teckenfärg i resursvyn, och drar resursen över den önskade widgeten i målvyn. Släpp resursen genom att släppa den vänstra musknappen över widgeten.

Färgresurser tilldelas alltid till widgetens normala bakgrundsfärg när du använder dra och släpp-metoden. Andra färger, till exempel markerad färg eller markerad textfärg, måste tilldelas med hjälp av egenskapsvyn.

På samma sätt tilldelas pixelkarta-resurser till pixelkartans "normala" eller "fyllnings"-fält för en widget som har stöd för pixelkartans visning. Om du vill tilldela andra fält till en widget som stöder flera pixelkartor måste du använda egenskapsvyn.

## <a name="using-templates"></a>Använda mallar

Alla skärmar eller samlingar med underordnade widgetar som du utformar i Studio kan användas som en mall för nya skärmar och nya underordnade kontroller. Du kan basera en mall på en Windows-typwidget, vilket är det normala användningsfallet eller andra widgettyper. Att använda en mall liknar att kopiera och klistra in en widget, förutom att allt som härletts från en mall ändras automatiskt när mallen som den baseras på ändras. Du kan inte ändra egenskaperna för mallwidgeten när du arbetar med en härledd skärm eller en ärvd instans av mallen. När du ändrar mallegenskaperna på något sätt uppdateras dock alla instanser som refererar till mallen automatiskt, eftersom de härleds från mallen.

En annan fördel med att använda mallar för upprepade objekt är att studiogenererade specifikationsfilen vanligtvis är mindre än om du återskapar de upprepade objekten varje gång de används.

Om du vill ange att en skärm eller en samling underordnade widgetar ska användas som en mall aktiverar du kryssrutan "Mall" i widgetens egenskapsvy. När du aktiverar kryssrutan "Mall" visas mallwidgeten i ***Infoga| Ned*** pull-meny(er) för mallar.

Som ett exempel på hur du använder en mall kan du definiera ett fönster som används som ett knappfält. Det här fönstret kan innehålla flera underordnade knappar och det här knappfältet används ofta på olika skärmar. Du kan definiera ett litet fristående fönster i Studio-projektet som innehåller de underordnade knappar som krävs och ge det här fönstret namnet "button_bar". Välj sedan det här fönstret och aktivera egenskapen "Mall". Välj sedan en skärm där du vill lägga till det här knappfältet. Använd Infoga| Mall|button_bar för att infoga en instans av button_bar på skärmen. Observera att du kan flytta knappfältet, men du kan inte ändra de flesta egenskaper. Du kan dock använda button_bar widget (och eventuella underordnade) precis som andra fördefinierade GUIX-widgettyper. Om du vill button_bar mallen måste du välja button_bar mallen för att göra dina ändringar.

Ett annat exempel på en typisk mallanvändning är ett program som innehåller många liknande skärmar. Programmet kan till exempel ha 10 olika skärmar som alla delar en gemensam namnlist, fyllningsfärg, storlek osv. I det här fallet kan du definiera en mallskärm som innehåller underordnade widgetar i namnlisten och konfigurerar skärmstorlek, fyllningsfärg och andra egenskaper. När den här mallskärmen har definierats kan du härleda dina 10 olika skärmar från den här mallen. När du använder Infoga| Mall| \<base_screen> menykommando börjar skärmen med alla underordnade widgetar och inställningar på mallskärmen. Observera att varje skärm som du härleder från mallskärmen inte är en kopia av mallen, utan är en härledd instans av mallskärmen. Du kan sedan anpassa varje härledd skärm så att den innehåller det ytterligare innehåll som krävs.

Observera att förutom att spara storlek på den genererade specifikationsfilen kan användningen av mallar göra det enklare att hantera ändringar i programmets utseende. I exemplet ovan antar vi att du måste ändra bakgrundsfärgen på dina 10 liknande skärmar. I stället för att behöva markera varje skärm och ändra inställningarna för fyllningsfärg behöver du bara välja basmallen och ändra dess fyllningsfärg. Den här ändringen återspeglas omedelbart i alla härledda skärmar.

Ytterligare en kommentar om mallar: du måste försäkra dig om att händelsebearbetningsflödet upprätthålls, vilket innebär att om du anger en händelsehanterare för både en basskärm (för hantering av vanliga widgethändelser) och för en härledd skärm, bör händelsehanteraren för härledd skärm anropa base_screen-händelsehanteraren i standardfallet. Detta gör att basskärmens händelsehanterare kan bearbeta händelser som genereras av widgetar som är gemensamma för alla skärmar som härletts från den här mallbasen.

## <a name="record-and-playback-macro"></a>Spela in och spela upp makro

Funktionerna för makropost och uppspelning hjälper dig att spela in och spela upp tangenttryckningar och mushändelser.

Du kan spela in till en makrofil genom att välja verktygsfältsknappen ***Spela** in makro _ eller på menyn som _*_väljer Redigera, Spela in makro._*_ GUIX Studio visar dialogrutan _*_Spela in makro_*_ där du kan ange sökvägen till makrofilen. När du har gjort det här valet klickar du _*_på knappen_*_ Spela in för att börja spela in. När du är klar med _**_ inspelningen väljer du återigen verktygsfältsknappen Spela in makro eller använder den nedströmsmeny som väljer _ *_Redigera,_* Avsluta makro * för att avsluta makroinspelning.

Uppspelning av en makrofil sker genom att välja verktygsfältsknappen ***Spela** upp makro _ med hjälp av huvudmenyn för att välja kommandot _*_Redigera, Spela upp makro._*_ GUIX Studio visar dialogrutan _ *_Spela upp makro_** där du kan ange den tidigare inspelade makrofilen som ska köras.

När du spelar in makron som väljer indata- eller utdatafiler, till exempel att lägga till ett teckensnitt eller en bild, är det viktigt att använda tangentbordet för att skriva filnamnet i stället för att använda musen för att välja från filwebbläsaren. Eftersom makroinspelaren registrerar mus- och tangentbordshändelser, och eftersom filwebbläsaren kan ändras med tiden, är det mer tillförlitligt att skriva filnamnet än att välja filen grafiskt.

## <a name="zooming-target-view"></a>Zoomning av målvy

Funktionen Zooma in hjälper dig att få en närbild av målskärmen.

Du kan välja den inställning för procentandel zoomning som du vill använda i ***Konfigurera| Målvy| Zoom** _ menyalternativet . _ Verktygsfältet **_har_* även knappar för att zooma in/ut.

## <a name="gridsnap-settings"></a>Rutnät/fäst Inställningar

Dialogrutan ***Rutnät och fäst Inställningar** _ innehåller vissa inställningar och alternativ för rutnät och fäst. _*_Bild 29_*_ visar dialogrutan _*_Rutnät och Fästinställning_*_ när menyn _ *_Congigure| Målvy| Rutnät/Fäst_** har valts.

![Skärmbild av rutnätet och fäst Inställningar.](./media/guix-studio/image63.jpg)

**Bild 29**

Aktivera ***Alternativet Visa rutnät** _ visar rutnät på målskärmen. Du kan ange ökning av rutnät (i bildpunkter) i fältet _*_Rutnätsavstånd._*_ Alternativet _ *_Fäst vid rutnät_** hjälper dig att få rätt position för en widget. Aktivera det här alternativet aktiveras fästen.

När ***alternativet Rutnät och Fäst*** är aktiverat:

- Om du drar ett objekt med musen i målvyn flyttas objektet stegvis med rutnät.
- Om du drar kanten för ett objekt för att ändra storlek fästs kanten som du drar på rutnätspositionen.
- Om du väljer ett objekt och använder upp-/vänster-/nedåt-/högertangenter, flyttas den valda widgeten med snapinkrement, du kan ange snapin-ökning (i bildpunkter) i fältet ***Fästavstånd.***
