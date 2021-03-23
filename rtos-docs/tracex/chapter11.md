---
title: Kapitel 11 – format för Event trace-buffert
description: ThreadX tillhandahåller inbyggt stöd för händelse spårning för alla Azure återställnings tider ThreadX-tjänster, ändringar i tråd tillstånd och användardefinierade händelser.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: d11b827558e9c96df44f462329b7807a500a64a4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827576"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a>Kapitel 11 – format för Event trace-buffert

Azure återställnings tider ThreadX innehåller inbyggt stöd för händelse spårning för alla ThreadX-tjänster, ändringar i tråd tillstånd och användardefinierade händelser. Om du vill använda händelse spårning skapar du bara ThreadX-, NetX-och FileX-biblioteken med **TX_ENABLE_EVENT_TRACE** definierat och aktiverar spårning genom att anropa funktionen **_tx_trace_enable_** . I det här kapitlet beskrivs processen.

## <a name="event-trace-format"></a>Händelse spårnings format

Formatet på ThreadX är uppdelat i tre delar, nämligen kontroll rubriken, objekt registret och spårnings posterna. I följande avsnitt beskrivs den allmänna layouten för ThreadX Event trace buffer:

**Kontroll rubrik**

**Objekt register post 0**

**…**

**Objekt register post "n"**

**Händelse spårnings post 0**

**…**

**Händelse spårnings post "n"**

### <a name="event-trace-control-header"></a>Kontroll rubrik för händelse spårning

Kontroll rubriken definierar den exakta layouten för Event trace-bufferten. Detta inkluderar hur många ThreadX-objekt som kan registreras och hur många händelser som kan registreras. Dessutom definierar kontroll rubriken var var och en av elementen i kommandobufferten finns. Följande data struktur definierar kontroll rubriken:

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

### <a name="control-header-id"></a>ID för kontroll huvud

Kontroll huvudets ID består av 32-bitars HEX-värdet för 0x54585442, som motsvarar ASCII-tecknen ***TXTB***. Eftersom det här värdet skrivs som en 32-bitars osignerad variabel, kan den också användas för att identifiera den här buffertens endian-värde. Om värdet i de första fyra byes i minnet till exempel är 0x54, 0x58, 0x54, 0x42 skrevs Event trace-bufferten i big endian format. Annars skrevs händelsespårningssessionen i little endian format.

### <a name="timer-valid-mask"></a>Giltig timer-mask

Den giltiga tids masken definierar hur många bitar av tidsstämpeln i de faktiska spårnings posterna för händelsen som är giltiga. Om till exempel en Time-stämpel-källa har 16 bitar, ska värdet i det här fältet vara 0xFFFF. En 32-bitars Time-tag-källa har värdet 0xFFFFFFFF. Det här värdet definieras av ***TX_TRACE_TIME_MASK** _ konstanten i _ *_tx_port. h_* *.

### <a name="trace-base-address"></a>Spårnings bas adress

Den sökta bas adressen är den adress som programmet angav som början på spårningssessionen i ***tx_trace_enable*** -anropet. Den här adressen upprätthålls för den enda användningen av analys verktyget för att härleda bufferrelative-förskjutningar för de olika elementen i bufferten. Till exempel beräknas den relativa förskjutningen för den aktuella händelsen i kommandobufferten med enkel subtraktion av bas adressen från den aktuella händelse adressen.

### <a name="registry-start-and-end-pointers"></a>Start-och slut punkter för registret

Start pekaren för registret pekar på adressen till den första objekt register posten, medan slut punkten för registret pekar på snabb adressen till adressen... /mediately följer den sista register posten. Dessa värden konfigureras under den *tx_trace_enable* bearbetningen och ändras inte under spårnings tiden.

### <a name="registry-name-size"></a>Register namn storlek

Register namnets storlek definierar den maximala storleken i byte för varje objekt namn i register posten och definieras av symbolen ***TX_TRACE_OBJECT_REGISTRY_NAME** _. Standardvärdet är 32 och definieras i _*_tx_trace. h_*_. Objekt namnet motsvarar det namn som angavs av programmet när objektet skapades. Objekt register namnet för en tråd är till exempel det namn som tillhandahålls av programmet till mappen _ *_tx_thread_create_* *.

### <a name="buffer-start-and-end-pointers"></a>Buffertens start-och slut punkter

