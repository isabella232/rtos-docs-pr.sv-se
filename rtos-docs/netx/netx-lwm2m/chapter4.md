---
title: Kapitel 4 – Beskrivning av Azure återställnings tider NetX LWM2M Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX LWM2M-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826673"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a>Kapitel 4 – Beskrivning av Azure återställnings tider NetX LWM2M Services

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX LWM2M-tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

### <a name="lwm2m-client-management"></a>LWM2M klient hantering

- **nx_lwm2m_client_create**: *skapa lwm2m-klient*
- **nx_lwm2m_client_delete**: *ta bort lwm2m-klienten*
- **nx_lwm2m_client_lock**: *Lås lwm2m-klienten*
- **nx_lwm2m_client_object_add**: *Lägg till objekt implementering i lwm2m-klienten*
- **nx_lwm2m_client_unlock**: *Lås upp lwm2m-klienten*

### <a name="lwm2m-client-session-management"></a>LWM2M för hantering av klient

- **nx_lwm2m_client_session_bootstrap**: *starta en session med en Start Server*
- **nx_lwm2m_client_session_bootstrap_dtls**: *starta en säker session med en Start Server*
- **nx_lwm2m_client_session_create**: *skapa en lwm2m-klientsession*
- **nx_lwm2m_client_session_delete**: *ta bort lwm2m-klientsession*
- **nx_lwm2m_client_session_deregister**: *Avsluta en session med en lwm2m-Server*
- **nx_lwm2m_client_session_error_get**: *Hämta senaste fel i en session*
- **nx_lwm2m_client_session_register**: *starta en session med en lwm2m-Server*
- **nx_lwm2m_client_session_register_dtls**: *starta en säker session med en lwm2m-Server*
- **nx_lwm2m_client_session_update**: *Uppdatera en session med en lwm2m-Server*

### <a name="security-object-implementation"></a>Implementering av säkerhets objekt

- **nx_lwm2m_client_security_key_callbacks_set**: *Ange återanrop för hantering av säkerhets nycklar*

### <a name="device-object-implementation"></a>Implementering av enhets objekt

- **nx_lwm2m_client_device_callbacks_set**: *Ange återanrop i enhets objekts program*
- **nx_lwm2m_client_device_error_push**: *Lägg till felkod till enhets objekt*
- **nx_lwm2m_client_device_error_reset**: *återställa felkoder för enhets objekt*
- **nx_lwm2m_client_device_resource_changed**: *signal ändring av enhets objekt resurs*

### <a name="custom-objects-implementation"></a>Implementering av anpassade objekt

- **nx_lwm2m_object_resource_changed**: *signal ändring av ett resurs värde för en objekt instans*

### <a name="local-device-management"></a>Hantering av lokala enheter

- **nx_lwm2m_client_object_create**: *skapa en ny objekt instans*
- **nx_lwm2m_client_object_delete**: *ta bort en objekt instans*
- **nx_lwm2m_client_object_discover**: *identifiera resurser för en objekt instans*
- **nx_lwm2m_client_object_execute**: *Kör resurs för en objekt instans*
- **nx_lwm2m_client_object_get_next**: *Hämta listan över objekt som IMPLEMENTERAs av lwm2m-klienten*
- **nx_lwm2m_client_object_instance_get_next**: *Hämta listan över instanser av ett objekt*
- **nx_lwm2m_client_object_read**: *läsa resurs värden för en objekt instans*
- **nx_lwm2m_client_object_write**: *Ändra resurs värden för en objekt instans*

### <a name="resources-values-decoding"></a>Resurs värden avkodning

