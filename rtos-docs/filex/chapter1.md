---
title: Kapitel 1 – Introduktion till Azure återställnings tider FileX
description: Azure återställnings tider-FileX är ett komplett FAT-format för medie-och fil hanterings system för djupt inbäddade program.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be7e6f9cd9fbc69ac0908d1de733dac1c4f73bf6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825518"
---
# <a name="chapter-1---introduction-to-azure-rtos-filex"></a>Kapitel 1 – Introduktion till Azure återställnings tider FileX

Azure återställnings tider-FileX är ett komplett FAT-format för medie-och fil hanterings system för djupt inbäddade program. I det här kapitlet introduceras FileX som beskriver dess program och fördelar.

## <a name="filex-unique-features"></a>FileX-unika funktioner

Azure återställnings tider FileX har stöd för ett obegränsat antal medie enheter samtidigt, inklusive RAM-diskar, FLASH-hanterare och faktiska fysiska enheter. Den har stöd för 12-, 16-och 32-bitars FAT-format (File Allocation Table) och har även stöd för Extended File Allocation Table (exFAT), kontinuerlig filallokering och är mycket optimerad för både storlek och prestanda. FileX innehåller även feltolerant support, medie öppning/stängning och fil skrivnings funktioner.

FileX har utformats för att möta växande behov av FLASH-enheter och använder samma design-och kodnings metoder som ThreadX. Precis som alla Microsoft-produkter distribueras FileX med fullständig ANSI C-källkod och har ingen körnings tid för royalty.

### <a name="product-highlights"></a>Produkt höjd punkter

- Slutför support för ThreadX-processor
- Ingen royalties
- Fullständig ANSI C-källkod
- Real tids prestanda
- Teknisk support som svarar
- Obegränsade FileX-objekt (Media, kataloger och filer)
- Dynamiskt skapande/borttagning av FileX-objekt
- Flexibel minnes användning
- Storlek skalas automatiskt
- Liten storlek (till och med 6 KB) i instruktions områden: 6 – 30 000
- Slutför integrering med ThreadX
- Endian-neutral
- Lättanvänd FileX I/O-drivrutiner
- 12-, 16-och 32-bitars stöd för FAT
- exFAT-stöd
- Stöd för långa fil namn
- Intern FAT-post-cache
- Stöd för Unicode-namn
- Kontinuerlig filallokering
- Löpande sektor och kluster läsning/skrivning
- Intern logisk sektor cache
- Demonstrationen av RAM-disken körs direkt
- Funktion för medie format
- Fel identifiering och återställning
- Fel tolerans alternativ
- Inbyggd prestanda statistik
- Fristående support (inga Azure-återställnings tider)

## <a name="safety-certifications"></a>Säkerhets certifieringar

### <a name="tv-certification"></a>TÜV-certifiering

FileX har certifierats av SGS-TÜV Saar för användning i säkerhets kritiska system enligt IEC-61508 och IEC-62304. Certifieringen bekräftar att FileX kan användas i utvecklingen av säkerhetsrelaterad program vara för den högsta säkerhets integritets nivån för International Electrotechnical Commission (IEC) 61508 och IEC 62304, för "den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade system." SGS – TÜV Saar, som bildas genom ett gemensamt venture i Tyskland SGS-Group och TÜV Saarland, har blivit det ledande ackrediterade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad program vara för säkerhetsrelaterade system i hela världen. Den industriella säkerhets standarden IEC 61508 och alla standarder som är härledda från IT, inklusive IEC 62304, används för att säkerställa den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, process kontroll system, industriella maskiner och järnvägs kontroll system.

SGS – TÜV Saar har certifierat FileX som ska användas i säkerhetskritiska bil system, enligt ISO 26262-standarden. Dessutom är FileX certifierat för att ASIL () D, som motsvarar den högsta nivån av ISO 26262-certifiering.

Dessutom har SGS-TÜV Saar certifierat FileX som ska användas i verksamhets kritiska järnvägs program, vilket motsvarar en 50128-standard upp till SW-SIL 4.

![SGS TUV Saar-logotyp](./media/user-guide/sgs-tuv-saar-logo.png)

- IEC 61508 upp till SIL 4
- IEC 62304 upp till SW säkerhets klass C
- ISO 26262 ASIL D
- EN 50128 SW-SIL 4

