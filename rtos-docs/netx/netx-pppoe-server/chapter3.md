---
title: Kapitel 3 – Beskrivning Azure RTOS NetX PPPoE Server Services
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX PPPoE-servertjänster (listas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d184fc3c5e6ed74ef25045561b1613e280672f77385fbb13b8e84bccf051b301
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782820"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a>Kapitel 3 – Beskrivning Azure RTOS NetX PPPoE Server Services

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX PPPoE-servertjänster (listas nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **FETSTIL** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

- **nx_pppoe_server_create:** Skapa *en PPPoE-serverinstans*

- **nx_pppoe_server_ac_name_set:** Ange *namnet på Access Concentrator*

- **nx_pppoe_server_delete:** Ta *bort en PPPoE-serverinstans*

- **nx_pppoe_server_enable:** Aktivera *PPPoE-servertjänster*

- **nx_pppoe_server_disable:** *Inaktivera PPPoE-servertjänster*

- **nx_pppoe_server_callback_notify_set: Ange** *meddela funktioner för PPPoE-serveranrop*

- **nx_pppoe_server_service_name_set:** Ange *PPPoE-servertjänstnamn*

- **nx_pppoe_server_session_send:** Skicka *PPPoE-serverdata till den angivna sessionen*

- **nx_pppoe_server_session_packet_send:** Skicka *PPPoE-serverpaket till angiven session*

- **nx_pppoe_server_session_terminate:** Avsluta *den angivna PPPoE-sessionen*

- **nx_pppoe_server_session_get:** Hämta *den angivna sessionsinformationen*

## <a name="nx_pppoe_server_create"></a>nx_pppoe_server_create

Skapa en PPPoE-serverinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a>Description

Den här tjänsten skapar en PPPoE-serverinstans med den användarangivna länkdrivrutinen för den angivna NetX IP-instansen. Om länkdrivrutinen inte har initierats och aktiverats ansvarar PPPoE-programvaran för att initiera länkdrivrutinen.

Dessutom måste programmet ange en paketpool som skapats tidigare för att PPPoE-serverinstansen ska kunna använda för intern paketallokering.

Observera att det vanligtvis är en bra idé att skapa NetX IP-tråden med högre prioritet än PPPoE-serverns trådprioritet. Mer information om *hur du anger IP-trådprioritet* finns i nx_ip_create-tjänsten.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr:** Pekare till PPPoE-serverkontrollblocket.
- **name**: Namnet på den här PPPoE-serverinstansen.
- **ip_ptr: Pekare** till kontrollblock för IP-instans.
- **interface_index:** Gränssnittsindex.
- **pppoe_link_driver:** Länkdrivrutin som användaren har angett.
- **pool_ptr:** Pekare till paketpool.
- **stack_ptr:** Pekare för att starta PPPoE-servertrådens stackområde.
- **stack_size:** Storlek i byte i trådens stack.
- **prioritet:** Prioritet för interna PPPoE-servertrådar (1–31).

### <a name="return-values"></a>Returvärden

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Lyckades PPPoE-server skapa.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ogiltig PPPoE-server, IP- eller paketpool eller stackpekare.
- NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Ogiltigt gränssnitt.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Ogiltig nyttolaststorlek för paketpoolen.
- NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Ogiltig minnesstorlek.
- NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) Ogiltig prioritet för PPPoE-servertråden.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a>nx_pppoe_server_delete

Ta bort en PPPoE-serverinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den tidigare skapade PPPoE-serverinstansen.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr:** Pekare till PPPoE-serverkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Lyckad PPPoE-server-borttagning.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ogiltig PPPoE-serverpekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a>nx_pppoe_server_enable

Aktivera PPPoE-servertjänsten

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar PPPoE-servertjänsterna.

> [!NOTE]
> Den här funktionen måste anropas *efter nx_pppoe_server_create* och *nx_pppoe_server_callback_notify_set*.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr:** Pekare till PPPoE-serverkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Lyckad PPPoE-server-borttagning.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ogiltig PPPoE-serverpekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a>nx_pppoe_server_disable

Inaktivera PPPoE-servertjänsten

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar PPPoE-servertjänsterna.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr:** Pekare till PPPoE-serverkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Lyckad PPPoE-server-borttagning.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ogiltig PPPoE-serverpekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a>nx_pppoe_server_callback_notify_set

Ange meddela funktioner för PPPoE-serveranrop 

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a>Description

Den här tjänsten ställer in PPPoE Server-återanrop av meddela funktioner.

> [!NOTE]
> Den här funktionen måste *anropas innan nx_pppoe_server_enabl och* pppoe_data_receive_notify-funktionspekaren måste anges, om *inte, nx_pppoe_server_enable* kommer att misslyckas.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr:** Pekare till PPPoE-serverkontrollblocket.
- **pppoe_discover_initiation_notify:** Programfunktion som anropas när PPPoE identifierar initieringsmeddelandet tas emot. Om det här värdet är NULL identifierar du att funktionen för initiering av motringning är inaktiverad.
- **pppoe_discover_request_notify:** Programfunktion som anropas när ett meddelande om pppoe-identifieringsbegäran tas emot. Om det här värdet är NULL är funktionen för återanrop av begäran inaktiverad.
- **pppoe_discover_terminate_notify:** Programfunktion som anropas när ett meddelande om att PPPoE-identifieringen har tagits emot tas emot. Om det här värdet är NULL är funktionen avsluta motringning inaktiverad.
- **pppoe_discover_terminate_confirm:** Programfunktion som anropas när ett meddelande om att PPPoE-identifieringen avslutas skickas. Om det här värdet är NULL identifierar du att funktionen för att avbryta motringning är inaktiverad.
- **pppoe_data_receive_notify:** Programfunktion som anropas när PPPoE-datameddelande tas emot. Det här värdet får inte vara noll.
- **pppoe_data_send_notify:** Programfunktion som anropas när PPPoE-datameddelandet skickas. Om det här värdet är NULL inaktiveras funktionen för återanrop vid datasänding.

### <a name="return-values"></a>Returvärden

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Lyckades PPPoE-server ta bort.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ogiltig PPPoE-server pekare eller funktionspekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a>nx_pppoe_server_ac_name_set

Ange Access Concentrator-namn

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a>Description

Den här funktionen anger funktionsanropet Access Concentrator name.

> [!NOTE]
> Strängen för ac_name måste vara NULL-avslutad och längden på ac_name matchar längden som anges i argumentlistan.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr:** Pekare till PPPoE-serverkontrollblock.
- **ac_name:** Access Concentrator-namn.
- **ac_name_length:** Längden på ac_ame.

### <a name="return-values"></a>Returvärden

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Lyckad PPPoE-serveruppsättning.
- **NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) Ogiltig PPPoE-server, IP-adress, paketpool eller stackpekare.
- **NX_SIZE_ERROR**: (0x09) Kontrollera name_length misslyckas.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a>nx_pppoe_server_service_name_set

