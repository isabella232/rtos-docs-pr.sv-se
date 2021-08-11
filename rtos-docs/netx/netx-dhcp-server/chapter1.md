---
title: Kapitel 1 – Introduktion till Azure RTOS NetX DHCP-server
description: Programmet upprättar kommunikation med sin Azure RTOS NetX DHCP-server för att dynamiskt begära och hämta en IP-adress.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f7a286118caf9bca9876d40ecdd176a3f4cb711e9cba39325808bfb6c09c2644
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799565"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-dhcp-server"></a>Kapitel 1 – Introduktion till Azure RTOS NetX DHCP-server

I NetX är programmets IP-adress en av  de angivna parametrarna för nx_ip_create tjänstanropet. Att ange IP-adressen utgör inget problem om IP-adressen är känd för programmet, antingen statiskt eller via användarkonfiguration. Det finns dock vissa instanser där programmet inte vet eller bryr sig om vad dess IP-adress är. I sådana situationer ska en noll-IP-adress tillhandahållas *till nx_ip_create-funktionen* och programmet upprättar kommunikation med sin Azure RTOS NetX DHCP-server för att dynamiskt begära och hämta en IP-adress.

## <a name="dynamic-ip-address-assignment"></a>Dynamisk IP-adresstilldelning

Den grundläggande tjänst som används för att hämta en dynamisk IP-adress från nätverket är REVERSE Address Resolution Protocol (RARP). Det här protokollet liknar ARP, förutom att det är utformat för att hämta en egen IP-adress i stället för att hitta MAC-adressen för en annan nätverksnod. RARP-meddelandet på låg nivå skickas i det lokala nätverket och det är serverns ansvar att svara med ett RARP-svar som innehåller en dynamiskt allokerad IP-adress.

Även om RARP är en tjänst för dynamisk allokering av IP-adresser, finns det flera brister. Det mest motständliga är att RARP endast tillhandahåller dynamisk allokering av IP-adressen. I de flesta fall krävs mer information för att en enhet ska kunna delta korrekt i ett nätverk. Förutom en IP-adress behöver de flesta enheter nätverksmasken och gatewayens IP-adress. IP-adressen för en DNS-server och annan nätverksinformation kan också behövas. RARP kan inte tillhandahålla den här informationen.

## <a name="rarp-alternatives"></a>RARP-alternativ

För att lösa problemen med RARP utvecklade forskare en mer omfattande allokeringsmekanism för IP-adresser som kallas Bootstrap Protocol (BOOTP). Det här protokollet har möjlighet att dynamiskt allokera en IP-adress och även tillhandahålla ytterligare viktig nätverksinformation. BOOTP har dock nackdelen med att utformas för statiska nätverkskonfigurationer. Det tillåter inte snabb eller automatiserad adresstilldelning.

Det är här Dynamic Host Configuration Protocol (DHCP) är mycket användbart. DHCP är utformat för att utöka de grundläggande funktionerna i BOOTP till att omfatta helt automatiserad IP-serverallokering och helt dynamisk IP-adressallokering genom "leasing" en IP-adress till en klient under en angiven tidsperiod. DHCP kan också konfigureras för att allokera IP-adresser på ett statiskt sätt, till exempel BOOTP.

## <a name="dhcp-messages"></a>DHCP-meddelanden

Även om DHCP förbättrar funktionerna i BOOTP kraftigt, använder DHCP samma meddelandeformat som BOOTP och stöder samma leverantörsalternativ som BOOTP. För att kunna utföra sin funktion introducerar DHCP sju nya DHCP-specifika alternativ, enligt följande:

| Alternativ     | Värde | Ursprung                |
| ---------- | ----- | --------------------- |
| Upptäck   | (1)   | (skickas av DHCP-klienten) |
| Erbjuder      | (2)   | (skickas av DHCP-server) |
| Begäran    | (3)   | (skickas av DHCP-klienten) |
| Nedgång    | (4)   | (skickas av DHCP-klienten) |
| ACK        | (5)   | (skickas av DHCP-server) |
| Nack       | (6)   | (skickas av DHCP-server) |
| Släppa    | (7)   | (skickas av DHCP-klienten) |
| Informera     | (8)   | (skickas av DHCP-klienten) |
| FORCERENEW | (9)   | (skickas av DHCP-klienten) |

## <a name="dhcp-communication"></a>DHCP-kommunikation

DHCP-servern använder UDP-protokollet för att ta emot DHCP-klientbegäranden och skicka svar. Innan du har en IP-adress skickas och tas UDP-meddelanden som innehåller DHCP-informationen emot genom att använda IP-sändningsadressen 255.255.255.255. Men om klienten känner till adressen till DHCP-servern kan den skicka DHCP-meddelanden med hjälp av unicast-meddelanden.

## <a name="dhcp-server-state-machine"></a>DHCP-servertillståndsdator

DHCP-servern implementeras som en dator med tvåstegstillstånd som bearbetas av en intern DHCP-tråd som skapas *under nx_dhcp_server_create* bearbetning. Huvud tillstånden för DHCP-servern är 1) tar emot ett DISCOVER-meddelande från en DHCP-klient och 2) tar emot ett BEGÄRANdemeddelande.

Nedan visas motsvarande DHCP-klient tillstånd:

- **NX_DHCP_STATE_BOOT:** Börjar med en tidigare IP-adress
- **NX_DHCP_STATE_INIT:** Startar utan tidigare IP-adressvärde
- **NX_DHCP_STATE_SELECTING:** Väntar på svar från en DHCP-server
- **NX_DHCP_STATE_REQUESTING:** DHCP-server identifierad, IP-adressbegäran skickas
- **NX_DHCP_STATE_BOUND:** DHCP IP-adresslån upprättas
- **NX_DHCP_STATE_RENEWING:** Förnyelsetiden för DHCP IP-adresslån förfluten, begärd förnyelse
- **NX_DHCP_STATE_REBINDING:** Ombindningstid för DHCP IP-adresslån förfluten, begärd förnyelse
- **NX_DHCP_STATE_FORCERENEW:** DHCP IP-adresslånet upprättas, framtrollsförnyelse av server eller program
- **NX_DHCP_STATE_FAILED:** Ingen server hittades eller inget svar från den mottagna servern

## <a name="dhcp-additional-parameters"></a>DHCP-ytterligare parametrar

NetX DHCP-servern har en standardlista med alternativparametrar som anges i det konfigurerbara alternativet NX_DHCP_DEFAULT_SERVER_OPTION_LISTin *nx_dhcp_server.h* för att förse DHCP-klienter med vanliga/kritiska nätverkskonfigurationsparametrar, t.ex. router- eller gatewayadress och DNS-server för DHCP-klienten.

## <a name="dhcp-rfcs"></a>DHCP-RFC

NetX DHCP-servern är kompatibel med RFC2132, RFC2131 och relaterade RFC: er.
