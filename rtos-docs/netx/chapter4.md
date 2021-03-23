---
title: Kapitel 4 – Beskrivning av Azure återställnings tider NetX-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 720e573b53070a754618830134f63a8421b9fd29
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825641"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a>Kapitel 4 – Beskrivning av Azure återställnings tider NetX-tjänster

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX-tjänster i alfabetisk ordning. Tjänst namn är utformade så att alla liknande tjänster grupperas tillsammans. Till exempel finns alla ARP-tjänster i början av det här kapitlet.

> [!NOTE]
> *Observera att det finns en BSD-Compatible socket-API för äldre program kod som inte kan dra full nytta av NetX-API: et med höga prestanda. Se bilaga D för mer information om API: et för BSD-Compatible socket.*

I avsnittet "returnera värden" i varje beskrivning påverkas inte värden i **fetstil** av NX_DISABLE_ERROR_CHECKING alternativ som används för att inaktivera API-felkontrollen, medan värden i icke-fetstil är helt inaktiverade. I avsnitten "tillåten från" anges från vilka varje NetX-tjänst kan anropas.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

Ogiltig förklara alla dynamiska poster i ARP-cachen

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

I den här tjänsten inaktive ras alla dynamiska ARP-poster i ARP-cachen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförde ARP-cachen.
- **NX_NOT_ENABLED** (0X14) ARP har inte Aktiver ATS.
- **NX_PTR_ERROR** (0X07) ogiltig IP-adress.
- **NX_CALLER_ERROR** (0X11) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find nx_arp_info_get,
- nx_arp_ip_address_find nx_arp_static_entries_delete,
- nx_arp_static_entry_create nx_arp_static_entry_delete

## <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

Ange dynamisk ARP-post

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Beskrivning

Den här tjänsten allokerar en dynamisk post från ARP-cachen och ställer in den angivna IP-adressen till fysisk adress mappning. Om en fysisk adress på noll anges skickas en faktisk ARP-begäran till nätverket för att den fysiska adressen ska kunna matchas. Observera också att den här posten tas bort om ARP-åldrande är aktiv eller om ARP-cachen är slut och det här är den minst nyligen använda ARP-posten.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **ip_address** IP-adress att mappa.
- **physical_msw** De 16 främsta bitarna (47-32) av den fysiska adressen.
- **physical_lsw** Lägre 32 bitar (31-0) av den fysiska adressen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) en dynamisk ARP-post uppsättning.
- **NX_NO_MORE_ENTRIES** (0X17) inga fler ARP-poster är tillgängliga i ARP-cachen.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.
- **NX_PTR_ERROR** (0X07) ogiltig IP-instans pekare.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entries_invalidate nx_arp_enable,
- nx_arp_gratuitous_send nx_arp_hardware_address_find,
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create nx_arp_static_entry_delete

## <a name="nx_arp_enable"></a>nx_arp_enable

Aktiverar adress matchnings protokoll (ARP).

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar ARP-komponenten i NetX för den angivna IP-instansen. ARP-initieringen innefattar konfiguration av ARP-cachen och olika ARP-bearbetnings rutiner som krävs för att skicka och ta emot ARP-meddelanden.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **arp_cache_memory** Pekare till minnes området för att placera ARP-cache.
- **arp_cache_size** Varje ARP-post är 52 byte, det totala antalet ARP-poster är därför att storleken dividerat med 52.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförde ARP-aktivering.
- **NX_PTR_ERROR** (0X07) ogiltig IP eller minnes pekare för cache.
- **NX_SIZE_ERROR** (0x09) den TILLHANDAHÅLLna ARP-cache-minnet är för litet.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_ALREADY_ENABLED** (0X15) den här komponenten har redan Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,
- nx_arp_gratuitous_send nx_arp_hardware_address_find,
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create nx_arp_static_entry_delete

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

Skicka en kostnads fria ARP-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Beskrivning

Den här tjänsten går igenom alla fysiska gränssnitt för att överföra AntiArp-begäranden så länge som gränssnittets IP-adress är giltig. Om ett ARP-svar sedan tas emot, anropas den tillhandahållna svars hanteraren för att bearbeta svaret till den kostnads fria ARP-filen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **response_handler** Pekare till funktionen för svars hantering. Om NX_NULL anges ignoreras svaren.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad överföring av kostnads fria ARP.
- **NX_NO_PACKET** (0X01) inget paket tillgängligt.
- **NX_NOT_ENABLED** (0X14) ARP har inte Aktiver ATS.
- Den aktuella IP-adressen för **NX_IP_ADDRESS_ERROR** (0x21) är ogiltig.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find nx_arp_static_entries_delete,
- nx_arp_static_entry_create nx_arp_static_entry_delete

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

Hitta en fysisk maskin varu adress med en IP-adress

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker hitta en fysisk maskin varu adress i ARP-cachen som är associerad med den angivna IP-adressen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **ip_address** IP-adress att söka efter.
- **physical_msw** Pekare till variabeln för att returnera de översta 16 bitarna (47-32) av den fysiska adressen.
- **physical_lsw** Pekare till variabeln för att returnera de lägre 32 bitarna (31-0) för den fysiska adressen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad ARP-maskinvara Sök.
- Det gick inte att hitta **NX_ENTRY_NOT_FOUND** -mappningen (0x16) i ARP-cachen.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.
- **NX_PTR_ERROR** (0X07) ogiltig IP-eller minnes pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,
- nx_arp_ip_address_find nx_arp_static_entries_delete,
- nx_arp_static_entry_create nx_arp_static_entry_delete

## <a name="nx_arp_info_get"></a>nx_arp_info_get

Hämta information om ARP-aktiviteter

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om ARP-aktiviteter för den associerade IP-instansen.

*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **arp_requests_sent** Pekare till målet för de totala ARP-begäranden som skickats från den här IP-instansen.
- **arp_requests_received** Pekare till målet för de totala ARP-begäranden som tagits emot från nätverket.
- **arp_responses_sent** Pekare till målet för det totala antalet ARP-svar som skickas från den här IP-instansen.
- **arp_responses_received** Pekar till målet för det totala antalet ARP-svar som tagits emot från nätverket.
- **arp_dynamic_entries** Pekar mot målet för det aktuella antalet dynamiska ARP-poster.
- **arp_static_entries** Pekar mot målet för det aktuella antalet statiska ARP-poster.
- **arp_aged_entries** Pekar till målet för det totala antalet ARP-poster som har föråldrats och blivit ogiltiga.
- **arp_invalid_messages** Pekar till målet för de totala ogiltiga ARP-meddelanden som tagits emot.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades Hämta ARP-information.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
    &arp_requests_received,
    &arp_responses_sent,
    &arp_responses_received,
    &arp_dynamic_entries,
    &arp_static_entries,
    &arp_aged_entries,
    &arp_invalid_messages);
/* If status is NX_SUCCESS, the ARP information has been stored in
    the supplied variables. */
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,
- nx_arp_enable nx_arp_gratuitous_send,
- nx_arp_hardware_address_find nx_arp_ip_address_find,
- nx_arp_static_entries_delete nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

Hitta IP-adress till en fysisk adress

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker hitta en IP-adress i ARP-cachen som är associerad med den angivna fysiska adressen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **ip_address** Pekare för att returnera IP-adress, om en sådan finns, som har mappats.
- **physical_msw** De 16 främsta bitarna (47-32) i den fysiska adressen som du vill söka efter.
- **physical_lsw** Lägre 32 bitar (31-0) för den fysiska adressen att söka efter.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckade ARP IP-adress Sök
- Det gick inte att hitta **NX_ENTRY_NOT_FOUND** -mappningen (0x16) i ARP-cachen.
- **NX_PTR_ERROR** (0X07) ogiltig IP-eller minnes pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw och physical_lsw är båda 0.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,
- nx_arp_enable nx_arp_gratuitous_send,
- nx_arp_hardware_address_find nx_arp_info_get,
- nx_arp_static_entries_delete nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

Ta bort alla statiska ARP-poster

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort alla statiska poster i ARP-cachen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) statiska poster tas bort.
- **NX_PTR_ERROR** (0X07) ogiltig ip_ptr pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,
- nx_arp_enable nx_arp_gratuitous_send,
- nx_arp_hardware_address_find nx_arp_info_get,
- nx_arp_ip_address_find nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

Skapa statisk IP-adress för maskin varu mappning i ARP-cache

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en statisk IP-till-fysisk-adress mappning i ARP-cachen för den angivna IP-instansen. Statiska ARP-poster omfattas inte av regelbundna ARP-uppdateringar.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **ip_address** IP-adress att mappa.
- **physical_msw** De 16 främsta bitarna (47-32) av den fysiska adressen som ska mappas.
- **physical_lsw** Nedre 32 bitar (31-0) av den fysiska adressen som ska mappas.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00)-statisk post har skapats.
- **NX_NO_MORE_ENTRIES** (0X17) inga fler ARP-poster är tillgängliga i ARP-cachen.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw och physical_lsw är båda 0.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,
- nx_arp_enable nx_arp_gratuitous_send,
- nx_arp_hardware_address_find nx_arp_info_get,
- nx_arp_ip_address_find nx_arp_static_entries_delete,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

Ta bort statisk IP-adress till maskin varu mappning i ARP-cache


### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hittar och tar bort en tidigare skapad statisk IP-till-fysisk-adress mappning i ARP-cachen för den angivna IP-instansen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **ip_address** IP-adress som har mappats statiskt.
- **physical_msw** De 16 16 bitarna (47-32) för den fysiska adress som har mappats statiskt.
- **physical_lsw** Lägre 32 bitar (31-0) för den fysiska adress som har mappats statiskt.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckade ARP-post borttagning.
- Det gick inte att hitta den statiska ARP-posten **NX_ENTRY_NOT_FOUND** (0x16) i ARP-cachen.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw och physical_lsw är båda 0.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,
- nx_arp_enable nx_arp_gratuitous_send,
- nx_arp_hardware_address_find nx_arp_info_get,
- nx_arp_ip_address_find nx_arp_static_entries_delete,
- nx_arp_static_entry_create

## <a name="nx_icmp_enable"></a>nx_icmp_enable

Aktivera Internet Control Message Protocol (ICMP)

### <a name="prototype"></a>Prototyp

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar ICMP-komponenten för den angivna IP-instansen.
ICMP-komponenten ansvarar för hantering av Internet fel meddelanden och ping-förfrågningar och svar.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförde ICMP-aktivering.
- **NX_ALREADY_ENABLED** (0X15) ICMP har redan Aktiver ATS.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a>Se även

- nx_icmp_info_get nx_icmp_ping

## <a name="nx_icmp_info_get"></a>nx_icmp_info_get

Hämta information om ICMP-aktiviteter

### <a name="prototype"></a>Prototyp

```C
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om ICMP-aktiviteter för den angivna IP-instansen.

*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **pings_sent** Pekare till målet för det totala antalet pingar som skickats.
- **ping_timeouts** Pekare till målet för det totala antalet ping-tidsgräns.
- **ping_threads_suspended** Pekare till målet för det totala antalet trådar som har inaktiverats för ping-begäranden.
- **ping_responses_received** Pekare till åltabell av det totala antalet ping-svar som tagits emot.
- **icmp_checksum_errors** Pekare till målet för det totala antalet fel i ICMP-kontrollsumma.
- **icmp_unhandled_messages** Pekare till åltabell av det totala antalet ohanterade ICMP-meddelanden.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades Hämta ICMP-information.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a>Se även

- nx_icmp_enable nx_icmp_ping

## <a name="nx_icmp_ping"></a>nx_icmp_ping

Skicka ping-begäran till angiven IP-adress

### <a name="prototype"></a>Prototyp

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar en ping-begäran till den angivna IP-adressen och väntar på den angivna tiden för ett ping-svarsmeddelande. Om inget svar tas emot returneras ett fel. Annars returneras hela svarsmeddelandet i variabeln som pekas av response_ptr.

*Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **ip_address** IP-adress i byte ordning för värden till ping. data pekare till data arean för ping-meddelande.
- **data_size** Antal byte i ping-data
- **response_ptr** Pekare till paket pekare för att returnera meddelandet ping-svar i.
- **wait_option** Anger hur lång tid det tar att vänta på ping-svar. vänte alternativen definieras enligt följande:

  - NX_NO_WAIT (0x00000000)
  - NX_WAIT_FOREVER (0xFFFFFFFF)
  - timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades ping. Svars meddelandets pekare placerades i variabeln som pekades på av response_ptr.
- **NX_NO_PACKET** (0X01) Det gick inte att allokera ett ping Request-paket.
- **NX_OVERFLOW** (0x03) det angivna data utrymmet överskrider standard paket storleken för den här IP-instansen.
- **NX_NO_RESPONSE** (0X29) begärda IP-adressen svarade inte.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.
- **NX_PTR_ERROR** (0X07) ogiltig IP-eller svars pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
    Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
    &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
    address 1.2.3.5 and the response packet is contained in the
    packet pointed to by response_ptr. It should have the same "abcd"
    four bytes of data. */
```

### <a name="see-also"></a>Se även

- nx_icmp_enable nx_icmp_info_get

## <a name="nx_igmp_enable"></a>nx_igmp_enable

Aktivera IGMP (Internet Group Management Protocol)

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar IGMP-komponenten på den angivna IP-instansen.
IGMP-komponenten ansvarar för att ge stöd för hanterings åtgärder för IP-multicast-grupper.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad IGMP-aktivering.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_ALREADY_ENABLED** (0X15) den här komponenten har redan Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a>Se även

