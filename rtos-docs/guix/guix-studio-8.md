---
title: Information om redigering av specifika widgettyper
description: Detaljerade kommentarer som beskriver redigeringsmetoder för vissa komplexa widgettyper.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d57aa4034aaa6bbb3b29e79ba2b38443822ea5ce554b62af9e3c9ea874614488
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785510"
---
# <a name="chapter-8-notes-on-editing-specific-widget-types"></a>Kapitel 8: Kommentarer om redigering av specifika widgettyper

MED GUIX Studio kan användaren enkelt skapa och ändra GUIX-widgetar som utgör programmets användargränssnittsskärmar. De flesta av dessa redigeringsmetoder är intuitiva och uppenbara. Om du till exempel vill ändra storlek på en widget kan du välja widgeten med musen och dra widgeten kantlinjer. Du kan också skriva direkt i egenskapsfälten vänster/topp/bredd/höjd för den valda widgeten.

Vissa widgettyper kräver en mer avancerad redigeringsprocess, eftersom dessa widgetar själva är lite mer avancerade i sitt funktionsstöd.

Det här kapitlet innehåller information om de mer avancerade redigeringsfunktionerna för dessa mer komplexa widgettyper. De här anteckningarna expanderas allt eftersom funktionerna i GUIX Studio utvecklas tillsammans med de widgettyper som finns i GUIX-biblioteket.

## <a name="rich-text-view"></a>RTF-vy

Den här widgeten används för att visa rtf-text som stöder infogade textformateringskoder. Formateringskoderna innehåller fetstil, kursiv stil och flera andra. Börja genom att högerklicka på den valda överordnade vyn  *från Project* Eller Målvy och välja menyn **Infoga/Text-/RTF-vy** för att infoga en widget för rtf-textvy.

Förutom standarduppsättningen med egenskaper som stöds av alla widgettyper stöder widgettypen Rich Text View ytterligare egenskaper.

### <a name="additional-properties"></a>Ytterligare egenskaper

| Egenskap | Innebörd |
|----------|---------|
| Textjustera | Standardjustering av text |
| Normalt teckensnitt| Standardteckensnitt för text |
| Fetstil  | Textteckensnitt för text som taggats som fet |
| Kursivt teckensnitt| Textteckensnitt för text som taggats som kursiv|
| Fet kursiv stil| Textteckensnitt för text som taggats som fet och kursiv |
| Privat textkopiering | Bör kontrolleras om widgeten ska behålla sin egen privata kopia av tilldelad text |
| Blanksteg | Bredd på marginalen mellan widgeten och den visade texten, i bildpunkter. |
| Radutrymme | Blanksteg mellan två rader i texten, i bildpunkter. |
|||

### <a name="the-rich-text-formatting-codes"></a>Formateringskoderna för RTF

Följande formatkoder stöds för textformatering.

|Tagg|Innebörd|
|---|---|
|\<b>\</b> | Rendera textteckensnitt med användarens angivna fetstils-ID|
|\<i>\</i> | Rendera textteckensnitt med användarangivet kursivt teckensnitts-ID|
|\<u>\</u> | Rendera understruken text|
|\<f GX_FONT_ID>\</f> | Rendera text med det angivna teckensnitts-ID:t. |
|\<c GX_COLOR_ID>\</c> | Rendera text med angivet färg-ID|
|\<hc GX_COLOR_ID>\</hc> | Rendera text med angivet bakgrundsfärg-ID|
|\<align left/right/center>\</align> | Tilldela textjustering|
|||

Det finns två sätt att redigera RTF-strängen från GUIX Studio:

- Använd dialogrutan Redigera RTF, vilket är den rekommenderade och enklaste redigeringsmetoden.
- Använd dialogrutan Redigerare för strängtabell, där du kan infoga formateringstaggarna som visas i tabellen ovan manuellt.

När du har valt en widget för RTF-vy i  målvyn väljer du knappen Redigera **RTF** i egenskapsvyn för att anropa dialogrutan för RTF-redigering, som visas i bild 8.1.

![Skärmbild av dialogrutan REDIGERA RTF i GUIX Studio.](./media/guix-studio/edit_rich_text_dialog.png)

**Bild 8.1**

Den vänstra rutan är textredigeringsfältet. Du kan använda verktygsfältsikonerna för att infoga taggar som du behöver. Markera ett textblock i redigeringsfältet och välj sedan knapparna i verktygsfältet för att tillämpa de format och färger som krävs för det valda textblocket. Dialogrutan Redigera RTF är ett enkelt sätt att infoga formateringskoderna i teststrängen. Du kan också infoga dessa taggar manuellt eller till och med generera dem vid körning om det behövs.

Det högra fönstret är widgetförhandsvisningen som visar hur texten återges i målvyn. Bakgrundsfärgen för widgetförhandsvisningen är fast, vilket kanske inte matchar widgetens tilldelade bakgrundsfärg i målvyn.

Resurs-ID-namn används i RTF för att referera till specifika teckensnitts- eller färgresurser. Om resursnamnet för ett teckensnitt eller en färg ändras efter att den har refererats till av RTF-strängen uppdaterar GUIX Studio automatiskt RTF-strängen så att den återspeglar resursnamnets ändringar. Å andra sidan, om du tar bort ett teckensnitt eller en färgresurs som refereras av en RTF-widget, måste du redigera den berörda RTF manuellt för att ta bort eller ändra resurs-ID-namn som har tagits bort.

