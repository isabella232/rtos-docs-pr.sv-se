---
title: Kapitel 4 – Beskrivning av NAT-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NETX Duo NAT API-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dbe2cb25607162b62b048251927bdc7671c5884d2a3b45b6b24bae539e08d24a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797303"
---
# <a name="chapter-4---description-of-nat-services"></a>Kapitel 4 – Beskrivning av NAT-tjänster

Det här kapitlet innehåller en beskrivning av alla NETX Duo NAT API-tjänster (anges nedan) i alfabetisk ordning.

> [!NOTE]
> I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **FETSTIL** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

## <a name="nx_nat_create"></a>nx_nat_create

Skapa en NAT-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en instans av NAT-servern.

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans att skapa
- **ip_ptr pekare till** IP-instans
- **global_interface_index** Indexera till det globala nätverksgränssnittet
- **dynamic_cache_memory** Pekar minnesområde till NAT-tabell
- **dynamic_cache_size** Storlek på minnesområdet för NAT-tabell

### <a name="return-values"></a>Returvärden

- **NAT-servern** NX_SUCCESS (0x00) har skapats
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter
- NX_NAT_PARAM_ERROR (0xD01) Ogiltiga icke-pekarindata
- NX_NAT_CACHE_ERROR (0xD02) Ogiltig cache-pekare

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
#define NX_NAT_ENTRY_CACHE_SIZE 20480

static UCHAR nat_cache[NX_NAT_ENTRY_CACHE_SIZE];
UINT global_interface_index = 0;

/* Create a NAT Server and cache with a global interface index. */
status = nx_nat_create(nat_ptr, ip_ptr, global_interface_index,
    nat_cache, NX_NAT_ENTRY_CACHE_SIZE);

/* If status = NX_SUCCESS, the NAT instance was successfully
    created. */
```

## <a name="nx_nat_delete"></a>nx_nat_delete

Ta bort en NAT-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_nat_delete(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en NAT-server som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans att ta bort

### <a name="return-values"></a>Returvärden

- **nat NX_SUCCESS** (0x00) har tagits bort
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a>nx_nat_enable

Aktivera IP-instansen för NAT

### <a name="prototype"></a>Prototyp

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar IP-instansen för NAT (t.ex. vidarebefordra mottagna paket till NAT-servern).

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans

### <a name="return-values"></a>Returvärden

- **NAT NX_SUCCESS** (0x00) har aktiverats
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a>nx_nat_disable

Inaktivera IP-instansen för NAT

### <a name="prototype"></a>Prototyp

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar NAT på IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans

### <a name="return-values"></a>Returvärden

- **NAT NX_SUCCESS** (0x00) har inaktiverats
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a>nx_nat_cache_notify_set

Ange en fullständig återanropsfunktion för att meddela cachen

### <a name="prototype"></a>Prototyp

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a>Description

Den här tjänsten registrerar cachens fullständiga återanrop med indatafunktionens pekare cache_full_notify_cb pekar på en användardefinierad full notify-funktion för cachen.

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans
- **cache_full_notify_cb** Pekare till cachelagra fullständig avvisningsfunktion

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Funktionen Cache full notify har angetts
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter
- NX_NAT_PARAM_ERROR (0xD01) Ogiltiga icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a>nx_nat_inbound_entry_create

Skapa en inkommande post i NAT-översättningstabellen

### <a name="prototype"></a>Prototyp

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a>Description

Den här tjänsten skapar en inkommande post som statisk (permanent post, upphör aldrig att gälla) och lägger till den i NAT-översättningstabellen. De här posterna skapas vanligtvis för lokala värdservrar där en anslutning initieras från en värd i det externa nätverket. NAT-servern kontrollerar att den externa porten inte redan används i översättningstabellen eller är bunden av en tidigare NetX Duo-socket för samma protokoll.

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans
- **entry_ptr** Pekare till översättningspost
- **local_ip_address** Lokal värd-IP-adress
- **external_port** Målport i det externa nätverket
- **local_port** Källport (lokal värd)
- **protokoll** Paketprotokoll (t.ex. TCP)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** -post (0x00) har skapats
- **NX_NAT_PORT_UNAVAILABLE** (0xD0D) Ogiltig extern port
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter
- NX_NAT_PARAM_ERROR (0xD01) Ogiltiga icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a>nx_nat_inbound_entry_delete

Ta bort en inkommande post i NAT-översättningstabellen

### <a name="prototype"></a>Prototyp

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a>Description

Den här tjänsten tar bort den angivna inkommande posten från översättningstabellen.

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans
- **delete_entry_ptr** Pekare till NAT-översättningsposten

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** -post (0x00) har tagits bort
- **NX_NAT_ENTRY_NOT_FOUND** (0xD04) Hittades inte
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter
- NX_NAT_ENTRY_TYPE_ERROR (0xD0C) Ogiltig översättningstyp

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
