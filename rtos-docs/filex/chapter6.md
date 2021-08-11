---
title: Kapitel 6 – Azure RTOS FileX-feltolerant modul
description: Det här kapitlet innehåller en beskrivning av Azure RTOS FileX Fault Tolerant Module som är utformad för att upprätthålla filsystemets integritet om mediet förlorar ström eller matas ut mitt i en filskrivningsåtgärd.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 66bffa2dbf52bc458bfaf124aa006a79e810100ac2e926c17444daf090519e66
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783793"
---
# <a name="chapter-6---azure-rtos-filex-fault-tolerant-module"></a>Kapitel 6 – Azure RTOS FileX-feltolerant modul

Det här kapitlet innehåller en beskrivning av Azure RTOS FileX Fault Tolerant Module som är utformad för att upprätthålla filsystemets integritet om mediet förlorar ström eller matas ut mitt i en filskrivningsåtgärd.

## <a name="filex-fault-tolerant-module-overview"></a>Översikt över FileX-feltolerant modul

När ett program skriver data till en fil uppdaterar FileX både datakluster och systeminformation. Dessa uppdateringar måste slutföras som en atomisk åtgärd för att hålla informationen i filsystemet sammanhängande. När du till exempel ska lägga till data i en fil måste FileX hitta ett tillgängligt kluster på mediet, uppdatera FAT-kedjan, uppdatera längden som finns i katalogposten och eventuellt uppdatera startklustret i katalogposten. Antingen kan ett strömavbrott eller mediautmatning avbryta uppdateringssekvensen, vilket gör att filsystemet är i ett inkonsekvent tillstånd. Om det inkonsekventa tillståndet inte korrigeras kan data som uppdateras gå förlorade, och på grund av skador på systeminformationen kan efterföljande filsystemsoperationer skada andra filer eller kataloger på mediet.

FileX-feltolerant modul fungerar genom att journalföra de steg som krävs *för att* uppdatera en fil innan de här stegen tillämpas på filsystemet. Om filuppdateringen lyckas tas loggposterna bort. Men om filuppdateringen avbryts lagras loggposterna på mediet. Nästa gång mediet monteras identifierar FileX dessa loggposter från den tidigare (oavslutade) skrivåtgärden. I sådana fall kan FileX återställas från ett fel genom att antingen återställa de ändringar som redan har gjorts i filsystemet eller genom att tillämpa de ändringar som krävs för att slutföra den föregående åtgärden igen. På så sätt upprätthåller FileX-feltolerant modul filsystemets integritet om mediet förlorar ström under en uppdateringsåtgärd.

> [!IMPORTANT]
> *FileX Fault Tolerant Module är inte utformad för att förhindra att filsystemet skadas på grund av att fysiska media skadas med giltiga data i den.*

> [!IMPORTANT]
> *När FileX Fault Tolerant-modulen skyddar ett medium får mediet inte monteras av något annat än FileX med Feltolerant aktiverat. Om du gör det kan loggposterna i filsystemet vara inkonsekventa med systeminformationen på mediet. Om FileX Fault Tolerant-modulen försöker bearbeta loggposter efter att mediet har uppdaterats av ett annat filsystem kan återställningsproceduren misslyckas, vilket gör att hela filsystemet är i ett oförutsägbart tillstånd.*

## <a name="use-of-the-fault-tolerant-module"></a>Användning av feltolerant modul

Funktionen Feltolerant FileX är tillgänglig för alla FAT-filsystem som stöds av FileX, inklusive FAT12, FAT16, FAT32 och exFAT. För att aktivera den feltoleranta funktionen måste FileX byggas med symbolen **FX_ENABLE_FAULT_TOLERANT** definieras. Vid körning startar programmet en feltolerant tjänst genom **_att anropa fx_fault_tolerant_enable_ _ omedelbart efter *anropet till _*_fx_media_open_**. När feltolerant har aktiverats skyddas alla filskrivningsåtgärder till det avsedda mediet. Som standard är den feltoleranta modulen inte aktiverad.

> [!IMPORTANT]
> *Programmet måste se till att filsystemet inte används innan ***** fx_fault_tolerant_enable _ anropas. Om programmet skriver data till filsystemet innan feltolerant aktivera, kan skrivåtgärden skada mediet om tidigare skrivåtgärder inte slutfördes och filsystemet inte återställdes med hjälp av feltolerant logg entries._

