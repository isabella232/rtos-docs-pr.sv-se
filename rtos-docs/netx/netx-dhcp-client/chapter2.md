---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX DHCP Client
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX DHCP-klienten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9224a4df70b8199032066e30108250a3baeb65f5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826799"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dhcp-client"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX DHCP Client

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX DHCP-komponenten.

## <a name="product-distribution"></a>Produkt distribution

DHCP för NetX finns på [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nx_dhcp. h** Rubrik fil för DHCP för NetX

- **nx_dhcp. c** C-källfil för DHCP för NetX

- **nx_dhcp.pdf** PDF-Beskrivning av DHCP för NetX

- **demo_netx_dhcp. c** NetX DHCP-demonstration

- **demo_netx_multihome_dhcp_client. c** NetX DHCP-klient demonstration av DHCP på flera gränssnitt

## <a name="dhcp-installation"></a>DHCP-installation

Om du vill använda DHCP för NetX ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX har installerats. Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*", ska *nx_dhcp. h* -och *nx_dhcp. c* -filerna kopieras till den här katalogen.

## <a name="using-dhcp"></a>Använda DHCP

Det är enkelt att använda DHCP för NetX. I princip måste program koden innehålla *nx_dhcp. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX respektive netx. När *nx_dhcp. h* ingår kan program koden sedan göra DHCP-funktions anropen angivna senare i den här hand boken. Programmet måste även innehålla *nx_dhcp. c* i build-processen. Den här filen måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer. Detta är allt som krävs för att använda NetX DHCP.

Observera att eftersom DHCP använder NetX UDP-tjänster, måste UDP aktive ras med *nx_udp_enable* anrop innan DHCP används.

Om du vill hämta en tidigare tilldelad IP-adress kan DHCP-klienten initiera DHCP-processen med begär ande meddelandet och alternativet 50 "begärd IP-adress" till DHCP-servern. DHCP-servern svarar med antingen ett ACK-meddelande om den ger IP-adressen till klienten eller en NACK om den vägrar. I det senare fallet startar DHCP-klienten om DHCP-processen i init-tillstånd med ett identifierings meddelande och ingen begärd IP-adress. Värd programmet skapar först DHCP-klienten och anropar sedan tjänsten *nx_dhcp_request_client_ip* API för att ange den begärda IP-adressen innan DHCP-processen startas med *nx_dhcp_start*. Ett exempel på ett DHCP-program finns på annan plats i det här dokumentet för mer information.

## <a name="in-the-bound-state"></a>I bindnings tillstånd

När DHCP-klienten är i ett begränsat tillstånd bearbetar DHCP-klientens tillstånd en gång per intervall (som anges i NX_DHCP_TIME_INTERVAL) och minskar den tid som återstår för det IP-lån som tilldelats till klienten. När förnyelse tiden har gått uppdateras DHCP-klientens tillstånd till det FÖRNYAde tillstånd där klienten begär en förnyelse från DHCP-servern.


## <a name="sending-dhcp-messages-to-the-server"></a>Skicka DHCP-meddelanden till servern

DHCP-klienten har API-tjänster som gör det möjligt för värd programmet att skicka ett meddelande till DHCP-servern. Observera att dessa tjänster inte är avsedda för att värd programmet ska köra DHCP-klient protokollet manuellt, eftersom de i första hand skickar meddelandet utan att nödvändigt vis uppdatera DHCP-klientens interna tillstånd.

  - *nx_dhcp_release*: detta skickar ett versions meddelande till servern när värd programmet antingen lämnar nätverket eller behöver lämna sin IP-adress.

  - *nx_dhcp_decline*: detta skickar ett neka-meddelande till servern om värd programmet avgör oberoende av DHCP-klienten att dess IP-adress redan används.

  - *nx_dhcp_forcerenew*: detta skickar ett forcerenew-meddelande till servern

  - *nx_dhcp_send_request*: Detta tar som ett argument av typen DHCP-meddelande som anges i *nx_dhcp. h* och skickar meddelandet till servern. Detta är främst avsett för att skicka meddelandet om DHCP-informning.

Se "*Beskrivning av DHCP-tjänster*" för mer information om dessa tjänster någon annan stans i det här dokumentet.

## <a name="starting-and-stopping-the-dhcp-client"></a>Starta och stoppa DHCP-klienten

Om du vill stoppa DHCP-klienten, oavsett om den har uppnått ett begränsat tillstånd, anropar värd programmet *nx_dhcp_stop*.

Om du vill starta om en DHCP-klient måste värd programmet först stoppa DHCP-klienten med hjälp av *nx_dhcp_stop* tjänst som beskrivs ovan. Sedan kan värden anropa *nx_dhcp_start* för att återuppta DHCP-klienten. Om värd programmet vill rensa en tidigare DHCP-klient profil, till exempel en som hämtats från en tidigare DHCP-server i ett annat nätverk, bör värd programmet anropa *nx_dhcp_reinitialize* för att utföra den här uppgiften internt innan du anropar nx_dhcp_start.

En typisk sekvens kan vara:

```C
nx_dhcp_stop(&my_dhcp);

nx_dhcp_reinitialize(&my_dhcp);

nx_dhcp_start(&my_dhcp);
```

För DHCP-program som körs på ett enda DHCP-gränssnitt inaktiverar DHCP-klienten även DHCP-KLIENTens timer. Det är därför inte längre att hålla koll på den återstående tiden i IP-lånet. Om DHCP-klienten stoppas på ett visst gränssnitt inaktive ras inte DHCP-klientens timer, men uppdateringar av timern stoppas vid den tid som återstår av IP-adresslån på det gränssnittet.

Att stoppa DHCP-klienten rekommenderas därför inte om värd programmet kräver omstart eller växling av nätverk.

## <a name="using-the-dhcp-client-with-auto-ip"></a>Använda DHCP-klienten med automatisk IP

NetX DHCP-klienten fungerar samtidigt med det automatiska IP-protokollet i program där DHCP och automatisk IP garanterar en adress där en DHCP-server inte är tillgänglig eller svarar. Men om värden inte kan identifiera en server eller hämta en IP-adress, kan den växla till det automatiska IP-protokollet för en lokal IP-adress. Innan du gör det rekommenderar vi dock att du stoppar DHCP-klienten tillfälligt medan den automatiska IP-adressen går igenom stegen "avsökning" och "försvar". När en automatisk IP-adress tilldelas till värden kan DHCP-klienten startas om och om en DHCP-server blir tillgänglig kan värd-IP-adressen acceptera IP-adressen som erbjuds av DHCP-servern medan programmet körs.

Den automatiska IP-NetX har ett meddelande om adress ändring för värden för att övervaka aktiviteter i händelse av en ändring av IP-adressen.

## <a name="small-example-system"></a>Litet exempel system

Ett exempel på hur användnings NetX beskrivs i bild 1,1 nedan. DHCP-klienten skapas "*my_thread_entry*" på rad 101. När åtgärden har skapats initieras DHCP-processen vid anropet till *nx_dhcp_start* på rad 108. Nu initieras DHCP-klientens försök att kontakta DHCP-servern. Under den här processen väntar program koden på att en giltig IP-adress ska registreras med IP-instansen med hjälp av *nx_ip_status_check* tjänsten (eller *nx_ip_interface_status_check* för ett sekundärt gränssnitt) som börjar på rad 95. Detta görs ofta i en slinga med ett kortare vänte alternativ.

Efter rad 127 har DHCP tagit emot en giltig IP-adress och programmet kan sedan fortsätta och använda NetX TCP/IP-tjänster som önskade.

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
      0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
      DEMO_STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


/* Define my thread. */

void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    actual_status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                            &actual_status, 100);

  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

