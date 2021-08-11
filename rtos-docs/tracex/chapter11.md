---
title: Kapitel 11 – Format för händelsespårningsbuffert
description: ThreadX har inbyggt stöd för händelsespårning för alla Azure RTOS ThreadX-tjänster, trådtillståndsändringar och användardefinierade händelser.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: b230a6207cec3a0968d88b197455896881e5ef7a0d8b93d4b1fb5a37696a7b6c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802149"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a>Kapitel 11 – Format för händelsespårningsbuffert

Azure RTOS ThreadX har inbyggt stöd för händelsespårning för alla ThreadX-tjänster, trådtillståndsändringar och användardefinierade händelser. Om du vill använda händelsespårning skapar du helt enkelt ThreadX-, NetX- och FileX-biblioteken **med TX_ENABLE_EVENT_TRACE** definierade och aktiverar spårning genom att **_anropa tx_trace_enable-funktionen._** Det här kapitlet beskriver den processen.

## <a name="event-trace-format"></a>Händelsespårningsformat

Formatet på händelsespårningsbufferten i ThreadX är indelat i tre delar, nämligen kontrollrubriken, objektregistret och spårningsposterna. Följande beskriver den allmänna layouten för händelsespårningsbufferten i ThreadX:

**Kontrollhuvud**

**Objektregisterpost 0**

**…**

**Objektregisterpost "n"**

**Händelsespårningspost 0**

**…**

**Händelsespårningspost "n"**

### <a name="event-trace-control-header"></a>Event Trace Control-huvud

Kontrollhuvudet definierar den exakta layouten för händelsespårningsbufferten. Detta inkluderar hur många ThreadX-objekt som kan registreras samt hur många händelser som kan registreras. Dessutom definierar kontrollhuvudet var vart och ett av elementen i spårningsbufferten finns. Följande datastruktur definierar kontrollrubriken:

```c
typedef struct TX_TRACE_CONTROL_HEADER_STRUCT
{
    ULONG    tx_trace_control_header_id;
    ULONG    tx_trace_control_header_timer_valid_mask;
    ULONG    tx_trace_control_header_trace_base_address;
    ULONG    tx_trace_control_header_object_registry_start_pointer;
    USHORT   tx_trace_control_header_reserved1;
    USHORT   tx_trace_control_header_object_registry_name_size;
    ULONG    tx_trace_control_header_object_registry_end_pointer;
    ULONG    tx_trace_control_header_buffer_start_pointer;
    ULONG    tx_trace_control_header_buffer_end_pointer;
    ULONG    tx_trace_control_header_buffer_current_pointer;
    ULONG    tx_trace_control_header_reserved2;
    ULONG    tx_trace_control_header_reserved3;
    ULONG    tx_trace_control_header_reserved4;
} TX_TRACE_CONTROL_HEADER;
```

### <a name="control-header-id"></a>Kontrollhuvud-ID

Kontrollhuvud-ID består av 32-bitars HEX-värdet för 0x54585442, vilket motsvarar ASCII-tecknen ***TXTB***. Eftersom det här värdet skrivs som en 32-bitars osignerad variabel kan det också användas för att identifiera händelsespårningsbufferts endianens. Om till exempel värdet i de första fyra byes av minnet är 0x54, 0x58, 0x54, 0x42, skrevs händelsespårningsbufferten i big endian format. Annars skrevs händelsespårningsbufferten i little endian format.

### <a name="timer-valid-mask"></a>Giltig timermask

Den giltiga timermasken definierar hur många bitar av tidsstämpeln i de faktiska händelsespårningsposterna som är giltiga. Om tidsstämpelkällan till exempel har 16 bitar ska värdet i det här fältet 0xFFFF. En 32-bitars tidsstämpelkälla skulle ha värdet 0xFFFFFFFF. Det här värdet definieras av **konstanten*** TX_TRACE_TIME_MASK _ i _*_tx_port.h_**.

### <a name="trace-base-address"></a>Spårningsbasadress

Basadressen för spårningsbufferten är den adress som programmet angav som början på spårningsbufferten ***i tx_trace_enable anropet.*** Den här adressen underhålls för den enda användningen av analysverktyget för att härleda buffertrelativa förskjutningar för de olika elementen i bufferten. Till exempel beräknas den relativa buffertförskjutningen för den aktuella händelsen i spårningsbufferten genom enkel subtraktion av basadressen från den aktuella händelseadressen.

