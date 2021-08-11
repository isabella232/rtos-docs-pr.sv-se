---
title: Kapitel 4 – Beskrivning Azure RTOS NetX Services
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f1ebbd4d78f96a257fc6cf62474917a1d618524ff6f27f99c108f904589f84fe
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801945"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a>Kapitel 4 – Beskrivning Azure RTOS NetX Services

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX-tjänster i alfabetisk ordning. Tjänstnamn är utformade så att alla liknande tjänster grupperas tillsammans. Till exempel finns alla ARP-tjänster i början av det här kapitlet.

> [!NOTE]
> *Observera att ett BSD-Compatible Socket API är tillgängligt för äldre programkod som inte kan dra full nytta av NetX-API:et med höga prestanda. Se bilaga D för mer information om BSD-Compatible Socket API.*

I avsnittet "Returvärden" i varje beskrivning påverkas inte värden i **BOLD** av det NX_DISABLE_ERROR_CHECKING-alternativ som används för att inaktivera API-felkontrollen, medan värden i icke-fetstil är helt inaktiverade. Avsnitten "Tillåten från" anger från vilka varje NetX-tjänst kan anropas.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

Ogiltigförklara alla dynamiska poster i ARP-cachen

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten ogiltigförklarar alla dynamiska ARP-poster som för närvarande finns i ARP-cachen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad ARP-cache ogiltigförklaras.
- **NX_NOT_ENABLED** (0x14) ARP är inte aktiverat.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-adress.
- **NX_CALLER_ERROR** (0x11) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

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

### <a name="description"></a>Description

Den här tjänsten allokerar en dynamisk post från ARP-cachen och uppsättningar upp den angivna IP-adressen till fysisk adressmappning. Om en fysisk adress är noll skickas en faktisk ARP-begäran till nätverket för att den fysiska adressen ska kunna matchas. Observera också att den här posten tas bort om ARP-åldersfördelningen är aktiv eller om ARP-cachen är uttömd och detta är den minst nyligen använda ARP-posten.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **ip_address** IP-adress att mappa.
- **physical_msw** Översta 16 bitar (47–32) av den fysiska adressen.
- **physical_lsw** Lägre 32 bitar (31–0) av den fysiska adressen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad dynamisk ARP-postuppsättning.
- **NX_NO_MORE_ENTRIES** (0x17) Inga fler ARP-poster är tillgängliga i ARP-cachen.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-adress.
- **NX_PTR_ERROR** (0x07) Pekare för ogiltig IP-instans.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_arp_dynamic_entries_invalidate, nx_arp_enable,
- nx_arp_gratuitous_send, nx_arp_hardware_address_find,
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_enable"></a>nx_arp_enable

Aktiverar ARP (Address Resolution Protocol).

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a>Description

Den här tjänsten initierar ARP-komponenten i NetX för den specifika IP-instansen. ARP-initiering omfattar att konfigurera ARP-cachen och olika ARP-bearbetningsrutiner som krävs för att skicka och ta emot ARP-meddelanden.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **arp_cache_memory** Pekare till minnesområdet för att placera ARP-cachen.
- **arp_cache_size** Varje ARP-post är 52 byte, det totala antalet ARP-poster är därför storleken dividerat med 52.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad ARP-aktivera.
- **NX_PTR_ERROR** (0x07) Ogiltig IP- eller cacheminnespekare.
- **NX_SIZE_ERROR** (0x09) Användaren angav att ARP-cacheminnet är för litet.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_ALREADY_ENABLED** (0x15) Den här komponenten har redan aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_gratuitous_send, nx_arp_hardware_address_find,
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

Skicka en gratuitous ARP-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Description

Den här tjänsten går igenom alla fysiska gränssnitt för att överföra gratuitous ARP-begäranden så länge gränssnittets IP-adress är giltig. Om ett ARP-svar senare tas emot anropas den angivna svarshanteraren för att bearbeta svaret till den ej intuitiska ARP:n.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **response_handler** Pekare till svarshanteringsfunktionen. Om NX_NULL anges ignoreras svar.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad, olöslig ARP-skicka.
- **NX_NO_PACKET** (0x01) Inget paket tillgängligt.
- **NX_NOT_ENABLED** (0x14) ARP är inte aktiverat.
- **NX_IP_ADDRESS_ERROR** (0x21) Den aktuella IP-adressen är ogiltig.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

Hitta den fysiska maskinvaruadressen med en IP-adress

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a>Description

Den här tjänsten försöker hitta en fysisk maskinvaruadress i ARP-cachen som är associerad med den angivna IP-adressen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **ip_address** IP-adress att söka efter.
- **physical_msw** Pekare till variabeln för att returnera de 16 översta bitarna (47–32) för den fysiska adressen.
- **physical_lsw** Pekare till variabeln för att returnera de lägre 32 bitarna (31–0) för den fysiska adressen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Hitta lyckad ARP-maskinvaruadress.
- **NX_ENTRY_NOT_FOUND** (0x16) Mappning hittades inte i ARP-cachen.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-adress.
- **NX_PTR_ERROR** (0x07) Ogiltig IP- eller minnespekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

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

### <a name="description"></a>Description

Den här tjänsten hämtar information om ARP-aktiviteter för den associerade IP-instansen.

*Om en mål pekare NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **arp_requests_sent** Pekare till mål för det totala antalet ARP-begäranden som skickats från den här IP-instansen.
- **arp_requests_received** Pekare till mål för totalt antal ARP-begäranden som tagits emot från nätverket.
- **arp_responses_sent** Pekare till mål för det totala ARP-svar som skickats från den här IP-instansen.
- **arp_responses_received** Pekare till målet för det totala antalet ARP-svar som tagits emot från nätverket.
- **arp_dynamic_entries** Pekare till målet för det aktuella antalet dynamiska ARP-poster.
- **arp_static_entries** Pekare till målet för det aktuella antalet statiska ARP-poster.
- **arp_aged_entries** Pekare till målet för det totala antalet ARP-poster som har blivit ogiltiga och har blivit ogiltiga.
- **arp_invalid_messages** Pekare till målet för de totala ogiltiga ARP-meddelanden som tagits emot.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad ARP-informationshämtning.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_ip_address_find,
- nx_arp_static_entries_delete, nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

Hitta IP-adress givet en fysisk adress

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a>Description

Den här tjänsten försöker hitta en IP-adress i ARP-cachen som är associerad med den angivna fysiska adressen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **ip_address** Pekare för att returnera IP-adress om en sådan har mappats.
- **physical_msw** Översta 16 bitar (47–32) av den fysiska adressen att söka efter.
- **physical_lsw** Lägre 32 bitar (31–0) av den fysiska adressen att söka efter.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IP-adress för ARP
- **NX_ENTRY_NOT_FOUND** (0x16) Mappning hittades inte i ARP-cachen.
- **NX_PTR_ERROR** (0x07) Ogiltig IP- eller minnespekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw och physical_lsw båda 0.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_static_entries_delete,nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

Ta bort alla statiska ARP-poster

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort alla statiska poster i ARP-cachen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Statiska poster tas bort.
- **NX_PTR_ERROR** (0x07) Ogiltig ip_ptr pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a>Se även

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

Skapa statisk IP till maskinvarumappning i ARP-cache

### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Description

Den här tjänsten skapar en statisk IP-till-fysisk adressmappning i ARP-cachen för den angivna IP-instansen. Statiska ARP-poster omfattas inte av periodiska ARP-uppdateringar.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **ip_address** IP-adress som ska mappa.
- **physical_msw** De 16 översta bitarna (47–32) av den fysiska adressen som ska mappa.
- **physical_lsw** Lägre 32 bitar (31–0) av den fysiska adressen som ska mappa.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Skapa en statisk ARP-post.
- **NX_NO_MORE_ENTRIES** (0x17) Inga fler ARP-poster är tillgängliga i ARP-cachen.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-adress.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw och physical_lsw båda 0.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

Ta bort statisk IP till maskinvarumappning i ARP-cache


### <a name="prototype"></a>Prototyp

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Description

Den här tjänsten hittar och tar bort en tidigare skapad statisk IP-till-fysisk adressmappning i ARP-cachen för den angivna IP-instansen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **ip_address** IP-adress som mappades statiskt.
- **physical_msw** De 16 översta bitarna (47–32) av den fysiska adressen som mappades statiskt.
- **physical_lsw** Lägre 32 bitar (31–0) av den fysiska adressen som mappades statiskt.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Borttagning av statisk ARP-post.
- **NX_ENTRY_NOT_FOUND** (0x16) Statisk ARP-post hittades inte i ARP-cachen.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-adress.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw och physical_lsw båda 0.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create

## <a name="nx_icmp_enable"></a>nx_icmp_enable

Aktivera Internet Control Message Protocol (ICMP)

### <a name="prototype"></a>Prototyp

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar ICMP-komponenten för den angivna IP-instansen.
ICMP-komponenten ansvarar för att hantera Internet-felmeddelanden och pinga begäranden och svar.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad ICMP-aktivera.
- **NX_ALREADY_ENABLED** (0x15) ICMP är redan aktiverat.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a>Se även

- nx_icmp_info_get, nx_icmp_ping

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

### <a name="description"></a>Description

Den här tjänsten hämtar information om ICMP-aktiviteter för den angivna IP-instansen.

*Om en mål pekare NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **pings_sent** Pekare till mål för det totala antalet pingar som skickats.
- **ping_timeouts** Pekare till mål för det totala antalet tidsgränser för ping.
- **ping_threads_suspended** Pekare till målet för det totala antalet trådar som pausas vid ping-begäranden.
- **ping_responses_received** Pekare till estination av det totala antalet ping-svar som tagits emot.
- **icmp_checksum_errors** Pekare till målet för det totala antalet ICMP-kontrollsummor.
- **icmp_unhandled_messages** Pekare till estination av det totala antalet ej hanterade ICMP-meddelanden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad ICMP-informationshämtning.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_icmp_enable, nx_icmp_ping

## <a name="nx_icmp_ping"></a>nx_icmp_ping

Skicka pingbegäran till angiven IP-adress

### <a name="prototype"></a>Prototyp

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skickar en ping-begäran till den angivna IP-adressen och väntar på den angivna tiden för ett pingsvarsmeddelande. Om inget svar tas emot returneras ett fel. Annars returneras hela svarsmeddelandet i variabeln som response_ptr.

*Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **ip_address** IP-adress, i värdbyteordning, för att pinga. data Pekare till dataområde för pingmeddelande.
- **data_size** Antal byte i pingdata
- **response_ptr** Pekare till paket pekare för att returnera pingsvarsmeddelandet i.
- **wait_option** Definierar hur lång tid det tar att vänta på ett pingsvar. väntealternativ definieras på följande sätt:

  - NX_NO_WAIT (0x00000000)
  - NX_WAIT_FOREVER (0xFFFFFFFF)
  - timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad ping. Pekaren för svarsmeddelanden placerades i variabeln som response_ptr.
- **NX_NO_PACKET** (0x01) Det går inte att allokera ett pingbegärandepaket.
- **NX_OVERFLOW** (0x03) Det angivna dataområdet överskrider standardpaketstorleken för den här IP-instansen.
- **NX_NO_RESPONSE** (0x29) Begärd IP-adress svarade inte.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-adress.
- **NX_PTR_ERROR** (0x07) Ogiltig IP- eller svarspekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_icmp_enable, nx_icmp_info_get

## <a name="nx_igmp_enable"></a>nx_igmp_enable

Aktivera Internet Group Management Protocol (IGMP)

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar IGMP-komponenten på den angivna IP-instansen.
IGMP-komponenten ansvarar för att tillhandahålla stöd för IP multicast-grupphanteringsåtgärder.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IGMP-aktivera.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_ALREADY_ENABLED** (0x15) Den här komponenten har redan aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a>Se även

- nx_igmp_info_get,nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join, nx_igmp_multicast_leave

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

### <a name="description"></a>Description

Den här tjänsten hämtar information om IGMP-aktiviteter för den angivna IP-instansen.

