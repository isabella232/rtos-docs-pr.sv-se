---
title: Kapitel 3 – Beskrivning av Azure RTOS NetX Duo SNTP Client Services
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo SNTP-klienttjänster (anges nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7aee18642e480ec61488515164c8a6816753dca86eb8f6d146ea22d4956e037a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791677"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a>Kapitel 3 – Beskrivning av Azure RTOS NetX Duo SNTP Client Services

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Duo SNTP-klienttjänster (listas nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **FETSTIL** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

- **nx_sntp_client_create:** Skapa *SNTP-klienten*
- **nx_sntp_client_delete:** *Ta bort SNTP-klienten*
- **nx_sntp_client_get_local_time:** Hämta *lokal tid för SNTP-klienten*
- **nx_sntp_client_get_local_time_extended:** Hämta *lokal tid för SNTP-klienten*
- **nx_sntp_client_initialize_broadcast:** Initiera *klienten för IPv4-sändningsåtgärd*
- **nxd_sntp_client_initialize_broadcast:** Initiera *klienten för IPv6- eller IPv4-sändningsåtgärd*
- **nx_sntp_client_initialize_unicast:** *Initiera klienten för IPv4-unicast-åtgärd*
- **nxd_sntp_client_initialize_unicast:** *Initiera klienten för IPv4- eller IPv6-unicast-åtgärd*
- **nx_sntp_client_receiving_udpates:** Klienten *tar emot giltiga SNTP-uppdateringar*
- **nx_sntp_client_request_unicast_time:** Skicka *en unicast-begäran direkt till NTP-servern*
- **nx_sntp_client_run_broadcast:** Kör *klienten i sändningsläge*
- **nx_sntp_client_run_unicast:** Kör *klienten i unicast-läge*
- **nx_sntp_client_set_local_time:** Ange *initial lokal tid för SNTP-klienten*
- **nx_sntp_client_set_time_update_notify:** Ange *återanrop för SNTP-uppdatering*
- **nx_sntp_client_stop:** Stoppa *SNTP-klienttråden*
- **nx_sntp_client_utility_display_date_and_time:** Visa *NTP-tid i sekunder*
- **nx_sntp_client_utility_msecs_to_fraction:** Konvertera *millisekunder till en NTP-bråkkomponent*
- **nx_sntp_client_utility_usecs_to_fraction:** Konvertera *mikrosekunder till en NTP-bråkkomponent*
- **nx_sntp_client_utility_fraction_to_usecs:** Konvertera *en NTP-bråkkomponent till mikrosekunder*


## <a name="nx_sntp_client_create"></a>nx_sntp_client_create

Skapa en SNTP-klient

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a>Description

Den här tjänsten skapar en SNTP-klientinstans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientens kontrollblock

- **ip_ptr** Pekare till klientens IP-instans

- **iface_index** Nätverksgränssnittet Index till SNTP

- **packet_pool_ptr** Pekare till klientpaketpool

- **leap_second_handler** Återanrop för programsvar på kommande skott sekund

- **kiss_of_death_handler** Återanrop för programsvar på mottagande av Ett of Death-paket

- **random_number_generator** Återanrop till slumptalsgeneratortjänsten

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad klientgenerering

- **NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) Ogiltig icke-pekarindata

- NX_PTR_ERROR (0x07) Ogiltig pekare

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a>nx_sntp_client_delete

Ta bort en SNTP-klient

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en SNTP-klientinstans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientens kontrollblock

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad klientgenerering

- NX_PTR_ERROR (0x07) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a>nx_sntp_client_get_local_time

Hämta lokal tid för SNTP-klienten

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a>Description

Den här tjänsten hämtar lokal tid för SNTP-klienten med ett alternativ för buffertindata för att ta emot data i strängmeddelandeformat.

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nx_sntp_client_get_local_time_extended*().

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientens kontrollblock

- **sekunder** Pekare till lokala tidssekunder

- **bråktal** Komponent för lokal tidsdel

- **buffert** Pekare till buffert för att skriva tidsdata

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad klientgenerering

- NX_PTR_ERROR (0x07) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a>nx_sntp_client_get_local_time_extended

Hämta den utökade lokala tiden för SNTP-klienten

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a>Description

Den här tjänsten hämtar den utökade lokala tiden för SNTP-klienten med ett alternativ för buffert pekare för att ta emot data i strängmeddelandeformat.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientens kontrollblock

- **sekunder** Pekare till lokala tidssekunder

- **bråktal** Pekare till bråkkomponent

- **buffert** Pekare till buffert för att skriva tidsdata

- **buffer_size** Längden på bufferten

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad klientgenerering

- NX_PTR_ERROR (0x07) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten

- NX_SIZE_ERROR (0x09) Kontrollera buffer_size misslyckas

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a>nx_sntp_client_initialize_broadcast

Initiera klienten för sändningsåtgärd

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a>Description

Den här tjänsten initierar klienten för sändningsåtgärd genom att ange SNTP-serverns IP-adress och initiera startparametrar och tidsgränser för SNTP. Om både multicast- och broadcast-adresser inte är null väljs multicast-adressen. Om båda adresserna är null returneras ett fel. Observera att detta endast stöder IPv4-serveradresser.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientkontrollblock

- **multicast_server_address** SNTP-multicast-adress

- **broadcast_time_server** SNTP-serverns broadcast-adress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad klientgenerering

- **NX_INVALID_PARAMETERS** (0x4D) Ogiltiga icke-pekarindata

- NX_PTR_ERROR (0x07) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a>nxd_sntp_client_initialize_broadcast

Initiera klienten för IPv4- eller IPv6-sändningsåtgärden

### <a name="prototype"></a>Prototyp

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a>Description

Den här tjänsten initierar klienten för sändningsåtgärd genom att konfigurera SNTP-serverns IP-adress och initiera startparametrar och tidsgränser för SNTP. Om både broadcast- och multicast-adress pekare inte är null, väljs multicast-adressen. Om båda adress pekarna är null returneras ett fel. Detta stöder både IPv4- och IPv6-adresstyper. Observera att IPv6 inte stöder broadcast, så pekaren för broadcast-adressen är inställd på IPv6. Ett fel returneras.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientkontrollblock

- **multicast_server_address** Multicast-adress för SNTP-server

- **broadcast_server_address** SNTP-serverns broadcast-adress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har initierats

- NX_SNTP_PARAM_ERROR (0xD0D) Ogiltiga icke-pekarindata

- NX_PTR_ERROR (0x07) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten


### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a>nx_sntp_client_initialize_unicast

Konfigurera SNTP-klienten så att den körs i unicast

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a>Description

Den här tjänsten initierar klienten för unicast-åtgärd genom att ange SNTP-serverns IP-adress och initiera startparametrar och tidsgränser för SNTP. Observera att detta endast stöder IPv4-serveradresser.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientkontrollblock

- **unicast_time_server** SNTP-serverns IP-adress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har initierats

- NX_INVALID_PARAMETERS (0x4D) Ogiltiga icke-pekarindata

- NX_PTR_ERROR (0x07) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a>nxd_sntp_client_initialize_unicast

Konfigurera SNTP-klienten så att den körs i IPv4- eller IPv6-unicast

### <a name="prototype"></a>Prototyp

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a>Description

Den här tjänsten initierar klienten för unicast-åtgärder genom att konfigurera SNTP-serverns IP-adress och initiera startparametrar och tidsgränser för SNTP. Detta stöder både IPv4- och IPv6-adresstyper.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientkontrollblock

- **unicast_time_server** SNTP-serverns IP-adress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har initierats

- NX_INVALID_PARAMETERS (0x4D) Ogiltiga icke-pekarindata

- NX_PTR_ERROR (0x07) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a>nx_sntp_client_receiving_updates

Ange om klienten får giltiga uppdateringar

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a>Description

Den här tjänsten anger om klienten tar emot giltiga SNTP-uppdateringar. Om den längsta tiden utan en giltig uppdatering eller gräns för på varandra följande ogiltiga uppdateringar överskrids, returneras mottagningsstatusen som falskt. Observera att SNTP-klienten fortfarande körs och om programmet vill starta om SNTP-klienten med en annan unicast- eller broadcast-/multicast-server måste SNTP-klienten med hjälp av *nx_sntp_client_stop-tjänsten* initiera om klienten med någon av de initierade tjänsterna med en annan server.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientens kontrollblock.

- **receive_status** Pekare till indikator om klienten tar emot giltiga uppdateringar.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Klienten har fått uppdateringsstatus

- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a>nx_sntp_client_request_unicast_time

Skicka en unicast-begäran direkt till NTP-servern


### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a>Description

Med den här tjänsten kan programmet skicka en unicast-begäran direkt till NTP-servern asynkront från SNTP-klienttrådsaktiviteten. Väntealternativet anger hur lång tid det tar att vänta på ett svar. Om det lyckas kan programmet använda andra SNTP-klienttjänster för att hämta den senaste tiden. Mer information **finns i avsnittet SNTP Asynchronous Unicast Requests(SNTP Asynchronous Unicast Requests).**

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientens kontrollblock.

- **Wait_option** Väntealternativ för NTP-svar i tids tick.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) klienten skickar och tar emot unicast-uppdatering

