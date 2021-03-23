---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX PPPoE Client Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX PPPoE-klienttjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 246115fc97d7597246f7fd5b4fb88cb615baab33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825590"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX PPPoE Client Services

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX PPPoE-klienttjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nx_pppoe_client_create** *skapa en PPPoE-klient instans*
- **nx_pppoe_client_delete** *ta bort en PPPoE-klient instans*
- **nx_pppoe_client_host_uniq_set** *Ange värden som unik för PPPoE-klienten*
- **nx_pppoe_client_host_uniq_set_extended** *Ange värden som unik för PPPoE-klienten*
- **nx_pppoe_client_service_name_set** *Ange tjänst namnet för PPPoE-klienten*
- **nx_pppoe_client_service_name_set_extended** *Ange tjänst namnet för PPPoE-klienten*
- **nx_pppoe_client_session_connect** *ansluta PPPoE-klientsessionen till PPPoE-servern*
- **nx_pppoe_client_session_packet_send** *Skicka PPPoE-session paket*
- **nx_pppoe_client_session_terminate** *Avsluta PPPoE-sessionen*
- **nx_pppoe_client_session_get** *Hämta den angivna INF-filen för PPPoE-sessionen*

## <a name="nx_pppoe_client_create"></a>nx_pppoe_client_create

Skapa en PPPoE-klient instans

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

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en PPPoE-klient instans med den angivna länk driv rutinen för den angivna NetX IP-instansen. Om länk driv rutinen inte har initierats, och Aktiver ATS, ansvarar PPPoE-klientprogrammet för att initiera länk driv rutinen.

Dessutom måste programmet ange en tidigare skapad modempool för den PPPoE-klient instans som ska användas för intern paket tilldelning.

> [!NOTE]
> I allmänhet är det en bra idé att skapa en NetX IP-tråd med högre prioritet än PPPoE-klientens tråd prioritet. Mer information om hur du anger prioritet för IP-tråd finns i *nx_ip_create* -tjänsten.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.
 - **namn** Namnet på den här PPPoE-klient instansen.
 - **ip_ptr** Pekare som styr blockering av IP-instans.
 - **interface_index** Gränssnitts index.
 - **pool_ptr** Pekare till Packet bassäng.
 - **stack_ptr** Pekare för start av PPPoE-klient trådens stack Area.
 - **stack_size** Storlek i byte i trådens stack.
 - **prioritet** Prioritet för interna PPPoE-klient trådar (1-31).
 - **pppoe_link_driver** Användarens angivna länk driv rutin.
 - **pppoe_packet_receive** Användare som har fått funktionen paket mottagning.

### <a name="return-values"></a>Retur värden

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad PPPoE-klient skapa.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient, IP, paket bassäng eller stack pekare.
 - NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) ogiltigt gränssnitt.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) ogiltig nytto Last storlek för Packet bassäng.
 - NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) ogiltig minnes storlek.
 - NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) ogiltig prioritet för PPPoE-klient tråd.

### <a name="allowed-from"></a>Tillåten från

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

Ta bort en PPPoE-klient instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den tidigare skapade PPPoE-klienten.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block

### <a name="return-values"></a>Retur värden

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad borttagning av PPPoE-klienten.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a>nx_pppoe_client_host_uniq_set

Ange unik värd för PPPoE-klienten

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger en unik PPPoE-klient värd. Host-Uniq används av en värd för att unikt koppla en åtkomst-koncentrator till en viss värd förfrågan.
Det kan vara binära data för alla värden och längden som värden väljer.

> [!NOTE]
> värdens unika måste vara null-terminerad sträng.

> [!NOTE]
> Den här tjänsten är föråldrad. Utvecklare uppmanas att migrera till *nx_pppoe_client_host_uniq_set_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.
 - **host_uniq** Pekar till en värd unik. Värdens unika måste vara null-terminerad sträng.

### <a name="return-values"></a>Retur värden

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad konfiguration av en unik PPPoE-klient värd.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a>nx_pppoe_client_host_uniq_set_extended

Ange unik värd för PPPoE-klienten

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger en unik PPPoE-klient värd. Host-Uniq används av en värd för att unikt koppla en åtkomst-koncentrator till en viss värd förfrågan.
Det kan vara binära data för alla värden och längden som värden väljer.

> [!NOTE]
> värdens unika måste vara null-terminerad sträng.

