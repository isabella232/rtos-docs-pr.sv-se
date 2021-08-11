---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av högpresterande nätverksstackar Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 942250cf864fca3c35b97ae731549c070ac2f2f2ef3ef8897e5cbf1e705e7c6a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801815"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av högpresterande nätverksstackar Azure RTOS NetX.

## <a name="host-considerations"></a>Värdöverväganden

Inbäddad utveckling utförs vanligtvis på Windows- eller Linux-värddatorer (Unix). När programmet har kompilerats, länkats och den körbara filen genereras på värden laddas den ned till målmaskinvaran för körning.

Vanligtvis görs målnedladdningen från felsökningsverktygets felsökningsverktyg. Efter nedladdningen ansvarar felsökningsprogrammet för att tillhandahålla målkörningskontroll (go, halt, brytpunkt osv.) samt åtkomst till minne och processorregister.

De flesta felsökningsverktyg kommunicerar med målmaskinvaran via OCD-anslutningar (on-chip debug), till exempel JTAG (IEEE 1149.1) och Bakgrundsfelsökningsläge (BDM). Felsökare kommunicerar också med målmaskinvaran via In-Circuit(ICE)-anslutningar. Både OCD- och ICE-anslutningar ger robusta lösningar med minimal intrång på målprogramvaran.

Precis som för resurser som används på värden levereras källkoden för NetX i ASCII-format och kräver cirka 1 MB utrymme på värddatorns hårddisk.

## <a name="target-considerations"></a>Målöverväganden

NetX kräver mellan 5 KByte och 45 KByte Read-Only (ROM) på målet. Ytterligare 1 till 5 KByte av målets RAM-minne (Random Access Memory) krävs för NetX-trådstacken och andra globala datastrukturer.

Dessutom kräver NetX användning av två ThreadX-timerobjekt och ett ThreadX mutex-objekt. Dessa anläggningar används för periodiska bearbetningsbehov och trådskydd i NetX-protokollstacken.

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS NetX kan hämtas från vår offentliga källkodsdatabas på <https://github.com/azure-rtos/netx/> .

Följande är en lista över flera viktiga filer på lagringsplatsen:

- ***nx_api.h:*** C-huvudfilen som innehåller alla system är lika med, datastrukturer och tjänstprototyper.
- ***nx_port.h:*** C-huvudfil som innehåller alla utvecklingsverktygets och målspecifika datadefinitioner och strukturer.  
- ***demo_netx.c***: C-fil som innehåller ett litet demoprogram.
- ***nx.a (eller nx.lib)** _: Binär version av NetX C-biblioteket som distribueras med _standard*-paketet.             |

## <a name="netx-installation"></a>NetX-installation

Du kan installera NetX genom att klona GitHub på den lokala datorn. Följande är en vanlig syntax för att skapa en klon av NetX-lagringsplatsen på datorn:

```c
    git clone https://github.com/azure-rtos/netx
```

Du kan också ladda ned en kopia av lagringsplatsen med **knappen Ladda** ned på GitHub huvudsidan.

Du hittar också anvisningar för att skapa NetX-biblioteket på startsidan för onlinedatabasen.

> [!IMPORTANT]
> Programprogramvaran behöver åtkomst till NetX-biblioteksfilen (vanligtvis ***nx.a** _ eller _*_nx.lib_*_) och C innehåller filerna _*_nx_api.h och nx_port.h_**. Detta åstadkoms antingen genom att ange lämplig sökväg för utvecklingsverktygen eller genom att kopiera dessa filer till programutvecklingsområdet.

## <a name="using-netx"></a>Använda NetX

Om du vill använda NetX måste programkoden innehålla ***nx_api.h** _ under kompileringen och länka till NetX-biblioteket _*_nx.a_*_ (eller _ *_nx.lib_*)*.

Följande är de fyra nödvändiga stegen för att skapa ett NetX-program:

1. Inkludera filen ***nx_api.h i*** alla programfiler som använder NetX-tjänster eller datastrukturer.
1. Initiera NetX-systemet genom att anropa ***nx_system_initialize** _ från funktionen _ *_tx_application_define_** eller en programtråd.  
1. Skapa en IP-instans, aktivera Address Resolution Protocol (ARP) vid behov och eventuella sockets ***när nx_system_initialize*** anropas.  
1. Kompilera programkällan och länka till NetX-körningsbiblioteket ***nx.a** _ (eller _*_nx.lib_**). Den resulterande avbildningen kan laddas ned till målet och köras!

## <a name="troubleshooting"></a>Felsökning

Varje NetX-port levereras med ett eller flera exempel som körs i ett faktiskt nätverk eller via en simulerad nätverksdrivrutin. Det är alltid en bra idé att få igång exempelsystemet först.

Om exempelsystemet inte körs korrekt utför du följande åtgärder för att begränsa problemet:

1. Fastställ hur mycket av exemplet som körs.
2. Öka stackstorlekarna i alla nya programtrådar.
3. Kompilera om NetX-biblioteket med lämpliga felsökningsalternativ som anges i avsnittet konfigurationsalternativ.
4. Granska **NX_IP** struktur för att se om paket skickas eller tas emot.
5. Granska standardpaketpoolen för att se om det finns tillgängliga paket.
6. Se till att nätverksdrivrutinen tillhandahåller ARP- och IP-paket med sina huvuden på 4 byte-gränser för program som kräver IP-anslutning.
7. Kringgå tillfälligt de senaste ändringarna för att se om problemet försvinner eller ändras. Sådan information bör vara användbar för våra supporttekniker.

Följ procedurerna som beskrivs i [kundsupportens avsnitt för](about-this-guide.md) att skicka den information som samlats in från felsökningsstegen.

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ när du skapar NetX-biblioteket och programmet med NetX. Konfigurationsalternativen kan definieras i programkällan, på kommandoraden eller i indelningsfilen ***nx_user.h,*** om inget annat anges.

> [!IMPORTANT]
> Alternativ som definieras **i * nx_user.h** _ tillämpas endast om programmet och NetX-biblioteket har skapats med _ *NX_INCLUDE_USER_DEFINE_FILE** definierat.

I följande avsnitt visas de konfigurationsalternativ som är tillgängliga i NetX.

### <a name="system-configuration-options"></a>Systemkonfigurationsalternativ  

| Alternativ  | Beskrivning  |
|---|---|
| X_DEBUG | Definierad aktiverar valfri felsökningsinformation för utskrift som är tillgänglig från RAM Ethernet-nätverksdrivrutinen. |
| NX_DISABLE_ERROR_CHECKING | Definierad tar bort det grundläggande API:et för NetX-felkontroll och förbättrar prestandan. API-returkoder som inte påverkas av inaktivering av felkontroll visas i fetstil i API-definitionen. Den här definierar används vanligtvis när programmet har felsökt och när dess användning förbättrar prestanda och minskar kodstorleken. |
| NX_DRIVER_DEFERRED_PROCESSING | Definierad aktiverar uppskjuten pakethantering av nätverksdrivrutiner. Detta gör att nätverksdrivrutinen kan placera ett paket på IP-instansen och få den verkliga bearbetningsrutinen anropad från den interna NETX-IP-hjälptråden. |
| NX_ENABLE_EXTENDED_NOTIFY_SUPPORT | Aktiverar fler återanrops hookar i stacken. Dessa återanropsfunktioner används av BSD-omslutningsskiktet. Som standard definieras inte det här alternativet. |
| NX_ENABLE_SOURCE_ADDRESS_CHECK | Definierad, gör att källadressen för inkommande paket kan kontrolleras. Som standard är det här alternativet inaktiverat. |
| NX_LITTLE_ENDIAN | Definierar utför nödvändig byteväxling på little endian för att säkerställa att protokollhuvudena är i rätt big endian format. Observera att standardinställningen vanligtvis är i ***nx_port.h***. |
| NX_MAX_PHYSICAL_INTERFACES | Anger det totala antalet fysiska nätverksgränssnitt på enheten. Standardvärdet är 1 och definieras i ***nx_api.h***. En enhet måste ha minst ett fysiskt gränssnitt. Observera att detta inte inkluderar loopback-gränssnittet. |
| NX_PHYSICAL_HEADER | Anger storleken i byte för den fysiska ramens sidhuvud. Standardvärdet är 16 (baserat på en typisk Ethernet-ram på 14 byte justerad till 32-bitars gräns) och definieras i ***nx_api.h** _. Programmet kan åsidosätta standardvärdet genom att definiera _*_värdet innan nx_api.h_*_ inkluderas, till exempel i _ *_nx_user.h_*.* |

### <a name="arp-configuration-options"></a>Konfigurationsalternativ för ARP  

| Alternativ  | Beskrivning  |
|---|---|
| NX_ARP_DEFEND_BY_REPLY | Definierad gör att NetX kan skydda sin IP-adress genom att skicka ett ARP-svar. |
| NX_ARP_DEFEND_INTERVAL | Definierar intervallet, i sekunder, som ARP-modulen skickar ut nästa försvarspaket som svar på ett inkommande ARP-meddelande som anger en adress i konflikt. |
| NX_ARP_DISABLE_AUTO_ARP_ENTRY | Har bytt namn **till NX_DISABLE_ARP_AUTO_ENTRY**. Även om det fortfarande stöds, rekommenderas nya designer att använda **NX_DISABLE_ARP_AUTO_ENTRY**.
| NX_ARP_EXPIRATION_RATE | Anger antalet sekunder som ARP-poster förblir giltiga. Standardvärdet noll inaktiverar förfallodatum eller föråldring av ARP-poster och definieras i ***nx_api.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.
| NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | Har bytt namn **till NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION**. Även om det fortfarande stöds, uppmuntras nya designer att använda **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION**. |
| NX_ARP_MAX_QUEUE_DEPTH | Anger det maximala antalet paket som kan köas i kö i väntan på ett ARP-svar. Standardvärdet är 4 och definieras i ***nx_api.h***. |
| NX_ARP_MAXIMUM_RETRIES | Anger det maximala antalet ARP-återförsök som görs utan ett ARP-svar. Standardvärdet är 18 och definieras i ***nx_api.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _*_nx_api.h_**. |
| NX_ARP_UPDATE_RATE | Anger antalet sekunder mellan ARP-återförsök. Standardvärdet är 10, vilket motsvarar 10 sekunder och definieras i ***nx_api.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _*_nx_api.h_**. |
| NX_DISABLE_ARP_AUTO_ENTRY | Definierad inaktiverar att ange information om ARP-begäran i ARP-cachen. |
| NX_DISABLE_ARP_INFO | Definierad, inaktiverar ARP-informationsinsamling. |
| NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION | Definierad, gör att ARP kan anropa en återanrops meddela-funktion vid identifiering av MAC-adressen uppdateras. |

### <a name="icmp-configuration-options"></a>ICMP-konfigurationsalternativ  

| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_ICMP_INFO | Definierad, inaktiverar ICMP-informationsinsamling. |
| NX_DISABLE_ICMP_RX_CHECKSUM | Inaktiverar beräkningen av ICMP-kontrollsumma vid mottagna ICMP-paket. Det här alternativet är användbart när nätverksgränssnittsdrivrutinen kan verifiera ICMP-kontrollsumman och programmet inte använder funktionen IP-fragmentering. Som standard definieras inte det här alternativet. |
| NX_DISABLE_ICMP_TX_CHECKSUM | Inaktiverar beräkning av kontrollsumma för ICMP vid överförda ICMP-paket. Det här alternativet är användbart när nätverksgränssnittsdrivrutinen kan beräkna ICMP-kontrollsumman och programmet inte använder funktionen IP-fragmentering. Som standard definieras inte det här alternativet. |

### <a name="igmp-configuration-options"></a>Konfigurationsalternativ för IGMP  

| Alternativ  | Beskrivning  |
|---|---| 
| NX_DISABLE_IGMP_INFO | Definierad, inaktiverar IGMP-informationsinsamling. |
| NX_DISABLE_IGMPV2 | Definierad, inaktiverar IGMPv2-stöd och NetX stöder endast IGMPv1. Som standard är det här alternativet inte inställt och definieras ***i nx_api.h***. |
| NX_MAX_MULTICAST_GROUPS | Anger det maximala antalet multicast-grupper som kan vara ansluten. Standardvärdet är 7 och definieras i ***nx_api.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas. |

### <a name="ip-configuration-options"></a>IP-konfigurationsalternativ

| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_FRAGMENTATION | Definierad, inaktiverar IP-fragmentering och sätta ihop logiken på en ny. |
| NX_DISABLE_IP_INFO | Definierad, inaktiverar IP-informationsinsamling. |
| NX_DISABLE_IP_RX_CHECKSUM | Definierad, inaktiverar logik för kontrollsumma för mottagna IP-paket. Detta är användbart om nätverksenheten kan verifiera kontrollsumman för IP-huvudet och programmet inte använder IP-fragmentering. |
| NX_DISABLE_IP_TX_CHECKSUM | Definierad, inaktiverar logik för kontrollsumma på SKICKADE IP-paket. Detta är användbart i situationer där den underliggande nätverksenheten kan generera kontrollsumman för IP-huvudet och programmet inte använder IP-fragmentering. |
| NX_DISABLE_LOOPBACK_INTERFACE | Definierad inaktiverar NetX-stöd för loopback-gränssnittet. |
| NX_DISABLE_RX_SIZE_CHECKING | Definierad inaktiverar storlekskontrollen på mottagna paket. |
| NX_ENABLE_IP_STATIC_ROUTING | Definierad aktiverar statisk IP-routning där en måladress kan tilldelas en specifik nexthop-adress. Statisk IP-routning är inaktiverat som standard. |
| NX_IP_PERIODIC_RATE | Definierad anger antalet Tick för ThreadX-timer på en sekund. Standardvärdet härleds från ThreadX-symbolen **TX_TIMER_TICKS_PER_SECOND,** som som standard är inställt på 100 (10 ms timer). Program bör vara försiktig när du ändrar det här värdet, eftersom resten av NetX-modulerna härleder tidsinformation **från NX_IP_PERIODIC_RATE*.** |
| NX_IP_ROUTING_TABLE_SIZE | Definierad anger det maximala antalet poster i den statiska IP-routningstabellen, som är en lista över ett utgående gränssnitt och nästa hopp
adresser för en viss måladress. Standardvärdet är 8 och definieras i ***nx_api.h.** _ Den här symbolen används bara om _ *NX_ENABLE_IP_STATIC_ROUTING** har definierats. |

### <a name="packet-configuration-options"></a>Alternativ för paketkonfiguration  

| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_PACKET_INFO | Definierad, inaktiverar insamling av paketpoolsinformation. | 
| NX_PACKET_HEADER_PAD | Definierad möjliggör utfyllnad mot slutet av NX_PACKET kontrollblocket. Antalet **ULONG-ord** som ska ersättas definieras av **NX_PACKET_HEADER_PAD_SIZE**. |
| NX_PACKET_HEADER_PAD_SIZE | Anger antalet **ULONG-ord** som ska läggas till i NX_PACKET, så att paketnyttolasten kan börja vid önskad nivå
Justering. Den här funktionen är användbar när du tar emot buffertbeskrivningar direkt till NX_PACKET-nyttolastområdet och nätverksgränssnittet tar emot logik eller cacheåtgärdslogiken förväntar sig att buffertstartadressen uppfyller vissa justeringskrav. Det här värdet blir endast **giltigt när NX_PACKET_HEADER_PAD** har definierats. |

### <a name="rarp-configuration-options"></a>RARP-konfigurationsalternativ  

| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_RARP_INFO | Definierad, inaktiverar RARP-informationsinsamling. |

### <a name="tcp-configuration-options"></a>TCP-konfigurationsalternativ

| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_RESET_DISCONNECT | Definierad inaktiverar återställningsbearbetningen under frånkoppling när det angivna tidsgränsvärdet anges som **NX_NO_WAIT**. |
| NX_DISABLE_TCP_INFO | Definierad, inaktiverar TCP-informationsinsamling. |
| NX_DISABLE_TCP_RX_CHECKSUM | Definierad, inaktiverar logik för kontrollsumma på mottagna TCP-paket. Detta är bara användbart i situationer där länklagret har tillförlitlig kontrollsumma eller CRC-bearbetning, eller där gränssnittsdrivrutinen kan verifiera TCP-kontrollsumman i maskinvaran. |
| NX_DISABLE_TCP_TX_CHECKSUM | Definierad, inaktiverar logik för kontrollsumma för att skicka TCP-paket. Detta är bara användbart i situationer där den mottagande nätverksnoden har den mottagna logiken för TCP-kontrollsumma inaktiverad eller om den underliggande nätverksdrivrutinen kan generera TCP-kontrollsumman. |
| NX_ENABLE_TCP_KEEPALIVE | Definierad aktiverar den valfria TCP-keepalive-timern. Standardinställningarna är inte aktiverade. |
| NX_ENABLE_TCP_MSS_CHECKING | Definierad aktiverar verifiering av minsta peer MSS innan du godkänner en TCP-anslutning. Om du vill använda den här **funktionen måste NX_ENABLE_TCP_MSS_MINIMUM** definieras. Det här alternativet är inte aktiverat som standard. |
NX_ENABLE_TCP_WINDOW_SCALING | Aktiverar alternativet för fönsterskalning för TCP-program. Om alternativet för fönsterskalning definieras förhandlas det under TCP-anslutningsfasen och programmet kan ange en fönsterstorlek som är större än 64 000. Standardinställningen är inte aktiverad (inte definierad). |
| NX_MAX_LISTEN_REQUESTS | Anger det maximala antalet serverlyssnandebegäranden. Standardvärdet är 10 och definieras i ***nx_api.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas. |
| NX_TCP_ACK_EVERY_N_PACKETS | Anger antalet TCP-paket som ska tas emot innan en ACK skickas. Observera om **NX_TCP_IMMEDIATE_ACK** är aktiverat **men NX_TCP_ACK_EVERY_N_PACKETS** är det här värdet automatiskt inställt på 1 för bakåtkompatibilitet. |
| NX_TCP_ACK_TIMER_RATE | Anger hur antalet system tick (NX_IP_PERIODIC_RATE) divideras för att beräkna timerhastigheten för DEN TCP-fördröjda ACK-bearbetningen. Standardvärdet är 5, vilket representerar 200 ms och definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _*_nx_api.h_**. |
| NX_TCP_ENABLE_KEEPALIVE | Har bytt namn till **NX_ENABLE_TCP_KEEPALIVE**. Även om det fortfarande stöds, rekommenderas nya designer att använda **NX_ENABLE_TCP_KEEPALIVE**. |
| NX_TCP_ENABLE_WINDOW_SCALING | Har bytt namn till **NX_ENABLE_TCP_WINDOW_SCALING**. Även om det fortfarande stöds, rekommenderas nya designer att använda **NX_ENABLE_TCP_WINDOW_SCALING**. |
| NX_TCP_FAST_TIMER_RATE | Anger hur antalet interna NetX-tick (NX_IP_PERIODIC_RATE) delas upp för att beräkna den snabba TCP-timerhastigheten. Den snabba TCP-timern används för att driva de olika TCP-timers, inklusive den fördröjda ACK-timern. Standardvärdet är 10, vilket motsvarar 100 ms förutsatt att ThreadX-timern körs på 10 ms. Det här värdet definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _*_nx_api.h_**. |
| NX_TCP_IMMEDIATE_ACK | Definierad aktiverar valfri tcp omedelbar ACK-svarsbearbetning. Att definiera den här symbolen motsvarar att **definiera NX_TCP_ACK_EVERY_N_PACKETS** till 1. |
| NX_TCP_KEEPALIVE_INITIAL | Anger antalet sekunder av inaktivitet innan keepalive-timern aktiveras. Standardvärdet är 7200, vilket motsvarar 2 timmar och definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _*_nx_api.h_**. |
| NX_TCP_KEEPALIVE_RETRIES | Anger hur många keepalive-återförsök som tillåts innan anslutningen anses vara bruten. Standardvärdet är 10, vilket representerar 10 återförsök och definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas. |
| NX_TCP_KEEPALIVE_RETRY | Anger antalet sekunder mellan återförsök för keepalive-timern förutsatt att den andra sidan av anslutningen inte svarar. Standardvärdet är 75, vilket motsvarar 75 sekunder mellan återförsöken och definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas. |
| NX_TCP_MAX_OUT_OF_ORDER_PACKETS | Symbol som definierar det maximala antalet out-of-order TCP-paket som kan behållas i TCP-socketens mottagningskö. Den här symbolen kan användas för att begränsa antalet paket i kö i TCP-mottagningssocketen, vilket förhindrar att paketpoolen blir utsvulten. Som standard definieras inte den här symbolen, vilket innebär att det inte finns någon gräns för antalet out-of-order-paket som köas i TCP-socketen. |
| NX_TCP_MAXIMUM_RETRIES | Anger hur många återförsök för dataöverföring som tillåts innan anslutningen anses vara bruten. Standardvärdet är 10, vilket representerar 10 återförsök och definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _*_nx_api.h_**. |
| NX_TCP_MAXIMUM_TX_QUEUE | Anger det maximala djupet för TCP-överföringskön innan TCP-sändningsbegäranden pausas eller avvisas. Standardvärdet är 20, vilket innebär att högst 20 paket kan finnas i överföringskön vid en given tidpunkt. Observera att paketen finns kvar i överföringskön tills en ACK som täcker vissa eller alla paketdata tas emot från den andra sidan av anslutningen. Den här konstanten definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan det inkluderar _*_nx_api.h_**. |
| X_TCP_MSS_CHECKING_ENABLED | Har bytt namn **till NX_ENABLE_TCP_MSS_CHECKING**. Även om det fortfarande stöds, rekommenderas nya designer att använda **NX_ENABLE_TCP_MSS_CHECKING**. |
| NX_TCP_MSS_MINIMUM | Symbol som definierar det minimala MSS-värdet som NetX TCP-modulen accepterar. Den här funktionen aktiveras av **NX_ENABLE_TCP_MSS_CHECK** |
| NX_TCP_RETRY_SHIFT | Anger hur tidsgränsen för återöverföring ändras mellan återförsök. Om det här värdet är 0 är den första tidsgränsen för återöverföring samma som efterföljande tidsgränser för återöverföring. Om det här värdet är 1 blir varje efterföljande återöverföring dubbelt så lång. Om det här värdet är 2 är varje efterföljande tidsgräns för återöverföring fyra gånger så lång. Standardvärdet är 0 och definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _*_nx_api.h_**. |
| NX_TCP_TRANSMIT_TIMER_RATE| Anger hur antalet system tick som NX_IP_PERIODIC_RATE **)** divideras för att beräkna timerhastigheten för BEARBETNING av TCP-överföringsförsök. Standardvärdet är 1, vilket representerar 1 sekund och definieras i **_nx_tcp.h_*_. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan det inkluderar _*_nx_api.h_**. |

### <a name="udp-configuration-options"></a>UDP-konfigurationsalternativ
| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_UDP_INFO | Definierad, inaktiverar UDP-informationsinsamling. |
| NX_DISABLE_UDP_RX_CHECKSUM | Definierad inaktiverar UDP-beräkningen av kontrollsumma för inkommande UDP-paket. Detta är användbart om nätverksgränssnittsdrivrutinen kan verifiera kontrollsumman för UDP-huvudet i maskinvaran och programmet inte aktiverar logik för IP-fragmentering. |
| NX_DISABLE_UDP_TX_CHECKSUM | Definierad inaktiverar UDP-beräkningen av kontrollsumma för utgående UDP-paket. Detta är användbart om nätverksgränssnittsdrivrutinen kan beräkna kontrollsumman för UDP-huvudet och infoga värdet i IP-huvudet innan data överförs, och programmet inte aktiverar logik för IP-fragmentering. |

## <a name="netx-version-id"></a>NetX-versions-ID

Den aktuella versionen av NetX är tillgänglig för både användaren och programprogramvaran under körning. Programmeraren kan hämta NetX-versionen från **filen nx_port.h.** Dessutom innehåller den här filen en versionshistorik för motsvarande port. Programprogramvara kan hämta NetX-versionen genom att undersöka den globala **strängen _nx_version_id** i **_nx_port.h_**.  

Programvaror kan också hämta versionsinformation från konstanterna som visas nedan, som definieras i ***nx_api.h**.*

Dessa konstanter identifierar den aktuella produktversionen efter namn och produkt major och delversion.

```c
#define EL_PRODUCT_NETX

#define NETX_MAJOR_VERSION

#define NETX_MINOR_VERSION
```