---
title: Kapitel 3 – Funktionella komponenter i Azure RTOS ThreadX SMP
description: Det här kapitlet innehåller en beskrivning av de höga Azure RTOS ThreadX SMP-kerneln ur ett funktionellt perspektiv.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04676491f8ccaa98fa9ad396c221c38901c188b420ed710da3c96d863b49e6c5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799261"
---
# <a name="chapter-3---functional-components-of-azure-rtos-threadx-smp"></a>Kapitel 3 – Funktionella komponenter i Azure RTOS ThreadX SMP

Det här kapitlet innehåller en beskrivning av de höga Azure RTOS ThreadX SMP-kerneln ur ett funktionellt perspektiv. Varje funktionell komponent presenteras på ett sätt som är lätt att förstå.

## <a name="execution-overview"></a>Körningsöversikt

Det finns fyra typer av programkörning i ett ThreadX SMP-program: initiering, trådkörning, avbrottstjänstrutiner (ISR) och programtimers.

Bild 1 på sidan 45 visar varje typ av programkörning. Mer detaljerad information om var och en av dessa typer finns i efterföljande avsnitt i det här kapitlet.

### <a name="initialization"></a>Initiering
Som namnet antyder är detta den första typen av programkörning i ett ThreadX SMP-program. Initieringen omfattar all programkörning mellan processoråterställningen och startpunkten för *trådschemaläggningsloopen.*

> [!IMPORTANT]
> Initieringen utförs av eller initieras av core 0, vilket är den standardkärna som körs efter återställning.

### <a name="thread-execution"></a>Trådkörning
När initieringen är klar går varje kärna som kör ThreadX SMP in i sin trådschemaläggningsloop. Schemaläggningsloopen söker efter en programtråd som är redo för körning på kärnan. När en färdig tråd hittas överför ThreadX SMP kontroll till den. När tråden är klar (eller när en annan tråd med högre prioritet blir klar) överförs körningen tillbaka till trådschemaslingan för att hitta nästa tråd med högst prioritet på varje kärna.

Den här processen för kontinuerlig körning och schemaläggning av trådar är den vanligaste typen av programkörning i ThreadX SMP-program.

![Trådkörning](media/image4.png)

**BILD 1. Typer av programkörning**

### <a name="interrupt-service-routines-isr"></a>ISR (Interrupt Service Routines)
Avbrott är hörnstenen i realtidssystem. Utan avbrott skulle det vara mycket svårt att svara på förändringar i den externa världen inom rimlig tid. Vid identifiering av ett avbrott sparar processorn viktig information om den aktuella programkörningen (vanligtvis i stacken) och överför sedan kontrollen till ett fördefinierat programområde. Det här fördefinierade programområdet kallas ofta avbrottstjänstrutin.

I de flesta fall inträffar avbrott under trådkörning (eller i trådschemaläggningsloopen). Avbrott kan dock också inträffa i en isr-körning eller en programtimer.

Alla kärnor tillåts bearbeta avbrott. Mappningen av avbrott till kärnor är under direkt kontroll av programmet. ThreadX SMP-timeravbrottet tilldelas som standard till core 0 för bearbetning. Se koden i *tx_timer_interrupt. S* för implementering av den här tilldelningen.

### <a name="application-timers"></a>Programtimerar
Programtimers liknar ISR:er, förutom att maskinvaruimplementering (vanligtvis ett enda periodiskt maskinvaruavbrott används) är dolt från programmet. Sådana timers används av program för att utföra time outs, periodiska åtgärder och/eller watchdog-tjänster. Precis som ISR avbryter programtimers oftast trådkörningen. Till skillnad från ISR kan dock programtimers inte avbryta varandra.

> [!NOTE]
> Precis som trådar kan programtimerar undantas från körning på valfri kärna.

## <a name="memory-usage"></a>Minnesanvändning

ThreadX SMP finns tillsammans med program. Därför bestäms användningen av statiskt minne (eller fast minne) av ThreadX SMP av utvecklingsverktygen. till exempel kompilatorn, länkaren och lokaliseraren. Användningen av dynamiskt minne (eller körningsminne) är under direkt kontroll av programmet.

> [!NOTE]
> Allt minne som används av ThreadX SMP måste vara sammanhängande och tillgängligt i cacheminnet från alla kärnor som kör ThreadX SMP.

### <a name="static-memory-usage"></a>Statisk minnesanvändning
De flesta utvecklingsverktyg delar in programavbildningen i fem grundläggande *områden:* instruktion, *konstant,* *initierade data,* *oinitierade data* och *systemstack*. Bild 2 på sidan 47 visar ett exempel på dessa minnesområden.

![Statisk minnesanvändning](media/image5.png)

**BILD 2. Exempel på minnesområde**

Det är viktigt att förstå att detta bara är ett exempel. Den faktiska statiska minneslayouten är specifik för processorn, utvecklingsverktygen och den underliggande maskinvaran.

Instruktionsområdet innehåller alla programprocessorinstruktioner. Det här området är vanligtvis det största och finns ofta i ROM.

Konstantområdet innehåller olika kompilerade konstanter, inklusive strängar som definierats eller refererats i programmet. Dessutom innehåller det här området den "inledande kopian" av det initierade dataområdet. Under kompilatorns initieringsprocess används den här delen av konstantområdet för att konfigurera det initierade dataområdet i RAM-minnet. Det konstanta området följer vanligtvis instruktionsområdet och finns ofta i ROM.

Initierade data och oinitierade dataområden innehåller alla globala och statiska variabler. Dessa områden finns alltid i RAM-minnet.

Systemstacken konfigureras vanligtvis direkt efter de initierade och oinitierade dataområdena. Systemstacken används av kompilatorn under initieringen, sedan av ThreadX SMP under initieringen och därefter i ISR-bearbetning.

### <a name="dynamic-memory-usage"></a>dynamiskt minne användning
Som tidigare nämnts är dynamisk minnesanvändning under direkt kontroll av programmet. Kontrollblock och minnesområden som är associerade med stackar, köer och minnespooler kan placeras var som helst i målets minnesutrymme. Det här är en viktig funktion eftersom det underlättar enkel användning av olika typer av fysiskt minne.

Anta till exempel att en målmaskinvarumiljö har både snabbt minne och långsamt minne. Om programmet behöver extra prestanda för en tråd med hög prioritet kan dess kontrollblock (TX_THREAD) och stack placeras i det snabba minnesområdet, vilket kan förbättra dess prestanda mycket.

## <a name="initialization"></a>Initiering 
Det är viktigt att förstå initieringsprocessen. Den första maskinvarumiljön konfigureras här. Dessutom är det här som programmet får sin första personlighet.

> [!IMPORTANT]
> ThreadX SMP försöker använda (när det är möjligt) det fullständiga utvecklingsverktygets initieringsprocess. Detta gör det enklare att uppgradera till nya versioner av utvecklingsverktygen i framtiden.

### <a name="system-reset-vector"></a>Systemåterställningsvektor 
Alla mikroprocessorer har återställningslogik. När en återställning sker (maskinvara eller programvara) hämtas adressen till programmets startpunkt från en specifik minnesplats. När startpunkten har hämtats överför processorn kontrollen till den platsen. 

Programmets startpunkt skrivs ofta i det inbyggda sammansättningsspråket och tillhandahålls vanligtvis av utvecklingsverktygen (åtminstone i mallformulär). I vissa fall levereras en särskild version av inmatningsprogrammet med ThreadX SMP. 

### <a name="development-tool-initialization"></a>Initiering av utvecklingsverktyg
När initieringen på låg nivå är klar överförs kontrollen till utvecklingsverktygets initiering på hög nivå. Det här är vanligtvis den plats där initierade globala och statiska C-variabler konfigureras. Kom ihåg att deras ursprungliga värden hämtas från det konstanta området. Den exakta initieringsbearbetningen är specifik för utvecklingsverktyg.

### <a name="main-function"></a>main Function 
När initieringen av utvecklingsverktyget är klar överförs kontrollen till den huvudfunktion som *användaren har angett.* Nu styr programmet vad som händer härnäst. För de flesta program anropar huvudfunktionen *bara tx_kernel_enter*, vilket är posten i ThreadX SMP. Program kan dock utföra preliminär bearbetning (vanligtvis för maskinvaru initialisering) innan de anger ThreadX SMP.

> [!IMPORTANT]
> Anropet till tx_kernel_enter returnerar inte, så placera inte någon bearbetning efter den!

### <a name="tx_kernel_enter"></a>tx_kernel_enter 
Entry-funktionen samordnar initieringen av olika interna ThreadX SMP-datastrukturer och anropar sedan programmets definitionsfunktion *tx_application_define*.

När *tx_application_define* returneras överförs kontrollen till trådschemaslingan. Detta markerar slutet på initieringen!

### <a name="application-definition-function"></a>Funktion för programdefinition
Funktionen *tx_application_define* definierar alla inledande programtrådar, köer, semaforer, mutexer, händelseflaggor, minnespooler och timers. Det är också möjligt att skapa och ta bort systemresurser från trådar under programmets normala drift. Alla inledande programresurser definieras dock här.

Funktionen *tx_application_define* har en enda indataparameter och det är värt att nämna. Den *första tillgängliga RAM-adressen* är den enda indataparametern för den här funktionen. Den används vanligtvis som utgångspunkt för inledande minnesallokeringar för körning av trådstackar, köer och minnespooler.

> [!IMPORTANT]
> När initieringen är klar kan endast en körande tråd skapa och ta bort systemresurser, inklusive andra trådar. Därför måste minst en tråd skapas under initieringen.

### <a name="interrupts"></a>Avbryter 
Avbrott inaktiveras under hela initieringsprocessen. Om programmet på något sätt aktiverar avbrott kan oförutsägbart beteende uppstå. Bild 3 på sidan 52 visar hela initieringsprocessen, från systemåterställning till programspecifik initiering.

## <a name="thread-execution"></a>Trådkörning

Schemaläggning och körning av programtrådar är den viktigaste aktiviteten i ThreadX SMP. En tråd definieras vanligtvis som ett halvoberoende programsegment med ett dedikerat syfte. Den kombinerade bearbetningen av alla trådar gör ett program.

Trådar skapas dynamiskt genom att anropa tx_thread_create *under* initieringen eller under trådkörningen. Trådar skapas antingen i tillståndet *klar eller* *inaktiverad.*

![SMP-initieringsprocess](media/image6.png)

**BILD 3. SMP-initieringsprocess**

