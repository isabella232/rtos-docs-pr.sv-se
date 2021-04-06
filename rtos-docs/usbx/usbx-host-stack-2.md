---
title: Kapitel 2 – Azure återställnings tider USBX Host stack-installation
description: Lär dig hur du installerar USBX-värds Tacken.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 4c33f95b8ac268c557fd947a1303ec3af315a37e
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377092"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a>Kapitel 2 – Azure återställnings tider USBX Host stack-installation

## <a name="host-considerations"></a>Värd överväganden

### <a name="computer-type"></a>Typ av dator

Inbäddad utveckling utförs vanligt vis på Windows-datorer eller UNIX-värddatorer. När programmet har kompilerats, länkats och finns på värden laddas den ned till mål maskin varan för körning.

### <a name="download-interfaces"></a>Hämta gränssnitt

Normalt görs mål nedladdningen via ett seriellt RS-232-gränssnitt, även om Parallel Interfaces, USB och Ethernet blir mer populära. I utvecklings verktygets dokumentation finns tillgängliga alternativ.

### <a name="debugging-tools"></a>Fel söknings verktyg

Fel sökning sker vanligt vis via samma länk som nedladdningen av program avbildningen. Det finns en mängd olika fel söknings program som sträcker sig från små övervakningsprogram som körs på målet genom BDM-verktyg (Background debug Monitor) och In-Circuit emulator (ICE). Verktyget ICE ger den mest robusta fel sökningen av faktisk mål maskin vara.

### <a name="required-hard-disk-space"></a>Nödvändigt hårddisk utrymme

Käll koden för USBX levereras i ASCII-format och kräver cirka 500 KB utrymme på värddatorns hård disk.

## <a name="target-considerations"></a>Mål överväganden

USBX kräver mellan 24 och 64 KB av skrivskyddat minne (ROM) på målet i värd läge. Mängden minne som krävs beror på vilken typ av styrenhet som används och vilka USB-klasser som är kopplade till USBX. En annan 32 KByte av målets RAM-minne (Random Access Memory) krävs för USBX globala data strukturer och minneskonfigurationer. Den här mediepoolen kan också justeras beroende på det förväntade antalet enheter på USB-enheten och typen av USB-styrenhet. Enhets sidan för USBX kräver ungefär 10-12 kB ROM beroende på typ av enhets styrenhet. Användningen av RAM-minnet beror på vilken typ av klass som emuleras av enheten.

USBX förlitar sig även på ThreadX-semaforer, mutexer och trådar för flera tråd skydd och I/O-inskjutningar och regelbunden bearbetning för övervakning av USB-bussens topologi.

### <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider-USBX kan hämtas från vår offentliga käll kods lagrings plats på <https://github.com/azure-rtos/usbx/> .

Följande är en lista över flera viktiga filer i lagrings platsen:

- ***ux_api. h***: den här C-huvudfilen innehåller alla system likställda, data strukturer och tjänst prototyper.
- ***ux_port. h***: den här C-huvudfilen innehåller alla data definitioner och strukturer för utveckling-verktyg.
- ***UX. lib***: det här är den binära versionen av USBX C-biblioteket. Den distribueras med standard paketet.
- ***demo_usbx. c***: c-filen som innehåller en enkel USBX-demo

Alla fil namn är i gemener. Den här namngivnings konventionen gör det lättare att konvertera kommandon till UNIX-utvecklings plattformar.

## <a name="usbx-installation"></a>USBX-installation

USBX installeras genom att klona GitHub-lagringsplatsen till den lokala datorn. Följande är en typisk syntax för att skapa en klon av USBX-lagringsplatsen på din dator:

```powershell
    git clone https://github.com/azure-rtos/usbx
```

Alternativt kan du ladda ned en kopia av lagrings platsen med hjälp av knappen Ladda ned på GitHub-huvud sidan.

Du hittar också instruktioner för att skapa USBX-biblioteket på den första sidan i online-lagringsplatsen.

