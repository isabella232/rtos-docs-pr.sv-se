---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo BSD
description: BSD socket API kompatibilitet-omslutningen har stöd för några av de grundläggande BSD-API-anropen, med vissa begränsningar och använder Azure återställnings tider NetX Duo-primitiver under.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e89018dffd2f9f9065efab2ecabdf4364c4f89a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826160"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="569c3-103">Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="569c3-103">Chapter 1 - Introduction to Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="569c3-104">BSD socket API kompatibilitet-omslutningen har stöd för några av de grundläggande BSD-API-anropen, med vissa begränsningar och använder Azure återställnings tider NetX Duo-primitiver under.</span><span class="sxs-lookup"><span data-stu-id="569c3-104">The BSD Socket API Compliancy Wrapper supports some of the basic BSD Socket API calls, with some limitations and utilizes Azure RTOS NetX Duo primitives underneath.</span></span>

## <a name="bsd-socket-api-compliancy-wrapper-source"></a><span data-ttu-id="569c3-105">BSD socket API kompatibilitet omslutnings källa</span><span class="sxs-lookup"><span data-stu-id="569c3-105">BSD Socket API Compliancy Wrapper Source</span></span>

<span data-ttu-id="569c3-106">Omslutnings käll koden är utformad för enkelhet och består av två filer, nämligen *nxd_bsd. h* och *nxd_bsd. c*.</span><span class="sxs-lookup"><span data-stu-id="569c3-106">The Wrapper source code is designed for simplicity and is comprised of two files, namely *nxd_bsd.h* and *nxd_bsd.c*.</span></span> <span data-ttu-id="569c3-107">Filen *nxd_bsd. h* definierar alla nödvändiga gränssnitts konstanter och underrutins prototyper för BSD-socket-API, medan *nxd_bsd. c* innehåller den faktiska BSD-källans källkod för BSD socket API.</span><span class="sxs-lookup"><span data-stu-id="569c3-107">The *nxd_bsd.h* file defines all the necessary BSD Socket API wrapper constants and subroutine prototypes, while *nxd_bsd.c* contains the actual BSD Socket API compatibility source code.</span></span> <span data-ttu-id="569c3-108">Dessa omslutnings-källfiler är gemensamma för alla NetX Duo-support paket.</span><span class="sxs-lookup"><span data-stu-id="569c3-108">These Wrapper source files are common to all NetX Duo support packages.</span></span>

<span data-ttu-id="569c3-109">Paketet består av:</span><span class="sxs-lookup"><span data-stu-id="569c3-109">The package consists of:</span></span>

- <span data-ttu-id="569c3-110">**nxd_bsd. c**: gränssnitts käll kod</span><span class="sxs-lookup"><span data-stu-id="569c3-110">**nxd_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="569c3-111">**nxd_bsd. h**: huvud rubrik fil</span><span class="sxs-lookup"><span data-stu-id="569c3-111">**nxd_bsd.h**: Main header file</span></span>

<span data-ttu-id="569c3-112">Exempel på demo program:</span><span class="sxs-lookup"><span data-stu-id="569c3-112">Sample demo programs:</span></span>

- <span data-ttu-id="569c3-113">**bsd_demo_udp. c**: *demo med två UDP-peer-datorer (endast IPv4)*</span><span class="sxs-lookup"><span data-stu-id="569c3-113">**bsd_demo_udp.c**: *Demo with two UDP peers (IPv4 only)*</span></span>
- <span data-ttu-id="569c3-114">**bsd_demo_tcp. c**: *demo med en enda TCP-server och-klient*</span><span class="sxs-lookup"><span data-stu-id="569c3-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="569c3-115">**bsd_demo_raw. c**: *demo med två obearbetade peer-datorer*</span><span class="sxs-lookup"><span data-stu-id="569c3-115">**bsd_demo_raw.c**: *Demo with two RAW peers*</span></span>