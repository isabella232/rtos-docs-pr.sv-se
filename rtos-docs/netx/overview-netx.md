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
# <a name="overview-of-azure-rtos-netx"></a>Översikt över Azure återställnings tider-NetX

Azure återställnings tider-NetX är en Azure-inbäddad TCP/IP IPv4-nätverks stack som är särskilt utformad för djupt inbäddade, real tids-och IoT-program. Azure återställnings tider NetX är Microsofts ursprungliga IPv4-nätverks stack och är i grunden en delmängd av Azure återställnings tider. NetX tillhandahåller inbäddade program med kärn nätverks protokoll som IPv4, TCP och UDP samt en fullständig uppsättning tilläggs protokoll på högre nivå. En liten genom gång, snabb körning och överlägsen enkel användning gör Azure återställnings tider NetX ett idealiskt val för de mest krävande inbäddade IoT-programmen.

## <a name="api-protocols"></a>API-protokoll

### <a name="telnet"></a>TELNET

* Minst 0,5 KB och 0,3 KB RAM-minne
* Stöd för klienter och servrar
* Intuitiva Telnet-API: er: *nx_telnet_ \**

### <a name="auto-ip"></a>Automatisk IP

* Automatisk tilldelning av IPv4-adress
* Minimal 1,2 KB, 300 byte RAM-minne
* Intuitiva AutoIP-API: er: *nx_autoip_ \**

### <a name="http---hypertext-transfer-protocolhttp"></a>HTTP-Hypertext Transfer Protocol (HTTP)

* Minimal 2,8 KB till 4.8 KBFLASH, 0,4 KB till 1,0 KB RAM-minne
* Stöd för klienter och servrar
* Intuitiva HTTP-API: er: *nx_http_ \**

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a>SMTP – Simple Mail Transfer Protocol (SMTP)

* Minst 4,1 KB och 0,6 KB RAM-minne
* Klient support
* Intuitiva SMTP-API: er: *nx_smtp_ \**

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a>DHCP-Dynamic Host Configuration Protocol (DHCP)

* Minimal 3,6 KB till 4,6 KB FLASH, 2,7 KB RAM-minne
* Stöd för klienter och servrar
* IPv4-stöd
* Intuitiva DHCP-API: er: *nx_dhcp_ \**

### <a name="p0p3---post-office-protocol-version-3-pop3"></a>P0P3-Post Office Protocol version 3 (POP3)

* Minst 8,1 KB och 1,4 KB RAM-minne
* Klient support
* Intuitiva P0P3-API: er: *nx_pop3_ \**

### <a name="snmp---simple-network-management-protocol-snmp"></a>SNMP – Simple Network Management Protocol (SNMP)

* Minst 10,9 KB och 2,6 KB RAM-minne
* Agent stöd för VI, v2 och v3
* Intuitiva SNMP-API: er: *nx_snmp_ \**

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a>FTP, TFTP-File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)

* FTP, minimal 1,8 KB till 7,2 KBFLASH, 0,6 KB till 2,1 KB RAM-minne
* TFTP minimal 1,7 KB till 2,4 KBFLASH, 0,3 KB till 1,8 KB RAM-minne
* Stöd för klienter och servrar
* Intuitiva API: er för FTP och TFTP: <i>nx_ftp_ *</i> eller <i>nx_tftp_*</i>

### <a name="ppp---polnt-to-point-protocol-ppp"></a>PPP-Polnt-to-PoInt Protocol (PPP)

* Minst 7,1 KB och 3,8 KB RAM-minne
* Intuitiva PPP-API: er: *nx_ppp_ \**

### <a name="sntp---simple-network-time-protocol-sntp"></a>SNTP – Simple Network Time Protocol (SNTP)

* Minst 4 KB och 0,5 KB RAM
* Klient support
* Intuitiva SNTP-API: er: *nx_sntp_ \**

### <a name="azure-rtos-netx-api"></a>Azure återställnings tider NetX-API

* Intuitiv och konsekvent API
* Substantiv-namn konvention för verb
* Snabb, noll-kopiera API-implementering
* Alla API-funktioner har ledande <i>nx_ *</i> för att enkelt identifiera som Azure återställnings tider netx
* Blockering av API-funktioner har en valfri tids gräns för trådar
* Valfritt BSD-lager för portning av äldre socket-kod

