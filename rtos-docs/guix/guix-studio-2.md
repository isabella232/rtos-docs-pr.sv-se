---
title: Installation och användning av GUIX Studio
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av GUIX Studio UI system design Tool.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d7b5f94c26842b408ea1b00aeeb78e111bea3623
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827168"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a>Kapitel 2: installation och användning av GUIX Studio

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av GUIX Studio UI system design Tool. 

## <a name="product-distribution"></a>Produkt distribution

Du kan hämta GUIX Studio-appen från [Microsoft App Store](https://microsoft.com/store/apps) genom att söka efter GUIX Studio, eller genom att gå direkt till [sidan GUIX Studio](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab). Gör sedan följande.

1. Från sidan GUIX Studio i App Store klickar du på knappen **Hämta** eller **Installera** för att ladda ned GUIX Studio.

1. Webbläsaren kan visa ett meddelande som frågar om du vill öppna Microsoft Store, som du ser i bilden nedan. Om det gör det väljer du knappen **Öppna** .
![Välj öppna för att installera GUIX Studio.](./media/guix-studio/open-ms-store.png)

1. När installationen är klar väljer du knappen **Starta** .

1. Första gången som GUIX Studio startar visas en dialog ruta där du tillfrågas om du vill klona GUIX-lagrings platsen till din lokala dator. Du kan antingen välja att klona lagrings platsen, peka på där du redan har klonat lagrings platsen eller välja att inte klona lagrings platsen (i så fall är ett exempel projekt installerat på datorn).
![Välj att klona lagrings platsen, peka på en redan klonad lagrings platsen eller hoppa över.](./media/guix-studio/clone-repo.png)

> ![!NOTE]
> Du kan gå tillbaka till den här dialog rutan när som helst genom att välja **Konfigurera** från huvud menyn i GUIX Stuido, följt av **GUIX-lagringsplatsen**.

När Start processen är klar kan du använda GUIX Studio.

## <a name="using-guix-studio"></a>Använda GUIX Studio

Att använda GUIX Studio är ett enkelt sätt att köra GUIX Studio via knappen "***Starta***". Nu kommer du att gå med i användar gränssnittet för GUIX Studio. Du är nu redo att använda GUIX Studio för att grafiskt skapa ditt inbäddade användar gränssnitt. Härifrån kan du skapa ett nytt projekt eller öppna ett befintligt projekt, inklusive GUIX-exempel projekt.

> [!NOTE]
> Du kan också dubbelklicka på en GUIX Studio-projektfil med tillägget "**GXP",** som automatiskt startar GUIX Studio och öppnar det refererade projektet.

## <a name="guix-studio-project-samples"></a>Projekt exempel för GUIX Studio

Ett antal exempel på GUIX Studio-projektfiler med tillägget "***GXP**_" finns i_ * under katalogen "_samples_* *" i installationen. Dessa färdiga exempel projekt hjälper dig att bli van vid att använda GUIX Studio.

En exempel projekt fil som alltid finns är filen ***samples/demo_guix_simple/guix_simple. GXP** _. I den här exempel projekt filen visas definitionen av ett enkelt GUIX-gränssnitt, enligt beskrivningen i _ *_kapitel 7_** i det här dokumentet.

![Skärm bild av användar gränssnittet för GUIX Studio.](./media/guix-studio/image_10.png)

**Bild 1**

## <a name="keyboard-shortcuts"></a>Kortkommandon

- **CTRL + N:** Nytt projekt
- **CTRL + O:** Öppna projekt
- **CTRL + S:** Spara projekt
- **CTRL + SHIFT + S:** Spara projektet som
- **Alt + F4:** Programmet
