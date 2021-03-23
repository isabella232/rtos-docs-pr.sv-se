---
title: Kapitel 4 – API för modul
author: philmea
ms.author: philmea
description: 'Den här artikeln är en sammanfattning av de ytterligare API: er som är tillgängliga för en modul.'
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5804e2dbb8d08a272abc85a583576f43b7204c1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825488"
---
# <a name="chapter-4---module-apis"></a>Kapitel 4 – API för modul

## <a name="summary-of-module-apis"></a>Översikt över API: er för modul

Det finns flera ytterligare API-funktioner som är tillgängliga för en modul enligt följande:

- ***txm_module_application_request** _-_Application-speciell begäran till Resident kod *
- ***txm_module_object_allocate** _-_Allocate minne utanför modulen för objekt *
- ***txm_module_object_deallocate** _-_Deallocate tidigare allokerat objekt minne *
- ***txm_module_object_pointer_get** _-_Find system objekt och hämta objekt pekare *
- ***txm_module_object_pointer_get_extended** _-_Find system objekt och hämta objekt pekare, namn längd säkerhet *

## <a name="return-values"></a>Returvärden

Ytterligare fel koder returneras för vissa Azure återställnings tider-API: er. Dessa ytterligare fel koder definieras enligt följande:

- **TXM_MODULE_INVALID_PROPERTIES** (0xF3): visar att modulen inte har rätt egenskaper för att göra ett API-anrop. Du kan till exempel anropa trace-API: er i användarläge.
- **TXM_MODULE_INVALID_MEMORY** (0xF4): anger att det minne som angavs av modulen är ogiltigt eller på en ogiltig plats. Till exempel, i minnesmoduler som är skyddade, kan objekt kontroll block inte finnas i minnet som modulen har åtkomst till.
- **TXM_MODULE_INVALID_CALLBACK** (0xF5): motringning som anges i API: t ligger utanför intervallet för modulens kod och är därför ogiltig.

---

## <a name="txm_module_application_request"></a>txm_module_application_request

Programspecifik begäran till Resident kod.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a>Beskrivning

Den här tjänsten gör den angivna begäran till den inhemska delen av programmet. Det förutsätts att begär ande strukturen har förberetts före anropet. Den faktiska bearbetningen av begäran sker i den inhemska koden i funktionen ***_txm_module_manager_application_request***. Den här funktionen lämnas som standard Tom och är utformad för den inhemska programutvecklaren att ändra.

### <a name="input-parameters"></a>Indataparametrar

- **begäran** ID för begäran (program definierat)
- **param_1** Första parametern
- **param_2** Andra parameter
- **param_3** Tredje parametern

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0X00) lyckad begäran.
- **TX_NOT_AVAILABLE** -begäran (0x1D) stöds inte av den inhemska koden.

### <a name="allowed-from"></a>Tillåten från

Modul-trådar

### <a name="example"></a>Exempel

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a>txm_module_object_allocate

Allokera minne i objektcachen (som skapats av det inhemska programmet) för ett objekt kontroll block i modulen.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten allokerar minne för ett modul-objekt från minnet utanför modulen, vilket förhindrar att objekt kontroll blocket skadas av modulens kod. I minnes skyddade system måste alla objekt kontroll block tilldelas med detta API innan de kan skapas.

### <a name="input-parameters"></a>Indataparametrar

- **object_ptr** Objekt pekarens mål för lyckad allokering.
- **object_size** Storlek i byte på det objekt som ska allokeras.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) objekt tilldelning har slutförts.
- **TX_NO_MEMORY** (0x10) det finns inte tillräckligt med minne.
- **TX_NOT_AVAILABLE** (0X1D) module Manager har inte skapat en objektmall att allokera från

### <a name="allowed-from"></a>Tillåten från

Modul-trådar

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

Frigör tidigare allokerat objekt minne

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a>Beskrivning

***Den här tjänsten är inaktuell eftersom den inte längre behövs***.

Minnet som tidigare har allokerats via ***txm_module_object_allocate **_ har* frigjorts i tjänsten _ _TX_ \_ _delete***.

### <a name="input-parameters"></a>Indataparametrar

- **object_ptr** Objekt pekare för att frigöra.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) objekt tilldelning har slutförts.

### <a name="allowed-from"></a>Tillåten från

Modul-trådar

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

Hitta system objekt och hämta objekt pekare

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar objekt pekaren för en viss typ med ett visst namn. Om objektet inte hittas returneras ett fel. Annars placeras adressen för objektet i "object_ptr", om objektet hittas. Den här pekaren kan sedan användas för att göra system tjänst anrop, för att interagera med den inhemska koden och/eller andra inlästa moduler i systemet.

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
- **namn** Programspecifikt objekt namn som definieras när objektet skapades.
- **object_ptr** Mål för objekt pekare.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) objekt hämtades.
- **TX_OPTION_ERROR** (0X08) ogiltig objekt typ.
- **TX_PTR_ERROR** (0X03) ogiltigt mål.
- **TX_SIZE_ERROR** (0X05) ogiltig storlek.
- Det gick inte att hitta **TX_NO_INSTANCE** -objektet (0x0D).

### <a name="allowed-from"></a>Tillåten från

Modul-trådar

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

Hitta system objekt och hämta objekt pekare

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar objekt pekaren för en viss typ med ett visst namn. Om objektet inte hittas returneras ett fel. Annars placeras adressen för objektet i "object_ptr", om objektet hittas. Den här pekaren kan sedan användas för att göra system tjänst anrop, för att interagera med den inhemska koden och/eller andra inlästa moduler i systemet.

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
- **namn** Programspecifikt objekt namn som definieras när objektet skapades.
- **name_length** Namnets längd.
- **object_ptr** Mål för objekt pekare.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) objekt hämtades.
- **TX_OPTION_ERROR** (0X08) ogiltig objekt typ.
- **TX_PTR_ERROR** (0X03) ogiltigt mål.
- **TX_SIZE_ERROR** (0X05) ogiltig storlek.
- Det gick inte att hitta **TX_NO_INSTANCE** -objektet (0x0D).

### <a name="allowed-from"></a>Tillåten från

Modul-trådar

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
