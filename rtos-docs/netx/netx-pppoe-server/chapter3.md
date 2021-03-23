---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX PPPoE Server Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX PPPoE Server-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d1137fae4dfea428d50e2defed94de6a838b01c6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826601"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX PPPoE Server Services

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX PPPoE Server-tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nx_pppoe_server_create**: *skapa en PPPoE-serverinstans*

- **nx_pppoe_server_ac_name_set**: *Ange namn på åtkomst kon centra Tor*

- **nx_pppoe_server_delete**: *ta bort en PPPoE-serverinstans*

- **nx_pppoe_server_enable**: *aktivera PPPoE Server-tjänster*

- **nx_pppoe_server_disable**: *inaktivera PPPoE Server-tjänster*

- **nx_pppoe_server_callback_notify_set**: *Ange återanrop för PPPoE-serverns aviserings funktioner*

- **nx_pppoe_server_service_name_set**: *Ange ett tjänst namn för PPPoE-servern*

- **nx_pppoe_server_session_send**: *Skicka PPPoE-serverns data till en angiven session*

- **nx_pppoe_server_session_packet_send**: *Skicka PPPoE-serverns paket till en angiven session*

- **nx_pppoe_server_session_terminate**: *avsluta den angivna PPPoE-sessionen*

- **nx_pppoe_server_session_get**: *Hämta information om den angivna sessionen*

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

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en PPPoE-serverinstans med den angivna länk driv rutinen för den angivna NetX IP-instansen. Om länk driv rutinen inte har initierats och är aktive rad, är den ansvarig för PPPoE Sever-programvara som initierar länk driv rutinen.

Dessutom måste programmet ange en tidigare skapad modempool för att PPPoE-serverinstansen ska användas för intern paket tilldelning.

Observera att det vanligt vis är en bra idé att skapa NetX IP-tråd med högre prioritet än tråd prioriteten för PPPoE-servern. Mer information om hur du anger prioritet för IP-tråd finns i *nx_ip_create* -tjänsten.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.
- **namn**: namnet på den här PPPoE-serverinstansen.
- **ip_ptr**: pekare till Control-Block för IP-instans.
- **interface_index**: gränssnitts index.
- **pppoe_link_driver**: användarens angivna länk driv rutin.
- **pool_ptr**: pekar mot Packet bassäng.
- **stack_ptr**: pekare för att starta PPPoE-Server trådens stack Area.
- **stack_size**: storlek i byte i trådens stack.
- **prioritet**: prioritet för interna PPPoE-Server trådar (1-31).

### <a name="return-values"></a>Retur värden

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad PPPoE-Server skapa.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server, IP, Packet bassäng eller stack pekare.
- NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) ogiltigt gränssnitt.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) ogiltig nytto Last storlek för Packet bassäng.
- NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) ogiltig minnes storlek.
- NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) ogiltig prioritet för PPPoE-serverns tråd.

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den tidigare skapade PPPoE-serverinstansen.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.

### <a name="return-values"></a>Retur värden

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Med den här tjänsten kan du använda PPPoE-Server tjänsterna.

> [!NOTE]
> Den här funktionen måste anropas efter *nx_pppoe_server_create* och *nx_pppoe_server_callback_notify_set*.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.

### <a name="return-values"></a>Retur värden

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar PPPoE-Server tjänsterna.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.

### <a name="return-values"></a>Retur värden

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a>nx_pppoe_server_callback_notify_set

Ange aviserings funktioner för motringning från PPPoE-Server 

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

### <a name="description"></a>Beskrivning

Den här tjänsten anger att återanrop i PPPoE-servern ska meddela funktioner.

