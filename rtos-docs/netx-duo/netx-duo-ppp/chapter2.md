---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo Point-to-Point Protocol (PPP)
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo Point-to-Point Protocol-komponenten (PPP).
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2270a2668884dbecc8368d4ee130e419afa92491
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825827"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-point-to-point-protocol-ppp"></a><span data-ttu-id="6deda-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo Point-to-Point Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="6deda-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo Point-to-Point Protocol (PPP)</span></span>

<span data-ttu-id="6deda-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo Point-to-Point Protocol-komponenten (PPP).</span><span class="sxs-lookup"><span data-stu-id="6deda-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo Point-to-Point Protocol (PPP) component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="6deda-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="6deda-105">Product Distribution</span></span>

<span data-ttu-id="6deda-106">Azure återställnings tider NetX Duo Point-to-Point Protocol-paketet (PPP) finns på <https://github.com/azure-rtos/netxduo> .</span><span class="sxs-lookup"><span data-stu-id="6deda-106">The Azure RTOS NetX Duo Point-to-Point Protocol (PPP) package is available at <https://github.com/azure-rtos/netxduo>.</span></span> <span data-ttu-id="6deda-107">Paketet innehåller följande filer:</span><span class="sxs-lookup"><span data-stu-id="6deda-107">The package includes the following files:</span></span>

- <span data-ttu-id="6deda-108">**nx_ppp. h**: rubrik fil för PPP för netx</span><span class="sxs-lookup"><span data-stu-id="6deda-108">**nx_ppp.h**: Header file for PPP for NetX</span></span>
- <span data-ttu-id="6deda-109">**nx_ppp. c**: c-KÄLLFIL för PPP för netx</span><span class="sxs-lookup"><span data-stu-id="6deda-109">**nx_ppp.c**: C Source file for PPP for NetX</span></span>
- <span data-ttu-id="6deda-110">**nx_ppp.pdf**: PDF-Beskrivning av PPP för netx</span><span class="sxs-lookup"><span data-stu-id="6deda-110">**nx_ppp.pdf**: PDF description of PPP for NetX</span></span>
- <span data-ttu-id="6deda-111">**demo_netx_ppp. c**: netx PPP-demonstration</span><span class="sxs-lookup"><span data-stu-id="6deda-111">**demo_netx_ppp.c**: NetX PPP demonstration</span></span>

## <a name="ppp-installation"></a><span data-ttu-id="6deda-112">PPP-installation</span><span class="sxs-lookup"><span data-stu-id="6deda-112">PPP Installation</span></span>

<span data-ttu-id="6deda-113">För att du ska kunna använda PPP för NetX, ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX är installerat.</span><span class="sxs-lookup"><span data-stu-id="6deda-113">In order to use PPP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="6deda-114">Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*", ska *nx_ppp. h* -och *nx_ppp. c* -filerna kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="6deda-114">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_ppp.h* and *nx_ppp.c* files should be copied into this directory.</span></span>

## <a name="using-ppp"></a><span data-ttu-id="6deda-115">Använda PPP</span><span class="sxs-lookup"><span data-stu-id="6deda-115">Using PPP</span></span>

<span data-ttu-id="6deda-116">Det är enkelt att använda PPP för NetX.</span><span class="sxs-lookup"><span data-stu-id="6deda-116">Using PPP for NetX is easy.</span></span> <span data-ttu-id="6deda-117">I princip måste program koden innehålla *nx_ppp. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX respektive netx.</span><span class="sxs-lookup"><span data-stu-id="6deda-117">Basically, the application code must include *nx_ppp.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="6deda-118">När *nx_ppp. h* ingår kan program koden sedan göra de PPP-funktions anrop som anges längre fram i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="6deda-118">Once *nx_ppp.h* is included, the application code is then able to make the PPP function calls specified later in this guide.</span></span> <span data-ttu-id="6deda-119">Programmet måste även innehålla *nx_ppp. c* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="6deda-119">The application must also include *nx_ppp.c* in the build process.</span></span> <span data-ttu-id="6deda-120">Den här filen måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="6deda-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="6deda-121">Detta är allt som krävs för att använda NetX PPP.</span><span class="sxs-lookup"><span data-stu-id="6deda-121">This is all that is required to use NetX PPP.</span></span>

## <a name="using-modems"></a><span data-ttu-id="6deda-122">Använda modem</span><span class="sxs-lookup"><span data-stu-id="6deda-122">Using Modems</span></span>

