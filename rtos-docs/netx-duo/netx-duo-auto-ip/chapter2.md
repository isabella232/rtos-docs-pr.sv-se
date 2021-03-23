---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo AutoIP
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo AutoIP-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 42c58a4cdec34a03eda9f42315438e5fbe2ea594
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826169"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo AutoIP

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo AutoIP-komponenten.

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider NetX-AutoIP kan hämtas från vår offentliga käll kods lagrings plats på [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Paketet innehåller tre källfiler, en inkludera filer och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nx_auto_ip. h**: rubrik fil för netx AutoIP
- **nx_auto_ip. c**: c-källfil för netx AutoIP
- **demo_netx_auto_ip. c**: c-källfil för netx AutoIP-demo
- **nx_auto_ip.pdf**: PDF-Beskrivning av netx AutoIP

## <a name="autoip-installation"></a>AutoIP-installation

För att kunna använda NetX-AutoIP bör hela distributionen som nämnts tidigare kopieras till samma katalog där NetX är installerad. Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*", ska *nx_auto_ip. h*-, *nx_auto_ip. c*-och *demo_netx_auto_ip. c* -filer kopieras till den här katalogen.

## <a name="using-autoip"></a>Använda AutoIP

Det är enkelt att använda NetX AutoIP. I princip måste program koden innehålla *nx_auto_ip. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX och netx. När *nx_auto_ip. h* ingår kan program koden sedan göra AutoIP-funktions anropen senare i den här hand boken. Programmet måste även innehålla *nx_auto_ip. c* i build-processen. De här filerna måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer. Detta är allt som krävs för att använda NetX AutoIP.

> [!NOTE]
> Eftersom AutoIP använder NetX ARP-tjänster måste ARP vara aktiverat med det *nx_arp_enable* anropet innan du använder AutoIP.

## <a name="small-example-system"></a>Litet exempel system

Ett exempel på hur enkelt det är att använda NetX AutoIP beskrivs i bild 1,1, som visas nedan. I det här exemplet tas AutoIP-filen *nx_auto_ip. h* in på rad 002. Därefter skapas NetX AutoIP-instansen i "*tx_application_define*" på rad 090. Observera att NetX AutoIP Control Block (auto_ip_0) definierades tidigare som en global variabel på rad 015. När du har skapat en NetX-AutoIP startas den på rad 098. Funktionen för att ändra motringning till IP-adress startar på rad 105, som används för att hantera efterföljande konflikter eller möjlig DHCP-adress matchning.

> [!NOTE]
> Exemplet nedan förutsätter att värd enheten är en enskild enhet. För en multihomed-enhet kan värd programmet använda NetX AutoIP-tjänsten för *nx_auto_ip_interface_* ange att ett sekundärt nätverks gränssnitt ska avsökas för en IP-adress. I [användar handboken för netx](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) finns mer information om hur du konfigurerar multihomed-program. Observera att värd programmet ska använda NetX API- *nx_status_ip_interface_check* för att verifiera att AutoIP har fått en IP-adress.

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

Figur 1,1 exempel på AutoIP användning med NetX

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa NetX-AutoIP. Följande är en lista över alla alternativ, där var och en beskrivs i detalj:

- **NX_DISABLE_ERROR_CHECKING**: det här alternativet tar bort den grundläggande fel kontrollen i AutoIP. Den används vanligt vis när programmet har felsökts.
- **NX_AUTO_IP_PROBE_WAIT**: antalet sekunder som ska förflyta innan den första avsökningen skickas. Som standard definieras värdet som 1.
- **NX_AUTO_IP_PROBE_NUM**: antalet ARP-avsökningar som ska skickas. Som standard definieras värdet som 3.
- **NX_AUTO_IP_PROBE_MIN**: det minsta antal sekunder som ska förflyta mellan att skicka avsökningar. Som standard definieras värdet som 1.
- **NX_AUTO_IP_PROBE_MAX**: det maximala antalet sekunder som ska förflyta mellan att skicka avsökningar. Som standard definieras värdet som 2.
- **NX_AUTO_IP_MAX_CONFLICTS**: antalet AutoIP-konflikter innan bearbetnings fördröjningar ökar. Som standard definieras värdet som 10.
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL**: antalet sekunder som vänte tiden ska utsträckas när det totala antalet konflikter överskrids. Som standard definieras värdet som 60.
- **NX_AUTO_IP_ANNOUNCE_WAIT**: hur många sekunder som ska förflyta innan meddelande skickas. Som standard definieras värdet som 2.
- **NX_AUTO_IP_ANNOUNCE_NUM**: antalet ARP tillkännager att skicka. Som standard definieras värdet som 2.
- **NX_AUTO_IP_ANNOUNCE_INTERVAL**: antalet sekunder som sändningen ska förflyta. Som standard definieras värdet som 2.
- **NX_AUTO_IP_DEFEND_INTERVAL**: antalet sekunder att vänta mellan försvar tillkännager. Som standard definieras värdet som 10.
