---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX Duo BSD
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Duo BSD-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 560621e528c8ce98013ce505ea1511f466317f4a087aa44cc0e70cb4d4b8ed1e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788515"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX Duo BSD

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Duo BSD-komponenten.

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS NetX Duo BSD kan hämtas från vår offentliga källkodsdatabas på [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nxd_bsd.h:** Rubrikfil för NetX Duo BSD
- **nxd_bsd.c:** C-källfil för NetX Duo BSD
- **nxd_bsd.pdf:** Användarhandbok för NetX Duo BSD

Demofiler:

- **bsd_demo_udp.c**
- **bsd_demo_tcp.c**
- **bsd_demo_raw.c**

## <a name="netx-duo-bsd-installation"></a>NetX Duo BSD-installation

För att kunna använda NetX Duo BSD ska hela distributionen som nämns ovan kopieras till samma katalog där NetX Duo är installerat. Om NetX Duo till exempel är installerat i katalogen "*\threadx\arm7\green*" ska *filerna nxd_bsd.h* *och nxd_bsd.c* kopieras till den här katalogen.

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a>Skapa ThreadX- och NetX Duo-komponenterna i ett BSD-program

### <a name="threadx"></a>ThreadX

ThreadX-biblioteket måste `bsd_errno` definieras i den lokala trådlagringen. Vi rekommenderar följande procedur:

1. I *tx_port.h* anger du ett av TX_THREAD_EXTENSION makron enligt följande:
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. Återskapa ThreadX-biblioteket.

> [!NOTE]
> Om TX_THREAD_EXTENSION_3 redan används kan användaren använda något av de andra TX_THREAD_EXTENSION makron.

### <a name="netx-duo"></a>NetX Duo

Innan du använder NetX Duo BSD Services måste NetX Duo-biblioteket byggas med NX_ENABLE_EXTENDED_NOTIFY_SUPPORT definieras. Som standard definieras den inte. Om BSD-råsocketarna ska användas måste NetX Duo-biblioteket byggas med NX_ENABLE_IP_RAW_PACKET_FILTER definierat.

## <a name="using-netx-duo-bsd"></a>Använda NetX Duo BSD

Ett NetX Duo BSD-programprojekt måste innehålla *nxd_bsd.h* efter att det innehåller *tx_api.h* och *nx_api.h* för att kunna använda BSD-tjänster som anges senare i den här guiden. Programmet måste även innehålla *nxd_bsd.c* i byggprocessen. Den här filen måste kompileras på samma sätt som andra programfiler och dess objektformulär måste länkas tillsammans med programmets filer. Det här är allt som krävs för att använda NetX Duo BSD.

Om du vill använda NetX Duo BSD-tjänster måste programmet skapa en IP-instans, skapa en paketpool för BSD-lagret för att allokera paket från, allokera minnesutrymme för den interna BSD-trådstacken och ange prioriteten för den interna BSD-tråden. BSD-lagret initieras genom att *anropa bsd_initialize* och skicka in parametrarna. Detta visas i "Små exempel" senare i det här dokumentet, men prototypen visas nedan:

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

Den default_ip är den IP-instans som BSD-lagret fungerar på. Den default_pool används av BSD-tjänsterna för att allokera paket från. Följande två parametrar: bsd_thread_stack_area, bsd_thread_stack_size definierar det stackområde som används av den interna BSD-tråden, och den sista parametern, bsd_thread_priority, anger trådens prioritet.

## <a name="netx-duo-bsd-raw-socket-support"></a>Stöd för NetX Duo BSD Raw Socket

NetX Duo BSD stöder även råsocketar. Om du vill använda råsocketar i NetX Duo BSD måste NetX Duo-biblioteket kompileras med NX_ENABLE_IP_RAW_PACKET_FILTER definierat. Som standard definieras den inte. Programmet måste sedan aktivera raw socket för en tidigare skapad IP-instans genom att anropa *nx_ip_raw_packet_enable.*

För att raw socket i NetX Duo BSD använder programmet socket create service *socket* och anger protokollfamilj, sockettyp och protokoll:

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

protocolFamily är AF_INET för IPv4-sockets eller AF_INET6 för IPv6-sockets, förutsatt att IPv6 är aktiverat på IP-instansen. Den socket_type måste anges till SOCK_RAW. protokollet är programspecifikt.

För att skicka och ta emot rådatapaket samt stänga ett raw socket använder programmet vanligtvis samma BSD-tjänster som för UDP, t.ex. *sendto, recvfrom, select* *och soc_close*. Råsocketar stöder inte *antingen* BSD-tjänster eller BSD-tjänster. 

- Mottagna IPv4-rådata innehåller som standard IPv4-huvudet.  Däremot innehåller mottagna IPv6-rådata inte IPv6-huvudet.

- När du skickar råa IPv6- eller IPv4-paket lägger BSD-omslutningslagret som standard till IPv6- eller IPv4-huvudet innan data skickas.

NetX Duo BSD stöder ytterligare raw socket alternativ, inklusive IP_RAW_RX_NO_HEADER, IP_HDRINCL och IP_RAW_IPV6_HDRINCL.

Om IP_RAW_RX_NO_HEADER har angetts tas IPv4-huvudet bort så att mottagna data inte innehåller IPv4-huvudet och den rapporterade meddelandelängden inte innehåller IPv4-huvudet.  För IPv6-sockets innehåller raw socket som standard inte IPv6-huvud, vilket motsvarar att IP_RAW_RX_NO_HEADER har angetts. Programmet kan använda *tjänsten setsockopt* för att rensa IP_RAW_RX_NO_HEADER-alternativet. När alternativet IP_RAW_RX_NO_HEADER är avmarkerat innehåller mottagna IPv6-rådata IPv6-huvudet och den rapporterade meddelandelängden innehåller IPv6-huvudet.

Det här alternativet har ingen effekt på IPv4- eller IPv6-överförda data.

Om IP_HDRINCL har angetts innehåller programmet IPv4-huvudet när data skickas.  Det här alternativet har ingen effekt på IPv6-överföring och definieras inte som standard. Om IP_RAW_IPV6_HDRINCL har angetts innehåller programmet IPv6-huvudet när data skickas.  Det här alternativet har ingen effekt på IPv4-överföring och definieras inte som standard.

IP_HDRINCL och IP_RAW_IPV6_HDRINCL ingen effekt på IPv4- eller IPv6-mottagning.

> [!NOTE]
> BSD 4.3 Socket-specifikationen anger att kerneln måste kopiera det råa paketet till varje socket-mottagningsbuffert. Men om flera socketar skapas med samma protokoll i NetX Duo BSD är beteendet odefinierat.

## <a name="netx-duo-bsd-raw-packet-support"></a>Stöd för Raw-paket för NetX Duo BSD

Om du vill aktivera råpaketstöd för PPPoE måste NetX Duo BSD-wrapper byggas med NX_BSD_RAW_PPPOE_SUPPORT aktiverat.

Följande kommando skapar en BSD-socket för att hantera PPPoE-rådatapaket:

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

Den aktuella BSD-implementeringen stöder bara två protokolltyper i AF_PACKET familjen

- `ETHERTYPE_PPPOE_DISC`: PPPoE Discovery-paket. I MAC-dataramen har identifieringspaketen Ethernet-ramtypen 0x8863.

- `ETHERTYPE_PPPOE_SESS`: PPP-sessionspaket. I MAC-dataramen har sessionspaketen Ethernet-ramtypen 0x8864.

Strukturen används `sockaddr_ll` för att ange parametrar när du skickar eller tar emot PPPoE-bildrutor.

`struct sockaddr_ll` deklareras som:

```c
struct sockaddr_ll
{
    USHORT  sll_family;     /* Must be AF_PACKET */
    USHORT  sll_protocol;   /* LL frame type */
    INT     sll_ifindex;    /* Interface Index. */
    USHORT  sll_hatype;     /* Header type */
    UCHAR   sll_pkttype;    /* Packet type */
    UCHAR   sll_halen;      /* Length of address */
    UCHAR   sll_addr[8];    /* Physical layer address */
};
```

> [!NOTE]
> Inte alla fält i strukturen används av `sendto()` eller `recvfrom()` . Se beskrivningen nedan om hur du ställer in för `sockaddr_ll` att skicka och ta emot PPPoE-paket.

Socket som skapats i AF_PACKET-familjen kan användas för att skicka antingen PPPoE Discovery-paket eller PPP-sessionspaket, oavsett vilket protokoll som anges. När ett PPPoE-paket överförs måste programmet förbereda bufferten som innehåller en korrekt formaterad PPPoE-ram, inklusive MAC-huvudena (MÅL-MAC-adress, MAC-källadress och bildrutetyp).) Storleken på bufferten innehåller Ethernet-huvudet på 14 byte.