- nx_igmp_info_get nx_igmp_loopback_disable,
- nx_igmp_loopback_enable nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join nx_igmp_multicast_leave

## <a name="nx_igmp_info_get"></a>nx_igmp_info_get

Hämta information om IGMP-aktiviteter

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om IGMP-aktiviteter för den angivna IP-instansen.

*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **igmp_reports_sent** Pekare till målet för det totala antalet ICMP-rapporter som skickats.
- **igmp_queries_received** Pekare till målet för det totala antalet frågor som tagits emot av multicast-router.
- **igmp_checksum_errors** Pekare till målet för det totala antalet fel i IGMP-kontrollsumma för mottagna paket.
- **current_groups_joined** Pekare till målet för det aktuella antalet grupper som anslöts via den här IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad IGMP-informations hämtning.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a>Se även

- nx_igmp_enable nx_igmp_loopback_disable,
- nx_igmp_loopback_enable nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

Inaktivera IGMP loopback

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar IGMP loopback för alla efterföljande multicast-grupper som anslutits.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0X00) lyckades IGMP loopback-inaktive ring.
- **NX_NOT_ENABLED** (0X14) IGMP är inte aktiverat.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) anroparen är inte en tråd eller initiering.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a>Se även

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,
- nx_igmp_multicast_interface_join nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

Aktivera IGMP loopback

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar IGMP loopback för alla efterföljande multicast-grupper som är anslutna.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0X00) lyckades IGMP loopback-inaktive ring.
- **NX_NOT_ENABLED** (0X14) IGMP är inte aktiverat.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) anroparen är inte en tråd eller initiering.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a>Se även

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_multicast_interface_join nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join

Ansluta IP-instans till angiven multicast-grupp via ett gränssnitt

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ansluter en IP-instans till den angivna multicast-gruppen via ett angivet nätverks gränssnitt. En intern räknare upprätthålls för att hålla reda på hur många gånger samma grupp har anslutits. När du har anslutit till multicast-gruppen tillåter IGMP-komponenten mottagning av IP-paket med den här grupp adressen via det angivna nätverks gränssnittet och rapporterar till routrar som den här IP-adressen är medlem i den här multicast-gruppen. IGMP-medlemskapet Anslut, rapportera och lämna meddelanden skickas också via det angivna nätverks gränssnittet.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **group_address** Klass D IP multicast-gruppadress att ansluta till i värdens byte ordning.
- **interface_index** Index för det gränssnitt som är kopplat till NetX-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) multicast-gruppanslutningen är klar.
- **NX_NO_MORE_ENTRIES** (0x17) Det går inte att ansluta fler multicast-grupper, maximalt antal har överskridits.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_INVALID_INTERFACE** (0X4C) enhets index pekar på ett ogiltigt nätverks gränssnitt.
- Den tillhandahållna **NX_IP_ADDRESS_ERROR** (0X21) multicast-gruppadressen är inte en giltig klass D-adress.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) stöd för IP-multicast är inte aktiverat.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a>Se även

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

Anslut IP-instans till angiven multicast-grupp

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ansluter en IP-instans till den angivna multicast-gruppen. En intern räknare upprätthålls för att hålla reda på hur många gånger samma grupp har anslutits. Driv rutinen anropas för att skicka en IGMP-rapport om detta är den första anslutnings förfrågan som finns i nätverket och som anger värden för att ansluta till gruppen. När du har anslutit till IGMP-komponenten kan IGMP-komponenten ta emot IP-paket med den här grupp adressen och rapportera till routrar som den här IP-adressen är medlem i den här multicast-gruppen.

> [!NOTE]
> *Använd tjänsten nx_igmp_multicast_interface_join om du vill ansluta en multicast-grupp på en icke-primär enhet **.***

- **Parametrar**

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **group_address** Klass D IP multicast-grupp adress att ansluta till.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) multicast-gruppanslutningen är klar.
- **NX_NO_MORE_ENTRIES** (0x17) Det går inte att ansluta fler multicast-grupper, maximalt antal har överskridits.
- **NX_INVALID_INTERFACE** (0X4C) enhets index pekar på ett ogiltigt nätverks gränssnitt.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-gruppadress.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a>Se även

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable nx_igmp_multicast_interface_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

Orsak till att IP-instansen lämnar angiven multicast-grupp

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten gör att en IP-instans lämnar den angivna multicast-gruppen, om antalet tjänstledighets begär Anden matchar antalet anslutnings begär Anden. Annars minskas antalet interna anslutningar helt enkelt.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **group_address** Multicast-grupp att lämna.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) multicast-gruppanslutningen är klar.
- Det gick inte att hitta den tidigare kopplings förfrågan för **NX_ENTRY_NOT_FOUND** (0x16).
- **NX_INVALID_INTERFACE** (0X4C) enhets index pekar på ett ogiltigt nätverks gränssnitt.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-gruppadress.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>Se även

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy

Meddela program om IP-adressen ändras


### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar en program meddelande funktion som anropas när IP-adressen ändras.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **change_notify** Pekare till funktionen IP-ändrings meddelande. Om den här parametern är NX_NULL inaktive ras meddelandet om ändring av IP-adress.
- **additional_info** Pekare till valfri ytterligare information som också tillhandahålls till meddelande funktionen när IP-adressen ändras.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) avisering om ändring av IP-adress har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,
- nx_ip_driver_direct_command nx_ip_driver_interface_direct_command,
- nx_ip_forwarding_disable nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check nx_system_initialize

## <a name="nx_ip_address_get"></a>nx_ip_address_get

Hämta IP-adress och nätverks mask

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar IP-adressen och dess nätmask för det primära nätverks gränssnittet.

* Om du vill hämta information om den sekundära enheten använder du tjänsten
- **nx_ip_interface_address_get**. *

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **ip_address** Pekare till mål för IP-adress.
- **network_mask** Pekare till målet för nätverks masken.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) IP-adress hämtades.
- **NX_PTR_ERROR** (0X07) ogiltig IP-eller RETUR variabel pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,
- nx_ip_delete nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,
- nx_ip_forwarding_enable nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_address_set"></a>nx_ip_address_set

Ange IP-adress och nätverks mask

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger IP-adress och nätverks mask för det primära nätverks gränssnittet.

*Om du vill ange IP-adress och nätverks mask för den sekundära enheten använder du tjänsten **nx_ip_interface_address_set**.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **ip_address** Ny IP-adress.
- **network_mask** Ny nätverks mask.

### <a name="return-values"></a>Retur värden

- Den angivna IP-adressen för **NX_SUCCESS** (0x00).
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,
- nx_ip_delete nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,
- nx_ip_forwarding_enable nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_create"></a>nx_ip_create

Skapa en IP-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en IP-instans med användaren angiven IP-adress och nätverks driv rutin. Dessutom måste programmet ange en tidigare skapad modempool för IP-instansen som ska användas för intern paket tilldelning. Observera att den angivna program nätverks driv rutinen inte anropas förrän den här IP-tråden körts.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare för att kontrol lera block för att skapa en ny IP-instans.
- **namn** Namnet på den nya IP-instansen.
- **ip_address** IP-adress för den här nya IP-instansen.
- **network_mask** Mask för att avgränsa nätverks delen av IP-adressen för under näts tycken och Super-nett användning.
- **default_pool** Pekare för att kontrol lera blockeringen av tidigare skapade NetX-paket.
- **ip_network_driver** Nätverks driv rutin som anges av användaren som används för att skicka och ta emot IP-paket.
- **memory_ptr** Pekare till minnes området för IP Helper-trådens stack Area.
- **memory_size** Antal byte i minnes området för IP Helper-trådens stack.
- **prioritet** Prioritet för IP Helper-tråd.

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0x00) en lyckad IP-instans skapas.
- **NX_NOT_IMPLEMENTED** (0X4A) netx-biblioteket är felaktigt konfigurerat.
- **NX_PTR_ERROR** (0X07) ogiltig IP, nätverks driv rutin funktion pekare, adresspool eller minnes pekare.
- **NX_SIZE_ERROR** (0X09) den angivna stack storleken är för liten.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_IP_ADDRESS_ERROR** (0X21) den angivna IP-adressen är ogiltig.
- **NX_OPTION_ERROR** (0X21) den angivna prioriteten för IP-tråd är ogiltig.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_delete nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,
- nx_ip_forwarding_enable nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_delete"></a>nx_ip_delete

Ta bort den tidigare skapade IP-instansen


### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad IP-instans och släpper alla system resurser som ägs av IP-instansen.

### <a name="parameters"></a>Parametrar
- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) IP-borttagning har slutförts.
- **NX_SOCKETS_BOUND** (0X28) den här IP-instansen har fortfarande UDP-eller TCP-Sockets kopplade till sig. Alla Sockets måste vara obundna och tas bort innan IP-instansen tas bort.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,
- nx_ip_forwarding_enable nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

Issue-kommando för nätverks driv rutin

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tillhandahåller ett direkt gränssnitt till programmets primära nätverks gränssnitts driv rutin som anges under ***nx_ip_create*** -anropet.

Programspecifika kommandon kan användas för att tillhandahålla ett numeriskt värde som är större än eller lika med NX_LINK_USER_COMMAND.

*Om du vill utfärda kommando för den sekundära enheten använder du tjänsten **nx_ip_driver_interface_direct_command** .*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **kommando** Numerisk kommando kod. Standard kommandon definieras enligt följande:

- NX_LINK_GET_STATUS (10)
- NX_LINK_GET_SPEED (11)
- NX_LINK_GET_DUPLEX_TYPE (12)
- NX_LINK_GET_ERROR_COUNT (13)
- NX_LINK_GET_RX_COUNT (14)
- NX_LINK_GET_TX_COUNT (15)
- NX_LINK_GET_ALLOC_ERRORS (16)
- NX_LINK_USER_COMMAND (50)

- **return_value_ptr** Pekare som returnerar variabeln i anroparen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) enhets direkt kommando för nätverks driv rutin.
- **NX_UNHANDLED_COMMAND** (0x44) ohanterad eller ej implementerad nätverks driv rutin kommando.
- **NX_PTR_ERROR** (0X07) ogiltig IP-eller RETUR värdes pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_INVALID_INTERFACE** (0X4C) ogiltigt gränssnitts index.

### <a name="allowed-from"></a>Tillåten från

Konversation

- **Avstängningen möjlig**

Inga

### <a name="example"></a>Exempel

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,
- nx_ip_forwarding_disable nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check nx_system_initialize

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command

Issue-kommando för nätverks driv rutin

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tillhandahåller ett direkt kommando för programmets nätverks enhets driv rutin i IP-instansen. Programspecifika kommandon kan användas för att tillhandahålla ett numeriskt värde som är större än eller lika med *NX_LINK_USER_COMMAND*.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **kommando** Numerisk kommando kod. Standard kommandon definieras enligt följande:
- NX_LINK_GET_STATUS (10)
- NX_LINK_GET_SPEED (11)
- NX_LINK_GET_DUPLEX_TYPE (12)
- NX_LINK_GET_ERROR_COUNT (13)
- NX_LINK_GET_RX_COUNT (14)
- NX_LINK_GET_TX_COUNT (15)
- NX_LINK_GET_ALLOC_ERRORS (16)
- NX_LINK_USER_COMMAND (50)
- **interface_index** Index för det nätverks gränssnitt som kommandot ska skickas till.
- **return_value_ptr** Pekare som returnerar variabeln i anroparen.

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0x00) enhets direkt kommando för nätverks driv rutin.
- **NX_UNHANDLED_COMMAND** (0x44) ohanterad eller ej implementerad nätverks driv rutin kommando.
- **NX_INVALID_INTERFACE** (0X4C) ogiltigt gränssnitts index
- **NX_PTR_ERROR** (0X07) ogiltig IP-eller RETUR värdes pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;
    status = nx_ip_driver_interface_direct_command(&ip_0,
    NX_LINK_GET_STATUS,
    interface_index,
    &link_status);
/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_forwarding_disable nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check nx_system_initialize

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

Inaktivera vidarebefordran av IP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar vidarebefordring av IP-paket i IP-komponenten NetX. Den här tjänsten inaktive ras automatiskt när du skapar IP-uppgiften.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00)-slutförd IP-vidarebefordring inaktivera.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check nx_system_initialize

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

Aktivera vidarebefordran av IP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar vidarebefordring av IP-paket i NetX-IP-komponenten. Den här tjänsten inaktive ras automatiskt när du skapar IP-uppgiften.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0X00) lyckad IP-vidarebefordring aktivera.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check nx_system_initialize

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

Inaktivera fragmentering av IP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar funktionen för fragmentering och sammansättning av IP-paket. För paket som väntar på att ommonteras, frigör tjänsten dessa paket. Den här tjänsten inaktive ras automatiskt när du skapar IP-uppgiften.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0x00) IP-fragment har inaktiverats.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) IP-fragmentering är inte aktive rad på IP-instansen.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check nx_system_initialize

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

Aktivera fragmentering av IP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar funktioner för att fragmentera och ommontera IP-paket. Den här tjänsten inaktive ras automatiskt när du skapar IP-uppgiften.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades aktivera IP-fragment.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) funktioner för IP-fragmentering har inte kompilerats i netx.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,
- nx_ip_status_check nx_system_initialize

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

Ange IP-adress för gateway

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger IP-gatewayens IP-adress. All trafik utanför nätverket dirigeras till den här gatewayen för överföring. Gatewayen måste vara direkt tillgänglig via ett av nätverks gränssnitten.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **ip_address** IP-adressen för gatewayen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) GATEWAYens IP-adress har angetts.
- **NX_PTR_ERROR** (0X07) ogiltig IP-instans pekare.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, tråd

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a>Se även

