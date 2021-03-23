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
# <a name="chapter-10---customer-user-events"></a><span data-ttu-id="b741b-103">Kapitel 10 – kund användar händelser</span><span class="sxs-lookup"><span data-stu-id="b741b-103">Chapter 10 - Customer user events</span></span>

<span data-ttu-id="b741b-104">Det här kapitlet innehåller en beskrivning av hur du skapar användardefinierade händelser och anpassade ikoner och informations fält för sådana händelser.</span><span class="sxs-lookup"><span data-stu-id="b741b-104">This chapter contains a description of how to create user-defined events and custom icons and information fields for such events.</span></span> <span data-ttu-id="b741b-105">Det här kapitlet innehåller följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="b741b-105">This chapter includes the following sections:</span></span> 

## <a name="inserting-user-defined-events"></a><span data-ttu-id="b741b-106">Infoga User-Defined händelser</span><span class="sxs-lookup"><span data-stu-id="b741b-106">Inserting User-Defined Events</span></span>

<span data-ttu-id="b741b-107">ThreadX ger utvecklare möjlighet att logga egna användardefinierade händelser, vilket ger ännu mer värdefull information som kan visas grafiskt av TraceX.</span><span class="sxs-lookup"><span data-stu-id="b741b-107">ThreadX provides the ability for developers to log their own user-defined events, providing even more useful information that can be viewed graphically by TraceX.</span></span> <span data-ttu-id="b741b-108">Användardefinierade händelse nummer intervall från</span><span class="sxs-lookup"><span data-stu-id="b741b-108">User-defined event numbers range from</span></span>

<span data-ttu-id="b741b-109">**TX_TRACE_USER_EVENT_START** (4096) via **TX_TRACE_USER_EVENT_END** (65535), inklusive.</span><span class="sxs-lookup"><span data-stu-id="b741b-109">**TX_TRACE_USER_EVENT_START** (4096) through **TX_TRACE_USER_EVENT_END** (65535), inclusive.</span></span> <span data-ttu-id="b741b-110">Placeringen av händelserna i kommandobufferten görs via den ***tx_trace_user_event_insert***, som definieras i kapitel 5.</span><span class="sxs-lookup"><span data-stu-id="b741b-110">The placement of the events in the trace buffer is done via the ***tx_trace_user_event_insert***, defined in Chapter 5.</span></span> <span data-ttu-id="b741b-111">I följande exempel anrop infogas två användardefinierade händelser i den aktuella spårningssessionen på målet, nämligen användardefinierad händelse 4096 och händelse 4098:</span><span class="sxs-lookup"><span data-stu-id="b741b-111">The following example calls insert two user-defined events into the current trace buffer on the target, namely user-defined event 4096 and event 4098:</span></span>

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a><span data-ttu-id="b741b-112">Standard visning av User-Defined händelser</span><span class="sxs-lookup"><span data-stu-id="b741b-112">Default Display of User-Defined Events</span></span>

![Användardefinierad händelse ikon](./media/user-guide/tx-events/image0.png)

<span data-ttu-id="b741b-114">Som standard visar TraceX alla användar händelser med en användardefinierad standard händelse ikon enligt beskrivningen i kapitel 6.</span><span class="sxs-lookup"><span data-stu-id="b741b-114">By default, TraceX displays all user events with a default user-defined Event icon as described in Chapter 6.</span></span> <span data-ttu-id="b741b-115">Bild 28 visar den användardefinierade standard händelse ikonen för händelserna 452 och 453, som placerades i Event buffer via föregående ***tx_trace_user_event_insert*** exempel.</span><span class="sxs-lookup"><span data-stu-id="b741b-115">Figure 28 shows the default user-defined event icon for events 452 and 453, which were placed in the event buffer via the previous ***tx_trace_user_event_insert*** examples.</span></span>

<span data-ttu-id="b741b-116">![Skärm bild av standard visning av användardefinierade händelser. ](./media/user-guide/10.1.png)
 **Bild 28**</span><span class="sxs-lookup"><span data-stu-id="b741b-116">![Screenshot of the default display of user-defined events.](./media/user-guide/10.1.png)
**FIGURE 28**</span></span>

<span data-ttu-id="b741b-117">Detaljerad information finns också för användardefinierade händelser.</span><span class="sxs-lookup"><span data-stu-id="b741b-117">Detailed information is also available for user-defined Events.</span></span> <span data-ttu-id="b741b-118">Bild 28 visar detaljerad händelse information för händelse 452, som har händelse numret 4096 och visar de angivna fyra informations fälten.</span><span class="sxs-lookup"><span data-stu-id="b741b-118">Figure 28 shows the detailed event information for event 452, which has event number 4096 and shows the specified four information fields.</span></span>