*Om en mål pekare NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **igmp_reports_sent** Pekare till mål för det totala antalet skickade ICMP-rapporter.
- **igmp_queries_received** Pekare till mål för det totala antalet frågor som tas emot av multicast-routern.
- **igmp_checksum_errors** Pekare till målet för det totala antalet IGMP-kontrollsummafel på mottagningspaket.
- **current_groups_joined** Pekare till målet för det aktuella antalet grupper som är sammanfogade via den här IP-instansen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IGMP-informationshämtning.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_igmp_enable, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join, nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

Inaktivera IGMP-loopback

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar IGMP-loopback för alla efterföljande multicast-grupper som är sammanfogade.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckad IGMP-loopback inaktiveras.
- **NX_NOT_ENABLED** (0x14) IGMP är inte aktiverat.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Anroparen är inte en tråd eller initiering.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a>Se även

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

Aktivera IGMP-loopback

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar IGMP-loopback för alla efterföljande multicast-grupper som är sammanslagna.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckad IGMP-loopback inaktiveras.
- **NX_NOT_ENABLED** (0x14) IGMP är inte aktiverat.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Anroparen är inte en tråd eller initiering.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a>Se även

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join

Ansluta IP-instansen till en angiven multicast-grupp via ett gränssnitt

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a>Description

Den här tjänsten ansluter en IP-instans till den angivna multicast-gruppen via ett angivet nätverksgränssnitt. En intern räknare underhålls för att hålla reda på antalet gånger som samma grupp har anslutits. När du har sammanfogat multicast-gruppen tillåter IGMP-komponenten mottagning av IP-paket med den här gruppadressen via det angivna nätverksgränssnittet och rapporterar även till routrar att denna IP-adress är medlem i den här multicast-gruppen. Meddelanden om IGMP-medlemskapskoppling, rapport och skrivning skickas också via det angivna nätverksgränssnittet.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **group_address** Multicast-gruppadress för klass D som ska anslutas i värdbyteordning.
- **interface_index** Index för gränssnittet som är kopplat till NetX-instansen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad multicast-gruppkoppling.
- **NX_NO_MORE_ENTRIES** (0x17) Inga fler multicast-grupper kan vara sammanfogade, maxvärdet överskrids.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_INVALID_INTERFACE** (0x4C) Enhetsindex pekar på ett ogiltigt nätverksgränssnitt.
- **NX_IP_ADDRESS_ERROR** (0x21) Multicast-gruppadress som anges är inte en giltig klass D-adress.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) IP-multicast-stöd är inte aktiverat.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_igmp_loopback_enable, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

Ansluta IP-instans till angiven multicast-grupp

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Description

Den här tjänsten ansluter en IP-instans till den angivna multicast-gruppen. En intern räknare underhålls för att hålla reda på antalet gånger som samma grupp har anslutits. Drivrutinen uppmanas att skicka en IGMP-rapport om det här är den första kopplingsbegäran i nätverket som anger värdens avsikt att ansluta till gruppen. Efter anslutningen tillåter IGMP-komponenten mottagning av IP-paket med den här gruppadressen och rapporterar till routrar att denna IP-adress är medlem i den här multicast-gruppen.

> [!NOTE]
> *Om du vill ansluta till en multicast-grupp på en icke-primär enhet använder du **nx_igmp_multicast_interface_join.***

- **Parametrar**

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **group_address** Multicast-gruppadress för klass D som ska anslutas.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad multicast-gruppkoppling.
- **NX_NO_MORE_ENTRIES** (0x17) Inga fler multicast-grupper kan vara sammanfogade, maxvärdet överskrids.
- **NX_INVALID_INTERFACE** (0x4C) Enhetsindex pekar på ett ogiltigt nätverksgränssnitt.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-gruppadress.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

Orsaka att IP-instansen lämnar angiven multicast-grupp

### <a name="prototype"></a>Prototyp

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Description

Den här tjänsten gör att en IP-instans lämnar den angivna multicast-gruppen om antalet ledighetsbegäranden matchar antalet kopplingsbegäranden. Annars minskar det interna antalet kopplingar helt enkelt.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till IP-instans som skapats tidigare.
- **group_address** Multicast-grupp som ska gå.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad multicast-gruppkoppling.
- **NX_ENTRY_NOT_FOUND** (0x16) Föregående kopplingsbegäran hittades inte.
- **NX_INVALID_INTERFACE** (0x4C) Enhetsindex pekar på ett ogiltigt nätverksgränssnitt.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-gruppadress.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>Se även

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy

Meddela programmet om IP-adressen ändras


### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a>Description

Den här tjänsten registrerar en programmeddelandefunktion som anropas när IP-adressen ändras.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till IP-instans som skapats tidigare.
- **change_notify** Pekare till ip-ändringsmeddelandefunktionen. Om den här parametern NX_NULL inaktiveras meddelandet om IP-adressändring.
- **additional_info** Pekar på valfri ytterligare information som också skickas till meddelandefunktionen när IP-adressen ändras.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Meddelande om lyckad ändring av IP-adress.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_address_get"></a>nx_ip_address_get

Hämta IP-adress och nätverksmask

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Description

Den här tjänsten hämtar IP-adressen och dess nätmask för det primära nätverksgränssnittet.

*Om du vill hämta information om den sekundära enheten använder du tjänsten
- **nx_ip_interface_address_get**.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till IP-instans som skapats tidigare.
- **ip_address** Pekare till mål för IP-adress.
- **network_mask** Pekare till mål för nätverksmask.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IP-adress hämta.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-adress eller returvariabel pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_address_set"></a>nx_ip_address_set

Ange IP-adress och nätverksmask

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Description

Den här tjänsten anger IP-adress och nätverksmask för det primära nätverksgränssnittet.

*Om du vill ange IP-adress och nätverksmask för den sekundära enheten använder du **nx_ip_interface_address_set**.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till IP-instans som skapats tidigare.
- **ip_address** Ny IP-adress.
- **network_mask** Ny nätverksmask.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IP-adressuppsättning.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-adress.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
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

### <a name="description"></a>Description

Den här tjänsten skapar en IP-instans med användarens angivna IP-adress och nätverksdrivrutin. Dessutom måste programmet tillhandahålla en tidigare skapad paketpool som IP-instansen kan använda för intern paketallokering. Observera att den tillhandahållna programnätverksdrivrutinen inte anropas förrän ip-adressens tråd körs.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till kontrollblock för att skapa en ny IP-instans.
- **namn** Namnet på den nya IP-instansen.
- **ip_address** IP-adress för den här nya IP-instansen.
- **network_mask** Maskera för att beskriva nätverksdelen av IP-adressen för användning av undernät och supernät.
- **default_pool** Pekare till kontrollblocket för netx-paketpoolen som skapats tidigare.
- **ip_network_driver** Nätverksdrivrutin som tillhandahålls av användaren används för att skicka och ta emot IP-paket.
- **memory_ptr** Pekare till minnesområdet för IP-hjälptrådens stackområde.
- **memory_size** Antal byte i minnesområdet för IP-hjälptrådens stack.
- **prioritet** Prioritet för IP-hjälptråd.

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckad skapande av IP-instans.
- **NX_NOT_IMPLEMENTED** (0x4A) NetX-biblioteket är felaktigt konfigurerat.
- **NX_PTR_ERROR** (0x07) Ogiltig IP, funktionspekare för nätverksdrivrutiner, paketpool eller minnespekare.
- **NX_SIZE_ERROR** (0x09) Den angivna stackstorleken är för liten.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_IP_ADDRESS_ERROR** (0x21) Den angivna IP-adressen är ogiltig.
- **NX_OPTION_ERROR** (0x21) Den angivna IP-trådprioritet är ogiltig.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_delete"></a>nx_ip_delete

Ta bort IP-instans som skapats tidigare


### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en tidigare skapad IP-instans och släpper alla systemresurser som ägs av IP-instansen.

### <a name="parameters"></a>Parametrar
- **ip_ptr** Pekare till IP-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IP-borttagning.
- **NX_SOCKETS_BOUND** (0x28) Den här IP-instansen har fortfarande UDP- eller TCP-sockets bundna till sig. Alla socketar måste vara obundna och borttagna innan DU tar bort IP-instansen.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>Se även

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

Utfärda kommando till nätverksdrivrutin

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tillhandahåller ett direkt gränssnitt till programmets primära nätverksgränssnittsdrivrutin som anges under ***nx_ip_create anropet.***

Programspecifika kommandon kan användas om deras numeriska värde är större än eller lika med NX_LINK_USER_COMMAND.

*Om du vill utfärda kommandot  för den sekundära enheten använder du nx_ip_driver_interface_direct_command tjänsten.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till IP-instans som skapats tidigare.
- **kommando** Numerisk kommandokod. Standardkommandon definieras på följande sätt:

- NX_LINK_GET_STATUS (10)
- NX_LINK_GET_SPEED (11)
- NX_LINK_GET_DUPLEX_TYPE (12)
- NX_LINK_GET_ERROR_COUNT (13)
- NX_LINK_GET_RX_COUNT (14)
- NX_LINK_GET_TX_COUNT (15)
- NX_LINK_GET_ALLOC_ERRORS (16)
- NX_LINK_USER_COMMAND (50)

- **return_value_ptr** Pekare för att returnera variabeln i anroparen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Ett lyckat direktkommando för nätverksdrivrutiner.
- **NX_UNHANDLED_COMMAND** (0x44) kommandot Ohanterad eller ohanterad nätverksdrivrutin.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-adress eller returvärdes pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_INVALID_INTERFACE** (0x4C) Ogiltigt gränssnittsindex.

### <a name="allowed-from"></a>Tillåts från

Trådar

- **Avtagande möjlig**

No

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
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command

Utfärda kommando till nätverksdrivrutin

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tillhandahåller ett direktkommando till programmets drivrutin för nätverksenhet i IP-instansen. Programspecifika kommandon kan användas om deras numeriska värde är större än eller lika med *NX_LINK_USER_COMMAND*.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **kommando** Numerisk kommandokod. Standardkommandon definieras på följande sätt:
- NX_LINK_GET_STATUS (10)
- NX_LINK_GET_SPEED (11)
- NX_LINK_GET_DUPLEX_TYPE (12)
- NX_LINK_GET_ERROR_COUNT (13)
- NX_LINK_GET_RX_COUNT (14)
- NX_LINK_GET_TX_COUNT (15)
- NX_LINK_GET_ALLOC_ERRORS (16)
- NX_LINK_USER_COMMAND (50)
- **interface_index** Index för nätverksgränssnittet som kommandot ska skickas till.
- **return_value_ptr** Pekare för att returnera variabeln i anroparen.

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Ett lyckat direktkommando för nätverksdrivrutiner.
- **NX_UNHANDLED_COMMAND** (0x44) kommandot Ohanterad eller ohanterad nätverksdrivrutin.
- **NX_INVALID_INTERFACE** (0x4C) Ogiltigt gränssnittsindex
- **NX_PTR_ERROR** (0x07) Ogiltig IP-adress eller returvärdes pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

Inaktivera vidarebefordran av IP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar vidarebefordran av IP-paket i NetX IP-komponenten. När IP-uppgiften skapas inaktiveras den här tjänsten automatiskt.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IP-vidarebefordran inaktiveras.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

Aktivera vidarebefordran av IP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten möjliggör vidarebefordran av IP-paket i NetX IP-komponenten. När IP-uppgiften skapas inaktiveras den här tjänsten automatiskt.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckad IP-vidarebefordran aktivera.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

Inaktivera fragmentering av IP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar funktionen för fragmentering och återmontering av IP-paket. För paket som väntar på att återmonteras släpper den här tjänsten dessa paket. När IP-uppgiften skapas inaktiveras den här tjänsten automatiskt.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till IP-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckades IP-fragment inaktiveras.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) IP-fragmentering är inte aktiverat på IP-instansen.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

Aktivera fragmentering av IP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten möjliggör fragmentering och återmontering av IP-paket. När IP-uppgiften skapas inaktiveras den här tjänsten automatiskt.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till IP-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IP-fragmentet aktivera.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) funktioner för IP-fragmentering kompileras inte till NetX.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

Ange IP-adress för gateway

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a>Description

