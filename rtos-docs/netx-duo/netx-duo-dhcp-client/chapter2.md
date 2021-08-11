---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX Duo DHCP-klient
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Duo DHCP-klientkomponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 08f88f4501a7b44272111cbe5c14ee09474827b72a1239b334fb9d40e8093c51
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788498"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcp-client"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX Duo DHCP-klient

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Duo DHCP-klientkomponenten.

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS NetX Duo kan hämtas från vår offentliga källkodsdatabas på <https://github.com/azure-rtos/netxduo> . Paketet innehåller följande filer:

- **nxd_dhcp_client.h:** Rubrikfil för NetX Duo DHCP
- **nxd_dhcp_client.c:** C-källfil för DHCP NetX Duo
- **nxd_dhcp_client.pdf:** Användarhandbok för NetX Duo DHCP 
    - **demo_netxduo_dhcp.c:** Demonstration av NetX Duo DHCP-klienten
    - **demo_netxduo_multihome_dhcp_client.c:** NetX Duo DHCP-klientdemonstration av DHCP på flera gränssnitt

## <a name="dhcp-installation"></a>DHCP-installation

Om du vill använda NetX Duo DHCP-klienten ska hela distributionen som nämns ovan kopieras till samma katalog där NetX Duo är installerat. Om NetX Duo till exempel är installerat i katalogen "*\threadx\arm7\green*" ska *filerna nxd_dhcp_client.h* *och nxd_dhcp_client.c* kopieras till den här katalogen.

## <a name="using-dhcp"></a>Använda DHCP

Det är enkelt att använda DHCP för NetX Duo. I princip måste programkoden innehålla *nxd_dhcp_client.h* efter att den innehåller *tx_api.h* och *nx_api.h* för att kunna använda ThreadX respektive NetX Duo. När *nxd_dhcp_client.h* ingår kan programkoden göra DHCP-funktionsanrop som anges senare i den här guiden. Programmet måste även innehålla *nxd_dhcp_client.c* i byggprocessen. Den här filen måste kompileras på samma sätt som andra programfiler och dess objektformulär måste länkas tillsammans med programmets filer. Det här är allt som krävs för att använda NetX DHCP.

Observera att eftersom DHCP använder NetX Duo UDP-tjänster måste UDP aktiveras med nx_udp_enable *innan* dhcp används.

För att få en tidigare tilldelad IP-adress kan DHCP-klienten initiera DHCP-processen med begärandemeddelandet och alternativ 50 "Begärd IP-adress" till DHCP-servern. DHCP-servern svarar med antingen ett ACK-meddelande om den beviljar IP-adressen till klienten eller en DHCP om den nekar. I det senare fallet startar DHCP-klienten om DHCP-processen i Init-tillstånd med meddelandet Identifiera och ingen begärd IP-adress. Värdprogrammet skapar först DHCP-klienten och anropar sedan *API nx_dhcp_request_client_ip tjänsten* för att ange den begärda IP-adressen innan DHCP-processen *startas med nx_dhcp_start*. Ett dhcp-exempelprogram tillhandahålls någon annanstans i det här dokumentet för mer information.

## <a name="in-the-bound-state"></a>I det bundna tillståndet

När DHCP-klienten är i ett bundet tillstånd bearbetar DHCP-klientens tråd klienttillstånd en gång per intervall (som anges av NX_DHCP_TIME_INTERVAL) och avtar den tid som återstår på det IP-lån som tilldelats klienten. När förnyelsetiden har förflutit uppdateras DHCP-klienttillståndet till det RENEW-tillstånd där klienten begär en förnyelse från DHCP-servern.

## <a name="sending-dhcp-messages-to-the-server"></a>Skicka DHCP-meddelanden till servern