### <a name="igmp---internet-group-management-protocol-igmp"></a>IGMP – IGMP (Internet Group Management Protocol)

* Minimal 2,5 KB FLASH
* Stöd för IPv4 multicast-grupp
* IXIA-IxANVL verifierad
* Valfri IGMP-statistik
* Spårning på system nivå via Azure återställnings tider TraceX
* Intuitiva IGMP-API: er: *nx_igmp_ \**

### <a name="udp---user-datagram-protocol-udp"></a>UDP-UDP (User Datagram Protocol)

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

### <a name="tcp---transmission-control-protocol-tcp"></a>TCP-Transmission Control Protocol (TCP)

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

### <a name="icmp---internet-control-message-protocol-icmp"></a>ICMP-Internet Control Message Protocol (ICMP)

* Minimal 2,5 KB FLASH
* IPv4-stöd
* IXIA-IxANVL verifierad
* Ping-begäran och ping-svar
* Valfri tråd SUS pension vid ping-begäranden
* Valfri tids gräns vid alla avbrott
* Valfri ICMP-statistik
* Spårning på system nivå via Azure återställnings tider TraceX
* Intuitiva ICMP-API: er: *nx_icmp_ \**

### <a name="ipv4---internet-protocol-ip"></a>IPv4-Internet Protocol (IP)

* Minimal 3,5 KB till 8,5 KB FLASH, 2 KB till 3 KB RAM-minne
* Piconet™-arkitektur
* Snabba, nära WireSpeed prestanda
* Stöd för flera gränssnitt
* Stöd för multihomed
* Stöd för statisk routning
* Stöd för IP-fragmentering/omsammansättning
* IPv4-stöd
* IXIA-IxANVL verifierad
* Fas II färdig logo typ certifiering
* Valfri IP-statistik
* Väl definierat, intuitivt gränssnitt för fysiskt skikt driv rutin
* Spårning på system nivå via Azure återställnings tider TraceX
* Intuitiva API: er för IP-lager: *nx_ip_ \** *nxd_ip_ \**
* Förcertifierat av TUV och UL till IEC 61508 SIL 4, IEC 62304 klass C, ISO 26262 ASIL D och EN 50128 SW-SIL4

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a>ARP/RARP-Address Resolution Protocol (ARP), omvänd Address Resolution Protocol (RARP)

* Minimal 1,7 KB FLASH, RAM-storlek
* Dynamisk matchning av 32-smörgås IPv4-och 48-smörgås MAC-adresser
* IXIA-IxANVL verifierad
* Flexibel, användardefinierad ARP-cache
* Stöd för kostnads fria ARP
* Valfri ARP/RARP-statistik som fastställs av programmet
* Spårning på system nivå via Azure återställnings tider TraceX
* Intuitiva ARP/RARP-API: er: *nx_arp_ \** *nx_rarp_ \**

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a>ETHERNET, WiFi, BLUETOOTH LE, 15,4 osv.

## <a name="small-footprint"></a>Små

Azure återställnings tider NetX har ett remarkably litet utrymme på 9 KB till 15 KB för grundläggande IP-och UDP-stöd. Det krävs ytterligare 10 KB till 13 KB av instruktions områdets minne för TCP-funktioner. Azure återställnings tider NetX RAM-användningen är vanligt vis mellan 2,6 KB och 3,6 KB plus det minne för Packet-poolen som definieras av programmet. Precis som Azure återställnings tider ThreadX skalas storleken på Azure återställnings tider-NetX automatiskt utifrån de tjänster som används av programmet. Detta eliminerar behovet av komplicerade konfigurations-och bygg parametrar, vilket gör det enklare för utvecklaren.

## <a name="fast-execution"></a>Snabb körning

Azure återställnings tider NetX innehåller en paket för att skicka och ta emot paket utan kopiering och är mycket integrerat med Azure återställnings tider ThreadX för att uppnå snabbast möjliga prestanda. Azure återställnings tider NetX kan till exempel normalt uppnå nära WireSpeed-dataöverföringar på en processor på 80 MHz (eller mindre), samtidigt som en liten del av processorns cykler används.

## <a name="simple-easy-to-use"></a>Enkel, lätt att använda

