---
title: Kapitel 3 – funktionella komponenter i USBX Host stack
description: Det här kapitlet innehåller en beskrivning av USBX-stacken med hög prestanda för inbäddade USB-värdar från ett funktionellt perspektiv.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 17b8d884dd2c71d60e91f5fcec40c360060f4fe8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828368"
---
# <a name="chapter-3---functional-components-of-usbx-host-stack"></a>Kapitel 3 – funktionella komponenter i USBX Host stack

Det här kapitlet innehåller en beskrivning av USBX-stacken med hög prestanda för inbäddade USB-värdar från ett funktionellt perspektiv.

## <a name="execution-overview"></a>Översikt över körning

USBX består av flera komponenter:

- Initiering
- Program gränssnitts anrop
- Root Hub
- NAV klass
- Värd klasser
- USB-värd, stack
- Värd styrenhet

I följande diagram illustreras USBX-värds Tacken.

![USBX värds tack](./media/usbx-host-stack/usbx-host-stack.png)

### <a name="initialization"></a>Initiering

Funktionen ***ux_system_initialize*** måste anropas för att aktivera USBX. Den här funktionen initierar minnes resurserna för USBX.

Funktionen ***ux_host_stack_initialize*** måste anropas för att aktivera USBX-värd anläggningar. Den här funktionen kommer i sin tur initiera alla resurser som används av USBX-värd stacken, till exempel ThreadX-trådar, mutexer och semaforer.

Det är upp till program initieringen att aktivera minst en USB-värdstyrenhet och en eller flera USB-klasser. När klasserna har registrerats till stacken och värd styrenhetens (a) initierings funktion har anropats är bussen aktiv och enhets identifieringen kan starta. Om värd styrenhetens rotmål identifierar en ansluten enhet, aktive ras USB-uppräknings tråden som är ansvarig för USB-topologin och fortsätter att räkna upp enhet (er).

Därför är det möjligt att alla anslutna USB-enheter kanske inte har kon figurer ATS helt när värd styrenhetens initierings funktion returnerar. Det kan ta flera sekunder att räkna upp alla USB-enheter, särskilt om det finns ett eller flera hubbar mellan rotnavet och USB-enheter.

### <a name="application-interface-calls"></a>Program gränssnitts anrop

Det finns två nivåer av API: er i USBX.

- Stack-API: er för USB-värd
- API: er för USB-värd klass

Normalt behöver ett USBX-program inte anropa någon av USB-värdens stack-API-funktioner. De flesta program får bara åtkomst till API-funktionerna i USB-klass.

### <a name="usb-host-stack-apis"></a>Stack-API: er för USB-värd

API-funktionerna i värd stacken ansvarar för registreringen av USBX-komponenter (värd klasser och värd styrenheter), konfiguration av enheter och överförings begär Anden för tillgängliga enhets slut punkter.

### <a name="usb-host-class-api"></a>API för USB-värd klass

Klass-API: erna är särskilt speciella för varje USB-klass. De flesta vanliga API-funktioner för USB-klasser tillhandahåller tjänster som att öppna/stänga en enhet och läsa från och skriva till en enhet.

### <a name="root-hub"></a>Root Hub

Varje värd styrenhets instans har ett eller flera USB-rotnav. Antalet rot nav bestäms antingen av styrenhetens typ eller kan hämtas genom att läsa specifika register från kontroll enheten.

### <a name="hub-class"></a>NAV klass

NAV klassen är ansvarig för USB-hubbar. En USB-hubb kan antingen vara en fristående hubb eller som en del av en sammansatt enhet, till exempel ett tangent bord eller en övervakare. En hubb kan vara oberoende eller bussad. Buss drivna nav har högst fyra underordnade portar och kan bara tillåta anslutning av enheter som antingen är självständiga eller bussbaserade enheter som använder mindre än 100mA energi. Hubbar kan överlappa varandra. Upp till fem hubbar kan vara anslutna till varandra.

### <a name="usb-host-stack"></a>USB-värd, stack

USB-värdstyrenheten är centerpiece för USBX. Den har tre huvud funktioner.

- Hantera USB-topologin.
- Bind en USB-enhet till en eller flera klasser.
- Ange ett API för klasser för att utföra förhör av enhets beskrivningar och USB-överföringar.

### <a name="topology-manager"></a>Topology Manager

Tråden för USB-stack-topologi är aktive ras när en ny enhet är ansluten eller när en enhet har kopplats från. Antingen rot navet eller en vanlig hubb kan du acceptera enhets anslutningar. När en enhet har anslutits till USB-enheten hämtar Topology Manager enhets beskrivningen. Den här beskrivningen kommer att innehålla antalet möjliga konfigurationer som är tillgängliga för den här enheten. De flesta enheter har bara en konfiguration. Vissa enheter kan användas på olika sätt beroende på vilken ström som är tillgänglig på den port där den är ansluten. I så fall har enheten flera konfigurationer som kan väljas beroende på tillgänglig ström. När enheten har kon figurer ATS av Topology Manager, tillåts den mängden energi som anges i konfigurations beskrivningen.

## <a name="usb-class-binding"></a>Bindning av USB-klass

