---
title: Kapitel 3 – funktionella komponenter i Azure återställnings tider ThreadX
description: Det här kapitlet innehåller en beskrivning av Azure återställnings tider ThreadX-kärnan med höga prestanda från ett funktionellt perspektiv.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: aa66ad392171958e5d2cc765992fd1a9e41250a6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827372"
---
# <a name="chapter-3---functional-components-of-azure-rtos-threadx"></a>Kapitel 3 – funktionella komponenter i Azure återställnings tider ThreadX

Det här kapitlet innehåller en beskrivning av Azure återställnings tider ThreadX-kärnan med höga prestanda från ett funktionellt perspektiv. Varje funktionell komponent presenteras på ett lätt förståeligt sätt.

## <a name="execution-overview"></a>Översikt över körning

Det finns fyra typer av program körningar i ett ThreadX-program: initiering, tråd körning, avbrotts tjänst rutiner (ISR: er) och program timers.

Bild 2 visar varje typ av program körning. Mer detaljerad information om var och en av dessa typer finns i följande avsnitt i det här kapitlet.

### <a name="initialization"></a>Initiering

Som namnet antyder är det här den första typen av program körning i ett ThreadX program. Initieringen omfattar all program körning mellan processor återställning och start punkten i *tråden för tråd schemaläggning.*

### <a name="thread-execution"></a>Tråd körning

När initieringen är klar anger ThreadX sin tråd schema slinga. Schemaläggnings slingan söker efter en program tråd som är klar för körning. När en färdig tråd påträffas, överför ThreadX kontrollen till den. När tråden har slutförts (eller en annan tråd med högre prioritet blir klar) överförs körningen tillbaka till tråden för tråd schemaläggning för att hitta nästa högsta prioritets klara tråd.

Den här processen för att kontinuerligt köra och schemalägga trådar är den vanligaste typen av program körning i ThreadX-program.

### <a name="interrupt-service-routines-isr"></a>Avbryta service rutiner (ISR)

Avbrott är hörn stenen i real tids system. Utan avbrott är det mycket svårt att svara på ändringar i den externa världen i rimlig tid. Vid identifiering av ett avbrott sparar processorn viktig information om den aktuella program körningen (vanligt vis i stacken) och överför sedan kontrollen till ett fördefinierat program. Den här fördefinierade program arean kallas ofta för en avbrotts tjänst rutin. I de flesta fall uppstår avbrott under tråd körning (eller i tråden för tråd schemaläggning). Avbrott kan dock också uppstå i en körning av ISR eller en programtimer.

![Typer av program körningar](./media/user-guide/types-program-execution.png)

**BILD 2. Typer av program körningar**

### <a name="application-timers"></a>Program timers

Program timers liknar ISR: er, förutom att maskin varu implementeringen (vanligt vis ett enda periodiskt maskin varu avbrott används) är dold från programmet. Sådana timers används av program för att utföra tids gränser, periodiska och/eller övervaknings tjänster. Precis som ISR: er har programtimers ofta avbrott för tråd körning. Till skillnad från ISR: er kan programtimers dock inte avbryta varandra.

## <a name="memory-usage"></a>Minnesanvändning

ThreadX finns tillsammans med program programmet. Därför bestäms användningen av statiskt minne (eller fast minne) för ThreadX av utvecklingsverktygen. t. ex. kompilatorn, länkar och lokaliserare. Användning av dynamiskt minne (eller körnings minne) är direkt kontroll över programmet.

### <a name="static-memory-usage"></a>Statisk minnes användning

De flesta av utvecklingsverktygen delar program program avbildningen i fem grundläggande områden: *instruktion*, *konstant*, *initierade data*, oinitierade *data* och *system stack*. Bild 3 visar ett exempel på dessa minnes områden.

Det är viktigt att förstå att detta bara är ett exempel. Den faktiska statiska minnesmodulen är specifika för processor, utvecklingsverktyg och den underliggande maskin varan.

Instruktions avsnittet innehåller alla programmets processor instruktioner. Det här fältet är vanligt vis det största och finns ofta i ROM.

Det konstanta fältet innehåller olika kompilerade konstanter, inklusive strängar som definierats eller refereras till i programmet. Dessutom innehåller det här avsnittet "ursprunglig kopia" av det initierade data fältet. Under initierings processen för *minnes användnings* kompilatorn används den här delen av det fasta området för att konfigurera det initierade data området i RAM-minnet. Det fasta områdena följer vanligt vis instruktions ytan och finns ofta i ROM.

De initierade data och oinitierade data områdena innehåller alla globala och statiska variabler. Dessa områden finns alltid i RAM-minnet.

System stacken konfigureras vanligt vis direkt efter de initierade och oinitierade data områdena.

System stacken används av kompilatorn vid initieringen, sedan av ThreadX under initieringen och senare i ISR-bearbetning.

![Exempel på minnes området](./media/user-guide/memory-area-example.png)

**BILD 3. Exempel på minnes området**

### <a name="dynamic-memory-usage"></a>dynamiskt minne användning

Som tidigare nämnts är dynamisk minnes användning direkt kontroll av programmet. Kontroll block och minnes områden som är kopplade till stackar, köer och lagringspooler kan placeras var som helst i målets minnes utrymme. Detta är en viktig funktion eftersom den underlättar användningen av olika typer av fysiskt minne.

Anta till exempel att en mål maskin varu miljö har både snabbt minne och långsamt minne. Om programmet behöver extra prestanda för en tråd med hög prioritet kan kontroll blocket (TX_THREAD) och stacken placeras i det snabba minnes området, vilket kan förbättra dess prestanda avsevärt.

## <a name="initialization"></a>Initiering

Det är viktigt att förstå initierings processen. Den första maskin varu miljön konfigureras här. Det är dessutom där programmet får sin initiala personlighet.

> [!NOTE]
> *ThreadX försöker använda (närhelst det är möjligt) för det fullständiga utvecklings verktygets initierings process. Detta gör det enklare att uppgradera till nya versioner av utvecklingsverktyg i framtiden.*

### <a name="system-reset-vector"></a>System återställning, Vector

Alla mikroprocessorer har återställnings logik. När en återställning sker (antingen maskin-eller program vara) hämtas adressen till programmets start punkt från en specifik minnes plats. När Start punkten har hämtats, överför processorn kontrollen till den platsen. Program start punkten skrivs vanligt vis på det inbyggda sammansättnings språket och tillhandahålls vanligt vis av utvecklingsverktyg (i minst mall-formulär). I vissa fall medföljer en special version av Entry-programmet med ThreadX.

### <a name="development-tool-initialization"></a>Initiering av utvecklingsverktyg

När den lågnivå initieringen är klar styr du överföring till utvecklings verktygets övergripande initierings nivå. Detta är vanligt vis den plats där initierade globala och statiska C-variabler konfigureras. Kom ihåg att de ursprungliga värdena hämtas från det fasta nätverket. Den exakta initierings bearbetningen är en specifika utvecklingsverktyg.

### <a name="main-function"></a>huvud funktion

När distributions verktygets initiering är klar styr du överföring till den användare som anges av *huvud* funktionen. I det här läget styr programmet vad som händer härnäst. För de flesta program anropar main-funktionen bara *tx_kernel_enter*, som är posten i ThreadX. Program kan dock utföra förberedande bearbetning (vanligt vis för maskin varu initiering) innan du anger ThreadX.

> [!IMPORTANT]
> *Anropet till tx_kernel_enter returnerar inte, så placera ingen bearbetning efter det.*

### <a name="tx_kernel_enter"></a>tx_kernel_enter

Funktionen post samordnar initiering av olika interna ThreadX-datastrukturer och anropar sedan programmets definitions funktion ***tx_application_define***.

När ***tx_application_define*** returnerar överförs kontrollen till tråd schema slingan. Detta markerar slutet av initieringen.

### <a name="application-definition-function"></a>Program definitions funktion

Funktionen ***tx_application_define*** definierar alla inledande program trådar, köer, semaforer, mutexer, händelse flaggor, minnesmoduler och timers. Det är också möjligt att skapa och ta bort system resurser från trådar under normal användning av programmet. Alla inledande program resurser definieras dock här.

Funktionen ***tx_application_define** _ har en enda indataparameter och det är värt att nämna. Den _first tillgängliga * RAM-adressen är den enda Indataparametern till den här funktionen. Den används vanligt vis som utgångs punkt för inledande minnes tilldelning för körning av tråds tackor, köer och lagringspooler.

> [!NOTE]
> *När initieringen är klar kan endast en exekverande tråd skapa och ta bort system resurser, inklusive andra trådar. Därför måste du skapa minst en tråd under initieringen.*

### <a name="interrupts"></a>Avbrott

Avbrott lämnas inaktiverade under hela initierings processen. Om programmet på något sätt aktiverar avbrott kan oförutsägbart beteende uppstå. Bild 4 visar hela initierings processen, från system återställning genom programspecifik initiering.

## <a name="thread-execution"></a>Tråd körning

Schemaläggning och körning av program trådar är den viktigaste aktiviteten i ThreadX. En tråd definieras vanligt vis som ett halv oberoende program segment med ett dedikerat syfte. Den kombinerade bearbetningen av alla trådar gör ett program.

Trådar skapas dynamiskt genom att anropa ***tx_thread_create** _ under initiering eller under tråd körning. Trådar skapas antingen i ett _ready * eller i *pausat* läge.

![Initierings process](./media/user-guide/initialization-process.png)

**BILD 4. Initierings process**

### <a name="thread-execution-states"></a>Tråd körnings tillstånd

Att förstå olika bearbetnings tillstånd för trådar är en viktig ingrediens för att förstå hela den flertrådade miljön. I ThreadX finns det fem olika tråd tillstånd: *redo*, *pausad*, *körning*, *avslutad* och *slutförd*. Bild 5 visar över gångs diagrammet för tråd tillstånd för ThreadX.

![Över gång av tråd tillstånd](./media/user-guide/thread-state-transition.png)

**BILD 5. Över gång av tråd tillstånd**

En tråd är i ett *klart* tillstånd när det är klart att köras. En färdig tråd körs inte förrän den har den högsta prioritets tråden i klart läge. När detta inträffar kör ThreadX tråden, som sedan ändrar dess tillstånd till att *köra*.

