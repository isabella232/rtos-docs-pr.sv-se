---
title: Kapitel 8 – Azure RTOS NetX-spårningshändelser
description: Det här kapitlet innehåller en beskrivning av Azure RTOS NetX-händelser.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: f785b421ffc6d588080eb45a50dad949daf1ca6a9bf36770110f0450cd465bf1
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116805293"
---
# <a name="chapter-8---azure-rtos-netx-trace-events"></a>Kapitel 8 – Azure RTOS NetX-spårningshändelser

Det här kapitlet innehåller en beskrivning av Azure RTOS NetX-händelser. 

## <a name="list-of-events-and-icons"></a>Lista över händelser och ikoner

Följande är en lista över NetX-händelser som visas av TraceX.

| Ikon                                           | Innebörd                 |
| -------------------------------- | ------------------------------------- |
| ![Ikon för intern mottagning av R P-begäran](./media/user-guide/netx-events/image1.png)    | Intern mottagning av ARP-begäran |
| ![Ikonen Skicka en intern R P-begäran](./media/user-guide/netx-events/image2.png)    | Skicka intern ARP-begäran |
| ![Ikon för intern R P-svars ta emot](./media/user-guide/netx-events/image3.png)    | Intern mottagning av ARP-svar |
| ![Ikonen Skicka internt R P-svar](./media/user-guide/netx-events/image4.png)    | Intern ARP-svarssändning |
| ![Ikon för intern IC M P-mottagning](./media/user-guide/netx-events/image5.png)    | Intern ICMP-mottagning |
| ![Ikonen Skicka internt I C M P](./media/user-guide/netx-events/image6.png)    | Internt ICMP-meddelande |
| ![Ikon för intern NetX I G M P-mottagning](./media/user-guide/netx-events/image7.png)    | Intern NetX IGMP-mottagning |
| ![Ikonen Intern I P-mottagning](./media/user-guide/netx-events/image8.png)    | Intern IP-mottagning |
| ![Ikonen Skicka internt I P](./media/user-guide/netx-events/image9.png)    | Internt IP-meddelande |
| ![Ikon för intern T C P-data tar emot](./media/user-guide/netx-events/image10.png)    | Intern TCP-data tar emot |
| ![Ikonen Skicka interna T C P-data](./media/user-guide/netx-events/image11.png)    | Intern TCP-datasänd |
| ![Ikon för intern T C P FIN-mottagning](./media/user-guide/netx-events/image12.png)    | Intern TCP FIN-mottagning |
| ![Ikonen Skicka internt T C P F I N](./media/user-guide/netx-events/image13.png)    | Internt TCP FIN-meddelande |
| ![Ikon för intern T C P R S T-mottagning](./media/user-guide/netx-events/image14.png)    | Intern TCP RST-mottagning |
| ![Ikonen Skicka internt T C P R S T](./media/user-guide/netx-events/image15.png)    | Internt TCP RST-meddelande |
| ![Ikon för intern T C P S Y N-mottagning](./media/user-guide/netx-events/image16.png)    | Intern TCP SYN-mottagning |
| ![Ikonen Skicka internt T C P S Y N](./media/user-guide/netx-events/image17.png)    | Internt TCP SYN-meddelande |
| ![Ikon för intern U D P-mottagning](./media/user-guide/netx-events/image18.png)    | Intern UDP-mottagning |
| ![Ikonen Skicka internt U D P](./media/user-guide/netx-events/image19.png)    | Intern UDP-skicka |
| ![Ikon för intern R A R P-mottagning](./media/user-guide/netx-events/image20.png)    | Intern RARP-mottagning |
| ![Ikonen Skicka internt R A R P](./media/user-guide/netx-events/image21.png)    | Internt RARP-meddelande |
| ![Ikon för internt T C P-återförsök](./media/user-guide/netx-events/image22.png)    | Internt TCP-återförsök |
| ![Ikon för ändring av internt T C P-tillstånd](./media/user-guide/netx-events/image23.png)    | Ändring av internt TCP-tillstånd |
| ![Ikonen Skicka internt I/O-drivrutinspaket](./media/user-guide/netx-events/image24.png)    | Skicka internt I/O-drivrutinspaket |
| ![storleken på](./media/user-guide/netx-events/image25.png)    | Initiera intern I/O-drivrutin |
| ![Initieringsikon för intern I/O-drivrutin](./media/user-guide/netx-events/image26.png)    | Aktivera intern I/O-drivrutinslänk |
| ![Ikon för inaktiverad intern I/O-drivrutinslänk](./media/user-guide/netx-events/image27.png)    | Inaktivera intern I/O-drivrutinslänk |
| ![Ikon för sändning av internt I/O-drivrutinspaket](./media/user-guide/netx-events/image28.png)    | Sändning av interna I/O-drivrutinspaket |
| ![Ikonen Skicka internt I/O-drivrutin för ARP](./media/user-guide/netx-events/image29.png)    | Intern ARP-skickad I/O-drivrutin |
| ![Ikonen Skicka internt I/O-drivrutins-ARP-svar](./media/user-guide/netx-events/image30.png)    | Internt ARP-svarssvar för I/O-drivrutin |
| ![Rarp-skicka-ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image31.png)    | Internt RARP-meddelande för I/O-drivrutin |
| ![Multicast-kopplingsikon för intern I/O-drivrutin](./media/user-guide/netx-events/image32.png)    | Intern Multicast-koppling för I/O-drivrutin |
| ![Multicast-lämna-ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image33.png)    | Multicast-ledighet för intern I/O-drivrutin |
| ![Ikonen Hämta status för intern I/O-drivrutin](./media/user-guide/netx-events/image34.png)    | Hämta status för intern I/O-drivrutin |
| ![Ikon för att hämta hastighet för intern I/O-drivrutin](./media/user-guide/netx-events/image35.png)    | Intern I/O-drivrutin – Hämta hastighet |
| ![Ikon för intern I/O-drivrutin: Hämta duplex-typ](./media/user-guide/netx-events/image36.png)    | Intern I/O-drivrutin– Hämta duplex-typ |
| ![Ikon för att hämta antal fel för intern I/O-drivrutin](./media/user-guide/netx-events/image37.png)    | Internt antal I/O-drivrutinsfel |
| ![Ikon för att hämta RX-antal interna I/O-drivrutiner](./media/user-guide/netx-events/image38.png)    | Intern I/O-drivrutin får RX-antal |
| ![Ikonen Hämta TX-antal för intern I/O-drivrutin](./media/user-guide/netx-events/image39.png)    | Intern I/O-drivrutin hämtar TX-antal |
| ![Ikon för att hämta allokeringsfel för intern I/O-drivrutin](./media/user-guide/netx-events/image40.png)    | Interna I/O-drivrutin får allokeringsfel |
| ![Ikon för avitiering av intern I/O-drivrutin](./media/user-guide/netx-events/image41.png)    | Avitiera intern I/O-drivrutin |
| ![Ikon för uppskjuten bearbetning av intern I/O-drivrutin](./media/user-guide/netx-events/image42.png)    | Intern I/O-drivrutin för uppskjuten bearbetning |
| ![Ikonen Ogiltiga R P dynamiska poster](./media/user-guide/netx-events/image43.png)    | **Dynamiska ARP-poster ogiltigförklaras** (*nx_arp_dynamic_entries_invalidate*) |
| ![Ikon för dynamisk postuppsättning för R P](./media/user-guide/netx-events/image44.png)    | **Dynamisk postuppsättning för ARP** (*nx_arp_dynamic_entry_set*) |
| ![En aktivera R P-ikon](./media/user-guide/netx-events/image45.png)    | **ARP Enable** (*nx_arp_enable*) |
| ![En R P Gratuitous Send-ikon](./media/user-guide/netx-events/image46.png)    | **ARP Gratuitous Send** (*nx_arp_gratuitous_send*) |
| ![En R P-ikon för att hitta maskinvaruadress](./media/user-guide/netx-events/image47.png)    | **ARP Hardware Address Find** (*nx_arp_hardware_address_find*) |
| ![Ikonen Hämta R P-information](./media/user-guide/netx-events/image48.png)    | **ARP Information Get** (*nx_arp_info_get*) |
| ![Ikonen Hitta EN R P IP-adress](./media/user-guide/netx-events/image49.png)    | **ARP IP-adress find** (*nx_arp_ip_address_find*) |
| ![En R P-ikon för att skapa statisk post](./media/user-guide/netx-events/image50.png)    | **ARP Static Entry Create** (*nx_arp_static_entry_create*) |
| ![Ikonen Ta bort statiska R P-poster](./media/user-guide/netx-events/image51.png)    | **Ta bort statiska ARP-poster** (*nx_arp_static_entries_delete*) |
| ![Ikonen Ta bort statisk post för R P](./media/user-guide/netx-events/image52.png)    | **Ta bort statisk ARP-post** (*nx_arp_static_entry_delete*) |
| ![Ikonen Ta bort post i Duo-cache](./media/user-guide/netx-events/image53.png)    | **Ta bort cachepost i Duo** (*nxd_nd_cache_entry_delete*) |
| ![Ikon för Duo Cache Entry Set](./media/user-guide/netx-events/image54.png)    | **Postuppsättning för Duo-cache** (*nxd_nd_cache_entry_set*) |
| ![Ikon för ogiltigt duo-cache](./media/user-guide/netx-events/image55.png)    | **Duo Cache Invalidate** (*nxd_nd_cache_invalidate*) |
| ![Ikonen Hitta IP-adress för Duo-cache](./media/user-guide/netx-events/image56.png)    | **Duo Cache IP Address Find** (*nxd_nd_cache_ip_address_find*) |
| ![Aktivera-ikonen för Duo I C M P](./media/user-guide/netx-events/image57.png)    | **Duo ICMP Enable** (*nxd_icmp_enable*) |
| ![Pingikonen Duo I C M P I P v 6](./media/user-guide/netx-events/image58.png)    | **Duo ICMP IPv6 Ping** (*nxd_icmp_ping*) |
| ![Ikonen Hitta största nyttostorlek för Duo I P](./media/user-guide/netx-events/image59.png)    | **Duo IP Max Payload Size Find** (*nx_max_payload_size_find*) |
| ![Ikonen Skicka raw-paket i Duo I P](./media/user-guide/netx-events/image60.png)    | **Duo IP Raw Packet Send** *(nxd_ip_raw_packet_send)* |
| ![Ikonen Lägg till standardrouter för Duo I P v 6](./media/user-guide/netx-events/image61.png)    | **Duo IPv6 Default Router Add** (*nxd_ipv6_default_router_add*) |
| ![Ikonen Ta bort standardrouter för Duo I P v 6](./media/user-guide/netx-events/image62.png)    | **Ta bort IPv6-standardrouter** *(nxd_ipv6_default_router_delete)* |
| ![Aktivera-ikonen för Duo I P v 6](./media/user-guide/netx-events/image63.png)    | **Duo IPv6 Enable** (*nxd_ipv6_enable)* |
| ![Ikonen Hämta global adress för Duo I P v 6](./media/user-guide/netx-events/image64.png)    | **Duo IPv6 Global Address Get** (*nxd_ipv6_global_address_get*) |
| ![Ikon för global adressuppsättning för Duo I P v 6](./media/user-guide/netx-events/image65.png)    | **Duo IPv6 Global Address Set** (*nxd_ipv6_global_address_set*) |
| ![Ikonen Starta process för Duo I P v 6](./media/user-guide/netx-events/image66.png)    | **Duo IPv6 Initiate Process (** *nxd_ipv6_initiate_dad_process*) |
| ![Ikonen Hämta gränssnittsadress för Duo I P v 6](./media/user-guide/netx-events/image67.png)    | **Duo IPv6-gränssnittsadress get** (*nxd_ipv6_interface_address_get*) |
| ![Ikon för duo I P v 6-gränssnittsadressuppsättning](./media/user-guide/netx-events/image68.png)    | **Duo IPv6-gränssnittsadressuppsättning** (*nxd_ipv6_interface_address_set*) |
| ![Ikonen Hämta lokal adress för Duo I P v 6-länk](./media/user-guide/netx-events/image69.png)    | **Duo IPv6 Link Local Address Get** (*nxd_ipv6_linklocal_address_get*) |
| ![Ikon för duo I P v 6-länk för lokal adressuppsättning](./media/user-guide/netx-events/image70.png)    | **Duo IPv6 Link Local Address Set** (*nxd_ipv6_linklocal_address_set*) |
| ![Ikonen Skicka raw-paket i Duo I P v 6](./media/user-guide/netx-events/image71.png)    | **Duo IPv6 Raw Packet Send** (*nxd_ipv6_raw_packet_send)* |
| ![Hämta information om peer-information för duo T C P Socket](./media/user-guide/netx-events/image72.png)    | **Duo TCP Socket Peer Info Get** (*nxd_tcp_socket_peer_info_get*) |
| ![Ikon för Duo T C Socket Set Interface](./media/user-guide/netx-events/image73.png)    | **Duo TCP Socket Set Interface** *(nxd_tcp_socket_set_interface)* |
| ![Skicka-ikonen för Duo U D P Socket](./media/user-guide/netx-events/image74.png)    | **Duo UDP Socket Send** (*nxd_udp_socket_send*) |
| ![Ikon för Duo U D P Socket Set Interface](./media/user-guide/netx-events/image75.png)    | **Duo UDP Socket Set Interface** *(nxd_udp_socket_set_interface)* |
| ![Extraheringsikon för Duo U D P-källa](./media/user-guide/netx-events/image76.png)    | **UDP-källutdrag** *(nxd_udp_source_extract)* |
| ![Aktivera-ikonen för IC M P](./media/user-guide/netx-events/image77.png)    | **ICMP Enable** (*nx_icmp_enable*) |
| ![Hämta informationsikon för IC M P](./media/user-guide/netx-events/image78.png)    | **Hämta ICMP-information** (*nx_icmp_info_get*) |
| ![I C M P Ping-ikon](./media/user-guide/netx-events/image79.png)    | **ICMP Ping** (*nx_icmp_ping*) |
| ![Aktivera-ikonen för I M P](./media/user-guide/netx-events/image80.png)    | **IGMP Enable** (*nx_igmp_enable*) |
| ![I G M P Information Hämta-ikon](./media/user-guide/netx-events/image81.png)    | **Hämta IGMP-information** (*nx_igmp_info_get*) |
| ![Ikonen Inaktivera loopback för I M P](./media/user-guide/netx-events/image82.png)    | **IGMP Loopback Disable** (*nx_igmp_loopback_disable*) |
| ![I G M P Loopback Aktivera-ikon](./media/user-guide/netx-events/image83.png)    | **IGMP Loopback Enable** (*nx_igmp_loopback_enable*) |
| ![I G M P Multicast Join-ikon](./media/user-guide/netx-events/image84.png)    | **IGMP Multicast Join** (*nx_igmp_multicast_join*) |
| ![I G M P Multicast Leave-ikon](./media/user-guide/netx-events/image85.png)    | **IGMP Multicast Leave** (*nx_igmp_multicast_leave*) |
| ![I P-adressändringsikonen Meddela](./media/user-guide/netx-events/image86.png)    | **Meddela om IP-adressändring** (*nx_ip_address_change_notify*) |
| ![Ikonen Hämta IP-adress](./media/user-guide/netx-events/image87.png)    | **IP-adress get** (*nx_ip_address_get*) |
| ![Ikon för I P-adressuppsättning](./media/user-guide/netx-events/image88.png)    | **IP-adressuppsättning** (*nx_ip_address_set*) |
| ![Ikonen Skapa i P](./media/user-guide/netx-events/image89.png)    | **IP-skapa** (*nx_ip_create*) |
| ![Ikonen Ta bort i P](./media/user-guide/netx-events/image90.png)    | **IP-borttagning** (*nx_ip_delete*) |
| ![Kommandoikon för I P-drivrutinskommando](./media/user-guide/netx-events/image91.png)    | **Kommandot IP Driver Direct** (*nx_ip_driver_direct_command*) |
| ![Ikonen Inaktivera vidarebefordran av I P](./media/user-guide/netx-events/image92.png)    | **Inaktivera IP-vidarebefordran** (*nx_ip_forwarding_disable*) |
| ![Ikonen Aktivera för vidarebefordran av I P](./media/user-guide/netx-events/image93.png)    | **Aktivera IP-vidarebefordran** (*nx_ip_forwarding_enable*) |
| ![Ikonen Inaktivera fragment i I P](./media/user-guide/netx-events/image94.png)    | **Inaktivera IP-fragment** (*nx_ip_fragment_disable*) |
| ![Aktivera fragmentikon för I P](./media/user-guide/netx-events/image95.png)    | **Aktivera IP-fragment** (*nx_ip_fragment_enable*)  |
| ![Ikon för IP Gateway-adressuppsättning](./media/user-guide/netx-events/image96.png)    | **IP Gateway-adressuppsättning** (*nx_ip_gateway_address_set*) |
| ![Ikonen Hämta information för I P](./media/user-guide/netx-events/image97.png)    | **IP-information hämta** (*nx_ip_info_get*) |
| ![Ikonen Anslut I P-gränssnitt](./media/user-guide/netx-events/image98.png)    | **IP-gränssnitts attach** *(nx_ip_interface_attach)* |
| ![Ikonen Hämta information om I P-gränssnitt](./media/user-guide/netx-events/image99.png)    | **Information om IP-gränssnitt hämta** (*nx_ip_interface_info_get*) |
| ![Ikonen Inaktivera raw-paket](./media/user-guide/netx-events/image100.png)    | **Inaktivera IP-rådatapaket** (*nx_ip_raw_packet_disable*) |
| ![Ikonen Aktivera raw-paket](./media/user-guide/netx-events/image101.png)    | **Aktivera IP-rådatapaket** (*nx_ip_raw_packet_enable*) |
| ![Ikonen Ta emot raw-paket](./media/user-guide/netx-events/image102.png)    | **IP Raw Packet Receive** (*nx_ip_raw_packet_receive*) |
| ![Ikonen Skicka raw-paket](./media/user-guide/netx-events/image103.png)    | **IP Raw Packet Send** (*nx_ip_raw_packet_send*) |
| ![Lägg till ikon för statisk väg i I P](./media/user-guide/netx-events/image104.png)    | **Lägg till statisk IP-väg** (*nx_ip_static_route_add*) |
| ![Ikonen Ta bort statisk väg i I P](./media/user-guide/netx-events/image105.png)    | **Ta bort statisk IP-väg** *(nx_ip_static_route_delete)* |
| ![Ikon för I P-statuskontroll](./media/user-guide/netx-events/image106.png)    | **IP-statuskontroll** (*nx_ip_status_check*)|
| ![Aktivera-ikonen för I P S E C](./media/user-guide/netx-events/image107.png)    | **IPSEC-aktivera** (*nx_ipsec_enable)* |
| ![Ikonen Allokera paket](./media/user-guide/netx-events/image108.png)    | **Packet Allocate** (*nx_packet_allocate*) |
| ![Ikon för paketkopiering](./media/user-guide/netx-events/image109.png)    | **Paketkopia** (*nx_packet_copy*) |
| ![Ikon för tillägg av paketdata](./media/user-guide/netx-events/image110.png)    | **Tillägg av paketdata** (*nx_packet_data_append*) |
| ![Ikon för förskjutning av extrahering av paketdata](./media/user-guide/netx-events/image111.png)    | **Offset för paketdatautdrag** *(nx_packet_data_extract_offset)* |
| ![Ikonen Hämta paketdata](./media/user-guide/netx-events/image112.png)    | **Hämta paketdata** (*nx_packet_data_retrieve*) |
| ![Hämta ikon för paketlängd](./media/user-guide/netx-events/image113.png)    | **Hämta paketlängd** (*nx_packet_length_get*) |
| ![Ikonen Skapa paketpool](./media/user-guide/netx-events/image114.png)    | **Skapa paketpool** (*nx_packet_pool_create*) |
| ![Ikonen Ta bort paketpool](./media/user-guide/netx-events/image115.png)    | **Ta bort paketpool** (*nx_packet_pool_delete*) |
| ![Hämta ikon för information om paketpool](./media/user-guide/netx-events/image116.png)    | **Information om paketpool hämta** (*nx_packet_pool_info_get*) |
| ![Ikon för paketutgås](./media/user-guide/netx-events/image117.png)    | **Paketutgår** *( nx_packet_release*) |
| ![Ikon för lansering av paket överföring](./media/user-guide/netx-events/image118.png)    | **Paket överföring release** (*nx_packet_transmit_release*) |
| ![Ikonen Inaktivera R A R P](./media/user-guide/netx-events/image119.png)    | **INAKTIVERA RARP** (*nx_rarp_disable*) |
| ![Aktivera R A R P-ikon](./media/user-guide/netx-events/image120.png)    | **RARP Enable** (*nx_rarp_enable*) |
| ![Ikonen Hämta R A R P-information](./media/user-guide/netx-events/image121.png)    | **RARP Information Get** (*nx_rarp_info_get*) |
| ![Ikonen System initialize (System initialisering)](./media/user-guide/netx-events/image122.png)    | **System initialize** (*nx_system_initialize*) |
| ![Ikon för T C P-klientsocketbindning](./media/user-guide/netx-events/image123.png)    | **TCP-klientsocketbindning** *(nx_tcp_client_socket_bind*) |
| ![T C P Client Socket Anslut-ikon](./media/user-guide/netx-events/image124.png)    | **TCP Client Socket Anslut** (*nx_tcp_client_socket_connect*) |
| ![Ikonen Hämta klientsocketport för T C P](./media/user-guide/netx-events/image125.png)    | **HÄMTA TCP-klientsocketport** (*nx_tcp_client_socket_port_get*) |
| ![Ta bort bindningsikon för T C P-klientsocket](./media/user-guide/netx-events/image126.png)    | **TCP Client Socket Unbind** (*nx_tcp_client_socket_unbind*) |
| ![Aktivera-ikonen för T C P](./media/user-guide/netx-events/image127.png)    | **TCP-aktivera** (*nx_tcp_enable*) |
| ![Ikonen Hitta den kostnadsfria porten t C P](./media/user-guide/netx-events/image128.png)    | **Hitta den kostnadsfria TCP-porten** (*nx_tcp_free_port_find*) |
| ![Hämta informationsikon för T C P](./media/user-guide/netx-events/image129.png)    | **TCP Information Get** (*nx_tcp_info_get*) |
| ![Ikonen Acceptera t C P-serversocket](./media/user-guide/netx-events/image130.png)    | **TCP Server Socket Accept** (*nx_tcp_server_socket_accept*) |
| ![Lyssnarikon för T C P Server Socket](./media/user-guide/netx-events/image131.png)    | **TCP Server Socket Listen** (*nx_tcp_server_socket_listen*) |
| ![Ikon för återlistning av T C P-serversocket](./media/user-guide/netx-events/image132.png)    | **TCP Server Socket Relisten** (*nx_tcp_server_socket_relisten*) |
| ![Unaccept-ikon för T C P-serversocket](./media/user-guide/netx-events/image133.png)    | **TCP Server Socket Unaccept** (*nx_tcp_server_socket_unaccept*) |
| ![Ikon för avlistning av T C P-serversocket](./media/user-guide/netx-events/image134.png)    | **TCP Server Socket Unlisten** (*nx_tcp_server_socket_unlisten*) |
| ![Ikon för tillgängliga T C P Socket-byte](./media/user-guide/netx-events/image135.png)    | **Tillgängliga TCP-socketbyte** *(nx_tcp_socket_bytes_available*) |
| ![Ikonen Skapa t C P Socket](./media/user-guide/netx-events/image136.png)    | **TCP Socket Create** (*nx_tcp_socket_create*) |
| ![Borttagningsikon för T C P Socket](./media/user-guide/netx-events/image137.png)    | **TCP Socket Delete** (*nx_tcp_socket_delete*) |
| ![Frånkopplingsikon för T C P Socket](./media/user-guide/netx-events/image138.png)    | **TCP Socket Disconnect** (*nx_tcp_socket_disconnect*) |
| ![Ikonen Hämta information om T C P Socket](./media/user-guide/netx-events/image139.png)    | **TCP Socket Information Get** (*nx_tcp_socket_info_get*) |
| ![Hämta T C P Socket MSS-ikon](./media/user-guide/netx-events/image140.png)    | **TCP Socket MSS Get** (*nx_tcp_socket_mss_get*) |
| ![T C P Socket MSS Peer Hämta-ikon](./media/user-guide/netx-events/image141.png)    | **TCP Socket MSS Peer Get** (*nx_tcp_socket_mss_peer_get*) |
| ![T C P Socket MSS Set-ikon](./media/user-guide/netx-events/image142.png)    | **TCP Socket MSS Set** (*nx_tcp_socket_mss_set*) |
| ![Hämta ikon för peer-information för T C P Socket](./media/user-guide/netx-events/image143.png)    | **Tcp Socket Peer Info Get** *(nx_tcp_socket_peer_info_get)* |
| ![Ta emot T C P Socket-ikon](./media/user-guide/netx-events/image144.png)    | **TCP Socket Receive** (*nx_tcp_socket_receive*) |
| ![Meddelandeikon för T C P Socket Receive](./media/user-guide/netx-events/image145.png)    | **Tcp Socket Receive Notify** (*nx_tcp_socket_receive_notify*) |
| ![Ikonen Skicka t C P Socket](./media/user-guide/netx-events/image146.png)    | **TCP Socket Send** (*nx_tcp_socket_send*) |
| ![Ikon för TC P Socket State Wait](./media/user-guide/netx-events/image147.png)    | **Tcp Socket State Wait** (*nx_tcp_socket_state_wait*) |
| ![Konfigurationsikon för överföring av T C P Socket](./media/user-guide/netx-events/image148.png)    | **Tcp Socket Transmit Configure** (*nx_tcp_socket_transmit_configure*) |
| ![Uppdateringsikon för T P Socket Window Update](./media/user-guide/netx-events/image149.png)    | **Tcp Socket Window Update Notify Set** (*nx_tcp_socket_window_update_notify_set*)  |
| ![Aktivera ikon för U D P](./media/user-guide/netx-events/image150.png)    | **UDP Enable** (*nx_udp_enable*) |
| ![Ikonen För att hitta kostnadsfri port i U D P](./media/user-guide/netx-events/image151.png)    | **UDP Free Port Find** (*nx_udp_free_port_find*) |
| ![Ikonen Hämta information för U D P](./media/user-guide/netx-events/image152.png)    | **UDP Information Get** (*nx_udp_info_get*) |
| ![Ikon för U D P Socket Bind](./media/user-guide/netx-events/image153.png)    | **UDP Socket Bind** *(nx_udp_socket_bind)* |
| ![Ikon för tillgängliga U D P Socket-byte](./media/user-guide/netx-events/image154.png)    | **UDP Socket Bytes Available** *(nx_udp_socket_bytes_available)* |
| ![Ikon för inaktiverad kontrollsumma för U D P Socket](./media/user-guide/netx-events/image155.png)    | **Inaktivera kontrollsumma för UDP-socket** (*nx_udp_socket_checksum_disable*) |
| ![Aktivera-ikonen för U D P Socket Checksum](./media/user-guide/netx-events/image156.png)    | **Aktivera kontrollsumma för UDP-socket** *(nx_udp_socket_checksum_enable)* |
| ![Ikonen Skapa U D P Socket](./media/user-guide/netx-events/image157.png)    | **UDP Socket Create** (*nx_udp_socket_create*) |
| ![Borttagningsikon för U D P Socket](./media/user-guide/netx-events/image158.png)    | **UDP Socket Delete** (*nx_udp_socket_delete*) |
| ![Ikonen Hämta information om U D Socket](./media/user-guide/netx-events/image159.png)    | **UDP Socket Information Get** (*nx_udp_socket_info_get*) |
| ![Ikon för U D P Socket Interface Set](./media/user-guide/netx-events/image160.png)    | **UDP Socket Interface Set** (*nx_udp_socket_interface_set*) |
| ![Ikonen Hämta port för U D P-socket](./media/user-guide/netx-events/image161.png)    | **UDP Socket Port Get** (*nx_udp_socket_port_get*) |
| ![Ikon för U D P Socket Receive](./media/user-guide/netx-events/image162.png)    | **UDP Socket Receive** (*nx_udp_socket_receive*) |
| ![Meddelandeikon för U D P Socket Receive](./media/user-guide/netx-events/image163.png)    | **UDP Socket Receive Notify** (*nx_udp_socket_receive_notify*) |
| ![Ikonen Skicka U D P Socket](./media/user-guide/netx-events/image164.png)    | **UDP Socket Send** (*nx_udp_socket_send*) |
| ![Ta bort bindningsikon för U D P Socket](./media/user-guide/netx-events/image165.png)    | **UDP Socket Unbind** (*nx_udp_socket_unbind*) |
| ![Ikon för extrahering av U D P-källa](./media/user-guide/netx-events/image166.png)    | **UDP-källutdrag** (*nx_udp_source_extract*) |

