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
# <a name="overview-of-azure-rtos-netx-duo"></a>Översikt över Azure återställnings tider NetX Duo

Azure återställnings tider NetX Duo Embedded TCP/IP Network stack är Microsofts avancerade, industriella klass med dubbla IPv4-och IPv6-nätverks stackar som är särskilt utformade för djupt inbäddade, real tids-och IoT-program. NetX Duo tillhandahåller inbäddade program med kärn nätverks protokoll som IPv4, IPv6, TCP och UDP samt en fullständig uppsättning tilläggs protokoll på högre nivå. Azure återställnings tider NetX Duo erbjuder säkerhet via ytterligare tilläggs säkerhets produkter, inklusive Azure återställnings tider NetX Secure IPsec och Azure återställnings tider NetX Secure SSL/TLS/DTLS. Allt detta kombinerat med en liten storlek, snabb körning och överlägsen enkel användning gör Azure återställnings tider NetX Duo det idealiska valet för de mest krävande inbäddade IoT-programmen.

## <a name="api-protocols"></a>API-protokoll

### <a name="mqtt"></a>MQTT

* MQTT (Messaging Queue telemetri transport)
* Minimal 2,7 KB FLASH
* Intuitiva MQTT-API: er: *nx_mqtt_*\*

### <a name="auto-ip"></a>Automatisk IP

* Automatisk tilldelning av IPv4-adress
* Minimal 1,2 KB, 300 byte RAM-minne
* Intuitiva AutoIP-API: er: *nx_autoip_ \**

### <a name="http-https"></a>HTTP, HTTPS

#### <a name="http-10"></a>HTTP 1,0

* Hypertext Transfer Protocol (HTTP)
* Minimal 2,8 KB till 4,8 KB FLASH/0,4 KB till 1,0 KB RAM
* Stöd för klienter och servrar
* Intuitiva API: er: *nx_http_ \**

#### <a name="httphttps-11"></a>HTTP/HTTPS 1,1

* Hypertext Transfer Protocol (HTTP)
* Minimal 3,0 KB till 9,5 KB FLASH/0,5 KB till 2 KB RAM
* Stöd för klienter och servrar
* Flera inkommande klientsessioner
* Oformaterad text och krypterad HTTPS
* Stöd för beständiga anslutningar
* Uppladdning av flerdelade filer
* Fullständigt integrerat med Azure återställnings tider NetX Secure TLS
* Intuitiva API: er: *nx_web_http \**

### <a name="smtp"></a>SMTP

* Simple mallar Transfer Protocol (SMTP)
* Minst 4,1 KB och 0,6 KB RAM-minne
* Klient support
* Intuitiva SMTP-API: er: *nx_smtp_ \**

### <a name="dhcp"></a>DHCP

* DHCP (Dynamic Host Configuration Protocol)
* Minimal 3,6 KB till 4,6 KB FLASH, 2,7 KB RAM-minne
* Stöd för klienter och servrar
* Stöd för IPv4 och IPv6
* Intuitiva DHCP-API: er: *nx_dhcp_ \**

### <a name="nat"></a>NAT

* NAT (Network Address Translation)
* Minimal 3,5-tums K6 och 0,6 KB RAM-minne
* Stöd för IPv4-adress
* Intuitiva NAT-API: er: *nx_nat_ \**
* NAT är endast tillgängligt med Azure återställnings tider NetX Duo

### <a name="snmp"></a>SNMP

* Simple Network Management Protocol (SNMP)
* Minst 10,9 KB och 2,6 KB RAM-minne
* Agent stöd för VI, v2 och v3
* Intuitiva SNMP-API: er: *nx_snmp_ \**

### <a name="dns-mdns-dns-sd"></a>DNS, mDNS, DNS-SD

* DNS (Domain Name System)
* Multicast-Domain Name System (mDNS)
* DNS-baserad tjänst identifiering (DNS-SD)
* DNS-minimal 2,4 KB till 3 KB FLASH, 1 KB RAM-minne
* Klient support
* Intuitiva API: er: *nx_dns_ \**
* mDNS och DNS – SD är bara tillgängliga med Azure återställnings tider NetX Duo

