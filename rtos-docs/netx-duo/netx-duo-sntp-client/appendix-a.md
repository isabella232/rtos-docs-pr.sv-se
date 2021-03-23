---
title: Bilaga A – Azure återställnings tider NetX Duo SNTP – oåterkalleliga felkoder
description: Följande felkoder leder till att Azure återställnings tider NetX Duo SNTP-klienten avbryter tids uppdateringar med den aktuella servern.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 065e7a3e65b3cf8d7fcfb34bb9568a673791609a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825761"
---
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a>Bilaga A – Azure återställnings tider NetX Duo SNTP – oåterkalleliga felkoder

Följande felkoder leder till att Azure återställnings tider NetX Duo SNTP-klienten avbryter tids uppdateringar med den aktuella servern. Det är upp till programmet att avgöra om servern ska tas bort från listan över tillgängliga servrar i SNTP-klienten, eller bara växla till nästa tillgängliga server i listan. Definitionen av varje fel status definieras i * nxd_sntp_client. h. *

När SNTP-klienten returnerar ett fel från listan nedan till programmet bör servern förmodligen ersättas med en annan server. Observera att NX_SNTP_KOD_REMOVE_SERVER fel status lämnas till SNTP-klientens kyss för död hanterare (callback-funktionen) för att ange:

- NX_SNTP_KOD_REMOVE_SERVER 0xD0C  
- NX_SNTP_SERVER_AUTH_FAIL 0xD0D  
- NX_SNTP_INVALID_NTP_VERSION 0xD11  
- NX_SNTP_INVALID_SERVER_MODE 0xD12  
- NX_SNTP_INVALID_SERVER_STRATUM 0xD15  

När SNTP-klienten returnerar ett fel från listan nedan till programmet, kan det hända att servern tillfälligt inte kan tillhandahålla giltiga tids uppdateringar och behöver inte tas bort:

- HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09  
- NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B  
- NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17  
- NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16  
- NX_SNTP_INVALID_RTT_TIME 0xD21  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24