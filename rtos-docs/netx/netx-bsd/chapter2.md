---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX BSD
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX BSD-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7539565ccd4956c5354be45000efab8318dc606c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826844"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-bsd"></a><span data-ttu-id="a9750-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX BSD</span><span class="sxs-lookup"><span data-stu-id="a9750-103">Chapter 2 - Installation and Use of Azure RTOS NetX BSD</span></span>

<span data-ttu-id="a9750-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX BSD-komponenten.</span><span class="sxs-lookup"><span data-stu-id="a9750-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX BSD component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="a9750-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="a9750-105">Product Distribution</span></span>

<span data-ttu-id="a9750-106">Azure återställnings tider NetX BSD kan hämtas från vår offentliga käll kods lagrings plats på [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) .</span><span class="sxs-lookup"><span data-stu-id="a9750-106">Azure RTOS NetX BSD can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="a9750-107">Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a9750-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="a9750-108">**nx_bsd. h**: rubrik fil för netx BSD</span><span class="sxs-lookup"><span data-stu-id="a9750-108">**nx_bsd.h**: Header file for NetX BSD</span></span>
- <span data-ttu-id="a9750-109">**nx_bsd. c**: c-källfil för netx BSD</span><span class="sxs-lookup"><span data-stu-id="a9750-109">**nx_bsd.c**: C Source file for NetX BSD</span></span>
- <span data-ttu-id="a9750-110">**nx_bsd.pdf**: Användar handbok för netx BSD</span><span class="sxs-lookup"><span data-stu-id="a9750-110">**nx_bsd.pdf**: User Guide for NetX BSD</span></span>

<span data-ttu-id="a9750-111">Demonstrations filer:</span><span class="sxs-lookup"><span data-stu-id="a9750-111">Demo files:</span></span>
- <span data-ttu-id="a9750-112">**bsd_demo_tcp. c**</span><span class="sxs-lookup"><span data-stu-id="a9750-112">**bsd_demo_tcp.c**</span></span>
- <span data-ttu-id="a9750-113">**bsd_demo_udp. c**</span><span class="sxs-lookup"><span data-stu-id="a9750-113">**bsd_demo_udp.c**</span></span>

## <a name="netx-bsd-installation"></a><span data-ttu-id="a9750-114">NetX BSD-installation</span><span class="sxs-lookup"><span data-stu-id="a9750-114">NetX BSD Installation</span></span>

<span data-ttu-id="a9750-115">För att kunna använda NetX BSD bör hela distributionen som nämnts tidigare kopieras till samma katalog där NetX har installerats.</span><span class="sxs-lookup"><span data-stu-id="a9750-115">In order to use NetX BSD the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="a9750-116">Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*", ska *nx_bsd. h* -och *nx_bsd. c* -filerna kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="a9750-116">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_bsd.h* and *nx_bsd.c* files should be copied into this directory.</span></span>

## <a name="building-the-threadx-and-netx-components-of-a-bsd-application"></a><span data-ttu-id="a9750-117">Skapa ThreadX-och NetX-komponenterna i ett BSD-program</span><span class="sxs-lookup"><span data-stu-id="a9750-117">Building the ThreadX and NetX components of a BSD Application</span></span>

### <a name="threadx"></a><span data-ttu-id="a9750-118">ThreadX</span><span class="sxs-lookup"><span data-stu-id="a9750-118">ThreadX</span></span>

<span data-ttu-id="a9750-119">ThreadX-biblioteket måste definiera *bsd_errno* i den lokala tråd lagringen.</span><span class="sxs-lookup"><span data-stu-id="a9750-119">The ThreadX library must define *bsd_errno* in the thread local storage.</span></span> <span data-ttu-id="a9750-120">Vi rekommenderar följande procedur:</span><span class="sxs-lookup"><span data-stu-id="a9750-120">We recommend the following procedure:</span></span>

1. <span data-ttu-id="a9750-121">I *tx_port. h* anger du ett av TX_THREAD_EXTENSION-makron enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a9750-121">In *tx_port.h*, set one of the TX_THREAD_EXTENSION macros as follows:</span></span>

  ```c
  #define TX_THREAD_EXTENSION_3     int bsd_errno
  ```

2. <span data-ttu-id="a9750-122">Återskapa ThreadX-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="a9750-122">Rebuild the ThreadX library.</span></span>

> [!NOTE]
> <span data-ttu-id="a9750-123">Om TX_THREAD_EXTENSION_3 redan används, är användaren kostnads fri att använda något av de andra TX_THREAD_EXTENSION-makron.</span><span class="sxs-lookup"><span data-stu-id="a9750-123">If TX_THREAD_EXTENSION_3 is already used, the user is free to use one of the other TX_THREAD_EXTENSION macros.</span></span>

### <a name="netx"></a><span data-ttu-id="a9750-124">NetX</span><span class="sxs-lookup"><span data-stu-id="a9750-124">NetX</span></span>

<span data-ttu-id="a9750-125">Innan du använder NetX BSD-tjänster måste NetX-biblioteket skapas med NX_ENABLE_EXTENDED_NOTIFY_SUPPORT definierat (t. ex. i *nx_user. h*).</span><span class="sxs-lookup"><span data-stu-id="a9750-125">Before using NetX BSD Services, the NetX library must be built with NX_ENABLE_EXTENDED_NOTIFY_SUPPORT defined (e.g. in *nx_user.h*).</span></span> <span data-ttu-id="a9750-126">Som standard är den inte definierad.</span><span class="sxs-lookup"><span data-stu-id="a9750-126">By default it is not defined.</span></span>

## <a name="using-netx-bsd"></a><span data-ttu-id="a9750-127">Använda NetX BSD</span><span class="sxs-lookup"><span data-stu-id="a9750-127">Using NetX BSD</span></span>

<span data-ttu-id="a9750-128">Det är enkelt att använda BSD för NetX.</span><span class="sxs-lookup"><span data-stu-id="a9750-128">Using BSD for NetX is easy.</span></span> <span data-ttu-id="a9750-129">I princip måste program koden innehålla *nx_bsd. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX respektive netx.</span><span class="sxs-lookup"><span data-stu-id="a9750-129">Basically, the application code must include *nx_bsd.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="a9750-130">När *nx_bsd. h* ingår kan program koden sedan använda BSD-tjänsterna som anges senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="a9750-130">Once *nx_bsd.h* is included, the application code is then able to use the BSD services specified later in this guide.</span></span> <span data-ttu-id="a9750-131">Programmet måste även innehålla *nx_bsd. c* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="a9750-131">The application must also include *nx_bsd.c* in the build process.</span></span> <span data-ttu-id="a9750-132">Den här filen måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="a9750-132">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="a9750-133">Detta är allt som krävs för att använda NetX BSD.</span><span class="sxs-lookup"><span data-stu-id="a9750-133">This is all that is required to use NetX BSD.</span></span>