### <a name="p0p3"></a>P0P3

* Post Office Protocol version 3 (POP3)
* Minst 8,1 KB och 1,4 KB RAM-minne
* Klient support
* Intuitiva P0P3-API: er: *nx_pop3_ \**

### <a name="telnet"></a>TELNET

* Minst 0,5 KB och 0,3 KB RAM-minne
* Stöd för klienter och servrar
* Intuitiva Telnet-API: er: *nx_telnet_ \**

### <a name="ftp-tftp"></a>FTP, TFTP

* File Transfer Protocol (FTP)
* Trivial file transfer protocol (TFTP)
* FTP, minimal 1,8 KB till 7,2 KB FLASH, 0,6 KB till 2,1 KB RAM-minne
* TFTP minimal 1,7 KB till 2,4 KB FLASH, 0,3 KB till 1,8 KB RAM-minne
* Stöd för klienter och servrar
* Intuitiva API: er för FTP och TFTP: *nx_ftp_ \** eller *nx_tftp_ \**

### <a name="ppp-pppoe"></a>PPP, PPPoE

* Polnt-to-PoInt Protocol (PPP)
* Point-to-Point Protocol över Ethernet (PPPoE)
* Minst 7,1 KB och 3,8 KB RAM-minne
* Intuitiva PPP-API: er: *nx_ppp_ \**

* PPPoE är endast tillgängligt med Azure återställnings tider NetX Duo

### <a name="sntp"></a>SNTP

* SNTP (Simple Network Time Protocol)
* Minst 4 KB och 0,5 KB RAM
* Klient support
* Intuitiva SNTP-API: er: *nx_sntp_ \**

### <a name="azure-rtos-netx-duo-api"></a>Azure återställnings tider NetX Duo-API

* Intuitiv och konsekvent API
* Substantiv-namn konvention för verb
* Snabb, noll-kopiera API-implementering
* Alla API: er har ledande <i>nx_ *</i> för att enkelt identifiera som Azure återställnings tider netx
* Blockering av API: er har valfri tråd-timeout
* Mer information finns i [användar handboken för Azure återställnings tider netx Duo](about-this-guide.md) .
* Valfritt BSD-lager för portning av äldre socket-kod

### <a name="igmp"></a>PROXYLÄGE

* Internet Grupphanteringsprotokoll (IGMP)
* Minimal 2,5 KB FLASH
* Stöd för IPv4 multicast-grupp
* IXIA-IxANVL verifierad
* Valfri IGMP-statistik
* Spårning på system nivå via Azure återställnings tider ThreadX
* Intuitiva IGMP-API: er: *nx_igmp_ \**

### <a name="azure-rtos-netx-secure-dtls"></a>Azure återställnings tider NetX Secure DTLS

* Datagram Transport Layer Security (DTLS) 1,0 och 1,2
* Minst 11 KB FLASH
* Snabb, programvaru-RSA 2048-bitars nyckel storlek ~ 1-sekund @120MHz
* Effektiv X. 509-implementering
* Fullständigt integrerat med Azure återställnings tider NetX Duo UDP-Sockets
* Stöd för maskin varu kryptering
* Stöd för program varu kryptografi: RSA (alla nyckel storlekar), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* Elliptic Curve Cryptography (ECC) med ECDSA (Sign) och ECDH (kryptering), inklusive P-kurvor 192/224/256/384/521
* Stöd för krypterad nyckel (maskin vara beroende)

### <a name="azure-rtos-netx-secure-tls"></a>Azure återställnings tider NetX Secure TLS

* Transport Layer Security (TLS) 1,0, 1,1 och 1,2
* Minimal 8,8 KB FLASH
* Snabb, programvaru-RSA 2048-bitars nyckel storlek ~ 1-sekund @120MHz
* Effektiv X. 509-implementering
* Fullständigt integrerat med Azure återställnings tider NetX Duo TCP-Sockets
* Stöd för maskin varu kryptering
* Stöd för program varu kryptografi: RSA (alla nyckel storlekar), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* Elliptic Curve Cryptography (ECC) med ECDSA (Sign) och ECDH (kryptering), inklusive P-kurvor 192/224/256/384/521
* Stöd för krypterad nyckel (maskin vara beroende)