<span data-ttu-id="b741b-119">![Skärm bild av den detaljerade visningen av användardefinierade händelser. ](./media/user-guide/10.2.png)
 **Bild 29**</span><span class="sxs-lookup"><span data-stu-id="b741b-119">![Screenshot of the detailed display of user-defined events.](./media/user-guide/10.2.png)
**FIGURE 29**</span></span>

## <a name="defining-custom-user-defined-event-icons"></a><span data-ttu-id="b741b-120">Definiera anpassade User-Defined händelse ikoner</span><span class="sxs-lookup"><span data-stu-id="b741b-120">Defining Custom User-Defined Event Icons</span></span>

<span data-ttu-id="b741b-121">TraceX ger också användaren möjlighet att skapa anpassade användardefinierade händelse ikoner och etiketter för anpassade informations fält.</span><span class="sxs-lookup"><span data-stu-id="b741b-121">TraceX also provides the user the ability to create custom user-defined event icons and custom information field labels.</span></span> <span data-ttu-id="b741b-122">Den här funktionen uppnås genom att lägga till specifikationer för händelse ikon i konfigurations filen \***tracex_custom. trxc** _.</span><span class="sxs-lookup"><span data-stu-id="b741b-122">This capability is achieved by adding event icon specifications to the \***tracex_custom.trxc** _ configuration file.</span></span> <span data-ttu-id="b741b-123">Den här filen finns i under katalogen _ *_CustomEvents_*\* i den användardefinierade TraceX-installations katalogen, som är som standard C:\ Azure_RTOS \tracex.</span><span class="sxs-lookup"><span data-stu-id="b741b-123">This file is located in the _ *_CustomEvents_*\* subdirectory of your user-defined TraceX installation directory, which defaults to c:\Azure_RTOS\TraceX.</span></span> <span data-ttu-id="b741b-124">En exempel katalog Sök väg visas i bild 30.</span><span class="sxs-lookup"><span data-stu-id="b741b-124">An example directory path is shown in Figure 30.</span></span>

<span data-ttu-id="b741b-125">![Skärm bild av en exempel katalog Sök väg. ](./media/user-guide/custom_events_folder.png)
 **Bild 30**</span><span class="sxs-lookup"><span data-stu-id="b741b-125">![Screenshot of an example directory path.](./media/user-guide/custom_events_folder.png)
**FIGURE 30**</span></span>

<span data-ttu-id="b741b-126">Den anpassade händelse konfigurations filen ***tracex_custom. trxc*** är en enkel ASCII-textfil som innehåller noll eller flera anpassade händelse definitioner.</span><span class="sxs-lookup"><span data-stu-id="b741b-126">The ***tracex_custom.trxc*** custom event configuration file is a simple ASCII text file containing zero or more custom event definitions.</span></span> <span data-ttu-id="b741b-127">Filens format är följande:</span><span class="sxs-lookup"><span data-stu-id="b741b-127">The format of the file is as follows:</span></span>

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

<span data-ttu-id="b741b-128">Varje rad mellan start och end används för att definiera en enskild anpassad händelse.</span><span class="sxs-lookup"><span data-stu-id="b741b-128">Each line between Start and End is used to define a single custom event.</span></span> <span data-ttu-id="b741b-129">TraceX innehåller en mall version av den här filen utan anpassade definierade händelser (inget mellan "Start" och "slut" etiketter).</span><span class="sxs-lookup"><span data-stu-id="b741b-129">TraceX provides a template version of this file with no custom events defined (nothing between the "Start" and "End" labels).</span></span> <span data-ttu-id="b741b-130">Formatet på en anpassad händelse definition är följande:</span><span class="sxs-lookup"><span data-stu-id="b741b-130">The format of a custom event definition is as follows:</span></span>

<span data-ttu-id="b741b-131">**nummer, namn, förkortning, top_color, bottom_color, Label1, Label2, Label2, Label4**</span><span class="sxs-lookup"><span data-stu-id="b741b-131">**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**</span></span>

<span data-ttu-id="b741b-132">där:</span><span class="sxs-lookup"><span data-stu-id="b741b-132">where:</span></span>