<span data-ttu-id="a9750-134">Om du vill använda NetX BSD-tjänster måste programmet skapa en IP-instans, en modempool och initiera BSD-tjänster genom att anropa *bsd_initialize.*</span><span class="sxs-lookup"><span data-stu-id="a9750-134">To utilize NetX BSD services, the application must create an IP instance, a packet pool, and initialize BSD services by calling *bsd_initialize.*</span></span> <span data-ttu-id="a9750-135">Detta visas i avsnittet "litet exempel" senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="a9750-135">This is demonstrated in the "Small Example" section later in this guide.</span></span> <span data-ttu-id="a9750-136">Prototypen visas nedan:</span><span class="sxs-lookup"><span data-stu-id="a9750-136">The prototype is shown below:</span></span>

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                  CHAR *free_memory_ptr, ULONG bsd_thread_stack_size,
                  UINT bsd_thread_priority);
```

<span data-ttu-id="a9750-137">De sista tre parametrarna används för att skapa en tråd för att utföra periodiska uppgifter, till exempel söka efter TCP-händelser och definiera trådens stack utrymme.</span><span class="sxs-lookup"><span data-stu-id="a9750-137">The last three parameters are used for creating a thread for performing periodic tasks such as checking for TCP events and define the thread stack space.</span></span>

> [!NOTE]
> <span data-ttu-id="a9750-138">Till skillnad från BSD-Sockets, som fungerar i nätverk bye-ordning, fungerar NetX i värd processorns värddators ordning.</span><span class="sxs-lookup"><span data-stu-id="a9750-138">In contrast to BSD sockets, which work in network bye order, NetX works in the host byte order of the host processor.</span></span> <span data-ttu-id="a9750-139">För språkkompatibilitetsproblem har makron htons (), ntohs (), htonl (), ntohl () definierats, men ändrar inte argumentet som skickas.</span><span class="sxs-lookup"><span data-stu-id="a9750-139">For source compatibility reasons, the macros htons(), ntohs(), htonl(), ntohl() have been defined, but do not modify the argument passed.</span></span>

## <a name="netx-bsd-limitations"></a><span data-ttu-id="a9750-140">NetX BSD-begränsningar</span><span class="sxs-lookup"><span data-stu-id="a9750-140">NetX BSD Limitations</span></span>

<span data-ttu-id="a9750-141">På grund av problem med prestanda och arkitektur stöder NetX BSD inte alla BSD 4,3-socket-funktioner:</span><span class="sxs-lookup"><span data-stu-id="a9750-141">Due to performance and architecture issues, NetX BSD does not support all the BSD 4.3 socket features:</span></span>

<span data-ttu-id="a9750-142">Det finns inte stöd för INT *-flaggor för sändnings-, Recv-, SendTo-* och *recvfrom* -anrop.</span><span class="sxs-lookup"><span data-stu-id="a9750-142">INT flags are not supported for *send, recv, sendto* and *recvfrom* calls.</span></span>

## <a name="netx-bsd-with-dns-support"></a><span data-ttu-id="a9750-143">NetX BSD med DNS-stöd</span><span class="sxs-lookup"><span data-stu-id="a9750-143">NetX BSD with DNS Support</span></span>

<span data-ttu-id="a9750-144">Om NX_BSD_ENABLE_DNS har definierats kan NetX BSD skicka DNS-frågor för att hämta värdnamn eller värd-IP-information.</span><span class="sxs-lookup"><span data-stu-id="a9750-144">If NX_BSD_ENABLE_DNS is defined, NetX BSD can send DNS queries to obtain hostname or host IP information.</span></span> <span data-ttu-id="a9750-145">Den här funktionen kräver att en NetX DNS-klient skapas tidigare med hjälp av tjänsten *nx_dns_create* .</span><span class="sxs-lookup"><span data-stu-id="a9750-145">This feature requires a NetX DNS Client to be previously created using the *nx_dns_create* service.</span></span> <span data-ttu-id="a9750-146">En eller flera kända DNS-Server-IP-adresser måste registreras med DNS-instansen med hjälp av *nx_dns_server_add* för att lägga till Server adresser.</span><span class="sxs-lookup"><span data-stu-id="a9750-146">One or more known DNS server IP addresses must be registered with the DNS instance using the *nx_dns_server_add* for adding server addresses.</span></span>

<span data-ttu-id="a9750-147">DNS-tjänster och minnesallokering används av *getaddrinfo* -och *getnameinfo* -tjänster:</span><span class="sxs-lookup"><span data-stu-id="a9750-147">DNS services and memory allocation are used by *getaddrinfo* and *getnameinfo* services:</span></span>

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
              const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
              char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

<span data-ttu-id="a9750-148">När BSD-programmet anropar *getaddrinfo* med ett värdnamn anropar netx BSD vilken som helst av tjänsterna nedan för att hämta IP-adressen:</span><span class="sxs-lookup"><span data-stu-id="a9750-148">When the BSD application calls *getaddrinfo* with a hostname, NetX BSD will call any of the below services to obtain the IP address:</span></span>

- <span data-ttu-id="a9750-149">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="a9750-149">nx_dns_ipv4_address_by_name_get</span></span>
- <span data-ttu-id="a9750-150">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="a9750-150">nx_dns_cname_get</span></span>

<span data-ttu-id="a9750-151">För *nx_dns_ipv4_address_by_name_get* använder NetX BSD ipv4_addr_buffer minnes områden.</span><span class="sxs-lookup"><span data-stu-id="a9750-151">For *nx_dns_ipv4_address_by_name_get*, NetX BSD uses the ipv4_addr_buffer memory areas.</span></span> <span data-ttu-id="a9750-152">Storleken på de här buffertarna definieras av ( `NX_BSD_IPV4_ADDR_PER_HOST * 4` ).</span><span class="sxs-lookup"><span data-stu-id="a9750-152">The size of these buffers are defined by (`NX_BSD_IPV4_ADDR_PER_HOST * 4`).</span></span>

<span data-ttu-id="a9750-153">För att returnera adress information från *getaddrinfo* använder netx BSD ThreadX block minnes tabell *nx_bsd_addrinfo_pool_memory*, vars minnes yta definieras av en annan uppsättning konfigurerbara alternativ *NX_BSD_IPV4_ADDR_MAX_NUM*.</span><span class="sxs-lookup"><span data-stu-id="a9750-153">For returning address information from *getaddrinfo*, NetX BSD uses the ThreadX block memory table *nx_bsd_addrinfo_pool_memory*, whose memory area is defined by another set of configurable options, *NX_BSD_IPV4_ADDR_MAX_NUM*.</span></span>

<span data-ttu-id="a9750-154">Se **konfigurations alternativ** för mer information om konfigurations alternativen ovan.</span><span class="sxs-lookup"><span data-stu-id="a9750-154">See **Configuration Options** for more details on the above configuration options.</span></span>

<span data-ttu-id="a9750-155">Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats och värd indatatypen är ett kanoniskt namn, allokerar NetX BSD dynamiskt minne från en tidigare skapad block pool *_nx_bsd_cname_block_pool*</span><span class="sxs-lookup"><span data-stu-id="a9750-155">Additionally, if NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, and the host input is a canonical name, NetX BSD will allocate memory dynamically from a previously created block pool *_nx_bsd_cname_block_pool*</span></span>

> [!NOTE]
> <span data-ttu-id="a9750-156">Efter att ha anropat *getaddrinfo* är BSD-programmet ansvarigt för att släppa det minne som pekas på av res argumentet tillbaka till block tabellen med hjälp av *freeaddrinfo* -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a9750-156">After calling *getaddrinfo* the BSD application is responsible for releasing the memory pointed to by the res argument back to the block table using the *freeaddrinfo* service.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="a9750-157">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="a9750-157">Configuration Options</span></span>

<span data-ttu-id="a9750-158">Alternativ som kan konfigureras i *nx_bsd. h* gör det möjligt för programmet att finjustera netx BSD-socketar för sina specifika krav.</span><span class="sxs-lookup"><span data-stu-id="a9750-158">User configurable options in *nx_bsd.h* allow the application to fine tune NetX BSD sockets for its particular requirements.</span></span> <span data-ttu-id="a9750-159">Följande är en lista över dessa parametrar:</span><span class="sxs-lookup"><span data-stu-id="a9750-159">The following is a list of these parameters:</span></span>

- <span data-ttu-id="a9750-160">**NX_BSD_TCP_WINDOW**: används i uppmaningen att skapa TCP-socketar.</span><span class="sxs-lookup"><span data-stu-id="a9750-160">**NX_BSD_TCP_WINDOW**: Used in TCP socket create calls.</span></span> <span data-ttu-id="a9750-161">65535 är en typisk fönster storlek för 100 MB Ethernet.</span><span class="sxs-lookup"><span data-stu-id="a9750-161">65535 is a typical window size for 100Mb Ethernet.</span></span> <span data-ttu-id="a9750-162">Standardvärdet är 65535.</span><span class="sxs-lookup"><span data-stu-id="a9750-162">The default value is 65535.</span></span>
- <span data-ttu-id="a9750-163">**NX_BSD_SOCKFD_START** Det här är det logiska indexet för start värde för BSD-socketens fil beskrivning.</span><span class="sxs-lookup"><span data-stu-id="a9750-163">**NX_BSD_SOCKFD_START** This is the logical index for the BSD socket file descriptor start value.</span></span> <span data-ttu-id="a9750-164">Som standard är det här alternativet 32.</span><span class="sxs-lookup"><span data-stu-id="a9750-164">By default this option is 32.</span></span>
- <span data-ttu-id="a9750-165">**NX_BSD_MAX_SOCKETS** Anger det maximala antalet totalt antal tillgängliga socketar i BSD-skiktet och måste vara en multipel av 32. värdet är standard 32.</span><span class="sxs-lookup"><span data-stu-id="a9750-165">**NX_BSD_MAX_SOCKETS** Specifies the maximum number of total sockets available in the BSD layer and must be a multiple of 32.The value is defaulted to 32.</span></span>
- <span data-ttu-id="a9750-166">**NX_BSD_SOCKET_QUEUE_MAX** Anger det maximala antalet UDP-paket som lagras i kön för mottagnings socket.</span><span class="sxs-lookup"><span data-stu-id="a9750-166">**NX_BSD_SOCKET_QUEUE_MAX** Specifies the maximum number of UDP packets stored on the receive socket queue.</span></span> <span data-ttu-id="a9750-167">Värdet är standard 5.</span><span class="sxs-lookup"><span data-stu-id="a9750-167">The value is defaulted to 5.</span></span>
- <span data-ttu-id="a9750-168">**NX_BSD_MAX_LISTEN_BACKLOG** Detta anger storleken på lyssnings kön ("efter släpning") för BSD TCP-Sockets.</span><span class="sxs-lookup"><span data-stu-id="a9750-168">**NX_BSD_MAX_LISTEN_BACKLOG** This specifies the size of the listen queue ('backlog') for BSD TCP sockets.</span></span> <span data-ttu-id="a9750-169">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="a9750-169">The default value is 5.</span></span>
- <span data-ttu-id="a9750-170">**NX_MICROSECOND_PER_CPU_TICK** Anger antalet mikrosekunder per timer-avbrott</span><span class="sxs-lookup"><span data-stu-id="a9750-170">**NX_MICROSECOND_PER_CPU_TICK** Specifies the number of microseconds per timer interrupt</span></span>
- <span data-ttu-id="a9750-171">**NX_BSD_TIMEOUT** Anger tids gränsen i timer-Tick på NetX interna anrop som krävs av BSD.</span><span class="sxs-lookup"><span data-stu-id="a9750-171">**NX_BSD_TIMEOUT** Specifies the timeout in timer ticks on NetX internal calls required by BSD.</span></span> <span data-ttu-id="a9750-172">Standardvärdet är 20 \* NX_IP_PERIODIC_RATE.</span><span class="sxs-lookup"><span data-stu-id="a9750-172">The default value is 20\*NX_IP_PERIODIC_RATE.</span></span>
- <span data-ttu-id="a9750-173">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: anger tids gränsen i timer-Tick på netx från kopplings anrop.</span><span class="sxs-lookup"><span data-stu-id="a9750-173">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Specifies the timeout in timer ticks on NetX disconnect call.</span></span> <span data-ttu-id="a9750-174">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="a9750-174">The default value is 1.</span></span>
- <span data-ttu-id="a9750-175">**NX_BSD_PRINT_ERRORS** Om detta anges returnerar fel status för en BSD-funktion ett rad nummer och en typ av fel, t. ex. NX_SOC_ERROR där felet uppstår.</span><span class="sxs-lookup"><span data-stu-id="a9750-175">**NX_BSD_PRINT_ERRORS** If set, the error status return of a BSD function returns a line number and type of error e.g. NX_SOC_ERROR where the error occurs.</span></span> <span data-ttu-id="a9750-176">Detta kräver att programutvecklaren definierar fel söknings resultatet.</span><span class="sxs-lookup"><span data-stu-id="a9750-176">This requires the application developer to define the debug output.</span></span> <span data-ttu-id="a9750-177">Standardinställningen är inaktive rad och inga fel söknings utdata har angetts i *nx_bsd. h*</span><span class="sxs-lookup"><span data-stu-id="a9750-177">The default setting is disabled and no debug output is specified in *nx_bsd.h*</span></span>
- <span data-ttu-id="a9750-178">**NX_BSD_TIMER_RATE** Intervall efter vilken BSD-återkommande timer-aktivitet körs.</span><span class="sxs-lookup"><span data-stu-id="a9750-178">**NX_BSD_TIMER_RATE** Interval after which BSD periodic timer task runs.</span></span> <span data-ttu-id="a9750-179">Standardvärdet är 1 sekund (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="a9750-179">The default value is 1 second (1 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="a9750-180">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER** Om det här alternativet är inställt kan BSD-timeoutvärdet köras i systemets timer-kontext.</span><span class="sxs-lookup"><span data-stu-id="a9750-180">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER** If set, this option allows the BSD timeout process to execute in the system timer context.</span></span> <span data-ttu-id="a9750-181">Standard beteendet är inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="a9750-181">The default behavior is disabled.</span></span> <span data-ttu-id="a9750-182">Den här funktionen beskrivs i detalj i kapitel 2 "installation och användning av NetX BSD".</span><span class="sxs-lookup"><span data-stu-id="a9750-182">This feature is described in more detail in Chapter 2 "Installation and Use of NetX BSD".</span></span>
- <span data-ttu-id="a9750-183">**NX_BSD_ENABLE_DNS** Om aktive rad skickar NetX BSD en DNS-fråga för ett värdnamn eller en värd-IP-adress.</span><span class="sxs-lookup"><span data-stu-id="a9750-183">**NX_BSD_ENABLE_DNS** If enabled, NetX BSD will send a DNS query for a hostname or host IP address.</span></span> <span data-ttu-id="a9750-184">Kräver att en DNS-klient instans skapas och startas tidigare.</span><span class="sxs-lookup"><span data-stu-id="a9750-184">Requires a DNS Client instance to be previously created and started.</span></span> <span data-ttu-id="a9750-185">Som standard är den inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="a9750-185">By default it is not enabled.</span></span>
- <span data-ttu-id="a9750-186">**NX_BSD_IPV4_ADDR_MAX_NUM** Maximalt antal IPv4-adresser som returneras av *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="a9750-186">**NX_BSD_IPV4_ADDR_MAX_NUM** Maximum number of IPv4 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="a9750-187">Detta tillsammans med NX_BSD_IPV4_ADDR_MAX_NUM definierar storleken på NetX BSD block-poolen nx_bsd_addrinfo_block_pool för dynamiskt allokerat minne för att adressera informations lagringen i *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="a9750-187">This along with NX_BSD_IPV4_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span> <span data-ttu-id="a9750-188">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="a9750-188">The default value is 5.</span></span>
- <span data-ttu-id="a9750-189">**NX_BSD_IPV4_ADDR_PER_HOST**: definierar maximalt antal IPv4-adresser som lagras per DNS-fråga.</span><span class="sxs-lookup"><span data-stu-id="a9750-189">**NX_BSD_IPV4_ADDR_PER_HOST**: Defines maximum IPv4 addresses stored per DNS query.</span></span> <span data-ttu-id="a9750-190">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="a9750-190">The default value is 5.</span></span>

## <a name="bsd-socket-options"></a><span data-ttu-id="a9750-191">BSD socket-alternativ</span><span class="sxs-lookup"><span data-stu-id="a9750-191">BSD Socket Options</span></span>

<span data-ttu-id="a9750-192">Följande lista över NetX BSD socket-alternativ kan aktive ras (eller inaktive RAS) vid körning per socket med hjälp av *Setsockopt* -tjänsten:</span><span class="sxs-lookup"><span data-stu-id="a9750-192">The following list of NetX BSD socket options can be enabled (or disabled) at run time on a per socket basis using the *setsockopt* service:</span></span>

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, const
                void *option_value, INT option_length);
```

