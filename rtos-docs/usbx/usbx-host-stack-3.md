---
title: Kapitel 3 – Funktionella komponenter i USBX-värdstack
description: Det här kapitlet innehåller en beskrivning av usbx-inbäddad USB-värdstack med höga prestanda ur ett funktionellt perspektiv.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a3cbbb2e26d66d3db26144a47a1b6cbb11387c7b5b2ba5e19d35df026e5e3598
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790933"
---
# <a name="chapter-3---functional-components-of-usbx-host-stack"></a>Kapitel 3 – Funktionella komponenter i USBX-värdstack

Det här kapitlet innehåller en beskrivning av usbx-inbäddad USB-värdstack med höga prestanda ur ett funktionellt perspektiv.

## <a name="execution-overview"></a>Körningsöversikt

USBX består av flera komponenter:

- Initiering
- Anrop till programgränssnitt
- Rothubb
- Hubbklass
- Värdklasser
- USB-värdstack
- Värdstyrenhet

Följande diagram illustrerar USBX-värdstacken.

![USBX-värdstack](./media/usbx-host-stack/usbx-host-stack.png)

### <a name="initialization"></a>Initiering

För att kunna aktivera USBX måste funktionen ***ux_system_initialize*** anropas. Den här funktionen initierar minnesresurserna för USBX.

För att kunna aktivera USBX-värdresurser måste ***funktionen ux_host_stack_initialize*** anropas. Den här funktionen initierar i sin tur alla resurser som används av USBX-värdstacken, till exempel ThreadX-trådar, mutexes och semaforer.

Det är upp till programmets initiering att aktivera minst en USB-värdstyrenhet och en eller flera USB-klasser. När klasserna har registrerats i stacken och initieringsfunktionen för värdstyrenheter har anropats är buss aktiv och enhetsidentifiering kan starta. Om värdstyrenhetens rothubb identifierar en ansluten enhet aktiveras USB-uppräkningstråden, som ansvarar för USB-topologin, och fortsätter att räkna upp enheter.

På grund av rothubbens och nedströmshubbens natur är det möjligt att alla anslutna USB-enheter kanske inte har konfigurerats helt när initieringsfunktionen för värdstyrenheten returnerar. Det kan ta flera sekunder att räkna upp alla USB-enheter, särskilt om det finns en eller flera hubbar mellan rothubben och USB-enheter.

### <a name="application-interface-calls"></a>Anrop till programgränssnitt

Det finns två nivåer av API:er i USBX.

- API:er för USB-värdstack
- API:er för USB-värdklass

Normalt bör ett USBX-program inte behöva anropa någon av API-funktionerna för USB-värdstacken. De flesta program har endast åtkomst till USB-klass-API-funktionerna.

### <a name="usb-host-stack-apis"></a>API:er för USB-värdstack

API-funktionerna i värdstacken ansvarar för registrering av USBX-komponenter (värdklasser och värdstyrenheter), konfiguration av enheter och överföringsbegäranden för tillgängliga enhetsslutpunkter.

### <a name="usb-host-class-api"></a>API för USB-värdklass

Klass-API:erna är mycket specifika för varje USB-klass. De flesta vanliga API-funktioner för USB-klasser tillhandahåller tjänster som att öppna/stänga en enhet och läsa från och skriva till en enhet.

### <a name="root-hub"></a>Rothubb

Varje värdstyrenhetsinstans har en eller flera USB-rothubar. Antalet rothubar bestäms antingen av kontrollantens typ eller kan hämtas genom läsning av specifika register från kontrollanten.

### <a name="hub-class"></a>Hubbklass

Hubbklassen ansvarar för att köra USB-hubbar. En USB-hubb kan antingen vara en fristående hubb eller som en del av en sammansatt enhet, till exempel ett tangentbord eller en bildskärm. En hubb kan vara självförsörjande eller bussdriven. Bussdrivna hubbar har högst fyra underordnade portar och kan endast tillåta anslutning av enheter som antingen är självdrivna eller bussdrivna enheter som använder mindre än 100 mA ström. Hubbar kan kaskadas. Upp till fem hubbar kan anslutas till varandra.

### <a name="usb-host-stack"></a>USB-värdstack

USB-värdstacken är mitten av USBX. Den har tre huvudfunktioner.

- Hantera USB-topologin.
- Binda en USB-enhet till en eller flera klasser.
- Ange ett API för klasser för att utföra enhetsbeskrivningsförfråga och USB-överföringar.

### <a name="topology-manager"></a>Topologihanterare

