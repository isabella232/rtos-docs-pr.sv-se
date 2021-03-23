---
title: Kapitel 2 – installation av enhets stack för Azure återställnings tider USBX
description: Lär dig hur du installerar USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 097fdd3c6f09c666ec3ad6eda9e5ba3fa159cb4d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828449"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a>Kapitel 2 – installation av enhets stack för Azure återställnings tider USBX

## <a name="host-considerations"></a>Värd överväganden

### <a name="computer-type"></a>Typ av dator

Inbäddad utveckling utförs vanligt vis på Windows-datorer eller UNIX-värddatorer. När programmet har kompilerats, länkats och finns på värden laddas den ned till mål maskin varan för körning.

### <a name="download-interfaces"></a>Hämta gränssnitt

Normalt görs mål hämtningen via ett seriellt RS-232-gränssnitt, även om Parallel Interfaces, USB och Ethernet blir mer populära. I utvecklings verktygets dokumentation finns tillgängliga alternativ.

### <a name="debugging-tools"></a>Fel söknings verktyg

Fel sökning sker vanligt vis via samma länk som nedladdningen av program avbildningen. Det finns en mängd olika fel söknings program som sträcker sig från små övervakningsprogram som körs på målet genom BDM-verktyg (Background debug Monitor) och In-Circuit emulator (ICE). Verktyget ICE ger den mest robusta fel sökningen av faktisk mål maskin vara.

### <a name="required-hard-disk-space"></a>Nödvändigt hårddisk utrymme

Käll koden för USBX levereras i ASCII-format och kräver cirka 500 KB utrymme på värddatorns hård disk.

### <a name="target-considerations"></a>Mål överväganden

USBX kräver mellan 24 och 64 KB av skrivskyddat minne (ROM) på målet i värd läge. Mängden minne som krävs beror på vilken typ av styrenhet som används och vilka USB-klasser som är kopplade till USBX. En annan 32 KByte av målets RAM-minne (Random Access Memory) krävs för USBX globala data strukturer och minneskonfigurationer. Den här mediepoolen kan också justeras beroende på det förväntade antalet enheter på USB-enheten och typen av USB-styrenhet. Enhets sidan för USBX kräver ungefär 10-12 kB ROM beroende på typ av enhets styrenhet. Användningen av RAM-minnet beror på vilken typ av klass som emuleras av enheten.

USBX förlitar sig även på ThreadX-semaforer, mutexer och trådar för flera tråd skydd och I/O-inskjutningar och regelbunden bearbetning för övervakning av USB-bussens topologi.

### <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider-USBX kan hämtas från vår offentliga käll kods lagrings plats på <https://github.com/azure-rtos/usbx/> .

Följande är en lista över flera viktiga filer i lagrings platsen.

* ***ux_api. h***: den här C-huvudfilen innehåller alla system likställda, data strukturer och tjänst prototyper.
* ***ux_port. h***: den här C-huvudfilen innehåller alla data definitioner och strukturer för utveckling-verktyg.
* ***UX. lib***: det här är den binära versionen av USBX C-biblioteket. Den distribueras med standard paketet.
* ***demo_usbx. c***: c-filen som innehåller en enkel USBX-demo

Alla fil namn är i gemener. Den här namngivnings konventionen gör det lättare att konvertera kommandon till UNIX-utvecklings plattformar.

## <a name="usbx-installation"></a>USBX-installation

USBX installeras genom att klona GitHub-lagringsplatsen till den lokala datorn. Följande är en typisk syntax för att skapa en klon av USBX-lagringsplatsen på din dator:

```c
    git clone https://github.com/azure-rtos/usbx
```

Alternativt kan du ladda ned en kopia av lagrings platsen med hjälp av knappen Ladda ned på GitHub-huvud sidan.

Du hittar också instruktioner för att skapa USBX-biblioteket på den första sidan i online-lagringsplatsen.

Följande allmänna instruktioner gäller för i princip vilken installation som helst:

