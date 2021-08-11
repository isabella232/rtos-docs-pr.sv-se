---
title: Kapitel 3 – Beskrivning Azure RTOS NetX Duo PTP Client Services
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo PTP-klienttjänster i alfabetisk ordning.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 686db68181e3712f9f6a09a9f471626eff610fd7f45ec5b83ba56f8b7aa378cc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798018"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a>Kapitel 3 – Beskrivning Azure RTOS NetX Duo PTP Client Services

Det här kapitlet innehåller en beskrivning av alla NetX Duo PTP-klienttjänster (visas nedan) i alfabetisk ordning.

[!NOTE]
> *I avsnittet **Returvärden** i följande API-funktionsbeskrivningar påverkas inte värden i **BOLD** av **NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.*

## <a name="nx_ptp_client_create"></a>nx_ptp_client_create

Skapa en PTP-klientinstans.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a>Description

Den här tjänsten skapar en instans av PTP-klienten.

Observera att programmet först måste skapa en IP-instans och en paketpool för att PTP-klienten ska kunna överföra paket. För paketpoolen kan programmet använda samma paketpool i IP-instansen. eller så kan den skapa en dedikerad paketpool för PTP-klienten.  Metoden med dedikerade paketpooler har fördelen att du använder små paket (128 byte-paket om IPv6 används eller 108 byte för endast IPv4).

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klienten som ska skapas
* **ip_ptr** Pekare till IP-instans
* **interface_index** Index för PTP-nätverksgränssnitt
* **packet_pool_ptr** Pekare till klientpaketpool
* **thread_priority**  Prioritet för PTP-tråd
* **thread_stack** Pekare till trådstack
* **stack_size** Storleken på trådstacken
* **clock_callback** Motringning av PTP-klockan
* **clock_callback_data** Data för klockanrop

### <a name="return-values"></a>Returvärden
* **NX_SUCCESS** -klienten (0x00) har skapats
* **NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) Paketnyttolasten är för liten
* **NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) Fel vid klockanrop
* **status** Status slutförande av NetX Duo- och ThreadX-tjänstanrop
* NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter
* NX_INVALID_INTERFACE (0x4C) Ogiltigt gränssnitt

### <a name="allowed-from"></a>Tillåts från
Trådar

### <a name="example"></a>Exempel
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a>nx_ptp_client_delete

Tar bort en PTP-klientinstans.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en instans av PTP-klienten.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klient som ska tas bort

### <a name="return-values"></a>Returvärden
* **NX_SUCCESS** (0x00) Klienten har tagits bort
* NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från
Trådar

### <a name="example"></a>Exempel
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a>nx_ptp_client_master_info_get

Hämta information om huvudklockan.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a>Description
Den här tjänsten hämtar information om huvudklockan. Huvudkontrollblocket skickas till användarprogrammet via funktionen för återanrop av händelser.

### <a name="input-parameters"></a>Indataparametrar
* **master_ptr** Pekare till PTP-huvudklocka
* **adress** Adress för huvudklockan
* **port_identity** PTP-huvudport och -identitet
* **port_identity_length** Längden på PTP-huvudport och identitet
* **priority1** Priority1 för PTP-huvudklockan
* **priority2** Priority2 för PTP-huvudklockan
* **clock_class** Klass av PTP-huvudklocka
* **clock_accuracy** Noggrannhet för PTP-huvudklockan
* **clock_variance** Varians för PTP-huvudklocka
* **grandmaster_identity** Grandmaster-klockans identitet
* **grandmaster_identity_length** Längden på grandmaster Identity
* **steps_removed** Steg som tagits bort från PTP-huvudet
* **time_source** Källan för timern som används av Grandmaster Clock

### <a name="return-values"></a>Returvärden
* **NX_SUCCESS** (0x00) Hämta information om huvudklockan
* NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från
Trådar

### <a name="example"></a>Exempel
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a>nx_ptp_client_packet_timestamp_notify

Meddela PTP-klienten tidsstämpeln för paketet.

### <a name="prototype"></a>Prototyp

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a>Description
Den här tjänsten meddelar PTP-klienten att paketet överförs med tidsstämpeln. Den här tjänsten är utformad för nätverksdrivrutiner och anropas när paketet överförs. Tidsstämpeln genereras vanligtvis av maskinvaran.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klienten som ska skapas
* **packet_ptr** Pekare till PTP-paket som överförs
* **timestamp_ptr** Pekare till tidsstämpel för PTP-paket

### <a name="return-values"></a>Returvärden
Ingen

### <a name="allowed-from"></a>Tillåts från
Trådar

### <a name="example"></a>Exempel
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a>nx_ptp_client_soft_clock_callback

