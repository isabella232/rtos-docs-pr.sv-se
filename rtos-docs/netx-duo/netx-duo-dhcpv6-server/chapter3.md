---
title: Kapitel 3 – Azure RTOS alternativ för NetX Duo DHCPv6-serverkonfiguration
description: Det här kapitlet innehåller en beskrivning Azure RTOS konfigurationsalternativ för NetX Duo DHCPv6-servern.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1dc0d6e41118a2f67fe98758f1f31f84d074d7af342b9db93162ffe6354077ea
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792136"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-server-configuration-options"></a>Kapitel 3 – Azure RTOS alternativ för NetX Duo DHCPv6-serverkonfiguration

Det finns flera konfigurationsalternativ för att skapa ett NetX Duo DHCPv6-serverprogram. I följande lista beskrivs var och en i detalj:
  
- **NX_DISABLE_ERROR_CHECKING** Det här alternativet tar bort DHCPv6-felkontroll. Det aktiveras vanligtvis när programmet felsöks.  
  
- **NX_DHCPV6_SERVER_THREAD_STACK_SIZE** Detta definierar storleken på DHCPv6-trådstacken. Som standard är storleken 4 096 byte, vilket är mer än tillräckligt för de flesta NetX Duo-program.

- **NX_DHCPV6_SERVER_THREAD_PRIORITY** Detta definierar trådprioritet för DHCPv6Server. Detta bör vara lägre än DHCPv6-serverns IP-trådaktivitetsprioritet. Standardvärdet är 2.

- **NX_DHCPV6_IP_LEASE_TIMER_INTERVAL** Timerintervall i sekunder när lease timer entry-funktionen anropas av ThreadX-schemaläggaren. Funktionen entry anger en flagga för DHCPv6-servern för att öka alla klienters upplupna tid på lånet med timerintervallet. Som standard är det här värdet 60.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL** Timerintervall i sekunder när session timer entry-funktionen anropas av ThreadX-schemaläggaren. Funktionen entry anger en flagga för DHCPv6-servern för att öka all aktiv klientsessionstid som ackumuleras med timerintervallet. Som standard är det här värdet 3.

Följande definierar gäller för meddelandetypen för statusalternativet och det användarkonfigurerbara meddelandet. Statusalternativet anger resultatet av en klientbegäran:

- **NX_DHCPV6_STATUS_MESSAGE_SUCCESS** *"IA-ALTERNATIV BEVILJAT"*

- **NX_DHCPV6_STATUS_NO_ADDRS_AVAILABLE** *"IA-ALTERNATIVET INTE BEVILJAT– INGA ADRESSER ÄR TILLGÄNGLIGA"*

- **NX_DHCPV6_STATUS_MESSAGE_NO_BINDING** *"IA-ALTERNATIVET BEVILJAS INTE OGILTIG KLIENTBEGÄRAN"*

- **NX_DHCPV6_STATUS_MESSAGE_NOT_ON_LINK** *"IA-ALTERNATIVET INTE BEVILJAD KLIENT INTE PÅ LÄNK"*

- **NX_DHCPV6_STATUS_MESSAGE_USE_MULTICAST** *"IA-ALTERNATIVET INTE BEVILJAD-KLIENT MÅSTE ANVÄNDA MULTICAST"*

- **NX_DHCPV6_STATUS_MESSAGE_NO_ADDRS_AVAILABLE** *IA-ALTERNATIVET INTE BEVILJAT – INGA ADRESSER ÄR TILLGÄNGLIGA*

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID** Skapa ett SERVER-DUID med ett leverantörs tilldelat ID. Observera att DUID-typen måste anges NX_DHCPV6_DUID_TYPE_VENDOR_ASSIGNED.

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_LENGTH** Anger den övre gränsen för det tilldelade ID:t för leverantör. Standardvärdet är 48.

- **NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID** Anger företagstyp för DUID till privat leverantörstyp.

- **NX_DHCPV6_PACKET_WAIT_OPTION** Detta definierar väntealternativet  för Server nx_udp_socket_receive-anropet. Detta är perfunctory eftersom socketen har ett meddelande om att få återanrop från NetX Duo, så paketet är redan iqueued när DHCPv6-servern anropar mottagningsfunktionen. Standardvärdet är 1 sekund (1 * NX_IP_PERIODIC_RATE).

- **NX_DHCPV6_SERVER_DUID_TYPE** Detta definierar den Server DUID-typ som servern inkluderar i alla meddelanden till klienter. Standardvärdet är länkskikt plus tid (NX_DHCPV6_SERVER_DUID_TYPE_LINK_TIME).

- **NX_DHCPV6_SERVER_HW_TYPE** Detta definierar maskinvarutypen i DUID-länklagret och länklagret plus tidsalternativ. Standardvärdet är NX_DHCPV6_SERVER_HARDWARE_TYPE_ETHERNET.

- **NX_DHCPV6_PREFERENCE_VALUE** Detta definierar inställningsalternativvärdet mellan 0 och 255, där ju högre värde desto högre prioritet, i DHCPv6-alternativet med samma namn. Detta talar om för klienten vilken inställning som ska användas på den här serverns erbjudande där flera DHCPv6-servrar är tillgängliga för att tilldela IP-adresser. Värdet 255 instruerar klienten att välja den här servern. Värdet noll anger att Klienten kan väljas utan kostnad. Standardvärdet är noll.

- **NX_DHCPV6_MAX_OPTION_REQUEST_OPTIONS** Detta definierar det maximala antalet alternativbegäranden i en klientbegäran som kan sparas till en klientpost. Standardvärdet är 6.

- **NX_DHCPV6_DEFAULT_T1_TIME** Tiden i sekunder som servern har tilldelats på ett klientadresslån för när klienten ska börja förnya sin IP-adress. Standardvärdet är 2 000 sekunder.

- **NX_DHCPV6_DEFAULT_T2_TIME** Tiden i sekunder som servern har tilldelats på ett klientadresslån för när klienten ska börja binda om sin IP-adress förutsatt att försöket att förnya misslyckades. Standardvärdet är 3 000 sekunder.

- **NX_DHCPV6_DEFAULT_PREFERRED_TIME** Detta definierar tiden i sekunder som servern tilldelas för när ett tilldelat klient-IP-adresslån blir inaktuellt. Standardvärdet är 2 NX_DHCPV6_DEFAULT_T1_TIME.

- **NX_DHCPV6_DEFAULT_VALID_TIME** Detta definierar förfallotiden i sekunder som tilldelas av servern på ett tilldelat klient-IP-adresslån. När den här tiden har gått ut är klientens IP-adress ogiltig. Standardvärdet är 2 NX_DHCPV6_DEFAULT_PREFERRED_TIME.

- **NX_DHCPV6_STATUS_MESSAGE_MAX** Definierar den maximala storleken för servermeddelandet i meddelandefältet för statusalternativet . Standardvärdet är 100 byte.

- **NX_DHCPV6_MAX_LEASES** Definierar storleken på serverns IP-lånetabell (t.ex. det maximala antalet IPv6-adresser som är tillgängliga för lån som kan lagras). Som standard är det här värdet 100.

- **NX_DHCPV6_MAX_CLIENTS** Definierar storleken på serverns klientposttabell (t.ex. maximalt antal klienter som kan lagras). Det här värdet ska vara mindre än eller lika med värdet för NX_DHCPV6_MAX_LEASES. Som standard är det här värdet 120.

- **NX_DHCPV6_PACKET_TIME_OUT** Definierar väntealternativet i timer tick för DHCPv6-serverns väntan på paketallokeringar. Standardvärdet är 3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND.

- **NX_DHCPV6_PACKET_RECEIVE_WAIT** Definierar väntealternativet i paket allokera anrop i serverpaketpoolen. Standardvärdet är (3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND) eller 3 sekunder.

- **NX_DHCPV6_PACKET_SIZE** Detta definierar paketnyttolasten för serverpaketpoolpaketen. Standardvärdet är 500 byte.

- **NX_DHCPV6_PACKET_POOL_SIZE** Definierar serverpaketpoolens storlek för paket som servern allokerar för att skicka DHCPv6-meddelanden ut. Standardvärdet är (10 * NX_DHCPV6_PACKET_SIZE).

- **NX_DHCPV6_TYPE_OF_SERVICE** Detta definierar typen av tjänst för UDP-paketöverföring. Som standard är det här värdet NX_IP_NORMAL.

- **NX_DHCPV6_FRAGMENT_OPTION** Detta definierar alternativet Fragmentering av serversocket. Standardvärdet är NX_DON T_FRAGMENT

- **NX_DHCPV6_TIME_TO_LIVE** Anger antalet routrar DHCPv6-paket från servern kan "hopp" passera innan paket ignoreras. Standardvärdet är inställt på 0x80.

- **NX_DHCPV6_QUEUE_DEPTH** Anger antalet paket som ska behållas i serverns UDP-socket-mottagningskö innan NetX Duo tar bort paket.