- **nx_lwm2m_resource_get_boolean**: *Hämta värdet för en boolesk resurs*
- **nx_lwm2m_resource_get_float32**: *Hämta värdet för en 32-bitars svävande punkt resurs*
- **nx_lwm2m_resource_get_float64**: *Hämta värdet för en 64-bitars svävande punkt resurs*
- **nx_lwm2m_resource_get_integer32**: *Hämta värdet för en 32-bitars heltals resurs*
- **nx_lwm2m_resource_get_integer64**: *Hämta värdet för en 64-bitars heltals resurs*
- **nx_lwm2m_resource_get_objlnk**: *Hämta värdet för en objekt länk resurs*
- **nx_lwm2m_resource_get_opaque**: *Hämta värdet för en ogenomskinlig resurs*
- **nx_lwm2m_resource_get_string**: *Hämta värdet för en sträng resurs*
- **nx_lwm2m_resource_multiple_get_boolean**: *Hämta värdet för en boolesk resurs flera resurs instanser*
- **nx_lwm2m_resource_multiple_get_float32**: *Hämta värdet för en 32-bitars flytt ALS plats med flera resurs instanser*
- **nx_lwm2m_resource_multiple_get_float64**: *Hämta värdet för en 64-bitars flytt ALS plats med flera resurs instanser*
- **nx_lwm2m_resource_multiple_get_integer32**: *Hämta värdet för ett 32-bitars heltal med flera resurs instanser*
- **nx_lwm2m_resource_multiple_get_integer64**: *Hämta värdet för ett 64-bitars heltal med flera resurs instanser*
- **nx_lwm2m_resource_multiple_get_objlnk**: *Hämta värdet för en objekt länk flera resurs instanser*
- **nx_lwm2m_resource_multiple_get_opaque**: *Hämta värdet för en täckande flera resurs instanser*
- **nx_lwm2m_resource_multiple_get_string**: *Hämta värdet för en sträng flera resurs instanser*

### <a name="firmware-update-object"></a>Uppdaterings objekt för inbyggd program vara

- **nx_lwm2m_firmware_create**: *skapa uppdaterings objekt för inbyggd program vara*
- **nx_lwm2m_firmware_package_info_set**: *Ange information om uppdaterings paket för inbyggd program vara*
- **nx_lwm2m_firmware_result_set**: *Ange uppdaterings resultat för inbyggd program vara*
- **nx_lwm2m_firmware_state_set**: *Ange uppdaterings tillstånd för inbyggd program vara*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Skapa LWM2M-klient

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en LWM2M-klient instans som körs i kontexten för en egen ThreadX-tråd.

LWM2M-klienten implementerar följande OMA LWM2M-objekt: Security (0), Server (1), Access Control (2) och enhet (3). Implementeringar av andra objekt måste läggas till av programmet.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **ip_ptr**: pekare till den tidigare skapade IP-instansen.
- **packet_pool_ptr**: pekar mot standardpoolen för den här LWM2M-klienten.
- **local_port**: den lokala UDP-port som används för osäker kommunikation.
- **name_ptr**: pekare till LWM2M-klientens slut punkts namn.
- **msisdn_ptr**: pekar på MSISDN där LWM2M-klienten kan nås för användning med SMS-bindningen, kan vara null om SMS-bindning inte stöds.
- **binding_modes**: bindningen och lägena som stöds av LWM2M-klienten måste vara en kombination av flaggor för NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S och NX_LWM2M_BINDING_SQ.
- **stack_ptr**: pekar på LWM2M för klient tråds tack.
- **stack_size**: LWM2M-klientens tråd storlek.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: LWM2M-klienten har skapats.
- **NX_LWM2M_ERROR**: LWM2M-klienten skapar fel.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

Ta bort LWM2M-klient

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad LWM2M-klient instans.

Alla sessioner som är anslutna till klienten tas också bort av det här anropet.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: LWM2M-klienten har tagits bort.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_device_callbacks_set"></a>nx_lwm2m_client_device_callbacks_set

Ange återanrop i enhets objekts program

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a>Beskrivning

Den här tjänsten installerar program återanrop för att implementera åtgärder på LWM2M enhets objekt resurser som inte hanteras av LWM2M-klienten.

LWM2M-klienten implementerar följande resurser: felkod (11), Reset-felkod (12) och bindning och lägen som stöds (16). åtgärder för de andra resurserna omdirigeras till programmet.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **read_callback**: metoden Read är Read.
- **discover_callback**: återanropet "Discover"-metoden.
- **write_callback**: metoden Write.
- **execute_callback**: "EXECUTE"-metod återanropet.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push

Lägg till felkod till enhets objekt

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en ny instans i fel kods resursen (11) för objekt enheten.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **kod**: den nya felkoden.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BUFFER_TOO_SMALL**: det maximala antalet lagrade fel koder har nåtts.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Återställa felkoder för enhets objekt

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort alla fel kods resurs instanser från objektet enhet. Det motsvarar att köra fel koden för resurs återställning (12).

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Signal ändring för enhets objekt resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Beskrivning