### <a name="thread-execution-states"></a>Körnings tillstånd för trådar  
Att förstå de olika bearbetnings tillstånden för trådar är en viktig faktor för att förstå hela den flertrådade miljön. I ThreadX SMP finns det fem olika tråd tillstånd: *ready*, *suspended*, *executing*, *terminated*, and *completed*. Bild 4 visar trådtillståndsövergångsdiagrammet för ThreadX SMP.

![Körnings tillstånd för trådar](media/image7.png)

**BILD 4. Trådtillståndsövergång**

En tråd har *statusen Klar* när den är redo för körning. En färdig tråd körs inte förrän den är den högsta prioritetstråden i tillståndet klar. När detta inträffar kör ThreadX SMP tråden, som sedan ändrar dess tillstånd till *att köra*.

Om en tråd med högre prioritet blir klar återgår den körande tråden till ett *redo* tillstånd. Den nyligen färdiga högprioritetstråden körs sedan, vilket ändrar dess logiska tillstånd till *att köra*. Den här övergången *mellan* *redo och* körbara tillstånd sker varje gång trådförseningen inträffar.

Vid ett givet tillfälle är endast en tråd i *körningstillstånd.* Det beror på att en tråd i *körningstillståndet* har kontroll över den underliggande processorn.

Trådar i *pausat tillstånd* är inte berättigade till körning. Orsaker till att  vara i pausat tillstånd är till exempel stängning av tid, kömeddelanden, semaforer, mutexer, händelseflaggor, minne och grundläggande trådavstängning. När orsaken till indragningen har tagits bort placeras tråden tillbaka i ett *tillstånd som är* redo.

En tråd i ett *slutfört* tillstånd är en tråd som har slutfört bearbetningen och returnerats från dess postfunktion. Postfunktionen anges när tråden skapas. En tråd i ett slutfört *tillstånd* kan inte köras igen.

En tråd är i ett *avslutat* tillstånd eftersom en annan tråd eller själva tråden kallas *för tx_thread_terminate tjänsten.* En tråd i ett *avslutat tillstånd* kan inte köras igen.

> [!IMPORTANT]
> Om du vill starta om en slutförd eller avslutad tråd måste programmet först ta bort tråden. Den kan sedan skapas och startas om.

### <a name="thread-entryexit-notification"></a>Meddelande om trådinmatning/avslut  
För vissa program kan det vara fördelaktigt att få ett meddelande när en viss tråd anges för första gången, när den är klar eller avslutas. ThreadX SMP ger den  här möjligheten via tx_thread_entry_exit_notify tjänsten. Den här tjänsten registrerar en programmeddelandefunktion för en specifik tråd, som anropas av ThreadX SMP när tråden börjar köras, slutförs eller avslutas. När programmets meddelandefunktion har anropats kan den utföra den programspecifika bearbetningen. Detta innebär vanligtvis att informera en annan programtråd om händelsen via en primitiv ThreadX SMP-synkronisering.

### <a name="thread-priorities"></a>Trådprioriteringar  
Som tidigare nämnts är en tråd ett halvoberoende programsegment med ett dedikerat syfte. Alla trådar skapas dock inte lika! Det dedikerade syftet med vissa trådar är mycket viktigare än andra. Den här heterogena typen av tråd prioritet är ett kännetecknande för inbäddade realtidsprogram.

ThreadX SMP avgör en tråds prioritet när tråden skapas genom att tilldela ett numeriskt värde som representerar dess *prioritet*. Det maximala antalet ThreadX SMP-prioriteter kan konfigureras från 32 till 1 024 i steg om 32. Det faktiska maximala antalet prioriteter bestäms av den *TX_MAX_PRIORITIES* konstanten under kompileringen av ThreadX SMP-biblioteket. Att ha ett större antal prioriteter ökar inte bearbetningens omkostnader avsevärt. För varje grupp med 32 prioritetsnivåer krävs dock ytterligare 128 byte RAM-minne för att hantera dem. Till exempel kräver 32 prioritetsnivåer 128 byte RAM, 64 prioritetsnivåer kräver 256 byte RAM och 96 prioritetsnivåer kräver 384 byte RAM-minne.

Som standard har ThreadX SMP 32 prioritetsnivåer, från prioritet 0 till prioritet 31.

Numeriskt mindre värden innebär högre prioritet. Prioritet 0 representerar därför den högsta prioriteten, medan prioritet (*TX_MAX_PRIORITIES*-1) representerar den lägsta prioriteten.

Flera trådar kan ha samma prioritet som förlitar sig på schemaläggning av schemaläggning eller tidsdelicering. Dessutom kan trådprioriteringar ändras under körning.

### <a name="thread-scheduling"></a>Trådschemaläggning 
ThreadX SMP schemalägger trådar baserat på deras prioritet. Den färdiga tråden med högst prioritet körs först. Om flera trådar med samma prioritet är klara körs de med *FIFO(first-in-first-out).*

Som standard schemalägger ThreadX SMP trådarna med "n" högsta prioritet på de "n" tillgängliga processorerna. Om samtidig bearbetning endast krävs på färdiga trådar med samma prioritet, måste ThreadX SMP-biblioteket byggas med **TX_THREAD_SMP_EQUAL_PRIORITY** definieras.

> [!NOTE]
> Att alla trådar inledningsvis bara kan köras på core 0 genom att skapa ThreadX SMP-biblioteket med **TX_THREAD_SMP_ONLY_CORE_0_DEFAULT** definierat.

### <a name="round-robin-scheduling"></a>Schemaläggning med resursallokering  
ThreadX SMP stöder *schemaläggning av resursallokering* för flera trådar med samma prioritet. Detta åstadkoms genom samtal till *tx_thread_relinquish*. Den här tjänsten ger alla andra färdiga trådar med samma prioritet en chans att *köra innan tx_thread_relinquish* anroparen körs igen.

### <a name="time-slicing"></a>Time-Slicing 
*Tidsdelicering är* en annan form av schemaläggning med resursallokering. En tidssegment anger det maximala antalet timer tick (timeravbrott) som en tråd kan köra utan att ge upp processorn. I ThreadX SMP är tidsuppdeling tillgängligt perthread-basis. Trådens tidssegment tilldelas när den skapas och kan ändras under körningen. När en tidssegment går ut får alla andra färdiga trådar på samma prioritetsnivå en chans att köras innan den tidssnittade tråden körs igen.

En ny trådtidssegment ges till en tråd när den pausar, relinquishar, gör ett ThreadX SMP-tjänstanrop som orsakar avbrott eller är tidssegmenterad.

När en tidsutsnittad tråd preempteras återupptas den före andra färdiga trådar med samma prioritet under resten av dess tidssegment.

> [!IMPORTANT]
> Användning av tidsdeling resulterar i en liten mängd systemkostnader. Eftersom tidssegmentering endast är användbart i fall där flera trådar delar samma prioritet, bör trådar som har en unik prioritet inte tilldelas en tidssegment.

### <a name="preemption"></a>Avsats 
Preemption är en process för att tillfälligt avbryta en körningstråd till förmån för en tråd med högre prioritet. Den här processen är osynlig för den körande tråden. När tråden med högre prioritet är klar överförs kontrollen tillbaka till den exakta plats där avförbrukningen ägde rum.

Det här är en mycket viktig funktion i realtidssystem eftersom det underlättar snabb svar på viktiga programhändelser. Även om det är en mycket viktig funktion kan förbrukningen också vara en källa till en mängd olika problem, inklusive utsvältning, höga kostnader och prioritetsinversion.

### <a name="preemption-threshold"></a>Tröskel för tröskel™ 
För att underlätta några av de inbyggda problemen med avspärrning tillhandahåller ThreadX SMP en unik och avancerad funktion som kallas *preemption-threshold*.

Med ett tröskelvärde för avaktivering kan en tråd ange ett *prioritetstak* för inaktivering av avaktivering. Trådar som har högre prioritet än taket tillåts fortfarande att preempt, medan de som är mindre än taket inte tillåts preempt.

Anta till exempel att en tråd med prioritet 20 bara interagerar med en grupp trådar som har prioriteter mellan 15 och 20. I dess kritiska avsnitt kan tråden med prioritet 20 ange tröskelvärdet för spärr till 15, vilket förhindrar avspärrning från alla trådar som den interagerar med. Detta tillåter fortfarande mycket viktiga trådar (prioriteringar mellan 0 och 14) för att preempta den här tråden under dess kritiska avsnittsbearbetning, vilket resulterar i mycket mer responsiv bearbetning.

Naturligtvis är det fortfarande möjligt för en tråd att inaktivera all avaktivering genom att ange dess tröskelvärde för avaktivering till 0. Dessutom kan tröskelvärdet för preemption ändras under körning.

> [!IMPORTANT]
> Om du använder preemption-threshold inaktiveras tidsdelicering för den angivna tråden.

### <a name="priority-inheritance"></a>Prioritetsarv 
ThreadX SMP stöder även valfritt prioritetsarv i dess mutex-tjänster som beskrivs senare i det här kapitlet. Med prioritetsarv kan en tråd med lägre prioritet tillfälligt anta prioriteten för en tråd med hög prioritet som väntar på en mutex som ägs av tråden med lägre prioritet. Den här funktionen hjälper programmet att undvika icke-terministisk prioritetsinversion genom att eliminera stillestånd av mellanliggande trådprioriteringar. Tröskel *för avspärrning kan naturligtvis* användas för att uppnå ett liknande resultat.

### <a name="thread-creation"></a>Skapa tråd 
Programtrådar skapas under initieringen eller under körningen av andra programtrådar. Det finns ingen gräns för hur många trådar som kan skapas av ett program.

### <a name="thread-control-block-tx_thread"></a>Block för trådkontroll TX_THREAD 
Egenskaperna för varje tråd finns i dess kontrollblock. Den här strukturen definieras i ***tx_api.h-filen.***

En tråds kontrollblock kan finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion.

Att hitta kontrollblocket i andra områden kräver lite mer försiktighet, precis som allt dynamiskt allokerat minne. Om ett kontrollblock allokeras i en C-funktion är det minne som är associerat med det en del av anropstrådens stack. I allmänhet bör du undvika att använda lokal lagring för kontrollblock eftersom när funktionen returnerar släpps allt dess lokala variabelstackutrymme – oavsett om en annan tråd använder den för ett kontrollblock!

I de flesta fall är programmet omedvetet om innehållet i trådens kontrollblock. Det finns dock vissa situationer, särskilt under felsökning, där det är användbart att titta på vissa medlemmar. Här följer några av de mer användbara kontrollblockmedlemmarna:

- **tx_thread_run_count** innehåller en räknare över hur många gånger tråden har schemalagts. En ökande räknare anger att tråden schemaläggs och körs.

