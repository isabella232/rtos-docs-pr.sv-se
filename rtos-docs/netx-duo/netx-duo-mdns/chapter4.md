---
title: Kapitel 4 – Beskrivning av mDNS-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX mDNS-tjänster
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89df0ab5f09be8ad50a27d23bae8b20d71caa0b4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825917"
---
# <a name="chapter-4---description-of-mdns-services"></a>Kapitel 4 – Beskrivning av mDNS-tjänster

Det här kapitlet innehåller en beskrivning av alla NetX mDNS-tjänster (visas nedan).

> [!NOTE]
> I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

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

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en mDNS-instans på den angivna IP-instansen och associerade resurser. En tråd skapas också för att hantera inkommande mDNS-meddelanden, för att svara på frågor och för att regelbundet överföra frågemeddelanden.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **ip_ptr** Pekare till den associerade IP-instansen.
- **packet_pool** Pekar mot en giltig adresspool.
- **prioritet** Prioritet för mDNS-tråden.
- **stack_ptr** Pekare till stackområdet för mDNS-tråden
- **stack_size** Storlek på stackområdet.
- **host_name** Värd namnet tilldelat till den här noden.
- **local_service_cache** Lagrings utrymme för lokala registrerade tjänster.
- **local_service_cache_size** Storlek på den lokala tjänstens cacheminne.
- **peer_service_cache** Lagrings utrymme för mottagen tjänst information
- **peer_service_cache_size** Storlek på peer-tjänstecache
- **probing_notify** Valfri callback-funktion anropades i slutet av avsöknings åtgärden. Det meddelar programmet oavsett om värd namnet (när du aktiverar mDNS på ett lokalt gränssnitt), eller om tjänst namnet (efter registreringen av en tjänst) är unikt.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) skapade mdns-instansen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort mDNS-instansen och frigör dess resurser.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till kontroll blocket mDNS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har tagit bort mdns-instansen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Detta API aktiverar mDNS-tjänsten på ett angivet fysiskt gränssnitt. När tjänsten är aktive rad avsöker mDNS-modulen först alla sina unika tjänst namn i nätverket innan de svarar på frågor som tagits emot i gränssnittet.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekar mot kontroll blocket för mDNS-instansen.
- **interface_index** Indexera det gränssnitt där tjänsten ska aktive ras

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) aktiverade tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a>nx_mdns_disable

Inaktivera tjänsten mDNS

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Beskrivning

Detta API inaktiverar mDNS-tjänsten för det angivna fysiska gränssnittet. När tjänsten är inaktive rad skickar mDNS meddelandet "Hej" för varje lokal tjänst till nätverket som är kopplat till gränssnittet, så att intilliggande noder meddelas.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **interface_index** Indexera till gränssnittet där tjänsten ska inaktive ras

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har inaktiverat tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a>nx_mdns_cache_notify_set

Installerar funktionen mDNS cache full notify

### <a name="prototype"></a>Prototyp

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a>Beskrivning

Den här tjänsten installerar en motringnings funktion som anges av användaren, som anropas när antingen den lokala tjänstecachen eller peer-tjänstecachen blir full. När tjänstecachen är full kan ingen mer mDNS-resurspost läggas till. Observera att tjänstecachen kan bli full till följd av intern fragmentering när tjänster med olika sträng längd läggs till och tas bort. Vid mottagning av en cache fullständig avisering i peer service cache kan programmet använda tjänsten "*nx_mdns_service_cache_clear"* för att radera alla poster i peer-tjänstecachen.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till kontroll blocket mDNS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har installerat funktionen mdns cache notify motringning.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a>nx_mdns_cache_notify_clear

Rensa funktionen mDNS service cache full notify

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten rensar en funktion för att skicka ett tjänst-cache som tillhandahålls av användaren.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till kontroll blocket mDNS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) rensade funktionen mdns service cache notify motringning.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a>nx_mdns_domain_name_set

Anger domän namnet

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten konfigurerar det lokala standard domän namnet. När mDNS-instansen skapas anges standard namnet för den lokala domänen till ". local". Detta API gör att ett program kan skriva över det lokala standard domän namnet.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **domain_name** Det domän namn som ska användas.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har konfigurerat en lokal domän.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a>nx_mdns_service_announcement_timing_set

Anger tids parametrar för service meddelande meddelanden

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a>Beskrivning

Den här tjänsten konfigurerar om de tids parametrar som används av mDNS när de skickar tjänst meddelanden. Publicerings perioden börjar från *t* -Tick och kan utökas telescopically med 2 till kraften i *k* faktor. Antalet upprepningar per annons är *p*, intervallet mellan varje upprepad annons är *intervall* Tick och antalet meddelande perioder är max_time. Som standard anges den inledande perioden till 1 sekund, med k = 1 (perioden dubbleras varje gång), *p = 1* (ingen upprepning), retrans_interval = 0 (inget tidsintervall), Period_interval = 0xFFFFFFFF (max period intervall) och max_time = 3 (antal annonser).

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **t** antal Tick för den inledande perioden. Standardvärdet är 100 för 1 sekund.
- **p** antal upprepningar. Standardvärdet är 1.
- **k** Telescopic faktor. Standardvärdet är 1.
- **retrans_interval** Antal Tick som ska förflyta innan meddelanden skickas ut från upprepade meddelanden. Standardvärdet är 0.
- **period_interval** Antalet Tick mellan två meddelande perioder. Standardvärdet är 0xFFFFFFFF.
- **max_time** Antal meddelande perioder som ska användas för annonsen. Efter *max_time* meddelande perioder skickas inga fler meddelande meddelanden. Standardvärdet är 3.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett tids värden.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a>nx_mdns_service_add

