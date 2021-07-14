---
title: Förstå Azure RTOS NetX
description: Azure RTOS NetX är en högpresterande implementering av TCP/IP-protokollstandarder, helt integrerad med Azure RTOS ThreadX och tillgänglig för alla processorer som stöds.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 63fd212249da6154926684f9bc844d2c2a78e84e
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754853"
---
# <a name="overview-of-azure-rtos-netx"></a>Översikt över Azure RTOS NetX

Azure RTOS NetX är en inbäddad TCP/IP IPv4-nätverksstack i branschklass som är utformad särskilt för djupt inbäddade program, realtidsprogram och IoT-program. Azure RTOS NetX är Microsofts ursprungliga IPv4-nätverksstack och är i stort sett en delmängd av Azure RTOS. NetX tillhandahåller inbäddade program med kärnnätverksprotokoll som IPv4, TCP och UDP samt en komplett uppsättning ytterligare tilläggsprotokoll på högre nivå. Ett litet fotavtryck, snabb körning och överlägsen användarvänlighet gör Azure RTOS NetX till ett perfekt val för de mest krävande inbäddade IoT-programmen.

## <a name="api-protocols"></a>API-protokoll
Azure RTOS NetX har stöd för följande.

### <a name="telnet"></a>Telnet

* Minimalt RAM-fotavtryck på 0,5 kB och 0,3 KB.
* Stöd för klienter och servrar.

### <a name="auto-ip"></a>Automatisk IP-adress

* Automatisk IPv4-adresstilldelning.
* Minimalt 1,2 kB, 300 byte RAM-minne.

### <a name="http---hypertext-transfer-protocolhttp"></a>HTTP – Hypertext Transfer Protocol(HTTP)

* Minimalt 2,8 kB till 4,8 kBFLASH, 0,4 kB till 1,0 KB RAM-fotavtryck.
* Stöd för klienter och servrar.

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a>SMTP – Simple Mail Transfer Protocol (SMTP)

* Minimalt RAM-fotavtryck på 4,1 kB och 0,6 KB
* Klientstöd

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a>DHCP – Dynamic Host Configuration Protocol (DHCP)

* Minimalt 3,6 KB till 4,6 KB FLASH, 2,7 KB RAM-fotavtryck
* Stöd för klienter och servrar
* Stöd för IPv4

### <a name="p0p3---post-office-protocol-version-3-pop3"></a>P0P3 – Efter Office Protocol Version 3 (POP3)

* Minimalt RAM-fotavtryck på 8,1 kB och 1,4 KB
* Klientstöd

### <a name="snmp---simple-network-management-protocol-snmp"></a>SNMP – Simple Network Management Protocol (SNMP)

* Minimalt RAM-fotavtryck på 10,9 kB och 2,6 KB
* Agentstöd för VI, V2 och V3

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a>FTP, TFTP – File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)

* FTP minimalt 1,8 kB till 7,2 kBFLASH, 0,6 kB till 2,1 KB RAM-fotavtryck
* TFTP Minimalt 1,7 kB till 2,4 kBFLASH, 0,3 kB till 1,8 KB RAM-fotavtryck
* Stöd för klienter och servrar

### <a name="ppp---polnt-to-point-protocol-ppp"></a>PPP – Polnt-to-PoInt Protocol (PPP)

* Minimalt RAM-fotavtryck på 7,1 kB och 3,8 KB
* Pålitlig och tillförlitlig.

### <a name="sntp---simple-network-time-protocol-sntp"></a>SNTP – Simple Network Time Protocol (SNTP)

* Minimalt 4 KB och 0,5 KB RAM
* Klientstöd

### <a name="azure-rtos-netx-api"></a>Azure RTOS NetX API

* Snabb IMPLEMENTERING av API:et nollkopiering
* Valfritt BSD-lager för portning av äldre socketkod

### <a name="igmp---internet-group-management-protocol-igmp"></a>IGMP – Internet Group Management Protocol (IGMP)