> [!NOTE]
> Den här tjänsten ersätter *nx_pppoe_client_host_uniq_set ()*. Den här versionen tillhandahåller ytterligare längd information till tjänsten.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.
 - **host_uniq** Pekar till en värd unik. Värdens unika måste vara null-terminerad sträng.
 - **host_uniq_length** Host_uniq längd

### <a name="return-values"></a>Retur värden

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad konfiguration av en unik PPPoE-klient värd.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0XD1) ogiltig PPPoE-klient pekare.
 - **NX_SIZE_ERROR** (0X09) kontrol lera host_uniq_length inte

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a>nx_pppoe_client_service_name_set

Ange PPPoE-klientens tjänst namn

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger PPPoE-klientens tjänst namn. Service-Name som indikerar den tjänst som värden begär. Om Service-Name inte är inställt, anger värden att antalet tjänster ska accepteras.

> [!NOTE]
> tjänst namnet måste vara null-avslutad sträng

> [!NOTE]
> Den här tjänsten är föråldrad. Utvecklare uppmanas att migrera till *nx_pppoe_client_service_name_set_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.
 - **SERVICE_NAME** Pekar till ett tjänst namn. Tjänst namnet måste vara null-avslutad sträng.

### <a name="return-values"></a>Retur värden

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad PPPoE-klient tjänst namn angavs.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0XD1) ogiltig PPPoE-klient pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a>nx_pppoe_client_service_name_set_extended

Ange PPPoE-klientens tjänst namn

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger PPPoE-klientens tjänst namn. Service-Name som indikerar den tjänst som värden begär. Om Service-Name inte är inställt, anger värden att antalet tjänster ska accepteras.

> [!NOTE]
> tjänst namnet måste vara null-avslutad sträng.

> [!NOTE]
> Den här tjänsten ersätter *nx_pppoe_client_service_name_set ()*. Den här versionen tillhandahåller ytterligare information om tjänst namnens längd till funktionen.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.
 - **SERVICE_NAME** Pekar till ett tjänst namn. Tjänst namnet måste vara null-avslutad sträng.
 - **service_name_length** Service_name längd

### <a name="return-values"></a>Retur värden

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad PPPoE-klient tjänst namn angavs.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0XD1) ogiltig PPPoE-klient pekare.
 - **NX_SIZE_ERROR** (0X09) kontrol lera service_name_length inte

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a>nx_pppoe_client_session_connect

Ansluta PPPoE-klientsession

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten gör PPPoE-sessionen ansluten med en tidigare skapad PPPoE-klient till den angivna PPPoE-servern.

> [!NOTE]
> Den här funktionen måste anropas efter nx_pppoe_client_create *nx_pppoe_client_host_uniq_set* och *nx_pppoe_client_service_name_set*.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.
 - **wait_option** Alternativet vänta medan anslutningen upprättas.

### <a name="return-values"></a>Retur värden

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad PPPoE-klientsession Connect.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a>nx_pppoe_client_session_packet_send

Skicka PPPoE-klient paketet till en angiven session

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar PPPoE-paket med angivet sessions-ID.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.
 - **packet_ptr** Pekare till PPPoE-paket.

### <a name="return-values"></a>Retur värden

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckades skicka PPPoE-klient paket.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient pekare.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) ogiltigt PPPoE-klient paket.
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE-sessionen har inte upprättats.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a>nx_pppoe_client_session_terminate

Avsluta PPPoE-klientsession

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten avslutar den angivna PPPoE-sessionen.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.

### <a name="return-values"></a>Retur värden

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) en lyckad PPPoE-klientsession avslutades.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a>nx_pppoe_client_session_get

Hämta den angivna informationen om PPPoE-sessionen

### <a name="prototype"></a>Prototyp

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den angivna PPPoE-sessionsinformation, serverns fysiska adress och sessions-ID.

### <a name="input-parameters"></a>Indataparametrar

 - **pppoe_server_ptr** Pekare till PPPoE-klientens kontroll block.
 - **server_mac_msw** Serverns fysiska MSW-pekare.
 - **server_mac_lsw** Serverns fysiska MSW-pekare.
 - **session_id** Sessions-ID-pekare.

### <a name="return-values"></a>Retur värden

 - **NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad PPPoE-klientsession Hämta.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient pekare.
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE-sessionen har inte upprättats.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
