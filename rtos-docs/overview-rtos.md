---
title: Vad är Microsoft Azure RTOS?
description: Azure RTOS är ett realtidsoperativsystemet (RTOS) för IoT- och Edge-enheter som drivs av mikrostyrenheter (MCU).
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: b099a5f18accfbe467a2a8fa680c0c76666a9ff3
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754921"
---
# <a name="what-is-microsoft-azure-rtos"></a>Vad är Microsoft Azure RTOS?

Azure RTOS är ett realtidsoperativsystemet (RTOS) för Sakernas Internet (IoT) och gränsenheter som drivs av mikrostyrenheter (MCU). Azure RTOS har utformats för att stödja de mest begränsade enheterna (batteridrivna och har mindre än 64 KB flashminne).

Azure RTOS är förcertifierat för en mängd olika säkerhetsstandarder. Dessa omfattar certifieringarna IEC 61508 SIL 4, IEC 62304 Class C och ISO 26262 ASIL D. Azure RTOS ThreadX är också DO-178-certifierat.

Azure RTOS en EAL4+ Common Criteria-certifierad miljö, inklusive fullständig SÄKERHET på IP-nivå via IPsec och socket layer security via TLS och DTLS. Vårt kryptobibliotek för programvara har certifierats med FIPS 140-2. Vi använder även kryptografiska funktioner för maskinvara, minnesskydd via ThreadX-MODULER och stöd för ARM:s TrustZone ARMv8-M-säkerhetsfunktioner.

## <a name="components-of-azure-rtos"></a>Komponenter i Azure RTOS

Plattformen Azure RTOS är en samling körningslösningar som Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo och Azure RTOS USBX.

### <a name="azure-rtos-threadx"></a>Azure RTOS ThreadX

Azure [RTOS ThreadX](threadx/overview-threadx.md) är ett avancerat Real-Time-operativsystem (RTOS) som utformats särskilt för djupt inbäddade program. Bland de många fördelar Azure RTOS ThreadX tillhandahåller finns avancerade schemaläggningsmöjligheter, meddelandehantering, avbrottshantering och meddelandetjänster. Azure RTOS ThreadX har många avancerade funktioner, inklusive dess picokernel-arkitektur, schemaläggning före tröskel, händelsekedja och en omfattande uppsättning systemtjänster.

### <a name="azure-rtos-filex"></a>Azure RTOS FileX

Azure [RTOS FileX](filex/overview-filex.md) är ett FAT-kompatibelt filsystem med höga prestanda. Den är helt integrerad med Azure RTOS ThreadX och är tillgänglig för alla processorer som stöds. Precis Azure RTOS ThreadX är Azure RTOS FileX utformat för att ha ett litet fotavtryck och höga prestanda, vilket gör det idealiskt för dagens djupt inbäddade program som kräver filåtgärder. Azure RTOS FileX har stöd för de flesta fysiska media, inklusive RAM-disk, USBX, SD-KORT och UTT-/NOR-flashminnen via Azure RTOS LevelX.

### <a name="azure-rtos-guix"></a>Azure RTOS GUIX

Azure [RTOS GUIX är](guix/overview-guix.md) ett grafiskt användargränssnittspaket av professionell kvalitet som skapats för att uppfylla behoven hos utvecklare av inbäddade system. Till skillnad från alternativen är Azure RTOS GUIX litet, snabbt och enkelt att porta till praktiskt taget alla maskinvarukonfigurationer som kan ge stöd för grafiska utdata. Azure RTOS GUIX ger också utmärkt visuellt tilltalande och ett intuitivt och kraftfullt API för utveckling av användargränssnitt på programnivå.

### <a name="azure-rtos-netx"></a>Azure RTOS NetX

Azure [RTOS NetX](netx/overview-netx.md) är en högpresterande implementering av TCP/IP-protokollstandarder. Den är helt integrerad med Azure RTOS ThreadX och är tillgänglig för alla processorer som stöds. Azure RTOS NetX har en unik Piconet-arkitektur. I kombination med ett API med nollkopiering passar det perfekt för dagens djupt inbäddade program som kräver nätverksanslutning.

### <a name="azure-rtos-netx-duo"></a>Azure RTOS NetX Duo

Azure [RTOS NetX](netx-duo/overview-netx-duo.md) Duo är en avancerad TCP/IP-nätverksstack i branschklass som utformats särskilt för djupt inbäddade, realtidsbaserade och IoT-program. Azure RTOS NetX Duo är en dubbel IPv4- och IPv6-nätverksstack, medan NetX är den ursprungliga IPv4-nätverksstacken, i princip en delmängd av Azure RTOS NetX Duo.

### <a name="azure-rtos-usbx"></a>Azure RTOS USBX

