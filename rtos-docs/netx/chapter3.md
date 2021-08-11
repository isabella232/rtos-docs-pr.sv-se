---
title: Kapitel 3 – Funktionella komponenter i Azure RTOS NetX
description: Det här kapitlet innehåller en beskrivning av den högpresterande Azure RTOS NetX TCP/IP-stacken ur ett funktionellt perspektiv.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4ebb002bc82d13210acf8db44cafb141d33a1b45fa8710295437e2dd15cbcf22
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784411"
---
# <a name="chapter-3---functional-components-of-azure-rtos-netx"></a>Kapitel 3 – Funktionella komponenter i Azure RTOS NetX

Det här kapitlet innehåller en beskrivning av den högpresterande Azure RTOS NetX TCP/IP-stacken ur ett funktionellt perspektiv. 

## <a name="execution-overview"></a>Körningsöversikt

Det finns fem typer av programkörning i ett NetX-program: initiering, anrop till programgränssnitt, intern IP-tråd, periodiska IP-timers och nätverksdrivrutinen.

> [!IMPORTANT]
> NetX kräver installation av ThreadX och är beroende av dess trådkörning, uppstängning, periodiska timers och ömsesidig exkludering.

### <a name="initialization"></a>Initiering

Tjänsten ***nx_system_initialize** _ måste anropas innan någon annan NetX-tjänst anropas. Systeminitiering kan anropas antingen från ThreadX _ *_tx_application_define_**-rutinen eller från programtrådar.

När ***nx_system_initialize** _ returnerar är systemet redo att skapa paketpooler och IP-instanser. Eftersom skapandet av en IP-instans kräver en standardpaketpool måste det finnas minst en NetX-paketpool innan du skapar en IP-instans. Att skapa paketpooler och IP-instanser tillåts från ThreadX-initieringsfunktionen _ *_tx_application_define_** och från programtrådar.

Internt skapas en IP-instans i två delar. Den första delen görs i kontexten för anroparen, ***antingen från tx_application_define*** eller från en programtråds kontext. Detta inkluderar att konfigurera IP-datastrukturen och skapa olika IP-resurser, inklusive den interna IP-tråden. Den andra delen utförs under den första körningen från den interna IP-tråden. Det är här som nätverksdrivrutinen, som angavs när den första delen av IP-skapandet, först anropas. Genom att anropa nätverksdrivrutinen från den interna IP-tråden kan drivrutinen utföra I/O och pausa under initieringsbearbetningen. När nätverksdrivrutinen återgår från initieringen är IP-skapandet klart.

> [!IMPORTANT]
> NetX-tjänstens **nx_ip_status_check** tillgänglig för att hämta information om IP-instansen och dess primära gränssnittsstatus. Statusinformationen omfattar huruvida länken har initierats, aktiverats och IP-adressen har lösts. Den här informationen används för att synkronisera programtrådar som behöver använda en nyligen skapad IP-instans. För multihome-system, se "Stöd för multihome" nedan. **nx_ip_interface_status_check** tillgänglig för att hämta information om det angivna gränssnittet.

### <a name="application-interface-calls"></a>Anrop till programgränssnitt

Anrop från programmet görs huvudsakligen från programtrådar som körs under ThreadX RTOS. Vissa initierings-, create- och enable-tjänster kan dock anropas ***från tx_application_define***. Avsnitten "Tillåten från" i kapitel 4 anger från vilka varje NetX-tjänst kan anropas.

I de flesta fall utförs bearbetningsintensiva aktiviteter som beräkning av kontrollsumor i den anropande trådens kontext – utan att blockera åtkomsten till andra trådar till IP-instansen. Vid överföring utförs till exempel UDP-kontrollsummaberäkningen i ***nx_udp_socket_send-tjänsten*** innan den underliggande IP-sändningsfunktionen anropas. På ett mottaget paket beräknas UDP-kontrollsumman ***i nx_udp_socket_receive-tjänsten,*** körs i programtrådens kontext. Detta förhindrar att nätverksbegäranden av trådar med högre prioritet stoppas på grund av bearbetning av intensiv beräkning av kontrollsumma i trådar med lägre prioritet.

Värden, till exempel IP-adresser och portnummer, skickas till API-funktioner i värdbyteordning. Internt lagras även dessa värden i värdbyteordning. På så sätt kan utvecklare enkelt visa värdena via ett felsökningsfel. När dessa värden programmeras till en ram för överföring konverteras de till nätverkets byteordning.

### <a name="internal-ip-thread"></a>Intern IP-tråd

Som tidigare nämnts har varje IP-instans i NetX en egen tråd. Prioritet och stackstorlek för den interna IP-tråden definieras i ***nx_ip_create tjänsten.*** Den interna IP-tråden skapas i ett körklart läge. Om IP-tråden har högre prioritet än anropstråden kan avbrott ske i IP-skapa-anropet.

Startpunkten för den interna IP-tråden finns i den interna funktionen ***_nx_ip_thread_entry***. När den startas slutför den interna IP-tråden först initieringen av nätverksdrivrutiner, som består av att göra tre anrop till den programspecifika nätverksdrivrutinen. Det första anropet är att koppla nätverksdrivrutinen till IP-instansen, följt av ett initieringssamtal, vilket gör att nätverksdrivrutinen kan gå igenom initieringsprocessen. När nätverksdrivrutinen återgår från initieringen (den kan pausa medan den väntar på att maskinvaran ska vara korrekt konfigurerad) anropar den interna IP-tråden nätverksdrivrutinen igen för att aktivera länken. 

När nätverksdrivrutinen returnerar från länkaktivera anropet går den interna IP-tråden in i en oändlig loopkontroll för olika händelser som behöver bearbetas för den här IP-instansen. Händelser som bearbetas i den här loopen omfattar uppskjuten mottagning av IP-paket, sammansättningen av IP-paketfragment, ICMP-pingbearbetning, IGMP-bearbetning, BEARBETNING av TCP-paketkö, regelbunden TCP-bearbetning, tidsgränser för IP-fragmentsammansättningen och periodisk IGMP-bearbetning. Händelser omfattar även adresslösningsaktiviteter: ARP-paketbearbetning och regelbunden ARP-bearbetning i IP-nätverket.

> [!NOTE]
> *NetX-återanropsfunktioner, inklusive lyssna och koppla från återanrop, anropas från den interna IP-tråden – inte den ursprungliga anropstråden. Programmet måste se till att inte pausa i någon NetX-återanropsfunktion.*

### <a name="ip-periodic-timers"></a>Periodiska IP-timers
Det finns två periodiska ThreadX-timers som används för varje IP-instans. Den första timern är en sekund för ARP, IGMP, TCP-timeout och den kör även bearbetningen av IP-fragmentet på nytt. Den andra timern är en 100 ms timer för att driva TCP-tidsgränsen för återöverföring.

### <a name="network-driver"></a>Nätverksdrivrutin
Varje IP-instans i NetX har ett primärt gränssnitt som identifieras av dess enhetsdrivrutin som anges i ***nx_ip_create*** tjänsten. Nätverksdrivrutinen ansvarar för att hantera olika NetX-begäranden, inklusive paketöverföring, paketmottagande och begäranden om status och kontroll.

För ett system med flera hem har IP-instansen flera gränssnitt, var och en med en associerad nätverksdrivrutin som utför dessa uppgifter för respektive gränssnitt.

Nätverksdrivrutinen måste också hantera asynkrona händelser som inträffar på mediet. Asynkrona händelser från mediet omfattar paketmottagande, slutförande av paketöverföring och statusändringar. NetX ger nätverksdrivrutinen flera åtkomstfunktioner för att hantera olika händelser. Dessa funktioner är utformade för att anropas från avbrottstjänstens rutindel av nätverksdrivrutinen. För IP-nätverk bör nätverksdrivrutinen vidarebefordra alla ARP-paket som tagits emot till funktionen ***_nx_arp_packet_deferred_receive** _ internal. Alla RARP-paket ska vidarebefordras till funktionen _ *_nx_rarp_packet_deferred_receive_* _ internal. Det finns två alternativ för IP-paket. Om snabb sändning av IP-paket krävs, ska inkommande IP-paket vidarebefordras till *_ _nx_ip_packet_receive_* _ för omedelbar bearbetning. Detta förbättrar Avsevärt NetX-prestanda vid hantering av IP-paket. Annars bör nätverksdrivrutinen vidarebefordra IP-paket till _*_ _nx_ip_packet_deferred_receive_**. Den här tjänsten placerar IP-paketet i kön för uppskjuten bearbetning där det sedan hanteras av den interna IP-tråden, vilket resulterar i minsta bearbetningstid för ISR.

Nätverksdrivrutinen kan också skjuta upp avbrottsbearbetningen så att IP-trådens kontext tar slut. I det här läget ska ISR spara nödvändig information, anropa den interna ***funktionen _nx_ip_driver_deferred_processing*** och bekräfta avbrottsstyrenheten. Den här tjänsten meddelar IP-tråden om att schemalägga ett återanrop till enhetsdrivrutinen för att slutföra bearbetningen av den händelse som orsakar avbrottet.

Vissa nätverksstyrenheter kan utföra beräkning och validering av tcp/IP-huvudkontrollsumma i maskinvara, utan att ta upp värdefulla CPU-resurser. För att dra nytta av funktionen för maskinvarukapacitet, tillhandahåller NetX alternativ för att aktivera eller inaktivera olika beräkningar av kontrollsumma för programvara vid kompilering, samt att aktivera eller inaktivera beräkning av kontrollsumma vid körning. Se "[Kapitel 5 NetX-nätverksdrivrutiner](chapter5.md)" för mer detaljerad information om hur du skriver NetX-nätverksdrivrutiner.

### <a name="multihome-support"></a>Stöd för flera start
NetX stöder system som är anslutna till flera fysiska enheter med en enda IP-instans. Varje fysiskt gränssnitt tilldelas till ett gränssnittskontrollblock i IP-instansen. Program som vill använda ett multihome-system måste definiera **värdet för NX_MAX_PHSYCIAL_INTERFACES** till antalet fysiska enheter som är anslutna till systemet och återskapa NetX-biblioteket. Som standard **NX_MAX_PHYSICAL_INTERFACES** till ett, vilket skapar ett gränssnittskontrollblock i IP-instansen.

NetX-programmet skapar en enskild IP-instans för den primära enheten med hjälp av tjänsten ***nx_ip_create** _ . För varje ytterligare nätverksenheter ansluter programmet enheten till IP-instansen med hjälp av tjänsten _ *_nx_ip_interface_attach_** .

Varje nätverksgränssnittsstruktur innehåller en delmängd av nätverksinformationen om nätverksgränssnittet som finns i IP-kontrollblocket, inklusive IP-adress för gränssnitt, nätmask, IP MTU-storlek och adressinformation på MAC-nivå.

> [!IMPORTANT]
> *NetX med stöd för multihome är bakåtkompatibel med tidigare versioner av NetX. Tjänster som inte tar explicit gränssnittsinformation som standard till den primära nätverksenheten.*

Det primära gränssnittet har index noll i listan över IP-instanser. Varje efterföljande enhet som är ansluten till IP-instansen tilldelas nästa index.

Alla protokolltjänster på den övre nivån som IP-instansen är aktiverad för, inklusive TCP, UDP, ICMP och IGMP, är tillgängliga för alla anslutna enheter.

I de flesta fall kan NetX fastställa den bästa källadressen som ska användas vid överföring av ett paket. Valet av källadress baseras på måladressen. NetX-tjänster tillhandahålls så att program kan ange en specifik källadress att använda, i de fall där den lämpligaste inte kan fastställas av måladressen. Ett exempel är i ett multihome-system. Ett program måste skicka ett paket till en IP-sändning eller multicast-måladress.

Tjänster som är specifika för utveckling av program med flera startprogram omfattar följande:

*nx_igmp_multicast_interface_join nx_ip_driver_interface_direct_command nx_ip_interface_address_get nx_ip_interface_address_set nx_ip_interface_attach nx_ip_interface_info_get nx_ip_interface_status_check nx_ip_raw_packet_interface_send nx_udp_socket_interface_send*

Dessa tjänster förklaras mer detaljerat i "[Kapitel 4 – Beskrivning Azure RTOS NetX Services](chapter4.md)".

### <a name="loopback-interface"></a>Loopback-gränssnitt
Loopback-gränssnittet är ett särskilt nätverksgränssnitt utan en fysisk länk kopplad till. Loopback-gränssnittet gör att program kan kommunicera med IP-loopbackadressen 127.0.0.1

Om du vill använda ett logiskt loopback-gränssnitt ser du till att det ***konfigurerbara NX_DISABLE_LOOPBACK_INTERFACE*** inte har angetts.

### <a name="interface-control-blocks"></a>Gränssnittskontrollblock
Antalet gränssnittskontrollblock i IP-instansen är antalet fysiska gränssnitt (definieras av ***NX_MAX_PHYSICAL_INTERFACES** _) plus loopback-gränssnittet om det är aktiverat. Det totala antalet gränssnitt definieras i _*_NX_MAX_IP_INTERFACES_**.

## <a name="protocol-layering"></a>Protokollskiktning

TCP/IP som implementeras av NetX är ett flerskiktat protokoll, vilket innebär att mer komplexa protokoll bygger på enklare underliggande protokoll. I TCP/IP finns protokollet på det lägsta lagret i *länklagret* och hanteras av nätverksdrivrutinen. Den här nivån är vanligtvis riktad mot Ethernet, men den kan också vara fiber, seriell eller praktiskt taget alla fysiska media.

Ovanpå länklagret finns *nätverkslagret*. I TCP/IP är detta IP-adressen, som i princip ansvarar för att skicka och ta emot enkla paket i nätverket. Protokoll av hanteringstyp som ICMP och IGMP kategoriseras vanligtvis också som nätverkslager, även om de förlitar sig på IP-adresser för att skicka och ta emot.

*Transportlagret* ligger ovanpå nätverkslagret. Det här lagret ansvarar för att hantera dataflödet mellan värdar i nätverket. Det finns två typer av transporttjänster som stöds av NetX: UDP och TCP. UDP-tjänster gör det möjligt att skicka och ta emot data mellan två värdar på ett anslutningslöst sätt, medan TCP tillhandahåller tillförlitlig anslutningsorienterad tjänst mellan två värdentiteter.

Den här skiktningen återspeglas i de faktiska nätverksdatapaketen. Varje lager i TCP/IP innehåller ett informationsblock som kallas rubrik. Den här tekniken med omgivande data (och eventuellt protokollinformation) med en rubrik kallas vanligtvis för datainkapsling. Bild 1 visar ett exempel på NetX-skiktning och bild 2 visar den resulterande datainkapsling för UDP-data som skickas.

![Protokollskiktning](./media/user-guide/protocol-layering.png)

**BILD 1. Protokollskiktning**

![UDP-datainkapsling](./media/user-guide/udp-data-encapsulation.png)

**BILD 2. UDP-datainkapsling**

## <a name="packet-pools"></a>Paketpooler

Att allokera paket på ett snabbt och deterministiskt sätt är alltid en utmaning i realtidsnätverksprogram. Med detta i åtanke ger NetX möjlighet att skapa och hantera flera pooler med nätverkspaket med fast storlek.

Eftersom NetX-paketpooler består av minnesblock med fast storlek finns det aldrig några interna fragmenteringsproblem. Fragmentering orsakar naturligtvis beteenden som i sig är icke-terministiska.

Den tid som krävs för att allokera och frigöra ett NetX-paket är dessutom en enkel manipulering av länkade listor. Dessutom sker paketallokering och avallokering i den tillgängliga listans huvud. Detta ger den snabbaste möjliga länkade listbearbetningen.

Brist på flexibilitet är vanligtvis den största nackdelen med paketpooler med fast storlek. Det är svårt att avgöra vilken optimal paketnyttolaststorlek som också hanterar det värsta inkommande paketet. NetX-paketen åtgärdar det här problemet med en valfri funktion som kallas *paketkedjekedja.* Ett faktiskt nätverkspaket kan göras av ett eller flera NetX-paket som är länkade till varandra. Dessutom har pakethuvudet en pekare överst i paketet. När ytterligare protokoll läggs till flyttas pekaren helt enkelt bakåt och det nya huvudet skrivs direkt framför data. Utan den flexibla pakettekniken skulle stacken behöva allokera en annan buffert och kopiera data till en ny buffert med det nya huvudet, vilket är bearbetningsintensivt.

Eftersom varje paketnyttolaststorlek är fast för en viss paketpool kräver programdata som är större än nyttolasten flera paket som är sammankedjade. När du fyller ett paket med användardata måste programmet använda tjänsten ***nx_packet_data_append***. Den här tjänsten flyttar programdata till ett paket. I situationer där ett paket inte är tillräckligt för att lagra användardata allokeras ytterligare paket för att lagra användardata. Om du vill använda länkning av paket måste drivrutinen kunna ta emot till eller överföra från kedjade paket.

Varje NetX-paketminnespool är en offentlig resurs. NetX har inga begränsningar för hur paketpooler används.

### <a name="packet-pool-memory-area"></a>Minnesområde för paketpool
Minnesområdet för paketpoolen anges när paketet skapas. Precis som andra minnesområden för ThreadX- och NetX-objekt kan den finnas var som helst i målets adressutrymme. Det här är en viktig funktion på grund av den stora flexibilitet som programmet får. Anta till exempel att en kommunikationsprodukt har ett minnesområde med hög hastighet för nätverksbuffertar. Det här minnesområdet används enkelt genom att göra det till en NetX-paketminnespool.

### <a name="creating-packet-pools"></a>Skapa paketpooler
Paketpooler skapas antingen under initieringen eller under körning av programtrådar. Det finns inga begränsningar för antalet paketminnespooler i ett NetX-program.

### <a name="packet-header-nx_packet"></a>Pakethuvud NX_PACKET
Som standard placerar NetX pakethuvudet omedelbart före paketets nyttolastområde. Paketminnespoolen är i princip en serie paket – huvuden som följs direkt av paketets nyttolast. Pakethuvudet (***NX_PACKET***) och layouten för paketpoolen visas på bild 3.

För nätverksdrivrutiner som kan utföra nollkopieringsåtgärder programmeras vanligtvis startadressen för paketets nyttolastområde i DMA-logiken. Vissa DMA-motorer har justeringskrav i nyttolastområdet.

> [!IMPORTANT]
> *Nätverksdrivrutinen till måste anropa funktionen ***nx_packet_transmit_release** _ när överföringen av ett paket är klar. Den här funktionen kontrollerar att paketet inte är en del av en TCP-utdatakö innan det faktiskt placeras tillbaka i den tillgängliga poolen. Om den här funktionen inte anropas kan det resultera i oförutsägbara behavior._

![Pakethuvud och paketpoollayout](./media/user-guide/packet-header-packet-pool-layout.png)

**BILD 3. Pakethuvud och paketpoollayout**

Fälten i pakethuvudet definieras enligt följande tabell. Observera att den här tabellen inte är en omfattande lista över alla medlemmar i *NX_PACKET* struktur.

| Pakethuvud          | Syfte                                                                                                                                                                                                                                                                                                                            |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *nx_packet_pool_owner*   | Det här fältet pekar på den paketpool som äger det här paketet. När paketet släpps släpps det till den här poolen. Med poolägarskapet i varje paket är det möjligt för ett datagram att sträcka sig över flera paket från flera paketpooler.                                                         |
| *nx_packet_next*         | Det här fältet pekar på nästa paket inom samma ram. Om null-värdet är null finns det inga ytterligare paket som ingår i ramen. |
| *nx_packet_last*         | Det här fältet pekar på det sista paketet i samma nätverkspaket. Om NULL, representerar det här paketet hela nätverkspaket.  |
| *nx_packet_length*       | Det här fältet innehåller det totala antalet byte i hela nätverkspaket, inklusive summan av alla byte i alla paket som är sammankedjade *av nx_packet_next* medlem. |
| *nx_packet_ip_interface* | Det här fältet är gränssnittskontrollblocket som tilldelas paketet när det tas emot av gränssnittsdrivrutinen och av NetX för utgående paket. Ett gränssnittskontrollblock beskriver gränssnittet, t.ex. nätverksadress, MAC-adress, IP-adress och gränssnittsstatus, till exempel länkaktiverad och fysisk mappning som krävs. |
| *nx_packet_data_start*   | Det här fältet pekar på början av paketets fysiska nyttolastområde. Den behöver inte följa den första NX_PACKET huvudet, men det är  standardvärdet för nx_packet_pool_create tjänsten. |
| *nx_packet_data_end*     | Det här fältet pekar på slutet av paketets fysiska nyttolastområde. Skillnaden mellan det här fältet och nx_packet_data_start representerar nyttolastens storlek. |
| *nx_packet_prepend_ptr*  | Det här fältet pekar på platsen där paketdata, antingen protokollhuvud eller faktiska data, läggs till framför befintliga paketdata (om det finns några) i paketets nyttolastområde. Det måste vara större än eller lika med *nx_packet_data_start* pekarens plats och mindre än eller lika med *nx_packet_append_ptr pekaren.*  *Av prestandaskäl förutsätter NetX att när paketet skickas till NetX-tjänster för överföring pekar den förberedda pekaren på en lång ordjusterad adress.* |
| *nx_packet_append_ptr*    | Det här fältet pekar på slutet av de data som för närvarande finns i paketets nyttolastområde. Det måste finnas mellan minnesplatsen som pekar på av *nx_packet_prepend_ptr* och *nx_packet_data_end*. Skillnaden mellan det här fältet *och nx_packet_prepend_ptr* representerar mängden data i det här paketet. |
| *nx_packet_fragment_next* | Det här fältet används för att hålla fragmenterade paket tills hela paketet kan sättas ihop på ett annat sätt. |
| *nx_packet_pad*           | Det här fältet definierar längden på utfyllnad i 4 byte-ord för att uppnå önskat justeringskrav. Det här fältet tas bort *om NX_PACKET_HEADER_PAD* inte har definierats. |
|  |  |

### <a name="packet-header-offsets"></a>Förskjutningar av pakethuvud

Pakethuvudstorleken definieras för att ge tillräckligt med utrymme för rubrikens storlek. Tjänsten *nx_packet_allocate* används för att allokera ett paket och justerar förberedelsepekaren i paketet enligt den typ av paket som anges. Pakettypen talar om för NetX vilken förskjutning som krävs för att infoga protokollrubriken (till exempel UDP, TCP eller ICMP) framför protokolldata.

Följande typer definieras i NetX för att ta hänsyn till IP-huvudet och ethernet-huvudet (fysiskt lager) i paketet. I det senare fallet antas det vara 16 byte med den nödvändiga justeringen på 4 byte i beräkningen. IP-paket definieras fortfarande i NetX för att program ska allokera paket för IP-nätverk. I följande tabell visas definierade symboler:

| Pakettyp   | Värde |
|---------------|-------|
| NX_IP_PACKET  | 0x24  |
| NX_UDP_PACKET | 0x2c  |
| NX_TCP_PACKET | 0x38  |
|               |       |

### <a name="pool-capacity"></a>Poolkapacitet
Antalet paket i en paketpool är en funktion av nyttolastens storlek och det totala antalet byte i det minnesområde som levereras till tjänsten för att skapa paketpoolen. Poolens kapacitet beräknas genom att dela upp paketstorleken (inklusive storleken på NX_PACKET-huvudet, nyttolastens storlek och korrekt justering) i det totala antalet byte i det angivna minnesområdet.

### <a name="thread-suspension"></a>Trådavstängning
Programtrådar kan pausas i väntan på ett paket från en tom pool. När ett paket returneras till poolen får den pausade tråden det här paketet och återupptas.

Om flera trådar pausas i samma paketpool återupptas de i den ordning de pausades (FIFO).

### <a name="pool-statistics-and-errors"></a>Poolstatistik och fel
Om funktionen är aktiverad håller  NetX-pakethanteringsprogramvaran Fel reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för paketpooler:

* Totalt antal paket i pool
* Kostnadsfria paket i pool
* Pool – tomma allokeringsbegäranden
* Allokeringsavstängningar för pool tom
* Ogiltiga paketsläppningar

Alla dessa statistik- och felrapporter, förutom det totala och antalet **kostnadsfria** paket i poolen, är inbyggda i NetX-biblioteket såvida inte * NX_DISABLE_PACKET_INFO _ har definierats. Dessa data är tillgängliga för programmet med tjänsten _ *_nx_packet_pool_info_get_** .

### <a name="packet-pool-control-block-nx_packet_pool"></a>Blockblockering för paketpoolkontroll NX_PACKET_POOL

Egenskaperna för varje paketminnespool finns i dess kontrollblock. Den innehåller användbar information, till exempel den länkade listan över kostnadsfria paket, antalet kostnadsfria paket och nyttolaststorleken för paket i den här poolen. Den här strukturen definieras i *nx_api.h-filen.*

Kontrollblock för paketpooler kan finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion.

## <a name="ip-protocol"></a>IP-protokoll

Ip Internet Protocol komponenten i NetX ansvarar för att skicka och ta emot IP-paket på Internet. I NetX ansvarar komponenten slutligen för att skicka och ta emot TCP-, UDP-, ICMP- och IGMP-meddelanden med hjälp av den underliggande nätverksdrivrutinen.

NetX stöder IP-protokoll (RFC 791)

### <a name="ip-addresses"></a>IP-adresser

Varje värd på Internet har en unik 32-bitars identifierare som kallas för en IP-adress. Det finns fem klasser med IP-adresser enligt beskrivningen i bild 4. Intervallen för de fem IP-adressklasserna är följande:

| Klass | Intervall                        |
|-------|------------------------------|
| A     | 0.0.0.0 till 127.255.255.255   |
| B     | 128.0.0.0 till 191.255.255.255 |
| C     | 192.0.0.0 till 223.255.255.255 |
| D     | 224.0.0.0 till 239.255.255.255 |
| E     | 240.0.0.0 till 247.255.255.255 |

**7 bitar 24 bitar**

![IP-adressstruktur](./media/user-guide/ip-address-structure.png)

**BILD 4. IP-adressstruktur**

Det finns också tre typer av adressspecifikationer: *unicast,* *broadcast* och *multicast.* Unicast-adresser är de IP-adresser som identifierar en specifik värd på Internet. Unicast-adresser kan vara antingen en käll- eller mål-IP-adress. En broadcast-adress identifierar alla värdar i ett visst nätverk eller undernätverk och kan bara användas som måladresser. Broadcast-adresser anges genom att värd-ID-delen av adressen anges till ettor. Multicast-adresser (klass D) anger en dynamisk grupp med värdar på Internet. Medlemmar i multicast-gruppen kan gå med och lämna när de vill.

> [!IMPORTANT]
> *Endast anslutningslösa protokoll som UDP över IP kan använda broadcast och den begränsade sändningsfunktionerna i multicast-gruppen.*

> [!IMPORTANT]
> *Makrot* IP_ADDRESS *definieras i*  * **nx_api.h** _. Det gör det enkelt att ange IP-adresser med kommatecken i stället för punkter. Till exempel IP_ADDRESS(128,0,0,0) _specifies den första klassens B-adress som visas på bild 4.*

### <a name="ip-gateway-address"></a>IP Gateway-adress

Nätverksgatewayer hjälper värdar i deras nätverk att vidarebefordra paket till mål utanför den lokala domänen. Varje nod har viss kunskap om vilket nästa hopp som ska skickas till, antingen målet någon av sina grannar eller via en förprogrammerad statisk routningstabell. Men om dessa metoder misslyckas bör noden vidarebefordra paketet till sin standardgateway som har mer information om hur paketet ska dirigeras till sitt mål. Observera att standardgatewayen måste vara direkt åtkomlig via ett av de fysiska gränssnitt som är anslutna till IP-instansen. Programmet anropar nx_ip_gateway_address_set ***konfigurera*** IP-standardgatewayadressen.

### <a name="ip-header"></a>IP-huvud

För att IP-paket ska kunna skickas på Internet måste det ha ett IP-huvud. När protokoll på högre nivå (UDP, TCP, ICMP eller IGMP) anropar IP-komponenten för att skicka ett paket, placerar IP-överföringsmodulen ett IP-huvud framför data. När IP-paket tas emot från nätverket tar IP-komponenten omvänt bort IP-huvudet från paketet innan de levereras till protokollen på högre nivå. Bild 5 visar formatet för IP-huvudet.

![IP-rubrikformat](./media/user-guide/ip-header-format.png)

**BILD 5. IP-rubrikformat**

> [!IMPORTANT]
> *Alla huvuden i TCP/IP-implementeringen förväntas vara i big endian format. I det här formatet finns den viktigaste byten av ordet på den lägsta byteadressen. Till exempel måste 4-bitarsversionen och 4-bitars huvudlängden för IP-huvudet finnas på den första byten i rubriken.*

Fälten i IP-huvudet definieras på följande sätt:

**Fältsyfte för IP-huvud**

***4-bitars version*** Det här fältet innehåller den ip-version som det här huvudet representerar. För IP-version 4, vilket är vad NetX stöder, är värdet för det här fältet 4.

***4-bitars rubriklängd*** Det här fältet anger antalet 32-bitars ord i IP-rubriken. Om det inte finns några alternativord är värdet för det här fältet 5.

***8-bitars tjänsttyp (TOS)*** Det här fältet anger vilken typ av tjänst som begärdes för det här IP-paketet. Giltiga begäranden är följande:

| **TOS-begäran**     | **Värde** |
| ------------------- | --------- |
| Normal              | 0x00      |
| Minsta fördröjning       | 0x10      |
| Maximalt antal data        | 0x08      |
| Maximal tillförlitlighet | 0x04      |
| Minimikostnad        | 0x02      |

***16-bitars total längd*** Det här fältet innehåller den totala längden på IP-datagrammet i byte, inklusive IP-rubriken. Ett IP-datagram är den grundläggande informationsenheten som finns på ett TCP/IP-Internet. Den innehåller ett mål och en källadress utöver data. Eftersom det är ett 16-bitars fält är den maximala storleken för ett IP-datagram 65 535 byte.

***16-bitars identifiering*** Fältet är ett tal som används för att unikt identifiera varje IP-datagram som skickas från en värd. Det här antalet ökas vanligtvis när ett IP-datagram har skickats. Det är särskilt användbart vid montering av mottagna IP-paketfragment.

***3-bitars flaggor*** Det här fältet innehåller information om IP-fragmentering. Bit 14 är "fragmentera inte"-biten. Om den här biten anges fragmenteras inte det utgående IP-datagrammet. Bit 13 är biten "fler fragment". Om den här biten har angetts finns det fler fragment. Om den här biten är tydlig är detta det sista fragmentet av IP-paketet.

**Fältsyfte för IP-huvud**

***13-bitars förskjutning av fragment*** Det här fältet innehåller de övre 13 bitarna i fragmentförskjutningen. Därför tillåts endast fragmentförskjutningar på 8 byte-gränser. Det första fragmentet av ett fragmenterat IP-datagram har bituppsättningen "fler fragment" och en offset på 0.

***8-bitars TTL -värde (Time to Live)*** Det här fältet innehåller antalet routrar som det här datagrammet kan passera, vilket begränsar livslängden för datagrammet.

***8-bitars protokoll*** Det här fältet anger vilket protokoll som använder IP-datagrammet. Följande är en lista över giltiga protokoll och deras värden:

| Protokoll | Värde |
|----------|-------|
| ICMP     | 0x01  |
| Igmp     | 0x02  |
| TCP      | 0X06  |
| UDP      | 0X11  |
|          |       |


***16-bitars kontrollsumma*** Det här fältet innehåller den 16-bitars kontrollsumma som endast täcker IP-huvudet. Det finns ytterligare kontrollsumor i protokollen på högre nivå som täcker IP-nyttolasten.

***IP-adress för 32-bitars källa*** Det här fältet innehåller avsändarens IP-adress och är alltid en värdadress.

***32-bitars mål-IP-adress*** Det här fältet innehåller IP-adressen för mottagaren eller mottagarna om adressen är en sändnings- eller multicast-adress.

### <a name="creating-ip-instances"></a>Skapa IP-instanser

IP-instanser skapas antingen under initieringen eller under körning av programtrådar. Den första IP-adressen, nätverksmasken, standardpaketpoolen, mediedrivrutinen samt minne och prioritet för den interna IP-tråden definieras *av nx_ip_create tjänsten.* Om programmet initierar IP-instansen med dess IP-adress inställd på en ogiltig adress (0.0.0.0) antas det att gränssnittsadressen kommer att lösas genom manuell konfiguration senare, via RARP eller via DHCP eller liknande protokoll.

För system med flera nätverksgränssnitt anges det primära gränssnittet när du anropar *nx_ip_create*. Varje ytterligare gränssnitt kan kopplas till samma IP-instans genom att anropa *nx_ip_interface_attach*. Den här tjänsten lagrar information om nätverksgränssnittet (till exempel IP-adress, nätverksmask) i gränssnittskontrollblocket och associerar drivrutinsinstansen med gränssnittskontrollblocket i IP-instansen. När drivrutinen tar emot ett datapaket måste den lagra gränssnittsinformationen i NX_PACKET innan den vidarebefordras till IP-mottagningslogiken. Observera att en IP-instans redan måste skapas innan du kopplar några gränssnitt.

 ### <a name="ip-send"></a>IP-skicka
 BEARBETNINGen av IP-meddelanden i NetX är mycket smidigare.

Förberedelsepekaren i paketet flyttas bakåt för att hantera IP-huvudet. IP-huvudet slutförs (med alla alternativ som anges av det anropande protokolllagret), IP-kontrollsumman beräknas in-line och paketet skickas till den associerade nätverksdrivrutinen. Dessutom koordineras utgående fragmentering inifrån IP-bearbetningen.

För IP initierar NetX ARP-begäranden om fysisk mappning krävs för ip-måladressen.

> [!IMPORTANT]
> För IP-anslutning köas paket som kräver IP-adressmatchning (dvs. fysisk mappning) i *ARP-kön tills* antalet paket som köas överskrider ARP-ködjupet (definieras av *symbolen **NX_ARP_MAX_QUEUE_DEPTH**). Om ködjupet* nås tar NetX bort det äldsta paketet i kön och fortsätter att vänta på adressmatchning för återstående paket i *kö. Å andra sidan, om en ARP-post* inte är löst, släpps de väntande paketen på ARP-posten när ARP-postens tidsgräns går ut.

För system med flera nätverksgränssnitt väljer NetX ett gränssnitt baserat på målets IP-adress. Följande procedur gäller för urvalsprocessen:

1. Om en måladress är IP-sändning eller multicast, och om ett giltigt utgående gränssnitt har angetts, använder du det gränssnittet. Annars används det första fysiska gränssnittet.

2. Om måladressen hittas i den statiska routningstabellen används gränssnittet som är associerat med gatewayen.

3. Om målet är på länken används gränssnittet på länken.

4. Om måladressen är en loopback-adress 127.0.0.1 används loopback-gränssnittet.

5. Om standardgatewayen är korrekt konfigurerad använder du gränssnittet som är associerat med standardgatewayen för att överföra paketet.

6. Utdatapaketet tas bort om allt ovanstående misslyckas.

### <a name="ip-receive"></a>IP-mottagning

IP-mottagningsbearbetningen anropas antingen från nätverksdrivrutinen eller den interna IP-tråden (för bearbetning av paket i den uppskjutna mottagna paketkön). IP-mottagningsbearbetningen undersöker protokollfältet och försöker skicka paketet till rätt protokollkomponent. Innan paketet faktiskt skickas tas IP-huvudet bort genom att presend-pekaren avancerar förbi IP-huvudet.

IP-mottagningsbearbetning identifierar också fragmenterade IP-paket och utför de nödvändiga stegen för att sätta ihop dem igen om fragmentering har aktiverats. Om fragmentering krävs men inte är aktiverat tas paketet bort.

NetX fastställer lämpligt nätverksgränssnitt baserat på det gränssnitt som anges i paketet. Om paketgränssnittet är NULL används det primära gränssnittet som standard i NetX. Detta görs för att garantera kompatibilitet med äldre NetX Ethernet-drivrutiner.

### <a name="raw-ip-send"></a>RÅ IP-skicka

Ett rå IP-paket är en IP-ram som innehåller protokollnyttolast på övre nivå som inte direkt stöds (och bearbetas) av NetX. Med ett råpaket kan utvecklare definiera sina egna IP-baserade program. Ett program kan skicka råa IP-paket direkt med hjälp av tjänsten ***nx_ip_raw_packet_send** _ om rå BEARBETNING av IP-paket har aktiverats _*_med nx_ip_raw_packet_enabled tjänsten._*_ Om måladressen är en multicast- eller broadcast-adress använder NetX som standard det första (primära) gränssnittet. För att skicka ut sådana paket i sekundära gränssnitt måste programmet därför använda tjänsten _ *_nx_ip_raw_packet_interface_send_** för att ange källadressen som ska användas för det utgående paketet.

### <a name="raw-ip-receive"></a>Rå IP-mottagning

Om råBEARBETNING av IP-paket är aktiverat kan programmet ta emot råa IP-paket via tjänsten ***nx_ip_raw_packet_receive** _ . Alla inkommande paket bearbetas enligt det protokoll som anges i IP-huvudet. Om protokollet anger UDP, TCP, IGMP eller ICMP bearbetar NetX paketet med lämplig hanterare för paketprotokolltypen. Om protokollet inte är ett av dessa protokoll och rå IP-mottagning är aktiverat, förs det inkommande paketet till den råa paketkön som väntar på att programmet ska ta emot det via tjänsten _ *_nx_ip_raw_packet_receive_** . Dessutom kan programtrådar pausas med en valfri tidsgräns i väntan på ett rå IP-paket.

### <a name="default-packet-pool"></a>Standardpaketpool

Varje IP-instans får en standardpaketpool när den skapas. Den här paketpoolen används för att allokera paket för ARP, RARP, ICMP, IGMP, olika TCP-kontrollpaket (till exempel SYN, ACK). Om standardpaketpoolen är tom när NetX behöver allokera ett paket kan NetX behöva avbryta den specifika åtgärden och returnerar ett felmeddelande om det är möjligt.

### <a name="ip-helper-thread"></a>IP-hjälptråd

Varje IP-instans har en hjälptråd. Den här tråden ansvarar för att hantera all uppskjuten paketbearbetning och all regelbunden bearbetning. IP-hjälptråden skapas i ***nx_ip_create.*** Det är här tråden får sin stack och prioritet. Observera att den första bearbetningen i IP-hjälptråden är att slutföra initieringen av nätverksdrivrutinen som är associerad med IP-tjänsten för att skapa. När initieringen av nätverksdrivrutiner är klar startar hjälptråden en oändlig loop för att bearbeta paket och periodiska begäranden.

> [!IMPORTANT]
> *Om ett oförklarligt beteende visas i IP-hjälptråden är det första felsökningssteget att öka stackstorleken under IP-tjänsten för att skapa. Om stacken är för liten kan IP-hjälptråden eventuellt skriva över minne, vilket kan orsaka ovanliga problem.*

### <a name="thread-suspension"></a>Trådavstängning

Programtrådar kan pausa vid försök att ta emot råa IP-paket. När ett raw-paket tas emot ges det nya paketet till den första tråden som pausas och tråden återupptas. NetX-tjänster för att ta emot paket har en valfri tidsgräns för inlåsning. När ett paket tas emot eller tidsgränsen går ut återupptas programtråden med lämplig slutförandestatus.

### <a name="ip-statistics-and-errors"></a>IP-statistik och -fel

Om den är aktiverad håller NetX reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP-instans:

- Totalt antal skickade IP-paket
- Totalt antal skickade IP-byte
- Totalt antal mottagna IP-paket
- Totalt antal mottagna IP-byte
- Totalt antal ogiltiga IP-paket
- Totalt antal ignorerade IP-mottagningspaket
- Totalt antal ip-mottagningsfel för kontrollsumma
- Totalt antal ignorerade IP-paket
- Totalt antal skickade IP-fragment
- Totalt antal mottagna IP-fragment

Alla dessa statistik- och felrapporter är  tillgängliga för programmet med nx_ip_info_get tjänsten.

### <a name="ip-control-block-nx_ip"></a>IP-kontrollblock NX_IP

Egenskaperna för varje IP-instans finns i dess kontrollblock. Den innehåller användbar information som IP-adresser och nätverksmasker för varje nätverksenhet och en tabell med grann-IP och adressmappning för fysisk maskinvara. Den här strukturen definieras ***i nx_api.h*** IP-instansens kontrollblock kan finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion.

### <a name="static-ip-routing"></a>Statisk IP-routning

Med funktionen för statisk routning kan ett program ange ett IP-nätverk och en nästa hoppadress för specifika IP-adresser utanför nätverkets mål. Om statisk routning är aktiverat söker NetX igenom den statiska routningstabellen efter en post som matchar måladressen för paketet som ska skickas. Om ingen matchning hittas söker NetX igenom listan över fysiska gränssnitt och väljer en käll-IP-adress och nästa hopp-adress baserat på målets IP-adress och nätverksmasken. Om målet inte matchar någon av IP-adresserna för nätverksdrivrutinerna som är anslutna till IP-instansen väljer NetX ett gränssnitt som är direkt anslutet till standardgatewayen och använder IP-adressen för gränssnittet som källadress och standardgatewayen som nästa hopp.

Poster kan läggas till och tas bort från den statiska ***routningstabellen med hjälp nx_ip_static_route_add*** och ***nx_ip_static_route_delete** _ tjänster. Om du vill använda statisk routning måste värdprogrammet aktivera den här funktionen genom att definiera _ *_NX_ENABLE_IP_STATIC_ROUTING_*.*

> [!IMPORTANT]
> *När du lägger till en post i den statiska routningstabellen söker NetX efter en matchande post för den angivna måladressen som redan finns i tabellen. Om det finns en sådan prioriteras posten med det mindre nätverket (längre prefix) i nätverksmasken.*

### <a name="ip-fragmentation"></a>IP-fragmentering

Nätverksenheten kan ha begränsningar för storleken på utgående paket. Den här gränsen kallas maximal överföringsenhet (MTU). IP MTU är den största IP-ramstorleken som en länklagerdrivrutin kan överföra utan att fragmentera IP-paketet. Under initieringsfasen för enhetsdrivrutiner måste drivrutinsmodulen konfigurera sin IP MTU-storlek via tjänsten ***nx_ip_interface_mtu_set**.*

Även om det inte rekommenderas kan programmet generera datagram som är större än den underliggande IP MTU som stöds av enheten. Innan sådana IP-datagram överförs måste IP-lagret fragmentera dessa paket. När fragmenterade IP-bildrutor tas emot måste den mottagande änden lagra alla fragmenterade IP-bildrutor med samma fragmenterings-ID och sätta ihop dem i ordning. Om IP-mottagningslogiken inte kan samla in alla fragment för att återställa den ursprungliga IP-ramen i tid, släpps alla fragment. Det är upp till det övre lagrets protokoll att identifiera sådana paketförluster och återställa från det.

Systemdesignern måste aktivera funktionen IP-fragmentering i NetX med hjälp av tjänsten nx_ip_fragment_enable för att stödja ***IP-fragmentering och sätta*** ihop dem igen. Om den här funktionen inte är aktiverad ignoreras inkommande fragmenterade IP-paket, samt paket som överskrider nätverksdrivrutinens MTU.

> [!IMPORTANT]
> *Logiken för IP-fragmentering kan tas bort helt genom att definiera*  * **NX_DISABLE_FRAGMENTATION** _ _when skapaNetX-biblioteket. På så sätt kan du minska kodstorleken för NetX.*

## <a name="address-resolution-protocol-arp-in-ip"></a>Address Resolution Protocol (ARP) i IP

Address Resolution Protocol (ARP) ansvarar för dynamisk mappning av 32-bitars IP-adresser till de underliggande fysiska medierna (RFC 826). Ethernet är det mest typiska fysiska mediet och har stöd för 48-bitarsadresser. Behovet av ARP bestäms av den nätverksdrivrutin som tillhandahålls till ***nx_ip_create*** tjänsten. Om fysisk mappning krävs måste nätverksdrivrutinen ange flaggan ***nx_interface_address_mapping_needed*** i gränssnittet strcuture.

### <a name="arp-enable"></a>Aktivera ARP
För att ARP ska fungera korrekt måste det  först aktiveras av programmet med nx_arp_enable tjänsten. Den här tjänsten uppsättningar olika datastrukturer för ARP-bearbetning, inklusive skapandet av ett ARP-cacheområde från det minne som anges till ARP-aktivera tjänsten.

### <a name="arp-cache"></a>ARP Cache
ARP-cachen kan ses som en matris med interna ARP-mappningsdatastrukturer. Varje intern struktur kan upprätthålla relationen mellan en IP-adress och en fysisk maskinvaruadress. Dessutom har varje datastruktur länkpekare så att den kan ingå i flera länkade listor.

Programmet kan söka efter en IP-adress från ARP-cachen genom att ange mac-maskinvaruadress med hjälp av tjänsten ***nx_arp_ip_address_find** _ om mappningen finns i ARP-tabellen. På samma sätt returnerar tjänsten _ *_nx_arp_hardware_address_find_** MAC-adressen för en viss IP-adress.


### <a name="arp-dynamic-entries"></a>Dynamiska ARP-poster

Som standard placerar ARP-aktivera tjänsten alla poster i ARP-cachen i listan över tillgängliga dynamiska ARP-poster. En dynamisk ARP-post allokeras från den här listan av NetX när en skicka-begäran till en omappad IP-adress identifieras. Efter allokeringen konfigureras ARP-posten och en ARP-begäran skickas till det fysiska mediet.

En dynamisk post kan också skapas av tjänsten ***nx_arp_dynamic_entry_set***.

> [!IMPORTANT]
> *Om alla dynamiska ARP-poster används ersätts den minst senast använda ARP-posten med en ny mappning.*

### <a name="arp-static-entries"></a>Statiska ARP-poster
Programmet kan också konfigurera statisk ARP-mappning med hjälp av ***nx_arp_static_entry_create tjänsten.*** Den här tjänsten allokerar en ARP-post från den dynamiska ARP-postlistan och placerar den på den statiska listan med mappningsinformationen som tillhandahålls av programmet. Statiska ARP-poster kan inte återanvändas eller bli äldre. Programmet kan ta bort en statisk post med hjälp av tjänsten ***nx_arp_static_entry_delete***.
Om du vill ta bort alla statiska poster i ARP-tabellen kan programmet använda tjänsten ***nx_arp_static_entries_delete***.

### <a name="automatic-arp-entry"></a>Automatisk ARP-post
NetX registrerar peer-peerns IP/MAC-mappning efter peer-svaren på ARP-begäran. NetX implementerar även funktionen för automatisk ARP-post där den registrerar peer-IP/MAC-adressmappning baserat på oönskade ARP-begäranden från nätverket. Med den här funktionen kan ARP-tabellen fyllas med peer-information, vilket minskar den fördröjning som krävs för att gå igenom ARP-begäran/-svarscykeln. Nackdelen med att aktivera automatisk ARP är dock att ARP-tabellen tenderar att fyllas upp snabbt i ett upptaget nätverk med många noder på den lokala länken, vilket så småningom skulle leda till att ARP-posten ersätts.

Den här funktionen är aktiverad som standard. Om du vill inaktivera det måste NetX-biblioteket kompileras med symbolen ***NX_DISABLE_ARP_AUTO_ENTRY*** definierad.

### <a name="arp-messages"></a>ARP-meddelanden

Som tidigare nämnts skickas ett meddelande om ARP-begäran när IP-uppgiften identifierar att mappning krävs för en IP-adress. ARP-begäranden skickas regelbundet (varje ***NX_ARP_UPDATE_RATE** _ sekunder) tills ett motsvarande ARP-svar tas emot. Totalt görs _ *_NX_ARP_MAXIMUM_RETRIES_** ARP-begäranden innan ARP-försöket avbryts. När ett ARP-svar tas emot lagras den associerade fysiska adressinformationen i ARP-posten som finns i cacheminnet.

För system med flera startdatorer avgör NetX vilket gränssnitt som ska skicka ARP-begäranden och svar baserat på den angivna måladressen.

> [!IMPORTANT]
> *Utgående IP-paket köas medan NetX väntar på ARP-svaret. Antalet utgående IP-paket* *i kö definieras av konstanten*  * **NX_ARP_MAX_QUEUE_DEPTH**.*

NetX svarar också på ARP-begäranden från andra noder i det lokala IP-nätverket. När en extern ARP-begäran görs som matchar den aktuella IP-adressen för gränssnittet som tar emot ARP-begäran, skapar NetX ett ARP-svarsmeddelande som innehåller den aktuella fysiska adressen.

Formaten för Ethernet ARP-begäranden och svar visas i bild 6 och beskrivs nedan:

| Fält för begäran/svar       | Syfte    |
|------------------------------|-----------------|
| Ethernet-måladress | Det här 6 byte-fältet innehåller måladressen för ARP-svaret och är en sändning (alla sådana) för ARP-begäranden. Det här fältet konfigureras av nätverksdrivrutinen. |
| Ethernet-källadress      | Det här 6 byte-fältet innehåller adressen till avsändaren av ARP-begäran eller -svaret och konfigureras av nätverksdrivrutinen. |
| Ramtyp                   | Det här fältet med 2 byte innehåller den typ av Ethernet-ram som finns, och för ARP-begäranden och -svar är detta lika med 0x0806. Det här är det sista fältet som nätverksdrivrutinen ansvarar för att konfigurera. |
| Maskinvarutyp                | Det här fältet med 2 byte innehåller maskinvarutypen, som är 0x0001 för Ethernet. |
| Protokolltyp                | Det här fältet med 2 byte innehåller protokolltypen, som 0x0800 IP-adresser. |
| Maskinvarustorlek                | Det här fältet med 1 byte innehåller maskinvarans adressstorlek, som är 6 för Ethernet-adresser. |


![ARP-paketformat](./media/user-guide/arp-packet-format.png)

**BILD 6. ARP-paketformat**

| Fältet Begäran/svar | Syfte  |
|---|---|
| Protokollstorlek | Det här fältet med 1 byte innehåller IP-adressstorleken, som är 4 för IP-adresser.  |
| Åtgärdskod | Det här fältet med 2 byte innehåller åtgärden för det här ARP-paketet. En ARP-begäran anges med värdet 0x0001, medan ett ARP-svar representeras av värdet 0x0002.  |
| Ethernet-adress för avsändare | Det här 6 byte-fältet innehåller avsändarens Ethernet-adress. |
| Avsändarens IP-adress | Det här fältet med 4 byte innehåller avsändarens IP-adress. |
| Ethernet-måladress | Det här 6 byte-fältet innehåller målets Ethernet-adress. |
| Mål-IP-adress | Det här 4 byte-fältet innehåller målets IP-adress. |

> [!IMPORTANT]
> *ARP-begäranden och svar är paket på Ethernet-nivå. Alla andra TCP/IP-paket kapslas in av ett IP-pakethuvud.*

> [!IMPORTANT]
> *Alla ARP-meddelanden i TCP/IP-implementeringen förväntas vara i big endian format. I det här formatet finns den viktigaste byten av ordet på den lägsta byte-adressen.*

### <a name="arp-aging"></a>ARP-åldersfördelning

NetX stöder automatisk ogiltighet av dynamiska ARP-inmatningar. ***NX_ARP_EXPIRATION_RATE** _specifies antal sekunder som en etablerad IP-adress till fysisk mappning är giltigt. Efter förfallodatum tas ARP-posten bort från ARP-cachen. Nästa försök att skicka till motsvarande IP-adress resulterar i en ny ARP-begäran. Inställningen _ *_NX_ARP_EXPIRATION_RATE_** till noll inaktiverar ARP-ålder, vilket är standardkonfigurationen.

### <a name="arp-defend"></a>ARP-försvar

När ett ARP-begärande- eller ARP-svarspaket tas emot och avsändaren har samma IP-adress, vilket står i konflikt med IP-adressen för den här noden, skickar NetX en ARP-begäran för den adressen som ett skydd. Om ARP-konfliktpaketet tas emot mer än en gång på 10 sekunder skickar NetX inte fler försvarspaket. Standardintervallet 10 sekunder kan omdefinieras med ***NX_ARP_DEFEND_INTERVAL** _. Det här beteendet följer den princip som anges i 2.4 (c) i RFC5227. Eftersom Windows XP ignorerar ARP-meddelandet som ett svar på ARP-avsökningen kan användaren definiera _*_NX_ARP_DEFEND_BY_REPLY_**för att skicka ARP-svar som ytterligare en funktion.

### <a name="arp-statistics-and-errors"></a>ARP-statistik och fel

Om den är aktiverad håller NetX ARP-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP-adress ARP-bearbetning:

- Totalt antal skickade ARP-begäranden
- Totalt antal mottagna ARP-begäranden
- Totalt antal skickade ARP-svar
- Totalt antal mottagna ARP-svar
- Totalt antal dynamiska ARP-poster
- Totalt antal statiska ARP-poster
- Totalt antal inspelade poster i ARP
- Totalt antal ogiltiga ARP-meddelanden

All statistik och alla felrapporter är  tillgängliga för programmet med nx_arp_info_get tjänsten.

## <a name="reverse-address-resolution-protocol-rarp-in-ip"></a>REVERSE Address Resolution Protocol (RARP) i IP

REVERSE Address Resolution Protocol (RARP) är protokollet för att begära nätverkstilldelning av värdens 32-bitars IP-adresser (RFC 903). Detta görs via en RARP-begäran och fortsätter regelbundet tills en nätverksmedlem tilldelar en IP-adress till värdnätverksgränssnittet i ett RARP-svar. Programmet skapar en IP-instans av ***tjänstinstansen nx_ip_create*** utan IP-adress. Om RARP har aktiverats av programmet kan det använda RARP-protokollet för att begära en IP-adress från nätverksservern som är tillgänglig via gränssnittet som har en IP-adress på noll.

### <a name="rarp-enable"></a>AKTIVERA RARP

Om du vill använda RARP måste programmet skapa IP-instansen med IP-adressen noll och sedan aktivera RARP med hjälp av ***nx_rarp_enable***. För multihome-system måste minst en nätverksenhet som är associerad med IP-instansen ha EN IP-adress på noll. RARP-bearbetningen skickar regelbundet RARP-begärandemeddelanden för NetX-systemet som kräver en IP-adress tills ett giltigt RARP-svar med nätverkets avsedda IP-adress tas emot. Nu är RARP-bearbetningen klar.

När RARP har aktiverats inaktiveras det automatiskt när alla gränssnittsadresser har lösts. Programmet kan tvinga RARP att avsluta med hjälp av tjänsten ***nx_rarp_disable***.

###  <a name="rarp-request"></a>RARP-begäran

Formatet för ett RARP-begärandepaket är nästan identiskt med ARP-paketet som visas i bild 6 i avsnittet [ARP-meddelanden.](#arp-messages) Den enda skillnaden är att ramtypens fält 0x8035 operation *code-fältet* är 3, vilket anger en RARP-begäran. Som tidigare nämnts skickas RARP-begäranden regelbundet (var ***NX_RARP_UPDATE_RATE*** sekunder) tills ett RARP-svar med den nätverks tilldelade IP-adressen tas emot.

> [!IMPORTANT]
> *Alla RARP-meddelanden i TCP/IP-implementeringen förväntas vara i big endian format. I det här formatet finns den viktigaste byten av ordet på den lägsta byte-adressen.*

### <a name="rarp-reply"></a>RARP-svar

RARP-svarsmeddelanden tas emot från nätverket och innehåller den nätverks tilldelade IP-adressen för den här värden. Formatet för ett RARP-svarspaket är nästan identiskt med ARP-paketet som visas i bild 6. Den enda skillnaden är att ramtypens fält 0x8035 operation *code-fältet* är 4, vilket anger ett RARP-svar. När IP-adressen har tagits emot konfigureras den i IP-instansen, den periodiska RARP-begäran inaktiveras och IP-instansen är nu redo för normal nätverksdrift.

För multihome-värdar tillämpas IP-adressen på det begärande nätverksgränssnittet. Om det finns andra nätverksgränssnitt som fortfarande begär en IP-adresstilldelning fortsätter den periodiska RARP-tjänsten tills alla GRÄNSSNITTs-IP-adressbegäranden har lösts.

> [!IMPORTANT]
> *Programmet bör inte använda IP-instansen förrän RARP-bearbetningen har slutförts. Den **nx_ip_status_check** kan användas av program för att vänta tills RARP har slutförts. För multihome-system bör programmet inte använda det begärande gränssnittet förrän RARP-bearbetningen har slutförts på det gränssnittet. Status för IP-adressen på den sekundära  enheten kan kontrolleras med nx_ip_interface_status_check tjänsten.*

### <a name="rarp-statistics-and-errors"></a>RARP-statistik och -fel

Om den är aktiverad håller NetX RARP-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP-adress RARP-bearbetning:

- Totalt antal SKICKADE RARP-begäranden
- Totalt antal mottagna RARP-svar
- Totalt antal ogiltiga RARP-meddelanden

All statistik och alla felrapporter är  tillgängliga för programmet med nx_rarp_info_get tjänsten.

## <a name="internet-control-message-protocol-icmp"></a>Internet Control Message Protocol (ICMP)

Internet Control Message Protocol ip-adress (ICMP) är begränsad till att skicka fel- och kontrollinformation mellan IP-nätverksmedlemmar.

Precis som de flesta andra programlagermeddelanden (t.ex. TCP/IP) kapslas ICMP-meddelanden in av ett IP-huvud med ICMP-protokollbeteckningen.

### <a name="icmp-statistics-and-errors"></a>ICMP-statistik och -fel

Om det här alternativet är aktiverat håller NetX reda på flera ICMP-statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP-adresss ICMP-bearbetning:

- Totalt antal skickade ICMP-pingar
- Totalt antal timeouter för ICMP-ping
- Totalt antal pausade ICMP-pingtrådar
- Totalt antal mottagna ICMP-pingsvar
- Totalt antal fel i ICMP-kontrollsumma
- Totalt antal ohanterade ICMP-meddelanden

All statistik och alla felrapporter är  tillgängliga för programmet med nx_icmp_info_get tjänsten.

### <a name="icmp-enable"></a>ICMP Enable
Innan ICMP-meddelanden kan bearbetas av NetX måste programmet anropa ***nx_icmp_enable tjänsten*** för att aktivera ICMP-bearbetning. När det är klart kan programmet utfärda pingbegäranden och fält för inkommande ping-paket.

### <a name="icmp-echo-request"></a>ICMP Echo-begäran
En ekobegäran är en typ av ICMP-meddelande som vanligtvis används för att kontrollera om det finns en specifik nod i nätverket, som identifieras av dess värd-IP-adress. Det populära ping-kommandot implementeras med hjälp av ICMP-ekobegäran/ekosvarsmeddelanden. Om den specifika värden finns bearbetar dess nätverksstack pingbegäran och svar med ett pingsvar. Bild 7 innehåller information om ICMP-pingmeddelandeformatet.

![ICMP-pingmeddelande](./media/user-guide/icmp-ping-message.png)

**BILD 7. ICMP-pingmeddelande**

> [!IMPORTANT]
> *Alla ICMP-meddelanden i TCP/IP-implementeringen förväntas vara i big endian format. I det här formatet finns den viktigaste byten av ordet på den lägsta byte-adressen.*

I följande tabell beskrivs ICMP-rubrikformatet:

| Rubrikfält    | Syfte |
|-----------------|---------------------------------------------------|
| Typ            | Det här fältet anger ICMP-meddelandet (bitar 31–24). De vanligaste är: 0 Ekosvar 8 Ekobegäran |
| Kod            | Det här fältet är kontextspecifikt för typfältet (bitar 23–16). För en ekobegäran eller svar är koden inställd på noll. |
| Kontrollsumma        | Det här fältet innehåller 16-bitars kontrollsumman för den ena komplementsumman av ICMP-meddelandet, inklusive hela ICMP-huvudet som börjar med fältet Typ. Innan kontrollsumman genereras rensas fältet kontrollsumma.                 |
| Identification  | Det här fältet innehåller ett ID-värde som identifierar värden. en värd ska använda DET ID som extraherats från en ECHO-begäran i ECHO REPLY (bitar 31-16). |
| Sekvensnummer | Det här fältet innehåller ett ID-värde. en värd ska använda DET ID som extraheras från en ECHO-begäran i ECHO REPLY (bitar 31-16). Till skillnad från identifierarfältet ändras det här värdet i en efterföljande Echo-begäran från samma värd (bitar 15-0). |


### <a name="icmp-echo-response"></a>Svar från ICMP Echo
Ett pingsvar är en annan typ av ICMP-meddelande som genereras internt av ICMP-komponenten som svar på en extern pingbegäran. Förutom bekräftelse innehåller ping-svaret även en kopia av användardata som anges i ping-begäran.

## <a name="internet-group-management-protocol-igmp"></a>Internet Grupphanteringsprotokoll (IGMP)

I Internet Group Management Protocol (IGMP) tillhandahåller en enhet för att kommunicera med sina grannar och dess routrar som den har för avsikt att ta emot eller ansluta till en IP-multicast-grupp (RFC 1112 och RFC 2236). En multicast-grupp är i princip en dynamisk samling nätverksmedlemmar och representeras av en IP-adress för klass D. Medlemmar i multicast-gruppen kan lämna när som helst och nya medlemmar kan gå med när som helst. Den samordning som ingår i att ansluta till och lämna gruppen är IGMP:s ansvar.

### <a name="igmp-enable"></a>Aktivera IGMP

Innan någon multicasting-aktivitet kan äga rum i  NetX måste programmet anropa nx_igmp_enable tjänsten. Den här tjänsten utför grundläggande IGMP-initiering som förberedelse för multicast-begäranden.

### <a name="multicast-ip-addressing"></a>Multicast IP-adressering

Som tidigare nämnts är multicast-adresser faktiskt IP-adresser av klass D som visas i bild 4 på sidan 58. De lägre 28 bitarna i klass D-adressen motsvarar multicast-grupp-ID:t. Det finns en serie fördefinierade multicast-adresser. Alla *värdars adress* (244.0.0.1) är dock särskilt viktig för IGMP-bearbetning. Alla *värdadresser* används av routrar för att fråga alla multicast-medlemmar för att rapportera om vilka multicast-grupper de tillhör.

### <a name="physical-address-mapping-in-ip"></a>Fysisk adressmappning i IP

Multicast-adresser för klass D mappas direkt till fysiska Ethernet-adresser från 01.00.5e.00.00.00 till 01.00.5e.7f.ff.ff. De lägre 23 bitarna av IP-multicast-adressmappningen direkt till de lägre 23 bitarna av Ethernet-adressen.

### <a name="multicast-group-join"></a>Multicast-gruppkoppling

Program som behöver ansluta till en viss multicast-grupp kan göra det genom att anropa ***nx_igmp_multicast_join tjänsten.*** Den här tjänsten håller reda på antalet begäranden om att ansluta till den här multicast-gruppen. Om det här är den första programbegäran om att ansluta till multicast-gruppen skickas en IGMP-rapport i det primära nätverket som anger den här värdens avsikt att ansluta till gruppen. Därefter anropas nätverksdrivrutinen för att konfigurera för att lyssna efter paket med Ethernet-adressen för den här multicast-gruppen.

Om multicast-gruppen är tillgänglig via ett specifikt gränssnitt i ett multihome-system, ska programmet använda tjänsten ***nx_igmp_multicast_interface_join*** i stället för ***nx_igmp_multicast_join**,* som är begränsad till multicast-grupper i det primära nätverket.

### <a name="multicast-group-leave"></a>Lämna multicast-grupp

Program som behöver lämna en tidigare ansluten multicast-grupp kan göra det genom att anropa ***nx_igmp_multicast_leave tjänsten.*** Den här tjänsten minskar det interna antalet som är associerat med hur många gånger gruppen har anslutits. Om det inte finns några utestående kopplingsbegäranden för en grupp anropas nätverksdrivrutinen för att inaktivera lyssna efter paket med den här multicast-gruppens Ethernet-adress

### <a name="multicast-loopback"></a>Multicast Loopback

Ett program kan vilja ta emot multicast-trafik från en av källorna på samma nod. Detta kräver att IP-multicast-komponenten har loopback aktiverat med hjälp av tjänsten ***nx_igmp_loopback_enable***.

### <a name="igmp-report-message"></a>IGMP-rapportmeddelande

När programmet ansluts till en multicast-grupp skickas ett IGMP-rapportmeddelande via nätverket för att ange värdens avsikt att ansluta till en viss multicast-grupp. Formatet för IGMP-rapportmeddelandet visas i bild 8. Multicast-gruppadressen används för både gruppmeddelandet i IGMP-rapportmeddelandet och mål-IP-adressen.

![IGMP-rapportmeddelande](./media/user-guide/igmp-report-message.png)

**BILD 8. IGMP-rapportmeddelande**

I bilden ovan (bild 8) innehåller IGMP-huvudet ett version/typ-fält, maximal svarstid, ett fält för kontrollsumma och ett multicast-gruppadressfält. För IGMPv1-meddelanden anges fältet Maximal svarstid alltid till noll, eftersom detta inte är en del av IGMPv1-protokollet. Fältet Maximal svarstid anges när värden tar emot ett IGMP-meddelande av frågetyp och rensas när en värd tar emot en annan värds rapporttypsmeddelande enligt definitionen i IGMPv2-protokollet.

Följande beskriver IGMP-rubrikformatet:

| **Rubrikfält**          | **Syfte** |
|-----------------------|--------------------------------------------------------------------|
| Version               | Det här fältet anger IGMP-versionen (bitar 31–28).                                                                               |
| Typ                  | Det här fältet anger typen av IGMP-meddelande (bitar 27-24).                                                                       |
| Maximal svarstid | Används inte i IGMPv1. I IGMPv2 fungerar det här fältet som maximal svarstid.                                                      |
| Kontrollsumma              | Det här fältet innehåller 16-bitars kontrollsumman för komplementssumman för IGMP-meddelandet som börjar med IGMP-versionen (bitar 0–15) |
| Gruppadress         | IP-adress för 32-bitars D-grupp |


IGMP-rapportmeddelanden skickas också som svar på IGMP-frågemeddelanden som skickas av en multicast-router. Multicast-routrar skickar regelbundet frågemeddelanden ut för att se vilka värdar som fortfarande kräver gruppmedlemskap. Frågemeddelanden har samma format som IGMP-rapportmeddelandet som visas i bild 8. De enda skillnaderna är att IGMP-typen är lika med 1 och gruppadressfältet är inställt på 0. IGMP-frågemeddelanden skickas till alla *värdars* IP-adress av multicast-routern. En värd som fortfarande vill behålla gruppmedlemskapet svarar genom att skicka ett annat IGMP-rapportmeddelande.

> [!IMPORTANT]
> *Alla meddelanden i TCP/IP-implementeringen förväntas vara i **big endian** format. I det här formatet finns den viktigaste byten av ordet på den lägsta byteadressen.*

### <a name="igmp-statistics-and-errors"></a>IGMP-statistik och -fel

Om den är aktiverad håller NetX IGMP-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP-adresss IGMP-bearbetning:

- Totalt antal skickade IGMP-rapporter
- Totalt antal mottagna IGMP-frågor
- Totalt antal IGMP-kontrollsummor
- Totalt antal IGMP-grupper som anslutits

Alla dessa statistik- och felrapporter är  tillgängliga för programmet med nx_igmp_info_get tjänsten.

## <a name="user-datagram-protocol-udp"></a>UDP (User Datagram Protocol)

UDP (User Datagram Protocol) är den enklaste formen av dataöverföring mellan nätverksmedlemmar (RFC 768). UDP-datapaket skickas från en nätverksmedlem till en annan på bästa sätt. Det finns alltså ingen inbyggd mekanism för bekräftelse av paketmottagaren. Att skicka ett UDP-paket kräver inte heller att någon anslutning upprättas i förväg. Därför är UDP-paketöverföring mycket effektivt.

### <a name="udp-header"></a>UDP-rubrik
UDP placerar ett enkelt pakethuvud framför programmets data vid överföring och tar bort ett liknande UDP-huvud från paketet vid mottagning innan ett mottaget UDP-paket levereras till programmet. UDP använder IP-protokollet för att skicka och ta emot paket, vilket innebär att det finns ett IP-huvud framför UDP-huvudet när paketet finns i nätverket. Bild 9 visar UDP-rubrikens format.

![UDP-rubrik](./media/user-guide/udp-header.png)

**BILD 9. UDP-rubrik**

> [!IMPORTANT]
> *Alla huvuden i UDP/IP-implementeringen förväntas vara i big endian format. I det här formatet finns den viktigaste byten av ordet på den lägsta byteadressen.*

Följande beskriver UDP-rubrikformatet:

| Rubrikfält                   | Syfte |
|--------------------------------|---------------------------------------------|
| Portnummer för 16-bitars källa      | Det här fältet innehåller porten som UDP-paketet skickas från. Giltiga UDP-portar sträcker sig från 1 till 0xFFFF. |
| Portnummer för 16-bitarsmål | Det här fältet innehåller UDP-porten som paketet skickas till. Giltiga UDP-portar sträcker sig från 1 till 0xFFFF.   |
| 16-bitars UDP-längd   | Det här fältet innehåller antalet byte i UDP-paketet, inklusive storleken på UDP-huvudet.                                  |
| 16-bitars UDP-kontrollsumma | Det här fältet innehåller 16-bitars kontrollsumma för paketet, inklusive UDP-huvudet, paketdataområdet och pseudo-IP-huvudet. |

### <a name="udp-enable"></a>UDP-aktivera

Innan UDP-paketöverföring är möjligt måste programmet först  aktivera UDP genom att anropa nx_udp_enable tjänsten. När det har aktiverats kan programmet skicka och ta emot UDP-paket.

### <a name="udp-socket-create"></a>Skapa UDP-socket

UDP-sockets skapas antingen under initieringen eller under körning av programtrådar. Den första typen av tjänst, TT-tid och  mottagning av ködjup definieras av nx_udp_socket_create tjänsten. Det finns inga begränsningar för antalet UDP-socketar i ett program.

### <a name="udp-checksum"></a>UDP-kontrollsumma

UDP anger ens kompletterande 16-bitars kontrollsumma som omfattar IP-pseudorubriken (som består av källans IP-adress, målets IP-adress och ip-ordet för protokoll/längd), UDP-huvudet och UDP-paketdata. Om den beräknade UDP-kontrollsumman är 0 lagras den som alla (0xFFFF). Om den skickande socketen har logiken för UDP-kontrollsumma inaktiverad placeras noll i fältet UDP-kontrollsumma för att indikera att kontrollsumman inte beräknades. Om UDP-kontrollsumman inte matchar den beräknade kontrollsumman av mottagaren ignoreras UDP-paketet.

I IP-nätverket är UDP-kontrollsumma valfri. Med NetX kan ett program aktivera eller inaktivera UDP-kontrollsummaberäkning per socket. Som standard är logiken för UDP-socketkontrollsumma aktiverad. Programmet kan inaktivera logik för kontrollsumma för en  viss UDP-socket genom att anropa nx_udp_socket_checksum_disable tjänsten.

Vissa Ethernet-styrenheter kan generera UDP-kontrollsumman i farten. Om systemet kan använda beräkningsfunktionen kontrollsumma för maskinvara kan NetX-biblioteket byggas utan logiken för kontrollsumma. Om du vill inaktivera kontrollsumma för UDP-programvara måste NetX-biblioteket byggas med följande definierade symboler: ***NX_DISABLE_UDP_TX_CHECKSUM*** ***och NX_DISABLE_UDP_RX_CHECKSUM**_ (beskrivs i kapitel [2](chapter2.md)). Konfigurationsalternativen tar bort* UDP-kontrollsummalogiken*** från NetX helt och hållet, samtidigt som tjänsten _ nx_udp_socket_checksum_disable anropar gör att programmet kan inaktivera bearbetning av IP UDP-kontrollsumma per socket.

### <a name="udp-ports-and-binding"></a>UDP-portar och bindning

En UDP-port är en logisk slutpunkt i UDP-protokollet. Det finns 65 535 giltiga portar i UDP-komponenten i NetX, från 1 till 0xFFFF. Om du vill skicka eller ta emot UDP-data måste programmet först skapa en UDP-socket och sedan binda den till en önskad port. När du har bindat en UDP-socket till en port kan programmet skicka och ta emot data på den socketen.

### <a name="udp-fast-pathtrade"></a>Snabb sökväg för UDP&trade;

Den snabba &trade; UDP-sökvägen är namnet på en låg paketkostnadsväg via NetX UDP-implementeringen. Att skicka ett UDP-paket kräver bara några funktionsanrop: ***nx_udp_socket_send** _, _*_nx_ip_packet_send_*_, och det slutliga anropet till nätverksdrivrutinen. _*_nx_udp_socket_send_*_ är tillgängligt i NetX för befintliga NetX-program och gäller endast för IP-paket. Den bästa metoden är dock att använda tjänsten _ *_nx_udp_socket_send_** som beskrivs nedan. Vid UDP-paketmottagande placeras UDP-paketet antingen i lämplig UDP-socket-mottagningskö eller levereras till en pausad programtråd i ett enda funktionsanrop från nätverksdrivrutinens bearbetning av avbrott vid mottagning. Den här mycket optimerade logiken för att skicka och ta emot UDP-paket är grunden för UDP Fast Path-teknik.

### <a name="udp-packet-send"></a>Skicka UDP-paket

Det är enkelt att skicka UDP-data via IP-nätverk genom att anropa funktionen ***nx_udp_socket_send** _ . Anroparen måste ange IP-versionen i fältet _IP address*. NetX avgör den bästa källadressen för överförda UDP-paket baserat på målets IP-adress. Den här tjänsten placerar ett UDP-huvud framför paketdata och skickar ut dem till nätverket med hjälp av en intern IP-sändrutin. Det finns ingen trådavstängning för att skicka UDP-paket eftersom alla UDP-paketöverföringar bearbetas omedelbart.

För multicast- eller broadcast-mål ska programmet ange den IP-källadress som ska användas om NetX-enheten har flera IP-adresser att välja mellan. Detta kan göras med de tjänster ***som nx_udp_socket_interface_send.***

> [!IMPORTANT]
> *Om **nx_udp_socket_send** används för att överföra multicast- eller broadcast-paket används IP-adressen för det första gränssnittet som källadress.*

> [!IMPORTANT]
> *Om UDP-kontrollsummalogik är aktiverad för den här socketen utförs åtgärden för kontrollsumma i kontexten för den anropande tråden, utan att blockera åtkomst till UDP- eller IP-datastrukturerna.*

> [!NOTE]
> *UDP-nyttolastdata som finns **i NX_PACKET** ska finnas på en lång ordgräns. Programmet måste lämna tillräckligt med utrymme mellan den förberedande pekaren och datastartspekaren för NetX för att placera UDP-, IP- och fysiska medierubriker.*

### <a name="udp-packet-receive"></a>UDP-paket ta emot

Programtrådar kan ta emot UDP-paket från en viss socket genom att anropa ***nx_udp_socket_receive***. Funktionen socket receive levererar det äldsta paketet på socketens mottagningskö. Om det inte finns några paket i mottagningskön kan den anropande tråden pausa (med en valfri tidsgräns) tills ett paket anländer.

UDP-mottagningspaketbearbetningen (anropas vanligtvis från nätverksdrivrutinens mottagningsavbrottshanterare) ansvarar för att antingen placera paketet i UDP-socketens mottagningskö eller leverera det till den första pausade tråden som väntar på ett paket. Om paketet köas kontrollerar mottagningsbearbetningen även det maximala mottagningsködjupet som är associerat med socketen. Om det nyligen köade paketet överskrider ködjupet tas det äldsta paketet i kön bort.

### <a name="udp-receive-notify"></a>UDP-meddelande om mottagning

Om programtråden behöver bearbeta mottagna data från mer än en socket, ***nx_udp_socket_receive_notify-funktionen*** användas. Den här funktionen registrerar en återanropsfunktion för mottagningspaket för socketen. När ett paket tas emot på socketen körs återanropsfunktionen.

Innehållet i återanropsfunktionen är programspecifikt. Det skulle dock sannolikt innehålla logik för att informera bearbetningstråden om att ett paket nu är tillgängligt på motsvarande socket.

### <a name="peer-address-and-port"></a>Peer-adress och port

När ett UDP-paket tas emot kan programmet hitta avsändarens IP-adress och portnummer med hjälp av tjänsten ***nx_udp_packet_info_extract***. Vid lyckad retur innehåller den här tjänsten information om avsändarens IP-adress, avsändarens portnummer och det lokala gränssnitt som paketet togs emot via.

### <a name="thread-suspension"></a>Trådavstängning

Som tidigare nämnts kan programtrådar pausa vid försök att ta emot ett UDP-paket på en viss UDP-port. När ett paket tas emot på den porten ges det till den första tråden som pausas och tråden återupptas sedan. En valfri tidsgräns är tillgänglig när du pausar på ett UDP-mottagningspaket, en funktion som är tillgänglig för de flesta NetX-tjänster.

### <a name="udp-socket-statistics-and-errors"></a>UDP Socket-statistik och fel

Om den är aktiverad håller NetX UDP-socketprogramvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP/UDP-instans:

- Totalt antal UDP-paket som skickats
- Totalt antal UDP-byte som skickats
- Totalt antal mottagna UDP-paket
- Totalt antal mottagna UDP-byte
- Totalt antal ogiltiga UDP-paket
- Totalt antal bort ignorerade UDP-mottagningspaket
- Totalt antal UDP-fel vid kontrollsumma
- UDP Socket-paket som skickats
- Skickade UDP Socket-byte
- Mottagna UDP Socket-paket
- Mottagna UDP Socket-byte
- UDP Socket-paket i kö
- UDP Socket Receive Packets Dropped
- Fel med kontrollsumma för UDP-socket

Alla dessa statistik- och felrapporter är tillgängliga för programmet med ***nx_udp_info_get-tjänsten*** för UDP-statistik amassed över alla UDP-sockets och ***nx_udp_socket_info_get-tjänsten*** för UDP-statistik på den angivna UDP-socketen.

### <a name="udp-socket-control-block-nx_udp_socket"></a>UDP Socket Control Block NX_UDP_SOCKET

Egenskaperna för varje UDP-socket finns i det associerade **NX_UDP_SOCKET** kontrollblocket. Den innehåller användbar information, till exempel länken till IP-datastrukturen, nätverksgränssnittet för de skickande och mottagande sökvägarna, den bundna porten och kön för att ta emot paket. Den här strukturen definieras i **_nx_api.h-filen._**

## <a name="transmission-control-protocol-tcp"></a>Transmission Control Protocol (TCP)

Med Transmission Control Protocol (TCP) kan du överföra tillförlitliga dataströmmar mellan två nätverksmedlemmar (RFC 793). Alla data som skickas från en nätverksmedlem verifieras och bekräftas av den mottagande medlemmen. Dessutom måste de två medlemmarna ha upprättat en anslutning före dataöverföringen. Allt detta resulterar i tillförlitlig dataöverföring. Det kräver dock betydligt mer omkostnader än den tidigare beskrivna UDP-dataöverföringen.

### <a name="tcp-header"></a>TCP-huvud

Vid överföring placeras TCP-huvudet framför data från användaren. Vid mottagning tas TCP-huvudet bort från det inkommande paketet, vilket lämnar endast användardata tillgängliga för programmet. TCP använder IP-protokollet för att skicka och ta emot paket, vilket innebär att det finns ett IP-huvud framför TCP-huvudet när paketet finns i nätverket. Bild 10 visar formatet för TCP-huvudet.

![TCP-huvud](./media/user-guide/tcp-header.png)

**BILD 10. TCP-huvud**

Följande beskriver TCP-rubrikformatet:

| Rubrikfält | Syfte |
|---|---|
| 16-bitars källportnummer | Det här fältet innehåller porten som TCP-paketet skickas ut på. Giltiga TCP-portar sträcker sig från 1 till 0xFFFF. |
| Portnummer för 16-bitarsmål | Det här fältet innehåller TCP-porten som paketet skickas till. Giltiga TCP-portar sträcker sig från 1 till 0xFFFF. |
| 32-bitars sekvensnummer | Det här fältet innehåller sekvensnumret för data som skickas från den här änden av anslutningen. Den ursprungliga sekvensen upprättas under den första anslutningssekvensen mellan två TCP-noder. Varje dataöverföring från den punkten resulterar i en ökning av sekvensnumret med mängden byte som skickas. |
| 32-bitars bekräftelsenummer | Det här fältet innehåller det sekvensnummer som motsvarar den sista byte som tagits emot av den här sidan av anslutningen. Detta används för att avgöra om data som tidigare har skickats har tagits emot av den andra änden av anslutningen. |
| 4-bitars rubriklängd           | Det här fältet innehåller antalet 32-bitars ord i TCP-rubriken. Om det inte finns några alternativ i TCP-huvudet är det här fältet 5. |
| 6-bitars kod bitar               | Det här fältet innehåller de sex olika kodbitarna som används för att ange olika kontrollinformation som är associerad med anslutningen. Kontrollbitarna definieras på följande sätt: |



| Name | Bitars | Innebörd                                                     |
|------|-----|-------------------------------------------------------------|
| URG  | 21  | Brådskande data finns                                         |
| ACK  | 20  | Bekräftelsenumret är giltigt                             |
| Psh  | 19  | Hantera dessa data omedelbart                                |
| Rst  | 18  | Återställa anslutningen                                        |
| Syn  | 17  | Synkronisera sekvensnummer (används för att upprätta anslutning) |
| FIN  | 16  | Avsändaren är klar med överföringen (används för att stänga anslutningen) |

**16-bitars fönster**

Det här fältet används för flödeskontroll. Den innehåller mängden byte som socketen kan ta emot för närvarande. Detta används i princip för flödeskontroll. Avsändaren ansvarar för att se till att de data som ska skickas får plats i mottagarens annonserade fönster.

| **Rubrikfält**          | **Syfte** |
| ------------------------- | --- |
| **16-bitars TCP-kontrollsumma**   | Det här fältet innehåller 16-bitars kontrollsumma för paketet, inklusive TCP-huvudet, paketdataområdet och pseudo-IP-huvudet.                |
| **16-bitars brådskande pekare** | Det här fältet innehåller den positiva förskjutningen av den sista byten av brådskande data. Det här fältet är bara giltigt om URG-kodbiten har angetts i rubriken. |

> [!IMPORTANT]
> *Alla huvuden i TCP/IP-implementeringen förväntas vara i big endian format. I det här formatet finns den viktigaste byten av ordet på den lägsta byteadressen.*

### <a name="tcp-enable"></a>TCP-aktivera

Innan TCP-anslutningar och paketöverföringar är möjliga måste programmet först aktivera TCP genom att anropa nx_tcp_enable tjänsten. När det har aktiverats kan programmet komma åt alla TCP-tjänster.

### <a name="tcp-socket-create"></a>Skapa TCP-socket

TCP-sockets skapas antingen under initieringen eller under körning av programtrådar. Den första typen av tjänst, TT-tid och  fönsterstorlek definieras av nx_tcp_socket_create tjänsten. Det finns inga begränsningar för antalet TCP-socketar i ett program.

### <a name="tcp-checksum"></a>TCP-kontrollsumma

TCP anger ett 16-bitars komplementkontrollsumma som omfattar IP-pseudorubriken (som består av källans IP-adress, målets IP-adress och ip-ordet för protokoll/längd), TCP-huvudet och TCP-paketdata.

Vissa nätverksstyrenheter kan utföra beräkning och validering av TCP-kontrollsumma i maskinvaran. För sådana system kanske program vill använda logik för kontrollsumma för maskinvara så mycket som möjligt för att minska körningskostnader. Program kan inaktivera beräkningslogik för TCP-kontrollsumma helt från NetX-biblioteket vid byggtiden genom **att definiera NX_DISABLE_TCP_TX_CHECKSUM** och **NX_DISABLE_TCP_RX_CHECKSUM**. På så sätt kompileras inte TCP-kontrollsummakoden.

### <a name="tcp-port"></a>TCP-port

En TCP-port är en logisk anslutningspunkt i TCP-protokollet. Det finns 65 535 giltiga portar i TCP-komponenten i NetX, från 1 till 0xFFFF. Till skillnad från UDP där data från en port kan skickas till en annan målport, ansluts en TCP-port till en annan specifik TCP-port, och endast när den här anslutningen upprättas kan dataöverföring ske– och endast mellan de två portarna som upprättar anslutningen.

> [!IMPORTANT]
> *TCP-portarna är helt åtskilda från UDP-portar. Till exempel har UDP-portnummer 1 ingen relation till TCP-portnummer 1.*

## <a name="client-server-model"></a>Client-Server modell

Om du vill använda TCP för dataöverföring måste en anslutning först upprättas mellan de två TCP-socketarna. Anslutningen upprättas på ett klient-server-sätt. Klientsidan av anslutningen är den sida som initierar anslutningen, medan serversidan bara väntar på klientanslutningsbegäranden innan bearbetningen är klar.

> [!IMPORTANT]
> *För multihome-enheter bestämmer NetX automatiskt källadressen som ska användas för anslutningen och nexthop-adressen baserat på anslutningens mål-IP-adress.*

### <a name="tcp-socket-state-machine"></a>TCP Socket State Machine

Anslutningen mellan två TCP-sockets (en klient och en server) är komplex och hanteras på ett tillståndsdator. Varje TCP-socket startar i stängt tillstånd. Via anslutningshändelser migreras varje sockets tillståndsdator till TILLSTÅNDET ESTABLISHED, där den största delen av dataöverföringen sker i TCP. När en sida av anslutningen inte längre vill skicka data kopplas den från. När den andra sidan har kopplat från återgår TCP-socketen till tillståndet STÄNGD. Den här processen upprepas varje gång en TCP-klient och -server upprättar och stänger en anslutning. Bild 11 visar de olika tillstånden för TCP-tillståndsdatorn.

![Tillstånd för TCP-tillståndsdatorn](./media/user-guide/states-tcp-state-machine.png)

### <a name="figure-11-states-of-the-tcp-state-machine"></a>BILD 11. Tillstånd för TCP-tillståndsdatorn

### <a name="tcp-client-connection"></a>TCP-klientanslutning

Som tidigare nämnts initierar klientsidan av TCP-anslutningen en anslutningsbegäran till en TCP-server. Innan en anslutningsbegäran kan göras måste TCP vara aktiverat på klientens IP-instans. Dessutom måste klientens TCP-socket skapas med tjänsten ***nx_tcp_socket_create** _ och bindas till en port via _*_nx_tcp_client_socket_bind tjänsten._*_ När klientsocketen har bindas *_används tjänsten_* _ nx_tcp_client_socket_connect * för att upprätta en anslutning till en TCP-server. Observera att socketen måste vara i tillståndet STÄNGD för att initiera ett anslutningsförsök. Att upprätta anslutningen börjar med att NetX utfärdar ett SYN-paket och väntar sedan på ett SYN ACK-paket tillbaka från servern, vilket innebär godkännande av anslutningsbegäran. När SYN ACK har tagits emot svarar NetX med ett ACK-paket och befordrar klientsocketen till tillståndet ESTABLISHED.

### <a name="tcp-client-disconnection"></a>TCP-klient frånkoppling

Du stänger anslutningen genom att anropa ***nx_tcp_socket_disconnect***. Om ingen spärr anges skickar klientsocketen ett RST-paket till serversocketen och placerar socketen i stängt tillstånd. Om en instängning begärs utförs annars det fullständiga TCP-frånkopplingsprotokollet enligt följande:

- Om servern tidigare initierade en frånkopplingsbegäran (klientsocketen redan har tagit emot ett FIN-paket, svarat med en ACK och är i TILLSTÅNDET STÄNG VÄNTA), befordrar NetX klientens TCP-sockettillstånd till LAST ACK-tillstånd och skickar ett FIN-paket. Den väntar sedan på en ACK från servern innan frånkopplingen slutförs och tillståndet STÄNGD.

- Om klienten å andra sidan är den första som initierar en frånkopplingsbegäran (servern har inte kopplats från och socketen fortfarande är i etablerat tillstånd), skickar NetX ett FIN-paket för att initiera frånkopplingen och väntar på att få en FIN och en ACK från servern innan frånkopplingen slutförs och socketen placeras i stängt tillstånd.

Om det fortfarande finns paket i socket överföringskön, pausar NetX för den angivna tidsgränsen så att paketen kan bekräftas. Om tidsgränsen går ut tömmer NetX överföringskön för klientsocketen.

För att ta bort bindningen av porten från klientsocketen anropar ***programmet nx_tcp_client_socket_unbind***. Socketen måste vara i stängt tillstånd eller under frånkoppling (t.ex. TIMED WAIT-tillstånd) innan porten släpps. annars returneras ett fel.

Slutligen, om programmet inte längre behöver klientsocketen anropas ***nx_tcp_socket_delete*** för att ta bort socketen.

### <a name="tcp-server-connection"></a>TCP-serveranslutning

Serversidan av en TCP-anslutning är passiv; Servern väntar alltså på att en klient ska initiera en anslutningsbegäran. Om du vill acceptera en klientanslutning måste TCP först aktiveras på IP-instansen genom att anropa tjänsten ***nx_tcp_enable** _. Därefter måste programmet skapa en TCP-socket med hjälp av tjänsten _ *_nx_tcp_socket_create_** .

Serversocketen måste också konfigureras för att lyssna efter anslutningsbegäranden. Detta uppnås med  hjälp av nx_tcp_server_socket_listen tjänsten. Den här tjänsten placerar serversocketen i LISTEN-tillstånd och binder den angivna serverporten till socketen.

> [!IMPORTANT]
> *Om du vill ange en socket listen callback-rutin anger programmet lämplig återanropsfunktion för tcp_listen_callback för **nx_tcp_server_socket_listen tjänsten.** Den här funktionen för programanrop körs sedan av NetX när en ny anslutning begärs på den här serverporten. Bearbetningen i motringning är under programkontroll.*

För att godkänna klientanslutningsbegäranden anropar programmet tjänsten ***nx_tcp_server_socket_accept** _ . Serversocketen måste antingen ha tillståndet LISTEN eller SYN RECEIVED (dvs. servern är i LISTEN-tillstånd och har tagit emot ett SYN-paket från en klient som begär en anslutning) för att anropa accept-tjänsten. En lyckad returstatus från _ *_nx_tcp_server_socket_accept_** anger att anslutningen har ställts in och att serversocketen är i tillståndet ESTABLISHED.

När serversocketen har en giltig anslutning köas ytterligare klientanslutningsbegäranden upp till det djup som anges av *listen_queue_size*, skickas till tjänsten ***nx_tcp_server_socket_listen** _ . För att kunna bearbeta efterföljande anslutningar på en serverport måste programmet anropa _ *_nx_tcp_server_socket_relisten_** med en tillgänglig socket (d.v.s. en socket med tillståndet STÄNGD). Observera att samma serversocket kan användas om den tidigare anslutningen som är associerad med socketen nu är klar och socketen är i tillståndet STÄNGD.

### <a name="tcp-server-disconnection"></a>TCP-server frånkoppling

Du stänger anslutningen genom att anropa ***nx_tcp_socket_disconnect***. Om ingen spärr har angetts skickar serversocketen ett RST-paket till klientsocketen och placerar socketen i tillståndet STÄNGD. Om en instängning begärs utförs annars det fullständiga TCP-frånkopplingsprotokollet på följande sätt: |

- Om klienten tidigare initierade en frånkopplingsbegäran (serversocketen redan har tagit emot ett FIN-paket, svarat med en ACK och är i TILLSTÅNDET STÄNG VÄNTA), höjer NetX TCP-sockettillståndet till LAST ACK-tillstånd och skickar ett FIN-paket. Den väntar sedan på en ACK från klienten innan frånkopplingen slutförs och tillståndet STÄNGD.

- Om servern å andra sidan är den första som initierar en frånkopplingsbegäran (klienten har inte kopplats från och socketen fortfarande är i etablerat tillstånd), skickar NetX ett FIN-paket för att initiera frånkopplingen och väntar på att få en FIN och en ACK från klienten innan frånkopplingen slutförs och socketen placeras i stängt tillstånd.

Om det fortfarande finns paket i socket överföringskön, pausar NetX för den angivna tidsgränsen så att dessa paket kan bekräftas. Om tidsgränsen går ut rensar NetX överföringskön för serversocketen.

När frånkopplingen har slutförts och serversocketen är i stängt tillstånd måste programmet anropa ***nx_tcp_server_socket_unaccept-tjänsten*** för att avsluta associationen mellan den här socketen och serverporten. Observera att den här tjänsten måste anropas av programmet ***även om nx_tcp_socket_disconnect*** eller ***nx_tcp_server_socket_accept** _ returnerar en felstatus. När *__nx_tcp_server_socket_unaccept_** returneras kan socketen användas som en klient- eller serversocket, eller till och med tas bort om den inte längre behövs. Om du vill acceptera en annan klientanslutning på samma serverport ***nx_tcp_server_socket_relisten*** tjänsten anropas på den här socketen.

Följande kodsegment illustrerar sekvensen med anrop som en typisk TCP-server använder:

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

### <a name="mss-validation"></a>MSS-validering

Maximal segmentstorlek (MSS) är den maximala mängden byte som en TCP-värd kan ta emot utan att fragmenteras av det underliggande IP-lagret. Under fasen för etablering av TCP-anslutning utbyter båda sina egna TCP MSS-värden, så att avsändaren inte skickar ett TCP-datasegment som är större än mottagarens MSS. NetX TCP-modulen kan validera peer-peerns annonserade MSS-värde innan en anslutning upprättas. Som standard aktiverar NetX inte en sådan kontroll. Program som vill utföra MSS-validering ska definiera ***NX_ENABLE_TCP_MSS_CHECKING** _ när du skapar NetX-biblioteket, och minimivärdet ska definieras _*_i NX_TCP_MSS_MINIMUM_*_. Inkommande TCP-anslutningar med *_MSS-värden nedan _ NX_TCP_MSS_MINIMUM_** tas bort.

### <a name="stop-listening-on-a-server-port"></a>Sluta lyssna på en serverport

Om programmet inte längre vill lyssna efter klientanslutningsbegäranden på en serverport som tidigare angavs av ett anrop till tjänsten ***nx_tcp_server_socket_listen** _ anropar programmet bara tjänsten _ *_nx_tcp_server_socket_unlisten_** . Den här tjänsten placerar alla socketar som väntar på en anslutning tillbaka i tillståndet STÄNGD och släpper eventuella paket för klientanslutningsbegäran i kö.

### <a name="tcp-window-size"></a>TCP-fönsterstorlek

Under både konfigurations- och dataöverföringsfaserna för anslutningen rapporterar varje port hur mycket data den kan hantera, vilket kallas för fönsterstorlek. När data tas emot och bearbetas justeras den här fönsterstorleken dynamiskt. I TCP kan en avsändare bara skicka en mängd data som passar in i mottagarens fönster. I princip ger fönsterstorleken flödeskontroll för dataöverföring i varje riktning av anslutningen.

### <a name="tcp-packet-send"></a>TCP-paket som skickas

Det är enkelt att skicka TCP-data genom att ***anropa nx_tcp_socket_send-funktionen.*** Om storleken på de data som överförs är större än MSS-värdet för socketen eller den aktuella peer-mottagningsfönstret, beroende på vilket som är mindre, tar TCP intern logik bort de data som passar min (MSS, peer receive Window) för överföring. Den här tjänsten skapar sedan ett TCP-huvud framför paketet (inklusive beräkningen av kontrollsumma). Om mottagarens fönsterstorlek inte är noll skickar anroparen så mycket data som möjligt för att fylla upp mottagarens fönsterstorlek. Om mottagningsfönstret blir noll kan anroparen pausa och vänta tills mottagarens fönsterstorlek ökar tillräckligt för att paketet ska skickas. Vid en given tidpunkt kan flera trådar pausas vid försök att skicka data via samma socket.

> [!IMPORTANT]
> *TCP-data som finns i NX_PACKET bör finnas på en lång ordgräns. Dessutom måste det finnas tillräckligt med utrymme mellan den förberedande pekaren och datastartspekaren för att placera TCP-, IP- och fysiska medierubriker.*

### <a name="tcp-packet-retransmit"></a>TCP-paket som skickas igen

Tidigare skickade TCP-paket lagrades faktiskt internt tills ett ACK returneras från andra sidan av anslutningen. Om överförda data inte bekräftas inom tidsgränsen skickas det lagrade paketet på ny gång och nästa timeout-period anges. När en ACK tas emot släpps slutligen alla paket som omfattas av bekräftelsenumret i den interna överföringskön.

> [!IMPORTANT]
> *Programmet får inte återanvända paketet eller ändra innehållet i paketet efter att funktionen ***nx_tcp_socket_send** _ returneras med NX_SUCCESS. Det överförda paketet släpps så småningom av intern NetX-bearbetning när data har bekräftats av den andra end._

### <a name="tcp-keepalive"></a>TCP Keepalive

Tcp Keepalive-funktionen gör att en socket kan identifiera om peer-anslutningen kopplas från utan korrekt avslutning (till exempel om peer-datorn kraschade) eller för att förhindra att vissa nätverksövervakningsaktiviteter avbryter en anslutning under långa perioder av inaktivitet. TCP Keepalive skickar regelbundet en TCP-ram utan data och sekvensnumret är inställt på ett mindre än det aktuella sekvensnumret. Vid mottagning av en sådan TCP Keepalive-ram svarar mottagaren, om den fortfarande är vid liv, med ett ACK för det aktuella sekvensnumret. Detta slutför keepalive-transaktionen.

Keepalive-funktionen är inte aktiverad som standard. Om du vill använda den här funktionen måste NetX-biblioteket byggas med ***NX_ENABLE_TCP_KEEPALIVE** _ definierat. Symbolen _ *_NX_TCP_KEEPALIVE_INITIAL_** anger antalet sekunder av inaktivitet innan keepalive-ramen initieras.

### <a name="tcp-packet-receive"></a>TCP-paket ta emot

TCP-mottagningspaketbearbetningen (anropas från IP-hjälptråden) ansvarar för att hantera olika åtgärder för anslutning och frånkoppling samt överföring av bekräftelsebearbetning. Dessutom ansvarar TCP-mottagningspaketbearbetningen för att placera paket med mottagningsdata på lämplig TCP-sockets mottagningskö eller leverera paketet till den första pausade tråden som väntar på ett paket.

### <a name="tcp-receive-notify"></a>TCP-meddelande om mottagning

Om programtråden behöver bearbeta mottagna data från mer än en socket, ***nx_tcp_socket_receive_notify-funktionen*** användas. Den här funktionen registrerar en återanropsfunktion för mottagningspaket för socketen. När ett paket tas emot på socketen körs återanropsfunktionen.

Innehållet i återanropsfunktionen är programspecifikt. Funktionen skulle dock sannolikt innehålla logik för att informera bearbetningstråden om att ett paket är tillgängligt på motsvarande socket.

### <a name="thread-suspension"></a>Trådavstängning

Som tidigare nämnts kan programtrådar pausa vid försök att ta emot data från en viss TCP-port. När ett paket tas emot på den porten ges det till den första tråden som pausas och tråden återupptas sedan. En valfri tidsgräns är tillgänglig när du pausar på ett TCP-mottagningspaket, en funktion som är tillgänglig för de flesta NetX-tjänster.

Trådavstängning är också tillgängligt för anslutning (både klient och server), klientbindning och frånkopplingstjänster.

### <a name="tcp-socket-statistics-and-errors"></a>Statistik och fel för TCP-socket

Om den är aktiverad håller NetX TCP-socketprogrammet reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP/TCP-instans:

- Totalt antal TCP-paket som skickats
- Totalt antal TCP-byte som skickats
- Totalt antal mottagna TCP-paket
- Totalt antal mottagna TCP-byte
- Totalt antal ogiltiga TCP-paket
- Totalt antal bort ignorerade TCP-mottagningspaket
- Totalt antal fel vid TCP-mottagning av kontrollsumma
- Totalt antal TCP-anslutningar
- Totalt antal TCP-frånkopplingar
- Totalt antal tcp-anslutningar som har tagits bort
- Totalt antal OMöverföringar av TCP-paket
- TCP Socket-paket som skickats
- SKICKADE TCP-socketbyte
- Mottagna TCP Socket-paket
- Mottagna TCP-socketbyte
- TCP Socket-paket skickas igen
- TCP Socket-paket i kö
- Tcp Socket Checksum-fel
- TCP-sockettillstånd
- Överföringsködjup för TCP Socket
- Tcp Socket-överföringsfönstrets storlek
- Tcp Socket-mottagningsfönstrets storlek

Alla dessa statistik- och felrapporter är tillgängliga för programmet med tjänsten ***nx_tcp_info_get** _ för total TCP-statistik och tjänsten _ *_nx_tcp_socket_info_get_** för TCP-statistik per socket.

## <a name="tcp-socket-control-block-nx_tcp_socket"></a>TCP Socket Control Block NX_TCP_SOCKET

Egenskaperna för varje TCP-socket finns i det associerade NX_TCP_SOCKET-kontrollblocket, som innehåller användbar information, till exempel länken till IP-datastrukturen, gränssnittet för nätverksanslutning, den bundna porten och kön för att ta emot paket.  Den här strukturen definieras i ***nx_api.h-filen.***
