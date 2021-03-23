---
title: Kapitel 4 – Beskrivning av LWM2M klient tjänster
description: Det här kapitlet innehåller en beskrivning av alla LWM2M klient tjänster i alfabetisk ordning.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 825a215ba756b39b6d76e6cc773c288e8b8aab01
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825929"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a>Kapitel 4 Beskrivning av LWM2M-KLIENTtjänster

Det här kapitlet innehåller en beskrivning av alla LWM2M klient tjänster som listas nedan i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av  **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

**LWM2M klient hantering:**

- nx_lwm2m_client_create: *skapa lwm2m-klient*

- nx_lwm2m_client_delete: *ta bort lwm2m-klienten*

- nx_lwm2m_client_lock: *Lås lwm2m-klienten*

- nx_lwm2m_client_unlock: *Lås upp lwm2m-klienten*

**LWM2M för hantering av klient sessioner:**

- nx_lwm2m_client_session_create: *skapa en lwm2m-klientsession*

- nx_lwm2m_client_session_delete: *ta bort lwm2m-klientsession*

- nx_lwm2m_client_session_bootstrap: *starta en session med en Start Server*

- nx_lwm2m_client_session_bootstrap_dtls: *starta en säker session med en Start Server*

- nx_lwm2m_client_session_register_info_get: *Hämta Lwm2m Server register information*

- nx_lwm2m_client_session_register: *starta en session med en lwm2m-Server*

- nx_lwm2m_client_session_register_dtls: *starta en säker session med en lwm2m-Server*

- nx_lwm2m_client_session_update: *Uppdatera en session med en lwm2m-Server*

- nx_lwm2m_client_session_deregister: *Avsluta en session med en lwm2m-Server*

- nx_lwm2m_client_session_error_get: *Hämta senaste fel i en session*

**Implementering av enhets objekt:**

- nx_lwm2m_client_device_callbacks_set: *Ange återanrop i enhets objekts program*

- nx_lwm2m_client_device_error_push: *Lägg till felkod till enhets objekt*

- nx_lwm2m_client_device_error_reset: *återställa felkoder för enhets objekt*

- nx_lwm2m_client_device_resource_changed: *signal ändring av enhets objekt resurs*

**Objekt implementering för uppdatering av inbyggd program vara:**

- nx_lwm2m_firmware_create: *skapa uppdaterings objekt för inbyggd program vara*

- nx_lwm2m_firmware_package_info_set: *Ange information om uppdaterings paket för inbyggd program vara*

- nx_lwm2m_firmware_result_set: *Ange uppdaterings resultat för inbyggd program vara*

- nx_lwm2m_firmware_state_set: *Ange uppdaterings tillstånd för inbyggd program vara*

**Implementering av anpassade objekt:**

- nx_lwm2m_client_object_add: *Lägg till objekt implementering i lwm2m-klienten*

- nx_lwm2m_client_object_remove: *ta bort objekt implementering från lwm2m-klienten*

- nx_lwm2m_client_object_instance_add: *Lägg till objekt instans i lwm2m-klienten*

- nx_lwm2m_client_object_instance_remove: *ta bort objekt instansen från lwm2m-klienten*

- nx_lwm2m_object_resource_changed: *signal ändring av ett resurs värde för en objekt instans*

**Hantering av lokala enheter**

- nx_lwm2m_client_object_create: *skapa en ny objekt instans*

- nx_lwm2m_client_object_delete: *ta bort en objekt instans*

- nx_lwm2m_client_object_discover: *identifiera resurser för en objekt instans*

- nx_lwm2m_client_object_execute: *Kör resurs för en objekt instans*

- nx_lwm2m_client_object_next_get: *Hämta listan över objekt som implementeras av lwm2m-klienten*

- nx_lwm2m_client_object_instance_next_get: *Hämta listan över instanser av ett objekt*

- nx_lwm2m_client_object_read: *läsa resurs värden för en objekt instans*

- nx_lwm2m_client_object_write: *Ändra resurs värden för en objekt instans*

**Inställning av resurs information och värden:**

- nx_lwm2m_client_resource_info_set: *Ange resurs informationen*

- nx_lwm2m_client_resource_string_set: *Ange resurs värde som sträng*

