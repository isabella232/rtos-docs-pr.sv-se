---
title: Förstå Azure RTOS NetX Duo
description: Azure RTOS NetX Duo är en avancerad TCP/IP-nätverksstack i branschklass som är speciellt utformad för djupt inbäddade realtids- och IoT-program.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 6112ab5cb711ca1a5c83fd5cd4b43abc0302c6c5
ms.sourcegitcommit: f9d8cf23becf96d5bd6d31dd54f89c48962fd09b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549346"
---
# <a name="overview-of-azure-rtos-netx-duo"></a>Översikt över Azure RTOS NetX Duo

Azure RTOS Inbäddad TCP/IP-nätverksstack i NetX Duo är Microsofts avancerade, industriella klass med dubbla IPv4- och IPv6 TCP/IP-nätverksstackar som är särskilt utformade för djupt inbäddade, realtids- och IoT-program. NetX Duo tillhandahåller inbäddade program med kärnnätverksprotokoll som IPv4, IPv6, TCP och UDP samt en komplett uppsättning ytterligare protokoll på högre nivå. Azure RTOS NetX Duo erbjuder säkerhet via ytterligare tillägg säkerhetsprodukter, inklusive Azure RTOS NetX Secure IPsec och Azure RTOS NetX Secure SSL/TLS/DTLS. Allt detta i kombination med ett litet fotavtryck, snabb körning och överlägsen användarvänlighet gör Azure RTOS NetX Duo till det perfekta valet för de mest krävande inbäddade IoT-programmen.

## <a name="api-protocols"></a>API-protokoll

### <a name="mqtt"></a>MQTT

* MQTT (Messaging Queue Telemetry Transport)
* Minimal 2,7 KB FLASH

### <a name="auto-ip"></a>Automatisk IP-adress

* Automatisk IPv4-adresstilldelning
* Minimalt 1,2 kB, 300 byte RAM-minne

### <a name="http-https"></a>HTTP, HTTPS

#### <a name="http-10"></a>HTTP 1.0

* Hypertext Transfer Protocol(HTTP)
* Minimalt 2,8 KB till 4,8 KB FLASH/0,4 KB till 1,0 KB RAM-minne
* Stöd för klienter och servrar

#### <a name="httphttps-11"></a>HTTP/HTTPS 1.1

* Hypertext Transfer Protocol(HTTP)
* Minimalt 3,0 KB till 9,5 KB FLASH/0,5 KB till 2 KB RAM
* Stöd för klienter och servrar
* Flera inkommande klientsessioner
* Oformaterad text och krypterad HTTPS
* Stöd för beständiga anslutningar
* Filuppladdning med flera delar
* Helt integrerad med Azure RTOS NetX Secure TLS

### <a name="smtp"></a>SMTP

* Simple Mall Transfer Protocol (SMTP)
* Minimalt RAM-fotavtryck på 4,1 kB och 0,6 KB
* Klientstöd

### <a name="dhcp"></a>DHCP

* DHCP (Dynamic Host Configuration Protocol)
* Minimalt 3,6 kB till 4,6 KB FLASH, 2,7 KB RAM-fotavtryck
* Stöd för klienter och servrar
* Stöd för IPv4 och IPv6

### <a name="nat"></a>NAT

* NAT (Network Address Translation)
* Minimalt RAM-fotavtryck på 3,5 K6 och 0,6 KB
* Stöd för IPv4-adresser
* NAT är endast tillgängligt med Azure RTOS NetX Duo

### <a name="snmp"></a>SNMP

* Simple Network Management Protocol (SNMP)
* Minimalt RAM-fotavtryck på 10,9 kB och 2,6 KB
* Agentstöd för VI, V2 och V3

### <a name="dns-mdns-dns-sd"></a>DNS, mDNS, DNS-SD

* DNS (Domain Name System)
* Multicast Domain Name System (mDNS)
* DNS-baserad tjänstidentifiering (DNS-SD)
* DNS Minimalt 2,4 KB till 3 KB FLASH, 1 KB RAM-fotavtryck
* Klientstöd
* mDNS och DNS-SD är endast tillgängliga med Azure RTOS NetX Duo

### <a name="pop3"></a>POP3

* Post Office Protocol Version 3 (POP3)
* Minimalt RAM-fotavtryck på 8,1 kB och 1,4 KB
* Klientstöd

### <a name="telnet"></a>Telnet