<span data-ttu-id="6deda-123">Om ett modem krävs för anslutning till Internet krävs vissa särskilda överväganden för att kunna använda NetX-PPP-produkten.</span><span class="sxs-lookup"><span data-stu-id="6deda-123">If a modem is required for connection to the internet, some special considerations are required in order to use the NetX PPP product.</span></span> <span data-ttu-id="6deda-124">Med hjälp av ett modem införs i princip den ytterligare initierings logiken och logiken för att förlora kommunikationen.</span><span class="sxs-lookup"><span data-stu-id="6deda-124">Basically, using a modem introduces additional initialization logic and logic for loss of communication.</span></span> <span data-ttu-id="6deda-125">Dessutom utförs de flesta ytterligare modem logiken utanför kontexten för NetX PPP.</span><span class="sxs-lookup"><span data-stu-id="6deda-125">In addition, most of the additional modem logic is done outside the context of NetX PPP.</span></span> <span data-ttu-id="6deda-126">Det grundläggande flödet för att använda NetX PPP med ett modem ser ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="6deda-126">The basic flow of using the NetX PPP with a modem goes something like this:</span></span>

1. <span data-ttu-id="6deda-127">Initiera modem</span><span class="sxs-lookup"><span data-stu-id="6deda-127">Initialize Modem</span></span>

1. <span data-ttu-id="6deda-128">Ring Internet Service Provider (ISP)</span><span class="sxs-lookup"><span data-stu-id="6deda-128">Dial Internet Service Provider (ISP)</span></span>

1. <span data-ttu-id="6deda-129">Vänta på anslutning</span><span class="sxs-lookup"><span data-stu-id="6deda-129">Wait for Connection</span></span>

1. <span data-ttu-id="6deda-130">Vänta på UserID-prompt</span><span class="sxs-lookup"><span data-stu-id="6deda-130">Wait for UserID Prompt</span></span>

1. <span data-ttu-id="6deda-131">Starta NetX PPP [PPP i drift]</span><span class="sxs-lookup"><span data-stu-id="6deda-131">Start NetX PPP [PPP in operation]</span></span>

1. <span data-ttu-id="6deda-132">Förlust av kommunikation</span><span class="sxs-lookup"><span data-stu-id="6deda-132">Loss of Communication</span></span>

1. <span data-ttu-id="6deda-133">Stoppa NetX PPP (eller starta om via nx_ppp_restart)</span><span class="sxs-lookup"><span data-stu-id="6deda-133">Stop NetX PPP (or restart via nx_ppp_restart)</span></span>

### <a name="initialize-modem"></a><span data-ttu-id="6deda-134">Initiera modem</span><span class="sxs-lookup"><span data-stu-id="6deda-134">Initialize Modem</span></span>

<span data-ttu-id="6deda-135">Med hjälp av programmets lågnivå seriella utmatnings rutin initieras modemet via en serie ASCII-tecken kommandon (se modem dokumentationen för mer information).</span><span class="sxs-lookup"><span data-stu-id="6deda-135">Using the application’s low-level serial output routine, the modem is initialized via a series of ASCII character commands (see modem’s documentation for more details).</span></span>

### <a name="dial-internet-service-provider"></a><span data-ttu-id="6deda-136">Ring Internet tjänst leverantör</span><span class="sxs-lookup"><span data-stu-id="6deda-136">Dial Internet Service Provider</span></span>

<span data-ttu-id="6deda-137">Med hjälp av programmets lågnivå serie för seriella utdata uppmanas modemet att ringa upp Internet leverantören.</span><span class="sxs-lookup"><span data-stu-id="6deda-137">Using the application’s low-level serial output routine, the modem is instructed to dial the ISP.</span></span> <span data-ttu-id="6deda-138">Till exempel är följande typiska för en ASCII-sträng som används för att ringa upp en ISP på siffran 123-4567:</span><span class="sxs-lookup"><span data-stu-id="6deda-138">For example, the following is typical of an ASCII string used to dial an ISP at the number 123-4567:</span></span>

<span data-ttu-id="6deda-139">"ATDT123456\r"</span><span class="sxs-lookup"><span data-stu-id="6deda-139">“ATDT123456\r”</span></span>

### <a name="wait-for-connection"></a><span data-ttu-id="6deda-140">Vänta på anslutning</span><span class="sxs-lookup"><span data-stu-id="6deda-140">Wait for Connection</span></span>

