---
title: Kapitel 3 – konfigurations alternativ för Azure återställnings tider NetX Duo-DHCPv6
description: Det finns flera konfigurations alternativ för att skapa Azure återställnings tider NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5396b1c04581b5f79d337462368c4718ba9bb16
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826088"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a><span data-ttu-id="d1b98-103">Kapitel 3 – konfigurations alternativ för Azure återställnings tider NetX Duo-DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d1b98-103">Chapter 3 - Azure RTOS NetX Duo DHCPv6 configuration options</span></span>

<span data-ttu-id="d1b98-104">Det finns flera konfigurations alternativ för att skapa Azure återställnings tider NetX Duo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="d1b98-104">There are several configuration options for building Azure RTOS NetX Duo DHCPv6.</span></span> <span data-ttu-id="d1b98-105">I följande lista beskrivs var och en i detalj:</span><span class="sxs-lookup"><span data-stu-id="d1b98-105">The following list describes each in detail:</span></span>  
  
  
- <span data-ttu-id="d1b98-106">**NX_DHCPV6_THREAD_PRIORITY** Klient Trådens prioritet.</span><span class="sxs-lookup"><span data-stu-id="d1b98-106">**NX_DHCPV6_THREAD_PRIORITY** Priority of the Client thread.</span></span> <span data-ttu-id="d1b98-107">Som standard anger det här värdet att klient tråden körs vid prioritet 2.</span><span class="sxs-lookup"><span data-stu-id="d1b98-107">By   default, this value specifies that   the Client thread runs at priority   2.</span></span>

- <span data-ttu-id="d1b98-108">**NX_DHCPV6_MUTEX_WAIT** Timeout-alternativ för att hämta ett exklusivt lås på en DHCPv6-klients mutex.</span><span class="sxs-lookup"><span data-stu-id="d1b98-108">**NX_DHCPV6_MUTEX_WAIT** Time out option for obtaining an exclusive lock on a DHCPv6 Client mutex.</span></span> <span data-ttu-id="d1b98-109">Standardvärdet är TX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="d1b98-109">The default value is TX_WAIT_FOREVER.</span></span>

- <span data-ttu-id="d1b98-110">**NX_DHCPV6_TICKS_PER_SECOND** Förhållandet mellan Tick och sekunder.</span><span class="sxs-lookup"><span data-stu-id="d1b98-110">**NX_DHCPV6_TICKS_PER_SECOND** Ratio of ticks to seconds.</span></span> <span data-ttu-id="d1b98-111">Detta är processor beroende.</span><span class="sxs-lookup"><span data-stu-id="d1b98-111">This is processor dependent.</span></span> <span data-ttu-id="d1b98-112">Standardvärdet är 100.</span><span class="sxs-lookup"><span data-stu-id="d1b98-112">The default value is 100.</span></span>

- <span data-ttu-id="d1b98-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Tidsintervallet i sekunder då IP-tidsintervallet för IP-livstiden uppdaterar den tid som den aktuella IP-adressen har tilldelats till klienten.</span><span class="sxs-lookup"><span data-stu-id="d1b98-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Time interval in seconds at which the IP lifetime timer updates the length of time the current IP address has been assigned to the Client.</span></span> <span data-ttu-id="d1b98-114">Som standard är det här värdet 1.</span><span class="sxs-lookup"><span data-stu-id="d1b98-114">By default, this value is 1.</span></span>

- <span data-ttu-id="d1b98-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL**  Tidsintervall i sekunder då sessionens timer uppdaterar den tid som klienten har varit i sessionen att kommunicera med servern.</span><span class="sxs-lookup"><span data-stu-id="d1b98-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL**  Time interval in seconds at which the session timer updates the length of time the Client has been in session communicating with the Server.</span></span> <span data-ttu-id="d1b98-116">Som standard är det här värdet 1.</span><span class="sxs-lookup"><span data-stu-id="d1b98-116">By default, this value is 1.</span></span>

- <span data-ttu-id="d1b98-117">**NX_DHCPV6_MAX_IA_ADDRESS** Det maximala antalet IA-adresser som kan läggas till i klient posten.</span><span class="sxs-lookup"><span data-stu-id="d1b98-117">**NX_DHCPV6_MAX_IA_ADDRESS** The maximum number of IA addresses that can be added to the Client record.</span></span> <span data-ttu-id="d1b98-118">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="d1b98-118">The default value is 1.</span></span> 

- <span data-ttu-id="d1b98-119">**NX_DHCPV6_NUM_DNS_SERVERS** Antal DNS-servrar som ska lagras i klient posten.</span><span class="sxs-lookup"><span data-stu-id="d1b98-119">**NX_DHCPV6_NUM_DNS_SERVERS** Number of DNS servers to store to the client record.</span></span> <span data-ttu-id="d1b98-120">Standardvärdet är 2.</span><span class="sxs-lookup"><span data-stu-id="d1b98-120">The default value is 2.</span></span>

