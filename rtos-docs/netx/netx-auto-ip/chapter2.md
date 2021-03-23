---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX-AutoIP
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX AutoIP-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 269a3b4e9754fdc19e2cf1482d483fad2b841de9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825611"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-autoip"></a><span data-ttu-id="72321-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX-AutoIP</span><span class="sxs-lookup"><span data-stu-id="72321-103">Chapter 2 - Installation and use of Azure RTOS NetX AutoIP</span></span>

<span data-ttu-id="72321-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX AutoIP-komponenten.</span><span class="sxs-lookup"><span data-stu-id="72321-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX AutoIP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="72321-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="72321-105">Product Distribution</span></span>

<span data-ttu-id="72321-106">AutoIP för NetX finns på [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="72321-106">AutoIP for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="72321-107">Paketet innehåller tre källfiler, en inkludera filer och en PDF-fil som innehåller det här dokumentet, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="72321-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="72321-108">**nx_auto_ip. h**: rubrik fil för netx AutoIP</span><span class="sxs-lookup"><span data-stu-id="72321-108">**nx_auto_ip.h**: Header file for NetX AutoIP</span></span>
- <span data-ttu-id="72321-109">**nx_auto_ip. c**: c-källfil för netx AutoIP</span><span class="sxs-lookup"><span data-stu-id="72321-109">**nx_auto_ip.c**: C Source file for NetX AutoIP</span></span>
- <span data-ttu-id="72321-110">**demo_netx_auto_ip. c**: c-källfil för netx AutoIP-demo</span><span class="sxs-lookup"><span data-stu-id="72321-110">**demo_netx_auto_ip.c**: C Source file for NetX AutoIP Demo</span></span>
- <span data-ttu-id="72321-111">**nx_auto_ip.pdf**: PDF-Beskrivning av netx AutoIP</span><span class="sxs-lookup"><span data-stu-id="72321-111">**nx_auto_ip.pdf**: PDF description of NetX AutoIP</span></span>

## <a name="autoip-installation"></a><span data-ttu-id="72321-112">AutoIP-installation</span><span class="sxs-lookup"><span data-stu-id="72321-112">AutoIP Installation</span></span>

<span data-ttu-id="72321-113">För att kunna använda NetX-AutoIP bör hela distributionen som nämnts tidigare kopieras till samma katalog där NetX är installerad.</span><span class="sxs-lookup"><span data-stu-id="72321-113">In order to use NetX AutoIP, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="72321-114">Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*", ska *nx_auto_ip. h*-, *nx_auto_ip. c*-och *demo_netx_auto_ip. c* -filer kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="72321-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_auto_ip.h*, *nx_auto_ip.c*, and *demo_netx_auto_ip.c* files should be copied into this directory.</span></span>

## <a name="using-autoip"></a><span data-ttu-id="72321-115">Använda AutoIP</span><span class="sxs-lookup"><span data-stu-id="72321-115">Using AutoIP</span></span>

<span data-ttu-id="72321-116">Det är enkelt att använda NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="72321-116">Using NetX AutoIP is easy.</span></span> <span data-ttu-id="72321-117">I princip måste program koden innehålla *nx_auto_ip. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX och netx.</span><span class="sxs-lookup"><span data-stu-id="72321-117">Basically, the application code must include *nx_auto_ip.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="72321-118">När *nx_auto_ip. h* ingår kan program koden sedan göra AutoIP-funktions anropen senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="72321-118">Once *nx_auto_ip.h* is included, the application code is then able to make the AutoIP function calls specified later in this guide.</span></span> <span data-ttu-id="72321-119">Programmet måste även innehålla *nx_auto_ip. c* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="72321-119">The application must also include *nx_auto_ip.c* in the build process.</span></span> <span data-ttu-id="72321-120">De här filerna måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="72321-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="72321-121">Detta är allt som krävs för att använda NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="72321-121">This is all that is required to use NetX AutoIP.</span></span>

> [!NOTE]
> <span data-ttu-id="72321-122">Eftersom AutoIP använder NetX ARP-tjänster måste ARP vara aktiverat med det *nx_arp_enable* anropet innan du använder AutoIP.</span><span class="sxs-lookup"><span data-stu-id="72321-122">Since AutoIP utilizes NetX ARP services, ARP must be enabled with the *nx_arp_enable* call prior to using AutoIP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="72321-123">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="72321-123">Small Example System</span></span>

<span data-ttu-id="72321-124">Ett exempel på hur enkelt det är att använda NetX AutoIP beskrivs i bild 1,1, som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="72321-124">An example of how easy it is to use NetX AutoIP is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="72321-125">I det här exemplet tas AutoIP-filen *nx_auto_ip. h* in på rad 002.</span><span class="sxs-lookup"><span data-stu-id="72321-125">In this example, the AutoIP include file *nx_auto_ip.h* is brought in at line 002.</span></span> <span data-ttu-id="72321-126">Därefter skapas NetX AutoIP-instansen i "*tx_application_define*" på rad 090.</span><span class="sxs-lookup"><span data-stu-id="72321-126">Next, the NetX AutoIP instance is created in "*tx_application_define*" at line 090.</span></span> <span data-ttu-id="72321-127">Observera att NetX AutoIP Control Block (auto_ip_0) definierades tidigare som en global variabel på rad 015.</span><span class="sxs-lookup"><span data-stu-id="72321-127">Note that the NetX AutoIP control block "auto_ip_0" was defined previously as a global variable at line 015.</span></span> <span data-ttu-id="72321-128">När du har skapat en NetX-AutoIP startas den på rad 098.</span><span class="sxs-lookup"><span data-stu-id="72321-128">After successful creation, an NetX AutoIP is started at line 098.</span></span> <span data-ttu-id="72321-129">Funktionen för att ändra motringning till IP-adress startar på rad 105, som används för att hantera efterföljande konflikter eller möjlig DHCP-adress matchning.</span><span class="sxs-lookup"><span data-stu-id="72321-129">The IP address change callback function processing starts at line 105, which is used to handle subsequent conflicts or possible DHCP address resolution.</span></span>

> [!NOTE]
> <span data-ttu-id="72321-130">Exemplet nedan förutsätter att värd enheten är en enskild enhet.</span><span class="sxs-lookup"><span data-stu-id="72321-130">The example below assumes the host device is a single-homed device.</span></span> <span data-ttu-id="72321-131">För en multihomed-enhet kan värd programmet använda NetX AutoIP-tjänsten för *nx_auto_ip_interface_* ange att ett sekundärt nätverks gränssnitt ska avsökas för en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="72321-131">For a multihomed device, the host application can use the NetX AutoIP service *nx_auto_ip_interface_* set to specify a secondary network interface to probe for an IP address.</span></span> <span data-ttu-id="72321-132">I **användar handboken för netx** finns mer information om hur du konfigurerar multihomed-program.</span><span class="sxs-lookup"><span data-stu-id="72321-132">See the **NetX User Guide** for more details on setting up multihomed applications.</span></span> <span data-ttu-id="72321-133">Observera att värd programmet ska använda NetX API- *nx_status_ip_interface_check* för att verifiera att AutoIP har fått en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="72321-133">Note further that the host application should use the NetX API *nx_status_ip_interface_check* to verify AutoIP has obtained an IP address.</span></span>

## <a name="example-of-autoip-use-with-netx"></a><span data-ttu-id="72321-134">Exempel på AutoIP användning med NetX</span><span class="sxs-lookup"><span data-stu-id="72321-134">Example of AutoIP use with NetX</span></span>

```c
000 #include "tx_api.h"
001 #include "nx_api.h"
002 #include "nx_auto_ip.h"
003
004 #define         DEMO_STACK_SIZE         4096
005
006 /* Define the ThreadX and NetX object control blocks... */
007
008 TX_THREAD         thread_0;
009 NX_PACKET_POOL    pool_0;
010 NX_IP             ip_0;
011
012
013 /* Define the AUTO IP structures for the IP instance. */
014
015 NX_AUTO_IP         auto_ip_0;
016
017
018 /* Define the counters used in the demo application... */
019
020 ULONG             thread_0_counter;
021 ULONG             address_changes;
022 ULONG             error_counter;
023
024
025 /* Define thread prototypes. */
026
027 void     thread_0_entry(ULONG thread_input);
028 void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
029 void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
030
031
032 /* Define main entry point. */
033
034 int main()
035 {
036
037     /* Enter the ThreadX kernel. */
038     tx_kernel_enter();
039 }
040
041
042 /* Define what the initial system looks like. */
043
044 void     tx_application_define(void *first_unused_memory)
045 {
046
047 CHAR     *pointer;
048 UINT     status;
049
050
051     /* Setup the working pointer. */
052     pointer = (CHAR *) first_unused_memory;
053
054     /* Create the main thread. */
055     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
056                     pointer, DEMO_STACK_SIZE,
057                     16, 16, 1, TX_AUTO_START);
058
059     pointer = pointer + DEMO_STACK_SIZE;
060
061     /* Initialize the NetX system. */
062     nx_system_initialize();
063
064     /* Create a packet pool. */
065     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
066                                     pointer, 4096);
067                                     pointer = pointer + 4096;
068
069     if (status)
070         error_counter++;
071
072     /* Create an IP instance. */
073     status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
074                             0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
075                             pointer, 4096, 1);
076                             pointer = pointer + 4096;
077
078     if (status)
079         error_counter++;
080
081     /* Enable ARP and supply ARP cache memory for IP Instance 0. */
082     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
083     pointer = pointer + 1024;
084
085     /* Check ARP enable status. */
086     if (status)
087         error_counter++;
088
089     /* Create the AutoIP instance for IP Instance 0. */
090     status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
091     pointer = pointer + 4096;
092
093     /* Check AutoIP create status. */
094     if (status)
095         error_counter++;
096
097     /* Start AutoIP instances. */
098     status = nx_auto_ip_start(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);
099
100     /* Check AutoIP start status. */
101     if (status)
102         error_counter++;
103
104     /* Register an IP address change function for IP Instance 0. */
105     status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
106                                         (void *) &auto_ip_0);
107
108     /* Check IP address change notify status. */
109     if (status)
110         error_counter++;
111     }
112
113
114     /* Define the test thread. */
115
116     void thread_0_entry(ULONG thread_input)
117     {
118
119     UINT      status;
120     ULONG     actual_status;
121
122
123          /* Wait for IP address to be resolved. */
124         do
125         {
126
127             /* Call IP status check routine. */
128             status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
129                                         &actual_status, 10000);
130
131         } while (status != NX_SUCCESS);
132
133         /* Since the IP address is resolved at this point, the application
134         can now fully utilize NetX! */
135
136         while(1)
137         {
138
139
140
141             /* Increment thread 0's counter. */
142             thread_0_counter++;
143
144             /* Sleep... */
145             tx_thread_sleep(10);
146         }
147     }
148
149
150     void ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
151     {
152
153     ULONG         ip_address;
154     ULONG         network_mask;
155     NX_AUTO_IP    *auto_ip_ptr;
156
157
158     /* Setup pointer to auto IP instance. */
159     auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;
160
161     /* Pickup the current IP address. */
162     nx_ip_address_get(ip_ptr, &ip_address, &network_mask);
163
164     /* Determine if the IP address has changed back to zero. If so,
165     make sure the AutoIP instance is started. */
166     if (ip_address == 0)
167     {
168
169         /* Get the last AutoIP address for this node. */
170         nx_auto_ip_get_address(auto_ip_ptr, &ip_address);
171
172         /* Start this AutoIP instance. */
173         nx_auto_ip_start(auto_ip_ptr, ip_address);
174     }
175
176     /* Determine if IP address has transitioned to a non local IP address. */
177     else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
178     {
179
180         /* Stop the AutoIP processing. */
181         nx_auto_ip_stop(auto_ip_ptr);
182     }
183
184     /* Increment a counter. */
185     address_changes++;
186 }
```

## <a name="configuration-options"></a><span data-ttu-id="72321-135">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="72321-135">Configuration Options</span></span>

<span data-ttu-id="72321-136">Det finns flera konfigurations alternativ för att skapa NetX-AutoIP.</span><span class="sxs-lookup"><span data-stu-id="72321-136">There are several configuration options for building NetX AutoIP.</span></span> <span data-ttu-id="72321-137">Följande är en lista över alla alternativ, där var och en beskrivs i detalj:</span><span class="sxs-lookup"><span data-stu-id="72321-137">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="72321-138">**NX_DISABLE_ERROR_CHECKING**: det här alternativet tar bort den grundläggande fel kontrollen i AutoIP.</span><span class="sxs-lookup"><span data-stu-id="72321-138">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic AutoIP error checking.</span></span> <span data-ttu-id="72321-139">Den används vanligt vis när programmet har felsökts.</span><span class="sxs-lookup"><span data-stu-id="72321-139">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="72321-140">**NX_AUTO_IP_PROBE_WAIT**: antalet sekunder som ska förflyta innan den första avsökningen skickas.</span><span class="sxs-lookup"><span data-stu-id="72321-140">**NX_AUTO_IP_PROBE_WAIT**: The number of seconds to wait before sending first probe.</span></span> <span data-ttu-id="72321-141">Som standard definieras värdet som 1.</span><span class="sxs-lookup"><span data-stu-id="72321-141">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="72321-142">**NX_AUTO_IP_PROBE_NUM**: antalet ARP-avsökningar som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="72321-142">**NX_AUTO_IP_PROBE_NUM**: The number of ARP probes to send.</span></span> <span data-ttu-id="72321-143">Som standard definieras värdet som 3.</span><span class="sxs-lookup"><span data-stu-id="72321-143">By default, this value is defined as 3.</span></span>
- <span data-ttu-id="72321-144">**NX_AUTO_IP_PROBE_MIN**: det minsta antal sekunder som ska förflyta mellan att skicka avsökningar.</span><span class="sxs-lookup"><span data-stu-id="72321-144">**NX_AUTO_IP_PROBE_MIN**: The minimum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="72321-145">Som standard definieras värdet som 1.</span><span class="sxs-lookup"><span data-stu-id="72321-145">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="72321-146">**NX_AUTO_IP_PROBE_MAX**: det maximala antalet sekunder som ska förflyta mellan att skicka avsökningar.</span><span class="sxs-lookup"><span data-stu-id="72321-146">**NX_AUTO_IP_PROBE_MAX**: The maximum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="72321-147">Som standard definieras värdet som 2.</span><span class="sxs-lookup"><span data-stu-id="72321-147">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="72321-148">**NX_AUTO_IP_MAX_CONFLICTS**: antalet AutoIP-konflikter innan bearbetnings fördröjningar ökar.</span><span class="sxs-lookup"><span data-stu-id="72321-148">**NX_AUTO_IP_MAX_CONFLICTS**: The number of AutoIP conflicts before increasing processing delays.</span></span> <span data-ttu-id="72321-149">Som standard definieras värdet som 10.</span><span class="sxs-lookup"><span data-stu-id="72321-149">By default, this value is defined as 10.</span></span>
- <span data-ttu-id="72321-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: antalet sekunder som vänte tiden ska utsträckas när det totala antalet konflikter överskrids.</span><span class="sxs-lookup"><span data-stu-id="72321-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: The number of seconds to extend the wait period when the total number of conflicts is exceeded.</span></span> <span data-ttu-id="72321-151">Som standard definieras värdet som 60.</span><span class="sxs-lookup"><span data-stu-id="72321-151">By default, this value is defined as 60.</span></span>
- <span data-ttu-id="72321-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: hur många sekunder som ska förflyta innan meddelande skickas.</span><span class="sxs-lookup"><span data-stu-id="72321-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: The number of seconds to wait before sending announcement.</span></span> <span data-ttu-id="72321-153">Som standard definieras värdet som 2.</span><span class="sxs-lookup"><span data-stu-id="72321-153">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="72321-154">**NX_AUTO_IP_ANNOUNCE_NUM**: antalet ARP tillkännager att skicka.</span><span class="sxs-lookup"><span data-stu-id="72321-154">**NX_AUTO_IP_ANNOUNCE_NUM**: The number of ARP announces to send.</span></span> <span data-ttu-id="72321-155">Som standard definieras värdet som 2.</span><span class="sxs-lookup"><span data-stu-id="72321-155">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="72321-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: antalet sekunder som sändningen ska förflyta.</span><span class="sxs-lookup"><span data-stu-id="72321-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: The number of seconds to wait between sending announces.</span></span> <span data-ttu-id="72321-157">Som standard definieras värdet som 2.</span><span class="sxs-lookup"><span data-stu-id="72321-157">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="72321-158">**NX_AUTO_IP_DEFEND_INTERVAL**: antalet sekunder att vänta mellan försvar tillkännager.</span><span class="sxs-lookup"><span data-stu-id="72321-158">**NX_AUTO_IP_DEFEND_INTERVAL**: The number of seconds to wait between defense announces.</span></span> <span data-ttu-id="72321-159">Som standard definieras värdet som 10.</span><span class="sxs-lookup"><span data-stu-id="72321-159">By default, this value is defined as 10.</span></span>