- **tx_thread_state** innehåller tillståndet för den associerade tråden. Följande visar möjliga tråd tillstånd:

    - TX_READY(0x00)
    - TX_COMPLETED(0x01)
    - TX_TERMINATED(0x02)
    - TX_SUSPENDED(0x03)
    - TX_SLEEP(0x04)
    - TX_QUEUE_SUSP(0x05)
    - TX_SEMAPHORE_SUSP(0x06)
    - TX_EVENT_FLAG (0x07)
    - TX_BLOCK_MEMORY(0x08)
    - TX_BYTE_MEMORY (0x09)
    - TX_MUTEX_SUSP(0x0D)

> [!IMPORTANT]
> Naturligtvis finns det många andra intressanta fält i trådkontrollblocket, inklusive stackpekaren, tidssnittsvärdet, prioriteringar osv. Användare är välkommen att granska medlemmar i kontrollblock, men ändringar är strikt förbjudna!

> [!IMPORTANT]
> Det finns inget som motsvarar det tillstånd för "körning" som nämndes tidigare i det här avsnittet. Det är inte nödvändigt eftersom det bara finns en körningstråd i taget. Tillståndet för en körningstråd är också ***TX_READY***.

### <a name="currently-executing-thread"></a>Tråd som körs för närvarande 
Som tidigare nämnts körs bara en tråd vid en given tidpunkt. Det finns flera sätt att identifiera den körande tråden, beroende på vilken tråd som gör begäran.

Ett programsegment kan hämta kontrollblockadressen för den körande tråden genom att anropa ***tx_thread_identify***. Detta är användbart i delade delar av programkoden som körs från flera trådar.

I felsökningssessioner kan användare undersöka den interna ThreadX SMP-pekarmatrisen ***_tx_thread_current_ptr[core]***. Den innehåller kontrollblocksadressen för den tråd som körs för närvarande. Om pekaren är NULL körs ingen programtråd. Det vill säga, ThreadX SMP väntar i sin schemaläggningsloop på att en tråd ska bli redo.

### <a name="thread-stack-area"></a>Trådstackområde 
Varje tråd måste ha en egen stack för att spara kontexten för den senaste körningen och kompilatorn. De flesta C-kompilatorer använder stacken för att göra funktionsanrop och för att tillfälligt allokera lokala variabler. Bild 5 på sidan 61 visar en typisk trådstack.

![Trådstackområde](media/image8.png)

**BILD 5. Typisk trådstack**

Var en trådstack finns i minnet är upp till programmet. Stackområdet anges när tråden skapas och kan finnas var som helst i målets adressutrymme. Det här är en viktig funktion eftersom den gör det möjligt för program att förbättra prestanda för viktiga trådar genom att placera stacken i ram-minne med hög hastighet.

Hur stor en stack bör vara är en av de vanligaste frågorna om trådar. En tråds stackområde måste vara tillräckligt stort för att hantera kapsling av sämsta funktionsanrop, lokal variabelallokering och spara dess senaste körningskontext.

Den minsta stackstorleken, **TX_MINIMUM_STACK**, definieras av ThreadX SMP. En stack av den här storleken har stöd för att spara en tråds kontext och minsta mängd funktionsanrop och lokal variabelallokering.

För de flesta trådar är dock den minsta stackstorleken för liten och användaren måste fastställa storlekskravet för sämsta fall genom att undersöka funktionsanropskapsling och lokal variabelallokering. Naturligtvis är det alltid bättre att börja med ett större stackområde.

När programmet har felsökts är det möjligt att justera trådstackens storlek om minnet är mindre. Ett favorittrick är att förinställa alla stackområden med ett enkelt identifierbart datamönster som (0xEFEF) innan du skapar trådarna. När programmet har genomförts noggrant kan du undersöka stackområdena för att se hur mycket stack som faktiskt användes genom att hitta den del av stacken där datamönstret fortfarande är intakt. Bild 6 visar en stackförinställning för att 0xEFEF efter noggrann trådkörning.

> [!IMPORTANT]
> Som standard initierar ThreadX SMP varje byte av varje trådstack med värdet 0xEF.

### <a name="memory-pitfalls"></a>Minnesgropar 
Stackkraven för trådar kan vara stora. Därför är det viktigt att utforma programmet så att det har ett rimligt antal trådar. Dessutom måste viss försiktighet vidtas för att undvika överdriven stackanvändning i trådar. Rekursiva algoritmer och stora lokala datastrukturer bör undvikas.

I de flesta fall orsakar en spillstack trådkörningen att skada minnet intill (vanligtvis 

![Minnesgropar](media/image9.png)

**BILD 6. Stackförinställning till 0xEFEF**

före) dess stackområde. Resultaten är oförutsägbara, men resulterar oftast i en icke-naturlig förändring i programräknaren. Detta kallas ofta för att "hoppa till de vise". Det enda sättet att förhindra detta är naturligtvis att se till att alla trådstackar är tillräckligt stora.

### <a name="optional-run-time-stack-checking"></a>Valfri körningsstackkontroll  
ThreadX SMP ger möjlighet att kontrollera om varje tråds stack är skadad under körningen. Som standard fyller ThreadX SMP varje byte av trådstackar med ett 0xEF datamönster under skapandet. Om programmet skapar ThreadX SMP-biblioteket med ***TX_ENABLE_STACK_CHECKING** _ definierat undersöker ThreadX SMP varje tråds stack för att se om den är skadad när den pausas eller återupptas. Om stackfel identifieras anropar ThreadX SMP programmets stackfelhanteringsrutin enligt anropet till _tx_thread_stack_error_notify*. Om ingen stackfelhanterare har angetts anropar ThreadX SMP annars den *interna _tx_thread_stack_error_handler* rutinen.

### <a name="reentrancy"></a>Återinträde 
En av de verkliga problem med flertrådstråd är att samma C-funktion kan anropas från flera trådar. Detta ger stor kraft och hjälper också till att minska kodutrymmet. Det kräver dock att C-funktioner som anropas från flera trådar *är reentrant*.

I princip lagrar en återentrant-funktion anroparens returadress på den aktuella stacken och förlitar sig inte på globala eller statiska C-variabler som den tidigare konfigurerade. De flesta kompilatorer placerar returadressen i stacken. Därför behöver programutvecklare bara bekymra sig om användningen av *globala och* *statiska .*

Ett exempel på en icke-reentrant-funktion är strängtokenfunktionen "strtok" som finns i standard-C-biblioteket. Den här funktionen kommer ihåg föregående sträng pekare för efterföljande anrop. Det gör detta med en statisk sträng pekare. Om den här funktionen anropas från flera trådar returnerar den troligen en ogiltig pekare.

### <a name="thread-priority-pitfalls"></a>Fallgropar för trådprioritet 
Att välja trådprioriteringar är en av de viktigaste aspekterna av flertrådstråding. Ibland är det lockande att tilldela prioriteringar baserat på en uppfattad trådpriorit i stället för att fastställa exakt vad som krävs under körningen. Missbruk av trådprioriteringar kan begränsa andra trådar, skapa prioritetsinversion, minska bearbetningsbandbredden och göra programmets körningsbeteende svårt att förstå.

Som tidigare nämnts tillhandahåller ThreadX SMP en prioritetsbaserad, förebyggande schemaläggningsalgoritm. Trådar med lägre prioritet körs inte förrän det inte finns några trådar med högre prioritet redo för körning. Om en tråd med högre prioritet alltid är redo körs aldrig trådar med lägre prioritet. Det här villkoret kallas *för trådsvält*.

De flesta problem med trådsvält identifieras tidigt i felsökningen och kan lösas genom att säkerställa att trådar med högre prioritet inte körs kontinuerligt. Alternativt kan logik läggas till i programmet som gradvis höjer prioriteten för utsvultna trådar tills de får möjlighet att köra.

En annan fallgrop som är associerad med *trådprioriteringar är prioritetsinversion*. Prioritetsinversion sker när en tråd med högre prioritet pausas eftersom en tråd med lägre prioritet har en nödvändig resurs. I vissa fall är det naturligtvis nödvändigt att två trådar med olika prioritet delar en gemensam resurs. Om dessa trådar är de enda som är aktiva begränsas prioritetstiden för inversion av den tid då tråden med lägre prioritet innehåller resursen. Det här villkoret är både deterministiskt och ganska normalt. Men om trådar med mellanliggande prioritet blir aktiva under det här prioritetsinversionsvillkoret är prioritetens inversionstid inte längre deterministisk och kan orsaka ett programfel.

Det finns huvudsakligen tre olika metoder för att förhindra icke-terministisk prioritetsinversion i ThreadX SMP. För det första kan val av programprioritet och körningsbeteende utformas på ett sätt som förhindrar problemet med prioritetsinversion. För det andra kan trådar med lägre prioritet använda tröskelvärdet *preemption för* att blockera avspärrning från mellanliggande trådar samtidigt som de delar resurser med trådar med högre prioritet. Slutligen kan trådar som använder ThreadX SMP mutex-objekt för  att skydda systemresurser använda valfritt mutex-prioritetsarv för att eliminera icke-terministisk prioritetsinversion.

### <a name="priority-overhead"></a>Omkostnader för prioritet 
Ett av de mest förbisedda sätten att minska omkostnaderna vid flertrådsläsning är att minska antalet kontextväxlar. Som tidigare nämnts sker en kontextväxel när körning av en tråd med högre prioritet prioriteras framför den som kör tråden. Det kan vara värt att nämna att trådar med högre prioritet kan bli redo på grund av både externa händelser (till exempel avbrott) och från tjänstanrop som görs av den körande tråden.

För att illustrera de effekter som trådprioriteringar har på kontextväxelkostnader förutsätter du en tretrådsmiljö med trådar *med thread_1*, *thread_2* *och thread_3*. Anta vidare att alla trådar är i ett tillstånd av stängning som väntar på ett meddelande. När thread_1 får ett meddelande vidarebefordras det omedelbart till thread_2. Thread_2 vidarebefordrar sedan meddelandet till thread_3. Thread_3 ignorerar bara meddelandet. När varje tråd har bearbetar meddelandet går det tillbaka och väntar på ett annat meddelande.

Den bearbetning som krävs för att köra dessa tre trådar varierar mycket beroende på deras prioriteringar. Om alla trådar har samma prioritet sker en enda kontextväxel innan varje tråd körs. Kontextväxeln inträffar när varje tråd pausar i en tom meddelandekö.

Men om thread_2 högre prioritet än thread_1 och thread_3 högre prioritet än thread_2, fördubblas antalet kontextväxlar. Det beror på att en annan kontextväxel inträffar *i tx_queue_send tjänsten* när den identifierar att en tråd med högre prioritet nu är klar.

