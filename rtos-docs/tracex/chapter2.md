---
title: Kapitel 2 – Installation och användning av Azure RTOS TraceX
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS TraceX-systemanalysverktyget.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 1a375975ef80cfb7b56466f5d91ed9a0ca00a20a38108e1b81f4fe8e5d85278d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802211"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a>Kapitel 2 – Installation och användning av Azure RTOS TraceX

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS TraceX-systemanalysverktyget. 

## <a name="product-distribution"></a>Produktdistribution

Du kan hämta TraceX-appen från [Microsoft App Store](https://microsoft.com/store/apps) genom att söka efter TraceX eller genom att [gå direkt till TraceX-sidan](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab). Gör sedan följande.

1. På sidan TraceX i App Store klickar du på knappen **Hämta** eller **Installera för** att installera TraceX.

1. Webbläsaren kan visa ett meddelande som frågar om du vill öppna Microsoft Store, som du ser i bilden nedan. I så fall väljer du **knappen** Öppna.
![Välj Öppna för att installera TraceX.](../guix/media/guix-studio/open-ms-store.png)

1. När installationen är klar väljer du **knappen** Starta. 

## <a name="using-tracex"></a>Använda TraceX

Det är lika enkelt att använda TraceX som att öppna en spårningsfil i TraceX! Kör TraceX via knappen ***Start** _ . Nu kommer du att se det grafiska användargränssnittet för TraceX (GUI). Nu är du redo att använda TraceX för att grafiskt visa en befintlig målspårningsbuffert. Det gör du enkelt genom att klicka på _ *_File -> Open ,_** och sedan ange den binära spårningsfilen.

>[!IMPORTANT]
>*Du kan också dubbelklicka på en spårningsfil med tillägget **trx,** som automatiskt startar TraceX.*

![Skärmbild av TraceX-gränssnittet.](./media/user-guide/screen_shot_8.png)

**BILD 1**

>[!IMPORTANT]
>*Se kapitel **5 för instruktioner** om hur du skapar spårningsbuffertar på målet med ThreadX.*

## <a name="tracex-examples"></a>TraceX-exempel

Första gången du kör TraceX-programmet, eller när TraceX-programmet uppdateras, uppmanas du att installera TraceX-exempelspårningsfilerna och filen custom_events.trxc till en användardefinierad katalog på den lokala datorn.

När det här installationssteget har slutförts finns exempelspårningsfilerna med tillägget **trx** i underkatalogen **TraceFiles** i installationsmappen. De här färdiga exemplen hjälper dig att bli bekväm med att använda TraceX på spårningsbuffertar som genereras av ThreadX som körs med ditt program.

Ett exempel på en spårningsfil som alltid finns är filen ***demo_threadx.trx** _. Den här exempelspårningsfilen visar körningen av ThreadX-standarddemo, enligt beskrivningen i kapitel 6 i _ThreadX användarhandbok*.

![Skärmbild av den öppna dialogrutan i TraceX.](./media/user-guide/screen_shot_9.png)

**BILD 2**
