---
title: Förstå Azure RTOS NetX
description: Azure RTOS NetX är en högpresterande implementering av TCP/IP-protokollstandarder, helt integrerad med Azure RTOS ThreadX och tillgänglig för alla processorer som stöds.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 7c864c23f019e4841ddb3096fde663c8039baf44
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171326"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="afbb7-103">Översikt över Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="afbb7-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="afbb7-104">Azure RTOS NetX är en inbäddad TCP/IP IPv4-nätverksstack i branschklass som utformats särskilt för djupt inbäddade, realtidsbaserade och IoT-program.</span><span class="sxs-lookup"><span data-stu-id="afbb7-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="afbb7-105">Azure RTOS NetX är Microsofts ursprungliga IPv4-nätverksstack och är i grunden en delmängd av Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="afbb7-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="afbb7-106">NetX tillhandahåller inbäddade program med kärnnätverksprotokoll som IPv4, TCP och UDP samt en komplett uppsättning ytterligare tilläggsprotokoll på högre nivå.</span><span class="sxs-lookup"><span data-stu-id="afbb7-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="afbb7-107">Ett litet fotavtryck, snabb körning och överlägsen användarvänlighet gör Azure RTOS NetX till ett perfekt val för de mest krävande inbäddade IoT-programmen.</span><span class="sxs-lookup"><span data-stu-id="afbb7-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="afbb7-108">API-protokoll</span><span class="sxs-lookup"><span data-stu-id="afbb7-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="afbb7-109">Telnet</span><span class="sxs-lookup"><span data-stu-id="afbb7-109">TELNET</span></span>

* <span data-ttu-id="afbb7-110">Minimalt RAM-fotavtryck på 0,5 kB och 0,3 KB.</span><span class="sxs-lookup"><span data-stu-id="afbb7-110">Minimal 0.5 KB and 0.3 KB RAM footprint.</span></span>
* <span data-ttu-id="afbb7-111">Stöd för klient och server.</span><span class="sxs-lookup"><span data-stu-id="afbb7-111">Client and server support.</span></span>

### <a name="auto-ip"></a><span data-ttu-id="afbb7-112">Automatisk IP-adress</span><span class="sxs-lookup"><span data-stu-id="afbb7-112">Auto IP</span></span>

* <span data-ttu-id="afbb7-113">Automatisk IPv4-adresstilldelning.</span><span class="sxs-lookup"><span data-stu-id="afbb7-113">Automatic IPv4 address assignment.</span></span>
* <span data-ttu-id="afbb7-114">Minimalt 1,2 kB, 300 byte RAM-minne.</span><span class="sxs-lookup"><span data-stu-id="afbb7-114">Minimal 1.2 KB, 300 bytes of RAM.</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="afbb7-115">HTTP – Hypertext Transfer Protocol(HTTP)</span><span class="sxs-lookup"><span data-stu-id="afbb7-115">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="afbb7-116">Minimalt RAM-fotavtryck på 2,8 kB till 4,8 kB, 0,4 kB till 1,0 kB RAM-fotavtryck.</span><span class="sxs-lookup"><span data-stu-id="afbb7-116">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint.</span></span>
* <span data-ttu-id="afbb7-117">Stöd för klient och server.</span><span class="sxs-lookup"><span data-stu-id="afbb7-117">Client and server support.</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="afbb7-118">SMTP – Simple Mail Transfer Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="afbb7-118">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="afbb7-119">Minimalt RAM-fotavtryck på 4,1 kB och 0,6 kB</span><span class="sxs-lookup"><span data-stu-id="afbb7-119">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="afbb7-120">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="afbb7-120">Client support</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="afbb7-121">DHCP – Dynamic Host Configuration Protocol (DHCP)</span><span class="sxs-lookup"><span data-stu-id="afbb7-121">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="afbb7-122">Minimalt 3,6 kB till 4,6 KB FLASH, 2,7 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="afbb7-122">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="afbb7-123">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="afbb7-123">Client and server support</span></span>
* <span data-ttu-id="afbb7-124">IPv4-stöd</span><span class="sxs-lookup"><span data-stu-id="afbb7-124">IPv4 support</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="afbb7-125">P0P3 – Post Office Protocol version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="afbb7-125">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="afbb7-126">Minimalt RAM-fotavtryck på 8,1 kB och 1,4 KB</span><span class="sxs-lookup"><span data-stu-id="afbb7-126">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="afbb7-127">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="afbb7-127">Client support</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="afbb7-128">SNMP – Simple Network Management Protocol (SNMP)</span><span class="sxs-lookup"><span data-stu-id="afbb7-128">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="afbb7-129">Minimalt RAM-fotavtryck på 10,9 kB och 2,6 KB</span><span class="sxs-lookup"><span data-stu-id="afbb7-129">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="afbb7-130">Agentstöd för VI, V2 och V3</span><span class="sxs-lookup"><span data-stu-id="afbb7-130">Agent support for VI, V2, and V3</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="afbb7-131">FTP, TFTP – File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span><span class="sxs-lookup"><span data-stu-id="afbb7-131">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="afbb7-132">FTP minimalt 1,8 kB till 7,2 kBFLASH, 0,6 kB till 2,1 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="afbb7-132">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="afbb7-133">TFTP Minimalt 1,7 kB till 2,4 kBFLASH, 0,3 kB till 1,8 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="afbb7-133">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="afbb7-134">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="afbb7-134">Client and server support</span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="afbb7-135">PPP – Polnt-to-PoInt Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="afbb7-135">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="afbb7-136">Minimalt RAM-fotavtryck på 7,1 kB och 3,8 KB</span><span class="sxs-lookup"><span data-stu-id="afbb7-136">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="afbb7-137">Pålitlig och tillförlitlig.</span><span class="sxs-lookup"><span data-stu-id="afbb7-137">Dependable and reliable.</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="afbb7-138">SNTP – Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="afbb7-138">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="afbb7-139">Minimalt 4 KB och 0,5 KB RAM</span><span class="sxs-lookup"><span data-stu-id="afbb7-139">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="afbb7-140">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="afbb7-140">Client support</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="afbb7-141">Azure RTOS NetX API</span><span class="sxs-lookup"><span data-stu-id="afbb7-141">Azure RTOS NetX API</span></span>