Mekanismen threadX SMP preemption-threshold kan undvika dessa extra kontextväxlar och fortfarande tillåta tidigare nämnda prioritetsval. Det här är en viktig funktion eftersom den möjliggör flera trådprioriteringar under schemaläggning, samtidigt som en del av den oönskade kontextväxlingen mellan dem elimineras under trådkörningen.

### <a name="run-time-thread-performance-information"></a>Prestandainformation för körningstråd 
ThreadX SMP tillhandahåller valfri prestandainformation för körningstrådar. Om ThreadX SMP-biblioteket och programmet ***har skapats med TX_THREAD_ENABLE_PERFORMANCE_INFO,*** ackumulerar ThreadX SMP följande information:

Totalt antal för det övergripande systemet:

- trådantaganden
- trådavstängningar
- service call preemptions
- avbrottsavbrott
- prioritetsinversioner
- tidssegment
- relinquishes
- timeouter för trådar
- brytningsavstängningar
- inaktivt system returnerar
- icke-inaktivt system returnerar

Totalt antal för varje tråd:

- återantaganden
- Suspensioner
- service call preemptions
- avbrottsavbrott
- prioritetsinversioner
- tidssegment
- trådrelinquishes
- timeouter för trådar
- brytningsavstängningar

Den här informationen är tillgänglig under körning via de tjänster som *tx_thread_performance_info_get* och *tx_thread_performance_system_info_get*. Trådprestandainformation är användbar för att avgöra om programmet fungerar korrekt. Det är också användbart för att optimera programmet. Ett relativt stort antal tjänstanropsanrop kan till exempel tyda på att trådens prioritet och/eller tröskelvärde för avspärrning är för lågt. Dessutom kan ett relativt lågt antal inaktiva systemreturer tyda på att trådar med lägre prioritet inte pausas tillräckligt.

### <a name="debugging-pitfalls"></a>Felsökning av fallgropar 
Det är lite svårare att felsöka flertrådade program eftersom samma programkod kan köras från flera trådar. I sådana fall räcker det kanske inte med en brytpunkt. Felsökaren måste också visa den aktuella tråd pekarmatrisen ***_tx_thread_current_ptr[core]*** med hjälp av en villkorlig brytpunkt för att se om den anropande tråden är den som ska felsökas.

Mycket av detta hanteras i stödpaket med fleratrådar som erbjuds via olika leverantörer av utvecklingsverktyg. Tack vare den enkla designen är det relativt enkelt att integrera ThreadX SMP med olika utvecklingsverktyg.

Stackstorlek är alltid ett viktigt felsökningsämne vid flertrådsläsning. När ett oförklarligt beteende observeras är det vanligtvis en bra första gissning att öka stackstorlekarna för alla trådar– särskilt stackstorleken för den sista tråden som ska köras!

> [!IMPORTANT]
> Det är också en bra idé att skapa ThreadX SMP-biblioteket med TX_ENABLE_STACK_CHECKING definierat. Detta hjälper dig att isolera felproblem i stacken så tidigt i bearbetningen som möjligt!

## <a name="message-queues"></a>Meddelandeköer

Meddelandeköer är det primära sättet att intertråda kommunikation i ThreadX SMP. Ett eller flera meddelanden kan finnas i en meddelandekö. En meddelandekö som innehåller ett enda meddelande kallas ofta för en *postlåda*.

Meddelanden kopieras till en kö av *tx_queue_send* och kopieras från en kö av *tx_queue_receive*. Det enda undantaget till detta är när en tråd pausas i väntan på ett meddelande i en tom kö. I det här fallet placeras nästa meddelande som skickas till kön direkt i trådens målområde.

Varje meddelandekö är en offentlig resurs. ThreadX SMP har inga begränsningar för hur meddelandeköer används.

### <a name="creating-message-queues"></a>Skapa meddelandeköer 
Meddelandeköer skapas antingen under initieringen eller under körning av programtrådar. Det finns ingen gräns för antalet meddelandeköer i ett program. 

### <a name="message-size"></a>Meddelandestorlek 
Varje meddelandekö stöder ett antal fasta meddelanden. De tillgängliga meddelandestorlekarna är 1 till 16 32-bitars ord. Meddelandestorleken anges när kön skapas. 

Programmeddelanden som är större än 16 ord måste skickas via pekare. Detta åstadkoms genom att skapa en kö med en meddelandestorlek på 1 ord (tillräckligt för att hålla en pekare) och sedan skicka och ta emot meddelandepekare i stället för hela meddelandet.

### <a name="message-queue-capacity"></a>Meddelandekökapacitet 
Antalet meddelanden som en kö kan innehålla är en funktion med meddelandestorleken och storleken på det minnesområde som angavs när den skapades. Den totala meddelandekapaciteten för kön beräknas genom att dela upp antalet byte i varje meddelande i det totala antalet byte i det angivna minnesområdet.

Om till exempel en meddelandekö som stöder en meddelandestorlek på 1 32-bitars ord (4 byte) skapas med ett minnesutrymme på 100 byte är dess kapacitet 25 meddelanden.

### <a name="queue-memory-area"></a>Köminnesområde 
Som tidigare nämnts anges minnesområdet för buffring av meddelanden när kön skapas. Precis som andra minnesområden i ThreadX SMP kan den finnas var som helst i målets adressutrymme.

Det här är en viktig funktion eftersom den ger programmet stor flexibilitet. Ett program kan till exempel hitta minnesområdet för en viktig kö i höghastighets-RAM för att förbättra prestandan.

### <a name="thread-suspension"></a>Trådavstängning  
Programtrådar kan pausa vid försök att skicka eller ta emot ett meddelande från en kö. Normalt innebär trådavstängning att vänta på ett meddelande från en tom kö. Det är dock också möjligt för en tråd att pausa försök att skicka ett meddelande till en fullständig kö. 

När villkoret för instängning har lösts slutförs den begärda tjänsten och den väntande tråden återupptas. Om flera trådar pausas i samma kö återupptas de i den ordning som de pausades (FIFO).

Men prioritetsupptagande är också möjligt om programmet ***anropar tx_queue_prioritize*** innan kötjänsten som tar bort trådavstängningen. Köprioritetstjänsten placerar den högsta prioritetstråden längst fram i tjänstgöringslistan, samtidigt som alla andra pausade trådar finns kvar i samma FIFO-ordning.

Det finns också time out-fel för alla köavstängningar. I princip anger en time out det maximala antalet timer tick som tråden ska pausas. Om en time out inträffar återupptas tråden och tjänsten returnerar med lämplig felkod.

### <a name="queue-send-notification"></a>Skicka meddelande i kö  
För vissa program kan det vara fördelaktigt att meddelas när ett meddelande placeras i en kö. ThreadX SMP ger den  här möjligheten via tx_queue_send_notify tjänsten. Den här tjänsten registrerar den angivna programmeddelandefunktionen med den angivna kön. ThreadX SMP anropar därefter den här programmeddelandefunktionen när ett meddelande skickas till kön. Den exakta bearbetningen i programmeddelandefunktionen bestäms av programmet. Den består dock vanligtvis av att återuppta rätt tråd för bearbetning av det nya meddelandet.

### <a name="queue-event-chaining"></a>Händelsekedja i kö™  
Meddelandefunktionerna i ThreadX SMP kan användas för att länka ihop olika synkroniseringshändelser. Detta är vanligtvis användbart när en enda tråd måste bearbeta flera synkroniseringshändelser.

Anta till exempel att en enda tråd ansvarar för bearbetning av meddelanden från fem olika köer och även måste pausa när inga meddelanden är tillgängliga. Detta kan enkelt åstadkommas genom att registrera en programmeddelandefunktion för varje kö och införa ytterligare en inventerings-semaphore. Mer specifikt utför programmeddelandefunktionen en *tx_semaphore_put* när den anropas (antalet semaforer representerar det totala antalet meddelanden i alla fem köer). Bearbetningstråden pausar på den här  semaforen via tx_semaphore_get tjänsten. När semaphore är tillgänglig (i det här fallet när ett meddelande är tillgängligt!) återupptas bearbetningstråden. Sedan frågas varje kö efter ett meddelande, bearbetar det hittade meddelandet och utför en *tx_semaphore_get* väntar på nästa meddelande. Att åstadkomma detta utan händelsekedja är ganska svårt och kräver troligen fler trådar och/eller ytterligare programkod.

I allmänhet resulterar händelsekedjan i färre trådar, lägre omkostnader och mindre *RAM-krav.* Det ger också en mycket flexibel mekanism för att hantera synkroniseringskrav för mer komplexa system.

### <a name="run-time-queue-performance-information"></a>Prestandainformation för körningskö  
ThreadX SMP tillhandahåller valfri prestandainformation för körningsköer. Om ThreadX SMP-biblioteket och programmet ***har skapats med TX_QUEUE_ENABLE_PERFORMANCE_INFO,*** ackumuleras följande information i ThreadX SMP:

Totalt antal för det övergripande systemet:

- skickade meddelanden
- mottagna meddelanden
- kö tomma stängningar
- fullständiga stängningar av köer
- fullständiga fel returneras i kön (indragningen är inte speci-fied)
- timeouter för köer

Totalt antal för varje kö:

- skickade meddelanden
- mottagna meddelanden
- kö tomma stängningar
- fullständiga stängningar av köer
- fullständiga fel returneras i kön (indragningen är inte speci-fied)
- timeouter för köer

Den här informationen är tillgänglig under körning via tjänsterna *tx_queue_performance_info_get* och *tx_queue_performance_system_info_get*. Köprestandainformation är användbar för att avgöra om programmet fungerar korrekt. Det är också användbart för att optimera programmet. Ett relativt stort antal "fullständiga köavstängningar" tyder till exempel på att en ökning av köstorleken kan vara fördelaktigt.

### <a name="queue-control-block-tx_queue"></a>Blockblockering för kökontroll TX_QUEUE 
Egenskaperna för varje meddelandekö finns i dess kontrollblock. Den innehåller intressant information, till exempel antalet meddelanden i kön. Den här strukturen definieras i ***tx_api.h-filen.***

Kontrollblock för meddelandeköer kan också finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion.

### <a name="message-destination-pitfall"></a>Fallgrop för meddelandemål  
Som tidigare nämnts kopieras meddelanden mellan köområdet och programmets dataområden. Det är viktigt att se till att målet för ett mottaget meddelande är tillräckligt stort för att innehålla hela meddelandet. Om inte, kommer minnet efter meddelandets mål troligen att skadas. 

