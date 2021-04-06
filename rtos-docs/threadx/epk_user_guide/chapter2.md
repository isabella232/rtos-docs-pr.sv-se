---
title: Kapitel 2 – API-referenser för körnings profil paket
description: I det här kapitlet dokumenteras de API-funktioner som tillhandahålls av EPK.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a198e48bdacbc141fb3de4670cc7ea5ba079612d
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377633"
---
#  <a name="chapter-2--execution-profile-kit-api-references"></a>Kapitel 2 API-referenser för körnings profil paket

ThreadX-EPK ger till gång till funktioner för att hämta körnings profil informationen, enligt följande.

| Funktions &nbsp; namn | Beskrivning |
| --- | --- |
| _tx_execution_thread_time_reset | Återställ den ackumulerade tiden för en tråd. |
| _tx_execution_thread_total_time_reset | Återställ den ackumulerade totala tråd tiden. |
| _tx_execution_isr_time_reset | Återställ den ackumulerade ISR-tiden. |
| _tx_execution_idle_time_reset | Återställ den ackumulerade inaktiva tiden. |
| _tx_execution_thread_time_get hämta den ackumulerade tiden för en tråd. |
| _tx_execution_thread_total_time_get | Hämta den ackumulerade total tråd tiden. |
| _tx_execution_isr_time_get | Hämta den ackumulerade ISR-tiden. |
| _tx_execution_idle_time_get | Hämta den ackumulerade inaktiva tiden. |

##  <a name="_tx_execution_thread_time_reset"></a>_tx_execution_thread_time_reset

Återställ den ackumulerade tiden för en tråd.

### <a name="prototype"></a>Prototyp

```C
UINT _tx_execution_thread_time_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger den ackumulerade tråd körnings tiden tillbaka till noll.

### <a name="input-parameters"></a>Indataparametrar

- **thread_ptr** Pekare till tråd.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0X00) lyckades EPK-återställning.

### <a name="allowed-from"></a>Tillåten från

Trådar, timers och ISR: er

### <a name="example"></a>Exempel

```c
/* Reset the execution time for thread_0.  */
status =  tx_execution_thread_time_reset(&thread_0);

/* If status is TX_SUCCESS thread_0's execution time is now 0.  */
```

### <a name="see-also"></a>Se även

- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_thread_total_time_reset"></a>_tx_execution_thread_total_time_reset

Återställ den totala ackumulerade tråd tiden.

### <a name="prototype"></a>Prototyp
```c
UINT _tx_execution_thread_total_time_reset(void);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger den ackumulerade totala körnings tiden för trådar tillbaka till noll.

### <a name="input-parameters"></a>Indataparametrar

Inga.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0X00) lyckades EPK-återställning.

### <a name="allowed-from"></a>Tillåten från

- Trådar, timers och ISR: er

### <a name="example"></a>Exempel

```c
/* Reset the total execution time for all threads.  */
status =  tx_execution_thread_total_time_reset();

/* If status is TX_SUCCESS the total thread execution time is now 0.  */
```

### <a name="see-also"></a>Se även

- _tx_execution_thread_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_isr_time_reset"></a>_tx_execution_isr_time_reset

Återställ den ackumulerade ISR-tiden.

### <a name="prototype"></a>Prototyp

```c
UINT _tx_execution_isr_time_reset(void);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger ackumulerad total ISR-körnings tid tillbaka till noll.

### <a name="input-parameters"></a>Indataparametrar

Inga.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0X00) lyckades EPK-återställning.

**Tillåten från**

- Trådar, timers och ISR: er

**Exempel**

```c
/* Reset the total ISR execution time.  */
status =  tx_execution_isr_time_reset();

/* If status is TX_SUCCESS the total ISR execution time is now 0.  */
```

### <a name="see-also"></a>Se även

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_idle_time_reset"></a>_tx_execution_idle_time_reset

Återställ den ackumulerade inaktiva tiden.

### <a name="prototype"></a>Prototyp

```c
UINT _tx_execution_idle_time_reset(void);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger den ackumulerade totala inaktiva körnings tiden tillbaka till noll.