> [!IMPORTANT]
> Kontakta oss om du vill ha mer information om vilka versioner av FileX som har certifierats av TÜV eller om du vill ha till gång till test rapporter, certifikat och tillhör ande dokumentation. *

### <a name="ul-certification"></a>UL-certifiering

FileX har certifierats av UL för efterlevnad med UL 60730-1 bilaga H, CSA E60730-1 bilaga H, IEC 60730-1 bilaga H, UL 60335-1 Bilaga R, IEC 603351 bilaga R och UL 1998 säkerhets standarder för program vara i programmerbara komponenter. Tillsammans med IEC/UL 60730-1, som har krav för "kontroller som använder program vara" i bilaga H, innehåller IEC 60335-1-standarden kraven för "programmerbara elektroniska kretsar" i bilaga R. IEC 60730 bilaga H och IEC 60335-1 Bilaga R MCU av maskin vara och program vara som används i anordningar som tvätt maskiner, disk maskiner, Dryers, kyl skåp, frysar och ugnar.

![C RU, USA 2](./media/user-guide/c-ru-us-logo.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]
>*Kontakta oss om du vill ha mer information om vilka versioner av FileX som har certifierats av UL eller för att få till gång till test rapporter, certifikat och tillhör ande dokumentation.*

## <a name="powerful-services-of-filex"></a>Kraftfulla tjänster av FileX

### <a name="multiple-media-management"></a>Hantering av flera Media

FileX kan stödja ett obegränsat antal fysiska media. Varje medie instans har sitt eget distinkta minnes området och tillhör ande driv rutin som anges i ***fx_media_open*** -anropet. Standard distributionen av FileX levereras med en enkel RAM medie driv rutin och ett demonstrations system som använder den här RAM-disken.

### <a name="logical-sector-cache"></a>Logisk sektor cache

Genom att minska antalet hela sektor överföringar, både till och från mediet, ökar FileX i logisk sektor avsevärt prestandan. FileX underhåller en logisk sektors-cache för varje öppnat medium. Djupet för den logiska sektorns cache bestäms av mängden minne som anges för FileX med API-anropet ***fx_media_open*** .

### <a name="contiguous-file-support"></a>Stöd för sammanhängande filer

FileX erbjuder sammanhängande fil stöd via API-tjänsten ***fx_file_allocate*** för att förbättra och göra tids fördröjnings tiden deterministisk. Den här rutinen tar den mängd minne som begärs och söker efter en serie intilliggande kluster för att uppfylla begäran. Om sådana kluster hittas fördelas de i förväg genom att göra dem till en del av filens kedja av allokerade kluster. Vid flytt av fysiska media ger FileX sammanhängande fil stöd resultat i en betydande prestanda förbättring och ger åtkomst tiden deterministisk.

### <a name="dynamic-creation"></a>Dynamisk generering

Med FileX kan du skapa system resurser dynamiskt. Detta är särskilt viktigt om ditt program har flera eller dynamiska konfigurations krav. Dessutom finns det inga förinställda gränser för antalet FileX-resurser som du kan använda (Media eller filer). Dessutom påverkar antalet system objekt inte prestanda.

## <a name="easy-to-use-api"></a>Lätt att använda API

FileX tillhandahåller den mycket bästa inbäddade fil system tekniken på ett sätt som är lätt att förstå och lätt att använda! FileX Application Programming Interface (API) gör tjänsterna intuitiva och konsekventa. Du behöver inte dechiffrera "alfabets soppor"-tjänster som är för vanliga med andra fil system.

En fullständig lista över FileX-tjänsterna i version 5 finns i [bilaga a](appendix-a.md).

## <a name="exfat-support"></a>exFAT-stöd

exFAT (Extended File Allocation Table) är ett fil system som har utvecklats av Microsoft för att tillåta fil storlek att överskrida 2 GB, en gräns som har införts av fil systemen FAT32. Det är standard fil systemet för SD-kort med kapacitet över 32 GB. SD-kort eller Flash-enheter som är formaterade med FileX exFAT-formatet är kompatibla med Windows. exFAT stöder fil storleken upp till en exabyte (EB), vilket är ungefär 1 000 000 000 GB.

