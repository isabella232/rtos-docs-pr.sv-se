---
title: Kapitel 2 – Installera ThreadX-stöd för ARMv8-M
description: I det här kapitlet beskrivs hur du installerar och använder ThreadX-källkod för ARMv8-M-arkitekturen.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 303b83bcc92797314b764353b770965c0170fb99
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377624"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a><span data-ttu-id="789f4-103">Kapitel 2 Installera ThreadX-stöd för ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="789f4-103">Chapter 2  Installing ThreadX support for ARMv8-M</span></span>

<span data-ttu-id="789f4-104">Det finns ytterligare ThreadX-källfiler som stöder ARMv8-M-arkitekturen.</span><span class="sxs-lookup"><span data-stu-id="789f4-104">There are additional ThreadX source code files to support the ARMv8-M architecture.</span></span>

<span data-ttu-id="789f4-105">Om ThreadX ska köras i säkert läge behövs inte dessa ytterligare filer och API: er.</span><span class="sxs-lookup"><span data-stu-id="789f4-105">If ThreadX is to be run in secure mode, these additional files and APIs are not needed.</span></span> <span data-ttu-id="789f4-106">Om du vill köra ThreadX i säkert läge definierar du symbolen **TX_SECURE_EXECUTION** överst i **_tx_port. h_*_ eller på kommando raden eller projekt inställningarna. Se till att _\* TX_SECURE_EXECUTION*\* har definierats för alla c-och Assembly-filer.</span><span class="sxs-lookup"><span data-stu-id="789f4-106">To run ThreadX in secure mode, define the symbol **TX_SECURE_EXECUTION** at the top of **_tx_port.h_*_ or on the command line or project settings. Ensure _\* TX_SECURE_EXECUTION*\* is defined for all c and assembly files.</span></span> <span data-ttu-id="789f4-107">ThreadX och användar programmet kommer att köras i säkert läge.</span><span class="sxs-lookup"><span data-stu-id="789f4-107">ThreadX and the user application will execute in secure mode.</span></span>

<span data-ttu-id="789f4-108">Om du vill köra ThreadX och användar programmet i icke-säkert läge och stödja säkra funktioner som inte är säkra kan du göra följande.</span><span class="sxs-lookup"><span data-stu-id="789f4-108">To run ThreadX and the user application in non-secure mode and support non-secure callable secure functions, please do the following.</span></span>

<span data-ttu-id="789f4-109">Filen ***tx_thread_secure_stack. c*** måste läggas till i det säkra programmet.</span><span class="sxs-lookup"><span data-stu-id="789f4-109">The file ***tx_thread_secure_stack.c*** must be added to the secure application.</span></span>

<span data-ttu-id="789f4-110">Följande filer måste läggas till i ThreadX-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="789f4-110">The following files must be added to the ThreadX library.</span></span>

- <span data-ttu-id="789f4-111">***tx_secure_interface. h***</span><span class="sxs-lookup"><span data-stu-id="789f4-111">***tx_secure_interface.h***</span></span>
- <span data-ttu-id="789f4-112">***txe_thread_secure_stack_allocate. c***</span><span class="sxs-lookup"><span data-stu-id="789f4-112">***txe_thread_secure_stack_allocate.c***</span></span>
- <span data-ttu-id="789f4-113">***txe_thread_secure_stack_free. c***</span><span class="sxs-lookup"><span data-stu-id="789f4-113">***txe_thread_secure_stack_free.c***</span></span>
- <span data-ttu-id="789f4-114">***tx_thread_secure_stack_allocate. s***</span><span class="sxs-lookup"><span data-stu-id="789f4-114">***tx_thread_secure_stack_allocate.s***</span></span>
- <span data-ttu-id="789f4-115">***tx_thread_secure_stack_free. s***</span><span class="sxs-lookup"><span data-stu-id="789f4-115">***tx_thread_secure_stack_free.s***</span></span>

<span data-ttu-id="789f4-116">Följande två filer ersätter de allmänna filerna i ThreadX-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="789f4-116">The following two files replace the generic files in the ThreadX library.</span></span>

