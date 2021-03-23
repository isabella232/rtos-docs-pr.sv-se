---
title: Kapitel 3 – Beskrivning av internt tjänst-cache
description: 'NetX Duo mDNS-modulen hanterar två interna tjänst-cacheminnen: den lokala tjänstecachen och peer-tjänstecache.'
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 007f1080a076730cfbcdedc9f063ac0c427a414c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825914"
---
# <a name="chapter-3---description-of-internal-service-cache"></a>Kapitel 3 – Beskrivning av internt tjänst-cache

NetX Duo mDNS-modulen hanterar två interna tjänst-cacheminnen: den lokala tjänstecachen och peer-tjänstecache. I cachen för lokal tjänst lagras resurs poster relaterade till tjänster som erbjuds av program som körs på noden. För inkommande frågor, om frågan matchar tjänsten som erbjuds, mDNS svar med svar lagrade i cacheminnet för den lokala tjänsten. Programmen registrerar tjänster genom att anropa API *-nx_mdns_service_add ()*. För att ta bort tjänster använder programmen API- *nx_mdns_service_delete ()*, som i sin tur skickar "tar bort" meddelanden innan motsvarande poster i den lokala tjänstecachen tas bort.

När en tjänst läggs till, behåller mDNS minst 3 resurs poster i cacheminnet för den lokala tjänsten: SRV, PTR och TXT. Ytterligare PTR-resursposter kan läggas till om tjänst typen innehåller undertyp. Ett program registrerar till exempel en tjänst:

```
*name*._*subtype*._sub._*type*._tcp.local,
```

två PTR-resursposter läggs till i cacheminnet för den lokala tjänsten, en för

```
“*_subtype._*sub*._type._*tcp.local *PTR name.type._*tcp*.*local”
```

och den andra för

```
*“_type._*tcp*.*local *PTR name.type._*tcp*.*local”.
```

Peer-tjänstecache innehåller mDNS resurs poster som tagits emot från närliggande noder. mDNS-modulen samlar in resurs poster som annonseras av andra noder i nätverket och lagrar den mottagna informationen i peer-tjänstens cacheminne. När programmet frågar efter information som värd-IPv4-eller IPv6-adresser söker mDNS i peer service-cachen efter lokalt cachelagrade svar. När program frågor för tjänster som erbjuds av peer-datorer söker mDNS i cacheminnet efter relaterade PTR-, SRV-, TXT-och IPv4-/IPv6-adress poster. Cacheminnet för peer-tjänsten lagrar också frågor som skickats till noden. Ett program kan till exempel begära en viss tjänst genom att anropa *nx_mdns_service_one_shot_query.* Om tjänsten inte finns i peer-tjänstecachen skapar mDNS frågor (PTR, SRV och TXT) i peer-tjänstecachen. De här frågorna skickas regelbundet till nätverket när tjänsten löses, eller tids gränsen uppnås. På liknande sätt kan programmet använda API- *nx_mdns_service_continous_query ()* för att begära en viss tjänst under en lång tids period (programmet avbryter en tidigare utfärdad kontinuerlig fråga med hjälp av API- *nx_mdns_service_query_stop ()* ). Om du vill söka efter en viss tjänst i peer-tjänstecachen utan att skicka frågor till nätverket, kan program använda API *-nx_mdns_serivce_lookup ().* Detta API söker bara igenom resurs posterna i peer-tjänstecachen.

Varje resurs post lagras i en data struktur *NX_MDNS_RR* i tjänstens cacheminnen. Strängar i resurs poster är variabel längd och lagras därför inte i *NX_MDNS_RRs* strukturen. Resurs posten innehåller en pekare till den faktiska minnes platsen där strängen lagras. Sträng tabellen och resurs posterna delar tjänstens cacheminne. Resurs poster lagras i början av tjänstecachen och växer mot slutet av cachen. Sträng tabellen startar från slutet av tjänstecachen och växer till början av cachen. Varje sträng i sträng tabellen har fältet längd och ett räknar fält. När en sträng läggs till i sträng tabellen, och om samma sträng redan finns i tabellen, ökar räknarvärdet och inget minne allokeras för strängen. Tjänstecachen anses vara full om inga fler resurs poster eller nya strängar kan läggas till i cachen för tjänsten.