Den här tjänsten anger IP-gatewayens IP-adress. All trafik utanför nätverket dirigeras till den här gatewayen för överföring. Gatewayen måste vara direkt åtkomlig via ett av nätverksgränssnitten.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till IP-instans som skapats tidigare.
- **ip_address** IP-adressen för gatewayen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Ip-adressuppsättning för lyckad gateway.
- **NX_PTR_ERROR** (0x07) Pekare för ogiltig IP-instans.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-adress.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, tråd

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a>Se även

- nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete

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

### <a name="description"></a>Description

Den här tjänsten hämtar information om IP-aktiviteter för den angivna IP-instansen.

*Om en mål pekare NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till IP-instans som skapats tidigare.
- **ip_total_packets_sent** Pekare till mål för det totala antalet skickade IP-paket.
- **ip_total_bytes_sent** Pekare till mål för det totala antalet skickade byte.
- **ip_total_packets_received** Pekare till målet för det totala antalet IP-mottagningspaket.
- **ip_total_bytes_received** Pekare till målet för det totala antalet mottagna IP-byte.
- **ip_invalid_packets** Pekare till målet för det totala antalet ogiltiga IP-paket.
- **ip_receive_packets_dropped** Pekare till målet för det totala antalet bort ignorerade inkommande paket.
- **ip_receive_checksum_errors** Pekare till målet för det totala antalet fel med kontrollsumma i inkommande paket.
- **ip_send_packets_dropped** Pekare till målet för det totala antalet bort ignorerade skickade paket.
- **ip_total_fragments_sent** Pekare till målet för det totala antalet fragment som skickats.
- **ip_total_fragments_received** Pekare till målet för det totala antalet mottagna fragment.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IP-informationshämtning.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get

Hämta IP-adress för gränssnitt

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Description

Den här tjänsten hämtar IP-adressen för ett angivet nätverksgränssnitt.

*Den angivna enheten, om den inte är den primära enheten, måste tidigare vara ansluten till IP-instansen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **interface_index** Gränssnittsindex, samma värde som indexet till nätverksgränssnittet som är kopplat till IP-instansen.
- **ip_address** Pekare till mål för enhetens gränssnitts-IP-adress.
- **network_mask** Pekare till mål för enhetens gränssnittsnätverksmask.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IP-adress hämta.
- **NX_INVALID_INTERFACE** (0x4C) Angivet nätverksgränssnitt är ogiltigt.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_ip_interface_address_set, nx_ip_interface_attach,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set

Ange IP-adress för gränssnitt och nätverksmask

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Description

Den här tjänsten anger IP-adressen och nätverksmasken för det angivna IP-gränssnittet.

*Det angivna gränssnittet måste tidigare vara kopplat till IP-instansen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **interface_index** Index för gränssnittet som är kopplat till NetX-instansen.
- **ip_address** Ny IP-adress för nätverksgränssnittet.
- **network_mask** Nätverksmask för nytt gränssnitt.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IP-adressuppsättning.
- **NX_INVALID_INTERFACE** (0x4C) Angivet nätverksgränssnitt är ogiltigt.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0x07) Ogiltiga pekare.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-adress

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_ip_interface_address_get, nx_ip_interface_attach,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach

Koppla nätverksgränssnitt till IP-instans

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

### <a name="description"></a>Description

Den här tjänsten lägger till ett fysiskt nätverksgränssnitt i IP-gränssnittet. Observera att IP-instansen skapas med det primära gränssnittet så att varje ytterligare gränssnitt är sekundärt till det primära gränssnittet. Det totala antalet nätverksgränssnitt som är kopplade till IP-instansen (inklusive det primära gränssnittet) får inte **överskrida NX_MAX_PHYSICAL_INTERFACES**.

Om IP-tråden inte har körts än initieras de sekundära gränssnitten som en del av IP-trådstartsprocessen som initierar alla fysiska gränssnitt.

Om IP-tråden inte körs ännu initieras det sekundära  gränssnittet som en del av nx_ip_interface_attach tjänsten.

*ip_ptr måste peka på en giltig NetX IP-struktur.*

- ***NX_MAX_PHYSICAL_INTERFACES** måste konfigureras för antalet nätverksgränssnitt för IP-instansen. Standardvärdet är ett.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **interface_name** Pekare till gränssnittets namnsträng.
- **ip_address** Enhetens IP-adress i värdbyteordning.
- **network_mask** Enhetens nätverksmask i värdbyteordning.
- **ip_link_driver** Ethernet-drivrutin för gränssnittet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) post läggs till i statisk routningstabell.
- **NX_NO_MORE_ENTRIES** (0x17) Maximalt antal gränssnitt.
- **NX_MAX_PHYSICAL_INTERFACES** överskrids.
- **NX_DUPLICATED_ENTRY** (0x52) Den angivna IP-adressen används redan på den här IP-instansen.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-adressinmatning.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

Hämta nätverksgränssnittsparametrar


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

### <a name="description"></a>Description

Den här tjänsten hämtar information om nätverksparametrar för det angivna nätverksgränssnittet. Alla data hämtas i värdbyteordningen.

*ip_ptr måste peka på en giltig NetX IP-struktur. Det angivna gränssnittet, om det inte är det primära gränssnittet, måste tidigare vara kopplat till IP-instansen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **interface_index** Index som anger nätverksgränssnitt.
- **interface_name** Pekare till den buffert som innehåller namnet på nätverksgränssnittet.
- **ip_address** Pekare till målet för IP-adressen för gränssnittet.
- **network_mask** Pekare till mål för nätverksmask.
- **mtu_size** Pekare till mål för maximal överföringsenhet för det här gränssnittet.
- **physical_address_msw** Pekare till mål för de 16 översta bitarna på enhetens MAC-adress.
- **physical_address_lsw** Pekare till mål för lägre 32 bitar av enhetens MAC-adress.


### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Gränssnittsinformation har erhållits.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare.
- **NX_INVALID_INTERFACE** (0x4C) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** tjänst (0x11) anropas inte från system initiering eller trådkontext.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check

Kontrollera status för en IP-instans


### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten kontrollerar och väntar eventuellt på den angivna statusen för nätverksgränssnittet för en tidigare skapad IP-instans.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till IP-instans som skapats tidigare.
- **interface_index** Gränssnittsindexnummer
- **needed_status** IP-status begärd, definierad i bitkartform enligt följande:
    - NX_IP_INITIALIZE_DONE (0x0001)
    - NX_IP_ADDRESS_RESOLVED (0x0002)
    - NX_IP_LINK_ENABLED (0x0004)
    - NX_IP_ARP_ENABLED (0x0008)
    - NX_IP_UDP_ENABLED (0x0010)
    - NX_IP_TCP_ENABLED (0x0020)
    - NX_IP_IGMP_ENABLED (0x0040)
    - NX_IP_RARP_COMPLETE (0x0080)
    - NX_IP_INTERFACE_LINK_ENABLED (0x0100)
- **actual_status** Pekare till mål för faktiska bitar som angetts.
- **wait_option** Definierar hur tjänsten beter sig om de begärda statusbitarna inte är tillgängliga. Väntealternativen definieras på följande sätt:
    - NX_NO_WAIT (0x00000000)
    - NX_WAIT_FOREVER (0xFFFFFFFF)
    - timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IP-statuskontroll.
- **NX_NOT_SUCCESSFUL** (0x43) Statusbegäran nöjdes inte inom den angivna tidsgränsen.
- **NX_PTR_ERROR** (0x07) IP-pekare är eller har blivit ogiltig, eller så är den faktiska status pekaren ogiltig.
- **NX_OPTION_ERROR** (0x0a) Statusalternativet Ogiltigt krävs.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_INVALID_INTERFACE** (0x4C) Interface_index ligger utanför intervallet. eller så är gränssnittet inte giltigt.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_info_get,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set

Ställ in länkstatusändringen för att meddela återanropsfunktionen

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a>Description

Den här tjänsten konfigurerar funktionen för att meddela återanrop om länkstatusändring. Den användarindelade *link_status_change_notify* anropas när antingen den primära eller sekundära gränssnittsstatusen ändras (till exempel IP-adress ändras.) Om *link_status_change_notify* är NULL inaktiveras funktionen meddela återanrop om länkstatusändring.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare för IP-kontrollblock
- **link_status_change_notify** Återanropsfunktionen som anges av användaren anropas vid en ändring av det fysiska gränssnittet.


### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad uppsättning
- **NX_PTR_ERROR** (0x07) Ogiltig PEKARe för IP-kontrollblock eller ny fysisk adress pekare
- **NX_CALLER_ERROR** tjänst (0x11) anropas inte från system initiering eller trådkontext.


### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a>Se även

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_info_get,
- nx_ip_interface_status_check

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

Inaktivera sändning/mottagning av råa paket


### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar överföring och mottagning av råa IP-paket för den här IP-instansen. Om den råa pakettjänsten tidigare har aktiverats och det finns råa paket i mottagningskön, släpper den här tjänsten alla mottagna raw-paket.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till IP-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckade IP-rådatapaket inaktiveras.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a>Se även

- nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

Aktivera bearbetning av rådatapaket


### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten möjliggör överföring och mottagning av råa IP-paket för den här IP-instansen. Inkommande TCP-, UDP-, ICMP- och IGMP-paket bearbetas fortfarande av NetX. Paket med okända protokolltyper på den övre nivån bearbetas av råa rutiner för paketmottagande.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckades aktivera IP-rådatapaket.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a>Se även

- nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_interface_send"></a>nx_ip_raw_packet_interface_send

Skicka råa IP-paket via angivet nätverksgränssnitt

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a>Description

Den här tjänsten skickar ett obearbetat IP-paket till målets IP-adress med den angivna lokala IP-adressen som källadress och via det associerade nätverksgränssnittet. Observera att den här rutinen returneras omedelbart och därför inte är känd om IP-paketet faktiskt har skickats. Nätverksdrivrutinen ansvarar för att frigöra paketet när överföringen är klar. Den här tjänsten skiljer sig från andra tjänster på så sätt att det inte finns något sätt att veta om paketet faktiskt skickades. Det kan gå förlorat på Internet.

*Observera att rå IP-bearbetning måste vara aktiverat.*

*Den här tjänsten liknar **den nx_ip_raw_packet_send**, förutom att den här tjänsten gör att ett program kan skicka råa IP-paket från ett angivet fysiskt gränssnitt.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till IP-uppgift som skapats tidigare.
- **packet_ptr** Pekare till paket som ska överföras.
- **destination_ip** IP-adress för att skicka paket.
- **address_index** Index för adressen för det gränssnitt som paketet ska skickas på.
- **type_of_service** Typ av tjänst för paket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** paket (0x00) har överförts.
- **NX_IP_ADDRESS_ERROR** (0x21) Inget lämpligt utgående gränssnitt är tillgängligt.
- **NX_NOT_ENABLED** (0x14) Rå IP-paketbearbetning är inte aktiverat.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare.
- **NX_OPTION_ERROR** (0x0A) Ogiltig typ av tjänst har angetts.
- **NX_OVERFLOW** (0x03) Pekare för ogiltig paketförberedelser.
- **NX_UNDERFLOW** (0x02) Ogiltig pekare för paketförberedelser.
- **NX_INVALID_INTERFACE** (0x4C) Ogiltigt gränssnittsindex har angetts.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_receive, nx_ip_raw_packet_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

Ta emot råa IP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten tar emot ett rå IP-paket från den angivna IP-instansen. Om det finns IP-paket i kön för rå paket tar emot returneras det första (äldsta) paketet till anroparen. Annars kan anroparen pausa som anges av väntealternativet om det inte finns några tillgängliga paket.

*Om NX_SUCCESS returneras ansvarar programmet för att frigöra det mottagna paketet när det inte längre behövs.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **packet_ptr** Pekare till pekare för att placera det mottagna rådata-IP-paketet i.
- **wait_option** Definierar hur tjänsten beter sig om det inte finns några råa IP-paket tillgängliga. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Ip-rådatapaket tas emot.
- **NX_NO_PACKET** (0x01) Inget paket var tillgängligt.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-adress eller returpaket pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a>Se även

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

Skicka RÅ-IP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a>Description