DHCP-klienten har API-tjänster som gör att värdprogrammet kan skicka ett meddelande till DHCP-servern. Observera att dessa tjänster INTE är avsedda för värdprogrammet att köra DHCP-klientprotokollet manuellt.

  - *nx_dhcp_release*: detta skickar ett RELEASE-meddelande till servern när värdprogrammet antingen lämnar nätverket eller behöver lämna sin IP-adress.
  - *nx_dhcp_decline:* detta skickar ett NEKA-meddelande till servern om värdprogrammet oberoende av DHCP-klienten avgör att dess IP-adress redan används.
  - *nx_dhcp_forcerenew*: ett FORCERENEW-meddelande skickas till servern
  - *nx_dhcp_send_request:* Detta tar som argument en DHCP-meddelandetyp, som anges *i nxd_dhcp_client.h*, och skickar meddelandet till servern. Detta är främst avsett för att skicka DHCP INFORM-meddelandet.

Mer [information om dessa tjänster](chapter3.md) finns i Beskrivning av DHCP-tjänster 

## <a name="starting-and-stopping-the-dhcp-client"></a>Starta och stoppa DHCP-klienten

För att stoppa DHCP-klienten, oavsett om den har uppnått ett bundet tillstånd, anropar värdprogrammet *nx_dhcp_stop*.

Om du vill starta om en DHCP-klient måste värdprogrammet först stoppa DHCP-klienten med hjälp *nx_dhcp_stop* som beskrivs ovan. Värden kan sedan anropa *nx_dhcp_start* för att återuppta DHCP-klienten. Om värdprogrammet vill rensa en tidigare DHCP-klientprofil, till exempel en som hämtas från en tidigare DHCP-server i ett annat nätverk, bör värdprogrammet anropa *nx_dhcp_reinitialize* för att utföra den här uppgiften internt innan den *anropar nx_dhcp_start*.

En typisk sekvens kan vara:

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

Om DHCP-program endast körs på ett enda DHCP-gränssnitt inaktiveras även timern för DHCP-KLIENTEN om DHCP-klienten stoppas. Därför håller den inte längre reda på den återstående tiden för IP-lånet. Om du stoppar DHCP-klienten i ett visst gränssnitt inaktiveras inte DHCP-klienttimern, men timeruppdateringar stoppas till den tid som återstår på IP-lånet på det gränssnittet

Därför rekommenderas det inte att stoppa DHCP-klienten om inte värdprogrammet kräver omstart eller byte av nätverk.

## <a name="using-the-dhcp-client-with-auto-ip"></a>Använda DHCP-klienten med automatisk IP-adress

NetX Duo DHCP-klienten fungerar samtidigt med det automatiska IP-protokollet i program där DHCP och automatisk IP garanterar en adress där en DHCP-server inte garanterat är tillgänglig eller svarar. Men om värden inte kan identifiera en server eller få en tilldelad IP-adress kan den växla till det automatiska IP-protokollet för en lokal IP-adress. Men innan du gör det rekommenderar vi att du tillfälligt stoppar DHCP-klienten medan den automatiska IP-adressen går igenom stegen "avsökning" och "skydd". När värden har tilldelats en automatisk IP-adress kan DHCP-klienten startas om och om en DHCP-server blir tillgänglig kan värdens IP-adress acceptera IP-adressen som erbjuds av DHCP-servern medan programmet körs.

NetX Duo Auto IP har ett meddelande om adressändring för värden för att övervaka dess aktiviteter i händelse av en IP-adressändring.

## <a name="packet-chaining"></a>Paketkedja

För effektivare användning av paketpooler och minnesresurser kan DHCP-klienten hantera inkommande kedjepaket (datagram som överstiger drivrutinens MTU) från Ethernet-drivrutinen. Om drivrutinen har den här funktionen kan programmet ange paketpoolen för att ta emot paket till under de obligatoriska NX_DHCP_PACKET_PAYLOAD byte. NX_DHCP_PACKET_PAYLOAD bör hantera den fysiska nätverksramen (vanligtvis Ethernet), plus 548 byte DHCP-meddelandedata samt IP och UDP.

Observera att programmet kan optimera paketnyttolasten och antalet paket i paketpoolen som ingår i DHCP-klienten och som används för att skicka UT DHCP-meddelanden. Den kan optimera storleken baserat på förväntad användning och storleken på DHCP-klientmeddelanden.

## <a name="small-example-system"></a>Litet exempelsystem

