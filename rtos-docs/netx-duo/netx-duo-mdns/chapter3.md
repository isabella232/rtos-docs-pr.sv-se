---
title: Kapitel 3 – Beskrivning av intern tjänstcache
description: 'NetX Duo mDNS-modulen hanterar två interna tjänstcacheminnen: den lokala tjänstcachen och peer-tjänstens cache.'
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: edf52cb2d7df293a4606d6c5b5b63075969933fb1a093a1d83b91b2709c08f0c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791728"
---
# <a name="chapter-3---description-of-internal-service-cache"></a>Kapitel 3 – Beskrivning av intern tjänstcache

NetX Duo mDNS-modulen hanterar två interna tjänstcacheminnen: den lokala tjänstcachen och peer-tjänstens cache. Den lokala tjänstens cachelagring lagrar resursposter relaterade till tjänster som erbjuds av program som körs på noden. För inkommande frågor gäller att om frågan matchar tjänsten som erbjuds, mDNS-svar med svar som lagras i den lokala tjänstens cacheminne. Program registrerar tjänster genom att anropa *API:et nx_mdns_service_add()*. För att ta bort tjänster använder program *API:et nx_mdns_service_delete()*, som i sin tur skickar "goodbye"-meddelanden innan motsvarande poster tas bort i den lokala tjänstens cacheminne.

När en tjänst läggs till har mDNS minst 3 resursposter i den lokala tjänstcachen: SRV, PTR och TXT. Ytterligare PTR-resurspost kan läggas till om tjänsttypen innehåller undertyp. Ett program registrerar till exempel en tjänst:

```
*name*._*subtype*._sub._*type*._tcp.local,
```

två PTR-resursposter läggs till i den lokala tjänstcachen, en för

```
“*_subtype._*sub*._type._*tcp.local *PTR name.type._*tcp*.*local”
```

och den andra för

```
*“_type._*tcp*.*local *PTR name.type._*tcp*.*local”.
```

Peer Service-cachen innehåller mDNS-resursposter som tas emot från närliggande noder. mDNS-modulen samlar in resursposter som annonseras av andra noder i nätverket och lagrar den mottagna informationen i peer-tjänstens cacheminne. När program frågar efter information, till exempel värd-IPv4- eller IPv6-adresser, söker mDNS i peer service-cachen efter lokalt cachelagrade svar. När programfrågor för tjänster som erbjuds av peer-användare söker mDNS igenom cacheminnet efter relaterade PTR-, SRV-, TXT- och IPv4/IPv6-adressposter. Peer Service-cachen lagrar också frågor som skickas till noden. Ett program kan till exempel begära en viss tjänst genom att anropa *nx_mdns_service_one_shot_query.* Om tjänsten inte hittas i peer-tjänstens cacheminne skapar mDNS frågefrågor (PTR, SRV och TXT) i peer-tjänstens cacheminne. De här frågefrågorna skickas regelbundet till nätverket tills tjänsten har lösts eller tills dess att den har förfjärstid. På liknande sätt kan programmet använda *API:et nx_mdns_service_continous_query()* för att begära en viss tjänst under en längre tid (programmet avbryter en tidigare utfärdad kontinuerlig fråga med hjälp av *API:et nx_mdns_service_query_stop()* ). Om du vill söka efter en viss tjänst i peer-tjänstens cache utan att skicka frågor till nätverket kan program använda *API:et nx_mdns_serivce_lookup().* Det här API:et söker bara igenom resursposterna i peer-tjänstens cacheminne.

Varje resurspost lagras i en datastruktur *NX_MDNS_RR* i tjänstens cacheminnen. Strängar i resursposter är varierande längd och lagras därför inte i *NX_MDNS_RR* struktur. Resursposten innehåller en pekare till den faktiska minnesplatsen där strängen lagras. Strängtabellen och resursposterna delar tjänstcachen. Resursposter lagras från början av tjänstcachen och växer mot slutet av cachen. Strängtabellen startar från slutet av tjänstcachen och växer mot början av cachen. Varje sträng i strängtabellen har ett längdfält och ett räknarfält. Om samma sträng redan finns i tabellen när en sträng läggs till i strängtabellen ökas räknarvärdet och inget minne allokeras för strängen. Tjänstcachen anses vara full om inga fler resursposter eller nya strängar kan läggas till i tjänstens cacheminne.

