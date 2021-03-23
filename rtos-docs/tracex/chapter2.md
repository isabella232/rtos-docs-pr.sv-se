---
title: Kapitel 2 – installation och användning av Azure återställnings tider TraceX
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av system analys verktyget för Azure återställnings tider-TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 05d7fe3df38c7e8a3480c8ea0d4922a109de9ede
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827573"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a>Kapitel 2 – installation och användning av Azure återställnings tider TraceX

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av system analys verktyget för Azure återställnings tider-TraceX. 

## <a name="product-distribution"></a>Produkt distribution

Du kan hämta TraceX-appen från [Microsoft App Store](https://microsoft.com/store/apps) genom att söka efter TraceX, eller genom att gå direkt till [TraceX-sidan](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab). Gör sedan följande.

1. På sidan TraceX i App Store klickar du på knappen **Hämta** eller **Installera** för att installera TraceX.

1. Webbläsaren kan visa ett meddelande som frågar om du vill öppna Microsoft Store, som du ser i bilden nedan. Om det gör det väljer du knappen **Öppna** .
![Välj öppna för att installera TraceX.](../guix/media/guix-studio/open-ms-store.png)

1. När installationen är klar väljer du knappen **Starta** . 

## <a name="using-tracex"></a>Använda TraceX

Att använda TraceX är lika enkelt som att öppna en spårnings fil i TraceX! Kör TraceX via knappen ***Start** _. Nu kommer du att titta på användar gränssnittet för TraceX (GUI). Du är nu redo att använda TraceX för att grafiskt visa en befintlig mål spårnings-buffert. Det gör du enkelt genom att klicka på _ *_fil-> öppna,_** sedan ange den binära spårnings filen.

>[!IMPORTANT]
>*Du kan också dubbelklicka på en spårnings fil med en utökning av **TRX,** som automatiskt startar TraceX.*

![Skärm bild av TraceX-ANVÄNDARGRÄNSSNITTET.](./media/user-guide/screen_shot_8.png)

**BILD 1**

>[!IMPORTANT]
>*Se **kapitel 5** för instruktioner om hur du genererar ThreadX i målet med hjälp av.*

## <a name="tracex-examples"></a>TraceX-exempel

Första gången du kör TraceX-programmet eller när TraceX-programmet uppdateras uppmanas du att installera TraceX-exemplen och filen custom_events. trxc i en användardefinierad katalog på den lokala datorn.

När det här installations steget har slutförts visas exemplet med tillägget **TRX** i undermappen **TraceFiles** i installationsmappen. De här fördefinierade exemplen hjälper dig att komma igång med att använda TraceX på de spårningsfiler som genereras av ThreadX som körs med ditt program.

Ett exempel på en spårnings fil är filen ***demo_threadx. trx** _. I den här exempel spårnings filen visas körningen av standard demonstrationen av ThreadX, enligt beskrivningen i kapitel 6 i _ThreadX Användar handbok *.

![Skärm bild av dialog rutan Öppna i TraceX.](./media/user-guide/screen_shot_9.png)

**BILD 2**