Figur 1,1 exempel på DHCP-användning med NetX

## <a name="multi-server-environments"></a>Miljöer med flera servrar

På nätverk där det finns mer än en DHCP-server godkänner DHCP-klienten det första mottagna meddelandet om erbjudande för DHCP-servern, går vidare till status för begäran och ignorerar alla andra mottagna erbjudanden.

## <a name="arp-probes"></a>ARP-avsökningar

DHCP-klienten kan konfigureras att skicka en eller flera ARP-avsökningar efter tilldelning av IP-adress från DHCP-servern för att kontrol lera att IP-adressen inte redan används. Steget ARP PROBE rekommenderas av RFC 2131 och är särskilt viktigt i miljöer med fler än en DHCP-server. Om värd programmet aktiverar NX_DHCP_CLIENT_SEND_ARP_PROBE alternativ (se **konfigurations alternativ** i kapitel två för ytterligare ARP-avsöknings alternativ) skickar DHCP-klienten en "självbetjänings" ARP-avsökning och väntar på den angivna tiden för ett svar. Om ingen tas emot förflyttar sig DHCP-klienten till det begränsade tillstånd. Om ett svar tas emot förutsätter DHCP-klienten att adressen redan används. Det skickar automatiskt ett neka-meddelande till servern och initierar om klienten för att starta om DHCP-avsökningarna igen från INITIERINGs statusen. Detta startar om DHCP-tillstånds datorn och klienten skickar ett annat IDENTIFIERINGs meddelande till servern.