1. Använd samma katalog som du tidigare installerade ThreadX på värd hård disken. Alla USBX namn är unika och påverkar inte den tidigare USBX-installationen.
1. Lägg till ett anrop till ***ux_system_initialize** _ i eller nära början av _ *_tx_application_define_* *. Det är här som USBX-resurserna initieras.
1. Lägg till ett anrop till ***ux_device_stack_initialize *.**
1. Lägg till ett eller flera anrop för att initiera nödvändiga USBX-klasser (antingen värd-och/eller enhets klasser)
1. Lägg till ett eller flera anrop för att initiera den tillgängliga enhets styrenheten i systemet.
1. Du kan behöva ändra filen tx_low_level_initialize. c för att kunna lägga till maskin varu initiering på låg nivå och avbryta vektor routning. Detta är särskilt för maskin varu plattformen och beskrivs inte här. |
1. Kompilera program käll koden och länka med USBX-och ThreadX-körnings biblioteken (FileX och/eller netx kan också krävas om klassen för USB-lagring och/eller USB-nätverksanslutningar ska kompileras), UX. a (eller UX. lib) och TX. a (eller TX. lib). Resultatet kan hämtas till målet och köras!

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa USBX-biblioteket. Alla alternativ finns i ***ux_user. h***.

I listan nedan beskrivs varje konfigurations alternativ.

| Konfigurations &nbsp; alternativ | Beskrivning |
| --- | --- |
| **UX_PERIODIC_RATE** | Det här värdet anger hur många Tick per sekund för en viss maskin varu plattform. Standardvärdet är 1000 som anger 1 Tick per millisekund. |
| **UX_THREAD_STACK_SIZE** | Det här värdet är storleken på stacken i byte för USBX-trådarna. Det kan vara vanligt vis 1024 byte eller 2048 byte beroende på vilken processor som används och värd styrenheten. |
| **UX_THREAD_PRIORITY_ENUM** | Detta är prioritet svärdet för ThreadX för USBX-uppräknings trådar som övervakar buss sto pol Ogin. |
| **UX_THREAD_PRIORITY_CLASS** | Detta är prioritet svärdet för ThreadX för standard trådarna för USBX. |
| **UX_THREAD_PRIORITY_KEYBOARD** | Detta är ThreadX prioritets värde för HID-tangentbordet för USBX. |
| **UX_THREAD_PRIORITY_DCD** | Detta är ThreadX prioritets värde för enhets styrenhetens tråd. |
| **UX_NO_TIME_SLICE** | Det här värdet definierar i själva verket den tids sektor som ska användas för trådar. Om t. ex. har definierats till 0 används inte tids segment i ThreadX Target-porten. |
| **UX_MAX_SLAVE_CLASS_DRIVER** | Detta är det maximala antalet USBX-klasser som kan registreras via ux_device_stack_class_register. |
| **UX_MAX_SLAVE_LUN** | Värdet representerar det aktuella antalet SCSI-logiska enheter som representeras i enhetens lagrings klass driv rutin. |
| **UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC** | Om den har definierats hanterar lagrings klassen multi-media-kommandon (MMC), som är DVD-ROM. |
| **UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES** | Det här värdet representerar antalet NetX-paket i CDC-ECM-klassen ' Packet pool. Standardvärdet är 16. |
| **UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH** | Det här värdet representerar det maximala antalet byte som tagits emot på en kontroll slut punkt i enhets stacken. Standardvärdet är 256 byte, men kan minskas i miljöer med minnes begränsning. |
| **UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH** | Det här värdet representerar den maximala längden i byte för en HID-rapport. |
| **UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE** | Det här värdet representerar det maximala antalet HID-rapporter som kan köas samtidigt. |
| **UX_SLAVE_REQUEST_DATA_MAX_LENGTH** | Det här värdet representerar det maximala antalet byte som tagits emot på en Mass slut punkt i enhets stacken. Standardvärdet är 4096 byte, men kan minskas i miljöer med minnes begränsning. |

## <a name="source-code-tree"></a>Käll kods träd

USBX-filerna finns i flera kataloger.

![Käll kods träd](media/usbx-device-stack/source-code-tree.png)

