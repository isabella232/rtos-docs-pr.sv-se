---
title: GUIX Studio-kommandorad
description: GUIX Studio tillhandahåller kommandoradsanrop som är användbart för bygg-pipelines som krävs för att uppdatera studiogenererade utdatafiler.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: bd88054d974aabea30b50c6f4e10b4c5df9994db03ab84a4a5d8f9394b4d6ed8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785404"
---
# <a name="chapter-9-guix-studio-command-line"></a>Kapitel 9: GUIX Studio-kommandoraden

GUIX Studio stöder kommandoradsanrop, vilket är användbart för bygg-pipelines som krävs för att uppdatera de Studio-genererade utdatafilerna.

## <a name="command-line-usage"></a>Command-Line användning

**Användning: guix_studio** \[ FÖR \] \[ ALTERNATIV\]

Öppna *.gxp-projektet.*

Öppna Studio-projektet och generera önskade utdatafiler.


**Exempel:**

`guix_studio demo.gxp`  
Öppna projektet "demo.gxp"


`guix_studio.exe –p demo.gxp`  
Öppna projektet "demo.gxp"


`guix_studio.exe –n –p demo.gxp`  
Generera alla utdatafiler för demo.gxp-projektet.

`guix_studio.exe –n –r –p demo.gxp`  
Generera resursfiler för demo.gxp-projekt


## <a name="command-line-options"></a>Command-Line alternativ

```C
***-n --nogui***  
```

Alternativet "nogui". Be GUIX Studio att köras utan att starta gränssnittet för fönstergränssnittet.

```C
***-o pathname***  
***--log***  
```

Loggalternativ, ange en loggfil.

```C
***-b***  
***--binary***  
```

Alternativet Binär resurs. Skapar en binär resursfil i stället för en C-fil.

```C
***-d display1, display2***  
***--display***  
```

Alternativet Visningsnamn. Om det här alternativet används inkluderas endast de angivna visningsnamnen i genererade resurs- eller specifikationsfiler. Om det här alternativet inte används inkluderas alla skärmar.

```C
***-t theme1, theme2***  
***--theme***  
```

Alternativ för temanamn. Om det här alternativet används inkluderas endast de angivna temanamnen i genererade resurs- eller specifikationsfiler. Om det här alternativet inte används ingår alla teman.

```C
***-l langage1, language2***  
***--language***  
```

Alternativ för språknamn. Om det här alternativet används inkluderas de angivna språknamnen i de genererade resurs- eller specifikationsfilerna. Annars inkluderas alla språknamn.

```C
***-r [filename]***  
***--resource***  
```

Resursalternativet anger att Studio ska skapa en resursfil för tidigare avsedda visning(er), tema och språk.

```C
***-s [filename]***  
***--specification***  
```

Specifikationsalternativet anger att Studio ska skapa en specifikationsfil för angivna skärmar, tema och språk.

```C
***-p project_pathname***  
***--project***  
```

Project sökvägsnamn anger du exempelprojektet som ska läsas in.

```C
***-i [pathname]***  
***--import***  
```

Importera strängen från xliff- eller csv-formatfilen.

***--big_endian***  
Generera resursdata i storslutsformat.
