---
title: Kommando rad för GUIX Studio
description: GUIX Studio tillhandahåller kommando rads anrop som är användbart för att skapa pipelines som krävs för att uppdatera de Studio-genererade utdatafilerna.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9f9bfc67c524a77b5bf736407bf2ca372ce98308
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826292"
---
# <a name="chapter-9-guix-studio-command-line"></a>Kapitel 9: kommando rads kommando rad för GUIX Studio

GUIX Studio stöder kommando rads anrop, vilket är användbart för att skapa pipelines som krävs för att uppdatera de Studio-genererade utdatafilerna.

## <a name="command-line-usage"></a>Command-Line användning

**Användning:** guix_studio \[ alternativ \] \[ argument\]

Öppna *. GXP* -projektet.

Öppna Studio-projektet och generera önskade utdatafiler.


**Exempel:**

`guix_studio demo.gxp`  
Öppna "demo. GXP"-projekt


`guix_studio.exe –p demo.gxp`  
Öppna "demo. GXP"-projekt


`guix_studio.exe –n –p demo.gxp`  
Generera alla utdatafiler för demo. GXP-projektet.

`guix_studio.exe –n –r –p demo.gxp`  
Generera resursfiler för demo. GXP-projekt


## <a name="command-line-options"></a>Command-Line alternativ

```C
***-n --nogui***  
```

Alternativet "nogui". Berätta för GUIX Studio att köra utan att starta GRÄNSSNITTs gränssnittet för Windowing.

```C
***-o pathname***  
***--log***  
```

Logg alternativ, ange en loggfil.

```C
***-b***  
***--binary***  
```

Alternativ för binär resurs. Skapar en binär resurs fil i stället för en C-fil.

```C
***-d display1, display2***  
***--display***  
```

Alternativet visnings namn. Om det här alternativet används inkluderas bara de angivna visnings namnen i alla genererade resurs-eller Specifikations filer. Om det här alternativet inte används tas alla visningar med.

```C
***-t theme1, theme2***  
***--theme***  
```

Tema namn (n). Om det här alternativet används inkluderas bara de angivna temanamn i alla genererade resurs-eller Specifikations filer. Om det här alternativet inte används ingår alla teman.

```C
***-l langage1, language2***  
***--language***  
```

Alternativ för språk namn. Om det här alternativet används inkluderas de angivna språk namnen i de genererade resurs-eller Specifikations filerna. Annars ingår alla språk namn.

```C
***-r [filename]***  
***--resource***  
```

Alternativet resurs anger att Studio ska skapa en resurs fil för tidigare angivna visnings alternativ, teman och språk.

```C
***-s [filename]***  
***--specification***  
```

Alternativet specifikation anger att Studio ska skapa en Specifikations fil för angivna visnings alternativ, teman och språk.

```C
***-p project_pathname***  
***--project***  
```

Alternativet projekt Sök väg anger du det exempel projekt som ska läsas in.

```C
***-i [pathname]***  
***--import***  
```

Importera sträng från XLIFF-eller CSV-format fil.

***--big_endian***  
Generera resurs data i big-endian-format.