Topologitråden i USB-stacken väcks när en ny enhet är ansluten eller när en enhet har kopplats från. Rothubben eller en vanlig hubb kan acceptera enhetsanslutningar. När en enhet har anslutits till USB-enheten hämtar topologihanteraren enhetsbeskrivningen. Den här beskrivningen innehåller antalet möjliga konfigurationer som är tillgängliga för den här enheten. De flesta enheter har endast en konfiguration. Vissa enheter kan fungera på olika sätt beroende på tillgänglig ström på porten där den är ansluten. Om så är fallet har enheten flera konfigurationer som kan väljas beroende på den tillgängliga kraften. När enheten har konfigurerats av topologihanteraren kan den sedan dra den mängd ström som anges i dess konfigurationsbeskrivning.

## <a name="usb-class-binding"></a>USB-klassbindning

När enheten har konfigurerats låter topologihanteraren klasshanteraren fortsätta identifieringen av enheten genom att titta på enhetsgränssnittsbeskrivningarna. En enhet kan ha en eller flera gränssnittsbeskrivningar.

Ett gränssnitt representerar en funktion i en enhet. En USB-talare har till exempel tre gränssnitt, ett för ljuduppspelning, ett för ljudkontroll och ett för att hantera de olika talarknapparna.

Klasshanteraren har två metoder för att ansluta enhetsgränssnitten till en eller flera klasser. Den kan antingen använda en kombination av en PID/VID (produkt-ID och leverantörs-ID) som finns i gränssnittsbeskrivningen eller en kombination av klass/underklass/protokoll.

KOMBINATIONEN PID/VID är giltig för gränssnitt som inte kan drivas av en generisk klass. Kombinationen Klass/Underklass/Protokoll används av gränssnitt som tillhör en USB-IF-certifierad klass, till exempel en skrivare, hubb, lagring, ljud eller HID.

Klasshanteraren innehåller en lista över registrerade klasser från initieringen av USBX. Klasshanteraren anropar varje klass en i taget tills en klass accepterar att hantera gränssnittet för den enheten. En klass kan bara hantera ett gränssnitt. I exemplet med USB-ljudhögtalaren anropar klasshanteraren alla klasser för vart och ett av gränssnitten.

När en klass accepterar ett gränssnitt skapas en ny instans av klassen. Klasshanteraren söker sedan efter den alternativa standardinställningen för gränssnittet. En enhet kan ha en eller flera alternativa inställningar för varje gränssnitt. Den alternativa inställningen 0 används som standard tills en klass bestämmer sig för att ändra den.

För den alternativa standardinställningen monterar klasshanteraren alla slutpunkter som finns i den alternativa inställningen. Om monteringen av varje slutpunkt lyckas slutför klasshanteraren sitt jobb genom att gå tillbaka till den klass som slutför initieringen av gränssnittet.

### <a name="usbx-apis"></a>USBX-API:er

USB-stacken exporterar ett visst antal API:er för USB-klasserna för att utföra frågor på enheten och USB-överföringar på specifika slutpunkter. Dessa API-funktioner beskrivs i detalj i den här referenshandboken.

### <a name="host-controller"></a>Värdstyrenhet

Värdstyrenhetsdrivrutinen ansvarar för att köra en specifik typ av USB-styrenhet. En USB-värdstyrenhet kan ha flera styrenheter inuti. Till exempel innehåller vissa Intel PC-kretsuppsättning tvåSTYRENHETskontrollanter. Vissa USB 2.0-styrenheter innehåller flera instanser av en OHCI-styrenhet utöver en instans avSTYRENHETEN.

Värdstyrenheten hanterar endast flera instanser av samma styrenhet. För att kunna köra de flesta USB 2.0-värdstyrenheter måste du initiera både OCHI-styrenheten och YECI-styrenheten under initieringen av USBX.

Värdstyrenheten ansvarar för att hantera följande.

- Rothubb
- Energisparfunktioner
- Slutpunkter
- Överföringar

### <a name="root-hub"></a>Rothubb

Rothubbens hantering ansvarar för att driva varje styrenhetsport och avgöra om det finns en enhet i eller inte. Den här funktionen används av den allmänna USBX-rothubben för att fråga styrenhetens underordnade portar.

### <a name="power-management"></a>Energisparfunktioner

Energisparfunktionerna möjliggör hantering av paus-/återupptagningssignaler antingen i gruppläge, vilket påverkar alla underordnade styrenhetsportar på samma gång eller individuellt om kontrollanten erbjuder den här funktionen.

### <a name="endpoints"></a>Slutpunkter

