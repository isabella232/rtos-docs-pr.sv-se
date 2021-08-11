---
title: Kapitel 4 – Beskrivning av LWM2M CLIENT Services
description: Det här kapitlet innehåller en beskrivning av alla LWM2M-klienttjänster i alfabetisk ordning.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0956cb43f4fcd87d5bd4d90b2288ce6f8d5295ee0be8b8a9f4719ad842e00b2a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783449"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a>Kapitel 4 Beskrivning av LWM2M CLIENT Services

Det här kapitlet innehåller en beskrivning av alla LWM2M-klienttjänster som anges nedan i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **FETSTIL** av  **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

**LWM2M-klienthantering:**

- nx_lwm2m_client_create: *Skapa LWM2M-klient*

- nx_lwm2m_client_delete: *Ta bort LWM2M-klient*

- nx_lwm2m_client_lock: Lås *LWM2M-klient*

- nx_lwm2m_client_unlock: Låsa *upp LWM2M-klient*

**LWM2M-klientsessionshantering:**

- nx_lwm2m_client_session_create: *Skapa LWM2M-klientsession*

- nx_lwm2m_client_session_delete: Ta *bort LWM2M-klientsession*

- nx_lwm2m_client_session_bootstrap: Starta *en session med en Bootstrap-server*

- nx_lwm2m_client_session_bootstrap_dtls: Starta *en säker session med en Bootstrap-server*

- nx_lwm2m_client_session_register_info_get: Hämta *registerinformation för LWM2M-server*

- nx_lwm2m_client_session_register: Starta *en session med en LWM2M-server*

- nx_lwm2m_client_session_register_dtls: Starta *en säker session med en LWM2M-server*

- nx_lwm2m_client_session_update: Uppdatera *en session med en LWM2M-server*

- nx_lwm2m_client_session_deregister: Avsluta *en session med en LWM2M-server*

- nx_lwm2m_client_session_error_get: Hämta *det senaste felet för en session*

**Implementering av enhetsobjekt:**

- nx_lwm2m_client_device_callbacks_set: *Ange återanrop för enhetsobjektprogram*

- nx_lwm2m_client_device_error_push: Lägg *till felkod i enhetsobjektet*

- nx_lwm2m_client_device_error_reset: Återställa *felkoder för enhetsobjektet*

- nx_lwm2m_client_device_resource_changed: *Signaländring av enhetsobjektresurs*

**Objektimplementering för uppdatering av inbyggd programvara:**

- nx_lwm2m_firmware_create: Skapa *objekt för uppdatering av inbyggd programvara*

- nx_lwm2m_firmware_package_info_set: Ange *information om uppdateringspaket för inbyggd programvara*

- nx_lwm2m_firmware_result_set: Ange *resultat för uppdatering av inbyggd programvara*

- nx_lwm2m_firmware_state_set: Ange *uppdateringstillstånd för inbyggd programvara*

**Implementering av anpassade objekt:**

- nx_lwm2m_client_object_add: Lägg *till objektimplementering till LWM2M-klienten*

- nx_lwm2m_client_object_remove: Ta *bort objektimplementering från LWM2M-klienten*

- nx_lwm2m_client_object_instance_add: Lägg *till objektinstans i LWM2M-klienten*

- nx_lwm2m_client_object_instance_remove: Ta *bort objektinstans från LWM2M-klienten*

- nx_lwm2m_object_resource_changed: *Signaländring av ett resursvärde för en objektinstans*

**Lokal Enhetshantering**

- nx_lwm2m_client_object_create: Skapa *en ny objektinstans*

- nx_lwm2m_client_object_delete: Ta *bort en objektinstans*

- nx_lwm2m_client_object_discover: Identifiera *resurser för en objektinstans*

- nx_lwm2m_client_object_execute: Köra *resurs för en objektinstans*

- nx_lwm2m_client_object_next_get: *Hämta listan över objekt som implementerats av LWM2M-klienten*

- nx_lwm2m_client_object_instance_next_get: *Hämta listan över instanser av ett objekt*

- nx_lwm2m_client_object_read: Läsa *resursvärden för en objektinstans*

- nx_lwm2m_client_object_write: Ändra *resursvärden för en objektinstans*

**Inställning av resursinformation och -värden:**

- nx_lwm2m_client_resource_info_set: Ange *resursinformation*

