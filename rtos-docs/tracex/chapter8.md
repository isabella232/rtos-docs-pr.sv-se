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
# <a name="chapter-8---azure-rtos-netx-trace-events"></a>Kapitel 8 – Azure återställnings tider NetX trace Events

Det här kapitlet innehåller en beskrivning av Azure återställnings tider NetX-händelser. 

## <a name="list-of-events-and-icons"></a>Lista över händelser och ikoner

Följande är en lista över NetX-händelser som visas av TraceX.

| Ikon                                           | Innebörd                 |
| -------------------------------- | ------------------------------------- |
| ![Intern A R P P-ikon för mottagnings förfrågan](./media/user-guide/netx-events/image1.png)    | Mottagning av intern ARP-begäran |
| ![Intern A R P P-ikon för att skicka förfrågan](./media/user-guide/netx-events/image2.png)    | Skicka intern ARP-begäran |
| ![Intern A R P-ikon för svars mottagning](./media/user-guide/netx-events/image3.png)    | Mottagna interna ARP-svar |
| ![Intern A R P P svar ikon för skicka](./media/user-guide/netx-events/image4.png)    | Skicka internt ARP-svar |
| ![Intern I C M P-ikon för mottagning](./media/user-guide/netx-events/image5.png)    | Internt ICMP-mottagning |
| ![Intern I/P e P skicka-ikon](./media/user-guide/netx-events/image6.png)    | Intern ICMP-sändning |
| ![Intern NetX I G M P-ikon](./media/user-guide/netx-events/image7.png)    | Internt NetX IGMP Receive |
| ![Intern I/e-ikon](./media/user-guide/netx-events/image8.png)    | Ta emot internt IP |
| ![Intern I/e-ikon](./media/user-guide/netx-events/image9.png)    | Skicka intern IP |
| ![Intern T C P data Receive-ikon](./media/user-guide/netx-events/image10.png)    | Mottagna interna TCP-data |
| ![Inbyggt T C P data Send-ikon](./media/user-guide/netx-events/image11.png)    | Intern TCP-data överföring |
| ![Intern T C P P-mottagnings ikon](./media/user-guide/netx-events/image12.png)    | Intern TCP FIN mottagning |
| ![Inbyggt T C P F I N skicka ikon](./media/user-guide/netx-events/image13.png)    | Intern TCP RÄNTETRANS-sändning |
| ![Inbyggt T C P R S T Inleverera-ikon](./media/user-guide/netx-events/image14.png)    | Internt TCP-mottagna |
| ![Intern T R P R S T skicka-ikon](./media/user-guide/netx-events/image15.png)    | Intern TCP-överföring |
| ![Ikon för intern T C P S Y N-mottagning](./media/user-guide/netx-events/image16.png)    | Ta emot internt TCP-SYN |
| ![Intern T C P S Y N skicka-ikon](./media/user-guide/netx-events/image17.png)    | Skicka internt TCP-SYN |
| ![Intern U D P-mottagnings ikon](./media/user-guide/netx-events/image18.png)    | Internt UDP-mottagning |
| ![Intern U D P-skicka-ikon](./media/user-guide/netx-events/image19.png)    | Intern UDP-sändning |
| ![Intern R A R P-ikon för mottagning](./media/user-guide/netx-events/image20.png)    | Intern RARP-mottagning |
| ![Interna R A R P-ikonen skicka](./media/user-guide/netx-events/image21.png)    | Intern RARP-sändning |
| ![Inbyggt T C P-återförsök-ikon](./media/user-guide/netx-events/image22.png)    | Internt TCP-försök |
| ![Ändrings ikon för den interna T C P-statusen](./media/user-guide/netx-events/image23.png)    | Intern TCP-tillstånds ändring |
| ![Ikon för att skicka intern I/O-drivrutin](./media/user-guide/netx-events/image24.png)    | Skicka internt I/O-drivrutins paket |
| ![storleken på](./media/user-guide/netx-events/image25.png)    | Intern I/O-drivrutin initieras |
| ![Initiera ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image26.png)    | Intern I/O driv Rutins länk aktivera |
| ![Ikon för inaktive ring av intern I/O-drivrutin](./media/user-guide/netx-events/image27.png)    | Inaktivera intern I/O driv Rutins länk |
| ![Ikon för intern I/O-drivrutin för driv Rutins paket](./media/user-guide/netx-events/image28.png)    | Intern I/O-drivrutins paket sändning |
| ![Skicka ikon för intern I/O-drivrutins-ARP](./media/user-guide/netx-events/image29.png)    | Överföring av intern I/O-drivrutins-ARP |
| ![Intern I/O-drivrutin för ARP-svar skicka ikon](./media/user-guide/netx-events/image30.png)    | Intern I/O-drivrutin ARP-svar skicka |
| ![Intern I/O driv rutin RARP skicka ikon](./media/user-guide/netx-events/image31.png)    | Intern I/O-drivrutin RARP skicka |
| ![Ikon för multicast-anslutning för intern I/O-drivrutin](./media/user-guide/netx-events/image32.png)    | Intern I/O-drivrutin multicast-anslutning |
| ![Ikon för multicast för intern I/O-drivrutin](./media/user-guide/netx-events/image33.png)    | Intern I/O-drivrutin för multicast-ledighet |
| ![Status ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image34.png)    | Status för intern I/O-drivrutin för hämtning |
| ![Intern I/O driv rutin Hämta hastighets ikon](./media/user-guide/netx-events/image35.png)    | Intern I/O-drivrutin Hämta hastighet |
| ![Intern I/O-drivrutin Hämta duplex-typ ikon](./media/user-guide/netx-events/image36.png)    | Intern I/O-drivrutin Hämta duplex-typ |
| ![Ikon för Hämta fel antal för intern I/O-drivrutin](./media/user-guide/netx-events/image37.png)    | Fel antal för intern I/O-drivrutin |
| ![Intern I/O-drivrutin Hämta RX-ikon](./media/user-guide/netx-events/image38.png)    | Intern I/O-drivrutin Hämta RX-antal |
| ![Intern I/O-drivrutin för Hämta TX-antal](./media/user-guide/netx-events/image39.png)    | Intern I/O-drivrutin Hämta TX-antal |
| ![Ikon för Hämta tilldelnings fel för intern I/O-drivrutin](./media/user-guide/netx-events/image40.png)    | Intern I/O-drivrutin Hämta tilldelnings fel |
| ![Ikon för intern I/O-drivrutin för avinitiering](./media/user-guide/netx-events/image41.png)    | Intern I/O-drivrutin avinitieras |
| ![Intern I/O-drivrutin för uppskjuten bearbetning](./media/user-guide/netx-events/image42.png)    | Intern I/O-drivrutin uppskjuten bearbetning |
| ![En ogiltig ikon för R P dynamiska poster](./media/user-guide/netx-events/image43.png)    | **Avvalidering av dynamiska ARP-poster** (*nx_arp_dynamic_entries_invalidate*) |
| ![En R P-ikon för dynamisk inmatnings uppsättning](./media/user-guide/netx-events/image44.png)    | **Dynamisk ARP-inmatnings uppsättning** (*nx_arp_dynamic_entry_set*) |
| ![Ikonen R P aktivera](./media/user-guide/netx-events/image45.png)    | **Aktivera ARP** (*nx_arp_enable*) |
| ![En R P-ikon för att skicka en kostnads fria sändning](./media/user-guide/netx-events/image46.png)    | **ARP, kostnads överföring** (*nx_arp_gratuitous_send*) |
| ![Ikonen R P P maskin varu adress Sök](./media/user-guide/netx-events/image47.png)    | **Sök efter ARP-maskinvara** (*nx_arp_hardware_address_find*) |
| ![En R P P information get-ikon](./media/user-guide/netx-events/image48.png)    | **Hämta ARP-information** (*nx_arp_info_get*) |
| ![Ikonen R P P IP-adress Sök](./media/user-guide/netx-events/image49.png)    | **ARP IP-adress Sök** (*nx_arp_ip_address_find*) |
| ![En ikon för att skapa R P statisk post](./media/user-guide/netx-events/image50.png)    | **Skapa statisk post i ARP** (*nx_arp_static_entry_create*) |
| ![Ta bort ikon för R P statisk poster](./media/user-guide/netx-events/image51.png)    | **Ta bort ARP statiska poster** (*nx_arp_static_entries_delete*) |
| ![Ikonen R P statisk post Delete](./media/user-guide/netx-events/image52.png)    | **Statisk borttagning av ARP-post** (*nx_arp_static_entry_delete*) |
| ![Duo cache Entry ta bort ikon](./media/user-guide/netx-events/image53.png)    | **Borttagning av Duo-cachepost** (*nxd_nd_cache_entry_delete*) |
| ![Ikon för Duo cache Entry set](./media/user-guide/netx-events/image54.png)    | **Duo cache-startpunkt** (*nxd_nd_cache_entry_set*) |
| ![Ikonen för Duo cache-Invalidate](./media/user-guide/netx-events/image55.png)    | **Duo-cachelagring är ogiltig** (*nxd_nd_cache_invalidate*) |
| ![Duo-cache I P-adress Sök ikon](./media/user-guide/netx-events/image56.png)    | **Duo-cache IP-adress Sök** (*nxd_nd_cache_ip_address_find*) |
| ![Ikonen Duo I C M P Enable](./media/user-guide/netx-events/image57.png)    | **Duo ICMP Enable** (*nxd_icmp_enable*) |
| ![Ikonen Duo I C M P I P v v 6-ping](./media/user-guide/netx-events/image58.png)    | **Duo ICMP IPv6-ping** (*nxd_icmp_ping*) |
| ![Ikonen Duo I P Max storlek för nytto Last](./media/user-guide/netx-events/image59.png)    | **Duo IP Max storlek för nytto laster Sök** (*nx_max_payload_size_find*) |
| ![Ikonen Duo I P RAW Packet sändning](./media/user-guide/netx-events/image60.png)    | **Duo IP RAW-paket sändning** (*nxd_ip_raw_packet_send*) |
| ![Duo I P v v standard ikon för Lägg till router](./media/user-guide/netx-events/image61.png)    | **Duo IPv6 standard router Add** (*nxd_ipv6_default_router_add*) |
| ![Duo I P v v standard ikon för ta bort router](./media/user-guide/netx-events/image62.png)    | **Duo IPv6 standardrouter ta bort** (*nxd_ipv6_default_router_delete)* |
| ![Duo I P v v v Aktivera ikon](./media/user-guide/netx-events/image63.png)    | **Duo IPv6 Enable** (*nxd_ipv6_enable)* |
| ![Ikonen Duo I P v v 6 global adress Hämta](./media/user-guide/netx-events/image64.png)    | **Duo IPv6 global adress get** (*nxd_ipv6_global_address_get*) |
| ![Ikonen Duo I P v v v 6, global adress uppsättning](./media/user-guide/netx-events/image65.png)    | **Global adress uppsättning för Duo IPv6** (*nxd_ipv6_global_address_set*) |
| ![Duo I P v v v Starta pappa-process ikon](./media/user-guide/netx-events/image66.png)    | **Duo IPv6-initiera pappa-process** (*nxd_ipv6_initiate_dad_process*) |
| ![Duo I P v v v-ikonen Hämta ikon](./media/user-guide/netx-events/image67.png)    | **Duo IPv6-gränssnitt adress Hämta** (*nxd_ipv6_interface_address_get*) |
| ![Ikon för ikonen Duo I P v v v-gränssnittet](./media/user-guide/netx-events/image68.png)    | **Duo IPv6 gränssnitts adress uppsättning** (*nxd_ipv6_interface_address_set*) |
| ![Ikonen Duo I P v v v länk lokal adress Hämta ikon](./media/user-guide/netx-events/image69.png)    | **Duo IPv6 länk lokal adress hämtning** (*nxd_ipv6_linklocal_address_get*) |
| ![Ikonen Duo I P v v v-länk lokalt adress uppsättning](./media/user-guide/netx-events/image70.png)    | **Duo IPv6-länk lokal adress uppsättning** (*nxd_ipv6_linklocal_address_set*) |
| ![Duo I P v v v-ikon för RAW Packet-sändning](./media/user-guide/netx-events/image71.png)    | **Duo IPv6 RAW Packet Send** (*nxd_ipv6_raw_packet_send)* |
| ![Duo T C P socket peer information get ikon](./media/user-guide/netx-events/image72.png)    | **Duo TCP socket peer information get** (*nxd_tcp_socket_peer_info_get*) |
| ![Ikonen Duo T C P socket set Interface](./media/user-guide/netx-events/image73.png)    | **Duo TCP socket set Interface** (*nxd_tcp_socket_set_interface*) |
| ![Duo U D P uttag ikon för skicka](./media/user-guide/netx-events/image74.png)    | **Duo UDP-socket sändning** (*nxd_udp_socket_send*) |
| ![Ikonen Duo U D P socket set Interface](./media/user-guide/netx-events/image75.png)    | **Duo UDP socket set Interface** (*nxd_udp_socket_set_interface*) |
| ![Duo U D P-käll extraherings ikon](./media/user-guide/netx-events/image76.png)    | **Duo UDP käll extrahering** (*nxd_udp_source_extract*) |
| ![I C M P Enable-ikon](./media/user-guide/netx-events/image77.png)    | **Aktivera ICMP** (*nx_icmp_enable*) |
| ![I C M P information get-ikonen](./media/user-guide/netx-events/image78.png)    | **ICMP information get** (*nx_icmp_info_get*) |
| ![I C M P ping-ikonen](./media/user-guide/netx-events/image79.png)    | **ICMP-Ping** (*nx_icmp_ping*) |
| ![I G M P Enable-ikon](./media/user-guide/netx-events/image80.png)    | **Aktivera IGMP** (*nx_igmp_enable*) |
| ![I G M P information get-ikon](./media/user-guide/netx-events/image81.png)    | **Hämta IGMP information** (*nx_igmp_info_get*) |
| ![I G M P loopback inaktivera ikon](./media/user-guide/netx-events/image82.png)    | **Inaktivera IGMP loopback** (*nx_igmp_loopback_disable*) |
| ![I G M P loopback Aktivera ikon](./media/user-guide/netx-events/image83.png)    | **Aktivera IGMP loopback** (*nx_igmp_loopback_enable*) |
| ![I G M P-ikon för multicast-anslutning](./media/user-guide/netx-events/image84.png)    | **IGMP multicast-anslutning** (*nx_igmp_multicast_join*) |
| ![Ikonen I G M P multicast-tjänstledighet](./media/user-guide/netx-events/image85.png)    | **IGMP multicast-ledighet** (*nx_igmp_multicast_leave*) |
| ![I P adress ändrings aviserings ikon](./media/user-guide/netx-events/image86.png)    | **Avisering om ändring av IP-adress** (*nx_ip_address_change_notify*) |
| ![Hämta ikon för mitt P-adress](./media/user-guide/netx-events/image87.png)    | **Hämta IP-adress** (*nx_ip_address_get*) |
| ![Ikonen I P Address set](./media/user-guide/netx-events/image88.png)    | **IP-adress uppsättning** (*nx_ip_address_set*) |
| ![I P skapa ikon](./media/user-guide/netx-events/image89.png)    | **Skapa IP-adress** (*nx_ip_create*) |
| ![I P ta bort-ikonen](./media/user-guide/netx-events/image90.png)    | **IP-borttagning** (*nx_ip_delete*) |
| ![I P driv rutin Direct kommando ikon](./media/user-guide/netx-events/image91.png)    | **IP-drivrutin Direct-kommando** (*nx_ip_driver_direct_command*) |
| ![I P-ikonen inaktivera](./media/user-guide/netx-events/image92.png)    | **Inaktivera IP-vidarebefordring** (*nx_ip_forwarding_disable*) |
| ![Aktiverings ikon för I P P-vidarebefordring](./media/user-guide/netx-events/image93.png)    | **Aktivera IP-vidarebefordring** (*nx_ip_forwarding_enable*) |
| ![I P fragment, inaktivera ikon](./media/user-guide/netx-events/image94.png)    | **Inaktivera IP-fragment** (*nx_ip_fragment_disable*) |
| ![Ikon för att aktivera I f-fragment](./media/user-guide/netx-events/image95.png)    | **Aktivera IP-fragment** (*nx_ip_fragment_enable*)  |
| ![Ikonen I P Gateway-adress uppsättning](./media/user-guide/netx-events/image96.png)    | **Adress uppsättning för IP-gateway** (*nx_ip_gateway_address_set*) |
| ![I P information get-ikonen](./media/user-guide/netx-events/image97.png)    | **Hämta IP-information** (*nx_ip_info_get*) |
| ![Ikon för att koppla mitt gränssnitt](./media/user-guide/netx-events/image98.png)    | **IP-gränssnitt kopplat** (*nx_ip_interface_attach*) |
| ![I P gränssnitts information Hämta ikon](./media/user-guide/netx-events/image99.png)    | **Hämta information om IP-gränssnitt** (*nx_ip_interface_info_get*) |
| ![Ikonen inaktivera I RAW-paket](./media/user-guide/netx-events/image100.png)    | **Inaktivera IP RAW-paket** (*nx_ip_raw_packet_disable*) |
| ![Ikonen aktivera I RAW-paket](./media/user-guide/netx-events/image101.png)    | **Aktivera IP RAW-paket** (*nx_ip_raw_packet_enable*) |
| ![Ikonen för att ta emot RAW-paket](./media/user-guide/netx-events/image102.png)    | **Ta emot IP RAW-paket** (*nx_ip_raw_packet_receive*) |
| ![I P skicka ikon för RAW Packet-sändning](./media/user-guide/netx-events/image103.png)    | **Skicka IP RAW-paket** (*nx_ip_raw_packet_send*) |
| ![I P statisk väg, Lägg till ikon](./media/user-guide/netx-events/image104.png)    | **Lägg till statisk väg för IP** (*nx_ip_static_route_add*) |
| ![I P statisk väg ta bort ikon](./media/user-guide/netx-events/image105.png)    | **IP-statisk väg borttagning** (*nx_ip_static_route_delete)* |
| ![Kontroll ikon för I P-status](./media/user-guide/netx-events/image106.png)    | **Kontroll av IP-status** (*nx_ip_status_check*)|
| ![I P S E C Aktivera ikon](./media/user-guide/netx-events/image107.png)    | **Aktivera IPsec** (*nx_ipsec_enable)* |
| ![Ikon för paket tilldelning](./media/user-guide/netx-events/image108.png)    | **Paket tilldelning** (*nx_packet_allocate*) |
| ![Paket kopierings ikon](./media/user-guide/netx-events/image109.png)    | **Paket kopia** (*nx_packet_copy*) |
| ![Ikon för Lägg till paket data](./media/user-guide/netx-events/image110.png)    | **Lägg till paket data** (*nx_packet_data_append*) |
| ![Förskjutnings ikon för extrahering av paket data](./media/user-guide/netx-events/image111.png)    | **Offset för extrahering av paket data** (*nx_packet_data_extract_offset*) |
| ![Hämta ikon för paket data](./media/user-guide/netx-events/image112.png)    | **Hämta paket data** (*nx_packet_data_retrieve*) |
| ![Hämta ikon för paket längd](./media/user-guide/netx-events/image113.png)    | **Hämta paket längd** (*nx_packet_length_get*) |
| ![Ikon för att skapa paket pool](./media/user-guide/netx-events/image114.png)    | **Skapa paket bassäng** (*nx_packet_pool_create*) |
| ![Ikon för borttagning av paket pool](./media/user-guide/netx-events/image115.png)    | **Ta bort paket bassäng** (*nx_packet_pool_delete*) |
| ![Hämta ikon för paket Pools information](./media/user-guide/netx-events/image116.png)    | **Hämta paketets pool information** (*nx_packet_pool_info_get*) |
| ![Ikon för paket frigörelse](./media/user-guide/netx-events/image117.png)    | **Paket release** (*nx_packet_release*) |
| ![Ikon för paket sändnings version](./media/user-guide/netx-events/image118.png)    | **Paket överförings version** (*nx_packet_transmit_release*) |
| ![R A R P inaktivera ikon](./media/user-guide/netx-events/image119.png)    | **Inaktivera RARP** (*nx_rarp_disable*) |
| ![R A R P Aktivera ikon](./media/user-guide/netx-events/image120.png)    | **Aktivera RARP** (*nx_rarp_enable*) |
| ![R A R P P-ikonen Hämta information](./media/user-guide/netx-events/image121.png)    | **RARP information get** (*nx_rarp_info_get*) |
| ![Ikon för system initiering](./media/user-guide/netx-events/image122.png)    | **System initiering** (*nx_system_initialize*) |
| ![Ikonen för T C P client socket bind](./media/user-guide/netx-events/image123.png)    | **TCP-klientens socket bind** (*nx_tcp_client_socket_bind*) |
| ![T C P P Connect-ikon för klient-socket](./media/user-guide/netx-events/image124.png)    | **TCP klient-socket Connect** (*nx_tcp_client_socket_connect*) |
| ![Ikonen Hämta ikon för T C P client socket](./media/user-guide/netx-events/image125.png)    | **Hämta TCP-klientens socket-port** (*nx_tcp_client_socket_port_get*) |
| ![Ikon för T C P P-bindning för klient-socket](./media/user-guide/netx-events/image126.png)    | **TCP-klientens socket-bindning** (*nx_tcp_client_socket_unbind*) |
| ![Ikonen T C P Enable](./media/user-guide/netx-events/image127.png)    | **TCP-aktivering** (*nx_tcp_enable*) |
| ![T C P kostnads fri port hitta ikon](./media/user-guide/netx-events/image128.png)    | **Sök efter lediga TCP-portar** (*nx_tcp_free_port_find*) |
| ![T C P information get-ikon](./media/user-guide/netx-events/image129.png)    | **Hämta TCP-information** (*nx_tcp_info_get*) |
| ![Ikonen för T C P P-mottagning för Server uttag](./media/user-guide/netx-events/image130.png)    | **TCP server-socket acceptera** (*nx_tcp_server_socket_accept*) |
| ![Lyssnings ikon för T C P i Server uttag](./media/user-guide/netx-events/image131.png)    | **TCP server-socket lyssna** (*nx_tcp_server_socket_listen*) |
| ![Ikon för T C P P relister för Server uttag](./media/user-guide/netx-events/image132.png)    | **TCP server socket relister** (*nx_tcp_server_socket_relisten*) |
| ![Ikon för att ta emot en ikon för T C P-nätuttag](./media/user-guide/netx-events/image133.png)    | **TCP server-socket accepteras** inte (*nx_tcp_server_socket_unaccept*) |
| ![Ikon för T C P P-avregistrering av Server-socket](./media/user-guide/netx-events/image134.png)    | **TCP-serverns socket avlistar** (*nx_tcp_server_socket_unlisten*) |
| ![Ikon för T C P-socket-tillgängliga byte](./media/user-guide/netx-events/image135.png)    | **Tillgängliga TCP-socket byte** (*nx_tcp_socket_bytes_available*) |
| ![T C P uttag ikon för skapa](./media/user-guide/netx-events/image136.png)    | **TCP-socket-skapande** (*nx_tcp_socket_create*) |
| ![Ta bort ikon för T C P socket](./media/user-guide/netx-events/image137.png)    | **Ta bort TCP-socket** (*nx_tcp_socket_delete*) |
| ![Ikon för T C P uttag från koppling](./media/user-guide/netx-events/image138.png)    | **TCP-socket från koppling** (*nx_tcp_socket_disconnect*) |
| ![T C P socket information get-ikon](./media/user-guide/netx-events/image139.png)    | **TCP socket information get** (*nx_tcp_socket_info_get*) |
| ![Ikon för T C P socket MSS get](./media/user-guide/netx-events/image140.png)    | **TCP-socket MSS get** (*nx_tcp_socket_mss_get*) |
| ![T C P socket MSS peer get-ikon](./media/user-guide/netx-events/image141.png)    | **TCP-socket MSS peer get** (*nx_tcp_socket_mss_peer_get*) |
| ![Ikon för T C P socket MSS-uppsättning](./media/user-guide/netx-events/image142.png)    | **TCP-socket MSS-uppsättning** (*nx_tcp_socket_mss_set*) |
| ![Hämta ikon för T C P socket peer info](./media/user-guide/netx-events/image143.png)    | **Hämta peer-information för TCP-socket** (*nx_tcp_socket_peer_info_get*) |
| ![Ikon för T C P socket Receive](./media/user-guide/netx-events/image144.png)    | **Mottagning av TCP-socket** (*nx_tcp_socket_receive*) |
| ![Ikonen för T C P socket Receive-avisering](./media/user-guide/netx-events/image145.png)    | **Mottagnings meddelande för TCP-socket** (*nx_tcp_socket_receive_notify*) |
| ![T C P socket-sändning, ikon](./media/user-guide/netx-events/image146.png)    | **TCP-socket-sändning** (*nx_tcp_socket_send*) |
| ![Vänta-ikon för T C P-insocket-tillstånd](./media/user-guide/netx-events/image147.png)    | **Vänte läge för TCP-socket** (*nx_tcp_socket_state_wait*) |
| ![Konfigurations ikon för T C P socket-överföring](./media/user-guide/netx-events/image148.png)    | **Konfigurera TCP socket-överföring** (*nx_tcp_socket_transmit_configure*) |
| ![Ikon för att uppdatera aviserings uppsättning i T C P socket Window](./media/user-guide/netx-events/image149.png)    | **TCP-socket fönstret uppdatering av meddelande uppsättning** (*nx_tcp_socket_window_update_notify_set*)  |
| ![U D P Enable-ikon](./media/user-guide/netx-events/image150.png)    | **UDP-aktivering** (*nx_udp_enable*) |
| ![U D P kostnads fri port hitta ikon](./media/user-guide/netx-events/image151.png)    | **Kostnads fri UDP-port hitta** (*nx_udp_free_port_find*) |
| ![U D P information get-ikon](./media/user-guide/netx-events/image152.png)    | **Hämta UDP-information** (*nx_udp_info_get*) |
| ![U D P v socket bind-ikon](./media/user-guide/netx-events/image153.png)    | **UDP-socket bind** (*nx_udp_socket_bind*) |
| ![Ikon för U D P socket-tillgängliga byte](./media/user-guide/netx-events/image154.png)    | **Tillgängliga UDP-socket-byte** (*nx_udp_socket_bytes_available*) |
| ![Inaktivera ikon för U D P socket-kontrollsumma](./media/user-guide/netx-events/image155.png)    | **Inaktivera kontroll summa för UDP-socket** (*nx_udp_socket_checksum_disable*) |
| ![Ikon för U D P-uttag för kontroll Summa](./media/user-guide/netx-events/image156.png)    | **Aktivera kontroll summa för UDP-uttag** *(nx_udp_socket_checksum_enable)* |
| ![U D P uttag ikon för skapa](./media/user-guide/netx-events/image157.png)    | **Skapa UDP-socket** (*nx_udp_socket_create*) |
| ![U D P socket ta bort ikon](./media/user-guide/netx-events/image158.png)    | **Ta bort UDP-socket** (*nx_udp_socket_delete*) |
| ![U D socket information get-ikon](./media/user-guide/netx-events/image159.png)    | **Hämta UDP-socket information** (*nx_udp_socket_info_get*) |
| ![Ikonen U D P socket interface set](./media/user-guide/netx-events/image160.png)    | **Gränssnitts uppsättning för UDP-socket** (*nx_udp_socket_interface_set*) |
| ![U D P socket port get-ikon](./media/user-guide/netx-events/image161.png)    | **Hämta UDP-socket** (*nx_udp_socket_port_get*) |
| ![U D P socket Receive-ikon](./media/user-guide/netx-events/image162.png)    | **Mottagning av UDP-socket** (*nx_udp_socket_receive*) |
| ![U D P socket ta emot meddelande ikon](./media/user-guide/netx-events/image163.png)    | **Mottagnings meddelande för UDP-socket** (*nx_udp_socket_receive_notify*) |
| ![U D P socket-skicka-ikon](./media/user-guide/netx-events/image164.png)    | **Skicka UDP-socket** (*nx_udp_socket_send*) |
| ![U D P-uppbindning-ikon](./media/user-guide/netx-events/image165.png)    | **UDP-socket-avbindning** (*nx_udp_socket_unbind*) |
| ![U D P P käll extraherings ikon](./media/user-guide/netx-events/image166.png)    | **UDP-käll extrahering** (*nx_udp_source_extract*) |

