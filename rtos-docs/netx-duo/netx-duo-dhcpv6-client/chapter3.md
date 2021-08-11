---
title: Kapitel 3 – Azure RTOS konfigurationsalternativ för NetX Duo DHCPv6
description: Det finns flera konfigurationsalternativ för att skapa Azure RTOS NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 129d1421215452448b1de4626fdeda530a5466bd63ed0c758676c3ad60f9d6fb
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782429"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a>Kapitel 3 – Azure RTOS konfigurationsalternativ för NetX Duo DHCPv6

Det finns flera konfigurationsalternativ för att skapa Azure RTOS NetX Duo DHCPv6. I följande lista beskrivs var och en i detalj:  
  
  
- **NX_DHCPV6_THREAD_PRIORITY** Prioritet för klienttråden. Som standard anger det här värdet att klienttråden körs med prioritet 2.

- **NX_DHCPV6_MUTEX_WAIT** Timeout-alternativ för att hämta ett exklusivt lås på en DHCPv6-klient mutex. Standardvärdet är TX_WAIT_FOREVER.

- **NX_DHCPV6_TICKS_PER_SECOND** Förhållandet mellan tick och sekunder. Detta är processorberoende. Standardvärdet är 100.

- **NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Tidsintervall i sekunder då TIMERn för IP-livslängd uppdaterar hur lång tid klienten har tilldelats den aktuella IP-adressen. Som standard är det här värdet 1.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL**  Tidsintervall i sekunder då sessionstimern uppdaterar hur lång tid klienten har varit i session som kommunicerar med servern. Som standard är det här värdet 1.

- **NX_DHCPV6_MAX_IA_ADDRESS** Det maximala antalet IA-adresser som kan läggas till i klientposten. Standardvärdet är 1. 

- **NX_DHCPV6_NUM_DNS_SERVERS** Antal DNS-servrar som ska lagras i klientposten. Standardvärdet är 2.

- **NX_DHCPV6_NUM_TIME_SERVERS** Antal tidsservrar som ska lagras på klientposten. Standardvärdet är 1.

- **NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Storleken på bufferten i klientposten som ska innehålla klientens nätverksdomännamn. Standardvärdet är 30.

- **NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Storleken på bufferten i klientposten som ska innehålla klientens tidszon. Standardvärdet är 10.

- **NX_DHCPV6_MAX_MESSAGE_SIZE** Storleken på bufferten i klientposten för att innehålla alternativets statusmeddelande i ett serversvar. Standardvärdet är 100 byte.

- **NX_DHCPV6_PACKET_TIME_OUT** Time out i sekunder för att allokera ett paket från klientpaketpoolen. Standardvärdet är 3 sekunder.

- **NX_DHCPV6_TYPE_OF_SERVICE** Detta definierar typen av tjänst för UDP-paketöverföring från DHCPv6-klientsocketen. Standardvärdet är **NX_IP_NORMAL**.

- **NX_DHCPV6_TIME_TO_LIVE** Antalet gånger ett klientpaket vidarebefordras av en nätverksrouter innan paketet tas bort. Standardvärdet är 0x80.

- **NX_DHCPV6_QUEUE_DEPTH** Anger antalet paket som ska behållas i klientens UDP-socket-mottagningskö innan NetX Duo tar bort paket. Standardvärdet är 5.

## <a name="dhcpv6-message-transmission"></a>DHCPv6-meddelandeöverföring

Det finns en uppsättning DHCPv6-klientalternativ för att ställa in parametrar för DHCPv6-meddelandeöverföring. Dessa är: 

  - initial timeout

  - maximal fördröjning vid den första överföringen

  - maximal tidsgräns för återöverföring 

  - maximalt antal återöverföringar 

  - maximal varaktighet för att vänta på serversvar

Dessa parametrar gäller för vart och ett av DHCPv6-klientmeddelandena:

- Värva

- Begäran

- Förnya

- REBIND

- Släppa

- Nedgång

- Bekräfta

- Informera

Följande är en fullständig lista över dessa konfigurerbara alternativ och deras standard 

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

Om det inte finns någon gräns för tidsgränsen för återöverföring anger du antalet omöverföringar av meddelanden till 0. Om det inte finns någon gräns för hur många gånger ett DHCPv6-klientmeddelande skickas igen (återförsök) anger du antalet återöverföringar av meddelanden till 0.

> [!NOTE]
> Oavsett tidsgränsen eller antalet återförsök tas den bort från IP-adresstabellen när en giltig IPv6-adress upphör att gälla och kan inte längre användas av klienten. NetX Duo DHCPv6-klienten börjar automatiskt skicka BEGÄRAN-meddelanden som begär en ny IPv6-adress.