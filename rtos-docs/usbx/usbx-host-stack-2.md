---
title: Kapitel 2 – Azure RTOS USBX-värdstackinstallation
description: Lär dig hur du installerar USBX-värdstacken.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 77df2c4e4bf4ef38403fe78eb98f18820de4325aadb941fc69275e4c77754212
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790974"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a>Kapitel 2 – Azure RTOS USBX-värdstackinstallation

## <a name="host-considerations"></a>Värdöverväganden

### <a name="computer-type"></a>Datortyp

Inbäddad utveckling utförs vanligtvis på Windows- eller Unix-värddatorer. När programmet har kompilerats, länkats och finns på värden laddas det ned till målmaskinvaran för körning.

### <a name="download-interfaces"></a>Ladda ned gränssnitt

Målnedladdningen görs vanligtvis via ett RS-232-seriellt gränssnitt, även om parallella gränssnitt, USB och Ethernet blir allt mer populära. Se dokumentationen för utvecklingsverktyg för tillgängliga alternativ.

### <a name="debugging-tools"></a>Felsökningsverktyg

Felsökning utförs vanligtvis via samma länk som nedladdningen av programavbildningen. Det finns en mängd olika felsökningsprogram, från små övervakningsprogram som körs på målet till verktygen Background Debug Monitor (BDM) och In-Circuit Emulator (ICE). VERKTYGET ICE ger den mest robusta felsökningen av den faktiska målmaskinvaran.

### <a name="required-hard-disk-space"></a>Nödvändigt hårddiskutrymme

Källkoden för USBX levereras i ASCII-format och kräver cirka 500 KByte utrymme på värddatorns hårddisk.

## <a name="target-considerations"></a>Målöverväganden

USBX kräver mellan 24 KByte och 64 KByte skrivskyddade minne (ROM) på målet i värdläge. Mängden minne som krävs beror på vilken typ av styrenhet som används och DE USB-klasser som är länkade till USBX. Ytterligare 32 KByte av målets RAM-minne (Random Access Memory) krävs för globala USBX-datastrukturer och minnespool. Den här minnespoolen kan också justeras beroende på det förväntade antalet enheter på USB-enheten och typen av USB-styrenhet. USBX-enhetssidan kräver ungefär 10–12 K ROM beroende på typ av styrenhet. RAM-minnesanvändningen beror på vilken typ av klass som emuleras av enheten.

USBX förlitar sig också på ThreadX-semaforer, mutexer och trådar för skydd av flera trådar och I/O-instängning och regelbunden bearbetning för övervakning av USB-busstopologin.

### <a name="product-distribution"></a>Produktdistribution

Azure RTOS USBX kan hämtas från vår offentliga källkodsdatabas på <https://github.com/azure-rtos/usbx/> .

Följande är en lista över flera viktiga filer på lagringsplatsen:

- ***ux_api.h:*** Den här C-huvudfilen innehåller alla systemekvat, datastrukturer och tjänstprototyper.
- ***ux_port.h:*** Den här C-huvudfilen innehåller alla datadefinitioner och strukturer som är specifika för utvecklingsverktyg.
- ***ux.lib:*** Det här är den binära versionen av USBX C-biblioteket. Den distribueras med standardpaketet.
- ***demo_usbx.c:*** C-filen som innehåller en enkel USBX-demo

Alla filnamn har gemener. Den här namngivningskonventionen gör det enklare att konvertera kommandona till Unix-utvecklingsplattformar.

## <a name="usbx-installation"></a>USBX-installation

USBX installeras genom att klona GitHub till din lokala dator. Följande är en vanlig syntax för att skapa en klon av USBX-lagringsplatsen på datorn:

```powershell
    git clone https://github.com/azure-rtos/usbx
```

Du kan också ladda ned en kopia av lagringsplatsen med hjälp av nedladdningsknappen GitHub på huvudsidan.

Du hittar också anvisningar för att skapa USBX-biblioteket på startsidan för onlinedatabasen.

Följande allmänna anvisningar gäller för praktiskt taget alla installationer:

1. Använd samma katalog som du tidigare installerade ThreadX i på värdhårdenheten. Alla USBX-namn är unika och stör inte den tidigare USBX-installationen.
2. Lägg till ett anrop **till * ux_system_initialize** _ i eller nära början av _ *_tx_application_define_.* * Här initieras USBX-resurserna.
3. Lägg till ett anrop till ***ux_host_stack_initialize*.**
4. Lägg till ett eller flera anrop för att initiera nödvändig USBX.
5. Lägg till ett eller flera anrop för att initiera de värdstyrenheter som är tillgängliga i systemet.
6. Det kan krävas att ändra filen tx_low_level_initialize.c för att lägga till maskinvaru-initiering på låg nivå och avbryta vektorroutning. Detta är specifikt för maskinvaruplattformen och kommer inte att diskuteras här.
7. Kompilera programmets källkod och länka till USBX- och ThreadX-körningsbiblioteken (FileX och/eller Netx kan också krävas om USB-lagringsklassen och/eller USB-nätverksklasserna ska kompileras i), ux.a (eller ux.lib) och tx.a (eller tx.lib). Resultatet kan laddas ned till målet och köras.

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ för att skapa USBX-biblioteket. Alla alternativ finns i ***ux_user.h***.

I listan nedan beskrivs varje konfigurationsalternativ.


- **UX_PERIODIC_RATE:** Det här värdet representerar hur många tick per sekund som gäller för en specifik maskinvaruplattform. Standardvärdet är 1 000, vilket anger ett tick per millisekund.
- **UX_MAX_CLASS_DRIVER:** Det här värdet är det maximala antalet klasser som kan läsas in av USBX. Det här värdet representerar klasscontainern och inte antalet instanser av en klass. Om en viss implementering av USBX till exempel behöver hubbklassen, skrivarklassen och lagringsklassen kan UX_MAX_CLASS_DRIVER-värdet anges till 3 oavsett antalet enheter som tillhör dessa klasser.
- **UX_MAX_HCD:** Det här värdet representerar antalet olika värdstyrenheter som är tillgängliga i systemet. För USB 1.1-stöd är det här värdet främst 1. För USB 2.0 kan det här värdet vara mer än 1. Det här värdet representerar antalet samtidiga värdstyrenheter som körs samtidigt. Om det till exempel finns två instanser av OHCI som körs eller en EHCI och en OHCI-styrenhet som kör, ska UX_MAX_HCD vara inställd på 2. 
- **UX_MAX_DEVICES:** Det här värdet representerar det maximala antalet enheter som kan anslutas till USB-enheten. Normalt är det teoretiska maximala antalet på en enda USB-enhet 127 enheter. Det här värdet kan skalas ned för att spara minne. Det bör noteras att det här värdet representerar det totala antalet enheter oavsett antalet USB-buss i systemet.
- **UX_MAX_ED:** Det här värdet representerar det maximala antalet ED:er i kontrollantpoolen. Det här numret tilldelas endast till en kontrollant. Om det finns flera instanser av kontrollanter används det här värdet av varje enskild kontrollant.
- **UX_MAX_TD och UX_MAX_ISO_TD:** Det här värdet representerar det maximala antalet vanliga och isokrona TD:er i kontrollantpoolen. Det här numret tilldelas endast till en kontrollant. Om det finns flera instanser av kontrollanter används det här värdet av varje enskild kontrollant.
- **UX_THREAD_STACK_SIZE:** Det här värdet är storleken på stacken i byte för USBX-trådarna. Det kan vanligtvis vara 1 024 byte eller 2 048 byte beroende på vilken processor som används och värdstyrenheten.
- **UX_HOST_ENUM_THREAD_STACK_SIZE:** Det här värdet är stackstorleken för USB-värduppräkningstråden. Om den här symbolen jag inte har angett anges STORLEKEN för USBX-värduppräkningstrådstacken **till UX_THREAD_STACK_SIZE**. 
- **UX_HOST_HCD_THREAD_STACK_SIZE:** Det här värdet är stackstorleken för USB-värdens HCD-tråd. Om den här symbolen jag inte har angett är USBX-värdens HCD-trådstackstorlek inställd **på UX_THREAD_STACK_SIZE**.
- **UX_THREAD_PRIORITY_ENUM:** Det här är ThreadX-prioritetsvärdet för USBX-uppräkningstrådarna som övervakar busstopologin.
- **UX_THREAD_PRIORITY_CLASS:** Det här är ThreadX-prioritetsvärdet för USBX-standardtrådarna.
- **UX_THREAD_PRIORITY_KEYBOARD:** Det här är ThreadX-prioritetsvärdet för USBX HID-tangentbordsklassen.
- **UX_THREAD_PRIORITY_HCD:** Det här är ThreadX-prioritetsvärdet för värdstyrenhetstråden.
- **UX_NO_TIME_SLICE:** Det här värdet definierar faktiskt det tidssegment som ska användas för trådar. Om till exempel definieras till 0 använder Inte ThreadX-målporten tidssegment.
- **UX_MAX_HOST_LUN:** Det här värdet representerar det maximala antalet logiska SCSI-enheter som representeras i värdlagringsklassdrivrutinen.
- **UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT:** Om det här värdet har definierats innehåller det här värdet kod för att hantera lagringsenheter som använder CB- eller CBI-protokollet (till exempel disketter). Det är inaktiverat som standard eftersom dessa protokoll är föråldrade och ersätts av BOT-protokollet (Bulk Only Transport) som i stort sett alla moderna lagringsenheter använder.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE:** Om det här värdet har definierats gör det ux_host_class_hid_keyboard_key_get att endast rapportera nyckeländringar, det vill säga tangenttryckningar och nyckelutgåningar. Som standard rapporterar den bara när en nyckel är nere.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY:** Används endast om **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** har definierats. Om detta definieras gör ux_host_class_hid_keyboard_key_get endast nedtryckta/nedtryckta rapportändringar. utgivna/upp-ändringar rapporteras inte.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS:** Används endast om **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** har definierats. Om den här definieras ux_host_class_hid_keyboard_key_get rapportlåsnyckeln (CapsLock/NumLock/ScrollLock) ändras.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS:** Används endast om **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** har definierats. Om detta definieras ux_host_class_hid_keyboard_key_get rapportmodifierarnyckeln (Ctrl/Alt/Skift/GUI).
- **UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES:** Om det här värdet har definierats representerar det antalet paket i CDC-ECM-värdklassen. Standardvärdet är 16.