`sockaddr_ll`Struct-structen `sll_ifindex` används för att ange det fysiska gränssnitt som ska användas för att skicka det här paketet. Resten av fälten i strukturen används inte. Värden som anges till oanvända fält ignoreras av den interna BSD-processen.

Följande kodblock visar hur du överför ett PPPoE-paket:

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

Returvärdet anger antalet byte som överförs. Eftersom PPPoE-paket är meddelandebaserade matchar antalet byte som skickats storleken på paketet vid en lyckad överföring, inklusive Ethernet-huvudet på 14 byte.

PPPoE-paket kan tas emot med hjälp av `recvfrom()` . Mottagningsbufferten måste vara tillräckligt stor för att hantera meddelanden med Ethernet MTU-storlek. Det mottagna PPPoE-paketet innehåller Ethernet-huvud på 14 byte. Vid mottagning av PPPoE-paket kan PPPoE Discovery-paket endast tas emot av socketar som skapats med protokollet `ETHERTYPE_PPPOE_DISC` . På samma sätt kan PPP-sessionspaket endast tas emot av socketar som skapats med protokollet `ETHERTYPE_PPPOE_SESS` . Om flera sockets skapas för samma protokolltyp vidarebefordras inkommande PPPoE-paket till den socket som skapas först. Om den första socketen som skapades för protokollet stängs används nästa socket i skapandeordningen för att ta emot dessa paket.