När enheten har kon figurer ATS tillåter Topology Manager att klass hanteraren fortsätter enhets identifieringen genom att titta på enhets gränssnittets beskrivningar. En enhet kan ha en eller flera gränssnitts beskrivningar.

Ett gränssnitt representerar en funktion i en enhet. Till exempel har en USB-högtalare tre gränssnitt, en för ljud uppspelning, en för ljud kontroll och en för att hantera de olika högtalar knapparna.

Klass hanteraren har två mekanismer för att ansluta enhets gränssnitten till en eller flera klasser. Den kan antingen använda kombinationen av ett PID/VID (produkt-ID och leverantörs-ID) som finns i gränssnitts beskrivningen eller kombinationen av klass/underklass/protokoll.

PID/VID-kombinationen är giltig för gränssnitt som inte kan drivas av en generisk klass. Kombinationen klass/underklass/protokoll används av gränssnitt som tillhör en USB-IF-certifierad klass, till exempel en skrivare, hubb, lagring, ljud eller HID.

Klass hanteraren innehåller en lista över registrerade klasser från initieringen av USBX. Klass hanteraren anropar varje klass en i taget tills en klass accepterar för att hantera gränssnittet för enheten. En klass kan bara hantera ett gränssnitt. I exempel på USB-ljudhögtalare kommer klass hanteraren att anropa alla klasser för var och en av gränssnitten.

När en klass accepterar ett gränssnitt skapas en ny instans av klassen. Klass hanteraren kommer sedan att söka efter standard alternativ inställningen för gränssnittet. En enhet kan ha en eller flera alternativa inställningar för varje gränssnitt. Den alternativa inställningen 0 används som standard tills en klass bestämmer sig för att ändra den.

För standard alternativ inställningen monterar klass hanteraren alla slut punkter som ingår i den alternativa inställningen. Om monteringen av varje slut punkt lyckas Slutför klass hanteraren sitt jobb genom att gå tillbaka till den klass som avslutar initieringen av gränssnittet.

### <a name="usbx-apis"></a>USBX-API: er

USB-stacken exporterar ett visst antal API: er för USB-klasserna för att utföra förhör på enheten och USB-överföringar på specifika slut punkter. Dessa API-funktioner beskrivs i detalj i den här referens hand boken.

### <a name="host-controller"></a>Värd styrenhet

Värd styrenhetens driv rutin ansvarar för att köra en speciell typ av USB-styrenhet. En USB-värdstyrenhet kan ha flera styrenheter i. Vissa Intel PC-chipset innehåller till exempel två UHCI-kontrollanter. Vissa USB 2,0-styrenheter innehåller flera instanser av en OHCI-styrenhet, förutom en instans av EHCI-styrenheten.

Värd styrenheten hanterar bara flera instanser av samma kontrollant. För att kunna driva de flesta USB 2,0-värd styrenheter måste du initiera både OCHI-styrenheten och EHCI-styrenheten under initieringen av USBX.

Värd styrenheten ansvarar för att hantera följande.

- Root Hub
- Energisparfunktioner
- Slutpunkter
- Överlåtelse

### <a name="root-hub"></a>Root Hub

Hantering av rot nav ansvarar för att starta varje styrenhets port och bestämma om en enhet har satts in eller inte. Den här funktionen används av USBX Generic root Hub för att kunna använda kontrollantens underordnade portar.

### <a name="power-management"></a>Energisparfunktioner

Bearbetningen av energispar funktioner gör att du kan hantera PAUSE/återuppta signaler antingen i Gang-läge, vilket påverkar alla underordnade portar på samma gång, eller individuellt om kontrollanten erbjuder den här funktionen.

### <a name="endpoints"></a>Slutpunkter

Slut punkts hanteringen ger möjlighet att skapa eller destruera fysiska slut punkter till kontrollanten. De fysiska slut punkterna är minnes enheter som tolkas av kontrollanten om styrenheten stöder Master DMA eller som är skrivna i kontrollanten. De fysiska slut punkterna innehåller transaktions information som ska utföras av kontrollanten.

### <a name="transfers"></a>Överlåtelse

Överförings hantering tillhandahåller en klass för att utföra en transaktion på varje slut punkt som har skapats. Varje logisk slut punkt innehåller en komponent som kallas ÖVERFÖRINGs förfrågan för USB-överförings begär Anden. ÖVERFÖRINGSBEGÄRAN används av stacken för att beskriva transaktionen. Denna ÖVERFÖRINGSBEGÄRAN skickas sedan till stacken och till kontrollanten, som kan dela upp den i flera under transaktioner beroende på funktionerna i kontrollanten.

## <a name="usb-device-framework"></a>Ramverk för USB-enhet

En USB-enhet representeras av ett träd med beskrivningar. Det finns sex huvud typer av beskrivningar.

- Enhets beskrivningar
- Konfigurations beskrivningar
- Gränssnitts beskrivningar
- Slut punkts beskrivningar
- Sträng beskrivningar
- Funktionella beskrivare

En USB-enhet kan ha en mycket enkel beskrivning och ser ut så här.
![Enkel USB-enhet](./media/usbx-host-stack/usb-device-simple.png)

