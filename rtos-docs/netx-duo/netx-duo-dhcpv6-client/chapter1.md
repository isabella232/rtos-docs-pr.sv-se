---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo DHCPv6-klienten
description: I IPv6-nätverk ersätter DHCPv6 DHCP för dynamisk global IP-adresstilldelning från en DHCPv6-server och erbjuder de flesta av samma funktioner och många förbättringar.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3bf3b52c53bb26e2c9c2c736ae35817eb967f609
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826097"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-client"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo DHCPv6-klienten

I IPv6-nätverk ersätter DHCPv6 DHCP för dynamisk global IP-adresstilldelning från en DHCPv6-server och erbjuder de flesta av samma funktioner och många förbättringar. Det här dokumentet beskriver i detalj hur Azure återställnings tider NetX Duo DHCPv6 client API används för att hämta IPv6-adresser.

## <a name="dhcpv6-communication"></a>DHCPv6-kommunikation

DHCPv6-protokollet använder UDP. Klienten använder port 546 och servern använder port 547 för att skicka DHCPv6-meddelanden. Klienten använder sin länk lokala adress för en käll adress för att initiera DHCPv6-begäranden till tillgängliga DHCPv6-servrar. När klienten skickar meddelanden som är avsedda för alla DHCPv6-servrar i nätverket använder den *All_DHCP_Relay_Agents_and_Servers* multicast- *FF02:: 01:02*. Detta är en reserverad, länkad multicast-adress.

## <a name="dhcpv6-process-of-requesting-an-ipv6-address"></a>DHCPv6-process för att begära en IPv6-adress

För att starta processen med att begära en global IPv6-adress tilldelning skickar klienten först ett VÄRVNINGs meddelande med hjälp av tjänsten *nx_dhcpv6_send_solicit* :

**UINT nx_dhcpv6_request_solicit (NX_DHCPV6 \* dhcpv6_ptr)**

Det här meddelandet skickas till alla servrar som använder *All_DHCP_Relay_Agents_and_Servers* -adressen. Klienten kan begära tilldelningen av vissa IPv6-adresser som ett tips till-servern i begäran om begär Ande. Den kan också begära annan konfigurations information för nätverket från-servern, till exempel DNS-server, NTP-server och andra alternativ i option-begäran i det EFTERFRÅGAde meddelandet.

En DHCPv6-server som kan betjäna en klientbegäran svarar med ett ANNONSERINGs meddelande som innehåller de IPv6-adresser som kan tilldelas till klienten, IPv6-adressens låne tid och eventuell ytterligare information som begärs av klienten. DHCPv6-klient protokollet kräver att klienten väntar under en tids period att ta emot ANNONSERINGs meddelanden från alla DHCPv6-servrar i nätverket. Den förbearbetar varje ANNONSERINGs meddelande som ett giltigt meddelande och skannar alternativ data för olika DHCPv6-parametrar. Det kontrollerar också Preference-värdet i alternativet Preference, om det tillhandahålls av servern. Om fler än ett ANNONSERINGs meddelande tas emot väljer DHCPv6-klienten NetX servern med det högsta preferens svärdet som togs emot i slutet av vänte perioden.

Undantaget är om klienten får ett ANNONSERINGs meddelande med Preference-värdet 255. Detta meddelande accepteras omedelbart och alla efterföljande ANNONSERINGs meddelanden ignoreras.

Vänte tiden definieras som den återöverförings period som DHCPv6-klienten väntar innan ett annat EFTERFRÅGAt meddelande skickas, om den inte har fått något svar från någon server. Den inledande tids gränsen för återöverföring i status för SOLICIT definieras av DHCPv6-protokollet som beskrivs i RFC 3315 som 1 sekund. Efterföljande återöverförings intervall, om DHCPv6-klienten Miss lyckas med att ta emot ett giltigt Server svar, dubbleras upp till högst 120 sekunder.

När du har valt-servern extraherar klienten data från annons meddelandet och skickar ett meddelande tillbaka till servern för att acceptera den tilldelade adress informationen och låne tiderna. Servern svarar med ett SVARSMEDDELANDE för att bekräfta att klientens IPv6-adress (er) är registrerade med servern som tilldelades till klienten.

DHCPv6-klienten registrerar de tilldelade IPv6-adresserna med IP-instansen (t. ex. NetX Duo). Om NetX Duo har kon figurer ATS för den duplicerade adress identifierings protokollet (pappa) kommer Duo automatiskt att skicka grann meddelanden för att verifiera att de tilldelade adresserna är unika i nätverket. I så fall, meddelar den DHCPv6-klienten när varje tilldelad adress har höjts från PRELIMINÄRt till giltig. DHCPv6-klienten befordras till ett begränsat tillstånd och enheten kan använda den IPv6-adressen för att skicka och skicka meddelanden. Om pappa-protokollet Miss lyckas meddelar NetX Duo DHCPv6-klienten och DHCPv6-klienten skickar ett neka-meddelande för de IPv6-adresser som tilldelas tillbaka till servern och återställer DHCPv6-klient statusen till INITIERINGs statusen.