- nx_lwm2m_client_resource_string_set: *Ange resursvärdet som sträng*

- nx_lwm2m_client_resource_integer32_set: Ange *resursvärdet som 32-bitars heltal*

- nx_lwm2m_client_resource_integer64_set: Ange *resursvärdet som 64-bitars heltal*

- nx_lwm2m_client_resource_float32_set: Ange *resursvärdet som 32-bitars flyttal*

- nx_lwm2m_client_resource_float64_set: *Ange resursvärdet som 64-bitars flyttal*

- nx_lwm2m_client_resource_boolean_set: *Ange resursvärdet som booleskt*

- nx_lwm2m_client_resource_objlnk_set: Ange *resursvärdet som objektlänk*

- nx_lwm2m_client_resource_opaque_set: Ange *resursvärdet som täckande*

- nx_lwm2m_client_resource_instance_set: Ange *resursvärdet som instans för flera resurser*
-
- nx_lwm2m_client_resource_dim_set: Ange *resursdimensionen för flera resurser.*

**Information om resurser och värden som hämtar:**

- nx_lwm2m_client_resource_info_get: Hämta *resursinformation*

- nx_lwm2m_client_resource_string_get: Hämta *värdet för en strängresurs*

- nx_lwm2m_client_resource_integer32_get: Hämta *värdet för en 32-bitars heltalsresurs*

- nx_lwm2m_client_resource_integer64_get: *Hämta värdet för en 64-bitars heltalsresurs*

- nx_lwm2m_client_resource_float32_get: Hämta *värdet för en 32-bitars flyttalsresurs*

- nx_lwm2m_client_resource_float64_get: *Hämta värdet för en 64-bitars flyttalsresurs*

- nx_lwm2m_client_resource_boolean_get: *Hämta värdet för en boolesk resurs*

- nx_lwm2m_client_resource_objlnk_get: Hämta *värdet för en objektlänkresurs*

- nx_lwm2m_client_resource_opaque_get: Hämta *värdet för en täckande resurs*

- nx_lwm2m_client_resource_instance_get: Hämta *resursinstansen för flera resurser*

- nx_lwm2m_client_resource_dim_get: Hämta *resursdimensionen för flera resurser.*

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

### <a name="description"></a>Description

Den här tjänsten skapar en LWM2M-klientinstans som körs i kontexten för en egen ThreadX-tråd.

LWM2M-klienten implementerar följande OMA LWM2M-objekt: Säkerhet (0), Server (1), Access Control (2) och Enhet (3). De andra objektimplementeringarna måste läggas till av programmet.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **packet_pool_ptr** Pekare till standardpaketpoolen för den här LWM2M-klienten.
- **name_ptr** Pekare till namnet på LWM2M-klientslutpunkten.
- **name_length** Längden på namnet på LWM2M-klientslutpunkten.
- **msisdn_ptr** Pekare till MSISDN där LWM2M-klienten kan nås för användning med SMS-bindningen, kan vara NULL om SMS-bindning inte stöds.
- **msisdn_length** Längden på MSISDN-talet.
- **binding_modes** Bindningen och lägena som stöds av LWM2M-klienten måste vara en kombination av flaggor NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S och NX_LWM2M_BINDING_SQ.
- **stack_ptr** Pekare till LWM2M-klientens trådstackområde.
- **stack_size** Storleken på LWM2M-klientens trådstack.
- **prioritet** Prioritet för LWM2M-klienten.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** LWM2M-klienten har skapats.
- **NX_LWM2M_CLIENT_ERROR** Fel när LWM2M-klienten skapas.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.
- **NX_PTR_ERROR** Ogiltig pekare.
- **NX_SIZE_ERROR** Ogiltig stackstorlek.
- **NX_OPTION_ERROR** Ogiltig prioritet.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten tar bort en tidigare skapad LWM2M-klientinstans.

Alla sessioner som för närvarande är kopplade till klienten tas också bort av det här anropet.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** LWM2M-klienten har tagits bort.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a>nx_lwm2m_client_device_callback_set

Anger ett enhetsobjekts programanrop.

### <a name="prototype"></a>Prototyp

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a>Description

Den här tjänsten installerar programmets återanrop för att implementera åtgärder på LWM2M-enhetsobjektresurser som inte hanteras av LWM2M-klienten.

