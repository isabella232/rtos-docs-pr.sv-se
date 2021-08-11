---
title: Kapitel 1 – Introduktion till Azure RTOS NetX PPPoE-klient
description: Det här kapitlet innehåller information om Azure RTOS NetX PPPoE-modulen.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 08edb5b332426d4ab5d2f92462438e1cb84245db6c2f6ab2ef72f28eab8a313f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798930"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-client"></a>Kapitel 1 – Introduktion till Azure RTOS NetX PPPoE-klient

PPP över Ethernet (PPPoE) gör att värdar kan ansluta till PPP-servern via Ethernet i stället för traditionell teckenbaserad serielinjekommunikation.  Den tekniska informationen om PPPoE beskrivs i RFC 2516: A Method for Transmitting PPP over Ethernet (PPPoE). Det här dokumentet fokuserar på information om Azure RTOS NetX PPPoE-modulen.

För att tillhandahålla en punkt-till-punkt-anslutning via Ethernet måste varje PPP-session lära sig Ethernet-adressen för fjärr-peer samt upprätta en unik sessionsidentifierare.

Enligt RFC 2516 består PPPoE av två faser: Identifieringsfasen och PPPoE-sessionssteget. När en värd (klient) vill starta en PPP-session måste den först utföra identifiering för att hitta PPPoE-servern. Det här steget gör också att servern och klienten kan identifiera varandras Ethernet MAC-adress och SESSION_ID, som kommer att användas för resten av PPP-sessionen.

En Ethernet-ram är följande:

![Ethernet-ram](media/ethernet-frame.png)

Ethernet-nyttolasten för PPPoE är följande:

![Ethernet-nyttolast](media/ethernet-payload.png)

## <a name="pppoe-discovery-stage"></a>PPPoE-identifieringssteg

PpPoE-identifieringsfasen gör att klienter kan välja en server från alla tillgängliga servrar i nätverket, vilket effektivt skapar en session innan PPP-bildrutor byts ut.  I slutet av identifieringsfasen ska både klienten och servern komma överens om ett unikt sessions-ID, och båda sidor måste känna till peer-datorns MAC-adress.

| Identifieringsmeddelande | Kod | Riktning |
| ----------------- | ---- | --------- |
| PPPoE Active Discovery Initiation (PADI) | 0x09 | Från klient till sändning |
| PPPoE Active Discovery-erbjudande (PADO) | 0x07 | Från server till klient |
| PPPoE Active Discovery Request (PADR) | 0x19 | Från klient till server |
| Sessionsbekräftelse för PPPOE Active Discovery (PADS) | 0x65 | Från server till klient |
| PPPoE Active Discovery Terminate (PADT) | 0xa7 | Kan initieras från antingen server eller klient |

Alla Discovery Ethernet-bildrutor har ETHER_TYPE-fältet inställt på värdet 0x8863.

## <a name="pppoe-session-message"></a>PPPoE-sessionsmeddelande

När klienten och servern har skapat en session kan PPP-bildrutor överföras som PPPoE-sessionsmeddelanden.  Under en session får SESSION_ID inte ändras och måste vara det värde som servern tilldelade under identifieringsfasen.

Alla PPPoE Session Ethernet-bildrutor har ETHER_TYPE-fältet inställt på värdet 0x8864.