- **NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) Klienttråden startades inte

- NX_PTR_ERROR (0x07) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a>nx_sntp_client_run_broadcast

Kör klienten i sändningsläge

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten startar klienten i sändningsläge där den väntar på att ta emot sändningar från SNTP-servern. Om ett giltigt SNTP-broadcast-meddelande tas emot, återställs tidsgränsen för SNTP-klienten för maximalt antal klienter utan uppdatering och antalet ogiltiga meddelanden i följd som tas emot. Om någon av dessa gränser överskrids anger SNTP-klienten serverstatusen till ogiltig, men den väntar fortfarande på att ta emot uppdateringar. Programmet kan avssöka SNTP-klientaktiviteten efter serverstatus, och om den är ogiltig stoppar du SNTP-klienten och initierar om den med en annan SNTP-sändningsadress. Den kan också växla till en unicast SNTP-server.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientens kontrollblock.

### <a name="return-values"></a>Returvärden

- **status** -------- Status för faktiskt slutförande

- **NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Klienten har redan startats

- **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Initieras inte

- NX_PTR_ERROR (0x07) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a>nx_sntp_client_run_unicast

Köra klienten i unicast-läge

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten startar klienten i unicast-läge där den regelbundet skickar en unicast-begäran till SNTP-servern för en tidsuppdatering. Om ett giltigt SNTP-meddelande tas emot, återställs tidsgränsen för SNTP-klienten för maximalt antal utan uppdatering, inledande avsökningsintervall och antal ogiltiga meddelanden i följd som tagits emot. Om någon av dessa gränser överskrids anger SNTP-klienten serverstatusen till ogiltig, men den avsöker fortfarande och väntar på att få uppdateringar. Programmet kan avssöka SNTP-klientaktiviteten efter serverstatus, och om den är ogiltig stoppar du SNTP-klienten och initierar om den med en annan SNTP unicast-adress. Den kan också växla till en SNTP-broadcast-server.