> [!WARNING]
> Detta är särskilt viktigt när ett för litet meddelandemål finns i stacken – ingenting som att skada returadressen för en funktion!

## <a name="counting-semaphores"></a>Räkna semaforer

ThreadX SMP tillhandahåller semaforer för 32-bitars räkning som sträcker sig i värde mellan 0 och 4 294 967 295. Det finns två åtgärder för att räkna semaforer: *tx_semaphore_get* och *tx_semaphore_put*. Åtgärden get minskar semaphore med en. Om semaphore är 0 lyckas inte get-åtgärden. Inversen av get-åtgärden är put-åtgärden. Det ökar semaphore med en.

Varje inventerings-semaphore är en offentlig resurs. ThreadX SMP har inga begränsningar för hur inventeringssemaforer används.

Räkna semaforer används vanligtvis för *ömsesidig exkludering.* Räkna semaforer kan dock också användas som en metod för händelseavisering.

### <a name="mutual-exclusion"></a>Ömsesidig exkludering 
Ömsesidig exkludering handlar om att kontrollera åtkomsten till trådar till vissa programområden (kallas även *kritiska avsnitt* eller *programresurser).* När det används för ömsesidig exkludering representerar det "aktuella antalet" för en semaphore det totala antalet trådar som tillåts åtkomst. I de flesta fall har räkning av semaforer som används för ömsesidig exkludering det inledande värdet 1, vilket innebär att endast en tråd kan komma åt den associerade resursen i taget. Att räkna semaforer som bara har värden 0 eller 1 kallas ofta *binär semafor.*

> [!IMPORTANT]
> Om en binär semaphore används måste användaren förhindra att samma tråd utför en get-åtgärd på en semaphore som den redan äger. En andra get misslyckas och kan leda till obegränsad stängning av anropstråden och permanent otillgänglighet för resursen.

### <a name="event-notification"></a>Händelseavisering 
Det är också möjligt att räkna semaforer som händelseaviseringar på producent-konsument-sätt. Konsumenten försöker hämta räkningen semaphore medan producenten ökar semaforen när något är tillgängligt. Sådana semaforer har vanligtvis det inledande värdet 0 och ökar inte förrän producenten har något klart för konsumenten. Semaforer som används för händelsemeddelanden kan  också dra nytta av tx_semaphore_ceiling_put tjänstanropet. Den här tjänsten säkerställer att semaphore-antalet aldrig överskrider det värde som anges i anropet.

### <a name="creating-counting-semaphores"></a>Skapa räkningssemaforer 
Räkna semaforer skapas antingen under initieringen eller under körning av programtrådar. Det första antalet semaphore anges när den skapas. Det finns ingen gräns för antalet räknande semaforer i ett program. 

### <a name="thread-suspension"></a>Trådavstängning  
Programtrådar kan pausas vid försök att utföra en get-åtgärd på en semaphore med det aktuella antalet 0. 

När en put-åtgärd har utförts utförs den pausade trådens get-åtgärd och tråden återupptas. Om flera trådar pausas på samma räkning återupptas de i samma ordning som de pausades (FIFO).

Prioritetsuppstängning är dock också möjligt om programmet ***anropar tx_semaphore_prioritize*** före anropet semaphore put som tar bort trådavstängningen. Tjänsten semaphore prioritize placerar tråden med högst prioritet längst fram i tjänstgöringslistan och lämnar alla andra pausade trådar i samma FIFO-ordning.

### <a name="semaphore-put-notification"></a>Semaphore Put Notification 
För vissa program kan det vara fördelaktigt att få ett meddelande varje gång en semaphore används. ThreadX SMP ger den  här möjligheten via tx_semaphore_put_notify tjänsten. Den här tjänsten registrerar den tillhandahållna programmeddelandefunktionen med den angivna semaphore. ThreadX SMP anropar därefter den här programmeddelandefunktionen när semaphore sätts. Den exakta bearbetningen i programmeddelandefunktionen bestäms av programmet. Den består dock vanligtvis av att återuppta rätt tråd för bearbetning av den nya semaphore put-händelsen.

### <a name="semaphore-eventchaining"></a>Semaphore Eventchaining™ 
Meddelandefunktionerna i ThreadX SMP kan användas för att länka ihop olika synkroniseringshändelser. Detta är vanligtvis användbart när en enda tråd måste bearbeta flera synkroniseringshändelser.

I stället för att till exempel ha separata trådar som pausar för ett kömeddelande, händelseflaggor och en semaphore kan programmet registrera en meddelanderutin för varje objekt. När den anropas kan programmeddelanderutinen sedan återuppta en enda tråd, som kan fråga varje objekt för att hitta och bearbeta den nya händelsen.

I allmänhet resulterar händelsekedja i färre trådar, mindre omkostnader och mindre *RAM-krav.* Det ger också en mycket flexibel mekanism för att hantera synkroniseringskrav för mer komplexa system.

### <a name="run-time-semaphore-performance-information"></a>Information om körningsprestanda för Semaphore 
ThreadX SMP tillhandahåller valfri körningsprestandainformation. Om ThreadX SMP-biblioteket och programmet ***har skapats med TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO,*** ackumulerar ThreadX SMP följande information. 

Totalt antal för det övergripande systemet:

- semaphore puts
- semaphore gets
- semaphore get suspends
- semaphore get timeouts

Totalt antal för varje semaphore:

- semaphore puts
- semaphore gets
- semaphore get suspends
- semaphore get timeouts

Den här informationen är tillgänglig under körning via de tjänster som *tx_semaphore_performance_info_get* och *tx_semaphore_performance_system_info_get*. Semaphore-prestandainformation är användbar för att avgöra om programmet fungerar korrekt. Det är också användbart för att optimera programmet. Ett relativt stort antal "semaphore get timeouts" kan till exempel tyda på att andra trådar håller resurser för länge.

### <a name="semaphore-control-block-tx_semaphore"></a>Semaphore Control Block TX_SEMAPHORE 
Egenskaperna för varje räkningssemaphore finns i dess kontrollblock. Den innehåller information som det aktuella antalet semaforer. Den här strukturen definieras i ***tx_api.h-filen.*** 

Semaforkontrollblock kan finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion. 

### <a name="deadly-embrace"></a>Famn 
En av de mest intressanta och farliga fallgroparna som är associerade med semaforer som används för ömsesidig exkludering är den första *anamman*. En yppande anamma, eller *deadlock,* är ett villkor där två eller flera trådar pausas på obestämd tid vid försök att få semaforer som redan ägs av varandra.

Det här villkoret illustreras bäst med en tvåtråd, två semaphore-exempel. Anta att den första tråden äger den första semaphore och den andra tråden äger den andra semaforen. Om den första tråden försöker hämta den andra semaphore och samtidigt den andra tråden försöker hämta den första semaforen, kommer båda trådarna att ange ett deadlock-villkor. Om de här trådarna pausas för alltid blir de associerade resurserna dessutom utelåsta för alltid. Bild 7 på sidan 78 illustrerar det här exemplet.

![Famn](media/image10.png)

**BILD 7. Exempel på pausade trådar**

För realtidssystem kan du förhindra att du tar till vara på det genom att lägga till vissa begränsningar för hur trådar hämtar semaforer. Trådar kan bara ha en semafor i taget. Alternativt kan trådar äga flera semaforer om de samlar dem i samma ordning. Om den första och andra tråden får den första och andra semaforen i ordning förhindras den första och andra tråden i det föregående exemplet.

> [!IMPORTANT]
> Det är också möjligt att använda den tidsgräns för instängning som är associerad med get-åtgärden för att återställa från en famn.

### <a name="priority-inversion"></a>Prioritetsinversion 
En annan fallgropar som är associerade med semaforer för ömsesidig exkludering är prioritetsinversion. Det här avsnittet beskrivs mer ingående i "Fallgropar med trådprioritet" på sidan 64.

Det grundläggande problemet är en situation där en tråd med lägre prioritet har en semafor som en tråd med högre prioritet behöver. Detta i sig är normalt. Trådar med prioriteringar mellan dem kan dock leda till att prioritetsinversionen varar en icke-terministisk tidsperiod. Detta kan hanteras genom noggrant val av trådprioriteringar med hjälp av tröskelvärdet för allokering och tillfälligt höja prioriteten för den tråd som äger resursen till den för tråden med hög prioritet.

## <a name="mutexes"></a>Mutexes

Förutom semaforer tillhandahåller ThreadX SMP även ett mutex-objekt. En mutex är i princip en binär semafor, vilket innebär att endast en tråd kan äga en mutex i taget. Dessutom kan samma tråd utföra en lyckad mutex get-åtgärd på en ägd mutex flera gånger, 4 294 967 295 för att vara exakt. Det finns två åtgärder för mutex-objektet: ***tx_mutex_get** _ och _*_tx_mutex_put_**. Get-åtgärden hämtar en mutex som inte ägs av en annan tråd, medan put-åtgärden frigör en tidigare hämtad mutex. För att en tråd ska släppa en mutex måste antalet put-åtgärder vara lika med antalet tidigare get-åtgärder.

Varje mutex är en offentlig resurs. ThreadX SMP har inga begränsningar för hur mutexes används.

ThreadX mutexes används endast för *mutex.* Till skillnad från att räkna semaforer har mutexes ingen användning som metod för händelseavisering.

### <a name="mutex-mutual-exclusion"></a>Mutex Mutual Exclusion 
På liknande sätt som diskussionen i avsnittet räkna semaphore gäller ömsesidig exkludering att  kontrollera åtkomsten för trådar till vissa programområden (kallas även kritiska avsnitt eller *programresurser).* När det är tillgängligt har ThreadX SMP mutex ett ägarskapsantal på 0. När mutex har erhållits av en tråd ökas ägarskapsantalet en gång för varje lyckad get-åtgärd som utförs på mutex och minskar för varje lyckad put-åtgärd.

### <a name="creating-mutexes"></a>Skapa Mutexes 
ThreadX SMP-mutexes skapas antingen under initieringen eller under körning av programtrådar. Det inledande villkoret för en mutex är alltid "tillgängligt". En mutex kan också skapas med *prioritetsarv* valt.

### <a name="thread-suspension"></a>Trådavstängning 
Programtrådar kan pausa vid försök att utföra en get-åtgärd på en mutex som redan ägs av en annan tråd.

När samma antal put-åtgärder har utförts av den ägande tråden utförs den pausade trådens get-åtgärd, vilket ger den ägarskap för mutex och tråden återupptas. Om flera trådar pausas på samma mutex återupptas de i samma ordning som de pausades (FIFO).