* Minimal 2,5 KB FLASH
* Stöd för IPv4-multicast-grupper
* IXIA IxANVL-verifierad
* Valfri IGMP-statistik
* Spårning på systemnivå via Azure RTOS TraceX

### <a name="udp---user-datagram-protocol-udp"></a>UDP – UDP (User Datagram Protocol)

* Minimal 2,5 KB FLASH, 124 sockets byte RAM-minne per socket
* Snabb, nära trådad TCP-paketbearbetning:
* RX 95 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 14 % MCU-användning
* TX 94 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 10 % MCU-användning
* UDP Fast Path™teknik
* Inga gränser för antalet UDP
* IXIA IxANVL-verifierad
* Valfri stängning vid socket-mottagning
* Valfri tidsgräns för all låsning
* Valfri UDP-statistik
* Spårning på systemnivå via Azure RTOS TraceX

### <a name="tcp---transmission-control-protocol-tcp"></a>TCP – Transmission Control Protocol (TCP)

* Minimal 10,5K8 till 12,5 KB FLASH, 280 byte RAM-minne per socket
* Snabb, nästan wlre tcp-paketbearbetning:
* RX 93 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 20 % MCU-användning
* TX 94 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 27 % MCU-användning
* Tillförlitlig anslutning
* Inga gränser för antalet TCP-sockets
* IXIA IxANVL-verifierad
* Valfri stängning vid socket-mottagning/-överföring
* Valfri tidsgräns för all låsning
* Valfri TCP-statistik
* Spårning på systemnivå via Azure RTOS TraceX

### <a name="icmp---internet-control-message-protocol-icmp"></a>ICMP – Internet Control Message Protocol (ICMP)

* Minimal 2,5 KB FLASH
* Stöd för IPv4
* IXIA IxANVL-verifierad
* Pingbegäran och pingsvar
* Valfri trådavstängning vid pingbegäranden
* Valfri tidsgräns för all låsning
* Valfri ICMP-statistik
* Spårning på systemnivå via Azure RTOS TraceX

### <a name="ipv4---internet-protocol-ip"></a>IPv4 – Internet Protocol (IP)

* Minimalt 3,5 KB till 8,5 KB FLASH, 2 KB till 3 KB RAM-fotavtryck.
* Piconet™Arkitektur.
* Snabb, nästan trådig prestanda.
* Stöd för flera gränssnitt.
* Stöd för flera hem.
* Stöd för statisk routning.
* Stöd för IP-fragmentering/återmontering.
* IPv4-stöd.
* IXIA IxANVL Validated.
* Fas II– redo logotypcertifiering.
* Valfri IP-statistik.
* Väldefinierat, intuitivt drivrutinsgränssnitt på fysiskt lager.
* Spårning på systemnivå via Azure RTOS TraceX.

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a>ARP/RARP – Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)

* Minimal 1,7 KB FLASH, RAM-storlek.
* Dynamisk upplösning av 32-blt IPv4- och 48-blt MAC-adresser.
* IXIA IxANVL Validated.
* Flexibel, användardefinierad ARP-cache.
* Bra ARP-stöd.
* Valfri ARP/RARP-statistik som bestäms av programmet.
* Spårning på systemnivå via Azure RTOS TraceX.

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a>ETHERNET, WiFi, BLUETOOTH LE, 15.4 osv.

## <a name="interoperability-verification"></a>Interoperabilitetsverifiering

Azure RTOS NetX följer RFC-standarder och erbjuder fullständig samverkan med enheter från de flesta leverantörer. Azure RTOS NetX använder även branschstandarden IxANVL (Automated Network Validation Library) för implementeringen av TCP/IP-protokollet Azure RTOS NetX Core.

## <a name="advanced-technology"></a>Avancerad teknik

Azure RTOS NetX är avancerad teknik som omfattar följande.
* Piconet™arkitektur.
* Automatisk skalning.
* UDP Fast-Path Technology™.
* Flexibel pakethantering.
* API med nollkopiering och implementering.
* Stöd för flera hem.
* Valfri tidsgräns för all låsning.
* Stöd för statisk routning.
* Azure RTOS TraceX-systemanalysstöd.
