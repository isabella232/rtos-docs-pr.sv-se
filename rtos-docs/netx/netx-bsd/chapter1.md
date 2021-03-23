---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX BSD
description: 'Azure återställnings tider NetX BSD Sockets API kompatibilitet-omslutningen har stöd för några av de grundläggande BSD-API: erna med vissa begränsningar och använder NetX-primitiver under.'
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fce781ac97ae75c4148614453eeb35c3064f8849
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825608"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a><span data-ttu-id="be09a-103">Kapitel 1 – Introduktion till Azure återställnings tider NetX BSD</span><span class="sxs-lookup"><span data-stu-id="be09a-103">Chapter 1 - Introduction to Azure RTOS NetX BSD</span></span>

<span data-ttu-id="be09a-104">NetX BSD Sockets API kompatibilitet-omslutningen stöder vissa av de grundläggande BSD-API: erna med vissa begränsningar och använder NetX-primitiver under.</span><span class="sxs-lookup"><span data-stu-id="be09a-104">The NetX BSD Sockets API Compliancy Wrapper supports some of the basic BSD Sockets API calls with some limitations and utilizes NetX primitives underneath.</span></span> <span data-ttu-id="be09a-105">Detta BSD-skikt i BSD Sockets-API: n ska fungera lika snabb eller något snabbare än vanliga BSD-implementeringar, eftersom den här omslutningen använder interna NetX-primitiver och kringgår grundläggande NetX fel kontroll.</span><span class="sxs-lookup"><span data-stu-id="be09a-105">This BSD Sockets API compatibility layer should perform as fast or slightly faster than typical BSD implementations, since this Wrapper utilizes internal NetX primitives and bypasses basic NetX error checking.</span></span>

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a><span data-ttu-id="be09a-106">BSD Sockets API kompatibilitet wrapper-källa</span><span class="sxs-lookup"><span data-stu-id="be09a-106">BSD Sockets API Compliancy Wrapper Source</span></span>

<span data-ttu-id="be09a-107">Käll koden för BSD-omslutningen är utformad för enkelhet och består bara av två filer, *nx_bsd. h* och *nx_bsd. c*.</span><span class="sxs-lookup"><span data-stu-id="be09a-107">The BSD Wrapper source code is designed for simplicity and is comprised of only two files, *nx_bsd.h* and *nx_bsd.c*.</span></span> <span data-ttu-id="be09a-108">Filen *nx_bsd. h* definierar alla nödvändiga BSD-konstanter och subrutin-prototyper för BSD-Sockets-API, medan *nx_bsd. c* innehåller den faktiska käll koden för BSD Sockets-API-kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="be09a-108">The *nx_bsd.h* file defines all the necessary BSD Sockets API Wrapper constants and subroutine prototypes, while *nx_bsd.c* contains the actual BSD Sockets API compatibility source code.</span></span> <span data-ttu-id="be09a-109">Dessa filer för BSD-omslutningen är gemensamma för alla NetX-support paket.</span><span class="sxs-lookup"><span data-stu-id="be09a-109">These BSD Wrapper source files are common to all NetX support packages.</span></span>

<span data-ttu-id="be09a-110">Paketet består av:</span><span class="sxs-lookup"><span data-stu-id="be09a-110">The package consists of:</span></span>

- <span data-ttu-id="be09a-111">**nx_bsd. c**: gränssnitts käll kod</span><span class="sxs-lookup"><span data-stu-id="be09a-111">**nx_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="be09a-112">**nx_bsd. h**: huvud rubrik fil</span><span class="sxs-lookup"><span data-stu-id="be09a-112">**nx_bsd.h**: Main header file</span></span>

<span data-ttu-id="be09a-113">Exempel på demo program:</span><span class="sxs-lookup"><span data-stu-id="be09a-113">Sample demo programs:</span></span>

- <span data-ttu-id="be09a-114">**bsd_demo_tcp. c**: *demo med en enda TCP-server och-klient*</span><span class="sxs-lookup"><span data-stu-id="be09a-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="be09a-115">**bsd_demo_udp. c**: *demo med två UDP-klienter och en UDP-Server*</span><span class="sxs-lookup"><span data-stu-id="be09a-115">**bsd_demo_udp.c**: *Demo with two UDP clients and a UDP server*</span></span>
