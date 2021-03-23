---
title: Kapitel 6 – Azure återställnings tider FileX fel tolerans modul
description: Det här kapitlet innehåller en beskrivning av den feltoleranta modulen i Azure återställnings tider FileX som är utformad för att underhålla fil systemets integritet om mediet förlorar ström eller matas ut i mitten av en fil skrivnings åtgärd.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 68a24f0345a2c4d3e824270699b00a2daab32f8e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826505"
---
# <a name="chapter-6---azure-rtos-filex-fault-tolerant-module"></a>Kapitel 6 – Azure återställnings tider FileX fel tolerans modul

Det här kapitlet innehåller en beskrivning av den feltoleranta modulen i Azure återställnings tider FileX som är utformad för att underhålla fil systemets integritet om mediet förlorar ström eller matas ut i mitten av en fil skrivnings åtgärd.

## <a name="filex-fault-tolerant-module-overview"></a>Översikt över FileX feltolerant modul

När ett program skriver data till en fil, uppdaterar FileX både data kluster och system information. Dessa uppdateringar måste utföras som en atomisk åtgärd för att hålla informationen i fil systemet konsekvent. Om du till exempel lägger till data i en fil måste FileX hitta ett tillgängligt kluster i mediet, uppdatera FAT-kedjan, uppdatera längden som har arkiverats i katalog posten och eventuellt uppdatera det första kluster numret i katalog posten. Antingen ett strömavbrott eller en medie utmatning kan avbryta sekvensen av uppdateringar, vilket lämnar fil systemet i ett inkonsekvent tillstånd. Om det inkonsekventa läget inte korrigeras kan data som uppdateras gå förlorade och på grund av skada på system informationen kan efterföljande fil system åtgärder skada andra filer eller kataloger på mediet.

Den feltoleranta modulen FileX fungerar med de Journal steg som krävs för att uppdatera en fil *innan* de här stegen tillämpas på fil systemet. Om fil uppdateringen lyckas tas dessa logg poster bort. Men om fil uppdateringen avbryts lagras logg posterna på mediet. Nästa gången mediet monteras identifierar FileX dessa logg poster från den tidigare (oavslutade) Skriv åtgärden. I sådana fall kan FileX återställas efter fel genom att antingen återställa de ändringar som redan har gjorts i fil systemet eller genom att tillämpa de nödvändiga ändringarna för att slutföra den tidigare åtgärden. På så sätt upprätthåller FileX-feltolerant modul fil systemets integritet om mediet förlorar ström under en uppdaterings åtgärd.

> [!IMPORTANT]
> *FileX feltolerant modul är inte utformad för att förhindra skada av fil system som orsakas av fysiskt medie fel med giltiga data.*

> [!IMPORTANT]
> *När FileX-feltolerant modul skyddar ett medium, får inte mediet monteras av något annat än FileX med feltolerant aktiverat. Detta kan orsaka att logg posterna i fil systemet är inkonsekventa med system information på mediet. Om FileX feltolerant module försöker bearbeta logg poster när mediet har uppdaterats av ett annat fil system, kan återställnings proceduren Miss lyckas, vilket lämnar hela fil systemet i ett oförutsägbart tillstånd.*

## <a name="use-of-the-fault-tolerant-module"></a>Användning av fel tolerans modulen

FileX-feltolerant funktion är tillgänglig för alla FAT-filsystem som stöds av FileX, inklusive FAT12, FAT16, FAT32 och exFAT. Om du vill aktivera den feltoleranta funktionen måste FileX skapas med symbolen **FX_ENABLE_FAULT_TOLERANT** definierad. Vid körning startar programmet feltolerant tjänst genom att anropa **_fx_fault_tolerant_enable_*_ omedelbart efter anropet till _*_fx_media_open_**. När fel tolerans har Aktiver ATS skyddas alla fil skrivnings åtgärder till det angivna mediet. Fel tolerans modulen är som standard inte aktive rad.

> [!IMPORTANT]
> * Programmet måste se till att fil systemet inte kommer åt före ***fx_fault_tolerant_enable** _ anropas. Om programmet skriver data till fil systemet före den feltoleranta aktiveringen, kan Skriv åtgärden skada mediet om tidigare Skriv åtgärder inte hade slutförts och fil systemet inte återställdes med feltolerant logg entries._

