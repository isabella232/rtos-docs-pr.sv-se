---
title: Förstå Azure återställnings tider-NetX
description: Azure återställnings tider-NetX är en högpresterande implementering av TCP/IP-protokoll som är helt integrerad med Azure återställnings tider-ThreadX och är tillgängliga för alla processorer som stöds.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 029f73b755d5c40279125fb010ec35baaaf7f38d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825584"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="c8749-103">Översikt över Azure återställnings tider-NetX</span><span class="sxs-lookup"><span data-stu-id="c8749-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="c8749-104">Azure återställnings tider-NetX är en Azure-inbäddad TCP/IP IPv4-nätverks stack som är särskilt utformad för djupt inbäddade, real tids-och IoT-program.</span><span class="sxs-lookup"><span data-stu-id="c8749-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="c8749-105">Azure återställnings tider NetX är Microsofts ursprungliga IPv4-nätverks stack och är i grunden en delmängd av Azure återställnings tider.</span><span class="sxs-lookup"><span data-stu-id="c8749-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="c8749-106">NetX tillhandahåller inbäddade program med kärn nätverks protokoll som IPv4, TCP och UDP samt en fullständig uppsättning tilläggs protokoll på högre nivå.</span><span class="sxs-lookup"><span data-stu-id="c8749-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="c8749-107">En liten genom gång, snabb körning och överlägsen enkel användning gör Azure återställnings tider NetX ett idealiskt val för de mest krävande inbäddade IoT-programmen.</span><span class="sxs-lookup"><span data-stu-id="c8749-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="c8749-108">API-protokoll</span><span class="sxs-lookup"><span data-stu-id="c8749-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="c8749-109">TELNET</span><span class="sxs-lookup"><span data-stu-id="c8749-109">TELNET</span></span>

* <span data-ttu-id="c8749-110">Minst 0,5 KB och 0,3 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="c8749-110">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="c8749-111">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="c8749-111">Client and server support</span></span>
* <span data-ttu-id="c8749-112">Intuitiva Telnet-API: er: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-112">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="auto-ip"></a><span data-ttu-id="c8749-113">Automatisk IP</span><span class="sxs-lookup"><span data-stu-id="c8749-113">Auto IP</span></span>

