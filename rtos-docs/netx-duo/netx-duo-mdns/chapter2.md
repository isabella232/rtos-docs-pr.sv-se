---
title: Kapitel 2 – installation och användning av mDNS
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX Duo mDNS-modulen.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6f9e3d023f1bdbde4546a94da1bc1ccb48578d0e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825920"
---
# <a name="chapter-2---installation-and-use-of-mdns"></a>Kapitel 2 – installation och användning av mDNS

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX Duo mDNS-modulen.

## <a name="product-distribution"></a>Produkt distribution

NetX Duo mDNS finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nxd_mdns. h** Rubrik fil för NetX Duo mDNS-modulen
- **nxd_mdns. c** C-källfil för NetX Duo mDNS-modulen
- **nxd_mdns.pdf** PDF-Beskrivning av mDNS för NetX Duo
- **demo_netxduo_mdns. c** Ett enkelt demonstrations program som illustrerar de tjänster som tillhandahålls av mDNS.

## <a name="netx-duo-mdns-installation"></a>NetX Duo mDNS-installation

För att kunna använda NetX Duo-mDNS-API: erna, ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX Duo är installerat. Om t. ex. NetX Duo installeras i katalogen "*c:\netxduo*" måste *nxd_mdns. h* och *nxd_mdns. c* kopieras till den här katalogen.

## <a name="using-netx-duo-mdns"></a>Använda NetX Duo-mDNS

Det är enkelt att använda NetX Duo mDNS-modulen. I princip måste program koden innehålla *nxd_mdns. h* när den innehåller *tx_api. h och* *nx_api. h* för att kunna använda ThreadX respektive netx Duo. Build-projektet måste innehålla mDNS-källkoden och program filen, och naturligtvis ThreadX-och NetX-biblioteksfilerna. Detta är allt som krävs för att använda NetX Duo-mDNS.

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa NetX Duo mDNS-modulen. Standardvärdena visas i listan, men varje definition kan anges av programmet innan den angivna NetX Duo-mDNS huvud filen tas med. I följande lista beskrivs var och en i detalj:

- **NX_MDNS_DISABLE_SERVER** Inaktiverar Server funktionen mDNS/DNS-SD. Utan server funktionen kan mDNS/DNS-SD-modulen inte meddela tjänster som tillhandahålls av den lokala värden eller som inte svarar på mDNS förfrågningar. Den här symbolen är inte definierad som standard.
- **NX_MDNS_DISABLE_CLIENT** Inaktiverar klient funktionen mDNS/DNS-SD. Utan-klient funktionen skickar mDNS/DNS-SD inte frågor eller så upprätthåller den inte mDNS fråge svar som tas emot över nätverket.
- **NX_MDNS_ENABLE_ADDRESS_CHECK** Definierad utför mDNS-modulen verifierar adresser (käll adress, mål adress och port nummer) från de mottagna mDNS-meddelandena. Den här symbolen definieras som standard.
- **NX_MDNS_ENABLE_CLIENT_POOF** Definierad, mDNS-modulen utför passiv observation av felen, mDNS/DNS_SD-klienten (frågare) kontrollerar multicast-frågorna som utfärdats av de andra värdarna i nätverket. Den här symbolen definieras som standard.
- **NX_MDNS_ENABLE_SERVER_NEGATIVE_RESPONSES** Definierad, mDNS/DNS-SD-servern (Responder) genererar negativa svar på frågor som den har legitim ägande rätt till. Den här symbolen definieras som standard.
- **NX_MDNS_ENABLE_IPV6** Definierad, mDNS/DNS-SD Send/process mDNS-meddelandet över IPv6-adress. Den här symbolen är inte definierad som standard.
- **NX_MDNS_IPV6_ADDRESS_COUNT** Högsta antal IPv6-adresser för värden. Standardvärdet är 2.
- **NX_MDNS_HOST_NAME_MAX** Maximal sträng storlek för värd namn. Standardvärdet är 64. Inkluderar inte NULL-begränsaren.
- **NX_MDNS_SERVICE_NAME_MAX** Maximal sträng storlek för tjänst namn. Standardvärdet är 64. Inkluderar inte NULL-begränsaren.
- **NX_MDNS_DOMAIN_NAME_MAX** Maximal sträng storlek för domän namn. Standardvärdet är 16. Inkluderar inte NULL-begränsaren.
- **NX_MDNS_CONFLICT_COUNT** Maximalt antal konflikter för värdnamn eller tjänst namn. Standardvärdet är 8.
- **NX_MDNS_RR_TTL_HOST** TTL-värde för resurs poster med värdnamn, i sekund. Standardvärdet är 120 för 120S.
- **NX_MDNS_RR_TTL_OTHER** TTL-värde för andra resurs poster, i andra. Standardvärdet är 4500 i 75 minuter.
- **NX_MDNS_PROBING_TIMER_COUNT** Tidsintervallet, i Tick, mellan mDNS avsöknings meddelanden. Standardvärdet är 25 Tick för 250ms.
- **NX_MDNS_ANNOUNCING_TIMER_COUNT** Tidsintervallet, i Tick, mellan mDNS meddelande meddelanden. Standardvärdet är 25 Tick för 250ms.
- **NX_MDNS_GOODBYE_TIMER_COUNT** Tidsintervallet, i Tick, mellan upprepade meddelanden. Standardvärdet är 25 Tick för 250ms.
- **NX_MDNS_QUERY_MIN_TIMER_COUNT** Det minsta tidsintervallet, i Tick, mellan två frågor. Standardvärdet är 100-Tick i 1 sekund.
- **NX_MDNS_QUERY_MAX_TIMER_COUNT** Det maximala tidsintervallet, i Tick, mellan två frågor. Standardvärdet är 360000 i 60 sekunder.
- **NX_MDNS_QUERY_DELAY_MIN** Den minsta fördröjningen för att skicka första frågan i Tick. Standardvärdet är 2 Tick för 20ms.
- **NX_MDNS_QUERY_DELAY_RANGE** Fördröjnings intervallet för att skicka den första frågan i Tick. Standardvärdet är 10 Tick för 100 MS.
- **NX_MDNS_RESPONSE_INTERVAL** Tidsintervallet, i Ticket, i svar på en fråga för att se till att intervallet är minst 1 sedan den senaste gången posten var multicast. Standardvärdet är 100-Tick.
- **NX_MDNS_RESPONSE_PROBING_TIMER_OUT** Tidsintervallet, i Ticket, i svar på en avsöknings fråga för att se till att intervallet minst 250ms sedan posten var multicast. Standardvärdet är 25 Tick.
- **NX_MDNS_RESPONSE_UNIQUE_DELAY** Fördröjningen, i Tick, i svar på en fråga till en tjänst som är unik för det lokala nätverket. Standardvärdet är 1 Ticket för 10ms.
- **NX_MDNS_RESPONSE_SHARED_DELAY_MIN** Den minsta fördröjningen i Tick i som svarar på en fråga till en delad resurs. Standardvärdet är 2 Tick för 20ms.
- **NX_MDNS_RESPONSE_SHARED_DELAY_RANGE** Fördröjnings intervallet, i Tick, i svar på en fråga till en delad resurs. Standardvärdet är 10 Tick för 100 MS.
- **NX_MDNS_RESPONSE_TC_DELAY_MIN** Den minsta fördröjningen i Tick i som svarar på en fråga med TC-bit. Standardvärdet är 40-Tick för 400ms.
- **NX_MDNS_RESPONSE_TC_DELAY_RANGE** Fördröjnings intervallet, i Tick, i svar på en fråga med TC-bit. Standardvärdet är 10 Tick för 100 MS.
- **NX_MDNS_TIMER_COUNT_RANGE** När du skickar ut mDNS svar innehåller paketet svar som annars skulle skickas inom detta intervall för timer. Antalet timer-intervall uttrycks i Tick. Standardvärdet är 12 för 120ms. Med det här värdet kan ett svar innehålla meddelanden som skickas inom nästa 120ms-intervall om varje Tick är 10ms.
- **NX_MDNS_PROBING_RETRANSMIT_COUNT** Antalet överförda meddelanden. Standardvärdet är 3.
- **NX_MDNS_GOODBYE_RETRANSMIT_COUNT** Antalet meddelanden som skickas igen. Standardvärdet är 1.
- **NX_MDNS_POOF_MIN_COUNT** Antalet frågor som inget multicast-svar har, kan värden ta detta som en indikation på att posten inte längre är giltig. Standardvärdet är 2.
- **NX_MDNS_POOF_TIME_COUNT** Tidsintervallet, i Tick, i borttagning av posten från cachen efter att ha sett två eller flera av dessa frågor, och som inte ser något multicast-svar som innehåller det förväntade svaret. Standardvärdet är 1000-Tick i 10 sekunder.
- **NX_MDNS_RR_DELETE_DELAY_TIMER_COUNT** Fördröjningen för borttagning av en resurs post när TTL för den här posten är noll, i Tick, är standardvärdet 100 Tick för 1 sekund.
