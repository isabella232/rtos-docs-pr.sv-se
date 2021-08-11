---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX Duo
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av högpresterande nätverksstackar Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 32a9efaac3c85d415316fba2e9536cc40939f1f6debcbe3e2fa588de613a694d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788838"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX Duo

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av högpresterande nätverksstackar Azure RTOS NetX Duo, inklusive följande: 

## <a name="host-considerations"></a>Värdöverväganden

Inbäddad utveckling utförs vanligtvis på Windows- eller Linux-värddatorer (Unix). När programmet har kompilerats, länkats och den körbara filen har genererats på värden laddas den ned till målmaskinvaran för körning.

Vanligtvis görs målnedladdningen från felsökningsverktygets felsökningsverktyg. Efter nedladdningen ansvarar felsökningsprogrammet för att tillhandahålla målkörningskontroll (go, halt, brytpunkt osv.) samt åtkomst till minne och processorregister.

De flesta felsökningsverktyg kommunicerar med målmaskinvaran via OCD-anslutningar (On-Chip Debug), till exempel JTAG (IEEE 1149.1) och Bakgrundsfelsökningsläge (BDM). Felsökningsprogrammet kommunicerar också med målmaskinvaran via In-Circuit(ICE) anslutningar. Både OCD- och ICE-anslutningar ger robusta lösningar med minimalt intrång på målprogramvaran.

Precis som för resurser som används på värden levereras källkoden för NetX Duo i ASCII-format och kräver cirka 1 MB utrymme på värddatorns hårddisk.

## <a name="target-considerations"></a>Målöverväganden

NetX Duo kräver mellan 5 KByte och 45 Read-Only (ROM) på målet. Ytterligare 1 till 5 KByte av målets RAM-minne (Random Access Memory) krävs för NetX Duo-trådstacken och andra globala datastrukturer.

Dessutom kräver NetX Duo användning av två ThreadX-timerobjekt och ett ThreadX mutex-objekt. Dessa anläggningar används för periodiska bearbetningsbehov och trådskydd i NetX Duo-protokollstacken.

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS NetX Duo kan hämtas från vår offentliga källkodsdatabas på <https://github.com/azure-rtos/netxduo/> .

Följande är en lista över flera viktiga filer på lagringsplatsen:

**nx_api.h**  
C-rubrikfil som innehåller alla systemekvar lika med, datastrukturer och tjänstprototyper.

**nx_port.h** C-rubrikfil som innehåller alla utvecklingsverktyget och målspecifika datadefinitioner och strukturer. 

**demo_netx.c** C-fil som innehåller ett litet demoprogram.

**nx.a (eller nx.lib)**  
Binär version av NetX C-biblioteket som distribueras med standardpaketet.

## <a name="netx-duo-installation"></a>NetX Duo-installation

NetX Duo installeras genom att klona GitHub till din lokala dator. Följande är en vanlig syntax för att skapa en klon av NetX Duo-lagringsplatsen på datorn:

```c
    git clone https://github.com/azure-rtos/netxduo
```

Du kan också ladda ned en kopia av lagringsplatsen med hjälp av nedladdningsknappen GitHub på huvudsidan.

Du hittar också anvisningar för att skapa NetX Duo-biblioteket på startsidan för onlinedatabasen.

> [!IMPORTANT]
> *Programprogramvaran behöver åtkomst till NetX Duo-biblioteksfilen (vanligtvis **nx.a** eller **nx.lib**) och C innehåller filerna **nx_api.h och nx_port.h**. Detta åstadkoms antingen genom att ange lämplig sökväg för utvecklingsverktygen eller genom att kopiera dessa filer till programutvecklingsområdet.*

## <a name="using-netx-duo"></a>Använda NetX Duo

Det är enkelt att använda NetX Duo. I princip måste programkoden innehålla ***nx_api.h** _ under kompileringen och länka till NetX Duo-biblioteket _*_nx.a_*_ (eller _ *_nx.lib_*)*.

Följande är de fyra enkla steg som krävs för att skapa ett NetX Duo-program:

| Steg  | Description  |
|---|---|
|Steg &nbsp; 1: |Inkludera filen ***nx_api.h i*** alla programfiler som använder NetX Duo-tjänster eller datastrukturer.|
|Steg &nbsp; 2: |Initiera NetX Duo-systemet genom att anropa ***nx_system_initialize** _ från funktionen _ *_tx_application_define_** eller en programtråd.|
|Steg &nbsp; 3: |Skapa en IP-instans, aktivera Address Resolution Protocol (ARP) vid behov och eventuella sockets ***när nx_system_initialize*** anropas.|
|Steg &nbsp; 4: |Kompilera programkällan och länka till NetX Duo-körningsbiblioteket ***nx.a** _ (eller _*_nx.lib_**). Den resulterande avbildningen kan laddas ned till målet och köras!|

## <a name="troubleshooting"></a>Felsökning

Varje NetX Duo-port levereras med en eller flera demonstrationer som körs i ett faktiskt nätverk eller via en simulerad nätverksdrivrutin. Det är alltid en bra idé att få igång demonstrationssystemet först.

Om demonstrationssystemet inte körs korrekt utför du följande åtgärder för att begränsa problemet:

1. Fastställ hur mycket av demonstrationen som körs.
2. Öka stackstorlekarna i alla nya programtrådar.
3. Kompilera om NetX Duo-biblioteket med lämpliga felsökningsalternativ som anges i avsnittet konfigurationsalternativ.
4. Granska NX_IP för att se om paket skickas eller tas emot.
5. Granska standardpaketpoolen för att se om det finns tillgängliga paket.
6. Se till att nätverksdrivrutinen tillhandahåller ARP- och IP-paket med sina huvuden på 4 byte-gränser för program som kräver IPv4- eller IPv6-anslutning.
7. Kringgå de senaste ändringarna tillfälligt för att se om problemet försvinner eller ändras. Sådan information bör vara användbar för Microsofts supporttekniker.

Följ procedurerna som beskrivs i "What We Need From You" på sidan 12 för att skicka den information som samlas in från felsökningsstegen.

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ när du skapar NetX Duo-biblioteket och programmet med NetX Duo. Konfigurationsalternativen kan definieras i programkällan, på kommandoraden eller i indelningsfilen ***nx_user.h,*** om inget annat anges.

> [!NOTE]
> *Alternativ som **definieras nx_user.h** tillämpas* endast om programmet och NetX Duo-biblioteket har skapats med **NX_INCLUDE_USER_DEFINE_FILE** definierats.*

I följande avsnitt visas de konfigurationsalternativ som är tillgängliga i NetX Duo. Allmänna alternativ som gäller för både IPv4 och IPv6 visas först, följt av IPv6-specifika alternativ.

### <a name="system-configuration-options"></a>Systemkonfigurationsalternativ

| Alternativ  | Beskrivning  |
|---|---|
| NX_ASSERT_FAIL    | Symbol som definierar den felsökningssats som ska användas när en kontroll misslyckas.                               |
| NX_DEBUG           | Definierad aktiverar valfri felsökningsinformation för utskrift som är tillgänglig från RAM Ethernet-nätverksdrivrutinen. |
| NX_DEBUG_PACKET   | Definierad aktiverar valfria dumpning av felsökningspaket som är tillgängliga i RAM Ethernet-nätverksdrivrutinen.      |
| NX_DISABLE_ASSERT | Definierad, inaktiverar ASSERT-kontroller i källkoden. Som standard definieras inte det här alternativet.            |
|NX_DISABLE_ERROR_CHECKING | Definieras, tar bort det grundläggande API:et för NetX Duo-felkontroll och förbättrar prestandan. API-returkoder som inte påverkas av inaktivering av felkontroll visas i fetstil i API-definitionen. Den här definierar används vanligtvis när programmet har felsökts tillräckligt och dess användning förbättrar prestanda och minskar kodstorleken.|
|NX_DRIVER_DEFERRED_PROCESSING | Definierad aktiverar uppskjuten pakethantering för nätverksdrivrutiner. Detta gör att nätverksdrivrutinen kan placera ett paket på IP-instansen och få den verkliga bearbetningsrutinen anropad från den interna IP-hjälptråden för NetX Duo.|
|NX_DUAL_PACKET_POOL_ENABLE | Har bytt namn till ***NX_ENABLE_DUAL_PACKET_POOL** _. Även om det fortfarande stöds, uppmuntras nya designer att använda _*_NX_ENABLE_DUAL_PACKET_POOL_**.|
|NX_ENABLE_DUAL_PACKET_POOL | Definierad gör att stacken kan använda två paketpooler, en med stor nyttolaststorlek och en med mindre nyttolaststorlek. Det här alternativet är inte aktiverat som standard.|
|NX_ENABLE_EXTENDED_NOTIFY_SUPPORT| Definierad, aktiverar fler återanrops-hookar i stacken. Dessa återanropsfunktioner används av BSD-omslutningsskiktet. Som standard definieras inte det här alternativet.|
|NX_ENABLE_INTERFACE_CAPABILITY| Definierad gör att gränssnittets enhetsdrivrutin kan ange extra kapacitetsinformation, till exempel kontrollsumma vid avläsning. Som standard definieras inte det här alternativet.|
|NX_ENABLE_SOURCE_ADDRESS_CHECK| Definierad, gör att källadressen för inkommande paket kan kontrolleras. Som standard är det här alternativet inaktiverat.|
| NX_IPSEC_ENABLE  | Definierad, aktiverar NetX Duo-biblioteket för att stödja IPsec-åtgärder. Den här funktionen kräver den valfria NetX Duo IPsec-modulen. Den här funktionen är inte aktiverad som standard.            |
| NX_LITTLE_ENDIAN | Definierar utför nödvändig byteväxling på little endian för att säkerställa att protokollhuvudena är i rätt big endian format. Observera att standardinställningen vanligtvis är i ***nx_port.h***.|
|NX_MAX_PHYSICAL_INTERFACES | Anger det totala antalet fysiska nätverksgränssnitt på enheten. Standardvärdet är 1 och definieras i ***nx_api.h***; en enhet måste ha minst ett fysiskt gränssnitt. Observera att detta inte inkluderar loopback-gränssnittet.|
| NX_NAT_ENABLE | NetX Duo har definierats med NAT-processen. Som standard definieras inte det här alternativet.|
| NX_PHYSICAL_HEADER  | Anger storleken i byte för den fysiska ramens sidhuvud. Standardvärdet är 16 (baserat på en typisk Ethernet-ram på 14 byte justerad till 32-bitars gräns) och definieras i ***nx_api.h** _. Programmet kan åsidosätta standardvärdet genom att definiera _*_värdet innan nx_api.h_*_ inkluderas, till exempel i _ *_nx_user.h_*.* |
| NX_PHYSICAL_TRAILER | Anger storleken i byte för det fysiska paketet och används vanligtvis för att reservera lagringsutrymme för sådant som Ethernet-CPC:er osv. Standardvärdet är 4 och definieras i ***nx_api.h***.|

### <a name="arp-configuration-options"></a>Konfigurationsalternativ för ARP

| Alternativ  | Beskrivning  |
|---|---|
|NX_ARP_DEFEND_BY_REPLY | Definierad gör att NetX Duo kan skydda sin IP-adress genom att skicka ett ARP-svar.|
|NX_ARP_DEFEND_INTERVAL| Definierar intervallet, i sekunder, som ARP-modulen skickar ut nästa försvarspaket som svar på ett inkommande ARP-meddelande som anger en adress i konflikt.|
|NX_ARP_DISABLE_AUTO_ARP_ENTRY|  Har bytt namn till ***NX_DISABLE_ARP_AUTO_ENTRY** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_DISABLE_ARP_AUTO_ENTRY_**.|
|NX_ARP_EXPIRATION_RATE| Anger antalet sekunder som ARP-poster förblir giltiga. Standardvärdet noll inaktiverar förfallodatum eller föråldring av ARP-poster och definieras i ***nx_api.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|
|NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | Har bytt namn till ***NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION_**.|
|NX_ARP_MAX_QUEUE_DEPTH | Anger det maximala antalet paket som kan köas i väntan på ett ARP-svar. Standardvärdet är 4 och definieras i ***nx_api.h***.|
|NX_ARP_MAXIMUM_RETRIES | Anger det maximala antalet ARP-återförsök som görs utan ett ARP-svar. Standardvärdet är 18 och definieras i ***nx_api.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|
|NX_ARP_UPDATE_RATE | Anger antalet sekunder mellan ARP-återförsök. Standardvärdet är 10, vilket motsvarar 10 sekunder och definieras i ***nx_api.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|
|NX_DISABLE_ARP_AUTO_ENTRY | Definierad inaktiverar att ange information om ARP-begäran i ARP-cachen.|
|NX_DISABLE_ARP_INFO | Definierad, inaktiverar ARP-informationsinsamling.|
|NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION| Definierad, tillåter att ARP anropar en återanrops meddela-funktion vid identifiering av MAC-adressen uppdateras.|

### <a name="icmp-configuration-options"></a>Konfigurationsalternativ för ICMP

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_ICMP_INFO| Definierad, inaktiverar ICMP-informationsinsamling.|
|NX_DISABLE_ICMP_RX_CHECKSUM| Definierad inaktiverar beräkning av både ICMPv4- och ICMPv6-kontrollsumma vid mottagna ICMP-paket. Det här alternativet är användbart när nätverksgränssnittsdrivrutinen kan verifiera kontrollsumman för ICMPv4 och ICMPv6 och programmet inte använder funktionen IP-fragmentering eller IPsec-funktionen. Som standard definieras inte det här alternativet.|
|NX_DISABLE_ICMP_TX_CHECKSUM | Definierad inaktiverar beräkning av både ICMPv4- och ICMPv6-kontrollsumma vid överförda ICMP-paket. Det här alternativet är användbart när nätverksgränssnittsdrivrutinen kan beräkna ICMPv4- och ICMPv6-kontrollsumman,
och programmet använder inte funktionen IP-fragmentering eller IPsec. Som standard definieras inte det här alternativet.|
|NX_DISABLE_ICMPV4_ERROR_MESSAGE | NetX Duo skickar inte ICMPv4-felmeddelanden som svar på feltillstånd, till exempel felaktigt formaterat IPv4-huvud. Som standard definieras inte det här alternativet.|
|NX_DISABLE_ICMPV4_RX_CHECKSUM | Definierad inaktiverar ICMPv4-beräkning av kontrollsumma vid mottagna ICMP-paket. Det här alternativet definieras automatiskt ***NX_DISABLE_ICMP_RX_CHECKSUM definieras.*** Som standard definieras inte det här alternativet.|
|NX_DISABLE_ICMPv4_RX_CHECKSUM | Har bytt namn till ***NX_DISABLE_ICMPV4_RX_CHECKSUM** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_DISABLE_ICMPV4_RX_CHECKSUM_**.|
|NX_DISABLE_ICMPV4_TX_CHECKSUM | Definierad inaktiverar ICMPv4-kontrollsummaberäkning på överförda ICMP-paket. Det här alternativet definieras automatiskt ***NX_DISABLE_ICMP_TX_CHECKSUM definieras.*** Som standard definieras inte det här alternativet.|
|NX_DISABLE_ICMPv4_TX_CHECKSUM | Har bytt namn till ***NX_DISABLE_ICMPV4_TX_CHECKSUM** _.</br>Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_DISABLE_ICMPV4_TX_CHECKSUM_**.|
|NX_ENABLE_ICMP_ADDRESS_CHECK | Måladressen för ICMP-paketet är markerad. Standardvärdet är inaktiverad. En ICMP Echo-begäran som är avsedd för en IP-sändning eller IP-multicast-adress ignoreras tyst.|

### <a name="igmp-configuration-options"></a>Konfigurationsalternativ för IGMP

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_IGMP_INFO | Definierad, inaktiverar IGMP-informationsinsamling.|
|NX_DISABLE_IGMPV2 | Definierad, inaktiverar IGMPv2-stöd och NetX Duo stöder endast IGMPv1. Som standard är det här alternativet inte inställt och definieras ***i nx_api.h***.|
|NX_MAX_MULTICAST_GROUPS | Anger det maximala antalet multicast-grupper som kan vara ansluten. Standardvärdet är 7 och definieras i ***nx_api.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|

### <a name="ip-configuration-options"></a>IP-konfigurationsalternativ

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_FRAGMENTATION | Definierad, inaktiverar både IPv4- och IPv6-fragmentering och sätter ihop logiken.|
| NX_DISABLE_IPV4     | Definierad, inaktiverar IPv4-funktioner. Det här alternativet kan endast användas för att skapa NetX Duo till suupport IPv6. Som standard definieras inte det här alternativet. |
| NX_DISABLE_IP_INFO | Definierad, inaktiverar IP-informationsinsamling.|
|NX_DISABLE_IP_RX_CHECKSUM | Definierad inaktiverar logik för kontrollsumma på mottagna IPv4-paket. Detta är användbart om nätverksenheten kan verifiera IPv4-kontrollsumman och programmet inte förväntar sig att använda IP-fragmentering eller IPsec.|
|NX_DISABLE_IP_TX_CHECKSUM | Definierad inaktiverar logik för kontrollsumma på IPv4-paket som skickas. Detta är användbart i situationer där den underliggande nätverksenheten kan generera kontrollsumman för IPv4-huvudet och programmet inte förväntar sig att använda IP-fragmentering eller IPsec.|
|NX_DISABLE_LOOPBACK_INTERFACE | Definierad inaktiverar NetX Duo-stöd för loopback-gränssnittet.|
|NX_DISABLE_RX_SIZE_CHECKING | Definierad inaktiverar storlekskontrollen för mottagna paket.|
|NX_ENABLE_IP_RAW_PACKET_FILTER | Definierad aktiverar filterfunktionen IP-rådata för mottagning av paket. Program som kräver mer kontroll över typen av råa IP-paket som ska tas emot kan använda den här funktionen. Filterfunktionen IP-rådatapaket stöder även raw socket i BSD-kompatibilitetslagret. Som standard definieras inte det här alternativet.|
|NX_ENABLE_IP_STATIC_ROUTING | Definierad aktiverar statisk IPv4-routning där en måladress kan tilldelas en specifik nexthop-adress. Statisk IPv4-routning är inaktiverat som standard.|
|NX_FRAGMENT_IMMEDIATE_ASSEMBLY | Definierad gör att IPv4- och IPv6-logiken kan köras direkt efter att ett IP-fragment har mottagits. Som standard definieras inte det här alternativet.|
|NX_IP_MAX_REASSEMBLY_TIME | Symbol som styr den längsta tid som tillåts för att sätta ihop IPv4-fragment och IPv6-fragment på ett annat sätt. Observera att värdet som definieras här skriver över både ***NX_IPV4_MAX_REASSEMBLY_TIME** _ och _*_NX_IPV6_MAX_REASSEMBLY_TIME_**.|
|NX_IP_PERIODIC_RATE | Definierad anger antalet ThreadX-timer tick på en sekund. Standardvärdet härleds från ThreadX-symbolen ***TX_TIMER_TICKS_PER_SECOND,** _ som som standard är inställt på 100 (10 ms timer). Programmen bör vara försiktig när du ändrar det här värdet, eftersom resten av NetX Duo-modulerna härleder tidsinformationen från _ *_NX_IP_PERIODIC_RATE_.**|
|NX_IP_RAW_MAX_QUEUE_DEPTH | Symbol som styr antalet råa IP-paket kan köas i kön för råpakets mottagning. Som standard är värdet inställt på 20.| 
|NX_IP_ROUTING_TABLE_SIZE | Definieras, anger det maximala antalet poster i den statiska IPv4-routningstabellen, som är en lista över ett utgående gränssnitt och nexthop-adresser för en viss måladress. Standardvärdet är 8 och definieras i ***nx_api.h.** _ Den här symbolen används bara om _ *_NX_ENABLE_IP_STATIC_ROUTING_** har definierats.|
|NX_IPV4_MAX_REASSEMBLY_TIME | Symbol som styr den längsta tid som tillåts för att sätta ihop IPv4-fragment på ett annat sätt. Observera att värdet som definieras NX_IP_MAX_REASSEMBLY_TIME skriver över det här värdet.|

### <a name="packet-configuration-options"></a>Alternativ för paketkonfiguration

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_PACKET_CHAIN | Definierad inaktiverar logiken för paketkedjan. Som standard definieras inte detta.|
|NX_DISABLE_PACKET_INFO | Definierad, inaktiverar insamling av paketpoolsinformation.|
|NX_ENABLE_LOW_WATERMARK | Definierad aktiverar funktionen För låg vattenstämpel i NetX Duo-paketpoolen. Programmet anger lågt vattenstämpelvärde. Vid mottagning av TCP-paket, om paketpoolens låga vattenstämpel nås, ignorerar NetX Duo paketet tyst genom att släppa det, vilket förhindrar att paketpoolen blir utsvulten. Den här funktionen är inte aktiverad som standard.|
|NX_ENABLE_PACKET_DEBUG_INFO | Definierad loggar paketfelsökningsinformation.|
|NX_PACKET_ALIGNMENT | Definierad anger justeringskrav i byte för startadressen för paketets nyttolastområde. Det här alternativet är inaktuellt ***NX_PACKET_HEADER_PAD** _ och _*_NX_PACKET_HEADER_PAD_SIZE_**. Som standard definieras det här alternativet som 4, vilket gör startadressen för nyttolastens område 4 byte justerad.|
|NX_PACKET_HEADER_PAD | Definierad aktiverar utfyllnad mot slutet av NX_PACKET kontrollblocket. Antalet ULONG-ord som ska ersättas definieras av ***NX_PACKET_HEADER_PAD_SIZE** _. Observera att det här alternativet avskrivs av _*_NX_PACKET_ALIGNMENT_**.|
|NX_PACKET_HEADER_PAD_SIZE | Anger antalet ULONG-ord som ska NX_PACKET strukturen, vilket gör att paketnyttolasten kan börja vid önskad justering. Den här funktionen är användbar när du tar emot buffertbeskrivningar direkt till NX_PACKET-nyttolasten och nätverksgränssnittet tar emot logiken eller cacheåtgärdslogiken förväntar sig att buffertens startadress uppfyller vissa justeringskrav. Det här värdet blir endast giltigt när ***NX_PACKET_HEADER_PAD** _ har definierats. Observera att det här alternativet är inaktuellt av _*_NX_PACKET_ALIGNMENT_**.|

