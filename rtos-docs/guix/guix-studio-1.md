---
title: Användarhandbok för GUIX Studio
description: Den här guiden innehåller omfattande information om GUIX Studio, Microsoft Windows-baserad miljö för snabb UI-utveckling som är särskilt utformad för GUIX-körningsbiblioteket från Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 2c36fb794816cb1acd51ec81f48c0dabe509336f27914050b6206f19bf8ceeff
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789841"
---
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a>Kapitel 1: Introduktion till Azure RTOS GUIX Studio

Azure RTOS GUIX Studio är en Microsoft Windows-baserad miljö för snabb UI-utveckling som är särskilt utformad för GUIX-körningsbiblioteket från Microsoft.

Inbäddade användargränssnitt Utvecklare kan använda GUIX Studio WYSIWYG-skärmdesignern för att snabbt skapa och uppdatera sitt inbäddade användargränssnitt med GUIX-körningsmiljön. GUIX Studio-designer sparas och underhålls i en GUIX Studio-projektfil med filnamnstillägget .gxp. När din design är redo för körning på målet genererar GUIX Studio C-kod som innehåller all nödvändig gränssnittsinformation och kod.

## <a name="guix-studio-requirements"></a>Krav för GUIX Studio

För att fungera korrekt kräver Microsofts GUIX Studio *Windows XP* (eller högre). Systemet ska ha minst 200 MB RAM-minne, 2 GB tillgängligt hårddiskutrymme och en minsta skärm på 1 024 x 768 med 256 färger. Dessutom måste det inbäddade programmet köras på *ThreadX/GUIX V6.0* eller senare.

Om du vill kunna skapa och köra det inbäddade ui-programmet som en fristående körbar Microsoft Windows-fil behöver du även en kompilator eller byggmiljö som kan kompilera C-källkod för att skapa en körbar Microsoft Windows-fil. Utvärderingspaketet som ingår i GUIX Studio innehåller även Visual Studio 2019-kompatibla projektfiler och lösningar för vart och ett av de tillhandahållna exempelprogrammen. Om du använder en annan kompilator måste du skapa egna projektfiler eller skapa filer för att skapa exempelprogram eller kontakta supporten på https://aka.ms/azrtos-support .

## <a name="guix-studio-constraints"></a>GUIX Studio-begränsningar

Designverktyget för GRÄNSSNITTET i GUIX Studio har flera begränsningar, enligt följande:

- Högst 4 visningar per projekt.
- Högst 100 000 widgetar per GUIX Studio-projekt.
- Högst 100 000 distinkta resurser, t.ex. färger, teckensnitt, pixelkartor, strängar osv.