<span data-ttu-id="a9750-193">Det finns två olika inställningar för *option_level*.</span><span class="sxs-lookup"><span data-stu-id="a9750-193">There are two different settings for *option_level*.</span></span>

<span data-ttu-id="a9750-194">Den första typen av ingångs alternativ för körning är SOL_SOCKET för alternativ för socketnivå.</span><span class="sxs-lookup"><span data-stu-id="a9750-194">The first type of run time socket options is SOL_SOCKET for socket level options.</span></span> <span data-ttu-id="a9750-195">Om du vill aktivera ett alternativ för en socketnivå anropar du *Setsockopt* med option_level inställd på SOL_SOCKET och option_name anger det speciella alternativet t. ex. SO_BROADCAST.</span><span class="sxs-lookup"><span data-stu-id="a9750-195">To enable a socket level option, call *setsockopt* with option_level set to SOL_SOCKET and option_name set to the specific option e.g. SO_BROADCAST.</span></span> <span data-ttu-id="a9750-196">Om du vill hämta en alternativ inställning anropar du *getsockopt* för option_name med option_level återigen inställt på SOL_SOCKET.</span><span class="sxs-lookup"><span data-stu-id="a9750-196">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to SOL_SOCKET.</span></span>

<span data-ttu-id="a9750-197">Listan över alternativ för körning av socket-nivå visas nedan.</span><span class="sxs-lookup"><span data-stu-id="a9750-197">The list of run time socket level options is shown below.</span></span>