Tjänsten används av programmet för att signalera till LWM2M-klienten att en resurs av objekt enheten har ändrats. LWM2M-klienten skickar ett meddelande om resursen observeras av en LWM2M-Server.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **resurs**: pekar till strukturen som beskriver den resurs som har ändrats.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Lås LWM2M-klient

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten låser LWM2M-klienten för att förhindra concurent-åtkomst till LWM2M-objekt från servrar eller någon annan program tråd.

Om LWM2M-klienten är låst av en annan tråd, kommer funktionen att blockeras tills LWM2M-klienten har låsts upp.

Anrop till nx_lwm2m_client_lock ()/nx_lwm2m_client_unlock ()-par kan kapslas.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Lägga till objekt implementering i LWM2M-klienten

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en ny objekt implementering i LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **object_ptr**: pekar mot strukturen som definierar objekt implementeringen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_ALREADY_EXIST**: objekt-ID: t finns redan.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Skapa en ny objekt instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en "skapa"-åtgärd på ett objekt av LWM2M-klienten för att skapa en ny objekt instans.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **object_id**: objekt-ID.
- **instance_id_ptr**: pekaren till ID: t för den nya instansen kan vara null om LWM2M-klienten måste tilldela ett instans-ID. Om ID: t är det reserverade värdet 65535, tilldelar LWM2M-klienten ett instans-ID. Om det tilldelade ID: t inte är NULL returneras det efter anropet.
- **num_values**: antalet värden som ska anges.
- **values_ptr**: pekar mot en matris med resurs värden för att initiera den nya objekt instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_ALREADY_EXIST**: ID: t för objekt instansen finns redan.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: objektet har inte stöd för att skapa en instans.
- **NX_LWM2M_NO_MEMORY**: det går inte att allokera minne för att lagra den nya instansen.
- **NX_LWM2M_NOT_FOUND**: objekt-ID: t finns inte.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Ta bort en objekt instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en borttagnings åtgärd på en objekt instans av LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **object_id**: objekt-ID.
- **instance_id**: ID för objekt instans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: objektet har inte stöd för borttagning av instans.
- **NX_LWM2M_NOT_FOUND**: ID för objekt-ID eller objekt instans saknas.
- NX_PTR_ERROR ogiltig pekare.

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

Identifiera resurser för en objekt instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en "Discover"-åtgärd på en objekt instans av LWM2M-klienten, vilket returnerar listan över resurser som implementeras av objektet.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **object_id**: objekt-ID.
- **instance_id**: ID för objekt instans.
- **num_resources_ptr**: om du vill ange storleken på måldomänkontrollanten vid utdata anger du antalet element som skrivs till bufferten.
- **resources_ptr**: pekar mot målcachen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades..
- **NX_LWM2M_BUFFER_TOO_SMALL**: bufferten är för liten för att lagra listan över resurser.
- **NX_LWM2M_NOT_FOUND**: ID för objekt-ID eller objekt instans saknas.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

Kör resurs för en objekt instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför åtgärden kör på en objekt instans resurs för LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **object_id**: objekt-ID.
- **instance_id**: ID för objekt instans.
- **resource_id**: resurs-ID.
- **arguments_ptr**: pekar mot argumenten för körnings åtgärden. Kan vara NULL om arguments_length är noll.
- **arguments_length**: argumentens längd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: resursen har inte stöd för körnings åtgärden.
- **NX_LWM2M_NOT_FOUND**: objekt-ID, objekt instans-ID eller resurs-ID finns inte.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_object_get_next"></a>nx_lwm2m_client_object_get_next

Hämta listan över objekt som implementeras av LWM2M-klienten

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar ID: t för nästa objekt som implementeras av LWM2M-klienten. Om aktuellt objekt-ID är inställt på NX_LWM2M_RESERVED_ID (65535) returneras det första objekt-ID: t.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **object_id_ptr**: pekar mot aktuellt objekt-ID. Vid retur innehåller nästa objekt-ID som implementeras av LWM2M-klienten.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades..
- **NX_LWM2M_NOT_FOUND**: angivet objekt-ID är det sista i databasen.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_object_instance_get_next"></a>nx_lwm2m_client_object_instance_get_next

