---
title: Kapitel 1 – Introduktion till Azure RTOS NetX PPPoE Server
description: Det här dokumentet fokuserar på information om Azure RTOS NetX PPPoE-modulen.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2f79cba35991555f7f8d10e589aa251387ce25c48c3b729da371b548f13321bd
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798335"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-server"></a>Kapitel 1 – Introduktion till Azure RTOS NetX PPPoE Server

PPP över Ethernet (PPPoE) gör att värdar kan ansluta till PPP-servern via Ethernet i stället för traditionell teckenbaserad serielinjekommunikation. Den tekniska informationen om PPPoE beskrivs i RFC 2516: A Method for Transmitting PPP over Ethernet (PPPoE). Det här dokumentet fokuserar på information om Azure RTOS NetX PPPoE-modulen.

För att tillhandahålla en punkt-till-punkt-anslutning över Ethernet måste varje PPP-session lära sig Ethernet-adressen för fjärr-peer samt upprätta en unik sessionsidentifierare.

Enligt RFC 2516 består PPPoE av två steg: identifieringssteget och PPPoE-sessionsfasen. När en värd (klient) vill starta en PPP-session måste den först utföra identifiering för att hitta PPPoE-servern. Det här steget gör det också möjligt för servern och klienten att identifiera varandras Ethernet MAC-adress och SESSION_ID, som kommer att användas för resten av PPP-sessionen.

En Ethernet-ram är följande:

![Diagram som visar en Ethernet-ram.](media/netx-pppoe-server-01.png)

Ethernet-nyttolasten för PPPoE är följande:

![Diagram som visar en Ethernet-nyttolast för PPPoE.](media/netx-pppoe-server-02.png)

## <a name="pppoe-discovery-stage"></a>PPPoE-identifieringssteg

Med PPPoE-identifieringsfasen kan klienter välja en server från alla tillgängliga servrar i nätverket för att effektivt skapa en session innan PPP-bildrutor byts ut. I slutet av identifieringsfasen ska både klienten och servern komma överens om ett unikt sessions-ID, och båda sidor måste känna till peer-datorns MAC-adress.

| Identifieringsmeddelande                                  | Kod | Riktning                                     |
| -------------------------------------------------- | ---- | --------------------------------------------- |
| PPPoE Active Discovery Initiering (PADI)           | 0x09 | Från klient till sändning                      |
| PPPoE Active Discovery-erbjudande (PADO)                | 0x07 | Från server till klient                         |
| PPPoE Active Discovery Request (PADR)              | 0x19 | Från klient till server                         |
| Sessionsbekräftelse för PPPOE Active Discovery (PADS) | 0x65 | Från server till klient                         |
| PPPoE Active Discovery Terminate (PADT)            | 0xa7 | Kan initieras från antingen server eller klient |

Alla Discovery Ethernet-bildrutor har ETHER_TYPE-fältet inställt på värdet 0x8863.

## <a name="pppoe-session-message"></a>PPPoE-sessionsmeddelande

När klienten och servern har skapat en session kan PPP-bildrutor överföras som PPPoE-sessionsmeddelanden. Under en session får SESSION_ID inte ändras och måste vara det värde som servern tilldelade under identifieringsfasen.

Alla PPPoE Session Ethernet-bildrutor har ETHER_TYPE-fältet inställt på värdet 0x8864.