- <span data-ttu-id="a9750-198">**SO_BROADCAST**: om den här inställningen är aktive rad kan du skicka och ta emot broadcast-paket från netx Sockets.</span><span class="sxs-lookup"><span data-stu-id="a9750-198">**SO_BROADCAST**: If set, this enables sending and receiving broadcast packets from Netx sockets.</span></span> <span data-ttu-id="a9750-199">Detta är standard beteendet för NetX.</span><span class="sxs-lookup"><span data-stu-id="a9750-199">This is the default behavior for NetX.</span></span> <span data-ttu-id="a9750-200">Alla Sockets har den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="a9750-200">All sockets have this capability.</span></span>
- <span data-ttu-id="a9750-201">**SO_ERROR**: används för att hämta socket-status för den tidigare socket-åtgärden för den angivna socketen med hjälp av *getsockopt* -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a9750-201">**SO_ERROR**: Used to obtain socket status on the previous socket operation of the specified socket, using the *getsockopt* service.</span></span> <span data-ttu-id="a9750-202">Alla Sockets har den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="a9750-202">All sockets have this capability.</span></span>
- <span data-ttu-id="a9750-203">**SO_KEEPALIVE**: om det här alternativet har angetts aktiverar detta TCP Keep Alive-funktionen.</span><span class="sxs-lookup"><span data-stu-id="a9750-203">**SO_KEEPALIVE**: If set, this enables the TCP Keep Alive feature.</span></span> <span data-ttu-id="a9750-204">Detta kräver att NetX-biblioteket skapas med NX_TCP_ENABLE_KEEPALIVE som definieras i *nx_user. h*.</span><span class="sxs-lookup"><span data-stu-id="a9750-204">This requires the NetX library to be built with NX_TCP_ENABLE_KEEPALIVE defined in *nx_user.h*.</span></span> <span data-ttu-id="a9750-205">Som standard är den här funktionen inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="a9750-205">By default this feature is disabled.</span></span>
- <span data-ttu-id="a9750-206">**SO_RCVTIMEO**: den här inställningen anger vänte tiden i sekunder för mottagning av paket på netx BSD-platser.</span><span class="sxs-lookup"><span data-stu-id="a9750-206">**SO_RCVTIMEO**: This sets the wait option in seconds for receiving packets on NetX BSD sockets.</span></span> <span data-ttu-id="a9750-207">Standardvärdet är NX_WAIT_FOREVER (0xFFFFFFFF) eller, om icke-blockerande är aktiverat, NX_NO_WAIT (0x0).</span><span class="sxs-lookup"><span data-stu-id="a9750-207">The default value is the NX_WAIT_FOREVER (0xFFFFFFFF) or, if non-blocking is enabled, NX_NO_WAIT (0x0).</span></span>
- <span data-ttu-id="a9750-208">**SO_RCVBUF**: här anges fönster storleken för TCP-socketen.</span><span class="sxs-lookup"><span data-stu-id="a9750-208">**SO_RCVBUF**: This sets the window size of the TCP socket.</span></span> <span data-ttu-id="a9750-209">Standardvärdet NX_BSD_TCP_WINDOW har angetts till 64 KB för BSD TCP-socketar.</span><span class="sxs-lookup"><span data-stu-id="a9750-209">The default value, NX_BSD_TCP_WINDOW, is set to 64k for BSD TCP sockets.</span></span> <span data-ttu-id="a9750-210">Om du vill ange storleken över 65535 kräver att NetX-biblioteket skapas med NX_TCP_ENABLE_WINDOW_SCALING definieras.</span><span class="sxs-lookup"><span data-stu-id="a9750-210">To set the size over 65535 requires the NetX library to be built with the NX_TCP_ENABLE_WINDOW_SCALING be defined.</span></span>
- <span data-ttu-id="a9750-211">**SO_REUSEADDR**: om den här inställningen är aktive rad kan flera Sockets mappas till en port.</span><span class="sxs-lookup"><span data-stu-id="a9750-211">**SO_REUSEADDR**: If set, this enables multiple sockets to be mapped to one port.</span></span> <span data-ttu-id="a9750-212">Den typiska användningen är för TCP-serverns socket.</span><span class="sxs-lookup"><span data-stu-id="a9750-212">The typical usage is for the TCP Server socket.</span></span> <span data-ttu-id="a9750-213">Detta är standard beteendet för NetX-Sockets.</span><span class="sxs-lookup"><span data-stu-id="a9750-213">This is the default behavior of NetX sockets.</span></span>

