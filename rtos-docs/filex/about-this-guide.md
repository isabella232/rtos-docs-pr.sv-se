---
title: Användar handbok för Azure återställnings tider FileX
description: Den här guiden innehåller omfattande information om Azure återställnings tider FileX, real tids fil systemet med höga prestanda från Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0ebcebdd2b227ed8d9ccf8b3078b716f90f35bef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825560"
---
# <a name="about-this-filex-user-guide"></a>Om den här användar handboken för FileX

Den här guiden innehåller omfattande information om Azure återställnings tider FileX, det högpresterande inbäddade fil systemet i real tid från Microsoft. För att få ut mesta möjliga av den här guiden bör du vara bekant med standard operativ system funktioner i real tid, FAT-filsystemtjänster och programmeringsspråket C.

## <a name="organization"></a>Organisation

[Kapitel 1](chapter1.md) – introducerar Azure återställnings tider FileX

[Kapitel 2](chapter2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider-FileX med ditt Azure återställnings tider ThreadX-program

[Kapitel 3](chapter3.md) – innehåller en funktionell översikt över Azure återställnings tider FileX-systemet och grundläggande information om fat-format för fil system

[Kapitel 4](chapter4.md) – information om programmets gränssnitt till Azure återställnings tider FileX

[Kapitel 5](chapter5.md) – beskriver den tillhandahållna Azure återställnings tider FileX ram-drivrutinen och hur du skriver egna anpassade Azure återställnings tider FileX-drivrutiner

[Kapitel 6](chapter6.md) – beskriver den feltoleranta modulen för Azure återställnings tider FileX

[Bilaga A](appendix-a.md) – Azure återställnings tider FileX-tjänster

[Bilaga B](appendix-b.md) – Azure återställnings tider FileX-konstanter

[Bilaga C](appendix-c.md) – data typer för Azure återställnings tider-FileX

[Bilaga D](appendix-d.md) – ASCII-diagram

## <a name="guide-conventions"></a>Guide konventioner

*Kursiv stil* – teckensnittet noterar bok titlar, betonar viktiga ord och indikerar variabler.

**Fetstil** – typsnitt anger fil namn, viktiga ord och betonar viktiga ord och variabler.

> [!NOTE]
> Informations symboler drar uppmärksamheten till viktig eller ytterligare information som kan påverka prestandan eller funktionen.

> [!IMPORTANT]
> Varnings symboler drar uppmärksamhet till situationer som utvecklare bör undvika eftersom de kan orsaka allvarliga fel.

## <a name="filex-data-types"></a>FileX data typer

Förutom de anpassade data typerna för kontroll strukturen i Azure återställnings tider-FileX, finns det en serie särskilda data typer som används i Azure återställnings tider FileX service Call-gränssnitt. Dessa särskilda data typer mappar direkt till data typer för den underliggande C-kompilatorn. Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer. Den exakta implementeringen ärvs från Azure återställnings tider ThreadX och finns i filen tx_port. h som ingår i Azure återställnings tider ThreadX-distributionen.

Följande är en lista över data typer för Azure återställnings tider FileX service Call och deras associerade betydelser.
| Typ  | Beskrivning  |
|---|---|
| **UINT** | Basic-osignerat heltal. Den här typen måste ha stöd för 8-bitars osignerade data. den är dock mappad till den mest användbara osignerade data typen. |
| **ULONG** | Osignerad lång typ. Den här typen måste ha stöd för 32-bitars osignerade data. |
| **VOID** | Nästan alltid ekvivalent med kompilatorns void-typ. |
| **HÄNGANDE** | Oftast en vanlig 8-bitars tecken typ. |
| **ULONG64** | 64-bit data typ med osignerat heltal. |

Ytterligare data typer används i FileX-källan. De finns antingen i ***tx_port. h** _ eller _ *_fx_port. h_** filer.

## <a name="customer-support-center"></a>Kund Support Center

Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här. Lämna oss med följande information i ett e-postmeddelande så att vi kan lösa ditt support ärende mer effektivt.

1. En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller FileX som föregåde problemet.
3. Innehållet i _tx_version_id-och _fx_version_id-strängar som finns i ***tx_port. h**_ -och _ *_fx_port. h_**-filerna i distributionen. De här strängarna ger oss värdefull information om din kör tids miljö.
4. Innehållet i RAM-minnet för följande **ulong** -variabler. Dessa variabler ger oss information om hur dina ThreadX-och FileX-bibliotek skapades:

    **_tx_build_options**

    **_fx_system_build_options1**

    **_fx_system_build_options2**

    **_fx_system_build_options3**