När du väljer knappen Spara i den här dialogrutan läggs den RTF-sträng som du har definierat till i projektsträngstabellen.

## <a name="string-scroll-wheel"></a>Rullningshjul för strängar

En widget för rullningshjul för strängar stöder visning av en matris med strängar. Dessa strängar kan tilldelas dynamiskt, eller, om programmet stöder flera språk, kan de tilldelade strängarna hämtas från den aktiva strängtabellen.

Widgeten för rullningshjul för strängar stöder en matris med strängar. Dialogrutan Redigera rullningshjul för strängar, som visas i bild 8.2, tillhandahålls så att användaren kan tilldela den här matrisen med strängar.

![Skärmbild av dialogrutan Redigera rullningshjul för GUIX Studio-strängsträng.](./media/guix-studio/string_scroll_wheel_edit.png)

**Bild 8.2**

Om du vill anropa den här dialogrutan väljer du en widget för rullningshjul *för* strängar i *målvyn eller Project Visa*. När den här widgettypen har valts *innehåller egenskapsvyn* knappen **Redigera strängar.** Välj den här knappen för att anropa dialogrutan Redigera strängrullningshjul.

Om du vill tilldela en sträng för varje textindex kan du antingen välja ett sträng-ID i listrutan eller ange ett nytt strängvärde i fältet Text till höger. När du är klar med dina ändringar sparas alla nya eller ändrade strängar i den aktiva strängtabellen.

## <a name="sprite"></a>Sprite

En positive-widget används för att visa en sekvens med bilder för att ge en animeringseffekt. En personwidget kräver en ramlista, som är en matris med bild-ID:er och unika parametrar som tillämpas på varje bild i ramen. Om du vill skapa den här bildrutelistan för personwidgeten visas dialogrutan Redigera Personere-bildrutor, som visas i bild 8.3:

![Skärmbild av dialogrutan GUIX Studio Redigera Intruteramar.](./media/guix-studio/edit_sprite_frames.png)

**Bild 8.3**

Om du vill anropa den här dialogrutan väljer du en widget för att hitta i *målvyn* *eller Project Visa*. När du har valt den här widgettypen *innehåller egenskapsvyn* knappen **Redigera bildruta.** Välj den här knappen för att anropa dialogrutan Redigera strängrullningshjul.

Fältet *Totalt antal Personere-bildrutor* är ett indatafält där du kan ange det totala antalet heltal för bildrutor som ska visas av widgeten för personer. Bilder kan återanvändas i bildrutelistan, vilket innebär att inte alla bilder måste vara unika.

Fältet Förser ram-ID är ett värde för val av ramindex som sträcker sig från 1 till Totalt antal bildrutor. Öka och minska det här värdet för att flytta från en personbildruta till nästa.

Varje personbildruta har flera parametrar. Den första är bakgrundsåtgärden. Det här fältet efterliknar funktionerna i det populära GIF-animeringsformatet. Alternativen här är:

- Ingen åtgärd, vilket innebär att den aktuella bildrutebilden ritas över föregående bildruta.
- Återställ första pixelkartan, vilket innebär att indexet 1 pixelkarta ritas före den aktuella pixelkartan och
- Solid Color Fill, vilket innebär att bakgrundsfärgen har fyllts med bakgrundsfärgen för din fyllnad innan den aktuella ramen ritas.

Med fältet Pixelkarta-ID kan du välja valfri pixelkarta som tidigare lagts till i projektresurserna. Samma pixelkarta-ID kan användas för flera bildrutor. Till exempel kan din favoritanimering använda förflyttning av bilden (med x- och y-förskjutningsfälten) i stället för eller utöver att använda olika bilder för personer.

Fältet Alfavärde tillämpas på hela pixelkartan. Det här fältet har bara en effekt när du kör med 8 bpp-färgdjup och högre. Alfavärdet 0 är helt transparent och alfavärdet 255 är täckande.

Du kan ange en förskjutning inom ramen där den aktuella pixelkartan ska ritas med hjälp av fälten Frame x-offset och Frame y-offset. Med andra ord behöver varje bild som ritas inte vara den fullständiga storleken på widgeten för personer.

Fördröjningsperioden anger tiden för fördröjning innan du flyttar till nästa figurram. Det här värdet är i tick, som för standardkonfigurationen av GUIX/ThreadX-timern representerar 50 ms.

När du sparar ändringarna i dialogrutan Redigera Inställningarramar kan GUIX Studio generera hela matrisen med bildrutor som en del av genereringen av utdataspecifikationerna.

### <a name="assign-a-sprite-widget-with-gif-resource"></a>Tilldela enfördelningswidget med GIF-resurs
Du kan lägga till en GIF-resurs **till Pixelmap-resursgruppen** och tilldela GIF-resursen till widgeten direkt. När GIF-resursen har angetts genereras en bildrutelista automatiskt. Du kan redigera varje bildruta i bildrutelistan ytterligare via dialogrutan för redigering av rutor:

![Skärmbild av dialogrutan GUIX Studio Redigera Inställningar för GIF-resurs.](./media/guix-studio/edit_sprite_gif_frames.jpg)

**Bild 8.4**