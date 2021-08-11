---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX DHCP-server
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX DHCP-serverkomponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04cbf4c9529538c3b5db6f8045a28bbcad5861c6ce846a898fa3ba1c7d97b19f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799582"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-dhcp-server"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX DHCP-server

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX DHCP-komponenten.

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS NetX DHCP-servern kan hämtas från vår offentliga källkodsdatabas på [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nx_dhcp_server.h:** Rubrikfil för NetX DHCP-server
- **nx_dhcp_server.c:** C-källfil för NetX DHCP-server
- **nx_dhcp_server.pdf:** PDF-beskrivning av NetX DHCP-server
- **demo_netx_dhcp_server.c:** Demonstration av NetX DHCP-server

## <a name="dhcp-installation"></a>DHCP-installation

För att kunna använda NetX DHCP-servern ska hela distributionen som nämns ovan kopieras till samma katalog där NetX är installerat. Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*" ska *filerna nx_dhcp_server.h* *och nx_dhpc_server.c* kopieras till den här katalogen.

## <a name="using-netx-dhcp-server"></a>Använda NetX DHCP-server

Det är enkelt att använda NetX DHCP-servern. I princip måste programkoden innehålla *nx_dhcp_server.h* efter att den *innehåller tx_api.h* och *nx_api.h*, för att kunna använda ThreadX respektive NetX. När *nx_dhcp_server.h* ingår kan programkoden sedan göra DHCP-funktionsanrop som anges senare i den här guiden. Programmet måste också inkludera *nx_dhcp_server.c* i byggprocessen. Den här filen måste kompileras på samma sätt som andra programfiler och dess objektformulär måste länkas tillsammans med programmets filer. Mer information om hur du använder NetX DHCP-servern finns i följande avsnitt Krav för [NetX DHCPServer](#requirements-of-the-netx-dhcp-server) och [begränsningar för NetX DHCP-servern](#constraints-of-the-netx-dhcp-server).

> [!NOTE]
> Eftersom DHCP använder NetX UDP-tjänster måste UDP aktiveras med nx_udp_enable *innan* DHCP används.

## <a name="requirements-of-the-netx-dhcp-server"></a>Krav för NetX DHCP-servern

NetX DHCP-servern kräver en UDP-socketport tilldelad till den välkända DHCP-porten 67. För att kunna skapa DHCP-servern måste programmet skapa en paketpool med paketnyttolast på minst 548 byte plus IP-, UDP- och Ethernet-huvuden (totalt 44 byte med 4 bytejustering).

Det förutsätts att både servern och klienten använder adressinställningar för Ethernet-maskinvara:

- **Maskinvarutyp:** 1
- **Maskinvarulängd:** 6
- **Hopp:** 0

### <a name="multiple-client-sessions"></a>Flera klientsessioner

NetX DHCP-servern kan hantera flera klientsessioner genom att ha en tabell med aktiva DHCP-klienter och vilket "tillstånd" klienten är i, t.ex. DHCP-tillstånd INIT, BOOT, SELECTING, REQUESTING, RENEWING osv. Om sessionens time out går ut innan nästa klientmeddelande tas emot, såvida inte klienten är bunden till ett IP-lån, rensar servern klientsessionsdata och returnerar den tilldelade IP-adressen till den tillgängliga poolen. Om servern tar emot flera DISCOVER-meddelanden från samma klient återställer servern sessionens time out och behåller den IP-adress som reserverats för klienten att acceptera i ett efterföljande BEGÄRAN-meddelande.

NetX DHCP-servern accepterar även klientens DHCP-begäran med ett enda tillstånd, t.ex. att klienten bara skickar ett REQUEST-meddelande. Detta förutsätter att klienten tidigare har tilldelats ett IP-lån från DHCP-servern.

### <a name="setting-interface-specific-network-parameters-server-responses"></a>Ange gränssnittsspecifika serversvar för nätverksparametrar

Programmet kan ange parametrarna router, nätmask och DNS-server för varje gränssnitt som det hanterar DHCP-klientbegäranden med hjälp *nx_dhcp_set_interface_network_parameters* tjänsten. Annars är dessa parametrar standard för IP-gatewayen på serverns primära gränssnitt, dess DHCP-nätverksundernät respektive DHCP-serverns IP-adress.

DHCP-servern innehåller dessa parametrar i alternativdata för DHCP-meddelanden som skickas till DHCP-klienter.

### <a name="assigning-ip-addresses-to-the-client"></a>Tilldela IP-adresser till klienten

Om client DISCOVER-meddelandet inte anger en begärd IP-adress kan DHCP-servern använda en från sin egen pool. Om servern inte har några tillgängliga IP-adresser skickar den klienten ett AV-meddelande.

NetX DHCP-servern beviljar den begärda IP-adressen i meddelandet Klientbegäran så länge IP-adressen är tillgänglig och finns i serverns IP-adressdatabas. Programmet skapar serverns lista över tillgängliga IP-adresser för tilldelning  till DHCP-klienter med hjälp av nx_dhcp_create_server_ip_address_list tjänsten. Om servern inte har de begärda IP-adresserna eller om den är tilldelad till en annan värd, skickar den klienten ett MEDDELANDE TILL KLIENTEN.

När DHCP-servern tar emot en klientbegäran identifierar den klienten unikt med hjälp av KLIENTENs MAC-adress i fältet Klient-MAC-adress i DHCP-meddelandet. Om klienten ändrar sin MAC-adress eller flyttas någon annanstans till ett annat undernät bör den skicka ett RELEASE-meddelande till servern för att returnera IP-adressen tillbaka till den tillgängliga poolen och begära en ny IP-adress i INIT-tillståndet.

Mer information finns i bild 1.1 i avsnittet **Litet** exempelsystem. Antalet IP-adresser som sparas till DHCP-serverinstansen är begränsat till storleken på serveradressmatrisen i DHCP-serverns kontrollblock och definieras av det konfigurerbara NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.

### <a name="ip-address-lease-times"></a>IP-adresslåntider

DHCP-servern accepterar också begäran Klientens lånetid om lånetiden är kortare än den standardtid för serverlån som definieras i konfigurerbar alternativ NX_DHCP_DEFAULT_LEASE_TIME. Förnyelse- och återbindningstiderna som tilldelas klienten är 50 % respektive 85 % av lånetiden, såvida inte lånetiden är oändlig (0xFFFFFFFF), i vilket fall förnyelse- och ombindningstider också är inställda på oändlighet.

### <a name="dhcp-server-timeouts"></a>Tidsgränser för DHCP-server

DHCP-servern har en användarkonfigurerbar tidsgräns för sessionen, NX_DHCP_CLIENT_SESSION_TIMEOUT, för att vänta på nästa DHCP-klientmeddelande om inte sessionen har slutförts. Time out återställs när servern tar emot nästa meddelande från klienten oavsett om samma meddelande har skickats tidigare.

### <a name="internal-error-handling"></a>Intern felhantering

DHCP-servern tar emot och bearbetar  DHCP-klientpaket i nx_dhcp_listen_for_messages-funktionen. Den här funktionen avbryter bearbetningen av det aktuella DHCP-klientpaketet om paketet är ogiltigt, eller om DHCP-servern påträffar ett internt fel.n *x_dhcp_listen_for_messages* returnerar en felstatus. DHCP-servertråden tar bort kontrollen en kort stund av ThreadX-schemaläggaren innan den här funktionen anropas för att ta emot nästa DHCP-klientmeddelande. I den aktuella versionen finns det inget loggningsstöd för felstatus som returneras *från nx_dhcp_listen_for_messages.*

### <a name="option-55-parameter-request-list"></a>Alternativ 55: Lista över parameterbegäran

NetX DHCP-servern måste konfigureras med en uppsättning alternativ för att läsa in till listan med alternativ för parameterbegäran (55) i erbjudande- och DHCPACK-meddelanden som skickas tillbaka till klienten. Dessa alternativ bör innehålla nätverkskritiska konfigurationsdata för klientnätverket och definieras som standard som router-IP-adress, nätmask och DNS-server. Alternativlistan är en blankstegsavgränsad lista som definieras i den användarkonfigurerbara NX_DHCP_DEFAULT_SERVER_OPTION_LIST. Observera att antalet alternativ som anges i den här listan måste vara lika NX_DHCP_DEFAULT_OPTION_LIST_SIZE som också är användardefinierat.

## <a name="constraints-of-the-netx-dhcp-server"></a>Begränsningar för NetX DHCP-servern

### <a name="dhcp-messages"></a>DHCP-meddelanden

NetX DHCP-servern verifierar inte att en IP-adress inte har tilldelats någon annanstans i nätverket innan IP-adressen tilldelas till klienten. Om det finns flera DHCP-servrar kan detta vara fallet. *Enligt RFC 2131* är det klientens ansvar att kontrollera att IP-adressen är unik i nätverket (t.ex. att pinga adressen). Om den inte är det bör servern ta emot ett NEKA-meddelande med IP-adressen för att uppdatera databasen från klienten.

NetX DHCP-servern utfärdar inte FORCE_RENEW meddelanden. Det är upp till DHCP-klienten att förnya sitt IP-adresslån. DHCP-servern övervakar dock återstående tid på alla tilldelade IP-adresser i databasen. När ett IP-adresslån upphör att gälla returneras DEN IP-adressen till poolen med tillgängliga IP-adresser. Det är därför upp till klienten att aktivt förnya/binda om ip-adresslånet.

Sessionsdata rensas så snart klienten antingen beviljas ("bunden") till ett IP-lån (eller så förnyas ett befintligt). Om ett klientpaket visar sig vara felaktigt, eller om klientens tid tar slut mellan svaren, rensas sessionsdata.

### <a name="saving-data-between-reboots"></a>Spara data mellan omstarter

NetX DHCP-servern sparar klientdata inklusive parametrar för DHCP-begäran i en klientposttabell. Den här tabellen lagras inte i beständigt minne, så om DHCP-servervärden måste starta om den informationen sparas inte mellan omstarter.

NetX DHCP-servern sparar IP-adresslåndata i en IP-adresstabell. Den här tabellen lagras inte i beständigt minne, så om DHCP-servervärden måste starta om den informationen sparas inte mellan omstarter.

### <a name="relay-agents"></a>Relay-agenter

NetX DHCP-servern har konfigurerats med en noll IP-adress för fältet "Relay agent" eftersom den inte stöder DHCP-begäranden i nätverket.

## <a name="small-example-system"></a>Litet exempelsystem

Ett exempel på hur enkelt det är att använda NetX DHCP-servern beskrivs i bild 1.1 som visas nedan. I det här exemplet tas *DHCP-indelningsfilen nx_dhcp_server.h* in på rad 5. STORLEKEN på DHCP-serverns trådstack, IP-trådstackens storlek och testtrådstackens storlek definieras på raderna 7–13.

Först skapas en valfri testtrådsaktivitet för att stoppa, starta om och så småningom ta bort DHCP-servern med funktionen "*test_thread_entry*" på rad 57. Ett DHCP-serverkontrollblock *" dhcp_server*" definieras som en global variabel på rad 20. Observera att serverpaketpoolen skapas med paket som har en nyttolast som är minst lika stor som dhcp-standardmeddelandet (548 byte plus IP- och UDP-huvudbyte). När du har skapat en IP-instans för DHCP-servern skapar programmet DHCP-servern på rad 96. Därefter aktiverar programmet server-IP-instansen för att vara UDP-aktiverad. Innan du startar DHCP-servern skapas den tillgängliga IP-adresslistan på rad 137 med *hjälp av nx_dhcp_create_server_ip_address_list tjänsten.* Nätverkskonfigurationsparametrarna anges på följande rad 138 med *hjälp av nx_dhcp_set_interface_network_parameters-tjänsten.* DHCP-servertjänster blir tillgängliga när programmet anropar *nx_dhcp_server_start* på rad 141. Testtrådsaktiviteten visar användningen av att stoppa och starta om DHCP-servern.

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

Bild 1.1 Exempel på NetX DHCP-serverprogram

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ för att skapa NetX DHCP-server. I följande lista beskrivs var och en i detalj:  
  
- **NX_DISABLE_ERROR_CHECKING:** Det här alternativet tar bort den grundläggande DHCP-felkontrollen. Det används vanligtvis när programmet har felsökt.  
- **NX_DHCP_SERVER_THREAD_PRIORITY:** Det här alternativet anger prioriteten för DHCP-servertråden. Som standard anger det här värdet att DHCP-tråden körs med prioritet 2.
- **NX_DHCP_TYPE_OF_SERVICE:** Det här alternativet anger vilken typ av tjänst som krävs för DHCP UDP-begäranden. Som standard definieras det här värdet som NX_IP_NORMAL för att indikera normal IP-pakettjänst.
- **NX_DHCP_FRAGMENT_OPTION:** Aktivera fragment för DHCP UDP-begäranden. Som standard är det här värdet inställt på NX_DONT_FRAGMENT inaktivera UDP-fragmentering.
- **NX_DHCP_TIME_TO_LIVE:** Anger antalet routrar som paketet kan passera innan det tas bort. Standardvärdet är 0x80.
- **NX_DHCP_QUEUE_DEPTH** Anger antalet paket som DHCP-serversocketen behåller innan kön rensas. Standardvärdet är 5.
- **NX_DHCP_PACKET_ALLOCATE_TIMEOUT:** Anger timeout-värdet i timer tick för netX DHCP-servern att vänta på att ett paket ska allokeras från paketpoolen. Standardvärdet är inställt på NX_IP_PERIODIC_RATE.
- **NX_DHCP_SUBNET_MASK:** Det här är nätmasken som DHCP-klienten ska konfigureras med. Standardvärdet är inställt på 0xFFFFFF00.
- **NX_DHCP_FAST_PERIODIC_TIME_INTERVAL:** Det här är timeout-perioden i timer tick för DHCP-serverns snabba timer för att kontrollera återstående sessionstid och hantera sessioner som har en tidsgräns.
- **NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL:** Det här är timeout-perioden i timer tick för DHCP-serverns långsamma timer för att kontrollera återstående IP-adresslåntid och hantera lån som har timeout.
- **NX_DHCP_CLIENT_SESSION_TIMEOUT:** Det här är timeout-perioden i timern tickar dhcp-servern väntar på att få nästa DHCP-klientmeddelande.
- **NX_DHCP_DEFAULT_LEASE_TIME:** Det här är IP-adresslåntiden i sekunder som tilldelats TILL DHCP-klienten och grunden för beräkning av förnyelse- och bindningstiderna som också tilldelats klienten. Standardvärdet är inställt på 0xFFFFFFFF (oändligt).
- **NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE:** Det här är storleken på DHCP-servermatrisen för att hålla tillgängliga IP-adresser för tilldelning till klienten. Standardvärdet är 20.
- **NX_DHCP_CLIENT_RECORD_TABLE_SIZE:** Det här är storleken på DHCP-servermatrisen för att hålla klientposter. Standardvärdet är 50.
- **NX_DHCP_CLIENT_OPTIONS_MAX:** Det här är storleken på matrisen i DHCP-klientinstansen för att hålla alla begärda alternativ i listan med parameterbegäran i den aktuella sessionen. Standardvärdet är 12.
- **NX_DHCP_OPTIONAL_SERVER_OPTION_LIST:** Det här är bufferten som innehåller DHCP-serverns standardlista över alternativ för att tillhandahålla till den aktuella DHCP-klienten i listan över parameterbegäran. Standardvärdet är "1 3 6".
- **NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE:** Det här är storleken på matrisen som ska innehålla DHCP-serverns standardlista över alternativ. Standardvärdet är 3.
- **NX_DHCP_SERVER_HOSTNAME_MAX:** Det här är storleken på bufferten för att lagra servervärdnamnet. Standardvärdet är 32.
- **NX_DHCP_CLIENT_HOSTNAME_MAX:** Det här är storleken på bufferten för att lagra klientvärdnamnet i den aktuella DHCP-serverklientsessionen. Standardvärdet är 32.
