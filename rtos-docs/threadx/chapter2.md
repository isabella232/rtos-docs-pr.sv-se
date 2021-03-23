---
title: Kapitel 2 – installation och användning av Azure återställnings tider ThreadX
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider ThreadX-kärnan med höga prestanda.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e1bf85d363b07c81f226d494107eae9ba18114a7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825455"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a>Kapitel 2 – installation och användning av Azure återställnings tider ThreadX

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider ThreadX-kärnan med höga prestanda.

## <a name="host-considerations"></a>Värd överväganden

Inbäddad program vara utvecklas vanligt vis på Windows-eller Linux-värddatorer (UNIX). När programmet har kompilerats, länkats och finns på värden laddas den ned till mål maskin varan för körning.

Normalt görs mål hämtningen från utvecklings verktygets fel sökare. När nedladdningen är klar ansvarar fel söknings programmet för att tillhandahålla mål körnings kontroll (gå till, stoppa, Bryt punkt osv.) samt åtkomst till minne och processor register.

De flesta utvecklings verktyg för fel sökning kommunicerar med mål maskin varan via OCD-anslutningar (on-chip debug) som JTAG (IEEE 1149,1) och fel söknings läge för bakgrunden (BDM). Fel sökare kommunicerar också med mål maskin vara via ICE-anslutningar (In-Circuit emulation). Både OCD-och ICE-anslutningar ger robusta lösningar med minimalt intrång på den inhemske program varan.

För resurser som används på värden levereras käll koden för ThreadX i ASCII-format och kräver cirka 1 MB utrymme på värddatorns hård disk.

## <a name="target-considerations"></a>Mål överväganden

ThreadX kräver mellan 2 KByte och 20 KB skrivskyddat minne (ROM) på målet. Det kräver också ytterligare 1 till 2 KByte av målets RAM-minne (Random Access Memory) för ThreadX system stack och andra globala data strukturer.

För timer-relaterade funktioner som tids gränser för tjänst anrop, tids segmentering och programtimers för att fungera, måste den underliggande mål maskin varan tillhandahålla en regelbunden avbrotts källa. Om processorn har den här funktionen används den av ThreadX. Annars, om mål processorn inte har möjlighet att generera ett periodiskt avbrott måste användarens maskin vara tillhandahålla den. Installationen och konfigurationen av det tidsinställda avbrottet finns vanligt vis i ***tx_initialize_low_level*** sammansättnings filen i ThreadX-distributionen.

> [!NOTE]
> *ThreadX fungerar fortfarande även om ingen återkommande timer-källa för avbrott är tillgänglig. Men ingen av de timer-relaterade tjänsterna fungerar.*

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider-ThreadX kan hämtas från vår offentliga käll kods lagrings plats på <https://github.com/azure-rtos/threadx/> .

Följande är en lista över flera viktiga filer i lagrings platsen.

| Sökväg | Beskrivning |
|------------------- | ----------- |
| **tx_api. h**                      | C-huvudfilen som innehåller alla system likställda, data strukturer och tjänst prototyper.                                                             |
| **tx_port. h**                     | C-huvudfil som innehåller alla utvecklings verktyg och targetspecific data definitioner och strukturer.                                                 |
| **demo_threadx. c**                | C-fil som innehåller ett litet demo program.                                                                                                       |
| **TX. a (eller TX. lib)**              | Binär version av ThreadX C-biblioteket som distribueras med *standard* paketet.                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
>*Alla fil namn är i gemener. Med den här namngivnings konventionen blir det enklare att konvertera kommandon till plattformar med Linux (UNIX).*

## <a name="threadx-installation"></a>ThreadX-installation

ThreadX installeras genom att klona GitHub-lagringsplatsen till den lokala datorn. Följande är en typisk syntax för att skapa en klon av ThreadX-lagringsplatsen på din dator.

```c
    git clone https://github.com/azure-rtos/threadx
```

Alternativt kan du ladda ned en kopia av lagrings platsen med hjälp av knappen Ladda ned på GitHub-huvud sidan.

Du hittar också instruktioner för att skapa ThreadX-biblioteket på den första sidan i online-lagringsplatsen.

> [!NOTE]
> * Program varan behöver åtkomst till biblioteks filen ThreadX (vanligt vis **TX. a** eller **TX. lib**) och C include-filerna **_tx_api. h_* _ och _*_tx_port. h_*_. Detta åstadkommer du genom att ange lämplig sökväg för utvecklingsverktyg eller genom att kopiera filerna till program utvecklingen area._