<span data-ttu-id="a9750-214">Den andra typen av alternativ för körning av socket är IP-alternativnivå.</span><span class="sxs-lookup"><span data-stu-id="a9750-214">The second type of run time socket options is the IP option level.</span></span> <span data-ttu-id="a9750-215">Om du vill aktivera ett alternativ för IP-nivå anropar du *Setsockopt* med option_level inställd på IP_PROTO och option_name anger alternativet t. ex. IP_MULTICAST_TTL.</span><span class="sxs-lookup"><span data-stu-id="a9750-215">To enable an IP level option, call *setsockopt* with option_level set to IP_PROTO and option_name set to the option e.g. IP_MULTICAST_TTL.</span></span> <span data-ttu-id="a9750-216">Om du vill hämta en alternativ inställning anropar du *getsockopt* för option_name med option_level återigen inställt på IP_PROTO.</span><span class="sxs-lookup"><span data-stu-id="a9750-216">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to IP_PROTO.</span></span>

<span data-ttu-id="a9750-217">Listan över alternativ för IP-nivå för körning visas nedan.</span><span class="sxs-lookup"><span data-stu-id="a9750-217">The list of run time IP level options is shown below.</span></span>

- <span data-ttu-id="a9750-218">**IP_MULTICAST_TTL**: Detta anger TTL-tiden för UDP-socketar.</span><span class="sxs-lookup"><span data-stu-id="a9750-218">**IP_MULTICAST_TTL**: This sets the time to live for UDP sockets.</span></span> <span data-ttu-id="a9750-219">Standardvärdet är NX_IP_TIME_TO_LIVE (0x80) när socketen skapas.</span><span class="sxs-lookup"><span data-stu-id="a9750-219">The default value is NX_IP_TIME_TO_LIVE (0x80) when the socket is created.</span></span> <span data-ttu-id="a9750-220">Det här värdet kan åsidosättas genom att anropa *Setsockopt* med alternativet socket.</span><span class="sxs-lookup"><span data-stu-id="a9750-220">This value can be overridden by calling *setsockopt* with this socket option.</span></span>
- <span data-ttu-id="a9750-221">**IP_ADD_MEMBERSHIP**: om det här alternativet är aktiverat aktiverar det här alternativet BSD-socketen (gäller endast UDP-socketar) för att ansluta till den angivna IGMP-gruppen.</span><span class="sxs-lookup"><span data-stu-id="a9750-221">**IP_ADD_MEMBERSHIP**: If set, this options enables the BSD socket (applies only to UDP sockets) to join the specified IGMP group.</span></span>
- <span data-ttu-id="a9750-222">**IP_DROP_MEMBERSHIP**: om det här alternativet är aktiverat aktiverar det här alternativet BSD-socketen (gäller endast UDP-socketar) för att lämna den angivna IGMP-gruppen.</span><span class="sxs-lookup"><span data-stu-id="a9750-222">**IP_DROP_MEMBERSHIP**: If set, this options enables the BSD socket (applies only to UDP sockets) to leave the specified IGMP group.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="a9750-223">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="a9750-223">Small Example System</span></span>

