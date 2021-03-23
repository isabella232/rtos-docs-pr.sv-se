---
title: Förstå Azure återställnings tider-ThreadX
description: Azure ThreadX är ett avancerat operativ system i real tid (återställnings tider) som utformats specifikt för djupt inbäddade program.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: acee58d9c48cb7a66993aaa5dc4a565dfe96234d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827345"
---
# <a name="overview-of-azure-rtos-threadx"></a>Översikt över Azure återställnings tider-ThreadX

Azure återställnings tider-ThreadX är Microsofts avancerade industriella klass Real-Time operativ system (återställnings tider) utformade särskilt för djupt inbäddade, real tids-och IoT-program. Azure återställnings tider ThreadX innehåller avancerade funktioner för schemaläggning, kommunikation, synkronisering, timer, minnes hantering och avbrotts hantering. Dessutom har Azure återställnings tider-ThreadX många avancerade funktioner, inklusive picokernel™ arkitektur, avstängningen tröskel™ schemaläggning, händelse länkning,™ körnings profilering, prestanda mått och spårning av system händelser. Med Azure återställnings tider ThreadX är det idealiska valet för de mest krävande inbäddade programmen, tillsammans med dess överlägsna lättanvända. Från och med 2017 har Azure återställnings tider ThreadX över 6 200 000 000-distributioner, i en mängd olika produkter, inklusive konsument enheter, medicin elektronik och industriell kontroll utrustning.

## <a name="api-protocols"></a>API-protokoll

### <a name="azure-rtos-threadx-api"></a>Azure återställnings tider ThreadX-API

* Intuitiv och konsekvent API
* Substantiv-namn konvention för verb
* Alla API: er har ledande *TX_* för att enkelt identifiera som Azure återställnings tider ThreadX
* Blockering av API: er har valfri tråd-timeout
* Många API: er är direkt tillgängliga från program ISR: er

### <a name="azure-rtos-threadx-services"></a>Azure återställnings tider ThreadX-tjänster

* Skapa dynamisk tråd
* Inga begränsningar för antalet trådar
* API: er för huvud tråd är:
  * tx_thread_create
  * tx_thread_delete
  * tx_thread_preemption_change
  * tx_thread_priority_change
  * tx_thread_relinquish
  * tx_thread_reset
  * tx_thread_resume
  * tx_thread_sleep
  * tx_thread_suspend
  * tx_thread_terminate
  * tx_thread_wait_abort
* Ytterligare information och prestanda-API: er

### <a name="message-queues"></a>Meddelande köer

* Skapa dynamisk kö
* Inga begränsningar för antalet köer
* Meddelanden som kopierats efter värde (eller referens via pekare)
* Meddelande storlekar från 1 till 16 32-bitars ord
* Valfri tråd upphängning på Tom och fullständig
* Valfri tids gräns vid alla avbrott
* API: er för huvud meddelande kön inkluderar:
  * tx_queue_create
  * tx_queue_delete
  * tx_queue_flush
  * tx_queue_front_send
  * tx_queue_receive
  * tx_queue_send_notify
* Ytterligare information och prestanda-API: er

### <a name="counting-semaphores"></a>Inventering av semaforer

* Skapa dynamisk semafor
* Inga begränsningar för antalet semaforer
* 32-bitars beräknings semaforer (0 till 4 294 967 295)
* Stöder konsument-eller resurs skydd
* Valfri tråd som avbrytas när semaforen är otillgänglig
* Valfri tids gräns vid alla avbrott
* API: er för huvud semaforen är:
  * tx_semaphore_create
  * tx_semaphore_delete
  * tx_semaphore_get
  * tx_semaphore_put
  * tx_semaphore_put_notify
* Ytterligare information och prestanda-API: er

### <a name="mutexes"></a>Mutexer