- nx_ip_info_get nx_ip_static_route_add nx_ip_static_route_delete

## <a name="nx_ip_info_get"></a>nx_ip_info_get

Hämta information om IP-aktiviteter

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om IP-aktiviteter för den angivna IP-instansen.

*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **ip_total_packets_sent** Pekare till målet för det totala antalet skickade IP-paket.
- **ip_total_bytes_sent** Pekare till målet för det totala antalet byte som har skickats.
- **ip_total_packets_received** Pekare till målet för det totala antalet IP-mottagna paket.
- **ip_total_bytes_received** Pekare till målet för det totala antalet mottagna IP-byte.
- **ip_invalid_packets** Pekare till målet för det totala antalet ogiltiga IP-paket.
- **ip_receive_packets_dropped** Pekare till målet för det totala antalet mottagna paket som har tagits bort.
- **ip_receive_checksum_errors** Pekare till målet för det totala antalet fel i kontroll summor i mottagna paket.
- **ip_send_packets_dropped** Pekare till målet för det totala antalet skickade paket som släppts.
- **ip_total_fragments_sent** Pekare till målet för det totala antalet fragment som skickats.
- **ip_total_fragments_received** Pekare till målet för det totala antalet fragment som tagits emot.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) hämtning av IP-information.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Retrieve IP information from previously created IP
Instance 0. */
status = nx_ip_info_get(&ip_0,
    &ip_total_packets_sent,
    &ip_total_bytes_sent,
    &ip_total_packets_received,
    &ip_total_bytes_received,
    &ip_invalid_packets,
    &ip_receive_packets_dropped,
    &ip_receive_checksum_errors,
    &ip_send_packets_dropped,
    &ip_total_fragments_sent,
    &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,
- nx_ip_forwarding_enable nx_ip_fragment_disable,
- nx_ip_fragment_enable nx_ip_status_check nx_system_initialize

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get

Hämta gränssnittets IP-adress

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar IP-adressen för ett angivet nätverks gränssnitt.

*Den angivna enheten måste, om den inte är den primära enheten, vara tidigare ansluten till IP-instansen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **interface_index** Gränssnitts index, samma värde som indexet till nätverks gränssnittet som är kopplat till IP-instansen.
- **ip_address** Pekare till målet för enhets gränssnittets IP-adress.
- **network_mask** Pekare till målet för enhets gränssnittets nätverks mask.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) IP-adress hämtades.
- **NX_INVALID_INTERFACE** (0x4C) det angivna nätverks gränssnittet är ogiltigt.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a>Se även

- nx_ip_interface_address_set nx_ip_interface_attach,
- nx_ip_interface_info_get nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set

Ange gränssnittets IP-adress och nätverks mask

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger IP-adressen och nätverks masken för det angivna IP-gränssnittet.

*Det angivna gränssnittet måste vara kopplat till IP-instansen tidigare.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **interface_index** Index för det gränssnitt som är kopplat till NetX-instansen.
- **ip_address** Nytt IP-adress för nätverks gränssnitt.
- **network_mask** Nätverks mask för nytt gränssnitt.

### <a name="return-values"></a>Retur värden

- Den angivna IP-adressen för **NX_SUCCESS** (0x00).
- **NX_INVALID_INTERFACE** (0x4C) det angivna nätverks gränssnittet är ogiltigt.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0X07) ogiltiga pekare.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a>Se även

- nx_ip_interface_address_get nx_ip_interface_attach,
- nx_ip_interface_info_get nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach

Koppla nätverks gränssnitt till IP-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till ett fysiskt nätverks gränssnitt i IP-gränssnittet. Observera att IP-instansen skapas med det primära gränssnittet så att varje ytterligare gränssnitt är sekundärt till det primära gränssnittet. Det totala antalet nätverks gränssnitt som är kopplade till IP-instansen (inklusive det primära gränssnittet) får inte överskrida **NX_MAX_PHYSICAL_INTERFACES**.

Om IP-tråden inte har körts än kommer de sekundära gränssnitten att initieras som en del av start processen för IP-tråd som initierar alla fysiska gränssnitt.

Om IP-tråden inte körs ännu initieras det sekundära gränssnittet som en del av ***nx_ip_interface_attachs*** tjänsten.

*ip_ptr måste peka på en giltig IP-struktur för NetX.*

- ***NX_MAX_PHYSICAL_INTERFACES** måste konfigureras för antalet nätverks gränssnitt för IP-instansen. Standardvärdet är ett.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **INTERFACE_NAME** Pekare till gränssnittets namn sträng.
- **ip_address** Enhetens IP-adress i byte ordningen för värden.
- **network_mask** Enhetens nätverks mask i byte ordningen för värden.
- **ip_link_driver** Ethernet-drivrutin för gränssnittet.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** -posten (0x00) läggs till i den statiska routningstabellen.
- **NX_NO_MORE_ENTRIES** (0X17) Max antal gränssnitt.
- **NX_MAX_PHYSICAL_INTERFACES** har överskridits.
- **NX_DUPLICATED_ENTRY** (0X52) den angivna IP-adressen används redan på den här IP-instansen.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0X07) ogiltig pekare inmatade.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress för indata.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Attach secondary device for device IP address 192.168.1.68 with
    the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
    IP_ADDRESS(192,168,1,68),
    0xFFFFFF00UL,
    nx_etherDriver);
/* If status is NX_SUCCESS the interface was successfully added to
    the IP instance interface table. */
```

### <a name="see-also"></a>Se även

- nx_ip_interface_address_get nx_ip_interface_address_set,
- nx_ip_interface_info_get nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

Hämta nätverks gränssnitts parametrar


### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om nätverks parametrar för det angivna nätverks gränssnittet. Alla data hämtas i byte ordning för värden.

*ip_ptr måste peka på en giltig IP-struktur för NetX. Det angivna gränssnittet, om inte det primära gränssnittet, måste vara tidigare kopplat till IP-instansen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **interface_index** Index som anger nätverks gränssnitt.
- **INTERFACE_NAME** Pekar på den buffert som innehåller namnet på nätverks gränssnittet.
- **ip_address** Pekar till målet för gränssnittets IP-adress.
- **network_mask** Pekare till målet för nätverks masken.
- **mtu_size** Pekare till målet för den maximala överförings enheten för det här gränssnittet.
- **physical_address_msw** Pekare till målet för de 16 främsta bitarna i enhetens MAC-adress.
- **physical_address_lsw** Pekare till målet för nedre 32 bitar av enhetens MAC-adress.


### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0X00) gränssnitts information har hämtats.
- **NX_PTR_ERROR** (0X07) ogiltig pekare inmatade.
- **NX_INVALID_INTERFACE** (0X4C) ogiltig IP-pekare.
- Tjänsten **NX_CALLER_ERROR** (0x11) anropas inte från system initiering eller tråd kontext.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Retrieve interface parameters for the specified interface (index
    1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1

status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
    &name_ptr, &ip_address,
    &network_mask,
    &mtu_size,
    &physical_address_msw,
    &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
    successfully retrieved. */
```

### <a name="see-also"></a>Se även

- nx_ip_interface_address_get nx_ip_interface_address_set,
- nx_ip_interface_attach nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check

Kontrol lera status för en IP-instans


### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kontrollerar och väntar på den angivna statusen för nätverks gränssnittet för en tidigare skapad IP-instans.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **interface_index** Gränssnitts index nummer
- **needed_status** IP-status begärd, definierad i bit-Map-formulär enligt följande:
    - NX_IP_INITIALIZE_DONE (0x0001)
    - NX_IP_ADDRESS_RESOLVED (0x0002)
    - NX_IP_LINK_ENABLED (0x0004)
    - NX_IP_ARP_ENABLED (0x0008)
    - NX_IP_UDP_ENABLED (0x0010)
    - NX_IP_TCP_ENABLED (0x0020)
    - NX_IP_IGMP_ENABLED (0x0040)
    - NX_IP_RARP_COMPLETE (0x0080)
    - NX_IP_INTERFACE_LINK_ENABLED (0x0100)
- **actual_status** Pekare till målet för faktisk BITS-uppsättning.
- **wait_option** Definierar hur tjänsten fungerar om de begärda status bitarna inte är tillgängliga. Vänte alternativen definieras enligt följande:
    - NX_NO_WAIT (0x00000000)
    - NX_WAIT_FOREVER (0xFFFFFFFF)
    - timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) kontroll av IP-status har slutförts.
- **NX_NOT_SUCCESSFUL** (0X43) status förfrågan uppfylldes inte inom den angivna tids gränsen.
- **NX_PTR_ERROR** (0x07) IP-pekaren är eller har blivit ogiltig eller så är den faktiska status pekaren ogiltig.
- **NX_OPTION_ERROR** (0X0a) ogiltigt status alternativ.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_INVALID_INTERFACE** (0x4C) Interface_index är utanför intervallet. eller så är gränssnittet ogiltigt.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a>Se även

- nx_ip_interface_address_get nx_ip_interface_address_set,
- nx_ip_interface_attach nx_ip_interface_info_get,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set

Ange funktionen länk status ändring meddela motringning

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a>Beskrivning

Den här tjänsten konfigurerar funktionen länk status ändring meddela motringning. Den användardefinierade *link_status_change_notify* rutinen anropas när antingen den primära eller sekundära gränssnitts statusen ändras (till exempel om IP-adressen har ändrats). Om *link_status_change_notify* är null, är länk status ändring meddela motringning funktion inaktive rad.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare för IP Control Block
- **link_status_change_notify** Återanrops funktion som användaren har angett för att anropas vid en ändring i det fysiska gränssnittet.


### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) har angetts
- **NX_PTR_ERROR** (0X07) ogiltig kontroll block pekare eller ny fysisk adress pekare
- Tjänsten **NX_CALLER_ERROR** (0x11) anropas inte från system initiering eller tråd kontext.


### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a>Se även

- nx_ip_interface_address_get nx_ip_interface_address_set,
- nx_ip_interface_attach nx_ip_interface_info_get,
- nx_ip_interface_status_check

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

Inaktivera sändning/mottagning av RAW-paket


### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar överföring och mottagning av obehandlade IP-paket för den här IP-instansen. Om RAW Packet service tidigare har Aktiver ATS och det finns RAW-paket i Receive-kön, kommer den här tjänsten att släppa eventuella mottagna rå paket.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) genomförde IP RAW-paket inaktivera.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a>Se även

- nx_ip_raw_packet_enable nx_ip_raw_packet_receive,
- nx_ip_raw_packet_send nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

Aktivera rå paket bearbetning


### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten möjliggör överföring och mottagning av RAW IP-paket för den här IP-instansen. Inkommande TCP-, UDP-, ICMP-och IGMP-paket bearbetas fortfarande av NetX. Paket med okända protokoll typer för övre skikt bearbetas av rutinen för mottagning av rå paket.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckade IP RAW-paket aktivera.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a>Se även

- nx_ip_raw_packet_disable nx_ip_raw_packet_receive,
- nx_ip_raw_packet_send nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_interface_send"></a>nx_ip_raw_packet_interface_send

Skicka RAW IP-paket via angivet nätverks gränssnitt

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett RAW IP-paket till målets IP-adress med den angivna lokala IP-adressen som käll adress och via det associerade nätverks gränssnittet. Observera att den här rutinen returnerar omedelbart och är därför inte känd om IP-paketet faktiskt har skickats. Nätverks driv rutinen kommer att ansvara för att släppa paketet när överföringen är klar. Den här tjänsten skiljer sig från andra tjänster eftersom det inte finns något sätt att veta om paketet faktiskt har skickats. Det kan gå förlorat på Internet.

*Observera att RAW IP-bearbetning måste vara aktiverat.*

*Den här tjänsten liknar **nx_ip_raw_packet_send**, förutom att den här tjänsten tillåter att ett program skickar RAW IP-paket från ett angivet fysiskt gränssnitt.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till en tidigare skapad IP-aktivitet.
- **packet_ptr** Pekare till paket att överföra.
- **destination_ip** IP-adress för att skicka paket.
- **address_index** Index för den gränssnitts adress som paketet ska skickas till.
- **type_of_service** Typ av tjänst för paket.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) paket har skickats.
- **NX_IP_ADDRESS_ERROR** (0X21) inget lämpligt utgående gränssnitt är tillgängligt.
- **NX_NOT_ENABLED** (0X14) RAW IP-paketfiltrering är inte aktiverat.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0X07) ogiltig pekare inmatade.
- **NX_OPTION_ERROR** (0X0a) ogiltig tjänst typ har angetts.
- **NX_OVERFLOW** (0X03) ogiltig lägga pekare för paket.
- **NX_UNDERFLOW** (protokollnumret 0x02) ogiltig lägga pekare för paket.
- **NX_INVALID_INTERFACE** (0X4C) ogiltigt gränssnitts index angavs.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a>Se även

- nx_ip_raw_packet_disable nx_ip_raw_packet_enable,
- nx_ip_raw_packet_receive nx_ip_raw_packet_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

Ta emot RAW IP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar emot ett RAW IP-paket från den angivna IP-instansen. Om det finns IP-paket i kön för mottagna obearbetade paket returneras det första (äldsta) paketet till anroparen. Annars, om inga paket är tillgängliga, kan anroparen pausa så som anges av alternativet vänta.

