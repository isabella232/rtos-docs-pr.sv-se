---
title: Kapitel 10 – Kundanvändarhändelser
description: Det här kapitlet innehåller en beskrivning av hur du skapar användardefinierade händelser och anpassade ikoner och informationsfält för sådana händelser.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: b287436fb7f61df846bb0c84d910f5c095bc1f8f6635305e97c9e8b7aab64655
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790431"
---
# <a name="chapter-10---customer-user-events"></a>Kapitel 10 – Kundanvändarhändelser

Det här kapitlet innehåller en beskrivning av hur du skapar användardefinierade händelser och anpassade ikoner och informationsfält för sådana händelser. Det här kapitlet innehåller följande avsnitt: 

## <a name="inserting-user-defined-events"></a>Infoga User-Defined händelser

ThreadX gör det möjligt för utvecklare att logga sina egna användardefinierade händelser, vilket ger ännu mer användbar information som kan visas grafiskt av TraceX. Användardefinierade händelsenummer sträcker sig från

**TX_TRACE_USER_EVENT_START** (4096) till **och med TX_TRACE_USER_EVENT_END** (65535). Placeringen av händelserna i spårningsbufferten görs via ***tx_trace_user_event_insert***, som definieras i kapitel 5. I följande exempel anropas infoga två användardefinierade händelser i den aktuella spårningsbufferten på målet, nämligen användardefinierad händelse 4096 och händelse 4098:

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a>Standardvisning av User-Defined händelser

![Ikon för användardefinierad händelse](./media/user-guide/tx-events/image0.png)

Som standard visar TraceX alla användarhändelser med en standardanvändardefinierad händelseikon enligt beskrivningen i kapitel 6. Bild 28 visar den användardefinierade standardhändelseikonen för händelserna 452 och 453, som placerades i händelsebufferten via ***föregående tx_trace_user_event_insert*** exempel.

![Skärmbild av standardvisningen av användardefinierade händelser. ](./media/user-guide/10.1.png)
 **BILD 28**

Detaljerad information är också tillgänglig för användardefinierade händelser. Bild 28 visar detaljerad händelseinformation för händelse 452, som har händelsenummer 4096 och visar de angivna fyra informationsfälten.

![Skärmbild av detaljerad visning av användardefinierade händelser. ](./media/user-guide/10.2.png)
 **BILD 29**

## <a name="defining-custom-user-defined-event-icons"></a>Definiera anpassade User-Defined händelseikoner

TraceX ger också användaren möjlighet att skapa anpassade användardefinierade händelseikoner och anpassade fältetiketter för information. Den här funktionen uppnås genom att lägga till händelseikonspecifikationer i konfigurationsfilen ***tracex_custom.trxc** _ . Den här filen finns i underkatalogen _ *_CustomEvents_** i din användardefinierade TraceX-installationskatalog, som standard är c:\Azure_RTOS\TraceX. Ett exempel på en katalogsökväg visas i bild 30.

![Skärmbild av ett exempel på en katalogsökväg. ](./media/user-guide/custom_events_folder.png)
 **BILD 30**

Den ***anpassade tracex_custom.trxc-händelsekonfigurationsfilen*** är en enkel ASCII-textfil som innehåller noll eller flera anpassade händelsedefinitioner. Formatet på filen är följande:

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

Varje rad mellan Start och End används för att definiera en enskild anpassad händelse. TraceX tillhandahåller en mallversion av den här filen utan definierade anpassade händelser (inget mellan etiketterna "Start&quot; och &quot;End"). Formatet för en anpassad händelsedefinition är följande:

**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**

där:

- number: Definierar det användardefinierade händelsenumret, inklusive mellan 4096 och 65535.</th>
- name: Definierar det logiska namnet för den användardefinierade händelsen.</td>
- abbreviation: Definierar den användardefinierade händelseförkortningen med två bokstäver.</td>
- top_color: Definierar RGB-värdet för den övre halvan av ikonen, vilket är ett tresiffrigt tal inom parentes. Några vanliga RGB-definitioner är
  - BLACK = (0,0,0)       
  - WHITE = (255 255 255)
  - RED = (255,0,0)     
  - GREEN = (0 255,0)     
  - BLUE = (0,0,255)     
  - YELLOW = (255 255,0)   
  - CYAN = (0 255 255)   
  - TAPTA = (255,0,255)   
  Med hjälp av RBG-specifikationen får användaren ett brett utbud av färger för varje användardefinierad ikon. Mer information om RBG-färgdefinition finns i: https://en.wikipedia.org/wiki/RGB#Digital_representations
- botton_color: Definierar RGB-värdet för den nedre halvan av ikonen, vilket är ett tresiffrigt tal inom parentes.
- label1: Etikett för ***info_field_1** _, som anges i anropet _ *_tx_trace_user_event_insert_** .
- label2: Etikett för ***info_field_2** _, som anges i anropet _ *_tx_trace_user_event_insert_** .
- label3: Etikett för ***info_field_3** _, som anges i anropet _ *_tx_trace_user_event_insert_** .
- label4: Etikett för ***info_field_4** _, som anges i anropet _ *_tx_trace_user_event_insert_** .

Exempeldefinitioner för var och en av de två användardefinierade händelser som används i det här kapitlet visas i bild 10.4. Den första definitionen är för händelse 4096 på rad 5 i filen ***tracex_custom.trxc** _ . Den här definitionen ger användardefinierad händelse 4096 namnet _*First_User_Event**, anger en tvåbokstavsförkortning av **FE**, gör den översta delen av ikonen röd, den nedre delen av ikonen grön och ger informationsfälten namnet **First_Info1**, **First_Info2**, **First_Info3** **och First_Info4**. Användardefinierad händelse 4098 definieras på liknande sätt på rad 6 **_i tracex_custom.trxc_**.

![Skärmbild av exempeldefinitionerna för de användardefinierade händelserna. ](./media/user-guide/10.4.png)
 **BILD 31**

Eftersom filen ***tracex_custom.trxc** _ läses av TraceX under initieringen måste TraceX avslutas och startas om innan de anpassade ikondefinitionerna kan börja gälla. Bild 32 visar TraceX-visningen av användardefinierade händelser 452 och 453 med de anpassade händelseikonerna som definierats i _*_tracex_custom.trxc_**.

![Skärmbild av TraceX-visningen av användardefinierade händelser med anpassade händelseikoner. ](./media/user-guide/10.5.png)
 **BILD 32**

Ytterligare information i den anpassade händelsedefinitionen visas när händelsen du väljer med hjälp av ett dubbelklicka, muspekaren över eller klicka på den aktuella händelseknappen. Bild 33 visar valet av dubbelklicka på händelse 452. Händelsenamnen och informationsfälten matchar exempeldefinitionen som lades till ***i tracex_custom.trxc***.

![Skärmbild av valet dubbelklicka på en händelse. ](./media/user-guide/10.6.png)
 **BILD 33**