Men om arvet av mutex-prioritet valdes när prioriteten skapades återupptas prioriteten automatiskt. Prioritetsavstängning är också möjligt om ***programmet anropar tx_mutex_prioritize*** innan mutex put-anropet som tar bort trådavstängningen. Mutex-prioritetstjänsten placerar tråden med högst prioritet längst fram i stängningslistan och lämnar alla andra pausade trådar i samma FIFO-ordning.

### <a name="run-time-mutex-performance-information"></a>Information om Mutex-prestanda vid körning 
ThreadX SMP tillhandahåller valfri information om mutex-prestanda vid körning. Om ThreadX SMP-biblioteket och programmet ***har skapats med TX_MUTEX_ENABLE_PERFORMANCE_INFO*** definieras ackumulerar ThreadX SMP följande information.

Totalt antal för det övergripande systemet:

- mutex puts
- mutex hämtar
- mutex get suspends
- mutex get timeouts
- mutex priority inversions (inversioner av mutex-prioritet)
- mutex-prioritetsarv

Totalt antal för varje mutex:

- mutex puts
- mutex hämtar
- mutex get suspends
- mutex get timeouts
- mutex priority inversions (inversioner av mutex-prioritet)
- mutex-prioritetsarv

Den här informationen är tillgänglig under körning via tjänsterna *tx_mutex_performance_info_get* och *tx_mutex_performance_system_info_get*. Mutex-prestandainformation är användbar för att avgöra om programmet fungerar korrekt. Det är också användbart för att optimera programmet. Ett relativt stort antal "mutex get timeouts" kan till exempel tyda på att andra trådar håller resurser för länge.

### <a name="mutex-control-block-tx_mutex"></a>Mutex-kontrollblock TX_MUTEX 
Egenskaperna för varje mutex finns i dess kontrollblock. Den innehåller information som det aktuella antalet mutex-ägarskap tillsammans med pekaren för tråden som äger mutex. Den här strukturen definieras i ***tx_api.h-filen.***

Mutex-kontrollblock kan finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion.

### <a name="deadly-embrace"></a>Famn  
En av de mest intressanta och farliga fallgroparna som är associerade med mutex-ägarskap är att ta till *sig*. En yvig anamma, eller *deadlock,* är ett villkor där två eller flera trådar pausas på obestämd tid vid försök att få en mutex som redan ägs av de andra trådarna. Diskussionen om att *ta del av* erbjudandet och dess åtgärder som finns på sidan 77 är också helt giltig för mutex-objektet.

### <a name="priority-inversion"></a>Prioritetsinversion 
Som tidigare nämnts är en stor fallgrop som är associerad med ömsesidig exkludering prioritetsinversion. Det här avsnittet beskrivs mer ingående i "Fallgropar med trådprioritet" på sidan 64. 

Det grundläggande problemet är en situation där en tråd med lägre prioritet har en semafor som en tråd med högre prioritet behöver. Detta i sig är normalt. Trådar med prioriteringar mellan dem kan dock leda till att prioritetsinversionen varar en icke-terministisk tidsperiod. Till skillnad från semaforer som beskrivits tidigare har ThreadX SMP mutex-objektet valfritt *prioritetsarv.* Den grundläggande idén bakom arv av prioritet är att en tråd med lägre prioritet tillfälligt höjs till prioriteten för en tråd med hög prioritet som vill att samma mutex ska ägas av tråden med lägre prioritet. När tråden med lägre prioritet släpper mutex återställs dess ursprungliga prioritet och tråden med högre prioritet får ägarskap för mutex. Den här funktionen eliminerar icke-terministisk prioritetsinversion genom att begränsa mängden inversion till den tidpunkt då tråden med lägre prioritet innehåller mutex. Naturligtvis är de tekniker som beskrivs tidigare i det här kapitlet för att hantera icke-terministisk prioritetsinversion också giltiga med mutexes också.

## <a name="event-flags"></a>Händelseflaggor

Händelseflaggor är ett kraftfullt verktyg för trådsynkronisering. Varje händelseflagga representeras av en enda bit. Händelseflaggor ordnas i grupper om 32.

Trådar kan användas på alla 32 händelseflaggor i en grupp samtidigt. Händelser anges av *tx_event_flags_set* och hämtas av *tx_event_flags_get*.

Du ställer in händelseflaggor med en logisk AND/OR-åtgärd mellan de aktuella händelseflaggorna och de nya händelseflaggorna. Typen av logisk åtgärd (antingen ett AND  eller OR) anges i tx_event_flags_set anropet.

Det finns liknande logiska alternativ för hämtning av händelseflaggor. En get-begäran kan ange att alla angivna händelseflaggor krävs (ett logiskt AND). Alternativt kan en get-begäran ange att någon av de angivna händelseflaggorna uppfyller begäran (ett logiskt OR). Den typ av logisk åtgärd som är associerad med hämtning av händelseflaggor anges i *tx_event_flags_get anropet.*

> [!IMPORTANT]
> Händelseflaggor som uppfyller en get-begäran förbrukas, det vill säga inställt på noll om **TX_OR_CLEAR** eller **TX_AND_CLEAR** anges av begäran.

Varje grupp med händelseflaggor är en offentlig resurs. ThreadX SMP har inga begränsningar för hur händelseflaggor används.

### <a name="creating-event-flags-groups"></a>Skapa händelseflaggor grupper
Händelseflaggor skapas antingen under initieringen eller under körning av programtrådar. När de skapas anges alla händelseflaggor i gruppen till noll. Det finns ingen gräns för antalet händelseflaggor i ett program.

### <a name="thread-suspension"></a>Trådavstängning 
Programtrådar kan pausa vid försök att hämta en logisk kombination av händelseflaggor från en grupp. När en händelseflagga har angetts granskas get-begäranden för alla pausade trådar. Alla trådar som nu har de nödvändiga händelseflaggorna återupptas.

> [!IMPORTANT]
> Alla inaktiverade trådar i en händelseflaggor granskas när dess händelseflaggor har angetts. Detta medför naturligtvis ytterligare omkostnader. Därför är det bra att begränsa antalet trådar som använder samma händelseflaggor till ett rimligt antal.

### <a name="event-flags-set-notification"></a>Meddelande om händelseflaggor 
För vissa program kan det vara fördelaktigt att meddelas när en händelseflagga har angetts. ThreadX SMP ger den  här möjligheten via tx_event_flags_set_notify tjänsten. Den här tjänsten registrerar den angivna programmeddelandefunktionen med den angivna händelseflaggor-gruppen. ThreadX SMP anropar sedan den här programmeddelandefunktionen när en händelseflagga i gruppen har angetts. Den exakta bearbetningen i programmeddelandefunktionen bestäms av programmet, men den består vanligtvis av att återuppta lämplig tråd för bearbetning av den nya händelseflaggan. 

### <a name="event-flags-event-chaining"></a>Händelsekedja för händelseflaggor™ 
Meddelandefunktionerna i ThreadX SMP kan användas för att "länka" olika synkroniseringshändelser tillsammans. Detta är vanligtvis användbart när en enda tråd måste bearbeta flera synkroniseringshändelser. 

I stället för att till exempel ha separata trådar pausa för ett kömeddelande, händelseflaggor och en semaphore kan programmet registrera en meddelanderutin för varje objekt. När den anropas kan programmeddelanderutinen sedan återuppta en enda tråd, som kan fråga varje objekt för att hitta och bearbeta den nya händelsen. 

I allmänhet resulterar händelsekedja i färre trådar, mindre omkostnader och mindre *RAM-krav.* Det ger också en mycket flexibel mekanism för att hantera synkroniseringskrav för mer komplexa system. 

### <a name="run-time-event-flags-performance-information"></a>Prestandainformation för körningshändelseflaggor 
ThreadX SMP tillhandahåller valfri prestandainformation för körningshändelseflaggor. Om ThreadX SMP-biblioteket och programmet ***har skapats med TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO,*** ackumulerar ThreadX SMP följande information.

Totalt antal för det övergripande systemet:

- händelseflaggor uppsättningar
- händelseflaggor hämtar
- händelseflaggor får stängningar
- händelseflaggor får tidsgränser

Totalt antal för varje händelseflaggasgrupp:

- händelseflaggor uppsättningar
- händelseflaggor hämtar
- händelseflaggor får stängningar
- händelseflaggor får tidsgränser

Den här informationen är tillgänglig under körning via tjänsterna *tx_event_flags_performance_info_get* och *tx_event_flags_performance_system_info_get*. Prestandainformation för Event Flags är användbar för att avgöra om programmet fungerar korrekt. Det är också användbart för att optimera programmet. Ett relativt stort antal timeouter på  tx_event_flags_get tjänsten kan till exempel tyda på att tidsgränsen för låsning av händelseflaggor är för kort.

### <a name="event-flags-group-control-block-tx_event_flags_group"></a>Gruppkontrollblockering för Händelseflaggor TX_EVENT_FLAGS_GROUP
Egenskaperna för varje händelseflaggasgrupp finns i dess kontrollblock. Den innehåller information som inställningar för aktuella händelseflaggor och antalet trådar som pausas för händelser. Den här strukturen definieras i ***tx_api.h-filen.*** 

Kontrollblock för händelsegrupper kan finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion.

## <a name="memory-block-pools"></a>Minnesblockpooler  

Att allokera minne på ett snabbt och deterministiskt sätt är alltid en utmaning i realtidsprogram. Med detta i åtanke ger ThreadX SMP möjligheten att skapa och hantera flera pooler med minnesblock med fast storlek.

Eftersom minnesblockpooler består av block med fast storlek finns det aldrig några fragmenteringsproblem. Fragmentering orsakar förstås beteenden som inte är obestämda. Dessutom är den tid som krävs för att allokera och frigöra ett minnesblock med fast storlek jämförbar med den för enkel manipulering av länkade listor. Dessutom sker minnesblocksallokering och avallokering i den tillgängliga listans huvud. Detta ger den snabbaste möjliga bearbetningen av länkade listor och kan hjälpa till att behålla det faktiska minnesblocket i cacheminnet.

Brist på flexibilitet är den största nackdelen med minnespooler med fast storlek. Blockstorleken för en pool måste vara tillräckligt stor för att hantera de sämsta minneskraven för användarna. Naturligtvis kan minnet vara bortkastat om många minnesbegäranden av olika storlek görs till samma pool. En möjlig lösning är att skapa flera olika minnesblockpooler som innehåller minnesblock av olika storlek.

Varje minnesblockpool är en offentlig resurs. ThreadX SMP har inga begränsningar för hur pooler används.