Lägg till en lokal tjänst

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a>Beskrivning

Detta API registrerar en tjänst som erbjuds av programmet. Om flaggan *is_unique* har angetts avsöker mdns tjänst namnet för att kontrol lera att det är unikt i det lokala nätverket innan du börjar meddela tjänsten i nätverket. *Instans* är instans delen av tjänst namnet. *Tjänsten* är tjänst delen av tjänst namnet. Till exempel "_http. _ TCP" är en tjänst. För att beskriva en tjänst med undertyp måste anroparen använda under *typ* parametern. Om den önskade tjänsten t. ex. är "_printer. _sub. _http. _ TCP", är tjänst fältet "_http. _ TCP:, och under Typ fältet är" _printer ".

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **instans** Pekar mot instans namnet för tjänsten.
- **tjänsten** Pekare till tjänst typen mDNS, exklusive information om undertyp.
- **undertyp** Pekar på under typs delen av mDNS-tjänsten, om tillämpligt.
- **prioritet** Tjänst prioritet
- **vikt** Tjänst vikt
- **port** TCP-eller UDP-portnummer som tjänsten använder
- **text** Ytterligare text information
- **is_unique** Boolesk flagga som anger om tjänsten är delad eller unik. För tjänster som är registrerade som unika måste mDNS avsöka tjänsten i nätverket innan de påbörjar erbjudandet.
- **Interface_index** Det fysiska gränssnitt som tjänsten erbjuds via. För en tjänst som erbjuds via någon av de anslutna tjänsterna används värdet *NX_MDNS_ALL_INTERFACES* .

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har registrerat tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Detta API tar bort en tidigare registrerad tjänst. När tjänsten tas bort skickas "" rader "meddelanden till det lokala nätverket så att intilliggande noder meddelas.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **instans** Pekar mot instans namnet för tjänsten.
- **tjänsten** Pekare till tjänst typen mDNS, exklusive information om undertyp.
- **undertyp** Pekar på under typs delen av mDNS-tjänsten, om tillämpligt.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har tagit bort tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a>nx_mdns_service_one_shot_query

Starta tjänst identifiering för en bild

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en mDNS-fråga med en bild. Om den angivna tjänsten finns i peer-tjänstecachen returneras den första instansen. Om inga tjänster hittas i den lokala peer-tjänstecachen, utfärdar mDNS-modulen ett Query-kommando och väntar på svar. Tjänsten är blockerad till antingen det första svaret eller tids gränsen för frågan.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **instans** Pekar mot instans namnet för tjänsten, om det är tillämpligt.
- **tjänsten** Pekare till tjänst typen mDNS, exklusive information om undertyp. programmet måste ange tjänst typen.
- **undertyp** Pekar på under typs delen av mDNS-tjänsten, om tillämpligt.
- **service_ptr** Användaren tillhandahöll NX_MDNS_SERVICE struktur som lagrar frågeresultaten.
- **wait_option** Tiden, i Tick, för att vänta på ett svar.

### <a name="return-values"></a>Retur värden

- Information om tjänsten **NX_SUCCESS** (0X00) har hämtats.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Initiera kontinuerlig identifiering av tjänst

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en kontinuerlig fråga. Observera att tjänsten returnerar omedelbart. När du har utfärdat en kontinuerlig fråga kan programmet Hämta tjänst poster med hjälp av API- *nx_mdns_service_lookup*. För att stoppa den kontinuerliga frågan kan programmet använda API- *nx_mdns_service_query_stop*

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **instans** Pekar mot instans namnet för tjänsten, om det är tillämpligt.
- **tjänsten** Pekare till tjänst typen mDNS, exklusive information om undertyp, om tillämpligt.
- **undertyp** Pekar på under typs delen av mDNS-tjänsten, om tillämpligt.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har börjat fortsätta fråga.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Upphöra med en tidigare utfärdad kontinuerlig tjänst identifiering

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Beskrivning

Detta API avslutar en tidigare utfärdad kontinuerlig tjänst identifiering.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **instans** Pekar mot instans namnet för tjänsten.
- **tjänsten** Pekare till mDNS Service Type, undertyp information.
- **undertyp** Pekar på under typs delen av mDNS-tjänsten, om tillämpligt.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har stoppats Fortsätt frågan.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a>nx_mdns_service_lookup

