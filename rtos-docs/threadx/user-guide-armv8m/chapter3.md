---
title: Kapitel 3 – ThreadX-API:er för ARMv8-M
description: Det här kapitlet innehåller en beskrivning av de ARMv8-M-specifika ThreadX-tjänsterna.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99633db55a5d93eb32ce4fb5429f3fe2f9ab5137cffc30b27982f702cece1ca5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791507"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a>Kapitel 3 ThreadX-API:er för ARMv8-M

Det här kapitlet innehåller en beskrivning av de ARMv8-M-specifika ThreadX-tjänsterna i alfabetisk ordning. Deras namn är utformade så att alla liknande tjänster grupperas tillsammans. I avsnittet "Returvärden" i följande beskrivningar påverkas inte värden i **BOLD** av den TX_DISABLE_ERROR_CHECKING **som** används för att inaktivera API-felkontroll. medan värden som visas i icke-fetstil är helt inaktiverade.

- [tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Allokera en trådstack i säkert minne.
- [tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Fri trådstack i säkert minne

## <a name="tx_thread_secure_stack_allocate"></a>tx_thread_secure_stack_allocate

Allokera en trådstack i säkert minne.

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a>Description

Den här tjänsten allokerar en stack med stack_size byte i säkert minne. Den här funktionen ska anropas för varje tråd som anropar säkra funktioner.

### <a name="input-parameters"></a>Indataparametrar

- **thread_ptr** Pekare till tidigare skapad tråd.

- **stack_size** Storleken på en säker stack.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad begäran.

- **TX_SIZE_ERROR** (0x05) Stackstorlek utanför intervallet.

- **TX_THREAD_ERROR** (0x0E) Ogiltig tråd pekare.

- **TX_NO_MEMORY** (0x10) Det går inte att allokera minne.

- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades för att köras i säkert läge.

### <a name="allowed-from"></a>Tillåts från

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

Frigör en trådstack i säkert minne. 

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

Den här tjänsten frigör en tråds säkra stack i skyddat minne. Den här funktionen ska anropas om en tråd har en säker stack och när tråden inte längre behöver anropa säkra funktioner eller om tråden tas bort.

### <a name="input-parameters"></a>Indataparametrar

- **thread_ptr** Pekare till tidigare skapad tråd.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad begäran.

- **TX_THREAD_ERROR** (0x0E) Ogiltig tråd pekare.

- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades för att köras i säkert läge.

### <a name="allowed-from"></a>Tillåts från

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
