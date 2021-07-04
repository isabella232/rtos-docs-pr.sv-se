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
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="78a54-103">Översikt över Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="78a54-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="78a54-104">Azure RTOS Inbäddad TCP/IP-nätverksstack i NetX Duo är Microsofts avancerade, industriella klass med dubbla IPv4- och IPv6 TCP/IP-nätverksstackar som är särskilt utformade för djupt inbäddade, realtids- och IoT-program.</span><span class="sxs-lookup"><span data-stu-id="78a54-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="78a54-105">NetX Duo tillhandahåller inbäddade program med kärnnätverksprotokoll som IPv4, IPv6, TCP och UDP samt en komplett uppsättning ytterligare protokoll på högre nivå.</span><span class="sxs-lookup"><span data-stu-id="78a54-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="78a54-106">Azure RTOS NetX Duo erbjuder säkerhet via ytterligare tillägg säkerhetsprodukter, inklusive Azure RTOS NetX Secure IPsec och Azure RTOS NetX Secure SSL/TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="78a54-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="78a54-107">Allt detta i kombination med ett litet fotavtryck, snabb körning och överlägsen användarvänlighet gör Azure RTOS NetX Duo till det perfekta valet för de mest krävande inbäddade IoT-programmen.</span><span class="sxs-lookup"><span data-stu-id="78a54-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="78a54-108">API-protokoll</span><span class="sxs-lookup"><span data-stu-id="78a54-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="78a54-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="78a54-109">MQTT</span></span>

* <span data-ttu-id="78a54-110">MQTT (Messaging Queue Telemetry Transport)</span><span class="sxs-lookup"><span data-stu-id="78a54-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="78a54-111">Minimal 2,7 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="78a54-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="78a54-112">Automatisk IP-adress</span><span class="sxs-lookup"><span data-stu-id="78a54-112">Auto IP</span></span>

* <span data-ttu-id="78a54-113">Automatisk IPv4-adresstilldelning</span><span class="sxs-lookup"><span data-stu-id="78a54-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="78a54-114">Minimalt 1,2 kB, 300 byte RAM-minne</span><span class="sxs-lookup"><span data-stu-id="78a54-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="78a54-115">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="78a54-115">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="78a54-116">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="78a54-116">HTTP 1.0</span></span>

* <span data-ttu-id="78a54-117">Hypertext Transfer Protocol(HTTP)</span><span class="sxs-lookup"><span data-stu-id="78a54-117">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="78a54-118">Minimalt 2,8 KB till 4,8 KB FLASH/0,4 KB till 1,0 KB RAM-minne</span><span class="sxs-lookup"><span data-stu-id="78a54-118">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="78a54-119">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="78a54-119">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="78a54-120">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="78a54-120">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="78a54-121">Hypertext Transfer Protocol(HTTP)</span><span class="sxs-lookup"><span data-stu-id="78a54-121">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="78a54-122">Minimalt 3,0 KB till 9,5 KB FLASH/0,5 KB till 2 KB RAM</span><span class="sxs-lookup"><span data-stu-id="78a54-122">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="78a54-123">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="78a54-123">Client and server support</span></span>
* <span data-ttu-id="78a54-124">Flera inkommande klientsessioner</span><span class="sxs-lookup"><span data-stu-id="78a54-124">Multiple incoming client sessions</span></span>
* <span data-ttu-id="78a54-125">Oformaterad text och krypterad HTTPS</span><span class="sxs-lookup"><span data-stu-id="78a54-125">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="78a54-126">Stöd för beständiga anslutningar</span><span class="sxs-lookup"><span data-stu-id="78a54-126">Persistent connection support</span></span>
* <span data-ttu-id="78a54-127">Filuppladdning med flera delar</span><span class="sxs-lookup"><span data-stu-id="78a54-127">Multipart file upload</span></span>
* <span data-ttu-id="78a54-128">Helt integrerad med Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="78a54-128">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="78a54-129">SMTP</span><span class="sxs-lookup"><span data-stu-id="78a54-129">SMTP</span></span>

* <span data-ttu-id="78a54-130">Simple Mall Transfer Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="78a54-130">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="78a54-131">Minimalt RAM-fotavtryck på 4,1 kB och 0,6 KB</span><span class="sxs-lookup"><span data-stu-id="78a54-131">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="78a54-132">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="78a54-132">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="78a54-133">DHCP</span><span class="sxs-lookup"><span data-stu-id="78a54-133">DHCP</span></span>