LWM2M-klienten implementerar följande resurser: Felkod (11), Återställ felkod (12) och Bindning och lägen som stöds (16), åtgärder till de andra resurserna omdirigeras till programmet.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **operation_callback** Åtgärdsanropet för "Read", "Discover", "Write" och "Execute" (Kör).

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärdens återanrop har angetts.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push
Lägger till en felkod i ett enhetsobjekt.

### <a name="prototype"></a>Prototyp

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en ny instans i resursen Felkod (11) för objektenheten.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **kod** Den nya felkoden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**

Det maximala antalet lagrade felkoder har

har nåtts.

NX_PTR_ERROR ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Återställer felkoderna för enhetsobjektet.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort alla felkodresursinstanser från enhetsobjektet. Detta motsvarar att köra resursåterställningsfelkoden (12).

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Signalerar en ändring av en enhetsobjektresurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a>Description

Tjänsten används av programmet för att signalera till LWM2M-klienten att en resurs för objektenheten har ändrats. LWM2M-klienten skickar ett meddelande om resursen observeras av en LWM2M-server.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **resurs** Pekare till den struktur som beskriver den resurs som har ändrats.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a>nx_lwm2m_client_firmware_create

Skapa ett LWM2M-klientobjekt för inbyggd programvara. 

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

### <a name="description"></a>Description

Tjänsten används av programmet för att skapa objekt för inbyggd programvara.

### <a name="parameters"></a>Parametrar

- **firmware_ptr** Pekare till LWM2M-klientens objekt för inbyggd programvara.
- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **protokoll** Protokoll som stöds.
- **package_callback** Paketanropet.
- **package_uri_callback** Paket-URI-återanrop.
- **update_callback** Uppdateringsanropet.

### <a name="return-values"></a>Returvärden

**NX_SUCCESS** Åtgärden lyckades.
**NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

Anger paketinformationen för LWM2M-klientens inbyggda programvara.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a>Description

Tjänsten används av programmet för att ange paketinformationsresurserna för objektet för uppdatering av inbyggd programvara.

### <a name="parameters"></a>Parametrar

- **firmware_ptr** Pekare till LWM2M-klientens objekt för inbyggd programvara.
- **namn** Namnet på paketet för inbyggd programvara.
- **name_length** Längden på namnet.
- **version** Versionen av paketet för inbyggd programvara.
- **version_length** Längden på versionen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

Anger resursen för uppdateringsresultat för objektet för uppdatering av inbyggd programvara.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Description

Tjänsten används av programmet för att ange resursen för uppdateringsresultat för objektet för uppdatering av inbyggd programvara.

### <a name="parameters"></a>Parametrar

- **firmware_ptr** Pekare till LWM2M-klientens objekt för inbyggd programvara.
- **resultat** Uppdateringsresultatet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a>nx_lwm2m_client_firmware_state_set

Anger resursen för uppdateringsresultat för objektet för uppdatering av inbyggd programvara.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Description

Tjänsten används av programmet för att ange tillståndet för objektet för uppdatering av inbyggd programvara.

### <a name="parameters"></a>Parametrar

- **firmware_ptr** Pekare till LWM2M-klientens objekt för inbyggd programvara.
- **tillstånd** Tillståndet för objektet för inbyggd programvara.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten låser LWM2M-klienten för att förhindra samtidig åtkomst till LWM2M-objekten från servrarna eller en annan programtråd.

Om LWM2M-klienten för närvarande är låst av en annan tråd blockeras funktionen tills LWM2M-klienten låses upp.

Anrop till ***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_** par kan kapslas.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Lägger till en objektimplementering till LWM2M-klienten.

### <a name="prototype"></a>Prototyp

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en ny objektimplementering till LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **object_ptr** Pekare till den struktur som definierar objektimplementering.
- **object_id** Objekt-ID:t.
- **object_operation** Funktionen för återanrop av objektåtgärd.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Objekt-ID:t finns redan.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Skapar en ny objektinstans.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Description

