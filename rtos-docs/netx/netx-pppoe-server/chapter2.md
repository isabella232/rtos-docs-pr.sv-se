---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX PPPoE-Server
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX PPPoE-Server komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5b52164911676b68c67da01d698e41c02730e45a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825587"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-server"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX PPPoE-Server

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX PPPoE-Server komponenten.

## <a name="product-distribution"></a>Produkt distribution

PPPoE-Server för NetX finns på [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nx_pppoe_server. h**: rubrik fil för PPPoE-Server för netx
- **nx_pppoe_server. c**: c-källfil för PPPoE-Server för netx
- **nx_pppoe_server.pdf**: PDF-Beskrivning av PPPoE-Server för netx
- **demo_netx_pppoe_server. c**: netx-demonstration av PPPoE-Server

## <a name="pppoe-server-installation"></a>Installation av PPPoE-Server

För att du ska kunna använda PPPoE-servern för NetX bör hela distributionen som nämnts tidigare kopieras till samma katalog där NetX har installerats. Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*", ska *nx_pppoe_server. h* -och *nx_pppoe_server. c* -filerna kopieras till den här katalogen.

## <a name="using-pppoe-server"></a>Använda PPPoE-Server

Det är enkelt att använda PPPoE-Server för NetX. I princip måste program koden innehålla *nx_pppoe_server. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX respektive netx. När *nx_pppoe_server. h* ingår kan program koden göra PPPoE-serverns funktions anrop senare i den här hand boken. Programmet måste även innehålla *nx_pppoe_server. c* i build-processen. Den här filen måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer. Detta är allt som krävs för att använda NetX PPPoE-Server.

## <a name="small-example-system"></a>Litet exempel system

Följande är ett exempel som illustrerar hur du använder NetX PPPoE-Server beskrivs i bild 1,1. I det här exemplet inkluderar PPPoE-servern filen *nx_pppoe_server. h* i rad 50. Därefter skapas PPPoE-servern i *"thread_0_entry*" på rad 248. Observera att PPPoE-servern ska skapas efter att du har skapat IP-instansen. IP-instansen skapas och initieras line165. PPPoE-serverns kontroll block *pppoe_server* definierades som en global variabel på rad 79 tidigare. Aviserings funktionerna anges på rad 257. Observera att pppoe_session_data_receive notify funktion måste anges. När du har skapat en IP-och PPPoE-Server kan du upprätta en PPPoE-session på anropet till nx_pppoe_server_enable på rad 272 i PPPoE-servern.

I allmänhet ska PPPoE-modulen användas med PPP-modulen. I det här exemplet inkluderar PPP-servern filen *nx_ppp. h* i rad 49. Sedan skapas PPP-servern på rad 174. Rad 182 konfigurera funktionen för att skicka PPP-paket. Rad 188-200 konfigurera IP-adresserna och definiera PAP-protokollet. Rad 115-139-konfigurera användar namn och lösen ord för PAP-protokollet.

Efter att PPPoE-sessionen har upprättats. Programmet kan anropa nx_pppoe_server_session_get för att hämta sessionsinformation (klientens MAC-adress och sessions-ID) på rad 281.

Om programmet inte längre bearbetar PPP-trafik, PppCloseInd eller nx_pppoe_server_session_terminate för att avsluta PPPoE-sessionen.

> [!NOTE]
> I det här exemplet fungerar PPPoE-servern med normal IP-stack på samma gång och delar en Ethernet-drivrutin. Överför samma Ethernet-drivrutin för den normala IP-instansen på rad 165 och PPPoE-Server instans på rad 248.

> [!NOTE]
> Funktionerna tillhandahålls av PPPoE-implementeringen för anrop av program varan under definierade NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE.

Aktiverar funktionen som styr PPPoE-sessionen om den har definierats.

PPPoE-servern svarar inte automatiskt på begäran förrän programmet anropar specifik API, om det inte har definierats, svarar PPPoE-servern automatiskt på begäran. Den aktive ras som standard i nx_pppoe_server. h.

Obs! omdefiniera **NX_PHYSICAL_HEADER** till 24 för att se till att det finns tillräckligt med utrymme för att fylla i fysiskt sidhuvud. Fysiskt sidhuvud: 14 (Ethernet-huvud) + 6 (PPPoE-huvud) + 2 (PPP-huvud) + 2 (Aligment för fyra byte).

```c
/**************************************************************************/
/**************************************************************************/
/**                                                                       */
/** NetX PPPoE Server stack Component                                     */
/**                                                                       */
/** This is a small demo of the high-performance NetX PPPoE Server        */
/** stack. This demo includes IP instance, PPPoE Server and PPP Server    */
/** stack. Create one IP instance includes two interfaces to support      */
/** for normal IP stack and PPPoE Server, PPPoE Server can use the        */
/** mutex of IP instance to send PPPoE message when share one Ethernet    */
/** driver. PPPoE Server work with normal IP instance at the same time.   */
/**                                                                       */
/** Note1: Substitute your Ethernet driver instead of                     */
/** _nx_ram_network_driver before run this demo                           */
/**                                                                       */
/** Note2: Prerequisite for using PPPoE.                                  */
/** Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling  */
/** in physical header. Physical header:14(Ethernet header)               */
/** + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)             */
/**                                                                       */
/**************************************************************************/
/**************************************************************************/


/*****************************************************************/
/*                            NetX Stack                         */
/*****************************************************************/

                                      /***************************/
                                      /* PPP Server              */
                                      /***************************/

                                      /***************************/
                                      /* PPPoE Server            */
                                      /***************************/
/***************************/         /***************************/
/* Normal Ethernet Type    */         /* PPPoE Ethernet Type     */
/***************************/         /***************************/
/***************************/         /***************************/
/* Interface 0             */         /* Interface 1             */
/***************************/         /***************************/

/*****************************************************************/
/*                     Ethernet Dirver                           */
/*****************************************************************/

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_ppp.h"
#include     "nx_pppoe_server.h"

/* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified to match PPPoE moduler under this definition. */
#ifdef NX_PPP_PPPOE_ENABLE

/*   If the driver is not initialized in other module, define */
/*   NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE to initialize the driver in PPPoE module. */
/*   In this demo, the driver has been initialized in IP module. */

#ifdef NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE

/*   NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE: If defined, enables the feature that */
/*   controls the PPPoE session. PPPoE server does not automatically response to the */
/*   request until application call specific API. */

/* Define the block size. */
#define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
#define     DEMO_STACK_SIZE         2048
#define     PPPOE_THREAD_SIZE       2048

/* Define the ThreadX and NetX object control blocks... */
TX_THREAD           thread_0;

/* Define the packet pool and IP instance for normal IP instnace. */
NX_PACKET_POOL      pool_0;
NX_IP               ip_0;

/* Define the PPP Server instance. */
NX_PPP              ppp_server;

/* Define the PPPoE Server instance. */
NX_PPPOE_SERVER     pppoe_server;

/* Define the counters. */
CHAR                *pointer;
ULONG               error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);

/***** Substitute your PPP driver entry function here *********/
extern void     _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);

/***** Substitute your Ethernet driver entry function here *********/
extern void     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define the callback functions. */
void     PppDiscoverReq(UINT interfaceHandle);
void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data);
void     PppCloseRsp(UINT interfaceHandle);
void     PppCloseReq(UINT interfaceHandle);
void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id);
void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data);

/* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP. */
/* Functions to be provided by PPP for calling by the PPPoE Stack. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

UINT verify_login(CHAR *name, CHAR *password)
{

    if ((name[0] == 'm') &&
        (name[1] == 'y') &&
        (name[2] == 'n') &&
        (name[3] == 'a') &&
        (name[4] == 'm') &&
        (name[5] == 'e') &&
        (name[6] == (CHAR) 0) &&
        (password[0] == 'm') &&
        (password[1] == 'y') &&
        (password[2] == 'p') &&
        (password[3] == 'a') &&
        (password[4] == 's') &&
        (password[5] == 's') &&
        (password[6] == 'w') &&
        (password[7] == 'o') &&
        (password[8] == 'r') &&
        (password[9] == 'd') &&
        (password[10] == (CHAR) 0))
            return(NX_SUCCESS);
    else
        return(NX_PPP_ERROR);
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{

    UINT status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool for normal IP instance. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
                                    (1536 + sizeof(NX_PACKET)),
                                    pointer, NX_PACKET_POOL_SIZE);
                                    pointer = pointer + NX_PACKET_POOL_SIZE;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create an normal IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 43),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create the PPP instance. */
    status = nx_ppp_create(&ppp_server, "PPP Instance", &ip_0, pointer, 2048, 1,
                            &pool_0, NX_NULL, NX_NULL);
    pointer = pointer + 2048;

    /* Check for PPP create error. */
    if (status)
        error_counter++;

    /* Set the PPP packet send function. */
    status = nx_ppp_packet_send_set(&ppp_server, ppp_server_packet_send);

    /* Check for PPP packet send function set error. */
    if (status)
        error_counter++;

    /* Define IP address. This PPP instance is effectively the server since it has both IP addresses. */
    status = nx_ppp_ip_address_assign(&ppp_server, IP_ADDRESS(192, 168, 10, 43),                                         IP_ADDRESS(192, 168, 10, 44));

    /* Check for PPP IP address assign error. */
    if (status)
        error_counter++;

    /* Setup PAP, this PPP instance is effectively the server since it will verify the name and password. */
    status = nx_ppp_pap_enable(&ppp_server, NX_NULL, verify_login);

    /* Check for PPP PAP enable error. */
    if (status)
        error_counter++;

    /* Attach an interface for PPP. */
    status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", 
                            IP_ADDRESS(0, 0, 0, 0), 0, nx_ppp_driver);

    /* Check for error. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for Normal IP Instance. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
        error_counter++;

    /* Enable ICMP */
    status = nx_icmp_enable(&ip_0);
    if(status)
        error_counter++;

    /* Enable UDP traffic. */
    status = nx_udp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Enable TCP traffic. */
    status = nx_tcp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;
}

/* Define the test threads. */

void     thread_0_entry(ULONG thread_input)
{
UINT     status;
ULONG    ip_status;

    /* Create the PPPoE instance. */
    status = nx_pppoe_server_create(&pppoe_server, (UCHAR *)"PPPoE Server", &ip_0, 0,
                    _nx_ram_network_driver, &pool_0, pointer, PPPOE_THREAD_SIZE, 4);
    pointer = pointer + PPPOE_THREAD_SIZE;
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the callback notify function. */
    status = nx_pppoe_server_callback_notify_set(&pppoe_server, PppDiscoverReq,
        PppOpenReq, PppCloseRsp, PppCloseReq, PppTransmitDataReq, PppReceiveDataRsp);

    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call function function to set the default service Name. */
        /* PppInitInd(length, aData); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

    /* Enable PPPoE Server. */
    status = nx_pppoe_server_enable(&pppoe_server);
    if (status)
    {
        error_counter++;
        return;
    }

    /* Get the PPPoE Client physical address and Session ID after establish PPPoE Session. */
    /*
        status = nx_pppoe_server_session_get(&pppoe_server, interfaceHandle, &client_mac_msw, &client_mac_lsw, &session_id);
        if (status)
            error_counter++;
    */

    /* Wait for the link to come up. */
    status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                            &ip_status, NX_WAIT_FOREVER);
    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to terminate the PPPoE Session. */
        /* PppCloseInd(interfaceHandle, causeCode); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

}

void     PppDiscoverReq(UINT interfaceHandle)
{

    /* Receive the PPPoE Discovery Initiation Message. */
    
    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to define the Service Name field of the PADO packet. */
        PppDiscoverCnf(0, NX_NULL, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data)
{

    /* Get the notify that receive the PPPoE Discovery Request Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to accept the PPPoE session. */
        PppOpenCnf(NX_TRUE, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseRsp(UINT interfaceHandle)
{

    /* Get the notify that receive the PPPoE Discovery Terminate Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to confirm that the handle has been freed. */
        PppCloseCnf(interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseReq(UINT interfaceHandle)
{

    /* Get the notify that PPPoE Discovery Terminate Message has been sent. */

}

void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id)
{

    NX_PACKET *packet_ptr;

    /* Get the notify that receive the PPPoE Session data. */

    /* Call PPP Server to receive the PPP data fame. */
    packet_ptr = (NX_PACKET *)(packet_id);
    nx_ppp_packet_receive(&ppp_server, packet_ptr);

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to confirm that the data has been processed. */
        PppTransmitDataCnf(interfaceHandle, data, packet_id);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data)
{

    /* Get the notify that the PPPoE Session data has been sent. */

}

/* PPP Server send function. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr)
{

    /* For Express Logic's PPP test, the session should be the first session, so set interfaceHandle as 0. */
    UINT interfaceHandle = 0;

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        while(packet_ptr)
        {

            /* Call functions to be provided by PPPoE for TTP. */
            PppReceiveDataInd(interfaceHandle, (packet_ptr -> nx_packet_append_ptr -
            packet_ptr -> nx_packet_prepend_ptr), packet_ptr -> nx_packet_prepend_ptr);

            /* Move to the next packet structure. */
            packet_ptr = packet_ptr -> nx_packet_next;
        }
    #else
        /* Directly Call PPPoE send function to send out the data through PPPoE module. */
        nx_pppoe_server_session_packet_send(&pppoe_server, interfaceHandle, packet_ptr);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}
#endif /* NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE */

#endif /* NX_PPP_PPPOE_ENABLE */
```

Figur 1,1 exempel på användning av PPPoE-servrar med NetX

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa en PPPoE-Server för NetX. I följande lista beskrivs var och en i detalj:

- **NX_DISABLE_ERROR_CHECKING**: det här alternativet tar bort den grundläggande fel kontrollen för PPPoE-servern. Den används vanligt vis när programmet har felsökts.

- **NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: om det är definierat aktiverar funktionen som styr PPPoE-sessionen. PPPoE-servern svarar inte automatiskt på begäran förrän programmet anropar ett specifik API.

- **NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: om den har definierats kan funktionen initiera Ethernet-drivrutinen i PPPoE-modulen. Den inaktive ras som standard.

- **NX_PPPOE_SERVER_THREAD_TIME_SLICE**: Time-slice-alternativ för PPPoE-serverns tråd. Som standard är det här värdet TX_NO_TIME_SLICE.

- **NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: Detta definierar det högsta antalet samtidiga klient sessioner. Som standard är det här värdet 10.

- **NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: Detta definierar Max storleken för värd-uniq. Som standard är det här värdet 32.

- **NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: Detta definierar Max storleken för relä-session-ID. Som standard är det här värdet 12.

- **NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: anger den minsta paket nytto Last storleken för PPPoE-servern. Om paketets nytto Last storlek är större än det här värdet kan du undvika paket länkning. Som standard är det här värdet 1520 (maximal nytto Last storlek för Ethernet 1500, Ethernet-huvud 14, CRC 2 och fyra byte 4).

- **NX_PPPOE_SERVER_PACKET_TIMEOUT**: Detta definierar vänte Potion (i timer-Tick) för att allokera paket eller lägga till data i paket. Som standard är det här värdet **NX_IP_PERIODIC_RATE** (100 Tick).

- **NX_PPPOE_SERVER_START_SESSION_ID**: Detta definierar startsessions-ID: t för att tilldela PPPoE-sessionen. Som standard är det här värdet 0X4944 (ASCII-värde för ID).