## <a name="bootp-protocol"></a>BOOTP-protokoll

DHCP-klienten stöder även BOOTP-protokollet och DHCP-protokollet. Om du vill aktivera det här alternativet och använda BOOTP i stället för DHCP måste värd programmet ange NX_DHCP_BOOTP_ENABLE konfigurations alternativet. Värd programmet kan fortfarande begära specifika IP-adresser i BOOTP-protokollet. DHCP-klienten stöder dock inte inläsning av värd operativ systemet eftersom BOOTP ibland används.

## <a name="dhcp-on-a-secondary-interface"></a>DHCP på ett sekundärt gränssnitt

NetX DHCP-klienten kan köras på sekundära gränssnitt i stället för det primära standard gränssnittet.

Om du vill köra NetX DHCP-klienten på ett sekundärt nätverks gränssnitt måste värd programmet ange gränssnitts index för DHCP-klienten till det sekundära gränssnittet med hjälp av tjänsten *nx_dhcp_set_interface_index* API. Gränssnittet måste redan vara kopplat till det primära nätverks gränssnittet med hjälp av tjänsten *nx_ip_interface_attach* . I användar handboken för NetX finns mer information om hur du kopplar sekundära gränssnitt.

Under bild 1,2 är ett exempel system där värd programmet ansluter till DHCP-servern på det sekundära gränssnittet. På rad 65 kopplas det sekundära gränssnittet till IP-aktiviteten med en null-IP-adress. Efter att DHCP-klienttjänsten har skapats på rad 104 anges DHCP-klientens gränssnitts index till 1 (t. ex. förskjutningen från det primära gränssnittet som själva är index 0) genom att anropa *nx_dhcp_set_interface_index*. Sedan är DHCP-klienten redo att startas på rad 108.

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
       0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  status = _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                            0xFFFFFF00UL, my_netx_driver);
                            
  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Set the DHCP client interface to the secondary interface. 
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

Figur 1,2 exempel på DHCP för NetX med support för multihome

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a>DHCP-klient på flera gränssnitt samtidigt

Om du vill köra DHCP-klienten på flera gränssnitt måste NX_MAX_PHYSICAL_INTERFACES i *nx_api. h* vara inställt på antalet fysiska gränssnitt som är anslutna till enheten. Som standard är det här värdet 1 (t. ex. det primära gränssnittet). Använd tjänsten *nx_ip_interface_attach* om du vill registrera ytterligare ett gränssnitt för IP-instansen. I användar handboken för NetX finns mer information om hur du kopplar sekundära gränssnitt.

Nästa steg är att ange NX_DHCP_CLIENT_MAX_RECORDS i *nx_dhcp. h* till det maximala antalet gränssnitt som förväntas köra DHCP samtidigt. Observera att NX_DHCP_CLIENT_MAX_RECORDS inte måste vara lika med NX_MAX_PHYSICAL_INTERFACES. NX_MAX_PHYSICAL_INTERFACES kan till exempel vara 3 och NX_DHCP_CLIENT_MAX_RECORDS lika med 2. I den här konfigurationen kan bara två gränssnitt (och båda vara två av de tre fysiska gränssnitten när som helst) av de tre fysiska gränssnitten köra DHCP vid ett och samma tillfälle. DHCP-klientens poster har ingen mappning till nätverks gränssnitt, t. ex. klient post 1 motsvarar inte automatiskt det fysiska gränssnittets index 1.

NX_DHCP_CLIENT_MAX_RECORDS kan också ställas in på fler än NX_MAX_PHYSICAL_INTERFACES men detta skulle skapa oanvända klient poster och vara en ineffektiv användning av minnet.

Innan den kan starta DHCP på alla gränssnitt måste programmet aktivera dessa gränssnitt genom att anropa *nx_dhcp_interface_enable*. Observera att undantaget är det primära gränssnittet som automatiskt aktive ras i *nx_dhcp_create* -anropet (och som kan inaktive ras med hjälp av tjänsten *nx_dhcp_interface_disable* som diskuteras nedan).