## <a name="event-descriptions"></a>Händelsebeskrivningar

Följande sidor beskriver NetX-spårningshändelserna.

### <a name="internal-arp-request-receive"></a>Intern mottagning av ARP-begäran 

#### <a name="internal-arp-request-receive"></a>Intern mottagning av ARP-begäran

**Ikon** ![ Ikonen för att ta emot interna ARP-förfrågningar](./media/user-guide/netx-events/image1.png)

**Beskrivning**

Den här händelsen representerar en intern mottagningshändelse för NetX ARP-begäran.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Käll-IP-adress
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Används inte

### <a name="internal-arp-request-send"></a>Skicka intern ARP-begäran 

#### <a name="internal-arp-request-send"></a>Skicka intern ARP-begäran

**Ikon** ![ Ikonen Skicka intern ARP-begäran](./media/user-guide/netx-events/image2.png)

**Beskrivning**

Den här händelsen representerar en intern skickad NetX ARP-begäran.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Mål-IP-adress
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Används inte

### <a name="internal-arp-response-receive"></a>Internt ARP-svar vid mottagning 

#### <a name="internal-arp-request-receive"></a>Intern mottagning av ARP-begäran

**Ikon** ![ Ikonen för att ta emot interna ARP-förfrågningar](./media/user-guide/netx-events/image3.png)

