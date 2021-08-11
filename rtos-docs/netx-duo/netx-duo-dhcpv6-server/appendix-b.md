---
title: Bilaga B – Azure RTOS statuskoder för NetX Duo DHCPv6-servern
description: Det här kapitlet innehåller en beskrivning av alla Statuskoder för NetX Duo DHCPv6-servern
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8b9795607c0fed80646ee01e36edf4ecd2aaadad7f0a023e6979e123b81e1660
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791780"
---
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a>Bilaga B – Azure RTOS statuskoder för NetX Duo DHCPv6-servern

| Name              | Kod            | Beskrivning |
| ------------------- | ------------------- | --------------- |
| Klart | 0 | Klart |
| Ospecificerat fel | 1 | Fel, orsak ospecificerad; Den här statuskoden anges av servern för att indikera ett allmänt fel vid beviljandet av klientbegäran som inte matchar de andra koderna |
| NoAddress Tillgänglig | 2 | Servern har inga adresser som kan tilldelas till klienten |
| NoBinding | 3 | Klientens IA-adress (bindning) är inte tillgänglig, t.ex. att den begärda IP-adressen inte är tillgänglig för servern att låna ut eller tilldelas till en annan klient. |
| NotOnLink | 4 | Prefixet för adressen anger att IP-adressen inte är en on-link-adress |
| UseMulticast | 5 | Skickas av en server som svar på att ta emot ett klientmeddelande med hjälp av serverns unicast-adress i stället *för All_DHCP_Relay_Agents_and_Servers* multicast-adress |