- <span data-ttu-id="d1b98-121">**NX_DHCPV6_NUM_TIME_SERVERS** Antal tids servrar som ska lagras i klient posten.</span><span class="sxs-lookup"><span data-stu-id="d1b98-121">**NX_DHCPV6_NUM_TIME_SERVERS** Number of time servers to store to the client record.</span></span> <span data-ttu-id="d1b98-122">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="d1b98-122">The default value is 1.</span></span>

- <span data-ttu-id="d1b98-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Storleken på bufferten i klient posten för att innehålla klientens nätverks domän namn.</span><span class="sxs-lookup"><span data-stu-id="d1b98-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Size of the buffer in the Client record to hold the client’s network domain name.</span></span> <span data-ttu-id="d1b98-124">Standardvärdet är 30.</span><span class="sxs-lookup"><span data-stu-id="d1b98-124">The default value is 30.</span></span>

- <span data-ttu-id="d1b98-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Storleken på bufferten i klient posten som ska innehålla klientens tidszon.</span><span class="sxs-lookup"><span data-stu-id="d1b98-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Size of the buffer in the Client record to hold the Client’s time zone.</span></span> <span data-ttu-id="d1b98-126">Standardvärdet är 10.</span><span class="sxs-lookup"><span data-stu-id="d1b98-126">The default value is 10.</span></span>

- <span data-ttu-id="d1b98-127">**NX_DHCPV6_MAX_MESSAGE_SIZE** Storleken på bufferten i klient posten för att innehålla alternativet status meddelande i ett Server svar.</span><span class="sxs-lookup"><span data-stu-id="d1b98-127">**NX_DHCPV6_MAX_MESSAGE_SIZE** Size of the buffer in the Client record to hold the option status message in a Server reply.</span></span> <span data-ttu-id="d1b98-128">Standardvärdet är 100 byte.</span><span class="sxs-lookup"><span data-stu-id="d1b98-128">The default value is 100 bytes.</span></span>

- <span data-ttu-id="d1b98-129">**NX_DHCPV6_PACKET_TIME_OUT** Tids gräns i sekunder för att allokera ett paket från klient paketets pool.</span><span class="sxs-lookup"><span data-stu-id="d1b98-129">**NX_DHCPV6_PACKET_TIME_OUT** Time out in seconds for allocating a packet from the Client packet pool.</span></span> <span data-ttu-id="d1b98-130">Standardvärdet är 3 sekunder.</span><span class="sxs-lookup"><span data-stu-id="d1b98-130">The default value is 3 seconds.</span></span>

- <span data-ttu-id="d1b98-131">**NX_DHCPV6_TYPE_OF_SERVICE** Detta definierar typ av tjänst för överföring av UDP-paket från DHCPv6-klientens socket.</span><span class="sxs-lookup"><span data-stu-id="d1b98-131">**NX_DHCPV6_TYPE_OF_SERVICE** This defines the type of service for UDP packet transmission from the DHCPv6 Client socket.</span></span> <span data-ttu-id="d1b98-132">Standardvärdet är **NX_IP_NORMAL**.</span><span class="sxs-lookup"><span data-stu-id="d1b98-132">The default value is **NX_IP_NORMAL**.</span></span>

- <span data-ttu-id="d1b98-133">**NX_DHCPV6_TIME_TO_LIVE** Antalet gånger som ett klient paket vidarebefordras av en Nätverks router innan paketet tas bort.</span><span class="sxs-lookup"><span data-stu-id="d1b98-133">**NX_DHCPV6_TIME_TO_LIVE** The number of times a Client packet is forwarded by a network router before the packet is discarded.</span></span> <span data-ttu-id="d1b98-134">Standardvärdet är 0x80.</span><span class="sxs-lookup"><span data-stu-id="d1b98-134">The default value is 0x80.</span></span>

- <span data-ttu-id="d1b98-135">**NX_DHCPV6_QUEUE_DEPTH** Anger antalet paket som ska behållas i klienten UDP socket Receive Queue innan NetX Duo tar bort paket.</span><span class="sxs-lookup"><span data-stu-id="d1b98-135">**NX_DHCPV6_QUEUE_DEPTH** Specifies the number of packets to keep in the Client UDP socket receive queue before NetX Duo discards packets.</span></span> <span data-ttu-id="d1b98-136">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="d1b98-136">The default value is 5.</span></span>

## <a name="dhcpv6-message-transmission"></a><span data-ttu-id="d1b98-137">DHCPv6-meddelande överföring</span><span class="sxs-lookup"><span data-stu-id="d1b98-137">DHCPv6 Message Transmission</span></span>