Start pekaren för Event trace buffer pekar mot adressen för den första spårnings posten, medan register slut punkten pekar på snabb meddelandet för adress. /mediately efter den sista spårnings posten. Dessa värden konfigureras under ***tx_trace_enable</*** bearbetning och ändras inte under spårnings tiden.

### <a name="current-buffer-pointer"></a>Aktuell buffert pekare

Den aktuella pekaren för Event trace buffer pekar på den äldsta spårnings postens adress. Eftersom spårnings posterna upprätthålls i en cirkulär lista, representerar den aktuella bufferten också nästa spårnings post som ska skrivas. |

## <a name="event-trace-object-registry"></a>Objekt register för händelse spårning

Händelse spårnings objekt registret innehåller ***n** _ objekt register poster som motsvarar de objekt som skapats av programmet. Huvud syftet med objekt registret är för externa analys verktyg för att korrelera faktiska objekt namn med objekt adresser för spårningens buffert poster. Antalet register poster som anges av programmet i _ *_tx_trace_enable_** anropa.

Varje objekt register post innehåller information om ett specifik ThreadX-objekt som tidigare har skapats av programmet. Följande data struktur definierar varje objekt register post:

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

### <a name="object-available-flag"></a>Flagga för objekt tillgänglig

Flaggan objekt available är inställd på 1 om objektets register post är tillgänglig. Annars, om värdet inte är 1, är objekt register posten inte tillgänglig. Observera att posten fortfarande kan innehålla giltig information trots att den är tillgänglig.

### <a name="object-entry-type"></a>Objekt post typ

Objekt post typen identifierar objekt typen i den här posten. Följande är en lista över giltiga objekt typer:

| **Värde** | **Objekt typ** |
|---------- | --------------- |
| 0         | Ogiltig       |
| 1         | Trådtoken          |
| 2         | Timer |
| 3         | Kö |
| 4         | Semafor |
| 5         | Mutex |
| 6         | Händelse flaggor grupp |
| 7         | Blockera pool |
| 8         | Byte-pool |
| 9         | .. /media |
| 10        | Fil |
| 11        | IP-adress |
| 12        | Paketets pool |
| 13        | TCP-socket |
| 14        | UDP-socket |
| 15-20     | Reserverat |  
| 21        | USB-värd, stack enhet |
| 22        | Gränssnitt för stack för USB-värd |
| 23        | Slut punkt för USB-värd |
| 24        | USB-värd klass |
| 25        | USB-enhet |
| 26        | USB-enhets gränssnitt |
| 27        | USB-enhetens slut punkt |
| 28        | USB-enhets klass |

### <a name="object-pointer"></a>Objekt pekare

Objekt pekaren anger objekt adressen som används för att komma åt objektet med ThreadX-API: et.

### <a name="object-reserved-fields"></a>Objekt reserverade fält

För alla objekt utom trådar ska dessa reserverade fält vara 0. För trådar placeras Trådens prioritet vid den tidpunkt som den anges i registret i dessa två reserverade fält.

### <a name="object-parameters"></a>Objekt parametrar

Objekt parametrarna innehåller kompletterande information om objektet. Följande beskriver kompletterande information för varje ThreadX-objekt:

| **Objekt typ**        | **Parameter 1**  | **Parameter 2** |
|----------------------- | ---------------- | --------------- |
| Trådtoken                 | Stack start      | Stack storlek |
| Timer                  | Inledande Tick | Ändra schema för Tick |
| Kö                  | Kös Tor lek | Meddelande storlek |
| Semafor              | Ursprungliga instanser | - |
| Mutex                  | Arvs flagga | - |
| Händelse flaggor grupp      | - | - |
| Blockera pool             | Totalt antal block | Blockstorlek |
| Byte-pool              | Totalt antal byte | - |
| .. /media                  | Storlek på fat-cache | Cachestorlek för sektor |
| Fil                   | - | - |
| IP-adress                     | Stack start | Stack storlek |
| Paketets pool            | Paket storlek | Antal paket |
| TCP-socket             | IP-adress | Fönster storlek |
| UDP-socket             | IP-adress | Max för RX-kö |

### <a name="object-name"></a>Objekt namn

Objekt namnet innehåller namnet på ThreadX-objektet. Namnet är det namn som angavs för ThreadX vid den tidpunkt då objektet skapades. Som standard har objekt namnet högst 32 tecken. Faktiska namn som är större än 32 tecken trunkeras.

## <a name="event-trace-entries"></a>Händelse spårnings poster

Händelse spårnings posterna finns i den nedre delen av bufferten för händelse spårning. Posterna bevaras i en cirkulär lista, och den aktuella post markören pekar på den äldsta posten. Antalet poster i listan beräknas av ***tx_trace_enable*** anropet.

Varje objekt register post innehåller information om en enskild spårnings händelse för ThreadX. Följande data struktur definierar varje spårnings händelse post:

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

Tråd pekaren innehåller adressen till tråden som körs vid tidpunkten för den här händelsen. Om händelsen inträffade under initieringen (ingen tråd körs), är värdet för den här visaren 0xF0F0F0F0. Om händelsen inträffade under en avbrotts tjänst rutin (ISR) är värdet för den här pekaren 0xFFFFFFFF. Om posten inte har använts än, är värdet för den här pekaren 0.

### <a name="thread-priority"></a>Tråd prioritet

Fältet tråd prioritet innehåller tråd prioriteten och avstängningen för den tråd som kördes vid tidpunkten för den här händelsen. Om det finns en avbrotts kontext (tråd pekare är 0xFFFFFFFF) är värdet för det här fältet inte prioritet utan i stället värdet för ***_tx_thread_current_ptr*** vid tidpunkten för händelsen. Annars är värdet för det här fältet 0.

### <a name="event-id"></a>Händelse-ID

Händelse-ID: t anger händelsen som ägde rum. Giltigt ID för spårnings händelse för ThreadX-spårning från 1 till 1024. Värden som börjar på 1025 och senare är reserverade för användarspecifika händelser. Den fullständiga definitionen av ThreadX-händelse-ID: n finns i filen ***tx_trace. h*** .</td>

### <a name="information-fields-1-4"></a>Informations fält (1-4)

Informations fälten innehåller ytterligare information om den aktuella händelsen. En fullständig beskrivning av informations fälten för varje definierat ThreadX händelse-ID finns i filen ***tx_trace. h*** .