När ett PPPoE-paket har tagits emot är följande fält i `sockaddr_ll` struct-datastructen giltiga:
- **sll_family:** Anger att BSD ska vara AF_PACKET
- **sll_ifindex:** Anger gränssnittet som paketet tas emot från
- **sll_protocol:** Ange till typen av paket som tas emot: `ETHERTYPE_PPPOE_DISC` eller `ETHERTYPE_PPPOE_SESS`

## <a name="eliminating-internal-bsd-thread"></a>Eliminera intern BSD-tråd

Som standard använder BSD en intern tråd för att utföra en del av bearbetningen. I system med begränsade minnesbegränsningar kan BSD byggas med NX_BSD_TIMEOUT_PROCESS_IN_TIMER definierade, vilket eliminerar den interna BSD-tråden och använder i stället en intern timer för att utföra samma bearbetning. Detta eliminerar det minne som krävs för det interna BSD-trådkontrollblocket och -stacken. Den övergripande timerbearbetningen ökar dock avsevärt och BSD-bearbetningen kan också köras med en högre prioritet än vad som behövs.

Om du vill konfigurera BSD-sockets att köras i ThreadX-timerkontexten definierar du NX_BSD_TIMEOUT_PROCESS_IN_TIMER *i nxd_bsd.h*. Om BSD-lagret är konfigurerat för att köra BSD-uppgifterna i timerkontexten ignoreras följande tre parametrar i anropet till *bsd_initialize* och ska anges till NULL:

- **bsd_thread_stack_area**
- **bsd_thread_stack_size**
- **bsd_thread_priority**

## <a name="netx-duo-bsd-with-dns-support"></a>NetX Duo BSD med DNS-stöd

Om NX_BSD_ENABLE_DNS har definierats kan NetX Duo BSD skicka DNS-frågor för att hämta information om värdnamn eller värd-IP. Den här funktionen kräver att en NetX DNS-klient har skapats tidigare med *hjälp nx_dns_create tjänsten.* En eller flera kända IP-adresser för DNS-servern måste registreras med DNS-instansen med hjälp av *nx_dns_server_add-tjänsten* för att lägga till IPv4-serveradresser eller med *hjälp av nxd_dns_server_add-tjänsten* för att lägga till Antingen IPv4- eller IPv6-serveradresser.

DNS-tjänster och minnesallokering används av *getaddrinfo-* och *getnameinfo-tjänster:*

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

När BSD-programmet anropar *getaddrinfo* med ett värdnamn anropar NetX BSD någon av nedanstående tjänster för att hämta IP-adressen:

- **nx_dns_ipv4_address_by_name_get**
- **nxd_dns_ipv6_address_by_name_get**
- **nx_dns_cname_get**

För *nx_dns_ipv4_address_by_name_get* och *nxd_dns_ipv6_address_by_name_get* använder NetX BSD ipv4_addr_buffer och ipv6_addr_buffer minnesområdena. Storleken på dessa buffertar definieras av (NX_BSD_IPV4_ADDR_PER_HOST * 4) respektive (NX_BSD_IPV6_ADDR_PER_HOST * 16).

För att returnera adressinformation från *getaddrinfo* använder NetX BSD ThreadX-blockminnestabellen nx_bsd_addrinfo_pool_memory, vars minnesområde definieras av en annan uppsättning konfigurerbara alternativ, NX_BSD_IPV4_ADDR_MAX_NUM och NX_BSD_IPV6_ADDR_MAX_NUM.

Se **Allmänna konfigurationsalternativ** för mer information om konfigurationsalternativen ovan.

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats och värdindata är ett kanoniskt namn, allokerar NetX Duo BSD minne dynamiskt från en tidigare skapad blockpool "_nx_bsd_cname_block_pool

> [!NOTE]
> När *du har anropat getaddrinfo* ansvarar BSD-programmet för att frigöra minnet som res-argumentet pekar på tillbaka till blocktabellen med hjälp av *freeaddrinfo-tjänsten.*

## <a name="netx-duo-bsd-limitations"></a>Begränsningar för NetX Duo BSD

På grund av prestanda- och arkitekturproblem stöder NetX Duo BSD inte alla BSD 4.3 socket-funktioner:

INT-flaggor stöds inte för *anropen send, recv, sendto* *och recvfrom.*

## <a name="general-configuration-options"></a>Allmänna konfigurationsalternativ

Med användarkonfigurerbara *alternativ i nxd_bsd.h* kan programmet finjustera NetX Duo BSD-sockets för sina specifika programkrav.

Följande är en lista över konfigurerbara alternativ som anges vid kompilering:

- **NX_BSD_TCP_WINDOW: Används** i TCP socket create-anrop. 64 000 är en normal fönsterstorlek för 100 MB Ethernet. Standardvärdet är 65535.

- **NX_BSD_SOCKFD_START:** Det här är det logiska indexet för startvärdet för BSD-socketfilbeskrivningen. Som standard är det här alternativet 32.

- **NX_BSD_MAX_SOCKETS:** Anger det maximala antalet totalt antal sockets som är tillgängliga i BSD-lagret och måste vara en multipel av 32. Standardvärdet är 32.