### <a name="registry-start-and-end-pointers"></a>Start- och slutpekare för registret

Startpekaren för registret pekar på adressen för den första objektregisterposten, medan registrets slut pekare pekar på adressen im.. /mediately efter den senaste registerposten. Dessa värden konfigureras under *tx_trace_enable* bearbetning och ändras inte under spårningstiden.

### <a name="registry-name-size"></a>Storlek på registernamn

Registernamnets storlek definierar maximal storlek i byte för varje objektnamn i registerposten och definieras av symbolen ***TX_TRACE_OBJECT_REGISTRY_NAME** _. Standardvärdet är 32 och definieras i _*_tx_trace.h_*_. Objektnamnet motsvarar det namn som programmet gav när objektet skapades. Till exempel är objektregisternamnet för en tråd det namn som anges av programmet till _*_tx_thread_create_**call.

### <a name="buffer-start-and-end-pointers"></a>Buffertstart- och slut pekare

Startpekaren för händelsespårningsbufferten pekar på adressen för den första spårningsposten, medan registrets slut pekare pekar på adressen im.. /mediately efter den senaste spårningsposten. Dessa värden konfigureras under ***tx_trace_enable</bearbetning*** och ändras inte under spårningstiden.

### <a name="current-buffer-pointer"></a>Aktuell buffertpekare

Den aktuella pekaren för händelsespårningsbufferten pekar på adressen för den äldsta spårningsposten. Eftersom spårningsposterna finns i en cirkelformad lista representerar den aktuella buffertpekaren även nästa spårningspost som ska skrivas. |

## <a name="event-trace-object-registry"></a>Event Trace Object Registry

Registret för händelsespårningsobjekt innehåller registerposter ***n** _ object som motsvarar de objekt som skapas av programmet. Huvudsyftet med objektregistret är att externa analysverktyg korrelerar faktiska objektnamn med objektadresserna för spårningsbuffertposterna. Antalet registerposter anges av programmet i anropet _ *_tx_trace_enable_** .

Varje objektregisterpost innehåller information om ett specifikt ThreadX-objekt som har skapats tidigare av programmet. Följande datastruktur definierar varje objektregisterpost:

```c
typedef struct TX_TRACE_OBJECT_REGISTRY_ENTRY_STRUCT
{
    UCHAR    tx_trace_object_registry_entry_object_available**;
    UCHAR    tx_trace_object_registry_entry_object_type**;
    UCHAR    tx_trace_object_registry_entry_object_reserved1;
    UCHAR    tx_trace_object_registry_entry_object_reserved2;
    ULONG    tx_trace_thread_registry_entry_object_pointer;
    ULONG    tx_trace_object_registry_entry_object_parameter_1;
    ULONG    tx_trace_object_registry_entry_object_parameter_2;
    UCHAR    tx_trace_thread_registry_entry_object_name[TX_TRACE_OBJECT_REGISTRY_NAME];

} TX_TRACE_OBJECT_REGISTRY_ENTRY;
```

### <a name="object-available-flag"></a>Flagga för tillgängligt objekt

Flaggan för objektet tillgänglig är inställd på 1 om posten i objektregistret är tillgänglig. Om värdet inte är 1 är objektregisterposten inte tillgänglig. Observera att posten fortfarande kan innehålla giltig information även om den är tillgänglig.

### <a name="object-entry-type"></a>Objektinmatningstyp

Objektposttypen identifierar typen av objekt i den här posten. Följande är en lista över giltiga objekttyper:

| **Värde** | **Objekttyp** |
|---------- | --------------- |
| 0         | Inte giltig       |
| 1         | Tråd          |
| 2         | Timer |
| 3         | Kö |
| 4         | Semafor |
| 5         | Mutex |
| 6         | Event Flags-grupp |
| 7         | Blockpool |
| 8         | Bytepool |
| 9         | .. /media |
| 10        | Fil |
| 11        | IP-adress |
| 12        | Paketpool |
| 13        | TCP Socket |
| 14        | UDP Socket |
| 15-20     | Reserverat |  
| 21        | USB-värdstacksenhet |
| 22        | USB-värdstackgränssnitt |
| 23        | USB-värdslutpunkt |
| 24        | USB-värdklass |
| 25        | USB-enhet |
| 26        | USB-enhetsgränssnitt |
| 27        | USB-enhetsslutpunkt |
| 28        | USB-enhetsklass |

### <a name="object-pointer"></a>Objekt pekare

