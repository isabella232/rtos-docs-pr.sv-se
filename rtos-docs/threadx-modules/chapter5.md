---
title: 'Kapitel 5 – modul Manager-API: er'
author: philmea
description: 'Den här artikeln är en sammanfattning av modul Manager-API: er som är tillgängliga för den inhemska delen av programmet.'
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ca0fee443c23fd1bdd34651f4a7b31cf71f886f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825485"
---
# <a name="chapter-5---module-manager-apis"></a>Kapitel 5 – modul Manager-API: er

## <a name="summary-of-module-manager-apis"></a>Översikt över API: er för modul Manager

Det finns flera ytterligare API: er som är tillgängliga för den inhemska delen av programmet, enligt följande.

- ***txm_module_manager_external_memory_enable** _-_Enable module-åtkomst till ett delat minnes utrymme *
- ***txm_module_manager_file_load** _-_Load modul från fil via FileX *
- ***txm_module_manager_in_place_load** _-_Load modul data, kör på plats *
- ***txm_module_manager_initialize** _-_Initialize modul Manager *
- ***txm_module_manager_mm_initialize** _-_Initialize minnes hanterings maskin varan *
- ***txm_module_manager_maximum_module_priority_set** _-_Set högsta tråd prioritet som tillåts i en modul *
- ***txm_module_manager_memory_fault_notify** _-_Register ett program motanrop vid minnes fel *
- ***txm_module_manager_memory_load** _-_Load modulen från minnet *
- ***txm_module_manager_object_pool_create** _-_Create en datapool för moduler *
- ***txm_module_manager_properties_get** _-_Get modul egenskaper *
- ***txm_module_manager_start** _-_Start körning av den angivna modulen *
- ***txm_module_manager_stop** _-_Stop körning av den angivna modulen *
- ***txm_module_manager_unload** _-_Unload modulen *

---

## <a name="txm_module_manager_external_memory_enable"></a>txm_module_manager_external_memory_enable

Aktivera modul för att få åtkomst till ett delat minnes utrymme.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en post i maskin varu tabellen för minnes hantering för en delad minnes region som modulen har åtkomst till.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekar till instansen av modulen.
- **start_address** Start adress till den delade minnes regionen.
- **längd** Längd på det delade minnets region.
- **attribut** Attribut för minnes region (cache, läsa, skriva osv.). Attribut är port-/regionsspecifika; Se [bilaga](appendix.md) för attribut format.

### <a name="return-values"></a>Returvärden

- Minnes posten **TX_SUCCESS** (0x00) har skapats.
- **TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats eller är inte tillgänglig.
- **TX_PTR_ERROR** (0X03) ogiltig module-instans.
- **TX_START_ERROR** -modulen (0x10) är inte i inläst läge.
- **TXM_MODULE_ALIGNMENT_ERROR** (0XF0) ogiltig justering av start adress.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) inkompatibla egenskaper.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a>txm_module_manager_file_load

Läs in modul från fil via FileX.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten läser in den binära avbildningen av modulen som finns i den angivna filen i modulens minnes området och förbereder den för körning. Det förutsätts att det angivna mediet redan är öppet.

> [!NOTE]
> FileX-systemet använder för att läsa in filen. För att kunna aktivera FileX-åtkomst måste modulen, modulens bibliotek, modul Manager och ThreadX-biblioteket (med modul Manager-källor) skapas med **FX_FILEX_PRESENT** som definierats i projekten.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekar till instansen av modulen.
- **module_name** Namn på modulen.
- **media_ptr** Pekare till redan öppnade FileX-medier.
- **file_name** Namnet på modulens binära fil.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0X00) lyckad inläsning av modul.
- **TX_CALLER_ERROR** (0X13) ogiltig anropare.
- **TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.
- **TX_NO_MEMORY** (0x10) det finns inte tillräckligt med minne för att läsa in modulen.
- **TX_NOT_DONE** (0X20) mediet är inte öppet, filen hittades inte eller så är filen ogiltig.
- **TX_PTR_ERROR** (0X03) ogiltig modul pekare.
- **TXM_MODULE_ALIGNMENT_ERROR** (0XF0) ogiltig justering.
- Modulen **TXM_MODULE_ALREADY_LOADED** (0xF1) har redan lästs in.
- **TXM_MODULE_INVALID** (0xF2) | Ogiltig inledning av modul.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) inkompatibla egenskaper.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>Se även

- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_in_place_load"></a>txm_module_manager_in_place_load

Läs endast in modul data, kör modul på en befintlig plats.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Beskrivning

Den här tjänsten läser bara in modulens data områden i modulens minnes området och förbereder den för körning. Modulens kod körning är på plats, det vill säga från den adress förskjutning som anges av modulens inledning på den angivna platsen.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekar till instansen av modulen.
- **module_name** Namn på modulen.
- **plats** Pekare till modulens kod områden, inledning först.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0X00) lyckad inläsning av modul.
- **TX_CALLER_ERROR** (0X13) ogiltig anropare.
- **TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.
- **TX_NO_MEMORY** (0x10) det finns inte tillräckligt med minne för att läsa in modulen.
- **TX_PTR_ERROR** (0X03) ogiltig pekare, modul instans eller inledning av modul.
- **TXM_MODULE_ALIGNMENT_ERROR** (0XF0) ogiltig justering.
- Modulen **TXM_MODULE_ALREADY_LOADED** (0xF1) har redan lästs in.
- **TXM_MODULE_INVALID** (0XF2) ogiltig inledning av modul.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) inkompatibla egenskaper.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>Se även

- txm_module_manager_file_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_initialize"></a>txm_module_manager_initialize

Initiera modul Manager.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar modul hanterarens interna resurser, inklusive det minnes utrymme som används för att läsa in moduler.

### <a name="input-parameters"></a>Indataparametrar

- **module_memory_start** Pekar till start av modulens minne.
- **module_memory_size** Storlek i byte för modulens minne.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0X00) lyckades.
- **TX_CALLER_ERROR** (0X13) ogiltig anropare.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a>Se även

- txm_module_manager_object_pool_create

---

## <a name="txm_module_manager_initialize_mmu"></a>txm_module_manager_initialize_mmu

Initiera maskin varan för minnes hantering.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar MMU.

### <a name="input-parameters"></a>Indataparametrar

inget

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0X00) lyckades.
- **TX_CALLER_ERROR** (0X13) ogiltig anropare.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a>txm_module_manager_maximum_module_priority_set

Ange högsta tillåtna tråd prioritet i en modul.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger den maximala tråd prioriteten som tillåts i en modul.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekar till instansen av modulen.
- **prioritet** Högsta tråd prioritet.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0X00) lyckades.
- **TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.
- **TX_PTR_ERROR** (0X03) ogiltig module-instans.
- **TX_START_ERROR** -modulen (0x10) är inte i inläst läge.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a>txm_module_manager_memory_fault_notify

Registrera ett program återanrop vid minnes fel.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar den angivna funktionen för motringning av program minnes fel med modul Manager. Om ett minnes fel inträffar anropas funktionen med en pekare till den felaktiga tråden och den modul som motsvarar den felaktiga tråden. Bearbetningen av den felaktiga tråden avbryts automatiskt av module Manager, men andra trådar i modulen lämnas orörda. Det är upp till programmet att bestämma vad som ska göras med den modul som är kopplad till minnes felet.

Du hittar mer information om själva minnes felet i den interna **_txm_module_manager_memory_fault_info** strukturer.

> [!NOTE]
> Funktionen för motanrop för minnes fel körs direkt från minnes Fels undantaget, så endast ThreadX-API: er som tillåts från avbrott i tjänst rutinen kan anropas. För att stoppa och ta bort den felaktiga modulen måste program meddelande återanropet skicka en signal till en program aktivitet så att modulen kan stoppas och tas bort från minnet.

### <a name="input-parameters"></a>Indataparametrar

