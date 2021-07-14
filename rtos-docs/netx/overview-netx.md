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
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="77ed5-103">Översikt över Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="77ed5-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="77ed5-104">Azure RTOS NetX är en inbäddad TCP/IP IPv4-nätverksstack i branschklass som är utformad särskilt för djupt inbäddade program, realtidsprogram och IoT-program.</span><span class="sxs-lookup"><span data-stu-id="77ed5-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="77ed5-105">Azure RTOS NetX är Microsofts ursprungliga IPv4-nätverksstack och är i stort sett en delmängd av Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="77ed5-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="77ed5-106">NetX tillhandahåller inbäddade program med kärnnätverksprotokoll som IPv4, TCP och UDP samt en komplett uppsättning ytterligare tilläggsprotokoll på högre nivå.</span><span class="sxs-lookup"><span data-stu-id="77ed5-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="77ed5-107">Ett litet fotavtryck, snabb körning och överlägsen användarvänlighet gör Azure RTOS NetX till ett perfekt val för de mest krävande inbäddade IoT-programmen.</span><span class="sxs-lookup"><span data-stu-id="77ed5-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="77ed5-108">API-protokoll</span><span class="sxs-lookup"><span data-stu-id="77ed5-108">API protocols</span></span>
<span data-ttu-id="77ed5-109">Azure RTOS NetX har stöd för följande.</span><span class="sxs-lookup"><span data-stu-id="77ed5-109">Azure RTOS NetX provides support for the following.</span></span>

### <a name="telnet"></a><span data-ttu-id="77ed5-110">Telnet</span><span class="sxs-lookup"><span data-stu-id="77ed5-110">TELNET</span></span>

* <span data-ttu-id="77ed5-111">Minimalt RAM-fotavtryck på 0,5 kB och 0,3 KB.</span><span class="sxs-lookup"><span data-stu-id="77ed5-111">Minimal 0.5 KB and 0.3 KB RAM footprint.</span></span>
* <span data-ttu-id="77ed5-112">Stöd för klienter och servrar.</span><span class="sxs-lookup"><span data-stu-id="77ed5-112">Client and server support.</span></span>

### <a name="auto-ip"></a><span data-ttu-id="77ed5-113">Automatisk IP-adress</span><span class="sxs-lookup"><span data-stu-id="77ed5-113">Auto IP</span></span>

* <span data-ttu-id="77ed5-114">Automatisk IPv4-adresstilldelning.</span><span class="sxs-lookup"><span data-stu-id="77ed5-114">Automatic IPv4 address assignment.</span></span>
* <span data-ttu-id="77ed5-115">Minimalt 1,2 kB, 300 byte RAM-minne.</span><span class="sxs-lookup"><span data-stu-id="77ed5-115">Minimal 1.2 KB, 300 bytes of RAM.</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="77ed5-116">HTTP – Hypertext Transfer Protocol(HTTP)</span><span class="sxs-lookup"><span data-stu-id="77ed5-116">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="77ed5-117">Minimalt 2,8 kB till 4,8 kBFLASH, 0,4 kB till 1,0 KB RAM-fotavtryck.</span><span class="sxs-lookup"><span data-stu-id="77ed5-117">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint.</span></span>
* <span data-ttu-id="77ed5-118">Stöd för klienter och servrar.</span><span class="sxs-lookup"><span data-stu-id="77ed5-118">Client and server support.</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="77ed5-119">SMTP – Simple Mail Transfer Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="77ed5-119">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="77ed5-120">Minimalt RAM-fotavtryck på 4,1 kB och 0,6 KB</span><span class="sxs-lookup"><span data-stu-id="77ed5-120">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="77ed5-121">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="77ed5-121">Client support</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="77ed5-122">DHCP – Dynamic Host Configuration Protocol (DHCP)</span><span class="sxs-lookup"><span data-stu-id="77ed5-122">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="77ed5-123">Minimalt 3,6 KB till 4,6 KB FLASH, 2,7 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="77ed5-123">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="77ed5-124">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="77ed5-124">Client and server support</span></span>
* <span data-ttu-id="77ed5-125">Stöd för IPv4</span><span class="sxs-lookup"><span data-stu-id="77ed5-125">IPv4 support</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="77ed5-126">P0P3 – Efter Office Protocol Version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="77ed5-126">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="77ed5-127">Minimalt RAM-fotavtryck på 8,1 kB och 1,4 KB</span><span class="sxs-lookup"><span data-stu-id="77ed5-127">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="77ed5-128">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="77ed5-128">Client support</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="77ed5-129">SNMP – Simple Network Management Protocol (SNMP)</span><span class="sxs-lookup"><span data-stu-id="77ed5-129">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="77ed5-130">Minimalt RAM-fotavtryck på 10,9 kB och 2,6 KB</span><span class="sxs-lookup"><span data-stu-id="77ed5-130">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="77ed5-131">Agentstöd för VI, V2 och V3</span><span class="sxs-lookup"><span data-stu-id="77ed5-131">Agent support for VI, V2, and V3</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="77ed5-132">FTP, TFTP – File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span><span class="sxs-lookup"><span data-stu-id="77ed5-132">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="77ed5-133">FTP minimalt 1,8 kB till 7,2 kBFLASH, 0,6 kB till 2,1 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="77ed5-133">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="77ed5-134">TFTP Minimalt 1,7 kB till 2,4 kBFLASH, 0,3 kB till 1,8 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="77ed5-134">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="77ed5-135">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="77ed5-135">Client and server support</span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="77ed5-136">PPP – Polnt-to-PoInt Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="77ed5-136">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="77ed5-137">Minimalt RAM-fotavtryck på 7,1 kB och 3,8 KB</span><span class="sxs-lookup"><span data-stu-id="77ed5-137">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="77ed5-138">Pålitlig och tillförlitlig.</span><span class="sxs-lookup"><span data-stu-id="77ed5-138">Dependable and reliable.</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="77ed5-139">SNTP – Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="77ed5-139">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="77ed5-140">Minimalt 4 KB och 0,5 KB RAM</span><span class="sxs-lookup"><span data-stu-id="77ed5-140">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="77ed5-141">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="77ed5-141">Client support</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="77ed5-142">Azure RTOS NetX API</span><span class="sxs-lookup"><span data-stu-id="77ed5-142">Azure RTOS NetX API</span></span>