* <span data-ttu-id="afbb7-142">Snabb IMPLEMENTERING av API med nollkopiering</span><span class="sxs-lookup"><span data-stu-id="afbb7-142">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="afbb7-143">Valfritt BSD-lager för portning av äldre socketkod</span><span class="sxs-lookup"><span data-stu-id="afbb7-143">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="afbb7-144">IGMP – Internet Group Management Protocol (IGMP)</span><span class="sxs-lookup"><span data-stu-id="afbb7-144">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="afbb7-145">Minimal 2,5 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="afbb7-145">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="afbb7-146">Stöd för IPv4-multicast-grupper</span><span class="sxs-lookup"><span data-stu-id="afbb7-146">IPv4 multicast group support</span></span>
* <span data-ttu-id="afbb7-147">Verifierad IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="afbb7-147">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="afbb7-148">Valfri IGMP-statistik</span><span class="sxs-lookup"><span data-stu-id="afbb7-148">Optional IGMP statistics</span></span>
* <span data-ttu-id="afbb7-149">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="afbb7-149">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="afbb7-150">UDP – UDP (User Datagram Protocol)</span><span class="sxs-lookup"><span data-stu-id="afbb7-150">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="afbb7-151">Minimalt 2,5 KB FLASH, 124 sockets byte RAM-minne per socket</span><span class="sxs-lookup"><span data-stu-id="afbb7-151">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="afbb7-152">Snabb TCP-paketbearbetning med nära wire speed:</span><span class="sxs-lookup"><span data-stu-id="afbb7-152">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="afbb7-153">RX 95 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 14 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="afbb7-153">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="afbb7-154">TX 94 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 10 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="afbb7-154">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="afbb7-155">UDP Fast Path™teknik</span><span class="sxs-lookup"><span data-stu-id="afbb7-155">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="afbb7-156">Inga gränser för antalet UDP</span><span class="sxs-lookup"><span data-stu-id="afbb7-156">No limits on the number of UDP</span></span>
* <span data-ttu-id="afbb7-157">Verifierad IXIA IxANVL</span><span class="sxs-lookup"><span data-stu-id="afbb7-157">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="afbb7-158">Valfri stängning vid socket-mottagning</span><span class="sxs-lookup"><span data-stu-id="afbb7-158">Optional suspension on socket receive</span></span>
* <span data-ttu-id="afbb7-159">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="afbb7-159">Optional timeout on all suspension</span></span>
* <span data-ttu-id="afbb7-160">Valfri UDP-statistik</span><span class="sxs-lookup"><span data-stu-id="afbb7-160">Optional UDP statistics</span></span>
* <span data-ttu-id="afbb7-161">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="afbb7-161">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="afbb7-162">TCP – Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="afbb7-162">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="afbb7-163">Minimal 10,5K8 till 12,5 KB FLASH, 280 byte RAM-minne per socket</span><span class="sxs-lookup"><span data-stu-id="afbb7-163">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="afbb7-164">Snabb, nästan wlre tcp-paketbearbetning:</span><span class="sxs-lookup"><span data-stu-id="afbb7-164">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="afbb7-165">RX 93 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 20 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="afbb7-165">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="afbb7-166">TX 94 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 27 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="afbb7-166">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="afbb7-167">Tillförlitlig anslutning</span><span class="sxs-lookup"><span data-stu-id="afbb7-167">Reliable connection</span></span>
* <span data-ttu-id="afbb7-168">Inga gränser för antalet TCP-sockets</span><span class="sxs-lookup"><span data-stu-id="afbb7-168">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="afbb7-169">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="afbb7-169">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="afbb7-170">Valfri uppstängning vid socket-mottagning/-överföring</span><span class="sxs-lookup"><span data-stu-id="afbb7-170">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="afbb7-171">Valfri tidsgräns för all låsning</span><span class="sxs-lookup"><span data-stu-id="afbb7-171">Optional timeout on all suspension</span></span>
* <span data-ttu-id="afbb7-172">Valfri TCP-statistik</span><span class="sxs-lookup"><span data-stu-id="afbb7-172">Optional TCP statistics</span></span>
* <span data-ttu-id="afbb7-173">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="afbb7-173">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="afbb7-174">ICMP – Internet Control Message Protocol (ICMP)</span><span class="sxs-lookup"><span data-stu-id="afbb7-174">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="afbb7-175">Minimal 2,5 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="afbb7-175">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="afbb7-176">IPv4-stöd</span><span class="sxs-lookup"><span data-stu-id="afbb7-176">IPv4 support</span></span>
* <span data-ttu-id="afbb7-177">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="afbb7-177">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="afbb7-178">Pingbegäran och pingsvar</span><span class="sxs-lookup"><span data-stu-id="afbb7-178">Ping request and ping response</span></span>
* <span data-ttu-id="afbb7-179">Valfri trådavstängning vid pingbegäranden</span><span class="sxs-lookup"><span data-stu-id="afbb7-179">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="afbb7-180">Valfri tidsgräns för all låsning</span><span class="sxs-lookup"><span data-stu-id="afbb7-180">Optional timeout on all suspension</span></span>
* <span data-ttu-id="afbb7-181">Valfri ICMP-statistik</span><span class="sxs-lookup"><span data-stu-id="afbb7-181">Optional ICMP statistics</span></span>
* <span data-ttu-id="afbb7-182">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="afbb7-182">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="afbb7-183">IPv4 – Internet Protocol (IP)</span><span class="sxs-lookup"><span data-stu-id="afbb7-183">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="afbb7-184">Minimalt RAM-fotavtryck på 3,5 kB till 8,5 KB FLASH, 2 KB till 3 KB RAM- fotavtryck.</span><span class="sxs-lookup"><span data-stu-id="afbb7-184">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint.</span></span>
* <span data-ttu-id="afbb7-185">Piconet™Arkitektur.</span><span class="sxs-lookup"><span data-stu-id="afbb7-185">Piconet™ Architecture.</span></span>
* <span data-ttu-id="afbb7-186">Snabb, nästan trådhastighetsprestanda.</span><span class="sxs-lookup"><span data-stu-id="afbb7-186">Fast, near wirespeed performance.</span></span>
* <span data-ttu-id="afbb7-187">Stöd för flera gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="afbb7-187">Multiple interface support.</span></span>
* <span data-ttu-id="afbb7-188">Stöd för flera hem.</span><span class="sxs-lookup"><span data-stu-id="afbb7-188">Multi-homed support.</span></span>
* <span data-ttu-id="afbb7-189">Stöd för statisk routning.</span><span class="sxs-lookup"><span data-stu-id="afbb7-189">Static routing support.</span></span>
* <span data-ttu-id="afbb7-190">Stöd för IP-fragmentering/återmontering.</span><span class="sxs-lookup"><span data-stu-id="afbb7-190">IP fragmentation/reassembly support.</span></span>
* <span data-ttu-id="afbb7-191">IPv4-stöd.</span><span class="sxs-lookup"><span data-stu-id="afbb7-191">IPv4 Support.</span></span>
* <span data-ttu-id="afbb7-192">IXIA IxANVL Verifierad.</span><span class="sxs-lookup"><span data-stu-id="afbb7-192">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="afbb7-193">Fas II– redo logotypcertifiering.</span><span class="sxs-lookup"><span data-stu-id="afbb7-193">Phase II Ready Logo Certification.</span></span>
* <span data-ttu-id="afbb7-194">Valfri IP-statistik.</span><span class="sxs-lookup"><span data-stu-id="afbb7-194">Optional IP statistics.</span></span>
* <span data-ttu-id="afbb7-195">Väldefinierat, intuitivt drivrutinsgränssnitt på fysiskt lager.</span><span class="sxs-lookup"><span data-stu-id="afbb7-195">Well defined, intuitive physical layer driver interface.</span></span>
* <span data-ttu-id="afbb7-196">Spårning på systemnivå via Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="afbb7-196">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="afbb7-197">ARP/RARP – Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span><span class="sxs-lookup"><span data-stu-id="afbb7-197">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="afbb7-198">Minimal 1,7 KB FLASH, RAM-storlek.</span><span class="sxs-lookup"><span data-stu-id="afbb7-198">Minimal 1.7 KB FLASH, RAM size.</span></span>
* <span data-ttu-id="afbb7-199">Dynamisk upplösning av 32-blt IPv4- och 48-blt MAC-adresser.</span><span class="sxs-lookup"><span data-stu-id="afbb7-199">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses.</span></span>
* <span data-ttu-id="afbb7-200">IXIA IxANVL Verifierad.</span><span class="sxs-lookup"><span data-stu-id="afbb7-200">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="afbb7-201">Flexibel, användardefinierad ARP-cache.</span><span class="sxs-lookup"><span data-stu-id="afbb7-201">Flexible, user-defined ARP cache.</span></span>
* <span data-ttu-id="afbb7-202">Bra ARP-stöd.</span><span class="sxs-lookup"><span data-stu-id="afbb7-202">Gratuitous ARP support.</span></span>
* <span data-ttu-id="afbb7-203">Valfri ARP/RARP-statistik som bestäms av programmet.</span><span class="sxs-lookup"><span data-stu-id="afbb7-203">Optional ARP/RARP statistics determined by application.</span></span>
* <span data-ttu-id="afbb7-204">Spårning på systemnivå via Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="afbb7-204">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="afbb7-205">ETHERNET, WiFi, BLUETOOTH LE, 15.4 osv.</span><span class="sxs-lookup"><span data-stu-id="afbb7-205">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="afbb7-206">Interoperabilitetsverifiering</span><span class="sxs-lookup"><span data-stu-id="afbb7-206">Interoperability verification</span></span>

