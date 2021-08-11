---
title: Kapitel 2 – Azure RTOS USBX-enhetsstackinstallation
description: Lär dig hur du installerar Azure RTOS USBX-enhetsstacken, samt viktiga värdöverväganden som du behöver tänka på innan du installerar.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: abe3e43e090890a5e51700fc2f587c59619fcdad5b71681fd4071c614dab5ce6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791416"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a>Kapitel 2 – Azure RTOS USBX-enhetsstackinstallation

## <a name="host-considerations"></a>Värdöverväganden

### <a name="computer-type"></a>Datortyp

Inbäddad utveckling utförs vanligtvis på Windows- eller Unix-värddatorer. När programmet har kompilerats, länkats och finns på värden laddas det ned till målmaskinvaran för körning.

### <a name="download-interfaces"></a>Ladda ned gränssnitt

Vanligtvis görs målnedladdningen via ett RS-232-seriellt gränssnitt, även om parallella gränssnitt, USB och Ethernet blir allt mer populära. Se dokumentationen för utvecklingsverktyg för tillgängliga alternativ.

### <a name="debugging-tools"></a>Felsökningsverktyg

Felsökning utförs vanligtvis via samma länk som nedladdningen av programavbildningen. Det finns en mängd olika felsökningsprogram, från små övervakningsprogram som körs på målet till verktygen Background Debug Monitor (BDM) och In-Circuit Emulator (ICE). VERKTYGET ICE ger den mest robusta felsökningen av den faktiska målmaskinvaran.

### <a name="required-hard-disk-space"></a>Nödvändigt hårddiskutrymme

Källkoden för USBX levereras i ASCII-format och kräver cirka 500 KByte utrymme på värddatorns hårddisk.

### <a name="target-considerations"></a>Målöverväganden

USBX kräver mellan 24 KByte och 64 KByte skrivskyddade minne (ROM) på målet i värdläge. Mängden minne som krävs beror på vilken typ av styrenhet som används och DE USB-klasser som är länkade till USBX. Ytterligare 32 KByte av målets RAM-minne (Random Access Memory) krävs för globala USBX-datastrukturer och minnespool. Den här minnespoolen kan också justeras beroende på det förväntade antalet enheter på USB-enheten och typen av USB-styrenhet. USBX-enhetssidan kräver ungefär 10–12 K ROM beroende på typ av styrenhet. RAM-minnesanvändningen beror på vilken typ av klass som emuleras av enheten.

USBX förlitar sig också på ThreadX-semaforer, mutexer och trådar för skydd av flera trådar och I/O-instängning och regelbunden bearbetning för övervakning av USB-busstopologin.

### <a name="product-distribution"></a>Produktdistribution

Azure RTOS USBX kan hämtas från vår offentliga källkodsdatabas på <https://github.com/azure-rtos/usbx/> .

Följande är en lista över flera viktiga filer på lagringsplatsen.

* ***ux_api.h:*** Den här C-huvudfilen innehåller alla systemekvat, datastrukturer och tjänstprototyper.
* ***ux_port.h:*** Den här C-huvudfilen innehåller alla datadefinitioner och strukturer som är specifika för utvecklingsverktyg.
* ***ux.lib:*** Det här är den binära versionen av USBX C-biblioteket. Den distribueras med standardpaketet.
* ***demo_usbx.c:*** C-filen som innehåller en enkel USBX-demo

Alla filnamn har gemener. Den här namngivningskonventionen gör det enklare att konvertera kommandona till Unix-utvecklingsplattformar.

## <a name="usbx-installation"></a>USBX-installation

USBX installeras genom att klona GitHub på den lokala datorn. Följande är en vanlig syntax för att skapa en klon av USBX-lagringsplatsen på datorn:

```c
    git clone https://github.com/azure-rtos/usbx
```

Du kan också ladda ned en kopia av lagringsplatsen med hjälp av nedladdningsknappen GitHub på huvudsidan.

Du hittar också anvisningar för att skapa USBX-biblioteket på startsidan för onlinedatabasen.

Följande allmänna anvisningar gäller för praktiskt taget alla installationer:

1. Använd samma katalog som du tidigare installerade ThreadX i på värdhårdenheten. Alla USBX-namn är unika och stör inte den tidigare USBX-installationen.
1. Lägg till ett anrop **till * ux_system_initialize** _ i eller nära början av _*_tx_application_define_**. Här initieras USBX-resurserna.
1. Lägg till ett anrop till ***ux_device_stack_initialize*.**
1. Lägg till ett eller flera anrop för att initiera nödvändiga USBX-klasser (antingen värd- och/eller enhetsklasser)
1. Lägg till ett eller flera anrop för att initiera den enhetsstyrenhet som är tillgänglig i systemet.
1. Det kan krävas att ändra filen tx_low_level_initialize.c för att lägga till maskinvaru-initiering på låg nivå och avbryta vektorroutning. Detta är specifikt för maskinvaruplattformen och kommer inte att diskuteras här.|
1. Kompilera programmets källkod och länka till USBX- och ThreadX-körningsbiblioteken (FileX och/eller Netx kan också krävas om USB-lagringsklassen och/eller USB-nätverksklasserna ska kompileras i), ux.a (eller ux.lib) och tx.a (eller tx.lib). Resultatet kan laddas ned till målet och köras!

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ för att skapa USBX-biblioteket. Alla alternativ finns i ***ux_user.h***.

I listan nedan beskrivs varje konfigurationsalternativ.

| &nbsp;Konfigurationsalternativ | Description |
| --- | --- |
| **UX_PERIODIC_RATE** | Det här värdet representerar hur många tick per sekund som gäller för en specifik maskinvaruplattform. Standardvärdet är 1 000, vilket anger 1 tick per millisekund. |
| **UX_THREAD_STACK_SIZE** | Det här värdet är storleken på stacken i byte för USBX-trådarna. Det kan vanligtvis vara 1 024 byte eller 2 048 byte beroende på vilken processor som används och värdstyrenheten. |
| **UX_THREAD_PRIORITY_ENUM** | Det här är ThreadX-prioritetsvärdet för DE USBX-uppräkningstrådar som övervakar busstopologin. |
| **UX_THREAD_PRIORITY_CLASS** | Det här är ThreadX-prioritetsvärdet för USBX-standardtrådarna. |
| **UX_THREAD_PRIORITY_KEYBOARD** | Det här är ThreadX-prioritetsvärdet för USBX HID-tangentbordsklassen. |
| **UX_THREAD_PRIORITY_DCD** | Det här är ThreadX-prioritetsvärdet för enhetsstyrenhetstråden. |
| **UX_NO_TIME_SLICE** | Det här värdet definierar faktiskt den tidssegment som ska användas för trådar. Om till exempel definieras till 0 använder Inte ThreadX-målporten tidssegment. |
| **UX_MAX_SLAVE_CLASS_DRIVER** | Det här är det maximala antalet USBX-klasser som kan registreras via ux_device_stack_class_register. |
| **UX_MAX_SLAVE_LUN** | Det här värdet representerar det aktuella antalet logiska SCSI-enheter som representeras i enhetens lagringsklassdrivrutin. |
| **UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC** | Om lagringsklassen definieras hanterar den KOMMANDON för flera medier (MMC), det vill säga DVD-ROM. |
| **UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES** | Det här värdet representerar antalet NetX-paket i CDC-ECM-klassens paketpool. Standardvärdet är 16. |
| **UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH** | Det här värdet representerar det maximala antalet byte som tas emot på en kontrollslutpunkt i enhetsstacken. Standardvärdet är 256 byte, men kan minskas i miljöer med minnesbegränsning. |
| **UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH** | Det här värdet representerar den maximala längden i byte för en HID-rapport. |
| **UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE** | Det här värdet representerar det maximala antalet HID-rapporter som kan köas samtidigt. |
| **UX_SLAVE_REQUEST_DATA_MAX_LENGTH** | Det här värdet representerar det maximala antalet byte som tas emot på en massslutpunkt i enhetsstacken. Standardvärdet är 4 096 byte, men kan minskas i miljöer med minnesbegränsning. |