### <a name="notification-of-successful-address-assignment-and-validation"></a>Meddelande om lyckad adress tilldelning och verifiering

Programmet kan bestämma resultatet av DHCPv6-klientens adress inbjudningar från tillstånds ändringar om DHCPv6-klienten är konfigurerad med motringningen för tillstånds ändring i *nx_dhcpv6_client_creates* tjänsten. Om den inte får något svar från servern kommer den status ändring som observerats från att begära att INITIERA. Om det tog emot ett svar från servern men servern inte kan tilldela adressen, meddelas programmet av fel återanrop av DHCPv6-klient servern om den konfigureras med en (även i *nx_dhcpv6_client_create).* Om klienten uppnått BINDNINGs tillstånd men sedan misslyckades pappa-kontrollen, ser den en tillstånds ändring från BINDNINGen till INIT. Tänk på att ett program som är aktiverat för pappa måste tillåta tid för pappa-kontrollen när du har startat processen för begäran. Detta är vanligt vis cirka 400-500 Tick (4-5 sekunder i de flesta fall).

### <a name="relinquishing-an-ipv6-address"></a>Lämna en IPv6-adress

Om och när klienten behöver släppa en tilldelad IPv6-adress informerar den DHCPv6-servern genom att anropa tjänsten *nx_dhcpv6_request_release* :

### <a name="uint-nx_dhcpv6_request_releasenx_dhcpv6-dhcpv6_ptr"></a>UINT nx_dhcpv6_request_release (NX_DHCPV6 \* dhcpv6_ptr)

DHCPv6-klienten skickar ett Unicast-meddelande som innehåller de tilldelade adresserna till den server som tilldelade adressen och väntar på ett svar som bekräftar att servern tog emot meddelandet.

Obs! det finns en annan process för klienten som stänger av, men planerar att fortsätta använda de tilldelade IPv6-adresserna vid omstart. Det skickar inte versions meddelandet vid inaktive om det inte planerar att begära en ny adress vid start. Se "krav på icke-flyktigt minne" för att få en förklaring till den här situationen.

### <a name="dhcpv6-lease-timeouts"></a>Timeout för DHCPv6-lån

IPv6-lånet som tilldelas av servern innehåller två timeout-parametrar, T1 och T2 i varje identitets Association – icke-temporära adresser (IANA)-block. En IANA beskrivs i någon annan i den här användar handboken. Om den förflutna tiden från när DHCPv6-klienten var kopplad till den tilldelade IPv6-adressen är lika med T1 börjar DHCPv6-klienten automatiskt förnya IPv6-adressen genom att skicka ett förnyelse meddelande. Om den förflutna tiden är lika med T2 skickar DHCPv6-klienten automatiskt ett rebind-meddelande om det inte fick några svar på sina FÖRNYAde begär Anden.

Två andra IPv6-låne parametrar, önskad och giltig livs längd, tilldelas till varje block med identitets associationer (IA) som finns i IANA-blocket. De önskade och giltiga livs längderna är när den tilldelade IPv6-adressen är inaktuell eller ogiltig. T1 måste vara mindre än den önskade livs längden. T2 måste vara mindre än den giltiga livs längden.

### <a name="ip-thread-task-requirements"></a>Aktivitets krav för IP-tråd

NetX Duo DHCPv6-klienten måste skapa en NetX Duo-tjänstinstans som är tidigare för att kunna skapa DHCPv6-klienten för att använda DHCPv6-klient tjänster.

UDP, IPv6 och ICMPv6 måste vara aktiverat på IP-instansen innan du använder DHCPv6-klienten.

  - *nx_udp_enable*

  - *nxd_ipv6_enable*

  - *nxd_icmp_enable*

### <a name="packet-pool-requirements"></a>Krav för paket pool

NetX Duo DHCPv6-klienten måste skapas en tidigare skapad modempool för att skicka DHCPv6-meddelanden. Storleken på poolen med paketets nytto last och antalet tillgängliga paket är att användaren kan konfigureras och är beroende av den förväntade volymen av DHCPv6-meddelanden och andra sändningar som programmet ska skicka.

Ett typiskt DHCPv6-meddelande är ungefär 200 byte beroende på antalet IA-adresser och DHCPv6-alternativ som begärs av klienten.