Slutpunktshanteringen möjliggör skapande eller destruktion av fysiska slutpunkter till kontrollanten. De fysiska slutpunkterna är minnesentiteter som parsas av kontrollanten om kontrollanten stöder huvud-DMA eller som är skrivna i kontrollanten. De fysiska slutpunkterna innehåller transaktionsinformation som ska utföras av kontrollanten.

### <a name="transfers"></a>Överföringar

Överföringshanteringen tillhandahåller en klass för att utföra en transaktion på var och en av de slutpunkter som har skapats. Varje logisk slutpunkt innehåller en komponent som kallas ÖVERFÖRINGSBEGÄRAN FÖR USB-överföringsbegäranden. ÖVERFÖRINGSBEGÄRAN används av stacken för att beskriva transaktionen. Denna ÖVERFÖRINGSBEGÄRAN skickas sedan till stacken och till kontrollanten, som kan dela upp den i flera undertransaktioner beroende på kontrollantens funktioner.

## <a name="usb-device-framework"></a>USB-enhetsramverk

En USB-enhet representeras av ett träd med beskrivningar. Det finns sex huvudtyper av beskrivningar.

- Enhetsbeskrivningar
- Konfigurationsbeskrivningar
- Gränssnittsbeskrivningar
- Slutpunktsbeskrivningar
- Strängbeskrivningar
- Funktionella beskrivningar

En USB-enhet kan ha en mycket enkel beskrivning och ser ut så här.
![Enkel USB-enhet](./media/usbx-host-stack/usb-device-simple.png)

I bilden ovan har enheten bara en konfiguration. Ett enda gränssnitt är kopplat till den här konfigurationen, vilket anger att enheten bara har en funktion och endast en slutpunkt. Ansluten till enhetsbeskrivningen är en strängbeskrivning som ger en synlig identifiering av enheten.

En enhet kan dock vara mer komplex och kan visas på följande sätt.

![Komplex USB-enhet](./media/usbx-host-stack/usb-device-complex.png)

I bilden ovan har enheten två konfigurationsbeskrivningar som är kopplade till enhetsbeskrivningen. Den här enheten kan indikera att den har två energilägen eller kan köras av antingen standardklasser eller tillverkarspecifika klasser.

Kopplade till den första konfigurationen är två gränssnitt som anger att enheten har två logiska funktioner. Den första funktionen har 3 slutpunktsbeskrivningar och en funktionell beskrivning. Den funktionella beskrivningen kan användas av den klass som ansvarar för att driva gränssnittet för att få ytterligare information om det här gränssnittet som normalt inte hittas av en allmän beskrivning.

### <a name="device-descriptors"></a>Enhetsbeskrivningar

Varje USB-enhet har en enda enhetsbeskrivning. Den här beskrivningen innehåller enhetsidentifiering, antalet konfigurationer som stöds och egenskaperna för den standardkontrollslutpunkt som används för att konfigurera enheten.

| Offset | Fält              | Storlek | Värde    | Beskrivning                             |
| ------ | ------------------ | ---- | -------- | --------------------------------------- |
| 0      | BLength            | 1    | Antal   | Storleken på den här beskrivningen i byte |
| 1      | bDescriptorType    | 1    | Konstant | Enhetsbeskrivningstyp |
| 2      | bcdUSB             | 2    | Bcd      | USB-specifikationsnumret i binärkodad dec<br />Exempel: 2.10 motsvarar 0x210. Det här fältet identifierar versionen av USB-specifikationen som enheten och dess beskrivningar är kompatibla med. |
| 4      | bDeviceClass       | 1    | Klass    | Klasskod (tilldelas av USB-IF).<br />Om det här fältet återställs till 0 anger varje gränssnitt i en konfiguration sin egen klassinformation och de olika gränssnitten fungerar oberoende av varandra.<br />Om det här fältet är inställt på ett värde mellan 1 och 0xFE stöder enheten olika klassspecifikationer på olika gränssnitt och gränssnitten kanske inte fungerar oberoende av varandra. Det här värdet identifierar klassdefinitionen som används för aggregeringsgränssnitten.<br />Om det här fältet är 0xFF är enhetsklassen leverantörsspecifik. |
| 5      | bDeviceSubClass    | 1    | Underklass | Underklasskod (tilldelad av USB-IF).<br />Dessa koder kvalificeras av värdet för fältet bDeviceClass. Om fältet bDeviceClass återställs till 0 måste det här fältet också återställas till 0. Om fältet bDeviceClass inte är inställt på 0xFF är alla värden reserverade för tilldelning via USB. |
| 6      | bDeviceProtocol    | 1    | Protokoll | Protokollkod (tilldelas av USB-IF).<br />Dessa koder kvalificeras av värdet för fälten bDeviceClass och bDeviceSubClass. Om en enhet stöder klassspecifika protokoll på enhetsbasis i stället för en gränssnittsbas identifierar den här koden de protokoll som enheten använder enligt definitionen av enhetsklassens specifikation. Om det här fältet återställs till 0 använder enheten inte klassspecifika protokoll på enhetsbasis.<br />Den kan dock använda klassspecifika protokoll på gränssnittsbasis.<br />Om det här fältet är 0xFF använder enheten ett leverantörsspecifikt protokoll på enhetsbasis. |
| 7      | bMaxPacketSize0    | 1    | Antal   | Maximal paketstorlek för slutpunkt noll (endast bytestorlekar på 8, 16, 32 eller 64 är giltiga) |
| 8      | idVendor           | 2    | ID       | Leverantörs-ID (tilldelas av USB-IF) |
| 10     | idProduct          | 2    | ID       | Produkt-ID (tilldelas av tillverkaren) |
| 12     | bcdDevice          | 2    | Bcd      | Enhetens versionsnummer i binärkodad decimal |
| 14     | iManufacturer      | 1    | Index    | Index för strängbeskrivning som beskriver tillverkare |
| 15     | iProduct           | 1    | Index    | Index för strängbeskrivning som beskriver produkten |
| 16     | iSerialNumbe       | 1    | Index    | Index för strängbeskrivning som beskriver enhetens serienummer |
| 17     | bNumConfigurations | 1    | Antal   | Antal möjliga konfigurationer |