Ett exempel på hur du använder NetX Duo visas i bild 1.1 nedan. Programtrådens postfunktion "*my_thread_entry*" skapas på rad 101. När det har skapats initieras DHCP-bearbetningen *nx_dhcp_start* anropet på rad 108. I det här läget försöker DHCP-klientens trådaktivitet att kontakta en DHCP-server separat. Under den här processen väntar programkoden på att en giltig IP-adress ska registreras med IP-instansen med *hjälp av nx_ip_status_check-tjänsten* (eller *nx_ip_interface_status_check* för ett sekundärt gränssnitt) på rad 95. Detta görs vanligtvis i en loop med ett kortare väntealternativ.

Efter rad 127 har DHCP tagit emot en giltig IP-adress och programmet kan sedan fortsätta med NetX Duo TCP/IP-tjänster efter behov.

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */
intmain()
{
  /* Enter the ThreadX kernel.  */
  tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;
    
    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create “my_thread”.  */
      tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                        pointer, DEMO_STACK_SIZE, 2, 2, 
                        TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

    /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                          0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
                          DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
 }


 /* Define my thread.  */

 void    my_thread_entry(ULONG thread_input)
 {

 UINT        status;
 ULONG       actual_status;
 NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
    /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                                     &actual_status, 100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
      error_counter++;
      return;
    }
    else
    {

  /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.
    }
 }

```
## <a name="multi-server-environments"></a>Miljöer med flera servrar

I nätverk där det finns fler än en DHCP-server accepterar DHCP-klienten det första mottagna meddelandet om DHCP-servererbjudandet, avancerar till begärandetillståndet och ignorerar alla andra mottagna erbjudanden.

## <a name="arp-probes"></a>ARP-avsökningar

DHCP-klienten kan konfigureras att skicka en eller flera ARP-avsökningar efter IP-adresstilldelning från DHCP-servern för att verifiera att IP-adressen inte redan används. ARP-avsökningssteget rekommenderas av RFC 2131 och är särskilt viktigt i miljöer med mer än en DHCP-server. Om värdprogrammet aktiverar alternativet NX_DHCP_CLIENT_SEND_ARP_PROBE (se  Konfigurationsalternativ i kapitel två för ytterligare alternativ för ARP-avsökning), skickar DHCP-klienten en "egen adress"-ARP-avsökning och väntar på ett svar under den angivna tiden. Om inget tas emot, avancerar DHCP-klienten till det bundna tillståndet. Om ett svar tas emot förutsätter DHCP-klienten att adressen redan används. Den skickar automatiskt ett NEKA-meddelande till servern och initierar om klienten för att starta om DHCP-avsökningarna igen från INIT-tillståndet. Detta startar om DHCP-tillståndsdatorn och klienten skickar ett nytt DISCOVER-meddelande till servern.

## <a name="bootp-protocol"></a>BOOTP-protokoll

DHCP-klienten stöder även BOOTP-protokollet samt DHCP-protokollet. Om du vill aktivera det här alternativet och använda BOOTP i stället för DHCP måste värdprogrammet ange NX_DHCP_BOOTP_ENABLE konfigurationsalternativet. Värdprogrammet kan fortfarande begära specifika IP-adresser i BOOTP-protokollet. DHCP-klienten stöder dock inte inläsning av värdoperativsystemet, eftersom BOOTP ibland används för att göra det.

## <a name="dhcp-on-a-secondary-interface"></a>DHCP på ett sekundärt gränssnitt

NetX Duo DHCP-klienten kan köras på sekundära gränssnitt i stället för det primära standardgränssnittet.

Om du vill köra NetX Duo DHCP-klienten i ett sekundärt nätverksgränssnitt måste värdprogrammet ange gränssnittsindexet för DHCP-klienten till det sekundära gränssnittet med *hjälp nx_dhcp_set_interface_index* API-tjänsten. Gränssnittet måste redan vara kopplat till det primära nätverksgränssnittet med hjälp *nx_ip_interface_attach* tjänsten. Mer information om hur du kopplar sekundära gränssnitt finns i användarhandboken för NetX Duo.

Nedan visas ett exempelsystem (bild 1.2) där värdprogrammet ansluter till DHCP-servern på det sekundära gränssnittet. På rad 65 är det sekundära gränssnittet kopplat till IP-uppgiften med en null-IP-adress. När DHCP-klientinstansen har skapats på rad 104 anges indexet för DHCP-klientgränssnittet till 1 (t.ex. förskjutningen från det primära gränssnittet som i sig är index 0) genom att *anropa nx_dhcp_set_interface_index*. Sedan är DHCP-klienten redo att startas på rad 108.

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */

intmain()
{
  /* Enter the ThreadX kernel.  */
  tx_kernel_enter();
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create “my_thread”.  */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                      pointer, DEMO_STACK_SIZE, 
                      2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

  /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                           0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    status =  _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                                       0xFFFFFF00UL, my_netx_driver);

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}


void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       status;
NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
      /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Set the DHCP client interface to the secondary interface. */
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
        error_counter++;
        return;
    }
    else
    {
    /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.*/
    }
}
```

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a>DHCP-klient på flera gränssnitt samtidigt

