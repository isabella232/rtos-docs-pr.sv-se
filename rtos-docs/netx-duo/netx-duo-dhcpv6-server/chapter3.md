---
title: Kapitel 3 – konfigurations alternativ för DHCPv6-server i Azure återställnings tider NetX Duo
description: Det här kapitlet innehåller en beskrivning av konfigurations alternativen för DHCPv6-server i Azure återställnings tider NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 30f6e1c657eb62ebec48d6bb8caafac320727146
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827003"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-server-configuration-options"></a>Kapitel 3 – konfigurations alternativ för DHCPv6-server i Azure återställnings tider NetX Duo

Det finns flera konfigurations alternativ för att skapa ett NetX Duo DHCPv6-serverprogram. I följande lista beskrivs var och en i detalj:
  
- **NX_DISABLE_ERROR_CHECKING** Det här alternativet tar bort DHCPv6-fel kontroll. Den aktive ras vanligt vis när programmet felsöks.  
  
- **NX_DHCPV6_SERVER_THREAD_STACK_SIZE** Detta definierar storleken på DHCPv6-trådens stack. Som standard är storleken 4096 byte, vilket är mer än tillräckligt för de flesta NetX Duo-program.

- **NX_DHCPV6_SERVER_THREAD_PRIORITY** Detta definierar DHCPv6Server tråd prioritet. Detta bör vara lägre än DHCPv6-serverns uppgifts prioritet för IP-tråd. Standardvärdet är 2.

- **NX_DHCPV6_IP_LEASE_TIMER_INTERVAL** Tidsintervall i sekunder när ThreadX Scheduler anropas av schema funktionen för lån. Funktionen Entry ställer in en flagga för DHCPv6-servern för att öka alla klienters upplupna tid på sitt lån enligt timer-intervallet. Som standard är det här värdet 60.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL** Tidsintervall i sekunder när ThreadX Scheduler anropas av Scheduler-funktionen. Funktionen Entry anger en flagga för DHCPv6-servern för att öka den aktiva tiden för alla aktiva klientsessioner som periodiseras av timer-intervallet. Som standard är det här värdet 3.

Följande definierar gäller för status alternativ meddelande typ och det användar konfigurerbara meddelandet. Alternativet status visar resultatet av en klientbegäran:

- **NX_DHCPV6_STATUS_MESSAGE_SUCCESS** *"IA-alternativet beviljat"*

- **NX_DHCPV6_STATUS_NO_ADDRS_AVAILABLE** *"AI-alternativet har inte beviljats-inga adresser är tillgängliga"*

- **NX_DHCPV6_STATUS_MESSAGE_NO_BINDING** *"AI-alternativet inte har beviljats-ogiltig klientbegäran"*

- **NX_DHCPV6_STATUS_MESSAGE_NOT_ON_LINK** *"IA-alternativet inte beviljats – klienten är inte på länk"*

- **NX_DHCPV6_STATUS_MESSAGE_USE_MULTICAST** *"IA-alternativet inte beviljas-klienten måste använda multicast"*

- ALTERNATIVET **NX_DHCPV6_STATUS_MESSAGE_NO_ADDRS_AVAILABLE** *IA har inte beviljats-inga adresser är tillgängliga*

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID** Skapa ett DUID för server med ett tilldelat leverantörs-ID. Observera att DUID-typen måste anges NX_DHCPV6_DUID_TYPE_VENDOR_ASSIGNED.

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_LENGTH** Anger den övre gränsen för det tilldelade leverantörs-ID: t. Standardvärdet är 48.

- **NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID** Anger företags typen för DUID till privat leverantörs typ.

- **NX_DHCPV6_PACKET_WAIT_OPTION** Detta definierar vänte alternativet för Server *nx_udp_socket_receive* anrop. Detta är perfunctory eftersom socketen har fått ett meddelande om motringning från NetX Duo, så paketet är redan placerat i kö när DHCPv6-servern anropar Receive-funktionen. Standardvärdet är 1 sekund (1 * NX_IP_PERIODIC_RATE).

- **NX_DHCPV6_SERVER_DUID_TYPE** Detta definierar den DUID-typ för server som servern inkluderar i alla meddelanden till klienter. Standardvärdet är länk skikt plus tid (NX_DHCPV6_SERVER_DUID_TYPE_LINK_TIME).

- **NX_DHCPV6_SERVER_HW_TYPE** Detta definierar maskin varu typen i DUID-länk skiktet och länk lagret plus tids alternativ. Standardvärdet är NX_DHCPV6_SERVER_HARDWARE_TYPE_ETHERNET.

- **NX_DHCPV6_PREFERENCE_VALUE** Detta definierar inställnings alternativets värde mellan 0 och 255, där ju högre värde ju högre prioritet, i DHCPv6-alternativet för samma namn. Detta talar om för klienten vilken inställning som ska finnas på den här serverns erbjudande där flera DHCPv6-servrar är tillgängliga för att tilldela IP-adresser. Värdet 255 instruerar klienten att välja den här servern. Värdet noll anger att klienten är kostnads fri att välja. Standardvärdet är noll.

- **NX_DHCPV6_MAX_OPTION_REQUEST_OPTIONS** Detta definierar det maximala antalet alternativ begär anden i en klientbegäran som kan sparas till en klient post. Standardvärdet är 6.

- **NX_DHCPV6_DEFAULT_T1_TIME** Tiden i sekunder som tilldelas av servern på ett klient adress lån för när klienten ska börja förnya sin IP-adress. Standardvärdet är 2000 sekunder.

- **NX_DHCPV6_DEFAULT_T2_TIME** Tiden i sekunder som tilldelas av servern på ett klient adress lån för när klienten ska börja ombinda sin IP-adress, förutsatt att försöket att förnya misslyckades. Standardvärdet är 3000 sekunder.

- **NX_DHCPV6_DEFAULT_PREFERRED_TIME** Detta definierar hur lång tid i sekunder som tilldelats bythe-servern när en tilldelad klients IP-adresslån är föråldrad. Standardvärdet är 2 NX_DHCPV6_DEFAULT_T1_TIME.

- **NX_DHCPV6_DEFAULT_VALID_TIME** Detta definierar hur lång tid i sekunder som tilldelats av servern på ett tilldelat klient-IP-adresslån. När den här tiden har gått ut är klientens IP-adress ogiltig. Standardvärdet är 2 NX_DHCPV6_DEFAULT_PREFERRED_TIME.

- **NX_DHCPV6_STATUS_MESSAGE_MAX** Definierar den maximala storleken för Server meddelandet i fältet status alternativ meddelande. Standardvärdet är 100 byte.

- **NX_DHCPV6_MAX_LEASES** Definierar storleken på serverns IP-adresslån (t. ex. det högsta antalet IPv6-adresser som kan lagras). Som standard är det här värdet 100.

- **NX_DHCPV6_MAX_CLIENTS** Definierar storleken på serverns klient post tabell (t. ex. maximalt antal klienter som kan lagras). Värdet måste vara mindre än eller lika med värdet NX_DHCPV6_MAX_LEASES. Som standard är det här värdet 120.

- **NX_DHCPV6_PACKET_TIME_OUT** Definierar vänte läget i timer-Tick för DHCPv6-servern vänta på paket tilldelningar. Standardvärdet är 3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND.

- **NX_DHCPV6_PACKET_RECEIVE_WAIT** Definierar alternativet vänta i paket tilldelnings anrop i Server paketets pool. Standardvärdet är (3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND) eller 3 sekunder.

- **NX_DHCPV6_PACKET_SIZE** Detta definierar paketets nytto last för paket för Server paket. Standardvärdet är 500 byte.

- **NX_DHCPV6_PACKET_POOL_SIZE** Definierar storleken på Server paketets pool för de paket som servern ska allokera för att skicka DHCPv6-meddelanden. Standardvärdet är (10 * NX_DHCPV6_PACKET_SIZE).

- **NX_DHCPV6_TYPE_OF_SERVICE** Detta definierar typ av tjänst för överföring av UDP-paket. Som standard är det här värdet NX_IP_NORMAL.

- **NX_DHCPV6_FRAGMENT_OPTION** Detta definierar alternativet fragmentering av Server-socket. Standardvärdet är NX_DON ' T_FRAGMENT

- **NX_DHCPV6_TIME_TO_LIVE** Anger antalet routrar som DHCPv6-paket från servern kan ta hopp innan paketen tas bort. Standardvärdet är inställt på 0x80.

- **NX_DHCPV6_QUEUE_DEPTH** Anger antalet paket som ska behållas i servern UDP socket Receive Queue innan NetX Duo tar bort paket.