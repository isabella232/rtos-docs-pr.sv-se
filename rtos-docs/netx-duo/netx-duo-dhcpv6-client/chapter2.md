---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo DHCPv6-klienten
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo DHCPv6-klient komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a154dbeb91b46a2c8bd5f4585e168a6b62d042ff
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826094"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcpv6-client"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo DHCPv6-klienten

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo DHCPv6-klient komponenten.

## <a name="product-distribution"></a>Produkt distribution

NetX Duo DHCPv6-klienten är tillgänglig på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nxd_dhcpv6_client. h** Rubrik fil för NetX DuoDHCPv6-klient

- **nxd_dhcpv6_client. c** Käll kods fil för NetX Duo DHCPv6-klienten

- **demo_netxduo_dhcpv6_client. c** Exempel program som demonstrerar installationen av NetX Duo DHCPv6-klienten

- **nxd_dhcpv6_client.pdf** PDF-Beskrivning av NetX Duo DHCPv6-klienten

## <a name="netx-duo-dhcpv6-client-installation"></a>NetX Duo DHCPv6-klient installation

Om du vill använda NetX Duo DHCPv6 client API kan hela distributionen som nämns ovan kopieras till samma katalog där NetX Duo är installerat. Om t. ex. NetX Duo är installerat i katalogen "*\threadx\arm7\green*" kan *nxd_dhcpv6_client. h* -och *nxd_dhpcv6_client. c* -filer kopieras till den här katalogen.

## <a name="using-the-netx-duo-dhcpv6-client"></a>Använda NetX Duo DHCPv6-klienten

Program koden måste innehålla *nxd_dhcpv6_client. h* när den innehåller *tx_api. h* och *nx_api. h*, för att använda Dhcpv6-klienten, ThreadX respektive netx Duo-tjänsterna. *nxd_dhcpv6_client. c* måste kompileras i projektet på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.

### <a name="span-classunderlineclient-dhcp-unique-identifier-duidspan"></a><span class="underline">Klientens DHCP-unika identifierare (DUID)</span>

Klientens DUID definierar unikt varje klient i ett nätverk. Ett program måste skapa ett klient-DUID innan du begär en IPv6-adress från en server. Klientens DUID ingår automatiskt i alla meddelanden till servern. För att skapa ett DUID anropar programmet tjänsten *nx_dhcpv6_create_client_duid:*
```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT duid_type, 
                                  UINT hardware_type, ULONG time);
```

Programmet anropar den här tjänsten och anger typen av DUID (endast länk lagret eller länk lagret plus tiden). För länk skiktet och tids DUIDs, kommer den här tjänsten att tillhandahålla fältet tid om tiden inte har angetts.

För att enheter ska starta om och vill använda ett tidigare tilldelat IPv6-adresslån måste programmet skapa klientens DUID som det som användes när du tilldelade IPv6-adressen. Länk skikt adressen är allt som behövs för att skapa ett DUID för ett länk lager klient. Detta kräver inte tidigare icke-flyktig minnes lagring om enheten har åtkomst till länk skikt adressen. För DUIDs av typen tid måste programmet ha åtkomst till samma tids data som används i föregående DUID och detta kräver icke-flyktigt minne. Klienter som inte har någon stabil lagring får inte använda DUIDs av typen Time.

### <a name="span-classunderlineclient-identity-association-for-non-temporary-addresses-ianaspan"></a><span class="underline">Klient identitets Association för icke-temporära adresser (IANA)</span>

Programmet måste skapa en IANA och eventuellt en eller flera IA-adresser innan du begär en IPv6-adress. För att göra detta anropar programmet *nx_dhcpv6_create_client_ianas* tjänsten. Om du vill skapa ett alternativ för en IA-adress anropar programmet *nx_dhcpv6_add_client_ia* tjänsten med en begärd IPv6-adress och livstids värden som ett tips till-servern.

I IANA och dess IAs definieras parametrarna för klientens IPv6-adress tilldelning:

Innan DHCPv6-klienten startas skapar DHCPv6-klient programmet en IANA med hjälp av tjänsten *nx_dhcpv6_create_client_iana* :

```C
UINT    nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                     UINT IA_ident, ULONG T1, ULONG T2);
```

Det måste också skapa en eller flera IAs med hjälp av *nx_dhcpv6_create_client_ia* tjänsten och begärda IPv6-adresser innan du startar Dhcpv6-klienten.

```C
UINT    nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                                NXD_ADDRESS *ipv6_address, 
                                ULONG preferred_lifetime, 
                                ULONG valid_lifetime);
```

> [!NOTE]
> Antalet AI-adresser som programmet skapar får inte överskrida NX_DHCPV6_MAX_IA_ADDRESS parameter vars standardvärde är 1.

NetX Duo DHCPv6-klienten har stöd för *nx_dhcpv6_create_client_ia* för äldre DHCPv6-klientprogram och som är identiska med *nx_dhcpv6_add_client_ia* men utvecklare uppmuntras att använda *nx_dhcpv6_add_client_ia* tjänsten.

Dessa tjänster visas i "litet exempel system" i det här kapitlet.

### <a name="span-classunderlinenon-volatile-memory-considerations-to-reuse-ianas-and-iasspan"></a><span class="underline">Icke-beständiga minnes överväganden för åter användning av IANAs och IAs</span>

Programmet måste spara IANA-parametrarna T1, T2 och IANA-identifieraren till icke-flyktigt minne om det vill använda samma adress (er) för att starta om. Programmet måste också spara sitt IA som innehåller dess IPv6-adress till icke-flyktigt minne.

Programmet måste också lagra den tid som förflutit som det har bundits till tilldelade IPv6-adresslån till icke-flyktigt minne om den stängs av. Detta sker genom att anropa tjänsten *nx_dhcpv6_get_time_accrued* innan den stoppar Dhcpv6-klienten.

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, 
                                ULONG *time_accrued);
```

Förutsatt att programmet har en oberoende klocka för att spåra tidsintervallet från när det stoppas och startas om DHCPv6-klienten efter en omstart, läggs den till den förfluten tid som förväntas i IPv6-lånet innan den stoppas. Nu startas aktiviteten klient tråd med den totala förfluten tid som har bundits till IPv6-lånet som nv_time indatatypen nedan:

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr, ULONG nv_time);
```

Från och med nu tar aktiviteten DHCPv6 client-tråd över den tid som periodiseras för IPv6-lånet för när lånet ska förnyas.

### <a name="span-classunderlinesetting-dhcpv6-option-dataspan"></a><span class="underline">Ange DHCPv6-alternativ data</span>

Innan ett IPv6-lån begärs kan programmet begära andra nätverks parameter data, till exempel DNS-server och tids Server. Vissa av dessa parametrar har vissa tjänster. Några visas nedan:

```C
UINT  nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT enable)

UINT  nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr, 
                                           UINT enable);
```

### <a name="span-classunderlineinitiating-the-ipv6-address-requestspan"></a><span class="underline">Initierar IPv6-adress förfrågan</span>

Programmet startar DHCPv6-klient tråden genom att anropa tjänsten *nx_dhcpv6_start* med noll som ingångs tid. För att initiera DHCPv6-protokollet för att begära en IPv6-adress anropar programmet *nx_dhcpv6_request_solicit.*

Om programmet vill använda ett tidigare tilldelat IPv6-lån anropas *nx_dhcpv6_start* med en tids gräns som inte är noll. Den ska inte anropa *nx_dhcpv6_request_solicit*.

Därefter behöver programmet inte göra något mer och DHCPv6-klienten övervakas automatiskt när det är dags att förnya eller binda om en IPv6-adress.

## <a name="small-example-system"></a>Litet exempel system

Ett exempel på hur enkelt det är att använda NetX Duo DHCPv6-klienten beskrivs i det lilla exemplet nedan med en DHCPv6-klient och en virtuell "RAM"-driv rutin. Den här demon förutsätter en enhet med endast ett enda fysiskt nätverks gränssnitt.