## <a name="source-code-tree"></a>Källkodsträd

USBX-filerna finns i flera kataloger.

![Källkodsträd](media/usbx-host-stack/source-code-tree.png)

För att göra filerna igenkännliga med deras namn har följande konvention godkänts:

| Namn på filsuffix | Filbeskrivning                          |
| ---------------- | ----------------------------------------- |
| ux_host_stack    | usbx-värdstackkärnfiler                |
| ux_host_class    | usbx-värdstackklassfiler             |
| ux_hcd           | drivrutinsfiler för usbx-värdstacksstyrenhet   |
| ux_device_stack  | usbx-enhetsstackens kärnfiler              |
| ux_device_class  | usbx-enhetsstackklassfiler           |
| ux_dcd           | drivrutinsfiler för usbx-enhetsstackenheter |
| ux_otg           | usbx otg controller driver related files  |
| ux_pictbridge    | usbx pictbridge files                     |
| ux_utility       | usbx-verktygsfunktioner                    |
| demo_usbx        | demonstrationsfiler för USBX              |

## <a name="initialization-of-usbx-resources"></a>Initiering av USBX-resurser

USBX har en egen minneshanterare. Minnet måste allokeras till USBX innan värd- eller enhetssidan för USBX initieras. USBX-minneshanteraren kan hantera system där minne kan cachelagras.

Följande funktion initierar USBX-minnesresurser med 128 000 vanligt minne och ingen separat pool för cacheminne:

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

Prototypen för ux_system_initialize är följande.

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a>Indataparametrar:

- **regular_memory_pool_start** Början av den vanliga minnespoolen.
- **regular_memory_size** Storleken på den vanliga minnespoolen.
- **cache_safe_memory_pool_start** Början av cacheminnets säkra minnespool.
- **cache_safe_memory_size** Storleken på cacheminnets säkra minnespool.    |

Alla system kräver inte definitionen av säkert cacheminne. I ett sådant system anges de värden som skickades under initieringen för minnespekaren till UX_NULL och storleken på poolen till 0. USBX använder sedan den vanliga minnespoolen i stället för den säkra cachepoolen.