<span data-ttu-id="afbb7-207">Azure RTOS NetX följer RFC-standarder och erbjuder fullständig samverkan med enheter för de flesta leverantörer.</span><span class="sxs-lookup"><span data-stu-id="afbb7-207">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="afbb7-208">Azure RTOS NetX använder även branschstandarden IxANVL (Automated Network Validation Library) för implementeringen av TCP/IP Azure RTOS NetX-kärnor.</span><span class="sxs-lookup"><span data-stu-id="afbb7-208">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="afbb7-209">Avancerad teknik</span><span class="sxs-lookup"><span data-stu-id="afbb7-209">Advanced technology</span></span>

<span data-ttu-id="afbb7-210">Azure RTOS NetX är avancerad teknik som omfattar följande.</span><span class="sxs-lookup"><span data-stu-id="afbb7-210">Azure RTOS NetX is advanced technology that includes the following.</span></span>
* <span data-ttu-id="afbb7-211">Piconet™arkitektur.</span><span class="sxs-lookup"><span data-stu-id="afbb7-211">Piconet™ architecture.</span></span>
* <span data-ttu-id="afbb7-212">Automatisk skalning.</span><span class="sxs-lookup"><span data-stu-id="afbb7-212">Automatic scaling.</span></span>
* <span data-ttu-id="afbb7-213">UDP Fast-Path Technology™.</span><span class="sxs-lookup"><span data-stu-id="afbb7-213">UDP Fast-Path Technology™.</span></span>
* <span data-ttu-id="afbb7-214">Flexibel pakethantering.</span><span class="sxs-lookup"><span data-stu-id="afbb7-214">Flexible packet management.</span></span>
* <span data-ttu-id="afbb7-215">API med nollkopiering och implementering.</span><span class="sxs-lookup"><span data-stu-id="afbb7-215">Zero-copy API and implementation.</span></span>
* <span data-ttu-id="afbb7-216">Stöd för flera hem.</span><span class="sxs-lookup"><span data-stu-id="afbb7-216">Multi-homed support.</span></span>
* <span data-ttu-id="afbb7-217">Valfri tidsgräns för all låsning.</span><span class="sxs-lookup"><span data-stu-id="afbb7-217">Optional timeout on all suspension.</span></span>
* <span data-ttu-id="afbb7-218">Stöd för statisk routning.</span><span class="sxs-lookup"><span data-stu-id="afbb7-218">Static routing support.</span></span>
* <span data-ttu-id="afbb7-219">Azure RTOS TraceX-systemanalysstöd.</span><span class="sxs-lookup"><span data-stu-id="afbb7-219">Azure RTOS TraceX system analysis support.</span></span>