<span data-ttu-id="a9750-224">Ett exempel på hur du använder NetX BSD visas i bild 1,0 nedan.</span><span class="sxs-lookup"><span data-stu-id="a9750-224">An example of how to use NetX BSD is shown in Figure 1.0 below.</span></span> <span data-ttu-id="a9750-225">I det här exemplet tas include-filen *nx_bsd. h* in på rad 7.</span><span class="sxs-lookup"><span data-stu-id="a9750-225">In this example, the include file *nx_bsd.h* is brought in at line 7.</span></span> <span data-ttu-id="a9750-226">Därefter skapas IP-instansen *bsd_ip* och packet pool *bsd_pool* som globala variabler på rad 20 och 21.</span><span class="sxs-lookup"><span data-stu-id="a9750-226">Next, the IP instance *bsd_ip* and packet pool *bsd_pool* are created as global variables at line 20 and 21.</span></span> <span data-ttu-id="a9750-227">Observera att den här demon använder en ram (virtuell) nätverks driv rutin (rad 41).</span><span class="sxs-lookup"><span data-stu-id="a9750-227">Note that this demo uses a ram (virtual) network driver (line 41).</span></span> <span data-ttu-id="a9750-228">Klienten och servern kommer att dela samma IP-adress på en enskild IP-instans i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="a9750-228">The client and server will share the same IP address on single IP instance in this example.</span></span>

<span data-ttu-id="a9750-229">Klient-och Server trådarna skapas på rad 303 och 309 i *tx_application_define* som konfigurerar programmet och definieras på rader 293-361.</span><span class="sxs-lookup"><span data-stu-id="a9750-229">The client and server threads are created on line 303 and 309 in *tx_application_define* which sets up the application and is defined on lines 293-361.</span></span> <span data-ttu-id="a9750-230">När IP-instansen har skapats på rad 327 aktive ras IP-instansen för TCP-tjänster på rad 350.</span><span class="sxs-lookup"><span data-stu-id="a9750-230">After IP instance successful creation on line 327, the IP instance is enabled for TCP services on line 350.</span></span> <span data-ttu-id="a9750-231">Det senaste kravet innan BSD-tjänster kan användas är att anropa *bsd_initialize* på rad 360 för att konfigurera alla data strukturer och netx och ThreadX resurser som krävs av BSD.</span><span class="sxs-lookup"><span data-stu-id="a9750-231">The last requirement before BSD services can be used is to call *bsd_initialize* on line 360 to set up all data structures and NetX, and ThreadX resources needed by BSD.</span></span>

<span data-ttu-id="a9750-232">I funktionen Server tråd inmatning *thread_1_entry,* som definieras på raderna 381-397, väntar programmet på att driv rutinen ska initiera netx med nätverks parametrar.</span><span class="sxs-lookup"><span data-stu-id="a9750-232">In the server thread entry function, *thread_1_entry,* which is defined on lines 381-397, the application waits for the driver to initialize NetX with network parameters.</span></span> <span data-ttu-id="a9750-233">När detta görs anropas *tcpServer,* som definieras på raderna 146-253, för att hantera den information som krävs för att konfigurera TCP-serverns socket.</span><span class="sxs-lookup"><span data-stu-id="a9750-233">Once this is done, it calls *tcpServer,* defined on lines 146-253, to handle the details of setting up the TCP server socket.</span></span>

<span data-ttu-id="a9750-234">*tcpServer* skapar huvudsocketen genom att anropa *socket* service på rad 159 och binder den till lyssnings-socketen med hjälp av *bindnings* anropet på rad 176.</span><span class="sxs-lookup"><span data-stu-id="a9750-234">*tcpServer* creates the master socket by calling the *socket* service on line 159 and binds it to the listening socket using the *bind* call on line 176.</span></span> <span data-ttu-id="a9750-235">Den konfigureras sedan för att lyssna efter anslutnings begär Anden på rad 191.</span><span class="sxs-lookup"><span data-stu-id="a9750-235">It is then configured for listening for connection requests on line 191.</span></span> <span data-ttu-id="a9750-236">Observera att huvud-socketen inte accepterar en anslutningsbegäran.</span><span class="sxs-lookup"><span data-stu-id="a9750-236">Note that the master socket does not accept a connection request.</span></span> <span data-ttu-id="a9750-237">Den körs i en kontinuerlig slinga som anropar *Välj* varje tidpunkt för att identifiera anslutnings begär Anden.</span><span class="sxs-lookup"><span data-stu-id="a9750-237">It runs in a continuous loop which calls *select* each time to detect connection requests.</span></span> <span data-ttu-id="a9750-238">En sekundär BSD-socket som valts från en matris med BSD-socketar tilldelas anslutningsbegäran när tjänsten *Accept* har anropats på rad 218.</span><span class="sxs-lookup"><span data-stu-id="a9750-238">A secondary BSD socket chosen from an array of BSD sockets is assigned the connection request after calling the *accept* service on line 218.</span></span>

<span data-ttu-id="a9750-239">På klient sidan ska klient tråds funktionen post, *thread_0_entry*, definieras på raderna 366-377, även vänta tills netx initieras av driv rutinen.</span><span class="sxs-lookup"><span data-stu-id="a9750-239">On the Client side, the client thread entry function, *thread_0_entry*, defined on lines 366-377, should also wait for NetX to be initialized by the driver.</span></span> <span data-ttu-id="a9750-240">Här väntar vi bara på att Server sidan ska göra det.</span><span class="sxs-lookup"><span data-stu-id="a9750-240">Here we just wait for the server side to do so.</span></span> <span data-ttu-id="a9750-241">Sedan anropas *tcpClient* som definierats på rad 54-142 för att hantera information om hur du konfigurerar TCP-klientens socket och begär en TCP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="a9750-241">It then calls *tcpClient* defined on line 54-142, to handle the details of setting up the TCP client socket and requesting a TCP connection.</span></span>

