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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a><span data-ttu-id="b39f8-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo AutoIP</span><span class="sxs-lookup"><span data-stu-id="b39f8-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo AutoIP</span></span>

<span data-ttu-id="b39f8-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo AutoIP-komponenten.</span><span class="sxs-lookup"><span data-stu-id="b39f8-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo AutoIP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="b39f8-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="b39f8-105">Product Distribution</span></span>

<span data-ttu-id="b39f8-106">Azure återställnings tider NetX-AutoIP kan hämtas från vår offentliga käll kods lagrings plats på [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) .</span><span class="sxs-lookup"><span data-stu-id="b39f8-106">Azure RTOS NetX AutoIP can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="b39f8-107">Paketet innehåller tre källfiler, en inkludera filer och en PDF-fil som innehåller det här dokumentet, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="b39f8-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="b39f8-108">**nx_auto_ip. h**: rubrik fil för netx AutoIP</span><span class="sxs-lookup"><span data-stu-id="b39f8-108">**nx_auto_ip.h**: Header file for NetX AutoIP</span></span>
- <span data-ttu-id="b39f8-109">**nx_auto_ip. c**: c-källfil för netx AutoIP</span><span class="sxs-lookup"><span data-stu-id="b39f8-109">**nx_auto_ip.c**: C Source file for NetX AutoIP</span></span>
- <span data-ttu-id="b39f8-110">**demo_netx_auto_ip. c**: c-källfil för netx AutoIP-demo</span><span class="sxs-lookup"><span data-stu-id="b39f8-110">**demo_netx_auto_ip.c**: C Source file for NetX AutoIP Demo</span></span>
- <span data-ttu-id="b39f8-111">**nx_auto_ip.pdf**: PDF-Beskrivning av netx AutoIP</span><span class="sxs-lookup"><span data-stu-id="b39f8-111">**nx_auto_ip.pdf**: PDF description of NetX AutoIP</span></span>

## <a name="autoip-installation"></a><span data-ttu-id="b39f8-112">AutoIP-installation</span><span class="sxs-lookup"><span data-stu-id="b39f8-112">AutoIP Installation</span></span>

<span data-ttu-id="b39f8-113">För att kunna använda NetX-AutoIP bör hela distributionen som nämnts tidigare kopieras till samma katalog där NetX är installerad.</span><span class="sxs-lookup"><span data-stu-id="b39f8-113">In order to use NetX AutoIP, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="b39f8-114">Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*", ska *nx_auto_ip. h*-, *nx_auto_ip. c*-och *demo_netx_auto_ip. c* -filer kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="b39f8-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_auto_ip.h*, *nx_auto_ip.c*, and *demo_netx_auto_ip.c* files should be copied into this directory.</span></span>

## <a name="using-autoip"></a><span data-ttu-id="b39f8-115">Använda AutoIP</span><span class="sxs-lookup"><span data-stu-id="b39f8-115">Using AutoIP</span></span>

<span data-ttu-id="b39f8-116">Det är enkelt att använda NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b39f8-116">Using NetX AutoIP is easy.</span></span> <span data-ttu-id="b39f8-117">I princip måste program koden innehålla *nx_auto_ip. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX och netx.</span><span class="sxs-lookup"><span data-stu-id="b39f8-117">Basically, the application code must include *nx_auto_ip.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="b39f8-118">När *nx_auto_ip. h* ingår kan program koden sedan göra AutoIP-funktions anropen senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="b39f8-118">Once *nx_auto_ip.h* is included, the application code is then able to make the AutoIP function calls specified later in this guide.</span></span> <span data-ttu-id="b39f8-119">Programmet måste även innehålla *nx_auto_ip. c* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="b39f8-119">The application must also include *nx_auto_ip.c* in the build process.</span></span> <span data-ttu-id="b39f8-120">De här filerna måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="b39f8-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="b39f8-121">Detta är allt som krävs för att använda NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b39f8-121">This is all that is required to use NetX AutoIP.</span></span>

> [!NOTE]
> <span data-ttu-id="b39f8-122">Eftersom AutoIP använder NetX ARP-tjänster måste ARP vara aktiverat med det *nx_arp_enable* anropet innan du använder AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b39f8-122">Since AutoIP utilizes NetX ARP services, ARP must be enabled with the *nx_arp_enable* call prior to using AutoIP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="b39f8-123">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="b39f8-123">Small Example System</span></span>

