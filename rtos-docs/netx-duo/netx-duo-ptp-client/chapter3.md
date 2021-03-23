---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo PTP Client Services
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo PTP-klienttjänster i alfabetisk ordning.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b4cdeca81c157934e35a219cd5535ec38f2c0746
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825803"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo PTP Client Services

Det här kapitlet innehåller en beskrivning av alla NetX Duo PTP-klienttjänster (visas nedan) i alfabetisk ordning.

[!NOTE]
> *I avsnittet **returnera värden** i följande beskrivningar av API-funktioner påverkas inte värdena i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.*

## <a name="nx_ptp_client_create"></a>nx_ptp_client_create

Skapa en PTP-klient instans.

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

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en instans av PTP-klienten.

Observera att programmet först måste skapa en IP-instans och en modempool för att PTP-klienten ska kunna överföra paket. För Packet-poolen kan programmet använda samma adresspool i IP-instansen. eller så kan den skapa en dedikerad modempool för PTP-klienten.  Den dedikerade lagringspoolen har fördelen med att använda små paket (128 byte-paket om IPv6 används eller 108 byte för endast IPv4).

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klient för att skapa
* **ip_ptr** Pekare till IP-instans
* **interface_index** Index för PTP-nätverks gränssnitt
* **packet_pool_ptr** Pekare till klient paketets pool
* **thread_priority**  Prioritet för PTP-tråd
* **thread_stack** Pekare till tråds tack
* **stack_size** Storlek på tråds tack
* **clock_callback** Motanrop för PTP-klocka
* **clock_callback_data** Data för klock anrop

### <a name="return-values"></a>Retur värden
* **NX_SUCCESS** (0x00)-klienten har skapats
* **NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** paketets nytto Last är för kort (0xD04)
* **NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) Det gick inte att återanrop
* **status** Status för slut för ande av NetX Duo-och ThreadX service-anrop
* NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare
* NX_INVALID_INTERFACE (0x4C) ogiltigt gränssnitt

### <a name="allowed-from"></a>Tillåten från
Konversation

### <a name="example"></a>Exempel
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a>nx_ptp_client_delete

Tar bort en PTP-klient instans.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en instans av PTP-klienten.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klient att ta bort

### <a name="return-values"></a>Retur värden
* **NX_SUCCESS** (0X00) klienten har tagits bort
* NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från
Konversation

### <a name="example"></a>Exempel
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a>nx_ptp_client_master_info_get

Hämta information om huvud klock klocka.

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

### <a name="description"></a>Beskrivning
Den här tjänsten hämtar information om huvud klockan. Master Control-blocket skickas till användar programmet via funktionen motringning av händelse.

### <a name="input-parameters"></a>Indataparametrar
* **master_ptr** Pekare till PTP-huvudklocka
* **adress** Adress till huvud klockan
* **port_identity** PTP-huvudport och identitet
* **port_identity_length** Längd på PTP-huvudporten och identiteten
* **priority1** Priority1 of PTP Master Clock
* **priority2** Priority2 of PTP Master Clock
* **clock_class** Klass för PTP-huvudklocka
* **clock_accuracy** Noggrannhet hos PTP-huvudklocka
* **clock_variance** Varians hos PTP-huvudklocka
* **grandmaster_identity** Identitet för Grandmaster-klocka
* **grandmaster_identity_length** Längd på Grandmaster-identitet
* **steps_removed** Steg borttagna från PTP-huvudet
* **time_source** Källan för timern som används av Grandmaster-klockan

### <a name="return-values"></a>Retur värden
* **NX_SUCCESS** (0X00) Hämta huvud klock information
* NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från
Konversation

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

Meddela PTP-klientens tidsstämpel för paketet.

### <a name="prototype"></a>Prototyp

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a>Beskrivning
Den här tjänsten meddelar PTP-klienten att paketet överförs med tidsstämpel. Den här tjänsten är avsedd för nätverks driv rutin och anropas när paketet överförs. Tidsstämpeln skapas vanligt vis av maskin vara.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klient för att skapa
* **packet_ptr** Pekare till PTP-paket som överförs
* **timestamp_ptr** Pekare till tidsstämpel för PTP-paket

### <a name="return-values"></a>Retur värden
Inget

### <a name="allowed-from"></a>Tillåten från
Konversation

### <a name="example"></a>Exempel
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a>nx_ptp_client_soft_clock_callback