## <a name="filex-fault-tolerant-module-log"></a>Logg för FileX feltolerant modul

FileX fel tolerans loggen tar upp ett logiskt kluster i Flash. Indexet till Start kluster numret för klustret registreras i Start sektorn för mediet, med en förskjutning som anges av symbolen **FX_FAULT_TOLERANT_BOOT_INDEX**. Som standard är den här symbolen definierad som 116. Den här platsen väljs eftersom den är markerad som reserverad i FAT12/16/32-och exFAT-specifikationen.

Bild 5, "logg strukturens layout", visar logg strukturens allmänna layout. Logg strukturen innehåller tre avsnitt: logg huvud, FAT-kedja och logg poster.

> [!IMPORTANT]
> *Alla värden för flera byte som lagras i logg posterna är i litet endian-format.*

![Layout för logg struktur](./media/user-guide/log-structure-layout.png)

**Bild 5. Layout för logg struktur**

Logg huvud området innehåller information som beskriver hela logg strukturen och förklarar varje fält i detalj.

**TABELL 8. Logg huvuds Area**

|Fält|Storlek (i byte)|Description|
|-----|--------------|-----------|
|ID|4|Identifierar en feltolerant logg struktur för FileX. Logg strukturen betraktas som ogiltig om ID-värdet inte är 0x46544C52.|
|Total storlek|2|Anger den totala storleken (i byte) för hela logg strukturen.|
|Huvud kontroll Summa|2|Kontroll summa som konverterar logg huvuds ytan. Logg strukturen betraktas som ogiltig om huvud fälten inte kan verifiera kontroll summan.|
|Versionsnummer|2|FileX-feltoleranta huvud-och del versions nummer.|
|Reserverat|2|För framtida expansion.|

Logg huvuds ytan följs av logg ytan FAT-kedja. Bild 9 innehåller information som beskriver hur FAT-kedjan ska ändras. Det här logg området innehåller information om de kluster som allokeras till en fil, de kluster som tas bort från en fil och där infogningen/borttagningen ska vara och beskriver varje fält i logg området FAT-kedja.

**TABELL 9. Logg områden för FAT-kedja**

|Fält|Storlek (i byte)|Beskrivning|
|-----|--------------|-----------|
|Logg kontroll summa för FAT-kedja|2|Kontroll summa för hela logg ytan FAT-kedja. Logg arean för FAT-kedjan betraktas som ogiltig om verifieringen av kontroll summan Miss lyckas.|
|Flagga|1|Giltiga flagg värden är:<br/>0x01 FAT-kedja giltig<br />protokollnumret 0x02-BITMAPP används|
|Reserverat|1|Reserverad för framtida användning|
|Insättnings punkt – överst|4|Klustret (som hör till den ursprungliga FAT-kedjan) där den nya kedjan ska kopplas till.|
|Huvud kluster för ny FAT-kedja|4|Det första klustret i den nyligen skapade FAT-kedjan|
|Huvud kluster för ursprunglig FAT-kedja|4|Det första klustret i den del av den ursprungliga FAT-kedjan som ska tas bort.|
|Insättnings punkt – bakåt|4|Det ursprungliga klustret där den nyligen skapade FAT-kedjan kopplas till.|
|Nästa borttagnings punkt|4|Det här fältet hjälper till med rensnings proceduren för FAT-kedjan.|

Fältet logg poster innehåller logg poster som beskriver de ändringar som krävs för att återställa efter ett fel. Det finns tre typer av logg poster som stöds i FileX feltolerant modul: FAT-loggpost; Katalog logg post; och Bitmap-loggpost.

Följande tre figurer och tre tabeller beskriver dessa logg poster i detalj.

![Logg post för FAT](./media/user-guide/fat-log-entry.png)

**Bild 6. Logg post för FAT**

**TABELL 10. Logg post för FAT**

