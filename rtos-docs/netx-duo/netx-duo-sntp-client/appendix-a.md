---
title: Bilaga A – Azure RTOS Kod för allvarliga fel i NetX Duo SNTP
description: Följande felkoder resulterar i att Azure RTOS NetX Duo SNTP-klienten avbryter tidsuppdateringar med den aktuella servern.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e0152c1342b3edffd42f7442c51e7c5d62b199a5b38085dac06b4c0dbee9e9a8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790113"
---
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a>Bilaga A – Azure RTOS Kod för allvarliga fel i NetX Duo SNTP

Följande felkoder resulterar i att Azure RTOS NetX Duo SNTP-klienten avbryter tidsuppdateringar med den aktuella servern. Det är upp till programmet att avgöra om servern ska tas bort från SNTP-klientlistan över tillgängliga servrar eller helt enkelt växla till nästa tillgängliga server i listan. Definitionen av varje felstatus definieras i *nxd_sntp_client.h. *

När SNTP-klienten returnerar ett fel från listan nedan till programmet bör servern förmodligen ersättas med en annan server. Observera att NX_SNTP_KOD_REMOVE_SERVER felstatus lämnas till SNTP Clientrn of death handler (callback function) för att ange:

- NX_SNTP_KOD_REMOVE_SERVER 0xD0C  
- NX_SNTP_SERVER_AUTH_FAIL 0xD0D  
- NX_SNTP_INVALID_NTP_VERSION 0xD11  
- NX_SNTP_INVALID_SERVER_MODE 0xD12  
- NX_SNTP_INVALID_SERVER_STRATUM 0xD15  

När SNTP-klienten returnerar ett fel från listan nedan till programmet kanske servern bara tillfälligt inte kan tillhandahålla giltiga tidsuppdateringar och behöver inte tas bort:

- HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09  
- NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B  
- NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17  
- NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16  
- NX_SNTP_INVALID_RTT_TIME 0xD21  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24