* <span data-ttu-id="c8749-114">Automatisk tilldelning av IPv4-adress</span><span class="sxs-lookup"><span data-stu-id="c8749-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="c8749-115">Minimal 1,2 KB, 300 byte RAM-minne</span><span class="sxs-lookup"><span data-stu-id="c8749-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="c8749-116">Intuitiva AutoIP-API: er: *nx_autoip_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="c8749-117">HTTP-Hypertext Transfer Protocol (HTTP)</span><span class="sxs-lookup"><span data-stu-id="c8749-117">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="c8749-118">Minimal 2,8 KB till 4.8 KBFLASH, 0,4 KB till 1,0 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="c8749-118">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint</span></span>
* <span data-ttu-id="c8749-119">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="c8749-119">Client and server support</span></span>
* <span data-ttu-id="c8749-120">Intuitiva HTTP-API: er: *nx_http_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-120">Intuitive HTTP APIs: *nx_http_\**</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="c8749-121">SMTP – Simple Mail Transfer Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="c8749-121">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="c8749-122">Minst 4,1 KB och 0,6 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="c8749-122">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="c8749-123">Klient support</span><span class="sxs-lookup"><span data-stu-id="c8749-123">Client support</span></span>
* <span data-ttu-id="c8749-124">Intuitiva SMTP-API: er: *nx_smtp_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-124">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="c8749-125">DHCP-Dynamic Host Configuration Protocol (DHCP)</span><span class="sxs-lookup"><span data-stu-id="c8749-125">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="c8749-126">Minimal 3,6 KB till 4,6 KB FLASH, 2,7 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="c8749-126">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="c8749-127">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="c8749-127">Client and server support</span></span>
* <span data-ttu-id="c8749-128">IPv4-stöd</span><span class="sxs-lookup"><span data-stu-id="c8749-128">IPv4 support</span></span>
* <span data-ttu-id="c8749-129">Intuitiva DHCP-API: er: *nx_dhcp_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-129">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="c8749-130">P0P3-Post Office Protocol version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="c8749-130">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="c8749-131">Minst 8,1 KB och 1,4 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="c8749-131">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="c8749-132">Klient support</span><span class="sxs-lookup"><span data-stu-id="c8749-132">Client support</span></span>
* <span data-ttu-id="c8749-133">Intuitiva P0P3-API: er: *nx_pop3_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-133">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="c8749-134">SNMP – Simple Network Management Protocol (SNMP)</span><span class="sxs-lookup"><span data-stu-id="c8749-134">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="c8749-135">Minst 10,9 KB och 2,6 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="c8749-135">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="c8749-136">Agent stöd för VI, v2 och v3</span><span class="sxs-lookup"><span data-stu-id="c8749-136">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="c8749-137">Intuitiva SNMP-API: er: *nx_snmp_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-137">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="c8749-138">FTP, TFTP-File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span><span class="sxs-lookup"><span data-stu-id="c8749-138">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="c8749-139">FTP, minimal 1,8 KB till 7,2 KBFLASH, 0,6 KB till 2,1 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="c8749-139">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="c8749-140">TFTP minimal 1,7 KB till 2,4 KBFLASH, 0,3 KB till 1,8 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="c8749-140">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="c8749-141">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="c8749-141">Client and server support</span></span>
* <span data-ttu-id="c8749-142">Intuitiva API: er för FTP och TFTP: <i>nx_ftp_ *</i> eller <i>nx_tftp_*</i></span><span class="sxs-lookup"><span data-stu-id="c8749-142">Intuitive FTP and TFTP APIs: <i>nx_ftp_ *</i> or <i>nx_tftp_*</i></span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="c8749-143">PPP-Polnt-to-PoInt Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="c8749-143">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="c8749-144">Minst 7,1 KB och 3,8 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="c8749-144">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="c8749-145">Intuitiva PPP-API: er: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-145">Intuitive PPP APIs: *nx_ppp_\**</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="c8749-146">SNTP – Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="c8749-146">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="c8749-147">Minst 4 KB och 0,5 KB RAM</span><span class="sxs-lookup"><span data-stu-id="c8749-147">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="c8749-148">Klient support</span><span class="sxs-lookup"><span data-stu-id="c8749-148">Client support</span></span>
* <span data-ttu-id="c8749-149">Intuitiva SNTP-API: er: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-149">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="c8749-150">Azure återställnings tider NetX-API</span><span class="sxs-lookup"><span data-stu-id="c8749-150">Azure RTOS NetX API</span></span>

