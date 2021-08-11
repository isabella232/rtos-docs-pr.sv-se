---
title: Kapitel 1 – Introduktion till Azure RTOS FileX
description: Azure RTOS FileX är ett komplett FAT-format och filhanteringssystem för djupt inbäddade program.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 48fab21d78ede88e84db11a4f30574ce2061d145820b819ec7846203e297f42a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782974"
---
# <a name="chapter-1---introduction-to-azure-rtos-filex"></a>Kapitel 1 – Introduktion till Azure RTOS FileX

Azure RTOS FileX är ett komplett FAT-format och filhanteringssystem för djupt inbäddade program. I det här kapitlet introduceras FileX som beskriver dess program och fördelar.

## <a name="filex-unique-features"></a>Unika funktioner i FileX

Azure RTOS FileX har stöd för ett obegränsat antal medieenheter på samma gång, inklusive RAM-diskar, FLASH-hanterare och faktiska fysiska enheter. Den stöder 12-, 16- och 32-bitars FAT-format (File Allocation Table) och har även stöd för Extended File Allocation Table (exFAT), sammanhängande filallokering och är mycket optimerad för både storlek och prestanda. FileX innehåller även feltolerant stöd, funktioner för att öppna/stänga media och återanrop av filskrivning.

FileX har utformats för att uppfylla det växande behovet av FLASH-enheter och använder samma design- och kodningsmetoder som ThreadX. Precis som med alla Microsoft-produkter distribueras FileX med fullständig ANSI C-källkod och har inga körningstillägg.

### <a name="product-highlights"></a>Produkthöjdpunkter

- Fullständigt stöd för ThreadX-processor
- Inga sporrar
- Slutför ANSI C-källkoden
- Prestanda i realtid
- Dynamisk teknisk support
- Obegränsade FileX-objekt (media, kataloger och filer)
- Skapa/ta bort dynamiskt FileX-objekt
- Flexibel minnesanvändning
- Storleken skalas automatiskt
- Litet fotavtryck (så lågt som 6 KByte) instruktionsområdesstorlek: 6–30 000
- Fullständig integrering med ThreadX
- Endiansk neutral
- Lätt att implementera FileX I/O-drivrutiner
- Stöd för 12-, 16- och 32-bitars FAT
- exFAT-stöd
- Stöd för långa filnamn
- Intern FAT-postcache
- Stöd för Unicode-namn
- Kontinuerlig filallokering
- Efterföljande sektor- och klusterläsning/-skrivning
- Intern cache för logisk sektor
- Demonstrationen av RAM-disken tar slut
- Funktioner för medieformat
- Felidentifiering och återställning
- Feltoleranta alternativ
- Inbyggd prestandastatistik
- Fristående stöd (Azure RTOS)

## <a name="safety-certifications"></a>Säkerhetscertifieringar

### <a name="tv-certification"></a>TÜV-certifiering

FileX har certifierats av SGS-TÜV Saar för användning i säkerhetskritiska system enligt IEC-61508 och IEC-62304. Certifieringen bekräftar att FileX kan användas i utvecklingen av säkerhetsrelaterad programvara för högsta säkerhetsintegritetsnivåer för International Electrotechnical Commission (IEC) 61508 och IEC 62304, för "funktionell säkerhet för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade system". SGS-TÜV Saar, som bildas tillsammans med Tysklands SGS-Group och TÜV Saarland, har blivit det ledande auktoriserade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad programvara för säkerhetsrelaterade system över hela världen. Den industriella säkerhetsstandarden IEC 61508 och alla standarder som härleds från den, inklusive IEC 62304, används för att garantera funktionell säkerhet för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, processkontrollsystem, industriella maskiner och system för kontroll av djur.

SGS-TÜV Saar har certifierat FileX som ska användas i säkerhetskritiska fordonssystem enligt ISO 26262-standarden. Dessutom är FileX certifierat till Bilsäkerhetsintegritetsnivå (ASIL) D, som representerar den högsta nivån av ISO 26262-certifiering.

SGS-TÜV Saar har dessutom certifierat FileX som ska användas i säkerhetskritiska program som uppfyller STANDARDEN EN 50128 upp till SW-SIL 4.

![SGS TUV Saar-logotyp](./media/user-guide/sgs-tuv-saar-logo.png)