Den här tjänsten utför en "Skapa"-åtgärd på ett objekt i LWM2M-klienten för att skapa en ny objektinstans.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **object_id** Objekt-ID:t.
- **instance_id_ptr** Pekare till ID för den nya instansen, kan vara **NULL** om LWM2M-klienten måste tilldela ett instans-ID. Om ID:t är det reserverade värdet 65535 tilldelar LWM2M-klienten ett instans-ID. Om inte NULL returneras det tilldelade ID:t efter anropet.
- **num_values** Antalet värden som ska anges.
- **values_ptr** Pekare till en matris med resursvärden för att initiera den nya objektinstansen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Objektinstans-ID:t finns redan.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Objektet stöder inte skapande av instanser.
- **NX_LWM2M_CLIENT_NO_MEMORY** Det går inte att allokera minne för att lagra den nya instansen.
- **NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID:t finns inte.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Tar bort en objektinstans.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Description

Den här tjänsten utför en "Delete"-åtgärd på en objektinstans av LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **object_id** Objekt-ID:t.
- **instance_id** Objektinstans-ID:t.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Objektet stöder inte borttagning av instanser.
- **NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID:t eller objektinstans-ID:t finns inte.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

Identifierar resurser för en objektinstans.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a>Description

Den här tjänsten utför en "Identifiera"-åtgärd på en objektinstans av LWM2M-klienten, vilket returnerar listan över resurser som implementeras av objektet.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **object_id** Objekt-ID: t.
- **instance_id** Objektinstans-ID:t.
- **num_resources** När du matar in storleken på målbufferten på matas antalet element som skrivits till bufferten ut.
- **resurser** Pekare till målbufferten.

### <a name="return-values"></a>Returvärden

- *NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Resursbufferten är för liten för att lagra listan över resurser.
- **NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID:t eller objektinstans-ID:t finns inte.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

Utför en Execute-åtgärd på en resurs i en objektinstans.

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

### <a name="description"></a>Description

Den här tjänsten utför åtgärden "Kör" på en objektinstansresurs för LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **object_id** Objekt-ID: t.
- **instance_id** Objektinstans-ID:t.
- **resource_id** Resurs-ID: t.
- **arguments_ptr** Pekare till argumenten för körningsåtgärden. Kan vara NULL om arguments_length är noll.
- **arguments_length** Längden på argumenten.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Resursbufferten är för liten för att lagra listan över resurser.
- **NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID:t eller objektinstans-ID:t finns inte.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a>nx_lwm2m_client_object_instance_add

Lägger till en implementering av en objektinstans till ett objekt.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en ny implementering av objektinstansen till LWM2M-klienten. Om värdet för instance_id_ptr är **NX_LWM2M_CLIENT_RESERVED_ID** tilldelar LWM2M-klienten automatiskt ett oanvänt instans-ID, annars använder LWM2M-klienten värdeuppsättningen. När den nya instansen har lagts till fylls instance_id i automatiskt instance_id_ptr att återgå till programmet.

### <a name="parameters"></a>Parametrar

- **object_ptr** Pekare till den struktur som definierar objektimplementering.
- **instance_ptr** Pekare till den struktur som definierar implementeringen av objektinstansen.
- **instance_id_ptr** Pekare till objektinstans-ID:t.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_CLIENT_LWM2M_ALREADY_EXIST** Objekt-ID:t finns redan.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten returnerar ID:t för nästa objektinstans för det angivna objektet. Om det aktuella instans-ID:t är NX_LWM2M_RESERVED_ID (65535) returneras ID:t för den första instansen.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **object_id** Objekt-ID: t.
- **instance_id_ptr** Pekare till aktuellt objektinstans-ID. Vid retur innehåller nästa instans-ID för objektet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_CLIENT_LWM2M_NOT_FOUND** Det angivna instans-ID:t är det sista av objektet, eller så implementeras inte objekt-ID:t.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a>nx_lwm2m_client_object_instance_remove

Tar bort en implementering av en objektinstans från ett objekt.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en objektinstans från ett objekt.

### <a name="parameters"></a>Parametrar

- ***object_ptr*** Pekare till den struktur som definierar objektimplementering.
- **instance_ptr** Pekare till den struktur som definierar implementeringen av objektinstansen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Objekt-ID:t finns redan.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten returnerar ID:t för nästa objekt som implementeras av LWM2M-klienten. Om aktuellt objekt-ID är inställt på NX_LWM2M_RESERVED_ID (65535) returneras det första objekt-ID:t.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **object_id_ptr** Pekare till aktuellt objekt-ID. Vid retur innehåller nästa objekt-ID som implementeras av LWM2M-klienten.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_NOT_FOUND** Det angivna objekt-ID:t är det sista i databasen.
**NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Läser en objektinstanss resursvärden.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Description

