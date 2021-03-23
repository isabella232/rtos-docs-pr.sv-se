---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo BSD
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider-NetX Duo BSD-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 582661bc66c51341fc098de9ff7b6fa2a7d746de
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826154"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="a4fb8-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="a4fb8-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="a4fb8-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider-NetX Duo BSD-komponenten.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo BSD component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="a4fb8-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="a4fb8-105">Product Distribution</span></span>

<span data-ttu-id="a4fb8-106">Azure återställnings tider NetX Duo BSD kan hämtas från vår offentliga käll kods lagrings plats på [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) .</span><span class="sxs-lookup"><span data-stu-id="a4fb8-106">Azure RTOS NetX Duo BSD can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="a4fb8-107">Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="a4fb8-108">**nxd_bsd. h**: rubrik fil för netx Duo BSD</span><span class="sxs-lookup"><span data-stu-id="a4fb8-108">**nxd_bsd.h**: Header file for NetX Duo BSD</span></span>
- <span data-ttu-id="a4fb8-109">**nxd_bsd. c**: c-källfil för netx Duo BSD</span><span class="sxs-lookup"><span data-stu-id="a4fb8-109">**nxd_bsd.c**: C Source file for NetX Duo BSD</span></span>
- <span data-ttu-id="a4fb8-110">**nxd_bsd.pdf**: Användar handbok för netx Duo BSD</span><span class="sxs-lookup"><span data-stu-id="a4fb8-110">**nxd_bsd.pdf**: User Guide for NetX Duo BSD</span></span>

<span data-ttu-id="a4fb8-111">Demonstrations filer:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-111">Demo files:</span></span>

- <span data-ttu-id="a4fb8-112">**bsd_demo_udp. c**</span><span class="sxs-lookup"><span data-stu-id="a4fb8-112">**bsd_demo_udp.c**</span></span>
- <span data-ttu-id="a4fb8-113">**bsd_demo_tcp. c**</span><span class="sxs-lookup"><span data-stu-id="a4fb8-113">**bsd_demo_tcp.c**</span></span>
- <span data-ttu-id="a4fb8-114">**bsd_demo_raw. c**</span><span class="sxs-lookup"><span data-stu-id="a4fb8-114">**bsd_demo_raw.c**</span></span>

## <a name="netx-duo-bsd-installation"></a><span data-ttu-id="a4fb8-115">Installation av NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="a4fb8-115">NetX Duo BSD Installation</span></span>

<span data-ttu-id="a4fb8-116">För att kunna använda NetX Duo BSD bör hela distributionen som nämnts tidigare kopieras till samma katalog där NetX Duo är installerat.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-116">In order to use NetX Duo BSD the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="a4fb8-117">Om t. ex. NetX Duo är installerat i katalogen "*\threadx\arm7\green*", ska *nxd_bsd. h* -och *nxd_bsd. c* -filerna kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-117">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_bsd.h* and *nxd_bsd.c* files should be copied into this directory.</span></span>

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a><span data-ttu-id="a4fb8-118">Skapa ThreadX-och NetX Duo-komponenter i ett BSD-program</span><span class="sxs-lookup"><span data-stu-id="a4fb8-118">Building the ThreadX and NetX Duo components of a BSD Application</span></span>

### <a name="threadx"></a><span data-ttu-id="a4fb8-119">ThreadX</span><span class="sxs-lookup"><span data-stu-id="a4fb8-119">ThreadX</span></span>

<span data-ttu-id="a4fb8-120">ThreadX-biblioteket måste definiera `bsd_errno` i den lokala tråd lagringen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-120">The ThreadX library must define `bsd_errno` in the thread local storage.</span></span> <span data-ttu-id="a4fb8-121">Vi rekommenderar följande procedur:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-121">We recommend the following procedure:</span></span>

1. <span data-ttu-id="a4fb8-122">I *tx_port. h* anger du ett av TX_THREAD_EXTENSION-makron enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-122">In *tx_port.h*, set one of the TX_THREAD_EXTENSION macros as follows:</span></span>
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. <span data-ttu-id="a4fb8-123">Återskapa ThreadX-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-123">Rebuild the ThreadX library.</span></span>

> [!NOTE]
> <span data-ttu-id="a4fb8-124">Om TX_THREAD_EXTENSION_3 redan används, är användaren kostnads fri att använda något av de andra TX_THREAD_EXTENSION-makron.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-124">If TX_THREAD_EXTENSION_3 is already used, the user is free to use one of the other TX_THREAD_EXTENSION macros.</span></span>

### <a name="netx-duo"></a><span data-ttu-id="a4fb8-125">NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a4fb8-125">NetX Duo</span></span>

<span data-ttu-id="a4fb8-126">Innan du använder NetX Duo BSD-tjänster måste NetX Duo-biblioteket skapas med NX_ENABLE_EXTENDED_NOTIFY_SUPPORT definierat.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-126">Before using NetX Duo BSD Services, the NetX Duo library must be built with NX_ENABLE_EXTENDED_NOTIFY_SUPPORT defined.</span></span> <span data-ttu-id="a4fb8-127">Som standard är den inte definierad.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-127">By default it is not defined.</span></span> <span data-ttu-id="a4fb8-128">Om BSD RAW-socketarna ska användas måste NetX Duo-biblioteket skapas med NX_ENABLE_IP_RAW_PACKET_FILTER definierat.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-128">If the BSD raw sockets are to be used, the NetX Duo library must be built with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span>

## <a name="using-netx-duo-bsd"></a><span data-ttu-id="a4fb8-129">Använda NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="a4fb8-129">Using NetX Duo BSD</span></span>

<span data-ttu-id="a4fb8-130">Ett NetX Duo BSD-programprojekt måste innehålla *nxd_bsd. h* när det innehåller *tx_api. h* och *nx_api. h* för att kunna använda BSD-tjänster som anges senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-130">A NetX Duo BSD application project must include *nxd_bsd.h* after it includes *tx_api.h* and *nx_api.h* to be able to use BSD services specified later in this guide.</span></span> <span data-ttu-id="a4fb8-131">Programmet måste även innehålla *nxd_bsd. c* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-131">The application must also include *nxd_bsd.c* in the build process.</span></span> <span data-ttu-id="a4fb8-132">Den här filen måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-132">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="a4fb8-133">Detta är allt som krävs för att använda NetX Duo BSD.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-133">This is all that is required to use NetX Duo BSD.</span></span>

<span data-ttu-id="a4fb8-134">Om du vill använda NetX Duo BSD-tjänster måste programmet skapa en IP-instans, skapa en adresspool för BSD-lagret för att allokera paket från, allokera minnes utrymme för den interna BSD-trådens stack och ange prioriteten för den interna BSD-tråden.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-134">To utilize NetX Duo BSD services, the application must create an IP instance, create a packet pool for the BSD layer to allocate packets from, allocate memory space for the internal BSD thread stack, and specify the priority of the internal BSD thread.</span></span> <span data-ttu-id="a4fb8-135">BSD-lagret initieras genom att anropa *bsd_initialize* och skicka in parametrarna.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-135">The BSD layer is initialized by calling *bsd_initialize* and passing in the parameters.</span></span> <span data-ttu-id="a4fb8-136">Detta visas i "små exempel" senare i det här dokumentet, men prototypen visas nedan:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-136">This is demonstrated in the "Small Examples" later in this document but the prototype is shown below:</span></span>

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

<span data-ttu-id="a4fb8-137">Default_ip är den IP-instans som BSD-lagret arbetar med.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-137">The default_ip is the IP instance the BSD layer operates on.</span></span> <span data-ttu-id="a4fb8-138">Default_pool används av BSD-tjänsterna för att allokera paket från.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-138">The default_pool is used by the BSD services to allocate packets from.</span></span> <span data-ttu-id="a4fb8-139">Följande två parametrar: bsd_thread_stack_area, bsd_thread_stack_size definierar stackområdet som används av den interna BSD-tråden och den sista parametern, bsd_thread_priority, anger trådens prioritet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-139">The next two parameters: bsd_thread_stack_area, bsd_thread_stack_size defines the stack area used by the internal BSD thread, and the last parameter, bsd_thread_priority, sets the priority of the thread.</span></span>

## <a name="netx-duo-bsd-raw-socket-support"></a><span data-ttu-id="a4fb8-140">Stöd för NetX Duo BSD RAW socket</span><span class="sxs-lookup"><span data-stu-id="a4fb8-140">NetX Duo BSD Raw Socket Support</span></span>

<span data-ttu-id="a4fb8-141">NetX Duo BSD stöder också RAW-Sockets.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-141">NetX Duo BSD also supports raw sockets.</span></span> <span data-ttu-id="a4fb8-142">Om du vill använda RAW-socketar i NetX Duo BSD måste NetX Duo-biblioteket kompileras med NX_ENABLE_IP_RAW_PACKET_FILTER definierat.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-142">To use raw sockets in NetX Duo BSD, the NetX Duo library must be compiled with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span> <span data-ttu-id="a4fb8-143">Som standard är den inte definierad.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-143">By default it is not defined.</span></span> <span data-ttu-id="a4fb8-144">Programmet måste sedan aktivera rå socket-bearbetning för en tidigare skapad IP-instans genom att anropa *nx_ip_raw_packet_enable.*</span><span class="sxs-lookup"><span data-stu-id="a4fb8-144">The application must then enable raw socket processing for a previously created IP instance by calling *nx_ip_raw_packet_enable.*</span></span>

<span data-ttu-id="a4fb8-145">För att skapa en RAW-socket i NetX Duo BSD använder programmet socketen skapa tjänst- *socket* och anger protokoll familjen, typ av socket och protokoll:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-145">To create a raw socket in NetX Duo BSD, the application uses the socket create service *socket* and specifies the protocol family, socket type and protocol:</span></span>

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

