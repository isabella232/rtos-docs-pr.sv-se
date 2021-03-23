---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo BSD
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider-NetX Duo BSD-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 582661bc66c51341fc098de9ff7b6fa2a7d746de
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826154"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo BSD

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider-NetX Duo BSD-komponenten.

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider NetX Duo BSD kan hämtas från vår offentliga käll kods lagrings plats på [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nxd_bsd. h**: rubrik fil för netx Duo BSD
- **nxd_bsd. c**: c-källfil för netx Duo BSD
- **nxd_bsd.pdf**: Användar handbok för netx Duo BSD

Demonstrations filer:

- **bsd_demo_udp. c**
- **bsd_demo_tcp. c**
- **bsd_demo_raw. c**

## <a name="netx-duo-bsd-installation"></a>Installation av NetX Duo BSD

För att kunna använda NetX Duo BSD bör hela distributionen som nämnts tidigare kopieras till samma katalog där NetX Duo är installerat. Om t. ex. NetX Duo är installerat i katalogen "*\threadx\arm7\green*", ska *nxd_bsd. h* -och *nxd_bsd. c* -filerna kopieras till den här katalogen.

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a>Skapa ThreadX-och NetX Duo-komponenter i ett BSD-program

### <a name="threadx"></a>ThreadX

ThreadX-biblioteket måste definiera `bsd_errno` i den lokala tråd lagringen. Vi rekommenderar följande procedur:

1. I *tx_port. h* anger du ett av TX_THREAD_EXTENSION-makron enligt följande:
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. Återskapa ThreadX-biblioteket.

> [!NOTE]
> Om TX_THREAD_EXTENSION_3 redan används, är användaren kostnads fri att använda något av de andra TX_THREAD_EXTENSION-makron.

### <a name="netx-duo"></a>NetX Duo

Innan du använder NetX Duo BSD-tjänster måste NetX Duo-biblioteket skapas med NX_ENABLE_EXTENDED_NOTIFY_SUPPORT definierat. Som standard är den inte definierad. Om BSD RAW-socketarna ska användas måste NetX Duo-biblioteket skapas med NX_ENABLE_IP_RAW_PACKET_FILTER definierat.

## <a name="using-netx-duo-bsd"></a>Använda NetX Duo BSD

Ett NetX Duo BSD-programprojekt måste innehålla *nxd_bsd. h* när det innehåller *tx_api. h* och *nx_api. h* för att kunna använda BSD-tjänster som anges senare i den här hand boken. Programmet måste även innehålla *nxd_bsd. c* i build-processen. Den här filen måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer. Detta är allt som krävs för att använda NetX Duo BSD.

Om du vill använda NetX Duo BSD-tjänster måste programmet skapa en IP-instans, skapa en adresspool för BSD-lagret för att allokera paket från, allokera minnes utrymme för den interna BSD-trådens stack och ange prioriteten för den interna BSD-tråden. BSD-lagret initieras genom att anropa *bsd_initialize* och skicka in parametrarna. Detta visas i "små exempel" senare i det här dokumentet, men prototypen visas nedan:

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

Default_ip är den IP-instans som BSD-lagret arbetar med. Default_pool används av BSD-tjänsterna för att allokera paket från. Följande två parametrar: bsd_thread_stack_area, bsd_thread_stack_size definierar stackområdet som används av den interna BSD-tråden och den sista parametern, bsd_thread_priority, anger trådens prioritet.

## <a name="netx-duo-bsd-raw-socket-support"></a>Stöd för NetX Duo BSD RAW socket

NetX Duo BSD stöder också RAW-Sockets. Om du vill använda RAW-socketar i NetX Duo BSD måste NetX Duo-biblioteket kompileras med NX_ENABLE_IP_RAW_PACKET_FILTER definierat. Som standard är den inte definierad. Programmet måste sedan aktivera rå socket-bearbetning för en tidigare skapad IP-instans genom att anropa *nx_ip_raw_packet_enable.*

För att skapa en RAW-socket i NetX Duo BSD använder programmet socketen skapa tjänst- *socket* och anger protokoll familjen, typ av socket och protokoll:

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

protocolFamily är AF_INET för IPv4-Sockets eller AF_INET6 för IPv6-Sockets förutsatt att IPv6 är aktiverat på IP-instansen. Socket_type måste anges till SOCK_RAW. protokollet är programspecifikt.

Om du vill skicka och ta emot obearbetade paket samt stänga en RAW-socket använder programmet vanligt vis samma BSD-tjänster som för UDP, t. ex. *SendTo, recvfrom, väljer* och *soc_close*. RAW-Sockets stöder varken *Accept* -eller *Listener* BSD-tjänster.

- Mottagna IPv4-rå data inkluderar som standard IPv4-huvudet.  Däremot inkluderar mottagna IPv6-rå data inte IPv6-sidhuvudet.

- När du skickar antingen obehandlade IPv6-eller IPv4-paket, lägger BSD-skiktet som standard till IPv6-eller IPv4-sidhuvudet innan data skickas.

NetX Duo BSD stöder ytterligare alternativ för RAW socket, inklusive IP_RAW_RX_NO_HEADER IP_HDRINCL och IP_RAW_IPV6_HDRINCL.

Om IP_RAW_RX_NO_HEADER har angetts tas IPv4-rubriken bort så att mottagna data inte innehåller IPv4-huvudet och den rapporterade meddelande längden inkluderar inte IPv4-huvudet.  För IPv6-socketar inkluderar Receive socket Receive inte IPv6-sidhuvudet, som motsvarar IP_RAW_RX_NO_HEADER alternativ uppsättning. Programmet kan använda *Setsockopt* -tjänsten för att ta bort alternativet IP_RAW_RX_NO_HEADER när alternativet IP_RAW_RX_NO_HEADER har rensats, skulle mottagna IPv6-rå data inkludera IPv6-huvudet och den rapporterade meddelande längden inkluderar IPv6-huvudet.

Det här alternativet har ingen påverkan på IPv4-eller IPv6-överförda data.

Om IP_HDRINCL har angetts inkluderar programmet IPv4-sidhuvudet när data skickas.  Det här alternativet har ingen påverkan på IPv6-överföring och definieras inte som standard. Om IP_RAW_IPV6_HDRINCL har angetts inkluderar programmet IPv6-sidhuvudet när data skickas.  Det här alternativet har ingen påverkan på IPv4-överföring och definieras inte som standard.

IP_HDRINCL och IP_RAW_IPV6_HDRINCL har ingen påverkan på IPv4-eller IPv6-mottagning.

> [!NOTE]
> BSD 4,3-socket-specifikationen anger att kerneln måste kopiera RAW-paketet till varje socket Receive-buffert. Men i NetX Duo BSD, om flera Sockets har skapats med att dela samma protokoll, är beteendet odefinierat.

## <a name="netx-duo-bsd-raw-packet-support"></a>Stöd för NetX Duo BSD RAW-paket

Om du vill aktivera stöd för RAW-paket för PPPoE måste NetX Duo BSD-omslutningen skapas med NX_BSD_RAW_PPPOE_SUPPORT aktiverat.

Följande kommando skapar en BSD-socket för att hantera PPPoE RAW-paket:

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

Den aktuella BSD-implementeringen stöder endast två protokoll typer i AF_PACKET-serien

- `ETHERTYPE_PPPOE_DISC`: PPPoE-identifierings paket. I MAC data-ramen har identifierings paketen Ethernet-ramtypen 0x8863.

- `ETHERTYPE_PPPOE_SESS`: PPP-session paket. I rutan MAC-data har sessions-paketen Ethernet-ramtyp 0x8864.

Strukturen `sockaddr_ll` används för att ange parametrar när du skickar eller tar emot PPPoE-ramar.

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
> Alla fält i strukturen används inte av `sendto()` eller `recvfrom()` . Se beskrivningen nedan om hur du konfigurerar `sockaddr_ll` för att skicka och ta emot PPPoE-paket.

Socket som skapats i AF_PACKETs familjen kan användas för att skicka PPPoE-paket eller PPP-sessionsobjekt, oavsett vilket protokoll som anges. När ett PPPoE-paket överförs måste programmet förbereda bufferten som innehåller korrekt formaterad PPPoE-ram, inklusive MAC-sidhuvuden (målets MAC-adress, käll-MAC-adress och ramtyp.) Buffertstorleken innehåller ett Ethernet-huvud på 14 byte.

`sockaddr_ll`Struct (struct) `sll_ifindex` används för att ange det fysiska gränssnitt som ska användas för att skicka det här paketet. Resten av fälten i strukturen används inte. Värden som används i de oanvända fälten ignoreras av den interna BSD-processen.

Följande kodblock visar hur du skickar ett PPPoE-paket:

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

Returvärdet anger antalet byte som skickats. Eftersom PPPoE-paketen är meddelandebaserade, i en lyckad överföring, matchar antalet skickade byte paketets storlek, inklusive Ethernet-huvudet på 14 byte.

PPPoE-paket kan tas emot med hjälp av `recvfrom()` . Receive buffer måste vara tillräckligt stor för att rymma meddelande om Ethernet MTU-storlek. Det mottagna PPPoE-paketet innehåller 14 byte Ethernet-sidhuvud. Vid mottagning av PPPoE-paket kan PPPoE-identifierings paket endast tas emot av socket som skapats med protokollet `ETHERTYPE_PPPOE_DISC` . På samma sätt kan bara PPP-sessionsobjekt tas emot av socket som skapats med protokollet `ETHERTYPE_PPPOE_SESS` . Om flera Sockets skapas för samma protokoll typ, vidarebefordras inkommande PPPoE-paket till den socket som skapades först. Om den första socketen som skapas för protokollet stängs, används nästa socket i skapande ordningen för att ta emot dessa paket.

När ett PPPoE-paket tas emot är följande fält i `sockaddr_ll` strukturen giltiga:
- **sll_family**: som anges av BSD Internal som ska AF_PACKET
- **sll_ifindex**: anger gränssnittet som paketet tas emot från
- **sll_protocol**: Ange till den typ av paket som tas emot: `ETHERTYPE_PPPOE_DISC` eller `ETHERTYPE_PPPOE_SESS`

## <a name="eliminating-internal-bsd-thread"></a>Tar bort intern BSD-tråd

Som standard använder BSD en intern tråd för att utföra en del bearbetning. I system med stränga minnes begränsningar kan BSD skapas med NX_BSD_TIMEOUT_PROCESS_IN_TIMER som definierats, vilket eliminerar den interna BSD-tråden och använder i stället en intern timer för att utföra samma bearbetning. Detta eliminerar det minne som krävs för det interna BSD-blocket och stacken för tråd kontroll. Övergripande timer-bearbetning ökar dock avsevärt och BSD-bearbetningen kan också köras med högre prioritet än vad som behövs.

Om du vill konfigurera BSD-Sockets så att de körs i ThreadX timer-kontexten definierar du NX_BSD_TIMEOUT_PROCESS_IN_TIMER i *nxd_bsd. h*. Om BSD-lagret har kon figurer ATS för att köra BSD-uppgifter i timer-kontexten ignoreras följande tre parametrar i anropet till *bsd_initialize* och ska anges till null:

- **bsd_thread_stack_area**
- **bsd_thread_stack_size**
- **bsd_thread_priority**

## <a name="netx-duo-bsd-with-dns-support"></a>NetX Duo BSD med DNS-stöd

Om NX_BSD_ENABLE_DNS har definierats kan NetX Duo BSD skicka DNS-frågor för att hämta värdnamn eller värd-IP-information. Den här funktionen kräver att en NetX DNS-klient skapas tidigare med hjälp av tjänsten *nx_dns_create* . En eller flera kända DNS-Server-IP-adresser måste registreras med DNS-instansen med hjälp av tjänsten *nx_dns_server_add* för att lägga till IPv4-serveradresser eller använda tjänsten *nxd_dns_server_add* för att lägga till IPv4-eller IPv6-serveradresser.

DNS-tjänster och minnesallokering används av *getaddrinfo* -och *getnameinfo* -tjänster:

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

När BSD-programmet anropar *getaddrinfo* med ett värdnamn anropar netx BSD vilken som helst av tjänsterna nedan för att hämta IP-adressen:

- **nx_dns_ipv4_address_by_name_get**
- **nxd_dns_ipv6_address_by_name_get**
- **nx_dns_cname_get**

För *nx_dns_ipv4_address_by_name_get* och *NXD_DNS_IPV6_ADDRESS_BY_NAME_GET* använder NetX BSD ipv4_addr_buffer och ipv6_addr_buffer respektive minnes område. Storleken på de här buffertarna definieras av (NX_BSD_IPV4_ADDR_PER_HOST * 4) och (NX_BSD_IPV6_ADDR_PER_HOST * 16).

För att returnera adress information från *getaddrinfo* använder netx BSD ThreadX block minnes tabell nx_bsd_addrinfo_pool_memory, vars minnes området definieras av en annan uppsättning konfigurerbara alternativ, NX_BSD_IPV4_ADDR_MAX_NUM och NX_BSD_IPV6_ADDR_MAX_NUM.

Se **allmänna konfigurations alternativ** för mer information om konfigurations alternativen ovan.

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats och värd indatatypen är ett kanoniskt namn, allokerar NetX Duo BSD dynamiskt minne från en tidigare skapad block pool _nx_bsd_cname_block_pool

> [!NOTE]
> Efter att ha anropat *getaddrinfo* är BSD-programmet ansvarigt för att släppa det minne som pekas på av res argumentet tillbaka till block tabellen med hjälp av *freeaddrinfo* -tjänsten.

## <a name="netx-duo-bsd-limitations"></a>Begränsningar för NetX Duo BSD

På grund av prestanda-och arkitektur problem har NetX Duo BSD inte stöd för alla BSD 4,3-socket-funktioner:

Det finns inte stöd för INT *-flaggor för sändnings-, Recv-, SendTo-* och *recvfrom* -anrop.

## <a name="general-configuration-options"></a>Allmänna konfigurations alternativ

Alternativ som kan konfigureras i *nxd_bsd. h* gör att programmet kan finjustera netx Duo BSD-socketar för sina specifika program krav.

Följande är en lista över konfigurerbara alternativ som ställs in vid kompilering:

- **NX_BSD_TCP_WINDOW**: används i uppmaningen att skapa TCP-socketar. 64 KB är en typisk fönster storlek för 100 MB Ethernet. Standardvärdet är 65535.

- **NX_BSD_SOCKFD_START**: det här är det logiska indexet för start värde för BSD-Sockelns fil beskrivning. Som standard är det här alternativet 32.

- **NX_BSD_MAX_SOCKETS**: anger det maximala antalet totalt antal tillgängliga socketar i BSD-lagret och måste vara en multipel av 32. Värdet är standard för 32.

- **NX_BSD_SOCKET_QUEUE_MAX**: anger det maximala antalet UDP-paket som lagras i kön för mottagnings socket. Värdet är standard 5.

- **NX_BSD_MAX_LISTEN_BACKLOG**: Detta anger storleken på lyssnings kön ("efter släpning") för BSD TCP-socketar. Standardvärdet är 5.

- **NX_MICROSECOND_PER_CPU_TICK**: anger antalet mikrosekunder per Schemaläggarens timer-Tick.

- **NX_BSD_TIMEOUT**: anger tids gränsen i timer-Tick på netx Duo-interna anrop som krävs av BSD. Standardvärdet är (20 * NX_IP_PERIODIC_RATE).

- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: anger tids gränsen i timer-Tick på netx duo från kopplings anrop. Standardvärdet är 1.

- **NX_BSD_PRINT_ERRORS**: om det här alternativet anges returnerar fel status för en BSD-funktion ett rad nummer och en typ av fel, t. ex. NX_SOC_ERROR där felet uppstår. Detta kräver att programutvecklaren definierar fel söknings resultatet. Standardinställningen är inaktive rad och inga fel söknings utdata har angetts i *nxd_bsd. h*.

- **NX_BSD_TIMER_RATE**: intervall efter vilken BSD periodiska timer-aktivitet körs. Standardvärdet är 1 sekund (1 * NX_IP_PERIODIC_RATE).

- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: om det här alternativet är inställt kan BSD-timeout-processen köras i systemets timer-kontext. Standard beteendet är inaktiverat. Den här funktionen beskrivs i detalj i kapitel 2 "installation och användning av NetX Duo BSD".

- **NX_BSD_RAW_PPPOE_SUPPORT**: Aktivera stöd för PPPoE-rå paket. Det här alternativet är inte aktiverat som standard.

- **NX_BSD_ENABLE_DNS**: om det är aktiverat skickar netx Duo BSD en DNS-fråga för värdnamn eller värd-IP-adress. Kräver att en DNS-klient instans skapas och startas tidigare. Som standard är den inte aktive rad.

- **NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: definierar storleken på tabellen RAW socket. Värdet måste vara en potens av två. NetX BSD skapar en matris med Sockets av typen NX_BSD_SOCKETS för att skicka och ta emot rå paket. NX_ENABLE_IP_RAW_PACKET_FILTER måste vara aktiverat. Som standard är den 32.

- **NX_BSD_IPV4_ADDR_MAX_NUM**: det maximala antalet IPv4-adresser som returneras av *getaddrinfo*. Detta tillsammans med NX_BSD_IPV6_ADDR_MAX_NUM definierar storleken på NetX BSD block-poolen nx_bsd_addrinfo_block_pool för dynamiskt allokerat minne för att adressera informations lagringen i *getaddrinfo*. Standardvärdet är 5.

- **NX_BSD_IPV6_ADDR_MAX_NUM**: det maximala antalet IPv6-adresser som returneras av *getaddrinfo*. Detta tillsammans med NX_BSD_IPV4_ADDR_MAX_NUM definierar storleken på NetX BSD block-poolen nx_bsd_addrinfo_block_pool för dynamiskt allokerat minne för att adressera informations lagringen i *getaddrinfo*.

- **NX_BSD_IPV4_ADDR_PER_HOST**: definierar maximalt antal IPv4-adresser som lagras per DNS-fråga. Standardvärdet är 5.

- **NX_BSD_IPV6_ADDR_PER_HOST**: definierar maximalt antal IPv6-adresser som lagras per DNS-fråga. Standardvärdet är 2.

## <a name="bsd-socket-options"></a>BSD socket-alternativ

Följande lista med alternativ för NetX Duo BSD-socket kan aktive ras (eller inaktive RAS) vid körning per socket med hjälp av *Setsockopt* -tjänsten:

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

Det finns två olika inställningar för option_level.

Den första typen av ingångs alternativ för körning är SOL_SOCKET för alternativ för socketnivå. Om du vill aktivera ett alternativ för en socketnivå anropar du *Setsockopt* med option_level inställd på SOL_SOCKET och option_name anger det speciella alternativet t. ex. SO_BROADCAST *.* Om du vill hämta en alternativ inställning anropar du *getsockopt* för option_name med option_level återigen inställt på SOL_SOCKET.

Listan över alternativ för körning av socket-nivå visas nedan.

- **SO_BROADCAST**: om den här inställningen är aktive rad kan du skicka och ta emot broadcast-paket från netx Sockets. Detta är standard beteendet för NetX Duo. Alla Sockets har den här funktionen.

- **SO_ERROR**: används för att hämta socket-status för den tidigare socket-åtgärden för den angivna socketen med hjälp av *getsockopt* -tjänsten. Alla Sockets har den här funktionen.

- **SO_KEEPALIVE**: om det här alternativet har angetts aktiverar detta TCP Keep Alive-funktionen. Detta kräver att NetX Duo-biblioteket skapas med NX_TCP_ENABLE_KEEPALIVE som definieras i *nx_user. h*. Som standard är den här funktionen inaktive rad.

- **SO_RCVTIMEO**: Detta anger vänte alternativet i sekunder för mottagning av paket på netx Duo BSD-socketar. Standardvärdet är NX_WAIT_FOREVER (0xFFFFFFFF) eller, om icke-blockerande är aktiverat, NX_NO_WAIT (0x0).

- **SO_RCVBUF**: här anges fönster storleken för TCP-socketen. Standardvärdet NX_BSD_TCP_WINDOW har angetts till 64 KB för BSD TCP-socketar. Om du vill ställa in storleken över 65535 kräver att NetX Duo-biblioteket skapas med NX_TCP_ENABLE_WINDOW_SCALING definieras.

- **SO_REUSEADDR**: om den här inställningen är aktive rad kan flera Sockets mappas till en port. Den typiska användningen är för TCP-serverns socket. Detta är standard beteendet för NetX Duo-platser.

Den andra typen av alternativ för körning av socket är IP-alternativnivå. Om du vill aktivera ett alternativ för IP-nivå anropar du *Setsockopt* med option_level inställd på IP_PROTO och option_name anger alternativet t. ex. IP_MULTICAST_TTL *.* Om du vill hämta en alternativ inställning anropar du *getsockopt* för option_name med option_level återigen inställt på IP_PROTO.

Listan över alternativ för IP-nivå för körning visas nedan.

- **IP_MULTICAST_TTL**: Detta anger TTL-tiden för UDP-socketar. Standardvärdet är NX_IP_TIME_TO_LIVE (0x80) när socketen skapas. Det här värdet kan åsidosättas genom att anropa *Setsockopt* med alternativet socket.

- **IP_RAW_IPV6_HDRINCL**: om det här alternativet är inställt måste det anropande programmet lägga till ett IPv6-huvud och eventuellt program rubriker till data som skickas till RAW IPv6-Sockets som skapats av BSD. Om du vill använda det här alternativet måste rå socket-bearbetning vara aktiverat för IP-aktiviteten.

- **IP_ADD_MEMBERSHIP**: om det här alternativet är aktiverat aktiverar det här alternativet BSD-socketen (gäller endast UDP-socketar) för att ansluta till den angivna IGMP-gruppen.

- **IP_DROP_MEMBERSHIP**: om det här alternativet är aktiverat aktiverar det här alternativet BSD-socketen (gäller endast UDP-socketar) för att lämna den angivna IGMP-gruppen.

- **IP_HDRINCL**: om det här alternativet är inställt måste det anropande programmet lägga till IP-huvudet och eventuellt program huvuden till data som skickas på obehandlade IPv4-socketar som skapats i BSD. Om du vill använda det här alternativet måste rå socket-bearbetning vara aktiverat för IP-aktiviteten.

- **IP_RAW_RX_NO_HEADER**: om alternativet är avmarkerat inkluderas IPv6-huvudet med mottagna data för RAW IPv6-Sockets som skapats i BSD. IPv6-huvuden tas bort som standard i BSD RAW IPv6-socketar och paket längden inkluderar inte IPv6-huvudet.

Om det här alternativet anges tas IPv4-sidhuvudet bort från mottagna data på BSD RAW-socketar av typen IPv4. IPv4-huvuden ingår som standard i BSD RAW IPv4-socketar och paket längden inkluderar IPv4-huvudet.

Det här alternativet har ingen påverkan på antingen IPv4-eller IPv6-överförings data.

## <a name="small-ipv4-example"></a>Exempel på små IPv4

Ett exempel på hur du använder NetX Duo BSD-tjänster för IPv4-nätverk beskrivs nedan. I det här exemplet tas include-filen *nxd_bsd. h* in på rad 8. Därefter skapas IP-instansen *bsd_ip* och packet pool *bsd_pool* som globala variabler på rad 20 och 21. Observera att den här demon använder en ram-drivrutin (virtuellt nätverk)*, _nx_ram_network_driver*. Klienten och servern kommer att dela samma IP-adress på en enskild IP-instans i det här exemplet.

Klient-och Server trådarna skapas på raderna 62 och 68. BSD-adresspoolen för överföring av paket skapas på rad 78 och används i skapa IP-instans på rad 87. Observera att IP-trådens aktivitet får prioritet 1 i *nx_ip_create* -anropet. Den här tråden bör vara den högsta prioritets uppgiften som definierats i programmet för optimal NetX-prestanda.

IP-instansen är aktive rad för ARP-och TCP-tjänster på raderna 88 och 110. Det senaste kravet innan BSD-tjänster kan användas är att anropa *bsd_initialize* på rad 120 för att konfigurera alla data strukturer och netx-och ThreadX-resurser som krävs av BSD.

Funktionen Server tråd post definieras härnäst. BSD TCP-socketen skapas på rad 149. Serverns IP-adress och Port har angetts på raderna 160-163. Observera användningen av värden för byte av nätverks byte *htonl* och *htons* som tillämpas på IP-adressen och porten. Detta är i överensstämmelse med BSD socket-specifikationen att data för flera byte skickas till BSD-tjänsterna i nätverkets byte ordning.

Sedan binds huvud serverns socket till porten med hjälp av *BIND* -tjänsten på rad 166. Detta är lyssnings-socketen för TCP-begäranden med hjälp av *lyssnar* tjänsten på rad 180. Härifrån kan du *thread_server_entry*, loopar för att söka efter mottagnings händelser med hjälp av funktionen *Välj* samtal på rad 202. Om en Receive-händelse är en anslutningsbegäran, som bestäms genom att jämföra listan med Läs klara, så anropas *den på rad* 213. En underordnad server-socket tilldelas för att hantera anslutningsbegäran och läggas till i huvud listan över TCP-server-socketar som är anslutna till en klient på rad 223. Om det inte finns några nya anslutnings begär Anden, kontrollerar Server tråden alla anslutna Sockets för att ta emot händelser i for-loopen med början på rad 236. När en Receive-händelse *väntar på anrop* , anropas *Skicka* och ta emot på denna socket tills inga data tas emot (anslutningen stängs på den andra sidan) och socketen stängs med hjälp av *soc_close* tjänsten på rad 277.

När Server tråden har ställts in skapar funktionen klient tråd post *thread_client_entry* en socket på rad 326 och ansluter med TCP-serverns socket med hjälp av *anslutnings* anropet på rad 337. Sedan loopar de för att skicka och ta emot paket med hjälp *av tjänsterna* *Skicka* och ta emot. När inga fler data tas emot, stängs socketen på rad 398 med hjälp av tjänsten *soc_close* . Efter från kopplingen skapar funktionen klient tråd post en ny TCP-socket och gör en annan anslutningsbegäran i loopen igång på rad 321.

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

## <a name="small-ipv6-example-system"></a>Exempel system för små IPv6-system

Ett exempel på hur du använder NetX Duo BSD-tjänster för IPv6-nätverk beskrivs i programmet nedan. Det här exemplet påminner mycket om demonstrations programmet för IPv4 som tidigare beskrivits med några viktiga skillnader.

Klient-och Server trådarna, BSD-adresspoolen, IP-instansen och BSD-Initieringen sker på samma sätt som för IPv4 BSD-socketar.

I funktionen Server tråd inmatning definierar *thread_server_entry* en par IPv6-variabler som använder *sockaddr_in6* och *NXD_ADDRESS* data typer på raderna 145-148. Data typen NXD_ADDRESS kan faktiskt lagra både IPv4-och IPv6-adress typer.

Sedan aktiverar Server tråden IPv6 och ICMPv6 på IP-instansen med hjälp av *nxd_ipv6_enable* och *nxd_icmpv6_enable* tjänst på rad 161 och 169. Sedan registreras lokala länkar och globala IP-adresser med IP-instansen. Detta görs med hjälp av *nxd_ipv6_address_set* -tjänsten på raderna 180 och 195. Därefter är det tillräckligt länge för IP-trådens uppgift att slutföra det duplicerade adress identifierings protokollet och registrera dessa adresser som giltiga adresser på *tx_thread_sleep* -anropet på rad 201.

Därefter skapas TCP-serverns socket med argumentet AF_INET6 indatamängds typ på rad 204. Socket-IPv6-adressen och porten är inställda på raderna 216-221, om du ombeds att använda *htonl* -och *htons* -makron för att lägga till data i byte ordningen i nätverket för BSD socket Services. Härifrån är funktionen för Server tråd inmatning nästan identisk med IPv4-exemplet.

Funktionen klient tråd post, *thread_client_entry*, definieras härnäst. Observera att eftersom TCP-klienten i det här exemplet delar samma IP-instans och IPv6-adress som TCP-servern, behöver vi inte aktivera IPv6-eller ICMPv6-tjänster på IP-instansen igen. Dessutom har IPv6-adressen redan registrerats med IP-instansen. I stället väntar klient tråd posten bara på rad 368 för att servern ska kunna konfigureras. Server adressen och porten anges, med hjälp av värden till bytes för byte i nätverk på rad 387-392 och klienten kan ansluta till TCP-servern på rad 412. Observera att de lokala IP-adressens data typer på raderna 378-383 bara används för att demonstrera *getsockname* -och *getpeername* -tjänsterna på raderna 425 respektive 434. Eftersom data kommer från nätverket kommer nätverket att vara värd för byte av byte-ordning som används i raderna 378-383.

Nästa funktion i klient tråds funktionen anger en loop i vilken den skapar en TCP-socket, gör en TCP-anslutning och skickar och tar emot data med TCP-servern tills inga fler data tas emot i stort sett samma som IPv4-exemplet. Den stänger sedan socketen på rad 483, pausar en kort stund och skapar en annan TCP-socket och begär en TCP-server anslutning.

En viktig skillnad med IPv4-exemplet är att *socket* -anropen anger en IPv6-socket med argumentet AF_INET6 indataargumentet. En annan viktig skillnad är att TCP client *Connect* -anropet använder *sockaddr_in6* datatyp och ett längd argument har angetts till storleken på data typen *sockaddr_in6* .

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
