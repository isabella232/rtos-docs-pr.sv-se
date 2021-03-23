---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo DHCP Client
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo DHCP-klienten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c3df64be337b557f492617c1ef20adc7c0f8d6e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826124"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcp-client"></a><span data-ttu-id="43c91-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo DHCP Client</span><span class="sxs-lookup"><span data-stu-id="43c91-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo DHCP Client</span></span>

<span data-ttu-id="43c91-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="43c91-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo DHCP Client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="43c91-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="43c91-105">Product Distribution</span></span>

<span data-ttu-id="43c91-106">Azure återställnings tider NetX Duo kan hämtas från vår offentliga käll kods lagrings plats på <https://github.com/azure-rtos/netxduo> .</span><span class="sxs-lookup"><span data-stu-id="43c91-106">Azure RTOS NetX Duo can be obtained from our public source code repository at <https://github.com/azure-rtos/netxduo>.</span></span> <span data-ttu-id="43c91-107">Paketet innehåller följande filer:</span><span class="sxs-lookup"><span data-stu-id="43c91-107">The package includes the following files:</span></span>

- <span data-ttu-id="43c91-108">**nxd_dhcp_client. h**: rubrik fil för netx Duo DHCP</span><span class="sxs-lookup"><span data-stu-id="43c91-108">**nxd_dhcp_client.h**: Header file for NetX Duo DHCP</span></span>
- <span data-ttu-id="43c91-109">**nxd_dhcp_client. c**: c-KÄLLFIL för DHCP netx Duo</span><span class="sxs-lookup"><span data-stu-id="43c91-109">**nxd_dhcp_client.c**: C Source file for DHCP NetX Duo</span></span>
- <span data-ttu-id="43c91-110">**nxd_dhcp_client.pdf**: Användar handbok för netx Duo DHCP</span><span class="sxs-lookup"><span data-stu-id="43c91-110">**nxd_dhcp_client.pdf**: User Guide for NetX Duo DHCP</span></span> 
    - <span data-ttu-id="43c91-111">**demo_netxduo_dhcp. c**: netx Duo DHCP Client demonstration</span><span class="sxs-lookup"><span data-stu-id="43c91-111">**demo_netxduo_dhcp.c**: NetX Duo DHCP Client demonstration</span></span>
    - <span data-ttu-id="43c91-112">**demo_netxduo_multihome_dhcp_client. c**: netx Duo DHCP Client demonstration av DHCP på flera gränssnitt</span><span class="sxs-lookup"><span data-stu-id="43c91-112">**demo_netxduo_multihome_dhcp_client.c**: NetX Duo DHCP Client demonstration of DHCP on multiple interfaces</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="43c91-113">DHCP-installation</span><span class="sxs-lookup"><span data-stu-id="43c91-113">DHCP Installation</span></span>

<span data-ttu-id="43c91-114">Om du vill använda NetX Duo DHCP-klienten ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX Duo är installerat.</span><span class="sxs-lookup"><span data-stu-id="43c91-114">To use NetX Duo DHCP Client, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="43c91-115">Om t. ex. NetX Duo är installerat i katalogen "*\threadx\arm7\green*", ska *nxd_dhcp_client. h* -och *nxd_dhcp_client. c* -filerna kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="43c91-115">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_dhcp_client.h* and *nxd_dhcp_client.c* files should be copied into this directory.</span></span>

## <a name="using-dhcp"></a><span data-ttu-id="43c91-116">Använda DHCP</span><span class="sxs-lookup"><span data-stu-id="43c91-116">Using DHCP</span></span>

<span data-ttu-id="43c91-117">Det är enkelt att använda DHCP för NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="43c91-117">Using DHCP for NetX Duo is easy.</span></span> <span data-ttu-id="43c91-118">I princip måste program koden innehålla *nxd_dhcp_client. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX respektive netx Duo.</span><span class="sxs-lookup"><span data-stu-id="43c91-118">Basically, the application code must include *nxd_dhcp_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="43c91-119">När *nxd_dhcp_client. h* ingår kan program koden sedan göra DHCP-funktions anropen angivna senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="43c91-119">Once *nxd_dhcp_client.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="43c91-120">Programmet måste även innehålla *nxd_dhcp_client. c* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="43c91-120">The application must also include *nxd_dhcp_client.c* in the build process.</span></span> <span data-ttu-id="43c91-121">Den här filen måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="43c91-121">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="43c91-122">Detta är allt som krävs för att använda NetX DHCP.</span><span class="sxs-lookup"><span data-stu-id="43c91-122">This is all that is required to use NetX DHCP.</span></span>

<span data-ttu-id="43c91-123">Observera att eftersom DHCP använder NetX Duo UDP-tjänster måste UDP aktive ras med *nx_udp_enable* anrop innan DHCP används.</span><span class="sxs-lookup"><span data-stu-id="43c91-123">Note that since DHCP utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

<span data-ttu-id="43c91-124">Om du vill hämta en tidigare tilldelad IP-adress kan DHCP-klienten initiera DHCP-processen med begär ande meddelandet och alternativet 50 "begärd IP-adress" till DHCP-servern.</span><span class="sxs-lookup"><span data-stu-id="43c91-124">To obtain a previously assigned IP address, the DHCP Client can initiate the DHCP process with the Request message and Option 50 “Requested IP Address” to the DHCP Server.</span></span> <span data-ttu-id="43c91-125">DHCP-servern svarar med antingen ett ACK-meddelande om den ger IP-adressen till klienten eller en NACK om den vägrar.</span><span class="sxs-lookup"><span data-stu-id="43c91-125">The DHCP Server will respond with either an ACK message if it grants the IP address to the Client or a NACK if it refuses.</span></span> <span data-ttu-id="43c91-126">I det senare fallet startar DHCP-klienten om DHCP-processen i init-tillstånd med ett identifierings meddelande och ingen begärd IP-adress.</span><span class="sxs-lookup"><span data-stu-id="43c91-126">In the latter case, the DHCP Client restarts the DHCP process at the Init state with a Discover message and no requested IP address.</span></span> <span data-ttu-id="43c91-127">Värd programmet skapar först DHCP-klienten och anropar sedan tjänsten *nx_dhcp_request_client_ip* API för att ange den begärda IP-adressen innan DHCP-processen startas med *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="43c91-127">The host application first creates the DHCP Client, then calls the *nx_dhcp_request_client_ip* API service to set the requested IP address before starting the DHCP process with *nx_dhcp_start*.</span></span> <span data-ttu-id="43c91-128">Ett exempel på ett DHCP-program finns på annan plats i det här dokumentet för mer information.</span><span class="sxs-lookup"><span data-stu-id="43c91-128">An example DHCP application is provided elsewhere in this document for more details.</span></span>

## <a name="in-the-bound-state"></a><span data-ttu-id="43c91-129">I bindnings tillstånd</span><span class="sxs-lookup"><span data-stu-id="43c91-129">In the Bound State</span></span>

