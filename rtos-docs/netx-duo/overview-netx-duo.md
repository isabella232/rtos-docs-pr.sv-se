---
title: Förstå Azure RTOS NetX Duo
description: Azure RTOS NetX Duo är en avancerad TCP/IP-nätverksstack i branschklass som är utformad specifikt för djupt inbäddade realtids- och IoT-program.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: b40a57bf385ddcf623ff7cbe0d2e798c547227d7
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754904"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="fc952-103">Översikt över Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="fc952-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="fc952-104">Azure RTOS Inbäddad TCP/IP-nätverksstack för NetX Duo är Microsofts avancerade, industriella dubbla IPv4- och IPv6 TCP/IP-nätverksstack som är utformad specifikt för djupt inbäddade, realtids- och IoT-program.</span><span class="sxs-lookup"><span data-stu-id="fc952-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="fc952-105">NetX Duo tillhandahåller inbäddade program med kärnnätverksprotokoll som IPv4, IPv6, TCP och UDP samt en komplett uppsättning ytterligare tilläggsprotokoll på högre nivå.</span><span class="sxs-lookup"><span data-stu-id="fc952-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="fc952-106">Azure RTOS NetX Duo erbjuder säkerhet via ytterligare tilläggssäkerhetsprodukter, inklusive Azure RTOS NetX Secure IPsec och Azure RTOS NetX Secure SSL/TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="fc952-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="fc952-107">Allt detta i kombination med ett litet fotavtryck, snabb körning och överlägsen användarvänlighet gör Azure RTOS NetX Duo till det perfekta valet för de mest krävande inbäddade IoT-programmen.</span><span class="sxs-lookup"><span data-stu-id="fc952-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="fc952-108">API-protokoll</span><span class="sxs-lookup"><span data-stu-id="fc952-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="fc952-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="fc952-109">MQTT</span></span>

* <span data-ttu-id="fc952-110">MQTT (Messaging Queue Telemetry Transport)</span><span class="sxs-lookup"><span data-stu-id="fc952-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="fc952-111">Minimal 2,7 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="fc952-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="fc952-112">Automatisk IP-adress</span><span class="sxs-lookup"><span data-stu-id="fc952-112">Auto IP</span></span>

* <span data-ttu-id="fc952-113">Automatisk IPv4-adresstilldelning</span><span class="sxs-lookup"><span data-stu-id="fc952-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="fc952-114">Minimalt 1,2 kB, 300 byte RAM-minne</span><span class="sxs-lookup"><span data-stu-id="fc952-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="fc952-115">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="fc952-115">HTTP, HTTPS</span></span>
<span data-ttu-id="fc952-116">NetX Duo stöder följande HTTP/HTTPS-protokoll.</span><span class="sxs-lookup"><span data-stu-id="fc952-116">NetX Duo supports the following HTTP/HTTPS protocols.</span></span>

#### <a name="http-10"></a><span data-ttu-id="fc952-117">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="fc952-117">HTTP 1.0</span></span>

* <span data-ttu-id="fc952-118">Hypertext Transfer Protocol(HTTP)</span><span class="sxs-lookup"><span data-stu-id="fc952-118">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="fc952-119">Minimalt 2,8 KB till 4,8 KB FLASH/0,4 KB till 1,0 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fc952-119">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="fc952-120">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="fc952-120">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="fc952-121">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="fc952-121">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="fc952-122">Hypertext Transfer Protocol(HTTP)</span><span class="sxs-lookup"><span data-stu-id="fc952-122">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="fc952-123">Minimalt 3,0 TILL 9,5 KB FLASH/0,5 KB till 2 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fc952-123">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="fc952-124">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="fc952-124">Client and server support</span></span>
* <span data-ttu-id="fc952-125">Flera inkommande klientsessioner</span><span class="sxs-lookup"><span data-stu-id="fc952-125">Multiple incoming client sessions</span></span>
* <span data-ttu-id="fc952-126">Oformaterad text och krypterad HTTPS</span><span class="sxs-lookup"><span data-stu-id="fc952-126">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="fc952-127">Stöd för beständig anslutning</span><span class="sxs-lookup"><span data-stu-id="fc952-127">Persistent connection support</span></span>
* <span data-ttu-id="fc952-128">Filuppladdning med flera delar</span><span class="sxs-lookup"><span data-stu-id="fc952-128">Multipart file upload</span></span>
* <span data-ttu-id="fc952-129">Helt integrerad med Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="fc952-129">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="fc952-130">SMTP</span><span class="sxs-lookup"><span data-stu-id="fc952-130">SMTP</span></span>

* <span data-ttu-id="fc952-131">Simple Mall Transfer Protocol (SMTP)</span><span class="sxs-lookup"><span data-stu-id="fc952-131">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="fc952-132">Minimalt RAM-fotavtryck på 4,1 kB och 0,6 kB</span><span class="sxs-lookup"><span data-stu-id="fc952-132">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="fc952-133">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="fc952-133">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="fc952-134">DHCP</span><span class="sxs-lookup"><span data-stu-id="fc952-134">DHCP</span></span>