I bilden ovan har enheten bara en konfiguration. Ett enda gränssnitt är kopplat till den här konfigurationen, vilket indikerar att enheten bara har en funktion och bara har en slut punkt. Kopplad till enhets beskrivningen är en sträng beskrivning som ger en synlig identifiering av enheten.

En enhet kan dock vara mer komplex och kan visas på följande sätt.

![Komplex USB-enhet](./media/usbx-host-stack/usb-device-complex.png)

I bilden ovan har enheten två konfigurations beskrivningar kopplade till enhets beskrivningen. Den här enheten kan indikera att den har två energi lägen eller kan drivas av antingen standard klasser eller egna klasser.

Kopplade till den första konfigurationen är två gränssnitt som indikerar att enheten har två logiska funktioner. Den första funktionen har 3 slut punkts beskrivningar och en funktionell beskrivning. Den funktionella beskrivningen kan användas av den klass som ansvarar för att köra gränssnittet för att få ytterligare information om det här gränssnittet som normalt inte hittas av en allmän beskrivning.

### <a name="device-descriptors"></a>Enhets beskrivningar

Varje USB-enhet har en enda enhets beskrivning. Den här beskrivningen innehåller enhets identifieringen, antalet konfigurationer som stöds och egenskaperna för den standard kontroll slut punkt som används för att konfigurera enheten.

| Offset | Fält              | Storlek | Värde    | Beskrivning                             |
| ------ | ------------------ | ---- | -------- | --------------------------------------- |
| 0      | BLength            | 1    | Antal   | Storlek på den här beskrivningen i byte |
| 1      | bDescriptorType    | 1    | Konstant | ENHETs beskrivnings typ |
| 2      | bcdUSB             | 2    | BCD      | Versions nummer för USB-specifikation i BinaryCoded dec<br />Exempel: 2,10 motsvarar 0x210. I det här fältet identifieras versionen av USB-specifikationen att enheten och dess beskrivningar är kompatibla med. |
| 4      | bDeviceClass       | 1    | Klass    | Klass kod (tilldelad av USB-IF).<br />Om det här fältet återställs till 0, anger varje gränssnitt i en konfiguration sin egen klass information och de olika gränssnitten fungerar oberoende av varandra.<br />Om det här fältet är inställt på ett värde mellan 1 och 0xFE, stöder enheten olika klass specifikationer på olika gränssnitt och gränssnitten kanske inte fungerar separat. Det här värdet identifierar den klass definition som används för de aggregerade gränssnitten.<br />Om det här fältet är inställt på 0xFF är enhets klassen leverantörsspecifik. |
| 5      | bDeviceSubClass    | 1    | Underklass | Underklassens kod (tilldelad av USB-IF).<br />Dessa koder är kvalificerade med värdet för fältet bDeviceClass. Om fältet bDeviceClass återställs till 0 måste det här fältet också återställas till 0. Om fältet bDeviceClass inte är inställt på 0xFF, är alla värden reserverade för tilldelning av USB. |
| 6      | bDeviceProtocol    | 1    | Protokoll | Protokoll kod (tilldelad av USB-IF).<br />Dessa koder kvalificeras av värdet för bDeviceClass och bDeviceSubClass-fälten. Om en enhet har stöd för klassbaserade protokoll på enhets nivå i stället för ett gränssnitt, identifierar den här koden de protokoll som enheten använder enligt specifikationen i enhets klassen. Om det här fältet återställs till 0 använder enheten inte klassbaserade protokoll på en enhets nivå.<br />Det kan dock använda klassbaserade protokoll på ett gränssnitt.<br />Om det här fältet är inställt på 0xFF använder enheten ett leverantörsspecifika protokoll på enhets nivå. |
| 7      | bMaxPacketSize0    | 1    | Antal   | Maximal paket storlek för slut punkt noll (endast byte storlekar på 8, 16, 32 eller 64 är giltiga) |
| 8      | idVendor           | 2    | ID       | Leverantörs-ID (tilldelat av USB-IF) |
| 10     | idProduct          | 2    | ID       | Produkt-ID (tilldelat av tillverkaren) |
| 12     | bcdDevice          | 2    | BCD      | Enhets versions nummer i binärt kodad decimal |
| 14     | iManufacturer      | 1    | Index    | Index för sträng beskrivning som beskriver tillverkare |
| 15     | iProduct           | 1    | Index    | Index för sträng beskrivning som beskriver produkten |
| 16     | iSerialNumbe       | 1    | Index    | Index för sträng beskrivning som beskriver enhetens serie nummer |
| 17     | bNumConfigurations | 1    | Antal   | Antal möjliga konfigurationer |

USBX definierar en USB-enhets Beskrivning enligt följande:

```c
typedef struct UX_DEVICE_DESCRIPTOR_STRUCT
{
    UINT      bLength;
    UINT      bDescriptorType;
    USHORT    bcdUSB;
    UINT      bDeviceClass;
    UINT      bDeviceSubClass;
    UINT      bDeviceProtocol;
    UINT      bMaxPacketSize0;
    USHORT    idVendor;
    USHORT    idProduct;
    USHORT    bcdDevice;
    UINT      iManufacturer;
    UINT      iProduct;
    UINT      iSerialNumber;
    UINT      bNumConfigurations;
} UX_DEVICE_DESCRIPTOR;
```