- **NX_BSD_SOCKET_QUEUE_MAX:** Anger det maximala antalet UDP-paket som lagras i den mottagna socketkön. Värdet är som standard 5.

- **NX_BSD_MAX_LISTEN_BACKLOG:** Anger storleken på lyssnarkön (' eftersläpning') för BSD TCP-sockets. Standardvärdet är 5.

- **NX_MICROSECOND_PER_CPU_TICK:** Anger antalet mikrosekunder per tids tick för schemaläggaren.

- **NX_BSD_TIMEOUT:** Anger timeout i tids tick för interna NetX Duo-anrop som krävs av BSD. Standardvärdet är (20 * NX_IP_PERIODIC_RATE).

- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT:** Anger tidsgränsen i timern för NetX Duo-frånkopplingsanrop. Standardvärdet är 1.

- **NX_BSD_PRINT_ERRORS:** Om det här anges returnerar felstatusen för en BSD-funktion ett radnummer och en typ av fel, t.ex. NX_SOC_ERROR där felet inträffar. Detta kräver att programutvecklaren definierar felsökningsutdata. Standardinställningen är inaktiverad och inga felsökningsutdata anges *i nxd_bsd.h*.

- **NX_BSD_TIMER_RATE:** Intervall efter vilket den periodiska BSD-timeraktiviteten körs. Standardvärdet är 1 sekund (1 * NX_IP_PERIODIC_RATE).

- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER:** Om det här alternativet är inställt kan BSD-timeout-processen köras i systemtimerkontexten. Standardbeteendet är inaktiverat. Den här funktionen beskrivs i detalj i kapitel 2 "Installation och användning av NetX Duo BSD".

- **NX_BSD_RAW_PPPOE_SUPPORT:** Aktivera stöd för PPPoE-råpaket. Det här alternativet är inte aktiverat som standard.

- **NX_BSD_ENABLE_DNS:** Om det här alternativet är aktiverat skickar NetX Duo BSD en DNS-fråga för ett värdnamn eller en värd-IP-adress. Kräver att en DNS-klientinstans har skapats och startats tidigare. Som standard är den inte aktiverad.

- **NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE:** Definierar storleken på raw socket tabellen. Värdet måste vara en kraft på två. NetX BSD skapar en matris med socketar av NX_BSD_SOCKETS för att skicka och ta emot råa paket. NX_ENABLE_IP_RAW_PACKET_FILTER måste vara aktiverat. Som standard är det 32.

- **NX_BSD_IPV4_ADDR_MAX_NUM:** Maximalt antal IPv4-adresser som returneras *av getaddrinfo*. Detta tillsammans NX_BSD_IPV6_ADDR_MAX_NUM definierar storleken på Blockpool-nx_bsd_addrinfo_block_pool NetX BSD för att dynamiskt allokera minne till adressinformationslagring i *getaddrinfo*. Standardvärdet är 5.

- **NX_BSD_IPV6_ADDR_MAX_NUM:** Maximalt antal IPv6-adresser som returneras *av getaddrinfo*. Detta tillsammans NX_BSD_IPV4_ADDR_MAX_NUM definierar storleken på NetX BSD-blockpoolen nx_bsd_addrinfo_block_pool för att dynamiskt allokera minne till adressinformationslagring *i getaddrinfo*.

- **NX_BSD_IPV4_ADDR_PER_HOST: Definierar** maximalt antal IPv4-adresser som lagras per DNS-fråga. Standardvärdet är 5.

- **NX_BSD_IPV6_ADDR_PER_HOST: Definierar** maximalt antal IPv6-adresser som lagras per DNS-fråga. Standardvärdet är 2.

## <a name="bsd-socket-options"></a>Alternativ för BSD Socket

Följande lista över NetX Duo BSD-socketalternativ kan aktiveras (eller inaktiveras) vid körning per socket med tjänsten *setsockopt:*

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

Det finns två olika inställningar för option_level.

Den första typen av socketalternativ för körningstid är SOL_SOCKET alternativ för socketnivå. Om du vill aktivera ett alternativ på socketnivå anropar du *setsockopt* med option_level inställt på SOL_SOCKET och option_name angett till det specifika alternativet, t.ex. SO_BROADCAST *.* Om du vill hämta en alternativinställning *anropar du getsockopt* för option_name med option_level återigen inställd på SOL_SOCKET.

Listan över alternativ på socketnivå för körningstid visas nedan.

- **SO_BROADCAST:** Om det här är inställt kan du skicka och ta emot broadcast-paket från Netx-sockets. Det här är standardbeteendet för NetX Duo. Alla sockets har den här funktionen.

- **SO_ERROR:** Används för att hämta socketstatus för den tidigare socketåtgärden för den angivna socketen med *hjälp av getsockopt-tjänsten.* Alla sockets har den här funktionen.

- **SO_KEEPALIVE:** Om detta anges aktiveras TCP Keep Alive-funktionen. Detta kräver att NetX Duo-biblioteket byggs med NX_TCP_ENABLE_KEEPALIVE definieras *i nx_user.h*. Den här funktionen är inaktiverad som standard.

