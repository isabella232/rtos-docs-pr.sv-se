---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX DHCP-servern
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av komponenten Azure återställnings tider NetX DHCP-server.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 034a4d74c566fbfe94981a42b7e06e7f2ee79d25
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826790"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-dhcp-server"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX DHCP-servern

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX DHCP-komponenten.

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider NetX DHCP-server kan hämtas från vår offentliga käll kods lagrings plats på [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nx_dhcp_server. h**: rubrik fil för netx DHCP-server
- **nx_dhcp_server. c**: c-källfil för netx DHCP-server
- **nx_dhcp_server.pdf**: PDF-Beskrivning av netx DHCP-server
- **demo_netx_dhcp_server. c**: netx DHCP-server demonstration

## <a name="dhcp-installation"></a>DHCP-installation

För att kunna använda NetX DHCP-server, ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX har installerats. Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*", ska *nx_dhcp_server. h* -och *nx_dhpc_server. c* -filerna kopieras till den här katalogen.

## <a name="using-netx-dhcp-server"></a>Använda NetX DHCP-server

Det är enkelt att använda NetX DHCP-server. I princip måste program koden innehålla *nx_dhcp_server. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX respektive netx. När *nx_dhcp_server. h* ingår kan program koden sedan göra DHCP-funktions anropen angivna senare i den här hand boken. Programmet måste även innehålla *nx_dhcp_server. c* i build-processen. Den här filen måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer. Mer information om hur du använder NetX DHCP-server finns i följande avsnitt [krav för netx](#requirements-of-the-netx-dhcp-server) DHCP [Server och begränsningar för netx DHCP-server](#constraints-of-the-netx-dhcp-server).

> [!NOTE]
> Eftersom DHCP använder sig av NetX UDP-tjänster måste UDP aktive ras med det *nx_udp_enable* samtalet innan DHCP används.

## <a name="requirements-of-the-netx-dhcp-server"></a>Krav för DHCP-servern NetX

NetX DHCP-servern kräver en UDP-socketanslutning som tilldelats den välkända DHCP-porten 67. För att skapa DHCP-servern måste programmet skapa en modempool med paket nytto Last minst 548 byte plus IP-, UDP-och Ethernet-huvuden (som totalt 44 byte med 4 byte justering).

Det förutsätts att både servern och klienten använder inställningarna för Ethernet-maskinvara:

- **Maskin varu typ**: 1
- **Maskin varu längd**: 6
- **Hopp**: 0

### <a name="multiple-client-sessions"></a>Flera klientsessioner

NetX DHCP-servern kan hantera flera klientsessioner genom att ha en tabell med aktiva DHCP-klienter och det tillstånd som klienten är i t. ex. DHCP-tillstånd INIT, start, välja, begära, förnya osv. Om tids gränsen för sessionen upphör att gälla innan nästa klient meddelande tas emot, om inte klienten är kopplad till ett IP-lån, rensar servern klientens sessionsdata och returnerar den tilldelade IP-adressen till den tillgängliga poolen. Om servern tar emot flera IDENTIFIERINGs meddelanden från samma klient återställs tids gränsen för sessionen och den IP-adress som är reserverad för klienten godkänns i ett efterföljande begär ande meddelande.

DHCP-NetX accepterar också klient-begäran med enskild tillstånd, t. ex. klienten skickar endast ett meddelande om begär Ande. Detta förutsätter att klienten har tilldelats ett IP-lån från DHCP-servern tidigare.

### <a name="setting-interface-specific-network-parameters-server-responses"></a>Ställer in gränssnitts information Server svar för nätverks parametrar

Programmet kan ange router, nätmask och DNS-serverns parametrar för varje gränssnitt som hanteras av DHCP-klienter med hjälp av tjänsten *nx_dhcp_set_interface_network_parameters* . Annars är dessa parametrar standardiserade till IP-gatewayen på serverns primära gränssnitt, dess DHCP-undernät och IP-adressen för DHCP-servern.

DHCP-servern inkluderar dessa parametrar i alternativ data för DHCP-meddelanden som skickas till DHCP-klienter.

### <a name="assigning-ip-addresses-to-the-client"></a>Tilldela IP-adresser till klienten

Om klient IDENTIFIERINGs meddelandet inte anger någon begärd IP-adress kan DHCP-servern använda en från sin egen pool. Om servern inte har några tillgängliga IP-adresser kommer den att skicka ett NACK-meddelande till klienten.

NetX DHCP-servern kommer att bevilja den begärda IP-adressen i klient begär ande meddelandet så länge IP-adressen är tillgänglig och finns i serverns IP-serverdatabas. Programmet skapar serverns lista över tillgängliga IP-adresser för att tilldela DHCP-klienter med hjälp av tjänsten *nx_dhcp_create_server_ip_address_list* . Om servern inte har de begärda IP-adresserna eller om den är tilldelad till en annan värd kommer den att skicka ett NACK-meddelande till klienten.

När DHCP-servern tar emot en klientbegäran, identifierar den klienten unikt med klientens MAC-adress i fältet klientens MAC-adress i DHCP-meddelandet. Om klienten ändrar sin MAC-adress eller flyttas någon annan stans till ett annat undernät bör den skicka ett RELEASE-meddelande till servern för att returnera IP-adressen tillbaka till den tillgängliga poolen och begära en ny IP-adress i INIT-tillstånd.

Mer information finns i bild 1,1 i system avsnittet för **små exempel** . Antalet IP-adresser som sparas till DHCP-serverinstansen är begränsat till storleken på server adress matrisen i DHCP-serverns kontroll block och definieras av det konfigurerbara alternativet NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.

### <a name="ip-address-lease-times"></a>IP-adressens låne tider

DHCP-servern kommer också att acceptera låne tiden för klient begär Anden om den här låne tiden är mindre än serverns standard låne tid som definieras i konfigurerbart alternativ NX_DHCP_DEFAULT_LEASE_TIME. Förnyelse-och återbind-tider som tilldelats till klienten är 50% och 85% av låne tiden, om inte låne tiden är oändlig (0xFFFFFFFF), vilket innebär att förnyelse och OMBINDNINGS tid också anges till oändlighet.

### <a name="dhcp-server-timeouts"></a>Timeout för DHCP-server

DHCP-servern har en tids gräns för användare som kan konfigureras, NX_DHCP_CLIENT_SESSION_TIMEOUT, för att vänta på nästa DHCP-klientcertifikat om inte sessionen har slutförts. Tids gränsen återställs när servern tar emot nästa meddelande från klienten oavsett om samma meddelande redan har skickats.

### <a name="internal-error-handling"></a>Intern fel hantering

DHCP-servern tar emot och bearbetar DHCP-klientens paket i *nx_dhcp_listen_for_messages* -funktionen. Den här funktionen upphör att bearbeta det aktuella DHCP-klientprogrammet om paketet är ogiltigt, eller så påträffar DHCP-servern ett internt fel. n *x_dhcp_listen_for_messages* returnerar en fel status. DHCP-serverrollen låser sig kort av ThreadX Scheduler innan den här funktionen anropas för att ta emot nästa DHCP-klient meddelande. I den aktuella versionen finns det ingen loggnings support för fel status från *nx_dhcp_listen_for_messages.*

### <a name="option-55-parameter-request-list"></a>Alternativ 55: lista över parameter begär Anden

DHCP-NetX måste konfigureras med en uppsättning alternativ som ska läsas in i listan med alternativ för parameter förfrågan (55) i erbjudandet och DHCPACK-meddelanden som skickas tillbaka till klienten. De här alternativen bör inkludera nätverks kritiska konfigurations data för klient nätverket och definieras som standard som routerns IP-adress, nätmask och DNS-server. Alternativ listan är en blankstegsavgränsad lista och definieras i den användare som kan konfigureras NX_DHCP_DEFAULT_SERVER_OPTION_LIST. Observera att antalet alternativ som anges i den här listan måste vara lika NX_DHCP_DEFAULT_OPTION_LIST_SIZE som också är användardefinierad.

## <a name="constraints-of-the-netx-dhcp-server"></a>Begränsningar för DHCP-servern NetX

### <a name="dhcp-messages"></a>DHCP-meddelanden

NetX DHCP-servern verifierar inte att en IP-adress inte har tilldelats någon annan stans i nätverket innan IP-adressen beviljas till klienten. Om det finns flera DHCP-servrar kan detta vara fallet. *Enligt RFC 2131 är det klientens ansvar att kontrol lera att IP-adressen är unik i nätverket* (t. ex. pinga adressen). Om så inte är fallet bör servern ta emot ett neka-meddelande med IP-adressen för att uppdatera sin databas från klienten.

NetX-DHCP-servern utfärdar inte FORCE_RENEW meddelanden. Det är upp till DHCP-klienten som förnyar IP-adresslån. DHCP-servern övervakar dock den återstående tiden på alla tilldelade IP-adresser i databasen. När ett IP-adresslån upphör att gälla returneras den IP-adressen till poolen med tillgängliga IP-adresser. Därför är det upp till klienten att aktivt förnya/ombinda sitt IP-adresslån.

Sessionsdata rensas så snart klienten beviljas ("bound") till ett IP-lån (eller en befintlig förnyas). Om ett klient paket bevisar falsk eller om klientens tids gräns mellan svaren rensas, rensas sessionens data.

### <a name="saving-data-between-reboots"></a>Spara data mellan omstarter

NetX DHCP-servern sparar klient data inklusive parametrar för DHCP-begäran i en klient post tabell. Den här tabellen lagras inte i icke-flyktigt minne, så om DHCP-serverns värd måste starta om den informationen inte sparas mellan omstarter.

NetX DHCP-servern sparar data för IP-adresslån i en IP-adress tabell. Den här tabellen lagras inte i icke-flyktigt minne, så om DHCP-serverns värd måste starta om den informationen inte sparas mellan omstarter.

### <a name="relay-agents"></a>Relä agenter

NetX DHCP-servern har kon figurer ATS med noll IP-adress för fältet "Relay Agent" eftersom den inte har stöd för out of Network DHCP-begäranden.

## <a name="small-example-system"></a>Litet exempel system

Ett exempel på hur enkelt det är att använda NetX DHCP-servern beskrivs i bild 1,1 som visas nedan. I det här exemplet tas DHCP-filen *nx_dhcp_server. h* in på rad 5. Stack storlek för DHCP-serverns tråd, stack storlek och test tråds stack storlek anges i rad 7-13.

Först skapar du en valfri test tråds aktivitet för att stoppa, starta om och slutligen ta bort DHCP-servern med funktionen "*test_thread_entry*" på rad 57. Ett kontroll block för DHCP-server (*dhcp_server*) definieras som en global variabel på rad 20. Observera att serverpoolen för servern skapas med paket som har en nytto last på minst lika stor som standard-DHCP-meddelandet (548 byte plus IP-och UDP-huvudets byte). När du har skapat en IP-instans för DHCP-servern skapar programmet DHCP-servern på rad 96. Därefter gör programmet det möjligt för Server-IP-instansen att vara UDP aktiverat. Innan du startar DHCP-servern skapas listan över tillgängliga IP-adresser på rad 137 med hjälp av tjänsten *nx_dhcp_create_server_ip_address_list* . Parametrarna för nätverks konfiguration anges på följande rad 138 med hjälp av tjänsten *nx_dhcp_set_interface_network_parameters* , blir DHCP-Server tjänsterna tillgängliga när programmet anropar *nx_dhcp_server_start* på rad 141. Uppgiften test tråd visar hur du stoppar och startar om DHCP-servern.

```c
/* This is a small demo of NetX DHCP Server for the high-performance NetX TCP/IP stack. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE       2048
#define     DEMO_SERVER_STACK_SIZE     2048
#define     SERVER_IP_ADDRESS_LIST     "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD             1000
#define     PACKET_POOL_SIZE           (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK     2048

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD          test_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_DHCP_SERVER     dhcp_server;

/* Define the counters used in the demo application... */

ULONG             state_changes;

/* Define thread prototypes. */

void     test_thread_entry(ULONG thread_input);
void     nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
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

    /* Create the test thread. */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
                pointer, TEST_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the DHCP Server packet pool. */
    status = nx_packet_pool_create(&server_pool, "NetX Main Packet Pool",
                                PACKET_PAYLOAD, pointer, PACKET_POOL_SIZE);
                                pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance. */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
                        0xFFFFFF00UL, &server_pool, nx_etherDriver_mcf5485, pointer,
                        SERVER_IP_THREAD_STACK, 1);

    pointer = pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors. */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance. */
    status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic. */
    status = nx_udp_enable(&server_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility. */
    status = nx_icmp_enable(&server_ip);

    /* Check for errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

    status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);
    status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                        NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                        IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server. */
    status = nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread. */
void     test_thread_entry(ULONG thread_input)
{

UINT     status;
UINT     keep_spinning;

    /* Just let the test thread be idle till we're ready to shut things down. */
    keep_spinning = 1;
    while(keep_spinning)
    {
        tx_thread_sleep(300);
    }

    printf("Stopping the server...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(500);

    printf("Starting the server...\n");
    status = nx_dhcp_server_start(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server start. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(600);

    printf("Stopping the server for good...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(200);

    printf("Deleting the server...\n");
    status = nx_dhcp_server_delete(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server delete. Status 0x%x\r\n", status);
        return;
    }
}
```

Figur 1,1 exempel NetX DHCP Server Application

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa NetX DHCP-server. I följande lista beskrivs var och en i detalj:  
  
- **NX_DISABLE_ERROR_CHECKING**: det här alternativet tar bort grundläggande fel sökning i DHCP. Den används vanligt vis efter fel sökning av programmet.  
- **NX_DHCP_SERVER_THREAD_PRIORITY**: det här alternativet anger prioriteten för DHCP-serverns tråd. Som standard anger det här värdet att DHCP-tråden körs vid prioritet 2.
- **NX_DHCP_TYPE_OF_SERVICE**: det här alternativet anger vilken typ av tjänst som krävs för DHCP UDP-begärandena. Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.
- **NX_DHCP_FRAGMENT_OPTION**: fragment aktivera för DHCP UDP-begäranden. Som standard är det här värdet inställt på NX_DONT_FRAGMENT för att inaktivera UDP-fragmentering.
- **NX_DHCP_TIME_TO_LIVE**: anger antalet routrar som paketet kan passera innan det tas bort. Standardvärdet är 0x80.
- **NX_DHCP_QUEUE_DEPTH** Anger antalet paket som DHCP-serverns socket behåller innan kön töms. Standardvärdet är 5.
- **NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: anger tids gränsen i timer-Tick för att netx DHCP-servern ska vänta på att allokera ett paket från paketets adresspool. Standardvärdet är inställt på NX_IP_PERIODIC_RATE.
- **NX_DHCP_SUBNET_MASK**: det här är nät masken som DHCP-klienten ska konfigureras med. Standardvärdet är inställt på 0xFFFFFF00.
- **NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: Detta är tids gräns i timer-Tick för DHCP-serverns snabba timer för att kontrol lera tiden som återstår och hantera sessioner som har nått tids gränsen.
- **NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: Detta är tids gräns i timer-Tick för DHCP-serverns långsamma timer för att kontrol lera om IP-adressen är kvar och hantera lån som har uppnådde sin tids gräns.
- **NX_DHCP_CLIENT_SESSION_TIMEOUT**: Detta är tids gräns i timer-Tick som DHCP-servern väntar på att ta emot nästa DHCP-klient meddelande.
- **NX_DHCP_DEFAULT_LEASE_TIME**: det här är IP-adressens låne tid i sekunder som tilldelats DHCP-klienten, och basen för att beräkna och återbinda tider som också har tilldelats till klienten. Standardvärdet är inställt på 0xFFFFFFFF (oändlighet).
- **NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: Detta är storleken på DHCP-serverns matris för att tillhandahålla tillgängliga IP-adresser för tilldelning till klienten. Standardvärdet är 20.
- **NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: Detta är storleken på DHCP-serverns matris för att lagra klient poster. Standardvärdet är 50.
- **NX_DHCP_CLIENT_OPTIONS_MAX**: Detta är storleken på matrisen i DHCP-klientens instans för att hålla alla begärda alternativ i listan parameter förfrågan i den aktuella sessionen. Standardvärdet är 12.
- **NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: det här är den buffert som innehåller DHCP-serverns standard lista med alternativ för att tillhandahålla den aktuella DHCP-klienten i listan med parameter begär Anden. Standardvärdet är "1 3 6".
- **NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: Detta är storleken på matrisen som innehåller DHCP-serverns standard lista med alternativ. Standardvärdet är 3.
- **NX_DHCP_SERVER_HOSTNAME_MAX**: storleken på bufferten för att placera serverns värdnamn. Standardvärdet är 32.
- **NX_DHCP_CLIENT_HOSTNAME_MAX**: storleken på bufferten för att placera klientens värdnamn i den aktuella DHCP-serverns klientsession. Standardvärdet är 32.