Den här tjänsten utför en läsåtgärd på en objektinstans av LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **object_id** Objekt-ID: t.
- **instance_id** Objektinstans-ID:t.
- **num_values** Antalet resurser som ska läsas.
- **values_ptr** Pekare till en matris NX_LWM2M_RESOURCE som innehåller DE RESURSERS-ID:er som ska läsas. När matrisen returneras fylls den med motsvarande typer och värden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** En resurs stöder inte läsåtgärden.
- **NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID, objektinstans-ID eller resurs-ID finns inte.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a>nx_lwm2m_client_object_remove

Tar bort en implementering av en objektinstans från ett objekt.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort ett objekt från LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **object_ptr** Pekare till den struktur som definierar objektimplementering.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Objekt-ID:t finns redan.
- **NX_PTR_ERROR** Ogiltig pekare.
- **NX_LWM2M_CLIENT_FORBIDDEN** Det är förbjudet att ta bort interna objekt.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a>nx_lwm2m_client_object_resource_changed

Signalerar en ändring av en objektresurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Description

Tjänsten används av programmet för att signalera till LWM2M-klienten att en resurs i objektet har ändrats. LWM2M-klienten skickar ett meddelande om resursen observeras av en LWM2M-server.

### <a name="parameters"></a>Parametrar

- **object_ptr** Pekare till den struktur som definierar objektimplementering.
- ***instance_ptr*** Pekare till den struktur som definierar implementeringen av objektinstansen.
- **resurs** Pekar på strukturen som beskriver den resurs som har ändrats.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Ändrar resursens värden för en objektinstans.

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

### <a name="description"></a>Description

Den här tjänsten utför en skrivåtgärd på en objektinstans av LWM2M-klienten.

Följande skrivåtgärder kan anges för den *write_op* parametern.

| Värde | &nbsp;Skrivåtgärd | Beskrivning |
| --- | ---| --- |
| 0 | Partiell uppdatering | Lägger till eller uppdaterar resurser som anges i det nya värdet och lämnar andra befintliga resurser oförändrade. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Ersätt instans | Ersätter objektinstansen med de nya angivna resursvärdena. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** | Ersätt resurs | Ersätter resurserna med de nya angivna resursvärdena (används för att ersätta flera resurser). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Bootstrap-skrivning | Anger ett anrop från en Bootstrap-sekvens. |

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.
- **object_id** Objekt-ID: t.
- **instance_id** Objektinstans-ID:t.
- **num_values** Antalet resurser som ska skrivas.
- **values_ptr** Pekare till en matris NX_LWM2M_RESOURCE som innehåller RESURSERNAs,de typer och värden som ska skrivas.
- **write_op** Typ av skrivåtgärd.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Typen av resurs är inte giltig.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Längden på ett värde är för stor för att lagras i instansen.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** En resurs stöder inte skrivåtgärden.
- **NX_LWM2M_CLIENT_NO_MEMORY** Det går inte att allokera minne för att lagra ett resursvärde.
- **NX_LWM2M_CLIENT_NOT_ACCEPTABLE** Värdet för en resurs är inte giltigt.
- **NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID, objektinstans-ID eller resurs-ID finns inte.
- **NX_OPTION_ERROR** Ogiltig typ av skrivåtgärd. 
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Tjänsten hämtar värdet för en boolesk resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Beskrivning av resursvärde.
- **bool_ptr** Pekare till det booleska målvärdet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursvärdet är inte ett booleskt värde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Tjänsten anger värdet för en boolesk resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **bool_data** Booleska data.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a>nx_lwm2m_client_resource_dim_get

Hämtar resursdimensionen för flera resurser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a>Description

Tjänsten hämtar resursdimensionen för flera resurser.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **tona** pekaren till måldimensionen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursvärdet är inte ett booleskt värde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a>nx_lwm2m_client_resource_dim_set

Anger resursdimensionen för flera resurser.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a>Description

Tjänsten anger resursdimensionen för flera resurser.

### <a name="parameters"></a>Parametrar

- **värde** Pekare till Beskrivning av resursvärde.
-  dim-dimensionsvärde.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a>nx_lwm2m_client_resource_float32_get

