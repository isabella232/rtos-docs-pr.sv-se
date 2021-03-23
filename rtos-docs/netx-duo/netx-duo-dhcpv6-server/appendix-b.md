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
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a>Bilaga B – Azure återställnings tider NetX Duo DHCPv6-server status koder

| Name              | Kod            | Beskrivning |
| ------------------- | ------------------- | --------------- |
| Klart | 0 | Klart |
| Ospecificerat haveri | 1 | Det gick inte att ange en orsak. den här status koden anges av servern för att indikera ett allmänt haveri vid beviljande av klientbegäran som inte matchar övriga koder |
| Noaddress tillgänglig | 2 | Servern har inga adresser som kan tilldelas till klienten |
| Nobinding | 3 | Klientens IA-adress (binding) är inte tillgänglig, t. ex. att den begärda IP-adressen inte är tillgänglig för att servern ska låna eller tilldelas till en annan klient. |
| NotOnLink | 4 | Prefixet för adressen anger att IP-adressen inte är en på länk adress |
| UseMulticast | 5 | Skickas av en server som svar på att ta emot ett klient meddelande med serverns unicast-adress i stället för *All_DHCP_Relay_Agents_and_Servers* multicast-adress |