Om en tråd med högre prioritet blir klar återgår den exekverande tråden tillbaka till ett *klart* tillstånd. Den nyligen färdiga tråden med hög prioritet körs sedan, vilket ändrar det logiska läget till att *köra*. Den här över gången mellan *färdiga* och *pågående* tillstånd sker varje gång tråden avstängningen inträffar.

Vid ett givet tillfälle är bara en tråd i ett *körnings* tillstånd. Detta beror på att en tråd i *körnings* tillstånd har kontroll över den underliggande processorn.

Trådar i tillståndet *Suspended* är inte tillgängliga för körning. Orsaker för att vara i *pausat* tillstånd är att skjuta upp tid, köa meddelanden, semaforer, mutexer, händelse flaggor, minne och Basic Thread SUS pension. När orsaken till avstängningen har tagits bort placeras tråden i ett *klart* tillstånd.

En tråd i ett *slutfört* tillstånd är en tråd som har slutfört bearbetningen och returnerats från inmatnings funktionen. Funktionen Entry anges när trådar skapas. En tråd i ett *slutfört* tillstånd kan inte köras igen.

En tråd är i ett *avslutat* tillstånd eftersom en annan tråd eller själva tråden anropade tjänsten *tx_thread_terminate* . En tråd i ett *avslutat* tillstånd kan inte köras igen.

> [!IMPORTANT]
> *Om du vill starta om en slutförd eller avslutad tråd måste du först ta bort tråden. Den kan sedan skapas på nytt och startas om.*

### <a name="thread-entryexit-notification"></a>Avisering om tråd post/avslutning

Vissa program kan vara fördelaktiga att meddelas när en viss tråd anges för första gången när den är klar eller avslutas. ThreadX tillhandahåller den här funktionen genom ***tx_thread_entry_exit_notifys*** tjänsten. Den här tjänsten registrerar en program meddelande funktion för en specifik tråd, som anropas av ThreadX när tråden börjar köras, slutförs eller avbryts. Efter att ha anropats kan program meddelande funktionen utföra programspecifik bearbetning. Det innebär vanligt vis att informerar en annan program tråd för händelsen via en primitiv ThreadX.

### <a name="thread-priorities"></a>Tråd prioriteter

Som tidigare nämnts är en tråd ett halv oberoende program segment med ett dedikerat syfte. Alla trådar skapas dock inte lika! Det dedikerade syftet med vissa trådar är mycket viktigare än andra. Den här heterogena typen av tråd prioritet är en Hallmark inbäddade real tids program.

ThreadX avgör en tråds betydelse när tråden skapas genom att tilldela ett numeriskt värde som representerar dess *prioritet*. Det maximala antalet ThreadX-prioriteter kan konfigureras från 32 till 1024 i steg om 32. Det faktiska maximala antalet prioriteringar bestäms av **TX_MAX_PRIORITIES** konstant vid kompilering av ThreadX-biblioteket. Om du har ett större antal prioriteter ökar inte bearbetnings kostnaderna avsevärt. För varje grupp med 32 prioritets nivåer krävs dock ytterligare 128 byte RAM-minne för att hantera dem. Till exempel kräver 32 prioritets nivåer 128 byte RAM, 64 prioritets nivåer kräver 256 byte RAM-minne, och prioritets nivåer för 96 kräver 384 byte RAM.

Som standard har ThreadX 32 prioritets nivåer, från 0 till prioritet 31. Numeriska mindre värden innebär högre prioritet. Prioritet 0 visar alltså högst prioritet, medan prioritet (**TX_MAX_PRIORITIES**-1) representerar den lägsta prioriteten.

Flera trådar kan ha samma prioritet som förlitar sig på samarbets schemaläggning eller tids segmentering. Dessutom kan tråd prioriteter ändras under körning.

### <a name="thread-scheduling"></a>Tråd schemaläggning

ThreadX schemalägger trådar utifrån deras prioritet. Den färdiga tråden med den högsta prioriteten körs först. Om flera trådar av samma prioritet är klara, körs de i ett första- *först-ut-* (FIFO)-sätt.

### <a name="round-robin-scheduling"></a>Round Robin-schemaläggning

ThreadX stöder schemaläggning med *resursallokering* för flera trådar med samma prioritet. Detta åstadkoms genom samarbets anrop till ***tx_thread_relinquish** _. Den här tjänsten ger alla andra redo trådar av samma prioritet en chans att köra innan _ *_tx_thread_relinquish_** anroparen körs igen.

### <a name="time-slicing"></a>Time-Slicing

*Tids segmentering* är en annan form av resursallokering-schemaläggning. Ett Time-slice anger det maximala antalet timer-Tick (timer-avbrott) som en tråd kan köras utan att processorn upprättas. I ThreadX är tids segmentering tillgänglig per tråd. Trådens tid-slice tilldelas när den skapas och kan ändras under körningen. När en Time-slice går ut får alla andra redo trådar med samma prioritets nivå möjlighet att köra innan den tidssegmenterade tråden körs igen.

En ny tråd-till-tråd-slice tilldelas en tråd när den har pausats, gör ett ThreadX tjänst anrop som gör att avstängningen eller är i sig själv att vara segmenterad.

När en tid-segmenterad tråd avbryts, återupptas den innan andra redo trådar med samma prioritet för resten av dess tids sektor.

> [!NOTE]
> *Om du använder tids segmentering blir det en liten del av systemets kostnader. Eftersom tids segmentering bara är användbart i fall där flera trådar delar samma prioritet, ska trådar som har en unik prioritet inte tilldelas en tid-sektor.*

### <a name="preemption"></a>Avstängningen

Avstängningen är processen för att tillfälligt avbryta en körnings tråd för en tråd med högre prioritet. Den här processen är osynlig för körnings tråden. När tråden med högre prioritet har slutförts överförs kontrollen tillbaka till den exakta platsen där avstängningen ägde rum. Det här är en mycket viktig funktion i real tids system, eftersom det underlättar snabba svar på viktiga program händelser. Även om det finns en mycket viktig funktion kan avstängningen också vara en källa till en mängd olika problem, inklusive effekter, överbelastning och prioritets version.

### <a name="preemption-thresholdtrade"></a>Avstängningen tröskel&trade;

För att under lätta för några av de avstängningena problemen ger ThreadX en unik och avancerad funktion som kallas *avstängningen-tröskel*.

Ett avstängningen-tröskelvärde gör det möjligt för en tråd att ange ett prioritets *tak* för inaktive ring av avstängningen. Trådar som har högre prioritet än taket är fortfarande tillåtna till preempt, medan dessa mindre än taket inte tillåts i preempt.

Anta till exempel att en tråd med prioritet 20 bara interagerar med en grupp trådar som har prioriteringar mellan 15 och 20. Under dess kritiska delar kan Trådens prioritet 20 ange dess avstängningen-tröskelvärde till 15, vilket hindrar avstängningen från alla trådar som den interagerar med. Detta tillåter fortfarande viktiga trådar (prioriteringar mellan 0 och 14) för att åsidosätta den här tråden under dess kritiska sektions bearbetning, vilket resulterar i mycket mer besvarad bearbetning.

Naturligtvis är det fortfarande möjligt för en tråd att inaktivera alla avstängningen genom att ange dess avstängningen-tröskelvärde till 0. Dessutom kan avstängningen-tröskelvärdet ändras under körning.

> [!NOTE]
> *Om du använder avstängningen-tröskelvärdet inaktive ras tids segmentering för den angivna tråden.*

### <a name="priority-inheritance"></a>Prioritera arv

ThreadX stöder även arv av valfria prioritet inom sina mutex-tjänster som beskrivs senare i det här kapitlet. Med prioriterad arv kan en tråd med lägre prioritet tillfälligt anta prioriteten för en tråd med hög prioritet som väntar på en mutex som ägs av tråden med lägre prioritet. Den här funktionen hjälper programmet att undvika icke-deterministiska prioritets versioner genom att eliminera avstängningen av mellanliggande tråd prioriteringar. Naturligtvis kan *avstängningen-tröskelvärdet* användas för att uppnå ett liknande resultat.

### <a name="thread-creation"></a>Skapa tråd

Program trådar skapas vid initiering eller vid körning av andra program trådar. Det finns ingen gräns för antalet trådar som kan skapas av ett program.

### <a name="thread-control-block-tx_thread"></a>Tråd kontroll block TX_THREAD

Egenskaperna för varje tråd finns i kontroll blocket. Den här strukturen definieras i filen ***tx_api. h*** .

En tråds kontroll block kan finnas var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

Att hitta kontroll blocket i andra områden kräver lite mer omsorg, precis som allt dynamiskt allokerat minne. Om ett kontroll block tilldelas i en C-funktion är det minne som är associerat med det en del av den anropande trådens stack. I allmänhet bör du undvika att använda lokal lagring för kontroll block eftersom när funktionen returnerar, så släpps hela det lokala variabel stack utrymmet – oavsett om en annan tråd använder den för ett kontroll block.

I de flesta fall är programmet Oblivious till innehållet i trådens kontroll block. Det finns dock vissa situationer, särskilt under fel sökning, där det är praktiskt att titta på vissa medlemmar. Följande är några av de mer användbara kontroll block medlemmarna.

**tx_thread_run_count** innehåller en räknare för antalet gånger som tråden har schemalagts. En ökande räknare anger att tråden schemaläggs och körs.

**tx_thread_state** innehåller den associerade Trådens tillstånd. Nedan visas de möjliga tråd tillstånden.

|  Tråd tillstånd   | Värde |
| --------------- | ------ |
| TX_READY       | 0x00 |
| TX_COMPLETED   | 0x01 |
| TX_TERMINATED  | protokollnumret 0x02 |
| TX_SUSPENDED   | (0x03) |
| TX_SLEEP       | (0x04) |
| TX_QUEUE_SUSP | (0x05) |
| TX_SEMAPHORE_SUSP | (0x06) |
| TX_EVENT_FLAG   | (0x07) |
| TX_BLOCK_MEMORY | (0x08) |
| TX_BYTE_MEMORY  | (0x09) |
| TX_MUTEX_SUSP   | (0x0D) |

> [!NOTE]
> *Naturligtvis finns det många andra intressanta fält i tråd kontroll blocket, inklusive stack pekare, Time-slice-värde, prioriteter osv. Användare är välkommen att granska kontroll Blocks medlemmar, men ändringar är strikt förbjudna!*