- IEC 61508 upp till SIL 4
- IEC 62304 upp till SW-säkerhetsklass C
- ISO 26262 ASIL D
- EN 50128 SW-SIL 4

> [!IMPORTANT]
> Kontakta oss för mer information om vilka versioner av FileX som har certifierats av TÜV eller för tillgängligheten av testrapporter, certifikat och tillhörande dokumentation.*

### <a name="ul-certification"></a>UL-certifiering

FileX har certifierats av UL för kompatibilitet med UL 60730-1Uppdateringar H, CSA E60730-1 Både H, IEC 60730-1 Ul 60335-1× R, IEC 603351 Samt UL 1998-säkerhetsstandarder för programvara i programmerbara komponenter. Tillsammans med IEC/UL 60730-1, som har krav för "Kontroller med hjälp av programvara" i sin Klass H beskriver IEC 60335-1-standarden kraven för "Programmerbara elektroniska kretsar" i sin iEC 60730 60330 60335-1 Gällande säkerheten för MCU-maskinvara och programvara som används i maskiner som t.ex. maskiner, reglage, torktumlare, kylskåp, frysar och installationer.

![C RU US 2](./media/user-guide/c-ru-us-logo.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]
>*Kontakta oss för mer information om vilka versioner av FileX som har certifierats av UL eller för tillgängligheten av testrapporter, certifikat och tillhörande dokumentation.*

## <a name="powerful-services-of-filex"></a>Kraftfulla tjänster i FileX

### <a name="multiple-media-management"></a>Hantering av flera media

FileX har stöd för ett obegränsat antal fysiska media. Varje medieinstans har ett eget distinkt minnesområde  och en associerad drivrutin som anges fx_media_open anropet. Standarddistributionen av FileX levereras med en enkel RAM-mediedrivrutin och ett demonstrationssystem som använder den här RAM-disken.

### <a name="logical-sector-cache"></a>Cache för logisk sektor

Genom att minska antalet överföringar av hela sektorer, både till och från mediet, förbättrar FileX-cachen för logisk sektor prestanda avsevärt. FileX har en logisk sektorcache för varje öppnat medium. Djupet i den logiska sektorcachen bestäms av mängden minne  som tillhandahålls till FileX med fx_media_open API-anropet.

### <a name="contiguous-file-support"></a>Stöd för sammanhängande filer

FileX erbjuder sammanhängande filstöd via API-tjänsten för ***fx_file_allocate*** att förbättra och göra filåtkomsttiden deterministisk. Den här rutinen tar den mängd minne som begärs och söker efter en serie intilliggande kluster för att uppfylla begäran. Om sådana kluster hittas är de för allokerade genom att göra dem till en del av filens kedja med allokerade kluster. Vid flytt av fysiska media ger fileX-sammanhängande filstöd en betydande prestandaförbättring och gör åtkomsttiden deterministisk.

### <a name="dynamic-creation"></a>Dynamiskt skapande

Med FileX kan du skapa systemresurser dynamiskt. Detta är särskilt viktigt om programmet har flera eller dynamiska konfigurationskrav. Dessutom finns det inga förinställda gränser för antalet FileX-resurser som du kan använda (media eller filer). Dessutom påverkar inte antalet systemobjekt prestandan.

## <a name="easy-to-use-api"></a>Lätt att använda API

FileX ger den allra bästa djupt inbäddade filsystemtekniken på ett sätt som är lätt att förstå och lätt att använda! FileX Application Programming Interface (API) gör tjänsterna intuitiva och konsekventa. Du behöver inte dechiffrera "alfabetiska alfabetiska" tjänster som är för vanliga med andra filsystem.

En fullständig lista över FileX Version 5-tjänster finns i [bilaga A.](appendix-a.md)

## <a name="exfat-support"></a>exFAT-stöd

exFAT (utökad filallokeringstabell) är ett filsystem som utformats av Microsoft för att tillåta att filstorleken överstiger 2 GB, en gräns som tillämpas av FAT32-filsystem. Det är standardfilsystemet för SD-kort med kapacitet över 32 GB. SD-kort eller flash-enheter formaterade med FileX exFAT-format är kompatibla med Windows. exFAT stöder filstorlek upp till en Exabyte (EB), vilket är cirka en miljard GB.

