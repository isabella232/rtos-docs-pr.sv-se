---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo LWM2M-klienten
description: Det här kapitlet innehåller en introduktion till Machine Protocol-klienten med Azure återställnings tider NetX Duo Lightweight Machine.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 12f13c154668b3cadfae0924e59b55631dc27424
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825956"
---
# <a name="chapter-1--introduction-to-lwm2m-client"></a><span data-ttu-id="48b23-103">Kapitel 1 Introduktion till LWM2M-klienten</span><span class="sxs-lookup"><span data-stu-id="48b23-103">Chapter 1  Introduction to LWM2M Client</span></span>

<span data-ttu-id="48b23-104">Klient protokollet Azure återställnings tider NetX Duo LWM2M implementerar klient delen av den lätta datorn till Machine Protocol standard.</span><span class="sxs-lookup"><span data-stu-id="48b23-104">The Azure RTOS NetX Duo LWM2M Client Protocol implements the client part of the Lightweight Machine to Machine protocol standard.</span></span> <span data-ttu-id="48b23-105">(LWM2M 1.0-20170208A)</span><span class="sxs-lookup"><span data-stu-id="48b23-105">(LWM2M 1.0-20170208A)</span></span>

## <a name="netx-lwm2m-client-requirements"></a><span data-ttu-id="48b23-106">NetX LWM2M-klient krav</span><span class="sxs-lookup"><span data-stu-id="48b23-106">NetX LWM2M Client Requirements</span></span>

<span data-ttu-id="48b23-107">För att kunna fungera korrekt kräver LWM2M-klientens kör tids bibliotek att en NetX-IP-instans redan har skapats.</span><span class="sxs-lookup"><span data-stu-id="48b23-107">In order to function properly, the LWM2M Client run-time library requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="48b23-108">NetX LWM2M-klient paketet innehåller inga ytterligare krav.</span><span class="sxs-lookup"><span data-stu-id="48b23-108">The NetX LWM2M Client package has no further requirements.</span></span>

## <a name="netx-lwm2m-client-rfcs"></a><span data-ttu-id="48b23-109">NetX LWM2M-klientens RFC</span><span class="sxs-lookup"><span data-stu-id="48b23-109">NetX LWM2M Client RFCs</span></span>

<span data-ttu-id="48b23-110">LWM2M-klienten är kompatibel med OMA-TS-LightweightM2M-v1 \_ 0-20170208-A och följande RFC: er relaterade till det begränsade applikations protokollet (CoAP).</span><span class="sxs-lookup"><span data-stu-id="48b23-110">LWM2M Client is compliant with OMA-TS-LightweightM2M-V1\_0-20170208-A and the following RFCs related to the Constrained Application Protocol (CoAP).</span></span>

* <span data-ttu-id="48b23-111">RFC 7252-CoAP (begränsat program protokoll)</span><span class="sxs-lookup"><span data-stu-id="48b23-111">RFC 7252 The Constrained Application Protocol (CoAP)</span></span>

* <span data-ttu-id="48b23-112">RFC 7641 om att observera resurser i det begränsade applikations protokollet (CoAP)</span><span class="sxs-lookup"><span data-stu-id="48b23-112">RFC 7641 Observing Resources in the Constrained Application Protocol (CoAP)</span></span>

* <span data-ttu-id="48b23-113">RFC 6690-länk format för begränsat RESTful-miljöer (CoRE)</span><span class="sxs-lookup"><span data-stu-id="48b23-113">RFC 6690 Constrained RESTful Environments (CoRE) Link Format</span></span>

<span data-ttu-id="48b23-114">Mer information finns i [OMA-TS-LightweightM2M-V1 \_ 0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).</span><span class="sxs-lookup"><span data-stu-id="48b23-114">For more information, please see [OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).</span></span>