Hämta listan över instanser av ett objekt

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar ID: t för nästa objekt instans av det aktuella objektet. Om det aktuella instans-ID: t är inställt på NX_LWM2M_RESERVED_ID (65535) returneras ID: t för den första instansen.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **object_id**: objekt-ID.
- **instance_id_ptr**: pekar mot aktuellt objekt instans-ID. Vid retur innehåller nästa instans-ID för objektet.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades..
- **NX_LWM2M_NOT_FOUND**: det aktuella instans-ID: t är det sista objektet eller objekt-ID: t är inte implementerat.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Läsa resurs värden för en objekt instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en Läs åtgärd på en objekt instans av LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **object_id**: objekt-ID.
- **instance_id**: ID för objekt instans.
- **num_values**: antalet resurser som ska läsas.
- **values_ptr**: pekar mot en matris med NX_LWM2M_RESOURCE som innehåller ID: n för de resurser som ska läsas. Vid retur fylls matrisen med motsvarande typer och värden.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: en resurs har inte stöd för Läs åtgärden.
- **NX_LWM2M_NOT_FOUND**: objekt-ID, objekt instans-ID eller resurs-ID finns inte.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Ändra resurs värden för en objekt instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en Skriv åtgärd på en objekt instans av LWM2M-klienten.

Följande Skriv åtgärder kan anges för parametern *write_op* :

- **0** &mdash; del uppdatering: lägger till eller uppdaterar resurser som finns i det nya värdet och låter andra befintliga resurser ändras,

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Ersätt instans: ersätter objekt instansen med de nya angivna resurs värdena.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Ersätt resurs: ersätter resurserna med de nya angivna resurs värdena (används för att ersätta flera resurser).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap-skrivning: indikerar ett anrop från en bootstrap-sekvens.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **object_id**: objekt-ID.
- **instance_id**: ID för objekt instans.
- **num_values**: antalet resurser som ska skrivas.
- **values_ptr**: pekar mot en matris med NX_LWM2M_RESOURCE som innehåller ID: n för resurserna, typerna och värdena som ska skrivas.
- **write_op**: typ av Skriv åtgärd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING**: resurs typen är inte giltig.
- **NX_LWM2M_BUFFER_TOO_SMALL**: längden på ett värde är för stor för att lagras i instansen.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: en resurs har inte stöd för Skriv åtgärden.
- **NX_LWM2M_NO_MEMORY**: det går inte att allokera minne för att lagra ett resurs värde.
- **NX_LWM2M_NOT_ACCEPTABLE**: värdet för en resurs är ogiltigt.
- **NX_LWM2M_NOT_FOUND**: objekt-ID, objekt instans-ID eller resurs-ID finns inte.
- NX_OPTION_ERROR: ogiltig typ av Skriv åtgärd.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a>nx_lwm2m_client_security_key_callbacks_set

Ange återanrop för hantering av säkerhets objekt

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a>Beskrivning

Den här tjänsten installerar återanrop för program för att implementera åtgärder på LWM2M säkerhets objekt resurser som är relaterade till säkerhets nycklarna.

LWM2M-klienten delegerar hantering av säkerhets nycklar till programmet under bootstrap-sessionerna, och återanropen anropas när bootstrap-servern skriver eller tar bort följande resurser på en säkerhets objekts instans: offentlig nyckel eller identitet (3), serverns offentliga nyckel (4), hemlig nyckel (5).

Programmet ansvarar för att lagra nycklarnas data och för att konfigurera de DTLS-sessioner som används av LWM2M-klienten.

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.
- **write_callback**: det går inte att anropa Key-metoden Write.
- **delete_callback**: den "ta bort" nyckel metoden motringning.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Starta en-session med en Start Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en session med en Start Server. Servern måste ha en motsvarande säkerhets instans i objektet Security.

Om resursen "vänta bort" skiljer sig från noll i säkerhets instansen som är kopplad till den här servern väntar sessionen på en initierad start av servern, om ingen start initieras av servern efter den här tids perioden som en klient initierade boostrap kommer att utföras.

Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya bootstrap-serversessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr**: pekare till LWM2M för klientens session.
- **security_id**: Start serverns säkerhets instans-ID måste vara inställt på NX_LWM2M_RESERVED_ID (65535) om ingen säkerhets instans har definierats för bootstrap-servern.
- **ip_address**: SERVERns IP-adress.
- **port**: SERVERns UDP-port.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_NOT_FOUND**: det finns ingen säkerhets objekt instans som motsvarar säkerhets instansens ID.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Starta en säker session med en Start Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en session med en Start Server med en säker DTLS-anslutning. Servern måste ha en motsvarande säkerhets instans i objektet Security.

DTLS-sessionen måste ha kon figurer ATS med lämpliga chiffersviter och nyckel material innan du anropar den här funktionen. NX_SECURE_ENABLE_DTLS måste definieras.