<span data-ttu-id="a4fb8-146">protocolFamily är AF_INET för IPv4-Sockets eller AF_INET6 för IPv6-Sockets förutsatt att IPv6 är aktiverat på IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-146">protocolFamily is AF_INET for IPv4 sockets, or AF_INET6 for IPv6 sockets, assuming IPv6 is enabled on the IP instance.</span></span> <span data-ttu-id="a4fb8-147">Socket_type måste anges till SOCK_RAW.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-147">The socket_type must be set to SOCK_RAW.</span></span> <span data-ttu-id="a4fb8-148">protokollet är programspecifikt.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-148">protocol is application specific.</span></span>

<span data-ttu-id="a4fb8-149">Om du vill skicka och ta emot obearbetade paket samt stänga en RAW-socket använder programmet vanligt vis samma BSD-tjänster som för UDP, t. ex. *SendTo, recvfrom, väljer* och *soc_close*.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-149">To send and receive raw packets as well as close a raw socket, the application typically uses the same BSD services as for UDP e.g. *sendto, recvfrom, select* and *soc_close*.</span></span> <span data-ttu-id="a4fb8-150">RAW-Sockets stöder varken *Accept* -eller *Listener* BSD-tjänster.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-150">Raw sockets do not support either *accept* or *listen* BSD services.</span></span>

- <span data-ttu-id="a4fb8-151">Mottagna IPv4-rå data inkluderar som standard IPv4-huvudet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-151">By default, received IPv4 raw data includes the IPv4 header.</span></span>  <span data-ttu-id="a4fb8-152">Däremot inkluderar mottagna IPv6-rå data inte IPv6-sidhuvudet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-152">Conversely, received IPv6 raw data does not include the IPv6 header.</span></span>

- <span data-ttu-id="a4fb8-153">När du skickar antingen obehandlade IPv6-eller IPv4-paket, lägger BSD-skiktet som standard till IPv6-eller IPv4-sidhuvudet innan data skickas.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-153">By default, when sending either raw IPv6 or IPv4 packets, the BSD wrapper layer adds the IPv6 or IPv4 header before sending the data.</span></span>

<span data-ttu-id="a4fb8-154">NetX Duo BSD stöder ytterligare alternativ för RAW socket, inklusive IP_RAW_RX_NO_HEADER IP_HDRINCL och IP_RAW_IPV6_HDRINCL.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-154">NetX Duo BSD supports additional raw socket options, including IP_RAW_RX_NO_HEADER, IP_HDRINCL and IP_RAW_IPV6_HDRINCL.</span></span>

<span data-ttu-id="a4fb8-155">Om IP_RAW_RX_NO_HEADER har angetts tas IPv4-rubriken bort så att mottagna data inte innehåller IPv4-huvudet och den rapporterade meddelande längden inkluderar inte IPv4-huvudet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-155">If IP_RAW_RX_NO_HEADER is set, the IPv4 header is removed so that the received data does not contain the IPv4 header, and the reported message length does not include the IPv4 header.</span></span>  <span data-ttu-id="a4fb8-156">För IPv6-socketar inkluderar Receive socket Receive inte IPv6-sidhuvudet, som motsvarar IP_RAW_RX_NO_HEADER alternativ uppsättning.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-156">For IPv6 sockets, by default the raw socket receive does not include IPv6 header, equivalent to having the IP_RAW_RX_NO_HEADER option set.</span></span> <span data-ttu-id="a4fb8-157">Programmet kan använda *Setsockopt* -tjänsten för att ta bort alternativet IP_RAW_RX_NO_HEADER när alternativet IP_RAW_RX_NO_HEADER har rensats, skulle mottagna IPv6-rå data inkludera IPv6-huvudet och den rapporterade meddelande längden inkluderar IPv6-huvudet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-157">Application may use the *setsockopt* service to clear the IP_RAW_RX_NO_HEADER option, Once the IP_RAW_RX_NO_HEADER option is cleared, the received IPv6 raw data would include the IPv6 header, and the reported message length includes the IPv6 header.</span></span>

<span data-ttu-id="a4fb8-158">Det här alternativet har ingen påverkan på IPv4-eller IPv6-överförda data.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-158">This option has no effect on IPv4 or IPv6 transmitted data.</span></span>

<span data-ttu-id="a4fb8-159">Om IP_HDRINCL har angetts inkluderar programmet IPv4-sidhuvudet när data skickas.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-159">If IP_HDRINCL is set, the application includes the IPv4 header when sending data.</span></span>  <span data-ttu-id="a4fb8-160">Det här alternativet har ingen påverkan på IPv6-överföring och definieras inte som standard.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-160">This option has no effect on IPv6 transmission and is not defined by default.</span></span> <span data-ttu-id="a4fb8-161">Om IP_RAW_IPV6_HDRINCL har angetts inkluderar programmet IPv6-sidhuvudet när data skickas.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-161">If IP_RAW_IPV6_HDRINCL is set, the application includes the IPv6 header when sending data.</span></span>  <span data-ttu-id="a4fb8-162">Det här alternativet har ingen påverkan på IPv4-överföring och definieras inte som standard.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-162">This option has no effect on IPv4 transmission and is not defined by default.</span></span>

<span data-ttu-id="a4fb8-163">IP_HDRINCL och IP_RAW_IPV6_HDRINCL har ingen påverkan på IPv4-eller IPv6-mottagning.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-163">IP_HDRINCL and IP_RAW_IPV6_HDRINCL have no effect on IPv4 or IPv6 reception.</span></span>

> [!NOTE]
> <span data-ttu-id="a4fb8-164">BSD 4,3-socket-specifikationen anger att kerneln måste kopiera RAW-paketet till varje socket Receive-buffert.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-164">The BSD 4.3 Socket specification specifies that the kernel must copy the raw packet to each socket receive buffer.</span></span> <span data-ttu-id="a4fb8-165">Men i NetX Duo BSD, om flera Sockets har skapats med att dela samma protokoll, är beteendet odefinierat.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-165">However in NetX Duo BSD, if multiple sockets are created sharing the same protocol, the behavior is undefined.</span></span>

## <a name="netx-duo-bsd-raw-packet-support"></a><span data-ttu-id="a4fb8-166">Stöd för NetX Duo BSD RAW-paket</span><span class="sxs-lookup"><span data-stu-id="a4fb8-166">NetX Duo BSD Raw Packet Support</span></span>

<span data-ttu-id="a4fb8-167">Om du vill aktivera stöd för RAW-paket för PPPoE måste NetX Duo BSD-omslutningen skapas med NX_BSD_RAW_PPPOE_SUPPORT aktiverat.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-167">To enable the raw packet support for PPPoE, NetX Duo BSD wrapper needs to be built with NX_BSD_RAW_PPPOE_SUPPORT enabled.</span></span>

<span data-ttu-id="a4fb8-168">Följande kommando skapar en BSD-socket för att hantera PPPoE RAW-paket:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-168">The following command creates a BSD socket to handle PPPoE raw packets:</span></span>

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

<span data-ttu-id="a4fb8-169">Den aktuella BSD-implementeringen stöder endast två protokoll typer i AF_PACKET-serien</span><span class="sxs-lookup"><span data-stu-id="a4fb8-169">The current BSD implementation only supports two protocol types in AF_PACKET family</span></span>

- <span data-ttu-id="a4fb8-170">`ETHERTYPE_PPPOE_DISC`: PPPoE-identifierings paket.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-170">`ETHERTYPE_PPPOE_DISC`: PPPoE Discovery packets.</span></span> <span data-ttu-id="a4fb8-171">I MAC data-ramen har identifierings paketen Ethernet-ramtypen 0x8863.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-171">In the MAC data frame, the Discovery packets have the Ethernet frame type 0x8863.</span></span>

- <span data-ttu-id="a4fb8-172">`ETHERTYPE_PPPOE_SESS`: PPP-session paket.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-172">`ETHERTYPE_PPPOE_SESS`: PPP Session packets.</span></span> <span data-ttu-id="a4fb8-173">I rutan MAC-data har sessions-paketen Ethernet-ramtyp 0x8864.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-173">In the MAC data frame, the Session packets have the Ethernet frame type 0x8864.</span></span>

<span data-ttu-id="a4fb8-174">Strukturen `sockaddr_ll` används för att ange parametrar när du skickar eller tar emot PPPoE-ramar.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-174">The structure `sockaddr_ll` is used to specify parameters when sending or receiving PPPoE frames.</span></span>

<span data-ttu-id="a4fb8-175">`struct sockaddr_ll` deklareras som:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-175">`struct sockaddr_ll` is declared as:</span></span>

```c
struct sockaddr_ll
{
    USHORT  sll_family;     /* Must be AF_PACKET */
    USHORT  sll_protocol;   /* LL frame type */
    INT     sll_ifindex;    /* Interface Index. */
    USHORT  sll_hatype;     /* Header type */
    UCHAR   sll_pkttype;    /* Packet type */
    UCHAR   sll_halen;      /* Length of address */
    UCHAR   sll_addr[8];    /* Physical layer address */
};
```

> [!NOTE]
> <span data-ttu-id="a4fb8-176">Alla fält i strukturen används inte av `sendto()` eller `recvfrom()` .</span><span class="sxs-lookup"><span data-stu-id="a4fb8-176">Not every field in the structure is used by `sendto()` or `recvfrom()`.</span></span> <span data-ttu-id="a4fb8-177">Se beskrivningen nedan om hur du konfigurerar `sockaddr_ll` för att skicka och ta emot PPPoE-paket.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-177">See the description below on how to set up the `sockaddr_ll` for sending and receiving PPPoE packets.</span></span>

<span data-ttu-id="a4fb8-178">Socket som skapats i AF_PACKETs familjen kan användas för att skicka PPPoE-paket eller PPP-sessionsobjekt, oavsett vilket protokoll som anges.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-178">Socket created in the AF_PACKET family can be used to send either PPPoE Discovery packets or PPP session packets, regardless of the protocol specified.</span></span> <span data-ttu-id="a4fb8-179">När ett PPPoE-paket överförs måste programmet förbereda bufferten som innehåller korrekt formaterad PPPoE-ram, inklusive MAC-sidhuvuden (målets MAC-adress, käll-MAC-adress och ramtyp.) Buffertstorleken innehåller ett Ethernet-huvud på 14 byte.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-179">When transmitting a PPPoE packet, application must prepare the buffer that includes properly formatted PPPoE frame, including the MAC headers (Destination MAC address, source MAC address, and frame type.) The size of the buffer includes the 14-byte Ethernet header.</span></span>