- nx_lwm2m_client_resource_integer32_set: *Ange resurs värde som 32-bitars heltal*

- nx_lwm2m_client_resource_integer64_set: *Ange resurs värde som 64-bitars heltal*

- nx_lwm2m_client_resource_float32_set: *Ange resurs värde som 32-bitars flyttal*

- nx_lwm2m_client_resource_float64_set: *Ange resurs värde som 64-bitars flyttal*

- nx_lwm2m_client_resource_boolean_set: *Ange resurs värde som booleskt värde*

- nx_lwm2m_client_resource_objlnk_set: *Ange resurs värde som objekt länk*

- nx_lwm2m_client_resource_opaque_set: *Ange resurs värde som ogenomskinligt*

- nx_lwm2m_client_resource_instance_set: *Ange resurs värde som instansen för flera resurser*
-
- nx_lwm2m_client_resource_dim_set: *Ange resurs dimensionen för flera resurser.*

**Resurs information och värden får:**

- nx_lwm2m_client_resource_info_get: *Hämta resursinformation*

- nx_lwm2m_client_resource_string_get: *Hämta värdet för en sträng resurs*

- nx_lwm2m_client_resource_integer32_get: *Hämta värdet för en 32-bitars heltals resurs*

- nx_lwm2m_client_resource_integer64_get: *Hämta värdet för en 64-bitars heltals resurs*

- nx_lwm2m_client_resource_float32_get: *Hämta värdet för en 32-bitars float-resurs*

- nx_lwm2m_client_resource_float64_get: *Hämta värdet för en 64-bitars float-resurs*

- nx_lwm2m_client_resource_boolean_get: *Hämta värdet för en boolesk resurs*

- nx_lwm2m_client_resource_objlnk_get: *Hämta värdet för en objekt länk resurs*

- nx_lwm2m_client_resource_opaque_get: *Hämta värdet för en ogenomskinlig resurs*

- nx_lwm2m_client_resource_instance_get: *Hämta resurs instansen för flera resurser*

- nx_lwm2m_client_resource_dim_get: *Hämta resurs dimensionen för flera resurser.*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Skapar en LWM2M-klient.

### <a name="prototype"></a>Prototyp

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en LWM2M-klient instans som körs i kontexten för en egen ThreadX-tråd.

LWM2M-klienten implementerar följande OMA LWM2M-objekt: Security (0), Server (1), Access Control (2) och enhet (3). Implementeringar av andra objekt måste läggas till av programmet.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **packet_pool_ptr** Visar en pekare till LWM2M-klientens standardpool.
- **name_ptr** Pekare till LWM2M-klientens slut punkts namn.
- **name_length** Längden på LWM2M-klientens slut punkts namn.
- **msisdn_ptr** Pekaren till MSISDN där LWM2M-klienten kan nås för användning med SMS-bindningen, kan vara NULL om SMS-bindning inte stöds.
- **msisdn_length** Längd på MSISDN-nummer.
- **binding_modes** Bindningen och lägena som stöds av LWM2M-klienten måste vara en kombination av NX_LWM2M_BINDING_U-, NX_LWM2M_BINDING_UQ-, NX_LWM2M_BINDING_S-och NX_LWM2M_BINDING_SQ flaggor.
- **stack_ptr** Pekare till LWM2M klient tråds tack.
- **stack_size** LWM2M klient trådens stack storlek.
- **prioritet** Prioritet för LWM2M-klienten.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** LWM2M-klienten har skapats.
- **NX_LWM2M_CLIENT_ERROR** LWM2M-klient skapa fel.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.
- **NX_PTR_ERROR** Ogiltig pekare.
- **NX_SIZE_ERROR** Ogiltig stack storlek.
- **NX_OPTION_ERROR** Ogiltig prioritet.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

Tar bort en LWM2M-klient.

### <a name="prototype"></a>Prototyp

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad LWM2M-klient instans.

Alla sessioner som är anslutna till klienten tas också bort av det här anropet.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** LWM2M-klienten har tagits bort.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a>nx_lwm2m_client_device_callback_set

Anger ett enhets objekts återanrop för programmet.

### <a name="prototype"></a>Prototyp

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a>Beskrivning