<span data-ttu-id="43c91-130">När DHCP-klienten är i ett begränsat tillstånd bearbetar DHCP-klientens tillstånd en gång per intervall (som anges i NX_DHCP_TIME_INTERVAL) och minskar den tid som återstår för det IP-lån som tilldelats till klienten.</span><span class="sxs-lookup"><span data-stu-id="43c91-130">While the DHCP Client is in the bound state, the DHCP Client thread processes the Client state once per interval (as specified by NX_DHCP_TIME_INTERVAL) and decrements the time remaining on the IP lease assigned to the Client.</span></span> <span data-ttu-id="43c91-131">När förnyelse tiden har gått uppdateras DHCP-klientens tillstånd till det FÖRNYAde tillstånd där klienten begär en förnyelse från DHCP-servern.</span><span class="sxs-lookup"><span data-stu-id="43c91-131">When the renewal time has elapsed the DHCP Client state is updated to the RENEW state where the Client will request a renewal from the DHCP Server.</span></span>

## <a name="sending-dhcp-messages-to-the-server"></a><span data-ttu-id="43c91-132">Skicka DHCP-meddelanden till servern</span><span class="sxs-lookup"><span data-stu-id="43c91-132">Sending DHCP Messages To The Server</span></span>

<span data-ttu-id="43c91-133">DHCP-klienten har API-tjänster som gör det möjligt för värd programmet att skicka ett meddelande till DHCP-servern.</span><span class="sxs-lookup"><span data-stu-id="43c91-133">The DHCP Client has API services that allow the host application to send a message to the DHCP Server.</span></span> <span data-ttu-id="43c91-134">Observera att dessa tjänster inte är avsedda för att värd programmet ska kunna köra DHCP-klient protokollet manuellt.</span><span class="sxs-lookup"><span data-stu-id="43c91-134">Note these services are NOT intended for the host application to manually run the DHCP Client protocol.</span></span>

  - <span data-ttu-id="43c91-135">*nx_dhcp_release*: detta skickar ett versions meddelande till servern när värd programmet antingen lämnar nätverket eller behöver lämna sin IP-adress.</span><span class="sxs-lookup"><span data-stu-id="43c91-135">*nx_dhcp_release*: this sends a RELEASE message to the Server when the host application is either leaving the network or needs relinquish its IP address.</span></span>
  - <span data-ttu-id="43c91-136">*nx_dhcp_decline*: detta skickar ett neka-meddelande till servern om värd programmet avgör oberoende av DHCP-klienten att dess IP-adress redan används.</span><span class="sxs-lookup"><span data-stu-id="43c91-136">*nx_dhcp_decline*: this sends a DECLINE message to the Server if the host application determines independently of the DHCP Client that its IP address is already in use.</span></span>
  - <span data-ttu-id="43c91-137">*nx_dhcp_forcerenew*: detta skickar ett forcerenew-meddelande till servern</span><span class="sxs-lookup"><span data-stu-id="43c91-137">*nx_dhcp_forcerenew*: this sends a FORCERENEW message to the Server</span></span>
  - <span data-ttu-id="43c91-138">*nx_dhcp_send_request*: Detta tar som ett argument av typen DHCP-meddelande som anges i *nxd_dhcp_client. h* och skickar meddelandet till servern.</span><span class="sxs-lookup"><span data-stu-id="43c91-138">*nx_dhcp_send_request*: This takes as an argument a DHCP message type, as specified in *nxd_dhcp_client.h*, and sends the message to the Server.</span></span> <span data-ttu-id="43c91-139">Detta är främst avsett för att skicka meddelandet om DHCP-informning.</span><span class="sxs-lookup"><span data-stu-id="43c91-139">This is intended primarily for sending the DHCP INFORM message.</span></span>

<span data-ttu-id="43c91-140">Se [Beskrivning av DHCP-tjänster](chapter3.md) för mer information om dessa tjänster</span><span class="sxs-lookup"><span data-stu-id="43c91-140">See [Description of DHCP Services](chapter3.md) for more information about these services</span></span> 

## <a name="starting-and-stopping-the-dhcp-client"></a><span data-ttu-id="43c91-141">Starta och stoppa DHCP-klienten</span><span class="sxs-lookup"><span data-stu-id="43c91-141">Starting and Stopping the DHCP Client</span></span>

<span data-ttu-id="43c91-142">Om du vill stoppa DHCP-klienten, oavsett om den har uppnått ett begränsat tillstånd, anropar värd programmet *nx_dhcp_stop*.</span><span class="sxs-lookup"><span data-stu-id="43c91-142">To stop the DHCP Client, regardless if it has achieved a bound state, the host application calls *nx_dhcp_stop*.</span></span>

<span data-ttu-id="43c91-143">Om du vill starta om en DHCP-klient måste värd programmet först stoppa DHCP-klienten med hjälp av *nx_dhcp_stop* tjänst som beskrivs ovan.</span><span class="sxs-lookup"><span data-stu-id="43c91-143">To restart a DHCP Client, the host application must first stop the DHCP Client using the *nx_dhcp_stop* service described above.</span></span> <span data-ttu-id="43c91-144">Sedan kan värden anropa *nx_dhcp_start* för att återuppta DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="43c91-144">Then the host can call *nx_dhcp_start* to resume the DHCP Client.</span></span> <span data-ttu-id="43c91-145">Om värd programmet vill rensa en tidigare DHCP-klient profil, till exempel en som hämtats från en tidigare DHCP-server i ett annat nätverk, bör värd programmet anropa *nx_dhcp_reinitialize* för att utföra den här uppgiften internt innan du anropar *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="43c91-145">If the host application wishes to clear a previous DHCP Client profile, for example, one obtained from a previous DHCP Server on another network, the host application should call *nx_dhcp_reinitialize* to perform this task internally before calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="43c91-146">En typisk sekvens kan vara:</span><span class="sxs-lookup"><span data-stu-id="43c91-146">A typical sequence might be:</span></span>

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="43c91-147">För DHCP-program som körs på ett enda DHCP-gränssnitt inaktiverar DHCP-klienten även DHCP-KLIENTens timer.</span><span class="sxs-lookup"><span data-stu-id="43c91-147">For DHCP applications running on only a single DHCP interface, stopping the DHCP Client also inactivates the DHCP CLIENT timer.</span></span> <span data-ttu-id="43c91-148">Det är därför inte längre att hålla koll på den återstående tiden i IP-lånet.</span><span class="sxs-lookup"><span data-stu-id="43c91-148">Thus it is no longer keeping track of the time remaining on the IP lease.</span></span> <span data-ttu-id="43c91-149">Om DHCP-klienten stoppas på ett visst gränssnitt inaktive ras inte DHCP-klientens timer, men uppdateringar av timern stoppas vid den tid som återstår av IP-adresslån på det gränssnittet</span><span class="sxs-lookup"><span data-stu-id="43c91-149">Stopping DHCP Client on a particular interface will not inactivate the DHCP Client timer but will stop timer updates to the time remaining on the IP lease on that interface</span></span>

<span data-ttu-id="43c91-150">Att stoppa DHCP-klienten rekommenderas därför inte om värd programmet kräver omstart eller växling av nätverk.</span><span class="sxs-lookup"><span data-stu-id="43c91-150">Therefore, stopping the DHCP Client is not advised unless the host application requires rebooting or switching networks.</span></span>

## <a name="using-the-dhcp-client-with-auto-ip"></a><span data-ttu-id="43c91-151">Använda DHCP-klienten med automatisk IP</span><span class="sxs-lookup"><span data-stu-id="43c91-151">Using the DHCP Client with Auto IP</span></span>

