---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo DHCP-server
description: I NetX Duo är programmets IP-adress en av de angivna parametrarna för *nx_ip_create* tjänst anropet.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 678b9ed77f07d0b526525c740f0fae7adc6d2c95
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826115"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcp-server"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo DHCP-server

I NetX Duo är programmets IP-adress en av de angivna parametrarna för *nx_ip_create* tjänst anropet. Att tillhandahålla IP-adressen innebär inget problem om IP-adressen är känd för programmet, antingen statiskt eller via användar konfiguration. Det finns dock vissa instanser där programmet inte känner till eller bryr sig om dess IP-adress. I sådana fall ska en noll IP-adress anges för funktionen *nx_ip_create* och programmet upprättar kommunikation med DHCP-servern för att dynamiskt begära och erhålla en IP-adress.

## <a name="dynamic-ip-address-assignment"></a>Dynamisk IP-adresstilldelning

Den grundläggande tjänsten som används för att hämta en dynamisk IP-adress från nätverket är RARP (reversed Address Resolution Protocol). Det här protokollet liknar ARP, förutom att det är utformat för att hämta en IP-adress för sig själv i stället för att hitta MAC-adressen för en annan nätverksmapp. Lågnivå-RARP-meddelandet skickas i det lokala nätverket och det är ansvaret för att en server i nätverket ska svara med ett RARP-svar som innehåller en dynamiskt tilldelad IP-adress.

Även om RARP tillhandahåller en tjänst för dynamisk allokering av IP-adresser, har den flera brister. De mest avbländnings bristen är att RARP endast tillhandahåller dynamisk tilldelning av IP-adressen. I de flesta situationer krävs mer information för att en enhet ska kunna delta i ett nätverk. Förutom en IP-adress behöver de flesta enheter nätverks masken och gatewayens IP-adress. IP-adressen för en DNS-server och annan nätverks information kan också behövas. RARP har inte möjlighet att ange den här informationen.

## <a name="rarp-alternatives"></a>RARP alternativ

För att kunna kringgå brister i RARP utvecklade forskare en mer omfattande mekanism för allokering av IP-adresser som kallas BOOTP (Bootstrap Protocol). Det här protokollet har möjlighet att dynamiskt allokera en IP-adress och även ange ytterligare viktig nätverks information. BOOTP har dock en nackdel med att utformas för statiska nätverkskonfigurationer. Den tillåter inte snabb eller automatisk adress tilldelning.

Det är här som Dynamic Host Configuration Protocol (DHCP) är mycket användbart. DHCP har utformats för att utöka de grundläggande funktionerna i BOOTP för att inkludera helt automatiserad allokering av IP-servrar och fullständig dynamisk IP-adressallokering genom att "leasa" en IP-adress till en klient under en angiven tids period. DHCP kan också konfigureras för att allokera IP-adresser på ett statiskt sätt som BOOTP.

## <a name="dhcp-messages"></a>DHCP-meddelanden

Även om DHCP avsevärt förbättrar funktionerna i BOOTP, använder DHCP samma meddelande format som BOOTP och stöder samma leverantörs alternativ som BOOTP. För att kunna utföra sin funktion introducerar DHCP sju nya DHCP-alternativ, enligt följande:

- IDENTIFIERA (1) (skickas av DHCP-klienten)
- ERBJUDANDE (2) (skickas av DHCP-server)
- BEGÄRAN (3) (skickas av DHCP-klienten)
- NEKA (4) (skickas av DHCP-klienten)
- ACK (5) (skickas av DHCP-server)
- NACK (6) (skickas av DHCP-server)
- VERSION (7) (skickas av DHCP-klienten)
- INFORMERA (8) (skickas av DHCP-klienten)
- FORCERENEW (9) (skickas av DHCP-klienten)

## <a name="dhcp-communication"></a>DHCP-kommunikation

DHCP-servern använder UDP-protokollet för att ta emot begär Anden om DHCP-klienter och överförings svar. Innan du använder en IP-adress skickas och tas UDP-meddelanden med DHCP-informationen genom att använda IP-broadcast-adressen 255.255.255.255. Men om klienten känner till adressen till DHCP-servern kan det skicka DHCP-meddelanden med unicast-meddelanden.

## <a name="dhcp-server-state-machine"></a>Status dator för DHCP-server

DHCP-servern implementeras som en dator med två steg som bearbetas av en intern DHCP-tråd som skapas under *nx_dhcp_server_create* bearbetning. Huvud tillstånden för DHCP-servern är 1) om du tar emot ett IDENTIFIERINGs meddelande från en DHCP-klient och 2) får du ett meddelande om begäran.

Nedan visas motsvarande DHCP-klient tillstånd:

- **NX_DHCP_STATE_BOOT** Börja med en tidigare IP-adress
- **NX_DHCP_STATE_INIT** Startar utan föregående IP-adress värde
- **NX_DHCP_STATE_SELECTING** Väntar på svar från valfri DHCP-server
- **NX_DHCP_STATE_REQUESTING** DHCP-server identifierad, begäran om IP-adress har skickats
- **NX_DHCP_STATE_BOUND** IP-adresslån upprättat för DHCP
- **NX_DHCP_STATE_RENEWING** Förnyelse tid för DHCP IP-adresslån har förflutit, förnyelse begärd
- **NX_DHCP_STATE_REBINDING** Förfluten tid för DHCP-IP-adresslån har förflutit, förnyelse begärd
- **NX_DHCP_STATE_FORCERENEW** DHCP IP-adresslån upprättat, framtvinga förnyelse av Server eller program
- **NX_DHCP_STATE_FAILED** Ingen server hittades eller inget svar från servern togs emot

## <a name="dhcp-additional-parameters"></a>Ytterligare DHCP-parametrar

NetX Duo DHCP-servern har en standard lista med alternativ parametrar som anges i det konfigurerbara alternativet NX_DHCP_DEFAULT_SERVER_OPTION_LIST i *nxd_dhcp_server. h* för att tillhandahålla DHCP-klienter med gemensamma/kritiska nätverks konfigurations parametrar, t. ex. router eller Gateway-adress och DNS-server för DHCP-klienten.

## <a name="dhcp-rfcs"></a>DHCP-rapporter

NetX Duo DHCP-servern är kompatibel med RFC2132, RFC2131 och relaterade RFC: er.