<span data-ttu-id="d1b98-138">Det finns en uppsättning DHCPv6-klient alternativ för att ange parametrar för överföring av DHCPv6-meddelanden.</span><span class="sxs-lookup"><span data-stu-id="d1b98-138">There are a set of DHCPv6 Client options for setting parameters on DHCPv6 message transmission.</span></span> <span data-ttu-id="d1b98-139">Dessa är:</span><span class="sxs-lookup"><span data-stu-id="d1b98-139">These are:</span></span> 

  - <span data-ttu-id="d1b98-140">Ursprunglig timeout</span><span class="sxs-lookup"><span data-stu-id="d1b98-140">initial timeout</span></span>

  - <span data-ttu-id="d1b98-141">maximal fördröjning vid första överföringen</span><span class="sxs-lookup"><span data-stu-id="d1b98-141">maximum delay on the first transmission</span></span>

  - <span data-ttu-id="d1b98-142">maximal timeout för återöverföring</span><span class="sxs-lookup"><span data-stu-id="d1b98-142">maximum retransmission timeout</span></span> 

  - <span data-ttu-id="d1b98-143">maximalt antal återöverföringar</span><span class="sxs-lookup"><span data-stu-id="d1b98-143">maximum number of retransmissions</span></span> 

  - <span data-ttu-id="d1b98-144">maximal varaktighet för att vänta på Server svar</span><span class="sxs-lookup"><span data-stu-id="d1b98-144">maximum duration to wait for server response</span></span>

<span data-ttu-id="d1b98-145">Dessa parametrar gäller för varje DHCPv6-klient meddelande:</span><span class="sxs-lookup"><span data-stu-id="d1b98-145">These parameters apply to each of the DHCPv6 Client messages:</span></span>

- <span data-ttu-id="d1b98-146">BE</span><span class="sxs-lookup"><span data-stu-id="d1b98-146">SOLICIT</span></span>

- <span data-ttu-id="d1b98-147">ANMODA</span><span class="sxs-lookup"><span data-stu-id="d1b98-147">REQUEST</span></span>

- <span data-ttu-id="d1b98-148">LÅNE</span><span class="sxs-lookup"><span data-stu-id="d1b98-148">RENEW</span></span>

- <span data-ttu-id="d1b98-149">OMBINDNING</span><span class="sxs-lookup"><span data-stu-id="d1b98-149">REBIND</span></span>

- <span data-ttu-id="d1b98-150">LANSERING</span><span class="sxs-lookup"><span data-stu-id="d1b98-150">RELEASE</span></span>

- <span data-ttu-id="d1b98-151">VÄGRAR</span><span class="sxs-lookup"><span data-stu-id="d1b98-151">DECLINE</span></span>

- <span data-ttu-id="d1b98-152">CONFIRM</span><span class="sxs-lookup"><span data-stu-id="d1b98-152">CONFIRM</span></span>

- <span data-ttu-id="d1b98-153">RÄTT</span><span class="sxs-lookup"><span data-stu-id="d1b98-153">INFORM</span></span>

<span data-ttu-id="d1b98-154">Följande är en fullständig lista över de konfigurerbara alternativen och deras standard</span><span class="sxs-lookup"><span data-stu-id="d1b98-154">The following is a complete list of these configurable options and their default</span></span> 

<span data-ttu-id="d1b98-155">values:</span><span class="sxs-lookup"><span data-stu-id="d1b98-155">values:</span></span>

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

<span data-ttu-id="d1b98-156">Om du inte vill ha någon gräns för en tids gräns för återöverföring anger du antalet återöverföringar för meddelanden till 0.</span><span class="sxs-lookup"><span data-stu-id="d1b98-156">For no limit on a retransmission timeout, set the message retransmission count to 0.</span></span> <span data-ttu-id="d1b98-157">Om du inte vill ha någon gräns för hur många gånger ett DHCPv6-klient meddelande ska skickas igen, anger du antalet återsändningar för meddelanden till 0.</span><span class="sxs-lookup"><span data-stu-id="d1b98-157">For no limit on the number of times a DHCPv6 Client message is retransmitted (retries), set the message retransmission count to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="d1b98-158">Oavsett tids gräns eller antal återförsök, tas den bort från IP-tabellen och kan inte längre användas av klienten när en giltig IPv6-adress går ut.</span><span class="sxs-lookup"><span data-stu-id="d1b98-158">Regardless of length of timeout or number of retries, when an IPv6 address valid lifetime expires, it is removed from the IP address table and can no longer be used by the Client.</span></span> <span data-ttu-id="d1b98-159">NetX Duo DHCPv6-klienten börjar automatiskt att skicka begär Anden som begär en ny IPv6-adress.</span><span class="sxs-lookup"><span data-stu-id="d1b98-159">The NetX Duo DHCPv6 Client will automatically begin sending SOLICIT messages requesting a new IPv6 address.</span></span>