Azure återställnings tider-NetX är enkelt att använda. Azure återställnings tider NetX-API: et är både intuitivt och mycket funktionellt. API-namnen består av riktiga ord och inte "alfabet soppor" eller förkortade namn som är vanliga i andra nätverks produkter. Alla Azure återställnings tider NetX-API: er har en ledande *nx_* och följer en namn konvention för substantiv-verb. Det finns dessutom en funktions konsekvens i hela API: et. Till exempel har alla API-funktioner som pausas en valfri tids gräns som fungerar på samma sätt. För äldre program erbjuder Azure återställnings tider NetX ytterligare ett BSD-kompatibelt lager. Det här lagret hjälper utvecklare att migrera stora nätverks program utan problem.

## <a name="interoperability-verification"></a>Verifiering av interoperabilitet

Azure återställnings tider-NetX överensstämmer med RFC-standarder och erbjuder fullständig interoperabilitet med enheter för de flesta leverantörer. Azure återställnings tider NetX använder också bransch standard IxANVL (automatiskt bibliotek för nätverks validering) för implementeringen av Azure återställnings tider NetX Core TCP/IP-protokollet.

## <a name="advanced-technology"></a>Avancerad teknik

Azure återställnings tider-NetX är en avancerad teknik som innehåller:

* Piconet™-arkitektur
* automatisk skalning
* ™ För UDP Fast-Path Technology
* flexibel paket hantering
* API för Zero-kopiering och implementering
* stöd för multihomed
* valfri tids gräns vid alla avbrott
* stöd för statisk routning
* Azure återställnings tider TraceX system Analysis support

## <a name="fastest-time-to-market"></a>Snabbast tid till marknad

Azure återställnings tider NetX är enkelt att installera, lära sig, använda, felsöka, verifiera, certifiera och underhålla. Därför är Azure återställnings tider NetX en av de mest populära TCP/IP-stackarna för inbäddade IoT-enheter, inklusive många SoCs från Broadcom, Gainspan och så vidare. Vår konsekventa tid till marknads fördelen bygger på:

* kvalitets dokumentation – Läs vår [Användar handbok för Azure återställnings tider netx](about-this-guide.md) och se själv!
* fullständig käll kods tillgänglighet
* lätt att använda API
* omfattande och avancerad funktions uppsättning

## <a name="one-simple-license"></a>En enkel licens

Det kostar inget att använda och testa käll koden och ingen kostnad för produktions licenser när de distribueras till förinstallerade enheter, men alla andra enheter behöver en enkel årlig licens.

## <a name="full-highest-quality-source-code"></a>Fullständig käll kod med högsta kvalitet

Under åren har Azure återställnings tider NetX-källkoden ställt in kvalitet och enkel förståelse. Dessutom tillhandahåller konventionen om en funktion per fil för enkel käll navigering.

## <a name="supports-most-popular-architectures"></a>Har stöd för de flesta populära arkitekturerna

Azure återställnings tider-NetX körs på de flesta populära 32/64-bitars mikroprocessorer, färdiga, fullständigt testade och fullt stödda, inklusive följande avancerade arkitekturer:

**Analoga enheter**: SHARC, Blackfin, CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: Apollo MCU

**Arm**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitars/R4/R5, TrustZone ARMv8-M

**Takt**: Xtensa, Diamond

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, WICED WiFi

**Cypress**: RISC-V

**Kiseldioxid**: ESI – RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel; Intel FPGA**: x36/Pentium, XScale, Nios II, Cyclone, Arria 10

**Mikrochip**: avr32, ARM7, ARM9, cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/sa, PIC24/PIC32

**Mikrohalv**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, coldfire, Kinetis cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, synergieffekt

**Silicon Labs**: EFM32

**Sammanfattning**: båge 600, 700, båge EM, båg HS

**St**: STM32, ARM7, ARM9, cortex-M3/M4/M7

**TL**: C5xxx, C6xxx, Stellaris, Sitara, tiva-C

**Wave-bearbetning**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class

**Xilinx**: mikroblixt, powerpc 405, ZYNQ, ZYNQ UltraSCALE

*Alla tids gränser och storleks värden i listan är uppskattningar och kan skilja sig åt på din utvecklings plattform.*