> [!IMPORTANT]
> Det finns *ingen som är lika med det "kör"-tillstånd som nämnts tidigare i det här avsnittet. Det är inte nödvändigt eftersom det bara finns en körnings tråd vid en specifik tidpunkt. Status för en körnings tråd* **TX_READY** också.

### <a name="currently-executing-thread"></a>Tråd som körs för närvarande

Som nämnts tidigare finns det bara en tråd som körs vid en specifik tidpunkt. Det finns flera sätt att identifiera den exekverande tråden på, beroende på vilken tråd som gör begäran.
Ett program segment kan hämta kontroll block adressen för tråden som körs genom att anropa ***tx_thread_identify***. Detta är användbart i delade delar av program kod som körs från flera trådar.

I fel söknings sessioner kan användare undersöka den interna ThreadX-pekaren ***_tx_thread_current_ptr***. Den innehåller kontroll block adressen för tråden som körs för tillfället. Om den här pekaren är NULL körs ingen program tråd. t. ex. väntar ThreadX i sin schemaläggnings slinga för att en tråd ska bli klar.

### <a name="thread-stack-area"></a>Tråds tack yta

Varje tråd måste ha en egen stack för att spara kontexten för den senaste körningen och kompilator användningen. De flesta C-kompilatorer använder stacken för att skapa funktions anrop och för att tillfälligt allokera lokala variabler. Bild 6 visar en typisk tråds stack.

Var en tråds tack finns i minnet är upp till programmet. Stack området anges när trådar skapas och kan placeras var som helst i mål adress utrymmet. Detta är en viktig funktion eftersom den gör det möjligt för program att förbättra prestanda för viktiga trådar genom att placera deras stack i höghastighets RAM-minne.

**Stack minnes området** (exempel)

![Typisk tråd stack](./media/user-guide/typical-thread-stack.png)

**BILD 6. Typisk tråd stack**

Hur stor stacken ska vara en av de mest vanliga frågorna om trådar. En tråds stack Area måste vara tillräckligt stor för att rymma värsta Falls funktion anrop, tilldelning av lokala variabler och att den senaste körnings kontexten sparas.

Den minsta stack storleken, **TX_MINIMUM_STACK**, definieras av ThreadX. En stack med den här storleken har stöd för att spara en tråds kontext och minsta funktions mängd funktions anrop och lokal variabel tilldelning.

För de flesta trådar är den minimala stack storleken för liten, och användaren måste kontrol lera det värsta tillåtna storleks kravet genom att undersöka funktion anrops kapsling och lokal variabel tilldelning. Naturligtvis är det alltid bättre att börja med ett större stack utrymme.

När programmet har felsökts är det möjligt att finjustera trådens stack storlek om minnet är begränsade. Ett favorit stick är att förinställda alla stack områden med ett enkelt identifierbart data mönster, t. ex. (0xEFEF) innan trådarna skapas. När programmet har genomgått en väl genomförd takt kan stack områdena undersökas för att se hur mycket stack som faktiskt användes genom att hitta området i stacken där data mönstret fortfarande är intakt. Bild 7 visar en förinställd stack för 0xEFEF efter en grundlig tråd körning.

**Stack minnes området** (ett annat exempel)

![Stack för inställning till 0xEFEF *](./media/user-guide/stack-preset.png)

**BILD 7. Stack för inställning till 0xEFEF**

> [!IMPORTANT]
> *Som standard initierar ThreadX varje byte av varje tråds tack med värdet 0xEF.*

### <a name="memory-pitfalls"></a>Fall GRO par för minne

Stack kraven för trådar kan vara stora. Därför är det viktigt att utforma programmet så att det har ett rimligt antal trådar. Dessutom måste en del försiktighet vidtas för att undvika överdriven stack användning i trådar. Rekursiva algoritmer och stora lokala data strukturer bör undvikas.

I de flesta fall orsakar en överflödad stack tråd körning till skadat minne (vanligt vis före) dess stack område. Resultatet är oförutsägbart, men oftast resulterar det i en naturlig ändring i program räknaren. Detta kallas ofta "att hoppa till ogräs". Det enda sättet att förhindra detta är naturligtvis att se till att alla tråds tackor är tillräckligt stora.

### <a name="optional-run-time-stack-checking"></a>Valfri stack kontroll på körnings tid

ThreadX ger möjlighet att kontrol lera varje tråds stack för att skadas under körnings tillfället. Som standard fyller ThreadX varje byte av tråd stackar med ett 0xEF-datamönster när de skapas. Om programmet bygger ThreadX-biblioteket med **TX_ENABLE_STACK_CHECKING** definierat undersöker ThreadX varje tråds stack för att skadas eftersom det pausas eller återupptas. Om stack skador identifieras anropar ThreadX programmets stack fel hanterings rutin som anges av anropet till **_tx_thread_stack_error_notify_*_ _. Annars, om ingen stack fel hanterare har angetts, kommer ThreadX att anropa den interna _* _ _tx_thread_stack_error_handler_** rutinen.

### <a name="reentrancy"></a>Återinträde

En av de verkliga Beauties i multitrådning är att samma C-funktion kan anropas från flera trådar. Detta ger bra kraft och hjälper också till att minska kod utrymmet. Det kräver dock att C-funktioner som anropas från flera trådar *återkallas.*

En reentrant-funktion lagrar i princip anroparens avsändar adress i den aktuella stacken och förlitar sig inte på globala eller statiska C-variabler som den tidigare har konfigurerat. De flesta kompilatorer placerar avsändar adressen i stacken. Programutvecklare behöver därför bara bekymra sig om användningen av *globala* och *statics*.

Ett exempel på en icke-reentrant funktion är funktionen String token ***strtok*** som finns i standard-C-biblioteket. Den här funktionen "Remembers" på föregående sträng pekare vid efterföljande anrop. Det gör detta med en statisk sträng pekare. Om den här funktionen anropas från flera trådar returnerar den förmodligen en ogiltig pekare.

### <a name="thread-priority-pitfalls"></a>Fall GRO par för tråd prioritet

Att välja tråd prioritet är en av de viktigaste aspekterna av multitrådning. Det är ibland mycket frestande att tilldela prioriteringar baserat på ett uppfattat begrepp i trådens betydelse snarare än att fastställa vad som krävs under körningen. Missbruk av tråd prioriteter kan strypa andra trådar, skapa prioritets version, minska bearbetnings bandbredden och göra programmets körnings beteende svårt att förstå.

Som nämnts tidigare tillhandahåller ThreadX en prioriterad algoritm för ogiltiga-schemaläggning. Trådar med lägre prioritet körs inte förrän det inte finns fler tråds trådar som är klara för körning. Om en tråd med högre prioritet alltid är klar körs inte trådarna med lägre prioritet. Det här villkoret kallas för *Thread effekter*.

De flesta tråd effekter problem upptäcks tidigt i debug och kan lösas genom att se till att trådar med högre prioritet inte körs kontinuerligt. Du kan också lägga till logik i programmet som gradvis höjer prioriteten för har-trådar tills de får en chans att köra.

En annan Pitfall som är kopplad till tråd prioriteter är *prioritets version*. Prioritets versionen sker när en tråd med högre prioritet har pausats eftersom en tråd med lägre prioritet har en nödvändig resurs. I vissa fall är det naturligtvis nödvändigt med två trådar av olika prioritet för att dela en gemensam resurs. Om de här trådarna är de enda som är aktiva, begränsas prioritets versionen av tiden av tiden som den lägre prioritets tråden innehåller resursen. Det här villkoret är både deterministiskt och helt vanligt. Men om trådar med mellanliggande prioritet blir aktiva under det här prioritets villkoret, är tiden för prioritets version inte längre deterministisk och kan orsaka ett program fel.

Det finns huvudsakligen tre distinkta metoder för att förhindra icke-deterministiska prioritets versioner i ThreadX. Först kan program prioritets valen och körnings beteendet utformas på ett sätt som förhindrar problem med prioritets versionen. För det andra kan trådar med lägre prioritet använda *avstängningen tröskel* för att blockera avstängningen från mellanliggande trådar medan de delar resurser med trådar med högre prioritet. Slutligen kan trådar som använder ThreadX mutex-objekt för att skydda system resurser använda sig av valfria mutex- *prioritets arv* för att eliminera icke-deterministiska prioritets versioner.

### <a name="priority-overhead"></a>Prioriterad omkostnader

Ett av de mest överblickade sätten att minska omkostnader i multitrådning är att minska antalet kontext byten. Som tidigare nämnts inträffar en kontext växel när körningen av en tråd med högre prioritet prioriteras över den som kör tråden. Det är ett exempel på att nämna att trådar med högre prioritet kan bli klara till följd av både externa händelser (t. ex. avbrott) och från tjänst anrop som görs av tråden som körs.

För att illustrera de effekter som Trådens prioritet har på kontext växlings omkostnader, förutsätter en tre tråd miljö med trådar som heter *thread_1*, *thread_2* och *thread_3*. Anta ytterligare att alla trådar är i ett tillstånd där SUS Pension väntar på ett meddelande. När thread_1 tar emot ett meddelande vidarebefordras det direkt till thread_2. Thread_2 vidarebefordrar sedan meddelandet till thread_3. Thread_3 tar bara bort meddelandet. När varje tråd bearbetar meddelandet går det tillbaka och väntar på ett annat meddelande.

Den bearbetning som krävs för att köra dessa tre trådar varierar kraftigt beroende på deras prioritet. Om alla trådar har samma prioritet inträffar en enda kontext växel innan varje tråd körs. Kontext växeln inträffar när varje tråd pausas i en tom meddelandekö.

Men om thread_2 högre prioritet än thread_1 och thread_3 är högre prioritet än thread_2, dubbleras antalet kontext byten. Detta beror på att en annan kontext växel förekommer i *tx_queue_send* tjänsten när den upptäcker att en tråd med högre prioritet nu är klar.

ThreadX avstängningen-tröskel kan undvika dessa extra kontext byten och tillåter fortfarande de tidigare nämnda prioritets valen. Detta är en viktig funktion eftersom den tillåter flera tråd prioriteringar under schemaläggningen, samtidigt som en del av den oönskade kontext växlingen mellan dem under tråd körningen elimineras.

### <a name="run-time-thread-performance-information"></a>Prestanda information för körnings tråd

