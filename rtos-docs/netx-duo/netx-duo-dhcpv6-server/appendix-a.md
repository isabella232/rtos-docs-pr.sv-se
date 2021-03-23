---
title: Bilaga A – Azure återställnings tider NetX Duo DHCPv6-alternativ koder
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo DHCPv6-alternativ koder
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 36d673c34479ec2d476eeaa094c0dc02714ee010
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826064"
---
# <a name="appendix-a--azure-rtos-netx-duo-dhcpv6-option-codes"></a>Bilaga A – Azure återställnings tider NetX Duo DHCPv6-alternativ koder

| Alternativ              | Kod            | Beskrivning |
| ------------------- | ------------------- | --------------- |
| DUID för klient identifierare | 1 | Identifierar unikt en klient värd i nätverket |
| Server identifierare (DUID) | 2 | Identifierar unikt DHCPv6Server-värden i nätverket |
| Identitets koppling för icke-temporära adresser (IANA) | 3 | Parametrar för en icke-tillfällig IP-adresstilldelning |
| Identitets koppling för temporära adresser (IATA) | 4 | Parametrar för en tillfällig IP-adresstilldelning |
| IA-adress | 5 | Faktiska IPv6-adress och livstider för IPv6-adress som ska tilldelas till klienten |
| Option-begäran | 6 | En lista med informations begär Anden för att hämta nätverks information, till exempel DNS-server och andra parametrar för nätverks konfiguration. |
| Personanpassa | 7 | Ingår i Server annonsera meddelande till klienten för att påverka klientens val av servrar. Klienten måste välja en server med högre prioritets värde för andra servrar. 255 är det maximala värdet, medan noll anger att klienten kan välja vilken server som helst som svarar igen |
| Förfluten tid | 8 | Innehåller tiden (i 0,01 sekunder) när klienten initierar DHCPv6 Exchange med servern. Används av sekundära servrar för att avgöra om den primära servern svarar i tid på klient begär Anden. |
| Relä meddelande | 9 | Innehåller det ursprungliga meddelandet i relä meddelandet | 
| Autentisering | 11 | Innehåller information för att autentisera identiteten och innehållet i DHCPv6-meddelanden |
| Server-unicast | 12 | Servern skickar det här alternativet för att låta klienten veta att servern accepterar unicast-meddelanden direkt från klienten i stället för multicast. |

IATA, relä meddelande, autentisering och Server-unicast-alternativ stöds inte i den här versionen av NetX Duo DHCPv6 server. Den aktuella alternativ koden 10 för DHCPv6-protokollet lämnas odefinierad i RFC 3315.