Den här tjänsten installerar program återanrop för att implementera åtgärder på LWM2M enhets objekt resurser som inte hanteras av LWM2M-klienten.

LWM2M-klienten implementerar följande resurser: felkod (11), Reset-felkod (12) och bindning och lägen som stöds (16). åtgärder för de andra resurserna omdirigeras till programmet.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **operation_callback** Återanrop för "Read", "Discovery", "Write" och "EXECUTE".

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Återanropet för åtgärden har angetts.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push
Lägger till en felkod till ett enhets objekt.

### <a name="prototype"></a>Prototyp

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en ny instans i fel kods resursen (11) för objekt enheten.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **kod** Den nya felkoden.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**

Det maximala antalet lagrade felkoder har

nåtts.

NX_PTR_ERROR ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Återställer felkoden för enhets objekt.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort alla fel kods resurs instanser från objektet enhet. Det motsvarar att köra fel koden för resurs återställning (12).

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Signalerar en ändring av en enhets objekt resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a>Beskrivning

Tjänsten används av programmet för att signalera till LWM2M-klienten att en resurs av objekt enheten har ändrats. LWM2M-klienten skickar ett meddelande om resursen observeras av en LWM2M-Server.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **resurs** Pekar till strukturen som beskriver den resurs som har ändrats.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a>nx_lwm2m_client_firmware_create

Skapa ett LWM2M-klient-objekt för inbyggd program vara. 

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a>Beskrivning

Tjänsten används av programmet för att skapa en inbyggd program vara.

### <a name="parameters"></a>Parametrar

- **firmware_ptr** Pekare till LWM2M-klientens inbyggda objekt.
- **client_ptr** Pekare till LWM2M klient kontroll block.
- **protokoll** Protokoll som stöds.
- **package_callback** Paket återanropet.
- **package_uri_callback** Paket-URI-motanrop.
- **update_callback** Återanropet för uppdateringen.

### <a name="return-values"></a>Retur värden

**NX_SUCCESS** Åtgärden lyckades.
**NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a>nx_lwm2m_client_firmware_package_info_set

Anger information om LWM2M-klientens firmware-paket.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a>Beskrivning

Tjänsten används av programmet för att ange paket informations resurserna för det inbyggda program varans uppdaterings objekt.

### <a name="parameters"></a>Parametrar

- **firmware_ptr** Pekare till LWM2M-klientens inbyggda objekt.
- **namn** Namnet på den inbyggda program varans paket.
- **name_length** Namnets längd.
- **version** Versionen av den inbyggda program varans paket.
- **version_length** Versionens längd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a>nx_lwm2m_client_firmware_result_set

Anger uppdaterings resultat resursen för det inbyggda program varans uppdaterings objekt.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Beskrivning

Tjänsten används av programmet för att ställa in uppdaterings resultat resursen för objektet för den inbyggda program varan.

### <a name="parameters"></a>Parametrar

- **firmware_ptr** Pekare till LWM2M-klientens inbyggda objekt.
- **resultat** Uppdaterings resultatet.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a>nx_lwm2m_client_firmware_state_set

Anger uppdaterings resultat resursen för det inbyggda program varans uppdaterings objekt.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Beskrivning

Tjänsten används av programmet för att ange tillstånd för uppdaterings objekt för den inbyggda program varan.

### <a name="parameters"></a>Parametrar

- **firmware_ptr** Pekare till LWM2M-klientens inbyggda objekt.
- **tillstånd** Status för den inbyggda program varans objekt.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Låser LWM2M-klienten.

### <a name="prototype"></a>Prototyp

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten låser LWM2M-klienten för att förhindra samtidig åtkomst till LWM2M-objekt från servrar eller en annan program tråd.

Om LWM2M-klienten är låst av en annan tråd, kommer funktionen att blockeras tills LWM2M-klienten har låsts upp.

Anrop till ***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_**-par kan kapslas.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Lägger till en objekt implementering i LWM2M-klienten.

