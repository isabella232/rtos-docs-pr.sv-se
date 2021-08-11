---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX Point-to-Point Protocol (PPP)
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS PPP-komponenten (NetX Point-to-Point Protocol).
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b62ca837cadd5f7bee2686ab566ff133f1088ff7ba8b572e372e5051b7bbaab9
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791099"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-point-to-point-protocol-ppp"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX Point-to-Point Protocol (PPP)

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS PPP-komponenten (NetX Point-to-Point Protocol).

## <a name="product-distribution"></a>Produktdistribution

Paketet Azure RTOS NetX Point-to-Point Protocol (PPP) finns på <https://github.com/azure-rtos/netx> . Paketet innehåller följande filer:

- **nx_ppp.h:** Rubrikfil för PPP för NetX
- **nx_ppp.c:** C-källfil för PPP för NetX
- **nx_ppp.pdf:** PDF-beskrivning av PPP för NetX
- **demo_netx_ppp.c:** Demonstration av NetX PPP

## <a name="ppp-installation"></a>PPP-installation

För att kunna använda PPP för NetX, bör hela distributionen som nämns ovan kopieras till samma katalog där NetX är installerat. Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*" ska *filerna nx_ppp.h* *och nx_ppp.c* kopieras till den här katalogen.

## <a name="using-ppp"></a>Använda PPP

Det är enkelt att använda PPP för NetX. I princip måste programkoden innehålla *nx_ppp.h* efter att den *innehåller tx_api.h* och *nx_api.h* för att kunna använda ThreadX respektive NetX. När *nx_ppp.h* ingår kan programkoden göra de PPP-funktionsanrop som anges senare i den här guiden. Programmet måste även innehålla *nx_ppp.c* i byggprocessen. Den här filen måste kompileras på samma sätt som andra programfiler och dess objektformulär måste länkas tillsammans med programmets filer. Det här är allt som krävs för att använda NetX PPP.

## <a name="using-modems"></a>Använda modem

Om ett modem krävs för anslutning till Internet, krävs vissa särskilda överväganden för att kunna använda NetX PPP-produkten. I princip introducerar användning av ett modem ytterligare initieringslogik och logik för förlust av kommunikation. Dessutom görs merparten av den ytterligare modemlogiken utanför kontexten för NetX PPP. Det grundläggande flödet för att använda NetX PPP med ett modem ser ut ungefär så här:

1. Initiera modem

1. Internetleverantör för uppringning

1. Vänta på anslutning

1. Vänta på UserID-fråga

1. Starta NetX PPP [PPP i drift]

1. Förlust av kommunikation

1. Stoppa NetX PPP (eller starta om via nx_ppp_restart)

### <a name="initialize-modem"></a>Initiera modem

Med programmets rutin för serieutdata på låg nivå initieras modemet via en serie ASCII-teckenkommandon (mer information finns i modemets dokumentation).

### <a name="dial-internet-service-provider"></a>Internetleverantör för uppringning

Med programmets rutin för seriella utdata på låg nivå uppmanas modemet att ringa Internetleverantören. Följande är till exempel typiskt för en ASCII-sträng som används för att ringa upp en Internetleverantör med numret 123–4567:

"ATDT123456\r"

### <a name="wait-for-connection"></a>Vänta på anslutning

Nu väntar programmet på att få en indikation från modemet om att en anslutning har upprättats. Detta åstadkoms genom att söka efter tecken från programmets rutin för serieindata på låg nivå. Vanligtvis returnerar modem en ASCII-sträng som "CONNECT" när en anslutning har upprättats.

### <a name="wait-for-user-id-prompt"></a>Vänta tills användarens ID efterfrågas

När anslutningen har upprättats måste programmet nu vänta på en första inloggningsbegäran från Internetleverantören. Detta sker vanligtvis i form av en ASCII-sträng som "Logga in?".

### <a name="start-netx-ppp"></a>Starta NetX PPP

Nu kan NetX PPP startas. Detta åstadkoms genom att *anropa nx_ppp_create* tjänsten följt av *nx_ip_create tjänsten.* Ytterligare tjänster för att aktivera PAP och konfigurera PPP-IP-adresserna kan också krävas. Mer information finns i följande avsnitt i den här guiden.

### <a name="loss-of-communication"></a>Förlust av kommunikation

När PPP har startats skickas eventuell icke-PPP-information till den "ogiltiga pakethanteringsrutin" som programmet har *angett till nx_ppp_create tjänsten.* Vanligtvis skickar modem en ASCII-sträng, till exempel "INGEN OPERATÖR" när kommunikationen med Internetleverantören går förlorad. När programmet tar emot ett icke-PPP-paket med sådan information bör det antingen stoppa NetX PPP-instansen eller starta om PPP-tillståndsdatorn via nx_ppp_restart-API:et. 