ThreadX tillhandahåller valfria prestanda information för körnings tråd. Om ThreadX-biblioteket och programmet har skapats med **TX_THREAD_ENABLE_PERFORMANCE_INFO** definierat, samlar ThreadX in följande information.

Totalt antal för det övergripande systemet:

  - återuppta trådar

  - tråd upphängningar

  - preemptions för service samtal

  - Avbryt preemptions

  - prioritets version

  - Time-Slices

  - låser sig

  - tids gräns för trådar

  - avbrott i avbrott

  - inaktiva system returnerar

  - system som inte är inaktiva returneras

Totalt antal för varje tråd:

  - återupptagning

  - SUS pensioner

  - preemptions för service samtal

  - Avbryt preemptions

  - prioritets version

  - Time-Slices

  - tråden låser sig

  - tids gräns för trådar

  - avbrott i avbrott

Den här informationen är tillgänglig i körnings läge genom tjänsterna ***tx_thread_performance_info_get** _ och _ *_tx_thread_performance_system_info_get_* *. Information om tråd prestanda är användbar för att fastställa om programmet fungerar korrekt. Det är också användbart när du optimerar programmet. Till exempel kan ett relativt högt antal service samtal preemptions föreslå Trådens prioritet och/eller avstängningen-tröskelvärdet är för lågt. Dessutom kan ett relativt lågt antal inaktiva system returer föreslå att trådar med lägre prioritet inte pausas tillräckligt.

### <a name="debugging-pitfalls"></a>Felsöka fall GRO par

Fel sökning av flertrådiga program är lite svårare eftersom samma program kod kan köras från flera trådar. I sådana fall kanske det inte finns tillräckligt med en Bryt punkt. Fel sökaren måste också visa den aktuella tråd pekaren **_tx_thread_current_ptr** att använda en villkorlig Bryt punkt för att se om den anropande tråden är den som ska felsöka.

Mycket av detta hanteras i support paket för flera trådar som erbjuds via olika leverantörer av utvecklingsverktyg. På grund av sin enkla utformning är det relativt enkelt att integrera ThreadX med olika utvecklingsverktyg.

Stack storleken är alltid ett viktigt fel söknings avsnitt i multitrådning. När ett oförutsägbart beteende observeras, är det vanligt vis en bra första gissning att öka stack storlekarna för alla trådar, särskilt stack storleken på den senaste tråden som ska köras!

> [!TIP]
> *Det är också en bra idé att bygga ThreadX-biblioteket med **TX_ENABLE_STACK_CHECKING** definierat. Detta hjälper till att isolera problem med stack skador så tidigt som möjligt.*

## <a name="message-queues"></a>Meddelande köer

Meddelande köer är det främsta sättet att kommunicera mellan trådar i ThreadX. Ett eller flera meddelanden kan finnas i en meddelandekö. En meddelandekö som innehåller ett enda meddelande kallas ofta för en *post låda*.

Meddelanden kopieras till en kö med ***tx_queue_send** _ och kopieras från en kö efter _ *_tx_queue_receive_* *. Det enda undantaget är när en tråd pausas och väntar på ett meddelande på en tom kö. I det här fallet placeras nästa meddelande som skickas till kön direkt i trådens mål område.

Varje meddelandekö är en offentlig resurs. ThreadX placerar inga begränsningar för hur meddelande köer används.

### <a name="creating-message-queues"></a>Skapa meddelande köer

Meddelande köer skapas antingen under initiering eller under körning av program trådar. Det finns ingen gräns för antalet meddelande köer i ett program.

### <a name="message-size"></a>Meddelande storlek

Varje meddelandekö har stöd för ett antal meddelanden med fast storlek. De tillgängliga meddelande storlekarna är 1 till 16 32-bitars ord, inklusive. Meddelande storleken anges när kön skapas. Program meddelanden som är större än 16 ord måste skickas av en pekare. Detta åstadkommer du genom att skapa en kö med en meddelande storlek på 1 ord (tillräckligt för att hålla en pekare) och sedan skicka och ta emot meddelande pekare i stället för hela meddelandet.

### <a name="message-queue-capacity"></a>Meddelandekö-kapacitet

Antalet meddelanden som en kö kan innehålla är en funktion i dess meddelande storlek och storleken på det minnes utrymme som angavs när den skapas. Den totala meddelande kapaciteten för kön beräknas genom att antalet byte i varje meddelande divideras med det totala antalet byte i det angivna minnes området.

Om till exempel en meddelandekö som stöder en meddelande storlek på 1 32-bitars ord (4 byte) skapas med minnes området 100 byte, är dess kapacitet 25 meddelanden.

### <a name="queue-memory-area"></a>Köa minnes området

Som tidigare nämnts anges minnes området för buffring av meddelanden när kön skapas. Precis som andra minnes områden i ThreadX kan det finnas var som helst i målets adress utrymme.

Detta är en viktig funktion eftersom den ger programmet stor flexibilitet. Ett program kan till exempel hitta minnes området för en viktig kö i snabb RAM-minne för att förbättra prestanda.

### <a name="thread-suspension"></a>Tråd upphängning

Program trådar kan pausas vid försök att skicka eller ta emot ett meddelande från en kö. Vanligt vis avser tråd upphängning väntar på ett meddelande från en tom kö. Det är dock också möjligt för en tråd att pausa försök att skicka ett meddelande till en fullständig kö.

När tillståndet för uppskjutningen har lösts slutförs den begärda tjänsten och vänte tråden återupptas. Om flera trådar är inaktiverade i samma kö återupptas de i den ordning som de var pausade (FIFO).

Men prioritets återupptagning är också möjligt om programmet anropar ***tx_queue_prioritize*** före den Queue Service som lyfter tråd SUS pension. Prioritets tjänsten för köer placerar den högsta prioritets tråden överst i uppskjutnings listan, samtidigt som alla andra pausade trådar i samma FIFO-ordning lämnas kvar.

Tids gränser är också tillgängliga för alla uppehåll i kön. I princip anger ett timeout-värde det maximala antalet timer-Tick som tråden förblir inaktive rad. Om en timeout inträffar återupptas tråden och tjänsten returnerar rätt felkod.

### <a name="queue-send-notification"></a>Köa sändnings meddelande

Vissa program kan vara fördelaktiga att meddelas när ett meddelande placeras i en kö. ThreadX tillhandahåller den här funktionen genom ***tx_queue_send_notifys*** tjänsten. Den här tjänsten registrerar den angivna program aviserings funktionen med den angivna kön. ThreadX anropar sedan den här program meddelande funktionen när ett meddelande skickas till kön. Den exakta bearbetningen inom programmets meddelande funktion bestäms av programmet. Det består dock vanligt vis av att återuppta den aktuella tråden för att bearbeta det nya meddelandet.

### <a name="queue-event-chainingtrade"></a>Köa händelse länkning&trade;

Aviserings funktionerna i ThreadX kan användas för att kedja samman olika synkroniseringsobjekt. Detta är vanligt vis användbart när en enskild tråd måste bearbeta flera synkroniseringsanvändare.

Anta till exempel att en enskild tråd ansvarar för att bearbeta meddelanden från fem olika köer och måste även inaktive ras när inga meddelanden är tillgängliga. Detta åstadkommer du genom att registrera en program meddelande funktion för varje kö och introducera en extra beräknings semafor. Mer specifikt utför funktionen program meddelande en *tx_semaphore_put* när den anropas (antalet semaforer representerar det totala antalet meddelanden i alla fem köer). Bearbetnings tråden inaktive ras på den här semaforen via tjänsten *tx_semaphore_get* . När semaforen är tillgänglig (i det här fallet när ett meddelande är tillgängligt!) återupptas bearbetnings tråden. Sedan söker den efter varje kö för ett meddelande, bearbetar det påträffade meddelandet och utför en annan ***tx_semaphore_get*** att vänta på nästa meddelande. Att göra detta utan händelse länkning är ganska svårt och sannolikt kräver fler trådar och/eller ytterligare program kod.

I allmänhet resulterar *händelse länkning* i färre trådar, mindre omkostnader och mindre RAM-krav. Det ger också en mycket flexibel mekanism för att hantera krav för synkronisering av mer komplexa system.

### <a name="run-time-queue-performance-information"></a>Prestanda information för kör tids kön
ThreadX tillhandahåller valfri prestanda information för körning av kö. Om ThreadX-biblioteket och programmet har skapats med ***TX_QUEUE_ENABLE_PERFORMANCE_INFO*** definierat, samlar ThreadX in följande information.

Totalt antal för det övergripande systemet:

  - skickade meddelanden

  - mottagna meddelanden

  - köa tomma SUS pensioner

  - köa fullständig fjädring

  - Returnerar fullständiga fel i kön (ingen avstängning har angetts)

  - timeout för kö

Totalt antal för varje kö:

  - skickade meddelanden

  - mottagna meddelanden

  - köa tomma SUS pensioner

  - köa fullständig fjädring

  - Returnerar fullständiga fel i kön (ingen avstängning har angetts)

  - timeout för kö

Den här informationen är tillgänglig i körnings läge genom tjänsterna ***tx_queue_performance_info_get** _ och _ *_tx_queue_performance_system_info_get_* *. Prestanda information för kö är användbar för att avgöra om programmet fungerar korrekt. Det är också användbart när du optimerar programmet. Till exempel, ett relativt högt antal "kön full fjädring" föreslår en ökning i kös Tor lek kan vara fördelaktig.

### <a name="queue-control-block-tx_queue"></a>Block TX_QUEUE för Queue Control

Egenskaperna för varje meddelandekö finns i kontroll blocket. Den innehåller intressant information, till exempel antalet meddelanden i kön. Den här strukturen definieras i filen ***tx_api. h*** .

Meddelande köns kontroll block kan också finnas var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="message-destination-pitfall"></a>Pitfall för meddelande mål

Som tidigare nämnts kopieras meddelanden mellan området kö och program data. Det är viktigt att se till att målet för ett mottaget meddelande är tillräckligt stort för att rymma hela meddelandet. Om inte, kommer minnet som följer meddelande målet förmodligen att skadas.

> [!NOTE]
> *Detta är särskilt dödligt när ett för litet meddelande mål är i stacken – inget som skadar retur adressen för en funktion!*

## <a name="counting-semaphores"></a>Inventering av semaforer