* Minimalt RAM-fotavtryck på 0,5 kB och 0,3 KB
* Stöd för klienter och servrar
* Intuitiva Telnet-API:er: *nx_telnet_ \**

### <a name="ftp-tftp"></a>FTP, TFTP

* File Transfer Protocol (FTP)
* Trivial file transfer protocol (TFTP)
* FTP minimalt 1,8 KB till 7,2 KB FLASH, 0,6 kB till 2,1 KB RAM-fotavtryck
* TFTP Minimal 1,7 KB till 2,4 KB FLASH, 0,3 kB till 1,8 KB RAM-fotavtryck
* Stöd för klienter och servrar
* Intuitiva FTP- och *TFTP-API:er: \* nx_ftp_* eller *\* nx_tftp_*

### <a name="ppp-pppoe"></a>PPP, PPPoE

* Polnt-to-PoInt Protocol (PPP)
* Point-to-Point Protocol over Ethernet(PPPoE)
* Minimalt RAM-fotavtryck på 7,1 kB och 3,8 KB
* Intuitiva PPP-API:er: *nx_ppp_ \**

* PPPoE är endast tillgängligt med Azure RTOS NetX Duo

### <a name="sntp"></a>Sntp

* Simple Network Time Protocol (SNTP)
* Minimalt 4 KB och 0,5 KB RAM
* Klientstöd
* Intuitiva SNTP-API:er: *nx_sntp_ \**

### <a name="azure-rtos-netx-duo-api"></a>Azure RTOS NetX Duo API

* Intuitivt och konsekvent API
* Namngivningskonvention för substantiv-verb
* Snabb IMPLEMENTERING av API:et nollkopiering
* Alla API:er har ledande <i>nx_*</i> för att enkelt identifiera som Azure RTOS NetX
* Blockerande API:er har valfri tidsgräns för tråd
* Mer Azure RTOS finns i användarhandboken för [NetX Duo](about-this-guide.md)
* Valfritt BSD-lager för portning av äldre socketkod

### <a name="igmp"></a>Igmp

* Internet Grupphanteringsprotokoll (IGMP)
* Minimal 2,5 KB FLASH
* Stöd för IPv4-multicast-grupper
* IXIA IxANVL-verifierad
* Valfri IGMP-statistik
* Spårning på systemnivå via Azure RTOS ThreadX
* Intuitiva IGMP-API:er: *nx_igmp_ \**

### <a name="azure-rtos-netx-secure-dtls"></a>Azure RTOS NetX Secure DTLS

* Datagram Transport Layer Security (DTLS) 1.0 och 1.2
* Minimalt 11 KB FLASH
* Snabb, programvara RSA 2048-bitars nyckelstorlek ~ 1 sekund @120MHz
* Effektiviserad X.509-implementering
* Helt integrerad med Azure RTOS NetX Duo UDP-sockets
* Stöd för maskinvarukryptutor
* Stöd för kryptografiprogram: RSA (alla nyckelstorlekar), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* Elliptic Curve Cryptography (ECC) med ECDSA (signering) och ECDH (kryptering), inklusive P-kurvor 192/224/256/384/521
* Stöd för krypterad nyckel (maskinvaruberoende)

### <a name="azure-rtos-netx-secure-tls"></a>Azure RTOS NetX Secure TLS

* Transport Layer Security (TLS) 1.0, 1.1 och 1.2
* Minimal 8,8 KB FLASH
* Snabb RSA 2048-bitars nyckelstorlek för programvara ~ 1 sekund @120MHz
* Effektiviserad X.509-implementering
* Helt integrerad med Azure RTOS NetX Duo TCP-sockets
* Stöd för maskinvarukryptutor
* Stöd för kryptografiprogram: RSA (alla nyckelstorlekar), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* Elliptic Curve Cryptography (ECC) med ECDSA (signering) och ECDH (kryptering), inklusive P-kurvor 192/224/256/384/521
* Stöd för krypterad nyckel (maskinvaruberoende)

### <a name="icmp"></a>ICMP

* Internet Control Message Protocol (ICMP)
* Minimal 2,5 KB FLASH
* Stöd för IPv4 och IPv6
* IXIA IxANVL-verifierad
* Pingbegäran och pingsvar
* Valfri trådavstängning vid ping-begäranden
* Valfri tidsgräns vid all låsning
* Valfri ICMP-statistik
* Spårning på systemnivå via Azure RTOS TraceX
* Intuitiva ICMP-API:er: *nx_icmp_ \**

