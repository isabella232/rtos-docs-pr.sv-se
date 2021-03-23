---
title: Kapitel 5 – generera spårnings-buffertar
description: Det här kapitlet innehåller en beskrivning av hur du skapar en Azure återställnings tider TraceX-händelsehubben och beskriver även det underliggande formatet för bufferten.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: f296137d23b9f3c1c4fd115947bb50a32b768123
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827522"
---
# <a name="chapter-5---generating-trace-buffers"></a>Kapitel 5 – generera spårnings-buffertar

Det här kapitlet innehåller en beskrivning av hur du skapar en Azure återställnings tider TraceX-händelsehubben och beskriver även det underliggande formatet för bufferten.

## <a name="threadx-event-trace-support"></a>Stöd för ThreadX Event trace

ThreadX tillhandahåller inbyggt stöd för spårning av händelser för alla ThreadX-tjänster, ändringar i tråd tillstånd och användardefinierade händelser. ThreadX Event – trace-funktionen har främst utformats som ett efter slakt verktyg för att analysera de senaste "n"-aktiviteterna i programmet. Med hjälp av den här informationen kan utvecklaren upptäcka problem och/eller potentiella optimerings mål.

TraceX visar den buffert för händelse spårning som skapats av ThreadX. Följande beskriver hur du skapar bufferten och beskriver buffertens underliggande format.

## <a name="enabling-event-trace"></a>Aktivera händelse spårning

Om du vill aktivera händelse spårning definierar du tids stämplings konstanterna, skapar ThreadX-biblioteket med **TX_ENABLE_EVENT_TRACE** definierat och aktiverar spårning genom att anropa funktionen **tx_trace_enable** .

## <a name="defining-time-stamp-constants"></a>Definiera Time-Stamp konstanter

Konstanterna för tidsstämpel är utformade för att ge utvecklare kontrollen över den tids stämpling som används i händelse spårnings posterna. De två konstanterna för tidsstämpel och deras standardvärden är följande:

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

Ovanstående konstanter definieras i **tx_port. h** och skapar en "falsk" tidstämpel som bara ökar med en för varje händelse. Följande är ett exempel på en faktisk tidsstämpel-definition:

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

Ovanstående konstanter anger en 32-bitars timer som hämtas genom att läsa adressen 0x13000004. De flesta programspecifika tidsstämplar bör konfigureras på liknande sätt.

## <a name="exporting-the-trace-buffer"></a>Exportera den sökta kommandobufferten

TraceX kräver en spårningssession i ett binärt, Intel HEX eller Motorola S-Record-filformat på värden. Det enklaste sättet att göra detta är att stoppa målet och instruera fel söknings programmet att dumpa det minnes utrymme som du angav för att ***tx_trace_enable*** funktionen i en fil på värden.

> [!WARNING]
>***Var noga med att inte stoppa målet i själva spårnings insamlings koden. Om du gör det kan det orsaka ogiltig spårnings information. Om programmet har stoppats i ThreadX, är det bäst att stega över alla spårnings infognings makron innan du påsöker en spårnings-buffert.***

> [!IMPORTANT]
> *Bilaga D visar hur du dumpar spårningssessionen från en rad olika utvecklingsverktyg.*

## <a name="extended-event-trace-api"></a>API för utökad händelse spårning

När ThreadX har skapats med **TX_ENABLE_EVENT_TRACE** definierat, är följande nya API: er för Event trace tillgängliga för programmet:

- tx_trace_enable: *Aktivera händelse spårning*
- tx_trace_event_filter: *filtrera angivna händelse (er)*
- tx_trace_event_unfilter: *avfiltrera angivna händelse (er)*
- tx_trace_disable: *inaktivera händelse spårning*
- tx_trace_isr_enter_insert: *Infoga ISR ange spårnings händelse*
- tx_trace_isr_exit_insert: *Infoga ISR-avsluta spårnings händelse*
- tx_trace_buffer_full_notify: *Registrera fullständig program återanrop i spårnings buffert*
- tx_trace_user_event_insert: *Infoga användar händelse*