ThreadX tillhandahåller 32-bitars beräknings semaforer som ligger inom intervallet 0 till 4 294 967 295. Det finns två åtgärder för att räkna semaforer: *tx_semaphore_get* och *tx_semaphore_put*. Åtgärden get minskar semaforen med en. Om semaforen är 0 fungerar inte get-åtgärden. Inversen av Get-åtgärden är åtgärden placera.
Den ökar semaforen med en.

Varje semafor i beräkningen är en offentlig resurs. ThreadX placerar inga begränsningar för hur antalet semaforer används.

Inventering av semaforer används vanligt vis för *ömsesidig uteslutning*. Inventering av semaforer kan dock också användas som en metod för händelse aviseringar.

### <a name="mutual-exclusion"></a>Ömsesidigt undantag

 Ömsesidigt undantag avser att kontrol lera åtkomsten till trådar till vissa program områden (kallas även *kritiska avsnitt* eller *program resurser*). När det används för ömsesidig uteslutning representerar "Aktuellt antal" för en semafor det totala antalet trådar som tillåts åtkomst. I de flesta fall har semaforer som används för ömsesidig undantag ett initialt värde på 1, vilket innebär att endast en tråd kan komma åt den associerade resursen i taget. Antalet semaforer som räknas som värden på 0 eller 1 kallas ofta *binära semaforer*.

> [!IMPORTANT]
> *Om en binär semafor används måste användaren förhindra att samma tråd utför en get-åtgärd på en semafor som redan äger. En andra get skulle Miss lyckas och kan orsaka obestämd avstängning av den anropande tråden och permanent otillgänglig resurs.*

### <a name="event-notification"></a>Händelse meddelande

Det är också möjligt att använda beräknings semaforer som händelse meddelanden i en producent som är konsument. Konsumenten försöker få inventerings semaforen medan producenten ökar semaforen när något är tillgängligt. Sådana semaforer har vanligt vis ett ursprungligt värde på 0 och kommer inte att öka förrän producenten har något som är redo för konsumenten. Semaforer som används för händelse aviseringar kan också ha nytta av att ***tx_semaphore_ceiling_put*** tjänst anropet. Den här tjänsten säkerställer att antalet semaforer aldrig överskrider det värde som anges i anropet.

### <a name="creating-counting-semaphores"></a>Skapa inventerings semaforer

Inventering av semaforer skapas antingen under initieringen eller under körningen av program trådar. Det inledande antalet av semaforen anges när du skapar. Det finns ingen gräns för antalet semaforer i ett program.

### <a name="thread-suspension"></a>Tråd upphängning

Program trådar kan pausas vid försök att utföra en get-åtgärd på en semafor med det aktuella antalet 0.

När en beställnings åtgärd utförs utförs den pausade trådens get-åtgärd och tråden återupptas. Om flera trådar har pausats på samma inventerings semafor, återupptas de i samma ordning som de var pausade (FIFO).

Men prioritets återupptagning är också möjligt om programmet anropar ***tx_semaphore_prioritize*** före semaforen som lyfter upp tråd SUS pension. I semafors prioriterings tjänsten placeras den högsta prioritets tråden längst fram i uppskjutnings listan, samtidigt som alla andra pausade trådar i samma FIFO-ordning lämnas kvar.

### <a name="semaphore-put-notification"></a>Varning om semafors placering

Vissa program kan vara fördelaktiga att meddelas varje gång en semafor införs. ThreadX tillhandahåller den här funktionen genom ***tx_semaphore_put_notifys*** tjänsten. Den här tjänsten registrerar den angivna program aviserings funktionen med den angivna semaforen. ThreadX kommer sedan att anropa den här program aviserings funktionen varje gång som semaforen placeras. Den exakta bearbetningen inom programmets meddelande funktion bestäms av programmet. Det består dock vanligt vis av att återuppta den aktuella tråden för bearbetning av den nya händelsen semafor.

### <a name="semaphore-event-chainingtrade"></a>Händelse länkning i semafor&trade;

Aviserings funktionerna i ThreadX kan användas för att kedja samman olika synkroniseringsobjekt. Detta är vanligt vis användbart när en enskild tråd måste bearbeta flera synkroniseringsanvändare.

I stället för att en separat tråd pausas för ett köat meddelande, händelse flaggor och en semafor, kan programmet registrera en avisering för varje objekt. Vid anrop kan program aviserings rutinen återupptas och sedan återuppta en enda tråd, som kan söka varje objekt för att hitta och bearbeta den nya händelsen.

I allmänhet resulterar *händelse länkning* i färre trådar, mindre omkostnader och mindre RAM-krav. Det ger också en mycket flexibel mekanism för att hantera krav för synkronisering av mer komplexa system.

### <a name="run-time-semaphore-performance-information"></a>Prestanda information om körning av semafor

ThreadX tillhandahåller valfria prestanda information för semaforen i körnings läge. Om ThreadX-biblioteket och programmet har skapats med **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** definierat, samlar ThreadX in följande information.

Totalt antal för det övergripande systemet:

  - Infoga semafor

  - semafor får

  - semafor för att hämta SUS pensioner

  - timeout för semafor

Totalt antal för varje semafor:

  - Infoga semafor

  - semafor får

  - semafor för att hämta SUS pensioner

  - timeout för semafor

Den här informationen är tillgänglig i körnings läge genom tjänsterna ***tx_semaphore_performance_info_get** _ och _ *_tx_semaphore_performance_system_info_get_* *. Information om semafor-prestanda är användbar för att fastställa om programmet fungerar korrekt. Det är också användbart när du optimerar programmet. Till exempel kan ett relativt högt antal "semafors tids gränser" innebära att andra trådar håller resurserna för långa.

### <a name="semaphore-control-block-tx_semaphore"></a>Semafor-kontroll block TX_SEMAPHORE

Egenskaperna för varje semafor i inventeringen finns i kontroll blocket. Den innehåller information som det aktuella antalet semaforer. Den här strukturen definieras i filen ***tx_api. h*** .

Semafors kontroll block kan finnas var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="deadly-embrace"></a>Deadly

En av de mest intressanta och farliga fall GRO par som är kopplade till semaforer som används för ömsesidiga undantag är *Deadly*. En Deadly-begränsning, eller *deadlock*, är ett tillstånd där två eller flera trådar pausas på obestämd tid vid försök att hämta semaforer som redan ägs av varandra.

Det här villkoret illustreras bäst av två trådar, två semafor-exempel. Anta att den första tråden äger den första semaforen och den andra tråden äger den andra semaforen. Om den första tråden försöker hämta den andra semaforen och samtidigt den andra tråden försöker hämta den första semaforen, anger båda trådarna ett död läge. Om dessa trådar fortsätter att skjutas upp, är deras associerade resurser även låsta för alltid. Bild 8 illustrerar det här exemplet.

**Deadly** (exempel)

![Exempel på pausade trådar](./media/user-guide/example-suspended-threads.png)

**FIGUR 8. Exempel på pausade trådar**

För real tids system kan Deadly-begränsningar förhindras genom att placera vissa begränsningar för hur trådar får semaforer. Trådar kan bara ha en semafor i taget. Ett annat sätt är att trådarna kan äga flera semaforer om de samlar in dem i samma ordning. I föregående exempel, om den första och andra tråden får den första och andra semaforen i ordning, förhindras Deadly-.

> [!TIP]
> *Du kan också använda tids gränsen för avstängningen som är kopplad till åtgärden Hämta för att återställa från en Deadly.*

### <a name="priority-inversion"></a>Prioritets version

En annan Pitfall som är kopplad till ömsesidiga undantags semaforer är prioritets version. Det här avsnittet beskrivs mer fullständigt i "[tråd prioritet fall GRO par](#thread-priority-pitfalls)".

Det grundläggande problemet uppstår i en situation där en lägre prioritets tråd har en semafor som kräver tråd med högre prioritet. Detta är normalt. Trådar med prioriteter mellan dem kan dock orsaka att prioriteten är inaktiv för senaste icke-deterministisk tids period. Detta kan hanteras genom noggrann val av tråd prioriteter, med hjälp av avstängningen och tillfälligt höja prioriteten för den tråd som äger resursen till den för tråden med hög prioritet.

## <a name="mutexes"></a>Mutexer

Förutom semaforer innehåller ThreadX även ett mutex-objekt. En mutex är i princip en binär semafor, vilket innebär att endast en tråd kan äga en mutex i taget. Dessutom kan samma tråd utföra en lyckad mutex get-åtgärd på ett ägd mutex flera gånger, 4 294 967 295 att vara exakt. Det finns två åtgärder på mutex-objektet: ***tx_mutex_get** _ och _ *_tx_mutex_put_* *. Get-åtgärden hämtar en mutex som inte ägs av en annan tråd, medan åtgärds åtgärden släpper en tidigare Hämtad mutex. För att en tråd ska kunna släppa en mutex måste antalet placera åtgärder vara lika med antalet tidigare hämtnings åtgärder.

Varje mutex är en offentlig resurs. ThreadX placerar inga begränsningar för hur mutexer används.

ThreadX-mutexer används enbart för *ömsesidigt uteslutande undantag*. Till skillnad från semaforer har mutexer ingen användning som metod för händelse aviseringar.

### <a name="mutex-mutual-exclusion"></a>Ömsesidigt uteslutande mutex

På samma sätt som i avsnittet om inventering av semafor, avser ömsesidigt undantag för att kontrol lera åtkomsten till trådar till vissa program områden (kallas även *kritiska avsnitt* eller *program resurser*). När det är tillgängligt får ett ThreadX-mutex ett antal ägarskap 0. När mutexen har hämtats av en tråd ökas ägarskapet en gång för varje lyckad get-åtgärd som utförs på mutex och minskas för varje lyckad åtgärd.

### <a name="creating-mutexes"></a>Skapa mutexer

ThreadX-mutexer skapas antingen under initieringen eller under körningen av program trådar. Det första villkoret för en mutex är alltid "tillgängligt". En mutex kan också skapas med *prioriterat arv* valt.

### <a name="thread-suspension"></a>Tråd upphängning

Program trådar kan pausas vid försök att utföra en get-åtgärd på en mutex som redan ägs av en annan tråd.

När samma antal placerings åtgärder utförs av den ägande tråden, utförs den inaktiverade trådens get-åtgärd, vilket ger IT-ägarskap för mutexen och tråden återupptas. Om flera trådar har pausats på samma mutex återupptas de i samma ordning som de var pausade (FIFO).