### <a name="udp"></a>UDP

* UDP (User Datagram Protocol)
* Minimalt 2,5 KB FLASH, 124 sockets byte RAM-minne per socket
* Snabb TCP-paketbearbetning med nära wire speed:
    * RX 95 Mbit/s på 100 Mbit/s Ethernet, @100MHz MCU, 14 % MCU-användning
    * TX 94 Mbit/s på 100 Mbit/s Ethernet, @100MHz MCU, 10 % MCU-användning
* UDP Fast Path™teknik
* Inga gränser för antalet UDP
* IXIA IxANVL-verifierad
* Valfri stängning vid socket-mottagning
* Valfri tidsgräns vid all låsning
* Valfri UDP-statistik
* Spårning på systemnivå via Azure RTOS TraceX
* Intuitiva UDP-API:er: *nx_udp_ \**

### <a name="tcp"></a>TCP

* Transmission Control Protocol (TCP)
* Minimal 10,5K8 till 12,5 KB FLASH, 280 byte RAM-minne per socket
* Snabb, nära wlre speed TCP-paketbearbetning:
    * RX 93 Mbit/s på 100 Mbit/s Ethernet, @100MHz MCU, 20 % MCU-användning
    * TX 94 Mbit/s på 100 Mbit/s Ethernet, @100MHz MCU, 27 % MCU-användning
* Tillförlitlig anslutning
* Inga gränser för antalet TCP-socketar
* IXIA IxANVL-verifierad
* Valfri stängning vid socket-mottagning/-överföring
* Valfri tidsgräns vid all låsning
* Valfri TCP-statistik
* Spårning på systemnivå via Azure RTOS TraceX
* Intuitiva TCP-API:er: *nx_tcp_ \**

### <a name="arprarp"></a>ARP/RARP

* Address Resolution Protocol (ARP)
* Reverse Address Resolution Protocol (RARP)
* Minimal 1,7 KB FLASH, RAM-storlek
* Dynamisk upplösning av 32-blt IPv4- och 48-blt MAC-adresser
* IXIA IxANVL-verifierad
* Flexibel, användardefinierad ARP-cache
* Gratuitous ARP support
* Valfri ARP/RARP-statistik som bestäms av programmet
* Spårning på systemnivå via Azure RTOS TraceX
* Intuitiva ARP/RARP-API:nx_arp_ *\**, *\* nx_rarp_*

### <a name="ipv4-amp-ipv6"></a>IPv4 &amp; IPv6

* Internet Protocol (IP)
* Minimal 3,5 kB till 8,5 KB FLASH, 2 KB till 3 KB RAM-fotavtryck
* Piconet™arkitektur
* Snabba, nära wire speed-prestanda
* Stöd för flera gränssnitt
* Stöd för flera start
* Stöd för statisk routning
* Stöd för IP-fragmentering/återmontering
* Stöd för IPv4- och IPv6-adresser
* IXIA IxANVL-verifierad
* Fas II IPv6 Ready Logo Certification (IPv6-redo logotypcertifiering)
* Valfri IP-statistik
* Väldefinierat, intuitivt drivrutinsgränssnitt på fysiskt lager
* Spårning på systemnivå via Azure RTOS TraceX
* Intuitiva API:er för *IP-lager: \* nx_ip_*, *nxd_ip_ \** *\** , nxd_ipv6_
* Förcertifierat av TUV och UL till IEC 61508 SIL 4, IEC 62304 Klass C, ISO 26262 ASIL D och EN 50128 SW-SIL4

### <a name="azure-rtos-netx-secure-ipsec"></a>Azure RTOS NetX Secure IPSEC

* Internet Protocol Security (IPSEC)
* IP-lager
* Stöd för maskinvarukryptutor
* Stöd för kryptografiprogram, inklusive:
    * DES, 3DES
    * AES
    * HMAC-MD5
    * HMAC-SHA1
* Stöd för Internet Key Exchange (IKE) Version 2
* Intuitiva IPsec-API:er: *nx_ipsec_ \**
* IPsec är endast tillgängligt med Azure RTOS NetX Duo

## <a name="safe-and-secure"></a>Valv och säkert

Azure RTOS NetX Duo är säker. Den här säkerheten tillhandahålls via tilläggssäkerhetsprodukter, inklusive IPsec, SSL, TLS och DTLS. Dessutom har programmet fullständig kontroll över all extern åtkomst till Azure RTOS NetX Duo, vilket gör det mycket enklare att fastställa säkerhetsrisker.