## <a name="filex-fault-tolerant-module-log"></a>FileX-feltolerant modullogg

Den feltoleranta FileX-loggen tar upp ett logiskt kluster i flash. Indexet för klustrets startkluster registreras i startsektorn för mediet, med en förskjutning som anges av symbolen **FX_FAULT_TOLERANT_BOOT_INDEX**. Som standard definieras den här symbolen som 116. Den här platsen väljs eftersom den är markerad som reserverad i FAT12/ 16/32 och exFAT-specifikation.

Bild 5, "Log Structure Layout", visar loggstrukturens allmänna layout. Loggstrukturen innehåller tre avsnitt: Loggrubrik, FAT-kedja och loggposter.

> [!IMPORTANT]
> *Alla värden för flera byte som lagras i loggposterna är i Little Endian-format.*

![Loggstrukturlayout](./media/user-guide/log-structure-layout.png)

**Bild 5. Layout för loggstruktur**

Området Loggrubrik innehåller information som beskriver hela loggstrukturen och förklarar varje fält i detalj.

**TABELL 8. Logghuvudområde**

|Fält|Storlek (i byte)|Description|
|-----|--------------|-----------|
|ID|4|Identifierar en FileX-feltolerant loggstruktur. Loggstrukturen anses vara ogiltig om ID-värdet inte 0x46544C52.|
|Total storlek|2|Anger den totala storleken (i byte) för hela loggstrukturen.|
|Rubrikkontrollsumma|2|Kontrollsumma som konverterar loggrubrikområdet. Loggstrukturen anses vara ogiltig om huvudfälten misslyckas med verifieringen av kontrollsumman.|
|Versionsnummer|2|FileX-feltolerant huvudversion och lägre versionsnummer.|
|Reserverat|2|För framtida expansion.|

Området Loggrubrik följs av området FAT Chain Log (FAT-kedja). Bild 9 innehåller information som beskriver hur FAT-kedjan ska ändras. Det här loggområdet innehåller information om de kluster som allokeras till en fil, klustren som tas bort från en fil och var infogningen/borttagningen ska vara och beskriver varje fält i området för FAT-kedjans logg.

**TABELL 9. FAT-kedjans loggområde**

|Fält|Storlek (i byte)|Description|
|-----|--------------|-----------|
|FAT-kedja, loggkontrollsumma|2|Kontrollsumma för hela FAT-kedjans loggområde. OMRÅDET FAT Chain Log anses vara ogiltigt om verifieringen av kontrollsumman misslyckas.|
|Flagga|1|Giltiga flaggvärden är:<br/>0x01 FAT-kedja giltig<br />0x02 SOM ANVÄNDS|
|Reserverat|1|Reserverad för framtida användning|
|Infogningspunkt – Front|4|Klustret (som tillhör den ursprungliga FAT-kedjan) där den nyligen skapade kedjan ska kopplas till.|
|Huvudkluster i ny FAT-kedja|4|Det första klustret i den nyligen skapade FAT-kedjan|
|Huvudkluster från den ursprungliga FAT-kedjan|4|Det första klustret i den del av den ursprungliga FAT-kedjan som ska tas bort.|
|Infogningspunkt – bakåt|4|Det ursprungliga klustret där den nyligen skapade FAT-kedjan ansluts.|
|Nästa borttagningspunkt|4|Det här fältet hjälper rensningsproceduren för FAT-kedjan.|

Området Loggposter innehåller loggposter som beskriver de ändringar som krävs för att återställa efter ett fel. Det finns tre typer av loggpost som stöds i fileX-feltolerant modul: FAT-loggpost; Katalogloggpost; och Bitmapp-loggpost.

Följande tre figurer och tre tabeller beskriver dessa loggposter i detalj.

![FAT-loggpost](./media/user-guide/fat-log-entry.png)

**Bild 6. FAT-loggpost**

**TABELL 10. FAT-loggpost**

