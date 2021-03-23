---
title: Kommentarer om hur du redigerar vissa typer av widget
description: Detaljerade kommentarer som beskriver redigerings metoder för vissa typer av komplexa widgetar.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3194a1b8c8965bf821631a8c34ac5e9961f8c8ff
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827126"
---
# <a name="chapter-8-notes-on-editing-specific-widget-types"></a>Kapitel 8: kommentarer om att redigera vissa typer av widget

GUIX Studio gör det möjligt för användaren att enkelt skapa och ändra GUIX-widgetar som skapar program GRÄNSSNITTs skärmarna. De flesta av dessa redigerings metoder är intuitiva och uppenbara. Om du till exempel vill ändra storlek på en widget kan du välja widgeten med musen och dra i widgetarna för widgeten. Du kan också skriva direkt i egenskaps fälten vänster/topp/bredd/höjd i den valda widgeten.

Vissa typer av widget kräver en mer avancerad redigerings process, eftersom dessa widgetar själva är lite mer sofistikerade i sin funktions support.

Det här kapitlet innehåller information om de mer avancerade redigerings funktionerna för dessa mer komplexa typer av widgetar. Dessa anteckningar visas som funktionerna i GUIX Studio-förflyttningen tillsammans med de widgets typer som finns i GUIX-biblioteket.

## <a name="rich-text-view"></a>RTF-vy

Den här widgeten används för att visa RTF-text som stöder text format koder med text rader. Dessa formateringsregler innehåller fetstil, kursiv stil och flera andra. Börja genom att högerklicka på den markerade överordnade vyn från *projektvyn* eller vyn *mål* och välja menyn **Infoga/text/RTF-vy** om du vill infoga en RTF-widget.

Förutom standard uppsättningen med egenskaper som stöds av alla typer av widgetar, stöder widgeten RTF-visning ytterligare egenskaper.

### <a name="additional-properties"></a>Ytterligare egenskaper

| Egenskap | Innebörd |
|----------|---------|
| Text justering | Standard justering av text |
| Normalt teckensnitt| Standard teckensnitt för text |
| Fetstil  | Teckensnitt för text som är formaterad som fet |
| Kursivt teckensnitt| Teckensnitt för text som är formaterad som kursiv|
| Fet kursivt teckensnitt| Teckensnitt för text som är formaterad som fet och kursiv |
| Privat text kopiering | Bör kontrol leras om widgeten är att behålla sin egen privata kopia av alla tilldelade text |
| Blanksteg | Bredd på marginalen mellan widgeten och den visade texten, i bild punkter. |
| Rad avstånd | Blank steg mellan två rader med texten, i bild punkter. |
|||

### <a name="the-rich-text-formatting-codes"></a>RTF-koderna för text formatering

Följande format koder stöds för formatering av text.

|Tagg|Innebörd|
|---|---|
|\<b>\</b> | Återge teckensnitt med användare angivet fet tecken-ID|
|\<i>\</i> | Återge teckensnitt med användarens angivna kursiva tecken-ID|
|\<u>\</u> | Återge understruken text|
|\<f GX_FONT_ID>\</f> | Återge text med angivet teckensnitts-ID. |
|\<c GX_COLOR_ID>\</c> | Återge text med angivet färg-ID|
|\<hc GX_COLOR_ID>\</hc> | Rendera text med angivet bakgrunds färg-ID|
|\<align left/right/center>\</align> | Tilldela text justering|
|||

Det finns två sätt att redigera Rich Text-strängen från GUIX Studio:

- Använd dialog rutan redigera RTF-format, vilket är den rekommenderade och enklaste redigerings metoden.
- Använd dialog rutan sträng tabell redigerare, som gör att du manuellt kan infoga formateringsmarkeringar som visas i tabellen ovan.

När du har valt en RTF-widget i vyn *mål* väljer du knappen **redigera RTF** i *egenskapsvyn* för att anropa RTF-redigera-dialog rutan, som visas i bild 8,1.

![Skärm bild av dialog rutan Redigera Rich text i GUIX Studio.](./media/guix-studio/edit_rich_text_dialog.png)

**Figur 8,1**

Den vänstra rutan är text redigerings fältet RTF. Du kan använda verktygsfälts ikonerna för att infoga taggar som du behöver. Välj ett textblock i redigerings fältet och välj sedan verktygsfälts knapparna för att tillämpa de format och färger som krävs för det valda textblocket. Dialog rutan redigera RTF-text är ett enkelt sätt att infoga formateringsregler i test strängen. Du kan också infoga taggarna manuellt eller till och med generera dem vid körning om det behövs.

Den högra rutan är för hands versionen av widgeten för att visa hur texten återges i mål visningen. Bakgrunds färgen för för hands versionen av widgeten är fast, vilket kanske inte matchar widgetens tilldelade bakgrunds färg i vyn mål.