<span data-ttu-id="43c91-152">NetX Duo DHCP-klienten fungerar samtidigt med det automatiska IP-protokollet i program där DHCP och automatisk IP garanterar en adress där en DHCP-server inte garanterat är tillgänglig eller svarar.</span><span class="sxs-lookup"><span data-stu-id="43c91-152">The NetX Duo DHCP Client works concurrently with the Auto IP protocol in applications where DHCP and Auto IP guarantee an address where a DHCP Server is not guaranteed to be available or responding.</span></span> <span data-ttu-id="43c91-153">Men om värden inte kan identifiera en server eller hämta en IP-adress, kan den växla till det automatiska IP-protokollet för en lokal IP-adress.</span><span class="sxs-lookup"><span data-stu-id="43c91-153">However, If the host is unable to detect a Server or get an IP address assigned, it can switch to the Auto IP protocol for a local IP address.</span></span> <span data-ttu-id="43c91-154">Innan du gör det rekommenderar vi dock att du stoppar DHCP-klienten tillfälligt medan den automatiska IP-adressen går igenom stegen "avsökning" och "försvar".</span><span class="sxs-lookup"><span data-stu-id="43c91-154">However before doing so, it is advisable to stop the DHCP Client temporarily while Auto IP goes through the “probe” and “defense” stages.</span></span> <span data-ttu-id="43c91-155">När en automatisk IP-adress tilldelas till värden kan DHCP-klienten startas om och om en DHCP-server blir tillgänglig kan värd-IP-adressen acceptera IP-adressen som erbjuds av DHCP-servern medan programmet körs.</span><span class="sxs-lookup"><span data-stu-id="43c91-155">Once an Auto IP address is assigned to the host, the DHCP Client can be restarted and if a DHCP Server does become available, the host IP address can accept the IP address offered by the DHCP Server while the application is running.</span></span>

<span data-ttu-id="43c91-156">NetX Duo Auto IP har ett meddelande om adress ändring för värden för att övervaka aktiviteter i händelse av en ändring av IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="43c91-156">The NetX Duo Auto IP has an address change notification for the host to monitor its activities in the event of an IP address change.</span></span>

## <a name="packet-chaining"></a><span data-ttu-id="43c91-157">Paket länkning</span><span class="sxs-lookup"><span data-stu-id="43c91-157">Packet Chaining</span></span>

<span data-ttu-id="43c91-158">För effektivare användning av paket-och minnes resurser kan DHCP-klienten hantera inkommande kedjade paket (datagram som överskrider driv Rutinens MTU) från Ethernet-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="43c91-158">For more efficient use of packet pool and memory resources, the DHCP Client can handle incoming chained packets (datagrams exceeding the driver MTU) from the Ethernet driver.</span></span> <span data-ttu-id="43c91-159">Om driv rutinen har den här funktionen kan programmet ställa in modempoolen för att ta emot paket under de obligatoriska NX_DHCP_PACKET_PAYLOAD byte.</span><span class="sxs-lookup"><span data-stu-id="43c91-159">If the driver has this capability, the application can set the packet pool for receiving packets to below the mandatory NX_DHCP_PACKET_PAYLOAD bytes.</span></span> <span data-ttu-id="43c91-160">NX_DHCP_PACKET_PAYLOAD bör rymma det fysiska nätverkets (oftast Ethernet) ram, plus 548 byte av DHCP-meddelande data och IP och UDP.</span><span class="sxs-lookup"><span data-stu-id="43c91-160">NX_DHCP_PACKET_PAYLOAD should accommodate the physical network (typically Ethernet) frame, plus 548 bytes of DHCP message data, and IP and UDP.</span></span>

<span data-ttu-id="43c91-161">Observera att programmet kan optimera paketets nytto last och antalet paket i modempoolen som ingår i DHCP-klienten och som används för att skicka DHCP-meddelanden. Den kan optimera storleken baserat på förväntad användning och storlek på DHCP-klientens meddelanden.</span><span class="sxs-lookup"><span data-stu-id="43c91-161">Note that the application can optimize the packet payload and number of packets in the packet pool that is part of the DHCP Client, and which is used for sending DHCP messages out. It can optimize the size based on expected usage and size of the DHCP Client messages.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="43c91-162">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="43c91-162">Small Example System</span></span>

<span data-ttu-id="43c91-163">Ett exempel på hur du använder NetX Duo visas i bild 1,1 nedan.</span><span class="sxs-lookup"><span data-stu-id="43c91-163">An example of how to use NetX Duo is shown in Figure 1.1 below.</span></span> <span data-ttu-id="43c91-164">Funktionen för program tråds post "*my_thread_entry*" skapas på rad 101.</span><span class="sxs-lookup"><span data-stu-id="43c91-164">The application thread entry function “*my_thread_entry*” is created at line 101.</span></span> <span data-ttu-id="43c91-165">När åtgärden har skapats initieras DHCP-bearbetningen med *nx_dhcp_start* -anropet på rad 108.</span><span class="sxs-lookup"><span data-stu-id="43c91-165">After successful creation, DHCP processing is initiated with the *nx_dhcp_start* call at line 108.</span></span> <span data-ttu-id="43c91-166">I det här läget försöker DHCP-klientens tråds aktivitet separat att kontakta en DHCP-server.</span><span class="sxs-lookup"><span data-stu-id="43c91-166">At this point, the DHCP Client thread task separately attempts to contact a DHCP server.</span></span> <span data-ttu-id="43c91-167">Under den här processen väntar program koden på att en giltig IP-adress ska registreras med IP-instansen med hjälp av *nx_ip_status_check* tjänsten (eller *nx_ip_interface_status_check* för ett sekundärt gränssnitt) på rad 95.</span><span class="sxs-lookup"><span data-stu-id="43c91-167">During this process, the application code waits for a valid IP address to be registered with the IP instance using the *nx_ip_status_check* service (or *nx_ip_interface_status_check* for a secondary interface) on line 95.</span></span> <span data-ttu-id="43c91-168">Detta görs ofta i en slinga med ett kortare vänte alternativ.</span><span class="sxs-lookup"><span data-stu-id="43c91-168">This is more commonly done in a loop with a shorter wait option.</span></span>

<span data-ttu-id="43c91-169">Efter rad 127 har DHCP tagit emot en giltig IP-adress och programmet kan sedan fortsätta, med NetX Duo TCP/IP-tjänster som önskade.</span><span class="sxs-lookup"><span data-stu-id="43c91-169">After line 127, DHCP has received a valid IP address and the application can then proceed, utilizing NetX Duo TCP/IP services as desired.</span></span>

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */
intmain()
{
  /* Enter the ThreadX kernel.  */
  tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;
    
    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create “my_thread”.  */
      tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                        pointer, DEMO_STACK_SIZE, 2, 2, 
                        TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

    /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                          0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
                          DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
 }


 /* Define my thread.  */

 void    my_thread_entry(ULONG thread_input)
 {

 UINT        status;
 ULONG       actual_status;
 NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
    /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                                     &actual_status, 100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
      error_counter++;
      return;
    }
    else
    {

  /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.
    }
 }

