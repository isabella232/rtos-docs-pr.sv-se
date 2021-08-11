---
title: Kapitel 1 – En introduktion till network address translation
description: NAT (IP Network Address Translation) utvecklades ursprungligen för att lösa problemet med ett begränsat antal Internet-IPv4-adresser.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8639b87decd78f58a34fe6b8033a2427b560c872814abfdbbcb6057166412d0d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797473"
---
# <a name="chapter-1---an-introduction-to-network-address-translation"></a>Kapitel 1 – En introduktion till network address translation

## <a name="the-need-for-network-address-translation"></a>Behovet av network address translation

NAT (IP Network Address Translation) utvecklades ursprungligen för att lösa problemet med ett begränsat antal Internet-IPv4-adresser. Behovet av NAT uppstår när flera enheter behöver åtkomst till Internet, men endast en IPv4-internetadress tilldelas av Internetleverantören (ISP).

Det finns även andra fördelar med att använda NAT. Nätverkstopologin utanför den lokala domänen kan ändras på många sätt. Kunder kan ändra leverantörer, företagets stamnät kan omorganiseras eller så kan leverantörer sammanslå eller dela. När den externa topologin ändras måste adresstilldelningar för värdar inom den lokala domänen också ändras för att återspegla dessa externa ändringar. Ändringar av den här typen kan döljas för användare i domänen genom att centralisera ändringar till en enda adressöversättningsrouter. NAT ger åtkomst för lokala värdar till det offentliga Internet och skyddar dem från direktåtkomst utifrån. Organisationer med en nätverkskonfiguration som främst är för internt bruk, med behov av tillfällig extern åtkomst, är bra kandidater för det här schemat.

## <a name="basic-nat-and-network-address-port-translation"></a>Grundläggande NAT och portöversättning för nätverk

En NAT-aktiverad router installeras mellan det offentliga nätverket och det privata nätverket. Den NAT-aktiverade routerns roll är att översätta mellan de interna privata IPv4-adresserna och den tilldelade offentliga IPv4-adressen, så att alla enheter i det privata nätverket kan dela samma offentliga IPv4-adress.

I den grundläggande implementeringen av NAT "äger" NAT-routern en eller flera globalt registrerade IP-adresser som skiljer sig från sin egen IP-adress. Dessa globala adresser är tillgängliga för att tilldela värdar i det privata nätverket antingen statiskt eller dynamiskt. NAPT, eller Network Address Port Translation, är en variant av grundläggande NAT, där översättning av nätverksadresser utökas till att omfatta en "transport"-identifierare. Oftast är detta portnumret för TCP- och UDP-paket och fråge-ID för ICMP-paket.

Anslutningar över NAT-gränsen initieras vanligtvis av värdar i det privata nätverket som skickar utgående paket till en extern värd. Dessa värdar tilldelas vanligtvis *dynamiska* (tillfälliga) IP-adresser för detta ändamål. Det är dock också möjligt att ha anslutningar initierade i motsatt riktning om det privata nätverket har "servrar", t.ex. HTTP- eller FTP-servrar som accepterar klientbegäranden från det externa nätverket. NAT tilldelar vanligtvis dessa lokala värdar en *statisk* (permanent) IP-adress:port.

## <a name="how-network-address-translation-works"></a>Så här fungerar network address translation

En typisk nätverkskonfiguration med en NAT-aktiverad router illustreras i bild 1.

![En vanlig nätverkskonfiguration med en NAT-aktiverad router](media/image2.png)

**Bild 1 – En typisk nätverkskonfiguration med en NAT-aktiverad router**

En NAT-aktiverad router har vanligtvis två nätverksgränssnitt. Ett gränssnitt är anslutet till det offentliga Internet. den andra är ansluten till det privata nätverket. En typisk router i den här konfigurationen ansvarar för routning av IP-datagram mellan det privata nätverket och det offentliga nätverket baserat på målets IP-adress. En NAT-aktiverad router utför adressöversättning innan en IPv4-datagram dirigeras mellan det offentliga och det privata gränssnittet. En översättning upprättas för varje TCP- eller UDP-session, baserat på den interna källadressen, källportnumret och den externa måladressen och målportnumret. För datagram för ICMP-ekobegäran och svar används ICMP-fråge-ID:t i stället för portnumret.