*tx_application_define* skapar en modempool för Dhcpv6-klienten att skicka DHCPv6-meddelanden. Det skapar också en program tråd och en IP-instans. Den aktiverar sedan UDP och ICMP på IP på raderna 130-148. Sedan skapas DHCPv6-klienten med återanrops funktioner för tillstånds ändring (*dhcpv6_state_change_notify* ) och Server fel (*dhcpv6_server_error_handler*) i line151.

I funktionen klient tråd inmatning *thread_client_entry*-klientens IP-adress konfigureras med en länk lokal adress och aktive ras för IPv6-och ICMPv6-tjänster på rad 202-217. Innan du startar DHCPv6-klienten skapar programmet en klient-DUID, ett IANA-alternativ och ett alternativ för en IA-adress på lines219-303. Alternativet för IA-adressen är valfritt om klienten vill begära en IPv6-adress och giltiga och önskade livs längder från servern. Servern kan eventuellt bevilja den begärda IPv6-adressen eller låne tiden. Programmet kan lägga till fler IA-alternativ (upp till NX_DHCPV6_MAX_IA_ADDRESS) som ska tilldelas flera globala adresser.

Slutligen anger programmet olika alternativ för att begära nätverks parametrar i sina meddelanden till DHCPv6-servern. DHCPv6-klientens aktivitet startas genom att anropa *nx_dhcpv6_start* i line306 och det faktiska DHCPv6-protokollet startas i SOLICIT-tillstånd med anropet till *nx_dhcpv6_request_solicit* på rad 317. DHCPv6-klienten hanterar sedan automatiskt befordran av klientens tillstånd via DHCPv6-protokollet tills det är kopplat till en adress eller ett fel uppstår. Under den här tiden väntar programmet på att protokollet ska slutföras, samt den duplicerade adress identifieringen (pappa) som ska slutföras om IP-instansen har kon figurer ATS för pappa (vilket är standard konfigurationen).

Efter tx_thread_sleep-anropet kontrollerar programmet på de globala parametrarna som anges i tillstånds ändringens motanrop för att fastställa framgången för både DHCPv6-klient aktiviteten för att få tilldelats ett IPv6-lån och i så fall att pappa-kontrollen är klar. Detta görs med hjälp av de räknare som ställts in i funktionerna för att återställa tillstånd och Server fel. Programmet avsöker för antalet address_not_assigned, address_expired och server_errors för misslyckad adress tilldelning. Om antalet bound_addresses inte är noll (minst en adress har tilldelats) söker den efter ett fel som inte är noll address_failed_dad för en pappa-kontroll. En förklaring av tillstånds ändringen och återanrop till Server fel följer:

Återanrop för tillstånds ändring, *dhcpv6_state_change_notify*, föregående och aktuella Dhcpv6-klient tillstånd för att avgöra om klienten tog emot några giltiga Server svar:

  - *dhcpv6_state_change_notify* söker efter över gångar direkt från begär att init, och om så är fallet ökar en räknare för att Dhcpv6-klienten får inga svar från servern.

Nästa *dhcpv6_state_change_notify* kontrollerar om klienten har tilldelats (bundits) till en eller flera IPv6-adresser:

  - Om det nya läget är kopplat ökar en räknare med adresser som är kopplade till klienten.
    
*Dhcpv6_state_change_notify* kontrollerar också om det finns en inpappa-kontroll:

  - Om tillstånds över gången från neka till INIT har DHCPv6-klienten upptäckt en pappa-kontroll på en av dess tilldelade adresser och ökar antalet misslyckade adress tilldelningar.
    
Den senaste kontrollen av *dhcpv6_state_change_notify* i det här exemplet är för en korrekt tilldelad adress som godkände pappa-kontrollen för att inte förnyas eller återbindas:

  - Om tillståndet ändras från ombind till INIT fick klienten inga svar på antingen förnyelse-eller OMBINDNINGS begär Anden och *dhcpv6_state_change_notify* ökar antalet utgångna adresser.