```
## <a name="multi-server-environments"></a><span data-ttu-id="43c91-170">Miljöer med flera servrar</span><span class="sxs-lookup"><span data-stu-id="43c91-170">Multi-Server Environments</span></span>

<span data-ttu-id="43c91-171">På nätverk där det finns mer än en DHCP-server godkänner DHCP-klienten det första mottagna meddelandet om erbjudande för DHCP-servern, går vidare till status för begäran och ignorerar alla andra mottagna erbjudanden.</span><span class="sxs-lookup"><span data-stu-id="43c91-171">On networks where there is more than one DHCP Server, the DHCP Client accepts the first received DHCP Server Offer message, advances to the Request state, and ignores any other received offers.</span></span>

## <a name="arp-probes"></a><span data-ttu-id="43c91-172">ARP-avsökningar</span><span class="sxs-lookup"><span data-stu-id="43c91-172">ARP Probes</span></span>

<span data-ttu-id="43c91-173">DHCP-klienten kan konfigureras att skicka en eller flera ARP-avsökningar efter tilldelning av IP-adress från DHCP-servern för att kontrol lera att IP-adressen inte redan används.</span><span class="sxs-lookup"><span data-stu-id="43c91-173">The DHCP Client can be configured to send one or more ARP probes after IP address assignment from the DHCP Server to verify the IP address is not already in use.</span></span> <span data-ttu-id="43c91-174">Steget ARP PROBE rekommenderas av RFC 2131 och är särskilt viktigt i miljöer med fler än en DHCP-server.</span><span class="sxs-lookup"><span data-stu-id="43c91-174">The ARP probe step is recommended by RFC 2131 and is particularly important in environments with more than one DHCP Server.</span></span> <span data-ttu-id="43c91-175">Om värd programmet aktiverar NX_DHCP_CLIENT_SEND_ARP_PROBE alternativ (se **konfigurations alternativ** i kapitel två för ytterligare ARP-avsöknings alternativ) skickar DHCP-klienten en "självbetjänings" ARP-avsökning och väntar på den angivna tiden för ett svar.</span><span class="sxs-lookup"><span data-stu-id="43c91-175">If the host application enables the NX_DHCP_CLIENT_SEND_ARP_PROBE option (see **Configuration Options** in Chapter Two for additional ARP probe options), the DHCP Client will send a ‘self addressed’ ARP probe and wait for the specified time for a response.</span></span> <span data-ttu-id="43c91-176">Om ingen tas emot förflyttar sig DHCP-klienten till det begränsade tillstånd.</span><span class="sxs-lookup"><span data-stu-id="43c91-176">If none is received, the DHCP Client advances to the Bound state.</span></span> <span data-ttu-id="43c91-177">Om ett svar tas emot förutsätter DHCP-klienten att adressen redan används.</span><span class="sxs-lookup"><span data-stu-id="43c91-177">If a response is received, the DHCP Client assumes the address is already in use.</span></span> <span data-ttu-id="43c91-178">Det skickar automatiskt ett neka-meddelande till servern och initierar om klienten för att starta om DHCP-avsökningarna igen från INITIERINGs statusen.</span><span class="sxs-lookup"><span data-stu-id="43c91-178">It automatically sends a DECLINE message to the Server, and reinitializes the Client to restart the DHCP probes again from the INIT state.</span></span> <span data-ttu-id="43c91-179">Detta startar om DHCP-tillstånds datorn och klienten skickar ett annat IDENTIFIERINGs meddelande till servern.</span><span class="sxs-lookup"><span data-stu-id="43c91-179">This restarts the DHCP state machine and the Client sends another DISCOVER message to the Server.</span></span>

## <a name="bootp-protocol"></a><span data-ttu-id="43c91-180">BOOTP-protokoll</span><span class="sxs-lookup"><span data-stu-id="43c91-180">BOOTP Protocol</span></span>

<span data-ttu-id="43c91-181">DHCP-klienten stöder även BOOTP-protokollet och DHCP-protokollet.</span><span class="sxs-lookup"><span data-stu-id="43c91-181">The DHCP Client also supports the BOOTP protocol as well the DHCP protocol.</span></span> <span data-ttu-id="43c91-182">Om du vill aktivera det här alternativet och använda BOOTP i stället för DHCP måste värd programmet ange NX_DHCP_BOOTP_ENABLE konfigurations alternativet.</span><span class="sxs-lookup"><span data-stu-id="43c91-182">To enable this option and use BOOTP instead of DHCP, the host application must set the NX_DHCP_BOOTP_ENABLE configuration option.</span></span> <span data-ttu-id="43c91-183">Värd programmet kan fortfarande begära specifika IP-adresser i BOOTP-protokollet.</span><span class="sxs-lookup"><span data-stu-id="43c91-183">The host application can still request specific IP addresses in the BOOTP protocol.</span></span> <span data-ttu-id="43c91-184">DHCP-klienten stöder dock inte inläsning av värd operativ systemet eftersom BOOTP ibland används.</span><span class="sxs-lookup"><span data-stu-id="43c91-184">However, the DHCP Client does not support loading the host operating system as BOOTP is sometimes used to do.</span></span>

## <a name="dhcp-on-a-secondary-interface"></a><span data-ttu-id="43c91-185">DHCP på ett sekundärt gränssnitt</span><span class="sxs-lookup"><span data-stu-id="43c91-185">DHCP on a Secondary Interface</span></span>

<span data-ttu-id="43c91-186">NetX Duo DHCP-klienten kan köras på sekundära gränssnitt i stället för det primära standard gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="43c91-186">The NetX Duo DHCP Client can run on secondary interfaces rather than the default primary interface.</span></span>

<span data-ttu-id="43c91-187">Om du vill köra NetX Duo DHCP-klienten på ett sekundärt nätverks gränssnitt måste värd programmet ange gränssnitts index för DHCP-klienten till det sekundära gränssnittet med hjälp av *nx_dhcp_set_interface_index* API-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="43c91-187">To run NetX Duo DHCP Client on a secondary network interface, the host application must set the interface index of the DHCP Client to the secondary interface using the *nx_dhcp_set_interface_index* API service.</span></span> <span data-ttu-id="43c91-188">Gränssnittet måste redan vara kopplat till det primära nätverks gränssnittet med hjälp av tjänsten *nx_ip_interface_attach* .</span><span class="sxs-lookup"><span data-stu-id="43c91-188">The interface must already be attached to the primary network interface using the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="43c91-189">I användar handboken för NetX Duo finns mer information om hur du kopplar sekundära gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="43c91-189">See the NetX Duo User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="43c91-190">Nedan visas ett exempel system (bild 1,2) där värd programmet ansluter till DHCP-servern på det sekundära gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="43c91-190">Below is an example system (Figure 1.2) in which the host application connects to the DHCP server on its secondary interface.</span></span> <span data-ttu-id="43c91-191">På rad 65 kopplas det sekundära gränssnittet till IP-aktiviteten med en null-IP-adress.</span><span class="sxs-lookup"><span data-stu-id="43c91-191">On line 65, the secondary interface is attached to the IP task with a null IP address.</span></span> <span data-ttu-id="43c91-192">Efter att DHCP-klienttjänsten har skapats på rad 104 anges DHCP-klientens gränssnitts index till 1 (t. ex. förskjutningen från det primära gränssnittet som själva är index 0) genom att anropa *nx_dhcp_set_interface_index*.</span><span class="sxs-lookup"><span data-stu-id="43c91-192">On line 104, after the DHCP Client instance is created, the DHCP Client interface index is set to 1 (e.g. the offset from the primary interface which itself is index 0) by calling *nx_dhcp_set_interface_index*.</span></span> <span data-ttu-id="43c91-193">Sedan är DHCP-klienten redo att startas på rad 108.</span><span class="sxs-lookup"><span data-stu-id="43c91-193">Then the DHCP Client is ready to be started in line 108.</span></span>

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */

intmain()
{
  /* Enter the ThreadX kernel.  */
  tx_kernel_enter();
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create “my_thread”.  */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                      pointer, DEMO_STACK_SIZE, 
                      2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

  /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                           0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    status =  _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                                       0xFFFFFF00UL, my_netx_driver);

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}


void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       status;
NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
      /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Set the DHCP client interface to the secondary interface. */
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
        error_counter++;
        return;
    }
    else
    {
    /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.*/
    }
}
```

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a><span data-ttu-id="43c91-194">DHCP-klient på flera gränssnitt samtidigt</span><span class="sxs-lookup"><span data-stu-id="43c91-194">DHCP Client on Multiple Interfaces Simultaneously</span></span>