Om resursen "vänta bort" skiljer sig från noll i säkerhets instansen som är kopplad till den här servern väntar sessionen på en initierad start av servern, om ingen start initieras av servern efter den här tids perioden som en klient initierade boostrap kommer att utföras.

Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya bootstrap-serversessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr**: pekare till LWM2M för klientens session.
- **security_id**: Start serverns säkerhets instans-ID måste vara inställt på NX_LWM2M_RESERVED_ID (65535) om ingen säkerhets instans har definierats för bootstrap-servern.
- **ip_address**: SERVERns IP-adress.
- **port**: SERVERns UDP-port.
- **dtls_session_ptr**: DTLS-sessionen som ska användas för bootstrap-sessionen.
- **dtls_local_port**: den lokala UDP-port som används för DTLS-sessionen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_NOT_FOUND**: det finns ingen säkerhets objekt instans som motsvarar säkerhets instansens ID.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Skapa LWM2M-klientsession

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en ny LWM2M-klientsession som är ansluten till en befintlig LWM2M-klient. Sessionen används av LWM2M-klienten för att kommunicera med en Start Server eller en LWM2M-Server.

Programmet måste tillhandahålla en callback-funktion som anropas när sessionens tillstånd uppdateras.

### <a name="parameters"></a>Parametrar

- **session_ptr**: pekare till LWM2M för klientens session.
- **client_ptr**: pekar mot den tidigare skapade LWM2M-klienten.
- **state_callback**: motringning till program som anropas när sessionens tillstånd har ändrats.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Ta bort LWM2M-klientsession

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en LWM2M-klientsession.

När en LWM2M-klient tas bort genom att anropa nx_lwm2m_client_delete alla sessioner som är anslutna till klienten också bort.

### <a name="parameters"></a>Parametrar

- **session_ptr**: pekare till LWM2M för klientens session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Avsluta en session med en LWM2M-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en "avregistrera"-åtgärd på en LWM2M-Server.

### <a name="parameters"></a>Parametrar

- **session_ptr**: pekare till LWM2M för klientens session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_NOT_REGISTERED**: klienten är inte registrerad på servern.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Hämta senaste fel i en session

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar felkoden för sessionen när sessionen är i ett fel tillstånd.

### <a name="parameters"></a>Parametrar

- **session_ptr**: pekare till LWM2M för klientens session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: sessionen har fel tillstånd.
- **NX_LWM2M_ADDRESS_ERROR**: ogiltig server adress.
- **NX_LWM2M_BUFFER_TOO_SMALL**: nytto lasten för begäran får inte plats i nätverksmappen.
- **NX_LWM2M_DTLS_ERROR**: det gick inte att upprätta en säker anslutning till servern.
- **NX_LWM2M_ERROR**: okänt fel.
- **NX_LWM2M_FORBIDDEN**: registreringen nekades av servern.
- **NX_LWM2M_NOT_FOUND**: klienten hittades inte av servern vid uppdatering/avregistrering.
- **NX_LWM2M_SERVER_INSTANCE_DELETED**: den server objekt instans som motsvarar sessionen har tagits bort.
- **NX_LWM2M_TIMED_OUT**: inget svar från servern.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Starta en-session med en LWM2M-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en "Registrera"-åtgärd på en LWM2M-Server. Servern måste ha en motsvarande Server instans i objektet Server.

Om registreringen lyckas kommer LWM2M-klienten att bearbeta ytterligare åtgärder från servern och skickar regelbundet meddelanden om uppdatering tills klienten avregistreras.

Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya LWM2M.

### <a name="parameters"></a>Parametrar

- **session_ptr**: pekare till LWM2M för klientens session.
- **server_id**: LWM2M-serverns korta Server-ID.
- **ip_address**: SERVERns IP-adress.
- **port**: SERVERns UDP-port.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades..
- **NX_LWM2M_NOT_FOUND**: det finns ingen Server objekt instans som motsvarar det korta Server-ID: t.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Starta en säker session med en LWM2M-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en "Registrera"-åtgärd på en LWM2M-server med en säker DTLS-anslutning. Servern måste ha en motsvarande Server instans i objektet Server.

DTLS-sessionen måste ha kon figurer ATS med lämpliga chiffersviter och nyckel material innan du anropar den här funktionen. NX_SECURE_ENABLE_DTLS måste definieras.