Om *dhcpv6_server_error_handler* om det visas ett meddelande om att Dhcpv6-klientens uppgift av en fel status som mottagits från servern, ökar antalet Server fel.

Under förutsättning att alla går bra skickar appen en fråga till DHCPv6-klienten för adress data, inklusive låne tider. Det får ett antal giltiga (tilldelade) adresser genom att anropa den *nx_dhcpv6_get_valid_ip_address_count* tjänsten och tiden att förnya i IANA (gäller alla IA-adresser tilldelade) genom att anropa *nx_dhcpv6_get_iana_lease_time* på raderna 372-392. Den skickar sedan en fråga till DHCPv6-klienten för var och en av dess IA-alternativ för IPv6-adress och låne tider med hjälp av adress index.

Vissa DHCPv6-klient tjänster (*nx_dhcpv6_get_lease_time_data, nx_dhcpv6_get_IP_address*) kräver inte ett adress index som indata och returnerar DHCPv6-parametrar för den primära klientens globala adress. Detta är lämpligt för klienter med en enda global IPv6-adress när den anropar *nx_dhcpv6_get_valid_ip_address_lease_time* på rad 384.

Med DHCPv6-klientens konfiguration NX_DHCPV6_CLIENT_RESTORE_STATE kan ett system återställa en tidigare skapad DHCPv6-klient i ett begränsat tillstånd mellan omstarter av systemet. Anropar *nx_dhcpv6_client_get_record* för att hämta Dhcpv6-klient posten mellan omstarter av systemet på rad 434, och anropar *nx_dhcpv6_client_restore_record* för att lagra DHCPV6-klient posten när systemet har startats på rad 525.

Programmet släpper sedan de tilldelade adresserna med hjälp av *nx_dhcpv6_request_release* tjänsten på rad 552. För att starta om programmet stoppar DHCPv6-klienten med *nx_dhcpv6_client_stop* tjänsten på rad 567 och rensar alla IPv6-adresser som registrerats med IP-instansen som har kon figurer ATS throughthe dhcpv6 client. Detta sker genom att anropa *nx_dhcpv6_reinitialize* på rad 578. Sedan startar den om DHCPv6-klient aktiviteten med *nx_dhcpv6_start* -och *nx_dhcpv6_request_solicit* -tjänster som tidigare.

DHCPv6-klienten tas bort med anropet till *nx_dhcpv6_delete* i line626. Observera att den inte tar bort den *e* -adresspool som den skapade för DHCPv6-klienten, eftersom den här poolen också används av IP-instansen. Annars bör den ta bort poolen om den inte längre används för att använda tjänsten NetX Duo *nx_packet_pool_delete* .

