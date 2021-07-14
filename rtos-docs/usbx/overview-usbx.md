---
title: Förstå Azure RTOS USBX
description: Azure RTOS USBX är en inbäddad STACK med höga prestanda för USB-värd, enhet och on-the-go (OTG), är Azure RTOS USBX helt integrerat med Azure RTOS ThreadX och tillgängligt för alla Azure RTOS ThreadX-processorer som stöds.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 3c214a49f7dd1af20c20f07412fb072dd785b16f
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754836"
---
# <a name="overview-of-azure-rtos-usbx"></a>Översikt över AZURE RTOS USBX

Azure RTOS USBX är en inbäddad STACK med höga prestanda för USB-värd, -enhet och on-the-go (OTG). Azure RTOS USBX är helt integrerat med Azure RTOS ThreadX och tillgängligt för alla ThreadX-processorer som stöds. Precis som ThreadX är Azure RTOS USBX utformat för att ha ett litet fotavtryck och höga prestanda, vilket gör det idealiskt för djupt inbäddade program som kräver ett gränssnitt med USB-enheter.

## <a name="host-device-otg--extensive-class-support"></a>Värd, enhet, OTG & omfattande klasssupport

Azure RTOS USBX-värd/enhetsinbäddad USB-protokollstack är en inbäddad USB-lösning i industriell klass som utformats särskilt för djupt inbäddade, realtids- och IoT-program. Azure RTOS USBX ger stöd för värd, enhet och OTG, samt omfattande klassstöd. Azure RTOS USBX är helt integrerat med operativsystemet ThreadX Real-Time, Azure RTOS FileX embedded FAT-kompatibla filsystem, Azure RTOS NetX och Azure RTOS NetX Duo inbäddade TCP/IP-stackar. Allt detta i kombination med ett mycket litet fotavtryck, snabb körning och överlägsen användarvänlighet gör Azure RTOS USBX till det perfekta valet för de mest krävande inbäddade IoT-programmen som kräver USB-anslutning.

### <a name="usbx-memory-footprint"></a>USBX-minnesfotavtryck

Azure RTOS USBX har ett mycket litet minimalt fotavtryck på 10,5 kB FLASH och 5,1 KB RAM för Azure RTOS USBX-enhetens CDC/ACM-stöd. Azure RTOS USBX-värden kräver minst 18 KB FLASH och 25 KB RAM för CDC/ACM-stöd.

Ytterligare 10 KB till 13 KB instruktionsområdesminne krävs för TCP-funktioner. Azure RTOS USBX RAM-användning sträcker sig vanligtvis från 2,6 kB till 3,6 kB plus paketpoolens minne, vilket definieras av programmet.

Precis som ThreadX skalas storleken Azure RTOS USBX automatiskt baserat på de tjänster som faktiskt används av programmet. Detta eliminerar praktiskt taget behovet av komplicerad konfiguration och byggparametrar, vilket gör det enklare för utvecklaren.

### <a name="usb-interoperability-verification"></a>USB-samverkansverifiering

Azure RTOS USBX-enhetsstack har noggrant testats med USB IF-standardtestverktyget USBCV för att säkerställa fullständig efterlevnad av USB-specifikationerna och samverkan med olika värdsystem.
Dessutom har Azure RTOS USBX OTG-stack verifierats och certifierats av den oberoende testlabbet Allion i Taiwan.

### <a name="usb-host-controller-support"></a>Stöd för USB-värdstyrenhet

Azure RTOS USBX har stöd för stora USB-standarder som OHCI och EHCI. Dessutom stöder Azure RTOS USBX egna diskreta USB-värdstyrenheter från Atmel, Microchip, Chip, Renesas, ST, TI och andra leverantörer. Azure RTOS USBX stöder också flera värdstyrenheter i samma program.
STÖD för USB-Azure RTOS USBX stöder populära USB-enhetsstyrenheter från analoga enheter, Atmel, Microchip, NXP, Tier, Renesas, ST, TI och andra leverantörer.

### <a name="extensive-host-class-support"></a>Omfattande stöd för värdklass

