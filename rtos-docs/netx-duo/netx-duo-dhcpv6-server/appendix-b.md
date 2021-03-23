---
title: Bilaga B – Azure återställnings tider NetX Duo DHCPv6-server status koder
description: Det här kapitlet innehåller en beskrivning av alla status koder för NetX Duo DHCPv6-server
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7c79a0c0bc9acfcfca69c7333d30cd7cab35ba5f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826058"
---
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a><span data-ttu-id="9b4b1-103">Bilaga B – Azure återställnings tider NetX Duo DHCPv6-server status koder</span><span class="sxs-lookup"><span data-stu-id="9b4b1-103">Appendix B - Azure RTOS NetX Duo DHCPv6 server status codes</span></span>

| <span data-ttu-id="9b4b1-104">Name</span><span class="sxs-lookup"><span data-stu-id="9b4b1-104">Name</span></span>              | <span data-ttu-id="9b4b1-105">Kod</span><span class="sxs-lookup"><span data-stu-id="9b4b1-105">Code</span></span>            | <span data-ttu-id="9b4b1-106">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="9b4b1-106">Description</span></span> |
| ------------------- | ------------------- | --------------- |
| <span data-ttu-id="9b4b1-107">Klart</span><span class="sxs-lookup"><span data-stu-id="9b4b1-107">Success</span></span> | <span data-ttu-id="9b4b1-108">0</span><span class="sxs-lookup"><span data-stu-id="9b4b1-108">0</span></span> | <span data-ttu-id="9b4b1-109">Klart</span><span class="sxs-lookup"><span data-stu-id="9b4b1-109">Success</span></span> |
| <span data-ttu-id="9b4b1-110">Ospecificerat haveri</span><span class="sxs-lookup"><span data-stu-id="9b4b1-110">Unspecified Failure</span></span> | <span data-ttu-id="9b4b1-111">1</span><span class="sxs-lookup"><span data-stu-id="9b4b1-111">1</span></span> | <span data-ttu-id="9b4b1-112">Det gick inte att ange en orsak. den här status koden anges av servern för att indikera ett allmänt haveri vid beviljande av klientbegäran som inte matchar övriga koder</span><span class="sxs-lookup"><span data-stu-id="9b4b1-112">Failure, reason unspecified; this status code is set by the Server to indicate a general failure in granting the Client request not matching the other codes</span></span> |
| <span data-ttu-id="9b4b1-113">Noaddress tillgänglig</span><span class="sxs-lookup"><span data-stu-id="9b4b1-113">NoAddress Available</span></span> | <span data-ttu-id="9b4b1-114">2</span><span class="sxs-lookup"><span data-stu-id="9b4b1-114">2</span></span> | <span data-ttu-id="9b4b1-115">Servern har inga adresser som kan tilldelas till klienten</span><span class="sxs-lookup"><span data-stu-id="9b4b1-115">Server has no addresses available to assign to the Client</span></span> |
| <span data-ttu-id="9b4b1-116">Nobinding</span><span class="sxs-lookup"><span data-stu-id="9b4b1-116">NoBinding</span></span> | <span data-ttu-id="9b4b1-117">3</span><span class="sxs-lookup"><span data-stu-id="9b4b1-117">3</span></span> | <span data-ttu-id="9b4b1-118">Klientens IA-adress (binding) är inte tillgänglig, t. ex. att den begärda IP-adressen inte är tillgänglig för att servern ska låna eller tilldelas till en annan klient.</span><span class="sxs-lookup"><span data-stu-id="9b4b1-118">Client IA address (binding) is not available e.g. the requested IP address is not available for the Server to lease or assigned to another Client.</span></span> |
| <span data-ttu-id="9b4b1-119">NotOnLink</span><span class="sxs-lookup"><span data-stu-id="9b4b1-119">NotOnLink</span></span> | <span data-ttu-id="9b4b1-120">4</span><span class="sxs-lookup"><span data-stu-id="9b4b1-120">4</span></span> | <span data-ttu-id="9b4b1-121">Prefixet för adressen anger att IP-adressen inte är en på länk adress</span><span class="sxs-lookup"><span data-stu-id="9b4b1-121">The prefix for the address indicates the IP address is not an on link address</span></span> |
| <span data-ttu-id="9b4b1-122">UseMulticast</span><span class="sxs-lookup"><span data-stu-id="9b4b1-122">UseMulticast</span></span> | <span data-ttu-id="9b4b1-123">5</span><span class="sxs-lookup"><span data-stu-id="9b4b1-123">5</span></span> | <span data-ttu-id="9b4b1-124">Skickas av en server som svar på att ta emot ett klient meddelande med serverns unicast-adress i stället för *All_DHCP_Relay_Agents_and_Servers* multicast-adress</span><span class="sxs-lookup"><span data-stu-id="9b4b1-124">Sent by a Server in response to receiving a Client message using the Server’s unicast address instead of the *All_DHCP_Relay_Agents_and_Servers* multicast address</span></span> |