Programvaruimplementering av en PTP-klocka.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a>Description
Den här återanropsfunktionen fungerar som en simulerad klockkälla med låg upplösning för PTP. Den här rutinen tillhandahålls som referens och kan inte användas för produktion.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klienten som ska skapas
* **åtgärd** Återanropsåtgärd, giltiga värden definieras som:
  * **NX_PTP_CLIENT_CLOCK_INIT** Initiera klockan.
  * **NX_PTP_CLIENT_CLOCK_SET** Ange den aktuella tidsstämpeln som anges av `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_GET** Returnera den aktuella tidsstämpeln till `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extrahera tidsstämpeln `packet_ptr` från till `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_ADJUST** Justera den aktuella tidsstämpeln mindre än *1* sekund.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Markera som `packet_ptr` kräver för att meddela PTP-klienten tidsstämpeln när den skickas.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Uppdatera mjuk timer. Det kan ignoreras av maskinvaruklockan.
* **time_ptr** Pekare till tidsstämpel.
* **packet_ptr** Pekare till paket.
* **callback_data** Pekare till täckande återanropsdata.

### <a name="return-values"></a>Returvärden
* **NX_SUCCESS** -åtgärd (0x00)
* **NX_PTP_PARAM_ERROR** (0xD03) Ogiltig parameter

### <a name="allowed-from"></a>Tillåts från
INTERN PTP

### <a name="example"></a>Exempel
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a>nx_ptp_client_start

Starta PTP-klienten.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a>Description
Den här tjänsten startar en PTP-klientinstans som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klienten som ska skapas
* **client_port_identity_ptr** Pekare till klientport och identitet, det kan vara NULL
* **client_port_identity_length** Längden på klientport och identitet. Det måste vara 0 om client_port_identity_ptr är NULL eller NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)
* **domän** PTP-klockdomän
* **transport_specific** 4 bitar transportspecifik
* **event_callback** Återanropsfunktionen anropas vid händelse
* **event_callback_data** Data för återanrop av händelser

### <a name="return-values"></a>Returvärden
* **NX_SUCCESS** (0x00) har startats
* **ptp NX_PTP_CLIENT_ALREADY_STARTED klienten** (0xD02) har redan startats
* **status** Status för slutförande av NetX Duo- och ThreadX-tjänstanrop
* NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från
Trådar

### <a name="example"></a>Exempel
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a>nx_ptp_client_stop

Stoppa PTP-klienten.  När PTP-klienten har stoppats bearbetar den inte PTP-paket och skickar heller inte PTP-paket.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description
Den här tjänsten stoppar en tidigare skapad och startad PTP-klientinstans.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klienten som ska stoppas

### <a name="return-values"></a>Returvärden
* **NX_SUCCESS** (0x00) Klienten har stoppats
* **NX_PTP_CLIENT_NOT_STARTED** (0xD01) Klienten har inte startats
* NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från
Trådar

### <a name="example"></a>Exempel
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a>nx_ptp_client_sync_info_get

Hämta synkroniseringsinformation.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a>Description
Den här tjänsten hämtar information om synkroniseringsmeddelandet. Kontrollblocket Sync skickas till användarprogrammet via funktionen för återanrop av händelser.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klienten som ska skapas
* **flaggor** Flaggor i synkroniseringsmeddelande
* **utc_offset** Offset mellan TAI och UTC

### <a name="return-values"></a>Returvärden
* **NX_SUCCESS** (0x00) Hämta synkroniseringsinformation
* NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från
Trådar

### <a name="example"></a>Exempel
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a>nx_ptp_client_time_get

Hämta aktuell tid.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Description
Den här tjänsten hämtar PTP-klockans aktuella värde. Den är tillgänglig oavsett om PTP-klienten har synkroniserats med huvudklockan eller inte.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klienten som ska skapas
* **time_ptr** Pekare till PTP-tid

### <a name="return-values"></a>Returvärden
* **NX_SUCCESS** -klienten (0x00) har skapats
* NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från
Trådar

### <a name="example"></a>Exempel
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a>nx_ptp_client_time_set

Ange aktuell tid.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Description
Den här tjänsten anger ptp-klockans aktuella värde. Den måste anropas innan PTP-klienten startar.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klienten som ska skapas
* **time_ptr** Pekare till PTP-tid

### <a name="return-values"></a>Returvärden
* **NX_SUCCESS** -klienten (0x00) har skapats
* **ptp NX_PTP_CLIENT_ALREADY_STARTED klienten** (0xD02) har redan startats
* NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från
Trådar

### <a name="example"></a>Exempel
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a>nx_ptp_client_utility_convert_time_to_date

Konvertera PTP-tid till datum och tid för UTC.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a>Description
Den här tjänsten konverterar PTP-tid till datum och tid för UTC.

### <a name="input-parameters"></a>Indataparametrar
* **time_ptr** Pekare till PTP-tid
* **offset** Signerad andra förskjutning för att lägga till PTP-tid
* **date_time_ptr** Pekare till resulterande datum

### <a name="return-values"></a>Returvärden
* **NX_SUCCESS** (0x00) Klienten har skapats
* **Pekare till resulterande datum** (0xD03) Ogiltig indataparameter
* NX_PTR_ERROR (0x07) Ogiltig indata pekarparameter

### <a name="allowed-from"></a>Tillåts från
Trådar

### <a name="example"></a>Exempel
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a>nx_ptp_client_utility_time_diff

Diffa två PTP-gånger.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a>Description
Den här tjänsten beräknar skillnaden mellan två PTP-tider.

### <a name="input-parameters"></a>Indataparametrar
* **time1_ptr** Pekare till första PTP-tid
* **time2_ptr** Pekare till andra PTP-tid
* **result_ptr** Pekare till resultatet time1-time2

### <a name="return-values"></a>Returvärden
* **NX_SUCCESS** (0x00) Klienten har skapats
* NX_PTR_ERROR (0x07) Ogiltig indata pekarparameter

### <a name="allowed-from"></a>Tillåts från
Trådar

### <a name="example"></a>Exempel
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```