<span data-ttu-id="a4fb8-180">`sockaddr_ll`Struct (struct) `sll_ifindex` används för att ange det fysiska gränssnitt som ska användas för att skicka det här paketet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-180">The `sockaddr_ll` struct, the `sll_ifindex` is used to indicate the physical interface to be used for sending this packet.</span></span> <span data-ttu-id="a4fb8-181">Resten av fälten i strukturen används inte.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-181">The rest of the fields in the structure are not used.</span></span> <span data-ttu-id="a4fb8-182">Värden som används i de oanvända fälten ignoreras av den interna BSD-processen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-182">Values set to the unused fields are ignored by the BSD internal process.</span></span>

<span data-ttu-id="a4fb8-183">Följande kodblock visar hur du skickar ett PPPoE-paket:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-183">The following code block illustrates how to transmit a PPPoE packet:</span></span>

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

<span data-ttu-id="a4fb8-184">Returvärdet anger antalet byte som skickats.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-184">The return value indicates the number of bytes transmitted.</span></span> <span data-ttu-id="a4fb8-185">Eftersom PPPoE-paketen är meddelandebaserade, i en lyckad överföring, matchar antalet skickade byte paketets storlek, inklusive Ethernet-huvudet på 14 byte.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-185">Since PPPoE packets are message-based, on a successful transmission, the number of bytes sent matches the size of the packet, including the 14-byte Ethernet header.</span></span>

<span data-ttu-id="a4fb8-186">PPPoE-paket kan tas emot med hjälp av `recvfrom()` .</span><span class="sxs-lookup"><span data-stu-id="a4fb8-186">PPPoE packets can be received using `recvfrom()`.</span></span> <span data-ttu-id="a4fb8-187">Receive buffer måste vara tillräckligt stor för att rymma meddelande om Ethernet MTU-storlek.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-187">The receive buffer must be big enough to accommodate message of Ethernet MTU size.</span></span> <span data-ttu-id="a4fb8-188">Det mottagna PPPoE-paketet innehåller 14 byte Ethernet-sidhuvud.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-188">The received PPPoE packet includes 14-byte Ethernet header.</span></span> <span data-ttu-id="a4fb8-189">Vid mottagning av PPPoE-paket kan PPPoE-identifierings paket endast tas emot av socket som skapats med protokollet `ETHERTYPE_PPPOE_DISC` .</span><span class="sxs-lookup"><span data-stu-id="a4fb8-189">On receiving PPPoE packets, PPPoE Discovery packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_DISC`.</span></span> <span data-ttu-id="a4fb8-190">På samma sätt kan bara PPP-sessionsobjekt tas emot av socket som skapats med protokollet `ETHERTYPE_PPPOE_SESS` .</span><span class="sxs-lookup"><span data-stu-id="a4fb8-190">Similarly, PPP session packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_SESS`.</span></span> <span data-ttu-id="a4fb8-191">Om flera Sockets skapas för samma protokoll typ, vidarebefordras inkommande PPPoE-paket till den socket som skapades först.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-191">If multiple sockets are created for the same protocol type, arriving PPPoE packets are forwarded to the socket created first.</span></span> <span data-ttu-id="a4fb8-192">Om den första socketen som skapas för protokollet stängs, används nästa socket i skapande ordningen för att ta emot dessa paket.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-192">If the first socket created for the protocol is closed, the next socket in the order of creation is used for receiving these packets.</span></span>

<span data-ttu-id="a4fb8-193">När ett PPPoE-paket tas emot är följande fält i `sockaddr_ll` strukturen giltiga:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-193">After a PPPoE packet is received, the following fields in the `sockaddr_ll` struct are valid:</span></span>
- <span data-ttu-id="a4fb8-194">**sll_family**: som anges av BSD Internal som ska AF_PACKET</span><span class="sxs-lookup"><span data-stu-id="a4fb8-194">**sll_family**: Set by the BSD internal to be AF_PACKET</span></span>
- <span data-ttu-id="a4fb8-195">**sll_ifindex**: anger gränssnittet som paketet tas emot från</span><span class="sxs-lookup"><span data-stu-id="a4fb8-195">**sll_ifindex**: Indicates the interface from which the packet is received</span></span>
- <span data-ttu-id="a4fb8-196">**sll_protocol**: Ange till den typ av paket som tas emot: `ETHERTYPE_PPPOE_DISC` eller `ETHERTYPE_PPPOE_SESS`</span><span class="sxs-lookup"><span data-stu-id="a4fb8-196">**sll_protocol**: Set to the type of packet received: `ETHERTYPE_PPPOE_DISC` or `ETHERTYPE_PPPOE_SESS`</span></span>

## <a name="eliminating-internal-bsd-thread"></a><span data-ttu-id="a4fb8-197">Tar bort intern BSD-tråd</span><span class="sxs-lookup"><span data-stu-id="a4fb8-197">Eliminating Internal BSD Thread</span></span>

<span data-ttu-id="a4fb8-198">Som standard använder BSD en intern tråd för att utföra en del bearbetning.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-198">By default, BSD utilizes an internal thread to perform some of its processing.</span></span> <span data-ttu-id="a4fb8-199">I system med stränga minnes begränsningar kan BSD skapas med NX_BSD_TIMEOUT_PROCESS_IN_TIMER som definierats, vilket eliminerar den interna BSD-tråden och använder i stället en intern timer för att utföra samma bearbetning.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-199">In systems with tight memory constraints, BSD can be built with NX_BSD_TIMEOUT_PROCESS_IN_TIMER defined, which eliminates the internal BSD thread and instead uses an internal timer to perform the same processing.</span></span> <span data-ttu-id="a4fb8-200">Detta eliminerar det minne som krävs för det interna BSD-blocket och stacken för tråd kontroll.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-200">This eliminates the memory required for the internal BSD thread control block and stack.</span></span> <span data-ttu-id="a4fb8-201">Övergripande timer-bearbetning ökar dock avsevärt och BSD-bearbetningen kan också köras med högre prioritet än vad som behövs.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-201">However, overall timer processing is significantly increased and the BSD processing may also execute at a higher priority than needed.</span></span>

<span data-ttu-id="a4fb8-202">Om du vill konfigurera BSD-Sockets så att de körs i ThreadX timer-kontexten definierar du NX_BSD_TIMEOUT_PROCESS_IN_TIMER i *nxd_bsd. h*.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-202">To configure BSD sockets to run in the ThreadX timer context, define NX_BSD_TIMEOUT_PROCESS_IN_TIMER in *nxd_bsd.h*.</span></span> <span data-ttu-id="a4fb8-203">Om BSD-lagret har kon figurer ATS för att köra BSD-uppgifter i timer-kontexten ignoreras följande tre parametrar i anropet till *bsd_initialize* och ska anges till null:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-203">If the BSD layer is configured to execute the BSD tasks in the timer context, in the call to *bsd_initialize*, the following three parameters are ignored, and should be set to NULL:</span></span>

- <span data-ttu-id="a4fb8-204">**bsd_thread_stack_area**</span><span class="sxs-lookup"><span data-stu-id="a4fb8-204">**bsd_thread_stack_area**</span></span>
- <span data-ttu-id="a4fb8-205">**bsd_thread_stack_size**</span><span class="sxs-lookup"><span data-stu-id="a4fb8-205">**bsd_thread_stack_size**</span></span>
- <span data-ttu-id="a4fb8-206">**bsd_thread_priority**</span><span class="sxs-lookup"><span data-stu-id="a4fb8-206">**bsd_thread_priority**</span></span>

## <a name="netx-duo-bsd-with-dns-support"></a><span data-ttu-id="a4fb8-207">NetX Duo BSD med DNS-stöd</span><span class="sxs-lookup"><span data-stu-id="a4fb8-207">NetX Duo BSD with DNS Support</span></span>

<span data-ttu-id="a4fb8-208">Om NX_BSD_ENABLE_DNS har definierats kan NetX Duo BSD skicka DNS-frågor för att hämta värdnamn eller värd-IP-information.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-208">If NX_BSD_ENABLE_DNS is defined, NetX Duo BSD can send DNS queries to obtain hostname or host IP information.</span></span> <span data-ttu-id="a4fb8-209">Den här funktionen kräver att en NetX DNS-klient skapas tidigare med hjälp av tjänsten *nx_dns_create* .</span><span class="sxs-lookup"><span data-stu-id="a4fb8-209">This feature requires a NetX DNS Client to be previously created using the *nx_dns_create* service.</span></span> <span data-ttu-id="a4fb8-210">En eller flera kända DNS-Server-IP-adresser måste registreras med DNS-instansen med hjälp av tjänsten *nx_dns_server_add* för att lägga till IPv4-serveradresser eller använda tjänsten *nxd_dns_server_add* för att lägga till IPv4-eller IPv6-serveradresser.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-210">One or more known DNS server IP addresses must be registered with the DNS instance using the *nx_dns_server_add* service for adding IPv4 server addresses, or using the *nxd_dns_server_add* service for adding either IPv4 or IPv6 server addresses.</span></span>

<span data-ttu-id="a4fb8-211">DNS-tjänster och minnesallokering används av *getaddrinfo* -och *getnameinfo* -tjänster:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-211">DNS services and memory allocation are used by *getaddrinfo* and *getnameinfo* services:</span></span>

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

<span data-ttu-id="a4fb8-212">När BSD-programmet anropar *getaddrinfo* med ett värdnamn anropar netx BSD vilken som helst av tjänsterna nedan för att hämta IP-adressen:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-212">When the BSD application calls *getaddrinfo* with a hostname, NetX BSD will call any of the below services to obtain the IP address:</span></span>