> [!NOTE]
> Den här funktionen måste anropas före *nx_pppoe_server_enabl och* pppoe_data_receive_notify-funktions pekare måste anges, om inte, *nx_pppoe_server_enable* kommer att Miss lyckas.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.
- **pppoe_discover_initiation_notify**: program funktion som anropas när ett meddelande om att initiering av PPPoE-identifiering tas emot. Om det här värdet är NULL inaktive ras funktionen motringning.
- **pppoe_discover_request_notify**: program funktion som anropas när ett meddelande om PPPoE-Discover tas emot. Om det här värdet är NULL är funktionen motringning för begäran inaktive rad.
- **pppoe_discover_terminate_notify**: program funktion som anropas när ett meddelande om att avsluta PPPoE-identifiering tas emot. Om det här värdet är NULL är funktionen avsluta motringning inaktive rad.
- **pppoe_discover_terminate_confirm**: program funktion som anropas när ett meddelande om att avsluta PPPoE-identifiering skickas. Om det här värdet är NULL är funktionen avsluta motringning inaktive rad.
- **pppoe_data_receive_notify**: program funktion som anropas när ett data meddelande för PPPoE tas emot. Värdet får inte vara noll.
- **pppoe_data_send_notify**: program funktion som anropas när ett data meddelande för PPPoE skickas. Om det här värdet är NULL är funktionen för att skicka motringning inaktive rad.

### <a name="return-values"></a>Retur värden

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare eller funktions pekare.

### <a name="allowed-from"></a>Tillåten från

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

Ange namn på åtkomst kon centra Tor

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a>Beskrivning

Den här funktionen ställer in åtkomst till koncentrator Name funktion anrop.

> [!NOTE]
> Strängen för ac_name måste vara NULL-terminerad och längden på ac_name matchar den längd som anges i argument listan.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.
- **ac_name**: åtkomst till koncentrator namn.
- **ac_name_length**: längden på ac_ame.

### <a name="return-values"></a>Retur värden

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad PPPoE-Server uppsättning.
- **NX_PPPOE_SERVER_PTR_ERROR**: (0XC1) ogiltig PPPoE-Server, IP, Packet bassäng eller stack pekare.
- **NX_SIZE_ERROR**: (0X09) kontrol lera name_length inte.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a>nx_pppoe_server_service_name_set

Ange namn på tjänsten PPPoE-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger tjänst namnet för en PPPoE-Server.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.

### <a name="return-values"></a>Retur värden

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.

### <a name="allowed-from"></a>Tillåten från

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

Skicka PPPoE-serverns data till en angiven session

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar PPPoE-ramen med angivet sessions-ID.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.
- **session_index**: sessionens index.
- **data_ptr**: pekare för att starta data rutan för PPPoE-servern.
- **data_length**: längden på data fältet för PPPoE-servern.

### <a name="return-values"></a>Retur värden

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE-servertjänsten är inte aktive rad.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) ogiltigt PPPoE-sessions index.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE-sessionen har inte upprättats.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a>nx_pppoe_server_session_packet_send

Skicka PPPoE-serverns paket till en angiven session

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar PPPoE-paket med angivet sessions-ID.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.
- **session_index**: sessionens index.
- **packet_ptr**: pekare till PPPoE-paket.

### <a name="return-values"></a>Retur värden

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) ogiltigt PPPoE-Server paket.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE-servertjänsten är inte aktive rad.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) ogiltigt PPPoE-sessions index.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE-sessionen har inte upprättats.

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten avslutar den angivna PPPoE-sessionen.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.
- **session_index**: sessionens index.

### <a name="return-values"></a>Retur värden

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE-servertjänsten är inte aktive rad.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) ogiltigt PPPoE-sessions index.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE-sessionen har inte upprättats.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a>nx_pppoe_server_session_get

Hämta den angivna informationen om PPPoE-sessionen

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den angivna PPPoE-sessionsinformation, klientens fysiska adress och sessions-ID.

### <a name="input-parameters"></a>Indataparametrar

- **pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.
- **session_index**: sessionens index.
- **client_mac_msw**: MSW-pekare för klientens fysiska adress.
- **client_mac_lsw**: MSW-pekare för klientens fysiska adress.
- **session_id**: sessions-ID-pekare.

### <a name="return-values"></a>Retur värden

- **NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) ogiltigt PPPoE-sessions index.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE-sessionen har inte upprättats.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a>PppInitInd

Konfigurera standard tjänst namnet

### <a name="prototype"></a>Prototyp

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a>Beskrivning

PPPoE-programmet kommer att visa den här funktionen för att tillåta att TTP-programvaran konfigurerar standard tjänst namnet som PPPoE ska använda för att filtrera inkommande PADI-begäranden. PPPoE-programvaran bör komma ihåg den här informationen och om ett PADI-paket tas emot som innehåller ett tjänst namn som matchar, ska det anropa PppDiscoverReq.