- <span data-ttu-id="b741b-133">Number: definierar det användardefinierade händelse numret, mellan 4096 och 65535.</span><span class="sxs-lookup"><span data-stu-id="b741b-133">number: Defines the user-defined event number, between 4096 and 65535, inclusive.</span></span></th>
- <span data-ttu-id="b741b-134">Namn: definierar det logiska namnet för den användardefinierade händelsen.</span><span class="sxs-lookup"><span data-stu-id="b741b-134">name: Defines the logical name for the user-defined event.</span></span></td>
- <span data-ttu-id="b741b-135">förkortning: definierar en användardefinierad händelse förkortning med två bokstäver.</span><span class="sxs-lookup"><span data-stu-id="b741b-135">abbreviation: Defines the two-letter user-defined event abbreviation.</span></span></td>
- <span data-ttu-id="b741b-136">top_color: definierar RGB-värdet för den övre halvan av ikonen, som är ett fyrsiffrigt tal inom parentes.</span><span class="sxs-lookup"><span data-stu-id="b741b-136">top_color: Defines the RGB value for the top-half of the icon, which is a three-digit number in parenthesis.</span></span> <span data-ttu-id="b741b-137">Några typiska RGB-definitioner är</span><span class="sxs-lookup"><span data-stu-id="b741b-137">Some typical RGB definitions are</span></span>
  - <span data-ttu-id="b741b-138">SVART = (0,0)</span><span class="sxs-lookup"><span data-stu-id="b741b-138">BLACK = (0,0,0)</span></span>       
  - <span data-ttu-id="b741b-139">VIT = (255 255 255)</span><span class="sxs-lookup"><span data-stu-id="b741b-139">WHITE = (255,255,255)</span></span>
  - <span data-ttu-id="b741b-140">RÖD = (255, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="b741b-140">RED = (255,0,0)</span></span>     
  - <span data-ttu-id="b741b-141">GRÖNT = (0255, 0)</span><span class="sxs-lookup"><span data-stu-id="b741b-141">GREEN = (0,255,0)</span></span>     
  - <span data-ttu-id="b741b-142">BLÅ = (0, 0255)</span><span class="sxs-lookup"><span data-stu-id="b741b-142">BLUE = (0,0,255)</span></span>     
  - <span data-ttu-id="b741b-143">GUL = (255255, 0)</span><span class="sxs-lookup"><span data-stu-id="b741b-143">YELLOW = (255,255,0)</span></span>   
  - <span data-ttu-id="b741b-144">CYAN = (0255 255)</span><span class="sxs-lookup"><span data-stu-id="b741b-144">CYAN = (0,255,255)</span></span>   
  - <span data-ttu-id="b741b-145">MAGENTA = (255, 0255)</span><span class="sxs-lookup"><span data-stu-id="b741b-145">MAGENTA = (255,0,255)</span></span>   
  <span data-ttu-id="b741b-146">Genom att använda RBG-specifikationen får användaren en rad olika färger för varje användardefinierad ikon.</span><span class="sxs-lookup"><span data-stu-id="b741b-146">Using the RBG specification gives the user a broad range of colors for each user-defined icon.</span></span> <span data-ttu-id="b741b-147">Mer information om RBG färg definition finns i: https://en.wikipedia.org/wiki/RGB#Digital_representations</span><span class="sxs-lookup"><span data-stu-id="b741b-147">For more information on RBG color definition, see: https://en.wikipedia.org/wiki/RGB#Digital_representations</span></span>
- <span data-ttu-id="b741b-148">botton_color: definierar RGB-värdet för den nedre halvan av ikonen, som är ett fyrsiffrigt tal inom parentes.</span><span class="sxs-lookup"><span data-stu-id="b741b-148">botton_color: Defines the RGB value for the bottom half of the icon, which is a three-digit number in parenthesis.</span></span>
- <span data-ttu-id="b741b-149">Label1: etikett för \***info_field_1** _, som anges i anropet _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b741b-149">label1: Label for ***info_field_1** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="b741b-150">Label2: etikett för \***info_field_2** _, som anges i anropet _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b741b-150">label2: Label for ***info_field_2** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="b741b-151">Label3: etikett för \***info_field_3** _, som anges i anropet _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b741b-151">label3: Label for ***info_field_3** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="b741b-152">Label4: etikett för \***info_field_4** _, som anges i anropet _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b741b-152">label4: Label for ***info_field_4** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>

<span data-ttu-id="b741b-153">Exempel definitioner för var och en av de två användardefinierade händelserna som används i det här kapitlet visas i bild 10,4.</span><span class="sxs-lookup"><span data-stu-id="b741b-153">Example definitions for each of the two user-defined events used in this chapter are shown in Figure 10.4.</span></span> <span data-ttu-id="b741b-154">Den första definitionen är för händelse 4096 på rad 5 i \***tracex_custom. trxc** _-filen.</span><span class="sxs-lookup"><span data-stu-id="b741b-154">The first definition is for event 4096 at line 5 of the \***tracex_custom.trxc** _ file.</span></span> <span data-ttu-id="b741b-155">Den här definitionen ger användardefinierad händelse 4096 namnet _ \* First_User_Event \* \*, anger en förkortning på två bokstäver i **FE**, gör den övre delen av ikonen röd, den nedre delen av ikonen grönt och namnger informations fälten som **First_Info1**, **First_Info2**, **First_Info3** och **First_Info4**.</span><span class="sxs-lookup"><span data-stu-id="b741b-155">This definition gives user-defined event 4096 the name _\*First_User_Event\*\*, specifies a two-letter abbreviation of **FE**, makes the top portion of the icon red, the bottom portion of the icon green, and names the information fields as **First_Info1**, **First_Info2**, **First_Info3**, and **First_Info4**.</span></span> <span data-ttu-id="b741b-156">Användardefinierad händelse 4098 definieras på samma sätt som rad 6 i **_tracex_custom. trxc_**.</span><span class="sxs-lookup"><span data-stu-id="b741b-156">User-defined event 4098 is defined similarly at line 6 of **_tracex_custom.trxc_**.</span></span>

<span data-ttu-id="b741b-157">![Skärm bild av exempel definitionerna för användardefinierade händelser. ](./media/user-guide/10.4.png)
 **Bild 31**</span><span class="sxs-lookup"><span data-stu-id="b741b-157">![Screenshot of the example definitions for the user-defined events.](./media/user-guide/10.4.png)
**FIGURE 31**</span></span>

<span data-ttu-id="b741b-158">Eftersom \***tracex_custom. trxc** _-filen läses av tracex under initieringen, måste tracex avslutas och startas om innan de anpassade ikon definitionerna kan börja gälla.</span><span class="sxs-lookup"><span data-stu-id="b741b-158">Since the \***tracex_custom.trxc** _ file is read by TraceX during initialization, TraceX must be exited and restarted before the custom icon definitions can take effect.</span></span> <span data-ttu-id="b741b-159">Bild 32 visar TraceX-visningen av användardefinierade händelser 452 och 453 med anpassade händelse ikoner definierade i _ *_tracex_custom. trxc_* \*.</span><span class="sxs-lookup"><span data-stu-id="b741b-159">Figure 32 shows the TraceX display of user-defined events 452 and 453 with the custom event icons defined in _\*_tracex_custom.trxc_\*\*.</span></span>

<span data-ttu-id="b741b-160">![Skärm bild av TraceX-visningen av användardefinierade händelser med ikonerna för anpassade händelser. ](./media/user-guide/10.5.png)
 **Figur 32**</span><span class="sxs-lookup"><span data-stu-id="b741b-160">![Screenshot of the TraceX display of user defined events with the custom event icons.](./media/user-guide/10.5.png)
**FIGURE 32**</span></span>

<span data-ttu-id="b741b-161">Den ytterligare informationen i den anpassade händelse definitionen visas när du väljer att använda ett dubbel klick, en mus över eller genom att klicka på den aktuella händelse knappen.</span><span class="sxs-lookup"><span data-stu-id="b741b-161">The additional information in the custom event definition is shown when the event you select using a double-click, mouse-over, or clicking the current event button.</span></span> <span data-ttu-id="b741b-162">Bild 33 visar hur du dubbelklickar på händelse 452.</span><span class="sxs-lookup"><span data-stu-id="b741b-162">Figure 33 shows the double-click selection on event 452.</span></span> <span data-ttu-id="b741b-163">Händelse namn och informations fält matchar alla exempel definitioner som har lagts till i ***tracex_custom. trxc***.</span><span class="sxs-lookup"><span data-stu-id="b741b-163">The event name and information fields all match the sample definition that was added to ***tracex_custom.trxc***.</span></span>

<span data-ttu-id="b741b-164">![Skärm bild av markeringen dubbelklicka på en händelse. ](./media/user-guide/10.6.png)
 **Figur 33**</span><span class="sxs-lookup"><span data-stu-id="b741b-164">![Screenshot of the double-click selection on an event.](./media/user-guide/10.6.png)
**FIGURE 33**</span></span>
