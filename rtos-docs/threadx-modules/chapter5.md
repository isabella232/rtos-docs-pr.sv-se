---
title: Kapitel 5 – API:er för Modulhanteraren
author: philmea
description: Den här artikeln är en sammanfattning av modulhanterarens API:er som är tillgängliga för programmets lokala del.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8e4da0f9591fd0b5d6249292f00266d96ccb67923c42632a4cfd8c39fa1f129
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799123"
---
# <a name="chapter-5---module-manager-apis"></a>Kapitel 5 – API:er för Modulhanteraren

## <a name="summary-of-module-manager-apis"></a>Sammanfattning av MODULE Manager-API:er

Det finns flera ytterligare API:er som är tillgängliga för den platsande delen av programmet, enligt följande.

- ***txm_module_manager_external_memory_enable** _ – _Enable åtkomst till ett delat minnesutrymme*
- ***txm_module_manager_file_load** _ – _Load-modul från fil via FileX*
- ***txm_module_manager_in_place_load** _ – _Load-moduldata, kör på plats*
- ***txm_module_manager_initialize** _ – _Initialize modulhanteraren*
- ***txm_module_manager_mm_initialize** _ – _Initialize maskinvaran för minneshantering*
- ***txm_module_manager_maximum_module_priority_set** _ – _Set högsta tillåtna trådprioritet i en modul*
- ***txm_module_manager_memory_fault_notify** _ – _Register ett programanrop om minnesfel*
- ***txm_module_manager_memory_load** _ – _Load modulen från minnet*
- ***txm_module_manager_object_pool_create** _ – _Create en objektpool för moduler*
- ***txm_module_manager_properties_get** _ – _Get modulegenskaper*
- ***txm_module_manager_start** _ _Start körning av den angivna modulen*
- ***txm_module_manager_stop** _ - _Stop körning av den angivna modulen*
- ***txm_module_manager_unload** _ _Unload modulen*

---

## <a name="txm_module_manager_external_memory_enable"></a>txm_module_manager_external_memory_enable

Aktivera modulen för att få åtkomst till ett delat minnesutrymme.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a>Description

Den här tjänsten skapar en post i maskinvarutabellen för minneshantering för en delad minnesregion som modulen kan komma åt.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekare till instansen av modulen.
- **start_address** Startadress för det delade minnesområdet.
- **längd** Längden på det delade minnesområdet.
- **attribut** Attribut för minnesregion (cache, läsning, skrivning osv.). Attributen är portspecifika. se [bilaga](appendix.md) för attributformat.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Minnesposten har skapats.
- **TX_NOT_AVAILABLE** (0x1D) Manager initieras inte eller funktionen är inte tillgänglig.
- **TX_PTR_ERROR** (0x03) Ogiltig modulinstans.
- **TX_START_ERROR** (0x10) Modulen är inte i inläst tillstånd.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Ogiltig justering av startadress.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) Inkompatibla egenskaper.

### <a name="allowed-from"></a>Tillåts från

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

Läs in modulen från filen via FileX.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a>Description

Den här tjänsten läser in den binära avbildningen av modulen som finns i den angivna filen i modulminnesområdet och förbereder den för körning. Det förutsätts att det angivna mediet redan har öppnats.

> [!NOTE]
> FileX-systemet används för att läsa in filen. För att aktivera FileX-åtkomst måste modulen, modulbiblioteket, modulhanteraren och ThreadX-biblioteket (med Module Manager-källorna) byggas med **FX_FILEX_PRESENT** definieras i projekten.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekare till instansen av modulen.
- **module_name** Namnet på modulen.
- **media_ptr** Pekare till redan öppnade FileX-media.
- **file_name** Namnet på modulens binära fil.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad modulbelastning.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare.
- **TX_NOT_AVAILABLE** (0x1D) Manager initieras inte.
- **TX_NO_MEMORY** (0x10) Det finns inte tillräckligt med minne för att läsa in modulen.
- **TX_NOT_DONE** (0x20) Media inte öppen, filen hittades inte eller filen är ogiltig.
- **TX_PTR_ERROR** (0x03) Pekare för ogiltig modul.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Ogiltig justering.
- **TXM_MODULE_ALREADY_LOADED** (0xF1) Modulen har redan lästs in.
- **TXM_MODULE_INVALID** (0xF2) | Ogiltig modulinamble.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) Inkompatibla egenskaper.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Läs in endast moduldata, kör modulen på befintlig plats.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Description

Den här tjänsten läser bara in modulens dataområde i modulens minnesområde och förbereder den för körning. Körning av modulkod sker på plats, det vill säga från den adressförskjutning som anges i modulens ingress på den angivna platsen.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekare till instansen av modulen.
- **module_name** Namnet på modulen.
- **plats** Pekare till modulens kodområde, ingressen först.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad modulbelastning.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare.
- **TX_NOT_AVAILABLE** (0x1D) Manager initieras inte.
- **TX_NO_MEMORY** (0x10) Det finns inte tillräckligt med minne för att läsa in modulen.
- **TX_PTR_ERROR** (0x03) Ogiltig pekare, modulinstans eller modulinledningen.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Ogiltig justering.
- **TXM_MODULE_ALREADY_LOADED** (0xF1) Modulen har redan lästs in.
- **TXM_MODULE_INVALID** (0xF2) Ogiltig modulinledningen.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) Inkompatibla egenskaper.

### <a name="allowed-from"></a>Tillåts från

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

Initiera modulhanteraren.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a>Description

Den här tjänsten initierar modulhanterarens interna resurser, inklusive det minnesområde som används för att läsa in moduler.

### <a name="input-parameters"></a>Indataparametrar