- **SO_RCVTIMEO:** Anger väntealternativet i sekunder för att ta emot paket på NetX Duo BSD-sockets. Standardvärdet är NX_WAIT_FOREVER (0xFFFFFFFF) eller, om icke-blockerande är aktiverat, NX_NO_WAIT (0x0).

- **SO_RCVBUF:** Anger fönsterstorleken för TCP-socketen. Standardvärdet, som NX_BSD_TCP_WINDOW, är inställt på 64k för BSD TCP-sockets. Om du vill ange storleken över 65535 måste NetX Duo-biblioteket byggas med NX_TCP_ENABLE_WINDOW_SCALING definieras.

- **SO_REUSEADDR:** Om det här anges gör detta att flera sockets kan mappas till en port. Den vanligaste användningen är för TCP-serversocketen. Det här är standardbeteendet för NetX Duo-sockets.

Den andra typen av socketalternativ för körningstid är IP-alternativnivån. Om du vill aktivera ett alternativ för IP-nivå anropar du *setsockopt* med option_level till IP_PROTO och option_name in på alternativet t.ex. IP_MULTICAST_TTL *.* Om du vill hämta en alternativinställning *anropar du getsockopt* för option_name med option_level återigen inställd på IP_PROTO.

Listan över ip-nivåalternativ för körningstid visas nedan.

- **IP_MULTICAST_TTL:** Detta anger TDD-sockets time to live. Standardvärdet är NX_IP_TIME_TO_LIVE (0x80) när socketen skapas. Det här värdet kan åsidosättas genom att anropa *setsockopt med det* här socketalternativet.

- **IP_RAW_IPV6_HDRINCL:** Om det här alternativet har angetts måste det anropande programmet lägga till ett IPv6-huvud och eventuellt programhuvuden till data som skickas på rådata IPv6-sockets som skapats av BSD. Om du vill använda det raw socket måste bearbetningen vara aktiverad på IP-uppgiften.

- **IP_ADD_MEMBERSHIP:** Om det här alternativet har angetts kan BSD-socketen (gäller endast UDP-socketar) ansluta till den angivna IGMP-gruppen.

- **IP_DROP_MEMBERSHIP:** Om det här alternativet har angetts kan BSD-socketen (gäller endast UDP-socketar) lämna den angivna IGMP-gruppen.

- **IP_HDRINCL:** Om det här alternativet har angetts måste det anropande programmet lägga till IP-huvudet och eventuellt programhuvuden till data som överförs på råa IPv4-sockets som skapats i BSD. Om du vill använda det raw socket måste bearbetningen vara aktiverad på IP-uppgiften.

- **IP_RAW_RX_NO_HEADER:** Om den är rensad inkluderas IPv6-huvudet med mottagna data för IPv6-råsocketar som skapats i BSD. IPv6-huvuden tas bort som standard i BSD-råa IPv6-socketar och paketlängden innehåller inte IPv6-huvudet.

Om detta anges tas IPv4-huvudet bort från mottagna data på BSD-råsocketar av typen IPv4. IPv4-huvuden ingår som standard i BSD-råa IPv4-sockets och paketlängden innehåller IPv4-huvudet.

Det här alternativet har ingen effekt på vare sig IPv4- eller IPv6-överföringsdata.

## <a name="small-ipv4-example"></a>Litet IPv4-exempel

Ett exempel på hur du använder NetX Duo BSD-tjänster för IPv4-nätverk beskrivs nedan. I det här exemplet kommer *indelningsfilen nxd_bsd.h* på rad 8. Därefter skapas *IP-bsd_ip* och *bsd_pool* som globala variabler på rad 20 och 21. Observera att den här demonstrationen använder en RAM-drivrutin (virtuell)*_nx_ram_network_driver*. Klienten och servern delar samma IP-adress på en enskild IP-instans i det här exemplet.

Klient- och servertrådarna skapas på raderna 62 och 68. BSD-paketpoolen för överföring av paket skapas på rad 78 och används när IP-instansen skapas på rad 87. Observera att IP-trådaktiviteten får prioritet 1 i *det nx_ip_create anropet.* Den här tråden bör vara den högsta prioritetsuppgiften som definierats i programmet för optimala NetX-prestanda.

IP-instansen är aktiverad för ARP- och TCP-tjänster på raderna 88 respektive 110. Det sista kravet innan BSD-tjänster kan användas är att *anropa bsd_initialize* på rad 120 för att konfigurera alla datastrukturer och NetX- och ThreadX-resurser som krävs av BSD.

Servertrådens postfunktion definieras härnäst. BSD TCP-socketen skapas på rad 149. Serverns IP-adress och port anges på raderna 160–163. Observera användningen av makron *htonl* och *hton-värden* för nätverksbyteordning som tillämpas på IP-adressen och porten. Detta är i enlighet med BSD-socketspecifikationen att multibyte-data skickas till BSD-tjänsterna i nätverksbyteordning.