## <a name="using-threadx"></a>Använda ThreadX

Om du vill använda ThreadX måste program koden innehålla ***tx_api. h** _ under kompileringen och länka med ThreadX för kör tids biblioteket _*_TX. a_*_ (eller _ *_TX. lib_* *).

Det krävs fyra steg för att bygga ett ThreadX-program.

1. Inkludera filen ***tx_api. h*** i alla filer som använder ThreadX Services eller data strukturer.

1. Skapa standard C *-funktionen **main** _. Den här funktionen måste slutligen anropa _ *_tx_kernel_enter_** för att starta ThreadX. Programspecifik initiering som inte omfattar ThreadX kan läggas till innan du anger kärnan.

      > [!IMPORTANT]
      > * ThreadX-inmatnings funktionen ***tx_kernel_enter** _ returnerar inte. Se därför till att inte placera några bearbetnings-eller funktions anrop efter it._

1. Skapa funktionen ***tx_application_define*** . Det är här som de ursprungliga system resurserna skapas. Exempel på system resurser är trådar, köer, minnesmoduler, händelse flaggor grupper, mutexer och semaforer.

1. Kompilera program källan och länka med ThreadX körnings bibliotekets ***TX. lib***. Den resulterande bilden kan laddas ned till målet och köras!

## <a name="small-example-system"></a>Litet exempel system

I det lilla exempel systemet i bild 1 visas skapandet av en enskild tråd med prioritet 3. Tråden körs, ökar en räknare och sedan vilo läge för ett klock streck.
Den här processen fortsätter för alltid.

```c
#include "tx_api.h"
unsigned long my_thread_counter = 0;
TX_THREAD my_thread;
main( )
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter( );
}
void tx_application_define(void *first_unused_memory)
{
    /* Create my_thread! */
    tx_thread_create(&my_thread, "My Thread",
    my_thread_entry, 0x1234, first_unused_memory, 1024,
    3, 3, TX_NO_TIME_SLICE, TX_AUTO_START);
}
void my_thread_entry(ULONG thread_input)
{
    /* Enter into a forever loop. */
    while(1)
    {
        /* Increment thread counter. */
        my_thread_counter++;
        /* Sleep for 1 tick. */
        tx_thread_sleep(1);
    }
}
```

**BILD 1. Mall för program utveckling**

Även om det här är ett enkelt exempel ger det en lämplig mall för verklig program utveckling.

## <a name="troubleshooting"></a>Felsökning

Varje ThreadX-port levereras med ett demonstrations program. Det är alltid en bra idé att först se till att demonstrations systemet körs, antingen på faktiskt mål maskin vara eller simulerad miljö.

Om demonstrations systemet inte körs korrekt är följande fel söknings tips.

1. Ta reda på hur mycket av demonstrationen som körs.
1. Öka stack storlekarna (detta är mer viktigt i den faktiska program koden än för demonstrationen).
1. Återskapa ThreadX-biblioteket med TX_ENABLE_STACK_CHECKING definierat. Detta aktiverar den inbyggda ThreadX stack-kontrollen.
1. Kringgå tillfälligt eventuella nyligen gjorda ändringar för att se om problemet försvinner eller ändras. Sådan information bör vara användbar för support tekniker.

Följ de procedurer som beskrivs i "[kund Support Center](about-this-guide.md#customer-support-center)" för att skicka den information som samlas in från fel söknings stegen.

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ när du skapar ThreadX-biblioteket och programmet med ThreadX. Alternativen nedan kan definieras i program källan, på kommando raden eller i filen ***tx_user. h*** include.

> [!IMPORTANT]
> * Alternativ som definieras i ***tx_user. h** _ används endast om program-och ThreadX-biblioteket har skapats med _ *TX_INCLUDE_USER_DEFINE_FILE** definierat.*

### <a name="smallest-configuration"></a>Minsta konfiguration

För den minsta tecken storleken bör följande konfigurations alternativ för ThreadX anses vara (i avsaknad av alla andra alternativ).

```c
TX_DISABLE_ERROR_CHECKING
TX_DISABLE_PREEMPTION_THRESHOLD
TX_DISABLE_NOTIFY_CALLBACKS
TX_DISABLE_REDUNDANT_CLEARING
TX_DISABLE_STACK_FILLING
TX_NOT_INTERRUPTABLE
TX_TIMER_PROCESS_IN_ISR
```