Beskrivningen av USB-enheten är en del av en enhets behållare som beskrivs som:

```c
typedef struct UX_DEVICE_STRUCT
{
    ULONG ux_device_handle;
    ULONG ux_device_type;
    ULONG ux_device_state;
    ULONG ux_device_address;
    ULONG ux_device_speed;
    ULONG ux_device_port_location;
    ULONG ux_device_max_power;
    ULONG ux_device_power_source;
    UINT ux_device_current_configuration;

    TX_SEMAPHORE ux_device_protection_semaphore;
    struct UX_DEVICE_STRUCT *ux_device_parent; 
    struct UX_HOST_CLASS_STRUCT *ux_device_class; 
    VOID *ux_device_class_instance;
    struct UX_HCD_STRUCT *ux_device_hcd;
    struct UX_CONFIGURATION_STRUCT *ux_device_first_configuration; 
    struct UX_DEVICE_STRUCT *ux_device_next_device;
    struct UX_DEVICE_DESCRIPTOR_STRUCT ux_device_descriptor;
    struct UX_ENDPOINT_STRUCT ux_device_control_endpoint;
    struct UX_HUB_TT_STRUCT ux_device_hub_tt[UX_MAX_TT];
} UX_DEVICE;
```

- **ux_device_handle**: hantering av enheten. Detta är vanligt vis adressen till instansen för den här strukturen för enheten.
- **ux_device_type**: föråldrat värde. Outnyttja.
- **ux_device_state**: enhets tillstånd, som kan ha ett av följande värden:
    - **UX_DEVICE_RESET**                0
    - **UX_DEVICE_ATTACHED**             1
    - **UX_DEVICE_ADDRESSED**            2
    - **UX_DEVICE_CONFIGURED**           3
    - **UX_DEVICE_SUSPENDED**            4
    - **UX_DEVICE_RESUMED**              5
    - **UX_DEVICE_SELF_POWERED_STATE**   6
    - **UX_DEVICE_SELF_POWERED_STATE**   7
    - **UX_DEVICE_REMOTE_WAKEUP**        8
    - **UX_DEVICE_BUS_RESET_COMPLETED**  9
    - **UX_DEVICE_REMOVED**              10
    - **UX_DEVICE_FORCE_DISCONNECT**     11
- **ux_device_address**: enhetens adress efter att kommandot **SET_ADDRESS** har godkänts (från 1 till 127).
- **ux_device_speed**: enhetens hastighet:
    - **UX_LOW_SPEED_DEVICE**      0
    - **UX_FULL_SPEED_DEVICE**     1
    - **UX_HIGH_SPEED_DEVICE**     2
- **ux_device_port_location**: index för den överordnade enhetens port (rotnavet eller hubb).
- **ux_device_max_power**: maximal effekt i ma som enheten kan ta i den valda konfigurationen.
- **ux_device_power_source**: kan vara ett av följande två värden:
    - **UX_DEVICE_BUS_POWERED**     1
    - **UX_DEVICE_SELF_POWERED**    2
- **ux_device_current_configuration**: index för den aktuella konfigurationen som används av den här enheten.
- **ux_device_parent**: enhets container pekare för den överordnade enheten. Om pekaren är null är den överordnade roten i kontrollanten.
- **ux_device_class**: pekar mot den typ av klass som äger den här enheten.
- **ux_device_class_instance**: pekar mot instansen av klassen som äger den här enheten.
- **ux_device_hcd**: USB-styrenhetens instans där den här enheten är ansluten.
- **ux_device_first_configuration**: pekar på den första konfigurations behållaren för den här enheten.
- **ux_device_next_device**: pekar på nästa enhet i enhets listan på någon av de bussar som identifieras av USBX.
- **ux_device_descriptor**: USB-enhets beskrivning.
- **ux_device_control_endpoint**: Beskrivning av den standard kontroll slut punkt som används av enheten.
- **ux_device_hub_tt**: matris med hubb-TTS för enheten

### <a name="configuration-descriptors"></a>Konfigurations beskrivningar

Konfigurations beskrivningen beskriver information om en speciell enhets konfiguration. En USB-enhet kan innehålla en eller flera konfigurations beskrivningar. Fältet **bNumConfigurations** i enhets beskrivningen anger antalet konfigurations beskrivningar. Beskrivningen innehåller ett **bConfigurationValue** -fält med ett värde som, när den används som en parameter i den angivna konfigurationen, gör att enheten antar den beskrivna konfigurationen.

Beskrivningen beskriver antalet gränssnitt som tillhandahålls av konfigurationen. Varje gränssnitt representerar en logisk funktion i enheten och kan fungera oberoende av varandra. Till exempel kan en USB-ljudhögtalare ha tre gränssnitt, ett för ljud uppspelning, en för ljud kontroll och ett HID-gränssnitt för att hantera högtalarenas knappar.

När värden utfärdar en GET_DESCRIPTOR begäran för konfigurations beskrivningen returneras alla relaterade gränssnitt och slut punkts beskrivningar.