Prioritets återupptagning görs dock automatiskt om arv av mutex prioritet valdes när de skapades. Prioritets återupptagning är också möjligt om programmet anropar ***tx_mutex_prioritize*** före det mutex-anrop som lyfter tråd upphängning. I mutex-prioriterings tjänsten placeras den högsta prioritets tråden längst fram i uppskjutnings listan, samtidigt som alla andra pausade trådar i samma FIFO-ordning lämnas kvar.

### <a name="run-time-mutex-performance-information"></a>Prestanda information för kör tid-mutex

ThreadX tillhandahåller valfria prestanda information för körning av mutex. Om ThreadX-biblioteket och programmet har skapats med **TX_MUTEX_ENABLE_PERFORMANCE_INFO** definierat, samlar ThreadX in följande information.

Totalt antal för det övergripande systemet:

- mutex lägger

- mutex hämtar

- mutex get SUS pensioner

- timeout för mutex-hämtning

- mutex Priority-versioner

- arv av mutex-prioritet

Totalt antal för varje mutex:

  - mutex lägger

  - mutex hämtar

  - mutex get SUS pensioner

  - timeout för mutex-hämtning

  - mutex Priority-versioner

  - arv av mutex-prioritet

Den här informationen är tillgänglig i körnings läge genom tjänsterna ***tx_mutex_performance_info_get** _ och _ *_tx_mutex_performance_system_info_get_* *. Information om mutex-prestanda är användbar för att fastställa om programmet fungerar korrekt. Det är också användbart när du optimerar programmet. Till exempel kanske ett relativt högt antal "mutex get Times"-tids gränser "föreslår att andra trådar håller resurserna för långa.

### <a name="mutex-control-block-tx_mutex"></a>Mutex Control Block TX_MUTEX

Egenskaperna för varje mutex finns i kontroll blocket. Den innehåller information, till exempel antalet aktuella mutex-ägarskap, tillsammans med pekaren över den tråd som äger mutex. Den här strukturen definieras i filen ***tx_api. h*** . Mutex Control Block kan finnas var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="deadly-embrace"></a>Deadly

En av de mest intressanta och farliga fall GRO par som är kopplade till mutex-ägande är att *Deadly-kraften*. En Deadly-begränsning, eller *deadlock*, är ett villkor där två eller flera trådar inaktive ras oändligt under försök att hämta en mutex som redan ägs av de andra trådarna. *Deadly* -diskussionen och dess lösningar är helt giltiga även för mutex-objektet.

### <a name="priority-inversion"></a>Prioritets version

Som tidigare nämnts är en större Pitfall som är kopplad till ömsesidig undantag prioritets version. Det här avsnittet beskrivs mer fullständigt i "[tråd prioritet fall GRO par](#thread-priority-pitfalls)".

Det grundläggande problemet uppstår i en situation där en tråd med lägre prioritet har en semafor som kräver tråd med högre prioritet. Detta är normalt. Trådar med prioriteter mellan dem kan dock orsaka att prioriteten är inaktiv för senaste icke-deterministisk tids period. Till skillnad från semaforer som diskuterats tidigare har mutex-objektet ThreadX valfria *prioritets arv*. Den grundläggande idén bakom prioriterad arv är att en tråd med lägre prioritet har sin prioritet tillfälligt upphöjt till prioriteten för en tråd med hög prioritet som vill ha samma mutex som ägs av tråden med lägre prioritet. När den nedre prioritets tråden frigör mutex återställs den ursprungliga prioriteten och tråden med högre prioritet får ägarskapet av mutexen. Den här funktionen eliminerar icke-deterministiska prioritets versioner genom att begränsa mängden inversion till den tid som den lägre prioritets tråden innehåller mutex. De tekniker som beskrivs tidigare i det här kapitlet för att hantera icke-deterministiska prioritets versioner är också även giltiga med mutexer.

## <a name="event-flags"></a>Händelse flaggor

Händelse flaggor är ett kraftfullt verktyg för Thread-synkronisering. Varje händelse flagga representeras av en enskild bit. Händelse flaggor är ordnade i grupper om 32. Trådar kan köras på alla 32 händelse flaggor i en grupp på samma tid. Händelser anges av ***tx_event_flags_set** _ och hämtas av _ *_tx_event_flags_get_* *.

Inställning av händelse flaggor görs med logisk och/eller åtgärd mellan aktuella händelse flaggor och nya händelse flaggor. Typen av logisk åtgärd (antingen en och eller eller) anges i ***tx_event_flags_set*** -anropet.

Det finns liknande logiska alternativ för att hämta händelse flaggor. En get-begäran kan ange att alla angivna händelse flaggor krävs (ett logiskt och).

Alternativt kan en get-begäran ange att någon av de angivna händelse flaggorna ska uppfylla begäran (ett logiskt eller). Den typ av logisk åtgärd som är associerad med händelse flaggorna som ska hämtas anges i ***tx_event_flags_get*** -anropet.

> [!IMPORTANT]
> *Händelse flaggor som uppfyller en get-begäran används, d.v.s. värdet noll, om* **TX_OR_CLEAR** *eller* **TX_AND_CLEAR** *anges i begäran.*

Varje händelse flaggor grupp är en offentlig resurs. ThreadX placerar inga begränsningar för hur grupper av händelse flaggor används.

### <a name="creating-event-flags-groups"></a>Skapa händelse flaggor grupper

Händelse flaggor grupper skapas antingen under initiering eller under körning av program trådar. När de skapas har alla händelse flaggor i gruppen värdet noll. Det finns ingen gräns för antalet händelse flaggor grupper i ett program.

### <a name="thread-suspension"></a>Tråd upphängning

Program trådar kan pausas vid försök att hämta en logisk kombination av händelse flaggor från en grupp. När en händelse flagga har angetts granskas get-begäranden för alla pausade trådar. Alla trådar som nu har de nödvändiga händelse flaggorna återupptas.

> [!NOTE]
> *Alla pausade trådar i en händelse flaggas grupp granskas när dess händelse flaggor anges. Det innebär naturligtvis ytterligare kostnader. Därför är det bra att begränsa antalet trådar som använder samma händelse flagg grupp till ett rimligt tal.*

### <a name="event-flags-set-notification"></a>Händelse flaggor ange meddelande

Vissa program kan vara fördelaktiga att meddelas när en händelse flagga har angetts. ThreadX tillhandahåller den här funktionen genom ***tx_event_flags_set_notifys*** tjänsten. Den här tjänsten registrerar den angivna program aviserings funktionen med den angivna händelse flaggas gruppen. ThreadX kommer sedan att anropa den här program aviserings funktionen när en händelse flagga i gruppen anges. Den exakta bearbetningen inom programmets meddelande funktion bestäms av programmet, men det består vanligt vis av att återuppta den aktuella tråden för att bearbeta den nya händelse flaggan.

### <a name="event-flags-event-chainingtrade"></a>Händelse länkning för händelse flaggor&trade;

Aviserings funktionerna i ThreadX kan användas för att "kedja" olika synkroniserings händelser tillsammans. Detta är vanligt vis användbart när en enskild tråd måste bearbeta flera synkroniseringsanvändare.

I stället för att en separat tråd pausas för ett köat meddelande, händelse flaggor och en semafor, kan programmet registrera en avisering för varje objekt. Vid anrop kan program aviserings rutinen återupptas och sedan återuppta en enda tråd, som kan söka varje objekt för att hitta och bearbeta den nya händelsen.

I allmänhet resulterar *händelse länkning* i färre trådar, mindre omkostnader och mindre RAM-krav. Det ger också en mycket flexibel mekanism för att hantera krav för synkronisering av mer komplexa system.

### <a name="run-time-event-flags-performance-information"></a>Prestanda information för kör tids händelse flaggor

ThreadX tillhandahåller valfria prestanda information för kör tids händelse flaggor. Om ThreadX-biblioteket och programmet har skapats med **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** definierat, samlar ThreadX in följande information.

Totalt antal för det övergripande systemet:

  - händelse flaggor uppsättningar

  - händelse flaggor hämtas

  - händelse flaggor hämta SUS pensioner

  - händelse flaggor Hämta timeout

Totalt antal för varje händelse flaggor grupp:

  - händelse flaggor uppsättningar

  - händelse flaggor hämtas

  - händelse flaggor hämta SUS pensioner

  - händelse flaggor Hämta timeout

Den här informationen är tillgänglig i körnings läge genom tjänsterna ***tx_event_flags_performance_info_get** _ och _*_tx_event_flags_performance_system_info_get_*_. Prestanda informationen för händelse flaggor är användbar för att fastställa om programmet fungerar korrekt. Det är också användbart när du optimerar programmet. Till exempel kan ett relativt högt antal tids gränser på den _ *_tx_event_flags_get_**-tjänsten föreslå att tids gränsen för inaktive ring av händelse flaggor är för kort.

### <a name="event-flags-group-control-block-tx_event_flags_group"></a>Händelse flaggor grupp kontroll block TX_EVENT_FLAGS_GROUP

Egenskaperna för varje händelse flaggas grupp finns i kontroll blocket. Den innehåller information som de aktuella inställningarna för händelse flaggor och antalet trådar som har avbrutits för händelser. Den här strukturen definieras i filen ***tx_api. h*** .

Kontroll block för händelse grupper kan finnas var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="memory-block-pools"></a>Pool för minnes block

Att allokera minne på ett snabbt och entydigt sätt är alltid en utmaning i real tids program. Med detta i åtanke ger ThreadX möjlighet att skapa och hantera flera pooler med minnes block med fast storlek.

Eftersom minnes Blocks pooler består av block med fast storlek, finns det aldrig några fragmenterings problem. Fragmenteringen orsakar naturligtvis att beteendet är icke deterministiskt. Dessutom är tiden som krävs för att allokera och frigöra ett minnes block med fast storlek jämförbar med det för enkel manipulering av länkade listor. Dessutom görs tilldelningen av minnes block och avallokering i huvudet i listan över tillgängliga. Detta ger snabbast möjlig länkad List bearbetning och kan hjälpa till att behålla det faktiska minnes blocket i cachen.