Hämtar värdet för en 32-bitars **flyttalsresurs**

### <a name="prototype"></a>Prototyp

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en 32-bitars **flyttalsresurs.**

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **float32_ptr** Pekare till målets 32-bitars **flyttal.**

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursvärdet är inte ett booleskt värde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a>nx_lwm2m_client_resource_float32_set

Anger värdet för en 32-bitars **flyttalsresurs**

### <a name="prototype"></a>Prototyp

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a>Description

Tjänsten anger värdet för en 32-bitars **flyttalsresurs.**

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **float32_data** 32-bitars **flyttalsdata.**

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a>nx_lwm2m_client_resource_float64_get

Hämtar värdet för en 64-bitars flyttalsresurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en 64-bitars **flyttalsresurs.**

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **float64_ptr** Pekare till målets 64-bitars **flyttal.**

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursvärdet är inte ett flyttal.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a>nx_lwm2m_client_resource_float64_set

Anger värdet för en 64-bitars **flyttalsresurs.**

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Description

Tjänsten anger värdet för en 64-bitars **flyttalsresurs.**

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **float64_data** 64-bitars **flyttalsdata.**

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a>nx_lwm2m_client_resource_info_get

Hämtar resursinformationen.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a>Description

Tjänsten hämtar resursinformationen för resursen.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **resource_id** Pekare till målresursens ID.
- **åtgärd** Pekare till målresursåtgärden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a>nx_lwm2m_client_resource_info_set

Anger resursinformationen.

### <a name="prototype"></a>Prototyp

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Description

Tjänsten anger resursinformationen.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **resource_id** ID för resursen.
- **åtgärd** Åtgärden för resursen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Tjänsten hämtar resursinformationen för resursen.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **resource_instances** Pekare till målresursens ID.
- **antal** Pekare till antalet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursvärdet är inte ett booleskt värde.
- **NX_LWM2M_CLIENT_NO_MEMORY** Inget minne för att fylla i instanser.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a>nx_lwm2m_client_resource_instances_set

Anger resursinstanserna.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a>Description

Tjänsten anger resursinstanser för flera resurser.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **resource_instance** Pekare till resursinstanser.
- **antal** Antal resursinstanser.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a>nx_lwm2m_client_resource_integer32_get

Hämtar värdet för en 32-bitars heltalsresurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en 32-bitars heltalsresurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **integer32_ptr** Pekare till 32-bitars heltalsvärde.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursvärdet är inte ett heltalsvärde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a>nx_lwm2m_client_resource_integer32_set

Anger värdet för en 32-bitars heltalsresurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a>Description

Tjänsten anger värdet för en 32-bitars heltalsresurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **integer32_data** 32-bitars heltalsdata.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a>nx_lwm2m_client_resource_integer64_get

Hämtar värdet för en 64-bitars heltalsresurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en 64-bitars heltalsresurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **integer64_ptr** Pekare till 64-bitars heltalsvärdet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursvärdet är inte 64-bitars heltalsvärde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a>nx_lwm2m_client_resource_integer64_set

## <a name="set-the-value-of-a-64-bit-integer-resource"></a>Ange värdet för en 64-bitars heltalsresurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a>Description

Tjänsten anger värdet för en 64-bitars heltalsresurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **integer64_data** 64-bitars heltal.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a>nx_lwm2m_client_resource_objlnk_get

Hämtar värdet för en objektlänkresurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för objektlänken.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **object_id** Pekare till objekt-ID:t.
- **instance_id** Pekare till objektinstans-ID:t.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursvärdet är inte ett objektlänkvärde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a>nx_lwm2m_client_resource_objlnk_set

Anger resursinstanserna

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Description

Tjänsten anger värdet för objektlänkresursen.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **object_id** Objekt-ID.
- **instance_id** Objektinstans-ID.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a>nx_lwm2m_client_resource_opaque_get

Hämtar värdet för en täckande resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a>Description

Tjänsten hämtar värdet för en täckande resurs. Ett täckande resursvärde består av en pekare till en buffert och en längd.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **opaque_ptr** Pekare till täckande data.
- **opaque_length** Pekare till den täckande datalängden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursvärdet är inte en täckande resurs.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a>nx_lwm2m_client_resource_opaque_set

