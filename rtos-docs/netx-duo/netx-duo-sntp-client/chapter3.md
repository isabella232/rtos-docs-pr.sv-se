---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo SNTP Client Services
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo SNTP-klienttjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b2b878cd084ca1c1cdd1eed4333d303fe32ad6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825746"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo SNTP Client Services

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo SNTP-klienttjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nx_sntp_client_create**: *skapa en SNTP-klient*
- **nx_sntp_client_delete**: *ta bort SNTP-klienten*
- **nx_sntp_client_get_local_time**: *Hämta lokal tid för SNTP-klient*
- **nx_sntp_client_get_local_time_extended**: *Hämta lokal tid för SNTP-klient*
- **nx_sntp_client_initialize_broadcast**: *initiera klienten för IPv4-sändnings åtgärd*
- **nxd_sntp_client_initialize_broadcast**: *initiera klienten för IPv6-eller IPv4-sändnings åtgärd*
- **nx_sntp_client_initialize_unicast**: *initiera klienten för IPv4 unicast-åtgärd*
- **nxd_sntp_client_initialize_unicast**: *initiera klienten för IPv4-eller IPv6 unicast-åtgärd*
- **nx_sntp_client_receiving_udpates**: *klienten får för närvarande giltiga SNTP-uppdateringar*
- **nx_sntp_client_request_unicast_time**: *skicka en unicast-begäran direkt till NTP-servern*
- **nx_sntp_client_run_broadcast**: *Kör klienten i sändnings läge*
- **nx_sntp_client_run_unicast**: *Kör klienten i unicast-läge*
- **nx_sntp_client_set_local_time**: *Ange första lokala tid för SNTP-klienten*
- **nx_sntp_client_set_time_update_notify**: *Ange uppdaterings ÅTERanrop för SNTP*
- **nx_sntp_client_stop**: *stoppa klient tråden för SNTP*
- **nx_sntp_client_utility_display_date_and_time**: *Visa NTP-tid i sekunder*
- **nx_sntp_client_utility_msecs_to_fraction**: *konvertera millisekunder till en NTP-fraktion*
- **nx_sntp_client_utility_usecs_to_fraction**: *konvertera mikrosekunder till en NTP-fraktion*
- **nx_sntp_client_utility_fraction_to_usecs**: *konvertera en NTP-fraktion till mikrosekunder*


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

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en SNTP-klient instans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP

- **ip_ptr** Pekare till klientens IP-instans

- **iface_index** Index till SNTP-nätverks gränssnitt

- **packet_pool_ptr** Pekare till klient paketets pool

- **leap_second_handler** Motringning för program svar till ett förestående skottår-sekund

- **kiss_of_death_handler** Motringning för program svar för att ta emot kyss av döden-paket

- **random_number_generator** Motringning till slumpmässig nummer generator tjänst

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad klient

- **NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0XD2A) ogiltig inmatad icke-pekare

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

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

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en SNTP-klient instans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad klient

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar SNTP-klientens lokala tid med en option buffer-indata för att ta emot data i sträng meddelande format.

Den här tjänsten är föråldrad. Utvecklare uppmanas att migrera till *nx_sntp_client_get_local_time_extended*().

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP

- **sekunder** Pekare till lokal tid i sekunder

- **bråk** Lokal tids fraktions komponent

- **buffert** Pekare som buffrar för att skriva tids data

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad klient

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Hämta den utökade SNTP-klientens lokala tid

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den utökade SNTP-klientens lokala tid med en option buffer-indata för att ta emot data i sträng meddelande format.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP

- **sekunder** Pekare till lokal tid i sekunder

- **bråk** Pekare till bråk del

- **buffert** Pekare som buffrar för att skriva tids data

- **buffer_size** Buffertens längd

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad klient

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten

- NX_SIZE_ERROR (0x09) kontrol lera buffer_size inte

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Initiera klienten för sändnings åtgärd

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar klienten för sändning genom att ange IP-adressen för SNTP-servern och initiera start parametrarna för SNTP och timeout. Om båda multicast-och broadcast-adresserna inte är null väljs multicast-adressen. Om båda adresserna är null returneras ett fel. Observera att detta endast stöder IPv4-serveradresser.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP

- **multicast_server_address** Multicast-adress för SNTP

- **broadcast_time_server** Broadcast-adress för SNTP-server

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad klient

- **NX_INVALID_PARAMETERS** (0X4D) ogiltig inmatad icke-pekare

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåten från

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

Initiera klienten för IPv4-eller IPv6-broadcast-åtgärd

### <a name="prototype"></a>Prototyp

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar klienten för sändning genom att konfigurera IP-adressen för SNTP-servern och initiera start parametrarna för SNTP och timeout. Om både sändnings-och multicast-adress pekare är icke-null väljs multicast-adressen. Om båda adress pekarna är null returneras ett fel. Detta stöder både IPv4-och IPv6-adress typer. Observera att IPv6 inte stöder sändning, så att sändnings adress pekaren är inställd på IPv6, ett fel returneras.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP

- **multicast_server_address** Multicast-adress för SNTP-server