- **notify_function** Funktions pekare till programmets återanrop för minnes Fels meddelanden. Om du anger ett NULL-värde inaktive ras minnes Fels aviseringen.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) registreringen av aviserings funktionen lyckades.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a>txm_module_manager_memory_load

Läsa in modulen från minnet.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Beskrivning

Den här tjänsten läser in modulens kod och data i modulens minnes området som har ställts in av ***txm_module_manager_initialize*** och förbereder den för körning.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekar till instansen av modulen.
- **module_name** Namn på modulen.
- **plats** Pekare till modulens kod områden, inledning först.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0X00) lyckad inläsning av modul.
- **TX_CALLER_ERROR** (0X13) ogiltig anropare.
- **TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.
- **TX_NO_MEMORY** (0x10) det finns inte tillräckligt med minne för att läsa in modulen.
- **TX_PTR_ERROR** (0X03) ogiltig pekare, modul instans eller inledning av modul.
- **TXM_MODULE_ALIGNMENT_ERROR** (0XF0) ogiltig justering.
- Modulen **TXM_MODULE_ALREADY_LOADED** (0xF1) har redan lästs in.
- **TXM_MODULE_INVALID** (0XF2) ogiltig inledning av modul.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) inkompatibla egenskaper.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a>Se även

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_object_pool_create"></a>txm_module_manager_object_pool_create

Skapa en datapool för moduler.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en pool för modul hanterarens objekt som modulerna kan använda för att allokera ThreadX/NetX-objekt från, och därmed behålla systemobjektet från modulens minnes yta.

### <a name="input-parameters"></a>Indataparametrar

- **pool_memory_start** Pekar mot start av objekt minnet.
- **pool_memory_size** Storlek i byte för objektets minnes uppsättning.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0X00) lyckades.
- **TX_CALLER_ERROR** (0X13) ogiltig anropare.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a>Se även

- txm_module_manager_initialize

---

## <a name="txm_module_manager_properties_get"></a>txm_module_manager_properties_get

Hämta egenskaper för modul.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar egenskaperna (anges i ingressen) för en modul.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekare till module-instansen.
- **module_properties_ptr** Pekare till målet för modulens egenskaper.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0X00) lyckades.
- **TX_PTR_ERROR** (0X03) ogiltig pekare.
- **TX_CALLER_ERROR** (0X13) ogiltig anropare.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a>txm_module_manager_start

Starta körningen av modulen.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar körningen av angiven, redan inläst modul.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekare till tidigare inläst modul-instans.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0X00) lyckad modul startades.
- **TX_CALLER_ERROR** (0X13) ogiltig anropare.
- **TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.
- **TX_PTR_ERROR** (0X03) ogiltig pekar-eller module-instans.
- Modulen **TX_START_ERROR** (0x10) har redan startats.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>Se även

- txm_module_manager_stop

---

## <a name="txm_module_manager_stop"></a>txm_module_manager_stop

Stoppa körningen av modulen.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar en modul som tidigare har lästs in och startats. Att stoppa en modul inkluderar att köra modulens valfria Stop-tråd, avsluta alla trådar och ta bort alla resurser som är kopplade till modulen.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekare till modul-instans.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0X00) lyckad modul stoppa.
- **TX_CALLER_ERROR** (0X13) ogiltig anropare.
- **TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.
- **TX_PTR_ERROR** (0X03) ogiltig pekar-eller module-instans.
- Modulen **TX_START_ERROR** (0x10) startades inte.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>Se även

- txm_module_manager_start

---

## <a name="txm_module_manager_unload"></a>txm_module_manager_unload

Ta bort modulen.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar den tidigare inlästa och stoppade modulen, vilket frigör alla associerade minnes resurser för modulen.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekar till instansen av modulen.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** 0x00) modulen har tagits bort från minnet.
- **TX_CALLER_ERROR** (0X13) ogiltig anropare.
- **TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.
- **TX_NOT_DONE** (0X20) ogiltig modul eller modul stoppades inte.
- **TX_PTR_ERROR** (0X03) ogiltig pekar-eller module-instans.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>Se även

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_stop