Brist på flexibilitet är den största nack delen med minnes pooler med fast storlek. Block storleken för en pool måste vara tillräckligt stor för att hantera de sämsta fall minnes kraven för sina användare. Naturligtvis kan minnet slösas om många olika storleks minnes begär Anden görs i samma pool. En möjlig lösning är att göra flera olika minnes Blocks pooler som innehåller olika minnes block i storlek.

Varje minnes Blocks pool är en offentlig resurs. ThreadX placerar inga begränsningar för hur pooler används.

### <a name="creating-memory-block-pools"></a>Skapa minnes Blocks pooler

Minnes Blocks pooler skapas antingen under initieringen eller under körningen av program trådar. Det finns ingen gräns för antalet minnes Blocks pooler i ett program.

### <a name="memory-block-size"></a>Minnes block storlek

Som tidigare nämnts innehåller Memory block-pooler ett antal block med fast storlek. Block storleken, i byte, anges när poolen skapas.

> [!NOTE]
> *ThreadX lägger till en liten mängd kostnader – storleken på en C-pekare – till varje minnes block i poolen. Dessutom kan ThreadX behöva fylla block storleken för att behålla början på varje minnes block vid rätt justering.*

### <a name="pool-capacity"></a>Pool-kapacitet

Antalet minnes block i en pool är en funktion i block storlek och det totala antalet byte i minnes området som angavs när den skapades. Kapaciteten för en pool beräknas genom att block storleken divideras (inklusive utfyllnad och övergångs byte) till det totala antalet byte i det angivna minnes området.

### <a name="pools-memory-area"></a>Poolens minnes områden

Som tidigare nämnts anges minnes området för block-poolen när den skapas. Precis som andra minnes områden i ThreadX kan det finnas var som helst i målets adress utrymme.

Detta är en viktig funktion på grund av den stora flexibiliteten. Anta till exempel att en kommunikations produkt har ett highspeed minnes utrymme för I/O. Det här minnes området hanteras enkelt genom att göra det till en ThreadX-pool för minnes block.

### <a name="thread-suspension"></a>Tråd upphängning

Program trådar kan pausas i väntan på ett minnes block från en tom pool. När ett block returneras till poolen får den pausade tråden det här blocket och tråden återupptas.

Om flera trådar har pausats på samma minnes Blocks pool återupptas de i den ordning som de var pausade (FIFO).

Men prioritets återupptagning är också möjligt om programmet anropar ***tx_block_pool_prioritize*** före det blockerade release-anropet som lyfter upp tråd upphängning. Prioritets tjänsten för block pool placerar den högsta prioritets tråden längst fram i uppskjutnings listan, samtidigt som alla andra pausade trådar i samma FIFO-ordning lämnas kvar.

### <a name="run-time-block-pool-performance-information"></a>Prestanda information för kör tid för block pool

ThreadX tillhandahåller valfri prestanda information för körning av programpooler. Om ThreadX-biblioteket och programmet har skapats med **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** definierat, samlar ThreadX in följande information.

Totalt antal för det övergripande systemet:

  - tilldelade block

  - släppta block

  - tilldelnings SUS pensioner

  - tids gräns för tilldelning

Totalt antal för varje block pool:

  - tilldelade block

  - släppta block

  - tilldelnings SUS pensioner

  - tids gräns för tilldelning

Den här informationen är tillgänglig i körnings läge genom tjänsterna ***tx_block_pool_performance_info_get** _ och _ *_tx_block_pool_performance_system_info_get_* *. Det är praktiskt att blockera poolens prestanda information när programmet fungerar korrekt. Det är också användbart när du optimerar programmet. Till exempel kan ett relativt högt antal "tilldelnings SUS pensioner" innebära att den blockerande poolen är för liten.

### <a name="memory-block-pool-control-block-tx_block_pool"></a>Minnes Blocks kontroll block TX_BLOCK_POOL

Egenskaperna för varje minnes Blocks pool finns i kontroll blocket. Den innehåller information som till exempel antalet tillgängliga minnes block och storleken på minnesbufferten. Den här strukturen definieras i filen ***tx_api. h*** .

Du kan också placera kontroll block var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="overwriting-memory-blocks"></a>Skriva över minnes block

Det är viktigt att se till att användaren av ett allokerat minnes block inte skriver utanför dess gränser. Om detta händer inträffar skada i ett intilliggande minnes område (vanligt vis senare). Resultatet är oförutsägbart och ofta allvarligt för programmet.

## <a name="memory-byte-pools"></a>Minnes byte pooler

ThreadX minnes byte pooler liknar en standard-C-heap. Till skillnad från standard-C-heapen är det möjligt att ha flera minnes byte pooler. Dessutom kan trådar pausa på en pool tills det begärda minnet är tillgängligt.

Tilldelningar från poolerna för minnes byte liknar traditionella ***malloc** _-anrop, vilket innefattar mängden minne som önskas (i byte). Minne tilldelas från poolen på ett _first-passning * sätt; dvs. det första lediga minnes blocket som uppfyller begäran används. Överflödigt minne från det här blocket konverteras till ett nytt block och placeras i listan över lediga minnen igen. Den här processen kallas *fragmentering*.

Intilliggande lediga minnes block *sammanfogas* tillsammans under en efterföljande tilldelnings sökning för att få tillräckligt med ledigt minnes block. Den här processen kallas *defragmentering*.

Varje pool för minnes byte är en offentlig resurs. ThreadX placerar inga begränsningar för hur pooler används, förutom att minnes byte tjänster inte kan anropas från ISR: er.

### <a name="creating-memory-byte-pools"></a>Skapa minnes byte pooler

Minnes byte pooler skapas antingen under initieringen eller under körningen av program trådar. Det finns ingen gräns för antalet minnes byte pooler i ett program.

### <a name="pool-capacity"></a>Pool-kapacitet

Antalet allocatable byte i en pool för minnes byte är något mindre än vad som angavs när det skapades. Detta beror på att hanteringen av det lediga minnes området introducerar en del kostnader. Varje ledigt minnes block i poolen kräver motsvarande två C-pekare. Dessutom skapas poolen med två block, ett stort ledigt block och ett litet permanent allokerat block i slutet av minnes området. Detta allokerade block används för att förbättra prestandan för algoritmen. Den eliminerar behovet av att kontinuerligt kontrol lera om poolens slut under sammanfogningen.

Under körningen ökar mängden omkostnader i poolen vanligt vis. Allokeringar av ett udda antal byte fylls i för att säkerställa korrekt justering av nästa minnes block. Dessutom ökar belastningen när poolen blir mer fragmenterad.

### <a name="pools-memory-area"></a>Poolens minnes områden

Minnes området för en Memory byte-pool anges när du skapar. Precis som andra minnes områden i ThreadX kan det finnas var som helst i målets adress utrymme. Detta är en viktig funktion på grund av den stora flexibiliteten. Om mål maskin varan till exempel har ett höghastighets minnes område och ett minnes kort med låg hastighet, kan användaren hantera minnesallokering för båda områdena genom att skapa en pool i var och en av dem.

### <a name="thread-suspension"></a>Tråd upphängning

Program trådar kan pausas i väntan på minnes byte från en pool. När tillräckligt sammanhängande minne blir tillgängligt får de pausade trådarna det begärda minnet och trådarna återupptas.

Om flera trådar har pausats på samma minnes byte pool, tilldelas de minne (återupptas) i den ordning som de var pausade (FIFO).

Men prioritets återupptagning är också möjligt om programmet anropar ***tx_byte_pool_prioritize*** före byte release-anropet som lyfter upp tråd upphängning. Prioritets tjänsten för byte av byte placerar den högsta prioritets tråden längst fram i uppskjutnings listan, samtidigt som alla andra pausade trådar i samma FIFO-ordning lämnas kvar.

### <a name="run-time-byte-pool-performance-information"></a>Prestanda information för kör tids byte-pool

ThreadX tillhandahåller valfria prestanda information för prestanda information för kör tids byte. Om ThreadX-biblioteket och programmet har skapats med ***TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO*** definierat, samlar ThreadX in följande information.

Totalt antal för det övergripande systemet:

  - allokeringar

  - versioner

  - genomsökta fragment

  - sammanfogade fragment

  - skapade fragment

  - tilldelnings SUS pensioner

  - tids gräns för tilldelning

Totalt antal för varje byte-pool:

  - allokeringar

  - versioner

  - genomsökta fragment

  - sammanfogade fragment

  - skapade fragment

  - tilldelnings SUS pensioner

  - tids gräns för tilldelning

Den här informationen är tillgänglig i körnings läge genom tjänsterna ***tx_byte_pool_performance_info_get** _ och _ *_tx_byte_pool_performance_system_info_get_* *. Prestanda informationen för byte-poolen är användbar för att fastställa om programmet fungerar korrekt. Det är också användbart när du optimerar programmet. Till exempel kan ett relativt högt antal "tilldelnings SUS pensioner" föreslå att byte-poolen är för liten.

### <a name="memory-byte-pool-control-block-tx_byte_pool"></a>Kontroll block TX_BYTE_POOL för minnes-byte-pool

Egenskaperna för varje pool för minnes byte finns i kontroll blocket. Den innehåller användbar information, till exempel antalet tillgängliga byte i poolen. Den här strukturen definieras i filen ***tx_api. h*** .

Du kan också placera kontroll block var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="nondeterministic-behavior"></a>Icke-deterministiskt beteende

Även om minnes byte pooler ger mest flexibel minnesallokering, har de också en något icke deterministisk funktion. Till exempel kan en minnes byte pool ha 2 000 byte tillgängligt minne, men kanske inte kan uppfylla en tilldelnings förfrågan på 1 000 byte. Det beror på att det inte finns några garantier för hur många lediga byte som är sammanhängande. Även om det finns ett ledigt block på 1 000 byte finns det inga garantier för hur lång tid det tar att hitta blocket. Det är helt möjligt att hela lagringspoolen måste sökas för att hitta 1 000 byte-blocket.

> [!TIP]
> *Som ett resultat av det icke deterministiska beteendet för minnes byte pooler är det vanligt vis bra att undvika att använda minnes byte tjänster i områden där deterministisk, real tids beteende krävs. Många program förallokerar det minne som krävs för att förallokeras under initiering eller körnings tids konfiguration.*

### <a name="overwriting-memory-blocks"></a>Skriva över minnes block