* Skapa dynamisk mutex
* Inga begränsningar för antalet mutexer
* Nästlat resurs skydd stöds
* Arv av valfria prioritet stöds
* Valfri tråd som avbrytas när mutex inte är tillgänglig
* Valfri tids gräns vid alla avbrott
* API: er för huvudsakliga mutex är:
  * tx_mutex_create
  * tx_mutex_delete
  * tx_mutex_get
  * tx_mutex_put
* Ytterligare information och prestanda-API: er

### <a name="event-flags"></a>Händelse flaggor

* Skapa grupp för dynamisk händelse flagga
* Inga begränsningar för antalet händelse flagg grupper
* Synkronisering av en tråd eller flera trådar
* Atomisk get och Clear stöds
* Valfri flertrådstestning SUS pension vid och/eller uppsättning av händelser
* Valfri tids gräns vid alla avbrott
* API: er för huvud händelse flagga inkluderar:
  * tx_event_flags_create
  * tx_event_flags_delete
  * tx_event_flags_get
  * tx_event_flags_set
  * tx_event_flags_set_notify
* Ytterligare information och prestanda-API: er

### <a name="block-memory-pools"></a>Blockera minnes pooler

* Skapa dynamisk block pool
* Inga begränsningar för antalet block pooler
* Det går inte att använda storleks gränser för block med fast storlek eller storlek på poolen
* Snabbast möjlig minnesallokering/-plats
* Valfri tråd upphängning i tom pool
* Valfri tids gräns vid alla avbrott
* API: er för huvudblockerad pool inkluderar:
  * tx_block_pool_create
  * tx_block_pool_delete
  * tx_block_allocate
  * tx_block_release
* Ytterligare information och prestanda-API: er

### <a name="byte-memory-pools"></a>Byte-minnes pooler

* Generering av dynamisk byte-pool
* Inga begränsningar för antalet byte pooler
* Inga gränser för byte-Poolens storlek
* Mest flexibla minnesallokering/frigörning av variabel längd
* Stöd för allokerings storlek stöds
* Valfri tråd upphängning i tom pool
* Valfri tids gräns vid alla avbrott
* API: er för main byte-pool omfattar:
  * tx_byte_pool_create
  * tx_byte_pool_delete
  * tx_byte_allocate
  * tx_byte_release
* Ytterligare information och prestanda-API: er

### <a name="application-timers"></a>Program timers

* Generering av dynamiskt timer
* Inga begränsningar för antalet timers
* Regelbundna eller ensidiga timers stöds
* Periodiska timers kan ha olika inledande förfallo värde
* Ingen sökning efter timer-aktivering eller inaktive ring
* Alla timers drivs från ett avbrott för maskin vara
* API: er för huvudsakliga timer är:
  * tx_timer_create
  * tx_timer_delete
  * tx_timer_activate
  * tx_timer_change
  * tx_timer_deactivate
* Ytterligare information och prestanda-API: er

### <a name="azure-rtos-threadx-core-scheduler"></a>Azure återställnings tider ThreadX Core Scheduler

* Minimalt 2KB FLASH, 1 KB RAM-minne
* Snabb, under-mikroandra kontext-växel
* Fullständigt deterministisk oberoende av antalet trådar
* Prioriterad, fullständig ogiltiga-schemaläggning
* 32 standard prioritets nivåer, alternativt upp till 1024 nivåer
* Samarbets schemaläggning inom prioritets nivå (FIFO)
* Avstängningen-tröskel teknik
* Valfria timer-tjänster, inklusive:
  * Valfri Time-slice per tråd
  * Valfri tids gräns vid all blockering
  * API: er kräver tids gräns för maskin vara
* Körnings profilering
* Spårning på system nivå
* Säkerhet certifierat för många standarder

## <a name="most-deployed-rtos"></a>Mest distribuerade återställnings tider

Azure återställnings tider ThreadX har över 6 200 000 000 distributioner över hela världen, enligt ledande M2M marknads informations företag, VDC Research. Populariteten av Azure återställnings TIDERe ThreadX är en vittnar till dess tillförlitlighet, kvalitet, storlek, prestanda, avancerade funktioner, enkel användning och övergripande tids till marknads fördelar.