Azure [RTOS USBX](usbx/overview-usbx.md) är en högpresterande USB-värd, -enhet och ON-The-Go-inbäddad STACK (OTG). Den är helt integrerad med ThreadX och är tillgänglig för alla Azure RTOS ThreadX-processorer som stöds. Precis som Azure RTOS ThreadX är Azure RTOS USBX utformat för att ha ett litet fotavtryck och hög prestanda, vilket gör det idealiskt för djupt inbäddade program som kräver ett gränssnitt med USB-enheter.

### <a name="windows-tools"></a>Windows verktyg

Azure [RTOS GUIX Studio](guix/about-guix-studio.md) tillhandahåller en komplett DESIGNmiljö för GUI-program som gör det lättare att skapa och underhålla alla grafiska element i programmets grafiska användargränssnitt. Azure RTOS GUIX Studio genererar automatiskt C-kod som är kompatibel med Azure RTOS GUIX-biblioteket, redo att kompileras och köras på målet.

Azure [RTOS TraceX](tracex/overview-tracex.md) är ett värdbaserat analysverktyg som ger utvecklare en grafisk vy över systemhändelser i realtid och gör det möjligt för dem att visualisera och bättre förstå beteendet för deras realtidssystem.

## <a name="the-azure-rtos-advantage"></a>Fördelen med Azure RTOS
Azure RTOS ger följande fördelar jämfört med andra operativsystem i realtid.

### <a name="most-deployed-rtos"></a>Mest distribuerad RTOS

Azure RTOS har över 6,2 miljarder distributioner över hela världen, enligt det ledande M2M-marknadsinformationsföretaget VDC Research. Hur populärt Azure RTOS är tillförlitlighet, kvalitet, storlek, prestanda, avancerade funktioner, användarvänlighet och övergripande fördelar med tid till marknad.

> *"Vi har följt den ökade tillväxten av THREADX på de trådlösa och IoT-marknader sedan företagets grundande, och är allt mer imponerade av det omfattande branschintagandet av THREADX."* – Chris Rommel, vice vd, VDC Research

### <a name="intuitive-and-consistent-api-design"></a>Intuitiv och konsekvent API-design

* Intuitivt och konsekvent API.
* Namngivningskonvention för substantivverb.
* Alla API:er har inledande prefix, till *exempel tx_* för ThreadX *och fx_* för FileX, för att enkelt identifiera Azure RTOS som de tillhör.
* Funktionell konsekvens i alla API:er. Till exempel har alla API-funktioner som pausar en valfri tidsgräns som fungerar på ett identiskt sätt.
* Många API:er är direkt tillgängliga från program-ISR:er.
- Valfria återanrop av användarmeddelanden för medie- och filåtgärder.
* Händelsedriven programmeringsmodell (API).

### <a name="high-efficiency"></a>Hög effektivitet

- Litet kodfotavtryck.
- Skalbart kodfotavtryck baserat på de tjänster som används.
- Förcertifierat av TUV och UL till IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D och EN 50128 SW-SIL4.
- Snabb körning. Azure RTOS är utformad för hastighet och har minimalt med interna funktionsanropslager för att uppnå högsta möjliga prestanda.

### <a name="fastest-time-to-market"></a>Snabbaste tid till marknad

Azure RTOS är enkelt att installera, lära sig, använda, felsöka, verifiera, certifiera och underhålla. Därför är Azure RTOS ett av de mest populära realtidsoperativsystemet för inbäddade IoT-enheter, inklusive många socs från Broadcom, Gainspan och så vidare. Vår konsekventa tid till marknad-fördel bygger på:

* Fullständig källkodstillgänglighet.
* Lätt att använda API:et.
* Omfattande och avancerad funktionsuppsättning.
* Kvalitetsdokumentation.

### <a name="one-simple-license"></a>En enkel licens

Det kostar inget att använda och testa källkoden och ingen kostnad för produktionslicenser när de distribueras till förlicensierade enheter. Alla andra enheter behöver en enkel årlig licens.

### <a name="full-highest-quality-source-code"></a>Fullständig källkod med högsta kvalitet

Under åren har Azure RTOS källkod angett stapeln i kvalitet och enkel förståelse. Dessutom ger konventionen att ha en funktion per fil för enkel källnavigering.

### <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a>Förcertifierat av TUV och UL till många säkerhetsstandarder

Azure RTOS har certifierats av SGS-TUV Saar för användning i säkerhetskritiska system enligt IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D och EN 50128. Certifieringen bekräftar att Azure RTOS kan användas i utvecklingen av säkerhetsrelaterad programvara för de högsta säkerhetsintegritetsnivåerna IEC-61508, IEC-62304, ISO 26262 och EN 50128 för "Funktionell säkerhet för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade system". SGS-TUV Saar, som bildas genom en gemensam sats av Tysklands SGS-Group och TUV Saarland, har blivit det ledande auktoriserade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad programvara för säkerhetsrelaterade system över hela världen. Den industriella säkerhetsstandarden IEC 61508 och alla standarder som härleds från den, inklusive IEC-62304, ISO 26262 och EN 50128, används för att garantera funktionell säkerhet för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, processkontrollsystem, industriella maskiner, bilar och styrenheter.