Om du vill köra DHCP-klienten på NX_MAX_PHYSICAL_INTERFACES gränssnitt *nx_api i nx_api.h* vara inställt på antalet fysiska gränssnitt som är anslutna till enheten. Som standard är det här värdet 1 (t.ex. det primära gränssnittet). Om du vill registrera ytterligare ett  gränssnitt för IP-instansen använder nx_ip_interface_attach tjänsten. Mer information om hur du kopplar sekundära gränssnitt finns i användarhandboken för NetX Duo.

Nästa steg är att ange NX_DHCP_CLIENT_MAX_RECORDS i *nxd_dhcp_client.h* till det maximala antalet gränssnitt som förväntas köra DHCP samtidigt. Observera att NX_DHCP_CLIENT_MAX_RECORDS inte behöver vara lika med NX_MAX_PHYSICAL_INTERFACES. Till exempel kan NX_MAX_PHYSICAL_INTERFACES vara 3 och NX_DHCP_CLIENT_MAX_RECORDS lika med 2. I den här konfigurationen kan endast två gränssnitt (och de kan vara två av de tre fysiska gränssnitten när som helst) av de tre fysiska gränssnitten köra DHCP samtidigt. DHCP-klientposter har ingen en-till-en-mappning till nätverksgränssnitt, t.ex. klientpost 1 korrelerar inte automatiskt med det fysiska gränssnittsindex 1.

NX_DHCP_CLIENT_MAX_RECORDS kan också anges till större än NX_MAX_PHYSICAL_INTERFACES detta skulle skapa oanvända klientposter och vara en ineffektiv användning av minnet.

Innan DHCP kan startas på ett gränssnitt måste programmet aktivera dessa gränssnitt genom att anropa *nx_dhcp_interface_enable*. Observera att undantaget är det primära gränssnittet  som aktiveras automatiskt i nx_dhcp_create anropet (och som kan inaktiveras med hjälp *av nx_dhcp_interface_disable tjänsten* som beskrivs nedan).

När som helst kan ett gränssnitt inaktiveras för DHCP eller DHCP kan stoppas på det gränssnittet oberoende av andra gränssnitt som kör DHCP.

Som nämnts ovan använder du tjänsten nx_dhcp_interface_enable  och anger det fysiska gränssnittsindexet i indataargumentet för att aktivera ett specifikt gränssnitt för DHCP. Upp till NX_DHCP_CLIENT_MAX_RECORDS-gränssnitt kan aktiveras med den enda begränsningen att gränssnittsindexets indataargument är mindre än NX_MAX_PHYSICAL_INTERFACES.

Om du vill starta DHCP på ett specifikt gränssnitt använder *du nx_dhcp_interface_start tjänsten.* Om du vill starta DHCP på  alla aktiverade gränssnitt använder nx_dhcp_start tjänsten. (Gränssnitt som redan har startat DHCP påverkas inte av *nx_dhcp_start*.)