Ange PPPoE-servertjänstnamn

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a>Description

Den här tjänsten anger PPPoE Server-tjänstens namn.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr:** Pekare till PPPoE-serverkontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Lyckades PPPoE-server ta bort.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ogiltig PPPoE-serverpekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a>nx_pppoe_server_session_send

Skicka PPPoE-serverdata till angiven session

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a>Description

Den här tjänsten skickar PPPoE-ram med angivet sessions-ID.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr:** Pekare till PPPoE-serverkontrollblock.
- **session_index:** Indexet för sessionen.
- **data_ptr:** Pekare till början av PPPoE Server-dataramen.
- **data_length:** Längden på PPPoE Server-dataramen.

### <a name="return-values"></a>Returvärden

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Lyckades PPPoE-server ta bort.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ogiltig PPPoE-serverpekare.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE-servertjänsten är inte aktiverad.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Ogiltigt PPPoE-sessionsindex.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE-session har inte upprättats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a>nx_pppoe_server_session_packet_send

Skicka PPPoE-serverpaket till angiven session

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skickar PPPoE-paket med angivet sessions-ID.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr:** Pekare till PPPoE-serverkontrollblock.
- **session_index:** Indexet för sessionen.
- **packet_ptr:** Pekare till PPPoE-paket.

### <a name="return-values"></a>Returvärden

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Lyckades PPPoE-server ta bort.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ogiltig PPPoE-serverpekare.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Ogiltigt PPPoE-serverpaket.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE-servertjänsten är inte aktiverad.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Ogiltigt PPPoE-sessionsindex.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE-session har inte upprättats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a>nx_pppoe_server_session_terminate

Avsluta den angivna PPPoE-sessionen

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a>Description

Den här tjänsten avslutar den angivna PPPoE-sessionen.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr:** Pekare till PPPoE-serverkontrollblock.
- **session_index:** Indexet för sessionen.

### <a name="return-values"></a>Returvärden

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Lyckades PPPoE-server ta bort.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ogiltig PPPoE-serverpekare.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE-servertjänsten är inte aktiverad.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Ogiltigt PPPoE-sessionsindex.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE-session har inte upprättats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a>nx_pppoe_server_session_get

Hämta den angivna PPPoE-sessionsinformationen

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Description

Den här tjänsten hämtar den angivna PPPoE-sessionsinformationen, klientens fysiska adress och sessions-ID.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr:** Pekare till PPPoE-serverkontrollblock.
- **session_index:** Indexet för sessionen.
- **client_mac_msw:** MSW-pekare för klientens fysiska adress.
- **client_mac_lsw:** MSW-pekare för klientens fysiska adress.
- **session_id:** Pekare för sessions-ID.

