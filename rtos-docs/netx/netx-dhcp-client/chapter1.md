---
title: Kapitel 1 – Introduktion till att Azure RTOS NetX DHCP-klient
description: I NetX är programmets IP-adress en av de angivna parametrarna för nx_ip_create tjänstanropet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 54853fd3677b8d60b7fbe1445ca67c7e7a4a6e832683f65cbfca86158cb7fbd3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788820"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-dhcp-client"></a>Kapitel 1 – Introduktion till att Azure RTOS NetX DHCP-klient

I NetX är programmets IP-adress en av  de angivna parametrarna för nx_ip_create tjänstanropet. Att ange IP-adressen innebär inga problem om IP-adressen är känd för programmet, antingen statiskt eller via användarkonfiguration. Det finns dock vissa instanser där programmet inte vet eller bryr sig om vad dess IP-adress är. I sådana situationer ska en noll-IP-adress *tillhandahållas till nx_ip_create-funktionen* och Azure RTOS DHCP-klientprotokollet ska användas för att dynamiskt hämta en IP-adress.

## <a name="dynamic-ip-address-assignment"></a>Dynamisk IP-adresstilldelning

Den grundläggande tjänst som används för att hämta en dynamisk IP-adress från nätverket är REVERSE Address Resolution Protocol (RARP). Det här protokollet liknar ARP, förutom att det är utformat för att hämta en egen IP-adress i stället för att hitta MAC-adressen för en annan nätverksnod. RARP-meddelandet på låg nivå skickas i det lokala nätverket och det är serverns ansvar att svara med ett RARP-svar som innehåller en dynamiskt allokerad IP-adress.

Även om RARP är en tjänst för dynamisk allokering av IP-adresser, finns det flera brister. Det mest motständliga är att RARP endast tillhandahåller dynamisk allokering av IP-adressen. I de flesta fall krävs mer information för att en enhet ska kunna delta korrekt i ett nätverk. Förutom en IP-adress behöver de flesta enheter nätverksmasken och gatewayens IP-adress. IP-adressen för en DNS-server och annan nätverksinformation kan också behövas. RARP kan inte tillhandahålla den här informationen.

## <a name="rarp-alternatives"></a>RARP-alternativ

För att lösa problemen med RARP utvecklade forskare en mer omfattande allokeringsmekanism för IP-adresser som kallas Bootstrap Protocol (BOOTP). Det här protokollet har möjlighet att dynamiskt allokera en IP-adress och även tillhandahålla ytterligare viktig nätverksinformation. BOOTP har dock nackdelen med att utformas för statiska nätverkskonfigurationer. Det tillåter inte snabb eller automatiserad adresstilldelning.

Det är här som Dynamic Host Configuration Protocol (DHCP) är mycket användbart. DHCP är utformat för att utöka de grundläggande funktionerna i BOOTP till att omfatta helt automatiserad IP-serverallokering och helt dynamisk IP-adressallokering genom att "leasa" en IP-adress till en klient under en angiven tidsperiod. DHCP kan också konfigureras för att allokera IP-adresser på ett statiskt sätt, till exempel BOOTP.

## <a name="dhcp-messages"></a>DHCP-meddelanden

Även om DHCP förbättrar funktionerna i BOOTP kraftigt, använder DHCP samma meddelandeformat som BOOTP och stöder samma leverantörsalternativ som BOOTP. För att kunna utföra sin funktion introducerar DHCP sju nya DHCP-specifika alternativ, enligt följande:

- DISCOVER (1) (skickas av DHCP-klienten)

- ERBJUDANDE (2) (skickas av DHCP-server)

- BEGÄRAN (3) (skickas av DHCP-klienten)

- NEKA (4) (skickas av DHCP-klient)

- ACK (5) (skickas av DHCP-server)

- DHCP (6) (skickas av DHCP-server)

- VERSION (7) (skickas av DHCP-klienten)

- INFORM (8) (skickas av DHCP-klienten)

- FORCERENEW (9) (skickas av DHCP-klienten)

## <a name="dhcp-communication"></a>DHCP-kommunikation

DHCP använder UDP-protokollet för att skicka begäranden och fältsvar. Innan du har en IP-adress skickas och tas UDP-meddelanden som innehåller DHCP-informationen emot genom att använda IP-sändningsadressen 255.255.255.255.

## <a name="dhcp-client-state-machine"></a>DHCP-klienttillståndsdator

DHCP-klienten implementeras som en tillståndsdator. Tillståndsdatorn bearbetas av en intern DHCP-tråd som skapas under *nx_dhcp_create* bearbetning. De viktigaste tillstånden för DHCP-klienten är följande:


- **NX_DHCP_STATE_BOOT** Börja med en tidigare IP-adress

- **NX_DHCP_STATE_INIT** Från och med inget tidigare IP-adressvärde

- **NX_DHCP_STATE_SELECTING** Väntar på svar från en DHCP-server

- **NX_DHCP_STATE_REQUESTING** IDENTIFIERAD DHCP-server, IP-adressbegäran skickades

- **NX_DHCP_STATE_BOUND** DHCP IP-adresslånet har upprättats

- **NX_DHCP_STATE_RENEWING** Förnyelsetid för DHCP IP-adresslån förfluten, begärd förnyelse

- **NX_DHCP_STATE_REBINDING** Förfluten tid för DHCP IP-adresslån, begärd förnyelse

- **NX_DHCP_STATE_FORCERENEW** DHCP IP-adresslån upprättas, framt tvingar förnyelse av server (stöds inte för närvarande) eller av programmet som anropar nx_dhcp_force_renew

- **NX_DHCP_STATE_ADDRESS_PROBING** DHCP IP-adressavsökning, skicka ARP-avsökningen för att identifiera IP-adresskonflikt.

## <a name="dhcp-client-multiple-interface-support"></a>Stöd för DHCP-klienten med flera gränssnitt

DHCP-klienten implementerades tidigare för att endast köras på ett enda nätverksgränssnitt. Standardbeteendet var (och är fortfarande) att DHCP-klienten skulle köras i det primära gränssnittet. Genom att *nx_dhcp_set_interface_index* kan programmet (och kan fortfarande) köra DHCP i ett sekundärt nätverksgränssnitt i stället för det primära gränssnittet.

Det stöder nu DHCP som körs på flera gränssnitt parallellt. Mer **information om hur du kör DHCP-klienten på** fler än ett fysiskt gränssnitt samtidigt finns i DHCP-klienten på flera gränssnitt samtidigt i kapitel två.

## <a name="dhcp-user-request"></a>DHCP-användarbegäran

När DHCP-servern ger en IP-adress kan DHCP-klientbearbetningen begära ytterligare parametrar – en i taget – med hjälp *nx_dhcp_user_option_request* tjänsten.

## <a name="dhcp-client-socket-queue"></a>DHCP-klientsocketkö 

DHCP-klienten rensar automatiskt broadcast-paket från DHCP-servrar som är avsedda för andra DHCP-klienter från dess socket-mottagningskö medan den väntar på att servern ska svara på sig själv. Om du inte gör det i ett upptaget nätverk kan paket som är avsedda för klienten tas bort.

## <a name="dhcp-rfcs"></a>DHCP-RFC

NetX DHCP är kompatibelt med RFC2132, RFC2131 och relaterade RFC: er.

