---
title: Kapitel 1 – en introduktion till nätverks adress Översättning
description: IP Network Address Translation (NAT) utvecklades ursprungligen för att lösa problemet med ett begränsat antal Internet IPv4-adresser.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3d01aa6f68e21ea82f65a59a19c4f5c7958a6b92
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825869"
---
# <a name="chapter-1---an-introduction-to-network-address-translation"></a>Kapitel 1 – en introduktion till nätverks adress Översättning

## <a name="the-need-for-network-address-translation"></a>Behovet av nätverks adress Översättning

IP Network Address Translation (NAT) utvecklades ursprungligen för att lösa problemet med ett begränsat antal Internet IPv4-adresser. Behovet av NAT uppstår när flera enheter behöver åtkomst till Internet, men endast en IPv4-Internet adress tilldelas av Internet leverantören.

Det finns även andra fördelar med att använda NAT. Nätverks sto pol Ogin utanför den lokala domänen kan ändras på många sätt. Kunder kan ändra leverantörer, företagets ben kan omorganiseras, eller så kan leverantörer sammanfogas eller delas. När den externa miljön ändras måste även adress tilldelningar för värdar inom den lokala domänen ändras så att de återspeglar dessa externa ändringar. Ändringar av den här typen kan vara dolda från användare i domänen genom att centralisera ändringar till en router med en enda adress översättning. NAT ger åtkomst för lokala värdar till det offentliga Internet och skyddar dem från direkt åtkomst från utsidan. Organisationer med en nätverks konfiguration främst för intern användning, med ett behov av tillfällig extern åtkomst är lämpliga kandidater för det här schemat.

## <a name="basic-nat-and-network-address-port-translation"></a>Grundläggande NAT-och nätverks adress port Översättning

En NAT-aktiverad router installeras mellan det offentliga nätverket och det privata nätverket. Den NAT-aktiverade routerns roll är att översätta mellan interna privata IPv4-adresser och den tilldelade offentliga IPv4-adressen, så alla enheter i det privata nätverket kan dela samma offentliga IPv4-adress.

I den grundläggande implementeringen av NAT äger NAT-routern en eller flera globalt registrerade IP-adresser som skiljer sig från sin egen IP-adress. Dessa globala adresser är tillgängliga för att tilldelas värdar i det privata nätverket antingen statiskt eller dynamiskt. NAPT, eller nätverks adress port översättning, är en variant av grundläggande NAT, där Network Address Translation utökas till att inkludera en "transport"-identifierare. Oftast är detta port numret för TCP-och UDP-paket och fråge-ID för ICMP-paket.

Anslutningar över NAT-gränser initieras vanligt vis av värdar i det privata nätverket som skickar utgående paket till en extern värd. Dessa värdar tilldelas vanligt vis *dynamiska* (temporära) IP-adresser för det här ändamålet. Det är dock också möjligt att ha anslutningar som initieras i motsatt riktning om det privata nätverket har "servrar", t. ex. HTTP-eller FTP-servrar som ska ta emot klient begär Anden från det externa nätverket. NAT tilldelar normalt dessa lokala värdar en *statisk* (permanent) IP-adress: port.

## <a name="how-network-address-translation-works"></a>Så här fungerar översättning av nätverks adresser

En typisk nätverks installation med en NAT-aktiverad router visas i bild 1.

![En typisk nätverks installation med en NAT-aktiverad router](media/image2.png)

**Bild 1 – en typisk nätverks installation med en NAT-aktiverad router**

En NAT-aktiverad router har vanligt vis två nätverks gränssnitt. Ett gränssnitt är anslutet till det offentliga Internet. den andra är ansluten till det privata nätverket. En typisk router i den här konfigurationen ansvarar för att dirigera IP-datagram mellan det privata nätverket och det offentliga nätverket baserat på målets IP-adress. En NAT-aktiverad router utför adress översättning innan ett IPv4-datagram dirigeras mellan det offentliga och det privata gränssnittet. En översättning upprättas för varje TCP-eller UDP-session, baserat på den interna käll adressen, käll port numret och den externa mål adressen och mål Port numret. För ICMP-ekobegäran och svar på svar används ICMP-fråge-ID i stället för port numret.