Följande allmänna instruktioner gäller för i princip vilken installation som helst:

1. Använd samma katalog som du tidigare installerade ThreadX på värd hård disken. Alla USBX namn är unika och påverkar inte den tidigare USBX-installationen.
2. Lägg till ett anrop till ***ux_system_initialize** _ i eller nära början av _ *_tx_application_define_.* * Det är här som USBX-resurserna initieras.
3. Lägg till ett anrop till ***ux_host_stack_initialize *.**
4. Lägg till ett eller flera anrop för att initiera nödvändiga USBX.
5. Lägg till ett eller flera anrop för att initiera de värd styrenheter som är tillgängliga i systemet.
6. Du kan behöva ändra filen tx_low_level_initialize. c för att kunna lägga till maskin varu initiering på låg nivå och avbryta vektor routning. Detta är särskilt för maskin varu plattformen och kommer inte att diskuteras här.
7. Kompilera program käll koden och länka med USBX-och ThreadX-körnings biblioteken (FileX och/eller netx kan också krävas om klassen för USB-lagring och/eller USB-nätverksanslutningar ska kompileras), UX. a (eller UX. lib) och TX. a (eller TX. lib). Resultatet kan hämtas till målet och köras.

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa USBX-biblioteket. Alla alternativ finns i ***ux_user. h***.

I listan nedan beskrivs varje konfigurations alternativ.