### <a name="tx_trace_enable"></a>tx_trace_enable

Aktivera händelse spårning

#### <a name="prototype"></a>Prototyp

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a>Beskrivning
Den här tjänsten aktiverar händelse spårning i ThreadX. Den sökta bufferten och det maximala antalet ThreadX-objekt tillhandahålls av programmet.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.

#### <a name="input-parameters"></a>Indataparametrar

- **trace_buffer_start**: pekar mot början av den användarspecifika spårningssessionen.
- **trace_buffer_size**: det totala antalet byte i minnet för den sökta kommandobufferten. Ju större kommandobufferten, desto fler poster kan de lagra.
- **registry_entries**: antalet program ThreadX objekt som ska behållas i spårnings registret. Registret används för att korrelera objekt adresser med objekt namn. Detta är mycket användbart för verktyg för spårnings analys av GUI.

#### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0x00) aktive ras spårning av händelse spårning.
- Den angivna storleken för 0x05 () är för liten. **TX_SIZE_ERROR** Det måste vara tillräckligt stort för spårnings huvudet, objekt registret och minst en spårnings post.
- **TX_NOT_DONE** (0X20) händelse spårning har redan Aktiver ATS.
- **TX_FEATURE_NOT_ENABLED** (0xFF)-systemet kompilerades inte med spårning aktiverat.

#### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

#### <a name="example"></a>Exempel

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a>Se även

tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_event_filter"></a>tx_trace_event_filter

Filtrera angivna händelser

#### <a name="prototype"></a>Prototyp

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a>Beskrivning

Den här tjänsten filtrerar den eller de angivna händelserna från att infogas i den aktiva spårningssessionen. Observera att standardinställningen inga händelser filtreras efter att *tx_trace_enable* anropas.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.

#### <a name="input-parameters"></a>Indataparametrar

- **event_filter_bits**: bitar som motsvarar händelser att filtrera. Flera händelser kan filtreras genom att helt enkelt Oring lämpliga konstanter. Giltiga konstanter för den här variabeln definieras enligt följande:

```c
TX_TRACE_ALL_EVENTS                   0x000007FF
TX_TRACE_INTERNAL_EVENTS              0x00000001
TX_TRACE_BLOCK_POOL_EVENTS            0x00000002
TX_TRACE_BYTE_POOL_EVENTS             0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS           0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT      0x00000010
TX_TRACE_MUTEX_EVENTS                 0x00000020
TX_TRACE_QUEUE_EVENTS                 0x00000040
TX_TRACE_SEMAPHORE_EVENTS             0x00000080
TX_TRACE_THREAD_EVENTS                0x00000100
TX_TRACE_TIME_EVENTS                  0x00000200
TX_TRACE_TIMER_EVENTS                 0x00000400
FX_TRACE_ALL_EVENTS                   0x00007800
FX_TRACE_INTERNAL_EVENTS              0x00000800
FX_TRACE_MEDIA_EVENTS                 0x00001000
FX_TRACE_DIRECTORY_EVENTS             0x00002000
FX_TRACE_FILE_EVENTS                  0x00004000
NX_TRACE_ALL_EVENTS                   0x00FF8000
NX_TRACE_INTERNAL_EVENTS              0x00008000
NX_TRACE_ARP_EVENTS                   0x00010000
NX_TRACE_ICMP_EVENTS                  0x00020000
NX_TRACE_IGMP_EVENTS                  0x00040000
NX_TRACE_IP_EVENTS                    0x00080000
NX_TRACE_PACKET_EVENTS                0x00100000
NX_TRACE_RARP_EVENTS                  0x00200000
NX_TRACE_TCP_EVENTS                   0x00400000
NX_TRACE_UDP_EVENTS                   0x00800000
UX_TRACE_ALL_EVENTS                   0x7F000000
UX_TRACE_ERRORS                       0x01000000
UX_TRACE_HOST_STACK_EVENTS            0x02000000
UX_TRACE_DEVICE_STACK_EVENTS          0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS       0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS     0x10000000
UX_TRACE_HOST_CLASS_EVENTS            0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS          0x40000000
```

#### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0x00) händelse filter har slutförts.
- **TX_FEATURE_NOT_ENABLED** (0xFF)-systemet kompilerades inte med spårning aktiverat.

#### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

#### <a name="example"></a>Exempel

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a>Se även

tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_event_unfilter"></a>tx_trace_event_unfilter

Filtrera angivna händelser

#### <a name="prototype"></a>Prototyp

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a>Beskrivning

Den här tjänsten avfiltrerar den eller de angivna händelse (er) som de ska infogas i den aktiva spårningssessionen.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.

#### <a name="input-parameters"></a>Indataparametrar

- **event_unfilter_bits**: bitar som motsvarar händelser som ska avfiltreras. Flera händelser kan avfiltreras genom att enkelt eller genom att kombinera lämpliga konstanter. Giltiga konstanter för den här variabeln definieras enligt följande:

```c
TX_TRACE_ALL_EVENTS                  0x000007FF
TX_TRACE_INTERNAL_EVENTS             0x00000001
TX_TRACE_BLOCK_POOL_EVENTS           0x00000002
TX_TRACE_BYTE_POOL_EVENTS            0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS          0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT     0x00000010
TX_TRACE_MUTEX_EVENTS                0x00000020
TX_TRACE_QUEUE_EVENTS                0x00000040
TX_TRACE_SEMAPHORE_EVENTS            0x00000080
TX_TRACE_THREAD_EVENTS               0x00000100
TX_TRACE_TIME_EVENTS                 0x00000200
TX_TRACE_TIMER_EVENTS                0x00000400
FX_TRACE_ALL_EVENTS                  0x00007800
FX_TRACE_INTERNAL_EVENTS             0x00000800
FX_TRACE_MEDIA_EVENTS                0x00001000
FX_TRACE_DIRECTORY_EVENTS            0x00002000
FX_TRACE_FILE_EVENTS                 0x00004000
NX_TRACE_ALL_EVENTS                  0x00FF8000
NX_TRACE_INTERNAL_EVENTS             0x00008000
NX_TRACE_ARP_EVENTS                  0x00010000
NX_TRACE_ICMP_EVENTS                 0x00020000
NX_TRACE_IGMP_EVENTS                 0x00040000
NX_TRACE_IP_EVENTS                   0x00080000
NX_TRACE_PACKET_EVENTS               0x00100000
NX_TRACE_RARP_EVENTS                 0x00200000
NX_TRACE_TCP_EVENTS                  0x00400000
NX_TRACE_UDP_EVENTS                  0x00800000
UX_TRACE_ALL_EVENTS                  0x7F000000
UX_TRACE_ERRORS                      0x01000000
UX_TRACE_HOST_STACK_EVENTS           0x02000000
UX_TRACE_DEVICE_STACK_EVENTS         0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS      0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS    0x10000000
UX_TRACE_HOST_CLASS_EVENTS           0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS         0x40000000
```

#### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0x00) händelse Avfiltrering slutfördes.
- **TX_FEATURE_NOT_ENABLED** (0xFF)-systemet kompilerades inte med spårning aktiverat.

#### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

#### <a name="example"></a>Exempel

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a>Se även

tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_disable"></a>tx_trace_disable

#### <a name="disable-event-tracing"></a>Inaktivera händelse spårning

#### <a name="prototype"></a>Prototyp

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar händelse spårning i ThreadX. Detta kan vara användbart om programmet vill låsa den aktuella bufferten för händelse spårning och eventuellt transportera den externt under körnings tillfället. När den är inaktive rad kan **tx_trace_enable** anropas för att börja spåra igen.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.

#### <a name="input-parameters"></a>Indataparametrar

Inga.

#### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0x00) inaktive ring av händelse spårning.
- Händelse spårning för **TX_NOT_DONE** (0x20) har inte Aktiver ATS.
- **TX_FEATURE_NOT_ENABLED** (0xFF)-systemet kompilerades inte med spårning aktiverat.

#### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

#### <a name="example"></a>Exempel 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a>Se även

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_isr_enter_insert"></a>tx_trace_isr_enter_insert

#### <a name="insert-isr-enter-event"></a>Infoga händelse för ISR-retur

#### <a name="prototype"></a>Prototyp

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a>Beskrivning

Den här tjänsten infogar ISR-händelsen retur i bufferten för händelse spårning. Den bör anropas av programmet i början av ISR-bearbetning. Den angivna parametern ska identifiera den specifika ISR för programmet.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.

#### <a name="input-parameters"></a>Indataparametrar 
- **isr_id**: Programspecifikt värde för att identifiera ISR.

#### <a name="return-values"></a>Retur värden

**Ingen**

#### <a name="allowed-from"></a>Tillåten från 

ISR: er

#### <a name="example"></a>Exempel

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a>Se även

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_isr_exit_insert"></a>tx_trace_isr_exit_insert

#### <a name="insert-isr-exit-event"></a>Infoga ISR-avsluts händelse

#### <a name="prototype"></a>Prototyp

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a>Beskrivning

Den här tjänsten infogar händelsen ISR-post i kommandobufferten. Den bör anropas av programmet i början av ISR-bearbetning. Den angivna parametern ska identifiera ISR till programmet.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.

#### <a name="input-parameters"></a>Indataparametrar 

- **isr_id**: Programspecifikt värde för att identifiera ISR.

#### <a name="return-values"></a>Retur värden

**Ingen**

#### <a name="allowed-from"></a>Tillåten från

ISR: er

#### <a name="example"></a>Exempel

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a>Se även

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_buffer_full_notify"></a>tx_trace_buffer_full_notify

#### <a name="register-trace-buffer-full-application-callback"></a>Registrera fullständig motringning för spårnings buffert

#### <a name="prototype"></a>Prototyp

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a>Beskrivning

Den här tjänsten registrerar en återanrops funktion för program som anropas av ThreadX när spårnings-bufferten blir full. Programmet kan sedan välja att inaktivera spårning och/eller eventuellt konfigurera en ny spårnings-buffert.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.

#### <a name="input-parameters"></a>Indataparametrar

- **full_buffer_callback**: program funktion som anropas när kommandobufferten är full. Värdet NULL inaktiverar återanropet av meddelandet.

#### <a name="return-values"></a>Retur värden

**Ingen**

#### <a name="allowed-from"></a>Tillåten från

ISR: er

#### <a name="example"></a>Exempel

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a>Se även

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert

### <a name="tx_trace_user_event_insert"></a>tx_trace_user_event_insert

#### <a name="insert-user-event"></a>Infoga användar händelse

#### <a name="prototype"></a>Prototyp

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a>Beskrivning

Den här tjänsten infogar användar händelsen i den sökta bufferten. Användar händelse-ID: n måste vara större än konstanten **TX_TRACE_USER_EVENT_START**, som definieras som 4096. Den maximala användar händelsen definieras av konstant **TX_TRACE_USER_EVENT_END**, som definieras som 65535. Alla händelser inom det här intervallet är tillgängliga för programmet. Informations fälten är programspecifika.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.

#### <a name="input-parameters"></a>Indataparametrar

- **event_id**: identifiering av programspecifik händelse och måste börja vara större än **TX_TRACE_USER_EVENT_START** och mindre än eller lika med **TX_TRACE_USER_EVENT_END**.
- **info_field_1**: programspecifikt informations fält.
- **info_field_2**: programspecifikt informations fält.
- **info_field_3**: programspecifikt informations fält.
- **info_field_4**: programspecifikt informations fält.

#### <a name="return-values"></a>Retur värden
- **TX_SUCCESS** (0x00) användar händelsen infogades.
- Händelse spårning för **TX_NOT_DONE** (0x20) har inte Aktiver ATS.
- **TX_FEATURE_NOT_ENABLED** (0xFF) systemet kompilerades inte med spårning aktiverat.

#### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

#### <a name="example"></a>Exempel

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a>Se även

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify