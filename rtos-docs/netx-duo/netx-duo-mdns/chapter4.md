---
title: Kapitel 4 – Beskrivning av mDNS-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX mDNS-tjänster
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6e37698ac6023b4cff6cb4fc05330a73b678ef3d2a813a706c9b821381e123db
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797576"
---
# <a name="chapter-4---description-of-mdns-services"></a>Kapitel 4 – Beskrivning av mDNS-tjänster

Det här kapitlet innehåller en beskrivning av alla NetX mDNS-tjänster (se nedan).

> [!NOTE]
> I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade.

## <a name="nx_mdns_create"></a>nx_mdns_create

Skapa en mDNS-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a>Description

Den här tjänsten skapar en mDNS-instans på den specifika IP-instansen och tillhörande resurser. En tråd skapas också för att hantera inkommande mDNS-meddelanden, svara på frågor och regelbundet överföra frågemeddelanden.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **ip_ptr** Pekare till den associerade IP-instansen.
- **packet_pool** Pekare till en giltig paketpool.
- **prioritet** Prioritet för mDNS-tråden.
- **stack_ptr** Pekare till stackområdet för mDNS-tråden
- **stack_size** Stackområdets storlek.
- **host_name** Värdnamn som tilldelats den här noden.
- **local_service_cache** Storage utrymme för lokala registrerade tjänster.
- **local_service_cache_size** Storleken på den lokala tjänstcachen.
- **peer_service_cache** Storage för mottagna tjänstinformation
- **peer_service_cache_size** Storleken på peer-tjänstcachen
- **probing_notify** Valfri återanropsfunktion anropas i slutet av avsökningsåtgärden. Den meddelar programmet om värdnamnet (när du aktiverar mDNS i ett lokalt gränssnitt) eller om tjänstnamnet (efter registreringen av en tjänst) är unikt.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) MDNS-instansen har skapats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a>nx_mdns_delete

Ta bort en mDNS-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort mDNS-instansen och frigör dess resurser.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) MDNS-instansen har tagits bort.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a>nx_mdns_enable

Starta mDNS-tjänsten

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Description

Det här API:et aktiverar mDNS-tjänsten i ett specifikt fysiskt gränssnitt. När tjänsten har aktiverats avser mDNS-modulen först alla sina unika tjänstnamn i nätverket innan den svarar på frågor som tas emot i gränssnittet.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-instansens kontrollblock.
- **interface_index** Indexera till gränssnittet där tjänsten ska aktiveras

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har aktiverat tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a>nx_mdns_disable

Inaktivera mDNS-tjänsten

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Description

Det här API:et inaktiverar mDNS-tjänsten i det specifika fysiska gränssnittet. När tjänsten har inaktiverats skickar mDNS "goodbye"-meddelanden för varje lokal tjänst till nätverket som är kopplat till gränssnittet, så att närliggande noder meddelas.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **interface_index** Indexera till gränssnittet där tjänsten ska inaktiveras

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har inaktiverat tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a>nx_mdns_cache_notify_set

Installerar mDNS cache full notify-funktion

### <a name="prototype"></a>Prototyp

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a>Description

Den här tjänsten installerar en återanropsfunktion som tillhandahålls av användaren, som anropas när antingen den lokala tjänstcachen eller peer-tjänstcachen blir full. När tjänstcachen är full går det inte att lägga till fler mDNS-resursposter. Observera att tjänstcachen kan bli full på grund av intern fragmentering när tjänster med olika stränglängder läggs till och tas bort. När ett fullständigt cachemeddelande tas emot i peer-tjänstcachen kan programmet använda tjänsten *"nx_mdns_service_cache_clear"* för att radera alla poster i peer-tjänstens cacheminne.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) MDNS Cache notify callback-funktionen har installerats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a>nx_mdns_cache_notify_clear

Rensa mDNS-tjänstens fullständiga av meddela-funktion

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Description

Den här tjänsten rensar en tjänstcache som användaren har angett för att meddela återanropsfunktionen.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har rensat funktionen mDNS-tjänstens cache för att meddela återanrop.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a>nx_mdns_domain_name_set

Anger domännamnet

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a>Description

Den här tjänsten ställer in det lokala standarddomännamnet. När mDNS-instansen skapas anges det lokala standarddomännamnet till ".local". Med det här API:et kan ett program skriva över det lokala standarddomännamnet.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **domain_name** Det domännamn som ska användas.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har konfigurerats på den lokala domänen.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a>nx_mdns_service_announcement_timing_set

Anger tidsparametrar för meddelanden om tjänstmeddelanden

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a>Description

Den här tjänsten konfigurerar om de tidsparametrar som används av mDNS när tjänstmeddelanden skickas. Publiceringsperioden börjar *från tick* och kan utökas telegrafiskt med 2 till kraften hos *k-faktorn.* Antalet upprepningar per annons är *p*, intervallet  mellan varje upprepad annons är intervall tick och antalet meddelanden är max_time. Som standard är den inledande perioden inställd på 1 sekund, med k = 1 (perioden fördubblas varje gång), *p = 1* (ingen upprepning), retrans_interval = 0(inget tidsintervall), period_interval = 0xFFFFFFFF(maxintervall) och max_time = 3(antal annonser).

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **t** Antal tick för den första perioden. Standardvärdet är 100 tick i 1 sekund.
- **p** Antal upprepningar. Standardvärdet är 1.
- **k** Telemetrifaktor. Standardvärdet är 1.
- **retrans_interval** Antal tick som ska vänta innan upprepade meddelanden skickas. Standardvärdet är 0.
- **period_interval** Antal tick mellan två meddelandeperioder. Standardvärdet är 0xFFFFFFFF.
- **max_time** Antal meddelanden som ska användas för annonsen. Efter *max_time* skickas inga fler meddelanden. Standardvärdet är 3.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Anger tidsvärden.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a>nx_mdns_service_add

Lägga till en lokal tjänst

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a>Description

Detta API registrerar en tjänst som erbjuds av programmet. Om flaggan *is_unique* har angetts avser mDNS tjänstnamnet för att se till att det är unikt i det lokala nätverket innan det börjar meddela tjänsten i nätverket. *Instansen* är instansdelen av tjänstnamnet. Tjänsten *är* tjänstdelen av namnet på tjänsten. Till exempel är "_http._tcp" en tjänst. För att beskriva en tjänst med undertyp måste anroparen använda *undertypsparametern.* Om den önskade tjänsten till exempel är "_printer._sub._http._tcp" är tjänstfältet "_http._tcp:, och fältet för undertyp är "_printer".

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **instans** Pekare till instansnamnet för tjänsten.
- **tjänst** Pekare till mDNS-tjänsttypen, exklusive information om undertyp.
- **undergrupp** Pekare till undertypsdelen av mDNS-tjänsten, om tillämpligt.
- **prioritet** Tjänstprioritet
- **vikt** Tjänstvikt
- **port** TCP- eller UDP-portnummer som tjänsten använder
- **text** Ytterligare textinformation
- **is_unique** Boolesk flagga som anger om tjänsten är delad eller unik. För tjänster som registrerats som unika måste mDNS avsläsa tjänsten i nätverket innan det börjar erbjudas.
- **Interface_index** Det fysiska gränssnitt som tjänsten erbjuds via. För en tjänst som erbjuds via någon av de anslutna tjänsterna används *NX_MDNS_ALL_INTERFACES* värdet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har registrerat tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a>nx_mdns_service_delete

Ta bort en tidigare registrerad tjänst

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a>Description

Detta API tar bort en tidigare registrerad tjänst. När tjänsten tas bort skickas "goodbye"-meddelanden till det lokala nätverket så att närliggande noder meddelas.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **instans** Pekare till instansnamnet för tjänsten.
- **tjänst** Pekare till mDNS-tjänsttypen, exklusive information om undertyp.
- **undergrupp** Pekare till undertypsdelen av mDNS-tjänsten, om tillämpligt.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Tjänsten har tagits bort.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a>nx_mdns_service_one_shot_query

Initiera identifiering av en shot-tjänst

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten utför en enda mDNS-fråga. Om den angivna tjänsten finns i peer-tjänstens cacheminne returneras den första instansen. Om inga tjänster hittas i den lokala peer-tjänstcachen utfärdar mDNS-modulen ett frågekommando och väntar på svar. Tjänsten blockeras tills antingen det första svaret tas emot eller så går frågan ut.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **instans** Pekare till instansnamnet för tjänsten, om tillämpligt.
- **tjänst** Pekare till mDNS-tjänsttypen, exklusive information om undertyp. programmet måste ange tjänsttypen.
- **undergrupp** Pekare till undertypsdelen av mDNS-tjänsten, om tillämpligt.
- **service_ptr** Användaren angav en pekare NX_MDNS_SERVICE en struktur som lagrar frågeresultatet.
- **wait_option** Hur lång tid det tar att vänta på ett svar i tick.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Tjänstinformation har erhållits.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a>nx_mdns_service_continuous_query

Initiera kontinuerlig tjänstidentifiering

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Description

Den här tjänsten startar en kontinuerlig fråga. Observera att tjänsten returneras omedelbart. När en kontinuerlig fråga har utfärdats kan programmet hämta tjänstposten med hjälp av *API:et nx_mdns_service_lookup*. För att stoppa den kontinuerliga frågan kan programmet använda *API-nx_mdns_service_query_stop*

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **instans** Pekare till instansnamnet för tjänsten, om tillämpligt.
- **tjänst** Pekare till mDNS-tjänsttypen, exklusive information om undertyp, om tillämpligt.
- **undergrupp** Pekare till undertypsdelen av mDNS-tjänsten, om tillämpligt.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Frågan har startats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a>nx_mdns_service_query_stop

Upphöra med en tidigare utfärdad kontinuerlig tjänstidentifiering

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Description

Det här API:et avslutar en tidigare utfärdad kontinuerlig tjänstidentifiering.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **instans** Pekare till instansnamnet för tjänsten.
- **tjänst** Pekare till mDNS-tjänsttypen, undertypsinformation.
- **undergrupp** Pekare till undertypsdelen av mDNS-tjänsten, om tillämpligt.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Frågan har stoppats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a>nx_mdns_service_lookup

Hämtar tjänsten från den lokala peer-tjänstcachen

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a>Description

Den här tjänsten söker efter tjänster som matchar instansnamnet (om det finns) och typen av tjänst i den lokala peer-tjänstcachen. Programmet ska starta tjänstsökningen med *en* instance_index inställd på noll för den första tjänsten i cacheminnet som matchar beskrivningen. Programmet ska fortsätta att använda den här *tjänsten med instance_index* öka värdet för ytterligare tjänster som finns i cacheminnet tills tjänsten returnerar *NX_NO_MORE_ENTRIES*, vilket anger slutet av cacheminnet.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **instans** Pekare till instansnamnet för tjänsten, om tillämpligt.
- **tjänst** Pekare till mDNS-tjänsttypen, exklusive information om undertyp, om tillämpligt.
- **undergrupp** Pekare till undertypsdelen av mDNS-tjänsten, om tillämpligt.
- **Instance_index** Indexnummer till den instans som ska returneras.
- **service_ptr** Användaren angav en pekare NX_MDNS_SERVICE en struktur som lagrar uppslagsresultatet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har hämtat tjänsten
- **NX_NO_MORE_ENTRIES** (0x17) Ingen tjänstpost hittas på det angivna indexnumret. Den här felkoden anger slutet av sökningen.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a>nx_mdns_service_ignore_set

Konfigurerar en ignorerad tjänstuppsättning

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a>Description

Detta API konfigurerar en mask för att ignorera tjänster som anges av *service_mask* bitmask. Användaren kan också använda service_mask för att välja tjänsttyper som inte ska cachelagras. En lista över tjänster definieras i tabellen *nx_mdns_service_types* i *nxd_mdns.c.* Motsvarande mask för den första tjänsttypen i nx_mdns_service_types[] är 0x00000001, masken för den andra tjänsttypen är 0x00000002 och så vidare.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **service_mask** Användardefinierade tjänsttyper som ska ignoreras. Masken är en 32-bitars ULONG-typ. Varje bit representerar en post i den användardefinierade *nx_mdns_service_types* matrisen. Om en bit har angetts lagras inte motsvarande tjänsttyp *som anges nx_mdns_service_type* matrisen i peer-tjänstens cacheminne.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Anger tjänstens ignorerade mask.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a>nx_mdns_service_notify_set

Konfigurerar en återanropsfunktion för att meddela om tjänständring

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a>Description

Det här API:et konfigurerar en tjänständringsfunktion för att meddela om återanrop. Den här återanropsfunktionen anropas när en tjänst som erbjuds av andra noder i nätverket läggs till, ändras eller inte längre är tillgänglig. Användaren kan också använda service_mask för att välja vilka tjänsttyper som ska övervakas. En lista över tjänster som övervakas är hårdkodade i tabellen *nx_mdns_service_types* i *nxd_mdns.c.*

Motsvarande mask för den första tjänsttypen i nx_mdns_service_types[] är 0x00000001, masken för den andra tjänsttypen är 0x00000002 och så vidare.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **service_mask** Användardefinierade tjänsttyper som ska övervakas. Masken är en 32-bitars ULONG-typ. Varje bit representerar en post i *nx_mdns_service_types* matrisen.
- **service_change_notify** Återanropsfunktionen som ska anropas när den angivna tjänsten ändras. Den detaljerade tjänstinformationen returneras i minnet som *service_ptr.* Observera att innehållet i minnet är ogiltigt efter att ha returnerats från återanropsfunktionen notify.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Återanropsfunktionen har installerats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a>nx_mdns_service_notify_clear

Rensa funktionen för att meddela återanrop om tjänständring

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Description

Det här API:et rensar funktionen för att meddela återanrop om tjänständring och .

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket..

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har rensat återanropsfunktionen.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a>nx_mdns_host_address_get

Hämta värdadressen

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten utför en mDNS-fråga på värd-IPv4- och IPv6-adresser. Om adressen för det angivna värdnamnet hittas i peer-tjänstcachen returneras adressen. Om ingen adress hittas i peer-tjänstens cacheminne utfärdar mDNS-modulen frågor av typen A och AAAA och väntar på svar. Det här API:et blockerar tills antingen ett svar tas emot eller tills frågan får sin tid.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.
- **host_name** Pekare till värdnamn.
- **ipv4_address** Pekare till en 4 byte-justerad adress för IPv4-adresslagringsutrymme. Användaren ska allokera 4 byte utrymme för IPv4 -adressen. NX_NULL-adressen kan skickas till det här API:et om programmet inte behöver hämta IPv4-adressen.
- **ipv6_address** Pekare till den 4 byte-justerade adressen för IPv6-adresslagringsutrymmet. Användaren ska allokera 16 byte utrymme för - IPv6-adressen. NX_NULL-adressen kan skickas till det här API:et om programmet inte behöver hämta IPv6-adressen.
- **wait_option** Hur lång tid det tar att vänta på ett svar i tick.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Värdadressen har erhållits.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a>nx_mdns_local_cache_clear

Radera alla lokala tjänster

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Description

Den här tjänsten rensar alla poster i den lokala tjänstcachen efter att ha skickat meddelandet Goodbye.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har raderat alla poster i cacheminnet.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a>nx_mdns_peer_cache_clear

Radera alla identifierade tjänster

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Description

Den här tjänsten rensar alla poster i peer-tjänstens cacheminne.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS-kontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har raderat alla poster i cacheminnet.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
