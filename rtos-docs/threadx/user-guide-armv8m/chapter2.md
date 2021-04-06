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
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a>Kapitel 2 Installera ThreadX-stöd för ARMv8-M

Det finns ytterligare ThreadX-källfiler som stöder ARMv8-M-arkitekturen.

Om ThreadX ska köras i säkert läge behövs inte dessa ytterligare filer och API: er. Om du vill köra ThreadX i säkert läge definierar du symbolen **TX_SECURE_EXECUTION** överst i **_tx_port. h_*_ eller på kommando raden eller projekt inställningarna. Se till att _* TX_SECURE_EXECUTION** har definierats för alla c-och Assembly-filer. ThreadX och användar programmet kommer att köras i säkert läge.

Om du vill köra ThreadX och användar programmet i icke-säkert läge och stödja säkra funktioner som inte är säkra kan du göra följande.

Filen ***tx_thread_secure_stack. c*** måste läggas till i det säkra programmet.

Följande filer måste läggas till i ThreadX-biblioteket.

- ***tx_secure_interface. h***
- ***txe_thread_secure_stack_allocate. c***
- ***txe_thread_secure_stack_free. c***
- ***tx_thread_secure_stack_allocate. s***
- ***tx_thread_secure_stack_free. s***

Följande två filer ersätter de allmänna filerna i ThreadX-biblioteket.

- ***tx_thread_stack_error_handler. c***
- ***tx_thread_stack_error_notify. c***

## <a name="additional-threadx-sources-for-armv8-m"></a>Ytterligare ThreadX-källor för ARMv8-M

De ytterligare ThreadX-filerna för ARMv8-M TrustZone-arkitekturen beskrivs nedan.

  | **Fil namn**                            | **Innehåll**                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | ***tx_secure_interface. h***              | Inkludera en fil som definierar ThreadX-funktioner som inte är säkra. |
  | ***txe_thread_secure_stack_allocate. c*** |  Fel vid kontroll av filen för Secure stack-tilldelningens API. |
  | ***txe_thread_secure_stack_free. c***     |  Fel vid kontroll av filen för det kostnads fria stack-API: et. |
  | ***tx_thread_secure_stack_allocate. s***  |  Icke-säkra Veneer för tjänsten för säker stack tilldelning. |
  | ***tx_thread_secure_stack_free. s***      |  Icke-säkra Veneer för den säkraste stack-tjänsten. |
  | ***tx_thread_stack_error_handler. c***    |  Hanterare för tråd Stacks fel. |
  | ***tx_thread_stack_error_notify. c***     |  Registrera motanrop för meddelanden för hantering av tråds tack-fel. |