- <span data-ttu-id="a4fb8-213">**nx_dns_ipv4_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="a4fb8-213">**nx_dns_ipv4_address_by_name_get**</span></span>
- <span data-ttu-id="a4fb8-214">**nxd_dns_ipv6_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="a4fb8-214">**nxd_dns_ipv6_address_by_name_get**</span></span>
- <span data-ttu-id="a4fb8-215">**nx_dns_cname_get**</span><span class="sxs-lookup"><span data-stu-id="a4fb8-215">**nx_dns_cname_get**</span></span>

<span data-ttu-id="a4fb8-216">För *nx_dns_ipv4_address_by_name_get* och *NXD_DNS_IPV6_ADDRESS_BY_NAME_GET* använder NetX BSD ipv4_addr_buffer och ipv6_addr_buffer respektive minnes område.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-216">For *nx_dns_ipv4_address_by_name_get* and *nxd_dns_ipv6_address_by_name_get*, NetX BSD uses the ipv4_addr_buffer and ipv6_addr_buffer memory areas respectively.</span></span> <span data-ttu-id="a4fb8-217">Storleken på de här buffertarna definieras av (NX_BSD_IPV4_ADDR_PER_HOST \* 4) och (NX_BSD_IPV6_ADDR_PER_HOST \* 16).</span><span class="sxs-lookup"><span data-stu-id="a4fb8-217">The size of these buffers are defined by (NX_BSD_IPV4_ADDR_PER_HOST \* 4) and (NX_BSD_IPV6_ADDR_PER_HOST \* 16) respectively.</span></span>

<span data-ttu-id="a4fb8-218">För att returnera adress information från *getaddrinfo* använder netx BSD ThreadX block minnes tabell nx_bsd_addrinfo_pool_memory, vars minnes området definieras av en annan uppsättning konfigurerbara alternativ, NX_BSD_IPV4_ADDR_MAX_NUM och NX_BSD_IPV6_ADDR_MAX_NUM.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-218">For returning address information from *getaddrinfo*, NetX BSD uses the ThreadX block memory table nx_bsd_addrinfo_pool_memory, whose memory area is defined by another set of configurable options, NX_BSD_IPV4_ADDR_MAX_NUM and NX_BSD_IPV6_ADDR_MAX_NUM.</span></span>

<span data-ttu-id="a4fb8-219">Se **allmänna konfigurations alternativ** för mer information om konfigurations alternativen ovan.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-219">See **General Configuration Options** for more details on the above configuration options.</span></span>