|Fält|Storlek (i byte)|Beskrivning|
|-----|--------------|-----------|
Typ|2|Typ av post måste vara FX_FAULT_TOLERANT_FAT_LOG_TYPE|
|Storlek|2|Storleken på den här posten|
|Klusternummer|4|Klusternummer|
|Värde|4|Värde som ska skrivas till FAT-posten|

![Katalogloggpost](./media/user-guide/directory-log-entry.png)

**Bild 7. Katalogloggpost**

**TABELL 11. Katalogloggpost**

|Fält|Storlek (i byte)|Beskrivning|
|-----|--------------|-----------|
|Typ|2|Typ av post måste vara FX_FAULT_TOLERANT_DIRECTORY_LOG_TYPE|
|Storlek|2|Storleken på den här posten|
|Sektorförskjutning|4|Förskjutning (i byte) i den sektor där den här katalogen finns.|
|Loggsektor|4|Den sektor där katalogposten finns|
|Loggdata|Variabel|Katalogpostens innehåll|

![Loggpost för Bitmapp](./media/user-guide/bitmap-log-entry.png)

**Bild 8. Loggpost för Bitmapp**

**TABELL 12. Loggpost för Bitmapp**

|Fält|Storlek (i byte)|Beskrivning|
|-----|--------------|-----------|
|Typ|2|Typ av post måste vara FX_FAULT_TOLERANT_BITMAP_LOG_TYPE|
|Storlek|2|Storleken på den här posten|
|Klusternummer|4|Klusternummer|
|Värde|4|Värde som ska skrivas till FAT-posten|

## <a name="fault-tolerant-protection"></a>Feltolerant skydd

När FileX-feltolerant modul startar söker den först efter en befintlig feltolerant loggfil på mediet. Om det inte går att hitta en giltig loggfil betraktar FileX mediet som oskyddat. I det här fallet skapar FileX en feltolerant loggfil på mediet.

> [!IMPORTANT]
> *FileX kan inte skydda ett filsystem om det var skadat innan FileX-feltolerant modul startar. *

Om en feltolerant loggfil finns söker FileX efter befintliga loggposter. En loggfil utan loggpost anger att den tidigare filåtgärden lyckades och att alla loggposter har tagits bort. I det här fallet kan programmet börja använda filsystemet med feltolerant skydd.

Men om loggposter finns måste FileX antingen slutföra den tidigare filåtgärden eller återställa ändringarna som redan tillämpats på filsystemet, vilket effektivt ångrar ändringarna. I båda fallen, när loggposterna har tillämpats på filsystemet, återställs filsystemet till ett sammanhängande tillstånd och programmet kan börja använda filsystemet igen.

För media som skyddas av FileX skrivs datadelen direkt till mediet under filuppdateringen. När FileX skriver data registrerar den även eventuella ändringar som måste tillämpas på katalogposter, FAT-tabell. Den här informationen registreras i filen toleranta loggposter. Den här metoden garanterar att uppdateringar av filsystemet sker när data har skrivits till mediet. Om mediet matas ut under dataskrivningsfasen har viktig filsysteminformation inte ändrats ännu. Därför påverkas inte filsystemet av avbrottet.

När alla data har skrivits till mediet följer FileX sedan information i loggposterna för att applicera ändringarna i systeminformationen, en post i taget. När all systeminformation har utförts på mediet tas loggposterna bort från den feltoleranta loggen. Nu slutför FileX filuppdateringsåtgärden.

Under filuppdateringen uppdateras inte filerna på plats. Den feltoleranta modulen allokerar en sektor som data ska skriva nya data till och tar sedan bort den sektor som innehåller de data som ska skrivas över och uppdaterar relaterade FAT-poster för att länka den nya sektorn till chian. I situationer där partiella data i ett kluster måste ändras allokerar FileX alltid nya kluster, skriver hela data från de gamla klustren med uppdaterade data till de nya klustren och frigör sedan de gamla klustren. Detta garanterar att den ursprungliga filen är intakt om filuppdateringen avbryts. Programmet måste vara medveten om att under Feltolerant FileX-skydd kräver uppdatering av data i en fil att mediet har tillräckligt med ledigt utrymme för att lagra nya data innan sektorer med gamla data kan släppas. Om mediet inte har tillräckligt med utrymme för att lagra nya data misslyckas uppdateringsåtgärden.