## <a name="event-descriptions"></a>Händelse beskrivningar

Följande sidor beskriver NetX spårnings händelser.

### <a name="internal-arp-request-receive"></a>Mottagning av intern ARP-begäran 

#### <a name="internal-arp-request-receive"></a>Mottagning av intern ARP-begäran

**Ikonen** ![ Ta emot ikon för intern ARP-begäran](./media/user-guide/netx-events/image1.png)

**Beskrivning**

Den här händelsen representerar en intern NetX ARP-begäran ta emot händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: Källans IP-adress
- Info-fält 3: pekar mot paket
- Info fält 4: används inte

### <a name="internal-arp-request-send"></a>Skicka intern ARP-begäran 

#### <a name="internal-arp-request-send"></a>Skicka intern ARP-begäran

**Ikonen** ![ Skicka ikon för intern ARP-begäran](./media/user-guide/netx-events/image2.png)

**Beskrivning**

Den här händelsen representerar en intern NetX ARP-begäran skicka händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: målets IP-adress
- Info-fält 3: pekar mot paket
- Info fält 4: används inte

### <a name="internal-arp-response-receive"></a>Mottagna interna ARP-svar 

#### <a name="internal-arp-request-receive"></a>Mottagning av intern ARP-begäran

**Ikonen** ![ Den interna ARP-begäran ta emot ikon](./media/user-guide/netx-events/image3.png)

