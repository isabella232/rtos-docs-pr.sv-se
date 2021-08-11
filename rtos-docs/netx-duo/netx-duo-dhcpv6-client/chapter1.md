---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo DHCPv6-klient
description: I IPv6-nätverk ersätter DHCPv6 DHCP för dynamisk global IP-adresstilldelning från en DHCPv6-server och erbjuder de flesta av samma funktioner samt många förbättringar.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f938be404c121f3080cfed1a81aa356f698538c4f557387009d951df40496a6d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791320"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-client"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo DHCPv6-klient

I IPv6-nätverk ersätter DHCPv6 DHCP för dynamisk global IP-adresstilldelning från en DHCPv6-server och erbjuder de flesta av samma funktioner samt många förbättringar. I det här dokumentet förklaras i detalj hur Azure RTOS NetX Duo DHCPv6-klient-API används för att hämta IPv6-adresser.

## <a name="dhcpv6-communication"></a>DHCPv6-kommunikation

DHCPv6-protokollet använder UDP. Klienten använder port 546 och servern använder port 547 för att utbyta DHCPv6-meddelanden. Klienten använder sin lokala länkadress för en källadress för att initiera DHCPv6-begäranden till de tillgängliga DHCPv6-servrarna. När klienten skickar meddelanden som är avsedda för alla DHCPv6-servrar i nätverket används All_DHCP_Relay_Agents_and_Servers-multicast-adressen *FF02::01:02*.  Det här är en reserverad, länkomfattning för multicast-adress.

## <a name="dhcpv6-process-of-requesting-an-ipv6-address"></a>DHCPv6-processen för att begära en IPv6-adress

För att påbörja processen med att begära en global IPv6-adresstilldelning skickar en klient först ett BEGÄR-meddelande med *hjälp nx_dhcpv6_send_solicit tjänsten:*

**UINT nx_dhcpv6_request_solicit(NX_DHCPV6 \* dhcpv6_ptr)**

Det här meddelandet skickas till  alla servrar med hjälp av All_DHCP_Relay_Agents_and_Servers adress. I REQUEST-begäran kan klienten begära tilldelningen av specifika IPv6-adresser som ett tips till servern. Den kan också begära annan information om nätverkskonfigurationen från servern, till exempel DNS-server, NTP-server och andra alternativ i alternativbegäran i MEDDELANDET BEGÄR.

En DHCPv6-server som kan hantera en klientbegäran svarar med ett ADVERTISE-meddelande som innehåller de IPv6-adresser som den kan tilldela till klienten, IPv6-adresslåntiden och eventuell ytterligare information som begärs av klienten. DHCPv6-klientprotokollet kräver att klienten väntar en stund för att ta emot ANNONSER-meddelanden från alla DHCPv6-servrar i nätverket. Den förbe bearbetar varje ADVERTISE-meddelande som ett giltigt meddelande och genomsöker alternativdata efter olika DHCPv6-parametrar. Den kontrollerar också inställningsvärdet i inställningsalternativet, om det anges av servern. Om fler än ett ADVERTISE-meddelande tas emot väljer NetX DHCPv6-klienten servern med det högsta inställningsvärdet som togs emot i slutet av väntetiden.

Undantaget är om klienten tar emot ett ADVERTISE-meddelande med inställningsvärdet 255. Den godkänner meddelandet omedelbart och tar bort alla efterföljande ADVERTISE-meddelanden.

Väntetiden definieras som den återöverföringsperiod som DHCPv6-klienten väntar på innan ett nytt BEGÄRA-meddelande skickas om den inte har tagit emot något svar från någon server. Den första tidsgränsen för återöverföring i TILLSTÅNDET BEGÄRD definieras av för DHCPv6-protokollet som beskrivs i RFC 3315 till 1 sekund. Efterföljande återöverföringsintervall, om DHCPv6-klienten inte kan ta emot ett giltigt serversvar, dubblas upp till högst 120 sekunder.

När du har valt server extraherar klienten data från MEDDELANDET ANNONSERa och skickar tillbaka ett BEGÄRANdemeddelande till servern för att acceptera den tilldelade adressinformationen och lånetiderna. Servern svarar med ett REPLY-meddelande för att bekräfta att klientens IPv6-adress (es) har registrerats med servern som tilldelats klienten.