* <span data-ttu-id="fc952-135">DHCP (Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="fc952-135">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="fc952-136">Minimalt 3,6 kB till 4,6 KB FLASH, 2,7 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="fc952-136">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="fc952-137">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="fc952-137">Client and server support</span></span>
* <span data-ttu-id="fc952-138">Stöd för IPv4 och IPv6</span><span class="sxs-lookup"><span data-stu-id="fc952-138">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="fc952-139">NAT</span><span class="sxs-lookup"><span data-stu-id="fc952-139">NAT</span></span>

* <span data-ttu-id="fc952-140">NAT (Network Address Translation)</span><span class="sxs-lookup"><span data-stu-id="fc952-140">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="fc952-141">Minimalt RAM-fotavtryck på 3,5 K6 och 0,6 kB</span><span class="sxs-lookup"><span data-stu-id="fc952-141">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="fc952-142">Stöd för IPv4-adresser</span><span class="sxs-lookup"><span data-stu-id="fc952-142">IPv4 address support</span></span>
* <span data-ttu-id="fc952-143">NAT är endast tillgängligt med Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="fc952-143">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="fc952-144">SNMP</span><span class="sxs-lookup"><span data-stu-id="fc952-144">SNMP</span></span>

* <span data-ttu-id="fc952-145">Simple Network Management Protocol (SNMP)</span><span class="sxs-lookup"><span data-stu-id="fc952-145">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="fc952-146">Minimalt RAM-fotavtryck på 10,9 kB och 2,6 kB</span><span class="sxs-lookup"><span data-stu-id="fc952-146">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="fc952-147">Agentstöd för VI, V2 och V3</span><span class="sxs-lookup"><span data-stu-id="fc952-147">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="fc952-148">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="fc952-148">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="fc952-149">DNS (Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="fc952-149">Domain Name System (DNS)</span></span>
* <span data-ttu-id="fc952-150">Multicast Domain Name System (mDNS)</span><span class="sxs-lookup"><span data-stu-id="fc952-150">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="fc952-151">DNS-baserad tjänstidentifiering (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="fc952-151">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="fc952-152">DNS Minimalt 2,4 kB till 3 KB FLASH, 1 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="fc952-152">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="fc952-153">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="fc952-153">Client support</span></span>
* <span data-ttu-id="fc952-154">mDNS och DNS-SD är endast tillgängliga med Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="fc952-154">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="pop3"></a><span data-ttu-id="fc952-155">POP3</span><span class="sxs-lookup"><span data-stu-id="fc952-155">POP3</span></span>

* <span data-ttu-id="fc952-156">Post Office Protocol Version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="fc952-156">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="fc952-157">Minimalt RAM-fotavtryck på 8,1 kB och 1,4 kB</span><span class="sxs-lookup"><span data-stu-id="fc952-157">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="fc952-158">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="fc952-158">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="fc952-159">Telnet</span><span class="sxs-lookup"><span data-stu-id="fc952-159">TELNET</span></span>

* <span data-ttu-id="fc952-160">Minimalt RAM-fotavtryck på 0,5 kB och 0,3 KB</span><span class="sxs-lookup"><span data-stu-id="fc952-160">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="fc952-161">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="fc952-161">Client and server support</span></span>
* <span data-ttu-id="fc952-162">Intuitiva Telnet-API:er: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="fc952-162">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="fc952-163">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="fc952-163">FTP, TFTP</span></span>

* <span data-ttu-id="fc952-164">File Transfer Protocol (FTP)</span><span class="sxs-lookup"><span data-stu-id="fc952-164">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="fc952-165">Trivial file transfer protocol (TFTP)</span><span class="sxs-lookup"><span data-stu-id="fc952-165">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="fc952-166">FTP minimalt 1,8 kB till 7,2 KB FLASH, 0,6 kB till 2,1 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="fc952-166">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="fc952-167">TFTP minimalt 1,7 kB till 2,4 KB FLASH, 0,3 kB till 1,8 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="fc952-167">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="fc952-168">Stöd för klienter och servrar</span><span class="sxs-lookup"><span data-stu-id="fc952-168">Client and server support</span></span>
* <span data-ttu-id="fc952-169">Intuitiva FTP- och *TFTP-API:er: \* nx_ftp_* eller *\* nx_tftp_*</span><span class="sxs-lookup"><span data-stu-id="fc952-169">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="fc952-170">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="fc952-170">PPP, PPPoE</span></span>

* <span data-ttu-id="fc952-171">PPP (Polnt-to-PoInt Protocol)</span><span class="sxs-lookup"><span data-stu-id="fc952-171">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="fc952-172">Point-to-Point Protocol over Ethernet(PPPoE)</span><span class="sxs-lookup"><span data-stu-id="fc952-172">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="fc952-173">Minimalt RAM-fotavtryck på 7,1 kB och 3,8 kB</span><span class="sxs-lookup"><span data-stu-id="fc952-173">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="fc952-174">Intuitiva PPP-API:er: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="fc952-174">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="fc952-175">PPPoE är endast tillgängligt med Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="fc952-175">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="fc952-176">Sntp</span><span class="sxs-lookup"><span data-stu-id="fc952-176">SNTP</span></span>

* <span data-ttu-id="fc952-177">Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="fc952-177">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="fc952-178">Minimalt RAM-minne på 4 kB och 0,5 kB</span><span class="sxs-lookup"><span data-stu-id="fc952-178">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="fc952-179">Klientstöd</span><span class="sxs-lookup"><span data-stu-id="fc952-179">Client support</span></span>
* <span data-ttu-id="fc952-180">Intuitiva SNTP-API:er: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="fc952-180">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="legacy-code-support"></a><span data-ttu-id="fc952-181">Stöd för äldre kod</span><span class="sxs-lookup"><span data-stu-id="fc952-181">Legacy code support</span></span>

* <span data-ttu-id="fc952-182">Valfritt BSD-lager för portning av äldre socketkod</span><span class="sxs-lookup"><span data-stu-id="fc952-182">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="fc952-183">Igmp</span><span class="sxs-lookup"><span data-stu-id="fc952-183">IGMP</span></span>

* <span data-ttu-id="fc952-184">Internet Grupphanteringsprotokoll (IGMP)</span><span class="sxs-lookup"><span data-stu-id="fc952-184">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="fc952-185">Minimal 2,5 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="fc952-185">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="fc952-186">Stöd för IPv4-multicast-grupper</span><span class="sxs-lookup"><span data-stu-id="fc952-186">IPv4 multicast group support</span></span>
* <span data-ttu-id="fc952-187">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="fc952-187">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fc952-188">Valfri IGMP-statistik</span><span class="sxs-lookup"><span data-stu-id="fc952-188">Optional IGMP statistics</span></span>
* <span data-ttu-id="fc952-189">Spårning på systemnivå via Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="fc952-189">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="fc952-190">Intuitiva IGMP-API:er: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="fc952-190">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="fc952-191">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="fc952-191">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="fc952-192">Datagram Transport Layer Security (DTLS) 1.0 och 1.2</span><span class="sxs-lookup"><span data-stu-id="fc952-192">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="fc952-193">Minimal 11 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="fc952-193">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="fc952-194">Snabb RSA 2048-bitars nyckelstorlek för programvara ~ 1 sekund @120MHz</span><span class="sxs-lookup"><span data-stu-id="fc952-194">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="fc952-195">Effektiviserad X.509-implementering</span><span class="sxs-lookup"><span data-stu-id="fc952-195">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="fc952-196">Helt integrerad med Azure RTOS NetX Duo UDP-sockets</span><span class="sxs-lookup"><span data-stu-id="fc952-196">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="fc952-197">Stöd för maskinvarukryptutor</span><span class="sxs-lookup"><span data-stu-id="fc952-197">Hardware Crypto Support</span></span>
* <span data-ttu-id="fc952-198">Stöd för kryptografiprogram: RSA (alla nyckelstorlekar), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="fc952-198">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="fc952-199">Elliptic Curve Cryptography (ECC) med ECDSA (signering) och ECDH (kryptering), inklusive P-kurvor 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="fc952-199">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="fc952-200">Stöd för krypterad nyckel (maskinvaruberoende)</span><span class="sxs-lookup"><span data-stu-id="fc952-200">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="fc952-201">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="fc952-201">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="fc952-202">Transport Layer Security (TLS) 1.0, 1.1 och 1.2</span><span class="sxs-lookup"><span data-stu-id="fc952-202">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="fc952-203">Minimal 8,8 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="fc952-203">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="fc952-204">Snabb RSA 2048-bitars nyckelstorlek för programvara ~ 1 sekund @120MHz</span><span class="sxs-lookup"><span data-stu-id="fc952-204">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="fc952-205">Effektiviserad X.509-implementering</span><span class="sxs-lookup"><span data-stu-id="fc952-205">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="fc952-206">Helt integrerad med Azure RTOS NetX Duo TCP-sockets</span><span class="sxs-lookup"><span data-stu-id="fc952-206">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="fc952-207">Stöd för maskinvarukryptutor</span><span class="sxs-lookup"><span data-stu-id="fc952-207">Hardware Crypto Support</span></span>
* <span data-ttu-id="fc952-208">Stöd för kryptografiprogram: RSA (alla nyckelstorlekar), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="fc952-208">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="fc952-209">Elliptic Curve Cryptography (ECC) med ECDSA (signering) och ECDH (kryptering), inklusive P-kurvor 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="fc952-209">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="fc952-210">Stöd för krypterad nyckel (maskinvaruberoende)</span><span class="sxs-lookup"><span data-stu-id="fc952-210">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="fc952-211">ICMP</span><span class="sxs-lookup"><span data-stu-id="fc952-211">ICMP</span></span>

* <span data-ttu-id="fc952-212">Internet Control Message Protocol (ICMP)</span><span class="sxs-lookup"><span data-stu-id="fc952-212">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="fc952-213">Minimal 2,5 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="fc952-213">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="fc952-214">Stöd för IPv4 och IPv6</span><span class="sxs-lookup"><span data-stu-id="fc952-214">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="fc952-215">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="fc952-215">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fc952-216">Pingbegäran och pingsvar</span><span class="sxs-lookup"><span data-stu-id="fc952-216">Ping request and ping response</span></span>
* <span data-ttu-id="fc952-217">Valfri trådavstängning vid ping-begäranden</span><span class="sxs-lookup"><span data-stu-id="fc952-217">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="fc952-218">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="fc952-218">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fc952-219">Valfri ICMP-statistik</span><span class="sxs-lookup"><span data-stu-id="fc952-219">Optional ICMP statistics</span></span>
* <span data-ttu-id="fc952-220">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="fc952-220">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fc952-221">Intuitiva ICMP-API:er: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="fc952-221">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="fc952-222">UDP</span><span class="sxs-lookup"><span data-stu-id="fc952-222">UDP</span></span>

* <span data-ttu-id="fc952-223">UDP (User Datagram Protocol)</span><span class="sxs-lookup"><span data-stu-id="fc952-223">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="fc952-224">Minimalt 2,5 KB FLASH, 124 sockets byte RAM-minne per socket</span><span class="sxs-lookup"><span data-stu-id="fc952-224">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="fc952-225">Snabb TCP-paketbearbetning med nära wire speed:</span><span class="sxs-lookup"><span data-stu-id="fc952-225">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="fc952-226">RX 95 Mbit/s på 100 Mbit/s Ethernet, @100MHz MCU, 14 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="fc952-226">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="fc952-227">TX 94 Mbit/s på 100 Mbit/s Ethernet, @100MHz MCU, 10 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="fc952-227">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="fc952-228">UDP Fast Path™teknik</span><span class="sxs-lookup"><span data-stu-id="fc952-228">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="fc952-229">Inga gränser för antalet UDP</span><span class="sxs-lookup"><span data-stu-id="fc952-229">No limits on the number of UDP</span></span>
* <span data-ttu-id="fc952-230">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="fc952-230">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fc952-231">Valfri stängning vid socket-mottagning</span><span class="sxs-lookup"><span data-stu-id="fc952-231">Optional suspension on socket receive</span></span>
* <span data-ttu-id="fc952-232">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="fc952-232">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fc952-233">Valfri UDP-statistik</span><span class="sxs-lookup"><span data-stu-id="fc952-233">Optional UDP statistics</span></span>
* <span data-ttu-id="fc952-234">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="fc952-234">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fc952-235">Intuitiva UDP-API:er: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="fc952-235">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="fc952-236">TCP</span><span class="sxs-lookup"><span data-stu-id="fc952-236">TCP</span></span>

* <span data-ttu-id="fc952-237">Transmission Control Protocol (TCP)</span><span class="sxs-lookup"><span data-stu-id="fc952-237">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="fc952-238">Minimal 10,5K8 till 12,5 KB FLASH, 280 byte RAM-minne per socket</span><span class="sxs-lookup"><span data-stu-id="fc952-238">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="fc952-239">Snabb, nära wlre speed TCP-paketbearbetning:</span><span class="sxs-lookup"><span data-stu-id="fc952-239">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="fc952-240">RX 93 Mbit/s på 100 Mbit/s Ethernet, @100MHz MCU, 20 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="fc952-240">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="fc952-241">TX 94 Mbit/s på 100 Mbit/s Ethernet, @100MHz MCU, 27 % MCU-användning</span><span class="sxs-lookup"><span data-stu-id="fc952-241">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="fc952-242">Tillförlitlig anslutning</span><span class="sxs-lookup"><span data-stu-id="fc952-242">Reliable connection</span></span>
* <span data-ttu-id="fc952-243">Inga gränser för antalet TCP-socketar</span><span class="sxs-lookup"><span data-stu-id="fc952-243">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="fc952-244">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="fc952-244">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fc952-245">Valfri stängning vid socket-mottagning/-överföring</span><span class="sxs-lookup"><span data-stu-id="fc952-245">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="fc952-246">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="fc952-246">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fc952-247">Valfri TCP-statistik</span><span class="sxs-lookup"><span data-stu-id="fc952-247">Optional TCP statistics</span></span>
* <span data-ttu-id="fc952-248">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="fc952-248">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fc952-249">Intuitiva TCP-API:er: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="fc952-249">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="fc952-250">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="fc952-250">ARP/RARP</span></span>

* <span data-ttu-id="fc952-251">Address Resolution Protocol (ARP)</span><span class="sxs-lookup"><span data-stu-id="fc952-251">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="fc952-252">Reverse Address Resolution Protocol (RARP)</span><span class="sxs-lookup"><span data-stu-id="fc952-252">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="fc952-253">Minimal 1,7 KB FLASH, RAM-storlek</span><span class="sxs-lookup"><span data-stu-id="fc952-253">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="fc952-254">Dynamisk upplösning av 32-blt IPv4- och 48-blt MAC-adresser</span><span class="sxs-lookup"><span data-stu-id="fc952-254">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="fc952-255">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="fc952-255">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fc952-256">Flexibel, användardefinierad ARP-cache</span><span class="sxs-lookup"><span data-stu-id="fc952-256">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="fc952-257">Gratuitous ARP support</span><span class="sxs-lookup"><span data-stu-id="fc952-257">Gratuitous ARP support</span></span>
* <span data-ttu-id="fc952-258">Valfri ARP/RARP-statistik som bestäms av programmet</span><span class="sxs-lookup"><span data-stu-id="fc952-258">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="fc952-259">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="fc952-259">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fc952-260">Intuitiva ARP/RARP-API:nx_arp_ *\**, *\* nx_rarp_*</span><span class="sxs-lookup"><span data-stu-id="fc952-260">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="fc952-261">IPv4 &amp; IPv6</span><span class="sxs-lookup"><span data-stu-id="fc952-261">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="fc952-262">Internet Protocol (IP)</span><span class="sxs-lookup"><span data-stu-id="fc952-262">Internet Protocol (IP)</span></span>
* <span data-ttu-id="fc952-263">Minimal 3,5 kB till 8,5 KB FLASH, 2 KB till 3 KB RAM-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="fc952-263">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="fc952-264">Piconet™arkitektur</span><span class="sxs-lookup"><span data-stu-id="fc952-264">Piconet™ architecture</span></span>
* <span data-ttu-id="fc952-265">Snabb, nära wire speed-prestanda</span><span class="sxs-lookup"><span data-stu-id="fc952-265">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="fc952-266">Stöd för flera gränssnitt</span><span class="sxs-lookup"><span data-stu-id="fc952-266">Multiple interface support</span></span>
* <span data-ttu-id="fc952-267">Stöd för flera start</span><span class="sxs-lookup"><span data-stu-id="fc952-267">Multihomed support</span></span>
* <span data-ttu-id="fc952-268">Stöd för statisk routning</span><span class="sxs-lookup"><span data-stu-id="fc952-268">Static routing support</span></span>
* <span data-ttu-id="fc952-269">Stöd för IP-fragmentering/återmontering</span><span class="sxs-lookup"><span data-stu-id="fc952-269">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="fc952-270">Stöd för IPv4- och IPv6-adresser</span><span class="sxs-lookup"><span data-stu-id="fc952-270">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="fc952-271">IXIA IxANVL-verifierad</span><span class="sxs-lookup"><span data-stu-id="fc952-271">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fc952-272">Fas II IPv6 Ready Logo Certification (IPv6-redo logotypcertifiering)</span><span class="sxs-lookup"><span data-stu-id="fc952-272">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="fc952-273">Valfri IP-statistik</span><span class="sxs-lookup"><span data-stu-id="fc952-273">Optional IP statistics</span></span>
* <span data-ttu-id="fc952-274">Väldefinierat, intuitivt drivrutinsgränssnitt på fysiskt lager</span><span class="sxs-lookup"><span data-stu-id="fc952-274">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="fc952-275">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="fc952-275">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fc952-276">Intuitiva API:er för *IP-lager: \* nx_ip_*, *nxd_ip_ \** *\** , nxd_ipv6_</span><span class="sxs-lookup"><span data-stu-id="fc952-276">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="fc952-277">Förcertifierat av TUV och UL till IEC 61508 SIL 4, IEC 62304 Klass C, ISO 26262 ASIL D och EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="fc952-277">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="fc952-278">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="fc952-278">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="fc952-279">Internet Protocol Security (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="fc952-279">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="fc952-280">IP-lager</span><span class="sxs-lookup"><span data-stu-id="fc952-280">IP layer</span></span>
* <span data-ttu-id="fc952-281">Stöd för maskinvarukryptutor</span><span class="sxs-lookup"><span data-stu-id="fc952-281">Hardware crypto support</span></span>
* <span data-ttu-id="fc952-282">Stöd för kryptografiprogram, inklusive:</span><span class="sxs-lookup"><span data-stu-id="fc952-282">Software crypto support, including:</span></span>
    * <span data-ttu-id="fc952-283">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="fc952-283">DES, 3DES</span></span>
    * <span data-ttu-id="fc952-284">AES</span><span class="sxs-lookup"><span data-stu-id="fc952-284">AES</span></span>
    * <span data-ttu-id="fc952-285">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="fc952-285">HMAC-MD5</span></span>
    * <span data-ttu-id="fc952-286">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="fc952-286">HMAC-SHA1</span></span>
* <span data-ttu-id="fc952-287">Stöd för Internet Key Exchange (IKE) Version 2</span><span class="sxs-lookup"><span data-stu-id="fc952-287">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="fc952-288">Intuitiva IPsec-API:er: *nx_ipsec_ \**</span><span class="sxs-lookup"><span data-stu-id="fc952-288">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="fc952-289">IPsec är endast tillgängligt med Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="fc952-289">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="fc952-290">Valv och säkert</span><span class="sxs-lookup"><span data-stu-id="fc952-290">Safe and secure</span></span>

<span data-ttu-id="fc952-291">Azure RTOS NetX Duo är säker.</span><span class="sxs-lookup"><span data-stu-id="fc952-291">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="fc952-292">Den här säkerheten tillhandahålls via tilläggssäkerhetsprodukter, inklusive IPsec, SSL, TLS och DTLS.</span><span class="sxs-lookup"><span data-stu-id="fc952-292">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="fc952-293">Dessutom har programmet fullständig kontroll över all extern åtkomst till Azure RTOS NetX Duo, vilket gör det mycket enklare att fastställa säkerhetsrisker.</span><span class="sxs-lookup"><span data-stu-id="fc952-293">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="fc952-294">Microsoft Azure RTOS tillhandahåller OEM-tillverkare med komponenter för säker kommunikation och för att skapa kod- och dataisolering med underliggande MCU/MPU-maskinvaruskyddsmekanismer.</span><span class="sxs-lookup"><span data-stu-id="fc952-294">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="fc952-295">Det är i slutänden enhetsbyggaren som ansvarar för att säkerställa att enheten uppfyller de föränderliga säkerhetskrav som är associerade med dess specifika användningsfall.</span><span class="sxs-lookup"><span data-stu-id="fc952-295">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="fc952-296">Interoperabilitetsverifiering</span><span class="sxs-lookup"><span data-stu-id="fc952-296">Interoperability verification</span></span>

<span data-ttu-id="fc952-297">NetX Duo följer RFC-standarder och erbjuder fullständig samverkan med enheter för de flesta leverantörer.</span><span class="sxs-lookup"><span data-stu-id="fc952-297">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Logotyp för IPv6-klar](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="fc952-299">Azure RTOS NetX Duo är en av de enda inbäddade TCP/IP-stackarna för att uppnå rigorös IPv6-Ready Logo-certifiering, bevis på att den har klarat överensstämmelse- och samverkanstester som administreras och verifierats av IPv6-forumet.</span><span class="sxs-lookup"><span data-stu-id="fc952-299">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="fc952-300">NetX Duo använder också branschstandarden IxANVL (Automated Network Validation Library) för netX Duo core TCP/IP-protokollimplementering.</span><span class="sxs-lookup"><span data-stu-id="fc952-300">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="fc952-301">Omfattande IoT-lösning</span><span class="sxs-lookup"><span data-stu-id="fc952-301">Comprehensive IoT solution</span></span>

<span data-ttu-id="fc952-302">NetX Duo har ett av de mest omfattande TCP/IP-nätverken för djupt inbäddade IoT-program.</span><span class="sxs-lookup"><span data-stu-id="fc952-302">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="fc952-303">Det här stödet omfattar följande tillägg protokollprodukter.</span><span class="sxs-lookup"><span data-stu-id="fc952-303">This support includes the following add-on protocol products.</span></span>

* <span data-ttu-id="fc952-304">MQTT</span><span class="sxs-lookup"><span data-stu-id="fc952-304">MQTT</span></span>
* <span data-ttu-id="fc952-305">CoAP</span><span class="sxs-lookup"><span data-stu-id="fc952-305">CoAP</span></span>
* <span data-ttu-id="fc952-306">LWM2M</span><span class="sxs-lookup"><span data-stu-id="fc952-306">LWM2M</span></span>
* <span data-ttu-id="fc952-307">6LoWPAN</span><span class="sxs-lookup"><span data-stu-id="fc952-307">6LoWPAN</span></span>
* <span data-ttu-id="fc952-308">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="fc952-308">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="fc952-309">IPsec</span><span class="sxs-lookup"><span data-stu-id="fc952-309">IPsec</span></span>
* <span data-ttu-id="fc952-310">AutoIP</span><span class="sxs-lookup"><span data-stu-id="fc952-310">AutoIP</span></span>
* <span data-ttu-id="fc952-311">DHCP</span><span class="sxs-lookup"><span data-stu-id="fc952-311">DHCP</span></span>
* <span data-ttu-id="fc952-312">DNS</span><span class="sxs-lookup"><span data-stu-id="fc952-312">DNS</span></span>
* <span data-ttu-id="fc952-313">Mdns</span><span class="sxs-lookup"><span data-stu-id="fc952-313">mDNS</span></span>
* <span data-ttu-id="fc952-314">DNS-SD</span><span class="sxs-lookup"><span data-stu-id="fc952-314">DNS-SD</span></span>
* <span data-ttu-id="fc952-315">FTP</span><span class="sxs-lookup"><span data-stu-id="fc952-315">FTP</span></span>
* <span data-ttu-id="fc952-316">HTTP</span><span class="sxs-lookup"><span data-stu-id="fc952-316">HTTP</span></span>
* <span data-ttu-id="fc952-317">IPsec</span><span class="sxs-lookup"><span data-stu-id="fc952-317">IPsec</span></span>
* <span data-ttu-id="fc952-318">NAT</span><span class="sxs-lookup"><span data-stu-id="fc952-318">NAT</span></span>
* <span data-ttu-id="fc952-319">POP3</span><span class="sxs-lookup"><span data-stu-id="fc952-319">POP3</span></span>
* <span data-ttu-id="fc952-320">Ppp</span><span class="sxs-lookup"><span data-stu-id="fc952-320">PPP</span></span>
* <span data-ttu-id="fc952-321">Pppoe</span><span class="sxs-lookup"><span data-stu-id="fc952-321">PPPoE</span></span>
* <span data-ttu-id="fc952-322">SMTP</span><span class="sxs-lookup"><span data-stu-id="fc952-322">SMTP</span></span>
* <span data-ttu-id="fc952-323">SNMP v1/2/3</span><span class="sxs-lookup"><span data-stu-id="fc952-323">SNMP v1/2/3</span></span>
* <span data-ttu-id="fc952-324">Telnet</span><span class="sxs-lookup"><span data-stu-id="fc952-324">Telnet</span></span>
* <span data-ttu-id="fc952-325">Tftp</span><span class="sxs-lookup"><span data-stu-id="fc952-325">TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="fc952-326">Avancerad teknik</span><span class="sxs-lookup"><span data-stu-id="fc952-326">Advanced technology</span></span>

<span data-ttu-id="fc952-327">Azure RTOS NetX Duo är avancerad teknik som omfattar följande.</span><span class="sxs-lookup"><span data-stu-id="fc952-327">Azure RTOS NetX Duo is advanced technology that includes the following.</span></span>

* <span data-ttu-id="fc952-328">Piconet™arkitektur</span><span class="sxs-lookup"><span data-stu-id="fc952-328">Piconet™ architecture</span></span>
* <span data-ttu-id="fc952-329">Automatisk skalning</span><span class="sxs-lookup"><span data-stu-id="fc952-329">Automatic scaling</span></span>
* <span data-ttu-id="fc952-330">UDP Fast-Path Technology™</span><span class="sxs-lookup"><span data-stu-id="fc952-330">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="fc952-331">Flexibel pakethantering</span><span class="sxs-lookup"><span data-stu-id="fc952-331">Flexible packet management</span></span>
* <span data-ttu-id="fc952-332">API med nollkopiering och implementering</span><span class="sxs-lookup"><span data-stu-id="fc952-332">Zero-copy API and implementation</span></span>
* <span data-ttu-id="fc952-333">Stöd för flera start</span><span class="sxs-lookup"><span data-stu-id="fc952-333">Multihomed support</span></span>
* <span data-ttu-id="fc952-334">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="fc952-334">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fc952-335">Stöd för statisk routning</span><span class="sxs-lookup"><span data-stu-id="fc952-335">Static routing support</span></span>
* <span data-ttu-id="fc952-336">IPsec</span><span class="sxs-lookup"><span data-stu-id="fc952-336">IPsec</span></span>
* <span data-ttu-id="fc952-337">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="fc952-337">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="fc952-338">Azure RTOS traceX-systemanalysstöd</span><span class="sxs-lookup"><span data-stu-id="fc952-338">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="fc952-339">Relaterade tjänster</span><span class="sxs-lookup"><span data-stu-id="fc952-339">Related services</span></span>

<span data-ttu-id="fc952-340">NetX Duo tillhandahåller följande ytterligare tjänster.</span><span class="sxs-lookup"><span data-stu-id="fc952-340">NetX Duo provides the following additional services.</span></span>

* <span data-ttu-id="fc952-341">Azure IoT Middleware</span><span class="sxs-lookup"><span data-stu-id="fc952-341">Azure IoT Middleware</span></span>
* <span data-ttu-id="fc952-342">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="fc952-342">Azure Defender</span></span>
* <span data-ttu-id="fc952-343">Enhetsuppdatering för IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="fc952-343">Device update for IoT Hub.</span></span>

### <a name="azure-iot-middleware"></a><span data-ttu-id="fc952-344">Azure IoT Middleware</span><span class="sxs-lookup"><span data-stu-id="fc952-344">Azure IoT Middleware</span></span>

<span data-ttu-id="fc952-345">NetX Duo innehåller [Azure IoT Middleware för Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), ett plattformsspecifikt bibliotek som fungerar som ett bindningslager mellan Azure RTOS och Azure SDK för Embedded C för att underlätta anslutningen till Azure IoT-tjänster.</span><span class="sxs-lookup"><span data-stu-id="fc952-345">NetX Duo includes [Azure IoT Middleware for Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), a platform-specific library that acts as a binding layer between the Azure RTOS and the Azure SDK for Embedded C to facilitate connectivity to Azure IoT services.</span></span> <span data-ttu-id="fc952-346">Målen med Azure IoT Middleware är följande.</span><span class="sxs-lookup"><span data-stu-id="fc952-346">The goals of Azure IoT Middleware are the following.</span></span>
* <span data-ttu-id="fc952-347">Tillhandahåll de smarta klientgränssnitt (IoTHub_Client, DeviceProvisioning_Client) som utvecklare behöver för sina program.</span><span class="sxs-lookup"><span data-stu-id="fc952-347">Provide the smart client interfaces (IoTHub_Client, DeviceProvisioning_Client) that developers need for their applications.</span></span>
* <span data-ttu-id="fc952-348">Samordna interaktionen mellan Embedded C SDK och plattformen.</span><span class="sxs-lookup"><span data-stu-id="fc952-348">Orchestrate the interaction between the Embedded C SDK and the platform.</span></span>
* <span data-ttu-id="fc952-349">Tillhandahåll Azure RTOS plattformsinitiering.</span><span class="sxs-lookup"><span data-stu-id="fc952-349">Provide Azure RTOS platform initialization.</span></span>
* <span data-ttu-id="fc952-350">IoT Plug and Play support.</span><span class="sxs-lookup"><span data-stu-id="fc952-350">IoT Plug and Play support.</span></span>
* <span data-ttu-id="fc952-351">Säkerhetsfunktioner.</span><span class="sxs-lookup"><span data-stu-id="fc952-351">Security capabilities.</span></span>
* <span data-ttu-id="fc952-352">Resursbegränsningsmedveten.</span><span class="sxs-lookup"><span data-stu-id="fc952-352">Resource limitation aware.</span></span>
* <span data-ttu-id="fc952-353">Protokollstöd.</span><span class="sxs-lookup"><span data-stu-id="fc952-353">Protocol support.</span></span>

![Azure RTOS NetX Duo Related Services](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a><span data-ttu-id="fc952-355">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="fc952-355">Azure Defender</span></span>

<span data-ttu-id="fc952-356">Säkerhetsmodulen Azure Defender for IoT innehåller en omfattande säkerhetslösning för Azure RTOS enheter.</span><span class="sxs-lookup"><span data-stu-id="fc952-356">The Azure Defender for IoT security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="fc952-357">Säkerhetsmodulen för Azure RTOS erbjuder identifiering av aktiviteter i skadliga nätverk, anpassade aviseringsbaserade enhetsbeteenden som baserar sig på och hjälper till att förbättra enhetens säkerhetshygien.</span><span class="sxs-lookup"><span data-stu-id="fc952-357">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="fc952-358">Läs mer om [säkerhetsmodulen för Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) eller kom igång med [snabbstarten Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) (Konfigurera säkerhetsmodul för Azure RTOS).</span><span class="sxs-lookup"><span data-stu-id="fc952-358">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

### <a name="device-update-for-iot-hub"></a><span data-ttu-id="fc952-359">Enhetsuppdatering för IoT Hub</span><span class="sxs-lookup"><span data-stu-id="fc952-359">Device Update for IoT Hub</span></span>

<span data-ttu-id="fc952-360">[Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) är en tjänst som gör att du kan distribuera trådlösa uppdateringar (OTA) för dina IoT-enheter.</span><span class="sxs-lookup"><span data-stu-id="fc952-360">The [Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) is a service that enables you to deploy over-the-air updates (OTA) for your IoT devices.</span></span> <span data-ttu-id="fc952-361">Modulen Enhetsuppdatering för IoT Hub är implementeringen av Enhetsuppdatering för IoT Hub Agent i Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="fc952-361">The Device Update for IoT Hub module is the implementation of Device Update for IoT Hub Agent in Azure RTOS NetX Duo.</span></span> <span data-ttu-id="fc952-362">Den innehåller enkla API:er som gör att enhetsbyggare kan integrera funktionen Enhetsuppdatering i sina program.</span><span class="sxs-lookup"><span data-stu-id="fc952-362">It provides simple APIs for device builders to integrate the Device Update capability in their application.</span></span>

<span data-ttu-id="fc952-363">Se exempel på viktiga utvärderingstavlor som innehåller kom igång-guiderna för att lära dig att konfigurera, bygga och distribuera trådlösa uppdateringar (OTA) till enheterna.</span><span class="sxs-lookup"><span data-stu-id="fc952-363">See the samples of key semiconductors evaluation boards that include the get started guides to learn configure, build and deploy the over-the-air (OTA) updates to the devices.</span></span>

<span data-ttu-id="fc952-364">Du kan också läsa mer om hur du [använder Enhetsuppdatering för IoT Hub med Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span><span class="sxs-lookup"><span data-stu-id="fc952-364">And you can learn more details about use [Device Update for IoT Hub with Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span></span>

## <a name="next-steps"></a><span data-ttu-id="fc952-365">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="fc952-365">Next steps</span></span>

<span data-ttu-id="fc952-366">Om du vill veta mer om NetX Duo börjar du [med Azure RTOS användarhandbok för NetX Duo.](about-this-guide.md)</span><span class="sxs-lookup"><span data-stu-id="fc952-366">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
