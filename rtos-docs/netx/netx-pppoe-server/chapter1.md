---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX PPPoE-Server
description: Det här dokumentet fokuserar på information om Azure återställnings tider NetX PPPoE-modulen.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 85a762f669e31c7e753f78b270ced15677a87c4c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826610"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-server"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX PPPoE-Server

Med PPP över Ethernet (PPPoE) kan värdar ansluta till PPP-servern via Ethernet i stället för den traditionella Character-baserade seriella linje kommunikationen. Den tekniska informationen om PPPoE beskrivs i RFC 2516: en metod för överföring av PPP över Ethernet (PPPoE). Det här dokumentet fokuserar på information om Azure återställnings tider NetX PPPoE-modulen.

För att tillhandahålla en punkt-till-punkt-anslutning över Ethernet måste varje PPP-session lära sig Ethernet-adressen för fjärr-peer, samt upprätta ett unikt ID för sessionen.

I enlighet med RFC 2516 består PPPoE av två steg: identifierings fasen och PPPoE-sessionen. När en värd (klient) vill starta en PPP-session måste den först utföra identifiering för att hitta en PPPoE-Server. Det här steget gör det också möjligt för servern och klienten att identifiera var and ras Ethernet MAC-adress och SESSION_ID som ska användas för resten av PPP-sessionen.

En Ethernet-ram är följande:

![Diagram som visar en Ethernet-ram.](media/netx-pppoe-server-01.png)

Ethernet-nyttolasten för PPPoE är följande:

![Diagram som visar en Ethernet-nyttolast för PPPoE.](media/netx-pppoe-server-02.png)

## <a name="pppoe-discovery-stage"></a>Stadium för PPPoE-identifiering

Med PPPoE-identifieringen kan klienter välja en server från alla tillgängliga servrar i nätverket, effektivt för att skapa en session innan PPP-ramar utbyts. I slutet av identifierings fasen måste både klienten och servern enas om ett unikt sessions-ID och båda sidorna måste känna till peer-MAC-adressen.

| Identifierings meddelande                                  | Kod | Riktning                                     |
| -------------------------------------------------- | ---- | --------------------------------------------- |
| Initiering av PPPoE-aktiv identifiering (PADI)           | 0x09 | Från klient till sändning                      |
| PADO (PPPoE Active Discovery-erbjudande)                | 0x07 | Från server till klient                         |
| PADR (PPPoE Active Discovery Request)              | 0x19 | Från klient till Server                         |
| Session för PPPOE-aktiv identifiering-bekräftelse (pad) | 0x65 | Från server till klient                         |
| Avsluta aktiv identifiering av PPPoE (PADT)            | 0xa7 | Kan initieras från antingen Server eller klient |

Alla identifierings-Ethernet-ramar har fältet ETHER_TYPE angivet till värdet 0x8863.

## <a name="pppoe-session-message"></a>Meddelande om PPPoE-session

När klienten och servern har skapat en session kan PPP-ramar överföras som PPPoE-session meddelanden. Under en session får SESSION_ID inte ändras och måste vara det värde som servern tilldelade under identifierings fasen.

Alla Ethernet-ramar för PPPoE-session har fältet ETHER_TYPE angivet till värdet 0x8864.