DHCPv6-klienten registrerar den tilldelade IPv6-adressen (es) med IP-instansen (t.ex. NetX Duo). Om netX Duo har konfigurerats för PROTOKOLLET FÖR dubblettadressidentifiering (DUPLICATE Address Detection) (aktiverat som standard) skickar NetX Duo automatiskt meddelanden om granne begäran för att verifiera att de tilldelade adresserna är unika i nätverket. I så fall meddelas DHCPv6-klienten när varje tilldelad adress har befordrats frånFLYTATIV till GILTIG. DHCPv6-klienten upphöjs till BOUND-tillstånd och enheten kan använda den IPv6-adressen för att skicka och överföra meddelanden. Om PROTOCOL misslyckas meddelar NetX Duo DHCPv6-klienten och DHCPv6-klienten skickar ett NEKA-meddelande för IPv6-adressen(es) som tilldelats tillbaka till servern och återställer DHCPv6-klienttillståndet till INIT-tillståndet.

### <a name="notification-of-successful-address-assignment-and-validation"></a>Meddelande om lyckad adresstilldelning och verifiering

Programmet kan fastställa resultatet av DHCPv6-klientens adressbegäran från tillståndsändringarna om DHCPv6-klienten är  konfigurerad med tillståndsändringsanropet i nx_dhcpv6_client_create tjänsten. Om den inte får något svar från servern är den observerade tillståndsändringen från BEGÄRAN till INIT. Om den har fått ett svar från servern men servern inte kan tilldela adressen meddelas programmet av DHCPv6-klientens serverfel om det konfigurerats med en (även *i nx_dhcpv6_client_create).* Om klienten uppnått BOUND-tillståndet men sedan misslyckades med KONTROLLEN AVS visas en tillståndsändring från BOUND till INIT. Observera att ett program som har aktiverats för FUNKTIONEN MÅSTE tillåta tid för CHECK CHECK efter att processen för begäran har påbörjas. Vanligtvis är det cirka 400–500 tick (4–5 sekunder i de flesta fall).

### <a name="relinquishing-an-ipv6-address"></a>Ta bort en IPv6-adress

Om och när klienten behöver frigöra en tilldelad IPv6-adress informerar den DHCPv6-servern genom att *anropa nx_dhcpv6_request_release tjänsten:*

### <a name="uint-nx_dhcpv6_request_releasenx_dhcpv6-dhcpv6_ptr"></a>UINT nx_dhcpv6_request_release(NX_DHCPV6 \* dhcpv6_ptr)

DHCPv6-klienten skickar ett unicast RELEASE-meddelande som innehåller de tilldelade adresserna till den server som tilldelade adressen och väntar på ett SVAR som bekräftar att servern har tagit emot meddelandet.

Obs! Det finns en annan process för klienten som håller på att stängas av, men som planerar att fortsätta använda de tilldelade IPv6-adresserna vid omstart. Den skickar inte RELEASE-meddelandet om att stänga av om det inte planerar att begära en ny adress vid ström. Se "Ej beständiga minneskrav" för en förklaring av den här situationen.

### <a name="dhcpv6-lease-timeouts"></a>Timeouter för DHCPv6-lån

IPv6-lånet som tilldelats av servern innehåller två timeout-parametrar, T1 och T2, i varje Block för identitetsassociatorer – icke-temporära adresser (IANA). En IANA beskrivs i någon annanstans i den här användarhandboken. Om tiden från det att DHCPv6-klienten var bunden till den tilldelade IPv6-adressen är lika med T1, börjar DHCPv6-klienten automatiskt förnya IPv6-adressen genom att skicka ett RENEW-meddelande. Om tiden är lika med T2 skickar DHCPv6-klienten automatiskt ett REBIND-meddelande om den inte har fått några svar på sina RENEW-begäranden.

Två andra IPv6-låneparametrar, önskad och giltig livslängd, tilldelas till varje IA-block (Identity Association) som finns i IANA-blocket. Den önskade och giltiga livslängden är när den tilldelade IPv6-adressen är inaktuell eller ogiltig. T1 måste vara mindre än den önskade livslängden. T2 måste vara mindre än den giltiga livslängden.

### <a name="ip-thread-task-requirements"></a>Krav för IP-trådaktivitet

NetX Duo DHCPv6-klienten kräver att en NetX Duo IP-instans skapas tidigare för att DHCPv6-klienten ska kunna använda DHCPv6-klienttjänster.

UDP, IPv6 och ICMPv6 måste vara aktiverat på IP-instansen innan du använder DHCPv6-klienten.

  - *nx_udp_enable*

  - *nxd_ipv6_enable*

  - *nxd_icmp_enable*

### <a name="packet-pool-requirements"></a>Krav för paketpool

NetX Duo DHCPv6-klientens skapande kräver en tidigare skapad paketpool för att skicka DHCPv6-meddelanden. Paketpoolens storlek när det gäller paketnyttolast och antal tillgängliga paket är användarkonfigurerbar och beror på den förväntade volymen av DHCPv6-meddelanden och andra överföringar som programmet kommer att skicka.

Ett typiskt DHCPv6-meddelande är cirka 200 byte beroende på antalet IA-adresser och DHCPv6-alternativ som begärs av klienten.