- <span data-ttu-id="789f4-117">***tx_thread_stack_error_handler. c***</span><span class="sxs-lookup"><span data-stu-id="789f4-117">***tx_thread_stack_error_handler.c***</span></span>
- <span data-ttu-id="789f4-118">***tx_thread_stack_error_notify. c***</span><span class="sxs-lookup"><span data-stu-id="789f4-118">***tx_thread_stack_error_notify.c***</span></span>

## <a name="additional-threadx-sources-for-armv8-m"></a><span data-ttu-id="789f4-119">Ytterligare ThreadX-källor för ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="789f4-119">Additional ThreadX Sources for ARMv8-M</span></span>

<span data-ttu-id="789f4-120">De ytterligare ThreadX-filerna för ARMv8-M TrustZone-arkitekturen beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="789f4-120">The additional ThreadX files for the ARMv8-M TrustZone architecture are described below.</span></span>

  | <span data-ttu-id="789f4-121">**Fil namn**</span><span class="sxs-lookup"><span data-stu-id="789f4-121">**File Name**</span></span>                            | <span data-ttu-id="789f4-122">**Innehåll**</span><span class="sxs-lookup"><span data-stu-id="789f4-122">**Contents**</span></span>                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | <span data-ttu-id="789f4-123">***tx_secure_interface. h***</span><span class="sxs-lookup"><span data-stu-id="789f4-123">***tx_secure_interface.h***</span></span>              | <span data-ttu-id="789f4-124">Inkludera en fil som definierar ThreadX-funktioner som inte är säkra.</span><span class="sxs-lookup"><span data-stu-id="789f4-124">Include file that defines the ThreadX non-secure callable functions.</span></span> |
  | <span data-ttu-id="789f4-125">***txe_thread_secure_stack_allocate. c***</span><span class="sxs-lookup"><span data-stu-id="789f4-125">***txe_thread_secure_stack_allocate.c***</span></span> |  <span data-ttu-id="789f4-126">Fel vid kontroll av filen för Secure stack-tilldelningens API.</span><span class="sxs-lookup"><span data-stu-id="789f4-126">Error-checking file for the secure stack allocate API.</span></span> |
  | <span data-ttu-id="789f4-127">***txe_thread_secure_stack_free. c***</span><span class="sxs-lookup"><span data-stu-id="789f4-127">***txe_thread_secure_stack_free.c***</span></span>     |  <span data-ttu-id="789f4-128">Fel vid kontroll av filen för det kostnads fria stack-API: et.</span><span class="sxs-lookup"><span data-stu-id="789f4-128">Error-checking file for the secure stack free API.</span></span> |
  | <span data-ttu-id="789f4-129">***tx_thread_secure_stack_allocate. s***</span><span class="sxs-lookup"><span data-stu-id="789f4-129">***tx_thread_secure_stack_allocate.s***</span></span>  |  <span data-ttu-id="789f4-130">Icke-säkra Veneer för tjänsten för säker stack tilldelning.</span><span class="sxs-lookup"><span data-stu-id="789f4-130">Non-secure veneer for the secure stack allocate service.</span></span> |
  | <span data-ttu-id="789f4-131">***tx_thread_secure_stack_free. s***</span><span class="sxs-lookup"><span data-stu-id="789f4-131">***tx_thread_secure_stack_free.s***</span></span>      |  <span data-ttu-id="789f4-132">Icke-säkra Veneer för den säkraste stack-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="789f4-132">Non-secure veneer for the secure stack free service.</span></span> |
  | <span data-ttu-id="789f4-133">***tx_thread_stack_error_handler. c***</span><span class="sxs-lookup"><span data-stu-id="789f4-133">***tx_thread_stack_error_handler.c***</span></span>    |  <span data-ttu-id="789f4-134">Hanterare för tråd Stacks fel.</span><span class="sxs-lookup"><span data-stu-id="789f4-134">Handler for thread stack errors.</span></span> |
  | <span data-ttu-id="789f4-135">***tx_thread_stack_error_notify. c***</span><span class="sxs-lookup"><span data-stu-id="789f4-135">***tx_thread_stack_error_notify.c***</span></span>     |  <span data-ttu-id="789f4-136">Registrera motanrop för meddelanden för hantering av tråds tack-fel.</span><span class="sxs-lookup"><span data-stu-id="789f4-136">Register notification callback for handling thread stack errors.</span></span> |