### <a name="prototype"></a>Prototyp

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en ny objekt implementering i LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **object_ptr** Pekare till strukturen som definierar objekt implementeringen.
- **object_id** Objekt-ID.
- **object_operation** Funktionen motringning för objekt åtgärd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Objekt-ID: t finns redan.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Skapar en ny objekt instans.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en "skapa"-åtgärd på ett objekt av LWM2M-klienten för att skapa en ny objekt instans.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **object_id** Objekt-ID.
- **instance_id_ptr** Pekaren till ID: t för den nya instansen kan vara **Null** om LWM2M-klienten måste tilldela ett instans-ID. Om ID: t är det reserverade värdet 65535, tilldelar LWM2M-klienten ett instans-ID. Om det tilldelade ID: t inte är NULL returneras det efter anropet.
- **num_values** Antalet värden som ska anges.
- **values_ptr** Pekar mot en matris med resurs värden för att initiera den nya objekt instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Objekt instans-ID: t finns redan.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Objektet har inte stöd för att skapa en instans.
- **NX_LWM2M_CLIENT_NO_MEMORY** Det går inte att allokera minne för att lagra den nya instansen.
- **NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID: t finns inte.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Tar bort en objekt instans.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en borttagnings åtgärd på en objekt instans av LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **object_id** Objekt-ID.
- **instance_id** Objekt instansens ID.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Objektet har inte stöd för borttagning av instans.
- **NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID: t eller objekt instans-ID: t finns inte.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

Identifierar resurser för en objekt instans.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en "Discover"-åtgärd på en objekt instans av LWM2M-klienten, vilket returnerar listan över resurser som implementeras av objektet.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **object_id** Objekt-ID.
- **instance_id** Objekt instansens ID.
- **num_resources** Vid indata anger du storleken på målcachen vid utdata av antalet element som skrivs till bufferten.
- **resurser** Pekar mot målcachen.

### <a name="return-values"></a>Retur värden

- *NX_SUCCESS** åtgärden lyckades.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Resursens buffert är för liten för att lagra listan över resurser.
- **NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID: t eller objekt instans-ID: t finns inte.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

Utför en körnings åtgärd på en resurs av en objekt instans.

### <a name="prototype"></a>Prototyp

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför åtgärden kör på en objekt instans resurs för LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **object_id** Objekt-ID.
- **instance_id** Objekt instansens ID.
- **resource_id** Resurs-ID.
- **arguments_ptr** Pekar till argumenten för körnings åtgärden. Kan vara NULL om arguments_length är noll.
- **arguments_length** Argumentens längd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Resursens buffert är för liten för att lagra listan över resurser.
- **NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID: t eller objekt instans-ID: t finns inte.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a>nx_lwm2m_client_object_instance_add

Lägger till en objekt instans implementering till ett objekt.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en ny implementering av objekt instansen i LWM2M-klienten. Om värdet för instance_id_ptr är **NX_LWM2M_CLIENT_RESERVED_ID** tilldelar LWM2M-klienten automatiskt ett oanvänt instans-ID, annars kommer LWM2M-klienten att använda värdet program uppsättning. När den nya instansen har lagts till kommer instance_id att fyllas i instance_id_ptr att återgå till programmet.

### <a name="parameters"></a>Parametrar

- **object_ptr** Pekare till strukturen som definierar objekt implementeringen.
- **instance_ptr** Pekare till strukturen som definierar implementeringen av objekt instansen.
- **instance_id_ptr** Pekare till objekt instansens ID.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_CLIENT_LWM2M_ALREADY_EXIST** Objekt-ID: t finns redan.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a>nx_lwm2m_client_object_instance_next_get

Hämtar nästa instans av ett objekt.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar ID: t för nästa objekt instans av det aktuella objektet. Om det aktuella instans-ID: t är inställt på NX_LWM2M_RESERVED_ID (65535) returneras ID: t för den första instansen.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **object_id** Objekt-ID.
- **instance_id_ptr** Pekar mot det aktuella objekt instans-ID: t. Vid retur innehåller nästa instans-ID för objektet.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_CLIENT_LWM2M_NOT_FOUND** Angivet instans-ID är det sista objektet eller objekt-ID: t är inte implementerat.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a>nx_lwm2m_client_object_instance_remove

Tar bort en objekt instans implementering från ett objekt.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en objekt instans från ett objekt.

### <a name="parameters"></a>Parametrar