<span data-ttu-id="43c91-195">Om du vill köra DHCP-klienten på flera gränssnitt måste NX_MAX_PHYSICAL_INTERFACES i *nx_api. h* vara inställt på antalet fysiska gränssnitt som är anslutna till enheten.</span><span class="sxs-lookup"><span data-stu-id="43c91-195">To run DHCP Client on multiple interfaces, NX_MAX_PHYSICAL_INTERFACES in *nx_api.h* must be set to the number of physical interfaces connected to the device.</span></span> <span data-ttu-id="43c91-196">Som standard är det här värdet 1 (t. ex. det primära gränssnittet).</span><span class="sxs-lookup"><span data-stu-id="43c91-196">By default, this value is 1 (e.g. the primary interface).</span></span> <span data-ttu-id="43c91-197">Använd tjänsten *nx_ip_interface_attach* om du vill registrera ytterligare ett gränssnitt för IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="43c91-197">To register an additional interface to the IP instance use the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="43c91-198">I användar handboken för NetX Duo finns mer information om hur du kopplar sekundära gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="43c91-198">See the NetX Duo User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="43c91-199">Nästa steg är att ange NX_DHCP_CLIENT_MAX_RECORDS i *nxd_dhcp_client. h* till det maximala antalet gränssnitt som förväntas köra DHCP samtidigt.</span><span class="sxs-lookup"><span data-stu-id="43c91-199">The next step is to set the NX_DHCP_CLIENT_MAX_RECORDS in *nxd_dhcp_client.h* to the maximum number of interfaces expected to run DHCP simultaneously.</span></span> <span data-ttu-id="43c91-200">Observera att NX_DHCP_CLIENT_MAX_RECORDS inte måste vara lika med NX_MAX_PHYSICAL_INTERFACES.</span><span class="sxs-lookup"><span data-stu-id="43c91-200">Note that NX_DHCP_CLIENT_MAX_RECORDS does not have to equal NX_MAX_PHYSICAL_INTERFACES.</span></span> <span data-ttu-id="43c91-201">NX_MAX_PHYSICAL_INTERFACES kan till exempel vara 3 och NX_DHCP_CLIENT_MAX_RECORDS lika med 2.</span><span class="sxs-lookup"><span data-stu-id="43c91-201">For example, NX_MAX_PHYSICAL_INTERFACES can be 3 and NX_DHCP_CLIENT_MAX_RECORDS equal to 2.</span></span> <span data-ttu-id="43c91-202">I den här konfigurationen kan bara två gränssnitt (och båda vara två av de tre fysiska gränssnitten när som helst) av de tre fysiska gränssnitten köra DHCP vid ett och samma tillfälle.</span><span class="sxs-lookup"><span data-stu-id="43c91-202">In this configuration, only two interfaces (and they can be any two of the three physical interfaces at any time) of the three physical interfaces can run DHCP at any one time.</span></span> <span data-ttu-id="43c91-203">DHCP-klientens poster har ingen mappning till nätverks gränssnitt, t. ex. klient post 1 motsvarar inte automatiskt det fysiska gränssnittets index 1.</span><span class="sxs-lookup"><span data-stu-id="43c91-203">DHCP Client Records do not have a one to one mapping to network interfaces e.g. Client Record 1 does not automatically correlate to physical interface index 1.</span></span>

<span data-ttu-id="43c91-204">NX_DHCP_CLIENT_MAX_RECORDS kan också ställas in på fler än NX_MAX_PHYSICAL_INTERFACES men detta skulle skapa oanvända klient poster och vara en ineffektiv användning av minnet.</span><span class="sxs-lookup"><span data-stu-id="43c91-204">NX_DHCP_CLIENT_MAX_RECORDS can also be set to greater than NX_MAX_PHYSICAL_INTERFACES but this would create unused client records and be an inefficient use of memory.</span></span>

<span data-ttu-id="43c91-205">Innan den kan starta DHCP på alla gränssnitt måste programmet aktivera dessa gränssnitt genom att anropa *nx_dhcp_interface_enable*.</span><span class="sxs-lookup"><span data-stu-id="43c91-205">Before it can start DHCP on any interface, the application must enable those interfaces by calling *nx_dhcp_interface_enable*.</span></span> <span data-ttu-id="43c91-206">Observera att undantaget är det primära gränssnittet som automatiskt aktive ras i *nx_dhcp_create* -anropet (och som kan inaktive ras med hjälp av tjänsten *nx_dhcp_interface_disable* som diskuteras nedan).</span><span class="sxs-lookup"><span data-stu-id="43c91-206">Note that the exception is the primary interface which is automatically enabled in the *nx_dhcp_create* call (and which can be disabled using the *nx_dhcp_interface_disable* service discussed below).</span></span>

<span data-ttu-id="43c91-207">När som helst kan ett gränssnitt inaktive ras för DHCP eller DHCP kan stoppas på det gränssnittet oberoende av andra gränssnitt som kör DHCP.</span><span class="sxs-lookup"><span data-stu-id="43c91-207">At any time, an interface can be disabled for DHCP or DHCP can be stopped on that interface independently of other interfaces running DHCP.</span></span>

<span data-ttu-id="43c91-208">Som nämnts ovan, för att aktivera ett särskilt gränssnitt för DHCP, använder du tjänsten *nx_dhcp_interface_enable* och anger det fysiska gränssnitts indexet i indataargumentet.</span><span class="sxs-lookup"><span data-stu-id="43c91-208">As mentioned above, to enable a specific interface for DHCP, use the *nx_dhcp_interface_enable* service and specify the physical interface index in the input argument.</span></span> <span data-ttu-id="43c91-209">Upp till NX_DHCP_CLIENT_MAX_RECORDS-gränssnitt kan aktive ras med den enda begränsningen att indataargumentet för gränssnitts indexet är mindre än NX_MAX_PHYSICAL_INTERFACES.</span><span class="sxs-lookup"><span data-stu-id="43c91-209">Up to NX_DHCP_CLIENT_MAX_RECORDS interfaces can be enabled with the only limitation that the interface index input argument be less than NX_MAX_PHYSICAL_INTERFACES.</span></span>