- **broadcast_server_address** Broadcast-adress för SNTP-server

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klienten har initierats

- NX_SNTP_PARAM_ERROR (0xD0D) ogiltig inmatad icke-pekare

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten


### <a name="allowed-from"></a>Tillåten från

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
### <a name="description"></a>Beskrivning

Den här tjänsten initierar klienten för unicast-åtgärd genom att ange IP-adressen för SNTP-servern och initiera start parametrar och tids gränser för SNTP. Observera att detta endast stöder IPv4-serveradresser.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP

- **unicast_time_server** IP-adress för SNTP-server

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klienten har initierats

- NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåten från

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

Konfigurera SNTP-klienten så att den körs i IPv4 eller IPv6 unicast

### <a name="prototype"></a>Prototyp

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar klienten för unicast-åtgärd genom att konfigurera IP-adressen för SNTP-servern och initiera start parametrarna för SNTP och timeout. Detta stöder både IPv4-och IPv6-adress typer.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP

- **unicast_time_server** IP-adress för SNTP-server

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klienten har initierats

- NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten anger om klienten tar emot giltiga SNTP-uppdateringar. Om den maximala tiden för fördröjning utan en giltig uppdatering eller gräns på efterföljande ogiltiga uppdateringar överskrids, returneras mottagar status som falskt. Observera att SNTP-klienten fortfarande körs och om programmet vill starta om SNTP-klienten med en annan unicast-eller broadcast/multicast-server måste den stoppa SNTP-klienten med hjälp av tjänsten *nx_sntp_client_stop* , initiera om klienten med hjälp av en av de initierande tjänsterna med en annan server.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP.

- **receive_status** Pekare till indikator om klienten får giltiga uppdateringar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klienten har tagit emot uppdaterings status

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Med den här tjänsten kan programmet direkt skicka en unicast-begäran till NTP-servern asynkront från klient tråds aktiviteten för SNTP. Alternativet wait anger hur lång tid det tar att vänta på ett svar. Om det lyckas kan programmet använda andra SNTP-klienttjänster för att hämta den senaste tiden. Se avsnittet **SNTP asynkrona unicast-begäranden** för mer information.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP.

- **Wait_option** Vänte alternativ för NTP-svar i timer-Tick.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klienten skickar och tar emot unicast-uppdatering

- **NX_SNTP_CLIENT_NOT_STARTED** (0XD0B) klient tråden har inte startats

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a>nx_sntp_client_run_broadcast

Kör klienten i sändnings läge

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar klienten i sändnings läge där den väntar på att få broadcasts från SNTP-servern. Om ett giltigt meddelande för broadcast-SNTP tas emot återställs klientens timeout-värde för SNTP-klienten för maximal fördröjning utan en uppdatering och antalet ogiltiga mottagna meddelanden som tagits emot återställs. Om någon av dessa gränser överskrids sätter SNTP-klienten Server statusen till ogiltig trots att den fortfarande väntar på att ta emot uppdateringar. Programmet kan avsöka SNTP-klientens aktivitet för Server status och om ogiltigt stoppa SNTP-klienten och initiera om den med en annan SNTP-sändnings adress. Den kan också växla till en unicast SNTP-server.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP.

### <a name="return-values"></a>Retur värden

- **status** --------faktisk slut för ande status

- **NX_SNTP_CLIENT_ALREADY_STARTED** -klienten (0xD0C) har redan startats

- **NX_SNTP_CLIENT_NOT_INITIALIZED** -klienten (0xD01) har inte initierats

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a>nx_sntp_client_run_unicast

Kör klienten i unicast-läge

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar klienten i unicast-läge där den regelbundet skickar en unicast-begäran till dess SNTP-server för en tids uppdatering. Om ett giltigt SNTP-meddelande tas emot återställs värdet för SNTP-klienten för maximal fördröjning utan en uppdatering, det inledande avsöknings intervallet och antalet felaktiga mottagna meddelanden som tas emot återställs. Om någon av dessa gränser överskrids sätter SNTP-klienten Server statusen till ogiltig trots att den fortfarande kommer att söka efter och vänta på att ta emot uppdateringar. Programmet kan avsöka SNTP-klientens aktivitet för Server status och om ogiltigt stoppa SNTP-klienten och initiera om den med en annan SNTP unicast-adress. Den kan också växla till en broadcast-SNTP-server.

.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) startade klienten i unicast-läge

- **NX_SNTP_CLIENT_ALREADY_STARTED** -klienten (0xD0C) har redan startats

- **NX_SNTP_CLIENT_NOT_INITIALIZED** -klienten (0xD01) har inte initierats

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten


### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten ställer in lokal tid för SNTP-klienten med ingångs tiden i SNTP-format, t. ex. sekunder och "bråk", vilket är formatet för att lägga bråk delar av en sekund i hexadecimalt format. Den är avsedd för att uppdatera SNTP-klientens lokala tid från en oberoende tids hållare, t. ex. en real tids klocka. SNTP-protokollet är avsett för uppdatering av SNTP-tid för att hålla lokal instämplingstid från "drivgarn". Uppdatering av SNTP-serverns tid kan vara, men är inte avsedd att vara den enda ingången till SNTP-klientens lokala tid om det inte finns någon oberoende tids behållare på program enheten.