<span data-ttu-id="6deda-141">I det här skedet väntar programmet på att ta emot indikationer från modemet som en anslutning har upprättats till.</span><span class="sxs-lookup"><span data-stu-id="6deda-141">At this point, the application waits to receive indication from the modem that a connection has been established.</span></span> <span data-ttu-id="6deda-142">Detta åstadkommer du genom att söka efter tecken från programmets lågnivå seriella Indatatyp.</span><span class="sxs-lookup"><span data-stu-id="6deda-142">This is accomplished by looking for characters from the application’s low-level serial input routine.</span></span> <span data-ttu-id="6deda-143">Vanligt vis returnerar modem en ASCII-sträng "CONNECT" när en anslutning har upprättats.</span><span class="sxs-lookup"><span data-stu-id="6deda-143">Typically, modems return an ASCII string “CONNECT” when a connection has been established.</span></span>

### <a name="wait-for-user-id-prompt"></a><span data-ttu-id="6deda-144">Vänta på användar-ID-prompt</span><span class="sxs-lookup"><span data-stu-id="6deda-144">Wait for User ID Prompt</span></span>

<span data-ttu-id="6deda-145">När anslutningen har upprättats måste programmet nu vänta på en första inloggningsbegäran från Internet leverantören.</span><span class="sxs-lookup"><span data-stu-id="6deda-145">Once the connection has been established, the application must now wait for an initial login request from the ISP.</span></span> <span data-ttu-id="6deda-146">Detta är vanligt vis formen av en ASCII-sträng som "inloggning?"</span><span class="sxs-lookup"><span data-stu-id="6deda-146">This typically takes the form of an ASCII string like “Login?”</span></span>

### <a name="start-netx-ppp"></a><span data-ttu-id="6deda-147">Starta NetX PPP</span><span class="sxs-lookup"><span data-stu-id="6deda-147">Start NetX PPP</span></span>

<span data-ttu-id="6deda-148">I det här läget kan NetX-PPP startas.</span><span class="sxs-lookup"><span data-stu-id="6deda-148">At this point, the NetX PPP can be started.</span></span> <span data-ttu-id="6deda-149">Detta åstadkommer du genom att anropa *nx_ppp_creates* tjänsten följt av *nx_ip_creates* tjänsten.</span><span class="sxs-lookup"><span data-stu-id="6deda-149">This is accomplished by calling the *nx_ppp_create* service followed by the *nx_ip_create* service.</span></span> <span data-ttu-id="6deda-150">Ytterligare tjänster för att aktivera PAP och för att konfigurera PPP-IP-adresser kan också krävas.</span><span class="sxs-lookup"><span data-stu-id="6deda-150">Additional services to enable PAP and to setup the PPP IP addresses might also be required.</span></span> <span data-ttu-id="6deda-151">Mer information finns i följande avsnitt i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="6deda-151">Please review the following sections of this guide for more information.</span></span>

### <a name="loss-of-communication"></a><span data-ttu-id="6deda-152">Förlust av kommunikation</span><span class="sxs-lookup"><span data-stu-id="6deda-152">Loss of Communication</span></span>

<span data-ttu-id="6deda-153">När PPP har startats skickas all icke-PPP-information till den "Ogiltig paket hantering"-rutinen som angetts till tjänsten *nx_ppp_create* .</span><span class="sxs-lookup"><span data-stu-id="6deda-153">Once PPP is started, any non-PPP information is passed to the “invalid packet handling” routine the application specified to the *nx_ppp_create* service.</span></span> <span data-ttu-id="6deda-154">Vanligt vis skickar modem en ASCII-sträng, till exempel "ingen BÄRVÅG" när kommunikationen går förlorad hos Internet leverantören.</span><span class="sxs-lookup"><span data-stu-id="6deda-154">Typically, modems send an ASCII string such as “NO CARRIER” when communication is lost with the ISP.</span></span> <span data-ttu-id="6deda-155">När programmet tar emot ett icke-PPP-paket med sådan information, bör det fortsätta att antingen stoppa NetX-PPP-instansen eller starta om datorn med PPP-tillstånd via *nx_ppp_restart* -API: et.</span><span class="sxs-lookup"><span data-stu-id="6deda-155">When the application receives a non-PPP packet with such information, it should proceed to either stop the NetX PPP instance or to restart the PPP state machine via the *nx_ppp_restart* API.</span></span>