Användare som vill använda exFAT måste kompilera om FileX-biblioteket med symbolen ***FX_ENABLE_EXFAT** _ definierad. När du öppnar mediet identifierar FileX medie typen. Om mediet är formaterat med exFAT läser FileX och skriver fil systemet efter exFAT-standarden. Om du vill formatera nya medier med exFAT använder du tjänsten _ *_fx_media_exFAT_format_* *. Som standard är exFAT inte aktiverat.

## <a name="fault-tolerant-support"></a>Feltolerant support

FileX feltolerant modul är utformad för att förhindra skada av fil system som orsakas av avbrott under fil-eller katalog uppdateringen. Om du till exempel lägger till data i en fil måste FileX uppdatera innehållet i filen, katalog posten och eventuellt FAT-poster. Om den här uppdaterings ordningen avbryts (till exempel ett strömavbrott eller om mediet matas ut i mitten av uppdateringen) är fil systemet i ett inkonsekvent tillstånd, vilket kan påverka hela fil systemets integritet, vilket leder till att andra filer skadas.

FileX-feltolerant modul fungerar genom att du registrerar alla steg som krävs för att uppdatera en fil eller en katalog på vägen. Den här logg posten lagras på mediet i dedikerade sektorer (block) som FileX kan hitta och komma åt. Platsen för loggdata kan nås även utan rätt fil system. Därför kan FileX fortfarande hitta logg posten och återställa fil systemet till ett korrekt tillstånd om fil systemet är skadat.

När FileX uppdaterar fil eller katalog skapas logg poster. När uppdateringen har slutförts tas logg posterna bort. Om logg posterna inte togs bort ordentligt efter en lyckad fil uppdatering, måste ingenting göras om återställnings processen avgör att innehållet i logg posten matchar fil systemet, och logg posterna kan rensas.

Om fil Systems uppdateringen har avbrutits nästa gången mediet monteras av FileX, analyserar feltolerant modul logg posterna. Informationen i logg posterna gör det möjligt för FileX att säkerhetskopiera del ändringar som redan har tillämpats på fil systemet (om felen inträffar under det tidiga steget av fil uppdaterings åtgärden), eller om logg posterna innehåller information om att göra det, kan FileX tillämpa de ändringar som krävs för att slutföra den tidigare åtgärden.

Den här feltoleranta funktionen är tillgänglig för alla FAT-filsystem som stöds av FileX, inklusive FAT12, FAT16, FAT32 och exFAT. Som standard är fel tolerans inte aktive rad i FileX. Om du vill aktivera fel tolerans funktionen måste FileX skapas med symbolen  **FX_ENABLE_FAULT_TOLERANT** och **FX_FAULT_TOLERANT** definieras. Vid körning startar programmet feltolerant tjänst genom att anropa **_fx_fault_tolerant_enable_**.
När tjänsten har startats går alla Skriv åtgärder för fil-och katalog tjänsten till fel tolerans-modulen.

As feltolerant tjänst startar identifierar den först om mediet skyddas av fel tolerans-modulen. Om så inte är fallet antar FileX integriteten för fil systemet och startar skyddet genom att allokera lediga block från fil systemet som ska användas för loggning och cachelagring. Om de feltoleranta modulerna loggar finns i fil systemet, analyseras logg posterna. FileX återställer den tidigare åtgärden eller utför den tidigare åtgärden, beroende på innehållet i logg posterna. Fil systemet blir tillgängligt efter att alla tidigare logg poster har bearbetats. Detta säkerställer att FIleX startar från ett känt fungerande tillstånd.

När ett medium skyddas i FileX-feltolerant modul kommer mediet inte att uppdateras med ett annat fil system. Detta skulle lämna logg posterna i fil systemet inkonsekventa med innehållet i FAT-tabellen, katalog posten. Om mediet uppdateras av ett annat fil system innan det flyttas tillbaka till FileX med feltolerant modul, blir resultatet odefinierat.

## <a name="callback-functions"></a>Återanrops funktioner

Följande tre callback-funktioner läggs till i FileX:

- Media-öppna motanrop
- Media-Stäng motringning
- Skriv motringning för fil

Efter registreringen kommer dessa funktioner att meddela programmet när sådana händelser inträffar.

## <a name="easy-integration"></a>Enkel integrering

FileX är enkelt att integrera med i princip vilken FLASH-eller media enhet som helst. Porting-FileX är enkelt. I den här hand boken beskrivs processen i detalj, och RAM-drivrutinen för demo systemet gör det en mycket bra plats att starta!