:::image type="content" source="media/partener-logo-sgs-tuv-saar.png" alt-text="SGS-TUV-certifiering":::

Azure RTOS har identifierats av UL för kompatibilitet med UL 60730-1 H, CSA E60730-1 Normal H, IEC 60730-1 Ul 60335-1 Inga R, IEC 60335-1 111 1998 säkerhetsstandarder för programvara i programmerbara komponenter. UL är ett globalt, oberoende säkerhetsvetenskapsföretag med mer än ett sekel av expertis inom innovation av säkerhetslösningar, från det offentliga elintagandet till banbrytande hållbarhet, förnyelsebar energi och nanoteknik.

:::image type="content" source="media/cru-logo-certification.png" alt-text="CRU UL-certifiering":::

Artefakter (certifikat, säkerhetshandbok, testrapport osv.) som är associerade med TUV- och UL-certifieringar är tillgängliga för försäljning.

I fall där programmet behöver ytterligare certifiering är en certifieringstjänst tillgänglig via Microsoft för att tillhandahålla nyckelnyckelcertifiering till olika standarder som använder den faktiska maskinvaruplattformen och även täcker programkoden. Kontakta oss för mer information om vår certifieringstjänst.

### <a name="eal4-common-criteria-security-certification"></a>EAL4+ Vanliga kriterier för säkerhetscertifiering

Azure RTOS har uppnått säkerhetscertifieringen EAL4+ Common Criteria. Utvärderingsmålet (TOE) omfattar Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS och Azure RTOS NetX MQTT. Detta representerar de mest typiska IoT-protokoll som krävs av djupt inbäddade sensorer, enheter, gränsroutrar och gatewayer.

:::image type="content" source="media/eal-logo-certification.png" alt-text="EAL-certifiering":::

Den IT-säkerhetsutvärderingsfunktion som används för Microsoft Azure RTOS SC-säkerhetscertifiering är Brightsight KARANTÄN och certifikatutfärdaren är SERTIT.

### <a name="fips-140-2-validated"></a>FIPS 140-2 Verifierad

Azure RTOS Crypto-bibliotek har uppnått FIPS 140-2-certifiering (Federal Information Processing Standardization 140-2) för programvara, som anger krav för kryptografimoduler. FIPS 140-2 kräver alla federala myndigheter och avdelningar som använder kryptografisk säkerhet för att uppfylla specifika standarder som rör krypteringsstyrka och -funktioner. Dessa kryptografiska säkerhetsstandarder är också kända i Kanada och EU.

Utvärderingslabbet för Information Security som användes för Azure RTOS Crypto-bibliotek var atsec och certifikatutfärdaren är [The National Institute of Standards and Technology (NIST).](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394)

### <a name="supports-most-popular-architectures"></a>Stöder de populäraste arkitekturerna

Azure RTOS på de populäraste 32/64-bitars mikroprocessorerna, fullständigt testade och fullständigt stödda, inklusive följande avancerade arkitekturer.

- **Analoga** enheter: SHARC, Blackfin, CM4xx

- **Andes Core:** RISC-V

- **Ambiqmicro:** McUs för McPu:er

- **ARM:** ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitars/R4/R5, TrustZone ARMv8-M

- **Cadence:** Xtensa, Diamond

- **CEVA:** PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, FM4, WICED WiFi

- **Cypress:** RISC-V

- **EnSilica:** eSi-RISC

- **Infineon:** XMC1000, XMC4000, TriCore

- **Intel; Intel FPGA:** x36/Pentium, XScale, NIOS II, Fpne, Arria 10

- **Microchip:** AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

- **Microsemi:** RISC-V

- **NXP:** LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

- **Renesas:** SH, HS, V850, RX, RZ, Synergi

- **Silicon Labs:** EFM32

- **Synopsys:** ARC 600, 700, ARC EM, ARC HS

- **ST:** STM32, ARM7, ARM9, Cortex-M3/M4/M7

- **Tl:** C5xxx, C6xxx,Modris, Sitara, Tiva-C

- **Wave Computing:** MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Klass

- **Xilinx:** MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Alla tids- och storlekssiffror som anges är uppskattningar och kan vara olika på din utvecklingsplattform.*

## <a name="in-the-context-of-azure-iot"></a>I samband med Azure IoT

Förutom att ansluta direkt till Azure IoT eller indirekt via Azure IoT Edge, finns Azure RTOS också tillgängligt på Azure Sphere enheter. Kombinationen av Azure RTOS och Azure Sphere samman bästa realtidsbearbetning och säkerhet på en enhet.
