---
title: Bilaga F – GUIX RTOS-bindningstjänster
description: Läs mer om GUIX RTOS-bindningstjänster.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7928e1781be03969de25901ebbe728e6554e96befb59c860f4ea53663c28932d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784605"
---
# <a name="appendix-f---guix-rtos-binding-services"></a>Bilaga F – GUIX RTOS-bindningstjänster

GUIX kräver tråd- eller uppgiftstjänster, mutex, händelsekö och tidsinställningstjänster som tillhandahåller av underliggande RTOS. Som standard är GUIX konfigurerat för att använda ThreadX-operativsystemet i realtid för att tillhandahålla dessa tjänster. Om du vill porta GUIX till ett annat operativsystem ska utvecklaren # definiera förprocessor-direktivet GX_DISABLE_THREADX_BINDING och återskapa GUIX-biblioteket för att ta bort ThreadX-beroendena. Dessutom måste utvecklaren ange följande makrodefinitioner och stödfunktioner. Exempel på dessa makrodefinitioner och stödfunktioner finns i filerna gx_system_rtos_bind.h och gx_system_rtos_bind.c, som ger ett exempel på allmän rtos-integrering.

Makron för systemintegrering:

**GX_RTOS_BINDING_INITIALIZE**

Det här makrot anropas under systeminitieringen. Makrot ska definieras för att anropa alla funktioner som behövs för att förbereda rtos-systemtjänsterna eller RTOS-resurserna innan det används. Det här är bindningens möjlighet att förbereda rtos-resurserna som GUIX kommer att använda.

**GX_SYSTEM_THREAD_START**

Det här makrot anropas när GUIX-uppgiften eller tråden ska börja köras. Det här makrot ska definieras för att anropa en funktion som startar GUIX-tråden som körs. Startpunkten till GUIX-tråden skickas till den anropade funktionen. Signaturen för den anropade funktionen måste vara

**UINT *function_name*(VOID (thread_entry_point)(VOID));**

Den här funktionen GX_SUCCESS returnera om tråden har startats eller GX_FAILURE.

**GX_EVENT_PUSH**

Det här makrot anropas för att skicka en händelse till FIFO-händelsekön som används av GUIX. När du portar till en ny rtos är det ditt ansvar att implementera den här händelsekön på ett trådsäkert sätt. GX_EVENT strukturer måste kopieras till den här kön och kopieras från den här kön, dvs. en kö med GX_EVENT-pekare fungerar inte, eftersom GUIX-händelser kan vara automatiska variabler från händelseproducentens vy. Signaturen för funktionen som anropas av det här makrot måste vara:

**UINT *function_name* (GX_EVENT *event_ptr);**

Den här funktionen ska GX_SUCCESS om händelsen push-skickas till händelsekön, annars ska den returnera GX_FAILURE.

**GX_EVENT_POP**

Det här makrot anropas för att ta bort huvudhändelsen (äldsta) från GUIX-händelsekön och kopiera den till den begärda platsen. Den här funktionen måste kunna blockera eller vänta på en händelse om inga händelser för närvarande finns i händelsekön. Signaturen för funktionen som anropas av det här makrot måste vara

UINT function_name(GX_EVENT *put_event, GX_BOOL wait)

Om wait-parametern == GX_TRUE ska funktionen inte returneras förrän en händelse har angetts. Om wait-parametern GX_FALSE returneras funktionen omedelbart med eller utan en händelse.

Om en händelse hämtas från kön bör den kopieras till put_event och returstatusen är GX_SUCCESS. Annars ska returstatusen vara GX_FAILURE.

**GX_EVENT_FOLD**

Det här makrot anropas av GUIX för att lägga en händelse i FIFO-händelsekön. Vikning av en händelse innebär att om en händelse av samma typ redan finns i kön uppdateras posten så att den innehåller nyttolasten för den nya händelsen. Om en befintlig händelse av samma typ inte hittas i kön, push-skickas en ny händelse till kön. 

För bindningar som inte kan implementera händelsedeckningsfunktionen är det acceptabelt att bara anropa GX_EVENT_PUSH.

**GX_TIMER_START**

Det här makrot anropas när GUIX behöver ta emot periodiska timerindata. Det här makrot ska anropa en tjänst som startar den periodiska RTOS-timertjänsten på låg nivå. Om RTOS-timertjänsten inte enkelt kan stoppas och startas är det acceptabelt men mindre effektivt att låta tjänsten köras hela tiden.

När RTOS-timertjänsten på låg nivå regelbundet upphör att gälla måste bindningen anropa GUIX-systemfunktionen _gx_system_timer_expiration(0); Att anropa den här funktionen med jämna mellanrum är det som driver timertjänsterna för GUIX-timer på hög nivå.

**GX_TIMER_STOP**

Det här makrot anropas när GUIX inte längre behöver en periodisk timer (d.v.s. det inte finns några aktiva GUIX-timers som körs). Om RTOS-timertjänsten inte enkelt kan stoppas och startas är det acceptabelt men mindre effektivt att låta tjänsten köras hela tiden och definiera det här makrot så att det inte gör någonting.

**GX_SYSTEM_MUTEX_LOCK**

Det här makrot anropas av GUIX under kritiska kodavsnitt för att förhindra att en annan uppgift före och ändrar gemensamma datastrukturer, vilket kan orsaka skada. Det här makrot bör anropa en funktion som implementerar lämplig RTOS-resurslåsningstjänst.

Om du aldrig använder några GUIX API-tjänster utanför GUIX-tråden kan du definiera det här makrot så att det inte gör någonting.

**GX_SYSTEM_MUTEX_UNLOCK**

Det här makrot anropas i slutet av kritiska kodavsnitt och bör låsa upp GUIX-resursen med hjälp av lämplig underliggande RTOS-tjänst. Om du aldrig använder några GUIX API-tjänster utanför GUIX-tråden kan du definiera det här makrot så att det inte gör någonting.

**GX_SYSTEM_TIME_GET**

Det här makrot bör anropa en funktion som returnerar att den aktuella systemtiden är "system tick", vilket vanligtvis är antalet timeravbrott på låg nivå som har inträffat sedan systemet startades. Den här tjänsten används för att beräkna pekhändelsepennans hastighet för pekgester. Signaturen för funktionen som anropas av det här makrot måste vara:

**ULONG *function_name*(VOID);**

**GX_CURRENT_THREAD**

Det här makrot anropas för att identifiera den tråd som körs för närvarande. Tjänsten som anropas av det här makrot måste returnera ett void *, vilket innebär att datatypen som används av operativsystemet för att identifiera den aktuella körningstråden måste typas till ett void * för att returneras till GUX.

Ett fullständigt exempel på en allmän RTOS-bindning implementeras i den arkiverade gx_system_rtos_bind.h och gx_system_rtos_bind.c