## <a name="source-code-tree"></a>Källkodsträd

USBX-filerna finns i flera kataloger.

![Källkodsträd](media/usbx-device-stack/source-code-tree.png)

För att göra filerna igenkännliga med deras namn har följande konvention godkänts:

| Namn på filsuffix  | Filbeskrivning                          |
| ----------------- | ----------------------------------------- |
| ux_host_stack   | usbx-värdstackens kärnfiler                |
| ux_host_class   | usbx-värdstackklassfiler             |
| ux_hcd           | drivrutinsfiler för usbx-värdstacksstyrenhet   |
| ux_device_stack | usbx-enhetsstackens kärnfiler              |
| ux_device_class | usbx-enhetsstackklassfiler           |
| ux_dcd           | drivrutinsfiler för usbx-enhetsstack |
| ux_otg           | usbx otg controller driver related files  |
| ux_pictbridge    | usbx pictbridge-filer                     |
| ux_utility       | usbx-verktygsfunktioner                    |
| demo_usbx        | demonstrationsfiler för USBX              |

## <a name="initialization-of-usbx-resources"></a>Initiering av USBX-resurser

USBX har en egen minneshanterare. Minnet måste allokeras till USBX innan värden eller enheten på USBX initieras. USBX-minneshanteraren kan hantera system där minne kan cachelagras.

Följande funktion initierar USBX-minnesresurser med 128 K vanligt minne och ingen separat pool för cacheminnet:

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
| VOID *regular_memory_pool_start    | Början av den vanliga minnespoolen    |
| ULONG-regular_memory_size          | Storleken på den vanliga minnespoolen         |
| VOID *cache_safe_memory_pool_start | Början av cacheminnespoolen |
| ULONG-cache_safe_memory_size       | Storleken på cacheminnets säkra minnespool      |

Alla system kräver inte definitionen av säkert cacheminne. I ett sådant system anges de värden som skickas under initieringen för minnespekaren till UX_NULL och storleken på poolen till 0. USBX använder sedan den vanliga minnespoolen i stället för den säkra cachepoolen.

I ett system där det vanliga minnet inte cachelagras på ett säkert sätt och en kontrollant kräver DMA-minne är det nödvändigt att definiera en minnespool i en säker cachezon.

## <a name="uninitialization-of-usbx-resources"></a>Oinitiering av USBX-resurser

USBX kan avslutas genom att dess resurser frigörs. Innan usbx avslutas måste alla klasser och kontrollantresurser avslutas korrekt. Följande funktion uninitialiserar USBX-minnesresurser:

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

Prototypen för ux_system_initialize är följande:

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a>Definition av USB-enhetsstyrenhet

Endast en USB-styrenhet kan definieras när som helst för att fungera i enhetsläge. Programmets initieringsfil ska innehålla den här definitionen. Följande rad utför definitionen av en allmän USB-styrenhet:

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

INitieringen av USB-enheten har följande prototyp:

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

med följande parametrar:

| Pararmeter               | Description                      |
| ------------------------ | -------------------------------- |
| ULONG-dcd_io            | Adress för kontrollantens IO     |
| ULONG-dcd_irq           | Avbrott som används av kontrollanten |
| ULONG-dcd_vbus_address | Adress för VBUS GPIO         |

Följande exempel är initieringen av USBX i enhetsläge med klassen för lagringsenheter och en allmän styrenhet:

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

USBX levereras med en demonstrationsfil och en simuleringsmiljö. Det är alltid en bra idé att få igång demonstrationsplattformen först – antingen på målmaskinvaran eller en specifik demonstrationsplattform.

## <a name="usbx-version-id"></a>USBX-versions-ID

Den aktuella versionen av USBX är tillgänglig för både användaren och programprogramvaran under körningen. Programmeraren kan hämta USBX-versionen från undersökningen av filen ***ux_port.h** _ . Dessutom innehåller den här filen även en versionshistorik för motsvarande port. Programprogramvara kan hämta USBX-versionen genom att undersöka den globala strängen *_ _ _ux_version_id_* _, som definieras i _*_ux_port.h_**.