> *"Vi har följt den växande inriktning av THREADX på de trådlösa och IoT-marknaderna, sedan företagets befunnits och är alltmer imponerade av den omfattande branschens införande av THREADX."* – Christer Rommel, Executive Vice VD, VDC Research

## <a name="small-footprint"></a>Små avtryck

Azure återställnings tider ThreadX kräver ett remarkably litet 2KB-instruktions områden och 1 KB RAM-minne för sitt minsta utrymme. Detta beror på en stor del av den icke-skiktade picokernel™ arkitektur och automatisk skalning. Automatisk skalning innebär att endast de tjänster (och den stödda infrastrukturen) som används av programmet ingår i den slutliga avbildningen vid länk tillfället.

Här är några typiska egenskaper för Azure återställnings tider-ThreadX storlek:

|Azure återställnings tider ThreadX-tjänsten  |Normal storlek i byte  |
|---------|---------|
|Kärn tjänster (kräver) |2 000  |
|Queue Services  |900  |
|Event flagga-tjänster  |900  |
|Semafor-tjänster  |450  |
|Mutex-tjänster  |1 200  |
|Blockera minnes tjänster  |550  |
|Byte minnes tjänster  |900  |

## <a name="fast-execution"></a>Snabb körning

Azure återställnings tider ThreadX uppnår en under-mikroandra kontext växel på de flesta populära processorerna och är betydligt snabbare än andra kommersiella RTOSes. Förutom att vara snabba är Azure återställnings tider-ThreadX också mycket deterministisk. Den ger samma snabba prestanda om det finns 200 trådar klara eller bara en.

Här följer några typiska prestanda egenskaper för Azure återställnings tider ThreadX:

* Snabb start: Azure återställnings tider ThreadX startar på mindre än 120 cykler.
* Valfri borttagning av grundläggande fel kontroll: Basic Azure återställnings tider ThreadX-fel kontrollen kan hoppas över vid kompilering. Detta kan vara användbart när program koden verifieras och inte längre kräver fel kontroll på varje parameter. Observera att detta kan göras på en-enhet i stället för hela systemet.
* Picokernel™ design: tjänsterna är inte skiktade på varandra, vilket eliminerar onödiga funktions anrop.
* * Optimerad avbrotts bearbetning: endast redovisnings registreringar sparas/återställs vid ISR-in-/utförsel, om inte avstängningen krävs.
* Optimerad API-bearbetning:

    |Azure återställnings tider ThreadX-tjänsten  |Tjänsttid i mikrosekunder *  |
    |---------|---------|
    |Tråden pausar  |0,6  |
    |Återuppta tråd  |0,6  |
    |Köa sändning  |0.3  |
    |Ta emot kön  |0.3  |
    |Hämta semafor  |0,2  |
    |Skicka semafor  |0,2  |
    |Kontext växel  |0,4  |
    |Avbrotts svar  |0,0 – 0,6  |

    **Prestanda siffror som baseras på en typisk processor som körs på 200MHz*.

## <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a>Förcertifierat av TUV och UL till många säkerhets standarder

Azure återställnings tider ThreadX och Azure återställnings tider ThreadX SMP har certifierats av SGS-TUV-Saar för användning i säkerhets kritiska system, enligt IEC-61508 SIL 4, IEC-62304 SW säkerhets klass C, ISO 26262 ASIL D och EN 50128. Certifieringen bekräftar att Azure återställnings tider ThreadX och Azure återställnings tider ThreadX SMP kan användas i utvecklingen av säkerhetsrelaterad program vara för den högsta säkerhets integritets nivån för IEC-61508, IEC-62304, ISO 26262 och EN 50128 för "fungerande säkerhet för elektriska, elektroniska och programmerbara elektroniskt säkerhetsrelaterade system". SGS – TUV Saar, som bildas genom ett gemensamt företag i Tyskland SGS-Group och TUV Saarland, har blivit det ledande ackrediterade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad program vara för säkerhetsrelaterade system i hela världen. Den industriella säkerhets standarden IEC 61508 och alla standarder som är härledda från IT, inklusive IEC-62304, ISO 26262 och EN 50128, används för att säkerställa den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, process kontroll system, industriella maskiner, bil-och järnvägs styrnings system.