- ***object_ptr*** Pekare till strukturen som definierar objekt implementeringen.
- **instance_ptr** Pekare till strukturen som definierar implementeringen av objekt instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Objekt-ID: t finns redan.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a>nx_lwm2m_client_object_next_get

Hämtar nästa objekt för LWM2M-klienten.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar ID: t för nästa objekt som implementeras av LWM2M-klienten. Om aktuellt objekt-ID är inställt på NX_LWM2M_RESERVED_ID (65535) returneras det första objekt-ID: t.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **object_id_ptr** Pekar mot aktuellt objekt-ID. Vid retur innehåller nästa objekt-ID som implementeras av LWM2M-klienten.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_NOT_FOUND** Angivet objekt-ID är det sista i databasen.
**NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Läser en objekt Instanss resource's-värden.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en Läs åtgärd på en objekt instans av LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **object_id** Objekt-ID.
- **instance_id** Objekt instansens ID.
- **num_values** Antalet resurser som ska läsas.
- **values_ptr** Pekar till en matris med NX_LWM2M_RESOURCE som innehåller ID: n för de resurser som ska läsas. Vid retur fylls matrisen med motsvarande typer och värden.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** En resurs har inte stöd för Läs åtgärden.
- **NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID, objekt instans-ID eller resurs-ID finns inte.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a>nx_lwm2m_client_object_remove

Tar bort en objekt instans implementering från ett objekt.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort ett objekt från LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **object_ptr** Pekare till strukturen som definierar objekt implementeringen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Objekt-ID: t finns redan.
- **NX_PTR_ERROR** Ogiltig pekare.
- **NX_LWM2M_CLIENT_FORBIDDEN** Borttagning av internt objekt är förbjudet.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a>nx_lwm2m_client_object_resource_changed

Signalerar en ändring av en objekt resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Beskrivning

Tjänsten används av programmet för att signalera till LWM2M-klienten om att en resurs objekt har ändrats. LWM2M-klienten skickar ett meddelande om resursen observeras av en LWM2M-Server.

### <a name="parameters"></a>Parametrar

- **object_ptr** Pekare till strukturen som definierar objekt implementeringen.
- ***instance_ptr*** Pekare till strukturen som definierar implementeringen av objekt instansen.
- **resurs** Pekar till strukturen som beskriver den resurs som har ändrats.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Ändrar resursens värden för en objekt instans.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en Skriv åtgärd på en objekt instans av LWM2M-klienten.

Följande Skriv åtgärder kan anges för parametern *write_op* .

| Värde | Skriv &nbsp; åtgärd | Beskrivning |
| --- | ---| --- |
| 0 | Partiell uppdatering | Lägger till eller uppdaterar resurser som finns i det nya värdet och lämnar andra befintliga resurser oförändrade. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Ersätt instans | Ersätter objekt instansen med de nya angivna resurs värdena. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** | Ersätt resurs | Ersätter resurserna med de nya angivna resurs värdena (används för att ersätta flera resurser). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Bootstrap-skrivning | Anger ett anrop från en bootstrap-sekvens. |

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.
- **object_id** Objekt-ID.
- **instance_id** Objekt instansens ID.
- **num_values** Antalet resurser som ska skrivas.
- **values_ptr** Pekar till en matris med NX_LWM2M_RESOURCE som innehåller ID: n för resurserna, typerna och värdena som ska skrivas.
- **write_op** Typ av Skriv åtgärd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resurs typen är inte giltig.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Längden på ett värde är för stor för att lagras i instansen.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** En resurs har inte stöd för Skriv åtgärden.
- **NX_LWM2M_CLIENT_NO_MEMORY** Det går inte att allokera minne för att lagra ett resurs värde.
- **NX_LWM2M_CLIENT_NOT_ACCEPTABLE** Värdet för en resurs är inte giltigt.
- **NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID, objekt instans-ID eller resurs-ID finns inte.
- **NX_OPTION_ERROR** Ogiltig typ av Skriv åtgärd. 
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a>nx_lwm2m_client_resource_boolean_get

Hämtar värdet för en boolesk resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en boolesk resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs värde beskrivning.
- **bool_ptr** Pekar mot målets booleska värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett booleskt värde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a>nx_lwm2m_client_resource_boolean_set

