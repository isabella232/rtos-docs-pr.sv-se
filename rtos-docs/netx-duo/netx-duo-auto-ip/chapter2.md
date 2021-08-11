---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX Duo AutoIP
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Duo AutoIP-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56bd8cd3cc361bbe0ec435012251e751af8c1566d01e8d52ff38d2eb9c381bfd
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790521"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX Duo AutoIP

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Duo AutoIP-komponenten.

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS NetX AutoIP kan hämtas från vår offentliga källkodsdatabas på [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Paketet innehåller tre källfiler, en med filer och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nx_auto_ip.h:** Rubrikfil för NetX AutoIP
- **nx_auto_ip.c:** C-källfil för NetX AutoIP
- **demo_netx_auto_ip.c:** C-källfil för NetX AutoIP Demo
- **nx_auto_ip.pdf:** PDF-beskrivning av NetX AutoIP

## <a name="autoip-installation"></a>AutoIP-installation

För att kunna använda NetX AutoIP bör hela distributionen som nämns ovan kopieras till samma katalog där NetX är installerat. Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*" ska filerna *nx_auto_ip.h* *, nx_auto_ip.c* och *demo_netx_auto_ip.c* kopieras till den här katalogen.

## <a name="using-autoip"></a>Använda AutoIP

Det är enkelt att använda NetX AutoIP. I princip måste programkoden innehålla *nx_auto_ip.h* efter att den *innehåller tx_api.h* och *nx_api.h* för att kunna använda ThreadX och NetX. När *nx_auto_ip.h* ingår kan programkoden göra AutoIP-funktionsanrop som anges senare i den här guiden. Programmet måste även innehålla *nx_auto_ip.c* i byggprocessen. Dessa filer måste kompileras på samma sätt som andra programfiler och dess objektformulär måste länkas tillsammans med programmets filer. Det här är allt som krävs för att använda NetX AutoIP.

> [!NOTE]
> Eftersom AutoIP använder NetX ARP-tjänster måste ARP aktiveras med nx_arp_enable *innan* du använder AutoIP.

## <a name="small-example-system"></a>Litet exempelsystem

Ett exempel på hur enkelt det är att använda NetX AutoIP beskrivs i bild 1.1, som visas nedan. I det här exemplet tas filen AutoIP include *nx_auto_ip.h* in på rad 002. Därefter skapas NetX AutoIP-instansen i "*tx_application_define*" på rad 090. Observera att NetX AutoIP-kontrollblocket "auto_ip_0" definierades tidigare som en global variabel på rad 015. När det har skapats startas en NetX AutoIP på rad 098. Bearbetningen av funktionen för återanrop av IP-adressändring börjar på rad 105, som används för att hantera efterföljande konflikter eller möjlig DHCP-adressupplösning.

> [!NOTE]
> I exemplet nedan förutsätts att värdenheten är en enhet med en enda värd. För en multihomed-enhet kan värdprogrammet använda NetX *AutoIP-nx_auto_ip_interface_* för att ange ett sekundärt nätverksgränssnitt för avsökning efter en IP-adress. Se [NetX-användarhandboken](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) för mer information om hur du ställer in program med flera startprogram. Observera också att värdprogrammet ska använda NetX API-nx_status_ip_interface_check för *att* verifiera att AutoIP har fått en IP-adress.

```c
#include "tx_api.h"
#include "nx_api.h"
#include "nx_auto_ip.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD              thread_0;
NX_PACKET_POOL         pool_0;
NX_IP                  ip_0;

/* Define the AUTO IP structures for the IP instance. */

NX_AUTO_IP             auto_ip_0;

/* Define the counters used in the demo application... */

ULONG                 thread_0_counter;
ULONG                 address_changes;
ULONG                 error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);
void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int main()
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

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    16, 16, 1, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
                                    pointer, 4096);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Create an IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
        error_counter++;

    /* Create the AutoIP instance for IP Instance 0. */
    status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Check AutoIP create status. */
    if (status)
        error_counter++;

    /* Start AutoIP instances. */
    status = **nx_auto_ip_start**(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);

    /* Check AutoIP start status. */
    if (status)
        error_counter++;

    /* Register an IP address change function for IP Instance 0. */
    status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
                                        (void *) &auto_ip_0);

    /* Check IP address change notify status. */
    if (status)
        error_counter++;
}

/* Define the test thread. */

void     thread_0_entry(ULONG thread_input)
{

UINT     status;
ULONG    actual_status;

    /* Wait for IP address to be resolved. */
    do
    {

        /* Call IP status check routine. */
        status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
            &actual_status, 10000);

    } while (status != NX_SUCCESS);

    /* Since the IP address is resolved at this point, the application can now fully utilize NetX! */

    while(1)
    {

        /* Increment thread 0's counter. */
        thread_0_counter++;

        /* Sleep... */
        tx_thread_sleep(10);
    }
}

void          ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
{

ULONG         ip_address;
ULONG         network_mask;
NX_AUTO_IP    *auto_ip_ptr;

    /* Setup pointer to auto IP instance. */
    auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;

    /* Pickup the current IP address. */
    nx_ip_address_get(ip_ptr, &ip_address, &network_mask);

    /* Determine if the IP address has changed back to zero. If so, make sure the AutoIP instance is started. */
    if (ip_address == 0)
    {

        /* Get the last AutoIP address for this node. */
        nx_auto_ip_get_address(auto_ip_ptr, &ip_address);

        /* Start this AutoIP instance. */
        nx_auto_ip_start(auto_ip_ptr, ip_address);
        }

    /* Determine if IP address has transitioned to a non local IP address. */
    else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
    {

        /* Stop the AutoIP processing. */
        nx_auto_ip_stop(auto_ip_ptr);
    }

    /* Increment a counter. */
    address_changes++;
}
```

Bild 1.1 Exempel på automatiskIP-användning med NetX

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ för att skapa NetX AutoIP. Följande är en lista över alla alternativ, där vart och ett beskrivs i detalj:

- **NX_DISABLE_ERROR_CHECKING:** Det här alternativet tar bort den grundläggande autoIP-felkontrollen. Det används vanligtvis när programmet har felsökts.
- **NX_AUTO_IP_PROBE_WAIT:** Antalet sekunder som ska vänta innan den första avsökningen skickas. Som standard definieras det här värdet som 1.
- **NX_AUTO_IP_PROBE_NUM:** Antalet ARP-avsökningar som ska skickas. Som standard definieras det här värdet som 3.
- **NX_AUTO_IP_PROBE_MIN:** Det minsta antal sekunder som ska vänta mellan att skicka avsökningar. Som standard definieras det här värdet som 1.
- **NX_AUTO_IP_PROBE_MAX:** Det maximala antalet sekunder att vänta mellan att skicka avsökningar. Som standard definieras det här värdet som 2.
- **NX_AUTO_IP_MAX_CONFLICTS:** Antalet AutoIP-konflikter innan bearbetningsfördröjningar ökar. Som standard definieras det här värdet som 10.
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL:** Antalet sekunder som väntetiden ska utökas när det totala antalet konflikter överskrids. Som standard definieras det här värdet som 60.
- **NX_AUTO_IP_ANNOUNCE_WAIT:** Antalet sekunder som ska vänta innan meddelandet skickas. Som standard definieras det här värdet som 2.
- **NX_AUTO_IP_ANNOUNCE_NUM:** Antalet ARP som ska skickas. Som standard definieras det här värdet som 2.
- **NX_AUTO_IP_ANNOUNCE_INTERVAL:** Antalet sekunder som ska vänta mellan att skicka meddelanden. Som standard definieras det här värdet som 2.
- **NX_AUTO_IP_DEFEND_INTERVAL:** Antalet sekunder som ska vänta mellan försvaren. Som standard definieras det här värdet som 10.
