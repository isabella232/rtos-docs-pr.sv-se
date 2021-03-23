---
title: Användar guide för GUIX Studio
description: Den här guiden innehåller omfattande information om GUIX Studio, den Microsoft Windows-baserade Rapid UI utvecklings miljön som är särskilt utformad för GUIX runtime-biblioteket från Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6a5d628581d4c6b44ff093bac45790d6e2755349
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827171"
---
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a>Kapitel 1: Introduktion till Azure återställnings tider GUIX Studio

Azure återställnings tider GUIX Studio är en Microsoft Windows-baserad snabb utvecklings miljö som är särskilt utformad för GUIX runtime-biblioteket från Microsoft.

Inbäddade UI-utvecklare kan använda WYSIWYG-skärmbilden i GUIX Studio för att snabbt skapa och uppdatera sitt inbäddade användar gränssnitt med hjälp av GUIX-körnings miljön. GUIX Studio-design sparas och bevaras i en GUIX Studio-projektfil som har fil namns tillägget. GXP. När designen är klar för körning på målet genererar GUIX Studio C-kod som innehåller all nödvändig GRÄNSSNITTs information och kod.

## <a name="guix-studio-requirements"></a>Krav för GUIX Studio

För att fungera korrekt kräver Microsofts GUIX Studio *Windows XP* (eller senare). Systemet bör ha minst 200 MB RAM-minne, 2 GB ledigt hårddisk utrymme och minst 1024x768 med 256 färger. Dessutom måste det inbäddade programmet köras på *ThreadX/GUIX v 6.0* eller senare.

Om du vill kunna skapa och köra det inbäddade GRÄNSSNITTs programmet som en fristående Microsoft Windows-körbar fil, behöver du också en kompilerare eller en build-miljö som kan kompilera C-källkod för att skapa en Microsoft Windows-körbar fil. I utvärderings paketet som ingår i GUIX Studio ingår även Visual Studio 2019-kompatibla projektfiler och lösningar för vart och ett av de tillhandahållna exempel programmen. Om du använder en annan kompilator måste du skapa dina egna projektfiler eller skapa filer för att skapa dina exempel program eller kontakta supporten på https://aka.ms/azrtos-support .

## <a name="guix-studio-constraints"></a>GUIX Studio-begränsningar

Design verktyget GUIX Studio UI design verktyg har flera begränsningar, enligt följande:

- Högst 4 visningar per projekt.
- Högst 100 000 widgetar per GUIX Studio-projekt.
- Högst 100 000 distinkta resurser, t. ex. färger, teckensnitt, pixelmaps, strängar osv.