---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX PPPoE-klienten
description: Det här kapitlet innehåller information om Azure återställnings tider NetX PPPoE-modulen.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bbf1e064bb38754bd67b279a0fd60d46d3d6d557
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826643"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-client"></a><span data-ttu-id="4bf62-103">Kapitel 1 – Introduktion till Azure återställnings tider NetX PPPoE-klienten</span><span class="sxs-lookup"><span data-stu-id="4bf62-103">Chapter 1 - Introduction to Azure RTOS NetX PPPoE Client</span></span>

<span data-ttu-id="4bf62-104">Med PPP över Ethernet (PPPoE) kan värdar ansluta till PPP-servern via Ethernet i stället för den traditionella Character-baserade seriella linje kommunikationen.</span><span class="sxs-lookup"><span data-stu-id="4bf62-104">PPP over Ethernet (PPPoE) allows hosts to connect to PPP server via Ethernet instead of the traditional character-based serial line communication.</span></span>  <span data-ttu-id="4bf62-105">Den tekniska informationen om PPPoE beskrivs i RFC 2516: en metod för överföring av PPP över Ethernet (PPPoE).</span><span class="sxs-lookup"><span data-stu-id="4bf62-105">The technical details of PPPoE are described in RFC 2516:  A Method for Transmitting PPP over Ethernet (PPPoE).</span></span> <span data-ttu-id="4bf62-106">Det här dokumentet fokuserar på information om Azure återställnings tider NetX PPPoE-modulen.</span><span class="sxs-lookup"><span data-stu-id="4bf62-106">This document focuses on the details of  Azure RTOS NetX PPPoE module.</span></span>

<span data-ttu-id="4bf62-107">För att tillhandahålla en punkt-till-punkt-anslutning över Ethernet måste varje PPP-session lära sig Ethernet-adressen för fjärr-peer, samt upprätta ett unikt ID för sessionen.</span><span class="sxs-lookup"><span data-stu-id="4bf62-107">To provide a point-to-point connection over Ethernet, each PPP session must learn the Ethernet address of the remote peer, as well as establish a unique session identifier.</span></span>

<span data-ttu-id="4bf62-108">I enlighet med RFC 2516 består PPPoE av två steg: identifierings fasen och PPPoE-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4bf62-108">According to RFC 2516, PPPoE consists of two stages: the Discovery stage, and PPPoE Session stage.</span></span> <span data-ttu-id="4bf62-109">När en värd (klient) vill starta en PPP-session måste den först utföra identifiering för att hitta en PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="4bf62-109">When a host (client) wishes to start a PPP session, it must first perform Discovery to find PPPoE server.</span></span> <span data-ttu-id="4bf62-110">Det här steget gör det också möjligt för servern och klienten att identifiera var and ras Ethernet MAC-adress och SESSION_ID som ska användas för resten av PPP-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4bf62-110">This step also allows the server and the client to identify each other’s Ethernet MAC address and SESSION_ID, which will be used for the rest of the PPP session.</span></span>

<span data-ttu-id="4bf62-111">En Ethernet-ram är följande:</span><span class="sxs-lookup"><span data-stu-id="4bf62-111">An Ethernet frame is as follows:</span></span>

![Ethernet-ram](media/ethernet-frame.png)

<span data-ttu-id="4bf62-113">Ethernet-nyttolasten för PPPoE är följande:</span><span class="sxs-lookup"><span data-stu-id="4bf62-113">The Ethernet payload for PPPoE is as follows:</span></span>

![Ethernet-nyttolast](media/ethernet-payload.png)

## <a name="pppoe-discovery-stage"></a><span data-ttu-id="4bf62-115">Stadium för PPPoE-identifiering</span><span class="sxs-lookup"><span data-stu-id="4bf62-115">PPPoE Discovery Stage</span></span>

<span data-ttu-id="4bf62-116">Med PPPoE-identifieringen kan klienter välja en server från alla tillgängliga servrar i nätverket, effektivt för att skapa en session innan PPP-ramar utbyts.</span><span class="sxs-lookup"><span data-stu-id="4bf62-116">The PPPoE Discovery stage allows clients to select a server from all available servers on the network, effectively to create a session prior to PPP frames being exchanged.</span></span>  <span data-ttu-id="4bf62-117">I slutet av identifierings fasen måste både klienten och servern enas om ett unikt sessions-ID och båda sidorna måste känna till peer-MAC-adressen.</span><span class="sxs-lookup"><span data-stu-id="4bf62-117">At the end of the discovery stage, both the client and the server shall agree on a unique session ID, and both sides need to know peer’s MAC address.</span></span>

| <span data-ttu-id="4bf62-118">Identifierings meddelande</span><span class="sxs-lookup"><span data-stu-id="4bf62-118">Discovery Message</span></span> | <span data-ttu-id="4bf62-119">Kod</span><span class="sxs-lookup"><span data-stu-id="4bf62-119">Code</span></span> | <span data-ttu-id="4bf62-120">Riktning</span><span class="sxs-lookup"><span data-stu-id="4bf62-120">Direction</span></span> |
| ----------------- | ---- | --------- |
| <span data-ttu-id="4bf62-121">Initiering av PPPoE-aktiv identifiering (PADI)</span><span class="sxs-lookup"><span data-stu-id="4bf62-121">PPPoE Active Discovery Initiation (PADI)</span></span> | <span data-ttu-id="4bf62-122">0x09</span><span class="sxs-lookup"><span data-stu-id="4bf62-122">0x09</span></span> | <span data-ttu-id="4bf62-123">Från klient till sändning</span><span class="sxs-lookup"><span data-stu-id="4bf62-123">From Client to broadcast</span></span> |
| <span data-ttu-id="4bf62-124">PADO (PPPoE Active Discovery-erbjudande)</span><span class="sxs-lookup"><span data-stu-id="4bf62-124">PPPoE Active Discovery Offer (PADO)</span></span> | <span data-ttu-id="4bf62-125">0x07</span><span class="sxs-lookup"><span data-stu-id="4bf62-125">0x07</span></span> | <span data-ttu-id="4bf62-126">Från server till klient</span><span class="sxs-lookup"><span data-stu-id="4bf62-126">From Server to Client</span></span> |
| <span data-ttu-id="4bf62-127">PADR (PPPoE Active Discovery Request)</span><span class="sxs-lookup"><span data-stu-id="4bf62-127">PPPoE Active Discovery Request (PADR)</span></span> | <span data-ttu-id="4bf62-128">0x19</span><span class="sxs-lookup"><span data-stu-id="4bf62-128">0x19</span></span> | <span data-ttu-id="4bf62-129">Från klient till Server</span><span class="sxs-lookup"><span data-stu-id="4bf62-129">From Client to Server</span></span> |
| <span data-ttu-id="4bf62-130">Session för PPPOE-aktiv identifiering-bekräftelse (pad)</span><span class="sxs-lookup"><span data-stu-id="4bf62-130">PPPOE Active Discovery Session-confirmation (PADS)</span></span> | <span data-ttu-id="4bf62-131">0x65</span><span class="sxs-lookup"><span data-stu-id="4bf62-131">0x65</span></span> | <span data-ttu-id="4bf62-132">Från server till klient</span><span class="sxs-lookup"><span data-stu-id="4bf62-132">From Server to Client</span></span> |
| <span data-ttu-id="4bf62-133">Avsluta aktiv identifiering av PPPoE (PADT)</span><span class="sxs-lookup"><span data-stu-id="4bf62-133">PPPoE Active Discovery Terminate (PADT)</span></span> | <span data-ttu-id="4bf62-134">0xa7</span><span class="sxs-lookup"><span data-stu-id="4bf62-134">0xa7</span></span> | <span data-ttu-id="4bf62-135">Kan initieras från antingen Server eller klient</span><span class="sxs-lookup"><span data-stu-id="4bf62-135">Can be initiated from either server or client</span></span> |

<span data-ttu-id="4bf62-136">Alla identifierings-Ethernet-ramar har fältet ETHER_TYPE angivet till värdet 0x8863.</span><span class="sxs-lookup"><span data-stu-id="4bf62-136">All Discovery Ethernet frames have the ETHER_TYPE field set to the value 0x8863.</span></span>

## <a name="pppoe-session-message"></a><span data-ttu-id="4bf62-137">Meddelande om PPPoE-session</span><span class="sxs-lookup"><span data-stu-id="4bf62-137">PPPoE Session Message</span></span>

<span data-ttu-id="4bf62-138">När klienten och servern har skapat en session kan PPP-ramar överföras som PPPoE-session meddelanden.</span><span class="sxs-lookup"><span data-stu-id="4bf62-138">After the client and the server create a session, PPP frames can be transferred as PPPoE Session messages.</span></span>  <span data-ttu-id="4bf62-139">Under en session får SESSION_ID inte ändras och måste vara det värde som servern tilldelade under identifierings fasen.</span><span class="sxs-lookup"><span data-stu-id="4bf62-139">During a session, the SESSION_ID must not change and must be the value the server assigned during the Discovery stage.</span></span>

<span data-ttu-id="4bf62-140">Alla Ethernet-ramar för PPPoE-session har fältet ETHER_TYPE angivet till värdet 0x8864.</span><span class="sxs-lookup"><span data-stu-id="4bf62-140">All PPPoE Session Ethernet frames have the ETHER_TYPE field set to the value 0x8864.</span></span>