Anger värdet för en täckande resurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a>Description

Tjänsten anger värdet för en täckande resurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **opaque_ptr** Pekare till täckande data.
- **opaque_length** Längden på täckande data.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a>nx_lwm2m_client_resource_string_get

Hämtar värdet för en strängresurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en strängresurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **string_ptr** Pekare till målsträngens pekare.
- **string_length** Pekare till målsträngens längd. Kan vara **NULL** om strängen är null-avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Resursvärdet är inte ett strängvärde.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a>nx_lwm2m_client_resource_string_set

Anger värdet för en strängresurs.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a>Description

Tjänsten anger värdet för en 64-bitars heltalsresurs.

### <a name="parameters"></a>Parametrar

- **resurs** Pekare till Resurs.
- **string_ptr** Pekare till strängen.
- **string_length** Strängens längd.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Startar en session med en Bootstrap-server.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a>Description

Den här tjänsten startar en session med en Bootstrap-server. Servern ska ha en motsvarande säkerhetsinstans i säkerhetsobjektet.

Om resursen "Håll av" skiljer sig från noll i den säkerhetsinstans som är associerad med den här servern väntar sessionen på en serverinitierad bootstrap. Om ingen bootstrap initieras av servern efter den här tidsperioden utförs en klientinitierad boostrap.

Alla aktiva sessioner avbryts av det här anropet och ersätts av den nya Bootstrap Server-sessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till kontrollblocket för LWM2M-klientsession.
- **security_id** Säkerhetsinstans-ID för Bootstrap-servern måste anges till NX_LWM2M_RESERVED_ID (65535) om Bootstrap-servern inte har någon definierad säkerhetsinstans.
- **ip_address** IP-adressen för servern.
- **port** UDP-porten för servern.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ERROR** Bootstrap-fel.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Startar en säker session med en Bootstrap-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten startar en session med en Bootstrap-server med hjälp av en säker DTLS-anslutning. Servern ska ha en motsvarande säkerhetsinstans i säkerhetsobjektet.

DTLS-sessionen måste ha konfigurerats med rätt chiffersviter och nyckelmaterial innan den här funktionen anropas. **NX_SECURE_ENABLE_DTLS** måste definieras.

Om resursen "Håll av" skiljer sig från noll i den säkerhetsinstans som är associerad med den här servern väntar sessionen på en serverinitierad bootstrap, om ingen bootstrap initieras av servern efter den här tidsperioden utförs en klientinitierad boostrap. 

Alla aktiva sessioner avbryts av det här anropet och ersätts av den nya Bootstrap Server-sessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till kontrollblocket för LWM2M-klientsession.
- **security_id** Säkerhetsinstans-ID för Bootstrap-servern måste anges till **NX_LWM2M_RESERVED_ID** (65535) om Bootstrap-servern inte har någon definierad säkerhetsinstans.
- **ip_address** IP-adressen för servern.
- **port** UDP-porten för servern.
- **dtls_session_ptr** DTLS-sessionen som ska användas för Bootstrap-sessionen.
- **dtls_local_port** Den lokala UDP-porten som används för DTLS-sessionen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ERROR** Bootstrap-fel.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar en ny LWM2M-klientsession som är kopplad till en befintlig LWM2M-klient. Sessionen används av LWM2M-klienten för att kommunicera med en Bootstrap-server eller en LWM2M-server. 

Programmet måste tillhandahålla en återanropsfunktion som anropas när sessionens tillstånd uppdateras.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till kontrollblocket för LWM2M-klientsession.
- **client_ptr** Pekare till LWM2M-klienten som du skapade tidigare.
- **state_callback** Programanrop som anropas när sessionens tillstånd har ändrats.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten tar bort en LWM2M-klientsession.