Varje DTLS-session använder sin egen UDP-socket för kommunikation, så den lokala port dtls_local_port måste vara olika för varje session om programmet skapar flera säkra sessioner.

Om registreringen lyckas kommer LWM2M-klienten att bearbeta ytterligare åtgärder från servern och skickar regelbundet meddelanden om uppdatering tills klienten avregistreras.

Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya LWM2M.

### <a name="parameters"></a>Parametrar

- **session_ptr**: pekare till LWM2M för klientens session.
- **server_id**: LWM2M-serverns korta Server-ID.
- **ip_address**: SERVERns IP-adress.
- **port**: SERVERns UDP-port.
- **dtls_session_ptr**: DTLS-sessionen som ska användas för LWM2M-sessionen.
- **dtls_local_port**: den lokala UDP-port som används för DTLS-sessionen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_NOT_FOUND**: det finns ingen Server objekt instans som motsvarar det korta Server-ID: t.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Uppdatera en session med en LWM2M-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en uppdaterings åtgärd på en LWM2M-Server.

### <a name="parameters"></a>Parametrar

- **session_ptr**: pekare till LWM2M för klientens session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_NOT_REGISTERED**: klienten är inte registrerad på servern.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Lås upp LWM2M-klienten

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten låser upp LWM2M-previoulsy som låsts av ett anrop till nx_lwm2m_client_unlock ().

### <a name="parameters"></a>Parametrar

- **client_ptr**: pekar mot LWM2M klient kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_firmware_create"></a>nx_lwm2m_firmware_create

Skapa uppdaterings objekt för inbyggd program vara

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar ett uppdaterings objekt för inbyggd program vara och lägger till objektet i en tidigare skapad LWM2M-klient. Objektet uppdatering av inbyggd program vara implementerar resurserna för kommunikation med en LWM2M-Server, men programmet måste tillhandahålla återanrop för att implementera de faktiska åtgärderna i den inbyggda program varan (dowloading, lagring och uppdatering av den inbyggda program varan).

Parametern Protocols anger vilka protokoll som stöds av programmet för att hämta den inbyggda program varan med "Package URI"-resursen, följande flaggor definieras:

NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.

### <a name="parameters"></a>Parametrar

- **firmware_ptr**: pekar mot objekt kontroll blocket för inbyggd program vara.
- **client_ptr**: pekare till PREVISOUSLY skapade LWM2M-klienten.
- **protokoll**: flaggor som anger vilka protokoll som stöds av PAKETets URI-resurs.
- **package_callback**: måste vara null [TBD].
- **package_uri_callback**: motringning används för att implementera PAKETets URI-resurs.
- **update_callback**: motringning används för att implementera uppdaterings resursen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_firmware_package_info_set"></a>nx_lwm2m_firmware_package_info_set

Ange information om uppdaterings paket för inbyggd program vara

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ändrar värdena för "PkgName" (6) och "PkgVersion" (7) resurser i uppdaterings objekt för inbyggd program vara.

### <a name="parameters"></a>Parametrar

- **firmware_ptr**: pekar mot uppdaterings objekt för inbyggd program vara.
- **namn**: det nya värdet för paket namnet.
- **version**: det nya värdet för paket versionen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_firmware_result_set"></a>nx_lwm2m_firmware_result_set

Ange uppdaterings resultat för inbyggd program vara

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ändrar värdet för resursen uppdaterings resultat (5) för objektet för den inbyggda program varan.

### <a name="parameters"></a>Parametrar

- **firmware_ptr**: pekar mot uppdaterings objekt för inbyggd program vara.
- **resultat**: det nya värdet för resursen uppdaterings resultat.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_firmware_state_set"></a>nx_lwm2m_firmware_state_set

Ange uppdaterings tillstånd för inbyggd program vara

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ändrar värdet för "State"-resursen (3) för objektet med uppdatering av inbyggd program vara.

### <a name="parameters"></a>Parametrar

- **firmware_ptr**: pekar mot uppdaterings objekt för inbyggd program vara.
- **status**: det nya värdet för tillstånds resursen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_object_resource_changed"></a>nx_lwm2m_object_resource_changed

Signal ändring för ett resurs värde för en objekt instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Beskrivning

Den här tjänsten används av en objekt implementering för att signalera LWM2M-klienten om att ett av resursens värde har ändrats. LWM2M-klienten skickar ett meddelande om resursen observeras av en LWM2M-Server.

### <a name="parameters"></a>Parametrar

