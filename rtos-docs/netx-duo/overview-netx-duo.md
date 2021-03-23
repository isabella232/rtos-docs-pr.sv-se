---
title: Förstå Azure återställnings tider NetX Duo
description: Azure återställnings tider NetX Duo är en avancerad och inbyggd TCP/IP-datastack i företags klass har utformats specifikt för djupt inbäddade real tids-och IoT-program.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 2339da391e52b437a2111ae439cccf41e038bdcf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826925"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="9dbda-103">Översikt över Azure återställnings tider NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9dbda-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="9dbda-104">Azure återställnings tider NetX Duo Embedded TCP/IP Network stack är Microsofts avancerade, industriella klass med dubbla IPv4-och IPv6-nätverks stackar som är särskilt utformade för djupt inbäddade, real tids-och IoT-program.</span><span class="sxs-lookup"><span data-stu-id="9dbda-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="9dbda-105">NetX Duo tillhandahåller inbäddade program med kärn nätverks protokoll som IPv4, IPv6, TCP och UDP samt en fullständig uppsättning tilläggs protokoll på högre nivå.</span><span class="sxs-lookup"><span data-stu-id="9dbda-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="9dbda-106">Azure återställnings tider NetX Duo erbjuder säkerhet via ytterligare tilläggs säkerhets produkter, inklusive Azure återställnings tider NetX Secure IPsec och Azure återställnings tider NetX Secure SSL/TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="9dbda-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="9dbda-107">Allt detta kombinerat med en liten storlek, snabb körning och överlägsen enkel användning gör Azure återställnings tider NetX Duo det idealiska valet för de mest krävande inbäddade IoT-programmen.</span><span class="sxs-lookup"><span data-stu-id="9dbda-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="9dbda-108">API-protokoll</span><span class="sxs-lookup"><span data-stu-id="9dbda-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="9dbda-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="9dbda-109">MQTT</span></span>

* <span data-ttu-id="9dbda-110">MQTT (Messaging Queue telemetri transport)</span><span class="sxs-lookup"><span data-stu-id="9dbda-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="9dbda-111">Minimal 2,7 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="9dbda-111">Minimal 2.7 KB FLASH</span></span>
* <span data-ttu-id="9dbda-112">Intuitiva MQTT-API: er: *nx_mqtt_*\*</span><span class="sxs-lookup"><span data-stu-id="9dbda-112">Intuitive MQTT APIs: *nx_mqtt_*\*</span></span>

### <a name="auto-ip"></a><span data-ttu-id="9dbda-113">Automatisk IP</span><span class="sxs-lookup"><span data-stu-id="9dbda-113">Auto IP</span></span>

* <span data-ttu-id="9dbda-114">Automatisk tilldelning av IPv4-adress</span><span class="sxs-lookup"><span data-stu-id="9dbda-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="9dbda-115">Minimal 1,2 KB, 300 byte RAM-minne</span><span class="sxs-lookup"><span data-stu-id="9dbda-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="9dbda-116">Intuitiva AutoIP-API: er: *nx_autoip_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http-https"></a><span data-ttu-id="9dbda-117">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="9dbda-117">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="9dbda-118">HTTP 1,0</span><span class="sxs-lookup"><span data-stu-id="9dbda-118">HTTP 1.0</span></span>

* <span data-ttu-id="9dbda-119">Hypertext Transfer Protocol (HTTP)</span><span class="sxs-lookup"><span data-stu-id="9dbda-119">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="9dbda-120">Minimal 2,8 KB till 4,8 KB FLASH/0,4 KB till 1,0 KB RAM</span><span class="sxs-lookup"><span data-stu-id="9dbda-120">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="9dbda-121">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="9dbda-121">Client and server support</span></span>
* <span data-ttu-id="9dbda-122">Intuitiva API: er: *nx_http_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-122">Intuitive APIs: *nx_http_\**</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="9dbda-123">HTTP/HTTPS 1,1</span><span class="sxs-lookup"><span data-stu-id="9dbda-123">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="9dbda-124">Hypertext Transfer Protocol (HTTP)</span><span class="sxs-lookup"><span data-stu-id="9dbda-124">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="9dbda-125">Minimal 3,0 KB till 9,5 KB FLASH/0,5 KB till 2 KB RAM</span><span class="sxs-lookup"><span data-stu-id="9dbda-125">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="9dbda-126">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="9dbda-126">Client and server support</span></span>
* <span data-ttu-id="9dbda-127">Flera inkommande klientsessioner</span><span class="sxs-lookup"><span data-stu-id="9dbda-127">Multiple incoming client sessions</span></span>
* <span data-ttu-id="9dbda-128">Oformaterad text och krypterad HTTPS</span><span class="sxs-lookup"><span data-stu-id="9dbda-128">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="9dbda-129">Stöd för beständiga anslutningar</span><span class="sxs-lookup"><span data-stu-id="9dbda-129">Persistent connection support</span></span>
* <span data-ttu-id="9dbda-130">Uppladdning av flerdelade filer</span><span class="sxs-lookup"><span data-stu-id="9dbda-130">Multipart file upload</span></span>
* <span data-ttu-id="9dbda-131">Fullständigt integrerat med Azure återställnings tider NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="9dbda-131">Fully integrated with Azure RTOS NetX Secure TLS</span></span>
* <span data-ttu-id="9dbda-132">Intuitiva API: er: *nx_web_http \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-132">Intuitive APIs: *nx_web_http\**</span></span>

### <a name="smtp"></a><span data-ttu-id="9dbda-133">SMTP</span><span class="sxs-lookup"><span data-stu-id="9dbda-133">SMTP</span></span>

* <span data-ttu-id="9dbda-134">Simple mallar Transfer Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="9dbda-134">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="9dbda-135">Minst 4,1 KB och 0,6 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="9dbda-135">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="9dbda-136">Klient support</span><span class="sxs-lookup"><span data-stu-id="9dbda-136">Client support</span></span>
* <span data-ttu-id="9dbda-137">Intuitiva SMTP-API: er: *nx_smtp_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-137">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp"></a><span data-ttu-id="9dbda-138">DHCP</span><span class="sxs-lookup"><span data-stu-id="9dbda-138">DHCP</span></span>