Azure RTOS USBX-värd har stöd för de flesta populära klasser, inklusive ASIX, AUDIO, CDC/ACM, CDC/ECM, GSER, HID (tangentbord, mus och fjärrstyrning), HUB, PIMA (PTP/MTP), PRINTER, PROLIFIC och STORAGE.

### <a name="extensive-usb-device-class-support"></a>Omfattande stöd för USB-enhetsklass

Azure RTOS USBX-enhet har stöd för de flesta populära klasser, inklusive CDC/ACM, CDC/ECM, DFU, HID, PIMA (PTP/MTP) (w/MTP), RNDIS och STORAGE. Stöd för anpassade klasser är också tillgängligt.

### <a name="pictbridge-support"></a>Pictbridge-stöd

Azure RTOS USBX stöder den fullständiga Pictbridge-implementeringen både på värden och enheten. Pictbridge finns ovanpå klassen AZURE RTOS USBX PIMA (PTP/MTP) på båda sidor. PictBridge-standarden tillåter anslutning av en digital fortfarande kamera eller en smart telefon direkt till en skrivare utan dator, vilket möjliggör direktutskrift till vissa Pictbridge-medvetna skrivare. När en kamera eller telefon är ansluten till en skrivare är skrivaren USB-värden och kameran är USB-enheten. Men med Pictbridge visas kameran som värden och kommandona körs från kameran. Kameran är lagringsservern, skrivaren för lagringsklienten. Kameran är utskriftsklienten och skrivaren är naturligtvis utskriftsservern. Pictbridge använder USB som transportlager men förlitar sig på PTP (Picture Transfer Protocol) för kommunikationsprotokollet.

### <a name="custom-class-support"></a>Stöd för anpassade klasser

Azure RTOS USBX-värd och enhet stöder anpassade klasser. Ett exempel på en anpassad klass finns i Azure RTOS USBX-distributionen. Den här enkla datapumpklassen kallas DPUMP och kan användas som en modell för anpassade programklasser.
Avancerad teknik Azure RTOS USBX-värd och enhet stöder anpassade klasser. Ett exempel på en anpassad klass finns i Azure RTOS USBX-distributionen. Azure RTOS USBX är avancerad teknik som omfattar:

* Stöd för värd, enhet och OTG
* Stöd för USB med låg, fullständig och hög hastighet
* Automatisk skalning
* Helt integrerad med ThreadX, Azure RTOS FileX och Azure RTOS NetX
* Valfria prestandamått
* Azure RTOS TraceX-systemanalysstöd

## <a name="azure-rtos-usbx-apis"></a>Azure RTOS USBX-API:er

### <a name="azure-rtos-usbx-host-api"></a>Azure RTOS USBX-värd-API

Det Azure RTOS USBX-värd-API:et är ett intuitivt och konsekvent API som följer en namngivningskonvention med substantivverb. Alla API:er har ledande ux_host_* som enkelt kan identifieras som USBX. Eventuella blockerande API:er har valfria tråd-timeout.

* ASIX
    - Minimal 0,3 KB FLASH, 4 KB RAM
    - Automatisk skalningSpårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-värd-API:er i det här formuläret: *ux_host_class_asix_**
* Ljud
    - Minimal 1,2 KB FLASH, 4 KB RAM
    - Automatisk skalning
    - Intuitiva Azure RTOS USBX-värd-API:er i det här formuläret: *ux_host_class_audio_**
* CDC/ACM
    - Minimal 1,4 KB FLASH, 4 KB RAM
    - Automatisk skalning
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-värd-API:er i det här formuläret: *ux_host_class_cdc_acm_**
* Hid
    - Minimal 0,3 KB FLASH, 4 KB RAM
    - Stöd för tangentbord, mus och fjärrstyrning
    - Automatisk skalning
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-värd-API:er i det här formuläret: *ux_host_class_hid_** 
* Nav
    - Minimal 1,7 KB FLASH, 2 KB RAM
    - Automatisk skalning
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-värd-API:er i det här formuläret: *ux_host_class_hub_**
* PIMA (PTP/MTP)
    - Minimal 0,9 KB FLASH, 8 KB RAM
    - Automatisk skalning
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-värd-API:er i det här formuläret: *ux_host_class_pima_**
* Skrivare
    - Minimal 0,8 KB FLASH, 8 KB RAM
    - Automatisk skalning
    -  Spårning på systemnivå via Azure RTOS TraceX
    -  Intuitiva Azure RTOS USBX-värd-API:er i det här formuläret: *ux_host_class_printer_**
* Produktiv
    - Minimal 1,5 KB FLASH, 4 KB RAM
    - Automatisk skalning
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-värd-API:er i det här formuläret: *ux_host_class_prolific_**
* STORAG
    - Minimal 5,6 KB FLASH, 4 KB RAM
    - Automatisk skalning<br> Integrerad med Azure RTOS FileX
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-värd-API:er i det här formuläret: *ux_host_class_storage_**
* USB-värdstack
    - Stöder många värdstyrenheter
    - Minimal 18 KB FLASH, 25 KB RAM
    - Automatisk skalning
    - Stöd för flera värdstyrenheter på samma plattform
    -  Stöd för USB med låg, fullständig och hög hastighet
    -  Spårning på systemnivå via Azure RTOS TraceX
    -  Intuitiva Azure RTOS USBX-värd-API:er i det här formuläret: *ux_host_stack_* * 
* OHCI, EHCI, PATENTSKYDDADE värdSTYRENHETER 

### <a name="azure-rtos-usbx-device-api"></a>AZURE RTOS USBX-enhets-API

API:Azure RTOS USBX-enhet är ett intuitivt och konsekvent API som följer en namngivningskonvention med substantivverb. Alla API:er har ledande ux_device_* som enkelt kan identifieras som USBX. Blockerande API:er har valfria tråd-timeout. Se [användarhandboken Azure RTOS USBX-värd](usbx-host-stack-about.md) för mer information.

* CDC/ACM
    - Minimal 0,8 KB FLASH, 2 KB RAM
    - Automatisk skalning
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-enhets-API:er i det här formuläret: *ux_device_class_cdc_acm_**.
* CDC/ECM
    - Minimal 1,5 KB FLASH, 4 KB till 8 KB RAM
    - Automatisk skalning
    - Spårning på systemnivå via Azure RTOS TraceX<br> Intuitiva Azure RTOS USBX-enhets-API:er i det här formuläret: *ux_device_class_cdc_ecm_**.
* Dfu
    - Minimal 1,1 KB FLASH, 2 KB RAM
    -  Automatisk skalning
    -  Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-enhets-API:er i det här formuläret: *ux_device_class_dfu_** 
* GSER
    - Minimal 0,6 KB FLASH, 4 KB RAM
    - Automatisk skalning
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-enhets-API:er i det här formuläret: *ux_device_class_gser_**
* Hid
    - Minimal 0,9 KB FLASH, 2 KB RAM
    - Automatisk skalning
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-enhets-API:er i *det här formuläret: ux_device_class_hid_** PIMA (PTP/MTP)
    - Minimal 5,2 KB FLASH, 8 KB RAM
    - Automatisk skalning
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-enhets-API:er i det här formuläret: *ux_device_class_pima_** 
* LAGRING
    - Minimal 2,3 KB FLASH, 4 KB RAM
    - Automatisk skalning
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-enhets-API:er i det här formuläret: *ux_device_class_storage_**
* RNDIS
    - Minimal 2,3 KB FLASH, 4 KB till 8 KB RAM
    - Automatisk skalning
    - Integrerad med Azure RTOS NetX och Azure RTOS NetX DUO
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-enhets-API:er i det här formuläret: *ux_device_class_rndls_**
* Azure RTOS USBX-enhetsstack
    - Minimal 2,3 KB FLASH, 4 KB RAM
    - Automatisk skalning
    - Spårning på systemnivå via Azure RTOS TraceX
    - Intuitiva Azure RTOS USBX-enhets-API:er i det här formuläret: *ux_device_class_storage_**
* EGNA värdSTYRENHETER

## <a name="next-steps"></a>Nästa steg

Börja arbeta med Azure RTOS USBX-värden och enhetsstacken genom att följa [användarhandboken för värdstacken](usbx-host-stack-about.md) [eller användarhandboken för enhetsstacken.](usbx-device-stack-about.md)