*Om NX_SUCCESS returneras, ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **packet_ptr** Pekare till pekaren för att placera det mottagna RAW IP-paketet i.
- **wait_option** Definierar hur tjänsten fungerar om det inte finns några tillgängliga obehandlade IP-paket. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) Det gick inte att ta emot IP RAW-paket.
- **NX_NO_PACKET** (0X01) inget paket var tillgängligt.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.
- **NX_PTR_ERROR** (0X07) ogiltig IP eller RETUR paket pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a>Se även

- nx_ip_raw_packet_disable nx_ip_raw_packet_enable,
- nx_ip_raw_packet_send nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

Skicka RAW IP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett RAW IP-paket till målets IP-adress. Observera att den här rutinen returnerar omedelbart och är därför inte känd om IP-paketet faktiskt har skickats. Nätverks driv rutinen kommer att ansvara för att släppa paketet när överföringen är klar.

För ett multihome-system använder NetX målets IP-adress för att hitta ett lämpligt nätverks gränssnitt och använder gränssnittets IP-adress som käll adress. Om mål-IP-adressen är broadcast eller multicast används det första giltiga gränssnittet. Programmen använder ***nx_ip_raw_packet_interface_send*** i det här fallet.

*Om ett fel returneras ska programmet inte släppa paketet efter det här anropet. På så sätt kan oväntade resultat uppstå, eftersom nätverks driv rutinen kommer att släppa paketet efter överföringen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **packet_ptr** Pekare till det RAW IP-paket som ska skickas.
- **destination_ip** Målets IP-adress, som kan vara en speciell värd-IP-adress, en nätverks sändning, en intern loop eller en multicast-adress.
- **type_of_service** Definierar typ av tjänst för överföringen, de juridiska värdena är följande:
- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)


### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckade IP RAW-paket sändning initierad.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.
- **NX_NOT_ENABLED** (0X14) RAW IP-funktionen är inte aktive rad.
- **NX_OPTION_ERROR** (0X0a) ogiltig typ av tjänst.
- **NX_UNDERFLOW** (protokollnumret 0x02) inte tillräckligt med utrymme för att lägga ett IP-huvud i paketet.
- **NX_OVERFLOW** (0X03) paket tilläggs pekare är ogiltig.
- **NX_PTR_ERROR** (0X07) ogiltig IP-eller paket pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a>Se även

- nx_ip_raw_packet_disable nx_ip_raw_packet_enable,
- nx_ip_raw_packet_receive nx_ip_raw_packet_send,
- nx_ip_raw_packet_interface_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

Lägg till statisk väg i routningstabellen

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en post i tabellen för statisk routning. Observera att den *next_hop* adressen måste vara direkt åtkomlig från en av de lokala nätverks enheterna.

*Observera att ip_ptr måste peka på en giltig IP-struktur för NetX och NetX-biblioteket måste skapas med NX_ENABLE_IP_STATIC_ROUTING som har definierats för att använda den här tjänsten. Som standard skapas NetX utan att NX_ENABLE_IP_STATIC_ROUTING definieras.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **network_address** Mål nätverks adress, i byte ordning för värden
- **net_mask** Mål nätverks mask, i byte ordning för värden
- **next_hop** Nästa hopp adress för mål nätverket, i byte ordning för värden

### <a name="return-values"></a>Retur värden

- **NX_SUCCESSs** posten (0x00) läggs till i tabellen med statiska vägar.
- **NX_OVERFLOW** (0X03) statisk routningstabell är full.
- **NX_NOT_SUPPORTED** (0X4B) den här funktionen är inte kompilerad i.
- **NX_IP_ADDRESS_ERROR** (0X21) nästa hopp är inte direkt tillgängligt via lokala gränssnitt.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0X07) ogiltig ip_ptr pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a>Se även

- nx_ip_gateway_address_set nx_ip_info_get nx_ip_static_route_delete

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

Ta bort statisk väg från routningstabell

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en post från tabellen för statisk routning.

*Observera att ip_ptr måste peka på en giltig IP-struktur för NetX och NetX-biblioteket måste skapas med NX_ENABLE_IP_STATIC_ROUTING som har definierats för att använda den här tjänsten. Som standard skapas NetX utan att NX_ENABLE_IP_STATIC_ROUTING definieras.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **network_address** Mål nätverks adress i byte ordning för värden.
- **net_mask** Mål nätverks mask i byte ordning för värden.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a>Se även

- nx_ip_gateway_address_set nx_ip_info_get nx_ip_static_route_add

## <a name="nx_ip_status_check"></a>nx_ip_status_check

Kontrol lera status för en IP-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kontrollerar och väntar på den angivna statusen för det primära nätverks gränssnittet för en tidigare skapad IP-instans. För att få status för sekundära gränssnitt, ska program använda tjänsten ***nx_ip_interface_status_check.***

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **needed_status** IP-status begärd, definierad i bit-Map-formulär enligt följande:
- NX_IP_INITIALIZE_DONE (0x0001)
- NX_IP_ADDRESS_RESOLVED (0x0002)
- NX_IP_LINK_ENABLED (0x0004)
- NX_IP_ARP_ENABLED (0x0008)
- NX_IP_UDP_ENABLED (0x0010)
- NX_IP_TCP_ENABLED (0x0020)
- NX_IP_IGMP_ENABLED (0x0040)
- NX_IP_RARP_COMPLETE (0x0080)
- NX_IP_INTERFACE_LINK_ENABLED (0x0100)
- **actual_status** Pekare till målet för faktisk BITS-uppsättning.
- **wait_option** Definierar hur tjänsten fungerar om de begärda status bitarna inte är tillgängliga. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) kontroll av IP-status har slutförts.
- **NX_NOT_SUCCESSFUL** (0X43) status förfrågan uppfylldes inte inom den angivna tids gränsen.
- **NX_PTR_ERROR** (0x07) IP-pekaren är eller har blivit ogiltig eller så är den faktiska status pekaren ogiltig.
- **NX_OPTION_ERROR** (0X0a) ogiltigt status alternativ.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,
- nx_ip_forwarding_enable nx_ip_fragment_disable,
- nx_ip_fragment_enable nx_ip_info_get nx_system_initialize

## <a name="nx_packet_allocate"></a>nx_packet_allocate

Allokera paket från angiven pool

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten allokerar ett paket från den angivna poolen och justerar lägga-pekaren i paketet enligt den typ av paket som angetts. Om inget paket är tillgängligt pausas tjänsten enligt det angivna vänte alternativet.

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till den tidigare skapade lagringspoolen.
- **packet_ptr** Pekare till pekaren över den allokerade paket pekaren.
- **packet_type** Definierar den typ av paket som begärs. Se "paket pooler" på sidan 49 i kapitel 3 för en lista över paket typer som stöds.
- **wait_option** Definierar vänte tiden i Tick om det inte finns några tillgängliga paket i modempoolen. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) paket tilldelningen lyckades.
- **NX_NO_PACKET** (0X01) inget paket tillgängligt.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_INVALID_PARAMETERSs** paket storlek (0X4D) stöder inte protokollet.
- **NX_OPTION_ERROR** (0X0a) ogiltig pakettyp.
- **NX_PTR_ERROR** (0X07) ogiltig pool eller paket retur pekare.
- **NX_CALLER_ERROR** (0X11) ogiltigt wait-alternativ från icke-tråd.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er (program nätverks driv rutiner). Alternativet wait måste vara NX_NO_WAIT när det används i ISR eller i timer-kontext.

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a>Se även

- nx_packet_copy nx_packet_data_append,
- nx_packet_data_extract_offset nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy

Kopiera paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kopierar informationen i det angivna paketet till ett eller flera nya paket som tilldelas från den angivna poolen. Om det lyckas returneras pekaren till det nya paketet i destinationen som **new_packet_ptr**.

### <a name="parameters"></a>Parametrar

- **packet_ptr** Pekare till käll paketet.
- **new_packet_ptr** Pekar till målet där pekaren återgår till den nya kopian av paketet.
- **pool_ptr** Visar en pekare till den tidigare skapade Packet-poolen som används för att allokera ett eller flera paket för kopian.
- **wait_option** Definierar hur tjänsten väntar om det inte finns några tillgängliga paket. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0x00) paket kopiering har slutförts.
- **NX_NO_PACKET** -paket (0x01) är inte tillgängligt för kopiering.
- **NX_INVALID_PACKET** (0X12) tomt käll paket eller kopia misslyckades.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_INVALID_PARAMETERSs** paket storlek (0X4D) stöder inte protokollet.
- **NX_PTR_ERROR** (0X07) ogiltig pool, paket eller destinations pekare.
- **NX_UNDERFLOW** (protokollnumret 0x02) ogiltig lägga pekare för paket.
- **NX_OVERFLOW** (0X03) ogiltig paket tilläggs pekare.
- **NX_CALLER_ERROR** (0X11) ett wait-alternativ angavs i initiering eller i en ISR.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate nx_packet_data_append,
- nx_packet_data_extract_offset nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append

Lägg till data i slutet av paketet

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till data i slutet av det angivna paketet. Det angivna data utrymmet kopieras till paketet. Om det inte finns tillräckligt med minne tillgängligt och funktionen länkat paket är aktive rad allokeras ett eller flera paket för att uppfylla begäran. Om funktionen för länkat paket inte är aktive rad returneras *NX_SIZE_ERROR* .

### <a name="parameters"></a>Parametrar

- **packet_ptr** Paket pekare.
- **data_start** Pekar till början av användarens data områden som ska läggas till i paketet.
- **data_size** Storlek på användarens data områden.
- **pool_ptr** Pekare till Packet bassäng från vilken du vill allokera ett annat paket om det inte finns tillräckligt med utrymme i det aktuella paketet.
- **wait_option** Definierar hur tjänsten fungerar om det inte finns några tillgängliga paket. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutfört paket tillägg.
- **NX_NO_PACKET** (0X01) inget paket tillgängligt.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till *tx_thread_wait_abort*.
- **NX_INVALID_PARAMETERSs** paket storlek (0X4D) stöder inte protokollet.
- **NX_UNDERFLOW** (protokollnumret 0x02) lägga-pekaren är mindre än start av nytto Last.
- **NX_OVERFLOW** (0X03) Lägg till-pekare är större än nytto Last slutet.
- **NX_PTR_ERROR** (0X07) ogiltig pool, paket eller data pekare.
- **NX_SIZE_ERROR** (0X09) ogiltig data storlek.
- **NX_CALLER_ERROR** (0X11) ogiltigt wait-alternativ från icke-tråd.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er (program nätverks driv rutiner)

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset

Extrahera data från paket via en förskjutning

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kopierar data från ett NetX-paket (eller paket kedja) som börjar vid den angivna förskjutningen från paketets lägga-pekare i byte till den angivna bufferten. Antalet byte som faktiskt kopieras returneras i *bytes_copied.* Den här tjänsten tar inte bort data från paketet eller justerar inte lägga-pekaren eller annan information om internt tillstånd.

### <a name="parameters"></a>Parametrar

- **packet_ptr** Pekare till paket att extrahera
- **förskjutning** Offset från den aktuella lägga-pekaren.
- **buffer_start** Pekare till början av Spara buffert
- **buffer_length** Antal byte som ska kopieras
- **bytes_copied** Antal byte som faktiskt har kopierats

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) paket kopiering har slutförts
- **NX_PACKET_OFFSET_ERROR** (0X53) ogiltigt offset-värde angavs
- **NX_PTR_ERROR** (0X07) ogiltig paket pekare eller buffert pekare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

Hämta data från paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kopierar data från det angivna paketet till den angivna bufferten. Det faktiska antalet kopierade byte returneras i målet som pekas av **bytes_copied**.

Observera att den här tjänsten inte ändrar paketets interna tillstånd. De data som hämtas är fortfarande tillgängliga i paketet.

*Måldomänkontrollanten måste vara tillräckligt stor för att rymma paketets innehåll. Om inte, kommer minnet att skadas orsaka oförutsägbara resultat.*

### <a name="parameters"></a>Parametrar

- **packet_ptr** Pekare till käll paketet.
- **buffer_start** Pekar till början av mellanlagringsområdet.
- **bytes_copied** Pekar mot målet för antalet kopierade byte.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) paket data hämtades.
- **NX_INVALID_PACKET** (0X12) ogiltigt paket.
- **NX_PTR_ERROR** (0X07) ogiltig paket, StartStart eller kopierade byte-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset nx_packet_length_get,
- nx_packet_pool_create nx_packet_pool_delete,
- nx_packet_pool_info_get nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get

Hämta längd på paket data

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar längden på data i det angivna paketet.

### <a name="parameters"></a>Parametrar

- **packet_ptr** Pekare till paketet.
- **längd** Mål för paketets längd.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset nx_packet_data_retrieve,
- nx_packet_pool_create nx_packet_pool_delete,
- nx_packet_pool_info_get nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create

Skapa en modempool i angivet minnes området

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en adresspool av den angivna paket storleken i det minnes utrymme som anges av användaren.

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till kontroll block för Packet-pool.
- **namn** Pekar till programmets namn för poolen.
- **payload_size** Antal byte i varje paket i poolen. Värdet måste vara minst 40 byte och måste också vara jämnt delbar med 4.
- **memory_ptr** Pekar på minnes området för att placera mediepoolen i. Pekaren ska vara justerad mot en ULONG-gränser.
- **memory_size** Storlek på poolens minnes området.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) en paket bassäng har skapats.
- **NX_PTR_ERROR** (0X07) ogiltig pool eller minnes pekare.
- **NX_SIZE_ERROR** (0X09) ogiltigt block eller minnes storlek.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,
- nx_packet_release nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