Anger värdet för en boolesk resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a>Beskrivning

Tjänsten anger värdet för en boolesk resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **bool_data** Booleska data.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a>nx_lwm2m_client_resource_dim_get

Hämtar resurs dimensionen för flera resurser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar resurs dimensionen för flera resurser.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **dim** pekare till mål dimensionen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett booleskt värde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a>nx_lwm2m_client_resource_dim_set

Anger resurs dimensionen för flera resurser.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a>Beskrivning

Tjänsten anger resurs dimensionen för flera resurser.

### <a name="parameters"></a>Parametrar

- **värde** Pekare till resurs värde beskrivning.
- dimensions värde för **dimension** .

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a>nx_lwm2m_client_resource_float32_get

Hämtar värdet för en 32-bitars **float** -resurs

### <a name="prototype"></a>Prototyp

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en 32-bitars **float** -resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **float32_ptr** Pekar till målet 32-bit **flytt ALS** värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett booleskt värde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a>nx_lwm2m_client_resource_float32_set

Anger värdet för en 32-bitars **float** -resurs

### <a name="prototype"></a>Prototyp

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a>Beskrivning

Tjänsten anger värdet för en 32-bitars **float** -resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **float32_data** 32-bitars **float** -data.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a>nx_lwm2m_client_resource_float64_get

Hämtar värdet för en 64-bitars float-resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en 64-bitars **float** -resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **float64_ptr** Pekar till målet 64-bit **flytt ALS** värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett flytt ALS värde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a>nx_lwm2m_client_resource_float64_set

Anger värdet för en 64-bitars **float** -resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Beskrivning

Tjänsten anger värdet för en 64-bitars **float** -resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **float64_data** 64-bitars **float** -data.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a>nx_lwm2m_client_resource_info_get

Hämtar resurs informationen.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar resurs informationen för resursen.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **resource_id** Pekare till mål resurs-ID: t.
- **åtgärd** Pekare till mål resurs åtgärden.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a>nx_lwm2m_client_resource_info_set

Anger resursinformation.

### <a name="prototype"></a>Prototyp

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Beskrivning

Tjänsten anger resursinformationen.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **resource_id** Resursens ID.
- **åtgärd** Driften av resursen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a>nx_lwm2m_client_resource_instances_get

Hämtar instansen av flera resurser.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar resurs informationen för resursen.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **resource_instances** Pekare till mål resurs-ID: t.
- **antal** Pekar mot Count.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett booleskt värde.
- **NX_LWM2M_CLIENT_NO_MEMORY** Det fanns inte tillräckligt med minne för att fylla i instanser.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a>nx_lwm2m_client_resource_instances_set

Anger resurs instanser.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a>Beskrivning

Tjänsten anger resurs instanserna för flera resurser.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **resource_instance** Pekare till resurs instanser.
- **antal** Antal resurs instanser.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a>nx_lwm2m_client_resource_integer32_get

Hämtar värdet för en 32-bitars heltals resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en 32-bitars heltals resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **integer32_ptr** Pekar mot 32-bitars heltals värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett heltals värde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a>nx_lwm2m_client_resource_integer32_set

Anger värdet för en 32-bitars heltals resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a>Beskrivning

Tjänsten anger värdet för en 32-bitars heltals resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **integer32_data** 32-bitars heltals data.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a>nx_lwm2m_client_resource_integer64_get

Hämtar värdet för en 64-bitars heltals resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en 64-bitars heltals resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **integer64_ptr** Pekar mot 64-bitars heltals värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte 64-bitars heltals värde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a>nx_lwm2m_client_resource_integer64_set

## <a name="set-the-value-of-a-64-bit-integer-resource"></a>Ange värdet för en 64-bitars heltals resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a>Beskrivning

Tjänsten anger värdet för en 64-bitars heltals resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **integer64_data** 64-bitars heltal.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a>nx_lwm2m_client_resource_objlnk_get

Hämtar värdet för en objekt länk resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för objekt länken.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **object_id** Pekar mot objekt-ID.
- **instance_id** Pekare till objekt instansens ID.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett objekt länk värde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a>nx_lwm2m_client_resource_objlnk_set