Följande konvention har antagits för att göra filerna identifierbara med deras namn:

| Namnsuffix  | Fil Beskrivning                          |
| ----------------- | ----------------------------------------- |
| ux_host_stack   | USBX Host stack core-filer                |
| ux_host_class   | USBX värd stack klasser filer             |
| ux_hcd           | USBX för värd stack kontrollant   |
| ux_device_stack | USBX Device stack core-filer              |
| ux_device_class | filer för USBX Device stack-klasser           |
| ux_dcd           | USBX enhets stack Controller-drivrutinsfiler |
| ux_otg           | USBX OTG Controller-relaterade filer  |
| ux_pictbridge    | USBX PictBridge-filer                     |
| ux_utility       | USBX verktygs funktioner                    |
| demo_usbx        | demonstrations filer för USBX              |

## <a name="initialization-of-usbx-resources"></a>Initiering av USBX-resurser

USBX har en egen minnes hanterare. Minnet måste allokeras till USBX innan värden eller enhets sidan på USBX initieras. USBX minnes hanteraren kan hantera system där minnet kan cachelagras.

Följande funktion initierar USBX minnes resurser med 128 kB reguljärt minne och ingen separat pool för cache-säkert minne:

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

Prototypen för ux_system_initialize är följande:

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

Indataparametrar:

| Parameter                          | Beskrivning                             |
| ---------------------------------- | --------------------------------------- |
| VOID * regular_memory_pool_start    | Början av den vanliga mediepoolen    |
| ULONG regular_memory_size          | Storlek på den ordinarie lagringspoolen         |
| VOID * cache_safe_memory_pool_start | Början av cacheminnet för säker cache |
| ULONG cache_safe_memory_size       | Storlek på cachen för cache-säker pool      |

Inte alla system kräver definitionen av cache-säkert minne. I ett sådant system kommer värdena som skickas under initieringen av minnes pekaren att anges till UX_NULL och storleken på poolen till 0. USBX kommer sedan att använda den vanliga lagringspoolen i stället för den betrodda cache-poolen.

I ett system där det normala minnet inte är cache-säkert och en styrenhet kräver DMA-minne är det nödvändigt att definiera en minnesbuffert i en säker cache-zon.

## <a name="uninitialization-of-usbx-resources"></a>Avinitiering av USBX-resurser

USBX kan avbrytas genom att frisläppa sina resurser. Innan du avslutar USBX måste alla klasser och styrenhets resurser avbrytas korrekt. Följande funktion avinitierar USBX minnes resurser:

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

Prototypen för ux_system_initialize är följande:

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a>Definition av USB-enhets styrenhet

Endast en USB-enhets styrenhet kan definieras när som helst för att köras i enhets läge. Programmets initierings fil ska innehålla den här definitionen. Följande rad utför definitionen av en allmän USB-styrenhet:

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

Initieringen av USB-enheten har följande prototyp:

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

med följande parametrar:

| Pararmeter               | Beskrivning                      |
| ------------------------ | -------------------------------- |
| ULONG dcd_io            | Adress till styrenhetens IO     |
| ULONG dcd_irq           | Avbrott som används av kontrollanten |
| ULONG dcd_vbus_address | Adressen för VBUS-GPIO         |

Följande exempel är initieringen av USBX i enhets läge med lagrings enhets klassen och en allmän styrenhet:

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a>Felsökning

USBX levereras med en demonstrations fil och en simulerings miljö. Det är alltid en bra idé att få demonstrations plattformen igång först – antingen på mål maskin varan eller en speciell demonstrations plattform.

## <a name="usbx-version-id"></a>USBX versions-ID

Den aktuella versionen av USBX är tillgänglig både för användaren och program varan under körnings tillfället. Programmerare kan hämta USBX-versionen från undersökningen av filen ***ux_port. h** _. Dessutom innehåller den här filen även en versions historik för motsvarande port. Program varan kan hämta USBX-versionen genom att undersöka den globala strängen _ *_ _ux_version_id_* _, som definieras i _ *_ux_port. h_* *.