### <a name="icmp"></a>ICMP

* Internet Control Message Protocol (ICMP)
* Minimal 2,5 KB FLASH
* Stöd för IPv4 och IPv6
* IXIA-IxANVL verifierad
* Ping-begäran och ping-svar
* Valfri tråd SUS pension vid ping-begäranden
* Valfri tids gräns vid alla avbrott
* Valfri ICMP-statistik
* Spårning på system nivå via Azure återställnings tider TraceX
* Intuitiva ICMP-API: er: *nx_icmp_ \**

### <a name="udp"></a>UDP

* UDP (User Datagram Protocol)
* Minimal 2,5 KB FLASH, 124 Sockets byte RAM per socket
* Snabb, nära WireSpeed TCP-paket bearbetning:
    * RX 95 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 14% MCU användning
    * TX 94 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 10% MCU användning
* Snabb väg för™ teknik för UDP
* Inga begränsningar för antalet UDP
* IXIA-IxANVL verifierad
* Valfri SUS Pension på socket får
* Valfri tids gräns vid alla avbrott
* Valfri UDP-statistik
* Spårning på system nivå via Azure återställnings tider TraceX
* Intuitiva UDP-API: er: *nx_udp_ \**

### <a name="tcp"></a>TCP

* Transmission Control Protocol (TCP)
* Minst 10,5 K8 till 12,5 KB FLASH, 280 byte RAM per socket
* Snabb, nära wlrespeed TCP-paket bearbetning:
    * RX 93 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 20% MCU användning
    * TX 94 Mbit/s på 100 Mbit/s Ethernet, MCU @100MHz , 27% MCU-användning
* Tillförlitlig anslutning
* Inga begränsningar för antalet TCP-socketar
* IXIA-IxANVL verifierad
* Valfri SUS Pension på socket Receive/överföring
* Valfri tids gräns vid alla avbrott
* Valfri TCP-statistik
* Spårning på system nivå via Azure återställnings tider TraceX
* Intuitiva TCP-API: er: *nx_tcp_ \**

### <a name="arprarp"></a>ARP/RARP

* ARP (Address Resolution Protocol)
* RARP (reversed Address Resolution Protocol)
* Minimal 1,7 KB FLASH, RAM-storlek
* Dynamisk matchning av 32-smörgås IPv4-och 48-smörgås MAC-adresser
* IXIA-IxANVL verifierad
* Flexibel, användardefinierad ARP-cache
* Stöd för kostnads fria ARP
* Valfri ARP/RARP-statistik som fastställs av programmet
* Spårning på system nivå via Azure återställnings tider TraceX
* Intuitiva ARP/RARP-API: er: *nx_arp_ \** *nx_rarp_ \**

### <a name="ipv4-amp-ipv6"></a>IPv4 &amp; IPv6

* Internet Protocol (IP)
* Minimal 3,5 KB till 8,5 KB FLASH, 2 KB till 3 KB RAM-minne
* Piconet™-arkitektur
* Snabba, nära WireSpeed prestanda
* Stöd för flera gränssnitt
* Stöd för multihomed
* Stöd för statisk routning
* Stöd för IP-fragmentering/omsammansättning
* Stöd för IPv4-och IPv6-adresser
* IXIA-IxANVL verifierad
* Fas II IPv6-färdig logo typ certifiering
* Valfri IP-statistik
* Väl definierat, intuitivt gränssnitt för fysiskt skikt driv rutin
* Spårning på system nivå via Azure återställnings tider TraceX
* Intuitiva API: er för IP-lager: *\* nx_ip_*, *nxd_ip_ \**, *nxd_ipv6_ \**
* Förcertifierat av TUV och UL till IEC 61508 SIL 4, IEC 62304 klass C, ISO 26262 ASIL D och EN 50128 SW-SIL4

### <a name="azure-rtos-netx-secure-ipsec"></a>Azure återställnings tider NetX Secure IPSEC

