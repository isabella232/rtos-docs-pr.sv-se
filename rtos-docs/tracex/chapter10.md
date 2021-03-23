---
title: Kapitel 10 – kund användar händelser
description: Det här kapitlet innehåller en beskrivning av hur du skapar användardefinierade händelser och anpassade ikoner och informations fält för sådana händelser.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 635c2d79922de9d5649bab841ae946cac862056c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827606"
---
# <a name="chapter-10---customer-user-events"></a>Kapitel 10 – kund användar händelser

Det här kapitlet innehåller en beskrivning av hur du skapar användardefinierade händelser och anpassade ikoner och informations fält för sådana händelser. Det här kapitlet innehåller följande avsnitt: 

## <a name="inserting-user-defined-events"></a>Infoga User-Defined händelser

ThreadX ger utvecklare möjlighet att logga egna användardefinierade händelser, vilket ger ännu mer värdefull information som kan visas grafiskt av TraceX. Användardefinierade händelse nummer intervall från

**TX_TRACE_USER_EVENT_START** (4096) via **TX_TRACE_USER_EVENT_END** (65535), inklusive. Placeringen av händelserna i kommandobufferten görs via den ***tx_trace_user_event_insert***, som definieras i kapitel 5. I följande exempel anrop infogas två användardefinierade händelser i den aktuella spårningssessionen på målet, nämligen användardefinierad händelse 4096 och händelse 4098:

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a>Standard visning av User-Defined händelser

![Användardefinierad händelse ikon](./media/user-guide/tx-events/image0.png)

Som standard visar TraceX alla användar händelser med en användardefinierad standard händelse ikon enligt beskrivningen i kapitel 6. Bild 28 visar den användardefinierade standard händelse ikonen för händelserna 452 och 453, som placerades i Event buffer via föregående ***tx_trace_user_event_insert*** exempel.

![Skärm bild av standard visning av användardefinierade händelser. ](./media/user-guide/10.1.png)
 **Bild 28**

Detaljerad information finns också för användardefinierade händelser. Bild 28 visar detaljerad händelse information för händelse 452, som har händelse numret 4096 och visar de angivna fyra informations fälten.

![Skärm bild av den detaljerade visningen av användardefinierade händelser. ](./media/user-guide/10.2.png)
 **Bild 29**

## <a name="defining-custom-user-defined-event-icons"></a>Definiera anpassade User-Defined händelse ikoner

TraceX ger också användaren möjlighet att skapa anpassade användardefinierade händelse ikoner och etiketter för anpassade informations fält. Den här funktionen uppnås genom att lägga till specifikationer för händelse ikon i konfigurations filen ***tracex_custom. trxc** _. Den här filen finns i under katalogen _ *_CustomEvents_** i den användardefinierade TraceX-installations katalogen, som är som standard C:\ Azure_RTOS \tracex. En exempel katalog Sök väg visas i bild 30.

![Skärm bild av en exempel katalog Sök väg. ](./media/user-guide/custom_events_folder.png)
 **Bild 30**

Den anpassade händelse konfigurations filen ***tracex_custom. trxc*** är en enkel ASCII-textfil som innehåller noll eller flera anpassade händelse definitioner. Filens format är följande:

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

Varje rad mellan start och end används för att definiera en enskild anpassad händelse. TraceX innehåller en mall version av den här filen utan anpassade definierade händelser (inget mellan "Start" och "slut" etiketter). Formatet på en anpassad händelse definition är följande:

**nummer, namn, förkortning, top_color, bottom_color, Label1, Label2, Label2, Label4**

där:

- Number: definierar det användardefinierade händelse numret, mellan 4096 och 65535.</th>
- Namn: definierar det logiska namnet för den användardefinierade händelsen.</td>
- förkortning: definierar en användardefinierad händelse förkortning med två bokstäver.</td>
- top_color: definierar RGB-värdet för den övre halvan av ikonen, som är ett fyrsiffrigt tal inom parentes. Några typiska RGB-definitioner är
  - SVART = (0,0)       
  - VIT = (255 255 255)
  - RÖD = (255, 0, 0)     
  - GRÖNT = (0255, 0)     
  - BLÅ = (0, 0255)     
  - GUL = (255255, 0)   
  - CYAN = (0255 255)   
  - MAGENTA = (255, 0255)   
  Genom att använda RBG-specifikationen får användaren en rad olika färger för varje användardefinierad ikon. Mer information om RBG färg definition finns i: https://en.wikipedia.org/wiki/RGB#Digital_representations
- botton_color: definierar RGB-värdet för den nedre halvan av ikonen, som är ett fyrsiffrigt tal inom parentes.
- Label1: etikett för ***info_field_1** _, som anges i anropet _ *_tx_trace_user_event_insert_**.
- Label2: etikett för ***info_field_2** _, som anges i anropet _ *_tx_trace_user_event_insert_**.
- Label3: etikett för ***info_field_3** _, som anges i anropet _ *_tx_trace_user_event_insert_**.
- Label4: etikett för ***info_field_4** _, som anges i anropet _ *_tx_trace_user_event_insert_**.

Exempel definitioner för var och en av de två användardefinierade händelserna som används i det här kapitlet visas i bild 10,4. Den första definitionen är för händelse 4096 på rad 5 i ***tracex_custom. trxc** _-filen. Den här definitionen ger användardefinierad händelse 4096 namnet _ * First_User_Event * *, anger en förkortning på två bokstäver i **FE**, gör den övre delen av ikonen röd, den nedre delen av ikonen grönt och namnger informations fälten som **First_Info1**, **First_Info2**, **First_Info3** och **First_Info4**. Användardefinierad händelse 4098 definieras på samma sätt som rad 6 i **_tracex_custom. trxc_**.

![Skärm bild av exempel definitionerna för användardefinierade händelser. ](./media/user-guide/10.4.png)
 **Bild 31**

Eftersom ***tracex_custom. trxc** _-filen läses av tracex under initieringen, måste tracex avslutas och startas om innan de anpassade ikon definitionerna kan börja gälla. Bild 32 visar TraceX-visningen av användardefinierade händelser 452 och 453 med anpassade händelse ikoner definierade i _ *_tracex_custom. trxc_* *.

![Skärm bild av TraceX-visningen av användardefinierade händelser med ikonerna för anpassade händelser. ](./media/user-guide/10.5.png)
 **Figur 32**

Den ytterligare informationen i den anpassade händelse definitionen visas när du väljer att använda ett dubbel klick, en mus över eller genom att klicka på den aktuella händelse knappen. Bild 33 visar hur du dubbelklickar på händelse 452. Händelse namn och informations fält matchar alla exempel definitioner som har lagts till i ***tracex_custom. trxc***.

![Skärm bild av markeringen dubbelklicka på en händelse. ](./media/user-guide/10.6.png)
 **Figur 33**
