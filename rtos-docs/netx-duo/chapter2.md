---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av nätverks stacken med höga prestanda i Azure återställnings tider NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8ee9d16c71d6c207de2098d688d49e6482c8b780
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550158"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av nätverks stacken med höga prestanda i Azure återställnings tider NetX Duo, inklusive följande: 

## <a name="host-considerations"></a>Värd överväganden

Inbäddad utveckling utförs vanligt vis på Windows-eller Linux-värddatorer (UNIX). När programmet har kompilerats, länkats och den körbara filen genereras på värden laddas den ned till mål maskin varan för körning.

Normalt görs mål hämtningen från utvecklings verktygets fel sökare. Efter nedladdningen ansvarar fel sökaren för att tillhandahålla mål körnings kontroll (gå till, stoppa, Bryt punkt osv.) samt åtkomst till minne och processor register.

De flesta utvecklings verktyg för fel sökning kommunicerar med mål maskin varan via OCD-anslutningar (on-chip debug) som JTAG (IEEE 1149,1) och fel söknings läge för bakgrunden (BDM). Fel sökare kommunicerar också med mål maskin vara via ICE-anslutningar (In-Circuit emulation). Både OCD-och ICE-anslutningar ger robusta lösningar med minimalt intrång på den inhemske program varan.

För resurser som används på värden levereras käll koden för NetX Duo i ASCII-format och kräver cirka 1 MB utrymme på värddatorns hård disk.

## <a name="target-considerations"></a>Mål överväganden

NetX Duo kräver mellan 5 och 45 KByte Read-Only minne (ROM) på målet. En annan 1 till 5KBytes av målets RAM-minne (Random Access Memory) krävs för NetX Duo-trådens stack och andra globala data strukturer.

Dessutom kräver NetX Duo användningen av två ThreadX-Timer-objekt och ett ThreadX mutex-objekt. Dessa funktioner används för periodiska bearbetnings behov och tråd skydd i NetX Duo-protokollstacken.

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider NetX Duo kan hämtas från vår offentliga käll kods lagrings plats på <https://github.com/azure-rtos/netxduo/> .

Följande är en lista över flera viktiga filer i lagrings platsen:

**nx_api. h**  
C-huvudfilen som innehåller alla system likställda, data strukturer och tjänst prototyper.

**nx_port. h** C-huvudfil som innehåller alla utvecklings verktyg och targetspecific data definitioner och strukturer. 

**demo_netx. c** C-fil som innehåller ett litet demo program.

**NX. a (eller NX. lib)**  
Binär version av NetX C-biblioteket som distribueras med standard paketet.

## <a name="netx-duo-installation"></a>NetX Duo-installation

NetX Duo installeras genom att klona GitHub-lagringsplatsen till den lokala datorn. Följande är en typisk syntax för att skapa en klon av NetX Duo-lagringsplatsen på din dator:

```c
    git clone https://github.com/azure-rtos/netxduo
```

Alternativt kan du ladda ned en kopia av lagrings platsen med hjälp av knappen Ladda ned på GitHub-huvud sidan.

Du hittar också instruktioner för att skapa NetX Duo-biblioteket på den första sidan i online-lagringsplatsen.

> [!IMPORTANT]
> *Program varan behöver åtkomst till NetX Duo Library-filen (vanligt vis **NX. a** eller **NX. lib**) och C include **-filerna nx_api. h och nx_port. h**. Detta åstadkommer du genom att ange lämplig sökväg för utvecklingsverktyg eller genom att kopiera filerna till program utvecklings ytan.*

## <a name="using-netx-duo"></a>Använda NetX Duo

Det är enkelt att använda NetX Duo. I princip måste program koden innehålla ***nx_api. h** _ under kompilering och länk med netx Duo-biblioteket _*_NX. a_*_ (eller _ *_NX. lib_*) *.

Följande är de fyra enkla stegen som krävs för att bygga ett NetX Duo-program:

[!div class="mx-tdCol2BreakAll"]

| Steg  | Description  |
|---|---|
|Steg &nbsp; 1: |Inkludera filen ***nx_api. h*** i alla filer som använder netx Duo-tjänster eller data strukturer.|
|Steg &nbsp; 2: |Initiera NetX Duo-systemet genom att anropa ***nx_system_initialize** _ från funktionen _ *_tx_application_define_** eller en program tråd.|
|Steg &nbsp; 3: |Skapa en IP-instans, aktivera adress matchnings protokollet (ARP), om det behövs, och eventuella Sockets efter ***nx_system_initialize*** anropas.|
|Steg &nbsp; 4: |Kompilera program källan och länka med NetX Duo runtime library ***NX. a** _ (eller _ *_NX. lib_* *). Den resulterande bilden kan laddas ned till målet och köras!|

## <a name="troubleshooting"></a>Felsökning

Varje NetX Duo-port levereras med en eller flera demonstrationer som körs på ett faktiskt nätverk eller via en simulerad nätverks driv rutin. Det är alltid en bra idé att få demonstrations systemet igång först.

Om demonstrations systemet inte körs korrekt utför du följande åtgärder för att begränsa problemet:

1. Ta reda på hur mycket av demonstrationen som körs.
2. Öka stack storlekarna i alla nya program trådar.
3. Kompilera om NetX Duo-biblioteket med lämpliga fel söknings alternativ som anges i avsnittet konfigurations alternativ.
4. Granska NX_IPs strukturen för att se om paket skickas eller tas emot.
5. Granska standard paketets pool för att se om det finns tillgängliga paket.
6. Se till att nätverks driv rutinen tillhandahåller ARP-och IP-paket med sina huvuden på 4 bytes gränser för program som kräver IPv4-eller IPv6-anslutning.
7. Kringgå tillfälligt eventuella nyligen gjorda ändringar för att se om problemet försvinner eller ändras. Sådan information bör vara användbar för Microsofts support tekniker.

Följ de procedurer som beskrivs i "vad vi behöver från dig" på sidan 12 för att skicka informationen som samlas in från fel söknings stegen.

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ när du skapar NetX Duo-biblioteket och programmet med NetX Duo. Konfigurations alternativen kan definieras i program källan, på kommando raden eller i ***nx_user. h*** include-filen, om inget annat anges.

> [!NOTE]
> *Alternativ som definieras i **nx_user. h** tillämpas endast om program-och netx Duo-biblioteket har skapats med* **NX_INCLUDE_USER_DEFINE_FILE** definierade. *

I följande avsnitt listas de konfigurations alternativ som är tillgängliga i NetX Duo. Allmänna alternativ som är tillämpliga för både IPv4 och IPv6 visas först, följt av IPv6-angivna alternativ.

### <a name="system-configuration-options"></a>Alternativ för system konfiguration

| Alternativ  | Beskrivning  |
|---|---|
| NX_ASSERT_FAIL    | Symbol som definierar den fel söknings instruktion som ska användas när en kontroll Miss lyckas.                               |
| NX_DEBUG           | Definierad, aktiverar den valfria fel söknings informationen från RAM-nätverkskortets nätverks driv rutin. |
| NX_DEBUG_PACKET   | Definierad, aktiverar det valfria fel söknings paket som är tillgängligt i RAM-Ethernet-nätverks driv rutinen.      |
| NX_DISABLE_ASSERT | Definierad, inaktiverar kontroller i käll koden. Som standard är det här alternativet inte definierat.            |
|NX_DISABLE_ERROR_CHECKING | Definierad tar bort det grundläggande NetX Duo-API: et för fel sökning och förbättrar prestandan. API-retur koder som inte påverkas av inaktive ring av fel kontroll visas i fetstil i API-definitionen. Den här definiera används vanligt vis när programmet har fel söknings läge och används för att förbättra prestanda och minska kod storleken.|
|NX_DRIVER_DEFERRED_PROCESSING | Definierad, aktiverar uppskjuten trafik hantering av nätverks driv rutiner. Detta gör att nätverks driv rutinen kan placera ett paket på IP-instansen och ha den faktiska bearbetnings rutinen som anropas från den interna IP-NetX Duo-tråden.|
|NX_DUAL_PACKET_POOL_ENABLE | Har bytt namn till ***NX_ENABLE_DUAL_PACKET_POOL** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_ENABLE_DUAL_PACKET_POOL_* *.|
|NX_ENABLE_DUAL_PACKET_POOL | Definierad tillåter stacken att använda två lagringspooler, en med stor nytto Last storlek och en med mindre nytto Last storlek. Det här alternativet är inte aktiverat som standard.|
|NX_ENABLE_EXTENDED_NOTIFY_SUPPORT| Definierad, aktiverar fler callback-hookar i stacken. Dessa återanrops funktioner används av BSD-skiktet. Som standard är det här alternativet inte definierat.|
|NX_ENABLE_INTERFACE_CAPABILITY| Definierad, tillåter att gränssnittets enhets driv rutin anger extra kapacitets information, till exempel kontroll Summa vid inläsning. Som standard är det här alternativet inte definierat.|
|NX_ENABLE_SOURCE_ADDRESS_CHECK| Definierad, gör det möjligt att kontrol lera käll adressen för det inkommande paketet. Som standard är det här alternativet inaktiverat.|
| NX_IPSEC_ENABLE  | Definierad, gör att NetX Duo-biblioteket stöder IPsec-åtgärder. Den här funktionen kräver den valfria NetX Duo IPsec-modulen. Som standard är den här funktionen inte aktive rad.            |
| NX_LITTLE_ENDIAN | Definierad, utför nödvändiga byte växling i little endian miljöer för att se till att protokoll rubrikerna är i rätt big endian format. Observera att standardvärdet är vanligt vis installations programmet i ***nx_port. h***.|
|NX_MAX_PHYSICAL_INTERFACES | Anger det totala antalet fysiska nätverks gränssnitt på enheten. Standardvärdet är 1 och definieras i ***nx_api. h***; en enhet måste ha minst ett fysiskt gränssnitt. OBS! detta inkluderar inte loopback-gränssnittet.|
| NX_NAT_ENABLE | Definierad, NetX Duo har skapats med NAT-processen. Som standard är det här alternativet inte definierat.|
| NX_PHYSICAL_HEADER  | Anger storleken i byte för ramens fysiska rubrik. Standardvärdet är 16 (baserat på en typisk 14 byte-Ethernet-ram som är justerad till 32-bitars gräns) och definieras i ***nx_api. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _*_nx_api. h_*_ ingår, t. ex. i _ *_nx_user. h_*. * |
| NX_PHYSICAL_TRAILER | Anger storlek i byte för det fysiska paketets trailer och används vanligt vis för att reservera lagring för sådant som Ethernet-CRCs osv. Standardvärdet är 4 och definieras i ***nx_api. h***.|

### <a name="arp-configuration-options"></a>Konfigurations alternativ för ARP

| Alternativ  | Beskrivning  |
|---|---|
|NX_ARP_DEFEND_BY_REPLY | Definierad, tillåter NetX Duo att försvara sin IP-adress genom att skicka ett ARP-svar.|
|NX_ARP_DEFEND_INTERVAL| Definierar intervallet, i sekunder, skickar ARP-modulen ut nästa försvara paket som svar på ett inkommande ARP-meddelande som anger en adress i konflikt.|
|NX_ARP_DISABLE_AUTO_ARP_ENTRY|  Har bytt namn till ***NX_DISABLE_ARP_AUTO_ENTRY** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_DISABLE_ARP_AUTO_ENTRY_* *.|
|NX_ARP_EXPIRATION_RATE| Anger antalet sekunder som ARP-poster fortfarande är giltiga. Standardvärdet noll inaktiverar förfallo datum eller åldrande för ARP-poster och definieras i ***nx_api. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|
|NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | Har bytt namn till ***NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION_* *.|
|NX_ARP_MAX_QUEUE_DEPTH | Anger det maximala antalet paket som kan köas i kö i väntan på ett ARP-svar. Standardvärdet är 4 och definieras i ***nx_api. h***.|
|NX_ARP_MAXIMUM_RETRIES | Anger det maximala antal ARP-försök som gjorts utan ARP-svar. Standardvärdet är 18 och definieras i ***nx_api. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|
|NX_ARP_UPDATE_RATE | Anger antalet sekunder mellan ARP-försök. Standardvärdet är 10, vilket representerar 10 sekunder och definieras i ***nx_api. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|
|NX_DISABLE_ARP_AUTO_ENTRY | Definierad, inaktiverar registrering av ARP-information i ARP-cachen.|
|NX_DISABLE_ARP_INFO | Definierad, inaktiverar insamling av ARP-information.|
|NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION| Definierad, tillåter ARP att anropa en motringnings funktion för att identifiera MAC-adressen.|

### <a name="icmp-configuration-options"></a>Konfigurations alternativ för ICMP

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_ICMP_INFO| Definierad, inaktiverar ICMP-information från insamling.|
|NX_DISABLE_ICMP_RX_CHECKSUM| Definierad inaktiverar beräkning av både ICMPv4 och ICMPv6-kontrollsumma på mottagna ICMP-paket. Det här alternativet är användbart när nätverks gränssnittets driv rutin kan verifiera egenskapen ICMPv4 och ICMPv6, och programmet använder inte funktionen IP-fragmentering eller IPsec-funktionen. Som standard är det här alternativet inte definierat.|
|NX_DISABLE_ICMP_TX_CHECKSUM | Definierad inaktiverar beräkning av både ICMPv4 och ICMPv6-kontrollsumma på överförda ICMP-paket. Det här alternativet är användbart när nätverks gränssnittets driv rutin kan beräkna ICMPv4-och ICMPv6-kontrollsumma,
och programmet använder inte funktionen IP-fragmentering eller IPsec. Som standard är det här alternativet inte definierat.|
|NX_DISABLE_ICMPV4_ERROR_MESSAGE | Definierad, NetX Duo skickar inte ICMPv4-felmeddelanden som svar på fel villkor som felaktigt formaterade IPv4-huvud. Som standard är det här alternativet inte definierat.|
|NX_DISABLE_ICMPV4_RX_CHECKSUM | Definierad, inaktiverar ICMPv4 beräkning av kontroll summa på mottagna ICMP-paket. Det här alternativet definieras automatiskt om ***NX_DISABLE_ICMP_RX_CHECKSUM*** har definierats. Som standard är det här alternativet inte definierat.|
|NX_DISABLE_ICMPv4_RX_CHECKSUM | Har bytt namn till ***NX_DISABLE_ICMPV4_RX_CHECKSUM** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_DISABLE_ICMPV4_RX_CHECKSUM_* *.|
|NX_DISABLE_ICMPV4_TX_CHECKSUM | Definierad, inaktiverar ICMPv4 beräkning av kontroll summa för överförda ICMP-paket. Det här alternativet definieras automatiskt om ***NX_DISABLE_ICMP_TX_CHECKSUM*** har definierats. Som standard är det här alternativet inte definierat.|
|NX_DISABLE_ICMPv4_TX_CHECKSUM | Har bytt namn till ***NX_DISABLE_ICMPV4_TX_CHECKSUM** _.</br>Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_DISABLE_ICMPV4_TX_CHECKSUM_* *.|
|NX_ENABLE_ICMP_ADDRESS_CHECK | Definierad är mål adressen för ICMP-paket markerat. Standardvärdet är inaktiverad. En ICMP-ekobegäran som är avsedd för en IP-broadcast eller IP multicast-adress kommer att ignoreras tyst.|

### <a name="igmp-configuration-options"></a>Konfigurations alternativ för IGMP

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_IGMP_INFO | Definierad, inaktiverar insamling av IGMP-information.|
|NX_DISABLE_IGMPV2 | Definierad, inaktiverar IGMPv2-stöd och NetX Duo stöder endast IGMPv1. Som standard är det här alternativet inte angivet och definieras i ***nx_api. h***.|
|NX_MAX_MULTICAST_GROUPS | Anger det maximala antalet multicast-grupper som kan anslutas. Standardvärdet är 7 och definieras i ***nx_api. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|

### <a name="ip-configuration-options"></a>Alternativ för IP-konfiguration

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_FRAGMENTATION | Definierad, inaktiverar både IPv4-och IPv6-fragmentering och omsammansättnings logik.|
| NX_DISABLE_IPV4     | Defined, inaktiverar IPv4-funktionen. Det här alternativet kan användas för att bygga NetX Duo till suupport endast IPv6. Som standard är det här alternativet inte definierat. |
| NX_DISABLE_IP_INFO | Definierad, inaktiverar insamling av IP-information.|
|NX_DISABLE_IP_RX_CHECKSUM | Definierad, inaktiverar kontroll summa för mottagna IPv4-paket. Detta är användbart om nätverks enheten kan verifiera IPv4-kontroll summan och programmet inte förväntar sig att använda IP-fragmentering eller IPsec.|
|NX_DISABLE_IP_TX_CHECKSUM | Definierad, inaktiverar kontroll summa för IPv4-paket som skickas. Detta är användbart i situationer där den underliggande nätverks enheten kan generera kontroll summan för IPv4-huvud, och programmet förväntar sig inte att använda IP-fragmentering eller IPsec.|
|NX_DISABLE_LOOPBACK_INTERFACE | Definierad, inaktiverar NetX Duo-stöd för loopback-gränssnittet.|
|NX_DISABLE_RX_SIZE_CHECKING | Definierad, inaktiverar storleks kontrollen på mottagna paket.|
|NX_ENABLE_IP_RAW_PACKET_FILTER | Definierad, aktiverar filtrerings funktionen för IP RAW-paket. Program som kräver mer kontroll över vilken typ av RAW-IP-paket som ska tas emot kan använda den här funktionen. Funktionen IP-paket filter stöder även åtgärden för RAW-socket i BSD-kompatibilitetsläget. Som standard är det här alternativet inte definierat.|
|NX_ENABLE_IP_STATIC_ROUTING | Definierad, aktiverar statisk routning för IPv4 där en mål adress kan tilldelas en viss nästa hopp-adress. Som standard är IPv4 statisk routning inaktiverat.|
|NX_FRAGMENT_IMMEDIATE_ASSEMBLY | Definierad, tillåter att IPv4-och IPv6-omsammansättnings logik körs direkt efter att ha tagit emot ett IP-fragment. Som standard är det här alternativet inte definierat.|
|NX_IP_MAX_REASSEMBLY_TIME | Symbol som styr den längsta tid som tillåts för att sätta samman IPv4-fragment och IPv6-fragment. Observera att värdet som definieras här skriver över både ***NX_IPV4_MAX_REASSEMBLY_TIME** _ och _ *_NX_IPV6_MAX_REASSEMBLY_TIME_* *.|
|NX_IP_PERIODIC_RATE | Definierad anger antalet ThreadX timer-Tick i en sekund. Standardvärdet härleds från ThreadX symbol ***TX_TIMER_TICKS_PER_SECOND,** _ som standard är inställt på 100 (10ms timer). Program bör vara försiktiga när du ändrar det här värdet, eftersom resten av NetX Duo-modulerna härleder tids information från _ *_NX_IP_PERIODIC_RATE_.**|
|NX_IP_RAW_MAX_QUEUE_DEPTH | Symbol som styr antalet obehandlade IP-paket som kan placeras i kö i kön för mottagna rå paket. Som standard är värdet 20.| 
|NX_IP_ROUTING_TABLE_SIZE | Definierat anger det maximala antalet poster i tabellen IPv4-statisk routning, som är en lista över ett utgående gränssnitt och nästa hopp adresser för en viss mål adress. Standardvärdet är 8 och definieras i ***nx_api. h.** _ Den här symbolen används endast om _ *_NX_ENABLE_IP_STATIC_ROUTING_** har definierats.|
|NX_IPV4_MAX_REASSEMBLY_TIME | Symbol som styr den längsta tid som tillåts för omsammansättning av IPv4-fragment. Observera att värdet som definieras i NX_IP_MAX_REASSEMBLY_TIME skriver över det här värdet.|

### <a name="packet-configuration-options"></a>Alternativ för paket konfiguration

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_PACKET_CHAIN | Definierad, inaktiverar logiken för paket kedjan. Som standard är detta inte definierat.|
|NX_DISABLE_PACKET_INFO | Definierad, inaktiverar insamling av paketets pool information.|
|NX_ENABLE_LOW_WATERMARK | Definierad, aktiverar NetX Duo-paketets pool med låg storleks gräns. I programmet anges ett värde för nedre vatten märket. Om du tar emot TCP-paket, och om paketets pool med låg storlek nås, ignorerar NetX Duo paketet genom att släppa det, vilket förhindrar poolen från effekter. Som standard är den här funktionen inte aktive rad.|
|NX_ENABLE_PACKET_DEBUG_INFO | Definierad loggar fel söknings information för paket.|
|NX_PACKET_ALIGNMENT | Definierad anger justerings kravet, i byte, för start adressen för paketets nytto Last. Det här alternativet är inaktuellt ***NX_PACKET_HEADER_PAD** _ och _ *_NX_PACKET_HEADER_PAD_SIZE_* *. Som standard är det här alternativet definierat som 4, vilket gör att start adressen för nytto lasts ytan 4-byte justerad.|
|NX_PACKET_HEADER_PAD | Definierad, aktiverar utfyllnad mot slutet av NX_PACKET kontroll blocket. Antalet ULONG-ord som ska pad definieras av ***NX_PACKET_HEADER_PAD_SIZE** _. Observera att det här alternativet skrivs av _ *_NX_PACKET_ALIGNMENT_* *.|
|NX_PACKET_HEADER_PAD_SIZE | Anger antalet ULONG-ord som ska fyllas i NX_PACKET-strukturen, vilket gör det möjligt för paketets nytto last att starta vid önskad justering. Den här funktionen är användbar när du ska ta emot buffertens beskrivare direkt i NX_PACKET nytto lastområdet, och nätverks gränssnittet tar emot logik eller om cache åtgärds logiken förväntar sig att de uppfyller vissa justerings krav. Det här värdet är bara giltigt när ***NX_PACKET_HEADER_PAD** _ har definierats. Observera att det här alternativet är föråldrat av _ *_NX_PACKET_ALIGNMENT_* *.|

### <a name="rarp-configuration-options"></a>Konfigurations alternativ för RARP

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_RARP_INFO | Definierad, inaktiverar insamling av RARP-information.|

### <a name="tcp-configuration-options"></a>Konfigurations alternativ för TCP

| Alternativ | Beskrivning |
|---|---|
|NX_DISABLE_RESET_DISCONNECT | Definierad, inaktiverar återställnings bearbetningen under från koppling när det angivna tids gräns värdet har angetts som ***NX_NO_WAIT***.|
|NX_DISABLE_TCP_INFO | Definierad, inaktiverar insamling av TCP-information.|
|NX_DISABLE_TCP_RX_CHECKSUM | Definierad, inaktiverar kontroll summa för mottagna TCP-paket. Detta är endast användbart i situationer där länk skiktet har tillförlitlig kontroll summa eller CRC-bearbetning, eller så kan gränssnitts driv rutinen verifiera TCP-kontrollsummaet i maskin vara och programmet använder inte IPsec.|
|NX_DISABLE_TCP_TX_CHECKSUM | Definierad, inaktiverar kontroll summa för att skicka TCP-paket. Detta är bara användbart i situationer där mottagande nätverks-noden har fått logik för kontroll Summa inaktive rad eller om den underliggande nätverks driv rutinen kan generera TCP-kontrollsumma, och programmet använder inte IPsec.|
|NX_ENABLE_TCP_KEEPALIVE | Definierad, aktiverar den valfria TCP keepalive-timern. Standardinställningarna är inte aktiverade.|
|NX_ENABLE_TCP_MSS_CHECK | Definierad, aktiverar verifiering av lägsta peer-MSS innan en TCP-anslutning accepteras. Om du vill använda den här funktionen måste symbol ***NX_ENABLE_TCP_MSS_MINIMUM*** definieras. Som standard är det här alternativet inte aktiverat.|
|NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY| Definierad, tillåter att programmet installerar en callback-funktion som anropas när TCP-överföringens ködjup inte längre är det högsta värdet. Det här återanropet fungerar som en indikation på att TCP-socketen är redo att skicka mer data. Det här alternativet är inte aktiverat som standard.|
|NX_ENABLE_TCP_WINDOW_SCALING | Aktiverar alternativ för fönster skalning för TCP-program. Om alternativet har definierats förhandlas alternativet för fönster skalning under fasen TCP-anslutning och programmet kan ange en fönster storlek som är större än 64 kB. Standardinställningen är inte aktive rad (inte definierad).|
|NX_MAX_LISTEN_REQUESTS | Anger det maximala antalet Server lyssnings begär Anden. Standardvärdet är 10 och definieras i ***nx_api. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|
|NX_TCP_ACK_EVERY_N_PACKETS | Anger antalet TCP-paket som ska tas emot innan en ACK skickas. Obs! Om ***NX_TCP_IMMEDIATE_ACK** _ är aktiverat men _ *_NX_TCP_ACK_EVERY_N_PACKETS_** inte är det här värdet automatiskt inställt på 1 för bakåtkompatibilitet.|
|NX_TCP_ACK_TIMER_RATE | Anger hur antalet system Tick (NX_IP_PERIODIC_RATE) delas för att beräkna timer-frekvensen för TCP-fördröjd ACK-bearbetning. Standardvärdet är 5, som representerar 200ms och definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|
|NX_TCP_ENABLE_KEEPALIVE | Har bytt namn till ***NX_ENABLE_TCP_KEEPALIVE** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_ENABLE_TCP_KEEPALIVE_* *.|
|NX_TCP_ENABLE_MSS_CHECK | Har bytt namn till ***NX_ENABLE_TCP_MSS_CHECK** _. Även om det fortfarande stöds, uppmanas nya mönster att använda _ *_NX_ENABLE_TCP_MSS_CHECK._**|
|NX_TCP_ENABLE_WINDOW_SCALING | Har bytt namn till ***NX_ENABLE_TCP_WINDOW_SCALING** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_ENABLE_TCP_WINDOW_SCALING_* *.|
|NX_TCP_FAST_TIMER_RATE | Anger hur antalet interna NetX Duo-Tick (NX_IP_PERIODIC_RATE) delas för att beräkna den snabba TCP-tidsfrekvensen. Den snabba TCP-timern används för att driva olika TCP-tidstjänster, inklusive den fördröjda ACK-tiden. Standardvärdet är 10, som representerar 100 MS förutsatt att ThreadX-timern körs vid 10ms. Det här värdet definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|
|NX_TCP_IMMEDIATE_ACK| Definierad, aktiverar den valfria bearbetningen av TCP omedelbart ACK-svar. Att definiera den här symbolen motsvarar att definiera  ***NX_TCP_ACK_EVERY_N_PACKETS*** som 1.|
|NX_TCP_KEEPALIVE_INITIAL | Anger antalet sekunder av inaktivitet innan keepalive-timern aktive ras. Standardvärdet är 7200, vilket motsvarar 2 timmar och definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|
|NX_TCP_KEEPALIVE_RETRIES | Anger hur många keepalive-återförsök som tillåts innan anslutningen anses vara bruten. Standardvärdet är 10, som representerar 10 återförsök och definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|
|NX_TCP_KEEPALIVE_RETRY | Anger antalet sekunder mellan återförsök för keepalive-timer under antagandet att den andra sidan av anslutningen inte svarar. Standardvärdet är 75, vilket motsvarar 75 sekunder mellan återförsök och definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|
|NX_TCP_MAX_OUT_OF_ORDER_PACKETS | Symbol som definierar det högsta antalet färdiga TCP-paket som kan behållas i kön för mottagning av TCP-socket. Den här symbolen kan användas för att begränsa antalet paket som har placerats i kö i TCP Receive-socketen, vilket förhindrar att modempoolen har. Som standard är den här symbolen inte definierad, så det finns ingen gräns för antalet paket som ska placeras i kö i TCP-socketen.|
|NX_TCP_MAXIMUM_RETRIES | Anger hur många försök till data överföring som tillåts innan anslutningen anses vara bruten. Standardvärdet är 10, som representerar 10 återförsök och definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|
|NX_TCP_MAXIMUM_RX_QUEUE | Symbol som definierar den maximala mottagnings kön för TCP-socketar. Den här funktionen aktive ras av ***NX_ENABLE_LOW_WATERMARK***.|
|NX_TCP_MAXIMUM_TX_QUEUE | Anger det maximala djupet för TCP-överförings kön innan TCP-begäran om sändning har pausats eller avvisats. Standardvärdet är 20, vilket innebär att högst 20 paket kan finnas i överförings kön vid en specifik tidpunkt. Antecknings paket förblir i överförings kön tills en bekräftelse som täcker vissa eller alla paket data tas emot från den andra sidan av anslutningen. Den här konstanten definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|
|NX_TCP_MSS_MINIMUM | Symbol som definierar det minimala MSS-värdet NetX Duo TCP-modulen accepterar. Den här funktionen aktive ras av ***NX_ENABLE_TCP_MSS_CHECK***.|
|NX_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_ENABLE | Har bytt namn till ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_* *.|
|NX_TCP_RETRY_SHIFT | Anger hur timeout-perioden för omsändning ändras mellan återförsök. Om det här värdet är 0, är den första timeoutn för omsändning detsamma som efterföljande timeout-Timeout. Om det här värdet är 1, är varje överföring i följd två gånger så lång. Om det här värdet är 2 är varje omsändnings-timeout fyra gånger så lång. Standardvärdet är 0 och definieras i ***nx_tcp. h** _. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|
|NX_TCP_TRANSMIT_TIMER_RATE | Anger hur antalet system Tick (***NX_IP_PERIODIC_RATE** _) delas för att beräkna timer-frekvensen för bearbetningen av återförsök för TCP-överföring. Standardvärdet är 1, vilket motsvarar 1 sekund och definieras i _*_nx_tcp. h_*_. Programmet kan åsidosätta standardvärdet genom att definiera värdet innan _ *_nx_api. h_** ingår.|

### <a name="udp-configuration-options"></a>Alternativ för UDP-konfiguration

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_UDP_INFO | Definierad, inaktiverar insamling av UDP-information.|
|NX_DISABLE_UDP_RX_CHECKSUM | Definierad inaktiverar beräkningen av UDP-kontrollsumma på inkommande UDP-paket. Detta är användbart om nätverks gränssnittets driv rutin kan verifiera kontroll summa för UDP-huvud i maskin vara och programmet inte aktiverar IPsec-eller IP-fragmentering-logik.|
|NX_DISABLE_UDP_TX_CHECKSUM | Definierad inaktiverar beräkningen av UDP-kontrollsumma på utgående UDP-paket. Detta är användbart om nätverks gränssnittets driv rutin kan beräkna kontroll summa för UDP-huvud och infoga värdet i IP-huvudet innan data överförs, och programmet aktiverar inte IPsec-eller IP-fragmentering.|

### <a name="ipv6-options"></a>IPv6-alternativ  

| Alternativ  | Beskrivning  |
|---|---|
| NX_DISABLE_IPV6 | Inaktiverar IPv6-funktioner när NetX Duo-biblioteket har skapats. För program som inte behöver IPv6 kan du undvika att hämta kod och ytterligare lagrings utrymme som krävs för att stödja IPv6.|
|NX_DISABLE_IPV6_PATH_MTU_DISCOVERY | Definierad, inaktiverar sökvägs-MTU-identifiering, som används för att fastställa maximal MTU i sökvägen till ett mål i mål tabellen för NetX Duo-värden. Detta gör att NetX Duo-värden kan skicka det största möjliga paketet som inte kräver fragmentering. Som standard är det här alternativet definierat (path MTU är inaktive rad).|
|NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY | Definierad, tillåter att en callback-funktion anropas när IPv6-adressen ändras. Det här alternativet är inte aktiverat som standard.|
|NX_ENABLE_IPV6_MULTICAST | Definierad, aktiverar funktionen IPv6 multicast-anslutning/lämna. Det här alternativet är inte aktiverat som standard.|
|NX_ENABLE_IPV6_PATH_MTU_DISCOVERY | Definierad, aktiverar IPv6-sökvägens MTU-identifierings funktion. Det här alternativet är inte aktiverat som standard.|
|NX_IPV6_ADDRESS_CHANGE_NOTIFY_ENABLE | Har bytt namn till ***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY_* *.|
|NX_IPV6_DEFAULT_ROUTER_TABLE_SIZE | Anger antalet poster i IPv6-routningstabellen. Posten minst krävs för standardroutern. Som definierats i ***nx_api. h*** är standardvärdet 8.|
|NX_IPV6_DESTINATION_TABLE_SIZE | Anger antalet poster i IPv6-mål tabellen. Här lagras information om adresser för nästa hopp för IPv6-adresser. Som definierats i ***nx_api. h*** är standardvärdet 8.|
|NX_IPV6_MAX_REASSEMBLY_TIME | Symbol som styr den längsta tid som tillåts för att sätta samman IPv6-fragment.|
|NX_IPV6_MULTICAST_ENABLE | Har bytt namn till ***NX_ENABLE_IPV6_MULTICAST** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_ENABLE_IPV6_MULTICAST_* *.|
|NX_IPV6_PREFIX_LIST_TABLE_SIZE | Anger storleken på prefix tabellen. Information om prefix hämtas från routermeddelanden och ingår i IPv6-adress konfigurationen. Som definierats i ***nx_api. h*** är standardvärdet 8.|
|NX_IPV6_STATELESS_AUTOCONFIG_CONTROL | Definierad, tillåter NetX Duo att inaktivera funktionen för automatisk konfiguration av tillstånds lösa adresser. Det här alternativet är inte aktiverat som standard.|
|NX_MAX_IPV6_ADDRESSES | Anger antalet poster i IPv6-adresspoolen. Under gränssnitts konfigurationen använder NetX Duo IPv6-poster från poolen. Standardvärdet är (NX_MAX_PHYSICAL_INTERFACES \* 3) för att tillåta varje gränssnitt att ha minst en lokal länk adress och två globala adresser. Observera att alla gränssnitt delar IPv6-adresspoolen.|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | Anger vänte intervallet i timer-Tick för att återställa Path-MTU för ett särskilt mål i mål tabellen. Om ***NX_DISABLE_IPV6_PATH_MTU_DISCOVERY*** har definierats har den här symbolen ingen påverkan.|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | Symbol som anger vänte tiden (i sekunder) för att återställa sökvägens MTU-värde för en mål tabell post. Den är endast giltig om ***NX_ENABLE_IPV6_PATH_MTU_DISCOVERY*** har definierats. Som standard är det här värdet inställt på 600 (sekunder).|

### <a name="neighbor-cache-configuration-options"></a>Konfigurations alternativ för närliggande cache

| Alternativ  | Beskrivning  |
|---|---|
|NX_DELAY_FIRST_PROBE_TIME | Anger fördröjningen i sekunder innan den första inbjudningen skickas ut för en cachepost i inaktuellt tillstånd. Som definierats i ***nx_nd_cache. h*** är standardvärdet 5.|
|NX_DISABLE_IPV6_DAD | Definierad inaktiverar den dubbla adress identifieringen (pappa) under IPv6-adresstilldelning. Adresser anges antingen genom manuell konfiguration eller via automatisk adress konfiguration för tillstånd.|
|NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES | Det här alternativet förhindrar att NetX Duo tar bort äldre cacheposter innan tids gränsen löper ut för att göra plats för nya poster när tabellen är full. Statiska och router-poster rensas aldrig.|
|NX_IPV6_DAD_TRANSMITS | Anger antalet grann Inbjudnings meddelanden som ska skickas innan NetX Duo markerar en gränssnitts adress som giltig. Om ***NX_DISABLE_IPV6_DAD** _ definieras (pappa inaktive rad) har det här alternativet ingen påverkan. Alternativt är värdet noll (0) inaktiverat pappa, men far-funktionen blir kvar i NetX Duo. Definieras i _ *_nx_api. h_* *, standardvärdet är 3.|
|NX_IPV6_DISABLE_PURGE_UNUSED_CACHE_ENTRIES | Har bytt namn till ***NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES_* *.|
|NX_IPV6_NEIGHBOR_CACHE_SIZE | Anger antalet poster i IPv6-den närliggande cache-tabellen. Som definierats i ***nx_nd_cache. h*** är standardvärdet 16.|
|NX_MAX_MULTICAST_SOLICIT | Anger antalet grann Inbjudnings meddelanden NetX Duo-överföringar som en del av IPv6-protokollet för grann identifiering när mappningen mellan IPv6-adressen och MAC-adressen krävs. Som definierats i ***nx_nd_cache. h*** är standardvärdet 3.|
|NX_MAX_UNICAST_SOLICIT | Anger antalet grann Inbjudnings meddelanden NetX Duo-överföringar för att fastställa en speciell grann tillgänglighet. Som definierats i ***nx_nd_cache. h*** är standardvärdet 3.|
|NX_ND_MAX_QUEUE_DEPTH | Symbol som definierar det maximala antalet paket som köade cache-minnet måste matcha. Som standard är den här symbolen inställd på 4.|
|NX_REACHABLE_TIME | Anger tids gränsen i sekunder för att en cachepost ska finnas i det NÅBARa läget utan att några paket tas emot från IPv6-adressen för cache-målet. Som definierats i ***nx_nd_cache. h*** är standardvärdet 30.|
|NX_RETRANS_TIMER  | Anger vänte tiden i millisekunder mellan de begärda paketen som skickas av NetX Duo. Som definierats i ***nx_nd_cache. h*** är standardvärdet 1000.|
| NXDUO_DISABLE_DAD | Har bytt namn till ***NX_DISABLE_IPV6_DAD** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_DISABLE_IPV6_DAD_* *.|
|NXDUO_DUP_ADDR_DETECT_TRANSMITS | Har bytt namn till ***NX_IPV6_DAD_TRANSMITS** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_IPV6_DAD_TRANSMITS_* *.|

### <a name="miscellaneous-icmpv6-configuration-options"></a>Diverse konfigurations alternativ för ICMPv6

| Alternativ  | Beskrivning  |
|---|---|
|NX_DISABLE_ICMPV6_ERROR_MESSAGE | Definierad, inaktiverar NetX duo från att skicka ett ICMPv6-felmeddelande som svar på ett problem paket (t. ex. felaktigt formaterat huvud-eller paket huvud typ är inaktuellt) som tagits emot från en annan värd.|
|NX_DISABLE_ICMPV6_REDIRECT_PROCESS | Definierad, inaktiverar ICMPv6-omdirigering av paket bearbetning. NetX Duo som standard bearbetar meddelanden och uppdaterar mål tabellen med IP-adressinformation för nästa hopp.|
|NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS | Definierad, inaktiverar NetX duo från bearbetning av information som tas emot i IPv6-routers annonserings paket.|
|NX_DISABLE_ICMPV6_ROUTER_SOLICITATION | Definierad, inaktiverar NetX duo från att skicka IPv6-routers inbjudningar meddelanden med jämna mellanrum till routern.|
|NX_DISABLE_ICMPV6_RX_CHECKSUM | Definierad, inaktiverar beräkning av beräkning av ICMPv6 på mottagna ICMP-paket.|
|NX_DISABLE_ICMPv6_RX_CHECKSUM | Har bytt namn till ***NX_DISABLE_ICMPV6_RX_CHECKSUM** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_DISABLE_CMPV6_RX_CHECKSUM_* *.|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | Definierad, inaktiverar och ICMPv6-kontrollsummas beräkning på överförda ICMP-paket.|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | Har bytt namn till ***NX_DISABLE_ICMPV6_TX_CHECKSUM** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_DISABLE_ICMPV6_TX_CHECKSUM_* *.|
|NX_ICMPV6_MAX_RTR_SOLICITATIONS | Definiera det högsta antalet routermeddelanden som en värd skickar tills ett router-svar tas emot. Om inget svar tas emot, avslutar värden ingen router. Standardvärdet är 3.|
|NX_ICMPV6_RTR_SOLICITATION_DELAY | Anger den maximala fördröjningen för den inledande router-inbjudningen på några sekunder.|
|NX_ICMPV6_RTR_SOLICITATION_INTERVAL | Anger intervallet mellan två router Inbjudnings meddelanden. Standardvärdet är 4.|
|NXDUO_DESTINATION_TABLE_SIZE | Har bytt namn till ***NX_IPV6_DESTINATION_TABLE_SIZE** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_IPV6_DESTINATION_TABLE_SIZE_* *.|
|NXDUO_DISABLE_ICMPV6_ERROR_MESSAGE | Har bytt namn till ***NX_DISABLE_ICMPV6_ERROR_MESSAGE** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_DISABLE_ICMPV6_ERROR_MESSAGE_* *.|
|NXDUO_DISABLE_ICMPV6_REDIRECT_PROCESS | Har bytt namn till ***NX_DISABLE_ICMPV6_REDIRECT_PROCESS** _. Även om det fortfarande stöds, uppmanas nya mönster att använda _ *_NX_DISABLE_ICMPV6_REDIRECT_PROCESS_**|  
|NXDUO_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS| Har bytt namn till ***NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS_* *.|
|NXDUO_DISABLE_ICMPV6_ROUTER_SOLICITATION | Har bytt namn till ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_DISABLE_ICMPV6_ROUTER_SOLICITATION_* *.|
|NXDUO_ICMPV6_MAX_RTR_SOLICITATIONS | Har bytt namn till ***NX_ICMPV6_MAX_RTR_SOLICITATIONS** _. Även om det fortfarande stöds, uppmuntras nya ritningar att använda _ *_NX_ICMPV6_MAX_RTR_SOLICITATIONS_* *.|
|NXDUO_ICMPV6_RTR_SOLICITATION_INTERVAL | Har bytt namn till ***NX_ICMPV6_RTR_SOLICITATION_INTERVAL** _. Den här symbolen skrivs över. Även om det fortfarande stöds, uppmanas nya mönster att använda _ *_NX_ICMPV6_RTR_SOLICITATION_INTERVAL_**|

## <a name="netx-duo-version-id"></a>Versions-ID för NetX Duo

Den aktuella versionen av NetX Duo är tillgänglig för både användaren och program varan under körning. Du kan hämta NetX Duo-versionen från undersökningen av filen **nx_port. h** . Dessutom innehåller den här filen även en versions historik för motsvarande port. Program varan kan hämta netx Duo-versionen genom att undersöka den globala strängen _* *_nx_version_id_*_ i _ *_nx_port. h_* *.

Program varan kan också hämta versions information från de konstanter som visas nedan definierade i ***nx_api. h***.

Dessa konstanter identifierar den aktuella produkt versionen efter namn och produktens huvud-och del version.

\#definiera EL_PRODUCT_NETXDUO  
\#definiera NETXDUO_MAJOR_VERSION  
\#definiera NETXDUO_MINOR_VERSION