**Beskrivning**

Den här händelsen representerar en intern NetX ARP-svarshändelse för mottagning.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Käll-IP-adress
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Används inte

### <a name="internal-arp-response-send"></a>Internt ARP-svarssänd 

#### <a name="internal-arp-request-send"></a>Skicka intern ARP-begäran

**Ikon** ![ Ikonen Skicka intern ARP-begäran](./media/user-guide/netx-events/image4.png)

**Beskrivning**

Den här händelsen representerar en intern skickad NetX-svarshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Mål-IP-adress
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Används inte

### <a name="internal-icmp-receive"></a>Intern ICMP-mottagning 

#### <a name="internal-icmp-receive"></a>Intern ICMP-mottagning

**Ikon** ![ Ikon för intern IC M P-mottagning](./media/user-guide/netx-events/image5.png)

**Beskrivning**

Den här händelsen representerar en intern NetX ICMP-mottagningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Käll-IP-adress
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Ord 0 i ICMP-rubriken

### <a name="internal-icmp-send"></a>Internt ICMP-meddelande 

#### <a name="internal-icmp-send"></a>Internt ICMP-meddelande

**Ikon** ![ Ikonen För internt IC M P-meddelande](./media/user-guide/netx-events/image6.png)

**Beskrivning**

Den här händelsen representerar en intern NetX ICMP-skicka händelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Mål-IP-adress
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Ord 0 i ICMP-rubriken

### <a name="internal-igmp-receive"></a>Intern IGMP-mottagning 

#### <a name="internal-igmp-receive"></a>Intern IGMP-mottagning

**Ikon** ![ Ikon för intern I G M P-mottagning](./media/user-guide/netx-events/image7.png)

**Beskrivning**

Den här händelsen representerar en intern NetX IGMP-mottagningshändelse.

**Informationsfält**

- Informationsfält 1: IP-pekare
- Informationsfält 2: Käll-IP-adress
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Ord 0 i IGMP-rubriken

### <a name="internal-ip-receive"></a>Intern IP-mottagning 

#### <a name="internal-ip-receive"></a>Intern IP-mottagning

**Ikon** ![ Ikon för intern I P-mottagning](./media/user-guide/netx-events/image8.png)

**Beskrivning**

Den här händelsen representerar en intern NetX IP-mottagningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Käll-IP-adress
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Paketlängd

### <a name="internal-ip-send"></a>Internt IP-meddelande

#### <a name="internal-ip-send"></a>Intern IP-skicka

**Ikon** ![ Ikonen Skicka internt I P](./media/user-guide/netx-events/image9.png)

**Beskrivning**

Den här händelsen representerar en intern NetX IP-skicka händelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Mål-IP-adress
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Paketlängd

### <a name="internal-tcp-data-receive"></a>Intern TCP-data tar emot 

#### <a name="internal-tcp-data-receive"></a>Intern TCP-data tar emot