* <span data-ttu-id="77ed5-143">Snabb IMPLEMENTERING av API:et nollkopiering</span><span class="sxs-lookup"><span data-stu-id="77ed5-143">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="77ed5-144">Valfritt BSD-lager för portning av äldre socketkod</span><span class="sxs-lookup"><span data-stu-id="77ed5-144">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="77ed5-145">IGMP – Internet Group Management Protocol (IGMP)</span><span class="sxs-lookup"><span data-stu-id="77ed5-145">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="77ed5-146">Minimal 2,5 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="77ed5-146">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="77ed5-147">Stöd för IPv4-multicast-grupper</span><span class="sxs-lookup"><span data-stu-id="77ed5-147">IPv4 multicast group support</span></span>
* <span data-ttu-id="77ed5-148">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="77ed5-148">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="77ed5-149">Valfri IGMP-statistik</span><span class="sxs-lookup"><span data-stu-id="77ed5-149">Optional IGMP statistics</span></span>
* <span data-ttu-id="77ed5-150">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="77ed5-150">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="77ed5-151">UDP – UDP (User Datagram Protocol)</span><span class="sxs-lookup"><span data-stu-id="77ed5-151">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="77ed5-152">Minimal 2,5 KB FLASH, 124 sockets byte RAM-minne per socket</span><span class="sxs-lookup"><span data-stu-id="77ed5-152">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="77ed5-153">Snabb, nära trådad TCP-paketbearbetning:</span><span class="sxs-lookup"><span data-stu-id="77ed5-153">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="77ed5-154">RX 95 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 14 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="77ed5-154">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="77ed5-155">TX 94 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 10 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="77ed5-155">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="77ed5-156">UDP Fast Path™teknik</span><span class="sxs-lookup"><span data-stu-id="77ed5-156">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="77ed5-157">Inga gränser för antalet UDP</span><span class="sxs-lookup"><span data-stu-id="77ed5-157">No limits on the number of UDP</span></span>
* <span data-ttu-id="77ed5-158">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="77ed5-158">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="77ed5-159">Valfri stängning vid socket-mottagning</span><span class="sxs-lookup"><span data-stu-id="77ed5-159">Optional suspension on socket receive</span></span>
* <span data-ttu-id="77ed5-160">Valfri tidsgräns för all låsning</span><span class="sxs-lookup"><span data-stu-id="77ed5-160">Optional timeout on all suspension</span></span>
* <span data-ttu-id="77ed5-161">Valfri UDP-statistik</span><span class="sxs-lookup"><span data-stu-id="77ed5-161">Optional UDP statistics</span></span>
* <span data-ttu-id="77ed5-162">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="77ed5-162">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="77ed5-163">TCP – Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="77ed5-163">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="77ed5-164">Minimal 10,5K8 till 12,5 KB FLASH, 280 byte RAM-minne per socket</span><span class="sxs-lookup"><span data-stu-id="77ed5-164">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="77ed5-165">Snabb, nästan wlre tcp-paketbearbetning:</span><span class="sxs-lookup"><span data-stu-id="77ed5-165">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="77ed5-166">RX 93 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 20 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="77ed5-166">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="77ed5-167">TX 94 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 27 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="77ed5-167">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="77ed5-168">Tillförlitlig anslutning</span><span class="sxs-lookup"><span data-stu-id="77ed5-168">Reliable connection</span></span>
* <span data-ttu-id="77ed5-169">Inga gränser för antalet TCP-sockets</span><span class="sxs-lookup"><span data-stu-id="77ed5-169">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="77ed5-170">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="77ed5-170">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="77ed5-171">Valfri stängning vid socket-mottagning/-överföring</span><span class="sxs-lookup"><span data-stu-id="77ed5-171">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="77ed5-172">Valfri tidsgräns för all låsning</span><span class="sxs-lookup"><span data-stu-id="77ed5-172">Optional timeout on all suspension</span></span>
* <span data-ttu-id="77ed5-173">Valfri TCP-statistik</span><span class="sxs-lookup"><span data-stu-id="77ed5-173">Optional TCP statistics</span></span>
* <span data-ttu-id="77ed5-174">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="77ed5-174">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="77ed5-175">ICMP – Internet Control Message Protocol (ICMP)</span><span class="sxs-lookup"><span data-stu-id="77ed5-175">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="77ed5-176">Minimal 2,5 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="77ed5-176">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="77ed5-177">Stöd för IPv4</span><span class="sxs-lookup"><span data-stu-id="77ed5-177">IPv4 support</span></span>
* <span data-ttu-id="77ed5-178">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="77ed5-178">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="77ed5-179">Pingbegäran och pingsvar</span><span class="sxs-lookup"><span data-stu-id="77ed5-179">Ping request and ping response</span></span>
* <span data-ttu-id="77ed5-180">Valfri trådavstängning vid pingbegäranden</span><span class="sxs-lookup"><span data-stu-id="77ed5-180">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="77ed5-181">Valfri tidsgräns för all låsning</span><span class="sxs-lookup"><span data-stu-id="77ed5-181">Optional timeout on all suspension</span></span>
* <span data-ttu-id="77ed5-182">Valfri ICMP-statistik</span><span class="sxs-lookup"><span data-stu-id="77ed5-182">Optional ICMP statistics</span></span>
* <span data-ttu-id="77ed5-183">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="77ed5-183">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="77ed5-184">IPv4 – Internet Protocol (IP)</span><span class="sxs-lookup"><span data-stu-id="77ed5-184">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="77ed5-185">Minimalt 3,5 KB till 8,5 KB FLASH, 2 KB till 3 KB RAM-fotavtryck.</span><span class="sxs-lookup"><span data-stu-id="77ed5-185">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint.</span></span>
* <span data-ttu-id="77ed5-186">Piconet™Arkitektur.</span><span class="sxs-lookup"><span data-stu-id="77ed5-186">Piconet™ Architecture.</span></span>
* <span data-ttu-id="77ed5-187">Snabb, nästan trådig prestanda.</span><span class="sxs-lookup"><span data-stu-id="77ed5-187">Fast, near wirespeed performance.</span></span>
* <span data-ttu-id="77ed5-188">Stöd för flera gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="77ed5-188">Multiple interface support.</span></span>
* <span data-ttu-id="77ed5-189">Stöd för flera hem.</span><span class="sxs-lookup"><span data-stu-id="77ed5-189">Multi-homed support.</span></span>
* <span data-ttu-id="77ed5-190">Stöd för statisk routning.</span><span class="sxs-lookup"><span data-stu-id="77ed5-190">Static routing support.</span></span>
* <span data-ttu-id="77ed5-191">Stöd för IP-fragmentering/återmontering.</span><span class="sxs-lookup"><span data-stu-id="77ed5-191">IP fragmentation/reassembly support.</span></span>
* <span data-ttu-id="77ed5-192">IPv4-stöd.</span><span class="sxs-lookup"><span data-stu-id="77ed5-192">IPv4 Support.</span></span>
* <span data-ttu-id="77ed5-193">IXIA IxANVL Validated.</span><span class="sxs-lookup"><span data-stu-id="77ed5-193">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="77ed5-194">Fas II– redo logotypcertifiering.</span><span class="sxs-lookup"><span data-stu-id="77ed5-194">Phase II Ready Logo Certification.</span></span>
* <span data-ttu-id="77ed5-195">Valfri IP-statistik.</span><span class="sxs-lookup"><span data-stu-id="77ed5-195">Optional IP statistics.</span></span>
* <span data-ttu-id="77ed5-196">Väldefinierat, intuitivt drivrutinsgränssnitt på fysiskt lager.</span><span class="sxs-lookup"><span data-stu-id="77ed5-196">Well defined, intuitive physical layer driver interface.</span></span>
* <span data-ttu-id="77ed5-197">Spårning på systemnivå via Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="77ed5-197">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="77ed5-198">ARP/RARP – Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span><span class="sxs-lookup"><span data-stu-id="77ed5-198">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="77ed5-199">Minimal 1,7 KB FLASH, RAM-storlek.</span><span class="sxs-lookup"><span data-stu-id="77ed5-199">Minimal 1.7 KB FLASH, RAM size.</span></span>
* <span data-ttu-id="77ed5-200">Dynamisk upplösning av 32-blt IPv4- och 48-blt MAC-adresser.</span><span class="sxs-lookup"><span data-stu-id="77ed5-200">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses.</span></span>
* <span data-ttu-id="77ed5-201">IXIA IxANVL Validated.</span><span class="sxs-lookup"><span data-stu-id="77ed5-201">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="77ed5-202">Flexibel, användardefinierad ARP-cache.</span><span class="sxs-lookup"><span data-stu-id="77ed5-202">Flexible, user-defined ARP cache.</span></span>
* <span data-ttu-id="77ed5-203">Bra ARP-stöd.</span><span class="sxs-lookup"><span data-stu-id="77ed5-203">Gratuitous ARP support.</span></span>
* <span data-ttu-id="77ed5-204">Valfri ARP/RARP-statistik som bestäms av programmet.</span><span class="sxs-lookup"><span data-stu-id="77ed5-204">Optional ARP/RARP statistics determined by application.</span></span>
* <span data-ttu-id="77ed5-205">Spårning på systemnivå via Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="77ed5-205">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="77ed5-206">ETHERNET, WiFi, BLUETOOTH LE, 15.4 osv.</span><span class="sxs-lookup"><span data-stu-id="77ed5-206">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="77ed5-207">Interoperabilitetsverifiering</span><span class="sxs-lookup"><span data-stu-id="77ed5-207">Interoperability verification</span></span>