USBX definierar en USB-enhetsbeskrivning enligt följande:

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

USB-enhetsbeskrivningen är en del av en enhetscontainer som beskrivs som:

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

- **ux_device_handle:** Enhetens handtag. Det här är vanligtvis adressen till instansen av den här strukturen för enheten.
- **ux_device_type:** Inaktuellt värde. Oanvända.
- **ux_device_state:** Enhetstillstånd, som kan ha något av följande värden:
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
- **ux_device_address:** Enhetens adress efter **att SET_ADDRESS** har godkänts (från 1 till 127).
- **ux_device_speed:** Enhetens hastighet:
    - **UX_LOW_SPEED_DEVICE**      0
    - **UX_FULL_SPEED_DEVICE**     1
    - **UX_HIGH_SPEED_DEVICE**     2
- **ux_device_port_location:** Index för porten för den överordnade enheten (rothubb eller hubb).
- **ux_device_max_power:** Maximal ström i mA som enheten kan ta i den valda konfigurationen.
- **ux_device_power_source:** Kan vara något av följande två värden:
    - **UX_DEVICE_BUS_POWERED**     1
    - **UX_DEVICE_SELF_POWERED**    2
- **ux_device_current_configuration:** Index för den aktuella konfiguration som används av den här enheten.
- **ux_device_parent: Pekare** för enhetscontainer för den överordnade enheten. Om pekaren är null är den överordnade rothubben för kontrollanten.
- **ux_device_class:** Pekare till den klasstyp som äger den här enheten.
- **ux_device_class_instance:** Pekare till instansen av klassen som äger den här enheten.
- **ux_device_hcd:** USB-värdstyrenhetsinstans där den här enheten är ansluten.
- ux_device_first_configuration : **Pekare** till den första konfigurationscontainern för den här enheten.
- **ux_device_next_device:** Pekare till nästa enhet i listan över enheter på någon av de bussarna som identifieras av USBX.
- **ux_device_descriptor:** USB-enhetsbeskrivning.
- **ux_device_control_endpoint:** Beskrivning av den standardkontrollslutpunkt som används av den här enheten.
- **ux_device_hub_tt:** Matris med hubb-TT för enheten

### <a name="configuration-descriptors"></a>Konfigurationsbeskrivningar

Konfigurationsbeskrivningen beskriver information om en specifik enhetskonfiguration. En USB-enhet kan innehålla en eller flera konfigurationsbeskrivningar. Fältet **bNumConfigurations** i enhetsbeskrivningen anger antalet konfigurationsbeskrivningar. Beskrivningen innehåller ett **bConfigurationValue-fält** med ett värde som, när det används som en parameter för begäran om set-konfiguration, gör att enheten antar den beskrivna konfigurationen.

Beskrivningen beskriver antalet gränssnitt som tillhandahålls av konfigurationen. Varje gränssnitt representerar en logisk funktion på enheten och kan fungera oberoende av varandra. En USB-ljudhögtalare kan till exempel ha tre gränssnitt, ett för ljudströmning, ett för ljudkontroll och ett HID-gränssnitt för att hantera talarens knappar.