### <a name="creating-memory-block-pools"></a>Skapa minnesblockpooler  
Minnesblockpooler skapas antingen under initieringen eller under körning av programtrådar. Det finns ingen gräns för antalet minnesblockpooler i ett program.

### <a name="memory-block-size"></a>Minnesblockstorlek  
Som tidigare nämnts innehåller minnesblockpooler ett antal block med fast storlek. Blockstorleken i byte anges när poolen skapas.

> [!IMPORTANT]
> ThreadX SMP lägger till en liten mängd overhead– storleken på en C-pekare – till varje minnesblock i poolen. Dessutom kan ThreadX SMP behöva lägga ut blockstorleken för att behålla början av varje minnesblock vid korrekt justering.

### <a name="pool-capacity"></a>Poolkapacitet 
Antalet minnesblock i en pool är en funktion av blockstorleken och det totala antalet byte i det angivna minnesområdet under skapandet. Kapaciteten för en pool beräknas genom att dela upp blockstorleken (inklusive utfyllnad och pekarens overhead byte) i det totala antalet byte i det angivna minnesområdet.

### <a name="pools-memory-area"></a>Poolens minnesområde 
Som tidigare nämnts anges minnesområdet för blockpoolen när den skapas. Precis som andra minnesområden i ThreadX SMP kan den finnas var som helst i målets adressutrymme.

Det här är en viktig funktion på grund av den stora flexibilitet som den ger. Anta till exempel att en kommunikationsprodukt har ett minnesområde med hög hastighet för I/O. Det här minnesområdet hanteras enkelt genom att göra det till en ThreadX SMP-minnesblockpool.

### <a name="thread-suspension"></a>Trådavstängning 
Programtrådar kan pausas i väntan på ett minnesblock från en tom pool. När ett block returneras till poolen ges den pausade tråden det här blocket och tråden återupptas.

Om flera trådar pausas i samma minnesblockpool återupptas de i den ordning som de pausades (FIFO).

Prioritetsavstängning är dock också möjligt om ***programmet anropar tx_block_pool_prioritize*** innan blockutgåsanropet som tar bort trådavstängningen. Blockpoolens prioritetstjänst placerar den högsta prioritetstråden längst fram i spärrlistan, samtidigt som alla andra pausade trådar är i samma FIFO-ordning.

### <a name="run-time-block-pool-performance-information"></a>Prestandainformation för blockpooler för körning  
ThreadX SMP tillhandahåller valfri prestandainformation för blockpooler för körning. Om ThreadX SMP-biblioteket och programmet har ***skapats med TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO,*** ackumulerar ThreadX SMP följande information.

Totalt antal för det övergripande systemet:

- allokerade block
- utgivna block
- allokeringsavstängningar
- tidsgränser för allokering

Totalt antal för varje blockpool:

- allokerade block
- utgivna block
- allokeringsavstängningar
- tidsgränser för allokering

Den här informationen är tillgänglig under körning via tjänsterna *tx_block_pool_performance_info_get* och *tx_block_pool_performance_system_info_get*. Prestandainformation för blockpooler är användbar för att avgöra om programmet fungerar korrekt. Det är också användbart för att optimera programmet. Ett relativt stort antal "allokeringsavstängningar" kan till exempel tyda på att blockpoolen är för liten.

### <a name="memory-block-pool-control-block-tx_block_pool"></a>Blockblockpool – blockblockering TX_BLOCK_POOL  
Egenskaperna för varje minnesblockpool finns i dess kontrollblock. Den innehåller information som antalet tillgängliga minnesblock och blockstorleken för minnespoolen. Den här strukturen definieras i ***tx_api.h-filen.*** 

Poolkontrollblock kan också finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion. 

### <a name="overwriting-memory-blocks"></a>Skriva över minnesblock  
Det är viktigt att se till att användaren av ett allokerat minnesblock inte skriver utanför sina gränser. Om detta inträffar uppstår skada i ett angränsande (vanligtvis efterföljande) minnesområde. Resultatet är oförutsägbart och ofta allvarligt! 

## <a name="memory-byte-pools"></a>Minnesbytepooler

ThreadX SMP-minnesbytepooler liknar en standard-C-heap. Till skillnad från standard-C heap, är det möjligt att ha flera minnesbytepooler. Dessutom kan trådar pausa i en pool tills det begärda minnet är tillgängligt.

Allokeringar från minnesbytepooler liknar traditionella *malloc-anrop,* som innehåller mängden minne som önskas (i byte). Minnet allokeras från poolen på ett *sätt som passar dig* först. Det första lediga minnesblocket som uppfyller begäran används alltså. Överflödigt minne från det här blocket konverteras till ett nytt block och placeras tillbaka i listan över ledigt minne. Den här processen kallas *fragmentering.*

Intilliggande lediga minnesblock *sammanfogas* under en efterföljande allokeringssökning efter ett tillräckligt stort ledigt minnesblock. Den här processen kallas *för defragmentering.*

Varje minnesbytepool är en offentlig resurs. ThreadX SMP har inga begränsningar för hur pooler används, förutom att minnesbytetjänster inte kan anropas från ISR:er.

### <a name="creating-memory-byte-pools"></a>Skapa minnesbytepooler 
Minnesbytepooler skapas antingen under initieringen eller under körning av programtrådar. Det finns ingen gräns för antalet minnesbytepooler i ett program.  

### <a name="pool-capacity"></a>Poolkapacitet 
Antalet byte som kan användas i en minnesbytepool är något mindre än vad som angavs när byte skapades. Det beror på att hanteringen av det lediga minnesområdet medför vissa extra kostnader. Varje ledigt minnesblock i poolen kräver motsvarande två C-pekare för overhead. Dessutom skapas poolen med två block, ett stort ledigt block och ett litet permanent allokerat block i slutet av minnesområdet. Det här allokerade blocket används för att förbättra allokeringsalgoritmens prestanda. Det eliminerar behovet av att kontinuerligt söka efter slutet av poolområdet under sammanslagningen.  

Under körningen ökar vanligtvis mängden overhead i poolen. Allokeringar av ett udda antal byte är utpadade för att säkerställa korrekt justering av nästa minnesblock. Dessutom ökar omkostnaderna när poolen blir mer fragmenterad.

### <a name="pools-memory-area"></a>Poolens minnesområde  
Minnesområdet för en minnesbytepool anges när den skapas. Precis som andra minnesområden i ThreadX SMP kan den finnas var som helst i målets adressutrymme. 

Det här är en viktig funktion på grund av den stora flexibilitet som den ger. Om målmaskinvaran till exempel har ett minnesområde med hög hastighet och ett minnesområde med låg hastighet kan användaren hantera minnesallokering för båda områdena genom att skapa en pool i var och en av dem. 

### <a name="thread-suspension"></a>Trådavstängning  
Programtrådar kan pausas i väntan på minnesbyte från en pool. När tillräckligt med sammanhängande minne blir tillgängligt får de pausade trådarna det begärda minnet och trådarna återupptas. 

Om flera trådar pausas i samma minnesbytepool får de minne (återupptas) i den ordning de pausades (FIFO). 

Prioritetsavstängning är dock också möjligt om programmet ***anropar tx_byte_pool_prioritize*** innan byte-lanseringsanropet som tar bort trådavstängningen. Bytepoolens prioritetstjänst placerar den högsta prioritetstråden längst fram i stängningslistan, samtidigt som alla andra pausade trådar är i samma FIFO-ordning.

### <a name="run-time-byte-pool-performance-information"></a>Prestandainformation för bytepooler under körning  
ThreadX SMP tillhandahåller valfri prestandainformation för bytepooler vid körning. Om ThreadX SMP-biblioteket och programmet ***har skapats med TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO,*** ackumulerar ThreadX SMP följande information.

Totalt antal för det övergripande systemet:

- Fördelningar
- versioner
- fragment som genomsökts
- sammanfogade fragment
- fragment som skapats
- allokeringsavstängningar
- tidsgränser för allokering

Totalt antal för varje bytepool:

- Fördelningar
- versioner
- fragment som genomsökts
- sammanfogade fragment
- fragment som skapats
- allokeringsavstängningar
- tidsgränser för allokering

Den här informationen är tillgänglig under körning via tjänsterna *tx_byte_pool_performance_info_get* och *tx_byte_pool_performance_system_info_get*. Prestandainformation för bytepooler är användbar för att avgöra om programmet fungerar korrekt. Det är också användbart för att optimera programmet. Ett relativt stort antal "allokeringsavstängningar" kan till exempel tyda på att bytepoolen är för liten.

### <a name="memory-byte-pool-control-block-tx_byte_pool"></a>Kontrollblockering för minnesbytepool TX_BYTE_POOL  
Egenskaperna för varje minnesbytepool finns i dess kontrollblock. Den innehåller användbar information, till exempel antalet tillgängliga byte i poolen. Den här strukturen definieras i ***tx_api.h-filen.*** 

Poolkontrollblock kan också finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion. 

### <a name="nondeterministic-behavior"></a>Icke-terministiskt beteende 
Även om minnesbytepooler ger den mest flexibla minnesallokeringen, har de också något icke-terministiskt beteende. En minnesbytepool kan till exempel ha 2 000 byte minne tillgängligt, men kanske inte uppfyller en allokeringsbegäran på 1 000 byte. Det beror på att det inte finns några garantier för hur många av de kostnadsfria byte som är sammanhängande. Även om det finns ett 1 000 byte ledigt block finns det inga garantier om hur lång tid det kan ta att hitta blocket. Det är helt möjligt att hela minnespoolen skulle behöva genomsökas för att hitta blocket 1 000 byte. 

> [!IMPORTANT]
> Därför är det vanligtvis bra att undvika att använda tjänster för minnesbyte i områden där deterministiskt beteende i realtid krävs. Många program allokerar det minne som krävs i förväg under initieringen eller körningskonfigurationen.

### <a name="overwriting-memory-blocks"></a>Skriva över minnesblock 
Det är viktigt att se till att användaren av allokerat minne inte skriver utanför gränserna. Om detta inträffar uppstår skada i ett angränsande (vanligtvis efterföljande) minnesområde. Resultatet är oförutsägbart och ofta allvarligt! 

## <a name="application-timers"></a>Programtimerar

Snabba svar på asynkrona externa händelser är den viktigaste funktionen i inbäddade realtidsprogram. Många av dessa program måste dock också utföra vissa aktiviteter med förinbestämda tidsintervall.

ThreadX SMP-programtimer ger program möjlighet att köra program C-funktioner vid specifika tidsintervall. Det är också möjligt för en programtimer att upphöra att gälla endast en gång. Den här typen av timer kallas *för en enslagstimer,* medan upprepande intervalltimer kallas *periodiska timers*.

