---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av nätverks stacken med hög prestanda för Azure återställnings tider-NetX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80d6ba18f47ad2b017dfa32260c83ba074a6dbac
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825638"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av nätverks stacken med hög prestanda för Azure återställnings tider-NetX.

## <a name="host-considerations"></a>Värd överväganden

Inbäddad utveckling utförs vanligt vis på Windows-eller Linux-värddatorer (UNIX). När programmet har kompilerats, länkats och den körbara filen genereras på värden laddas den ned till mål maskin varan för körning.

Normalt görs mål hämtningen från utvecklings verktygets fel sökare. Efter nedladdningen ansvarar fel sökaren för att tillhandahålla mål körnings kontroll (gå till, stoppa, Bryt punkt osv.) samt åtkomst till minne och processor register.

De flesta utvecklings verktyg för fel sökning kommunicerar med mål maskin varan via OCD-anslutningar (on-chip debug) som JTAG (IEEE 1149,1) och fel söknings läge för bakgrunden (BDM). Fel sökare kommunicerar också med mål maskin vara via ICE-anslutningar (In-Circuit emulation). Både OCD-och ICE-anslutningar ger robusta lösningar med minimalt intrång på den inhemske program varan.

För resurser som används på värden levereras käll koden för NetX i ASCII-format och kräver cirka 1 MB utrymme på värddatorns hård disk.

## <a name="target-considerations"></a>Mål överväganden

NetX kräver mellan 5 KByte och 45 KB Read-Only minne (ROM) på målet. Det krävs ytterligare 1 till 5 KByte av målets RAM-minne (Random Access Memory) för NetX-trådens stack och andra globala data strukturer.

Dessutom kräver NetX användning av två ThreadX-Timer-objekt och ett ThreadX mutex-objekt. Dessa funktioner används för periodiska bearbetnings behov och tråd skydd i NetX-protokollstacken.

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider-NetX kan hämtas från vår offentliga käll kods lagrings plats på <https://github.com/azure-rtos/netx/> .

Följande är en lista över flera viktiga filer i lagrings platsen:

- ***nx_api. h***: C-huvudfilen som innehåller alla system likställda, data strukturer och tjänst prototyper.
- ***nx_port. h***: C-huvudfilen som innehåller alla utvecklingsverktyg-och språkspecifika data definitioner och strukturer.  
- ***demo_netx. c***: c-fil som innehåller ett litet demo program.
- ***NX. a (eller NX. lib)** _: binär version av netx C-biblioteket som distribueras med _standard *-paketet.             |

## <a name="netx-installation"></a>NetX-installation

Du kan installera NetX genom att klona GitHub-lagringsplatsen till den lokala datorn. Följande är en typisk syntax för att skapa en klon av NetX-lagringsplatsen på din dator:

```c
    git clone https://github.com/azure-rtos/netx
```

Alternativt kan du ladda ned en kopia av lagrings platsen med hjälp av knappen **Ladda ned** på GitHub-huvud sidan.

Du hittar också instruktioner för att skapa NetX-biblioteket på den första sidan i online-lagringsplatsen.

> [!IMPORTANT]
> Program varan behöver åtkomst till NetX-biblioteks filen (vanligt vis ***NX. a** _ eller _*_NX. lib_*_) och C include-filerna _ *_nx_api. h och nx_port. h_* *. Detta åstadkommer du genom att ange lämplig sökväg för utvecklingsverktyg eller genom att kopiera filerna till program utvecklings ytan.

## <a name="using-netx"></a>Använda NetX

Om du vill använda NetX måste program koden innehålla ***nx_api. h** _ under kompileringen och länka med netx-biblioteket _*_NX. a_*_ (eller _ *_NX. lib_*) *.

Nedan följer fyra nödvändiga steg för att skapa ett NetX-program:

1. Inkludera filen ***nx_api. h*** i alla filer som använder netx Services eller data strukturer.
1. Initiera NetX-systemet genom att anropa ***nx_system_initialize** _ från funktionen _ *_tx_application_define_** eller en program tråd.  
1. Skapa en IP-instans, aktivera adress matchnings protokollet (ARP), om det behövs, och eventuella Sockets efter ***nx_system_initialize*** anropas.  
1. Kompilera program källan och länka med NetX runtime library ***NX. a** _ (eller _ *_NX. lib_* *). Den resulterande bilden kan laddas ned till målet och köras!

## <a name="troubleshooting"></a>Felsökning

Varje NetX-port levereras med ett eller flera exempel som körs på ett faktiskt nätverk eller via en simulerad nätverks driv rutin. Det är alltid en bra idé att få exempel systemet igång först.

Om exempel systemet inte körs korrekt utför du följande åtgärder för att begränsa problemet:

1. Ta reda på hur mycket av exemplet som körs.
2. Öka stack storlekarna i alla nya program trådar.
3. Kompilera om biblioteket NetX med lämpliga fel söknings alternativ som anges i avsnittet konfigurations alternativ.
4. Granska **NX_IPs** strukturen för att se om paket skickas eller tas emot.
5. Granska standard paketets pool för att se om det finns tillgängliga paket.
6. Se till att nätverks driv rutinen tillhandahåller ARP-och IP-paket med sina huvuden på 4 bytes gränser för program som kräver IP-anslutning.
7. Kringgå tillfälligt eventuella nyligen gjorda ändringar för att se om problemet försvinner eller ändras. Sådan information bör vara användbar för våra support tekniker.

Följ de procedurer som beskrivs i avsnittet [kund Support Center](about-this-guide.md) för att skicka den information som samlas in från fel söknings stegen.

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ när du skapar NetX-biblioteket och programmet med NetX. Konfigurations alternativen kan definieras i program källan, på kommando raden eller i ***nx_user. h*** include-filen, om inget annat anges.

> [!IMPORTANT]
> Alternativ som definieras i ***nx_user. h** _ tillämpas endast om program-och netx-biblioteket har skapats med _ *NX_INCLUDE_USER_DEFINE_FILE** definierat.

I följande avsnitt listas de konfigurations alternativ som är tillgängliga i NetX.

### <a name="system-configuration-options"></a>Alternativ för system konfiguration  

| Alternativ  | Beskrivning  |
|---|---|
| X_DEBUG | Definierad, aktiverar den valfria fel söknings informationen från RAM-nätverkskortets nätverks driv rutin. |
| NX_DISABLE_ERROR_CHECKING | Definierad tar bort det grundläggande NetX-API: et för fel sökning och förbättrar prestandan. API-retur koder som inte påverkas av inaktive ring av fel kontroll visas i fetstil i API-definitionen. Den här definiera används vanligt vis när programmet har fel sökning och när dess användning har förbättrat prestanda och minskar kod storleken. |
| NX_DRIVER_DEFERRED_PROCESSING | Definierad, aktiverar uppskjuten trafik hantering av nätverks driv rutiner. Detta gör att nätverks driv rutinen kan placera ett paket på IP-instansen och ha den faktiska bearbetnings rutinen som anropas från den interna IP-NetX tråd. |
| NX_ENABLE_EXTENDED_NOTIFY_SUPPORT | Aktiverar fler Hook-hookar i stacken. Dessa återanrops funktioner används av BSD-skiktet. Som standard är det här alternativet inte definierat. |
| NX_ENABLE_SOURCE_ADDRESS_CHECK | Definierad, gör det möjligt att kontrol lera käll adressen för det inkommande paketet. Som standard är det här alternativet inaktiverat. |
| NX_LITTLE_ENDIAN | Definierad, utför nödvändiga byte växling i little endian miljöer för att se till att protokoll rubrikerna är i rätt big endian format. Observera att standardvärdet är vanligt vis installations programmet i ***nx_port. h***. |
| NX_MAX_PHYSICAL_INTERFACES | Anger det totala antalet fysiska nätverks gränssnitt på enheten. Standardvärdet är 1 och definieras i ***nx_api. h***. En enhet måste ha minst ett fysiskt gränssnitt. OBS! detta inkluderar inte loopback-gränssnittet. |
| NX_PHYSICAL_HEADER | Anger storleken i byte för ramens fysiska rubrik. Standardvärdet är 16 (baserat på en typisk 14 byte-Ethernet-ram som är justerad till 32-bitars gräns) och definieras i ***nx_api. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _*_nx_api. h_*_ ingår, t. ex. i _ *_nx_user. h_*. * |

### <a name="arp-configuration-options"></a>Konfigurations alternativ för ARP  

| Alternativ  | Beskrivning  |
|---|---|
| NX_ARP_DEFEND_BY_REPLY | Definierad, tillåter att NetX skyddar sin IP-adress genom att skicka ett ARP-svar. |
| NX_ARP_DEFEND_INTERVAL | Definierar intervallet, i sekunder, skickar ARP-modulen ut nästa försvara paket som svar på ett inkommande ARP-meddelande som anger en adress i konflikt. |
| NX_ARP_DISABLE_AUTO_ARP_ENTRY | Har bytt namn till **NX_DISABLE_ARP_AUTO_ENTRY**. Även om det fortfarande stöds, uppmuntras nya ritningar att använda **NX_DISABLE_ARP_AUTO_ENTRY**.
| NX_ARP_EXPIRATION_RATE | Anger antalet sekunder som ARP-poster fortfarande är giltiga. Standardvärdet noll inaktiverar förfallo datum eller åldrande för ARP-poster och definieras i ***nx_api. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.
| NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | Har bytt namn till **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION**. Även om det fortfarande stöds, uppmuntras nya ritningar att använda **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION**. |
| NX_ARP_MAX_QUEUE_DEPTH | Anger det maximala antalet paket som kan köas i kö i väntan på ett ARP-svar. Standardvärdet är 4 och definieras i ***nx_api. h***. |
| NX_ARP_MAXIMUM_RETRIES | Anger det maximala antal ARP-försök som gjorts utan ARP-svar. Standardvärdet är 18 och definieras i ***nx_api. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _ *_nx_api. h_* *. |
| NX_ARP_UPDATE_RATE | Anger antalet sekunder mellan ARP-försök. Standardvärdet är 10, vilket representerar 10 sekunder och definieras i ***nx_api. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _ *_nx_api. h_* *. |
| NX_DISABLE_ARP_AUTO_ENTRY | Definierad, inaktiverar registrering av ARP-information i ARP-cachen. |
| NX_DISABLE_ARP_INFO | Definierad, inaktiverar insamling av ARP-information. |
| NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION | Definierad, tillåter ARP att anropa en motringnings funktion för att identifiera MAC-adressen. |

### <a name="icmp-configuration-options"></a>Konfigurations alternativ för ICMP  

| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_ICMP_INFO | Definierad, inaktiverar ICMP-information från insamling. |
| NX_DISABLE_ICMP_RX_CHECKSUM | Inaktiverar beräkningen av ICMP-kontrollsumma på mottagna ICMP-paket. Det här alternativet är användbart när nätverks gränssnittets driv rutin kan verifiera ICMP-kontrollsumma och programmet använder inte funktionen IP-fragmentering. Som standard är det här alternativet inte definierat. |
| NX_DISABLE_ICMP_TX_CHECKSUM | Inaktiverar beräkning av ICMP-kontrollsumma på överförda ICMP-paket. Det här alternativet är användbart när nätverks gränssnittets driv rutin kan beräkna ICMP-kontrollsumma och programmet inte använder funktionen IP-fragmentering. Som standard är det här alternativet inte definierat. |

### <a name="igmp-configuration-options"></a>Konfigurations alternativ för IGMP  

| Alternativ  | Beskrivning  |
|---|---| 
| NX_DISABLE_IGMP_INFO | Definierad, inaktiverar insamling av IGMP-information. |
| NX_DISABLE_IGMPV2 | Definierad, inaktiverar IGMPv2-stöd och NetX stöder endast IGMPv1. Som standard är det här alternativet inte angivet och definieras i ***nx_api. h***. |
| NX_MAX_MULTICAST_GROUPS | Anger det maximala antalet multicast-grupper som kan anslutas. Standardvärdet är 7 och definieras i ***nx_api. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår. |

### <a name="ip-configuration-options"></a>Alternativ för IP-konfiguration

| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_FRAGMENTATION | Definierad, inaktiverar IP-fragmentering och omsammansättnings logik. |
| NX_DISABLE_IP_INFO | Definierad, inaktiverar insamling av IP-information. |
| NX_DISABLE_IP_RX_CHECKSUM | Definierad, inaktiverar kontroll summa för mottagna IP-paket. Detta är användbart om nätverks enheten kan verifiera kontroll summan för IP-huvudet och programmet inte använder IP-fragmentering. |
| NX_DISABLE_IP_TX_CHECKSUM | Definierad, inaktiverar logik för kontroll summa för IP-paket som skickas. Detta är användbart i situationer där den underliggande nätverks enheten kan generera kontroll summan för IP-huvudet och programmet inte använder IP-fragmentering. |
| NX_DISABLE_LOOPBACK_INTERFACE | Definierad, inaktiverar NetX-stöd för loopback-gränssnittet. |
| NX_DISABLE_RX_SIZE_CHECKING | Definierad, inaktiverar storleks kontrollen på mottagna paket. |
| NX_ENABLE_IP_STATIC_ROUTING | Definierad, aktiverar statisk IP-routning där en mål adress kan tilldelas en viss nästa hopp-adress. Som standard är IP-statisk routning inaktive rad. |
| NX_IP_PERIODIC_RATE | Definierad anger antalet ThreadX timer-Tick i en sekund. Standardvärdet härleds från ThreadX symbol **TX_TIMER_TICKS_PER_SECOND,** vilket som standard är inställt på 100 (10ms timer). Program bör vara försiktiga när du ändrar det här värdet, eftersom resten av NetX-modulerna härleder tids information från **NX_IP_PERIODIC_RATE *.** |
| NX_IP_ROUTING_TABLE_SIZE | Definierat anger det maximala antalet poster i tabellen statisk routningstabell, som är en lista över ett utgående gränssnitt och nästa hopp
adresser för en specifik mål adress. Standardvärdet är 8 och definieras i ***nx_api. h.** _ Den här symbolen används endast om _ *NX_ENABLE_IP_STATIC_ROUTING** har definierats. |

### <a name="packet-configuration-options"></a>Alternativ för paket konfiguration  

| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_PACKET_INFO | Definierad, inaktiverar insamling av paketets pool information. | 
| NX_PACKET_HEADER_PAD | Definierad, aktiverar utfyllnad mot slutet av NX_PACKET kontroll blocket. Antalet **ulong** -ord som ska pad definieras av **NX_PACKET_HEADER_PAD_SIZE**. |
| NX_PACKET_HEADER_PAD_SIZE | Anger antalet **ulong** -ord som ska fyllas i NX_PACKET-strukturen, vilket gör det möjligt för paketets nytto last att starta vid önskad
Justera. Den här funktionen är användbar när du ska ta emot buffertens beskrivare direkt i NX_PACKET nytto lastområdet, och nätverks gränssnittet tar emot logik eller om cache åtgärds logiken förväntar sig att de uppfyller vissa justerings krav. Det här värdet blir giltigt endast när **NX_PACKET_HEADER_PAD** har definierats. |

### <a name="rarp-configuration-options"></a>Konfigurations alternativ för RARP  

| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_RARP_INFO | Definierad, inaktiverar insamling av RARP-information. |

### <a name="tcp-configuration-options"></a>Konfigurations alternativ för TCP

| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_RESET_DISCONNECT | Definierad, inaktiverar återställnings bearbetningen under från koppling när det angivna tids gräns värdet har angetts som **NX_NO_WAIT**. |
| NX_DISABLE_TCP_INFO | Definierad, inaktiverar insamling av TCP-information. |
| NX_DISABLE_TCP_RX_CHECKSUM | Definierad, inaktiverar kontroll summa för mottagna TCP-paket. Detta är endast användbart i situationer där länk skiktet har tillförlitlig kontroll summa eller CRC-bearbetning, eller så kan gränssnitts driv rutinen verifiera TCP-kontrollsumma i maskin vara. |
| NX_DISABLE_TCP_TX_CHECKSUM | Definierad, inaktiverar kontroll summa för att skicka TCP-paket. Detta är endast användbart i situationer där den mottagande nätverks-noden har fått den mottagna TCP-kontrollsumma-logiken inaktive rad eller den underliggande nätverks driv rutinen kan generera TCP-kontrollsumma. |
| NX_ENABLE_TCP_KEEPALIVE | Definierad, aktiverar den valfria TCP keepalive-timern. Standardinställningarna är inte aktiverade. |
| NX_ENABLE_TCP_MSS_CHECKING | Definierad, aktiverar verifiering av lägsta peer-MSS innan en TCP-anslutning accepteras. Om du vill använda den här funktionen måste symbol **NX_ENABLE_TCP_MSS_MINIMUM** definieras. Som standard är det här alternativet inte aktiverat. |
NX_ENABLE_TCP_WINDOW_SCALING | Aktiverar alternativ för fönster skalning för TCP-program. Om det här alternativet har definierats förhandlas alternativet för fönster skalning under fasen TCP-anslutning och programmet kan ange en fönster storlek som är större än 64 kB. Standardinställningen är inte aktive rad (inte definierad). |
| NX_MAX_LISTEN_REQUESTS | Anger det maximala antalet Server lyssnings begär Anden. Standardvärdet är 10 och definieras i ***nx_api. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår. |
| NX_TCP_ACK_EVERY_N_PACKETS | Anger antalet TCP-paket som ska tas emot innan en ACK skickas. Obs! Om **NX_TCP_IMMEDIATE_ACK** har Aktiver ats men **NX_TCP_ACK_EVERY_N_PACKETS** inte är, anges värdet automatiskt till 1 för bakåtkompatibilitet. |
| NX_TCP_ACK_TIMER_RATE | Anger hur antalet system Tick (NX_IP_PERIODIC_RATE) delas för att beräkna timer-frekvensen för TCP-fördröjd ACK-bearbetning. Standardvärdet är 5, som representerar 200ms och definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _ *_nx_api. h_* *. |
| NX_TCP_ENABLE_KEEPALIVE | Har bytt namn till **NX_ENABLE_TCP_KEEPALIVE**. Även om det fortfarande stöds, uppmuntras nya ritningar att använda **NX_ENABLE_TCP_KEEPALIVE**. |
| NX_TCP_ENABLE_WINDOW_SCALING | Har bytt namn till **NX_ENABLE_TCP_WINDOW_SCALING**. Även om det fortfarande stöds, uppmuntras nya ritningar att använda **NX_ENABLE_TCP_WINDOW_SCALING**. |
| NX_TCP_FAST_TIMER_RATE | Anger hur antalet interna NetX-Tick (NX_IP_PERIODIC_RATE) delas för att beräkna den snabba TCP-tidsfrekvensen. Den snabba TCP-timern används för att driva olika TCP-tidstjänster, inklusive den fördröjda ACK-tiden. Standardvärdet är 10, som representerar 100 MS förutsatt att ThreadX-timern körs vid 10ms. Det här värdet definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _ *_nx_api. h_* *. |
| NX_TCP_IMMEDIATE_ACK | Definierad, aktiverar den valfria bearbetningen av TCP omedelbart ACK-svar. Att definiera den här symbolen motsvarar att definiera **NX_TCP_ACK_EVERY_N_PACKETS** som 1. |
| NX_TCP_KEEPALIVE_INITIAL | Anger antalet sekunder av inaktivitet innan keepalive-timern aktive ras. Standardvärdet är 7200, vilket motsvarar 2 timmar och definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _ *_nx_api. h_* *. |
| NX_TCP_KEEPALIVE_RETRIES | Anger hur många keepalive-återförsök som tillåts innan anslutningen anses vara bruten. Standardvärdet är 10, som representerar 10 återförsök och definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår. |
| NX_TCP_KEEPALIVE_RETRY | Anger antalet sekunder mellan återförsök för keepalive-timer under antagandet att den andra sidan av anslutningen inte svarar. Standardvärdet är 75, vilket motsvarar 75 sekunder mellan återförsök och definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår. |
| NX_TCP_MAX_OUT_OF_ORDER_PACKETS | Symbol som definierar det maximala antalet färdiga TCP-paket som kan behållas i kön för mottagning av TCP-socket. Den här symbolen kan användas för att begränsa antalet paket som har placerats i kö i TCP Receive-socketen, vilket förhindrar att modempoolen har. Som standard är den här symbolen inte definierad, så det finns ingen gräns för antalet paket som ska placeras i kö i TCP-socketen. |
| NX_TCP_MAXIMUM_RETRIES | Anger hur många försök till data överföring som tillåts innan anslutningen anses vara bruten. Standardvärdet är 10, som representerar 10 återförsök och definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _ *_nx_api. h_* *. |
| NX_TCP_MAXIMUM_TX_QUEUE | Anger det maximala djupet för TCP-överförings kön innan TCP-begäran om sändning har pausats eller avvisats. Standardvärdet är 20, vilket innebär att högst 20 paket kan finnas i överförings kön vid en specifik tidpunkt. Antecknings paket förblir i överförings kön tills en bekräftelse som täcker vissa eller alla paket data tas emot från den andra sidan av anslutningen. Den här konstanten definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan det inkluderar _ *_nx_api. h_* *. |
| X_TCP_MSS_CHECKING_ENABLED | Har bytt namn till **NX_ENABLE_TCP_MSS_CHECKING**. Även om det fortfarande stöds, uppmuntras nya ritningar att använda **NX_ENABLE_TCP_MSS_CHECKING**. |
| NX_TCP_MSS_MINIMUM | Symbol som definierar det minimala MSS-värdet NetX TCP-modulen accepterar. Den här funktionen aktive ras av **NX_ENABLE_TCP_MSS_CHECK** |
| NX_TCP_RETRY_SHIFT | Anger hur timeout-perioden för omsändning ändras mellan återförsök. Om det här värdet är 0, är den första timeoutn för omsändning detsamma som efterföljande timeout-Timeout. Om det här värdet är 1, är varje överföring i följd två gånger så lång. Om det här värdet är 2 är varje omsändnings-timeout fyra gånger så lång. Standardvärdet är 0 och definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan du inkluderar _ *_nx_api. h_* *. |
| NX_TCP_TRANSMIT_TIMER_RATE| Anger hur antalet system Tick **NX_IP_PERIODIC_RATE**) divideras för att beräkna timer-frekvensen för bearbetningen av återförsök i TCP-överföring. Standardvärdet är 1, vilket motsvarar 1 sekund och definieras i **_nx_tcp. h_*_. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan det inkluderar _*_nx_api. h_**. |

### <a name="udp-configuration-options"></a>Alternativ för UDP-konfiguration
| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_UDP_INFO | Definierad, inaktiverar insamling av UDP-information. |
| NX_DISABLE_UDP_RX_CHECKSUM | Definierad inaktiverar beräkningen av UDP-kontrollsumma på inkommande UDP-paket. Detta är användbart om nätverks gränssnittets driv rutin kan verifiera kontroll summa för UDP-huvud i maskin vara och programmet inte aktiverar logik för IP-fragmentering. |
| NX_DISABLE_UDP_TX_CHECKSUM | Definierad inaktiverar beräkningen av UDP-kontrollsumma på utgående UDP-paket. Detta är användbart om nätverks gränssnittets driv rutin kan beräkna kontroll summa för UDP-huvud och infoga värdet i IP-huvudet innan data överförs, och programmet aktiverar inte IP-fragmentering-logik. |

## <a name="netx-version-id"></a>NetX versions-ID

Den aktuella versionen av NetX är tillgänglig för både användaren och program varan under körning. Programmerare kan hämta NetX-versionen från filen **nx_port. h** . Dessutom innehåller den här filen en versions historik för motsvarande port. Program varan kan hämta NetX-versionen genom att undersöka den globala strängen **_nx_version_id** i **_nx_port. h_**.  

Program varan kan också hämta versions information från de konstanter som visas nedan, som definieras i ***nx_api. h**. *

Dessa konstanter identifierar den aktuella produkt versionen efter namn och produktens huvud-och del version.

```c
#define EL_PRODUCT_NETX

#define NETX_MAJOR_VERSION

#define NETX_MINOR_VERSION
```