Det finns två sätt för ett program att hitta tjänster som erbjuds i det lokala nätverket. Den kan antingen utfärda en specifik tjänst genom att söka igenom en enda fråga eller initiera en kontinuerlig fråga för att "övervaka" aktiviteterna i nätverket. I det ena korta frågescenariot måste programmet ange tjänsttypen. mDNS söker igenom den lokala tjänstens cacheminne och peer-tjänstens cache. Om en tjänstinstans finns returnerar en shot-frågan med informationen som finns i resursposterna. Om det inte finns några poster i den lokala tjänstens cacheminne eller peer-tjänstcache skickar mDNS ut frågemeddelanden. Om instansnamnet anges skickas en *ANY-typ* (fråga SRV- och TXT-typen) med det specifika instansnamnet i form av "name.type.local" till det lokala nätverket. Om instansnamnet inte anges skickas en PTR-typ av fråga till det lokala nätverket. Den första fullständiga tjänsten som tas emot returneras till anroparen.

Kontinuerlig fråga fungerar på olika sätt. Det vanligaste användningsfallet för en kontinuerlig fråga är att övervaka det lokala nätverket för en specifik tjänst (till exempel för att ständigt söka efter utskriftstjänster i det lokala nätverket). I det här fallet utfärdar programmet en sökfråga (via *API nx_mdns_service_continious_fråga)* för en viss typ av tjänster. Anroparen väntar vanligtvis inte på ett visst svar. För frågor som skickas som kontinuerlig fråga överför mDNS-modulen frågorna regelbundet med exponentiellt ökande intervall. För att stoppa frågan måste programmet använda *API-nx_mdns_service_query_stop* för att stoppa den interna timern i dessa frågor. Frågetypen kan vara NULL, vilket innebär att frågetypen är inställd på den särskilda PTR-typen "_services._dns-sd._udp.local". Den här tjänsttypen definieras av mDNS som ett sätt att identifiera alla tjänster som är tillgängliga i det lokala nätverket. Om instansnamnet anges skickas en ANY-typ (fråga SRV- och TXT-typen) med det specifika instansnamnet "name.type.local" till det lokala nätverket. Om instansnamnet är NULL skickas en PTR-typ av fråga till det lokala nätverket.

Alla svar, inklusive svar från oönskade frågor, registreras i peer-tjänstens cacheminne. Vid ett senare tillfälle använder programmet API-nx_mdns_service_lookup *för att* hämta en specifik tjänst från peer-tjänstens cacheminne.

Särskild anteckning om fragmentering: *Varje NX_MDNS_RR* struktur är fast i storlek och kan därför inte fragmenteras eftersom mDNS lägger till och tar bort RR.er. Strängar är dock varierande längd. När en sträng har tagits bort blir utrymmet tillgängligt och kan användas för en ny sträng om den nya strängen kan få plats. Men den här åtgärden gör att minnet fragmenteras. När tjänster läggs till och tas bort kan strängtabellen fragmenteras så långt att inga nya strängar kan läggas till, även om tjänstcachen innehåller tillräckligt många oanvända byte för strängen. Lokala program tenderar att vara mer stabila och förutsägbara. Därför är det mindre troligt att den lokala tjänstcachen drabbas av fragmentering. Peer Service-cachen lägger å andra sidan ständigt till RR när tjänsterna blir tillgängliga, eller tar bort RR när tjänsterna tas bort av noderna i nätverket. Tjänster i nätverket kommer och går, vilket orsakar mer frekventa allokera/ta bort-åtgärder i strängtabellen. Med tiden är det möjligt att strängtabellen blir fragmenterad. När den här situationen inträffar är en enkel lösning att tömma hela peer service-cachen. Detta kan göras genom att anropa *API:et nx_mdns_peer_cache_clear().* Observera att detta API automatiskt avslutar eventuella utestående kontinuerliga frågor.
