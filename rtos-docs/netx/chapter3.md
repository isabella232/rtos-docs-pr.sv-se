---
title: Kapitel 3 – funktionella komponenter i Azure återställnings tider NetX
description: Det här kapitlet innehåller en beskrivning av den högpresterande Azure-återställnings tider NetX TCP/IP-stacken från ett funktionellt perspektiv.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db23aa152b2765ac7cc9be098723fc5df0947484
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826886"
---
# <a name="chapter-3---functional-components-of-azure-rtos-netx"></a>Kapitel 3 – funktionella komponenter i Azure återställnings tider NetX

Det här kapitlet innehåller en beskrivning av den högpresterande Azure-återställnings tider NetX TCP/IP-stacken från ett funktionellt perspektiv. 

## <a name="execution-overview"></a>Översikt över körning

Det finns fem typer av program körningar i ett NetX-program: initiering, program gränssnitts anrop, intern IP-tråd, periodiska timers och nätverks driv rutinen.

> [!IMPORTANT]
> NetX kräver installation av ThreadX och beror på dess tråd körning, avbrytande, periodiska timers och ömsesidiga undantags funktioner.

### <a name="initialization"></a>Initiering

Tjänsten ***nx_system_initialize** _ måste anropas innan någon annan netx-tjänst anropas. System initiering kan anropas antingen från ThreadX _ *_tx_application_define_** rutin eller från program trådar.

Efter ***nx_system_initialize** _ returnerar, är systemet redo att skapa paket pooler och IP-instanser. Eftersom det krävs en standardpool för att skapa en IP-instans måste det finnas minst en NetX-modempool innan en IP-instans skapas. Det går att skapa paket pooler och IP-instanser från initierings funktionen ThreadX _ *_tx_application_define_** och från program trådar.

Internt skapas en IP-instans i två delar. Den första delen görs inom kontexten för anroparen, antingen från ***tx_application_define*** eller från en program tråds kontext. Detta innefattar att konfigurera IP-datastrukturen och skapa olika IP-resurser, inklusive den interna IP-tråden. Den andra delen utförs vid den första körningen från den interna IP-tråden. Det är här som nätverks driv rutinen, som angavs under den första delen av IP-skapandet, först anropas. Genom att anropa nätverks driv rutinen från den interna IP-tråden kan driv rutinen utföra I/O och pausa under initierings bearbetningen. När nätverks driv rutinen återgår från initierings processen slutförs IP-skapandet.

> [!IMPORTANT]
> NetX-tjänsten **nx_ip_status_check** finns tillgänglig för att hämta information om IP-instansen och dess primära gränssnitts status. Sådan statusinformation innehåller om länken är initierad, aktive rad och IP-adressen är löst. Den här informationen används för att synkronisera program trådar som behöver använda en nyligen skapad IP-instans. För multihome-system, se "Support för multihome" nedan. **nx_ip_interface_status_check** finns tillgängligt för att hämta information om det angivna gränssnittet.

### <a name="application-interface-calls"></a>Program gränssnitts anrop

Anrop från programmet görs i stort sett från program trådar som körs under ThreadX-återställnings tider. Vissa initierings-, Create-och enable-tjänster kan dock anropas från ***tx_application_define***. I avsnitten "tillåtet från" i kapitel 4 anges från vilka varje NetX-tjänst kan anropas.

För det mesta görs bearbetningen av intensiva aktiviteter, till exempel beräknings kontroll summor i den anropande trådens kontext, utan att åtkomsten till andra trådar blockeras till IP-instansen. Vid överföring utförs exempelvis beräkningen av UDP-kontrollsumma i ***nx_udp_socket_sends*** tjänsten innan den underliggande IP-Send-funktionen anropas. På ett mottaget paket beräknas UDP-kontrollsummaet i ***nx_udp_socket_receive*** tjänsten som körs i kontexten för program tråden. Detta bidrar till att förhindra att nätverks begär Anden med högre prioritet kan stoppas på grund av bearbetning av intensiv beräkning av kontroll summa i trådar med lägre prioritet.

Värden, till exempel IP-adresser och port nummer, skickas till API-funktioner i värd byte ordning. Internt lagras dessa värden i värdens byte-ordning. På så sätt kan utvecklare enkelt visa värdena via en fel sökare. När dessa värden är programmerade i en ram för överföring, konverteras de till byte ordning för nätverk.

### <a name="internal-ip-thread"></a>Intern IP-tråd

Som nämnts har varje IP-instans i NetX en egen tråd. Prioriteten och stack storleken för den interna IP-tråden definieras i ***nx_ip_creates*** tjänsten. Den interna IP-tråden skapas i ett läge som är klart att köras. Om IP-tråden har högre prioritet än den anropande tråden kan avstängningen uppstå i IP-Create-anropet.

Den interna IP-trådens start punkt är den interna funktionen ***_nx_ip_thread_entry***. När den interna IP-tråden startas slutförs först nätverks driv Rutinens initiering, som består av tre anrop till den programspecifika nätverks driv rutinen. Det första anropet är att koppla nätverks driv rutinen till IP-instansen, följt av ett initierings anrop, vilket gör att nätverks driv rutinen kan gå igenom initierings processen. När nätverks driv rutinen har returnerat från initieringen (den kan stoppas under väntan på att maskin varan ska konfigureras korrekt), anropar den interna IP-tråden nätverks driv rutinen igen för att aktivera länken. 

När nätverks driv rutinen har returnerat från länken Aktivera anrop, anger den interna IP-tråden en oändlig loop-kontroll för olika händelser som behöver bearbetas för den här IP-instansen. Händelser som bearbetas i den här slingan är inskjuten mottagning av IP-paket, sammansättning av IP-paket, ICMP-Ping-bearbetning, IGMP-bearbetning, bearbetning av TCP-paketfiltrering, TCP-periodisk bearbetning, timeout för IP-fragment och IGMP-periodisk bearbetning. Händelser omfattar även adress matchnings aktiviteter: ARP-paketfiltrering och regelbunden bearbetning i ARP i IP-nätverket.

> [!NOTE]
> *Återanrops funktionerna i NetX, inklusive lyssnings-och från koppling, anropas från den interna IP-tråden, inte den ursprungliga anropande tråden. Programmet måste ta hand om att inte pausa i någon NetX-callback-funktion.*

### <a name="ip-periodic-timers"></a>Periodiska timers för IP
Det finns två ThreadX-periodiska timers som används för varje IP-instans. Den första är en eng-Second-timer för ARP, IGMP, TCP-tidsgräns och den också bearbetar ommonteringen av IP-fragment. Den andra timern är en 100 MS-timer för att köra timeout för TCP-omöverföring.

### <a name="network-driver"></a>Nätverks driv rutin
Varje IP-instans i NetX har ett primärt gränssnitt som identifieras av den driv rutin som anges i ***nx_ip_creates*** tjänsten. Nätverks driv rutinen ansvarar för hantering av olika NetX-förfrågningar, inklusive paket överföring, paket mottagning och förfrågningar om status och kontroll.

För ett multi-Home-system har IP-instansen flera gränssnitt, var och en med en associerad nätverks driv rutin som utför dessa uppgifter för respektive gränssnitt.

Nätverks driv rutinen måste också hantera asynkrona händelser som inträffar på mediet. Asynkrona händelser från mediet omfattar paket mottagning, slut för ande av paket överföring och status ändringar. NetX tillhandahåller nätverks driv rutinen med flera åtkomst funktioner för att hantera olika händelser. Dessa funktioner är utformade för att anropas från Interrupt Service Routine delen av nätverks driv rutinen. För IP-nätverk bör nätverks driv rutinen vidarebefordra alla ARP-paket som tas emot till ***_nx_arp_packet_deferred_receive** _ intern funktion. Alla RARP-paket ska vidarebefordras till _ *_ _nx_rarp_packet_deferred_receive_* _ intern funktion. Det finns två alternativ för IP-paket. Om snabb sändning av IP-paket krävs ska inkommande IP-paket vidarebefordras till _ *_ _nx_ip_packet_receive_* _ för omedelbar bearbetning. Detta förbättrar prestandan i NetX i hanteringen av IP-paket. Annars bör nätverks driv rutinen vidarebefordra IP-paket till _ * _ _nx_ip_packet_deferred_receive_* *. Den här tjänsten placerar IP-paketet i den uppskjutna bearbetnings kön där den hanteras av den interna IP-tråden, vilket resulterar i minst mängden ISR-bearbetnings tid.

Nätverks driv rutinen kan också skjuta upp avbrott-bearbetningen så att den inte går att använda i kontexten för IP-tråden. I det här läget måste ISR Spara nödvändig information, anropa den interna funktionen ***_nx_ip_driver_deferred_processing*** och bekräfta avbrotts styrenheten. Den här tjänsten meddelar IP-tråden att schemalägga ett återanrop till enhets driv rutinen för att slutföra bearbetningen av händelsen som orsakar avbrottet.

Vissa nätverks styrenheter kan utföra beräkning och validering av kontroll summa för TCP/IP-huvud i maskin vara, utan att ta upp värdefulla processor resurser. För att kunna dra nytta av funktionen för maskin varu kapacitet tillhandahåller NetX alternativ för att aktivera eller inaktivera olika beräkningar av program kontroll summor vid kompilering, samt aktivera eller inaktivera beräkning av kontroll Summa vid körning. Mer detaljerad information om hur du skriver NetX-nätverks driv rutiner finns i "[kapitel 5 netx Network Drivers](chapter5.md)".

### <a name="multihome-support"></a>Support för multihome
NetX stöder system som är anslutna till flera fysiska enheter som använder en enda IP-instans. Varje fysiskt gränssnitt tilldelas ett gränssnitts kontroll block i IP-instansen. Program som vill använda ett hem system måste definiera värdet för **NX_MAX_PHSYCIAL_INTERFACES** till antalet fysiska enheter som är anslutna till systemet och återskapa netx-biblioteket. Som standard **NX_MAX_PHYSICAL_INTERFACES** har angetts till ett, skapar du ett gränssnitts kontroll block i IP-instansen.

NetX-programmet skapar en enskild IP-instans för den primära enheten med hjälp av tjänsten ***nx_ip_create** _. För varje ytterligare nätverks enheter ansluter programmet enheten till IP-instansen med hjälp av tjänsten _ *_nx_ip_interface_attach_**.

Varje nätverks gränssnitts struktur innehåller en delmängd av nätverksinformation om det nätverks gränssnitt som finns i IP Control-blocket, inklusive IP-adress för gränssnitt, nätmask, IP-MTU-storlek och adress information för MAC-lager.

> [!IMPORTANT]
> *NetX med stöd för multihome är bakåtkompatibel med tidigare versioner av NetX. Tjänster som inte har uttryckligen gränssnitts information som standard till den primära nätverks enheten.*

Det primära gränssnittet har index noll i listan över IP-instanser. Varje efterföljande enhet som är kopplad till IP-instansen tilldelas nästa index.

Alla de övre skikt protokoll tjänsterna för vilka IP-instansen är aktive rad, inklusive TCP, UDP, ICMP och IGMP, är tillgängliga för alla anslutna enheter.

I de flesta fall kan NetX avgöra den bästa käll adressen som ska användas vid överföring av ett paket. Käll adress valet baseras på mål adressen. NetX Services tillhandahålls för att tillåta att program anger en speciell käll adress som ska användas, i de fall där den lämpligaste orsaken inte kan fastställas av mål adressen. Ett exempel skulle finnas i ett hem system, ett program måste skicka ett paket till en IP-broadcast eller multicast-mål adresser.

Tjänster som är specifika för att utveckla program med fler Hem nätverk är följande:

*nx_igmp_multicast_interface_join nx_ip_driver_interface_direct_command nx_ip_interface_address_get nx_ip_interface_address_set nx_ip_interface_attach nx_ip_interface_info_get nx_ip_interface_status_check nx_ip_raw_packet_interface_send nx_udp_socket_interface_send*

Dessa tjänster förklaras i detalj i "[kapitel 4 – Beskrivning av Azure återställnings tider netx-tjänster](chapter4.md)".

### <a name="loopback-interface"></a>Loopback-gränssnitt
Loopback-gränssnittet är ett särskilt nätverks gränssnitt utan en fysisk länk som är kopplad till. Loopback-gränssnittet gör att program kan kommunicera med IP loopback-adressen 127.0.0.1

Om du vill använda ett logiskt loopback-gränssnitt ser du till att alternativet konfigurerbar ***NX_DISABLE_LOOPBACK_INTERFACE*** inte har angetts.

### <a name="interface-control-blocks"></a>Gränssnitts kontroll block
Antalet gränssnitts kontroll block i IP-instansen är antalet fysiska gränssnitt (definieras med ***NX_MAX_PHYSICAL_INTERFACES** _) plus loopback-gränssnittet om det är aktiverat. Det totala antalet gränssnitt definieras i _ *_NX_MAX_IP_INTERFACES_* *.