Ta bort tidigare skapade paket pool

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad paket pool. NetX söker efter trådar som för närvarande är inaktiverade på paket i modempoolen och rensar uppskjutningen.

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare för kontroll block för Packet-pool.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades ta bort paketets pool.
- **NX_PTR_ERROR** (0X07) ogiltig pool pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset nx_packet_data_retrieve,
- nx_packet_length_get nx_packet_pool_create,
- nx_packet_pool_info_get nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

Hämta information om en modempool

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om den angivna poolen.

*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till den tidigare skapade lagringspoolen.
- **total_packets** Pekare till målet för det totala antalet paket i poolen.
- **free_packets** Pekare till målet för det totala antalet paket som för närvarande är kostnads fria.
- **empty_pool_requests** Pekare till målet för det totala antalet tilldelnings begär anden när poolen var tom.
- **empty_pool_suspensions** Pekare till målet för det totala antalet avstängningar av tomma pooler.
- **invalid_packet_releases** Pekare till målet för det totala antalet ogiltiga paket utgåvor.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) information om hämtning av paket bassäng lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar och timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
    &total_packets,
    &free_packets,
    &empty_pool_requests,
    &empty_pool_suspensions,
    &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
    retrieved. */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset nx_packet_data_retrieve,
- nx_packet_length_get nx_packet_pool_create nx_packet_pool_delete
- nx_packet_release nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release

Frigör tidigare allokerat paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten frigör ett paket, inklusive eventuella ytterligare paket som är länkade till det angivna paketet. Om en annan tråd blockeras vid paket tilldelningen får den paketet och återupptas.

*Programmet måste förhindra att ett paket släpps mer än en gång, eftersom detta kan orsaka oförutsägbara resultat.*

### <a name="parameters"></a>Parametrar

- **packet_ptr** Paket pekare.


### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0x00) paket versionen har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig paket pekare.
- **NX_UNDERFLOW** (protokollnumret 0x02) lägga-pekaren är mindre än start av nytto Last.
- **NX_OVERFLOW** (0X03) Lägg till-pekare är större än nytto Last slutet.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er (program nätverks driv rutiner)

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

Frisläpp ett överfört paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Beskrivning

För icke-TCP-paket släpper den här tjänsten ett överfört paket, inklusive eventuella ytterligare paket som är länkade till det angivna paketet. Om en annan tråd blockeras vid paket tilldelningen får den paketet och återupptas. För ett överfört TCP-paket markeras paketet som överfört, men släpps inte till paketet. Den här tjänsten kallas vanligt vis för programmets nätverks driv rutin när ett paket har överförts.

*Nätverks driv rutinen bör ta bort det fysiska medie huvudet och justera Paketets längd innan du anropar den här tjänsten.*

### <a name="parameters"></a>Parametrar

- **packet_ptr** Paket pekare.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) utgåva av överförings paket lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig paket pekare.
- **NX_UNDERFLOW** (protokollnumret 0x02) lägga-pekaren är mindre än start av nytto Last.
- **NX_OVERFLOW** (0X03) Lägg till-pekare är större än nytto Last slutet.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers, program nätverks driv rutiner (inklusive ISR: er)

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable

Inaktivera RARP (reverse Address Resolution Protocol)

### <a name="prototype"></a>Prototyp

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar RARP-komponenten för NetX för den angivna IP-instansen. För ett multihome-system inaktiverar den här tjänsten RARP på alla gränssnitt.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) RARP-inaktive ras.
- **NX_NOT_ENABLED** (0X14) RARP har inte Aktiver ATS.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a>Se även

- nx_rarp_enable nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable

Aktivera omvänt adress matchnings protokoll (RARP)

### <a name="prototype"></a>Prototyp

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar RARP-komponenten för NetX för den angivna IP-instansen. RARP-komponenterna söker igenom alla anslutna nätverks gränssnitt för noll IP-adress. En noll-IP-adress anger att gränssnittet inte har IP-adresstilldelning ännu. RARP försöker matcha IP-adressen genom att aktivera RARP-processen på det gränssnittet.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) RARP aktivera har slutförts.
- **NX_IP_ADDRESS_ERROR** (0x21) IP-adressen är redan giltig.
- **NX_ALREADY_ENABLED** (0X15) RARP har redan Aktiver ATS.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a>Se även

- nx_rarp_disable nx_rarp_info_get

## <a name="nx_rarp_info_get"></a>nx_rarp_info_get

Hämta information om RARP-aktiviteter

### <a name="prototype"></a>Prototyp

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om RARP-aktiviteter för den angivna IP-instansen.

*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **rarp_requests_sent** Pekare till målet för det totala antalet RARP-begäranden som skickats.
- **rarp_responses_received** Pekare till målet för det totala antalet RARP-svar som tagits emot.
- **rarp_invalid_messages** Pekare till målet för det totala antalet ogiltiga meddelanden.


### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0X00) lyckad RARP information hämtning.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a>Se även

- nx_rarp_disable nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize

Initiera NetX-system

### <a name="prototype"></a>Prototyp

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar de grundläggande NetX system resurserna som förberedelse för användning. Den ska anropas av programmet under initieringen och innan något annat NetX-anrop görs.

### <a name="parameters"></a>Parametrar

Ingen

### <a name="return-values"></a>Retur värden

Inget

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers, ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,
- nx_ip_forwarding_enable nx_ip_fragment_disable,
- nx_ip_fragment_enable nx_ip_info_get nx_ip_status_check

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

Bind klient TCP-socket till TCP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten binder den tidigare skapade TCP-klientcachen till den angivna TCP-porten. Giltiga TCP-Sockets sträcker sig från 0 till 0xFFFF. Om den angivna TCP-porten inte är tillgänglig pausas tjänsten enligt det angivna vänte alternativet.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade TCP-socket-instansen.
- **port** Port nummer att binda (1 till 0xFFFF). Om Port numret är NX_ANY_PORT (0x0000) kommer IP-instansen att söka efter nästa lediga port och använda den för bindningen.
- **wait_option** Definierar hur tjänsten beter sig om porten redan är kopplad till en annan socket. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) socket-bindning.
- **NX_ALREADY_BOUND** (0X22) den här socketen är redan kopplad till en annan TCP-port.
- **NX_PORT_UNAVAILABLE** -porten (0x23) är redan kopplad till en annan socket.
- **NX_NO_FREE_PORTS** (0X45) ingen kostnads fri port.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till *tx_thread_wait_abort*.
- **NX_INVALID_PORT** (0X46) ogiltig port.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_connect nx_tcp_client_socket_port_get,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available nx_tcp_socket_create,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

Anslut klientens TCP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ansluter den tidigare skapade och kopplade TCP-klientens socket till den angivna serverns port. Giltiga TCP server-portar är mellan 0 och 0xFFFF. Om anslutningen inte slutförs omedelbart pausas tjänsten enligt det angivna vänte alternativet.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade TCP-socket-instansen.
- **server_ip** Serverns IP-adress.
- **SERVER_PORT** Server port nummer att ansluta till (1 till 0xFFFF).
- **wait_option** Definierar hur tjänsten fungerar när anslutningen upprättas. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) anslutningen lyckades.
- **NX_NOT_BOUND** -socketen (0x24) är inte kopplad.
- **NX_NOT_CLOSED** -socketen (0x35) är inte i ett stängt tillstånd.
- **NX_IN_PROGRESS** (0X37) ingen väntan angavs, anslutnings försöket pågår.
- **NX_INVALID_INTERFACE** (0X4C) ogiltigt gränssnitt har angetts.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig Server-IP-adress.
- **NX_INVALID_PORT** (0X46) ogiltig port.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_port_get,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available nx_tcp_socket_create,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

Hämta port nummer kopplat till klienten TCP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det port nummer som är associerat med socketen, vilket är användbart för att hitta den port som allokerats av NetX i situationer där NX_ANY_PORT angavs vid den tidpunkt då socketen var kopplad.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade TCP-socket-instansen.
- **port_ptr** Pekare till målet för retur port numret. Giltiga port nummer är (1 till 0xFFFF).

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) socket-bindning.
- **NX_NOT_BOUND** (0X24) den här socketen är inte kopplad till någon port.
- **NX_PTR_ERROR** (0X07) ogiltig socket pekare eller port retur pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available nx_tcp_socket_create,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

Bind TCP-klientens socket från TCP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten frigör bindningen mellan TCP-klientens socket och en TCP-port. Om det finns andra trådar som väntar på att binda en annan socket till samma port nummer, binds den första pausade tråden till den här porten.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade TCP-socket-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) uppkopplad socket-bindning.
- **NX_NOT_BOUND** -socketen var inte kopplad till någon port.
- **NX_NOT_CLOSED** -socketen (0x35) har inte kopplats från.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available nx_tcp_socket_create,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_enable"></a>nx_tcp_enable

Aktivera TCP-komponenten NetX

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar Transmission Control Protocol-komponenten (TCP) i NetX. När den har Aktiver ATS kan TCP-anslutningar upprättas av programmet.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) TCP-aktivering har slutförts.
- **NX_ALREADY_ENABLED** (0X15) TCP har redan Aktiver ATS.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available nx_tcp_socket_create,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

Hitta nästa tillgängliga TCP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker hitta en kostnads fri TCP-port (obunden) med början från appens angivna port. Sök logiken kommer att figursättas runt om sökningen sker för att uppnå det högsta port svärdet för 0xFFFF. Om sökningen lyckas returneras den kostnads fria porten i variabeln som pekar på *free_port_ptr*.

*Den här tjänsten kan anropas från en annan tråd och har samma port returnerad. För att förhindra det här konkurrens tillståndet kanske programmet vill placera den här tjänsten och det faktiska klient-socket-bindningen under skyddet av en mutex.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **port** Port nummer för att starta sökningen vid (1 till 0xFFFF).
- **free_port_ptr** Pekar till målets lediga port retur värde.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) den kostnads fria porten hittades.
- **NX_NO_FREE_PORTS** (0X45) inga lediga portar hittades.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.
- **NX_INVALID_PORT** (0X46) det angivna port numret är ogiltigt.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available nx_tcp_socket_create,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get

Hämta information om TCP-aktiviteter

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om TCP-aktiviteter för den angivna IP-instansen.

*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **tcp_packets_sent** Pekare till målet för det totala antalet skickade TCP-paket.
- **tcp_bytes_sent** Pekare till målet för det totala antalet TCP-byte som har skickats.
- **tcp_packets_received** Pekare till målet för det totala antalet mottagna TCP-paket.
- **tcp_bytes_received** Pekare till målet för det totala antalet mottagna TCP-byte.
- **tcp_invalid_packets** Pekare till målet för det totala antalet ogiltiga TCP-paket.
- **tcp_receive_packets_dropped** Pekare till målet för det totala antalet TCP-mottagna paket som har tagits bort.
- **tcp_checksum_errors** Pekare till målet för det totala antalet TCP-paket med fel kontroll summor.
- **tcp_connections** Pekare till målet för det totala antalet TCP-anslutningar.
- **tcp_disconnections** Pekare till målet för det totala antalet TCP-anslutningar.
- **tcp_connections_dropped** Pekare till målet för det totala antalet avbrutna TCP-anslutningar.
- **tcp_retransmit_packets** Pekare till målet för det totala antalet återsända TCP-paket.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad hämtning av TCP-information.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
status = nx_tcp_info_get(&ip_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_invalid_packets,
    &tcp_receive_packets_dropped,
    &tcp_checksum_errors,
    &tcp_connections,
    &tcp_disconnections
    &tcp_connections_dropped,
    &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available nx_tcp_socket_create,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

Acceptera TCP-anslutning

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten accepterar (eller förbereder att godkänna) en begäran om TCP-anslutning till Socket för en port som tidigare har kon figurer ATS för lyssning. Den här tjänsten kan anropas omedelbart när programmet anropar lyssnings-eller återlyssnar-tjänsten, eller efter att lyssnings rutinen för lyssning anropas när klient anslutningen faktiskt finns. Om en anslutning inte kan upprättas direkt, pausas tjänsten enligt det angivna vänte alternativet.

*Programmet måste anropa **nx_tcp_server_socket_unaccept** när anslutningen inte längre behövs för att ta bort Server socketens bindning till Server porten.*

*Rutinen för återanrop av program anropas inifrån IP: s hjälp tråd.*

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekar mot TCP-serverns socket Control-Block.
- **wait_option** Definierar hur tjänsten fungerar när anslutningen upprättas. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)


### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0X00) lyckad TCP-server-socket acceptera (passiv anslutning).
- **NX_NOT_LISTEN_STATE** (0X36) den angivna Server-socketen är inte i ett lyssnings tillstånd.
- **NX_IN_PROGRESS** (0X37) ingen väntan angavs, anslutnings försöket pågår.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till *tx_thread_wait_abort*.
- **NX_PTR_ERROR** (0X07) socket Point-fel.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;
    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
                message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
            again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available nx_tcp_socket_create,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

Aktivera lyssning för klient anslutning på TCP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a>Beskrivning

Med den här tjänsten kan du lyssna efter en klient anslutnings förfrågan på den angivna TCP-porten. När en begäran om klient anslutning tas emot binds den angivna Server sockeln till den angivna porten och den angivna funktionen för lyssnings motringning anropas.

Bearbetningen av lyssnings rutinen för lyssning är helt upp i programmet. Den kan innehålla logik för att väcka en program tråd som sedan utför en acceptera-åtgärd. Om programmet redan har en tråd inaktive rad för accepterad bearbetning för den här socketen kanske inte rutinen för lyssnings anrop behövs.

Om programmet vill hantera ytterligare klient anslutningar på samma port måste ***nx_tcp_server_socket_relisten*** anropas med en tillgänglig socket (en socket i stängt tillstånd) för nästa anslutning. Ytterligare klient anslutningar köas tills tjänsten relistener anropas. När det maximala ködjup överskrids, släpps den äldsta anslutningsbegäran i stället för att köa den nya anslutningsbegäran. Det maximala ködjup anges av den här tjänsten.

*Rutinen för återanrop av program anropas från den interna IP-hjälpen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **port** Port nummer att lyssna på (1 till 0xFFFF).
- **socket_ptr** Pekare till Socket som ska användas för anslutningen.
- **listen_queue_size** Antal klient anslutnings begär Anden som kan köas.
- **listen_callback** Program funktion som anropas när anslutningen tas emot. Om du anger ett NULL-värde är funktionen lyssnande motringning inaktive rad.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckade TCP-ports lyssning.
- **NX_MAX_LISTEN** (0X33) inga fler lyssnar begär ande strukturer är tillgängliga. Konstanten NX_MAX_LISTEN_REQUESTS i nx_api. h definierar hur många aktiva lyssnings begär Anden som är möjliga.
- **NX_NOT_CLOSED** (0X35) den angivna Server socketen är inte i ett stängt tillstånd.
- **NX_ALREADY_BOUND** (0X22) den angivna Server socketen är redan kopplad till en port.
- **NX_DUPLICATE_LISTEN** (0X34) det finns redan en aktiv avlyssnings förfrågan för den här porten.
- **NX_INVALID_PORT** (0X46) ogiltig Port har angetts.
- **NX_PTR_ERROR** (0X07) ogiltig IP-eller socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket.
        This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created
        and the link is enabled "my_pool" packet pool has already
        been created.
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
        Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

    /* Wait for 200 ticks for the client socket connection
        to complete. */
    status = nx_tcp_server_socket_accept(&server_socket, 200);

    /* Check for a successful connection. */
    if (status == NX_SUCCESS)
    {
        /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
        nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
            NX_WAIT_FOREVER);

        /* Place "Hello_and_Goodbye" in the packet. */
        nx_packet_data_append(my_packet, "Hello_and_Goodbye",
            sizeof("Hello_and_Goodbye"),
            &my_pool,
            NX_WAIT_FOREVER);

        /* Send "Hello_and_Goodbye" to client. */
        nx_tcp_socket_send(&server_socket, my_packet, 200);

        /* Check for an error. */
        if (status)
        {
            /* Error, release the packet. */
            nx_packet_release(my_packet);
        }
        /* Now disconnect the server socket from the client. */
        nx_tcp_socket_disconnect(&server_socket, 200);
    }

    /* Unaccept the server socket. Note that unaccept is called
        even if disconnect or accept fails. */
    nx_tcp_server_socket_unaccept(&server_socket);

    /* Setup server socket for listening with this socket
    again. */
    nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
}

/* We are now done so unlisten on server port 12. */
nx_tcp_server_socket_unlisten(&my_ip, 12);

/* Delete the server socket. */
nx_tcp_socket_delete(&server_socket);
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available nx_tcp_socket_create,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

Lyssna efter klient anslutning på TCP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anropas efter att en anslutning har tagits emot på en port som tidigare har kon figurer ATS för lyssning. Huvud syftet med den här tjänsten är att tillhandahålla en ny server-socket för nästa klient anslutning. Om en anslutningsbegäran är i kö kommer anslutningen att bearbetas omedelbart under det här tjänst anropet.

*Samma återanrops rutin som anges av den ursprungliga lyssnar förfrågan kallas även när det finns en anslutning för denna nya server-socket.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **port** Port nummer att lyssna på igen (1 till 0xFFFF).
- **socket_ptr** Socket som ska användas för nästa klient anslutning.

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0X00) lyckade TCP-port-lyssna igen.
- **NX_NOT_CLOSED** (0X35) den angivna Server socketen är inte i ett stängt tillstånd.
- **NX_ALREADY_BOUND** (0X22) den angivna Server socketen är redan kopplad till en port.
- **NX_INVALID_RELISTEN** (0X47) det finns redan en giltig socket-pekare för den här porten, eller så har den angivna porten ingen avlyssnings förfrågan aktiv.
- **NX_CONNECTION_PENDING** (0X48) samma som NX_SUCCESS, förutom att det fanns en köade anslutningsbegäran och bearbetades under det här anropet.
- **NX_INVALID_PORT** (0X46) ogiltig Port har angetts.
- **NX_PTR_ERROR** (0X07) ogiltig IP-eller lyssnande återanrops pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
    }

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
    "port_12_semaphore" has already been created with an initial
        count of 0.
        "my_ip" has already been created and the link is enabled.
        "my_pool" packet pool has already been created. */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);
    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
        complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is
        called even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
        again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept nx_tcp_server_socket_listen,
- nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available nx_tcp_socket_create,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

Ta bort socket-associationen med lyssnings porten

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort associationen mellan denna server-socket och den angivna Server porten. Programmet måste anropa tjänsten efter en från koppling eller efter ett misslyckat accept-anrop.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till tidigare konfigurerad server-socket-instans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad Server-socket accepterades inte.
- **NX_NOT_LISTEN_STATE** (0x36)-serverns socket är i ett felaktigt tillstånd och är förmodligen inte frånkopplad.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
        */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request
            is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet,
                "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called even
            if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

Inaktivera lyssning för klient anslutning på TCP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
```

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar avlyssningen av en klient anslutnings förfrågan på den angivna TCP-porten.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **port** Antal portar för att inaktivera lyssning (0 till 0xFFFF).

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) TCP-lyssning har inaktiverats.
- Lyssning för **NX_ENTRY_NOT_FOUND** (0x16) har inte Aktiver ATS för den angivna porten.
- **NX_INVALID_PORT** (0X46) ogiltig Port har angetts.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request is
            present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"), &my_pool,
                NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }
            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }
        /* Unaccept the server socket. Note that unaccept is called even if
        disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,
- nx_tcp_socket_bytes_available nx_tcp_socket_create,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

Hämtar antalet byte som är tillgängliga för hämtning

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar antalet byte som är tillgängliga för hämtning i den angivna TCP-socketen. Observera att TCP-socketen måste vara ansluten.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till tidigare skapad och ansluten TCP-socket.
- **bytes_available** Pekare till målet för tillgängliga byte.

### <a name="return-values"></a>Retur värden

- Tjänsten **NX_SUCCESS** (0x00) har körts. Antalet byte som är tillgängliga för läsning returneras till anroparen.
- **NX_NOT_CONNECTED** -socketen (0x38) är inte i ett anslutet tillstånd.
- **NX_PTR_ERROR** (0X07) ogiltiga pekare.
- **NX_NOT_ENABLED** (0X14) TCP är inte aktiverat.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten nx_tcp_socket_create,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

Skapa TCP-klient eller Server-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en TCP-klient eller Server-socket för den angivna IP-instansen.

*Rutinen för återanrop av program anropas från tråden som är kopplad till den här IP-instansen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **socket_ptr** Pekare till nytt TCP socket Control-Block.
- **namn** Programmets namn för denna TCP-socket.
- **type_of_service** Definierar typ av tjänst för överföringen, de juridiska värdena är följande:

- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)

- **fragment**  Anger om IP-fragmentering tillåts eller inte. Om NX_FRAGMENT_OKAY (0x0) anges tillåts IP-fragmentering. Om NX_DONT_FRAGMENT (0x4000) anges inaktive ras IP-fragmentering.
- **time_to_live** Anger det 8-bitars värde som definierar hur många routrar det här paketet kan passera innan det utlöses. Standardvärdet anges av NX_IP_TIME_TO_LIVE.
- **window_size** Definierar det maximala antalet byte som tillåts i mottagnings kön för denna socket
- **urgent_data_callback** Programfunktion som anropas när brådskande data identifieras i Receive-dataströmmen. Om det här värdet är NX_NULL ignoreras brådskande data.
- **disconnect_callback** Program funktion som anropas när en från koppling utfärdas av socketen i den andra änden av anslutningen. Om det här värdet är NX_NULL inaktive ras funktionen för motringning.

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0X00) TCP-klient-socket har skapats.
- **NX_OPTION_ERROR** (0X0a) ogiltigt alternativ för typ av tjänst, fragment, ogiltig fönster storlek eller tid tolive.
- **NX_PTR_ERROR** (0X07) ogiltig IP-eller socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Create a TCP client socket on the previously created IP instance,
    with normal delivery, IP fragmentation enabled, 0x80 time to
    live, a 200-byte receive window, no urgent callback routine, and
    the "client_disconnect" routine to handle disconnection initiated
    from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
    "Client Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY,
    0x80, 200, NX_NULL
    client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
    to be bound. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,
- nx_tcp_socket_delete nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

Ta bort TCP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad TCP-socket. Om socketen fortfarande är bunden eller ansluten, returnerar tjänsten en felkod.

### <a name="parameters"></a>Parametrar

- **socket_ptr** TCP-socket har skapats tidigare

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) ta bort socket.
- Det gick inte att skapa **NX_NOT_CREATED** (0X27) socket.
- **NX_STILL_BOUND** (0X42) socket är fortfarande kopplad.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,
- nx_tcp_socket_create nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

Koppla från klient-och Server anslutningar

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kopplar från en upprättad klient eller Server-socket-anslutning. En från koppling av en server-socket bör följas av en begäran om att ta emot begäran, medan en klient-socket som är frånkopplad är kvar i ett tillstånd som är redo för en annan anslutningsbegäran. Om från kopplings processen inte kan slutföras omedelbart pausas tjänsten enligt det angivna vänte alternativet.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare anslutna klienten eller Server-socket-instansen.
- **wait_option** Definierar hur tjänsten fungerar när från koppling pågår. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades socket från kopplingen.
- **NX_NOT_CONNECTED** (0x38) den angivna socketen är inte ansluten.
- **NX_IN_PROGRESS** (0x37) från koppling pågår, ingen väntan har angetts.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,
- nx_tcp_socket_receive nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify

Installera TCP från koppling Slutför meddela motringning

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar en callback-funktion som anropas när en socket-från koppling har slutförts. Callback-funktionen för att koppla från TCP socket är tillgänglig om NetX har skapats med alternativet

- ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definierats.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare anslutna klienten eller Server-socket-instansen.
- **tcp_disconnect_complete_notify** Motringningsfunktionen som ska installeras.

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0x00) registrerade återanrops funktionen.
- **NX_NOT_SUPPORTED** (0x4B) funktionen för utökad avisering är inte inbyggd i netx-biblioteket
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) TCP-funktionen är inte aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a>Se även

- nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,
- nx_tcp_socket_mss_get nx_tcp_socket_mss_peer_get,
- nx_tcp_socket_mss_set nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify

Ange TCP-upprättning av funktionen meddela motringning

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar en callback-funktion som anropas när en TCP-socket upprättar en anslutning. TCP-socketen för att skapa en motringning är tillgänglig om NetX har skapats med alternativet ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definierat.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare anslutna klienten eller Server-socket-instansen.
- **tcp_establish_notify** Callback-funktionen anropas efter att en TCP-anslutning har upprättats.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett funktionen notify.
- **NX_NOT_SUPPORTED** (0x4B) funktionen för utökad avisering är inte inbyggd i netx-biblioteket
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) TCP har inte Aktiver ATS av programmet.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a>Se även

- nx_tcp_enable nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

Hämta information om TCP-socket-aktiviteter

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om TCP-socket-aktiviteter för den angivna TCP socket-instansen.

*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade TCP-socket-instansen.
- **tcp_packets_sent** Pekare till målet för det totala antalet TCP-paket som skickats på socket.
- **tcp_bytes_sent** Pekare till målet för det totala antalet TCP-byte som skickats på socket.
- **tcp_packets_received** Pekare till målet för det totala antalet TCP-paket som tagits emot på socket.
- **tcp_bytes_received** Pekare till målet för det totala antalet TCP-byte som tagits emot vid socket.
- **tcp_retransmit_packets** Pekare till målet för det totala antalet återöverföringar av TCP-paket.
- **tcp_packets_queued** Pekare till målet för det totala antalet köade TCP-paket på socket.
- **tcp_checksum_errors** Pekare till målet för det totala antalet TCP-paket med fel kontroll summor på socket.
- **tcp_socket_state** Pekare till målet för socketens aktuella tillstånd.
- **tcp_transmit_queue_depth** Pekare till målet för det totala antalet överförings paket som fortfarande står i kö i väntan på bekräftelse.
- **tcp_transmit_window** Pekare till målet för den aktuella överförings fönster storleken.
- **tcp_receive_window** Pekare till målet för den aktuella storleken för mottagnings fönster.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades Hämta TCP-socket-information.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="return-values"></a>Retur värden

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_receive nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

Hämta MSS för socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den angivna socketens lokala maximala segment storlek (MSS).

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade socketen.
- **MSS** Mål för returnerad MSS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) godkänd MSS Hämta.
- **NX_PTR_ERROR** (0X07) ogiltig mål pekare för socket eller MSS.
- **NX_NOT_ENABLED** (0X14) TCP är inte aktiverat.
- **NX_CALLER_ERROR** (0X11) anroparen är inte en tråd eller initiering.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a>Se även

- nx_tcp_enable nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify nx_tcp_socket_mss_peer_get,
- nx_tcp_socket_mss_set nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

Hämta MSS för peer TCP-socketen

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den maximala segment storleken (MSS) som annonseras av peer-socketen.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till tidigare skapad och ansluten socket.
- **MSS** Mål för att returnera MSS.


### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad peer-MSS Hämta.
- **NX_PTR_ERROR** (0X07) ogiltig mål pekare för socket eller MSS.
- **NX_NOT_ENABLED** (0X14) TCP är inte aktiverat.
- **NX_CALLER_ERROR** (0X11) anroparen är inte en tråd eller initiering.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a>Se även

- nx_tcp_enable nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_set nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

Ange MSS för socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger den angivna socketens största segment storlek (MSS). Observera att MSS-värdet måste ligga inom nätverks gränssnittets IP-MTU, vilket ger utrymme för IP-och TCP-huvuden.

Den här tjänsten ska användas innan en TCP-socket startar anslutnings processen. Om tjänsten används när en TCP-anslutning har upprättats har det nya värdet ingen påverkan på anslutningen.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade socketen.
- **MSS** Värdet för MSS som ska anges.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) godkänd MSS-uppsättning.
- Det angivna MSS-värdet för **NX_SIZE_ERROR** (0x09) är för stort.
- **NX_NOT_CONNECTED** (0X38) TCP-anslutning har inte upprättats
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_NOT_ENABLED** (0X14) TCP är inte aktiverat.
- **NX_CALLER_ERROR** (0X11) anroparen är inte en tråd eller initiering.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>Se även

- nx_tcp_enable nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

Hämta information om peer TCP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om peer-IP-adress och port för den anslutna TCP-socketen över IP-nätverket.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade TCP-socketen.
- **peer_ip_address** Pekare till mål för peer-IP-adress i byte ordning för värden.
- **peer_port** Pekar till mål för peer-portnummer i byte ordning för värden.

### <a name="return-values"></a>Retur värden

- Tjänsten **NX_SUCCESS** (0x00) har körts. Peer-IP-adress och port nummer returneras till anroparen.
- **NX_NOT_CONNECTED** -socketen (0x38) är inte i ett anslutet tillstånd.
- **NX_PTR_ERROR** (0X07) ogiltiga pekare.
- **NX_NOT_ENABLED** (0X14) TCP är inte aktiverat.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a>Se även

- nx_tcp_enable nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get nx_tcp_socket_mss_set,
- nx_tcp_socket_receive_notify nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

Ta emot data från TCP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar emot TCP-data från den angivna socketen. Om inga data har placerats i kö på den angivna socketen, pausas anroparen utifrån det angivna wait-alternativet.

*Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade TCP-socket-instansen.
- **packet_ptr** Pekare till TCP-paketfiltrering.
- **wait_option** Definierar hur tjänsten beter sig om inga data är köade på denna socket. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0X00) lyckades ta emot socket-data.
- **NX_NOT_BOUND** (0x24)-socketen är inte kopplad än.
- **NX_NO_PACKET** (0X01) inga data togs emot.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_NOT_CONNECTED** (0x38) socketen är inte längre ansluten.
- **NX_PTR_ERROR** (0X07) ogiltig socket eller RETUR paket pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

/* Ta emot ett paket från den tidigare skapade och anslutna TCP-klientens socket. Om det inte finns något paket tillgängligt väntar du tills 200 timer-Tick innan du får upp. */status = nx_tcp_socket_receive (&client_socket &packet_ptr 200);

/* Om status är NX_SUCCESS kommer det mottagna paketet att pekas av "packet_ptr". */

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

Meddela program om mottagna paket


### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Beskrivning

Den här tjänsten konfigurerar funktionen ta emot aviserings funktion med återanrops funktionen som anges av programmet. Den här återanrops funktionen anropas sedan när ett eller flera paket tas emot på socketen. Om en NX_NULL-pekare har angetts inaktive ras funktionen notify.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till TCP-socketen.
- **tcp_receive_notify** Funktionen motringning till program som anropas när ett eller flera paket tas emot på socketen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad socket Receive-avisering.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) TCP-funktionen är inte aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a>Se även

- nx_tcp_enable nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

Skicka data via en TCP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar TCP-data via en tidigare ansluten TCP-socket. Om mottagarens senaste annonserade fönster storlek är mindre än den här begäran, så pausas tjänsten om den inte har angetts. Den här tjänsten garanterar att inga paket data som är större än MSS skickas till IP-skiktet.

*Om ett fel returneras ska programmet inte släppa paketet efter det här anropet. Om du gör det kan det orsaka oförutsägbara resultat, eftersom nätverks driv rutinen även försöker frigöra paketet efter överföringen.*

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare anslutna TCP-socket-instansen.
- **packet_ptr** TCP data paket pekare.
- **wait_option** Definierar hur tjänsten fungerar om begäran är större än mottagarens fönster storlek. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) skickade socket-sändning.
- **NX_NOT_BOUND** -socketen var inte kopplad till någon port.
- **NX_NO_INTERFACE_ADDRESS** (0X50) inget lämpligt utgående gränssnitt hittades.
- **NX_NOT_CONNECTED** -socketen (0x38) är inte längre ansluten.
- **NX_WINDOW_OVERFLOW** -begäran (0x39) är större än mottagarens annonserade fönster storlek i byte.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_INVALID_PACKET** -paketet (0x12) har inte allokerats.
- **NX_TX_QUEUE_DEPTH** (0X49) högsta tillåtna djup för överförings kön har uppnåtts.
- **NX_OVERFLOW** (0X03) paket tilläggs pekare är ogiltig.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.
- **NX_UNDERFLOW** (protokollnumret 0x02) paket lägga pekare är ogiltig.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_state_wait

### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

Vänta tills TCP-socketen har angett ett angivet tillstånd

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a>Beskrivning

Den här tjänsten väntar på att socketen ska ange önskat tillstånd. Om socketen inte har önskat tillstånd pausas tjänsten enligt det angivna wait-alternativet.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare anslutna TCP-socket-instansen.
- **desired_state** Önskat TCP-tillstånd. Giltiga TCP-socket-tillstånd definieras enligt följande:
- NX_TCP_CLOSED (0x01)
- NX_TCP_LISTEN_STATE (protokollnumret 0x02)
- NX_TCP_SYN_SENT (0x03)
- NX_TCP_SYN_RECEIVED (0x04)
- NX_TCP_ESTABLISHED (0x05)
- NX_TCP_CLOSE_WAIT (0x06)
- NX_TCP_FIN_WAIT_1 (0x07)
- NX_TCP_FIN_WAIT_2 (0x08)
- NX_TCP_CLOSING (0x09)
- NX_TCP_TIMED_WAIT (0x0A)
- NX_TCP_LAST_ACK (0x0B)
- **wait_option** Definierar hur tjänsten fungerar om det begärda läget inte finns. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0x00) tillstånd väntar.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_NOT_SUCCESSFUL** (0X43) status finns inte inom angiven vänte tid.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.
- **NX_OPTION_ERROR** (0X0a) det önskade socket-läget är ogiltigt.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback

Installera motringning för vänte läge med vänte tid

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar en callback-funktion som anropas när TCP-socketen är i vänte läge. Om du vill använda den här tjänsten måste NetX-biblioteket skapas med alternativet ***NX_ENABLE_EXTENDED_NOTIFY*** definierat.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare anslutna klienten eller Server-socket-instansen.
- **tcp_timed_wait_callback** Funktionen vänte tid för motringning

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) registrerar återanrops funktionens socket
- **NX_NOT_SUPPORTED** (0X4B) netx-biblioteket har skapats utan den utökade meddelande funktionen aktive rad.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) TCP-funktionen är inte aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>Se även

- nx_tcp_enable nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get nx_tcp_socket_receive_notify,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

Konfigurera överförings parametrar för socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```