### <a name="network-requirements"></a>Nätverks krav

NetX Duo DHCPv6-klienten kräver att UDP-socketen som binds till port 546 skapas. Socketen skapas när aktiviteten DHCPv6-klienten skapas.

### <a name="non-volatile-memory-requirements"></a>Krav för icke-flyktigt minne

Om en DHCPv6-klient släpper sitt IPv6-lån med DHCPv6-servern vid avstängning och begär nya IPv6-adresser vid omstart, krävs inte icke-flyktig minnes lagring. Om en klient vill fortsätta att använda sitt tilldelade lån måste den lagra viss information om DHCPv6-klienten till icke-flyktigt minne mellan omstarter.

Icke-flyktiga minnes krav och DHCPv6-klientens API beskrivs ytterligare i **använda netx Duo DHCPv6-klienten** i kapitel två.

### <a name="netx-duo-dhcpv6-client-limitations"></a>NetX Duo DHCPv6-klient begränsningar

Den aktuella versionen av NetX Duo DHCPv6-klienten har följande begränsningar:

  - NetX Duo DHCPv6-klienten har inte stöd för alternativet Server-unicast för att skicka unicast DHCPv6-meddelanden till DHCPv6-servern även om servern anger att detta är tillåtet.

  - NetX Duo DHCPv6-klienten har inte stöd för den omkonfigurerande begäran där en server initierar IPv6-adress ändringar till klienter i nätverket.

  - NetX Duo DHCPv6-klienten har inte stöd för Enterprise-formatet för det unika ID-kontroll blocket för DHCPv6. Det stöder endast länk lager och länk lager plus tids format.

  - NetX Duo DHCPv6-klienten har inte stöd för tillfälliga associerings begär Anden (TA), men har stöd för icke-temporära (IANA) option-begär Anden.

## <a name="multihome-and-multiple-address-support"></a>Stöd för flera hem och flera adresser

DHCPv6-klienten har stöd för flera gränssnitt och flera adresser per gränssnitt. DHCPv6-klienttjänsten *nx_dhcpv6_client_set_interface* gör att klient programmet kan ange det nätverks gränssnitt som programmet ska kommunicera med DHCPv6-servern. DHCPv6-klienten som standard är det primära gränssnittet (index noll).

För flera adresser per gränssnitt behåller DHCPv6-klienten en intern lista med adresser som börjar vid indexet 0. Observera att samma adress som har registrerats med DHCPv6-klienten kanske inte nödvändigt vis finns i samma index i IP-tabellen för gränssnitts adresser.

Vissa kräver att ett adress index anges för DHCPv6-klient tjänster som hämtar information om klientens IPv6-adresslån. Ett exempel på hur du hämtar önskade och giltiga livstider visas nedan:

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                              UINT address_index, 
                                              NXD_ADDRESS *ip_address,
                                              ULONG preferred_lifetime, 
                                              ULONG *valid_lifetime)
```

Klient programmet kan också hämta antalet giltiga IPv6-adresser som tilldelats från tjänsten *nx_dhcpv6_get_valid_ip_address_count* :

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count)
```

Äldre DHCPv6-klient tjänster som skapades innan flera adresser stöddes i NetX Duo tar inget adress index. Med dessa tjänster tas de data som efter frågas från den primära globala IA-adressen, oavsett hur många IA-adresser som tilldelas till klienten. Ett exempel på detta visas nedan:

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address)
```

## <a name="netx-duo-dhcpv6-client-callback-functions"></a>NetX Duo DHCPv6 klienten motringning funktioner

*nx_dhcpv6_state_change_callback*

När DHCPv6-klienten ändras till ett nytt DHCPv6-tillstånd som ett resultat av bearbetningen av en DHCPv6-begäran, meddelas programmet med denna motringnings funktion.

*nx_dhcpv6_server_error_handler*

När DHCPv6-klienten får ett Server svar som innehåller ett *status* alternativ med en status som inte är noll (ej fungerande) meddelar den programmet med det här återanropet som innehåller status koden för Server fel.

Obs! eftersom dessa återanrops funktioner anropas från aktiviteten DHCPv6 klient tråd, får klient programmet inte anropa några NetX Duo DHCPv6-klient tjänster som kräver mutex-kontroll av DHCPv6-klienten, till exempel *nx_dhcpv6_start, nx_dhcpv6_stop* och alla API: er som skickar meddelanden direkt från återanropet, t. ex. *nx_dhcpv6_request_release*.

## <a name="dhcpv6-rfcs"></a>DHCPv6 RFC

NetX Duo DHCP är kompatibel med RFC3315, RFC3646 och relaterade RFC: er.