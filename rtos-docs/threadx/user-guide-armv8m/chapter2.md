---
title: Kapitel 2 – Installera ThreadX-stöd för ARMv8-M
description: I det här kapitlet beskrivs hur du installerar och använder ThreadX-källkoden för ARMv8-M-arkitekturen.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 085310acd5262226e9ff3af440a5f05268c7799e78eda81334a13b736222b95c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801962"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a>Kapitel 2 Installera ThreadX-stöd för ARMv8-M

Det finns ytterligare ThreadX-källkodsfiler som stöder ARMv8-M-arkitekturen.

Om ThreadX ska köras i säkert läge behövs inte dessa ytterligare filer och API:er. Om du vill köra ThreadX i säkert läge **definierar du symbolen TX_SECURE_EXECUTION** längst upp i tx_port.h _ eller på ***kommandoraden eller projektinställningarna. Se till att _* TX_SECURE_EXECUTION** har definierats för alla c- och sammansättningsfiler. ThreadX och användarprogrammet körs i säkert läge.

Om du vill köra ThreadX och användarprogrammet i icke-säkert läge och stödja icke-säkra anropbara säkra funktioner gör du följande.

Filen ***tx_thread_secure_stack.c*** måste läggas till i det säkra programmet.

Följande filer måste läggas till i ThreadX-biblioteket.

- ***tx_secure_interface.h***
- ***txe_thread_secure_stack_allocate.c***
- ***txe_thread_secure_stack_free.c***
- ***tx_thread_secure_stack_allocate.s***
- ***tx_thread_secure_stack_free.s***

Följande två filer ersätter de allmänna filerna i ThreadX-biblioteket.

- ***tx_thread_stack_error_handler.c***
- ***tx_thread_stack_error_notify.c***

## <a name="additional-threadx-sources-for-armv8-m"></a>Ytterligare ThreadX-källor för ARMv8-M

Ytterligare ThreadX-filer för ARMv8-M TrustZone-arkitekturen beskrivs nedan.

  | **Filnamn**                            | **Innehåll**                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | ***tx_secure_interface.h***              | Inkludera fil som definierar ThreadX-funktioner som inte är säkra att anropa. |
  | ***txe_thread_secure_stack_allocate.c*** |  Felkontrollsfil för API:et secure stack allocate. |
  | ***txe_thread_secure_stack_free.c***     |  Felkontrollsfil för det kostnadsfria API:et för säker stack. |
  | ***tx_thread_secure_stack_allocate.s***  |  Icke-säker faner för den säkra stacken allokerar tjänsten. |
  | ***tx_thread_secure_stack_free.s***      |  Icke-säker veneer för den kostnadsfria secure stack-tjänsten. |
  | ***tx_thread_stack_error_handler.c***    |  Hanterare för trådstackfel. |
  | ***tx_thread_stack_error_notify.c***     |  Registrera återanrop av meddelanden för hantering av fel i trådstacken. |
