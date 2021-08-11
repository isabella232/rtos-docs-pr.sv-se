---
title: Kapitel 1 – Introduktion till att Azure RTOS NetX Duo DHCP-server
description: I NetX Duo är programmets IP-adress en av de angivna parametrarna för *nx_ip_create* tjänstanropet.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a56f692059cbd3e2a72d64cf80ee90a917b80987add8130d3a1df70b3b0c3a71
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788481"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcp-server"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo DHCP-server

I NetX Duo är programmets IP-adress en av de angivna parametrarna för *nx_ip_create* tjänstanropet. Att ange IP-adressen utgör inget problem om IP-adressen är känd för programmet, antingen statiskt eller via användarkonfiguration. Det finns dock vissa instanser där programmet inte vet eller bryr sig om vad dess IP-adress är. I sådana situationer ska en NOLL IP-adress *anges till nx_ip_create-funktionen* och programmet upprättar kommunikation med dhcp-servern för att dynamiskt begära och hämta en IP-adress.

## <a name="dynamic-ip-address-assignment"></a>Dynamisk IP-adresstilldelning

Den grundläggande tjänst som används för att hämta en dynamisk IP-adress från nätverket är REVERSE Address Resolution Protocol (RARP). Det här protokollet liknar ARP, förutom att det är utformat för att hämta en EGEN IP-adress i stället för att hitta MAC-adressen för en annan nätverksnod. RARP-meddelandet på låg nivå skickas i det lokala nätverket och det är en servers ansvar att svara med ett RARP-svar, som innehåller en dynamiskt allokerad IP-adress.

Även om RARP tillhandahåller en tjänst för dynamisk allokering av IP-adresser har den flera brister. Den mest uppenbara bristen är att RARP endast tillhandahåller dynamisk allokering av IP-adressen. I de flesta fall krävs mer information för att en enhet ska kunna delta korrekt i ett nätverk. Förutom en IP-adress behöver de flesta enheter nätverksmasken och gatewayens IP-adress. IP-adressen för en DNS-server och annan nätverksinformation kan också behövas. RARP har inte möjlighet att tillhandahålla den här informationen.

## <a name="rarp-alternatives"></a>RARP-alternativ

För att lösa problemen med RARP utvecklade forskare en mer omfattande mekanism för IP-adressallokering som kallas Bootstrap Protocol (BOOTP). Det här protokollet har möjlighet att dynamiskt allokera en IP-adress och även tillhandahålla ytterligare viktig nätverksinformation. BootP har dock nackdelen med att utformas för statiska nätverkskonfigurationer. Det tillåter inte snabb eller automatiserad adresstilldelning.

Det är här som Dynamic Host Configuration Protocol (DHCP) är mycket användbart. DHCP är utformat för att utöka de grundläggande funktionerna i BOOTP så att den omfattar helt automatiserad IP-serverallokering och helt dynamisk IP-adressallokering genom "leasing" av en IP-adress till en klient under en angiven tidsperiod. DHCP kan också konfigureras för att allokera IP-adresser på ett statiskt sätt, till exempel BOOTP.

## <a name="dhcp-messages"></a>DHCP-meddelanden

Även om DHCP förbättrar funktionerna i BOOTP kraftigt, använder DHCP samma meddelandeformat som BOOTP och stöder samma leverantörsalternativ som BOOTP. För att kunna utföra sin funktion introducerar DHCP sju nya DHCP-specifika alternativ, enligt följande:

- DISCOVER (1) (skickas av DHCP-klienten)
- ERBJUDANDE (2) (skickas av DHCP-server)
- BEGÄRAN (3) (skickas av DHCP-klienten)
- NEKA (4) (skickas av DHCP-klienten)
- ACK (5) (skickas av DHCP-server)
- DHCP (6) (skickas av DHCP-server)
- VERSION (7) (skickas av DHCP-klienten)
- INFORM (8) (skickas av DHCP-klienten)
- FORCERENEW (9) (skickas av DHCP-klienten)

## <a name="dhcp-communication"></a>DHCP-kommunikation

DHCP-servern använder UDP-protokollet för att ta emot DHCP-klientbegäranden och skicka svar. Innan du har en IP-adress skickas och tas UDP-meddelanden som innehåller DHCP-informationen emot genom att använda IP-sändningsadressen 255.255.255.255. Men om klienten känner till adressen till DHCP-servern kan den skicka DHCP-meddelanden med hjälp av unicast-meddelanden.

## <a name="dhcp-server-state-machine"></a>DHCP-servertillståndsdator

DHCP-servern implementeras som en dator med två stegs tillstånd som bearbetas av en intern DHCP-tråd som skapas *under nx_dhcp_server_create* bearbetning. De huvudsakliga tillstånden för DHCP-servern är 1) tar emot ett DISCOVER-meddelande från en DHCP-klient och 2) tar emot ett REQUEST-meddelande.

Nedan visas motsvarande DHCP-klient tillstånd:

- **NX_DHCP_STATE_BOOT** Börja med en tidigare IP-adress
- **NX_DHCP_STATE_INIT** Från och med inget tidigare IP-adressvärde
- **NX_DHCP_STATE_SELECTING** Väntar på svar från en DHCP-server
- **NX_DHCP_STATE_REQUESTING** DHCP-server identifierad, IP-adressbegäran skickas
- **NX_DHCP_STATE_BOUND** DHCP IP-adresslånet har upprättats
- **NX_DHCP_STATE_RENEWING** Förnyelsetid för DHCP IP-adresslån har förflutit, begärd förnyelse
- **NX_DHCP_STATE_REBINDING** Ombindningstid för DHCP IP-adresslån förfluten, begärd förnyelse
- **NX_DHCP_STATE_FORCERENEW** DHCP IP-adresslånet upprättas, framtrollsförnyelse per server eller program
- **NX_DHCP_STATE_FAILED** Ingen server hittades eller inget svar från den mottagna servern

## <a name="dhcp-additional-parameters"></a>Ytterligare DHCP-parametrar

NetX Duo DHCP-servern har en standardlista med alternativparametrar som anges i det konfigurerbara alternativet NX_DHCP_DEFAULT_SERVER_OPTION_LIST i *nxd_dhcp_server.h för* att förse DHCP-klienter med vanliga/kritiska nätverkskonfigurationsparametrar, t.ex. router- eller gatewayadress och DNS-server för DHCP-klienten.

## <a name="dhcp-rfcs"></a>DHCP-RFC

NetX Duo DHCP-servern är kompatibel med RFC2132, RFC2131 och relaterade RFC: er.