### <a name="stop-netx-ppp"></a><span data-ttu-id="6deda-156">Stoppa NetX PPP</span><span class="sxs-lookup"><span data-stu-id="6deda-156">Stop NetX PPP</span></span>

<span data-ttu-id="6deda-157">Det är ganska enkelt att stoppa NetX-PPP.</span><span class="sxs-lookup"><span data-stu-id="6deda-157">Stopping the NetX PPP is fairly straightforward.</span></span> <span data-ttu-id="6deda-158">I princip måste alla skapade Sockets vara obundna och ta bort.</span><span class="sxs-lookup"><span data-stu-id="6deda-158">Basically, all created sockets must be unbound and deleted.</span></span> <span data-ttu-id="6deda-159">Ta sedan bort IP-instansen via tjänsten *nx_ip_delete* .</span><span class="sxs-lookup"><span data-stu-id="6deda-159">Next, delete the IP instance via the *nx_ip_delete* service.</span></span> <span data-ttu-id="6deda-160">När IP-instansen har tagits bort ska *nx_ppp_delete* -tjänsten anropas för att avsluta processen att stoppa PPP.</span><span class="sxs-lookup"><span data-stu-id="6deda-160">Once the IP instance is deleted, the *nx_ppp_delete* service should be called to finish the process of stopping PPP.</span></span> <span data-ttu-id="6deda-161">Nu kan programmet nu försöka återupprätta kommunikationen med Internet leverantören.</span><span class="sxs-lookup"><span data-stu-id="6deda-161">At this point, the application is now able to attempt to reestablish communication with the ISP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="6deda-162">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="6deda-162">Small Example System</span></span>

<span data-ttu-id="6deda-163">Ett exempel som illustrerar hur enkelt det är att använda NetX PPP beskrivs i bild 1,1 som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="6deda-163">An example that illustrates how easy it is to use NetX PPP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="6deda-164">I det här exemplet tas PPP-filen *nx_ppp. h* in på rad 3.</span><span class="sxs-lookup"><span data-stu-id="6deda-164">In this example, the PPP include file *nx_ppp.h* is brought in at line 3.</span></span> <span data-ttu-id="6deda-165">Därefter skapas PPP i *"tx_application_define*" på rad 56.</span><span class="sxs-lookup"><span data-stu-id="6deda-165">Next, PPP is created in *”tx_application_define*” at line 56.</span></span> <span data-ttu-id="6deda-166">PPP-kontroll blocket "*my_ppp*" definierades som en global variabel på rad 9 tidigare.</span><span class="sxs-lookup"><span data-stu-id="6deda-166">The PPP control block “*my_ppp*” was defined as a global variable at line 9 previously.</span></span> 

>[!NOTE]
><span data-ttu-id="6deda-167">PPP bör skapas innan du skapar IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="6deda-167">PPP should be created prior to creating the IP instance.</span></span> <span data-ttu-id="6deda-168">När du har skapat PPP och IP väntar tråden "*my_thread*" på att PPP-länken ska komma i rad 98.</span><span class="sxs-lookup"><span data-stu-id="6deda-168">After successful creation of PPP and IP, the thread “*my_thread*” waits for the PPP link to come alive at line 98.</span></span> <span data-ttu-id="6deda-169">På rad 104 är både PPP och NetX fullt operativa.</span><span class="sxs-lookup"><span data-stu-id="6deda-169">At line 104, both PPP and NetX are fully operational.</span></span>

<span data-ttu-id="6deda-170">Det element som inte visas i det här exemplet är programmets serie byte erhåller ISR.</span><span class="sxs-lookup"><span data-stu-id="6deda-170">The one item not shown in this example is the application’s serial byte receive ISR.</span></span> <span data-ttu-id="6deda-171">Det måste anropa *nx_ppp_byte_receive* med "*my_ppp*" och mottagna byte som indataparametrar.</span><span class="sxs-lookup"><span data-stu-id="6deda-171">It will need to call *nx_ppp_byte_receive* with “*my_ppp*” and the byte received as input parameters.</span></span>

