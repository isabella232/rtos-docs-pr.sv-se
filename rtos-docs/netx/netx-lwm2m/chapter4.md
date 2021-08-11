---
title: Kapitel 4 – Beskrivning Azure RTOS NetX LWM2M-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX LWM2M-tjänster (listas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 171f8577d252027548c24ec92f11f03c1fae768f1676f476256c13b8e8dc4175
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799089"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a>Kapitel 4 – Beskrivning Azure RTOS NetX LWM2M-tjänster

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX LWM2M-tjänster (listas nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **FETSTIL** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

### <a name="lwm2m-client-management"></a>LWM2M-klienthantering

- **nx_lwm2m_client_create:** Skapa *LWM2M-klient*
- **nx_lwm2m_client_delete:** Ta *bort LWM2M-klient*
- **nx_lwm2m_client_lock:** *Lås LWM2M-klienten*
- **nx_lwm2m_client_object_add:** Lägg *till objektimplementering till LWM2M-klienten*
- **nx_lwm2m_client_unlock:** Låsa *upp LWM2M-klient*

### <a name="lwm2m-client-session-management"></a>LWM2M-klientsessionshantering

- **nx_lwm2m_client_session_bootstrap:** Starta *en session med en Bootstrap-server*
- **nx_lwm2m_client_session_bootstrap_dtls:** Starta *en säker session med en Bootstrap-server*
- **nx_lwm2m_client_session_create:** Skapa *LWM2M-klientsession*
- **nx_lwm2m_client_session_delete:** *Ta bort LWM2M-klientsession*
- **nx_lwm2m_client_session_deregister:** Avsluta *en session med en LWM2M-server*
- **nx_lwm2m_client_session_error_get:** Hämta *det senaste felet för en session*
- **nx_lwm2m_client_session_register:** Starta *en session med en LWM2M-server*
- **nx_lwm2m_client_session_register_dtls:** Starta *en säker session med en LWM2M-server*
- **nx_lwm2m_client_session_update:** Uppdatera *en session med en LWM2M-server*

### <a name="security-object-implementation"></a>Implementering av säkerhetsobjekt

- **nx_lwm2m_client_security_key_callbacks_set:** Ange *återanrop för hantering av säkerhetsnyckel*

### <a name="device-object-implementation"></a>Implementering av enhetsobjekt

- **nx_lwm2m_client_device_callbacks_set:** Ange *återanrop för enhetsobjektprogram*
- **nx_lwm2m_client_device_error_push:** Lägg *till felkod i enhetsobjektet*
- **nx_lwm2m_client_device_error_reset:** Återställa *felkoder för enhetsobjektet*
- **nx_lwm2m_client_device_resource_changed:** *Signaländring av enhetsobjektresurs*

### <a name="custom-objects-implementation"></a>Implementering av anpassade objekt

- **nx_lwm2m_object_resource_changed:** *Signaländring av ett resursvärde för en objektinstans*

### <a name="local-device-management"></a>Lokal Enhetshantering

- **nx_lwm2m_client_object_create:** Skapa *en ny objektinstans*
- **nx_lwm2m_client_object_delete:** Ta *bort en objektinstans*
- **nx_lwm2m_client_object_discover:** *Identifiera resurser för en objektinstans*
- **nx_lwm2m_client_object_execute:** Köra *resurs för en objektinstans*
- **nx_lwm2m_client_object_get_next:** Hämta *listan över objekt som implementeras av LWM2M-klienten*
- **nx_lwm2m_client_object_instance_get_next:** Hämta *listan över instanser av ett objekt*
- **nx_lwm2m_client_object_read:** Läsa *resursvärden för en objektinstans*
- **nx_lwm2m_client_object_write:** Ändra *resursvärden för en objektinstans*

### <a name="resources-values-decoding"></a>Avkodning av resursvärden

- **nx_lwm2m_resource_get_boolean:** *Hämta värdet för en boolesk resurs*
- **nx_lwm2m_resource_get_float32:** Hämta *värdet för en 32-bitars flyttalsresurs*
- **nx_lwm2m_resource_get_float64:** *Hämta värdet för en 64-bitars flyttalsresurs*
- **nx_lwm2m_resource_get_integer32:** Hämta *värdet för en 32-bitars heltalsresurs*
- **nx_lwm2m_resource_get_integer64:** Hämta *värdet för en 64-bitars heltalsresurs*
- **nx_lwm2m_resource_get_objlnk:** Hämta *värdet för en objektlänkresurs*
- **nx_lwm2m_resource_get_opaque:** Hämta *värdet för en täckande resurs*
- **nx_lwm2m_resource_get_string:** Hämta *värdet för en strängresurs*
- **nx_lwm2m_resource_multiple_get_boolean:** Hämta *värdet för en boolesk resurs med flera resursinstanser*
- **nx_lwm2m_resource_multiple_get_float32:** Hämta *värdet för en 32-bitars flyttal med flera resursinstanser*
- **nx_lwm2m_resource_multiple_get_float64:** Hämta *värdet för en 64-bitars flyttal med flera resursinstanser*
- **nx_lwm2m_resource_multiple_get_integer32:** *Hämta värdet för ett 32-bitars heltal med flera resursinstanser*
- **nx_lwm2m_resource_multiple_get_integer64:** *Hämta värdet för en 64-bitars heltal för flera resursinstanser*
- **nx_lwm2m_resource_multiple_get_objlnk:** Hämta *värdet för en objektlänk för flera resursinstanser*
- **nx_lwm2m_resource_multiple_get_opaque:** Hämta *värdet för en täckande flerresursinstans*
- **nx_lwm2m_resource_multiple_get_string:** Hämta *värdet för en sträng med flera resursinstanser*

### <a name="firmware-update-object"></a>Objekt för uppdatering av inbyggd programvara

- **nx_lwm2m_firmware_create: Skapa** *objekt för uppdatering av inbyggd programvara*
- **nx_lwm2m_firmware_package_info_set: Ange** *information om uppdateringspaket för inbyggd programvara*
- **nx_lwm2m_firmware_result_set: Ange** *resultat för uppdatering av inbyggd programvara*
- **nx_lwm2m_firmware_state_set: Ange** *uppdateringstillstånd för inbyggd programvara*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Skapa LWM2M-klient

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en LWM2M-klientinstans som körs i kontexten för en egen ThreadX-tråd.

LWM2M-klienten implementerar följande OMA LWM2M-objekt: Säkerhet (0), Server (1), Access Control (2) och Enhet (3). De andra objektimplementeringarna måste läggas till av programmet.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblocket.
- **ip_ptr:** Pekare till ip-instans som skapats tidigare.
- **packet_pool_ptr:** Pekare till standardpaketpoolen för den här LWM2M-klienten.
- **local_port:** Den lokala UDP-porten som används för icke-säker kommunikation.
- **name_ptr:** Pekare till namnet på LWM2M-klientslutpunkten.
- **msisdn_ptr:** Pekare till MSISDN där LWM2M-klienten kan nås för användning med SMS-bindningen kan vara NULL om SMS-bindning inte stöds.
- **binding_modes:** Bindningen och lägena som stöds av LWM2M-klienten måste vara en kombination av flaggor NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S och NX_LWM2M_BINDING_SQ.
- **stack_ptr:** Pekare till LWM2M-klienttrådstackområdet.
- **stack_size:** Storleken på LWM2M-klienttrådstacken.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** LWM2M-klienten har skapats.
- **NX_LWM2M_ERROR:** LWM2M Client create error.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

Ta bort LWM2M-klient

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en tidigare skapad LWM2M-klientinstans.

Alla sessioner som för närvarande är kopplade till klienten tas också bort med det här anropet.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** LWM2M-klienten har tagits bort.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_device_callbacks_set"></a>nx_lwm2m_client_device_callbacks_set

Ange återanrop för enhetsobjektprogram

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a>Description

Den här tjänsten installerar programanrop för att implementera åtgärder på LWM2M-enhetsobjektresurser som inte hanteras av LWM2M-klienten.

LWM2M-klienten implementerar följande resurser: Felkod (11), Återställ felkod (12) och Bindning och lägen som stöds (16), åtgärder till de andra resurserna omdirigeras till programmet.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **read_callback:** Motringningsmetoden "Läsa".
- **discover_callback:** Motringningsmetoden "Identifiera".
- **write_callback:** Återanrop av metoden "Write".
- **execute_callback:** Motringningsmetoden "Kör".

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push

Lägga till felkod i enhetsobjektet

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en ny instans i resursen Felkod (11) för objektenheten.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **kod:** Den nya felkoden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BUFFER_TOO_SMALL:** Det maximala antalet lagrade felkoder har uppnåtts.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Återställa felkoder för enhetsobjekt

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort alla felkodresursinstanser från enhetsobjektet. Detta motsvarar att köra resursåterställningsfelkoden (12).

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Signaländring av enhetsobjektresurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Description

Tjänsten används av programmet för att signalera till LWM2M-klienten att en resurs för objektenheten har ändrats. LWM2M-klienten skickar ett meddelande om resursen observeras av en LWM2M-server.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **resource**: Pekare till den struktur som beskriver den resurs som har ändrats.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Låsa LWM2M-klienten

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten låser LWM2M-klienten för att förhindra samtidig åtkomst till LWM2M-objekten från servrarna eller en annan programtråd.

Om LWM2M-klienten för närvarande är låst av en annan tråd blockeras funktionen tills LWM2M-klienten låses upp.

Anrop till nx_lwm2m_client_lock()/nx_lwm2m_client_unlock()-par kan kapslas.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Lägga till objektimplementering till LWM2M-klienten

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en ny objektimplementering till LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **object_ptr**: Pekare till den struktur som definierar objektimplementering.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_ALREADY_EXIST:** Objekt-ID:t finns redan.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Skapa en ny objektinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Description

Den här tjänsten utför en "Skapa"-åtgärd på ett objekt i LWM2M-klienten för att skapa en ny objektinstans.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **object_id:** Objekt-ID:t.
- **instance_id_ptr:** Pekare till ID:t för den nya instansen kan vara NULL om LWM2M-klienten måste tilldela ett instans-ID. Om ID:t är det reserverade värdet 65535 tilldelar LWM2M-klienten ett instans-ID. Om inte NULL returneras det tilldelade ID:t efter anropet.
- **num_values:** Antalet värden som ska anges.
- **values_ptr:** Pekare till en matris med resursvärden för att initiera den nya objektinstansen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_ALREADY_EXIST:** Objektinstans-ID:t finns redan.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** Objektet stöder inte skapande av instanser.
- **NX_LWM2M_NO_MEMORY: Det** går inte att allokera minne för att lagra den nya instansen.
- **NX_LWM2M_NOT_FOUND:** Objekt-ID:t finns inte.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Ta bort en objektinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Description

Den här tjänsten utför en "Delete"-åtgärd på en objektinstans av LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **object_id:** Objekt-ID:t.
- **instance_id:** Objektinstans-ID:t.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** Objektet stöder inte borttagning av instanser.
- **NX_LWM2M_NOT_FOUND:** Objekt-ID:t eller objektinstans-ID:t finns inte.
- NX_PTR_ERROR ogiltig pekare.

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

Identifiera resurser för en objektinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a>Description

Den här tjänsten utför en identifieringsåtgärd på en objektinstans av LWM2M-klienten. Detta returnerar listan över resurser som implementeras av objektet.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **object_id:** Objekt-ID:t.
- **instance_id:** Objektinstans-ID:t.
- **num_resources_ptr:** När du matar in storleken på målbufferten matar du ut antalet element som skrivits till bufferten.
- **resources_ptr:** Pekare till målbufferten.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades..
- **NX_LWM2M_BUFFER_TOO_SMALL:** Resursbufferten är för liten för att lagra listan över resurser.
- **NX_LWM2M_NOT_FOUND:** Objekt-ID:t eller objektinstans-ID:t finns inte.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

Köra en objektinstanss resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a>Description

Den här tjänsten utför åtgärden "Kör" på en objektinstansresurs för LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **object_id:** Objekt-ID:t.
- **instance_id:** Objektinstans-ID:t.
- **resource_id:** Resurs-ID.
- **arguments_ptr:** Pekare till argumenten för körningsåtgärden. Kan vara NULL om arguments_length är noll.
- **arguments_length:** Längden på argumenten.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** Resursen stöder inte körningsåtgärden.
- **NX_LWM2M_NOT_FOUND:** Objekt-ID, objektinstans-ID eller resurs-ID finns inte.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_object_get_next"></a>nx_lwm2m_client_object_get_next

Hämta listan över objekt som implementerats av LWM2M-klienten

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a>Description

Den här tjänsten returnerar ID:t för nästa objekt som implementeras av LWM2M-klienten. Om det aktuella objekt-ID:t är NX_LWM2M_RESERVED_ID (65535) returneras det första objekt-ID:t.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **object_id_ptr:** Pekare till aktuellt objekt-ID. Vid retur innehåller nästa objekt-ID som implementeras av LWM2M-klienten.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades..
- **NX_LWM2M_NOT_FOUND:** Det angivna objekt-ID:t är det sista i databasen.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_object_instance_get_next"></a>nx_lwm2m_client_object_instance_get_next

Hämta listan över instanser av ett objekt

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Description

Den här tjänsten returnerar ID:t för nästa objektinstans för det angivna objektet. Om det aktuella instans-ID:t är NX_LWM2M_RESERVED_ID (65535) returneras ID:t för den första instansen.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **object_id:** Objekt-ID:t.
- **instance_id_ptr: Pekare** till det aktuella objektinstans-ID:t. Vid retur innehåller nästa instans-ID för objektet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades..
- **NX_LWM2M_NOT_FOUND:** Det angivna instans-ID:t är det sista objektet, eller så implementeras inte objekt-ID:t.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Läsa resursvärden för en objektinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Description

Den här tjänsten utför en läsåtgärd på en objektinstans av LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **object_id:** Objekt-ID:t.
- **instance_id:** Objektinstans-ID:t.
- **num_values:** Antalet resurser som ska läsas.
- **values_ptr:** Pekare till en matris med NX_LWM2M_RESOURCE som innehåller DE RESURSER som ska läsas. Vid retur fylls matrisen med motsvarande typer och värden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** En resurs stöder inte läsåtgärden.
- **NX_LWM2M_NOT_FOUND:** Objekt-ID, objektinstans-ID eller resurs-ID finns inte.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Ändra resursvärden för en objektinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a>Description

Den här tjänsten utför en skrivningsåtgärd på en objektinstans av LWM2M-klienten.

Följande skrivåtgärder kan anges för den *write_op* parametern:

- **0** &mdash; Partiell uppdatering: Lägger till eller uppdaterar resurser som anges i det nya värdet och lämnar andra befintliga resurser oförändrade,

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Ersätt instans: ersätter objektinstansen med de nya angivna resursvärdena.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Ersätt resurs: ersätter resurser med de nya angivna resursvärdena (används för att ersätta flera resurser).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: anger ett anrop från en Bootstrap-sekvens.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **object_id:** Objekt-ID:t.
- **instance_id:** Objektinstans-ID:t.
- **num_values:** Antalet resurser som ska skrivas.
- **values_ptr:** Pekare till en matris med NX_LWM2M_RESOURCE som innehåller RESURSERNAs,de typer och värden som ska skrivas.
- **write_op:** Typen av skrivåtgärd.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING:** Typen av en resurs är inte giltig.
- **NX_LWM2M_BUFFER_TOO_SMALL:** Längden på ett värde är för stor för att lagras i instansen.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** En resurs stöder inte skrivåtgärden.
- **NX_LWM2M_NO_MEMORY: Det** går inte att allokera minne för att lagra ett resursvärde.
- **NX_LWM2M_NOT_ACCEPTABLE:** Värdet för en resurs är inte giltigt.
- **NX_LWM2M_NOT_FOUND:** Objekt-ID, objektinstans-ID eller resurs-ID finns inte.
- NX_OPTION_ERROR: Ogiltig typ av skrivåtgärd.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a>nx_lwm2m_client_security_key_callbacks_set

Ange återanrop för nyckelhantering för säkerhetsobjekt

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a>Description

Den här tjänsten installerar programanrop för att implementera åtgärder på LWM2M Security Object-resurser som är relaterade till säkerhetsnycklarna.

LWM2M-klienten delegerar hanteringen av säkerhetsnyckeln till programmet under Bootstrap-sessionerna. Återanrop anropas när Bootstrap-servern skriver eller tar bort följande resurser på en instans av säkerhetsobjekt: offentlig nyckel eller identitet (3), offentlig servernyckel (4), hemlig nyckel (5).

Programmet ansvarar för att lagra nyckeldata och för att konfigurera de DTLS-sessioner som används av LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblock.
- **write_callback:** Återanropet "Skriv"-nyckelmetoden.
- **delete_callback:** Återanropet "Ta bort"-nyckelmetoden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Starta en session med en Bootstrap-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Description

Den här tjänsten startar en session med en Bootstrap-server. Servern ska ha en motsvarande säkerhetsinstans i säkerhetsobjektet.

Om resursen "Håll av" skiljer sig från noll i den säkerhetsinstans som är associerad med den här servern väntar sessionen på en serverinitierad bootstrap, om ingen bootstrap initieras av servern efter den här tidsperioden utförs en klientinitierad boostrap.

Alla aktiva sessioner avbryts av det här anropet och ersätts av den nya Bootstrap Server-sessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr:** Pekare till LWM2M-klientsessionskontrollblock.
- **security_id:** Säkerhetsinstans-ID för Bootstrap-servern måste anges till NX_LWM2M_RESERVED_ID (65535) om Bootstrap-servern inte har någon definierad säkerhetsinstans.
- **ip_address:** SERVERNS IP-adress.
- **port:** Serverns UDP-port.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_NOT_FOUND:** Det finns ingen instans av säkerhetsobjekt som motsvarar säkerhetsinstansens ID.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Starta en säker session med en Bootstrap-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Description

Den här tjänsten startar en session med en Bootstrap-server med hjälp av en säker DTLS-anslutning. Servern ska ha en motsvarande säkerhetsinstans i säkerhetsobjektet.

DTLS-sessionen måste ha konfigurerats med rätt chiffersviter och nyckelmaterial innan den här funktionen anropas. NX_SECURE_ENABLE_DTLS måste definieras.

Om resursen "Håll av" skiljer sig från noll i den säkerhetsinstans som är associerad med den här servern väntar sessionen på en serverinitierad bootstrap, om ingen bootstrap initieras av servern efter den här tidsperioden utförs en klientinitierad boostrap.

Alla aktiva sessioner avbryts av det här anropet och ersätts av den nya Bootstrap Server-sessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr:** Pekare till LWM2M-klientsessionskontrollblock.
- **security_id:** Säkerhetsinstans-ID för Bootstrap-servern måste anges till NX_LWM2M_RESERVED_ID (65535) om Bootstrap-servern inte har någon definierad säkerhetsinstans.
- **ip_address:** SERVERNS IP-adress.
- **port:** Serverns UDP-port.
- **dtls_session_ptr:** DTLS-sessionen som ska användas för Bootstrap-sessionen.
- **dtls_local_port:** Den lokala UDP-porten som används för DTLS-sessionen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_NOT_FOUND:** Det finns ingen instans av säkerhetsobjekt som motsvarar säkerhetsinstansens ID.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Skapa LWM2M-klientsession

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Description

Den här tjänsten skapar en ny LWM2M-klientsession som är ansluten till en befintlig LWM2M-klient. Sessionen används av LWM2M-klienten för att kommunicera med en Bootstrap-server eller en LWM2M-server.

Programmet måste tillhandahålla en återanropsfunktion som anropas när sessionens tillstånd uppdateras.

### <a name="parameters"></a>Parametrar

- **session_ptr:** Pekare till LWM2M-klientsessionskontrollblock.
- **client_ptr:** Pekare till LWM2M-klienten som du skapade tidigare.
- **state_callback:** Programanrop som anropas när sessionens tillstånd har ändrats.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Ta bort LWM2M-klientsession

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en LWM2M-klientsession.

När en LWM2M-klient tas bort genom nx_lwm2m_client_delete alla sessioner som är kopplade till klienten tas också bort.

### <a name="parameters"></a>Parametrar

- **session_ptr:** Pekare till LWM2M-klientsessionskontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Avsluta en session med en LWM2M-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten utför en "Avregistrera"-åtgärd till en LWM2M-server.

### <a name="parameters"></a>Parametrar

- **session_ptr:** Pekare till LWM2M-klientsessionskontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_NOT_REGISTERED:** Klienten är inte registrerad på servern.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Hämta det sista felet för en session

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten returnerar felkoden för sessionen när sessionen är i ett feltillstånd.

### <a name="parameters"></a>Parametrar

- **session_ptr:** Pekare till kontrollblocket för LWM2M-klientsession.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Sessionen är inte i feltillstånd.
- **NX_LWM2M_ADDRESS_ERROR:** Ogiltig serveradress.
- **NX_LWM2M_BUFFER_TOO_SMALL:** Nyttolasten för begäran får inte plats i nätverksbufferten.
- **NX_LWM2M_DTLS_ERROR:** Det gick inte att upprätta en säker anslutning till servern.
- **NX_LWM2M_ERROR:** Ospecificerat fel.
- **NX_LWM2M_FORBIDDEN:** Registreringen nekas av servern.
- **NX_LWM2M_NOT_FOUND:** Klienten hittades inte av servern vid uppdatering/avregistrering.
- **NX_LWM2M_SERVER_INSTANCE_DELETED:** Serverobjektinstansen som motsvarar sessionen har tagits bort.
- **NX_LWM2M_TIMED_OUT:** Inget svar från servern.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Starta en session med en LWM2M-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Description

Den här tjänsten utför en registeråtgärd till en LWM2M-server. Servern måste ha en motsvarande serverinstans i serverobjektet.

Om registreringen lyckas bearbetar LWM2M-klienten ytterligare åtgärder från servern och skickar regelbundet "Uppdatera"-meddelanden tills klienten avregistreras.

Alla aktiva sessioner avbryts av det här anropet och ersätts av den nya LWM2M-serversessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr:** Pekare till kontrollblocket för LWM2M-klientsession.
- **server_id:** Kort server-ID för LWM2M-servern.
- **ip_address:** SERVERNS IP-adress.
- **port:** Serverns UDP-port.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades..
- **NX_LWM2M_NOT_FOUND:** Det finns ingen serverobjektinstans som motsvarar kort server-ID.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Starta en säker session med en LWM2M-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Description

Den här tjänsten utför en registeråtgärd till en LWM2M-server med hjälp av en säker DTLS-anslutning. Servern måste ha en motsvarande serverinstans i serverobjektet.

DTLS-sessionen måste ha konfigurerats med rätt chiffersviter och nyckelmaterial innan den här funktionen anropas. NX_SECURE_ENABLE_DTLS måste definieras.

Varje DTLS-session använder sin egen UDP-socket för kommunikation, så den lokala dtls_local_port måste vara olika för varje session om programmet skapar flera säkra sessioner.

Om registreringen lyckas bearbetar LWM2M-klienten ytterligare åtgärder från servern och skickar regelbundet "Uppdatera"-meddelanden tills klienten avregistreras.

Alla aktiva sessioner avbryts av det här anropet och ersätts av den nya LWM2M-serversessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr:** Pekare till kontrollblocket för LWM2M-klientsession.
- **server_id:** Kort server-ID för LWM2M-servern.
- **ip_address:** SERVERNS IP-adress.
- **port:** Serverns UDP-port.
- **dtls_session_ptr:** DTLS-sessionen som ska användas för LWM2M-sessionen.
- **dtls_local_port:** Den lokala UDP-porten som används för DTLS-sessionen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_NOT_FOUND:** Det finns ingen serverobjektinstans som motsvarar kort server-ID.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Uppdatera en session med en LWM2M-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten utför en uppdateringsåtgärd till en LWM2M-server.

### <a name="parameters"></a>Parametrar

- **session_ptr:** Pekare till kontrollblocket för LWM2M-klientsession.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_NOT_REGISTERED:** Klienten är inte registrerad på servern.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Låsa upp LWM2M-klient

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten låser upp LWM2M-klienten via ett anrop till nx_lwm2m_client_unlock().

### <a name="parameters"></a>Parametrar

- **client_ptr:** Pekare till LWM2M-klientkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_firmware_create"></a>nx_lwm2m_firmware_create

Skapa objekt för uppdatering av inbyggd programvara

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a>Description

Den här tjänsten initierar ett objekt för uppdatering av inbyggd programvara och lägger till objektet till en tidigare skapad LWM2M-klient. Objektet för uppdatering av inbyggd programvara implementerar resurser för kommunikation med en LWM2M-server, men programmet måste ge återanrop för att implementera de faktiska åtgärderna på den inbyggda programvaran (dowloading, lagring och uppdatering av den inbyggda programvaran).

Protokollparametern anger vilka protokoll som stöds av programmet för att hämta den inbyggda programvaran med resursen "Package URI" (Paket-URI). Följande flaggor har definierats:

NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.

### <a name="parameters"></a>Parametrar

- **firmware_ptr: Pekare** till kontrollblocket för objekt för inbyggd programvara.
- **client_ptr:** Pekare till en LWM2M-klient som skapats i förväg.
- **protokoll:** Flaggor som anger vilka protokoll som stöds av Package URI-resursen.
- **package_callback:** Måste vara NULL [TBD].
- **package_uri_callback:** Motringning som används för att implementera paket-URI-resursen.
- **update_callback:** Motringning som används för att implementera uppdateringsresursen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_firmware_package_info_set"></a>nx_lwm2m_firmware_package_info_set

Ange information om uppdateringspaket för inbyggd programvara

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a>Description

Den här tjänsten ändrar värdena för resurserna "PkgName" (6) och "PkgVersion" (7) för objektet för uppdatering av inbyggd programvara.

### <a name="parameters"></a>Parametrar

- **firmware_ptr:** Pekare till objektet för uppdatering av inbyggd programvara.
- **name**: Det nya värdet för Paketnamn.
- **version**: Det nya värdet för paketversionen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_firmware_result_set"></a>nx_lwm2m_firmware_result_set

Ange resultat för uppdatering av inbyggd programvara

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a>Description

Den här tjänsten ändrar värdet för resursen "Uppdatera resultat" (5) för objektet för uppdatering av inbyggd programvara.

### <a name="parameters"></a>Parametrar

- **firmware_ptr:** Pekare till objektet för uppdatering av inbyggd programvara.
- **result**: Det nya värdet för resursen Uppdatera resultat.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_firmware_state_set"></a>nx_lwm2m_firmware_state_set

Ange uppdateringstillstånd för inbyggd programvara

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a>Description

Den här tjänsten ändrar värdet för resursen State (3) för objektet för uppdatering av inbyggd programvara.

### <a name="parameters"></a>Parametrar

- **firmware_ptr:** Pekare till objektet för uppdatering av inbyggd programvara.
- **state**: Det nya värdet för tillståndsresursen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_object_resource_changed"></a>nx_lwm2m_object_resource_changed

Signaländring av ett resursvärde för en objektinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Description

Den här tjänsten används av en objektimplementering för att signalera till LWM2M-klienten att ett av dess resursvärde har ändrats. LWM2M-klienten skickar ett meddelande om resursen observeras av en LWM2M-server.

### <a name="parameters"></a>Parametrar

- **object_ptr:** Pekare till objektimplementering.
- **instance_ptr:** Pekare till objektinstansen.
- **resource**: Pekare till den struktur som beskriver den resurs som har ändrats.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- NX_PTR_ERROR: Ogiltig pekare.

## <a name="nx_lwm2m_resource_get_boolean"></a>nx_lwm2m_resource_get_boolean

Hämta värdet för en boolesk resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en boolesk resurs.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivning av resursvärde.
- **bool_ptr:** Pekare till det booleska målvärdet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING:** Resursvärdet är inte ett booleskt värde.

## <a name="nx_lwm2m_resource_get_float32"></a>nx_lwm2m_resource_get_float32

Hämta värdet för en 32-bitars flyttalsresurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en 32-bitars flyttalsresurs.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivning av resursvärde.
- **float32_ptr:** Pekare till målets 32-bitars flyttal.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING:** Resursvärdet är inte ett flyttalsvärde.

## <a name="nx_lwm2m_resource_get_float64"></a>nx_lwm2m_resource_get_float64

Hämta värdet för en 64-bitars flyttalsresurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en 64-bitars flyttalsresurs.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivning av resursvärde.
- **float64_ptr:** Pekare till målets 64-bitars flyttal.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING:** Resursvärdet är inte ett flyttalsvärde.

## <a name="nx_lwm2m_resource_get_integer32"></a>nx_lwm2m_resource_get_integer32

Hämta värdet för en 32-bitars heltalsresurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en 32-bitars heltalsresurs.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivning av resursvärde.
- **int32_ptr:** Pekare till målets 32-bitars heltalsvärde.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING:** Resursvärdet är inte ett heltalsvärde, eller så får inte heltalsvärdet plats i ett 32-bitars tal.

## <a name="nx_lwm2m_resource_get_integer64"></a>nx_lwm2m_resource_get_integer64

Hämta värdet för en 64-bitars heltalsresurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en 64-bitars heltalsresurs.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivning av resursvärde.
- **int64_ptr:** Pekare till målets 64-bitars heltalsvärde.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING:** Resursvärdet är inte ett heltalsvärde.

## <a name="nx_lwm2m_resource_get_objlnk"></a>nx_lwm2m_resource_get_objlnk

Hämta värdet för en objektlänkresurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en objektlänkresurs.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivning av resursvärde.
- **objlnk_ptr:** Pekare till målvärdet för Object Link.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING:** Resursvärdet är inte ett objektlänkvärde.

## <a name="nx_lwm2m_resource_get_opaque"></a>nx_lwm2m_resource_get_opaque

Hämta värdet för en Täckande resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en Täckande resurs.

Ett täckande resursvärde består av en pekare till en buffert och en längd.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivning av resursvärde.
- **opaque_ptr_ptr:** Pekare till den täckande målbufferten.
- **opaque_length_ptr:** Pekare till den täckande målbuffertlängden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING:** Resursvärdet är inte ett täckande värde.

## <a name="nx_lwm2m_resource_get_string"></a>nx_lwm2m_resource_get_string

Hämta värdet för en strängresurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en strängresurs.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivning av resursvärde.
- **string_ptr_ptr: Pekare** till målsträngens pekare.
- **string_length_ptr:** Pekare till målsträngens längd. Kan vara NULL om strängen är null-avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING:** Resursvärdet är inte ett strängvärde.

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a>nx_lwm2m_resource_multiple_get_boolean

Hämta värdet för en boolesk resurs med flera resurser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en boolesk resursinstans från en flera resurser.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivningen av flera resursvärden.
- **index:** Index för den instans som ska hämtas i resursvärdematrisen.
- **instance_id_ptr:** Pekare till målinstansens ID.
- **bool_ptr:** Pekare till det booleska målvärdet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER:** Indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING:** Resursen är inte en flera resurser eller resursvärdet är inte ett booleskt värde.

## <a name="nx_lwm2m_resource_multiple_get_float32"></a>nx_lwm2m_resource_multiple_get_float32

Hämta värdet för en 32-bitars flyttal med flera resursinstanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en 32-bitars resursinstans för flyttal från en flera resurser.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivningen av flera resursvärden.
- **index:** Index för den instans som ska hämtas i resursvärdematrisen.
- **instance_id_ptr:** Pekare till målinstansens ID.
- **float32_ptr:** Pekare till målets 32-bitars flyttal.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER:** Indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING:** Resursen är inte en flera resurser, eller så är resursvärdet inte ett flyttalsvärde.

## <a name="nx_lwm2m_resource_multiple_get_float64"></a>nx_lwm2m_resource_multiple_get_float64

Hämta värdet för en 64-bitars flyttal med flera resursinstanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en 64-bitars flyttalsresursinstans från en flera resurser.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivningen av flera resursvärden.
- **index:** Index för den instans som ska hämtas i resursvärdematrisen.
- **instance_id_ptr:** Pekare till målinstansens ID.
- **float64_ptr:** Pekare till målets 64-bitars flyttal.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER:** Indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING:** Resursen är inte en flera resurser, eller så är resursvärdet inte ett flyttalsvärde.

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a>nx_lwm2m_resource_multiple_get_integer32

Hämta värdet för en 32-bitars heltal för flera resursinstanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en 32-bitars heltalsresursinstans från en flera resurser.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivningen av flera resursvärden.
- **index:** Index för den instans som ska hämtas i resursvärdematrisen.
- **instance_id_ptr:** Pekare till målinstansens ID.
- **int32_ptr:** Pekare till målets 32-bitars heltalsvärde.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER:** Indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING:** Resursen är inte en flera resurser, resursvärdet är inte ett heltalsvärde eller heltalsvärdet får inte plats i ett 32-bitars tal.

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a>nx_lwm2m_resource_multiple_get_integer64

Hämta värdet för en 64-bitars heltalsinstans med flera resurser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en 64-bitars heltalsresursinstans från en flera resurser.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivningen av flera resursvärden.
- **index:** Index för den instans som ska hämtas i resursvärdematrisen.
- **instance_id_ptr:** Pekare till målinstansens ID.
- **int64_ptr:** Pekare till målets 64-bitars heltalsvärde.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER:** Indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING:** Resursen är inte en flera resurser, eller så är resursvärdet inte ett heltalsvärde.

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a>nx_lwm2m_resource_multiple_get_objlnk

Hämta värdet för en objektlänk med flera resursinstanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en objektlänkresursinstans från en flera resurser.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivningen av flera resursvärden.
- **index:** Index för den instans som ska hämtas i resursvärdematrisen.
- **instance_id_ptr:** Pekare till målinstansens ID.
- **objlnk_ptr:** Pekare till målvärdet för Object Link.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER:** Indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING:** Resursen är inte en flera resurser eller resursvärdet är inte ett objektlänkvärde.

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a>nx_lwm2m_resource_multiple_get_opaque

Hämta värdet för en täckande flerresursinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en täckande resursinstans från en flera resurser.

Ett täckande resursvärde består av en pekare till en buffert och en längd.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivningen av flera resursvärden.
- **index:** Index för den instans som ska hämtas i resursvärdematrisen.
- **instance_id_ptr:** Pekare till målinstansens ID.
- **opaque_ptr_ptr:** Pekare till den täckande målbufferten.
- **opaque_length_ptr:** Pekare till den täckande målbuffertlängden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER:** Indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING:** Resursen är inte en flera resurser eller resursvärdet är inte ett täckande värde.

## <a name="nx_lwm2m_resource_multiple_get_string"></a>nx_lwm2m_resource_multiple_get_string

Hämta värdet för en sträng med flera resursinstanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a>Description

Tjänsten hämtar värdet för en strängresursinstans från en flera resurser.

### <a name="parameters"></a>Parametrar

- **value**: Pekare till beskrivningen av flera resursvärden.
- **index:** Index för den instans som ska hämtas i resursvärdematrisen.
- **instance_id_ptr:** Pekare till målinstansens ID.
- **string_ptr_ptr: Pekare** till målsträngens pekare.
- **string_length_ptr:** Pekare till målsträngens längd. Kan vara NULL om strängen är null-avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:** Åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER:** Indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING:** Resursen är inte en flera resurser, eller instansvärdet är inte ett strängvärde.