Därefter binds huvudserversocketen till porten med *bindningstjänsten* på rad 166. Det här är lyssningssocketen för TCP-anslutningsbegäranden med *hjälp* av lyssningstjänsten på rad 180. Härifrån loopar servertrådfunktionen, *thread_server_entry*, för att söka efter mottagningshändelser med hjälp av select-anropet på rad 202.  Om en mottagningshändelse är en anslutningsbegäran, som bestäms genom att jämföra den läsklara listan, anropas *acceptera* på rad 213. En underordnad serversocket tilldelas för att hantera anslutningsbegäran och läggs till i huvudlistan över TCP-serversocketar som är anslutna till en klient på rad 223. Om det inte finns några nya anslutningsbegäranden söker servertråden sedan igenom alla anslutna socketar efter mottagningshändelser i for-loopen som börjar på rad 236. När en väntande mottagningshändelse  identifieras anropar den send och *recv* på den socketen tills inga data tas emot (anslutningen stängs på den andra sidan) och socketen stängs med *hjälp av soc_close-tjänsten* på rad 277.

När servertråden har anslutits skapar funktionen Client thread *entry, thread_client_entry,* en socket på rad 326 och ansluter med TCP-serversocketen med anslutningsanropet på rad 337.  Den loopar sedan för att skicka och ta emot paket med *hjälp av* tjänsterna send *respektive recv.* När inga fler data tas emot stängs socketen på  rad 398 med soc_close tjänsten. Efter frånkopplingen skapar klienttrådens postfunktion en ny TCP-socket och gör en till anslutningsbegäran i while-loopen som startades på rad 321.

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection, sending,
and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQR
    STUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */

ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */

VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */
int     main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool", 128,
                                pointer, 16384);

    pointer = pointer + 16384;
    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                    0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                    pointer, 2048, 1);
                    pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable ARP \n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize (&bsd_ip, &bsd_pool,pointer, 2048, 2);
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT       status, sock, sock_tcp_server;
ULONG     actual_status;
INT       Clientlen;
INT       i;
UINT      is_set = NX_FALSE;
struct    sockaddr_in serverAddr;
struct    sockaddr_in ClientAddr;

    tx_thread_sleep(100);

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
        &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("Error on Server socket %d create \n", sock_tcp_server);
        return;
    }

    printf("Server socket %d created\n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    serverAddr.sin_port = htons(SERVER_PORT);

    /* Bind this server socket */
    status = bind (sock_tcp_server, (struct sockaddr *) &serverAddr,
                sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error on Server Socket %d Bind \n", sock_tcp_server);
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen (sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error on Server Socket %d Listen\n", sock_tcp_server);
        return;
    }
    else
        printf("Server socket %d listen complete\n", sock_tcp_server);

    /* All set to accept client connections */

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ((status == 0xFFFFFFFF) || (status == 0))
        {

            printf("Error with select. Status 0x%x\n", status);

            continue;
        }

        /* Check for a connection request. */
        is_set = FD_ISSET(sock_tcp_server, &read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,(struct sockaddr*)&ClientAddr,
                        &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i , &master_list)) &&
                (FD_ISSET(i , &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server received no data from Client on
                            socket %d)\n", i);
                        break;
                    }
                    else if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server receiving data from Client on
                            socket %d\n", i);
                        break;
                    }
                    if(status == SERVER_RCV_BUFFER_SIZE) status--;
                    Server_Rcv_Buffer[status] = 0;
                    printf("Server socket %d received %d bytes: %s\n ",
                            i, (ULONG)status, Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                        Client\n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                        Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != NX_SOC_ERROR)
                {
                    printf("Server socket %d closed \n", i);
                }
                else
                {
                    printf("Error on closing Server socket %d \n", i);
                }
            }
        }

    /* Loop back to check any next client connection */
    }
}

CHAR     Client_Rcv_Buffer[100];