```c
0001 #include   "tx_api.h"
0002 #include   "nx_api.h"
0003 #include   "nx_ppp.h"
0004
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
## <a name="configuration-options"></a><span data-ttu-id="6deda-172">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="6deda-172">Configuration Options</span></span>

<span data-ttu-id="6deda-173">Det finns flera konfigurations alternativ för att skapa PPP för NetX.</span><span class="sxs-lookup"><span data-stu-id="6deda-173">There are several configuration options for building PPP for NetX.</span></span> <span data-ttu-id="6deda-174">I följande lista beskrivs var och en i detalj:</span><span class="sxs-lookup"><span data-stu-id="6deda-174">The following list describes each in detail:</span></span>

- <span data-ttu-id="6deda-175">**NX_DISABLE_ERROR_CHECKING**: det här alternativet tar bort grundläggande fel sökning av PPP.</span><span class="sxs-lookup"><span data-stu-id="6deda-175">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic PPP error checking.</span></span> <span data-ttu-id="6deda-176">Den används vanligt vis när programmet har felsökts.</span><span class="sxs-lookup"><span data-stu-id="6deda-176">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="6deda-177">**NX_PPP_PPPOE_ENABLE**: om det är DEFINIERAT kan PPP överföra paket över Ethernet</span><span class="sxs-lookup"><span data-stu-id="6deda-177">**NX_PPP_PPPOE_ENABLE**: If defined, PPP can transmit packet over Ethernet</span></span>
- <span data-ttu-id="6deda-178">**NX_PPP_BASE_TIMEOUT**: Detta definierar period frekvensen (i timer-Tick) som PPP-trådens aktivitet är aktive för att söka efter PPP-händelser.</span><span class="sxs-lookup"><span data-stu-id="6deda-178">**NX_PPP_BASE_TIMEOUT**: This defines the period rate (in timer ticks) that the PPP thread task is woken to check for PPP events.</span></span> <span data-ttu-id="6deda-179">Standardvärdet är 1 \* NX_IP_PERIODIC_RATE (100 Tick).</span><span class="sxs-lookup"><span data-stu-id="6deda-179">The default value is 1\*NX_IP_PERIODIC_RATE (100 ticks).</span></span>
- <span data-ttu-id="6deda-180">**NX_PPP_DISABLE_INFO**: om det här är definierat inaktive ras intern insamling av PPP-information.</span><span class="sxs-lookup"><span data-stu-id="6deda-180">**NX_PPP_DISABLE_INFO**: If defined, internal PPP information gathering is disabled.</span></span>
- <span data-ttu-id="6deda-181">**NX_PPP_DEBUG_LOG_ENABLE**: om den har definierats är intern PPP-felsökning aktive rad.</span><span class="sxs-lookup"><span data-stu-id="6deda-181">**NX_PPP_DEBUG_LOG_ENABLE**: If defined, internal PPP debug log is enabled.</span></span>
- <span data-ttu-id="6deda-182">**NX_PPP_DEBUG_LOG_PRINT_ENABLE**: om det är definierat är den interna PPP-felsöknings loggen *printf* till *Stdio* aktive rad.</span><span class="sxs-lookup"><span data-stu-id="6deda-182">**NX_PPP_DEBUG_LOG_PRINT_ENABLE**:If defined, internal PPP debug log *printf* to *stdio* is enabled.</span></span> <span data-ttu-id="6deda-183">Detta är endast giltigt om fel söknings loggen också är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="6deda-183">This is only valid if the debug log is also enabled.</span></span>
- <span data-ttu-id="6deda-184">**NX_PPP_DEBUG_LOG_SIZE**: storleken på fel söknings loggen (antalet poster i fel söknings loggen).</span><span class="sxs-lookup"><span data-stu-id="6deda-184">**NX_PPP_DEBUG_LOG_SIZE**: Size of debug log (number of entries in the debug log).</span></span> <span data-ttu-id="6deda-185">När den senaste posten hamnade, radbryts fel söknings avbildningen till den första posten och skriver över alla data som tidigare har registrerats.</span><span class="sxs-lookup"><span data-stu-id="6deda-185">On reaching the last entry, the debug capture wraps to the first entry and overwrites any data previously captured.</span></span> <span data-ttu-id="6deda-186">Standardvärdet är 50.</span><span class="sxs-lookup"><span data-stu-id="6deda-186">The default value is 50.</span></span>
- <span data-ttu-id="6deda-187">**NX_PPP_DEBUG_FRAME_SIZE**: maximal mängd data som samlas in från en mottagen paket nytto last och sparas i fel söknings utdata.</span><span class="sxs-lookup"><span data-stu-id="6deda-187">**NX_PPP_DEBUG_FRAME_SIZE**: Maximum amount of data captured from a received packet payload and saved to debug output.</span></span> <span data-ttu-id="6deda-188">Standardvärdet är 50.</span><span class="sxs-lookup"><span data-stu-id="6deda-188">The default value is 50.</span></span>
- <span data-ttu-id="6deda-189">**NX_PPP_DISABLE_CHAP**: om det är definierat tas intern PPP CHAP-logik bort, inklusive MD5 Digest-logiken.</span><span class="sxs-lookup"><span data-stu-id="6deda-189">**NX_PPP_DISABLE_CHAP**: If defined, internal PPP CHAP logic is removed, including the MD5 digest logic.</span></span>
- <span data-ttu-id="6deda-190">**NX_PPP_DISABLE_PAP**: om det är definierat tas intern PPP PAP-logik bort.</span><span class="sxs-lookup"><span data-stu-id="6deda-190">**NX_PPP_DISABLE_PAP**: If defined, internal PPP PAP logic is removed.</span></span>
- <span data-ttu-id="6deda-191">**NX_PPP_DNS_OPTION_DISABLE**: om det är definierat inaktive ras alternativet primär DNS-server i IPCP-svaret.</span><span class="sxs-lookup"><span data-stu-id="6deda-191">**NX_PPP_DNS_OPTION_DISABLE**: If defined, the primary DNS Server Option is disabled in the IPCP response.</span></span> <span data-ttu-id="6deda-192">Som standard är det här alternativet inte definierat.</span><span class="sxs-lookup"><span data-stu-id="6deda-192">By default this option is not defined.</span></span>
- <span data-ttu-id="6deda-193">**NX_PPP_DNS_ADDRESS_MAX_RETRIES**: Detta anger hur många gånger PPP-värden ska begära en DNS-serveradress från peer-datorn i IPCP-tillstånd.</span><span class="sxs-lookup"><span data-stu-id="6deda-193">**NX_PPP_DNS_ADDRESS_MAX_RETRIES**: This specifies how many times the PPP host will request a DNS Server address from the peer in the IPCP state.</span></span> <span data-ttu-id="6deda-194">Detta har ingen påverkan om NX_PPP_DNS_OPTION_DISABLE har definierats.</span><span class="sxs-lookup"><span data-stu-id="6deda-194">This has no effect if NX_PPP_DNS_OPTION_DISABLE is defined.</span></span> <span data-ttu-id="6deda-195">Standardvärdet är 2.</span><span class="sxs-lookup"><span data-stu-id="6deda-195">The default value is 2.</span></span>
- <span data-ttu-id="6deda-196">**NX_PPP_HASHED_VALUE_SIZE**: anger storleken på "hashed Value"-strängar som används i CHAP-autentisering.</span><span class="sxs-lookup"><span data-stu-id="6deda-196">**NX_PPP_HASHED_VALUE_SIZE**: Specifies the size of “hashed value” strings used in CHAP authentication.</span></span> <span data-ttu-id="6deda-197">Standardvärdet är inställt på 16 byte, men kan omdefinieras innan *nx_ppp. h.*</span><span class="sxs-lookup"><span data-stu-id="6deda-197">The default value is set to 16 bytes, but can be redefined prior to inclusion of *nx_ppp.h.*</span></span>
- <span data-ttu-id="6deda-198">**NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: Detta definierar Max antalet återförsök om PPP-tiden överskrids innan en annan LCP-konfiguration begär ett meddelande skickas.</span><span class="sxs-lookup"><span data-stu-id="6deda-198">**NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another LCP configure request message.</span></span> <span data-ttu-id="6deda-199">När det här talet nås avbryts PPP-handskakningen och länkens status är nere.</span><span class="sxs-lookup"><span data-stu-id="6deda-199">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="6deda-200">Standardvärdet är 20.</span><span class="sxs-lookup"><span data-stu-id="6deda-200">The default value is 20.</span></span>
- <span data-ttu-id="6deda-201">**NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: Detta definierar Max antalet återförsök om PPP-tiden överskrids innan ett annat meddelande om PAP-autentiseringsbegäran skickas.</span><span class="sxs-lookup"><span data-stu-id="6deda-201">**NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another PAP authentication request message.</span></span> <span data-ttu-id="6deda-202">När det här talet nås avbryts PPP-handskakningen och länkens status är nere.</span><span class="sxs-lookup"><span data-stu-id="6deda-202">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="6deda-203">Standardvärdet är 20.</span><span class="sxs-lookup"><span data-stu-id="6deda-203">The default value is 20.</span></span>
- <span data-ttu-id="6deda-204">**NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: Detta definierar Max antalet återförsök om PPP-tiden överskrids innan ett annat CHAP-utmanings meddelande skickas.</span><span class="sxs-lookup"><span data-stu-id="6deda-204">**NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another CHAP challenge message.</span></span> <span data-ttu-id="6deda-205">När det här talet nås avbryts PPP-handskakningen och länkens status är nere.</span><span class="sxs-lookup"><span data-stu-id="6deda-205">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="6deda-206">Standardvärdet är 20.</span><span class="sxs-lookup"><span data-stu-id="6deda-206">The default value is 20.</span></span>
- <span data-ttu-id="6deda-207">**NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: Detta definierar Max antalet återförsök om PPP-tiden överskrids innan en annan IPCP-konfiguration skickas.</span><span class="sxs-lookup"><span data-stu-id="6deda-207">**NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another IPCP configure request message.</span></span> <span data-ttu-id="6deda-208">När det här talet nås avbryts PPP-handskakningen och länkens status är nere.</span><span class="sxs-lookup"><span data-stu-id="6deda-208">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="6deda-209">Standardvärdet är 20.</span><span class="sxs-lookup"><span data-stu-id="6deda-209">The default value is 20.</span></span>
- <span data-ttu-id="6deda-210">**NX_PPP_MRU**: anger den maximala mottagnings enheten (MRU) för PPP.</span><span class="sxs-lookup"><span data-stu-id="6deda-210">**NX_PPP_MRU**: Specifies the Maximum Receive Unit (MRU) for PPP.</span></span> <span data-ttu-id="6deda-211">Som standard är det här värdet 1 500 byte (minimivärdet).</span><span class="sxs-lookup"><span data-stu-id="6deda-211">By default, this value is 1,500 bytes (the minimum value).</span></span> <span data-ttu-id="6deda-212">Den här inställningen kan anges av programmet innan *nx_ppp. h*.</span><span class="sxs-lookup"><span data-stu-id="6deda-212">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="6deda-213">**NX_PPP_MINIMUM_MRU**: anger det lägsta MRU som tas emot i ett LCP-meddelande om att konfigurera begär Anden.</span><span class="sxs-lookup"><span data-stu-id="6deda-213">**NX_PPP_MINIMUM_MRU**: Specifies the minimum MRU received in an LCP configure request message.</span></span> <span data-ttu-id="6deda-214">Som standard är det här värdet 1 500 byte (minimivärdet).</span><span class="sxs-lookup"><span data-stu-id="6deda-214">By default, this value is 1,500 bytes (the minimum value).</span></span> <span data-ttu-id="6deda-215">Den här inställningen kan anges av programmet innan *nx_ppp. h*.</span><span class="sxs-lookup"><span data-stu-id="6deda-215">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="6deda-216">**NX_PPP_NAME_SIZE**: anger storleken på "namn"-strängar som används vid autentisering.</span><span class="sxs-lookup"><span data-stu-id="6deda-216">**NX_PPP_NAME_SIZE**: Specifies the size of “name” strings used in authentication.</span></span> <span data-ttu-id="6deda-217">Standardvärdet är inställt på 32bytes, men kan definieras om innan inkludering av \* nx_ppp. h.</span><span class="sxs-lookup"><span data-stu-id="6deda-217">The default value is set to 32bytes, but can be redefined prior to inclusion of \*nx_ppp.h.</span></span>
- <span data-ttu-id="6deda-218">**NX_PPP_PASSWORD_SIZE**: anger storleken på "Password"-strängar som används i autentisering.</span><span class="sxs-lookup"><span data-stu-id="6deda-218">**NX_PPP_PASSWORD_SIZE**: Specifies the size of “password” strings used in authentication.</span></span> <span data-ttu-id="6deda-219">Standardvärdet är inställt på 32bytes, men kan omdefinieras innan du tar med *nx_ppp. h.*</span><span class="sxs-lookup"><span data-stu-id="6deda-219">The default value is set to 32bytes, but can be redefined prior to inclusion of *nx_ppp.h.*</span></span>
- <span data-ttu-id="6deda-220">**NX_PPP_PROTOCOL_TIMEOUT**: Detta definierar vänte alternativet (i sekunder) för att PPP-aktiviteten ska ta emot ett svar på ett meddelande om PPP-protokoll begär Ande.</span><span class="sxs-lookup"><span data-stu-id="6deda-220">**NX_PPP_PROTOCOL_TIMEOUT**: This defines the wait option (in seconds) for the PPP task to receive a response to a PPP protocol request message.</span></span> <span data-ttu-id="6deda-221">Standardvärdet är 4 sekunder.</span><span class="sxs-lookup"><span data-stu-id="6deda-221">The default value is 4 seconds.</span></span>
- <span data-ttu-id="6deda-222">**NX_PPP_RECEIVE_TIMEOUTS**: Detta definierar antalet gånger som en tids gräns i PPP-tråden väntar på att ta emot nästa-tecknen i en PPP-meddelande ström.</span><span class="sxs-lookup"><span data-stu-id="6deda-222">**NX_PPP_RECEIVE_TIMEOUTS**: This defines the number of times the PPP thread task times out waiting to receive the next character in a PPP message stream.</span></span> <span data-ttu-id="6deda-223">Därefter släpper PPP paketet och börjar vänta på att ta emot nästa PPP-meddelande.</span><span class="sxs-lookup"><span data-stu-id="6deda-223">Thereafter, PPP releases the packet and begins waiting to receive the next PPP message.</span></span> <span data-ttu-id="6deda-224">Standardvärdet är 4.</span><span class="sxs-lookup"><span data-stu-id="6deda-224">The default value is 4.</span></span>
- <span data-ttu-id="6deda-225">**NX_PPP_SERIAL_BUFFER_SIZE**: anger storleken på den seriella bufferten för mottagnings tecknen.</span><span class="sxs-lookup"><span data-stu-id="6deda-225">**NX_PPP_SERIAL_BUFFER_SIZE**: Specifies the size of the receive character serial buffer.</span></span> <span data-ttu-id="6deda-226">Som standard är det här värdet 3 000 byte.</span><span class="sxs-lookup"><span data-stu-id="6deda-226">By default, this value is 3,000 bytes.</span></span> <span data-ttu-id="6deda-227">Den här inställningen kan anges av programmet innan *nx_ppp. h*.</span><span class="sxs-lookup"><span data-stu-id="6deda-227">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="6deda-228">**NX_PPP_TIMEOUT**: Detta definierar vänte alternativet (i timer-Tick) för att allokera paket för att överföra data och buffra PPP-Datadata till paket som ska skickas till IP-lagret.</span><span class="sxs-lookup"><span data-stu-id="6deda-228">**NX_PPP_TIMEOUT**: This defines the wait option (in timer ticks) for allocating packets to transmit data as well as buffer PPP serial data into packets to send to the IP layer.</span></span> <span data-ttu-id="6deda-229">Standardvärdet är 4 \* NX_IP_PERIODIC_RATE (400 Tick).</span><span class="sxs-lookup"><span data-stu-id="6deda-229">The default value is 4\*NX_IP_PERIODIC_RATE (400 ticks).</span></span>
- <span data-ttu-id="6deda-230">**NX_PPP_THREAD_TIME_SLICE**: Time-slice-alternativ för PPP-trådar.</span><span class="sxs-lookup"><span data-stu-id="6deda-230">**NX_PPP_THREAD_TIME_SLICE**: Time-slice option for PPP threads.</span></span> <span data-ttu-id="6deda-231">Som standard är det här värdet TX_NO_TIME_SLICE.</span><span class="sxs-lookup"><span data-stu-id="6deda-231">By default, this value is TX_NO_TIME_SLICE.</span></span> <span data-ttu-id="6deda-232">Den här inställningen kan anges av programmet innan *nx_ppp. h*.</span><span class="sxs-lookup"><span data-stu-id="6deda-232">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="6deda-233">**NX_PPP_VALUE_SIZE**: anger storleken på "värde"-strängar som används i CHAP-autentisering.</span><span class="sxs-lookup"><span data-stu-id="6deda-233">**NX_PPP_VALUE_SIZE**: Specifies the size of “value” strings used in CHAP authentication.</span></span> <span data-ttu-id="6deda-234">Standardvärdet är inställt på 32bytes, men kan omdefinieras innan du tar med nx_ppp. h.</span><span class="sxs-lookup"><span data-stu-id="6deda-234">The default value is set to 32bytes, but can be redefined prior to inclusion of nx_ppp.h.</span></span>