När värden utfärdar en GET_DESCRIPTOR för konfigurationsbeskrivningen returneras alla relaterade gränssnitts- och slutpunktsbeskrivningar.

| Offset | Fält               | Storlek | Värde    | Beskrivning                       |
| ------ | ------------------- | ---- | -------- | --------------------------------- |
| 0      | bLength             | 1    | Antal   | Storleken på den här beskrivningen i byte. |
| 1      | bDescriptorType     | 1    | Konstant | KONFIGURATION                     |
| 2      | wTotalLength        | 2    | Antal   | Total längd på data som returneras för den här konfigurationen. Innehåller den kombinerade längden för alla deskriptorer (konfiguration, gränssnitt, slutpunkt och klass- eller leverantörsspecifik) som returneras för den här konfigurationen. |
| 4      | bNumInterfaces      | 1    | Antal   | Antal gränssnitt som stöds av den här konfigurationen. |
| 5      | bConfigurationValue | 1    | Antal   | Värde som ska användas som argument för Set<br/>Konfiguration för att välja den här konfigurationen. |
| 6      | iConfiguration      | 1    | Index    | Index för strängbeskrivning som beskriver den här konfigurationen. |
| 7      | bMAttributes        | 1    | Bitmapp   | Konfigurationsegenskaper D7-bussdriven<br />D6 med egen strömförsörjning<br />D5 Remote Wakeup<br />D4.. 0 Reserverad (återställ till 0)<br />En enhetskonfiguration som använder ström från buss och en lokal källa anger både D7 och D6. Den faktiska strömkällan vid körning kan fastställas med hjälp av enhetsbegäran hämta status.<br />Om en enhetskonfiguration stöder fjärrvaking anges D5 till 1. |
| 8      | MaxPower            | 1    | Ma       | Maximal strömförbrukning för USB-enheter från buss i den här specifika konfigurationen när enheten är helt i drift.<br />Uttryckt i 2 mA enheter (t.ex. 50 = 100 mA).<br />Obs! En enhetskonfiguration rapporterar om konfigurationen är bussdriven eller självdriven.<br />Enhetsstatus rapporterar om enheten för närvarande är självdriven. Om en enhet kopplas bort från den externa strömkällan uppdateras enhetens status för att indikera att den inte längre är självdriven. |

USBX definierar en USB-konfigurationsbeskrivning enligt följande.

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

USB-konfigurationsbeskrivningen är en del av en konfigurationscontainer som beskrivs nedan.

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

- **ux_configuration_handle:** Referens för konfigurationen. Det här är vanligtvis adressen till instansen av den här strukturen för konfigurationen.
- **ux_configuration_state:** Konfigurationstillstånd.
- **ux_configuration_descriptor:** USB-enhetsbeskrivning.
- **ux_configuration_first_interface:** Pekare till det första gränssnittet för den här konfigurationen.
- **ux_configuration_next_configuration:** Pekaren till nästa konfiguration för samma enhet.
- **ux_configuration_device:** Pekare till enhetsägaren för den här konfigurationen.

### <a name="interface-descriptors"></a>Gränssnittsbeskrivningar

Gränssnittsbeskrivningen beskriver ett specifikt gränssnitt i en konfiguration. Ett gränssnitt är en logisk funktion i en USB-enhet. En konfiguration tillhandahåller ett eller flera gränssnitt, vart och ett med noll eller flera slutpunktsbeskrivningar som beskriver en unik uppsättning slutpunkter i konfigurationen. När en konfiguration stöder mer än ett gränssnitt följer slutpunktsbeskrivningarna för ett visst gränssnittsbeskrivningen i de data som **returneras** av GET_DESCRIPTOR begäran om den angivna konfigurationen.

En gränssnittsbeskrivning returneras alltid som en del av en konfigurationsbeskrivning. En gränssnittsbeskrivning kan inte kommas åt direkt av en GET_DESCRIPTOR begäran.

Ett gränssnitt kan innehålla alternativa inställningar som gör att slutpunkterna och/eller deras egenskaper kan variera efter att enheten har konfigurerats. Standardinställningen för ett gränssnitt är alltid alternativ inställning noll. En klass kan välja att ändra den aktuella alternativa inställningen för att ändra gränssnittsbeteendet och egenskaperna för de associerade slutpunkterna. Den SET_INTERFACE begäran används för att välja en alternativ inställning eller för att återgå till standardinställningen.

Med alternativa inställningar kan en del av enhetskonfigurationen varieras medan andra gränssnitt fortsätter att användas. Om en konfiguration har alternativa inställningar för ett eller flera av dess gränssnitt inkluderas en separat gränssnittsbeskrivning och dess associerade slutpunkter för varje inställning.