Om du vill stoppa DHCP  på ett gränssnitt använder nx_dhcp_interface_stop tjänsten. DHCP måste redan ha startats på det gränssnittet, annars returneras en felstatus. Om du vill stoppa DHCP på  alla aktiverade gränssnitt använder du nx_dhcp_stop tjänsten. DHCP kan stoppas oberoende av andra gränssnitt när som helst.

De flesta befintliga DHCP-klienttjänster har motsvarande "gränssnitt", *t.ex. nx_dhcp_interface_release* är gränssnittsspecifik motsvarighet till *nx_dhcp_release.* Om DHCP-klienten har konfigurerats för ett enda gränssnitt utför de samma åtgärd.

Observera att icke-gränssnittsspecifika DHCP-klienttjänster vanligtvis gäller för alla gränssnitt, men inte alla. I det senare fallet gäller den icke-gränssnittsspecifika tjänsten det första DHCP-aktiverade gränssnittet som hittades vid sökning i DHCP-klientlistan över gränssnittsposter. Se **Beskrivning av tjänster** i kapitel tre för hur en icke-gränssnittsspecifik tjänst presterar när flera gränssnitt är aktiverade för DHCP.

I exempelsekvensen nedan har IP-instansen två nätverksgränssnitt och kör först DHCP på det sekundära gränssnittet. Vid ett senare tillfälle startar dhcp på det primära gränssnittet. Sedan släpper den IP-adressen i det primära gränssnittet och startar om DHCP på det primära gränssnittet:

```c
nx_dhcp_create(&my_dhcp_client); /* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); /* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); /* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); /* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is restarted on primary interface. */
```

En fullständig lista över gränssnittsspecifika tjänster finns **i Beskrivning av tjänster** i kapitel tre.

## <a name="configuration-options"></a>Konfigurationsalternativ

Användarkonfigurerbara *DHCP-alternativ i nxd_dhcp_client.h* gör det möjligt för värdprogrammet att finjustera DHCP-klienten för sina specifika krav. Följande är en lista över dessa parametrar:  
  
