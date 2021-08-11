---
title: Kapitel 4 – Modul-API:er
author: philmea
ms.author: philmea
description: Den här artikeln är en sammanfattning av de ytterligare API:er som är tillgängliga för en modul.
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1c7590d0ccddc606a6cacdfeb3b3a99631e125554b524c4ce65c8154e65a20ee
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799140"
---
# <a name="chapter-4---module-apis"></a>Kapitel 4 – Modul-API:er

## <a name="summary-of-module-apis"></a>Sammanfattning av modul-API:er

Det finns flera ytterligare API-funktioner som är tillgängliga för en modul, enligt följande:

- ***txm_module_application_request** _ – _Application specifik begäran till den tillhörande koden*
- ***txm_module_object_allocate** _ – _Allocate minne utanför modulen för objekt*
- ***txm_module_object_deallocate** _ – _Deallocate tidigare allokerat objektminne*
- ***txm_module_object_pointer_get** _ – _Find systemobjekt och hämta objekt pekare*
- ***txm_module_object_pointer_get_extended** _ – _Find systemobjekt och hämta objekt pekare, namnlängdssäkerhet*

## <a name="return-values"></a>Returvärden

Ytterligare felkoder returneras för vissa Azure RTOS API:er. Dessa ytterligare felkoder definieras på följande sätt:

- **TXM_MODULE_INVALID_PROPERTIES** (0xF3): Anger att modulen inte har rätt egenskaper för att göra ett API-anrop. Till exempel anropa spårnings-API:er i användarläge.
- **TXM_MODULE_INVALID_MEMORY** (0xF4): Anger att det minne som tillhandahålls av modulen är ogiltigt eller finns på en ogiltig plats. I minnesskyddade moduler tillåts till exempel inte objektkontrollblock finnas i minnet som modulen kan komma åt.
- **TXM_MODULE_INVALID_CALLBACK** (0xF5): Återanrop som anges i API:et ligger utanför intervallet för modulens kod och är därför ogiltigt.

---

## <a name="txm_module_application_request"></a>txm_module_application_request

Programspecifik begäran till kod som finns i den aktuella koden.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a>Description

Den här tjänsten gör den angivna begäran till den hemmavarande delen av programmet. Det förutsätts att begärandestrukturen förbereds före anropet. Den faktiska bearbetningen av begäran sker i den hemmaande koden i funktionen ***_txm_module_manager_application_request***. Som standard lämnas den här funktionen tom och är utformad för den lokala programutvecklaren att ändra.

### <a name="input-parameters"></a>Indataparametrar

- **begäran** Begärande-ID (definierat program)
- **param_1** Första parametern
- **param_2** Andra parametern
- **param_3** Tredje parametern

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad begäran.
- **TX_NOT_AVAILABLE** (0x1D) Begäran som inte stöds av den hemmavarande koden.

### <a name="allowed-from"></a>Tillåts från

Modultrådar

### <a name="example"></a>Exempel

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a>txm_module_object_allocate

Allokera minne i objektpoolen (som skapats av det hemmavarande programmet) för ett modulobjektkontrollblock.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a>Description

Den här tjänsten allokerar minne för ett modulobjekt från minnet utanför modulen, vilket förhindrar att objektkontrollblocket skadas av modulens kod. I minnesskyddade system måste alla objektkontrollblock allokeras med det här API:et innan de kan skapas.

### <a name="input-parameters"></a>Indataparametrar

- **object_ptr** Mål för objekt pekare för lyckad allokering.
- **object_size** Storleken i byte för objektet som ska allokeras.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Allokera objekt på rätt sätt.
- **TX_NO_MEMORY** (0x10) Det finns inte tillräckligt med minne.
- **TX_NOT_AVAILABLE** (0x1D) Modulhanteraren har inte skapat en objektpool att allokera från

### <a name="allowed-from"></a>Tillåts från

Modultrådar

### <a name="example"></a>Exempel

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a>Se även

- txm_module_object_deallocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_deallocate"></a>txm_module_object_deallocate

Frisallokera tidigare allokerat objektminne

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a>Description

***Den här tjänsten är inaktuell eftersom den inte längre behövs***.

Det minne som tidigare allokerades ***via txm_module_object_allocate**_ frisallokeras* i tjänsten _ _tx_ \_ _delete***.

### <a name="input-parameters"></a>Indataparametrar

- **object_ptr** Objekt pekare för att frisöka.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Allokera objekt på rätt sätt.

### <a name="allowed-from"></a>Tillåts från

Modultrådar

### <a name="example"></a>Exempel

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a>Se även

- txm_module_object_allocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_pointer_get"></a>txm_module_object_pointer_get

Hitta systemobjekt och hämta objekt pekare

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a>Description

Den här tjänsten hämtar objekt pekaren för en viss typ med ett visst namn. Om objektet inte hittas returneras ett fel. Om objektet hittas placeras annars adressen till objektet i "object_ptr". Den här pekaren kan sedan användas för att göra systemtjänst-anrop, för att interagera med den lokala koden och/eller andra inlästa moduler i systemet.

### <a name="input-parameters"></a>Indataparametrar

- **object_type** Typ av ThreadX-objekt som begärdes. Giltiga typer är följande:
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **namn** Programspecifikt objektnamn enligt definitionen när objektet skapades.
- **object_ptr** Mål för objekt pekare.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Successful object get.
- **TX_OPTION_ERROR** (0x08) Ogiltig objekttyp.
- **TX_PTR_ERROR** (0x03) Ogiltigt mål.
- **TX_SIZE_ERROR** (0x05) Ogiltig storlek.
- **TX_NO_INSTANCE** (0x0D) Det går inte att hitta objektet.

### <a name="allowed-from"></a>Tillåts från

Modultrådar

### <a name="example"></a>Exempel

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>Se även

- txm_module_manager_object_pointer_get_extended

---

## <a name="txm_module_object_pointer_get_extended"></a>txm_module_object_pointer_get_extended

Hitta systemobjekt och hämta objekt pekare

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a>Description

Den här tjänsten hämtar objekt pekaren för en viss typ med ett visst namn. Om objektet inte hittas returneras ett fel. Om objektet hittas placeras annars adressen för objektet i "object_ptr". Den här pekaren kan sedan användas för att göra systemtjänstsamtal, för att interagera med den lokala koden och/eller andra inlästa moduler i systemet.

### <a name="input-parameters"></a>Indataparametrar

- **object_type** Typ av ThreadX-objekt som begärdes. Giltiga typer är följande:
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **namn** Programspecifikt objektnamn enligt definitionen när objektet skapades.
- **name_length** Namnlängd.
- **object_ptr** Mål för objekt pekare.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Successful object get.
- **TX_OPTION_ERROR** (0x08) Ogiltig objekttyp.
- **TX_PTR_ERROR** (0x03) Ogiltigt mål.
- **TX_SIZE_ERROR** (0x05) Ogiltig storlek.
- **TX_NO_INSTANCE** (0x0D) Det går inte att hitta objektet.

### <a name="allowed-from"></a>Tillåts från

Modultrådar

### <a name="example"></a>Exempel

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>Se även

- txm_module_manager_object_pointer_get