- **UX_PERIODIC_RATE**: det här värdet anger hur många Tick per sekund för en viss maskin varu plattform. Standardvärdet är 1000 som anger ett Tick per millisekund.
- **UX_MAX_CLASS_DRIVER**: det här värdet är det maximala antalet klasser som kan läsas in av USBX. Det här värdet representerar klass behållaren och inte antalet instanser av en klass. Om till exempel en viss implementering av USBX behöver klassen Hub, klassen skrivare och lagrings klassen, kan UX_MAX_CLASS_DRIVER svärdet anges till 3 oavsett hur många enheter som tillhör dessa klasser.
- **UX_MAX_HCD**: det här värdet representerar antalet olika värd styrenheter som är tillgängliga i systemet. För USB 1,1-stöd blir det här värdet 1. För USB 2,0-stöd kan det här värdet vara större än 1. Det här värdet representerar antalet samtidiga värd styrenheter som körs på samma gång. Om det till exempel finns två instanser av OHCI som körs eller en EHCI och en OHCI-styrenhet som kör, ska UX_MAX_HCD vara inställd på 2. 
- **UX_MAX_DEVICES**: det här värdet representerar det maximala antalet enheter som kan kopplas till USB-enheten. Normalt är det teoretiska maximala antalet på en enda USB 127-enheter. Det här värdet kan skalas ned för att spara minne. Det bör noteras att det här värdet representerar det totala antalet enheter oavsett antalet USB-bussar i systemet.
- **UX_MAX_ED**: det här värdet representerar det maximala antalet EDs i Controller-poolen. Det här numret tilldelas endast en kontrollant. Om det finns flera instanser av kontrollanter används det här värdet av varje enskild kontrollant.
- **UX_MAX_TD och UX_MAX_ISO_TD**: det här värdet representerar det maximala antalet vanliga och isokrona TDS i Controller-poolen. Det här numret tilldelas endast en kontrollant. Om det finns flera instanser av kontrollanter används det här värdet av varje enskild kontrollant.
- **UX_THREAD_STACK_SIZE**: det här värdet är storleken på stacken i byte för USBX-trådar. Det kan vara vanligt vis 1024 byte eller 2048 byte beroende på vilken processor som används och värd styrenheten.
- **UX_HOST_ENUM_THREAD_STACK_SIZE**: det här värdet är stack storleken för uppräknings tråden för USB-värden. Om den här symbolen inte är inställd anges USBX som **UX_THREAD_STACK_SIZE**. 
- **UX_HOST_HCD_THREAD_STACK_SIZE**: det här värdet är stack storleken för USB-VÄRDENS HCD-tråd. Om den här symbolen inte är inställd, anges USBX Host HCD tråd stack-storlek till **UX_THREAD_STACK_SIZE**.
- **UX_THREAD_PRIORITY_ENUM**: det här är prioritet svärdet för THREADX för USBX-uppräknings trådar som övervakar buss sto pol Ogin.
- **UX_THREAD_PRIORITY_CLASS**: det här är prioritet svärdet för ThreadX för standard trådarna för USBX.
- **UX_THREAD_PRIORITY_KEYBOARD**: det här är prioritet svärdet för THREADX för HID-tangentbordet för USBX.
- **UX_THREAD_PRIORITY_HCD**: Detta är prioritet svärdet för ThreadX för värd styrenhets tråden.
- **UX_NO_TIME_SLICE**: det här värdet definierar i själva verket den tids sektor som ska användas för trådar. Om t. ex. har definierats till 0 används inte tids segment i ThreadX Target-porten.
- **UX_MAX_HOST_LUN**: det här värdet representerar det maximala antalet SCSI-logiska enheter som representeras i värd lagrings klass driv rutinen.
- **UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: om det här värdet är definierat innehåller det här värdet kod för hantering av lagrings enheter som använder CB-eller CBI-protokollet (t. ex. disketter). Den är inaktive rad som standard eftersom dessa protokoll är föråldrade och ersätts av protokollet enbart Mass transport (BOT), vilket praktiskt taget alla moderna lagrings enheter använder.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: om det här värdet har definierats gör det här värdet ux_host_class_hid_keyboard_key_get till att bara rapportera viktiga ändringar, tangenttryckningar och viktiga versioner. Som standard rapporteras den bara när en nyckel är nere.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: används endast om **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** har definierats. Om det här är definierat, gör ux_host_class_hid_keyboard_key_get till att bara rapportera tangenter nedtryckt/ned-ändringar. viktiga uppdateringar/uppdateringar rapporteras inte.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: används endast om **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** har definierats. Om det här är definierat, gör ux_host_class_hid_keyboard_key_get att rapportera lås nyckel ändringar (CapsLock/NumLock/ScrollLock).
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: används endast om **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** har definierats. Om det här är definierat, gör ux_host_class_hid_keyboard_key_get att rapportens ändrings nyckel (Ctrl/Alt/Shift/GUI) ändras.
- **UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: om det här värdet är definierat representerar det här värdet antalet paket i värd klassen CDC-ECM. Standardvärdet är 16.

## <a name="source-code-tree"></a>Käll kods träd

USBX-filerna finns i flera kataloger.

![Käll kods träd](media/usbx-host-stack/source-code-tree.png)

Följande konvention har antagits för att göra filerna identifierbara med deras namn:

| Namnsuffix | Fil Beskrivning                          |
| ---------------- | ----------------------------------------- |
| ux_host_stack    | USBX Host stack core-filer                |
| ux_host_class    | USBX värd stack klasser filer             |
| ux_hcd           | USBX för värd stack kontrollant   |
| ux_device_stack  | USBX Device stack core-filer              |
| ux_device_class  | filer för USBX Device stack-klasser           |
| ux_dcd           | USBX enhets stack Controller-drivrutinsfiler |
| ux_otg           | USBX OTG Controller-relaterade filer  |
| ux_pictbridge    | USBX PictBridge-filer                     |
| ux_utility       | USBX verktygs funktioner                    |
| demo_usbx        | demonstrations filer för USBX              |

## <a name="initialization-of-usbx-resources"></a>Initiering av USBX-resurser

USBX har en egen minnes hanterare. Minnet måste allokeras till USBX innan värden eller enhets sidan på USBX initieras. USBX minnes hanteraren kan hantera system där minnet kan cachelagras.

Följande funktion initierar USBX minnes resurser med 128 kB av vanligt minne och ingen separat pool för cache-säkert minne:

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