Anger resurs instanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Beskrivning

Tjänsten anger värdet för objekt länk resursen.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **object_id** Objekt-ID.
- **instance_id** Objekt instans-ID.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a>nx_lwm2m_client_resource_opaque_get

Hämtar värdet för en ogenomskinlig resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en ogenomskinlig resurs. Ett ogenomskinligt resurs värde består av en pekare till en buffert och en längd.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **opaque_ptr** Pekar mot täckande data.
- **opaque_length** Pekar mot ogenomskinlig data längd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte en ogenomskinlig resurs.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a>nx_lwm2m_client_resource_opaque_set

Anger värdet för en ogenomskinlig resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a>Beskrivning

Tjänsten anger värdet för en ogenomskinlig resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **opaque_ptr** Pekar mot täckande data.
- **opaque_length** Längden på täckande data.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a>nx_lwm2m_client_resource_string_get

Hämtar värdet för en sträng resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en sträng resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **string_ptr** Pekare till mål sträng pekaren.
- **string_length** Pekar mot mål strängens längd. Kan vara **Null** om strängen är null-terminerad.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett sträng värde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a>nx_lwm2m_client_resource_string_set

Anger värdet för en sträng resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a>Beskrivning

Tjänsten anger värdet för en 64-bitars heltals resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till resurs.
- **string_ptr** Pekare till strängen.
- **string_length** Strängens längd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Startar en-session med en Start Server.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en session med en Start Server. Servern måste ha en motsvarande säkerhets instans i objektet Security.

Om resursen "vänta bort" skiljer sig från noll i säkerhets instansen som är kopplad till den här servern väntar sessionen på en initierad start av servern, om ingen start initieras av servern efter den här tids perioden som en klient initierade boostrap kommer att utföras.

Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya bootstrap-serversessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till LWM2M för klientens session.
- **security_id** Start serverns säkerhets instans-ID måste anges till NX_LWM2M_RESERVED_ID (65535) om ingen säkerhets instans har definierats för bootstrap-servern.
- **ip_address** Serverns IP-adress.
- **port** Serverns UDP-port.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ERROR** Start fel.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Startar en säker session med en Start Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en session med en Start Server med en säker DTLS-anslutning. Servern måste ha en motsvarande säkerhets instans i objektet Security.

DTLS-sessionen måste ha kon figurer ATS med lämpliga chiffersviter och nyckel material innan du anropar den här funktionen. **NX_SECURE_ENABLE_DTLS** måste definieras.

Om resursen "vänta bort" skiljer sig från noll i säkerhets instansen som är kopplad till den här servern väntar sessionen på en initierad start av servern, om ingen start initieras av servern efter den här tids perioden som en klient initierade boostrap kommer att utföras. 

Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya bootstrap-serversessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till LWM2M för klientens session.
- **security_id** Start serverns säkerhets instans-ID måste anges till **NX_LWM2M_RESERVED_ID** (65535) om ingen säkerhets instans har definierats för bootstrap-servern.
- **ip_address** Serverns IP-adress.
- **port** Serverns UDP-port.
- **dtls_session_ptr** DTLS-sessionen som ska användas för bootstrap-sessionen.
- **dtls_local_port** Den lokala UDP-porten som används för DTLS-sessionen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ERROR** Start fel.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Skapar en LWM2M-klientsession.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en ny LWM2M-klientsession som är ansluten till en befintlig LWM2M-klient. Sessionen används av LWM2M-klienten för att kommunicera med en Start Server eller en LWM2M-Server. 

Programmet måste tillhandahålla en callback-funktion som anropas när sessionens tillstånd uppdateras.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till LWM2M för klientens session.
- **client_ptr** Pekare till den tidigare skapade LWM2M-klienten.
- **state_callback** Återanrop från program som anropas när sessionens tillstånd har ändrats.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Tar bort en LWM2M-klientsession.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en LWM2M-klientsession.