- **module_memory_start** Pekare till början av modulminnet.
- **module_memory_size** Storlek i byte för modulminnet.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad initiering.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare.

### <a name="allowed-from"></a>Tillåts från

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

Initiera maskinvaran för minneshantering.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a>Description

Den här tjänsten initierar MMU.

### <a name="input-parameters"></a>Indataparametrar

inget

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad initiering.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare.

### <a name="allowed-from"></a>Tillåts från

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

Ange den högsta trådprioritet som tillåts i en modul.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a>Description

Den här tjänsten anger den högsta trådprioritet som tillåts i en modul.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekare till instansen av modulen.
- **prioritet** Högsta trådprioritet.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad initiering.
- **TX_NOT_AVAILABLE** (0x1D) Manager initieras inte.
- **TX_PTR_ERROR** (0x03) Ogiltig modulinstans.
- **TX_START_ERROR** (0x10) Modulen är inte i inläst tillstånd.

### <a name="allowed-from"></a>Tillåts från

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

Registrera ett programanrop vid minnesfel.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a>Description

Den här tjänsten registrerar den angivna återanropsfunktionen för meddelanden om minnesfel i programmet med Modulhanteraren. Om ett minnesfel uppstår anropas den här funktionen med en pekare till den felaktiga tråden och modulinstansen som motsvarar den felaktiga tråden. Modulhanterarens bearbetning avslutar automatiskt den stötande tråden, men lämnar alla andra trådar i modulen oförändrade. Det är upp till programmet att bestämma vad som ska göra med modulen som är associerad med minnesfelet.

Se den interna **_txm_module_manager_memory_fault_info** för specifik information om själva minnesfelet.

> [!NOTE]
> Funktionen för återanrop av minnesfelmeddelanden körs direkt från minnesfelfelet, så endast ThreadX-API:er som tillåts från avbrottstjänstrutiner kan anropas. För att stoppa och ta bort den stötande modulen måste återanropet av programmeddelandet skicka en signal till en programuppgift så att modulen kan stoppas och tas bort.

### <a name="input-parameters"></a>Indataparametrar

- **notify_function** Funktionspekare till programmets återanrop av minnesfelmeddelande. Om du tillhandahåller ett NULL-värde inaktiveras meddelandet om minnesfel.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad registrering av meddelandefunktionen.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="example"></a>Exempel

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a>txm_module_manager_memory_load

Läs in modulen från minnet.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Description

Den här tjänsten läser in modulens kod och dataområde till modulminnesområdet som konfigureras ***av txm_module_manager_initialize*** och förbereder den för körning.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekare till instansen av modulen.
- **module_name** Namnet på modulen.
- **plats** Pekare till modulens kodområde, ingressen först.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad modulbelastning.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare.
- **TX_NOT_AVAILABLE** (0x1D) Manager initieras inte.
- **TX_NO_MEMORY** (0x10) Det finns inte tillräckligt med minne för att läsa in modulen.
- **TX_PTR_ERROR** (0x03) Ogiltig pekare, modulinstans eller modulinamble.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Ogiltig justering.
- **TXM_MODULE_ALREADY_LOADED** (0xF1) Modulen har redan lästs in.
- **TXM_MODULE_INVALID** (0xF2) Ogiltig modulinledningen.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) Inkompatibla egenskaper.

### <a name="allowed-from"></a>Tillåts från

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

Skapa en objektpool för moduler.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en Module Manager-objektminnespool som modulerna kan allokera ThreadX/NetX-objekt från, vilket håller systemobjektet utanför modulens minnesyta.

### <a name="input-parameters"></a>Indataparametrar

- **pool_memory_start** Pekare till början av objektminnet.
- **pool_memory_size** Storlek i byte för objektminnespoolen.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad initiering.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare.

### <a name="allowed-from"></a>Tillåts från

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

Hämta modulegenskaper.

### <a name="prototype"></a>Prototyp

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a>Description

Den här tjänsten returnerar egenskaperna (anges i ingressen) för en modul.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekare till modulinstansen.
- **module_properties_ptr** Pekare till mål för modulens egenskaper.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad initiering.
- **TX_PTR_ERROR** (0x03) Ogiltig pekare.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten startar körningen av den angivna, redan inlästa modulen.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekare till en modulinstans som lästs in tidigare.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad modulstart.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare.
- **TX_NOT_AVAILABLE** (0x1D) Manager initieras inte.
- **TX_PTR_ERROR** (0x03) Ogiltig pekare eller modulinstans.
- **TX_START_ERROR** -modulen (0x10) har redan startats.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten stoppar en modul som tidigare har lästs in och startats. Att stoppa en modul omfattar att köra modulens valfria stopptråd, avsluta alla trådar och ta bort alla resurser som är associerade med modulen.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekare till modulinstans.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad modulstopp.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare.
- **TX_NOT_AVAILABLE** (0x1D) Manager initieras inte.
- **TX_PTR_ERROR** (0x03) Ogiltig pekare eller modulinstans.
- **TX_START_ERROR** (0x10) Modulen har inte startats.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten tar bort den tidigare inlästa och stoppade modulen, vilket frigör alla associerade modulminnesresurser.

### <a name="input-parameters"></a>Indataparametrar

- **module_instance** Pekare till instansen av modulen.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** 0x00) Lyckad modulavlastning.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare.
- **TX_NOT_AVAILABLE** (0x1D) Manager initieras inte.
- **TX_NOT_DONE** (0x20) Ogiltig modul eller modul har inte stoppats.
- **TX_PTR_ERROR** (0x03) Ogiltig pekare eller modulinstans.

### <a name="allowed-from"></a>Tillåts från

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