Den här tjänsten skickar ett obearbetat IP-paket till målets IP-adress. Observera att den här rutinen returneras omedelbart och det är därför inte känt om IP-paketet faktiskt har skickats. Nätverksdrivrutinen ansvarar för att frigöra paketet när överföringen är klar.

För ett multihome-system använder NetX mål-IP-adressen för att hitta ett lämpligt nätverksgränssnitt och använder IP-adressen för gränssnittet som källadress. Om mål-IP-adressen sänds eller multicast används det första giltiga gränssnittet. Program använder ***nx_ip_raw_packet_interface_send*** i det här fallet.

*Om inget fel returneras ska programmet inte släppa paketet efter det här anropet. Detta leder till oförutsägbara resultat eftersom nätverksdrivrutinen släpper paketet efter överföringen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **packet_ptr** Pekare till det råa IP-paket som ska skickas.
- **destination_ip** Mål-IP-adress, som kan vara en specifik värd-IP-adress, en nätverkssändning, en intern loop-back eller en multicast-adress.
- **type_of_service** Definierar typen av tjänst för överföringen. De juridiska värdena är följande:
- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)


### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IP-råpaketssändning initierad.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-adress.
- **IP-NX_NOT_ENABLED** (0x14) Raw är inte aktiverad.
- **NX_OPTION_ERROR** (0x0A) Ogiltig typ av tjänst.
- **NX_UNDERFLOW** (0x02) Det finns inte tillräckligt med utrymme för att lägga till ett IP-huvud i paketet.
- **NX_OVERFLOW** -paket (0x03) är ogiltig.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-adress eller paket pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_receive, nx_ip_raw_packet_send,
- nx_ip_raw_packet_interface_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

Lägga till statisk väg i routningstabellen

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en post i den statiska routningstabellen. Observera att *next_hop* måste vara direkt åtkomlig från någon av de lokala nätverksenheterna.

*Observera att ip_ptr måste peka på en giltig NetX IP-struktur, och NetX-biblioteket måste byggas med en NX_ENABLE_IP_STATIC_ROUTING definieras för att använda den här tjänsten. Som standard byggs NetX utan att NX_ENABLE_IP_STATIC_ROUTING definieras.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **network_address** Målnätverksadress i värdbyteordning
- **net_mask** Målnätverksmask i värdbyteordning
- **next_hop** Nästa hoppadress för målnätverket, i värdbyteordning

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) post läggs till i den statiska routningstabellen.
- **NX_OVERFLOW** (0x03) Statisk routningstabell är full.
- **NX_NOT_SUPPORTED** (0x4B) Den här funktionen kompileras inte i.
- **NX_IP_ADDRESS_ERROR** (0x21) Nästa hopp kan inte nås direkt via lokala gränssnitt.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0x07) Ogiltig ip_ptr pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

Ta bort statisk väg från routningstabellen

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en post från den statiska routningstabellen.

*Observera att ip_ptr måste peka på en giltig NetX IP-struktur, och NetX-biblioteket måste byggas med en NX_ENABLE_IP_STATIC_ROUTING definieras för att använda den här tjänsten. Som standard byggs NetX utan att NX_ENABLE_IP_STATIC_ROUTING definieras.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **network_address** Målnätverksadress i värdbyteordning.
- **net_mask** Målnätverksmask i värdbyteordning.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a>Se även

- nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add

## <a name="nx_ip_status_check"></a>nx_ip_status_check

Kontrollera status för en IP-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten kontrollerar och kan eventuellt vänta på den angivna statusen för det primära nätverksgränssnittet för en tidigare skapad IP-instans. För att få status på sekundära gränssnitt ska programmen använda tjänsten ***nx_ip_interface_status_check.***

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **needed_status** IP-status begärd, definierad i bitkartform enligt följande:
- NX_IP_INITIALIZE_DONE (0x0001)
- NX_IP_ADDRESS_RESOLVED (0x0002)
- NX_IP_LINK_ENABLED (0x0004)
- NX_IP_ARP_ENABLED (0x0008)
- NX_IP_UDP_ENABLED (0x0010)
- NX_IP_TCP_ENABLED (0x0020)
- NX_IP_IGMP_ENABLED (0x0040)
- NX_IP_RARP_COMPLETE (0x0080)
- NX_IP_INTERFACE_LINK_ENABLED (0x0100)
- **actual_status** Pekare till mål för faktiska bitar som angetts.
- **wait_option** Definierar hur tjänsten beter sig om de begärda statusbitarna inte är tillgängliga. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad IP-statuskontroll.
- **NX_NOT_SUCCESSFUL** (0x43) Statusbegäran nöjdes inte inom den angivna tidsgränsen.
- **NX_PTR_ERROR** (0x07) IP-pekare är eller har blivit ogiltig, eller så är den faktiska status pekaren ogiltig.
- **NX_OPTION_ERROR** (0x0a) Statusalternativet Ogiltigt krävs.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize

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

### <a name="description"></a>Description

Den här tjänsten allokerar ett paket från den angivna poolen och justerar förberedelse pekaren i paketet enligt den typ av paket som angetts. Om inget paket är tillgängligt pausar tjänsten enligt det angivna väntealternativet.

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till paketpool som skapats tidigare.
- **packet_ptr** Pekare till pekaren för den allokerade paket pekaren.
- **packet_type** Definierar vilken typ av paket som begärs. Se "Paketpooler" på sidan 49 i kapitel 3 för en lista över pakettyper som stöds.
- **wait_option** Definierar väntetiden i tick om det inte finns några paket tillgängliga i paketpoolen. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Allokera ett lyckat paket.
- **NX_NO_PACKET** (0x01) Inget paket tillgängligt.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_INVALID_PARAMETERS** (0x4D) Paketstorleken stöder inte protokoll.
- **NX_OPTION_ERROR** (0x0A) Ogiltig pakettyp.
- **NX_PTR_ERROR** (0x07) Ogiltig pool eller paketretur pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltigt väntealternativ från icke-läst.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR (programnätverksdrivrutiner). Väntealternativet måste vara NX_NO_WAIT när det används i ISR eller i timerkontext.

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
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

### <a name="description"></a>Description

Den här tjänsten kopierar informationen i det angivna paketet till ett eller flera nya paket som allokeras från den angivna paketpoolen. Om det lyckas returneras pekaren till det nya paketet i målet som visas av **new_packet_ptr**.

### <a name="parameters"></a>Parametrar

- **packet_ptr** Pekare till källpaketet.
- **new_packet_ptr** Pekare till målet för var pekaren ska returneras till den nya kopian av paketet.
- **pool_ptr** Pekare till den tidigare skapade paketpoolen som används för att allokera ett eller flera paket för kopian.
- **wait_option** Definierar hur tjänsten väntar om det inte finns några tillgängliga paket. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckad paketkopiering.
- **NX_NO_PACKET** (0x01) Paket som inte är tillgängligt för kopiering.
- **NX_INVALID_PACKET** (0x12) Tomt källpaket eller kopiering misslyckades.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_INVALID_PARAMETERS** (0x4D) Paketstorleken stöder inte protokoll.
- **NX_PTR_ERROR** (0x07) Ogiltig pool, paket eller mål pekare.
- **NX_UNDERFLOW** (0x02) Ogiltig pekare för paketförberedelser.
- **NX_OVERFLOW** (0x03) Pekare för ogiltigt paketfördr dess tillägg.
- **NX_CALLER_ERROR** (0x11) Ett väntealternativ angavs vid initieringen eller i en ISR.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append

Lägga till data i slutet av paketet

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten lägger till data i slutet av det angivna paketet. Det angivna dataområdet kopieras till paketet. Om det inte finns tillräckligt med minne tillgängligt och funktionen för kedjade paket är aktiverad, allokeras ett eller flera paket för att uppfylla begäran. Om funktionen för kedjade paket inte är *aktiverad NX_SIZE_ERROR* returneras.

### <a name="parameters"></a>Parametrar

- **packet_ptr** Paket pekare.
- **data_start** Pekare till början av användarens dataområde som ska läggas till i paketet.
- **data_size** Storleken på användarens dataområde.
- **pool_ptr** Pekare till paketpoolen som ett annat paket ska allokeras från om det inte finns tillräckligt med utrymme i det aktuella paketet.
- **wait_option** Definierar hur tjänsten beter sig om det inte finns några tillgängliga paket. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckat paket.
- **NX_NO_PACKET** (0x01) Inget paket tillgängligt.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop *till tx_thread_wait_abort*.
- **NX_INVALID_PARAMETERS** paketstorlek (0x4D) stöder inte protokoll.
- **NX_UNDERFLOW** (0x02) pekare är mindre än nyttolastens start.
- **NX_OVERFLOW** (0x03) Pekaren är större än nyttolastens slut.
- **NX_PTR_ERROR** (0x07) Ogiltig pool, paket eller datapekare.
- **NX_SIZE_ERROR** (0x09) Ogiltig datastorlek.
- **NX_CALLER_ERROR** (0x11) Ogiltigt väntealternativ från oläst.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR (programnätverksdrivrutiner)

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

### <a name="description"></a>Description

Den här tjänsten kopierar data från ett NetX-paket (eller paketkedja) med början vid den angivna förskjutningen från paketförberedaren för den angivna storleken i byte till den angivna bufferten. Antalet byte som kopieras returneras i *bytes_copied.* Den här tjänsten tar inte bort data från paketet och justerar inte heller den förberedande pekaren eller annan intern tillståndsinformation.

### <a name="parameters"></a>Parametrar

- **packet_ptr** Pekare till paket som ska extraheras
- **offset** Offset from the current prepend pointer.Offset from the current prepend pointer.Offset from the current prepend pointer.
- **buffer_start** Pekare till start av spara buffert
- **buffer_length** Antal byte som ska kopieras
- **bytes_copied** Antal byte som faktiskt kopierats

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad paketkopiering
- **NX_PACKET_OFFSET_ERROR** (0x53) Ogiltigt förskjutningsvärde har angetts
- **NX_PTR_ERROR** (0x07) Ogiltig paket pekare eller buffert pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

### <a name="description"></a>Description

Den här tjänsten kopierar data från det angivna paketet till den angivna bufferten. Det faktiska antalet kopierade byte returneras i det mål som bytes_copied **.**

Observera att den här tjänsten inte ändrar paketets interna tillstånd. De data som hämtas är fortfarande tillgängliga i paketet.

*Målbufferten måste vara tillräckligt stor för paketets innehåll. Annars skadas minnet, vilket orsakar oförutsägbara resultat.*

### <a name="parameters"></a>Parametrar

- **packet_ptr** Pekare till källpaketet.
- **buffer_start** Pekare till början av buffertområdet.
- **bytes_copied** Pekare till målet för antalet kopierade byte.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckade paketdata hämtas.
- **NX_INVALID_PACKET** (0x12) Ogiltigt paket.
- **NX_PTR_ERROR** (0x07) Ogiltigt paket, buffertstart eller kopierad pekare för byte.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_packet_data_extract_offset, nx_packet_length_get,
- nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get

Hämta längden på paketdata

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a>Description

Den här tjänsten hämtar längden på data i det angivna paketet.

### <a name="parameters"></a>Parametrar

- **packet_ptr** Pekare till paketet.
- **längd** Mål för paketlängden.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create

Skapa paketpool i angivet minnesområde

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en paketpool med den angivna paketstorleken i det minnesområde som anges av användaren.

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till paketpoolens kontrollblock.
- **namn** Pekare till programmets namn för paketpoolen.
- **payload_size** Antal byte i varje paket i poolen. Det här värdet måste vara minst 40 byte och måste också vara jämnt delbart med 4.
- **memory_ptr** Pekare till det minnesområde som paketpoolen ska placeras i. Pekaren bör justeras mot en ULONG-gräns.
- **memory_size** Storleken på poolens minnesområde.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad paketpool som skapas.
- **NX_PTR_ERROR** (0x07) Ogiltig pool eller minnespekare.
- **NX_SIZE_ERROR** (0x09) Ogiltig block- eller minnesstorlek.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

Ta bort paketpool som skapats tidigare

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en paketpool som skapats tidigare. NetX söker efter trådar som för närvarande är inaktiverade på paket i paketpoolen och tar bort instängningen.