<span data-ttu-id="b39f8-124">Ett exempel på hur enkelt det är att använda NetX AutoIP beskrivs i bild 1,1, som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="b39f8-124">An example of how easy it is to use NetX AutoIP is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="b39f8-125">I det här exemplet tas AutoIP-filen *nx_auto_ip. h* in på rad 002.</span><span class="sxs-lookup"><span data-stu-id="b39f8-125">In this example, the AutoIP include file *nx_auto_ip.h* is brought in at line 002.</span></span> <span data-ttu-id="b39f8-126">Därefter skapas NetX AutoIP-instansen i "*tx_application_define*" på rad 090.</span><span class="sxs-lookup"><span data-stu-id="b39f8-126">Next, the NetX AutoIP instance is created in "*tx_application_define*" at line 090.</span></span> <span data-ttu-id="b39f8-127">Observera att NetX AutoIP Control Block (auto_ip_0) definierades tidigare som en global variabel på rad 015.</span><span class="sxs-lookup"><span data-stu-id="b39f8-127">Note that the NetX AutoIP control block "auto_ip_0" was defined previously as a global variable at line 015.</span></span> <span data-ttu-id="b39f8-128">När du har skapat en NetX-AutoIP startas den på rad 098.</span><span class="sxs-lookup"><span data-stu-id="b39f8-128">After successful creation, an NetX AutoIP is started at line 098.</span></span> <span data-ttu-id="b39f8-129">Funktionen för att ändra motringning till IP-adress startar på rad 105, som används för att hantera efterföljande konflikter eller möjlig DHCP-adress matchning.</span><span class="sxs-lookup"><span data-stu-id="b39f8-129">The IP address change callback function processing starts at line 105, which is used to handle subsequent conflicts or possible DHCP address resolution.</span></span>

> [!NOTE]
> <span data-ttu-id="b39f8-130">Exemplet nedan förutsätter att värd enheten är en enskild enhet.</span><span class="sxs-lookup"><span data-stu-id="b39f8-130">The example below assumes the host device is a single-homed device.</span></span> <span data-ttu-id="b39f8-131">För en multihomed-enhet kan värd programmet använda NetX AutoIP-tjänsten för *nx_auto_ip_interface_* ange att ett sekundärt nätverks gränssnitt ska avsökas för en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="b39f8-131">For a multihomed device, the host application can use the NetX AutoIP service *nx_auto_ip_interface_* set to specify a secondary network interface to probe for an IP address.</span></span> <span data-ttu-id="b39f8-132">I [användar handboken för netx](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) finns mer information om hur du konfigurerar multihomed-program.</span><span class="sxs-lookup"><span data-stu-id="b39f8-132">See the [NetX User Guide](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) for more details on setting up multihomed applications.</span></span> <span data-ttu-id="b39f8-133">Observera att värd programmet ska använda NetX API- *nx_status_ip_interface_check* för att verifiera att AutoIP har fått en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="b39f8-133">Note further that the host application should use the NetX API *nx_status_ip_interface_check* to verify AutoIP has obtained an IP address.</span></span>

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

<span data-ttu-id="b39f8-134">Figur 1,1 exempel på AutoIP användning med NetX</span><span class="sxs-lookup"><span data-stu-id="b39f8-134">Figure 1.1 Example of AutoIP use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="b39f8-135">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="b39f8-135">Configuration Options</span></span>

