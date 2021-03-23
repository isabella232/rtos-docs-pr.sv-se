---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Point-to-Point Protocol (PPP)
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Point-to-Point Protocol (PPP)-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40f09da31f5541208c3b2cc0eeb54850b3d71f7c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826655"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-point-to-point-protocol-ppp"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX Point-to-Point Protocol (PPP)

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Point-to-Point Protocol (PPP)-komponenten.

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider NetX Point-to-Point Protocol-paketet (PPP) finns på <https://github.com/azure-rtos/netx> . Paketet innehåller följande filer:

- **nx_ppp. h**: rubrik fil för PPP för netx
- **nx_ppp. c**: c-KÄLLFIL för PPP för netx
- **nx_ppp.pdf**: PDF-Beskrivning av PPP för netx
- **demo_netx_ppp. c**: netx PPP-demonstration

## <a name="ppp-installation"></a>PPP-installation

För att du ska kunna använda PPP för NetX, ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX är installerat. Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*", ska *nx_ppp. h* -och *nx_ppp. c* -filerna kopieras till den här katalogen.

## <a name="using-ppp"></a>Använda PPP

Det är enkelt att använda PPP för NetX. I princip måste program koden innehålla *nx_ppp. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX respektive netx. När *nx_ppp. h* ingår kan program koden sedan göra de PPP-funktions anrop som anges längre fram i den här hand boken. Programmet måste även innehålla *nx_ppp. c* i build-processen. Den här filen måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer. Detta är allt som krävs för att använda NetX PPP.

## <a name="using-modems"></a>Använda modem

Om ett modem krävs för anslutning till Internet krävs vissa särskilda överväganden för att kunna använda NetX-PPP-produkten. Med hjälp av ett modem införs i princip den ytterligare initierings logiken och logiken för att förlora kommunikationen. Dessutom utförs de flesta ytterligare modem logiken utanför kontexten för NetX PPP. Det grundläggande flödet för att använda NetX PPP med ett modem ser ut ungefär så här:

1. Initiera modem

1. Ring Internet Service Provider (ISP)

1. Vänta på anslutning

1. Vänta på UserID-prompt

1. Starta NetX PPP [PPP i drift]

1. Förlust av kommunikation

1. Stoppa NetX PPP (eller starta om via nx_ppp_restart)

### <a name="initialize-modem"></a>Initiera modem

Med hjälp av programmets lågnivå seriella utmatnings rutin initieras modemet via en serie ASCII-tecken kommandon (se modem dokumentationen för mer information).

### <a name="dial-internet-service-provider"></a>Ring Internet tjänst leverantör

Med hjälp av programmets lågnivå serie för seriella utdata uppmanas modemet att ringa upp Internet leverantören. Till exempel är följande typiska för en ASCII-sträng som används för att ringa upp en ISP på siffran 123-4567:

"ATDT123456\r"

### <a name="wait-for-connection"></a>Vänta på anslutning

I det här skedet väntar programmet på att ta emot indikationer från modemet som en anslutning har upprättats till. Detta åstadkommer du genom att söka efter tecken från programmets lågnivå seriella Indatatyp. Vanligt vis returnerar modem en ASCII-sträng "CONNECT" när en anslutning har upprättats.

### <a name="wait-for-user-id-prompt"></a>Vänta på användar-ID-prompt

När anslutningen har upprättats måste programmet nu vänta på en första inloggningsbegäran från Internet leverantören. Detta är vanligt vis formen av en ASCII-sträng som "inloggning?"

### <a name="start-netx-ppp"></a>Starta NetX PPP

I det här läget kan NetX-PPP startas. Detta åstadkommer du genom att anropa *nx_ppp_creates* tjänsten följt av *nx_ip_creates* tjänsten. Ytterligare tjänster för att aktivera PAP och för att konfigurera PPP-IP-adresser kan också krävas. Mer information finns i följande avsnitt i den här hand boken.

### <a name="loss-of-communication"></a>Förlust av kommunikation