* <span data-ttu-id="9dbda-139">DHCP (Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="9dbda-139">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="9dbda-140">Minimal 3,6 KB till 4,6 KB FLASH, 2,7 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="9dbda-140">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="9dbda-141">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="9dbda-141">Client and server support</span></span>
* <span data-ttu-id="9dbda-142">Stöd för IPv4 och IPv6</span><span class="sxs-lookup"><span data-stu-id="9dbda-142">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="9dbda-143">Intuitiva DHCP-API: er: *nx_dhcp_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-143">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="nat"></a><span data-ttu-id="9dbda-144">NAT</span><span class="sxs-lookup"><span data-stu-id="9dbda-144">NAT</span></span>

* <span data-ttu-id="9dbda-145">NAT (Network Address Translation)</span><span class="sxs-lookup"><span data-stu-id="9dbda-145">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="9dbda-146">Minimal 3,5-tums K6 och 0,6 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="9dbda-146">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="9dbda-147">Stöd för IPv4-adress</span><span class="sxs-lookup"><span data-stu-id="9dbda-147">IPv4 address support</span></span>
* <span data-ttu-id="9dbda-148">Intuitiva NAT-API: er: *nx_nat_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-148">Intuitive NAT APIs: *nx_nat_\**</span></span>
* <span data-ttu-id="9dbda-149">NAT är endast tillgängligt med Azure återställnings tider NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9dbda-149">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="9dbda-150">SNMP</span><span class="sxs-lookup"><span data-stu-id="9dbda-150">SNMP</span></span>

* <span data-ttu-id="9dbda-151">Simple Network Management Protocol (SNMP)</span><span class="sxs-lookup"><span data-stu-id="9dbda-151">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="9dbda-152">Minst 10,9 KB och 2,6 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="9dbda-152">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="9dbda-153">Agent stöd för VI, v2 och v3</span><span class="sxs-lookup"><span data-stu-id="9dbda-153">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="9dbda-154">Intuitiva SNMP-API: er: *nx_snmp_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-154">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="9dbda-155">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="9dbda-155">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="9dbda-156">DNS (Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="9dbda-156">Domain Name System (DNS)</span></span>
* <span data-ttu-id="9dbda-157">Multicast-Domain Name System (mDNS)</span><span class="sxs-lookup"><span data-stu-id="9dbda-157">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="9dbda-158">DNS-baserad tjänst identifiering (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="9dbda-158">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="9dbda-159">DNS-minimal 2,4 KB till 3 KB FLASH, 1 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="9dbda-159">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="9dbda-160">Klient support</span><span class="sxs-lookup"><span data-stu-id="9dbda-160">Client support</span></span>
* <span data-ttu-id="9dbda-161">Intuitiva API: er: *nx_dns_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-161">Intuitive APIs: *nx_dns_\**</span></span>
* <span data-ttu-id="9dbda-162">mDNS och DNS – SD är bara tillgängliga med Azure återställnings tider NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9dbda-162">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="p0p3"></a><span data-ttu-id="9dbda-163">P0P3</span><span class="sxs-lookup"><span data-stu-id="9dbda-163">P0P3</span></span>

* <span data-ttu-id="9dbda-164">Post Office Protocol version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="9dbda-164">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="9dbda-165">Minst 8,1 KB och 1,4 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="9dbda-165">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="9dbda-166">Klient support</span><span class="sxs-lookup"><span data-stu-id="9dbda-166">Client support</span></span>
* <span data-ttu-id="9dbda-167">Intuitiva P0P3-API: er: *nx_pop3_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-167">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="telnet"></a><span data-ttu-id="9dbda-168">TELNET</span><span class="sxs-lookup"><span data-stu-id="9dbda-168">TELNET</span></span>

* <span data-ttu-id="9dbda-169">Minst 0,5 KB och 0,3 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="9dbda-169">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="9dbda-170">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="9dbda-170">Client and server support</span></span>
* <span data-ttu-id="9dbda-171">Intuitiva Telnet-API: er: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-171">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="9dbda-172">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="9dbda-172">FTP, TFTP</span></span>

* <span data-ttu-id="9dbda-173">File Transfer Protocol (FTP)</span><span class="sxs-lookup"><span data-stu-id="9dbda-173">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="9dbda-174">Trivial file transfer protocol (TFTP)</span><span class="sxs-lookup"><span data-stu-id="9dbda-174">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="9dbda-175">FTP, minimal 1,8 KB till 7,2 KB FLASH, 0,6 KB till 2,1 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="9dbda-175">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="9dbda-176">TFTP minimal 1,7 KB till 2,4 KB FLASH, 0,3 KB till 1,8 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="9dbda-176">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="9dbda-177">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="9dbda-177">Client and server support</span></span>
* <span data-ttu-id="9dbda-178">Intuitiva API: er för FTP och TFTP: *nx_ftp_ \** eller *nx_tftp_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-178">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="9dbda-179">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="9dbda-179">PPP, PPPoE</span></span>

* <span data-ttu-id="9dbda-180">Polnt-to-PoInt Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="9dbda-180">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="9dbda-181">Point-to-Point Protocol över Ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="9dbda-181">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="9dbda-182">Minst 7,1 KB och 3,8 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="9dbda-182">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="9dbda-183">Intuitiva PPP-API: er: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-183">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="9dbda-184">PPPoE är endast tillgängligt med Azure återställnings tider NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9dbda-184">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="9dbda-185">SNTP</span><span class="sxs-lookup"><span data-stu-id="9dbda-185">SNTP</span></span>

* <span data-ttu-id="9dbda-186">SNTP (Simple Network Time Protocol)</span><span class="sxs-lookup"><span data-stu-id="9dbda-186">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="9dbda-187">Minst 4 KB och 0,5 KB RAM</span><span class="sxs-lookup"><span data-stu-id="9dbda-187">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="9dbda-188">Klient support</span><span class="sxs-lookup"><span data-stu-id="9dbda-188">Client support</span></span>
* <span data-ttu-id="9dbda-189">Intuitiva SNTP-API: er: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-189">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="9dbda-190">Azure återställnings tider NetX Duo-API</span><span class="sxs-lookup"><span data-stu-id="9dbda-190">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="9dbda-191">Intuitiv och konsekvent API</span><span class="sxs-lookup"><span data-stu-id="9dbda-191">Intuitive and consistent API</span></span>
* <span data-ttu-id="9dbda-192">Substantiv-namn konvention för verb</span><span class="sxs-lookup"><span data-stu-id="9dbda-192">Noun-verb naming convention</span></span>
* <span data-ttu-id="9dbda-193">Snabb, noll-kopiera API-implementering</span><span class="sxs-lookup"><span data-stu-id="9dbda-193">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="9dbda-194">Alla API: er har ledande <i>nx_ \*</i> för att enkelt identifiera som Azure återställnings tider netx</span><span class="sxs-lookup"><span data-stu-id="9dbda-194">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="9dbda-195">Blockering av API: er har valfri tråd-timeout</span><span class="sxs-lookup"><span data-stu-id="9dbda-195">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="9dbda-196">Mer information finns i [användar handboken för Azure återställnings tider netx Duo](about-this-guide.md) .</span><span class="sxs-lookup"><span data-stu-id="9dbda-196">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="9dbda-197">Valfritt BSD-lager för portning av äldre socket-kod</span><span class="sxs-lookup"><span data-stu-id="9dbda-197">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="9dbda-198">PROXYLÄGE</span><span class="sxs-lookup"><span data-stu-id="9dbda-198">IGMP</span></span>

* <span data-ttu-id="9dbda-199">Internet Grupphanteringsprotokoll (IGMP)</span><span class="sxs-lookup"><span data-stu-id="9dbda-199">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="9dbda-200">Minimal 2,5 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="9dbda-200">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="9dbda-201">Stöd för IPv4 multicast-grupp</span><span class="sxs-lookup"><span data-stu-id="9dbda-201">IPv4 multicast group support</span></span>
* <span data-ttu-id="9dbda-202">IXIA-IxANVL verifierad</span><span class="sxs-lookup"><span data-stu-id="9dbda-202">IXIA IxANVL validated</span></span>
* <span data-ttu-id="9dbda-203">Valfri IGMP-statistik</span><span class="sxs-lookup"><span data-stu-id="9dbda-203">Optional IGMP statistics</span></span>
* <span data-ttu-id="9dbda-204">Spårning på system nivå via Azure återställnings tider ThreadX</span><span class="sxs-lookup"><span data-stu-id="9dbda-204">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="9dbda-205">Intuitiva IGMP-API: er: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-205">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="9dbda-206">Azure återställnings tider NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="9dbda-206">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="9dbda-207">Datagram Transport Layer Security (DTLS) 1,0 och 1,2</span><span class="sxs-lookup"><span data-stu-id="9dbda-207">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="9dbda-208">Minst 11 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="9dbda-208">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="9dbda-209">Snabb, programvaru-RSA 2048-bitars nyckel storlek ~ 1-sekund @120MHz</span><span class="sxs-lookup"><span data-stu-id="9dbda-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="9dbda-210">Effektiv X. 509-implementering</span><span class="sxs-lookup"><span data-stu-id="9dbda-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="9dbda-211">Fullständigt integrerat med Azure återställnings tider NetX Duo UDP-Sockets</span><span class="sxs-lookup"><span data-stu-id="9dbda-211">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="9dbda-212">Stöd för maskin varu kryptering</span><span class="sxs-lookup"><span data-stu-id="9dbda-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="9dbda-213">Stöd för program varu kryptografi: RSA (alla nyckel storlekar), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="9dbda-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="9dbda-214">Elliptic Curve Cryptography (ECC) med ECDSA (Sign) och ECDH (kryptering), inklusive P-kurvor 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="9dbda-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="9dbda-215">Stöd för krypterad nyckel (maskin vara beroende)</span><span class="sxs-lookup"><span data-stu-id="9dbda-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="9dbda-216">Azure återställnings tider NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="9dbda-216">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="9dbda-217">Transport Layer Security (TLS) 1,0, 1,1 och 1,2</span><span class="sxs-lookup"><span data-stu-id="9dbda-217">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="9dbda-218">Minimal 8,8 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="9dbda-218">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="9dbda-219">Snabb, programvaru-RSA 2048-bitars nyckel storlek ~ 1-sekund @120MHz</span><span class="sxs-lookup"><span data-stu-id="9dbda-219">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="9dbda-220">Effektiv X. 509-implementering</span><span class="sxs-lookup"><span data-stu-id="9dbda-220">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="9dbda-221">Fullständigt integrerat med Azure återställnings tider NetX Duo TCP-Sockets</span><span class="sxs-lookup"><span data-stu-id="9dbda-221">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="9dbda-222">Stöd för maskin varu kryptering</span><span class="sxs-lookup"><span data-stu-id="9dbda-222">Hardware Crypto Support</span></span>
* <span data-ttu-id="9dbda-223">Stöd för program varu kryptografi: RSA (alla nyckel storlekar), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="9dbda-223">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="9dbda-224">Elliptic Curve Cryptography (ECC) med ECDSA (Sign) och ECDH (kryptering), inklusive P-kurvor 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="9dbda-224">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="9dbda-225">Stöd för krypterad nyckel (maskin vara beroende)</span><span class="sxs-lookup"><span data-stu-id="9dbda-225">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="9dbda-226">ICMP</span><span class="sxs-lookup"><span data-stu-id="9dbda-226">ICMP</span></span>

* <span data-ttu-id="9dbda-227">Internet Control Message Protocol (ICMP)</span><span class="sxs-lookup"><span data-stu-id="9dbda-227">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="9dbda-228">Minimal 2,5 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="9dbda-228">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="9dbda-229">Stöd för IPv4 och IPv6</span><span class="sxs-lookup"><span data-stu-id="9dbda-229">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="9dbda-230">IXIA-IxANVL verifierad</span><span class="sxs-lookup"><span data-stu-id="9dbda-230">IXIA IxANVL validated</span></span>
* <span data-ttu-id="9dbda-231">Ping-begäran och ping-svar</span><span class="sxs-lookup"><span data-stu-id="9dbda-231">Ping request and ping response</span></span>
* <span data-ttu-id="9dbda-232">Valfri tråd SUS pension vid ping-begäranden</span><span class="sxs-lookup"><span data-stu-id="9dbda-232">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="9dbda-233">Valfri tids gräns vid alla avbrott</span><span class="sxs-lookup"><span data-stu-id="9dbda-233">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9dbda-234">Valfri ICMP-statistik</span><span class="sxs-lookup"><span data-stu-id="9dbda-234">Optional ICMP statistics</span></span>
* <span data-ttu-id="9dbda-235">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="9dbda-235">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="9dbda-236">Intuitiva ICMP-API: er: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-236">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="9dbda-237">UDP</span><span class="sxs-lookup"><span data-stu-id="9dbda-237">UDP</span></span>

* <span data-ttu-id="9dbda-238">UDP (User Datagram Protocol)</span><span class="sxs-lookup"><span data-stu-id="9dbda-238">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="9dbda-239">Minimal 2,5 KB FLASH, 124 Sockets byte RAM per socket</span><span class="sxs-lookup"><span data-stu-id="9dbda-239">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="9dbda-240">Snabb, nära WireSpeed TCP-paket bearbetning:</span><span class="sxs-lookup"><span data-stu-id="9dbda-240">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="9dbda-241">RX 95 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 14% MCU användning</span><span class="sxs-lookup"><span data-stu-id="9dbda-241">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="9dbda-242">TX 94 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 10% MCU användning</span><span class="sxs-lookup"><span data-stu-id="9dbda-242">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="9dbda-243">Snabb väg för™ teknik för UDP</span><span class="sxs-lookup"><span data-stu-id="9dbda-243">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="9dbda-244">Inga begränsningar för antalet UDP</span><span class="sxs-lookup"><span data-stu-id="9dbda-244">No limits on the number of UDP</span></span>
* <span data-ttu-id="9dbda-245">IXIA-IxANVL verifierad</span><span class="sxs-lookup"><span data-stu-id="9dbda-245">IXIA IxANVL validated</span></span>
* <span data-ttu-id="9dbda-246">Valfri SUS Pension på socket får</span><span class="sxs-lookup"><span data-stu-id="9dbda-246">Optional suspension on socket receive</span></span>
* <span data-ttu-id="9dbda-247">Valfri tids gräns vid alla avbrott</span><span class="sxs-lookup"><span data-stu-id="9dbda-247">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9dbda-248">Valfri UDP-statistik</span><span class="sxs-lookup"><span data-stu-id="9dbda-248">Optional UDP statistics</span></span>
* <span data-ttu-id="9dbda-249">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="9dbda-249">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="9dbda-250">Intuitiva UDP-API: er: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-250">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="9dbda-251">TCP</span><span class="sxs-lookup"><span data-stu-id="9dbda-251">TCP</span></span>

* <span data-ttu-id="9dbda-252">Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="9dbda-252">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="9dbda-253">Minst 10,5 K8 till 12,5 KB FLASH, 280 byte RAM per socket</span><span class="sxs-lookup"><span data-stu-id="9dbda-253">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="9dbda-254">Snabb, nära wlrespeed TCP-paket bearbetning:</span><span class="sxs-lookup"><span data-stu-id="9dbda-254">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="9dbda-255">RX 93 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 20% MCU användning</span><span class="sxs-lookup"><span data-stu-id="9dbda-255">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="9dbda-256">TX 94 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 27% MCU-användning</span><span class="sxs-lookup"><span data-stu-id="9dbda-256">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="9dbda-257">Tillförlitlig anslutning</span><span class="sxs-lookup"><span data-stu-id="9dbda-257">Reliable connection</span></span>
* <span data-ttu-id="9dbda-258">Inga begränsningar för antalet TCP-socketar</span><span class="sxs-lookup"><span data-stu-id="9dbda-258">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="9dbda-259">IXIA-IxANVL verifierad</span><span class="sxs-lookup"><span data-stu-id="9dbda-259">IXIA IxANVL validated</span></span>
* <span data-ttu-id="9dbda-260">Valfri SUS Pension på socket Receive/överföring</span><span class="sxs-lookup"><span data-stu-id="9dbda-260">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="9dbda-261">Valfri tids gräns vid alla avbrott</span><span class="sxs-lookup"><span data-stu-id="9dbda-261">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9dbda-262">Valfri TCP-statistik</span><span class="sxs-lookup"><span data-stu-id="9dbda-262">Optional TCP statistics</span></span>
* <span data-ttu-id="9dbda-263">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="9dbda-263">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="9dbda-264">Intuitiva TCP-API: er: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-264">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="9dbda-265">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="9dbda-265">ARP/RARP</span></span>

* <span data-ttu-id="9dbda-266">ARP (Address Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="9dbda-266">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="9dbda-267">RARP (reversed Address Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="9dbda-267">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="9dbda-268">Minimal 1,7 KB FLASH, RAM-storlek</span><span class="sxs-lookup"><span data-stu-id="9dbda-268">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="9dbda-269">Dynamisk matchning av 32-smörgås IPv4-och 48-smörgås MAC-adresser</span><span class="sxs-lookup"><span data-stu-id="9dbda-269">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="9dbda-270">IXIA-IxANVL verifierad</span><span class="sxs-lookup"><span data-stu-id="9dbda-270">IXIA IxANVL validated</span></span>
* <span data-ttu-id="9dbda-271">Flexibel, användardefinierad ARP-cache</span><span class="sxs-lookup"><span data-stu-id="9dbda-271">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="9dbda-272">Stöd för kostnads fria ARP</span><span class="sxs-lookup"><span data-stu-id="9dbda-272">Gratuitous ARP support</span></span>
* <span data-ttu-id="9dbda-273">Valfri ARP/RARP-statistik som fastställs av programmet</span><span class="sxs-lookup"><span data-stu-id="9dbda-273">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="9dbda-274">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="9dbda-274">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="9dbda-275">Intuitiva ARP/RARP-API: er: *nx_arp_ \** *nx_rarp_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-275">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="9dbda-276">IPv4 &amp; IPv6</span><span class="sxs-lookup"><span data-stu-id="9dbda-276">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="9dbda-277">Internet Protocol (IP)</span><span class="sxs-lookup"><span data-stu-id="9dbda-277">Internet Protocol (IP)</span></span>
* <span data-ttu-id="9dbda-278">Minimal 3,5 KB till 8,5 KB FLASH, 2 KB till 3 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="9dbda-278">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="9dbda-279">Piconet™-arkitektur</span><span class="sxs-lookup"><span data-stu-id="9dbda-279">Piconet™ architecture</span></span>
* <span data-ttu-id="9dbda-280">Snabba, nära WireSpeed prestanda</span><span class="sxs-lookup"><span data-stu-id="9dbda-280">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="9dbda-281">Stöd för flera gränssnitt</span><span class="sxs-lookup"><span data-stu-id="9dbda-281">Multiple interface support</span></span>
* <span data-ttu-id="9dbda-282">Stöd för multihomed</span><span class="sxs-lookup"><span data-stu-id="9dbda-282">Multihomed support</span></span>
* <span data-ttu-id="9dbda-283">Stöd för statisk routning</span><span class="sxs-lookup"><span data-stu-id="9dbda-283">Static routing support</span></span>
* <span data-ttu-id="9dbda-284">Stöd för IP-fragmentering/omsammansättning</span><span class="sxs-lookup"><span data-stu-id="9dbda-284">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="9dbda-285">Stöd för IPv4-och IPv6-adresser</span><span class="sxs-lookup"><span data-stu-id="9dbda-285">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="9dbda-286">IXIA-IxANVL verifierad</span><span class="sxs-lookup"><span data-stu-id="9dbda-286">IXIA IxANVL validated</span></span>
* <span data-ttu-id="9dbda-287">Fas II IPv6-färdig logo typ certifiering</span><span class="sxs-lookup"><span data-stu-id="9dbda-287">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="9dbda-288">Valfri IP-statistik</span><span class="sxs-lookup"><span data-stu-id="9dbda-288">Optional IP statistics</span></span>
* <span data-ttu-id="9dbda-289">Väl definierat, intuitivt gränssnitt för fysiskt skikt driv rutin</span><span class="sxs-lookup"><span data-stu-id="9dbda-289">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="9dbda-290">Spårning på system nivå via Azure återställnings tider TraceX</span><span class="sxs-lookup"><span data-stu-id="9dbda-290">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="9dbda-291">Intuitiva API: er för IP-lager: *\* nx_ip_*, *nxd_ip_ \**, *nxd_ipv6_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-291">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="9dbda-292">Förcertifierat av TUV och UL till IEC 61508 SIL 4, IEC 62304 klass C, ISO 26262 ASIL D och EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="9dbda-292">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="9dbda-293">Azure återställnings tider NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="9dbda-293">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="9dbda-294">Internet Protocol säkerhet (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="9dbda-294">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="9dbda-295">IP-skikt</span><span class="sxs-lookup"><span data-stu-id="9dbda-295">IP layer</span></span>
* <span data-ttu-id="9dbda-296">Stöd för maskin varu kryptering</span><span class="sxs-lookup"><span data-stu-id="9dbda-296">Hardware crypto support</span></span>
* <span data-ttu-id="9dbda-297">Stöd för program varu kryptering, inklusive:</span><span class="sxs-lookup"><span data-stu-id="9dbda-297">Software crypto support, including:</span></span>
    * <span data-ttu-id="9dbda-298">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="9dbda-298">DES, 3DES</span></span>
    * <span data-ttu-id="9dbda-299">AES</span><span class="sxs-lookup"><span data-stu-id="9dbda-299">AES</span></span>
    * <span data-ttu-id="9dbda-300">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="9dbda-300">HMAC-MD5</span></span>
    * <span data-ttu-id="9dbda-301">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="9dbda-301">HMAC-SHA1</span></span>
* <span data-ttu-id="9dbda-302">Stöd för Internet Key Exchange (IKE) version 2</span><span class="sxs-lookup"><span data-stu-id="9dbda-302">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="9dbda-303">Intuitiva IPsec-API: er: *nx_ipsec_ \**</span><span class="sxs-lookup"><span data-stu-id="9dbda-303">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="9dbda-304">IPsec är endast tillgängligt med Azure återställnings tider NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9dbda-304">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="small-footprint"></a><span data-ttu-id="9dbda-305">Små</span><span class="sxs-lookup"><span data-stu-id="9dbda-305">Small-footprint</span></span>

<span data-ttu-id="9dbda-306">Azure återställnings tider NetX Duo har ett remarkably litet utrymme på 9 KB till 15 KB för grundläggande IP-och UDP-stöd.</span><span class="sxs-lookup"><span data-stu-id="9dbda-306">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="9dbda-307">Det krävs ytterligare 10 KB till 13 KB av instruktions områdets minne för TCP-funktioner.</span><span class="sxs-lookup"><span data-stu-id="9dbda-307">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="9dbda-308">Azure återställnings tider NetX Duo RAM-användningen är vanligt vis mellan 2,6 KB och 3,6 KB plus det paket minne som definieras av programmet.</span><span class="sxs-lookup"><span data-stu-id="9dbda-308">Azure RTOS NetX Duo RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="9dbda-309">Precis som Azure återställnings tider ThreadX skalas storleken på Azure återställnings tider NetX Duo automatiskt baserat på de tjänster som används av programmet.</span><span class="sxs-lookup"><span data-stu-id="9dbda-309">Like Azure RTOS ThreadX, the size of Azure RTOS NetX Duo automatically scales based on the services used by the application.</span></span> <span data-ttu-id="9dbda-310">Detta eliminerar behovet av komplicerade konfigurations-och bygg parametrar, vilket gör det enklare för utvecklaren.</span><span class="sxs-lookup"><span data-stu-id="9dbda-310">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="9dbda-311">Snabb körning</span><span class="sxs-lookup"><span data-stu-id="9dbda-311">Fast execution</span></span>

<span data-ttu-id="9dbda-312">Azure återställnings tider NetX Duo innehåller en paket för att skicka och ta emot en nollställnings kopiering, som är mycket integrerat med Azure återställnings tider ThreadX, för att uppnå snabbast möjliga prestanda.</span><span class="sxs-lookup"><span data-stu-id="9dbda-312">Azure RTOS NetX Duo provides a zero-copy packet send/receive implementation, highly integrated with Azure RTOS ThreadX, to achieve the fastest possible performance.</span></span> <span data-ttu-id="9dbda-313">Till exempel kan Azure återställnings tider NetX Duo normalt uppnå nära WireSpeed-dataöverföringar på en 80 MHz-processor (eller mindre) och bara använda en liten procent andel av processorns cykler.</span><span class="sxs-lookup"><span data-stu-id="9dbda-313">For example, Azure RTOS NetX Duo can typically achieve near wirespeed data transfers on an 80 MHz (or less) processor, while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="9dbda-314">Enkel, lätt att använda</span><span class="sxs-lookup"><span data-stu-id="9dbda-314">Simple, easy-to-use</span></span>

<span data-ttu-id="9dbda-315">Azure återställnings tider NetX Duo-API: n är intuitiv, enkel och mycket funktionell.</span><span class="sxs-lookup"><span data-stu-id="9dbda-315">The Azure RTOS NetX Duo API is intuitive, straightforward,  and highly functional.</span></span>

<span data-ttu-id="9dbda-316">API-namnen består av riktiga ord och inte "alfabet soppor" eller förkortade namn som är vanliga i andra nätverks produkter.</span><span class="sxs-lookup"><span data-stu-id="9dbda-316">The API names are made of real words and not the “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="9dbda-317">Alla Azure återställnings tider NetX Duo-API: er har en ledande *nx_* och följer en namn konvention för substantiv-verb.</span><span class="sxs-lookup"><span data-stu-id="9dbda-317">All Azure RTOS NetX Duo APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="9dbda-318">Det finns dessutom en funktions konsekvens i hela API: et.</span><span class="sxs-lookup"><span data-stu-id="9dbda-318">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="9dbda-319">Till exempel har alla API-funktioner som pausas en valfri tids gräns som fungerar på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="9dbda-319">For example, all API functions that suspend have an optional timeout that operates in an identical manner.</span></span>

<span data-ttu-id="9dbda-320">För äldre program erbjuder Azure återställnings tider NetX Duo ytterligare ett BSD-kompatibelt lager.</span><span class="sxs-lookup"><span data-stu-id="9dbda-320">For legacy applications, Azure RTOS NetX Duo offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="9dbda-321">Det här lagret hjälper utvecklare att migrera stora nätverks program utan problem.</span><span class="sxs-lookup"><span data-stu-id="9dbda-321">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="9dbda-322">Säkert och säkert</span><span class="sxs-lookup"><span data-stu-id="9dbda-322">Safe and secure</span></span>

<span data-ttu-id="9dbda-323">Azure återställnings tider NetX Duo är säkert.</span><span class="sxs-lookup"><span data-stu-id="9dbda-323">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="9dbda-324">Den här säkerheten tillhandahålls genom tilläggs säkerhets produkter, inklusive IPsec, SSL, TLS och DTLS.</span><span class="sxs-lookup"><span data-stu-id="9dbda-324">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="9dbda-325">Programmet har också fullständig kontroll över all extern åtkomst till Azure återställnings tider NetX Duo, vilket gör det enklare att fastställa säkerhets risk.</span><span class="sxs-lookup"><span data-stu-id="9dbda-325">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="9dbda-326">Microsoft Azure återställnings tider förser OEM-tillverkare med komponenter för att skydda kommunikationen och skapa kod-och data isolering med underliggande MCU/MPU-funktioner för maskin varu skydd.</span><span class="sxs-lookup"><span data-stu-id="9dbda-326">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="9dbda-327">I slut ändan är enhets verktygets ansvar att säkerställa att enheten fullt ut uppfyller de säkerhets krav som är kopplade till det särskilda användnings fallet.</span><span class="sxs-lookup"><span data-stu-id="9dbda-327">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="9dbda-328">Förcertifierat av TUV och UL till många säkerhets standarder</span><span class="sxs-lookup"><span data-stu-id="9dbda-328">Pre-certified  by TUV and UL to many safety standards</span></span>

<span data-ttu-id="9dbda-329">Azure återställnings tider NetX Duo har certifierats av SGS-TUV Saar för användning i säkerhets kritiska system, enligt IEC-61508 SIL 4, IEC-62304 SW säkerhets klass C, ISO 26262 ASIL D och EN 50128.</span><span class="sxs-lookup"><span data-stu-id="9dbda-329">Azure RTOS NetX Duo has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="9dbda-330">Certifieringen bekräftar att Azure återställnings tider NetX Duo kan användas i utvecklingen av säkerhetsrelaterad program vara för den högsta säkerhets integritets nivån för IEC-61508, IEC-62304, ISO 26262 och EN 50128 för "fungerande säkerhet för elektriska, elektroniska och programmerbara elektroniskt säkerhetsrelaterade system".</span><span class="sxs-lookup"><span data-stu-id="9dbda-330">The certification confirms that Azure RTOS NetX Duo can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="9dbda-331">SGS – TUV Saar, som bildas genom ett gemensamt venture i Tyskland SGS-Group och TUV Saarland, har blivit det ledande ackrediterade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad program vara för säkerhetsrelaterade system i hela världen.</span><span class="sxs-lookup"><span data-stu-id="9dbda-331">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="9dbda-332">Den industriella säkerhets standarden IEC 61508 och alla standarder som är härledda från IT, inklusive IEC-62304, ISO 26262 och EN 50128, används för att säkerställa den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, process kontroll system, industriella maskiner, bil-och järnvägs styrnings system.</span><span class="sxs-lookup"><span data-stu-id="9dbda-332">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="SGS – TUV-certifiering":::

<span data-ttu-id="9dbda-334">Azure återställnings tider NetX Duo har erkänts av UL för att följa UL 60730-1 bilaga H, CSA E60730-1 bilaga H, IEC 60730-1 bilaga H, UL 60335-1 Bilaga R, IEC 60335-1 Bilaga R och UL 1998 säkerhets standarder för program vara i programmerbara komponenter.</span><span class="sxs-lookup"><span data-stu-id="9dbda-334">Azure RTOS NetX Duo has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="9dbda-335">UL är ett globalt, oberoende, säkerhets vetenskaps företag med mer än en Century av expertis som förnyar säkerhetslösningar, från det offentliga införandet av elektricitet till genombrott i hållbarhet, förnybar energi och Nanotechnology.</span><span class="sxs-lookup"><span data-stu-id="9dbda-335">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="CRU UL-certifiering":::

<span data-ttu-id="9dbda-337">Artefakter (certifikat, säkerhets hand bok, test rapport osv.) som är associerade med TUV och UL-certifieringar är tillgängliga för försäljning.</span><span class="sxs-lookup"><span data-stu-id="9dbda-337">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="9dbda-338">I de fall där programmet behöver ytterligare certifiering, är en certifierings tjänst tillgänglig via Microsoft för att tillhandahålla certifierings certifiering till olika standarder med hjälp av den aktuella maskin varu plattformen och till och med program koden.</span><span class="sxs-lookup"><span data-stu-id="9dbda-338">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span> <span data-ttu-id="9dbda-339">Kontakta oss för mer information om vår certifierings tjänst.</span><span class="sxs-lookup"><span data-stu-id="9dbda-339">Contact us for more details on our certification service.</span></span>

## <a name="eal4-common-criteria-security-certification"></a><span data-ttu-id="9dbda-340">EAL4 + gemensamma villkor säkerhets certifiering</span><span class="sxs-lookup"><span data-stu-id="9dbda-340">EAL4+ Common Criteria security certification</span></span>

<span data-ttu-id="9dbda-341">Azure återställnings tider har uppnått säkerhets certifieringen EAL4 + Common Criteria.</span><span class="sxs-lookup"><span data-stu-id="9dbda-341">Azure RTOS has achieved EAL4+ Common Criteria security certification.</span></span> <span data-ttu-id="9dbda-342">Målet för evalution (TOE) täcker Azure återställnings tider ThreadX, Azure återställnings tider NetX Duo, Azure återställnings tider NetX Secure TLS och Azure återställnings tider NetX MQTT.</span><span class="sxs-lookup"><span data-stu-id="9dbda-342">The Target of Evalution (TOE) covers Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS, and Azure RTOS NetX MQTT.</span></span> <span data-ttu-id="9dbda-343">Detta representerar de mest typiska IoT-protokollen som krävs av djupt inbäddade sensorer, enheter, yttre routrar och gatewayer.</span><span class="sxs-lookup"><span data-stu-id="9dbda-343">This represents the most typical IoT protocols required by deeply embedded sensors, devices, edge routers, and gateways.</span></span>

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="EAL-certifiering":::

<span data-ttu-id="9dbda-345">Den utvärderings funktion för IT-säkerhet som används för Microsoft Azure återställnings tider SC Security Certificate är Brightsight BV och certifikat utfärdaren är SERTIT.</span><span class="sxs-lookup"><span data-stu-id="9dbda-345">The IT Security Evaluation Facility used for the Microsoft Azure RTOS SC security certification is Brightsight BV and the Certification Authority is SERTIT.</span></span>

## <a name="fips-140-2-validated"></a><span data-ttu-id="9dbda-346">FIPS 140-2 verifierad</span><span class="sxs-lookup"><span data-stu-id="9dbda-346">FIPS 140-2 Validated</span></span>

<span data-ttu-id="9dbda-347">Azure återställnings tider NetX-krypterings bibliotek har erhållit FIPS 140-2-certifiering (Federal Information Processing 140-2 Standardization) för program vara, som anger krav för krypteringsalgoritmer.</span><span class="sxs-lookup"><span data-stu-id="9dbda-347">Azure RTOS NetX Crypto libraries have achieved Federal Information Processing Standardization 140-2 (FIPS 140-2) Certification for software, which specifies requirements for cryptography modules.</span></span> <span data-ttu-id="9dbda-348">FIPS 140-2 kräver alla federala myndigheter och avdelningar som använder kryptografisk säkerhet för att uppfylla vissa standarder som rör krypterings styrka och-funktioner.</span><span class="sxs-lookup"><span data-stu-id="9dbda-348">FIPS 140-2 requires all federal government agencies and departments that use cryptographic-based security to meet specific standards related to encryption strength and capabilities.</span></span> <span data-ttu-id="9dbda-349">Dessa kryptografiska säkerhets standarder är också kända i Kanada och EU.</span><span class="sxs-lookup"><span data-stu-id="9dbda-349">These cryptographic-based security standards are also recognized in Canada and the European Union.</span></span>

<span data-ttu-id="9dbda-350">Utvärderings versionen av informations säkerhet som används för Azure återställnings tider NetX-krypterings bibliotek var atsec och certifikat utfärdaren är National Institute of Standards and Technology (NIST).</span><span class="sxs-lookup"><span data-stu-id="9dbda-350">The Information Security evaluation lab used for Azure RTOS NetX Crypto libraries was atsec and the certification authority is The National Institute of Standards and Technology (NIST).</span></span> <span data-ttu-id="9dbda-351">Granska [NIST-webbplatsen](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) för ytterligare information.</span><span class="sxs-lookup"><span data-stu-id="9dbda-351">Review the [NIST website](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) for additional details.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="9dbda-352">Verifiering av interoperabilitet</span><span class="sxs-lookup"><span data-stu-id="9dbda-352">Interoperability verification</span></span>

<span data-ttu-id="9dbda-353">NetX Duo överensstämmer med RFC-standarder och erbjuder fullständig interoperabilitet med enheter för de flesta leverantörer.</span><span class="sxs-lookup"><span data-stu-id="9dbda-353">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![IPv6-färdig logo typ](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="9dbda-355">Azure återställnings tider NetX Duo är en av de enda inbäddade TCP/IP-stackarna för att uppnå den rigorösa IPv6-Ready-certifieringen, bevis på att den har genomgått avvikelser och samverkans, administrerad och verifierad av IPv6-forumet.</span><span class="sxs-lookup"><span data-stu-id="9dbda-355">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="9dbda-356">NetX Duo använder också IxANVL för bransch standard (automatiskt bibliotek för nätverks validering) för implementeringen av NetX Duo Core TCP/IP-protokollet.</span><span class="sxs-lookup"><span data-stu-id="9dbda-356">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="9dbda-357">Omfattande IoT-lösning</span><span class="sxs-lookup"><span data-stu-id="9dbda-357">Comprehensive IoT solution</span></span>

<span data-ttu-id="9dbda-358">Azure återställnings tider NetX Duo har ett remarkably litet utrymme på 9 KB till 15 KB för grundläggande IP-och UDP-stöd.</span><span class="sxs-lookup"><span data-stu-id="9dbda-358">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="9dbda-359">NetX Duo har ett av de mest omfattande TCP/IP-nätverken för djupt inbäddade IoT-program.</span><span class="sxs-lookup"><span data-stu-id="9dbda-359">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="9dbda-360">Det här stödet omfattar följande tilläggs protokoll produkter:</span><span class="sxs-lookup"><span data-stu-id="9dbda-360">This support includes the following add-on protocol products:</span></span>

<span data-ttu-id="9dbda-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="9dbda-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="9dbda-362">Avancerad teknik</span><span class="sxs-lookup"><span data-stu-id="9dbda-362">Advanced technology</span></span>

<span data-ttu-id="9dbda-363">Azure återställnings tider NetX Duo är en avancerad teknik som innehåller:</span><span class="sxs-lookup"><span data-stu-id="9dbda-363">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="9dbda-364">Piconet™-arkitektur</span><span class="sxs-lookup"><span data-stu-id="9dbda-364">Piconet™ architecture</span></span>
* <span data-ttu-id="9dbda-365">Automatisk skalning</span><span class="sxs-lookup"><span data-stu-id="9dbda-365">Automatic scaling</span></span>
* <span data-ttu-id="9dbda-366">™ För UDP Fast-Path Technology</span><span class="sxs-lookup"><span data-stu-id="9dbda-366">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="9dbda-367">Flexibel paket hantering</span><span class="sxs-lookup"><span data-stu-id="9dbda-367">Flexible packet management</span></span>
* <span data-ttu-id="9dbda-368">API för Zero-kopiering och implementering</span><span class="sxs-lookup"><span data-stu-id="9dbda-368">Zero-copy API and implementation</span></span>
* <span data-ttu-id="9dbda-369">Stöd för multihomed</span><span class="sxs-lookup"><span data-stu-id="9dbda-369">Multihomed support</span></span>
* <span data-ttu-id="9dbda-370">Valfri tids gräns vid alla avbrott</span><span class="sxs-lookup"><span data-stu-id="9dbda-370">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9dbda-371">Stöd för statisk routning</span><span class="sxs-lookup"><span data-stu-id="9dbda-371">Static routing support</span></span>
* <span data-ttu-id="9dbda-372">IPsec</span><span class="sxs-lookup"><span data-stu-id="9dbda-372">IPsec</span></span>
* <span data-ttu-id="9dbda-373">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="9dbda-373">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="9dbda-374">Azure återställnings tider TraceX system Analysis support</span><span class="sxs-lookup"><span data-stu-id="9dbda-374">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="9dbda-375">Snabbast tid till marknad</span><span class="sxs-lookup"><span data-stu-id="9dbda-375">Fastest time-to-market</span></span>

<span data-ttu-id="9dbda-376">Azure återställnings tider NetX Duo är enkelt att installera, lära sig, använda, felsöka, verifiera, certifiera och underhålla.</span><span class="sxs-lookup"><span data-stu-id="9dbda-376">Azure RTOS NetX Duo is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="9dbda-377">Det innebär att NetX Duo är en av de mest populära TCP/IP-stackarna för inbäddade IoT-enheter, inklusive många SoCs från Broadcom, Gainspan osv. Vår konsekventa tid till marknads fördelen bygger på:</span><span class="sxs-lookup"><span data-stu-id="9dbda-377">As a result, NetX Duo is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, etc. Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="9dbda-378">Kvalitets dokumentation – Läs vår [Användar handbok för Azure återställnings tider netx Duo](about-this-guide.md) och se själv!</span><span class="sxs-lookup"><span data-stu-id="9dbda-378">Quality documentation – please review our [Azure RTOS NetX Duo User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="9dbda-379">Fullständig käll kods tillgänglighet</span><span class="sxs-lookup"><span data-stu-id="9dbda-379">Complete source code availability</span></span>
* <span data-ttu-id="9dbda-380">Lätt att använda API</span><span class="sxs-lookup"><span data-stu-id="9dbda-380">Easy-to-use API</span></span>
* <span data-ttu-id="9dbda-381">Omfattande och avancerad funktions uppsättning</span><span class="sxs-lookup"><span data-stu-id="9dbda-381">Comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="9dbda-382">En enkel licens</span><span class="sxs-lookup"><span data-stu-id="9dbda-382">One Simple License</span></span>

<span data-ttu-id="9dbda-383">Det kostar inget att använda och testa käll koden och ingen kostnad för produktions licenser när de distribueras till förinstallerade enheter, men alla andra enheter behöver en enkel årlig licens.</span><span class="sxs-lookup"><span data-stu-id="9dbda-383">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="9dbda-384">Fullständig käll kod med högsta kvalitet</span><span class="sxs-lookup"><span data-stu-id="9dbda-384">Full, highest-quality source code</span></span>

<span data-ttu-id="9dbda-385">Under åren har Azure återställnings tider NetX Duo-källkoden ställt in kvalitet och enkel förståelse.</span><span class="sxs-lookup"><span data-stu-id="9dbda-385">Throughout the years, Azure RTOS NetX Duo source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="9dbda-386">Dessutom tillhandahåller konventionen om en funktion per fil för enkel käll navigering.</span><span class="sxs-lookup"><span data-stu-id="9dbda-386">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="9dbda-387">Har stöd för de flesta populära arkitekturerna</span><span class="sxs-lookup"><span data-stu-id="9dbda-387">Supports most popular architectures</span></span>

<span data-ttu-id="9dbda-388">Azure återställnings tider NetX Duo körs på de flesta populära 32/64-bitars mikroprocessorer som är färdiga, helt testade och fullt stödda, inklusive följande avancerade arkitekturer:</span><span class="sxs-lookup"><span data-stu-id="9dbda-388">Azure RTOS NetX Duo runs on most popular 32/64-bit microprocessors out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="9dbda-389">**Analoga enheter**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="9dbda-389">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="9dbda-390">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="9dbda-390">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="9dbda-391">**Ambiqmicro**: avsöknings MCU</span><span class="sxs-lookup"><span data-stu-id="9dbda-391">**Ambiqmicro**: pollo MCUs</span></span>

<span data-ttu-id="9dbda-392">**Arm**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitars/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="9dbda-392">**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="9dbda-393">**Takt**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="9dbda-393">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="9dbda-394">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="9dbda-394">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="9dbda-395">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="9dbda-395">**Cypress**: RISC-V</span></span>

<span data-ttu-id="9dbda-396">**Kiseldioxid**: ESI – RISC</span><span class="sxs-lookup"><span data-stu-id="9dbda-396">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="9dbda-397">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="9dbda-397">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="9dbda-398">**Intel & Intel FPGA**: X36/Pentium, XSCALE, Nios II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="9dbda-398">**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="9dbda-399">**Mikrochip**: avr32, ARM7, ARM9, cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/sa, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="9dbda-399">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="9dbda-400">**Mikrohalv**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="9dbda-400">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="9dbda-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, coldfire, Kinetis cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="9dbda-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="9dbda-402">**Renesas**: SH, HS, V850, RX, RZ, synergieffekt</span><span class="sxs-lookup"><span data-stu-id="9dbda-402">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="9dbda-403">**Silicon** Labb: EFM32</span><span class="sxs-lookup"><span data-stu-id="9dbda-403">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="9dbda-404">**Sammanfattning**: båge 600, 700, båge EM, båg HS</span><span class="sxs-lookup"><span data-stu-id="9dbda-404">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="9dbda-405">**St**: STM32, ARM7, ARM9, cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="9dbda-405">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="9dbda-406">**TL**: C5xxx, C6xxx, Stellaris, Sitara, tiva-C</span><span class="sxs-lookup"><span data-stu-id="9dbda-406">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="9dbda-407">**Wave-bearbetning**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="9dbda-407">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="9dbda-408">**Xilinx**: mikroblixt, powerpc 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="9dbda-408">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="9dbda-409">*Alla tids gränser och storleks värden i listan är uppskattningar och kan skilja sig åt på din utvecklings plattform.*</span><span class="sxs-lookup"><span data-stu-id="9dbda-409">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>

## <a name="related-services"></a><span data-ttu-id="9dbda-410">Relaterade tjänster</span><span class="sxs-lookup"><span data-stu-id="9dbda-410">Related services</span></span>

<span data-ttu-id="9dbda-411">Azure Security Center för IoT återställnings tider Security-modulen innehåller en omfattande säkerhetslösning för Azure återställnings tider-enheter.</span><span class="sxs-lookup"><span data-stu-id="9dbda-411">The Azure Security Center for IoT RTOS security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="9dbda-412">Säkerhetsmodulen för Azure återställnings tider erbjuder skadlig identifiering av nätverks aktiviteter, anpassad avisering baserad enhets beteende bas linje och hjälper till att förbättra enhetens säkerhets hygien.</span><span class="sxs-lookup"><span data-stu-id="9dbda-412">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="9dbda-413">Lär dig mer om [säkerhetsmodulen för Azure återställnings tider](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) eller kom igång med att [Konfigurera säkerhetsmodulen för Azure återställnings tider](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) snabb start.</span><span class="sxs-lookup"><span data-stu-id="9dbda-413">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9dbda-414">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="9dbda-414">Next steps</span></span>

<span data-ttu-id="9dbda-415">Om du vill veta mer om NetX Duo börjar du med [användar handboken för Azure återställnings tider netx Duo](about-this-guide.md).</span><span class="sxs-lookup"><span data-stu-id="9dbda-415">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