Det finns två sätt för ett program att hitta tjänster som erbjuds i det lokala nätverket. Det kan antingen utfärda en speciell tjänst genom en enda bilds fråga, eller så kan den initiera en kontinuerlig fråga till "övervaka" aktiviteterna i nätverket. I ett scenario med en kort fråga måste programmet ange tjänst typen. mDNS söker igenom cacheminnet för den lokala tjänsten och peer-tjänstecachen. Om det finns en tjänst instans, returnerar den ensidiga frågan den information som finns i resurs posterna. Om det inte finns några poster i den lokala tjänstecachen eller peer-tjänstecachen skickar mDNS meddelanden. Om instans namnet anges skickas en *valfri* typ (fråga SRV-och txt-typ) med det specifika instans namnet, i formatet "namn. Type. local", till det lokala nätverket. Om instans namnet inte anges skickas en PTR-typ av fråga till det lokala nätverket. Den första fullständiga tjänsten som togs emot returneras till anroparen.

Kontinuerlig fråga fungerar på olika sätt. Det vanligaste användnings fallet för en kontinuerlig fråga är att övervaka det lokala nätverket för en speciell tjänst (till exempel för att ständigt söka efter utskrifts tjänster i det lokala nätverket). I det här fallet utfärdar programmet en Sök fråga (via API- *nx_mdns_service_continious_* fråga) för vissa typer av tjänster. Anroparen väntar vanligt vis inte på ett särskilt svar. För frågor som skickats som kontinuerliga frågor, skickar mDNS-modulen frågor med jämna mellanrum med exponentiellt ökande intervall. För att stoppa frågan måste programmet använda API- *nx_mdns_service_query_stop* för att stoppa den interna timern i dessa frågor. Typen av fråga kan vara NULL. i så fall har frågetyp angetts till speciell PTR-typ "_services. _DNS-SD. _udp. local". Den här tjänst typen definieras av mDNS som ett sätt att identifiera alla tjänster som är tillgängliga i det lokala nätverket. Om instans namnet anges skickas en valfri typ (fråga SRV-och TXT-typ) med det angivna instans namnet "Name. Type. local" till det lokala nätverket. Om instans namnet är NULL skickas en PTR-typ av fråga till det lokala nätverket.

Alla svar, inklusive svar från oönskade frågor, registreras i peer-tjänstecacheminnet. Vid ett senare tillfälle använder programmet API- *nx_mdns_service_lookup* för att hämta specifika tjänster från peer-tjänstecachen.

Särskild anmärkning om fragmentering: varje *NX_MDNS_RRs* struktur är fast i storlek och är därför inte föremål för fragmentering eftersom mdns lägger till och tar bort resurs poster. Däremot är strängarna variabel längd. När en sträng har tagits bort blir utrymmet tillgängligt och kan användas för en ny sträng om den nya strängen kan anpassas i. Men den här åtgärden gör att minnet fragmenteras. När tjänster läggs till och tas bort kan sträng tabellen fragmenteras till den punkt där det inte går att lägga till några nya strängar, trots att tjänstens cacheminne innehåller tillräckligt många oanvända byte för strängen. Lokala program är ofta mer stabila och förutsägbara. Därför är den lokala tjänstecachen mindre sannolik för fragmentering. Peer service-cachen, å andra sidan, lägger ständigt till resurs poster när tjänsterna blir tillgängliga eller tar bort resurs poster som tjänster tas bort av noderna i nätverket. Tjänster i nätverket kommer och går, vilket orsakar mer frekvent allokera/ta bort-åtgärder i sträng tabellen. Det är möjligt att sträng tabellen är fragmenterad med tiden. När den här situationen inträffar är en enkel lösning att tömma hela peer-tjänstecacheminnet. Detta kan göras genom att anropa API- *nx_mdns_peer_cache_clear ().* Observera att detta API automatiskt avslutar alla väntande kontinuerliga frågor.