**Ikon** ![ Ikon för intern T C P-data tar emot](./media/user-guide/netx-events/image10.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP-data tar emot händelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Käll-IP-adress
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Ta emot sekvensnummer

### <a name="internal-tcp-data-send"></a>Intern TCP-datasändning 

#### <a name="internal-tcp-data-send"></a>Intern TCP-datasänding

**Ikon** ![ Ikonen Skicka interna T C P-data](./media/user-guide/netx-events/image11.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP-datasänd händelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Överföringssekvensnummer

### <a name="internal-tcp-fin-receive"></a>Intern TCP FIN-mottagning 

#### <a name="internal-tcp-fin-receive"></a>Intern TCP-fin mottagning

**Ikon** ![ Ikon för intern T C P F F I N-mottagning](./media/user-guide/netx-events/image12.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP FIN-mottagningshändelse.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Ta emot sekvensnummer

### <a name="internal-tcp-fin-send"></a>Internt TCP FIN-meddelande 

#### <a name="internal-tcp-fin-send"></a>Internt TCP-finsänd

**Ikon** ![ Skicka ikon för intern T C P F I N](./media/user-guide/netx-events/image13.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP FIN-skicka-händelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Pekare till paket
- Informationsfält 4:Överföringssekvensnummer

### <a name="internal-tcp-rst-receive"></a>Intern TCP RST-mottagning 

#### <a name="internal-tcp-rst-receive"></a>Intern TCP RST-mottagning

**Ikon** ![ Ikon för intern T C P R S T-mottagning](./media/user-guide/netx-events/image14.png)

**Beskrivning**

Den här händelsen representerar en intern mottagningshändelse för NetX TCP-återställning.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen.
- Informationsfält 2: Pekare till socket.
- Informationsfält 3: Pekare till paket.
- Informationsfält 4: Ta emot sekvensnummer.

### <a name="internal-tcp-rst-send"></a>Internt TCP RST-meddelande 

#### <a name="internal-tcp-rst-send"></a>Internt TCP RST-meddelande

**Ikon** ![ Skicka ikon för intern T C P R S T](./media/user-guide/netx-events/image15.png)

**Beskrivning**

Den här händelsen representerar en intern send-händelse för NetX TCP-återställning.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Överföringssekvensnummer

### <a name="internal-tcp-syn-receive"></a>Intern TCP SYN-mottagning 

#### <a name="internal-tcp-syn-receive"></a>Intern TCP SYN-mottagning

**Ikon** ![ Ikon för intern T C P S Y N-mottagning](./media/user-guide/netx-events/image16.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP SYN-mottagningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Ta emot sekvensnummer

### <a name="internal-tcp-syn-send"></a>Internt TCP SYN-meddelande 

#### <a name="internal-tcp-syn-send"></a>Internt TCP SYN-meddelande

**Ikon** ![ Skicka ikon för intern T C P S Y N](./media/user-guide/netx-events/image17.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP SYN-skicka-händelse.

Informationsfält 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Pekare till paket -Info Fält 4: Överföringssekvensnummer

### <a name="internal-udp-receive"></a>Intern UDP-mottagning 

#### <a name="internal-udp-receive"></a>Intern UDP-mottagning

**Ikon** ![ Intern U D P-mottagningsikon](./media/user-guide/netx-events/image18.png)

**Beskrivning**

Den här händelsen representerar en intern NetX UDP-mottagningshändelse.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Ord 0 i UDP-rubrik

### <a name="internal-udp-send"></a>Internt UDP-skicka 

#### <a name="internal-udp-send"></a>Internt UDP-meddelande

**Ikon** ![ Ikonen Skicka intern U D P](./media/user-guide/netx-events/image19.png)

**Beskrivning**

Den här händelsen representerar en intern NetX UDP-skicka händelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Ord 0 i UDP-rubrik

### <a name="internal-rarp-receive"></a>Intern RARP-mottagning 

#### <a name="internal-rarp-receive"></a>Intern RARP-mottagning 

**Ikon** ![ Ikon för intern R A R P-mottagning](./media/user-guide/netx-events/image20.png)

**Beskrivning**

Den här händelsen representerar en intern NetX RARP-mottagningshändelse.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Mål-IP-adress
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Word 1 i RARP-rubriken

### <a name="internal-rarp-send"></a>Internt RARP-meddelande 

#### <a name="internal-rarp-send"></a>Internt RARP-meddelande 

**Ikon** ![ Ikonen Skicka intern R A R P](./media/user-guide/netx-events/image21.png)

**Beskrivning**

Den här händelsen representerar en intern NetX RARP-skicka-händelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Mål-IP-adress
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Word 1 i RARP-rubriken

### <a name="internal-tcp-retry"></a>Internt TCP-återförsök 

#### <a name="internal-tcp-retry"></a>Internt TCP-återförsök 

**Ikon** ![ Ikon för internt T C P-återförsök](./media/user-guide/netx-events/image22.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP-återförsökshändelse.

**Informationsfält**
- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Pekare till paket
- Informationsfält 4: Antal återförsök

### <a name="internal-tcp-state-change"></a>Ändring av internt TCP-tillstånd 

#### <a name="internal-tcp-state-change"></a>Ändring av internt TCP-tillstånd 

**Ikon** ![ Ikon för ändring av internt T C P-tillstånd](./media/user-guide/netx-events/image23.png)

**Beskrivning**

Den här händelsen representerar en intern ändringshändelse för NetX TCP-sockettillstånd.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Föregående tillstånd
- Informationsfält 4: Nytt tillstånd

### <a name="internal-io-driver-packet-send"></a>Skicka internt I/O-drivrutinspaket 

#### <a name="internal-io-driver-packet-send"></a>Skicka internt I/O-drivrutinspaket

**Ikon** ![ Ikonen Skicka internt I/O-drivrutinspaket](./media/user-guide/netx-events/image24.png)

**Beskrivning**

Den här händelsen representerar en intern skicka-händelse för NetX I/O-drivrutinspaket.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till paket
- Informationsfält 3: Paketstorlek
- Informationsfält 4: Används inte

### <a name="internal-io-driver-initialize"></a>Initiera intern I/O-drivrutin 

#### <a name="internal-io-driver-initialize"></a>Initiera intern I/O-drivrutin

**Ikon** ![ Initieringsikon för intern I/O-drivrutin](./media/user-guide/netx-events/image25.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin som initierar händelsen.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="internal-io-driver-link-enable"></a>Aktivera intern I/O-drivrutinslänk 

#### <a name="internal-io-driver-link-enable"></a>Aktivera intern I/O-drivrutinslänk

**Ikon** ![ Aktivera ikon för intern I/O-drivrutinslänk](./media/user-guide/netx-events/image26.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutinslänk för att aktivera händelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="internal-io-driver-link-disable"></a>Inaktivera intern I/O-drivrutinslänk 

#### <a name="internal-io-driver-link-disable"></a>Inaktivera intern I/O-drivrutinslänk

**Ikon** ![ Inaktiveringsikon för intern I/O-drivrutinslänk](./media/user-guide/netx-events/image27.png)

**Beskrivning**

Den här händelsen representerar en intern inaktiveringshändelse för NetX I/O-drivrutinslänken.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="internal-io-driver-packet-broadcast"></a>Sändning av interna I/O-drivrutinspaket 

#### <a name="internal-io-driver-packet-broadcast"></a>Sändning av interna I/O-drivrutinspaket

**Ikon** ![ Sändikon för internt I/O-drivrutinspaket](./media/user-guide/netx-events/image28.png)

**Beskrivning**

Den här händelsen representerar en intern sändningshändelse för NetX I/O-drivrutinspaket.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till paket
- Informationsfält 3: Paketstorlek
- Informationsfält 4: Används inte

### <a name="internal-io-driver-arp-send"></a>Internt I/O-drivrutins-ARP-meddelande 

#### <a name="internal-io-driver-arp-send"></a>Internt I/O-drivrutins-ARP-meddelande

**Ikon** ![ Skicka-ikon för intern I/O-drivrutin för ARP](./media/user-guide/netx-events/image29.png)

**Beskrivning**

Den här händelsen representerar en intern ARP-skickande händelse för NetX I/O-drivrutin.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till paket
- Informationsfält 3: Paketstorlek
- Informationsfält 4: Används inte

### <a name="internal-io-driver-arp-response-send"></a>Skicka internt ARP-svar för I/O-drivrutin 

#### <a name="internal-io-driver-arp-response-send"></a>Intern I/O-drivrutin för ARP-svarssändning

**Ikon** ![ Skicka-ikon för internt I/O-drivrutins-ARP-svar](./media/user-guide/netx-events/image30.png)

**Beskrivning**

Den här händelsen representerar en intern ARP-svarshändelse för NetX I/O-drivrutin.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till paket
- Informationsfält 3: Paketstorlek
- Informationsfält 4: Används inte

### <a name="internal-io-driver-rarp-send"></a>Internt RARP-meddelande för I/O-drivrutin 

#### <a name="internal-io-driver-rarp-send"></a>INTERNT RARP-meddelande för I/O-drivrutin

**Ikon** ![ Rarp-skicka-ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image31.png)

**Beskrivning**

Den här händelsen representerar en intern RARP-skickande händelse för NetX I/O-drivrutin.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till paket
- Informationsfält 3: Paketstorlek
- Informationsfält 4: Används inte

### <a name="internal-io-driver-multicast-join"></a>Intern multicast-koppling för I/O-drivrutin 

#### <a name="internal-io-driver-multicast-join"></a>Intern multicast-koppling för I/O-drivrutin

**Ikon** ![ Multicast-kopplingsikon för intern I/O-drivrutin](./media/user-guide/netx-events/image32.png)

**Beskrivning**

Den här händelsen representerar en intern multicast-kopplingshändelse för NetX I/O-drivrutinen.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="internal-io-driver-multicast-leave"></a>Multicast-ledighet för intern I/O-drivrutin 

#### <a name="internal-io-driver-multicast-leave"></a>Multicast-ledighet för intern I/O-drivrutin

**Ikon** ![ Multicast-lämna-ikon för intern I/O-drivrutin](./media/user-guide/netx-events/image33.png)

**Beskrivning**

Den här händelsen representerar en intern Multicast Leave-händelse för NetX I/O-drivrutinen.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="internal-io-driver-get-status"></a>Hämta status för intern I/O-drivrutin 

#### <a name="internal-io-driver-get-status"></a>Hämta status för intern I/O-drivrutin

**Ikon** ![ Ikon för att hämta status för intern I/O-drivrutin](./media/user-guide/netx-events/image34.png)

**Beskrivning**

Den här händelsen representerar en intern statushändelse för att hämta status för NetX I/O-drivrutinen.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="internal-io-driver-get-speed"></a>Intern I/O-drivrutin – Hämta hastighet 

#### <a name="internal-io-driver-get-speed"></a>Intern I/O-drivrutin får hastighet

**Ikon** ![ Ikon för att hämta hastighet för intern I/O-drivrutin](./media/user-guide/netx-events/image35.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin som kör en get speed-händelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="internal-io-driver-get-duplex-type"></a>Intern I/O-drivrutin : Get Duplex Type (Hämta duplex-typ) 

#### <a name="internal-io-driver-get-duplex-type"></a>Intern I/O-drivrutin får duplex-typ

**Ikon** ![ Ikon för intern I/O-drivrutin för att hämta duplex-typ](./media/user-guide/netx-events/image36.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin med en get duplex-typhändelse.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="internal-io-driver-get-error-count"></a>Internt antal I/O-drivrutinsfel

#### <a name="internal-io-driver-get-error-count"></a>Intern I/O-drivrutin får antal fel

**Ikon** ![ Ikon för internt I/O-drivrutin får antal fel](./media/user-guide/netx-events/image37.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin som får felantalshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="internal-io-driver-get-rx-count"></a>Intern I/O-drivrutin får RX-antal 

#### <a name="internal-io-driver-get-rx-count"></a>Intern I/O-drivrutin får RX-antal

**Ikon** ![ Ikon för internt I/O-drivrutin för att hämta RX-antal](./media/user-guide/netx-events/image38.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin som får RX-antal händelser.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="internal-io-driver-get-tx-count"></a>Intern I/O-drivrutin hämtar TX-antal 

#### <a name="internal-io-driver-get-tx-count"></a>Intern I/O-drivrutin får TX-antal

**Ikon** ![ Intern I/O-drivrutin får T X-antal-ikon](./media/user-guide/netx-events/image39.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin som hämtar TX-antal händelser.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="internal-io-driver-get-allocation-errors"></a>Interna I/O-drivrutin får allokeringsfel 

#### <a name="internal-io-driver-get-allocation-errors"></a>Intern I/O-drivrutin får allokeringsfel

**Ikon** ![ Ikon för internt I/O-drivrutin för att hämta allokeringsfel](./media/user-guide/netx-events/image40.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin som får allokeringsfel.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="internal-io-driver-un-initialize"></a>Avitiera intern I/O-drivrutin 

#### <a name="internal-io-driver-un-initialize"></a>Avitiering av intern I/O-drivrutin 

**Ikon** ![ Avitieringsikon för intern I/O-drivrutin](./media/user-guide/netx-events/image41.png)

**Beskrivning**

Den här händelsen representerar en intern I/O-drivrutin för NetX som avinitierar händelsen.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="internal-io-driver-deferred-processing"></a>Intern uppskjuten bearbetning av I/O-drivrutin 

#### <a name="internal-io-driver-deferred-processing"></a>Intern uppskjuten bearbetning av I/O-drivrutin 

**Ikon** ![ Ikon för uppskjuten bearbetning av intern I/O-drivrutin](./media/user-guide/netx-events/image42.png)

**Beskrivning**

Den här händelsen representerar en intern uppskjuten bearbetningshändelse i NetX I/O-drivrutinen.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till paket
- Informationsfält 3: Paketlängd
- Informationsfält 4: Används inte

### <a name="arp-dynamic-entries-invalidate"></a>Dynamiska ARP-poster ogiltigförklaras 

#### <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

**Ikon** ![ Ikonen Ogiltiga R P dynamiska poster](./media/user-guide/netx-events/image43.png)

**Beskrivning**

Den här händelsen representerar ogiltighet av alla dynamiska ARP-helheter via nx_arp_dynamic_entries_invalidate.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Poster ogiltigförklaras
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="arp-dynamic-entry-set"></a>Dynamisk ARP-postuppsättning 

#### <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

**Ikon** ![ Ikon för dynamisk postuppsättning för R P](./media/user-guide/netx-events/image44.png)

**Beskrivning**

Den här händelsen representerar inställning av en dynamisk ARP-post via nx_arp_dynamic_entry_set.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: IP-adress
- Informationsfält 3: Fysisk adress (MSW)
- Informationsfält 4: Fysisk adress (LSW)

### <a name="arp-enable"></a>Aktivera ARP 

#### <a name="nx_arp_enable"></a>nx_arp_enable

**Ikon** ![ En R P-aktivera-ikon](./media/user-guide/netx-events/image45.png)

**Beskrivning**

Den här händelsen representerar aktivering av ARP via nx_arp_enable.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Minnes pekare för ARP-cache
- Informationsfält 3: Minnesstorlek för ARP-cache
- Informationsfält 4: Används inte

### <a name="arp-gratuitous-send"></a>ARP Gratuitous Send 

#### <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

**Ikon** ![ En R P-ikon för att skicka utan att göra något](./media/user-guide/netx-events/image46.png)

**Beskrivning**

Den här händelsen representerar en överflödig ARP-skicka via nx_arp_gratuitous_send.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="arp-hardware-address-find"></a>Hitta ARP-maskinvaruadress 

#### <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

**Ikon** ![ Ikonen Hitta en R P-maskinvaruadress](./media/user-guide/netx-events/image47.png)

**Beskrivning**

Den här händelsen representerar att hitta en fysisk adress via nx_arp_hardware_address_find.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: IP-adress
- Informationsfält 3: Fysisk adress (MSW)
- Informationsfält 4: Fysisk adress (LSW)

### <a name="arp-information-get"></a>Hämta ARP-information 

#### <a name="nx_arp_info_get"></a>nx_arp_info_get

**Ikon** ![ Hämta en R P-informationsikon](./media/user-guide/netx-events/image48.png)

**Beskrivning**

Den här händelsen representerar att hämta information via nx_arp_info_get.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: ADE:er skickade
- Informationsfält 3: ARP-svar
- Informationsfält 4: Mottagna ADE:er

### <a name="arp-ip-address-find"></a>ARP IP-adress find 

#### <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

**Ikon** ![ Ikonen Hitta en R P I P-adress](./media/user-guide/netx-events/image49.png)

**Beskrivning**

Den här händelsen representerar att hitta en IP-adress som är associerad med den angivna fysiska adressen via nx_arp_ip_address_find.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: IP-adress
- Informationsfält 3: Fysisk adress (MSW)
- Informationsfält 4: Fysisk adress (LSW)

### <a name="arp-static-entry-create"></a>Skapa statisk ARP-post 

#### <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

**Ikon** ![ En ikon för att skapa en statisk R P-post](./media/user-guide/netx-events/image50.png)

**Beskrivning**

Den här händelsen representerar skapandet av en statisk ARP-post via nx_arp_static_entry_create.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: IP-adress
- Informationsfält 3: Fysisk adress (MSW)
- Informationsfält 4: Fysisk adress (LSW)

### <a name="arp-static-entries-delete"></a>Ta bort statiska ARP-poster 

#### <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

**Ikon** ![ Ikonen Ta bort statiska R P-poster](./media/user-guide/netx-events/image51.png)

**Beskrivning**

Den här händelsen representerar borttagning av alla statiska ARP-poster via nx_arp_static_entries_delete.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Borttagna poster
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="arp-static-entry-delete"></a>Ta bort statisk ARP-post 

### <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

**Ikon** ![ En borttagningsikon för statisk R P-post](./media/user-guide/netx-events/image52.png)

**Beskrivning**

Den här händelsen representerar borttagning av en statisk ARP-post via nx_arp_static_entry_delete.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: IP-adress
- Informationsfält 3: Fysisk adress (MSW)
- Informationsfält 4: Fysisk adress (LSW)

### <a name="duo-cache-entry-delete"></a>Ta bort duo-cachepost 

#### <a name="nxd_und_cache_entry_delete"></a>nxd_und_cache_entry_delete

**Ikon** ![ Borttagningsikon för Duo-cachepost](./media/user-guide/netx-events/image53.png)

**Beskrivning**

Den här händelsen representerar borttagning av en post i granncachen via nx_udp_socket_create.

**Informationsfält** 

- Informationsfält 1: Fjärde (minst signifikanta) ordet i den lokala IPv6-länkens adress som ska tas bort
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="duo-cache-entry-set"></a>Postuppsättning för Duo-cache 

#### <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set

**Ikon** ![ Ikon för att ange duo-cachepost](./media/user-guide/netx-events/image54.png)

**Beskrivning**

Den här händelsen representerar att skapa en cachepost och lägga till den angränsande cachetabellen via nxd_nd_cache_entry_set.

**Informationsfält** 

- Informationsfält 1: Fjärde (minst signifikanta) ordet i den IPv6-adress som ska läggas till
- Informationsfält 2: Fysisk adress msb
- Informationsfält 3: Fysisk adress lsb
- Informationsfält 4: Används inte

### <a name="duo-cache-invalidate"></a>Duo Cache Invalidate 

#### <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate

**Ikon** ![ Ikon för ogiltigt duo-cacheminne](./media/user-guide/netx-events/image55.png)

**Beskrivning**

Den här händelsen representerar att hela granncachens tabell ogiltigförklaras via nxd_nd_cache_invalidate.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="duo-cache-ip-address-find"></a>Duo Cache IP Address Find 

#### <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find

**Ikon** ![ Ikon för att hitta I P-adress för duo-cache](./media/user-guide/netx-events/image56.png)

**Beskrivning**

Den här händelsen representerar hämtning av en IP-adress som matchar den angivna fysiska adressen från cachetabellen via nxd_nd_cache_ip_address_find.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Fjärde (minst signifikanta) ordet i IPv6-adressen
- Informationsfält 3: Fysisk adress msb
- Informationsfält 4: Fysisk adress lsb

### <a name="duo-icmp-enable"></a>Aktivera Duo ICMP 

#### <a name="nxd_icmp_enable"></a>nxd_icmp_enable

**Ikon** ![ Aktivera ikon för Duo I C M P](./media/user-guide/netx-events/image57.png)

**Beskrivning**

Den här händelsen representerar ICMPv4- och ICMPv6-tjänster som aktiveras på den angivna IP-instansen via nxd_icmp_enable.

**Informationsfält**
- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="duo-icmp-ping"></a>Duo ICMP Ping 

#### <a name="nxd_icmp_ping"></a>nxd_icmp_ping

**Ikon** ![ Pingikonen Duo I C M P](./media/user-guide/netx-events/image58.png)

**Beskrivning**

Den här händelsen representerar sändning av ett ping (ekobegäran) till en IPv6-värd via nxd_icmp_ping.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: IPv6-adress
- Informationsfält 3: Pekare till ekodata
- Informationsfält 4: Storleken på ekodata

### <a name="duo-ip-max-payload-size-find"></a>Duo IP Max Payload Size Find 

#### <a name="nxd_ip_max_payload_size"></a>nxd_ip_max_payload_size

**Ikon** ![ Ikonen Hitta maximal nyttolaststorlek för Duo I P](./media/user-guide/netx-events/image59.png)

**Beskrivning**

Den här händelsen beräknar den maximala nyttolasten som det angivna paketet kan medföra utan fragmentering.

**Informationsfält**

- Informationsfält 1: Socket-pekare
- Informationsfält 2: Peer-IP-adress
- Informationsfält 3: Peer-port info fält 4: Används inte

### <a name="duo-ip-raw-packet-send"></a>Duo IP Raw Packet Send 

#### <a name="nxd_ip_max_packet_send"></a>nxd_ip_max_packet_send

**Ikon** ![ Ikonen Skicka raw-paket med Duo I P](./media/user-guide/netx-events/image60.png)

**Beskrivning**

Den här händelsen representerar sändning av ett rådata-IP-paket från det angivna nätverksgränssnittet till den angivna IP-måladressenvia nxd_ip_raw_packet_send.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till paket som ska skickas
- Informationsfält 3: Pekare till måladress
- Informationsfält 4: Paketprotokoll

### <a name="duo-ipv6-default-router-add"></a>Duo IPv6 Standard router Lägg till 

#### <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add

**Ikon** ![ Lägg till ikon för standardrouter med Duo I P v 6](./media/user-guide/netx-events/image61.png)

**Beskrivning**

Den här händelsen representerar tillägg av en standardrouter till IP-instansens IPv6-routningstabell via nxd_ipv6_default_router_add.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans.
- Informationsfält 2: Målnätverksadress.
- Informationsfält 3: Information om livslängd.
- Informationsfält 4: Används inte.

### <a name="duo-ipv6-default-router-delete"></a>Duo IPv6 standard router ta bort 

#### <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete

**Ikon** ![ Ikonen Ta bort standardrouter med Duo I P v 6](./media/user-guide/netx-events/image62.png)

**Beskrivning**

Den här händelsen representerar borttagning av en standardrouter från IP-instansens IPv6-routningstabell via nxd_ipv6_default_router_delete.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans.
- Informationsfält 2: Fjärde ordet (minst signifikant) för standardrouter-IPv6-adressen.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="duo-ipv6-enable"></a>Aktivera Duo IPv6 

#### <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable

**Ikon** ![ Aktivera duo I P v 6-ikon](./media/user-guide/netx-events/image63.png)

**Beskrivning**

Den här händelsen representerar aktivering av IPv6-tjänster på den angivna IP-instansen via nxd_ipv6_enable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="duo-ipv6-global-address-get"></a>Hämta global adress för Duo IPv6 

#### <a name="nxd_ipv6_global_address_get"></a>nxd_ipv6_global_address_get

**Ikon** ![ Ikonen Hämta global adress för Duo I P v 6](./media/user-guide/netx-events/image64.png)

**Beskrivning**

Den här händelsen representerar hämtning av den globala (primära) IP-adressen på IP-instansen som finns vid index 1 i ip-instansgränssnittstabellen via nxd_ipv6_global_address_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans.
- Informationsfält 2: Fjärde ordet (minst signifikant) för den globala adressen
- Informationsfält 3: IPv6-adressprefixets längd.
- Informationsfält 4: Indexera till IP-gränssnittstabell (1).

### <a name="duo-ipv6-global-address-set"></a>Duo IPv6 Global Address Set 

#### <a name="nxd_ipv6_global_address_set"></a>nxd_ipv6_global_address_set

**Ikon** ![ Ikon för global adressuppsättning för Duo I P v 6](./media/user-guide/netx-events/image65.png)

**Beskrivning**

Den här händelsen representerar inställningen av den globala (primära) IP-adressen på IP-instansen som finns vid index 1 i ip-instansgränssnittstabellen via nxd_ipv6_global_address_set.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Fjärde ordet (minst signifikant) för den globala adressen
- Informationsfält 3: IPv6-adressprefixlängd
- Informationsfält 4: Indexera till IP-gränssnittstabell (1)

### <a name="duo-ipv6-initiate-dad-process"></a>Duo IPv6 Initiate Dad Process 

#### <a name="nxd_ipv6_initiate_dad_process"></a>nxd_ipv6_initiate_dad_process

**Ikon** ![ Ikon för att starta process för Duo I P v 6](./media/user-guide/netx-events/image66.png)

**Beskrivning**

Den här händelsen representerar början av processen för dubblettadressidentifiering (ORDNAD) när IP-instansen tilldelas en lokal länk eller en IP-gränssnittsadress via nxd_ipv6_initiate_dad_process.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="duo-ipv6-interface-address-get"></a>Hämta duo IPv6-gränssnittsadress 

#### <a name="nxd_ipv6_interface_address_get"></a>nxd_ipv6_interface_address_get

**Ikon** ![ Hämta ikon för gränssnittsadress för Duo I P v 6](./media/user-guide/netx-events/image67.png)

**Beskrivning**

Den här händelsen representerar hämtning av IP-adressen och prefixet vid det angivna indexet till IP-instansens gränssnittsadresstabell via nxd_ipv6_interface_address_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Fjärde ordet (minst signifikant) för IPv6-adressen som ska returneras
- Informationsfält 4: Index för gränssnittet i gränssnittstabellen för IP-instansen

### <a name="duo-ipv6-interface-address-set"></a>Duo IPv6-gränssnittsadressuppsättning 

### <a name="nxd_ipv6_interface_address_set"></a>nxd_ipv6_interface_address_set

**Ikon** ![ Duo I P v 6-gränssnittsadresser et-ikon](./media/user-guide/netx-events/image68.png)

**Beskrivning**

Den här händelsen representerar inställning av IP-adressen och prefixet för det angivna indexet i IP-instansgränssnittets adresstabell. Tillåts inte på index noll (länka lokal adress) via nxd_ipv6_interface_address_set.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Fjärde ordet (minst signifikant) för IPv6-adressen som ska returneras
- Informationsfält 3: Prefixlängd
- Informationsfält 4: Index för gränssnittet i gränssnittstabellen för IP-instansen

### <a name="duo-ipv6-link-local-address-get"></a>Hämta lokal adress för IPv6-länk i Duo 

#### <a name="nxd_ipv6_linklocal_address_get"></a>nxd_ipv6_linklocal_address_get

**Ikon** ![ Ikonen Hämta lokal adress för Duo I P v 6-länk](./media/user-guide/netx-events/image69.png)

**Beskrivning**

Den här händelsen representerar hämtning av den lokala länkadressen för den angivna IP-instansen via nxd_ipv6_linklocal_address_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Fjärde ordet (minst signifikant) för den lokala IP v6-länkens adress
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="duo-ipv6-link-local-address-set"></a>Duo IPv6 Link Lokal adressuppsättning 

#### <a name="nxd_ipv6_linklocal_address_set"></a>nxd_ipv6_linklocal_address_set

**Ikon** ![ Duo I P v 6-länk ikon för lokal adressuppsättning](./media/user-guide/netx-events/image70.png)

**Beskrivning**

Den här händelsen representerar inställningen av ip-instansens länk lokala adress via nxd_ipv6_linklocal_address_set.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Fjärde (minst signifikanta) ordet i den lokala IPv6-länkens adress
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="duo-ipv6-raw-packet-send"></a>Skicka Duo IPv6-rådatapaket 

#### <a name="nxd_ipv6_raw_packet_send"></a>nxd_ipv6_raw_packet_send

**Ikon** ![ Skicka obearbetat paket i Duo I P v 6](./media/user-guide/netx-events/image71.png)

**Beskrivning**

Den här händelsen representerar sändning av ett rå IP-paket via det primära IP-gränssnittet till det speficierade målet via nxd_ip_raw_packet_send.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till paket som ska skickas
- Informationsfält 3: Mål-IP-adress
- Informationsfält 4: Används inte

### <a name="duo-tcp-socket-peer-info-get"></a>Hämta information om DUO TCP Socket-peer 

#### <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get

**Ikon** ![ Hämta ikon för peer-information om duo T C P socket](./media/user-guide/netx-events/image72.png)

**Beskrivning**

Den här händelsen extraherar avsändardata från ett mottaget TCP-paket på den angivna socketen. Den returnerar avsändarens IP-adress och port.

**Informationsfält**

- Informationsfält 1: Socket pekare
- Informationsfält 2: Peer-IP-adress
- Informationsfält 3: Peer-port
- Informationsfält 4: Lånet som är betydande 32-bitars av IP-adressen

### <a name="duo-tcp-socket-set-interface"></a>Duo TCP Socket Set Interface 

#### <a name="nxd_tcp_socket_set_interface"></a>nxd_tcp_socket_set_interface

**Ikon** ![ Gränssnittsikon för Duo T C P socket set](./media/user-guide/netx-events/image73.png)

**Beskrivning**

Den här händelsen representerar inställning av utgående socketgränssnitt när en klient ansluter till en TCP-server på den angivna serverns IP-adress via nxd_tcp_client_socket_connect.

**Informationsfält** 

- Informationsfält 1: Pekare till TCP Socket
- Informationsfält 2: Gränssnitts-ID
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="duo-udp-socket-send"></a>Skicka UDP-socket för Duo 

#### <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send

**Ikon** ![ Skicka-ikonen för Duo U D P-socket](./media/user-guide/netx-events/image74.png)

**Beskrivning**

Den här händelsen representerar sändning av ett UDP-paket via den angivna socketen med inkommande IP-adress och port via nxd_udp_socket_send.

**Informationsfält** 

- Informationsfält 1: UDP-pekarsocket
- Informationsfält 2: Pekare till UDP-paket
- Informationsfält 3: Paketlängd
- Informationsfält 4: Används inte


### <a name="duo-udp-socket-set-interface"></a>Duo UDP Socket Set Interface 

#### <a name="nxd_udp_socket_set_interface"></a>nxd_udp_socket_set_interface

**Ikon** ![ Gränssnittsikon för Duo U D P socket set](./media/user-guide/netx-events/image75.png)

**Beskrivning**

Den här händelsen representerar inställning av det angivna utgående UDP-gränssnittet till det gränssnitt som motsvarar ID:t för indatagränssnittet via nxd_udp_socket_set_interface.

**Informationsfält** 

- Informationsfält 1: Pekare till UDP-socket
- Informationsfält 2: Gränssnitts-ID
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="duo-udp-source-extract"></a>Extrahera UDP-källa i Duo 

#### <a name="nxd_udp_socket_extract"></a>nxd_udp_socket_extract

**Ikon** ![ Extraheringsikon för Duo U D P-källa](./media/user-guide/netx-events/image76.png)

**Beskrivning**

Den här händelsen representerar extrahering av IP-adressen och källporten för ett mottaget paket (antingen IPv4 eller IPv6). Om IPv6 används returneras det fjärde ordet (minst betydande) i IP-adressen via nxd_udp_source_extract.

**Informationsfält**

- Informationsfält 1: Pekare till paketet
- Informationsfält 2: IP-version
- Informationsfält 3: Käll-IP-adress (IPv4 eller IPv6)
- Informationsfält 4: Källport

### <a name="icmp-enable"></a>ICMP-aktivera 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Ikon** ![ IC M P-aktivera-ikon](./media/user-guide/netx-events/image77.png)

**Beskrivning**

Den här händelsen representerar aktivering av ICMP via nx_icmp_enable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen l;
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="icmp-information-get"></a>Hämta ICMP-information 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Ikon** ![ I C M P information hämta ikon](./media/user-guide/netx-events/image78.png)

**Beskrivning**

Den här händelsen representerar att hämta information via nx_icmp_info_get.

**Informationsfält**
- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Skickade pingar
- Informationsfält 3: Pinga svar
- Informationsfält 4: Mottagna pingar

### <a name="icmp-ping"></a>ICMP Ping 

#### <a name="nx_icmp_ping"></a>nx_icmp_ping

**Ikon** ![ IC M P-pingikon](./media/user-guide/netx-events/image79.png)

**Beskrivning**

Den här händelsen representerar pingning av en mål-IP-adress via nx_icmp_ping.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: IP-adress
- Informationsfält 3: Pekare till data
- Informationsfält 4: Datastorlek

### <a name="igmp-enable"></a>Aktivera IGMP 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Ikon** ![ Aktivera ikon för I M P](./media/user-guide/netx-events/image80.png)

**Beskrivning**

Den här händelsen representerar aktivering av IGMP via nx_igmp_enable.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="igmp-information-get"></a>Hämta IGMP-information 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Ikon** ![ I G M P information get icon](./media/user-guide/netx-events/image81.png)

**Beskrivning**

Den här händelsen representerar att hämta information via nx_igmp_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Skickade rapporter
- Informationsfält 3: Mottagna frågor
- Informationsfält 4: Grupper som är sammanfogade

### <a name="igmp-loopback-disable"></a>Inaktivera IGMP Loopback 

#### <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

**Ikon** ![ Ikon för inaktivering av loopback för I M P](./media/user-guide/netx-events/image82.png)

**Beskrivning**

Den här händelsen representerar inaktivering av IGMP-loopback via nx_igmp_loopback_disable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="igmp-loopback-enable"></a>Aktivera IGMP Loopback 

#### <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

**Ikon** ![ Aktivera-ikonen för I M P-loopback](./media/user-guide/netx-events/image83.png)

**Beskrivning**

Den här händelsen representerar aktivering av IGMP-loopback via nx_igmp_loopback_enable.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="igmp-multicast-join"></a>IGMP Multicast Join 

#### <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

**Ikon** ![ Multicast-kopplingsikon för I M P](./media/user-guide/netx-events/image84.png)

**Beskrivning**

Den här händelsen representerar anslutning av en multicast-grupp via nx_igmp_multicast_join.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Grupp-IP-adress
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="igmp-multicast-leave"></a>IGMP Multicast Leave 

#### <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

**Ikon** ![ I G M P multicast leave-ikon](./media/user-guide/netx-events/image85.png)

**Beskrivning**

Den här händelsen representerar att lämna en multicast-grupp via nx_igmp_multicast_leave.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Grupp-IP-adress
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="ip-address-change-notify"></a>Meddela om IP-adressändring 

#### <a name="nx_ip_address_change_notify"></a>nx_ip_address_change_notify

**Ikon** ![ Meddelandeikon för ändring av I P-adress](./media/user-guide/netx-events/image86.png)

**Beskrivning**

Den här händelsen representerar registrering för IP-ändringsmeddelanden via nx_ip_address_change_notify.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare för återanropsfunktion
- Informationsfält 3: Pekare för ytterligare information
- Informationsfält 4: Används inte

### <a name="ip-address-get"></a>HÄMTA IP-adress 

#### <a name="nx_ip_address_get"></a>nx_ip_address_get

**Ikon** ![ Ikonen Hämta I P-adress](./media/user-guide/netx-events/image87.png)

**Beskrivning**

Den här händelsen representerar att IP-adressen skickas via nx_ip_address_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: IP-adress
- Informationsfält 3: Nätverksmask
- Informationsfält 4: Används inte

### <a name="ip-address-set"></a>IP-adressuppsättning 

#### <a name="nx_ip_address_set"></a>nx_ip_address_set

**Ikon** ![ Ikon för I P-adressuppsättning](./media/user-guide/netx-events/image88.png)

**Beskrivning**

Den här händelsen representerar inställningen av IP-adressen via nx_ip_address_set.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: IP-adress
- Informationsfält 3: Nätverksmask
- Informationsfält 4: Används inte

### <a name="ip-create"></a>IP-skapa 

#### <a name="nx_ip_create"></a>nx_ip_create

**Ikon** ![ Ikonen Skapa i P](./media/user-guide/netx-events/image89.png)

**Beskrivning**

Den här händelsen representerar skapandet av en IP-instans via nx_ip_create.

**Informationsfält** 
- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: IP-adress
- Informationsfält 3: Nätverksmask
- Informationsfält 4: Pekare för standardpaketpool

### <a name="ip-delete"></a>IP-borttagning 

#### <a name="nx_ip_delete"></a>nx_ip_delete

**Ikon** ![ Ikonen Ta bort I P](./media/user-guide/netx-events/image90.png)

**Beskrivning**

Den här händelsen representerar borttagning av en IP-instans via nx_ip_delete.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="ip-driver-direct-command"></a>Direktkommando för IP-drivrutin 

#### <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

**Ikon** ![ Kommandoikon för I P-drivrutinskommando](./media/user-guide/netx-events/image91.png)

**Beskrivning**

Den här händelsen representerar ett direkt I/O-drivrutinskommando via nx_ip_driver_direct_command.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instansen
- Infofält 2: Drivrutinskommando
- Informationsfält 3: Returvärde
- Informationsfält 4: Används inte

### <a name="ip-forwarding-disable"></a>Inaktivera IP-vidarebefordran 

#### <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

**Ikon** ![ Inaktiveringsikon för I P-vidarebefordran](./media/user-guide/netx-events/image92.png)

**Beskrivning**

Den här händelsen representerar inaktivering av IP-vidarebefordran via nx_ip_forwarding_disable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="ip-forwarding-enable"></a>Aktivera IP-vidarebefordran 

#### <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

**Ikon** ![ Aktivera-ikonen för I P-vidarebefordran](./media/user-guide/netx-events/image93.png)

**Beskrivning**

Den här händelsen representerar aktivering av IP-vidarebefordran via nx_ip_forwarding_enable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="ip-fragment-disable"></a>Inaktivera IP-fragment 

#### <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

**Ikon** ![ Inaktiveringsikon för I P-fragment](./media/user-guide/netx-events/image94.png)

**Beskrivning**

Den här händelsen representerar inaktivering av IP-fragmentering via nx_ip_fragment_disable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="ip-fragment-enable"></a>Aktivera IP-fragment 

#### <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

**Ikon** ![ Aktivera fragmentikon för I P](./media/user-guide/netx-events/image95.png)

**Beskrivning**

Den här händelsen representerar aktivering av IP-fragmentering via nx_ip_fragment_enable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="ip-gateway-address-set"></a>IP Gateway-adressuppsättning 

#### <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

**Ikon** ![ Ikon för ip-gatewayadressuppsättning](./media/user-guide/netx-events/image96.png)

**Beskrivning**

Den här händelsen representerar inställningen av gatewayens IP-adress via nx_ip_gateway_address_set.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Gateway-IP-adress
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="ip-information-get"></a>Hämta IP-information 

#### <a name="nx_ip_info_get"></a>nx_ip_info_get

**Ikon** ![ Hämta ikon för I P-information](./media/user-guide/netx-events/image97.png)

**Beskrivning** Den här händelsen representerar att hämta IP-information via nx_ip_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: SKICKADE IP-byte
- Informationsfält 3: MOTTAGNA IP-byte
- Informationsfält 4: IP-paket som släppts

### <a name="ip-interface-attach"></a>Koppla IP-gränssnitt 

#### <a name="nx_interface_attach"></a>nx_interface_attach

**Ikon** ![ I P iterface attach icon (I P iterface attach icon)](./media/user-guide/netx-events/image98.png)

**Beskrivning**

Den här händelsen representerar ett sekundärt nätverksgränssnitt som kopplas till IP-instansen via nx_ip_interface_attach.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: IP-adress för gränssnitt
- Informationsfält 3: Indexera till IP-gränssnittstabell
- Informationsfält 4: Används inte

### <a name="ip-interface-info-get"></a>Hämta information om IP-gränssnitt 

#### <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

**Ikon** ![ Hämta ikon för INFORMATION OM IP-gränssnitt](./media/user-guide/netx-events/image99.png)

**Beskrivning**

Den här händelsen representerar information som hämtats från det angivna nätverksgränssnittet via nx_ip_interface_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: IP-adress för gränssnitt
- Informationsfält 3: MAC-gränssnittsadress msb
- Informationsfält 4: MAC-gränssnittsadress lsb

### <a name="ip-raw-packet-disable"></a>Inaktivera IP-rådatapaket 

#### <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

**Ikon** ![ Inaktiveringsikon för I P raw-paket](./media/user-guide/netx-events/image100.png)

**Beskrivning**

Den här händelsen representerar inaktivering av rå IP-paketkommunikation via nx_ip_raw_packet_disable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="ip-raw-packet-enable"></a>Aktivera IP-rådatapaket 

#### <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

**Ikon** ![ I P raw packet enable icon (Aktivera I P-raw-paketikon)](./media/user-guide/netx-events/image101.png)

**Beskrivning**

Den här händelsen representerar aktivering av rå IP-paketkommunikation via nx_ip_raw_packet_enable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="ip-raw-packet-receive"></a>IP-rådata inkommande paket 

#### <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

**Ikon** ![ Ikonen Ta emot raw-paket i I P](./media/user-guide/netx-events/image102.png)

**Beskrivning**

Den här händelsen representerar mottagandet av ett rådata-IP-paket via nx_ip_raw_packet_receive.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till paket
- Informationsfält 3: Väntealternativ
- Informationsfält 4: Används inte

### <a name="ip-raw-packet-send"></a>SKICKA IP-rådatapaket 

#### <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

**Ikon** ![ Ikonen Skicka raw-paket](./media/user-guide/netx-events/image103.png)

**Beskrivning**

Den här händelsen representerar sändning av ett obearbetat IP-paket via nx_ip_raw_packet_send.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Pekare till paket
- Informationsfält 3: Mål-IP-adress
- Informationsfält 4: Typ av tjänst

### <a name="ip-static-route-add"></a>Lägg till statisk IP-väg 

#### <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

**Ikon** ![ Lägg till ikon för statisk väg för I P](./media/user-guide/netx-events/image104.png)

**Beskrivning**

Den här händelsen representerar en statisk väg som läggs till i IP-instansroutningstabellen via nx_ip_static_route_add.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Nätverksadress
- Informationsfält 3: Nätverksmask
- Informationsfält 4: Nästa hopp

### <a name="ip-static-route-delete"></a>Ta bort statisk IP-väg 

#### <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

**Ikon** ![ Ikonen Ta bort statiska spår för I P](./media/user-guide/netx-events/image105.png)

**Beskrivning**

Den här händelsen representerar en statisk väg som tas bort från IP-instansroutningstabellen via nx_ip_static_route_delete.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Nätverksadress
- Informationsfält 3: Nätverksmask
- Informationsfält 4: Används inte

### <a name="ip-status-check"></a>IP-statuskontroll 

#### <a name="nx_ip_status_check"></a>nx_ip_status_check

**Ikon** ![ Ikon för I P-statuskontroll](./media/user-guide/netx-events/image106.png)

**Beskrivning**

Den här händelsen representerar kontroll av IP-status via nx_ip_status_check.

Informationsfält 

- Informationsfält 1: Pekare till IP-instansen
- Informationsfält 2: Begärd status
- Informationsfält 3: Faktisk status
- Informationsfält 4: Väntealternativ

### <a name="ipsec-enable"></a>IPSEC-aktivera 

#### <a name="nx_ipsec_enable"></a>nx_ipsec_enable

**Ikon** ![ Aktivera-ikonen för I P S E C](./media/user-guide/netx-events/image107.png)

**Beskrivning**

Den här händelsen representerar aktivering av IPSec-tjänster på den angivna IP-instansen via nx_ipsec_enable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="packet-allocate"></a>Allokera paket 

#### <a name="nx_packet_allocate"></a>nx_packet_allocate

**Ikon** ![ Ikon för att allokera paket](./media/user-guide/netx-events/image108.png)

**Beskrivning**

Den här händelsen representerar allokering av ett paket via nx_packet_allocate.

**Informationsfält**

- Informationsfält 1: Pekare till paketpoolen
- Informationsfält 2: Pekare till allokerat paket
- Informationsfält 3: Pakettyp
- Informationsfält 4: Tillgängliga paket

### <a name="packet-copy"></a>Paketkopiering 

#### <a name="nx_packet_copy"></a>nx_packet_copy

**Ikon** ![ Paket cpy-ikon](./media/user-guide/netx-events/image109.png)

**Beskrivning**

Den här händelsen representerar kopiering av ett paket via nx_packet_copy.

**Informationsfält**

- Informationsfält 2: Ny paket pekare
- Informationsfält 3: Pekare till paketpool
- Informationsfält 4: Väntealternativ

### <a name="packet-data-append"></a>Tillägg av paketdata 

#### <a name="nx_packet_data_append"></a>nx_packet_data_append

**Ikon** ![ Ikon för tillägg av paketdata](./media/user-guide/netx-events/image110.png)

**Beskrivning**

Den här händelsen representerar att lägga till data till ett paket via nx_packet_data_append.

**Informationsfält**

- Informationsfält 1: Pekare till paketet
- Informationsfält 2: Pekare till data
- Informationsfält 3: Datastorlek
- Informationsfält 4: Pekare till paketpool

### <a name="packet-data-extract-offset"></a>Offset för extrahering av paketdata 

#### <a name="nx_udp_source_extract_offset"></a>nx_udp_source_extract_offset

**Ikon** ![ Förskjutningsikon för paketdatautdrag](./media/user-guide/netx-events/image111.png)

**Beskrivning**

Den här händelsen representerar paketdata som extraheras till en tillhandahållen buffert från ett paket via nx_udp_source_extract_offset.

**Informationsfält**

- Informationsfält 1: Pekare till paket
- Informationsfält 2: Storleken på angiven buffert
- Informationsfält 3: Antal kopierade byte
- Informationsfält 4: Används inte

### <a name="packet-data-retrieve"></a>Hämta paketdata 

#### <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

**Ikon** ![ Ikonen Hämta paketdata](./media/user-guide/netx-events/image112.png)

**Beskrivning**

Den här händelsen representerar hämtning av data från ett paket via nx_packet_data_retrieve.

**Informationsfält** 

- Informationsfält 1: Pekare till paketet
- Informationsfält 2: Pekare till buffertens start
- Informationsfält 3: Kopierade byte
- Informationsfält 4: Används inte

### <a name="packet-length-get"></a>Hämta paketlängd 

#### <a name="nx_packet_length_get"></a>nx_packet_length_get

**Ikon** ![ Hämta ikon för paketlängd](./media/user-guide/netx-events/image113.png)

**Beskrivning**

Den här händelsen representerar att hämta längden på ett paket via nx_packet_length_get.

**Informationsfält**

- Informationsfält 1: Pekare till paketet
- Informationsfält 2: Paketlängd
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="packet-pool-create"></a>Skapa paketpool 

#### <a name="nx_packet_pool_create"></a>nx_packet_pool_create

**Ikon** ![ Ikon för att skapa paketpool](./media/user-guide/netx-events/image114.png)

**Beskrivning**

Den här händelsen representerar skapandet av en paketpool via nx_packet_pool_create.

**Informationsfält** 

- Informationsfält 1: Pekare till paketpoolen
- Informationsfält 2: Paketnyttolaststorlek
- Informationsfält 3: Pekare till poolminnesområdet
- Informationsfält 4: Storlek på poolminnesområdet

### <a name="packet-pool-delete"></a>Ta bort paketpool 

#### <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

**Ikon** ![ Ikonen Ta bort paketpool](./media/user-guide/netx-events/image115.png)

**Beskrivning**

Den här händelsen representerar borttagning av en paketpool via nx_packet_pool_delete.

**Informationsfält** 

- Informationsfält 1: Pekare till paketpoolen
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

#### <a name="packet-pool-information-get"></a>Hämta information om paketpool 

#### <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

**Ikon** ![ Hämta ikon för information om paketpool](./media/user-guide/netx-events/image116.png)

**Beskrivning**

Den här händelsen representerar att hämta information om paketpoolen via nx_packet_pool_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till paketpool
- Informationsfält 2: Totalt antal paket
- Informationsfält 3: Tillgängliga paket
- Informationsfält 4: Tomma begäranden

### <a name="packet-release"></a>Paketutgågår 

#### <a name="nx_packet_data_release"></a>nx_packet_data_release

**Ikon** ![ Ikon för paketutgås](./media/user-guide/netx-events/image117.png)

**Beskrivning**

Den här händelsen representerar lanserar ett paket via nx_packet_release.

**Informationsfält**

- Informationsfält 1: Pekare till paketet
- Informationsfält 2: Paketstatus
- Informationsfält 3: Tillgängliga paket
- Informationsfält 4: Används inte

### <a name="packet-transmit-release"></a>Frisläppning av paket överföring 

#### <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

**Ikon** ![ Ikon för lansering av paket överföring](./media/user-guide/netx-events/image118.png)

**Beskrivning**

Den här händelsen representerar lanserar ett överföringspaket via nx_packet_transmit_release.

**Informationsfält**

- Informationsfält 1: Pekare till paketet
- Informationsfält 2: Paketstatus
- Informationsfält 3: Tillgängliga paket
- Informationsfält 4: Används inte

### <a name="rarp-disable"></a>Inaktivera RARP 

#### <a name="nx_rarp_disable"></a>nx_rarp_disable

**Ikon** ![ Inaktivera R A R P-ikon](./media/user-guide/netx-events/image119.png)

**Beskrivning**

Den här händelsen representerar inaktivering av RARP via nx_rarp_disable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="rarp-enable"></a>RARP-aktivera 

#### <a name="nx_rarp_enable"></a>nx_rarp_enable

**Ikon** ![ Aktivera R A R P-ikon](./media/user-guide/netx-events/image120.png)

**Beskrivning**

Den här händelsen representerar aktivering av RARP via nx_rarp_enable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="rarp-information-get"></a>Hämta RARP-information 

#### <a name="nx_rarp_info_get"></a>nx_rarp_info_get

**Ikon** ![ Hämta information om R A R P-information](./media/user-guide/netx-events/image121.png)

**Beskrivning**

Den här händelsen representerar att hämta RARP-information via nx_rarp_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Skickade begäranden
- Informationsfält 3: Mottagna svar
- Informationsfält 4: Ogiltiga svar

### <a name="system-initialize"></a>Initiera systemet 

#### <a name="nx_system_initialize"></a>nx_system_initialize

**Ikon** ![ Ikonen Systemitiering](./media/user-guide/netx-events/image122.png)

**Beskrivning**

Den här händelsen representerar initiering av NetX via nx_system_initialize.

**Informationsfält**

- Informationsfält 1: Används inte
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="tcp-client-socket-bind"></a>TCP-klientsocketbindning 

#### <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

**Ikon** ![ Bindningsikon för T P-klientsocket](./media/user-guide/netx-events/image123.png)

**Beskrivning**

Den här händelsen representerar bindning av en klientsocket till en port via nx_tcp_client_socket_bind.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Begärd port
- Informationsfält 4: Väntealternativ

### <a name="tcp-client-socket-connect"></a>TCP Client Socket Anslut 

#### <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

**Ikon** ![ Anslutningsikon för T C P-klientsocket](./media/user-guide/netx-events/image124.png)

**Beskrivning**

Den här händelsen representerar att upprätta en klientsocketanslutning via nx_tcp_client_socket_connect.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Serverns IP-adress
- Informationsfält 4: Serverport begärd

### <a name="tcp-client-socket-port-get"></a>Hämta TCP-klientsocketport 

#### <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

**Ikon** ![ Hämta ikon för T C P-klientsocketport](./media/user-guide/netx-events/image125.png)

**Beskrivning**

Den här händelsen representerar att portnumret för klientsocketen skickas via nx_tcp_client_socket_port_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Portnummer
- Informationsfält 4: Används inte

### <a name="tcp-client-socket-unbind"></a>Ta bort bindning för TCP-klientsocket 

#### <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

**Ikon** ![ Ta bort bindningsikon för T C P-klientsocket](./media/user-guide/netx-events/image126.png)

**Beskrivning**

Den här händelsen representerar avbindning av porten som är associerad med socketen via nx_tcp_client_socket_unbind.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="tcp-enable"></a>TCP-aktivera 

#### <a name="nx_tcp_enable"></a>nx_tcp_enable

**Ikon** ![ Aktivera-ikonen T C P](./media/user-guide/netx-events/image127.png)

**Beskrivning**

Den här händelsen representerar aktivering av TCP via nx_tcp_enable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

###  <a name="tcp-free-port-find-tcp-free-port-find"></a>Hitta den kostnadsfria TCP-porten hitta den kostnadsfria TCP-porten 

#### <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

**Ikon** ![ Ikonen T CP free port find (T CP kostnadsfri port för att hitta)](./media/user-guide/netx-events/image128.png)

**Beskrivning**

Den här händelsen representerar att hitta en kostnadsfri TCP-port via nx_tcp_free_port_find.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Starta sökportnummer
- Informationsfält 3: Kostnadsfritt portnummer
- Informationsfält 4: Används inte

###  <a name="tcp-infomation-get"></a>TCP Infomation Get 

#### <a name="nx_tcp_info_get"></a>nx_tcp_info_get

**Ikon** ![ Hämta informationsikon för T C P](./media/user-guide/netx-events/image129.png)

**Beskrivning**

Den här händelsen representerar hämtning av TCP-information för den angivna IP-instansen via nx_tcp_info_get.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Antal skickade byte
- Informationsfält 3: Antal mottagna byte
- Informationsfält 4: Antal ogiltiga paket

###  <a name="tcp-server-socket-accept"></a>ACCEPTERA TCP-serversocket 

#### <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

**Ikon** ![ Ikonen acceptera t C P-serversocket](./media/user-guide/netx-events/image130.png)

**Beskrivning**

Den här händelsen representerar att konfigurera serversocketen efter att en aktiv anslutningsbegäran togs emot via nx_tcp_server_socket_accept.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Alternativet Vänta
- Informationsfält 4: Sockettillstånd

###  <a name="tcp-server-socket-listen"></a>Lyssna på TCP-serversocket 

#### <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

**Ikon** ![ Ikon för T C P-serversocket lsten](./media/user-guide/netx-events/image131.png)

**Beskrivning**

Den här händelsen representerar registrering av en lyssnarbegäran och en serversocket för den angivna TCP-porten via nx_tcp_server_socket_listen.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: TCP-portnummer
- Informationsfält 3: Pekare till socket
- Informationsfält 4: Maximalt antal anslutningar som kan köas

###  <a name="tcp-server-socket-relisten"></a>Omlistning av TCP-serversocket 

#### <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

**Ikon** ![ Ikon för återlistning av T C P-serversocket](./media/user-guide/netx-events/image132.png)

**Beskrivning**

Den här händelsen representerar registrering av en annan serversocket för en befintlig lyssna-begäran på den angivna TCP-porten via nx_tcp_server_socket_relisten.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: TCP-portnummer
- Informationsfält 3: Pekare till socket
- Informationsfält 4: Sockettillstånd

###  <a name="tcp-server-socket-unaccept"></a>Tcp-serversocket unaccept 

#### <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

**Ikon** ![ Unaccept-ikon för T C P-serversocket](./media/user-guide/netx-events/image133.png)

**Beskrivning**

Den här händelsen representerar borttagning av serversocketen från associationen med porten som tar emot en tidigare passiv anslutning via nx_tcp_server_socket_unaccept.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Sockettillstånd
- Informationsfält 4: Används inte

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a>TCP-serversocket avlistat TCP-serversocket avlistat 

#### <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

**Ikon** ![ Ikon för avlistning av T C P-serversocket](./media/user-guide/netx-events/image134.png)

**Beskrivning**

Den här händelsen representerar borttagning av en tidigare lyssnarbegäran för den angivna TCP-porten via nx_tcp_server_socket_unlisten.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: TCP-portnummer
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="tcp-socket-bytes-available"></a>Tillgängliga TCP Socket-byte 

#### <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

**Ikon** ![ Ikon för tillgängliga T C P-socketbyte](./media/user-guide/netx-events/image135.png)

**Beskrivning**

Den här händelsen representerar det antal byte som för närvarande är tillgängliga på den angivna TCP-mottagande socketen via nx_tcp_socket_bytes_available.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till TCP-socket
- Informationsfält 3: Mottagna byte på socketen
- Informationsfält 4: Används inte

### <a name="tcp-socket-create"></a>Skapa TCP Socket 

#### <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

**Ikon** ![ Ikon för att skapa T C P-socket](./media/user-guide/netx-events/image136.png)

**Beskrivning**

Den här händelsen representerar skapandet av en TCP-socket via nx_tcp_socket_create.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Typ av tjänst
- Informationsfält 4: Ta emot fönsterstorlek

### <a name="tcp-socket-delete"></a>Ta bort TCP-socket 

#### <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

**Ikon** ![ Borttagningsikon för T C P-socket](./media/user-guide/netx-events/image137.png)

**Beskrivning**

Den här händelsen representerar borttagning av en socket via nx_tcp_socket_delete.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Sockettillstånd
- Informationsfält 4: Används inte

### <a name="tcp-socket-disconnect"></a>Koppla från TCP-socket 

#### <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

**Ikon** ![ Frånkopplingsikon för T C P-socket](./media/user-guide/netx-events/image138.png)

**Beskrivning**

Den här händelsen representerar frånkoppling av en socket via nx_tcp_socket_disconnect.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Alternativet Vänta
- Informationsfält 4: Sockettillstånd

### <a name="tcp-socket-information-get"></a>HÄMTA INFORMATION OM TCP-socket 

#### <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

**Ikon** ![ Information om T C P socket hämta ikon](./media/user-guide/netx-events/image139.png)

**Beskrivning**

Den här händelsen representerar att hämta information om en socket via nx_tcp_socket_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Byte som skickas via den här socketen
- Informationsfält 4: Mottagna byte via den här socketen

### <a name="tcp-socket-mss-get"></a>TCP Socket MSS Get 

#### <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

**Ikon** ![ Hämta-ikonen för T C P socket M S S](./media/user-guide/netx-events/image140.png)

**Beskrivning**

Den här händelsen representerar att hämta socketens MSS via nx_tcp_socket_mss_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Maximal segmentstorlek (MSS)
- Informationsfält 4: Sockettillstånd

### <a name="tcp-socket-mss-peer-get"></a>TCP Socket MSS Peer Get 

#### <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

**Ikon** ![ T C P socket M S S peer get-ikon](./media/user-guide/netx-events/image141.png)

**Beskrivning**

Den här händelsen representerar att hämta MSS-värdet för socketens peer via nx_tcp_socket_mss_peer_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Peers MSS
- Informationsfält 4: Sockettillstånd

### <a name="tcp-socket-mss-set"></a>MSS-uppsättning för TCP Socket 

#### <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

**Ikon** ![ Ikon för T C P socket M S S S-uppsättning](./media/user-guide/netx-events/image142.png)

**Beskrivning**

Den här händelsen representerar inställning av en sockets MSS via nx_tcp_socket_mss_set.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: MSS
- Informationsfält 4: Sockettillstånd

### <a name="tcp-socket-peer-info-get"></a>Hämta peerinformation för TCP Socket 

#### <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

**Ikon** ![ Peerinfo för T C P socket hämta ikon](./media/user-guide/netx-events/image143.png)

**Beskrivning**

Den här händelsen representerar information som hämtas från TCP-socketen angående peer-IP-adressen (t.ex>som ansluter värden) och porten via nx_tcp_socket_peer_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till TCP-socket
- Informationsfält 2: Peer-IP-adress
- Informationsfält 3: Peer-portnummer
- Informationsfält 4: Används inte

### <a name="tcp-socket-receive"></a>TCP Socket Receive 

#### <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

**Ikon** ![ Ta emot T C P-socketikonen](./media/user-guide/netx-events/image144.png)

**Beskrivning**

Den här händelsen representerar mottagande av data från en socket via nx_tcp_socket_receive.

**Informationsfält**

- Informationsfält 1: Pekare till socket
- Informationsfält 2: Pekare till mottaget paket
- Informationsfält 3: Mottagen paketlängd
- Informationsfält 4: Ta emot sekvensnummer

### <a name="tcp-socket-receive-notify"></a>Meddelande om TCP Socket-mottagning 

#### <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

**Ikon** ![ Meddelandeikon för att ta emot T C P-socket](./media/user-guide/netx-events/image145.png)

**Beskrivning**

Den här händelsen representerar registrering av ett meddelande om återanrop för en socket via nx_tcp_socket_receive_notify.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Pekare för att ta emot infofält 4: Används inte

### <a name="tcp-socket-send"></a>TCP Socket Send 

#### <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

**Ikon** ![ Ikonen Skicka T C P-socket](./media/user-guide/netx-events/image146.png)

**Beskrivning**

Den här händelsen representerar sändning av data på en socket via nx_tcp_socket_send.

**Informationsfält**

- Informationsfält 1: Pekare till socket
- Informationsfält 2: Pekare till paket
- Informationsfält 3: Paketlängd
- Informationsfält 4: Överföringssekvensnummer

### <a name="tcp-socket-state-wait"></a>TCP Socket State Wait 

#### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

**Ikon** ![ Ikon för t C P sockettillståndsvänteikon](./media/user-guide/netx-events/image147.png)

**Beskrivning**

Den här händelsen representerar väntan på att en socket ska ange ett visst tillstånd via nx_tcp_socket_state_wait.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Önskat sockettillstånd
- Informationsfält 4: Tidigare sockettillstånd

### <a name="tcp-socket-transmit-configure"></a>Konfigurera TCP Socket-överföring 

#### <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

**Ikon** ![ Konfigurationsikon för överföring av T C P-socket](./media/user-guide/netx-events/image148.png)

**Beskrivning**

Den här händelsen representerar konfiguration av överföringsalternativen för en socket via nx_tcp_socket_transmit_configure.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Överföringsködjup
- Informationsfält 4: Tidsgränsvärde

### <a name="tcp-socket-window-update-notify-set"></a>Meddelandeuppsättning för TCP Socket-fönsteruppdatering 

#### <a name="nx_tcp_window_update_notify_set"></a>nx_tcp_window_update_notify_set

**Ikon** ![ Meddelandeikon för uppdatering av T C P-socketfönster](./media/user-guide/netx-events/image149.png)

**Beskrivning**

Den här händelsen representerar en TCP-socket som tar emot ett meddelande om en ökning i fjärrvärdens mottagningsfönster via nx_tcp_window_update_notify_set.

**Informationsfält** 

- Informationsfält 1: Pekare till TCP-socket
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="udp-enable"></a>UDP-aktivera 

#### <a name="nx_udp_enable"></a>nx_udp_enable

**Ikon** ![ Aktivera ikon för U D P](./media/user-guide/netx-events/image150.png)

**Beskrivning**

Den här händelsen representerar aktivering av UDP via nx_udp_enable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="udp-free-port-find"></a>Hitta kostnadsfri UDP-port 

#### <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

**Ikon** ![ Ikon för att hitta den kostnadsfria porten i U D P](./media/user-guide/netx-events/image151.png)

**Beskrivning**

Den här händelsen representerar att hitta en kostnadsfri UDP-port via nx_udp_free_port_find.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Startar porten att söka från
- Informationsfält 3: Kostnadsfri port
- Informationsfält 4: Används inte

### <a name="udp-information-get"></a>Hämta UDP-information 

#### <a name="nx_udp_info_get"></a>nx_udp_info_get

**Ikon** ![ Hämta information för U D P-information](./media/user-guide/netx-events/image152.png)

**Beskrivning**

Den här händelsen representerar att hämta information via nx_udp_info_get.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: UDP-byte skickade
- Informationsfält 3: Mottagna UDP-byte
- Informationsfält 4: Ogiltiga paket

### <a name="udp-socket-bind"></a>UDP Socket Bind 

#### <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

**Ikon** ![ Ikon för U D P-socketbindning](./media/user-guide/netx-events/image153.png)

**Beskrivning**

Den här händelsen representerar bindning av en UDP-socket till en port via nx_udp_socket_bind.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Portnummer
- Informationsfält 4: Väntealternativ

### <a name="udp-socket-bytes-available"></a>Tillgängliga UDP Socket Bytes 

#### <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

**Ikon** ![ Ikon för tillgängliga byte för U D P-socket](./media/user-guide/netx-events/image154.png)

**Beskrivning**

Den här händelsen representerar det aktuella antalet byte som tas emot på UDP-socketen via nx_udp_socket_bytes_available.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Mottagna byte på socket
- Informationsfält 4: Används inte

### <a name="udp-socket-checksum-disable"></a>Inaktivera kontrollsumma för UDP-socket 

#### <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

**Ikon** ![ Inaktivera ikon för kontrollsumma för U D P-socket](./media/user-guide/netx-events/image155.png)

**Beskrivning**

Den här händelsen representerar inaktivering av kontrollsumman för data på en UDP-socket via nx_udp_socket_checksum_disable.

**Informationsfält** 

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="udp-socket-checksum-enable"></a>Aktivera kontrollsumma för UDP-socket 

#### <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

**Ikon** ![ Aktivera ikon för kontrollsumma för U D P-socket](./media/user-guide/netx-events/image156.png)

**Beskrivning**

Den här händelsen representerar aktivering av bearbetning av kontrollsumma på en socket via nx_udp_socket_checksum_enable.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="udp-socket-create"></a>Skapa UDP-socket 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Ikon** ![ Ikon för att skapa U D P-socket](./media/user-guide/netx-events/image157.png)

**Beskrivning**

Den här händelsen representerar skapandet av en UDP-socket via nx_udp_socket_create.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Typ av tjänst
- Informationsfält 4: Maximal mottagningskö

### <a name="udp-socket-delete-event"></a>UDP Socket Delete-händelse 

#### <a name="nx_udp_socket_delete-event"></a>nx_udp_socket_delete händelse

**Ikon** ![ Händelseikon för borttagning av U D P-socket](./media/user-guide/netx-events/image158.png)

**Beskrivning**

Den här händelsen representerar borttagning av en UDP-socket via nx_udp_socket_delete.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="udp-socket-information-get-event"></a>Hämta händelse för UDP Socket-information 

#### <a name="nx_udp_socket_info_get-event"></a>nx_udp_socket_info_get händelse

**Ikon** ![ Information om U D P socket hämta händelseikon](./media/user-guide/netx-events/image159.png)

**Beskrivning**

Den här händelsen representerar att få information om en UDP-socket via nx_udp_socket_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Byte som skickas via socket
- Informationsfält 4: Mottagna byte via socket

### <a name="udp-socket-interface-set"></a>UDP Socket Interface Set 

#### <a name="nx_udp_socket_interface_set-event"></a>nx_udp_socket_interface_set händelse

**Ikon** ![ Ikon för U D P socket-gränssnittsuppsättning](./media/user-guide/netx-events/image160.png)

**Beskrivning**

Den här händelsen representerar inställning av det utgående gränssnittet för den angivna UDP-socketen med det angivna gränssnittet via nx_udp_socket_interface_set.

**Informationsfält**

- Informationsfält 1: Pekare till UDP-socket
- Informationsfält 2: Index som motsvarar gränssnittet för socketen
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="udp-socket-port-get"></a>Hämta UDP Socket-port 

#### <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

**Ikon** ![ Ikonen hämta U D P-socketport](./media/user-guide/netx-events/image161.png)

**Beskrivning**

Den här händelsen representerar hämtning av den UDP-port som den angivna UDP-socketen är bunden till via nx_udp_socket_port_get.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till UDP-socket
- Informationsfält 3: Portnummer
- Informationsfält 4: Används inte

### <a name="udp-socket-receive"></a>UDP Socket Receive 

#### <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

**Ikon** ![ Ta emot U D P-socketikon](./media/user-guide/netx-events/image162.png)

**Beskrivning**

Den här händelsen representerar mottagande av data på den angivna UDP-socketen via nx_udp_socket_receive.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till UDP-socket
- Informationsfält 3: Pekare till mottaget paket
- Informationsfält 4: Mottagen paketstorlek

### <a name="udp-socket-receive-notify"></a>UDP Socket Receive Notify 

#### <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

**Ikon** ![ U D P socket receive notify icon ](./media/user-guide/netx-events/image163.png) s **Description**

Den här händelsen representerar registrering av ett motringningsanrop via nx_udp_socket_receive_notify.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Pekare för att ta emot notify-funktionen InfoFält 4: Används inte

### <a name="udp-socket-send"></a>UDP Socket Send 

#### <a name="nx_udp_socket_send"></a>nx_udp_socket_send

**Ikon** ![ Skicka U D P-socketikon](./media/user-guide/netx-events/image164.png)

**Beskrivning**

Den här händelsen representerar sändning av data via en UDP-socket via nx_udp_socket_send.

**Informationsfält**

- Informationsfält 1: Pekare till socket
- Informationsfält 2: Pekare till paket
- Informationsfält 3: Paketlängd
- Informationsfält 4: Mål-IP-adress

### <a name="udp-socket-unbind"></a>UDP Socket Unbind 

#### <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

**Ikon** ![ Ta bort bindningsikon för U D P-socket](./media/user-guide/netx-events/image165.png)

**Beskrivning**

Den här händelsen representerar avbindning av en UDP-port med en socket via nx_udp_socket_unbind.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans
- Informationsfält 2: Pekare till socket
- Informationsfält 3: Portnummer
- Informationsfält 4: Används inte

### <a name="udp-source-extract"></a>UDP-källutdrag 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Ikon** ![ Extraheringsikon för U D P-källa](./media/user-guide/netx-events/image166.png)

**Beskrivning**

Den här händelsen representerar att ip-adressen och portnumret för ett mottaget UDP-paket tas emot via nx_udp_source_extract.

**Informationsfält**

- Informationsfält 1: Pekare till paket
- Informationsfält 2: Avsändarens IP-adress
- Informationsfält 3: Avsändarens portnummer
- Informationsfält 4: Används inte