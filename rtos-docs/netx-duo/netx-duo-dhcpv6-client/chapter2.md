---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX Duo DHCPv6-klient
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Duo DHCPv6-klientkomponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 481e29cc674edfa7e437e8e14253172b89aeae6856114192f4ca5b35717c91e0
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791541"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcpv6-client"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX Duo DHCPv6-klient

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Duo DHCPv6-klientkomponenten.

## <a name="product-distribution"></a>Produktdistribution

NetX Duo DHCPv6-klienten finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nxd_dhcpv6_client.h** Huvudfil för NetX DuoDHCPv6-klient

- **nxd_dhcpv6_client.c** Källkodsfil för NetX Duo DHCPv6-klienten

- **demo_netxduo_dhcpv6_client.c** Exempelprogram som demonstrerar installationen av NetX Duo DHCPv6-klienten

- **nxd_dhcpv6_client.pdf** PDF-beskrivning av NetX Duo DHCPv6-klienten

## <a name="netx-duo-dhcpv6-client-installation"></a>NetX Duo DHCPv6-klientinstallation

Om du vill använda NetX Duo DHCPv6-klient-API:et kan hela fördelningen som nämns ovan kopieras till samma katalog där NetX Duo är installerat. Om NetX Duo till exempel är installerat i katalogen "*\threadx\arm7\green*" kan *filerna nxd_dhcpv6_client.h* *och nxd_dhpcv6_client.c* kopieras till den här katalogen.

## <a name="using-the-netx-duo-dhcpv6-client"></a>Använda NetX Duo DHCPv6-klienten

Programkoden måste innehålla *nxd_dhcpv6_client.h* när den innehåller *tx_api.h* och *nx_api.h* för att använda DHCPv6-klienten, ThreadX- respektive NetX Duo-tjänster. *nxd_dhcpv6_client.c* måste kompileras i projektet på samma sätt som andra programfiler och dess objektformulär måste länkas tillsammans med programmets filer.

### <a name="span-classunderlineclient-dhcp-unique-identifier-duidspan"></a><span class="underline">Klientens unika DHCP-identifierare (DUID)</span>

Klient-DUID definierar unikt varje klient i ett nätverk. Ett program måste skapa ett klient-DUID innan en IPv6-adress begärs från en server. Klientens DUID inkluderas automatiskt i alla meddelanden till servern. För att skapa ett DUID anropar programmet tjänsten *nx_dhcpv6_create_client_duid:*
```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT duid_type, 
                                  UINT hardware_type, ULONG time);
```

Programmet anropar den här tjänsten och anger typen av DUID (endast länkskikt eller länkskikt plus tid. För länklager plus tids-DUID:er anger den här tjänsten tidsfältet om tidsinmatningen inte har angetts.

För enheter som startar om och vill använda ett tidigare tilldelat IPv6-adresslån måste programmet skapa klient-DUID som det som användes när det tilldelade IPv6-adressen. Adressen för länklagret är allt som behövs för att skapa ett klient-DUID för länkskikt. Detta kräver inte tidigare beständiga minneslagring om enheten har åtkomst till adressen på länklagret. För DUID:er av typen tid måste programmet ha åtkomst till samma tidsdata som användes vid den tidigare DUID-genereringen och detta kräver icke-beständigt minne. Klienter som inte har någon stabil lagring får inte använda DUID:er av typen time.

### <a name="span-classunderlineclient-identity-association-for-non-temporary-addresses-ianaspan"></a><span class="underline">Klientidentitetsassociating för icke-tillfälliga adresser (IANA)</span>

Programmet måste skapa en IANA och eventuellt en eller flera IA-adresser innan en IPv6-adress begärs. För att göra det anropar programmet *nx_dhcpv6_create_client_iana* tjänsten. För att skapa ett alternativ för IA-adress anropar *programmet nx_dhcpv6_add_client_ia-tjänsten* med en begärd IPv6-adress och livslängdsvärden som ett tips till servern.

IANA och dess IA definierar kumulativt tilldelningsparametrarna för klientens IPv6-adress:

Innan du startar DHCPv6-klienten skapar DHCPv6-klientprogrammet en IANA nx_dhcpv6_create_client_iana *tjänsten:*

```C
UINT    nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                     UINT IA_ident, ULONG T1, ULONG T2);
```

Den måste också skapa en eller flera IA:er *med nx_dhcpv6_create_client_ia-tjänsten* och begärda IPv6-adresser innan DHCPv6-klienten startas.

```C
UINT    nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                                NXD_ADDRESS *ipv6_address, 
                                ULONG preferred_lifetime, 
                                ULONG valid_lifetime);
```

> [!NOTE]
> Antalet IA-adresser som programmet skapar får inte överskrida NX_DHCPV6_MAX_IA_ADDRESS vars standardvärde är 1.

NetX Duo DHCPv6-klienten stöder *nx_dhcpv6_create_client_ia* äldre DHCPv6-klientprogram och som är identiska med *nx_dhcpv6_add_client_ia* men utvecklare uppmuntras att *använda nx_dhcpv6_add_client_ia tjänsten.*

Dessa tjänster visas i "Litet exempelsystem" någon annanstans i det här kapitlet.

### <a name="span-classunderlinenon-volatile-memory-considerations-to-reuse-ianas-and-iasspan"></a><span class="underline">Överväganden för icke-beständigt minne vid återanvändning av IANA:er och IA:er</span>

Programmet måste spara IANA-parametrarna T1, T2 och IANA-identifieraren till ej beständigt minne om det vill använda samma adress(er) vid omstart. Programmet måste också spara sin IA som innehåller dess IPv6-adress till icke-beständigt minne.

Programmet måste också lagra den tid som förflutit att det har varit bundet till sina tilldelade IPv6-adresslån till icke-beständigt minne om det stängs av. Den gör detta genom att *anropa nx_dhcpv6_get_time_accrued tjänsten* innan den stoppar DHCPv6-klienten.

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, 
                                ULONG *time_accrued);