<span data-ttu-id="a4fb8-220">Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats och värd indatatypen är ett kanoniskt namn, allokerar NetX Duo BSD dynamiskt minne från en tidigare skapad block pool _nx_bsd_cname_block_pool</span><span class="sxs-lookup"><span data-stu-id="a4fb8-220">Additionally, if NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, and the host input is a canonical name, NetX Duo BSD will allocate memory dynamically from a previously created block pool \`_nx_bsd_cname_block_pool</span></span>

> [!NOTE]
> <span data-ttu-id="a4fb8-221">Efter att ha anropat *getaddrinfo* är BSD-programmet ansvarigt för att släppa det minne som pekas på av res argumentet tillbaka till block tabellen med hjälp av *freeaddrinfo* -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-221">After calling *getaddrinfo* the BSD application is responsible for releasing the memory pointed to by the res argument back to the block table using the *freeaddrinfo* service.</span></span>

## <a name="netx-duo-bsd-limitations"></a><span data-ttu-id="a4fb8-222">Begränsningar för NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="a4fb8-222">NetX Duo BSD Limitations</span></span>

<span data-ttu-id="a4fb8-223">På grund av prestanda-och arkitektur problem har NetX Duo BSD inte stöd för alla BSD 4,3-socket-funktioner:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-223">Due to performance and architecture issues, NetX Duo BSD does not support all the BSD 4.3 socket features:</span></span>

<span data-ttu-id="a4fb8-224">Det finns inte stöd för INT *-flaggor för sändnings-, Recv-, SendTo-* och *recvfrom* -anrop.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-224">INT flags are not supported for *send, recv, sendto* and *recvfrom* calls.</span></span>

## <a name="general-configuration-options"></a><span data-ttu-id="a4fb8-225">Allmänna konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="a4fb8-225">General Configuration Options</span></span>

<span data-ttu-id="a4fb8-226">Alternativ som kan konfigureras i *nxd_bsd. h* gör att programmet kan finjustera netx Duo BSD-socketar för sina specifika program krav.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-226">User configurable options in *nxd_bsd.h* allow the application to fine tune NetX Duo BSD sockets for its particular application requirements.</span></span>

<span data-ttu-id="a4fb8-227">Följande är en lista över konfigurerbara alternativ som ställs in vid kompilering:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-227">The following is the list of configurable options that are set at compile time:</span></span>

- <span data-ttu-id="a4fb8-228">**NX_BSD_TCP_WINDOW**: används i uppmaningen att skapa TCP-socketar.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-228">**NX_BSD_TCP_WINDOW**: Used in TCP socket create calls.</span></span> <span data-ttu-id="a4fb8-229">64 KB är en typisk fönster storlek för 100 MB Ethernet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-229">64k is typical window size for 100Mb Ethernet.</span></span> <span data-ttu-id="a4fb8-230">Standardvärdet är 65535.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-230">The default value is 65535.</span></span>

- <span data-ttu-id="a4fb8-231">**NX_BSD_SOCKFD_START**: det här är det logiska indexet för start värde för BSD-Sockelns fil beskrivning.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-231">**NX_BSD_SOCKFD_START**: This is the logical index for the BSD socket file descriptor start value.</span></span> <span data-ttu-id="a4fb8-232">Som standard är det här alternativet 32.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-232">By default this option is 32.</span></span>

- <span data-ttu-id="a4fb8-233">**NX_BSD_MAX_SOCKETS**: anger det maximala antalet totalt antal tillgängliga socketar i BSD-lagret och måste vara en multipel av 32.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-233">**NX_BSD_MAX_SOCKETS**: Specifies the maximum number of total sockets available in the BSD layer and must be a multiple of 32.</span></span> <span data-ttu-id="a4fb8-234">Värdet är standard för 32.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-234">The value is defaulted to 32.</span></span>

- <span data-ttu-id="a4fb8-235">**NX_BSD_SOCKET_QUEUE_MAX**: anger det maximala antalet UDP-paket som lagras i kön för mottagnings socket.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-235">**NX_BSD_SOCKET_QUEUE_MAX**: Specifies the maximum number of UDP packets stored on the receive socket queue.</span></span> <span data-ttu-id="a4fb8-236">Värdet är standard 5.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-236">The value is defaulted to 5.</span></span>

- <span data-ttu-id="a4fb8-237">**NX_BSD_MAX_LISTEN_BACKLOG**: Detta anger storleken på lyssnings kön ("efter släpning") för BSD TCP-socketar.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-237">**NX_BSD_MAX_LISTEN_BACKLOG**: This specifies the size of the listen queue ('backlog') for BSD TCP sockets.</span></span> <span data-ttu-id="a4fb8-238">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-238">The default value is 5.</span></span>

- <span data-ttu-id="a4fb8-239">**NX_MICROSECOND_PER_CPU_TICK**: anger antalet mikrosekunder per Schemaläggarens timer-Tick.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-239">**NX_MICROSECOND_PER_CPU_TICK**: Specifies the number of microseconds per scheduler timer tick.</span></span>

- <span data-ttu-id="a4fb8-240">**NX_BSD_TIMEOUT**: anger tids gränsen i timer-Tick på netx Duo-interna anrop som krävs av BSD.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-240">**NX_BSD_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo internal calls required by BSD.</span></span> <span data-ttu-id="a4fb8-241">Standardvärdet är (20 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="a4fb8-241">The default value is (20 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="a4fb8-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: anger tids gränsen i timer-Tick på netx duo från kopplings anrop.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo disconnect call.</span></span> <span data-ttu-id="a4fb8-243">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-243">The default value is 1.</span></span>

- <span data-ttu-id="a4fb8-244">**NX_BSD_PRINT_ERRORS**: om det här alternativet anges returnerar fel status för en BSD-funktion ett rad nummer och en typ av fel, t. ex. NX_SOC_ERROR där felet uppstår.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-244">**NX_BSD_PRINT_ERRORS**: If set, the error status return of a BSD function returns a line number and type of error e.g. NX_SOC_ERROR where the error occurs.</span></span> <span data-ttu-id="a4fb8-245">Detta kräver att programutvecklaren definierar fel söknings resultatet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-245">This requires the application developer to define the debug output.</span></span> <span data-ttu-id="a4fb8-246">Standardinställningen är inaktive rad och inga fel söknings utdata har angetts i *nxd_bsd. h*.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-246">The default setting is disabled and no debug output is specified in *nxd_bsd.h*.</span></span>

- <span data-ttu-id="a4fb8-247">**NX_BSD_TIMER_RATE**: intervall efter vilken BSD periodiska timer-aktivitet körs.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-247">**NX_BSD_TIMER_RATE**: Interval after which BSD periodic timer task runs.</span></span> <span data-ttu-id="a4fb8-248">Standardvärdet är 1 sekund (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="a4fb8-248">The default value is 1 second (1 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="a4fb8-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: om det här alternativet är inställt kan BSD-timeout-processen köras i systemets timer-kontext.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: If set, this option allows the BSD timeout process to execute in the system timer context.</span></span> <span data-ttu-id="a4fb8-250">Standard beteendet är inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-250">The default behavior is disabled.</span></span> <span data-ttu-id="a4fb8-251">Den här funktionen beskrivs i detalj i kapitel 2 "installation och användning av NetX Duo BSD".</span><span class="sxs-lookup"><span data-stu-id="a4fb8-251">This feature is described in more detail in Chapter 2 "Installation and Use of NetX Duo BSD".</span></span>

- <span data-ttu-id="a4fb8-252">**NX_BSD_RAW_PPPOE_SUPPORT**: Aktivera stöd för PPPoE-rå paket.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-252">**NX_BSD_RAW_PPPOE_SUPPORT**: Enable PPPoE raw packet support.</span></span> <span data-ttu-id="a4fb8-253">Det här alternativet är inte aktiverat som standard.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-253">By default this option is not enabled.</span></span>

- <span data-ttu-id="a4fb8-254">**NX_BSD_ENABLE_DNS**: om det är aktiverat skickar netx Duo BSD en DNS-fråga för värdnamn eller värd-IP-adress.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-254">**NX_BSD_ENABLE_DNS**: If enabled, NetX Duo BSD will send a DNS query for a hostname or host IP address.</span></span> <span data-ttu-id="a4fb8-255">Kräver att en DNS-klient instans skapas och startas tidigare.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-255">Requires a DNS Client instance to be previously created and started.</span></span> <span data-ttu-id="a4fb8-256">Som standard är den inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-256">By default it is not enabled.</span></span>

- <span data-ttu-id="a4fb8-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: definierar storleken på tabellen RAW socket.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: Defines the size of the raw socket table.</span></span> <span data-ttu-id="a4fb8-258">Värdet måste vara en potens av två.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-258">The value must be a power of two.</span></span> <span data-ttu-id="a4fb8-259">NetX BSD skapar en matris med Sockets av typen NX_BSD_SOCKETS för att skicka och ta emot rå paket.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-259">NetX BSD creates an array of sockets of type NX_BSD_SOCKETS for sending and receiving raw packets.</span></span> <span data-ttu-id="a4fb8-260">NX_ENABLE_IP_RAW_PACKET_FILTER måste vara aktiverat.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-260">NX_ENABLE_IP_RAW_PACKET_FILTER must be enabled.</span></span> <span data-ttu-id="a4fb8-261">Som standard är den 32.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-261">By default it is 32.</span></span>

- <span data-ttu-id="a4fb8-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: det maximala antalet IPv4-adresser som returneras av *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: Maximum number of IPv4 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="a4fb8-263">Detta tillsammans med NX_BSD_IPV6_ADDR_MAX_NUM definierar storleken på NetX BSD block-poolen nx_bsd_addrinfo_block_pool för dynamiskt allokerat minne för att adressera informations lagringen i *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-263">This along with NX_BSD_IPV6_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span> <span data-ttu-id="a4fb8-264">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-264">The default value is 5.</span></span>

- <span data-ttu-id="a4fb8-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: det maximala antalet IPv6-adresser som returneras av *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: Maximum number of IPv6 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="a4fb8-266">Detta tillsammans med NX_BSD_IPV4_ADDR_MAX_NUM definierar storleken på NetX BSD block-poolen nx_bsd_addrinfo_block_pool för dynamiskt allokerat minne för att adressera informations lagringen i *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-266">This along with NX_BSD_IPV4_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span>

- <span data-ttu-id="a4fb8-267">**NX_BSD_IPV4_ADDR_PER_HOST**: definierar maximalt antal IPv4-adresser som lagras per DNS-fråga.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-267">**NX_BSD_IPV4_ADDR_PER_HOST**: Defines maximum IPv4 addresses stored per DNS query.</span></span> <span data-ttu-id="a4fb8-268">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-268">The default value is 5.</span></span>

- <span data-ttu-id="a4fb8-269">**NX_BSD_IPV6_ADDR_PER_HOST**: definierar maximalt antal IPv6-adresser som lagras per DNS-fråga.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-269">**NX_BSD_IPV6_ADDR_PER_HOST**: Defines maximum IPv6 addresses stored per DNS query.</span></span> <span data-ttu-id="a4fb8-270">Standardvärdet är 2.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-270">The default value is 2.</span></span>

## <a name="bsd-socket-options"></a><span data-ttu-id="a4fb8-271">BSD socket-alternativ</span><span class="sxs-lookup"><span data-stu-id="a4fb8-271">BSD Socket Options</span></span>

<span data-ttu-id="a4fb8-272">Följande lista med alternativ för NetX Duo BSD-socket kan aktive ras (eller inaktive RAS) vid körning per socket med hjälp av *Setsockopt* -tjänsten:</span><span class="sxs-lookup"><span data-stu-id="a4fb8-272">The following list of NetX Duo BSD socket options can be enabled (or disabled) at run time on a per socket basis using the *setsockopt* service:</span></span>

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

<span data-ttu-id="a4fb8-273">Det finns två olika inställningar för option_level.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-273">There are two different settings for option_level.</span></span>

<span data-ttu-id="a4fb8-274">Den första typen av ingångs alternativ för körning är SOL_SOCKET för alternativ för socketnivå.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-274">The first type of run time socket options is SOL_SOCKET for socket level options.</span></span> <span data-ttu-id="a4fb8-275">Om du vill aktivera ett alternativ för en socketnivå anropar du *Setsockopt* med option_level inställd på SOL_SOCKET och option_name anger det speciella alternativet t. ex. SO_BROADCAST *.*</span><span class="sxs-lookup"><span data-stu-id="a4fb8-275">To enable a socket level option, call *setsockopt* with option_level set to SOL_SOCKET and option_name set to the specific option e.g. SO_BROADCAST *.*</span></span> <span data-ttu-id="a4fb8-276">Om du vill hämta en alternativ inställning anropar du *getsockopt* för option_name med option_level återigen inställt på SOL_SOCKET.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-276">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to SOL_SOCKET.</span></span>

<span data-ttu-id="a4fb8-277">Listan över alternativ för körning av socket-nivå visas nedan.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-277">The list of run time socket level options is shown below.</span></span>

- <span data-ttu-id="a4fb8-278">**SO_BROADCAST**: om den här inställningen är aktive rad kan du skicka och ta emot broadcast-paket från netx Sockets.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-278">**SO_BROADCAST**:  If set, this enables sending and receiving broadcast packets from Netx sockets.</span></span> <span data-ttu-id="a4fb8-279">Detta är standard beteendet för NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-279">This is the default behavior for NetX Duo.</span></span> <span data-ttu-id="a4fb8-280">Alla Sockets har den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-280">All sockets have this capability.</span></span>

- <span data-ttu-id="a4fb8-281">**SO_ERROR**: används för att hämta socket-status för den tidigare socket-åtgärden för den angivna socketen med hjälp av *getsockopt* -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-281">**SO_ERROR**:  Used to obtain socket status on the previous socket operation of the specified socket, using the *getsockopt* service.</span></span> <span data-ttu-id="a4fb8-282">Alla Sockets har den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-282">All sockets have this capability.</span></span>

- <span data-ttu-id="a4fb8-283">**SO_KEEPALIVE**: om det här alternativet har angetts aktiverar detta TCP Keep Alive-funktionen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-283">**SO_KEEPALIVE**:  If set, this enables the TCP Keep Alive feature.</span></span> <span data-ttu-id="a4fb8-284">Detta kräver att NetX Duo-biblioteket skapas med NX_TCP_ENABLE_KEEPALIVE som definieras i *nx_user. h*.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-284">This requires the NetX Duo library to be built with NX_TCP_ENABLE_KEEPALIVE defined in *nx_user.h*.</span></span> <span data-ttu-id="a4fb8-285">Som standard är den här funktionen inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-285">By default this feature is disabled.</span></span>

- <span data-ttu-id="a4fb8-286">**SO_RCVTIMEO**: Detta anger vänte alternativet i sekunder för mottagning av paket på netx Duo BSD-socketar.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-286">**SO_RCVTIMEO**:  This sets the wait option in seconds for receiving packets on NetX Duo BSD sockets.</span></span> <span data-ttu-id="a4fb8-287">Standardvärdet är NX_WAIT_FOREVER (0xFFFFFFFF) eller, om icke-blockerande är aktiverat, NX_NO_WAIT (0x0).</span><span class="sxs-lookup"><span data-stu-id="a4fb8-287">The default value is the NX_WAIT_FOREVER (0xFFFFFFFF) or, if non-blocking is enabled, NX_NO_WAIT (0x0).</span></span>

- <span data-ttu-id="a4fb8-288">**SO_RCVBUF**: här anges fönster storleken för TCP-socketen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-288">**SO_RCVBUF**:  This sets the window size of the TCP socket.</span></span> <span data-ttu-id="a4fb8-289">Standardvärdet NX_BSD_TCP_WINDOW har angetts till 64 KB för BSD TCP-socketar.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-289">The default value, NX_BSD_TCP_WINDOW, is set to 64k for BSD TCP sockets.</span></span> <span data-ttu-id="a4fb8-290">Om du vill ställa in storleken över 65535 kräver att NetX Duo-biblioteket skapas med NX_TCP_ENABLE_WINDOW_SCALING definieras.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-290">To set the size over 65535 requires the NetX Duo library to be built with the NX_TCP_ENABLE_WINDOW_SCALING be defined.</span></span>

- <span data-ttu-id="a4fb8-291">**SO_REUSEADDR**: om den här inställningen är aktive rad kan flera Sockets mappas till en port.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-291">**SO_REUSEADDR**:  If set, this enables multiple sockets to be mapped to one port.</span></span> <span data-ttu-id="a4fb8-292">Den typiska användningen är för TCP-serverns socket.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-292">The typical usage is for the TCP Server socket.</span></span> <span data-ttu-id="a4fb8-293">Detta är standard beteendet för NetX Duo-platser.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-293">This is the default behavior of NetX Duo sockets.</span></span>

<span data-ttu-id="a4fb8-294">Den andra typen av alternativ för körning av socket är IP-alternativnivå.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-294">The second type of run time socket options is the IP option level.</span></span> <span data-ttu-id="a4fb8-295">Om du vill aktivera ett alternativ för IP-nivå anropar du *Setsockopt* med option_level inställd på IP_PROTO och option_name anger alternativet t. ex. IP_MULTICAST_TTL *.*</span><span class="sxs-lookup"><span data-stu-id="a4fb8-295">To enable an IP level option, call *setsockopt* with option_level set to IP_PROTO and option_name set to the option e.g. IP_MULTICAST_TTL *.*</span></span> <span data-ttu-id="a4fb8-296">Om du vill hämta en alternativ inställning anropar du *getsockopt* för option_name med option_level återigen inställt på IP_PROTO.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-296">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to IP_PROTO.</span></span>

<span data-ttu-id="a4fb8-297">Listan över alternativ för IP-nivå för körning visas nedan.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-297">The list of run time IP level options is shown below.</span></span>

- <span data-ttu-id="a4fb8-298">**IP_MULTICAST_TTL**: Detta anger TTL-tiden för UDP-socketar.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-298">**IP_MULTICAST_TTL**:  This sets the time to live for UDP sockets.</span></span> <span data-ttu-id="a4fb8-299">Standardvärdet är NX_IP_TIME_TO_LIVE (0x80) när socketen skapas.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-299">The default value is NX_IP_TIME_TO_LIVE (0x80) when the socket is created.</span></span> <span data-ttu-id="a4fb8-300">Det här värdet kan åsidosättas genom att anropa *Setsockopt* med alternativet socket.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-300">This value can be overridden by calling *setsockopt* with this socket option.</span></span>

- <span data-ttu-id="a4fb8-301">**IP_RAW_IPV6_HDRINCL**: om det här alternativet är inställt måste det anropande programmet lägga till ett IPv6-huvud och eventuellt program rubriker till data som skickas till RAW IPv6-Sockets som skapats av BSD.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-301">**IP_RAW_IPV6_HDRINCL**:  If this option is set, the calling application must append an IPv6 header and optionally application headers to data being transmitted on raw IPv6 sockets created by BSD.</span></span> <span data-ttu-id="a4fb8-302">Om du vill använda det här alternativet måste rå socket-bearbetning vara aktiverat för IP-aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-302">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="a4fb8-303">**IP_ADD_MEMBERSHIP**: om det här alternativet är aktiverat aktiverar det här alternativet BSD-socketen (gäller endast UDP-socketar) för att ansluta till den angivna IGMP-gruppen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-303">**IP_ADD_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to join the specified IGMP group.</span></span>

- <span data-ttu-id="a4fb8-304">**IP_DROP_MEMBERSHIP**: om det här alternativet är aktiverat aktiverar det här alternativet BSD-socketen (gäller endast UDP-socketar) för att lämna den angivna IGMP-gruppen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-304">**IP_DROP_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to leave the specified IGMP group.</span></span>

- <span data-ttu-id="a4fb8-305">**IP_HDRINCL**: om det här alternativet är inställt måste det anropande programmet lägga till IP-huvudet och eventuellt program huvuden till data som skickas på obehandlade IPv4-socketar som skapats i BSD.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-305">**IP_HDRINCL**:  If this option is set, the calling application must append the IP header and optionally application headers to data being transmitted on raw IPv4 sockets created in BSD.</span></span> <span data-ttu-id="a4fb8-306">Om du vill använda det här alternativet måste rå socket-bearbetning vara aktiverat för IP-aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-306">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="a4fb8-307">**IP_RAW_RX_NO_HEADER**: om alternativet är avmarkerat inkluderas IPv6-huvudet med mottagna data för RAW IPv6-Sockets som skapats i BSD.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-307">**IP_RAW_RX_NO_HEADER**:  If cleared, the IPv6 header is included with the received data for raw IPv6 sockets created in BSD.</span></span> <span data-ttu-id="a4fb8-308">IPv6-huvuden tas bort som standard i BSD RAW IPv6-socketar och paket längden inkluderar inte IPv6-huvudet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-308">IPv6 headers are removed by default in BSD raw IPv6 sockets, and the packet length does not include the IPv6 header.</span></span>

<span data-ttu-id="a4fb8-309">Om det här alternativet anges tas IPv4-sidhuvudet bort från mottagna data på BSD RAW-socketar av typen IPv4.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-309">If set, the IPv4 header is removed from received data on BSD raw sockets of type IPv4.</span></span> <span data-ttu-id="a4fb8-310">IPv4-huvuden ingår som standard i BSD RAW IPv4-socketar och paket längden inkluderar IPv4-huvudet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-310">IPv4 headers are included by default in BSD raw IPv4 sockets and packet length includes the IPv4 header.</span></span>

<span data-ttu-id="a4fb8-311">Det här alternativet har ingen påverkan på antingen IPv4-eller IPv6-överförings data.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-311">This option has no effect on either IPv4 or IPv6 transmission data.</span></span>

## <a name="small-ipv4-example"></a><span data-ttu-id="a4fb8-312">Exempel på små IPv4</span><span class="sxs-lookup"><span data-stu-id="a4fb8-312">Small IPv4 Example</span></span>

<span data-ttu-id="a4fb8-313">Ett exempel på hur du använder NetX Duo BSD-tjänster för IPv4-nätverk beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-313">An example of how to use NetX Duo BSD services for IPv4 networks is described below.</span></span> <span data-ttu-id="a4fb8-314">I det här exemplet tas include-filen *nxd_bsd. h* in på rad 8.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-314">In this example, the include file *nxd_bsd.h* is brought in at line 8.</span></span> <span data-ttu-id="a4fb8-315">Därefter skapas IP-instansen *bsd_ip* och packet pool *bsd_pool* som globala variabler på rad 20 och 21.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-315">Next, the IP instance *bsd_ip* and packet pool *bsd_pool* are created as global variables at line 20 and 21.</span></span> <span data-ttu-id="a4fb8-316">Observera att den här demon använder en ram-drivrutin (virtuellt nätverk)*, _nx_ram_network_driver*.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-316">Note that this demo uses a ram (virtual) network driver *, _nx_ram_network_driver*.</span></span> <span data-ttu-id="a4fb8-317">Klienten och servern kommer att dela samma IP-adress på en enskild IP-instans i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-317">The client and server will share the same IP address on single IP instance in this example.</span></span>

<span data-ttu-id="a4fb8-318">Klient-och Server trådarna skapas på raderna 62 och 68.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-318">The client and server threads are created on lines 62 and 68.</span></span> <span data-ttu-id="a4fb8-319">BSD-adresspoolen för överföring av paket skapas på rad 78 och används i skapa IP-instans på rad 87.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-319">The BSD packet pool for transmitting packets is created on line 78 and used in the IP instance creation on line 87.</span></span> <span data-ttu-id="a4fb8-320">Observera att IP-trådens aktivitet får prioritet 1 i *nx_ip_create* -anropet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-320">Note that the IP thread task is given priority 1 in the *nx_ip_create* call.</span></span> <span data-ttu-id="a4fb8-321">Den här tråden bör vara den högsta prioritets uppgiften som definierats i programmet för optimal NetX-prestanda.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-321">This thread should be the highest priority task defined in the program for optimal NetX performance.</span></span>

<span data-ttu-id="a4fb8-322">IP-instansen är aktive rad för ARP-och TCP-tjänster på raderna 88 och 110.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-322">The IP instance is enabled for ARP and TCP services on lines 88 and 110 respectively.</span></span> <span data-ttu-id="a4fb8-323">Det senaste kravet innan BSD-tjänster kan användas är att anropa *bsd_initialize* på rad 120 för att konfigurera alla data strukturer och netx-och ThreadX-resurser som krävs av BSD.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-323">The last requirement before BSD services can be used is to call *bsd_initialize* on line 120 to set up all data structures and NetX and ThreadX resources needed by BSD.</span></span>

<span data-ttu-id="a4fb8-324">Funktionen Server tråd post definieras härnäst.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-324">The server thread entry function is defined next.</span></span> <span data-ttu-id="a4fb8-325">BSD TCP-socketen skapas på rad 149.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-325">The BSD TCP socket is created on line 149.</span></span> <span data-ttu-id="a4fb8-326">Serverns IP-adress och Port har angetts på raderna 160-163.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-326">The server IP address and port are set on lines 160-163.</span></span> <span data-ttu-id="a4fb8-327">Observera användningen av värden för byte av nätverks byte *htonl* och *htons* som tillämpas på IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-327">Note the use of host to network byte order macros *htonl* and *htons* applied to the IP address and port.</span></span> <span data-ttu-id="a4fb8-328">Detta är i överensstämmelse med BSD socket-specifikationen att data för flera byte skickas till BSD-tjänsterna i nätverkets byte ordning.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-328">This is in compliance with BSD socket specification that multi byte data is submitted to the BSD services in network byte order.</span></span>

<span data-ttu-id="a4fb8-329">Sedan binds huvud serverns socket till porten med hjälp av *BIND* -tjänsten på rad 166.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-329">Next, the master server socket is bound to the port using the *bind* service on line 166.</span></span> <span data-ttu-id="a4fb8-330">Detta är lyssnings-socketen för TCP-begäranden med hjälp av *lyssnar* tjänsten på rad 180.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-330">This is the listening socket for TCP connection requests using the *listen* service on line 180.</span></span> <span data-ttu-id="a4fb8-331">Härifrån kan du *thread_server_entry*, loopar för att söka efter mottagnings händelser med hjälp av funktionen *Välj* samtal på rad 202.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-331">From here the server thread function, *thread_server_entry*, loops to check for receive events using the *select* call on line 202.</span></span> <span data-ttu-id="a4fb8-332">Om en Receive-händelse är en anslutningsbegäran, som bestäms genom att jämföra listan med Läs klara, så anropas *den på rad* 213.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-332">If a receive event is a connection request, which is determined by comparing the read ready list, it calls *accept* on line 213.</span></span> <span data-ttu-id="a4fb8-333">En underordnad server-socket tilldelas för att hantera anslutningsbegäran och läggas till i huvud listan över TCP-server-socketar som är anslutna till en klient på rad 223.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-333">A child server socket is assigned to handle the connection request and added to the master list of TCP server sockets connected to a Client on line 223.</span></span> <span data-ttu-id="a4fb8-334">Om det inte finns några nya anslutnings begär Anden, kontrollerar Server tråden alla anslutna Sockets för att ta emot händelser i for-loopen med början på rad 236.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-334">If there are no new connection requests, the server thread then checks all the currently connected sockets for receive events in the for loop starting on line 236.</span></span> <span data-ttu-id="a4fb8-335">När en Receive-händelse *väntar på anrop* , anropas *Skicka* och ta emot på denna socket tills inga data tas emot (anslutningen stängs på den andra sidan) och socketen stängs med hjälp av *soc_close* tjänsten på rad 277.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-335">When a receive event waiting is detected, it calls *send* and *recv* on that socket until no data is received (connection closed on the other side) and the socket is closed using the *soc_close* service on line 277.</span></span>

<span data-ttu-id="a4fb8-336">När Server tråden har ställts in skapar funktionen klient tråd post *thread_client_entry* en socket på rad 326 och ansluter med TCP-serverns socket med hjälp av *anslutnings* anropet på rad 337.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-336">After the server thread sets up, the Client thread entry function, *thread_client_entry,* creates a socket on line 326 and connects with the TCP server socket using the *connect* call on line 337.</span></span> <span data-ttu-id="a4fb8-337">Sedan loopar de för att skicka och ta emot paket med hjälp *av tjänsterna* *Skicka* och ta emot.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-337">It then loops to send and receive packets using the *send* and *recv* services respectively.</span></span> <span data-ttu-id="a4fb8-338">När inga fler data tas emot, stängs socketen på rad 398 med hjälp av tjänsten *soc_close* .</span><span class="sxs-lookup"><span data-stu-id="a4fb8-338">When no more data is received, it closes the socket on line 398 using the *soc_close* service.</span></span> <span data-ttu-id="a4fb8-339">Efter från kopplingen skapar funktionen klient tråd post en ny TCP-socket och gör en annan anslutningsbegäran i loopen igång på rad 321.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-339">After disconnection, the client thread entry function creates a new TCP socket and makes another connection request in the while loop started on line 321.</span></span>

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection, sending,
and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQR
    STUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */

ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */

VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */
int     main()
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

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool", 128,
                                pointer, 16384);

    pointer = pointer + 16384;
    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                    0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                    pointer, 2048, 1);
                    pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable ARP \n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize (&bsd_ip, &bsd_pool,pointer, 2048, 2);
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT       status, sock, sock_tcp_server;
ULONG     actual_status;
INT       Clientlen;
INT       i;
UINT      is_set = NX_FALSE;
struct    sockaddr_in serverAddr;
struct    sockaddr_in ClientAddr;

    tx_thread_sleep(100);

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
        &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("Error on Server socket %d create \n", sock_tcp_server);
        return;
    }

    printf("Server socket %d created\n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    serverAddr.sin_port = htons(SERVER_PORT);

    /* Bind this server socket */
    status = bind (sock_tcp_server, (struct sockaddr *) &serverAddr,
                sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error on Server Socket %d Bind \n", sock_tcp_server);
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen (sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error on Server Socket %d Listen\n", sock_tcp_server);
        return;
    }
    else
        printf("Server socket %d listen complete\n", sock_tcp_server);

    /* All set to accept client connections */

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ((status == 0xFFFFFFFF) || (status == 0))
        {

            printf("Error with select. Status 0x%x\n", status);

            continue;
        }

        /* Check for a connection request. */
        is_set = FD_ISSET(sock_tcp_server, &read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,(struct sockaddr*)&ClientAddr,
                        &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i , &master_list)) &&
                (FD_ISSET(i , &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server received no data from Client on
                            socket %d)\n", i);
                        break;
                    }
                    else if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server receiving data from Client on
                            socket %d\n", i);
                        break;
                    }
                    if(status == SERVER_RCV_BUFFER_SIZE) status--;
                    Server_Rcv_Buffer[status] = 0;
                    printf("Server socket %d received %d bytes: %s\n ",
                            i, (ULONG)status, Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                        Client\n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                        Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != NX_SOC_ERROR)
                {
                    printf("Server socket %d closed \n", i);
                }
                else
                {
                    printf("Error on closing Server socket %d \n", i);
                }
            }
        }

    /* Loop back to check any next client connection */
    }
}

CHAR     Client_Rcv_Buffer[100];

VOID     thread_client_entry(ULONG thread_input)
{

INT        status;
INT        sock_tcp_client, length;
struct     sockaddr_in echoServAddr;
struct     sockaddr_in localAddr; /

    /* Let the server side get set up. */
    tx_thread_sleep(200);

    /* Set local port for displaying IP address and port. */
    memset(&localAddr, 0, sizeof(localAddr));
    localAddr.sin_family = AF_INET;
    localAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    localAddr.sin_port = htons(CLIENT_PORT);

    /* Set server port and IP address which we need to connect. */
    memset(&echoServAddr, 0, sizeof(echoServAddr));
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    echoServAddr.sin_port = htons(SERVER_PORT);

    /* Now make client connections with the server. */
    while (1)
    {

        printf("\n");

        /* Create BSD TCP Socket */
        sock_tcp_client = socket( AF_INET, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n", sock_tcp_client);
            return;
        }

        printf("Client socket %d created\n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr,
                        sizeof(echoServAddr));

        /* Check for error. */
        if (status != OK)
        {
            printf("Error on Client socket %d connect\n", sock_tcp_client);
                    soc_close(sock_tcp_client);
            return;
        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr,
                            &length);

        printf("Client port = %lu , Client = 0x%x,",
            htonl(localAddr.sin_port), htonl(localAddr.sin_addr.s_addr));

        length = sizeof(struct sockaddr_in);

        status = getpeername( sock_tcp_client, (struct sockaddr *)
                            &echoServAddr, &length);

        printf("Remote port = %lu, Remote IP = 0x%x \n",
                htonl(echoServAddr.sin_port),
                htonl(echoServAddr.sin_addr.s_addr));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
            sock_tcp_client);

            status = send(sock_tcp_client, "Hello", (sizeof("Hello")), 0);

            if (status == ERROR)
            {
                printf("Error: Client Socket (%d) send \n", sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,100,0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    380 printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Nothing received by Client on socket %d\n",
                            sock_tcp_client);
                }

                break;
            }
            else
            {
                printf("Client socket %d received %d bytes: %s\n",
                        sock_tcp_client,
                        status, Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = soc_close(sock_tcp_client);

        if (status != ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```