Varje programtimer är en offentlig resurs. ThreadX SMP har inga begränsningar för hur programtimer används.

> [!IMPORTANT]
> Programtimer kan undantas från körning på valfri kärna via tx_timer_smp_core_exclude API.

### <a name="timer-intervals"></a>Timerintervall 
I ThreadX SMP mäts tidsintervallen med periodiska timeravbrott. Varje timeravbrott kallas för en timer *tick*. Den faktiska tiden mellan timer tick anges av programmet, men 10 ms är normen för de flesta implementeringar. Den periodiska timerinställningen finns vanligtvis i den ***tx_initialize_low_level*** sammansättningsfilen.

Det är värt att nämna att den underliggande maskinvaran måste kunna generera periodiska avbrott för att programtimer ska fungera. I vissa fall har processorn en inbyggd periodisk avbrottsfunktion. Om processorn inte har den här möjligheten måste användarens tavla ha en kringutrustningsenhet som kan generera periodiska avbrott.

> [!IMPORTANT]
> ThreadX SMP kan fortfarande fungera även utan en periodisk avbrottskälla. Men all timerrelaterad bearbetning inaktiveras sedan. Detta inkluderar timelicering, lämningstidsutbrott och timertjänster.

### <a name="timer-accuracy"></a>Timernoggrannhet 
Timerförfallotid anges i tick. Det angivna förfallovärdet minskas med ett på varje tids tick. Eftersom en programtimer kan aktiveras precis före ett timeravbrott (eller ett tids tick) kan den faktiska förfallotiden vara upp till ett tick tidigt.

Om timern tickhastighet är 10 ms kan programtimer gå ut upp till 10 ms tidigt. Detta är mer betydande för 10 ms timers än 1 sekund timers. Om du ökar frekvensen för timeravbrott minskar du naturligtvis felmarginalen.

### <a name="timer-execution"></a>Timerkörning 
Programtimer körs i den ordning de blir aktiva. Om till exempel tre timers skapas med samma förfallovärde och aktiveras, kommer deras motsvarande förfallofunktioner garanterat att köras i den ordning som de aktiverades. 

### <a name="creating-application-timers"></a>Skapa programtimerar 
Programtimer skapas antingen under initieringen eller under körning av programtrådar. Det finns ingen gräns för antalet programtimer i ett program. 

### <a name="run-time-application-timer-performance-information"></a>Prestandainformation för körningsprogramtimer  
ThreadX SMP tillhandahåller valfri prestandainformation för körningsprogrammets timer. Om ThreadX SMP-biblioteket och programmet har ***skapats TX_TIMER_ENABLE_PERFORMANCE_INFO*** har definierats ackumuleras följande information i ThreadX SMP. 

Totalt antal för hela systemet:

- Aktiveringar
- inaktiveringar
- återaktiveringar (periodiska timers)
- Utgångsdatum
- förfallojusteringar

Totalt antal för varje programtimer:

- Aktiveringar
- inaktiveringar
- återaktiveringar (periodiska timers)
- Utgångsdatum
- förfallojusteringar

Den här informationen är tillgänglig under körning via tjänsterna *tx_timer_performance_info_get* och *tx_timer_performance_system_info_get*. Prestandainformation för programtimer är användbar för att avgöra om programmet fungerar korrekt. Det är också användbart för att optimera programmet.

### <a name="application-timer-control-block-tx_timer"></a>Kontrollblockering för programtimer TX_TIMER 
Egenskaperna för varje programtimer finns i dess kontrollblock. Den innehåller användbar information, till exempel värdet för 32-bitars förfalloidentifiering. Den här strukturen definieras i ***tx_api.h-filen.***

Kontrollblock för programtimer kan finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion. 

### <a name="excessive-timers"></a>Överdrivna timers 
Som standard körs programtimer inifrån en dold systemtråd som körs på prioritet noll, vilket vanligtvis är högre än någon programtråd. Därför bör bearbetningen i programtimer hållas på ett minimum. 

Det är också viktigt att undvika timers som upphör att gälla varje tids tick när det är möjligt. En sådan situation kan medföra onödigt mycket omkostnader i programmet.

> [!WARNING]
> Som tidigare nämnts körs programtimer från en dold systemtråd. Därför är det viktigt att inte välja stängning för alla ThreadX SMP-tjänstanrop som görs inifrån programtimerns förfallofunktion.

## <a name="relative-time"></a>Relativ tid

Förutom de programtimer som nämnts tidigare tillhandahåller ThreadX SMP en enda stegvis ökning av 32-bitars tickräknare. Tickräknaren eller *tiden* ökas med ett på varje timeravbrott.

Programmet kan läsa eller ange den här 32-bitars räknaren *via anrop till tx_time_get* respektive *tx_time_set*. Användningen av den här tickräknaren bestäms helt av programmet. Den används inte internt av ThreadX SMP.

### <a name="interrupts"></a>Avbryter 
Snabba svar på asynkrona händelser är den huvudsakliga funktionen för inbäddade realtidsprogram. Programmet vet att en sådan händelse finns genom maskinvaruavbrott. 

Ett avbrott är en asynkron ändring i processorkörningen. När ett avbrott inträffar sparar processorn vanligtvis en liten del av den aktuella körningen på stacken och överför kontrollen till lämplig avbrottsvektor. Avbrottsvektorn är i princip bara adressen till den rutin som ansvarar för att hantera det specifika typavbrottet. Den exakta proceduren för avbrottshantering är processorspecifik. 

### <a name="interrupt-control"></a>Avbrottskontroll 
Med *tx_interrupt_control-tjänsten* kan program aktivera och inaktivera avbrott. Den tidigare avbrottsstatusen för att aktivera/inaktivera returneras av den här tjänsten. Det är viktigt att nämna att avbrottskontrollen endast påverkar det programsegment som körs just nu. Om en tråd till exempel inaktiverar avbrott förblir de bara inaktiverade under körningen av tråden. 

> [!WARNING]
> Ett avbrott som inte kan maskeras (NMI) är ett avbrott som inte kan inaktiveras av maskinvaran. Ett sådant avbrott kan användas av ThreadX SMP-program. Programmets NMI-hanteringsrutin tillåts dock inte att använda ThreadX SMP-kontexthantering eller API-tjänster. ThreadX SMP-hanterade avbrott

ThreadX SMP ger program fullständig avbrottshantering. Den här hanteringen omfattar att spara och återställa kontexten för den avbrutna körningen. Dessutom tillåter ThreadX SMP att vissa tjänster anropas inifrån ISR(Interrupt Service Routines). Följande är en lista över ThreadX SMP-tjänster som tillåts från program-ISR:

- tx_block_allocate 
- tx_block_pool_info_get 
- tx_block_pool_prioritize 
- tx_block_pool_performance_info_get 
- tx_block_pool_performance_system_info_get 
- tx_block_release 
- tx_byte_pool_info_get 
- tx_byte_pool_performance_info_get 
- tx_byte_pool_performance_system_info_get 
- tx_byte_pool_prioritize 
- tx_event_flags_info_get 
- tx_event_flags_get 
- tx_event_flags_set 
- tx_event_flags_performance_info_get 
- tx_event_flags_performance_system_info_get 
- tx_event_flags_set_notify 
- tx_interrupt_control 
- tx_mutex_performance_info_get 
- tx_mutex_performance_system_info_get 
- tx_queue_front_send 
- tx_queue_info_get 
- tx_queue_performance_info_get 
- tx_queue_performance_system_info_get 
- tx_queue_prioritize 
- tx_queue_receive 
- tx_queue_send 
- tx_semaphore_get 
- tx_queue_send_notify 
- tx_semaphore_ceiling_put 
- tx_semaphore_info_get 
- tx_semaphore_performance_info_get 
- tx_semaphore_performance_system_info_get 
- tx_semaphore_prioritize 
- tx_semaphore_put 
- tx_thread_identify 
- tx_semaphore_put_notify 
- tx_thread_entry_exit_notify 
- tx_thread_info_get 
- tx_thread_resume 
- tx_thread_performance_info_get 
- tx_thread_performance_system_info_get 
- tx_thread_stack_error_notify 
- tx_thread_wait_abort 
- tx_time_get 
- tx_time_set 
- tx_timer_activate 
- tx_timer_change 
- tx_timer_deactivate 
- tx_timer_info_get 
- tx_timer_performance_info_get 
- tx_timer_performance_system_info_get

> [!WARNING]
> Indragning tillåts inte från ISR:er. Därför måste **wait_option** för alla ThreadX SMP-tjänstanrop som görs från en ISR anges till **TX_NO_WAIT**.

### <a name="isr-template"></a>ISR-mall 
För att hantera programavbrott måste flera ThreadX SMP-verktyg anropas i början och slutet av program-ISR:er. Det exakta formatet för avbrottshantering varierar mellan olika portar. Granska ***readme_threadx.txt*** på distributionsdisken för specifika instruktioner om hur du hanterar ISR.

Följande små kodsegment är typiskt för de flesta ThreadX SMP-hanterade ISR:er. I de flesta fall är bearbetningen i sammansättningsspråk.

**_application_ISR_vector_entry**:  
; Spara kontexten och förbered dig för  
; ThreadX SMP-användning genom att anropa ISR  
; entry-funktion.  
ANROPA **_TX_THREAD_CONTEXT_SAVE**  

; ISR kan nu anropa ThreadX SMP  
; tjänster och egna C-funktioner  

; När ISR är klar kontext  
; återställs (eller trådförseing)  
; genom att anropa kontextåterställning  
; Funktion. Kontrollen returneras inte!  
JUMP **_tx_thread_context_restore**

### <a name="high-frequency-interrupts"></a>Avbrott med hög frekvens  
Vissa avbrott inträffar med så hög frekvens att sparande och återställning av fullständig kontext vid varje avbrott skulle förbruka för hög bearbetningsbandbredd. I sådana fall är det vanligt att programmet har en liten isr på sammansättningsspråket som gör en begränsad mängd bearbetning för en majoritet av dessa avbrott med högfrekventhet. 

Efter en viss tidpunkt kan den lilla ISR:en behöva interagera med ThreadX SMP. Detta åstadkoms genom att anropa funktionerna entry och exit som beskrivs i mallen ovan. 

### <a name="interrupt-latency"></a>Avbrottssvarstid  
ThreadX SMP låser ut avbrott under korta tidsperioder. Den maximala tidsavbrotten är inaktiverade i den ordning som krävs för att spara eller återställa en tråds kontext. 