### <a name="parameters"></a>Parametrar

- **pool_ptr** Block pekare för paketpoolskontroll.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Borttagna paketpooler.
- **NX_PTR_ERROR** (0x07) Ogiltig poolpekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

Hämta information om en paketpool

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

### <a name="description"></a>Description

Den här tjänsten hämtar information om den angivna paketpoolen.

*Om en mål pekare NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till paketpool som skapats tidigare.
- **total_packets** Pekare till mål för det totala antalet paket i poolen.
- **free_packets** Pekare till mål för det totala antalet för närvarande kostnadsfria paket.
- **empty_pool_requests** Pekare till målet för det totala antalet allokeringsbegäranden när poolen var tom.
- **empty_pool_suspensions** Pekare till mål för det totala antalet tomma pooluppstängningar.
- **invalid_packet_releases** Pekare till målet för det totala antalet ogiltiga paketutgåningar.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Information om lyckad paketpool.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar och timers

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release

Frisläpp tidigare allokerat paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

Den här tjänsten släpper ett paket, inklusive eventuella ytterligare paket som är kedjade till det angivna paketet. Om en annan tråd blockeras vid paketallokering får den paketet och återupptas.

*Programmet måste förhindra att ett paket frigörs mer än en gång, eftersom det kan orsaka oförutsägbara resultat.*

### <a name="parameters"></a>Parametrar

- **packet_ptr** Paket pekare.


### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckad paketsläppning.
- **NX_PTR_ERROR** (0x07) Ogiltig paket pekare.
- **NX_UNDERFLOW** (0x02) Förberedelsepekaren är mindre än nyttolastens start.
- **NX_OVERFLOW** (0x03)-pekare är större än nyttolastens slut.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR (programnätverksdrivrutiner)

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a>Se även

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

Släppa ett överfört paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

För icke-TCP-paket släpper den här tjänsten ett överfört paket, inklusive eventuella ytterligare paket som är kedjade till det angivna paketet. Om en annan tråd blockeras vid paketallokering får den paketet och återupptas. För ett överfört TCP-paket markeras paketet som överfört men släpps inte förrän paketet har bekräftats. Den här tjänsten anropas vanligtvis från programmets nätverksdrivrutin när ett paket har överförts.

*Nätverksdrivrutinen bör ta bort det fysiska mediehuvudet och justera paketets längd innan den här tjänsten anropas.*

### <a name="parameters"></a>Parametrar

- **packet_ptr** Paket pekare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad sändning av paket.
- **NX_PTR_ERROR** (0x07) Felaktig paketpekare.
- **NX_UNDERFLOW** (0x02) pekare är mindre än nyttolastens start.
- **NX_OVERFLOW** (0x03) Pekaren är större än nyttolastens slut.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers, programnätverksdrivrutiner (inklusive ISR:er)

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

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
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable

Inaktivera RARP (Reverse Address Resolution Protocol)

### <a name="prototype"></a>Prototyp

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar RARP-komponenten för NetX för den specifika IP-instansen. För ett multihome-system inaktiverar den här tjänsten RARP i alla gränssnitt.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad RARP-inaktivering.
- **NX_NOT_ENABLED** (0x14) RARP har inte aktiverats.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a>Se även

- nx_rarp_enable, nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable

Aktivera RARP (Reverse Address Resolution Protocol)

### <a name="prototype"></a>Prototyp

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar RARP-komponenten för NetX för den specifika IP-instansen. RARP-komponenterna söker igenom alla anslutna nätverksgränssnitt efter noll IP-adress. En noll IP-adress anger att gränssnittet inte har IP-adresstilldelning ännu. RARP försöker matcha IP-adressen genom att aktivera RARP-processen i det gränssnittet.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad RARP-aktivera.
- **IP-NX_IP_ADDRESS_ERROR** (0x21) är redan giltig.
- **NX_ALREADY_ENABLED** (0x15) RARP har redan aktiverats.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a>Se även

- nx_rarp_disable, nx_rarp_info_get

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

### <a name="description"></a>Description

Den här tjänsten hämtar information om RARP-aktiviteter för den angivna IP-instansen.

*Om en mål pekare NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **rarp_requests_sent** Pekare till mål för det totala antalet RARP-begäranden som skickats.
- **rarp_responses_received** Pekare till mål för det totala antalet RARP-svar som tagits emot.
- **rarp_invalid_messages** Pekare till målet för det totala antalet ogiltiga meddelanden.


### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckad hämtning av RARP-information.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_rarp_disable, nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize

Initiera NetX-system

### <a name="prototype"></a>Prototyp

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a>Description

Den här tjänsten initierar de grundläggande NetX-systemresurserna som förberedelse för användning. Det bör anropas av programmet under initieringen och innan något annat NetX-anrop görs.

### <a name="parameters"></a>Parametrar

Ingen

### <a name="return-values"></a>Returvärden

Ingen

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers, ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

Binda klientens TCP-socket till TCP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten binder den tidigare skapade TCP-klientsocketen till den angivna TCP-porten. Giltiga TCP-sockets sträcker sig från 0 till 0xFFFF. Om den angivna TCP-porten inte är tillgänglig pausar tjänsten enligt det angivna väntealternativet.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till tcp socketinstans som skapats tidigare.
- **port** Portnummer som ska bindas (1 till 0xFFFF). Om portnumret är NX_ANY_PORT (0x0000) söker IP-instansen efter nästa kostnadsfria port och använder den för bindningen.
- **wait_option** Definierar hur tjänsten beter sig om porten redan är bunden till en annan socket. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socketbindning.
- **NX_ALREADY_BOUND** (0x22) Den här socketen är redan bunden till en annan TCP-port.
- **NX_PORT_UNAVAILABLE** (0x23) Porten är redan bunden till en annan socket.
- **NX_NO_FREE_PORTS** (0x45) Ingen kostnadsfri port.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop *till tx_thread_wait_abort*.
- **NX_INVALID_PORT** (0x46) Ogiltig port.
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

Anslut TCP-socket för klient

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten ansluter den tidigare skapade och bundna TCP-klientsocketen till den angivna serverns port. Giltiga TCP-serverportar sträcker sig från 0 till 0xFFFF. Om anslutningen inte slutförs omedelbart pausas tjänsten enligt det angivna väntealternativet.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till tcp socketinstans som skapats tidigare.
- **server_ip** Serverns IP-adress.
- **server_port** Serverportnummer att ansluta till (1 till 0xFFFF).
- **wait_option** Definierar hur tjänsten beter sig när anslutningen upprättas. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socketanslutning.
- **NX_NOT_BOUND** (0x24) Socket är inte bunden.
- **NX_NOT_CLOSED** (0x35) Socket är inte i stängt tillstånd.
- **NX_IN_PROGRESS** (0x37) Ingen väntetid har angetts, anslutningsförsöket pågår.
- **NX_INVALID_INTERFACE** (0x4C) Ogiltigt gränssnitt har angetts.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig server-IP-adress.
- **NX_INVALID_PORT** (0x46) Ogiltig port.
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

Hämta portnummer som är bundet till klientens TCP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a>Description

Den här tjänsten hämtar det portnummer som är associerat med socketen, vilket är användbart för att hitta porten som allokerades av NetX i situationer där NX_ANY_PORT angavs när socketen bindas.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till tcp socketinstans som skapats tidigare.
- **port_ptr** Pekare till mål för returportnumret. Giltiga portnummer är (1 till 0xFFFF).

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socketbindning.
- **NX_NOT_BOUND** (0x24) Den här socketen är inte bunden till en port.
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare eller portretur pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

Ta bort TCP-klientsocket från TCP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

Den här tjänsten släpper bindningen mellan TCP-klientsocketen och en TCP-port. Om det finns andra trådar som väntar på att binda en annan socket till samma portnummer, binds den första pausade tråden till den här porten.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till tcp socketinstans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socket-unbind.
- **NX_NOT_BOUND** (0x24) Socket var inte bunden till någon port.
- **NX_NOT_CLOSED** (0x35) Socket har inte frånkopplats.
- **NX_PTR_ERROR** (0x07) Felaktig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_enable"></a>nx_tcp_enable

Aktivera TCP-komponenten för NetX

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Med den här tjänsten Transmission Control Protocol (TCP)-komponenten i NetX. När det är aktiverat kan TCP-anslutningar upprättas av programmet.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Tcp-aktivera.
- **TCP NX_ALREADY_ENABLED** (0x15) har redan aktiverats.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

Hitta nästa tillgängliga TCP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a>Description

Den här tjänsten försöker hitta en kostnadsfri TCP-port (obunden) från den port som programmet har angett. Söklogiken omsluts om sökningen når det maximala portvärdet för 0xFFFF. Om sökningen lyckas returneras den kostnadsfria porten i variabeln som free_port_ptr *.*

*Den här tjänsten kan anropas från en annan tråd och returnera samma port. För att förhindra det här rastillståndet kanske programmet vill placera den här tjänsten och den faktiska klientsocketen bindas under skyddet av en mutex.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **port** Portnummer för att börja söka på (1 till 0xFFFF).
- **free_port_ptr** Pekare till returvärdet för den kostnadsfria målporten.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Hitta den kostnadsfria porten.
- **NX_NO_FREE_PORTS** (0x45) Inga lediga portar hittades.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.
- **NX_INVALID_PORT** (0x46) Det angivna portnumret är ogiltigt.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
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

### <a name="description"></a>Description

Den här tjänsten hämtar information om TCP-aktiviteter för den angivna IP-instansen.

*Om en mål pekare NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **tcp_packets_sent** Pekare till mål för det totala antalet TCP-paket som skickats.
- **tcp_bytes_sent** Pekare till mål för det totala antalet TCP-byte som skickats.
- **tcp_packets_received** Pekare till målet för det totala antalet MOTTAGNA TCP-paket.
- **tcp_bytes_received** Pekare till mål för det totala antalet mottagna TCP-byte.
- **tcp_invalid_packets** Pekare till målet för det totala antalet ogiltiga TCP-paket.
- **tcp_receive_packets_dropped** Pekare till mål för det totala antalet TCP-mottagningspaket som tagits bort.
- **tcp_checksum_errors** Pekare till målet för det totala antalet TCP-paket med kontrollsummafel.
- **tcp_connections** Pekare till målet för det totala antalet TCP-anslutningar.
- **tcp_disconnections** Pekare till målet för det totala antalet TCP-frånkopplingar.
- **tcp_connections_dropped** Pekare till mål för det totala antalet TCP-anslutningar som har tagits bort.
- **tcp_retransmit_packets** Pekare till målet för det totala antalet TCP-paket som har återöversatts.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad TCP-informationshämtning.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

Acceptera TCP-anslutning

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten accepterar (eller förbereder för att acceptera) en TCP-klientsocketanslutningsbegäran för en port som tidigare har ställts in för lyssning. Den här tjänsten kan anropas omedelbart efter att programmet anropar lyssna- eller lyssnartjänsten, eller efter att återanropsrutinen för lyssnande anropas när klientanslutningen faktiskt finns. Om det inte går att upprätta en anslutning direkt pausas tjänsten enligt det angivna väntealternativet.

*Programmet måste anropa **nx_tcp_server_socket_unaccept** när anslutningen inte längre behövs för att ta bort serversocketens bindning till serverporten.*

*Rutiner för programanrop anropas inifrån IP-adressens hjälptråd.*

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till TCP-serverns socketkontrollblock.
- **wait_option** Definierar hur tjänsten beter sig när anslutningen upprättas. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)


### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckad TCP-serversocket accept (passiv anslutning).
- **NX_NOT_LISTEN_STATE** (0x36) Den angivna serversocketen är inte i ett lyssnande tillstånd.
- **NX_IN_PROGRESS** (0x37) Ingen väntetid har angetts, anslutningsförsöket pågår.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop *till tx_thread_wait_abort*.
- **NX_PTR_ERROR** (0x07) Socket-pekarfel.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

Aktivera lyssnande efter klientanslutning på TCP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a>Description