Om en enhetskonfiguration innehåller ett enda gränssnitt med två alternativa inställningar returnerar GET_DESCRIPTOR-begäran för konfigurationen konfigurationsbeskrivningen, sedan gränssnittsbeskrivningen med fälten **bInterfaceNumber** och **bAlternateSetting** inställda på noll och sedan slutpunktsbeskrivningarna för den inställningen, följt av en annan gränssnittsbeskrivning och dess associerade slutpunktsbeskrivningar. Det andra gränssnittsbeskrivningens **bInterfaceNumber-fält** skulle också anges till noll, men **fältet bAlternateSetting** i den andra gränssnittsbeskrivningen skulle anges till 1 som anger att den här alternativa inställningen tillhör det första gränssnittet.

Ett gränssnitt kanske inte har några associerade slutpunkter, vilket innebär att endast standardkontrollslutpunkten är giltig för det gränssnittet.

Alternativa inställningar används främst för att ändra den begärda bandbredden för periodiska slutpunkter som är associerade med gränssnittet. Ett USB-gränssnitt för talarströmning bör till exempel ha den första alternativa inställningen med 0 bandbreddsefterfrågan på dess isokrona slutpunkt. Andra alternativa inställningar kan välja olika bandbreddskrav beroende på ljudströmningsfrekvensen.

USB-beskrivningen för gränssnittet är följande:

| Offset | Fält              | Storlek | Värde     | Deskriptor                              |
| ------ | ------------------ | ---- | --------- | --------------------------------------- |
| 0      | bLength            | 1    | Antal    | Den här beskrivningens storlek i byte.       |
| 1      | bDescriptorType    | 1    | Konstant  | Gränssnittsbeskrivningstyp               |
| 2      | bInterfaceNumber   | 1    | Antal    | Antal gränssnitt. Nollbaserat värde som identifierar indexet i matrisen med samtidiga gränssnitt som stöds av den här konfigurationen. |
| 3      | bAltenateSetting   | 1    | Antal    | Värde som används för att välja alternativ inställning för gränssnittet som identifierats i föregående fält. |
| 4      | bNumEndpoints      | 1    | Antal    | Antal slutpunkter som används av det här gränssnittet (exklusive slutpunkt noll). Om det här värdet är 0 använder det här gränssnittet endast slutpunkt noll. |
| 5      | bInterfaceClass    | 1    | Klass     | Klasskod (tilldelad via USB)<br />Om det här fältet återställs till 0 tillhör inte gränssnittet någon USB-angiven enhetsklass.<br />Om fältet är inställt på 0xFF är gränssnittsklassen leverantörsspecifik.<br />Alla andra värden är reserverade för tilldelning via USB. |
| 6      | bInterfaceSubClass | 1    | Underklass  | Underklasskod (tilldelad via USB).<br />Dessa koder kvalificeras av värdet för fältet bInterfaceClass. Om fältet bInterfaceClass återställs till 0 måste det här fältet också återställas till 0. Om fältet bInterfaceClass inte är inställt på 0xFF, reserveras alla värden för tilldelning via USB. |
| 7      | bInterfaceProtocol | 1    | Protokoll  | Protokollkod (tilldelad via USB). Dessa koder kvalificeras av värdet för fälten bInterfaceClass och bInterfaceSubClass. Om ett gränssnitt stöder klassspecifika begäranden identifierar den här koden de protokoll som enheten använder enligt specifikationen för enhetsklassen.<br />Om det här fältet återställs till 0 använder enheten inte något klassspecifikt protokoll i det här gränssnittet. Om fältet är inställt på 0xFF använder enheten ett leverantörsspecifikt protokoll för det här gränssnittet. |
| 8      | iInterface         | 1    | Index     | Index för strängbeskrivning som beskriver det här gränssnittet. |

USBX definierar en USB-gränssnittsbeskrivning enligt följande.

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

Beskrivningen av USB-gränssnittet är en del av en gränssnittscontainer som beskrivs på följande sätt.

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

- **ux_interface_handle**: Referens för gränssnittet. Det här är vanligtvis adressen till instansen av den här strukturen för gränssnittet.
- **ux_interface_state:** Gränssnittets tillstånd.
- **ux_interface_descriptor:** USB-gränssnittsbeskrivning.
- **ux_interface_class:** Pekare till den klasstyp som äger det här gränssnittet.
- **ux_interface_class_instance:** Pekare till instansen av klassen som äger det här gränssnittet.
- **ux_interface_first_endpoint: Pekare** till den första slutpunkten som registrerats med det här gränssnittet.
- **ux_interface_next_interface:** Pekare till nästa gränssnitt som är associerat med konfigurationen.
- **ux_interface_configuration:** Pekare till konfigurationsägaren för det här gränssnittet.