## <a name="small-ipv6-example-system"></a><span data-ttu-id="a4fb8-340">Exempel system för små IPv6-system</span><span class="sxs-lookup"><span data-stu-id="a4fb8-340">Small IPv6 Example System</span></span>

<span data-ttu-id="a4fb8-341">Ett exempel på hur du använder NetX Duo BSD-tjänster för IPv6-nätverk beskrivs i programmet nedan.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-341">An example of how to use NetX Duo BSD services for IPv6 networks is described in the program below.</span></span> <span data-ttu-id="a4fb8-342">Det här exemplet påminner mycket om demonstrations programmet för IPv4 som tidigare beskrivits med några viktiga skillnader.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-342">This example is very similar to the IPv4 demo program previously described with a few important differences.</span></span>

<span data-ttu-id="a4fb8-343">Klient-och Server trådarna, BSD-adresspoolen, IP-instansen och BSD-Initieringen sker på samma sätt som för IPv4 BSD-socketar.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-343">The client and server threads, BSD packet pool, IP instance and BSD initialization happens as it does for IPv4 BSD sockets.</span></span>

<span data-ttu-id="a4fb8-344">I funktionen Server tråd inmatning definierar *thread_server_entry* en par IPv6-variabler som använder *sockaddr_in6* och *NXD_ADDRESS* data typer på raderna 145-148.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-344">In the server thread entry function, *thread_server_entry*, defines a couple IPv6 variables using *sockaddr_in6* and *NXD_ADDRESS* data types on lines 145-148.</span></span> <span data-ttu-id="a4fb8-345">Data typen NXD_ADDRESS kan faktiskt lagra både IPv4-och IPv6-adress typer.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-345">The NXD_ADDRESS data type can actually store both IPv4 and IPv6 address types.</span></span>

