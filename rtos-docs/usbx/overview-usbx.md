---
title: Förstå Azure återställnings tider-USBX
description: Azure återställnings tider-USBX är en högpresterande USB-värd, enhet och on-Go (OTG)-inbäddad stack, Azure återställnings tider USBX är helt integrerat med Azure återställnings tider ThreadX och är tillgängligt för alla Azure återställnings tider-ThreadX – processorer som stöds.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 87eb6ee9f8733db3201280d377aa832b87131871
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828470"
---
# <a name="overview-of-azure-rtos-usbx"></a>Översikt över Azure återställnings tider-USBX

Azure återställnings tider-USBX är en högpresterande USB-värd, enhet och on-Go (OTG)-inbäddad stack. Azure återställnings tider USBX är helt integrerat med Azure återställnings tider ThreadX och är tillgängligt för alla ThreadX-processorer som stöds. Precis som ThreadX är Azure återställnings tider-USBX utformad för att ha ett litet utrymme och höga prestanda, vilket gör det perfekt för djupt inbäddade program som kräver ett gränssnitt med USB-enheter.

## <a name="host-device-otg--extensive-class-support"></a>Värd, enhet, OTG & omfattande klass support

Azure återställnings tider USBX-värd/inbyggda USB-protokollstacken är en inbäddad USB-lösning i närings klass som utformats specifikt för djupt inbäddade, real tids-och IoT-program. Azure återställnings tider-USBX tillhandahåller stöd för värdar, enheter och OTG samt omfattande klass support. Azure återställnings tider USBX är helt integrerat med ThreadX Real-Time-operativsystem, Azure återställnings tider FileX Embedded FAT-kompatibel fil system, Azure återställnings tider NetX och Azure återställnings tider NetX Duo Embedded TCP/IP-stackar. Allt detta, kombinerat med en mycket liten storlek, snabb körning och överlägsen enkel användning, gör Azure återställnings tider USBX det idealiska valet för de mest krävande inbäddade IoT-programmen som kräver USB-anslutning.

### <a name="small-footprint"></a>Små

Azure återställnings tider USBX har ett remarkably litet minimalt utrymme på 10,5 KB FLASH och 5,1 KB RAM för Azure återställnings tider USBX Device CDC/ACM support. Azure återställnings tider USBX-värden kräver minst 18 KB av FLASH och 25 KB RAM för stöd för CDC/ACM.

Det krävs ytterligare 10 KB till 13 KB av instruktions områdets minne för TCP-funktioner. Azure återställnings tider USBX RAM-användningen är vanligt vis mellan 2,6 KB och 3,6 KB plus det minne för Packet-poolen som definieras av programmet.

Precis som ThreadX skalas storleken på Azure återställnings tider-USBX automatiskt utifrån de tjänster som faktiskt används av programmet. Detta eliminerar behovet av komplicerade konfigurations-och bygg parametrar, vilket gör det enklare för utvecklaren.

### <a name="fast-execution"></a>Snabb körning

Azure återställnings tider USBX har utformats för snabbhet och har minimalt internt funktions anrops lager och stöd för cachelagring och DMA-användning. Allt detta och en allmän prestanda orienterad design filosofi hjälper Azure återställnings tider USBX att uppnå snabbast möjliga prestanda.

### <a name="simple-easy-to-use"></a>Enkel, lätt att använda

Azure återställnings tider-USBX är enkelt att använda. Azure återställnings tider USBX-API: et är både intuitivt och mycket funktionellt. API-namnen består av riktiga ord och inte "alfabet soppor" eller förkortade namn som är vanliga i andra fil system produkter. Alla Azure återställnings tider USBX-API: er har ledande "ux_" och följer en namn konvention för substantiv-verb. Det finns dessutom en funktions konsekvens i hela API: et. Till exempel har alla API: er som pausas en valfri tids gräns som fungerar på samma sätt för API: er.

### <a name="usb-interoperability-verification"></a>Verifiering av USB-interoperabilitet