För att illustrera en typisk implementering av Network Address Translation kan vi titta på en nätverkskonfiguration i bild 2.

![En typisk implementering av Network Address Translation](media/image3.png)

**Bild 2 – En typisk implementering av Network Address Translation**

I det här scenariot ansluter NAT-routern det privata nätverket till vänster och det offentliga nätverket till höger. Vi antar att IP-adressen för NAT-routergränssnittet är 202.151.25.14 på den offentliga nätverkssidan. i det privata nätverksgränssnittet använder NAT-routern IP-adressen 192.168.1.254. En nod i det privata nätverket initierar en TCP-anslutning med en webbserver på Internet.

Bild 3 visar en högnivåvy över processen för översättning av nätverksadresser.

![En högnivåvy över processen för översättning av nätverksadresser](media/image4.png)

**Bild 3 – En högnivåvy över processen för översättning av nätverksadresser**

1. Klienten skickar ett TCP SYN-meddelande till webbservern. Avsändaradressen är 192.168.1.15, portnummer 6732; måladressen är 128.15.54.3, portnummer 80.
1. Paketet från klienten tas emot i det privata nätverksgränssnittet av NAT-routern. Regeln för utgående trafik gäller för paketet: avsändarens (klientens) adress översätts till NAT-routerns offentliga IP-adress 202.15.25.14 och avsändarens (klientens) källportnummer översätts till TCP-portnumret 2015 i det offentliga gränssnittet.
1. Paketet överförs sedan via Internet och når slutligen målvärden 128.15.54.3. Observera att på mottagarsidan verkar paketet ha sitt ursprung från 202.151.24.14, portnummer 2015, baserat på källadressen för IP-lager och TCP-lagrets portnummer.
   Bild 4 visar NAT-processen på returvägen.

   ![NAT-processen på retursökvägen](media/image5.png)

   **Bild 4 – NAT-processen på returvägen**
1. I det här scenariot skickar Internetvärden 128.15.54.3 ett svarspaket med NAT-routerns Internetadress som mål.
1. Paketet når NAT-routern. Eftersom det här är ett inkommande paket gäller reglerna för inkommande översättning: måladressen ändras tillbaka till den ursprungliga avsändarens (klientens) IP-adress: 192.168.1.15, målportnummer 6732.
1. Paketet vidarebefordras sedan till klienten via gränssnittet som är anslutet till det interna nätverket.

På så sätt exponeras inte avsändarens Internetnätverksadress och portnummer för andra värdar på det offentliga Internet.

## <a name="netx-duo-nat-features"></a>NAT-funktioner i NetX Duo

När NAT-instansen skapas med *nx_nat_create* anrop skapas NAT-översättningstabellen.

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

NetX Duo NAT-aktiverade routrar har en översättningstabell med information om varje privat värdanslutning som innehåller käll- och mål-IP-adress och portnummer för att hålla reda på nätverksadressöversättningar för alla aktiva anslutningar mellan lokala och externa nätverk.

Platsen för den här översättningstabellen ("cache") anges med dynamic_cache_memory pekaren. Det här området måste vara ett 4 byte-justerat buffertutrymme. Storleken på tabellen (eller antalet poster) bestäms genom att dela upp cachestorleken dynamic_cache_size storleken på en NAT-tabellpost. Tabellen måste vara tillräckligt stor för det minsta antalet poster som anges **av NX_NAT_MIN_ENTRY_COUNT som definieras i *nx_nat.h*. Standardvärdet är 3.**

Tidsgränsen för alla dynamiska poster i NetX Duo NAT-översättningstabellen initieras till NX_NAT_ENTRY_RESPONSE_TIMEOUT som definieras *i nx_nat.h*. Standardvärdet är 4 minuter (eller 240 system tick för en 100 mHz-processor) som rekommenderas av RFC 2663. Varje gång NetX Duo NAT tar emot eller skickar ett paket som matchar en dynamisk post i tabellen återställs den postens time out till NX_NAT_ENTRY_RESPONSE_TIMEOUT. När du söker i tabellen kontrollerar NetX Duo NAT även tabellen efter utgångna poster och tar bort dem.

Om du vill skapa inkommande poster som statiska i tabellen, t.ex. för  servrar i det lokala nätverket, tillhandahåller NetX Duo NAT nx_nat_inbound_entry_create tjänsten. Om en tabellpost definierar den lokala värdanslutningen som statisk upphör den aldrig att gälla.

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr,
    ULONG local_ip_address, USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

Den här tjänsten beskrivs i detalj i [kapitel 4 – Beskrivning av tjänster](chapter4.md)

Om översättningstabellen är full och inga fler poster kan läggas till under körning meddelar NetX Duo NAT NAT NAT-programmet med ett fullständigt återanrop i cacheminnet om en sådan har registrerats med NAT-instansen. Detta görs med  hjälp av nx_nat_cache_notify_set tjänsten:

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)(NX_NAT_DEVICE *nat_ptr));
```

Se [kapitel 4 – Beskrivning av tjänster för](chapter4.md) mer information om den här tjänsten.

## <a name="nat-packet-processing-in-netx-duo"></a>NAT-paketbearbetning i NetX Duo

NetX Duo NAT är avsett att användas på en IPv4-router. För att NAT ska fungera måste NetX Duo konfigureras för att vidarebefordra paket till NAT-servern. Se kapitel 2 om NetX Duo NAT-installation för hur du gör det. NAT-servern anger sedan om den kommer att "använda" (försöka vidarebefordra) paketet till en värd i något av sina nätverk. Om paketet inte kommer att förbrukas returneras det till NetX Duo för att bearbeta paketet på vanligt sätt.

När NAT-servern tar emot ett paket som ska vidarebefordras från NetX Duo avgör den om paketet är inkommande eller utgående.

För utgående paket kontrollerar NAT-servern paketets källadress och port för IP-huvudet. Om översättningstabellen inte innehåller en post för ett paket som tidigare skickats av den här värden för samma mål, skapar NAT en ny post som innehåller en unik global käll-IP-adress:port för anslutningen och ändrar pakethuvudena med den nya IP-adressen:port innan den skickas till det externa nätverket.

För inkommande paket letar NAT-servern efter en tidigare post i översättningstabellen med en extern IP-adress: port som matchar paketets mål-IP-adress: port. Om ingen matchning hittas ignoreras paketet om inte måladressen: porten är den externa adressen för servern i det lokala nätverket. Om den hittar en matchning ersätter den pakethuvudets externa mål-IP-adress: port med den privata IP-adressen: port och skickar paketet till det lokala nätverket till den avsedda privata värden.

NetX Duo NAT använder ett antal TCP-, UDP- och ICMP-översättningsportar för att skapa unika lokala adresser: portanslutningar för lokala värdar som ansluter till externa värdar. Följande användarkonfigurerbara alternativ, som definieras *i nx_nat.h,* definierar intervallet för varje protokoll:

```C
NX_NAT_START_TCP_PORT

NX_NAT_END_TCP_PORT

NX_NAT_START_UDP_PORT

NX_NAT_END_UDP_PORT

NX_NAT_START_ICMP_QUERY_ID

NX_NAT_END_ICMP_QUERY_ID
```

## <a name="nat-requirements-and-constraints"></a>NAT-krav och -begränsningar

NetX Duo NAT kräver NetX Duo 5.8 eller senare. NAT-programmet kräver att du skapar en enda IP-instans och ett gränssnitt för det interna och externa fysiska nätverket.

Begränsningar:

- NetX Duo NAT stöder TCP, UDP och ICMP. IGMP stöds inte.
- NetX Duo NAT stöder inte IPv6-adressering.
- NetX Duo NAT inkluderar inte DNS- eller DHCP-tjänster, även om NetX Duo NAT kan integrera dessa tjänster med dess NAT-åtgärder.

## <a name="rfcs-supported-by-netx-duo-nat"></a>RFC:er som stöds av NetX Duo NAT

NetX Duo NAT-implementeringen baseras på information som presenteras i följande RFC:

- RFC 2663: TERMINOLOGI och överväganden Translator IP-nätverksadresser (NAT)
- RFC 3022: Traditionell IP Netowrk-Translator (traditionell NAT)
- RFC 4787: Beteendekrav för NAT (Network Address Translation) för Unicast UDP