Det är viktigt att se till att användaren av allokerat minne inte skriver utanför dess gränser. Om detta händer inträffar skada i ett intilliggande minnes område (vanligt vis senare). Resultatet är oförutsägbart och ofta oåterkalleligt för program körning.

## <a name="application-timers"></a>Program timers

Snabba svar på asynkrona externa händelser är den viktigaste funktionen för inbäddade program i real tid. Många av dessa program måste dock också utföra vissa aktiviteter vid förinställda tids perioder.

ThreadX-programtimers tillhandahåller program med möjlighet att köra program C-funktioner vid specifika tidsintervall. Det är också möjligt att ett programs timer upphör att gälla en gång. Den här typen av timer kallas för en väntande *timer*, medan timers med upprepade intervall kallas *periodiska timers*.

Varje program timer är en offentlig resurs. ThreadX placerar inga begränsningar för hur Application timers används.

### <a name="timer-intervals"></a>Tidsintervall

I ThreadX tidsintervaller mäts av periodiska timer-avbrott. Varje timer-avbrott kallas för ett timer- *Tick*. Den faktiska tiden mellan timer-Tick anges av programmet, men 10ms är normen för de flesta implementeringar. Den periodiska tids inställningen finns vanligt vis i ***tx_initialize_low_level*** sammansättnings filen.

Det är värt att nämna att den underliggande maskin varan måste ha möjlighet att generera periodiska avbrott för att program timers ska fungera. I vissa fall har processorn en inbyggd periodisk avbrotts funktion. Om processorn inte har denna möjlighet måste användarens tavla ha en kring utrustning som kan generera periodiska avbrott.

> [!IMPORTANT]
> *ThreadX kan fortfarande fungera även utan en regelbunden avbrotts källa. All timer-relaterad bearbetning inaktive ras dock. Detta omfattar timeslicing, uppskjutnings tids gränser och timer-tjänster.*

### <a name="timer-accuracy"></a>Tids exakthet

Timer-förfaller anges i förhållande till Tick. Det angivna värdet för förfallo tid minskas med ett på varje timer-Ticket. Eftersom en programtimer kunde aktive ras precis före ett timer-avbrott (eller timer Ticket), kan den faktiska förfallo tiden vara upp till ett kort tidigt.

Om timer-skalstrecket är 10ms kan programtimers förfalla upp till 10ms tidigt. Detta är mer betydelsefullt för 10ms timers än 1 andra timers. Om du ökar den tids lösa frekvensen minskar dock den här fel marginalen.

### <a name="timer-execution"></a>Timer-körning

Program timers körs i den ordning som de blir aktiva. Om till exempel tre timers har skapats med samma förfallo värde och aktive ras, så garanteras att deras motsvarande utgångs funktioner kan köras i den ordning som de aktiverades.

### <a name="creating-application-timers"></a>Skapa timers för program

Program timers skapas antingen under initieringen eller under körningen av program trådar. Det finns ingen gräns för antalet program timers i ett program.

### <a name="run-time-application-timer-performance-information"></a>Prestanda information för programtimern för program

ThreadX tillhandahåller valfria prestanda information för programtimern för program. Om ThreadX-biblioteket och programmet har skapats med **TX_TIMER_ENABLE_PERFORMANCE_INFO** definierat ackumuleras följande information i ThreadX.

Totalt antal för det övergripande systemet:

- aktiveringar

- inaktive ring

- återaktivering (periodiska timers)

- förfallo tider

- giltighets justeringar

Totalt antal för varje program-timer:

- aktiveringar

- inaktive ring

- återaktivering (periodiska timers)

- förfallo tider

- giltighets justeringar

Den här informationen är tillgänglig i körnings läge genom tjänsterna ***tx_timer_performance_info_get** _ och _ *_tx_timer_performance_system_info_get_* *. Prestanda information för programtimern är användbar för att fastställa om programmet fungerar korrekt. Det är också användbart när du optimerar programmet.

### <a name="application-timer-control-block-tx_timer"></a>Block TX_TIMER för kontroll av program timer

Egenskaperna för varje program timer finns i kontroll blocket. Den innehåller användbar information, till exempel ett värde för identifiering av 32-bitars utgång. Den här strukturen definieras i filen ***tx_api. h*** .

Block för timer-kontroll kan finnas var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="excessive-timers"></a>Överdriven timers

Som standard körs programtimers inifrån en dold system tråd som körs med prioritet noll, vilket vanligt vis är högre än alla program trådar. På grund av detta bör bearbetningen i program timers vara minst.

Det är också viktigt att undvika, när så är möjligt, timers som upphör att gälla varje timer. En sådan situation kan medföra överdriven till koppling i programmet.

> [!IMPORTANT]
> *Som tidigare nämnts körs tids program timers från en dold system tråd. Det är därför viktigt att inte välja SUS pension för eventuella ThreadX tjänst anrop som görs inifrån programmets timer-funktion.*

## <a name="relative-time"></a>Relativ tid

Utöver de program timers som nämnts tidigare, ger ThreadX en enda stegvis ökning av 32-bitars Ticket-räknare. Ticket eller *tiden* ökas med ett vid varje timer-avbrott.

Programmet kan läsa eller ange denna 32-bitars räknare genom anrop till ***tx_time_get** _ och _ *_tx_time_set_* *. Användningen av den här skal räknaren avgörs helt av programmet. Den används inte internt av ThreadX.

## <a name="interrupts"></a>Avbrott

Snabba svar på asynkrona händelser är huvud funktionen för inbäddade program i real tid. Programmet vet att en sådan händelse föreligger genom maskin varu avbrott.

Ett avbrott är en asynkron ändring i processor körningen. När ett avbrott uppstår sparar *avbrotts* processorn vanligt vis en liten del av den aktuella körningen på stacken och överför kontrollen till lämplig avbrotts vektor. Avbrotts vektorn är i själva verket bara adressen till den rutin som ansvarar för att hantera det speciella typ avbrottet. Den exakta avbrotts hanterings proceduren är processor information.

### <a name="interrupt-control"></a>Avbrotts kontroll

Med tjänsten ***tx_interrupt_control*** kan program aktivera och inaktivera avbrott. Föregående avbrott för att aktivera/inaktivera position returneras av den här tjänsten. Det är viktigt att nämna att avbrotts kontrollen endast påverkar det program segment som körs för tillfället. Om t. ex. en tråd inaktiverar avbrott, förblir de bara inaktiverade under körningen av tråden.

> [!NOTE]
> *Ett icke-Maskbart avbrott (NMI) är ett avbrott som inte kan inaktive ras av maskin varan. Ett sådant avbrott kan användas av ThreadX-program. Programmets NMI hanterings rutin får dock inte användas för ThreadX kontext hantering eller API-tjänster.*

### <a name="threadx-managed-interrupts"></a>ThreadX hanterade avbrott

ThreadX tillhandahåller program med slutförd avbrott-hantering. Den här hanteringen omfattar att spara och återställa kontexten för den avbrutna körningen. Dessutom tillåter ThreadX att vissa tjänster anropas inifrån ISR: er (Interrupt service rutiner). Följande är en lista över ThreadX-tjänster som tillåts från Application ISR: er.

```c
tx_block_allocate
tx_block_pool_info_get tx_block_pool_prioritize
tx_block_pool_performance_info_get
tx_block_pool_performance_system_info_get tx_block_release
tx_byte_pool_info_get tx_byte_pool_performance_info_get
tx_byte_pool_performance_system_info_get
tx_byte_pool_prioritize tx_event_flags_info_get
tx_event_flags_get tx_event_flags_set
tx_event_flags_performance_info_get
tx_event_flags_performance_system_info_get
tx_event_flags_set_notify tx_interrupt_control
tx_mutex_performance_info_get
tx_mutex_performance_system_info_get tx_queue_front_send
tx_queue_info_get tx_queue_performance_info_get
tx_queue_performance_system_info_get tx_queue_prioritize
tx_queue_receive tx_queue_send tx_semaphore_get
tx_queue_send_notify tx_semaphore_ceiling_put
tx_semaphore_info_get tx_semaphore_performance_info_get
tx_semaphore_performance_system_info_get
tx_semaphore_prioritize tx_semaphore_put tx_thread_identify
tx_semaphore_put_notify tx_thread_entry_exit_notify
tx_thread_info_get tx_thread_resume
tx_thread_performance_info_get
tx_thread_performance_system_info_get
tx_thread_stack_error_notify tx_thread_wait_abort tx_time_get
tx_time_set tx_timer_activate tx_timer_change
tx_timer_deactivate tx_timer_info_get
tx_timer_performance_info_get
tx_timer_performance_system_info_get
```

> [!IMPORTANT]
> *SUS Pension tillåts inte från ISR: er. Därför måste **wait_option** parameter för alla ThreadX-tjänst anrop som görs från en ISR anges till **TX_NO_WAIT**.*

### <a name="isr-template"></a>ISR-mall

För att hantera program avbrott måste flera ThreadX-verktyg anropas i början och slutet av Application ISR: er. Det exakta formatet för avbrotts hantering varierar mellan olika portar.

Följande små kod segment är typiska för de flesta ThreadX-hanterade ISR: er. I de flesta fall är den här bearbetningen i sammansättnings språk.

```c
_application_ISR_vector_entry:

; Save context and prepare for

; ThreadX use by calling the ISR

; entry function.

CALL _tx_thread_context_save

; The ISR can now call ThreadX

; services and its own C functions

; When the ISR is finished, context

; is restored (or thread preemption)

; by calling the context restore ; function. Control does not return!

JUMP _tx_thread_context_restore
```

### <a name="high-frequency-interrupts"></a>Höga frekvens avbrott

Vissa avbrott sker i en sådan hög frekvens att spara och återställa en fullständig kontext vid varje avbrott förbrukar överdriven bearbetnings bandbredd. I sådana fall är det vanligt att programmet har ett litet insamlings språk för en ISR som gör en begränsad mängd bearbetning för en majoritet av dessa höga frekvens avbrott.

Efter en viss tidpunkt kan den lilla ISR behöva interagera med ThreadX. Detta åstadkommer du genom att anropa start-och slut funktionerna som beskrivs i ovanstående mall.

### <a name="interrupt-latency"></a>Avbrotts svars tid

ThreadX låser ut avbrott under korta tids perioder. Det maximala antalet tids avbrott är inaktiverat i den tid som krävs för att spara eller återställa en tråds kontext.