### <a name="input-parameters"></a>Indataparametrar

- **längd**: längden på standard tjänst namnet.
- **aData**: standard tjänst namn.

### <a name="return-values"></a>Retur värden

**Ingen**

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a>PppDiscoverCnf

Definiera tjänst namns fältet för PADO-paketet

### <a name="prototype"></a>Prototyp

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a>Beskrivning

PPPoE-programmet kommer att visa den här funktionen för att tillåta att TTP-programvaran definierar fältet för tjänst namn i PADO-paketet. PPPoE-programvaran bör inte skicka PADO förrän PppDiscoverCnf anropas.

PADO-paketet måste innehålla ett namn för åtkomst koncentrator (med taggen ID 0x0102 som definieras i RFC2516), definierat i initieringen av PPPoE-programvaran.

Flera tjänst namn kan skickas i aData, där varje namn ska vara null.

NULL-tecken används som avgränsare för att ge maximal flexibilitet om andra kommandon måste skickas in som en del av tjänstens namn.

### <a name="input-parameters"></a>Indataparametrar

- **längd**: längden på standard tjänst namnet.
- **aData**: standard tjänst namn.
- **interfaceHandle**: gränssnitts referens.

### <a name="return-values"></a>Retur värden

**Ingen**

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

PPPoE-programmet kommer att exponera den här funktionen så att TTP-programvaran kan godkänna eller avvisa PPPoE-sessionen.  Som svar på det här är PPPoE-stacken att godkänna anslutningen och tilldela ett unikt PPPoE-Session_ID kopplat till interfaceHandle.

### <a name="input-parameters"></a>Indataparametrar

- **acceptera**: NX_TRUE om anslutningen ska godkännas.
- **interfaceHandle**: gränssnitts referens.

### <a name="return-values"></a>Retur värden

**Ingen**

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

PPPoE-programvaran kommer att exponera den här funktionen för att låta TTP-programvaran stänga en PPPoE-session.

PPPoE-programvaran anger orsaks kod strängen i Generic-Error-taggen (0x0203) i PADT-meddelandet

### <a name="input-parameters"></a>Indataparametrar

- **interfaceHandle**: gränssnitts referens.
- **causeCode**: null-avslutad sträng för sändning av information om orsaken till att anslutningen stängdes från PPPoE-servern.

### <a name="return-values"></a>Retur värden

**Ingen**

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a>PppCloseCnf

Bekräfta att referensen har frigjorts

### <a name="prototype"></a>Prototyp

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a>Beskrivning

PPPoE-programmet kommer att exponera den här funktionen för att tillåta att TTP-programvaran bekräftar att referensen har frigjorts.

### <a name="input-parameters"></a>Indataparametrar

- **interfaceHandle**: gränssnitts referens.

### <a name="return-values"></a>Retur värden

**Ingen**

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a>PppTransmitDataCnf

Tillåt att en tidigare PPP-data bekräftas

### <a name="prototype"></a>Prototyp

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a>Beskrivning

PPPoE-programmet kommer att exponera den här funktionen så att en föregående PppTransmitDataReq kan bekräftas.  Det innebär att TTP-programvaran är redo för en ny PPP-ram från PPPoE.

### <a name="input-parameters"></a>Indataparametrar

- **interfaceHandle**: gränssnitts referens.
- **aData**: pekar på den PPP-databuffert som har godkänts.
- **Packet_id**: paket-ID.

### <a name="return-values"></a>Retur värden

**Ingen**

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a>PppReceiveDataInd

Ta emot data från överföring över Ethernet

### <a name="prototype"></a>Prototyp

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a>Beskrivning

PPPoE-programmet kommer att exponera den här funktionen för att ta emot data för överföring via Ethernet

### <a name="input-parameters"></a>Indataparametrar

- **interfaceHandle**: gränssnitts referens.
- **längd**: antalet byte i aData.
- **aData**: databuffert som innehåller en ram med PPP-data.

### <a name="return-values"></a>Retur värden

**Ingen**

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```