.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientens kontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Klienten har startats i unicast-läge

- **NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Klienten har redan startats

- **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Initieras inte

- NX_PTR_ERROR (0x07) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten


### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a>nx_sntp_client_set_local_time

Ange lokal tid för SNTP-klienten

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a>Description

Den här tjänsten anger lokal tid för SNTP-klienten med indatatiden i SNTP-format, t.ex. sekunder och "bråk" som är formatet för att placera bråkdelar av en sekund i hexadecimalt format. Den är avsedd för att uppdatera lokal tid för SNTP-klienten från en oberoende tids keeper, t.ex. en realtidsklocka. SNTP-protokollet är avsett för SNTP-tidsuppdateringar för att hålla lokal klocktid från "drifting". Tidsuppdateringar för SNTP-servern kan vara, men är inte avsedda att vara den enda indatan till lokal tid för SNTP-klienten om det inte finns någon oberoende tids keeper på programenheten.

Detta API kan också användas för att ge SNTP-klienten en bastid innan SNTP-klienttråden startas. Lokal tid för SNTP-klienten jämförs med mottagna uppdateringar för giltiga tidsdata. För första gången uppdateringen tas emot kan det finnas en mycket stor avvikelse. Det finns därför ett alternativ för SNTP-klienten att ignorera avvikelsen i den första uppdateringen. På så sätt kan SNTP-klienten starta utan bastid. Indatatiden kan hämtas från kända epoktider (vanligtvis tillgänglig på Internet) och beräknas som antalet sekunder sedan den 1 januari 1900 (fram till 2036 när en ny "epok" startas.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientens kontrollblock

- **sekunder** Sekunderskomponenten för tidsinmatningen

- **bråktal** Undersekunder-komponent i SNTP-bråkformat

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lokal tid har angetts

- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Initiering

### <a name="example"></a>Exempel

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a>nx_sntp_client_set_time_update_notify

Ange återanrop för SNTP-uppdatering

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a>Description

Den här tjänsten ställer in återanrop för att meddela programmet när SNTP-klienten tar emot en giltig tidsuppdatering. Den tillhandahåller det faktiska SNTP-meddelandet och SNTP-klientens lokala tid (vanligtvis samma) i NTP-format. Programmet kan använda NTP-data direkt eller anropa *nx_sntp_client_utility_display_date_time för* att konvertera tiden till läsbart format.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientens kontrollblock

- **time_update_cb** Pekare till återanropsfunktionen

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Ange återanrop

- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Initiering

### <a name="example"></a>Exempel

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a>nx_sntp_client_stop

Stoppa SNTP-klienttråden

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten stoppar SNTP-klienttråden. SNTP-klientens tråduppgifter, som körs i en oändlig loop, pausar vid varje iteration för att frigöra kontroll över SNTP-klienttillståndet och tillåta program att göra API-anrop på SNTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SNTP-klientens kontrollblock

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Stoppad klienttråd

- **NX_SNTP_CLIENT_NOT_STARTED** (0xDB) SNTP-klienttråden har inte startats

- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a>nx_sntp_client_utility_display_date_time

Konvertera en NTP-tid till datum- och tidssträng

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a>Description

Den här tjänsten konverterar SNTP-klientens lokala tid till datumformatet year month och returnerar datumet i den angivna bufferten. Den NX_SNTP_CURRENT_YEAR måste inte vara samma år som den aktuella klienttiden, men den måste definieras.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr pekare till SNTP-klient**

- **buffert** Pekare till buffert för att lagra datum

- **längd** Storleken på indatabufferten

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad konvertering

- **NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR inte har definierats eller ingen lokal klienttid har upprättats

- **NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) Otillräcklig buffertlängd


### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a>nx_sntp_client_utility_msecs_to_fraction

Konvertera millisekunder till en NTP-bråkkomponent

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a>Description

Den här tjänsten konverterar indata millisekunderna till NTP-bråkkomponenten. Den är avsedd att användas med program som har en startbastid för SNTP-klienten men inte i NTP-sekunders-/bråkformat. Antalet millisekunder måste vara mindre än 1 000 för att ett giltigt bråk ska bli.

### <a name="input-parameters"></a>Indataparametrar

- **millisekunder millisekunder att konvertera**

- **bråktal** Pekare till millisekunder som konverterats till bråk

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad konvertering

- **NX_SNTP_OVERFLOW_ERROR** (0xD32) Fel vid konvertering av tid till ett datum

- NX_SNTP_INVALID_TIME (0xD30) Ogiltig SNTP-datainmatning

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a>nx_sntp_client_utility_usecs_to_fraction

Konvertera mikrosekunder till en NTP-bråkkomponent

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a>Description

Den här tjänsten konverterar mikrosekunder för indata till NTP-bråkkomponenten. Den är avsedd att användas med program som har en startbastid för SNTP-klienten men inte i NTP-sekunders-/bråkformat. Antalet mikrosekunder måste vara mindre än 100 0000 för att göra ett giltigt bråk.

### <a name="input-parameters"></a>Indataparametrar

- **mikrosekunder** Mikrosekunder att konvertera

- **bråktal** Pekare till mikrosekunder konverterade till bråk

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad konvertering

- **NX_SNTP_OVERFLOW_ERROR** (0xD32) Fel vid konvertering av tid till ett datum

- NX_SNTP_INVALID_TIME (0xD30) Ogiltig SNTP-datainmatning

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a>nx_sntp_client_utility_fraction_to_usecs

Konvertera en NTP-bråkkomponent till mikrosekunder

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a>Description

Den här tjänsten konverterar indatakomponenten för NTP-fraktion till mikrosekunder.

### <a name="input-parameters"></a>Indataparametrar

- **bråktal att konvertera**

- **mikrosekunder** Pekare till bråk som konverterats till mikrosekunder

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad konvertering

- NX_SNTP_INVALID_TIME (0xD30) Ogiltig SNTP-datainmatning

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```