Hämtar tjänsten från den lokala peer-tjänstecachen

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten söker efter tjänster som matchar instans namnet (om det finns) och typen av tjänst i den lokala peer-tjänstecachen. Programmet ska starta tjänstens sökning med *instance_index* har värdet noll för den första tjänsten i cachen som matchar beskrivningen. Programmet måste fortsätta använda den här tjänsten med ökande *instance_index* värde för ytterligare tjänster som finns i cacheminnet, till tjänsten returnerar *NX_NO_MORE_ENTRIES*, vilket indikerar cacheminnets slut.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **instans** Pekar mot instans namnet för tjänsten, om det är tillämpligt.
- **tjänsten** Pekare till tjänst typen mDNS, exklusive information om undertyp, om tillämpligt.
- **undertyp** Pekar på under typs delen av mDNS-tjänsten, om tillämpligt.
- **Instance_index** Index numret till den instans som ska returneras.
- **service_ptr** Användaren tillhandahöll en NX_MDNS_SERVICE struktur som lagrar Sök resultaten.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har hämtat tjänsten
- **NX_NO_MORE_ENTRIES** (0x17) Det gick inte att hitta någon tjänst post på det angivna index numret. Den här fel koden anger slutet på sökningen.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a>nx_mdns_service_ignore_set

Konfigurerar en tjänst som ignorerar

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a>Beskrivning

Detta API konfigurerar en mask för att ignorera tjänster som anges av *service_mask* bitmask. Användaren kan eventuellt använda service_mask för att välja tjänst typer som inte vill cachelagras. En lista över tjänster definieras i tabellen *nx_mdns_service_types* i *nxd_mdns. c.* Motsvarande mask för den första tjänst typen i nx_mdns_service_types [] är 0x00000001, masken för den andra tjänst typen är 0x00000002 och så vidare.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **service_mask** Användardefinierade tjänst typer att ignorera. Masken är en 32-bitars ULONG-typ. Varje bit representerar en post i den användardefinierade *nx_mdns_service_types* matrisen. Om en bit anges kommer motsvarande tjänst typ som anges i *nx_mdns_service_type* matrisen inte att lagras i peer-tjänstecacheminnet.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett en mask för att ignorera tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a>nx_mdns_service_notify_set

Konfigurerar en tjänst ändring Avisera motringning funktion

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a>Beskrivning

Detta API konfigurerar en tjänst ändrings avisering om motringning. Den här callback-funktionen anropas när en tjänst som erbjuds av andra noder i nätverket läggs till, ändras eller inte längre är tillgänglig. Användaren kan eventuellt använda service_mask för att välja tjänst typer som det vill övervaka. En lista över tjänster som övervakas är hårdkodade i tabellen *nx_mdns_service_types* i *nxd_mdns. c.*

Motsvarande mask för den första tjänst typen i nx_mdns_service_types [] är 0x00000001, masken för den andra tjänst typen är 0x00000002 och så vidare.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **service_mask** Användardefinierade tjänst typer som ska övervakas. Masken är en 32-bitars ULONG-typ. Varje bit representerar en post i *nx_mdns_service_types* matrisen.
- **service_change_notify** Motringningsfunktionen som anropas när den angivna tjänsten ändras. Detaljerad tjänst information returneras i minnet som pekas på *service_ptr.* Observera att innehållet i minnet är ogiltigt när du har returnerat från funktionen meddela motringning.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har installerat motringningsfunktionen.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a>nx_mdns_service_notify_clear

Rensa aviserings funktionen för tjänst ändringar

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Beskrivning

Detta API rensar tjänst ändringen meddela motringning och.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS kontroll block..

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) rensade återanrops funktionen.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a>nx_mdns_host_address_get

Hämta värd adressen

### <a name="prototype"></a>Prototyp

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten utför en mDNS-fråga på värd-IPv4-och IPv6-adresser. Om adressen för det angivna värd namnet finns i peer-tjänstecachen returneras adressen. Om ingen adress hittas i peer-tjänstecachen, utfärdar mDNS-modulen en och AAAA-typfrågor och väntar på svar. Detta API-block tills antingen ett svar tas emot eller tids gränsen för frågan har uppnåtts.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.
- **host_name** Pekare till värd namnet.
- **ipv4_address** Pekar på en 4-bytes justerad adress för IPv4-adress lagrings utrymme. Användaren ska allokera 4 byte av utrymme för IPv4-adressen. NX_NULL adress kan skickas till det här API: et om programmet inte behöver hämta IPv4-adressen.
- **ipv6_address** Pekar på 4-bytes justerad adress för IPv6-adress lagrings utrymme. Användaren tilldelas 16 bytes utrymme för-IPv6-adressen. NX_NULL adress kan skickas till det här API: et om programmet inte behöver hämta IPv6-adressen.
- **wait_option** Tiden, i Tick, för att vänta på ett svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) hämtade värd adressen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten rensar alla poster i den lokala tjänstecachen när meddelandet har skickats.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) raderade alla poster i cacheminnet.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten rensar alla poster i peer-tjänstecachen.

### <a name="input-parameters"></a>Indataparametrar

- **mdns_ptr** Pekare till mDNS Control Block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) raderade alla poster i cacheminnet.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