Med den här tjänsten kan du lyssna efter en klientanslutningsbegäran på den angivna TCP-porten. När en klientanslutningsbegäran tas emot binds den angivna serversocketen till den angivna porten och den angivna funktionen för lyssnande återanrop anropas.

Bearbetningen av lyssnaranropsrutinen är helt upp till programmet. Den kan innehålla logik för att väcka en programtråd som därefter utför en accept-åtgärd. Om programmet redan har en tråd som pausas vid bearbetning av accept för den här socketen kanske inte återanropsrutinen för lyssnande behövs.

Om programmet vill hantera ytterligare klientanslutningar på samma port ***måste nx_tcp_server_socket_relisten*** anropas med en tillgänglig socket (en socket med tillståndet STÄNGD) för nästa anslutning. Tills tjänsten för återlyssning anropas köas ytterligare klientanslutningar. När det maximala ködjupet överskrids tas den äldsta anslutningsbegäran bort och den nya anslutningsbegäran köas. Maximalt ködjup anges av den här tjänsten.

*Rutiner för programanrop anropas från den interna IP-hjälptråden.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **port** Portnummer att lyssna på (1 till 0xFFFF).
- **socket_ptr** Pekare till socket som ska användas för anslutningen.
- **listen_queue_size** Antal klientanslutningsbegäranden som kan köas.
- **listen_callback** Programfunktion som anropas när anslutningen tas emot. Om ett NULL-värde anges inaktiveras funktionen för att lyssna motringning.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad TCP-portlyssning aktivera.
- **NX_MAX_LISTEN** (0x33) Inga fler strukturer för lyssna-begäran är tillgängliga. Konstanten NX_MAX_LISTEN_REQUESTS i nx_api.h definierar hur många aktiva lyssnarbegäranden som är möjliga.
- **NX_NOT_CLOSED** (0x35) Den angivna serversocketen är inte i stängt tillstånd.
- **NX_ALREADY_BOUND** (0x22) Den angivna serversocketen är redan bunden till en port.
- **NX_DUPLICATE_LISTEN** (0x34) Det finns redan en aktiv lyssnarbegäran för den här porten.
- **NX_INVALID_PORT** (0x46) Ogiltig port har angetts.
- **NX_PTR_ERROR** (0x07) Ogiltig IP- eller socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

Lyssna efter klientanslutning på TCP-port igen

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

Den här tjänsten anropas när en anslutning har tagits emot på en port som tidigare har ställts in för lyssning. Huvudsyftet med den här tjänsten är att tillhandahålla en ny serversocket för nästa klientanslutning. Om en anslutningsbegäran köas bearbetas anslutningen omedelbart under det här tjänstsamtalet.

*Samma återanropsrutin som anges av den ursprungliga lyssna-begäran anropas också när det finns en anslutning för den nya serversocketen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **port** Portnummer att lyssna på igen (1 till 0xFFFF).
- **socket_ptr** Socket som ska användas för nästa klientanslutning.

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckad TCP-port lyssnar om.
- **NX_NOT_CLOSED** (0x35) Den angivna serversocketen är inte i stängt tillstånd.
- **NX_ALREADY_BOUND** (0x22) Den angivna serversocketen är redan bunden till en port.
- **NX_INVALID_RELISTEN** (0x47) Det finns redan en giltig socket-pekare för den här porten eller så har den angivna porten ingen aktiv lyssnarbegäran.
- **NX_CONNECTION_PENDING** (0x48) Samma som NX_SUCCESS, förutom att det fanns en anslutningsbegäran i kö och den bearbetades under anropet.
- **NX_INVALID_PORT** (0x46) Ogiltig port har angetts.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-adress eller lyssnar pekare för återanrop.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

Ta bort socketassociatiering med lyssningsport

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort associationen mellan den här serversocketen och den angivna serverporten. Programmet måste anropa den här tjänsten efter en frånkoppling eller efter ett misslyckat accept-anrop.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till tidigare konfigurera server socket-instans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Unaccept för lyckad serversocket.
- **NX_NOT_LISTEN_STATE** (0x36) Server socket är i felaktigt tillstånd och är förmodligen inte frånkopplad.
- **NX_PTR_ERROR** (0x07) Felaktig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

Inaktivera lyssnande efter klientanslutning på TCP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar lyssnandet efter en klientanslutningsbegäran på den angivna TCP-porten.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **port** Antalet portar som lyssnar (0 till och med 0xFFFF).

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad TCP-lyssnar inaktivera.
- **NX_ENTRY_NOT_FOUND** (0x16) Lyssnar har inte aktiverats för den angivna porten.
- **NX_INVALID_PORT** (0x46) Ogiltig port har angetts.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

Hämtar antalet tillgängliga byte för hämtning

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a>Description

Den här tjänsten hämtar antalet byte som är tillgängliga för hämtning i den angivna TCP-socketen. Observera att TCP-socketen redan måste vara ansluten.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till tidigare skapade och anslutna TCP-socketar.
- **bytes_available** Pekare till mål för tillgängliga byte.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) tjänsten körs. Antalet byte som är tillgängliga för läsning returneras till anroparen.
- **NX_NOT_CONNECTED** (0x38) Socket är inte i ett anslutet tillstånd.
- **NX_PTR_ERROR** (0x07) Ogiltiga pekare.
- **TCP NX_NOT_ENABLED** (0x14) är inte aktiverat.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

Skapa TCP-klient eller serversocket

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

### <a name="description"></a>Description

Den här tjänsten skapar en TCP-klient eller serversocket för den angivna IP-instansen.

*Rutiner för programanrop anropas från tråden som är associerad med den här IP-instansen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **socket_ptr** Pekare till det nya TCP-socketkontrollblocket.
- **namn** Programnamn för den här TCP-socketen.
- **type_of_service** Definierar typen av tjänst för överföringen. De juridiska värdena är följande:

- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)

- **fragment**  Anger om IP-fragmentering tillåts eller inte. Om NX_FRAGMENT_OKAY (0x0) anges tillåts IP-fragmentering. Om NX_DONT_FRAGMENT (0x4000) anges inaktiveras IP-fragmentering.
- **time_to_live** Anger det 8-bitars värde som definierar hur många routrar det här paketet kan passera innan det slängs. Standardvärdet anges av NX_IP_TIME_TO_LIVE.
- **window_size** Definierar det maximala antalet byte som tillåts i mottagningskön för den här socketen
- **urgent_data_callback** Programfunktion som anropas när brådskande data identifieras i mottagningsströmmen. Om det här NX_NULL ignoreras brådskande data.
- **disconnect_callback** Programfunktion som anropas när en frånkoppling utfärdas av socketen i den andra änden av anslutningen. Om det här NX_NULL inaktiveras återanropsfunktionen för frånkoppling.

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckad TCP-klientsocket för att skapa.
- **NX_OPTION_ERROR** (0x0A) Ogiltig tjänsttyp, fragment, ogiltig fönsterstorlek eller time tolive-alternativ.
- **NX_PTR_ERROR** (0x07) Ogiltig IP- eller socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

Ta bort TCP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en TCP-socket som skapats tidigare. Om socketen fortfarande är bunden eller ansluten returnerar tjänsten en felkod.

### <a name="parameters"></a>Parametrar

- **socket_ptr** TCP-socket har skapats tidigare

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socket-borttagning.
- **NX_NOT_CREATED** (0x27) Socket skapades inte.
- **NX_STILL_BOUND** (0x42) Socket är fortfarande bunden.
- **NX_PTR_ERROR** (0x07) Felaktig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

Koppla från klient- och serversocketanslutningar

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten kopplar från en upprättad klient- eller serversocketanslutning. En frånkoppling av en serversocket ska följas av en icke-acceptsbegäran, medan en klientsocket som är frånkopplad lämnas i ett tillstånd som är redo för en annan anslutningsbegäran. Om frånkopplingsprocessen inte kan slutföras omedelbart pausas tjänsten enligt det angivna väntealternativet.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en tidigare ansluten klient- eller serversocketinstans.
- **wait_option** Definierar hur tjänsten beter sig medan frånkopplingen pågår. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socketkoppling.
- **NX_NOT_CONNECTED** (0x38) Angiven socket är inte ansluten.
- **NX_IN_PROGRESS** (0x37) Frånkoppling pågår har ingen väntetid angetts.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_PTR_ERROR** (0x07) Felaktig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify

Installera tcp disconnect complete notify callback function (Installera TCP-frånkoppling av fullständig avanropsfunktion)

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

Den här tjänsten registrerar en återanropsfunktion som anropas när en socket-frånkoppling har slutförts. Funktionen för att koppla från TCP-socketen är tillgänglig om NetX har skapats med alternativet

- ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definieras.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en tidigare ansluten klient- eller serversocketinstans.
- **tcp_disconnect_complete_notify** Återanropsfunktionen som ska installeras.

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Har registrerat återanropsfunktionen.
- **NX_NOT_SUPPORTED** (0x4B) Den utökade av meddela-funktionen är inte inbyggd i NetX-biblioteket
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) TCP-funktionen är inte aktiverad.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a>Se även

- nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,
- nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify

Ställ in TCP-upprätta funktionen för att meddela motringning

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

Den här tjänsten registrerar en återanropsfunktion som anropas när en TCP-socket upprättar en anslutning. Funktionen för att etablera återanrop för TCP-socket är tillgänglig om NetX har skapats med ***alternativet NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definieras.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en tidigare ansluten klient- eller serversocketinstans.
- **tcp_establish_notify** Återanropsfunktionen anropas när en TCP-anslutning har upprättats.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Anger funktionen notify.
- **NX_NOT_SUPPORTED** (0x4B) Den utökade av meddela-funktionen är inte inbyggd i NetX-biblioteket
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) TCP har inte aktiverats av programmet.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a>Se även

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

Hämta information om TCP-socketaktiviteter

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

### <a name="description"></a>Description

Den här tjänsten hämtar information om TCP-socketaktiviteter för den angivna TCP socket-instansen.

*Om en mål pekare NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till tcp socketinstans som skapats tidigare.
- **tcp_packets_sent** Pekare till mål för det totala antalet TCP-paket som skickats på socket.
- **tcp_bytes_sent** Pekare till mål för det totala antalet TCP-byte som skickats på socket.
- **tcp_packets_received** Pekare till målet för det totala antalet TCP-paket som tagits emot på socketen.
- **tcp_bytes_received** Pekare till mål för det totala antalet TCP-byte som tagits emot på socket.
- **tcp_retransmit_packets** Pekare till målet för det totala antalet TCP-paketöverföringar.
- **tcp_packets_queued** Pekare till mål för det totala antalet köade TCP-paket på socket.
- **tcp_checksum_errors** Pekare till målet för det totala antalet TCP-paket med kontrollsummafel på socket.
- **tcp_socket_state** Pekare till målet för socketens aktuella tillstånd.
- **tcp_transmit_queue_depth** Pekare till målet för det totala antalet överföringspaket som fortfarande står i kö och väntar på ACK.
- **tcp_transmit_window** Pekare till mål för den aktuella överföringsfönstrets storlek.
- **tcp_receive_window** Pekare till målet för den aktuella mottagningsfönstrets storlek.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad hämtning av TCP-socketinformation.
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="return-values"></a>Returvärden

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

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

Hämta MSS för socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Description

Den här tjänsten hämtar den angivna socketens lokala maximal segmentstorlek (MSS).

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till socket som skapats tidigare.
- **mss** Mål för att returnera MSS.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad MSS-get.
- **NX_PTR_ERROR** (0x07) Ogiltig socket eller MSS-mål pekare.
- **NX_NOT_ENABLED** (0x14) TCP är inte aktiverat.
- **NX_CALLER_ERROR** (0x11) Anroparen är inte en tråd eller initiering.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a>Se även

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

Hämta MSS för peer-TCP-socketen

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Description

Den här tjänsten hämtar maximal segmentstorlek (MSS) som annonseras av peer-socketen.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till tidigare skapade och anslutna socketar.
- **mss** Mål för att returnera MSS.


### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad peer-MSS hämta.
- **NX_PTR_ERROR** (0x07) Ogiltig socket eller MSS-mål pekare.
- **NX_NOT_ENABLED** (0x14) TCP är inte aktiverat.
- **NX_CALLER_ERROR** (0x11) Anroparen är inte en tråd eller initiering.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a>Se även

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
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

### <a name="description"></a>Description

Den här tjänsten anger den angivna socketens maximal segmentstorlek (MSS). Observera att MSS-värdet måste finnas i nätverksgränssnittets IP MTU, vilket ger utrymme för IP- och TCP-huvuden.

Den här tjänsten ska användas innan en TCP-socket startar anslutningsprocessen. Om tjänsten används när en TCP-anslutning har upprättats har det nya värdet ingen effekt på anslutningen.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till socket som skapats tidigare.
- **mss** Värdet för MSS som ska anges.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad MSS-uppsättning.
- **NX_SIZE_ERROR** (0x09) Det angivna MSS-värdet är för stort.
- **NX_NOT_CONNECTED** (0x38) TCP-anslutningen har inte upprättats
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_NOT_ENABLED** (0x14) TCP är inte aktiverat.
- **NX_CALLER_ERROR** (0x11) Anroparen är inte en tråd eller initiering.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>Se även

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

Hämta information om peer-TCP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a>Description

Den här tjänsten hämtar peer-IP-adress och portinformation för den anslutna TCP-socketen via IP-nätverk.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till TCP-socket som skapats tidigare.
- **peer_ip_address** Pekare till mål för peer-IP-adress, i värdbyteordning.
- **peer_port** Pekare till mål för peer-portnummer, i värdbyteordning.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) tjänsten körs. Peer-IP-adress och portnummer returneras till anroparen.
- **NX_NOT_CONNECTED** (0x38) Socket är inte i ett anslutet tillstånd.
- **NX_PTR_ERROR** (0x07) Ogiltiga pekare.
- **NX_NOT_ENABLED** (0x14) TCP är inte aktiverat.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a>Se även

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
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

### <a name="description"></a>Description

Den här tjänsten tar emot TCP-data från den angivna socketen. Om inga data köas på den angivna socketen pausar anroparen baserat på det angivna väntealternativet.

*Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till tcp socketinstans som skapats tidigare.
- **packet_ptr** Pekare till TCP-paket pekare.
- **wait_option** Definierar hur tjänsten beter sig om inga data för närvarande köas på den här socketen. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckad socketdatain mottagning.
- **NX_NOT_BOUND** (0x24) Socket är inte bunden ännu.
- **NX_NO_PACKET** (0x01) Inga data tas emot.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_NOT_CONNECTED** (0x38) Socketen är inte längre ansluten.
- **NX_PTR_ERROR** (0x07) Ogiltig socket eller returnera paket pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

/* Ta emot ett paket från den tidigare skapade och anslutna TCP-klientsocketen. Om inget paket är tillgängligt väntar du på 200 timer tick innan du ger upp. */ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);

/* Om statusen NX_SUCCESS visas det mottagna paketet med "packet_ptr". */

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

Meddela tillämpningen av mottagna paket


### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

Den här tjänsten konfigurerar pekaren för receive notify-funktionen med återanropsfunktionen som anges av programmet. Den här återanropsfunktionen anropas sedan när ett eller flera paket tas emot på socketen. Om en NX_NULL pekare anges inaktiveras notify-funktionen.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till TCP-socketen.
- **tcp_receive_notify** Funktionspekare för programanrop som anropas när ett eller flera paket tas emot på socketen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Ett meddelande om att socketen har lyckats.
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) TCP-funktionen är inte aktiverad.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,
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

### <a name="description"></a>Description

Den här tjänsten skickar TCP-data via en tidigare ansluten TCP-socket. Om mottagarens senast annonserade fönsterstorlek är mindre än den här begäran, pausar tjänsten eventuellt baserat på det angivna väntealternativet. Den här tjänsten garanterar att inga paketdata som är större än MSS skickas till IP-lagret.

*Om inget fel returneras ska programmet inte släppa paketet efter det här anropet. Detta leder till oförutsägbara resultat eftersom nätverksdrivrutinen även försöker släppa paketet efter överföringen.*

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en tidigare ansluten TCP socket-instans.
- **packet_ptr** Pekare för TCP-datapaket.
- **wait_option** Definierar hur tjänsten beter sig om begäran är större än mottagarens fönsterstorlek. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socket-send.
- **NX_NOT_BOUND** (0x24) Socket var inte bunden till någon port.
- **NX_NO_INTERFACE_ADDRESS** (0x50) Inget lämpligt utgående gränssnitt hittades.
- **NX_NOT_CONNECTED** (0x38) Socket är inte längre ansluten.
- **NX_WINDOW_OVERFLOW** (0x39) Begäran är större än mottagarens annonserade fönsterstorlek i byte.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_INVALID_PACKET** (0x12) Paket allokeras inte.
- **NX_TX_QUEUE_DEPTH** (0x49) Maximalt överföringsködjup har nåtts.
- **NX_OVERFLOW** -paket (0x03) är ogiltig.
- **NX_PTR_ERROR** (0x07) Felaktig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.
- **NX_UNDERFLOW** (0x02) Pekaren för paketförberedelser är ogiltig.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a>Se även

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait

### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

Vänta tills TCP-socketen förs in i ett visst tillstånd

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a>Description

Den här tjänsten väntar på att socketen ska ange önskat tillstånd. Om socketen inte är i önskat tillstånd pausar tjänsten enligt det angivna väntealternativet.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en tidigare ansluten TCP socket-instans.
- **desired_state** Önskat TCP-tillstånd. Giltiga TCP-socket-tillstånd definieras på följande sätt:
- NX_TCP_CLOSED (0x01)
- NX_TCP_LISTEN_STATE (0x02)
- NX_TCP_SYN_SENT (0x03)
- NX_TCP_SYN_RECEIVED (0x04)
- NX_TCP_ESTABLISHED (0x05)
- NX_TCP_CLOSE_WAIT (0x06)
- NX_TCP_FIN_WAIT_1 (0x07)
- NX_TCP_FIN_WAIT_2 (0x08)
- NX_TCP_CLOSING (0x09)
- NX_TCP_TIMED_WAIT (0x0A)
- NX_TCP_LAST_ACK (0x0B)
- **wait_option** Definierar hur tjänsten beter sig om det begärda tillståndet inte finns. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Lyckad tillståndsvänte.
- **NX_PTR_ERROR** (0x07) Felaktig socket-pekare.
- **NX_NOT_SUCCESSFUL** (0x43) tillstånd som inte finns inom den angivna väntetiden.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.
- **NX_OPTION_ERROR** (0x0A) Det önskade sockettillståndet är ogiltigt.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback

Installera återanrop för väntetillståndet för tidsend

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

Den här tjänsten registrerar en återanropsfunktion som anropas när TCP-socketen är i väntetidstillstånd. Om du vill använda den här tjänsten måste NetX-biblioteket byggas med alternativet ***NX_ENABLE_EXTENDED_NOTIFY*** definierat.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en tidigare ansluten klient- eller serversocketinstans.
- **tcp_timed_wait_callback** Funktionen för återanrop i tidsväntetid

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Registrerar motringningsfunktionens socket
- **NX_NOT_SUPPORTED** (0x4B) NetX-biblioteket har skapats utan att den utökade av meddela-funktionen är aktiverad.
- **NX_PTR_ERROR** (0x07) Felaktig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **TCP 0x14 funktionen** (NX_NOT_ENABLED) är inte aktiverad.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>Se även

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