<span data-ttu-id="a4fb8-346">Sedan aktiverar Server tråden IPv6 och ICMPv6 på IP-instansen med hjälp av *nxd_ipv6_enable* och *nxd_icmpv6_enable* tjänst på rad 161 och 169.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-346">Next, the server thread enables IPv6 and ICMPv6 on the IP instance using the *nxd_ipv6_enable* and *nxd_icmpv6_enable* service respectively on line 161 and 169.</span></span> <span data-ttu-id="a4fb8-347">Sedan registreras lokala länkar och globala IP-adresser med IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-347">Next, the link local and global IP addresses are registered with the IP instance.</span></span> <span data-ttu-id="a4fb8-348">Detta görs med hjälp av *nxd_ipv6_address_set* -tjänsten på raderna 180 och 195.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-348">This is done using the *nxd_ipv6_address_set* service on lines 180 and 195.</span></span> <span data-ttu-id="a4fb8-349">Därefter är det tillräckligt länge för IP-trådens uppgift att slutföra det duplicerade adress identifierings protokollet och registrera dessa adresser som giltiga adresser på *tx_thread_sleep* -anropet på rad 201.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-349">It then sleeps long enough for the IP thread task to complete the Duplicate Address Detection protocol and register these addresses as valid addresses on the *tx_thread_sleep* call on line 201.</span></span>

<span data-ttu-id="a4fb8-350">Därefter skapas TCP-serverns socket med argumentet AF_INET6 indatamängds typ på rad 204.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-350">Next, the TCP server socket is created with the AF_INET6 socket type input argument on line 204.</span></span> <span data-ttu-id="a4fb8-351">Socket-IPv6-adressen och porten är inställda på raderna 216-221, om du ombeds att använda *htonl* -och *htons* -makron för att lägga till data i byte ordningen i nätverket för BSD socket Services.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-351">The socket IPv6 address and port are set on lines 216-221, again noting the use of *htonl* and *htons* macros to put data in network byte order for BSD socket services.</span></span> <span data-ttu-id="a4fb8-352">Härifrån är funktionen för Server tråd inmatning nästan identisk med IPv4-exemplet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-352">From here on, the server thread entry function is virtually identical to the IPv4 example.</span></span>