<span data-ttu-id="b39f8-136">Det finns flera konfigurations alternativ för att skapa NetX-AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b39f8-136">There are several configuration options for building NetX AutoIP.</span></span> <span data-ttu-id="b39f8-137">Följande är en lista över alla alternativ, där var och en beskrivs i detalj:</span><span class="sxs-lookup"><span data-stu-id="b39f8-137">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="b39f8-138">**NX_DISABLE_ERROR_CHECKING**: det här alternativet tar bort den grundläggande fel kontrollen i AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b39f8-138">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic AutoIP error checking.</span></span> <span data-ttu-id="b39f8-139">Den används vanligt vis när programmet har felsökts.</span><span class="sxs-lookup"><span data-stu-id="b39f8-139">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="b39f8-140">**NX_AUTO_IP_PROBE_WAIT**: antalet sekunder som ska förflyta innan den första avsökningen skickas.</span><span class="sxs-lookup"><span data-stu-id="b39f8-140">**NX_AUTO_IP_PROBE_WAIT**: The number of seconds to wait before sending first probe.</span></span> <span data-ttu-id="b39f8-141">Som standard definieras värdet som 1.</span><span class="sxs-lookup"><span data-stu-id="b39f8-141">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="b39f8-142">**NX_AUTO_IP_PROBE_NUM**: antalet ARP-avsökningar som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="b39f8-142">**NX_AUTO_IP_PROBE_NUM**: The number of ARP probes to send.</span></span> <span data-ttu-id="b39f8-143">Som standard definieras värdet som 3.</span><span class="sxs-lookup"><span data-stu-id="b39f8-143">By default, this value is defined as 3.</span></span>
- <span data-ttu-id="b39f8-144">**NX_AUTO_IP_PROBE_MIN**: det minsta antal sekunder som ska förflyta mellan att skicka avsökningar.</span><span class="sxs-lookup"><span data-stu-id="b39f8-144">**NX_AUTO_IP_PROBE_MIN**: The minimum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="b39f8-145">Som standard definieras värdet som 1.</span><span class="sxs-lookup"><span data-stu-id="b39f8-145">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="b39f8-146">**NX_AUTO_IP_PROBE_MAX**: det maximala antalet sekunder som ska förflyta mellan att skicka avsökningar.</span><span class="sxs-lookup"><span data-stu-id="b39f8-146">**NX_AUTO_IP_PROBE_MAX**: The maximum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="b39f8-147">Som standard definieras värdet som 2.</span><span class="sxs-lookup"><span data-stu-id="b39f8-147">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="b39f8-148">**NX_AUTO_IP_MAX_CONFLICTS**: antalet AutoIP-konflikter innan bearbetnings fördröjningar ökar.</span><span class="sxs-lookup"><span data-stu-id="b39f8-148">**NX_AUTO_IP_MAX_CONFLICTS**: The number of AutoIP conflicts before increasing processing delays.</span></span> <span data-ttu-id="b39f8-149">Som standard definieras värdet som 10.</span><span class="sxs-lookup"><span data-stu-id="b39f8-149">By default, this value is defined as 10.</span></span>
- <span data-ttu-id="b39f8-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: antalet sekunder som vänte tiden ska utsträckas när det totala antalet konflikter överskrids.</span><span class="sxs-lookup"><span data-stu-id="b39f8-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: The number of seconds to extend the wait period when the total number of conflicts is exceeded.</span></span> <span data-ttu-id="b39f8-151">Som standard definieras värdet som 60.</span><span class="sxs-lookup"><span data-stu-id="b39f8-151">By default, this value is defined as 60.</span></span>
- <span data-ttu-id="b39f8-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: hur många sekunder som ska förflyta innan meddelande skickas.</span><span class="sxs-lookup"><span data-stu-id="b39f8-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: The number of seconds to wait before sending announcement.</span></span> <span data-ttu-id="b39f8-153">Som standard definieras värdet som 2.</span><span class="sxs-lookup"><span data-stu-id="b39f8-153">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="b39f8-154">**NX_AUTO_IP_ANNOUNCE_NUM**: antalet ARP tillkännager att skicka.</span><span class="sxs-lookup"><span data-stu-id="b39f8-154">**NX_AUTO_IP_ANNOUNCE_NUM**: The number of ARP announces to send.</span></span> <span data-ttu-id="b39f8-155">Som standard definieras värdet som 2.</span><span class="sxs-lookup"><span data-stu-id="b39f8-155">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="b39f8-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: antalet sekunder som sändningen ska förflyta.</span><span class="sxs-lookup"><span data-stu-id="b39f8-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: The number of seconds to wait between sending announces.</span></span> <span data-ttu-id="b39f8-157">Som standard definieras värdet som 2.</span><span class="sxs-lookup"><span data-stu-id="b39f8-157">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="b39f8-158">**NX_AUTO_IP_DEFEND_INTERVAL**: antalet sekunder att vänta mellan försvar tillkännager.</span><span class="sxs-lookup"><span data-stu-id="b39f8-158">**NX_AUTO_IP_DEFEND_INTERVAL**: The number of seconds to wait between defense announces.</span></span> <span data-ttu-id="b39f8-159">Som standard definieras värdet som 10.</span><span class="sxs-lookup"><span data-stu-id="b39f8-159">By default, this value is defined as 10.</span></span>