* Internet Protocol säkerhet (IPSEC)
* IP-skikt
* Stöd för maskin varu kryptering
* Stöd för program varu kryptering, inklusive:
    * DES, 3DES
    * AES
    * HMAC-MD5
    * HMAC-SHA1
* Stöd för Internet Key Exchange (IKE) version 2
* Intuitiva IPsec-API: er: *nx_ipsec_ \**
* IPsec är endast tillgängligt med Azure återställnings tider NetX Duo

## <a name="small-footprint"></a>Små

Azure återställnings tider NetX Duo har ett remarkably litet utrymme på 9 KB till 15 KB för grundläggande IP-och UDP-stöd. Det krävs ytterligare 10 KB till 13 KB av instruktions områdets minne för TCP-funktioner. Azure återställnings tider NetX Duo RAM-användningen är vanligt vis mellan 2,6 KB och 3,6 KB plus det paket minne som definieras av programmet. Precis som Azure återställnings tider ThreadX skalas storleken på Azure återställnings tider NetX Duo automatiskt baserat på de tjänster som används av programmet. Detta eliminerar behovet av komplicerade konfigurations-och bygg parametrar, vilket gör det enklare för utvecklaren.

## <a name="fast-execution"></a>Snabb körning

Azure återställnings tider NetX Duo innehåller en paket för att skicka och ta emot en nollställnings kopiering, som är mycket integrerat med Azure återställnings tider ThreadX, för att uppnå snabbast möjliga prestanda. Till exempel kan Azure återställnings tider NetX Duo normalt uppnå nära WireSpeed-dataöverföringar på en 80 MHz-processor (eller mindre) och bara använda en liten procent andel av processorns cykler.

## <a name="simple-easy-to-use"></a>Enkel, lätt att använda

Azure återställnings tider NetX Duo-API: n är intuitiv, enkel och mycket funktionell.

API-namnen består av riktiga ord och inte "alfabet soppor" eller förkortade namn som är vanliga i andra nätverks produkter. Alla Azure återställnings tider NetX Duo-API: er har en ledande *nx_* och följer en namn konvention för substantiv-verb. Det finns dessutom en funktions konsekvens i hela API: et. Till exempel har alla API-funktioner som pausas en valfri tids gräns som fungerar på samma sätt.

För äldre program erbjuder Azure återställnings tider NetX Duo ytterligare ett BSD-kompatibelt lager. Det här lagret hjälper utvecklare att migrera stora nätverks program utan problem.

## <a name="safe-and-secure"></a>Säkert och säkert

Azure återställnings tider NetX Duo är säkert. Den här säkerheten tillhandahålls genom tilläggs säkerhets produkter, inklusive IPsec, SSL, TLS och DTLS. Programmet har också fullständig kontroll över all extern åtkomst till Azure återställnings tider NetX Duo, vilket gör det enklare att fastställa säkerhets risk.

Microsoft Azure återställnings tider förser OEM-tillverkare med komponenter för att skydda kommunikationen och skapa kod-och data isolering med underliggande MCU/MPU-funktioner för maskin varu skydd. I slut ändan är enhets verktygets ansvar att säkerställa att enheten fullt ut uppfyller de säkerhets krav som är kopplade till det särskilda användnings fallet.

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a>Förcertifierat av TUV och UL till många säkerhets standarder

Azure återställnings tider NetX Duo har certifierats av SGS-TUV Saar för användning i säkerhets kritiska system, enligt IEC-61508 SIL 4, IEC-62304 SW säkerhets klass C, ISO 26262 ASIL D och EN 50128. Certifieringen bekräftar att Azure återställnings tider NetX Duo kan användas i utvecklingen av säkerhetsrelaterad program vara för den högsta säkerhets integritets nivån för IEC-61508, IEC-62304, ISO 26262 och EN 50128 för "fungerande säkerhet för elektriska, elektroniska och programmerbara elektroniskt säkerhetsrelaterade system". SGS – TUV Saar, som bildas genom ett gemensamt venture i Tyskland SGS-Group och TUV Saarland, har blivit det ledande ackrediterade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad program vara för säkerhetsrelaterade system i hela världen. Den industriella säkerhets standarden IEC 61508 och alla standarder som är härledda från IT, inklusive IEC-62304, ISO 26262 och EN 50128, används för att säkerställa den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, process kontroll system, industriella maskiner, bil-och järnvägs styrnings system.

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="SGS – TUV-certifiering":::

