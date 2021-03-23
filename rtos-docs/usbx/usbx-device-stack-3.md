---
title: Kapitel 3 – funktionella komponenter i USBX Device stack
description: Det här kapitlet innehåller en beskrivning av stacken med USBX inbäddade USB-enheter med hög prestanda från ett funktionellt perspektiv.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a20fed71cbee8c50519be4a971eb191e0cc93915
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827426"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a>Kapitel 3 – funktionella komponenter i USBX Device stack

Det här kapitlet innehåller en beskrivning av stacken med USBX inbäddade USB-enheter med hög prestanda från ett funktionellt perspektiv.

## <a name="execution-overview"></a>Översikt över körning

USBX för enheten består av flera komponenter.

- Initiering
- Program gränssnitts anrop
- Enhets klasser
- USB-enhets stack
- Enhets styrenhet
- VBUS Manager

Följande diagram illustrerar USBX Device-stacken.

![USBX Device-stack](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a>Initiering

Funktionen ***ux_system_initialize*** måste anropas för att aktivera USBX. Den här funktionen initierar minnes resurserna för USBX.

Funktionen ***ux_device_stack_initialize*** måste anropas för att kunna aktivera enhets anläggningar för USBX. Den här funktionen kommer att initiera alla resurser som används av USBX Device stack, till exempel ThreadX-trådar, mutexer och semaforer.

Det är upp till program initieringen att aktivera USB-styrenheten och en eller flera USB-klasser. Till skillnad från USB-värdstyrenheten kan enhets sidan bara ha en USB Controller-drivrutin som körs när som helst. När klasserna har registrerats till stacken och enhets styrenhetens (a) initierings funktion har anropats, är bussen aktiv och stacken svarar på kommandona för Bus-återställning och värd uppräkning.

### <a name="application-interface-calls"></a>Program gränssnitts anrop

Det finns två nivåer av API: er i USBX.

- Stack-API: er för USB-enhet
- API: er för USB-enhets klass

Normalt behöver ett USBX-program inte anropa någon av USB-API: erna för USB-enhet. De flesta program får bara åtkomst till API: er för USB-klass.

### <a name="usb-device-stack-apis"></a>Stack-API: er för USB-enhet

API: erna för enhets stacken ansvarar för registreringen av USBX-enhets komponenter, till exempel klasser och enhets ramverket.

### <a name="usb-device-class-apis"></a>API: er för USB-enhets klass

Klass-API: erna är särskilt speciella för varje USB-klass. De flesta vanliga API: er för USB-klasser tillhandahåller tjänster som att öppna/stänga en enhet och läsa från och skriva till en enhet. API: erna liknar värd sidans typ.

## <a name="device-framework"></a>Enhets ramverk

USB-enhetens sida ansvarar för definitionen av enhets ramverket. Enhets ramverket är uppdelat i tre kategorier, enligt beskrivningen i följande avsnitt.

### <a name="definition-of-the-components-of-the-device-framework"></a>Definition av komponenterna i enhets ramverket

Definitionen av varje komponent i enhets ramverket är relaterad till enhetens beskaffenhet och de resurser som används av enheten. Följande är de viktigaste kategorierna.

- Enhets Beskrivning
- Konfigurations Beskrivning
- Gränssnitts Beskrivning
- Slut punkts Beskrivning

USBX stöder enhets komponent definition för både hög och fullständig hastighet (låg hastighet behandlas på samma sätt som full hastighet). Detta gör att enheten fungerar annorlunda när den är ansluten till en hög hastighets-eller full hastighets värd. De typiska skillnaderna är storleken på varje slut punkt och den ström som förbrukas av enheten.

Definitionen av enhets komponenten tar formen av en byte-sträng som följer USB-specifikationen. Definitionen är sammanhängande och den ordning som ramverket är representerat i minnet är samma som det som returneras till värden under uppräkningen.

Följande är ett exempel på ett enhets ramverk för en USB-flash-disk med hög hastighet.

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

### <a name="definition-of-the-strings-of-the-device-framework"></a>Definition av strängarna i enhets ramverket

Strängar är valfria i en enhet. Syftet med detta är att låta USB-värden veta om enhetens tillverkare, produktens namn och revisions numret genom Unicode-strängarna.

Huvud strängarna är inbäddade index i enhets beskrivarna. Ytterligare sträng index kan bäddas in i enskilda gränssnitt.

Förutsatt att enhets ramverket ovan har tre sträng index inbäddade i enhets beskrivningen kan sträng Ramverks definitionen se ut som den här exempel koden.

```c
/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string
*/

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
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

Om olika strängar måste användas för varje hastighet måste olika index användas när indexen är hastigheten oberoende.

Kodningen för strängen är UNICODE-baserad. Mer information om UNICODE-encoding-standarden hittar du i följande publikation:

*Unicode-standarden, global tecken kodning, version 1., volym 1 och 2, Unicode-konsortiet, Addison-Wesley publicerings företag, läser MA.*

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a>Definition av de språk som stöds av enheten för varje sträng

USBX har möjlighet att stödja flera språk även om engelska är standard. Definitionen av varje språk för sträng beskrivningar är i form av en matris med språk definition som definieras enligt följande.

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

För att stödja ytterligare språk lägger du helt enkelt till språk kodens dubbla byte-definition efter den engelska standard koden. Språk koden har definierats av Microsoft i dokumentet.

*Utveckla internationell program vara för Windows 95 och Windows NT, Nadine Kano, Microsoft Press, Redmond, WA*

## <a name="vbus-manager"></a>VBUS Manager

I de flesta USB-enheter är VBUS inte en del av USB-enhetens kärna utan är i stället ansluten till en extern GPIO, som övervakar linje signalen.

Därför måste VBUS hanteras separat från enhets styrenhetens driv rutin.

Det är upp till programmet att tillhandahålla enhets styrenheten med adressen för VBUS i/o. VBUS måste initieras före initieringen av enhets styrenheten.

Beroende på plattforms specifikationen för övervakning av VBUS, är det möjligt att låta kontrollantens driv rutin hantera VBUS-signaler när VBUS i/o har initierats eller om detta inte är möjligt måste programmet tillhandahålla koden för att hantera VBUS.

Om programmet vill hantera VBUS själva, är det enda kravet att anropa funktionen ***ux_device_stack_disconnect*** när den upptäcker att en enhet har extraherats. Det är inte nödvändigt att meddela kontrollanten när en enhet sätts in, eftersom styrenheten kommer att aktive ras när bussen Återställ kontrollerad/avkontrollerande signalen identifieras.