När som helst kan ett gränssnitt inaktive ras för DHCP eller DHCP kan stoppas på det gränssnittet oberoende av andra gränssnitt som kör DHCP.

Som nämnts ovan, för att aktivera ett särskilt gränssnitt för DHCP, använder du tjänsten *nx_dhcp_interface_enable* och anger det fysiska gränssnitts indexet i indataargumentet. Upp till NX_DHCP_CLIENT_MAX_RECORDS-gränssnitt kan aktive ras med den enda begränsningen att indataargumentet för gränssnitts indexet är mindre än NX_MAX_PHYSICAL_INTERFACES.

Använd tjänsten *nx_dhcp_interface_start* för att starta DHCP på ett speciellt gränssnitt. Använd tjänsten *nx_dhcp_start* för att starta DHCP på alla aktiverade gränssnitt. (Gränssnitt som redan har startat DHCP kommer inte att påverkas av *nx_dhcp_start*.)

Om du vill stoppa DHCP på ett gränssnitt använder du tjänsten *nx_dhcp_interface_stop* . DHCP måste redan ha startat på det gränssnittet, annars returneras en fel status. Om du vill stoppa DHCP på alla aktiverade gränssnitt använder du tjänsten *nx_dhcp_stop* . DHCP kan stoppas oberoende av andra gränssnitt när som helst.

De flesta av de befintliga DHCP-klient tjänsterna har en motsvarande gränssnitt, t. ex. *nx_dhcp_interface_release* är det gränssnitt som motsvarar *nx_dhcp_release.* Om DHCP-klienten har kon figurer ATS för ett enda gränssnitt utför de samma åtgärd.

Observera att icke-gränssnitts klient tjänster för DHCP gäller vanligt vis för alla gränssnitt, men inte alla. I det senare fallet gäller den icke-gränssnitts tjänsten för det första DHCP-aktiverade gränssnittet som finns i Sök i DHCP-klient listan över gränssnitts poster. Se **Beskrivning av tjänster** i kapitel tre för hur en icke-gränssnitts tjänst fungerar när flera gränssnitt är aktiverade för DHCP.

I exempel ordningen nedan har IP-instansen två nätverks gränssnitt och kör först DHCP på det sekundära gränssnittet. Vid ett senare tillfälle startar det DHCP på det primära gränssnittet. Sedan frigör den IP-adressen för det primära gränssnittet och startar om DHCP på det primära gränssnittet:

```C
nx_dhcp_create(&my_dhcp_client);
/* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); 
/* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); 
/* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); 

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is restarted on primary interface. */
```

En fullständig lista över gränssnitts vissa tjänster finns i **Beskrivning av tjänster** i kapitel tre.

## <a name="configuration-options"></a>Konfigurations alternativ

Användar konfigurerbara DHCP-alternativ i *nx_dhcp. h* gör det möjligt för värd programmet att finjustera DHCP-klienten för särskilda krav. Följande är en lista över dessa parametrar:  
  
- **NX_DHCP_ENABLE_BOOTP** Definierad aktiverar det här alternativet BOOTP-protokollet i stället för DHCP. Som standard är det här alternativet inaktiverat.

- **NX_DHCP_CLIENT_RESTORE_STATE** Om det här alternativet har definierats kan DHCP-klienten spara sin aktuella DHCP-klients tillstånd, inklusive återstående tid i lånet, och återställa det här läget mellan DHCP-klientens omstarter. Standardvärdet är inaktiverat.

- **NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** Om det här alternativet är inställt skapas ingen egen modempool i DHCP-klienten. Värd programmet måste använda nx_dhcp_packet_pool_set tjänsten för att ange DHCP-klientens adresspool. Standardvärdet är inaktiverat.

- **NX_DHCP_CLIENT_SEND_ARP_PROBE** Detta gör att DHCP-klienten kan skicka en ARP-avsökning efter tilldelning av IP-adresser för att verifiera att den tilldelade DHCP-adressen inte ägs av en annan värd. Som standard är det här alternativet inaktiverat.

- **NX_DHCP_ARP_PROBE_WAIT** Definierar hur lång tid DHCP-klienten väntar på ett svar efter att en ARP-avsökning har skickats. Standardvärdet är en sekund (1 * NX_IP_PERIODIC_RATE)

- **NX_DHCP_ARP_PROBE_MIN** Definierar den minsta variationen i intervallet mellan sändning av ARP-avsökningar. Värdet är standard 1 sekund.

