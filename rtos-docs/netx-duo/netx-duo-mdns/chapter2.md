---
title: Kapitel 2 – Installation och användning av mDNS
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av NetX Duo mDNS-modulen.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b27671f82c100db4e6a70a568e8a68f14b3ab45e3a33f46dd1f2e1852010f500
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796437"
---
# <a name="chapter-2---installation-and-use-of-mdns"></a>Kapitel 2 – Installation och användning av mDNS

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av NetX Duo mDNS-modulen.

## <a name="product-distribution"></a>Produktdistribution

NetX Duo mDNS finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nxd_mdns.h** Huvudfil för NetX Duo mDNS-modul
- **nxd_mdns.c** C-källfil för NetX Duo mDNS-modul
- **nxd_mdns.pdf** PDF-beskrivning av mDNS för NetX Duo
- **demo_netxduo_mdns.c** Ett enkelt demonstrationsprogram som illustrerar de tjänster som tillhandahålls av mDNS.

## <a name="netx-duo-mdns-installation"></a>NetX Duo mDNS Installation

För att kunna använda NetX Duo mDNS API:er bör hela distributionen som nämns ovan kopieras till samma katalog där NetX Duo är installerat. Om NetX Duo till exempel är installerat i katalogen *" c:\netxduo*" ska *nxd_mdns.h* *och nxd_mdns.c* kopieras till den här katalogen.

## <a name="using-netx-duo-mdns"></a>Använda NetX Duo mDNS

Det är enkelt att använda NetX Duo mDNS-modulen. I princip måste programkoden innehålla *nxd_mdns.h* efter att den *innehåller tx_api.h* och *nx_api.h* för att kunna använda ThreadX respektive NetX Duo. Byggprojektet måste innehålla mDNS-källkoden och programfilen, och naturligtvis biblioteksfilerna ThreadX och NetX. Det här är allt som krävs för att använda NetX Duo mDNS.

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ för att skapa NetX Duo mDNS-modulen. Standardvärdena visas, men varje definition kan anges av programmet innan den angivna NetX Duo mDNS-huvudfilen tas med. I följande lista beskrivs var och en i detalj:

- **NX_MDNS_DISABLE_SERVER** Inaktiverar funktionen för mDNS/DNS-SD-servern. Utan serverfunktionen meddelar inte mDNS/DNS-SD-modulen tjänster som tillhandahålls av den lokala värden, och svarar inte heller på mDNS-härdning. Den här symbolen definieras inte som standard.
- **NX_MDNS_DISABLE_CLIENT** Inaktiverar mDNS/DNS-SD-klientfunktionen. Utan klientfunktionen skickar mDNS/DNS-SD inte några frågor, och den underhåller inte heller mDNS-frågesvar som tas emot via nätverket.
- **NX_MDNS_ENABLE_ADDRESS_CHECK** MDNS-modulen har definierats och verifierar adresser (källadress, måladress och portnummer) från de mottagna mDNS-meddelandena. Den här symbolen definieras som standard.
- **NX_MDNS_ENABLE_CLIENT_POOF** MDNS-modulen har definierats för att utföra passiv observation av fel, mDNS /DNS_SD-klienten (querier) observerar de multicast-frågor som utfärdas av de andra värdarna i nätverket. Den här symbolen definieras som standard.
- **NX_MDNS_ENABLE_SERVER_NEGATIVE_RESPONSES** Definierad genererar mDNS /DNS-SD-servern (svarare) negativa svar på frågor som den har legitimt ägarskap för. Den här symbolen definieras som standard.
- **NX_MDNS_ENABLE_IPV6** MDNS-/DNS-SD-meddelandet för att skicka/bearbeta mDNS över IPv6-adress har definierats. Den här symbolen definieras inte som standard.
- **NX_MDNS_IPV6_ADDRESS_COUNT** Maximalt antal IPv6-adresser för värden. Standardvärdet är 2.
- **NX_MDNS_HOST_NAME_MAX** Maximal strängstorlek för värdnamn. Standardvärdet är 64. Innehåller inte NULL-terminatorn.
- **NX_MDNS_SERVICE_NAME_MAX** Maximal strängstorlek för tjänstens namn. Standardvärdet är 64. Innehåller inte NULL-terminatorn.
- **NX_MDNS_DOMAIN_NAME_MAX** Maximal strängstorlek för domännamn. Standardvärdet är 16. Innehåller inte NULL-terminatorn.
- **NX_MDNS_CONFLICT_COUNT** Maximalt antal konflikter för värdnamn eller tjänstnamn. Standardvärdet är 8.
- **NX_MDNS_RR_TTL_HOST** TTL-värde för resursposter med värdnamn, i sekunden. Standardvärdet är 120 för 120-tal.
- **NX_MDNS_RR_TTL_OTHER** TTL-värde för andra resursposter, i sekunden. Standardvärdet är 4 500 i 75 minuter.
- **NX_MDNS_PROBING_TIMER_COUNT** Tidsintervallet i tick mellan mDNS-avsökningsmeddelanden. Standardvärdet är 25 tick för 250 ms.
- **NX_MDNS_ANNOUNCING_TIMER_COUNT** Tidsintervallet, i tick, mellan mDNS-meddelanden. Standardvärdet är 25 tick för 250 ms.
- **NX_MDNS_GOODBYE_TIMER_COUNT** Tidsintervallet, i tick, mellan upprepade "goodbye"-meddelanden. Standardvärdet är 25 tick för 250 ms.
- **NX_MDNS_QUERY_MIN_TIMER_COUNT** Det minsta tidsintervallet, i tick, mellan två frågor. Standardvärdet är 100 tick i 1 sekund.
- **NX_MDNS_QUERY_MAX_TIMER_COUNT** Det maximala tidsintervallet i tick mellan två frågor. Standardvärdet är 360000 i 60 sekunder.
- **NX_MDNS_QUERY_DELAY_MIN** Den minsta fördröjningen för att skicka den första frågan i tick. Standardvärdet är 2 tick för 20 ms.
- **NX_MDNS_QUERY_DELAY_RANGE** Fördröjningsintervallet för att skicka den första frågan i tick. Standardvärdet är 10 tick för 100 ms.
- **NX_MDNS_RESPONSE_INTERVAL** Tidsintervallet, i tick, i svarar på en fråga för att säkerställa ett intervall på minst 1:e sedan den senaste gången posten multicast. Standardvärdet är 100 tick.
- **NX_MDNS_RESPONSE_PROBING_TIMER_OUT** Tidsintervallet i tick i svarar på en avsökningsfråga för att säkerställa ett intervall på minst 250 ms sedan den senaste gången posten multicast.. Standardvärdet är 25 tick.
- **NX_MDNS_RESPONSE_UNIQUE_DELAY** Fördröjningen, i tick, i svarar på en fråga till en tjänst som är unik för det lokala nätverket. Standardvärdet är 1 tick för 10 ms.
- **NX_MDNS_RESPONSE_SHARED_DELAY_MIN** Den minsta fördröjningen i tick i svarar på en fråga till en delad resurs. Standardvärdet är 2 tick för 20 ms.
- **NX_MDNS_RESPONSE_SHARED_DELAY_RANGE** Fördröjningsintervallet, i tick, i svarar på en fråga till en delad resurs. Standardvärdet är 10 tick för 100 ms.
- **NX_MDNS_RESPONSE_TC_DELAY_MIN** Den minsta fördröjningen, i tick, i att svara på en fråga med TC-bit. Standardvärdet är 40 tick för 400 ms.
- **NX_MDNS_RESPONSE_TC_DELAY_RANGE** Fördröjningsintervallet, i tick, i svarar på en fråga med TC-bit. Standardvärdet är 10 tick för 100 ms.
- **NX_MDNS_TIMER_COUNT_RANGE** När du skickar ut mDNS-svar innehåller paketet svar som annars skulle skickas inom det här timerräknarintervallet. Timerantalsintervallet uttrycks i tick. Standardvärdet är 12 för 120 ms. Med det här värdet kan ett svar inkludera meddelanden som skickas inom nästa 120 ms-intervall om varje tick är 10 ms.
- **NX_MDNS_PROBING_RETRANSMIT_COUNT** Antalet återskickade avsökningsmeddelanden. Standardvärdet är 3.
- **NX_MDNS_GOODBYE_RETRANSMIT_COUNT** Antalet återskickade "goodbye"-meddelanden. Standardvärdet är 1.
- **NX_MDNS_POOF_MIN_COUNT** Antalet frågor som inte ger multicast-svar kan vara en indikation på att posten kanske inte längre är giltig. Standardvärdet är 2.
- **NX_MDNS_POOF_TIME_COUNT** Tidsintervallet, i tick, för att ta bort posten från cacheminnet efter att ha sett två eller flera av dessa frågor, och ser inget multicast-svar som innehåller det förväntade svaret. Standardvärdet är 1 000 tick i 10 sekunder.
- **NX_MDNS_RR_DELETE_DELAY_TIMER_COUNT** Fördröjningen för att ta bort en resurspost när TTL för den här posten är noll, i tick, är standardvärdet 100 tick i 1 sekund.