För att illustrera en typisk implementering av översättning av nätverks adresser, låt oss ta en nätverks konfiguration i bild 2.

![En typisk implementering av NAT (Network Address Translation)](media/image3.png)

**Bild 2 – en typisk implementering av NAT (Network Address Translation)**

I det här scenariot ansluter NAT-routern det privata nätverket till vänster och det offentliga nätverket till höger. Vi antar att IP-adressen för NAT-routerns gränssnitt är 202.151.25.14; i det privata nätverks gränssnittet använder NAT-routern IP-192.168.1.254. En nod i det privata nätverket initierar en TCP-anslutning till en webb server på Internet.

Bild 3 visar en övergripande vy över översättnings processen för nätverks adresser.

![En övergripande översikt över processen för översättning av nätverks adresser](media/image4.png)

**Bild 3 – en övergripande översikt över processen för översättning av nätverks adresser**

1. Klienten skickar ett TCP-SYN-meddelande till webb servern. Avsändar adressen är 192.168.1.15, port nummer 6732; mål adressen är 128.15.54.3, port nummer 80.
1. Paketet från klienten tas emot på det privata nätverks gränssnittet av NAT-routern. Regeln för utgående trafik gäller för paketet: avsändarens (klientens) adress översätts till NAT-routerns offentliga IP-202.15.25.14 och avsändar port numret översätts till TCP-port nummer 2015 i det offentliga gränssnittet.
1. Paketet skickas sedan via Internet och når slutligen mål värden 128.15.54.3. Observera att på mottagar sidan, baserat på IP-skiktets käll adress och port numret för TCP-skiktet, verkar paketet ha sitt ursprung från 202.151.24.14, port nummer 2015.
   Bild 4 visar NAT-processen på RETUR Sök vägen.

   ![NAT-process på RETUR Sök vägen](media/image5.png)

   **Bild 4 – NAT-process på RETUR Sök vägen**
1. I det här scenariot skickar Internet Host-128.15.54.3 ett svars paket med NAT-routerns Internet adress som mål.
1. Paketet når NAT-routern. Eftersom det här är ett bebindt paket gäller de inbounda översättnings reglerna: mål adressen ändras tillbaka till den ursprungliga avsändarens (klient) IP-adress: 192.168.1.15, målport nummer 6732.
1. Paketet vidarebefordras sedan till klienten via gränssnittet som är anslutet till det interna nätverket.

På detta sätt exponeras inte Internet nätverks adressen och port numret för avsändaren för andra värdar på det offentliga Internet.

## <a name="netx-duo-nat-features"></a>NetX Duo NAT-funktioner

När NAT-instansen skapas med *nx_nat_create* -anrop skapas NAT-tabellen översättning.

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

För att hålla koll på nätverks adress översättningarna för alla aktiva anslutningar mellan lokala och externa nätverk, upprätthåller den NetX Duo NAT-aktiverade routern en översättnings tabell med information om varje privat värd anslutning som innefattar käll-och mål-IP-adress och port nummer.

Platsen för översättnings tabellen ("cache") anges med dynamic_cache_memory-pekaren. Det här området måste vara 4 byte-justerat buffertutrymme. Storleken på tabellen (eller antalet poster) bestäms genom att den cachelagrade cachestorleken divideras dynamic_cache_size av storleken på en tabell post i NAT. Tabellen måste vara tillräckligt stor för det minimala antalet poster som anges av **NX_NAT_MIN_ENTRY_COUNT som definieras i *nx_nat. h*. Standardvärdet är 3.**

Tids gränsen för alla dynamiska poster i översättnings tabellen NetX Duo NAT initieras till NX_NAT_ENTRY_RESPONSE_TIMEOUT som definieras i *nx_nat. h*. Standardvärdet är 4 minuter (eller 240 system Tick för en 100 mHz-processor) enligt rekommendationerna i RFC 2663. Varje gång NetX Duo NAT tar emot eller skickar ett paket som matchar en dynamisk post i tabellen återställs tids gränsen för posten till NX_NAT_ENTRY_RESPONSE_TIMEOUT. När du söker i tabellen kommer även NetX Duo NAT att kontrol lera tabellen för utgångna poster och ta bort dem.

Om du vill skapa inkommande poster som statiska i tabellen, t. ex. för servrar i det lokala nätverket, tillhandahåller NetX Duo NAT *nx_nat_inbound_entry_create* -tjänsten. Om en tabell post definierar den lokala värd anslutningen som statisk upphör den aldrig att gälla.

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr,
    ULONG local_ip_address, USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

Den här tjänsten beskrivs i detalj i [kapitel 4 – Beskrivning av tjänster](chapter4.md)

Om översättnings tabellen är full och det inte går att lägga till fler poster under körningen, kommer NetX Duo NAT att meddela NAT-programmet med en cache-fullständig motringning om en är registrerad hos NAT-instansen. Detta görs med hjälp av tjänsten *nx_nat_cache_notify_set* :

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)(NX_NAT_DEVICE *nat_ptr));
```

Se [kapitel 4 – Beskrivning av tjänster](chapter4.md) för mer information om den här tjänsten.

## <a name="nat-packet-processing-in-netx-duo"></a>Bearbetning av NAT-paket i NetX Duo

NetX Duo NAT är avsett att användas på en IPv4-router. För att NAT ska fungera måste NetX Duo konfigureras för att vidarebefordra paket till NAT-servern. Mer information om hur du gör detta finns i kapitel 2 på NetX Duo NAT-installation. NAT-servern anger sedan om den kommer att förbruka (försöker vidarebefordra) paketet till en värd i något av dess nätverk. Om det inte kommer att använda paketet returneras paketet till NetX Duo för att bearbeta paketet som vanligt.

När NAT-servern tar emot ett paket för att vidarebefordra från NetX Duo fastställer det om paketet är inkommande eller utgående.

För utgående paket kontrollerar NAT-servern paketets IP-rubriks käll adress och port. Om översättnings tabellen inte innehåller någon post för ett paket som tidigare har skickats av denna värd för samma mål, kommer NAT att skapa en ny post som innehåller en unik IP-adress för global Källa: port för anslutningen och ändra paket rubrikerna med den nya IP-adressen: port innan du skickar den till det externa nätverket.

För inkommande paket söker NAT-servern efter en tidigare post i översättnings tabellen med en extern IP-adress: port som matchar paket målets IP-adress: port. Om ingen matchning hittas, ignoreras paketet om inte mål adressen: port är den externa adressen för servern i det lokala nätverket. Om den hittar en matchning ersätter den paket huvudets externa mål-IP-adress: port med den privata IP-adressen: port och skicka paketet till det lokala nätverket till den avsedda privata värden.

NetX Duo NAT använder en mängd TCP-, UDP-och ICMP-förflyttningsverktyget för att skapa unik lokal adress: port anslutningar för lokala värdar som ansluter med externa värdar. Följande användar konfigurerbara alternativ, definierade i *nx_nat. h,* definierar intervallet för varje protokoll:

```C
NX_NAT_START_TCP_PORT

NX_NAT_END_TCP_PORT

NX_NAT_START_UDP_PORT

NX_NAT_END_UDP_PORT

NX_NAT_START_ICMP_QUERY_ID

NX_NAT_END_ICMP_QUERY_ID
```

## <a name="nat-requirements-and-constraints"></a>NAT-krav och begränsningar

NetX Duo NAT kräver NetX Duo 5,8 eller senare. NAT-programmet kräver att en enskild IP-instans skapas och ett gränssnitt till det interna och externa fysiska nätverket.

Begränsningar

- NetX Duo NAT stöder TCP, UDP och ICMP. IGMP stöds inte.
- NetX Duo NAT stöder inte IPv6-adressering.
- NetX Duo NAT inkluderar inte DNS-eller DHCP-tjänster, men NetX Duo NAT kan integrera dessa tjänster med sina NAT-åtgärder.

## <a name="rfcs-supported-by-netx-duo-nat"></a>RFC: er som stöds av NetX Duo NAT

NetX Duo NAT-implementeringen baseras på information som presenteras i följande RFC: er:

- RFC 2663: terminologi och överväganden för IP-NAT (Network Address Translator)
- RFC 3022: traditionell IP nätverket Address Translator (traditionell NAT)
- RFC 4787: beteende krav för NAT (Network Address Translation) för unicast UDP