### <a name="fastest-configuration"></a>Snabbast konfiguration

För den snabbaste körningen har samma konfigurations alternativ som används för den minsta konfigurationen, men med dessa alternativ beaktas även.

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

[Detaljerade konfigurations alternativ](#detailed-configuration-options) beskrivs.

### <a name="global-time-source"></a>Global tids källa

För andra Microsoft Azure återställnings tider-produkter (FileX, NetX, GUIX, USBX osv.) definierar ThreadX antalet ThreadX timer-Tick som motsvarar en sekund. Andra uppfyller sina tids krav baserat på denna konstant. Som standard är värdet 100, vilket förutsätter ett periodiskt avbrott i 10ms. Användaren kan åsidosätta det här värdet genom att definiera TX_TIMER_TICKS_PER_SECOND med det önskade värdet i ***tx_port. h*** eller i IDE-eller kommando raden.

### <a name="detailed-configuration-options"></a>Detaljerade konfigurations alternativ

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

När det här alternativet är definierat aktiverar det här alternativet insamling av prestanda information i byte-pooler. Som standard är det här alternativet inte definierat.

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

När det här alternativet är definierat aktiverar det här alternativet insamling av prestanda information i byte-pooler. Som standard är det här alternativet inte definierat.

**TX_DISABLE_ERROR_CHECKING**

Hoppar över grundläggande fel kontroll av tjänst anrop. När den är definierad i program källan är all grundläggande parameter fel kontroll inaktive rad. Detta kan förbättra prestandan med så mycket som 30% och kan också minska bild storleken.

> [!NOTE]
> *Det är bara säkert att inaktivera fel kontrollen om programmet kan vara absolut garantera att alla indataparametrar alltid är giltiga under alla omständigheter, inklusive indataparametrar härledda från externa ingångar. Om ogiltiga indata har angetts i API: et med fel kontrollen inaktive rad, är det resulterande beteendet odefinierat och kan leda till minnes skada eller system krasch.*

> [!NOTE]
> *ThreadX API-retur värden påverkas inte genom inaktive ring av fel kontroll visas i fetstil i avsnittet "retur värden" i varje API-beskrivning i kapitel 4. Retur värden i fet stil är ogiltiga om fel kontrollen har inaktiverats med alternativet TX_DISABLE_ERROR_CHECKING.*

**TX_DISABLE_NOTIFY_CALLBACKS**

När det här alternativet är definierat inaktive ras aviserings återanrop för olika ThreadX-objekt. Genom att använda det här alternativet minskar du kodens storlek och förbättrar prestandan. Som standard är det här alternativet inte definierat.

**TX_DISABLE_PREEMPTION_THRESHOLD**

När det här alternativet är definierat inaktive ras avstängningen-tröskelvärdet, vilket minskar kod storleken och ökar prestandan. Naturligtvis är avstängningen-tröskeln inte längre tillgängliga. Som standard är det här alternativet inte definierat.

**TX_DISABLE_REDUNDANT_CLEARING**

När den är definierad tas logiken bort för att initiera ThreadX globala C-datastrukturer till noll. Detta bör endast användas om kompilatorns initierings kod anger alla oinitierade C globala data till noll. Genom att använda det här alternativet minskar du kodens storlek och förbättrar prestandan under initieringen. Som standard är det här alternativet inte definierat.

**TX_DISABLE_STACK_FILLING**

När det här alternativet är definierat inaktive ras 0xEF-värdet i varje byte av varje tråds stack när de skapas. Som standard är det här alternativet inte definierat.

**TX_ENABLE_EVENT_TRACE**

När det är definierat aktiverar ThreadX händelse insamlings koden för att skapa en TraceX-spårningssession.

**TX_ENABLE_STACK_CHECKING**

När det är definierat aktiverar ThreadX körning av stack-kontroll, vilket innefattar analys av hur mycket stack som har använts och granskning av data mönster "avgränsningar" före och efter stackområdet. Om ett stack fel upptäcks, anropas den registrerade program stackens fel hanterare. Det här alternativet resulterar i en något ökad omkostnader och kod storlek. Läs ***tx_thread_stack_error_notify*** API-funktionen för mer information. Som standard är det här alternativet inte definierat.

**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**

När det är definierat aktiverar insamling av prestanda information på händelse flaggor grupper. Som standard är det här alternativet inte definierat.

**TX_INLINE_THREAD_RESUME_SUSPEND**

När det här alternativet har definierats förbättrar ThreadX ***tx_thread_resume** _ och _ *_tx_thread_suspend_** API-anrop via kod i rad. Detta ökar kod storleken men förbättrar prestandan för dessa två API-anrop.

**TX_MAX_PRIORITIES**

Definierar prioritets nivåer för ThreadX. Giltiga värden är mellan 32 och 1024 (inklusive) och *måste* vara jämnt delbar med 32. Om antalet tillåtna nivåer ökar ökar RAM-användningen med 128 byte för varje grupp med 32 prioriteter. Det finns dock bara en försumbar effekt på prestanda. Som standard är det här värdet inställt på 32 prioritets nivåer.

**TX_MINIMUM_STACK**

Definierar den minsta stack storleken (i byte). Den används för fel kontroll när trådar skapas. Standardvärdet är port-Specific och finns i ***tx_port. h***.

**TX_MISRA_ENABLE**

När det är definierat använder ThreadX MISRA C-kompatibla konventioner. Mer information finns i  ***ThreadX_MISRA_Compliance.pdf*** .

**TX_MUTEX_ENABLE_PERFORMANCE_INFO**

När det är definierat aktiverar insamling av prestanda information på mutexer. Som standard är det här alternativet inte definierat.

**TX_NO_TIMER**

När det är definierat är ThreadX timer-logiken helt inaktive rad. Detta är användbart i de fall där ThreadX timer-funktioner (tråd ström spar läge, API-tidsgräns, tids segmentering och program timers) inte används. Om **TX_NO_TIMER** anges måste alternativet **TX_TIMER_PROCESS_IN_ISR** också definieras.

**TX_NOT_INTERRUPTABLE**

När det här är definierat försöker ThreadX inte minimera avbrotts utelåsnings tiden. Detta resulterar i snabbare körning men ökar snabbt avbrotts utelåsnings tiden.

**TX_QUEUE_ENABLE_PERFORMANCE_INFO**

När det är definierat aktiverar insamling av prestanda information i köer. Som standard är det här alternativet inte definierat.

**TX_REACTIVATE_INLINE**

När det här definieras utförs återaktivering av ThreadX timers infogade timers i stället för att använda ett funktions anrop. Detta förbättrar prestandan, men ökar kod storleken något. Som standard är det här alternativet inte definierat.

**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**

När det är definierat aktiverar insamling av prestanda information för semaforer. Som standard är det här alternativet inte definierat.

**TX_THREAD_ENABLE_PERFORMANCE_INFO**

När det är definierat aktiverar insamling av prestanda information på trådar. Som standard är det här alternativet inte definierat.

**TX_TIMER_ENABLE_PERFORMANCE_INFO**

När det är definierat aktiverar insamling av prestanda information för timers. Som standard är det här alternativet inte definierat.

**TX_TIMER_PROCESS_IN_ISR**

När det här alternativet är definierat elimineras den interna systemets timer-tråd för ThreadX. Detta resulterar i bättre prestanda vid timer-händelser och mindre RAM-krav eftersom timer-stacken och kontroll blocket inte längre behövs. Om du använder det här alternativet flyttas all timer för förfallo tid till ISR-nivå. Som standard är det här alternativet inte definierat.

> [!NOTE]
> *Tjänster som tillåts från timers är kanske inte tillåtna från ISR: er och kan därför inte användas när du använder det här alternativet.*

**TX_TIMER_THREAD_PRIORITY**

Definierar prioriteten för den interna ThreadX system timer-tråden. Standardvärdet är Priority 0, högst prioritet i ThreadX. Standardvärdet är definierat i ***tx_port. h***.

**TX_TIMER_THREAD_STACK_SIZE**

Definierar stack storleken (i byte) för den interna ThreadX system timer-tråden. Den här tråden bearbetar alla tråd Ströms begär Anden och alla tids gränser för tjänst anrop. Dessutom anropas alla rutiner för återanrop från program timer från den här kontexten. Standardvärdet är port-Specific och finns i ***tx_port. h***.

## <a name="threadx-version-id"></a>ThreadX versions-ID

Programmerare kan hämta ThreadX-versionen från undersökningen av filen ***tx_port. h** _. Dessutom innehåller den här filen även en versions historik för motsvarande port. Program varan kan hämta ThreadX-versionen genom att undersöka den globala strängen _ * _tx_version_id * *.
