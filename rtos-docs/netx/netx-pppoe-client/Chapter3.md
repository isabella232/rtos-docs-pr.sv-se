---
title: Kapitel 3 – Beskrivning Azure RTOS NetX PPPoE Client Services
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX PPPoE-klienttjänster (listas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8310006b7c188fa63402c931459ffd84ebb776c207dc520959208449862fe27f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790215"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a>Kapitel 3 – Beskrivning Azure RTOS NetX PPPoE Client Services

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX PPPoE-klienttjänster (listas nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade.

- **nx_pppoe_client_create Skapa** *en PPPoE-klientinstans*
- **nx_pppoe_client_delete ta** *bort en PPPoE-klientinstans*
- **nx_pppoe_client_host_uniq_set** *Ange värden unik för PPPoE-klienten*
- **nx_pppoe_client_host_uniq_set_extended** *Ange värden unik för PPPoE-klienten*
- **nx_pppoe_client_service_name_set** *Ange tjänstnamnet för PPPoE-klienten*
- **nx_pppoe_client_service_name_set_extended** *Ange tjänstnamnet för PPPoE-klienten*
- **nx_pppoe_client_session_connect** *Anslut PPPoE-klientsession till PPPoE-server*
- **nx_pppoe_client_session_packet_send skicka** *PPPoE-sessionspaket*
- **nx_pppoe_client_session_terminate** *avsluta PPPoE-sessionen*
- **nx_pppoe_client_session_get** *hämta den angivna PPPoE-sessionen inf*

## <a name="nx_pppoe_client_create"></a>nx_pppoe_client_create

Skapa en PPPoE-klientinstans

### <a name="prototype"></a>Prototyp

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a>Description

Den här tjänsten skapar en PPPoE-klientinstans med den användarangivna länkdrivrutinen för den angivna NetX IP-instansen. Om länkdrivrutinen inte har initierats och aktiverats initierar PPPoE-klientprogrammet länkdrivrutinen.

Dessutom måste programmet ange en paketpool som skapats tidigare för att PPPoE-klientinstansen ska kunna använda för intern paketallokering.

> [!NOTE]
> I allmänhet är det bra att skapa NetX IP-tråden med högre prioritet än PPPoE-klientens trådprioritet. Mer information om *hur du anger IP-trådprioritet* finns i nx_ip_create-tjänsten.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientkontrollblocket.
 - **namn** Namnet på den här PPPoE-klientinstansen.
 - **ip_ptr** Pekare till kontrollblock för IP-instans.
 - **interface_index** Gränssnittsindex.
 - **pool_ptr** Pekare till paketpool.
 - **stack_ptr** Pekare för att starta PPPoE-klienttrådens stackområde.
 - **stack_size** Storlek i byte i trådens stack.
 - **prioritet** Prioritet för interna PPPoE-klienttrådar (1–31).
 - **pppoe_link_driver** Länkdrivrutin som användaren har angett.
 - **pppoe_packet_receive** Funktionen för att ta emot paket som användaren har angett.

### <a name="return-values"></a>Returvärden

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Lyckades PPPoE-klienten skapas.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ogiltig PPPoE-klient, IP-adress, paketpool eller stack pekare.
 - NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Ogiltigt gränssnitt.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Ogiltig nyttolaststorlek för paketpool.
 - NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Ogiltig minnesstorlek.
 - NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Ogiltig prioritet för PPPoE-klienttråden.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a>nx_pppoe_client_delete

Ta bort en PPPoE-klientinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den tidigare skapade PPPoE-klientinstansen.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientkontrollblock

### <a name="return-values"></a>Returvärden

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Lyckad PPPoE-klient borttagning.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ogiltig PPPoE-klient pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a>nx_pppoe_client_host_uniq_set

Ange unik PPPoE-klientvärd

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a>Description

Den här tjänsten ställer in PPPoE-klientvärden unika. Host-Uniq används av en värd för att unikt associera en Access Concentrator till en viss värdbegäran.
Det kan vara binära data av val annat värde och längd som värden väljer.

> [!NOTE]
> värdens unika måste vara null-avslutad sträng.

> [!NOTE]
> Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nx_pppoe_client_host_uniq_set_extended().*

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientkontrollblocket.
 - **host_uniq** Pekare till en unik värd. Värdens unika måste vara en null-avslutad sträng.

### <a name="return-values"></a>Returvärden

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Lyckad unik PPPoE-klientvärduppsättning.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ogiltig PPPoE-klient pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a>nx_pppoe_client_host_uniq_set_extended

Ange unik PPPoE-klientvärd

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a>Description

Den här tjänsten ställer in PPPoE-klientvärden unika. Host-Uniq används av en värd för att unikt associera en Access Concentrator till en viss värdbegäran.
Det kan vara binära data av val annat värde och längd som värden väljer.

> [!NOTE]
> värdens unika måste vara null-avslutad sträng.

> [!NOTE]
> Den här tjänsten *ersätter nx_pppoe_client_host_uniq_set()*. Den här versionen tillhandahåller ytterligare längdinformation till tjänsten.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientkontrollblocket.
 - **host_uniq** Pekare till en unik värd. Värdens unika måste vara en null-avslutad sträng.
 - **host_uniq_length** Längden på host_uniq

### <a name="return-values"></a>Returvärden

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Lyckad unik PPPoE-klientvärduppsättning.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Ogiltig PPPoE-klient pekare.
 - **NX_SIZE_ERROR** (0x09) Kontrollera host_uniq_length misslyckas

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a>nx_pppoe_client_service_name_set

Ange PPPoE-klienttjänstnamn

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a>Description

Den här tjänsten anger PPPoE-klienttjänstens namn. Den Service-Name som anger vilken tjänst värden begär. Om Service-Name inte har angetts kommer värden att acceptera val av antal tjänster.

> [!NOTE]
> tjänstnamnet måste vara null-avslutad sträng

> [!NOTE]
> Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nx_pppoe_client_service_name_set_extended().*

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientkontrollblocket.
 - **service_name** Pekare till ett tjänstnamn. Tjänstnamnet måste vara null-avslutad sträng.

### <a name="return-values"></a>Returvärden

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Namnuppsättning för PPPoE-klienttjänsten.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Ogiltig PPPoE-klient pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a>nx_pppoe_client_service_name_set_extended

Ange PPPoE-klienttjänstnamn

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a>Description

Den här tjänsten anger PPPoE-klienttjänstens namn. Den Service-Name som anger vilken tjänst värden begär. Om Service-Name inte har angetts kommer värden att acceptera val av antal tjänster.

> [!NOTE]
> tjänstnamnet måste vara null-avslutad sträng.

> [!NOTE]
> Den här tjänsten *ersätter nx_pppoe_client_service_name_set()*. Den här versionen tillhandahåller ytterligare information om tjänstens namnlängd till funktionen.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientkontrollblocket.
 - **service_name** Pekare till ett tjänstnamn. Tjänstnamnet måste vara null-avslutad sträng.
 - **service_name_length** Längden på service_name

### <a name="return-values"></a>Returvärden

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Namnuppsättning för PPPoE-klienttjänsten.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Ogiltig PPPoE-klient pekare.
 - **NX_SIZE_ERROR** (0x09) Kontrollera service_name_length misslyckas

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a>nx_pppoe_client_session_connect

Anslut PPPoE-klientsession

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten upprättar EN PPPoE-sessionsanslutning med hjälp av en tidigare skapad PPPoE-klient till den angivna PPPoE-servern.

> [!NOTE]
> Den här funktionen måste anropas *efter nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* och *nx_pppoe_client_service_name_set*.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientkontrollblocket.
 - **wait_option** Väntealternativet medan anslutningen upprättas.

### <a name="return-values"></a>Returvärden

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Lyckades PPPoE-klientsessionen.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ogiltig PPPoE-klient pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a>nx_pppoe_client_session_packet_send

Skicka PPPoE-klientpaket till angiven session

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skickar PPPoE-paket med angivet sessions-ID.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientkontrollblocket.
 - **packet_ptr** Pekare till PPPoE-paket.

### <a name="return-values"></a>Returvärden

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Lyckades SKICKA PPPoE-klientpaket.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ogiltig PPPoE-klient pekare.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Ogiltigt PPPoE-klientpaket.
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE-session har inte upprättats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a>nx_pppoe_client_session_terminate

Avsluta PPPoE-klientsessionen

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten avslutar den angivna PPPoE-sessionen.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientkontrollblocket.

### <a name="return-values"></a>Returvärden

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Lyckad PPPoE-klientsession avslutas.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ogiltig PPPoE-klient pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a>nx_pppoe_client_session_get

Hämta den angivna PPPoE-sessionsinformationen

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Description

Den här tjänsten hämtar den angivna PPPoE-sessionsinformationen, serverns fysiska adress och sessions-ID.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_server_ptr** Pekare till PPPoE-klientens kontrollblock.
 - **server_mac_msw** MSW-pekare för serverns fysiska adress.
 - **server_mac_lsw** MSW-pekare för serverns fysiska adress.
 - **session_id** Pekare för sessions-ID.

### <a name="return-values"></a>Returvärden

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Lyckad PPPoE-klientsession hämta.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ogiltig PPPoE-klient pekare.
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE-session har inte upprättats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