<span data-ttu-id="43c91-210">Använd tjänsten *nx_dhcp_interface_start* för att starta DHCP på ett speciellt gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="43c91-210">To start DHCP on a specific interface, use the *nx_dhcp_interface_start* service.</span></span> <span data-ttu-id="43c91-211">Använd tjänsten *nx_dhcp_start* för att starta DHCP på alla aktiverade gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="43c91-211">To start DHCP on all enabled interfaces, use the *nx_dhcp_start* service.</span></span> <span data-ttu-id="43c91-212">(Gränssnitt som redan har startat DHCP kommer inte att påverkas av *nx_dhcp_start*.)</span><span class="sxs-lookup"><span data-stu-id="43c91-212">(Interfaces that have already started DHCP will not be affected by *nx_dhcp_start*.)</span></span>

<span data-ttu-id="43c91-213">Om du vill stoppa DHCP på ett gränssnitt använder du tjänsten *nx_dhcp_interface_stop* .</span><span class="sxs-lookup"><span data-stu-id="43c91-213">To stop DHCP on an interface, use the *nx_dhcp_interface_stop* service.</span></span> <span data-ttu-id="43c91-214">DHCP måste redan ha startat på det gränssnittet, annars returneras en fel status.</span><span class="sxs-lookup"><span data-stu-id="43c91-214">DHCP must already have started on that interface or an error status is returned.</span></span> <span data-ttu-id="43c91-215">Om du vill stoppa DHCP på alla aktiverade gränssnitt använder du tjänsten *nx_dhcp_stop* .</span><span class="sxs-lookup"><span data-stu-id="43c91-215">To stop DHCP on all enabled interfaces, use the *nx_dhcp_stop* service.</span></span> <span data-ttu-id="43c91-216">DHCP kan stoppas oberoende av andra gränssnitt när som helst.</span><span class="sxs-lookup"><span data-stu-id="43c91-216">DHCP can be stopped independently of other interfaces at any time.</span></span>

<span data-ttu-id="43c91-217">De flesta av de befintliga DHCP-klient tjänsterna har en motsvarande gränssnitt, t. ex. *nx_dhcp_interface_release* är det gränssnitt som motsvarar *nx_dhcp_release.*</span><span class="sxs-lookup"><span data-stu-id="43c91-217">Most of the existing DHCP Client services have an ‘interface’ equivalent e.g. *nx_dhcp_interface_release* is the interface specific equivalent of *nx_dhcp_release.*</span></span> <span data-ttu-id="43c91-218">Om DHCP-klienten har kon figurer ATS för ett enda gränssnitt utför de samma åtgärd.</span><span class="sxs-lookup"><span data-stu-id="43c91-218">If DHCP Client is configured for a single interface, they perform the same action.</span></span>

<span data-ttu-id="43c91-219">Observera att icke-gränssnitts klient tjänster för DHCP gäller vanligt vis för alla gränssnitt, men inte alla.</span><span class="sxs-lookup"><span data-stu-id="43c91-219">Note that non-interface specific DHCP Client services typically apply to all interfaces but not all.</span></span> <span data-ttu-id="43c91-220">I det senare fallet gäller den icke-gränssnitts tjänsten för det första DHCP-aktiverade gränssnittet som finns i Sök i DHCP-klient listan över gränssnitts poster.</span><span class="sxs-lookup"><span data-stu-id="43c91-220">In the latter case, the non-interface specific service applies to the first DHCP enabled interface found in searching the DHCP Client list of interface records.</span></span> <span data-ttu-id="43c91-221">Se **Beskrivning av tjänster** i kapitel tre för hur en icke-gränssnitts tjänst fungerar när flera gränssnitt är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="43c91-221">See **Description of Services** in Chapter Three for how a non-interface specific service performs when multiple interfaces are enabled for DHCP.</span></span>

<span data-ttu-id="43c91-222">I exempel ordningen nedan har IP-instansen två nätverks gränssnitt och kör först DHCP på det sekundära gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="43c91-222">In the example sequence below, the IP instance has two network interfaces and first runs DHCP on the secondary interface.</span></span> <span data-ttu-id="43c91-223">Vid ett senare tillfälle startar det DHCP på det primära gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="43c91-223">At some time later, it starts DHCP on the primary interface.</span></span> <span data-ttu-id="43c91-224">Sedan frigör den IP-adressen för det primära gränssnittet och startar om DHCP på det primära gränssnittet:</span><span class="sxs-lookup"><span data-stu-id="43c91-224">Then it releases the IP address on the primary interface and restarts DHCP on the primary interface:</span></span>

```c
nx_dhcp_create(&my_dhcp_client); /* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); /* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); /* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); /* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is restarted on primary interface. */
```

<span data-ttu-id="43c91-225">En fullständig lista över gränssnitts vissa tjänster finns i **Beskrivning av tjänster** i kapitel tre.</span><span class="sxs-lookup"><span data-stu-id="43c91-225">For a complete list of interface specific services see **Description of Services** in Chapter Three.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="43c91-226">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="43c91-226">Configuration Options</span></span>

<span data-ttu-id="43c91-227">Användar konfigurerbara DHCP-alternativ i *nxd_dhcp_client. h* gör det möjligt för värd programmet att finjustera DHCP-klienten för särskilda krav.</span><span class="sxs-lookup"><span data-stu-id="43c91-227">User configurable DHCP options in *nxd_dhcp_client.h* allow the host application to fine tune DHCP Client for its particular requirements.</span></span> <span data-ttu-id="43c91-228">Följande är en lista över dessa parametrar:</span><span class="sxs-lookup"><span data-stu-id="43c91-228">The following is a list of these parameters:</span></span>  
  
