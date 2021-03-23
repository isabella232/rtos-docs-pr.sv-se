---
title: Vad är Microsoft Azure återställnings tider?
description: Azure återställnings tider är ett återställnings tider (real tids operativ system) för IoT-och Edge-enheter som drivs av mikrostyrenhet Units (MCU).
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 3b1c63135f6069652d7f66fc976b9d770a4dfeb2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826598"
---
# <a name="what-is-microsoft-azure-rtos"></a>Vad är Microsoft Azure återställnings tider

Azure återställnings tider är ett återställnings tider (real tids operativ system) för IoT-och Edge-enheter som drivs av mikrostyrenhet Units (MCU). Azure dataåterställnings tiders har utformats för att stödja de flesta mycket begränsade enheter (batteri som drivs och har mindre än 64 KB Flash-minne).
 
Azure återställnings tider är förcertifierat för en rad säkerhets standarder. Dessa inkluderar SIL för IEC 61508-4, IEC 62304-klass C och ISO 26262 ASIL D-certifieringar. Azure återställnings tider-ThreadX är också-178-certifierad.

Azure återställnings tider tillhandahåller en EAL4 + Common Criteria Security Certified-miljö, inklusive fullständig säkerhet i IP-skikt via IPsec och Socket Layer Security via TLS och DTLS. Program varans kryptografi bibliotek har uppnått FIPS 140-2-certifiering. Vi använder även maskinvaru-kryptografiska funktioner, minnes skydd via ThreadX-moduler och stöd för ARMns TrustZone ARMv8-M-säkerhetsfunktioner.

## <a name="components-of-azure-rtos"></a>Komponenter i Azure återställnings tider

Azure återställnings tider-plattformen är insamlingen av körnings lösningar, inklusive Azure återställnings tider ThreadX, Azure återställnings tider FileX, Azure återställnings tider GUIX, Azure återställnings tider NetX, Azure återställnings tider NetX Duo och Azure återställnings tider USBX.

### <a name="azure-rtos-threadx"></a>Azure RTOS ThreadX

Azure RTOS ThreadX är ett avancerat realtidsoperativsystem (RTOS) som är särskilt utformat för djupt inbäddade program. Bland de olika fördelarna med Azure återställnings tider-ThreadX finns avancerade funktioner för schemaläggning, meddelande överföring, hantering av avbrott och meddelande tjänster. Azure återställnings tider ThreadX har många avancerade funktioner, inklusive dess picokernel-arkitektur, avstängningen-tröskelvärde för schemaläggning, händelse länkning och en omfattande uppsättning system tjänster.

### <a name="azure-rtos-filex"></a>Azure RTOS FileX

Azure återställnings tider-FileX är ett FAT-kompatibelt fil system med hög prestanda. Den är helt integrerad med Azure återställnings tider ThreadX och är tillgänglig för alla processorer som stöds. Precis som med Azure återställnings tider-ThreadX är Azure återställnings tider FileX utformad för att ha ett litet utrymme och höga prestanda, vilket gör det perfekt för dagens djupt inbäddade program som kräver fil åtgärder. Azure återställnings tider FileX har stöd för de flesta fysiska media, inklusive RAM-disk, USBX, SD-kort och NAND/eller Flash-minnen via Azure återställnings tider LevelX.

### <a name="azure-rtos-guix"></a>Azure RTOS GUIX

Azure återställnings tider GUIX är ett grafiskt användar gränssnitts paket med professionell kvalitet som skapats för att uppfylla behoven hos inbäddade system utvecklare. Till skillnad från alternativen är Azure återställnings tider-GUIX liten, snabb och lätt att transportera till i stort sett all maskin varu konfiguration som stöder grafiska utdata. Azure återställnings tider GUIX ger också enastående visuellt överklagande och ett intuitivt och kraftfullt API för utveckling av användar gränssnitt på program nivå.

### <a name="azure-rtos-netx"></a>Azure RTOS NetX

Azure återställnings tider NetX är en högpresterande implementering av TCP/IP-protokollets standarder. Den är helt integrerad med Azure återställnings tider ThreadX och är tillgänglig för alla processorer som stöds. Azure återställnings tider-NetX har en unik piconet-arkitektur. Kombinerat med en tom kopierings-API gör den perfekt anpassad för dagens djupt inbäddade program som kräver nätverks anslutning.

### <a name="azure-rtos-netx-duo"></a>Azure RTOS NetX Duo

Azure återställnings tider NetX Duo är en avancerad, industri klass med TCP/IP-baserade nätverks stackar som utformats specifikt för djupt inbäddade, real tids-och IoT-program. Azure återställnings tider NetX Duo är en dubbel IPv4-och IPv6-nätverks stack, medan NetX är den ursprungliga IPv4-nätverks stacken, i stort sett en delmängd av Azure återställnings tider NetX Duo.

### <a name="azure-rtos-usbx"></a>Azure RTOS USBX

Azure återställnings tider-USBX är en högpresterande USB-värd, enhet och on-Go (OTG)-inbäddad stack. Den är helt integrerad med ThreadX och är tillgänglig för alla Azure återställnings tider ThreadX-processorer som stöds. Precis som med Azure återställnings tider-ThreadX är Azure återställnings tider USBX utformad för att ha ett litet utrymme och höga prestanda, vilket gör det perfekt för djupt inbäddade program som kräver ett gränssnitt med USB-enheter.

### <a name="windows-tools"></a>Windows-verktyg

Azure återställnings tider GUIX Studio innehåller en komplett design miljö för GUI-program, vilket underlättar skapandet och underhållet av alla grafiska element i programmets GUI. Azure återställnings tider GUIX Studio genererar automatiskt C-kod som är kompatibel med Azure återställnings tider GUIX-biblioteket, som är redo att kompileras och köras på målet.

Azure återställnings tider TraceX är ett värdbaserad analys verktyg som ger utvecklare en grafisk vy över system händelser i real tid och gör det möjligt för dem att visualisera och bättre förstå beteendet i real tids system.

## <a name="in-the-context-of-azure-iot"></a>I Azure IoT-kontext

Förutom att ansluta direkt till Azure IoT eller indirekt via Azure IoT Edge är Azure återställnings tider också tillgängligt på Azure Sphere enheter. Kombinationen av Azure återställnings tider och Azure Sphere ger förstklassig bearbetning och säkerhet i real tid i en enda enhet.