## <a name="protocol-layering"></a>Protokoll skikt

TCP/IP som implementeras av NetX är ett lager protokoll, vilket innebär att mer komplexa protokoll skapas ovanpå enklare underliggande protokoll. I TCP/IP finns det lägsta skikt protokollet på *länk skiktet* och hanteras av nätverks driv rutinen. Den här nivån är normalt riktad mot Ethernet, men det kan också vara fiber, seriellt eller praktiskt taget valfritt fysiskt medium.

Ovanpå länk skiktet finns *nätverks skiktet*. I TCP/IP är detta IP-adressen, som i princip ansvarar för att skicka och ta emot enkla paket, på bästa möjliga sätt i hela nätverket. Hanterings typ protokoll som ICMP och IGMP kategoriseras vanligt vis som nätverks lager, även om de förlitar sig på IP för att skicka och ta emot.

*Transport lagret* vilar ovanpå nätverks nivån. Det här lagret ansvarar för att hantera data flödet mellan värdar i nätverket. Det finns två typer av transport tjänster som stöds av NetX: UDP och TCP. UDP-tjänsterna ger dig bästa möjliga sändning och mottagning av data mellan två värdar på ett anslutnings effektivt sätt, medan TCP tillhandahåller Reliable anslutningsorienterade tjänster mellan två värd enheter.

Skiktning visas i de faktiska nätverks data paketen. Varje lager i TCP/IP innehåller ett block med information som kallas rubrik. Den här metoden för omgivande data (och eventuellt protokoll information) med en rubrik kallas vanligt vis för data inkapsling. Bild 1 visar ett exempel på NetX-skiktning och bild 2 visar den resulterande data inkapslingen för UDP-data som skickas.

![Protokoll skikt](./media/user-guide/protocol-layering.png)

**BILD 1. Protokoll skikt**

![UDP-inkapsling](./media/user-guide/udp-data-encapsulation.png)

**BILD 2. UDP-inkapsling**

## <a name="packet-pools"></a>Paket pooler

Att allokera paket på ett snabbt och entydigt sätt är alltid en utmaning i real tids nätverks program. Med detta i åtanke ger NetX möjlighet att skapa och hantera flera pooler med nätverks paket med fast storlek.

Eftersom NetX paket består av minnes block med fast storlek, finns det aldrig några interna fragmenterings problem. Fragmenteringen orsakar naturligtvis att beteendet är icke deterministiskt.

Dessutom är tiden som krävs för att allokera och frigöra ett NetX paket belopp till enkel manipulering av länkade listor. Paket tilldelningen och avallokeringen görs dessutom på huvud sidan i listan över tillgängliga. Detta ger snabbast möjlig länkad List bearbetning.

Brist på flexibilitet är vanligt vis den huvudsakliga nack delen med paket med fast storlek. Att fastställa den optimala paket nytto Last storleken som även hanterar det värsta inkommande paketet är en svår uppgift. NetX paket löser det här problemet med en valfri funktion som kallas *paket länkning*. Ett faktiskt nätverks paket kan skapas för en eller flera NetX-paket som är länkade till varandra. Dessutom upprätthåller paket huvudet en pekare överst i paketet. När ytterligare protokoll läggs till flyttas den här pekaren bara baklänges och det nya sidhuvudet skrivs direkt framför data. Utan flexibel paket teknik skulle stacken behöva allokera en annan buffert och kopiera data till en ny buffert med det nya sidhuvudet, vilket är bearbetnings intensiv.

Eftersom varje paketets nytto Last storlek har åtgärd ATS för en viss modempool, kräver program data som är större än nytto Last storleken flera paket sammankopplade. När du fyller ett paket med användar data måste programmet använda tjänsten ***nx_packet_data_append***. Den här tjänsten flyttar program data till ett paket. I situationer där ett paket inte är tillräckligt för att lagra användar data allokeras ytterligare paket för att lagra användar data. Om du vill använda paket länkning måste driv rutinen kunna ta emot eller överföra från kedjade paket.

Varje NetX Packet-pool är en offentlig resurs. NetX placerar inga begränsningar för hur Packet-pooler används.

### <a name="packet-pool-memory-area"></a>Minnes området för paket pool
Minnes området för Packet-poolen anges när den skapas. Precis som andra minnes områden för ThreadX-och NetX-objekt kan det finnas var som helst i mål adress utrymmet. Detta är en viktig funktion på grund av den stora flexibiliteten ger programmet. Anta till exempel att en kommunikations produkt har ett höghastighets minnes utrymme för nätverks buffertar. Det här minnes området används enkelt genom att göra det till en NetX Packet-pool.

### <a name="creating-packet-pools"></a>Skapa paket pooler
Paket pooler skapas antingen under initieringen eller under körningen av program trådar. Det finns ingen gräns för antalet paket minnes pooler i ett NetX program.

### <a name="packet-header-nx_packet"></a>Paket huvud NX_PACKET
Som standard placerar NetX paket rubriken omedelbart före paketets nytto Last-sektion. Paketets minnes uppsättning är i princip en serie paket – huvuden som följs omedelbart av paketets nytto Last. Paket huvudet (***NX_PACKET***) och poolens layout visas i bild 3.

För nätverks enhets driv rutin som kan utföra kostnads kopierings åtgärder är vanligt vis start adressen för paketets nytto Last i DMA-logiken. Vissa DMA-motorer har justerings krav på nytto lasts ytan.

> [!IMPORTANT]
> * Nätverks driv rutinen måste anropa ***nx_packet_transmit_release** _-funktionen när överföring av ett paket är slutförd. Den här funktionen kontrollerar att paketet inte ingår i en kö för TCP-utdata innan den faktiskt placeras i den tillgängliga poolen. Om du inte anropar den här funktionen kan det leda till oförutsägbara behavior._

![Layout för paket huvud och adresspool](./media/user-guide/packet-header-packet-pool-layout.png)

**BILD 3. Layout för paket huvud och adresspool**

Fälten i paket rubriken definieras enligt följande tabell. Observera att den här tabellen inte är en omfattande lista över alla medlemmar i *NX_PACKETs* strukturen.

| Paket huvud          | Syfte                                                                                                                                                                                                                                                                                                                            |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *nx_packet_pool_owner*   | Det här fältet pekar på den modempool som äger det aktuella paketet. När paketet släpps släpps det till den här poolen. Med poolen ägarskap i varje paket är det möjligt för ett datagram att spänna över flera paket från flera paket pooler.                                                         |
| *nx_packet_next*         | Det här fältet pekar på nästa paket inom samma ram. Om värdet är NULL finns det inga ytterligare paket som är en del av ramen. |
| *nx_packet_last*         | Det här fältet pekar på det sista paketet i samma nätverks paket. Om värdet är NULL representerar det här paketet hela nätverks paketet.  |
| *nx_packet_length*       | Det här fältet innehåller det totala antalet byte i hela nätverks paketet, inklusive summan av alla byte i alla paket som sammankopplas tillsammans med den *nx_packet_next* medlemmen. |
| *nx_packet_ip_interface* | Det här fältet är gränssnitts kontroll blocket som tilldelas paketet när det tas emot av gränssnitts driv rutinen och av NetX för utgående paket. Ett gränssnitts kontroll block beskriver gränssnittet, t. ex. nätverks adress, MAC-adress, IP-adress och gränssnitts status, till exempel länk aktiverat och fysisk mappning krävs. |
| *nx_packet_data_start*   | Det här fältet pekar på början av det fysiska nytto Last området för det här paketet. Det behöver inte omedelbart följa NX_PACKETs huvudet, men det är standardvärdet för tjänsten ***nx_packet_pool_create*** . |
| *nx_packet_data_end*     | Det här fältet pekar på slutet av det fysiska nytto Last området för det här paketet. Skillnaden mellan det här fältet och fältet nx_packet_data_start representerar nytto lastens storlek. |
| *nx_packet_prepend_ptr*  | Det här fältet pekar på platsen där paket data, antingen protokoll huvud eller faktiska data, läggs till framför befintliga paket data (om sådana finns) i paketets nytto Last område. Det måste vara större än eller lika med platsen för *nx_packet_data_start* pekare och mindre än eller lika med *nx_packet_append_ptrs* pekaren.  *Av prestanda skäl förutsätter NetX att när paketet skickas till NetX-tjänster för överföring, pekar lägga pekar på lång Word-justerad adress.* |
| *nx_packet_append_ptr*    | Det här fältet pekar på slutet av de data som för närvarande finns i paketets nytto Last område. Det måste ligga mellan minnes platsen som *nx_packet_prepend_ptr* och *nx_packet_data_end*. Skillnaden mellan det här fältet och fältet *nx_packet_prepend_ptr* representerar mängden data i det här paketet. |
| *nx_packet_fragment_next* | Det här fältet används för att lagra fragmenterade paket tills hela paketet kan sammanställas igen. |
| *nx_packet_pad*           | I det här fältet definieras längden på utfyllnad i 4 byte-ord för att uppnå det önskade justerings kravet. Det här fältet tas bort om *NX_PACKET_HEADER_PAD* inte har definierats. |
|  |  |

### <a name="packet-header-offsets"></a>Paket huvud förskjutningar

Paketets huvud storlek definieras för att tillåta tillräckligt med utrymme för att rymma rubrikens storlek. Tjänsten *nx_packet_allocate* används för att allokera ett paket och justerar lägga-pekaren i paketet enligt den typ av paket som angetts. Paket typen talar om för NetX vilken förskjutning som krävs för att lägga till protokoll huvudet (till exempel UDP, TCP eller ICMP) framför protokoll data.

Följande typer definieras i NetX för att ta hänsyn till IP-huvudet och det fysiska skiktet (Ethernet) i paketet. I det senare fallet antas det vara 16 byte som tar hänsyn till den nödvändiga justeringen av 4 byte. IP-paket definieras fortfarande i NetX för program för att allokera paket för IP-nätverk. Följande tabell innehåller symboler som definierats:

| Pakettyp   | Värde |
|---------------|-------|
| NX_IP_PACKET  | 0x24  |
| NX_UDP_PACKET | 0x2c  |
| NX_TCP_PACKET | 0x38  |
|               |       |

### <a name="pool-capacity"></a>Pool-kapacitet
Antalet paket i en adresspool är en funktion i nytto lastens storlek och det totala antalet byte i minnes området som har angetts till Packet poolens Create-tjänst. Poolens kapacitet beräknas genom att du dividerar paket storleken (inklusive storleken på NX_PACKET huvud, nytto lastens storlek och rätt justering) till det totala antalet byte i det angivna minnes området.

### <a name="thread-suspension"></a>Tråd upphängning
Program trådar kan pausas i väntan på ett paket från en tom pool. När ett paket returneras till poolen får den pausade tråden det här paketet och återupptas.

Om flera trådar är inaktiverade i samma modempool återupptas de i den ordning som de var pausade (FIFO).

### <a name="pool-statistics-and-errors"></a>Statistik och fel i pooler
Om den här inställningen är aktive rad håller NetX Packet Management-program varu **fel** att spåra flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter underhålls för paketbaserade pooler:

* Totalt antal paket i poolen
* Lediga paket i poolen
* Pool tomma tilldelnings begär Anden
* Förskjutande av pool, tomma allokeringar
* Ogiltiga paket versioner

Alla dessa statistik-och fel rapporter, förutom det totala antalet och det lediga paket antalet i poolen, är inbyggda i NetX-biblioteket om inte ***NX_DISABLE_PACKET_INFO** _ har definierats. Dessa data är tillgängliga för programmet med tjänsten _ *_nx_packet_pool_info_get_**.

### <a name="packet-pool-control-block-nx_packet_pool"></a>Kontroll block för Packet-pool NX_PACKET_POOL

Egenskaperna för varje paket minnes uppsättning finns i kontroll blocket. Den innehåller användbar information, till exempel den länkade listan över lediga paket, antalet lediga paket och nytto Last storleken för paket i den här poolen. Den här strukturen definieras i filen *nx_api. h* .

Du kan placera kontroll block var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

## <a name="ip-protocol"></a>IP-protokoll

Komponenten Internet Protocol (IP) i NetX ansvarar för att skicka och ta emot IP-paket på Internet. I NetX är det den komponent som slutligen ansvarar för att skicka och ta emot TCP-, UDP-, ICMP-och IGMP-meddelanden med hjälp av den underliggande nätverks driv rutinen.

NetX stöder IP-protokoll (RFC 791)

### <a name="ip-addresses"></a>IP-adresser

Varje värd på Internet har en unik 32-bitars identifierare som kallas för en IP-adress. Det finns fem klasser av IP-adresser enligt beskrivningen i bild 4. Intervallen för de fem IP-adress klasserna är följande:

| Klass | Intervall                        |
|-------|------------------------------|
| A     | 0.0.0.0 till 127.255.255.255   |
| B     | 128.0.0.0 till 191.255.255.255 |
| C     | 192.0.0.0 till 223.255.255.255 |
| D     | 224.0.0.0 till 239.255.255.255 |
| E     | 240.0.0.0 till 247.255.255.255 |

**7 bitar 24 bitar**

![IP-adress struktur](./media/user-guide/ip-address-structure.png)

**BILD 4. IP-adress struktur**

Det finns också tre typer av adress specifikationer: *unicast*, *broadcast* och *multicast*. Unicast-adresser är de IP-adresser som identifierar en speciell värd på Internet. Unicast-adresser kan vara antingen en källa eller en mål-IP-adress. En broadcast-adress identifierar alla värdar i ett särskilt nätverk eller under nätverk och kan bara användas som mål adresser. Broadcast-adresser anges genom att ha den värd-ID-del av adressen som anges till dem. Multicast-adresser (klass D) anger en dynamisk grupp värdar på Internet. Medlemmar i multicast-gruppen kan ansluta till och lämna när de vill.

> [!IMPORTANT]
> *Endast anslutnings bara protokoll som UDP över IP kan använda broadcast och begränsad broadcast-kapacitet för multicast-gruppen.*

> [!IMPORTANT]
> *Makrot* IP_ADDRESS *definieras i*  * **nx_api. h** _. Det möjliggör enkel specifikation av IP-adresser med kommatecken i stället för en punkt. Exempel: IP_ADDRESS (128, 0, 0) _specifies den första klass B-adressen som visas i bild 4. *

### <a name="ip-gateway-address"></a>IP-gateway-adress

Nätverksgateway hjälper värdar i sina nätverk att vidarebefordra paket som är avsedda för destinationer utanför den lokala domänen. Varje nod har en viss kunskap om vilka nästa hopp som ska skickas till, antingen på målet en av dess grannar, eller genom en förprogrammerad statisk routningstabell. Men om dessa metoder inte fungerar bör noden vidarebefordra paketet till dess standardgateway som innehåller mer information om hur paketet dirigeras till målet. Observera att standardgateway måste vara direkt tillgänglig via ett av de fysiska gränssnitt som är kopplade till IP-instansen. Programmet anropar ***nx_ip_gateway_address_set*** att konfigurera IP-adress för standardgateway.

### <a name="ip-header"></a>IP-huvud

För att IP-paket ska kunna skickas på Internet måste det ha ett IP-huvud. När protokoll på högre nivå (UDP, TCP, ICMP eller IGMP) anropar IP-komponenten för att skicka ett paket, placerar modulen IP-överföring ett IP-huvud framför data. När IP-paket tas emot från nätverket, tar IP-komponenten bort IP-huvudet från paketet innan det levereras till protokoll på högre nivå. Bild 5 visar formatet på IP-huvudet.

![Format för IP-huvud](./media/user-guide/ip-header-format.png)

**BILD 5. Format för IP-huvud**

> [!IMPORTANT]
> *Alla rubriker i TCP/IP-implementeringen förväntas vara i big endian format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen. Till exempel måste 4-bitars versionen och längden på 4-bitars huvudet för IP-huvudet finnas på den första byten i rubriken.*

Fälten i IP-huvudet definieras enligt följande:

**Fält syfte för IP-huvud**

***4-bitars version*** Det här fältet innehåller den version av IP som detta sidhuvud representerar. För IP version 4, vilket är vad NetX stöder, är värdet för det här fältet 4.

***4-bitars rubrik längd*** Det här fältet anger antalet 32-bitars ord i IP-huvudet. Om det inte finns några alternativ ord är värdet för det här fältet 5.

***8-bitars typ av tjänst (TOS)*** I det här fältet anges vilken typ av tjänst som begärs för det här IP-paketet. Giltiga begär Anden är följande:

| **TOS-begäran**     | **Värde** |
| ------------------- | --------- |
| Normal              | 0x00      |
| Minsta fördröjning       | 0x10      |
| Maximalt antal data        | 0x08      |
| Högsta pålitlighet | 0x04      |
| Lägsta kostnad        | 0x02      |

***16-bitars total längd*** Det här fältet innehåller den totala längden för IP-datagram i byte, inklusive IP-huvudet. Ett IP-datagram är den grundläggande informations enheten som finns på ett TCP/IP-Internet. Den innehåller en mål-och käll adress förutom data. Eftersom det är ett 16-bitars fält är den maximala storleken för ett IP-datagram 65 535 byte.

***16-bitars identifiering*** Fältet är ett tal som används för att unikt identifiera varje IP-datagram som skickas från en värd. Det här talet ökar ofta när ett IP-datagram har skickats. Det är särskilt användbart i att montera mottagna IP-paket.

***3-bitars flaggor*** Det här fältet innehåller information om IP-fragment. Bit 14 är biten "ingen fragment". Om den här biten anges fragmenteras inte det utgående IP-datagrammet. Bit 13 är biten "fler fragment". Om den här biten anges finns det fler fragment. Om den här biten är klar är det sista fragmentet i IP-paketet.

**Fält syfte för IP-huvud**

***13-bitars fragment förskjutning*** Det här fältet innehåller den övre 13 bitarna i fragment förskjutningen. Därför tillåts fragment förskjutningar bara på 8 byte-gränser. Det första fragmentet i ett fragmenterat IP-datagram kommer att ha biten "fler fragment" och ha en förskjutning på 0.

***8-bitars TTL-värde (Time to Live)*** Det här fältet innehåller antalet routrar som det här datagrammet kan skicka, vilket begränsar datagrammets livstid.

***8-bitars protokoll*** Det här fältet anger vilket protokoll som använder IP-datagrammet. Följande är en lista över giltiga protokoll och deras värden:

| Protokoll | Värde |
|----------|-------|
| ICMP     | 0x01  |
| PROXYLÄGE     | 0x02  |
| TCP      | 0X06  |
| UDP      | 0X11  |
|          |       |


***16-bitars kontroll Summa*** Det här fältet innehåller 16-bitars kontroll summa som endast täcker IP-huvudet. Det finns ytterligare kontroll summor i protokoll på högre nivå som behandlar IP-nyttolasten.

***32-bitars käll-IP-adress*** Det här fältet innehåller avsändarens IP-adress och är alltid en värd adress.

***32-bitars mål-IP-adress*** Det här fältet innehåller mottagarens eller mottagarens IP-adress om adressen är en broadcast-eller multicast-adress.

### <a name="creating-ip-instances"></a>Skapar IP-instanser

IP-instanser skapas antingen under initieringen eller under körningen av program trådar. Den första IP-adressen, nätverks masken, standard paketet, medie driv rutinen och minnet och prioriteten för den interna IP-tråden definieras av tjänsten *nx_ip_create* . Om programmet initierar IP-instansen med dess IP-adress inställt på en ogiltig adress (0.0.0.0), förutsätts att gränssnitts adressen kommer att lösas av manuell konfiguration senare, via RARP eller via DHCP eller liknande protokoll.

För system med flera nätverks gränssnitt anges det primära gränssnittet när du anropar *nx_ip_create*. Varje ytterligare gränssnitt kan kopplas till samma IP-instans genom att anropa *nx_ip_interface_attach*. Den här tjänsten lagrar information om nätverks gränssnittet (till exempel IP-adress, nätverks mask) i gränssnitts kontroll blocket och kopplar driv rutins instansen till gränssnitts kontroll blocket i IP-instansen. När driv rutinen tar emot ett data paket måste den lagra gränssnitts informationen i NX_PACKETs strukturen innan den vidarebefordras till IP Receive-logiken. Observera att en IP-instans redan måste skapas innan du kopplar några gränssnitt.

 ### <a name="ip-send"></a>IP-sändning
 IP-sändnings bearbetning i NetX är mycket effektivt.

Lägga-pekaren i paketet flyttas bakåt för att hantera IP-huvudet. IP-huvudet har slutförts (med alla alternativ som anges av anrops protokoll skiktet), beräkning av IP-kontroll i rad och paketet skickas till den associerade nätverks driv rutinen. Dessutom samordnas utgående fragmentering från bearbetningen av IP-överföring.

För IP initierar NetX ARP-begäranden om fysisk mappning krävs för målets IP-adress.

> [!IMPORTANT]
> *För IP-anslutning placeras paket som kräver IP-namnmatchning (dvs. fysisk mappning) i ARP-kön tills antalet paket i kö överskrider ARP-ködjup (definieras av* *symbolen **NX_ARP_MAX_QUEUE_DEPTH**). Om* *ködjup nås tar netx bort det äldsta paketet i kön och fortsätter att vänta på adress matchning för de återstående paketen i kö. Å andra sidan, om en ARP-post inte har lösts, släpps de väntande paketen på ARP-posten vid tids gränsen för ARP-posten.*

För system med flera nätverks gränssnitt väljer NetX ett gränssnitt baserat på mål-IP-adressen. Följande procedur gäller för urvals processen:

1. Om en mål adress är IP-broadcast eller multicast, och om ett giltigt utgående gränssnitt har angetts, använder du det gränssnittet. Annars används det första fysiska gränssnittet.

2. Om mål adressen finns i tabellen för statisk routning används det gränssnitt som är associerat med gatewayen.

3. Om målet är länkat, används on-Link-gränssnittet.

4. Om mål adressen är en loopback-adress 127.0.0.1 används loopback-gränssnittet.

5. Om standard-gatewayen är korrekt konfigurerad använder du det gränssnitt som är associerat med standard-gatewayen för att överföra paketet.

6. Utgående paket ignoreras om ovanstående inte fungerar.

### <a name="ip-receive"></a>IP-mottagning

Den mottagna IP-bearbetningen anropas antingen från nätverks driv rutinen eller den interna IP-tråden (för bearbetning av paket i kön med uppskjutna mottagna paket). IP-inleveransbearbetning undersöker protokoll fältet och försöker skicka paketet till rätt protokoll komponent. Innan paketet skickas tas IP-huvudet bort genom att lägga-pekaren flyttas förbi IP-huvudet.

IP Receive-bearbetning identifierar också fragmenterade IP-paket och utför nödvändiga steg för att sätta samman dem igen om fragmentering har Aktiver ATS. Om fragmentering krävs men inte aktive rad, ignoreras paketet.

NetX identifierar lämpligt nätverks gränssnitt baserat på det gränssnitt som anges i paketet. Om paket gränssnittet är NULL, NetX som standard det primära gränssnittet. Detta görs för att garantera kompatibilitet med äldre NetX Ethernet-drivrutiner.

### <a name="raw-ip-send"></a>RAW IP-sändning

Ett RAW IP-paket är en IP-ram som innehåller nytto lasten i versaler och protokoll som inte stöds direkt (och bearbetas) av NetX. Med ett RAW-paket kan utvecklare definiera sina egna IP-baserade program. Ett program kan skicka Raw IP-paket direkt med hjälp av ***nx_ip_raw_packet_send** _-tjänsten om RAW IP-paketfiltrering har Aktiver ATS med tjänsten _*_nx_ip_raw_packet_enabled_*_ . Om mål adressen är en multicast-eller broadcast-adress, kommer NetX att standardvärdet för det första (primära) gränssnittet. För att skicka sådana paket från sekundära gränssnitt måste programmet därför använda tjänsten _ *_nx_ip_raw_packet_interface_send_** för att ange käll adressen som ska användas för det utgående paketet.

### <a name="raw-ip-receive"></a>RAW IP-mottagning

Om RAW IP-paketfiltrering är aktive rad kan programmet få obehandlade IP-paket via tjänsten ***nx_ip_raw_packet_receive** _. Alla inkommande paket bearbetas enligt det protokoll som anges i IP-huvudet. Om protokollet anger UDP, TCP, IGMP eller ICMP, kommer NetX att bearbeta paketet med lämplig hanterare för paket protokoll typen. Om protokollet inte är ett av dessa protokoll och RAW IP Receive är aktive rad placeras det inkommande paketet i den obehandlade paket kön som väntar på att programmet ska ta emot det via tjänsten _ *_nx_ip_raw_packet_receive_**. Dessutom kan program trådar pausas med en valfri tids gräns vid väntan på ett RAW IP-paket.

### <a name="default-packet-pool"></a>Standard pakets bassäng

Varje IP-instans tilldelas en standardpool för paket när den skapas. Den här poolen används för att allokera paket för ARP, RARP, ICMP, IGMP, olika TCP-kontroll paket (till exempel SYN, ACK). Om standardpoolen är tom när NetX måste allokera ett paket kan NetX behöva avbryta den aktuella åtgärden och returnera ett fel meddelande om möjligt.

### <a name="ip-helper-thread"></a>IP-hjälp tråd

Varje IP-instans har en hjälp tråd. Den här tråden ansvarar för hantering av all uppskjuten paket bearbetning och all periodisk bearbetning. IP-hjälpens tråd skapas i ***nx_ip_create.*** Det är här som tråden tilldelas sin stack och prioritet. Observera att den första bearbetningen i IP Helper-tråden är att slutföra initieringen av nätverks driv rutinen som är associerad med IP-Create-tjänsten. När nätverks driv rutins initieringen är klar startar hjälp tråden en oändlig slinga för att bearbeta paket och periodiska begär Anden.

> [!IMPORTANT]
> *Om ett oförutsägbart beteende visas i IP-undersöknings tråden, är det första fel söknings steget att öka dess stack storlek under IP-tjänsten för att skapa fel sökning. Om stacken är för liten kan IP-hjälpen eventuellt skriva över minne, vilket kan orsaka ovanliga problem.*

### <a name="thread-suspension"></a>Tråd upphängning

Program trådar kan pausas vid försök att ta emot obehandlade IP-paket. När ett RAW-paket tas emot, tilldelas det nya paketet den första tråden och tråden återupptas. NetX Services för att ta emot paket har en valfri tids gräns för timeout. När ett paket tas emot eller tids gränsen går ut, återupptas program tråden med rätt slut för ande status.

### <a name="ip-statistics-and-errors"></a>IP-statistik och fel

Om den är aktive rad håller NetX koll på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter underhålls för varje IP-instans:

- Totalt antal skickade IP-paket
- Totalt antal skickade IP-byte
- Totalt antal mottagna IP-paket
- Totalt antal mottagna IP-byte
- Totalt antal ogiltiga IP-paket
- Totalt antal borttagna IP-mottagna paket
- Totalt antal fel vid kontroll av IP-mottagning
- Totalt antal borttagna IP-skickade paket
- Totalt antal skickade IP-fragment
- Totalt antal mottagna IP-fragment

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med tjänsten ***nx_ip_info_get*** .

### <a name="ip-control-block-nx_ip"></a>Kontroll block för IP-kontroll NX_IP

Egenskaperna för varje IP-instans finns i kontroll blocket. Den innehåller användbar information, till exempel IP-adresser och nätverks masker för varje nätverks enhet och en tabell med grann-IP och mappning av fysiska maskin varu adresser. Den här strukturen definieras i kontroll blocken för ***nx_api. h*** -kontroll som kan finnas var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="static-ip-routing"></a>Statisk IP-routning

Funktionen för statisk routning gör att ett program kan ange ett IP-nätverk och nästa hopp adress för specifika IP-adresser för nätverks mål. Om statisk routning är aktiverat söker NetX igenom den statiska routningstabellen för en post som matchar mål adressen för det paket som ska skickas. Om ingen matchning hittas söker NetX igenom listan över fysiska gränssnitt och väljer en käll-IP-adress och nästa hopp adress baserat på mål-IP-adressen och nätverks masken. Om målet inte matchar någon av IP-adresserna för de nätverks driv rutiner som är kopplade till IP-instansen, väljer NetX ett gränssnitt som är direkt anslutet till standard-gatewayen och använder IP-adressen för gränssnittet som käll adress och standard-gatewayen som nästa hopp.

Poster kan läggas till och tas bort från tabellen med statiska vägar med hjälp av ***nx_ip_static_route_add*** och ***nx_ip_static_route_delete** _ tjänster. Om du vill använda statisk routning måste värd programmet aktivera den här funktionen genom att definiera _ *_NX_ENABLE_IP_STATIC_ROUTING_*. *

> [!IMPORTANT]
> *När du lägger till en post i den statiska routningstabellen, söker NetX efter en matchande post för den angivna mål adressen redan i tabellen. Om det finns en sådan, ger den företräde för posten med det mindre nätverket (längre prefix) i nätverks masken.*

### <a name="ip-fragmentation"></a>IP-fragmentering

Nätverks enheten kan ha gränser för storleken på utgående paket. Den här gränsen kallas för maximal överförings enhet (MTU). IP-MTU är den största IP-bildrutans storlek som en länk skikt driv rutin kan överföra utan att fragmentera IP-paketet. Under en initierings fas av enhets driv rutinen måste driv rutins modulen konfigurera dess IP-MTU-storlek via tjänsten ***nx_ip_interface_mtu_set**. *

Även om det inte rekommenderas kan programmet generera datagram som är större än den underliggande IP-MTU som stöds av enheten. Innan det här IP-datagrammet överförs måste IP-skiktet fragmentera dessa paket. När du tar emot fragmenterade IP-ramar måste det mottagande slutet lagra alla fragmenterade IP-ramar med samma fragment-ID och ommontera dem i rätt ordning. Om IP-mottagnings logiken inte kan samla in alla fragment för att återställa den ursprungliga IP-ramen i tiden, släpps alla fragment. Det är upp till det övre skikt protokollet för att identifiera sådana paket förluster och återställa från det.

För att stödja IP-fragmentering och omsammansättnings åtgärd måste system designern aktivera funktionen IP-fragmentering i NetX med hjälp av tjänsten ***nx_ip_fragment_enable*** . Om den här funktionen inte är aktive rad ignoreras inkommande fragmenterade IP-paket, samt paket som överskrider nätverks driv Rutinens MTU.

> [!IMPORTANT]
> *Logiken för IP-fragmentering kan tas bort helt genom att definiera*  * **NX_DISABLE_FRAGMENTATION** _ _When skapa theNetX-bibliotek. Detta bidrar till att minska kod storleken för NetX. *

## <a name="address-resolution-protocol-arp-in-ip"></a>ARP (Address Resolution Protocol) i IP

ARP-protokollet (Address Resolution Protocol) ansvarar för att dynamiskt mappa 32-bitars IP-adresser till de underliggande fysiska medierna (RFC 826). Ethernet är det mest typiska fysiska mediet och stöder 48-bitars adresser. Behovet av ARP bestäms av nätverks driv rutinen som tillhandahålls till ***nx_ip_create*** tjänsten. Om fysisk mappning krävs måste nätverks driv rutinen ange flaggan ***nx_interface_address_mapping_needed*** i gränssnittet struktur.

### <a name="arp-enable"></a>Aktivera ARP
För att ARP ska fungera korrekt måste den först aktive ras av programmet med ***nx_arp_enable*** -tjänsten. Den här tjänsten konfigurerar olika data strukturer för ARP-bearbetning, inklusive skapandet av ett ARP-cache-utrymme från det minne som har angetts till tjänsten ARP enable.

### <a name="arp-cache"></a>ARP-cache
ARP-cachen kan visas som en matris med interna ARP-mappnings data strukturer. Varje intern struktur kan underhålla relationen mellan en IP-adress och en fysisk maskin varu adress. Dessutom har varje data struktur länk pekare så att den kan ingå i flera länkade listor.

Programmet kan slå upp en IP-adress från ARP-cachen genom att tillhandahålla maskin varans MAC-adress med hjälp av tjänsten ***nx_arp_ip_address_find** _ om mappningen finns i ARP-tabellen. På samma sätt returnerar tjänsten _ *_nx_arp_hardware_address_find_** Mac-adressen för en specifik IP-adress.


### <a name="arp-dynamic-entries"></a>Dynamiska ARP-poster

Som standard placerar tjänsten ARP Enable alla poster i ARP-cachen i listan över tillgängliga dynamiska ARP-poster. En dynamisk ARP-post tilldelas från den här listan av NetX när en skicka-begäran till en omappad IP-adress identifieras. Efter allokeringen konfigureras ARP-posten och en ARP-begäran skickas till det fysiska mediet.

En dynamisk post kan också skapas av tjänsten ***nx_arp_dynamic_entry_set***.

> [!IMPORTANT]
> *Om alla dynamiska ARP-poster används ersätts den senast använda ARP-posten med en ny mappning.*

### <a name="arp-static-entries"></a>Statiska ARP-poster
Programmet kan också konfigurera statiska ARP-mappningar med hjälp av tjänsten ***nx_arp_static_entry_create*** . Den här tjänsten allokerar en ARP-post från listan över dynamiska ARP-poster och placerar den på den statiska listan med mappnings informationen som tillhandahålls av programmet. Statiska ARP-poster omfattas inte av åter användning eller åldrande. Programmet kan ta bort en statisk post genom att använda tjänsten ***nx_arp_static_entry_delete***.
Om du vill ta bort alla statiska poster i ARP-tabellen kan programmet använda tjänsten ***nx_arp_static_entries_delete***.

### <a name="automatic-arp-entry"></a>Automatisk ARP-post
NetX registrerar peers IP/MAC-mappning efter peer-svar på ARP-begäran. NetX implementerar också funktionen automatisk ARP-post där den registrerar peer IP/MAC-adress mappning baserat på oombedda ARP-begäranden från nätverket. Med den här funktionen kan ARP-tabellen fyllas i med peer-information, vilket minskar fördröjningen som krävs för att gå igenom ARP-begäran/svars cykeln. Nack delen med att aktivera automatisk ARP är dock att ARP-tabellen ofta fyller på ett upptaget nätverk med många noder på den lokala länken, vilket skulle leda till byte av ARP-post.

Den här funktionen är aktive rad som standard. För att inaktivera det måste NetX-biblioteket kompileras med symbolen ***NX_DISABLE_ARP_AUTO_ENTRY*** definierad.

### <a name="arp-messages"></a>ARP-meddelanden

Som tidigare nämnts skickas ett meddelande om ARP-begäran när IP-aktiviteten identifierar att mappning krävs för en IP-adress. ARP-begäranden skickas regelbundet (var ***NX_ARP_UPDATE_RATE** _ sekunder) tills ett motsvarande ARP-svar tas emot. Totalt _ *_NX_ARP_MAXIMUM_RETRIES_** ARP-begäranden görs innan ARP-försöket överges. När ett ARP-svar tas emot lagras den associerade fysiska adress informationen i ARP-posten i cacheminnet.

För multihome-system bestämmer NetX vilket gränssnitt som ska skicka ARP-förfrågningar och svar baserat på den angivna mål adressen.

> [!IMPORTANT]
> *Utgående IP-paket köas när netx väntar på ARP-svaret. Antalet utgående IP-* *paket i kö definieras av konstanten*  * **NX_ARP_MAX_QUEUE_DEPTH**. *

NetX svarar också på ARP-förfrågningar från andra noder i det lokala IP-nätverket. När en extern ARP-begäran görs som matchar den aktuella IP-adressen för det gränssnitt som tar emot ARP-begäran, skapar NetX ett ARP-svarsmeddelande som innehåller den aktuella fysiska adressen.

Formatet på Ethernet ARP-begäranden och-svar visas i bild 6 och beskrivs nedan:

| Fråge-/svars fält       | Syfte    |
|------------------------------|-----------------|
| Ethernet-mål adress | Detta 6-byte-fält innehåller mål adressen för ARP-svaret och är en sändning (alla) för ARP-förfrågningar. Det här fältet ställs in av nätverks driv rutinen. |
| Ethernet-källans adress      | Detta 6-byte-fält innehåller adressen till avsändaren av ARP-begäran eller-svaret och har kon figurer ATS av nätverks driv rutinen. |
| Ramtyp                   | Detta fält i 2 byte innehåller typen av Ethernet-ram som finns och, för ARP-förfrågningar och svar, detta är lika med 0x0806. Detta är det sista fältet som nätverks driv rutinen ansvarar för att konfigurera. |
| Maskin varu typ                | Detta fält i 2 byte innehåller maskin varu typen, som är 0x0001 för Ethernet. |
| Protokoll typ                | Detta fält i 2 byte innehåller protokoll typen, som är 0x0800 för IP-adresser. |
| Maskin varu storlek                | Det här 1-byte fältet innehåller maskin varu adressens storlek, som är 6 för Ethernet-adresser. |


![ARP-paketfilter](./media/user-guide/arp-packet-format.png)

**BILD 6. ARP-paketfilter**

| Fråge-/svars fält | Syfte  |
|---|---|
| Protokoll storlek | Detta 1-byte-fält innehåller IP-adressens storlek, som är 4 för IP-adresser.  |
| Åtgärds kod | Detta fält i 2 byte innehåller åtgärden för det här ARP-paketet. En ARP-begäran anges med värdet 0x0001, medan ett ARP-svar representeras av värdet 0x0002.  |
| Avsändarens Ethernet-adress | Det här 6-byte-fältet innehåller avsändarens Ethernet-adress. |
| Avsändarens IP-adress | Detta fält med fyra byte innehåller avsändarens IP-adress. |
| Mål-Ethernet-adress | Detta 6-byte-fält innehåller målets Ethernet-adress. |
| Mål-IP-adress | Detta fält i 4 byte innehåller målets IP-adress. |

> [!IMPORTANT]
> *ARP-förfrågningar och-svar är paket med Ethernet-nivå. Alla andra TCP/IP-paket kapslas in av ett IP-pakets huvud.*

> [!IMPORTANT]
> *Alla ARP-meddelanden i TCP/IP-implementeringen förväntas vara i big endian format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen.*

### <a name="arp-aging"></a>ARP-åldrande

NetX stöder automatisk ogiltig dynamisk ARP-post. ***NX_ARP_EXPIRATION_RATE** _specifies antalet sekunder som en upprättad IP-adress till fysisk mappning fortfarande är giltig. Efter förfallo datum tas ARP-posten bort från ARP-cachen. Nästa försök att skicka till motsvarande IP-adress leder till en ny ARP-begäran. Om du anger _ *_NX_ARP_EXPIRATION_RATE_** till noll inaktive ras ARP-åldrande, vilket är standard konfigurationen.

### <a name="arp-defend"></a>ARP-försvara

När en ARP-begäran eller ett ARP-svars paket tas emot och avsändaren har samma IP-adress, som står i konflikt med IP-adressen för den här noden, skickar NetX en ARP-begäran för den adressen som försvars tid. Om ett konflikt-ARP-paket tas emot mer än en gång om 10 sekunder, skickar NetX inte fler försvarande paket. Standard intervallet på 10 sekunder kan omdefinieras med ***NX_ARP_DEFEND_INTERVAL** _. Det här beteendet följer principen som anges i 2.4 (c) av RFC5227. Eftersom Windows XP ignorerar ARP-meddelande som ett svar för sin ARP-avsökning kan användaren definiera _ *_NX_ARP_DEFEND_BY_REPLY_* * för att skicka ARP-svar som ytterligare försvar.

### <a name="arp-statistics-and-errors"></a>ARP-statistik och fel

Om den är aktive rad håller NetX ARP-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter underhålls för varje IP-ARP-bearbetning:

- Totalt antal skickade ARP-begäranden
- Totalt antal mottagna ARP-begäranden
- Totalt antal skickade ARP-svar
- Totalt antal mottagna ARP-svar
- Totalt antal dynamiska ARP-poster
- Totalt antal statiska ARP-poster
- Totalt antal inaktuella ARP-poster
- Totalt antal ogiltiga ARP-meddelanden

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med tjänsten ***nx_arp_info_get*** .

## <a name="reverse-address-resolution-protocol-rarp-in-ip"></a>RARP (reversed Address Resolution Protocol) i IP

RARP (reversed Address Resolution Protocol) är protokollet för att begära nätverks tilldelning av värdens 32-bitars IP-adresser (RFC 903). Detta görs via en RARP-begäran och fortsätter regelbundet tills en nätverks medlem tilldelar en IP-adress till värd nätverks gränssnittet i ett RARP-svar. Programmet skapar en IP-instans av tjänsten ***nx_ip_create*** med en noll IP-adress. Om RARP har Aktiver ATS av programmet kan det använda RARP-protokollet för att begära en IP-adress från nätverks servern som är tillgänglig via gränssnittet som har en noll IP-adress.

### <a name="rarp-enable"></a>Aktivera RARP

Om du vill använda RARP måste programmet skapa IP-instansen med en IP-adress som är noll och sedan aktivera RARP med hjälp av tjänsten ***nx_rarp_enable***. För flera hem system måste minst en nätverks enhet som är associerad med IP-instansen ha en IP-adress som är noll. RARP-bearbetningen skickar regelbundet RARP begär Anden för NetX-systemet som kräver en IP-adress tills ett giltigt RARP-svar med den angivna IP-adressen för nätverket tas emot. I det här läget är RARP-bearbetningen klar.

När RARP har Aktiver ATS inaktive ras den automatiskt när alla gränssnitts adresser har lösts. Programmet kan tvinga RARP att avslutas genom att använda tjänsten ***nx_rarp_disable***.

###  <a name="rarp-request"></a>RARP-begäran

Formatet på ett RARP begär ande paket är nästan identiskt med ARP-paketet som visas i bild 6 i avsnittet om [ARP-meddelanden](#arp-messages). Den enda skillnaden är att fältet ramtyp är 0x8035 och fältet *Åtgärds kod* är 3, vilket anger en RARP-begäran. Som tidigare nämnts kommer RARP-begäranden att skickas regelbundet (var ***NX_RARP_UPDATE_RATE*** sekund) tills ett RARP-svar med den tilldelade IP-adressen för nätverket tas emot.

> [!IMPORTANT]
> *Alla RARP-meddelanden i TCP/IP-implementeringen förväntas vara i big endian format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen.*

### <a name="rarp-reply"></a>RARP-svar

RARP svarsmeddelanden tas emot från nätverket och innehåller den nätverks tilldelade IP-adressen för den här värden. Formatet på ett RARP Reply-paket är nästan identiskt med ARP-paketet som visas i bild 6. Den enda skillnaden är att fältet ramtyp är 0x8035 och fältet *Åtgärds kod* är 4, vilket anger ett RARP-svar. När den har tagits emot är IP-adressen konfigurerad i IP-instansen, den periodiska RARP-begäran är inaktive rad och IP-instansen är nu klar för normal nätverks drift.

För multihome-värdar tillämpas IP-adressen på det begärda nätverks gränssnittet. Om det fortfarande finns andra nätverks gränssnitt som begär en tilldelning av IP-adresser, fortsätter den periodiska RARP-tjänsten tills alla IP-begäranden för IP-adresser är lösta.

> [!IMPORTANT]
> *Programmet ska inte använda IP-instansen förrän RARP-bearbetningen har slutförts. **Nx_ip_status_check** kan användas av program för att vänta på att RARP slutförs. För multihome-system ska programmet inte använda det begärda gränssnittet förrän RARP-bearbetningen har slutförts på det gränssnittet. Status för IP-adressen på den sekundära enheten kan kontrol leras med tjänsten **nx_ip_interface_status_check** .*

### <a name="rarp-statistics-and-errors"></a>RARP statistik och fel

Om den är aktive rad håller NetX RARP-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter underhålls för varje IP-RARP bearbetning:

- Totalt antal skickade RARP-begäranden
- Totalt antal mottagna RARP-svar
- Totalt antal RARP ogiltiga meddelanden

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med tjänsten ***nx_rarp_info_get*** .

## <a name="internet-control-message-protocol-icmp"></a>Internet Control Message Protocol (ICMP)

Internet Control Message Protocol för IP (ICMP) är begränsad till överföring av fel och kontroll av information mellan IP-medlemmar.

Precis som de flesta andra program skikt (t. ex. TCP/IP-meddelanden) kapslas ICMP-meddelanden av ett IP-huvud med ICMP-protokollets beteckning.

### <a name="icmp-statistics-and-errors"></a>ICMP-statistik och fel

Om aktive rad håller NetX koll på flera ICMP-statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter hanteras för varje IP-ICMP-bearbetning:

- Totalt antal ICMP-pingar som skickats
- Totalt antal ICMP-Ping-Timeoutar
- Totalt antal inaktiverade ICMP Ping-trådar
- Totalt antal mottagna ICMP ping-svar
- Totalt antal fel i ICMP-kontrollsumma
- Totalt antal ICMP-ohanterade meddelanden

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med tjänsten ***nx_icmp_info_get*** .

### <a name="icmp-enable"></a>ICMP-aktivering
Innan ICMP-meddelanden kan bearbetas av NetX måste programmet anropa tjänsten ***nx_icmp_enable*** för att aktivera ICMP-bearbetning. När det är färdigt kan programmet utfärda ping-begäranden och fält inkommande ping-paket.

### <a name="icmp-echo-request"></a>ICMP-ekobegäran
En ekobegäran är en typ av ICMP-meddelanden som vanligt vis används för att kontrol lera om det finns en speciell nod i nätverket, som identifieras av dess värd-IP-adress. Det populära Ping-kommandot implementeras med ICMP Echo Request/Echo Reply-meddelanden. Om den aktuella värden finns, bearbetar dess nätverks stack ping-begäran och svaren med ett ping-svar. Bild 7 information om ICMP Ping Message-formatet.

![ICMP ping-meddelande](./media/user-guide/icmp-ping-message.png)

**BILD 7. ICMP ping-meddelande**

> [!IMPORTANT]
> *Alla ICMP-meddelanden i TCP/IP-implementeringen förväntas vara i big endian format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen.*

I följande tabell beskrivs ICMP-huvudets format:

| Rubrik fält    | Syfte |
|-----------------|---------------------------------------------------|
| Typ            | I det här fältet anges ICMP-meddelandet (bitar 31-24). De vanligaste är: 0 Echo Reply 8 ECHO förfrågan |
| Kod            | Det här fältet är Sammanhangs beroende av typ fältet (bitar 23-16). För en ekobegäran eller svara har koden värdet noll. |
| Kontrollsumma        | Det här fältet innehåller 16-bitars kontroll summa för den enda komplement summan av ICMP-meddelandet, inklusive hela ICMP-huvudet som börjar med fältet typ. Innan du genererar kontroll summan rensas fältet kontroll summa.                 |
| Identification  | Det här fältet innehåller ett ID-värde som identifierar värden. en värd ska använda det ID som extraheras från en EKOBEGÄRAN i eko svaret (bitar 31-16). |
| Sekvensnummer | Det här fältet innehåller ett ID-värde; en värd ska använda det ID som extraheras från en EKOBEGÄRAN i eko svaret (bitar 31-16). Till skillnad från fältet identifierare kommer det här värdet att ändras i en efterföljande ekobegäran från samma värd (bitar 15-0). |


### <a name="icmp-echo-response"></a>ICMP Echo svar
Ett ping-svar är en annan typ av ICMP-meddelanden som genereras internt av ICMP-komponenten som svar på en extern ping-begäran. Utöver bekräftelsen innehåller ping-svaret även en kopia av de användar data som angavs i ping-begäran.

## <a name="internet-group-management-protocol-igmp"></a>Internet Grupphanteringsprotokoll (IGMP)

IGMP (Internet Group Management Protocol) tillhandahåller en enhet för att kommunicera med sina grannar och dess routrar som den avser att ta emot, eller ansluta till, en IP-multicast-grupp (RFC 1112 och RFC 2236). En multicast-grupp är i princip en dynamisk uppsättning nätverks medlemmar och representeras av en klass D IP-adress. Medlemmar i multicast-gruppen kan lämna när som helst och nya medlemmar kan gå med i taget. Den samordning som används för att ansluta till och lämna gruppen är ansvaret för IGMP.

### <a name="igmp-enable"></a>Aktivera IGMP

Innan en multicasting-aktivitet kan ske i NetX måste programmet anropa tjänsten ***nx_igmp_enable*** . Den här tjänsten utför grundläggande IGMP-initiering som förberedelse för multicast-begäranden.

### <a name="multicast-ip-addressing"></a>Multicast-IP-adressering

Som tidigare nämnts är multicast-adresser faktiskt klass D IP-adresser som visas i bild 4 på sidan 58. De nedre 28 bitarna i klass D-adressen motsvarar multicast-gruppens ID. Det finns en serie fördefinierade multicast-adresser. Men *alla värd adresser* (244.0.0.1) är särskilt viktiga för IGMP-bearbetning. *Adressen alla värdar* används av routrar för att fråga alla multicast-medlemmar att rapportera om vilka multicast-grupper de tillhör.

### <a name="physical-address-mapping-in-ip"></a>Fysisk adress mappning i IP

Klass D multicast-adresser mappas direkt till fysiska Ethernet-adresser som sträcker sig från 01.00.5 e. 00.00.00 till 01.00.5 e. 7f. AA. AA. De lägre 23 bitarna av IP-multicast-adress kartan direkt till de lägre 23 bitarna av Ethernet-adressen.

### <a name="multicast-group-join"></a>Anslutning till multicast-grupp

Program som behöver ansluta till en viss multicast-grupp kan göra detta genom att anropa tjänsten ***nx_igmp_multicast_join*** . Den här tjänsten håller reda på antalet begär Anden att ansluta till den här multicast-gruppen. Om det här är den första program förfrågan för att ansluta till multicast-gruppen skickas en IGMP-rapport ut från det primära nätverket som anger att den här värdens avsikt att ansluta till gruppen. Därefter anropas nätverks driv rutinen för att ställa in för att lyssna efter paket med Ethernet-adressen för den här multicast-gruppen.

Om multicast-gruppen är tillgänglig via ett visst gränssnitt i ett multihome-system använder programmet tjänsten ***nx_igmp_multicast_interface_join*** i stället för ***nx_igmp_multicast_join**, * som är begränsat till multicast-grupper i det primära nätverket.

### <a name="multicast-group-leave"></a>Lämna multicast-grupp

Program som måste lämna en tidigare ansluten multicast-grupp kan göra det genom att anropa tjänsten ***nx_igmp_multicast_leave*** . Den här tjänsten minskar det interna antalet som är associerat med hur många gånger gruppen anslöts. Om det inte finns några utestående kopplings begär Anden för en grupp, anropas nätverks driv rutinen för att inaktivera lyssning av paket med multicast-gruppens Ethernet-adress

### <a name="multicast-loopback"></a>Multicast-loopback

Ett program kan vilja ta emot multicast-trafik som härstammar från en av källorna på samma nod. För detta krävs att loopback aktive ras av IP-multicast-komponenten med hjälp av tjänsten ***nx_igmp_loopback_enable***.

### <a name="igmp-report-message"></a>IGMP-rapport meddelande

När programmet ansluter till en multicast-grupp skickas ett IGMP-rapport meddelande via nätverket för att indikera värddatorns avsikt att ansluta till en viss multicast-grupp. Formatet på IGMP-rapportens meddelande visas i bild 8. Multicast-gruppadressen används för både grupp meddelandet i IGMP-rapport meddelandet och mål-IP-adressen.

![IGMP-rapport meddelande](./media/user-guide/igmp-report-message.png)

**FIGUR 8. IGMP-rapport meddelande**

I bilden ovan (bild 8) innehåller IGMP-huvudet ett fält av version/typ, maximal svars tid, ett fält för kontroll summa och ett adress fält för multicast-gruppen. För IGMPv1-meddelanden är fältet maximal svars tid alltid inställt på noll, eftersom detta inte är en del av IGMPv1-protokollet. Fältet Max svars tid anges när värden får ett IGMP-meddelande av typen fråga och rensas när en värd får ett annat värde för rapport typ meddelandet som definieras av IGMPv2-protokollet.

I följande avsnitt beskrivs IGMP-huvud formatet:

| **Rubrik fält**          | **Syfte** |
|-----------------------|--------------------------------------------------------------------|
| Version               | Det här fältet anger IGMP-versionen (bitar 31-28).                                                                               |
| Typ                  | Det här fältet anger typen av IGMP-meddelande (bitar 27 -24).                                                                       |
| Maximal svars tid | Används inte i IGMPv1. I IGMPv2 används det här fältet som maximal svars tid.                                                      |
| Kontrollsumma              | Det här fältet innehåller 16-bitars kontroll summa för den enda komplement summan av IGMP-meddelandet som börjar med IGMP-versionen (bitar 0-15) |
| Grupp adress         | 32-bitars klass D grupp IP-adress |


IGMP-rapport meddelanden skickas också som svar på IGMP-frågemeddelanden som skickas av en multicast-router. Multicast-routrar skickar regelbundet frågemeddelanden ut för att se vilka värdar som fortfarande kräver grupp medlemskap. Fråga meddelanden har samma format som IGMP-rapport meddelandet som visas i bild 8. De enda skillnaderna är att IGMP-typen är lika med 1 och att grupp adress fältet är inställt på 0. IGMP-frågemeddelanden skickas till IP-adressen *alla värdar* av multicast-routern. En värd som fortfarande vill behålla grupp medlemskapet svarar genom att skicka ett annat IGMP-rapport meddelande.

> [!IMPORTANT]
> *Alla meddelanden i TCP/IP-implementeringen förväntas vara i **big endian** format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen.*

### <a name="igmp-statistics-and-errors"></a>IGMP-statistik och fel

Om den är aktive rad håller NetX IGMP-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter underhålls för varje IP-IGMP-bearbetning:

- Totalt antal skickade IGMP-rapporter
- Totalt antal mottagna IGMP-frågor
- Totalt antal fel i IGMP-kontrollsumma
- Totalt antal IGMP-aktuella grupper anslutna

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med tjänsten ***nx_igmp_info_get*** .

## <a name="user-datagram-protocol-udp"></a>UDP (User Datagram Protocol)

UDP (User Datagram Protocol) ger den enklaste formen av data överföring mellan nätverks medlemmar (RFC 768). UDP-datapaket skickas från en nätverks medlem till en annan på bästa möjliga sätt. Det finns alltså ingen inbyggd mekanism för bekräftelse av paket mottagaren. Att skicka ett UDP-paket kräver dessutom inte att någon anslutning upprättas i förväg. Därför är det mycket effektivt att överföra UDP-paket.

### <a name="udp-header"></a>UDP-huvud
UDP placerar ett enkelt paket huvud framför programmets data vid överföring och tar bort ett liknande UDP-huvud från paketet vid mottagning innan ett mottaget UDP-paket levereras till programmet. UDP använder IP-protokollet för att skicka och ta emot paket, vilket innebär att det finns ett IP-huvud framför UDP-huvudet när paketet är i nätverket. Bild 9 visar UDP-huvudets format.

![UDP-huvud](./media/user-guide/udp-header.png)

**BILD 9. UDP-huvud**

> [!IMPORTANT]
> *Alla rubriker i UDP/IP-implementeringen förväntas vara i big endian format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen.*

I följande avsnitt beskrivs UDP-huvudets format:

| Rubrik fält                   | Syfte |
|--------------------------------|---------------------------------------------|
| 16-bitars käll port nummer      | Det här fältet innehåller porten som UDP-paketet skickas från. Giltiga UDP-portar sträcker sig från 1 till 0xFFFF. |
| 16-bitars mål port nummer | Det här fältet innehåller den UDP-port som paketet skickas till. Giltiga UDP-portar sträcker sig från 1 till 0xFFFF.   |
| 16-bitars UDP-längd   | Det här fältet innehåller antalet byte i UDP-paketet, inklusive storleken på UDP-huvudet.                                  |
| 16-bitars UDP-kontrollsumma | Det här fältet innehåller 16-bitars kontroll summa för paketet, inklusive UDP-huvudet, paket data området och pseudo-IP-huvudet. |

### <a name="udp-enable"></a>Aktivera UDP

Innan överföring av UDP-paket är möjligt måste programmet först aktivera UDP genom att anropa tjänsten ***nx_udp_enable*** . När det har Aktiver ATS är programmet fritt att skicka och ta emot UDP-paket.

### <a name="udp-socket-create"></a>Skapa UDP-socket

UDP-Sockets skapas antingen under initieringen eller under körningen av program trådar. Den första typen av tjänst, Time to Live och Receive Queue djup definieras av tjänsten ***nx_udp_socket_create*** . Det finns ingen gräns för antalet UDP-socketar i ett program.

### <a name="udp-checksum"></a>UDP-kontrollsumma

UDP anger en komplett 16-bitars kontroll summa som täcker IP-pseudo-huvudet (som består av käll-IP-adressen, målets IP-adress och protokoll/längd-IP-adress), UDP-huvudet och UDP-paketets data. Om den beräknade UDP-kontrollsumman är 0 lagras den som alla (0xFFFF). Om inaktive ring av UDP-kontrollsumma är inaktive rad placeras noll i fältet UDP-kontrollsumma för att indikera att kontroll summan inte har beräknats. Om UDP-kontrollsumma inte matchar den beräknade kontroll summan av mottagaren, ignoreras UDP-paketet helt enkelt.

I IP-nätverket är UDP-kontrollsumma valfri. NetX gör det möjligt för ett program att aktivera eller inaktivera beräkning av UDP-kontrollsumma per socket. Som standard är logiken för kontroll summa för UDP aktiverat. Programmet kan inaktivera logik för kontroll summa för en viss UDP-socket genom att anropa tjänsten ***nx_udp_socket_checksum_disable*** .

Vissa Ethernet-styrenheter kan generera UDP-kontrollsumma i farten. Om systemet kan använda beräknings funktionen för maskin varu kontroll summa kan NetX-biblioteket skapas utan logik för kontroll summa. Om du vill inaktivera kontroll summa för UDP-programvara måste NetX-biblioteket skapas med följande symboler: ***NX_DISABLE_UDP_TX_CHECKSUM*** och ***NX_DISABLE_UDP_RX_CHECKSUM **_ (beskrivs i [kapitel 2](chapter2.md)). Konfigurations alternativen tar bort den logiska kontroll summan för UDP från NetX helt, samtidigt som anropet _* nx_udp_socket_checksum_disable*** -tjänsten gör det möjligt för programmet att inaktivera bearbetning av IP UDP-kontrollsumma per socket.

### <a name="udp-ports-and-binding"></a>UDP-portar och bindning

En UDP-port är en logisk slut punkt i UDP-protokollet. Det finns 65 535 giltiga portar i UDP-komponenten NetX, från 1 till 0xFFFF. Om du vill skicka eller ta emot UDP-data måste programmet först skapa en UDP-socket och sedan binda den till en önskad port. När du har bundit en UDP-socket till en port kan programmet skicka och ta emot data på denna socket.

### <a name="udp-fast-pathtrade"></a>Snabb sökväg för UDP&trade;

Snabb sökvägen för UDP &trade; är namnet på en låg paket väg genom netx UDP-implementering. Att skicka ett UDP-paket kräver bara några funktions anrop: ***nx_udp_socket_send** _, _*_nx_ip_packet_send_*_ och det eventuella anropet till nätverks driv rutinen. _*_nx_udp_socket_send_*_ är tillgängligt i netx för befintliga netx-program och gäller endast för IP-paket. Den bästa metoden är dock att använda _ *_nx_udp_socket_send_** tjänsten som diskuteras nedan. Vid mottagning av UDP-paket placeras UDP-paketet antingen på lämplig UDP socket Receive-kö eller levereras till en inaktive rad program tråd i ett enda funktions anrop från nätverks driv Rutinens mottagnings bearbetning. Den här mycket optimerade logiken för att skicka och ta emot UDP-paket är grunden för en snabb väg teknik för UDP.

### <a name="udp-packet-send"></a>Skicka UDP-paket

Att skicka UDP-data via IP-nätverk kan enkelt utföras genom att anropa funktionen ***nx_udp_socket_send** _. Anroparen måste ange IP-versionen i fältet _IP-adress *. NetX kommer att avgöra den bästa käll adressen för överförda UDP-paket baserat på mål-IP-adressen. Den här tjänsten placerar ett UDP-huvud framför paket data och skickar det till nätverket med en intern IP-sändnings rutin. Det finns ingen tråd Inskjutning vid sändning av UDP-paket eftersom alla UDP-paketfiltrering bearbetas omedelbart.

För multicast-eller broadcast-mål ska programmet ange vilken käll-IP-adress som ska användas om NetX-enheten har flera IP-adresser att välja mellan. Detta kan göras med tjänsterna ***nx_udp_socket_interface_send.***

> [!IMPORTANT]
> *Om **nx_udp_socket_send** används för att överföra multicast-eller broadcast-paket används IP-adressen för det första gränssnittet som käll adress.*

> [!IMPORTANT]
> *Om logics kontroll summa för UDP är aktive rad för denna socket utförs åtgärden för kontroll summa i kontexten för den anropande tråden, utan att blockera åtkomst till UDP-eller IP-datastrukturerna.*

> [!NOTE]
> *De UDP-nyttolaster som finns i **NX_PACKETs** strukturen bör finnas på ett långt ord. Programmet måste lämna tillräckligt med utrymme mellan lägga-pekaren och data start pekaren för att NetX ska kunna placera både UDP-, IP-och fysiska medie huvudena.*

### <a name="udp-packet-receive"></a>Mottagning av UDP-paket

Program trådar kan ta emot UDP-paket från en viss socket genom att anropa ***nx_udp_socket_receive***. Funktionen Receive Receive levererar det äldsta paketet i socketens mottagnings kön. Om det inte finns några paket i mottagnings kön kan den anropande tråden skjuta upp (med en valfri tids gräns) tills ett paket tas emot.

Bearbetningen av UDP Receive-paket (som vanligt vis anropas från nätverks driv Rutinens avbrotts hanterare) är ansvarig för att antingen placera paketet på UDP-socketens mottagnings kö eller leverera den till den första pausade tråden för ett paket. Om paketet är i kö, kontrollerar Receive-bearbetningen även det maximala mottagnings ködjup som är associerat med socketen. Om det nyligen köade paketet överskrider ködjup, ignoreras det äldsta paketet i kön.

### <a name="udp-receive-notify"></a>Mottagnings meddelande för UDP

Om program tråden behöver bearbeta mottagna data från fler än en socket ska funktionen ***nx_udp_socket_receive_notify*** användas. Den här funktionen registrerar en motringnings funktion för mottagnings paket för socketen. När ett paket tas emot på socketen körs motringningsfunktionen.

Innehållet i motringningsfunktionen är programspecifikt. Det skulle dock förmodligen innehålla logik för att informera bearbetnings tråden att ett paket nu är tillgängligt på motsvarande socket.

### <a name="peer-address-and-port"></a>Peer-adress och port

Vid mottagning av ett UDP-paket kan programmet hitta avsändarens IP-adress och port nummer med hjälp av tjänsten ***nx_udp_packet_info_extract***. Vid lyckad återgång tillhandahåller den här tjänsten information om avsändarens IP-adress, avsändarens port nummer och det lokala gränssnitt som paketet togs emot via.

### <a name="thread-suspension"></a>Tråd upphängning

Som tidigare nämnts kan program trådar pausa vid försök att ta emot ett UDP-paket på en viss UDP-port. När ett paket har mottagits på den porten, tilldelas den första tråden inaktive rad och tråden återupptas sedan. En valfri timeout är tillgänglig när du pausar ett UDP Receive-paket, en funktion som är tillgänglig för de flesta NetX-tjänster.

### <a name="udp-socket-statistics-and-errors"></a>Statistik och fel för UDP-socket

Om den är aktive rad håller NetX UDP-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter upprätthålls för varje IP/UDP-instans:

- Totalt antal skickade UDP-paket
- Totalt antal skickade UDP-byte
- Totalt antal mottagna UDP-paket
- Totalt antal mottagna UDP-byte
- Totalt antal ogiltiga UDP-paket
- Totalt antal mottagna UDP-paket
- Totalt antal UDP mottagnings kontroll Summa fel
- Skickade UDP-socket-paket
- Skickade UDP-socket-byte
- Mottagna UDP-socket-paket
- Mottagna UDP-socket byte
- Köade UDP-socket-paket
- Mottagna paket för UDP-socket tas bort
- Fel vid kontroll summa för UDP-socket

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med ***nx_udp_info_get*** tjänsten för UDP-amassed över alla UDP-socketar och ***nx_udp_socket_info_get*** -tjänsten för UDP-statistik på den angivna UDP-socketen.

### <a name="udp-socket-control-block-nx_udp_socket"></a>UDP socket Control Block NX_UDP_SOCKET

Egenskaperna för varje UDP-socket finns i det associerade **NX_UDP_SOCKET** kontroll blocket. Den innehåller användbar information, till exempel länken till IP-datastrukturen, nätverks gränssnittet för att skicka och ta emot sökvägar, den kopplade porten och kön för mottagnings paket. Den här strukturen definieras i filen **_nx_api. h_** .

## <a name="transmission-control-protocol-tcp"></a>Transmission Control Protocol (TCP)

Transmission Control Protocol (TCP) ger tillförlitlig data överföring mellan två nätverks medlemmar (RFC 793). Alla data som skickas från en nätverks medlem verifieras och bekräftas av den mottagande medlemmen. Dessutom måste de två medlemmarna ha upprättat en anslutning före en data överföring. Allt detta resulterar i tillförlitlig data överföring. Det kräver dock betydligt mer belastning än den tidigare beskrivna UDP-dataöverföringen.

### <a name="tcp-header"></a>TCP-huvud

Vid överföring placeras TCP-huvud framför data från användaren. Vid mottagning tas TCP-huvud bort från det inkommande paketet, och endast de användar data som är tillgängliga för programmet lämnas kvar. TCP använder IP-protokollet för att skicka och ta emot paket, vilket innebär att det finns ett IP-huvud framför TCP-huvudet när paketet är i nätverket. Bild 10 visar formatet för TCP-sidhuvudet.

![TCP-huvud](./media/user-guide/tcp-header.png)

**BILD 10. TCP-huvud**

I följande avsnitt beskrivs formatet TCP-huvud:

| Rubrik fält | Syfte |
|---|---|
| 16-bitars käll port nummer | Det här fältet innehåller den port som TCP-paketet skickas till. Giltiga TCP-portar är mellan 1 och 0Xffffffff. |
| 16-bitars mål port nummer | Det här fältet innehåller TCP-porten som paketet skickas till. Giltiga TCP-portar är mellan 1 och 0Xffffffff. |
| 32-bitars sekvensnummer | Det här fältet innehåller sekvensnumret för data som skickas från det här slutet av anslutningen. Den ursprungliga sekvensen upprättas under den inledande anslutnings ordningen mellan två TCP-noder. Varje data överföring från den punkten resulterar i en ökning av sekvensnumret med antalet byte som skickats. |
| 32-bitars bekräftelse nummer | Det här fältet innehåller det ordnings nummer som motsvarar den sista mottagna byte som togs emot av anslutningen. Detta används för att avgöra om data som skickats tidigare har tagits emot av den andra änden av anslutningen. |
| 4-bitars rubrik längd           | Det här fältet innehåller antalet 32-bitars ord i TCP-huvudet. Om det inte finns några alternativ i TCP-huvudet är det här fältet 5. |
| 6-bitars kod bitar               | Det här fältet innehåller sex olika kod bitar som används för att ange olika kontroll information som är associerad med anslutningen. Kontroll bitarna definieras enligt följande: |



| Name | Bitmask | Innebörd                                                     |
|------|-----|-------------------------------------------------------------|
| URG  | 21  | Brådskande data finns                                         |
| Följ  | 20  | Bekräftelse numret är giltigt                             |
| PSH  | 19  | Hantera dessa data direkt                                |
| RSTA  | 18  | Återställ anslutningen                                        |
| TILLSTÅNDET  | 17  | Synkronisera sekvensnummer (används för att upprätta anslutning) |
| FIN  | 16  | Avsändaren har slutförts med överföring (används för att stänga anslutningen) |

**16-bitars fönster**

Det här fältet används för flödes kontroll. Det innehåller mängden byte som socketen kan ta emot för närvarande. Detta används i princip för flödes kontroll. Avsändaren ansvarar för att se till att de data som skickas får plats i mottagarens annonserade fönster.

| **Rubrik fält**          | **Syfte** |
| ------------------------- | --- |
| **16-bitars TCP-kontrollsumma**   | Det här fältet innehåller 16-bitars kontroll summa för paketet, inklusive TCP-huvud, paket data området och pseudo-IP-huvudet.                |
| **16-bitars brådskande pekare** | Det här fältet innehåller den positiva förskjutningen för den senaste byten av brådskande data. Det här fältet är endast giltigt om URG-kodfragmentet har angetts i huvudet. |

> [!IMPORTANT]
> *Alla rubriker i TCP/IP-implementeringen förväntas vara i big endian format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen.*

### <a name="tcp-enable"></a>TCP-aktivering

Innan TCP-anslutningar och paket överföring är möjliga måste programmet först aktivera TCP genom att anropa tjänsten nx_tcp_enable. När det har Aktiver ATS är programmet tillgängligt för att få åtkomst till alla TCP-tjänster.

### <a name="tcp-socket-create"></a>Skapa TCP-socket

TCP-Sockets skapas antingen under initieringen eller under körningen av program trådar. Den första typen av tjänst, tid till Live och fönster storlek definieras av tjänsten ***nx_tcp_socket_create*** . Det finns ingen gräns för antalet TCP-Sockets i ett program.

### <a name="tcp-checksum"></a>TCP-kontrollsumma

TCP anger en komplett 16-bitars kontroll summa som täcker IP-pseudo-sidhuvudet (som består av käll-IP-adressen, målets IP-adress och protokoll/längd-IP-adress), TCP-huvudet och TCP-paketets data.

Vissa nätverks styrenheter kan utföra beräkning av TCP-kontrollsumma och verifiering i maskin vara. För sådana system kan program använda sig av logik för maskin varu kontroll så mycket som möjligt för att minska körnings belastningen. Program kan inaktivera beräknings logiken för TCP-kontrollsumma från NetX-biblioteket helt i bygg tiden genom att definiera **NX_DISABLE_TCP_TX_CHECKSUM** och **NX_DISABLE_TCP_RX_CHECKSUM**. På så sätt kompileras inte TCP-kontrollsummats kod i.

### <a name="tcp-port"></a>TCP-port

En TCP-port är en logisk anslutnings punkt i TCP-protokollet. Det finns 65 535 giltiga portar i TCP-komponenten i NetX, mellan 1 och 0xFFFF. Till skillnad från UDP där data från en port kan skickas till en annan målport, är en TCP-port ansluten till en annan angiven TCP-port, och endast när den här anslutningen upprättas kan all data överföring ske, och endast mellan de två portarna som utgör anslutningen.

> [!IMPORTANT]
> *TCP-portar är helt åtskilda från UDP-portar; t. ex. är UDP-port nummer 1 ingen relation till TCP-port nummer 1.*

## <a name="client-server-model"></a>Client-Server modell

Om du vill använda TCP för data överföring måste du först upprätta en anslutning mellan de två TCP-socketarna. Upprättandet av anslutningen görs på en klient-server. Klient sidan av anslutningen är den sida som initierar anslutningen, medan Server sidan bara väntar på klient anslutnings begär Anden innan bearbetningen görs.

> [!IMPORTANT]
> *För multihome-enheter bestämmer NetX automatiskt käll adressen som ska användas för anslutningen och nästa hopp adress baserat på anslutningens mål-IP-adress.*

### <a name="tcp-socket-state-machine"></a>TCP socket State Machine

Anslutningen mellan två TCP-Sockets (en klient och en server) är komplex och hanteras på ett sätt som är en tillstånds dator. Varje TCP-socket startar i ett stängt tillstånd. Via anslutnings händelser varje Sockets tillstånds dator migreras till ett etablerat tillstånd, vilket är den mängd data överföringen i TCP äger rum. När en sida av anslutningen inte längre vill skicka data, kopplas den bort. När den andra sidan kopplas från återgår TCP-socketen till stängt tillstånd. Den här processen upprepas varje gång en TCP-klient och Server upprättar och stänger en anslutning. Bild 11 visar de olika tillstånden för datorn för TCP-tillstånd.

![Tillstånd för TCP-tillstånds dator](./media/user-guide/states-tcp-state-machine.png)

### <a name="figure-11-states-of-the-tcp-state-machine"></a>BILD 11. Tillstånd för TCP-tillstånds dator

### <a name="tcp-client-connection"></a>TCP-klient anslutning

Som tidigare nämnts, initierar klient sidan av TCP-anslutningen en anslutningsbegäran till en TCP-server. Innan en anslutningsbegäran kan göras måste TCP aktive ras på klientens IP-instans. Dessutom måste klienten TCP-socketen sedan skapas med ***nx_tcp_socket_create** _-tjänsten och vara kopplad till en port via tjänsten _*_nx_tcp_client_socket_bind_*_ . När klient-socketen är kopplad, används _ *_nx_tcp_client_socket_connect_**-tjänsten för att upprätta en anslutning till en TCP-server. Observera att socketen måste vara i stängt tillstånd för att ett anslutnings försök ska kunna initieras. Att upprätta anslutningen börjar med NetX som utfärdar ett SYN paket och väntar sedan på ett SYN ACK-paket tillbaka från servern, vilket innebär att anslutningsbegäran tas emot. När SYN-ACK-ACK tas emot svarar NetX med ett ACK-paket och höjer upp klientens socket till tillståndet etablerad.

### <a name="tcp-client-disconnection"></a>TCP-klient från koppling

Att stänga anslutningen uppnås genom att anropa ***nx_tcp_socket_disconnect***. Om ingen uppskjutning har angetts skickar klient-socketen ett för-paket till Server-socketen och placerar socketen i stängt tillstånd. Annars, om en SUS Pension begärs, utförs det fullständiga TCP-från kopplings protokollet enligt följande:

- Om servern tidigare initierade en från kopplings förfrågan (klient-socketen redan har tagit emot ett RÄNTETRANS-paket, svarat på en ACK och är i nära VÄNTe läge), höjer NetX klientens TCP socket State till det senaste bekräftelse stadiet och skickar ett RÄNTETRANS-paket. Den väntar sedan på en bekräftelse från servern innan du slutför från kopplingen och anger det stängda läget.

- Om klienten å andra sidan är den första för att initiera en från kopplings förfrågan (servern har inte kopplats från och socketen fortfarande är i det tillstånd som har ETABLERATs), skickar NetX ett RÄNTETRANS-paket för att initiera från kopplingen och väntar på att ta emot en FIN och en bekräftelse från servern innan du slutför från kopplingen och placera socketen i ett stängt tillstånd.

Om det fortfarande finns paket i kön för överföring av socket pausar NetX under den angivna tids gränsen för att tillåta att paketen kan bekräftas. Om tids gränsen går ut tömmer NetX överförings kön för klientens socket.

Programmet anropar ***nx_tcp_client_socket_unbind*** för att frigöra porten från klientens socket. Socketen måste vara i ett stängt tillstånd eller vid från koppling (t. ex. VÄNTe läge VÄNTe tid) innan porten släpps. annars returneras ett fel.

Slutligen, om programmet inte längre behöver klient-socketen, anropar den ***nx_tcp_socket_delete*** för att ta bort socketen.

### <a name="tcp-server-connection"></a>Anslutning till TCP-server

Server sidan av en TCP-anslutning är passiv; servern väntar alltså på att en klient ska initiera anslutningsbegäran. Om du vill acceptera en klient anslutning måste TCP först vara aktiverat på IP-instansen genom att anropa tjänsten ***nx_tcp_enable** _. Därefter måste programmet skapa en TCP-socket med hjälp av _ *_nx_tcp_socket_create_**-tjänsten.

Server-socketen måste också konfigureras för att lyssna efter anslutnings begär Anden. Detta uppnås med hjälp av tjänsten ***nx_tcp_server_socket_listen*** . Den här tjänsten placerar serverns socket i LYSSNINGs tillstånd och binder den angivna Server porten till socketen.

> [!IMPORTANT]
> *Om du vill ange en utgångs rutin för socket-motringning anger programmet lämplig motringning för argumentet tcp_listen_callback i **nx_tcp_server_socket_listens** tjänsten. Den här program återanrops funktionen körs sedan av NetX när en ny anslutning begärs på den här Server porten. Bearbetningen i återanropet är under program kontroll.*

För att godkänna förfrågningar om klient anslutning anropar programmet ***nx_tcp_server_socket_accept** _-tjänsten. Server-socketen måste antingen vara i ett LYSSNINGs tillstånd eller tillstånd som tagits emot (dvs. servern är i LYSSNINGs tillståndet och har tagit emot ett SYN paket från en klient som begär en anslutning) för att anropa tjänsten accept. En lyckad retur status från _ *_nx_tcp_server_socket_accept_** anger att anslutningen har kon figurer ATS och att serverns socket har tillståndet etablerad.

När Server-socketen har en giltig anslutning, köas ytterligare klient anslutnings begär anden till det djup som anges av *listen_queue_size*, som skickas till ***nx_tcp_server_socket_listen** _-tjänsten. För att kunna bearbeta efterföljande anslutningar på en server port måste programmet anropa _ *_nx_tcp_server_socket_relisten_** med en tillgänglig socket (t. ex. en socket i ett stängt tillstånd). Observera att samma server-socket kan användas om den tidigare anslutningen som är associerad med socketen nu är slutförd och socketen är i stängt tillstånd.

### <a name="tcp-server-disconnection"></a>AvAnslutning av TCP-server

Att stänga anslutningen uppnås genom att anropa ***nx_tcp_socket_disconnect***. Om ingen uppskjutning har angetts skickar Server-socketen ett för-paket till klientens socket och placerar socketen i stängt tillstånd. Annars, om en SUS Pension begärs, utförs det fullständiga TCP-från kopplings protokollet enligt följande: |

- Om klienten tidigare initierade en från kopplings förfrågan (Server-socketen redan har tagit emot ett RÄNTETRANS-paket, svarat på en ACK och är i nära VÄNTe läge), höjer NetX TCP socket State till det senaste bekräftelse stadiet och skickar ett RÄNTETRANS-paket. Den väntar sedan på en bekräftelse från klienten innan du slutför från kopplingen och anger det stängda läget.

- Om servern å andra sidan är den första att initiera en från kopplings förfrågan (klienten har inte kopplats från och att socketen fortfarande är i det tillstånd som har ETABLERATs), skickar NetX ett RÄNTETRANS-paket för att initiera från kopplingen och väntar på att ta emot en FIN och en bekräftelse från klienten innan du slutför från kopplingen och placera socketen i ett stängt tillstånd.

Om det fortfarande finns paket i kön för överföring av socket pausar NetX under den angivna tids gränsen för att tillåta att dessa paket bekräftas. Om tids gränsen går ut tömmer NetX för serverns socket.

När från kopplings bearbetningen har slutförts och Server-socketen är i stängt tillstånd måste programmet anropa tjänsten ***nx_tcp_server_socket_unaccept*** för att avsluta associationen mellan denna socket och Server porten. OBS! den här tjänsten måste anropas av programmet även om ***nx_tcp_socket_disconnect*** eller ***nx_tcp_server_socket_accept** _ returnerar en fel status. När _ *_nx_tcp_server_socket_unaccept_** returnerar kan socketen användas som en klient eller Server-socket, eller till och med tas bort om den inte längre behövs. Om du vill acceptera en annan klient anslutning på samma server port bör ***nx_tcp_server_socket_relisten*** tjänsten anropas på denna socket.

Följande kod segment illustrerar sekvensen av anrop en typisk TCP-server använder:

```c
/* Set up a previously created TCP socket to listen on port 12 */

nx_tcp_server_socket_listen()

/* Loop to make a (another) connection. */
while(1) {

    /* Wait for a client socket connection request for 100 ticks. */
    nx_tcp_server_socket_accept();

    /* (Send and receive TCP messages with the TCP client) */

    /* Disconnect the server socket. */
    nx_tcp_socket_disconnect();

    /* Remove this server socket from listening on the port. */

    nx_tcp_server_socket_unaccept(&server_socket);

    /* Set up server socket to relisten on the same port for the next
    client. */
    nx_tcp_server_socket_relisten();
}
```

### <a name="mss-validation"></a>MSS-verifiering

Maximal segment storlek (MSS) är den maximala mängden byte som en TCP-värd kan ta emot utan att fragmenteras av det underliggande IP-lagret. Under fasen för etablering av TCP-anslutningar, avslutar båda sina egna TCP-MSS-värden, så att avsändaren inte skickar ett TCP-datasegment som är större än mottagarens MSS. NetX TCP-modul kan alternativt validera dess peers annonserade MSS-värde innan en anslutning upprättas. Som standard aktiverar NetX inte någon sådan kontroll. Program som vill utföra MSS-verifieringen måste definiera ***NX_ENABLE_TCP_MSS_CHECKING** _ vid skapande av netx-biblioteket och det minsta värdet måste definieras i _*_NX_TCP_MSS_MINIMUM_*_. Inkommande TCP-anslutningar med MSS-värden under _ *_NX_TCP_MSS_MINIMUM_** ignoreras.

### <a name="stop-listening-on-a-server-port"></a>Stoppa lyssning på en server port

Om programmet inte längre vill lyssna efter klient anslutnings begär Anden på en server port som tidigare angavs av ett anrop till tjänsten ***nx_tcp_server_socket_listen** _, anropar programmet bara tjänsten _ *_nx_tcp_server_socket_unlisten_**. Den här tjänsten placerar en socket i väntan på en anslutning tillbaka i stängt tillstånd och släpper alla paket med köade klient anslutnings begär Anden.

### <a name="tcp-window-size"></a>TCP-fönster storlek

Under både installationen och data överförings faserna i anslutningen, rapporterar varje port mängden data som kan hanteras, vilket kallas dess fönster storlek. När data tas emot och bearbetas justeras den här fönstrets storlek dynamiskt. I TCP kan en sändare bara skicka en mängd data som passar i mottagarens fönster. I själva verket ger fönster storleken flödes kontroll för data överföring i varje riktning i anslutningen.

### <a name="tcp-packet-send"></a>Skicka TCP-paket

Det är enkelt att skicka TCP-data genom att anropa funktionen ***nx_tcp_socket_send*** . Om storleken på de data som överförs är större än MSS-värdet för socketen eller den aktuella peer-mottagande fönster storlek, beroende på vilket som är mindre, är TCP Internal Logic carves av data som passar i min (MSS, peer Receive-fönster) för överföring. Den här tjänsten skapar sedan ett TCP-huvud framför paketet (inklusive beräkning av kontroll summa). Om mottagarens fönster storlek inte är noll, skickar anroparen lika mycket data som det kan fylla i mottagarens fönster storlek. Om mottagnings fönstret blir noll kan anroparen pausa och vänta tills mottagarens fönster storlek ökar tillräckligt för att det här paketet ska skickas. Vid en specifik tidpunkt kan flera trådar pausas vid försök att skicka data via samma socket.

> [!IMPORTANT]
> *De TCP-data som finns i NX_PACKETs strukturen bör finnas på en lång ord linje. Dessutom måste det finnas tillräckligt med utrymme mellan lägga-pekaren och data start pekaren för att placera rubrikerna TCP, IP och fysisk media.*

### <a name="tcp-packet-retransmit"></a>Återsändning av TCP-paket

Tidigare skickade TCP-paket som faktiskt lagrats internt tills en ACK returneras från den andra sidan av anslutningen. Om överförda data inte har bekräftats inom tids gränsen, skickas det lagrade paketet igen och nästa timeout-period anges. När en ACK tas emot släpps slutligen alla paket som omfattas av bekräftelse numret i den interna överförings kön.

> [!IMPORTANT]
> * Programmet får inte återanvända paketet eller ändra paketets innehåll efter att funktionen ***nx_tcp_socket_send** _ returnerar med NX_SUCCESS. Det överförda paketet släpps slutligen genom intern bearbetning av NetX när data har godkänts av den andra end._

### <a name="tcp-keepalive"></a>TCP keepalive

TCP keepalive-funktionen gör det möjligt för en socket att identifiera om dess peer-kopplas bort utan korrekt avslutning (t. ex. om motparten har kraschat) eller för att förhindra vissa nätverks övervaknings anläggningar att avsluta en anslutning under långa perioder av inaktivitet. TCP keepalive fungerar genom att regelbundet skicka en TCP-ram utan data, och sekvensnumret anges till ett lägre värde än det aktuella sekvensnumret. När en sådan TCP keepalive-ram tas emot, kan mottagaren, om den fortfarande är aktiv, svara med ett ACK-värde för det aktuella sekvensnumret. Detta slutför keepalive-transaktionen.

Som standard är keepalive-funktionen inte aktive rad. Om du vill använda den här funktionen måste NetX-biblioteket skapas med ***NX_ENABLE_TCP_KEEPALIVE** _ definieras. Symbolen _ *_NX_TCP_KEEPALIVE_INITIAL_** anger antalet sekunder av inaktivitet innan keepalive-ramen initieras.

### <a name="tcp-packet-receive"></a>Mottagning av TCP-paket

TCP Receive-paketets bearbetning (anropas från IP-hjälpens tråd) ansvarar för hantering av olika anslutnings-och från kopplings åtgärder samt överföring av bekräftelse bearbetning. Dessutom ansvarar TCP Receive Packet-bearbetningen för att placera paket med ta emot data på rätt TCP-Sockets mottagande kö eller leverera paketet till den första pausade tråden som väntar på ett paket.

### <a name="tcp-receive-notify"></a>TCP Receive-avisering

Om program tråden behöver bearbeta mottagna data från fler än en socket ska funktionen ***nx_tcp_socket_receive_notify*** användas. Den här funktionen registrerar en motringnings funktion för mottagnings paket för socketen. När ett paket tas emot på socketen körs motringningsfunktionen.

Innehållet i motringningsfunktionen är programspecifikt. funktionen skulle dock förmodligen innehålla logik för att informera bearbetnings tråden att ett paket är tillgängligt på motsvarande socket.

### <a name="thread-suspension"></a>Tråd upphängning

Som tidigare nämnts kan program trådar pausa vid försök att ta emot data från en viss TCP-port. När ett paket har mottagits på den porten, tilldelas den första tråden inaktive rad och tråden återupptas sedan. En valfri timeout är tillgänglig när du pausar ett TCP Receive-paket, en funktion som är tillgänglig för de flesta NetX-tjänster.

Tråd upphängning är också tillgängligt för anslutning (både klient och Server), klient bindning och från kopplings tjänster.

### <a name="tcp-socket-statistics-and-errors"></a>TCP-socket statistik och fel

Om den här inställningen är aktive rad håller NetX TCP socket Track-baserad på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter underhålls för varje IP/TCP-instans:

- Totalt antal skickade TCP-paket
- Totalt antal skickade TCP-byte
- Totalt antal mottagna TCP-paket
- Totalt antal mottagna TCP-byte
- Totalt antal ogiltiga TCP-paket
- Totalt antal borttagna TCP-mottagna paket
- Totalt antal fel i TCP Receive-kontrollsumma
- Totalt antal TCP-anslutningar
- Totalt antal TCP-anslutningar
- Totalt antal borttagna TCP-anslutningar
- Totalt antal återsändningar av TCP-paket
- Skickade TCP-socket-paket
- Skickade TCP-socket-byte
- Mottagna TCP-socket-paket
- Mottagna TCP-socket-byte
- Återsändning av TCP-socket-paket
- TCP-socket-paket i kö
- Fel vid kontroll summa för TCP-socket
- TCP-socket-tillstånd
- Djup i överförings kön för TCP-socket
- Överförings fönster storlek för TCP-socket
- TCP-Sockets mottagnings fönster storlek

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med ***nx_tcp_info_get** _-tjänsten för total TCP-statistik och _ *_nx_tcp_socket_info_get_**-tjänsten för TCP-statistik per socket.

## <a name="tcp-socket-control-block-nx_tcp_socket"></a>TCP socket Control Block NX_TCP_SOCKET

Egenskaperna för varje TCP-socket finns i det associerade *NX_TCP_SOCKET* kontroll blocket som innehåller användbar information, till exempel länken till IP-datastrukturen, nätverks anslutnings gränssnittet, den bundna porten och kön för mottagnings paket. Den här strukturen definieras i filen ***nx_api. h*** .