### <a name="input-parameters"></a>Indataparametrar

Inga.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0X00) lyckades EPK-återställning.

### <a name="allowed-from"></a>Tillåten från

- Trådar, timers och ISR: er

### <a name="example"></a>Exempel

```c
/* Reset the total idle execution time.  */
status =  tx_execution_idle_time_reset();

/* If status is TX_SUCCESS the total idle execution time is now 0.  */
```

### <a name="see-also"></a>Se även

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_thread_time_get"></a>_tx_execution_thread_time_get

Hämta den ackumulerade tiden för en tråd.

### <a name="prototype"></a>Prototyp

```c
UINT _tx_execution_thread_time_get(
    TX_THREAD *thread_ptr,
    EXECUTION_TIME *total_time);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den ackumulerade körnings tiden för en tråd.

### <a name="input-parameters"></a>Indataparametrar

- **thread_ptr** Pekare till tråd.

- **total_time** Målet för trådens \' körnings tid.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0X00) lyckades EPK Time get.

### <a name="allowed-from"></a>Tillåten från

Trådar, timers och ISR: er

### <a name="example"></a>Exempel

```c

/* Get the total thread execution time for thread_0.  */
status =  tx_execution_thread_time_get(&thread_0, &execution_time);

/* If status is TX_SUCCESS, execution_time contains the thread's
   execution time.  */
```

### <a name="see-also"></a>Se även

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_thread_total_time_get"></a>_tx_execution_thread_total_time_get

Hämta den ackumulerade trådens sammanlagda tid.

### <a name="prototype"></a>Prototyp

```c
UINT _tx_execution_thread_total_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den ackumulerade total körnings tiden för tråden.

### <a name="input-parameters"></a>Indataparametrar

- **total_time** Mål för total körnings tid för tråd.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0X00) lyckades EPK Time get.

### <a name="allowed-from"></a>Tillåten från

- Trådar, timers och ISR: er

### <a name="example"></a>Exempel

```c
EXECUTION_TIME *execution_time;

/* Get the total thread execution time.  */
status =  tx_execution_thread_total_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the thread
   execution time.  */
```

### <a name="see-also"></a>Se även

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_isr_time_get"></a>_tx_execution_isr_time_get

Hämta den ackumulerade ISR-tiden.

### <a name="prototype"></a>Prototyp

```c
UINT _tx_execution_isr_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den ackumulerade ISR-körnings tiden.

### <a name="input-parameters"></a>Indataparametrar

- **total_time** Mål för total ISR-körnings tid.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0X00) lyckades EPK Time get.

### <a name="allowed-from"></a>Tillåten från

Trådar, timers och ISR: er

### <a name="example"></a>Exempel

```c
EXECUTION_TIME  *execution_time;

/* Get the total ISR execution time.  */
status =  tx_execution_isr_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the ISR
   execution time.  */
```

### <a name="see-also"></a>Se även

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_idle_time_get"></a>_tx_execution_idle_time_get

### <a name="get-the-accumulated-idle-time"></a>Hämta den ackumulerade inaktiva tiden

### <a name="prototype"></a>Prototyp

```c
UINT _tx_execution_idle_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den ackumulerade körnings tiden för inaktivitet.

### <a name="input-parameters"></a>Indataparametrar

- **total_time** Mål för total körnings tid för inaktivitet.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0X00) lyckades EPK Time get.

### <a name="allowed-from"></a>Tillåten från

- Trådar, timers och ISR: er

### <a name="example"></a>Exempel

```c
EXECUTION_TIME  *execution_time;

/* Get the total idle execution time.  */
status =  tx_execution_idle_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the idle
   execution time.  */
```

### <a name="see-also"></a>Se även

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
