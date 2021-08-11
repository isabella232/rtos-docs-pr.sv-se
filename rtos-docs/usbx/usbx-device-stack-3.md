---
title: Kapitel 3 – Funktionella komponenter i USBX-enhetsstacken
description: Det här kapitlet innehåller en beskrivning av stacken med USBX-inbäddad USB-enhet med höga prestanda ur ett funktionellt perspektiv.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 104badcbf1ec682cd8b09008578ba91768834d694473ecccf59e35637dfd9f3c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791365"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a>Kapitel 3 – Funktionella komponenter i USBX-enhetsstacken

Det här kapitlet innehåller en beskrivning av stacken med USBX-inbäddad USB-enhet med höga prestanda ur ett funktionellt perspektiv.

## <a name="execution-overview"></a>Körningsöversikt

USBX för enheten består av flera komponenter.

- Initiering
- Anrop till programgränssnitt
- Enhetsklasser
- USB-enhetsstack
- Enhetsstyrenhet
- VBUS-chef

Följande diagram illustrerar USBX-enhetsstacken.

![USBX-enhetsstack](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a>Initiering

För att aktivera USBX måste funktionen ***ux_system_initialize*** anropas. Den här funktionen initierar minnesresurserna för USBX.

För att aktivera USBX-enhetsanläggningar måste ***funktionen ux_device_stack_initialize*** anropas. Den här funktionen initierar i sin tur alla resurser som används av USBX-enhetsstacken, till exempel ThreadX-trådar, mutexer och semaforer.

Det är upp till programmets initiering att aktivera USB-enhetsstyrenheten och en eller flera USB-klasser. Till skillnad från USB-värdsidan kan enhetssidan bara ha en USB-styrenhetsdrivrutin som körs när som helst. När klasserna har registrerats i stacken och initieringsfunktionen för enhetsstyrenheter har anropats är buss aktiv och stacken svarar på kommandon för bussåterställning och värduppräkning.

### <a name="application-interface-calls"></a>Anrop till programgränssnitt

Det finns två nivåer av API:er i USBX.

- API:er för USB-enhetsstack
- API:er för USB-enhetsklass

Normalt bör ett USBX-program inte behöva anropa något av API:erna för USB-enhetsstacken. De flesta program kommer endast åt USB-klass-API:er.

### <a name="usb-device-stack-apis"></a>API:er för USB-enhetsstack

API:erna för enhetsstackar ansvarar för registreringen av USBX-enhetskomponenter, till exempel klasser och enhetsramverket.

### <a name="usb-device-class-apis"></a>API:er för USB-enhetsklass

Klass-API:erna är mycket specifika för varje USB-klass. De flesta vanliga API:er för USB-klasser tillhandahåller tjänster som att öppna/stänga en enhet och läsa från och skriva till en enhet. API:erna liknar värdsidan.

## <a name="device-framework"></a>Enhetsramverk

USB-enheten ansvarar för definitionen av enhetsramverket. Enhetsramverket är indelat i tre kategorier, enligt beskrivningen i följande avsnitt.

### <a name="definition-of-the-components-of-the-device-framework"></a>Definition av komponenterna i Device Framework

Definitionen av varje komponent i enhetsramverket är relaterad till enhetens typ och de resurser som används av enheten. Följande är huvudkategorierna.

- Enhetsbeskrivning
- Konfigurationsbeskrivning
- Gränssnittsbeskrivning
- Slutpunktsbeskrivning

USBX stöder enhetskomponentdefinitioner för både hög och full hastighet (låg hastighet behandlas på samma sätt som full hastighet). Detta gör att enheten kan fungera på olika sätt när den är ansluten till en värd med hög hastighet eller full hastighet. De vanligaste skillnaderna är storleken på varje slutpunkt och den ström som förbrukas av enheten.

Definitionen av enhetskomponenten har formen av en bytesträng som följer USB-specifikationen. Definitionen är sammanhängande och den ordning i vilken ramverket representeras i minnet är samma som det som returnerades till värden under uppräkningen.

Följande är ett exempel på ett enhetsramverk för en USB-flashdisk med hög hastighet.

```c
#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60
UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02, 0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50, 0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};
```

### <a name="definition-of-the-strings-of-the-device-framework"></a>Definition av strängar i Device Framework

Strängar är valfria i en enhet. Deras syfte är att meddela USB-värden om tillverkaren av enheten, produktnamnet och revisionsnumret via Unicode-strängar.

Huvudsträngarna är index som är inbäddade i enhetsbeskrivningarna. Ytterligare strängindex kan bäddas in i enskilda gränssnitt.

Förutsatt att enhetsramverket ovan har tre strängindex inbäddade i enhetsbeskrivningen kan definitionen av strängramverket se ut som den här exempelkoden.

```c
/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string
*/

#define STRING_FRAMEWORK_LENGTH 38
UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};
```

Om olika strängar måste användas för varje hastighet måste olika index användas eftersom indexen är hastighetsoberoende.

Strängens kodning är UNICODE-baserad. Mer information om UNICODE-kodningsstandarden finns i följande publikation:

*Unicode Standard, Worldwide Character Encoding, Version 1., Volumes 1 och 2, Unicode Consortium, Addison-Wesley Publishing Company, Reading MA.*

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a>Definition av de språk som stöds av enheten för varje sträng

USBX har stöd för flera språk, även om engelska är standard. Definitionen av varje språk för strängbeskrivningarna är i form av en matris med språkdefinition som definieras på följande sätt.

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

För att stödja ytterligare språk lägger du helt enkelt till språkkoden double-byte definition efter den engelska standardkoden. Språkkoden har definierats av Microsoft i dokumentet.

*Utveckla internationell programvara för Windows 95 och Windows NT, Nadine Kano, Microsoft Press, Redmond WA*

## <a name="vbus-manager"></a>VBUS Manager

I de flesta USB-enhetsutformningar är VBUS inte en del av USB-enhetskärnan utan ansluten till en extern GPIO som övervakar linjesignalen.

Därför måste VBUS hanteras separat från enhetsstyrenhetsdrivrutinen.

Det är upp till programmet att förse enhetskontrollanten med adressen till VBUS-IO:t. VBUS måste initieras innan styrenheten initieras.

Beroende på plattformsspecifikationen för övervakning av VBUS är det möjligt att låta styrenhetsdrivrutinen hantera VBUS-signaler när VBUS IO har initierats eller om detta inte är möjligt, måste programmet tillhandahålla koden för hantering av VBUS.

Om programmet vill hantera VBUS på egen hand är det enda kravet att anropa funktionen ***ux_device_stack_disconnect*** den upptäcker att en enhet har extraherats. Det är inte nödvändigt att informera kontrollanten när en enhet infogas eftersom styrenheten aktiveras när BUS RESET assert/deassert-signalen har identifierats.