:::image type="content" source="media/overview-threadx/partener-logo-sgs-tuv-saar-2.png" alt-text="SGS TUV SAAR-certifiering":::

Azure återställnings tider ThreadX och Azure återställnings tider ThreadX SMP har erkänts av UL för att följa UL 60730-1 bilaga H, CSA E60730-1 bilaga H, IEC 60730-1 bilaga H, UL 60335-1 Bilaga R, IEC 60335-1 Bilaga R och UL 1998 säkerhets standarder för program vara i programmerbara komponenter. UL är ett globalt, oberoende, säkerhets vetenskaps företag med mer än en Century av expertis som förnyar säkerhetslösningar, från det offentliga införandet av elektricitet till genombrott i hållbarhet, förnybar energi och Nanotechnology.

:::image type="content" source="media/overview-threadx/cru-logo-certification.png" alt-text="UL-certifiering":::

Artefakter (certifikat, säkerhets hand bok, test rapport osv.) som är associerade med TUV och UL-certifieringar är tillgängliga för försäljning.

## <a name="eal4-common-criteria-security-certification"></a>EAL4 + gemensamma villkor säkerhets certifiering

Azure återställnings tider har uppnått säkerhets certifieringen EAL4 + Common Criteria. Målet för evalution (TOE) täcker Azure återställnings tider ThreadX, Azure återställnings tider NetX-Duo, Azure återställnings tider NetX Secure TLS och Azure återställnings tider NetX MQTT. Detta representerar de mest typiska IoT-protokollen som krävs av djupt inbäddade sensorer, enheter, yttre routrar och gatewayer.

:::image type="content" border="false" source="media/overview-threadx/eal-logo-certification.png" alt-text="EAL-certifiering":::

Den utvärderings funktion för IT-säkerhet som används för Azure återställnings tider Security-certifieringen är Brightsight BV och certifikat utfärdaren är SERTIT.

## <a name="simple-easy-to-use"></a>Enkel, lätt att använda

Azure återställnings tider-ThreadX är mycket enkelt att använda. Azure återställnings tider ThreadX-API: et är både intuitivt och mycket funktionellt. API-namnen består av riktiga ord och inte alfabetet soppor av förkortade namn som är så vanliga i andra återställnings tider-produkter. Alla Azure återställnings tider ThreadX-API: er har en ledande `tx_` och följer en namn konvention för substantiv-verb. Det finns dessutom en funktions konsekvens i hela API: et. Till exempel har alla API: er som pausas en valfri tids gräns som fungerar på samma sätt för API: er.

Det är enkelt att skapa ett Azure återställnings tider ThreadX-program. Programmet måste innehålla *tx_api. h*, anropa `tx_kernel_enter` från huvud, definiera `tx_application_define` funktionen och skapa en tråd, definiera funktionen för trådens start punkt och länka mot Azure återställnings tider ThreadX-biblioteket (vanligt vis *TX. a*).

Azure återställnings tider-ThreadX har också den högsta Caliber i dokumentationen som är tillgänglig. 

## <a name="advanced-technology"></a>Avancerad teknik

Azure återställnings tider ThreadX är en avancerad teknik vars viktigaste funktion är avstängningen-tröskelvärdet för schemaläggning. Den här funktionen är unik för Azure återställnings tider-ThreadX och har varit föremål för omfattande akademiska undersökningar. Se till exempel [schemaläggning Fixed-Priority uppgifter med tröskelvärdet avstängningen](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), av Yun Wang, Concordia University och manas Saksena, University of Pittsburgh.

Beakta funktionerna i Azure återställnings tider ThreadX:

* Fullständiga och omfattande multikörnings funktioner
  * Trådar, program timers, meddelande köer, inventering av semaforer, mutexer, händelse flaggor, block-och byte-lagringspooler
* Priority-Based schemaläggning av ogiltiga
* Prioriterad flexibilitet – upp till 1024 prioritets nivåer
* Samarbets schemaläggning
* Avstängningen-tröskel™ – unik för Azure återställnings tider-ThreadX, hjälper till att minska kontext byten och hjälpa till att garantera schedulability (per akademiska Research)
* Minnes skydd via Azure återställnings tider ThreadX-moduler
* Fullständigt deterministisk
* Händelse spårning – fånga senaste *n* system/program händelser
* Händelse länkning™ – registrera en programspecifik återanrops funktion för varje Azure återställnings tider ThreadX-kommunikation eller synkroniseringsobjekt
* Azure återställnings tider ThreadX-moduler med valfritt minnes skydd
* Run-Time prestanda mått
  * Antal trådar som återupptas
  * Antal tråd upphängningar
  * Antal preemptions för begärd tråd
  * Antal preemptions för asynkront tråd avbrott
  * Antal tråd prioritets versioner
  * Antal trådar som låser sig
* EPK (Execution Profile Kit)
* Separat avbrotts stack
* Run-Time stack-analys
* Optimerad bearbetning av tids avbrott

## <a name="multicore-support-amp--smp"></a>Stöd för flera kärnor (AMP & SMP)

Standard Azure återställnings tider-ThreadX används ofta i en asymmetrisk multiprocessering (AMP), där en separat kopia av Azure återställnings tider ThreadX och programmet (eller Linux) körs på varje kärna och kommunicerar med varandra via delat minne eller en kommunikations mekanism mellan processor, till exempel OpenAMP (Azure återställnings tider ThreadX stöder OpenAMP). Detta är den mest typiska konfigurationen för flera kärnor med Azure återställnings tider ThreadX och kan vara den mest effektiva om programmet kan läsa in processorerna effektivt.

För miljöer där inläsning av processorerna är mycket dynamiska är Azure återställnings tider ThreadX Symetric multi Processing (SMP) tillgängligt för följande processor familjer:

* ARM-Cortex-Ax
* ARM-Cortex-Rx
* ARM Cortex-A5x 64-bitars
* MIPS 34K, 1004K och interAptiv
* PowerPC
* Sammanfattnings båge HS
* x86

Azure återställnings tider ThreadX SMP utför dynamisk belastnings utjämning för *n* processorer och tillåter alla Azure återställnings tider ThreadX-resurser (köer, semaforer, händelse flaggor, minnesmoduler osv.) som kan nås av alla trådar på alla kärnor. Azure återställnings tider ThreadX SMP möjliggör hela Azure återställnings tider ThreadX-API: et på alla kärnor och introducerar följande nya API: er som gäller för SMP-åtgärder:

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Minnes skydd via Azure återställnings tider ThreadX-moduler

Med en tilläggs produkt som heter Azure återställnings tider ThreadX-moduler kan en eller flera program trådar paketeras i en "modul" som kan läsas in och köras dynamiskt (eller köras på plats) på målet.

Moduler aktiverar fält uppgradering, fel sökning och programpartitionering så att stora program bara tar upp det minne som behövs för aktiva trådar.

Moduler har också ett helt separat adress utrymme från Azure återställnings tider ThreadX. Detta gör att Azure återställnings tider-ThreadX kan placera minnes skydd (via MPU eller MMU) runt modulen så att oavsiktlig åtkomst utanför modulen inte kan skada någon annan program komponent.

## <a name="fastest-time-to-market"></a>Snabbast tid till marknad

Azure återställnings tider ThreadX är enkelt att installera, lära sig, använda, felsöka, verifiera, certifiera och underhålla. Det innebär att Azure återställnings tider ThreadX har varit det inledande återställnings tider för under de senaste sju föregående åren, enligt de inbäddade EMF-undersökningarna (Marketing deforecaster). Undersökningarna visar konsekvent att 70% av designerna med Azure återställnings tider-ThreadX får till gång till marknaden, vilket överskrider alla andra RTOSes.