Resurs-ID-namn används i RTF-format för att referera till vissa teckensnitt eller färg resurser. Om resurs namnet för ett teckensnitt eller en färg ändras efter det att text strängen har refererats till, kommer GUIX Studio automatiskt att uppdatera RTF-strängen så att den återspeglar resursens namn ändringar. Å andra sidan om du tar bort en teckensnitts-eller färg resurs som refereras till av en RTF-widget måste du redigera den påverkade RTF-texten manuellt för att ta bort eller ändra resurs-ID-namn som har tagits bort.

När du väljer knappen Spara i den här dialog rutan läggs den RTF-sträng som du har definierat till i tabellen med projekt strängar.

## <a name="string-scroll-wheel"></a>Sträng rullnings hjul

En widget för rullnings hjul för String stöder visning av en sträng mat ris. De här strängarna kan tilldelas dynamiskt eller, om programmet har stöd för flera språk, kan de tilldelade strängarna hämtas från den aktiva sträng tabellen.

Widgeten för rullnings hjul för String stöder en sträng mat ris. Redigera-dialog rutan för sträng rullnings hjul, som visas i bild 8,2, tillhandahålls för att tillåta att användaren tilldelar denna sträng mat ris.

![Skärm bild av dialog rutan Redigera rullnings hjul för GUIX Studio-sträng.](./media/guix-studio/string_scroll_wheel_edit.png)

**Figur 8,2**

För att anropa den här dialog rutan väljer du en widget för String-rullnings hjul i *vyn mål* eller *projektvyn*. När den här widgeten har marker ATS innehåller *egenskapsvyn* en knapp för att **Redigera strängar** . Välj den här knappen för att aktivera redigerings dialog rutan för sträng rullnings hjul.

Om du vill tilldela en sträng för varje text index kan du antingen välja ett sträng-ID i list rutan, eller så kan du skriva ett nytt sträng värde i fältet text till höger. När du är färdig med ändringarna sparas alla nya eller ändrade strängar i den aktiva sträng tabellen.

## <a name="sprite"></a>Sprit

En sprite-widget används för att visa en sekvens med bilder för att skapa en animeringseffekt. En widget för Sprite kräver en ram lista, som är en matris med bild-ID: n och unika parametrar som används för varje bild i ramen. Om du vill bygga List rutan för widgeten Sprite för Sprite visas dialog rutan Redigera Sprite-ramar, som visas i bild 8,3,:

![Skärm bild av dialog rutan Redigera Sprite-ramar i GUIX Studio.](./media/guix-studio/edit_sprite_frames.png)

**Figur 8,3**

Välj en widget för sprite i vyn *mål* eller *projektvyn* för att anropa den här dialog rutan. När den här widgeten har marker ATS innehåller *egenskapsvyn* en knapp för att **Redigera Framelist** . Välj den här knappen för att aktivera redigerings dialog rutan för sträng rullnings hjul.

Det *totala antalet bild Rute fält för Sprite* är ett indatafält som gör att du kan ange det totala antalet ramar som ska visas av widgeten Sprite. Bilder kan återanvändas i ram listan, vilket innebär att alla bilder måste vara unika.

Fältet ID för bild sprites ram är ett markerings värde för ram index som sträcker sig från 1 till totalt antal ramar. Öka och minska det här värdet för att flytta från en sprite-ram till nästa.

Varje Sprite-ram har flera parametrar. Det första är bakgrunds åtgärden. Det här fältet imiterar funktionerna i formatet populär GIF-animering. Alternativen här inkluderar:

- Ingen åtgärd, vilket innebär att den aktuella bild Rute bilden ritas över föregående bild Rute bild.
- Återställ första pixeln – kartan, vilket innebär att index 1 pixel-Map ritas före den aktuella pixel kartan och
- Enfärgad fyllning, vilket innebär att Sprite-bakgrunden fylls med bakgrunds färgen för spriten innan den aktuella ramen ritas.

I fältet pixel-Map-ID kan du välja en pixel karta som tidigare har lagts till i projekt resurserna. Samma pixel-kart-ID kan användas för flera ramar. Till exempel kan din Sprite-animering använda bildens rörelse (med fälten x och y offset) i stället för eller förutom att använda olika Sprite-bilder.

Fältet alfa värde används för hela bild punkts kart ritningen. Det här fältet har bara en funktion när du kör med 8 BPP färgdjup och högre. Alfa värdet 0 är helt transparent och alfa värdet 255 är ogenomskinligt.

Du kan ange en förskjutning i Sprite-ramen där den aktuella pixel kartan ska ritas med hjälp av fälten ram x-förskjutning och ram y-offset. Med andra ord behöver varje bild ritas inte vara full storlek för widgeten Sprite.

Fördröjnings perioden anger hur lång tid det tar innan flyttas till nästa Sprite-ram. Det här värdet är i Tick, som för standard konfigurationen av GUIX/ThreadX varje Tick representerar 50 ms.

När du sparar ändringarna i dialog rutan Redigera Sprite-ramar kan GUIX Studio generera den kompletta mat ris listan som en del av den genererade filen med utdata.
