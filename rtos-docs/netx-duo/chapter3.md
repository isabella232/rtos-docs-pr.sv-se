---
title: Kapitel 3 – Funktionella komponenter i Azure RTOS NetX Duo
description: Det här kapitlet innehåller en beskrivning av högpresterande TCP/IP-stacken Azure RTOS NetX Duo ur ett funktionellt perspektiv.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 32af483db1f97b45bfe3d334b8c79d984dedc8470a37ce1d4164331549b6954c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789056"
---
# <a name="chapter-3---functional-components-of-azure-rtos-netx-duo"></a>Kapitel 3 – Funktionella komponenter i Azure RTOS NetX Duo

Det här kapitlet innehåller en beskrivning av högpresterande TCP/IP-stacken Azure RTOS NetX Duo ur ett funktionellt perspektiv. 

## <a name="execution-overview"></a>Körningsöversikt

Det finns fem typer av programkörning i ett NetX Duo-program: initiering, anrop till programgränssnitt, intern IP-tråd, periodiska IP-timers och nätverksdrivrutinen.

> [!NOTE]
> *NetX Duo förutsätter att ThreadX finns och är beroende av trådkörningen, uppstängningen, periodiska timers och ömsesidig exkludering.*

### <a name="initialization"></a>Initiering

Tjänsten ***nx_system_initialize** _ måste anropas innan någon annan NetX Duo-tjänst anropas. Systemitiering kan anropas antingen från funktionen ThreadX _ *_tx_application_define_** eller från programtrådar.

När ***nx_system_initialize** _ returneras är systemet redo att skapa paketpooler och IP-instanser. Eftersom skapandet av en IP-instans kräver en standardpaketpool måste det finnas minst en NetX Duo-paketpool innan du skapar en IP-instans. Att skapa paketpooler och IP-instanser tillåts från ThreadX-initieringsfunktionen _ *_tx_application_define_** och från programtrådar.

Internt sker skapandet av en IP-instans i två delar: Den första delen görs i kontexten för anroparen, antingen ***från tx_application_define*** eller från en programtråds kontext. Detta inkluderar att konfigurera IP-datastrukturen och skapa olika IP-resurser, inklusive den interna IP-tråden. Den andra delen utförs under den första körningen från den interna IP-tråden. Det är här som nätverksdrivrutinen, som angavs när den första delen av IP-skapandet, först anropas. Genom att anropa nätverksdrivrutinen från den interna IP-tråden kan drivrutinen utföra I/O och pausa under initieringsbearbetningen.

När nätverksdrivrutinen återgår från initieringen är IP-skapandet klart.

Initiering av IPv6 i NetX Duo kräver några ytterligare NetX Duo-tjänster. Dessa beskrivs mer detaljerat i avsnittet [IPv6 i NetX Duo senare](#ipv6-in-netx-duo) i det här kapitlet.

> [!NOTE]
> *Tjänsten NetX Duo **nx_ip_status_check** tillgänglig för att hämta information om IP-instansen och dess primära gränssnittsstatus. Statusinformationen omfattar huruvida länken har initierats, aktiverats och IP-adressen har lösts. Den här informationen används för att synkronisera programtrådar som behöver använda en nyligen skapad IP-instans. Information om multihome-system finns [i Multihome-stöd.](#multihome-support) **nx_ip_interface_status_check** tillgänglig för att få 3 information på det angivna gränssnittet.*

### <a name="application-interface-calls"></a>Anrop till programgränssnitt

Anrop från programmet görs huvudsakligen från programtrådar som körs under ThreadX RTOS. Vissa initierings-, create- och enable-tjänster kan dock anropas ***från tx_application_define***. Avsnitten "Tillåten från" i kapitel 4 – beskrivning [av Azure RTOS NetX Duo Services](chapter4.md) anger från vilka varje NetX Duo-tjänst kan anropas.

I de flesta fall utförs bearbetningsintensiva aktiviteter som beräkning av kontrollsumor i den anropande trådens kontext – utan att blockera åtkomsten till andra trådar till IP-instansen. Vid överföring utförs till exempel UDP-kontrollsummaberäkningen inuti tjänsten ***nx_udp_socket_send** _ innan den underliggande IP-sändningsfunktionen anropas. På ett mottaget paket beräknas UDP-kontrollsumman i tjänsten _ *_nx_udp_socket_receive_** som körs i för programtråden. Detta förhindrar att nätverksbegäranden av trådar med högre prioritet stoppas på grund av bearbetning av intensiv beräkning av kontrollsumma i trådar med lägre prioritet.

Värden, till exempel IP-adresser och portnummer, skickas till API:er i värdbyteordning. Internt lagras även dessa värden i värdbyteordning. På så sätt kan utvecklare enkelt visa värdena via ett felsökningsfel. När dessa värden programmeras till en ram för överföring konverteras de till nätverkets byteordning.

### <a name="internal-ip-thread"></a>Intern IP-tråd

Som tidigare nämnts har varje IP-instans i NetX Duo en egen tråd. Prioritet och stackstorlek för den interna IP-tråden definieras i ***nx_ip_create tjänsten.*** Den interna IP-tråden skapas i ett körklart läge. Om IP-tråden har högre prioritet än anropstråden kan avbrott ske i IP-skapa-anropet.

Startpunkten för den interna IP-tråden finns i den interna funktionen _ ***nx_ip_thread_entry***. När den startas slutför den interna IP-tråden först initieringen av nätverksdrivrutiner, som består av att göra tre anrop till den programspecifika nätverksdrivrutinen. Det första anropet är att koppla nätverksdrivrutinen till IP-instansen, följt av ett initieringssamtal, vilket gör att nätverksdrivrutinen kan gå igenom initieringsprocessen. När nätverksdrivrutinen återgår från initieringen (den kan pausa medan den väntar på att maskinvaran ska vara korrekt konfigurerad) anropar den interna IP-tråden nätverksdrivrutinen igen för att aktivera länken. När nätverksdrivrutinen har returnerat från länkaktivera anropet anger den interna IP-tråden en för alltid-loopkontroll för olika händelser som behöver bearbetas för den här IP-instansen. Händelser som bearbetas i den här loopen omfattar uppskjuten mottagning av IP-paket, sammansättningen av IP-paketfragment, ICMP-pingbearbetning, IGMP-bearbetning, BEARBETNING av TCP-paketkö, regelbunden TCP-bearbetning, tidsgränser för IP-fragmentsammansättningen och periodisk IGMP-bearbetning. Händelser omfattar även adresslösningsaktiviteter; ARP-paketbearbetning och periodisk ARP-bearbetning i IPv4, dubblettadressidentifiering, router-begäran och grannidentifiering i IPv6.

> [!CAUTION]
> *NetX Duo-återanropsfunktioner, inklusive lyssna och koppla från återanrop, anropas från den interna IP-tråden – inte den ursprungliga anropstråden. Programmet måste se till att inte pausa i någon NetX Duo-återanropsfunktion.*

### <a name="ip-periodic-timers"></a>Periodiska IP-timers

Det finns två periodiska ThreadX-timers som används för varje IP-instans. Den första timern är en sekund för ARP, IGMP, TCP-timeout och den kör även bearbetningen av IP-fragmentet på nytt. Den andra timern är en 100 ms timer som kör TCP-tidsgränsen för återöverföring och IPv6-relaterade åtgärder.

### <a name="network-driver"></a>Nätverksdrivrutin

Varje IP-instans i NetX Duo har ett primärt gränssnitt som identifieras av dess enhetsdrivrutin som anges ***i nx_ip_create*** tjänsten. Nätverksdrivrutinen ansvarar för att hantera olika NetX Duo-begäranden, inklusive paketöverföring, paketmottagande och begäranden om status och kontroll. 

För ett system med flera hem har IP-instansen flera gränssnitt, var och en med en associerad nätverksdrivrutin som utför dessa uppgifter för respektive gränssnitt.

Nätverksdrivrutinen måste också hantera asynkrona händelser som inträffar på mediet. Asynkrona händelser från mediet omfattar paketmottagande, slutförande av paketöverföring och statusändringar. NetX Duo ger nätverksdrivrutinen flera åtkomstfunktioner för att hantera olika händelser. Dessa funktioner är utformade för att anropas från avbrottstjänstens rutindel av nätverksdrivrutinen. För IPv4-nätverk bör nätverksdrivrutinen vidarebefordra alla ARP-paket som tas emot ***_nx_arp_packet_deferred_receive*** interna funktionen. Alla RARP-paket ska vidarebefordras till ***_nx_rarp_packet_deferred_receive** _ intern funktion. Det finns två alternativ för IP-paket. Om snabb sändning av IP-paket krävs, ska inkommande IP-paket vidarebefordras till *_ _nx_ip_packet_receive_* _ för omedelbar bearbetning. Detta förbättrar avsevärt NetX Duo-prestanda vid hantering av IP-paket. Annars bör vidarebefordran av IP-paket *till _ _nx_ip_packet_deferred_receive_** göras. Den här tjänsten placerar IP-paketet i kön för uppskjuten bearbetning där det sedan hanteras av den interna IP-tråden, vilket resulterar i minsta bearbetningstid för ISR.

Nätverksdrivrutinen kan också skjuta upp avbrottsbearbetningen för att få slut på IP-trådens kontext. I det här läget ska ISR spara nödvändig information, anropa den interna ***funktionen _nx_ip_driver_deferred_processing*** och bekräfta avbrottsstyrenheten. Den här tjänsten meddelar IP-tråden om att schemalägga ett återanrop till enhetsdrivrutinen för att slutföra processen för den händelse som orsakar avbrottet.

Vissa nätverksstyrenheter kan utföra beräkning och validering av tcp/IP-huvudkontrollsumma i maskinvara, utan att ta upp värdefulla CPU-resurser. För att dra nytta av funktionen för maskinvarukapacitet, tillhandahåller NetX Duo alternativ för att aktivera eller inaktivera olika beräkningar av programkontrollsumma vid kompilering, samt att aktivera eller inaktivera beräkning av kontrollsumma vid körning, om enhetsdrivrutinen kan kommunicera med IP-lagret om är maskinvarufunktioner. Se [kapitel 5 – Azure RTOS NetX Duo-nätverksdrivrutiner](chapter5.md) för mer detaljerad information om hur du skriver NetX Duo-nätverksdrivrutiner.

### <a name="multihome-support"></a>Stöd för flera start

NetX Duo stöder system som är anslutna till flera fysiska enheter med en enda IP-instans. Varje fysiskt gränssnitt tilldelas till ett gränssnittskontrollblock i IP-instansen. Program som vill använda ett multihome-system måste definiera värdet för ***NX_MAX_PHSYCIAL_INTERFACES** _ till antalet fysiska enheter som är anslutna till systemet och återskapa NetX Duo-biblioteket. Som standard är _ *_NX_MAX_PHYSICAL_INTERFACES_** inställt på ett, vilket skapar ett gränssnittskontrollblock i IP-instansen.

NetX Duo-programmet skapar en enskild IP-instans för den primära enheten med hjälp av tjänsten ***nx_ip_create** _ . För varje ytterligare nätverksenheter ansluter programmet enheten till IP-instansen med hjälp av tjänsten _ *_nx_ip_interface_attach_** .

Varje nätverksgränssnittsstruktur innehåller en delmängd av nätverksinformationen om nätverksgränssnittet som finns i IP-kontrollblocket, inklusive gränssnitts-IPv4-adress, nätmask, IP MTU-storlek och ADRESSinformation på MAC-nivå.

> [!NOTE]
> *NetX Duo med stöd för multihome är bakåtkompatibel med tidigare versioner av NetX Duo. Tjänster som inte tar explicit gränssnittsinformation som standard till den primära nätverksenheten.*

Det primära gränssnittet har index noll i listan över IP-instanser. Varje efterföljande enhet som är ansluten till IP-instansen tilldelas nästa index.

Alla protokolltjänster på den övre nivån som IP-instansen är aktiverad för, inklusive TCP, UDP, ICMP och IGMP, är tillgängliga för alla anslutna enheter.

I de flesta fall kan NetX Duo avgöra den bästa källadressen som ska användas vid överföring av ett paket. Valet av källadress baseras på måladressen. NetX Duo-tjänster läggs till så att program kan ange en specifik källadress att använda, i de fall där den lämpligaste inte kan fastställas av måladressen. Ett exempel är i ett multihome-system. Ett program måste skicka ett paket till en IPv4-sändning eller multicast-måladress.

Tjänster som är specifika för utveckling av program med flera startprogram omfattar följande:

- *nx_igmp_multicast_interface_join*
- *nx_igmp_multicast_interface_leave*
- *nx_ip_driver_interface_direct_command*
- *nx_ip_interface_address_get*
- *nx_ip_interface_address_mapping_configure*
- *nx_ip_interface_address_set*  
- *nx_ip_interface_attach*
- *nx_ip_interface_capability_get* 
- *nx_ip_interface_capability_set*
- *nx_ip_interface_detach*
- *nx_ip_interface_info_get*
- *nx_ip_interface_mtu_set*
- *nx_ip_interface_physical_address_get*
- *nx_ip_interface_physical_address_set*
- *nx_ip_interface_status_check*
- *nx_ip_raw_packet_source_send*
- *nx_ipv4_multicast_interface_join*
- *nx_ipv4_multicast_interface_leave*
- *nx_udp_socket_source_send*
- *nxd_ipv6_multicast_interface_join*
- *nxd_ipv6_multicast_interface_leave* 
- *nxd_udp_socket_source_send*
- *nxd_icmp_source_ping*
- *nxd_ip_raw_packet_source_send*
- *nxd_udp_socket_source_send*

Dessa tjänster förklaras mer detaljerat i [Beskrivning av NetX Duo Services](chapter4.md).

### <a name="loopback-interface"></a>Loopback-gränssnitt

Loopback-gränssnittet är ett särskilt nätverksgränssnitt utan en fysisk länk kopplad till. Loopback-gränssnittet gör att program kan kommunicera med IPv4-loopbackadressen 127.0.0.1 Om du vill använda ett logiskt loopback-gränssnitt måste du se till att det ***konfigurerbara NX_DISABLE_LOOPBACK_INTERFACE*** inte har angetts.

### <a name="interface-control-blocks"></a>Gränssnittskontrollblock

Antalet gränssnittskontrollblock i IP-instansen är antalet fysiska gränssnitt (definieras av ***NX_MAX_PHYSICAL_INTERFACES** _) plus loopback-gränssnittet om det är aktiverat. Det totala antalet gränssnitt definieras i _*_NX_MAX_IP_INTERFACES_**.

## <a name="protocol-layering"></a>Protokollskiktning

TCP/IP som implementeras av NetX Duo är ett flerskiktat protokoll, vilket innebär att mer komplexa protokoll bygger på enklare underliggande protokoll. I TCP/IP är protokollet på det lägsta lagret på *länknivå* och hanteras av nätverksdrivrutinen. Den här nivån är vanligtvis riktad mot Ethernet, men den kan också vara fiber, seriell eller praktiskt taget alla fysiska media.

Ovanpå länklagret finns *nätverkslagret*. I TCP/IP är detta IP-adressen, som i princip ansvarar för att skicka och ta emot enkla paket – på bästa sätt – i nätverket. Protokoll av hanteringstyp som ICMP och IGMP kategoriseras vanligtvis också som nätverkslager, även om de förlitar sig på IP för att skicka och ta emot.

*Transportlagret* ligger ovanpå nätverkslagret. Det här lagret ansvarar för att hantera dataflödet mellan värdar i nätverket. Det finns två typer av transporttjänster som stöds av NetX Duo: UDP och TCP. UDP-tjänster gör det möjligt att skicka och ta emot data mellan två värdar på ett anslutningslöst sätt, medan TCP tillhandahåller tillförlitlig anslutningsorienterad tjänst mellan två värdentiteter.

Den här skiktningen återspeglas i de faktiska nätverksdatapaketen. Varje lager i TCP/IP innehåller ett informationsblock som kallas rubrik. Den här tekniken med omgivande data (och eventuellt protokollinformation) med en rubrik kallas vanligtvis för datainkapsling. Bild 1 visar ett exempel på NetX Duo-lager och bild 2 visar den resulterande datainkapsling för UDP-data som skickas.

![Protokollskiktning](./media/user-guide/image12.jpg)

**BILD 1. Protokollskiktning**

## <a name="packet-pools"></a>Paketpooler

Att allokera paket på ett snabbt och deterministiskt sätt är alltid en utmaning i realtidsnätverksprogram. Med detta i åtanke ger NetX Duo möjligheten att skapa och hantera flera pooler med nätverkspaket med fast storlek.

Eftersom NetX Duo-paketpooler består av minnesblock med fast storlek finns det aldrig några interna fragmenteringsproblem. Fragmentering orsakar naturligtvis beteenden som inte är obestämda. Dessutom utgör den tid som krävs för att allokera och frigöra ett NetX Duo-paket till enkel manipulering av länkade listor. Dessutom sker paketallokering och avallokering i den tillgängliga listans huvud. Detta ger den snabbaste möjliga länkade listbearbetningen.

![UDP-datainkapsling](./media/user-guide/image13.png)

**BILD 2. UDP-datainkapsling**

Brist på flexibilitet är vanligtvis den största nackdelen med paketpooler med fast storlek. Det är svårt att avgöra vilken optimal paketnyttolaststorlek som också hanterar det värsta inkommande paketet. NetX Duo-paketen åtgärdar det här problemet med en valfri funktion som kallas paketkedjekedja. Ett faktiskt nätverkspaket kan göras av ett eller flera NetX Duo-paket som är länkade till varandra. Dessutom har pakethuvudet en pekare överst i paketet. När ytterligare protokoll läggs till flyttas pekaren helt enkelt bakåt och det nya huvudet skrivs direkt framför data. Utan den flexibla pakettekniken skulle stacken behöva allokera en annan buffert och kopiera data till en ny buffert med det nya huvudet, vilket är bearbetningsintensivt.

Eftersom varje paketnyttolaststorlek är fast för en viss paketpool skulle programdata som är större än nyttolasten kräva flera paket som är sammankedjade. När ett paket fylls med användardata ska programmet använda tjänsten ***nx_packet_data_append***. Den här tjänsten flyttar programdata till ett paket. I situationer där ett paket inte är tillräckligt för att lagra användardata allokeras ytterligare paket för att lagra användardata. Om du vill använda länkning av paket måste drivrutinen kunna ta emot till eller överföra från kedjade paket.

För inbäddade system som inte behöver använda funktionen för paketkedjekedja kan NetX Duo-biblioteket byggas med ***NX_DISABLE_PACKET_CHAIN** _ för att ta bort logiken för paketkedja. Observera att funktionen IP-fragmentering och återmontering kan behöva använda funktionen för kedjade paket. Därför _*_definieras NX_DISABLE_PACKET_CHAIN_*_ kräver _ *_NX_DISABLE_FRAGMENTATION_** definieras. 

Varje NetX Duo-paketminnespool är en offentlig resurs. NetX Duo har inga begränsningar för hur paketpooler används. 

### <a name="packet-pool-memory-area"></a>Minnesområde för paketpool

Minnesområdet för paketpoolen anges när paketet skapas. Precis som andra minnesområden för ThreadX- och NetX Duo-objekt kan den finnas var som helst i målets adressutrymme. 

Det här är en viktig funktion på grund av den stora flexibilitet som programmet får. Anta till exempel att en kommunikationsprodukt har ett minnesområde med hög hastighet för nätverksbuffertar. Det här minnesområdet används enkelt genom att göra det till en NetX Duo-paketminnespool.

### <a name="creating-packet-pools"></a>Skapa paketpooler

Paketpooler skapas antingen under initieringen eller under körning av programtrådar. Det finns inga begränsningar för antalet paketminnespooler i ett NetX Duo-program.

### <a name="dual-packet-pool"></a>Dubbel paketpool

Normalt är nyttolasten för IP-paketpoolens standardstorlek tillräckligt stor för ramstorleken upp till nätverksgränssnittet för MTU. Under normal drift måste IP-tråden skicka meddelanden som ARP, TCP-kontrollmeddelanden, IGMP-meddelanden och ICMPv6-meddelanden. Dessa meddelanden använder de paket som allokerats från standardpaketpoolen i IP-instansen. I ett minnesbegränsat system där mängden tillgängligt minne för paketpoolen är begränsad kanske inte en optimal lösning är att använda en enda paketpool (med den stora nyttolaststorleken för att matcha MTU-storleken). Med NetX Duo kan programmet installera en extra paketpool, där nyttolasten är mindre. När den extra paketpoolen har installerats allokerar IP-hjälptråden paket från antingen standardpaketpoolen eller den extra poolen, beroende på storleken på det meddelande som den skickar. För en extra paketpool skulle en nyttolaststorlek på 200 byte fungera med de flesta meddelanden som IP-hjälptråden överför.

Som standard är NetX Duo-biblioteket byggt utan att aktivera dubbla paketpooler. Om du vill aktivera funktionen skapar du biblioteket med ***NX_DUAL_PACKET_POOL_ENABLE** _ definierat. Den extra paketpoolen kan sedan anges genom att anropa _*_nx_ip_auxiliary_packet_pool_set_**.

Det finns också möjlighet att skapa fler än en paketpool. Till exempel skapas en överföringspaketpool med optimal nyttolaststorlek för förväntade meddelandestorlekar. En paketpool för mottagning skapas i drivrutinen med en nyttolaststorlek inställd på drivrutinens MTU, eftersom man inte kan förutsäga storleken på mottagna paket.

### <a name="packet-header-nx_packet"></a>Pakethuvud NX_PACKET   
Som standard placerar NetX Duo pakethuvudet omedelbart före paketets nyttolastområde. Paketminnespoolen är i princip en serie paket – huvuden som följs direkt av paketets nyttolast. Pakethuvudet (***NX_PACKET***) och layouten för paketpoolen visas på bild 3.

För nätverksdrivrutiner som kan utföra nollkopieringsåtgärder programmeras vanligtvis startadressen för paketets nyttolastområde i DMA-logiken. Vissa DMA-motorer har justeringskrav i nyttolastområdet. För att göra så att startadressen för nyttolastens område justeras korrekt för DMA-motorn, eller cacheåtgärden, kan användaren definiera symbolen ***NX_PACKET_ALIGNMENT***.

> [!WARNING]
> *Det är viktigt att nätverksdrivrutinen använder **nx_packet_transmit_release** när överföringen av ett paket är klar. Den här funktionen kontrollerar att paketet inte är en del av en TCP-utdatakö innan det faktiskt placeras tillbaka i den tillgängliga poolen.*

![Pakethuvud och paketpoollayout](./media/user-guide/image14.jpg)

**BILD 3. Pakethuvud och paketpoollayout**

Fälten i pakethuvudet definieras på följande sätt. Observera att den här tabellen inte är en omfattande lista över alla medlemmar i *NX_PACKET* struktur.

|Pakethuvud | Syfte |
|---|---|
|***nx_packet_pool_owner***|Det här fältet pekar på paketpoolen som äger det här paketet. När paketet släpps släpps det till den här specifika poolen. Med poolägarskapet i varje paket är det möjligt för ett datagram att sträcka sig över flera paket från flera paketpooler.|
|***nx_packet_next** _|Det här fältet pekar på nästa paket inom samma ram. Om null är null finns det inga ytterligare paket som ingår i ramen. Det här fältet används också för att hålla fragmenterade paket tills hela paketet kan sättas ihop på ett annat sätt. den tas bort om _*_NX_DISABLE_PACKET_CHAIN_**har definierats.|
|***nx_packet_last** _|Det här fältet pekar på det sista paketet inom samma nätverkspaket. Om VÄRDET ÄR NULL representerar det här paketet hela nätverkspaket. Det här fältet tas bort om _*_NX_DISABLE_PACKET_CHAIN_**har definierats.|
|***nx_packet_length** _| Det här fältet innehåller det totala antalet byte i hela nätverkspaket, inklusive totalsumman för alla byte i alla paket som är sammankedjade av _nx_packet_next*medlemmen.|
|***nx_packet_ip_interface***| Det här fältet är gränssnittskontrollblocket som tilldelas paketet när det tas emot av gränssnittsdrivrutinen och av NetX Duo för utgående paket. Ett gränssnittskontrollblock beskriver gränssnittet, t.ex. nätverksadress, MAC-adress, IP-adress och gränssnittsstatus, till exempel länkaktiverad och fysisk mappning som krävs.|
|***nx_packet_data_start** _| Det här fältet pekar på början av paketets fysiska nyttolastområde. Det behöver inte omedelbart följa NX_PACKET sidhuvud, men det är standardvärdet för tjänsten _ *_nx_packet_pool_create_** .|
|***nx_packet_data_end** _|Det här fältet pekar på slutet av paketets fysiska nyttolastområde. Skillnaden mellan det här fältet och _nx_packet_data_start*-fältet representerar nyttolastens storlek.|
|***nx_packet_prepend_ptr** _|Det här fältet pekar på platsen där paketdata, antingen protokollhuvud eller faktiska data, läggs till framför befintliga paketdata (om det finns några) i paketets nyttolastområde. Det måste vara större än eller lika med _nx_packet_data_start*-pekarens plats och mindre än eller lika med *nx_packet_append_ptr pekaren.*|
> [!CAUTION]
> *Av prestandaskäl förutsätter NetX Duo att när paketet skickas till NetX Duo-tjänster för överföring pekar den förberedda pekaren på en lång ordjusterad adress.*

| Pakethuvud | Syfte |
|---|---|
|***nx_packet_append_ptr** _|Det här fältet pekar på slutet av de data som för närvarande finns i paketets nyttolastområde. Den måste finnas mellan den minnesplats som _nx_packet_prepend_ptr* och *nx_packet_data_end.* Skillnaden mellan det här fältet och *nx_packet_prepend_ptr* representerar mängden data i det här paketet.|
|***nx_packet_packet_pad** _|Det här fältet definierar längden på utfyllnad i 4 byte-ord för att uppnå önskat justeringskrav. Det här fältet tas bort _*_om NX_PACKET_HEADER_PAD_*_ inte har definierats. Du kan _*_NX_PACKET_ALIGNMENT_*_ i stället för att definiera _nx_packet_header_pad.*|

### <a name="packet-header-offsets"></a>Förskjutningar av pakethuvud

Pakethuvudstorleken definieras för att ge tillräckligt med utrymme för rubrikens storlek. Tjänsten ***nx_packet_allocate*** används för att allokera ett paket och justerar förberedelsepekaren i paketet enligt den typ av paket som anges. Pakettypen talar om för NetX Duo vilken förskjutning som krävs för att infoga protokollhuvudet (till exempel UDP, TCP eller ICMP) framför protokolldata.

Följande typer definieras i NetX Duo för att ta hänsyn till IP-huvudet och ethernet-huvudet (fysiskt lager) i paketet. I det senare fallet antas det vara 16 byte med den nödvändiga justeringen på 4 byte i beräkningen. IPv4-paket definieras fortfarande i NetX Duo för program som allokerar paket för IPv4-nätverk. Observera att om NetX Duo-biblioteket har skapats med IPv6 aktiverat mappas de allmänna pakettyperna (till exempel NX_IP_PACKET) till IPv6-versionen. Om NetX Duo-biblioteket har skapats utan IPv6 aktiverat mappas dessa allmänna pakettyper till IPv4-versionen.

I följande tabell visas symboler som definierats med IPv6 aktiverat:

|**Pakettyp** |**Värde** |
|---|---|
|NX_IPv6_PACKET (NX_IP_PACKET) | 0x38 |
|NX_UDPv6_PACKET (NX_UDP_PACKET) |0x40 |
|NX_TCPv6_PACKET (NX_TCP_PACKET) |0x4c |
|NX_IPv4_PACKET |0x24 |
|NX_IPv4_UDP_PACKET |0x2c |
|NX_IPv4_TCP_PACKET |0x38 |

I följande tabell visas symboler som definierats med IPv6 inaktiverat:

|**Pakettyp** |**Värde** |
|---|---|
|NX_IPv4_PACKET (NX_IP_PACKET) |0x24 |
|NX_IPv4_UDP_PACKET (NX_UDP_PACKET) |0x2c |
|NX_IPv4_TCP_PACKET (NX_TCP_PACKET) |0x38 |

Observera att dessa värden ändras om *NX_IPSEC_ENABLE* har definierats. Mer information finns i Användarhandbok för NetX Duo IPsec för program som använder IPsec.

### <a name="pool-capacity"></a>Poolkapacitet

Antalet paket i en paketpool är en funktion av nyttolastens storlek och det totala antalet byte i det minnesområde som levereras till tjänsten för att skapa paketpoolen. Poolens kapacitet beräknas genom att dela upp paketstorleken (inklusive storleken på NX_PACKET-huvudet, nyttolastens storlek och korrekt justering) i det totala antalet byte i det angivna minnesområdet.

### <a name="payload-area-alignment"></a>Justering av nyttolastområde

Paketpoolsdesignen i NetX Duo stöder nollkopiering. På enhetsdrivrutinsnivå kan drivrutinen tilldela nyttolastområdet direkt till buffertbeskrivningar för datamottagande. Ibland kräver DMA-motorn eller cachesynkroniseringsmekanismen startadressen för nyttolastområdet för att ha ett visst justeringskrav. Detta kan uppnås genom att definiera önskat justeringskrav (i byte) i ***NX_PACKET_ALIGNMENT***. När du skapar en paketpool justeras startadressen för nyttolastområdet till det här värdet. Som standard är startadressen 4 byte justerad.

### <a name="thread-suspension"></a>Trådavstängning

Programtrådar kan pausas i väntan på ett paket från en tom pool. När ett paket returneras till poolen får den pausade tråden det här paketet och återupptas.

Om flera trådar pausas i samma paketpool återupptas de i den ordning de pausades (FIFO).

### <a name="pool-statistics-and-errors"></a>Poolstatistik och fel

Om den är aktiverad håller NetX Duo-pakethanteringsprogrammet reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för paketpooler:

- Totalt antal paket i pool
- Kostnadsfria paket i pool
- Totalt antal paketallokeringar
- Pool – tomma allokeringsbegäranden
- Allokeringsavstängningar för pool tom
- Ogiltiga paketsläppningar

Alla dessa statistik- och felrapporter, förutom det totala och antalet kostnadsfria paket i poolen, är inbyggda i NetX Duo-biblioteket såvida inte ***NX_DISABLE_PACKET_INFO** _ har definierats. Dessa data är tillgängliga för programmet med tjänsten _ *_nx_packet_pool_info_get_** .

### <a name="packet-pool-control-block-nx_packet_pool"></a>Blockblockering för paketpoolkontroll NX_PACKET_POOL

Egenskaperna för varje paketminnespool finns i dess kontrollblock. Den innehåller användbar information, till exempel den länkade listan över kostnadsfria paket, antalet kostnadsfria paket och nyttolaststorleken för paket i den här poolen. Den här strukturen definieras i ***nx_api.h-filen.***

Kontrollblock för paketpooler kan finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion.

## <a name="ipv4-protocol"></a>IPv4-protokoll

Ip Internet Protocol komponenten i NetX Duo ansvarar för att skicka och ta emot IPv4-paket på Internet. I NetX Duo är det komponenten som i slutändan ansvarar för att skicka och ta emot TCP-, UDP-, ICMP- och IGMP-meddelanden med hjälp av den underliggande nätverksdrivrutinen.

NetX Duo stöder både IPv4-protokollet (RFC 791) och IPv6-protokollet (RFC 2460). I det här avsnittet beskrivs IPv4. IPv6 beskrivs i nästa avsnitt.

### <a name="ipv4-addresses"></a>IPv4-adresser

Varje värd på Internet har en unik 32-bitars identifierare som kallas för en IP-adress. Det finns fem klasser med IPv4-adresser enligt beskrivningen i bild 4. Intervallen för de fem IPv4-adressklasserna är följande:

|Klass|Intervall|
|---|---|
|A |0.0.0.0 till 127.255.255.255|
|B |128.0.0.0 till 191.255.255.255|
|C |192.0.0.0 till 223.255.255.255|
|D |224.0.0.0 till 239.255.255.255|
|E |240.0.0.0 till 247.255.255.255|

![Diagram över IPv4-adressstrukturen.](./media/user-guide/ipv4-address-structure.png)

### <a name="figure-4-ipv4-address-structure"></a>BILD 4. IPv4-adressstruktur

Det finns också tre typer av adressspecifikationer: *unicast,* *broadcast* och *multicast.* Unicast-adresser är de IPv4-adresser som identifierar en specifik värd på Internet. Unicast-adresser kan vara antingen en käll- eller mål-IPv4-adress. En broadcast-adress identifierar alla värdar i ett visst nätverk eller undernätverk och kan bara användas som måladresser. Broadcast-adresser anges genom att värd-ID-delen av adressen anges till ettor. Multicast-adresser (klass D) anger en dynamisk grupp med värdar på Internet. Medlemmar i multicast-gruppen kan gå med och lämna när de vill.

> [!IMPORTANT]
> *Endast anslutningslösa protokoll som UDP över IPv4 kan använda broadcast och den begränsade sändningsfunktionerna i multicast-gruppen.*

> [!IMPORTANT]
> *Makron *IP_ADDRESS* i ***nx_api.h** _. Det gör det enkelt att specificering av IPv4-adresser med kommatecken i stället för en punkter. Till exempel anger _IP_ADDRESS(128,0,0,0)* den första klassens B-adress som visas i bild 4.*

### <a name="ipv4-gateway-address"></a>IPv4-gatewayadress

Nätverksgatewayer hjälper värdar i deras nätverk att vidarebefordra paket till mål utanför den lokala domänen. Varje nod har viss kunskap om vilket nästa hopp som ska skickas till, antingen målet någon av sina grannar eller via en förprogrammerad statisk routningstabell. Men om dessa metoder misslyckas bör noden vidarebefordra paketet till sin standardgateway som har bättre kunskap om hur paketet ska dirigeras till sitt mål. Observera att standardgatewayen måste vara direkt åtkomlig via ett av de fysiska gränssnitt som är anslutna till IP-instansen. Programmet anropar ***nx_ip_gateway_address_set** _ för att konfigurera IPv4-standardgatewayadressen. Använd tjänstinställningarna _*_nx_ip_gateway_address_get_*_ att hämta de aktuella IPv4-gatewayinställningarna. Programmet ska använda tjänsten _ *_nx_ip_gateway_address_clear_** för att rensa gatewayinställningen.

### <a name="ipv4-header"></a>IPv4-rubrik

För att ett IPv4-paket ska kunna skickas på Internet måste det ha ett IPv4-huvud. När protokoll på högre nivå (UDP, TCP, ICMP eller IGMP) anropar IP-komponenten för att skicka ett paket, placerar IPv4-överföringsmodulen ett IPv4-huvud framför data. När IP-paket tas emot från nätverket tar IP-komponenten omvänt bort IPv4-huvudet från paketet innan de levereras till protokollen på högre nivå. Bild 5 visar formatet för IP-huvudet.

![IPv4-rubrikformat](./media/user-guide/ipv4-header-format.png)

### <a name="figure-5-ipv4-header-format"></a>BILD 5. IPv4-rubrikformat

> [!IMPORTANT]
> *Alla huvuden i TCP/IP-implementeringen förväntas vara i **big endian** format. I det här formatet finns den viktigaste byten av ordet på den lägsta byteadressen. Till exempel måste 4-bitarsversionen och 4-bitars huvudlängden för IP-huvudet finnas på den första byten i rubriken.*

Fälten i IPv4-huvudet definieras på följande sätt:

|&nbsp;IPv4-rubrikfält &nbsp; |Syfte |
|---|---|
|***4-bitars version*** |Det här fältet innehåller den ip-version som det här huvudet representerar. För IP-version 4, vilket är vad NetX Duo stöder, är värdet för det här fältet 4. |
|***4-bitars rubriklängd*** |Det här fältet anger antalet 32-bitars ord i IP-rubriken. Om det inte finns några alternativord är värdet för det här fältet 5. |
|***8-bitars tjänsttyp (TOS)*** |Det här fältet anger vilken typ av tjänst som begärdes för det här IP-paketet. Giltiga begäranden är följande:<br />– Normalt: 0x00 <br />– Minsta fördröjning: 0x00<br />– Maximalt antal data: 0x08<br />– Maximal tillförlitlighet: 0x04<br />– Minimikostnad: 0x02 |
|***16-bitars total längd*** |Det här fältet innehåller den totala längden på IP-datagrammet i byte, inklusive IP-huvudet. Ett IP-datagram är den grundläggande informationsenheten som finns på ett TCP/IP-Internet. Den innehåller ett mål och en källadress utöver data. Eftersom det är ett 16-bitarsfält är den maximala storleken för ett IP-datagram 65 535 byte.|
|***16-bitars identifiering*** |Fältet är ett tal som används för att unikt identifiera varje IP-datagram som skickas från en värd. Det här antalet ökas vanligtvis när ett IP-datagram har skickats. Det är särskilt användbart vid montering av mottagna IP-paketfragment.|
|***3-bitars flaggor*** |Det här fältet innehåller information om IP-fragmentering. Bit 14 är biten "fragmentera inte". Om den här biten anges fragmenteras inte det utgående IP-datagrammet. Bit 13 är biten "fler fragment". Om den här biten har angetts finns det fler fragment. Om den här biten är tydlig är detta det sista fragmentet av IP-paketet.|
|***13-bitars förskjutning av fragment*** |Det här fältet innehåller de övre 13 bitarna i fragmentförskjutningen. På grund av detta tillåts endast fragmentförskjutningar på 8 byte-gränser. Det första fragmentet av ett fragmenterat IP-datagram har bituppsättningen "fler fragment" och en förskjutning på 0.|
|***8-bitars TTL (Time to Live)*** |Det här fältet innehåller antalet routrar som det här datagrammet kan passera, vilket i princip begränsar livslängden för datagrammet.|
|***8-bitars protokoll***|Det här fältet anger vilket protokoll som använder IP-datagrammet. Följande är en lista över giltiga protokoll och deras värden:<br />– ICMP: 0x01 <br />– IGMP: 0x02<br />– TCP: 0X06<br />- UDP: 0X11 |
|***16-bitars kontrollsumma*** |Det här fältet innehåller den 16-bitars kontrollsumma som endast täcker IP-huvudet. Det finns ytterligare kontrollsumor i protokollen på högre nivå som täcker IP-nyttolasten. |
|***IP-adress för 32-bitars källa*** |Det här fältet innehåller avsändarens IP-adress och är alltid en värdadress. |
|***32-bitars mål-IP-adress*** |Det här fältet innehåller IP-adressen för mottagaren eller mottagarna om adressen är en sändnings- eller multicast-adress. |

### <a name="creating-ip-instances"></a>Skapa IP-instanser

IP-instanser skapas antingen under initieringen eller under körning av programtrådar. Den första IPv4-adressen, nätverksmasken, standardpaketpoolen, mediedrivrutinen och minnet och prioriteten för den interna IP-tråden definieras av ***nx_ip_create-tjänsten*** även om programmet endast har för avsikt att använda IPv6-nätverk. Om programmet initierar IP-instansen med sin IPv4-adress inställd på en ogiltig adress(0.0.0.0) antas det att gränssnittsadressen kommer att lösas med manuell konfiguration senare, via RARP eller via DHCP eller liknande protokoll.

För system med flera nätverksgränssnitt anges det primära gränssnittet när du anropar ***nx_ip_create** _. Varje ytterligare gränssnitt kan kopplas till samma IP-instans genom att anropa _*_nx_ip_interface_attach_**. Den här tjänsten lagrar information om nätverksgränssnittet (till exempel IP-adress, nätverksmask) i gränssnittskontrollblocket och associerar drivrutinsinstansen med gränssnittskontrollblocket i IP-instansen. När drivrutinen tar emot ett datapaket måste den lagra gränssnittsinformationen i NX_PACKET innan den vidarebefordras till IP-mottagningslogiken. Observera att en IP-instans redan måste skapas innan du kopplar några gränssnitt.

IPv6-tjänster startas inte efter anrop av ***nx_ip_create** _. Program som vill använda IPv6-tjänster måste anropa tjänsten _ *_nx_ipv6_enable_** för att starta IPv6.

I IPv6-nätverket kan varje gränssnitt i en IP-instans ha flera globala IPv6-adresser. Förutom att använda DHCPv6 för IPv6-adresstilldelning kan en enhet också använda tillståndslös automatisk adresskonfiguration. Mer information finns i avsnitten "IP Control Block" och "IPv6 Address Resolution" senare i det här kapitlet.

### <a name="ip-send"></a>IP-skicka

BEARBETNINGen av IP-meddelanden i NetX Duo är mycket smidigare. Förberedelsepekaren i paketet flyttas bakåt för att hantera IP-huvudet. IP-huvudet har slutförts (med alla alternativ som anges av det anropande protokolllagret), IP-kontrollsumman beräknas i rad (endast för IPv4-paket) och paketet skickas till den associerade nätverksdrivrutinen. Dessutom koordineras utgående fragmentering inifrån IP-bearbetningen.

För IPv4 initierar NetX Duo ARP-begäranden om fysisk mappning krävs för målets IP-adress. IPv6 använder Neighbor Discovery för mappning av IPv6-adress till fysisk adress.

> [!NOTE]
> *För IPv4-anslutning köas paket som kräver IP-adressmatchning (dvs. fysisk mappning) i ARP-kön tills antalet paket i kö överskrider ARP-ködjupet (definieras av symbolen **NX_ARP_MAX_QUEUE_DEPTH**). Om ködjupet nås tar NetX Duo bort det äldsta paketet i kön och fortsätter att vänta på adressmatchning för återstående paket i kö. Å andra sidan, om en ARP-post inte är löst, släpps de väntande paketen på ARP-posten när ARP-postens tidsgräns går ut.*

För system med flera nätverksgränssnitt väljer NetX Duo ett gränssnitt baserat på målets IP-adress. Följande procedur gäller för urvalsprocessen:

1. Om avsändaren anger ett utgående gränssnitt och gränssnittet är giltigt använder du det gränssnittet.
2. Om en måladress är IPv4 broadcast eller multicast används det första aktiverade fysiska gränssnittet.
3. Om måladressen hittas i den statiska routningstabellen används gränssnittet som är associerat med gatewayen.
4. Om målet är på länken används gränssnittet på länken.
5. Om måladressen är en länk-lokal adress (169.254.0.0/16) används det första giltiga gränssnittet.
6. Om standardgatewayen har konfigurerats använder du gränssnittet som är associerat med standardgatewayen för att överföra paketet.
7. Slutligen, om en av de giltiga IP-gränssnittsadresserna är länk-lokal adress (169.254.0.0/16), används det här gränssnittet som källadress för överföringen.
8. Utdatapaketet tas bort om allt ovan misslyckas.

### <a name="ip-receive"></a>IP-mottagning

IP-mottagningsbearbetningen anropas antingen från nätverksdrivrutinen eller den interna IP-tråden (för bearbetning av paket i den uppskjutna mottagna paketkön). IP-mottagningsbearbetningen undersöker protokollfältet och försöker skicka paketet till rätt protokollkomponent. Innan paketet faktiskt skickas tas IP-huvudet bort genom att presend-pekaren avancerar förbi IP-huvudet.

IP-mottagningsbearbetning identifierar också fragmenterade IP-paket och utför de nödvändiga stegen för att sätta ihop dem igen om fragmentering har aktiverats. Om fragmentering krävs men inte är aktiverat tas paketet bort.

NetX Duo fastställer lämpligt nätverksgränssnitt baserat på det gränssnitt som anges i paketet. Om paketgränssnittet är NULL använder NetX Duo som standard det primära gränssnittet. Detta görs för att garantera kompatibilitet med äldre NetX Duo Ethernet-drivrutiner.

### <a name="raw-ip-send"></a>RÅ IP-skicka

Ett rå IP-paket är en IP-ram som innehåller protokollnyttolast på övre nivå som inte direkt stöds (och bearbetas) av NetX Duo. Med ett råpaket kan utvecklare definiera sina egna IP-baserade program. Ett program kan skicka råa IP-paket direkt med hjälp av tjänsten ***nxd_ip_raw_packet_send** _ om rå BEARBETNING av IP-paket har aktiverats _*_med nx_ip_raw_packet_enabled tjänsten._*_ Vid överföring av ett unicast-paket i ett IPv6-nätverk avgör NetX Duo automatiskt vilken IPv6-källadress som ska användas för att skicka ut paketen baserat på måladressen. Om måladressen är en multicast-adress (eller broadcast för IPv4) får NetX Duo som standard det första (primära) gränssnittet. För att skicka ut sådana paket i sekundära gränssnitt måste programmet därför använda tjänsten _ *_nx_ip_raw_packet_source_send_** för att ange källadressen som ska användas för det utgående paketet.

### <a name="raw-ip-receive"></a>Rå IP-mottagning

Om råBEARBETNING av IP-paket är aktiverat kan programmet ta emot råa IP-paket via tjänsten ***nx_ip_raw_packet_receive** _ . Alla inkommande paket bearbetas enligt det protokoll som anges i IP-huvudet. Om protokollet anger UDP, TCP, IGMP eller ICMP bearbetar NetX Duo paketet med lämplig hanterare för paketprotokolltypen. Om protokollet inte är ett av dessa protokoll och rå IP-mottagning är aktiverat, förs det inkommande paketet till den råa paketkön som väntar på att programmet ska ta emot det via _*_tjänsten nx_ip_raw_packet_receive_** . Dessutom kan programtrådar pausas med en valfri tidsgräns i väntan på ett rå IP-paket. Antalet paket som kan köas i kön för råa paket är begränsat. Det högsta värdet definieras i ***NX_IP_RAW_MAX_QUEUE_DEPTH**_, vars standardvärde är 20. Ett program kan ändra det högsta värdet genom att anropa tjänsten _ *_nx_ip_raw_receive_queue_max_set_** .

Alternativt kan NetX Duo-biblioteket byggas med ***NX_ENABLE_IP_RAW_PACKET_FILTER*.** I det här läget tillhandahåller programmet en återanropsfunktion som anropas varje gång ett paket med en ohanterad protokolltyp tas emot. IP-mottagningslogiken vidarebefordrar paketet till den användardefinierade filterrutinen för att ta emot råpaket. Filterrutinen bestämmer om det råa paketet ska behållas för framtida processer eller inte. Returvärdet från motringningrutinen anger om paketet har bearbetats av det råa paketets mottagningsfilter. Om paketet bearbetas av återanropsfunktionen ska paketet släppas när programmet är klart med paketet. Annars ansvarar NetX Duo för att släppa paketet. Se informationen **_nx_ip_raw_packet_filter_set_** mer information om hur du använder filterfunktionen för rådatapaket.

> [!NOTE]
> *BSD-wrapper-funktionen för NetX Duo använder filterfunktionen raw-paket för att hantera BSD-råsocketar. För att stödja raw socket i BSD-omslutaren måste NetX Duo-biblioteket därför byggas med ***NX_ENABLE_IP_RAW_PACKET_FILTER** _ definierat och programmet bör inte använda _*_nx_ip_raw_packet_filter_set_*_ för att installera ett eget filter för rådata functions._

### <a name="default-packet-pool"></a>Standardpaketpool

Varje IP-instans får en standardpaketpool när den skapas. Den här paketpoolen används för att allokera paket för ARP, RARP, ICMP, IGMP, olika TCP-kontrollpaket (SYN, ACK och så vidare), neighbor discovery, routeridentifiering och dubblettadressidentifiering. Om standardpaketpoolen är tom när NetX Duo behöver allokera ett paket kan NetX Duo behöva avbryta den specifika åtgärden och returnerar ett felmeddelande om det är möjligt.

### <a name="ip-helper-thread"></a>IP-hjälptråd

Varje IP-instans har en hjälptråd. Den här tråden ansvarar för att hantera all uppskjuten paketbearbetning och all regelbunden bearbetning. IP-hjälptråden skapas i ***nx_ip_create.*** Det är här tråden får sin stack och prioritet. Observera att den första bearbetningen i IP-hjälptråden är att slutföra initieringen av nätverksdrivrutinen som är associerad med IP-tjänsten för att skapa. När initieringen av nätverksdrivrutiner är klar startar hjälptråden en oändlig loop för att bearbeta paket och periodiska begäranden.

> [!IMPORTANT]
> *Om ett oförklarligt beteende visas i IP-hjälptråden är det första felsökningssteget att öka stackstorleken under IP-tjänsten för att skapa. Om stacken är för liten kan IP-hjälptråden eventuellt skriva över minne, vilket kan orsaka ovanliga problem.*

### <a name="thread-suspension"></a>Trådavstängning

Programtrådar kan pausa vid försök att ta emot råa IP-paket. När ett råpaket tas emot ges det nya paketet till den första tråden som pausas och tråden återupptas. NetX Duo-tjänster för att ta emot paket har en valfri tidsgräns för låsning. När ett paket tas emot eller tidsgränsen går ut återupptas programtråden med lämplig slutförandestatus.

### <a name="ip-statistics-and-errors"></a>IP-statistik och -fel

Om den är aktiverad håller NetX Duo reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP-instans:

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

Alla dessa statistik- och felrapporter är tillgängliga för programmet med nx_ip_info_get tjänsten.

### <a name="ip-control-block-nx_ip"></a>IP-kontrollblock NX_IP

Egenskaperna för varje IP-instans finns i dess kontrollblock. Den innehåller användbar information som IP-adresser och nätverksmasker för varje nätverksenhet och en tabell med grann-IP och adressmappning för fysisk maskinvara. Den här strukturen definieras i ***nx_api.h _file.** Om IPv6 är aktiverat innehåller den även en matris med IPv6-adress, som anges av det användarkonfigurerbara alternativet _*_NX_MAX_IPV6_ADDRESSES_**. Med standardvärdet kan varje fysiskt nätverksgränssnitt ha tre IPv6-adresser.

Kontrollblock för IP-instanser kan finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion.

### <a name="static-ipv4-routing"></a>Statisk IPv4-routning

Med funktionen för statisk routning kan ett program ange ett IPv4-nätverk och en nästa hoppadress för specifika IP-adresser utanför nätverkets mål. Om statisk routning är aktiverat söker NetX Duo igenom den statiska routningstabellen efter en post som matchar måladressen för paketet som ska skickas. Om ingen matchning hittas söker NetX Duo igenom listan över fysiska gränssnitt och väljer en käll-IP-adress och nästa hopp-adress baserat på mål-IP-adressen och nätverksmasken. Om målet inte matchar någon av IP-adresserna för nätverksdrivrutinerna som är anslutna till IP-instansen väljer NetX Duo ett gränssnitt som är direkt anslutet till standardgatewayen och använder IP-adressen för gränssnittet som källadress och standardgatewayen som nästa hopp.

Poster kan läggas till och tas bort från den statiska routningstabellen med hjälp av tjänsterna ***nx_ip_static_route_add** _ och _ *_nx_ip_static_route_delete_** . Om du vill använda statisk routning måste värdprogrammet aktivera den här funktionen genom att ***definiera NX_ENABLE_IP_STATIC_ROUTING.***

> [!NOTE]
> *När du lägger till en post i den statiska routningstabellen söker NetX Duo efter en matchande post för den angivna måladressen som redan finns i tabellen. Om det finns en sådan prioriteras posten med det mindre nätverket (längre prefix) i nätverksmasken.*

### <a name="ipv4-forwarding"></a>IPv4-vidarebefordran

Om det inkommande IPv4-paketet inte är avsett för den här noden och funktionen för IPv4-vidarebefordran är aktiverad, försöker NetX Duo vidarebefordra paketet via de andra gränssnitten.  

### <a name="ip-fragmentation"></a>IP-fragmentering

Nätverksenheten kan ha begränsningar för storleken på utgående paket. Den här gränsen kallas maximal överföringsenhet (MTU). IP MTU är den största IP-ramstorleken som en länklagerdrivrutin kan överföra utan att fragmentera IP-paketet. Under initieringsfasen för enhetsdrivrutiner måste drivrutinsmodulen konfigurera sin IP MTU-storlek via ***nx_ip_interface_mtu_set.***

Även om det inte rekommenderas kan programmet generera datagram som är större än den underliggande IP MTU som stöds av enheten. Innan sådana IP-datagram överförs måste IP-lagret fragmentera dessa paket. När fragmenterade IP-bildrutor tas emot måste den mottagande änden lagra alla fragmenterade IP-bildrutor med samma fragmenterings-ID och sätta ihop dem i ordning. Om IP-mottagningslogiken inte kan samla in alla fragment för att återställa den ursprungliga IP-ramen i tid släpps alla fragment. Det är upp till det övre lagrets protokoll att identifiera sådana paketförluster och återställa från det.

IP-fragmentering gäller för både IPv4- och IPv6-paket.

Systemdesignern måste aktivera funktionen IP-fragmentering i NetX Duo med hjälp av ***tjänsten nx_ip_fragment_enable*** för att stödja IP-fragmentering och sätta ihop dem igen. Om den här funktionen inte är aktiverad ignoreras inkommande fragmenterade IP-paket, samt paket som överskrider nätverksdrivrutinens MTU.

> [!NOTE]
> *Logiken för IP-fragmentering kan tas bort helt genom att definiera ***NX_DISABLE_FRAGMENTATION** _ när du skapar NetX Duo-biblioteket. På så sätt kan du minska kodstorleken för NetX Duo. Observera att funktionerna för både IPv4- och IPv6-fragmentering/återmontering i den här situationen disabled._

> [!NOTE]
> *Om **NX_DISABLE_CHAINED_PACKET** definieras måste IP-fragmentering inaktiveras.*

> [!NOTE]
> *I ett IPv6-nätverk fragmenteras inte ett datagram om storleken på datagrammet överskrider den minsta MTU-storleken. Det är därför upp till den skickande enheten att fastställa den minsta MTU:en mellan källan och målet, och för att säkerställa att IP-datagramstorleken inte överskrider sökvägen MTU. I NetX Duo kan du aktivera IPv6 PATH MTU-identifiering genom att skapa NetX Duo-bibliotek med symbolen **NX_ENABLE_IPV6_PATH_MTU_DISCOVERY** definierad.*

## <a name="address-resolution-protocol-arp-in-ipv4"></a>Address Resolution Protocol (ARP) i IPv4

Address Resolution Protocol (ARP) ansvarar för dynamisk mappning av 32-bitars IPv4-adresser till de underliggande fysiska medierna (RFC 826). Ethernet är det mest typiska fysiska mediet och har stöd för 48-bitarsadresser. Behovet av ARP bestäms av den nätverksdrivrutin som tillhandahålls till tjänsten ***nx_ip_create** _ . Om fysisk mappning krävs måste nätverksdrivrutinen använda tjänsten _ *_nx_interface_address_mapping_needed_** för att konfigurera drivrutinsgränssnittet korrekt.

### <a name="arp-enable"></a>Aktivera ARP

För att ARP ska fungera korrekt måste det  först aktiveras av programmet med nx_arp_enable tjänsten. Den här tjänsten uppsättningar olika datastrukturer för ARP-bearbetning, inklusive skapandet av ett ARP-cacheområde från det minne som anges till ARP-aktivera tjänsten.

### <a name="arp-cache"></a>ARP Cache

ARP-cachen kan ses som en matris med interna ARP-mappningsdatastrukturer. Varje intern struktur kan upprätthålla relationen mellan en IP-adress och en fysisk maskinvaruadress. Dessutom har varje datastruktur länkpekare så att den kan ingå i flera länkade listor.

Programmet kan söka efter en IP-adress från ARP-cachen genom att ange mac-maskinvaruadress med hjälp av tjänsten ***nx_arp_ip_address_find** _ om mappningen finns i ARP-tabellen. På samma sätt returnerar tjänsten _ *_nx_arp_hardware_address_find_** MAC-adressen för en viss IP-adress.

### <a name="arp-dynamic-entries"></a>Dynamiska ARP-poster

Som standard placerar ARP-aktivera tjänsten alla poster i ARP-cachen i listan över tillgängliga dynamiska ARP-poster. En dynamisk ARP-post allokeras från den här listan av NetX Duo när en skicka-begäran till en omappad IP-adress identifieras. Efter allokeringen konfigureras ARP-posten och en ARP-begäran skickas till det fysiska mediet.

En dynamisk post kan också skapas av tjänsten ***nx_arp_dynamic_entry_set***.

> [!IMPORTANT]
> *Om alla dynamiska ARP-poster används ersätts den minst senast använda ARP-posten med en ny mappning.*

### <a name="arp-static-entries"></a>Statiska ARP-poster

Programmet kan också konfigurera statisk ARP-mappning med hjälp av ***nx_arp_static_entry_create** _service. Den här tjänsten allokerar en ARP-post från den dynamiska ARP-postlistan och placerar den på den statiska listan med mappningsinformationen som tillhandahålls av programmet. Statiska ARP-poster kan inte återanvändas eller bli äldre. Programmet kan ta bort en statisk post med hjälp av tjänsten _*_nx_arp_static_entry_delete_*_. Om du vill ta bort alla statiska poster i ARP-tabellen kan programmet använda tjänsten _*_nx_arp_static_entries_delete_**.

### <a name="automatic-arp-entry"></a>Automatisk ARP-post

NetX Duo registrerar peer-peerns IP/MAC-mappning efter peer-svaren på ARP-begäran. NetX Duo implementerar även funktionen för automatisk ARP-post där den registrerar peer-IP/MAC-adressmappning baserat på oönskade ARP-begäranden från nätverket. Med den här funktionen kan ARP-tabellen fyllas med peer-information, vilket minskar den fördröjning som krävs för att gå igenom ARP-begäran/-svarscykeln. Nackdelen med att aktivera automatisk ARP är dock att ARP-tabellen tenderar att fyllas upp snabbt i ett upptaget nätverk med många noder på den lokala länken, vilket så småningom skulle leda till att ARP-posten ersätts.

Den här funktionen är aktiverad som standard. Om du vill inaktivera det måste NetX Duo-biblioteket kompileras med symbolen ***NX_DISABLE_ARP_AUTO_ENTRY*** definieras.</p>

### <a name="arp-messages"></a>ARP-meddelanden

Som tidigare nämnts skickas ett meddelande om ARP-begäran när IP-uppgiften identifierar att mappning krävs för en IP-adress. ARP-begäranden skickas regelbundet (varje ***NX_ARP_UPDATE_RATE** _ sekunder) tills ett motsvarande ARP-svar tas emot. Totalt görs _ *_NX_ARP_MAXIMUM_RETRIES_** ARP-begäranden innan ARP-försöket avbryts. När ett ARP-svar tas emot lagras den associerade fysiska adressinformationen i den ARP-post som finns i cacheminnet.

För system med flera startdatorer avgör NetX Duo vilket gränssnitt som ARP-begäranden och svar ska skickas till baserat på den angivna måladressen.

> [!NOTE]
> *Utgående IP-paket köas medan NetX Duo väntar på ARP-svaret. Antalet utgående IP-paket i kö definieras av konstanten **NX_ARP_MAX_QUEUE_DEPTH**.*

NetX Duo svarar också på ARP-begäranden från andra noder i det lokala IPv4-nätverket. När en extern ARP-begäran görs som matchar den aktuella IP-adressen för gränssnittet som tar emot ARP-begäran, skapar NetX Duo ett ARP-svarsmeddelande som innehåller den aktuella fysiska adressen.

Formaten för Ethernet ARP-begäranden och svar visas i bild 6 och beskrivs nedan.

| **Fält för &nbsp; begäran/svar**         | **Syfte**            |
| ---------------------------------- | ---------------------- |
| ***Ethernet-måladress*** | Det här 6 byte-fältet innehåller måladressen för ARP-svaret och är en sändning (alla sådana) för ARP-begäranden. Det här fältet konfigureras av nätverksdrivrutinen. 
| ***Ethernet-källadress***      | Det här 6 byte-fältet innehåller adressen till avsändaren av ARP-begäran eller -svaret och konfigureras av nätverksdrivrutinen. |
| ***Ramtyp*** | Det här fältet med 2 byte innehåller den typ av Ethernet-ram som finns, och för ARP-begäranden och -svar är detta lika med 0x0806. Det här är det sista fältet som nätverksdrivrutinen ansvarar för att konfigurera. |
| ***Maskinvarutyp*** | Det här fältet med 2 byte innehåller maskinvarutypen, som är 0x0001 för Ethernet. |
| ***Protokolltyp*** | Det här fältet med 2 byte innehåller protokolltypen, som 0x0800 IP-adresser. |
| ***Maskinvarustorlek*** | Det här fältet med 1 byte innehåller maskinvarans adressstorlek, som är 6 för Ethernet-adresser. |

![Diagram över ARP-paketformatet.](./media/user-guide/arp-packet-format.png)

**BILD 6. ARP-paketformat**

| Fältet &nbsp; Begäran/svar | Syfte |
|---|---|
| ***Protokollstorlek*** | Det här fältet med 1 byte innehåller IP-adressstorleken, som är 4 för IP-adresser. |
| ***Åtgärdskod*** | Det här fältet med 2 byte innehåller åtgärden för det här ARP-paketet. En ARP-begäran anges med värdet 0x0001, medan ett ARP-svar representeras av värdet 0x0002. |
| ***Ethernet-adress för avsändare*** | Det här 6 byte-fältet innehåller avsändarens Ethernet-adress. |
| ***Avsändarens IP-adress*** | Det här fältet med 4 byte innehåller avsändarens IP-adress. |
| ***Ethernet-måladress*** | Det här 6 byte-fältet innehåller målets Ethernet-adress. |
| ***Mål-IP-adress*** | Det här 4 byte-fältet innehåller målets IP-adress. |

> [!NOTE]
> *ARP-begäranden och svar är paket på Ethernet-nivå. Alla andra TCP/IP-paket kapslas in av ett IP-pakethuvud.*

> [!NOTE]
> *Alla ARP-meddelanden i TCP/IP-implementeringen förväntas vara **i big endian** format. I det här formatet finns den viktigaste byten av ordet på den lägsta byte-adressen.*

### <a name="arp-aging"></a>ARP-åldersfördelning

NetX stöder automatisk ogiltighet av dynamiska ARP-inmatningar. ***NX_ARP_EXPIRATION_RATE** _ anger hur många sekunder som en etablerad IP-adress till fysisk mappning ska vara giltig. Efter förfallodatum tas ARP-posten bort från ARP-cachen. Nästa försök att skicka till motsvarande IP-adress resulterar i en ny ARP-begäran. Inställning _ *_NX_ARP_EXPIRATION_RATE_** till noll inaktiverar ARP-ålder, vilket är standardkonfigurationen.

### <a name="arp-defend"></a>ARP-försvar

När en ARP-begäran eller ett ARP-svarspaket tas emot och avsändaren har samma IP-adress, vilket är i konflikt med IP-adressen för den här noden, skickar NetX Duo en ARP-begäran för den adressen som ett skydd. Om ARP-konfliktpaketet tas emot mer än en gång på 10 sekunder skickar NetX Duo inte fler skyddspaket. Standardintervallet 10 sekunder kan omdefinieras med ***NX_ARP_DEFEND_INTERVAL** _. Det här beteendet följer den princip som anges i 2.4 (c) i RFC5227. Eftersom Windows XP ignorerar ARP-meddelandet som ett svar på ARP-avsökningen kan användaren definiera _ *_NX_ARP_DEFEND_BY_REPLY_** för att skicka ARP-svar som ytterligare stöd.

### <a name="arp-statistics-and-errors"></a>ARP-statistik och fel

Om den är aktiverad håller NetX Duo ARP-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP-adress ARP-bearbetning:

- Totalt antal skickade ARP-begäranden
- Totalt antal mottagna ARP-begäranden
- Totalt antal skickade ARP-svar 
- Totalt antal mottagna ARP-svar 
- Totalt antal dynamiska ARP-poster 
- Totalt antal statiska ARP-poster 
- Totalt antal inspelade poster i ARP 
- Totalt antal ogiltiga ARP-meddelanden 

All statistik och alla felrapporter är  tillgängliga för programmet med nx_arp_info_get tjänsten.

## <a name="reverse-address-resolution-protocol-rarp-in-ipv4"></a>REVERSE Address Resolution Protocol (RARP) i IPv4

Reverse Address Resolution Protocol (RARP) är protokollet för att begära nätverkstilldelning av värdens 32-bitars IP-adresser (RFC 903). Detta görs via en RARP-begäran och fortsätter regelbundet tills en nätverksmedlem tilldelar en IP-adress till värdnätverksgränssnittet i ett RARP-svar. Programmet skapar en IP-instans av ***tjänstinstansen nx_ip_create*** utan IP-adress. Om RARP har aktiverats av programmet kan det använda RARP-protokollet för att begära en IP-adress från nätverksservern som är tillgänglig via gränssnittet som har en IP-adress på noll.

### <a name="rarp-enable"></a>AKTIVERA RARP

Om du vill använda RARP måste programmet skapa IP-instansen med IP-adressen noll och sedan aktivera RARP med hjälp av ***nx_rarp_enable***. För multihome-system måste minst en nätverksenhet som är associerad med IP-instansen ha EN IP-adress på noll. RARP-bearbetningen skickar regelbundet RARP-begärandemeddelanden för NetX Duo-systemet som kräver en IP-adress tills ett giltigt RARP-svar med nätverkets avsedda IP-adress tas emot. Nu är RARP-bearbetningen klar.

När RARP har aktiverats inaktiveras det automatiskt när alla gränssnittsadresser har lösts. Programmet kan tvinga RARP att avsluta med hjälp av tjänsten ***nx_rarp_disable***.

### <a name="rarp-request"></a>RARP-begäran

Formatet för ett RARP-begärandepaket är nästan identiskt med ARP-paketet som visas [i bild 6](#arp-messages). Den enda skillnaden är att ramtypens fält  0x8035 åtgärdskoden är 3, vilket anger en RARP-begäran. Som tidigare nämnts skickas RARP-begäranden regelbundet (var ***NX_RARP_UPDATE_RATE*** sekunder) tills ett RARP-svar med den nätverks tilldelade IP-adressen tas emot.

> [!NOTE]
> *Alla RARP-meddelanden i TCP/IP-implementeringen förväntas vara **i big endian** format. I det här formatet finns den viktigaste byten av ordet på den lägsta byte-adressen.*

### <a name="rarp-reply"></a>RARP-svar

RARP-svarsmeddelanden tas emot från nätverket och innehåller den nätverks tilldelade IP-adressen för den här värden. Formatet för ett RARP-svarspaket är nästan identiskt med ARP-paketet som visas i bild 6. Den enda skillnaden är att ramtypens fält 0x8035 operation *code-fältet* är 4, vilket anger ett RARP-svar. När IP-adressen har tagits emot konfigureras den i IP-instansen, den periodiska RARP-begäran inaktiveras och IP-instansen är nu redo för normal nätverksdrift.

För multihome-värdar tillämpas IP-adressen på det begärande nätverksgränssnittet. Om det finns andra nätverksgränssnitt som fortfarande begär en IP-adresstilldelning fortsätter den periodiska RARP-tjänsten tills alla GRÄNSSNITTs-IP-adressbegäranden har lösts.

> [!NOTE]
> *Programmet bör inte använda IP-instansen förrän RARP-bearbetningen har slutförts. Den **nx_ip_status_check** kan användas av program för att vänta tills RARP har slutförts. För multihome-system bör programmet inte använda det begärande gränssnittet förrän RARP-bearbetningen har slutförts på det gränssnittet. Status för IP-adressen på den sekundära  enheten kan kontrolleras med nx_ip_interface_status_check tjänsten.*

### <a name="rarp-statistics-and-errors"></a>RARP-statistik och -fel

Om den är aktiverad håller NetX Duo RARP-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP-adress RARP-bearbetning:

- Totalt antal SKICKADE RARP-begäranden
- Totalt antal mottagna RARP-svar
- Totalt antal ogiltiga RARP-meddelanden

All statistik och alla felrapporter är  tillgängliga för programmet med nx_rarp_info_get tjänsten.

## <a name="internet-control-message-protocol-icmp"></a>Internet Control Message Protocol (ICMP)

Internet Control Message Protocol för IPv4 (ICMP) är begränsad till att skicka fel- och kontrollinformation mellan IP-nätverksmedlemmar. Internet Control Message Protocol för IPv6 (ICMPv6) hanterar även fel- och kontrollinformation och krävs för adressmatchningsprotokoll som DUPLICATE Address Detection (PV) och automatisk konfiguration av tillståndslösa adresser.

Precis som de flesta andra programlagermeddelanden (t.ex. TCP/IP) kapslas ICMP- och ICMPv6-meddelanden in av ett IP-huvud med protokollbeteckningen ICMP (eller ICMPv6).

### <a name="icmp-statistics-and-errors"></a>ICMP-statistik och -fel

Om den är aktiverad håller NetX Duo reda på flera ICMP-statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP-adresss ICMP-bearbetning: 

- Totalt antal skickade ICMP-pingar  
- Totalt antal timeouter för ICMP-ping 
- Totalt antal pausade ICMP-pingtrådar 
- Totalt antal mottagna ICMP-pingsvar 
- Totalt antal fel i ICMP-kontrollsumma 
- Totalt antal ohanterade ICMP-meddelanden 

All statistik och alla felrapporter är  tillgängliga för programmet med nx_icmp_info_get tjänsten.

## <a name="icmpv4-services-in-netx-duo"></a>ICMPv4-tjänster i NetX Duo

### <a name="icmpv4-enable"></a>Aktivera ICMPv4

Innan ICMPv4-meddelanden kan bearbetas av NetX Duo måste programmet anropa ***nx_icmp_enable-tjänsten*** för att aktivera ICMPv4-bearbetning. När det är klart kan programmet utfärda pingbegäranden och fält för inkommande ping-paket.  

### <a name="icmpv4-echo-request"></a>ICMPv4 Echo-begäran

En ekobegäran är en typ av ICMPv4-meddelande som vanligtvis används för att kontrollera om det finns en specifik nod i nätverket, som identifieras av dess värd-IP-adress. Det populära ping-kommandot implementeras med hjälp av ICMP-ekobegäran/ekosvarsmeddelanden. Om den specifika värden finns bearbetar dess nätverksstack pingbegäran och svar med ett pingsvar. Bild 7 innehåller information om ICMPv4-pingmeddelandeformatet.

![ICMPv4-pingmeddelande](./media/user-guide/icmpv4-ping-message.png)  

**BILD 7. ICMPv4-pingmeddelande**

> [!NOTE]
> *Alla ICMPv4-meddelanden i TCP/IP-implementeringen förväntas vara **i big endian** format. I det här formatet finns den viktigaste byten av ordet på den lägsta byte-adressen.*

Följande beskriver ICMPv4-huvudformatet:

|Rubrikfält |Syfte |
|---|---|
|**Typ** |Det här fältet anger ICMPv4-meddelandet (bitar 31–24). De vanligaste är:<br />- 0: Ekosvar<br />– 3: Det går inte att nå målet<br />- 8: Ekobegäran<br />- 11: Överskriden tid<br />– 12: Parameterproblem |
|**Kod** |Det här fältet är kontextspecifikt för typfältet (bitar 23–16). För en ekobegäran eller svar är koden inställd på noll.|
|**Kontrollsumma** |Det här fältet innehåller 16-bitars kontrollsumman för komplementssumman för ICMPv4-meddelandet, inklusive hela ICMPv4-rubriken som börjar med fältet Typ. Innan kontrollsumman genereras rensas fältet kontrollsumma.|
|**Identification** | Det här fältet innehåller ett ID-värde som identifierar värden. en värd ska använda DET ID som extraherats från en ECHO-begäran i ECHO REPLY (bitar 31-16).|
|**Sekvensnummer** |Det här fältet innehåller ett ID-värde. en värd ska använda DET ID som extraherats från en ECHO-begäran i ECHO REPLY (bitar 31-16). Till skillnad från identifierarfältet ändras det här värdet i en efterföljande Echo-begäran från samma värd (bitar 15-0).|

### <a name="icmpv4-echo-response"></a>Svar från ICMPv4-eko    
Ett pingsvar är en annan typ av ICMP-meddelande som genereras internt av ICMP-komponenten som svar på en extern ping-begäran. Förutom bekräftelse innehåller ping-svaret även en kopia av användardata som anges i ping-begäran.

### <a name="icmpv4-error-messages"></a>Felmeddelanden för ICMPv4   
Följande ICMPv4-felmeddelanden stöds i NetX Duo: 
- Det går inte att nå målet 
- Överskriden tid 
- Parameterproblem

## <a name="internet-group-management-protocol-igmp"></a>Internet Grupphanteringsprotokoll (IGMP)

I Internet Group Management Protocol (IGMP) tillhandahåller en enhet för att kommunicera med sina grannar och dess routrar som den har för avsikt att ta emot eller ansluta till en IPv4-multicast-grupp (RFC 1112 och RFC 2236). En multicast-grupp är i princip en dynamisk samling nätverksmedlemmar och representeras av en IP-adress för klass D. Medlemmar i multicast-gruppen kan lämna när som helst och nya medlemmar kan gå med när som helst. Den samordning som ingår i att ansluta till och lämna gruppen är IGMP:s ansvar.

> [!NOTE]
> *IGMP är endast utformat för IPv4-multicast-grupper. Det kan inte användas i IPv6-nätverket.*

### <a name="igmp-enable"></a>Aktivera IGMP     
Innan någon multicasting-aktivitet kan ske i NetX Duo måste programmet anropa ***nx_igmp_enable tjänsten.*** Den här tjänsten utför grundläggande IGMP-initiering som förberedelse för multicast-begäranden.

### <a name="multicast-ipv4-addressing"></a>Multicast IPv4-adressering  
Som tidigare nämnts är multicast-adresser faktiskt IP-adresser av klass D som visas [i bild 4](#ipv4-addresses). De lägre 28 bitarna i klass D-adressen motsvarar multicast-grupp-ID:t. Det finns en serie fördefinierade multicast-adresser. Men alla *värdars adress* (244.0.0.1) är särskilt viktig för IGMP-bearbetning. Alla *värdadresser* används av routrar för att fråga alla multicast-medlemmar för att rapportera om vilka multicast-grupper de tillhör.  

### <a name="physical-address-mapping-in-ipv4"></a>Fysisk adressmappning i IPv4
Multicast-adresser för klass D mappas direkt till fysiska Ethernet-adresser från 01.00.5e.00.00.00 till 01.00.5e.7f.ff.ff. De lägre 23 bitarna av IP-multicast-adressmappningen direkt till de lägre 23 bitarna av Ethernet-adressen.

### <a name="multicast-group-join"></a>Multicast-gruppkoppling
Program som behöver ansluta till en viss multicast-grupp kan göra det genom att anropa ***nx_igmp_multicast_join tjänsten.*** Den här tjänsten håller reda på antalet begäranden om att ansluta till den här multicast-gruppen. Om det här är den första programbegäran om att ansluta till multicast-gruppen skickas en IGMP-rapport i det primära nätverket som anger den här värdens avsikt att ansluta till gruppen. Därefter anropas nätverksdrivrutinen för att konfigurera för att lyssna efter paket med Ethernet-adressen för den här multicast-gruppen.

Om multicast-gruppen är tillgänglig via ett specifikt gränssnitt i ett multihome-system, ska programmet använda tjänsten ***nx_igmp_multicast_interface_join** _ i stället för _*_nx_igmp_multicast_join_**, som är begränsad till multicast-grupper i det primära nätverket.

### <a name="multicast-group-leave"></a>Lämna multicast-grupp   
Program som behöver lämna en tidigare ansluten multicast-grupp kan göra det genom att anropa ***nx_igmp_multicast_leave tjänsten.*** Den här tjänsten minskar det interna antalet som är associerat med hur många gånger gruppen har anslutits. Om det inte finns några utestående kopplingsbegäranden för en grupp anropas nätverksdrivrutinen för att inaktivera lyssna efter paket med den här multicast-gruppens Ethernet-adress.

### <a name="multicast-loopback"></a>Multicast Loopback    
Ett program kan vilja ta emot multicast-trafik från en av källorna på samma nod. Detta kräver att IP-multicast-komponenten har loopback aktiverat med hjälp av ***nx_igmp_loopback_enable***.

### <a name="igmp-report-message"></a>IGMP-rapportmeddelande      
När programmet ansluts till en multicast-grupp skickas ett IGMP-rapportmeddelande via nätverket för att ange värdens avsikt att ansluta till en viss multicast-grupp. Formatet för IGMP-rapportmeddelandet visas i bild 8. Multicast-gruppadressen används för både gruppmeddelandet i IGMP-rapportmeddelandet och mål-IP-adressen.

I bilden ovan (bild 8) innehåller IGMP-huvudet ett fält för version/typ, maximalt svar

![Diagram över ett IGMP-rapportmeddelande.](./media/user-guide/image17.jpg)

**BILD 8. IGMP-rapportmeddelande**

tid, ett fält för kontrollsumma och ett multicast-gruppadressfält. För IGMPv1-meddelanden anges fältet Maximal svarstid alltid till noll, eftersom detta inte är en del av IGMPv1-protokollet. Fältet Maximal svarstid anges när värden tar emot ett IGMP-meddelande av frågetyp och rensas när en värd tar emot en annan värds rapporttypsmeddelande enligt definitionen i IGMPv2-protokollet.

Följande beskriver IGMP-rubrikformatet:

|Rubrikfält|Syfte|
|---|---|
|**Version** |Det här fältet anger IGMP-versionen (bitar 31–28).|
|**Typ** |Det här fältet anger typen av IGMP-meddelande (bitar 27-24).|
|**Maximal svarstid** |Används inte i IGMP v1. I IGMP v2 fungerar det här fältet som maximal svarstid.|
|**Kontrollsumma** |Det här fältet innehåller 16-bitars kontrollsumman för komplementssumman för IGMP-meddelandet som börjar med IGMP-versionen (bitar 0–15)|
|**Gruppadress** |IP-adress för 32-bitars D-grupp|

IGMP-rapportmeddelanden skickas också som svar på IGMP-frågemeddelanden som skickas av en multicast-router. Multicast-routrar skickar regelbundet frågemeddelanden ut för att se vilka värdar som fortfarande kräver gruppmedlemskap. Frågemeddelanden har samma format som IGMP-rapportmeddelandet som visas i bild 8. De enda skillnaderna är att IGMP-typen är lika med 1 och gruppadressfältet är inställt på 0. IGMP-frågemeddelanden skickas till alla *värdars* IP-adress av multicast-routern. En värd som fortfarande vill behålla gruppmedlemskapet svarar genom att skicka ett annat IGMP-rapportmeddelande.

> [!NOTE]
> *Alla meddelanden i TCP/IP-implementeringen förväntas vara i **big endian** format. I det här formatet finns den viktigaste byten av ordet på den lägsta byteadressen.*

### <a name="igmp-statistics-and-errors"></a>IGMP-statistik och -fel    
<th><p>Om funktionen är aktiverad håller NetX Duo IGMP-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP-adresss IGMP-bearbetning: 

- Totalt antal skickade IGMP-rapporter 
- Totalt antal mottagna IGMP-frågor 
- Totalt antal IGMP-kontrollsummor 
- Totalt antal IGMP-aktuella grupper som anslutits 

Alla dessa statistik- och felrapporter är tillgängliga för programmet med nx_igmp_info_get tjänsten. 

### <a name="multicast-without-igmp"></a>Multicast utan IGMP  
Program som förväntar sig IPv4-multicast-trafik kan ansluta till en multicast-gruppadress utan att aktivera IGMP-meddelanden med hjälp av ***tjänsten nx_ipv4_multicast_interface_join***. Den här tjänsten instruerar IPv4-lagret och den underliggande gränssnittsdrivrutinen att acceptera paket från den avsedda IPv4-multicast-adressen. Det finns dock inga IGMP-grupphanteringsmeddelanden som skickas eller bearbetas för den här gruppen.

Programmet vill inte längre ta emot trafik från gruppen kan använda tjänsten ***nx_ipv4_multicast_interface_leave.***

## <a name="ipv6-in-netx-duo"></a>IPv6 i NetX Duo

### <a name="ipv6-addresses"></a>IPv6-adresser   
IPv6-adresser är 128 bitar. Arkitekturen för IPv6-adressen beskrivs i RFC 4291. Adressen är indelad i ett prefix som innehåller de viktigaste bitarna och en värdadress som innehåller de lägre bitarna. Prefixet anger adresstypen och motsvarar ungefär nätverksadressen i IPv4-nätverket.

IPv6 har tre typer av adressspecifikationer: unicast, anycast (stöds inte i NetX Duo) och multicast. Unicast-adresser är de IP-adresser som identifierar en specifik värd på Internet. Unicast-adresser kan vara antingen en källa eller en mål-IP-adress. Multicast-adresser anger en dynamisk grupp med värdar på Internet. Medlemmar i multicast-gruppen kan gå med och lämna när de vill.

IPv6 har inte motsvarigheten till IPv4-sändningsmekanismen. Du kan skicka ett paket till alla värdar genom att skicka ett paket till den länk-lokala multicast-gruppen för alla värdar.

IPv6 använder multicast-adresser för att utföra procedurer för grannidentifiering, routeridentifiering och automatisk konfiguration av tillståndslös adress.

Det finns två typer av IPv6-unicast-adresser: länka lokala adresser, som vanligtvis skapas genom att kombinera det välkända lokala länkprefixet med gränssnittets MAC-adress och globala IP-adresser, som också har prefixdelen och värd-ID-delen. En global adress kan konfigureras manuellt eller via den tillståndslösa automatisk adresskonfigurationen eller DHCPv6. NetX Duo stöder både länk lokal adress och global adress.

För att hantera både IPv4- och IPv6-format tillhandahåller NetX Duo en ny datatyp, NXD_ADDRESS, för att lagra IPv4- och IPv6-adresser. Definitionen av den här strukturen visas nedan. Adressfältet är en union av IPv4- och IPv6-adresser.

```c
typedef struct NXD_ADDRESS_STRUCT
{
    ULONG nxd_ip_version;
    union
    {
        ULONG v4;
        ULONG v6[4];
    } nxd_ip_address;
} NXD_ADDRESS;
```

I NXD_ADDRESS anger det första elementet, *nxd_ip_version*, IPv4- eller IPv6-version. Värden som stöds är antingen NX_IP_VERSION_V4 eller NX_IP_VERSION_V6. *nxd_ip_version* anger vilket fält i *nxd_ip_address* som ska användas som IP-adress. NetX Duo API-tjänster tar vanligtvis en pekare till NXD_ADDRESS struktur som indataargument i stället för IP-adressen för ULONG (32-bitars).

### <a name="link-local-addresses"></a>Länka lokala adresser     
En länk-lokal adress är endast giltig i det lokala nätverket. En enhet kan skicka och ta emot paket till en annan enhet i samma nätverk när en giltig lokal länk har tilldelats till den. Ett program tilldelar en länk-lokal adress genom att anropa NetX Duo-nxd_ipv6_address_set , med prefixlängdsparametern inställd på 10. Programmet kan ange en länk-lokal adress till tjänsten, eller så kan det helt enkelt använda NX_NULL som den länk-lokala adressen och låta NetX Duo skapa en länk-lokal adress baserat på enhetens MAC-adress.

I följande exempel instrueras NetX Duo att konfigurera den länk-lokala adressen med prefixlängden 10 på den primära enheten (index 0) med hjälp av dess MAC-adress:

```c
nxd_ipv6_address_set(ip_ptr, 0, NX_NULL, 10, NX_NULL);
```
Om MAC-adressen för gränssnittet i exemplet ovan är 54:32:10:1A:BC:67 blir motsvarande länk-lokala adress:

```c
FE80::5632:10FF:FE1A:BC67
```
Observera att värd-ID-delen av IPv6-adressen (**5632:10FF:FE1A:BC67**) består av MAC-adressen på 6 byte med följande ändringar:

- **0xFFFE** mellan byte 3 och byte 4 av MAC-adressen
- Den näst lägsta biten av den första byten av MAC-adressen (U/L-bit) är inställd på 1

Mer information om hur du konstruerar värddelen av en IPv6-adress från gränssnittets MAC-adress finns i RFC 2464 (överföring av IPv6-paket över Ethernet-nätverk).

Det finns några särskilda multicast-adresser för att skicka multicast-meddelanden till en eller flera värdar i IPv6:

| Group  | Adress   | Description  |
|---|---|---|
|Gruppen Alla noder |**FF02::1** |Alla värdar i det lokala nätverket|
|Alla routergrupper |**FF02::2** |Alla routrar i det lokala nätverket|
|Begärd nod |**FF02::1:FF00:0/104** |Förklaras nedan|

En begärd multicast-adress med nod är inriktad på specifika värdar på den lokala länken i stället för alla IPv6-värdar. Den består av prefixet **FF02::1:FF00:0/104**, som är 104 bitar och de sista 24 bitarna i mål-IPv6-adressen. Till exempel har en IPv6-adress **205B:209D:D028::F058:D1C8:1024** en begärd multicast-adress för adressen **FF02::1:FFC8:1024.**

> [!IMPORTANT]
> *Den dubbla kolons notationen anger att de mellanliggande bitarna alla är nollor. **FF02::1:FF00:0/104*** fullständigt expanderad ser ut så **här: FF02:0000:0000:0000:0000:0001:FF00:0000**

### <a name="global-addresses"></a>Globala adresser    
Ett exempel på en global IPv6-adress är **2001:0123:4567:89AB:CDEF::1** NetX Duo lagrar IPv6-adresser i NXD_ADDRESS-strukturen. I exemplet nedan innehåller variabeln NXD_ADDRESS som **global_ipv6_address** unicast IPv6-adress. I följande exempel visas en NetX Duo-enhet som skapar en specifik global IPv6-adress för den primära enheten:

```c
NXD_ADDRESS global_ipv6_address;
UINT        primary_interface_index = 0;

global_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
global_ipv6_address.nxd_ip_address.v6[0] = 0x20010123;
global_ipv6_address.nxd_ip_address.v6[1] = 0x456789AB;
global_ipv6_address.nxd_ip_address.v6[2] = 0xCDEF0000;
global_ipv6_address.nxd_ip_address.v6[3] = 0x00000001;

status = nxd_ipv6_address_set(
            &ip_0,
            primary_interface_index,
            &global_ipv6_address,
            64,
            NX_NULL);
```
Observera att prefixet för den här IPv6-adressen är **2001:0123:4567:89AB,** som är 64 bitar långt och är en vanlig prefixlängd för globala unicast IPv6-adresser på Ethernet.

Den NXD_ADDRESS strukturen innehåller även IPv4-adresser. En IP-adress **på 192.1.168.10** (**0xC001A80A**) som lagras i global_ipv4_address skulle ha följande minneslayout:

|Fält |Värde |
|---|---|
|global_ipv4_address.nxd_ip_version |NX_IP_VERSION_V4|
|global_ipv4_address.nxd_ip_address.v4 |0xC001A80A|

När ett program skickar en adress till NetX Duo-tjänster *nxd_ip_version* fältet ange rätt IP-version för korrekt pakethantering.

NetX Duo stöder alla NetX-tjänster för att vara bakåtkompatibel med befintliga NetX-program. Internt konverterar NetX Duo IPv4-adresstypen ULONG till en NXD_ADDRESS-datatyp innan den vidarebefordras till den faktiska NetX Duo-tjänsten.

I följande exempel visas likheten och skillnaderna mellan tjänster i NetX och NetX Duo.

```c
/* Make a connection to the destination IPv4 address
   192.1.168.12 through an already created TCP socket bound
   to the well known HTTP port number 80. */

global_ipv4_address.nxd_ip_version = NX_IP_VERSION_V4;
global_ipv4_address.nxd_ip_address.v4 = 0xC001A80C;

nxd_tcp_client_socket_connect(&tcp_socket,
                              &global_ipv4_address,
                              port_number,
                              NX_WAIT_FOREVER);
```

Följande är motsvarande NetX API:

```c
ULONG         server_ip = 0xC001A80C;
NX_TCP_SOCKET tcp_socket;
UINT          port_number = 80;

nx_tcp_client_socket_connect(&tcp_socket,
                             server_ip,
                             port_number,
                             NX_WAIT_FOREVER); 
```

> [!IMPORTANT]
> *Programutvecklare uppmanas att använda nxd-versionen av dessa API:er.*

### <a name="ipv6-default-routers"></a>IPv6-standardroutrar    
IPv6 använder en standardrouter för att vidarebefordra paket till offlink-mål. NetX Duo-tjänsten ***nxd_ipv6_default_router_add*** ett program kan lägga till en IPv6-router i standardroutrtabellen. Se kapitel 4 "Beskrivning av tjänster" för fler standardroutningstjänster som erbjuds av NetX Duo.  

När du vidarebefordrar IPv6-paket kontrollerar NetX Duo först om paketets mål är på länken. Om inte, kontrollerar NetX Duo standardroutningens tabell efter en giltig router att vidarebefordra off-link-paketet till.  

Om du vill ta bort en router från IPv6-standardroutrtabellen ska programmet använda tjänsten ***nxd_ipv6_default_router_delete** _. Om du vill hämta poster i IPv6-standardroutrtabellen använder du tjänsten _*_nxd_ipv6_default_router_entry_get_**.

### <a name="ipv6-header"></a>IPv6-rubrik    
IPv6-huvudet har ändrats från IPv4-huvudet. När ett paket allokeras anger anroparen programprotokollet (t.ex. UDP, TCP), buffertstorleken i byte och hoppgränsen.   

Bild 9 visar formatet för IPv6-rubriken och tabellen visar rubrikkomponenterna.

![Diagram över IPv6-huvudformatet.](./media/user-guide/image18.png)

**BILD 9. Format för IPv6-huvud**

|IP-huvud | Syfte |
|---|---|
|Version |4-bitars fält för IP-version. För IPv6-nätverk måste värdet i det här fältet vara 6. För IPv4-nätverk måste det vara 4.|
|Trafikklass |8-bitars fält som lagrar trafikklassinformationen. Det här fältet används inte av NetX Duo.|
|Flow Etikett |20-bitars fält för att unikt identifiera flödet, om det finns något, som ett paket är associerat med. Värdet noll anger att paketet inte tillhör ett visst flöde. Det här fältet ersätter *TOS-fältet* i IPv4.|
|Nyttolastlängd |16-bitars fält som anger mängden data i byte för IPv6-paketet efter IPv6-bashuvudet. Detta inkluderar alla inkapslade protokollrubriker och data.|
|Nästa rubrik | 8-bitars fält som anger vilken typ av tilläggsrubrik som följer IPv6-basrubriken. Det här fältet ersätter *fältet* Protokoll i IPv4.|
|Hoppgräns |8-bitars fält som begränsar antalet routrar som paketet får passera. Det här fältet ersätter *TTL-fältet* i IPv4.|
|Källadress |128-bitars fält som lagrar avsändarens IPv6-adress.|
|Måladress |128-bitars fält som använder målets IPv6-adress.|

### <a name="enabling-ipv6-in-netx-duo"></a>Aktivera IPv6 i NetX Duo    
Som standard är IPv6 aktiverat i NetX Duo. IPv6-tjänster är aktiverade i NetX Duo om det konfigurerbara alternativet ***NX_DISABLE_IPV6** _ i _nx_user.h* inte har definierats. Om ***NX_DISABLE_IPV6*** definieras erbjuder NetX Duo endast IPv4-tjänster och alla IPv6-relaterade moduler och tjänster är inte inbyggda i NetX Duo-biblioteket.

Följande tjänst tillhandahålls för program för att konfigurera enhetens IPv6-adress: ***nxd_ipv6_address_set***

Förutom att manuellt ange enhetens IPv6-adresser kan systemet också använda automatisk konfiguration av tillståndslösa adresser. Om du vill använda det här alternativet måste programmet anropa ***nxd_ipv6_enable** _ för att starta IPv6-tjänster på enheten. Dessutom måste ICMPv6-tjänster startas genom att _*_anropa nxd_icmp_enable_*_, vilket gör att NetX Duo kan utföra tjänster som Router-begäran, Neighbor Discovery och dubblettadressidentifiering. Observera att _*_nx_icmp_enable_*_ bara startar ICMP för IPv4-tjänster. _*_nxd_icmp_enable_*_ startar ICMP-tjänster för både IPv4 och IPv6. Om systemet inte behöver ICMPv6-tjänster kan _ *_nx_icmp_enable_** användas så att ICMPv6-modulen inte är länkad till systemet.

I följande exempel visas en typisk initieringsprocedur för NetX Duo IPv6.

```c
/* Assume ip_0 has been created and IPv4 services (such as ARP,
   ICMP, have been enabled. */
#define SECONDARY_INTERFACE 1

/* Enable IPv6 */
status = nxd_ipv6_enable(&ip_0);

if(status != NX_SUCCESS)
{
    /* nxd_ipv6_enable failed. */
}

/* Enable ICMPv6 */
status = nxd_icmp_enable(&ip_0);
if(status != NX_SUCCESS)
{
    /* nxd_icmp_enable failed. */
}

/* Configure the link local address on the primary interface. */
status = nxd_ipv6_address_set(&ip_0, 0, NX_NULL, 10, NX_NULL);

/* Configure ip_0 primary interface global address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6
ip_address.nxd_ip_address.v6[0] = 0x20010db8;
ip_address.nxd_ip_address.v6[1] = 0x0000f101;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 0x202;

/* Configure global address of the primary interface. */
status = nxd_ipv6_address_set(&ip_0, SECONDARY_INTERFACE,
                              &ip_address, 64, NX_NULL);
```                              

Övre lagerprotokoll (till exempel TCP och UDP) kan aktiveras antingen före eller efter att IPv6 startar.

> [!IMPORTANT]  
> *IPv6-tjänster är endast tillgängliga när IP-tråden har initierats och enheten har aktiverats.*

När gränssnittet har aktiverats (dvs. gränssnittets enhetsdrivrutin är redo att skicka och ta emot data och en giltig lokal länkadress har erhållits) kan enheten hämta globala IPv6-adresser med någon av följande metoder:

- Automatisk konfiguration av tillståndslös adress;  
- Manuell IPv6-adresskonfiguration;  
- Adresskonfiguration via DHCPv6 (med valfritt DHCPv6-paket)

De första två metoderna beskrivs nedan. Den tredje metoden (DHCPv6) beskrivs i DHCP-paketet.

### <a name="stateless-address-autoconfiguration-using-router-solicitation"></a>Automatisk konfiguration av tillståndslös adress med routeröversättning      
NetX Duo-enheter kan konfigurera sina gränssnitt automatiskt när de är anslutna till ett IPv6-nätverk med en router som tillhandahåller prefixinformation. Enheter som kräver tillståndslös automatisk adresskonfiguration skickar ut RS-meddelanden (routeröversättning). Routrar i nätverket svarar med begärda meddelanden från routerannonsering (RA). RA-meddelanden annonserar prefix som identifierar de nätverksadresser som är associerade med en länk. Enheter genererar sedan en unik identifierare för nätverket som enheten är ansluten till. Adressen skapas genom att prefixet och dess unika identifierare kombineras. På det här sättet genererar värdarna sina IP-adresser när de tar emot RA-meddelanden. Routrar kan också skicka periodiska oönskade RA-meddelanden. 

> [!WARNING]
> *Med NetX Duo kan ett program aktivera eller inaktivera automatisk konfiguration av tillståndslös adress vid körning. Om du vill aktivera den här funktionen måste NetX Duo-biblioteket kompileras med **NX_IPV6_STATELESS_AUTOCONFIG_CONTROL** definieras. När den här funktionen har  aktiverats kan* program använda nxd_ipv6_stateless_address_autoconfigure_enable och nxd_ipv6_stateless_address_autocofigure_disable för att aktivera eller inaktivera den tillståndslösa IPv6-adresskonfigurationen.

### <a name="manual-ipv6-address-configuration"></a>Manuell IPv6-adresskonfiguration     
Om en specifik IPv6-adress behövs kan programmet använda ***nxd_ipv6_address_set*** konfigurera en IPv6-adress manuellt. Ett nätverksgränssnitt kan ha flera IPv6-adresser. Tänk dock på att det totala antalet IPv6-adresser i ett system, som antingen hämtas via tillståndslös automatisk adresskonfiguration eller via den manuella konfigurationen, inte ***får överskrida NX_MAX_IPV6_ADDRESSES***.

I följande exempel visas hur du manuellt konfigurerar en global adress i det primära gränssnittet (enhet 0) i ip_0:

```c
NXD_ADDRESS global_address;
global_address.nxd_ip_version = NX_IP_VERSION_V6;
global_address.nxd_ip_address.v6[0] = 0x20010000;
global_address.nxd_ip_address.v6[1] = 0x00000000;
global_address.nxd_ip_address.v6[2] = 0x00000000;
global_address.nxd_ip_address.v6[3] = 0x0000ABCD;
```

Värden anropar sedan följande NetX Duo-tjänst för att tilldela den här adressen som dess globala IP-adress:

```c
status = nxd_ipv6_address_set(&ip_0, 0,  
                              &global_address, 64
                              NX_NULL);
```

### <a name="duplicate-address-detection-dad"></a>Dubblettadressidentifiering (MENS)    
När ett system konfigurerar sin IPv6-adress markeras adressen som *PVATIVE*. Om dubblettadressidentifiering (DW), som beskrivs i RFC 4862, är aktiverat, skickar NetX Duo automatiskt NS-meddelanden (neighbor-förfrågning) med den här adressen som mål. Om inga värdar i nätverket svarar på dessa NS-meddelanden inom en viss tidsperiod antas adressen vara unik för den lokala länken och dess tillstånd överförs till DET GILTIGA tillståndet. I det här läget kan programmet börja använda den här IP-adressen för kommunikation.  

FUNKTIONEN ÄR en del av ICMPv6-modulen. Därför måste programmet aktivera ICMPv6-tjänster innan en nykonfigurerad adress kan gå igenom PROCESSA. Alternativt kan PROCESS AV stängas av genom att definiera ***NX_DISABLE_IPV6_DAD** _ alternativet i NetX Duo-biblioteksbyggmiljön (definieras _*_som nx_user.h_*_). Under PROCESS AV _**_ anger NX_IPV6_DAD_TRANSMITS-parametern antalet NS-meddelanden som skickas av NetX Duo utan att ta emot något svar för att fastställa att adressen är unik. Som standard och rekommenderas av RFC 4862 är _ *_NX_IPV6_DAD_TRANSMITS_** inställt på 3. Om du ställer in den här symbolen på noll inaktiveras EFFEKTIVT INVALID.

Om ICMPv6 eller PV inte är aktiverat när programmet tilldelar en IPv6-adress, utförs INTE PV och NetX Duo anger tillståndet för IPv6-adressen till GILTIG omedelbart.

NetX Duo kan inte kommunicera i IPv6-nätverket förrän dess lokala och/eller globala adress är giltig. När en giltig adress har erhållits försöker NetX Duo matcha måladressen för ett inkommande paket mot en av dess konfigurerade IPv6-adress eller en aktiverad multicast-adress. Om inga matchningar hittas tas paketet bort. 

> [!WARNING]  
> *Under PROCESS PROCESS AVS definieras antalet PACKET NS som ska överföras av ***NX_IPV6_DAD_TRANSMITS**, som standard är 3, och som standard skickas en sekunds fördröjning mellan varje _NS-meddelande. När en IPv6-adress_ har tilldelats (och förutsatt att det inte är en duplicerad adress) i ett system där HAR AKTIVERATs, finns det därför cirka 3 sekunders fördröjning innan IP-adressen är i ett giltigt tillstånd och är redo för kommunikation.

Program kan vilja ta emot meddelanden när IPv6-adresser i systemet ändras. Om du vill aktivera funktionen för meddelanden om ändring av IPv6-adress måste NetX Duo-biblioteket byggas med symbolen **NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY** definierad. När funktionen har aktiverats kan program installera återanropsfunktionen med hjälp av **_nxd_ipv6_address_change_notify tjänsten._**

När en IPv6-adress ändras eller blir ogiltig anropas den återanropsfunktion som användaren har angett med följande information:

| Funktion  | Beskrivning  |
|---|---|
|ip_ptr |Pekare till IP-instansen|
|interface_index |Indexera till nätverksgränssnittet som den här IPv6-adressen är associerad med
|ipv6_addr_index |Indexera till IPv6-adresstabellen|
|ipv6_address |Pekare till IPv6-adressen i form av en matris med fyra ULONG-heltal. Pv6-adresser visas i värdbyteordning.|

### <a name="ipv6-multicast-support-in-netx-duo"></a>Stöd för IPv6 Multicast i NetX Duo      
Multicast-adresser anger en dynamisk grupp med värdar på Internet. Medlemmar i multicast-gruppen kan gå med och lämna när de vill. NetX Duo implementerar flera ICMPv6-protokoll, inklusive dubblettadressidentifiering, neighbor discovery och routeridentifiering, som kräver IP-multicast-kapacitet. Därför förväntar sig NetX Duo att den underliggande enhetsdrivrutinen stöder multicast-åtgärder.

När NetX Duo behöver ansluta till eller lämna en multicast-grupp (till exempel multicast-adressen för alla noder och den begärda multicast-adressen) utfärdar den ett drivrutinskommando till enhetsdrivrutinen för att ansluta till eller lämna en multicast *MAC-adress.* Drivrutinskommandot för att ansluta till multicast-adressen är ***NX_LINK_MULTICAST_JOIN** _. Om du vill lämna en multicast-adress utfärdar NetX Duo drivrutinskommandot _*_NX_LINK_MULTICAST_LEAVE_**. Enhetsdrivrutinen måste implementera dessa två kommandon för att ICMPv6-protokollen ska fungera korrekt.

Program kan ansluta till en IPv6-multicast-grupp med hjälp av tjänsten ***nxd_ipv6_multicast_interface_join*.** Den här tjänsten registrerar multicast-adressen med IP-stacken och meddelar sedan den angivna enhetsdrivrutinen om IPv6-multicast-adressen. Om du vill lämna en multicast-grupp använder program tjänsten ***nxd_ipv6_multicast_interface_leave.***

### <a name="neighbor-discovery-nd"></a>Neighbor Discovery (ND)    
Neighbor Discovery är ett protokoll i IPv6-nätverk för mappning av fysiska adresser till IPv6-adresser (global adress eller länk-lokal adress). Den här mappningen finns i Neighbor Discovery Cache (ND Cache). ND-processen motsvarar ARP-processen i IPv4 och ND Cache liknar ARP-tabellen. En IPv6-nod kan hämta grannens MAC-adress med hjälp av ND-protokollet (Neighbor Discovery). Den skickar ett meddelande om granne-begäran (NS) till den nod som efterfrågas multicast-adressen och väntar på ett motsvarande NA-meddelande (neighbor advertisement). MAC-adressen som erhålls genom den här processen lagras i ND-cachen.

Varje IP-instans har en ND-cache. ND Cache underhålls som en matris med poster. Matrisens storlek definieras vid kompileringstiden genom att ange alternativet ***NX_IPV6_NEIGHBOR_CACHE_SIZE** _ som i _*_nx_user.h_**. Observera att alla gränssnitt som är anslutna till en IP-instans delar samma ND-cache.

Hela ND Cache är tom när NetX Duo startar. När systemet körs uppdaterar NetX Duo automatiskt ND Cache och lägger till och tar bort poster enligt ND-protokollet. Ett program kan dock även uppdatera ND-cachen genom att manuellt lägga till och ta bort cacheposter med hjälp av följande NetX Duo-tjänster:

- ***nxd_nd_cache_entry_delete***  
- ***nxd_nd_cache_entry_set***   
- ***nxd_nd_cache_invalidate***

När du skickar och tar emot IPv6-paket uppdaterar NetX Duo automatiskt ND Cache-tabellen.

## <a name="internet-control-message-protocol-in-ipv6-icmpv6"></a>Internet Control Message Protocol i IPv6 (ICMPv6)  

Rollen som ICMPv6 i IPv6 har utökats kraftigt för att stödja IPv6-adressmappning och routeridentifiering. Dessutom stöder NetX Duo ICMPv6 ekobegäran och svar, ICMPv6-felrapporter och ICMPv6-omdirigeringsmeddelanden.

### <a name="icmpv6-enable"></a>Aktivera ICMPv6    
Innan ICMPv6-meddelanden kan bearbetas av NetX Duo måste programmet anropa ***nxd_icmp_enable-tjänsten*** för att aktivera ICMPv6-bearbetning enligt tidigare förklaring. 

### <a name="icmpv6-messages"></a>ICMPv6-meddelanden     
ICMPv6-rubrikstrukturen liknar ICMPv4-rubrikstrukturen. Som du ser nedan innehåller den grundläggande ICMPv6-rubriken de tre fälten, typ, kod och kontrollsumma, plus variabel längd på ICMPv6-alternativdata. 

![Diagram över ett grundläggande ICMPv6-huvud.](./media/user-guide/image19.png)

**BILD 10. Grundläggande ICMPv6-huvud**

|Fält |Size(bytes) |Beskrivning |
|-----|-----|-----|
|     | 1   |Identifierar meddelandetypen ICMPv6. |
|     |     |1 Det går inte att nå målet |
|     |     |2 paket är för stort |
|     |     |3 överskriden tid |
|     |     |4 Parameterproblem |
|     |     |128 Ekobegäran |
|     |     |129 Ekosvar |
|     |     |133 Router-begäran |
|     |     |134 Router Advertisement |
|     |     |135 Neighbor-begäran |
|     |     |136 Neighbor Advertisement |
|     |     |137 Omdirigeringsmeddelande |
|Kod | 1   |Kvalificerar även ICMPv6-meddelandetypen. Används vanligtvis med felmeddelanden. Om den inte används anges den till noll. Ekobegäran/svar och NS-meddelanden använder den inte.|
|Kontrollsumma | 2 |16-bitars kontrollsummafält för ICMP-huvudet. Det här är ett 16-bitars komplement till hela ICMPv6-meddelandet, inklusive ICMPv6-huvudet. Den innehåller också en pseudorubrik för IPv6-källadressen, måladressen och paketnyttolastens längd. |

Ett exempel på angränsande begäranderubrik visas nedan.

![Diagram över ett exempel på angränsande begäranderubrik.](./media/user-guide/image20.jpg)

**BILD 11. ICMPv6-rubrik för ett angränsande begärandemeddelande**

|Fält |Size(bytes) |Beskrivning |
|-----|-----|-----|
|Typ | 1   |Identifierar ICMPv6-meddelandetypen för angränsande begärandemeddelanden. Värdet är 135. |
|Kod | 1   |Används inte. Ange till 0. |
|Kontrollsumma | 2  |16-bitars kontrollsummafält för ICMPv6-huvudet. |
|Reserverat | 4  |4 reserverade byte inställt på 0. |
|Måladress | 16  |IPv6-adress för målet för begäran. För IPv6-adressmatchning är detta den faktiska unicast-IP-adressen för den enhet vars adress på länklagret måste matchas. |
|Alternativ | Variabel |Valfri information som anges av Neighbor Discovery Protocol. |

### <a name="icmpv6-ping-request"></a>Begäran om ICMPv6-ping
I NetX Duo-program ***använder nxd_icmp_ping*** för att utfärda Antingen IPv6- eller IPv4-pingbegäranden, baserat på målets IP-adress som anges i parametrarna.  

### <a name="icmpv6-ping-response"></a>ICMPv6 Ping-svar
Ett ICMPv6-pingsvar är en annan typ av ICMPv6-meddelande som genereras internt av ICMPv6-komponenten som svar på en extern ICMPv6-pingbegäran. Utöver bekräftelsen innehåller ICMPv6-pingsvaret även en kopia av användardata som anges i ICMPv6-pingbegäran.  

### <a name="thread-suspension"></a>Trådavstängning
Programtrådar kan pausa vid försök att pinga en annan nätverksmedlem. När ett pingsvar tas emot ges pingsvarsmeddelandet till den första tråden som pausas och tråden återupptas. Precis som alla NetX Duo-tjänster har en valfri tidsgräns för att pausa en pingbegäran.  

### <a name="other-icmpv6-messages"></a>Andra ICMPv6-meddelanden
ICMPv6-meddelanden krävs för följande funktioner:  

- Granneidentifiering  
- Automatisk konfiguration av tillståndslös adress 
- Routeridentifiering 
- Neighbor Unreachability Detection  

### <a name="neighbor-unreachability-router-and-prefix-discovery"></a>Neighbor Unreachability, Router and Prefix Discovery    
Neighbor Unreachability Detection, Router Discovery och Prefix Discovery baseras på Neighbor Discovery-protokollet och beskrivs nedan. 

***Identifiering av onåbarhet för granne:*** En IPv6-enhet söker i sin ND-cache (Neighbor Discovery) efter mållänklagrets adress när den vill skicka ett paket. Det omedelbara målet, som ibland kallas "nästa hopp", kan vara det faktiska målet på samma länk, eller så kan det vara en router om målet är avlänkat. En ND-cachepost innehåller status för en grannes nåbarhet.

Statusen NÅBAR anger att grannen anses vara nåbar. En granne kan nås om den nyligen har fått en bekräftelse på att paket som skickats till grannen har tagits emot. Bekräftelse i NetX Duo tar emot ett NA-meddelande från grannen som svar på ett NS-meddelande som skickas av NetX Duo-enheten. NetX Duo ändrar också tillståndet för grannstatusen till REACHABLE om programmet anropar NetX Duo-tjänsten ***nxd_nd_cache_entry_set*** att manuellt ange en cachepost.

***Routeridentifiering:*** En IPv6-enhet använder en router för att vidarebefordra alla paket som är avsedda för off-link-mål. Den kan också använda information som skickas av routern, till exempel routerannonseringsmeddelanden (RA) för att konfigurera dess globala IPv6-adresser.

En enhet i nätverket kan initiera routeridentifieringsprocessen genom att skicka ett RS-meddelande (routeröversättning) till multicast-adressen för alla routrar (FF01::2). Eller så kan den vänta på multicast-adressen för alla noder (FF::1) för en periodisk RA från routrarna.

Ett RA-meddelande innehåller prefixinformationen för att konfigurera en IPv6-adress för nätverket. I NetX Duo är router-begäran som standard aktiverad och kan inaktiveras genom att ange konfigurationsalternativet ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _ i _*_nx_user.h_**. Se Konfigurationsalternativ i kapitlet "Installation och användning av NetX Duo" för mer information om hur du anger parametrar för routeröversättning. 

***Prefixidentifiering:*** En IPv6-enhet använder prefixidentifiering för att lära sig vilka målvärdar som är tillgängliga direkt utan att gå via en router. Den här informationen görs tillgänglig för IPv6-enheten från RA-meddelanden från routern. IPv6-enheten lagrar prefixinformationen i en prefixtabell. Prefixidentifiering matchar ett prefix från tabellen med IPv6-enhetsprefix till en måladress. Ett prefix matchar en måladress om alla bitar i prefixet matchar de viktigaste bitarna i måladressen. Om fler än ett prefix omfattar en adress väljs det längsta prefixet.

### <a name="icmpv6-error-messages"></a>Felmeddelanden för ICMPv6    
Följande ICMPv6-felmeddelanden stöds i NetX Duo:  

- Det går inte att nå målet  
- Paket för stort  
- Överskriden tid  
- Parameterproblem  

## <a name="user-datagram-protocol-udp"></a>UDP (User Datagram Protocol)

UDP (User Datagram Protocol) är den enklaste formen av dataöverföring mellan nätverksmedlemmar (RFC 768). UDP-datapaket skickas från en nätverksmedlem till en annan på bästa sätt. Det finns alltså ingen inbyggd mekanism för bekräftelse av paketmottagaren. Att skicka ett UDP-paket kräver inte heller att någon anslutning upprättas i förväg. Därför är UDP-paketöverföring mycket effektivt.

För utvecklare som migrerar sina NetX-program till NetX Duo finns det bara några grundläggande ändringar i UDP-funktionerna mellan NetX och NetX Duo. Det beror på att IPv6 främst handlar om det underliggande IP-lagret. Alla NetX Duo UDP-tjänster kan användas för Antingen IPv4- eller IPv6-anslutning.

### <a name="udp-header"></a>UDP-rubrik       
UDP placerar ett enkelt pakethuvud framför programmets data vid överföring och tar bort ett liknande UDP-huvud från paketet vid mottagning innan ett mottaget UDP-paket levereras till programmet. UDP använder IP-protokollet för att skicka och ta emot paket, vilket innebär att det finns ett IP-huvud framför UDP-huvudet när paketet finns i nätverket. Bild 12 visar UDP-rubrikens format.

![Diagram över UDP-rubrikformatet.](./media/user-guide/image21.png)

### <a name="figure-12-udp-header"></a>BILD 12. UDP-rubrik

> [!NOTE]
> *Alla huvuden i UDP/IP-implementeringen förväntas vara **i big endian** format. I det här formatet finns den viktigaste byten av ordet på den lägsta byteadressen.*

Följande beskriver UDP-rubrikformatet:

|Rubrikfält |Syfte |
|---|---|
|**16-bitars källportnummer** |Det här fältet innehåller porten som UDP-paketet skickas från. Giltiga UDP-portar sträcker sig från 1 till 0xFFFF. |
|**Portnummer för 16-bitarsmål** |Det här fältet innehåller UDP-porten som paketet skickas till. Giltiga UDP-portar sträcker sig från 1 till 0xFFFF. |
|**16-bitars UDP-längd** |Det här fältet innehåller antalet byte i UDP-paketet, inklusive storleken på UDP-huvudet. |
|**16-bitars UDP-kontrollsumma** |Det här fältet innehåller 16-bitars kontrollsumma för paketet, inklusive UDP-huvudet, paketdataområdet och pseudo-IP-huvudet. |

### <a name="udp-enable"></a>UDP-aktivera   
Innan UDP-paketöverföring är möjligt måste programmet först  aktivera UDP genom att anropa nx_udp_enable tjänsten. När det har aktiverats kan programmet skicka och ta emot UDP-paket.  

### <a name="udp-socket-create"></a>Skapa UDP-socket    
UDP-sockets skapas antingen under initieringen eller under körning av programtrådar. Den första typen av tjänst, TT-tid och  mottagning av ködjup definieras av nx_udp_socket_create tjänsten. Det finns inga begränsningar för antalet UDP-socketar i ett program.

### <a name="udp-checksum"></a>UDP-kontrollsumma   
IPv6-protokollet kräver en beräkning av kontrollsumma för UDP-huvud på paketdata, medan det i IPv4-protokollet är valfritt.  

UDP anger ett komplement till 16-bitars kontrollsumma som omfattar IP-pseudorubriken (som består av källans IP-adress, målets IP-adress och protokoll-/längd-IP-ordet), UDP-huvudet och UDP-paketdata. De enda skillnaderna mellan kontrollsummerna för IPv4- och IPv6 UDP-pakethuvud är att käll- och mål-IP-adresserna är 32-bitars i IPv4 och i IPv6 är de 128 bitar. Om den beräknade UDP-kontrollsumman är 0 lagras den som alla (0xFFFF). Om den skickande socketen har logiken för UDP-kontrollsumma inaktiverad placeras noll i fältet UDP-kontrollsumma för att indikera att kontrollsumman inte beräknades.

Om UDP-kontrollsumman inte matchar den beräknade kontrollsumman av mottagaren ignoreras UDP-paketet.

I IPv4-nätverket är UDP-kontrollsumma valfri. Med NetX Duo kan ett program aktivera eller inaktivera UDP-kontrollsummberäkning per socket. Som standard är logiken för UDP-socketkontrollsumma aktiverad. Programmet kan inaktivera logik för kontrollsumma för en viss UDP-socket genom att anropa tjänsten ***nx_udp_socket_checksum_disable** _ . I IPv6-nätverket är dock UDP-kontrollsumma obligatorisk. Tjänsten _ nx_udp_socket_checksum_disable **_inaktiverar_* därför inte logiken för UDP-kontrollsumma när ett paket skickas via IPv6-nätverket.

Vissa Ethernet-styrenheter kan generera UDP-kontrollsumman i farten. Om systemet kan använda beräkningsfunktionen kontrollsumma för maskinvara kan NetX Duo-biblioteket byggas utan logiken för kontrollsumma. Om du vill inaktivera kontrollsumma för UDP-programvara måste NetX Duo-biblioteket byggas med följande definierade symboler: ***NX_DISABLE_UDP_TX_CHECKSUM** _ _*_NX_DISABLE_UDP_RX_CHECKSUM_*_ (beskrivs i kapitel två). Konfigurationsalternativen tar bort UDP-kontrollsummalogiken från NetX Duo helt och hållet medan tjänsten _ *_nx_udp_socket_checksum_disable_** anropar gör att programmet kan inaktivera IPv4 UDP-kontrollsummabearbetning per socket.

### <a name="udp-ports-and-binding"></a>UDP-portar och bindning      
En UDP-port är en logisk slutpunkt i UDP-protokollet. Det finns 65 535 giltiga portar i UDP-komponenten i NetX Duo, från 1 till 0xFFFF. Om du vill skicka eller ta emot UDP-data måste programmet först skapa en UDP-socket och sedan binda den till en önskad port. När du har bindat en UDP-socket till en port kan programmet skicka och ta emot data på den socketen.

### <a name="udp-fast-pathtrade"></a>Snabb sökväg för UDP&trade;   
Den snabba &trade; UDP-sökvägen är namnet på en låg paketkostnadsväg via NetX Duo UDP-implementeringen. Att skicka ett UDP-paket kräver bara några funktionsanrop: ***nx_udp_socket_send** _, _*_nx_ip_packet_send_*_, och det slutliga anropet till nätverksdrivrutinen. _*_nx_udp_socket_send_*_ är tillgänglig i NetX Duo för befintliga NetX-program och gäller endast för IPv4-paket. Den föredragna metoden är dock att använda tjänsten _ *_nxd_udp_socket_send_** som beskrivs nedan. Vid UDP-paketmottagande placeras UDP-paketet antingen i lämplig UDP-socket-mottagningskö eller levereras till en pausad programtråd i ett enda funktionsanrop från nätverksdrivrutinens bearbetning av avbrott. Den här mycket optimerade logiken för att skicka och ta emot UDP-paket är grunden för UDP Fast Path-teknik.  

### <a name="udp-packet-send"></a>Skicka UDP-paket    
Det är enkelt att skicka UDP-data via IPv6- eller IPv4-nätverk genom att anropa funktionen ***nxd_udp_socket_send** _ . Anroparen måste ange IP-versionen i fältet _nx_ip_version* för den NXD_ADDRESS pekarparametern. NetX Duo fastställer den bästa källadressen för överförda UDP-paket baserat på målets IPv4/IPv6-adress. Den här tjänsten placerar ett UDP-huvud framför paketdata och skickar ut dem till nätverket med hjälp av en intern IP-sändrutin. Det finns ingen trådavstängning för att skicka UDP-paket eftersom alla UDP-paketöverföringar bearbetas omedelbart. 

För multicast- eller broadcast-mål bör programmet ange den IP-källadress som ska användas om NetX Duo-enheten har flera IP-adresser att välja mellan. Detta kan göras med de tjänster ***som nxd_udp_socket_source_send.***

> [!IMPORTANT]    
> *Om **nx_udp_socket_send** används för att överföra multicast-* eller broadcast-paket används IP-adressen för det första aktiverade gränssnittet som källadress .

> [!NOTE] 
> *Om UDP-kontrollsummalogik* är aktiverad för den här socketen utförs åtgärden för kontrollsumma i kontexten för den anropande tråden, utan att blockera åtkomsten till UDP- eller IP-datastrukturerna . 

> [!WARNING]    
> *UDP-nyttolastdata som finns i NX_PACKET bör finnas på en lång ordgräns. Programmet måste lämna tillräckligt med utrymme* mellan den förberedande pekaren och datastartspekaren för NetX Duo för att placera UDP-, IP- och fysiska medierubriker .

### <a name="udp-packet-receive"></a>UDP-paket ta emot    
Programtrådar kan ta emot UDP-paket från en viss socket genom att anropa ***nx_udp_socket_receive***. Funktionen socket receive levererar det äldsta paketet på socketens mottagningskö. Om det inte finns några paket i mottagningskön kan den anropande tråden pausa (med en valfri tidsgräns) tills ett paket anländer.

UDP-mottagningspaketbearbetningen (anropas vanligtvis från nätverksdrivrutinens mottagningsavbrottshanterare) ansvarar för att antingen placera paketet i UDP-socketens mottagningskö eller leverera det till den första pausade tråden som väntar på ett paket. Om paketet köas kontrollerar mottagningsbearbetningen även det maximala mottagningsködjupet som är associerat med socketen. Om det nyligen köade paketet överskrider ködjupet tas det äldsta paketet i kön bort.

### <a name="udp-receive-notify"></a>UDP Receive Notify   
Om programtråden behöver bearbeta mottagna data från mer än en socket, ***nx_udp_socket_receive_notify-funktionen*** användas. Den här funktionen registrerar en återanropsfunktion för mottagningspaket för socketen. När ett paket tas emot på socketen körs återanropsfunktionen.

Innehållet i återanropsfunktionen är programspecifikt. Det skulle dock sannolikt innehålla logik för att informera bearbetningstråden om att ett paket nu är tillgängligt på motsvarande socket.

### <a name="peer-address-and-port"></a>Peer-adress och port   
När ett UDP-paket tas emot kan programmet hitta avsändarens IP-adress och portnummer med hjälp av ***tjänsten nx_udp_packet_info_extract***. Vid lyckad retur innehåller den här tjänsten information om avsändarens IP-adress, avsändarens portnummer och det lokala gränssnitt som paketet togs emot via.  

### <a name="thread-suspension"></a>Trådavstängning   
Som tidigare nämnts kan programtrådar pausa vid försök att ta emot ett UDP-paket på en viss UDP-port. När ett paket tas emot på den porten ges det till den första tråden som pausas och tråden återupptas sedan. En valfri tidsgräns är tillgänglig när du pausar ett UDP-mottagningspaket, en funktion som är tillgänglig för de flesta NetX Duo-tjänster.  

### <a name="udp-socket-statistics-and-errors"></a>UDP Socket-statistik och fel     
Om den är aktiverad håller NetX Duo UDP-socketprogrammet reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP/UDP-instans:

- Totalt antal UDP-paket som skickats  
- Totalt antal UDP-byte som skickats  
- Totalt antal mottagna UDP-paket   
- Totalt antal mottagna UDP-byte  
- Totalt antal ogiltiga UDP-paket  
- Totalt antal bort ignorerade UDP-mottagningspaket  
- Totalt antal UDP-fel vid mottagning av kontrollsumma  
- UDP Socket-paket som skickats  
- UDP-socketbyte skickade  
- Mottagna UDP Socket-paket   
- Mottagna UDP Socket-byte  
- UDP Socket-paket i kö  
- UDP Socket Receive Packets Dropped  
- UDP Socket Checksum Errors  

Alla dessa statistik- och felrapporter är tillgängliga för programmet med tjänsten ***nx_udp_info_get** _ för UDP-statistik som har amasserats över alla UDP-sockets och tjänsten _ *_nx_udp_socket_info_get_** för UDP-statistik på den angivna UDP-socketen.

### <a name="udp-socket-control-block-nx_udp_socket"></a>UDP Socket Control Block NX_UDP_SOCKET
Egenskaperna för varje UDP-socket finns i det associerade NX_UDP_SOCKET kontrollblocket. Den innehåller användbar information, till exempel länken till IP-datastrukturen, nätverksgränssnittet för de skickande och mottagande sökvägarna, den bundna porten och kön för inkommande paket. Den här strukturen definieras i ***nx_api.h-filen.***

## <a name="transmission-control-protocol-tcp"></a>Transmission Control Protocol (TCP)

Med Transmission Control Protocol (TCP) kan du överföra tillförlitlig dataströmdata mellan två nätverksmedlemmar (RFC 793). Alla data som skickas från en nätverksmedlem verifieras och bekräftas av den mottagande medlemmen. Dessutom måste de två medlemmarna ha upprättat en anslutning innan dataöverföringen. Allt detta resulterar i tillförlitlig dataöverföring; Det kräver dock betydligt mer omkostnader än den tidigare beskrivna UDP-dataöverföringen.

Förutom där det anges finns det inga ändringar i TCP-protokoll-API-tjänster mellan NetX och NetX Duo eftersom IPv6 främst handlar om det underliggande IP-lagret. Alla NetX Duo TCP-tjänster kan användas för Antingen IPv4- eller IPv6-anslutningar.

### <a name="tcp-header"></a>TCP-huvud   
Vid överföring placeras TCP-huvudet framför data från användaren. Vid mottagning tas TCP-huvudet bort från det inkommande paketet, så att endast användardata är tillgängliga för programmet. TCP använder IP-protokollet för att skicka och ta emot paket, vilket innebär att det finns ett IP-huvud framför TCP-huvudet när paketet finns i nätverket. Bild 13 visar formatet för TCP-huvudet.

![Diagram över TCP-huvudformatet.](./media/user-guide/image22.png)

### <a name="figure-13-tcp-header"></a>BILD 13. TCP-huvud

Följande beskriver TCP-huvudformatet:

|&nbsp;Rubrikfält |Syfte |
|------|------|
| **Portnummer för 16-bitars källa** | Det här fältet innehåller porten som TCP-paketet skickas ut på. Giltiga TCP-portar sträcker sig från 1 till 0xFFFF. |
| **16-bitars målport** | Det här fältet innehåller TCP-porten som paketet skickas till. Giltiga TCP-portar sträcker sig från 1 till 0xFFFF. |
| **32-bitars sekvensnummer** | Det här fältet innehåller sekvensnumret för data som skickas från den här änden av anslutningen. Den ursprungliga sekvensen upprättas under den första anslutningssekvensen mellan två TCP-noder. Varje dataöverföring från den punkten resulterar i en ökning av sekvensnumret med mängden byte som skickas. |
| **32-bitars bekräftelsenummer** | Det här fältet innehåller sekvensnumret som motsvarar den sista byten som tagits emot av den här sidan av anslutningen. Detta används för att avgöra om data som tidigare har skickats har tagits emot av den andra änden av anslutningen. |
| **4-bitars rubriklängd** | Det här fältet innehåller antalet 32-bitars ord i TCP-rubriken. Om det inte finns några alternativ i TCP-huvudet är det här fältet 5. |
| **6-bitars kod bitar** |Det här fältet innehåller de sex olika kodbitarna som används för att ange olika kontrollinformation som är associerad med anslutningen. Kontrollbitarna definieras enligt följande:<br \> - URG (21): Brådskande data före<br \> - ACK (20): Bekräftelsenumret är giltigt<br \> – PSH (19): Hantera dessa data omedelbart<br - RST (18): Återställ anslutningen<br - SYN (17): Synkronisera sekvensnummer (används för att upprätta \> \> anslutning)<br \> - FIN (16): Avsändaren har slutfört överföringen (används för att stänga anslutningen) |
|**16-bitars fönster** |Det här fältet används för flödeskontroll. Den innehåller mängden byte som socketen för närvarande kan ta emot. Detta används i princip för flödeskontroll. Avsändaren ansvarar för att se till att de data som ska skickas får plats i mottagarens annonserade fönster. |
|**16-bitars TCP-kontrollsumma** |Det här fältet innehåller 16-bitars kontrollsumma för paketet, inklusive TCP-huvudet, paketdataområdet och pseudo-IP-huvudet. |
|**16-bitars brådskande pekare** |Det här fältet innehåller den positiva förskjutningen av den sista byten av brådskande data. Det här fältet är endast giltigt om URG-kodbiten har angetts i rubriken. |

> [!NOTE]  
> *Alla huvuden i TCP/IP-implementeringen förväntas vara **i big endian** format. I det här formatet finns den viktigaste byten av ordet på den lägsta byte-adressen*.

### <a name="tcp-enable"></a>TCP-aktivera       
Innan TCP-anslutningar och paketöverföringar är möjliga måste programmet  först aktivera TCP genom att anropa nx_tcp_enable tjänsten. När det är aktiverat kan programmet komma åt alla TCP-tjänster.  

### <a name="tcp-socket-create"></a>Skapa TCP Socket    
TCP-sockets skapas antingen under initieringen eller under körning av programtrådar. Den första typen av tjänst, TT-tid och  fönsterstorlek definieras av nx_tcp_socket_create tjänsten. Det finns inga begränsningar för antalet TCP-sockets i ett program.  

### <a name="tcp-checksum"></a>TCP-kontrollsumma     
TCP anger ett komplement till en 16-bitars kontrollsumma som omfattar IP-pseudorubriken (som består av källans IP-adress, målets IP-adress och protokollets/längdens IP-ord), TCP-huvudet och TCP-paketdata. Den enda skillnaden mellan kontrollsumor för IPv4- och IPv6-pakethuvud är att käll- och mål-IP-adresserna är 32-bitars i IPv4 och 128-bitars i IPv6. 

Vissa nätverksstyrenheter kan utföra beräkning och validering av TCP-kontrollsumma i maskinvaran. För sådana system kanske program vill använda logik för kontrollsumma för maskinvara så mycket som möjligt för att minska körningskostnader. Program kan inaktivera beräkningslogik för TCP-kontrollsumma från NetX Duo-biblioteket helt vid byggtiden genom att definiera ***NX_DISABLE_TCP_TX_CHECKSUM** _ och _*_NX_DISABLE_TCP_RX_CHECKSUM_**. På så sätt kompileras inte TCP-kontrollsummakoden. Var dock försiktig om det valfria NetX Duo IPsec-paketet är installerat och TCP-anslutningen kan behöva passera via en säker kanal. I det här fallet är data i paket som hör till TCP-anslutningen redan krypterade, och de flesta moduler för TCP-kontrollsumma för maskinvara som finns i nätverksdrivrutinen kan inte generera rätt kontrollsummavärde från den krypterade TCP-nyttolasten.

För att lösa det här problemet ska programmet ha logiken för TCP-kontrollsumma tillgänglig i biblioteket och använda gränssnittsfunktionen. När gränssnittsfunktionen är aktiverad vet TCP-modulen hur TCP-kontrollsumman ska hanteras korrekt om drivrutinen också kan beräkna kontrollsummavärdet:

1) Om TCP-paketet inte omfattas av IPsec-processen kan nätverksgränssnittsmaskinvaran beräkna kontrollsumman. Tcp-modulen försöker därför inte beräkna kontrollsumman.

2) Om IPsec-paketet är installerat och TCP-paketet omfattas av IPsec-processen beräknar TCP-modulen kontrollsumman i programvaran innan paketet skickas till IPsec-lagret.

### <a name="tcp-port"></a>TCP-port     
En TCP-port är en logisk anslutningspunkt i TCP-protokollet. Det finns 65 535 giltiga portar i TCP-komponenten i NetX Duo, från 1 till 0xFFFF. Till skillnad från UDP där data från en port kan skickas till en annan målport, ansluts en TCP-port till en annan specifik TCP-port, och endast när den här anslutningen upprättas kan dataöverföring ske– och endast mellan de två portarna som upprättar anslutningen.

> [!IMPORTANT]
> TCP-portarna är helt åtskilda från *UDP-portar. UDP-portnummer 1 har t.ex. ingen relation till TCP-portnummer 1.*

### <a name="client-server-model"></a>Client-Server modell     
Om du vill använda TCP för dataöverföring måste en anslutning först upprättas mellan de två TCP-socketarna. Anslutningen upprättas på klient-server-sätt. Klientsidan av anslutningen är den sida som initierar anslutningen, medan serversidan bara väntar på klientanslutningsbegäranden innan någon bearbetning är klar.

> [!IMPORTANT]
> För multihome-enheter avgör NetX Duo automatiskt källadressen som ska användas för anslutningen och nexthop-adressen baserat på anslutningens *mål-IP-adress. Eftersom TCP är begränsat till att skicka paket till unicast-måladresser (t.ex. icke-broadcast) kräver NetX Duo ingen "ledtråd" för att välja käll-IPv6-adressen*.

### <a name="tcp-socket-state-machine"></a>TCP Socket State Machine      
Anslutningen mellan två TCP-sockets (en klient och en server) är komplex och hanteras på ett tillståndsdator. Varje TCP-socket startar i stängt tillstånd. Via anslutningshändelser migreras varje sockets tillståndsdator till TILLSTÅNDET ETABLERAD, där den största delen av dataöverföringen sker i TCP. När en sida av anslutningen inte längre vill skicka data kopplas den från. När den andra sidan kopplas från återgår TCP-socketen till tillståndet STÄNGD. Den här processen upprepas varje gång en TCP-klient och server upprättar och stänger en anslutning. Bild 14 visar de olika tillstånden för TCP-tillståndsdatorn.

### <a name="tcp-client-connection"></a>TCP-klientanslutning       
Som tidigare nämnts initierar klientsidan av TCP-anslutningen en anslutningsbegäran till en TCP-server. Innan en anslutningsbegäran kan göras måste TCP aktiveras på klientens IP-instans. Dessutom måste klientens TCP-socket skapas med tjänsten ***nx_tcp_socket_create** _ och bindas till en port via tjänsten _ *_nx_tcp_client_socket_bind_** .

När klientsocketen har bindas ***används nxd_tcp_client_socket_connect*** för att upprätta en anslutning till en TCP-server. Observera att socketen måste vara i tillståndet STÄNGD för att initiera ett anslutningsförsök. Upprättandet av anslutningen börjar med att NetX Duo utfärdar ett SYN-paket och väntar sedan på ett SYN ACK-paket tillbaka från servern, vilket innebär godkännande av anslutningsbegäran. När SYN ACK har tagits emot svarar NetX Duo med ett ACK-paket och befordrar klientsocketen till tillståndet ESTABLISHED.

![Diagram över tillstånden för TCP-tillståndsdatorn.](./media/user-guide/image24.png)   

**BILD 14. Tillstånd för TCP-tillståndsdatorn**


> [!WARNING]
> *Program bör använda **nxd_tcp_client_socket_connect Antingen** IPv4- och IPv6 TCP-anslutningar. Program kan fortfarande **använda nx_tcp_client_socket_connect** IPv4 TCP-anslutningar, men utvecklare uppmuntras att  använda **nxd_tcp_client_socket_connect*** eftersom nx_tcp_client_socket_connect kommer att bli inaktuella.

*På samma sätt **nxd_tcp_socket_peer_info_get** antingen med IPv4- eller IPv6 TCP-anslutningar. Men **nx_tcp_socket_peer_info_get** fortfarande tillgänglig för äldre program. Utvecklare uppmanas att använda **nxd_tcp_socket_peer_info_get** i framtiden.*

### <a name="tcp-client-disconnection"></a>TCP-klient frånkoppling    
Du stänger anslutningen genom att anropa ***nx_tcp_socket_disconnect***. Om ingen spärr har angetts skickar klientsocketen ett RST-paket till serversocketen och placerar socketen i tillståndet STÄNGD. Om en instängning begärs utförs annars det fullständiga TCP-frånkopplingsprotokollet enligt följande: 

- Om servern tidigare initierade en frånkopplingsbegäran (klientsocketen redan har tagit emot ett FIN-paket, svarat med en ACK och är i TILLSTÅNDET STÄNG VÄNTA), befordrar NetX Duo klientens TCP-sockettillstånd till LAST ACK-tillstånd och skickar ett FIN-paket. Den väntar sedan på en ACK från servern innan frånkopplingen slutförs och förs in i tillståndet STÄNGD.

- Om klienten å andra sidan är den första som initierar en frånkopplingsbegäran (servern har inte kopplats från och socketen fortfarande är i etablerat tillstånd), skickar NetX Duo ett FIN-paket för att initiera frånkopplingen och väntar på att få en FIN och en ACK från servern innan anslutningen slutförs och socketen placeras i stängt tillstånd.

Om det fortfarande finns paket i kön för socket-överföring pausar NetX Duo för den angivna tidsgränsen så att paketen kan bekräftas. Om tidsgränsen går ut tömmer NetX Duo överföringskön för klientsocketen. 

För att ta bort bindningen av porten från klientsocketen anropar programmet ***nx_tcp_client_socket_unbind***. Socketen måste vara i tillståndet STÄNGD eller så måste den kopplas från (t.ex. ETT TIMED WAIT-tillstånd) innan porten släpps. Annars returneras ett fel.

Slutligen, om programmet inte längre behöver klientsocketen anropas ***nx_tcp_socket_delete*** att ta bort socketen.

### <a name="tcp-server-connection"></a>TCP-serveranslutning      
Serversidan av en TCP-anslutning är passiv; Servern väntar alltså på att en klient ska initiera anslutningsbegäran. Om du vill acceptera en klientanslutning måste TCP först aktiveras på IP-instansen genom att anropa tjänsten ***nx_tcp_enable** _. Därefter måste programmet skapa en TCP-socket med hjälp av tjänsten _ *_nx_tcp_socket_create_** .  

Serversocketen måste också konfigureras för att lyssna efter anslutningsbegäranden. Detta uppnås med  hjälp av nx_tcp_server_socket_listen tjänsten. Den här tjänsten placerar serversocketen i LISTEN-tillstånd och binder den angivna serverporten till socketen.

> [!NOTE] 
> *Om du vill ange en socket listen callback-rutin anger programmet lämplig återanropsfunktion för tcp_listen_callback för **nx_tcp_server_socket_listen tjänsten.** Den här återanropsfunktionen för programmet körs sedan av NetX Duo när en ny anslutning begärs på den här serverporten. Bearbetningen i motringning är under programkontroll.*

För att godkänna klientanslutningsbegäranden anropar programmet tjänsten ***nx_tcp_server_socket_accept** _ . Serversocketen måste antingen ha statusEN LISTEN eller SYN RECEIVED (dvs. servern är i LISTEN-tillstånd och har tagit emot ett SYN-paket från en klient som begär en anslutning) för att anropa accepttjänsten. En lyckad returstatus från _ *_nx_tcp_server_socket_accept_** anger att anslutningen har ställts in och serversocketen är i tillståndet ESTABLISHED.

När serversocketen har en giltig anslutning köas ytterligare klientanslutningsbegäranden upp till det djup som *anges av listen_queue_size och* skickas till  * **nx_tcp_server_socket_listen** _-tjänsten. För att kunna bearbeta efterföljande anslutningar på en serverport måste programmet anropa _ *_nx_tcp_server_socket_relisten_** med en tillgänglig socket (d.v.s. en socket i tillståndet STÄNGD). Observera att samma serversocket kan användas om den tidigare anslutningen som är associerad med socketen nu är klar och socketen är i tillståndet STÄNGD.

### <a name="tcp-server-disconnection"></a>TCP-server frånkoppling     
Du stänger anslutningen genom att anropa ***nx_tcp_socket_disconnect***. Om ingen spärr har angetts skickar serversocketen ett RST-paket till klientsocketen och placerar socketen i tillståndet STÄNGD. Om en instängning begärs utförs annars det fullständiga TCP-frånkopplingsprotokollet enligt följande:

- Om klienten tidigare initierade en frånkopplingsbegäran (serversocketen redan har tagit emot ett FIN-paket, svarat med en ACK och är i TILLSTÅNDET STÄNG VÄNTETID), höjer NetX Duo TCP-sockettillståndet till LAST ACK-tillstånd och skickar ett FIN-paket. Den väntar sedan på en ACK från klienten innan frånkopplingen slutförs och förs in i tillståndet STÄNGD.

- Om servern å andra sidan är den första som initierar en frånkopplingsbegäran (klienten har inte kopplats från och socketen fortfarande är i etablerat tillstånd), skickar NetX Duo ett FIN-paket för att initiera frånkopplingen och väntar på att få en FIN och en ACK från klienten innan du slutför frånkopplingen och placerar socketen i stängt tillstånd.

Om det fortfarande finns paket i socket överföringskön, pausar NetX Duo för den angivna tidsgränsen för att tillåta att dessa paket bekräftas. Om tidsgränsen går ut rensar NetX Duo överföringskön för serversocketen.

När frånkopplingen har slutförts och serversocketen är i stängt tillstånd måste programmet anropa tjänsten ***nx_tcp_server_socket_unaccept** _ för att avsluta associationen mellan den här socketen och serverporten. Observera att den här tjänsten måste anropas av programmet även _*_om nx_tcp_socket_disconnect_*_ eller _*_nx_tcp_server_socket_accept returnerar_*_ en felstatus. När _*_nx_tcp_server_socket_unaccept_*_ returneras kan socketen användas som klient- eller serversocket, eller till och med tas bort om den inte längre behövs. Om du vill acceptera en annan klientanslutning på samma serverport ska tjänsten _ *_nx_tcp_server_socket_relisten_** anropas på den här socketen.

Följande kodsegment illustrerar sekvensen med anrop som en typisk TCP-server använder:

```c
/* Set up a previously created TCP socket to
   listen on port 12 */
nx_tcp_server_socket_listen()

/* Loop to make a (another) connection. */
while(1)
{
    /* Wait for a client socket connection request
       for 100 ticks. */
    nx_tcp_server_socket_accept();

    /* (Send and receive TCP messages with the TCP
       client) */

    /* Disconnect the server socket. */
    nx_tcp_socket_disconnect();

    /* Remove this server socket from listening on
       the port. */
    nx_tcp_server_socket_unaccept(&server_socket);
    /* Set up server socket to relisten on the
       same port for the next client. */
    nx_tcp_server_socket_relisten();
}
```

### <a name="mss-validation"></a>MSS-validering      
Maximal segmentstorlek (MSS) är den maximala mängden byte som en TCP-värd kan ta emot utan att fragmenteras av det underliggande IP-lagret. Under fasen för etablering av TCP-anslutning utbyter båda ändar sitt eget TCP MSS-värde, så att avsändaren inte skickar ett TCP-datasegment som är större än mottagarens MSS. NetX Duo TCP-modulen kan validera peer-peerns annonserade MSS-värde innan en anslutning upprättas. Som standard aktiverar NetX Duo inte en sådan kontroll. Program som vill utföra MSS-validering ska definiera ***NX_ENABLE_TCP_MSS_CHECK** _ när netX Duo-biblioteket byggs, och minimivärdet ska definieras _*_i NX_TCP_MSS_MINIMUM_*_. Inkommande TCP-anslutningar med *_MSS-värden nedan _ NX_TCP_MSS_MINIMUM_** tas bort.

### <a name="stop-listening-on-a-server-port"></a>Sluta lyssna på en serverport    
Om programmet inte längre vill lyssna efter klientanslutningsbegäranden på en serverport som tidigare angavs av ett anrop till tjänsten ***nx_tcp_server_socket_listen** _ anropar programmet helt enkelt tjänsten _ *_nx_tcp_server_socket_unlisten_** . Den här tjänsten placerar alla socketar som väntar på en anslutning tillbaka i stängt tillstånd och släpper eventuella paket för klientanslutningsbegäran i kö. 

### <a name="tcp-window-size"></a>TCP-fönsterstorlek   
Under både konfigurations- och dataöverföringsfaserna för anslutningen rapporterar varje port mängden data som den kan hantera, vilket kallas dess fönsterstorlek. När data tas emot och bearbetas justeras fönsterstorleken dynamiskt. I TCP kan en avsändare bara skicka en mängd data som passar in i mottagarens fönster. I princip ger fönsterstorleken flödeskontroll för dataöverföring i varje riktning av anslutningen.   

### <a name="tcp-packet-send"></a>TCP-paket som skickas     
Det är enkelt att skicka TCP-data genom att ***anropa nx_tcp_socket_send-funktionen.*** Om storleken på de data som överförs är större än MSS-värdet för socketen eller den aktuella peer-mottagningsfönstret, beroende på vilket som är mindre, tar TCP intern logik bort de data som passar min (MSS, peer receive Window) för överföring. Den här tjänsten skapar sedan ett TCP-huvud framför paketet (inklusive beräkningen av kontrollsumma). Om mottagarens fönsterstorlek inte är noll skickar anroparen så mycket data som möjligt för att fylla mottagarfönstrets storlek. Om mottagningsfönstret blir noll kan anroparen pausa och vänta tills mottagarens fönsterstorlek ökar tillräckligt för att paketet ska skickas. Vid en given tidpunkt kan flera trådar pausas vid försök att skicka data via samma socket. 

> [!WARNING]  
> *TCP-data som finns i NX_PACKET struktur bör finnas på en lång ord-gräns. Dessutom måste det finnas tillräckligt med utrymme mellan prepend-pekaren* och datastartspekaren för att placera TCP-, IP- och fysiska mediehuvuden .

### <a name="tcp-packet-retransmit"></a>TCP-paket som skickas igen      
Tidigare skickade TCP-paket som faktiskt har skickats lagras internt tills ett ACK returneras från den andra sidan av anslutningen. Om överförda data inte bekräftas inom tidsgränsen skickas det lagrade paketet på ny gång och nästa tidsgräns anges. När ett ACK tas emot släpps slutligen alla paket som omfattas av bekräftelsenumret i den interna överföringskön.  

> [!WARNING]   
> Programmet får inte återanvända paketet eller ändra innehållet i paketet när *nx_tcp_socket_send() returneras med NX_SUCCESS. Det överförda paketet släpps så småningom av intern NetX Duo-bearbetning när data har bekräftats av den andra änden*.

### <a name="tcp-keepalive"></a>TCP Keepalive     
Tcp Keepalive-funktionen gör att en socket kan identifiera om peer-anslutningen kopplas från utan korrekt avslutning (till exempel om peer-datorn kraschade) eller för att förhindra att vissa nätverksövervakningsaktiviteter avbryter en anslutning under långa perioder av inaktivitet. TCP Keepalive fungerar genom att regelbundet skicka en TCP-ram utan data och sekvensnumret är inställt på ett mindre än det aktuella sekvensnumret. Vid mottagning av en sådan TCP Keepalive-ram svarar mottagaren, om den fortfarande är vid liv, med ett ACK för det aktuella sekvensnumret. Detta slutför keepalive-transaktionen.  

Keepalive-funktionen är inte aktiverad som standard. Om du vill använda den här funktionen måste NetX Duo-biblioteket byggas med ***NX_ENABLE_TCP_KEEPALIVE** _ definierat. Symbolen _ *_NX_TCP_KEEPALIVE_INITIAL_** anger antalet sekunder av inaktivitet innan keepalive-ramen initieras.  

### <a name="tcp-packet-receive"></a>TCP-paket ta emot   
TCP-mottagningspaketbearbetningen (anropas från IP-hjälptråden) ansvarar för att hantera olika åtgärder för anslutning och frånkoppling samt överföring av bekräftelsebearbetning. Dessutom ansvarar TCP-mottagningspaketbearbetningen för att placera paket med mottagningsdata på lämplig TCP-sockets mottagningskö eller leverera paketet till den första pausade tråden som väntar på ett paket.

### <a name="tcp-receive-notify"></a>TCP-meddelande om mottagning     
Om programtråden behöver bearbeta mottagna data från mer än en socket, ***nx_tcp_socket_receive_notify-funktionen*** användas. Den här funktionen registrerar en återanropsfunktion för mottagningspaket för socketen. När ett paket tas emot på socketen körs återanropsfunktionen.  

Innehållet i återanropsfunktionen är programspecifikt. Funktionen skulle dock med största sannolikhet innehålla logik för att informera bearbetningstråden om att ett paket är tillgängligt på motsvarande socket. 

### <a name="thread-suspension"></a>Trådavstängning      
Som tidigare nämnts kan programtrådar pausa vid försök att ta emot data från en viss TCP-port. När ett paket tas emot på den porten ges det till den första tråden som pausas och tråden återupptas sedan. En valfri tidsgräns är tillgänglig när du pausar på ett TCP-mottagningspaket, en funktion som är tillgänglig för de flesta NetX Duo-tjänster.  

Trådavstängning är också tillgängligt för anslutning (både klient och server), klientbindning och frånkopplingstjänster.  

### <a name="tcp-socket-statistics-and-errors"></a>Statistik och fel för TCP-socket     
Om den är aktiverad håller NetX Duo TCP-socketprogrammet reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik- och felrapporter underhålls för varje IP/TCP-instans:   

- Totalt antal TCP-paket som skickats  
- Totalt antal TCP-byte som skickats  
- Totalt antal mottagna TCP-paket   
- Totalt antal mottagna TCP-byte   
- Totalt antal ogiltiga TCP-paket   
- Totalt antal bort ignorerade TCP-mottagningspaket    
- Totalt antal tcp-mottagningsfel för kontrollsumma   
- Totalt antal TCP-anslutningar   
- Totalt antal TCP-frånkopplingar   
- Totalt antal TCP-anslutningar som har tagits bort    
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

### <a name="tcp-socket-control-block-nx_tcp_socket"></a>TCP Socket Control Block NX_TCP_SOCKET      
Egenskaperna för varje TCP-socket finns i det associerade NX_TCP_SOCKET-kontrollblocket, som innehåller användbar information, till exempel länken till IP-datastrukturen, gränssnittet för nätverksanslutning, den bundna porten och kön för att ta emot paket.  Den här strukturen definieras i ***nx_api.h-filen.***