|Fält|Storlek (i byte)|Beskrivning|
|-----|--------------|-----------|
Typ|2|Typ av post måste vara FX_FAULT_TOLERANT_FAT_LOG_TYPE|
|Storlek|2|Storlek på posten|
|Kluster nummer|4|Kluster nummer|
|Värde|4|Värde som ska skrivas till FAT-posten|

![Katalog logg post](./media/user-guide/directory-log-entry.png)

**Bild 7. Katalog logg post**

**TABELL 11. Katalog logg post**

|Fält|Storlek (i byte)|Beskrivning|
|-----|--------------|-----------|
|Typ|2|Typ av post måste vara FX_FAULT_TOLERANT_DIRECTORY_LOG_TYPE|
|Storlek|2|Storlek på posten|
|Sektor förskjutning|4|Offset (i byte) i den sektor där katalogen finns.|
|Logg sektor|4|Den sektor där katalog posten finns|
|Loggdata|Variabel|Katalog postens innehåll|

![Loggpost för Bitmap](./media/user-guide/bitmap-log-entry.png)

**Figur 8. Loggpost för Bitmap**

**TABELL 12. Loggpost för Bitmap**

|Fält|Storlek (i byte)|Beskrivning|
|-----|--------------|-----------|
|Typ|2|Typ av post måste vara FX_FAULT_TOLERANT_BITMAP_LOG_TYPE|
|Storlek|2|Storlek på posten|
|Kluster nummer|4|Kluster nummer|
|Värde|4|Värde som ska skrivas till FAT-posten|

## <a name="fault-tolerant-protection"></a>Fel tolerans skydd

När FileX-feltolerant modul startar söker den först efter en befintlig feltolerant loggfil på mediet. Om det inte går att hitta en giltig loggfil anser FileX att mediet inte är skyddat. I det här fallet kommer FileX att skapa en feltolerant logg fil på mediet.

> [!IMPORTANT]
> * FileX kan inte skydda ett fil system om det var skadat innan den FileX feltoleranta modulen startar. *

Om det finns en feltolerant logg fil söker FileX efter befintliga logg poster. En loggfil utan loggpost indikerar att en tidigare fil har genomförts och alla logg poster togs bort. I det här fallet kan programmet börja använda fil systemet med feltolerant skydd.

Men om det finns logg poster måste FileX antingen slutföra den tidigare fil åtgärden eller återställa ändringarna som redan har tillämpats på fil systemet, ångra ändringarna. I båda fallen återställs fil systemet till ett enhetligt tillstånd efter att logg posterna har tillämpats på fil systemet och programmet kan börja använda fil systemet igen.

För mediet som skyddas av FileX, under fil uppdaterings åtgärden, skrivs data delen direkt till mediet. När FileX skriver data registreras även alla ändringar som krävs för att tillämpas på katalog poster, FAT-tabell. Den här informationen registreras i de File-toleranta logg posterna. Den här metoden garanterar att uppdateringar av fil systemet sker efter att data har skrivits till mediet. Om mediet matas ut under data skrivnings fasen har viktig fil system information ännu inte ändrats. Därför påverkas inte fil systemet av avbrottet.

När alla data har skrivits till mediet kan FileX följa informationen i logg posterna för att tillämpa ändringarna i system information, en post i taget. När all system information har allokerats till mediet tas logg posterna bort från fel tolerans loggen. Vid det här tillfället Slutför FileX fil uppdaterings åtgärden.

Filer uppdateras inte på plats under fil uppdaterings åtgärden. Feltolerant modul allokerar en sektor för data att skriva nya data till och sedan ta bort sektorn som innehåller de data som ska skrivas över, uppdatera tillhör ande fett poster för att länka den nya sektorn till Chian. För situationer där partiella data i ett kluster behöver ändras, tilldelar FileX alltid nya kluster, skriver hela data från de gamla klustren med uppdaterade data till de nya klustren och frigör sedan de gamla klustren. Detta garanterar att den ursprungliga filen är intakt om fil uppdateringen avbryts. Programmet måste vara medveten om att det under FileX feltoleranta skyddet kräver att mediet har tillräckligt med ledigt utrymme för att rymma nya data innan sektorer med gamla data kan släppas. Om mediet inte har tillräckligt med utrymme för att lagra nya data, Miss lyckas uppdaterings åtgärden.