```

Förutsatt att programmet har en oberoende klocka för att spåra tidsintervallet från när det stoppade och startade om DHCPv6-klienten efter en omstart, lägger det till den förflutna tiden till den tid som ackumuleras på IPv6-lånet innan det stoppas. Nu startar den klienttrådaktiviteten med den totala förflutna tiden som är bunden till IPv6-lånet som nv_time indata nedan:

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr, ULONG nv_time);
```

Från och med nu tar DHCPv6-klienttrådaktiviteten över övervakningen av den tid som ackumuleras på IPv6-lånet för när lånet ska förnyas.

### <a name="span-classunderlinesetting-dhcpv6-option-dataspan"></a><span class="underline">Ange DHCPv6-alternativdata</span>

Innan ett IPv6-lån begärs kan programmet begära andra nätverksparameterdata, till exempel DNS-server och tidsserver. Vissa av dessa parametrar har specifika tjänster. Några visas nedan:

```C
UINT  nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT enable)

UINT  nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr, 
                                           UINT enable);
```

### <a name="span-classunderlineinitiating-the-ipv6-address-requestspan"></a><span class="underline">Initiera IPv6-adressbegäran</span>

Programmet startar DHCPv6-klienttråden genom att anropa *nx_dhcpv6_start-tjänsten* med nolltidsinmatning. För att initiera DHCPv6-protokollet för att begära en IPv6-adress anropar *programmet nx_dhcpv6_request_solicit.*

Om programmet vill använda ett tidigare tilldelat IPv6-lån anropar det nx_dhcpv6_start *med* indata som inte är noll. Den bör inte anropa *nx_dhcpv6_request_solicit*.

Därefter behöver programmet inte göra något mer och DHCPv6-klienten övervakar automatiskt när det är dags att förnya eller binda om en IPv6-adress.

## <a name="small-example-system"></a>Litet exempelsystem

Ett exempel på hur enkelt det är att använda NetX Duo DHCPv6-klienten beskrivs i det lilla exemplet nedan med hjälp av en DHCPv6-klient och en virtuell RAM-drivrutin. Den här demonstrationen förutsätter att en enhet endast har ett enda fysiskt nätverksgränssnitt.

*tx_application_define* skapar paketpool för DHCPv6-klienten för att skicka DHCPv6-meddelanden. Det skapar också en programtråd och en IP-instans. Den aktiverar sedan UDP och ICMP på IP på raderna 130–148. DHCPv6-klienten skapas sedan med funktioner för *tillståndsändring* ( dhcpv6_state_change_notify ) och serverfel *(dhcpv6_server_error_handler)* på rad151.

I funktionen Client thread entry *,thread_client_entry*, konfigureras klient-IP med en lokal länkadress och aktiverad för IPv6- och ICMPv6-tjänster på raderna 202-217. Innan du startar DHCPv6-klienten skapar programmet ett Klient-DUID, ett IANA-alternativ och ett IA-adressalternativ på raderna219–303. Alternativet IA-adress är valfritt om klienten vill begära en IPv6-adress och giltig och önskad livslängd från servern. Servern kan bevilja den begärda IPv6-adressen eller lånetiderna. Programmet kan lägga till fler IA-alternativ (upp till NX_DHCPV6_MAX_IA_ADDRESS) som ska tilldelas flera globala adresser.

Slutligen anger programmet olika alternativ för att begära nätverksparametrar i sina meddelanden till DHCPv6-servern. DHCPv6-klientaktiviteten startas genom att *anropa nx_dhcpv6_start* på rad306 och det faktiska DHCPv6-protokollet startas i TILLSTÅNDET BEGÄRD med *anropet till nx_dhcpv6_request_solicit* på rad 317. DHCPv6-klienten hanterar sedan automatiskt befordran av klienttillståndet via DHCPv6-protokollet tills den är bunden till en adress eller ett fel inträffar. Under den här tiden väntar programmet på att protokollet ska slutföras, samt ATTPlicera adressidentifiering (DUPLICATE) för att slutföras om IP-instansen är konfigurerad för ISP (vilket är standardkonfigurationen).