### <a name="network-requirements"></a>Nätverkskrav

NetX Duo DHCPv6-klienten kräver att UDP-socket skapas som är bunden till port 546. Socketen skapas när DHCPv6-klientuppgiften skapas.

### <a name="non-volatile-memory-requirements"></a>Ej beständiga minneskrav

Om en DHCPv6-klient frigör sitt IPv6-lån med DHCPv6-servern vid strömavbrott och begär nya IPv6-adresser vid omstart, krävs inte ej beständiga minneslagring. Om en klient vill fortsätta att använda sitt tilldelade lån måste den lagra viss information om DHCPv6-klienten till icke-beständigt minne vid omstarter.

Icke-beständiga minneskrav och DHCPv6-klient-API:et beskrivs närmare i Använda **NetX Duo DHCPv6-klienten** i kapitel två.

### <a name="netx-duo-dhcpv6-client-limitations"></a>Begränsningar för NetX Duo DHCPv6-klienten

Den aktuella versionen av NetX Duo DHCPv6-klienten har följande begränsningar:

  - NetX Duo DHCPv6-klienten stöder inte alternativet Server Unicast för att skicka unicast DHCPv6-meddelanden till DHCPv6-servern även om servern anger att detta är tillåtet.

  - NetX Duo DHCPv6-klienten stöder inte omkonfigurationsbegäran där en server initierar IPv6-adressändringar för klienterna i nätverket.

  - NetX Duo DHCPv6-klienten stöder inte Enterprise-formatet för kontrollblocket för unik identifierare för DHCPv6. Det stöder endast formatet Link Layer och Link Layer Plus Time.

  - NetX Duo DHCPv6-klienten stöder inte tillfälliga associationer (TA) adressbegäranden, men har stöd för icke-tillfälliga alternativbegäranden (IANA).

## <a name="multihome-and-multiple-address-support"></a>Stöd för flera adresser och flera adresser

DHCPv6-klienten stöder flera gränssnitt och flera adresser per gränssnitt. DHCPv6-klienttjänsten, *nx_dhcpv6_client_set_interface* gör det möjligt för klientprogrammet att ange nätverksgränssnittet som programmet ska kommunicera med DHCPv6-servern på. DHCPv6-klienten använder som standard det primära gränssnittet (index noll).

För flera adresser per gränssnitt sparar DHCPv6-klienten en intern lista över adresser med början vid index 0. Observera att samma adress som registrerats med DHCPv6-klienten kanske inte nödvändigtvis finns i samma index i IP-tabellen med gränssnittsadresser.

För DHCPv6-klienttjänster som hämtar information om klientens IPv6-adresslån kräver vissa att ett adressindex anges. Ett exempel på hur du får önskad och giltig livslängd visas nedan:

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                              UINT address_index, 
                                              NXD_ADDRESS *ip_address,
                                              ULONG preferred_lifetime, 
                                              ULONG *valid_lifetime)
```

Klientprogrammet kan också hämta antalet giltiga IPv6-adresser som tilldelats från *nx_dhcpv6_get_valid_ip_address_count tjänsten:*

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count)
```

Äldre DHCPv6-klienttjänster som skapades innan flera adresser hade stöd i NetX Duo tar inte ett adressindex. Med dessa tjänster tas därför begärda data från den primära globala IA-adressen, oavsett hur många IA-adresser som har tilldelats klienten. Ett exempel på detta visas nedan:

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address)
```

## <a name="netx-duo-dhcpv6-client-callback-functions"></a>NetX Duo DHCPv6-funktioner för återanrop av klienter

*nx_dhcpv6_state_change_callback*

När DHCPv6-klienten ändras till ett nytt DHCPv6-tillstånd som ett resultat av bearbetningen av en DHCPv6-begäran, meddelar den programmet med den här återanropsfunktionen.

*nx_dhcpv6_server_error_handler*

När DHCPv6-klienten får ett serversvar som innehåller ett *statusalternativ* med statusen Icke-noll (inte lyckad) meddelas programmet med det här återanropet som innehåller serverns felstatuskod.

Obs! Eftersom dessa återanropsfunktioner anropas från DHCPv6-klienttrådsaktiviteten får klientprogrammet INTE anropa några NetX Duo DHCPv6-klienttjänster som kräver mutex-kontroll av DHCPv6-klienten, till exempel *nx_dhcpv6_start, nx_dhcpv6_stop och* något av de API:er som skickar meddelanden direkt från motringning, t.ex. *nx_dhcpv6_request_release*.

## <a name="dhcpv6-rfcs"></a>DHCPv6-RFC:er

NetX Duo DHCP är kompatibelt med RFC3315, RFC3646 och relaterade RFCs.