Prototypen för ux_system_initialize är som följer.

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a>Indataparametrar:

- **regular_memory_pool_start** Början av den vanliga mediepoolen.
- **regular_memory_size** Storlek på den vanliga mediepoolen.
- **cache_safe_memory_pool_start** Början av cacheminnet för säker cache.
- **cache_safe_memory_size** Storlek på cachen för säkert minne.    |

Inte alla system kräver definitionen av cache-säkert minne. I ett sådant system kommer värdena som skickas under initieringen av minnes pekaren att anges till UX_NULL och storleken på poolen till 0. USBX kommer sedan att använda den vanliga lagringspoolen i stället för den betrodda cache-poolen.

I ett system där det normala minnet inte är cache-säkert och en styrenhet kräver DMA-minne (till exempel OHCI, EHCI-styrenheter bland andra) måste du definiera en minnesbuffert i en säker cache-zon.

## <a name="uninitialization-of-usbx-resources"></a>Avinitiering av USBX-resurser

USBX kan avbrytas genom att frisläppa sina resurser. Innan du avslutar USBX måste alla klasser och styrenhets resurser avbrytas korrekt. Följande funktion avinitierar USBX minnes resurser:

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

Prototypen för ux_system_initialize är som följer.

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a>Definition av USB-värdstyrenheter

Du måste definiera minst en USB-värdstyrenhet för att USBX ska kunna köras i värd läge. Programmets initierings fil ska innehålla den här definitionen. Följande rad utför definitionen av en allmän värd styrenhet.

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

Ux_host_stack_hcd_register har följande prototyp.

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

Funktionen ux_host_stack_hcd_register har följande parametrar.

- **hcd_name**: sträng för kontroll enhetens namn
- **hcd_initialize_function**: initierings funktionen för kontrollanten
- **hcd_param1**: vanligt vis det IO-värde eller minne som används av kontrollanten
- **hcd_param2**: vanligt vis IRQ som används av kontrollanten

I vårt föregående exempel:

- "ux_hcd_controller" är namnet på kontrollanten
- "ux_hcd_controller_initialize" är initierings rutinen för värd styrenheten
- 0xd0000 är den adress där värd styrenhetens register visas i minnet
- och 0x0A är den IRQ som används av värd styrenheten.

Följande är ett exempel på initiering av USBX i värd läge med en värd styrenhet och flera klasser.

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

## <a name="definition-of-host-classes"></a>Definition av värd klasser

Det krävs för att definiera en eller flera värd klasser med USBX. En USB-klass krävs för att köra en USB-enhet när USB-stacken har konfigurerat USB-enheten. En USB-klass är speciell för enheten. En eller flera klasser kan krävas för att köra en USB-enhet beroende på antalet gränssnitt som finns i USB-enhetens beskrivningar.

Detta är ett exempel på registreringen av HUB-klassen.

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
- **class_entry_address** är start punkten för klassen

I exemplet på initiering av HUB-klassen:

- "ux_host_class_hub" är namnet på NAV klassen
- ux_host_class_hub_entry är start punkten för NAV klassen.

## <a name="troubleshooting"></a>Felsökning

USBX levereras med en demonstrations fil och en simulerings miljö. Det är alltid en bra idé att få demonstrations plattformen igång först – antingen på mål maskin varan eller en speciell demonstrations plattform.

Om demonstrations systemet inte fungerar kan du prova följande saker för att begränsa problemet.

## <a name="usbx-version-id"></a>USBX versions-ID

Den aktuella versionen av USBX är tillgänglig både för användaren och program varan under körnings tillfället. Programmerare kan hämta USBX-versionen från undersökningen av filen ***ux_port. h** _. Dessutom innehåller den här filen även en versions historik för motsvarande port. Program varan kan hämta USBX-versionen genom att undersöka den globala strängen _ *_ _ux_version_id_* _, som definieras i _ *_ux_port. h_* *.
