---
title: Installation och användning av GUIX Studio
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av GUIX Studio UI-systemdesignverktyget.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 55d2b0ac08bdceebdf286effe4bbc679320541243ff78359deafe0858a7b597e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786480"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a>Kapitel 2: Installation och användning av GUIX Studio

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av GUIX Studio UI-systemdesignverktyget. 

## <a name="product-distribution"></a>Produktdistribution

Du kan hämta GUIX Studio-appen från [Microsoft App Store](https://microsoft.com/store/apps) genom att söka efter GUIX Studio eller genom att gå direkt till [GUIX Studio-sidan](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab). Gör sedan följande.

1. Från GUIX Studio-sidan i App Store klickar du på knappen **Hämta** eller **Installera för att** ladda ned GUIX Studio.

1. Webbläsaren kan visa ett meddelande som frågar om du vill öppna Microsoft Store, som du ser i bilden nedan. I så fall väljer du **knappen** Öppna.
![Välj Öppna för att installera GUIX Studio.](./media/guix-studio/open-ms-store.png)

1. När installationen är klar väljer du **knappen** Starta.

1. Första gången GUIX Studio startas visas en dialogruta som frågar om du vill klona GUIX-lagringsplatsen till den lokala datorn. Du kan antingen välja att klona lagringsplatsen, peka på den plats där du redan har klonat lagringsplatsen eller välja att inte klona lagringsplatsen alls (i så fall installeras ett exempelprojekt på datorn).
![Välj att klona lagringsplatsen, peka på en redan klonad lagringsplats eller hoppa över.](./media/guix-studio/clone-repo.png)

> ![!NOTE]
> Du kan gå tillbaka till den  här dialogrutan när som helst genom att välja Konfigurera på huvudmenyn i GUIX Stuido, följt av **GUIX-lagringsplats**.

När startprocessen är klar är du redo att använda GUIX Studio.

## <a name="using-guix-studio"></a>Använda GUIX Studio

Det är enkelt att använda GUIX Studio – du behöver bara köra GUIX Studio via ***knappen "Starta".*** Nu ska du observera ANVÄNDArgränssnittet för GUIX Studio. Nu är du redo att använda GUIX Studio för att grafiskt skapa ditt inbäddade användargränssnitt. Härifrån skapar du ett nytt projekt eller öppnar ett befintligt projekt, inklusive GUIX-exempelprojekten.

> [!NOTE]
> Du kan också dubbelklicka på en GUIX Studio-projektfil med tillägget "**gxp,**" som automatiskt startar GUIX Studio och öppnar det refererade projektet.

## <a name="guix-studio-project-samples"></a>GUIX Studio Project exempel

En serie GUIX Studio-exempelprojektfiler med tillägget "***gxp**" finns i _underkatalogen "_ * _Exempel_**" i din installation. Dessa färdiga exempelprojekt hjälper dig att bli bekväm med att använda GUIX Studio.

Ett exempel på en projektfil som alltid finns är filen ***samples/demo_guix_simple/guix_simple.gxp** _. Den här exempelprojektfilen visar definitionen av ett enkelt GUIX-användargränssnitt, enligt beskrivningen i _ *_Kapitel 7_** i det här dokumentet.

![Skärmbild av användargränssnittet för GUIX Studio.](./media/guix-studio/image_10.png)

**Bild 1**

## <a name="keyboard-shortcuts"></a>Kortkommandon

- **Ctrl + N:** Ny Project
- **Ctrl + O:** Öppna Project
- **Ctrl + S:** Spara Project
- **Ctrl + Skift + S:** Spara Project som
- **Alt + F4:** Avsluta