När en LWM2M-klient tas bort genom nx_lwm2m_client_delete alla sessioner som är kopplade till klienten tas också bort.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till kontrollblocket för LWM2M-klientsession.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Avslutar en session med en LWM2M-server.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten utför en "Avregistrera"-åtgärd till en LWM2M-server.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till kontrollblocket för LWM2M-klientsession.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** Klienten är inte registrerad på servern.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Hämtar det sista felet för en session.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten returnerar felkoden för sessionen när sessionen är i ett feltillstånd.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till kontrollblocket för LWM2M-klientsession.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Sessionen är inte i feltillstånd.
- **NX_LWM2M_CLIENT_ADDRESS_ERROR** Ogiltig serveradress.
- **NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Nyttolasten för begäran får inte plats i nätverksbufferten.
- **NX_LWM2M_ CLIENT_DTLS_ERROR** Det gick inte att upprätta en säker anslutning med servern.
- **NX_LWM2M_ CLIENT_ERROR** Ospecificerat fel.
- **NX_LWM2M_ CLIENT_FORBIDDEN** Registreringen nekades av servern.
- **NX_LWM2M_ CLIENT_NOT_FOUND** Klienten hittades inte av servern vid uppdatering/avregistrering.
- **NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** Serverobjektinstansen som motsvarar sessionen har tagits bort.
- **NX_LWM2M_ CLIENT_TIMED_OUT** Inget svar från servern.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Startar en session med en LWM2M-server.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a>Description

Den här tjänsten utför en registeråtgärd till en LWM2M-server. Servern måste ha en motsvarande serverinstans i serverobjektet.

Om registreringen lyckas bearbetar LWM2M-klienten ytterligare åtgärder från servern och skickar regelbundet uppdateringsmeddelanden tills klienten avregistreras.

Alla aktiva sessioner avbryts av det här anropet och ersätts av den nya LWM2M-serversessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till kontrollblocket för LWM2M-klientsession.
- **server_id** Kort server-ID för LWM2M-servern.
- **ip_address** IP-adressen för servern.
- **port** UDP-porten för servern.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ERROR** Bootstrap-fel.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Startar en säker session med en LWM2M-server.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten utför en registeråtgärd till en LWM2M-server med hjälp av en säker DTLS-anslutning. Servern måste ha en motsvarande serverinstans i serverobjektet.

DTLS-sessionen måste ha konfigurerats med rätt chiffersviter och nyckelmaterial innan den här funktionen anropas. **NX_SECURE_ENABLE_DTLS** måste definieras.

Om registreringen lyckas bearbetar LWM2M-klienten ytterligare åtgärder från servern och skickar regelbundet uppdateringsmeddelanden tills klienten avregistreras.

Alla aktiva sessioner avbryts av det här anropet och ersätts av den nya LWM2M-serversessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till kontrollblocket för LWM2M-klientsession.
- **server_id** Kort server-ID för LWM2M-servern.
- **ip_address** IP-adressen för servern.
- **port** UDP-porten för servern.
- **dtls_session_ptr** DTLS-sessionen som ska användas för LWM2M-sessionen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_ERROR** Bootstrap-fel.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a>nx_lwm2m_client_session_register_info_get

Startar en säker session med en LWM2M-server.

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

### <a name="description"></a>Description

När en kommunikationssession med en Bootstrap-server hade upprättats. Programmet kan anropa det här API:et för att hämta server- och säkerhetsinformation för nästa registreringssteg.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till LWM2M-klientsessionskontrollblocket.
- **security_instance_id** Säkerhetsinstans-ID.
- **server_id** Pekare till målserverns ID.
- **server_uri** Pekare till målserverns URI.
- **server_uri_len** Pekare till målserverns URI-längd.
- **security_mode** Pekare till målsäkerhetsläge.
- **pub_key_or_id** Pekare till den offentliga målnyckeln eller identiteten.
- **pub_key_or_id_len** Pekare till den offentliga målnyckeln eller identitetslängden.
- **server_pub_key** Pekare till den offentliga målserverns nyckel.
- **server_pub_key_len** Pekare till målserverns offentliga nyckellängd.
- **secret_key** Pekare till målhemlighetsnyckel.
- **secret_key_len** Pekare till målhemlighetens nyckellängd.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_NOT_FOUND** Det finns ingen säkerhetsobjektinstans.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Uppdaterar en session med en LWM2M-server.

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten utför en uppdateringsåtgärd till en LWM2M-server.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till LWM2M-klientsessionskontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** Klienten är inte registrerad på servern.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten låser upp LWM2M-klienten som tidigare låsts av ett anrop ***till nx_lwm2m_client_unlock***.

### <a name="parameters"></a>Parametrar

- **client_ptr** Pekare till LWM2M-klientkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** Åtgärden lyckades.
- **NX_PTR_ERROR** Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```