### <a name="stop-netx-ppp"></a>Stoppa NetX PPP

Det är ganska enkelt att stoppa NetX PPP. I princip måste alla skapade socketar vara obundna och borttagna. Ta sedan bort IP-instansen via *nx_ip_delete tjänsten.* När IP-instansen har tagits *bort nx_ppp_delete* tjänsten anropas för att slutföra processen med att stoppa PPP. Nu kan programmet försöka återupprätta kommunikationen med Internetleverantören.

## <a name="small-example-system"></a>Litet exempelsystem

Ett exempel som illustrerar hur enkelt det är att använda NetX PPP beskrivs i bild 1.1 som visas nedan. I det här exemplet tas *PPP-indelningsfilen nx_ppp.h* in på rad 3. Därefter skapas PPP i *"tx_application_define"* på rad 56. PPP-kontrollblocket "*my_ppp*" definierades som en global variabel på rad 9 tidigare. 

>[!NOTE]
>PPP bör skapas innan du skapar IP-instansen. När PPP och IP har skapats väntar tråden "*my_thread*" på att PPP-länken ska bli levande på rad 98. På rad 104 fungerar både PPP och NetX fullt ut.

Det objekt som inte visas i det här exemplet är programmets isr-in mottagning av seriebyte. Den måste anropa nx_ppp_byte_receive *"* my_ppp "*och* bytet tas emot som indataparametrar.

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nx_ppp.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_PPP                  my_ppp;

/* Define function prototypes. */

void    my_thread_entry(ULONG thread_input);
void    my_serial_driver_byte_output(UCHAR byte);
void    my_invalid_packet_handler(NX_PACKET *packet_ptr);
 
/* Define main entry point. */
intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
 }


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

/* Setup the working pointer. */
pointer =  (CHAR *) first_unused_memory;

/* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                  pointer, DEMO_STACK_SIZE, 
                  2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                    1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error. */
    if (status)
        error_counter++;

    /* Create a PPP instance. */
    status = nx_ppp_create(&my_ppp, “My PPP”, &my_ip, pointer, 1024, 2, 
                           &my_pool, my_invalid_packet_handler, my_serial_driver_byte_output);
    pointer =  pointer + 1024;
    /* Check for PPP creation pool. */
    if (status)
        error_counter++;

    /* Create an IP instance with the PPP driver. */
    status = nx_ip_create(&my_ip,"My NetX IP Instance", 
                           IP_ADDRESS(216,2,3,1), 0xFFFFFF00, &my_pool, 
                           nx_ppp_driver, pointer, DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors. */
    if (status)
        error_counter++;

    /* Enable ICMP for my IP Instance. */
    status =  nx_icmp_enable(&my_ip);

    /* Check for ICMP enable errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}

/* Define my thread. */
void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       ip_status;
NX_PACKET   *my_packet;

/* Wait for the PPP link in my_ip to become enabled. */
    status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,&ip_status,3000);

    /* Check for IP status error. */
    if (status) 
        return;

    /* Link is fully up and operational. All NetX activities 
    are now available. */

}
```
## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ för att skapa PPP för NetX. I följande lista beskrivs var och en i detalj:

- **NX_DISABLE_ERROR_CHECKING:** Det här alternativet tar bort den grundläggande PPP-felkontrollen. Det används vanligtvis när programmet har felsökts.
- **NX_PPP_PPPOE_ENABLE:** Om PPP definieras kan det överföra paket via Ethernet
- **NX_PPP_BASE_TIMEOUT:** Detta definierar den periodfrekvens (i tids tick) som PPP-tråduppgiften är incheckad för att söka efter PPP-händelser. Standardvärdet är 1 *NX_IP_PERIODIC_RATE (100 tick).
- **NX_PPP_DISABLE_INFO:** Om det här definieras inaktiveras intern PPP-informationsinsamling.
- **NX_PPP_DEBUG_LOG_ENABLE:** Om den definieras aktiveras den interna PPP-felsökningsloggen.
- **NX_PPP_DEBUG_LOG_PRINT_ENABLE:Om** den har definierats aktiveras internt PPP-felsökningsloggutskrift till *stdio.*  Detta är endast giltigt om felsökningsloggen också är aktiverad.
- **NX_PPP_DEBUG_LOG_SIZE:** Storleken på felsökningsloggen (antalet poster i felsökningsloggen). När den senaste posten har nåtts omsluter felsökningsfångst till den första posten och skriver över alla data som tidigare har avbildats. Standardvärdet är 50.
- **NX_PPP_DEBUG_FRAME_SIZE:** Maximal mängd data som samlas in från en mottagen paketnyttolast och som sparats i felsökningsutdata. Standardvärdet är 50.
- **NX_PPP_DISABLE_CHAP:** Om den definieras tas intern PPP CHAP-logik bort, inklusive sammanfattad MD5-logik.
- **NX_PPP_DISABLE_PAP**: Om den definieras tas intern PPP PAP-logik bort.
- **NX_PPP_DNS_OPTION_DISABLE:** Om DNS-alternativet har definierats är det inaktiverat i IPCP-svaret.  Som standard definieras inte det här alternativet (DNS-alternativet har angetts).
- **NX_PPP_DNS_ADDRESS_MAX_RETRIES:** Anger hur många gånger PPP-värden begär en DNS-serveradress från peer-datorn i IPCP-tillståndet. Detta har ingen effekt om NX_PPP_DNS_OPTION_DISABLE har definierats. Standardvärdet är 2.
- **NX_PPP_HASHED_VALUE_SIZE:** Anger storleken på "hashade värde"-strängar som används vid CHAP-autentisering. Standardvärdet är inställt på 16 byte, men kan definieras om innan du tar *med nx_ppp.h.*
- **NX_PPP_MAX_LCP_PROTOCOL_RETRIES:** Detta definierar det maximala antalet återförsök om PPP-tiden går ut innan ett annat meddelande om LCP-konfigurationsbegäran skickas. När det här numret nås avbryts PPP-handskakningen och länkstatusen är nere. Standardvärdet är 20.
- **NX_PPP_MAX_PAP_PROTOCOL_RETRIES:** Detta definierar det maximala antalet återförsök om PPP-tiden går ut innan ett annat PAP-meddelande om autentiseringsbegäran skickas. När det här numret nås avbryts PPP-handskakningen och länkstatusen är nere. Standardvärdet är 20.
- **NX_PPP_MAX_CHAP_PROTOCOL_RETRIES:** Detta definierar det maximala antalet återförsök om PPP-tiden går ut innan ett annat CHAP-utmaningsmeddelande skickas. När det här numret nås avbryts PPP-handskakningen och länkstatusen är nere. Standardvärdet är 20.
- **NX_PPP_MAX_IPCP_PROTOCOL_RETRIES:** Detta definierar det maximala antalet återförsök om PPP-tiden går ut innan ett annat meddelande om IPCP-konfigurationsbegäran skickas. När det här numret nås avbryts PPP-handskakningen och länkstatusen är nere. Standardvärdet är 20.
- **NX_PPP_MRU:** Anger högsta mottagningsenhet (MRU) för PPP. Som standard är det här värdet 1 500 byte (minimivärdet). Den här definierar kan anges av programmet innan du tar med *nx_ppp.h*.
- **NX_PPP_MINIMUM_MRU:** Anger den minsta mru som tas emot i ett meddelande om LCP-konfigurationsbegäran. Som standard är det här värdet 1 500 byte (minimivärdet). Den här definierar kan anges av programmet innan du tar med *nx_ppp.h*.
- **NX_PPP_NAME_SIZE**: Anger storleken på "namn"-strängar som används vid autentisering. Standardvärdet är inställt på 32byte, men kan definieras om innan *nx_ppp.h tas med.
- **NX_PPP_PASSWORD_SIZE:** Anger storleken på "lösenordssträngar" som används vid autentisering. Standardvärdet är inställt på 32byte, men kan definieras om innan du tar *nx_ppp.h.*
- **NX_PPP_PROTOCOL_TIMEOUT:** Detta definierar väntealternativet (i sekunder) för PPP-uppgiften att ta emot ett svar på ett begärandemeddelande om PPP-protokoll. Standardvärdet är 4 sekunder.
- **NX_PPP_RECEIVE_TIMEOUTS:** Detta definierar hur många gånger PPP-trådaktiviteten får sin tid ut i väntan på att ta emot nästa tecken i en PPP-meddelandeström. Därefter släpper PPP paketet och börjar vänta på att få nästa PPP-meddelande. Standardvärdet är 4.
- **NX_PPP_SERIAL_BUFFER_SIZE:** Anger storleken på seriebufferten för mottagningstecken. Som standard är det här värdet 3 000 byte. Den här definierar kan anges av programmet innan du tar med *nx_ppp.h*.
- **NX_PPP_TIMEOUT:** Detta definierar väntealternativet (i timer tick) för att allokera paket för att överföra data samt buffra PPP-seriella data till paket som ska skickas till IP-lagret. Standardvärdet är 4*NX_IP_PERIODIC_RATE (400 tick).
- **NX_PPP_THREAD_TIME_SLICE:** Alternativet För tidssegment för PPP-trådar. Som standard är det här värdet TX_NO_TIME_SLICE. Den här definierar kan anges av programmet innan du tar med *nx_ppp.h*.
- **NX_PPP_VALUE_SIZE:** Anger storleken på "value"-strängar som används vid CHAP-autentisering. Standardvärdet är inställt på 32byte, men kan definieras om innan du tar nx_ppp.h.