- **object_ptr**: pekar mot objekt implementeringen.
- **instance_ptr**: pekar mot objekt instansen.
- **resurs**: pekar till strukturen som beskriver den resurs som har ändrats.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- NX_PTR_ERROR: ogiltig pekare.

## <a name="nx_lwm2m_resource_get_boolean"></a>nx_lwm2m_resource_get_boolean

Hämta värdet för en boolesk resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en boolesk resurs.

### <a name="parameters"></a>Parametrar

- **värde**: pekare till resurs värde beskrivning.
- **bool_ptr**: pekar mot målets booleska värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett booleskt värde.

## <a name="nx_lwm2m_resource_get_float32"></a>nx_lwm2m_resource_get_float32

Hämta värdet för en 32-bitars svävande punkt resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en 32-bitars svävande punkt resurs.

### <a name="parameters"></a>Parametrar

- **värde**: pekare till resurs värde beskrivning.
- **float32_ptr**: pekar på målets 32-bitars flytt ALS värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett flytt ALS värde.

## <a name="nx_lwm2m_resource_get_float64"></a>nx_lwm2m_resource_get_float64

Hämta värdet för en 64-bitars svävande punkt resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en 64-bitars svävande punkt resurs.

### <a name="parameters"></a>Parametrar

- **värde**: pekare till resurs värde beskrivning.
- **float64_ptr**: pekar på målets 64-bitars flytt ALS värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett flytt ALS värde.

## <a name="nx_lwm2m_resource_get_integer32"></a>nx_lwm2m_resource_get_integer32

Hämta värdet för en 32-bitars heltals resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en 32-bitars heltals resurs.

### <a name="parameters"></a>Parametrar

- **värde**: pekare till resurs värde beskrivning.
- **int32_ptr**: pekar mot målet 32-bitars heltals värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett heltals värde, eller så ryms inte heltalet i ett 32-bitars tal.

## <a name="nx_lwm2m_resource_get_integer64"></a>nx_lwm2m_resource_get_integer64

Hämta värdet för en 64-bitars heltals resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en 64-bitars heltals resurs.

### <a name="parameters"></a>Parametrar

- **värde**: pekare till resurs värde beskrivning.
- **int64_ptr**: pekar mot målet 64-bitars heltals värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett heltals värde.

## <a name="nx_lwm2m_resource_get_objlnk"></a>nx_lwm2m_resource_get_objlnk

Hämta värdet för en objekt länk resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en objekt länk resurs.

### <a name="parameters"></a>Parametrar

- **värde**: pekare till resurs värde beskrivning.
- **objlnk_ptr**: pekar mot länk värde för mål objekt.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett objekt länk värde.

## <a name="nx_lwm2m_resource_get_opaque"></a>nx_lwm2m_resource_get_opaque

Hämta värdet för en ogenomskinlig resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en ogenomskinlig resurs.

Ett ogenomskinligt resurs värde består av en pekare till en buffert och en längd.

### <a name="parameters"></a>Parametrar

- **värde**: pekare till resurs värde beskrivning.
- **opaque_ptr_ptr**: pekar mot målets täckande buffer-pekare.
- **opaque_length_ptr**: pekar mot målets täckande buffertlängd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett ogenomskinligt värde.

## <a name="nx_lwm2m_resource_get_string"></a>nx_lwm2m_resource_get_string

Hämta värdet för en sträng resurs

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en sträng resurs.

### <a name="parameters"></a>Parametrar

- **värde**: pekare till resurs värde beskrivning.
- **string_ptr_ptr**: pekar mot mål sträng pekaren.
- **string_length_ptr**: pekar mot mål strängens längd. Kan vara NULL om strängen är null-terminerad.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett sträng värde.

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a>nx_lwm2m_resource_multiple_get_boolean

Hämta värdet för en boolesk resurs flera resurs instanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en boolesk resurs instans från flera resurser.

### <a name="parameters"></a>Parametrar

- **värde**: pekar mot värde beskrivning för flera resurser.
- **index**: index för den instans som ska hämtas i resurs värdes mat ris.
- **instance_id_ptr**: pekar mot mål instansens ID.
- **bool_ptr**: pekar mot målets booleska värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är resursens värde inte ett booleskt värde.

## <a name="nx_lwm2m_resource_multiple_get_float32"></a>nx_lwm2m_resource_multiple_get_float32