### <a name="rarp-configuration-options"></a>RARP-konfigurationsalternativ

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_RARP_INFO | Definierad, inaktiverar RARP-informationsinsamling.|

### <a name="tcp-configuration-options"></a>TCP-konfigurationsalternativ

| Alternativ | Beskrivning |
|---|---|
|NX_DISABLE_RESET_DISCONNECT | Definierad inaktiverar återställningsbearbetningen under frånkoppling när det angivna tidsgränsvärdet anges som ***NX_NO_WAIT***.|
|NX_DISABLE_TCP_INFO | Definierad, inaktiverar TCP-informationsinsamling.|
|NX_DISABLE_TCP_RX_CHECKSUM | Definierad, inaktiverar logik för kontrollsumma på mottagna TCP-paket. Detta är bara användbart i situationer där länklagret har tillförlitlig kontrollsumma eller CRC-bearbetning, eller gränssnittsdrivrutinen kan verifiera TCP-kontrollsumman i maskinvaran och programmet inte använder IPsec.|
|NX_DISABLE_TCP_TX_CHECKSUM | Definierad, inaktiverar logik för kontrollsumma för att skicka TCP-paket. Detta är bara användbart i situationer där den mottagande nätverksnoden har tagit emot TCP-kontrollsummalogik inaktiverad eller om den underliggande nätverksdrivrutinen kan generera TCP-kontrollsumman och programmet inte använder IPsec.|
|NX_ENABLE_TCP_KEEPALIVE | Definierad aktiverar den valfria TCP-keepalive-timern. Standardinställningarna är inte aktiverade.|
|NX_ENABLE_TCP_MSS_CHECK | Definierad aktiverar verifiering av minsta peer MSS innan du godkänner en TCP-anslutning. Om du vill använda den här ***funktionen måste NX_ENABLE_TCP_MSS_MINIMUM*** definieras. Det här alternativet är inte aktiverat som standard.|
|NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY| Definierad, tillåter att programmet installerar en återanropsfunktion som anropas när TCP-överföringsködjupet inte längre har det högsta värdet. Det här återanropet fungerar som en indikation på att TCP-socketen är redo att överföra mer data. Det här alternativet är inte aktiverat som standard.|
|NX_ENABLE_TCP_WINDOW_SCALING | Aktiverar alternativet för fönsterskalning för TCP-program. Om alternativet för fönsterskalning definieras förhandlas det under TCP-anslutningsfasen och programmet kan ange en fönsterstorlek som är större än 64 000. Standardinställningen är inte aktiverad (inte definierad).|
|NX_MAX_LISTEN_REQUESTS | Anger det maximala antalet serverlyssnandebegäranden. Standardvärdet är 10 och definieras i ***nx_api.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|
|NX_TCP_ACK_EVERY_N_PACKETS | Anger antalet TCP-paket som ska tas emot innan en ACK skickas. Observera att om ***NX_TCP_IMMEDIATE_ACK** _ är aktiverat men _ *_NX_TCP_ACK_EVERY_N_PACKETS_** inte är det här värdet automatiskt inställt på 1 för bakåtkompatibilitet.|
|NX_TCP_ACK_TIMER_RATE | Anger hur antalet system tick (NX_IP_PERIODIC_RATE) divideras för att beräkna timerhastigheten för DEN TCP-fördröjda ACK-bearbetningen. Standardvärdet är 5, vilket representerar 200 ms och definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|
|NX_TCP_ENABLE_KEEPALIVE | Har bytt namn till ***NX_ENABLE_TCP_KEEPALIVE** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_ENABLE_TCP_KEEPALIVE_**.|
|NX_TCP_ENABLE_MSS_CHECK | Har bytt namn till ***NX_ENABLE_TCP_MSS_CHECK** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _ *_NX_ENABLE_TCP_MSS_CHECK._**|
|NX_TCP_ENABLE_WINDOW_SCALING | Har bytt namn till ***NX_ENABLE_TCP_WINDOW_SCALING** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_ENABLE_TCP_WINDOW_SCALING_**.|
|NX_TCP_FAST_TIMER_RATE | Anger hur antalet interna NetX Duo-tick (NX_IP_PERIODIC_RATE) delas upp för att beräkna den snabba TCP-timerhastigheten. Den snabba TCP-timern används för att driva de olika TCP-timers, inklusive den fördröjda ACK-timern. Standardvärdet är 10, vilket motsvarar 100 ms förutsatt att ThreadX-timern körs på 10 ms. Det här värdet definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|
|NX_TCP_IMMEDIATE_ACK| Definierad aktiverar valfri tcp omedelbar ACK-svarsbearbetning. Att definiera den här symbolen motsvarar att  ***definiera NX_TCP_ACK_EVERY_N_PACKETS*** till 1.|
|NX_TCP_KEEPALIVE_INITIAL | Anger antalet sekunder av inaktivitet innan keepalive-timern aktiveras. Standardvärdet är 7200, vilket motsvarar 2 timmar och definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|
|NX_TCP_KEEPALIVE_RETRIES | Anger hur många keepalive-återförsök som tillåts innan anslutningen anses vara bruten. Standardvärdet är 10, vilket representerar 10 återförsök och definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|
|NX_TCP_KEEPALIVE_RETRY | Anger antalet sekunder mellan återförsök för keepalive-timern förutsatt att den andra sidan av anslutningen inte svarar. Standardvärdet är 75, vilket motsvarar 75 sekunder mellan återförsöken och definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|
|NX_TCP_MAX_OUT_OF_ORDER_PACKETS | Symbol som definierar det maximala antalet out-of-order TCP-paket kan behållas i TCP socket-mottagningskön. Den här symbolen kan användas för att begränsa antalet paket i kö i TCP-mottagningssocketen, vilket förhindrar att paketpoolen blir utsvulten. Som standard definieras inte den här symbolen, vilket innebär att det inte finns någon gräns för antalet out-of-order-paket som köas i TCP-socketen.|
|NX_TCP_MAXIMUM_RETRIES | Anger hur många återförsök för dataöverföring som tillåts innan anslutningen anses vara bruten. Standardvärdet är 10, vilket representerar 10 återförsök och definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|
|NX_TCP_MAXIMUM_RX_QUEUE | Symbol som definierar den maximala mottagningskön för TCP-sockets. Den här funktionen aktiveras av ***NX_ENABLE_LOW_WATERMARK***.|
|NX_TCP_MAXIMUM_TX_QUEUE | Anger det maximala djupet för TCP-överföringskön innan TCP-sändningsbegäranden pausas eller avvisas. Standardvärdet är 20, vilket innebär att högst 20 paket kan finnas i överföringskön vid en given tidpunkt. Observera att paketen finns kvar i överföringskön tills en ACK som täcker vissa eller alla paketdata tas emot från den andra sidan av anslutningen. Den här konstanten definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|
|NX_TCP_MSS_MINIMUM | Symbol som definierar det minimala MSS-värdet som NetX Duo TCP-modulen accepterar. Den här funktionen aktiveras av ***NX_ENABLE_TCP_MSS_CHECK***.|
|NX_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_ENABLE | Har bytt namn till ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_**.|
|NX_TCP_RETRY_SHIFT | Anger hur tidsgränsen för återöverföring ändras mellan återförsök. Om det här värdet är 0 är den första tidsgränsen för återöverföring samma som efterföljande tidsgränser för återöverföring. Om det här värdet är 1 blir varje efterföljande återöverföring dubbelt så lång. Om det här värdet är 2 är varje efterföljande tidsgräns för återöverföring fyra gånger så lång. Standardvärdet är 0 och definieras i ***nx_tcp.h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|
|NX_TCP_TRANSMIT_TIMER_RATE | Anger hur antalet system tick **(*** NX_IP_PERIODIC_RATE _) divideras för att beräkna timerhastigheten för BEARBETNING av TCP-överföringsförsök. Standardvärdet är 1, vilket representerar 1 sekund och definieras i _*_nx_tcp.h_*_. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api.h_** inkluderas.|

### <a name="udp-configuration-options"></a>UDP-konfigurationsalternativ

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_UDP_INFO | Definierad, inaktiverar UDP-informationsinsamling.|
|NX_DISABLE_UDP_RX_CHECKSUM | Definierad inaktiverar UDP-beräkningen av kontrollsumma för inkommande UDP-paket. Detta är användbart om nätverksgränssnittsdrivrutinen kan verifiera kontrollsumman för UDP-huvudet i maskinvaran och programmet inte aktiverar IPsec- eller IP-fragmenteringslogik.|
|NX_DISABLE_UDP_TX_CHECKSUM | Definierad inaktiverar UDP-beräkningen av kontrollsumma för utgående UDP-paket. Detta är användbart om nätverksgränssnittsdrivrutinen kan beräkna kontrollsumman för UDP-huvudet och infoga värdet i IP-huvudet innan data överförs, och programmet inte aktiverar IPsec- eller IP-fragmenteringslogik.|

### <a name="ipv6-options"></a>IPv6-alternativ  

| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_IPV6 | Inaktiverar IPv6-funktioner när NetX Duo-biblioteket har skapats. För program som inte behöver IPv6 undviker detta att dra in kod och ytterligare lagringsutrymme som krävs för att stödja IPv6.|
|NX_DISABLE_IPV6_PATH_MTU_DISCOVERY | Definierad inaktiverar sökvägen MTU-identifiering, som används för att fastställa det maximala antalet MTU:er i sökvägen till ett mål i NetX Duo-värdmåltabellen. Detta gör att NetX Duo-värden kan skicka största möjliga paket som inte kräver fragmentering. Som standard definieras det här alternativet (sökvägen MTU är inaktiverad).|
|NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY | Definierad, tillåter att en återanropsfunktion anropas när IPv6-adressen ändras. Det här alternativet är inte aktiverat som standard.|
|NX_ENABLE_IPV6_MULTICAST | Definierad aktiverar funktionen IPv6 multicast join/leave. Det här alternativet är inte aktiverat som standard.|
|NX_ENABLE_IPV6_PATH_MTU_DISCOVERY | Definierad aktiverar IPv6-sökvägens MTU-identifieringsfunktion. Det här alternativet är inte aktiverat som standard.|
|NX_IPV6_ADDRESS_CHANGE_NOTIFY_ENABLE | Har bytt namn till ***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY_**.|
|NX_IPV6_DEFAULT_ROUTER_TABLE_SIZE | Anger antalet poster i IPv6-routningstabellen. Minst onS-post krävs för standardrouter. Standardvärdet ***nx_api.h*** är 8.|
|NX_IPV6_DESTINATION_TABLE_SIZE | Anger antalet poster i IPv6-måltabellen. Då lagras information om nästa hoppadresser för IPv6-adresser. Standardvärdet ***nx_api.h*** är 8.|
|NX_IPV6_MAX_REASSEMBLY_TIME | Symbol som styr den längsta tid som tillåts för att sätta ihop IPv6-fragmentet på ett annat sätt.|
|NX_IPV6_MULTICAST_ENABLE | Har bytt namn till ***NX_ENABLE_IPV6_MULTICAST** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_ENABLE_IPV6_MULTICAST_**.|
|NX_IPV6_PREFIX_LIST_TABLE_SIZE | Anger storleken på prefixtabellen. Prefixinformationen hämtas från routerannonseringar och ingår i IPv6-adresskonfigurationen. Standardvärdet ***nx_api.h*** är 8.|
|NX_IPV6_STATELESS_AUTOCONFIG_CONTROL | Definierad gör att NetX Duo kan inaktivera funktionen för automatisk konfiguration av tillståndslösa adresser. Det här alternativet är inte aktiverat som standard.|
|NX_MAX_IPV6_ADDRESSES | Anger antalet poster i IPv6-adresspoolen. Under gränssnittskonfigurationen använder NetX Duo IPv6-poster från poolen. Standardvärdet är (NX_MAX_PHYSICAL_INTERFACES 3) så att varje gränssnitt har minst en \* lokal länkadress och två globala adresser. Observera att alla gränssnitt delar IPv6-adresspoolen.|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | Anger väntetiden i timern tick för att återställa sökvägens MTU för ett specifikt mål i måltabellen. Om ***NX_DISABLE_IPV6_PATH_MTU_DISCOVERY*** definieras har definitionen av den här symbolen ingen effekt.|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | Symbol som anger väntetiden (i sekunder) för att återställa sökvägens MTU-värde för en måltabellpost. Det är endast giltigt ***om NX_ENABLE_IPV6_PATH_MTU_DISCOVERY*** har definierats. Som standard är det här värdet inställt på 600 (sekunder).|

### <a name="neighbor-cache-configuration-options"></a>Konfigurationsalternativ för granncache

| Alternativ  | Beskrivning  |
|---|---|
|NX_DELAY_FIRST_PROBE_TIME | Anger fördröjningen i sekunder innan den första begäran skickas ut för en cachepost i tillståndet STALE. Standardvärdet ***nx_nd_cache.h*** är 5.|
|NX_DISABLE_IPV6_DAD | Definierad inaktiverar det här alternativet DUPlicerad adressidentifiering (PV) under IPv6-adresstilldelning. Adresser anges antingen genom manuell konfiguration eller via tillståndslös automatisk adresskonfiguration.|
|NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES | Det här alternativet förhindrar att NetX Duo tar bort äldre cachetabellposter innan tidsgränsen går ut för att göra plats för nya poster när tabellen är full. Statiska poster och routerposter rensas aldrig.|
|NX_IPV6_DAD_TRANSMITS | Anger antalet meddelanden om granne-begäran som ska skickas innan NetX Duo markerar en gränssnittsadress som giltig. Om ***NX_DISABLE_IPV6_DAD** _ har definierats (DISABLED inaktiverat) har det här alternativet ingen effekt. Alternativt kan ett värde på noll (0) stänga av KANT, men lämnar FUNKTIONEN KANT i NetX Duo. Standardvärdet är _3 och definieras i_ _* nx_api.h**.|
|NX_IPV6_DISABLE_PURGE_UNUSED_CACHE_ENTRIES | Har bytt namn till ***NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES** _. Även om det fortfarande stöds, uppmuntras nya designer att använda _*_NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES_**.|
|NX_IPV6_NEIGHBOR_CACHE_SIZE | Anger antalet poster i IPv6 Neighbor Cache-tabellen. Standardvärdet nx_nd_cache 16 i ***nx_nd_cache.h.***|
|NX_MAX_MULTICAST_SOLICIT | Anger antalet angränsande begärda meddelanden NetX Duo överför som en del av IPv6 Neighbor Discovery-protokollet när mappning mellan IPv6-adress och MAC-adress krävs. Standardvärdet är 3 som definieras i ***nx_nd_cache.h.***|
|NX_MAX_UNICAST_SOLICIT | Anger antalet meddelanden om granne-begäran som NetX Duo överför för att fastställa en specifik grannes nåbarhet. Standardvärdet är 3 som definieras i ***nx_nd_cache.h.***|
|NX_ND_MAX_QUEUE_DEPTH | Symbol som definierar det maximala antalet paket som köas för att ND-cachen ska matchas. Som standard är den här symbolen inställd på 4.|
|NX_REACHABLE_TIME | Anger time out i sekunder för att en cachepost ska finnas i reachable-tillstånd utan att paket tas emot från cachens IPv6-måladress. Standardvärdet ***nx_nd_cache i nx_nd_cache.h*** 30.|
|NX_RETRANS_TIMER  | Anger i millisekunder längden på fördröjningen mellan begärda paket som skickas av NetX Duo. Standardvärdet nx_nd_cache 1 000, definieras i ***nx_nd_cache.h.***|
| NXDUO_DISABLE_DAD | Har bytt namn till ***NX_DISABLE_IPV6_DAD** _. Även om det fortfarande stöds, uppmuntras nya designer att använda _*_NX_DISABLE_IPV6_DAD_**.|
|NXDUO_DUP_ADDR_DETECT_TRANSMITS | Har bytt namn till ***NX_IPV6_DAD_TRANSMITS** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_IPV6_DAD_TRANSMITS_**.|

### <a name="miscellaneous-icmpv6-configuration-options"></a>Diverse konfigurationsalternativ för ICMPv6

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_ICMPV6_ERROR_MESSAGE | Definierad, inaktiverar NetX Duo från att skicka ett ICMPv6-felmeddelande som svar på ett problempaket (t.ex. felaktigt formaterad rubrik eller pakethuvudtyp är inaktuell) som tagits emot från en annan värd.|
|NX_DISABLE_ICMPV6_REDIRECT_PROCESS | Definierad, inaktiverar bearbetning av ICMPv6-omdirigeringspaket. NetX Duo bearbetar som standard omdirigeringsmeddelanden och uppdaterar måltabellen med nästa hopp-IP-adressinformation.|
|NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS | Definierad inaktiverar NetX Duo från att bearbeta information som tas emot i IPv6-routerannonseringspaket.|
|NX_DISABLE_ICMPV6_ROUTER_SOLICITATION | Definierad, inaktiverar NetX Duo från att skicka IPv6-router begärda meddelanden med jämna mellanrum till routern.|
|NX_DISABLE_ICMPV6_RX_CHECKSUM | Definierad, inaktiverar beräkning av kontrollsumma för ICMPv6 på mottagna ICMP-paket.|
|NX_DISABLE_ICMPv6_RX_CHECKSUM | Har bytt namn till ***NX_DISABLE_ICMPV6_RX_CHECKSUM** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_DISABLE_CMPV6_RX_CHECKSUM_**.|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | Definierar, inaktiverar och ICMPv6-beräkning av kontrollsumma vid överförda ICMP-paket.|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | Har bytt namn till ***NX_DISABLE_ICMPV6_TX_CHECKSUM** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_DISABLE_ICMPV6_TX_CHECKSUM_**.|
|NX_ICMPV6_MAX_RTR_SOLICITATIONS | Definiera det maximala antalet routerinrop som en värd skickar tills ett routersvar tas emot. Om inget svar tas emot drar värden slutsatsen att det inte finns någon router. Standardvärdet är 3.|
|NX_ICMPV6_RTR_SOLICITATION_DELAY | Anger den maximala fördröjningen för den inledande router-begäran i sekunder.|
|NX_ICMPV6_RTR_SOLICITATION_INTERVAL | Anger intervallet mellan två meddelanden om router-begäran. Standardvärdet är 4.|
|NXDUO_DESTINATION_TABLE_SIZE | Har bytt namn till ***NX_IPV6_DESTINATION_TABLE_SIZE** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_IPV6_DESTINATION_TABLE_SIZE_**.|
|NXDUO_DISABLE_ICMPV6_ERROR_MESSAGE | Har bytt namn till ***NX_DISABLE_ICMPV6_ERROR_MESSAGE** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_DISABLE_ICMPV6_ERROR_MESSAGE_**.|
|NXDUO_DISABLE_ICMPV6_REDIRECT_PROCESS | Har bytt namn till ***NX_DISABLE_ICMPV6_REDIRECT_PROCESS** _. Även om det fortfarande stöds, uppmuntras nya designer att använda _ *_NX_DISABLE_ICMPV6_REDIRECT_PROCESS_**|  
|NXDUO_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS| Har bytt namn till ***NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS_**.|
|NXDUO_DISABLE_ICMPV6_ROUTER_SOLICITATION | Har bytt namn till ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_DISABLE_ICMPV6_ROUTER_SOLICITATION_**.|
|NXDUO_ICMPV6_MAX_RTR_SOLICITATIONS | Har bytt namn till ***NX_ICMPV6_MAX_RTR_SOLICITATIONS** _. Även om det fortfarande stöds, rekommenderas nya designer att använda _*_NX_ICMPV6_MAX_RTR_SOLICITATIONS_**.|
|NXDUO_ICMPV6_RTR_SOLICITATION_INTERVAL | Har bytt namn till ***NX_ICMPV6_RTR_SOLICITATION_INTERVAL** _. Den här symbolen avskrivs. Även om det fortfarande stöds, uppmuntras nya designer att använda _ *_NX_ICMPV6_RTR_SOLICITATION_INTERVAL_**|

## <a name="netx-duo-version-id"></a>NetX Duo-versions-ID

Den aktuella versionen av NetX Duo är tillgänglig för både användaren och programprogramvaran under körning. Du kan hämta NetX Duo-versionen från undersökningen av **nx_port.h.** Dessutom innehåller den här filen även en versionshistorik för motsvarande port. Programprogramvara kan hämta NetX Duo-versionen genom att undersöka den globala _* *_strängen nx_version_id_*_ _*_nx_port.h_**.

Programvaror kan också hämta versionsinformation från de konstanter som visas nedan som definieras ***i nx_api.h***.

Dessa konstanter identifierar den aktuella produktversionen efter namn och produkt major och delversion.

\#definiera EL_PRODUCT_NETXDUO  
\#definiera NETXDUO_MAJOR_VERSION  
\#definiera NETXDUO_MINOR_VERSION