---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo DHCP-klienten
description: I Azure återställnings tider NetX Duo DHCP-klienten är programmets IP-adress en av de angivna parametrarna för *nx_ip_create* tjänst anropet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f5b2f2ef7b440e2f2ee8aa6a9bd6ed199eaf13fb
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826136"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-dhcp-client"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo DHCP-klienten

I Azure återställnings tider NetX Duo DHCP-klienten är programmets IP-adress en av de angivna parametrarna för *nx_ip_create* tjänst anropet. Att tillhandahålla IP-adressen innebär inget problem om IP-adressen är känd för programmet, antingen statiskt eller via användar konfiguration. Det finns dock vissa instanser där programmet inte känner till eller bryr sig om dess IP-adress. I sådana fall ska en noll IP-adress anges till *nx_ip_create* -funktionen och DHCP-klient protokollet ska användas för att dynamiskt erhålla en IP-adress.

## <a name="dynamic-ip-address-assignment"></a>Dynamisk IP-adresstilldelning

Den grundläggande tjänsten som används för att hämta en dynamisk IP-adress från nätverket är RARP (reversed Address Resolution Protocol). Det här protokollet liknar ARP, förutom att det är utformat för att hämta en IP-adress för sig själv i stället för att hitta MAC-adressen för en annan nätverksmapp. Lågnivå-RARP-meddelandet skickas i det lokala nätverket och det är ansvaret för att en server i nätverket ska svara med ett RARP-svar som innehåller en dynamiskt tilldelad IP-adress.

Även om RARP tillhandahåller en tjänst för dynamisk allokering av IP-adresser, har den flera brister. De mest avbländnings bristen är att RARP endast tillhandahåller dynamisk tilldelning av IP-adressen. I de flesta situationer krävs mer information för att en enhet ska kunna delta i ett nätverk. Förutom en IP-adress behöver de flesta enheter nätverks masken och gatewayens IP-adress. IP-adressen för en DNS-server och annan nätverks information kan också behövas. RARP har inte möjlighet att ange den här informationen.

## <a name="rarp-alternatives"></a>RARP alternativ

För att kunna kringgå brister i RARP utvecklade forskare en mer omfattande mekanism för allokering av IP-adresser som kallas BOOTP (Boot remmar Protocol). Det här protokollet har möjlighet att dynamiskt allokera en IP-adress och även ange ytterligare viktig nätverks information. BOOTP har dock en nackdel med att utformas för statiska nätverkskonfigurationer. Den tillåter inte snabb eller automatisk adress tilldelning.

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

DHCP använder UDP-protokollet för att skicka begär Anden och fält svar. Innan du använder en IP-adress skickas och tas UDP-meddelanden med DHCP-informationen genom att använda IP-broadcast-adressen 255.255.255.255.

## <a name="dhcp-client-state-machine"></a>Klient tillstånds dator för DHCP

DHCP-klienten implementeras som en tillstånds dator. Tillstånds datorn bearbetas av en intern DHCP-tråd som skapas under *nx_dhcp_create* bearbetning. Huvud tillstånden för DHCP-klienten är följande:

- **NX_DHCP_STATE_BOOT** Börja med en tidigare IP-adress
- **NX_DHCP_STATE_INIT** Startar utan föregående IP-adress värde
- **NX_DHCP_STATE_SELECTING** Väntar på svar från valfri DHCP-server
- **NX_DHCP_STATE_REQUESTING** DHCP-server identifierad, begäran om IP-adress har skickats
- **NX_DHCP_STATE_BOUND** IP-adresslån upprättat för DHCP
- **NX_DHCP_STATE_RENEWING** Förnyelse tid för DHCP IP-adresslån har förflutit, förnyelse begärd
- **NX_DHCP_STATE_REBINDING** Förfluten tid för DHCP-IP-adresslån har förflutit, förnyelse begärd
- **NX_DHCP_STATE_FORCERENEW** DHCP IP-adresslån upprättat, framtvinga förnyelse av Server (stöds inte för närvarande) eller av programmet som anropar nx_dhcp_force_renew
- **NX_DHCP_STATE_ADDRESS_PROBING** DHCP IP Address probing, skicka ARP-avsökningen för att identifiera IP-adresskonflikt.

## <a name="dhcp-client-multiple-interface-support"></a>Stöd för flera gränssnitt för DHCP-klienter

DHCP-klienten har tidigare implementerats för att köras endast på ett enda nätverks gränssnitt. Standard beteendet var (och fortfarande) för DHCP-klienten att köras på det primära gränssnittet. Genom att anropa *nx_dhcp_set_interface_index* kan programmet (och fortfarande köra) köra DHCP på ett sekundärt nätverks gränssnitt i stället för det primära gränssnittet.

Det stöder nu DHCP som körs på flera gränssnitt parallellt. Se **DHCP-klienten på flera gränssnitt samtidigt** i kapitel två för detaljerad information om hur du kör DHCP-klienten på fler än ett fysiskt gränssnitt samtidigt.

## <a name="dhcp-user-request"></a>Begäran om DHCP-användare

När DHCP-servern tilldelar en IP-adress kan DHCP-klienten begära ytterligare parametrar, en i taget, med hjälp av tjänsten *nx_dhcp_user_option_request* .

## <a name="dhcp-client-socket-queue"></a>DHCP-klientens socket-kö 

DHCP-klienten rensar automatiskt broadcast-paket från DHPC-servrar som är avsedda för andra DHCP-klienter från socket Receive-kön och väntar på att servern ska svara på sig själv. I ett upptaget nätverk kan det hända att paket som är avsedda för klienten släpps.

## <a name="dhcp-rfcs"></a>DHCP-rapporter

NetX Duo DHCP-klienten är kompatibel med RFC2132, RFC2131 och relaterade RFC: er.