| Offset | Fält               | Storlek | Värde    | Beskrivning                       |
| ------ | ------------------- | ---- | -------- | --------------------------------- |
| 0      | bLength             | 1    | Antal   | Storlek på den här beskrivningen i byte. |
| 1      | bDescriptorType     | 1    | Konstant | KONFIGURATION                     |
| 2      | wTotalLength        | 2    | Antal   | Total längd på data som returneras för den här konfigurationen. Innehåller den sammanlagda längden på alla beskrivningar (konfiguration, gränssnitt, slut punkt och klass eller leverantörsspecifik) som returneras för den här konfigurationen. |
| 4      | bNumInterfaces      | 1    | Antal   | Antalet gränssnitt som stöds av den här konfigurationen. |
| 5      | bConfigurationValue | 1    | Antal   | Värde som ska användas som argument för att ange<br/>Konfiguration för att välja den här konfigurationen. |
| 6      | iConfiguration      | 1    | Index    | Index för sträng beskrivning som beskriver den här konfigurationen. |
| 7      | bMAttributes        | 1    | Bitmappsfilen   | Konfigurations egenskaper D7 Bus Powered<br />D6, egen strömförsörjning<br />Fjärraktivering av D5<br />D4.. 0 reserverad (Återställ till 0)<br />En enhets konfiguration som använder ström från bussen och en lokal källa anger både D7 och D6. Den faktiska ström källan vid körning kan fastställas med hjälp av enhets förfrågan för att hämta status.<br />Om en enhets konfiguration har stöd för fjärraktivering, anges D5 till 1. |
| 8      | MaxPower            | 1    | &       | Maximal energi förbrukning av USB-enhet från bussen i denna speciella konfiguration när enheten är fullt fungerande.<br />Uttryckt i 2 mA-enheter (t. ex. 50 = 100 mA).<br />Obs! en enhets konfiguration rapporterar om konfigurationen är buss driven eller med egen strömförsörjning.<br />Enhets status rapporterar om enheten för närvarande är självständig. Om en enhet är frånkopplad från den externa ström källan uppdaterar den enhets statusen för att indikera att den inte längre är självständiga. |

USBX definierar en beskrivning av en USB-konfiguration enligt följande.

```c
typedef struct UX_CONFIGURATION_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT wTotalLength;
    UINT bNumInterfaces;
    UINT bConfigurationValue;
    UINT iConfiguration;
    UINT bmAttributes;
    UINT MaxPower;
} UX_CONFIGURATION_DESCRIPTOR;
```

Beskrivningen av USB-konfigurationen är en del av en konfigurations behållare som beskrivs nedan.

```c
typedef struct UX_CONFIGURATION_STRUCT
{
    ULONG ux_configuration_handle;
    ULONG ux_configuration_state;
    struct UX_CONFIGURATION_DESCRIPTOR_STRUCT ux_configuration_descriptor;
    struct UX_INTERFACE_STRUCT *ux_configuration_first_interface;
    struct UX_CONFIGURATION_STRUCT *ux_configuration_next_configuration;
    struct UX_DEVICE_STRUCT *ux_configuration_device;
} UX_CONFIGURATION;
```

- **ux_configuration_handle**: hantering av konfigurationen. Detta är vanligt vis adressen till instansen för den här strukturen för konfigurationen.
- **ux_configuration_state**: konfigurationens tillstånd.
- **ux_configuration_descriptor**: USB-enhets beskrivning.
- **ux_configuration_first_interface**: pekar mot det första gränssnittet för den här konfigurationen.
- **ux_configuration_next_configuration**: pekar mot nästa konfiguration för samma enhet.
- **ux_configuration_device**: pekar mot enhetens ägare av den här konfigurationen.

### <a name="interface-descriptors"></a>Gränssnitts beskrivningar

Gränssnitts beskrivningen beskriver ett speciellt gränssnitt i en konfiguration. Ett gränssnitt är en logisk funktion i en USB-enhet. En konfiguration tillhandahåller ett eller flera gränssnitt, var och en med noll eller fler slut punkts beskrivningar som beskriver en unik uppsättning slut punkter i konfigurationen. När en konfiguration stöder fler än ett gränssnitt följer slut punkts beskrivarna för ett visst gränssnitt gränssnitts beskrivningen i de data som returneras av **GET_DESCRIPTOR** begäran för den angivna konfigurationen.

En gränssnitts Beskrivning returneras alltid som en del av en konfigurations beskrivning. En gränssnitts beskrivning kan inte nås direkt av en GET_DESCRIPTOR begäran.

Ett gränssnitt kan innehålla alternativa inställningar som gör att slut punkterna och/eller deras egenskaper kan variera efter att enheten har kon figurer ATS. Standardvärdet för ett gränssnitt är alltid alternativ noll. En klass kan välja att ändra den aktuella alternativa inställningen för att ändra gränssnittets beteende och egenskaperna för de associerade slut punkterna. SET_INTERFACE förfrågan används för att välja en alternativ inställning eller för att återgå till standardvärdet.

Med alternativa inställningar kan en del av enhets konfigurationen variera medan andra gränssnitt är i drift. Om en konfiguration har alternativa inställningar för ett eller flera av dess gränssnitt, ingår en separat gränssnitts beskrivning och dess associerade slut punkter för varje inställning.

Om en enhets konfiguration innehåller ett enda gränssnitt med två alternativa inställningar, returnerar GET_DESCRIPTOR begäran för konfigurationen konfigurations beskrivningen, sedan gränssnitts beskrivningen med fälten **bInterfaceNumber** och **bAlternateSetting** inställd på noll och sedan slut punkts Descriptor för den inställningen följt av en annan gränssnitts beskrivning och dess associerade slut punkts beskrivningar. Den andra gränssnitts beskrivningens **bInterfaceNumber** -fält skulle också anges till noll, men fältet **bAlternateSetting** för den andra gränssnitts beskrivningen skulle anges till 1 som anger att den här alternativa inställningen tillhör det första gränssnittet.

Ett gränssnitt kanske inte har några kopplade slut punkter, i vilket fallet är det bara standard kontroll punkten som är giltig för det gränssnittet.

Alternativa inställningar används huvudsakligen för att ändra den begärda bandbredden för periodiska slut punkter som är kopplade till gränssnittet. Till exempel bör ett Stream-gränssnitt för USB-högtalare ha den första alternativa inställningen med 0 bandbredds krav på den isokrona slut punkten. Andra alternativa inställningar kan välja olika bandbredds krav beroende på hur ofta ljudet strömmas.

Gränssnittets USB-beskrivning är följande:

| Offset | Fält              | Storlek | Värde     | Script                              |
| ------ | ------------------ | ---- | --------- | --------------------------------------- |
| 0      | bLength            | 1    | Antal    | Storlek på den här beskrivningen i byte.       |
| 1      | bDescriptorType    | 1    | Konstant  | Typ av GRÄNSSNITTs Beskrivning               |
| 2      | bInterfaceNumber   | 1    | Antal    | Antal gränssnitt. Nollbaserat värde som identifierar indexet i matrisen med samtidiga gränssnitt som stöds av den här konfigurationen. |
| 3      | bAltenateSetting   | 1    | Antal    | Värde som används för att välja alternativ inställning för gränssnittet som identifierades i föregående fält. |
| 4      | bNumEndpoints      | 1    | Antal    | Antal slut punkter som används av det här gränssnittet (exklusive slut punkten noll). Om värdet är 0, använder det här gränssnittet bara slut punkt noll. |
| 5      | bInterfaceClass    | 1    | Klass     | Klass kod (tilldelad av USB)<br />Om det här fältet återställs till 0, tillhör inte gränssnittet någon enhets klass som har angetts för USB.<br />Om det här fältet är inställt på 0xFF, är gränssnitts klassen leverantörsspecifik.<br />Alla andra värden är reserverade för tilldelning av USB. |
| 6      | bInterfaceSubClass | 1    | Underklass  | Underklassens kod (tilldelad av USB).<br />Dessa koder är kvalificerade med värdet för fältet bInterfaceClass. Om fältet bInterfaceClass återställs till 0 måste det här fältet också återställas till 0. Om fältet bInterfaceClass inte är inställt på 0xFF, är alla värden reserverade för tilldelning av USB. |
| 7      | bInterfaceProtocol | 1    | Protokoll  | Protokoll kod (tilldelad av USB). Dessa koder kvalificeras av värdet för bInterfaceClass och bInterfaceSubClass-fälten. Om ett gränssnitt stöder landsspecifika begär Anden identifierar den här koden de protokoll som enheten använder enligt specifikationen i enhets klassen.<br />Om det här fältet återställs till 0 använder enheten inte något klass protokoll i det här gränssnittet. Om det här fältet är inställt på 0xFF använder enheten ett leverantörsspecifika protokoll för det här gränssnittet. |
| 8      | iInterface         | 1    | Index     | Index för sträng beskrivning som beskriver det här gränssnittet. |

USBX definierar en USB-gränssnitts beskrivning på följande sätt.

```c
typedef struct UX_INTERFACE_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    UINT bInterfaceNumber;
    UINT bAlternateSetting;
    UINT bNumEndpoints;
    UINT bInterfaceClass
    UINT bInterfaceSubClass;
    UINT bInterfaceProtocol;
    UINT iInterface;
} UX_INTERFACE_DESCRIPTOR;
```

USB-gränssnittets beskrivning är en del av en gränssnitts behållare som beskrivs på följande sätt.

```c
typedef struct UX_INTERFACE_STRUCT
{
    ULONG ux_interface_handle;
    ULONG ux_interface_state;
    ULONG ux_interface_current_alternate_setting;
    struct UX_INTERFACE_DESCRIPTOR_STRUCT ux_interface_descriptor;
    struct UX_HOST_CLASS_STRUCT    *ux_interface_class;
    VOID    *ux_interface_class_instance;
    struct UX_ENDPOINT_STRUCT    *ux_interface_first_endpoint;
    struct UX_INTERFACE_STRUCT    *ux_interface_next_interface;
    struct UX_CONFIGURATION_STRUCT    *ux_interface_configuration;
} UX_INTERFACE;
```

- **ux_interface_handle**: referens för gränssnittet. Detta är vanligt vis adressen till instansen av den här strukturen för gränssnittet.
- **ux_interface_state**: gränssnittets tillstånd.
- **ux_interface_descriptor**: USB-gränssnittets beskrivning.
- **ux_interface_class**: pekar mot den klass typ som äger det här gränssnittet.
- **ux_interface_class_instance**: pekar mot instansen av klassen som äger det här gränssnittet.
- **ux_interface_first_endpoint**: pekar mot den första slut punkten som har registrerats med det här gränssnittet.
- **ux_interface_next_interface**: pekar mot nästa gränssnitt som är associerat med konfigurationen.
- **ux_interface_configuration**: pekar mot konfigurations ägaren för det här gränssnittet.

### <a name="endpoint-descriptors"></a>Slut punkts beskrivningar

Varje slut punkt som är associerad med ett gränssnitt har sin egen slut punkts beskrivning. Den här beskrivningen innehåller den information som krävs av värd stacken för att fastställa bandbredds kraven för varje slut punkt, maximal nytto last som är associerad med slut punkten, dess periodicitet och dess riktning. En slut punkts Beskrivning returneras alltid av ett GET_DESCRIPTOR-kommando för konfigurationen.

Standard kontroll punkten som är associerad med enhets beskrivningen räknas inte som en del av slut punkten (erna) som är associerad med gränssnittet och som därför inte returneras i den här beskrivningen.

När värd program varan begär en ändring av den alternativa inställningen för ett gränssnitt, ändras alla associerade slut punkter och deras USB-resurser enligt den nya alternativa inställningen.

Förutom standard kontroll slut punkter kan slut punkter inte dela mellan gränssnitt.

| Offset | Fält            | Storlek | Värde    | Beskrivning                       |
| ------ | ---------------- | ---- | -------- | --------------------------------- |
| 0      | bLength          | 1    | Antal   | Storlek på den här beskrivningen i byte. |
| 1      | bDescriptorType  | 1    | Konstant | Typ av slut PUNKTs beskrivning. |
| 2      | bEndpointAddress | 1    | Slutpunkt | Adressen till slut punkten på USB-enheten som beskrivs i den här beskrivningen. Adressen kodas enligt följande:<br />Bit 3... 0: slut punkts numret<br />Bit 6... 4: reserverad, Återställ till noll<br />Bit 7: Direction, ignoreras för kontroll slut punkter<br />0 = slut punkt<br />1 = i slut punkt |
| 3      | bmAttributes     | 1    | Bitmappsfilen   | I det här fältet beskrivs slutpunktens attribut när den konfigureras med hjälp av fältet **bConfigurationValue** . Bitar 1.. 0: överförings typ<br />00 = kontroll<br />01 = isokrona<br />10 = Mass<br />11 = avbrott<br />Om inte en isokrona slut punkt är BITS 5.. 2 reserverade och måste anges till noll. Om den är isokrona definieras de enligt följande:<br />BITS 3.. 2: typ av synkronisering<br />00 = ingen synkronisering<br />01 = asynkron<br />10 = adaptiv<br />11 = synkron<br />BITS 5.. 4: användnings typ<br />00 = data slut punkt<br />01 = feedback-slutpunkt<br />10 = slut punkt för implicit feedback-data<br />11 = reserverad |
| 4      | wMaxPacketSize   | 2    | Antal   | Maximal paket storlek den här slut punkten kan skicka eller ta emot när den här konfigurationen är vald.<br />För isokrona slut punkter används det här värdet för att reservera buss tiden i schemat, vilket krävs för data nytto lasterna per-(Micro). Denna pipe kan regelbundet använda mindre bandbredd än den reserverade. Enheten rapporterar vid behov den faktiska bandbredden som används via dess normala, icke-USB-definierade mekanismer.<br />För alla slut punkter anger BITS 10.. 0 den maximala paket storleken (i byte).<br />För höghastighets isokrona och avbrotts slut punkter:<br />BITS 12.. 11 Ange antalet ytterligare transaktions möjligheter per mikroram: 00 = ingen (1 transaktion per mikroram)<br />01 = 1 ytterligare (2 per mikroram)<br />10 = 2 ytterligare (3 per mikrobild)<br />11 = reserverad<br />Bitarna 15.. 13 är reserverade och måste anges till noll. |
| 6      | bInterval        | 1     | Antal   | Nummer intervall för avsöknings slut punkt för data överföringar.<br />Uttrycks i ramar eller mikrobild rutor beroende på enhetens drifts hastighet (t. ex. 1 millisekund eller 125 μs-enheter).<br />För fullständig/High-Speed isokrona slut punkter måste det här värdet vara i intervallet från 1 till 16. **BInterval** används som exponent för ett 2bInterval-1-värde. t. ex. är **bInterval** 4 en period på 8 (24-1).<br />Värdet för det här fältet kan vara mellan 1 och 255 för avbrotts slut punkter med fullständig/Low-Speed.<br />För snabba avbrotts slut punkter används **bInterval** som exponent för ett 2bInterval-1-värde. t. ex. är **bInterval** 4 en period på 8 (24-1). Värdet måste vara mellan 1 och 16.<br />För Mass-och kontroll slut punkter med hög hastighet anger **bInterval** den maximala NAK-frekvensen för slut punkten. Värdet 0 anger att slut punkten aldrig NAKs. Andra värden anger högst en NAK varje **bInterval** för mikrobild rutor.<br />Värdet måste vara mellan 0 och 255. |