Azure återställnings tider USBX Device stack har testats rigoröst med USB om standard test verktyg USBCV för att säkerställa full kompatibilitet med USB-specifikationer och interoperabilitet med olika värd system.
Dessutom har Azure återställnings tider USBX OTG-stacken verifierats och certifierats av den oberoende test labb Allion i Taiwan.

### <a name="usb-host-controller-support"></a>Stöd för USB-värdstyrenhet

Azure återställnings tider USBX har stöd för stora USB-standarder som OHCI och EHCI. Dessutom stöder Azure återställnings tider USBX egna diskreta USB-värdstyrenheter från Atmel, mikrochip, Philips, Renesas, ST, TI och andra leverantörer. Azure återställnings tider USBX stöder också flera värd styrenheter i samma program.
USB-enhetens styrenhet stöder Azure återställnings tider USBX har stöd för populära USB-styrenheter från analoga enheter, Atmel, mikrochip, NXP, Philips, Renesas, ST, TI och andra leverantörer.

### <a name="extensive-host-class-support"></a>Omfattande stöd för värd klass

Azure återställnings tider USBX-värd har stöd för de flesta populära klasserna, inklusive ASIX, AUDIO, CDC/ACM, CDC/ECM, GSER, HID (tangent bord, mus och fjärr styrning), hubb, PIMA (PTP/MTP), skrivare, PROLIFIC och lagring.

### <a name="extensive-usb-device-class-support"></a>Omfattande stöd för en USB-enhets klass

Azure återställnings tider USBX-enheten ger stöd för de flesta populära klasserna, inklusive CDC/ACM, CDC/ECM, DFU, HID, PIMA (PTP/MTP) (w/MTP), RNDIS och lagring. Stöd för anpassade klasser är också tillgängligt.

### <a name="pictbridge-support"></a>PictBridge-stöd

Azure återställnings tider USBX stöder fullständig PictBridge-implementering både på värden och på enheten. PictBridge är ovanpå Azure återställnings tider USBX PIMA (PTP/MTP)-klassen på båda sidor. PictBridge-standarden tillåter anslutning av en digital stillbilds kamera eller en smart telefon direkt till en skrivare utan en dator, vilket möjliggör direkt utskrift till vissa PictBridge-medvetna skrivare. När en kamera eller telefon är ansluten till en skrivare är skrivaren USB-värden och kameran är USB-enheten. Men med PictBridge visas kameran som värd och kommandona drivs från kameran. Kameran är lagrings servern, skrivaren på lagrings klienten. Kameran är utskrifts klienten och skrivaren är naturligtvis utskrifts servern. PictBridge använder USB som transport lager men förlitar sig på PTP (Picture Transfer Protocol) för kommunikations protokollet.

### <a name="custom-class-support"></a>Stöd för anpassade klasser

Azure återställnings tider USBX-värden och-enheten stöder anpassade klasser. Ett exempel på en anpassad klass finns i Azure återställnings tider USBX-distributionen. Den här enkla data Pumps klassen kallas DPUMP och kan användas som en modell för anpassade program klasser.
Avancerad teknik Azure återställnings tider USBX-värd och-enhet stöder anpassade klasser. Ett exempel på en anpassad klass finns i Azure återställnings tider USBX-distributionen. Azure återställnings tider-USBX är en avancerad teknik som innehåller:

* Stöd för värd-, enhets-och OTG
* USB-låg, fullständig och hög hastighets support
* Automatisk skalning
* Fullständigt integrerat med ThreadX, Azure återställnings tider FileX och Azure återställnings tider NetX
* Valfria prestanda mått
* Azure återställnings tider TraceX system Analysis support

### <a name="fastest-time-to-market"></a>Snabbast tid till marknad

Azure återställnings tider USBX har ett remarkably litet utrymme på 9 KB till 15 KB för grundläggande IP-och UDP-stöd. Azure återställnings tider USBX är enkelt att installera, lära sig, använda, felsöka, verifiera, certifiera och underhålla. Därför är Azure återställnings tider-USBX en av de mest populära USB-lösningarna för inbäddade IoT-enheter. Vår konsekventa tid till marknads fördelen bygger på:

* Kvalitets dokumentation – Läs mer i vår Azure återställnings tider USBX-värd och enhets användar handböcker och se själv!
* Fullständig käll kods tillgänglighet
* Lätt att använda API
* Omfattande och avancerad funktions uppsättning

## <a name="one-simple-license"></a>En enkel licens

Det kostar inget att använda och testa käll koden och ingen kostnad för produktions licenser när de distribueras till förinstallerade enheter, men alla andra enheter behöver en enkel årlig licens.

## <a name="full-highest-quality-source-code"></a>Fullständig käll kod med högsta kvalitet

Under åren har Azure återställnings tider NetX-källkoden ställt in kvalitet och enkel förståelse. Dessutom tillhandahåller konventionen om en funktion per fil för enkel käll navigering.

### <a name="supports-most-popular-architectures"></a>Har stöd för de flesta populära arkitekturerna

Azure återställnings tider-USBX körs på de flesta populära 32/64-bitars mikroprocessorer, färdiga, fullständigt testade och fullt stödda, inklusive följande:

* **Analoga enheter**: SHARC, Blackfin, CM4xx
* **Andes Core**: RISC-V
* **Ambiqmicro**: Apollo MCU
* **Arm**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitars/R4/R5, TrustZone ARMv8-M
* **Takt**: Xtensa, Diamond
* **CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, WICED WiFi
* **Cypress**: RISC-V
* **Kiseldioxid**: ESI – RISC
* **Infineon**: XMC1000, XMC4000, TriCore
* **Intel & Intel FPGA**: X36/Pentium, XSCALE, Nios II, Cyclone, Arria 10
* **Mikrochip**: avr32, ARM7, ARM9, cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/sa, PIC24/PIC32
* **Mikrohalv**: RISC-V
* **NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, coldfire, Kinetis cortex-M3/M4
* **Renesas**: SH, HS, V850, RX, RZ, synergieffekt Silicon Labs: EFM32
* **Sammanfattning**: båge 600, 700, båge EM, båg HS
* **St**: STM32, ARM7, ARM9, cortex-M3/M4/M7
* **TL**: C5xxx, C6xxx, Stellaris, Sitara, tiva-C
* **Wave-bearbetning**: MIPS32 4K, 24 K, 34 k, 1004 k, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class **Xilinx**: mikroblixt, powerpc 405, ZYNQ, ZYNQ UltraSCALE

## <a name="azure-rtos-usbx-apis"></a>Azure återställnings tider USBX-API: er

### <a name="azure-rtos-usbx-host-api"></a>Azure återställnings tider USBX-värd-API

Azure återställnings tider USBX-värd-API: et är ett intuitivt och konsekvent API som följer en namn konvention för substantiv-verb. Alla API: er har ledande ux_host_ * för att enkelt identifiera som USBX. Eventuella blockerings-API: er har valfria tråd-timeout.

* ASIX
    - Minimal 0,3 KB FLASH, 4 KB RAM
    - Automatisk spårning på scalingSystem via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-värd-API: er i detta formulär: *ux_host_class_asix_**
* IN
    - Minimal 1,2 KB FLASH, 4 KB RAM
    - Automatisk skalning
    - Intuitiva Azure återställnings tider USBX-värd-API: er i detta formulär: *ux_host_class_audio_**
* CDC/ACM
    - Minimal 1,4 KB FLASH, 4 KB RAM
    - Automatisk skalning
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-värd-API: er i detta formulär: *ux_host_class_cdc_acm_**
* Dold
    - Minimal 0,3 KB FLASH, 4 KB RAM
    - Tangent bord, mus och fjärrsupport
    - Automatisk skalning
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-värd-API: er i detta formulär: *ux_host_class_hid_** 
* )
    - Minimal 1,7 KB FLASH, 2 KB RAM
    - Automatisk skalning
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-värd-API: er i detta formulär: *ux_host_class_hub_**
* PIMA (PTP/MTP)
    - Minimal 0,9 KB FLASH, 8 KB RAM
    - Automatisk skalning
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-värd-API: er i detta formulär: *ux_host_class_pima_**
* SKRIVARKÖ
    - Minimal 0,8 KB FLASH, 8 KB RAM
    - Automatisk skalning
    -  Spårning på system nivå via Azure återställnings tider TraceX
    -  Intuitiva Azure återställnings tider USBX-värd-API: er i detta formulär: *ux_host_class_printer_**
