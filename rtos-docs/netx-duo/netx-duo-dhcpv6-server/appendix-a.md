---
title: Bilaga A – Azure RTOS NetX Duo DHCPv6-alternativkoder
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo DHCPv6-alternativkoder
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 58b6e36fab4de02a9fb973894500a48f2656809ec2baa3dfc65fcd80ae33b832
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791847"
---
# <a name="appendix-a--azure-rtos-netx-duo-dhcpv6-option-codes"></a>Bilaga A – Azure RTOS NetX Duo DHCPv6-alternativkoder

| Alternativ              | Kod            | Description |
| ------------------- | ------------------- | --------------- |
| DUID för klientidentifierare | 1 | Identifierar unikt en klientvärd i nätverket |
| Serveridentifierare (DUID) | 2 | Identifierar unikt DHCPv6Server-värden i nätverket |
| Identity Association for Non Temporary Addresses (IANA) | 3 | Parametrar för en icke-tillfällig IP-adresstilldelning |
| Identity Association for Temporary Addresses (IATA) | 4 | Parametrar för en tillfällig IP-adresstilldelning |
| IA-adress | 5 | Faktisk IPv6-adress och IPv6-adresslivstid som ska tilldelas till klienten |
| Alternativbegäran | 6 | En lista med informationsförfrågningar om att hämta nätverksinformation, till exempel DNS-server och andra nätverkskonfigurationsparametrar. |
| Preferens | 7 | Ingår i servern Annonsera meddelande till klienten för att påverka klientens val av servrar. Klienten måste välja en server med högre inställningsvärde framför andra servrar. 255 är det högsta värdet, medan noll anger att klienten kan välja vilken server som helst som svarar tillbaka till dem |
| Förfluten tid | 8 | Innehåller tiden (i 0,01 sekunder) när klienten initierar DHCPv6-utbyte med servern. Används av sekundära servrar för att avgöra om den primära servern svarar i tid på klientbegäran. |
| Vidarebefordrande meddelande | 9 | Innehåller det ursprungliga meddelandet i Relay-meddelandet | 
| Autentisering | 11 | Innehåller information för att autentisera identiteten och innehållet i DHCPv6-meddelanden |
| Server Unicast | 12 | Servern skickar det här alternativet för att meddela klienten att servern accepterar unicast-meddelanden direkt från klienten i stället för multicast. |

IATA-, Relay Message-, Authentication- och Server Unicast-alternativ stöds inte i den här versionen av NetX Duo DHCPv6 Server. Den aktuella alternativkoden för DHCPv6-protokollet 10 är odefinierad i RFC 3315.