### <a name="description"></a>Beskrivning

Den här tjänsten konfigurerar olika överförings parametrar för den angivna TCP-socketen.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till TCP-socketen.
- **max_queue_depth** Högsta antal paket som får placeras i kö för överföring.
- **tids gräns** Antal ThreadX timer-Tick som en ACK väntar innan paketet skickas igen.
- **max_retries** Maximalt antal tillåtna försök.
- **timeout_shift** Värde för att skifta tids gränsen för varje efterföljande försök. Värdet 0, resulterar i samma tids gräns mellan efterföljande försök. Värdet 1, dubblar tids gränsen mellan återförsök.

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0x00) konfiguration av överförings-socket har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_OPTION_ERROR** (0X0a) ogiltigt ködjup-alternativ.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) TCP-funktionen är inte aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a>Se även

- nx_tcp_enable nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set

Meddela programmet om uppdateringar av fönster storlek

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Beskrivning

Den här tjänsten installerar ett socket-fönster uppdatera motringning. Den här rutinen anropas automatiskt när den angivna socketen tar emot ett paket som anger en ökning av fönster storleken för fjärrvärden.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade TCP-socketen.
- **tcp_window_update_notify** Callback-rutin som anropas när fönstrets storlek ändras. Värdet NULL inaktiverar uppdatering av fönster ändringar.

### <a name="return-values"></a>Retur värden
- **NX_SUCCESS** (0x00) återanrops rutinen är installerad på socketen.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0X07) ogiltiga pekare.
- **NX_NOT_ENABLED** (0X14) TCP-funktionen är inte aktive rad.


### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a>Se även

- nx_tcp_enable nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable

Aktivera UDP-komponenten för NetX

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar UDP-komponenten (User Datagram Protocol) i NetX. När den har Aktiver ATS kan UDP-datagram skickas och tas emot av programmet.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad UDP-aktivering.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_ALREADY_ENABLED** (0X15) den här komponenten har redan Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a>Se även

- nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,
- nx_udp_socket_bind nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive,
- nx_udp_socket_receive_notify nx_udp_socket_send,
- nx_udp_socket_interface_send nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

Hitta nästa tillgängliga UDP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten söker efter en kostnads fri UDP-port (obunden) med början från det angivna port numret för programmet. Sök logiken kommer att figursättas runt om sökningen når det högsta port svärdet för 0xFFFF. Om sökningen lyckas returneras den kostnads fria porten i variabeln som pekar på *free_port_ptr*.

*Den här tjänsten kan anropas från en annan tråd och kan ha samma port som returneras. För att förhindra det här konkurrens tillståndet kanske programmet vill placera den här tjänsten och faktiskt socket-bindning under skyddet av en mutex.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **port** Port nummer för att starta sökning (1 till 0xFFFF).
- **free_port_ptr** Pekar på den lediga portens retur variabel.


### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) den kostnads fria porten hittades.
- **NX_NO_FREE_PORTS** (0X45) inga lediga portar hittades.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.
- **NX_INVALID_PORT** (0x46) det angivna port numret är ogiltigt.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,
- nx_udp_socket_bind nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive,
- nx_udp_socket_receive_notify nx_udp_socket_send,
- nx_udp_socket_interface_send nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get

Hämta information om UDP-aktiviteter

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om UDP-aktiviteter för den angivna IP-instansen.

*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **udp_packets_sent** Pekare till målet för det totala antalet skickade UDP-paket.
- **udp_bytes_sent** Pekare till målet för det totala antalet UDP-byte som har skickats.
- **udp_packets_received** Pekare till målet för det totala antalet mottagna UDP-paket.
- **udp_bytes_received** Pekare till målet för det totala antalet mottagna UDP-byte.
- **udp_invalid_packets** Pekare till målet för det totala antalet ogiltiga UDP-paket.
- **udp_receive_packets_dropped** Pekare till målet för det totala antalet mottagna UDP-paket.
- **udp_checksum_errors** Pekare till målet för det totala antalet UDP-paket med fel kontroll summor.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades hämtning av UDP-information.
- **NX_PTR_ERROR** (0X07) ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.


### <a name="allowed-from"></a>Tillåten från

Initiering, trådar och timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_invalid_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,
- nx_udp_socket_bind nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive,
- nx_udp_socket_receive_notify nx_udp_socket_send,
- nx_udp_socket_interface_send nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract

Extrahera nätverks parametrar från UDP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten extraherar nätverks parametrar, till exempel IP-adress, peer-portnummer, protokoll typ (den här tjänsten returnerar alltid UDP-typ) från ett paket som tas emot i ett inkommande gränssnitt.

### <a name="parameters"></a>Parametrar

- **packet_ptr** Pekar mot paket.
- **ip_address** Pekare till avsändar-IP-adress.
- **protokoll** Pekare till protokoll (UDP).
- **port** Pekare till avsändarens port nummer.
- **interface_index** Pekare för att ta emot gränssnitts index.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) paket gränssnitts data har extraherats.
- **NX_INVALID_PACKET** -paketet (0x12) innehåller inte någon IP-ram.
- **NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_socket_bind nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive,
- nx_udp_socket_receive_notify nx_udp_socket_send,
- nx_udp_socket_interface_send nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

