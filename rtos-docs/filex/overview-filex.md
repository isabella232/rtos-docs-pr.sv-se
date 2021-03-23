---
title: Förstå Azure återställnings tider-FileX
description: Azure återställnings tider FileX är ett FAT-kompatibelt (File Allocation Table)-kompatibelt fil system som är fullständigt integrerat med Azure återställnings tider-ThreadX och är tillgängligt för alla processorer som stöds. Precis som med Azure återställnings tider-ThreadX är Azure återställnings tider FileX utformad för att ha ett litet utrymme och höga prestanda, vilket gör det perfekt för dagens djupt inbäddade program som kräver fil hanterings åtgärder. FileX stöder de flesta fysiska media, inklusive RAM-, Azure återställnings tider-USBX, SD-kort och NAND/eller Flash-minnen via Azure återställnings tider LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a3a20c8ced3426399ceedf6994c872ce7aec93c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827321"
---
# <a name="overview-of-azure-rtos-filex"></a>Översikt över Azure återställnings tider-FileX

Azure återställnings tider FileX Embedded File System är Azure återställnings TIDERs Advanced, lösning för industriella klasser för Microsoft FAT-filformat, särskilt utformad för djupt inbäddade, real tids-och IoT-program. Azure återställnings tider-FileX har stöd för alla Microsofts fil format, inklusive FAT12, FAT16, FAT32 och exFAT. FileX erbjuder också valfri fel tolerans och blixt slitage via en tilläggs produkt som kallas [Azure återställnings tider LevelX](https://docs.microsoft.com/azure/rtos/levelx/). Allt detta kombinerat med en liten storlek, snabb körning och överlägsen enkel användning, gör Azure återställnings tider FileX det idealiska valet för de mest krävande inbäddade IoT-programmen.

## <a name="api-protocols"></a>API-protokoll

### <a name="azure-rtos-filex-api"></a>Azure återställnings tider FileX-API

- Intuitiv och konsekvent API
- Substantiv-namn konvention för verb
- Alla API: er har ledande *fx_* för att enkelt identifiera som FileX
- Blockering av API: er har valfri tråd-timeout
- Valfria återanrop för användar meddelanden för medie-och fil åtgärder
- Mer information finns i [användar handboken för Azure återställnings tider FileX](about-this-guide.md) .

### <a name="media-services"></a>Media Services

- Stöd för FAT 12/16/32 och exFAT
- Minimalt 6KB FLASH, 2,5 KB RAM
- Slutför Media Access Services
- Obegränsat antal medie instanser
- Enkelt Läs/skriv-gränssnitt för logisk sektor driv rutin
- Stöd för flera partitioner
- Logisk sektor cache
- Cache för FAT-post
- Tillval fel tolerans support
- Uppskjuten sekundär FAT-uppdatering
- Spårning på system nivå via Azure återställnings tider TraceX
- Intuitiva API: er för medie åtkomst, inklusive:
  - fx_media_open
  - fx_media_close
  - fx_media_format
  - fx_media_space_available

### <a name="directory-services"></a>Katalog tjänster

- Upp till 256 byte-sökvägar
- Långa och 8,3 Katalog namn stöds
- Ta bort katalog skapa &
- Katalog navigering och-Traversal
- Hantering av katalogattribut
- Spårning på system nivå via Azure återställnings tider TraceX
- Intuitiva API: er för katalog åtkomst, inklusive:
  - fx_directory_create
  - fx_directory_delete
  - fx_directory_attributes_set
  - fx_directory_attributes_read
  - fx_directory_first_entry_find
  - fx_directory_next_entry_find

### <a name="file-services"></a>Filtjänster

- Minimalt 3,3 KB FLASH
- Obegränsade öppna filer
- Skrivskyddade filer kan öppnas flera gånger
- Långa och 8,3 Katalog namn stöds
- Stöd för sammanhängande filer
- Snabb söknings logik
- För tilldelning av kluster
- Skapa, ta bort och Byt namn på filen
- Läsa, skriva och se fil
- Hantering av filattribut
- Spårning på system nivå via Azure återställnings tider TraceX
- Intuitiva API: er för fil åtkomst, inklusive:
  - fx_file_create
  - fx_file_delete
  - fx_file_attributes_set
  - fx_file_attributes_read
  - fx_file_read
  - fx_file_seek
  - fx_file_write

## <a name="small-footprint"></a>Små

Azure återställnings tider FileX Embedded File System har ett remarkably litet minimalt utrymme på 8,6 KB till 12 KB för grundläggande läsning/skrivning av filer. Minimalt antal Azure återställnings tider FileX RAM-användning är i ordningen 1,8 KB för en Media instans och endast en 512-byte logisk sektor cache. Precis som Azure återställnings tider ThreadX skalas storleken på Azure återställnings tider-FileX automatiskt utifrån de tjänster som används av programmet. Detta eliminerar behovet av komplicerade konfigurations-och build-parametrar, vilket gör det lättare för utvecklaren att göra något.

## <a name="fast-execution"></a>Snabb körning

Azure återställnings tider FileX tillhandahåller en logisk sektor och cache för FAT-poster. Storlekarna för båda är direkt kontroll över programmet. Dessutom tillhandahåller Azure återställnings tider-FileX sammanhängande kluster tilldelning och direkt kluster läsning och skrivning i följd. Läs-och skriv förfrågningar för hela sektorer görs direkt mellan programbufferten och mediet, vilket innebär att ingen mellanlagring görs. Allt detta och en allmän prestanda orienterad design filosofi hjälper Azure återställnings tider FileX att uppnå snabbast möjliga prestanda.

## <a name="advanced-technology"></a>Avancerad teknik

Azure återställnings tider-FileX är avancerad teknik, inklusive följande.

- Stöd för FAT 12/16/32 och exFAT
- Stöd för flera partitioner
- Automatisk skalning
- Endian-neutral
- Långt fil namn och 8,3-stöd
- Tillval fel tolerans support
- Logisk sektor cache
- Cache för FAT-post
- För tilldelning av kluster
- Stöd för sammanhängande filer
- Valfria prestanda mått
- Azure återställnings tider TraceX system Analysis support

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a>ELLER/NAND slitage (Azure återställnings tider LevelX)

Azure återställnings tider-LevelX är Microsofts eller/NAND FLASH slitage-produkt. Azure återställnings tider LevelX kan användas tillsammans med FileX eller som ett fristående, direkt Läs-och skrivbart FLASH sektor bibliotek för programmet.

## <a name="fastest-time-to-market"></a>Snabbast tid till marknad

Azure återställnings tider FileX är enkelt att installera, lära sig, använda, felsöka, verifiera, certifiera och underhålla. Därför är Azure återställnings tider FileX ett av de mest populära FAT-filsystemen för inbäddade IoT-enheter. Följande är några av orsakerna till vår konsekventa tids-till-marknad-fördel:

- Kvalitets dokumentation – Läs vår [Användar handbok för Azure återställnings tider FileX](about-this-guide.md) och se själv!
- Fullständig käll kods tillgänglighet
- Lätt att använda API
- Omfattande och avancerad funktions uppsättning

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a>Förcertifierat av TUV och UL till många säkerhets standarder

![SGS – TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

Azure återställnings tider FileX har certifierats av SGS-TUV Saar för användning i säkerhets kritiska system, enligt IEC-61508 SIL 4, IEC-62304 SW säkerhets klass C, ISO 26262 ASIL D och EN 50128. Certifieringen bekräftar att FileX kan användas i utvecklingen av säkerhetsrelaterad program vara för högsta säkerhets integritets nivå för IEC-61508, IEC-62304, ISO 26262 och EN 50128 för "fungerande säkerhet för elektriska, elektroniska och programmerbara elektroniskt säkerhetsrelaterade system". SGS – TUV Saar, som bildas genom ett gemensamt venture i Tyskland SGS-Group och TUV Saarland, har blivit det ledande ackrediterade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad program vara för säkerhetsrelaterade system i hela världen. Den industriella säkerhets standarden IEC 61508, och alla standarder som är härledda från IT, inklusive IEC-62304, ISO 26262 och EN 50128, används för att säkerställa den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, process kontroll system, industriella maskiner, bilar och järnvägs styrnings system.

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="CRU UL-certifiering":::

Azure återställnings tider FileX har erkänts av UL för att följa UL 60730-1 bilaga H, CSA E60730-1 bilaga H, IEC 60730-1 bilaga H, UL 60335-1 Bilaga R, IEC 60335-1 Bilaga R och UL 1998 säkerhets standarder för program vara i programmerbara komponenter. UL är ett globalt, oberoende, säkerhets vetenskaps företag med mer än en Century av expertis som förnyar säkerhetslösningar, från det offentliga införandet av elektricitet till genombrott i hållbarhet, förnybar energi och Nanotechnology.

Artefakter (certifikat, säkerhets hand bok, test rapport osv.) som är associerade med TUV och UL-certifieringar är tillgängliga för försäljning.

I de fall där programmet behöver ytterligare certifiering, är en certifierings tjänst tillgänglig via Microsoft för att tillhandahålla certifierings certifiering till olika standarder med hjälp av den aktuella maskin varu plattformen och till och med program koden.

## <a name="one-simple-license"></a>En enkel licens

Det kostar inget att använda och testa käll koden och ingen kostnad för produktions licenser när de distribueras till förinstallerade enheter, men alla andra enheter behöver en enkel årlig licens.

## <a name="full-highest-quality-source-code"></a>Fullständig käll kod med högsta kvalitet

Under åren har FileX-källkod angett kvalitet och enkel förståelse. Dessutom tillhandahåller konventionen om en funktion per fil för enkel käll navigering.

## <a name="supports-most-popular-architectures"></a>Har stöd för de flesta populära arkitekturerna

Azure återställnings tider-FileX körs på de flesta populära 32/64-bitars mikroprocessorer, färdiga, fullständigt testade och fullt stödda, inklusive följande:

**Analoga enheter**: SHARC, Blackfin, CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: Apollo MCU

**Arm**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitars/R4/R5, TrustZone ARMv8-M

**Takt**: Xtensa, Diamond

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, WICED WiFi

**Cypress**: RISC-V

**Kiseldioxid**: ESI – RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel**; **Intel FPGA**: X36/Pentium, XSCALE, Nios II, Cyclone, Arria 10

**Mikrochip**: avr32, ARM7, ARM9, cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/sa, PIC24/PIC32

**Mikrohalv**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, coldfire, Kinetis cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, synergieffekt

**Silicon** Labb: EFM32

**Sammanfattning**: båge 600, 700, båge EM, båg HS

**St**: STM32, ARM7, ARM9, cortex-M3/M4/M7

**TL**: C5xxx, C6xxx, Stellaris, Sitara, tiva-C

**Wave-bearbetning**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class

**Xilinx**: mikroblixt, powerpc 405, ZYNQ, ZYNQ UltraSCALE

*Alla tids gränser och storleks värden i listan är uppskattningar och kan skilja sig åt på din utvecklings plattform.*