* <span data-ttu-id="78a54-134">DHCP (Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="78a54-134">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="78a54-135">Minimalt 3,6 kB till 4,6 KB FLASH, 2,7 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="78a54-135">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="78a54-136">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="78a54-136">Client and server support</span></span>
* <span data-ttu-id="78a54-137">Stöd för IPv4 och IPv6</span><span class="sxs-lookup"><span data-stu-id="78a54-137">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="78a54-138">NAT</span><span class="sxs-lookup"><span data-stu-id="78a54-138">NAT</span></span>

* <span data-ttu-id="78a54-139">NAT (Network Address Translation)</span><span class="sxs-lookup"><span data-stu-id="78a54-139">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="78a54-140">Minimalt RAM-fotavtryck på 3,5 K6 och 0,6 KB</span><span class="sxs-lookup"><span data-stu-id="78a54-140">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="78a54-141">Stöd för IPv4-adresser</span><span class="sxs-lookup"><span data-stu-id="78a54-141">IPv4 address support</span></span>
* <span data-ttu-id="78a54-142">NAT är endast tillgängligt med Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="78a54-142">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="78a54-143">SNMP</span><span class="sxs-lookup"><span data-stu-id="78a54-143">SNMP</span></span>

* <span data-ttu-id="78a54-144">Simple Network Management Protocol (SNMP)</span><span class="sxs-lookup"><span data-stu-id="78a54-144">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="78a54-145">Minimalt RAM-fotavtryck på 10,9 kB och 2,6 KB</span><span class="sxs-lookup"><span data-stu-id="78a54-145">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="78a54-146">Agentstöd för VI, V2 och V3</span><span class="sxs-lookup"><span data-stu-id="78a54-146">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="78a54-147">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="78a54-147">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="78a54-148">DNS (Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="78a54-148">Domain Name System (DNS)</span></span>
* <span data-ttu-id="78a54-149">Multicast Domain Name System (mDNS)</span><span class="sxs-lookup"><span data-stu-id="78a54-149">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="78a54-150">DNS-baserad tjänstidentifiering (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="78a54-150">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="78a54-151">DNS Minimalt 2,4 KB till 3 KB FLASH, 1 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="78a54-151">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="78a54-152">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="78a54-152">Client support</span></span>
* <span data-ttu-id="78a54-153">mDNS och DNS-SD är endast tillgängliga med Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="78a54-153">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="pop3"></a><span data-ttu-id="78a54-154">POP3</span><span class="sxs-lookup"><span data-stu-id="78a54-154">POP3</span></span>

* <span data-ttu-id="78a54-155">Post Office Protocol Version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="78a54-155">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="78a54-156">Minimalt RAM-fotavtryck på 8,1 kB och 1,4 KB</span><span class="sxs-lookup"><span data-stu-id="78a54-156">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="78a54-157">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="78a54-157">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="78a54-158">Telnet</span><span class="sxs-lookup"><span data-stu-id="78a54-158">TELNET</span></span>

* <span data-ttu-id="78a54-159">Minimalt RAM-fotavtryck på 0,5 kB och 0,3 KB</span><span class="sxs-lookup"><span data-stu-id="78a54-159">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="78a54-160">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="78a54-160">Client and server support</span></span>
* <span data-ttu-id="78a54-161">Intuitiva Telnet-API:er: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="78a54-161">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="78a54-162">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="78a54-162">FTP, TFTP</span></span>

* <span data-ttu-id="78a54-163">File Transfer Protocol (FTP)</span><span class="sxs-lookup"><span data-stu-id="78a54-163">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="78a54-164">Trivial file transfer protocol (TFTP)</span><span class="sxs-lookup"><span data-stu-id="78a54-164">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="78a54-165">FTP minimalt 1,8 KB till 7,2 KB FLASH, 0,6 kB till 2,1 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="78a54-165">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="78a54-166">TFTP Minimal 1,7 KB till 2,4 KB FLASH, 0,3 kB till 1,8 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="78a54-166">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="78a54-167">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="78a54-167">Client and server support</span></span>
* <span data-ttu-id="78a54-168">Intuitiva FTP- och *TFTP-API:er: \* nx_ftp_* eller *\* nx_tftp_*</span><span class="sxs-lookup"><span data-stu-id="78a54-168">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="78a54-169">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="78a54-169">PPP, PPPoE</span></span>

* <span data-ttu-id="78a54-170">Polnt-to-PoInt Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="78a54-170">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="78a54-171">Point-to-Point Protocol over Ethernet(PPPoE)</span><span class="sxs-lookup"><span data-stu-id="78a54-171">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="78a54-172">Minimalt RAM-fotavtryck på 7,1 kB och 3,8 KB</span><span class="sxs-lookup"><span data-stu-id="78a54-172">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="78a54-173">Intuitiva PPP-API:er: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="78a54-173">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="78a54-174">PPPoE är endast tillgängligt med Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="78a54-174">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="78a54-175">Sntp</span><span class="sxs-lookup"><span data-stu-id="78a54-175">SNTP</span></span>

* <span data-ttu-id="78a54-176">Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="78a54-176">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="78a54-177">Minimalt 4 KB och 0,5 KB RAM</span><span class="sxs-lookup"><span data-stu-id="78a54-177">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="78a54-178">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="78a54-178">Client support</span></span>
* <span data-ttu-id="78a54-179">Intuitiva SNTP-API:er: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="78a54-179">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="78a54-180">Azure RTOS NetX Duo API</span><span class="sxs-lookup"><span data-stu-id="78a54-180">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="78a54-181">Intuitivt och konsekvent API</span><span class="sxs-lookup"><span data-stu-id="78a54-181">Intuitive and consistent API</span></span>
* <span data-ttu-id="78a54-182">Namngivningskonvention för substantiv-verb</span><span class="sxs-lookup"><span data-stu-id="78a54-182">Noun-verb naming convention</span></span>
* <span data-ttu-id="78a54-183">Snabb IMPLEMENTERING av API:et nollkopiering</span><span class="sxs-lookup"><span data-stu-id="78a54-183">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="78a54-184">Alla API:er har ledande <i>nx_\*</i> för att enkelt identifiera som Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="78a54-184">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="78a54-185">Blockerande API:er har valfri tidsgräns för tråd</span><span class="sxs-lookup"><span data-stu-id="78a54-185">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="78a54-186">Mer Azure RTOS finns i användarhandboken för [NetX Duo](about-this-guide.md)</span><span class="sxs-lookup"><span data-stu-id="78a54-186">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="78a54-187">Valfritt BSD-lager för portning av äldre socketkod</span><span class="sxs-lookup"><span data-stu-id="78a54-187">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="78a54-188">Igmp</span><span class="sxs-lookup"><span data-stu-id="78a54-188">IGMP</span></span>

* <span data-ttu-id="78a54-189">Internet Grupphanteringsprotokoll (IGMP)</span><span class="sxs-lookup"><span data-stu-id="78a54-189">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="78a54-190">Minimal 2,5 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="78a54-190">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="78a54-191">Stöd för IPv4-multicast-grupper</span><span class="sxs-lookup"><span data-stu-id="78a54-191">IPv4 multicast group support</span></span>
* <span data-ttu-id="78a54-192">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="78a54-192">IXIA IxANVL validated</span></span>
* <span data-ttu-id="78a54-193">Valfri IGMP-statistik</span><span class="sxs-lookup"><span data-stu-id="78a54-193">Optional IGMP statistics</span></span>
* <span data-ttu-id="78a54-194">Spårning på systemnivå via Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="78a54-194">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="78a54-195">Intuitiva IGMP-API:er: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="78a54-195">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="78a54-196">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="78a54-196">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="78a54-197">Datagram Transport Layer Security (DTLS) 1.0 och 1.2</span><span class="sxs-lookup"><span data-stu-id="78a54-197">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="78a54-198">Minimalt 11 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="78a54-198">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="78a54-199">Snabb, programvara RSA 2048-bitars nyckelstorlek ~ 1 sekund @120MHz</span><span class="sxs-lookup"><span data-stu-id="78a54-199">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="78a54-200">Effektiviserad X.509-implementering</span><span class="sxs-lookup"><span data-stu-id="78a54-200">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="78a54-201">Helt integrerad med Azure RTOS NetX Duo UDP-sockets</span><span class="sxs-lookup"><span data-stu-id="78a54-201">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="78a54-202">Stöd för maskinvarukryptutor</span><span class="sxs-lookup"><span data-stu-id="78a54-202">Hardware Crypto Support</span></span>
* <span data-ttu-id="78a54-203">Stöd för kryptografiprogram: RSA (alla nyckelstorlekar), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="78a54-203">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="78a54-204">Elliptic Curve Cryptography (ECC) med ECDSA (signering) och ECDH (kryptering), inklusive P-kurvor 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="78a54-204">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="78a54-205">Stöd för krypterad nyckel (maskinvaruberoende)</span><span class="sxs-lookup"><span data-stu-id="78a54-205">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="78a54-206">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="78a54-206">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="78a54-207">Transport Layer Security (TLS) 1.0, 1.1 och 1.2</span><span class="sxs-lookup"><span data-stu-id="78a54-207">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="78a54-208">Minimal 8,8 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="78a54-208">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="78a54-209">Snabb RSA 2048-bitars nyckelstorlek för programvara ~ 1 sekund @120MHz</span><span class="sxs-lookup"><span data-stu-id="78a54-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="78a54-210">Effektiviserad X.509-implementering</span><span class="sxs-lookup"><span data-stu-id="78a54-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="78a54-211">Helt integrerad med Azure RTOS NetX Duo TCP-sockets</span><span class="sxs-lookup"><span data-stu-id="78a54-211">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="78a54-212">Stöd för maskinvarukryptutor</span><span class="sxs-lookup"><span data-stu-id="78a54-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="78a54-213">Stöd för kryptografiprogram: RSA (alla nyckelstorlekar), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="78a54-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="78a54-214">Elliptic Curve Cryptography (ECC) med ECDSA (signering) och ECDH (kryptering), inklusive P-kurvor 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="78a54-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="78a54-215">Stöd för krypterad nyckel (maskinvaruberoende)</span><span class="sxs-lookup"><span data-stu-id="78a54-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="78a54-216">ICMP</span><span class="sxs-lookup"><span data-stu-id="78a54-216">ICMP</span></span>

* <span data-ttu-id="78a54-217">Internet Control Message Protocol (ICMP)</span><span class="sxs-lookup"><span data-stu-id="78a54-217">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="78a54-218">Minimal 2,5 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="78a54-218">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="78a54-219">Stöd för IPv4 och IPv6</span><span class="sxs-lookup"><span data-stu-id="78a54-219">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="78a54-220">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="78a54-220">IXIA IxANVL validated</span></span>
* <span data-ttu-id="78a54-221">Pingbegäran och pingsvar</span><span class="sxs-lookup"><span data-stu-id="78a54-221">Ping request and ping response</span></span>
* <span data-ttu-id="78a54-222">Valfri trådavstängning vid ping-begäranden</span><span class="sxs-lookup"><span data-stu-id="78a54-222">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="78a54-223">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="78a54-223">Optional timeout on all suspension</span></span>
* <span data-ttu-id="78a54-224">Valfri ICMP-statistik</span><span class="sxs-lookup"><span data-stu-id="78a54-224">Optional ICMP statistics</span></span>
* <span data-ttu-id="78a54-225">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="78a54-225">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="78a54-226">Intuitiva ICMP-API:er: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="78a54-226">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="78a54-227">UDP</span><span class="sxs-lookup"><span data-stu-id="78a54-227">UDP</span></span>

* <span data-ttu-id="78a54-228">UDP (User Datagram Protocol)</span><span class="sxs-lookup"><span data-stu-id="78a54-228">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="78a54-229">Minimalt 2,5 KB FLASH, 124 sockets byte RAM-minne per socket</span><span class="sxs-lookup"><span data-stu-id="78a54-229">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="78a54-230">Snabb TCP-paketbearbetning med nära wire speed:</span><span class="sxs-lookup"><span data-stu-id="78a54-230">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="78a54-231">RX 95 Mbit/s på 100 Mbit/s Ethernet, @100MHz MCU, 14 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="78a54-231">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="78a54-232">TX 94 Mbit/s på 100 Mbit/s Ethernet, @100MHz MCU, 10 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="78a54-232">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="78a54-233">UDP Fast Path™teknik</span><span class="sxs-lookup"><span data-stu-id="78a54-233">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="78a54-234">Inga gränser för antalet UDP</span><span class="sxs-lookup"><span data-stu-id="78a54-234">No limits on the number of UDP</span></span>
* <span data-ttu-id="78a54-235">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="78a54-235">IXIA IxANVL validated</span></span>
* <span data-ttu-id="78a54-236">Valfri stängning vid socket-mottagning</span><span class="sxs-lookup"><span data-stu-id="78a54-236">Optional suspension on socket receive</span></span>
* <span data-ttu-id="78a54-237">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="78a54-237">Optional timeout on all suspension</span></span>
* <span data-ttu-id="78a54-238">Valfri UDP-statistik</span><span class="sxs-lookup"><span data-stu-id="78a54-238">Optional UDP statistics</span></span>
* <span data-ttu-id="78a54-239">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="78a54-239">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="78a54-240">Intuitiva UDP-API:er: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="78a54-240">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="78a54-241">TCP</span><span class="sxs-lookup"><span data-stu-id="78a54-241">TCP</span></span>

* <span data-ttu-id="78a54-242">Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="78a54-242">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="78a54-243">Minimal 10,5K8 till 12,5 KB FLASH, 280 byte RAM-minne per socket</span><span class="sxs-lookup"><span data-stu-id="78a54-243">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="78a54-244">Snabb, nära wlre speed TCP-paketbearbetning:</span><span class="sxs-lookup"><span data-stu-id="78a54-244">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="78a54-245">RX 93 Mbit/s på 100 Mbit/s Ethernet, @100MHz MCU, 20 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="78a54-245">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="78a54-246">TX 94 Mbit/s på 100 Mbit/s Ethernet, @100MHz MCU, 27 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="78a54-246">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="78a54-247">Tillförlitlig anslutning</span><span class="sxs-lookup"><span data-stu-id="78a54-247">Reliable connection</span></span>
* <span data-ttu-id="78a54-248">Inga gränser för antalet TCP-socketar</span><span class="sxs-lookup"><span data-stu-id="78a54-248">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="78a54-249">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="78a54-249">IXIA IxANVL validated</span></span>
* <span data-ttu-id="78a54-250">Valfri stängning vid socket-mottagning/-överföring</span><span class="sxs-lookup"><span data-stu-id="78a54-250">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="78a54-251">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="78a54-251">Optional timeout on all suspension</span></span>
* <span data-ttu-id="78a54-252">Valfri TCP-statistik</span><span class="sxs-lookup"><span data-stu-id="78a54-252">Optional TCP statistics</span></span>
* <span data-ttu-id="78a54-253">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="78a54-253">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="78a54-254">Intuitiva TCP-API:er: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="78a54-254">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="78a54-255">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="78a54-255">ARP/RARP</span></span>

* <span data-ttu-id="78a54-256">Address Resolution Protocol (ARP)</span><span class="sxs-lookup"><span data-stu-id="78a54-256">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="78a54-257">Reverse Address Resolution Protocol (RARP)</span><span class="sxs-lookup"><span data-stu-id="78a54-257">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="78a54-258">Minimal 1,7 KB FLASH, RAM-storlek</span><span class="sxs-lookup"><span data-stu-id="78a54-258">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="78a54-259">Dynamisk upplösning av 32-blt IPv4- och 48-blt MAC-adresser</span><span class="sxs-lookup"><span data-stu-id="78a54-259">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="78a54-260">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="78a54-260">IXIA IxANVL validated</span></span>
* <span data-ttu-id="78a54-261">Flexibel, användardefinierad ARP-cache</span><span class="sxs-lookup"><span data-stu-id="78a54-261">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="78a54-262">Gratuitous ARP support</span><span class="sxs-lookup"><span data-stu-id="78a54-262">Gratuitous ARP support</span></span>
* <span data-ttu-id="78a54-263">Valfri ARP/RARP-statistik som bestäms av programmet</span><span class="sxs-lookup"><span data-stu-id="78a54-263">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="78a54-264">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="78a54-264">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="78a54-265">Intuitiva ARP/RARP-API:nx_arp_ *\**, *\* nx_rarp_*</span><span class="sxs-lookup"><span data-stu-id="78a54-265">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="78a54-266">IPv4 &amp; IPv6</span><span class="sxs-lookup"><span data-stu-id="78a54-266">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="78a54-267">Internet Protocol (IP)</span><span class="sxs-lookup"><span data-stu-id="78a54-267">Internet Protocol (IP)</span></span>
* <span data-ttu-id="78a54-268">Minimal 3,5 kB till 8,5 KB FLASH, 2 KB till 3 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="78a54-268">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="78a54-269">Piconet™arkitektur</span><span class="sxs-lookup"><span data-stu-id="78a54-269">Piconet™ architecture</span></span>
* <span data-ttu-id="78a54-270">Snabba, nära wire speed-prestanda</span><span class="sxs-lookup"><span data-stu-id="78a54-270">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="78a54-271">Stöd för flera gränssnitt</span><span class="sxs-lookup"><span data-stu-id="78a54-271">Multiple interface support</span></span>
* <span data-ttu-id="78a54-272">Stöd för flera start</span><span class="sxs-lookup"><span data-stu-id="78a54-272">Multihomed support</span></span>
* <span data-ttu-id="78a54-273">Stöd för statisk routning</span><span class="sxs-lookup"><span data-stu-id="78a54-273">Static routing support</span></span>
* <span data-ttu-id="78a54-274">Stöd för IP-fragmentering/återmontering</span><span class="sxs-lookup"><span data-stu-id="78a54-274">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="78a54-275">Stöd för IPv4- och IPv6-adresser</span><span class="sxs-lookup"><span data-stu-id="78a54-275">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="78a54-276">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="78a54-276">IXIA IxANVL validated</span></span>
* <span data-ttu-id="78a54-277">Fas II IPv6 Ready Logo Certification (IPv6-redo logotypcertifiering)</span><span class="sxs-lookup"><span data-stu-id="78a54-277">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="78a54-278">Valfri IP-statistik</span><span class="sxs-lookup"><span data-stu-id="78a54-278">Optional IP statistics</span></span>
* <span data-ttu-id="78a54-279">Väldefinierat, intuitivt drivrutinsgränssnitt på fysiskt lager</span><span class="sxs-lookup"><span data-stu-id="78a54-279">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="78a54-280">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="78a54-280">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="78a54-281">Intuitiva API:er för *IP-lager: \* nx_ip_*, *nxd_ip_ \** *\** , nxd_ipv6_</span><span class="sxs-lookup"><span data-stu-id="78a54-281">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="78a54-282">Förcertifierat av TUV och UL till IEC 61508 SIL 4, IEC 62304 Klass C, ISO 26262 ASIL D och EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="78a54-282">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="78a54-283">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="78a54-283">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="78a54-284">Internet Protocol Security (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="78a54-284">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="78a54-285">IP-lager</span><span class="sxs-lookup"><span data-stu-id="78a54-285">IP layer</span></span>
* <span data-ttu-id="78a54-286">Stöd för maskinvarukryptutor</span><span class="sxs-lookup"><span data-stu-id="78a54-286">Hardware crypto support</span></span>
* <span data-ttu-id="78a54-287">Stöd för kryptografiprogram, inklusive:</span><span class="sxs-lookup"><span data-stu-id="78a54-287">Software crypto support, including:</span></span>
    * <span data-ttu-id="78a54-288">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="78a54-288">DES, 3DES</span></span>
    * <span data-ttu-id="78a54-289">AES</span><span class="sxs-lookup"><span data-stu-id="78a54-289">AES</span></span>
    * <span data-ttu-id="78a54-290">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="78a54-290">HMAC-MD5</span></span>
    * <span data-ttu-id="78a54-291">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="78a54-291">HMAC-SHA1</span></span>
* <span data-ttu-id="78a54-292">Stöd för Internet Key Exchange (IKE) Version 2</span><span class="sxs-lookup"><span data-stu-id="78a54-292">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="78a54-293">Intuitiva IPsec-API:er: *nx_ipsec_ \**</span><span class="sxs-lookup"><span data-stu-id="78a54-293">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="78a54-294">IPsec är endast tillgängligt med Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="78a54-294">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="78a54-295">Valv och säkert</span><span class="sxs-lookup"><span data-stu-id="78a54-295">Safe and secure</span></span>

<span data-ttu-id="78a54-296">Azure RTOS NetX Duo är säker.</span><span class="sxs-lookup"><span data-stu-id="78a54-296">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="78a54-297">Den här säkerheten tillhandahålls via tilläggssäkerhetsprodukter, inklusive IPsec, SSL, TLS och DTLS.</span><span class="sxs-lookup"><span data-stu-id="78a54-297">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="78a54-298">Dessutom har programmet fullständig kontroll över all extern åtkomst till Azure RTOS NetX Duo, vilket gör det mycket enklare att fastställa säkerhetsrisker.</span><span class="sxs-lookup"><span data-stu-id="78a54-298">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="78a54-299">Microsoft Azure RTOS tillhandahåller OEM-tillverkare med komponenter för säker kommunikation och för att skapa kod- och dataisolering med underliggande MCU/MPU-maskinvaruskyddsmekanismer.</span><span class="sxs-lookup"><span data-stu-id="78a54-299">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="78a54-300">Det är i slutänden enhetsbyggarens ansvar att se till att enheten uppfyller de föränderliga säkerhetskrav som är associerade med dess specifika användningsfall.</span><span class="sxs-lookup"><span data-stu-id="78a54-300">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>


## <a name="interoperability-verification"></a><span data-ttu-id="78a54-301">Interoperabilitetsverifiering</span><span class="sxs-lookup"><span data-stu-id="78a54-301">Interoperability verification</span></span>

<span data-ttu-id="78a54-302">NetX Duo följer RFC-standarder och erbjuder fullständig samverkan med enheter för de flesta leverantörer.</span><span class="sxs-lookup"><span data-stu-id="78a54-302">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Logotyp för IPv6-klar](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="78a54-304">Azure RTOS NetX Duo är en av de enda inbäddade TCP/IP-stackarna för att uppnå rigorös IPv6-Ready Logo-certifiering, bevis på att den har klarat överensstämmelse- och samverkanstester som administreras och verifierats av IPv6-forumet.</span><span class="sxs-lookup"><span data-stu-id="78a54-304">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="78a54-305">NetX Duo använder också branschstandarden IxANVL (Automated Network Validation Library) för netX Duo-kärnimplementeringen av TCP/IP-protokollet.</span><span class="sxs-lookup"><span data-stu-id="78a54-305">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="78a54-306">Omfattande IoT-lösning</span><span class="sxs-lookup"><span data-stu-id="78a54-306">Comprehensive IoT solution</span></span>

<span data-ttu-id="78a54-307">NetX Duo har ett av de mest omfattande TCP/IP-nätverken för djupt inbäddade IoT-program.</span><span class="sxs-lookup"><span data-stu-id="78a54-307">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="78a54-308">Det här stödet omfattar följande tillägg protokollprodukter.</span><span class="sxs-lookup"><span data-stu-id="78a54-308">This support includes the following add-on protocol products.</span></span>

<span data-ttu-id="78a54-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="78a54-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="78a54-310">Avancerad teknik</span><span class="sxs-lookup"><span data-stu-id="78a54-310">Advanced technology</span></span>

<span data-ttu-id="78a54-311">Azure RTOS NetX Duo är avancerad teknik som omfattar:</span><span class="sxs-lookup"><span data-stu-id="78a54-311">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="78a54-312">Piconet™arkitektur</span><span class="sxs-lookup"><span data-stu-id="78a54-312">Piconet™ architecture</span></span>
* <span data-ttu-id="78a54-313">Automatisk skalning</span><span class="sxs-lookup"><span data-stu-id="78a54-313">Automatic scaling</span></span>
* <span data-ttu-id="78a54-314">UDP Fast-Path Technology™</span><span class="sxs-lookup"><span data-stu-id="78a54-314">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="78a54-315">Flexibel pakethantering</span><span class="sxs-lookup"><span data-stu-id="78a54-315">Flexible packet management</span></span>
* <span data-ttu-id="78a54-316">API med nollkopiering och implementering</span><span class="sxs-lookup"><span data-stu-id="78a54-316">Zero-copy API and implementation</span></span>
* <span data-ttu-id="78a54-317">Stöd för flera start</span><span class="sxs-lookup"><span data-stu-id="78a54-317">Multihomed support</span></span>
* <span data-ttu-id="78a54-318">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="78a54-318">Optional timeout on all suspension</span></span>
* <span data-ttu-id="78a54-319">Stöd för statisk routning</span><span class="sxs-lookup"><span data-stu-id="78a54-319">Static routing support</span></span>
* <span data-ttu-id="78a54-320">IPsec</span><span class="sxs-lookup"><span data-stu-id="78a54-320">IPsec</span></span>
* <span data-ttu-id="78a54-321">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="78a54-321">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="78a54-322">Azure RTOS traceX-systemanalysstöd</span><span class="sxs-lookup"><span data-stu-id="78a54-322">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="78a54-323">Relaterade tjänster</span><span class="sxs-lookup"><span data-stu-id="78a54-323">Related services</span></span>

### <a name="azure-iot"></a><span data-ttu-id="78a54-324">Azure IoT</span><span class="sxs-lookup"><span data-stu-id="78a54-324">Azure IoT</span></span>

<span data-ttu-id="78a54-325">NetX Duo innehåller [Azure IoT Middleware för Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), ett plattformsspecifikt bibliotek som fungerar som ett bindningslager mellan Azure RTOS och Azure SDK för Embedded C för att underlätta anslutningen till Azure IoT-tjänster.</span><span class="sxs-lookup"><span data-stu-id="78a54-325">NetX Duo includes [Azure IoT Middleware for Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), a platform-specific library that acts as a binding layer between the Azure RTOS and the Azure SDK for Embedded C to facilitate connectivity to Azure IoT services.</span></span> <span data-ttu-id="78a54-326">Målen med Azure IoT Middleware är följande.</span><span class="sxs-lookup"><span data-stu-id="78a54-326">The goals of Azure IoT Middleware are the following.</span></span>
* <span data-ttu-id="78a54-327">Tillhandahåll de smarta klientgränssnitt (IoTHub_Client, DeviceProvisioning_Client) som utvecklare behöver för sina program.</span><span class="sxs-lookup"><span data-stu-id="78a54-327">Provide the smart client interfaces (IoTHub_Client, DeviceProvisioning_Client) that developers need for their applications.</span></span>
* <span data-ttu-id="78a54-328">Samordna interaktionen mellan Embedded C SDK och plattformen.</span><span class="sxs-lookup"><span data-stu-id="78a54-328">Orchestrate the interaction between the Embedded C SDK and the platform.</span></span>
* <span data-ttu-id="78a54-329">Tillhandahåll Azure RTOS plattformsinitiering.</span><span class="sxs-lookup"><span data-stu-id="78a54-329">Provide Azure RTOS platform initialization.</span></span>
* <span data-ttu-id="78a54-330">IoT Plug and Play support.</span><span class="sxs-lookup"><span data-stu-id="78a54-330">IoT Plug and Play support.</span></span>
* <span data-ttu-id="78a54-331">Säkerhetsfunktioner.</span><span class="sxs-lookup"><span data-stu-id="78a54-331">Security capabilities.</span></span>
* <span data-ttu-id="78a54-332">Resursbegränsningsmedveten.</span><span class="sxs-lookup"><span data-stu-id="78a54-332">Resource limitation aware.</span></span>
* <span data-ttu-id="78a54-333">Protokollstöd.</span><span class="sxs-lookup"><span data-stu-id="78a54-333">Protocol support.</span></span>

![Azure RTOS NetX Duo Related Services](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a><span data-ttu-id="78a54-335">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="78a54-335">Azure Defender</span></span>

<span data-ttu-id="78a54-336">Säkerhetsmodulen Azure Defender for IoT innehåller en omfattande säkerhetslösning för Azure RTOS enheter.</span><span class="sxs-lookup"><span data-stu-id="78a54-336">The Azure Defender for IoT security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="78a54-337">Säkerhetsmodulen för Azure RTOS erbjuder identifiering av aktiviteter i skadliga nätverk, anpassade aviseringsbaserade enhetsbeteenden som baserar sig på och hjälper till att förbättra enhetens säkerhetshygien.</span><span class="sxs-lookup"><span data-stu-id="78a54-337">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="78a54-338">Läs mer om [säkerhetsmodulen för Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) eller kom igång med [snabbstarten Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) (Konfigurera säkerhetsmodul för Azure RTOS).</span><span class="sxs-lookup"><span data-stu-id="78a54-338">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

### <a name="device-update-for-iot-hub"></a><span data-ttu-id="78a54-339">Enhetsuppdatering för IoT Hub</span><span class="sxs-lookup"><span data-stu-id="78a54-339">Device Update for IoT Hub</span></span>

<span data-ttu-id="78a54-340">[Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) är en tjänst som gör att du kan distribuera trådlösa uppdateringar (OTA) för dina IoT-enheter.</span><span class="sxs-lookup"><span data-stu-id="78a54-340">The [Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) is a service that enables you to deploy over-the-air updates (OTA) for your IoT devices.</span></span> <span data-ttu-id="78a54-341">Modulen Enhetsuppdatering för IoT Hub är implementeringen av Enhetsuppdatering för IoT Hub Agent i Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="78a54-341">The Device Update for IoT Hub module is the implementation of Device Update for IoT Hub Agent in Azure RTOS NetX Duo.</span></span> <span data-ttu-id="78a54-342">Den innehåller enkla API:er som gör att enhetsbyggare kan integrera funktionen Enhetsuppdatering i sina program.</span><span class="sxs-lookup"><span data-stu-id="78a54-342">It provides simple APIs for device builders to integrate the Device Update capability in their application.</span></span>

<span data-ttu-id="78a54-343">Se exempel på viktiga utvärderingstavlor som innehåller kom igång-guiderna för att lära dig att konfigurera, bygga och distribuera trådlösa uppdateringar (OTA) till enheterna.</span><span class="sxs-lookup"><span data-stu-id="78a54-343">See the samples of key semiconductors evaluation boards that include the get started guides to learn configure, build and deploy the over-the-air (OTA) updates to the devices.</span></span>

<span data-ttu-id="78a54-344">Du kan också läsa mer om hur du [använder Enhetsuppdatering för IoT Hub med Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span><span class="sxs-lookup"><span data-stu-id="78a54-344">And you can learn more details about use [Device Update for IoT Hub with Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span></span>

## <a name="next-steps"></a><span data-ttu-id="78a54-345">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="78a54-345">Next steps</span></span>

<span data-ttu-id="78a54-346">Om du vill veta mer om NetX Duo börjar du [med Azure RTOS användarhandbok för NetX Duo.](about-this-guide.md)</span><span class="sxs-lookup"><span data-stu-id="78a54-346">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