* PROLIFIC
    - Minimal 1,5 KB FLASH, 4 KB RAM
    - Automatisk skalning
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-värd-API: er i detta formulär: *ux_host_class_prolific_**
* Innsbruck
    - Minimal 5,6 KB FLASH, 4 KB RAM
    - Automatisk skalning<br> Integrerat med Azure återställnings tider FileX
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-värd-API: er i detta formulär: *ux_host_class_storage_**
* USB-värd, STACK
    - Har stöd för många värd styrenheter
    - Minst 18 KB FLASH, 25 KB RAM
    - Automatisk skalning
    - Stöd för flera värd styrenheter på samma plattform
    -  USB-låg, fullständig och hög hastighets support
    -  Spårning på system nivå via Azure återställnings tider TraceX
    -  Intuitiva Azure återställnings tider USBX-värd-API: er i detta formulär: *ux_host_stack_* * 
* OHCI-, EHCI-och PATENTSKYDDade värd STYRENHETer 

### <a name="azure-rtos-usbx-device-api"></a>Azure återställnings tider USBX-enhets-API

Azure återställnings tider USBX Device API är ett intuitivt och konsekvent API som följer en namn konvention för substantiv-verb. Alla API: er har ledande ux_device_ * för att enkelt identifiera som USBX. Blockering av API: er har valfri tråd-timeout. Mer information finns i [användar handboken för Azure återställnings tider USBX-värden](usbx-host-stack-about.md) .

* CDC/ACM
    - Minimal 0,8 KB FLASH, 2 KB RAM
    - Automatisk skalning
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-enhets-API: er i detta formulär: * ux_device_class_cdc_acm_ * *.
* CDC/ECM
    - Minimal 1,5 KB FLASH, 4 KB till 8 KB RAM
    - Automatisk skalning
    - Spårning på system nivå via Azure återställnings tider TraceX<br> Intuitiva Azure återställnings tider USBX-enhets-API: er i detta formulär: * ux_device_class_cdc_ecm_ * *.
* DFU
    - Minimal 1,1 KB FLASH, 2 KB RAM
    -  Automatisk skalning
    -  Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-enhets-API: er i detta formulär: *ux_device_class_dfu_** 
* GSER
    - Minimal 0,6 KB FLASH, 4 KB RAM
    - Automatisk skalning
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-enhets-API: er i detta formulär: *ux_device_class_gser_**
* Dold
    - Minimal 0,9 KB FLASH, 2 KB RAM
    - Automatisk skalning
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-enhets-API: er i detta formulär: *ux_device_class_hid_** PIMA (PTP/MTP)
    - Minimal 5,2 KB FLASH, 8 KB RAM
    - Automatisk skalning
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-enhets-API: er i detta formulär: *ux_device_class_pima_** 
* LAGRING
    - Minimal 2,3 KB FLASH, 4 KB RAM
    - Automatisk skalning
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-enhets-API: er i detta formulär: *ux_device_class_storage_**
* RNDIS
    - Minimal 2,3 KB FLASH, 4 KB till 8 KB RAM
    - Automatisk skalning
    - Integrerat med Azure återställnings tider NetX och Azure återställnings tider NetX DUO
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-enhets-API: er i detta formulär: *ux_device_class_rndls_**
* Enhets STACK för Azure återställnings tider USBX
    - Minimal 2,3 KB FLASH, 4 KB RAM
    - Automatisk skalning
    - Spårning på system nivå via Azure återställnings tider TraceX
    - Intuitiva Azure återställnings tider USBX-enhets-API: er i detta formulär: *ux_device_class_storage_**
* TILLVERKARSPECIFIKA värd STYRENHETer

## <a name="next-steps"></a>Nästa steg

Börja arbeta med Azure återställnings tider USBX-värden och enhets stacken genom att följa vår Användar handbok för [värd stacken](usbx-host-stack-about.md) eller [användar handboken för enhets stacken](usbx-device-stack-about.md).