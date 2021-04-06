---
title: 'Kapitel 3 – ThreadX-API: er för ARMv8-M'
description: Det här kapitlet beskriver en beskrivning av ARMv8-M-Specific ThreadX-tjänsterna.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 14bdfab3d56476d52ba91f859cec4af4ab7f4bef
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377630"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a>Kapitel 3 ThreadX-API: er för ARMv8-M

Det här kapitlet innehåller en beskrivning av ARMv8-M-Specific ThreadX-tjänsterna i alfabetisk ordning. Deras namn är utformade så att alla liknande tjänster grupperas tillsammans. I avsnittet "retur värden" i följande beskrivningar påverkas inte värden i **fetstil** av **TX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-kontrollen. värden som visas i icke-fetstil är helt inaktiverade.

- [tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Allokera en tråds tack i säkert minne.
- [tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Fri tråds tack i säkert minne

## <a name="tx_thread_secure_stack_allocate"></a>tx_thread_secure_stack_allocate

Allokera en tråds tack i säkert minne.

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten allokerar en stack med storlek stack_size byte i säkert minne. Den här funktionen ska anropas för varje tråd som anropar säkra funktioner.

### <a name="input-parameters"></a>Indataparametrar

- **thread_ptr** Pekare till den tidigare skapade tråden.

- **stack_size** Storlek på säker stack.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0X00) lyckad begäran.

- **TX_SIZE_ERRORs** stackens storlek (0x05) är utanför intervallet.

- **TX_THREAD_ERROR** (0X0E) ogiltig tråd pekare.

- **TX_NO_MEMORY** (0X10) Det gick inte att allokera minne.

- **TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.

- **TX_FEATURE_NOT_ENABLED** (0xFF) systemet kompilerades för att köras i säkert läge.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a>Se även

tx_thread_secure_stack_free

##  <a name="tx_thread_secure_stack_free"></a>tx_thread_secure_stack_free

Frigör en tråds tack i säkert minne. 

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten frigör en tråds säkra stack i säkert minne. Den här funktionen ska anropas om en tråd har en säker stack och när tråden inte längre behöver anropa säkra funktioner eller om tråden tas bort.

### <a name="input-parameters"></a>Indataparametrar

- **thread_ptr** Pekare till den tidigare skapade tråden.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0X00) lyckad begäran.

- **TX_THREAD_ERROR** (0X0E) ogiltig tråd pekare.

- **TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.

- **TX_FEATURE_NOT_ENABLED** (0xFF) systemet kompilerades för att köras i säkert läge.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a>Se även

tx_thread_secure_stack_allocate