USBX definierar en identifierare för USB-slutpunkten enligt följande:

```c
typedef struct UX_ENDPOINT_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    UINT bEndpointAddress;
    UINT bmAttributes;
    USHORT wMaxPacketSize;
    UINT bInterval;
} UX_ENDPOINT_DESCRIPTOR;
```

USB-slutpunktens beskrivning är en del av en slut punkts behållare, som beskrivs nedan.

```c
typedef struct UX_ENDPOINT_STRUCT {
    ULONG    ux_endpoint_handle;
    ULONG    ux_endpoint_state;
    VOID    *ux_endpoint_ed;
    struct UX_ENDPOINT_DESCRIPTOR_STRUCT    ux_endpoint_descriptor;
    struct UX_ENDPOINT_STRUCT    *ux_endpoint_next_endpoint;
    struct UX_INTERFACE_STRUCT    *ux_endpoint_interface;
    struct UX_DEVICE_STRUCT    *ux_endpoint_device;
    struct UX_TRANSFER REQUEST_STRUCT    ux_endpoint_transfer request;
} UX_ENDPOINT;

```

- **ux_endpoint_handle**: referens för slut punkten. Detta är vanligt vis adressen till instansen för den här strukturen för slut punkten.
- **ux_endpoint_state**: tillstånd för slut punkten.
- **ux_endpoint_ed**: pekar mot den fysiska slut punkten på värd styrenhets skiktet.
- **ux_endpoint_descriptor**: USB-slutpunktens beskrivning.
- **ux_endpoint_next_endpoint**: pekar mot nästa slut punkt som tillhör samma gränssnitt.
- **ux_endpoint_interface**: pekar mot gränssnittet som äger det här slut punkts gränssnittet.
- **ux_endpoint_device**: pekar mot behållaren för överordnad enhet.
- **ux_endpoint_transfer begäran**: begäran om USB-överföring som används för att skicka/ta emot data från till/från enheten.

### <a name="string-descriptors"></a>Sträng beskrivningar

Sträng beskrivningar är valfria. Om en enhet inte stöder sträng beskrivningar måste alla referenser till sträng beskrivningar i enhets-, konfigurations-och gränssnitts beskrivningar återställas till noll.

Sträng beskrivningar använder UNICODE-kodning, vilket ger stöd för flera teckenuppsättningar. Strängarna i en USB-enhet kan ha stöd för flera språk. När en sträng Beskrivning begärs anger beställaren det önskade språket med ett språk-ID som definieras av USB-IF. Listan över för närvarande definierade USB-LANGIDs finns i USBX-tillägget??.
Sträng index noll för alla språk returnerar en sträng beskrivning som innehåller en matris med två bytes LANGID-koder som stöds av enheten. Det bör noteras att UNICODE-strängen inte är 0 avslutad. I stället beräknas storleken på sträng mat ris genom att subtrahera två från storleken på matrisen som finns i den första byten av beskrivningen.

USB-sträng beskrivningen 0 kodas enligt följande.

| Offset | Fält           | Storlek | Värde    | Beskrivning                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | N + 2      | Storlek på den här beskrivningen i byte |
| 1      | bDescriptorType | 1    | Konstant | STRÄNG beskrivnings typ           |
| 2      | wLANGID [0]      | 2    | Antal   | LANGID-kod 0                    |
| ...    | ...]            | ...  | ...      | ...                              |
| N      | wLANGID [n]      | 2    | Antal   | LANGID-kod n                    |

Andra USB-strängar är kodade enligt följande.

| Offset | Fält           | Storlek | Värde    | Beskrivning                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | Antal   | Storlek på den här beskrivningen i byte |
| 1      | bDescriptorType | 1    | Konstant | STRÄNG beskrivnings typ           |
| 2      | bString         | n    | Antal   | UNICODE-kodad sträng           |

USBX definierar en USB-sträng med nollängd som inte är noll enligt följande:

```c
typedef struct UX_STRING_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT bString[1];
} UX_STRING_DESCRIPTOR;
```

### <a name="functional-descriptors"></a>Funktionella beskrivare

Funktionella beskrivningar kallas även för klassbaserade beskrivningar. De använder normalt samma grundläggande strukturer som allmänna beskrivningar och gör att ytterligare information kan vara tillgänglig för klassen. Om t. ex. USB-ljudhögtalart är fallet tillåter klassbaserade beskrivningar ljud klassen att hämta för varje alternativ inställning vilken typ av ljud frekvens som stöds.

### <a name="usbx-device-descriptor-framework-in-memory"></a>Ramverk för USBX Device Descriptor i minnet

USBX hanterar de flesta enhets beskrivningar i minnet, det vill säga alla beskrivare förutom strängen och funktions beskrivare. Följande diagram visar hur dessa beskrivningar lagras och är relaterade.

![Ramverk för USBX Device Descriptor i minnet](./media/usbx-host-stack/usbx-device-descriptor-framework.png)