Efter tx_thread_sleep-anropet kontrollerar programmet på de globala parametrar som angetts i tillståndsändringens återanrop för att fastställa om både DHCPv6-klientuppgiften har lyckats tilldelas ett IPv6-lån och i så fall att KONTROLL av unikhet lyckades. Detta görs med hjälp av räknarna som har ställts in i funktionerna för tillståndsändring och återanrop av serverfel. Programmet söker efter antal som inte är noll address_not_assigned, address_expired och server_errors efter misslyckad adresstilldelning. Om antalet användare bound_addresses inte är noll (minst en adress har tilldelats) söker den efter en icke-noll-address_failed_dad efter en misslyckad CHECK. En förklaring av tillståndsändringen och återanrop av serverfel följer:

Tillståndsändringens *återanrop, dhcpv6_state_change_notify*, det tidigare och aktuella DHCPv6-klienttillståndet för att avgöra om klienten tog emot giltiga serversvar:

  - *dhcpv6_state_change_notify* söker efter övergångar direkt från SOLICIT till INIT och ökar i så sätt en räknare för DHCPv6-klienten som inte får några svar från servern.

Nästa *dhcpv6_state_change_notify* kontrollerar om klienten har tilldelats (bunden) till en eller flera IPv6-adresser:

  - Om det nya tillståndet är BOUND ökas en räknare med adresser som är bundna till klienten.
    
Den *dhcpv6_state_change_notify söker* även efter en misslyckad CHECK:

  - Om tillståndet övergår från NEKA till INIT, har DHCPv6-klienten misslyckats MED ATT kontrollera en av dess tilldelade adresser och ökar antalet misslyckade adresstilldelningar.
    
Den sista kontrollen *dhcpv6_state_change_notify* i det här exemplet är att en tilldelad adress som godkänts i NLA-kontrollen inte kan förnyas eller bindas om:

  - Om tillståndet ändras från REBIND till INIT får klienten inga svar på sina RENEW- eller REBIND-begäranden och *dhcpv6_state_change_notify* ökar antalet utgångna adresser.

Om *dhcpv6_server_error_handler* meddelas av DHCPv6-klienten om en felstatus som tagits emot från servern ökas antalet serverfel.

Förutsatt att allt går bra frågar programmet DHCPv6-klienten efter adressdata, inklusive lånetider. Det får ett antal giltiga (tilldelade) adresser genom att anropa *nx_dhcpv6_get_valid_ip_address_count-tjänsten* och tid för att förnya i IANA (gäller för alla tilldelade IA-adresser) genom att *anropa nx_dhcpv6_get_iana_lease_time* på raderna 372–392. Den frågar sedan DHCPv6-klienten efter var och en av dess IA-alternativ för IPv6-adress och lånetider efter adressindex.

Vissa DHCPv6-klienttjänster (*nx_dhcpv6_get_lease_time_data, nx_dhcpv6_get_IP_address*) kräver inte ett adressindex som indata och returnerar DHCPv6-parametrar för den primära klientens globala adress. Detta är lämpligt för klienter med en enda global IPv6-adress när *den anropar nx_dhcpv6_get_valid_ip_address_lease_time* på rad 384.

DHCPv6-klientkonfigurationen, NX_DHCPV6_CLIENT_RESTORE_STATE, tillåter inte att ett system återställer en tidigare skapad DHCPv6-klient i bundet tillstånd mellan systemstarter. Anropa  nx_dhcpv6_client_get_record för att hämta DHCPv6-klientposten mellan omstarter av systemet på rad 434 och anropa *nx_dhcpv6_client_restore_record* för att lagra DHCPv6-klientposten efter att systemet startats på rad 525.

Programmet släpper sedan de tilldelade adresserna med hjälp *av nx_dhcpv6_request_release tjänsten* på rad 552. Om du vill starta om programmet stoppas DHCPv6-klienten med *nx_dhcpv6_client_stop-tjänsten* på rad 567 och rensar alla IPv6-adresser som registrerats med IP-instansen som konfigurerades via DHCPv6-klienten. Det gör den genom att *anropa nx_dhcpv6_reinitialize* på rad 578. Sedan startar den om DHCPv6-klientuppgiften *med nx_dhcpv6_start* och *nx_dhcpv6_request_solicit* tjänster som tidigare.

DHCPv6-klienten tas bort med anropet till *nx_dhcpv6_delete* på rad626. Observera att den inte tar bort den *paketpool* som skapades för DHCPv6-klienten eftersom den här paketpoolen också används av IP-instansen. Annars bör paketpoolen tas bort om den inte har någon  ytterligare användning för den med hjälp av NetX Duo nx_packet_pool_delete tjänsten.

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
