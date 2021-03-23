---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX-LWM2M
description: Azure återställnings tider NetX LWM2M-protokollet implementerar klient delen av den lätta datorn till Machine Protocol standard.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c29af430975266eed684bd1de38d9e5d7e2586a6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826709"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a><span data-ttu-id="b80cb-103">Kapitel 1 – Introduktion till Azure återställnings tider NetX-LWM2M</span><span class="sxs-lookup"><span data-stu-id="b80cb-103">Chapter 1 - Introduction to Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="b80cb-104">Azure återställnings tider NetX LWM2M-protokollet implementerar klient delen av den lätta datorn till Machine Protocol standard.</span><span class="sxs-lookup"><span data-stu-id="b80cb-104">The Azure RTOS NetX LWM2M Protocol implements the client part of the Lightweight Machine to Machine protocol standard.</span></span>

## <a name="netx-lwm2m-requirements"></a><span data-ttu-id="b80cb-105">NetX LWM2M-krav</span><span class="sxs-lookup"><span data-stu-id="b80cb-105">NetX LWM2M Requirements</span></span>

<span data-ttu-id="b80cb-106">För att fungera korrekt, kräver NetX-LWM2M kör tids bibliotek att en NetX-IP-instans redan har skapats.</span><span class="sxs-lookup"><span data-stu-id="b80cb-106">In order to function properly, the NetX LWM2M run-time library requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="b80cb-107">NetX LWM2M-paketet har inga ytterligare krav.</span><span class="sxs-lookup"><span data-stu-id="b80cb-107">The NetX LWM2M package has no further requirements.</span></span>

## <a name="netx-lwm2m-rfcs"></a><span data-ttu-id="b80cb-108">NetX LWM2M-rapporter</span><span class="sxs-lookup"><span data-stu-id="b80cb-108">NetX LWM2M RFCs</span></span>

<span data-ttu-id="b80cb-109">NetX LWM2M är kompatibel med OMA-TS-LightweightM2M-V1_0 -20170208-A och följande RFC: er relaterade till det begränsade applikations protokollet (CoAP):</span><span class="sxs-lookup"><span data-stu-id="b80cb-109">NetX LWM2M is compliant with OMA-TS-LightweightM2M-V1_0-20170208-A and the following RFCs related to the Constrained Application Protocol (CoAP):</span></span>

- <span data-ttu-id="b80cb-110">**RFC 7252**: det begränsade applikations protokollet (CoAP)</span><span class="sxs-lookup"><span data-stu-id="b80cb-110">**RFC 7252**: The Constrained Application Protocol (CoAP)</span></span>

- <span data-ttu-id="b80cb-111">**RFC 7641**: att observera resurser i det begränsade program protokollet (CoAP)</span><span class="sxs-lookup"><span data-stu-id="b80cb-111">**RFC 7641**: Observing Resources in the Constrained Application Protocol (CoAP)</span></span>

- <span data-ttu-id="b80cb-112">**RFC 6690**: begränsat RESTful miljöer (Core) länk format</span><span class="sxs-lookup"><span data-stu-id="b80cb-112">**RFC 6690**: Constrained RESTful Environments (CoRE) Link Format</span></span>