- **NX_DHCP_ENABLE_BOOTP:** Det här alternativet aktiverar BOOTP-protokollet i stället för DHCP. Som standard är det här alternativet inaktiverat.
- **NX_DHCP_CLIENT_RESTORE_STATE:** Om det här definieras gör detta att DHCP-klienten kan spara sitt aktuella DHCP-klientlicenstillstånd, inklusive återstående tid på lånet, och återställa det här tillståndet mellan omstarter av DHCP-klientprogrammet. Standardvärdet är inaktiverat.
- **NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL:** Om detta anges skapar DHCP-klienten inte en egen paketpool. Värdprogrammet måste använda tjänsten *nx_dhcp_packet_pool_set* för att ställa in DHCP-klientens paketpool. Standardvärdet är inaktiverat.
- **NX_DHCP_CLIENT_SEND_ARP_PROBE:** Detta gör att DHCP-klienten kan skicka en ARP-avsökning efter IP-adresstilldelning för att verifiera att den tilldelade DHCP-adressen inte ägs av någon annan värd. Det här alternativet är inaktiverat som standard.
- **NX_DHCP_ARP_PROBE_WAIT:** Definierar hur lång tid DHCP-klienten väntar på ett svar efter att ha skickat en ARP-avsökning. Standardvärdet är en sekund (1 * NX_IP_PERIODIC_RATE)
- **NX_DHCP_ARP_PROBE_MIN:** Definierar den lägsta variationen i intervallet mellan att skicka ARP-avsökningar. Värdet är som standard 1 sekund.
- **NX_DHCP_ARP_PROBE_MAX:** Definierar den maximala variationen i intervallet mellan att skicka ARP-avsökningar. Värdet är som standard 2 sekunder.
- **NX_DHCP_ARP_PROBE_NUM:** Definierar antalet ARP-avsökningar som skickas för att avgöra om IP-adressen som tilldelats av DHCP-servern redan används. Värdet är som standard 3 avsökningar.
- **NX_DHCP_RESTART_WAIT:** Definierar hur lång tid DHCP-klienten väntar på att starta om DHCP om IP-adressen som tilldelats DHCP-klienten redan används. Värdet är som standard 10 sekunder.
- **NX_DHCP_CLIENT_MAX_RECORDS:** Anger det maximala antalet gränssnittsposter som ska sparas till DHCP-klientinstansen. En DHCP-klientgränssnittspost är en post för DHCP-klienten som körs på ett specifikt gränssnitt. Standardvärdet anges som antal fysiska gränssnitt (NX_MAX_PHYSICAL_INTERFACES).
- **NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION:** Definieras gör detta att DHCP-klienten kan skicka alternativet maximal DHCP-meddelandestorlek. Det här alternativet är inaktiverat som standard.
- **NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK:** Definieras gör det möjligt för DHCP-klienten att kontrollera värdnamnet för indata i nx_dhcp_create-anropet efter ogiltiga tecken eller längd. Det här alternativet är inaktiverat som standard.
- **NX_DHCP_THREAD_PRIORITY:** Dhcp-trådens prioritet. Som standard anger det här värdet att DHCP-tråden körs med prioritet 3.
- **NX_DHCP_THREAD_STACK_SIZE:** Storleken på DHCP-trådstacken. Som standard är storleken 2 048 byte.
- **NX_DHCP_TIME_INTERVAL:** Intervall i sekunder när dhcp-klientens timers förfallofunktion körs. Den här funktionen uppdaterar alla tidsgränser i DHCP-processen, t.ex. om meddelanden ska skickas igen eller DHCP-klienttillståndet ändras. Som standard är det här värdet 1 sekund.
- **NX_DHCP_OPTIONS_BUFFER_SIZE:** Storleken på DHCP-alternativbufferten. Som standard är det här värdet 312 byte.
- **NX_DHCP_PACKET_PAYLOAD:** Anger storleken i byte för dhcp-klientens paketnyttolast. Standardvärdet är NX_DHCP_MINIMUM_IP_DATAGRAM + fysisk rubrikstorlek. Storleken på det fysiska huvudet i ett kabelnätverk är vanligtvis Ethernet-ramstorleken.
- **NX_DHCP_PACKET_POOL_SIZE:** Anger storleken på DHCP-klientens paketpool. Standardvärdet är (5 *NX_DHCP_PACKET_PAYLOAD) som ger fyra paket plus utrymme för interna paketpooler.
- **NX_DHCP_MIN_RETRANS_TIMEOUT:** Anger minsta väntealternativ för att ta emot ett DHCP-serversvar på klientmeddelandet innan meddelandet skickas igen. Standardvärdet är RFC 2131 som rekommenderas 4 sekunder.
- **NX_DHCP_MAX_RETRANS_TIMEOUT:** Anger alternativet för maximal väntetid för att ta emot ett DHCP-serversvar på klientmeddelandet innan meddelandet skickas igen. Standardvärdet är 64 sekunder.
- **NX_DHCP_MIN_RENEW_TIMEOUT:** Anger minsta väntealternativ för att ta emot ett DHCP-servermeddelande och skicka en förnyelsebegäran när DHCP-klienten är bunden till en IP-adress. Standardvärdet är 60 sekunder. DHCP-klienten använder dock förfallotiderna Förnya och Bind om från DHCP-servermeddelandet innan standardvärdet är den minsta tidsgränsen för förnyelse.
- **NX_DHCP_TYPE_OF_SERVICE:** Typ av tjänst som krävs för DHCP UDP-begäranden. Som standard definieras det här värdet som NX_IP_NORMAL för att indikera normal IP-pakettjänst.
- **NX_DHCP_FRAGMENT_OPTION:** Aktivera fragment för DHCP UDP-begäranden. Som standard är det här värdet NX_DONT_FRAGMENT inaktivera DHCP UDP-fragmentering.
- **NX_DHCP_TIME_TO_LIVE:** Anger antalet routrar som det här paketet kan passera innan det tas bort. Standardvärdet är inställt på 0x80.
- **NX_DHCP_QUEUE_DEPTH:** Anger det maximala djupet för mottagningskön. Standardvärdet är inställt på 4.