<span data-ttu-id="77ed5-208">Azure RTOS NetX följer RFC-standarder och erbjuder fullständig samverkan med enheter från de flesta leverantörer.</span><span class="sxs-lookup"><span data-stu-id="77ed5-208">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices from most vendors.</span></span> <span data-ttu-id="77ed5-209">Azure RTOS NetX använder även branschstandarden IxANVL (Automated Network Validation Library) för implementeringen av TCP/IP-protokollet Azure RTOS NetX Core.</span><span class="sxs-lookup"><span data-stu-id="77ed5-209">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="77ed5-210">Avancerad teknik</span><span class="sxs-lookup"><span data-stu-id="77ed5-210">Advanced technology</span></span>

<span data-ttu-id="77ed5-211">Azure RTOS NetX är avancerad teknik som omfattar följande.</span><span class="sxs-lookup"><span data-stu-id="77ed5-211">Azure RTOS NetX is advanced technology that includes the following.</span></span>
* <span data-ttu-id="77ed5-212">Piconet™arkitektur.</span><span class="sxs-lookup"><span data-stu-id="77ed5-212">Piconet™ architecture.</span></span>
* <span data-ttu-id="77ed5-213">Automatisk skalning.</span><span class="sxs-lookup"><span data-stu-id="77ed5-213">Automatic scaling.</span></span>
* <span data-ttu-id="77ed5-214">UDP Fast-Path Technology™.</span><span class="sxs-lookup"><span data-stu-id="77ed5-214">UDP Fast-Path Technology™.</span></span>
* <span data-ttu-id="77ed5-215">Flexibel pakethantering.</span><span class="sxs-lookup"><span data-stu-id="77ed5-215">Flexible packet management.</span></span>
* <span data-ttu-id="77ed5-216">API med nollkopiering och implementering.</span><span class="sxs-lookup"><span data-stu-id="77ed5-216">Zero-copy API and implementation.</span></span>
* <span data-ttu-id="77ed5-217">Stöd för flera hem.</span><span class="sxs-lookup"><span data-stu-id="77ed5-217">Multi-homed support.</span></span>
* <span data-ttu-id="77ed5-218">Valfri tidsgräns för all låsning.</span><span class="sxs-lookup"><span data-stu-id="77ed5-218">Optional timeout on all suspension.</span></span>
* <span data-ttu-id="77ed5-219">Stöd för statisk routning.</span><span class="sxs-lookup"><span data-stu-id="77ed5-219">Static routing support.</span></span>
* <span data-ttu-id="77ed5-220">Azure RTOS TraceX-systemanalysstöd.</span><span class="sxs-lookup"><span data-stu-id="77ed5-220">Azure RTOS TraceX system analysis support.</span></span>