När en LWM2M-klient tas bort genom att anropa nx_lwm2m_client_delete alla sessioner som är anslutna till klienten också bort.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till LWM2M för klientens session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Avslutar en session med en LWM2M-Server.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en "avregistrera"-åtgärd på en LWM2M-Server.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till LWM2M för klientens session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** Klienten är inte registrerad på servern.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Hämtar det senaste felet i en session.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar felkoden för sessionen när sessionen är i ett fel tillstånd.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till LWM2M för klientens session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Sessionen är inte i ett fel tillstånd.
- **NX_LWM2M_CLIENT_ADDRESS_ERROR** Ogiltig server adress.
- **NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Nytto lasten för begäran får inte plats i nätverksmappen.
- **NX_LWM2M_ CLIENT_DTLS_ERROR** Det gick inte att upprätta en säker anslutning till servern.
- **NX_LWM2M_ CLIENT_ERROR** Okänt fel.
- **NX_LWM2M_ CLIENT_FORBIDDEN** Registreringen nekades av servern.
- **NX_LWM2M_ CLIENT_NOT_FOUND** Klienten kunde inte hittas av servern vid uppdatering/avregistrering.
- **NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** Server objekts instansen som motsvarar sessionen har tagits bort.
- **NX_LWM2M_ CLIENT_TIMED_OUT** Inget svar från servern.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Startar en session med en LWM2M-Server.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a>Beskrivning

Den här tjänsten utför en "Registrera"-åtgärd på en LWM2M-Server. Servern måste ha en motsvarande Server instans i objektet Server.

Om registreringen lyckas kommer LWM2M-klienten att bearbeta ytterligare åtgärder från servern och skickar regelbundet meddelanden om uppdatering tills klienten avregistreras.

Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya LWM2M.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till LWM2M för klientens session.
- **server_id** Det korta Server-ID: t för LWM2M-servern.
- **ip_address** Serverns IP-adress.
- **port** Serverns UDP-port.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ERROR** Start fel.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Startar en säker session med en LWM2M-Server.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en "Registrera"-åtgärd på en LWM2M-server med en säker DTLS-anslutning. Servern måste ha en motsvarande Server instans i objektet Server.

DTLS-sessionen måste ha kon figurer ATS med lämpliga chiffersviter och nyckel material innan du anropar den här funktionen. **NX_SECURE_ENABLE_DTLS** måste definieras.

Om registreringen lyckas kommer LWM2M-klienten att bearbeta ytterligare åtgärder från servern och skickar regelbundet meddelanden om uppdatering tills klienten avregistreras.

Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya LWM2M.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till LWM2M för klientens session.
- **server_id** Det korta Server-ID: t för LWM2M-servern.
- **ip_address** Serverns IP-adress.
- **port** Serverns UDP-port.
- **dtls_session_ptr** DTLS-sessionen som ska användas för LWM2M-sessionen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ERROR** Start fel.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a>nx_lwm2m_client_session_register_info_get

Startar en säker session med en LWM2M-Server.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a>Beskrivning

När en kommunikations-session med en Start Server upprättats. Programmet kan anropa detta API för att hämta server-och säkerhets information för nästa registrerings steg.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till LWM2M för klientens session.
- **security_instance_id** Säkerhets instans-ID.
- **server_id** Pekare till mål serverns ID.
- **server_uri** Pekare till mål serverns URI.
- **server_uri_len** Pekare till mål serverns URI-längd.
- **security_mode** Pekare till mål säkerhets läge.
- **pub_key_or_id** Pekare till den offentliga nyckeln eller identiteten.
- **pub_key_or_id_len** Pekare till målets offentliga nyckel eller identitets längd.
- **server_pub_key** Pekare till den offentliga nyckeln för mål servern.
- **server_pub_key_len** Pekare till mål serverns offentliga nyckel längd.
- **SECRET_KEY** Pekare till målets hemliga nyckel.
- **secret_key_len** Pekare till målets hemliga nyckel längd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_NOT_FOUND** Det finns ingen säkerhets objekts instans.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Uppdaterar en session med en LWM2M-Server.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en uppdaterings åtgärd på en LWM2M-Server.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till LWM2M för klientens session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** Klienten är inte registrerad på servern.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Låser upp en LWM2M-klient.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten låser upp LWM2M-klienten som tidigare låstes av ett anrop till ***nx_lwm2m_client_unlock***.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M klient kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```