```C
/* This is a small demo of the NetX Duo DHCPv6 Client for the high-performance NetX Duo stack. */

#include    <stdio.h>
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcpv6_client.h"

#ifdef FEATURE_NX_IPV6
#define     DEMO_STACK_SIZE         2048

/* Set the client address, and request these address from DHCPv6 Server. */
/*
#define     NX_DHCPV6_REQUEST_IA_ADDRESS
*/

/* Set the list of DHCPv6 option data (timezone, DNS server, timer server, domain name)to get from the DHCPv6 server. */

#define     NX_DHCPV6_REQUEST_OPTION


/* Add the fully qualified domain name to request whether the DHCPv6 server SHOULD or SHOULD NOT perform the AAAA RR or DNS updates. */

#define     NX_DHCPV6_REQUEST_FQDN_OPTION


/* Define the ThreadX and NetX object control blocks... */

NX_PACKET_POOL          pool_0;
TX_THREAD               thread_client;
NX_IP                   client_ip;

/* Define the Client and Server instances. */

NX_DHCPV6               dhcp_client;

/* Define the error counter used in the demo application... */
ULONG                   error_counter;
CHAR                    *pointer;

/* Define thread prototypes. */
void    thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Declare DHCPv6 Client callbacks */
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state);
VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type);

/* Set up globals for tracking changes to DHCPv6 Client from callback services. */
UINT state_changes = 0;
UINT address_expired = 0;
UINT address_failed_dad = 0;
UINT bound_addresses = 0;
UINT address_not_assigned = 0;
UINT server_errors = 0;

/* Define some DHCPv6 parameters. */

#define DHCPV6_IANA_ID      0xC0DEDBAD
#define DHCPV6_T1           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_T2           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_RENEW_TIME   NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_REBIND_TIME  NX_DHCPV6_INFINITE_LEASE
#define PACKET_PAYLOAD      500
#define PACKET_POOL_SIZE    (5*PACKET_PAYLOAD)

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

UINT    status;

    /* Setup the working pointer. */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the Client thread. */
    status = tx_thread_create(&thread_client, "Client thread", thread_client_entry, 0,
                              pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1024,  pointer, PACKET_POOL_SIZE);

    pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create a Client IP instance. */
    status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                          0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                          pointer, 2048, 1);

    pointer =  pointer + 2048;

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable UDP traffic for sending DHCPv6 messages. */
    status =  nx_udp_enable(&client_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable ICMP. */
    status =  nx_icmp_enable(&client_ip);

    /* Check for ICMP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 Client. */
    status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                      &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                      dhcpv6_server_error_handler);

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update the stack pointer because we need it again. */
    pointer = pointer + 2048;

    /* Yield control to DHCPv6 threads and ThreadX. */
    return;
}


/* Define the Client host application thread. */

void    thread_client_entry(ULONG thread_input)
{

UINT        status;
ULONG       T1, T2;
UINT        address_count;
UINT        address_index = 0;
NXD_ADDRESS valid_ipv6_address;
ULONG       preferred_lifetime;
ULONG       valid_lifetime;
UINT        ia_count = 1;

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
NXD_ADDRESS ipv6_address;
#endif

#ifdef NX_DHCPV6_REQUEST_OPTION
UCHAR       buffer[200];
NXD_ADDRESS dns_server;
#endif

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE
ULONG       current_time;
ULONG       elapsed_time;
NX_DHCPV6_CLIENT_RECORD dhcpv6_client_record;
#endif


    state_changes = 0;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address of 0x1122334456. */
    status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

    if (status)
    {
        error_counter++;
        return;
    }

    /* Let NetX Duo get initialized. */
    tx_thread_sleep(50);

    /* Enable the Client IP for IPv6 and ICMPv6 services. */
    nxd_ipv6_enable(&client_ip);
    nxd_icmp_enable(&client_ip);

    /* Create a Link Layer Plus Time DUID for the DHCPv6 Client. Set time ID field
       to NULL; the DHCPv6 Client API will supply one. */
    status = nx_dhcpv6_create_client_duid(&dhcp_client, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                          NX_DHCPV6_HW_TYPE_IEEE_802, 0);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 client's Identity Association (IA-NA) now.

       Note that if this host had already been assigned in IPv6 lease, it
       would have to use the assigned T1 and T2 values in loading the DHCPv6
       client with an IANA block.
    */
    status = nx_dhcpv6_create_client_iana(&dhcp_client, DHCPV6_IANA_ID, DHCPV6_T1,  DHCPV6_T2);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
    memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
    ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
    ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
    ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
    ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
    ipv6_address.nxd_ip_address.v6[3] = 0x0000abcd;

    /* Create an IA address option.
        Note that if this host had already been assigned in IPv6 lease, it
        would have to use the assigned IPv6 address, preferred and valid lifetime
        values in loading the DHCPv6 Client with an IA block.
    */
    status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address,DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* If the DHCPv6 Client is configured for a maximum number of IA addresses
       greater than 1, we can add another IA address if the device requires
       multiple global IPv6 addresses. */
    if(NX_DHCPV6_MAX_IA_ADDRESS >= 2)
    {
        memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
        ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
        ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
        ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
        ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
        ipv6_address.nxd_ip_address.v6[3] = 0x00001234;

        /* Add another  IA address option. */
        status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address, DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            return;
        }
    }
#endif /* NX_DHCPV6_REQUEST_IA_ADDRESS  */

#ifdef NX_DHCPV6_REQUEST_OPTION
    /* Set the list of DHCPv6 option data to get from the DHCPv6 server if needed. */
    nx_dhcpv6_request_option_timezone(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_DNS_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_time_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_domain_name(&dhcp_client, NX_TRUE);
#endif /* NX_DHCPV6_REQUEST_OPTION */


#ifdef NX_DHCPV6_REQUEST_FQDN_OPTION
    /* Set the DHCPv6 Client FQDN option.
       operation: NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR         DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client.
                  NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE   DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client to the server.
                  NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE   DHCPv6 Client choose to request that the server perform no DNS updatest on its behalf. */
    nx_dhcpv6_request_option_FQDN(&dhcp_client, "DHCPv6-Client", NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR);
#endif /* NX_DHCPV6_REQUEST_FQDN_OPTION */

    /* Start up the NetX DHCPv6 Client thread task. */
    status =  nx_dhcpv6_start(&dhcp_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start the DHCPv6 by sending a Solicit message out on the network. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Is the DHCPv6 Client request for address assignment successfully started? */
    if (status == NX_SUCCESS)
    {

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Check the bound address. */
        if (bound_addresses != ia_count)
        {

            /* Attempt to find out why DHCPv6 failed, where...*/

            if (server_errors > 0)
            {
                /* Actually you would compare server_error count with number of IA's added
                   to determine if any addresses were assigned. */
                printf("Server error, not all address assigned\n");
            }

            if (address_not_assigned > 0)
            {
                /* Actually you would compare address not assigned count with number of IA's added
                   to determine if any addresses were assigned. */

                printf("No servers responded to some or all of our IAs\n");
            }

        }

        /* Regardless if the DHCPv6 Client achieved a bound state, check for DAD
           failures. */
        if (address_failed_dad > 0)
        {
            /* Actually you would compare failed dad count with number of IA's added
               to determine if any addresses were assigned. */

            printf("Some or all of our IAs failed DAD\n");

        }

        /* Successfully assigned IPv6 addresses! */

        /* Get the count of valid IPv6 address obtained by DHCPv6. */
        status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_client, &address_count);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IPv6 address and related lifetimes by address index. This index is the
           index into the DHCPv6 Client address table. Not to be confused with the IP
           instance address table! */
        status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_client, address_index,
                                                           &valid_ipv6_address, 
                                                               &preferred_lifetime,
                                                           &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IANA options for when to start renew/rebind requests. These time
           parameters are the same for all IPv6 addresses assigned in the Client
           e.g. IANA returned from Server. */
        status = nx_dhcpv6_get_iana_lease_time(&dhcp_client, &T1, &T2);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /*****************************************************************************/
        /* These are 'legacy' DHCPv6 services and are for the most part identical to the services
           above except they default to the primary global IPv6 address regardless if the
           Client was assigned more than one global IPv6 address. */

        /* Now check the assigned lease times. */
        status = nx_dhcpv6_get_lease_time_data(&dhcp_client, &T1, &T2,
                                               &preferred_lifetime, &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IP address. */
        status = nx_dhcpv6_get_IP_address(&dhcp_client, &valid_ipv6_address);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Bound state. */

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE

        /* Get the DHCPv6 Client record. */
        nx_dhcpv6_client_get_record(&dhcp_client, &dhcpv6_client_record);

        /* Delete DHCPv6 instance. */
        nx_dhcpv6_client_delete(&dhcp_client);

        /* Delete IP instance. */
        status = nx_ip_delete(&client_ip);

        /* Check for error. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Create a Client IP instance. */
        status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                              0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                              pointer, 2048, 1);

        pointer =  pointer + 2048;

        /* Check for IP create errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable UDP traffic for sending DHCPv6 messages. */
        status =  nx_udp_enable(&client_ip);

        /* Check for UDP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable ICMP. */
        status =  nx_icmp_enable(&client_ip);

        /* Check for ICMP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable the Client IP for IPv6 and ICMPv6 services. */
        status = nxd_ipv6_enable(&client_ip);
        status += nxd_icmp_enable(&client_ip);

        /* Check for IPv6 and ICMPv6 enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Establish the link local address for the host. The RAM driver creates
           a virtual MAC address of 0x1122334456. */
        status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

        if (status)
        {
            error_counter++;
            return;
        }

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Create the DHCPv6 Client. */
        status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                          &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                          dhcpv6_server_error_handler);

        /* Check for errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Update the stack pointer because we need it again. */
        pointer = pointer + 2048;

        /* Restore the DHCPv6 record. */
        nx_dhcpv6_client_restore_record(&dhcp_client, &dhcpv6_client_record, 5);

        /* Resume the DHCPv6 service. */
        nx_dhcpv6_resume(&dhcp_client);
#endif


#ifdef NX_DHCPV6_REQUEST_OPTION

        /* Get the DNS Server address. */
        nx_dhcpv6_get_DNS_server_address(&dhcp_client, 0, &dns_server);

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_DOMAIN_NAME_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        /* Get the time zone. */
        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_NEW_POSIX_TIMEZONE_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server
#endif

        /* At some point, we may wish to release the IPv6 address lease e.g. the device
           is leaving the network or powering down. In that case we inform the
           DHCPv6 Server that we are releasing the address lease. */
        status = nx_dhcpv6_request_release(&dhcp_client);

        /* Check status. */
        if (status != NX_SUCCESS)
        {

            error_counter++;
            return;
        }

        /* Send the release message. */
        tx_thread_sleep(100);
    }

    /* Stopping the Client task. */
    status = nx_dhcpv6_stop(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Clear the previously assigned IPv6 addresses from the Client and IP address table. */
    status = nx_dhcpv6_reinitialize(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start up the Client task again. */
    status = nx_dhcpv6_start(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Begin the request process by sending a Solicit message with the IA created above
       with our preferred IPv6 address. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);
    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Wait a bit before releasing the IP address and terminating the client. */
    tx_thread_sleep(500);

    /* Ok, lets stop the application. Again we DO NOT plan
       to keep the IPv6 address we were assigned and need to release it
       back to the DHCPv6 server. */
    status = nx_dhcpv6_request_release(&dhcp_client);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* Now delete the DHCPv6 client and release ThreadX and
       NetX Duo resources back to the system. */
    nx_dhcpv6_client_delete(&dhcp_client);


    return;

}


/* This is the notification from the DHCPv6 Client task that it has changed
   state in the DHCPv6 protocol, for example getting assigned an IPv6 lease and
   achieving the bound state or an IPv6 lease expires and being reset to
   the init state.
*/
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state)
{


    /* Increment state change counter. */
    state_changes++;

    /* Check if the Client attempted to request an IPv6 lease but no servers
       responded. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_SOLICIT) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that either DAD failed or IP lease expired. */
        address_not_assigned++;
    }

    /* Check if the Client has been assigned an IPv6 lease. */
    if (new_state == NX_DHCPV6_STATE_BOUND_TO_ADDRESS)
    {
        bound_addresses++;
    }

   /* Check if the Client was bound, but failed the uniqueness check
       (Duplicate Address Detection) and was reset to the INIT state. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_DECLINE) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that DAD failed on Client IA. */
        address_failed_dad++;
    }

    /* Check if the Client was bound, attempted renew the lease but the
       IPv6 address renewal/rebinding failed. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_REBIND) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that the IP lease expired. */
        address_expired++;
    }



    /* Other checks are possible. */

}

/* This is the notification from the DHCPv6 Client task that it received an error
   from the server (status code) in response to the Client's last DHCPv6 message.
*/

VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type)
{

    /* Increment the server error count. */
    server_errors++;

    /* This should distinguish between receiving a server error and no server
       available to assign the Client an IPv6 address if the Client fails
       to get assigned an address. */
}

#endif /* FEATURE_NX_IPV6 */
```
