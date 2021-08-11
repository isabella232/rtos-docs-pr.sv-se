---
title: Kapitel 5 – Generera spårningsbuffertar
description: Det här kapitlet innehåller en beskrivning av hur du skapar en Azure RTOS TraceX-händelsebuffert och beskriver även buffertens underliggande format.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 7d5c90675728fc7e374d625f5a9ae27340268ca8398200c68fb7113a84aa2983
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801792"
---
# <a name="chapter-5---generating-trace-buffers"></a>Kapitel 5 – Generera spårningsbuffertar

Det här kapitlet innehåller en beskrivning av hur du skapar en Azure RTOS TraceX-händelsebuffert och beskriver även buffertens underliggande format.

## <a name="threadx-event-trace-support"></a>Stöd för Händelsespårning i ThreadX

ThreadX har inbyggt stöd för händelsespårning för alla ThreadX-tjänster, ändringar av trådtillstånd och användardefinierade händelser. Händelsespårningsfunktionerna i ThreadX är främst utformade som ett verktyg för efteranalys för att analysera de senaste "n"-aktiviteterna i programmet. Med den här informationen kan utvecklaren upptäcka problem och/eller potentiella optimeringsmål.

TraceX visar grafiskt händelsespårningsbufferten som skapats av ThreadX. Följande beskriver hur du skapar bufferten och beskriver buffertens underliggande format.

## <a name="enabling-event-trace"></a>Aktivera händelsespårning

Om du vill aktivera händelsespårning definierar du tidsstämpelkonstanterna, skapar ThreadX-biblioteket **med TX_ENABLE_EVENT_TRACE** definierat och aktiverar spårning genom att **anropa tx_trace_enable-funktionen.**

## <a name="defining-time-stamp-constants"></a>Definiera Time-Stamp konstanter

Tidsstämpelkonstanterna är utformade för att ge utvecklaren kontroll över den tidsstämpel som används i händelsespårningsposterna. De två tidsstämpelkonstanterna och deras standardvärden är följande:

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

Ovanstående konstanter definieras i **tx_port.h** och skapar en "falsk" tidsstämpel som bara ökar med en för varje händelse. Följande är ett exempel på en faktisk tidsstämpeldefinition:

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

Ovanstående konstanter anger en 32-bitars timer som hämtas genom att läsa adressen 0x13000004. De flesta programspecifika tidsstämplar bör konfigureras på liknande sätt.

## <a name="exporting-the-trace-buffer"></a>Exportera spårningsbufferten

TraceX behöver spårningsbufferten i ett binärt format, Intel HEX eller Samsung S-Record-filformat på värden. Det enklaste sättet att åstadkomma detta är att stoppa målet och instruera felsökningsprogrammet att dumpa det minnesområde som du angav ***för att tx_trace_enable*** till en fil på värden.

> [!WARNING]
>***Var noga med att inte stoppa målet i själva spårningssamlingskoden. Detta kan orsaka ogiltig spårningsinformation. Om programmet stoppas i ThreadX är det bäst att gå igenom ett makro för att infoga spårning innan spårningsbufferten dumpas.***

> [!IMPORTANT]
> *Bilaga D visar hur du dumpar spårningsbufferten från en mängd olika utvecklingsverktyg.*

## <a name="extended-event-trace-api"></a>Extended Event Trace API

När ThreadX har skapats med **TX_ENABLE_EVENT_TRACE** definieras är följande nya händelsespårnings-API:er tillgängliga för programmet:

- tx_trace_enable: Aktivera *händelsespårning*
- tx_trace_event_filter: *Filtrera angivna händelser*
- tx_trace_event_unfilter: *Ofiltrera angivna händelser*
- tx_trace_disable: Inaktivera *händelsespårning*
- tx_trace_isr_enter_insert: Infoga *ISR ange spårningshändelse*
- tx_trace_isr_exit_insert: Infoga *isr-avslutsspårningshändelse*
- tx_trace_buffer_full_notify: Registrera *spårningsbuffert med fullständigt programanrop*
- tx_trace_user_event_insert: Infoga *användarhändelse*

### <a name="tx_trace_enable"></a>tx_trace_enable

