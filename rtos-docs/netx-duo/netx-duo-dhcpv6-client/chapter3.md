---
title: Kapitel 3 – konfigurations alternativ för Azure återställnings tider NetX Duo-DHCPv6
description: Det finns flera konfigurations alternativ för att skapa Azure återställnings tider NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5396b1c04581b5f79d337462368c4718ba9bb16
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826088"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a>Kapitel 3 – konfigurations alternativ för Azure återställnings tider NetX Duo-DHCPv6

Det finns flera konfigurations alternativ för att skapa Azure återställnings tider NetX Duo DHCPv6. I följande lista beskrivs var och en i detalj:  
  
  
- **NX_DHCPV6_THREAD_PRIORITY** Klient Trådens prioritet. Som standard anger det här värdet att klient tråden körs vid prioritet 2.

- **NX_DHCPV6_MUTEX_WAIT** Timeout-alternativ för att hämta ett exklusivt lås på en DHCPv6-klients mutex. Standardvärdet är TX_WAIT_FOREVER.

- **NX_DHCPV6_TICKS_PER_SECOND** Förhållandet mellan Tick och sekunder. Detta är processor beroende. Standardvärdet är 100.

- **NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Tidsintervallet i sekunder då IP-tidsintervallet för IP-livstiden uppdaterar den tid som den aktuella IP-adressen har tilldelats till klienten. Som standard är det här värdet 1.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL**  Tidsintervall i sekunder då sessionens timer uppdaterar den tid som klienten har varit i sessionen att kommunicera med servern. Som standard är det här värdet 1.

- **NX_DHCPV6_MAX_IA_ADDRESS** Det maximala antalet IA-adresser som kan läggas till i klient posten. Standardvärdet är 1. 

- **NX_DHCPV6_NUM_DNS_SERVERS** Antal DNS-servrar som ska lagras i klient posten. Standardvärdet är 2.

- **NX_DHCPV6_NUM_TIME_SERVERS** Antal tids servrar som ska lagras i klient posten. Standardvärdet är 1.

- **NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Storleken på bufferten i klient posten för att innehålla klientens nätverks domän namn. Standardvärdet är 30.

- **NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Storleken på bufferten i klient posten som ska innehålla klientens tidszon. Standardvärdet är 10.

- **NX_DHCPV6_MAX_MESSAGE_SIZE** Storleken på bufferten i klient posten för att innehålla alternativet status meddelande i ett Server svar. Standardvärdet är 100 byte.

- **NX_DHCPV6_PACKET_TIME_OUT** Tids gräns i sekunder för att allokera ett paket från klient paketets pool. Standardvärdet är 3 sekunder.

- **NX_DHCPV6_TYPE_OF_SERVICE** Detta definierar typ av tjänst för överföring av UDP-paket från DHCPv6-klientens socket. Standardvärdet är **NX_IP_NORMAL**.

- **NX_DHCPV6_TIME_TO_LIVE** Antalet gånger som ett klient paket vidarebefordras av en Nätverks router innan paketet tas bort. Standardvärdet är 0x80.

- **NX_DHCPV6_QUEUE_DEPTH** Anger antalet paket som ska behållas i klienten UDP socket Receive Queue innan NetX Duo tar bort paket. Standardvärdet är 5.

## <a name="dhcpv6-message-transmission"></a>DHCPv6-meddelande överföring

Det finns en uppsättning DHCPv6-klient alternativ för att ange parametrar för överföring av DHCPv6-meddelanden. Dessa är: 

  - Ursprunglig timeout

  - maximal fördröjning vid första överföringen

  - maximal timeout för återöverföring 

  - maximalt antal återöverföringar 

  - maximal varaktighet för att vänta på Server svar

Dessa parametrar gäller för varje DHCPv6-klient meddelande:

- BE

- ANMODA

- LÅNE

- OMBINDNING

- LANSERING

- VÄGRAR

- CONFIRM

- RÄTT

Följande är en fullständig lista över de konfigurerbara alternativen och deras standard 

values:

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

Om du inte vill ha någon gräns för en tids gräns för återöverföring anger du antalet återöverföringar för meddelanden till 0. Om du inte vill ha någon gräns för hur många gånger ett DHCPv6-klient meddelande ska skickas igen, anger du antalet återsändningar för meddelanden till 0.

> [!NOTE]
> Oavsett tids gräns eller antal återförsök, tas den bort från IP-tabellen och kan inte längre användas av klienten när en giltig IPv6-adress går ut. NetX Duo DHCPv6-klienten börjar automatiskt att skicka begär Anden som begär en ny IPv6-adress.