Följande är orsaken till vår konsekventa tids till marknads fördel:

* Kvalitets dokumentation
* Fullständig käll kods tillgänglighet
* Lätt att använda API
* Omfattande och avancerad funktions uppsättning
* Omfattande integrerings verktyg från tredje part – särskilt IARs inbyggda Workbench™

## <a name="royalty-free"></a>Royalty kostnads fri

Det kostar inget att använda och testa käll koden och ingen kostnad för produktions licenser när de distribueras till förinstallerade enheter, men alla andra enheter behöver en enkel årlig licens.

## <a name="full-highest-quality-source-code"></a>Fullständig käll kod med högsta kvalitet

Från början är Azure återställnings tider-ThreadX utformad för att vara en återställnings tider med, distribuerad med fullständig C-källkod. Käll koden för Azure återställnings tider-ThreadX har angett kvalitet och enkel förståelse. Dessutom tillhandahåller konventionen om en funktion per fil för enkel käll navigering.

Azure återställnings tider-ThreadX följer strikta kodnings konventioner, inklusive kravet att varje rad C-kod har en meningsfull kommentar. Dessutom har Azure återställnings tider ThreadX-källan certifierats enligt de högsta standarderna.

## <a name="misra-compliant"></a>MISRA-kompatibel

Azure återställnings tider ThreadX och Azure återställnings tider ThreadX SMP resurs kod är MISRA-C:2004 och MISRA C:2012-kompatibel. MISRA C är en uppsättning programmerings rikt linjer för kritiska system med hjälp av programmeringsspråket C. De ursprungliga MISRA C-rikt linjerna var främst riktade mot fordonsbaserade program. men MISRA C är nu allmänt erkänd som giltig för alla säkerhets kritiska program. Azure återställnings tider ThreadX är kompatibelt med alla obligatoriska och obligatoriska regler för MISRA-C:2004 och MISRA C:2012.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Misra-certifiering":::

## <a name="supports-most-popular-architectures"></a>Har stöd för de flesta populära arkitekturerna

Azure återställnings tider-ThreadX körs på de flesta populära 32/64-bitars mikroprocessorer, färdiga, fullständigt testade och fullt stödda, inklusive följande:

* Analoga enheter: SHARC, Blackfin, CM4xx
* Andes Core: RISC-V
* Ambiqmicro: Apollo MCU
* ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitars/R4/R5, TrustZone ARMv8-M
* Takt: Xtensa, Diamond
* CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, WICED WiFi
* Cypress: RISC-V
* Kiseldioxid: eSi – RISC
* Infineon: XMC1000, XMC4000, TriCore
* Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10
* Mikrochip: AVR32, ARM7, ARM9, cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/sa, PIC24/PIC32
* Mikrohalv: RISC-V
* NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis cortex-M3/M4
* Renesas: SH, HS, V850, RX, RZ, synergieffekt
* Silicon Labs: EFM32
* Sammanfattning: båge 600, 700, båge EM, båg HS
* ST: STM32, ARM7, ARM9, cortex-M3/M4/M7
* TL: C5xxx, C6xxx, Stellaris, Sitara, tiva-C
* Wave-bearbetning: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5 K, microAptiv, interAptiv, proAptiv, M-Class
* Xilinx: mikroblixt, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

## <a name="supports-most-popular-tools"></a>Har stöd för de flesta populära verktygen

Azure återställnings tider ThreadX har stöd för de flesta populära inbäddade utvecklingsverktyg, inklusive IARs inbäddade Workbench-™, som också har den mest omfattande Azure återställnings tider-ThreadX kernel-medvetenhet tillgänglig. Ytterligare verktygs integrering inkluderar GNU (GCC), ARM DS-5/uVision®, gröna kullar MULTI®, vind flod Workbench™, fantasi Codescape, Renesas e2studio, meta-SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore och alla analoga enheter.