- <span data-ttu-id="43c91-229">**NX_DHCP_ENABLE_BOOTP**: med det här alternativet aktive ras BOOTP-protokollet i stället för DHCP.</span><span class="sxs-lookup"><span data-stu-id="43c91-229">**NX_DHCP_ENABLE_BOOTP**: Defined, this option enables the BOOTP protocol instead of DHCP.</span></span> <span data-ttu-id="43c91-230">Som standard är det här alternativet inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="43c91-230">By default this option is disabled.</span></span>
- <span data-ttu-id="43c91-231">**NX_DHCP_CLIENT_RESTORE_STATE**: om det här alternativet har definierats så gör det möjligt för DHCP-klienten att spara sin aktuella DHCP-klients licens tillstånd, inklusive återstående tid i lånet, och återställa det här läget mellan DHCP-klientens omstarter.</span><span class="sxs-lookup"><span data-stu-id="43c91-231">**NX_DHCP_CLIENT_RESTORE_STATE**: If defined, this enables the DHCP Client to save its current DHCP Client license ‘state’ including time remaining on the lease, and restore this state between DHCP Client application reboots.</span></span> <span data-ttu-id="43c91-232">Standardvärdet är inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="43c91-232">The default value is disabled.</span></span>
- <span data-ttu-id="43c91-233">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL**: om det är inställt kommer DHCP-klienten inte att skapa en egen modempool.</span><span class="sxs-lookup"><span data-stu-id="43c91-233">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL**: If set, the DHCP Client will not create its own packet pool.</span></span> <span data-ttu-id="43c91-234">Värd programmet måste använda *nx_dhcp_packet_pool_set* tjänsten för att ange DHCP-klientens adresspool.</span><span class="sxs-lookup"><span data-stu-id="43c91-234">The host application must use the *nx_dhcp_packet_pool_set* service to set the DHCP Client packet pool.</span></span> <span data-ttu-id="43c91-235">Standardvärdet är inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="43c91-235">The default value is disabled.</span></span>
- <span data-ttu-id="43c91-236">**NX_DHCP_CLIENT_SEND_ARP_PROBE**: Detta gör att DHCP-klienten kan skicka en ARP-avsökning efter tilldelning av IP-adresser för att kontrol lera att den tilldelade DHCP-adressen inte ägs av en annan värd.</span><span class="sxs-lookup"><span data-stu-id="43c91-236">**NX_DHCP_CLIENT_SEND_ARP_PROBE**: Defined, this enables the DHCP Client to send an ARP probe after IP address assignment to verify the assigned DHCP address is not owned by another host.</span></span> <span data-ttu-id="43c91-237">Som standard är det här alternativet inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="43c91-237">By default, this option is disabled.</span></span>
- <span data-ttu-id="43c91-238">**NX_DHCP_ARP_PROBE_WAIT**: definierar hur lång tid DHCP-klienten väntar på ett svar efter att en ARP-avsökning har skickats.</span><span class="sxs-lookup"><span data-stu-id="43c91-238">**NX_DHCP_ARP_PROBE_WAIT**: Defines the length of time the DHCP Client waits for a response after sending an ARP probe.</span></span> <span data-ttu-id="43c91-239">Standardvärdet är en sekund (1 \* NX_IP_PERIODIC_RATE)</span><span class="sxs-lookup"><span data-stu-id="43c91-239">The default value is one second (1 \* NX_IP_PERIODIC_RATE)</span></span>
- <span data-ttu-id="43c91-240">**NX_DHCP_ARP_PROBE_MIN**: definierar den minsta variationen i intervallet mellan sändning av ARP-avsökningar.</span><span class="sxs-lookup"><span data-stu-id="43c91-240">**NX_DHCP_ARP_PROBE_MIN**: Defines the minimum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="43c91-241">Värdet är standard 1 sekund.</span><span class="sxs-lookup"><span data-stu-id="43c91-241">The value is defaulted to 1 second.</span></span>
- <span data-ttu-id="43c91-242">**NX_DHCP_ARP_PROBE_MAX**: definierar den maximala variationen i intervallet mellan sändning av ARP-avsökningar.</span><span class="sxs-lookup"><span data-stu-id="43c91-242">**NX_DHCP_ARP_PROBE_MAX**: Defines the maximum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="43c91-243">Värdet är standard 2 sekunder.</span><span class="sxs-lookup"><span data-stu-id="43c91-243">The value is defaulted to 2 seconds.</span></span>
- <span data-ttu-id="43c91-244">**NX_DHCP_ARP_PROBE_NUM**: definierar antalet ARP-avsökningar som har skickats för att avgöra om den IP-adress som tilldelats av DHCP-servern redan används.</span><span class="sxs-lookup"><span data-stu-id="43c91-244">**NX_DHCP_ARP_PROBE_NUM**: Defines the number of ARP probes sent for determining if the IP address assigned by the DHCP server is already in use.</span></span> <span data-ttu-id="43c91-245">Värdet är standardvärdet 3 avsökningar.</span><span class="sxs-lookup"><span data-stu-id="43c91-245">The value is defaulted to 3 probes.</span></span>
- <span data-ttu-id="43c91-246">**NX_DHCP_RESTART_WAIT**: definierar hur lång tid DHCP-klienten väntar på att starta om DHCP om IP-adressen som tilldelats DHCP-klienten redan används.</span><span class="sxs-lookup"><span data-stu-id="43c91-246">**NX_DHCP_RESTART_WAIT**: Defines the length of time the DHCP Client waits to restart DHCP if the IP address assigned to the DHCP Client is already in use.</span></span> <span data-ttu-id="43c91-247">Värdet är standard 10 sekunder.</span><span class="sxs-lookup"><span data-stu-id="43c91-247">The value is defaulted to 10 seconds.</span></span>
- <span data-ttu-id="43c91-248">**NX_DHCP_CLIENT_MAX_RECORDS**: anger det maximala antalet gränssnitts poster som ska sparas i DHCP-klientens instans.</span><span class="sxs-lookup"><span data-stu-id="43c91-248">**NX_DHCP_CLIENT_MAX_RECORDS**: Specifies the maximum number of interface records to save to the DHCP Client instance.</span></span> <span data-ttu-id="43c91-249">En DHCP-klients gränssnitts post är en post för DHCP-klienten som körs på ett speciellt gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="43c91-249">A DHCP Client interface record is a record of the DHCP Client running on a specific interface.</span></span> <span data-ttu-id="43c91-250">Standardvärdet anges som antal fysiska gränssnitt (NX_MAX_PHYSICAL_INTERFACES).</span><span class="sxs-lookup"><span data-stu-id="43c91-250">The default value is set as physical interfaces count(NX_MAX_PHYSICAL_INTERFACES).</span></span>
- <span data-ttu-id="43c91-251">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION**: det här alternativet gör att DHCP-klienten kan skicka maximalt värde för DHCP-meddelande storlek.</span><span class="sxs-lookup"><span data-stu-id="43c91-251">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION**: Defined, this enables the DHCP Client to send maximum DHCP message size option.</span></span> <span data-ttu-id="43c91-252">Som standard är det här alternativet inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="43c91-252">By default, this option is disabled.</span></span>
- <span data-ttu-id="43c91-253">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK**: Detta gör att DHCP-klienten kan kontrol lera det angivna värd namnet i nx_dhcp_create anropet för ogiltiga tecken eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="43c91-253">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK**: Defined, this enables the DHCP Client to check the input host name in the nx_dhcp_create call for invalid characters or length.</span></span> <span data-ttu-id="43c91-254">Som standard är det här alternativet inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="43c91-254">By default, this option is disabled.</span></span>
- <span data-ttu-id="43c91-255">**NX_DHCP_THREAD_PRIORITY**: DHCP-Trådens prioritet.</span><span class="sxs-lookup"><span data-stu-id="43c91-255">**NX_DHCP_THREAD_PRIORITY**: Priority of the DHCP thread.</span></span> <span data-ttu-id="43c91-256">Som standard anger det här värdet att DHCP-tråden körs vid prioritet 3.</span><span class="sxs-lookup"><span data-stu-id="43c91-256">By default, this value specifies that the DHCP thread runs at priority 3.</span></span>
- <span data-ttu-id="43c91-257">**NX_DHCP_THREAD_STACK_SIZE**: storleken på DHCP-trådens stack.</span><span class="sxs-lookup"><span data-stu-id="43c91-257">**NX_DHCP_THREAD_STACK_SIZE**: Size of the DHCP thread stack.</span></span> <span data-ttu-id="43c91-258">Som standard är storleken 2048 byte.</span><span class="sxs-lookup"><span data-stu-id="43c91-258">By default, the size is 2048 bytes.</span></span>
- <span data-ttu-id="43c91-259">**NX_DHCP_TIME_INTERVAL**: intervall i sekunder då funktionen för tids gräns för DHCP-klienten körs.</span><span class="sxs-lookup"><span data-stu-id="43c91-259">**NX_DHCP_TIME_INTERVAL**: Interval in seconds when the DHCP Client timer expiration function executes.</span></span> <span data-ttu-id="43c91-260">Den här funktionen uppdaterar alla tids gränser i DHCP-processen, t. ex. om meddelanden ska skickas om eller om DHCP-klientens tillstånd ändras.</span><span class="sxs-lookup"><span data-stu-id="43c91-260">This function updates all the timeouts in the DHCP process e.g. if messages should be retransmitted or DHCP Client state changed.</span></span> <span data-ttu-id="43c91-261">Som standard är det här värdet 1 sekund.</span><span class="sxs-lookup"><span data-stu-id="43c91-261">By default, this value is 1 second.</span></span>
- <span data-ttu-id="43c91-262">**NX_DHCP_OPTIONS_BUFFER_SIZE**: storleken på en buffert för DHCP-alternativ.</span><span class="sxs-lookup"><span data-stu-id="43c91-262">**NX_DHCP_OPTIONS_BUFFER_SIZE**: Size of DHCP options buffer.</span></span> <span data-ttu-id="43c91-263">Som standard är det här värdet 312 byte.</span><span class="sxs-lookup"><span data-stu-id="43c91-263">By default, this value is 312 bytes.</span></span>
- <span data-ttu-id="43c91-264">**NX_DHCP_PACKET_PAYLOAD**: anger storleken i byte för DHCP-klientens paket nytto Last.</span><span class="sxs-lookup"><span data-stu-id="43c91-264">**NX_DHCP_PACKET_PAYLOAD**: Specifies the size in bytes of the DHCP Client packet payload.</span></span> <span data-ttu-id="43c91-265">Standardvärdet är NX_DHCP_MINIMUM_IP_DATAGRAM + fysisk huvud storlek.</span><span class="sxs-lookup"><span data-stu-id="43c91-265">The default value is NX_DHCP_MINIMUM_IP_DATAGRAM + physical header size.</span></span> <span data-ttu-id="43c91-266">Storleken på det fysiska sidhuvudet i ett Wireline-nätverk är vanligt vis Ethernet-Rams storleken.</span><span class="sxs-lookup"><span data-stu-id="43c91-266">The physical header size in a wireline network is usually the Ethernet frame size.</span></span>
- <span data-ttu-id="43c91-267">**NX_DHCP_PACKET_POOL_SIZE**: anger storleken på DHCP-klientens adresspool.</span><span class="sxs-lookup"><span data-stu-id="43c91-267">**NX_DHCP_PACKET_POOL_SIZE**: Specifies the size of the DHCP Client packet pool.</span></span> <span data-ttu-id="43c91-268">Standardvärdet är (5 \* NX_DHCP_PACKET_PAYLOAD) som kommer att tillhandahålla fyra paket plus utrymme för att lägga till en intern paket pool.</span><span class="sxs-lookup"><span data-stu-id="43c91-268">The default value is (5 \*NX_DHCP_PACKET_PAYLOAD) which will provide four packets plus room for internal packet pool overhead.</span></span>
- <span data-ttu-id="43c91-269">**NX_DHCP_MIN_RETRANS_TIMEOUT**: anger det minsta vänte alternativet för att ta emot en DHCP-server svara på klient meddelande innan meddelandet överförs igen.</span><span class="sxs-lookup"><span data-stu-id="43c91-269">**NX_DHCP_MIN_RETRANS_TIMEOUT**: Specifies the minimum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="43c91-270">Standardvärdet är RFC 2131 rekommenderade 4 sekunder.</span><span class="sxs-lookup"><span data-stu-id="43c91-270">The default value is the RFC 2131 recommended 4 seconds.</span></span>
- <span data-ttu-id="43c91-271">**NX_DHCP_MAX_RETRANS_TIMEOUT**: anger det maximala vänte vänte alternativet för att ta emot en DHCP-server svara på klient meddelande innan meddelandet överförs igen.</span><span class="sxs-lookup"><span data-stu-id="43c91-271">**NX_DHCP_MAX_RETRANS_TIMEOUT**: Specifies the maximum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="43c91-272">Standardvärdet är 64 sekunder.</span><span class="sxs-lookup"><span data-stu-id="43c91-272">The default value is 64 seconds.</span></span>
- <span data-ttu-id="43c91-273">**NX_DHCP_MIN_RENEW_TIMEOUT**: anger minimalt vänte alternativ för att ta emot ett DHCP-server meddelande och skicka en FÖRNYELSEBEGÄRAN när DHCP-klienten är kopplad till en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="43c91-273">**NX_DHCP_MIN_RENEW_TIMEOUT**: Specifies minimum wait option for receiving a DHCP Server message and sending a renewal request after the DHCP Client is bound to an IP address.</span></span> <span data-ttu-id="43c91-274">Standardvärdet är 60 sekunder.</span><span class="sxs-lookup"><span data-stu-id="43c91-274">The default value is 60 seconds.</span></span> <span data-ttu-id="43c91-275">DHCP-klienten använder dock utgångs tiden för förnyelse och OMBINDNING från DHCP-servern innan standard tids gränsen för förnyelse används.</span><span class="sxs-lookup"><span data-stu-id="43c91-275">However, the DHCP Client uses the Renew and Rebind expiration times from the DHCP server message before defaulting to the minimum renew timeout.</span></span>
- <span data-ttu-id="43c91-276">**NX_DHCP_TYPE_OF_SERVICE**: typ av tjänst som krävs för DHCP UDP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="43c91-276">**NX_DHCP_TYPE_OF_SERVICE**: Type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="43c91-277">Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.</span><span class="sxs-lookup"><span data-stu-id="43c91-277">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="43c91-278">**NX_DHCP_FRAGMENT_OPTION**: fragment aktivera för DHCP UDP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="43c91-278">**NX_DHCP_FRAGMENT_OPTION**: Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="43c91-279">Som standard är det här värdet NX_DONT_FRAGMENT för att inaktivera DHCP UDP-fragmentering.</span><span class="sxs-lookup"><span data-stu-id="43c91-279">By default, this value is NX_DONT_FRAGMENT to disable DHCP UDP fragmenting.</span></span>
- <span data-ttu-id="43c91-280">**NX_DHCP_TIME_TO_LIVE**: anger antalet routrar som det här paketet kan passera innan det tas bort.</span><span class="sxs-lookup"><span data-stu-id="43c91-280">**NX_DHCP_TIME_TO_LIVE**: Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="43c91-281">Standardvärdet är inställt på 0x80.</span><span class="sxs-lookup"><span data-stu-id="43c91-281">The default value is set to 0x80.</span></span>
- <span data-ttu-id="43c91-282">**NX_DHCP_QUEUE_DEPTH**: anger antalet maximalt djup för mottagnings kön.</span><span class="sxs-lookup"><span data-stu-id="43c91-282">**NX_DHCP_QUEUE_DEPTH**: Specifies the number of maximum depth of receive queue.</span></span> <span data-ttu-id="43c91-283">Standardvärdet är inställt på 4.</span><span class="sxs-lookup"><span data-stu-id="43c91-283">The default value is set to 4.</span></span>