Hämta värdet för en 32-bitars flytt ALS plats med flera resurs instanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en 32-bitars flytt ALS resurs instans från flera resurser.

### <a name="parameters"></a>Parametrar

- **värde**: pekar mot värde beskrivning för flera resurser.
- **index**: index för den instans som ska hämtas i resurs värdes mat ris.
- **instance_id_ptr**: pekar mot mål instansens ID.
- **float32_ptr**: pekar på målets 32-bitars flytt ALS värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är resursens värde inte ett flytt ALS värde.

## <a name="nx_lwm2m_resource_multiple_get_float64"></a>nx_lwm2m_resource_multiple_get_float64

Hämta värdet för en 64-bitars flytt ALS plats med flera resurs instanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en 64-bitars flytt ALS resurs instans från flera resurser.

### <a name="parameters"></a>Parametrar

- **värde**: pekar mot värde beskrivning för flera resurser.
- **index**: index för den instans som ska hämtas i resurs värdes mat ris.
- **instance_id_ptr**: pekar mot mål instansens ID.
- **float64_ptr**: pekar på målets 64-bitars flytt ALS värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är resursens värde inte ett flytt ALS värde.

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a>nx_lwm2m_resource_multiple_get_integer32

Hämta värdet för ett 32-bitars heltal flera resurs instanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en 32-bitars heltals resurs instans från en flera resurser.

### <a name="parameters"></a>Parametrar

- **värde**: pekar mot värde beskrivning för flera resurser.
- **index**: index för den instans som ska hämtas i resurs värdes mat ris.
- **instance_id_ptr**: pekar mot mål instansens ID.
- **int32_ptr**: pekar mot målet 32-bitars heltals värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs eller också är resursens värde inte ett heltals värde, eller så ryms inte heltalet i ett 32-bitars tal.

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a>nx_lwm2m_resource_multiple_get_integer64

Hämta värdet för ett 64-bitars heltal flera resurs instanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en 64-bitars heltals resurs instans från en flera resurser.

### <a name="parameters"></a>Parametrar

- **värde**: pekar mot värde beskrivning för flera resurser.
- **index**: index för den instans som ska hämtas i resurs värdes mat ris.
- **instance_id_ptr**: pekar mot mål instansens ID.
- **int64_ptr**: pekar mot målet 64-bitars heltals värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är resursens värde inte ett heltals värde.

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a>nx_lwm2m_resource_multiple_get_objlnk

Hämta värdet för en objekt länk flera resurs instanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en objekt länk resurs instans från en flera resurser.

### <a name="parameters"></a>Parametrar

- **värde**: pekar mot värde beskrivning för flera resurser.
- **index**: index för den instans som ska hämtas i resurs värdes mat ris.
- **instance_id_ptr**: pekar mot mål instansens ID.
- **objlnk_ptr**: pekar mot länk värde för mål objekt.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är resursens värde inte ett objekt länk värde.

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a>nx_lwm2m_resource_multiple_get_opaque

Hämta värdet för en täckande flera resurs instanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en ogenomskinlig resurs instans från flera resurser.

Ett ogenomskinligt resurs värde består av en pekare till en buffert och en längd.

### <a name="parameters"></a>Parametrar

- **värde**: pekar mot värde beskrivning för flera resurser.
- **index**: index för den instans som ska hämtas i resurs värdes mat ris.
- **instance_id_ptr**: pekar mot mål instansens ID.
- **opaque_ptr_ptr**: pekar mot målets täckande buffer-pekare.
- **opaque_length_ptr**: pekar mot målets täckande buffertlängd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är resursens värde inte ett ogenomskinligt värde.

## <a name="nx_lwm2m_resource_multiple_get_string"></a>nx_lwm2m_resource_multiple_get_string

Hämta värdet för en sträng flera resurs instanser

### <a name="prototype"></a>Prototyp

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar värdet för en sträng resurs instans från flera resurser.

### <a name="parameters"></a>Parametrar

- **värde**: pekar mot värde beskrivning för flera resurser.
- **index**: index för den instans som ska hämtas i resurs värdes mat ris.
- **instance_id_ptr**: pekar mot mål instansens ID.
- **string_ptr_ptr**: pekar mot mål sträng pekaren.
- **string_length_ptr**: pekar mot mål strängens längd. Kan vara NULL om strängen är null-terminerad.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: åtgärden lyckades.
- **NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.
- **NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är instans svärdet inte ett sträng värde.