VOID     thread_client_entry(ULONG thread_input)
{

INT        status;
INT        sock_tcp_client, length;
struct     sockaddr_in echoServAddr;
struct     sockaddr_in localAddr; /

    /* Let the server side get set up. */
    tx_thread_sleep(200);

    /* Set local port for displaying IP address and port. */
    memset(&localAddr, 0, sizeof(localAddr));
    localAddr.sin_family = AF_INET;
    localAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    localAddr.sin_port = htons(CLIENT_PORT);

    /* Set server port and IP address which we need to connect. */
    memset(&echoServAddr, 0, sizeof(echoServAddr));
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    echoServAddr.sin_port = htons(SERVER_PORT);

    /* Now make client connections with the server. */
    while (1)
    {

        printf("\n");

        /* Create BSD TCP Socket */
        sock_tcp_client = socket( AF_INET, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n", sock_tcp_client);
            return;
        }

        printf("Client socket %d created\n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr,
                        sizeof(echoServAddr));

        /* Check for error. */
        if (status != OK)
        {
            printf("Error on Client socket %d connect\n", sock_tcp_client);
                    soc_close(sock_tcp_client);
            return;
        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr,
                            &length);

        printf("Client port = %lu , Client = 0x%x,",
            htonl(localAddr.sin_port), htonl(localAddr.sin_addr.s_addr));

        length = sizeof(struct sockaddr_in);

        status = getpeername( sock_tcp_client, (struct sockaddr *)
                            &echoServAddr, &length);

        printf("Remote port = %lu, Remote IP = 0x%x \n",
                htonl(echoServAddr.sin_port),
                htonl(echoServAddr.sin_addr.s_addr));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
            sock_tcp_client);

            status = send(sock_tcp_client, "Hello", (sizeof("Hello")), 0);

            if (status == ERROR)
            {
                printf("Error: Client Socket (%d) send \n", sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,100,0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    380 printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Nothing received by Client on socket %d\n",
                            sock_tcp_client);
                }

                break;
            }
            else
            {
                printf("Client socket %d received %d bytes: %s\n",
                        sock_tcp_client,
                        status, Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = soc_close(sock_tcp_client);

        if (status != ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```

## <a name="small-ipv6-example-system"></a>Litet IPv6-exempelsystem

Ett exempel på hur du använder NetX Duo BSD-tjänster för IPv6-nätverk beskrivs i programmet nedan. Det här exemplet liknar IPv4-demoprogrammet som beskrevs tidigare med några viktiga skillnader.

Klient- och servertrådarna, BSD-paketpoolen, IP-instansen och BSD-initieringen sker på samma sätt som för IPv4 BSD-sockets.

I servertrådens postfunktion *definierar thread_server_entry* ett par IPv6-variabler med *hjälp av sockaddr_in6* och *NXD_ADDRESS-datatyper* på raderna 145–148. Datatypen NXD_ADDRESS kan faktiskt lagra både IPv4- och IPv6-adresstyper.

Därefter aktiverar servertråden IPv6 och ICMPv6 på IP-instansen med *hjälp av nxd_ipv6_enable* och *nxd_icmpv6_enable* på rad 161 respektive 169. Därefter registreras länkens lokala och globala IP-adresser med IP-instansen. Detta görs med hjälp av *nxd_ipv6_address_set tjänsten* på raderna 180 och 195. Den försparar sig sedan tillräckligt länge för att IP-trådaktiviteten ska slutföra protokollet Dubblettadressidentifiering och registrera dessa adresser som giltiga adresser i tx_thread_sleep-anropet på rad 201. 

Därefter skapas TCP-serversocketen med AF_INET6 argument för sockettyp på rad 204. Socket-IPv6-adressen och porten är inställda på raderna 216–221, vilket återigen visar användningen av *htonl-* och *htons-makron* för att placera data i nätverksbyteordningen för BSD-sockettjänster. Härifrån är servertrådens postfunktion praktiskt taget identisk med IPv4-exemplet.

Klienttrådens *postfunktion, thread_client_entry*, definieras härnäst. Observera att eftersom TCP-klienten i det här exemplet delar samma IP-instans och IPv6-adress som TCP-servern behöver vi inte aktivera IPv6- eller ICMPv6-tjänster på IP-instansen igen. Dessutom är IPv6-adressen redan registrerad med IP-instansen. I stället väntar klienttrådens postfunktion helt enkelt på rad 368 tills servern har ställts in. Serveradressen och porten anges med hjälp av värden för att nätverksbyteordning makron på raderna 387-392 och sedan klienten kan ansluta till TCP-servern på rad 412. Observera att de lokala IP-adressdatatyperna på raderna 378–383 endast används för att demonstrera *getockname-* och *getpeername-tjänsterna* på raderna 425 respektive 434. Eftersom data kommer från nätverket är nätverket värd för byteordningsma makron som används på raderna 378–383.

Därefter anger klienttrådens postfunktion en loop där den skapar en TCP-socket, gör en TCP-anslutning och skickar och tar emot data med TCP-servern tills inga fler data tas emot i princip på samma sätt som IPv4-exemplet. Den stänger sedan socketen på rad 483, pausar kort och skapar en annan TCP-socket och begär en TCP-serveranslutning.

En viktig skillnad med IPv4-exemplet är *att socketanropen* anger en IPv6-socket med hjälp AF_INET6 indataargumentet. En annan viktig skillnad  är att TCP-klient *connect-anropet tar en* sockaddr_in6-datatyp och ett längdargument som är inställt på storleken på sockaddr_in6-datatypen. 

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection,
disconnection, sending, and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */
ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */
VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int     main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool",
    128, pointer, 16384);

    pointer = pointer + 16384;

    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                        0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in enable ARP on BSD IP instance\n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 2);

    /* Check BSD initialize status. */
    if (status)
    {
        error_counter++;
        printf("Error in BSD initialize \n");
    }

    pointer = pointer + 2048;
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT             status, sock, sock_tcp_server;
ULONG           actual_status;
INT             Clientlen;
INT             i;
UINT            is_set = NX_FALSE;
NXD_ADDRESS     ip_address;
struct          sockaddr_in6 serverAddr;
struct          sockaddr_in6 ClientAddr;
UINT            iface_index, address_index;

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
            &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 */
    status = nxd_ipv6_enable(&bsd_ip);
    if((status != NX_SUCCESS) && (status != NX_ALREADY_ENABLED))
    {
        printf("Error with IPv6 enable 0x%x\n", status);
        return;
    }

    /* Enable ICMPv6 */
    status = nxd_icmp_enable(&bsd_ip);

    if(status)
    {
        printf("Error with ECMPv6 enable 0x%x\n", status);
        return;
    }

    /* Set the primary interface for our DNS IPv6 addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, NX_NULL, 10,
                                &address_index);

    if (status)
        return;

    /* Set ip_0 interface address. */
    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    ip_address.nxd_ip_address.v6[0] = htonl(0x20010db8);
    ip_address.nxd_ip_address.v6[1] = htonl(0x0000f101);
    ip_address.nxd_ip_address.v6[2] = 0;
    ip_address.nxd_ip_address.v6[3] = htonl(0x101);

    /* Set the host global IP address. We are assuming a 64
    bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, &ip_address, 64,
                                &address_index);

    if (status)
        return;

    /* Wait for IPv6 stack to finish DAD process. */
    tx_thread_sleep(400);

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET6, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("\nError: BSD TCP Server socket create \n");
        return;
    }

    printf("\nBSD TCP Server socket created %lu \n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    serverAddr.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    serverAddr.sin6_addr._S6_un._S6_u32[2] = 0x0;
    serverAddr.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    serverAddr.sin6_port = htons(SERVER_PORT);
    serverAddr.sin6_family = AF_INET6;

    /* Bind this server socket */
    status = bind(sock_tcp_server, (struct sockaddr *) &serverAddr,
                    sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error: Server Socket Bind \n");
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen(sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error: Server Socket Listen\n");
        return;
    }
    else
        printf("Server Listen complete\n");

    /* All set to accept client connections */
    printf("Now accepting client connections\n");

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ( (status == 0xFFFFFFFF) || (status == 0) )
        {
            printf("Error with select? Status 0x%x. Try again\n", status);

            continue;
        }

        /* Detected a connection request. */
        is_set = FD_ISSET(sock_tcp_server,&read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,
            (struct sockaddr*)&ClientAddr,
            &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {
                printf("New connection %d\n", sock);

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i, &master_list)) &&
                (FD_ISSET(i, &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server socket %d received no data from
                                Client)\n", i);

                        break;
                    }
                    else if (status == 0xFFFFFFFF)
                    {
                        printf("Error on Server socket %d receiving data from
                                Client\n", i);

                        break;
                    }

                    printf("Server socket %d received from Client %lu bytes:
                            %s\n ", i, (ULONG)status,
                            Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                                Client \n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                                Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != ERROR)
                {
                    printf("Server socket %d closing\n", i);
                }
                else
                {

                    printf("Error on Server socket %d closing\n", i);
                }
            }
        }

        /* Loop back to check any next client connection */
    }
}

#define     CLIENT_BUFFER_SIZE 100
CHAR        Client_Rcv_Buffer[CLIENT_BUFFER_SIZE];

VOID        thread_client_entry(ULONG thread_input)
{

INT         status;
INT         sock_tcp_client, length;
struct      sockaddr_in6 echoServAddr6;
struct      sockaddr_in6 localAddr6; address */

    /* Wait for the server side to get set up, including the DAD process. */
    tx_thread_sleep(500);

    /* ICMPv6 and IPv6 should already be enabled on the IP instance
    by the server thread entry function. */

    /* Further the IPv6 address is already established with the IP instance.
    so no need to wait for DAD completion. */

    /* Set local port and IP address (used only for getsockname call). */
    memset(&localAddr6, 0, sizeof(localAddr6));
    localAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    localAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    localAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    localAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    localAddr6.sin6_port = htons(CLIENT_PORT);
    localAddr6.sin6_family = AF_INET6;

    /* Set Server port and IP address to connect to the TCP server. */
    memset(&echoServAddr6, 0, sizeof(echoServAddr6));
    echoServAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    echoServAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    echoServAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    echoServAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    echoServAddr6.sin6_port = htons(SERVER_PORT);
    echoServAddr6.sin6_family = AF_INET6;

    /* Now make client connections with the server. */
    while (1)
    {
        printf("\n");

        /* Create BSD TCP Socket */

        sock_tcp_client = socket(AF_INET6, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n");
            return;
        }

        printf("Client socket %d created \n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr6,
                sizeof(echoServAddr6));

        /* Check for error. */
        if (status != NX_SOC_OK)
        {
            printf("Error on Client socket %d connect\n");
            soc_close(sock_tcp_client);
            return;

        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr6,
        &length);

        printf("Client port = %lu , Client = 0x%x 0x%x 0x%x 0x%x,",
                ntohs(localAddr6.sin6_port),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[3]));

        length = sizeof(struct sockaddr_in6);

        status = getpeername(sock_tcp_client, (struct sockaddr *)
                            &echoServAddr6, &length);

        printf("Remote port = %lu, Remote IP = 0x%x 0x%x 0x%x 0x%x \n",
                ntohs(echoServAddr6.sin6_port),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[3]));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
                sock_tcp_client);

            status = send(sock_tcp_client, "Hello", sizeof("Hello"), 0);

            if (status == NX_SOC_ERROR)
            {
                printf("Error on Client Socket (%d) send \n",
                        sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message: Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,
                        CLIENT_BUFFER_SIZE, 0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Client received no data on socket %d\n",
                            sock_tcp_client);
                }

            break;
            }
            else
            {
                printf("Client socket %d received %d bytes and this message:
                        %s\n", sock_tcp_client, status,
                        Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = oc_close(sock_tcp_client);

        if (status != NX_SOC_ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```
