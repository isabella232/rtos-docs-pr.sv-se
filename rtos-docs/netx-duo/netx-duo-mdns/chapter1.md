---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo mDNS/DNS-SD
description: Azure återställnings tider NetX Duo mDNS/DNS-SD ökar den traditionella DNS-tjänsten.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b46539ee4d502fa4c90fb3392e25cd3bee40dc5b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825926"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a><span data-ttu-id="42356-103">Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo mDNS/DNS-SD</span><span class="sxs-lookup"><span data-stu-id="42356-103">Chapter 1 - Introduction to Azure RTOS NetX Duo mDNS/DNS-SD</span></span>

<span data-ttu-id="42356-104">MDNS och DNS-SD är protokoll som har utformats för att utöka den traditionella DNS-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="42356-104">The mDNS and DNS-SD are protocols designed to augment the traditional DNS service.</span></span> <span data-ttu-id="42356-105">mDNS tillhandahåller värd namn och tjänsts ökning till noderna i det lokala nätverket.</span><span class="sxs-lookup"><span data-stu-id="42356-105">mDNS provides host name and service lookup to the nodes on the local network.</span></span> <span data-ttu-id="42356-106">Varje nod använder IPv4-eller IPv6-multicast-kanal för att meddela tjänster som den erbjuder för sina grannar, svarar på frågor från sina grannar och skickar frågor om sina program.</span><span class="sxs-lookup"><span data-stu-id="42356-106">Each node uses IPv4 or IPv6 multicast channel to announce services it offers to its neighbors, responds to queries from its neighbors, and sends queries on behave of its applications.</span></span> <span data-ttu-id="42356-107">MDNS körs i en distribuerad miljö, vilket eliminerar en centraliserad funktion.</span><span class="sxs-lookup"><span data-stu-id="42356-107">By design, mDNS operates in a distributed environment, thus eliminates a centralized serve.</span></span>

<span data-ttu-id="42356-108">DNS-SD byggts ovanpå mDNS.</span><span class="sxs-lookup"><span data-stu-id="42356-108">DNS-SD is built on top of mDNS.</span></span> <span data-ttu-id="42356-109">DNS-SD tillåter noder att meddela tjänster som de tillhandahåller till det lokala nätverket eller för att identifiera tjänster som erbjuds av andra noder i det lokala nätverket.</span><span class="sxs-lookup"><span data-stu-id="42356-109">DNS-SD allows nodes to announce services they provide to the local network or to discover services offered by other nodes on the local network.</span></span> <span data-ttu-id="42356-110">I hela dokumentet refererar termen *mdns* till tjänsterna som omfattar både mdns-specifikationen och DNS-SD-specifikationen.</span><span class="sxs-lookup"><span data-stu-id="42356-110">Throughout the document, the term *mDNS* refers to the services that cover both the mDNS specification and the DNS-SD specification.</span></span>

## <a name="mdns-standard"></a><span data-ttu-id="42356-111">mDNS standard</span><span class="sxs-lookup"><span data-stu-id="42356-111">mDNS Standard</span></span>

<span data-ttu-id="42356-112">NetX Duo-mDNS/DNS-SD-implementering följer följande RFC: er:</span><span class="sxs-lookup"><span data-stu-id="42356-112">NetX Duo mDNS/DNS-SD implementation conforms to the following RFCs:</span></span>

- <span data-ttu-id="42356-113">RFC 6762: mDNS-specifikation</span><span class="sxs-lookup"><span data-stu-id="42356-113">RFC 6762: mDNS Specification</span></span>
- <span data-ttu-id="42356-114">RFC 6763: DNS-SD-specifikation</span><span class="sxs-lookup"><span data-stu-id="42356-114">RFC 6763: DNS-SD Specification</span></span>