Program varu implementering av en PTP-klocka.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a>Beskrivning
Denna motringning fungerar som en simulerad låg upplöst klock källa för PTP. Den här rutinen tillhandahålls som en referens och kan inte användas för produktion.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klient för att skapa
* **åtgärd** Återanrops åtgärd, giltiga värden definieras som:
  * **NX_PTP_CLIENT_CLOCK_INIT** Initiera klockan.
  * **NX_PTP_CLIENT_CLOCK_SET** Ange aktuell tidsstämpel som anges av `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_GET** Returnera aktuell tidstämpel till `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extrahera tidsstämpel från `packet_ptr` till `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_ADJUST** Justera den aktuella tidsstämpeln på mindre än *en* sekund.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Markera det `packet_ptr` som krävs för att meddela PTP-klienten tidsstämpeln när den överförs.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Uppdatera mjuk timer. Den kan ignoreras av maskin varu klockan.
* **time_ptr** Pekare till tidsstämpel.
* **packet_ptr** Pekar mot paket.
* **callback_data** Pekare mot täckande återanrops data.

### <a name="return-values"></a>Retur värden
* **NX_SUCCESS** (0x00) har åtgärd ATS
* **NX_PTP_PARAM_ERROR** (0XD03) ogiltig parameter

### <a name="allowed-from"></a>Tillåten från
PTP, intern

### <a name="example"></a>Exempel
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a>nx_ptp_client_start

Starta PTP-klient.

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

### <a name="description"></a>Beskrivning
Den här tjänsten startar en tidigare skapad PTP-klient instans.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klient för att skapa
* **client_port_identity_ptr** Pekare till klient port och identitet, den kan vara NULL
* **client_port_identity_length** Längden på klient porten och identiteten. Värdet måste vara 0 om client_port_identity_ptr är NULL eller NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)
* **domän** PTP-klockans domän
* **transport_specific** 4 bitar av transporten är speciell
* **event_callback** Callback-funktionen har anropats för händelsen
* **event_callback_data** Data för händelse återanrop

### <a name="return-values"></a>Retur värden
* **NX_SUCCESS** (0X00) klienten har startats
* **NX_PTP_CLIENT_ALREADY_STARTED** (0XD02) PTP-klienten har redan startats
* **status** Status för slut för ande av NetX Duo-och ThreadX service-anrop
* NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från
Konversation

### <a name="example"></a>Exempel
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a>nx_ptp_client_stop

Stoppa PTP-klienten.  När PTP-klienten har stoppats bearbetar den inte PTP-paket eller överför PTP-paket.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning
Den här tjänsten stoppar en tidigare skapad och startad PTP-klient instans.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klient för att stoppa

### <a name="return-values"></a>Retur värden
* **NX_SUCCESS** (0X00) klienten har stoppats
* **NX_PTP_CLIENT_NOT_STARTED** -klienten (0xD01) har inte startats
* NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från
Konversation

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

### <a name="description"></a>Beskrivning
Den här tjänsten hämtar information om Sync-meddelande. Kontroll blocket för synkronisering skickas till användar programmet via funktionen motringning av händelse.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klient för att skapa
* **flaggor** Flaggor i Sync-meddelande
* **utc_offset** Förskjutning mellan TAI och UTC

### <a name="return-values"></a>Retur värden
* **NX_SUCCESS** (0X00) Hämta synkroniseringsinformation
* NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från
Konversation

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

### <a name="description"></a>Beskrivning
Den här tjänsten hämtar den aktuella värdet för PTP-klockan. Den finns tillgänglig oavsett om PTP-klienten är synkroniserad med huvud klockan eller inte.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klient för att skapa
* **time_ptr** Pekare till PTP-tid

### <a name="return-values"></a>Retur värden
* **NX_SUCCESS** (0x00)-klienten har skapats
* NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från
Konversation

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

### <a name="description"></a>Beskrivning
Den här tjänsten anger den aktuella värdet för PTP-klockan. Den måste anropas innan PTP-klienten startar.

### <a name="input-parameters"></a>Indataparametrar
* **client_ptr** Pekare till PTP-klient för att skapa
* **time_ptr** Pekare till PTP-tid

### <a name="return-values"></a>Retur värden
* **NX_SUCCESS** (0x00)-klienten har skapats
* **NX_PTP_CLIENT_ALREADY_STARTED** (0XD02) PTP-klienten har redan startats
* NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från
Konversation

### <a name="example"></a>Exempel
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a>nx_ptp_client_utility_convert_time_to_date

Konvertera PTP-tid till UTC-datum och tid.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a>Beskrivning
Den här tjänsten konverterar PTP-tid till UTC-datum och tid.

### <a name="input-parameters"></a>Indataparametrar
* **time_ptr** Pekare till PTP-tid
* **förskjutning** Signerad andra förskjutning för att lägga till PTP-tid
* **date_time_ptr** Pekare till resultat datum

### <a name="return-values"></a>Retur värden
* **NX_SUCCESS** (0x00)-klienten har skapats
* **Pekare till resulterande datum** (0XD03) ogiltig indataparameter
* NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från
Konversation

### <a name="example"></a>Exempel
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a>nx_ptp_client_utility_time_diff

Skilj två PTP-tider.

### <a name="prototype"></a>Prototyp

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a>Beskrivning
Den här tjänsten beräknar skillnaden mellan två PTP-tider.

### <a name="input-parameters"></a>Indataparametrar
* **time1_ptr** Pekare till första PTP-tid
* **time2_ptr** Pekare till andra PTP-tid
* **result_ptr** Pekare till resultat time1 – Time2

### <a name="return-values"></a>Retur värden
* **NX_SUCCESS** (0x00)-klienten har skapats
* NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från
Konversation

### <a name="example"></a>Exempel
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```