### <a name="endpoint-descriptors"></a>Slutpunktsbeskrivningar

Varje slutpunkt som är associerad med ett gränssnitt har en egen slutpunktsbeskrivning. Den här beskrivningen innehåller den information som krävs av värdstacken för att fastställa bandbreddskraven för varje slutpunkt, den maximala nyttolasten som är associerad med slutpunkten, dess periodicitet och riktning. En slutpunktsbeskrivning returneras alltid av ett GET_DESCRIPTOR kommando för konfigurationen.

Standardkontrollslutpunkten som är associerad med enhetsbeskrivningen räknas inte som en del av de slutpunkter som är associerade med gränssnittet och returneras därför inte i den här beskrivningen.

När värdprogramvaran begär en ändring av den alternativa inställningen för ett gränssnitt, ändras alla associerade slutpunkter och deras USB-resurser enligt den nya alternativa inställningen.

Förutom standardkontrollslutpunkterna kan slutpunkterna inte dela mellan gränssnitt.

| Offset | Fält            | Storlek | Värde    | Beskrivning                       |
| ------ | ---------------- | ---- | -------- | --------------------------------- |
| 0      | bLength          | 1    | Antal   | Den här beskrivningens storlek i byte. |
| 1      | bDescriptorType  | 1    | Konstant | Endpoint Descriptor Type (Slutpunktsbeskrivningstyp). |
| 2      | bEndpointAddress | 1    | Slutpunkt | Adressen till slutpunkten på USB-enheten som beskrivs i den här beskrivningen. Adressen är kodad på följande sätt:<br />Bit 3...0: Slutpunktsnumret<br />Bit 6...4: Reserverad, återställ till noll<br />Bit 7: Riktning, ignorerad för kontrollslutpunkter<br />0 = OUT-slutpunkt<br />1 = IN-slutpunkt |
| 3      | bmAttributes     | 1    | Bitmapp   | Det här fältet beskriver slutpunktens attribut när den konfigureras med hjälp av fältet **bConfigurationValue.** Bits 1..0: Överföringstyp<br />00 = Kontroll<br />01 = Isokron<br />10 = massutskick<br />11 = Avbrott<br />Om inte en isokron slutpunkt är bitarna 5..2 reserverade och måste vara inställda på noll. Om det ärochkront definieras de på följande sätt:<br />Bits 3..2: Synkroniseringstyp<br />00 = Ingen synkronisering<br />01 = Asynkron<br />10 = Anpassningsbar<br />11 = Synkron<br />Bits 5..4: Användningstyp<br />00 = Dataslutpunkt<br />01 = Feedbackslutpunkt<br />10 = Dataslutpunkt för implicit feedback<br />11 = Reserverad |
| 4      | wMaxPacketSize   | 2    | Antal   | Maximal paketstorlek som den här slutpunkten kan skicka eller ta emot när den här konfigurationen väljs.<br />För isokrona slutpunkter används det här värdet för att reservera busstiden i schemat, vilket krävs för datanyttolaster per mikroram. Pipe kan löpande använda mindre bandbredd än den reserverade. Enheten rapporterar vid behov den faktiska bandbredd som används via dess normala, icke-USB-definierade mekanismer.<br />För alla slutpunkter anger bitar 10..0 den maximala paketstorleken (i byte).<br />För isokrona och avbrottsslutpunkter med hög hastighet:<br />Bitar 12..11 anger antalet ytterligare transaktionsmöjligheter per mikroram: 00 = Ingen (1 transaktion per mikroram)<br />01 = ytterligare 1 (2 per mikroram)<br />10 = 2 ytterligare (3 per mikroram)<br />11 = Reserverad<br />Bitarna 15..13 är reserverade och måste anges till noll. |
| 6      | bInterval        | 1     | Antal   | Nummerintervall för avsökningsslutpunkt för dataöverföringar.<br />Uttryckt i bildrutor eller mikroramar beroende på enhetens drifthastighet (dvs. antingen 1 millisekund eller 125 μs enheter).<br />För fullständiga/snabba isokrona slutpunkter måste det här värdet vara inom intervallet 1 till 16. **bInterval används** som exponent för ett 2bInterval-1-värde. Till exempel betyder **bInterval** 4 en period på 8 (24-1).<br />För slutpunkter för avbrott med full/låg hastighet kan värdet för det här fältet vara mellan 1 och 255.<br />För slutpunkter med höghastighetsavbrott används **bInterval** som exponent för ett 2bInterval-1-värde. Till exempel betyder **bInterval** 4 en period på 8 (24-1). Det här värdet måste vara mellan 1 och 16.<br />För snabba bulk-/kontroll-OUT-slutpunkter anger **bInterval** slutpunktens maximala SPEED-hastighet. Värdet 0 anger slutpunktens aldrig NAK:er. Andra värden anger högst ett FÖR VARJE **bInterval** av mikroramar.<br />Det här värdet måste vara i intervallet 0 till 255. |