Användare som vill använda exFAT måste kompilera om FileX-biblioteket med symbolen ***FX_ENABLE_EXFAT** _ definierad. När du öppnar ett medium identifierar FileX medietypen. Om mediet är formaterat med exFAT läser och skriver FileX filsystemet enligt exFAT-standarden. Om du vill formatera nya medier med exFAT använder du tjänsten _*_fx_media_exFAT_format_**. ExFAT är inte aktiverat som standard.

## <a name="fault-tolerant-support"></a>Stöd för feltolerant

FileX-feltolerant modul är utformad för att förhindra att filsystemet skadas på grund av avbrott under fil- eller kataloguppdateringen. När du till exempel ska lägga till data i en fil måste FileX uppdatera innehållet i filen, katalogposten och eventuellt FAT-posterna. Om den här uppdateringssekvensen avbryts (till exempel strömavbrott eller om mediet matas in mitt i uppdateringen) är filsystemet i ett inkonsekvent tillstånd, vilket kan påverka hela filsystemets integritet, vilket leder till att andra filer skadas.

FileX-feltolerant modul fungerar genom att registrera alla steg som krävs för att uppdatera en fil eller en katalog längs vägen. Den här loggposten lagras på media i dedikerade sektorer (block) som FileX kan hitta och komma åt. Platsen för loggdata kan nås även utan ett korrekt filsystem. Om filsystemet är skadat kan FileX därför fortfarande hitta loggposten och återställa filsystemet till ett bra tillstånd.

När FileX uppdaterar fil eller katalog skapas loggposter. När uppdateringsåtgärden har slutförts tas loggposterna bort. Om loggposterna inte har tagits bort korrekt efter en lyckad filuppdatering, om återställningsprocessen avgör att innehållet i loggposten matchar filsystemet, behöver inget göras och loggposterna kan rensas.

Om filsystemets uppdateringsåtgärd avbröts analyserar den feltoleranta modulen loggposterna nästa gång mediet monteras av FileX. Informationen i loggposterna gör att FileX kan backa ut partiella ändringar som redan har tillämpats på filsystemet (om felet inträffar i det tidiga skedet av filuppdateringsåtgärden), eller om loggposterna innehåller information om omåtgärd, kan FileX tillämpa de ändringar som krävs för att slutföra den tidigare åtgärden.

Den här feltoleranta funktionen är tillgänglig för alla FAT-filsystem som stöds av FileX, inklusive FAT12, FAT16, FAT32 och exFAT. Feltoleranta är som standard inte aktiverat i FileX. För att aktivera den feltoleranta funktionen måste FileX byggas med symbolen  **FX_ENABLE_FAULT_TOLERANT** och **FX_FAULT_TOLERANT** definieras. Vid körning startar programmet en feltolerant tjänst genom att anropa **_fx_fault_tolerant_enable_**.
När tjänsten startar går alla skrivåtgärder för filer och kataloger igenom den feltoleranta modulen.

När en feltolerant tjänst startar identifierar den först om mediet är skyddat under den feltoleranta modulen. Om det inte är det antar FileX filsystemets integritet och börjar skydda genom att allokera lediga block från filsystemet som ska användas för loggning och cachelagring. Om loggarna för feltoleranta moduler hittas i filsystemet analyseras loggposterna. FileX återställer den tidigare åtgärden eller gör om den tidigare åtgärden, beroende på innehållet i loggposterna. Filsystemet blir tillgängligt när alla tidigare loggposter har bearbetats. Detta säkerställer att FIleX startar från ett känt bra tillstånd.

När ett medium har skyddats under FileX Fault Tolerant Module uppdateras inte mediet med något annat filsystem. Då blir loggposterna i filsystemet inkonsekventa med innehållet i FAT-tabellen, katalogposten. Om mediet uppdateras av ett annat filsystem innan det flyttas tillbaka till FileX med den feltoleranta modulen är resultatet odefinierat.

## <a name="callback-functions"></a>Återanropsfunktioner

Följande tre återanropsfunktioner läggs till i FileX:

- Media Open-återanrop
- Media Close-återanrop
- Återanrop av filskrivning

När de har registrerats meddelar dessa funktioner programmet när sådana händelser inträffar.

## <a name="easy-integration"></a>Enkel integrering

FileX är enkelt att integrera med praktiskt taget vilken FLASH- eller medieenhet som helst. Det är enkelt att porta FileX. Den här guiden beskriver processen i detalj och DEMO-systemets RAM-drivrutin är ett mycket bra ställe att börja på!