Bind UDP-socket till UDP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten binder den tidigare skapade UDP-socketen till den angivna UDP-porten. Giltiga UDP-socketar sträcker sig från 0 till 0xFFFF. Om det begärda port numret är kopplat till en annan socket, väntar den här tjänsten på den angivna tids perioden för att socketen ska kunna bindas från Port numret.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade UDP-instansen.
- **port** Port nummer att binda till (1 till 0xFFFF). Om Port numret är NX_ANY_PORT (0x0000) kommer IP-instansen att söka efter nästa lediga port och använda den för bindningen.
- **wait_option** Definierar hur tjänsten beter sig om porten redan är kopplad till en annan socket. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) socket-bindning.
- **NX_ALREADY_BOUND** (0X22) den här socketen är redan kopplad till en annan port.
- **NX_PORT_UNAVAILABLE** -porten (0x23) är redan kopplad till en annan socket.
- **NX_NO_FREE_PORTS** (0X45) ingen kostnads fri port.
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_INVALID_PORT** (0X46) ogiltig Port har angetts.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive,
- nx_udp_socket_receive_notify nx_udp_socket_send,
- nx_udp_socket_interface_send nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

Hämtar antalet byte som är tillgängliga för hämtning

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar antalet byte som är tillgängliga för mottagning i den angivna UDP-socketen.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade UDP-socketen.
- **bytes_available** Pekare till målet för tillgängliga byte.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) hämtade bytes tillgängliga byte.
- **NX_NOT_SUCCESSFUL** -socketen (0x43) är inte kopplad till en port.
- **NX_PTR_ERROR** (0X07) ogiltiga pekare.
- **NX_NOT_ENABLED** (0X14) UDP-funktionen är inte aktive rad.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_checksum_disable nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive,
- nx_udp_socket_receive_notify nx_udp_socket_send,
- nx_udp_socket_interface_send nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

Inaktivera kontroll summa för UDP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar kontroll summan för att skicka och ta emot paket på den angivna UDP-socketen. När logiken för kontroll summa är inaktive rad läses värdet noll in i UDP-huvudets fält för kontroll summa för alla paket som skickas via denna socket. Ett värde för en kontroll summa med noll värde i UDP-huvudet signalerar mottagaren om att kontroll summan inte har beräknats för det här paketet.

Observera också att detta inte har någon inverkan om ***NX_DISABLE_UDP_RX_CHECKSUM** _ och _ *_NX_DISABLE_UDP_TX_CHECKSUM_** definieras när du tar emot och skickar UDP-paket.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade UDP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) inaktive ring av kontroll summa.
- **NX_NOT_BOUND** -socketen (0x24) är inte kopplad.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timer

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive,
- nx_udp_socket_receive_notify nx_udp_socket_send,
- nx_udp_socket_interface_send nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

Aktivera kontroll summa för UDP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar den logiska kontroll summan för att skicka och ta emot paket på den angivna UDP-socketen. Kontroll summan täcker hela UDP-dataområdet samt ett IP-huvud för pseudo.

Observera också att detta inte har någon påverkan om **NX_DISABLE_UDP_RX_CHECKSUM** och **NX_DISABLE_UDP_TX_CHECKSUM** definieras när UDP-paket tas emot och skickas.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade UDP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) Enabled-kontroll Summa aktivera.
- **NX_NOT_BOUND** -socketen (0x24) är inte kopplad.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timer

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive,
- nx_udp_socket_receive_notify nx_udp_socket_send,
- nx_udp_socket_interface_send nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_create"></a>nx_udp_socket_create

Skapa UDP-socket.

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en UDP-socket för den angivna IP-instansen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **socket_ptr** Pekar på ny Bloc för UDP-socket.
- **namn** Program namn för denna UDP-socket.
- **type_of_service** Definierar typ av tjänst för överföringen, de juridiska värdena är följande:
    - NX_IP_NORMAL (0x00000000)
    - NX_IP_MIN_DELAY (0x00100000)
    - NX_IP_MAX_DATA (0x00080000)
    - NX_IP_MAX_RELIABLE (0x00040000)
    - NX_IP_MIN_COST (0x00020000)
- **fragment** Anger om IP-fragmentering tillåts eller inte. Om NX_FRAGMENT_OKAY (0x0) anges tillåts IP-fragmentering. Om NX_DONT_FRAGMENT (0x4000) anges inaktive ras IP-fragmentering.
- **time_to_live** Anger det 8-bitars värde som definierar hur många routrar det här paketet kan passera innan det utlöses. Standardvärdet anges av NX_IP_TIME_TO_LIVE.
- **queue_maximum** Definierar det maximala antalet UDP-datagram som kan köas för denna socket. När gränsen för kön har uppnåtts frigörs det äldsta UDP-paketet för varje nytt paket som togs emot.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) Det gick inte att skapa UDP-socket.
- **NX_OPTION_ERROR** (0X0a) ogiltigt alternativ typ-of-service, fragment eller Time-to-Live.
- **NX_PTR_ERROR** (0X07) ogiltig IP-eller socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable nx_udp_socket_delete,
- nx_udp_socket_info_get nx_udp_socket_port_get,
- nx_udp_socket_receive nx_udp_socket_receive_notify,
- nx_udp_socket_send nx_udp_socket_interface_send,
- nx_udp_socket_unbind nx_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete

Ta bort UDP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en UDP-socket som skapats tidigare. Om socketen var kopplad till en port måste socketen vara obunden först.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade UDP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) ta bort socket.
- **NX_STILL_BOUND** (0X42) socket är fortfarande kopplad.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable nx_udp_socket_create,
- nx_udp_socket_info_get nx_udp_socket_port_get,
- nx_udp_socket_receive nx_udp_socket_receive_notify,
- nx_udp_socket_send nx_udp_socket_interface_send,
- nx_udp_socket_unbind nx_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get

Hämta information om UDP-socket-aktiviteter

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om UDP-socket-aktiviteter för den angivna UDP-socket-instansen.

*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade UDP socket-instansen.
- **udp_packets_sent** Pekare till målet för det totala antalet UDP-paket som skickats på socket.
- **udp_bytes_sent** Pekare till målet för det totala antalet UDP-byte som skickats på socket.
- **udp_packets_received** Pekare till målet för det totala antalet UDP-paket som tagits emot på socket.
- **udp_bytes_received** Pekare till målet för det totala antalet UDP-byte som tagits emot vid socket.
- **udp_packets_queued** Pekare till målet för det totala antalet köade UDP-paket på socket.
- **udp_receive_packets_dropped** Pekare till målet för det totala antalet UDP-mottagna paket som har tagits bort för socket på grund av att köns storlek överskrids.
- **udp_checksum_errors** Pekare till målet för det totala antalet UDP-paket med fel kontroll summor på socket.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades hämtning av UDP-socket-information.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar och timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
    &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_queued_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable nx_udp_socket_create,
- nx_udp_socket_delete nx_udp_socket_port_get,
- nx_udp_socket_receive nx_udp_socket_receive_notify,
- nx_udp_socket_send nx_udp_socket_interface_send,
- nx_udp_socket_unbind nx_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

Hämta port nummer som är kopplat till UDP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det port nummer som är associerat med socketen, vilket är användbart för att hitta den port som allokerats av NetX i situationer där NX_ANY_PORT angavs vid den tidpunkt då socketen var kopplad.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade UDP-instansen.
- **port_ptr** Pekare till målet för retur port numret. Giltiga port nummer är (1 – 0xFFFF).

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) socket-bindning.
- **NX_NOT_BOUND** (0X24) den här socketen är inte kopplad till någon port.
- **NX_PTR_ERROR** (0X07) ogiltig socket pekare eller port retur pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable nx_udp_socket_create,
- nx_udp_socket_delete nx_udp_socket_info_get,
- nx_udp_socket_receive nx_udp_socket_receive_notify,
- nx_udp_socket_send nx_udp_socket_interface_send,
- nx_udp_socket_unbind nx_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

Ta emot datagram från UDP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar emot ett UDP-datagram från den angivna socketen. Om inget datagram har placerats i kö på den angivna socketen, pausas anroparen utifrån det angivna wait-alternativet.

*Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade UDP-instansen.
- **packet_ptr** Pekare till paket pekare för UDP-datagram.
- **wait_option** Definierar hur tjänsten fungerar om ett datagram inte är i kö för närvarande i kö. Vänte alternativen definieras enligt följande:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable nx_udp_socket_create,
- nx_udp_socket_delete nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive_notify,
- nx_udp_socket_send nx_udp_socket_interface_send,
- nx_udp_socket_unbind nx_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

Meddela program om varje mottaget paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a>Beskrivning

Den här tjänsten ställer in en aviserings funktions pekare för funktionen motringning till funktionen motringning som anges av programmet. Den här återanrops funktionen anropas sedan när ett paket tas emot på socketen. Om det finns en NX_NULL-pekare är funktionen Receive notify inaktive rad.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till UDP-socketen.
- **udp_receive_notify** Funktionen motringning till program som anropas när ett paket tas emot på socketen.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable nx_udp_socket_create,
- nx_udp_socket_delete nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,
- nx_udp_socket_interface_send nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send

Skicka ett UDP-datagram

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett UDP-datagram via en tidigare skapad och kopplad UDP-socket. NetX hittar en lämplig lokal IP-adress som käll adress baserat på mål-IP-adressen. Om du vill ange ett särskilt gränssnitt och en käll-IP-adress ska programmet använda tjänsten **nx_udp_socket_interface_send** .

Observera att den här tjänsten returnerar omedelbart oavsett om UDP-datagramet har skickats.

Socketen måste vara kopplad till en lokal port.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade UDP-instansen
- **packet_ptr** Paket pekare för UDP-datagram
- **ip_address** Mål-IP-adress
- **port** Giltigt mål port nummer mellan 1 och 0Xffffffff) i värdens byte ordning

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades UDP socket Send
- **NX_NOT_BOUND** -sockel (0x24) är inte kopplad till någon port
- **NX_NO_INTERFACE_ADDRESS** (0x50) Det går inte att hitta något lämpligt utgående gränssnitt.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig Server-IP-adress
- **NX_UNDERFLOW** (protokollnumret 0x02) inte tillräckligt med utrymme för UDP-huvudet i paketet
- **NX_OVERFLOW** (0X03) paket tilläggs pekare är ogiltig
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten
- **NX_NOT_ENABLED** (0X14) UDP har inte Aktiver ATS
- **NX_INVALID_PORT** (0X46) port numret är inte inom ett giltigt intervall

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
    server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
    the packet out the UDP socket to its peer. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable nx_udp_socket_create,
- nx_udp_socket_delete nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive,
- nx_udp_socket_receive_notify nx_udp_socket_interface_send,
- nx_udp_socket_unbind nx_udp_source_extract

## <a name="nx_udp_socket_interface_send"></a>nx_udp_socket_interface_send

Skicka datagram via UDP-socket.

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett UDP-datagram via en tidigare skapad och kopplad UDP-socket via nätverks gränssnittet med den angivna IP-adressen som käll adress. Observera att tjänsten returnerar omedelbart, oavsett om UDP-datagramet har skickats eller inte.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Socket för att överföra paketet.
- **packet_ptr** Pekare till paket att överföra.
- **ip_address** Mål-IP-adress att skicka paket.
- **port** Målport.
- **address_index** Index för den adress som är associerad med det gränssnitt som ska användas för att skicka paket.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESSs** paket (0x00) har skickats.
- **NX_NOT_BOUND** -socketen (0x24) är inte kopplad till en port.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.
- **NX_NOT_ENABLED** (0X14) UDP-bearbetning är inte aktiverat.
- **NX_PTR_ERROR** (0X07) ogiltig pekare.
- **NX_OVERFLOW** (0X03) ogiltig paket tilläggs pekare.
- **NX_UNDERFLOW** (protokollnumret 0x02) ogiltig lägga pekare för paket.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_INVALID_INTERFACE** (0X4C) ogiltigt adress index.
- **NX_INVALID_PORT** (0X46) port numret överskrider det högsta port numret.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable nx_udp_socket_create,
- nx_udp_socket_delete nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive,
- nx_udp_socket_receive_notify nx_udp_socket_send,
- nx_udp_socket_unbind

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

Bind UDP-socketen från UDP-porten.

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten frigör bindningen mellan UDP-socketen och en UDP-port. Alla mottagna paket som lagras i mottagnings kön frigörs som en del av Unbind-åtgärden.

Om det finns andra trådar som väntar på att binda en annan socket till den obundna porten, binds den första pausade tråden till den nyligen obundna porten.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till den tidigare skapade UDP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) uppkopplad socket-bindning.
- **NX_NOT_BOUND** -socketen var inte kopplad till någon port.
- **NX_PTR_ERROR** (0X07) ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable nx_udp_socket_create,
- nx_udp_socket_delete nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive,
- nx_udp_socket_receive_notify nx_udp_socket_send,
- nx_udp_socket_interface_send nx_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract

Extrahera IP och skicka port från UDP-datagram

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a>Beskrivning

Den här tjänsten extraherar avsändarens IP-adress och port nummer från IP-och UDP-huvudena för det angivna UDP-datagrammet.

### <a name="parameters"></a>Parametrar

- **packet_ptr** Paket pekare för UDP-datagram.
- **ip_address** Giltig pekare till variabeln returnera IP-adress.
- **port** Giltig pekare till retur port-variabeln.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad käll-IP/port-extrahering.
- **NX_INVALID_PACKET** (0X12) det angivna paketet är ogiltigt.
- **NX_PTR_ERROR** (0X07) ogiltigt paket eller IP-eller port mål.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers, ISR

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract nx_udp_socket_bind,
- nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable nx_udp_socket_create,
- nx_udp_socket_delete nx_udp_socket_info_get,
- nx_udp_socket_port_get nx_udp_socket_receive,
- nx_udp_socket_receive_notify nx_udp_socket_send,
- nx_udp_socket_interface_send nx_udp_socket_unbind