Aktivera händelsespårning

#### <a name="prototype"></a>Prototyp

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a>Description
Den här tjänsten aktiverar händelsespårning i ThreadX. Spårningsbufferten och det maximala antalet ThreadX-objekt tillhandahålls av programmet.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste byggas med **TX_ENABLE_EVENT_TRACE** definieras för att kunna använda händelsespårning.

#### <a name="input-parameters"></a>Indataparametrar

- **trace_buffer_start:** Pekare till början av den spårningsbuffert som användaren angav.
- **trace_buffer_size:** Totalt antal byte i minnet för spårningsbufferten. Ju större spårningsbuffert, desto fler poster kan den lagra.
- **registry_entries:** Antal ThreadX-programobjekt som ska behållas i spårningsregistret. Registret används för att korrelera objektadresser med objektnamn. Detta är mycket användbart för GUI-spårningsanalysverktyg.

#### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Aktivera lyckad händelsespårning.
- **TX_SIZE_ERROR** (0x05) Den angivna spårningsbuffertstorleken är för liten. Det måste vara tillräckligt stort för spårningsrubriken, objektregistret och minst en spårningspost.
- **TX_NOT_DONE** (0x20) Händelsespårning har redan aktiverats.
- **TX_FEATURE_NOT_ENABLED** (0xFF) System kompilerades inte med spårning aktiverat.

#### <a name="allowed-from"></a>Tillåts från

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

#### <a name="description"></a>Description

Den här tjänsten filtrerar angivna händelser från att infogas i den aktiva spårningsbufferten. Observera att inga händelser filtreras som standard när *tx_trace_enable* anropas.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste byggas med **TX_ENABLE_EVENT_TRACE** definieras för att kunna använda händelsespårning.

#### <a name="input-parameters"></a>Indataparametrar

- **event_filter_bits:** Bitar som motsvarar händelser som ska filtreras. Flera händelser kan filtreras genom att helt enkelt eller tillsammans koppla ihop lämpliga konstanter. Giltiga konstanter för den här variabeln definieras på följande sätt:

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

#### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Filtret Lyckades.
- **TX_FEATURE_NOT_ENABLED** (0xFF) System kompilerades inte med spårning aktiverat.

#### <a name="allowed-from"></a>Tillåts från

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

Ofiltrera angivna händelser

#### <a name="prototype"></a>Prototyp

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a>Description

Den här tjänsten avfiltrerar de angivna händelse(erna) så att de infogas i den aktiva spårningsbufferten.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste byggas med **TX_ENABLE_EVENT_TRACE** definieras för att kunna använda händelsespårning.

#### <a name="input-parameters"></a>Indataparametrar

- **event_unfilter_bits:** Bitar som motsvarar händelser som ofiltrerar. Flera händelser kan vara ofiltrerade genom att helt enkelt eller tillsammans koppla ihop lämpliga konstanter. Giltiga konstanter för den här variabeln definieras på följande sätt:

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

#### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad händelse ofiltrera.
- **TX_FEATURE_NOT_ENABLED** (0xFF) System kompilerades inte med spårning aktiverat.

#### <a name="allowed-from"></a>Tillåts från

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

#### <a name="disable-event-tracing"></a>Inaktivera händelsespårning

#### <a name="prototype"></a>Prototyp

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a>Description

Den här tjänsten inaktiverar händelsespårning i ThreadX. Detta kan vara användbart om programmet vill låsa den aktuella händelsespårningsbufferten och eventuellt transportera den externt under körning. När den har **inaktiverats kan tx_trace_enable** anropas för att börja spåra igen.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste byggas **TX_ENABLE_EVENT_TRACE** definieras för att du ska kunna använda händelsespårning.

#### <a name="input-parameters"></a>Indataparametrar

Inga.

#### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad händelsespårning inaktiveras.
- **TX_NOT_DONE** (0x20) Händelsespårning har inte aktiverats.
- **TX_FEATURE_NOT_ENABLED** (0xFF) System kompilerades inte med spårning aktiverat.

#### <a name="allowed-from"></a>Tillåts från

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

