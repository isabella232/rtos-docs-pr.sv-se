---
title: Kapitel 3 – Funktionell översikt över GUIX
description: Det här kapitlet innehåller en funktionell översikt över produkten med högpresterande GUIX-användargränssnitt.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2a53da048b18d35b6b15a4ad8d4138e1a2acd4e8
ms.sourcegitcommit: 95f4ae0842a486fec8f10d1480203695faa9592d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/09/2021
ms.locfileid: "111875262"
---
# <a name="chapter-3---functional-overview-of-guix"></a>Kapitel 3 – Funktionell översikt över GUIX

Det här kapitlet innehåller en funktionell översikt över produkten med högpresterande GUIX-användargränssnitt. 

## <a name="execution-overview"></a>Körningsöversikt

GUIX implementerar en händelsedriven programmeringsmodell. Det innebär att GUIX-ramverket främst drivs av mottagandet av händelser som skickas till GUIX-händelsekön. Bearbetningen av dessa händelser sker i kontexten för GUIX-tråden, som är en ThreadX-tråd som skapas under GUIX-system initieringen.

GUIX-program definierar användargränssnittet genom att anropa GUIX API-funktioner för att skapa fönster och underordnade widgetar och anpassa utseendet på dessa widgetar genom att anropa ytterligare API-funktioner som används för att definiera färger, format, teckensnitt och olika andra attribut för varje fönster eller widgettyp. Om du använder GUIX Studio för att skapa utseendet på dina användargränssnittsskärmar utförs mycket av det här arbetet med att anropa GUIX API-funktioner för att skapa din skärm åt dig av GUIX Studio-programmet.

GUIX-program interagerar med systemanvändaren och med extern affärslogik genom att hantera händelser som hämtats från GUIX-händelsekön.
Dessa händelser skapas vanligtvis av GUIX-widgetar, men de kan också skapas av externa trådar. När en typisk GUIX-knapp pushas skickar knappen en händelse till knappens överordnade fönster. Ditt program agerar på knapp-push-knappen genom att tillhandahålla en hanterare för knappens push-händelse.

Ytterligare GUIX-trådar skapas ofta för saker som indatadrivrutiner. En typisk drivrutin för pekskärmsinmatning körs som en fristående tråd som är extern till guix-huvudtråden. Touch-indatadrivrutinen skickar pekinformation till GUIX-tråden genom att skicka händelser till GUIX-händelsekön.

Eftersom många användargränssnittsåtgärder som animeringar kräver korrekt tidsinformation implementerar GUIX också ett enkelt och lättanvändargränssnitt. Det här timergränssnittet bygger på ThreadX-timertjänsten och konfigureras automatiskt vid systemstart.

Merparten av GUIX-programvaran är oberoende av eventuella maskinvaruberoenden. Ramverket kräver maskinvaruspecifika indatadrivrutiner och maskinvaruspecifika grafikdrivrutiner. Information om hur dessa maskinvaruspecifika drivrutiner implementeras skjuts upp till kapitel 5.

## <a name="initialization"></a>Initiering 

Tjänsten måste ***gx_system_initialize*** anropas innan någon annan GUIX-tjänst anropas. GUIX-systeminitiering kan anropas ***från*** ThreadX tx_application_define rutinen (initieringskontext) eller från programtrådar. Funktionen ***gx_system_initialize*** skapar GUIX-händelsekön, initierar GUIX-timerfunktionen, skapar den huvudsakliga GUIX-systemtråden och initierar olika datastrukturer som underhålls av GUIX under körningen av ditt program.

När ***gx_system_initialize*** returneras är programmet redo att skapa skärmar, arbetsyteobjekt, fönster, widgetar och anpassa egenskaperna för alla GUIX-objekt. Mycket av API:et för att skapa GUIX-objekt ***kan anropas från tx_application_define*** eller från programtrådar.

## <a name="application-interface-calls"></a>Anrop till programgränssnitt 

Anrop från programmet görs huvudsakligen från ***tx_application_define*** (initieringskontext) eller från programtrådar. Se avsnittet "Tillåten från" i varje GUIX-API som beskrivs i kapitel 4 för att avgöra vilken kontext det kan anropas från.

I de flesta fall skjuts bearbetningsintensiva aktiviteter upp till den interna GUIX-tråden, inklusive all händelsebearbetning och widget/fönsterritning.

GUIX API-funktionerna kan anropas från vilken tråd som helst när som helst.
Det anses dock vanligtvis vara en bättre arkitektur för att separera din tidskritiska affärslogik från logiken i användargränssnittet. Eftersom ritningsåtgärder i användargränssnittet ibland kan ta lång tid beroende på din visningsstorlek och CPU-prestanda vill du normalt inte ha tidskritiska trådar som väntar på att en ritningsåtgärd ska slutföras.

## <a name="internal-guix-thread"></a>Intern GUIX-tråd 

Som tidigare nämnts har GUIX en intern tråd som utför den största delen av GUI-bearbetningen. Den här tråden skapas av programmet genom att anropa ***gx_system_initialize** _ följt av _*_gx_system_start_**.

Prioriteten för den interna GUIX-tråden bestäms av `#define GX_SYSTEM_THREAD_PRIORITY` . Det här värdet är som standard 16 (mellanprioritet), men kan ändras genom att det här värdet anges i gx_port.h- eller gx_user.h-huvudfilen, vilket åsidosätter standardvärdet.

GUIX-trådtidssegmentet definieras på liknande sätt av `#define GX_SYSTEM_THREAD_TIMESLICE` , som har värdet 10 ms som standard.

Stack-sie för systemtråden bestäms av , som finns i gx_port.h-huvudfilen, men kan också åsidosättas genom att ange det här värdet i `#define GX_THREAD_STACK_SIZE` gx_user.h-huvudfilen. 

Den interna GUIX-trådkörningsloopen består av tre åtgärder.
Först hämtar GUIX händelser från GUIX-händelsekön och skickar dessa händelser för bearbetning av GUIX-fönster och widgetar. Händelser pushas vanligtvis till GUIX-händelsekön av periodiska timers, indataenheter som en pekskärm eller knappsats och av GUIX-widgetar själva när de bearbetar användarindata. Efter att alla händelser har bearbetats avgör GUIX om en skärmuppdatering krävs och i så fall utför den bearbetning som krävs för att uppdatera visningsgrafikdata, främst genom att anropa ritningsfunktionerna i de fönster och widgetar som har markerats som dirty (dirty). Slutligen pausar GUIX GUIX-tråden tills en ny indatahändelse eller händelser anländer.

## <a name="event-processing"></a>Händelsebearbetning 

Touch- eller pennindatahändelser bearbetas genom att fastställa det översta fönstret eller widgeten under pek- eller pennindatapunktspositionen och anropa fönstrets/widgetens händelsebearbetningsfunktion. Om widgeten förstår pennindatahändelser bearbetas händelsen efter behov för den widgettypen. Annars skickar widgeten längst upp touch- eller penninmatningshändelsen till widgetens överordnade för bearbetning. Det här avfallet av händelsen uppåt i kedjan fortsätter tills antingen händelsen hanteras eller tills händelsen kommer till rotfönstret, i vilket fall händelsen ignoreras.

Tangenthändelser skickas till fönstret/widgeten som har indatafokus. Fokusstatus för indata underhålls av GUIX-gx_system komponenten.

Timerhändelser skickas alltid till fönstret eller widgeten som äger timern för bearbetning.

Internt genererade händelser, till exempel knapptryckningshändelser eller ändringshändelser för skjutreglagets värde, skickas alltid till den överordnade komponenten som genererar händelsen. Om den överordnade inte bearbetar händelsen skickas den upp i kedjan som liknar pek- eller penninmatningshändelser.

## <a name="drawing"></a>Ritning 

När all händelsebearbetning är klar avgör GUIX interna tråd om någon visningsuppdatering behövs och i så fall anropas lämpliga fönster-/widgetritningsfunktioner. När ritningen är klar väntar den interna GUIX-tråden helt enkelt på händelsekön tills nästa GUIX-händelse ska bearbetas.

GUIX implementerar begreppet *"dirty areas",* som är områden som måste ritas om för varje widget och arbetsyta. En widget kan bara ritas till områden som tidigare har markerats som dirty (dirty). När en widgetritningsfunktion anropas klipps alla ritningsåtgärder internt till den tidigare definierade dirty-rektangeln.
Försök att rita utanför det här området ignoreras.

Widgetar och fönster markerar sig själva som dirty genom att anropa ***API-funktionen gx_system_dirty_mark***. Den här funktionen markerar hela widgeten eller fönstret som behöver ritas om. En andra ***funktion, gx_system_dirty_partial_add***, kan anropas som ett alternativ för att bara markera en del av ett fönster eller en widget som skadad.

Den här modellen för att markera widgetar som dirty och sedan rita om dessa widgetar endast när alla indatahändelser har bearbetats kallas *uppskjuten ritning*. GUIX-algoritmen för uppskjuten ritning och underhåll av en dirty list har utformats för att förbättra ritningseffektiviteten. Eftersom ritningsåtgärder vanligtvis är dyra, arbetar GUIX hårt för att förhindra onödig ritning.

Ritningen görs på en *GUIX-arbetsyta*. En arbetsyta är ett minnesutrymme som reserveras för att lagra grafikdata. En arbetsyta kan vara direkt kopplad till maskinvarurambufferten, beroende på systemarkitekturen och minnesbegränsningarna. Innan en ritning kan ske måste en arbetsyta först öppnas för ritning genom att anropa ***GX_CANVAS_DRAWING_INITIATE API-funktionen.*** Det här API:et förbereder en arbetsyta för ritning och upprättar den aktuella *ritningskontexten*. När GUIX utför en uppdatering av systemarbetsytan öppnas arbetsytan för ritning och den ritningskontext som upprättats innan API:erna för ritning på widgetnivå anropas. Därför behöver widgetar inte initiera ritning på en arbetsyta i widgetens ritningsfunktion.

Men om ett program vill utföra en omedelbar ritning till en arbetsyta, utanför flödet av standardalgoritmen för GUIX-uppskjuten ritning, måste programmet anropa ***gx_canvas_drawing_initiate*** direkt innan andra API-funktioner för ritning anropas och måste anropa ***gx_canvas_drawing_complete*** när den omedelbara ritningen har slutförts.

## <a name="user-input"></a>Användarindata 

GUIX stöder enheter med pekskärm, mus och tangentbord med fördefinierade händelsetyper. Ytterligare indataenheter kan användas genom att definiera anpassade händelsetyper eller genom att mappa den anpassade indataenheten till de fördefinierade händelsetyperna.

Åtgärder som är associerade med dessa enheter översätts till händelser som bearbetas av den interna GUIX-tråden. Programvara på drivrutinsnivå som skrivits för att stödja en pekskärm måste förbereda och skicka händelser i GUIX-händelsekön för penn- och penntryckningar. På samma sätt måste en drivrutin för tangenttangentens indata generera händelser för inmatning av tangenttryckningar och tangentutdata.

## <a name="modal-dialog-execution"></a>Körning av modal dialogruta 

Körning av modal dialog syftar på att presentera ett fönster för användaren som måste stängas på något sätt innan andra GUIX-fönster eller widgetar kan ta emot användarindata. Modala dialogrutor samlar in alla användarindata medan dialogfönstret visas, oavsett x,y-position för touch- eller musindatahändelser.

Modala dialogrutor utlöses av programmet genom att först skapa fönstret på vanligt sätt genom att anropa ***gx_window_create*** och sedan anropa GUIX API-funktionen ***gx_window_execute.***

När ***gx_window_execute*** anropas anger GUIX en lokal händelsebearbetningsloop. Funktionen ***gx_window_execute*** inte tillbaka till anroparen förrän dialogrutan stängs, antingen via användarindata eller genom att anropa ***gx_window_close***. Därför är det mycket viktigt att aldrig anropa ***gx_window_execute*** från någon annan tråd än den interna GUIX-tråden.

## <a name="periodic-processing"></a>Regelbunden bearbetning 

Guix använder en ThreadX-timer för att ge visningseffekter, animering av programmet och stöd för program periodiska begäranden. Den här enskilda timern används för att driva alla GUIX-tidsrelaterade behov. Som standard anges frekvensen för intern GUIX-timerbearbetning till 20 ms via konstanten **GX_SYSTEM_TIMER_MS**, som definieras i **_gx_api.h_**, såvida inte konstanten tidigare har definierats i gx_port.h- eller gx_user.h-huvudet. Standardfrekvensen kan ändras av programmet via ett kompileringsalternativ när GUIX-biblioteket byggs eller genom att uttryckligen definiera om det ***i gx_user.h***.

> [!IMPORTANT]
> Observera att GUIX-timerfrekvensen uttrycks i RTOS-timers tick och definieras av konstanten **GX_SYSTEM_TIMER_TICKS**. Värdet för **GX_SYSTEM_TIMER_TICKS** beräknas med **hjälp GX_SYSTEM_TIMER_MS** och **TX_TIMER_TICKS_PER_SECOND**. Användaren kan definiera om något av dessa värden i ***gx_port.h** _ eller _ *_gx_user.h_** för att justera GUIX-timerfrekvensen och -upplösningen.

## <a name="display-driver"></a>Visningsdrivrutin 

Visningsdrivrutiner ansvarar för att tillhandahålla en uppsättning ritningsfunktioner till guix-kärnkoden. Implementeringen av var och en av dessa ritningsfunktioner bestäms av drivrutinen, och när det är möjligt utnyttjar implementeringen stöd för maskinvaruacceleration. I allmänhet fungerar ritningsfunktionen genom att skriva pixeldata till en minnesbuffert, som kan vara den fysiska rambufferten eller en sekundär buffert beroende på drivrutinsarkitekturen. Många drivrutiner implementerar dubbel buffring med hjälp av två rambuffertar, och dessa buffertar växlas genom att aktivera buffertreglagefunktionen. GUIX anropar dessa funktioner internt vid lämpliga tidpunkter. För minnesbegränsade system kan ritningsfunktionerna bara skriva till en enda buffert för minnesramen.

GUIX tillhandahåller standardprogramimplementering av varje ritningsfunktion på låg nivå vid varje stöd för färgdjup och format. Dessa funktioner anropas via funktionspekare som finns i den **GX_DISPLAY** strukturen. När maskinvaruspecifika drivrutiner skapas skriver de vanligtvis över ett visst antal av dessa funktionspekare med funktioner som är specifika för målmaskinvaran.

En typisk drivrutin för maskinvaruvisning implementeras genom att först skapa standarddrivrutinen för GUIX-visning för det färgdjup och format som krävs.
Sedan ersätter maskinvarudrivrutinen de funktioner som behöver optimeras eller anpassas för den specifika maskinvaruimplementering.

GUIX stöder pixelfärgformat från 1-bpp till formatet 32-bpp a:r:g:b. GUIX stöder också många varianter i varje bred färgdjupkategori, till exempel r:g:b jämfört med b:g:r byteordning, packad pixel jämfört med ordjusterade pixelformat och alfakanaler. Det finns för närvarande 25 olika färgformat som stöds, men den här listan växer när maskinvaruleverantörer levererar nya varianter.

## <a name="display-memory-architectures"></a>Visa minnesarkitekturer

Olika maskinvarumål och -skärmar använder en mängd olika arkitekturer för visningsminne, beroende på målets minnesbegränsningar och programmets funktionskrav. Vi kommer att beskriva några av de vanliga minnesarkitekturerna här med en kort beskrivning av var och en.

Modell 1) Ingen rambuffert, grafikdata som lagras i extern GRAM:

![Ingen rambuffert, grafikdata som lagras i extern GRAM](./media/guix/user-guide/no-frame-buffer.png)

I modellen ovan finns det inget minne för en rambuffert i minnet som är lokalt för processorn. Alla grafikdata lagras i en extern GRAM som ingår i själva visningen. Gränssnittet till den externa GRAM:n kan vara parallellt eller seriellt. Den här typen av arkitektur är mycket låg kostnad. men det kan ha oönskade retningseffekter när grafikdata uppdateras.

Modell 2) En lokal rambuffert:

![En lokal rambuffert](./media/guix/user-guide/one-local-frame-buffer.png)

I den här modellen allokeras minnet för grafikdata från ett slumpmässigt åtkomstminne som är direkt åtkomligt processorn. Dedikerad maskinvara måste finnas för att upprepade gånger överföra grafikdata (tillsammans med tidssignaler) från det lokala minnet till skärmen. Den här modellen skiljer sig från modell 1 eftersom grafikminnet är ett block av den lokala SRAM eller DRAM som är tillgänglig för processorn. Det kan vara samma minne där stack- och programvariabler finns.

Modell 3) Lokal rambuffert + extern GRAM:

![Lokal rambuffert + extern GRAM](./media/guix/user-guide/local-frame-buffer-external-gram.png)

Modell 3 är en kombination av de två första. I den här modellen finns det tillräckligt med lokalt minne för att rymma en rambuffert. Dessutom tillhandahåller visningsenheten en extern GRAM och uppdaterar sig själv automatiskt med hjälp av de data som anges i GRAM. Den här arkitekturen drar nytta av förbättrad uppdateringseffektivitet eftersom vi kan överföra den ändrade delen av den lokala rambufferten till den externa GRAM:en i en blocköverföring, ofta med hjälp av inbyggda DMA-kanaler. Den här modellen eliminerar också den reducering som kan finnas i någon av de två första modellerna, eftersom endast färdigt grafikinnehåll kopieras till den externa GRAM:en.

Modell 4) Ping-frame-buffertar:

![Ping-frame-buffertar](./media/guix/user-guide/ping-pong-frame-buffers.png)

I modell 4 finns det tillräckligt med minne för att tillhandahålla två lokala rambuffertar. I det här fallet behandlar GUIX en bildrutebuffert som aktiv rambuffert och den andra som arbetsramsbuffert. När en uppdaterings- eller ritningsåtgärd pågår sker den i arbetsbufferten. När ritningsåtgärden har slutförts aktiveras buffertarna, och arbetsbufferten blir den aktiva bufferten och den aktiva bufferten blir arbetsbufferten. Den här modellen eliminerar även skärmslitande som kan observeras i ett enda buffrat system.

Modell 5) Ping-buffers med sammansättning av arbetsyta:

![Ping-buffers med sammansättning av arbetsyta](./media/guix/user-guide/ping-pong-buffers-canvas-composting.png)

I modell 5 kan val av antal arbetsyta skapas, upp till gränserna för tillgängligt minne. Arbetsyta kan överlagras eller blandas enligt definitionen i programmet för att skapa arbetsytans sammansatta. När en ny sammansatt skapas efter en uppdateringsåtgärd på skärmen, aktiveras aktiva och fungerande sammansatta buffertar i en åtgärd som är identisk med standardarkitekturen för ping-buffer. Modell 5 lägger till möjligheten att utföra toning och blandning av skärmåtgärder genom att blanda arbetsyta i den slutliga sammansatta utdatan.

Modell 6) Sammansättning av arbetsyta med extern GRAM:

![Sammansättning av arbetsyta med extern GRAM](./media/guix/user-guide/canvas-compositing-external-gram.png)

Modell 6 är en liten variation av modell 5, där endast en sammansatt buffert krävs och den sammansatta bufferten sedan överförs till externa GRAM. Den här modellen stöder även helskärmsblandning och överlägg.

## <a name="string-encoding"></a>Strängkodning 

GUIX stöder som standard strängkodning i UTF8-format. Stöd för UTF8-strängkodning kan inaktiveras **genom att definiera GX_DISABLE_UTF8_SUPPORT** i ***gx_user.h-huvudfilen.*** Om UTF8-kodning är inaktiverad använder GUIX internt endast standardkodning för 8-bitars ASCII plus teckenkodning för tecken på latin-1-tecken. Om du inaktiverar UTF8-strängkodning resulterar det i ett något mindre GUIX-biblioteksfotavtryck och något snabbare körning av stränghanterings- och textritningsfunktioner.

UTF8-strängkodning har följande egenskaper:

  - ASCII-strängar tar inte mer lagringsutrymme än standard-7-bitars ASCII-kodning.

  - De flesta ANSI-C-strängfunktioner fungerar med UTF8-strängkodning utan modifiering.

Alla aktiva teckenuppsättningar i världen, inklusive Kanji-teckenuppsättningar, kan representeras med utf8-strängkodning.

### <a name="static-and-dynamic-strings"></a>Statiska och dynamiska strängar 

De strängar som tilldelas dina GUIX-widgetar som stöder textvisning kan statiskt definieras strängkonstanter, som normalt placeras i konstant lagring som en del av GUIX-strängtabellen som beskrivs nedan, och dynamiskt definierade strängar, som är strängar som genereras vid körning med hjälp av tjänster som ***sprintf** _ eller _*_gx_utility_ltoa_**.

Exempel på dynamiska strängar kan vara ett värde som visas som ett tal i en GUIX-promptwidget eller en sträng för "tid/datum" som formateras dynamiskt baserat på användarens plats- och formatinställningar. Om du skapar strängar vid körning som ska tilldelas GUIX-widgetar som **GX_PROMPT-** eller **GX_TEXT_BUTTON-widgetar** måste du välja att antingen statiskt allokera lagringen för dessa körningsgenererade strängar (d.v.s.
globala teckenmatriser), eller så kan du definiera och installera  en funktion för dynamisk minnes allocator och använda GX_STYLE_TEXT_COPY-formatet, som instruerar dessa widgetar att skapa en privat kopia av tilldelade textsträngar.

Det är ett programmeringsfel att använda tillfällig lagring, till exempel en automatisk teckenmatris, för att lagra en dynamiskt genererad sträng och sedan tilldela den här strängen till en widget som **inte har GX_STYLE_TEXT_COPY** format. När det här formatet inte är aktiverat kopierar widgeten bara den angivna sträng pekaren, och strängdata måste allokeras statiskt, annars kommer widgetsträngens pekare troligen att peka på skräpdata som ger oförutsägbara resultat.

### <a name="passing-gx_string-arguments"></a>Skicka GX_STRING argument 

GUIX API-funktionerna som accepterar en GX_STRING-parameter kontrollerar alltid att längden på strängen som fältet **GX_STRING.gx_string_ptr** pekar på matchar värdet för fältet **GX_STRING.gx_string_length.** Om de två fälten inte är konsekventa returneras **ett GX_INVALID_STRING_LENGTH** och API:et som anropas returnerar utan att acceptera strängtilldelningen.

För säkerhetsöverväganden använder GUIX-programvaran aldrig internt standard C-strängfunktioner som ***strlen** _ eller _*_strcpy_**. Dessa funktioner har varit kända för att vara sårbara för skadliga attacker när strängdata inhämtas dynamiskt, vilket ofta är fallet med anslutna program.

GUIX-biblioteksutgåor före version 5.6 definierade API-funktioner som accepterade ( `GX_CONST GX_CHAR *text` ) som en parameter. Dessa funktioner, även om de fortfarande stöds för bakåtkompatibilitet, har gjorts inaktuella och ersatts av de önskade API-funktionerna som accepterar ( `GX_CONST GX_STRING *string` ) som indataparameter.

Som standard är det inaktuella API:et för texthantering aktiverat så att alla tidigare skrivna program kan byggas korrekt med de senaste uppdateringarna för GUIX-biblioteket. Om du vill inaktivera det inaktuella API:et för texthantering **ska** definitionen GX_DISABLE_DEPRECATED_STRING_API läggas **_till i gx_user.h_*_-huvudfilen. Alla nya program ska definiera _* GX_DISABLE_DEPRECATED_STRING_API och** bör endast använda api-ersättningsfunktionerna. Alla utdatafiler som genereras av GUIX Studio för GUIX-biblioteksversion 5.6 eller senare använder endast api-ersättningsfunktionerna.

I följande tabell visas de inaktuella och nyligen definierade ersättnings-API-funktionsnamnen:

| **Inaktuellt funktionsnamn**              | **Ersatt med**                              |
| ------------------------------------------ | ----------------------------------------------- |
| gx_binres_language_table_load          | gx_binres_language_table_load_ext          |
| gx_canvas_rotated_text_draw            | gx_canvas_rotated_text_draw_ext            |
| gx_canvas_text_draw                     | gx_canvas_text_draw_ext                     |
| gx_context_string_get                   | gx_context_string_get_ext                   |
| gx_display_language_table_get          | gx_display_language_table_get_ext          |
| gx_display_language_table_set          | gx_display_language_table_set_ext          |
| gx_display_string_get                   | gx_display_string_get_ext                   |
| gx_display_string_table_get            | gx_display_string_table_get_ext            |
| gx_multi_line_text_button_text_set   | gx_multi_line_text_button_text_set_ext   |
| gx_multi_line_text_input_char_insert | gx_multi_line_text_input_char_insert_ext |
| gx_multi_line_text_input_text_set    | gx_multi_line_text_input_text_set_ext    |
| gx_multi_line_text_view_text_set     | gx_multi_line_text_view_text_set_ext     |
| gx_prompt_text_get                      | gx_prompt_text_get_ext                      |
| gx_prompt_text_set                      | gx_prompt_text_set_ext                      |
| gx_single_line_text_input_text_set   | gx_single_line_text_input_text_set_ext   |
| gx_system_string_width_get             | gx_system_string_width_get_ext             |
| gx_system_version_string_get           | gx_system_version_string_get_ext           |
| gx_text_button_text_get                | gx_text_button_text_get_ext                |
| gx_text_button_text_set                | gx_text_button_text_set_ext                |
| gx_text_scroll_wheel_callback_set     | gx_text_scroll_wheel_callback_set_ext     |
| gx_utility_string_to_alphamap          | gx_utility_string_to_alphamap_ext          |
| gx_widget_string_get                    | gx_widget_string_get_ext                    |
| gx_widget_text_blend                    | gx_widget_text_blend_ext                    |
| gx_widget_text_draw                     | gx_widget_text_draw_ext                     |

### <a name="guix-string-table"></a>GUIX-strängtabell 

GUIX-strängtabellen och strängresurserna registreras med en GUIX-visningsinstans.

Varje visning i ett system med flera skärmar har en egen strängtabell och varje visning kan köras på sitt eget valda språk. De andra GUIX-resurstyperna (färger, teckensnitt och pixelkartor) underhålls också av GUIX-visningskomponenten, eftersom dessa resurstyper är specifika för varje visningsfärgformat och färgdjup.

Du kan skapa programsträngtabellen manuellt, men oftast definieras visningssträngtabellen av GUIX Studio-programmet som en del av projektresursfilen. De tillgängliga språken definieras också i resurshuvudfilen. Visningssträngstabellen är en tabell med flera kolumner med pekare till programsträngar. Varje kolumn i strängtabellen representerar ett språk som stöds av programmet.
Om ditt program endast stöder ett språk, till exempel engelska, har strängtabellen bara en kolumn. Du kan fortfarande lägga till stöd för ytterligare språk när som helst utan att ändra din programprogramvara.

Den aktiva strängtabellen tilldelas genom anrop ***gx_display_string_table_set*** API-funktionen. Den här funktionen anropas automatiskt av den GUIX Studio-genererade startkoden, men kan också anropas direkt av programmet för att ändra den aktiva strängtabellen.

Det aktiva språket tilldelas genom anrop ***gx_display_active_language_set*** API-funktionen. Den här funktionen avgör vilken kolumn i visningssträngtabellen som är aktiv.

När den här funktionen anropas skickas **en GX_EVENT_LANGUAGE_CHANGE-händelse** till alla synliga GUIX-widgetar, så att de kan uppdatera för att visa nyligen aktiva strängdata.

Widgetar och programprogramvara löser statiskt definierade strängar med sträng-ID-värden och ***gx_display_string_get_ext*** eller ***gx_widget_string_get_ext*** API-funktioner. De här funktionerna returnerar **GX_STRING som** är associerade med ett visst sträng-ID och det aktiva språket.

### <a name="bi-directional-text-display"></a>Dubbelriktad textvisning 

GUIX tillhandahåller två strategier för dubbelriktad textsupport.

Ett alternativ är att ordna om bidi-text i GUIX Studio-programmet. Med det här alternativet ansvarar GUIX Studio för att generera bidi-text till utdatafilen i visningsordningen. Den här lösningen har ingen inverkan på körningsprestanda och kräver inga tillägg till GUIX-körningsbiblioteket. Om du vill tillåta att GUIX Studio genererar displayorder-bidi-textsträngar markerar du kryssrutan **Generera Bidi-text** i visningsordning i dialogrutan för guix studio-språkkonfiguration:

![Konfigurera språk](./media/guix/user-guide/configure-languages.png)

När dessa alternativ är markerade innehåller den genererade resursfilen Bidi-strängar som genererats i visningsordning och ingen extra bearbetning krävs i GUIX-körningsbiblioteket.

Det andra alternativet är att ordna om bidi-text vid körning. Det här alternativet stöds för de program som måste hantera bidi-textsträngar som definieras dynamiskt och som inte genereras av GUIX Studio-programmet. I det här fallet ansvarar GUIX-körningsbiblioteket för att ordna om bidi-texten innan varje textsträng ritas. Den här lösningen har en påverkan på körningsprestanda och minne. Tillräckligt med dynamiskt minne måste vara tillgängligt för omsorteringsprocessen för bidi-text. Den här lösningen kräver att den villkorliga GX_DYNAMIC_BIDI_TEXT_SUPPORT definieras när GUIX-biblioteket byggs. Två ***API-funktioner gx_system_bidi_text_enable*** och ***gx_system_bidi_text_disable*** tillhandahålls för att aktivera/inaktivera stöd för bidi-text vid körning.

Du bör inte använda både **GX_DYNAMIC_BIDI_TEXT_SUPPORT** och konfigurera GUIX Studio för att generera Bidi-text i visningsordning. Du måste välja en strategi eller en annan för att hantera bidi-textsträngar.

## <a name="memory-usage"></a>Minnesanvändning 

GUIX finns tillsammans med programmet. Därför bestäms användningen av GUIX för statiskt minne (eller fast minne) av utvecklingsverktygen. till exempel kompilatorn, länkaren och lokaliseraren. Användningen av dynamiskt minne (eller körningsminne) är under direkt kontroll av programmet.

### <a name="static-memory-usage"></a>Statisk minnesanvändning 

De flesta utvecklingsverktyg delar in programavbildningen i fem grundläggande *områden:* instruktion , *konstant,* *initierade data,* *oinitierade data* och *GUIX-trådstacken*.  Bilden nedan visar en möjlig layout av dessa minnesområden:

![Minneslayout](./media/guix/user-guide/memory-area-example.png)

Det är viktigt att förstå att detta bara är ett exempel. Den faktiska statiska minneslayouten är specifik för processor, utvecklingsverktyg, underliggande maskinvara och själva programmet.

Instruktionsområdet innehåller alla programprocessorinstruktioner. Det här området finns ofta i ROM.

Det konstanta området innehåller olika kompilerade konstanter, som i GUIX innehåller standardinställningar och alla programresurser (bilder, strängar, teckensnitt och färger). Dessutom innehåller det här området den "inledande kopian" av det initierade dataområdet. Under kompilatorns initieringsprocess används den här delen av konstantområdet för att konfigurera globala initierade data i RAM-minnet. Det konstanta området är vanligtvis det största och följer vanligtvis instruktionsområdet och finns ofta i ROM.

GUIX-pixelkartor och teckensnitt kräver vanligtvis stora mängder konstant datalagring. Dessa stora statiska dataområden lagras normalt i ROM eller FLASH.

GUIX-trådstacken definieras i det oinniterade dataområdet (som en global variabel) ***i gx_system.h-filen*** enligt följande:

```C
_gx_system_thread_stack[GX_THREAD_STACK_SIZE];
```

**GX_THREAD_STACK_SIZE** definieras i **_gx_port.h_**, men kan åsidosättas av programmet genom att definiera den här symbolen i ***gx_user.h-huvudfilen*** eller via projektalternativ eller kommandoradsparametrar. Stackstorleken måste vara tillräckligt stor för att hantera händelsehantering i värsta fall och kapslade ritnings-anrop.

### <a name="dynamic-memory-usage"></a>dynamiskt minne användning 

Som tidigare nämnts är dynamisk minnesanvändning under direkt kontroll av programmet. Kontrollblock och minne som är associerade med arbetsytor osv. kan placeras var som helst i målets minnesutrymme. Det här är en viktig funktion eftersom den underlättar enkel användning av olika typer av fysiskt minne – vid körning.

Anta till exempel att en målmaskinvarumiljö har både snabbt minne och långsamt minne. Om programmet behöver extra prestanda för ritning kan arbetsytans minne uttryckligen placeras i området för höghastighetsminne för bästa prestanda.

Flera valfria GUIX-tjänster och -funktioner kräver en dynamisk minnesallokeringsmekanism för körning, vilket ofta kallas en heap. Dessa tjänster och funktioner är helt valfria och många GUIX-program använder inte någon heap och definierar inte någon mekanism för minnesallokering vid körning.

Om du ska använda tjänster som kräver minnesallokering vid körning måste du installera funktioner som GUIX anropar när minnet måste allokeras dynamiskt eller frigöras. Du kan implementera dessa funktioner som du vill, så att även i det här fallet är platsen för den dynamiska minnespoolen under programkontroll. Om du vill installera stöd för dynamisk minnesallokering bör programmet anropa ***API-gx_system_memory_allocator_set*** under programstarten för att definiera din minnesallokering och minnesfria tjänster. Ett komplett exempel finns i dokumentationen för det här API:et.

GUIX-tjänster som kräver en körningsminnesallokering och avallokeringstjänst omfattar:

  - Läsa in binära resurser från extern lagring i GUIX-körningsmiljön.

  - Jpeg-bildavkodaren för programkörning.

  - Png-bildavkodaren för programkörning.

  - Använda textwidgetar med GX_STYLE_TEXT_COPY.

  - Funktioner för storleksändring och rotationsverktyg för körningsdiagram.
  - Körningsskärmen och widgeten styr blockallokeringen.

För mindre program kompileras VANLIGTVIS GUIX-resurser och länkas statiskt som en del av programavbildningen, och installation av binär resurs krävs inte. Binära resurser gör att ett program kan installera resurser (teckensnitt, bilder, språk) vid körning som lästs in från en lagringsplats, till exempel ett flash-minne eller en URL.

Jpeg- och png-avkodare för körning är valfria komponenter. De flesta GUIX-program tillåter att GUIX Studio-verktyget förkodar alla nödvändiga bildfiler och lagrar dem som egna GUIX Pixemap-dataresurser. Dessa tjänster tillhandahålls för fullständighet för de program som kräver körningskonvertering av jpeg- och/eller PNG-bilder till pixelkartformat.

**GX_STYLE_TEXT_COPY** tillåter användaren att ange att en viss widget eller widget behåller sin egen privata kopia av dynamiskt tilldelad text. Om du använder det här alternativet måste minnesallokeringsmekanismen installeras innan du använder den. Om den här **<span class="underline">stilflaggan</span>** inte anges när en texttypswidget skapas måste programmet allokera statiska lagringsområden för alla dynamiskt skapade och tilldelade textsträngar. Automatiska variabler ska inte användas i det här fallet för att lagra körningsgenererade strängdata. Om formatet **GX_STYLE_TEXT_COPY** aktiverat kan automatiska variabler användas för att lagra strängdata som tilldelats GUIX-widgetar, eftersom varje widget skapar en egen kopia av den tilldelade texten.

Funktionerna för storleksändring och rotation av pixelkarta returnerar den resulterande översatta pixelkartan som en ny pixelkarta som är tillgänglig för programmet.
Tillräckligt med dynamiskt minne måste vara tillgängligt för att lagra dessa körningsgenererade pixelkarta-datablock om dessa tjänster används.

Slutligen kan kontrollblocken för GUIX-skärmarna och widgetarna allokeras statiskt eller dynamiskt. För mindre program är det vanligt att skapa alla programskärmar under programstart och använda statiskt allokerade kontrollblock. För stora program är det vanligt att skapa skärm- och underordnade widgetkontroller dynamiskt på en efter behov-bas. Dynamiskt allokerade kontrollblock anges  genom att markera kryssrutan Allokera körning i GUIX Studio-egenskapsvyn eller genom att skicka stilflaggan **GX_STYLE_DYNAMICALLY_ALLOCATED** när du skapar en widget via standard-API:et. Användning av dynamiskt allokerade widgetkontrollblock kräver att tjänsterna för minnesallokering och avallokering definieras enligt beskrivningen ovan.

## <a name="guix-components"></a>GUIX-komponenter 

GUIX-API:erna är indelade och ordnade i flera grundläggande grupper som motsvarar grundläggande komponenter i GUIX-systemet. De grundläggande komponenterna är:

| Komponenter  | Beskrivning  |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GX_SYSTEM  | GUIX-systemkomponenten, som ansvarar för initiering, händelser, timers, strängtabeller och synlig hantering av widgethierarki.                                                                                                                                                                                                                                                                      |
| GX_CANVAS  | Ett ritningsområde. En arbetsyta kan vara en tunn abstraktion av maskinvarurambufferten, eller också kan det vara en ren minnesarbetsyta. Typen av arbetsyta bestäms av parametrar som skickas gx_canvas_create API-funktionen.                                                                                                                                                                                   |
| GX_CONTEXT | Komponenten för ritningskontext. Ritningskontexten innehåller information om skärmen, arbetsytan och pensel- och urklippsområdet för de aktuella ritningsoperationerna.                                                                                                                                                                                                                                      |
| GX_DISPLAY | Tillhandahåller API:er och implementeringar på drivrutinsnivå så att ditt program och GUIX-widgetar kan utföra ritning på en arbetsyta. GX_DISPLAY implementeras för att korrekt återge grafik på varje arbetsyta med hjälp av arbetsytans färgformat som krävs. Komponenten GX_DISPLAY hanterar också de resurser (färger, teckensnitt och pixelkartor) som är tillgängliga för widgetar som ritar på arbetsyta som är länkade till varje visning. |
| GX_WIDGET  | Det grundläggande synliga widgetobjektet och tillhörande API:er. Alla GUIX-widgettyper baseras på eller härleds från den grundläggande GX_WIDGET typ.                                                                                                                                                                                                                                                                      |
| GX_UTILITY | Verktygsfunktioner för att arbeta med rektanglar, funktioner för strängkonvertering och icke-ANSI-matematiska funktioner ingår i den här gruppen.                                                                                                                                                                                                                                                         |

Förutom dessa grundläggande komponenter innehåller GUIX API:er som är unika för varje typ av widget som finns i biblioteket. Dessa API:er beskrivs i kapitel 4 i den här användarhandboken, "Beskrivning av GUIX-tjänster".

## <a name="guix-system-component"></a>GUIX-systemkomponent

GUIX-systemkomponenten tillhandahåller flera tjänster som är globala för UI-programmet. Dessa tjänster omfattar: *initiering, händelsehantering, visningshantering, resurshantering, timerhantering och* *widgethantering.* Varje tjänst är viktig för organisationen av ditt program, och dessa tjänster beskrivs i detalj i följande underavsnitt.

### <a name="initialization"></a>Initiering 

GUIX-initiering åstadkoms genom att programmet anropar service ***gx_system_initialize***, som kan anropas av programmet från ThreadX ***tx_application_define-rutinen*** (initieringskontext) eller från programtrådar. Funktionen ***gx_system_initialize*** initierar alla globala GUIX-datastrukturer och skapar GUIX-systemet mutex, händelsekö, timer och tråd. När ***gx_system_initialize*** returneras kan programmet använda GUIX.

### <a name="thread-processing"></a>Trådbearbetning 

Den interna GUIX-tråden – som skapades under initieringen – ansvarar för merparten av bearbetningen i GUIX. Bearbetningen i den här tråden slutför först eventuell ytterligare initiering som krävs av den underliggande visningsdrivrutinen. När detta är klart går GUIX-tråden in i en loop som först bearbetar alla händelser som finns i GUIX-händelsekön och sedan uppdaterar skärmen om det behövs. Skärmuppdateringen kör nödvändiga GUIX-ritningsfunktioner, baserat på vad som är synligt och har markerats som grovt, vilket innebär att det måste ritas om. När det inte finns några händelser och inget kvar att uppdatera på skärmen pausas GUIX-tråden och väntar på att nästa GUIX-händelse ska tas emot.

### <a name="rtos-binding"></a>RTOS-bindning 

GUIX-systemkomponenten är som standard konfigurerad för att använda operativsystemet ThreadX i realtid för tjänster som trådtjänster, händelsekötjänster och timertjänster. GUIX kan enkelt portas till andra operativsystem med hjälp av direktivet preprocessor GX_DISABLE_THREADX_BINDING och bygga om GUIX-biblioteket. Detta tar bort ThreadX-beroenden från GUIX-källkoden och gör att programutvecklaren kan implementera nödvändiga operativsystemtjänster med hjälp av det RTOS som tillhandahålls av målsystemet. [Bilaga F – GUIX RTOS-bindningstjänster](appendix-f.md) beskriver de tjänster som måste implementeras på port-GUIX till ett annat operativsystem än ThreadX-operativsystemet.

### <a name="multithread-safety"></a>Flertrådssäkerhet 

GUIX-API:et är tillgängligt från GUIX-trådkontexten samt andra programtrådar. Programtrådar kan interagera med GUIX-tråden genom att skicka och ta emot händelser, via åtkomst till delade variabler och med hjälp av GUIX API-funktionerna. GUIX använder en intern ThreadX mutex för resursskydd med flera trådar. Dessutom förhindrar GUIX att den interna strukturen för synliga widgetar ändras när en uppdateringsåtgärd har påbörjats. API:er som ändrar trädet för synliga objekt blockeras när ritningsåtgärder pågår och släpps när skärmuppdateringen är klar.

### <a name="system-timers"></a>Systemtimerar 

GUIX ger programmet periodiska timers, som ofta används för regelbunden uppdatering av data som visas i GUIX-fönster. Detta åstadkoms via en periodisk ThreadX-timer, som också används för att utföra GUIX-systemnivåeffekter som skärmtoning in/ut osv.

Programmet kan skapa timers och använda samma timerfunktion som används internt av GUIX. Naturligtvis kan programmet också skapa och använda ThreadX-timers direkt om det behövs. Fördelen med GUIX-timers är att de är mycket enkla att använda och är förkonfigurerade att fungera i GUIX-händelsedrivna bearbetningssystem.

För att skapa och starta en GUIX-timer ska programmet anropa funktionen ***gx_system_timer_start***. Parametrarna för den här funktionen innehåller en pekare till den anropande widgeten, timer-ID:t (så att en widget kan starta många timers) och de inledande och omplanerade timeout-värdena. Om tidsgränsvärdet för omplan är 0 körs timern bara en gång och tar bort sig själv från listan över aktiva timer när den upphör att gälla.

När guix-timern har startats skickar den GX_EVENT_TIMEOUT händelser till timerägaren, antingen en gång eller regelbundet beroende på timern som schemalades om. En GUIX-timer kan stoppas genom att anropa ***API-funktionen gx_system_timer_stop***.

### <a name="pen-speed-configuration"></a>Konfiguration av pennhastighet 

GUIX-systemkomponenten innehåller konfigurationsinformation som rör spårning av pennhastighet. GUIX genereras **GX_EVENT_VERTICAL_FLICK** och **GX_EVENT_HORIZONTAL_FLICK** händelser baserat på hastighet och avstånd för PEN_DOWN-händelser som genereras av touch-indatadrivrutinen, om sådana finns. Programmet kan konfigurera det minsta avstånd och den hastighet som krävs för att utlösa dessa internt genererade händelser med hjälp **_gx_system_pen_configure_** API-funktionen.

### <a name="screen-stack"></a>Skärmstack 

GUIX-systemkomponenten tillhandahåller tjänster relaterade till GUIX-skärmstacken, vilket är en valfri funktion som stöder en virtuell widgetstack på vilken skärmar kan pushas, skjutas och hämtas vid körning av programmet. Skärmstacken är användbar för att hantera komplexa menysystem, där den väg som användaren kan komma åt i olika tillstånd i menysystemet varierar. Det är enkelt att gå tillbaka till det tidigare tillståndet i menysystemet genom att först push-skicka det tidigare skärmtillståndet och sedan visa den nya skärmen och låta den nya skärmen öppna föregående tillstånd från skärmstacken när den aktuella skärmen ignoreras.

### <a name="clipboard-maintenance"></a>Underhåll av Urklipp 

GUIX stöder urklipp för att kopiera och klistra in text under körning. Det här stödet tillhandahålls av GUIX-systemkomponenten.

### <a name="dirty-list-maintenance"></a>Underhåll av dirty list 

GUIX har en lista över felgrafiska widgetar, vilket innebär att widgetar som är synliga och måste ritas om på grund av statusändringar eller nyligen synliga. Den här ändrade listan förbättrar ritningens prestanda genom att tillåta GUIX att göra en uppdateringsåtgärd för arbetsytan för att återspegla alla aktuella ändringar av ui-statusen, i stället för att göra en uppdatering av arbetsytan när varje ui-ändring görs.
Den här listan underhålls också av GUIX-systemkomponenten.

### <a name="animation-control-block-pool"></a>Blockpool för animeringskontroll 

Program vill ofta köra flera animeringssekvenser, ofta parallellt. GUIX har en pool med animeringskontrollblock som programmet kan allokera och använda från. Detta frigör programmet från att statiskt definiera dessa kontrollblock och gör att de kan återanvändas vid olika tidpunkter, i stället för att definiera ett unikt animeringskontrollblock för varje animering som programmet kan definiera. Blockpoolen för animeringskontroll underhålls också av GUIX-systemkomponenten.

### <a name="system-error-handling"></a>Systemfelhantering 

GUIX-systemfelhanteraren är avsedd att hjälpa programmet att hitta interna systemfel i GUIX som kan vara svårare att fastställa ur API-perspektivet. När ett systemfel inträffar i GUIX anropas ***den _gx_system_error_process*** funktionen. Den här funktionen sparar den angivna felkoden och ökar det totala antalet identifierade systemfel. Systemfelvariablerna definieras på följande sätt:

UINT **_gx_system_last_error**;

ULONG **_gx_system_error_count**;

Om GUIX-programmet beter sig konstigt är det bra att titta på variabeln felantal i felsökningsprogrammet. Om den har angetts är ett bra sätt att felsöka problemet att ange en ***brytpunkt i _gx_system_error_process-funktionen*** och se när/var den anropas från.

## <a name="guix-canvas-component"></a>GUIX-arbetsytekomponent

Komponenten för arbetsyta ansvarar för all arbetsyterelaterad bearbetning. En arbetsyta är i praktiken en virtuell rambuffert. Programmet måste skapa minst en arbetsyta för att kunna skapa grafiska utdata.
Normalt skapar du minst en arbetsyta för varje fysisk skärm som stöds av systemet.

All GUIX-ritning sker på en arbetsyta. I enklare system eller minnesbegränsade system finns det förmodligen bara en arbetsyta som kan vara direkt länkad till den synliga rambufferten, medan system med mer minne och mer avancerade grafikkrav kan kräva flera arbetsyta. Genom att göra flera arbetsyta tillgängliga för en visning aktiveras funktioner som skärm- och fönstertonings- och toningsfunktioner.
Arbetsytetyper kan vara en av två huvudtyper, enkla eller hanterade.

En enkel arbetsyta är ett ritningsområde utanför skärmen som används av programmet.
GUIX gör ingenting direkt med en enkel arbetsyta, men programmet kan använda en enkel arbetsyta för att rendera komplex ritning till en buffert utanför skärmen och sedan använda den här bufferten utanför skärmen för att uppdatera den synliga arbetsytan när det behövs.

En hanterad arbetsyta visas automatiskt i maskinvarurambufferten av GUIX. En hanterad arbetsyta ingår i att skapa en sammansatt arbetsyta för dessa system med tillräckligt med minne för att stödja flera hanterade arbetsyta. Hanterade arbetsyta har en Z-ordning som underhålls av GUIX, och visningskakt tillämpas på alla hanterade arbetsyta.

En arbetsyta skiljer sig från en rambuffert på så sätt att den är mer allmän. I minnesbegränsade system kan det bara finnas en arbetsyta och minnet för den här arbetsytan kan vara det synliga rambuffertminnet. Men för mer komplexa system som stöder mer avancerade grafiska överlägg och flera arbetsytor allokeras de hanterade arbetsytorna sina egna minnesområden som skiljer sig från maskinvarurambuffertminnet.
Dessa hanterade arbetsyta återges i den synliga rambufferten under uppdatering av rambufferten eller växlingsåtgärden.

För maskinvara som stöder flera grafiklager, dvs. flera överläggsrambuffertar, kan programmet binda en eller flera arbetsyta till maskinvarugrafikskikten med hjälp av gx_canvas_hardware_layer_bind-API:et.  Den här tjänsten informerar arbetsytan om att den är länkad till ett visst maskinvarugrafiklager, och när arbetsytan har länkats försöker den använda maskinvarustöd för synlighet för arbetsyta (dvs. gx_canvas_show, gx_canvas_hide), alfablandning av arbetsyta (d.v.s. ***gx_canvas_alpha_set***) och förskjutning av arbetsytan i ***visningen***( gx_canvas_offset_set ).

För andra arkitekturer än den enklaste organisationen med en enda arbetsyta/en enda rambuffert bestäms storleken på en arbetsyta av programmet och kan vara annorlunda än den fasta storleken på en rambuffert.
Det kan också vara vid en förskjutning som valts av programmet. Annan information, till exempel Z-order, underhålls på arbetsytan. När arbetsytans ritning är klar överförs innehållet på arbetsytan till den fysiska visningen av visningsdrivrutinen. I vissa system som inte har tillräckligt med minne för en separat arbetsyta och rambuffertens minnesområden görs uppdateringen av arbetsytan direkt till den fysiska visningen via visningsdrivrutinen.

### <a name="canvas-creation"></a>Skapa arbetsyta 

Ett arbetsyteobjekt kan skapas under initieringen eller när som helst under körningen av programtrådar. Det finns ingen gräns för hur många arbetsyteobjekt som kan skapas av ett program. De flesta program skapar dock bara ett arbetsyteobjekt för all GUIX-ritning.

### <a name="canvas-control-block"></a>Kontrollblock för arbetsyta 

Egenskaperna för varje arbetsyteobjekt finns i dess kontrollblock **GX_CANVAS** definieras i **_gx_api.h_**. Det minne som krävs för ett arbetsyteobjekt tillhandahålls av programmet och kan finnas var som helst i minnet. Det är dock vanligast att göra arbetsytans objektkontrollblock och ritningsområdet till en global struktur genom att definiera dem utanför omfånget för en funktion.

### <a name="canvas-alpha-channel"></a>Alpha Channel för arbetsyta

GUIX stöder alfablanding av förgrunds- och bakgrundsfärger på många nivåer, inklusive alfakanal för bitmapp som anger ett blandningsförhållande per pixel, borst alfa som anger blandningsförhållandet för en pensel med 16 bpp och högre färgdjup och alfa för arbetsytan som anger blandningsförhållandet för en överläggsarbetsyta.

Alfavärdet för en arbetsyta används när det finns flera arbetsyta som är sammansatta tillsammans för visning i rambufferten. Om arbetsytans Z-ordning är sådan att en arbetsyta är ovanför andra arbetsyta kan du ange alfavärdet för arbetsytan för att blanda arbetsytan med de som ligger bakom. Snabb ändring av alfavärdet för en arbetsyta används för att ge "tona in"-skärmövergångseffekter, men alfa för arbetsyta kan användas på många sätt.

Om en arbetsyta är bunden till ett maskinvarugrafiklager med hjälp av gx_canvas_hardware_layer_bind(), försöker GUIX implementera alfablandning av arbetsyta med maskinvarustöd, vilket minimerar programvarukostnaderna som är associerade med att blanda en överläggsarbetsyta.

Alfavärden sträcker sig från 0 till 255, där värdet 0 innebär att pixeln är helt transparent och värden större än 0 ökar mindre transparent alfavärde för arbetsyta kan endast stödjas för skärmdrivrutiner som körs med 16 bpp och högre om inte maskinvaruhjälp för kombination av arbetsyta tillhandahålls.

### <a name="canvas-offset"></a>Förskjutning av arbetsyta 

En arbetsyta kan förskjutas inom den synliga rambufferten genom att anropa ***gx_canvas_offset_set API-tjänsten.*** Förskjutningar för arbetsyta används vanligtvis för att implementera andra animeringar. Om en arbetsyta är bunden till ett maskinvarugrafiklager genom att anropa ***gx_canvas_hardware_layer_bind*** API-funktionen, kommer GUIX att försöka implementera ändringar av arbetsytans offset med hjälp av maskinvarustöd, vilket minimerar programvarukostnaderna som är associerade med att flytta arbetsytans position.

### <a name="canvas-drawing"></a>Arbetsyteritning 

KOMPONENTEN GUIX-arbetsyta tillhandahåller ett fullständigt API för ritning till programmet. Innan du kan anropa ***API:erna för*** gx_canvas_line_draw eller ***gx_canvas_pixelmap_draw*** måste målarbetsytan öppnas för ritning genom att anropa ***API gx_canvas_drawing_initiate funktionen.*** Den här funktionen förbereder en arbetsyta för ritning och skapar en ***ritningskontext***.

De ritnings-API:er som återges på arbetsytan, till exempel ***gx_canvas_line_draw** _ eller _*_gx_canvas_text_draw_*_, använder parametrar som finns i den aktuella penseln för ritningskontext för att definiera linjeformat, bredd och färger. Dessa penselparametrar ändras genom att _*_anropa api-funktionerna gx_context_brush_define_*_, _* _gx_context_brush_set_**, ***gx_context_brush_style_set**_ och liknande API när en ritningskontext har upprättats genom att anropa _*_gx_canvas_drawing_initiate_**.

När GUIX anropar fönster- och widgetritningsfunktioner som en del av en uppskjuten arbetsyteuppdatering öppnas målarbetsytan för ritning innan widgetens ritningsfunktion anropas. Därför krävs inte standardwidgetritningsfunktioner för att öppna målarbetsytan, detta har gjorts för dem.

I vissa fall kanske programmet vill tvinga fram en omedelbar ritning till en arbetsyta. I det här fallet kan programmet utföra följande steg.

1. Anropa ***gx_canvas_drawing_initiate*** API-funktionen och skicka in målarbetsytan och rektangeln i arbetsytan som programmet vill rita på. 

2. Anropa val annat antal API:er för arbetsyteritning för att utföra den önskade ritningen.

3. Anropa ***API gx_canvas_drawing_complete funktionen*** för att signalera att ritningen har slutförts. Detta rensar arbetsytan till den synliga rambufferten och/eller utlöser en buffert växlingsåtgärd, beroende på systemets minnesarkitektur.

### <a name="drawing-apis"></a>API:er för ritning 

Det finns flera primitiver för huvudritning som krävs av GUIX för att rita alla visuella element på skärmen. De här API:erna för ritning kan också anropas av programprogramvaran, vanligtvis som en del av en anpassad widgetritning. Dessa API:er för GUIX-arbetsyteritning utför parametervalidering och urklipp och skickar sedan de urklippta ritningskoordinaterna till visningsdrivrutinen för maskinvaru- och färgformatsspecifika ritningsimplementeringar. Dessa api-ritningsfunktioner definieras på följande sätt.

- gx_canvas_alpha_set
- gx_canvas_arc_draw
- gx_canvas_block_move
- gx_canvas_circle_draw
- gx_canvas_ellipse_draw
- gx_canvas_glyphs_draw
- gx_canvas_hardware_layer_bind
- gx_canvas_hide
- gx_canvas_line_draw
- gx_canvas_offset_set
- gx_canvas_pie_draw
- gx_canvas_pixel_draw
- gx_canvas_pixelmap_blend
- gx_canvas_pixelmap_rotate
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw
- gx_canvas_rotated_text_draw
- gx_canvas_shift
- gx_canvas_show
- gx_canvas_text_draw

Api:et för ritning anropas via API:et för GUIX-arbetsytan och all ritning görs med hjälp gx_canvas_* API-funktioner. Ritningen görs med hjälp av den aktuella penseln i den aktuella ritningskontexten. Alla formritningsfunktioner ovan kan beskrivas, en heldragen färg eller en pixelkarta som fyllts enligt definitionen i den aktuella penseln. Om du vill ändra bredd, färg eller fyllning för formkonturerna använder du API gx_context_brush_funktionerna* för att definiera penseln i den aktuella ritningskontexten.

Ovanstående API:er för ritning på programnivå gör inte själva ritningen till arbetsytan, utan verifierar i stället anroparens parametrar innan du anropar funktionen för att visa förarnivåritning. Ritningsfunktionen på drivrutinsnivå skriver faktiskt pixeldata till arbetsytans minne.

GUIX tillhandahåller aktiebaserade eller allmänna visningsdrivrutiner för olika färgdjup, inklusive 1, 2, 4, 8, 16, 24 och 32 bitar per pixel (bpp). I vissa fall ersätts standardimplementering av programvaruritning med maskinvaruaccelererade implementeringar för de maskinvarumål som tillhandahåller en 2D-ritningsaccelerator.

### <a name="color-depth"></a>Färgdjup 

GUIX stöder färgdjup upp till 32 bpp samt gråskala och gråskala. Typen av stöd för färgdjup bestäms huvudsakligen av funktionerna i den underliggande fysiska visningen och påverkar även hur mycket minne som krävs för arbetsytans ritningsområde. Följande är en lista över stöd för färgdjup tillsammans med en kort beskrivning av variationerna inom det färgdjupet.

| &nbsp;Färgformat       | Beskrivning                                                                                                   |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| 1-bitars 1-bitars   | 1 bit per pixel-paketerad format.                                                                                                   |
| 2-bitars gråskala    | 4 grå nivåer, packade fyra bildpunkter per byte.                                                                                      |
| 4-bitars gråskala    | 16 grå nivåer, packade två bildpunkter per byte.                                                                                      |
| 4-bitarsfärg        | En planarminnesorganisation i VGA-format.                                                                                         |
| 8-bitars gråskala    | 256 grå nivåer                                                                                                                  |
| 8-bitars paletteläge | 1 byte per pixel som används som paletteindex                                                                                           |
| 8-bitars r:g:b-läge   | Ett mindre vanligt 2:3:2 r:g:b-format.                                                                                         |
| 16-bitars             | Varje pixel kräver två byte. Kan vara r:g:b eller b:g:r byteordning. Normalt struktur 5:6:5, men kan också vara struktur 5:5:5 eller 4:4:4:4 a:r:g:b. |
| 24-bitars             | Varje pixel kräver 3 (packad format) eller 4 (uppackade format) byte. Kan vara i r:g:b eller b:g:r byte ordning som krävs av maskinvaran. |
| 32-bitars             | Varje pixel kräver 4 byte med en alfakanal. Kan vara a:r:g:b eller b:g:r:a byteordning och bestäms av maskinvara.              |

### <a name="mouse-support"></a>Musstöd 

GUIX stöder ritning av en musmarkör på valfri arbetsyta. Musmarkören kan ritas i programvara eller kan ha stöd av maskinvarumarkörsöverlägg. I båda fallen är API:et som tillhandahålls till programmet relaterat till stöd för markörer detsamma oavsett om du använder programvaru- eller maskinvarumarkörsritning.

GUIX-musstöd är endast aktiverat om har definierats `#define GX_MOUSE_SUPPORT` i gx_user.h-huvudfilen innan GUIX-biblioteket byggs.

Programmet måste definiera markören och hotspot med hjälp ***gx_canvas_mouse_define*** API-funktionen. Det här API:et accepterar en pekare till arbetsytan där markörbilden ska ritas och en pekare till **en GX_MOUSE_CURSOR_INFO-struktur,** som definierar musmarkörbilden och hotspot för musbilden relativt den övre vänstra bilden.

## <a name="guix-display-component"></a>GUIX-visningskomponent 

Visningskomponenten är grundläggande i GUIX eftersom den hanterar bearbetningen av alla visningsobjekt, som i sig innehåller en eller flera arbetsyta, widgetar och fönster. Visningskomponenten interagerar också med den underliggande maskinvaruskärmdrivrutinen som är associerad med varje visning via en serie funktionspekare.

### <a name="display-creation"></a>Skapa visning 

Ett visningsobjekt kan skapas under initieringen eller när som helst under körningen av programtrådar. Vanligtvis skapar ett program ett visningsobjekt för att hantera varje fysisk skärm. Om du har använt GUIX Studio för att definiera ditt program och de fysiska skärmarna som är tillgängliga använder du API gx_studio_display_configure funktionen för att skapa och initiera var och en av dina skärmar.

### <a name="display-control-block"></a>Visningskontrollblock 

Egenskaperna för varje visningsobjekt finns i dess kontrollblock ***GX_DISPLAY** _ och definieras i _*_gx_api.h_**. Det minne som krävs för ett visningsobjekt tillhandahålls av programmet och kan finnas var som helst i minnet. Det är dock vanligast att göra visningskontrollblocket till en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="resource-management"></a>Resurshantering 

Resurser är gränssnittskomponenter som krävs av programmet, men de är inte programkod. Resurser är programdata och definieras vanligtvis statiskt. Resurstyper är pixelkartor, teckensnitt, färger och strängar. Dessa resurser kan ändras när som helst, vanligtvis utan att ändra någon programvara. Det är viktigt att hålla lagringen av och referenser till resurser åtskilda från programprogramvaran för att tillåta ändring av användargränssnittets utseende utan att ändra programkod eftersom ändringar i programprogramvaran vanligtvis kräver tillhörande omtestning och verifiering av programvaran.

***GUIX-visningsmodulen*** tillhandahåller resurshantering för alla resurser som är beroende av färgdjupet och formatet på skärmen. Dessa anläggningar omfattar att underhålla den aktiva pixelkarta-tabellen, aktiv teckensnittstabell och aktiv färgtabell. Strängtabellresursen underhålls av GUIX-systemmodulen eftersom strängresurser normalt inte behöver ändras baserat på färgdjup och format.

Programmet refererar till resurser efter resurs-ID, vilket är ett index i motsvarande resurstabell. Detta gör att tabellen kan ändras, till exempel kan färgtabellen ändras när en produkt ändras från "dagläge" till "nattläge", men färg-ID-värdena förblir desamma.

Dina programresurser skrivs till en resursfil (eller en uppsättning resursfiler) av GUIX Studio-programmet. Standardfärger, pixelkartor och teckensnitt tillhandahålls automatiskt när du skapar ett nytt GUIX Studio-projekt, men dessa standardvärden ersätts enkelt när du definierar utseendet och känslan i ditt program.

Det är viktigt att observera att resurs-ID:er för färger, teckensnitt och pixelkartor inte kan matchas till deras faktiska värden för färg, teckensnitt eller pixelkarta förrän den aktiva visningskomponenten är känd. Eftersom GUIX-arkitekturen stöder flera aktiva visningar kan resurs-ID:n bara matchas till resursvärden när en widget och dess associerade resurs-ID kan matchas till en specifik visning. Den här egenskapen kallas dynamisk bindning. Resurs-ID för en egenskap, till exempel en textfärg, till exempel resurs-ID **GX_COLOR_ID_TEXT,** kan matcha till ett 16-bitars R:G:B-värde för vitt när det används på en skärm, men samma färg-ID kan matcha till ett svart färgvärde när det används på en annan visning.

I praktiken innebär den här dynamiska bindningen av resurs-ID:er till resursvärden att programprogramvara och interna GUIX-komponenter oftast bara ska matcha resurs-ID:er till resursvärden i en aktiv ritningskontext. En aktiv ritningskontext anger den aktiva visningen, vilket gör att GUIX kan matcha varje resurs-ID till ett specifikt resursvärde. Om programprogramvaran krävs för att hitta ett specifikt resursvärde utanför en ritningskontext kan detta även göras för synliga widgetar. Synliga widgetar är länkade till ett rotfönster som också kan användas för att matcha den aktiva arbetsytan och visningen för widgeten.

Om en widget har skapats men ännu inte visas (d.v.s. inte har länkats till något rotfönster eller något annat synligt överordnat fönster), kan inte resurs-ID:n som är associerade med widgeten matchas till ett specifikt resursvärde förutom genom att indexera direkt till resurstabellen som är tilldelad till en specifik visning. Den här direktåtkomsten till en specifik resurstabell kan utföras på ett säkert sätt av programprogramvaran, men görs aldrig i den interna GUIX-biblioteksprogramvaran.

### <a name="widget-defaults"></a>Standardinställningar för widget 

GUIX-visningskomponenten innehåller också standarddefinitioner för olika widgetattribut. Om inget annat anges av programmet skapas widgetar/fönster med dessa systemattribut. Dessa systemattribut består huvudsakligen av teckensnitt, färger och bitmappar som finns i systemets resurstabeller. Ytterligare attribut för standardutseendet av rullningslisten underhålls också av GUIX-visningskomponenten.

Standardfärginställningarna definieras av färgtabellen som tilldelas varje visning och de fördefinierade standardfärg-ID:erna. Dessa standardfärg-ID:n inkluderar följande.

| Färg-ID | Beskrivning |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| GX_COLOR_ID_CANVAS | Standardfärg för arbetsyta (d.v.s. visa bakgrund) |
| GX_COLOR_ID_WIDGET_FILL | Fyllningsfärg för standardwidget |
| GX_COLOR_ID_WINDOW_FILL | Standardfärg för fönsterfyllning |
| GX_COLOR_ID_DISABLED_FILL | Standardinaktiverad widgetfyllningsfärg |
| GX_COLOR_ID_DEFAULT_BORDER | Standardfärg för widgetens kantlinje |
| GX_COLOR_ID_WINDOW_BORDER | Standardfärg för fönsterkantlinje |
| GX_COLOR_ID_TEXT | Standardtextfärg |
| GX_COLOR_ID_SELECTED_TEXT | Standardvald textfärg |
| GX_COLOR_ID_DISABLED_TEXT | Standard inaktiverad textfärg |
| GX_COLOR_ID_SELECTED_TEXT_FILL | Standardvald textfyllningsfärg |
| GX_COLOR_ID_READONLY_TEXT | Standardfärg för skrivskyddade text |
| GX_COLOR_ID_READONLY_FILL | Standardfärg för skrivskyddade textfyllningar |
| GX_COLOR_ID_SCROLL_FILL |    Fyllningsfärg för rullningslist |
| GX_COLOR_ID_SCROLL_BUTTON | Fyllningsfärg för knapp för rullningslist |
| GX_COLOR_ID_SHADOW | Standardskuggfärg |
| GX_COLOR_ID_SHINE | Standardfärg för markering |
| GX_COLOR_ID_BUTTON_BORDER | Knappwidgetens kantlinjefärg |
| GX_COLOR_ID_BUTTON_UPPER | Knappwidgetens övre fyllningsfärg |
| GX_COLOR_ID_BUTTON_LOWER | Knappwidget med lägre fyllningsfärg |
| GX_COLOR_ID_BUTTON_TEXT | Textfärg för knappwidget |
| GX_COLOR_ID_TEXT_INPUT_TEXT | Textfärg för text i textinmatningswidgeten |
| GX_COLOR_ID_TEXT_INPUT_FILL | Fyllningsfärg för textinmatning |
| GX_COLOR_ID_SLIDER_TICK | Färg som används för att rita bockmarkeringar för skjutreglage. |
| GX_COLOR_ID_SLIDER_GROOVE_BOTTOM | Färg som används för att rita skjutreglagets skjutreglage |
| GX_COLOR_ID_SLIDER_NEEDLE_OUTLINE | Färg som används för att rita nålkontur |
| GX_COLOR_ID_SLIDER_NEEDLE_FILL | Färg som används för att fylla på skjutreglagets nål |
| GX_COLOR_ID_SLIDER_NEEDLE_LINE1 | Färg som används för att rita nål markeringar |
| GX_COLOR_ID_SLIDER_NEEDLE_LINE2 | Färg som används för att rita nålskuggor |

Dessa färg-ID-värden mappas till ett specifikt färgvärde som definieras av färgtabellen som är tilldelad till varje visning. Dessa standardvärden kan ändras som en grupp för en visning genom att anropa ***gx_display_color_table_set*** API-funktionen. Om du använder GUIX Studio initieras visningsfärgtabellen automatiskt  när programmet anropar gx_studio_display_configure funktionen.

GUIX-visningskomponenten har också en standardtabell för teckensnitt. Standardteckensnittstabellen definierar teckensnittet som används av varje widgettyp om det inte anges specifikt av programmet. De fördefinierade tabell-ID:erna för visningsteckensnitt innehåller följande värden.

| &nbsp;Teckensnitts-ID | Beskrivning |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------|
| GX_FONT_ID_DEFAULT | Standardteckensnitt som används när inget specifikt teckensnitt har definierats |
| GX_FONT_ID_BUTTON | Standardteckensnitt som används för all text på knappar |
| GX_FONT_ID_TEXT_INPUT | Standardteckensnitt som används för textredigeringsfält |

Teckensnitts-ID:t som används av valfri texttypswidget kan tilldelas om med hjälp av det **gx_<widget_type>_font_set-API** som tillhandahålls för varje textrelaterad widgettyp. Hela teckensnittstabellen kan tilldelas om genom att anropa **api gx_display_font_table_set funktionen.**

### <a name="scrollbar-appearance"></a>Rullningslistens utseende 

GUIX-visning har också standardinställningar för rullningslistens utseende för den visningen. De här inställningarna definieras av **GX_SCROLLBAR_APPEARANCE** struktur som definieras nedan. GUIX-visningen har en struktur för rullningslistens utseende för lodräta rullningslister och en andra struktur för vågräta rullningslister. Programmet kan ändra standardutseendet för rullningslisten för alla skärmar genom **att initiera en GX_SCROLLBAR_APPEARANCE** struktur och anropa API-funktionen ***gx_display_scroll_appearance_set***.

```c
typedef struct GX_SCROLLBAR_APPEARANCE_STRUCT
{
    GX_VALUE       gx_scroll_width;
    GX_VALUE       gx_scroll_thumb_width;
    GX_VALUE       gx_scroll_thumb_travel_min;
    GX_VALUE       gx_scroll_thumb_travel_max;
    GX_UBYTE       gx_scroll_thumb_border_style;
    GX_RESOURCE_ID gx_scroll_fill_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_pixelmap;
    GX_RESOURCE_ID gx_scroll_up_pixelmap;
    GX_RESOURCE_ID gx_scroll_down_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_color;
    GX_RESOURCE_ID gx_scroll_thumb_border_color;
    GX_RESOURCE_ID gx_scroll_button_color;
} GX_SCROLLBAR_APPEARANCE;
```
| GX_SCROLLBAR_APPEARANCE strukturmedlem | Beskrivning |
| --- | --- |
| gx_scroll_width | Bredden på en lodrät rullningslist eller höjden på en vågrät rullningslist, i bildpunkter. |
| gx_scroll_thumb_width | Bredden på hiss- och slutknapparna, i bildpunkter. |
| gx_scroll_thumb_travel_max | Förskjut från slutet av rullningslisten till den maximala respunkten för tumknappen. |
| gx_scroll_fill_pixelmap | Pixelkarta som används för att fylla rullningsbakgrunden. |
| gx_scroll_thumb_pixelmap | Pixelkarta som används för att rita bläddringstumknappen. |
| gx_scroll_up_pixelmap | Pixelkarta som används för att rita upp bläddringsknappen. |
| gx_scroll_down_pixelmap | Pixelkarta som används för att rita nedrullningsknappen. |
| gx_scroll_fill_color | Färg-ID för färg som används för att fylla rullningslistens bakgrund. |
| gx_scroll_button_color | Färg-ID för färg som används för att fylla rullningslistens tumknapp. |

Förutom dessa standardinställningar för teckensnitt, färg och format kan programmet ange valfria parametrar från fall till fall efter behov med hjälp av API:et som tillhandahålls av varje widgettyp.

### <a name="skinning-and-themes"></a>Skalning och teman

Utsnling gör att GUIX-widgetar och fönster enkelt kan ändra sitt basutseende, dvs. att ändra "hud" på en plats ändrar basutseendet för alla associerade widgetar och fönster.

Omskalning av GUIX-programmet kräver att du tillhandahåller en ny färg-, teckensnitts- och eller pixelkarta-tabell till GUIX-visningsresurstabellerna. Eftersom alla GUIX-widgetar refererar till färg, bitmappning eller teckensnitt efter resurs-ID gör en ny resurstabell automatiskt att alla GUIX-widgetar börjar använda dina nya färger och pixelkartor när de ritar sig till den önskade visningen.

En ny uppsättning teckensnitt, färger och pixelkartor som är utformade för att fungera tillsammans för att ge ett attraktivt utseende kallas för *ett tema.* Ett tema definierar en uppsättning resurstabeller och storleken på varje resurstabell. Val av antal teman kan definieras för alla skärmar med hjälp av GUIX Studio-programmet. Du måste skicka starttemaindexet till den GUIX Studio-genererade ***funktionen gx_studio_display_configure***, som installerar det första temat i den skapade visningen. Det aktiva temat för alla skärmar kan ändras när som helst genom att anropa funktionen ***gx_display_theme_install***.

### <a name="root-window"></a>Rotfönster

För varje synlig arbetsyta som skapats av ett program måste programmet också skapa ett rotfönster för arbetsytan. Det här särskilda fönstret fungerar i princip som en container för alla programfönster och widgetar på den översta nivån. Rotfönstret ritar arbetsytans bakgrund, och eftersom rotfönstret härleds **från GX_WINDOW-klassen** kan rotfönstret också ha skrivbordsunderlägg. Om du vill ändra bakgrundsfärgen för din skärm eller arbetsyta ändrar du helt enkelt fyllningsfärgen för rotfönstret som är kopplat till arbetsytan.

Om du använder den GUIX Studio-genererade ***funktionen gx_studio_display_configure*** för att konfigurera dina skärmar skapas arbetsytan och rotfönstret för varje visning åt dig som en del av initieringsfunktionen.

### <a name="anti-aliasing"></a>Antialias 

Antialias är en valfri funktion i GUIX som används för att jämna ut linjer, kurvor och teckensnitt. Antialias stöds endast när du kör med en visningsdrivrutin med 16 bpp eller högre färgdjup.

Antialias linjeritning aktiveras genom att ställa in **GX_BRUSH_ALIAS** flash i den aktiva penseln. Detta gäller för linjer som ritas direkt samt för linjer som ritas som kantlinje för en polygon eller cirkel.

Antialias textritning aktiveras med hjälp av ett antialias teckensnitt som produceras av GUIX Studio-programmet. Du anger om ett teckensnitt ska genereras som antialiased eller binär när du skapar teckensnittet.
Antialias teckensnitt i GUIX använder 16 nivåer av transparens för varje pixel.

### <a name="clipping"></a>Klippning 

Urklipp stöds internt av GUIX-visningskomponenten och i fönster- och widgetskikten av den överordnade-underordnade arkitekturen som underhålls av GUIX-widgetar. Inget fönster eller en widget tillåts någonsin rita utanför widgetens område och en widget får aldrig rita utanför området för widgetens överordnade område.

Detta förhindrar också widgetar från att rita vid pixelkoordinater som ligger utanför arbetsytans minne, vilket sannolikt leder till minnesfel eller systemfel. Widgetar får inte rita utanför widgetens område, widgetens överordnade område eller utanför arbetsytans utrymme.

Dessutom kan widgetar endast ritas till områden som tidigare har markerats som dirty (dirty). Detta förhindrar att ett helt fönster ritas, till exempel när bara ett hörn av fönstret har visats. Endast den del av fönstret som faktiskt behöver uppdateras markeras som dirty (dirty) så att fönsterritningsfunktionen bara uppdaterar bildpunkter i det dirty-området.

GUIX-visningskomponenten framtvingar dessa algoritmer innan ritningsfunktionerna på drivrutinsnivå används.

### <a name="views"></a>Vyer 

GUIX har alltid en uppsättning vyer för varje rotfönster och varje underfönster i rotfönstret. Vyer är ett dynamiskt, körningsbestämt urklippsområde som ändras när fönstrets position och Z-ordningen ändras.
GUIX använder vyer för att förhindra att ett fönster eller en widget i bakgrunden ritar ovanpå ett fönster eller en widget i förgrunden. Vyer tillämpar Z-ordningsdisciplin. Dessutom är vyer viktiga för effektiviteten eftersom de förhindrar att ett fönster i bakgrunden ritas till någon del av arbetsytan som inte kan ses. Om ett fönster är helt täckt av ett annat fönster, kommer det täckta fönstret inte att kunna ritas på arbetsytan alls, även om det försöker göra det.

### <a name="display-driver-interface"></a>Visa drivrutinsgränssnitt 

GUIX-visningsdrivrutiner ansvarar för all interaktion med den underliggande fysiska skärmen. Visningsdrivrutinerna har tre grundläggande funktioner: initiering, ritning och bildrutebuffertvisning.
Initieringen ansvarar för att förbereda den fysiska skärmmaskinvaran, informera GUIX om egenskaperna för den fysiska skärmmaskinvaran och informera GUIX om vilka specifika ritningsfunktioner som ska användas. Den huvudsakliga initieringen av visningsdrivrutiner anropas från ***GUIX-gx_display_create funktion.*** Dessutom anropar GUIX-tråden även en sekundär initiering av visningsdrivrutiner från trådkontexten. Den här sekundära visningsdrivrutinen behövs bara om drivrutinen behöver RTOS-tjänster under initieringen, t.ex. enhetsavbrott eller ***tx_thread_sleep-begäranden*** om fördröjning mellan stegen i initieringsprocessen.

När initieringen är klar ansvarar visningsdrivrutinen för alla direkta ritningar som kan göras i den fysiska skärmmaskinvaran.
Slutligen ansvarar visningsdrivrutinen för att visa rambufferten.

## <a name="guix-widget-component"></a>KOMPONENT FÖR GUIX-widget

En GUIX-widget är ett synligt grafiskt element. Det finns GUIX-komponenter som inte är synliga, till exempel timers och matematikverktygsfunktioner.
Alla synliga komponenter härleds dock från den grundläggande GUIX-widgetkomponenten. En GUIX-widget är den primära byggstenen i GUIX-visningen – alla andra grafiska element härleds från baswidgetens funktioner.

GUIX-widgetar implementeras på ett objektorienterat sätt med fullständigt stöd för arv. Detta åstadkoms med ansi C, vilket resulterar i minsta möjliga minne och bearbetningskrav. När vi talar om en viss widget, till  exempel **GX_BUTTON**, som härleds från en annan widget, till exempel **bas-GX_WIDGET**, är det vi menar att **GX_BUTTON-kontrollstrukturen** innehåller alla medlemsvariabler och funktionspekare för **GX_WIDGET**, med några ytterligare variabler som är specifika för **GX_BUTTON**. GUIX bygger upp lager av widgetar på det här sättet, så att mer komplexa widgetar alltid baseras på en enklare widget före dem. Den här hierarkiska modellen för härledning gör det enklare att lära sig de API:er som används för att ändra widgetparametrar. Om du vill ändra färgen på en knapp använder du samma API som du använder för att ändra färgen på en widget, ***nämligen gx_widget_fill_color_set***.

Organisationen av synliga widgetar underhålls på ett överordnat-underordnat sätt med hjälp av trädstrukturerade listor som länkar underordnade widgetar till sina föräldrar. Underordnade ärver egenskaper från sina föräldrar, till exempel vyer som de kan rita i och arbetsytan som de ritar på.
Underordnade widgetar kan ha sina egna underordnade widgetar, som återigen ärver olika egenskaper från den överordnade widgeten. Egenskaperna för en widget kan uttryckligen omdefinieras via olika GUIX API-anrop.

### <a name="widget-creation"></a>Skapa widget 

Ett widgetobjekt kan skapas under initieringen eller när som helst under körningen av programtrådar. Det finns ingen gräns för hur många widgetobjekt som kan skapas av ett program. Det finns heller ingen gräns för hur många underordnade en widget kan ha, inom minnesgränserna för målmaskinvaran.

Varje widgettyp har en egen create-funktion, till exempel ***gx_button_create** _ eller _*_gx_prompt_create_**. De första tre parametrarna för dessa funktioner är alltid desamma, nämligen en pekare till widgetens kontrollstruktur, en sträng pekare till widgetens namn och en pekare till widgetens överordnade. Varje create-funktion kan ha val av ytterligare parametrar beroende på kraven för den specifika widgettypen.

### <a name="widget-control-block"></a>Kontrollblock för widget 

Egenskaperna för varje widgetobjekt finns i dess kontrollblock och **GX_WIDGET** definieras i **_gx_api.h_**. Det minne som krävs för ett widgetobjekt tillhandahålls av programmet och kan finnas var som helst i minnet. Det är dock vanligast att göra widgetobjektets kontrollblock till en global struktur genom att definiera den utanför omfånget för en funktion. Om du använder GUIX Studio kan widgetkontrollblocken statiskt allokeras i din Studio-genererade specifikationsfil, eller så kan de allokeras dynamiskt av ditt program.

### <a name="dynamic-widget-control-block-allocation-and-de-allocation"></a>Blockallokering och avallokering för dynamisk widgetkontroll 

Om du använder dynamisk blockallokering måste du definiera två funktioner som GUIX använder för att allokera och frigöra det minne som krävs för widgetkontrollblocken. Dina funktioner för minneshantering skickas till GUIX-systemkomponenten via gx_system_memory_allocator_set  API-funktionen. Med den här funktionen kan du skicka två funktionspekare till GUIX: den första är en pekare till en minnesallokeringsfunktion och den andra är en pekare till en minnesfri funktion. Oftast implementerar du dessa funktioner med ThreadX-bytepooler, men med designen av GUIX kan du implementera dynamisk minneshantering på det sätt du föredrar.

Dynamisk widgetallokering används oftast i din Studio-genererade programspecifikationsfil när du väljer alternativet "dynamiskt allokerad" i egenskapsfältet för Studio-widgeten. Men du kan också använda dynamisk kontrollblocksallokering i ditt program. Om du använder dynamisk blockallokering i ditt program bör du anropa **API-funktionen*** gx_widget_allocate _ för att allokera widgetkontrollblocket. När du sedan skapar widgeten ska du kontrollera att du skickar formatflaggan _ *GX_WIDGET_STYLE_DYNAMICALLY_ALLOCATED** (tillsammans med andra formatflaggor som behövs) till widgetens create-funktion. Den här flaggan används för att markera widgeten som dynamiskt allokerad i widgetens statusfält. När och om widgeten senare tas bort med **_hjälp av gx_widget_delete_**, kontrollerar GUIX det här statusfältet och anropar automatiskt funktionen för avkrypterare av minne för att försäkra att det inte finns några minnesläckor.

> [!IMPORTANT]
> En widget som skapas med hjälp av ett dynamiskt allokerat kontrollblock måste skapas **med flaggan GX_WIDGET_STYLE_DYNAMICALLY_ALLOCATED** för att förhindra minnesförlust.

### <a name="types"></a>Typer

GUIX ger en omfattande, fullt funktionell uppsättning inbyggda widgetar. Som tidigare nämnts härleds alla specialiserade widgetar från baswidgeten. Följande är en lista över inbyggda widgetar i GUIX:

**GX_TYPE_WIDGET**

**GX_TYPE_BUTTON**

**GX_TYPE_TEXT_BUTTON**

**GX_TYPE_MULTI_LINE_TEXT_BUTTON**

**GX_TYPE_RADIO_BUTTON**

**GX_TYPE_CHECKBOX**

**GX_TYPE_PIXELMAP_BUTTON**

**GX_TYPE_ICON_BUTTON**

**GX_TYPE_ICON**

**GX_TYPE_SPRITE**

**GX_TYPE_SLIDER**

**GX_TYPE_PIXELMAP_SLIDER**

**GX_TYPE_VERTICAL_SCROLL**

**GX_TYPE_HORIZONTAL_SCROLL**

**GX_TYPE_PROGRESS_BAR**

**GX_TYPE_PROMPT**

**GX_TYPE_NUMERIC_PROMPT**

**GX_TYPE_PIXELMAP_PROMPT**

**GX_TYPE_NUMERIC_PIXELMAP_PROMPT**

**GX_TYPE_SINGLE_LINE_TEXT_INPUT**

**GX_TYPE_MULTI_LINE_TEXT_VIEW**

**GX_TYPE_MULTI_LINE_TEXT_INPUT**

**GX_TYPE_WINDOW**

**GX_TYPE_ROOT_WINDOW**

**GX_TYPE_VERTICAL_LIST**

**GX_TYPE_HORIZONTAL_LIST**

**GX_TYPE_POPUP_LIST**

**GX_TYPE_DROP_LIST**

**GX_TYPE_LINE_CHART**

**GX_TYPE_DIALOG**

**GX_TYPE_KEYBOARD**

**GX_TYPE_SCROLL_WHEEL**

**GX_TYPE_TEXT_SCROLL_WHEEL**

**GX_TYPE_STRING_SCROLL_WHEEL**

**GX_TYPE_NUMERIC_SCROLL_WHEEL**

**GX_TYPE_CIRCULAR_GAUGE**

**GX_TYPE_RADIAL_PROGRESS_BAR**

**GX_TYPE_RADIAL_SLIDER**

**GX_TYPE_MENU_LIST**

**GX_TYPE_MENU**

**GX_TYPE_ACCORDION_MENU**

**GX_TYPE_TREE_VIEW**


### <a name="styles"></a>Format

Widgetformat består av saker som kantlinjeegenskaper (upphöjt, upphöjt, tunt, tjockt eller ingen boarder alls) samt egenskaper för specifika widgettyper, enligt listan ovan. Widgetens stilflaggor är den enklaste metoden för att ändra utseendet på en widget.
Det inledande widgetformatet är alltid en parameter som skickas till widgettypen för specifik create-funktion.

### <a name="colors"></a>Färger 

Widgetar ritar sig själva med hjälp av färger som definierats i systemfärgtabellen.
Färg-ID:er definieras för arbetsytans bakgrund, standardfyllningsfärg för widget, knappfyllningsfärg, fyllningsfärg för textwidget, fönsterfyllningsfärg och flera andra standardfärgvärden. Dessutom stöder **GX_WINDOW** visning av en bitmapp eller skrivbordsunderlägg när fönsterklienten fylls.

Den enklaste metoden för att ändra standardfärgschemat är att använda GUIX Studio och skapa eller definiera ett färgschema som uppfyller dina krav.
Du kan också definiera färgschemat manuellt genom att skapa en matris med GX_COLOR och anropa API gx_system_color_table_set funktion.

### <a name="event-notification"></a>Händelseavisering 

GUIX-händelser är begäranden som görs till en eller flera widgetar för att utföra en viss åtgärd och meddelanden för att meddela widgetar om användarindata och interna systemstatusändringar. När en widget till exempel får fokus skickas **GX_EVENT_FOCUS_GAINED** till widgeten via ***API gx_system_event_send tjänsten.***

Händelser skickas via GUIX-händelsekön och varje händelse är en instans av den **GX_EVENT** datastrukturen. Den **GX_EVENT** datastrukturen definieras ***i gx_api.h***, men de viktigaste fälten i strukturen är **gx_event_type**, **gx_event_sender**, **gx_event_target** **och gx_event_payload**.

Fältet **gx_event_type** används för att identifiera den specifika händelseklassen. Händelsetypen anger om detta till exempel är en **GX_EVENT_PEN_DOWN** händelse eller en **GX_EVENT_TIMER** händelse. Den **gx_event_payload** är en union av olika datafält och alla är inte giltiga för varje händelsetyp.
Du använder fältet händelsetyp först innan du undersöker de andra fälten för händelsedata.

Fältet **gx_event_sender** innehåller ID:t för widgeten som genererade händelsen om händelsen är ett meddelande för underordnad widget.

Fältet **gx_event_target** kan användas för att dirigera användardefinierade händelser till ett visst fönster eller en viss widget. Om du vill skicka en händelse till ett visst fönster bör du ge fönstret ett unikt ID-värde (så att det kan identifieras positivt) och när du skapar händelsen placerar du fönster-ID-värdet **i gx_event_target fältet.** Om du inte känner till mål-ID:t eller om du bara vill att händelsen ska dirigeras till widgeten som har indatafokus ska du ange **gx_event_target** fältet till 0.

Slutligen är **gx_event_payload** en union av olika datatyper. För **GX_EVENT_PEN_DOWN** och **GX_EVENT_PEN_UP** händelser **innehåller gx_event_pointdata** fältet x,y pixelkoordinaten pennpositionen. För timerhändelser innehåller **fältet gx_event_timer_id** ID för den utgångna timern. Andra nyttolastdatafält används för andra händelsetyper. Den fullständiga listan över fördefinierade händelsetyper och deras nyttolastfält definieras i [bilaga E – GUIX-händelsebeskrivningar](appendix-e.md).

Programmet kan också lägga till egna anpassade händelser, som startar numeriskt efter konstanten **GX_FIRST_APP_EVENT**. Alla händelsenummer efter den här konstanten är reserverade för programmets användning. Naturligtvis måste programmets widget-händelsehanterare ha bearbetning för sådana programhändelser.

### <a name="event-processing"></a>Händelsebearbetning 

Det finns en standardfunktion för händelsebearbetning av widgetar för varje widget med ***gx_<av widgettyp>_event_process***. I de flesta fall behöver programmet inte bekymra sig om händelsehanteringen för en viss widget. Men i situationer där programmet kräver anpassad eller kompletterande händelsebearbetning kan programmet åsidosätta standardbearbetningsfunktionen med en egen via GUIX ***API-gx_widget_event_process_set***. Den här funktionen åsidosätter standardfunktionen för händelsebearbetning med funktionen för händelsefunktionsbearbetning angiven i API:et.

> [!IMPORTANT]
> Funktioner för programhändelsebearbetning kan dra nytta av (d.v.s. inte duplicera bearbetningen) av standardbearbetningen genom ***att helt enkelt anropa gx_widget_event_process*** bearbetningen direkt.

Händelsebearbetning anropas exklusivt från kontexten för den interna GUIX-systemtråden. På så sätt gäller stackkraven för att bearbeta händelsehanteringen endast FÖR GUIX-tråden.

### <a name="implementing-custom-event-processing-example"></a>Implementera anpassad händelsebearbetning (exempel) 

Du kan ange en egen händelsebearbetningsfunktion för en widget eller ett fönster i GUIX-systemet. Om du skapar en egen anpassad widgettyp installerar du normalt din anpassade händelsehanterare i funktionen för widgetskapande. Om du bara utökar eller ändrar driften av en befintlig widget eller ett fönster kan du anropa API gx_widget_event_process_set-funktionen efter att widgeten eller fönstret har skapats. Du kommer nästan alltid att tillhandahålla din egen händelsehantering för dina toppnivåfönster (kallas även skärmar) för att bearbeta händelser som genereras av dina underordnade kontroller. Bearbetningshändelse som genereras av underordnade kontroller på en skärm är det huvudsakliga sättet att lägga till funktioner i GUIX-programmet.

Anta till exempel att du definierar en skärm på den översta nivån med namnet "main_menu".
Den här skärmen kan definieras med hjälp av GUIX Studio, eller så kan du skapa den här skärmen i programkoden. Om du definierar skärmen i GUIX Studio skriver du helt enkelt namnet på din händelsehanterare i fältet Studio-egenskaper för skärmen så installeras händelsehanteraren automatiskt av den Studio-genererade specifikationskoden. I det här fallet anropar vi den anpassade ***main_menu_event_handler*** och den ska vara kodad så här:

```C
int main_menu_item; /* example: variable to keep track of selected item */

UINT main_menu_event_handler(GX_WINDOW *main_screen, GX_EVENT *event_ptr)
{
    UINT status = GX_SUCCESS;

    switch(event_ptr->gx_event_type)
    {
    /* this is an example for catching events from a child button */
    case GX_SIGNAL(IDB_CHILD_BUTTON, GX_EVENT_CLICKED):
        /* insert your button handler code here */
        break;

    case GX_EVENT_SHOW:
        /* add functionality to the show event handler */
        /* first, do default processing */
        status = gx_window_event_process(main_screen, event_ptr); /* note 1 */

        /* now add my own processing */
        main_menu_item = 0;
        break;

    default:
        /* pass all other events to base processing function */
        status = gx_window_event_process(main_screen, event_ptr); /* note 1 */
        break;
    }
    return status;
}
```

I exemplet ovan är det viktigt att observera att för systemhändelser som **GX_EVENT_SHOW** (händelser som genereras internt för att meddela en widget om en statusändring) måste programmet skicka dessa händelser till funktionen för händelsebearbetning av baswidgeten för att säkerställa att den normala bearbetningen sker. Programmet kan sedan lägga till ytterligare logik efter behov. Alla händelser som inte hanteras av programmet (standardfallet ovan) ska också skickas till funktionen för bashändelsebearbetning. Eftersom det här exemplet var för en toppnivåskärm **baserad GX_WINDOW** är standardfunktionen för händelsebearbetning gx_window_event_process.

### <a name="drawing-function"></a>Ritningsfunktion 

All widgetritning utförs separat från händelsehanteringen. Detta är mer effektivt eftersom ritningen vanligtvis är dyr när det gäller CPU-cykler. Genom att implementera en algoritm för uppskjuten ritning kan alla utestående händelser och associerade visningsändringar slutföras innan en ritning görs, vilket eliminerar slöseri med ritningen. På liknande sätt som vid händelsebearbetning finns det en standardfunktion för widgetritning för de flesta widgetar med ***gx_<av widgettyp>_draw***, där xxx är widgettypen. I de flesta fall behöver programmet inte bekymra sig om ritningsfunktionen för en viss widget. Men i situationer där programmet kräver anpassad eller kompletterande ritning kan programmet åsidosätta standardritningsfunktionen med en egen via GUIX ***API-gx_widget_draw_set***. Den här funktionen gör att programmet kan tillhandahålla en egen anpassad ritningsfunktion för alla widgetar. Detta gör det möjligt för programmet att definiera hela nya widgettyper.

> [!IMPORTANT]
> Programritningsfunktioner kan dra nytta av (d.v.s. inte duplicera kodningen) för standardritningen genom att helt enkelt anropa den direkt från den åsidosättda ritningsfunktionen.

Widgetritning kallas exklusivt för den interna GUIX-systemtråden. På så sätt gäller tidsinställning och stackkrav för att utföra ritningen endast för GUIX-tråden.

### <a name="implementing-custom-drawing-example"></a>Implementera anpassad ritning (exempel) 

Ritningsfunktionen för en widget refereras via en indirekt funktionspekare som är medlem i GX_WIDGET kontrollblocket. Om du använder GUIX Studio för att definiera widgeten kan du installera en egen funktionspekare genom att skriva namnet på funktionen i parametern "Ritningsfunktion" i widgetegenskaperna så installerar Studio funktionspekaren åt dig när widgeten skapas. Om du skapar widgeten i programkoden måste du använda ***API gx_widget_draw_set funktionen*** för att installera din anpassade ritningsfunktion när widgeten har skapats.

I det här exemplet antar vi att du vill anpassa utseendet på en knapp. Knappen ser ut ungefär som en **GX_TEXT_BUTTON**, men vi kommer att lägga till en liten grön "LED_ON"-bitmapp i mitten till höger på knappen när knappen trycks ned och liten "LED_OFF"-knapp när knappen inte trycks ned. Vi vill skapa en knapp som ser ut som bilderna nedan.

![Skärmbild av den gröna knappen för På.](./media/guix/image4.jpg) anpassad knapp "på"

![Skärmbild av den röda knappen för Av.](./media/guix/image5.jpg) anpassad knapp "av"

I det här fallet skulle vi skriva en funktion för knappritning som ser ut ungefär så här.

```C
UINT my_button_draw(GX_TEXT_BUTTON *button)
{
    GX_PIXELMAP *map;
    ULONG button_style;
    INT xpos;
    INT ypos;

    /* first, do the normal text button drawing */
    gx_text_button_draw(button);

    /* now add our extra pixelmap */

    gx_widget_style_get(button, &button_style);

    if (button_style & GX_STYLE_BUTTON_PUSHED)
    {
        /* use the ON pixelmap */
        gx_context_pixelmap_get(GX_PIXELMAP_ID_LED_ON, &map);
    }
    else
    {
        /* use the OFF pixelmap */
        gx_context_pixelmap_get(GX_PIXELMAP_ID_LED_OFF, &map);
    }
    if (map)
    {
        /* draw it 20 pixels in from right edge */
        xpos = button->gx_widget_size.gx_rectangle_right;
        xpos -= map->gx_pixelmap_width + 20;

        /* and draw 10 pixels from the top edge */
        ypos = button->gx_widget_size.gx_rectangle_top + 10;

        /* draw the extra pixelmap on top of the button */
        gx_canvas_pixelmap_draw(xpos, ypos, map);
    }
}
```

## <a name="guix-drawing-context-component"></a>Komponent för GUIX-ritningskontext 

Ritningskontexten skapas dynamiskt vid körning, eftersom GUIX utför varje uppdateringsåtgärd för arbetsytan. Ritningskontexten kopplar samman arbetsytan, skärmdrivrutinen och penseln som används för att utföra de aktuella ritningsåtgärder.

Ritningskontexten definieras av **GX_DRAW_CONTEXT** struktur.
Den här strukturen innehåller variabler som definierar urklipp och vy för den aktuella ritningsåtgärden, definierar den aktuella arbetsytan och definierar den aktuella skärmdrivrutinen som används. Den **GX_DRAW_CONTEXT** strukturen innehåller även penseln som används för ritning. Penseln för ritarkontext är den medlem som du arbetar direkt med i dina anpassade ritningsfunktioner. Penselstrukturen definieras enligt koden nedan.

```C
typedef struct GX_BRUSH_STRUCT
{
    GX_PIXELMAP *gx_brush_pixelmap;
    GX_FONT     *gx_brush_font;
    ULONG        gx_brush_line_pattern;
    ULONG        gx_brush_pattern_mask;
    GX_COLOR     gx_brush_fill_color;  
    GX_COLOR     gx_brush_line_color;  
    UINT         gx_brush_style;
    GX_VALUE     gx_brush_width;
    UCHAR        gx_brush_alpha;  
} GX_BRUSH;
```

Fältet **gx_brush_pixelmap** definierar en pixelkarta som ska användas för rektangel- och polygonfyllningar. Den här medlemmen används inte om **inte gx_brush_style** är innehåller **GX_BRUSH_PIXELMAP** format.

Den **gx_brush_font definierar** teckensnittet som används för textritning.
Den **gx_brush_line_pattern medlemmen** definierar mönstret som används för streckade linjer.
Den **gx_brush_style** är en uppsättning formatflaggor som kan vara ELLER tillsammans för att fullständigt definiera penselattributen. Tillgängliga flaggor för penselformat innehåller följande.

**GX_BRUSH_OUTLINE**  
**GX_BRUSH_SOLID_FILL**  
**GX_BRUSH_PIXELMAP_FILL**  
**GX_BRUSH_ALIAS**  
**GX_BRUSH_UNDERLINE**  
**GX_BRUSH_ROUND**

Den **gx_brush_width** medlemmen definierar linjen med för linjeritning eller konturbredden för konturritning.

Den **gx_brush_line_color-medlemmen** definierar förgrundsfärgen för linjeritning och för textritning.

Den **gx_brush_fill_color medlemmen** definierar den heldragna fyllningsfärgen som används för formfyllning. GUIX-kontextkomponenten innehåller en uppsättning API:er som är utformade för att göra det mycket enkelt att ändra den aktuella penseln i den aktiva kontexten. Dessa API:er **gx_context_brush_define**, **gx_context_line_color_set**, **gx_context_fill_color_set**, **gx_context_font_set** och många andra.

Rita kontexten för ett överordnat objekt ärvs av underordnade objekt. I själva verket ärvs en klon av den överordnade ritningskontexten av de underordnade objekten när deras ritningsfunktioner anropas. Den underordnade kan ändra kontexten utan att den överordnade ritningen påverkas, men den kan också ärva information från den överordnade, till exempel penselfärg och stil om så önskas.

## <a name="guix-window-component"></a>GUIX-fönsterkomponent 

Fönsterkomponenten ansvarar för all fönsterbearbetning i GUIX. Ett GUIX-fönster är i grunden ett distinkt visningsområde som kan innehålla en eller flera underordnade widgetar. I GUIX är fönstret egentligen bara en särskild form av det grundläggande widgetobjektet.

GUIX-fönster implementeras på ett objektorienterat sätt med fullständigt stöd för arv. Detta åstadkoms med ansi C, vilket resulterar i minsta möjliga minne och bearbetningskrav.

GUIX-fönster utökar funktionerna i GUIX-widgeten främst genom att lägga till stöd för vågrät och lodrät rullning. GUIX-fönsterobjekt kan automatiskt skapa och visa rullningslister och svara på rullningslistsinmatning. Flyttbara fönster har också inbyggd händelsehantering som gör att fönstret kan flyttas eller dras baserat på pennindatahändelser.
Slutligen svarar GUIX-fönstret på att få indatafokus genom att flytta fönstret längst fram i Z-ordningen.

GUIX-fönstret underhåller begreppet klientområde *,* som är den inre delen av fönstret när fönstret kantlinjer och icke-klientobjekt som rullningslisterna tas bort från det tillgängliga området. Underordnade widgetar i klientområdet klipps till fönstrets klientområde, medan underordnade rullningslister som rullningslister tillåts rita utanför klientområdet, men de är fortfarande urklippta i fönstrets yttre dimensioner.

Windows underhålls på ett överordnat-underordnat sätt, där underordnade objekt ärver egenskaper från sina överordnade. Underordnade fönster kan ha egna underordnade fönster som återigen ärver olika egenskaper från det överordnade fönstret. Egenskaperna för alla fönster kan uttryckligen omdefinieras via olika GUIX API-anrop.

### <a name="window-creation"></a>Skapa fönster 

Ett fönsterobjekt kan skapas under initieringen eller när som helst under körningen av programtrådar. Det finns ingen gräns för hur många fönsterobjekt som kan skapas av ett program. Det finns heller ingen gräns för hur många underordnade underfönster som helst.

### <a name="window-control-block"></a>Fönsterkontrollblock 

Egenskaperna för varje fönsterobjekt finns i dess kontrollblock **och GX_WINDOW** definieras i **_gx_api.h_**. Det minne som krävs för ett fönsterobjekt tillhandahålls av programmet och kan finnas var som helst i minnet. Det är dock vanligast att göra så att kontrollen av fönsterobjekt blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="root-window"></a>Rotfönster 

GUIX kräver vad som kallas ett rotfönster för varje arbetsyta. Rotfönstret är kantlöst och har samma dimensioner som arbetsytan som det är kopplat till. Den används främst som en container för alla widgetar och fönster på första nivån. Rotfönstret skapas vanligtvis av programmet via API-funktionen ***gx_window_root_create***, strax efter att skärmen och arbetsytan har skapats. Om du använder den Studio-genererade gx_studio_display_configure kan adressen till rotfönstret returneras på den plats som skickades som den sista parametern till den här funktionen.

Ett rotfönster är som standard oflyttningsbart, och i det enklaste fallet är rotfönstret arbetsytans storlek. Rotfönstret ritar i praktiken visningsbakgrunden, så om du vill ändra visningsbakgrundsfärgen eller visa bakgrundsbakgrunden tilldelar du en färg eller bakgrundsbild till rotfönstret.

Om ett rotfönster kan flyttas flyttas det inte genom att ändra dess position på arbetsytan som ett underfönster, utan genom att flytta själva arbetsytan.
Med den här funktionen kan GUIX-rotfönstret utnyttja maskinvara som stöder flera bildrutebuffertar med maskinvaruförskjutningsregister.

### <a name="background"></a>Bakgrund 

Fönsterbakgrunder är antingen solida färger eller bitmappbilder. Det finns en standardfönsterbakgrund på systemnivå som tillhandahåller standardvärdet för den första uppsättningen fönster. Naturligtvis kan alla fönsterbakgrunder ändras via GUIX-API:et.

Om du vill ändra bakgrundsfärgen i ett fönster använder du ***gx_widget_fill_color_set*** API. Om du vill tilldela ett bakgrundsunderlägg till ett fönster använder du ***gx_window_wallpaper_set*** API.

### <a name="scrolling"></a>Rullning 

GUIX stöder standardfönsterrullning när det krävs ett område för att visa fönster underordnade överskrider den aktuella storleken på fönstret – vågrätt och/eller lodrätt. Om du vill aktivera rullning måste programmet skapa önskade rullningslister och koppla dem till fönstret.

GUIX-fönsterkomponenten tillhandahåller en standardimplementering av rullning baserat på storleken på fönstrets klientområde och omfattningen för alla underordnade widgetar. Program kan också tillhandahålla sin egen rullningsimplementering och tolkning genom ***att åsidosätta gx_window_scroll_info_get*** för ett visst fönster.

### <a name="event-notification"></a>Händelsemeddelande 

Standardfunktionen för händelsebearbetning i fönstret skiljer sig från GX_WIDGET händelsebearbetningen främst i hanteringen av bläddrings- och storleksändringshändelser. GX_WINDOW defalt-hanterare för bläddring och storleksändring av händelser.

Programmet kan också lägga till egna anpassade händelser, som startar numeriskt efter **konstanten GX_FIRST_APP_EVENT**. Alla händelsenummer efter den här konstanten är reserverade för programmets användning. Naturligtvis måste programmets fönsterhändelsehanterare ha bearbetning för sådana programhändelser.

### <a name="event-processing"></a>Händelsebearbetning 

Precis som alla andra widgettyper finns det en standardfunktion för bearbetning av fönsterhändelse för varje fönster med ***namnet gx_window_event_process***. Du åsidosätter vanligtvis den här händelsehanteringsfunktionen med din egen händelsehanterare i de fönster som du skapar. På så sätt svarar du på händelser och vidta åtgärder baserat på händelser som genereras av de underordnade kontrollerna i fönstret.

Det är viktigt att komma ihåg att anropa ***bas-gx_window_event_process-funktionen*** för GUIX-systemhändelser om du åsidosätter den händelsehanteraren, så att standardhändelsehanteringen kan ske utöver den åtgärd som du lägger till i händelsehanteraren. Om du till exempel anger en anpassad hanterare **för GX_EVENT_SHOW händelsen** och inte skickar den här händelsen till ***gx_window_event_process*** visas aldrig ditt fönster.
Om du vill ange en anpassad händelsehanterare för ett ***fönster använder gx_widget_event_process_set*** för att definiera adressen för händelsehanteraren. Den här funktionen åsidosätter standardfunktionen för händelsebearbetning med funktionen för bearbetning av händelsefunktioner angiven i API:et.

> [!IMPORTANT]
> Funktioner för programhändelsebearbetning kan dra nytta av (d.v.s. inte duplicera bearbetningen) av standardbearbetningen genom ***att helt enkelt anropa gx_window_event_process direkt.***

Händelsebearbetning anropas exklusivt från kontexten för den interna GUIX-systemtråden. På så sätt gäller stackkraven för att bearbeta händelsehanteringen endast GUIX-tråden.

## <a name="guix-image-reader-component"></a>Komponent för GUIX-bildläsare 

Komponenten för bildläsare innehåller verktyg och API-funktioner för att dekomprimera komprimerade raw-bilder till GUIX pixelmap-format. Rådata för JPEG- och PNG-format stöds, med ytterligare format som är reserverade för framtida versioner.

Observera att för de allra flesta GUIX-program krävs inte komponenten GUIX Image Reader. De flesta program förlitar sig på GUIX Studio-programmet för att konvertera grafiktillgångar i JPEG- och PNG-format **till GUIX-kompatibla GX_PIXELMAP** resurser. KOMPONENTEN GUIX-bildläsare används när grafiktillgångarna i rådata endast är kända vid körning, eller när systemlagringsbegränsningarna förhindrar lagring av resurser **i GX_PIXELMAP** format. Bilddata i JPEG- och PNG-format är vanligtvis mer kompakta än **GX_PIXELMAP-format,** men det finns betydande körningskostnader för att utföra dekomprimering och konvertering av färgutrymme för dessa bildtyper dynamiskt.

Om JPEG- eller PNG-bilder i raw-format skickas gx_canvas_pixelmap_draw API-funktionen dekomprimerar GUIX dynamiskt och ritar JPEG- eller PNG-data. Observera att detta har en betydande negativ inverkan på körningshastigheten och att skicka RAW-formatbilddata till gx_canvas_pixelmap_draw-funktionen rekommenderas inte om du inte använder ett maskinvarumål som stöder maskinvarustödd JPEG- eller PNG-dekomprimering.

> [!IMPORTANT]
> Att skicka rå JPEG- eller PNG-formaterade bilder till gx_canvas_pixelmap_draw API medför betydande körningskostnader för merparten av målmaskinvaran.

Alternativt kan råa JPEG- och PNG-data konverteras till GX_PIXELMAP-format vid körning med hjälp av komponenten Bildläsare.
Pixelkartor som skapas på det här sättet kan användas och ritas precis som pixelkartor som skapas av Studio och som finns i din resursfil. På så sätt kan ditt program utföra bilddekomprimering, dithering och konvertering av färgutrymme en gång (vanligtvis vid programstart) i stället för att utföra dessa åtgärder varje gång bilden ritas.

Komponentfunktionerna för bildläsare omfattar:

***gx_image_reader_create***  
***gx_image_reader_palette_set***  
***gx_image_reader_start***

## <a name="guix-animation-component"></a>Komponent för GUIX-animering 

Komponenten GUIX-animering är en uppsättning funktioner och tjänster som används för att automatisera automatisering av skärm- och widgetövergångar. Komponenten GUIX-animering har stöd för att tona in, tona ut och flytta eller dra av animeringar av valfri widgettyp.

Animeringar av toningstyp kan stödjas antingen genom att variera det interna alfavärdet för toningswidgeten (om **GX_BRUSH_ALPHA_SUPPORT** är aktiverat) eller genom att rita någon samling widgetar till en separat minnesarbetsyta när den sedan blandas med bakgrunden. För maskinvarumål som stöder flera maskinvarugrafikskikt uppnås bäst stöd för jämna avfasningseffekter med den här metoden för att blanda arbetsyta, ofta med mycket lite processorbandbredd som krävs. För maskinvarumål som inte har stöd för flera grafiklager stöds blending med hjälp av ALFA-värdet för GUIX-pensel vid körning med 16 bpp och högre färgdjup.

Om en animering ska använda en separat arbetsyta tillhandahåller KOMPONENTEN GUIX-animering API-gx_animation_canvas_define för detta ändamål. Andra animeringstyper kräver inte en separat arbetsyta, men de använder den om den är tillgänglig. På så sätt får du bästa möjliga användning av underliggande maskinvarustöd för flera maskinvaruytor.

Variablerna som styr en animering definieras av två kontrollblock. Först definierar **GX_ANIMATION** som definierar animeringskontrollanten. Animeringskontrollanten är den motor som kör animeringssekvensen som du definierar. En enda animeringskontrollant kan användas flera gånger för att köra många olika animeringssekvenser. Om du behöver köra flera animeringssekvenser samtidigt  kan du skapa flera GX_ANIMATION animeringskontrollanter.

GUIX-systemkomponenten kan tillhandahålla ett återanvändargränssnittsblock **med GX_ANIMATION-kontrollstrukturer** som kan begäras av programmet när och animering behövs och som automatiskt returneras till systempoolen när animeringssekvensen har slutförts. Detta frigör programmet från att statiskt definiera en **GX_ANIMATION** struktur för varje animering som kan implementeras. Storleken på den här **poolen med GX_ANIMATION-strukturer** definieras av konstanten **GX_ANIMATION_POOL_SIZE**, som standard är 6, vilket innebär att som standard kan 6 samtidiga animeringar allokeras från systempoolen. Den här konstanten kan naturligtvis omdefinieras i gx_user.h-huvudfilen är mer samtidiga animeringar krävs. Om **GX_ANIMATION_POOL_SIZE** har angetts till noll tillhandahåller inte GUIX-systemkomponenten någon animeringspool eller relaterade tjänster.

Det andra kontrollblocket eller strukturen som används för att definiera en animering är **GX_ANIMATION_INFO** struktur. Den här strukturen används för att definiera en viss animeringssekvens. Du skickar den här informationsstrukturen till animeringskontrollanten för att initiera en animeringssekvens med hjälp gx_animation_start API-tjänsten. Den **GX_ANIMATION_INFO** strukturen innehåller följande fält:

```C
typedef struct GX_ANIMATION_INFO_STRUCT
{
    GX_WIDGET *gx_animation_target;
    GX_WIDGET *gx_animation_parent;
    GX_WIDGET *gx_animation_screen_list;
    USHORT gx_animation_style;
    USHORT gx_animation_id;
    USHORT gx_animation_start_delay;
    USHORT gx_animation_frame_interval;
    GX_POINT gx_animation_start_position;
    GX_POINT gx_animation_end_position;
    GX_UBYTE gx_animation_start_alpha;
    GX_UBYTE gx_animation_end_alpha;
    GX_UBYTE gx_animation_steps;
} GX_ANIMATION_INFO;
```

Den **gx_animation_target medlemmen** definierar målwidgeten som animeringskontrollanten kommer att agera på.

Den **gx_animation_parent** medlemmen definierar den överordnade widgeten, om en eventuell, som målwidgeten ska kopplas till när animeringssekvensen är klar. Den gx_animation_parent är också mottagare av GX_ANIMATION_COMPLETE händelse som genereras när en animering har slutförts.

Den **gx_animation_screen_list** definierar en widgetlista för penndrivna animeringar av skärmbild. Widge-listan bör avslutas med GX_NULL pekare och varje widget i listan bör ha samma x,y-dimensioner som gx_animation_parent.

Den **gx_animation_style** är en bitmask som definierar vilken typ av animering som ska utföras och associerade alternativ. Flaggor för animeringsstil inkluderar följande.

| Flagga &nbsp; för &nbsp; animeringsstil | Beskrivning |
| --- | --- |
| GX_ANIMATION_TRANSLATE | Begär animering av en bild- eller toningstyp. |
| GX_ANIMATION_SCREEN_DRAG | Begära en penndriven skärm dra animering. |

Följande flaggor kan användas i kombination med **SCREEN_DRAG** animeringar.

| Dra &nbsp; &nbsp; flaggor på skärmen | Beskrivning |
| --- | --- |
| GX_ANIMATION_WRAP | Skärmlistan bör omsluta från end back till start. |
| GX_ANIMATION_HORIZONTAL | Skärm dra tillåts i vågrät riktning.  |
| GX_ANIMATION_VERTICAL | Skärm dra tillåts i lodrät riktning. |

Följande flagga kan användas i kombination med översätt animeringar.

| Översätta &nbsp; animeringar &nbsp; flaggor | Beskrivning |
| --- | --- |
| GX_ANIMATION_DETACH | Koppla från animeringsmålet från animeringen som är överordnat när animeringen har slutförts. Om målet dynamiskt allokerades och skapades av GUIX Studio-genererad automatiserad händelsehantering tas målet bort när det har frånkopplades. |
| GX_ANIMATION_TRANSLATE | Animeringstyper är timerdrivna animeringar. Programmet definierar start- och slutpositionen och start- och slut alfavärdet för målwidgeten, och animeringshanteraren skapar en timer för att fungera och som drivande kraft för att köra animeringen.
| GX_ANIMATION_SCREEN_DRAG | Skiljer sig  från TRANSLATE-animeringarna på så sätt att den här animeringstypen drivs av penninmatningshändelser. Den här animeringstypen spårar tillsammans med pekskärmens indata för att svepa målwidgeten när användaren drar en penna eller snodd över indatans pekskärm. Om du vill använda den här typen av animering ska programmet anropa **_gx_animation_drag_enable_** API för att aktivera den här animeringen. |

Värdet **gx_animation_id** skickas tillbaka till animeringens överordnade i event.gx_event_sender i **GX_ANIMATION_COMPLETE** händelse. Det här värdet används av animeringens överordnade för att avgöra vilken av eventuellt flera underordnade animeringar som rapporterar slutförande. Det här värdet kan vara 0, och en animering med ID-värde 0 genererar **inte ANIMATION_COMPLETE** händelse alls.

Det **gx_animation_start_delay** värdet är ett GUIX-tidsvärde som anger hur många timer tick som ska fördröjas efter att gx_animation_start _ anropas innan animeringen ***faktiskt körs. Värdet kan vara 0 för att starta animeringen omedelbart när den anropar _*_gx_animation_start_**.

Fältet **gx_animation_frame_interval** definierar antalet GUIX-timers tick (en multipel av den underliggande OS-tickfrekvensen) för att fördröja mellan varje bildruta i animeringssekvensen. Det minsta värdet är 1.

I **gx_animation_start_position definieras** startpunkten längst upp till vänster för målwidgeten för översättningsanimeringar.

Den **gx_animation_end_position definierar** slutpositionen längst upp till vänster för målwidgeten för animeringar av översättningstyp.

Fältet **gx_animation_start_alpha** definierar det första alfavärdet för arbetsytan för animeringar av översättningstyp.

Fältet **gx_animation_end_alpha definierar** det sista alfavärdet för arbetsytan för animeringar av översättningstyp.

Fältet **gx_animation_steps** definierar hur många steg eller ramar kontrollanten ska köra för översättningsanimeringar. Ett större antal steg ger ett jämnare utseende och/eller toning, men kräver också större systembandbredd.

Om du vill implementera animeringseffekter i ditt program måste du först ***anropa gx_animation_create för*** att initiera animeringskontrollanten. Om animeringen ska använda en sekundär arbetsyta initierar du den här arbetsytan genom att anropa gx_animation_canvas_define. Därefter ska du initiera GX_ANIMATION_INFO **för att** definiera den specifika typen av animering som ska utföras och de andra animeringsparametrarna. Anropa slutligen gx_animation_start för att utlösa animeringssekvensen.

När animeringskontrollanten har slutfört en animeringssekvens skickar den en **GX_ANIMATION_COMPLETE-händelse** till den överordnade widgeten, vilket gör att du kan rensa animeringens arbetsyta vid den tidpunkten.

## <a name="guix-utility-component"></a>GUIX-verktygskomponent 

Verktygskomponenten ansvarar för alla vanliga verktygsfunktioner i GUIX. Det här är vanliga funktioner som är användbara verktyg och som kan anropas var som helst i programmet eller den interna GUIX-koden. Verktygskomponentens funktioner omfattar följande.

***gx_utility_canvas_to_bmp***

***gx_utility_circle_point_get***

***gx_utility_alphamap_create***

***gx_utility_gradient_create***

***gx_utility_gradient_delete***

***gx_utlity_ltoa***

***gx_utility_math_acos***

***gx_utility_math_asin***

***gx_utility_math_cos***

***gx_utility_math_sin***

***gx_utility_math_sqrt***

***gx_utility_pixelmap_resize***

***gx_utility_pixelmap_rotate***

***gx_utility_pixelmap_simple_rotate***

***gx_utility_rectangle_center***

***gx_utility_rectangle_center_find***

***gx_utility_rectangle_combine***

***gx_utility_rectangle_compare***

***gx_utility_rectangle_define***

***gx_utility_rectangle_overlap_detect***

***gx_utility_rectangle_point_detect***

***gx_utility_rectangle_resize***

***gx_utility_rectangle_shift***

***gx_utility_string_to_alphamap***