Det här API: et kan också användas för att ge SNTP-klienten en grund tid innan du startar klient tråden för SNTP. Den lokala tiden för SNTP-klienten jämförs med mottagna uppdateringar för giltiga tids data. Den första gången mottagna uppdateringen kan ha stor avvikelse. Det finns därför ett alternativ för SNTP-klienten som ignorerar avvikelsen vid den första uppdateringen. På så sätt kan SNTP-klienten starta utan en bas tid. Indata-tid kan hämtas från kända epok tider (vanligt vis på Internet) och beräknas som antalet sekunder sedan 1 januari 1900 (tills 2036 när en ny "epok" kommer att startas.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP

- **sekunder** Sekunders komponent för tids indatamängden

- **bråk** Subseconds-komponent i SNTP-bråk formatet

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett lokal tid

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

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

Ange uppdaterings återanrop för SNTP

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a>Beskrivning

Den här tjänsten anger motringning för att meddela programmet när SNTP-klienten får en giltig tid uppdatering. Den tillhandahåller det faktiska SNTP-meddelandet och SNTP-klientens lokala tid (vanligt vis samma) i NTP-format. Programmet kan använda NTP-data direkt eller anropa *tjänsten nx_sntp_client_utility_display_date_time* för att konvertera tiden till läsligt format.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP

- **time_update_cb** Pekare till motringnings funktion

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett återanrop

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

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

Stoppa klient tråden för SNTP

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar klient tråden för SNTP. Klient tråds aktiviteterna i SNTP, som körs i en oändlig slinga, pausas vid varje iteration för att släppa kontrollen över SNTP-klientens tillstånd och tillåta att program gör API-anrop på SNTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient kontroll block för SNTP

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförde sluten klient tråd

- **NX_SNTP_CLIENT_NOT_STARTED** (0XDB) SNTP-klient tråd inte Startad

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a>nx_sntp_client_utility_display_date_time

Konvertera en NTP-tid till datum-och tids sträng

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a>Beskrivning

Tjänsten konverterar lokal tid för SNTP-klienten till ett datum format för en månad och returnerar datumet i den angivna bufferten. NX_SNTP_CURRENT_YEAR behöver inte vara samma år som den aktuella klient tiden, men det måste definieras.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr pekare till SNTP-klient**

- **buffert** Pekare till data lagrets datum

- **längd** Storlek på indatabufferten

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) konverteringen lyckades

- **NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR inte definierat eller så har ingen lokal klient tid etablerats

- **NX_SNTP_INVALID_DATETIME_BUFFER** (0XD07) otillräcklig buffert längd


### <a name="allowed-from"></a>Tillåten från

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

Konvertera millisekunder till en NTP-fraktion

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a>Beskrivning

Den här tjänsten konverterar indataportar i millisekunder till komponenten NTP-fraktion. Den är avsedd för användning med program som har en start bas tid för SNTP-klienten men inte i formatet NTP-sekunder/bråk. Antalet millisekunder måste vara mindre än 1000 för att ett giltigt bråk ska vara giltigt.

### <a name="input-parameters"></a>Indataparametrar

- **millisekunder i millisekunder som ska konverteras**

- **bråk** Pekare till millisekunder som omvandlats till bråk

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) konverteringen lyckades

- **NX_SNTP_OVERFLOW_ERROR** (0xD32) Det gick inte att konvertera tiden till ett datum

- NX_SNTP_INVALID_TIME (0xD30) ogiltig data inmatning för SNTP

### <a name="allowed-from"></a>Tillåten från

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

Omvandla mikrosekunder till en NTP-fraktion

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a>Beskrivning

Den här tjänsten konverterar de inmatade mikrosekunderna till NTP-fraktions komponenten. Den är avsedd för användning med program som har en start bas tid för SNTP-klienten men inte i formatet NTP-sekunder/bråk. Antalet mikrosekunder måste vara mindre än 1000000 för att ett giltigt bråk ska vara giltigt.

### <a name="input-parameters"></a>Indataparametrar

- **mikrosekunder** Mikrosekunder att konvertera

- **bråk** Pekare till mikrosekunder omvandlas till bråk

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) konverteringen lyckades

- **NX_SNTP_OVERFLOW_ERROR** (0xD32) Det gick inte att konvertera tiden till ett datum

- NX_SNTP_INVALID_TIME (0xD30) ogiltig data inmatning för SNTP

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a>nx_sntp_client_utility_fraction_to_usecs

Omvandla en NTP-fraktion till mikrosekunder

### <a name="prototype"></a>Prototyp

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a>Beskrivning

Den här tjänsten konverterar den inmatade NTP-delen till mikrosekunder.

### <a name="input-parameters"></a>Indataparametrar

- **bråk bråk att konvertera**

- **mikrosekunder** Pekare till bråk som omvandlats till mikrosekunder

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) konverteringen lyckades

- NX_SNTP_INVALID_TIME (0xD30) ogiltig data inmatning för SNTP

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```