Azure återställnings tider NetX Duo har erkänts av UL för att följa UL 60730-1 bilaga H, CSA E60730-1 bilaga H, IEC 60730-1 bilaga H, UL 60335-1 Bilaga R, IEC 60335-1 Bilaga R och UL 1998 säkerhets standarder för program vara i programmerbara komponenter. UL är ett globalt, oberoende, säkerhets vetenskaps företag med mer än en Century av expertis som förnyar säkerhetslösningar, från det offentliga införandet av elektricitet till genombrott i hållbarhet, förnybar energi och Nanotechnology.

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="CRU UL-certifiering":::

Artefakter (certifikat, säkerhets hand bok, test rapport osv.) som är associerade med TUV och UL-certifieringar är tillgängliga för försäljning.

I de fall där programmet behöver ytterligare certifiering, är en certifierings tjänst tillgänglig via Microsoft för att tillhandahålla certifierings certifiering till olika standarder med hjälp av den aktuella maskin varu plattformen och till och med program koden. Kontakta oss för mer information om vår certifierings tjänst.

## <a name="eal4-common-criteria-security-certification"></a>EAL4 + gemensamma villkor säkerhets certifiering

Azure återställnings tider har uppnått säkerhets certifieringen EAL4 + Common Criteria. Målet för evalution (TOE) täcker Azure återställnings tider ThreadX, Azure återställnings tider NetX Duo, Azure återställnings tider NetX Secure TLS och Azure återställnings tider NetX MQTT. Detta representerar de mest typiska IoT-protokollen som krävs av djupt inbäddade sensorer, enheter, yttre routrar och gatewayer.

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="EAL-certifiering":::

Den utvärderings funktion för IT-säkerhet som används för Microsoft Azure återställnings tider SC Security Certificate är Brightsight BV och certifikat utfärdaren är SERTIT.

## <a name="fips-140-2-validated"></a>FIPS 140-2 verifierad

Azure återställnings tider NetX-krypterings bibliotek har erhållit FIPS 140-2-certifiering (Federal Information Processing 140-2 Standardization) för program vara, som anger krav för krypteringsalgoritmer. FIPS 140-2 kräver alla federala myndigheter och avdelningar som använder kryptografisk säkerhet för att uppfylla vissa standarder som rör krypterings styrka och-funktioner. Dessa kryptografiska säkerhets standarder är också kända i Kanada och EU.

Utvärderings versionen av informations säkerhet som används för Azure återställnings tider NetX-krypterings bibliotek var atsec och certifikat utfärdaren är National Institute of Standards and Technology (NIST). Granska [NIST-webbplatsen](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) för ytterligare information.

## <a name="interoperability-verification"></a>Verifiering av interoperabilitet

NetX Duo överensstämmer med RFC-standarder och erbjuder fullständig interoperabilitet med enheter för de flesta leverantörer.

![IPv6-färdig logo typ](./media/overview-netx-duo/ipv6-ready-logo.png)

Azure återställnings tider NetX Duo är en av de enda inbäddade TCP/IP-stackarna för att uppnå den rigorösa IPv6-Ready-certifieringen, bevis på att den har genomgått avvikelser och samverkans, administrerad och verifierad av IPv6-forumet. NetX Duo använder också IxANVL för bransch standard (automatiskt bibliotek för nätverks validering) för implementeringen av NetX Duo Core TCP/IP-protokollet.

## <a name="comprehensive-iot-solution"></a>Omfattande IoT-lösning

Azure återställnings tider NetX Duo har ett remarkably litet utrymme på 9 KB till 15 KB för grundläggande IP-och UDP-stöd. NetX Duo har ett av de mest omfattande TCP/IP-nätverken för djupt inbäddade IoT-program. Det här stödet omfattar följande tilläggs protokoll produkter:

MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP

## <a name="advanced-technology"></a>Avancerad teknik

Azure återställnings tider NetX Duo är en avancerad teknik som innehåller:

* Piconet™-arkitektur
* Automatisk skalning
* ™ För UDP Fast-Path Technology
* Flexibel paket hantering
* API för Zero-kopiering och implementering
* Stöd för multihomed
* Valfri tids gräns vid alla avbrott
* Stöd för statisk routning
* IPsec
* SSL/TLS/DTLS
* Azure återställnings tider TraceX system Analysis support

## <a name="fastest-time-to-market"></a>Snabbast tid till marknad

Azure återställnings tider NetX Duo är enkelt att installera, lära sig, använda, felsöka, verifiera, certifiera och underhålla. Det innebär att NetX Duo är en av de mest populära TCP/IP-stackarna för inbäddade IoT-enheter, inklusive många SoCs från Broadcom, Gainspan osv. Vår konsekventa tid till marknads fördelen bygger på:

* Kvalitets dokumentation – Läs vår [Användar handbok för Azure återställnings tider netx Duo](about-this-guide.md) och se själv!
* Fullständig käll kods tillgänglighet
* Lätt att använda API
* Omfattande och avancerad funktions uppsättning

## <a name="one-simple-license"></a>En enkel licens

Det kostar inget att använda och testa käll koden och ingen kostnad för produktions licenser när de distribueras till förinstallerade enheter, men alla andra enheter behöver en enkel årlig licens.

## <a name="full-highest-quality-source-code"></a>Fullständig käll kod med högsta kvalitet

Under åren har Azure återställnings tider NetX Duo-källkoden ställt in kvalitet och enkel förståelse. Dessutom tillhandahåller konventionen om en funktion per fil för enkel käll navigering.

## <a name="supports-most-popular-architectures"></a>Har stöd för de flesta populära arkitekturerna

Azure återställnings tider NetX Duo körs på de flesta populära 32/64-bitars mikroprocessorer som är färdiga, helt testade och fullt stödda, inklusive följande avancerade arkitekturer:

**Analoga enheter**: SHARC, Blackfin, CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: avsöknings MCU

**Arm**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitars/R4/R5, TrustZone ARMv8-M

**Takt**: Xtensa, Diamond

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, WICED WiFi

**Cypress**: RISC-V

**Kiseldioxid**: ESI – RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel & Intel FPGA**: X36/Pentium, XSCALE, Nios II, Cyclone, Arria 10

**Mikrochip**: avr32, ARM7, ARM9, cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/sa, PIC24/PIC32

**Mikrohalv**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, coldfire, Kinetis cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, synergieffekt

**Silicon** Labb: EFM32

**Sammanfattning**: båge 600, 700, båge EM, båg HS

**St**: STM32, ARM7, ARM9, cortex-M3/M4/M7

**TL**: C5xxx, C6xxx, Stellaris, Sitara, tiva-C

**Wave-bearbetning**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class

**Xilinx**: mikroblixt, powerpc 405, ZYNQ, ZYNQ UltraSCALE

*Alla tids gränser och storleks värden i listan är uppskattningar och kan skilja sig åt på din utvecklings plattform.*

## <a name="related-services"></a>Relaterade tjänster

Azure Security Center för IoT återställnings tider Security-modulen innehåller en omfattande säkerhetslösning för Azure återställnings tider-enheter. Säkerhetsmodulen för Azure återställnings tider erbjuder skadlig identifiering av nätverks aktiviteter, anpassad avisering baserad enhets beteende bas linje och hjälper till att förbättra enhetens säkerhets hygien. Lär dig mer om [säkerhetsmodulen för Azure återställnings tider](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) eller kom igång med att [Konfigurera säkerhetsmodulen för Azure återställnings tider](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) snabb start.

## <a name="next-steps"></a>Nästa steg

Om du vill veta mer om NetX Duo börjar du med [användar handboken för Azure återställnings tider netx Duo](about-this-guide.md).