Konfigurera socketens överföringsparametrar

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```

### <a name="description"></a>Description

Den här tjänsten konfigurerar olika överföringsparametrar för den angivna TCP-socketen.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till TCP-socketen.
- **max_queue_depth** Maximalt antal paket som får köas för överföring.
- **tidsgräns** Antalet ThreadX-timer tick som en ACK väntar på innan paketet skickas igen.
- **max_retries** Maximalt antal återförsök som tillåts.
- **timeout_shift** Värde för att flytta tidsgränsen för varje efterföljande återförsök. Värdet 0 resulterar i samma tidsgräns mellan efterföljande återförsök. Värdet 1 fördubblar tidsgränsen mellan återförsöken.

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) Konfigurera lyckad överföringssocket.
- **NX_PTR_ERROR** (0x07) Felaktig socket-pekare.
- **NX_OPTION_ERROR** (0x0a) Alternativet Ogiltig ködjup.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **TCP 0x14 funktionen** (NX_NOT_ENABLED) är inte aktiverad.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set

Meddela programmet om uppdateringar av fönsterstorlek

### <a name="prototype"></a>Prototyp

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

Den här tjänsten installerar en uppdateringsrutin för socketfönsteruppdatering. Den här rutinen anropas automatiskt när den angivna socketen tar emot ett paket som anger en ökning av fönsterstorleken för fjärrvärden.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till TCP-socket som skapats tidigare.
- **tcp_window_update_notify** Återanropsrutin anropas när fönsterstorleken ändras. Värdet NULL inaktiverar uppdateringen av fönsterändringen.

### <a name="return-values"></a>Returvärden
- **NX_SUCCESS** (0x00) motringning är installerad på socketen.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_PTR_ERROR** (0x07) Ogiltiga pekare.
- **TCP 0x14 funktionen** (NX_NOT_ENABLED) är inte aktiverad.


### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable

Aktivera UDP-komponenten i NetX

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar UDP-komponenten (User Datagram Protocol) i NetX. När det är aktiverat kan UDP-datagram skickas och tas emot av programmet.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad UDP-aktivera.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_ALREADY_ENABLED** (0x15) Den här komponenten har redan aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a>Se även

- nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
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

### <a name="description"></a>Description

Den här tjänsten söker efter en kostnadsfri UDP-port (obunden) från programmets angivna portnummer. Söklogiken omsluts om sökningen når det maximala portvärdet för 0xFFFF. Om sökningen lyckas returneras den kostnadsfria porten i variabeln som free_port_ptr *.*

*Den här tjänsten kan anropas från en annan tråd och kan returnera samma port. För att förhindra det här rastillståndet kanske programmet vill placera den här tjänsten och den faktiska socketbindningen under skyddet av en mutex.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **port** Portnummer för att starta sökningen (1 till 0xFFFF).
- **free_port_ptr** Pekare till returvariabeln för den kostnadsfria målporten.


### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad hitta kostnadsfri port.
- **NX_NO_FREE_PORTS** (0x45) Inga lediga portar hittades.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.
- **NX_INVALID_PORT** (0x46) Det angivna portnumret är ogiltigt.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
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

### <a name="description"></a>Description

Den här tjänsten hämtar information om UDP-aktiviteter för den angivna IP-instansen.

*Om en mål pekare NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **udp_packets_sent** Pekare till mål för det totala antalet UDP-paket som skickats.
- **udp_bytes_sent** Pekare till mål för det totala antalet UDP-byte som skickats.
- **udp_packets_received** Pekare till målet för det totala antalet UDP-paket som tagits emot.
- **udp_bytes_received** Pekare till mål för det totala antalet UDP-byte som tagits emot.
- **udp_invalid_packets** Pekare till målet för det totala antalet ogiltiga UDP-paket.
- **udp_receive_packets_dropped** Pekare till mål för det totala antalet UDP-mottagningspaket som tagits bort.
- **udp_checksum_errors** Pekare till målet för det totala antalet UDP-paket med kontrollsummafel.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad UDP-informationshämtning.
- **NX_PTR_ERROR** (0x07) Ogiltig IP-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.


### <a name="allowed-from"></a>Tillåts från

Initiering, trådar och timers

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract

Extrahera nätverksparametrar från UDP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a>Description

Den här tjänsten extraherar nätverksparametrar, till exempel IP-adress, peer-portnummer, protokolltyp (den här tjänsten returnerar alltid UDP-typ) från ett paket som tas emot i ett inkommande gränssnitt.

### <a name="parameters"></a>Parametrar

- **packet_ptr** Pekare till paket.
- **ip_address** Pekare till avsändarens IP-adress.
- **protokoll** Pekare till protokoll (UDP).
- **port** Pekare till avsändarens portnummer.
- **interface_index** Pekare till det mottagande gränssnittsindexet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Paketgränssnittsdata har extraherats.
- **NX_INVALID_PACKET** -paket (0x12) innehåller inte NÅGON IP-ram.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

Binda UDP-socket till UDP-port

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten binder den tidigare skapade UDP-socketen till den angivna UDP-porten. Giltiga UDP-sockets sträcker sig från 0 till 0xFFFF. Om det begärda portnumret är bundet till en annan socket väntar den här tjänsten under angiven tidsperiod på att socketen ska ta bort bindningen från portnumret.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en UDP-socketinstans som skapats tidigare.
- **port** Portnummer som ska bindas till (1 till 0xFFFF). Om portnumret är NX_ANY_PORT (0x0000) söker IP-instansen efter nästa kostnadsfria port och använder den för bindningen.
- **wait_option** Definierar hur tjänsten beter sig om porten redan är bunden till en annan socket. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socketbindning.
- **NX_ALREADY_BOUND** (0x22) Den här socketen är redan bunden till en annan port.
- **NX_PORT_UNAVAILABLE** (0x23) Porten är redan bunden till en annan socket.
- **NX_NO_FREE_PORTS** (0x45) Ingen kostnadsfri port.
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop till tx_thread_wait_abort.
- **NX_INVALID_PORT** (0x46) Ogiltig port har angetts.
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_udp_packet_info_extract, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

Hämtar antalet byte som är tillgängliga för hämtning

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a>Description

Den här tjänsten hämtar antalet byte som är tillgängliga för mottagning i den angivna UDP-socketen.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till UDP-socket som skapats tidigare.
- **bytes_available** Pekare till mål för tillgängliga byte.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckade byte tillgänglig hämtning.
- **NX_NOT_SUCCESSFUL** (0x43) Socket är inte bunden till en port.
- **NX_PTR_ERROR** (0x07) Ogiltiga pekare.
- **UDP-funktionen** NX_NOT_ENABLED (0x14) är inte aktiverad.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

Inaktivera kontrollsumma för UDP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar logiken för kontrollsumma för att skicka och ta emot paket på den angivna UDP-socketen. När logiken för kontrollsumma är inaktiverad läses värdet noll in i UDP-huvudets kontrollsummafält för alla paket som skickas via den här socketen. Ett nollvärdesvärde för kontrollsumma i UDP-huvudet signalerar till mottagaren att kontrollsumman inte har beräknats för det här paketet.

Observera också att detta inte har någon effekt om ***NX_DISABLE_UDP_RX_CHECKSUM** _ och _ *_NX_DISABLE_UDP_TX_CHECKSUM_** definieras när du tar emot och skickar UDP-paket.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en UDP-socketinstans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socketkontrollsumma inaktiveras.
- **NX_NOT_BOUND** (0x24) Socket är inte bunden.
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timer

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

Aktivera kontrollsumma för UDP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar logiken för kontrollsumma för att skicka och ta emot paket på den angivna UDP-socketen. Kontrollsumman omfattar hela UDP-dataområdet samt en pseudo-IP-rubrik.

Observera också att detta inte har någon effekt **om NX_DISABLE_UDP_RX_CHECKSUM** **och NX_DISABLE_UDP_TX_CHECKSUM** definieras när du tar emot respektive skickar UDP-paket.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en UDP-socketinstans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socketkontrollsumma aktiveras.
- **NX_NOT_BOUND** (0x24) Socket är inte bunden.
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timer

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
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

### <a name="description"></a>Description

Den här tjänsten skapar en UDP-socket för den angivna IP-instansen.

### <a name="parameters"></a>Parametrar

- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **socket_ptr** Pekare till ny UDP socket control bloc.
- **namn** Programnamn för den här UDP-socketen.
- **type_of_service** Definierar typen av tjänst för överföringen. De juridiska värdena är följande:
    - NX_IP_NORMAL (0x00000000)
    - NX_IP_MIN_DELAY (0x00100000)
    - NX_IP_MAX_DATA (0x00080000)
    - NX_IP_MAX_RELIABLE (0x00040000)
    - NX_IP_MIN_COST (0x00020000)
- **fragment** Anger om IP-fragmentering tillåts eller inte. Om NX_FRAGMENT_OKAY (0x0) anges tillåts IP-fragmentering. Om NX_DONT_FRAGMENT (0x4000) har angetts inaktiveras IP-fragmentering.
- **time_to_live** Anger det 8-bitarsvärde som definierar hur många routrar det här paketet kan passera innan det slängs. Standardvärdet anges av NX_IP_TIME_TO_LIVE.
- **queue_maximum** Definierar det maximala antalet UDP-datagram som kan köas för den här socketen. När kögränsen har nåtts släpps det äldsta UDP-paketet för varje nytt paket som tas emot.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad UDP-socket skapas.
- **NX_OPTION_ERROR** (0x0A) Ogiltigt tjänst-, fragment- eller time-to-live-alternativ.
- **NX_PTR_ERROR** (0x07) Ogiltig IP- eller socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_delete,
- nx_udp_socket_info_get, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete

Ta bort UDP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en UDP-socket som skapats tidigare. Om socketen var bunden till en port måste socketen vara obunden först.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en UDP-socketinstans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socket-borttagning.
- **NX_STILL_BOUND** (0x42) Socket är fortfarande bunden.
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_info_get, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get

Hämta information om UDP-socketaktiviteter

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

### <a name="description"></a>Description

Den här tjänsten hämtar information om UDP-socketaktiviteter för den angivna UDP-socketinstansen.

*Om en mål pekare NX_NULL returneras inte den informationen till anroparen.*

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en UDP-socketinstans som skapats tidigare.
- **udp_packets_sent** Pekare till mål för det totala antalet UDP-paket som skickats på socket.
- **udp_bytes_sent** Pekare till mål för det totala antalet UDP-byte som skickats på socket.
- **udp_packets_received** Pekare till målet för det totala antalet UDP-paket som tagits emot på socket.
- **udp_bytes_received** Pekare till målet för det totala antalet UDP-byte som tagits emot på socketen.
- **udp_packets_queued** Pekare till mål för det totala antalet köade UDP-paket på socket.
- **udp_receive_packets_dropped** Pekare till mål för det totala antalet UDP-mottagningspaket som tagits bort för socket på grund av att köstorleken har överskridits.
- **udp_checksum_errors** Pekare till målet för det totala antalet UDP-paket med kontrollsummafel på socket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad informationshämtning av UDP-socket.
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar och timers

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

Upphämtning av portnummer som är bundet till UDP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a>Description

Den här tjänsten hämtar det portnummer som är associerat med socketen, vilket är användbart för att hitta porten som allokerades av NetX i situationer där NX_ANY_PORT angavs när socketen bindas.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en UDP-socketinstans som skapats tidigare.
- **port_ptr** Pekare till mål för returportnumret. Giltiga portnummer är (1-0xFFFF).

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socketbindning.
- **NX_NOT_BOUND** (0x24) Den här socketen är inte bunden till en port.
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare eller portretur pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

Ta emot datagram från UDP-socket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten tar emot ett UDP-datagram från den angivna socketen. Om inget datagram finns i kö på den angivna socketen pausar anroparen baserat på det angivna väntealternativet.

*Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en UDP-socketinstans som skapats tidigare.
- **packet_ptr** Pekare till UDP-paket pekare för datagram.
- **wait_option** Definierar hur tjänsten beter sig om ett datagram för närvarande inte finns i kö på den här socketen. Väntealternativen definieras på följande sätt:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- timeout-värde i tick (0x00000001 via 0xFFFFFFFE)

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

Meddela tillämpningen av varje mottaget paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

Den här tjänsten anger pekaren för receive notify-funktionen till återanropsfunktionen som anges av programmet. Den här återanropsfunktionen anropas sedan när ett paket tas emot på socketen. Om en NX_NULL-pekare anges inaktiveras receive notify-funktionen.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till UDP-socketen.
- **udp_receive_notify** Funktions pekare för återanrop av program som anropas när ett paket tas emot på socketen.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
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

### <a name="description"></a>Description

Den här tjänsten skickar ett UDP-datagram via en tidigare skapad och bunden UDP-socket. NetX hittar en lämplig lokal IP-adress som källadress baserat på målets IP-adress. Om du vill ange ett specifikt gränssnitt och  en käll-IP-adress ska programmet använda nx_udp_socket_interface_send tjänsten.

Observera att den här tjänsten returnerar omedelbart oavsett om UDP-datagrammet har skickats.

Socketen måste vara bunden till en lokal port.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en UDP-socketinstans som skapats tidigare
- **packet_ptr** Pekare för UDP-datagrampaket
- **ip_address** Mål-IP-adress
- **port** Giltigt målportnummer mellan 1 och 0xFFFF) i värdbyteordning

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad UDP-socketssändning
- **NX_NOT_BOUND** (0x24) Socket som inte är bunden till någon port
- **NX_NO_INTERFACE_ADDRESS** (0x50) Det går inte att hitta något lämpligt utgående gränssnitt.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig server-IP-adress
- **NX_UNDERFLOW** (0x02) Det finns inte tillräckligt med utrymme för UDP-huvudet i paketet
- **NX_OVERFLOW** (0x03) Pekaren för tilläggspaket är ogiltig
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten
- **NX_NOT_ENABLED** (0x14) UDP har inte aktiverats
- **NX_INVALID_PORT** (0x46) Portnumret ligger inte inom ett giltigt intervall

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

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

### <a name="description"></a>Description

Den här tjänsten skickar ett UDP-datagram via en tidigare skapad och bunden UDP-socket via nätverksgränssnittet med den angivna IP-adressen som källadress. Observera att tjänsten returnerar omedelbart, oavsett om UDP-datagrammet har skickats eller inte.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Socket för att överföra paketet ut på.
- **packet_ptr** Pekare till paket som ska överföras.
- **ip_address** Mål-IP-adress för att skicka paket.
- **port** Målport.
- **address_index** Index för den adress som är associerad med gränssnittet för att skicka paket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** paket (0x00) har skickats.
- **NX_NOT_BOUND** (0x24) Socket som inte är bunden till en port.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-adress.
- **NX_NOT_ENABLED** (0x14) UDP-bearbetning har inte aktiverats.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare.
- **NX_OVERFLOW** (0x03) Pekare för ogiltigt paketfördr dess tillägg.
- **NX_UNDERFLOW** (0x02) Ogiltig pekare för paketförberedelser.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_INVALID_INTERFACE** (0x4C) Ogiltigt adressindex.
- **NX_INVALID_PORT** (0x46) Portnumret överskrider det maximala portnumret.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_unbind

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

Ta bort bindning för UDP-socket från UDP-porten.

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

Den här tjänsten släpper bindningen mellan UDP-socketen och en UDP-port. Mottagna paket som lagras i mottagningskön släpps som en del av unbind-åtgärden.

Om det finns andra trådar som väntar på att binda en annan socket till den obundna porten, binds den första pausade tråden till den nyligen obundna porten.

### <a name="parameters"></a>Parametrar

- **socket_ptr** Pekare till en UDP-socketinstans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad socket-unbind.
- **NX_NOT_BOUND** (0x24) Socket var inte bunden till någon port.
- **NX_PTR_ERROR** (0x07) Ogiltig socket-pekare.
- **NX_CALLER_ERROR** (0x11) Ogiltig anropare för den här tjänsten.
- **NX_NOT_ENABLED** (0x14) Den här komponenten har inte aktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a>Se även

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract

Extrahera IP och skicka port från UDP-datagram

### <a name="prototype"></a>Prototyp

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a>Description

Den här tjänsten extraherar avsändarens IP-adress och portnummer från IP- och UDP-huvudena för det angivna UDP-datagrammet.

### <a name="parameters"></a>Parametrar

- **packet_ptr** UDP-datagrampaket pekare.
- **ip_address** Giltig pekare till den returnerade IP-adressvariabeln.
- **port** Giltig pekare till returportvariabeln.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad extrahering av käll-IP/port.
- **NX_INVALID_PACKET** (0x12) Det angivna paketet är ogiltigt.
- **NX_PTR_ERROR** (0x07) Ogiltigt paket eller IP- eller portmål.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers, ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

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
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind