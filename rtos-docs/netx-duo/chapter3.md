---
title: Kapitel 3 – funktionella komponenter i Azure återställnings tider NetX Duo
description: Det här kapitlet innehåller en beskrivning av den högpresterande Azure återställnings tider NetX Duo TCP/IP-stacken från ett funktionellt perspektiv.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 07e51643c828afc8e6c0b968e78380316e84ccd7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826211"
---
# <a name="chapter-3---functional-components-of-azure-rtos-netx-duo"></a>Kapitel 3 – funktionella komponenter i Azure återställnings tider NetX Duo

Det här kapitlet innehåller en beskrivning av den högpresterande Azure återställnings tider NetX Duo TCP/IP-stacken från ett funktionellt perspektiv. 

## <a name="execution-overview"></a>Översikt över körning

Det finns fem typer av program körningar i ett NetX Duo-program: initiering, program gränssnitts anrop, intern IP-tråd, periodiska timers och nätverks driv rutinen.

> [!NOTE]
> *NetX Duo förutsätter att det finns ThreadX och beror på dess tråd körning, upphängning, periodiska timers och ömsesidiga undantags funktioner.*

### <a name="initialization"></a>Initiering

Tjänsten ***nx_system_initialize** _ måste anropas innan någon annan netx Duo-tjänst anropas. System initiering kan anropas antingen från ThreadX _ *_tx_application_define_** Function eller from Application threads.

Efter ***nx_system_initialize** _ returnerar, är systemet redo att skapa paket pooler och IP-instanser. Eftersom det krävs en standardpool för att skapa en IP-instans måste minst en NetX Duo-paket finnas innan du skapar en IP-instans. Det går att skapa paket pooler och IP-instanser från initierings funktionen ThreadX _ *_tx_application_define_** och från program trådar.

Internt skapas en IP-instans i två delar: den första delen görs inom kontexten för anroparen, antingen från ***tx_application_define*** eller från en program tråds kontext. Detta innefattar att konfigurera IP-datastrukturen och skapa olika IP-resurser, inklusive den interna IP-tråden. Den andra delen utförs vid den första körningen från den interna IP-tråden. Det är här som nätverks driv rutinen, som angavs under den första delen av IP-skapandet, först anropas. Genom att anropa nätverks driv rutinen från den interna IP-tråden kan driv rutinen utföra I/O och pausa under initierings bearbetningen.

När nätverks driv rutinen återgår från initierings processen slutförs IP-skapandet.

Initiering av IPv6 i NetX Duo kräver ytterligare NetX Duo-tjänster. Dessa beskrivs mer detaljerat i avsnittet [IPv6 i netx Duo](#ipv6-in-netx-duo) senare i det här kapitlet.

> [!NOTE]
> *NetX Duo-tjänsten **nx_ip_status_check** finns tillgänglig för att hämta information om IP-instansen och dess primära gränssnitts status. Sådan statusinformation innehåller om länken är initierad, aktive rad och IP-adressen är löst. Den här informationen används för att synkronisera program trådar som behöver använda en nyligen skapad IP-instans. För multihome-system, se [stöd för multihome](#multihome-support). **nx_ip_interface_status_check** finns tillgängligt för att hämta 3information på det angivna gränssnittet.*

### <a name="application-interface-calls"></a>Program gränssnitts anrop

Anrop från programmet görs i stort sett från program trådar som körs under ThreadX-återställnings tider. Vissa initierings-, Create-och enable-tjänster kan dock anropas från ***tx_application_define***. I avsnitten "tillåtet från" i [kapitel 4 – Beskrivning av Azure återställnings tider netx Duo-tjänsterna](chapter4.md) anges från vilka varje netx Duo-tjänst kan anropas.

För det mesta görs bearbetningen av intensiva aktiviteter, till exempel beräknings kontroll summor i den anropande trådens kontext, utan att blockera åtkomsten till andra trådar till IP-instansen. Vid överföring utförs exempelvis beräkningen av UDP-kontrollsumma i ***nx_udp_socket_send** _-tjänsten innan den underliggande IP-Send-funktionen anropas. På ett mottaget paket beräknas UDP-kontrollsummaet i mappen _ *_nx_udp_socket_receive_** som körs i program tråden. Detta bidrar till att förhindra att nätverks begär Anden med högre prioritet kan stoppas på grund av bearbetning av intensiv beräkning av kontroll summa i trådar med lägre prioritet.

Värden, till exempel IP-adresser och port nummer, skickas till API: er i värdens byte ordning. Internt lagras dessa värden i värdens byte-ordning. På så sätt kan utvecklare enkelt visa värdena via en fel sökare. När dessa värden är programmerade i en ram för överföring, konverteras de till byte ordning för nätverk.

### <a name="internal-ip-thread"></a>Intern IP-tråd

Som nämnts har varje IP-instans i NetX Duo en egen tråd. Prioriteten och stack storleken för den interna IP-tråden definieras i ***nx_ip_creates*** tjänsten. Den interna IP-tråden skapas i ett läge som är klart att köras. Om IP-tråden har högre prioritet än den anropande tråden kan avstängningen uppstå i IP-Create-anropet.

Start punkten för den interna IP-tråden är i den interna funktionen _ ***nx_ip_thread_entry***. När den interna IP-tråden startas slutförs först nätverks driv Rutinens initiering, som består av tre anrop till den programspecifika nätverks driv rutinen. Det första anropet är att koppla nätverks driv rutinen till IP-instansen, följt av ett initierings anrop, vilket gör att nätverks driv rutinen kan gå igenom initierings processen. När nätverks driv rutinen har returnerat från initieringen (den kan stoppas under väntan på att maskin varan ska konfigureras korrekt), anropar den interna IP-tråden nätverks driv rutinen igen för att aktivera länken. När nätverks driv rutinen har returnerat från länken Aktivera anrop, anger den interna IP-tråden en oändlig loop-kontroll för olika händelser som behöver bearbetas för den här IP-instansen. Händelser som bearbetas i den här slingan är inskjuten mottagning av IP-paket, sammansättning av IP-paket, ICMP-Ping-bearbetning, IGMP-bearbetning, bearbetning av TCP-paketfiltrering, TCP-periodisk bearbetning, timeout för IP-fragment och IGMP-periodisk bearbetning. Händelser omfattar även adress matchnings aktiviteter. Bearbetning av ARP-paket och regelbunden ARP-bearbetning i IPv4, dubblettidentifiering, router-inbjudningar och identifiering av grannar i IPv6.

> [!CAUTION]
> *NetX Duo-callback-funktionerna, inklusive lyssnings-och från kopplings-motanrop, anropas från den interna IP-tråden, inte den ursprungliga anropande tråden. Programmet måste ta hand om att inte pausa i någon NetX Duo-callback-funktion.*

### <a name="ip-periodic-timers"></a>Periodiska timers för IP

Det finns två ThreadX-periodiska timers som används för varje IP-instans. Den första är en eng-Second-timer för ARP, IGMP, TCP-tidsgräns och den också bearbetar ommonteringen av IP-fragment. Den andra timern är en 100 MS-timer för att köra timeout för TCP-överföring och IPv6-relaterade åtgärder.

### <a name="network-driver"></a>Nätverks driv rutin

Varje IP-instans i NetX Duo har ett primärt gränssnitt som identifieras av den driv rutin som anges i ***nx_ip_creates*** tjänsten. Nätverks driv rutinen ansvarar för hantering av olika NetX Duo-begäranden, inklusive paket överföring, paket mottagning och förfrågningar om status och kontroll. 

För ett multi-Home-system har IP-instansen flera gränssnitt, var och en med en associerad nätverks driv rutin som utför dessa uppgifter för respektive gränssnitt.

Nätverks driv rutinen måste också hantera asynkrona händelser som inträffar på mediet. Asynkrona händelser från mediet omfattar paket mottagning, slut för ande av paket överföring och status ändringar. NetX Duo tillhandahåller nätverks driv rutinen med flera åtkomst funktioner för att hantera olika händelser. Dessa funktioner är utformade för att anropas från Interrupt Service Routine delen av nätverks driv rutinen. För IPv4-nätverk bör nätverks driv rutinen vidarebefordra alla ARP-paket som tas emot till den ***_nx_arp_packet_deferred_receive*** interna funktionen. Alla RARP-paket ska vidarebefordras till ***_nx_rarp_packet_deferred_receive** _ intern funktion. Det finns två alternativ för IP-paket. Om snabb sändning av IP-paket krävs ska inkommande IP-paket vidarebefordras till _ *_ _nx_ip_packet_receive_* _ för omedelbar bearbetning. Detta förbättrar prestandan för NetX Duo i hantering av IP-paket. Annars bör vidarebefordrande IP-paket till _ *_ _nx_ip_packet_deferred_receive_** göras. Den här tjänsten placerar IP-paketet i den uppskjutna bearbetnings kön där den hanteras av den interna IP-tråden, vilket resulterar i minst mängden ISR-bearbetnings tid.

Nätverks driv rutinen kan också skjuta upp avbrott-bearbetningen så att den inte går att använda i kontexten för IP-tråden. I det här läget måste ISR Spara nödvändig information, anropa den interna funktionen ***_nx_ip_driver_deferred_processing*** och bekräfta avbrotts styrenheten. Den här tjänsten meddelar IP-tråden att schemalägga ett återanrop till enhets driv rutinen för att slutföra processen för händelsen som orsakar avbrottet.

Vissa nätverks styrenheter kan utföra beräkning och validering av kontroll summa för TCP/IP-huvud i maskin vara, utan att ta upp värdefulla processor resurser. För att kunna dra nytta av funktionen för maskin varu kapacitet tillhandahåller NetX Duo alternativ för att aktivera eller inaktivera olika beräkningar av program varu kontroll vid kompilering, samt för att aktivera eller inaktivera beräkning av kontroll Summa vid körning, om enhetens driv rutin kan kommunicera med IP-lagret om är maskin varu funktioner. Mer detaljerad information om hur du skriver NetX Duo [-återställnings tider finns i kapitel 5 – Azure netx Duo-nätverks driv rutiner](chapter5.md) .

### <a name="multihome-support"></a>Support för multihome

NetX Duo stöder system som är anslutna till flera fysiska enheter som använder en enda IP-instans. Varje fysiskt gränssnitt tilldelas ett gränssnitts kontroll block i IP-instansen. Program som vill använda ett hem system måste definiera värdet för ***NX_MAX_PHSYCIAL_INTERFACES** _ till antalet fysiska enheter som är anslutna till systemet och återskapa netx Duo-biblioteket. Som standard är _ *_NX_MAX_PHYSICAL_INTERFACES_** inställt på ett, vilket skapar ett gränssnitts kontroll block i IP-instansen.

NetX Duo-programmet skapar en enda IP-instans för den primära enheten med hjälp av tjänsten ***nx_ip_create** _. För varje ytterligare nätverks enheter ansluter programmet enheten till IP-instansen med hjälp av tjänsten _ *_nx_ip_interface_attach_**.

Varje nätverks gränssnitts struktur innehåller en delmängd av nätverksinformation om nätverks gränssnittet som finns i kontroll blocket för IP, inklusive gränssnitts-IPv4-adress, nätmask, IP-MTU-storlek och adress information för MAC-lager.

> [!NOTE]
> *NetX Duo med stöd för multihome är bakåtkompatibel med tidigare versioner av NetX Duo. Tjänster som inte har uttryckligen gränssnitts information som standard till den primära nätverks enheten.*

Det primära gränssnittet har index noll i listan över IP-instanser. Varje efterföljande enhet som är kopplad till IP-instansen tilldelas nästa index.

Alla de övre skikt protokoll tjänsterna för vilka IP-instansen är aktive rad, inklusive TCP, UDP, ICMP och IGMP, är tillgängliga för alla anslutna enheter.

I de flesta fall kan NetX Duo avgöra den bästa käll adressen som ska användas vid överföring av ett paket. Käll adress valet baseras på mål adressen. NetX Duo-tjänster läggs till för att tillåta att program anger en speciell käll adress som ska användas, i de fall där den lämpligaste orsaken inte kan fastställas av mål adressen. Ett exempel skulle finnas i ett hem system, ett program måste skicka ett paket till en IPv4-broadcast eller multicast-mål adresser.

Tjänster som är specifika för att utveckla program med fler Hem nätverk är följande:

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

Dessa tjänster förklaras mer detaljerat i [beskrivningen av netx Duo-tjänster](chapter4.md).

### <a name="loopback-interface"></a>Loopback-gränssnitt

Loopback-gränssnittet är ett särskilt nätverks gränssnitt utan en fysisk länk som är kopplad till. Loopback-gränssnittet gör att program kan kommunicera med IPv4 loopback-adressen 127.0.0.1 för att använda ett logiskt loopback-gränssnitt, se till att det konfigurerbara alternativet ***NX_DISABLE_LOOPBACK_INTERFACE*** inte har angetts.

### <a name="interface-control-blocks"></a>Gränssnitts kontroll block

Antalet gränssnitts kontroll block i IP-instansen är antalet fysiska gränssnitt (definieras med ***NX_MAX_PHYSICAL_INTERFACES** _) plus loopback-gränssnittet om det är aktiverat. Det totala antalet gränssnitt definieras i _ *_NX_MAX_IP_INTERFACES_* *.

## <a name="protocol-layering"></a>Protokoll skikt

TCP/IP som implementeras av NetX Duo är ett lager protokoll, vilket innebär att mer komplexa protokoll skapas ovanpå enklare underliggande protokoll. I TCP/IP finns det lägsta skikt protokollet på *länk nivån* och hanteras av nätverks driv rutinen. Den här nivån är normalt riktad mot Ethernet, men det kan också vara fiber, seriellt eller praktiskt taget valfritt fysiskt medium.

Ovanpå länk skiktet finns *nätverks skiktet*. I TCP/IP är detta IP-adressen, som i princip ansvarar för att skicka och ta emot enkla paket – på bästa möjliga sätt – över nätverket. Hanterings typ protokoll som ICMP och IGMP kategoriseras vanligt vis som nätverks lager, även om de förlitar sig på IP för att skicka och ta emot.

*Transport lagret* vilar ovanpå nätverks nivån. Det här lagret ansvarar för att hantera data flödet mellan värdar i nätverket. Det finns två typer av transport tjänster som stöds av NetX Duo: UDP och TCP. UDP-tjänsterna ger dig bästa möjliga sändning och mottagning av data mellan två värdar på ett anslutnings effektivt sätt, medan TCP tillhandahåller Reliable anslutningsorienterade tjänster mellan två värd enheter.

Skiktning visas i de faktiska nätverks data paketen. Varje lager i TCP/IP innehåller ett block med information som kallas rubrik. Den här metoden för omgivande data (och eventuellt protokoll information) med en rubrik kallas vanligt vis för data inkapsling. Bild 1 visar ett exempel på NetX Duo-lager och bild 2 visar den resulterande data inkapslingen för UDP-data som skickas.

![Protokoll skikt](./media/user-guide/image12.jpg)

**BILD 1. Protokoll skikt**

## <a name="packet-pools"></a>Paket pooler

Att allokera paket på ett snabbt och entydigt sätt är alltid en utmaning i real tids nätverks program. Med detta i åtanke ger NetX Duo möjlighet att skapa och hantera flera pooler med nätverks paket med fast storlek.

Eftersom NetX Duo-paket består av minnes block med fast storlek, finns det aldrig några interna fragmenterings problem. Fragmenteringen orsakar naturligtvis att beteendet är icke deterministiskt. Dessutom är tiden som krävs för att allokera och frigöra ett NetX Duo-paket med en enkel hantering av länkade listor. Paket tilldelningen och avallokeringen görs dessutom på huvud sidan i listan över tillgängliga. Detta ger snabbast möjlig länkad List bearbetning.

![UDP-inkapsling](./media/user-guide/image13.png)

**BILD 2. UDP-inkapsling**

Brist på flexibilitet är vanligt vis den huvudsakliga nack delen med paket med fast storlek. Att fastställa den optimala paket nytto Last storleken som även hanterar det värsta inkommande paketet är en svår uppgift. NetX Duo-paketen löser det här problemet med en valfri funktion som kallas paket länkning. Ett faktiskt nätverks paket kan skapas för en eller flera NetX Duo-paket som länkas samman. Dessutom upprätthåller paket huvudet en pekare överst i paketet. När ytterligare protokoll läggs till flyttas den här pekaren bara baklänges och det nya sidhuvudet skrivs direkt framför data. Utan flexibel paket teknik skulle stacken behöva allokera en annan buffert och kopiera data till en ny buffert med det nya sidhuvudet, vilket är bearbetnings intensiv.

Eftersom varje paket nytto Last har åtgärd ATS för en viss modempool, kräver program data som är större än nytto Last storleken flera paket sammankopplade. När ett paket fylls med användar data, ska programmet använda tjänsten ***nx_packet_data_append***. Den här tjänsten flyttar program data till ett paket. I situationer där ett paket inte är tillräckligt för att lagra användar data allokeras ytterligare paket för att lagra användar data. Om du vill använda paket länkning måste driv rutinen kunna ta emot eller överföra från kedjade paket.

För inbäddade system som inte behöver använda funktionen paket länkning kan NetX Duo-biblioteket skapas med ***NX_DISABLE_PACKET_CHAIN** _ för att ta bort paket länknings logiken. Observera att funktionen för att komma åt IP-fragment och omsammansättning kan behöva använda funktionen för kedjade paket. Därför krävs _ *_NX_DISABLE_FRAGMENTATION_** även för att definiera _*_NX_DISABLE_PACKET_CHAIN_*_ . 

Varje NetX Duo Packet-pool är en offentlig resurs. NetX Duo placerar inga begränsningar för hur paket pooler används. 

### <a name="packet-pool-memory-area"></a>Minnes området för paket pool

Minnes området för Packet-poolen anges när den skapas. Precis som andra minnes områden för ThreadX-och NetX Duo-objekt kan det finnas var som helst i målets adress utrymme. 

Detta är en viktig funktion på grund av den stora flexibiliteten ger programmet. Anta till exempel att en kommunikations produkt har ett höghastighets minnes utrymme för nätverks buffertar. Det här minnes området används enkelt genom att göra det till en NetX Duo-paketets minnes uppsättning.

### <a name="creating-packet-pools"></a>Skapa paket pooler

Paket pooler skapas antingen under initieringen eller under körningen av program trådar. Det finns inga begränsningar för antalet paket minnes pooler i ett NetX Duo-program.

### <a name="dual-packet-pool"></a>Pool med dubbla paket

Normalt är nytto Last storleken för standardpoolen för IP-paket tillräckligt stor för att rymma ram storleken upp till nätverks gränssnittets MTU. Under normal drift måste IP-tråden skicka meddelanden som ARP, TCP-kontrollmeddelanden, IGMP-meddelanden och ICMPv6-meddelanden. Dessa meddelanden använder de paket som tilldelas från standard paketets pool i IP-instansen. På ett minnes begränsat system där mängden minne som är tillgängligt för Packet-poolen är begränsad, är det inte säkert att du använder en enda adresspool (med stor nytto Last storlek som matchar MTU-storleken). NetX Duo gör det möjligt för program att installera en tilläggs paket pool, där nytto Last storleken är mindre. När tilläggs paketets pool har installerats allokerar IP-hjälp-tråden paket från antingen standardpoolen eller tilläggs poolen, beroende på storleken på det meddelande som den överför. För en tilläggs paket pool kommer en nytto Last storlek på 200 byte att fungera med de flesta av de meddelanden som IP-hjälpens tråd överför.

Som standard har NetX Duo-biblioteket skapats utan att du behöver aktivera Dual Packet-pool. Om du vill aktivera funktionen skapar du biblioteket med ***NX_DUAL_PACKET_POOL_ENABLE** _ definierat. Sedan kan du ställa in tilläggs paketets pool genom att anropa _ *_nx_ip_auxiliary_packet_pool_set_* *.

Det finns också möjlighet att skapa fler än en modempool. Till exempel skapas en pool för överförings paket med optimal nytto Last storlek för förväntade meddelande storlekar. En Receive Packet-pool skapas i driv rutinen med en nytto Last storlek som är inställd på driv Rutinens MTU, eftersom det inte går att förutse storleken på mottagna paket.

### <a name="packet-header-nx_packet"></a>Paket huvud NX_PACKET   
Som standard placerar NetX Duo paket rubriken omedelbart före paketets nytto Last-sektion. Paketets minnes uppsättning är i princip en serie paket – huvuden som följs omedelbart av paketets nytto Last. Paket huvudet (***NX_PACKET***) och poolens layout visas i bild 3.

För nätverks enhets driv rutin som kan utföra kostnads kopierings åtgärder är vanligt vis start adressen för paketets nytto Last i DMA-logiken. Vissa DMA-motorer har justerings krav på nytto lasts ytan. Om du vill att start adressen för nytto lastområdet ska justeras korrekt för DMA-motorn eller cache-åtgärden kan användaren definiera symbol ***NX_PACKET_ALIGNMENT***.

> [!WARNING]
> *Det är viktigt att nätverks driv rutinen använder funktionen **nx_packet_transmit_release** när överföringen av ett paket har slutförts. Den här funktionen kontrollerar att paketet inte ingår i en kö för TCP-utdata innan den faktiskt placeras i den tillgängliga poolen.*

![Layout för paket huvud och adresspool](./media/user-guide/image14.jpg)

**BILD 3. Layout för paket huvud och adresspool**

Fälten i paket rubriken definieras enligt följande. Observera att den här tabellen inte är en omfattande lista över alla medlemmar i *NX_PACKETs* strukturen.

|Paket huvud | Syfte |
|---|---|
|***nx_packet_pool_owner***|Det här fältet pekar på den modempool som äger det aktuella paketet. När paketet släpps släpps det till den här poolen. Med poolen ägarskap i varje paket är det möjligt för ett datagram att spänna över flera paket från flera paket pooler.|
|***nx_packet_next** _|Det här fältet pekar på nästa paket inom samma ram. Om värdet är NULL finns det inga ytterligare paket som är en del av ramen. Det här fältet används också för att lagra fragmenterade paket tills hela paketet kan sammanställas igen. det tas bort om _ *_NX_DISABLE_PACKET_CHAIN_* * har definierats.|
|***nx_packet_last** _|Det här fältet pekar på det sista paketet i samma nätverks paket. Om värdet är NULL representerar det här paketet hela nätverks paketet. Det här fältet tas bort om _ *_NX_DISABLE_PACKET_CHAIN_* * har definierats.|
|***nx_packet_length** _| Det här fältet innehåller det totala antalet byte i hela nätverks paketet, inklusive summan av alla byte i alla paket som sammankopplas av _nx_packet_next *-medlemmen.|
|***nx_packet_ip_interface***| Det här fältet är gränssnitts kontroll blocket som tilldelas paketet när det tas emot av gränssnitts driv rutinen och av NetX Duo för utgående paket. Ett gränssnitts kontroll block beskriver gränssnittet, t. ex. nätverks adress, MAC-adress, IP-adress och gränssnitts status, till exempel länk aktiverat och fysisk mappning krävs.|
|***nx_packet_data_start** _| Det här fältet pekar på början av det fysiska nytto Last området för det här paketet. Det behöver inte omedelbart följa NX_PACKET huvud, men det är standardinställningen för tjänsten _ *_nx_packet_pool_create_**.|
|***nx_packet_data_end** _|Det här fältet pekar på slutet av det fysiska nytto Last området för det här paketet. Skillnaden mellan det här fältet och fältet _nx_packet_data_start * representerar nytto lastens storlek.|
|***nx_packet_prepend_ptr** _|Det här fältet pekar på platsen där paket data, antingen protokoll huvud eller faktiska data, läggs till framför befintliga paket data (om sådana finns) i paketets nytto Last område. Det måste vara större än eller lika med _nx_packet_data_start * pekare och mindre än eller lika med *nx_packet_append_ptrs* pekaren.|
> [!CAUTION]
> *Av prestanda skäl förutsätter NetX Duo att när paketet skickas till NetX Duo-tjänster för överföring, pekar lägga pekar på lång Word-justerad adress.*

|   |   |
|---|---|
|***nx_packet_append_ptr** _|Det här fältet pekar på slutet av de data som för närvarande finns i paketets nytto Last område. Det måste ligga mellan minnes platsen som _nx_packet_prepend_ptr * och *nx_packet_data_end.* Skillnaden mellan det här fältet och fältet *nx_packet_prepend_ptr* representerar mängden data i det här paketet.|
|***nx_packet_packet_pad** _|I det här fältet definieras längden på utfyllnad i 4 byte-ord för att uppnå det önskade justerings kravet. Det här fältet tas bort om _*_NX_PACKET_HEADER_PAD_*_ inte har definierats. Du kan också använda _*_NX_PACKET_ALIGNMENT_*_ i stället för att definiera _nx_packet_header_pad. *|

### <a name="packet-header-offsets"></a>Paket huvud förskjutningar

Paketets huvud storlek definieras för att tillåta tillräckligt med utrymme för att rymma rubrikens storlek. Tjänsten ***nx_packet_allocate*** används för att allokera ett paket och justerar lägga-pekaren i paketet enligt den typ av paket som angetts. Paket typen talar om för NetX Duo vilken förskjutning som krävs för att lägga till protokoll huvudet (till exempel UDP, TCP eller ICMP) framför protokoll data.

Följande typer definieras i NetX Duo för att ta hänsyn till IP-huvudet och det fysiska skiktet (Ethernet) i paketet. I det senare fallet antas det vara 16 byte som tar hänsyn till den nödvändiga justeringen av 4 byte. IPv4-paket definieras fortfarande i NetX Duo för program för att allokera paket för IPv4-nätverk. Observera att om NetX Duo-biblioteket har skapats med IPv6 aktiverat, mappas de generiska paket typerna (till exempel NX_IP_PACKET) till IPv6-versionen. Om NetX Duo-biblioteket har skapats utan IPv6 aktive rad, mappas dessa generiska paket typer till IPv4-versionen.

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

Observera att dessa värden kommer att ändras om *NX_IPSEC_ENABLE* har definierats. För program som använder IPsec finns mer information i användar handboken för NetX Duo IPsec.

### <a name="pool-capacity"></a>Pool-kapacitet

Antalet paket i en adresspool är en funktion i nytto lastens storlek och det totala antalet byte i minnes området som har angetts till Packet poolens Create-tjänst. Poolens kapacitet beräknas genom att du dividerar paket storleken (inklusive storleken på NX_PACKET huvud, nytto lastens storlek och rätt justering) till det totala antalet byte i det angivna minnes området.

### <a name="payload-area-alignment"></a>Justering av nytto Last områden

Skrivarpool i NetX Duo stöder noll-kopiering. På enhets driv rutins nivån kan driv rutinen tilldela nytto lastområdet direkt till buffertens beskrivningar för att ta emot data. Ibland måste DMA-motorn eller mekanismen för cachelagring kräva start adressen för nytto lastområdet för att få ett visst justerings krav. Detta kan uppnås genom att definiera det önskade justerings kravet (i byte) i ***NX_PACKET_ALIGNMENT***. När du skapar en adresspool, justeras start adressen för nytto Last ytan till det här värdet. Som standard är start adressen 4 byte justerad.

### <a name="thread-suspension"></a>Tråd upphängning

Program trådar kan pausas i väntan på ett paket från en tom pool. När ett paket returneras till poolen får den pausade tråden det här paketet och återupptas.

Om flera trådar har pausats på samma modempool, återupptas de i den ordning som de var pausade (FIFO).

### <a name="pool-statistics-and-errors"></a>Statistik och fel i pooler

Om den här inställningen är aktive rad håller NetX Duo Packet Management-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter underhålls för paketbaserade pooler:

- Totalt antal paket i poolen
- Lediga paket i poolen
- Totalt antal paket tilldelningar
- Pool tomma tilldelnings begär Anden
- Förskjutande av pool, tomma allokeringar
- Ogiltiga paket versioner

Alla dessa statistik-och fel rapporter, förutom det totala antalet och det lediga paket antalet i poolen, är inbyggda i NetX Duo-biblioteket om inte ***NX_DISABLE_PACKET_INFO** _ har definierats. Dessa data är tillgängliga för programmet med tjänsten _ *_nx_packet_pool_info_get_**.

### <a name="packet-pool-control-block-nx_packet_pool"></a>Kontroll block för Packet-pool NX_PACKET_POOL

Egenskaperna för varje paket minnes uppsättning finns i kontroll blocket. Den innehåller användbar information, till exempel den länkade listan över lediga paket, antalet lediga paket och nytto Last storleken för paket i den här poolen. Den här strukturen definieras i filen ***nx_api. h*** .

Du kan placera kontroll block var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

## <a name="ipv4-protocol"></a>IPv4-protokoll

Komponenten Internet Protocol (IP) i NetX Duo ansvarar för att skicka och ta emot IPv4-paket på Internet. I NetX Duo är det den komponent som slutligen ansvarar för att skicka och ta emot TCP-, UDP-, ICMP-och IGMP-meddelanden med hjälp av den underliggande nätverks driv rutinen.

NetX Duo stöder både IPv4-protokollet (RFC 791) och IPv6-protokollet (RFC 2460). I det här avsnittet beskrivs IPv4. IPv6 beskrivs i nästa avsnitt.

### <a name="ipv4-addresses"></a>IPv4-adresser

Varje värd på Internet har en unik 32-bitars identifierare som kallas för en IP-adress. Det finns fem klasser av IPv4-adresser enligt beskrivningen i bild 4. Intervallen för de fem IPv4-adress klasserna är följande:

|Klass|Intervall|
|---|---|
|A |0.0.0.0 till 127.255.255.255|
|B |128.0.0.0 till 191.255.255.255|
|C |192.0.0.0 till 223.255.255.255|
|D |224.0.0.0 till 239.255.255.255|
|E |240.0.0.0 till 247.255.255.255|

![Diagram över IPv4-adress strukturen.](./media/user-guide/ipv4-address-structure.png)

### <a name="figure-4-ipv4-address-structure"></a>BILD 4. IPv4-adress struktur

Det finns också tre typer av adress specifikationer: *unicast*, *broadcast* och *multicast*. Unicast-adresser är de IPv4-adresser som identifierar en speciell värd på Internet. Unicast-adresser kan antingen vara en källa eller en mål-IPv4-adress. En broadcast-adress identifierar alla värdar i ett särskilt nätverk eller under nätverk och kan bara användas som mål adresser. Broadcast-adresser anges genom att ha den värd-ID-del av adressen som anges till dem. Multicast-adresser (klass D) anger en dynamisk grupp värdar på Internet. Medlemmar i multicast-gruppen kan ansluta till och lämna när de vill.

> [!IMPORTANT]
> *Endast anslutnings bara protokoll som UDP över IPv4 kan använda broadcast och begränsad broadcast-kapacitet för multicast-gruppen.*

> [!IMPORTANT]
> * Makro *IP_ADDRESS* definieras i ***nx_api. h** _. Det möjliggör enkel specifikation av IPv4-adresser med kommatecken i stället för en punkt. Exempel: _IP_ADDRESS (128, 0, 0) * anger den första klass B-adressen som visas i bild 4. *

### <a name="ipv4-gateway-address"></a>IPv4-Gateway-adress

Nätverksgateway hjälper värdar i sina nätverk att vidarebefordra paket som är avsedda för destinationer utanför den lokala domänen. Varje nod har en viss kunskap om vilka nästa hopp som ska skickas till, antingen på målet en av dess grannar, eller genom en förprogrammerad statisk routningstabell. Men om dessa metoder inte fungerar bör noden vidarebefordra paketet till dess standardgateway som har bättre kunskap om hur paketet dirigeras till målet. Observera att standardgateway måste vara direkt tillgänglig via ett av de fysiska gränssnitt som är kopplade till IP-instansen. Programmet anropar ***nx_ip_gateway_address_set** _ för att konfigurera IPv4-standardgateway. Använd tjänst _*_nx_ip_gateway_address_get_*_ för att hämta de aktuella inställningarna för IPv4 Gateway. Programmet ska använda tjänsten _ *_nx_ip_gateway_address_clear_** för att rensa Gateway-inställningen.

### <a name="ipv4-header"></a>IPv4-sidhuvud

För att IPv4-paket ska kunna skickas på Internet måste det ha ett IPv4-huvud. När protokoll på högre nivå (UDP, TCP, ICMP eller IGMP) anropar IP-komponenten för att skicka ett paket, placerar modulen IPv4-överföring ett IPv4-huvud framför data. När IP-paket tas emot från nätverket tar IP-komponenten bort IPv4-huvudet från paketet innan det levereras till protokollen på högre nivå. Bild 5 visar formatet på IP-huvudet.

![Format för IPv4-sidhuvud](./media/user-guide/ipv4-header-format.png)

### <a name="figure-5-ipv4-header-format"></a>BILD 5. Format för IPv4-sidhuvud

> [!IMPORTANT]
> *Alla rubriker i TCP/IP-implementeringen förväntas vara i **big endian** format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen. Till exempel måste 4-bitars versionen och längden på 4-bitars huvudet för IP-huvudet finnas på den första byten i rubriken.*

Fälten i IPv4-rubriken definieras enligt följande:

|Fält för IPv4- &nbsp; huvud &nbsp; |Syfte |
|---|---|
|***4-bitars version*** |Det här fältet innehåller den version av IP som detta sidhuvud representerar. För IP version 4, som är det som NetX Duo stöder, är värdet för det här fältet 4. |
|***4-bitars rubrik längd*** |Det här fältet anger antalet 32-bitars ord i IP-huvudet. Om det inte finns några alternativ ord är värdet för det här fältet 5. |
|***8-bitars typ av tjänst (TOS)*** |I det här fältet anges vilken typ av tjänst som begärs för det här IP-paketet. Giltiga begär Anden är följande:<br />-Normal: 0x00 <br />-Minsta fördröjning: 0x00<br />-Högsta data: 0x08<br />-Högsta tillförlitlighet: 0x04<br />-Lägsta kostnad: protokollnumret 0x02 |
|***16-bitars total längd*** |Det här fältet innehåller den totala längden för IP-datagram i byte, inklusive IP-huvudet. Ett IP-datagram är den grundläggande informations enheten som finns på ett TCP/IP-Internet. Den innehåller en mål-och käll adress förutom data. Eftersom det är ett 16-bitars fält är den maximala storleken för ett IP-datagram 65 535 byte.|
|***16-bitars identifiering*** |Fältet är ett tal som används för att unikt identifiera varje IP-datagram som skickas från en värd. Det här talet ökar ofta när ett IP-datagram har skickats. Det är särskilt användbart i att montera mottagna IP-paket.|
|***3-bitars flaggor*** |Det här fältet innehåller information om IP-fragment. Bit 14 är biten "ingen fragment". Om den här biten anges fragmenteras inte det utgående IP-datagrammet. Bit 13 är biten "fler fragment". Om den här biten anges finns det fler fragment. Om den här biten är klar är det sista fragmentet i IP-paketet.|
|***13-bitars fragment förskjutning*** |Det här fältet innehåller den övre 13 bitarna i fragment förskjutningen. Därför tillåts fragment förskjutningar bara på 8 byte-gränser. Det första fragmentet i ett fragmenterat IP-datagram kommer att ha biten "fler fragment" och ha en förskjutning på 0.|
|***8-bitars TTL-värde (Time to Live)*** |Det här fältet innehåller antalet routrar som det här datagrammet kan skicka, vilket i princip är det som begränsar datagrammets livstid.|
|***8-bitars protokoll***|Det här fältet anger vilket protokoll som använder IP-datagrammet. Följande är en lista över giltiga protokoll och deras värden:<br />-ICMP: 0x01 <br />-IGMP: protokollnumret 0x02<br />-TCP: 0X06<br />-UDP: 0X11 |
|***16-bitars kontroll Summa*** |Det här fältet innehåller 16-bitars kontroll summa som endast täcker IP-huvudet. Det finns ytterligare kontroll summor i protokoll på högre nivå som behandlar IP-nyttolasten. |
|***32-bitars käll-IP-adress*** |Det här fältet innehåller avsändarens IP-adress och är alltid en värd adress. |
|***32-bitars mål-IP-adress*** |Det här fältet innehåller mottagarens eller mottagarens IP-adress om adressen är en broadcast-eller multicast-adress. |

### <a name="creating-ip-instances"></a>Skapar IP-instanser

IP-instanser skapas antingen under initieringen eller under körningen av program trådar. Den första IPv4-adressen, nätverks masken, standardpoolen, medie driv rutinen och minnet och prioriteten för den interna IP-tråden definieras av den ***nx_ip_create*** tjänsten även om programmet endast avser att använda IPv6-nätverk. Om programmet initierar IP-instansen med IPv4-adressen inställt på en ogiltig adress (0.0.0.0), förutsätts att gränssnitts adressen kommer att lösas genom manuell konfiguration senare, via RARP eller via DHCP eller liknande protokoll.

För system med flera nätverks gränssnitt anges det primära gränssnittet vid anrop till ***nx_ip_create** _. Varje ytterligare gränssnitt kan kopplas till samma IP-instans genom att anropa _ *_nx_ip_interface_attach_* *. Den här tjänsten lagrar information om nätverks gränssnittet (till exempel IP-adress, nätverks mask) i gränssnitts kontroll blocket och kopplar driv rutins instansen till gränssnitts kontroll blocket i IP-instansen. När driv rutinen tar emot ett data paket måste den lagra gränssnitts informationen i NX_PACKETs strukturen innan den vidarebefordras till IP Receive-logiken. Observera att en IP-instans redan måste skapas innan du kopplar några gränssnitt.

IPv6-tjänster har inte startats efter anrop till ***nx_ip_create** _. Program som vill använda IPv6-tjänster måste anropa tjänsten _ *_nx_ipv6_enable_** för att starta IPv6.

I IPv6-nätverket kan varje gränssnitt i en IP-instans ha flera globala IPv6-adresser. Förutom att använda DHCPv6 för IPv6-adresstilldelning, kan en enhet även använda automatisk adress konfiguration. Mer information finns i avsnitten "IP Control Block" och "IPv6-adress matchning" senare i det här kapitlet.

### <a name="ip-send"></a>IP-sändning

IP-sändnings bearbetningen i NetX Duo är mycket effektiv. Lägga-pekaren i paketet flyttas bakåt för att hantera IP-huvudet. IP-huvudet har slutförts (med alla alternativ som anges av anrops protokoll skiktet) beräknas kontroll summan på raden (endast för IPv4-paket) och paketet skickas till den associerade nätverks driv rutinen. Dessutom samordnas utgående fragmentering från bearbetningen av IP-överföring.

För IPv4 initierar NetX Duo ARP-begäranden om fysisk mappning krävs för målets IP-adress. IPv6 använder Neighbor Discovery för IPv6-Address-tophysical-Address-mappning.

> [!NOTE]
> *För IPv4-anslutningar är paket som kräver IP-namnmatchning (dvs. fysisk mappning) i kö i ARP-kön tills antalet paket i kö överskrider ARP-ködjup (definieras av symbolen **NX_ARP_MAX_QUEUE_DEPTH**). Om ködjup nås tar NetX Duo bort det äldsta paketet i kön och fortsätter att vänta på adress matchning för de återstående paketen i kö. Å andra sidan, om en ARP-post inte har lösts, släpps de väntande paketen på ARP-posten vid tids gränsen för ARP-posten.*

För system med flera nätverks gränssnitt väljer NetX Duo ett gränssnitt baserat på mål-IP-adressen. Följande procedur gäller för urvals processen:

1. Om avsändaren anger ett utgående gränssnitt och gränssnittet är giltigt använder du det gränssnittet.
2. Om en mål adress är IPv4-broadcast eller multicast används det första aktiverade fysiska gränssnittet.
3. Om mål adressen finns i tabellen för statisk routning används det gränssnitt som är associerat med gatewayen.
4. Om målet är länkat, används on-Link-gränssnittet.
5. Om mål adressen är en länk lokal adress (169.254.0.0/16) används det första giltiga gränssnittet.
6. Om standard-gatewayen har kon figurer ATS använder du det gränssnitt som är associerat med standardgateway för att överföra paketet.
7. Slutligen, om en av de giltiga IP-adresserna för gränssnittet är länk lokal adress (169.254.0.0/16), används det här gränssnittet som käll adress för överföringen.
8. Utgående paket ignoreras om inget av ovanstående inträffar.

### <a name="ip-receive"></a>IP-mottagning

Den mottagna IP-bearbetningen anropas antingen från nätverks driv rutinen eller den interna IP-tråden (för bearbetning av paket i kön med uppskjutna mottagna paket). IP-inleveransbearbetning undersöker protokoll fältet och försöker skicka paketet till rätt protokoll komponent. Innan paketet skickas tas IP-huvudet bort genom att lägga-pekaren flyttas förbi IP-huvudet.

IP Receive-bearbetning identifierar också fragmenterade IP-paket och utför nödvändiga steg för att sätta samman dem igen om fragmentering har Aktiver ATS. Om fragmentering krävs men inte aktive rad, ignoreras paketet.

NetX Duo avgör lämpligt nätverks gränssnitt baserat på det gränssnitt som anges i paketet. Om paket gränssnittet är NULL är NetX Duo standardvärdet för det primära gränssnittet. Detta görs för att garantera kompatibilitet med äldre NetX Duo Ethernet-drivrutiner.

### <a name="raw-ip-send"></a>RAW IP-sändning

Ett RAW IP-paket är en IP-ram som innehåller nytto lasten i versaler och protokoll som inte stöds direkt (och bearbetas) av NetX Duo. Med ett RAW-paket kan utvecklare definiera sina egna IP-baserade program. Ett program kan skicka Raw IP-paket direkt med hjälp av ***nxd_ip_raw_packet_send** _-tjänsten om RAW IP-paketfiltrering har Aktiver ATS med tjänsten _*_nx_ip_raw_packet_enabled_*_ . När du överför ett unicast-paket i ett IPv6-nätverk fastställer NetX Duo automatiskt den bästa käll-IPv6-adressen som ska användas för att skicka paketen utifrån mål adressen. Om mål adressen är en multicast-eller broadcast för IPv4-adress, kommer NetX Duo att standardvärdet för det första (primära) gränssnittet. För att skicka sådana paket från sekundära gränssnitt måste programmet därför använda tjänsten _ *_nx_ip_raw_packet_source_send_** för att ange käll adressen som ska användas för det utgående paketet.

### <a name="raw-ip-receive"></a>RAW IP-mottagning

Om RAW IP-paketfiltrering är aktive rad kan programmet få obehandlade IP-paket via tjänsten ***nx_ip_raw_packet_receive** _. Alla inkommande paket bearbetas enligt det protokoll som anges i IP-huvudet. Om protokollet anger UDP, TCP, IGMP eller ICMP, kommer NetX Duo att bearbeta paketet med lämplig hanterare för paket protokoll typen. Om protokollet inte är ett av dessa protokoll och RAW IP Receive är aktiverat placeras det inkommande paketet i kön för rå paket som väntar på att programmet ska ta emot det via _*_nx_ip_raw_packet_receive_**-tjänsten. Dessutom kan program trådar pausas med en valfri tids gräns vid väntan på ett RAW IP-paket. Antalet paket som kan köas i kön för obehandlade paket är begränsat. Max värdet definieras i ***NX_IP_RAW_MAX_QUEUE_DEPTH**_, vars standardvärde är 20. Ett program kan ändra det maximala värdet genom att anropa tjänsten _ *_nx_ip_raw_receive_queue_max_set_**.

Alternativt kan NetX Duo-biblioteket skapas med ***NX_ENABLE_IP_RAW_PACKET_FILTER *.** I det här läget har programmet en motringnings funktion som anropas varje gång ett paket med en ohanterad protokoll typ tas emot. IP Receive-logiken vidarebefordrar paketet till den användardefinierade RAW-paketets mottagnings filter rutin. Filter rutinen bestämmer huruvida RAW-paketet ska behållas för framtida processer eller inte. Returvärdet från återanrops rutinen visar om paketet har bearbetats av det obehandlade paket mottagnings filtret. Om paketet bearbetas av motringningsfunktionen bör paketet frisläppas när programmet har gjorts med paketet. Annars är NetX Duo ansvarig för att släppa paketet. Mer information om hur du använder funktionen RAW Packet filter hittar du i **_nx_ip_raw_packet_filter_set_** .

> [!NOTE]
> * BSD-funktionen för NetX Duo förlitar sig på funktionen för RAW Packet filter för att hantera BSD RAW-socketar. För att stödja RAW-socket i BSD-omslutningen måste NetX Duo-biblioteket skapas med ***NX_ENABLE_IP_RAW_PACKET_FILTER** _ definieras och programmet ska inte använda _*_nx_ip_raw_packet_filter_set_*_ för att installera ett eget paket FILTER för rå data functions._

### <a name="default-packet-pool"></a>Standard pakets bassäng

Varje IP-instans tilldelas en standardpool för paket när den skapas. Den här poolen används för att allokera paket för ARP, RARP, ICMP, IGMP, olika TCP-kontroll paket (SYN, ACK, och så vidare), identifiering av grannar, routerupptäckt och duplicerad adress identifiering. Om standardpoolen är tom när NetX Duo måste allokera ett paket kan NetX Duo behöva avbryta den specifika åtgärden och returnera ett fel meddelande om möjligt.

### <a name="ip-helper-thread"></a>IP-hjälp tråd

Varje IP-instans har en hjälp tråd. Den här tråden ansvarar för hantering av all uppskjuten paket bearbetning och all periodisk bearbetning. IP-hjälpens tråd skapas i ***nx_ip_create.*** Det är här som tråden tilldelas sin stack och prioritet. Observera att den första bearbetningen i IP Helper-tråden är att slutföra initieringen av nätverks driv rutinen som är associerad med IP-Create-tjänsten. När nätverks driv rutins initieringen är klar startar hjälp tråden en oändlig slinga för att bearbeta paket och periodiska begär Anden.

> [!IMPORTANT]
> *Om ett oförutsägbart beteende visas i IP-undersöknings tråden, är det första fel söknings steget att öka dess stack storlek under IP-tjänsten för att skapa fel sökning. Om stacken är för liten kan IP-hjälpen eventuellt skriva över minne, vilket kan orsaka ovanliga problem.*

### <a name="thread-suspension"></a>Tråd upphängning

Program trådar kan pausas vid försök att ta emot obehandlade IP-paket. När ett RAW-paket tas emot, tilldelas det nya paketet den första tråden och tråden återupptas. NetX Duo-tjänster för att ta emot paket har en valfri tids gräns för avstängning. När ett paket tas emot eller tids gränsen går ut, återupptas program tråden med rätt slut för ande status.

### <a name="ip-statistics-and-errors"></a>IP-statistik och fel

Om den är aktive rad håller NetX Duo reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter underhålls för varje IP-instans:

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

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med tjänsten ***nx_ip_info_get***.

### <a name="ip-control-block-nx_ip"></a>Kontroll block för IP-kontroll NX_IP

Egenskaperna för varje IP-instans finns i kontroll blocket. Den innehåller användbar information, till exempel IP-adresser och nätverks masker för varje nätverks enhet och en tabell med grann-IP och mappning av fysiska maskin varu adresser. Den här strukturen definieras i ***nx_api. h**-_file. Om IPv6 är aktiverat innehåller den även en matris med IPv6-adress, antalet som anges av alternativet användare som kan konfigureras, _ *_NX_MAX_IPV6_ADDRESSES_* *. Standardvärdet tillåter att varje fysiskt nätverks gränssnitt har tre IPv6-adresser.

Kontroll block för IP-instans kan finnas var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="static-ipv4-routing"></a>Statisk IPv4-routning

Funktionen för statisk routning gör det möjligt för ett program att ange ett IPv4-nätverk och nästa hopp adress för specifika nätverks mål-IP-adresser. Om statisk routning är aktiverat söker NetX Duo igenom den statiska routningstabellen för en post som matchar mål adressen för det paket som ska skickas. Om ingen matchning hittas söker NetX Duo igenom listan över fysiska gränssnitt och väljer en käll-IP-adress och nästa hopp adress baserat på mål-IP-adressen och nätverks masken. Om målet inte matchar någon av IP-adresserna för de nätverks driv rutiner som är kopplade till IP-instansen, väljer NetX Duo ett gränssnitt som är direkt anslutet till standard-gatewayen och använder gränssnittets IP-adress som käll adress och standard-gateway som nästa hopp.

Du kan lägga till och ta bort poster från tabellen för statisk routning med hjälp av ***nx_ip_static_route_add** _ och _ *_nx_ip_static_route_delete_**-tjänsterna. Om du vill använda statisk routning måste värd programmet aktivera den här funktionen genom att definiera ***NX_ENABLE_IP_STATIC_ROUTING.***

> [!NOTE]
> *När du lägger till en post i den statiska routningstabellen söker NetX Duo efter en matchande post för den angivna mål adressen redan i tabellen. Om det finns en sådan, ger den företräde för posten med det mindre nätverket (längre prefix) i nätverks masken.*

### <a name="ipv4-forwarding"></a>IPv4-vidarebefordring

Om det inkommande IPv4-paketet inte är avsett för den här noden och IPv4-vidarebefordrings funktionen är aktive rad försöker NetX Duo vidarebefordra paketet via de andra gränssnitten.  

### <a name="ip-fragmentation"></a>IP-fragmentering

Nätverks enheten kan ha gränser för storleken på utgående paket. Den här gränsen kallas för maximal överförings enhet (MTU). IP-MTU är den största IP-bildrutans storlek som en länk skikt driv rutin kan överföra utan att fragmentera IP-paketet. Under en initierings fas av enhets driv rutinen måste driv rutins modulen konfigurera dess IP-MTU-storlek via tjänsten ***nx_ip_interface_mtu_set.***

Även om det inte rekommenderas kan programmet generera datagram som är större än den underliggande IP-MTU som stöds av enheten. Innan det här IP-datagrammet överförs måste IP-skiktet fragmentera dessa paket. När du tar emot fragmenterade IP-ramar måste det mottagande slutet lagra alla fragmenterade IP-ramar med samma fragment-ID och ommontera dem i rätt ordning. Om IP-mottagnings logiken inte kan samla in alla fragment för att återställa den ursprungliga IP-ramen i tiden, släpps alla fragment. Det är upp till det övre skikt protokollet för att identifiera sådana paket förluster och återställa från det.

IP-fragmentering gäller för både IPv4-och IPv6-paket.

För att stödja IP-fragmentering och omsammansättnings åtgärd måste system designern aktivera funktionen IP-fragmentering i NetX Duo med hjälp av tjänsten ***nx_ip_fragment_enable*** . Om den här funktionen inte är aktive rad ignoreras inkommande fragmenterade IP-paket, samt paket som överskrider nätverks driv Rutinens MTU.

> [!NOTE]
> * Logiken för IP-fragmentering kan tas bort helt genom att definiera ***NX_DISABLE_FRAGMENTATION** _ när du skapar netx Duo-biblioteket. Detta bidrar till att minska kod storleken för NetX Duo. Observera att i den här situationen är funktionerna för både IPv4-och IPv6-fragmentering/ommontering disabled._

> [!NOTE]
> *Om **NX_DISABLE_CHAINED_PACKET** har definierats måste IP-fragmentering vara inaktiverat.*

> [!NOTE]
> *I ett IPv6-nätverk fragmenterar inte routrar ett datagram om storleken på datagrammet överskrider den minsta MTU-storleken. Därför är det upp till den sändande enheten för att fastställa den minsta MTU mellan källan och målet, och för att säkerställa att storleken på IP-datagram inte överskrider sökvägen till MTU. I NetX Duo kan IPv6-SÖKVÄGens MTU-identifiering aktive ras genom att skapa NetX Duo-biblioteket med symbolen **NX_ENABLE_IPV6_PATH_MTU_DISCOVERY** definierad.*

## <a name="address-resolution-protocol-arp-in-ipv4"></a>ARP (Address Resolution Protocol) i IPv4

ARP-protokollet (Address Resolution Protocol) ansvarar för att dynamiskt mappa 32-bitars IPv4-adresser till de underliggande fysiska medierna (RFC 826). Ethernet är det mest typiska fysiska mediet och stöder 48-bitars adresser. Behovet av ARP bestäms av nätverks driv rutinen som tillhandahålls till tjänsten ***nx_ip_create** _. Om fysisk mappning krävs måste nätverks driv rutinen använda _ *_nx_interface_address_mapping_needed_**-tjänsten för att konfigurera driv rutins gränssnittet korrekt.

### <a name="arp-enable"></a>Aktivera ARP

För att ARP ska fungera korrekt måste den först aktive ras av programmet med ***nx_arp_enable*** -tjänsten. Den här tjänsten konfigurerar olika data strukturer för ARP-bearbetning, inklusive skapandet av ett ARP-cache-utrymme från det minne som har angetts till tjänsten ARP enable.

### <a name="arp-cache"></a>ARP-cache

ARP-cachen kan visas som en matris med interna ARP-mappnings data strukturer. Varje intern struktur kan underhålla relationen mellan en IP-adress och en fysisk maskin varu adress. Dessutom har varje data struktur länk pekare så att den kan ingå i flera länkade listor.

Programmet kan slå upp en IP-adress från ARP-cachen genom att tillhandahålla maskin varans MAC-adress med hjälp av tjänsten ***nx_arp_ip_address_find** _ om mappningen finns i ARP-tabellen. På samma sätt returnerar tjänsten _ *_nx_arp_hardware_address_find_** Mac-adressen för en specifik IP-adress.

### <a name="arp-dynamic-entries"></a>Dynamiska ARP-poster

Som standard placerar tjänsten ARP Enable alla poster i ARP-cachen i listan över tillgängliga dynamiska ARP-poster. En dynamisk ARP-post tilldelas från den här listan av NetX Duo när en skicka-begäran till en omappad IP-adress identifieras. Efter allokeringen konfigureras ARP-posten och en ARP-begäran skickas till det fysiska mediet.

En dynamisk post kan också skapas av tjänsten ***nx_arp_dynamic_entry_set***.

> [!IMPORTANT]
> *Om alla dynamiska ARP-poster används ersätts den senast använda ARP-posten med en ny mappning.*

### <a name="arp-static-entries"></a>Statiska ARP-poster

Programmet kan också konfigurera statiska ARP-mappningar genom att använda ***nx_arp_static_entry_create** _service. Den här tjänsten allokerar en ARP-post från listan över dynamiska ARP-poster och placerar den på den statiska listan med mappnings informationen som tillhandahålls av programmet. Statiska ARP-poster omfattas inte av åter användning eller åldrande. Programmet kan ta bort en statisk post genom att använda tjänsten _*_nx_arp_static_entry_delete_*_. Om du vill ta bort alla statiska poster i ARP-tabellen kan programmet använda tjänsten _ *_nx_arp_static_entries_delete_* *.

### <a name="automatic-arp-entry"></a>Automatisk ARP-post

NetX Duo registrerar peers IP/MAC-mappning efter peer-svar på ARP-begäran. NetX Duo implementerar också funktionen automatisk ARP-post där den registrerar peer IP/MAC-adress mappning baserat på oombedda ARP-förfrågningar från nätverket. Med den här funktionen kan ARP-tabellen fyllas i med peer-information, vilket minskar fördröjningen som krävs för att gå igenom ARP-begäran/svars cykeln. Nack delen med att aktivera automatisk ARP är dock att ARP-tabellen ofta fyller på ett upptaget nätverk med många noder på den lokala länken, vilket skulle leda till byte av ARP-post.

Den här funktionen är aktive rad som standard. För att inaktivera det måste NetX Duo-biblioteket kompileras med symbolen ***NX_DISABLE_ARP_AUTO_ENTRY*** definierad.</p>

### <a name="arp-messages"></a>ARP-meddelanden

Som tidigare nämnts skickas ett meddelande om ARP-begäran när IP-aktiviteten identifierar att mappning krävs för en IP-adress. ARP-begäranden skickas regelbundet (var ***NX_ARP_UPDATE_RATE** _ sekunder) tills ett motsvarande ARP-svar tas emot. Totalt _ *_NX_ARP_MAXIMUM_RETRIES_** ARP-begäranden görs innan ARP-försöket överges. När ett ARP-svar tas emot lagras den associerade fysiska adress informationen i ARP-posten i cacheminnet.

För NetX Duo avgör Duo vilket gränssnitt som skickar ARP-förfrågningar och svar baserat på den angivna mål adressen.

> [!NOTE]
> *Utgående IP-paket köas medan NetX Duo väntar på ARP-svaret. Antalet utgående IP-paket i kö definieras av konstanten **NX_ARP_MAX_QUEUE_DEPTH**.*

NetX Duo svarar även på ARP-förfrågningar från andra noder i det lokala IPv4-nätverket. När en extern ARP-begäran görs som matchar den aktuella IP-adressen för det gränssnitt som tar emot ARP-begäran, skapar NetX Duo ett ARP-svarsmeddelande som innehåller den aktuella fysiska adressen.

Formatet på Ethernet ARP-begäranden och-svar visas i bild 6 och beskrivs nedan.

| **Fråge-/svars &nbsp; fält**         | **Syfte**            |
| ---------------------------------- | ---------------------- |
| ***Ethernet-mål adress*** | Detta 6-byte-fält innehåller mål adressen för ARP-svaret och är en sändning (alla) för ARP-förfrågningar. Det här fältet ställs in av nätverks driv rutinen. 
| ***Ethernet-källans adress***      | Detta 6-byte-fält innehåller adressen till avsändaren av ARP-begäran eller-svaret och har kon figurer ATS av nätverks driv rutinen. |
| ***Ramtyp*** | Detta fält i 2 byte innehåller typen av Ethernet-ram som finns och, för ARP-förfrågningar och svar, detta är lika med 0x0806. Detta är det sista fältet som nätverks driv rutinen ansvarar för att konfigurera. |
| ***Maskin varu typ*** | Detta fält i 2 byte innehåller maskin varu typen, som är 0x0001 för Ethernet. |
| ***Protokoll typ*** | Detta fält i 2 byte innehåller protokoll typen, som är 0x0800 för IP-adresser. |
| ***Maskin varu storlek*** | Det här 1-byte fältet innehåller maskin varu adressens storlek, som är 6 för Ethernet-adresser. |

![Diagram över ARP-paketets format.](./media/user-guide/arp-packet-format.png)

**BILD 6. ARP-paketfilter**

| Fråge-/svars &nbsp; fält | Syfte |
|---|---|
| ***Protokoll storlek*** | Detta 1-byte-fält innehåller IP-adressens storlek, som är 4 för IP-adresser. |
| ***Åtgärds kod*** | Detta fält i 2 byte innehåller åtgärden för det här ARP-paketet. En ARP-begäran anges med värdet 0x0001, medan ett ARP-svar representeras av värdet 0x0002. |
| ***Avsändarens Ethernet-adress*** | Det här 6-byte-fältet innehåller avsändarens Ethernet-adress. |
| ***Avsändarens IP-adress*** | Detta fält med fyra byte innehåller avsändarens IP-adress. |
| ***Mål-Ethernet-adress*** | Detta 6-byte-fält innehåller målets Ethernet-adress. |
| ***Mål-IP-adress*** | Detta fält i 4 byte innehåller målets IP-adress. |

> [!NOTE]
> *ARP-förfrågningar och-svar är paket med Ethernet-nivå. Alla andra TCP/IP-paket kapslas in av ett IP-pakets huvud.*

> [!NOTE]
> *Alla ARP-meddelanden i TCP/IP-implementeringen förväntas vara i **big endian** format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen.*

### <a name="arp-aging"></a>ARP-åldrande

NetX stöder automatisk ogiltig dynamisk ARP-post. ***NX_ARP_EXPIRATION_RATE** _ anger antalet sekunder som en upprättad IP-adress till fysisk mappning är giltig. Efter förfallo datum tas ARP-posten bort från ARP-cachen. Nästa försök att skicka till motsvarande IP-adress leder till en ny ARP-begäran. Om du anger _ *_NX_ARP_EXPIRATION_RATE_** till noll inaktive ras ARP-åldrande, vilket är standard konfigurationen.

### <a name="arp-defend"></a>ARP-försvara

När en ARP-begäran eller ett ARP-svars paket tas emot och avsändaren har samma IP-adress, som står i konflikt med IP-adressen för den här noden, skickar NetX Duo en ARP-begäran för den adressen som försvars tid. Om ett konflikt-ARP-paket tas emot mer än en gång på 10 sekunder skickar NetX Duo inte fler försvarande paket. Standard intervallet på 10 sekunder kan omdefinieras med ***NX_ARP_DEFEND_INTERVAL** _. Det här beteendet följer principen som anges i 2.4 (c) av RFC5227. Eftersom Windows XP ignorerar ARP-meddelande som ett svar för sin ARP-avsökning kan användaren definiera _ *_NX_ARP_DEFEND_BY_REPLY_** för att skicka ARP-svar som ytterligare försvar.

### <a name="arp-statistics-and-errors"></a>ARP-statistik och fel

Om den här inställningen är aktive rad håller NetX Duo ARP reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter underhålls för varje IP-ARP-bearbetning:

- Totalt antal skickade ARP-begäranden
- Totalt antal mottagna ARP-begäranden
- Totalt antal skickade ARP-svar 
- Totalt antal mottagna ARP-svar 
- Totalt antal dynamiska ARP-poster 
- Totalt antal statiska ARP-poster 
- Totalt antal inaktuella ARP-poster 
- Totalt antal ogiltiga ARP-meddelanden 

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med tjänsten ***nx_arp_info_get*** .

## <a name="reverse-address-resolution-protocol-rarp-in-ipv4"></a>RARP (reversed Address Resolution Protocol) i IPv4

RARP (reversed Address Resolution Protocol) är protokollet för att begära nätverks tilldelning av värdens 32-bitars IP-adresser (RFC 903). Detta görs via en RARP-begäran och fortsätter regelbundet tills en nätverks medlem tilldelar en IP-adress till värd nätverks gränssnittet i ett RARP-svar. Programmet skapar en IP-instans av tjänsten ***nx_ip_create*** med en noll IP-adress. Om RARP har Aktiver ATS av programmet kan det använda RARP-protokollet för att begära en IP-adress från nätverks servern som är tillgänglig via gränssnittet som har en noll IP-adress.

### <a name="rarp-enable"></a>Aktivera RARP

Om du vill använda RARP måste programmet skapa IP-instansen med en IP-adress som är noll och sedan aktivera RARP med hjälp av tjänsten ***nx_rarp_enable***. För flera hem system måste minst en nätverks enhet som är associerad med IP-instansen ha en IP-adress som är noll. RARP-bearbetningen skickar regelbundet RARP begär Anden för NetX Duo-systemet som kräver en IP-adress tills ett giltigt RARP-svar med den angivna IP-adressen för nätverket tas emot. I det här läget är RARP-bearbetningen klar.

När RARP har Aktiver ATS inaktive ras den automatiskt när alla gränssnitts adresser har lösts. Programmet kan tvinga RARP att avslutas genom att använda tjänsten ***nx_rarp_disable***.

### <a name="rarp-request"></a>RARP-begäran

Formatet på ett RARP begär ande paket är nästan identiskt med ARP-paketet som visas i [bild 6](#arp-messages). Den enda skillnaden är att fältet ramtyp är 0x8035 och fältet *Åtgärds kod* är 3, vilket anger en RARP-begäran. Som tidigare nämnts kommer RARP-begäranden att skickas regelbundet (var ***NX_RARP_UPDATE_RATE*** sekund) tills ett RARP-svar med den tilldelade IP-adressen för nätverket tas emot.

> [!NOTE]
> *Alla RARP-meddelanden i TCP/IP-implementeringen förväntas vara i **big endian** format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen.*

### <a name="rarp-reply"></a>RARP-svar

RARP svarsmeddelanden tas emot från nätverket och innehåller den nätverks tilldelade IP-adressen för den här värden. Formatet på ett RARP Reply-paket är nästan identiskt med ARP-paketet som visas i bild 6. Den enda skillnaden är att fältet ramtyp är 0x8035 och fältet *Åtgärds kod* är 4, vilket anger ett RARP-svar. När den har tagits emot är IP-adressen konfigurerad i IP-instansen, den periodiska RARP-begäran är inaktive rad och IP-instansen är nu klar för normal nätverks drift.

För multihome-värdar tillämpas IP-adressen på det begärda nätverks gränssnittet. Om det fortfarande finns andra nätverks gränssnitt som begär en tilldelning av IP-adresser, fortsätter den periodiska RARP-tjänsten tills alla IP-begäranden för IP-adresser är lösta.

> [!NOTE]
> *Programmet ska inte använda IP-instansen förrän RARP-bearbetningen har slutförts. **Nx_ip_status_check** kan användas av program för att vänta på att RARP slutförs. För multihome-system ska programmet inte använda det begärda gränssnittet förrän RARP-bearbetningen har slutförts på det gränssnittet. Status för IP-adressen på den sekundära enheten kan kontrol leras med tjänsten **nx_ip_interface_status_check** .*

### <a name="rarp-statistics-and-errors"></a>RARP statistik och fel

Om den här inställningen är aktive rad håller NetX Duo RARP koll på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter underhålls för varje IP-RARP bearbetning:

- Totalt antal skickade RARP-begäranden
- Totalt antal mottagna RARP-svar
- Totalt antal RARP ogiltiga meddelanden

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med tjänsten ***nx_rarp_info_get*** .

## <a name="internet-control-message-protocol-icmp"></a>Internet Control Message Protocol (ICMP)

Internet Control Message Protocol för IPv4 (ICMP) är begränsad till överföring av fel och kontroll av information mellan IP-medlemmar. Internet Control Message Protocol för IPv6 (ICMPv6) hanterar också fel-och kontroll information och krävs för adress matchnings protokoll som duplicerad adress identifiering (pappa) och automatisk adress konfiguration för tillstånd.

Precis som de flesta andra program skikt (t. ex. TCP/IP-meddelanden) kapslas ICMP-och ICMPv6-meddelanden av ett IP-huvud med protokoll beteckningen ICMP (eller ICMPv6).

### <a name="icmp-statistics-and-errors"></a>ICMP-statistik och fel

Om den är aktive rad håller NetX Duo reda på flera ICMP-statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter hanteras för varje IP-ICMP-bearbetning: 

- Totalt antal ICMP-pingar som skickats  
- Totalt antal ICMP-Ping-Timeoutar 
- Totalt antal inaktiverade ICMP Ping-trådar 
- Totalt antal mottagna ICMP ping-svar 
- Totalt antal fel i ICMP-kontrollsumma 
- Totalt antal ICMP-ohanterade meddelanden 

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med tjänsten ***nx_icmp_info_get*** .

## <a name="icmpv4-services-in-netx-duo"></a>ICMPv4-tjänster i NetX Duo

### <a name="icmpv4-enable"></a>ICMPv4 Enable

Innan ICMPv4-meddelanden kan bearbetas av NetX Duo måste programmet anropa tjänsten ***nx_icmp_enable*** för att aktivera ICMPv4-bearbetning. När det är färdigt kan programmet utfärda ping-begäranden och fält inkommande ping-paket.  

### <a name="icmpv4-echo-request"></a>ICMPv4 ECHO-begäran

En ekobegäran är en typ av ICMPv4-meddelande som vanligt vis används för att kontrol lera om det finns en speciell nod i nätverket, som identifieras av dess värd-IP-adress. Det populära Ping-kommandot implementeras med ICMP Echo Request/Echo Reply-meddelanden. Om den aktuella värden finns, bearbetar dess nätverks stack ping-begäran och svaren med ett ping-svar. Bild 7 information om formatet ICMPv4 ping Message.

![ICMPv4 ping-meddelande](./media/user-guide/icmpv4-ping-message.png)  

**BILD 7. ICMPv4 ping-meddelande**

> [!NOTE]
> *Alla ICMPv4-meddelanden i TCP/IP-implementeringen förväntas vara i **big endian** format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen.*

Följande beskriver formatet ICMPv4-sidhuvud:

|Rubrik fält |Syfte |
|---|---|
|**Typ** |Det här fältet anger ICMPv4-meddelandet (bitar 31-24). De vanligaste är:<br />-0: eko svar<br />-3: det går inte att hitta målet<br />-8: ekobegäran<br />-11: tiden överskreds<br />-12: parameter problem |
|**Kod** |Det här fältet är Sammanhangs beroende av typ fältet (bitar 23-16). För en ekobegäran eller svara har koden värdet noll.|
|**Lastning** |Det här fältet innehåller 16-bitars kontroll summa för den enda komplement summan av ICMPv4-meddelandet, inklusive hela det ICMPv4-sidhuvudet som börjar med fältet typ. Innan du genererar kontroll summan rensas fältet kontroll summa.|
|**Fastställa** | Det här fältet innehåller ett ID-värde som identifierar värden. en värd ska använda det ID som extraheras från en EKOBEGÄRAN i eko svaret (bitar 31-16).|
|**Sekvensnummer** |Det här fältet innehåller ett ID-värde; en värd ska använda det ID som extraheras från en EKOBEGÄRAN i eko svaret (bitar 31-16). Till skillnad från fältet identifierare kommer det här värdet att ändras i en efterföljande ekobegäran från samma värd (bitar 15-0).|

### <a name="icmpv4-echo-response"></a>ICMPv4 eko-svar    
Ett ping-svar är en annan typ av ICMP-meddelanden som genereras internt av ICMP-komponenten som svar på en extern ping-begäran. Utöver bekräftelsen innehåller ping-svaret även en kopia av de användar data som angavs i ping-begäran.

### <a name="icmpv4-error-messages"></a>ICMPv4-fel meddelanden   
Följande ICMPv4-fel meddelanden stöds i NetX Duo: 
- Det går inte att hitta målet 
- Tiden överskrider 
- Parameter problem

## <a name="internet-group-management-protocol-igmp"></a>Internet Grupphanteringsprotokoll (IGMP)

IGMP (Internet Group Management Protocol) tillhandahåller en enhet för att kommunicera med sina grannar och dess routrar som den avser att ta emot, eller ansluta till, en IPv4-multicast-grupp (RFC 1112 och RFC 2236). En multicast-grupp är i princip en dynamisk uppsättning nätverks medlemmar och representeras av en klass D IP-adress. Medlemmar i multicast-gruppen kan lämna när som helst och nya medlemmar kan gå med i taget. Den samordning som används för att ansluta till och lämna gruppen är ansvaret för IGMP.

> [!NOTE]
> *IGMP är endast utformat för IPv4-multicast-grupper. Det kan inte användas i IPv6-nätverket.*

### <a name="igmp-enable"></a>Aktivera IGMP     
Innan en multicasting-aktivitet kan ske i NetX Duo måste programmet anropa tjänsten ***nx_igmp_enable*** . Den här tjänsten utför grundläggande IGMP-initiering som förberedelse för multicast-begäranden.

### <a name="multicast-ipv4-addressing"></a>Multicast-IPv4-adressering  
Som tidigare nämnts är multicast-adresser faktiskt klass D IP-adresser som visas i [bild 4](#ipv4-addresses). De nedre 28 bitarna i klass D-adressen motsvarar multicast-gruppens ID. Det finns en serie fördefinierade multicast-adresser. men *alla värd adresser* (244.0.0.1) är särskilt viktiga för IGMP-bearbetning. *Adressen alla värdar* används av routrar för att fråga alla multicast-medlemmar att rapportera om vilka multicast-grupper de tillhör.  

### <a name="physical-address-mapping-in-ipv4"></a>Fysisk adress mappning i IPv4
Klass D multicast-adresser mappas direkt till fysiska Ethernet-adresser som sträcker sig från 01.00.5 e. 00.00.00 till 01.00.5 e. 7f. AA. AA. De lägre 23 bitarna av IP-multicast-adress kartan direkt till de lägre 23 bitarna av Ethernet-adressen.

### <a name="multicast-group-join"></a>Anslutning till multicast-grupp
Program som behöver ansluta till en viss multicast-grupp kan göra detta genom att anropa tjänsten ***nx_igmp_multicast_join*** . Den här tjänsten håller reda på antalet begär Anden att ansluta till den här multicast-gruppen. Om det här är det första programmet requestto ansluter till multicast-gruppen skickas en IGMP-rapport ut från det primära nätverket som anger att den här värdens avsikt att ansluta till gruppen. Därefter anropas nätverks driv rutinen för att ställa in för att lyssna efter paket med Ethernet-adressen för den här multicast-gruppen.

Om multicast-gruppen är tillgänglig via ett visst gränssnitt i ett multihome-system måste programmet använda tjänsten ***nx_igmp_multicast_interface_join** _ i stället för _ *_nx_igmp_multicast_join_* *, som är begränsad till multicast-grupper i det primära nätverket.

### <a name="multicast-group-leave"></a>Lämna multicast-grupp   
Program som måste lämna en tidigare ansluten multicast-grupp kan göra det genom att anropa tjänsten ***nx_igmp_multicast_leave*** . Den här tjänsten minskar det interna antalet som är associerat med hur många gånger gruppen anslöts. Om det inte finns några väntande kopplings begär Anden för en grupp, anropas nätverks driv rutinen för att inaktivera lyssning av paket med den här multicast-gruppens Ethernet-adress.

### <a name="multicast-loopback"></a>Multicast-loopback    
Ett program kan vilja ta emot multicast-trafik som härstammar från en av källorna på samma nod. För detta krävs att loopback aktive ras av IP-multicast-komponenten med hjälp av tjänsten ***nx_igmp_loopback_enable***.

### <a name="igmp-report-message"></a>IGMP-rapport meddelande      
När programmet ansluter till en multicast-grupp skickas ett IGMP-rapport meddelande via nätverket för att indikera värddatorns avsikt att ansluta till en viss multicast-grupp. Formatet på IGMP-rapportens meddelande visas i bild 8. Multicast-gruppadressen används för både grupp meddelandet i IGMP-rapport meddelandet och mål-IP-adressen.

I bilden ovan (bild 8) innehåller IGMP-huvudet ett fält av version/typ, maximalt svar

![Diagram över ett IGMP-rapport meddelande.](./media/user-guide/image17.jpg)

**FIGUR 8. IGMP-rapport meddelande**

tid, fält för kontroll summa och adress fält för multicast-grupp. För IGMPv1-meddelanden är fältet maximal svars tid alltid inställt på noll, eftersom detta inte är en del av IGMPv1-protokollet. Fältet Max svars tid anges när värden får ett IGMP-meddelande av typen fråga och rensas när en värd får ett annat värde för rapport typ meddelandet som definieras av IGMPv2-protokollet.

I följande avsnitt beskrivs IGMP-huvud formatet:

|Rubrik fält|Syfte|
|---|---|
|**Version** |Det här fältet anger IGMP-versionen (bitar 31-28).|
|**Typ** |Det här fältet anger typen av IGMP-meddelande (bitar 27 -24).|
|**Maximal svars tid** |Används inte i IGMP v1. I IGMP v2 fungerar det här fältet som maximal svars tid.|
|**Lastning** |Det här fältet innehåller 16-bitars kontroll summa för den enda komplement summan av IGMP-meddelandet som börjar med IGMP-versionen (bitar 0-15)|
|**Grupp adress** |32-bitars klass D grupp IP-adress|

IGMP-rapport meddelanden skickas också som svar på IGMP-frågemeddelanden som skickas av en multicast-router. Multicast-routrar skickar regelbundet frågemeddelanden ut för att se vilka värdar som fortfarande kräver grupp medlemskap. Fråga meddelanden har samma format som IGMP-rapport meddelandet som visas i bild 8. De enda skillnaderna är att IGMP-typen är lika med 1 och att grupp adress fältet är inställt på 0. IGMP-frågemeddelanden skickas till IP-adressen *alla värdar* av multicast-routern. En värd som fortfarande vill behålla grupp medlemskapet svarar genom att skicka ett annat IGMP-rapport meddelande.

> [!NOTE]
> *Alla meddelanden i TCP/IP-implementeringen förväntas vara i **big endian** format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen.*

### <a name="igmp-statistics-and-errors"></a>IGMP-statistik och fel    
<th><p>Om den är aktive rad håller NetX Duo IGMP-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter underhålls för varje IP-IGMP-bearbetning: 

- Totalt antal skickade IGMP-rapporter 
- Totalt antal mottagna IGMP-frågor 
- Totalt antal fel i IGMP-kontrollsumma 
- Totalt antal IGMP-aktuella grupper anslutna 

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med tjänsten ***nx_igmp_info_get***. 

### <a name="multicast-without-igmp"></a>Multicast utan IGMP  
Program som förväntar sig IPv4-multicast-trafik kan ansluta till en multicast-gruppadress utan att anropa IGMP-meddelanden med hjälp av tjänsten ***nx_ipv4_multicast_interface_join***. Den här tjänsten instruerar IPv4-lagret och den underliggande gränssnitts driv rutinen att acceptera paket från den angivna IPv4-multicast-adressen. Det finns dock inga IGMP-grupphanterings meddelanden som skickas eller bearbetas för den här gruppen.

Programmet vill inte längre ta emot trafik från gruppen kan använda tjänsten ***nx_ipv4_multicast_interface_leave.***

## <a name="ipv6-in-netx-duo"></a>IPv6 i NetX Duo

### <a name="ipv6-addresses"></a>IPv6-adresser   
IPv6-adresser är 128 bitar. Arkitekturen i IPv6-adressen beskrivs i RFC 4291. Adressen är indelad i ett prefix som innehåller de mest signifikanta bitarna och en värd adress som innehåller de lägre bitarna. Prefixet anger typ av adress och är ungefär samma som nätverks adressen i IPv4-nätverket.

IPv6 har tre typer av adress specifikationer: unicast, anycast (stöds inte i NetX Duo) och multicast. Unicast-adresser är de IP-adresser som identifierar en speciell värd på Internet. Unicast-adresser kan vara antingen en källa eller en mål-IP-adress. Multicast-adresser anger en dynamisk grupp värdar på Internet. Medlemmar i multicast-gruppen kan ansluta till och lämna när de vill.

IPv6 har inte motsvarigheten till IPv4-broadcast-mekanismen. Möjligheten att skicka ett paket till alla värdar kan uppnås genom att skicka ett paket till den länk lokala alla värdarna multicast-gruppen.

IPv6 använder multicast-adresser för att utföra identifiering av grannar, routerupptäckt och tillstånds lösa automatiska konfigurations procedurer.

Det finns två typer av IPv6 unicast-adresser: länka lokala adresser, vanligt vis konstruerade genom att kombinera det välkända länk lokala prefixet med gränssnittets MAC-adress och globala IP-adresser, som även har prefixet och värd-ID-delen. En global adress kan konfigureras manuellt eller via den autonoma adress konfigurationen eller DHCPv6. NetX Duo stöder både länk lokal adress och global adress.

För att kunna hantera både IPv4-och IPv6-format tillhandahåller NetX Duo en ny datatyp, NXD_ADDRESS, för att tillhandahålla IPv4-och IPv6-adresser. Definitionen av den här strukturen visas nedan. Adress fältet är en union av IPv4-och IPv6-adresser.

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

Det första elementet *nxd_ip_version* i NXD_ADDRESS-strukturen anger IPv4-eller IPv6-version. De värden som stöds är antingen NX_IP_VERSION_V4 eller NX_IP_VERSION_V6. *nxd_ip_version* anger vilket fält i *nxd_ip_address* union som ska användas som IP-adress. NetX Duo API-tjänster tar vanligt vis en pekare till NXD_ADDRESS Structure as indataargumentet i stället för IP-adressen ULONG (32 bitar).

### <a name="link-local-addresses"></a>Länka lokala adresser     
En länk lokal adress är bara giltig i det lokala nätverket. En enhet kan skicka och ta emot paket till en annan enhet i samma nätverk när en giltig länk lokal adress har tilldelats till den. Ett program tilldelar en länk lokal adress genom att anropa NetX Duo-tjänsten ***nxd_ipv6_address_set*** med parametern prefixlängd inställd på 10. Programmet kan ange en länk lokal adress till tjänsten, eller så kan den bara använda NX_NULL som länk lokal adress och tillåta NetX Duo att skapa en länk lokal adress baserat på enhetens MAC-adress.

I följande exempel instruerar NetX Duo att konfigurera den länk lokala adressen med prefixlängden 10 på den primära enheten (index 0) med MAC-adressen:

```c
nxd_ipv6_address_set(ip_ptr, 0, NX_NULL, 10, NX_NULL);
```
I exemplet ovan, om MAC-adressen för gränssnittet är 54:32:10:1A: BC: 67, är motsvarande länk lokal adress:

```c
FE80::5632:10FF:FE1A:BC67
```
Observera att värd-ID-delen av IPv6-adressen (**5632:10FF: FE1A: BC67**) består av Mac-adressen på 6 byte, med följande ändringar:

- **0xFFFE** infogade mellan byte 3 och byte 4 i Mac-adressen
- Den andra lägsta biten i den första byten av MAC-adressen (U/L-biten) har angetts till 1

Se RFC 2464 (överföring av IPv6-paket över Ethernet-nätverk) för mer information om hur du skapar värd delen av en IPv6-adress från dess gränssnitts-MAC-adress.

Det finns några särskilda multicast-adresser för att skicka multicast-meddelanden till en eller flera värdar i IPv6:

| Group  | Adress   | Beskrivning  |
|---|---|---|
|Gruppen alla noder |**FF02:: 1** |Alla värdar i det lokala nätverket|
|Gruppen alla routrar |**FF02:: 2** |Alla routrar i det lokala nätverket|
|Anropad nod |**FF02:: 1: FF00:0/104** |Förklaras nedan|

En begärd nod-multicast-adress riktar sig till vissa värdar på den lokala länken i stället för alla IPv6-värdar. Det består av prefixet **FF02:: 1: ff00:0/104**, som är 104 bitar och de sista 24 bitarna i mål-IPv6-adressen. Till exempel är en IPv6-adress **205B: 209D: D028:: F058: D1C8:1024** har en solicitednode multicast-adress för adress **FF02:: 1: FFC8:1024**.

> [!IMPORTANT]
> *Den dubbla kolon notationen visar att de mellanliggande bitarna bara är nollor. **FF02:: 1: ff00:0/104** helt expanderat ser ut som* **FF02:0000:0000:0000:0000:0,001: ff00:0000**

### <a name="global-addresses"></a>Globala adresser    
Ett exempel på en global IPv6-adress är **2001:0123:4567:89AB: CDEF:: 1** netx Duo lagrar IPv6-adresser i NXD_ADDRESS-strukturen. I exemplet nedan innehåller NXD_ADDRESS variabeln **global_ipv6_address** en IPv6-adress för unicast. I följande exempel demonstreras en NetX Duo-enhet som skapar en speciell IPv6-global adress för den primära enheten:

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
Observera att prefixet för den här IPv6-adressen är **2001:0123:4567:89AB**, som är 64 bitar långt och är en vanlig prefixlängd för globala unicast IPv6-adresser på Ethernet.

NXD_ADDRESSs strukturen innehåller också IPv4-adresser. En IP-adress för **192.1.168.10** (**0xC001A80A**) som lagras i global_ipv4_address skulle ha följande minnes-layout:

|Fält |Värde |
|---|---|
|global_ipv4_address global_ipv4_address.nxd_ip_version |NX_IP_VERSION_V4|
|global_ipv4_address global_ipv4_address.nxd_ip_address. v4 |0xC001A80A|

När ett program skickar en adress till NetX Duo-tjänster, måste fältet *nxd_ip_version* ange rätt IP-version för lämplig paket hantering.

För att vara bakåtkompatibla med befintliga NetX-program stöder NetX Duo alla NetX-tjänster. Internt konverterar NetX Duo IPv4-adress typen ULONG till data typen NXD_ADDRESS innan den vidarebefordras till den faktiska NetX Duo-tjänsten.

I följande exempel illustreras likheten och skillnaderna mellan tjänsterna i NetX och NetX Duo.

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

Följande är motsvarande NetX-API:

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
> *Programutvecklare uppmuntras att använda NXD-versionen av dessa API: er*.

### <a name="ipv6-default-routers"></a>IPv6-standardroutrar    
IPv6 använder en standard router för att vidarebefordra paket till offlink-mål. NetX Duo-tjänsten ***nxd_ipv6_default_router_add*** gör det möjligt för ett program att lägga till en IPv6-router i tabellen default router. Se kapitel 4 "Beskrivning av tjänster" för fler standard router tjänster som erbjuds av NetX Duo.  

Vid vidarebefordring av IPv6-paket kontrollerar NetX Duo först om paket målet är på länk. Om inte, kontrollerar NetX Duo standardroutningstabell för en giltig router för att vidarebefordra off-Link-paketet till.  

Om du vill ta bort en router från IPv6-tabellen Standard router, måste programmet använda tjänsten ***nxd_ipv6_default_router_delete** _. Om du vill hämta poster i IPv6-tabellen Standard router använder du tjänsten _ *_nxd_ipv6_default_router_entry_get_* *.

### <a name="ipv6-header"></a>IPv6-sidhuvud    
IPv6-huvudet har ändrats från IPv4-huvudet. När ett paket allokeras anger anroparen program protokollet (t. ex. UDP, TCP), buffertstorlek i byte och hopp gräns.   

Bild 9 visar IPv6-huvudets format och tabellen innehåller rubrik komponenterna.

![Diagram över IPv6-huvudets format.](./media/user-guide/image18.png)

**BILD 9. IPv6-huvud format**

|IP-huvud | Syfte |
|---|---|
|Version |4-bitars fält för IP-version. För IPv6-nätverk måste värdet i det här fältet vara 6; För IPv4-nätverk måste det vara 4.|
|Trafikklass |8-bitars fält som lagrar information om trafik klass. Det här fältet används inte av NetX Duo.|
|Flödes etikett |20-bitars fält för att unikt identifiera flödet, om det finns något, som ett paket är associerat med. Värdet noll anger att paketet inte tillhör ett visst flöde. Det här fältet ersätter *TOS*-fältet i IPv4.|
|Nytto last längd |16-bitars fält som visar mängden data i byte för IPv6-paketet som följer IPv6-bas huvudet. Detta inkluderar alla inkapslade protokoll huvud och data.|
|Nästa sidhuvud | 8-bitars fält som anger vilken typ av tilläggs rubrik som följer IPv6-bas rubriken. Det här fältet ersätter *protokoll* fältet i IPv4.|
|Hopp gräns |8-bitars fält som begränsar antalet routrar som paketet tillåts att gå igenom. Det här fältet ersätter *TTL*-fältet i IPv4.|
|Käll adress |128-bitars fält som lagrar avsändarens IPv6-adress.|
|Mål adress |128-bitars fält som Sores IPv6-adressen till målet.|

### <a name="enabling-ipv6-in-netx-duo"></a>Aktivera IPv6 i NetX Duo    
Som standard är IPv6 aktiverat i NetX Duo. IPv6-tjänster är aktiverade i NetX Duo om det konfigurerbara alternativet ***NX_DISABLE_IPV6** _ i _nx_user. h * inte har definierats. Om ***NX_DISABLE_IPV6*** har definierats kommer netx Duo endast att erbjuda IPv4-tjänster och alla IPv6-relaterade moduler och tjänster är inte inbyggda i netx Duo-biblioteket.

Följande tjänst tillhandahålls för program för att konfigurera enhetens IPv6-adress: ***nxd_ipv6_address_set***

Förutom att manuellt ange enhetens IPv6-adresser, kan systemet även använda automatisk adress konfiguration med tillstånd. Om du vill använda det här alternativet måste programmet anropa ***nxd_ipv6_enable** _ för att kunna starta IPv6-tjänsterna på enheten. Dessutom måste ICMPv6-tjänster startas genom att anropa _*_nxd_icmp_enable_*_, vilket gör att netx Duo kan utföra tjänster som routermeddelanden, Neighbor Discovery och dubblettidentifiering. Observera att _*_nx_icmp_enable_*_ endast startar ICMP för IPv4-tjänster. _*_nxd_icmp_enable_*_ startar ICMP-tjänster för både IPv4 och IPv6. Om systemet inte behöver ICMPv6-tjänster kan du använda _ *_nx_icmp_enable_** så att modulen ICMPv6 inte är länkad till systemet.

I följande exempel visas en typisk NetX Duo IPv6-initierings procedur.

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

Protokoll på övre nivå (t. ex. TCP och UDP) kan aktive ras antingen före eller efter att IPv6 startar.

> [!IMPORTANT]  
> *IPv6-tjänster är bara tillgängliga när IP-tråd har initierats och enheten är aktive rad.*

När gränssnittet har Aktiver ATS (det vill säga att gränssnitts enhetens driv rutin är redo att skicka och ta emot data och en giltig länk lokal adress har hämtats) kan enheten erhålla globala IPv6-adresser med någon av följande metoder:

- Automatisk konfiguration av autonoma adresser;  
- Manuell konfiguration av IPv6-adress;  
- Adress konfiguration via DHCPv6 (med valfritt DHCPv6-paket)

De första två metoderna beskrivs nedan. Den tredje metoden (DHCPv6) beskrivs i DHCP-paketet.

### <a name="stateless-address-autoconfiguration-using-router-solicitation"></a>Automatisk adress konfiguration med router-inbjudning      
NetX Duo-enheter kan konfigurera sina gränssnitt automatiskt när de ansluts till ett IPv6-nätverk med en router som tillhandahåller prefixs information. Enheter som kräver tillstånds lös automatisk adress konfiguration skickar RS-meddelanden (router inbjudningar). Routrar i nätverket svarar med meddelanden om begärd router-annonsering (RA). RA-meddelanden annonserar prefix som identifierar de nätverks adresser som är associerade med en länk. Enheter genererar sedan en unik identifierare för nätverket som enheten är ansluten till. Adressen skapas genom att kombinera prefixet och dess unika identifierare. På det här sättet när du tar emot RA-meddelanden genererar värdarna sin IP-adress. Routrar kan också skicka regelbundna oönskade RA-meddelanden. 

> [!WARNING]
> *Netx Duo gör det möjligt för ett program att aktivera eller inaktivera tillstånds lös automatisk adress konfiguration vid körning. Om du vill aktivera den här funktionen måste NetX Duo-biblioteket kompileras med **NX_IPV6_STATELESS_AUTOCONFIG_CONTROL** definierat. När den här funktionen är aktive rad kan program använda **nxd_ipv6_stateless_address_autoconfigure_enable** och **nxd_ipv6_stateless_address_autocofigure_disable** för att aktivera eller inaktivera IPv6-tillstånds lös adress automatisk konfiguration*.

### <a name="manual-ipv6-address-configuration"></a>Manuell konfiguration av IPv6-adress     
Om en specifik IPv6-adress behövs kan programmet använda ***nxd_ipv6_address_set*** för att manuellt konfigurera en IPv6-adress. Ett nätverks gränssnitt kan ha flera IPv6-adresser. Tänk dock på att det totala antalet IPv6-adresser i ett system, antingen erhållna genom tillstånds lös adress konfiguration eller genom manuell konfiguration, inte överskrider ***NX_MAX_IPV6_ADDRESSES***.

I följande exempel visas hur du manuellt konfigurerar en global adress på det primära gränssnittet (enhet 0) i ip_0:

```c
NXD_ADDRESS global_address;
global_address.nxd_ip_version = NX_IP_VERSION_V6;
global_address.nxd_ip_address.v6[0] = 0x20010000;
global_address.nxd_ip_address.v6[1] = 0x00000000;
global_address.nxd_ip_address.v6[2] = 0x00000000;
global_address.nxd_ip_address.v6[3] = 0x0000ABCD;
```

Värden anropar sedan följande NetX Duo-tjänst för att tilldela adressen som global IP-adress:

```c
status = nxd_ipv6_address_set(&ip_0, 0,  
                              &global_address, 64
                              NX_NULL);
```

### <a name="duplicate-address-detection-dad"></a>Duplicerad adress identifiering (pappa)    
När ett system har konfigurerat IPv6-adressen markeras adressen som *preliminär*. Om duplicerad adress identifiering (pappa), som beskrivs i RFC 4862, är aktive rad, skickar NetX Duo automatiskt grann Inbjudnings meddelanden (NS) med den här preliminära adressen som mål. Om inga värdar i nätverket svarar på dessa NS-meddelanden inom en viss tids period, antas adressen vara unik på den lokala länken och dess tillstånds överföring till ett giltigt tillstånd. I det här läget kan programmet börja använda den här IP-adressen för kommunikation.  

Pappa-funktionen är en del av modulen ICMPv6. Programmet måste därför aktivera ICMPv6-tjänster innan en nyligen konfigurerad adress kan gå igenom pappa-processen. Du kan också stänga av pappa-processen genom att definiera ***NX_DISABLE_IPV6_DAD** _ alternativ i versions miljön netx Duo Library (definieras som _*_nx_user. h_*_). Under pappa-processen bestämmer _*_NX_IPV6_DAD_TRANSMITS_*_ -parametern antalet ns-meddelanden som skickats av netx Duo utan att ta emot något svar för att avgöra om adressen är unik. Som standard och rekommenderas av RFC 4862, _ *_NX_IPV6_DAD_TRANSMITS_** anges till 3. Om du anger den här symbolen till noll inaktive ras pappa.

Om ICMPv6 eller pappa inte är aktiverat när programmet tilldelar en IPv6-adress, utförs inte pappa och NetX Duo anger statusen för IPv6-adressen till giltig omedelbart.

NetX Duo kan inte kommunicera med IPv6-nätverket förrän dess länk lokala och/eller globala adress är giltiga. När en giltig adress har erhållits försöker NetX Duo matcha mål adressen för ett inkommande paket mot en av dess konfigurerade IPv6-adress eller en aktive rad multicast-adress. Om inga matchningar hittas ignoreras paketet. 

> [!WARNING]  
> * Under pappa-processen definieras antalet pappa NS-paket som ska överföras av ***NX_IPV6_DAD_TRANSMITS**_, som är standardvärdet 3, och som standard är det en sekund fördröjning mellan varje far ns-meddelande som skickas. I ett system med pappa aktiverat efter att en IPv6-adress har tilldelats (och förutsatt att detta inte är en duplicerad adress), är det cirka 3 sekunder innan IP-adressen är i ett giltigt tillstånd och är klar för kommunikation._

Program kanske vill få meddelanden när IPv6-adresser i systemet ändras. Om du vill aktivera funktionen ändrings meddelande för IPv6-adress måste NetX Duo-biblioteket skapas med symbolen **NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY** definierad. När funktionen är aktive rad kan program installera motringningsfunktionen med hjälp av tjänsten **_nxd_ipv6_address_change_notify_** .

När en IPv6-adress har ändrats eller blir ogiltig, anropas funktionen motringning med följande information:

| Funktion  | Beskrivning  |
|---|---|
|ip_ptr |Pekare till IP-instansen|
|interface_index |Indexera det nätverks gränssnitt som denna IPv6-adress är associerad med
|ipv6_addr_index |Index till IPv6-adress tabellen|
|ipv6_address |Pekare till IPv6-adressen, i form av en matris med fyra ULONG-heltal. Pv6-adresser presenteras i värdens byte ordning.|

### <a name="ipv6-multicast-support-in-netx-duo"></a>Stöd för IPv6-multicast i NetX Duo      
Multicast-adresser anger en dynamisk grupp värdar på Internet. Medlemmar i multicast-gruppen kan ansluta till och lämna när de vill. NetX Duo implementerar flera ICMPv6-protokoll, inklusive dubblettidentifiering, identifiering av grannar och routerupptäckt, som kräver IP-multicast-kapacitet. Därför förväntar NetX Duo den underliggande driv rutinen för att stödja multicast-åtgärder.

När NetX Duo måste ansluta till eller lämna en multicast-grupp (t. ex. multicast-adress för alla noder och den *anropade nodens* multicast-adress), utfärdar den ett driv rutins kommando till enhets driv rutinen för att ansluta till eller lämna en multicast-MAC-adress. Driv rutins kommandot för att ansluta till multicast-adressen är ***NX_LINK_MULTICAST_JOIN** _ _. För att lämna en multicast-adress utfärdar NetX Duo driv rutins kommandot _ *_NX_LINK_MULTICAST_LEAVE_* *. Driv rutinen måste implementera dessa två kommandon för att ICMPv6-protokoll ska fungera korrekt.

Program kan ansluta till en IPv6-multicast-grupp med hjälp av tjänsten ***nxd_ipv6_multicast_interface_join *.** Den här tjänsten registrerar multicast-adressen med IP-stacken och meddelar sedan den angivna driv rutinen för IPv6-multicast-adressen. För att lämna en multicast-grupp använder programmen tjänsten ***nxd_ipv6_multicast_interface_leave.***

### <a name="neighbor-discovery-nd"></a>Neighbor Discovery (ND)    
Neighbor Discovery är ett protokoll i IPv6-nätverk för mappning av fysiska adresser till IPv6-adresserna (global adress eller länk lokal adress). Den här mappningen underhålls i cacheminnet för Neighbor Discovery (ND cache). ND-processen motsvarar ARP-processen i IPv4 och ND-cachen liknar ARP-tabellen. En IPv6-nod kan hämta grannens MAC-adress med hjälp av ND-protokollet (Neighbor Discovery). Den skickar ut ett meddelande om en grann inbjudning (NS) till multicast-adressen för den begärda noden med alla noder och väntar på ett motsvarande meddelande om grann annonsering (NA). MAC-adressen som hämtas genom den här processen lagras i ND-cachen.

Varje IP-instans har en ND-cache. ND-cachen upprätthålls som en matris med poster. Storleken på matrisen definieras vid kompileringen genom att ange alternativet ***NX_IPV6_NEIGHBOR_CACHE_SIZE** _ som i _ *_nx_user. h_* *. Observera att alla gränssnitt som är kopplade till en IP-instans delar samma ND-cache.

Hela ND-cachen är tom när NetX Duo startar. När systemet körs uppdaterar NetX Duo automatiskt ND-cachen, lägger till och tar bort poster enligt varje ND-protokoll. Ett program kan dock också uppdatera ND-cachen genom att manuellt lägga till och ta bort cacheposter med följande NetX Duo-tjänster:

- ***nxd_nd_cache_entry_delete***  
- ***nxd_nd_cache_entry_set***   
- ***nxd_nd_cache_invalidate***

När du skickar och tar emot IPv6-paket uppdaterar NetX Duo automatiskt ND cache-tabellen.

## <a name="internet-control-message-protocol-in-ipv6-icmpv6"></a>Internet Control Message Protocol i IPv6 (ICMPv6)  

Rollen som ICMPv6 i IPv6 har utökats avsevärt för att stödja IPv6-adress mappning och router-identifiering. Dessutom har NetX Duo ICMPv6 stöd för ekobegäran och svar, ICMPv6-fel rapporter och ICMPv6-omdirigerar meddelanden.

### <a name="icmpv6-enable"></a>ICMPv6-aktivering    
Innan ICMPv6-meddelanden kan bearbetas av NetX Duo måste programmet anropa tjänsten ***nxd_icmp_enable*** för att aktivera ICMPv6-bearbetning som förklarat tidigare. 

### <a name="icmpv6-messages"></a>ICMPv6-meddelanden     
Sidhuvud strukturen i ICMPv6 liknar ICMPv4-huvud strukturen. Som visas nedan innehåller det grundläggande ICMPv6-huvudet de tre fälten, typ, kod och kontroll summa, plus varierande längd för ICMPv6-Datadata. 

![Diagram över ett grundläggande ICMPv6-huvud.](./media/user-guide/image19.png)

**BILD 10. Grundläggande ICMPv6-huvud**

|Fält |Storlek (byte) |Beskrivning |
|-----|-----|-----|
|     | 1   |Identifierar typen av ICMPv6-meddelande. |
|     |     |1 mål kan inte kontaktas |
|     |     |2 paketet är för stort |
|     |     |3 tid överskriden |
|     |     |4 parameter problem |
|     |     |128 ECHO-begäran |
|     |     |129 ECHO svar |
|     |     |133 router-inbjudning |
|     |     |134 router-annonsering |
|     |     |135 grann inbjudning |
|     |     |136 grann annonsering |
|     |     |137 omdirigera meddelande |
|Kod | 1   |Ytterligare kvalificerar typen av ICMPv6-meddelande. Används vanligt vis med fel meddelanden. Om den inte används är den inställd på noll. Echo Request/Reply-och NS-meddelanden använder inte det.|
|Kontrollsumma | 2 |16-bitars kontroll Summa fält för ICMP-huvudet. Detta är en 16-bitars komplett av hela ICMPv6-meddelandet, inklusive ICMPv6-huvudet. Den innehåller också ett pseudo-sidhuvud för IPv6-käll adressen, mål adressen och paketets nytto last längd. |

Ett exempel på grann Inbjudnings huvud visas nedan.

![Diagram över ett exempel på grann Inbjudnings huvud.](./media/user-guide/image20.jpg)

**BILD 11. ICMPv6-huvud för ett grann Inbjudnings meddelande**

|Fält |Storlek (byte) |Beskrivning |
|-----|-----|-----|
|Typ | 1   |Identifierar ICMPv6-meddelandets typ för grann Inbjudnings meddelanden. Värdet är 135. |
|Kod | 1   |Används inte. Ange värdet 0. |
|Kontrollsumma | 2  |16-bitars kontroll Summa fält för ICMPv6-huvudet. |
|Reserverat | 4  |4 reserverade byte har angetts till 0. |
|Mål adress | 16  |IPv6-adress till målet för inbjudningen. För IPv6-adress matchning är detta den faktiska unicast-IP-adressen för enheten vars länk skikts adress måste matchas. |
|Alternativ | Variabel |Valfri information som anges av Neighbor Discovery-protokollet. |

### <a name="icmpv6-ping-request"></a>ICMPv6 ping-begäran
I NetX Duo-program används ***nxd_icmp_ping*** för att utfärda antingen IPv6-eller IPv4-ping-förfrågningar, baserat på den mål-IP-adress som anges i parametrarna.  

### <a name="icmpv6-ping-response"></a>Ping-svar för ICMPv6
Ett ICMPv6-ping-svar är en annan typ av ICMPv6-meddelande som genereras internt av ICMPv6-komponenten som svar på en extern ICMPv6-ping-begäran. I tillägg till bekräftelse innehåller ICMPv6 ping-svaret även en kopia av de användar data som angavs i ICMPv6-ping-begäran.  

### <a name="thread-suspension"></a>Tråd upphängning
Program trådar kan pausas vid försök att pinga en annan nätverks medlem. När ett ping-svar har tagits emot får ping-svarsmeddelandet den första tråden pausad och tråden återupptas. Precis som alla NetX Duo-tjänster är det en valfri timeout att pausa vid en ping-begäran.  

### <a name="other-icmpv6-messages"></a>Andra ICMPv6-meddelanden
ICMPv6-meddelanden krävs för följande funktioner:  

- Identifiering av grannar  
- Automatisk adress konfiguration för tillstånd 
- Routerupptäckt 
- Identifiering av grann tillgänglighet  

### <a name="neighbor-unreachability-router-and-prefix-discovery"></a>Grannen kan inte kontaktas, router-och prefix identifiering    
Identifiering av grannars tillgänglighet, routerupptäckt och identifiering av prefix baseras på Neighbor Discovery-protokollet och beskrivs nedan. 

***Identifiering av grann tillgänglighet:*** En IPv6-enhet söker igenom den angränsande identifierings-cachen (ND) för mål länk skikt adressen när du vill skicka ett paket. Det omedelbara målet, som ibland kallas "nästa hopp", kan vara den faktiska destinationen på samma länk, eller så kan det vara en router om målet är av länken. En ND cache-post innehåller status för en grannens tillgänglighet.

En NÅBAR status anger att grannen betraktas som nåbar. Det går att få åtkomst till en granne om den nyligen har fått en bekräftelse på att paket som skickats till grannen har tagits emot. Bekräftelse i NetX Duo tar emot ett NA-meddelande från grannen som svar på ett NS-meddelande som skickats av NetX Duo-enheten. NetX Duo kommer också att ändra status för grannens status till att kunna UPPNÅs om programmet anropar NetX Duo-tjänsten ***nxd_nd_cache_entry_set*** att ange en cachepost manuellt.

***Routerupptäckt:*** En IPv6-enhet använder en router för att vidarebefordra alla paket som är avsedda för av länk destinationer. Den kan också använda information som skickas av routern, till exempel meddelanden om routerannonsering (RA) för att konfigurera dess globala IPv6-adresser.

En enhet i nätverket kan initiera identifierings processen för routern genom att skicka ett RS-meddelande (router inbjudningar) till multicast-adressen all router (FF01:: 2). Eller så kan den vänta på multicast-adressen för alla noder (FF:: 1) för en periodisk RA från routrarna.

Ett RA-meddelande innehåller prefixs information för att konfigurera en IPv6-adress för nätverket. I NetX Duo är Routerinbjudning aktiverat som standard och kan inaktive ras genom att ställa in konfigurations alternativet ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _ i _ *_nx_user. h_* *. Se konfigurations alternativ i kapitlet "installera och använda NetX Duo" för mer information om att ställa in parametrar för router-inbjudningar. 

***Prefix identifiering***: en IPv6-enhet använder prefix identifiering för att lära sig vilka mål värdar som är tillgängliga direkt utan att gå via en router. Den här informationen görs tillgänglig för IPv6-enheten från RA-meddelanden från routern. IPv6-enheten lagrar prefixlängden i en tabell med prefix. Prefixet som identifieras matchar ett prefix från tabellen IPv6-enhets prefix till en mål adress. Ett prefix matchar en mål adress om alla bitar i prefixet matchar de mest signifikanta bitarna i mål adressen. Om fler än ett prefix täcker en adress väljs det längsta prefixet.

### <a name="icmpv6-error-messages"></a>Fel meddelanden för ICMPv6    
Följande ICMPv6-fel meddelanden stöds i NetX Duo:  

- Det går inte att hitta målet  
- Paketet är för stort  
- Tiden överskrider  
- Parameter problem  

## <a name="user-datagram-protocol-udp"></a>UDP (User Datagram Protocol)

UDP (User Datagram Protocol) ger den enklaste formen av data överföring mellan nätverks medlemmar (RFC 768). UDP-datapaket skickas från en nätverks medlem till en annan på bästa möjliga sätt. Det finns alltså ingen inbyggd mekanism för bekräftelse av paket mottagaren. Att skicka ett UDP-paket kräver dessutom inte att någon anslutning upprättas i förväg. Därför är det mycket effektivt att överföra UDP-paket.

För utvecklare som migrerar sina NetX-program till NetX Duo finns det bara några få grundläggande ändringar i UDP-funktioner mellan NetX och NetX Duo. Detta beror på att IPv6 främst berör det underliggande IP-lagret. Alla NetX Duo UDP-tjänster kan användas för antingen IPv4-eller IPv6-anslutning.

### <a name="udp-header"></a>UDP-huvud       
UDP placerar ett enkelt paket huvud framför programmets data vid överföring och tar bort ett liknande UDP-huvud från paketet vid mottagning innan ett mottaget UDP-paket levereras till programmet. UDP använder IP-protokollet för att skicka och ta emot paket, vilket innebär att det finns ett IP-huvud framför UDP-huvudet när paketet är i nätverket. Bild 12 visar UDP-huvudets format.

![Diagram över UDP-huvudformatet.](./media/user-guide/image21.png)

### <a name="figure-12-udp-header"></a>FIGUR 12. UDP-huvud

> [!NOTE]
> *Alla rubriker i UDP/IP-implementeringen förväntas vara i **big endian** format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen.*

I följande avsnitt beskrivs UDP-huvudets format:

|Rubrik fält |Syfte |
|---|---|
|**16-bitars käll port nummer** |Det här fältet innehåller porten som UDP-paketet skickas från. Giltiga UDP-portar sträcker sig från 1 till 0xFFFF. |
|**16-bitars mål port nummer** |Det här fältet innehåller den UDP-port som paketet skickas till. Giltiga UDP-portar sträcker sig från 1 till 0xFFFF. |
|**16-bitars UDP-längd** |Det här fältet innehåller antalet byte i UDP-paketet, inklusive storleken på UDP-huvudet. |
|**16-bitars UDP-kontrollsumma** |Det här fältet innehåller 16-bitars kontroll summa för paketet, inklusive UDP-huvudet, paket data området och pseudo-IP-huvudet. |

### <a name="udp-enable"></a>Aktivera UDP   
Innan överföring av UDP-paket är möjligt måste programmet först aktivera UDP genom att anropa tjänsten ***nx_udp_enable*** . När det har Aktiver ATS är programmet fritt att skicka och ta emot UDP-paket.  

### <a name="udp-socket-create"></a>Skapa UDP-socket    
UDP-Sockets skapas antingen under initieringen eller under körningen av program trådar. Den första typen av tjänst, Time to Live och Receive Queue djup definieras av tjänsten ***nx_udp_socket_create*** . Det finns ingen gräns för antalet UDP-socketar i ett program.

### <a name="udp-checksum"></a>UDP-kontrollsumma   
IPv6-protokollet kräver en beräkning av kontroll summa för UDP-huvud på paket data, men i IPv4-protokollet är det valfritt.  

UDP anger en komplett 16-bitars kontroll summa som täcker IP-pseudo-huvudet (som består av käll-IP-adressen, målets IP-adress och protokoll/längd-IP-adress), UDP-huvudet och UDP-paketets data. De enda skillnaderna mellan kontroll summor för IPv4-och IPv6-paket huvud är att käll-och mål-IP-adresserna är 32 bitar i IPv4 medan de är 128 bitar i IPv6. Om den beräknade UDP-kontrollsumman är 0 lagras den som alla (0xFFFF). Om inaktive ring av UDP-kontrollsumma är inaktive rad placeras noll i fältet UDP-kontrollsumma för att indikera att kontroll summan inte har beräknats.

Om UDP-kontrollsumma inte matchar den beräknade kontroll summan av mottagaren, ignoreras UDP-paketet helt enkelt.

I IPv4-nätverket är UDP-kontrollsumma valfri. NetX Duo gör det möjligt för ett program att aktivera eller inaktivera beräkning av UDP-kontrollsumma per socket. Som standard är logiken för kontroll summa för UDP aktiverat. Programmet kan inaktivera logik för kontroll summa för en viss UDP-socket genom att anropa tjänsten ***nx_udp_socket_checksum_disable** _. I IPv6-nätverket är dock kontroll summan av UDP obligatorisk. Därför kommer tjänsten _ *_nx_udp_socket_checksum_disable_** inte att inaktivera logik för kontroll summa för UDP när ett paket skickas via IPv6-nätverket.

Vissa Ethernet-styrenheter kan generera UDP-kontrollsumma i farten. Om systemet kan använda beräknings funktionen för maskin varu kontroll summa kan NetX Duo-biblioteket skapas utan logik för kontroll summa. Om du vill inaktivera kontroll summa för UDP-programvara måste NetX Duo-biblioteket vara byggt med följande symboler: ***NX_DISABLE_UDP_TX_CHECKSUM** _ och _*_NX_DISABLE_UDP_RX_CHECKSUM_*_ (beskrivs i kapitel två). Konfigurations alternativen tar bort UDP-kontrollsumma från NetX Duo helt och hållet, samtidigt som du anropar tjänsten _ *_nx_udp_socket_checksum_disable_** så att programmet kan inaktivera bearbetning av IPv4 UDP-kontrollsumma per socket.

### <a name="udp-ports-and-binding"></a>UDP-portar och bindning      
En UDP-port är en logisk slut punkt i UDP-protokollet. Det finns 65 535 giltiga portar i UDP-komponenten för NetX Duo, mellan 1 och 0xFFFF. Om du vill skicka eller ta emot UDP-data måste programmet först skapa en UDP-socket och sedan binda den till en önskad port. När du har bundit en UDP-socket till en port kan programmet skicka och ta emot data på denna socket.

### <a name="udp-fast-pathtrade"></a>Snabb sökväg för UDP&trade;   
Snabb sökvägen för UDP &trade; är namnet på en låg paket väg genom netx Duo UDP-implementeringen. Att skicka ett UDP-paket kräver bara några funktions anrop: ***nx_udp_socket_send** _, _*_nx_ip_packet_send_*_ och det eventuella anropet till nätverks driv rutinen. _*_nx_udp_socket_send_*_ är tillgängligt i netx Duo för befintliga netx-program och gäller endast för IPv4-paket. Den bästa metoden är dock att använda _ *_nxd_udp_socket_send_** tjänsten som diskuteras nedan. Vid mottagning av UDP-paket placeras UDP-paketet antingen på lämplig UDP socket Receive-kö eller levereras till en inaktive rad program tråd i ett enda funktions anrop från nätverks driv Rutinens mottagnings bearbetning. Den här mycket optimerade logiken för att skicka och ta emot UDP-paket är grunden för en snabb väg teknik för UDP.  

### <a name="udp-packet-send"></a>Skicka UDP-paket    
Att skicka UDP-data via IPv6 eller IPv4-nätverk kan enkelt utföras genom att anropa funktionen ***nxd_udp_socket_send** _. Anroparen måste ange IP-versionen i fältet _nx_ip_version * i NXD_ADDRESS pekarpost-parametern. NetX Duo avgör den bästa käll adressen för överförda UDP-paket baserat på IPv4/IPv6-adress för målet. Den här tjänsten placerar ett UDP-huvud framför paket data och skickar det till nätverket med en intern IP-sändnings rutin. Det finns ingen tråd Inskjutning vid sändning av UDP-paket eftersom alla UDP-paketfiltrering bearbetas omedelbart. 

För multicast-eller broadcast-mål ska programmet ange vilken käll-IP-adress som ska användas om NetX Duo-enheten har flera IP-adresser att välja mellan. Detta kan göras med tjänsterna ***nxd_udp_socket_source_send.***

> [!IMPORTANT]    
> *Om **nx_udp_socket_send** används för att överföra multicast-eller broadcast-paket används IP-adressen för det första aktiverade gränssnittet som käll adress*.

> [!NOTE] 
> *Om logics kontroll summa för UDP är aktive rad för denna socket utförs åtgärden för kontroll summa i kontexten för den anropande tråden, utan att blockera åtkomst till UDP-eller IP-datastrukturerna*. 

> [!WARNING]    
> *De UDP-nyttolaster som finns i NX_PACKETs strukturen bör finnas på ett långt ord. Programmet måste lämna tillräckligt med utrymme mellan lägga-pekaren och data start pekaren för NetX Duo för att placera både UDP-, IP-och fysiska medie huvudena*.

### <a name="udp-packet-receive"></a>Mottagning av UDP-paket    
Program trådar kan ta emot UDP-paket från en viss socket genom att anropa ***nx_udp_socket_receive***. Funktionen Receive Receive levererar det äldsta paketet i socketens mottagnings kön. Om det inte finns några paket i mottagnings kön kan den anropande tråden skjuta upp (med en valfri tids gräns) tills ett paket tas emot.

Bearbetningen av UDP Receive-paket (som vanligt vis anropas från nätverks driv Rutinens avbrotts hanterare) är ansvarig för att antingen placera paketet på UDP-socketens mottagnings kö eller leverera den till den första pausade tråden för ett paket. Om paketet är i kö, kontrollerar Receive-bearbetningen även det maximala mottagnings ködjup som är associerat med socketen. Om det nyligen köade paketet överskrider ködjup, ignoreras det äldsta paketet i kön.

### <a name="udp-receive-notify"></a>Mottagnings meddelande för UDP   
Om program tråden behöver bearbeta mottagna data från fler än en socket ska funktionen ***nx_udp_socket_receive_notify*** användas. Den här funktionen registrerar en motringnings funktion för mottagnings paket för socketen. När ett paket tas emot på socketen körs motringningsfunktionen.

Innehållet i motringningsfunktionen är applicationspecific; Det skulle dock förmodligen innehålla logik för att informera bearbetnings tråden att ett paket nu är tillgängligt på motsvarande socket.

### <a name="peer-address-and-port"></a>Peer-adress och port   
Vid mottagning av ett UDP-paket kan programmet hitta avsändarens IP-adress och port nummer med hjälp av tjänsten ***nx_udp_packet_info_extract***. Vid lyckad återgång tillhandahåller den här tjänsten information om avsändarens IP-adress, avsändarens port nummer och det lokala gränssnitt som paketet togs emot via.  

### <a name="thread-suspension"></a>Tråd upphängning   
Som tidigare nämnts kan program trådar pausa vid försök att ta emot ett UDP-paket på en viss UDP-port. När ett paket har mottagits på den porten, tilldelas den första tråden inaktive rad och tråden återupptas sedan. En valfri timeout är tillgänglig när du pausar ett UDP-paket, en funktion som är tillgänglig för de flesta NetX Duo-tjänster.  

### <a name="udp-socket-statistics-and-errors"></a>Statistik och fel för UDP-socket     
Om den här inställningen är aktive rad håller NetX Duo UDP socket-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter upprätthålls för varje IP/UDP-instans:

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

Alla dessa statistik-och fel rapporter är tillgängliga för programmet med ***nx_udp_info_get** _-tjänsten för UDP-amassed över alla UDP-socketar och _ *_nx_udp_socket_info_get_**-tjänsten för UDP-statistik på den angivna UDP-socketen.

### <a name="udp-socket-control-block-nx_udp_socket"></a>UDP socket Control Block NX_UDP_SOCKET
Egenskaperna för varje UDP-socket finns i det associerade NX_UDP_SOCKET kontroll blocket. Den innehåller användbar information, till exempel länken till IP-datastrukturen, nätverks gränssnittet för att skicka och ta emot sökvägar, den kopplade porten och kön för mottagnings paket. Den här strukturen definieras i filen ***nx_api. h*** .

## <a name="transmission-control-protocol-tcp"></a>Transmission Control Protocol (TCP)

Transmission Control Protocol (TCP) ger tillförlitlig data överföring mellan två nätverks medlemmar (RFC 793). Alla data som skickas från en nätverks medlem verifieras och bekräftas av den mottagande medlemmen. Dessutom måste de två medlemmarna ha upprättat en anslutning före en data överföring. Allt detta resulterar i tillförlitlig data överföring. Det kräver dock betydligt mer belastning än den tidigare beskrivna UDP-dataöverföringen.

Om inget annat anges sker inga ändringar i API-tjänsterna för TCP-protokollet mellan NetX och NetX Duo, eftersom IPv6 främst berör det underliggande IP-skiktet. Alla NetX Duo TCP-tjänster kan användas för antingen IPv4-eller IPv6-anslutningar.

### <a name="tcp-header"></a>TCP-huvud   
Vid överföring placeras TCP-huvud framför data från användaren. Vid mottagning tas TCP-huvud bort från det inkommande paketet, och endast de användar data som är tillgängliga för programmet lämnas kvar. TCP använder IP-protokollet för att skicka och ta emot paket, vilket innebär att det finns ett IP-huvud framför TCP-huvudet när paketet är i nätverket. Bild 13 visar formatet för TCP-sidhuvudet.

![Diagram över TCP-huvudformatet.](./media/user-guide/image22.png)

### <a name="figure-13-tcp-header"></a>FIGUR 13. TCP-huvud

I följande avsnitt beskrivs formatet TCP-huvud:

|Rubrik &nbsp; fält |Syfte |
|------|------|
| **16-bitars käll port nummer** | Det här fältet innehåller den port som TCP-paketet skickas till. Giltiga TCP-portar är mellan 1 och 0Xffffffff. |
| **16-bitars målport** | Det här fältet innehåller TCP-porten som paketet skickas till. Giltiga TCP-portar är mellan 1 och 0Xffffffff. |
| **32-bitars sekvensnummer** | Det här fältet innehåller sekvensnumret för data som skickas från det här slutet av anslutningen. Den ursprungliga sekvensen upprättas under den inledande anslutnings ordningen mellan två TCP-noder. Varje data överföring från den punkten resulterar i en ökning av sekvensnumret med antalet byte som skickats. |
| **32-bitars bekräftelse nummer** | Det här fältet innehåller det ordnings nummer som motsvarar den sista mottagna byte som togs emot av anslutningen. Detta används för att avgöra om data som skickats tidigare har tagits emot av den andra änden av anslutningen. |
| **4-bitars rubrik längd** | Det här fältet innehåller antalet 32-bitars ord i TCP-huvudet. Om det inte finns några alternativ i TCP-huvudet är det här fältet 5. |
| **6-bitars kod bitar** |Det här fältet innehåller sex olika kod bitar som används för att ange olika kontroll information som är associerad med anslutningen. Kontroll bitarna definieras enligt följande: <br \> -URG (21): brådskande data preset<br \> -ack (20): bekräftelse numret är giltigt<br \> -PSH (19): hantera dessa data direkt<br-20-25 \> (18): Återställ anslutningen<br \> -syn (17): synkronisera sekvensnumret (används för att upprätta anslutning) <br \> -räntetrans (16): avsändaren har slutförts med överföring (används för att stänga anslutningen) |
|**16-bitars fönster** |Det här fältet används för flödes kontroll. Det innehåller mängden byte som socketen kan ta emot för närvarande. Detta används i princip för flödes kontroll. Avsändaren ansvarar för att se till att de data som skickas får plats i mottagarens annonserade fönster. |
|**16-bitars TCP-kontrollsumma** |Det här fältet innehåller 16-bitars kontroll summa för paketet, inklusive TCP-huvud, paket data området och pseudo-IP-huvudet. |
|**16-bitars brådskande pekare** |Det här fältet innehåller den positiva förskjutningen för den senaste byten av brådskande data. Det här fältet är endast giltigt om URG-kodfragmentet har angetts i huvudet. |

> [!NOTE]  
> *Alla rubriker i TCP/IP-implementeringen förväntas vara i **big endian** format. I det här formatet finns de mest signifikanta byten av ordet på den lägsta byte-adressen*.

### <a name="tcp-enable"></a>TCP-aktivering       
Innan TCP-anslutningar och paket överföring är möjliga måste programmet först aktivera TCP genom att anropa tjänsten ***nx_tcp_enable*** . När det har Aktiver ATS är programmet tillgängligt för att få åtkomst till alla TCP-tjänster.  

### <a name="tcp-socket-create"></a>Skapa TCP-socket    
TCP-Sockets skapas antingen under initieringen eller under körningen av program trådar. Den första typen av tjänst, tid till Live och fönster storlek definieras av tjänsten ***nx_tcp_socket_create*** . Det finns ingen gräns för antalet TCP-Sockets i ett program.  

### <a name="tcp-checksum"></a>TCP-kontrollsumma     
TCP anger en komplett 16-bitars kontroll summa som täcker IP-pseudo-sidhuvudet (som består av käll-IP-adressen, målets IP-adress och protokoll/längd-IP-adress), TCP-huvudet och TCP-paketets data. Den enda skillnaden mellan IPv4-och IPv6-paketets kontroll summor är att käll-och mål-IP-adresserna är 32 bitar i IPv4 och 128 bitar i IPv6. 

Vissa nätverks styrenheter kan utföra beräkning av TCP-kontrollsumma och verifiering i maskin vara. För sådana system kan program använda sig av logik för maskin varu kontroll så mycket som möjligt för att minska körnings belastningen. Program kan inaktivera beräknings logiken för TCP-kontrollsumma från NetX Duo-biblioteket helt vid Bygg tiden genom att definiera ***NX_DISABLE_TCP_TX_CHECKSUM** _ och _ *_NX_DISABLE_TCP_RX_CHECKSUM_* *. På så sätt kompileras inte TCP-kontrollsummats kod i. En bör dock vara försiktig om det valfria NetX Duo-paketet är installerat och TCP-anslutningen kan behöva passera via en säker kanal. I det här fallet är data i paket som tillhör TCP-anslutningen redan krypterade och de flesta moduler för maskin varu-TCP-kontrollsumma som finns i nätverks driv rutinen kan inte generera korrekt kontroll Summa värde från den krypterade TCP-nyttolasten.

För att lösa det här problemet måste programmet behålla logiken för kontroll summa för att vara tillgänglig i biblioteket och använda funktionen gränssnitts funktion. Med funktionen gränssnitts kapacitet aktive rad vet TCP-modulen hur TCP-kontrollsumma hanteras korrekt om driv rutinen också kan beräkna kontroll summan:

1) Om TCP-paketet inte omfattas av IPsec-processen kan maskin varan för nätverks gränssnittet beräkna kontroll summan. Därför försöker inte TCP-modulen beräkna kontroll summan.

2) Om IPsec-paketet är installerat och TCP-paketet omfattas av IPsec-processen beräknar TCP-modulen kontroll summor i program vara innan paketet skickas till IPsec-lagret.

### <a name="tcp-port"></a>TCP-port     
En TCP-port är en logisk anslutnings punkt i TCP-protokollet. Det finns 65 535 giltiga portar i TCP-komponenten för NetX Duo, mellan 1 och 0xFFFF. Till skillnad från UDP där data från en port kan skickas till en annan målport, är en TCP-port ansluten till en annan angiven TCP-port, och endast när den här anslutningen upprättas kan all data överföring ske, och endast mellan de två portarna som utgör anslutningen.

> [!IMPORTANT]
> *TCP-portar är helt åtskilda från UDP-portar, t. ex. UDP-port nummer 1 har ingen relation till TCP-port nummer 1*.

### <a name="client-server-model"></a>Client-Server modell     
Om du vill använda TCP för data överföring måste du först upprätta en anslutning mellan de två TCP-socketarna. Upprättandet av anslutningen görs på en klient-server. Klient sidan av anslutningen är den sida som initierar anslutningen, medan Server sidan bara väntar på klient anslutnings begär Anden innan bearbetningen görs.

> [!IMPORTANT]
> *För multihome-enheter bestämmer netx Duo automatiskt käll adressen som ska användas för anslutningen och nästa hopp adress baserat på anslutningens mål-IP-adress. Eftersom TCP är begränsat till att skicka paket till unicast-mål adresser (t. ex. icke-broadcast), kräver NetX Duo inte något "tips" för att välja källans IPv6-adress*.

### <a name="tcp-socket-state-machine"></a>TCP socket State Machine      
Anslutningen mellan två TCP-Sockets (en klient och en server) är komplex och hanteras på ett sätt som är en tillstånds dator. Varje TCP-socket startar i ett stängt tillstånd. Via anslutnings händelser varje Sockets tillstånds dator migreras till ett etablerat tillstånd, vilket är den mängd data överföringen i TCP äger rum. När en sida av anslutningen inte längre vill skicka data, kopplas den bort. När den andra sidan kopplas från återgår TCP-socketen till stängt tillstånd. Den här processen upprepas varje gång en TCP-klient och Server upprättar och stänger en anslutning. Bild 14 visar de olika tillstånden för datorn för TCP-tillstånd.

### <a name="tcp-client-connection"></a>TCP-klient anslutning       
Som tidigare nämnts, initierar klient sidan av TCP-anslutningen en anslutningsbegäran till en TCP-server. Innan en anslutningsbegäran kan göras måste TCP aktive ras på klientens IP-instans. Dessutom måste klienten TCP-socketen sedan skapas med ***nx_tcp_socket_create** _-tjänsten och vara kopplad till en port via tjänsten _ *_nx_tcp_client_socket_bind_**.

När klient-socketen är kopplad, används tjänsten ***nxd_tcp_client_socket_connect*** för att upprätta en anslutning till en TCP-server. Observera att socketen måste vara i stängt tillstånd för att ett anslutnings försök ska kunna initieras. Upprättandet av anslutningen börjar med NetX Duo som utfärdar ett SYN paket och väntar sedan på ett SYN ACK-paket tillbaka från servern, vilket innebär att anslutningsbegäran tas emot. När SYN ACK tar emot svarar NetX Duo med ett ACK-paket och höjer upp klientens socket till tillståndet etablerad.

![Diagram över tillstånden för TCP-tillstånds datorn.](./media/user-guide/image24.png)   

**BILD 14. Tillstånd för TCP-tillstånds dator**


> [!WARNING]
> *Program bör använda **Nxd_tcp_client_socket_connect** för IPv4-och IPv6 TCP-anslutningar. Program kan fortfarande använda **nx_tcp_client_socket_connect** för IPv4 TCP-anslutningar, men utvecklare uppmuntras att använda **nxd_tcp_client_socket_connect** eftersom **nx_tcp_client_socket_connect** slutligen kommer att bli föråldrad*.

*På samma sätt fungerar **nxd_tcp_socket_peer_info_get** med antingen IPv4-eller IPv6 TCP-anslutningar. **Nx_tcp_socket_peer_info_get** är dock fortfarande tillgängligt för äldre program. Utvecklare uppmanas att använda **nxd_tcp_socket_peer_info_get** framåt*.

### <a name="tcp-client-disconnection"></a>TCP-klient från koppling    
Att stänga anslutningen uppnås genom att anropa ***nx_tcp_socket_disconnect***. Om ingen uppskjutning har angetts skickar klient-socketen ett för-paket till Server-socketen och placerar socketen i stängt tillstånd. Annars, om en SUS Pension begärs, utförs det fullständiga TCP-från kopplings protokollet enligt följande: 

- Om servern tidigare initierade en från kopplings förfrågan (klient-socketen redan har tagit emot ett RÄNTETRANS-paket, svarat på en ACK och är i nära VÄNTe läge), höjer NetX Duo klientens TCP socket-tillstånd till det senaste bekräftelse stadiet och skickar ett RÄNTETRANS-paket. Den väntar sedan på en bekräftelse från servern innan du slutför från kopplingen och anger det stängda läget.

- Om klienten å andra sidan är den första för att initiera en från kopplings förfrågan (servern har inte kopplats från och socketen fortfarande är i det tillstånd som har ETABLERATs), skickar NetX Duo ett RÄNTETRANS-paket för att initiera från kopplingen och väntar på att ta emot en FIN och en bekräftelse från servern innan du slutför från kopplingen och placera socketen i ett stängt tillstånd.

Om det fortfarande finns paket i kön för överföring av socket, pausar NetX Duo under den angivna tids gränsen för att tillåta att paketen kan bekräftas. Om tids gränsen går ut tömmer NetX Duo överförings kön för klientens socket. 

Programmet anropar ***nx_tcp_client_socket_unbind*** för att frigöra porten från klientens socket. Socketen måste vara i ett stängt tillstånd eller vid från koppling (t. ex. VÄNTe läge VÄNTe tid) innan porten släpps. annars returneras ett fel.

Slutligen, om programmet inte längre behöver klient-socketen, anropar den ***nx_tcp_socket_delete*** för att ta bort socketen.

### <a name="tcp-server-connection"></a>Anslutning till TCP-server      
Server sidan av en TCP-anslutning är passiv; servern väntar alltså på att en klient ska initiera anslutningsbegäran. Om du vill acceptera en klient anslutning måste TCP först vara aktiverat på IP-instansen genom att anropa tjänsten ***nx_tcp_enable** _. Därefter måste programmet skapa en TCP-socket med hjälp av _ *_nx_tcp_socket_create_**-tjänsten.  

Server-socketen måste också konfigureras för att lyssna efter anslutnings begär Anden. Detta uppnås med hjälp av tjänsten ***nx_tcp_server_socket_listen*** . Den här tjänsten placerar serverns socket i LYSSNINGs tillstånd och binder den angivna Server porten till socketen.

> [!NOTE] 
> *Om du vill ange en utgångs rutin för socket-motringning anger programmet lämplig motringning för argumentet tcp_listen_callback i **nx_tcp_server_socket_listens** tjänsten. Den här program återanrops funktionen körs sedan av NetX Duo när en ny anslutning begärs på den här Server porten. Bearbetningen i återanropet är under program kontroll.*

För att godkänna förfrågningar om klient anslutning anropar programmet ***nx_tcp_server_socket_accept** _-tjänsten. Server-socketen måste antingen vara i ett LYSSNINGs tillstånd eller tillstånd som tagits emot (dvs. servern är i LYSSNINGs tillståndet och har tagit emot ett SYN paket från en klient som begär en anslutning) för att anropa tjänsten accept. En lyckad retur status från _ *_nx_tcp_server_socket_accept_** anger att anslutningen har kon figurer ATS och att serverns socket har tillståndet etablerad.

När Server-socketen har en giltig anslutning, köas ytterligare klient anslutnings begär anden till det djup som anges av *listen_queue_size, som skickas till*  * **nx_tcp_server_socket_listen** _-tjänsten. För att kunna bearbeta efterföljande anslutningar på en server port måste programmet anropa _ *_nx_tcp_server_socket_relisten_** med en tillgänglig socket (t. ex. en socket i ett stängt tillstånd). Observera att samma server-socket kan användas om den tidigare anslutningen som är associerad med socketen nu är slutförd och socketen är i stängt tillstånd.

### <a name="tcp-server-disconnection"></a>AvAnslutning av TCP-server     
Att stänga anslutningen uppnås genom att anropa ***nx_tcp_socket_disconnect***. Om ingen uppskjutning har angetts skickar Server-socketen ett för-paket till klientens socket och placerar socketen i stängt tillstånd. Annars, om en SUS Pension begärs, utförs det fullständiga TCP-från kopplings protokollet enligt följande:

- Om klienten tidigare initierade en från kopplings förfrågan (Server-socketen redan har tagit emot ett RÄNTETRANS-paket, svarat på en ACK och är i nära VÄNTe läge), höjer NetX Duo TCP-socketen till det senaste bekräftelse stadiet och skickar ett RÄNTETRANS-paket. Den väntar sedan på en bekräftelse från klienten innan du slutför från kopplingen och anger det stängda läget.

- Om servern å andra sidan är den första att initiera en från kopplings förfrågan (klienten har inte kopplats från och att socketen fortfarande är i det tillstånd som har ETABLERATs), skickar NetX Duo ett RÄNTETRANS-paket för att initiera från kopplingen och väntar på att ta emot en FIN och en bekräftelse från klienten innan du slutför från kopplingen och placera socketen i ett stängt tillstånd.

Om det fortfarande finns paket i kön för överföring av socket, pausar NetX Duo under den angivna tids gränsen för att tillåta att dessa paket bekräftas. Om tids gränsen går ut tömmer NetX Duo Server-socketens överförings kön.

När från kopplings bearbetningen har slutförts och Server-socketen är i stängt tillstånd måste programmet anropa tjänsten ***nx_tcp_server_socket_unaccept** _ för att avsluta associationen mellan denna socket och Server porten. OBS! den här tjänsten måste anropas av programmet även om _*_nx_tcp_socket_disconnect_*_ eller _*_nx_tcp_server_socket_accept_*_ returnera en fel status. När _*_nx_tcp_server_socket_unaccept_*_ returnerar kan socketen användas som en klient eller Server-socket, eller till och med tas bort om den inte längre behövs. Om du vill acceptera en annan klient anslutning på samma server port bör du anropa tjänsten _ *_nx_tcp_server_socket_relisten_** på denna socket.

Följande kod segment illustrerar sekvensen av anrop en typisk TCP-server använder:

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

### <a name="mss-validation"></a>MSS-verifiering      
Maximal segment storlek (MSS) är den maximala mängden byte som en TCP-värd kan ta emot utan att fragmenteras av det underliggande IP-lagret. Under fasen för etablering av TCP-anslutningar, avslutar båda sina egna TCP-MSS-värden, så att avsändaren inte skickar ett TCP-datasegment som är större än mottagarens MSS. Med NetX Duo TCP-modulen kan du välja att validera dess peers annonserade MSS-värde innan du upprättar en anslutning. Som standard ger NetX Duo ingen sådan kontroll. Program som vill utföra MSS-verifieringen måste definiera ***NX_ENABLE_TCP_MSS_CHECK** _ när du skapar netx Duo-biblioteket och det minsta värdet måste definieras i _*_NX_TCP_MSS_MINIMUM_*_. Inkommande TCP-anslutningar med MSS-värden under _ *_NX_TCP_MSS_MINIMUM_** ignoreras.

### <a name="stop-listening-on-a-server-port"></a>Stoppa lyssning på en server port    
Om programmet inte längre vill lyssna efter klient anslutnings begär Anden på en server port som tidigare angavs av ett anrop till tjänsten ***nx_tcp_server_socket_listen** _, anropar programmet bara tjänsten _ *_nx_tcp_server_socket_unlisten_**. Den här tjänsten placerar en socket i väntan på en anslutning tillbaka i stängt tillstånd och släpper alla paket med köade klient anslutnings begär Anden. 

### <a name="tcp-window-size"></a>TCP-fönster storlek   
Under både installationen och data överförings faserna i anslutningen, rapporterar varje port mängden data som kan hanteras, vilket kallas dess fönster storlek. När data tas emot och bearbetas justeras den här fönstrets storlek dynamiskt. I TCP kan en sändare bara skicka en mängd data som passar i mottagarens fönster. I själva verket ger fönster storleken flödes kontroll för data överföring i varje riktning i anslutningen.   

### <a name="tcp-packet-send"></a>Skicka TCP-paket     
Det är enkelt att skicka TCP-data genom att anropa funktionen ***nx_tcp_socket_send*** . Om storleken på de data som överförs är större än MSS-värdet för socketen eller den aktuella peer-mottagande fönster storlek, beroende på vilket som är mindre, är TCP Internal Logic carves av data som passar i min (MSS, peer Receive-fönster) för överföring. Den här tjänsten skapar sedan ett TCP-huvud framför paketet (inklusive beräkning av kontroll summa). Om mottagarens fönster storlek inte är noll, skickar anroparen lika mycket data som det kan fylla i mottagarens fönster storlek. Om mottagnings fönstret blir noll kan anroparen pausa och vänta tills mottagarens fönster storlek ökar tillräckligt för att det här paketet ska skickas. Vid en specifik tidpunkt kan flera trådar pausas vid försök att skicka data via samma socket. 

> [!WARNING]  
> *De TCP-data som finns i NX_PACKETs strukturen bör finnas på en lång ord linje. Dessutom måste det finnas tillräckligt med utrymme mellan lägga-pekaren och data start pekaren för att placera rubrikerna TCP, IP och fysisk media*.

### <a name="tcp-packet-retransmit"></a>Återsändning av TCP-paket      
Tidigare skickade TCP-paket som faktiskt lagrats internt tills en ACK returneras från den andra sidan av anslutningen. Om överförda data inte har bekräftats inom tids gränsen, skickas det lagrade paketet igen och nästa timeout-period anges. När en ACK tas emot släpps slutligen alla paket som omfattas av bekräftelse numret i den interna överförings kön.  

> [!WARNING]   
> *Programmet får inte återanvända paketet eller ändra paketets innehåll efter nx_tcp_socket_send () returnerar NX_SUCCESS. Det överförda paketet släpps slutligen av NetX Duo intern bearbetning när data har bekräftats av den andra parten*.

### <a name="tcp-keepalive"></a>TCP keepalive     
TCP keepalive-funktionen gör det möjligt för en socket att identifiera om dess peer-kopplas bort utan korrekt avslutning (t. ex. om motparten har kraschat) eller för att förhindra vissa nätverks övervaknings anläggningar att avsluta en anslutning under långa perioder av inaktivitet. TCP keepalive fungerar genom att regelbundet skicka en TCP-ram utan data, och sekvensnumret anges till ett lägre värde än det aktuella sekvensnumret. När en sådan TCP keepalive-ram tas emot, kan mottagaren, om den fortfarande är aktiv, svara med ett ACK-värde för det aktuella sekvensnumret. Detta slutför keepalive-transaktionen.  

Som standard är keepalive-funktionen inte aktive rad. Om du vill använda den här funktionen måste NetX Duo-biblioteket skapas med ***NX_ENABLE_TCP_KEEPALIVE** _ definierade. Symbolen _ *_NX_TCP_KEEPALIVE_INITIAL_** anger antalet sekunder av inaktivitet innan keepalive-ramen initieras.  

### <a name="tcp-packet-receive"></a>Mottagning av TCP-paket   
TCP Receive-paketets bearbetning (anropas från IP-hjälpens tråd) ansvarar för hantering av olika anslutnings-och från kopplings åtgärder samt överföring av bekräftelse bearbetning. Dessutom ansvarar TCP Receive Packet-bearbetningen för att placera paket med ta emot data på rätt TCP-Sockets mottagande kö eller leverera paketet till den första pausade tråden som väntar på ett paket.

### <a name="tcp-receive-notify"></a>TCP Receive-avisering     
Om program tråden behöver bearbeta mottagna data från fler än en socket ska funktionen ***nx_tcp_socket_receive_notify*** användas. Den här funktionen registrerar en motringnings funktion för mottagnings paket för socketen. När ett paket tas emot på socketen körs motringningsfunktionen.  

Innehållet i motringningsfunktionen är applicationspecific; funktionen skulle dock förmodligen innehålla logik för att informera bearbetnings tråden att ett paket är tillgängligt på motsvarande socket. 

### <a name="thread-suspension"></a>Tråd upphängning      
Som tidigare nämnts kan program trådar pausa vid försök att ta emot data från en viss TCP-port. När ett paket har mottagits på den porten, tilldelas den första tråden inaktive rad och tråden återupptas sedan. En valfri timeout är tillgänglig när du pausar ett TCP Receive-paket, en funktion som är tillgänglig för de flesta NetX Duo-tjänster.  

Tråd upphängning är också tillgängligt för anslutning (både klient och Server), klient bindning och från kopplings tjänster.  

### <a name="tcp-socket-statistics-and-errors"></a>TCP-socket statistik och fel     
Om den här inställningen är aktive rad håller NetX Duo TCP socket-programvaran reda på flera statistik och fel som kan vara användbara för programmet. Följande statistik och fel rapporter underhålls för varje IP/TCP-instans:   

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

### <a name="tcp-socket-control-block-nx_tcp_socket"></a>TCP socket Control Block NX_TCP_SOCKET      
Egenskaperna för varje TCP-socket finns i det associerade *NX_TCP_SOCKET* kontroll blocket som innehåller användbar information, till exempel länken till IP-datastrukturen, nätverks anslutnings gränssnittet, den bundna porten och kön för mottagnings paket. Den här strukturen definieras i filen ***nx_api. h*** .