Microsoft Azure RTOS tillhandahåller OEM-tillverkare med komponenter för säker kommunikation och för att skapa kod- och dataisolering med underliggande MCU/MPU-maskinvaruskyddsmekanismer. Det är i slutänden enhetsbyggarens ansvar att se till att enheten uppfyller de föränderliga säkerhetskrav som är associerade med dess specifika användningsfall.


## <a name="interoperability-verification"></a>Interoperabilitetsverifiering

NetX Duo följer RFC-standarder och erbjuder fullständig samverkan med enheter för de flesta leverantörer.

![Logotyp för IPv6-klar](./media/overview-netx-duo/ipv6-ready-logo.png)

Azure RTOS NetX Duo är en av de enda inbäddade TCP/IP-stackarna för att uppnå rigorös IPv6-Ready Logo-certifiering, bevis på att den har klarat överensstämmelse- och samverkanstester som administreras och verifierats av IPv6-forumet. NetX Duo använder också branschstandarden IxANVL (Automated Network Validation Library) för netX Duo-kärnimplementeringen av TCP/IP-protokollet.

## <a name="comprehensive-iot-solution"></a>Omfattande IoT-lösning

NetX Duo har ett av de mest omfattande TCP/IP-nätverken för djupt inbäddade IoT-program. Det här stödet omfattar följande tillägg protokollprodukter.

MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP

## <a name="advanced-technology"></a>Avancerad teknik

Azure RTOS NetX Duo är avancerad teknik som omfattar:

* Piconet™arkitektur
* Automatisk skalning
* UDP Fast-Path Technology™
* Flexibel pakethantering
* API med nollkopiering och implementering
* Stöd för flera start
* Valfri tidsgräns vid all låsning
* Stöd för statisk routning
* IPsec
* SSL/TLS/DTLS
* Azure RTOS traceX-systemanalysstöd

## <a name="related-services"></a>Relaterade tjänster

### <a name="azure-iot"></a>Azure IoT

NetX Duo innehåller [Azure IoT Middleware för Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), ett plattformsspecifikt bibliotek som fungerar som ett bindningslager mellan Azure RTOS och Azure SDK för Embedded C för att underlätta anslutningen till Azure IoT-tjänster. Målen med Azure IoT Middleware är följande.
* Tillhandahåll de smarta klientgränssnitt (IoTHub_Client, DeviceProvisioning_Client) som utvecklare behöver för sina program.
* Samordna interaktionen mellan Embedded C SDK och plattformen.
* Tillhandahåll Azure RTOS plattformsinitiering.
* IoT Plug and Play support.
* Säkerhetsfunktioner.
* Resursbegränsningsmedveten.
* Protokollstöd.

![Azure RTOS NetX Duo Related Services](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a>Azure Defender

Säkerhetsmodulen Azure Defender for IoT innehåller en omfattande säkerhetslösning för Azure RTOS enheter. Säkerhetsmodulen för Azure RTOS erbjuder identifiering av aktiviteter i skadliga nätverk, anpassade aviseringsbaserade enhetsbeteenden som baserar sig på och hjälper till att förbättra enhetens säkerhetshygien. Läs mer om [säkerhetsmodulen för Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) eller kom igång med [snabbstarten Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) (Konfigurera säkerhetsmodul för Azure RTOS).

### <a name="device-update-for-iot-hub"></a>Enhetsuppdatering för IoT Hub

[Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) är en tjänst som gör att du kan distribuera trådlösa uppdateringar (OTA) för dina IoT-enheter. Modulen Enhetsuppdatering för IoT Hub är implementeringen av Enhetsuppdatering för IoT Hub Agent i Azure RTOS NetX Duo. Den innehåller enkla API:er som gör att enhetsbyggare kan integrera funktionen Enhetsuppdatering i sina program.

Se exempel på viktiga utvärderingstavlor som innehåller kom igång-guiderna för att lära dig att konfigurera, bygga och distribuera trådlösa uppdateringar (OTA) till enheterna.

Du kan också läsa mer om hur du [använder Enhetsuppdatering för IoT Hub med Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).

## <a name="next-steps"></a>Nästa steg

Om du vill veta mer om NetX Duo börjar du [med Azure RTOS användarhandbok för NetX Duo.](about-this-guide.md)