Objektpekaren anger den objektadress som används för att komma åt objektet med hjälp av ThreadX-API:et.

### <a name="object-reserved-fields"></a>Objektreserverade fält

För alla andra objekt än trådar ska dessa reserverade fält vara 0. För trådar placeras prioriteten för tråden när den anges i registret i dessa två reserverade fält.

### <a name="object-parameters"></a>Objektparametrar

Objektparametrarna innehåller kompletterande information om objektet. Följande beskriver kompletterande information för varje ThreadX-objekt:

| **Objekttyp**        | **Parameter 1**  | **Parameter 2** |
|----------------------- | ---------------- | --------------- |
| Tråd                 | Stackstart      | Stackstorlek |
| Timer                  | Inledande tick | Scheman för omscheman |
| Kö                  | Köstorlek | Meddelandestorlek |
| Semafor              | Inledande instanser | - |
| Mutex                  | Arvsflagga | - |
| Event Flags-grupp      | - | - |
| Blockpool             | Totalt antal block | Blockstorlek |
| Bytepool              | Totalt antal byte | - |
| .. /media                  | Fat Cache Size | Sektorcachestorlek |
| Fil                   | - | - |
| IP-adress                     | Stackstart | Stackstorlek |
| Paketpool            | Paketstorlek | Antal paket |
| TCP Socket             | IP-adress | Fönsterstorlek |
| UDP Socket             | IP-adress | Maximalt antal RX-köer |

### <a name="object-name"></a>Objektnamn

Objektnamnet innehåller namnet på ThreadX-objektet. Namnet är det namn som angavs för ThreadX när objektet skapades. Som standard har objektnamnet högst 32 tecken. Faktiska namn som är större än 32 tecken trunkeras.

## <a name="event-trace-entries"></a>Händelsespårningsposter

Händelsespårningsposterna finns i den nedre delen av händelsespårningsbufferten. Posterna finns i en cirkelformad lista med den aktuella pekaren som pekar på den äldsta posten. Antalet poster i listan beräknas av  det tx_trace_enable anropet.

Varje objektregisterpost innehåller information om en specifik ThreadX-spårningshändelse. Följande datastruktur definierar varje spårningshändelsepost:

```c
typedef struct TX_TRACE_BUFFER_ENTRY_STRUCT
{
    ULONG     tx_trace_buffer_entry_thread_pointer;
    ULONG     tx_trace_buffer_entry_thread_priority;
    ULONG     tx_trace_buffer_entry_event_id;
    ULONG     tx_trace_buffer_entry_time_stamp;
    ULONG     tx_trace_buffer_entry_information_field_1;
    ULONG     tx_trace_buffer_entry_information_field_2;
    ULONG     tx_trace_buffer_entry_information_field_3;
    ULONG     tx_trace_buffer_entry_information_field_4;
} TX_TRACE_BUFFER_ENTRY;
```

### <a name="thread-pointer"></a>Tråd pekare

Trådpekaren innehåller adressen till tråden som körs vid tidpunkten för den här händelsen. Om händelsen inträffade under initieringen (ingen tråd körs) är värdet för pekaren 0xF0F0F0F0. Om händelsen inträffade under en ISR (Interrupt Service Routine) är värdet för pekaren 0xFFFFFFFF. Om posten inte har använts än är värdet för pekaren 0.

### <a name="thread-priority"></a>Trådprioritet

Trådprioritetsfältet innehåller trådprioritet och preemption-threshold för tråden som kördes vid tidpunkten för den här händelsen. Om det finns en avbrottskontext (trådpekaren är 0xFFFFFFFF) är värdet för  det här fältet inte prioriteten utan istället värdet för _tx_thread_current_ptr vid tidpunkten för händelsen. Annars är värdet för det här fältet 0.

### <a name="event-id"></a>Händelse-ID

Händelse-ID:t anger den händelse som ägde rum. Giltiga Händelse-ID:t för ThreadX-spårning sträcker sig från 1 till 1024. Värden som börjar 1025 och senare är reserverade för användarspecifika händelser. Se filen ***tx_trace.h för*** den fullständiga definitionen av ThreadX-händelse-ID:er.</td>

### <a name="information-fields-1-4"></a>Informationsfält (1–4)

Informationsfälten innehåller ytterligare information om den specifika händelsen. Se filen ***tx_trace.h*** för en fullständig beskrivning av informationsfälten för var och en av de definierade ThreadX-händelse-ID:erna.