När PPP har startats skickas all icke-PPP-information till den "Ogiltig paket hantering"-rutinen som angetts till tjänsten *nx_ppp_create* . Vanligt vis skickar modem en ASCII-sträng, till exempel "ingen BÄRVÅG" när kommunikationen går förlorad hos Internet leverantören. När programmet tar emot ett icke-PPP-paket med sådan information, bör det fortsätta att antingen stoppa NetX-PPP-instansen eller starta om datorn med PPP-tillstånd via *nx_ppp_restart* -API: et.

### <a name="stop-netx-ppp"></a>Stoppa NetX PPP

Det är ganska enkelt att stoppa NetX-PPP. I princip måste alla skapade Sockets vara obundna och ta bort. Ta sedan bort IP-instansen via tjänsten *nx_ip_delete* . När IP-instansen har tagits bort ska *nx_ppp_delete* -tjänsten anropas för att avsluta processen att stoppa PPP. Nu kan programmet nu försöka återupprätta kommunikationen med Internet leverantören.

## <a name="small-example-system"></a>Litet exempel system

Ett exempel som illustrerar hur enkelt det är att använda NetX PPP beskrivs i bild 1,1 som visas nedan. I det här exemplet tas PPP-filen *nx_ppp. h* in på rad 3. Därefter skapas PPP i *"tx_application_define*" på rad 56. PPP-kontroll blocket "*my_ppp*" definierades som en global variabel på rad 9 tidigare. 

>[!NOTE]
>PPP bör skapas innan du skapar IP-instansen. När du har skapat PPP och IP väntar tråden "*my_thread*" på att PPP-länken ska komma i rad 98. På rad 104 är både PPP och NetX fullt operativa.

Det element som inte visas i det här exemplet är programmets serie byte erhåller ISR. Det måste anropa *nx_ppp_byte_receive* med "*my_ppp*" och mottagna byte som indataparametrar.

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
## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa PPP för NetX. I följande lista beskrivs var och en i detalj:

- **NX_DISABLE_ERROR_CHECKING**: det här alternativet tar bort grundläggande fel sökning av PPP. Den används vanligt vis när programmet har felsökts.
- **NX_PPP_PPPOE_ENABLE**: om det är DEFINIERAT kan PPP överföra paket över Ethernet
- **NX_PPP_BASE_TIMEOUT**: Detta definierar period frekvensen (i timer-Tick) som PPP-trådens aktivitet är aktive för att söka efter PPP-händelser. Standardvärdet är 1 * NX_IP_PERIODIC_RATE (100 Tick).
- **NX_PPP_DISABLE_INFO**: om det här är definierat inaktive ras intern insamling av PPP-information.
- **NX_PPP_DEBUG_LOG_ENABLE**: om den har definierats är intern PPP-felsökning aktive rad.
- **NX_PPP_DEBUG_LOG_PRINT_ENABLE**: om det är definierat är den interna PPP-felsöknings loggen *printf* till *Stdio* aktive rad. Detta är endast giltigt om fel söknings loggen också är aktive rad.
- **NX_PPP_DEBUG_LOG_SIZE**: storleken på fel söknings loggen (antalet poster i fel söknings loggen). När den senaste posten hamnade, radbryts fel söknings avbildningen till den första posten och skriver över alla data som tidigare har registrerats. Standardvärdet är 50.
- **NX_PPP_DEBUG_FRAME_SIZE**: maximal mängd data som samlas in från en mottagen paket nytto last och sparas i fel söknings utdata. Standardvärdet är 50.
- **NX_PPP_DISABLE_CHAP**: om det är definierat tas intern PPP CHAP-logik bort, inklusive MD5 Digest-logiken.
- **NX_PPP_DISABLE_PAP**: om det är definierat tas intern PPP PAP-logik bort.
- **NX_PPP_DNS_OPTION_DISABLE**: om alternativet är definierat är DNS-alternativet inaktiverat i IPCP-svaret.  Som standard är det här alternativet inte definierat (DNS-alternativet är inställt).
- **NX_PPP_DNS_ADDRESS_MAX_RETRIES**: Detta anger hur många gånger PPP-värden ska begära en DNS-serveradress från peer-datorn i IPCP-tillstånd. Detta har ingen påverkan om NX_PPP_DNS_OPTION_DISABLE har definierats. Standardvärdet är 2.
- **NX_PPP_HASHED_VALUE_SIZE**: anger storleken på "hashed Value"-strängar som används i CHAP-autentisering. Standardvärdet är inställt på 16 byte, men kan omdefinieras innan *nx_ppp. h.*
- **NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: Detta definierar Max antalet återförsök om PPP-tiden överskrids innan en annan LCP-konfiguration begär ett meddelande skickas. När det här talet nås avbryts PPP-handskakningen och länkens status är nere. Standardvärdet är 20.
- **NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: Detta definierar Max antalet återförsök om PPP-tiden överskrids innan ett annat meddelande om PAP-autentiseringsbegäran skickas. När det här talet nås avbryts PPP-handskakningen och länkens status är nere. Standardvärdet är 20.
- **NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: Detta definierar Max antalet återförsök om PPP-tiden överskrids innan ett annat CHAP-utmanings meddelande skickas. När det här talet nås avbryts PPP-handskakningen och länkens status är nere. Standardvärdet är 20.
- **NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: Detta definierar Max antalet återförsök om PPP-tiden överskrids innan en annan IPCP-konfiguration skickas. När det här talet nås avbryts PPP-handskakningen och länkens status är nere. Standardvärdet är 20.
- **NX_PPP_MRU**: anger den maximala mottagnings enheten (MRU) för PPP. Som standard är det här värdet 1 500 byte (minimivärdet). Den här inställningen kan anges av programmet innan *nx_ppp. h*.
- **NX_PPP_MINIMUM_MRU**: anger det lägsta MRU som tas emot i ett LCP-meddelande om att konfigurera begär Anden. Som standard är det här värdet 1 500 byte (minimivärdet). Den här inställningen kan anges av programmet innan *nx_ppp. h*.
- **NX_PPP_NAME_SIZE**: anger storleken på "namn"-strängar som används vid autentisering. Standardvärdet är inställt på 32bytes, men kan definieras om innan inkludering av * nx_ppp. h.
- **NX_PPP_PASSWORD_SIZE**: anger storleken på "Password"-strängar som används i autentisering. Standardvärdet är inställt på 32bytes, men kan omdefinieras innan du tar med *nx_ppp. h.*
- **NX_PPP_PROTOCOL_TIMEOUT**: Detta definierar vänte alternativet (i sekunder) för att PPP-aktiviteten ska ta emot ett svar på ett meddelande om PPP-protokoll begär Ande. Standardvärdet är 4 sekunder.
- **NX_PPP_RECEIVE_TIMEOUTS**: Detta definierar antalet gånger som en tids gräns i PPP-tråden väntar på att ta emot nästa-tecknen i en PPP-meddelande ström. Därefter släpper PPP paketet och börjar vänta på att ta emot nästa PPP-meddelande. Standardvärdet är 4.
- **NX_PPP_SERIAL_BUFFER_SIZE**: anger storleken på den seriella bufferten för mottagnings tecknen. Som standard är det här värdet 3 000 byte. Den här inställningen kan anges av programmet innan *nx_ppp. h*.
- **NX_PPP_TIMEOUT**: Detta definierar vänte alternativet (i timer-Tick) för att allokera paket för att överföra data och buffra PPP-Datadata till paket som ska skickas till IP-lagret. Standardvärdet är 4 * NX_IP_PERIODIC_RATE (400 Tick).
- **NX_PPP_THREAD_TIME_SLICE**: Time-slice-alternativ för PPP-trådar. Som standard är det här värdet TX_NO_TIME_SLICE. Den här inställningen kan anges av programmet innan *nx_ppp. h*.
- **NX_PPP_VALUE_SIZE**: anger storleken på "värde"-strängar som används i CHAP-autentisering. Standardvärdet är inställt på 32bytes, men kan omdefinieras innan du tar med nx_ppp. h.