<span data-ttu-id="a4fb8-353">Funktionen klient tråd post, *thread_client_entry*, definieras härnäst.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-353">The client thread entry function, *thread_client_entry*, is defined next.</span></span> <span data-ttu-id="a4fb8-354">Observera att eftersom TCP-klienten i det här exemplet delar samma IP-instans och IPv6-adress som TCP-servern, behöver vi inte aktivera IPv6-eller ICMPv6-tjänster på IP-instansen igen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-354">Note that because the TCP client in this example shares the same IP instance and IPv6 address as the TCP server, we do not need to enable IPv6 or ICMPv6 services on the IP instance again.</span></span> <span data-ttu-id="a4fb8-355">Dessutom har IPv6-adressen redan registrerats med IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-355">Further, the IPv6 address is also already registered with the IP instance.</span></span> <span data-ttu-id="a4fb8-356">I stället väntar klient tråd posten bara på rad 368 för att servern ska kunna konfigureras.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-356">Instead, the client thread entry function simply waits on line 368 for the server to set up.</span></span> <span data-ttu-id="a4fb8-357">Server adressen och porten anges, med hjälp av värden till bytes för byte i nätverk på rad 387-392 och klienten kan ansluta till TCP-servern på rad 412.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-357">The server address and port are set, using the host to network byte order macros on lines 387-392, and then the Client can connect with the TCP server on line 412.</span></span> <span data-ttu-id="a4fb8-358">Observera att de lokala IP-adressens data typer på raderna 378-383 bara används för att demonstrera *getsockname* -och *getpeername* -tjänsterna på raderna 425 respektive 434.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-358">Note that the local IP address data types in lines 378-383 are used only to demonstrate the *getsockname* and *getpeername* services on lines 425 and 434 respectively.</span></span> <span data-ttu-id="a4fb8-359">Eftersom data kommer från nätverket kommer nätverket att vara värd för byte av byte-ordning som används i raderna 378-383.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-359">Because the data is coming from the network, the network to host byte order macros as used in lines 378-383.</span></span>

<span data-ttu-id="a4fb8-360">Nästa funktion i klient tråds funktionen anger en loop i vilken den skapar en TCP-socket, gör en TCP-anslutning och skickar och tar emot data med TCP-servern tills inga fler data tas emot i stort sett samma som IPv4-exemplet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-360">Next the client thread entry function enters a loop in which it creates a TCP socket, makes a TCP connection and sends and receives data with the TCP server until no more data is received virtually the same as the IPv4 example.</span></span> <span data-ttu-id="a4fb8-361">Den stänger sedan socketen på rad 483, pausar en kort stund och skapar en annan TCP-socket och begär en TCP-server anslutning.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-361">It then closes the socket on line 483, pauses briefly and creates another TCP socket and requests a TCP server connection.</span></span>

<span data-ttu-id="a4fb8-362">En viktig skillnad med IPv4-exemplet är att *socket* -anropen anger en IPv6-socket med argumentet AF_INET6 indataargumentet.</span><span class="sxs-lookup"><span data-stu-id="a4fb8-362">One important difference with the IPv4 example is the *socket* calls specify an IPv6 socket using the AF_INET6 input argument.</span></span> <span data-ttu-id="a4fb8-363">En annan viktig skillnad är att TCP client *Connect* -anropet använder *sockaddr_in6* datatyp och ett längd argument har angetts till storleken på data typen *sockaddr_in6* .</span><span class="sxs-lookup"><span data-stu-id="a4fb8-363">Another important difference is that the TCP Client *connect* call takes an *sockaddr_in6* data type and a length argument set to the size of the *sockaddr_in6* data type.</span></span>

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection,
disconnection, sending, and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */
ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */
VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int     main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool",
    128, pointer, 16384);

    pointer = pointer + 16384;

    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                        0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in enable ARP on BSD IP instance\n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 2);

    /* Check BSD initialize status. */
    if (status)
    {
        error_counter++;
        printf("Error in BSD initialize \n");
    }

    pointer = pointer + 2048;
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT             status, sock, sock_tcp_server;
ULONG           actual_status;
INT             Clientlen;
INT             i;
UINT            is_set = NX_FALSE;
NXD_ADDRESS     ip_address;
struct          sockaddr_in6 serverAddr;
struct          sockaddr_in6 ClientAddr;
UINT            iface_index, address_index;

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
            &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 */
    status = nxd_ipv6_enable(&bsd_ip);
    if((status != NX_SUCCESS) && (status != NX_ALREADY_ENABLED))
    {
        printf("Error with IPv6 enable 0x%x\n", status);
        return;
    }

    /* Enable ICMPv6 */
    status = nxd_icmp_enable(&bsd_ip);

    if(status)
    {
        printf("Error with ECMPv6 enable 0x%x\n", status);
        return;
    }

    /* Set the primary interface for our DNS IPv6 addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, NX_NULL, 10,
                                &address_index);

    if (status)
        return;

    /* Set ip_0 interface address. */
    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    ip_address.nxd_ip_address.v6[0] = htonl(0x20010db8);
    ip_address.nxd_ip_address.v6[1] = htonl(0x0000f101);
    ip_address.nxd_ip_address.v6[2] = 0;
    ip_address.nxd_ip_address.v6[3] = htonl(0x101);

    /* Set the host global IP address. We are assuming a 64
    bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, &ip_address, 64,
                                &address_index);

    if (status)
        return;

    /* Wait for IPv6 stack to finish DAD process. */
    tx_thread_sleep(400);

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET6, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("\nError: BSD TCP Server socket create \n");
        return;
    }

    printf("\nBSD TCP Server socket created %lu \n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    serverAddr.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    serverAddr.sin6_addr._S6_un._S6_u32[2] = 0x0;
    serverAddr.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    serverAddr.sin6_port = htons(SERVER_PORT);
    serverAddr.sin6_family = AF_INET6;

    /* Bind this server socket */
    status = bind(sock_tcp_server, (struct sockaddr *) &serverAddr,
                    sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error: Server Socket Bind \n");
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen(sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error: Server Socket Listen\n");
        return;
    }
    else
        printf("Server Listen complete\n");

    /* All set to accept client connections */
    printf("Now accepting client connections\n");

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ( (status == 0xFFFFFFFF) || (status == 0) )
        {
            printf("Error with select? Status 0x%x. Try again\n", status);

            continue;
        }

        /* Detected a connection request. */
        is_set = FD_ISSET(sock_tcp_server,&read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,
            (struct sockaddr*)&ClientAddr,
            &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {
                printf("New connection %d\n", sock);

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i, &master_list)) &&
                (FD_ISSET(i, &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server socket %d received no data from
                                Client)\n", i);

                        break;
                    }
                    else if (status == 0xFFFFFFFF)
                    {
                        printf("Error on Server socket %d receiving data from
                                Client\n", i);

                        break;
                    }

                    printf("Server socket %d received from Client %lu bytes:
                            %s\n ", i, (ULONG)status,
                            Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                                Client \n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                                Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != ERROR)
                {
                    printf("Server socket %d closing\n", i);
                }
                else
                {

                    printf("Error on Server socket %d closing\n", i);
                }
            }
        }

        /* Loop back to check any next client connection */
    }
}

#define     CLIENT_BUFFER_SIZE 100
CHAR        Client_Rcv_Buffer[CLIENT_BUFFER_SIZE];

VOID        thread_client_entry(ULONG thread_input)
{

INT         status;
INT         sock_tcp_client, length;
struct      sockaddr_in6 echoServAddr6;
struct      sockaddr_in6 localAddr6; address */

    /* Wait for the server side to get set up, including the DAD process. */
    tx_thread_sleep(500);

    /* ICMPv6 and IPv6 should already be enabled on the IP instance
    by the server thread entry function. */

    /* Further the IPv6 address is already established with the IP instance.
    so no need to wait for DAD completion. */

    /* Set local port and IP address (used only for getsockname call). */
    memset(&localAddr6, 0, sizeof(localAddr6));
    localAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    localAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    localAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    localAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    localAddr6.sin6_port = htons(CLIENT_PORT);
    localAddr6.sin6_family = AF_INET6;

    /* Set Server port and IP address to connect to the TCP server. */
    memset(&echoServAddr6, 0, sizeof(echoServAddr6));
    echoServAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    echoServAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    echoServAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    echoServAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    echoServAddr6.sin6_port = htons(SERVER_PORT);
    echoServAddr6.sin6_family = AF_INET6;

    /* Now make client connections with the server. */
    while (1)
    {
        printf("\n");

        /* Create BSD TCP Socket */

        sock_tcp_client = socket(AF_INET6, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n");
            return;
        }

        printf("Client socket %d created \n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr6,
                sizeof(echoServAddr6));

        /* Check for error. */
        if (status != NX_SOC_OK)
        {
            printf("Error on Client socket %d connect\n");
            soc_close(sock_tcp_client);
            return;

        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr6,
        &length);

        printf("Client port = %lu , Client = 0x%x 0x%x 0x%x 0x%x,",
                ntohs(localAddr6.sin6_port),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[3]));

        length = sizeof(struct sockaddr_in6);

        status = getpeername(sock_tcp_client, (struct sockaddr *)
                            &echoServAddr6, &length);

        printf("Remote port = %lu, Remote IP = 0x%x 0x%x 0x%x 0x%x \n",
                ntohs(echoServAddr6.sin6_port),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[3]));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
                sock_tcp_client);

            status = send(sock_tcp_client, "Hello", sizeof("Hello"), 0);

            if (status == NX_SOC_ERROR)
            {
                printf("Error on Client Socket (%d) send \n",
                        sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message: Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,
                        CLIENT_BUFFER_SIZE, 0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Client received no data on socket %d\n",
                            sock_tcp_client);
                }

            break;
            }
            else
            {
                printf("Client socket %d received %d bytes and this message:
                        %s\n", sock_tcp_client, status,
                        Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = oc_close(sock_tcp_client);

        if (status != NX_SOC_ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```