* <span data-ttu-id="c8749-151">Intuitiv och konsekvent API</span><span class="sxs-lookup"><span data-stu-id="c8749-151">Intuitive and consistent API</span></span>
* <span data-ttu-id="c8749-152">Substantiv-namn konvention för verb</span><span class="sxs-lookup"><span data-stu-id="c8749-152">Noun-verb naming convention</span></span>
* <span data-ttu-id="c8749-153">Snabb, noll-kopiera API-implementering</span><span class="sxs-lookup"><span data-stu-id="c8749-153">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="c8749-154">Alla API-funktioner har ledande <i>nx_ \*</i> för att enkelt identifiera som Azure återställnings tider netx</span><span class="sxs-lookup"><span data-stu-id="c8749-154">All API functions have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="c8749-155">Blockering av API-funktioner har en valfri tids gräns för trådar</span><span class="sxs-lookup"><span data-stu-id="c8749-155">Blocking API functions have an optional thread timeout</span></span>
* <span data-ttu-id="c8749-156">Valfritt BSD-lager för portning av äldre socket-kod</span><span class="sxs-lookup"><span data-stu-id="c8749-156">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="c8749-157">IGMP – IGMP (Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="c8749-157">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="c8749-158">Minimal 2,5 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="c8749-158">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="c8749-159">Stöd för IPv4 multicast-grupp</span><span class="sxs-lookup"><span data-stu-id="c8749-159">IPv4 multicast group support</span></span>
* <span data-ttu-id="c8749-160">IXIA-IxANVL verifierad</span><span class="sxs-lookup"><span data-stu-id="c8749-160">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="c8749-161">Valfri IGMP-statistik</span><span class="sxs-lookup"><span data-stu-id="c8749-161">Optional IGMP statistics</span></span>
* <span data-ttu-id="c8749-162">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="c8749-162">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="c8749-163">Intuitiva IGMP-API: er: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-163">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="c8749-164">UDP-UDP (User Datagram Protocol)</span><span class="sxs-lookup"><span data-stu-id="c8749-164">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="c8749-165">Minimal 2,5 KB FLASH, 124 Sockets byte RAM per socket</span><span class="sxs-lookup"><span data-stu-id="c8749-165">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="c8749-166">Snabb, nära WireSpeed TCP-paket bearbetning:</span><span class="sxs-lookup"><span data-stu-id="c8749-166">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="c8749-167">RX 95 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 14% MCU användning</span><span class="sxs-lookup"><span data-stu-id="c8749-167">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="c8749-168">TX 94 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 10% MCU användning</span><span class="sxs-lookup"><span data-stu-id="c8749-168">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="c8749-169">Snabb väg för™ teknik för UDP</span><span class="sxs-lookup"><span data-stu-id="c8749-169">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="c8749-170">Inga begränsningar för antalet UDP</span><span class="sxs-lookup"><span data-stu-id="c8749-170">No limits on the number of UDP</span></span>
* <span data-ttu-id="c8749-171">IXIA-IxANVL verifierad</span><span class="sxs-lookup"><span data-stu-id="c8749-171">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="c8749-172">Valfri SUS Pension på socket får</span><span class="sxs-lookup"><span data-stu-id="c8749-172">Optional suspension on socket receive</span></span>
* <span data-ttu-id="c8749-173">Valfri tids gräns vid alla avbrott</span><span class="sxs-lookup"><span data-stu-id="c8749-173">Optional timeout on all suspension</span></span>
* <span data-ttu-id="c8749-174">Valfri UDP-statistik</span><span class="sxs-lookup"><span data-stu-id="c8749-174">Optional UDP statistics</span></span>
* <span data-ttu-id="c8749-175">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="c8749-175">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="c8749-176">Intuitiva UDP-API: er: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-176">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="c8749-177">TCP-Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="c8749-177">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="c8749-178">Minst 10,5 K8 till 12,5 KB FLASH, 280 byte RAM per socket</span><span class="sxs-lookup"><span data-stu-id="c8749-178">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="c8749-179">Snabb, nära wlrespeed TCP-paket bearbetning:</span><span class="sxs-lookup"><span data-stu-id="c8749-179">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="c8749-180">RX 93 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 20% MCU användning</span><span class="sxs-lookup"><span data-stu-id="c8749-180">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="c8749-181">TX 94 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 27% MCU-användning</span><span class="sxs-lookup"><span data-stu-id="c8749-181">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="c8749-182">Tillförlitlig anslutning</span><span class="sxs-lookup"><span data-stu-id="c8749-182">Reliable connection</span></span>
* <span data-ttu-id="c8749-183">Inga begränsningar för antalet TCP-socketar</span><span class="sxs-lookup"><span data-stu-id="c8749-183">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="c8749-184">IXIA-IxANVL verifierad</span><span class="sxs-lookup"><span data-stu-id="c8749-184">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="c8749-185">Valfri SUS Pension på socket Receive/överföring</span><span class="sxs-lookup"><span data-stu-id="c8749-185">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="c8749-186">Valfri tids gräns vid alla avbrott</span><span class="sxs-lookup"><span data-stu-id="c8749-186">Optional timeout on all suspension</span></span>
* <span data-ttu-id="c8749-187">Valfri TCP-statistik</span><span class="sxs-lookup"><span data-stu-id="c8749-187">Optional TCP statistics</span></span>
* <span data-ttu-id="c8749-188">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="c8749-188">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="c8749-189">Intuitiva TCP-API: er: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-189">Intuitive TCP APIs:  *nx_tcp_\**</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="c8749-190">ICMP-Internet Control Message Protocol (ICMP)</span><span class="sxs-lookup"><span data-stu-id="c8749-190">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="c8749-191">Minimal 2,5 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="c8749-191">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="c8749-192">IPv4-stöd</span><span class="sxs-lookup"><span data-stu-id="c8749-192">IPv4 support</span></span>
* <span data-ttu-id="c8749-193">IXIA-IxANVL verifierad</span><span class="sxs-lookup"><span data-stu-id="c8749-193">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="c8749-194">Ping-begäran och ping-svar</span><span class="sxs-lookup"><span data-stu-id="c8749-194">Ping request and ping response</span></span>
* <span data-ttu-id="c8749-195">Valfri tråd SUS pension vid ping-begäranden</span><span class="sxs-lookup"><span data-stu-id="c8749-195">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="c8749-196">Valfri tids gräns vid alla avbrott</span><span class="sxs-lookup"><span data-stu-id="c8749-196">Optional timeout on all suspension</span></span>
* <span data-ttu-id="c8749-197">Valfri ICMP-statistik</span><span class="sxs-lookup"><span data-stu-id="c8749-197">Optional ICMP statistics</span></span>
* <span data-ttu-id="c8749-198">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="c8749-198">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="c8749-199">Intuitiva ICMP-API: er: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-199">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="c8749-200">IPv4-Internet Protocol (IP)</span><span class="sxs-lookup"><span data-stu-id="c8749-200">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="c8749-201">Minimal 3,5 KB till 8,5 KB FLASH, 2 KB till 3 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="c8749-201">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="c8749-202">Piconet™-arkitektur</span><span class="sxs-lookup"><span data-stu-id="c8749-202">Piconet™ Architecture</span></span>
* <span data-ttu-id="c8749-203">Snabba, nära WireSpeed prestanda</span><span class="sxs-lookup"><span data-stu-id="c8749-203">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="c8749-204">Stöd för flera gränssnitt</span><span class="sxs-lookup"><span data-stu-id="c8749-204">Multiple interface support</span></span>
* <span data-ttu-id="c8749-205">Stöd för multihomed</span><span class="sxs-lookup"><span data-stu-id="c8749-205">Multihomed support</span></span>
* <span data-ttu-id="c8749-206">Stöd för statisk routning</span><span class="sxs-lookup"><span data-stu-id="c8749-206">Static routing support</span></span>
* <span data-ttu-id="c8749-207">Stöd för IP-fragmentering/omsammansättning</span><span class="sxs-lookup"><span data-stu-id="c8749-207">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="c8749-208">IPv4-stöd</span><span class="sxs-lookup"><span data-stu-id="c8749-208">IPv4 Support</span></span>
* <span data-ttu-id="c8749-209">IXIA-IxANVL verifierad</span><span class="sxs-lookup"><span data-stu-id="c8749-209">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="c8749-210">Fas II färdig logo typ certifiering</span><span class="sxs-lookup"><span data-stu-id="c8749-210">Phase II Ready Logo Certification</span></span>
* <span data-ttu-id="c8749-211">Valfri IP-statistik</span><span class="sxs-lookup"><span data-stu-id="c8749-211">Optional IP statistics</span></span>
* <span data-ttu-id="c8749-212">Väl definierat, intuitivt gränssnitt för fysiskt skikt driv rutin</span><span class="sxs-lookup"><span data-stu-id="c8749-212">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="c8749-213">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="c8749-213">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="c8749-214">Intuitiva API: er för IP-lager: *nx_ip_ \** *nxd_ip_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-214">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**</span></span>
* <span data-ttu-id="c8749-215">Förcertifierat av TUV och UL till IEC 61508 SIL 4, IEC 62304 klass C, ISO 26262 ASIL D och EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="c8749-215">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="c8749-216">ARP/RARP-Address Resolution Protocol (ARP), omvänd Address Resolution Protocol (RARP)</span><span class="sxs-lookup"><span data-stu-id="c8749-216">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="c8749-217">Minimal 1,7 KB FLASH, RAM-storlek</span><span class="sxs-lookup"><span data-stu-id="c8749-217">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="c8749-218">Dynamisk matchning av 32-smörgås IPv4-och 48-smörgås MAC-adresser</span><span class="sxs-lookup"><span data-stu-id="c8749-218">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="c8749-219">IXIA-IxANVL verifierad</span><span class="sxs-lookup"><span data-stu-id="c8749-219">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="c8749-220">Flexibel, användardefinierad ARP-cache</span><span class="sxs-lookup"><span data-stu-id="c8749-220">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="c8749-221">Stöd för kostnads fria ARP</span><span class="sxs-lookup"><span data-stu-id="c8749-221">Gratuitous ARP support</span></span>
* <span data-ttu-id="c8749-222">Valfri ARP/RARP-statistik som fastställs av programmet</span><span class="sxs-lookup"><span data-stu-id="c8749-222">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="c8749-223">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="c8749-223">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="c8749-224">Intuitiva ARP/RARP-API: er: *nx_arp_ \** *nx_rarp_ \**</span><span class="sxs-lookup"><span data-stu-id="c8749-224">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="c8749-225">ETHERNET, WiFi, BLUETOOTH LE, 15,4 osv.</span><span class="sxs-lookup"><span data-stu-id="c8749-225">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="small-footprint"></a><span data-ttu-id="c8749-226">Små</span><span class="sxs-lookup"><span data-stu-id="c8749-226">Small-footprint</span></span>

<span data-ttu-id="c8749-227">Azure återställnings tider NetX har ett remarkably litet utrymme på 9 KB till 15 KB för grundläggande IP-och UDP-stöd.</span><span class="sxs-lookup"><span data-stu-id="c8749-227">Azure RTOS NetX has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="c8749-228">Det krävs ytterligare 10 KB till 13 KB av instruktions områdets minne för TCP-funktioner.</span><span class="sxs-lookup"><span data-stu-id="c8749-228">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="c8749-229">Azure återställnings tider NetX RAM-användningen är vanligt vis mellan 2,6 KB och 3,6 KB plus det minne för Packet-poolen som definieras av programmet.</span><span class="sxs-lookup"><span data-stu-id="c8749-229">Azure RTOS NetX RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="c8749-230">Precis som Azure återställnings tider ThreadX skalas storleken på Azure återställnings tider-NetX automatiskt utifrån de tjänster som används av programmet.</span><span class="sxs-lookup"><span data-stu-id="c8749-230">Like Azure RTOS ThreadX, the size of Azure RTOS NetX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="c8749-231">Detta eliminerar behovet av komplicerade konfigurations-och bygg parametrar, vilket gör det enklare för utvecklaren.</span><span class="sxs-lookup"><span data-stu-id="c8749-231">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="c8749-232">Snabb körning</span><span class="sxs-lookup"><span data-stu-id="c8749-232">Fast execution</span></span>

<span data-ttu-id="c8749-233">Azure återställnings tider NetX innehåller en paket för att skicka och ta emot paket utan kopiering och är mycket integrerat med Azure återställnings tider ThreadX för att uppnå snabbast möjliga prestanda.</span><span class="sxs-lookup"><span data-stu-id="c8749-233">Azure RTOS NetX provides a zero-copy packet send/receive implementation and is highly integrated with Azure RTOS ThreadX to achieve the fastest possible performance.</span></span> <span data-ttu-id="c8749-234">Azure återställnings tider NetX kan till exempel normalt uppnå nära WireSpeed-dataöverföringar på en processor på 80 MHz (eller mindre), samtidigt som en liten del av processorns cykler används.</span><span class="sxs-lookup"><span data-stu-id="c8749-234">For example, Azure RTOS NetX can typically achieve near wirespeed data transfers on an 80-MHz processor (or less), while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="c8749-235">Enkel, lätt att använda</span><span class="sxs-lookup"><span data-stu-id="c8749-235">Simple, easy-to-use</span></span>

<span data-ttu-id="c8749-236">Azure återställnings tider-NetX är enkelt att använda.</span><span class="sxs-lookup"><span data-stu-id="c8749-236">Azure RTOS NetX is simple to use.</span></span> <span data-ttu-id="c8749-237">Azure återställnings tider NetX-API: et är både intuitivt och mycket funktionellt.</span><span class="sxs-lookup"><span data-stu-id="c8749-237">The Azure RTOS NetX API is both intuitive and highly functional.</span></span> <span data-ttu-id="c8749-238">API-namnen består av riktiga ord och inte "alfabet soppor" eller förkortade namn som är vanliga i andra nätverks produkter.</span><span class="sxs-lookup"><span data-stu-id="c8749-238">The API names are made of real words and not “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="c8749-239">Alla Azure återställnings tider NetX-API: er har en ledande *nx_* och följer en namn konvention för substantiv-verb.</span><span class="sxs-lookup"><span data-stu-id="c8749-239">All Azure RTOS NetX APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="c8749-240">Det finns dessutom en funktions konsekvens i hela API: et.</span><span class="sxs-lookup"><span data-stu-id="c8749-240">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="c8749-241">Till exempel har alla API-funktioner som pausas en valfri tids gräns som fungerar på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="c8749-241">For example, all API functions that suspend have an optional timeout that functions in an identical manner.</span></span> <span data-ttu-id="c8749-242">För äldre program erbjuder Azure återställnings tider NetX ytterligare ett BSD-kompatibelt lager.</span><span class="sxs-lookup"><span data-stu-id="c8749-242">For legacy applications, Azure RTOS NetX offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="c8749-243">Det här lagret hjälper utvecklare att migrera stora nätverks program utan problem.</span><span class="sxs-lookup"><span data-stu-id="c8749-243">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="c8749-244">Verifiering av interoperabilitet</span><span class="sxs-lookup"><span data-stu-id="c8749-244">Interoperability verification</span></span>

<span data-ttu-id="c8749-245">Azure återställnings tider-NetX överensstämmer med RFC-standarder och erbjuder fullständig interoperabilitet med enheter för de flesta leverantörer.</span><span class="sxs-lookup"><span data-stu-id="c8749-245">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="c8749-246">Azure återställnings tider NetX använder också bransch standard IxANVL (automatiskt bibliotek för nätverks validering) för implementeringen av Azure återställnings tider NetX Core TCP/IP-protokollet.</span><span class="sxs-lookup"><span data-stu-id="c8749-246">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="c8749-247">Avancerad teknik</span><span class="sxs-lookup"><span data-stu-id="c8749-247">Advanced technology</span></span>

<span data-ttu-id="c8749-248">Azure återställnings tider-NetX är en avancerad teknik som innehåller:</span><span class="sxs-lookup"><span data-stu-id="c8749-248">Azure RTOS NetX is advanced technology that includes:</span></span>

* <span data-ttu-id="c8749-249">Piconet™-arkitektur</span><span class="sxs-lookup"><span data-stu-id="c8749-249">Piconet™ architecture</span></span>
* <span data-ttu-id="c8749-250">automatisk skalning</span><span class="sxs-lookup"><span data-stu-id="c8749-250">automatic scaling</span></span>
* <span data-ttu-id="c8749-251">™ För UDP Fast-Path Technology</span><span class="sxs-lookup"><span data-stu-id="c8749-251">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="c8749-252">flexibel paket hantering</span><span class="sxs-lookup"><span data-stu-id="c8749-252">flexible packet management</span></span>
* <span data-ttu-id="c8749-253">API för Zero-kopiering och implementering</span><span class="sxs-lookup"><span data-stu-id="c8749-253">zero-copy API and implementation</span></span>
* <span data-ttu-id="c8749-254">stöd för multihomed</span><span class="sxs-lookup"><span data-stu-id="c8749-254">multihomed support</span></span>
* <span data-ttu-id="c8749-255">valfri tids gräns vid alla avbrott</span><span class="sxs-lookup"><span data-stu-id="c8749-255">optional timeout on all suspension</span></span>
* <span data-ttu-id="c8749-256">stöd för statisk routning</span><span class="sxs-lookup"><span data-stu-id="c8749-256">static routing support</span></span>
* <span data-ttu-id="c8749-257">Azure återställnings tider TraceX system Analysis support</span><span class="sxs-lookup"><span data-stu-id="c8749-257">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="c8749-258">Snabbast tid till marknad</span><span class="sxs-lookup"><span data-stu-id="c8749-258">Fastest time-to-market</span></span>

<span data-ttu-id="c8749-259">Azure återställnings tider NetX är enkelt att installera, lära sig, använda, felsöka, verifiera, certifiera och underhålla.</span><span class="sxs-lookup"><span data-stu-id="c8749-259">Azure RTOS NetX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="c8749-260">Därför är Azure återställnings tider NetX en av de mest populära TCP/IP-stackarna för inbäddade IoT-enheter, inklusive många SoCs från Broadcom, Gainspan och så vidare.</span><span class="sxs-lookup"><span data-stu-id="c8749-260">As a result, Azure RTOS NetX is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, and so forth.</span></span> <span data-ttu-id="c8749-261">Vår konsekventa tid till marknads fördelen bygger på:</span><span class="sxs-lookup"><span data-stu-id="c8749-261">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="c8749-262">kvalitets dokumentation – Läs vår [Användar handbok för Azure återställnings tider netx](about-this-guide.md) och se själv!</span><span class="sxs-lookup"><span data-stu-id="c8749-262">quality documentation – please review our [Azure RTOS NetX User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="c8749-263">fullständig käll kods tillgänglighet</span><span class="sxs-lookup"><span data-stu-id="c8749-263">complete source code availability</span></span>
* <span data-ttu-id="c8749-264">lätt att använda API</span><span class="sxs-lookup"><span data-stu-id="c8749-264">easy-to-use API</span></span>
* <span data-ttu-id="c8749-265">omfattande och avancerad funktions uppsättning</span><span class="sxs-lookup"><span data-stu-id="c8749-265">comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="c8749-266">En enkel licens</span><span class="sxs-lookup"><span data-stu-id="c8749-266">One Simple License</span></span>

<span data-ttu-id="c8749-267">Det kostar inget att använda och testa käll koden och ingen kostnad för produktions licenser när de distribueras till förinstallerade enheter, men alla andra enheter behöver en enkel årlig licens.</span><span class="sxs-lookup"><span data-stu-id="c8749-267">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="c8749-268">Fullständig käll kod med högsta kvalitet</span><span class="sxs-lookup"><span data-stu-id="c8749-268">Full, highest-quality source code</span></span>

<span data-ttu-id="c8749-269">Under åren har Azure återställnings tider NetX-källkoden ställt in kvalitet och enkel förståelse.</span><span class="sxs-lookup"><span data-stu-id="c8749-269">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="c8749-270">Dessutom tillhandahåller konventionen om en funktion per fil för enkel käll navigering.</span><span class="sxs-lookup"><span data-stu-id="c8749-270">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="c8749-271">Har stöd för de flesta populära arkitekturerna</span><span class="sxs-lookup"><span data-stu-id="c8749-271">Supports most popular architectures</span></span>

<span data-ttu-id="c8749-272">Azure återställnings tider-NetX körs på de flesta populära 32/64-bitars mikroprocessorer, färdiga, fullständigt testade och fullt stödda, inklusive följande avancerade arkitekturer:</span><span class="sxs-lookup"><span data-stu-id="c8749-272">Azure RTOS NetX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="c8749-273">**Analoga enheter**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="c8749-273">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="c8749-274">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="c8749-274">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="c8749-275">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="c8749-275">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="c8749-276">**Arm**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitars/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="c8749-276">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="c8749-277">**Takt**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="c8749-277">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="c8749-278">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="c8749-278">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="c8749-279">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="c8749-279">**Cypress**: RISC-V</span></span>

<span data-ttu-id="c8749-280">**Kiseldioxid**: ESI – RISC</span><span class="sxs-lookup"><span data-stu-id="c8749-280">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="c8749-281">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="c8749-281">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="c8749-282">**Intel; Intel FPGA**: x36/Pentium, XScale, Nios II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="c8749-282">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="c8749-283">**Mikrochip**: avr32, ARM7, ARM9, cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/sa, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="c8749-283">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="c8749-284">**Mikrohalv**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="c8749-284">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="c8749-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, coldfire, Kinetis cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="c8749-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="c8749-286">**Renesas**: SH, HS, V850, RX, RZ, synergieffekt</span><span class="sxs-lookup"><span data-stu-id="c8749-286">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="c8749-287">**Silicon Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="c8749-287">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="c8749-288">**Sammanfattning**: båge 600, 700, båge EM, båg HS</span><span class="sxs-lookup"><span data-stu-id="c8749-288">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="c8749-289">**St**: STM32, ARM7, ARM9, cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="c8749-289">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="c8749-290">**TL**: C5xxx, C6xxx, Stellaris, Sitara, tiva-C</span><span class="sxs-lookup"><span data-stu-id="c8749-290">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="c8749-291">**Wave-bearbetning**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="c8749-291">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="c8749-292">**Xilinx**: mikroblixt, powerpc 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="c8749-292">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="c8749-293">*Alla tids gränser och storleks värden i listan är uppskattningar och kan skilja sig åt på din utvecklings plattform.*</span><span class="sxs-lookup"><span data-stu-id="c8749-293">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