#### <a name="insert-isr-enter-event"></a>Infoga ISR Enter-händelse

#### <a name="prototype"></a>Prototyp

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a>Description

Den här tjänsten infogar ISR Enter-händelsen i händelsespårningsbufferten. Det bör anropas av programmet i början av ISR-bearbetningen. Den angivna parametern ska identifiera programmets specifika ISR.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste byggas **TX_ENABLE_EVENT_TRACE** definieras för att du ska kunna använda händelsespårning.

#### <a name="input-parameters"></a>Indataparametrar 
- **isr_id:** Programspecifikt värde för att identifiera ISR.

#### <a name="return-values"></a>Returvärden

**Ingen**

#### <a name="allowed-from"></a>Tillåts från 

Isrs

#### <a name="example"></a>Exempel

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a>Se även

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_isr_exit_insert"></a>tx_trace_isr_exit_insert

#### <a name="insert-isr-exit-event"></a>Infoga ISR-avslutshändelse

#### <a name="prototype"></a>Prototyp

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a>Description

Den här tjänsten infogar ISR-posthändelsen i händelsespårningsbufferten. Det bör anropas av programmet i början av ISR-bearbetningen. Den angivna parametern ska identifiera ISR för programmet.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste byggas **TX_ENABLE_EVENT_TRACE** definieras för att du ska kunna använda händelsespårning.

#### <a name="input-parameters"></a>Indataparametrar 

- **isr_id:** Programspecifikt värde för att identifiera ISR.

#### <a name="return-values"></a>Returvärden

**Ingen**

#### <a name="allowed-from"></a>Tillåts från

Isrs

#### <a name="example"></a>Exempel

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a>Se även

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_buffer_full_notify"></a>tx_trace_buffer_full_notify

#### <a name="register-trace-buffer-full-application-callback"></a>Registrera spårningsbuffert för fullständigt programanrop

#### <a name="prototype"></a>Prototyp

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a>Description

Den här tjänsten registrerar en återanropsfunktion för program som anropas av ThreadX när spårningsbufferten blir full. Programmet kan sedan välja att inaktivera spårning och/eller eventuellt konfigurera en ny spårningsbuffert.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste byggas **TX_ENABLE_EVENT_TRACE** definieras för att du ska kunna använda händelsespårning.

#### <a name="input-parameters"></a>Indataparametrar

- **full_buffer_callback:** Programfunktionen anropar när spårningsbufferten är full. Värdet NULL inaktiverar återanropet av meddelanden.

#### <a name="return-values"></a>Returvärden

**Ingen**

#### <a name="allowed-from"></a>Tillåts från

Isrs

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

#### <a name="insert-user-event"></a>Infoga användarhändelse

#### <a name="prototype"></a>Prototyp

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a>Description

Den här tjänsten infogar användarhändelsen i spårningsbufferten. Användarhändelse-ID måste vara större än **konstanten TX_TRACE_USER_EVENT_START**, som har definierats till 4096. Den maximala användarhändelsen definieras av **konstanten TX_TRACE_USER_EVENT_END**, som har definierats till 65535. Alla händelser inom det här intervallet är tillgängliga för programmet. Informationsfälten är programspecifika.

> [!IMPORTANT]
> ThreadX-biblioteket och programmet måste byggas **TX_ENABLE_EVENT_TRACE** definieras för att du ska kunna använda händelsespårning.

#### <a name="input-parameters"></a>Indataparametrar

- **event_id:** Programspecifik händelseidentifiering och måste börja vara **större än TX_TRACE_USER_EVENT_START** och mindre än eller lika med **TX_TRACE_USER_EVENT_END**.
- **info_field_1:** Programspecifikt informationsfält.
- **info_field_2:** Programspecifikt informationsfält.
- **info_field_3:** Programspecifikt informationsfält.
- **info_field_4:** Programspecifikt informationsfält.

#### <a name="return-values"></a>Returvärden
- **TX_SUCCESS** (0x00) Infogning av användarhändelse.
- **TX_NOT_DONE** (0x20) Händelsespårning är inte aktiverat.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med spårning aktiverat.

#### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

#### <a name="example"></a>Exempel

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a>Se även

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify