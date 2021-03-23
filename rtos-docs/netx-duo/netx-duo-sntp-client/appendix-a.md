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
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a><span data-ttu-id="d1849-103">Bilaga A – Azure återställnings tider NetX Duo SNTP – oåterkalleliga felkoder</span><span class="sxs-lookup"><span data-stu-id="d1849-103">Appendix A - Azure RTOS NetX Duo SNTP Fatal Error Codes</span></span>

<span data-ttu-id="d1849-104">Följande felkoder leder till att Azure återställnings tider NetX Duo SNTP-klienten avbryter tids uppdateringar med den aktuella servern.</span><span class="sxs-lookup"><span data-stu-id="d1849-104">The following error codes will result in the Azure RTOS NetX Duo SNTP Client aborting time updates with the current server.</span></span> <span data-ttu-id="d1849-105">Det är upp till programmet att avgöra om servern ska tas bort från listan över tillgängliga servrar i SNTP-klienten, eller bara växla till nästa tillgängliga server i listan.</span><span class="sxs-lookup"><span data-stu-id="d1849-105">It is up to the application to decide if the server should be removed from the SNTP Client list of available servers, or simply switch to the next available server on the list.</span></span> <span data-ttu-id="d1849-106">Definitionen av varje fel status definieras i \* nxd_sntp_client. h.</span><span class="sxs-lookup"><span data-stu-id="d1849-106">The definition of each error status is defined in \*nxd_sntp_client.h.</span></span> *

<span data-ttu-id="d1849-107">När SNTP-klienten returnerar ett fel från listan nedan till programmet bör servern förmodligen ersättas med en annan server.</span><span class="sxs-lookup"><span data-stu-id="d1849-107">When the SNTP Client returns an error from the list below to the application, the Server should probably be replaced with another Server.</span></span> <span data-ttu-id="d1849-108">Observera att NX_SNTP_KOD_REMOVE_SERVER fel status lämnas till SNTP-klientens kyss för död hanterare (callback-funktionen) för att ange:</span><span class="sxs-lookup"><span data-stu-id="d1849-108">Note that the NX_SNTP_KOD_REMOVE_SERVER error status is left to the SNTP Client kiss of death handler (callback function) to set:</span></span>

- <span data-ttu-id="d1849-109">NX_SNTP_KOD_REMOVE_SERVER 0xD0C</span><span class="sxs-lookup"><span data-stu-id="d1849-109">NX_SNTP_KOD_REMOVE_SERVER 0xD0C</span></span>  
- <span data-ttu-id="d1849-110">NX_SNTP_SERVER_AUTH_FAIL 0xD0D</span><span class="sxs-lookup"><span data-stu-id="d1849-110">NX_SNTP_SERVER_AUTH_FAIL 0xD0D</span></span>  
- <span data-ttu-id="d1849-111">NX_SNTP_INVALID_NTP_VERSION 0xD11</span><span class="sxs-lookup"><span data-stu-id="d1849-111">NX_SNTP_INVALID_NTP_VERSION 0xD11</span></span>  
- <span data-ttu-id="d1849-112">NX_SNTP_INVALID_SERVER_MODE 0xD12</span><span class="sxs-lookup"><span data-stu-id="d1849-112">NX_SNTP_INVALID_SERVER_MODE 0xD12</span></span>  
- <span data-ttu-id="d1849-113">NX_SNTP_INVALID_SERVER_STRATUM 0xD15</span><span class="sxs-lookup"><span data-stu-id="d1849-113">NX_SNTP_INVALID_SERVER_STRATUM 0xD15</span></span>  

<span data-ttu-id="d1849-114">När SNTP-klienten returnerar ett fel från listan nedan till programmet, kan det hända att servern tillfälligt inte kan tillhandahålla giltiga tids uppdateringar och behöver inte tas bort:</span><span class="sxs-lookup"><span data-stu-id="d1849-114">When the SNTP Client returns an error from the list below to the application, the Server may only temporarily be unable to provide valid time updates and need not be removed:</span></span>

- <span data-ttu-id="d1849-115">HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09</span><span class="sxs-lookup"><span data-stu-id="d1849-115">HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09</span></span>  
- <span data-ttu-id="d1849-116">NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A</span><span class="sxs-lookup"><span data-stu-id="d1849-116">NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A</span></span>  
- <span data-ttu-id="d1849-117">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B</span><span class="sxs-lookup"><span data-stu-id="d1849-117">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B</span></span>  
- <span data-ttu-id="d1849-118">NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17</span><span class="sxs-lookup"><span data-stu-id="d1849-118">NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17</span></span>  
- <span data-ttu-id="d1849-119">NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16</span><span class="sxs-lookup"><span data-stu-id="d1849-119">NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16</span></span>  
- <span data-ttu-id="d1849-120">NX_SNTP_INVALID_RTT_TIME 0xD21</span><span class="sxs-lookup"><span data-stu-id="d1849-120">NX_SNTP_INVALID_RTT_TIME 0xD21</span></span>  
- <span data-ttu-id="d1849-121">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24</span><span class="sxs-lookup"><span data-stu-id="d1849-121">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24</span></span>