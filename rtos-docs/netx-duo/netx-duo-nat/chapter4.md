---
title: Kapitel 4 – Beskrivning av NAT-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo NAT API-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8bdbdfcb2da6425fb99cadc7b2f6815dedc12953
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825851"
---
# <a name="chapter-4---description-of-nat-services"></a>Kapitel 4 – Beskrivning av NAT-tjänster

Det här kapitlet innehåller en beskrivning av alla NetX Duo NAT API-tjänster (visas nedan) i alfabetisk ordning.

> [!NOTE]
> I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

## <a name="nx_nat_create"></a>nx_nat_create

Skapa en NAT-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en instans av NAT-servern.

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans som ska skapas
- **Ip_ptr pekare** till IP-instans
- **global_interface_index** Index till det globala nätverks gränssnittet
- **dynamic_cache_memory** Pekarens minnes yta i NAT-tabellen
- **dynamic_cache_size** Storlek på minnes området för NAT-tabell

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) NAT-servern har skapats
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare
- NX_NAT_PARAM_ERROR (0xD01) ogiltig inmatad icke-pekare
- NX_NAT_CACHE_ERROR (0xD02) ogiltig Indatatyp för cache pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

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

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad NAT-server.

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans som ska tas bort

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) NAT har tagits bort
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

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

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar IP-instansen för NAT (t. ex. vidarebefordrade paket till NAT-servern).

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) NAT har Aktiver ATS
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

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

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar NAT på IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) NAT har inaktiverats
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

### <a name="example"></a>Exempel

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a>nx_nat_cache_notify_set

Ange en cache fullständig notify motringnings funktion

### <a name="prototype"></a>Prototyp

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar cachen med fullständig motringning med indata-funktionen pekare cache_full_notify_cb som pekar på en användardefinierad cache fullständig meddelande funktion.

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans
- **cache_full_notify_cb** Pekare för att cachelagra fullständig Avisera-funktion

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) cache fullständig aviserings funktion har angetts
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare
- NX_NAT_PARAM_ERROR (0xD01) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

### <a name="example"></a>Exempel

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a>nx_nat_inbound_entry_create

Skapa en inkommande post i översättnings tabellen för NAT

### <a name="prototype"></a>Prototyp

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en inkommande post som statisk (permanent post, upphör aldrig att gälla) och lägger till den i översättnings tabellen NAT. Dessa poster skapas vanligt vis för lokala värd servrar där en anslutning initieras från en värd i nätverket utanför nätverket. NAT-servern kontrollerar att den externa porten inte redan används i översättnings tabellen eller bundits av en tidigare befintlig NetX Duo-socket av samma protokoll.

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans
- **entry_ptr** Pekare till översättnings post
- **local_ip_address** IP-adress för lokal värd
- **external_port** Mål port på det externa nätverket
- **local_port** Käll port (lokal värd)
- **protokoll** Paket protokoll (t. ex. TCP)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) har skapats
- **NX_NAT_PORT_UNAVAILABLE** (0XD0D) ogiltig extern port
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare
- NX_NAT_PARAM_ERROR (0xD01) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

### <a name="example"></a>Exempel

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a>nx_nat_inbound_entry_delete

Ta bort en inkommande post i översättnings tabellen för NAT

### <a name="prototype"></a>Prototyp

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna inkommande posten från översättnings tabellen.

### <a name="input-parameters"></a>Indataparametrar

- **nat_ptr** Pekare till NAT-instans
- **delete_entry_ptr** Pekare till översättnings posten NAT

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) har tagits bort
- Det gick inte att hitta **NX_NAT_ENTRY_NOT_FOUND** (0xD04)-posten
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare
- NX_NAT_ENTRY_TYPE_ERROR (0xD0C) ogiltig översättnings typ

### <a name="allowed-from"></a>Tillåten från

Program kod

### <a name="example"></a>Exempel

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