I ett system där det vanliga minnet inte cachelagras säkert och en styrenhet kräver att DMA-minne (t.ex. OHCI- och ANCI-styrenheter med flera) definieras, är det nödvändigt att definiera en minnespool i en säker cachezon.

## <a name="uninitialization-of-usbx-resources"></a>Oinitiering av USBX-resurser

USBX kan avslutas genom att dess resurser frigörs. Innan usbx avslutas måste alla klasser och kontrollantresurser avslutas korrekt. Följande funktion initierar USBX-minnesresurser:

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

Prototypen för ux_system_initialize är följande.

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a>Definition av USB-värdstyrenheter

Du måste definiera minst en USB-värdstyrenhet för att USBX ska fungera i värdläge. Programmets initieringsfil ska innehålla den här definitionen. Följande rad utför definitionen av en allmän värdkontrollant.

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

Den ux_host_stack_hcd_register har följande prototyp.

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

Funktionen ux_host_stack_hcd_register har följande parametrar.

- **hcd_name**: strängen för kontrollantens namn
- **hcd_initialize_function:** kontrollantens initieringsfunktion
- **hcd_param1:** vanligtvis I/O-värdet eller minnet som används av kontrollanten
- **hcd_param2**: vanligtvis den IRQ som används av kontrollanten

I vårt föregående exempel:

- "ux_hcd_controller" är namnet på kontrollanten
- "ux_hcd_controller_initialize" är initieringsrutinen för värdstyrenheten
- 0xd0000 är den adress där värdstyrenhetens register visas i minnet
- och 0x0a är den IRQ som används av värdstyrenheten.

Följande är ett exempel på initiering av USBX i värdläge med en värdkontrollant och flera klasser.

```c
UINT status;

/* Initialize USBX. */
ux_system_initialize(memory_ptr, (128*1024),0,0);

/* The code below is required for installing the USBX host stack. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, host stack has been initialized. */

/* Register all the host classes for this USBX implementation. */
status = ux_host_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_storage", ux_host_class_storage_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_printer", ux_host_class_printer_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_audio", ux_host_class_audio_entry);

/* If status equals UX_SUCCESS, host class has been registered. */

/* Register all the USB host controllers available in this system. */ 
status = ux_host_stack_hcd_register("ux_hcd_controller", ux_hcd_controller_initialize, 0x300000, 0x0a);

/* If status equals UX_SUCCESS, USB host controllers have been registered. */
```

## <a name="definition-of-host-classes"></a>Definition av värdklasser

Du måste definiera en eller flera värdklasser med USBX. En USB-klass krävs för att köra en USB-enhet när USB-stacken har konfigurerat USB-enheten. En USB-klass är specifik för enheten. En eller flera klasser kan krävas för att köra en USB-enhet beroende på antalet gränssnitt som finns i USB-enhetsbeskrivningarna.

Det här är ett exempel på registreringen av HUBB-klassen.

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

Funktionen ux_host_class_register har följande prototyp.

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- **class_name** är namnet på klassen
- **class_entry_address** är startpunkten för klassen

I exemplet med HUB-klass initiering:

- "ux_host_class_hub" är namnet på hubbklassen
- ux_host_class_hub_entry är startpunkten för HUBB-klassen.

## <a name="troubleshooting"></a>Felsökning

USBX levereras med en demonstrationsfil och en simuleringsmiljö. Det är alltid en bra idé att få igång demonstrationsplattformen först – antingen på målmaskinvaran eller en specifik demonstrationsplattform.

Om demonstrationssystemet inte fungerar kan du prova följande för att begränsa problemet.

## <a name="usbx-version-id"></a>USBX-versions-ID

Den aktuella versionen av USBX är tillgänglig för både användaren och programprogramvaran under körningen. Programmeraren kan hämta USBX-versionen från undersökningen av filen ***ux_port.h** _ . Dessutom innehåller den här filen även en versionshistorik för motsvarande port. Programprogramvara kan hämta USBX-versionen genom att undersöka den globala strängen *_ _ _ux_version_id_* _, som definieras i _*_ux_port.h_**.