**Beskrivning**

Den här händelsen representerar en händelse för en intern NetX ARP-svar.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: Källans IP-adress
- Info-fält 3: pekar mot paket
- Info fält 4: används inte

### <a name="internal-arp-response-send"></a>Skicka internt ARP-svar 

#### <a name="internal-arp-request-send"></a>Skicka intern ARP-begäran

**Ikonen** ![ Den interna ARP-begäran skicka ikon](./media/user-guide/netx-events/image4.png)

**Beskrivning**

Den här händelsen representerar en intern NetX som skickar svars händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: målets IP-adress
- Info-fält 3: pekar mot paket
- Info fält 4: används inte

### <a name="internal-icmp-receive"></a>Internt ICMP-mottagning 

#### <a name="internal-icmp-receive"></a>Internt ICMP-mottagning

**Ikonen** ![ Intern I C M P-ikon för mottagning](./media/user-guide/netx-events/image5.png)

**Beskrivning**

Den här händelsen representerar en intern NetX ICMP Receive-händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: Källans IP-adress
- Info-fält 3: pekar mot paket
- Info fält 4: Word 0 av ICMP-sidhuvud

### <a name="internal-icmp-send"></a>Intern ICMP-sändning 

#### <a name="internal-icmp-send"></a>Intern ICMP-sändning

**Ikonen** ![ Intern I/P e P skicka-ikon](./media/user-guide/netx-events/image6.png)

**Beskrivning**

Den här händelsen representerar en intern NetX ICMP Send-händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: målets IP-adress
- Info-fält 3: pekar mot paket
- Info fält 4: Word 0 av ICMP-sidhuvud

### <a name="internal-igmp-receive"></a>Intern IGMP-mottagning 

#### <a name="internal-igmp-receive"></a>Intern IGMP-mottagning

**Ikonen** ![ Internt I G/P-ikon för mottagning](./media/user-guide/netx-events/image7.png)

**Beskrivning**

Den här händelsen representerar en intern NetX IGMP Receive-händelse.

**Informations fält**

- Informations fält 1: IP-pekare
- Informations fält 2: Källans IP-adress
- Info-fält 3: pekar mot paket
- Info fält 4: Word 0 av IGMP-huvud

### <a name="internal-ip-receive"></a>Ta emot internt IP 

#### <a name="internal-ip-receive"></a>Ta emot internt IP

**Ikonen** ![ Intern I/e-ikon](./media/user-guide/netx-events/image8.png)

**Beskrivning**

Den här händelsen representerar en intern NetX IP-mottagnings händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: Källans IP-adress
- Info-fält 3: pekar mot paket
- Info fält 4: paket längd

### <a name="internal-ip-send"></a>Skicka intern IP

#### <a name="internal-ip-send"></a>Skicka intern IP

**Ikonen** ![ Intern I/e-ikon](./media/user-guide/netx-events/image9.png)

**Beskrivning**

Den här händelsen representerar en intern NetX IP-sändnings händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: målets IP-adress
- Info-fält 3: pekar mot paket
- Info fält 4: paket längd

### <a name="internal-tcp-data-receive"></a>Mottagna interna TCP-data 

#### <a name="internal-tcp-data-receive"></a>Mottagna interna TCP-data

**Ikonen** ![ Intern T C P data Receive-ikon](./media/user-guide/netx-events/image10.png)

**Beskrivning**

Den här händelsen representerar en intern NetX för mottagna TCP-data.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: Källans IP-adress
- Info-fält 3: pekar mot paket
- Info fält 4: mottagnings ordnings nummer

### <a name="internal-tcp-data-send"></a>Intern TCP-data överföring 

#### <a name="internal-tcp-data-send"></a>Intern TCP-data överföring

**Ikonen** ![ Inbyggt T C P data Send-ikon](./media/user-guide/netx-events/image11.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP-data sändnings händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekare till Socket
- Info-fält 3: pekar mot paket
- Info-fält 4: överförings ordnings nummer

### <a name="internal-tcp-fin-receive"></a>Intern TCP FIN mottagning 

#### <a name="internal-tcp-fin-receive"></a>Intern TCP fin mottagning

**Ikonen** ![ Inbyggt T C P F I N ta emot-ikon](./media/user-guide/netx-events/image12.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP FIN Receive-händelse.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekare till Socket
- Info-fält 3: pekar mot paket
- Info fält 4: mottagnings ordnings nummer

### <a name="internal-tcp-fin-send"></a>Intern TCP RÄNTETRANS-sändning 

#### <a name="internal-tcp-fin-send"></a>Intern TCP räntetrans-sändning

**Ikonen** ![ Inbyggt T C P F I N skicka ikon](./media/user-guide/netx-events/image13.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP RÄNTETRANS-sändning.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekare till Socket
- Info-fält 3: pekar mot paket
- Info-fält 4: överförings ordnings nummer

### <a name="internal-tcp-rst-receive"></a>Internt TCP-mottagna 

#### <a name="internal-tcp-rst-receive"></a>Internt TCP-mottagna

**Ikonen** ![ Inbyggt T C P R S T Inleverera-ikon](./media/user-guide/netx-events/image14.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP reset Receive-händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen.
- Info fält 2: pekare till Socket.
- Info-fält 3: pekar mot paket.
- Info fält 4: mottagnings ordnings nummer.

### <a name="internal-tcp-rst-send"></a>Intern TCP-överföring 

#### <a name="internal-tcp-rst-send"></a>Intern TCP-överföring

**Ikonen** ![ Intern T R P R S T skicka-ikon](./media/user-guide/netx-events/image15.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP reset Send-händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekare till Socket
- Info-fält 3: pekar mot paket
- Info-fält 4: överförings ordnings nummer

### <a name="internal-tcp-syn-receive"></a>Ta emot internt TCP-SYN 

#### <a name="internal-tcp-syn-receive"></a>Ta emot internt TCP-SYN

**Ikonen** ![ Ikon för intern T C P S Y N-mottagning](./media/user-guide/netx-events/image16.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP SYN-händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekare till Socket
- Info-fält 3: pekar mot paket
- Info fält 4: mottagnings ordnings nummer

### <a name="internal-tcp-syn-send"></a>Skicka internt TCP-SYN 

#### <a name="internal-tcp-syn-send"></a>Skicka internt TCP-SYN

**Ikonen** ![ Intern T C P S Y N skicka-ikon](./media/user-guide/netx-events/image17.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP SYN-sändning.

Informations fält 

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekare till Socket
- Info-fält 3: pekar på paket-info fält 4: överförings ordnings nummer

### <a name="internal-udp-receive"></a>Internt UDP-mottagning 

#### <a name="internal-udp-receive"></a>Internt UDP-mottagning

**Ikonen** ![ Intern U D P-mottagnings ikon](./media/user-guide/netx-events/image18.png)

**Beskrivning**

Den här händelsen representerar en intern NetX UDP Receive-händelse.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekare till Socket
- Info-fält 3: pekar mot paket
- Info fält 4: Word 0 av UDP-huvud

### <a name="internal-udp-send"></a>Intern UDP-sändning 

#### <a name="internal-udp-send"></a>Intern UDP-sändning

**Ikonen** ![ Intern U D P-skicka-ikon](./media/user-guide/netx-events/image19.png)

**Beskrivning**

Den här händelsen representerar en intern NetX UDP-sändning.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekare till Socket
- Info-fält 3: pekar mot paket
- Info fält 4: Word 0 av UDP-huvud

### <a name="internal-rarp-receive"></a>Intern RARP-mottagning 

#### <a name="internal-rarp-receive"></a>Intern RARP-mottagning 

**Ikonen** ![ Intern R A R P-ikon för mottagning](./media/user-guide/netx-events/image20.png)

**Beskrivning**

Den här händelsen representerar en intern NetX RARP Receive-händelse.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: mål-IP-adress
- Info-fält 3: pekar mot paket
- Info fält 4: Word 1 av RARP-huvudet

### <a name="internal-rarp-send"></a>Intern RARP-sändning 

#### <a name="internal-rarp-send"></a>Intern RARP-sändning 

**Ikonen** ![ Interna R A R P-ikonen skicka](./media/user-guide/netx-events/image21.png)

**Beskrivning**

Den här händelsen representerar en intern NetX RARP-sändnings händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: mål-IP-adress
- Info-fält 3: pekar mot paket
- Info fält 4: Word 1 av RARP-huvudet

### <a name="internal-tcp-retry"></a>Internt TCP-försök 

#### <a name="internal-tcp-retry"></a>Internt TCP-försök 

**Ikonen** ![ Inbyggt T C P-återförsök-ikon](./media/user-guide/netx-events/image22.png)

**Beskrivning**

Den här händelsen representerar en intern NetX-händelse för TCP-försök.

**Informations fält**
- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekare till Socket
- Info-fält 3: pekar mot paket
- Info-fält 4: antal återförsök

### <a name="internal-tcp-state-change"></a>Intern TCP-tillstånds ändring 

#### <a name="internal-tcp-state-change"></a>Intern TCP-tillstånds ändring 

**Ikonen** ![ Ändrings ikon för den interna T C P-statusen](./media/user-guide/netx-events/image23.png)

**Beskrivning**

Den här händelsen representerar en intern NetX av status ändrings händelse för TCP-socket.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekare till Socket
- Info-fält 3: föregående tillstånd
- Info fält 4: nytt tillstånd

### <a name="internal-io-driver-packet-send"></a>Skicka internt I/O-drivrutins paket 

#### <a name="internal-io-driver-packet-send"></a>Skicka internt I/O-drivrutins paket

**Ikonen** ![ Ikon för att skicka intern I/O-drivrutin](./media/user-guide/netx-events/image24.png)

**Beskrivning**

Den här händelsen representerar en intern sändnings händelse för NetX I/O-drivrutinen.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekar mot paket
- Informations fält 3: paket storlek
- Info fält 4: används inte

### <a name="internal-io-driver-initialize"></a>Intern I/O-drivrutin initieras 

#### <a name="internal-io-driver-initialize"></a>Intern I/O-drivrutin initieras

**Ikonen** ![ Initiera ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image25.png)

**Beskrivning**

Den här händelsen representerar en intern händelse för NetX I/O-drivrutinen.

**Informations fält**

- Info fält 1: pekar mot IP-instansen.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="internal-io-driver-link-enable"></a>Intern I/O driv Rutins länk aktivera 

#### <a name="internal-io-driver-link-enable"></a>Intern I/O driv rutins länk aktivera

**Ikonen** ![ Ikonen Aktivera ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image26.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutins länk aktivera händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="internal-io-driver-link-disable"></a>Inaktivera intern I/O driv Rutins länk 

#### <a name="internal-io-driver-link-disable"></a>Inaktivera intern I/O driv rutins länk

**Ikonen** ![ Ikon för inaktive ring av intern I/O-drivrutin](./media/user-guide/netx-events/image27.png)

**Beskrivning**

Den här händelsen representerar en intern inaktive rings händelse för NetX I/O-drivrutin.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="internal-io-driver-packet-broadcast"></a>Intern I/O-drivrutins paket sändning 

#### <a name="internal-io-driver-packet-broadcast"></a>Intern I/O-drivrutins paket sändning

**Ikonen** ![ Ikon för intern I/O-drivrutin för driv rutins paket](./media/user-guide/netx-events/image28.png)

**Beskrivning**

Den här händelsen representerar en intern sändnings händelse för NetX I/O-drivrutin.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekar mot paket
- Informations fält 3: paket storlek
- Info fält 4: används inte

### <a name="internal-io-driver-arp-send"></a>Överföring av intern I/O-drivrutins-ARP 

#### <a name="internal-io-driver-arp-send"></a>Överföring av intern I/O-drivrutins-ARP

**Ikonen** ![ Skicka ikon för intern I/O-drivrutins-ARP](./media/user-guide/netx-events/image29.png)

**Beskrivning**

Den här händelsen representerar en intern sändnings händelse för NetX I/O-drivrutin.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekar mot paket
- Informations fält 3: paket storlek
- Info fält 4: används inte

### <a name="internal-io-driver-arp-response-send"></a>Intern I/O-drivrutin ARP-svar skicka 

#### <a name="internal-io-driver-arp-response-send"></a>Intern I/O-drivrutin ARP-svar skicka

**Ikonen** ![ Intern I/O-drivrutin för ARP-svar skicka ikon](./media/user-guide/netx-events/image30.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin ARP-svar skicka händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekar mot paket
- Informations fält 3: paket storlek
- Info fält 4: används inte

### <a name="internal-io-driver-rarp-send"></a>Intern I/O-drivrutin RARP skicka 

#### <a name="internal-io-driver-rarp-send"></a>Intern I/O-drivrutin RARP skicka

**Ikonen** ![ Intern I/O driv rutin RARP skicka ikon](./media/user-guide/netx-events/image31.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin RARP skicka händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekar mot paket
- Informations fält 3: paket storlek
- Info fält 4: används inte

### <a name="internal-io-driver-multicast-join"></a>Intern I/O-drivrutin multicast-anslutning 

#### <a name="internal-io-driver-multicast-join"></a>Intern I/O-drivrutin multicast-anslutning

**Ikonen** ![ Ikon för multicast-anslutning för intern I/O-drivrutin](./media/user-guide/netx-events/image32.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin för IO-anslutning.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="internal-io-driver-multicast-leave"></a>Intern I/O-drivrutin för multicast-ledighet 

#### <a name="internal-io-driver-multicast-leave"></a>Intern I/O-drivrutin för multicast-ledighet

**Ikonen** ![ Ikon för multicast för intern I/O-drivrutin](./media/user-guide/netx-events/image33.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="internal-io-driver-get-status"></a>Status för intern I/O-drivrutin för hämtning 

#### <a name="internal-io-driver-get-status"></a>Status för intern I/O-drivrutin för hämtning

**Ikonen** ![ Status ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image34.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta status händelse.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="internal-io-driver-get-speed"></a>Intern I/O-drivrutin Hämta hastighet 

#### <a name="internal-io-driver-get-speed"></a>Intern I/O-drivrutin Hämta hastighet

**Ikonen** ![ Intern I/O driv rutin Hämta hastighets ikon](./media/user-guide/netx-events/image35.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta hastighet.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="internal-io-driver-get-duplex-type"></a>Intern I/O-drivrutin Hämta duplex-typ 

#### <a name="internal-io-driver-get-duplex-type"></a>Intern I/O-drivrutin Hämta duplex-typ

**Ikonen** ![ Intern I/O-drivrutin Hämta duplex-typ ikon](./media/user-guide/netx-events/image36.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta duplex-typ.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="internal-io-driver-get-error-count"></a>Fel antal för intern I/O-drivrutin

#### <a name="internal-io-driver-get-error-count"></a>Fel antal för intern I/O-drivrutin

**Ikonen** ![ Ikon för Hämta fel antal för intern I/O-drivrutin](./media/user-guide/netx-events/image37.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta fel antal.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="internal-io-driver-get-rx-count"></a>Intern I/O-drivrutin Hämta RX-antal 

#### <a name="internal-io-driver-get-rx-count"></a>Intern I/O-drivrutin Hämta RX-antal

**Ikonen** ![ Intern I/O-drivrutin Hämta RX-ikon](./media/user-guide/netx-events/image38.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta antal RX.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="internal-io-driver-get-tx-count"></a>Intern I/O-drivrutin Hämta TX-antal 

#### <a name="internal-io-driver-get-tx-count"></a>Intern I/O-drivrutin Hämta TX-antal

**Ikonen** ![ Ikon för att hämta T X för intern I/O-drivrutin](./media/user-guide/netx-events/image39.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta TX-antal.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="internal-io-driver-get-allocation-errors"></a>Intern I/O-drivrutin Hämta tilldelnings fel 

#### <a name="internal-io-driver-get-allocation-errors"></a>Intern I/O-drivrutin Hämta tilldelnings fel

**Ikonen** ![ Ikon för Hämta tilldelnings fel för intern I/O-drivrutin](./media/user-guide/netx-events/image40.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin för att hämta tilldelnings fel.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="internal-io-driver-un-initialize"></a>Intern I/O-drivrutin avinitieras 

#### <a name="internal-io-driver-un-initialize"></a>Intern I/O-drivrutin avinitieras 

**Ikonen** ![ Ikon för intern I/O-drivrutin för avinitiering](./media/user-guide/netx-events/image41.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin som avinitieras.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="internal-io-driver-deferred-processing"></a>Intern I/O-drivrutin uppskjuten bearbetning 

#### <a name="internal-io-driver-deferred-processing"></a>Intern I/O-drivrutin uppskjuten bearbetning 

**Ikonen** ![ Intern I/O-drivrutin för uppskjuten bearbetning](./media/user-guide/netx-events/image42.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin som Uppskjut bearbetnings händelsen.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekar mot paket
- Informations fält 3: paket längd
- Info fält 4: används inte

### <a name="arp-dynamic-entries-invalidate"></a>Avvalidering av dynamiska ARP-poster 

#### <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

**Ikonen** ![ En ogiltig ikon för R P dynamiska poster](./media/user-guide/netx-events/image43.png)

**Beskrivning**

Den här händelsen representerar invalideringen av alla dynamiska ARP-hela via nx_arp_dynamic_entries_invalidate.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: ogiltiga poster
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="arp-dynamic-entry-set"></a>Dynamisk ARP-post uppsättning 

#### <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

**Ikonen** ![ En R P-ikon för dynamisk inmatnings uppsättning](./media/user-guide/netx-events/image44.png)

**Beskrivning**

Den här händelsen representerar att ange en dynamisk ARP-post via nx_arp_dynamic_entry_set.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Info fält 2: IP-adress
- Informations fält 3: fysisk adress (MSW)
- Info-fält 4: fysisk adress (LSW)

### <a name="arp-enable"></a>Aktivera ARP 

#### <a name="nx_arp_enable"></a>nx_arp_enable

**Ikonen** ![ Ikonen R P aktivera](./media/user-guide/netx-events/image45.png)

**Beskrivning**

Den här händelsen representerar aktivering av ARP via nx_arp_enable.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: minnes pekare för ARP-cache
- Info-fält 3: minnes storlek för ARP-cache
- Info fält 4: används inte

### <a name="arp-gratuitous-send"></a>ARP, kostnads överföring 

#### <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

**Ikonen** ![ En R P-ikon för att skicka en kostnads fria sändning](./media/user-guide/netx-events/image46.png)

**Beskrivning**

Den här händelsen representerar en kostnads fria ARP-sändning via nx_arp_gratuitous_send.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="arp-hardware-address-find"></a>Sök efter ARP-maskinvara 

#### <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

**Ikonen** ![ Ikonen R P P maskin varu adress Sök](./media/user-guide/netx-events/image47.png)

**Beskrivning**

Den här händelsen representerar att hitta en fysisk adress via nx_arp_hardware_address_find.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Info fält 2: IP-adress
- Informations fält 3: fysisk adress (MSW)
- Info-fält 4: fysisk adress (LSW)

### <a name="arp-information-get"></a>Hämta ARP-information 

#### <a name="nx_arp_info_get"></a>nx_arp_info_get

**Ikonen** ![ En R P P informition get-ikon](./media/user-guide/netx-events/image48.png)

**Beskrivning**

Den här händelsen representerar att hämta information via nx_arp_info_get.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: ARPs har skickats
- Informations fält 3: ARP-svar
- Info fält 4: ARPs mottagen

### <a name="arp-ip-address-find"></a>Sök efter ARP IP-adress 

#### <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

**Ikonen** ![ Ikonen R P I P-adress Sök](./media/user-guide/netx-events/image49.png)

**Beskrivning**

Den här händelsen representerar att hitta en IP-adress som är associerad med den angivna fysiska adressen via nx_arp_ip_address_find.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Info fält 2: IP-adress
- Informations fält 3: fysisk adress (MSW)
- Info-fält 4: fysisk adress (LSW)

### <a name="arp-static-entry-create"></a>Skapa statisk ARP-post 

#### <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

**Ikonen** ![ En ikon för att skapa R P statisk post](./media/user-guide/netx-events/image50.png)

**Beskrivning**

Den här händelsen representerar att skapa en statisk ARP-post via nx_arp_static_entry_create.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: IP-adress
- Informations fält 3: fysisk adress (MSW)
- Info-fält 4: fysisk adress (LSW)

### <a name="arp-static-entries-delete"></a>Ta bort ARP statiska poster 

#### <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

**Ikonen** ![ Ta bort ikon för R P statisk poster](./media/user-guide/netx-events/image51.png)

**Beskrivning**

Den här händelsen representerar borttagning av alla statiska ARP-poster via nx_arp_static_entries_delete.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: poster har tagits bort
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="arp-static-entry-delete"></a>Ta bort ARP statisk post 

### <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

**Ikonen** ![ Ikonen R P statisk post Delete](./media/user-guide/netx-events/image52.png)

**Beskrivning**

Den här händelsen representerar borttagning av en statisk ARP-post via nx_arp_static_entry_delete.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Info fält 2: IP-adress
- Informations fält 3: fysisk adress (MSW)
- Info-fält 4: fysisk adress (LSW)

### <a name="duo-cache-entry-delete"></a>Duo-cachepost ta bort 

#### <a name="nxd_und_cache_entry_delete"></a>nxd_und_cache_entry_delete

**Ikonen** ![ Duo cache Entry ta bort ikon](./media/user-guide/netx-events/image53.png)

**Beskrivning**

Den här händelsen representerar borttagning av en post i den närliggande cache-tabellen via nx_udp_socket_create.

**Informations fält** 

- Informations fält 1: fjärde (minst signifikant) ord för den IPv6-länk lokala adressen som ska tas bort
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="duo-cache-entry-set"></a>Duo cache-post uppsättning 

#### <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set

**Ikonen** ![ Ikon för Duo cache Entry set](./media/user-guide/netx-events/image54.png)

**Beskrivning**

Den här händelsen representerar att skapa en cachepost och lägga till den i den närliggande cache-tabellen via nxd_nd_cache_entry_set.

**Informations fält** 

- Informations fält 1: fjärde (minst signifikant) ord för IPv6-adressen som ska läggas till
- Info-fält 2: fysisk MSB
- Info-fält 3: fysisk lsb
- Info fält 4: används inte

### <a name="duo-cache-invalidate"></a>Duo-cache ogiltig 

#### <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate

**Ikonen** ![ Ikonen för Duo cache-Invalidate](./media/user-guide/netx-events/image55.png)

**Beskrivning**

Den här händelsen representerar att hela den angränsande cache-tabellen ska verifieras via nxd_nd_cache_invalidate.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="duo-cache-ip-address-find"></a>Duo-cache IP-adress Sök 

#### <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find

**Ikonen** ![ Duo-cache I P-adress Sök ikon](./media/user-guide/netx-events/image56.png)

**Beskrivning**

Den här händelsen representerar hämtning av en IP-adress som matchar den angivna fysiska adressen från cache-tabellen via nxd_nd_cache_ip_address_find.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: fjärde (minst signifikant) ord för IPv6-adressen
- Info-fält 3: fysisk MSB
- Info-fält 4: fysisk lsb

### <a name="duo-icmp-enable"></a>Duo ICMP-aktivering 

#### <a name="nxd_icmp_enable"></a>nxd_icmp_enable

**Ikonen** ![ Ikonen Duo I C M P Enable](./media/user-guide/netx-events/image57.png)

**Beskrivning**

Den här händelsen representerar ICMPv4-och ICMPv6-tjänster som Aktiver ATS på den angivna IP-instansen via nxd_icmp_enable.

**Informations fält**
- Informations fält 1: pekare till IP-instans
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="duo-icmp-ping"></a>Duo ICMP-Ping 

#### <a name="nxd_icmp_ping"></a>nxd_icmp_ping

**Ikonen** ![ Ikonen Duo I C M P ping](./media/user-guide/netx-events/image58.png)

**Beskrivning**

Den här händelsen representerar sändning av en ping-begäran (ekobegäran) till en IPv6-värd via nxd_icmp_ping.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: IPv6-adress
- Informations fält 3: pekar på data i eko
- Info fält 4: storlek på ECHO data

### <a name="duo-ip-max-payload-size-find"></a>Duo IP-största nytto Last storlek hitta 

#### <a name="nxd_ip_max_payload_size"></a>nxd_ip_max_payload_size

**Ikonen** ![ Ikonen Duo I P Max storlek för nytto Last](./media/user-guide/netx-events/image59.png)

**Beskrivning**

Den här händelsen beräknar den maximala nytto lasten som det angivna paketet kan medföra utan fragmentering.

**Informations fält**

- Informations fält 1: socket-pekare
- Informations fält 2: peer-IP-adress
- Informations fält 3: information om peer-Port 4: används inte

### <a name="duo-ip-raw-packet-send"></a>Överföring av Duo IP RAW-paket 

#### <a name="nxd_ip_max_packet_send"></a>nxd_ip_max_packet_send

**Ikonen** ![ Ikonen Duo I P RAW Packet sändning](./media/user-guide/netx-events/image60.png)

**Beskrivning**

Den här händelsen representerar att skicka ett RAW IP-paket från det angivna nätverks gränssnittet till den angivna IP-addressvia nxd_ip_raw_packet_send.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till paket att skicka
- Informations fält 3: pekare till mål adress
- Info-fält 4: paket protokoll

### <a name="duo-ipv6-default-router-add"></a>Duo IPv6 standard router Lägg till 

#### <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add

**Ikonen** ![ Duo I P v v standard ikon för Lägg till router](./media/user-guide/netx-events/image61.png)

**Beskrivning**

Den här händelsen representerar att lägga till en standard-router till IP-instansens IPv6-routningstabell via nxd_ipv6_default_router_add.

**Informations fält**

- Informations fält 1: pekare till IP-instans.
- Info-fält 2: mål nätverks adress.
- Info fält 3: information om livs längd.
- Info fält 4: används inte.

### <a name="duo-ipv6-default-router-delete"></a>Duo IPv6 standardrouter ta bort 

#### <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete

**Ikonen** ![ Duo I P v v standard ikon för ta bort router](./media/user-guide/netx-events/image62.png)

**Beskrivning**

Den här händelsen representerar borttagning av en standard-router från IP-instansens IPv6-routningstabell via nxd_ipv6_default_router_delete.

**Informations fält**

- Informations fält 1: pekare till IP-instans.
- Informations fält 2: fjärde ordet (minst signifikant) av IPv6-standardadressen för router.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="duo-ipv6-enable"></a>Duo IPv6 Enable 

#### <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable

**Ikonen** ![ Duo I P v v v Aktivera ikon](./media/user-guide/netx-events/image63.png)

**Beskrivning**

Den här händelsen representerar aktivering av IPv6-tjänster på den angivna IP-instansen via nxd_ipv6_enable.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="duo-ipv6-global-address-get"></a>Global adress för Duo IPv6 get 

#### <a name="nxd_ipv6_global_address_get"></a>nxd_ipv6_global_address_get

**Ikonen** ![ Ikonen Duo I P v v 6 global adress Hämta](./media/user-guide/netx-events/image64.png)

**Beskrivning**

Den här händelsen representerar hämtning av den globala (primära) IP-adressen på IP-instansen som finns på index 1 i tabellen IP-instans-gränssnitt via nxd_ipv6_global_address_get.

**Informations fält**

- Informations fält 1: pekare till IP-instans.
- Informations fält 2: fjärde ordet (minst signifikant) av den globala adressen
- Info-fält 3: längden på IPv6-adressprefixet.
- Info fält 4: index i IP-gränssnitts tabell (1).

### <a name="duo-ipv6-global-address-set"></a>Global adress uppsättning för Duo IPv6 

#### <a name="nxd_ipv6_global_address_set"></a>nxd_ipv6_global_address_set

**Ikonen** ![ Ikonen Duo I P v v v 6, global adress uppsättning](./media/user-guide/netx-events/image65.png)

**Beskrivning**

Den här händelsen representerar att ange den globala (primära) IP-adressen på IP-instansen som finns på index 1 i tabellen IP-instans-gränssnitt via nxd_ipv6_global_address_set.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Informations fält 2: fjärde ordet (minst signifikant) av den globala adressen
- Informations fält 3: längden på IPv6-adressprefixet
- Info fält 4: index i IP-gränssnitts tabell (1)

### <a name="duo-ipv6-initiate-dad-process"></a>Duo IPv6-initiera pappa-process 

#### <a name="nxd_ipv6_initiate_dad_process"></a>nxd_ipv6_initiate_dad_process

**Ikonen** ![ Duo I P v v v Starta pappa-process ikon](./media/user-guide/netx-events/image66.png)

**Beskrivning**

Den här händelsen representerar start processen för den duplicerade adress identifieringen (pappa) när IP-instansen tilldelas en länk lokal eller IP-gränssnitts adress via nxd_ipv6_initiate_dad_process.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="duo-ipv6-interface-address-get"></a>Duo IPv6-gränssnitt adress Hämta 

#### <a name="nxd_ipv6_interface_address_get"></a>nxd_ipv6_interface_address_get

**Ikonen** ![ Duo I P v v v-ikonen Hämta ikon](./media/user-guide/netx-events/image67.png)

**Beskrivning**

Den här händelsen representerar hämtning av IP-adressen och prefixet vid det angivna indexet i IP-instansens gränssnitts adress tabell via nxd_ipv6_interface_address_get.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: fjärde ordet (minst signifikant) för IPv6-adressen som ska returneras
- Info-fält 4: index för gränssnittet i IP-instansens gränssnitts tabell

### <a name="duo-ipv6-interface-address-set"></a>Adress uppsättning för Duo IPv6-gränssnitt 

### <a name="nxd_ipv6_interface_address_set"></a>nxd_ipv6_interface_address_set

**Ikonen** ![ Duo-ikonen I P v v v-gränssnittet](./media/user-guide/netx-events/image68.png)

**Beskrivning**

Den här händelsen representerar att ange IP-adressen och prefixet vid det angivna indexet i adress tabellen för IP-instansen. Tillåts inte för index noll (länk lokal adress) via nxd_ipv6_interface_address_set.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: fjärde ordet (minst signifikant) för IPv6-adressen som ska returneras
- Informations fält 3: prefixlängd
- Info-fält 4: index för gränssnittet i IP-instansens gränssnitts tabell

### <a name="duo-ipv6-link-local-address-get"></a>Duo IPv6-länk lokal adress Hämta 

#### <a name="nxd_ipv6_linklocal_address_get"></a>nxd_ipv6_linklocal_address_get

**Ikonen** ![ Ikonen Duo I P v v v länk lokal adress Hämta ikon](./media/user-guide/netx-events/image69.png)

**Beskrivning**

Den här händelsen representerar hämtning av länkens lokala adress för den angivna IP-instansen via nxd_ipv6_linklocal_address_get.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: fjärde ordet (minst signifikant) av IP V6-länkens lokala adress
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="duo-ipv6-link-local-address-set"></a>Duo IPv6-länk lokal adress uppsättning 

#### <a name="nxd_ipv6_linklocal_address_set"></a>nxd_ipv6_linklocal_address_set

**Ikonen** ![ Ikonen Duo I P v v v-länk lokalt adress uppsättning](./media/user-guide/netx-events/image70.png)

**Beskrivning**

Den här händelsen representerar att ange den lokala länk adressen för IP-instansen via nxd_ipv6_linklocal_address_set.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: fjärde (minst signifikant) ord för IPv6-länkens lokala adress
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="duo-ipv6-raw-packet-send"></a>Duo IPv6 RAW-paket sändning 

#### <a name="nxd_ipv6_raw_packet_send"></a>nxd_ipv6_raw_packet_send

**Ikonen** ![ Duo I P v v v-ikon för RAW Packet-sändning](./media/user-guide/netx-events/image71.png)

**Beskrivning**

Den här händelsen representerar att skicka ett RAW IP-paket via det primära IP-gränssnittet till Proxyport anges-målet via nxd_ip_raw_packet_send.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till paket att skicka
- Informations fält 3: målets IP-adress
- Info fält 4: används inte

### <a name="duo-tcp-socket-peer-info-get"></a>Duo TCP socket peer information get 

#### <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get

**Ikonen** ![ Duo T C P socket peer information get ikon](./media/user-guide/netx-events/image72.png)

**Beskrivning**

Den här händelsen extraherar avsändar data från ett mottaget TCP-paket på den angivna socketen. Den returnerar avsändarens IP-adress och port.

**Informations fält**

- Informations fält 1: socket-pekare
- Informations fält 2: peer-IP-adress
- Informations fält 3: peer-port
- Info-fält 4: lånet är signifikant 32-bitars IP-adressen

### <a name="duo-tcp-socket-set-interface"></a>Duo TCP socket set Interface 

#### <a name="nxd_tcp_socket_set_interface"></a>nxd_tcp_socket_set_interface

**Ikonen** ![ Ikonen Duo T C P socket set Interface](./media/user-guide/netx-events/image73.png)

**Beskrivning**

Den här händelsen representerar att ange utgående socket-gränssnitt när en klient ansluter med en TCP-server på den angivna serverns IP-adress via nxd_tcp_client_socket_connect.

**Informations fält** 

- Informations fält 1: pekare till TCP-socket
- Informations fält 2: gränssnitts-ID
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="duo-udp-socket-send"></a>Duo UDP-socket skicka 

#### <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send

**Ikonen** ![ Duo U D P uttag ikon för skicka](./media/user-guide/netx-events/image74.png)

**Beskrivning**

Den här händelsen representerar att skicka ett UDP-paket via den angivna socketen med IP-adressen för indata och port via nxd_udp_socket_send.

**Informations fält** 

- Info fält 1: pekare UDP-socket
- Info fält 2: pekare till UDP-paket
- Informations fält 3: paket längd
- Info fält 4: används inte


### <a name="duo-udp-socket-set-interface"></a>Duo UDP socket set Interface 

#### <a name="nxd_udp_socket_set_interface"></a>nxd_udp_socket_set_interface

**Ikonen** ![ Ikonen Duo U D P socket set Interface](./media/user-guide/netx-events/image75.png)

**Beskrivning**

Den här händelsen representerar inställningen för det angivna utgående UDP-socket-gränssnittet till gränssnittet som motsvarar ID för indataports-gränssnitt via nxd_udp_socket_set_interface.

**Informations fält** 

- Info fält 1: pekare till UDP-socket
- Informations fält 2: gränssnitts-ID
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="duo-udp-source-extract"></a>Duo UDP-käll extrahering 

#### <a name="nxd_udp_socket_extract"></a>nxd_udp_socket_extract

**Ikonen** ![ Duo U D P-käll extraherings ikon](./media/user-guide/netx-events/image76.png)

**Beskrivning**

Den här händelsen representerar extrahering av IP-adressen och käll porten för ett mottaget paket (antingen IPv4 eller IPv6). Om IPv6 returneras det fjärde ordet (minst signifikant) av IP-adressen via nxd_udp_source_extract.

**Informations fält**

- Info fält 1: pekar mot paketet
- Informations fält 2: IP-version
- Informations fält 3: Källans IP-adress (IPv4 eller IPv6)
- Info-fält 4: källport

### <a name="icmp-enable"></a>ICMP-aktivering 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Ikonen** ![ I C M P Enable-ikon](./media/user-guide/netx-events/image77.png)

**Beskrivning**

Den här händelsen representerar aktivering av ICMP via nx_icmp_enable.

**Informations fält**

- Info fält 1: pekare till IP-instansen l;
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="icmp-information-get"></a>ICMP information get 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Ikonen** ![ I C M P information get-ikonen](./media/user-guide/netx-events/image78.png)

**Beskrivning**

Den här händelsen representerar att hämta information via nx_icmp_info_get.

**Informations fält**
- Info fält 1: pekar mot IP-instansen
- Informations fält 2: pingar skickas
- Info-fält 3: ping-svar
- Info fält 4: mottagna pingar

### <a name="icmp-ping"></a>ICMP-Ping 

#### <a name="nx_icmp_ping"></a>nx_icmp_ping

**Ikonen** ![ I C M P ping-ikonen](./media/user-guide/netx-events/image79.png)

**Beskrivning**

Den här händelsen representerar pinga en mål-IP-adress via nx_icmp_ping.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: IP-adress
- Informations fält 3: pekare till data
- Info fält 4: data storlek

### <a name="igmp-enable"></a>Aktivera IGMP 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Ikonen** ![ I G M P Enable-ikon](./media/user-guide/netx-events/image80.png)

**Beskrivning**

Den här händelsen representerar aktivering av IGMP via nx_igmp_enable.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="igmp-information-get"></a>Hämta IGMP-information 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Ikonen** ![ I G M P information get-ikon](./media/user-guide/netx-events/image81.png)

**Beskrivning**

Den här händelsen representerar att hämta information via nx_igmp_info_get.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: rapporter har skickats
- Informations fält 3: frågor mottagna
- Info fält 4: grupper kopplade

### <a name="igmp-loopback-disable"></a>Inaktivera IGMP loopback 

#### <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

**Ikonen** ![ I G M P loopback inaktivera ikon](./media/user-guide/netx-events/image82.png)

**Beskrivning**

Den här händelsen representerar inaktive ring av IGMP loopback via nx_igmp_loopback_disable.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="igmp-loopback-enable"></a>Aktivera IGMP loopback 

#### <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

**Ikonen** ![ I G M P loopback Aktivera ikon](./media/user-guide/netx-events/image83.png)

**Beskrivning**

Den här händelsen representerar aktivering av IGMP loopback via nx_igmp_loopback_enable.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="igmp-multicast-join"></a>IGMP multicast-anslutning 

#### <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

**Ikonen** ![ I G M P-ikon för multicast-anslutning](./media/user-guide/netx-events/image84.png)

**Beskrivning**

Den här händelsen representerar anslutning till en multicast-grupp via nx_igmp_multicast_join.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: grupp-IP-adress
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="igmp-multicast-leave"></a>IGMP multicast-tjänstledighet 

#### <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

**Ikonen** ![ Ikonen I G M P multicast-tjänstledighet](./media/user-guide/netx-events/image85.png)

**Beskrivning**

Den här händelsen representerar att lämna en multicast-grupp via nx_igmp_multicast_leave.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Info fält 2: grupp-IP-adress
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="ip-address-change-notify"></a>Avisering om ändring av IP-adress 

#### <a name="nx_ip_address_change_notify"></a>nx_ip_address_change_notify

**Ikonen** ![ I P adress ändrings aviserings ikon](./media/user-guide/netx-events/image86.png)

**Beskrivning**

Den här händelsen representerar registrering för meddelanden om IP-ändring via nx_ip_address_change_notify.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: återanrops funktions pekare
- Informations fält 3: ytterligare informations pekare
- Info fält 4: används inte

### <a name="ip-address-get"></a>Hämta IP-adress 

#### <a name="nx_ip_address_get"></a>nx_ip_address_get

**Ikonen** ![ Hämta ikon för mitt P-adress](./media/user-guide/netx-events/image87.png)

**Beskrivning**

Den här händelsen representerar hämtning av IP-adressen via nx_ip_address_get.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: IP-adress
- Informations fält 3: nätverks mask
- Info fält 4: används inte

### <a name="ip-address-set"></a>IP-adress uppsättning 

#### <a name="nx_ip_address_set"></a>nx_ip_address_set

**Ikonen** ![ Ikonen I P Address set](./media/user-guide/netx-events/image88.png)

**Beskrivning**

Den här händelsen representerar att ange IP-adressen via nx_ip_address_set.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: IP-adress
- Informations fält 3: nätverks mask
- Info fält 4: används inte

### <a name="ip-create"></a>Skapa IP 

#### <a name="nx_ip_create"></a>nx_ip_create

**Ikonen** ![ I P skapa ikon](./media/user-guide/netx-events/image89.png)

**Beskrivning**

Den här händelsen representerar att skapa en IP-instans via nx_ip_create.

**Informations fält** 
- Info fält 1: pekar mot IP-instansen
- Info fält 2: IP-adress
- Informations fält 3: nätverks mask
- Info fält 4: standard pekare för Packet pool

### <a name="ip-delete"></a>Ta bort IP 

#### <a name="nx_ip_delete"></a>nx_ip_delete

**Ikonen** ![ I P ta bort-ikonen](./media/user-guide/netx-events/image90.png)

**Beskrivning**

Den här händelsen representerar borttagning av en IP-instans via nx_ip_delete.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="ip-driver-direct-command"></a>IP-drivrutin Direct-kommando 

#### <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

**Ikonen** ![ I P driv rutin Direct kommando ikon](./media/user-guide/netx-events/image91.png)

**Beskrivning**

Den här händelsen representerar ett direkt I/O-drivrutins kommando via nx_ip_driver_direct_command.

**Informations fält** 

- Info fält 1: pekar mot IP-instansen
- Info-fält 2: driv Rutins kommando
- Info-fält 3: retur värde
- Info fält 4: används inte

### <a name="ip-forwarding-disable"></a>Inaktivera IP-vidarebefordring 

#### <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

**Ikonen** ![ I P-ikonen inaktivera](./media/user-guide/netx-events/image92.png)

**Beskrivning**

Den här händelsen representerar inaktive ring av IP-vidarebefordring via nx_ip_forwarding_disable.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="ip-forwarding-enable"></a>Aktivera IP-vidarebefordring 

#### <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

**Ikonen** ![ Aktiverings ikon för I P P-vidarebefordring](./media/user-guide/netx-events/image93.png)

**Beskrivning**

Den här händelsen representerar aktivering av IP-vidarebefordring via nx_ip_forwarding_enable.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="ip-fragment-disable"></a>Inaktivera IP-fragment 

#### <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

**Ikonen** ![ I P fragment, inaktivera ikon](./media/user-guide/netx-events/image94.png)

**Beskrivning**

Den här händelsen representerar inaktive ring av IP-fragmentering via nx_ip_fragment_disable.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="ip-fragment-enable"></a>Aktivera IP-fragment 

#### <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

**Ikonen** ![ Ikon för att aktivera I f-fragment](./media/user-guide/netx-events/image95.png)

**Beskrivning**

Den här händelsen representerar aktivering av IP-fragment via nx_ip_fragment_enable.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="ip-gateway-address-set"></a>Adress uppsättning för IP-gateway 

#### <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

**Ikonen** ![ Ikonen I P Gateway-adress uppsättning](./media/user-guide/netx-events/image96.png)

**Beskrivning**

Den här händelsen representerar att ange IP-adressen för gatewayen via nx_ip_gateway_address_set.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: Gateway-IP-adress
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="ip-information-get"></a>Hämta IP-information 

#### <a name="nx_ip_info_get"></a>nx_ip_info_get

**Ikonen** ![ I P information get-ikonen](./media/user-guide/netx-events/image97.png)

**Beskrivning** Den här händelsen representerar hämtning av IP-information via nx_ip_info_get.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: skickade IP-byte
- Informations fält 3: mottagna IP-byte
- Info fält 4: ignorerade IP-paket

### <a name="ip-interface-attach"></a>Koppla IP-gränssnitt 

#### <a name="nx_interface_attach"></a>nx_interface_attach

**Ikonen** ![ Ikonen I P iterface-koppling](./media/user-guide/netx-events/image98.png)

**Beskrivning**

Den här händelsen representerar ett sekundärt nätverks gränssnitt som kopplas till IP-instansen via nx_ip_interface_attach.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: gränssnittets IP-adress
- Info-fält 3: index i IP-gränssnitts tabellen
- Info fält 4: används inte

### <a name="ip-interface-info-get"></a>Hämta information om IP-gränssnitt 

#### <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

**Ikonen** ![ Hämta ikon för IP-gränssnittets information](./media/user-guide/netx-events/image99.png)

**Beskrivning**

Den här händelsen representerar information som hämtats från det angivna nätverks gränssnittet via nx_ip_interface_info_get.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: gränssnittets IP-adress
- Info-fält 3: gränssnitts-MAC-MSB
- Info-fält 4: gränssnitts-MAC-lsb

### <a name="ip-raw-packet-disable"></a>Inaktivera IP RAW-paket 

#### <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

**Ikonen** ![ Ikonen inaktivera I RAW-paket](./media/user-guide/netx-events/image100.png)

**Beskrivning**

Den här händelsen representerar inaktive ring av kommunikation mellan rå IP-paket via nx_ip_raw_packet_disable.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="ip-raw-packet-enable"></a>Aktivera IP RAW-paket 

#### <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

**Ikonen** ![ Ikonen aktivera I RAW-paket](./media/user-guide/netx-events/image101.png)

**Beskrivning**

Den här händelsen representerar aktivering av rå IP-paketfiltrering via nx_ip_raw_packet_enable.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="ip-raw-packet-receive"></a>Ta emot IP RAW-paket 

#### <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

**Ikonen** ![ Ikonen för att ta emot RAW-paket](./media/user-guide/netx-events/image102.png)

**Beskrivning**

Den här händelsen representerar att ta emot ett RAW IP-paket via nx_ip_raw_packet_receive.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekar mot paket
- Informations fält 3: vänte alternativ
- Info fält 4: används inte

### <a name="ip-raw-packet-send"></a>Skicka IP RAW-paket 

#### <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

**Ikonen** ![ I P skicka ikon för RAW Packet-sändning](./media/user-guide/netx-events/image103.png)

**Beskrivning**

Den här händelsen representerar sändning av ett RAW IP-paket via nx_ip_raw_packet_send.

**Informations fält**

- Info fält 1: pekar mot IP-instansen
- Info fält 2: pekar mot paket
- Informations fält 3: målets IP-adress
- Info-fält 4: typ av tjänst

### <a name="ip-static-route-add"></a>IP-statisk väg Lägg till 

#### <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

**Ikonen** ![ I P statisk väg, Lägg till ikon](./media/user-guide/netx-events/image104.png)

**Beskrivning**

Den här händelsen representerar en statisk väg som läggs till i routningstabellen för IP-instansen via nx_ip_static_route_add.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: nätverks adress
- Informations fält 3: nätverks mask
- Info-fält 4: nästa hopp

### <a name="ip-static-route-delete"></a>Ta bort IP statisk väg 

#### <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

**Ikonen** ![ Ta bort-ikonen I P statisk Rute](./media/user-guide/netx-events/image105.png)

**Beskrivning**

Den här händelsen representerar en statisk väg som tas bort från routningstabellen för IP-instansen via nx_ip_static_route_delete.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: nätverks adress
- Informations fält 3: nätverks mask
- Info fält 4: används inte

### <a name="ip-status-check"></a>Kontroll av IP-status 

#### <a name="nx_ip_status_check"></a>nx_ip_status_check

**Ikonen** ![ Kontroll ikon för I P-status](./media/user-guide/netx-events/image106.png)

**Beskrivning**

Den här händelsen representerar att kontrol lera en IP-status via nx_ip_status_check.

Informations fält 

- Info fält 1: pekar mot IP-instansen
- Informations fält 2: begärd status
- Info-fält 3: faktisk status
- Info fält 4: vänte alternativ

### <a name="ipsec-enable"></a>Aktivera IPSEC 

#### <a name="nx_ipsec_enable"></a>nx_ipsec_enable

**Ikonen** ![ I P S E C Aktivera ikon](./media/user-guide/netx-events/image107.png)

**Beskrivning**

Den här händelsen representerar aktivering av IPSec-tjänster på den angivna IP-instansen via nx_ipsec_enable.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="packet-allocate"></a>Paket tilldelning 

#### <a name="nx_packet_allocate"></a>nx_packet_allocate

**Ikonen** ![ Ikon för paket tilldelning](./media/user-guide/netx-events/image108.png)

**Beskrivning**

Den här händelsen representerar att allokera ett paket via nx_packet_allocate.

**Informations fält**

- Info fält 1: pekar mot paketschemaläggaren
- Info fält 2: pekar på allokerat paket
- Informations fält 3: pakettyp
- Info fält 4: tillgängliga paket

### <a name="packet-copy"></a>Paket kopia 

#### <a name="nx_packet_copy"></a>nx_packet_copy

**Ikonen** ![ Ikon för paket CPY](./media/user-guide/netx-events/image109.png)

**Beskrivning**

Den här händelsen representerar kopiering av ett paket via nx_packet_copy.

**Informations fält**

- Informations fält 2: ny paket pekare
- Informations fält 3: pekare till Packet bassäng
- Info fält 4: vänte alternativ

### <a name="packet-data-append"></a>Lägg till paket data 

#### <a name="nx_packet_data_append"></a>nx_packet_data_append

**Ikonen** ![ Ikon för Lägg till paket data](./media/user-guide/netx-events/image110.png)

**Beskrivning**

Den här händelsen representerar att lägga till data i ett paket via nx_packet_data_append.

**Informations fält**

- Info fält 1: pekar mot paketet
- Info fält 2: pekare till data
- Informations fält 3: data storlek
- Info fält 4: pekar mot Packet bassäng

### <a name="packet-data-extract-offset"></a>Förskjutning av paket data extrahering 

#### <a name="nx_udp_source_extract_offset"></a>nx_udp_source_extract_offset

**Ikonen** ![ Förskjutnings ikon för extrahering av paket data](./media/user-guide/netx-events/image111.png)

**Beskrivning**

Den här händelsen representerar paket data som extraheras till en angiven buffert från ett paket via nx_udp_source_extract_offset.

**Informations fält**

- Info fält 1: pekar mot paket
- Informations fält 2: storleken på den angivna bufferten
- Informations fält 3: antal kopierade byte
- Info fält 4: används inte

### <a name="packet-data-retrieve"></a>Hämta paket data 

#### <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

**Ikonen** ![ Hämta ikon för paket data](./media/user-guide/netx-events/image112.png)

**Beskrivning**

Den här händelsen representerar hämtning av data från ett paket via nx_packet_data_retrieve.

**Informations fält** 

- Info fält 1: pekar mot paketet
- Informations fält 2: pekar till början av bufferten
- Informations fält 3: kopierade byte
- Info fält 4: används inte

### <a name="packet-length-get"></a>Hämta paket längd 

#### <a name="nx_packet_length_get"></a>nx_packet_length_get

**Ikonen** ![ Hämta ikon för paket längd](./media/user-guide/netx-events/image113.png)

**Beskrivning**

Den här händelsen representerar hämtning av längden på ett paket via nx_packet_length_get.

**Informations fält**

- Info fält 1: pekar mot paketet
- Informations fält 2: paket längd
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="packet-pool-create"></a>Skapa paket pool 

#### <a name="nx_packet_pool_create"></a>nx_packet_pool_create

**Ikonen** ![ Ikon för att skapa paket pool](./media/user-guide/netx-events/image114.png)

**Beskrivning**

Den här händelsen representerar skapandet av en adresspool via nx_packet_pool_create.

**Informations fält** 

- Info fält 1: pekar mot paketschemaläggaren
- Informations fält 2: paketets nytto Last storlek
- Informations fält 3: pekare till pool minnes område
- Info fält 4: storlek på poolens minnes område

### <a name="packet-pool-delete"></a>Ta bort paket pool 

#### <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

**Ikonen** ![ Ikon för borttagning av paket pool](./media/user-guide/netx-events/image115.png)

**Beskrivning**

Den här händelsen representerar borttagning av en modempool via nx_packet_pool_delete.

**Informations fält** 

- Info fält 1: pekar mot paketschemaläggaren
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

#### <a name="packet-pool-information-get"></a>Hämta paket bassängs information 

#### <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

**Ikonen** ![ Hämta ikon för paket Pools information](./media/user-guide/netx-events/image116.png)

**Beskrivning**

Den här händelsen representerar hämtning av paketets pool med information via nx_packet_pool_info_get.

**Informations fält**

- Info fält 1: pekare till Packet bassäng
- Informations fält 2: totalt antal paket
- Informations fält 3: tillgängliga paket
- Info fält 4: tomma begär Anden

### <a name="packet-release"></a>Paket version 

#### <a name="nx_packet_data_release"></a>nx_packet_data_release

**Ikonen** ![ Ikon för paket frigörelse](./media/user-guide/netx-events/image117.png)

**Beskrivning**

Den här händelsen representerar att släppa ett paket via nx_packet_release.

**Informations fält**

- Info fält 1: pekar mot paketet
- Informations fält 2: paket status
- Informations fält 3: tillgängliga paket
- Info fält 4: används inte

### <a name="packet-transmit-release"></a>Paket överförings version 

#### <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

**Ikonen** ![ Ikon för paket sändnings version](./media/user-guide/netx-events/image118.png)

**Beskrivning**

Den här händelsen representerar att släppa ett överförings paket via nx_packet_transmit_release.

**Informations fält**

- Info fält 1: pekar mot paketet
- Informations fält 2: paket status
- Informations fält 3: tillgängliga paket
- Info fält 4: används inte

### <a name="rarp-disable"></a>Inaktivera RARP 

#### <a name="nx_rarp_disable"></a>nx_rarp_disable

**Ikonen** ![ R A R P inaktivera ikon](./media/user-guide/netx-events/image119.png)

**Beskrivning**

Den här händelsen representerar inaktive ring av RARP via nx_rarp_disable.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="rarp-enable"></a>Aktivera RARP 

#### <a name="nx_rarp_enable"></a>nx_rarp_enable

**Ikonen** ![ R A R P Aktivera ikon](./media/user-guide/netx-events/image120.png)

**Beskrivning**

Den här händelsen representerar aktivering av RARP via nx_rarp_enable.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="rarp-information-get"></a>RARP information get 

#### <a name="nx_rarp_info_get"></a>nx_rarp_info_get

**Ikonen** ![ R A R P P-ikonen Hämta information](./media/user-guide/netx-events/image121.png)

**Beskrivning**

Den här händelsen representerar att hämta RARP-information via nx_rarp_info_get.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: begär Anden som skickats
- Informations fält 3: svar mottagna
- Info-fält 4: ogiltiga svar

### <a name="system-initialize"></a>System initiering 

#### <a name="nx_system_initialize"></a>nx_system_initialize

**Ikonen** ![ Ikon för system initiering](./media/user-guide/netx-events/image122.png)

**Beskrivning**

Den här händelsen representerar initiering av NetX via nx_system_initialize.

**Informations fält**

- Informations fält 1: används inte
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="tcp-client-socket-bind"></a>TCP-klientens socket-bindning 

#### <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

**Ikonen** ![ Ikonen för T P client socket bind](./media/user-guide/netx-events/image123.png)

**Beskrivning**

Den här händelsen representerar bindning av en klient-socket till en port via nx_tcp_client_socket_bind.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: port begärd
- Info fält 4: vänte alternativ

### <a name="tcp-client-socket-connect"></a>TCP-klient-socket Connect 

#### <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

**Ikonen** ![ T C P P Connect-ikon för klient-socket](./media/user-guide/netx-events/image124.png)

**Beskrivning**

Den här händelsen representerar att skapa en klient anslutning via nx_tcp_client_socket_connect.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: serverns IP-adress
- Info fält 4: Server porten har begärts

### <a name="tcp-client-socket-port-get"></a>Hämta TCP-klientens socket-port 

#### <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

**Ikonen** ![ Ikonen Hämta ikon för T C P client socket](./media/user-guide/netx-events/image125.png)

**Beskrivning**

Den här händelsen representerar klientens socket port nummer via nx_tcp_client_socket_port_get.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: port nummer
- Info fält 4: används inte

### <a name="tcp-client-socket-unbind"></a>TCP-klientens socket-DataBind 

#### <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

**Ikonen** ![ Ikon för T C P P-bindning för klient-socket](./media/user-guide/netx-events/image126.png)

**Beskrivning**

Den här händelsen representerar en avbindning av porten som är kopplad till socketen via nx_tcp_client_socket_unbind.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="tcp-enable"></a>TCP-aktivering 

#### <a name="nx_tcp_enable"></a>nx_tcp_enable

**Ikonen** ![ Ikonen T C P Enable](./media/user-guide/netx-events/image127.png)

**Beskrivning**

Den här händelsen representerar aktivering av TCP via nx_tcp_enable.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

###  <a name="tcp-free-port-find-tcp-free-port-find"></a>Kostnads fri TCP-port hitta gratis TCP-port hitta 

#### <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

**Ikonen** ![ T CP-kostnads fri port hitta ikon](./media/user-guide/netx-events/image128.png)

**Beskrivning**

Den här händelsen motsvarar att hitta en kostnads fri TCP-port via nx_tcp_free_port_find.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Informations fält 2: startar Sök port nummer
- Info-fält 3: ledigt port nummer
- Info fält 4: används inte

###  <a name="tcp-infomation-get"></a>Hämta TCP-information 

#### <a name="nx_tcp_info_get"></a>nx_tcp_info_get

**Ikonen** ![ T C P information get-ikon](./media/user-guide/netx-events/image129.png)

**Beskrivning**

Den här händelsen representerar hämtning av TCP-information för den angivna IP-instansen via nx_tcp_info_get.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Informations fält 2: antal byte som skickats
- Informations fält 3: Antal mottagna byte
- Info fält 4: antal ogiltiga paket

###  <a name="tcp-server-socket-accept"></a>Acceptera TCP-serverns socket 

#### <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

**Ikonen** ![ Ikonen för T C P P-mottagning för Server uttag](./media/user-guide/netx-events/image130.png)

**Beskrivning**

Den här händelsen representerar konfigurationen av Server-socketen efter en aktiv anslutningsbegäran togs emot via nx_tcp_server_socket_accept.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: vänte alternativ
- Info-fält 4: socket State

###  <a name="tcp-server-socket-listen"></a>TCP server-socket Lyssna 

#### <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

**Ikonen** ![ T C P P lsten ikon för en server-socket](./media/user-guide/netx-events/image131.png)

**Beskrivning**

Den här händelsen representerar registrering av en lyssnande begäran och en server-socket för den angivna TCP-porten via nx_tcp_server_socket_listen.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Informations fält 2: TCP-portnummer
- Informations fält 3: pekare till Socket
- Informations fält 4: maximalt antal anslutningar som kan placeras i kö

###  <a name="tcp-server-socket-relisten"></a>TCP server socket relister 

#### <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

**Ikonen** ![ Ikon för T C P P relister för Server uttag](./media/user-guide/netx-events/image132.png)

**Beskrivning**

Den här händelsen representerar att registrera en annan server-socket för en befintlig lyssnande begäran på den angivna TCP-porten via nx_tcp_server_socket_relisten.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Informations fält 2: TCP-portnummer
- Informations fält 3: pekare till Socket
- Info-fält 4: socket State

###  <a name="tcp-server-socket-unaccept"></a>TCP-serverns socket accepteras inte 

#### <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

**Ikonen** ![ Ikon för att ta emot en ikon för T C P-nätuttag](./media/user-guide/netx-events/image133.png)

**Beskrivning**

Den här händelsen representerar borttagning av Server-socketen från associationen med porten som tar emot en tidigare passiv anslutning via nx_tcp_server_socket_unaccept.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: socket State
- Info fält 4: används inte

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a>TCP-server-socket avlistat TCP-serverns socket avlistar 

#### <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

**Ikonen** ![ Ikon för T C P P-avregistrering av Server-socket](./media/user-guide/netx-events/image134.png)

**Beskrivning**

Den här händelsen representerar borttagning av en tidigare lyssnar-begäran för den angivna TCP-porten via nx_tcp_server_socket_unlisten.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Informations fält 2: TCP-portnummer
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="tcp-socket-bytes-available"></a>Tillgängliga TCP-socket-byte 

#### <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

**Ikonen** ![ Ikon för T C P-socket-tillgängliga byte](./media/user-guide/netx-events/image135.png)

**Beskrivning**

Den här händelsen representerar antalet byte som för närvarande är tillgängliga på den angivna TCP-mottagande socketen via nx_tcp_socket_bytes_available.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Informations fält 2: pekare till TCP-socket
- Informations fält 3: byte mottagna på socketen
- Info fält 4: används inte

### <a name="tcp-socket-create"></a>Skapa TCP-socket 

#### <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

**Ikonen** ![ T C P uttag ikon för skapa](./media/user-guide/netx-events/image136.png)

**Beskrivning**

Den här händelsen representerar att skapa en TCP-socket via nx_tcp_socket_create.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: typ av tjänst
- Info fält 4: mottagnings fönster storlek

### <a name="tcp-socket-delete"></a>Ta bort TCP-socket 

#### <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

**Ikonen** ![ Ta bort ikon för T C P socket](./media/user-guide/netx-events/image137.png)

**Beskrivning**

Den här händelsen representerar borttagning av en socket via nx_tcp_socket_delete.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: socket State
- Info fält 4: används inte

### <a name="tcp-socket-disconnect"></a>Koppla från TCP-socket 

#### <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

**Ikonen** ![ Ikon för T C P uttag från koppling](./media/user-guide/netx-events/image138.png)

**Beskrivning**

Den här händelsen representerar att koppla från en socket via nx_tcp_socket_disconnect.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: vänte alternativ
- Info-fält 4: socket State

### <a name="tcp-socket-information-get"></a>Hämta TCP socket-information 

#### <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

**Ikonen** ![ T C P socket information get-ikon](./media/user-guide/netx-events/image139.png)

**Beskrivning**

Den här händelsen representerar hämtning av information om en socket via nx_tcp_socket_info_get.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: byte skickade via denna socket
- Info fält 4: byte mottagna via denna socket

### <a name="tcp-socket-mss-get"></a>TCP-socket-MSS Hämta 

#### <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

**Ikonen** ![ T C P Socket M S S get-ikon](./media/user-guide/netx-events/image140.png)

**Beskrivning**

Den här händelsen representerar socketens MSS via nx_tcp_socket_mss_get.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: maximal segment storlek (MSS)
- Info-fält 4: socket State

### <a name="tcp-socket-mss-peer-get"></a>TCP-socket MSS peer get 

#### <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

**Ikonen** ![ T C P Socket M S S peer get-ikon](./media/user-guide/netx-events/image141.png)

**Beskrivning**

Den här händelsen representerar MSS-värdet för socketens peer via nx_tcp_socket_mss_peer_get.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Info-fält 3: peer-MSS
- Info-fält 4: socket State

### <a name="tcp-socket-mss-set"></a>TCP-socket MSS-uppsättning 

#### <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

**Ikonen** ![ Ikon för T C P Socket M S S set](./media/user-guide/netx-events/image142.png)

**Beskrivning**

Den här händelsen representerar att ange en Sockets MSS via nx_tcp_socket_mss_set.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Info-fält 3: MSS
- Info-fält 4: socket State

### <a name="tcp-socket-peer-info-get"></a>Hämta peer-information för TCP-socket 

#### <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

**Ikonen** ![ Hämta ikon för T C P socket peer info](./media/user-guide/netx-events/image143.png)

**Beskrivning**

Den här händelsen representerar information som hämtats från TCP-socketen om peer-datorn (t. ex. >ansluter värd) IP-adress och port via nx_tcp_socket_peer_info_get.

**Informations fält**

- Informations fält 1: pekare till TCP-socket
- Informations fält 2: peer-IP-adress
- Informations fält 3: peer port nummer
- Info fält 4: används inte

### <a name="tcp-socket-receive"></a>Ta emot TCP-socket 

#### <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

**Ikonen** ![ Ikon för T C P socket Receive](./media/user-guide/netx-events/image144.png)

**Beskrivning**

Den här händelsen representerar mottagning av data från en socket via nx_tcp_socket_receive.

**Informations fält**

- Informations fält 1: pekare till Socket
- Info fält 2: pekare till mottaget paket
- Informations fält 3: mottaget paket längd
- Info fält 4: mottagnings ordnings nummer

### <a name="tcp-socket-receive-notify"></a>Mottagnings meddelande för TCP-socket 

#### <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

**Ikonen** ![ Ikonen för T C P socket Receive-avisering](./media/user-guide/netx-events/image145.png)

**Beskrivning**

Den här händelsen representerar registrering av ett mottagnings återanrop för en socket via nx_tcp_socket_receive_notify.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: pekare för att ta emot meddelande om återanrops information 4: används inte

### <a name="tcp-socket-send"></a>Skicka TCP-socket 

#### <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

**Ikonen** ![ T C P socket-sändning, ikon](./media/user-guide/netx-events/image146.png)

**Beskrivning**

Den här händelsen representerar sändning av data på en socket via nx_tcp_socket_send.

**Informations fält**

- Informations fält 1: pekare till Socket
- Info fält 2: pekar mot paket
- Informations fält 3: Paketets längd
- Info-fält 4: överförings ordnings nummer

### <a name="tcp-socket-state-wait"></a>Vänte läge för TCP-socket 

#### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

**Ikonen** ![ Vänta-ikon för T C P-insocket-tillstånd](./media/user-guide/netx-events/image147.png)

**Beskrivning**

Den här händelsen representerar väntan på att en socket ska ange ett visst tillstånd via nx_tcp_socket_state_wait.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Info-fält 3: önskat socket-tillstånd
- Info-fält 4: tidigare socket-tillstånd

### <a name="tcp-socket-transmit-configure"></a>Konfigurera TCP socket-överföring 

#### <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

**Ikonen** ![ Konfigurations ikon för T C P socket-överföring](./media/user-guide/netx-events/image148.png)

**Beskrivning**

Den här händelsen representerar konfigurering av överförings alternativ för en socket via nx_tcp_socket_transmit_configure.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: överförings köns djup
- Info-fält 4: tids gräns värde

### <a name="tcp-socket-window-update-notify-set"></a>Meddelande uppsättning för uppdatering av TCP-socket-fönstret 

#### <a name="nx_tcp_window_update_notify_set"></a>nx_tcp_window_update_notify_set

**Ikonen** ![ Ikon för att uppdatera aviserings uppsättning i T C P socket Window](./media/user-guide/netx-events/image149.png)

**Beskrivning**

Den här händelsen representerar en TCP-socket som tar emot meddelanden om en ökning i fönstret för att ta emot fjärrvärdar via nx_tcp_window_update_notify_set.

**Informations fält** 

- Informations fält 1: pekare till TCP-socket
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="udp-enable"></a>Aktivera UDP 

#### <a name="nx_udp_enable"></a>nx_udp_enable

**Ikonen** ![ U D P Enable-ikon](./media/user-guide/netx-events/image150.png)

**Beskrivning**

Den här händelsen representerar aktivering av UDP via nx_udp_enable.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="udp-free-port-find"></a>Kostnads fri UDP-port hitta 

#### <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

**Ikonen** ![ U D P kostnads fri port hitta ikon](./media/user-guide/netx-events/image151.png)

**Beskrivning**

Den här händelsen motsvarar att hitta en kostnads fri UDP-port via nx_udp_free_port_find.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Informations fält 2: startar porten för sökning från
- Info-fält 3: ledig port
- Info fält 4: används inte

### <a name="udp-information-get"></a>Hämta UDP-information 

#### <a name="nx_udp_info_get"></a>nx_udp_info_get

**Ikonen** ![ U D P information get-ikon](./media/user-guide/netx-events/image152.png)

**Beskrivning**

Den här händelsen representerar att hämta information via nx_udp_info_get.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Informations fält 2: skickade UDP-byte
- Informations fält 3: mottagna UDP-byte
- Info-fält 4: ogiltiga paket

### <a name="udp-socket-bind"></a>UDP-socket-bindning 

#### <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

**Ikonen** ![ U D P v socket bind-ikon](./media/user-guide/netx-events/image153.png)

**Beskrivning**

Den här händelsen representerar bindning av en UDP-socket till en port via nx_udp_socket_bind.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: port nummer
- Info fält 4: vänte alternativ

### <a name="udp-socket-bytes-available"></a>Tillgängliga UDP-socket-byte 

#### <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

**Ikonen** ![ Ikon för U D P socket-tillgängliga byte](./media/user-guide/netx-events/image154.png)

**Beskrivning**

Den här händelsen representerar det aktuella antalet byte som tagits emot på UDP-socketen via nx_udp_socket_bytes_available.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: byte mottagna på socket
- Info fält 4: används inte

### <a name="udp-socket-checksum-disable"></a>Inaktivera kontroll summa för UDP-socket 

#### <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

**Ikonen** ![ Inaktivera ikon för U D P socket-kontrollsumma](./media/user-guide/netx-events/image155.png)

**Beskrivning**

Den här händelsen representerar inaktive ring av kontroll summan för data på en UDP-socket via nx_udp_socket_checksum_disable.

**Informations fält** 

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="udp-socket-checksum-enable"></a>Aktivera kontroll summa för UDP-uttag 

#### <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

**Ikonen** ![ Ikon för U D P-uttag för kontroll Summa](./media/user-guide/netx-events/image156.png)

**Beskrivning**

Den här händelsen representerar aktivering av kontroll Summa bearbetning på en socket via nx_udp_socket_checksum_enable.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="udp-socket-create"></a>Skapa UDP-socket 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Ikonen** ![ U D P uttag ikon för skapa](./media/user-guide/netx-events/image157.png)

**Beskrivning**

Den här händelsen representerar att skapa en UDP-socket via nx_udp_socket_create.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: typ av tjänst
- Info-fält 4: Max mottagnings kön

### <a name="udp-socket-delete-event"></a>Ta bort händelse för UDP-socket 

#### <a name="nx_udp_socket_delete-event"></a>nx_udp_socket_delete händelse

**Ikonen** ![ U D P socket ta bort händelse ikon](./media/user-guide/netx-events/image158.png)

**Beskrivning**

Den här händelsen representerar borttagning av en UDP-socket via nx_udp_socket_delete.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="udp-socket-information-get-event"></a>UDP socket information get-händelse 

#### <a name="nx_udp_socket_info_get-event"></a>nx_udp_socket_info_get händelse

**Ikonen** ![ U D P l socket information Hämta händelse ikon](./media/user-guide/netx-events/image159.png)

**Beskrivning**

Den här händelsen representerar hämtning av information om en UDP-socket via nx_udp_socket_info_get.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: byte som skickats via socket
- Info fält 4: byte mottagna via socket

### <a name="udp-socket-interface-set"></a>Gränssnitts uppsättning för UDP-socket 

#### <a name="nx_udp_socket_interface_set-event"></a>nx_udp_socket_interface_set händelse

**Ikonen** ![ Ikonen U D P socket interface set](./media/user-guide/netx-events/image160.png)

**Beskrivning**

Den här händelsen representerar inställningen utgående gränssnitt för den angivna UDP-socketen med det angivna gränssnittet via nx_udp_socket_interface_set.

**Informations fält**

- Info fält 1: pekare till UDP-socket
- Info fält 2: index som motsvarar gränssnittet för socketen
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="udp-socket-port-get"></a>Hämta UDP-socket port 

#### <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

**Ikonen** ![ U D P socket port get-ikon](./media/user-guide/netx-events/image161.png)

**Beskrivning**

Den här händelsen representerar hämtning av UDP-porten som den angivna UDP-socketen är kopplad till via nx_udp_socket_port_get.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till UDP-socket
- Informations fält 3: port nummer
- Info fält 4: används inte

### <a name="udp-socket-receive"></a>Ta emot UDP-socket 

#### <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

**Ikonen** ![ U D P socket Receive-ikon](./media/user-guide/netx-events/image162.png)

**Beskrivning**

Den här händelsen representerar mottagning av data på angiven UDP-socket via nx_udp_socket_receive.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till UDP-socket
- Informations fält 3: pekare till mottaget paket
- Info fält 4: mottaget paket storlek

### <a name="udp-socket-receive-notify"></a>Mottagnings meddelande för UDP-socket 

#### <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

**Ikonen** ![ Beskrivning av U D P socket Receive-ikonen ](./media/user-guide/netx-events/image163.png) 

Den här händelsen representerar registrering av mottagnings återanrop via nx_udp_socket_receive_notify.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: pekare för att ta emot meddelande funktions information fält 4: används inte

### <a name="udp-socket-send"></a>Skicka UDP-socket 

#### <a name="nx_udp_socket_send"></a>nx_udp_socket_send

**Ikonen** ![ U D P socket-skicka-ikon](./media/user-guide/netx-events/image164.png)

**Beskrivning**

Den här händelsen representerar sändning av data via en UDP-socket via nx_udp_socket_send.

**Informations fält**

- Informations fält 1: pekare till Socket
- Info fält 2: pekar mot paket
- Informations fält 3: paket längd
- Info-fält 4: målets IP-adress

### <a name="udp-socket-unbind"></a>UDP-socket-avbindning 

#### <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

**Ikonen** ![ U D P-uppbindning-ikon](./media/user-guide/netx-events/image165.png)

**Beskrivning**

Den här händelsen representerar en avbindning av en UDP-port med en socket via nx_udp_socket_unbind.

**Informations fält**

- Informations fält 1: pekare till IP-instans
- Info fält 2: pekare till Socket
- Informations fält 3: port nummer
- Info fält 4: används inte

### <a name="udp-source-extract"></a>Extrahering av UDP-källa 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Ikonen** ![ U D P P käll extraherings ikon](./media/user-guide/netx-events/image166.png)

**Beskrivning**

Den här händelsen representerar att hämta IP-adressen och port numret för ett mottaget UDP-paket via nx_udp_source_extract.

**Informations fält**

- Info fält 1: pekar mot paket
- Informations fält 2: avsändarens IP-adress
- Informations fält 3: avsändarens port nummer
- Info fält 4: används inte