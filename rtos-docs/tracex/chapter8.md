---
title: Kapitel 8 – Azure återställnings tider NetX trace Events
description: Det här kapitlet innehåller en beskrivning av Azure återställnings tider NetX-händelser.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: ce355d86d7db0b7e259ae58e306d990277b77a8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828353"
---
# <a name="chapter-8---azure-rtos-netx-trace-events"></a><span data-ttu-id="0f9f0-103">Kapitel 8 – Azure återställnings tider NetX trace Events</span><span class="sxs-lookup"><span data-stu-id="0f9f0-103">Chapter 8 - Azure RTOS NetX trace events</span></span>

<span data-ttu-id="0f9f0-104">Det här kapitlet innehåller en beskrivning av Azure återställnings tider NetX-händelser.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-104">This chapter contains a description of the Azure RTOS NetX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="0f9f0-105">Lista över händelser och ikoner</span><span class="sxs-lookup"><span data-stu-id="0f9f0-105">List of Events and Icons</span></span>

<span data-ttu-id="0f9f0-106">Följande är en lista över NetX-händelser som visas av TraceX.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-106">The following is a list of NetX events displayed by TraceX.</span></span>

| <span data-ttu-id="0f9f0-107">Ikon</span><span class="sxs-lookup"><span data-stu-id="0f9f0-107">Icon</span></span>                                           | <span data-ttu-id="0f9f0-108">Innebörd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-108">Meaning</span></span>                 |
| -------------------------------- | ------------------------------------- |
| ![Intern A R P P-ikon för mottagnings förfrågan](./media/user-guide/netx-events/image1.png)    | <span data-ttu-id="0f9f0-110">Mottagning av intern ARP-begäran</span><span class="sxs-lookup"><span data-stu-id="0f9f0-110">Internal ARP Request Receive</span></span> |
| ![Intern A R P P-ikon för att skicka förfrågan](./media/user-guide/netx-events/image2.png)    | <span data-ttu-id="0f9f0-112">Skicka intern ARP-begäran</span><span class="sxs-lookup"><span data-stu-id="0f9f0-112">Internal ARP Request Send</span></span> |
| ![Intern A R P-ikon för svars mottagning](./media/user-guide/netx-events/image3.png)    | <span data-ttu-id="0f9f0-114">Mottagna interna ARP-svar</span><span class="sxs-lookup"><span data-stu-id="0f9f0-114">Internal ARP Response Receive</span></span> |
| ![Intern A R P P svar ikon för skicka](./media/user-guide/netx-events/image4.png)    | <span data-ttu-id="0f9f0-116">Skicka internt ARP-svar</span><span class="sxs-lookup"><span data-stu-id="0f9f0-116">Internal ARP Response Send</span></span> |
| ![Intern I C M P-ikon för mottagning](./media/user-guide/netx-events/image5.png)    | <span data-ttu-id="0f9f0-118">Internt ICMP-mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-118">Internal ICMP Receive</span></span> |
| ![Intern I/P e P skicka-ikon](./media/user-guide/netx-events/image6.png)    | <span data-ttu-id="0f9f0-120">Intern ICMP-sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-120">Internal ICMP Send</span></span> |
| ![Intern NetX I G M P-ikon](./media/user-guide/netx-events/image7.png)    | <span data-ttu-id="0f9f0-122">Internt NetX IGMP Receive</span><span class="sxs-lookup"><span data-stu-id="0f9f0-122">Internal NetX IGMP Receive</span></span> |
| ![Intern I/e-ikon](./media/user-guide/netx-events/image8.png)    | <span data-ttu-id="0f9f0-124">Ta emot internt IP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-124">Internal IP Receive</span></span> |
| ![Intern I/e-ikon](./media/user-guide/netx-events/image9.png)    | <span data-ttu-id="0f9f0-126">Skicka intern IP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-126">Internal IP Send</span></span> |
| ![Intern T C P data Receive-ikon](./media/user-guide/netx-events/image10.png)    | <span data-ttu-id="0f9f0-128">Mottagna interna TCP-data</span><span class="sxs-lookup"><span data-stu-id="0f9f0-128">Internal TCP Data Receive</span></span> |
| ![Inbyggt T C P data Send-ikon](./media/user-guide/netx-events/image11.png)    | <span data-ttu-id="0f9f0-130">Intern TCP-data överföring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-130">Internal TCP Data Send</span></span> |
| ![Intern T C P P-mottagnings ikon](./media/user-guide/netx-events/image12.png)    | <span data-ttu-id="0f9f0-132">Intern TCP FIN mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-132">Internal TCP FIN Receive</span></span> |
| ![Inbyggt T C P F I N skicka ikon](./media/user-guide/netx-events/image13.png)    | <span data-ttu-id="0f9f0-134">Intern TCP RÄNTETRANS-sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-134">Internal TCP FIN Send</span></span> |
| ![Inbyggt T C P R S T Inleverera-ikon](./media/user-guide/netx-events/image14.png)    | <span data-ttu-id="0f9f0-136">Internt TCP-mottagna</span><span class="sxs-lookup"><span data-stu-id="0f9f0-136">Internal TCP RST Receive</span></span> |
| ![Intern T R P R S T skicka-ikon](./media/user-guide/netx-events/image15.png)    | <span data-ttu-id="0f9f0-138">Intern TCP-överföring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-138">Internal TCP RST Send</span></span> |
| ![Ikon för intern T C P S Y N-mottagning](./media/user-guide/netx-events/image16.png)    | <span data-ttu-id="0f9f0-140">Ta emot internt TCP-SYN</span><span class="sxs-lookup"><span data-stu-id="0f9f0-140">Internal TCP SYN Receive</span></span> |
| ![Intern T C P S Y N skicka-ikon](./media/user-guide/netx-events/image17.png)    | <span data-ttu-id="0f9f0-142">Skicka internt TCP-SYN</span><span class="sxs-lookup"><span data-stu-id="0f9f0-142">Internal TCP SYN Send</span></span> |
| ![Intern U D P-mottagnings ikon](./media/user-guide/netx-events/image18.png)    | <span data-ttu-id="0f9f0-144">Internt UDP-mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-144">Internal UDP Receive</span></span> |
| ![Intern U D P-skicka-ikon](./media/user-guide/netx-events/image19.png)    | <span data-ttu-id="0f9f0-146">Intern UDP-sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-146">Internal UDP Send</span></span> |
| ![Intern R A R P-ikon för mottagning](./media/user-guide/netx-events/image20.png)    | <span data-ttu-id="0f9f0-148">Intern RARP-mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-148">Internal RARP Receive</span></span> |
| ![Interna R A R P-ikonen skicka](./media/user-guide/netx-events/image21.png)    | <span data-ttu-id="0f9f0-150">Intern RARP-sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-150">Internal RARP Send</span></span> |
| ![Inbyggt T C P-återförsök-ikon](./media/user-guide/netx-events/image22.png)    | <span data-ttu-id="0f9f0-152">Internt TCP-försök</span><span class="sxs-lookup"><span data-stu-id="0f9f0-152">Internal TCP Retry</span></span> |
| ![Ändrings ikon för den interna T C P-statusen](./media/user-guide/netx-events/image23.png)    | <span data-ttu-id="0f9f0-154">Intern TCP-tillstånds ändring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-154">Internal TCP State Change</span></span> |
| ![Ikon för att skicka intern I/O-drivrutin](./media/user-guide/netx-events/image24.png)    | <span data-ttu-id="0f9f0-156">Skicka internt I/O-drivrutins paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-156">Internal I/O Driver Packet Send</span></span> |
| ![storleken på](./media/user-guide/netx-events/image25.png)    | <span data-ttu-id="0f9f0-158">Intern I/O-drivrutin initieras</span><span class="sxs-lookup"><span data-stu-id="0f9f0-158">Internal I/O Driver Initialize</span></span> |
| ![Initiera ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image26.png)    | <span data-ttu-id="0f9f0-160">Intern I/O driv Rutins länk aktivera</span><span class="sxs-lookup"><span data-stu-id="0f9f0-160">Internal I/O Driver Link Enable</span></span> |
| ![Ikon för inaktive ring av intern I/O-drivrutin](./media/user-guide/netx-events/image27.png)    | <span data-ttu-id="0f9f0-162">Inaktivera intern I/O driv Rutins länk</span><span class="sxs-lookup"><span data-stu-id="0f9f0-162">Internal I/O Driver Link Disable</span></span> |
| ![Ikon för intern I/O-drivrutin för driv Rutins paket](./media/user-guide/netx-events/image28.png)    | <span data-ttu-id="0f9f0-164">Intern I/O-drivrutins paket sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-164">Internal I/O Driver Packet Broadcast</span></span> |
| ![Skicka ikon för intern I/O-drivrutins-ARP](./media/user-guide/netx-events/image29.png)    | <span data-ttu-id="0f9f0-166">Överföring av intern I/O-drivrutins-ARP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-166">Internal I/O Driver ARP Send</span></span> |
| ![Intern I/O-drivrutin för ARP-svar skicka ikon](./media/user-guide/netx-events/image30.png)    | <span data-ttu-id="0f9f0-168">Intern I/O-drivrutin ARP-svar skicka</span><span class="sxs-lookup"><span data-stu-id="0f9f0-168">Internal I/O Driver ARP Response Send</span></span> |
| ![Intern I/O driv rutin RARP skicka ikon](./media/user-guide/netx-events/image31.png)    | <span data-ttu-id="0f9f0-170">Intern I/O-drivrutin RARP skicka</span><span class="sxs-lookup"><span data-stu-id="0f9f0-170">Internal I/O Driver RARP Send</span></span> |
| ![Ikon för multicast-anslutning för intern I/O-drivrutin](./media/user-guide/netx-events/image32.png)    | <span data-ttu-id="0f9f0-172">Intern I/O-drivrutin multicast-anslutning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-172">Internal I/O Driver Multicast Join</span></span> |
| ![Ikon för multicast för intern I/O-drivrutin](./media/user-guide/netx-events/image33.png)    | <span data-ttu-id="0f9f0-174">Intern I/O-drivrutin för multicast-ledighet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-174">Internal I/O Driver Multicast Leave</span></span> |
| ![Status ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image34.png)    | <span data-ttu-id="0f9f0-176">Status för intern I/O-drivrutin för hämtning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-176">Internal I/O Driver Get Status</span></span> |
| ![Intern I/O driv rutin Hämta hastighets ikon](./media/user-guide/netx-events/image35.png)    | <span data-ttu-id="0f9f0-178">Intern I/O-drivrutin Hämta hastighet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-178">Internal I/O Driver Get Speed</span></span> |
| ![Intern I/O-drivrutin Hämta duplex-typ ikon](./media/user-guide/netx-events/image36.png)    | <span data-ttu-id="0f9f0-180">Intern I/O-drivrutin Hämta duplex-typ</span><span class="sxs-lookup"><span data-stu-id="0f9f0-180">Internal I/O Driver Get Duplex Type</span></span> |
| ![Ikon för Hämta fel antal för intern I/O-drivrutin](./media/user-guide/netx-events/image37.png)    | <span data-ttu-id="0f9f0-182">Fel antal för intern I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="0f9f0-182">Internal I/O Driver Get Error Count</span></span> |
| ![Intern I/O-drivrutin Hämta RX-ikon](./media/user-guide/netx-events/image38.png)    | <span data-ttu-id="0f9f0-184">Intern I/O-drivrutin Hämta RX-antal</span><span class="sxs-lookup"><span data-stu-id="0f9f0-184">Internal I/O Driver Get RX Count</span></span> |
| ![Intern I/O-drivrutin för Hämta TX-antal](./media/user-guide/netx-events/image39.png)    | <span data-ttu-id="0f9f0-186">Intern I/O-drivrutin Hämta TX-antal</span><span class="sxs-lookup"><span data-stu-id="0f9f0-186">Internal I/O Driver Get TX Count</span></span> |
| ![Ikon för Hämta tilldelnings fel för intern I/O-drivrutin](./media/user-guide/netx-events/image40.png)    | <span data-ttu-id="0f9f0-188">Intern I/O-drivrutin Hämta tilldelnings fel</span><span class="sxs-lookup"><span data-stu-id="0f9f0-188">Internal I/O Driver Get Allocation Errors</span></span> |
| ![Ikon för intern I/O-drivrutin för avinitiering](./media/user-guide/netx-events/image41.png)    | <span data-ttu-id="0f9f0-190">Intern I/O-drivrutin avinitieras</span><span class="sxs-lookup"><span data-stu-id="0f9f0-190">Internal I/O Driver Un-initialize</span></span> |
| ![Intern I/O-drivrutin för uppskjuten bearbetning](./media/user-guide/netx-events/image42.png)    | <span data-ttu-id="0f9f0-192">Intern I/O-drivrutin uppskjuten bearbetning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-192">Internal I/O Driver Deferred Processing</span></span> |
| ![En ogiltig ikon för R P dynamiska poster](./media/user-guide/netx-events/image43.png)    | <span data-ttu-id="0f9f0-194">**Avvalidering av dynamiska ARP-poster** (*nx_arp_dynamic_entries_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-194">**ARP Dynamic Entries Invalidate** (*nx_arp_dynamic_entries_invalidate*)</span></span> |
| ![En R P-ikon för dynamisk inmatnings uppsättning](./media/user-guide/netx-events/image44.png)    | <span data-ttu-id="0f9f0-196">**Dynamisk ARP-inmatnings uppsättning** (*nx_arp_dynamic_entry_set*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-196">**ARP Dynamic Entry Set** (*nx_arp_dynamic_entry_set*)</span></span> |
| ![Ikonen R P aktivera](./media/user-guide/netx-events/image45.png)    | <span data-ttu-id="0f9f0-198">**Aktivera ARP** (*nx_arp_enable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-198">**ARP Enable** (*nx_arp_enable*)</span></span> |
| ![En R P-ikon för att skicka en kostnads fria sändning](./media/user-guide/netx-events/image46.png)    | <span data-ttu-id="0f9f0-200">**ARP, kostnads överföring** (*nx_arp_gratuitous_send*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-200">**ARP Gratuitous Send** (*nx_arp_gratuitous_send*)</span></span> |
| ![Ikonen R P P maskin varu adress Sök](./media/user-guide/netx-events/image47.png)    | <span data-ttu-id="0f9f0-202">**Sök efter ARP-maskinvara** (*nx_arp_hardware_address_find*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-202">**ARP Hardware Address Find** (*nx_arp_hardware_address_find*)</span></span> |
| ![En R P P information get-ikon](./media/user-guide/netx-events/image48.png)    | <span data-ttu-id="0f9f0-204">**Hämta ARP-information** (*nx_arp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-204">**ARP Information Get** (*nx_arp_info_get*)</span></span> |
| ![Ikonen R P P IP-adress Sök](./media/user-guide/netx-events/image49.png)    | <span data-ttu-id="0f9f0-206">**ARP IP-adress Sök** (*nx_arp_ip_address_find*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-206">**ARP IP Address Find** (*nx_arp_ip_address_find*)</span></span> |
| ![En ikon för att skapa R P statisk post](./media/user-guide/netx-events/image50.png)    | <span data-ttu-id="0f9f0-208">**Skapa statisk post i ARP** (*nx_arp_static_entry_create*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-208">**ARP Static Entry Create** (*nx_arp_static_entry_create*)</span></span> |
| ![Ta bort ikon för R P statisk poster](./media/user-guide/netx-events/image51.png)    | <span data-ttu-id="0f9f0-210">**Ta bort ARP statiska poster** (*nx_arp_static_entries_delete*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-210">**ARP Static Entries Delete** (*nx_arp_static_entries_delete*)</span></span> |
| ![Ikonen R P statisk post Delete](./media/user-guide/netx-events/image52.png)    | <span data-ttu-id="0f9f0-212">**Statisk borttagning av ARP-post** (*nx_arp_static_entry_delete*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-212">**ARP Static Entry Delete** (*nx_arp_static_entry_delete*)</span></span> |
| ![Duo cache Entry ta bort ikon](./media/user-guide/netx-events/image53.png)    | <span data-ttu-id="0f9f0-214">**Borttagning av Duo-cachepost** (*nxd_nd_cache_entry_delete*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-214">**Duo Cache Entry Delete** (*nxd_nd_cache_entry_delete*)</span></span> |
| ![Ikon för Duo cache Entry set](./media/user-guide/netx-events/image54.png)    | <span data-ttu-id="0f9f0-216">**Duo cache-startpunkt** (*nxd_nd_cache_entry_set*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-216">**Duo Cache Entry Set** (*nxd_nd_cache_entry_set*)</span></span> |
| ![Ikonen för Duo cache-Invalidate](./media/user-guide/netx-events/image55.png)    | <span data-ttu-id="0f9f0-218">**Duo-cachelagring är ogiltig** (*nxd_nd_cache_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-218">**Duo Cache Invalidate** (*nxd_nd_cache_invalidate*)</span></span> |
| ![Duo-cache I P-adress Sök ikon](./media/user-guide/netx-events/image56.png)    | <span data-ttu-id="0f9f0-220">**Duo-cache IP-adress Sök** (*nxd_nd_cache_ip_address_find*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-220">**Duo Cache IP Address Find** (*nxd_nd_cache_ip_address_find*)</span></span> |
| ![Ikonen Duo I C M P Enable](./media/user-guide/netx-events/image57.png)    | <span data-ttu-id="0f9f0-222">**Duo ICMP Enable** (*nxd_icmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-222">**Duo ICMP Enable** (*nxd_icmp_enable*)</span></span> |
| ![Ikonen Duo I C M P I P v v 6-ping](./media/user-guide/netx-events/image58.png)    | <span data-ttu-id="0f9f0-224">**Duo ICMP IPv6-ping** (*nxd_icmp_ping*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-224">**Duo ICMP IPv6 Ping** (*nxd_icmp_ping*)</span></span> |
| ![Ikonen Duo I P Max storlek för nytto Last](./media/user-guide/netx-events/image59.png)    | <span data-ttu-id="0f9f0-226">**Duo IP Max storlek för nytto laster Sök** (*nx_max_payload_size_find*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-226">**Duo IP Max Payload Size Find** (*nx_max_payload_size_find*)</span></span> |
| ![Ikonen Duo I P RAW Packet sändning](./media/user-guide/netx-events/image60.png)    | <span data-ttu-id="0f9f0-228">**Duo IP RAW-paket sändning** (*nxd_ip_raw_packet_send*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-228">**Duo IP Raw Packet Send** (*nxd_ip_raw_packet_send*)</span></span> |
| ![Duo I P v v standard ikon för Lägg till router](./media/user-guide/netx-events/image61.png)    | <span data-ttu-id="0f9f0-230">**Duo IPv6 standard router Add** (*nxd_ipv6_default_router_add*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-230">**Duo IPv6 Default Router Add** (*nxd_ipv6_default_router_add*)</span></span> |
| ![Duo I P v v standard ikon för ta bort router](./media/user-guide/netx-events/image62.png)    | <span data-ttu-id="0f9f0-232">**Duo IPv6 standardrouter ta bort** (*nxd_ipv6_default_router_delete)*</span><span class="sxs-lookup"><span data-stu-id="0f9f0-232">**Duo IPv6 Default Router Delete** (*nxd_ipv6_default_router_delete)*</span></span> |
| ![Duo I P v v v Aktivera ikon](./media/user-guide/netx-events/image63.png)    | <span data-ttu-id="0f9f0-234">**Duo IPv6 Enable** (*nxd_ipv6_enable)*</span><span class="sxs-lookup"><span data-stu-id="0f9f0-234">**Duo IPv6 Enable** (*nxd_ipv6_enable)*</span></span> |
| ![Ikonen Duo I P v v 6 global adress Hämta](./media/user-guide/netx-events/image64.png)    | <span data-ttu-id="0f9f0-236">**Duo IPv6 global adress get** (*nxd_ipv6_global_address_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-236">**Duo IPv6 Global Address Get** (*nxd_ipv6_global_address_get*)</span></span> |
| ![Ikonen Duo I P v v v 6, global adress uppsättning](./media/user-guide/netx-events/image65.png)    | <span data-ttu-id="0f9f0-238">**Global adress uppsättning för Duo IPv6** (*nxd_ipv6_global_address_set*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-238">**Duo IPv6 Global Address Set** (*nxd_ipv6_global_address_set*)</span></span> |
| ![Duo I P v v v Starta pappa-process ikon](./media/user-guide/netx-events/image66.png)    | <span data-ttu-id="0f9f0-240">**Duo IPv6-initiera pappa-process** (*nxd_ipv6_initiate_dad_process*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-240">**Duo IPv6 Initiate Dad Process** (*nxd_ipv6_initiate_dad_process*)</span></span> |
| ![Duo I P v v v-ikonen Hämta ikon](./media/user-guide/netx-events/image67.png)    | <span data-ttu-id="0f9f0-242">**Duo IPv6-gränssnitt adress Hämta** (*nxd_ipv6_interface_address_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-242">**Duo IPv6 Interface Address Get** (*nxd_ipv6_interface_address_get*)</span></span> |
| ![Ikon för ikonen Duo I P v v v-gränssnittet](./media/user-guide/netx-events/image68.png)    | <span data-ttu-id="0f9f0-244">**Duo IPv6 gränssnitts adress uppsättning** (*nxd_ipv6_interface_address_set*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-244">**Duo IPv6 Interface Address Set** (*nxd_ipv6_interface_address_set*)</span></span> |
| ![Ikonen Duo I P v v v länk lokal adress Hämta ikon](./media/user-guide/netx-events/image69.png)    | <span data-ttu-id="0f9f0-246">**Duo IPv6 länk lokal adress hämtning** (*nxd_ipv6_linklocal_address_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-246">**Duo IPv6 Link Local Address Get** (*nxd_ipv6_linklocal_address_get*)</span></span> |
| ![Ikonen Duo I P v v v-länk lokalt adress uppsättning](./media/user-guide/netx-events/image70.png)    | <span data-ttu-id="0f9f0-248">**Duo IPv6-länk lokal adress uppsättning** (*nxd_ipv6_linklocal_address_set*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-248">**Duo IPv6 Link Local Address Set** (*nxd_ipv6_linklocal_address_set*)</span></span> |
| ![Duo I P v v v-ikon för RAW Packet-sändning](./media/user-guide/netx-events/image71.png)    | <span data-ttu-id="0f9f0-250">**Duo IPv6 RAW Packet Send** (*nxd_ipv6_raw_packet_send)*</span><span class="sxs-lookup"><span data-stu-id="0f9f0-250">**Duo IPv6 Raw Packet Send** (*nxd_ipv6_raw_packet_send)*</span></span> |
| ![Duo T C P socket peer information get ikon](./media/user-guide/netx-events/image72.png)    | <span data-ttu-id="0f9f0-252">**Duo TCP socket peer information get** (*nxd_tcp_socket_peer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-252">**Duo TCP Socket Peer Info Get** (*nxd_tcp_socket_peer_info_get*)</span></span> |
| ![Ikonen Duo T C P socket set Interface](./media/user-guide/netx-events/image73.png)    | <span data-ttu-id="0f9f0-254">**Duo TCP socket set Interface** (*nxd_tcp_socket_set_interface*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-254">**Duo TCP Socket Set Interface** (*nxd_tcp_socket_set_interface*)</span></span> |
| ![Duo U D P uttag ikon för skicka](./media/user-guide/netx-events/image74.png)    | <span data-ttu-id="0f9f0-256">**Duo UDP-socket sändning** (*nxd_udp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-256">**Duo UDP Socket Send** (*nxd_udp_socket_send*)</span></span> |
| ![Ikonen Duo U D P socket set Interface](./media/user-guide/netx-events/image75.png)    | <span data-ttu-id="0f9f0-258">**Duo UDP socket set Interface** (*nxd_udp_socket_set_interface*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-258">**Duo UDP Socket Set Interface** (*nxd_udp_socket_set_interface*)</span></span> |
| ![Duo U D P-käll extraherings ikon](./media/user-guide/netx-events/image76.png)    | <span data-ttu-id="0f9f0-260">**Duo UDP käll extrahering** (*nxd_udp_source_extract*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-260">**Duo UDP Source Extract** (*nxd_udp_source_extract*)</span></span> |
| ![I C M P Enable-ikon](./media/user-guide/netx-events/image77.png)    | <span data-ttu-id="0f9f0-262">**Aktivera ICMP** (*nx_icmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-262">**ICMP Enable** (*nx_icmp_enable*)</span></span> |
| ![I C M P information get-ikonen](./media/user-guide/netx-events/image78.png)    | <span data-ttu-id="0f9f0-264">**ICMP information get** (*nx_icmp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-264">**ICMP Information Get** (*nx_icmp_info_get*)</span></span> |
| ![I C M P ping-ikonen](./media/user-guide/netx-events/image79.png)    | <span data-ttu-id="0f9f0-266">**ICMP-Ping** (*nx_icmp_ping*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-266">**ICMP Ping** (*nx_icmp_ping*)</span></span> |
| ![I G M P Enable-ikon](./media/user-guide/netx-events/image80.png)    | <span data-ttu-id="0f9f0-268">**Aktivera IGMP** (*nx_igmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-268">**IGMP Enable** (*nx_igmp_enable*)</span></span> |
| ![I G M P information get-ikon](./media/user-guide/netx-events/image81.png)    | <span data-ttu-id="0f9f0-270">**Hämta IGMP information** (*nx_igmp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-270">**IGMP Information Get** (*nx_igmp_info_get*)</span></span> |
| ![I G M P loopback inaktivera ikon](./media/user-guide/netx-events/image82.png)    | <span data-ttu-id="0f9f0-272">**Inaktivera IGMP loopback** (*nx_igmp_loopback_disable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-272">**IGMP Loopback Disable** (*nx_igmp_loopback_disable*)</span></span> |
| ![I G M P loopback Aktivera ikon](./media/user-guide/netx-events/image83.png)    | <span data-ttu-id="0f9f0-274">**Aktivera IGMP loopback** (*nx_igmp_loopback_enable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-274">**IGMP Loopback Enable** (*nx_igmp_loopback_enable*)</span></span> |
| ![I G M P-ikon för multicast-anslutning](./media/user-guide/netx-events/image84.png)    | <span data-ttu-id="0f9f0-276">**IGMP multicast-anslutning** (*nx_igmp_multicast_join*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-276">**IGMP Multicast Join** (*nx_igmp_multicast_join*)</span></span> |
| ![Ikonen I G M P multicast-tjänstledighet](./media/user-guide/netx-events/image85.png)    | <span data-ttu-id="0f9f0-278">**IGMP multicast-ledighet** (*nx_igmp_multicast_leave*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-278">**IGMP Multicast Leave** (*nx_igmp_multicast_leave*)</span></span> |
| ![I P adress ändrings aviserings ikon](./media/user-guide/netx-events/image86.png)    | <span data-ttu-id="0f9f0-280">**Avisering om ändring av IP-adress** (*nx_ip_address_change_notify*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-280">**IP Address Change Notify** (*nx_ip_address_change_notify*)</span></span> |
| ![Hämta ikon för mitt P-adress](./media/user-guide/netx-events/image87.png)    | <span data-ttu-id="0f9f0-282">**Hämta IP-adress** (*nx_ip_address_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-282">**IP Address Get** (*nx_ip_address_get*)</span></span> |
| ![Ikonen I P Address set](./media/user-guide/netx-events/image88.png)    | <span data-ttu-id="0f9f0-284">**IP-adress uppsättning** (*nx_ip_address_set*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-284">**IP Address Set** (*nx_ip_address_set*)</span></span> |
| ![I P skapa ikon](./media/user-guide/netx-events/image89.png)    | <span data-ttu-id="0f9f0-286">**Skapa IP-adress** (*nx_ip_create*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-286">**IP Create** (*nx_ip_create*)</span></span> |
| ![I P ta bort-ikonen](./media/user-guide/netx-events/image90.png)    | <span data-ttu-id="0f9f0-288">**IP-borttagning** (*nx_ip_delete*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-288">**IP Delete** (*nx_ip_delete*)</span></span> |
| ![I P driv rutin Direct kommando ikon](./media/user-guide/netx-events/image91.png)    | <span data-ttu-id="0f9f0-290">**IP-drivrutin Direct-kommando** (*nx_ip_driver_direct_command*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-290">**IP Driver Direct Command** (*nx_ip_driver_direct_command*)</span></span> |
| ![I P-ikonen inaktivera](./media/user-guide/netx-events/image92.png)    | <span data-ttu-id="0f9f0-292">**Inaktivera IP-vidarebefordring** (*nx_ip_forwarding_disable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-292">**IP Forwarding Disable** (*nx_ip_forwarding_disable*)</span></span> |
| ![Aktiverings ikon för I P P-vidarebefordring](./media/user-guide/netx-events/image93.png)    | <span data-ttu-id="0f9f0-294">**Aktivera IP-vidarebefordring** (*nx_ip_forwarding_enable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-294">**IP Forwarding Enable** (*nx_ip_forwarding_enable*)</span></span> |
| ![I P fragment, inaktivera ikon](./media/user-guide/netx-events/image94.png)    | <span data-ttu-id="0f9f0-296">**Inaktivera IP-fragment** (*nx_ip_fragment_disable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-296">**IP Fragment Disable** (*nx_ip_fragment_disable*)</span></span> |
| ![Ikon för att aktivera I f-fragment](./media/user-guide/netx-events/image95.png)    | <span data-ttu-id="0f9f0-298">**Aktivera IP-fragment** (*nx_ip_fragment_enable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-298">**IP Fragment Enable** (*nx_ip_fragment_enable*)</span></span>  |
| ![Ikonen I P Gateway-adress uppsättning](./media/user-guide/netx-events/image96.png)    | <span data-ttu-id="0f9f0-300">**Adress uppsättning för IP-gateway** (*nx_ip_gateway_address_set*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-300">**IP Gateway Address Set** (*nx_ip_gateway_address_set*)</span></span> |
| ![I P information get-ikonen](./media/user-guide/netx-events/image97.png)    | <span data-ttu-id="0f9f0-302">**Hämta IP-information** (*nx_ip_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-302">**IP Information Get** (*nx_ip_info_get*)</span></span> |
| ![Ikon för att koppla mitt gränssnitt](./media/user-guide/netx-events/image98.png)    | <span data-ttu-id="0f9f0-304">**IP-gränssnitt kopplat** (*nx_ip_interface_attach*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-304">**IP Interface Attach** (*nx_ip_interface_attach*)</span></span> |
| ![I P gränssnitts information Hämta ikon](./media/user-guide/netx-events/image99.png)    | <span data-ttu-id="0f9f0-306">**Hämta information om IP-gränssnitt** (*nx_ip_interface_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-306">**IP Interface Info Get** (*nx_ip_interface_info_get*)</span></span> |
| ![Ikonen inaktivera I RAW-paket](./media/user-guide/netx-events/image100.png)    | <span data-ttu-id="0f9f0-308">**Inaktivera IP RAW-paket** (*nx_ip_raw_packet_disable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-308">**IP Raw Packet Disable** (*nx_ip_raw_packet_disable*)</span></span> |
| ![Ikonen aktivera I RAW-paket](./media/user-guide/netx-events/image101.png)    | <span data-ttu-id="0f9f0-310">**Aktivera IP RAW-paket** (*nx_ip_raw_packet_enable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-310">**IP Raw Packet Enable** (*nx_ip_raw_packet_enable*)</span></span> |
| ![Ikonen för att ta emot RAW-paket](./media/user-guide/netx-events/image102.png)    | <span data-ttu-id="0f9f0-312">**Ta emot IP RAW-paket** (*nx_ip_raw_packet_receive*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-312">**IP Raw Packet Receive** (*nx_ip_raw_packet_receive*)</span></span> |
| ![I P skicka ikon för RAW Packet-sändning](./media/user-guide/netx-events/image103.png)    | <span data-ttu-id="0f9f0-314">**Skicka IP RAW-paket** (*nx_ip_raw_packet_send*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-314">**IP Raw Packet Send** (*nx_ip_raw_packet_send*)</span></span> |
| ![I P statisk väg, Lägg till ikon](./media/user-guide/netx-events/image104.png)    | <span data-ttu-id="0f9f0-316">**Lägg till statisk väg för IP** (*nx_ip_static_route_add*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-316">**IP Static Route Add** (*nx_ip_static_route_add*)</span></span> |
| ![I P statisk väg ta bort ikon](./media/user-guide/netx-events/image105.png)    | <span data-ttu-id="0f9f0-318">**IP-statisk väg borttagning** (*nx_ip_static_route_delete)*</span><span class="sxs-lookup"><span data-stu-id="0f9f0-318">**IP Static Route Delete** (*nx_ip_static_route_delete)*</span></span> |
| ![Kontroll ikon för I P-status](./media/user-guide/netx-events/image106.png)    | <span data-ttu-id="0f9f0-320">**Kontroll av IP-status** (*nx_ip_status_check*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-320">**IP Status Check** (*nx_ip_status_check*)</span></span>|
| ![I P S E C Aktivera ikon](./media/user-guide/netx-events/image107.png)    | <span data-ttu-id="0f9f0-322">**Aktivera IPsec** (*nx_ipsec_enable)*</span><span class="sxs-lookup"><span data-stu-id="0f9f0-322">**IPSEC Enable** (*nx_ipsec_enable)*</span></span> |
| ![Ikon för paket tilldelning](./media/user-guide/netx-events/image108.png)    | <span data-ttu-id="0f9f0-324">**Paket tilldelning** (*nx_packet_allocate*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-324">**Packet Allocate** (*nx_packet_allocate*)</span></span> |
| ![Paket kopierings ikon](./media/user-guide/netx-events/image109.png)    | <span data-ttu-id="0f9f0-326">**Paket kopia** (*nx_packet_copy*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-326">**Packet Copy** (*nx_packet_copy*)</span></span> |
| ![Ikon för Lägg till paket data](./media/user-guide/netx-events/image110.png)    | <span data-ttu-id="0f9f0-328">**Lägg till paket data** (*nx_packet_data_append*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-328">**Packet Data Append** (*nx_packet_data_append*)</span></span> |
| ![Förskjutnings ikon för extrahering av paket data](./media/user-guide/netx-events/image111.png)    | <span data-ttu-id="0f9f0-330">**Offset för extrahering av paket data** (*nx_packet_data_extract_offset*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-330">**Packet Data Extract Offset** (*nx_packet_data_extract_offset*)</span></span> |
| ![Hämta ikon för paket data](./media/user-guide/netx-events/image112.png)    | <span data-ttu-id="0f9f0-332">**Hämta paket data** (*nx_packet_data_retrieve*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-332">**Packet Data Retrieve** (*nx_packet_data_retrieve*)</span></span> |
| ![Hämta ikon för paket längd](./media/user-guide/netx-events/image113.png)    | <span data-ttu-id="0f9f0-334">**Hämta paket längd** (*nx_packet_length_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-334">**Packet Length Get** (*nx_packet_length_get*)</span></span> |
| ![Ikon för att skapa paket pool](./media/user-guide/netx-events/image114.png)    | <span data-ttu-id="0f9f0-336">**Skapa paket bassäng** (*nx_packet_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-336">**Packet Pool Create** (*nx_packet_pool_create*)</span></span> |
| ![Ikon för borttagning av paket pool](./media/user-guide/netx-events/image115.png)    | <span data-ttu-id="0f9f0-338">**Ta bort paket bassäng** (*nx_packet_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-338">**Packet Pool Delete** (*nx_packet_pool_delete*)</span></span> |
| ![Hämta ikon för paket Pools information](./media/user-guide/netx-events/image116.png)    | <span data-ttu-id="0f9f0-340">**Hämta paketets pool information** (*nx_packet_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-340">**Packet Pool Information Get** (*nx_packet_pool_info_get*)</span></span> |
| ![Ikon för paket frigörelse](./media/user-guide/netx-events/image117.png)    | <span data-ttu-id="0f9f0-342">**Paket release** (*nx_packet_release*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-342">**Packet Release** (*nx_packet_release*)</span></span> |
| ![Ikon för paket sändnings version](./media/user-guide/netx-events/image118.png)    | <span data-ttu-id="0f9f0-344">**Paket överförings version** (*nx_packet_transmit_release*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-344">**Packet Transmit Release** (*nx_packet_transmit_release*)</span></span> |
| ![R A R P inaktivera ikon](./media/user-guide/netx-events/image119.png)    | <span data-ttu-id="0f9f0-346">**Inaktivera RARP** (*nx_rarp_disable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-346">**RARP Disable** (*nx_rarp_disable*)</span></span> |
| ![R A R P Aktivera ikon](./media/user-guide/netx-events/image120.png)    | <span data-ttu-id="0f9f0-348">**Aktivera RARP** (*nx_rarp_enable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-348">**RARP Enable** (*nx_rarp_enable*)</span></span> |
| ![R A R P P-ikonen Hämta information](./media/user-guide/netx-events/image121.png)    | <span data-ttu-id="0f9f0-350">**RARP information get** (*nx_rarp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-350">**RARP Information Get** (*nx_rarp_info_get*)</span></span> |
| ![Ikon för system initiering](./media/user-guide/netx-events/image122.png)    | <span data-ttu-id="0f9f0-352">**System initiering** (*nx_system_initialize*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-352">**System Initialize** (*nx_system_initialize*)</span></span> |
| ![Ikonen för T C P client socket bind](./media/user-guide/netx-events/image123.png)    | <span data-ttu-id="0f9f0-354">**TCP-klientens socket bind** (*nx_tcp_client_socket_bind*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-354">**TCP Client Socket Bind** (*nx_tcp_client_socket_bind*)</span></span> |
| ![T C P P Connect-ikon för klient-socket](./media/user-guide/netx-events/image124.png)    | <span data-ttu-id="0f9f0-356">**TCP klient-socket Connect** (*nx_tcp_client_socket_connect*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-356">**TCP Client Socket Connect** (*nx_tcp_client_socket_connect*)</span></span> |
| ![Ikonen Hämta ikon för T C P client socket](./media/user-guide/netx-events/image125.png)    | <span data-ttu-id="0f9f0-358">**Hämta TCP-klientens socket-port** (*nx_tcp_client_socket_port_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-358">**TCP Client Socket Port Get** (*nx_tcp_client_socket_port_get*)</span></span> |
| ![Ikon för T C P P-bindning för klient-socket](./media/user-guide/netx-events/image126.png)    | <span data-ttu-id="0f9f0-360">**TCP-klientens socket-bindning** (*nx_tcp_client_socket_unbind*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-360">**TCP Client Socket Unbind** (*nx_tcp_client_socket_unbind*)</span></span> |
| ![Ikonen T C P Enable](./media/user-guide/netx-events/image127.png)    | <span data-ttu-id="0f9f0-362">**TCP-aktivering** (*nx_tcp_enable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-362">**TCP Enable** (*nx_tcp_enable*)</span></span> |
| ![T C P kostnads fri port hitta ikon](./media/user-guide/netx-events/image128.png)    | <span data-ttu-id="0f9f0-364">**Sök efter lediga TCP-portar** (*nx_tcp_free_port_find*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-364">**TCP Free Port Find** (*nx_tcp_free_port_find*)</span></span> |
| ![T C P information get-ikon](./media/user-guide/netx-events/image129.png)    | <span data-ttu-id="0f9f0-366">**Hämta TCP-information** (*nx_tcp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-366">**TCP Information Get** (*nx_tcp_info_get*)</span></span> |
| ![Ikonen för T C P P-mottagning för Server uttag](./media/user-guide/netx-events/image130.png)    | <span data-ttu-id="0f9f0-368">**TCP server-socket acceptera** (*nx_tcp_server_socket_accept*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-368">**TCP Server Socket Accept** (*nx_tcp_server_socket_accept*)</span></span> |
| ![Lyssnings ikon för T C P i Server uttag](./media/user-guide/netx-events/image131.png)    | <span data-ttu-id="0f9f0-370">**TCP server-socket lyssna** (*nx_tcp_server_socket_listen*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-370">**TCP Server Socket Listen** (*nx_tcp_server_socket_listen*)</span></span> |
| ![Ikon för T C P P relister för Server uttag](./media/user-guide/netx-events/image132.png)    | <span data-ttu-id="0f9f0-372">**TCP server socket relister** (*nx_tcp_server_socket_relisten*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-372">**TCP Server Socket Relisten** (*nx_tcp_server_socket_relisten*)</span></span> |
| ![Ikon för att ta emot en ikon för T C P-nätuttag](./media/user-guide/netx-events/image133.png)    | <span data-ttu-id="0f9f0-374">**TCP server-socket accepteras** inte (*nx_tcp_server_socket_unaccept*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-374">**TCP Server Socket Unaccept** (*nx_tcp_server_socket_unaccept*)</span></span> |
| ![Ikon för T C P P-avregistrering av Server-socket](./media/user-guide/netx-events/image134.png)    | <span data-ttu-id="0f9f0-376">**TCP-serverns socket avlistar** (*nx_tcp_server_socket_unlisten*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-376">**TCP Server Socket Unlisten** (*nx_tcp_server_socket_unlisten*)</span></span> |
| ![Ikon för T C P-socket-tillgängliga byte](./media/user-guide/netx-events/image135.png)    | <span data-ttu-id="0f9f0-378">**Tillgängliga TCP-socket byte** (*nx_tcp_socket_bytes_available*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-378">**TCP Socket Bytes Available** (*nx_tcp_socket_bytes_available*)</span></span> |
| ![T C P uttag ikon för skapa](./media/user-guide/netx-events/image136.png)    | <span data-ttu-id="0f9f0-380">**TCP-socket-skapande** (*nx_tcp_socket_create*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-380">**TCP Socket Create** (*nx_tcp_socket_create*)</span></span> |
| ![Ta bort ikon för T C P socket](./media/user-guide/netx-events/image137.png)    | <span data-ttu-id="0f9f0-382">**Ta bort TCP-socket** (*nx_tcp_socket_delete*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-382">**TCP Socket Delete** (*nx_tcp_socket_delete*)</span></span> |
| ![Ikon för T C P uttag från koppling](./media/user-guide/netx-events/image138.png)    | <span data-ttu-id="0f9f0-384">**TCP-socket från koppling** (*nx_tcp_socket_disconnect*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-384">**TCP Socket Disconnect** (*nx_tcp_socket_disconnect*)</span></span> |
| ![T C P socket information get-ikon](./media/user-guide/netx-events/image139.png)    | <span data-ttu-id="0f9f0-386">**TCP socket information get** (*nx_tcp_socket_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-386">**TCP Socket Information Get** (*nx_tcp_socket_info_get*)</span></span> |
| ![Ikon för T C P socket MSS get](./media/user-guide/netx-events/image140.png)    | <span data-ttu-id="0f9f0-388">**TCP-socket MSS get** (*nx_tcp_socket_mss_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-388">**TCP Socket MSS Get** (*nx_tcp_socket_mss_get*)</span></span> |
| ![T C P socket MSS peer get-ikon](./media/user-guide/netx-events/image141.png)    | <span data-ttu-id="0f9f0-390">**TCP-socket MSS peer get** (*nx_tcp_socket_mss_peer_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-390">**TCP Socket MSS Peer Get** (*nx_tcp_socket_mss_peer_get*)</span></span> |
| ![Ikon för T C P socket MSS-uppsättning](./media/user-guide/netx-events/image142.png)    | <span data-ttu-id="0f9f0-392">**TCP-socket MSS-uppsättning** (*nx_tcp_socket_mss_set*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-392">**TCP Socket MSS Set** (*nx_tcp_socket_mss_set*)</span></span> |
| ![Hämta ikon för T C P socket peer info](./media/user-guide/netx-events/image143.png)    | <span data-ttu-id="0f9f0-394">**Hämta peer-information för TCP-socket** (*nx_tcp_socket_peer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-394">**TCP Socket Peer Info Get** (*nx_tcp_socket_peer_info_get*)</span></span> |
| ![Ikon för T C P socket Receive](./media/user-guide/netx-events/image144.png)    | <span data-ttu-id="0f9f0-396">**Mottagning av TCP-socket** (*nx_tcp_socket_receive*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-396">**TCP Socket Receive** (*nx_tcp_socket_receive*)</span></span> |
| ![Ikonen för T C P socket Receive-avisering](./media/user-guide/netx-events/image145.png)    | <span data-ttu-id="0f9f0-398">**Mottagnings meddelande för TCP-socket** (*nx_tcp_socket_receive_notify*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-398">**TCP Socket Receive Notify** (*nx_tcp_socket_receive_notify*)</span></span> |
| ![T C P socket-sändning, ikon](./media/user-guide/netx-events/image146.png)    | <span data-ttu-id="0f9f0-400">**TCP-socket-sändning** (*nx_tcp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-400">**TCP Socket Send** (*nx_tcp_socket_send*)</span></span> |
| ![Vänta-ikon för T C P-insocket-tillstånd](./media/user-guide/netx-events/image147.png)    | <span data-ttu-id="0f9f0-402">**Vänte läge för TCP-socket** (*nx_tcp_socket_state_wait*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-402">**TCP Socket State Wait** (*nx_tcp_socket_state_wait*)</span></span> |
| ![Konfigurations ikon för T C P socket-överföring](./media/user-guide/netx-events/image148.png)    | <span data-ttu-id="0f9f0-404">**Konfigurera TCP socket-överföring** (*nx_tcp_socket_transmit_configure*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-404">**TCP Socket Transmit Configure** (*nx_tcp_socket_transmit_configure*)</span></span> |
| ![Ikon för att uppdatera aviserings uppsättning i T C P socket Window](./media/user-guide/netx-events/image149.png)    | <span data-ttu-id="0f9f0-406">**TCP-socket fönstret uppdatering av meddelande uppsättning** (*nx_tcp_socket_window_update_notify_set*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-406">**TCP Socket Window Update Notify Set** (*nx_tcp_socket_window_update_notify_set*)</span></span>  |
| ![U D P Enable-ikon](./media/user-guide/netx-events/image150.png)    | <span data-ttu-id="0f9f0-408">**UDP-aktivering** (*nx_udp_enable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-408">**UDP Enable** (*nx_udp_enable*)</span></span> |
| ![U D P kostnads fri port hitta ikon](./media/user-guide/netx-events/image151.png)    | <span data-ttu-id="0f9f0-410">**Kostnads fri UDP-port hitta** (*nx_udp_free_port_find*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-410">**UDP Free Port Find** (*nx_udp_free_port_find*)</span></span> |
| ![U D P information get-ikon](./media/user-guide/netx-events/image152.png)    | <span data-ttu-id="0f9f0-412">**Hämta UDP-information** (*nx_udp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-412">**UDP Information Get** (*nx_udp_info_get*)</span></span> |
| ![U D P v socket bind-ikon](./media/user-guide/netx-events/image153.png)    | <span data-ttu-id="0f9f0-414">**UDP-socket bind** (*nx_udp_socket_bind*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-414">**UDP Socket Bind** (*nx_udp_socket_bind*)</span></span> |
| ![Ikon för U D P socket-tillgängliga byte](./media/user-guide/netx-events/image154.png)    | <span data-ttu-id="0f9f0-416">**Tillgängliga UDP-socket-byte** (*nx_udp_socket_bytes_available*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-416">**UDP Socket Bytes Available** (*nx_udp_socket_bytes_available*)</span></span> |
| ![Inaktivera ikon för U D P socket-kontrollsumma](./media/user-guide/netx-events/image155.png)    | <span data-ttu-id="0f9f0-418">**Inaktivera kontroll summa för UDP-socket** (*nx_udp_socket_checksum_disable*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-418">**UDP Socket Checksum Disable** (*nx_udp_socket_checksum_disable*)</span></span> |
| ![Ikon för U D P-uttag för kontroll Summa](./media/user-guide/netx-events/image156.png)    | <span data-ttu-id="0f9f0-420">**Aktivera kontroll summa för UDP-uttag** *(nx_udp_socket_checksum_enable)*</span><span class="sxs-lookup"><span data-stu-id="0f9f0-420">**UDP Socket Checksum Enable** *(nx_udp_socket_checksum_enable)*</span></span> |
| ![U D P uttag ikon för skapa](./media/user-guide/netx-events/image157.png)    | <span data-ttu-id="0f9f0-422">**Skapa UDP-socket** (*nx_udp_socket_create*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-422">**UDP Socket Create** (*nx_udp_socket_create*)</span></span> |
| ![U D P socket ta bort ikon](./media/user-guide/netx-events/image158.png)    | <span data-ttu-id="0f9f0-424">**Ta bort UDP-socket** (*nx_udp_socket_delete*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-424">**UDP Socket Delete** (*nx_udp_socket_delete*)</span></span> |
| ![U D socket information get-ikon](./media/user-guide/netx-events/image159.png)    | <span data-ttu-id="0f9f0-426">**Hämta UDP-socket information** (*nx_udp_socket_info_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-426">**UDP Socket Information Get** (*nx_udp_socket_info_get*)</span></span> |
| ![Ikonen U D P socket interface set](./media/user-guide/netx-events/image160.png)    | <span data-ttu-id="0f9f0-428">**Gränssnitts uppsättning för UDP-socket** (*nx_udp_socket_interface_set*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-428">**UDP Socket Interface Set** (*nx_udp_socket_interface_set*)</span></span> |
| ![U D P socket port get-ikon](./media/user-guide/netx-events/image161.png)    | <span data-ttu-id="0f9f0-430">**Hämta UDP-socket** (*nx_udp_socket_port_get*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-430">**UDP Socket Port Get** (*nx_udp_socket_port_get*)</span></span> |
| ![U D P socket Receive-ikon](./media/user-guide/netx-events/image162.png)    | <span data-ttu-id="0f9f0-432">**Mottagning av UDP-socket** (*nx_udp_socket_receive*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-432">**UDP Socket Receive** (*nx_udp_socket_receive*)</span></span> |
| ![U D P socket ta emot meddelande ikon](./media/user-guide/netx-events/image163.png)    | <span data-ttu-id="0f9f0-434">**Mottagnings meddelande för UDP-socket** (*nx_udp_socket_receive_notify*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-434">**UDP Socket Receive Notify** (*nx_udp_socket_receive_notify*)</span></span> |
| ![U D P socket-skicka-ikon](./media/user-guide/netx-events/image164.png)    | <span data-ttu-id="0f9f0-436">**Skicka UDP-socket** (*nx_udp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-436">**UDP Socket Send** (*nx_udp_socket_send*)</span></span> |
| ![U D P-uppbindning-ikon](./media/user-guide/netx-events/image165.png)    | <span data-ttu-id="0f9f0-438">**UDP-socket-avbindning** (*nx_udp_socket_unbind*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-438">**UDP Socket Unbind** (*nx_udp_socket_unbind*)</span></span> |
| ![U D P P käll extraherings ikon](./media/user-guide/netx-events/image166.png)    | <span data-ttu-id="0f9f0-440">**UDP-käll extrahering** (*nx_udp_source_extract*)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-440">**UDP Source Extract** (*nx_udp_source_extract*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="0f9f0-441">Händelse beskrivningar</span><span class="sxs-lookup"><span data-stu-id="0f9f0-441">Event Descriptions</span></span>

<span data-ttu-id="0f9f0-442">Följande sidor beskriver NetX spårnings händelser.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-442">The following pages describe the NetX Trace Events.</span></span>

### <a name="internal-arp-request-receive"></a><span data-ttu-id="0f9f0-443">Mottagning av intern ARP-begäran</span><span class="sxs-lookup"><span data-stu-id="0f9f0-443">Internal ARP Request Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="0f9f0-444">Mottagning av intern ARP-begäran</span><span class="sxs-lookup"><span data-stu-id="0f9f0-444">Internal ARP request receive</span></span>

<span data-ttu-id="0f9f0-445">**Ikonen** ![ Ta emot ikon för intern ARP-begäran](./media/user-guide/netx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-445">**Icon** ![Internal ARP request receive icon](./media/user-guide/netx-events/image1.png)</span></span>

<span data-ttu-id="0f9f0-446">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-446">**Description**</span></span>

<span data-ttu-id="0f9f0-447">Den här händelsen representerar en intern NetX ARP-begäran ta emot händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-447">This event represents an internal NetX ARP request receive event.</span></span>

<span data-ttu-id="0f9f0-448">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-448">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-449">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-449">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-450">Informations fält 2: Källans IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-450">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="0f9f0-451">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-451">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-452">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-452">Info Field 4: Not used</span></span>

### <a name="internal-arp-request-send"></a><span data-ttu-id="0f9f0-453">Skicka intern ARP-begäran</span><span class="sxs-lookup"><span data-stu-id="0f9f0-453">Internal ARP Request Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="0f9f0-454">Skicka intern ARP-begäran</span><span class="sxs-lookup"><span data-stu-id="0f9f0-454">Internal ARP request send</span></span>

<span data-ttu-id="0f9f0-455">**Ikonen** ![ Skicka ikon för intern ARP-begäran](./media/user-guide/netx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-455">**Icon** ![Internal ARP request send icon](./media/user-guide/netx-events/image2.png)</span></span>

<span data-ttu-id="0f9f0-456">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-456">**Description**</span></span>

<span data-ttu-id="0f9f0-457">Den här händelsen representerar en intern NetX ARP-begäran skicka händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-457">This event represents an internal NetX ARP request send event.</span></span>

<span data-ttu-id="0f9f0-458">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-458">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-459">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-459">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-460">Info fält 2: målets IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-460">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="0f9f0-461">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-461">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-462">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-462">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-receive"></a><span data-ttu-id="0f9f0-463">Mottagna interna ARP-svar</span><span class="sxs-lookup"><span data-stu-id="0f9f0-463">Internal ARP Response Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="0f9f0-464">Mottagning av intern ARP-begäran</span><span class="sxs-lookup"><span data-stu-id="0f9f0-464">Internal ARP request receive</span></span>

<span data-ttu-id="0f9f0-465">**Ikonen** ![ Den interna ARP-begäran ta emot ikon](./media/user-guide/netx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-465">**Icon** ![The Internal ARP request receive icon](./media/user-guide/netx-events/image3.png)</span></span>

<span data-ttu-id="0f9f0-466">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-466">**Description**</span></span>

<span data-ttu-id="0f9f0-467">Den här händelsen representerar en händelse för en intern NetX ARP-svar.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-467">This event represents an internal NetX ARP response receive event.</span></span>

<span data-ttu-id="0f9f0-468">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-468">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-469">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-469">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-470">Informations fält 2: Källans IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-470">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="0f9f0-471">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-471">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-472">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-472">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-send"></a><span data-ttu-id="0f9f0-473">Skicka internt ARP-svar</span><span class="sxs-lookup"><span data-stu-id="0f9f0-473">Internal ARP Response Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="0f9f0-474">Skicka intern ARP-begäran</span><span class="sxs-lookup"><span data-stu-id="0f9f0-474">Internal ARP request send</span></span>

<span data-ttu-id="0f9f0-475">**Ikonen** ![ Den interna ARP-begäran skicka ikon](./media/user-guide/netx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-475">**Icon** ![The Internal ARP request send icon](./media/user-guide/netx-events/image4.png)</span></span>

<span data-ttu-id="0f9f0-476">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-476">**Description**</span></span>

<span data-ttu-id="0f9f0-477">Den här händelsen representerar en intern NetX som skickar svars händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-477">This event represents an internal NetX response send event.</span></span>

<span data-ttu-id="0f9f0-478">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-478">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-479">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-479">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-480">Info fält 2: målets IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-480">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="0f9f0-481">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-481">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-482">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-482">Info Field 4: Not used</span></span>

### <a name="internal-icmp-receive"></a><span data-ttu-id="0f9f0-483">Internt ICMP-mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-483">Internal ICMP Receive</span></span> 

#### <a name="internal-icmp-receive"></a><span data-ttu-id="0f9f0-484">Internt ICMP-mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-484">Internal ICMP receive</span></span>

<span data-ttu-id="0f9f0-485">**Ikonen** ![ Intern I C M P-ikon för mottagning](./media/user-guide/netx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-485">**Icon** ![Internal I C M P receive icon](./media/user-guide/netx-events/image5.png)</span></span>

<span data-ttu-id="0f9f0-486">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-486">**Description**</span></span>

<span data-ttu-id="0f9f0-487">Den här händelsen representerar en intern NetX ICMP Receive-händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-487">This event represents an internal NetX ICMP receive event.</span></span>

<span data-ttu-id="0f9f0-488">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-488">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-489">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-489">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-490">Informations fält 2: Källans IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-490">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="0f9f0-491">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-491">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-492">Info fält 4: Word 0 av ICMP-sidhuvud</span><span class="sxs-lookup"><span data-stu-id="0f9f0-492">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-icmp-send"></a><span data-ttu-id="0f9f0-493">Intern ICMP-sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-493">Internal ICMP Send</span></span> 

#### <a name="internal-icmp-send"></a><span data-ttu-id="0f9f0-494">Intern ICMP-sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-494">Internal ICMP send</span></span>

<span data-ttu-id="0f9f0-495">**Ikonen** ![ Intern I/P e P skicka-ikon](./media/user-guide/netx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-495">**Icon** ![Internal I C M P send icon](./media/user-guide/netx-events/image6.png)</span></span>

<span data-ttu-id="0f9f0-496">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-496">**Description**</span></span>

<span data-ttu-id="0f9f0-497">Den här händelsen representerar en intern NetX ICMP Send-händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-497">This event represents an internal NetX ICMP send event.</span></span>

<span data-ttu-id="0f9f0-498">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-498">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-499">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-499">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-500">Info fält 2: målets IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-500">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="0f9f0-501">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-501">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-502">Info fält 4: Word 0 av ICMP-sidhuvud</span><span class="sxs-lookup"><span data-stu-id="0f9f0-502">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-igmp-receive"></a><span data-ttu-id="0f9f0-503">Intern IGMP-mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-503">Internal IGMP Receive</span></span> 

#### <a name="internal-igmp-receive"></a><span data-ttu-id="0f9f0-504">Intern IGMP-mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-504">Internal IGMP receive</span></span>

<span data-ttu-id="0f9f0-505">**Ikonen** ![ Internt I G/P-ikon för mottagning](./media/user-guide/netx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-505">**Icon** ![Internal I G M P receive icon](./media/user-guide/netx-events/image7.png)</span></span>

<span data-ttu-id="0f9f0-506">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-506">**Description**</span></span>

<span data-ttu-id="0f9f0-507">Den här händelsen representerar en intern NetX IGMP Receive-händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-507">This event represents an internal NetX IGMP receive event.</span></span>

<span data-ttu-id="0f9f0-508">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-508">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-509">Informations fält 1: IP-pekare</span><span class="sxs-lookup"><span data-stu-id="0f9f0-509">Info Field 1: IP Pointer</span></span>
- <span data-ttu-id="0f9f0-510">Informations fält 2: Källans IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-510">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="0f9f0-511">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-511">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-512">Info fält 4: Word 0 av IGMP-huvud</span><span class="sxs-lookup"><span data-stu-id="0f9f0-512">Info Field 4: Word 0 of IGMP header</span></span>

### <a name="internal-ip-receive"></a><span data-ttu-id="0f9f0-513">Ta emot internt IP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-513">Internal IP Receive</span></span> 

#### <a name="internal-ip-receive"></a><span data-ttu-id="0f9f0-514">Ta emot internt IP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-514">Internal IP receive</span></span>

<span data-ttu-id="0f9f0-515">**Ikonen** ![ Intern I/e-ikon](./media/user-guide/netx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-515">**Icon** ![Internal I P receive icon](./media/user-guide/netx-events/image8.png)</span></span>

<span data-ttu-id="0f9f0-516">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-516">**Description**</span></span>

<span data-ttu-id="0f9f0-517">Den här händelsen representerar en intern NetX IP-mottagnings händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-517">This event represents an internal NetX IP receive event.</span></span>

<span data-ttu-id="0f9f0-518">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-518">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-519">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-519">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-520">Informations fält 2: Källans IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-520">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="0f9f0-521">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-521">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-522">Info fält 4: paket längd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-522">Info Field 4: Packet length</span></span>

### <a name="internal-ip-send"></a><span data-ttu-id="0f9f0-523">Skicka intern IP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-523">Internal IP Send</span></span>

#### <a name="internal-ip-send"></a><span data-ttu-id="0f9f0-524">Skicka intern IP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-524">Internal IP send</span></span>

<span data-ttu-id="0f9f0-525">**Ikonen** ![ Intern I/e-ikon](./media/user-guide/netx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-525">**Icon** ![Internal I P send icon](./media/user-guide/netx-events/image9.png)</span></span>

<span data-ttu-id="0f9f0-526">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-526">**Description**</span></span>

<span data-ttu-id="0f9f0-527">Den här händelsen representerar en intern NetX IP-sändnings händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-527">This event represents an internal NetX IP send event.</span></span>

<span data-ttu-id="0f9f0-528">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-528">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-529">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-529">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-530">Info fält 2: målets IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-530">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="0f9f0-531">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-531">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-532">Info fält 4: paket längd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-532">Info Field 4: Packet length</span></span>

### <a name="internal-tcp-data-receive"></a><span data-ttu-id="0f9f0-533">Mottagna interna TCP-data</span><span class="sxs-lookup"><span data-stu-id="0f9f0-533">Internal TCP Data Receive</span></span> 

#### <a name="internal-tcp-data-receive"></a><span data-ttu-id="0f9f0-534">Mottagna interna TCP-data</span><span class="sxs-lookup"><span data-stu-id="0f9f0-534">Internal TCP Data Receive</span></span>

<span data-ttu-id="0f9f0-535">**Ikonen** ![ Intern T C P data Receive-ikon](./media/user-guide/netx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-535">**Icon** ![Internal T C P data receive icon](./media/user-guide/netx-events/image10.png)</span></span>

<span data-ttu-id="0f9f0-536">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-536">**Description**</span></span>

<span data-ttu-id="0f9f0-537">Den här händelsen representerar en intern NetX för mottagna TCP-data.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-537">This event represents an internal NetX TCP data receive event.</span></span>

<span data-ttu-id="0f9f0-538">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-538">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-539">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-539">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-540">Informations fält 2: Källans IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-540">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="0f9f0-541">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-541">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-542">Info fält 4: mottagnings ordnings nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-542">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-data-send"></a><span data-ttu-id="0f9f0-543">Intern TCP-data överföring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-543">Internal TCP data send</span></span> 

#### <a name="internal-tcp-data-send"></a><span data-ttu-id="0f9f0-544">Intern TCP-data överföring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-544">Internal TCP Data Send</span></span>

<span data-ttu-id="0f9f0-545">**Ikonen** ![ Inbyggt T C P data Send-ikon](./media/user-guide/netx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-545">**Icon** ![Internal T C P data send icon](./media/user-guide/netx-events/image11.png)</span></span>

<span data-ttu-id="0f9f0-546">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-546">**Description**</span></span>

<span data-ttu-id="0f9f0-547">Den här händelsen representerar en intern NetX TCP-data sändnings händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-547">This event represents an internal NetX TCP data send event.</span></span>

<span data-ttu-id="0f9f0-548">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-548">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-549">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-549">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-550">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-550">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-551">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-551">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-552">Info-fält 4: överförings ordnings nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-552">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="0f9f0-553">Intern TCP FIN mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-553">Internal TCP FIN Receive</span></span> 

#### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="0f9f0-554">Intern TCP fin mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-554">Internal TCP fin receive</span></span>

<span data-ttu-id="0f9f0-555">**Ikonen** ![ Inbyggt T C P F I N ta emot-ikon](./media/user-guide/netx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-555">**Icon** ![Internal T C P F I N receive icon](./media/user-guide/netx-events/image12.png)</span></span>

<span data-ttu-id="0f9f0-556">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-556">**Description**</span></span>

<span data-ttu-id="0f9f0-557">Den här händelsen representerar en intern NetX TCP FIN Receive-händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-557">This event represents an internal NetX TCP FIN receive event.</span></span>

<span data-ttu-id="0f9f0-558">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-558">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-559">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-559">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-560">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-560">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-561">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-561">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-562">Info fält 4: mottagnings ordnings nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-562">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-fin-send"></a><span data-ttu-id="0f9f0-563">Intern TCP RÄNTETRANS-sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-563">Internal TCP FIN Send</span></span> 

#### <a name="internal-tcp-fin-send"></a><span data-ttu-id="0f9f0-564">Intern TCP räntetrans-sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-564">Internal TCP fin send</span></span>

<span data-ttu-id="0f9f0-565">**Ikonen** ![ Inbyggt T C P F I N skicka ikon](./media/user-guide/netx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-565">**Icon** ![Internal T C P F I N send icon](./media/user-guide/netx-events/image13.png)</span></span>

<span data-ttu-id="0f9f0-566">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-566">**Description**</span></span>

<span data-ttu-id="0f9f0-567">Den här händelsen representerar en intern NetX TCP RÄNTETRANS-sändning.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-567">This event represents an internal NetX TCP FIN send event.</span></span>

<span data-ttu-id="0f9f0-568">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-568">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-569">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-569">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-570">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-570">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-571">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-571">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-572">Info-fält 4: överförings ordnings nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-572">Info Field 4:Transmit sequence number</span></span>

### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="0f9f0-573">Internt TCP-mottagna</span><span class="sxs-lookup"><span data-stu-id="0f9f0-573">Internal TCP RST Receive</span></span> 

#### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="0f9f0-574">Internt TCP-mottagna</span><span class="sxs-lookup"><span data-stu-id="0f9f0-574">Internal TCP RST receive</span></span>

<span data-ttu-id="0f9f0-575">**Ikonen** ![ Inbyggt T C P R S T Inleverera-ikon](./media/user-guide/netx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-575">**Icon** ![Internal T C P R S T receive icon](./media/user-guide/netx-events/image14.png)</span></span>

<span data-ttu-id="0f9f0-576">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-576">**Description**</span></span>

<span data-ttu-id="0f9f0-577">Den här händelsen representerar en intern NetX TCP reset Receive-händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-577">This event represents an internal NetX TCP reset receive event.</span></span>

<span data-ttu-id="0f9f0-578">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-578">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-579">Info fält 1: pekar mot IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-579">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="0f9f0-580">Info fält 2: pekare till Socket.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-580">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="0f9f0-581">Info-fält 3: pekar mot paket.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-581">Info Field 3: Pointer to packet.</span></span>
- <span data-ttu-id="0f9f0-582">Info fält 4: mottagnings ordnings nummer.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-582">Info Field 4: Receive sequence number.</span></span>

### <a name="internal-tcp-rst-send"></a><span data-ttu-id="0f9f0-583">Intern TCP-överföring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-583">Internal TCP RST Send</span></span> 

#### <a name="internal-tcp-rst-send"></a><span data-ttu-id="0f9f0-584">Intern TCP-överföring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-584">Internal TCP RST send</span></span>

<span data-ttu-id="0f9f0-585">**Ikonen** ![ Intern T R P R S T skicka-ikon](./media/user-guide/netx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-585">**Icon** ![Internal T C P R S T send icon](./media/user-guide/netx-events/image15.png)</span></span>

<span data-ttu-id="0f9f0-586">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-586">**Description**</span></span>

<span data-ttu-id="0f9f0-587">Den här händelsen representerar en intern NetX TCP reset Send-händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-587">This event represents an internal NetX TCP reset send event.</span></span>

<span data-ttu-id="0f9f0-588">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-588">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-589">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-589">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-590">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-590">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-591">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-591">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-592">Info-fält 4: överförings ordnings nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-592">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="0f9f0-593">Ta emot internt TCP-SYN</span><span class="sxs-lookup"><span data-stu-id="0f9f0-593">Internal TCP SYN Receive</span></span> 

#### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="0f9f0-594">Ta emot internt TCP-SYN</span><span class="sxs-lookup"><span data-stu-id="0f9f0-594">Internal TCP SYN receive</span></span>

<span data-ttu-id="0f9f0-595">**Ikonen** ![ Ikon för intern T C P S Y N-mottagning](./media/user-guide/netx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-595">**Icon** ![Internal T C P S Y N receive icon](./media/user-guide/netx-events/image16.png)</span></span>

<span data-ttu-id="0f9f0-596">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-596">**Description**</span></span>

<span data-ttu-id="0f9f0-597">Den här händelsen representerar en intern NetX TCP SYN-händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-597">This event represents an internal NetX TCP SYN receive event.</span></span>

<span data-ttu-id="0f9f0-598">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-598">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-599">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-599">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-600">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-600">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-601">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-601">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-602">Info fält 4: mottagnings ordnings nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-602">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-syn-send"></a><span data-ttu-id="0f9f0-603">Skicka internt TCP-SYN</span><span class="sxs-lookup"><span data-stu-id="0f9f0-603">Internal TCP SYN Send</span></span> 

#### <a name="internal-tcp-syn-send"></a><span data-ttu-id="0f9f0-604">Skicka internt TCP-SYN</span><span class="sxs-lookup"><span data-stu-id="0f9f0-604">Internal TCP SYN send</span></span>

<span data-ttu-id="0f9f0-605">**Ikonen** ![ Intern T C P S Y N skicka-ikon](./media/user-guide/netx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-605">**Icon** ![Internal T C P S Y N send icon](./media/user-guide/netx-events/image17.png)</span></span>

<span data-ttu-id="0f9f0-606">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-606">**Description**</span></span>

<span data-ttu-id="0f9f0-607">Den här händelsen representerar en intern NetX TCP SYN-sändning.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-607">This event represents an internal NetX TCP SYN send event.</span></span>

<span data-ttu-id="0f9f0-608">Informations fält</span><span class="sxs-lookup"><span data-stu-id="0f9f0-608">Information Fields</span></span> 

- <span data-ttu-id="0f9f0-609">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-609">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-610">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-610">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-611">Info-fält 3: pekar på paket-info fält 4: överförings ordnings nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-611">Info Field 3: Pointer to packet -Info Field 4: Transmit sequence number</span></span>

### <a name="internal-udp-receive"></a><span data-ttu-id="0f9f0-612">Internt UDP-mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-612">Internal UDP Receive</span></span> 

#### <a name="internal-udp-receive"></a><span data-ttu-id="0f9f0-613">Internt UDP-mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-613">Internal UDP receive</span></span>

<span data-ttu-id="0f9f0-614">**Ikonen** ![ Intern U D P-mottagnings ikon](./media/user-guide/netx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-614">**Icon** ![Internal U D P receive icon](./media/user-guide/netx-events/image18.png)</span></span>

<span data-ttu-id="0f9f0-615">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-615">**Description**</span></span>

<span data-ttu-id="0f9f0-616">Den här händelsen representerar en intern NetX UDP Receive-händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-616">This event represents an internal NetX UDP receive event.</span></span>

<span data-ttu-id="0f9f0-617">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-617">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-618">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-618">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-619">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-619">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-620">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-620">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-621">Info fält 4: Word 0 av UDP-huvud</span><span class="sxs-lookup"><span data-stu-id="0f9f0-621">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-udp-send"></a><span data-ttu-id="0f9f0-622">Intern UDP-sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-622">Internal UDP Send</span></span> 

#### <a name="internal-udp-send"></a><span data-ttu-id="0f9f0-623">Intern UDP-sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-623">Internal UDP send</span></span>

<span data-ttu-id="0f9f0-624">**Ikonen** ![ Intern U D P-skicka-ikon](./media/user-guide/netx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-624">**Icon** ![Internal U D P send icon](./media/user-guide/netx-events/image19.png)</span></span>

<span data-ttu-id="0f9f0-625">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-625">**Description**</span></span>

<span data-ttu-id="0f9f0-626">Den här händelsen representerar en intern NetX UDP-sändning.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-626">This event represents an internal NetX UDP send event.</span></span>

<span data-ttu-id="0f9f0-627">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-627">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-628">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-628">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-629">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-629">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-630">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-630">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-631">Info fält 4: Word 0 av UDP-huvud</span><span class="sxs-lookup"><span data-stu-id="0f9f0-631">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-rarp-receive"></a><span data-ttu-id="0f9f0-632">Intern RARP-mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-632">Internal RARP Receive</span></span> 

#### <a name="internal-rarp-receive"></a><span data-ttu-id="0f9f0-633">Intern RARP-mottagning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-633">Internal RARP receive</span></span> 

<span data-ttu-id="0f9f0-634">**Ikonen** ![ Intern R A R P-ikon för mottagning](./media/user-guide/netx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-634">**Icon** ![Internal R A R P receive icon](./media/user-guide/netx-events/image20.png)</span></span>

<span data-ttu-id="0f9f0-635">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-635">**Description**</span></span>

<span data-ttu-id="0f9f0-636">Den här händelsen representerar en intern NetX RARP Receive-händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-636">This event represents an internal NetX RARP receive event.</span></span>

<span data-ttu-id="0f9f0-637">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-637">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-638">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-638">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-639">Informations fält 2: mål-IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-639">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="0f9f0-640">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-640">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-641">Info fält 4: Word 1 av RARP-huvudet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-641">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-rarp-send"></a><span data-ttu-id="0f9f0-642">Intern RARP-sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-642">Internal RARP Send</span></span> 

#### <a name="internal-rarp-send"></a><span data-ttu-id="0f9f0-643">Intern RARP-sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-643">Internal RARP send</span></span> 

<span data-ttu-id="0f9f0-644">**Ikonen** ![ Interna R A R P-ikonen skicka](./media/user-guide/netx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-644">**Icon** ![Internal R A R P send icon](./media/user-guide/netx-events/image21.png)</span></span>

<span data-ttu-id="0f9f0-645">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-645">**Description**</span></span>

<span data-ttu-id="0f9f0-646">Den här händelsen representerar en intern NetX RARP-sändnings händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-646">This event represents an internal NetX RARP send event.</span></span>

<span data-ttu-id="0f9f0-647">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-647">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-648">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-648">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-649">Informations fält 2: mål-IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-649">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="0f9f0-650">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-650">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-651">Info fält 4: Word 1 av RARP-huvudet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-651">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-tcp-retry"></a><span data-ttu-id="0f9f0-652">Internt TCP-försök</span><span class="sxs-lookup"><span data-stu-id="0f9f0-652">Internal TCP Retry</span></span> 

#### <a name="internal-tcp-retry"></a><span data-ttu-id="0f9f0-653">Internt TCP-försök</span><span class="sxs-lookup"><span data-stu-id="0f9f0-653">Internal TCP retry</span></span> 

<span data-ttu-id="0f9f0-654">**Ikonen** ![ Inbyggt T C P-återförsök-ikon](./media/user-guide/netx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-654">**Icon** ![Internal T C P retry icon](./media/user-guide/netx-events/image22.png)</span></span>

<span data-ttu-id="0f9f0-655">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-655">**Description**</span></span>

<span data-ttu-id="0f9f0-656">Den här händelsen representerar en intern NetX-händelse för TCP-försök.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-656">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="0f9f0-657">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-657">**Information Fields**</span></span>
- <span data-ttu-id="0f9f0-658">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-658">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-659">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-659">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-660">Info-fält 3: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-660">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-661">Info-fält 4: antal återförsök</span><span class="sxs-lookup"><span data-stu-id="0f9f0-661">Info Field 4: Number of retries</span></span>

### <a name="internal-tcp-state-change"></a><span data-ttu-id="0f9f0-662">Intern TCP-tillstånds ändring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-662">Internal TCP State Change</span></span> 

#### <a name="internal-tcp-state-change"></a><span data-ttu-id="0f9f0-663">Intern TCP-tillstånds ändring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-663">Internal TCP state change</span></span> 

<span data-ttu-id="0f9f0-664">**Ikonen** ![ Ändrings ikon för den interna T C P-statusen](./media/user-guide/netx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-664">**Icon** ![Internal T C P state change icon](./media/user-guide/netx-events/image23.png)</span></span>

<span data-ttu-id="0f9f0-665">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-665">**Description**</span></span>

<span data-ttu-id="0f9f0-666">Den här händelsen representerar en intern NetX av status ändrings händelse för TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-666">This event represents an internal NetX TCP socket state change event.</span></span>

<span data-ttu-id="0f9f0-667">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-667">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-668">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-668">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-669">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-669">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-670">Info-fält 3: föregående tillstånd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-670">Info Field 3: Previous state</span></span>
- <span data-ttu-id="0f9f0-671">Info fält 4: nytt tillstånd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-671">Info Field 4: New state</span></span>

### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="0f9f0-672">Skicka internt I/O-drivrutins paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-672">Internal I/O Driver Packet Send</span></span> 

#### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="0f9f0-673">Skicka internt I/O-drivrutins paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-673">Internal I/O driver packet send</span></span>

<span data-ttu-id="0f9f0-674">**Ikonen** ![ Ikon för att skicka intern I/O-drivrutin](./media/user-guide/netx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-674">**Icon** ![Internal I / O driver packet send icon](./media/user-guide/netx-events/image24.png)</span></span>

<span data-ttu-id="0f9f0-675">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-675">**Description**</span></span>

<span data-ttu-id="0f9f0-676">Den här händelsen representerar en intern sändnings händelse för NetX I/O-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-676">This event represents an internal NetX I/O driver packet send event.</span></span>

<span data-ttu-id="0f9f0-677">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-677">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-678">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-678">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-679">Info fält 2: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-679">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-680">Informations fält 3: paket storlek</span><span class="sxs-lookup"><span data-stu-id="0f9f0-680">Info Field 3: Packet size</span></span>
- <span data-ttu-id="0f9f0-681">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-681">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="0f9f0-682">Intern I/O-drivrutin initieras</span><span class="sxs-lookup"><span data-stu-id="0f9f0-682">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="0f9f0-683">Intern I/O-drivrutin initieras</span><span class="sxs-lookup"><span data-stu-id="0f9f0-683">Internal I/O driver initialize</span></span>

<span data-ttu-id="0f9f0-684">**Ikonen** ![ Initiera ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-684">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/netx-events/image25.png)</span></span>

<span data-ttu-id="0f9f0-685">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-685">**Description**</span></span>

<span data-ttu-id="0f9f0-686">Den här händelsen representerar en intern händelse för NetX I/O-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-686">This event represents an internal NetX I/O driver initialize event.</span></span>

<span data-ttu-id="0f9f0-687">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-687">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-688">Info fält 1: pekar mot IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-688">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="0f9f0-689">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-689">Info Field 2: Not used.</span></span>
- <span data-ttu-id="0f9f0-690">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-690">Info Field 3: Not used.</span></span>
- <span data-ttu-id="0f9f0-691">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-691">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="0f9f0-692">Intern I/O driv Rutins länk aktivera</span><span class="sxs-lookup"><span data-stu-id="0f9f0-692">Internal I/O Driver Link Enable</span></span> 

#### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="0f9f0-693">Intern I/O driv rutins länk aktivera</span><span class="sxs-lookup"><span data-stu-id="0f9f0-693">Internal I/O driver link enable</span></span>

<span data-ttu-id="0f9f0-694">**Ikonen** ![ Ikonen Aktivera ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-694">**Icon** ![Internal I / O driver link enable icon](./media/user-guide/netx-events/image26.png)</span></span>

<span data-ttu-id="0f9f0-695">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-695">**Description**</span></span>

<span data-ttu-id="0f9f0-696">Den här händelsen representerar en intern NetX I/O-drivrutins länk aktivera händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-696">This event represents an internal NetX I/O driver link enable event.</span></span>

<span data-ttu-id="0f9f0-697">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-697">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-698">Info fält 1: pekar mot IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-698">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="0f9f0-699">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-699">Info Field 2: Not used.</span></span>
- <span data-ttu-id="0f9f0-700">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-700">Info Field 3: Not used.</span></span>
- <span data-ttu-id="0f9f0-701">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-701">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="0f9f0-702">Inaktivera intern I/O driv Rutins länk</span><span class="sxs-lookup"><span data-stu-id="0f9f0-702">Internal I/O Driver Link Disable</span></span> 

#### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="0f9f0-703">Inaktivera intern I/O driv rutins länk</span><span class="sxs-lookup"><span data-stu-id="0f9f0-703">Internal I/O driver link disable</span></span>

<span data-ttu-id="0f9f0-704">**Ikonen** ![ Ikon för inaktive ring av intern I/O-drivrutin](./media/user-guide/netx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-704">**Icon** ![Internal I / O driver link disable icon](./media/user-guide/netx-events/image27.png)</span></span>

<span data-ttu-id="0f9f0-705">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-705">**Description**</span></span>

<span data-ttu-id="0f9f0-706">Den här händelsen representerar en intern inaktive rings händelse för NetX I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-706">This event represents an internal NetX I/O driver link disable event.</span></span>

<span data-ttu-id="0f9f0-707">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-707">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-708">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-708">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-709">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-709">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-710">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-710">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-711">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-711">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="0f9f0-712">Intern I/O-drivrutins paket sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-712">Internal I/O Driver Packet Broadcast</span></span> 

#### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="0f9f0-713">Intern I/O-drivrutins paket sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-713">Internal I/O driver packet broadcast</span></span>

<span data-ttu-id="0f9f0-714">**Ikonen** ![ Ikon för intern I/O-drivrutin för driv rutins paket](./media/user-guide/netx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-714">**Icon** ![Internal I / O driver packet broadcast icon](./media/user-guide/netx-events/image28.png)</span></span>

<span data-ttu-id="0f9f0-715">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-715">**Description**</span></span>

<span data-ttu-id="0f9f0-716">Den här händelsen representerar en intern sändnings händelse för NetX I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-716">This event represents an internal NetX I/O driver packet broadcast event.</span></span>

<span data-ttu-id="0f9f0-717">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-717">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-718">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-718">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-719">Info fält 2: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-719">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-720">Informations fält 3: paket storlek</span><span class="sxs-lookup"><span data-stu-id="0f9f0-720">Info Field 3: Packet size</span></span>
- <span data-ttu-id="0f9f0-721">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-721">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="0f9f0-722">Överföring av intern I/O-drivrutins-ARP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-722">Internal I/O Driver ARP Send</span></span> 

#### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="0f9f0-723">Överföring av intern I/O-drivrutins-ARP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-723">Internal I/O driver ARP send</span></span>

<span data-ttu-id="0f9f0-724">**Ikonen** ![ Skicka ikon för intern I/O-drivrutins-ARP](./media/user-guide/netx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-724">**Icon** ![Internal I / O driver ARP send icon](./media/user-guide/netx-events/image29.png)</span></span>

<span data-ttu-id="0f9f0-725">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-725">**Description**</span></span>

<span data-ttu-id="0f9f0-726">Den här händelsen representerar en intern sändnings händelse för NetX I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-726">This event represents an internal NetX I/O driver ARP send event.</span></span>

<span data-ttu-id="0f9f0-727">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-727">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-728">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-728">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-729">Info fält 2: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-729">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-730">Informations fält 3: paket storlek</span><span class="sxs-lookup"><span data-stu-id="0f9f0-730">Info Field 3: Packet size</span></span>
- <span data-ttu-id="0f9f0-731">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-731">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="0f9f0-732">Intern I/O-drivrutin ARP-svar skicka</span><span class="sxs-lookup"><span data-stu-id="0f9f0-732">Internal I/O Driver ARP Response Send</span></span> 

#### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="0f9f0-733">Intern I/O-drivrutin ARP-svar skicka</span><span class="sxs-lookup"><span data-stu-id="0f9f0-733">Internal I/O driver ARP response send</span></span>

<span data-ttu-id="0f9f0-734">**Ikonen** ![ Intern I/O-drivrutin för ARP-svar skicka ikon](./media/user-guide/netx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-734">**Icon** ![Internal I / O driver ARP response send icon](./media/user-guide/netx-events/image30.png)</span></span>

<span data-ttu-id="0f9f0-735">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-735">**Description**</span></span>

<span data-ttu-id="0f9f0-736">Den här händelsen representerar en intern NetX I/O-drivrutin ARP-svar skicka händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-736">This event represents an internal NetX I/O driver ARP response send event.</span></span>

<span data-ttu-id="0f9f0-737">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-737">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-738">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-738">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-739">Info fält 2: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-739">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-740">Informations fält 3: paket storlek</span><span class="sxs-lookup"><span data-stu-id="0f9f0-740">Info Field 3: Packet size</span></span>
- <span data-ttu-id="0f9f0-741">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-741">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="0f9f0-742">Intern I/O-drivrutin RARP skicka</span><span class="sxs-lookup"><span data-stu-id="0f9f0-742">Internal I/O Driver RARP Send</span></span> 

#### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="0f9f0-743">Intern I/O-drivrutin RARP skicka</span><span class="sxs-lookup"><span data-stu-id="0f9f0-743">Internal I/O driver RARP send</span></span>

<span data-ttu-id="0f9f0-744">**Ikonen** ![ Intern I/O driv rutin RARP skicka ikon](./media/user-guide/netx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-744">**Icon** ![Internal I / O driver RARP send icon](./media/user-guide/netx-events/image31.png)</span></span>

<span data-ttu-id="0f9f0-745">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-745">**Description**</span></span>

<span data-ttu-id="0f9f0-746">Den här händelsen representerar en intern NetX I/O-drivrutin RARP skicka händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-746">This event represents an internal NetX I/O driver RARP send event.</span></span>

<span data-ttu-id="0f9f0-747">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-747">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-748">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-748">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-749">Info fält 2: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-749">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-750">Informations fält 3: paket storlek</span><span class="sxs-lookup"><span data-stu-id="0f9f0-750">Info Field 3: Packet size</span></span>
- <span data-ttu-id="0f9f0-751">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-751">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="0f9f0-752">Intern I/O-drivrutin multicast-anslutning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-752">Internal I/O Driver Multicast Join</span></span> 

#### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="0f9f0-753">Intern I/O-drivrutin multicast-anslutning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-753">Internal I/O driver multicast join</span></span>

<span data-ttu-id="0f9f0-754">**Ikonen** ![ Ikon för multicast-anslutning för intern I/O-drivrutin](./media/user-guide/netx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-754">**Icon** ![Internal I / O driver multicast join icon](./media/user-guide/netx-events/image32.png)</span></span>

<span data-ttu-id="0f9f0-755">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-755">**Description**</span></span>

<span data-ttu-id="0f9f0-756">Den här händelsen representerar en intern NetX I/O-drivrutin för IO-anslutning.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-756">This event represents an internal NetX I/O driver multicast join event.</span></span>

<span data-ttu-id="0f9f0-757">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-757">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-758">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-758">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-759">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-759">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-760">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-760">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-761">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-761">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="0f9f0-762">Intern I/O-drivrutin för multicast-ledighet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-762">Internal I/O Driver Multicast Leave</span></span> 

#### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="0f9f0-763">Intern I/O-drivrutin för multicast-ledighet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-763">Internal I/O driver multicast leave</span></span>

<span data-ttu-id="0f9f0-764">**Ikonen** ![ Ikon för multicast för intern I/O-drivrutin](./media/user-guide/netx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-764">**Icon** ![Internal I / O driver multicast leave icon](./media/user-guide/netx-events/image33.png)</span></span>

<span data-ttu-id="0f9f0-765">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-765">**Description**</span></span>

<span data-ttu-id="0f9f0-766">Den här händelsen representerar en intern NetX I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-766">This event represents an internal NetX I/O driver multicast leave event.</span></span>

<span data-ttu-id="0f9f0-767">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-767">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-768">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-768">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-769">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-769">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-770">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-770">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-771">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-771">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-status"></a><span data-ttu-id="0f9f0-772">Status för intern I/O-drivrutin för hämtning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-772">Internal I/O Driver Get Status</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="0f9f0-773">Status för intern I/O-drivrutin för hämtning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-773">Internal I/O driver get status</span></span>

<span data-ttu-id="0f9f0-774">**Ikonen** ![ Status ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-774">**Icon** ![Internal I / O driver get status icon](./media/user-guide/netx-events/image34.png)</span></span>

<span data-ttu-id="0f9f0-775">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-775">**Description**</span></span>

<span data-ttu-id="0f9f0-776">Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta status händelse.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-776">This event represents an internal NetX I/O driver get status event.</span></span>

<span data-ttu-id="0f9f0-777">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-777">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-778">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-778">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-779">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-779">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-780">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-780">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-781">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-781">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="0f9f0-782">Intern I/O-drivrutin Hämta hastighet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-782">Internal I/O Driver Get Speed</span></span> 

#### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="0f9f0-783">Intern I/O-drivrutin Hämta hastighet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-783">Internal I/O driver get speed</span></span>

<span data-ttu-id="0f9f0-784">**Ikonen** ![ Intern I/O driv rutin Hämta hastighets ikon](./media/user-guide/netx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-784">**Icon** ![Internal I / O driver get speed icon](./media/user-guide/netx-events/image35.png)</span></span>

<span data-ttu-id="0f9f0-785">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-785">**Description**</span></span>

<span data-ttu-id="0f9f0-786">Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta hastighet.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-786">This event represents an internal NetX I/O driver get speed event.</span></span>

<span data-ttu-id="0f9f0-787">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-787">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-788">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-788">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-789">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-789">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-790">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-790">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-791">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-791">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="0f9f0-792">Intern I/O-drivrutin Hämta duplex-typ</span><span class="sxs-lookup"><span data-stu-id="0f9f0-792">Internal I/O Driver Get Duplex Type</span></span> 

#### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="0f9f0-793">Intern I/O-drivrutin Hämta duplex-typ</span><span class="sxs-lookup"><span data-stu-id="0f9f0-793">Internal I/O driver get duplex type</span></span>

<span data-ttu-id="0f9f0-794">**Ikonen** ![ Intern I/O-drivrutin Hämta duplex-typ ikon](./media/user-guide/netx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-794">**Icon** ![Internal I / O driver get duplex type icon](./media/user-guide/netx-events/image36.png)</span></span>

<span data-ttu-id="0f9f0-795">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-795">**Description**</span></span>

<span data-ttu-id="0f9f0-796">Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta duplex-typ.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-796">This event represents an internal NetX I/O driver get duplex type event.</span></span>

<span data-ttu-id="0f9f0-797">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-797">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-798">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-798">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-799">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-799">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-800">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-800">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-801">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-801">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="0f9f0-802">Fel antal för intern I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="0f9f0-802">Internal I/O Driver Get Error Count</span></span>

#### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="0f9f0-803">Fel antal för intern I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="0f9f0-803">Internal I/O driver get error count</span></span>

<span data-ttu-id="0f9f0-804">**Ikonen** ![ Ikon för Hämta fel antal för intern I/O-drivrutin](./media/user-guide/netx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-804">**Icon** ![Internal I / O driver get error count icon](./media/user-guide/netx-events/image37.png)</span></span>

<span data-ttu-id="0f9f0-805">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-805">**Description**</span></span>

<span data-ttu-id="0f9f0-806">Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta fel antal.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-806">This event represents an internal NetX I/O driver get error count event.</span></span>

<span data-ttu-id="0f9f0-807">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-807">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-808">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-808">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-809">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-809">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-810">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-810">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-811">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-811">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="0f9f0-812">Intern I/O-drivrutin Hämta RX-antal</span><span class="sxs-lookup"><span data-stu-id="0f9f0-812">Internal I/O Driver Get RX Count</span></span> 

#### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="0f9f0-813">Intern I/O-drivrutin Hämta RX-antal</span><span class="sxs-lookup"><span data-stu-id="0f9f0-813">Internal I/O driver get RX count</span></span>

<span data-ttu-id="0f9f0-814">**Ikonen** ![ Intern I/O-drivrutin Hämta RX-ikon](./media/user-guide/netx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-814">**Icon** ![Internal I / O driver get RX count icon](./media/user-guide/netx-events/image38.png)</span></span>

<span data-ttu-id="0f9f0-815">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-815">**Description**</span></span>

<span data-ttu-id="0f9f0-816">Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta antal RX.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-816">This event represents an internal NetX I/O driver get RX count event.</span></span>

<span data-ttu-id="0f9f0-817">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-817">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-818">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-818">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-819">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-819">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-820">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-820">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-821">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-821">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="0f9f0-822">Intern I/O-drivrutin Hämta TX-antal</span><span class="sxs-lookup"><span data-stu-id="0f9f0-822">Internal I/O Driver Get TX Count</span></span> 

#### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="0f9f0-823">Intern I/O-drivrutin Hämta TX-antal</span><span class="sxs-lookup"><span data-stu-id="0f9f0-823">Internal I/O driver get TX count</span></span>

<span data-ttu-id="0f9f0-824">**Ikonen** ![ Ikon för att hämta T X för intern I/O-drivrutin](./media/user-guide/netx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-824">**Icon** ![Internal I / O driver get T X count icon](./media/user-guide/netx-events/image39.png)</span></span>

<span data-ttu-id="0f9f0-825">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-825">**Description**</span></span>

<span data-ttu-id="0f9f0-826">Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta TX-antal.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-826">This event represents an internal NetX I/O driver get TX count event.</span></span>

<span data-ttu-id="0f9f0-827">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-827">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-828">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-828">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-829">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-829">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-830">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-830">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-831">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-831">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="0f9f0-832">Intern I/O-drivrutin Hämta tilldelnings fel</span><span class="sxs-lookup"><span data-stu-id="0f9f0-832">Internal I/O Driver Get Allocation Errors</span></span> 

#### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="0f9f0-833">Intern I/O-drivrutin Hämta tilldelnings fel</span><span class="sxs-lookup"><span data-stu-id="0f9f0-833">Internal I/O driver get allocation errors</span></span>

<span data-ttu-id="0f9f0-834">**Ikonen** ![ Ikon för Hämta tilldelnings fel för intern I/O-drivrutin](./media/user-guide/netx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-834">**Icon** ![Internal I / O driver get allocation errors icon](./media/user-guide/netx-events/image40.png)</span></span>

<span data-ttu-id="0f9f0-835">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-835">**Description**</span></span>

<span data-ttu-id="0f9f0-836">Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta tilldelnings fel.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-836">This event represents an internal NetX I/O driver get allocation errors event.</span></span>

<span data-ttu-id="0f9f0-837">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-837">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-838">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-838">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-839">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-839">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-840">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-840">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-841">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-841">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="0f9f0-842">Intern I/O-drivrutin avinitieras</span><span class="sxs-lookup"><span data-stu-id="0f9f0-842">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="0f9f0-843">Intern I/O-drivrutin avinitieras</span><span class="sxs-lookup"><span data-stu-id="0f9f0-843">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="0f9f0-844">**Ikonen** ![ Ikon för intern I/O-drivrutin för avinitiering](./media/user-guide/netx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-844">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/netx-events/image41.png)</span></span>

<span data-ttu-id="0f9f0-845">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-845">**Description**</span></span>

<span data-ttu-id="0f9f0-846">Den här händelsen representerar en intern NetX I/O-drivrutin som avinitieras.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-846">This event represents an internal NetX I/O driver un-initialize event.</span></span>

<span data-ttu-id="0f9f0-847">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-847">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-848">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-848">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-849">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-849">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-850">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-850">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-851">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-851">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="0f9f0-852">Intern I/O-drivrutin uppskjuten bearbetning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-852">Internal I/O Driver Deferred Processing</span></span> 

#### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="0f9f0-853">Intern I/O-drivrutin uppskjuten bearbetning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-853">Internal I/O driver deferred processing</span></span> 

<span data-ttu-id="0f9f0-854">**Ikonen** ![ Intern I/O-drivrutin för uppskjuten bearbetning](./media/user-guide/netx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-854">**Icon** ![Internal I / O driver deferred processing icon](./media/user-guide/netx-events/image42.png)</span></span>

<span data-ttu-id="0f9f0-855">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-855">**Description**</span></span>

<span data-ttu-id="0f9f0-856">Den här händelsen representerar en intern NetX I/O-drivrutin som Uppskjut bearbetnings händelsen.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-856">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="0f9f0-857">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-857">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-858">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-858">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-859">Info fält 2: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-859">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-860">Informations fält 3: paket längd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-860">Info Field 3: Packet length</span></span>
- <span data-ttu-id="0f9f0-861">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-861">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entries-invalidate"></a><span data-ttu-id="0f9f0-862">Avvalidering av dynamiska ARP-poster</span><span class="sxs-lookup"><span data-stu-id="0f9f0-862">ARP Dynamic Entries Invalidate</span></span> 

#### <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="0f9f0-863">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="0f9f0-863">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="0f9f0-864">**Ikonen** ![ En ogiltig ikon för R P dynamiska poster](./media/user-guide/netx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-864">**Icon** ![A R P Dynamic Entries Invalidate icon](./media/user-guide/netx-events/image43.png)</span></span>

<span data-ttu-id="0f9f0-865">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-865">**Description**</span></span>

<span data-ttu-id="0f9f0-866">Den här händelsen representerar invalideringen av alla dynamiska ARP-hela via nx_arp_dynamic_entries_invalidate.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-866">This event represents invalidating all dynamic ARP entires via nx_arp_dynamic_entries_invalidate.</span></span>

<span data-ttu-id="0f9f0-867">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-867">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-868">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-868">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-869">Informations fält 2: ogiltiga poster</span><span class="sxs-lookup"><span data-stu-id="0f9f0-869">Info Field 2: Entries invalidated</span></span>
- <span data-ttu-id="0f9f0-870">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-870">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-871">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-871">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entry-set"></a><span data-ttu-id="0f9f0-872">Dynamisk ARP-post uppsättning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-872">ARP Dynamic Entry Set</span></span> 

#### <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="0f9f0-873">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="0f9f0-873">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="0f9f0-874">**Ikonen** ![ En R P-ikon för dynamisk inmatnings uppsättning](./media/user-guide/netx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-874">**Icon** ![A R P Dynamic Entry Set icon](./media/user-guide/netx-events/image44.png)</span></span>

<span data-ttu-id="0f9f0-875">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-875">**Description**</span></span>

<span data-ttu-id="0f9f0-876">Den här händelsen representerar att ange en dynamisk ARP-post via nx_arp_dynamic_entry_set.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-876">This event represents setting a dynamic ARP entry via nx_arp_dynamic_entry_set.</span></span>

<span data-ttu-id="0f9f0-877">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-877">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-878">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-878">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-879">Info fält 2: IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-879">Info Field 2: IP address</span></span>
- <span data-ttu-id="0f9f0-880">Informations fält 3: fysisk adress (MSW)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-880">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="0f9f0-881">Info-fält 4: fysisk adress (LSW)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-881">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-enable"></a><span data-ttu-id="0f9f0-882">Aktivera ARP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-882">ARP Enable</span></span> 

#### <a name="nx_arp_enable"></a><span data-ttu-id="0f9f0-883">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-883">nx_arp_enable</span></span>

<span data-ttu-id="0f9f0-884">**Ikonen** ![ Ikonen R P aktivera](./media/user-guide/netx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-884">**Icon** ![A R P enable icon](./media/user-guide/netx-events/image45.png)</span></span>

<span data-ttu-id="0f9f0-885">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-885">**Description**</span></span>

<span data-ttu-id="0f9f0-886">Den här händelsen representerar aktivering av ARP via nx_arp_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-886">This event represents enabling ARP via nx_arp_enable.</span></span>

<span data-ttu-id="0f9f0-887">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-887">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-888">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-888">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-889">Informations fält 2: minnes pekare för ARP-cache</span><span class="sxs-lookup"><span data-stu-id="0f9f0-889">Info Field 2: ARP cache memory pointer</span></span>
- <span data-ttu-id="0f9f0-890">Info-fält 3: minnes storlek för ARP-cache</span><span class="sxs-lookup"><span data-stu-id="0f9f0-890">Info Field 3: ARP cache memory size</span></span>
- <span data-ttu-id="0f9f0-891">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-891">Info Field 4: Not used</span></span>

### <a name="arp-gratuitous-send"></a><span data-ttu-id="0f9f0-892">ARP, kostnads överföring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-892">ARP Gratuitous Send</span></span> 

#### <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="0f9f0-893">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="0f9f0-893">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="0f9f0-894">**Ikonen** ![ En R P-ikon för att skicka en kostnads fria sändning](./media/user-guide/netx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-894">**Icon** ![A R P gratuitous send icon](./media/user-guide/netx-events/image46.png)</span></span>

<span data-ttu-id="0f9f0-895">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-895">**Description**</span></span>

<span data-ttu-id="0f9f0-896">Den här händelsen representerar en kostnads fria ARP-sändning via nx_arp_gratuitous_send.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-896">This event represents a gratuitous ARP send via nx_arp_gratuitous_send.</span></span>

<span data-ttu-id="0f9f0-897">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-897">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-898">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-898">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-899">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-899">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-900">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-900">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-901">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-901">Info Field 4: Not used</span></span>

### <a name="arp-hardware-address-find"></a><span data-ttu-id="0f9f0-902">Sök efter ARP-maskinvara</span><span class="sxs-lookup"><span data-stu-id="0f9f0-902">ARP Hardware Address Find</span></span> 

#### <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="0f9f0-903">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="0f9f0-903">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="0f9f0-904">**Ikonen** ![ Ikonen R P P maskin varu adress Sök](./media/user-guide/netx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-904">**Icon** ![A R P Hardware Address Find icon](./media/user-guide/netx-events/image47.png)</span></span>

<span data-ttu-id="0f9f0-905">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-905">**Description**</span></span>

<span data-ttu-id="0f9f0-906">Den här händelsen representerar att hitta en fysisk adress via nx_arp_hardware_address_find.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-906">This event represents finding a physical address via nx_arp_hardware_address_find.</span></span>

<span data-ttu-id="0f9f0-907">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-907">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-908">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-908">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-909">Info fält 2: IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-909">Info Field 2: IP address</span></span>
- <span data-ttu-id="0f9f0-910">Informations fält 3: fysisk adress (MSW)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-910">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="0f9f0-911">Info-fält 4: fysisk adress (LSW)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-911">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-information-get"></a><span data-ttu-id="0f9f0-912">Hämta ARP-information</span><span class="sxs-lookup"><span data-stu-id="0f9f0-912">ARP Information Get</span></span> 

#### <a name="nx_arp_info_get"></a><span data-ttu-id="0f9f0-913">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-913">nx_arp_info_get</span></span>

<span data-ttu-id="0f9f0-914">**Ikonen** ![ En R P P informition get-ikon](./media/user-guide/netx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-914">**Icon** ![A R P informition get icon](./media/user-guide/netx-events/image48.png)</span></span>

<span data-ttu-id="0f9f0-915">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-915">**Description**</span></span>

<span data-ttu-id="0f9f0-916">Den här händelsen representerar att hämta information via nx_arp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-916">This event represents getting information via nx_arp_info_get.</span></span>

<span data-ttu-id="0f9f0-917">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-917">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-918">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-918">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-919">Informations fält 2: ARPs har skickats</span><span class="sxs-lookup"><span data-stu-id="0f9f0-919">Info Field 2: ARPs sent</span></span>
- <span data-ttu-id="0f9f0-920">Informations fält 3: ARP-svar</span><span class="sxs-lookup"><span data-stu-id="0f9f0-920">Info Field 3: ARP responses</span></span>
- <span data-ttu-id="0f9f0-921">Info fält 4: ARPs mottagen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-921">Info Field 4: ARPs received</span></span>

### <a name="arp-ip-address-find"></a><span data-ttu-id="0f9f0-922">Sök efter ARP IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-922">ARP IP Address Find</span></span> 

#### <a name="nx_arp_ip_address_find"></a><span data-ttu-id="0f9f0-923">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="0f9f0-923">nx_arp_ip_address_find</span></span>

<span data-ttu-id="0f9f0-924">**Ikonen** ![ Ikonen R P I P-adress Sök](./media/user-guide/netx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-924">**Icon** ![A R P I P address find icon](./media/user-guide/netx-events/image49.png)</span></span>

<span data-ttu-id="0f9f0-925">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-925">**Description**</span></span>

<span data-ttu-id="0f9f0-926">Den här händelsen representerar att hitta en IP-adress som är associerad med den angivna fysiska adressen via nx_arp_ip_address_find.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-926">This event represents finding an IP address associated with the supplied physical address via nx_arp_ip_address_find.</span></span>

<span data-ttu-id="0f9f0-927">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-927">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-928">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-928">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-929">Info fält 2: IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-929">Info Field 2: IP address</span></span>
- <span data-ttu-id="0f9f0-930">Informations fält 3: fysisk adress (MSW)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-930">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="0f9f0-931">Info-fält 4: fysisk adress (LSW)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-931">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entry-create"></a><span data-ttu-id="0f9f0-932">Skapa statisk ARP-post</span><span class="sxs-lookup"><span data-stu-id="0f9f0-932">ARP Static Entry Create</span></span> 

#### <a name="nx_arp_static_entry_create"></a><span data-ttu-id="0f9f0-933">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="0f9f0-933">nx_arp_static_entry_create</span></span>

<span data-ttu-id="0f9f0-934">**Ikonen** ![ En ikon för att skapa R P statisk post](./media/user-guide/netx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-934">**Icon** ![A R P static entry create icon](./media/user-guide/netx-events/image50.png)</span></span>

<span data-ttu-id="0f9f0-935">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-935">**Description**</span></span>

<span data-ttu-id="0f9f0-936">Den här händelsen representerar att skapa en statisk ARP-post via nx_arp_static_entry_create.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-936">This event represents creating a static ARP entry via nx_arp_static_entry_create.</span></span>

<span data-ttu-id="0f9f0-937">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-937">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-938">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-938">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-939">Info fält 2: IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-939">Info Field 2: IP address</span></span>
- <span data-ttu-id="0f9f0-940">Informations fält 3: fysisk adress (MSW)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-940">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="0f9f0-941">Info-fält 4: fysisk adress (LSW)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-941">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entries-delete"></a><span data-ttu-id="0f9f0-942">Ta bort ARP statiska poster</span><span class="sxs-lookup"><span data-stu-id="0f9f0-942">ARP Static Entries Delete</span></span> 

#### <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="0f9f0-943">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="0f9f0-943">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="0f9f0-944">**Ikonen** ![ Ta bort ikon för R P statisk poster](./media/user-guide/netx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-944">**Icon** ![A R P static entries delete icon](./media/user-guide/netx-events/image51.png)</span></span>

<span data-ttu-id="0f9f0-945">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-945">**Description**</span></span>

<span data-ttu-id="0f9f0-946">Den här händelsen representerar borttagning av alla statiska ARP-poster via nx_arp_static_entries_delete.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-946">This event represents deleting all ARP static entries via nx_arp_static_entries_delete.</span></span>

<span data-ttu-id="0f9f0-947">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-947">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-948">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-948">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-949">Informations fält 2: poster har tagits bort</span><span class="sxs-lookup"><span data-stu-id="0f9f0-949">Info Field 2: Entries deleted</span></span>
- <span data-ttu-id="0f9f0-950">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-950">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-951">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-951">Info Field 4: Not used</span></span>

### <a name="arp-static-entry-delete"></a><span data-ttu-id="0f9f0-952">Ta bort ARP statisk post</span><span class="sxs-lookup"><span data-stu-id="0f9f0-952">ARP Static Entry Delete</span></span> 

### <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="0f9f0-953">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="0f9f0-953">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="0f9f0-954">**Ikonen** ![ Ikonen R P statisk post Delete](./media/user-guide/netx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-954">**Icon** ![A R P static entry delete icon](./media/user-guide/netx-events/image52.png)</span></span>

<span data-ttu-id="0f9f0-955">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-955">**Description**</span></span>

<span data-ttu-id="0f9f0-956">Den här händelsen representerar borttagning av en statisk ARP-post via nx_arp_static_entry_delete.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-956">This event represents deleting a static ARP entry via nx_arp_static_entry_delete.</span></span>

<span data-ttu-id="0f9f0-957">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-957">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-958">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-958">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-959">Info fält 2: IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-959">Info Field 2: IP address</span></span>
- <span data-ttu-id="0f9f0-960">Informations fält 3: fysisk adress (MSW)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-960">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="0f9f0-961">Info-fält 4: fysisk adress (LSW)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-961">Info Field 4: Physical address (LSW)</span></span>

### <a name="duo-cache-entry-delete"></a><span data-ttu-id="0f9f0-962">Duo-cachepost ta bort</span><span class="sxs-lookup"><span data-stu-id="0f9f0-962">Duo Cache Entry Delete</span></span> 

#### <a name="nxd_und_cache_entry_delete"></a><span data-ttu-id="0f9f0-963">nxd_und_cache_entry_delete</span><span class="sxs-lookup"><span data-stu-id="0f9f0-963">nxd_und_cache_entry_delete</span></span>

<span data-ttu-id="0f9f0-964">**Ikonen** ![ Duo cache Entry ta bort ikon](./media/user-guide/netx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-964">**Icon** ![Duo cache entry delete icon](./media/user-guide/netx-events/image53.png)</span></span>

<span data-ttu-id="0f9f0-965">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-965">**Description**</span></span>

<span data-ttu-id="0f9f0-966">Den här händelsen representerar borttagning av en post i den närliggande cache-tabellen via nx_udp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-966">This event represents deleting an entry in the neighbor cache table via nx_udp_socket_create.</span></span>

<span data-ttu-id="0f9f0-967">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-967">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-968">Informations fält 1: fjärde (minst signifikant) ord för den IPv6-länk lokala adressen som ska tas bort</span><span class="sxs-lookup"><span data-stu-id="0f9f0-968">Info Field 1: Fourth (least significant) word of the IPv6 link local address to delete</span></span>
- <span data-ttu-id="0f9f0-969">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-969">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-970">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-970">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-971">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-971">Info Field 4: Not used</span></span>

### <a name="duo-cache-entry-set"></a><span data-ttu-id="0f9f0-972">Duo cache-post uppsättning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-972">Duo Cache Entry Set</span></span> 

#### <a name="nxd_nd_cache_entry_set"></a><span data-ttu-id="0f9f0-973">nxd_nd_cache_entry_set</span><span class="sxs-lookup"><span data-stu-id="0f9f0-973">nxd_nd_cache_entry_set</span></span>

<span data-ttu-id="0f9f0-974">**Ikonen** ![ Ikon för Duo cache Entry set](./media/user-guide/netx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-974">**Icon** ![Duo cache entry set icon](./media/user-guide/netx-events/image54.png)</span></span>

<span data-ttu-id="0f9f0-975">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-975">**Description**</span></span>

<span data-ttu-id="0f9f0-976">Den här händelsen representerar att skapa en cachepost och lägga till den i den närliggande cache-tabellen via nxd_nd_cache_entry_set.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-976">This event represents creating a cache entry and adding to the neighbor cache table via nxd_nd_cache_entry_set.</span></span>

<span data-ttu-id="0f9f0-977">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-977">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-978">Informations fält 1: fjärde (minst signifikant) ord för IPv6-adressen som ska läggas till</span><span class="sxs-lookup"><span data-stu-id="0f9f0-978">Info Field 1: Fourth (least significant) word of the IPv6 address to add</span></span>
- <span data-ttu-id="0f9f0-979">Info-fält 2: fysisk MSB</span><span class="sxs-lookup"><span data-stu-id="0f9f0-979">Info Field 2: Physical address msb</span></span>
- <span data-ttu-id="0f9f0-980">Info-fält 3: fysisk lsb</span><span class="sxs-lookup"><span data-stu-id="0f9f0-980">Info Field 3: Physical address lsb</span></span>
- <span data-ttu-id="0f9f0-981">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-981">Info Field 4: Not used</span></span>

### <a name="duo-cache-invalidate"></a><span data-ttu-id="0f9f0-982">Duo-cache ogiltig</span><span class="sxs-lookup"><span data-stu-id="0f9f0-982">Duo Cache Invalidate</span></span> 

#### <a name="nxd_nd_cache_invalidate"></a><span data-ttu-id="0f9f0-983">nxd_nd_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="0f9f0-983">nxd_nd_cache_invalidate</span></span>

<span data-ttu-id="0f9f0-984">**Ikonen** ![ Ikonen för Duo cache-Invalidate](./media/user-guide/netx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-984">**Icon** ![Duo cache invalidate icon](./media/user-guide/netx-events/image55.png)</span></span>

<span data-ttu-id="0f9f0-985">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-985">**Description**</span></span>

<span data-ttu-id="0f9f0-986">Den här händelsen representerar att hela den angränsande cache-tabellen ska verifieras via nxd_nd_cache_invalidate.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-986">This event represents invalidating the entire neighbor cache table via nxd_nd_cache_invalidate.</span></span>

<span data-ttu-id="0f9f0-987">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-987">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-988">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-988">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-989">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-989">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-990">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-990">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-991">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-991">Info Field 4: Not used</span></span>

### <a name="duo-cache-ip-address-find"></a><span data-ttu-id="0f9f0-992">Duo-cache IP-adress Sök</span><span class="sxs-lookup"><span data-stu-id="0f9f0-992">Duo Cache IP Address Find</span></span> 

#### <a name="nxd_nd_cache_ip_address_find"></a><span data-ttu-id="0f9f0-993">nxd_nd_cache_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="0f9f0-993">nxd_nd_cache_ip_address_find</span></span>

<span data-ttu-id="0f9f0-994">**Ikonen** ![ Duo-cache I P-adress Sök ikon](./media/user-guide/netx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-994">**Icon** ![Duo cache I P address find icon](./media/user-guide/netx-events/image56.png)</span></span>

<span data-ttu-id="0f9f0-995">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-995">**Description**</span></span>

<span data-ttu-id="0f9f0-996">Den här händelsen representerar hämtning av en IP-adress som matchar den angivna fysiska adressen från cache-tabellen via nxd_nd_cache_ip_address_find.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-996">This event represents retrieving an IP address matching the supplied physical address from the cache table via nxd_nd_cache_ip_address_find.</span></span>

<span data-ttu-id="0f9f0-997">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-997">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-998">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-998">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-999">Informations fält 2: fjärde (minst signifikant) ord för IPv6-adressen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-999">Info Field 2: Fourth (least significant) word of the IPv6 address</span></span>
- <span data-ttu-id="0f9f0-1000">Info-fält 3: fysisk MSB</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1000">Info Field 3: Physical address msb</span></span>
- <span data-ttu-id="0f9f0-1001">Info-fält 4: fysisk lsb</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1001">Info Field 4: Physical address lsb</span></span>

### <a name="duo-icmp-enable"></a><span data-ttu-id="0f9f0-1002">Duo ICMP-aktivering</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1002">Duo ICMP Enable</span></span> 

#### <a name="nxd_icmp_enable"></a><span data-ttu-id="0f9f0-1003">nxd_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1003">nxd_icmp_enable</span></span>

<span data-ttu-id="0f9f0-1004">**Ikonen** ![ Ikonen Duo I C M P Enable](./media/user-guide/netx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1004">**Icon** ![Duo I C M P enable icon](./media/user-guide/netx-events/image57.png)</span></span>

<span data-ttu-id="0f9f0-1005">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1005">**Description**</span></span>

<span data-ttu-id="0f9f0-1006">Den här händelsen representerar ICMPv4-och ICMPv6-tjänster som Aktiver ATS på den angivna IP-instansen via nxd_icmp_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1006">This event represents ICMPv4 and ICMPv6 services being enabled on the specified IP instance via nxd_icmp_enable.</span></span>

<span data-ttu-id="0f9f0-1007">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1007">**Information Fields**</span></span>
- <span data-ttu-id="0f9f0-1008">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1008">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1009">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1009">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1010">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1010">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1011">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1011">Info Field 4: Not used</span></span>

### <a name="duo-icmp-ping"></a><span data-ttu-id="0f9f0-1012">Duo ICMP-Ping</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1012">Duo ICMP Ping</span></span> 

#### <a name="nxd_icmp_ping"></a><span data-ttu-id="0f9f0-1013">nxd_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1013">nxd_icmp_ping</span></span>

<span data-ttu-id="0f9f0-1014">**Ikonen** ![ Ikonen Duo I C M P ping](./media/user-guide/netx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1014">**Icon** ![Duo I C M P ping icon](./media/user-guide/netx-events/image58.png)</span></span>

<span data-ttu-id="0f9f0-1015">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1015">**Description**</span></span>

<span data-ttu-id="0f9f0-1016">Den här händelsen representerar sändning av en ping-begäran (ekobegäran) till en IPv6-värd via nxd_icmp_ping.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1016">This event represents sending a ping (echo request) to an IPv6 host via nxd_icmp_ping.</span></span>

<span data-ttu-id="0f9f0-1017">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1017">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1018">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1018">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1019">Informations fält 2: IPv6-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1019">Info Field 2: IPv6 address</span></span>
- <span data-ttu-id="0f9f0-1020">Informations fält 3: pekar på data i eko</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1020">Info Field 3: Pointer to echo data</span></span>
- <span data-ttu-id="0f9f0-1021">Info fält 4: storlek på ECHO data</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1021">Info Field 4: Size of echo data</span></span>

### <a name="duo-ip-max-payload-size-find"></a><span data-ttu-id="0f9f0-1022">Duo IP-största nytto Last storlek hitta</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1022">Duo IP Max Payload Size Find</span></span> 

#### <a name="nxd_ip_max_payload_size"></a><span data-ttu-id="0f9f0-1023">nxd_ip_max_payload_size</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1023">nxd_ip_max_payload_size</span></span>

<span data-ttu-id="0f9f0-1024">**Ikonen** ![ Ikonen Duo I P Max storlek för nytto Last](./media/user-guide/netx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1024">**Icon** ![Duo I P max payload size find icon](./media/user-guide/netx-events/image59.png)</span></span>

<span data-ttu-id="0f9f0-1025">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1025">**Description**</span></span>

<span data-ttu-id="0f9f0-1026">Den här händelsen beräknar den maximala nytto lasten som det angivna paketet kan medföra utan fragmentering.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1026">This event computes the max payload the specified packet can carry without requiring fragmentation.</span></span>

<span data-ttu-id="0f9f0-1027">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1027">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1028">Informations fält 1: socket-pekare</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1028">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="0f9f0-1029">Informations fält 2: peer-IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1029">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="0f9f0-1030">Informations fält 3: information om peer-Port 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1030">Info Field 3: Peer port Info Field 4: Not used</span></span>

### <a name="duo-ip-raw-packet-send"></a><span data-ttu-id="0f9f0-1031">Överföring av Duo IP RAW-paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1031">Duo IP Raw Packet Send</span></span> 

#### <a name="nxd_ip_max_packet_send"></a><span data-ttu-id="0f9f0-1032">nxd_ip_max_packet_send</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1032">nxd_ip_max_packet_send</span></span>

<span data-ttu-id="0f9f0-1033">**Ikonen** ![ Ikonen Duo I P RAW Packet sändning](./media/user-guide/netx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1033">**Icon** ![Duo I P raw packet send icon](./media/user-guide/netx-events/image60.png)</span></span>

<span data-ttu-id="0f9f0-1034">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1034">**Description**</span></span>

<span data-ttu-id="0f9f0-1035">Den här händelsen representerar att skicka ett RAW IP-paket från det angivna nätverks gränssnittet till den angivna IP-addressvia nxd_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1035">This event represents sending a raw IP packet out the specified network interface to the supplied IP destination addressvia nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="0f9f0-1036">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1036">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1037">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1037">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1038">Info fält 2: pekare till paket att skicka</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1038">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="0f9f0-1039">Informations fält 3: pekare till mål adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1039">Info Field 3: Pointer to destination address</span></span>
- <span data-ttu-id="0f9f0-1040">Info-fält 4: paket protokoll</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1040">Info Field 4: Packet protocol</span></span>

### <a name="duo-ipv6-default-router-add"></a><span data-ttu-id="0f9f0-1041">Duo IPv6 standard router Lägg till</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1041">Duo IPv6 Default Router Add</span></span> 

#### <a name="nxd_ipv6_default_router_add"></a><span data-ttu-id="0f9f0-1042">nxd_ipv6_default_router_add</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1042">nxd_ipv6_default_router_add</span></span>

<span data-ttu-id="0f9f0-1043">**Ikonen** ![ Duo I P v v standard ikon för Lägg till router](./media/user-guide/netx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1043">**Icon** ![Duo I P v 6 default router add icon](./media/user-guide/netx-events/image61.png)</span></span>

<span data-ttu-id="0f9f0-1044">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1044">**Description**</span></span>

<span data-ttu-id="0f9f0-1045">Den här händelsen representerar att lägga till en standard-router till IP-instansens IPv6-routningstabell via nxd_ipv6_default_router_add.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1045">This event represents adding a default router to the IP instance's IPv6 routing table via nxd_ipv6_default_router_add.</span></span>

<span data-ttu-id="0f9f0-1046">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1046">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1047">Informations fält 1: pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1047">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="0f9f0-1048">Info-fält 2: mål nätverks adress.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1048">Info Field 2: Destination Network address.</span></span>
- <span data-ttu-id="0f9f0-1049">Info fält 3: information om livs längd.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1049">Info Field 3: Life time information.</span></span>
- <span data-ttu-id="0f9f0-1050">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1050">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-default-router-delete"></a><span data-ttu-id="0f9f0-1051">Duo IPv6 standardrouter ta bort</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1051">Duo IPv6 Default Router Delete</span></span> 

#### <a name="nxd_ipv6_default_router_delete"></a><span data-ttu-id="0f9f0-1052">nxd_ipv6_default_router_delete</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1052">nxd_ipv6_default_router_delete</span></span>

<span data-ttu-id="0f9f0-1053">**Ikonen** ![ Duo I P v v standard ikon för ta bort router](./media/user-guide/netx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1053">**Icon** ![Duo I P v 6 default router delete icon](./media/user-guide/netx-events/image62.png)</span></span>

<span data-ttu-id="0f9f0-1054">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1054">**Description**</span></span>

<span data-ttu-id="0f9f0-1055">Den här händelsen representerar borttagning av en standard-router från IP-instansens IPv6-routningstabell via nxd_ipv6_default_router_delete.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1055">This event represents removing a default router from the IP instance's IPv6 routing table via nxd_ipv6_default_router_delete.</span></span>

<span data-ttu-id="0f9f0-1056">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1056">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1057">Informations fält 1: pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1057">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="0f9f0-1058">Informations fält 2: fjärde ordet (minst signifikant) av IPv6-standardadressen för router.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1058">Info Field 2: Fourth word (least significant) of the default router IPv6 address.</span></span>
- <span data-ttu-id="0f9f0-1059">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="0f9f0-1060">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1060">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-enable"></a><span data-ttu-id="0f9f0-1061">Duo IPv6 Enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1061">Duo IPv6 Enable</span></span> 

#### <a name="nxd_ipv6_enable"></a><span data-ttu-id="0f9f0-1062">nxd_ipv6_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1062">nxd_ipv6_enable</span></span>

<span data-ttu-id="0f9f0-1063">**Ikonen** ![ Duo I P v v v Aktivera ikon](./media/user-guide/netx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1063">**Icon** ![Duo I P v 6 enable icon](./media/user-guide/netx-events/image63.png)</span></span>

<span data-ttu-id="0f9f0-1064">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1064">**Description**</span></span>

<span data-ttu-id="0f9f0-1065">Den här händelsen representerar aktivering av IPv6-tjänster på den angivna IP-instansen via nxd_ipv6_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1065">This event represents enabling IPv6 services on the supplied IP instance via nxd_ipv6_enable.</span></span>

<span data-ttu-id="0f9f0-1066">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1066">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1067">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1067">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1068">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1068">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1069">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1069">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1070">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1070">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-global-address-get"></a><span data-ttu-id="0f9f0-1071">Global adress för Duo IPv6 get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1071">Duo IPv6 Global Address Get</span></span> 

#### <a name="nxd_ipv6_global_address_get"></a><span data-ttu-id="0f9f0-1072">nxd_ipv6_global_address_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1072">nxd_ipv6_global_address_get</span></span>

<span data-ttu-id="0f9f0-1073">**Ikonen** ![ Ikonen Duo I P v v 6 global adress Hämta](./media/user-guide/netx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1073">**Icon** ![Duo I P v 6 global address get icon](./media/user-guide/netx-events/image64.png)</span></span>

<span data-ttu-id="0f9f0-1074">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1074">**Description**</span></span>

<span data-ttu-id="0f9f0-1075">Den här händelsen representerar hämtning av den globala (primära) IP-adressen på IP-instansen som finns på index 1 i tabellen IP-instans-gränssnitt via nxd_ipv6_global_address_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1075">This event represents retrieving the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_get.</span></span>

<span data-ttu-id="0f9f0-1076">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1076">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1077">Informations fält 1: pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1077">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="0f9f0-1078">Informations fält 2: fjärde ordet (minst signifikant) av den globala adressen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1078">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="0f9f0-1079">Info-fält 3: längden på IPv6-adressprefixet.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1079">Info Field 3: IPv6 address prefix length.</span></span>
- <span data-ttu-id="0f9f0-1080">Info fält 4: index i IP-gränssnitts tabell (1).</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1080">Info Field 4: Index into IP interface table (1).</span></span>

### <a name="duo-ipv6-global-address-set"></a><span data-ttu-id="0f9f0-1081">Global adress uppsättning för Duo IPv6</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1081">Duo IPv6 Global Address Set</span></span> 

#### <a name="nxd_ipv6_global_address_set"></a><span data-ttu-id="0f9f0-1082">nxd_ipv6_global_address_set</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1082">nxd_ipv6_global_address_set</span></span>

<span data-ttu-id="0f9f0-1083">**Ikonen** ![ Ikonen Duo I P v v v 6, global adress uppsättning](./media/user-guide/netx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1083">**Icon** ![Duo I P v 6 global address set icon](./media/user-guide/netx-events/image65.png)</span></span>

<span data-ttu-id="0f9f0-1084">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1084">**Description**</span></span>

<span data-ttu-id="0f9f0-1085">Den här händelsen representerar att ange den globala (primära) IP-adressen på IP-instansen som finns på index 1 i tabellen IP-instans-gränssnitt via nxd_ipv6_global_address_set.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1085">This event represents setting the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_set.</span></span>

<span data-ttu-id="0f9f0-1086">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1086">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1087">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1087">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1088">Informations fält 2: fjärde ordet (minst signifikant) av den globala adressen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1088">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="0f9f0-1089">Informations fält 3: längden på IPv6-adressprefixet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1089">Info Field 3: IPv6 address prefix length</span></span>
- <span data-ttu-id="0f9f0-1090">Info fält 4: index i IP-gränssnitts tabell (1)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1090">Info Field 4: Index into IP interface table (1)</span></span>

### <a name="duo-ipv6-initiate-dad-process"></a><span data-ttu-id="0f9f0-1091">Duo IPv6-initiera pappa-process</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1091">Duo IPv6 Initiate Dad Process</span></span> 

#### <a name="nxd_ipv6_initiate_dad_process"></a><span data-ttu-id="0f9f0-1092">nxd_ipv6_initiate_dad_process</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1092">nxd_ipv6_initiate_dad_process</span></span>

<span data-ttu-id="0f9f0-1093">**Ikonen** ![ Duo I P v v v Starta pappa-process ikon](./media/user-guide/netx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1093">**Icon** ![Duo I P v 6 initiate dad process icon](./media/user-guide/netx-events/image66.png)</span></span>

<span data-ttu-id="0f9f0-1094">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1094">**Description**</span></span>

<span data-ttu-id="0f9f0-1095">Den här händelsen representerar start processen för den duplicerade adress identifieringen (pappa) när IP-instansen tilldelas en länk lokal eller IP-gränssnitts adress via nxd_ipv6_initiate_dad_process.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1095">This event represents the start of the Duplicate Address Detection (DAD) process when the IP instance is assigned a link local or an IP interface address via nxd_ipv6_initiate_dad_process.</span></span>

<span data-ttu-id="0f9f0-1096">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1096">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1097">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1097">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1098">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1098">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1099">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1099">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1100">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1100">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-interface-address-get"></a><span data-ttu-id="0f9f0-1101">Duo IPv6-gränssnitt adress Hämta</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1101">Duo IPv6 Interface Address Get</span></span> 

#### <a name="nxd_ipv6_interface_address_get"></a><span data-ttu-id="0f9f0-1102">nxd_ipv6_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1102">nxd_ipv6_interface_address_get</span></span>

<span data-ttu-id="0f9f0-1103">**Ikonen** ![ Duo I P v v v-ikonen Hämta ikon](./media/user-guide/netx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1103">**Icon** ![Duo I P v 6 interface address get icon](./media/user-guide/netx-events/image67.png)</span></span>

<span data-ttu-id="0f9f0-1104">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1104">**Description**</span></span>

<span data-ttu-id="0f9f0-1105">Den här händelsen representerar hämtning av IP-adressen och prefixet vid det angivna indexet i IP-instansens gränssnitts adress tabell via nxd_ipv6_interface_address_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1105">This event represents retrieving the IP address and prefix at the specified index into the IP instance interface address table via nxd_ipv6_interface_address_get.</span></span>

<span data-ttu-id="0f9f0-1106">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1106">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1107">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1107">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1108">Informations fält 2: fjärde ordet (minst signifikant) för IPv6-adressen som ska returneras</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1108">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="0f9f0-1109">Info-fält 4: index för gränssnittet i IP-instansens gränssnitts tabell</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1109">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-interface-address-set"></a><span data-ttu-id="0f9f0-1110">Adress uppsättning för Duo IPv6-gränssnitt</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1110">Duo IPv6 Interface Address Set</span></span> 

### <a name="nxd_ipv6_interface_address_set"></a><span data-ttu-id="0f9f0-1111">nxd_ipv6_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1111">nxd_ipv6_interface_address_set</span></span>

<span data-ttu-id="0f9f0-1112">**Ikonen** ![ Duo-ikonen I P v v v-gränssnittet](./media/user-guide/netx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1112">**Icon** ![Duo I P v 6 interface addresss et icon](./media/user-guide/netx-events/image68.png)</span></span>

<span data-ttu-id="0f9f0-1113">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1113">**Description**</span></span>

<span data-ttu-id="0f9f0-1114">Den här händelsen representerar att ange IP-adressen och prefixet vid det angivna indexet i adress tabellen för IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1114">This event represents setting the IP address and prefix at the specified index into the IP instance interface address table.</span></span> <span data-ttu-id="0f9f0-1115">Tillåts inte för index noll (länk lokal adress) via nxd_ipv6_interface_address_set.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1115">Not permitted on index zero (link local address) via nxd_ipv6_interface_address_set.</span></span>

<span data-ttu-id="0f9f0-1116">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1116">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1117">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1117">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1118">Informations fält 2: fjärde ordet (minst signifikant) för IPv6-adressen som ska returneras</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1118">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="0f9f0-1119">Informations fält 3: prefixlängd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1119">Info Field 3: Prefix length</span></span>
- <span data-ttu-id="0f9f0-1120">Info-fält 4: index för gränssnittet i IP-instansens gränssnitts tabell</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1120">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-link-local-address-get"></a><span data-ttu-id="0f9f0-1121">Duo IPv6-länk lokal adress Hämta</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1121">Duo IPv6 Link Local Address Get</span></span> 

#### <a name="nxd_ipv6_linklocal_address_get"></a><span data-ttu-id="0f9f0-1122">nxd_ipv6_linklocal_address_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1122">nxd_ipv6_linklocal_address_get</span></span>

<span data-ttu-id="0f9f0-1123">**Ikonen** ![ Ikonen Duo I P v v v länk lokal adress Hämta ikon](./media/user-guide/netx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1123">**Icon** ![Duo I P v 6 link local address get icon](./media/user-guide/netx-events/image69.png)</span></span>

<span data-ttu-id="0f9f0-1124">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1124">**Description**</span></span>

<span data-ttu-id="0f9f0-1125">Den här händelsen representerar hämtning av länkens lokala adress för den angivna IP-instansen via nxd_ipv6_linklocal_address_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1125">This event represents retrieving the link local address of the specified IP instance via nxd_ipv6_linklocal_address_get.</span></span>

<span data-ttu-id="0f9f0-1126">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1126">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1127">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1127">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1128">Informations fält 2: fjärde ordet (minst signifikant) av IP V6-länkens lokala adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1128">Info Field 2: Fourth word (least significant) of the IP v6 link local address</span></span>
- <span data-ttu-id="0f9f0-1129">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1129">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1130">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1130">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-link-local-address-set"></a><span data-ttu-id="0f9f0-1131">Duo IPv6-länk lokal adress uppsättning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1131">Duo IPv6 Link Local Address Set</span></span> 

#### <a name="nxd_ipv6_linklocal_address_set"></a><span data-ttu-id="0f9f0-1132">nxd_ipv6_linklocal_address_set</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1132">nxd_ipv6_linklocal_address_set</span></span>

<span data-ttu-id="0f9f0-1133">**Ikonen** ![ Ikonen Duo I P v v v-länk lokalt adress uppsättning](./media/user-guide/netx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1133">**Icon** ![Duo I P v 6 link local address set icon](./media/user-guide/netx-events/image70.png)</span></span>

<span data-ttu-id="0f9f0-1134">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1134">**Description**</span></span>

<span data-ttu-id="0f9f0-1135">Den här händelsen representerar att ange den lokala länk adressen för IP-instansen via nxd_ipv6_linklocal_address_set.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1135">This event represents setting the link local address of the IP instance via nxd_ipv6_linklocal_address_set.</span></span>

<span data-ttu-id="0f9f0-1136">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1136">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1137">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1137">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1138">Informations fält 2: fjärde (minst signifikant) ord för IPv6-länkens lokala adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1138">Info Field 2: Fourth (least significant) word of the IPv6 link local address</span></span>
- <span data-ttu-id="0f9f0-1139">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1139">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1140">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1140">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-raw-packet-send"></a><span data-ttu-id="0f9f0-1141">Duo IPv6 RAW-paket sändning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1141">Duo IPv6 Raw Packet Send</span></span> 

#### <a name="nxd_ipv6_raw_packet_send"></a><span data-ttu-id="0f9f0-1142">nxd_ipv6_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1142">nxd_ipv6_raw_packet_send</span></span>

<span data-ttu-id="0f9f0-1143">**Ikonen** ![ Duo I P v v v-ikon för RAW Packet-sändning](./media/user-guide/netx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1143">**Icon** ![Duo I P v 6 raw packet send icon](./media/user-guide/netx-events/image71.png)</span></span>

<span data-ttu-id="0f9f0-1144">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1144">**Description**</span></span>

<span data-ttu-id="0f9f0-1145">Den här händelsen representerar att skicka ett RAW IP-paket via det primära IP-gränssnittet till Proxyport anges-målet via nxd_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1145">This event represents sending a raw IP packet through the primary IP interface to the speficied destination via nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="0f9f0-1146">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1146">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1147">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1147">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1148">Info fält 2: pekare till paket att skicka</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1148">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="0f9f0-1149">Informations fält 3: målets IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1149">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="0f9f0-1150">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1150">Info Field 4: Not used</span></span>

### <a name="duo-tcp-socket-peer-info-get"></a><span data-ttu-id="0f9f0-1151">Duo TCP socket peer information get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1151">Duo TCP Socket Peer Info Get</span></span> 

#### <a name="nxd_tcp_socket_peer_info_get"></a><span data-ttu-id="0f9f0-1152">nxd_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1152">nxd_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="0f9f0-1153">**Ikonen** ![ Duo T C P socket peer information get ikon](./media/user-guide/netx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1153">**Icon** ![Duo T C P socket peer info get icon](./media/user-guide/netx-events/image72.png)</span></span>

<span data-ttu-id="0f9f0-1154">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1154">**Description**</span></span>

<span data-ttu-id="0f9f0-1155">Den här händelsen extraherar avsändar data från ett mottaget TCP-paket på den angivna socketen.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1155">This event extracts the sender data from a received TCP packet on the specified socket.</span></span> <span data-ttu-id="0f9f0-1156">Den returnerar avsändarens IP-adress och port.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1156">It returns the IP address and port of the sender.</span></span>

<span data-ttu-id="0f9f0-1157">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1157">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1158">Informations fält 1: socket-pekare</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1158">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="0f9f0-1159">Informations fält 2: peer-IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1159">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="0f9f0-1160">Informations fält 3: peer-port</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1160">Info Field 3: Peer port</span></span>
- <span data-ttu-id="0f9f0-1161">Info-fält 4: lånet är signifikant 32-bitars IP-adressen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1161">Info Field 4: The lease significant 32-bit of the IP address</span></span>

### <a name="duo-tcp-socket-set-interface"></a><span data-ttu-id="0f9f0-1162">Duo TCP socket set Interface</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1162">Duo TCP Socket Set Interface</span></span> 

#### <a name="nxd_tcp_socket_set_interface"></a><span data-ttu-id="0f9f0-1163">nxd_tcp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1163">nxd_tcp_socket_set_interface</span></span>

<span data-ttu-id="0f9f0-1164">**Ikonen** ![ Ikonen Duo T C P socket set Interface](./media/user-guide/netx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1164">**Icon** ![Duo T C P socket set interface icon](./media/user-guide/netx-events/image73.png)</span></span>

<span data-ttu-id="0f9f0-1165">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1165">**Description**</span></span>

<span data-ttu-id="0f9f0-1166">Den här händelsen representerar att ange utgående socket-gränssnitt när en klient ansluter med en TCP-server på den angivna serverns IP-adress via nxd_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1166">This event represents setting the outgoing socket interface after a client connects with a TCP server on the specified server IP address via nxd_tcp_client_socket_connect.</span></span>

<span data-ttu-id="0f9f0-1167">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1167">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1168">Informations fält 1: pekare till TCP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1168">Info Field 1: Pointer to TCP Socket</span></span>
- <span data-ttu-id="0f9f0-1169">Informations fält 2: gränssnitts-ID</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1169">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="0f9f0-1170">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1170">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1171">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1171">Info Field 4: Not used</span></span>

### <a name="duo-udp-socket-send"></a><span data-ttu-id="0f9f0-1172">Duo UDP-socket skicka</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1172">Duo UDP Socket Send</span></span> 

#### <a name="nxd_udp_socket_send"></a><span data-ttu-id="0f9f0-1173">nxd_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1173">nxd_udp_socket_send</span></span>

<span data-ttu-id="0f9f0-1174">**Ikonen** ![ Duo U D P uttag ikon för skicka](./media/user-guide/netx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1174">**Icon** ![Duo U D P socket send icon](./media/user-guide/netx-events/image74.png)</span></span>

<span data-ttu-id="0f9f0-1175">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1175">**Description**</span></span>

<span data-ttu-id="0f9f0-1176">Den här händelsen representerar att skicka ett UDP-paket via den angivna socketen med IP-adressen för indata och port via nxd_udp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1176">This event represents sending a UDP packet through the specified socket with the input IP address and port via nxd_udp_socket_send.</span></span>

<span data-ttu-id="0f9f0-1177">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1177">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1178">Info fält 1: pekare UDP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1178">Info Field 1: Pointer UDP Socket</span></span>
- <span data-ttu-id="0f9f0-1179">Info fält 2: pekare till UDP-paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1179">Info Field 2: Pointer to UDP packet</span></span>
- <span data-ttu-id="0f9f0-1180">Informations fält 3: paket längd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1180">Info Field 3: Packet length</span></span>
- <span data-ttu-id="0f9f0-1181">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1181">Info Field 4: Not used</span></span>


### <a name="duo-udp-socket-set-interface"></a><span data-ttu-id="0f9f0-1182">Duo UDP socket set Interface</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1182">Duo UDP Socket Set Interface</span></span> 

#### <a name="nxd_udp_socket_set_interface"></a><span data-ttu-id="0f9f0-1183">nxd_udp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1183">nxd_udp_socket_set_interface</span></span>

<span data-ttu-id="0f9f0-1184">**Ikonen** ![ Ikonen Duo U D P socket set Interface](./media/user-guide/netx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1184">**Icon** ![Duo U D P socket set interface icon](./media/user-guide/netx-events/image75.png)</span></span>

<span data-ttu-id="0f9f0-1185">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1185">**Description**</span></span>

<span data-ttu-id="0f9f0-1186">Den här händelsen representerar inställningen för det angivna utgående UDP-socket-gränssnittet till gränssnittet som motsvarar ID för indataports-gränssnitt via nxd_udp_socket_set_interface.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1186">This event represents setting the specified UDP socket outgoing interface to the interface corresponding to the input interface ID via nxd_udp_socket_set_interface.</span></span>

<span data-ttu-id="0f9f0-1187">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1187">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1188">Info fält 1: pekare till UDP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1188">Info Field 1: Pointer to UDP Socket</span></span>
- <span data-ttu-id="0f9f0-1189">Informations fält 2: gränssnitts-ID</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1189">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="0f9f0-1190">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1190">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1191">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1191">Info Field 4: Not used</span></span>

### <a name="duo-udp-source-extract"></a><span data-ttu-id="0f9f0-1192">Duo UDP-käll extrahering</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1192">Duo UDP Source Extract</span></span> 

#### <a name="nxd_udp_socket_extract"></a><span data-ttu-id="0f9f0-1193">nxd_udp_socket_extract</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1193">nxd_udp_socket_extract</span></span>

<span data-ttu-id="0f9f0-1194">**Ikonen** ![ Duo U D P-käll extraherings ikon](./media/user-guide/netx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1194">**Icon** ![Duo U D P source extract icon](./media/user-guide/netx-events/image76.png)</span></span>

<span data-ttu-id="0f9f0-1195">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1195">**Description**</span></span>

<span data-ttu-id="0f9f0-1196">Den här händelsen representerar extrahering av IP-adressen och käll porten för ett mottaget paket (antingen IPv4 eller IPv6).</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1196">This event represents extracting the IP address and source port of a received packet (either IPv4 or IPv6).</span></span> <span data-ttu-id="0f9f0-1197">Om IPv6 returneras det fjärde ordet (minst signifikant) av IP-adressen via nxd_udp_source_extract.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1197">If IPv6, the fourth word (least significant) of the IP address is returned via nxd_udp_source_extract.</span></span>

<span data-ttu-id="0f9f0-1198">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1198">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1199">Info fält 1: pekar mot paketet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1199">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="0f9f0-1200">Informations fält 2: IP-version</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1200">Info Field 2: IP version</span></span>
- <span data-ttu-id="0f9f0-1201">Informations fält 3: Källans IP-adress (IPv4 eller IPv6)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1201">Info Field 3: Source IP address (IPv4 or IPv6)</span></span>
- <span data-ttu-id="0f9f0-1202">Info-fält 4: källport</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1202">Info Field 4: Source port</span></span>

### <a name="icmp-enable"></a><span data-ttu-id="0f9f0-1203">ICMP-aktivering</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1203">ICMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="0f9f0-1204">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1204">nx_icmp_enable</span></span>

<span data-ttu-id="0f9f0-1205">**Ikonen** ![ I C M P Enable-ikon](./media/user-guide/netx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1205">**Icon** ![I C M P enable icon](./media/user-guide/netx-events/image77.png)</span></span>

<span data-ttu-id="0f9f0-1206">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1206">**Description**</span></span>

<span data-ttu-id="0f9f0-1207">Den här händelsen representerar aktivering av ICMP via nx_icmp_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1207">This event represents enabling ICMP via nx_icmp_enable.</span></span>

<span data-ttu-id="0f9f0-1208">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1208">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1209">Info fält 1: pekare till IP-instansen l;</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1209">Info Field 1: Pointer to the IP instance l;</span></span>
- <span data-ttu-id="0f9f0-1210">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1210">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1211">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1211">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1212">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1212">Info Field 4: Not used</span></span>

### <a name="icmp-information-get"></a><span data-ttu-id="0f9f0-1213">ICMP information get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1213">ICMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="0f9f0-1214">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1214">nx_icmp_info_get</span></span>

<span data-ttu-id="0f9f0-1215">**Ikonen** ![ I C M P information get-ikonen](./media/user-guide/netx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1215">**Icon** ![I C M P information get icon](./media/user-guide/netx-events/image78.png)</span></span>

<span data-ttu-id="0f9f0-1216">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1216">**Description**</span></span>

<span data-ttu-id="0f9f0-1217">Den här händelsen representerar att hämta information via nx_icmp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1217">This event represents getting information via nx_icmp_info_get.</span></span>

<span data-ttu-id="0f9f0-1218">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1218">**Information Fields**</span></span>
- <span data-ttu-id="0f9f0-1219">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1219">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1220">Informations fält 2: pingar skickas</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1220">Info Field 2: Pings sent</span></span>
- <span data-ttu-id="0f9f0-1221">Info-fält 3: ping-svar</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1221">Info Field 3: Ping responses</span></span>
- <span data-ttu-id="0f9f0-1222">Info fält 4: mottagna pingar</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1222">Info Field 4: Pings received</span></span>

### <a name="icmp-ping"></a><span data-ttu-id="0f9f0-1223">ICMP-Ping</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1223">ICMP Ping</span></span> 

#### <a name="nx_icmp_ping"></a><span data-ttu-id="0f9f0-1224">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1224">nx_icmp_ping</span></span>

<span data-ttu-id="0f9f0-1225">**Ikonen** ![ I C M P ping-ikonen](./media/user-guide/netx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1225">**Icon** ![I C M P ping icon](./media/user-guide/netx-events/image79.png)</span></span>

<span data-ttu-id="0f9f0-1226">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1226">**Description**</span></span>

<span data-ttu-id="0f9f0-1227">Den här händelsen representerar pinga en mål-IP-adress via nx_icmp_ping.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1227">This event represents pinging a target IP address via nx_icmp_ping.</span></span>

<span data-ttu-id="0f9f0-1228">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1228">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1229">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1229">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1230">Info fält 2: IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1230">Info Field 2: IP address</span></span>
- <span data-ttu-id="0f9f0-1231">Informations fält 3: pekare till data</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1231">Info Field 3: Pointer to data</span></span>
- <span data-ttu-id="0f9f0-1232">Info fält 4: data storlek</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1232">Info Field 4: Size of data</span></span>

### <a name="igmp-enable"></a><span data-ttu-id="0f9f0-1233">Aktivera IGMP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1233">IGMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="0f9f0-1234">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1234">nx_icmp_enable</span></span>

<span data-ttu-id="0f9f0-1235">**Ikonen** ![ I G M P Enable-ikon](./media/user-guide/netx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1235">**Icon** ![I G M P enable icon](./media/user-guide/netx-events/image80.png)</span></span>

<span data-ttu-id="0f9f0-1236">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1236">**Description**</span></span>

<span data-ttu-id="0f9f0-1237">Den här händelsen representerar aktivering av IGMP via nx_igmp_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1237">This event represents enabling IGMP via nx_igmp_enable.</span></span>

<span data-ttu-id="0f9f0-1238">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1238">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1239">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1239">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1240">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1240">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1241">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1241">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1242">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1242">Info Field 4: Not used</span></span>

### <a name="igmp-information-get"></a><span data-ttu-id="0f9f0-1243">Hämta IGMP-information</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1243">IGMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="0f9f0-1244">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1244">nx_icmp_info_get</span></span>

<span data-ttu-id="0f9f0-1245">**Ikonen** ![ I G M P information get-ikon](./media/user-guide/netx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1245">**Icon** ![I G M P information get icon](./media/user-guide/netx-events/image81.png)</span></span>

<span data-ttu-id="0f9f0-1246">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1246">**Description**</span></span>

<span data-ttu-id="0f9f0-1247">Den här händelsen representerar att hämta information via nx_igmp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1247">This event represents getting information via nx_igmp_info_get.</span></span>

<span data-ttu-id="0f9f0-1248">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1248">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1249">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1249">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1250">Informations fält 2: rapporter har skickats</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1250">Info Field 2: Reports sent</span></span>
- <span data-ttu-id="0f9f0-1251">Informations fält 3: frågor mottagna</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1251">Info Field 3: Queries received</span></span>
- <span data-ttu-id="0f9f0-1252">Info fält 4: grupper kopplade</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1252">Info Field 4: Groups joined</span></span>

### <a name="igmp-loopback-disable"></a><span data-ttu-id="0f9f0-1253">Inaktivera IGMP loopback</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1253">IGMP Loopback Disable</span></span> 

#### <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="0f9f0-1254">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1254">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="0f9f0-1255">**Ikonen** ![ I G M P loopback inaktivera ikon](./media/user-guide/netx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1255">**Icon** ![I G M P loopback disable icon](./media/user-guide/netx-events/image82.png)</span></span>

<span data-ttu-id="0f9f0-1256">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1256">**Description**</span></span>

<span data-ttu-id="0f9f0-1257">Den här händelsen representerar inaktive ring av IGMP loopback via nx_igmp_loopback_disable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1257">This event represents disabling IGMP loopback via nx_igmp_loopback_disable.</span></span>

<span data-ttu-id="0f9f0-1258">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1258">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1259">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1259">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1260">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1260">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1261">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1261">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1262">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1262">Info Field 4: Not used</span></span>

### <a name="igmp-loopback-enable"></a><span data-ttu-id="0f9f0-1263">Aktivera IGMP loopback</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1263">IGMP Loopback Enable</span></span> 

#### <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="0f9f0-1264">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1264">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="0f9f0-1265">**Ikonen** ![ I G M P loopback Aktivera ikon](./media/user-guide/netx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1265">**Icon** ![I G M P loopback enable icon](./media/user-guide/netx-events/image83.png)</span></span>

<span data-ttu-id="0f9f0-1266">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1266">**Description**</span></span>

<span data-ttu-id="0f9f0-1267">Den här händelsen representerar aktivering av IGMP loopback via nx_igmp_loopback_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1267">This event represents enabling IGMP loopback via nx_igmp_loopback_enable.</span></span>

<span data-ttu-id="0f9f0-1268">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1268">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1269">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1269">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1270">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1270">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1271">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1271">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1272">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1272">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-join"></a><span data-ttu-id="0f9f0-1273">IGMP multicast-anslutning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1273">IGMP Multicast Join</span></span> 

#### <a name="nx_igmp_multicast_join"></a><span data-ttu-id="0f9f0-1274">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1274">nx_igmp_multicast_join</span></span>

<span data-ttu-id="0f9f0-1275">**Ikonen** ![ I G M P-ikon för multicast-anslutning](./media/user-guide/netx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1275">**Icon** ![I G M P multicast join icon](./media/user-guide/netx-events/image84.png)</span></span>

<span data-ttu-id="0f9f0-1276">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1276">**Description**</span></span>

<span data-ttu-id="0f9f0-1277">Den här händelsen representerar anslutning till en multicast-grupp via nx_igmp_multicast_join.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1277">This event represents joining a multicast group via nx_igmp_multicast_join.</span></span>

<span data-ttu-id="0f9f0-1278">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1278">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1279">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1279">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1280">Info fält 2: grupp-IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1280">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="0f9f0-1281">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1281">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1282">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1282">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-leave"></a><span data-ttu-id="0f9f0-1283">IGMP multicast-tjänstledighet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1283">IGMP Multicast Leave</span></span> 

#### <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="0f9f0-1284">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1284">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="0f9f0-1285">**Ikonen** ![ Ikonen I G M P multicast-tjänstledighet](./media/user-guide/netx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1285">**Icon** ![I G M P multicast leave icon](./media/user-guide/netx-events/image85.png)</span></span>

<span data-ttu-id="0f9f0-1286">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1286">**Description**</span></span>

<span data-ttu-id="0f9f0-1287">Den här händelsen representerar att lämna en multicast-grupp via nx_igmp_multicast_leave.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1287">This event represents leaving a multicast group via nx_igmp_multicast_leave.</span></span>

<span data-ttu-id="0f9f0-1288">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1288">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1289">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1289">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1290">Info fält 2: grupp-IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1290">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="0f9f0-1291">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1291">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1292">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1292">Info Field 4: Not used</span></span>

### <a name="ip-address-change-notify"></a><span data-ttu-id="0f9f0-1293">Avisering om ändring av IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1293">IP Address Change Notify</span></span> 

#### <a name="nx_ip_address_change_notify"></a><span data-ttu-id="0f9f0-1294">nx_ip_address_change_notify</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1294">nx_ip_address_change_notify</span></span>

<span data-ttu-id="0f9f0-1295">**Ikonen** ![ I P adress ändrings aviserings ikon](./media/user-guide/netx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1295">**Icon** ![I P address change notify icon](./media/user-guide/netx-events/image86.png)</span></span>

<span data-ttu-id="0f9f0-1296">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1296">**Description**</span></span>

<span data-ttu-id="0f9f0-1297">Den här händelsen representerar registrering för meddelanden om IP-ändring via nx_ip_address_change_notify.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1297">This event represents registering for IP change notification via nx_ip_address_change_notify.</span></span>

<span data-ttu-id="0f9f0-1298">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1298">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1299">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1299">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1300">Informations fält 2: återanrops funktions pekare</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1300">Info Field 2: Callback function pointer</span></span>
- <span data-ttu-id="0f9f0-1301">Informations fält 3: ytterligare informations pekare</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1301">Info Field 3: Additional information pointer</span></span>
- <span data-ttu-id="0f9f0-1302">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1302">Info Field 4: Not used</span></span>

### <a name="ip-address-get"></a><span data-ttu-id="0f9f0-1303">Hämta IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1303">IP Address Get</span></span> 

#### <a name="nx_ip_address_get"></a><span data-ttu-id="0f9f0-1304">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1304">nx_ip_address_get</span></span>

<span data-ttu-id="0f9f0-1305">**Ikonen** ![ Hämta ikon för mitt P-adress](./media/user-guide/netx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1305">**Icon** ![I P address get icon](./media/user-guide/netx-events/image87.png)</span></span>

<span data-ttu-id="0f9f0-1306">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1306">**Description**</span></span>

<span data-ttu-id="0f9f0-1307">Den här händelsen representerar hämtning av IP-adressen via nx_ip_address_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1307">This event represents getting the IP address via nx_ip_address_get.</span></span>

<span data-ttu-id="0f9f0-1308">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1308">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1309">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1309">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1310">Info fält 2: IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1310">Info Field 2: IP address</span></span>
- <span data-ttu-id="0f9f0-1311">Informations fält 3: nätverks mask</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1311">Info Field 3: Network mask</span></span>
- <span data-ttu-id="0f9f0-1312">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1312">Info Field 4: Not used</span></span>

### <a name="ip-address-set"></a><span data-ttu-id="0f9f0-1313">IP-adress uppsättning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1313">IP Address Set</span></span> 

#### <a name="nx_ip_address_set"></a><span data-ttu-id="0f9f0-1314">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1314">nx_ip_address_set</span></span>

<span data-ttu-id="0f9f0-1315">**Ikonen** ![ Ikonen I P Address set](./media/user-guide/netx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1315">**Icon** ![I P address set icon](./media/user-guide/netx-events/image88.png)</span></span>

<span data-ttu-id="0f9f0-1316">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1316">**Description**</span></span>

<span data-ttu-id="0f9f0-1317">Den här händelsen representerar att ange IP-adressen via nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1317">This event represents setting the IP address via nx_ip_address_set.</span></span>

<span data-ttu-id="0f9f0-1318">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1318">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1319">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1319">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1320">Info fält 2: IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1320">Info Field 2: IP address</span></span>
- <span data-ttu-id="0f9f0-1321">Informations fält 3: nätverks mask</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1321">Info Field 3: Network mask</span></span>
- <span data-ttu-id="0f9f0-1322">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1322">Info Field 4: Not used</span></span>

### <a name="ip-create"></a><span data-ttu-id="0f9f0-1323">Skapa IP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1323">IP Create</span></span> 

#### <a name="nx_ip_create"></a><span data-ttu-id="0f9f0-1324">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1324">nx_ip_create</span></span>

<span data-ttu-id="0f9f0-1325">**Ikonen** ![ I P skapa ikon](./media/user-guide/netx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1325">**Icon** ![I P create icon](./media/user-guide/netx-events/image89.png)</span></span>

<span data-ttu-id="0f9f0-1326">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1326">**Description**</span></span>

<span data-ttu-id="0f9f0-1327">Den här händelsen representerar att skapa en IP-instans via nx_ip_create.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1327">This event represents creating an IP instance via nx_ip_create.</span></span>

<span data-ttu-id="0f9f0-1328">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1328">**Information Fields**</span></span> 
- <span data-ttu-id="0f9f0-1329">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1329">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1330">Info fält 2: IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1330">Info Field 2: IP address</span></span>
- <span data-ttu-id="0f9f0-1331">Informations fält 3: nätverks mask</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1331">Info Field 3: Network mask</span></span>
- <span data-ttu-id="0f9f0-1332">Info fält 4: standard pekare för Packet pool</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1332">Info Field 4: Default packet pool pointer</span></span>

### <a name="ip-delete"></a><span data-ttu-id="0f9f0-1333">Ta bort IP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1333">IP Delete</span></span> 

#### <a name="nx_ip_delete"></a><span data-ttu-id="0f9f0-1334">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1334">nx_ip_delete</span></span>

<span data-ttu-id="0f9f0-1335">**Ikonen** ![ I P ta bort-ikonen](./media/user-guide/netx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1335">**Icon** ![I P delete icon](./media/user-guide/netx-events/image90.png)</span></span>

<span data-ttu-id="0f9f0-1336">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1336">**Description**</span></span>

<span data-ttu-id="0f9f0-1337">Den här händelsen representerar borttagning av en IP-instans via nx_ip_delete.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1337">This event represents deleting an IP instance via nx_ip_delete.</span></span>

<span data-ttu-id="0f9f0-1338">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1338">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1339">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1339">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1340">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1340">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1341">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1341">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1342">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1342">Info Field 4: Not used</span></span>

### <a name="ip-driver-direct-command"></a><span data-ttu-id="0f9f0-1343">IP-drivrutin Direct-kommando</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1343">IP Driver Direct Command</span></span> 

#### <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="0f9f0-1344">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1344">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="0f9f0-1345">**Ikonen** ![ I P driv rutin Direct kommando ikon](./media/user-guide/netx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1345">**Icon** ![I P driver direct command icon](./media/user-guide/netx-events/image91.png)</span></span>

<span data-ttu-id="0f9f0-1346">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1346">**Description**</span></span>

<span data-ttu-id="0f9f0-1347">Den här händelsen representerar ett direkt I/O-drivrutins kommando via nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1347">This event represents a direct I/O driver command via nx_ip_driver_direct_command.</span></span>

<span data-ttu-id="0f9f0-1348">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1348">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1349">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1349">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1350">Info-fält 2: driv Rutins kommando</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1350">Info Field 2: Driver command</span></span>
- <span data-ttu-id="0f9f0-1351">Info-fält 3: retur värde</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1351">Info Field 3: Return value</span></span>
- <span data-ttu-id="0f9f0-1352">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1352">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-disable"></a><span data-ttu-id="0f9f0-1353">Inaktivera IP-vidarebefordring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1353">IP Forwarding Disable</span></span> 

#### <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="0f9f0-1354">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1354">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="0f9f0-1355">**Ikonen** ![ I P-ikonen inaktivera](./media/user-guide/netx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1355">**Icon** ![I P forwarding disable icon](./media/user-guide/netx-events/image92.png)</span></span>

<span data-ttu-id="0f9f0-1356">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1356">**Description**</span></span>

<span data-ttu-id="0f9f0-1357">Den här händelsen representerar inaktive ring av IP-vidarebefordring via nx_ip_forwarding_disable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1357">This event represents disabling IP forwarding via nx_ip_forwarding_disable.</span></span>

<span data-ttu-id="0f9f0-1358">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1358">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1359">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1359">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1360">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1360">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1361">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1361">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1362">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1362">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-enable"></a><span data-ttu-id="0f9f0-1363">Aktivera IP-vidarebefordring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1363">IP Forwarding Enable</span></span> 

#### <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="0f9f0-1364">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1364">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="0f9f0-1365">**Ikonen** ![ Aktiverings ikon för I P P-vidarebefordring](./media/user-guide/netx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1365">**Icon** ![I P forwarding enable icon](./media/user-guide/netx-events/image93.png)</span></span>

<span data-ttu-id="0f9f0-1366">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1366">**Description**</span></span>

<span data-ttu-id="0f9f0-1367">Den här händelsen representerar aktivering av IP-vidarebefordring via nx_ip_forwarding_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1367">This event represents enabling IP forwarding via nx_ip_forwarding_enable.</span></span>

<span data-ttu-id="0f9f0-1368">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1368">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1369">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1369">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1370">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1370">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1371">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1371">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1372">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1372">Info Field 4: Not used</span></span>

### <a name="ip-fragment-disable"></a><span data-ttu-id="0f9f0-1373">Inaktivera IP-fragment</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1373">IP Fragment Disable</span></span> 

#### <a name="nx_ip_fragment_disable"></a><span data-ttu-id="0f9f0-1374">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1374">nx_ip_fragment_disable</span></span>

<span data-ttu-id="0f9f0-1375">**Ikonen** ![ I P fragment, inaktivera ikon](./media/user-guide/netx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1375">**Icon** ![I P fragment disable icon](./media/user-guide/netx-events/image94.png)</span></span>

<span data-ttu-id="0f9f0-1376">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1376">**Description**</span></span>

<span data-ttu-id="0f9f0-1377">Den här händelsen representerar inaktive ring av IP-fragmentering via nx_ip_fragment_disable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1377">This event represents disabling IP fragmenting via nx_ip_fragment_disable.</span></span>

<span data-ttu-id="0f9f0-1378">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1378">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1379">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1379">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1380">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1380">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1381">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1381">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1382">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1382">Info Field 4: Not used</span></span>

### <a name="ip-fragment-enable"></a><span data-ttu-id="0f9f0-1383">Aktivera IP-fragment</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1383">IP Fragment Enable</span></span> 

#### <a name="nx_ip_fragment_enable"></a><span data-ttu-id="0f9f0-1384">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1384">nx_ip_fragment_enable</span></span>

<span data-ttu-id="0f9f0-1385">**Ikonen** ![ Ikon för att aktivera I f-fragment](./media/user-guide/netx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1385">**Icon** ![I P fragment enable icon](./media/user-guide/netx-events/image95.png)</span></span>

<span data-ttu-id="0f9f0-1386">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1386">**Description**</span></span>

<span data-ttu-id="0f9f0-1387">Den här händelsen representerar aktivering av IP-fragment via nx_ip_fragment_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1387">This event represents enabling IP fragmenting via nx_ip_fragment_enable.</span></span>

<span data-ttu-id="0f9f0-1388">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1388">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1389">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1389">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1390">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1390">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1391">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1391">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1392">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1392">Info Field 4: Not used</span></span>

### <a name="ip-gateway-address-set"></a><span data-ttu-id="0f9f0-1393">Adress uppsättning för IP-gateway</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1393">IP Gateway Address Set</span></span> 

#### <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="0f9f0-1394">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1394">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="0f9f0-1395">**Ikonen** ![ Ikonen I P Gateway-adress uppsättning](./media/user-guide/netx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1395">**Icon** ![I P gateway address set icon](./media/user-guide/netx-events/image96.png)</span></span>

<span data-ttu-id="0f9f0-1396">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1396">**Description**</span></span>

<span data-ttu-id="0f9f0-1397">Den här händelsen representerar att ange IP-adressen för gatewayen via nx_ip_gateway_address_set.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1397">This event represents setting the gateway IP address via nx_ip_gateway_address_set.</span></span>

<span data-ttu-id="0f9f0-1398">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1398">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1399">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1399">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1400">Informations fält 2: Gateway-IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1400">Info Field 2: Gateway IP address</span></span>
- <span data-ttu-id="0f9f0-1401">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1401">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1402">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1402">Info Field 4: Not used</span></span>

### <a name="ip-information-get"></a><span data-ttu-id="0f9f0-1403">Hämta IP-information</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1403">IP Information Get</span></span> 

#### <a name="nx_ip_info_get"></a><span data-ttu-id="0f9f0-1404">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1404">nx_ip_info_get</span></span>

<span data-ttu-id="0f9f0-1405">**Ikonen** ![ I P information get-ikonen](./media/user-guide/netx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1405">**Icon** ![I P information get icon](./media/user-guide/netx-events/image97.png)</span></span>

<span data-ttu-id="0f9f0-1406">**Beskrivning** Den här händelsen representerar hämtning av IP-information via nx_ip_info_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1406">**Description** This event represents getting IP information via nx_ip_info_get.</span></span>

<span data-ttu-id="0f9f0-1407">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1407">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1408">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1408">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1409">Informations fält 2: skickade IP-byte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1409">Info Field 2: IP bytes sent</span></span>
- <span data-ttu-id="0f9f0-1410">Informations fält 3: mottagna IP-byte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1410">Info Field 3: IP bytes received</span></span>
- <span data-ttu-id="0f9f0-1411">Info fält 4: ignorerade IP-paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1411">Info Field 4: IP packets dropped</span></span>

### <a name="ip-interface-attach"></a><span data-ttu-id="0f9f0-1412">Koppla IP-gränssnitt</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1412">IP Interface Attach</span></span> 

#### <a name="nx_interface_attach"></a><span data-ttu-id="0f9f0-1413">nx_interface_attach</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1413">nx_interface_attach</span></span>

<span data-ttu-id="0f9f0-1414">**Ikonen** ![ Ikonen I P iterface-koppling](./media/user-guide/netx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1414">**Icon** ![I P iterface attach icon](./media/user-guide/netx-events/image98.png)</span></span>

<span data-ttu-id="0f9f0-1415">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1415">**Description**</span></span>

<span data-ttu-id="0f9f0-1416">Den här händelsen representerar ett sekundärt nätverks gränssnitt som kopplas till IP-instansen via nx_ip_interface_attach.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1416">This event represents a secondary network interface being attached to the IP instance via nx_ip_interface_attach.</span></span>

<span data-ttu-id="0f9f0-1417">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1417">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1418">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1418">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1419">Informations fält 2: gränssnittets IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1419">Info Field 2: Interface IP Address</span></span>
- <span data-ttu-id="0f9f0-1420">Info-fält 3: index i IP-gränssnitts tabellen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1420">Info Field 3: Index into IP interface table</span></span>
- <span data-ttu-id="0f9f0-1421">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1421">Info Field 4: Not used</span></span>

### <a name="ip-interface-info-get"></a><span data-ttu-id="0f9f0-1422">Hämta information om IP-gränssnitt</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1422">IP Interface Info Get</span></span> 

#### <a name="nx_ip_interface_info_get"></a><span data-ttu-id="0f9f0-1423">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1423">nx_ip_interface_info_get</span></span>

<span data-ttu-id="0f9f0-1424">**Ikonen** ![ Hämta ikon för IP-gränssnittets information](./media/user-guide/netx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1424">**Icon** ![ IP interface info get icon](./media/user-guide/netx-events/image99.png)</span></span>

<span data-ttu-id="0f9f0-1425">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1425">**Description**</span></span>

<span data-ttu-id="0f9f0-1426">Den här händelsen representerar information som hämtats från det angivna nätverks gränssnittet via nx_ip_interface_info_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1426">This event represents information retrieved from the specified network interface via nx_ip_interface_info_get.</span></span>

<span data-ttu-id="0f9f0-1427">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1427">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1428">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1428">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1429">Informations fält 2: gränssnittets IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1429">Info Field 2: Interface IP address</span></span>
- <span data-ttu-id="0f9f0-1430">Info-fält 3: gränssnitts-MAC-MSB</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1430">Info Field 3: Interface MAC address msb</span></span>
- <span data-ttu-id="0f9f0-1431">Info-fält 4: gränssnitts-MAC-lsb</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1431">Info Field 4: Interface MAC address lsb</span></span>

### <a name="ip-raw-packet-disable"></a><span data-ttu-id="0f9f0-1432">Inaktivera IP RAW-paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1432">IP Raw Packet Disable</span></span> 

#### <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="0f9f0-1433">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1433">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="0f9f0-1434">**Ikonen** ![ Ikonen inaktivera I RAW-paket](./media/user-guide/netx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1434">**Icon** ![I P raw packet disable icon](./media/user-guide/netx-events/image100.png)</span></span>

<span data-ttu-id="0f9f0-1435">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1435">**Description**</span></span>

<span data-ttu-id="0f9f0-1436">Den här händelsen representerar inaktive ring av kommunikation mellan rå IP-paket via nx_ip_raw_packet_disable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1436">This event represents disabling raw IP packet communication via nx_ip_raw_packet_disable.</span></span>

<span data-ttu-id="0f9f0-1437">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1437">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1438">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1438">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1439">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1439">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1440">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1440">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1441">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1441">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-enable"></a><span data-ttu-id="0f9f0-1442">Aktivera IP RAW-paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1442">IP Raw Packet Enable</span></span> 

#### <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="0f9f0-1443">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1443">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="0f9f0-1444">**Ikonen** ![ Ikonen aktivera I RAW-paket](./media/user-guide/netx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1444">**Icon** ![I P raw packet enable icon](./media/user-guide/netx-events/image101.png)</span></span>

<span data-ttu-id="0f9f0-1445">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1445">**Description**</span></span>

<span data-ttu-id="0f9f0-1446">Den här händelsen representerar aktivering av rå IP-paketfiltrering via nx_ip_raw_packet_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1446">This event represents enabling raw IP packet communication via nx_ip_raw_packet_enable.</span></span>

<span data-ttu-id="0f9f0-1447">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1447">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1448">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1448">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1449">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1449">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1450">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1450">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1451">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1451">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-receive"></a><span data-ttu-id="0f9f0-1452">Ta emot IP RAW-paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1452">IP Raw Packet Receive</span></span> 

#### <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="0f9f0-1453">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1453">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="0f9f0-1454">**Ikonen** ![ Ikonen för att ta emot RAW-paket](./media/user-guide/netx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1454">**Icon** ![I P raw packet receive icon](./media/user-guide/netx-events/image102.png)</span></span>

<span data-ttu-id="0f9f0-1455">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1455">**Description**</span></span>

<span data-ttu-id="0f9f0-1456">Den här händelsen representerar att ta emot ett RAW IP-paket via nx_ip_raw_packet_receive.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1456">This event represents receiving a raw IP packet via nx_ip_raw_packet_receive.</span></span>

<span data-ttu-id="0f9f0-1457">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1457">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1458">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1458">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1459">Info fält 2: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1459">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-1460">Informations fält 3: vänte alternativ</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1460">Info Field 3: Wait option</span></span>
- <span data-ttu-id="0f9f0-1461">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1461">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-send"></a><span data-ttu-id="0f9f0-1462">Skicka IP RAW-paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1462">IP Raw Packet Send</span></span> 

#### <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="0f9f0-1463">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1463">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="0f9f0-1464">**Ikonen** ![ I P skicka ikon för RAW Packet-sändning](./media/user-guide/netx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1464">**Icon** ![I P raw packet send icon](./media/user-guide/netx-events/image103.png)</span></span>

<span data-ttu-id="0f9f0-1465">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1465">**Description**</span></span>

<span data-ttu-id="0f9f0-1466">Den här händelsen representerar sändning av ett RAW IP-paket via nx_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1466">This event represents sending a raw IP packet via nx_ip_raw_packet_send.</span></span>

<span data-ttu-id="0f9f0-1467">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1467">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1468">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1468">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1469">Info fält 2: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1469">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-1470">Informations fält 3: målets IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1470">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="0f9f0-1471">Info-fält 4: typ av tjänst</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1471">Info Field 4: Type of service</span></span>

### <a name="ip-static-route-add"></a><span data-ttu-id="0f9f0-1472">IP-statisk väg Lägg till</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1472">IP Static Route Add</span></span> 

#### <a name="nx_ip_static_route_add"></a><span data-ttu-id="0f9f0-1473">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1473">nx_ip_static_route_add</span></span>

<span data-ttu-id="0f9f0-1474">**Ikonen** ![ I P statisk väg, Lägg till ikon](./media/user-guide/netx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1474">**Icon** ![I P static route add icon](./media/user-guide/netx-events/image104.png)</span></span>

<span data-ttu-id="0f9f0-1475">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1475">**Description**</span></span>

<span data-ttu-id="0f9f0-1476">Den här händelsen representerar en statisk väg som läggs till i routningstabellen för IP-instansen via nx_ip_static_route_add.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1476">This event represents a static route being added to the IP instance routing table via nx_ip_static_route_add.</span></span>

<span data-ttu-id="0f9f0-1477">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1477">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1478">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1478">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1479">Informations fält 2: nätverks adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1479">Info Field 2: Network address</span></span>
- <span data-ttu-id="0f9f0-1480">Informations fält 3: nätverks mask</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1480">Info Field 3: Network mask</span></span>
- <span data-ttu-id="0f9f0-1481">Info-fält 4: nästa hopp</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1481">Info Field 4: Next hop</span></span>

### <a name="ip-static-route-delete"></a><span data-ttu-id="0f9f0-1482">Ta bort IP statisk väg</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1482">IP Static Route Delete</span></span> 

#### <a name="nx_ip_static_route_delete"></a><span data-ttu-id="0f9f0-1483">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1483">nx_ip_static_route_delete</span></span>

<span data-ttu-id="0f9f0-1484">**Ikonen** ![ Ta bort-ikonen I P statisk Rute](./media/user-guide/netx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1484">**Icon** ![I P static rute delete icon](./media/user-guide/netx-events/image105.png)</span></span>

<span data-ttu-id="0f9f0-1485">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1485">**Description**</span></span>

<span data-ttu-id="0f9f0-1486">Den här händelsen representerar en statisk väg som tas bort från routningstabellen för IP-instansen via nx_ip_static_route_delete.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1486">This event represents a static route being removed from the IP instance routing table via nx_ip_static_route_delete.</span></span>

<span data-ttu-id="0f9f0-1487">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1487">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1488">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1488">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1489">Informations fält 2: nätverks adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1489">Info Field 2: Network address</span></span>
- <span data-ttu-id="0f9f0-1490">Informations fält 3: nätverks mask</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1490">Info Field 3: Network mask</span></span>
- <span data-ttu-id="0f9f0-1491">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1491">Info Field 4: Not used</span></span>

### <a name="ip-status-check"></a><span data-ttu-id="0f9f0-1492">Kontroll av IP-status</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1492">IP Status Check</span></span> 

#### <a name="nx_ip_status_check"></a><span data-ttu-id="0f9f0-1493">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1493">nx_ip_status_check</span></span>

<span data-ttu-id="0f9f0-1494">**Ikonen** ![ Kontroll ikon för I P-status](./media/user-guide/netx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1494">**Icon** ![I P status check icon](./media/user-guide/netx-events/image106.png)</span></span>

<span data-ttu-id="0f9f0-1495">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1495">**Description**</span></span>

<span data-ttu-id="0f9f0-1496">Den här händelsen representerar att kontrol lera en IP-status via nx_ip_status_check.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1496">This event represents checking for an IP status via nx_ip_status_check.</span></span>

<span data-ttu-id="0f9f0-1497">Informations fält</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1497">Information Fields</span></span> 

- <span data-ttu-id="0f9f0-1498">Info fält 1: pekar mot IP-instansen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1498">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="0f9f0-1499">Informations fält 2: begärd status</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1499">Info Field 2: Requested status</span></span>
- <span data-ttu-id="0f9f0-1500">Info-fält 3: faktisk status</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1500">Info Field 3: Actual status</span></span>
- <span data-ttu-id="0f9f0-1501">Info fält 4: vänte alternativ</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1501">Info Field 4: Wait option</span></span>

### <a name="ipsec-enable"></a><span data-ttu-id="0f9f0-1502">Aktivera IPSEC</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1502">IPSEC Enable</span></span> 

#### <a name="nx_ipsec_enable"></a><span data-ttu-id="0f9f0-1503">nx_ipsec_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1503">nx_ipsec_enable</span></span>

<span data-ttu-id="0f9f0-1504">**Ikonen** ![ I P S E C Aktivera ikon](./media/user-guide/netx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1504">**Icon** ![I P S E C enable icon](./media/user-guide/netx-events/image107.png)</span></span>

<span data-ttu-id="0f9f0-1505">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1505">**Description**</span></span>

<span data-ttu-id="0f9f0-1506">Den här händelsen representerar aktivering av IPSec-tjänster på den angivna IP-instansen via nx_ipsec_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1506">This event represents enabling IPSec services on the supplied IP instance via nx_ipsec_enable.</span></span>

<span data-ttu-id="0f9f0-1507">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1507">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1508">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1508">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1509">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1509">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1510">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1510">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1511">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1511">Info Field 4: Not used</span></span>

### <a name="packet-allocate"></a><span data-ttu-id="0f9f0-1512">Paket tilldelning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1512">Packet Allocate</span></span> 

#### <a name="nx_packet_allocate"></a><span data-ttu-id="0f9f0-1513">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1513">nx_packet_allocate</span></span>

<span data-ttu-id="0f9f0-1514">**Ikonen** ![ Ikon för paket tilldelning](./media/user-guide/netx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1514">**Icon** ![Packet allocate icon](./media/user-guide/netx-events/image108.png)</span></span>

<span data-ttu-id="0f9f0-1515">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1515">**Description**</span></span>

<span data-ttu-id="0f9f0-1516">Den här händelsen representerar att allokera ett paket via nx_packet_allocate.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1516">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="0f9f0-1517">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1517">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1518">Info fält 1: pekar mot paketschemaläggaren</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1518">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="0f9f0-1519">Info fält 2: pekar på allokerat paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1519">Info Field 2: Pointer to packet allocated</span></span>
- <span data-ttu-id="0f9f0-1520">Informations fält 3: pakettyp</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1520">Info Field 3: Packet type</span></span>
- <span data-ttu-id="0f9f0-1521">Info fält 4: tillgängliga paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1521">Info Field 4: Available packets</span></span>

### <a name="packet-copy"></a><span data-ttu-id="0f9f0-1522">Paket kopia</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1522">Packet Copy</span></span> 

#### <a name="nx_packet_copy"></a><span data-ttu-id="0f9f0-1523">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1523">nx_packet_copy</span></span>

<span data-ttu-id="0f9f0-1524">**Ikonen** ![ Ikon för paket CPY](./media/user-guide/netx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1524">**Icon** ![Packet cpy icon](./media/user-guide/netx-events/image109.png)</span></span>

<span data-ttu-id="0f9f0-1525">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1525">**Description**</span></span>

<span data-ttu-id="0f9f0-1526">Den här händelsen representerar kopiering av ett paket via nx_packet_copy.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1526">This event represents copying a packet via nx_packet_copy.</span></span>

<span data-ttu-id="0f9f0-1527">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1527">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1528">Informations fält 2: ny paket pekare</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1528">Info Field 2: New packet pointer</span></span>
- <span data-ttu-id="0f9f0-1529">Informations fält 3: pekare till Packet bassäng</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1529">Info Field 3: Pointer to packet pool</span></span>
- <span data-ttu-id="0f9f0-1530">Info fält 4: vänte alternativ</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1530">Info Field 4: Wait option</span></span>

### <a name="packet-data-append"></a><span data-ttu-id="0f9f0-1531">Lägg till paket data</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1531">Packet Data Append</span></span> 

#### <a name="nx_packet_data_append"></a><span data-ttu-id="0f9f0-1532">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1532">nx_packet_data_append</span></span>

<span data-ttu-id="0f9f0-1533">**Ikonen** ![ Ikon för Lägg till paket data](./media/user-guide/netx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1533">**Icon** ![Packet data append icon](./media/user-guide/netx-events/image110.png)</span></span>

<span data-ttu-id="0f9f0-1534">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1534">**Description**</span></span>

<span data-ttu-id="0f9f0-1535">Den här händelsen representerar att lägga till data i ett paket via nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1535">This event represents appending data to a packet via nx_packet_data_append.</span></span>

<span data-ttu-id="0f9f0-1536">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1536">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1537">Info fält 1: pekar mot paketet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1537">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="0f9f0-1538">Info fält 2: pekare till data</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1538">Info Field 2: Pointer to data</span></span>
- <span data-ttu-id="0f9f0-1539">Informations fält 3: data storlek</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1539">Info Field 3: Size of data</span></span>
- <span data-ttu-id="0f9f0-1540">Info fält 4: pekar mot Packet bassäng</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1540">Info Field 4: Pointer to packet pool</span></span>

### <a name="packet-data-extract-offset"></a><span data-ttu-id="0f9f0-1541">Förskjutning av paket data extrahering</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1541">Packet Data Extract Offset</span></span> 

#### <a name="nx_udp_source_extract_offset"></a><span data-ttu-id="0f9f0-1542">nx_udp_source_extract_offset</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1542">nx_udp_source_extract_offset</span></span>

<span data-ttu-id="0f9f0-1543">**Ikonen** ![ Förskjutnings ikon för extrahering av paket data](./media/user-guide/netx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1543">**Icon** ![Packet data extract offset icon](./media/user-guide/netx-events/image111.png)</span></span>

<span data-ttu-id="0f9f0-1544">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1544">**Description**</span></span>

<span data-ttu-id="0f9f0-1545">Den här händelsen representerar paket data som extraheras till en angiven buffert från ett paket via nx_udp_source_extract_offset.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1545">This event represents packet data that is extracted into a supplied buffer from a packet via nx_udp_source_extract_offset.</span></span>

<span data-ttu-id="0f9f0-1546">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1546">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1547">Info fält 1: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1547">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-1548">Informations fält 2: storleken på den angivna bufferten</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1548">Info Field 2: Size of specified buffer</span></span>
- <span data-ttu-id="0f9f0-1549">Informations fält 3: antal kopierade byte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1549">Info Field 3: Number of bytes copied</span></span>
- <span data-ttu-id="0f9f0-1550">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1550">Info Field 4: Not used</span></span>

### <a name="packet-data-retrieve"></a><span data-ttu-id="0f9f0-1551">Hämta paket data</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1551">Packet Data Retrieve</span></span> 

#### <a name="nx_packet_data_retrieve"></a><span data-ttu-id="0f9f0-1552">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1552">nx_packet_data_retrieve</span></span>

<span data-ttu-id="0f9f0-1553">**Ikonen** ![ Hämta ikon för paket data](./media/user-guide/netx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1553">**Icon** ![Packet data retrieve icon](./media/user-guide/netx-events/image112.png)</span></span>

<span data-ttu-id="0f9f0-1554">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1554">**Description**</span></span>

<span data-ttu-id="0f9f0-1555">Den här händelsen representerar hämtning av data från ett paket via nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1555">This event represents retrieving data from a packet via nx_packet_data_retrieve.</span></span>

<span data-ttu-id="0f9f0-1556">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1556">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1557">Info fält 1: pekar mot paketet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1557">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="0f9f0-1558">Informations fält 2: pekar till början av bufferten</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1558">Info Field 2: Pointer to start of buffer</span></span>
- <span data-ttu-id="0f9f0-1559">Informations fält 3: kopierade byte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1559">Info Field 3: Bytes copied</span></span>
- <span data-ttu-id="0f9f0-1560">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1560">Info Field 4: Not used</span></span>

### <a name="packet-length-get"></a><span data-ttu-id="0f9f0-1561">Hämta paket längd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1561">Packet Length Get</span></span> 

#### <a name="nx_packet_length_get"></a><span data-ttu-id="0f9f0-1562">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1562">nx_packet_length_get</span></span>

<span data-ttu-id="0f9f0-1563">**Ikonen** ![ Hämta ikon för paket längd](./media/user-guide/netx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1563">**Icon** ![Packet length get icon](./media/user-guide/netx-events/image113.png)</span></span>

<span data-ttu-id="0f9f0-1564">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1564">**Description**</span></span>

<span data-ttu-id="0f9f0-1565">Den här händelsen representerar hämtning av längden på ett paket via nx_packet_length_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1565">This event represents getting the length of a packet via nx_packet_length_get.</span></span>

<span data-ttu-id="0f9f0-1566">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1566">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1567">Info fält 1: pekar mot paketet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1567">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="0f9f0-1568">Informations fält 2: paket längd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1568">Info Field 2: Packet length</span></span>
- <span data-ttu-id="0f9f0-1569">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1569">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1570">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1570">Info Field 4: Not used</span></span>

### <a name="packet-pool-create"></a><span data-ttu-id="0f9f0-1571">Skapa paket pool</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1571">Packet Pool Create</span></span> 

#### <a name="nx_packet_pool_create"></a><span data-ttu-id="0f9f0-1572">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1572">nx_packet_pool_create</span></span>

<span data-ttu-id="0f9f0-1573">**Ikonen** ![ Ikon för att skapa paket pool](./media/user-guide/netx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1573">**Icon** ![Packet pool create icon](./media/user-guide/netx-events/image114.png)</span></span>

<span data-ttu-id="0f9f0-1574">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1574">**Description**</span></span>

<span data-ttu-id="0f9f0-1575">Den här händelsen representerar skapandet av en adresspool via nx_packet_pool_create.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1575">This event represents creating a packet pool via nx_packet_pool_create.</span></span>

<span data-ttu-id="0f9f0-1576">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1576">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1577">Info fält 1: pekar mot paketschemaläggaren</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1577">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="0f9f0-1578">Informations fält 2: paketets nytto Last storlek</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1578">Info Field 2: Packet payload size</span></span>
- <span data-ttu-id="0f9f0-1579">Informations fält 3: pekare till pool minnes område</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1579">Info Field 3: Pointer to pool memory area</span></span>
- <span data-ttu-id="0f9f0-1580">Info fält 4: storlek på poolens minnes område</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1580">Info Field 4: Size of pool memory area</span></span>

### <a name="packet-pool-delete"></a><span data-ttu-id="0f9f0-1581">Ta bort paket pool</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1581">Packet Pool Delete</span></span> 

#### <a name="nx_packet_pool_delete"></a><span data-ttu-id="0f9f0-1582">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1582">nx_packet_pool_delete</span></span>

<span data-ttu-id="0f9f0-1583">**Ikonen** ![ Ikon för borttagning av paket pool](./media/user-guide/netx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1583">**Icon** ![Packet pool delete icon](./media/user-guide/netx-events/image115.png)</span></span>

<span data-ttu-id="0f9f0-1584">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1584">**Description**</span></span>

<span data-ttu-id="0f9f0-1585">Den här händelsen representerar borttagning av en modempool via nx_packet_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1585">This event represents deleting a packet pool via nx_packet_pool_delete.</span></span>

<span data-ttu-id="0f9f0-1586">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1586">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1587">Info fält 1: pekar mot paketschemaläggaren</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1587">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="0f9f0-1588">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1588">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1589">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1589">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1590">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1590">Info Field 4: Not used</span></span>

#### <a name="packet-pool-information-get"></a><span data-ttu-id="0f9f0-1591">Hämta paket bassängs information</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1591">Packet Pool Information Get</span></span> 

#### <a name="nx_packet_pool_info_get"></a><span data-ttu-id="0f9f0-1592">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1592">nx_packet_pool_info_get</span></span>

<span data-ttu-id="0f9f0-1593">**Ikonen** ![ Hämta ikon för paket Pools information](./media/user-guide/netx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1593">**Icon** ![Packet pool information get icon](./media/user-guide/netx-events/image116.png)</span></span>

<span data-ttu-id="0f9f0-1594">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1594">**Description**</span></span>

<span data-ttu-id="0f9f0-1595">Den här händelsen representerar hämtning av paketets pool med information via nx_packet_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1595">This event represents getting packet pool information via nx_packet_pool_info_get.</span></span>

<span data-ttu-id="0f9f0-1596">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1596">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1597">Info fält 1: pekare till Packet bassäng</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1597">Info Field 1: Pointer to packet pool</span></span>
- <span data-ttu-id="0f9f0-1598">Informations fält 2: totalt antal paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1598">Info Field 2: Total packets</span></span>
- <span data-ttu-id="0f9f0-1599">Informations fält 3: tillgängliga paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1599">Info Field 3: Available packets</span></span>
- <span data-ttu-id="0f9f0-1600">Info fält 4: tomma begär Anden</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1600">Info Field 4: Empty requests</span></span>

### <a name="packet-release"></a><span data-ttu-id="0f9f0-1601">Paket version</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1601">Packet Release</span></span> 

#### <a name="nx_packet_data_release"></a><span data-ttu-id="0f9f0-1602">nx_packet_data_release</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1602">nx_packet_data_release</span></span>

<span data-ttu-id="0f9f0-1603">**Ikonen** ![ Ikon för paket frigörelse](./media/user-guide/netx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1603">**Icon** ![Packet release icon](./media/user-guide/netx-events/image117.png)</span></span>

<span data-ttu-id="0f9f0-1604">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1604">**Description**</span></span>

<span data-ttu-id="0f9f0-1605">Den här händelsen representerar att släppa ett paket via nx_packet_release.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1605">This event represents releasing a packet via nx_packet_release.</span></span>

<span data-ttu-id="0f9f0-1606">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1606">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1607">Info fält 1: pekar mot paketet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1607">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="0f9f0-1608">Informations fält 2: paket status</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1608">Info Field 2: Packet status</span></span>
- <span data-ttu-id="0f9f0-1609">Informations fält 3: tillgängliga paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1609">Info Field 3: Available packets</span></span>
- <span data-ttu-id="0f9f0-1610">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1610">Info Field 4: Not used</span></span>

### <a name="packet-transmit-release"></a><span data-ttu-id="0f9f0-1611">Paket överförings version</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1611">Packet Transmit Release</span></span> 

#### <a name="nx_packet_transmit_release"></a><span data-ttu-id="0f9f0-1612">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1612">nx_packet_transmit_release</span></span>

<span data-ttu-id="0f9f0-1613">**Ikonen** ![ Ikon för paket sändnings version](./media/user-guide/netx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1613">**Icon** ![Packet transmit release icon](./media/user-guide/netx-events/image118.png)</span></span>

<span data-ttu-id="0f9f0-1614">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1614">**Description**</span></span>

<span data-ttu-id="0f9f0-1615">Den här händelsen representerar att släppa ett överförings paket via nx_packet_transmit_release.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1615">This event represents releasing a transmit packet via nx_packet_transmit_release.</span></span>

<span data-ttu-id="0f9f0-1616">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1616">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1617">Info fält 1: pekar mot paketet</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1617">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="0f9f0-1618">Informations fält 2: paket status</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1618">Info Field 2: Packet status</span></span>
- <span data-ttu-id="0f9f0-1619">Informations fält 3: tillgängliga paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1619">Info Field 3: Available packets</span></span>
- <span data-ttu-id="0f9f0-1620">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1620">Info Field 4: Not used</span></span>

### <a name="rarp-disable"></a><span data-ttu-id="0f9f0-1621">Inaktivera RARP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1621">RARP Disable</span></span> 

#### <a name="nx_rarp_disable"></a><span data-ttu-id="0f9f0-1622">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1622">nx_rarp_disable</span></span>

<span data-ttu-id="0f9f0-1623">**Ikonen** ![ R A R P inaktivera ikon](./media/user-guide/netx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1623">**Icon** ![R A R P disable icon](./media/user-guide/netx-events/image119.png)</span></span>

<span data-ttu-id="0f9f0-1624">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1624">**Description**</span></span>

<span data-ttu-id="0f9f0-1625">Den här händelsen representerar inaktive ring av RARP via nx_rarp_disable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1625">This event represents disabling RARP via nx_rarp_disable.</span></span>

<span data-ttu-id="0f9f0-1626">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1626">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1627">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1627">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1628">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1628">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1629">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1629">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1630">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1630">Info Field 4: Not used</span></span>

### <a name="rarp-enable"></a><span data-ttu-id="0f9f0-1631">Aktivera RARP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1631">RARP Enable</span></span> 

#### <a name="nx_rarp_enable"></a><span data-ttu-id="0f9f0-1632">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1632">nx_rarp_enable</span></span>

<span data-ttu-id="0f9f0-1633">**Ikonen** ![ R A R P Aktivera ikon](./media/user-guide/netx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1633">**Icon** ![R A R P enable icon](./media/user-guide/netx-events/image120.png)</span></span>

<span data-ttu-id="0f9f0-1634">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1634">**Description**</span></span>

<span data-ttu-id="0f9f0-1635">Den här händelsen representerar aktivering av RARP via nx_rarp_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1635">This event represents enabling RARP via nx_rarp_enable.</span></span>

<span data-ttu-id="0f9f0-1636">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1636">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1637">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1637">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1638">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1638">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1639">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1639">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1640">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1640">Info Field 4: Not used</span></span>

### <a name="rarp-information-get"></a><span data-ttu-id="0f9f0-1641">RARP information get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1641">RARP Information Get</span></span> 

#### <a name="nx_rarp_info_get"></a><span data-ttu-id="0f9f0-1642">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1642">nx_rarp_info_get</span></span>

<span data-ttu-id="0f9f0-1643">**Ikonen** ![ R A R P P-ikonen Hämta information](./media/user-guide/netx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1643">**Icon** ![R A R P information get icon](./media/user-guide/netx-events/image121.png)</span></span>

<span data-ttu-id="0f9f0-1644">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1644">**Description**</span></span>

<span data-ttu-id="0f9f0-1645">Den här händelsen representerar att hämta RARP-information via nx_rarp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1645">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="0f9f0-1646">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1646">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1647">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1647">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1648">Informations fält 2: begär Anden som skickats</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1648">Info Field 2: Requests sent</span></span>
- <span data-ttu-id="0f9f0-1649">Informations fält 3: svar mottagna</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1649">Info Field 3: Responses received</span></span>
- <span data-ttu-id="0f9f0-1650">Info-fält 4: ogiltiga svar</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1650">Info Field 4: Invalid responses</span></span>

### <a name="system-initialize"></a><span data-ttu-id="0f9f0-1651">System initiering</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1651">System Initialize</span></span> 

#### <a name="nx_system_initialize"></a><span data-ttu-id="0f9f0-1652">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1652">nx_system_initialize</span></span>

<span data-ttu-id="0f9f0-1653">**Ikonen** ![ Ikon för system initiering](./media/user-guide/netx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1653">**Icon** ![System initialize icon](./media/user-guide/netx-events/image122.png)</span></span>

<span data-ttu-id="0f9f0-1654">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1654">**Description**</span></span>

<span data-ttu-id="0f9f0-1655">Den här händelsen representerar initiering av NetX via nx_system_initialize.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1655">This event represents initializing NetX via nx_system_initialize.</span></span>

<span data-ttu-id="0f9f0-1656">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1656">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1657">Informations fält 1: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1657">Info Field 1: Not used</span></span>
- <span data-ttu-id="0f9f0-1658">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1658">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1659">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1659">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1660">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1660">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-bind"></a><span data-ttu-id="0f9f0-1661">TCP-klientens socket-bindning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1661">TCP Client Socket Bind</span></span> 

#### <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="0f9f0-1662">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1662">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="0f9f0-1663">**Ikonen** ![ Ikonen för T P client socket bind](./media/user-guide/netx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1663">**Icon** ![T  P client socket bind icon](./media/user-guide/netx-events/image123.png)</span></span>

<span data-ttu-id="0f9f0-1664">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1664">**Description**</span></span>

<span data-ttu-id="0f9f0-1665">Den här händelsen representerar bindning av en klient-socket till en port via nx_tcp_client_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1665">This event represents binding a client socket to a port via nx_tcp_client_socket_bind.</span></span>

<span data-ttu-id="0f9f0-1666">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1666">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1667">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1667">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1668">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1668">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1669">Informations fält 3: port begärd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1669">Info Field 3: Port requested</span></span>
- <span data-ttu-id="0f9f0-1670">Info fält 4: vänte alternativ</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1670">Info Field 4: Wait option</span></span>

### <a name="tcp-client-socket-connect"></a><span data-ttu-id="0f9f0-1671">TCP-klient-socket Connect</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1671">TCP Client Socket Connect</span></span> 

#### <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="0f9f0-1672">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1672">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="0f9f0-1673">**Ikonen** ![ T C P P Connect-ikon för klient-socket](./media/user-guide/netx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1673">**Icon** ![T C P client socket connect icon](./media/user-guide/netx-events/image124.png)</span></span>

<span data-ttu-id="0f9f0-1674">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1674">**Description**</span></span>

<span data-ttu-id="0f9f0-1675">Den här händelsen representerar att skapa en klient anslutning via nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1675">This event represents making a client socket connection via nx_tcp_client_socket_connect.</span></span>

<span data-ttu-id="0f9f0-1676">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1676">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1677">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1677">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1678">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1678">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1679">Informations fält 3: serverns IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1679">Info Field 3: Server IP address</span></span>
- <span data-ttu-id="0f9f0-1680">Info fält 4: Server porten har begärts</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1680">Info Field 4: Server port requested</span></span>

### <a name="tcp-client-socket-port-get"></a><span data-ttu-id="0f9f0-1681">Hämta TCP-klientens socket-port</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1681">TCP Client Socket Port Get</span></span> 

#### <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="0f9f0-1682">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1682">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="0f9f0-1683">**Ikonen** ![ Ikonen Hämta ikon för T C P client socket](./media/user-guide/netx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1683">**Icon** ![T C P client socket port get icon](./media/user-guide/netx-events/image125.png)</span></span>

<span data-ttu-id="0f9f0-1684">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1684">**Description**</span></span>

<span data-ttu-id="0f9f0-1685">Den här händelsen representerar klientens socket port nummer via nx_tcp_client_socket_port_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1685">This event represents getting the client socket port number via nx_tcp_client_socket_port_get.</span></span>

<span data-ttu-id="0f9f0-1686">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1686">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1687">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1687">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1688">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1688">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1689">Informations fält 3: port nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1689">Info Field 3: Port number</span></span>
- <span data-ttu-id="0f9f0-1690">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1690">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-unbind"></a><span data-ttu-id="0f9f0-1691">TCP-klientens socket-DataBind</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1691">TCP Client Socket Unbind</span></span> 

#### <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="0f9f0-1692">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1692">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="0f9f0-1693">**Ikonen** ![ Ikon för T C P P-bindning för klient-socket](./media/user-guide/netx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1693">**Icon** ![T C P client socket unbind icon](./media/user-guide/netx-events/image126.png)</span></span>

<span data-ttu-id="0f9f0-1694">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1694">**Description**</span></span>

<span data-ttu-id="0f9f0-1695">Den här händelsen representerar en avbindning av porten som är kopplad till socketen via nx_tcp_client_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1695">This event represents unbinding the port associated with the socket via nx_tcp_client_socket_unbind.</span></span>

<span data-ttu-id="0f9f0-1696">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1696">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1697">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1697">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1698">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1698">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1699">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1699">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1700">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1700">Info Field 4: Not used</span></span>

### <a name="tcp-enable"></a><span data-ttu-id="0f9f0-1701">TCP-aktivering</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1701">TCP Enable</span></span> 

#### <a name="nx_tcp_enable"></a><span data-ttu-id="0f9f0-1702">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1702">nx_tcp_enable</span></span>

<span data-ttu-id="0f9f0-1703">**Ikonen** ![ Ikonen T C P Enable](./media/user-guide/netx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1703">**Icon** ![T C P enable icon](./media/user-guide/netx-events/image127.png)</span></span>

<span data-ttu-id="0f9f0-1704">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1704">**Description**</span></span>

<span data-ttu-id="0f9f0-1705">Den här händelsen representerar aktivering av TCP via nx_tcp_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1705">This event represents enabling TCP via nx_tcp_enable.</span></span>

<span data-ttu-id="0f9f0-1706">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1706">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1707">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1707">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1708">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1708">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1709">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1709">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1710">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1710">Info Field 4: Not used</span></span>

###  <a name="tcp-free-port-find-tcp-free-port-find"></a><span data-ttu-id="0f9f0-1711">Kostnads fri TCP-port hitta gratis TCP-port hitta</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1711">TCP Free Port Find TCP Free Port Find</span></span> 

#### <a name="nx_tcp_free_port_find"></a><span data-ttu-id="0f9f0-1712">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1712">nx_tcp_free_port_find</span></span>

<span data-ttu-id="0f9f0-1713">**Ikonen** ![ T CP-kostnads fri port hitta ikon](./media/user-guide/netx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1713">**Icon** ![T  CP free port find icon](./media/user-guide/netx-events/image128.png)</span></span>

<span data-ttu-id="0f9f0-1714">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1714">**Description**</span></span>

<span data-ttu-id="0f9f0-1715">Den här händelsen motsvarar att hitta en kostnads fri TCP-port via nx_tcp_free_port_find.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1715">This event represents finding a free TCP port via nx_tcp_free_port_find.</span></span>

<span data-ttu-id="0f9f0-1716">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1716">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1717">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1717">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1718">Informations fält 2: startar Sök port nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1718">Info Field 2: Starting search port number</span></span>
- <span data-ttu-id="0f9f0-1719">Info-fält 3: ledigt port nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1719">Info Field 3: Free port number</span></span>
- <span data-ttu-id="0f9f0-1720">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1720">Info Field 4: Not used</span></span>

###  <a name="tcp-infomation-get"></a><span data-ttu-id="0f9f0-1721">Hämta TCP-information</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1721">TCP Infomation Get</span></span> 

#### <a name="nx_tcp_info_get"></a><span data-ttu-id="0f9f0-1722">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1722">nx_tcp_info_get</span></span>

<span data-ttu-id="0f9f0-1723">**Ikonen** ![ T C P information get-ikon](./media/user-guide/netx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1723">**Icon** ![T C P infomation get icon](./media/user-guide/netx-events/image129.png)</span></span>

<span data-ttu-id="0f9f0-1724">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1724">**Description**</span></span>

<span data-ttu-id="0f9f0-1725">Den här händelsen representerar hämtning av TCP-information för den angivna IP-instansen via nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1725">This event represents retrieving TCP information for the specified IP instance via nx_tcp_info_get.</span></span>

<span data-ttu-id="0f9f0-1726">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1726">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1727">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1727">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1728">Informations fält 2: antal byte som skickats</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1728">Info Field 2: Number of bytes sent</span></span>
- <span data-ttu-id="0f9f0-1729">Informations fält 3: Antal mottagna byte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1729">Info Field 3: Number of bytes received</span></span>
- <span data-ttu-id="0f9f0-1730">Info fält 4: antal ogiltiga paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1730">Info Field 4: Number of invalid packets</span></span>

###  <a name="tcp-server-socket-accept"></a><span data-ttu-id="0f9f0-1731">Acceptera TCP-serverns socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1731">TCP Server Socket Accept</span></span> 

#### <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="0f9f0-1732">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1732">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="0f9f0-1733">**Ikonen** ![ Ikonen för T C P P-mottagning för Server uttag](./media/user-guide/netx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1733">**Icon** ![T C P server socket accept icon](./media/user-guide/netx-events/image130.png)</span></span>

<span data-ttu-id="0f9f0-1734">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1734">**Description**</span></span>

<span data-ttu-id="0f9f0-1735">Den här händelsen representerar konfigurationen av Server-socketen efter en aktiv anslutningsbegäran togs emot via nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1735">This event represents setting up the server socket after an active connection request was received via nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="0f9f0-1736">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1736">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1737">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1737">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1738">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1738">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1739">Informations fält 3: vänte alternativ</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1739">Info Field 3: Wait option</span></span>
- <span data-ttu-id="0f9f0-1740">Info-fält 4: socket State</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1740">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-listen"></a><span data-ttu-id="0f9f0-1741">TCP server-socket Lyssna</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1741">TCP Server Socket Listen</span></span> 

#### <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="0f9f0-1742">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1742">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="0f9f0-1743">**Ikonen** ![ T C P P lsten ikon för en server-socket](./media/user-guide/netx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1743">**Icon** ![T C P server socket lsten icon](./media/user-guide/netx-events/image131.png)</span></span>

<span data-ttu-id="0f9f0-1744">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1744">**Description**</span></span>

<span data-ttu-id="0f9f0-1745">Den här händelsen representerar registrering av en lyssnande begäran och en server-socket för den angivna TCP-porten via nx_tcp_server_socket_listen.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1745">This event represents register a listen request and a server socket for the specified TCP port via nx_tcp_server_socket_listen.</span></span>

<span data-ttu-id="0f9f0-1746">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1746">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1747">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1747">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1748">Informations fält 2: TCP-portnummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1748">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="0f9f0-1749">Informations fält 3: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1749">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1750">Informations fält 4: maximalt antal anslutningar som kan placeras i kö</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1750">Info Field 4: Maximum number of connections that can be queued</span></span>

###  <a name="tcp-server-socket-relisten"></a><span data-ttu-id="0f9f0-1751">TCP server socket relister</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1751">TCP Server Socket Relisten</span></span> 

#### <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="0f9f0-1752">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1752">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="0f9f0-1753">**Ikonen** ![ Ikon för T C P P relister för Server uttag](./media/user-guide/netx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1753">**Icon** ![T C P server socket relisten icon](./media/user-guide/netx-events/image132.png)</span></span>

<span data-ttu-id="0f9f0-1754">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1754">**Description**</span></span>

<span data-ttu-id="0f9f0-1755">Den här händelsen representerar att registrera en annan server-socket för en befintlig lyssnande begäran på den angivna TCP-porten via nx_tcp_server_socket_relisten.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1755">This event represents register another server socket for an existing listen request on the specified TCP port via nx_tcp_server_socket_relisten.</span></span>

<span data-ttu-id="0f9f0-1756">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1756">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1757">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1757">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1758">Informations fält 2: TCP-portnummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1758">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="0f9f0-1759">Informations fält 3: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1759">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1760">Info-fält 4: socket State</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1760">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-unaccept"></a><span data-ttu-id="0f9f0-1761">TCP-serverns socket accepteras inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1761">TCP Server Socket Unaccept</span></span> 

#### <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="0f9f0-1762">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1762">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="0f9f0-1763">**Ikonen** ![ Ikon för att ta emot en ikon för T C P-nätuttag](./media/user-guide/netx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1763">**Icon** ![T C P server socket unaccept icon](./media/user-guide/netx-events/image133.png)</span></span>

<span data-ttu-id="0f9f0-1764">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1764">**Description**</span></span>

<span data-ttu-id="0f9f0-1765">Den här händelsen representerar borttagning av Server-socketen från associationen med porten som tar emot en tidigare passiv anslutning via nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1765">This event represents removing the server socket from association with the port receiving an earlier passive connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="0f9f0-1766">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1766">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1767">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1767">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1768">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1768">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1769">Informations fält 3: socket State</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1769">Info Field 3: Socket state</span></span>
- <span data-ttu-id="0f9f0-1770">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1770">Info Field 4: Not used</span></span>

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a><span data-ttu-id="0f9f0-1771">TCP-server-socket avlistat TCP-serverns socket avlistar</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1771">TCP Server Socket Unlisten TCP Server Socket Unlisten</span></span> 

#### <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="0f9f0-1772">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1772">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="0f9f0-1773">**Ikonen** ![ Ikon för T C P P-avregistrering av Server-socket](./media/user-guide/netx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1773">**Icon** ![T C P server socket unlisten icon](./media/user-guide/netx-events/image134.png)</span></span>

<span data-ttu-id="0f9f0-1774">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1774">**Description**</span></span>

<span data-ttu-id="0f9f0-1775">Den här händelsen representerar borttagning av en tidigare lyssnar-begäran för den angivna TCP-porten via nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1775">This event represents removing a previous listen request for the specified TCP port via nx_tcp_server_socket_unlisten.</span></span>

<span data-ttu-id="0f9f0-1776">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1776">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1777">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1777">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1778">Informations fält 2: TCP-portnummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1778">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="0f9f0-1779">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1779">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1780">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1780">Info Field 4: Not used</span></span>

### <a name="tcp-socket-bytes-available"></a><span data-ttu-id="0f9f0-1781">Tillgängliga TCP-socket-byte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1781">TCP Socket Bytes Available</span></span> 

#### <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="0f9f0-1782">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1782">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="0f9f0-1783">**Ikonen** ![ Ikon för T C P-socket-tillgängliga byte](./media/user-guide/netx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1783">**Icon** ![T C P socket bytes available icon](./media/user-guide/netx-events/image135.png)</span></span>

<span data-ttu-id="0f9f0-1784">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1784">**Description**</span></span>

<span data-ttu-id="0f9f0-1785">Den här händelsen representerar antalet byte som för närvarande är tillgängliga på den angivna TCP-mottagande socketen via nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1785">This event represents the number of bytes currently available on the specified TCP receiving socket via nx_tcp_socket_bytes_available.</span></span>

<span data-ttu-id="0f9f0-1786">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1786">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1787">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1787">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1788">Informations fält 2: pekare till TCP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1788">Info Field 2: Pointer to TCP socket</span></span>
- <span data-ttu-id="0f9f0-1789">Informations fält 3: byte mottagna på socketen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1789">Info Field 3: Bytes received on the socket</span></span>
- <span data-ttu-id="0f9f0-1790">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1790">Info Field 4: Not used</span></span>

### <a name="tcp-socket-create"></a><span data-ttu-id="0f9f0-1791">Skapa TCP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1791">TCP Socket Create</span></span> 

#### <a name="nx_tcp_socket_create"></a><span data-ttu-id="0f9f0-1792">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1792">nx_tcp_socket_create</span></span>

<span data-ttu-id="0f9f0-1793">**Ikonen** ![ T C P uttag ikon för skapa](./media/user-guide/netx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1793">**Icon** ![T C P socket create icon](./media/user-guide/netx-events/image136.png)</span></span>

<span data-ttu-id="0f9f0-1794">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1794">**Description**</span></span>

<span data-ttu-id="0f9f0-1795">Den här händelsen representerar att skapa en TCP-socket via nx_tcp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1795">This event represents creating a TCP socket via nx_tcp_socket_create.</span></span>

<span data-ttu-id="0f9f0-1796">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1796">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1797">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1797">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1798">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1798">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1799">Informations fält 3: typ av tjänst</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1799">Info Field 3: Type of service</span></span>
- <span data-ttu-id="0f9f0-1800">Info fält 4: mottagnings fönster storlek</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1800">Info Field 4: Receive window size</span></span>

### <a name="tcp-socket-delete"></a><span data-ttu-id="0f9f0-1801">Ta bort TCP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1801">TCP Socket Delete</span></span> 

#### <a name="nx_tcp_socket_delete"></a><span data-ttu-id="0f9f0-1802">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1802">nx_tcp_socket_delete</span></span>

<span data-ttu-id="0f9f0-1803">**Ikonen** ![ Ta bort ikon för T C P socket](./media/user-guide/netx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1803">**Icon** ![T C P socket delete icon](./media/user-guide/netx-events/image137.png)</span></span>

<span data-ttu-id="0f9f0-1804">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1804">**Description**</span></span>

<span data-ttu-id="0f9f0-1805">Den här händelsen representerar borttagning av en socket via nx_tcp_socket_delete.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1805">This event represents deleting a socket via nx_tcp_socket_delete.</span></span>

<span data-ttu-id="0f9f0-1806">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1806">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1807">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1807">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1808">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1808">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1809">Informations fält 3: socket State</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1809">Info Field 3: Socket state</span></span>
- <span data-ttu-id="0f9f0-1810">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1810">Info Field 4: Not used</span></span>

### <a name="tcp-socket-disconnect"></a><span data-ttu-id="0f9f0-1811">Koppla från TCP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1811">TCP Socket Disconnect</span></span> 

#### <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="0f9f0-1812">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1812">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="0f9f0-1813">**Ikonen** ![ Ikon för T C P uttag från koppling](./media/user-guide/netx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1813">**Icon** ![T C P socket disconnect icon](./media/user-guide/netx-events/image138.png)</span></span>

<span data-ttu-id="0f9f0-1814">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1814">**Description**</span></span>

<span data-ttu-id="0f9f0-1815">Den här händelsen representerar att koppla från en socket via nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1815">This event represents disconnecting a socket via nx_tcp_socket_disconnect.</span></span>

<span data-ttu-id="0f9f0-1816">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1816">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1817">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1817">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1818">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1818">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1819">Informations fält 3: vänte alternativ</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1819">Info Field 3: Wait option</span></span>
- <span data-ttu-id="0f9f0-1820">Info-fält 4: socket State</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1820">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-information-get"></a><span data-ttu-id="0f9f0-1821">Hämta TCP socket-information</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1821">TCP Socket Information Get</span></span> 

#### <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="0f9f0-1822">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1822">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="0f9f0-1823">**Ikonen** ![ T C P socket information get-ikon](./media/user-guide/netx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1823">**Icon** ![T C P socket information get icon](./media/user-guide/netx-events/image139.png)</span></span>

<span data-ttu-id="0f9f0-1824">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1824">**Description**</span></span>

<span data-ttu-id="0f9f0-1825">Den här händelsen representerar hämtning av information om en socket via nx_tcp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1825">This event represents getting information about a socket via nx_tcp_socket_info_get.</span></span>

<span data-ttu-id="0f9f0-1826">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1826">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1827">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1827">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1828">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1828">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1829">Informations fält 3: byte skickade via denna socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1829">Info Field 3: Bytes sent through this socket</span></span>
- <span data-ttu-id="0f9f0-1830">Info fält 4: byte mottagna via denna socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1830">Info Field 4: Bytes received through this socket</span></span>

### <a name="tcp-socket-mss-get"></a><span data-ttu-id="0f9f0-1831">TCP-socket-MSS Hämta</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1831">TCP Socket MSS Get</span></span> 

#### <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="0f9f0-1832">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1832">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="0f9f0-1833">**Ikonen** ![ T C P Socket M S S get-ikon](./media/user-guide/netx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1833">**Icon** ![T C P socket M S S get icon](./media/user-guide/netx-events/image140.png)</span></span>

<span data-ttu-id="0f9f0-1834">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1834">**Description**</span></span>

<span data-ttu-id="0f9f0-1835">Den här händelsen representerar socketens MSS via nx_tcp_socket_mss_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1835">This event represents getting the socket's MSS via nx_tcp_socket_mss_get.</span></span>

<span data-ttu-id="0f9f0-1836">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1836">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1837">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1837">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1838">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1838">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1839">Informations fält 3: maximal segment storlek (MSS)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1839">Info Field 3: Maximum Segment Size (MSS)</span></span>
- <span data-ttu-id="0f9f0-1840">Info-fält 4: socket State</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1840">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-peer-get"></a><span data-ttu-id="0f9f0-1841">TCP-socket MSS peer get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1841">TCP Socket MSS Peer Get</span></span> 

#### <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="0f9f0-1842">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1842">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="0f9f0-1843">**Ikonen** ![ T C P Socket M S S peer get-ikon](./media/user-guide/netx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1843">**Icon** ![T C P socket M S S peer get icon](./media/user-guide/netx-events/image141.png)</span></span>

<span data-ttu-id="0f9f0-1844">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1844">**Description**</span></span>

<span data-ttu-id="0f9f0-1845">Den här händelsen representerar MSS-värdet för socketens peer via nx_tcp_socket_mss_peer_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1845">This event represents getting the MSS value of the socket's peer via nx_tcp_socket_mss_peer_get.</span></span>

<span data-ttu-id="0f9f0-1846">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1846">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1847">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1847">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1848">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1848">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1849">Info-fält 3: peer-MSS</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1849">Info Field 3: Peer's MSS</span></span>
- <span data-ttu-id="0f9f0-1850">Info-fält 4: socket State</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1850">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-set"></a><span data-ttu-id="0f9f0-1851">TCP-socket MSS-uppsättning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1851">TCP Socket MSS Set</span></span> 

#### <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="0f9f0-1852">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1852">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="0f9f0-1853">**Ikonen** ![ Ikon för T C P Socket M S S set](./media/user-guide/netx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1853">**Icon** ![T C P socket M S S set icon](./media/user-guide/netx-events/image142.png)</span></span>

<span data-ttu-id="0f9f0-1854">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1854">**Description**</span></span>

<span data-ttu-id="0f9f0-1855">Den här händelsen representerar att ange en Sockets MSS via nx_tcp_socket_mss_set.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1855">This event represents setting a socket's MSS via nx_tcp_socket_mss_set.</span></span>

<span data-ttu-id="0f9f0-1856">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1856">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1857">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1857">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1858">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1858">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1859">Info-fält 3: MSS</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1859">Info Field 3: MSS</span></span>
- <span data-ttu-id="0f9f0-1860">Info-fält 4: socket State</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1860">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-peer-info-get"></a><span data-ttu-id="0f9f0-1861">Hämta peer-information för TCP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1861">TCP Socket Peer Info Get</span></span> 

#### <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="0f9f0-1862">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1862">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="0f9f0-1863">**Ikonen** ![ Hämta ikon för T C P socket peer info](./media/user-guide/netx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1863">**Icon** ![T C P socket peer info get icon](./media/user-guide/netx-events/image143.png)</span></span>

<span data-ttu-id="0f9f0-1864">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1864">**Description**</span></span>

<span data-ttu-id="0f9f0-1865">Den här händelsen representerar information som hämtats från TCP-socketen om peer-datorn (t. ex. >ansluter värd) IP-adress och port via nx_tcp_socket_peer_info_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1865">This event represents information retrieved from the TCP socket regarding the peer (e.g. >connecting host) IP address and port via nx_tcp_socket_peer_info_get.</span></span>

<span data-ttu-id="0f9f0-1866">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1866">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1867">Informations fält 1: pekare till TCP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1867">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="0f9f0-1868">Informations fält 2: peer-IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1868">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="0f9f0-1869">Informations fält 3: peer port nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1869">Info Field 3: Peer port number</span></span>
- <span data-ttu-id="0f9f0-1870">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1870">Info Field 4: Not used</span></span>

### <a name="tcp-socket-receive"></a><span data-ttu-id="0f9f0-1871">Ta emot TCP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1871">TCP Socket Receive</span></span> 

#### <a name="nx_tcp_socket_receive"></a><span data-ttu-id="0f9f0-1872">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1872">nx_tcp_socket_receive</span></span>

<span data-ttu-id="0f9f0-1873">**Ikonen** ![ Ikon för T C P socket Receive](./media/user-guide/netx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1873">**Icon** ![T C P socket receive icon](./media/user-guide/netx-events/image144.png)</span></span>

<span data-ttu-id="0f9f0-1874">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1874">**Description**</span></span>

<span data-ttu-id="0f9f0-1875">Den här händelsen representerar mottagning av data från en socket via nx_tcp_socket_receive.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1875">This event represents receiving data from a socket via nx_tcp_socket_receive.</span></span>

<span data-ttu-id="0f9f0-1876">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1876">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1877">Informations fält 1: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1877">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1878">Info fält 2: pekare till mottaget paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1878">Info Field 2: Pointer to received packet</span></span>
- <span data-ttu-id="0f9f0-1879">Informations fält 3: mottaget paket längd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1879">Info Field 3: Received packet length</span></span>
- <span data-ttu-id="0f9f0-1880">Info fält 4: mottagnings ordnings nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1880">Info Field 4: Receive sequence number</span></span>

### <a name="tcp-socket-receive-notify"></a><span data-ttu-id="0f9f0-1881">Mottagnings meddelande för TCP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1881">TCP Socket Receive Notify</span></span> 

#### <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="0f9f0-1882">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1882">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="0f9f0-1883">**Ikonen** ![ Ikonen för T C P socket Receive-avisering](./media/user-guide/netx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1883">**Icon** ![T C P socket receive notify icon](./media/user-guide/netx-events/image145.png)</span></span>

<span data-ttu-id="0f9f0-1884">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1884">**Description**</span></span>

<span data-ttu-id="0f9f0-1885">Den här händelsen representerar registrering av ett mottagnings återanrop för en socket via nx_tcp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1885">This event represents registering a receive notify callback for a socket via nx_tcp_socket_receive_notify.</span></span>

<span data-ttu-id="0f9f0-1886">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1886">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1887">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1887">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1888">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1888">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1889">Informations fält 3: pekare för att ta emot meddelande om återanrops information 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1889">Info Field 3: Pointer to receive notify callback Info Field 4: Not used</span></span>

### <a name="tcp-socket-send"></a><span data-ttu-id="0f9f0-1890">Skicka TCP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1890">TCP Socket Send</span></span> 

#### <a name="nx_tcp_socket_send"></a><span data-ttu-id="0f9f0-1891">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1891">nx_tcp_socket_send</span></span>

<span data-ttu-id="0f9f0-1892">**Ikonen** ![ T C P socket-sändning, ikon](./media/user-guide/netx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1892">**Icon** ![T C P socket send icon](./media/user-guide/netx-events/image146.png)</span></span>

<span data-ttu-id="0f9f0-1893">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1893">**Description**</span></span>

<span data-ttu-id="0f9f0-1894">Den här händelsen representerar sändning av data på en socket via nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1894">This event represents sending data on a socket via nx_tcp_socket_send.</span></span>

<span data-ttu-id="0f9f0-1895">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1895">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1896">Informations fält 1: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1896">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1897">Info fält 2: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1897">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-1898">Informations fält 3: Paketets längd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1898">Info Field 3: Length of packet</span></span>
- <span data-ttu-id="0f9f0-1899">Info-fält 4: överförings ordnings nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1899">Info Field 4: Transmit sequence number</span></span>

### <a name="tcp-socket-state-wait"></a><span data-ttu-id="0f9f0-1900">Vänte läge för TCP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1900">TCP Socket State Wait</span></span> 

#### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="0f9f0-1901">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1901">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="0f9f0-1902">**Ikonen** ![ Vänta-ikon för T C P-insocket-tillstånd](./media/user-guide/netx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1902">**Icon** ![T C P socket state wait icon](./media/user-guide/netx-events/image147.png)</span></span>

<span data-ttu-id="0f9f0-1903">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1903">**Description**</span></span>

<span data-ttu-id="0f9f0-1904">Den här händelsen representerar väntan på att en socket ska ange ett visst tillstånd via nx_tcp_socket_state_wait.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1904">This event represents waiting for a socket to enter a particular state via nx_tcp_socket_state_wait.</span></span>

<span data-ttu-id="0f9f0-1905">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1905">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1906">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1906">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1907">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1907">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1908">Info-fält 3: önskat socket-tillstånd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1908">Info Field 3: Desired socket state</span></span>
- <span data-ttu-id="0f9f0-1909">Info-fält 4: tidigare socket-tillstånd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1909">Info Field 4: Previous socket state</span></span>

### <a name="tcp-socket-transmit-configure"></a><span data-ttu-id="0f9f0-1910">Konfigurera TCP socket-överföring</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1910">TCP Socket Transmit Configure</span></span> 

#### <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="0f9f0-1911">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1911">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="0f9f0-1912">**Ikonen** ![ Konfigurations ikon för T C P socket-överföring](./media/user-guide/netx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1912">**Icon** ![T C P socket transmit configure icon](./media/user-guide/netx-events/image148.png)</span></span>

<span data-ttu-id="0f9f0-1913">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1913">**Description**</span></span>

<span data-ttu-id="0f9f0-1914">Den här händelsen representerar konfigurering av överförings alternativ för en socket via nx_tcp_socket_transmit_configure.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1914">This event represents configuring the transmit options for a socket via nx_tcp_socket_transmit_configure.</span></span>

<span data-ttu-id="0f9f0-1915">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1915">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1916">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1916">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1917">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1917">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1918">Informations fält 3: överförings köns djup</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1918">Info Field 3: Transmit queue depth</span></span>
- <span data-ttu-id="0f9f0-1919">Info-fält 4: tids gräns värde</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1919">Info Field 4: Timeout value</span></span>

### <a name="tcp-socket-window-update-notify-set"></a><span data-ttu-id="0f9f0-1920">Meddelande uppsättning för uppdatering av TCP-socket-fönstret</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1920">TCP Socket Window Update Notify Set</span></span> 

#### <a name="nx_tcp_window_update_notify_set"></a><span data-ttu-id="0f9f0-1921">nx_tcp_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1921">nx_tcp_window_update_notify_set</span></span>

<span data-ttu-id="0f9f0-1922">**Ikonen** ![ Ikon för att uppdatera aviserings uppsättning i T C P socket Window](./media/user-guide/netx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1922">**Icon** ![T C P socket window update notify set icon](./media/user-guide/netx-events/image149.png)</span></span>

<span data-ttu-id="0f9f0-1923">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1923">**Description**</span></span>

<span data-ttu-id="0f9f0-1924">Den här händelsen representerar en TCP-socket som tar emot meddelanden om en ökning i fönstret för att ta emot fjärrvärdar via nx_tcp_window_update_notify_set.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1924">This event represents a TCP socket receiving notification of an increase in the remote host receive window via nx_tcp_window_update_notify_set.</span></span>

<span data-ttu-id="0f9f0-1925">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1925">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1926">Informations fält 1: pekare till TCP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1926">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="0f9f0-1927">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1927">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1928">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1928">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1929">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1929">Info Field 4: Not used</span></span>

### <a name="udp-enable"></a><span data-ttu-id="0f9f0-1930">Aktivera UDP</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1930">UDP Enable</span></span> 

#### <a name="nx_udp_enable"></a><span data-ttu-id="0f9f0-1931">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1931">nx_udp_enable</span></span>

<span data-ttu-id="0f9f0-1932">**Ikonen** ![ U D P Enable-ikon](./media/user-guide/netx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1932">**Icon** ![U D P enable icon](./media/user-guide/netx-events/image150.png)</span></span>

<span data-ttu-id="0f9f0-1933">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1933">**Description**</span></span>

<span data-ttu-id="0f9f0-1934">Den här händelsen representerar aktivering av UDP via nx_udp_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1934">This event represents enabling UDP via nx_udp_enable.</span></span>

<span data-ttu-id="0f9f0-1935">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1935">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1936">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1936">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1937">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1937">Info Field 2: Not used</span></span>
- <span data-ttu-id="0f9f0-1938">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1938">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1939">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1939">Info Field 4: Not used</span></span>

### <a name="udp-free-port-find"></a><span data-ttu-id="0f9f0-1940">Kostnads fri UDP-port hitta</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1940">UDP Free Port Find</span></span> 

#### <a name="nx_udp_free_port_find"></a><span data-ttu-id="0f9f0-1941">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1941">nx_udp_free_port_find</span></span>

<span data-ttu-id="0f9f0-1942">**Ikonen** ![ U D P kostnads fri port hitta ikon](./media/user-guide/netx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1942">**Icon** ![U D P free port find icon](./media/user-guide/netx-events/image151.png)</span></span>

<span data-ttu-id="0f9f0-1943">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1943">**Description**</span></span>

<span data-ttu-id="0f9f0-1944">Den här händelsen motsvarar att hitta en kostnads fri UDP-port via nx_udp_free_port_find.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1944">This event represents finding a free UDP port via nx_udp_free_port_find.</span></span>

<span data-ttu-id="0f9f0-1945">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1945">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1946">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1946">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1947">Informations fält 2: startar porten för sökning från</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1947">Info Field 2: Starting port to search from</span></span>
- <span data-ttu-id="0f9f0-1948">Info-fält 3: ledig port</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1948">Info Field 3: Free port</span></span>
- <span data-ttu-id="0f9f0-1949">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1949">Info Field 4: Not used</span></span>

### <a name="udp-information-get"></a><span data-ttu-id="0f9f0-1950">Hämta UDP-information</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1950">UDP Information Get</span></span> 

#### <a name="nx_udp_info_get"></a><span data-ttu-id="0f9f0-1951">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1951">nx_udp_info_get</span></span>

<span data-ttu-id="0f9f0-1952">**Ikonen** ![ U D P information get-ikon](./media/user-guide/netx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1952">**Icon** ![U D P information get icon](./media/user-guide/netx-events/image152.png)</span></span>

<span data-ttu-id="0f9f0-1953">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1953">**Description**</span></span>

<span data-ttu-id="0f9f0-1954">Den här händelsen representerar att hämta information via nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1954">This event represents getting information via nx_udp_info_get.</span></span>

<span data-ttu-id="0f9f0-1955">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1955">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1956">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1956">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1957">Informations fält 2: skickade UDP-byte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1957">Info Field 2: UDP bytes sent</span></span>
- <span data-ttu-id="0f9f0-1958">Informations fält 3: mottagna UDP-byte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1958">Info Field 3: UDP bytes received</span></span>
- <span data-ttu-id="0f9f0-1959">Info-fält 4: ogiltiga paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1959">Info Field 4: Invalid packets</span></span>

### <a name="udp-socket-bind"></a><span data-ttu-id="0f9f0-1960">UDP-socket-bindning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1960">UDP Socket Bind</span></span> 

#### <a name="nx_udp_socket_bind"></a><span data-ttu-id="0f9f0-1961">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1961">nx_udp_socket_bind</span></span>

<span data-ttu-id="0f9f0-1962">**Ikonen** ![ U D P v socket bind-ikon](./media/user-guide/netx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1962">**Icon** ![U D P socket bind icon](./media/user-guide/netx-events/image153.png)</span></span>

<span data-ttu-id="0f9f0-1963">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1963">**Description**</span></span>

<span data-ttu-id="0f9f0-1964">Den här händelsen representerar bindning av en UDP-socket till en port via nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1964">This event represents binding a UDP socket to a port via nx_udp_socket_bind.</span></span>

<span data-ttu-id="0f9f0-1965">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1965">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1966">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1966">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1967">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1967">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1968">Informations fält 3: port nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1968">Info Field 3: Port number</span></span>
- <span data-ttu-id="0f9f0-1969">Info fält 4: vänte alternativ</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1969">Info Field 4: Wait option</span></span>

### <a name="udp-socket-bytes-available"></a><span data-ttu-id="0f9f0-1970">Tillgängliga UDP-socket-byte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1970">UDP Socket Bytes Available</span></span> 

#### <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="0f9f0-1971">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1971">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="0f9f0-1972">**Ikonen** ![ Ikon för U D P socket-tillgängliga byte](./media/user-guide/netx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1972">**Icon** ![U D P socket bytes available icon](./media/user-guide/netx-events/image154.png)</span></span>

<span data-ttu-id="0f9f0-1973">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1973">**Description**</span></span>

<span data-ttu-id="0f9f0-1974">Den här händelsen representerar det aktuella antalet byte som tagits emot på UDP-socketen via nx_udp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1974">This event represents the current number of bytes received on the UDP socket via nx_udp_socket_bytes_available.</span></span>

<span data-ttu-id="0f9f0-1975">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1975">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1976">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1976">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1977">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1977">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1978">Informations fält 3: byte mottagna på socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1978">Info Field 3: Bytes received on socket</span></span>
- <span data-ttu-id="0f9f0-1979">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1979">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-disable"></a><span data-ttu-id="0f9f0-1980">Inaktivera kontroll summa för UDP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1980">UDP Socket Checksum Disable</span></span> 

#### <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="0f9f0-1981">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1981">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="0f9f0-1982">**Ikonen** ![ Inaktivera ikon för U D P socket-kontrollsumma](./media/user-guide/netx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1982">**Icon** ![U D P socket checksum disable icon](./media/user-guide/netx-events/image155.png)</span></span>

<span data-ttu-id="0f9f0-1983">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1983">**Description**</span></span>

<span data-ttu-id="0f9f0-1984">Den här händelsen representerar inaktive ring av kontroll summan för data på en UDP-socket via nx_udp_socket_checksum_disable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1984">This event represents disabling the checksum for data on a UDP socket via nx_udp_socket_checksum_disable.</span></span>

<span data-ttu-id="0f9f0-1985">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1985">**Information Fields**</span></span> 

- <span data-ttu-id="0f9f0-1986">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1986">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1987">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1987">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1988">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1988">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1989">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1989">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-enable"></a><span data-ttu-id="0f9f0-1990">Aktivera kontroll summa för UDP-uttag</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1990">UDP Socket Checksum Enable</span></span> 

#### <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="0f9f0-1991">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1991">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="0f9f0-1992">**Ikonen** ![ Ikon för U D P-uttag för kontroll Summa](./media/user-guide/netx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1992">**Icon** ![U D P socket checksum enable icon](./media/user-guide/netx-events/image156.png)</span></span>

<span data-ttu-id="0f9f0-1993">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1993">**Description**</span></span>

<span data-ttu-id="0f9f0-1994">Den här händelsen representerar aktivering av kontroll Summa bearbetning på en socket via nx_udp_socket_checksum_enable.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1994">This event represents enabling checksum processing on a socket via nx_udp_socket_checksum_enable.</span></span>

<span data-ttu-id="0f9f0-1995">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1995">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-1996">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1996">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-1997">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1997">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-1998">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1998">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-1999">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-1999">Info Field 4: Not used</span></span>

### <a name="udp-socket-create"></a><span data-ttu-id="0f9f0-2000">Skapa UDP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2000">UDP Socket Create</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="0f9f0-2001">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2001">nx_udp_socket_create</span></span>

<span data-ttu-id="0f9f0-2002">**Ikonen** ![ U D P uttag ikon för skapa](./media/user-guide/netx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2002">**Icon** ![U D P socket create icon](./media/user-guide/netx-events/image157.png)</span></span>

<span data-ttu-id="0f9f0-2003">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2003">**Description**</span></span>

<span data-ttu-id="0f9f0-2004">Den här händelsen representerar att skapa en UDP-socket via nx_udp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2004">This event represents creating a UDP socket via nx_udp_socket_create.</span></span>

<span data-ttu-id="0f9f0-2005">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2005">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-2006">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2006">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-2007">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2007">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-2008">Informations fält 3: typ av tjänst</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2008">Info Field 3: Type of service</span></span>
- <span data-ttu-id="0f9f0-2009">Info-fält 4: Max mottagnings kön</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2009">Info Field 4: Maximum receive queue</span></span>

### <a name="udp-socket-delete-event"></a><span data-ttu-id="0f9f0-2010">Ta bort händelse för UDP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2010">UDP Socket Delete Event</span></span> 

#### <a name="nx_udp_socket_delete-event"></a><span data-ttu-id="0f9f0-2011">nx_udp_socket_delete händelse</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2011">nx_udp_socket_delete event</span></span>

<span data-ttu-id="0f9f0-2012">**Ikonen** ![ U D P socket ta bort händelse ikon](./media/user-guide/netx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2012">**Icon** ![U D P socket delete event icon](./media/user-guide/netx-events/image158.png)</span></span>

<span data-ttu-id="0f9f0-2013">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2013">**Description**</span></span>

<span data-ttu-id="0f9f0-2014">Den här händelsen representerar borttagning av en UDP-socket via nx_udp_socket_delete.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2014">This event represents deleting a UDP socket via nx_udp_socket_delete.</span></span>

<span data-ttu-id="0f9f0-2015">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2015">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-2016">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2016">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-2017">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2017">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-2018">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2018">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-2019">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2019">Info Field 4: Not used</span></span>

### <a name="udp-socket-information-get-event"></a><span data-ttu-id="0f9f0-2020">UDP socket information get-händelse</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2020">UDP Socket Information Get Event</span></span> 

#### <a name="nx_udp_socket_info_get-event"></a><span data-ttu-id="0f9f0-2021">nx_udp_socket_info_get händelse</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2021">nx_udp_socket_info_get event</span></span>

<span data-ttu-id="0f9f0-2022">**Ikonen** ![ U D P l socket information Hämta händelse ikon](./media/user-guide/netx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2022">**Icon** ![U D P socket information get event icon](./media/user-guide/netx-events/image159.png)</span></span>

<span data-ttu-id="0f9f0-2023">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2023">**Description**</span></span>

<span data-ttu-id="0f9f0-2024">Den här händelsen representerar hämtning av information om en UDP-socket via nx_udp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2024">This event represents getting information about a UDP socket via nx_udp_socket_info_get.</span></span>

<span data-ttu-id="0f9f0-2025">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2025">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-2026">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2026">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-2027">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2027">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-2028">Informations fält 3: byte som skickats via socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2028">Info Field 3: Bytes sent through socket</span></span>
- <span data-ttu-id="0f9f0-2029">Info fält 4: byte mottagna via socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2029">Info Field 4: Bytes received through socket</span></span>

### <a name="udp-socket-interface-set"></a><span data-ttu-id="0f9f0-2030">Gränssnitts uppsättning för UDP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2030">UDP Socket Interface Set</span></span> 

#### <a name="nx_udp_socket_interface_set-event"></a><span data-ttu-id="0f9f0-2031">nx_udp_socket_interface_set händelse</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2031">nx_udp_socket_interface_set event</span></span>

<span data-ttu-id="0f9f0-2032">**Ikonen** ![ Ikonen U D P socket interface set](./media/user-guide/netx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2032">**Icon** ![U D P socket interface set icon](./media/user-guide/netx-events/image160.png)</span></span>

<span data-ttu-id="0f9f0-2033">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2033">**Description**</span></span>

<span data-ttu-id="0f9f0-2034">Den här händelsen representerar inställningen utgående gränssnitt för den angivna UDP-socketen med det angivna gränssnittet via nx_udp_socket_interface_set.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2034">This event represents setting the outgoing interface of the specified UDP socket with the specified interface via nx_udp_socket_interface_set.</span></span>

<span data-ttu-id="0f9f0-2035">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2035">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-2036">Info fält 1: pekare till UDP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2036">Info Field 1: Pointer to UDP socket</span></span>
- <span data-ttu-id="0f9f0-2037">Info fält 2: index som motsvarar gränssnittet för socketen</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2037">Info Field 2: Index corresponding to the interface for the socket</span></span>
- <span data-ttu-id="0f9f0-2038">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2038">Info Field 3: Not used</span></span>
- <span data-ttu-id="0f9f0-2039">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2039">Info Field 4: Not used</span></span>

### <a name="udp-socket-port-get"></a><span data-ttu-id="0f9f0-2040">Hämta UDP-socket port</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2040">UDP Socket Port Get</span></span> 

#### <a name="nx_udp_socket_port_get"></a><span data-ttu-id="0f9f0-2041">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2041">nx_udp_socket_port_get</span></span>

<span data-ttu-id="0f9f0-2042">**Ikonen** ![ U D P socket port get-ikon](./media/user-guide/netx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2042">**Icon** ![U D P socket port get icon](./media/user-guide/netx-events/image161.png)</span></span>

<span data-ttu-id="0f9f0-2043">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2043">**Description**</span></span>

<span data-ttu-id="0f9f0-2044">Den här händelsen representerar hämtning av UDP-porten som den angivna UDP-socketen är kopplad till via nx_udp_socket_port_get.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2044">This event represents retrieving the UDP port the specified UDP socket is bound to via nx_udp_socket_port_get.</span></span>

<span data-ttu-id="0f9f0-2045">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2045">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-2046">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2046">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-2047">Info fält 2: pekare till UDP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2047">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="0f9f0-2048">Informations fält 3: port nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2048">Info Field 3: Port number</span></span>
- <span data-ttu-id="0f9f0-2049">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2049">Info Field 4: Not used</span></span>

### <a name="udp-socket-receive"></a><span data-ttu-id="0f9f0-2050">Ta emot UDP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2050">UDP Socket Receive</span></span> 

#### <a name="nx_udp_socket_receive"></a><span data-ttu-id="0f9f0-2051">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2051">nx_udp_socket_receive</span></span>

<span data-ttu-id="0f9f0-2052">**Ikonen** ![ U D P socket Receive-ikon](./media/user-guide/netx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2052">**Icon** ![U D P socket receive icon](./media/user-guide/netx-events/image162.png)</span></span>

<span data-ttu-id="0f9f0-2053">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2053">**Description**</span></span>

<span data-ttu-id="0f9f0-2054">Den här händelsen representerar mottagning av data på angiven UDP-socket via nx_udp_socket_receive.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2054">This event represents receiving data on the specified UDP socket via nx_udp_socket_receive.</span></span>

<span data-ttu-id="0f9f0-2055">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2055">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-2056">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2056">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-2057">Info fält 2: pekare till UDP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2057">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="0f9f0-2058">Informations fält 3: pekare till mottaget paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2058">Info Field 3: Pointer to received packet</span></span>
- <span data-ttu-id="0f9f0-2059">Info fält 4: mottaget paket storlek</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2059">Info Field 4: Received packet size</span></span>

### <a name="udp-socket-receive-notify"></a><span data-ttu-id="0f9f0-2060">Mottagnings meddelande för UDP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2060">UDP Socket Receive Notify</span></span> 

#### <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="0f9f0-2061">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2061">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="0f9f0-2062">**Ikonen** ![ Beskrivning av U D P socket Receive-ikonen ](./media/user-guide/netx-events/image163.png) </span><span class="sxs-lookup"><span data-stu-id="0f9f0-2062">**Icon** ![U D P socket receive notify icon](./media/user-guide/netx-events/image163.png)s **Description**</span></span>

<span data-ttu-id="0f9f0-2063">Den här händelsen representerar registrering av mottagnings återanrop via nx_udp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2063">This event represents registering a receive notify callback via nx_udp_socket_receive_notify.</span></span>

<span data-ttu-id="0f9f0-2064">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2064">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-2065">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2065">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-2066">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2066">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-2067">Informations fält 3: pekare för att ta emot meddelande funktions information fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2067">Info Field 3: Pointer to receive notify function Info Field 4: Not used</span></span>

### <a name="udp-socket-send"></a><span data-ttu-id="0f9f0-2068">Skicka UDP-socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2068">UDP Socket Send</span></span> 

#### <a name="nx_udp_socket_send"></a><span data-ttu-id="0f9f0-2069">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2069">nx_udp_socket_send</span></span>

<span data-ttu-id="0f9f0-2070">**Ikonen** ![ U D P socket-skicka-ikon](./media/user-guide/netx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2070">**Icon** ![U D P socket send icon](./media/user-guide/netx-events/image164.png)</span></span>

<span data-ttu-id="0f9f0-2071">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2071">**Description**</span></span>

<span data-ttu-id="0f9f0-2072">Den här händelsen representerar sändning av data via en UDP-socket via nx_udp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2072">This event represents sending data through a UDP socket via nx_udp_socket_send.</span></span>

<span data-ttu-id="0f9f0-2073">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2073">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-2074">Informations fält 1: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2074">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-2075">Info fält 2: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2075">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-2076">Informations fält 3: paket längd</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2076">Info Field 3: Packet length</span></span>
- <span data-ttu-id="0f9f0-2077">Info-fält 4: målets IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2077">Info Field 4: Destination IP address</span></span>

### <a name="udp-socket-unbind"></a><span data-ttu-id="0f9f0-2078">UDP-socket-avbindning</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2078">UDP Socket Unbind</span></span> 

#### <a name="nx_udp_socket_unbind"></a><span data-ttu-id="0f9f0-2079">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2079">nx_udp_socket_unbind</span></span>

<span data-ttu-id="0f9f0-2080">**Ikonen** ![ U D P-uppbindning-ikon](./media/user-guide/netx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2080">**Icon** ![U D P socket unbind icon](./media/user-guide/netx-events/image165.png)</span></span>

<span data-ttu-id="0f9f0-2081">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2081">**Description**</span></span>

<span data-ttu-id="0f9f0-2082">Den här händelsen representerar en avbindning av en UDP-port med en socket via nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2082">This event represents unbinding a UDP port with a socket via nx_udp_socket_unbind.</span></span>

<span data-ttu-id="0f9f0-2083">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2083">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-2084">Informations fält 1: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2084">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="0f9f0-2085">Info fält 2: pekare till Socket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2085">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="0f9f0-2086">Informations fält 3: port nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2086">Info Field 3: Port number</span></span>
- <span data-ttu-id="0f9f0-2087">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2087">Info Field 4: Not used</span></span>

### <a name="udp-source-extract"></a><span data-ttu-id="0f9f0-2088">Extrahering av UDP-källa</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2088">UDP Source Extract</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="0f9f0-2089">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2089">nx_udp_socket_create</span></span>

<span data-ttu-id="0f9f0-2090">**Ikonen** ![ U D P P käll extraherings ikon](./media/user-guide/netx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2090">**Icon** ![U D P source extract icon](./media/user-guide/netx-events/image166.png)</span></span>

<span data-ttu-id="0f9f0-2091">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2091">**Description**</span></span>

<span data-ttu-id="0f9f0-2092">Den här händelsen representerar att hämta IP-adressen och port numret för ett mottaget UDP-paket via nx_udp_source_extract.</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2092">This event represents getting the IP address and port number of a received UDP packet via nx_udp_source_extract.</span></span>

<span data-ttu-id="0f9f0-2093">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2093">**Information Fields**</span></span>

- <span data-ttu-id="0f9f0-2094">Info fält 1: pekar mot paket</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2094">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="0f9f0-2095">Informations fält 2: avsändarens IP-adress</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2095">Info Field 2: Sender's IP address</span></span>
- <span data-ttu-id="0f9f0-2096">Informations fält 3: avsändarens port nummer</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2096">Info Field 3: Sender's port number</span></span>
- <span data-ttu-id="0f9f0-2097">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="0f9f0-2097">Info Field 4: Not used</span></span>