### <a name="return-values"></a>Returvärden

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Lyckades PPPoE-server ta bort.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ogiltig PPPoE-serverpekare.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Ogiltigt PPPoE-sessionsindex.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE-session har inte upprättats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a>PppInitInd

Konfigurera standardnamnet för tjänsten

### <a name="prototype"></a>Prototyp

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a>Description

PPPoE-programvaran exponerar den här funktionen så att TTP:s programvara kan konfigurera det "standardtjänstnamn" som PPPoE ska använda för att filtrera inkommande PADI-begäranden. PPPoE-programvaran bör komma ihåg den här informationen, och om ett PADI-paket tas emot som innehåller ett tjänstnamn som matchar ska det anropa PppDiscoverReq.

### <a name="input-parameters"></a>Indataparametrar

- **length**: Längden på standardtjänstnamnet.
- **aData:** Standardtjänstnamn.

### <a name="return-values"></a>Returvärden

**Ingen**

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a>PppDiscoverCnf

Definiera fältet Tjänstnamn för PADO-paketet

### <a name="prototype"></a>Prototyp

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a>Description

PPPoE-programvaran exponerar den här funktionen så att TTP:s programvara kan definiera fältet Tjänstnamn för PADO-paketet. PPPoE-programvaran bör inte skicka PADO förrän PppDiscoverCnf anropas.

PADO-paketet ska innehålla ett åtkomstkoncentratornamn (med tagg-ID:t 0x0102 enligt definitionen i RFC2516) som definieras vid initieringen av PPPoE-programvaran.

Flera tjänstnamn kan skickas i aData, där varje namn ska avslutas med null.

Null-tecknet används som avgränsare för att ge maximal flexibilitet om andra kommandon måste skickas som en del av tjänstnamnet.

### <a name="input-parameters"></a>Indataparametrar

- **length**: Längden på standardtjänstnamnet.
- **aData:** Standardtjänstnamn.
- **interfaceHandle:** Gränssnittshandtag.

### <a name="return-values"></a>Returvärden

**Ingen**

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a>PppOpenCnf

Acceptera eller avvisa PPPoE-sessionen

### <a name="prototype"></a>Prototyp

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a>Description

PPPoE-programvaran exponerar den här funktionen så att TTP:s programvara kan godkänna eller avvisa PPPoE-sessionen.  Som svar på detta bör PPPoE-stacken acceptera anslutningen och tilldela ett unikt PPPoE Session_ID-nummer som är associerat med interfaceHandle.

### <a name="input-parameters"></a>Indataparametrar

- **accept**: NX_TRUE om anslutningen ska godkännas.
- **interfaceHandle:** Gränssnittshandtag.

### <a name="return-values"></a>Returvärden

**Ingen**

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a>PppCloseInd

Stänga en PPPoE-session

### <a name="prototype"></a>Prototyp

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a>Description

PPPoE-programvaran exponerar den här funktionen så att TTP:s programvara kan stänga en PPPoE-session.

PPPoE-programvaran anger orsakskodsträngen i den Generic-Error taggen (0x0203) i PADT-meddelandet

### <a name="input-parameters"></a>Indataparametrar

- **interfaceHandle:** Gränssnittshandtag.
- **causeCode:** Null-avslutad sträng för att skicka information om orsaken till att anslutningen stängs från PPPoE-servern.

### <a name="return-values"></a>Returvärden

**Ingen**

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a>PppCloseCnf

Bekräfta att referensen har frisats

### <a name="prototype"></a>Prototyp

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a>Description

PPPoE-programvaran exponerar den här funktionen så att TTP:s programvara kan bekräfta att referensen har frispolerats.

### <a name="input-parameters"></a>Indataparametrar

- **interfaceHandle:** Gränssnittshandtag.

### <a name="return-values"></a>Returvärden

**Ingen**

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a>PppTransmitDataCnf

Tillåt att tidigare PPP-data bekräftas

### <a name="prototype"></a>Prototyp

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a>Description

PPPoE-programvaran exponerar den här funktionen för att tillåta att en tidigare PppTransmitDataReq bekräftas.  Det innebär att TTP:s programvara är redo för en ny PPP-ram från PPPoE.

### <a name="input-parameters"></a>Indataparametrar

- **interfaceHandle:** Gränssnittshandtag.
- **aData:** Pekar den PPP-databuffert som har godkänts.
- **Packet_id:** Paketidentifierare.

### <a name="return-values"></a>Returvärden

**Ingen**

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a>PppReceiveDataInd

Ta emot data från överföring via Ethernet

### <a name="prototype"></a>Prototyp

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a>Description

PPPoE-programvaran exponerar den här funktionen för att ta emot data för överföring via Ethernet

### <a name="input-parameters"></a>Indataparametrar

- **interfaceHandle:** Gränssnittshandtag.
- **length**: Antalet byte i aData.
- **aData:** Databuffert som innehåller ramen för PPP-data.

### <a name="return-values"></a>Returvärden

**Ingen**

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```