USBX definierar en USB-slutpunktsbeskrivning enligt följande:

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

USB-slutpunktsbeskrivningen är en del av en slutpunktscontainer, som beskrivs på följande sätt.

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

- **ux_endpoint_handle**: Referens för slutpunkten. Det här är vanligtvis adressen till instansen av den här strukturen för slutpunkten.
- **ux_endpoint_state:** Slutpunktens tillstånd.
- **ux_endpoint_ed:** Pekare till den fysiska slutpunkten i värdstyrenhetens lager.
- **ux_endpoint_descriptor:** USB-slutpunktsbeskrivning.
- **ux_endpoint_next_endpoint:** Pekare till nästa slutpunkt som tillhör samma gränssnitt.
- **ux_endpoint_interface:** Pekare till det gränssnitt som äger det här slutpunktsgränssnittet.
- **ux_endpoint_device:** Pekare till den överordnade enhetscontainern.
- **ux_endpoint_transfer:** USB-överföringsbegäran som används för att skicka/ta emot data från till och från enheten.

### <a name="string-descriptors"></a>Strängbeskrivningar

Strängbeskrivningar är valfria. Om en enhet inte stöder strängbeskrivningar måste alla referenser till strängbeskrivningar i enhets-, konfigurations- och gränssnittsbeskrivningar återställas till noll.

Strängbeskrivningar använder UNICODE-kodning, vilket ger stöd för flera teckenuppsättningar. Strängarna i en USB-enhet kan ha stöd för flera språk. När du begär en strängbeskrivning anger beställaren önskat språk med hjälp av ett språk-ID som definieras av USB-IF. Listan över för närvarande definierade USB-SPRÅK finns i USBX-bilaga ??.
Strängindex noll för alla språk returnerar en strängbeskrivning som innehåller en matris med två byte LANGID-koder som stöds av enheten. Det bör noteras att UNICODE-strängen inte är 0 avslutad. I stället beräknas storleken på strängmatrisen genom att subtrahera två från storleken på matrisen som finns i den första byten i beskrivningen.

USB-strängbeskrivningen 0 är kodad på följande sätt.

| Offset | Fält           | Storlek | Värde    | Beskrivning                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | N+2      | Den här beskrivningens storlek i byte |
| 1      | bDescriptorType | 1    | Konstant | STRING-beskrivningstyp           |
| 2      | wLANGID[0]      | 2    | Antal   | LANGID-kod 0                    |
| ...    | ...]            | ...  | ...      | ...                              |
| N      | wLANGID[n]      | 2    | Antal   | LANGID-kod n                    |

Andra USB-strängbeskrivningar kodas på följande sätt.

| Offset | Fält           | Storlek | Värde    | Beskrivning                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | Antal   | Den här beskrivningens storlek i byte |
| 1      | bDescriptorType | 1    | Konstant | STRING-beskrivningstyp           |
| 2      | bString         | n    | Antal   | UNICODE-kodad sträng           |

USBX definierar en USB-strängbeskrivning som inte är noll längd enligt följande:

```c
typedef struct UX_STRING_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT bString[1];
} UX_STRING_DESCRIPTOR;
```

### <a name="functional-descriptors"></a>Funktionella beskrivningar

Funktionella beskrivningar kallas även för klassspecifika beskrivningar. De använder normalt samma grundläggande strukturer som allmänna beskrivningar och gör att ytterligare information kan vara tillgänglig för klassen. När det till exempel gäller USB-ljudtalare tillåter klassspecifika beskrivningar att ljudklassen hämtar för varje alternativ inställning av den typ av ljudfrekvens som stöds.

### <a name="usbx-device-descriptor-framework-in-memory"></a>USBX Device Descriptor Framework i minnet

USBX underhåller de flesta enhetsbeskrivningar i minnet, det vill säga alla beskrivningar utom strängen och funktionella beskrivningar. Följande diagram visar hur de här beskrivningarna lagras och är relaterade.

![USBX Device Descriptor Framework i minnet](./media/usbx-host-stack/usbx-device-descriptor-framework.png)