- **NX_DHCP_ARP_PROBE_MAX** Definierar den maximala variationen i intervallet mellan sändning av ARP-avsökningar. Värdet är standard 2 sekunder.

- **NX_DHCP_ARP_PROBE_NUM** Definierar antalet ARP-avsökningar som har skickats för att avgöra om den IP-adress som tilldelats av DHCP-servern redan används. Värdet är standardvärdet 3 avsökningar.

- **NX_DHCP_RESTART_WAIT** Definierar hur lång tid DHCP-klienten väntar på att starta om DHCP om IP-adressen som tilldelats DHCP-klienten redan används. Värdet är standard 10 sekunder.

- **NX_DHCP_CLIENT_MAX_RECORDS** Anger det maximala antalet gränssnitts poster som ska sparas i DHCP-klientens instans. En DHCP-klients gränssnitts post är en post för DHCP-klienten som körs på ett speciellt gränssnitt. Standardvärdet anges som antal fysiska gränssnitt (NX_MAX_PHYSICAL_INTERFACES).

- **NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Definierad, detta gör att DHCP-klienten kan skicka maximalt alternativ för DHCP-meddelande storlek. Som standard är det här alternativet inaktiverat.

- **NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Detta gör att DHCP-klienten kan kontrol lera det angivna värd namnet i nx_dhcp_create-anropet för ogiltiga tecken eller ogiltig längd. Som standard är det här alternativet inaktiverat.

- **NX_DHCP_THREAD_PRIORITY** DHCP-Trådens prioritet. Som standard anger det här värdet att DHCP-tråden körs vid prioritet 3.

- **NX_DHCP_THREAD_STACK_SIZE** Storlek på DHCP-trådens stack. Som standard är storleken 2048 byte.

- **NX_DHCP_TIME_INTERVAL** Intervall i sekunder då funktionen för tids gräns för DHCP-klienten körs. Den här funktionen uppdaterar alla tids gränser i DHCP-processen, t. ex. om meddelanden ska skickas om eller om DHCP-klientens tillstånd ändras. Som standard är det här värdet 1 sekund.

- **NX_DHCP_OPTIONS_BUFFER_SIZE** Storlek på DHCP-alternativ buffert. Som standard är det här värdet 312.

- **NX_DHCP_PACKET_PAYLOAD** Anger storlek i byte för DHCP-klientens paket nytto Last. Standardvärdet är NX_DHCP_MINIMUM_IP_DATAGRAM + fysisk huvud storlek. Storleken på det fysiska sidhuvudet i ett Wireline-nätverk är vanligt vis Ethernet-Rams storleken.

- **NX_DHCP_PACKET_POOL_SIZE** Anger storleken på DHCP-klientens adresspool. Standardvärdet är (5 * NX_DHCP_PACKET_PAYLOAD) som kommer att tillhandahålla fyra paket plus utrymme för att lägga till en intern paket pool.

- **NX_DHCP_MIN_RETRANS_TIMEOUT** Anger det minsta vänte alternativet för att ta emot en DHCP-server svara på klient meddelande innan meddelandet överförs igen. Standardvärdet är RFC 2131 rekommenderade 4 sekunder.

- **NX_DHCP_MAX_RETRANS_TIMEOUT** Anger maximalt vänte alternativ för att ta emot en DHCP-server svara på klient meddelande innan meddelandet skickas igen. Standardvärdet är RFC 2131 rekommenderade 64 sekunder.

- **NX_DHCP_MIN_RENEW_TIMEOUT** Anger minimalt vänte alternativ för att ta emot ett DHCP-server meddelande och skicka en förnyelsebegäran när DHCP-klienten är kopplad till en IP-adress. Standardvärdet är 60 sekunder. DHCP-klienten använder dock utgångs tiden för förnyelse och OMBINDNING från DHCP-servern innan standard tids gränsen för förnyelse används.

- **NX_DHCP_TYPE_OF_SERVICE** Typ av tjänst som krävs för DHCP UDP-begäranden. Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.

- **NX_DHCP_FRAGMENT_OPTION** Fragment aktivera för DHCP UDP-begäranden. Som standard är det här värdet NX_DONT_FRAGMENT för att inaktivera DHCP UDP-fragmentering.

- **NX_DHCP_TIME_TO_LIVE** Anger antalet routrar som det här paketet kan passera innan det tas bort. Standardvärdet är inställt på 0x80.

- **NX_DHCP_QUEUE_DEPTH** Anger antalet maximalt djup för mottagnings kön. Standardvärdet är inställt på 4.
