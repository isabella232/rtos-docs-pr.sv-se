---
title: Bilaga F-GUIX återställnings tider binding Services
description: Lär dig mer om GUIX återställnings tider binding Services.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d94dbb9d7d53ec3e1900188142974cc981dfea9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827270"
---
# <a name="appendix-f---guix-rtos-binding-services"></a>Bilaga F-GUIX återställnings tider binding Services

GUIX kräver tråd-eller aktivitets tjänster, mutex, händ Els Queue och timing-tjänster som tillhandahålls av den underliggande återställnings tider. Som standard är GUIX konfigurerat för att använda det ThreadX real tids operativ systemet för att tillhandahålla dessa tjänster. Om du vill port GUIX till ett annat operativ system ska utvecklaren # definiera för hands versionen av direktivet GX_DISABLE_THREADX_BINDING och återskapa GUIX-biblioteket för att ta bort ThreadX-beroenden. Dessutom måste utvecklaren tillhandahålla följande makro definitioner och stöd funktioner. Exempel på dessa makro definitioner och stöd funktioner finns i filerna gx_system_rtos_bind. h och gx_system_rtos_bind. c, som ger ett exempel på allmän återställnings tider-integrering.

System integrerings makron:

**GX_RTOS_BINDING_INITIALIZE**

Det här makrot anropas under system initiering. Makrot bör definieras för att anropa alla funktioner som behövs för att förbereda dina återställnings tider system tjänster eller återställnings tider-resurser innan de används. Detta är bindningens möjlighet att förbereda de återställnings tider-resurser som GUIX kommer att använda.

**GX_SYSTEM_THREAD_START**

Det här makrot anropas när GUIX-uppgiften eller-tråden ska börja köras. Det här makrot måste definieras för att anropa en funktion som startar GUIX-tråden som körs. Start punkten för GUIX-tråden skickas till den anropade funktionen. Signaturen för den anropade funktionen måste vara

**UINT *function_name*(void (thread_entry_point) (void));**

Den här funktionen ska returnera GX_SUCCESS om tråden har startats eller GX_FAILURE.

**GX_EVENT_PUSH**

Det här makrot anropas för att skicka en händelse till den FIFO-händelselogg som används av GUIX. När du hamnar i en ny återställnings tider är det ditt ansvar att implementera den här händelse kön på ett tråd säkert sätt. GX_EVENT strukturer måste kopieras till den här kön och kopieras från den här kön, dvs. en kö med GX_EVENT pekare fungerar inte, eftersom GUIX-händelser kan vara automatiska variabler från händelse producentens vy. Signaturen för funktionen som anropas av det här makrot måste vara:

**UINT *function_name* (GX_EVENT *event_ptr);**

Den här funktionen bör returnera GX_SUCCESS om händelsen skickas till händelse kön, annars bör den returnera GX_FAILURE.

**GX_EVENT_POP**

Det här makrot anropas för att ta bort huvud händelsen (äldsta) från händelse kön GUIX och kopiera den till den begärda platsen. Den här funktionen måste kunna blockera eller vänta på en händelse om inga händelser finns i händelse kön. Signaturen för funktionen som anropas av det här makrot måste vara

UINT function_name (GX_EVENT * put_event GX_BOOL vänta)

Om parametern wait = = GX_TRUE ska funktionen inte returneras förrän en händelse har angetts. Om parametern wait är GX_FALSE ska funktionen returnera omedelbart med eller utan en händelse.

Om en händelse hämtas från kön bör den kopieras till put_event plats och retur status är GX_SUCCESS. Annars ska retur status vara GX_FAILURE.

**GX_EVENT_FOLD**

Det här makrot anropas av GUIX för att vika en händelse till händelse kön för FIFO. Vik en händelse innebär att om en händelse av samma typ redan finns i kön, uppdateras posten så att den innehåller den nya händelsens nytto Last. Om en befintlig händelse av samma typ inte hittas i kön, skickas en ny händelse till kön. 

För bindningar som inte kan implementera Event viknings funktionen, är det acceptabelt att bara anropa GX_EVENT_PUSH.

**GX_TIMER_START**

Det här makrot anropas när GUIX måste ta emot regelbunden timer-indatamängd. Det här makrot ska anropa en tjänst som startar den periodiska tids tjänsten på låg nivå återställnings tider. Om återställnings tider timer-tjänsten inte kan stoppas och startas, är det acceptabelt men det är mindre effektivt att låta den här tjänsten köras hela tiden.

När återställnings tider timer-tjänsten med låg nivå upphör att gälla regelbundet, måste bindningen anropa systemfunktionen GUIX _gx_system_timer_expiration (0). Att anropa den här funktionen är med jämna mellanrum det som driver GUIX timer-tjänster på hög nivå.

**GX_TIMER_STOP**

Det här makrot anropas när GUIX inte längre behöver en periodisk timer (dvs. inga aktiva GUIX-timers körs). Om återställnings tider timer-tjänsten inte kan stoppas och startas, är det acceptabelt men är mindre effektivt att låta den här tjänsten köras hela tiden och definiera det här makrot för att göra ingenting.

**GX_SYSTEM_MUTEX_LOCK**

Det här makrot anropas av GUIX under kritiska kod avsnitt för att förhindra att en annan aktivitet än empting och ändrar gemensamma data strukturer, vilket kan orsaka skada. Det här makrot ska anropa en funktion som implementerar lämplig resurs låsnings tjänst för återställnings tider.

Om du aldrig använder några GUIX-API-tjänster utanför GUIX-tråden kan du definiera det här makrot för att göra ingenting.

**GX_SYSTEM_MUTEX_UNLOCK**

Det här makrot anropas i slutet av kritiska kod avsnitt och bör låsa upp GUIX-resursen med lämplig underliggande återställnings tider-tjänst. Om du aldrig använder några GUIX-API-tjänster utanför GUIX-tråden kan du definiera det här makrot för att göra ingenting.

**GX_SYSTEM_TIME_GET**

Det här makrot ska anropa en funktion som returnerar den aktuella system tiden är "system tickes", vilket vanligt vis är antalet timer-avbrott på låg nivå som har inträffat sedan systemet startades. Den här tjänsten används för att beräkna touch-pennans hastighet för gester för touch-ingångar. Signaturen för funktionen som anropas av det här makrot måste vara:

**ULONG *function_name*(void);**

**GX_CURRENT_THREAD**

Det här makrot anropas för att identifiera den tråd som körs för tillfället. Tjänsten som anropas av det här makrot måste returnera en Void *, vilket innebär att den datatyp som används av operativ systemet för att identifiera den aktuella körnings tråden måste omvandlas till void * för att returneras till GUX.

Ett fullständigt exempel på en allmän återställnings tider-bindning implementeras i det arkiverade gx_system_rtos_bind. h och gx_system_rtos_bind. c