<span data-ttu-id="a9750-242">TCP-klientens socket skapas på rad 68.</span><span class="sxs-lookup"><span data-stu-id="a9750-242">The TCP client socket is created on line 68.</span></span> <span data-ttu-id="a9750-243">Socketen är kopplad till den angivna IP-adressen och försöker ansluta till TCP-servern genom att anropa *Connect* på rad 84.</span><span class="sxs-lookup"><span data-stu-id="a9750-243">The socket is bound to the specified IP address and attempts to connect to the TCP server by calling *connect* on line 84.</span></span> <span data-ttu-id="a9750-244">Nu är det dags att börja skicka och ta emot paket.</span><span class="sxs-lookup"><span data-stu-id="a9750-244">It is now ready to begin sending and receiving packets.</span></span>

```c
1 /*  This is a small demo of BSD Wrapper for the high-performance NetX TCP/IP stack.
2     This demo demonstrate TCP connection, disconnection, sending, and receiving using
3     ARP and a simulated Ethernet driver. */
4
5 #include     "tx_api.h"
6 #include     "nx_api.h"
7 #include     "nx_bsd.h"
8 #include     <string.h>
9 #include     <stdlib.h>
10
11 #define         DEMO_STACK_SIZE         (16*1024)
12
13
14 /* Define the ThreadX and NetX object control blocks... */
15
16 TX_THREAD       thread_0;
17 TX_THREAD       thread_1;
18
19
20 NX_PACKET_POOL  bsd_pool;
21 NX_IP           bsd_ip;
22
23
24 /* Define the counters used in the demo application... */
25
26 ULONG           error_counter;
27
28 /* Define fd_set for select call */
29 fd_set          master_list,read_ready,read_ready1;
30
31
32 /* Define thread prototypes. */
33
34 VOID            thread_0_entry(ULONG thread_input);
35 VOID            thread_1_entry(ULONG thread_input);
36
37 VOID            tcpClient(CHAR *msg0);
38 VOID            tcpServer(VOID);
39 INT             HandleClient(INT sock);
40
41 VOID            _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
42
43
44 /* Define main entry point. */
45
46 int main()
47 {
48
49     /* Enter the ThreadX kernel. */
50     tx_kernel_enter();
51 }
52
53
54 VOID tcpClient(CHAR *msg0)
55 {
56
57 INT     status,status1,send_counter;
58 INT     sock_tcp_1,length,length1;
59 struct  sockaddr_in echoServAddr;       /* Echo server address */
60 struct  sockaddr_in localAddr;          /* Local address */
61 struct  sockaddr_in remoteAddr;         /* Remote address */
62
63 UINT    echoServPort; /* Echo Server Port */
64 CHAR    rcvBuffer1[32]
65
66
67     /* Create BSD TCP Socket */
68     sock_tcp_1 = **socket**( PF_INET, SOCK_STREAM, IPPROTO_TCP);
69     if (sock_tcp_1 == -1)
70     {
71         printf("\nError: BSD TCP Client socket create \n");
72         return;
73     }
74
75     printf("\nBSD TCP Client socket created %lu \n", sock_tcp_1);
76     /* Fill destination port and IP address */
77     echoServPort = 12;
78     memset(&echoServAddr, 0, sizeof(echoServAddr));
79     echoServAddr.sin_family = PF_INET;
80     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
81     echoServAddr.sin_port = echoServPort;
82
83     /* Now connect this client the server */
84     status1 = connect(sock_tcp_1, (struct sockaddr *)&echoServAddr, sizeof(echoServAddr));
85     /* Check for error. */
86     if (status1 != OK)
87     {
88         printf("\nError: BSD TCP Client socket Connect, %d \n",sock_tcp_1);
89         status = soc_close(sock_tcp_1);
90         if (status != ERROR)
91             printf("\nConnect ERROR so BSD Client Socket Closed: %d\n",sock_tcp_1);
92         else
93             printf("\nError: BSD Client Socket close %d\n",sock_tcp_1);
94         return;
95     }
96     /* Get and print source and destination information */
97     printf("\nBSD TCP Client socket: %d connected \n", sock_tcp_1);
98
99     status = getsockname(sock_tcp_1, (struct sockaddr *)&localAddr, &length);
100    printf("Client port = %lu , Client = %lu,", 
            localAddr.sin_port, localAddr.sin_addr.s_addr);
101    status = getpeername( sock_tcp_1, (struct sockaddr *) &remoteAddr, &length1);
102    printf("Remote port = %lu, Remote IP = %lu \n", 
            remoteAddr.sin_port remoteAddr.sin_addr.s_addr);
103
104    send_counter = 1;
105
106    /* Now receive the echoed packet from the server */
107    while(1)
108    {
109        tx_thread_sleep(2);
110
111        printf("\nClient sock: %d Sending packet No: %d to
                server\n",sock_tcp_1,send_counter);
112        status = send(sock_tcp_1,msg0, sizeof(msg0), 0);
113        if (status == ERROR)
114            printf("Error: BSD Client Socket send %d\n",sock_tcp_1);
115        else
116        {
117            printf("\nMessage sent: %s\n",msg0);
118            send_counter++;
119        }
120
121        status = recv(sock_tcp_1, (VOID *)rcvBuffer1, 31,0);
122        if (status == 0)
123            break;
124
125        rcvBuffer1[status] = 0;
126
127        if (status != ERROR)
128            printf("\nBSD Client Socket: %d received %lu bytes: %s ", 
                        sock_tcp_1,(ULONG)status,rcvBuffer1);
129        else
130            printf("\nError: BSD Client Socket receive %d \n",sock_tcp_1);
131
132    }
133
134    /* close this client socket */
135    status = soc_close(sock_tcp_1);
136    if (status != ERROR)
137        printf("\nBSD Client Socket Closed %d\n",sock_tcp_1);
138    else
139        printf("\nError: BSD Client Socket close %d \n",sock_tcp_1);
140
141    /* End */
142 }
143
144
145
146 void tcpServer(void)
147 {
148
149 INT         status,status1,sock,sock_tcp_2,i;
150 struct      sockaddr_in echoServAddr; /* Echo server address */
151 struct      sockaddr_in ClientAddr;
152
153 INT         Clientlen;
154 UINT        echoServPort; /* Echo Server Port */
155
156 INT         maxfd;
157
158 /* Create BSD TCP Server Socket */
159     sock_tcp_2 = socket( PF_INET, SOCK_STREAM, IPPROTO_TCP);
160     if (sock_tcp_2 == -1)
161     {
162         printf("Error: BSD TCP Server socket create\n");
163         return;
164     }
165     else
166         printf("BSD TCP Server socket created \n");
167
168     /* Now fill server side information */
169     echoServPort = 12;
170     memset(&echoServAddr, 0, sizeof(echoServAddr));
171     echoServAddr.sin_family = PF_INET;
172     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
173     echoServAddr.sin_port = echoServPort;
174
175     /* Bind this server socket */
176         status = bind(sock_tcp_2, (struct sockaddr *) &echoServAddr, sizeof(echoServAddr));
177     if (status < 0)
178     {
179         printf("Error: BSD TCP Server Socket Bind \n");
180         return;
181     }
182     else
183         printf("BSD TCP Server Socket bound \n");
184
185     FD_ZERO(&master_list);
186     FD_ZERO(&read_ready);
187     FD_SET(sock_tcp_2,&master_list);
188     maxfd = sock_tcp_2;
189
190     /* Now listen for any client connections for this server socket */
191     status = listen(sock_tcp_2,5);
192     if (status < 0)
193     {
194         printf("Error: BSD TCP Server Socket Listen\n");
195         return;
196     }
197     else
198         printf("BSD TCP Server Socket Listen complete, ");
199
200     /* All set to accept client connections */
201     printf("Now accepting client connections\n");
202
203     /* Loop to create and establish server connections. */
204     while(1)
205     {
206
207         read_ready = master_list;
208         tx_thread_sleep(2); /* Allow some time to other threads too */
209         status = select(maxfd+1,&read_ready,0,0,0);
210         if (status == ERROR)
211         {
212             continue;
213         }
214
215         status = FD_ISSET(sock_tcp_2,&read_ready);
216         if(status)
217         {
218             sock = accept(sock_tcp_2,(struct sockaddr*)&ClientAddr, &Clientlen);
219
220             /* Add this new connection to our master list */
221             FD_SET(sock,&master_list);
222             if ( sock \maxfd)
223             {
224                 maxfd = sock;
225             }
226
227             continue;
228         }
229         for (i = 0; i < (maxfd+1); i++)
230         {
231             if (( i != sock_tcp_2) && (FD_ISSET(i,&master_list)) && 
                    (FD_ISSET(i,&read_ready)))
232             {
233                 status1 = HandleClient(i);
234                 if (status1 == 0)
235                 {
236                     status1 = soc_close(i);
237                     if (status1 == OK)
238                     {
239                         FD_CLR(i,&master_list);
240                         printf("\nBSD Server Socket:%d closed\n",i);
241                     }
242                     else
243                         printf("\nError:BSD Server Socket:%d close\n",i);
244                 }
245
246             }
247         }
248
249         /* Loop back to check any next client connection */
250
251     } /* While(1) ends */
252
253 }
254
255 CHAR     rcvBuffer[128];
256
257 INT     HandleClient(INT sock)
258 {
259
260 INT     status;
261
262
263     status = recv(sock, (VOID *)rcvBuffer, 128,0);
264     if (status == ERROR )
265     {
266         printf("\n BSD Server Socket:%d receive \n",sock);
267         return(ERROR);
268     }
269
270     /* a zero return from a recv() call indicates client is terminated! */
271     if (status == 0)
272     {
273         /* Done with this client , close this secondary server socket */
274         return(status);
275     }
276
277     /* print data received from the client */
278     printf("\nBSD Server Socket:%d received %lu bytes: %s \n", sock, (ULONG)status,rcvBuffer);
279
280     /* And echo the same data to the client */
281     status = send(sock,rcvBuffer, status + 1, 0);
282     if (status == ERROR )
283     {
284         printf("\nError: BSD Server Socket:%d send \n",sock);
285         return(ERROR);
286     }
287     return(status);
288 }
289
290
291 /* Define what the initial system looks like. */
292
293 void     tx_application_define(void *first_unused_memory)
294 {
295
296 CHAR     *pointer;
297 UINT     status;
298
299     /* Setup the working pointer. */
300     pointer = (CHAR *) first_unused_memory;
301
302     /* Create a client thread. */
303     tx_thread_create(&thread_0, "Client1", thread_0_entry, 0,
304         pointer, DEMO_STACK_SIZE, 2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
305
306     pointer = pointer + DEMO_STACK_SIZE;
307
308     /* Create a server thread. */
309     tx_thread_create(&thread_1, "Server", thread_1_entry, 0,
310         pointer, DEMO_STACK_SIZE,1,1, TX_NO_TIME_SLICE, TX_AUTO_START);
311
312     pointer = pointer + DEMO_STACK_SIZE;
313
314     /* Initialize the NetX system. */
315     nx_system_initialize();
316
317     /* Create a BSD packet pool. */
318     status = nx_packet_pool_create(&bsd_pool,"NetX BSD Packet Pool", 128
                                        pointer, 16384);
319     pointer = pointer + 16384;
320     if (status)
321     {
322         error_counter++;
323         printf("Error in creating BSD packet pool\n!");
324     }
325
326     /* Create an IP instance for BSD. */
327     status = nx_ip_create(&bsd_ip, "NetX IP Instance 2", IP_ADDRESS(1, 2, 3, 4),
                              0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                              pointer, 2048, 1);
328
329     pointer = pointer + 2048;
330
331     if (status)
332     {
333         error_counter++;
334         printf("Error creating BSD IP instance\n!");
335     }
336
337     /* Enable ARP and supply ARP cache memory for BSD IP Instance */
338     status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
339     pointer = pointer + 1024;
340
341     /* Check ARP enable status. */
342     if (status)
343     {
344         error_counter++;
345         printf("Error in Enable ARP and supply ARP cache memory to BSD IP instance\n");
346     }
347
348     /* Enable TCP processing for BSD IP instances. */
349
350     status = nx_tcp_enable(&bsd_ip);
351
352     /* Check TCP enable status. */
353     if (status)
354     {
355         error_counter++;
356         printf("Error in Enable TCP \n");
357     }
358
359     /* Now initialize BSD Scoket Wrapper */
360     status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 1);
361 }
362
363
364 /* Define the test threads. */
365
366 void     thread_0_entry)ULONG thread_input)
367 {
368
369 CHAR     *msg0 = "Client 1:
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<> \
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";
370
371     /* Wait till Server side is all set */
372     tx_thread_sleep(2);
373     while (1)
374     {
375         tcpClient(msg0);
376         tx_thread_sleep(1);
377     }
378 }
379
380 /* Define the server thread entry function. */
381 void     thread_1_entry(ULONG thread_input)
382 {
383
384 UINT     status;
385 ULONG    actual_status;
386
387 /* Ensure the IP instance has been initialized. */
388 status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE, &actual_status, 100);
389
390 /* Check status... */
391 if (status != NX_SUCCESS)
392 {
393     error_counter++;
394     return;
395 }
396 /* Start a TCP Server */
397 tcpServer();
398 }
399
```
