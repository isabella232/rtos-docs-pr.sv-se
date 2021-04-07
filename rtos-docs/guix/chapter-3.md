---
title: Kapitel 3 – funktionell översikt över GUIX
description: Det här kapitlet innehåller en funktionell översikt över produkten GUIX User Interface med hög prestanda.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 53ffc900debd3bfaa1a38d792ddf294b2ce92461
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550311"
---
# <a name="chapter-3---functional-overview-of-guix"></a>Kapitel 3 – funktionell översikt över GUIX

Det här kapitlet innehåller en funktionell översikt över produkten GUIX User Interface med hög prestanda. 

## <a name="execution-overview"></a>Översikt över körning

GUIX implementerar en händelse driven programmerings modell. Det innebär att GUIX-ramverket främst styrs av mottagandet av händelser i händelse kön för GUIX. Bearbetningen av dessa händelser sker i kontexten för GUIX-tråden, som är en ThreadX-tråd som skapas under system initieringen av GUIX.

GUIX-program definierar användar gränssnittet genom att anropa GUIX API-funktioner för att skapa Windows och underordnade widgetar och anpassa utseendet på dessa widgetar genom att anropa ytterligare API-funktioner som används för att definiera färger, format, teckensnitt och olika attribut för varje fönster eller widget. Om du använder GUIX Studio för att skapa utseendet på dina användar gränssnitts skärmar, är det mycket av det här arbetet med att anropa GUIX API-funktioner för att skapa din visning som du gör av GUIX Studio-programmet.

GUIX-program interagerar med system användaren och med en extern affärs logik genom att hantera händelser som hämtats från händelse kön GUIX.
Dessa händelser skapas vanligt vis av GUIX-widgetar, men de kan också skapas av externa trådar. När en typisk GUIX-knapp skickas skickar den här knappen en händelse till knappens överordnade fönster. Ditt program kommer att agera på knappen push genom att tillhandahålla en hanterare för knapp-push-händelsen.

Ytterligare GUIX-trådar skapas ofta för sådant som indatamängds driv rutiner. En typisk driv rutin för touch-indatamängden körs som en fristående tråd utanför den huvudsakliga GUIX-tråden. Driv rutinen för touch-indata skickar touch-information till GUIX-tråden genom att skicka händelser till händelse kön för GUIX.

Eftersom många användar gränssnitts åtgärder, t. ex. animeringar kräver korrekt tids information, implementerar GUIX också ett enkelt och lätt att använda timer-gränssnittet. Detta timer-gränssnitt skapas på ThreadX timer-tjänsten och konfigureras automatiskt vid system start.

Den stora delen av GUIX-programvaran är oberoende av eventuella maskin varu beroenden. Ramverket kräver maskinvarubaserade indrivmedel och maskinvarubaserade grafik driv rutiner. Information om hur dessa maskinvaruspecifika driv rutiner implementeras härleds till kapitel 5.

## <a name="initialization"></a>Initiering 

Tjänst ***gx_system_initialize*** måste anropas innan någon annan GUIX-tjänst anropas. GUIX system initiering kan anropas från ThreadX ***tx_application_define*** rutinen (initierings kontext) eller från program trådar. Funktionen ***gx_system_initialize*** skapar händelse kön GUIX, initierar GUIX timer, skapar den huvudsakliga GUIX system-tråden och initierar olika data strukturer som underhålls av GUIX under körningen av ditt program.

När ***gx_system_initialize*** har returnerat är programmet redo att skapa skärmar, arbets ytor, Windows, widgetar och anpassa egenskaperna för alla GUIX-objekt. Många av GUIX-API: et för att skapa objekt kan anropas från ***tx_application_define*** eller från program trådar.

## <a name="application-interface-calls"></a>Program gränssnitts anrop 

Anrop från programmet görs i stort sett från ***tx_application_define*** (initierings kontext) eller från program trådar. Se avsnittet "tillåten från" i varje GUIX-API som beskrivs i kapitel 4 för att avgöra vilken kontext det kan anropas från.

För det mesta är bearbetningen av intensiva aktiviteter härledd till den interna GUIX-tråden, inklusive alla ritningar för händelse bearbetning och widget/fönster.

GUIX API-funktioner kan anropas från alla trådar när som helst.
Det anses dock vanligt vis vara bättre arkitektur för att skilja din tids kritiska affärs logik från användar gränssnitts logiken. Eftersom rit åtgärder för användar gränssnittet ibland kan ta lång tid beroende på din visnings storlek och CPU-prestanda skulle du normalt inte behöva ha tids kritiska trådar fördröjda i väntan på att en rit åtgärd ska slutföras.

## <a name="internal-guix-thread"></a>Intern GUIX-tråd 

Som nämnts har GUIX en intern tråd som utför Mass bearbetningen av GUI. Den här tråden skapas av program varan genom att anropa ***gx_system_initialize** _ följt av _ *_gx_system_start_* *.

Prioriteten för den interna GUIX-tråden bestäms av `#define GX_SYSTEM_THREAD_PRIORITY` . Standardvärdet är 16 (mellan prioritet), men kan ändras genom att ange det här värdet i sidhuvud filen gx_port. h eller gx_user. h. åsidosätter standardvärdet.

GUIX trådens tids sektor definieras på samma sätt som `#define GX_SYSTEM_THREAD_TIMESLICE` , som som standard är värdet 10 MS.

System trådens stack-SIE bestäms av `#define GX_THREAD_STACK_SIZE` , som finns i huvud filen ***gx_port. h*** , men kan också åsidosättas genom att ange det här värdet i filen gx_user. h.

Den interna tråden för GUIX tråd körning består av tre åtgärder.
Först hämtar GUIX händelser från händelse kön GUIX och skickar händelser för bearbetning av GUIX-Fönstren och-widgetarna. Händelser skickas vanligt vis till händelse kön för GUIX med regelbundna timers, indata-enheter som pekskärmar eller tangent bord och av GUIX-widgetar själva när de bearbetar indata från användaren. Efter att alla händelser har bearbetats bestämmer GUIX om en skärm uppdatering behövs, och om så är fallet utförs bearbetningen för att uppdatera visnings grafik data, huvudsakligen genom att anropa rit funktionerna i de fönster och widgetar som har marker ATS som skadade. Slutligen avbryter GUIX GUIX-tråden tills en ny inlogg eller händelser tas emot.

## <a name="event-processing"></a>Händelse bearbetning 

Indata för touch-eller Penn indata bearbetas genom att fastställa det översta fönstret eller widgeten under touch-bildningens pixel position och anropar funktionen för händelse bearbetning i Window/widgeten. Om widgeten förstår Penn inmatade händelser, kommer den att bearbeta händelsen som lämplig för widgeten. Om inte, kommer den översta widgeten att skicka händelsen touch eller Penn indata till widgetens överordnade för bearbetning. Detta pass i händelse av att kedjan fortsätter tills händelsen hanteras eller händelsen kommer till rot fönstret, i vilket fall händelsen ignoreras.

Knapp knappar skickas till det fönster/den widget som har fokus. Status för inGUIX underhålls av komponenten gx_system.

Timer-händelser skickas alltid till fönstret eller widgeten som äger timern för bearbetning.

Internt genererade händelser, t. ex. När knapp klickar på händelser eller värde ändrings händelser för skjutreglaget, skickas alltid till den överordnade för widgeten som genererar händelsen. Om den överordnade inte bearbetar händelsen, så skickas den till kedjan som liknar touch-eller Penn ingångs händelser.

## <a name="drawing"></a>Ritning 

När all händelse bearbetning har slutförts fastställer den interna GUIX-tråden om det behövs någon visnings uppdatering och om så är fallet fungerar lämpliga ritnings funktioner för fönster/widget. När ritningen är klar väntar den interna GUIX-tråden bara på händelse kön vid nästa GUIX-händelse för bearbetning.

GUIX implementerar begreppet *felaktiga områden*, som är områden som måste ritas om för varje widget och arbets yta. En widget kan bara rita till områden som tidigare har marker ATS som skadade. När en widgets ritnings funktion anropas, klipps alla ritnings åtgärder internt till den tidigare definierade ändrings ramen.
Försök att rita utanför området ignoreras.

Widgetar och Windows markerar sig själva som felaktiga genom att anropa API-funktionen ***gx_system_dirty_mark***. Den här funktionen markerar hela widgeten eller fönstret som måste ritas om. En andra funktion, ***gx_system_dirty_partial_add***, kan anropas som ett alternativ till att bara markera en del av ett fönster eller en widget som smutsig.

Den här modellen för att märka widgetar som smutsig och sedan rita om dessa widgetar endast när alla inmatnings händelser har bearbetats kallas *uppskjuten ritning*. GUIX för uppskjutna ritningar och listor över skadade listor är utformad för att förbättra effektiviteten i ritningen. Eftersom rit åtgärder vanligt vis är kostsamma arbetar GUIX hårt för att förhindra onödig ritning.

Ritningen görs till en GUIX- *arbetsyta*. En arbets yta är ett minnes område som är reserverat för grafik data. En arbets yta kan vara direkt länkad till maskin varu Rams bufferten, beroende på system arkitektur och minnes begränsningar. Innan en ritning kan ske måste du först öppna en arbets yta för att rita genom att anropa API-funktionen ***gx_canvas_drawing_initiate*** . Det här API: et förbereder en arbets yta för ritning och upprättat den aktuella *ritnings kontexten*. När GUIX utför en system arbets ytans uppdatering, öppnas arbets ytan för ritning och ritnings kontexten som upprättats innan API: erna för Drawing-nivå anropas. Därför behöver inte widgeten starta ritningen på en arbets yta i ritnings funktionen för widgeten.

Men om ett program vill utföra omedelbar ritning på en arbets yta, utanför flödet av den standardinställda GUIX, måste programmet direkt anropa ***gx_canvas_drawing_initiate*** innan du anropar några andra funktioner i Drawing API och måste anropa ***gx_canvas_drawing_complete*** när den omedelbara ritningen har slutförts.

## <a name="user-input"></a>Användarindata 

GUIX stöder touch screen, Mouse och keyboard-enheter med fördefinierade händelse typer. Ytterligare inmatade enheter kan användas genom att definiera anpassade händelse typer eller genom att mappa den anpassade Indataporten till de fördefinierade händelse typerna.

Åtgärder som är kopplade till dessa enheter översätts till händelser som bearbetas av den interna GUIX-tråden. Program vara för driv rutins nivå som har skrivits för att stödja en pekskärm måste förbereda och skicka till händelse köns händelser för GUIX för Penn-och Penn-och Penn aktiviteter. På samma sätt måste ingångs driv rutinen för tangent bordet skapa händelser för tangenttryckning och viktig information.

## <a name="modal-dialog-execution"></a>Körning av modal dialog ruta 

Den modala dialog körningen avser att presentera ett fönster för användaren som måste stängas på något sätt innan andra GUIX-fönster eller widgetar kan ta emot användarindata. Modala dialog rutor fångar upp alla användarindata medan dialog fönstret visas, oavsett x, y-position för touch-eller mus ingångs händelser.

Modala dialog rutor utlöses av program varan genom att först skapa fönstret på det normala sättet genom att anropa ***gx_window_create*** och sedan anropa API-funktionen GUIX ***gx_window_execute.***

När funktionen ***gx_window_execute*** anropas, anger GUIX en lokal händelse bearbetnings slinga. Funktionen ***gx_window_execute*** återgår inte till anroparen förrän dialog fönstret stängs, antingen genom användarindata eller genom att anropa ***gx_window_close***. Därför är det mycket viktigt att aldrig anropa funktionen ***gx_window_execute*** från någon annan tråd än den interna GUIX-tråden.

## <a name="periodic-processing"></a>Periodisk bearbetning 

För att kunna tillhandahålla visnings effekter, Sprite-animeringar och stöd för program periodiska begär Anden, använder GUIX en ThreadX-timer. Denna enda timer används för att driva alla GUIX-tidsrelaterade behov. Som standard är frekvensen för GUIX intern timer-bearbetningen inställd på 20ms via konstanten **GX_SYSTEM_TIMER_MS**, som definieras i **_gx_api. h_**, om inte konstanten tidigare definierats i gx_port. h-eller gx_user. h-sidhuvudet. Standard frekvensen kan ändras av programmet via ett kompilerings alternativ när du skapar GUIX-biblioteket eller genom att uttryckligen omdefiniera det i ***gx_user. h***.

> [!IMPORTANT]
> Observera att frekvensen för GUIX timer uttrycks i återställnings tider timer-Tick och definieras av konstanten **GX_SYSTEM_TIMER_TICKS**. Värdet för **GX_SYSTEM_TIMER_TICKS** beräknas med **GX_SYSTEM_TIMER_MS** och **TX_TIMER_TICKS_PER_SECOND**. Användaren kan omdefiniera något av dessa värden i ***gx_port. h** _ eller _ *_gx_user. h_** för att justera frekvensen och lösningen för GUIX timer.

## <a name="display-driver"></a>Visa driv rutin 

Bildskärms driv rutiner är ansvariga för att tillhandahålla en uppsättning rit funktioner till kärn GUIX-koden. Implementeringen av var och en av dessa rit funktioner bestäms av driv rutinen och om möjligt kan implementeringen utnyttja stöd för maskin varu acceleration. I allmänhet fungerar ritnings funktionen genom att skriva pixel data till en minnesbuffert, vilket kan vara den fysiska RAM-bufferten eller också kan den vara en sekundär buffert beroende på driv rutins arkitekturen. Många driv rutiner implementerar dubbel buffring med två ramtyper och dessa buffertar växlas genom att aktivera funktionen för buffring av buffert. GUIX anropar dessa funktioner internt vid lämpliga tidpunkter. För minnes begränsade system kan ritnings funktionerna bara skriva till en enda buffert för minnes ramar.

GUIX tillhandahåller standard program varu implementeringar av varje lågnivå ritnings funktion vid varje support färgdjup och format. Dessa funktioner anropas via funktions pekare som behålls i **GX_DISPLAYs** strukturen. När maskinvaruspecifika driv rutiner skapas skriver de normalt över vissa antal av dessa funktions pekare med funktioner som är specifika för mål maskin varan.

En typisk maskin varu bildskärms driv rutin implementeras genom att först skapa standard driv rutinen GUIX för det obligatoriska färg djupet och formatet.
Maskin varu driv rutinen ersätter sedan de funktioner som måste optimeras eller anpassas för den specifika maskin varu implementeringen.

GUIX stöder pixel färg format som sträcker sig från 1 – BPP monokrom till 32-BPP a:r: g:b format. GUIX har också stöd för många variationer i varje bred färg djups kategori, till exempel r:g: b jämfört med b:g: r byte order, packad pixel jämfört med Word-justerade bild punkts format och alfa kanaler. Det finns för närvarande 25 distinkta färg format som stöds, men den här listan växer som maskin varu leverantörer levererar nya variationer.

## <a name="display-memory-architectures"></a>Visa minnes arkitekturer

Olika maskin varu mål och skärmar använder en mängd olika grafik minnes arkitekturer, beroende på minnes begränsningar för mål-och funktions kraven för programmet. Vi kommer att beskriva några av de vanligaste minnes arkitekturerna här med en kort beskrivning av varje.

Modell 1) ingen ramkant, grafik data som lagras i externa GRAM:

![Ingen ramkant, grafik data som lagras i externa GRAM](./media/guix/user-guide/no-frame-buffer.png)

I modellen ovan finns det inget minne för en ramkant i minnet lokalt till processorn. All grafik information lagras i en extern GRAM som ingår i själva visningen. Gränssnittet till den externa utgramen kan vara parallellt eller seriellt. Den här typen av arkitektur är mycket låg kostnad. Det kan dock visa oönskade avrivnings effekter när grafik data uppdateras.

Modell 2) en lokal RAM-buffert:

![En lokal RAM-buffert](./media/guix/user-guide/one-local-frame-buffer.png)

I den här modellen allokeras minne för grafik data från ett slumpmässigt åtkomst minne som är direkt tillgängligt för processorn. Dedikerad maskin vara måste vara tillgänglig för att upprepade gånger skicka grafik data (tillsammans med tids signaler) från det lokala minnet till visningen. Den här modellen skiljer sig från modell 1 i att grafik minnet är ett block av den lokala SRAM eller det DRAM som är tillgängligt för processorn. Detta kan vara samma minne som stack-och programvariablerna är Live.

Modell 3) lokal RAM-buffert + extern GRAM:

![Lokal RAM-buffert + extern GRAM](./media/guix/user-guide/local-frame-buffer-external-gram.png)

Modell 3 är en kombination av de två första. I den här modellen finns det tillräckligt med lokalt minne för att rymma en RAM-buffert. Dessutom tillhandahåller visnings enheten en extern GRAM och uppdateras automatiskt med hjälp av de data som anges i GRAM. Den här arkitekturen drar nytta av förbättrad uppdaterings effektivitet eftersom vi kan överföra den ändrade delen av den lokala buffertens buffert till den externa GRAM i en block överföring, ofta med hjälp av inbyggda DMA-kanaler. Den här modellen eliminerar också avrivning och flimmer som kan finnas i någon av de två första modellerna, eftersom endast slutfört grafik innehåll kopieras till den externa GRAM.

Modell 4) ping-pong-ramtyper:

![Ping-Pong-ramdata](./media/guix/user-guide/ping-pong-frame-buffers.png)

I modell 4 finns det tillräckligt med minne för att tillhandahålla två lokala bildruteproportioner. I det här fallet behandlar GUIX en RAM-buffert som den aktiva bufferten och den andra som arbets Rams buffert. När en uppdaterings-eller ritnings åtgärd pågår, sker det i den arbetsbufferten. När ritningen är klar växlas buffertarna och den aktiva bufferten blir den aktiva bufferten och den aktiva bufferten blir arbetsbufferten. Den här modellen eliminerar också skärm flimmer och riva som kan observeras i ett enda buffrat system.

Modell 5) ping-pong buffertar med arbets ytans sammansättning:

![Ping-Pong buffertar med arbets ytans sammansättning](./media/guix/user-guide/ping-pong-buffers-canvas-composting.png)

I modell 5 kan du skapa ett valfritt antal arbets ytor, upp till gränserna för tillgängligt minne. Arbets ytorna kan vara översatta eller blandade tillsammans som de definieras av programmet för att skapa arbets ytans sammansättning. När en ny sammansatt enhet skapas efter en skärm uppdatering, växlas aktiva och fungerande sammansatta sammansatta buffertar i en åtgärd som är identisk med standarden ping-pong buffer. Med modell 5 kan du utföra tonings-och blandnings åtgärder på skärmen genom att blanda arbets ytorna i det slutliga resultatet.

Modell 6) arbets yta med extern GRAM:

![Arbets yta som är sammansättning med extern GRAM](./media/guix/user-guide/canvas-compositing-external-gram.png)

Modell 6 är en liten variation i modell 5, där endast en sammansatt buffert krävs och den sammansatta bufferten överförs sedan till extern GRAM. Den här modellen stöder även hel skärms blandning och överlägg.

## <a name="string-encoding"></a>Sträng kodning 

GUIX som standard stöder UTF8-format sträng kodning. Stöd för UTF8-sträng kodning kan inaktive ras genom att definiera **GX_DISABLE_UTF8_SUPPORT** i huvud filen ***gx_user. h*** . Om UTF8-kodning är inaktive rad använder GUIX endast standard 8-bitars ASCII plus tecken kodning med latinsk tecken kodning. Inaktive ring av UTF8-Strängs kodning resulterar i ett något mindre GUIX bibliotek och påskyndas körning av funktioner för sträng hantering och text ritning.

UTF8-sträng kodning har följande egenskaper:

  - ASCII-strängar tar inte mer lagrings utrymme än standard 7-bitars ASCII-kodning.

  - De flesta ANSI-C-sträng funktioner fungerar med UTF8-sträng kodning utan modifiering.

Alla aktiva teckenuppsättningar i världen, inklusive kanji Character-uppsättningar, kan representeras med UTF8-sträng kodning.

### <a name="static-and-dynamic-strings"></a>Statiska och dynamiska strängar 

De strängar som är kopplade till dina GUIX-widgetar som stöder text visning kan vara statiskt definierade strängkonstant, som normalt placeras i konstant lagring som en del av tabellen GUIX-sträng som beskrivs nedan, och dynamiskt definierade strängar, som är strängar som genereras vid körning med tjänster som ***sprintf** _ eller _ *_gx_utility_ltoa_* *.

Exempel på dynamiska strängar kan innehålla ett värde som visas som ett tal i en GUIX prompt-widget eller en "tid/datum"-sträng som är dynamiskt formaterad baserat på användarens plats och format inställningar. Om du skapar strängar vid körning som ska tilldelas GUIX-widgetar, till exempel **GX_PROMPT** eller **GX_TEXT_BUTTON widgetar**, måste du välja att statiskt allokera lagringen för de här körnings bara strängarna (dvs.
globala tecken mat ris) eller definiera och installera en funktion för dynamisk minnesallokering och Använd **GX_STYLE_TEXT_COPY** format, som instruerar dessa widgetar att skapa en privat kopia av text strängar som tilldelas.

Det är ett programmerings fel som använder temporär lagring, till exempel en automatisk tecken mat ris, som innehåller en dynamiskt genererad sträng och tilldelar sedan den här strängen till en widget som inte har **GX_STYLE_TEXT_COPY** format. När det här formatet inte har Aktiver ATS kopierar widgeten bara den angivna sträng pekaren och sträng data måste tilldelas statiskt, eller så kommer strängen för widgeten att leda till oväntade resultat.

### <a name="passing-gx_string-arguments"></a>Skicka GX_STRING argument 

GUIX API-funktioner som accepterar en GX_STRING-parameter kontrollerar alltid att längden på strängen som anges av fältet **GX_STRING. gx_string_ptr** matchar värdet för fältet **GX_STRING. gx_string_length** . Om de två fälten inte är konsekventa returneras ett **GX_INVALID_STRING_LENGTH** fel och API: t som kallas returnerar utan att sträng tilldelningen accepteras.

För säkerhets överväganden använder GUIX-programvaran aldrig vanliga C-sträng funktioner som ***strlen** _ eller _ *_strcpy_* *. Dessa funktioner har visat sig vara känsliga för skadliga attacker när sträng data hämtas dynamiskt, vilket ofta är fallet med anslutna program.

GUIX biblioteks versioner före version 5,6 definierade API-funktioner som godkändes ( `GX_CONST GX_CHAR *text` ) som en parameter. Dessa funktioner, men stöds fortfarande för bakåtkompatibilitet, har ersatts och ersatts av de prioriterade API-funktioner som accepterar ( `GX_CONST GX_STRING *string` ) som indataparameter.

Som standard är den föråldrade text hanterings-API: n aktive rad så att alla tidigare skrivna program kan bygga korrekt med de senaste uppdateringarna i GUIX-biblioteket. För att inaktivera det inaktuella API: et för text hantering ska definitions **GX_DISABLE_DEPRECATED_STRING_API** läggas till i **filen _gx_user. h_*_. Alla nya program bör definiera _* GX_DISABLE_DEPRECATED_STRING_API** och ska endast använda funktioner för ERSÄTTNINGS-API. Alla utdatafiler som genereras av GUIX Studio för GUIX library version version 5,6 eller senare använder bara funktioner för byte av API.

I följande tabell visas de inaktuella och nyligen definierade ersättnings API-funktions namnen:

| **Föråldrat funktions namn**              | **Ersatt med**                              |
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

### <a name="guix-string-table"></a>GUIX sträng tabell 

GUIX sträng tabell och sträng resurser registreras med en GUIX-visnings instans.

Varje visning i ett system med flera skärmar har en egen sträng tabell och varje visning kan köras på ett eget språk. De andra GUIX-resurs typerna (färger, teckensnitt och pixelmaps) underhålls också av GUIX display-komponenten eftersom dessa resurs typer är speciella för varje visnings färg format och färgdjup.

Även om du kan skapa en program sträng tabell manuellt, är det oftast tabellen med visnings strängar som definieras av GUIX Studio-programmet som en del av projektets resurs fil. De tillgängliga språken definieras också i resurs huvud filen. Tabellen visnings sträng är en tabell med flera kolumner med pekare till program strängar. Varje kolumn i sträng tabellen representerar ett språk som stöds av programmet.
Om ditt program stöder endast ett språk, till exempel engelska, kommer sträng tabellen bara ha en kolumn. Du kan fortfarande lägga till stöd för ytterligare språk när som helst utan att ändra program varan.

Den aktiva sträng tabellen tilldelas genom att anropa API-funktionen ***gx_display_string_table_set*** . Den här funktionen anropas automatiskt av den genererade start koden i GUIX Studio, men kan också anropas direkt av programmet för att ändra den aktiva sträng tabellen.

Det aktiva språket tilldelas genom att anropa API-funktionen ***gx_display_active_language_set*** . Den här funktionen avgör vilken kolumn i tabell visnings strängen som är aktiv.

När den här funktionen anropas skickas en **GX_EVENT_LANGUAGE_CHANGE** -händelse till alla synliga GUIX-widgetar, så att de kan uppdateras för att visa de nya aktiva sträng data.

Widgetar och program program vara matchar statiskt definierade strängar med sträng-ID-värden och ***gx_display_string_get_ext*** -eller ***gx_widget_string_get_ext*** API-funktioner. Dessa funktioner returnerar **GX_STRING** som associeras med ett angivet sträng-ID och det aktuella aktiva språket.

### <a name="bi-directional-text-display"></a>Dubbelriktad text visning 

GUIX tillhandahåller två strategier för dubbelriktad text support.

Ett alternativ är att ändra ordningen för dubbelriktad text i GUIX Studio-programmet. Med det här alternativet GUIX Studio ansvarar för att generera dubbelriktad text till utdatafilen i dess visnings ordning. Den här lösningen har ingen inverkan på körnings prestanda och kräver inte några tillägg i GUIX runtime-biblioteket. Om du vill tillåta att GUIX Studio skapar displayorder dubbelriktade text strängar, bör du markera kryss rutan **generera dubbelriktad text i visnings ordning** i dialog rutan språk konfiguration för GUIX Studio:

![Konfigurera språk](./media/guix/user-guide/configure-languages.png)

När de här alternativen är markerade innehåller den genererade resurs filen dubbelriktade strängar som genereras i visnings ordningen och ingen extra bearbetning krävs inom GUIX runtime-biblioteket.

Det andra alternativet är att göra dubbelriktad text sortering vid körning. Det här alternativet stöds för de program som måste hantera dubbelriktad text sträng som definieras dynamiskt och som inte genereras av GUIX Studio-programmet. I det här fallet ansvarar GUIX runtime library för att ändra ordning på dubbelriktad text innan du ritar varje text sträng. Den här lösningen har en prestanda för körning och minnes påverkan. Det finns tillräckligt med dynamiskt minne för att ändra dubbelriktad text. Den här lösningen kräver att den villkorliga GX_DYNAMIC_BIDI_TEXT_SUPPORT definieras när du skapar GUIX-biblioteket. Två API Functions ***gx_system_bidi_text_enable*** och ***gx_system_bidi_text_disable*** tillhandahålls för att aktivera/inaktivera dubbelriktad text support vid körning.

Du bör inte använda både **GX_DYNAMIC_BIDI_TEXT_SUPPORT** och konfigurera GUIX Studio för att generera dubbelriktad text i visnings ordning. Du måste välja en strategi eller en annan för dubbelriktad text sträng hantering.

## <a name="memory-usage"></a>Minnesanvändning 

GUIX finns tillsammans med program programmet. Därför bestäms användningen av statiskt minne (eller fast minne) för GUIX av utvecklingsverktygen. t. ex. kompilatorn, länkar och lokaliserare. Användning av dynamiskt minne (eller körnings minne) är direkt kontroll över programmet.

### <a name="static-memory-usage"></a>Statisk minnes användning 

De flesta av utvecklingsverktygen delar program program avbildningen i fem grundläggande områden: *instruktion*, *konstant*, *initierade data*, oinitierade *data* och *GUIX tråds tack*. Figur X på sidan X visar ett exempel på dessa minnes områden.

Det är viktigt att förstå att det här bara är ett exempel. Den faktiska statiska minnesmodulen är specifik för processor, utvecklingsverktyg, underliggande maskin vara och själva programmet.

Instruktions avsnittet innehåller alla programmets processor instruktioner. Det här avsnittet finns ofta i ROM.

Det fasta arean innehåller olika kompilerade konstanter, som i GUIX innehåller standardinställningar och alla program resurser (bilder, strängar, teckensnitt och färger). Dessutom innehåller det här avsnittet "ursprunglig kopia" av det initierade data fältet. Under kompilatorns initierings process används den här delen av det konstanta området för att ställa in globala initierade data i RAM-minnet. Konstant arean är vanligt vis störst och följer vanligt vis instruktions ytan och finns ofta i ROM.

GUIX-pixelmaps och-teckensnitt kräver vanligt vis stora mängder konstant data lagring. Dessa stora statiska data områden hålls normalt i ROM eller FLASH.

GUIX tråds tack definieras i det oinitierade data fältet (som en global variabel) i ***gx_system. h*** -fil på följande sätt:

```C
_gx_system_thread_stack[GX_THREAD_STACK_SIZE];
```

**GX_THREAD_STACK_SIZE** definieras i **_gx_port. h_**, men kan åsidosättas av programmet genom att definiera den här symbolen i sidhuvud filen ***gx_user. h*** eller via projekt alternativ eller kommando rads parametrar. Stack storleken måste vara tillräckligt stor för att hantera värsta fall händelse hantering och kapslade ritnings anrop.

### <a name="dynamic-memory-usage"></a>dynamiskt minne användning 

Som tidigare nämnts är dynamisk minnes användning direkt kontroll av programmet. Kontroll block och minne som är kopplade till arbets ytor osv. kan placeras var som helst i målets minnes utrymme. Detta är en viktig funktion eftersom den underlättar enkel användning av olika typer av fysiskt minne – vid körning.

Anta till exempel att en mål maskin varu miljö har både snabbt minne och långsamt minne. Om programmet behöver extra prestanda för ritning kan arbets ytans minne placeras explicit i det snabba minnes området för bästa prestanda.

Flera valfria GUIX-tjänster och-funktioner kräver en mekanism för dynamisk minnesallokering för körning, som ofta kallas för en heap. Dessa tjänster och funktioner är helt valfria och många GUIX-program använder inte någon heap och definierar inte en mekanism för minnes tilldelning vid körning.

Om du kommer att använda tjänster som kräver minnesallokering måste du installera funktioner som GUIX kommer att anropa när minnet måste tilldelas dynamiskt eller frigöras. Du kan implementera dessa funktioner som du föredrar, så att platsen för den dynamiska mediepoolen är under program kontroll. Om du vill installera stöd för dynamisk minnesallokering ska programmet anropa API-tjänsten ***gx_system_memory_allocator_set*** under program start för att definiera minnesallokering och minnes fria tjänster. Se dokumentationen för detta API för ett fullständigt exempel.

GUIX Services som kräver en minnesallokering för körning och tjänsten för resursallokering är:

  - Läser in binära resurser från extern lagring till GUIX Runtime Environment.

  - Bild avkodaren för program körnings-JPEG.

  - Bild avkodaren för program körnings png.

  - Använda text-widgetar med GX_STYLE_TEXT_COPY.

  - Körnings pixemap funktioner för att ändra storlek och rotation.
  - Körnings-och widgets kontroll block tilldelning.

För mindre program kompileras GUIX-resurser vanligt vis och statiskt länkas som en del av program avbildningen och ingen binär resurs installation krävs. Binära resurser gör det möjligt för ett program att installera resurser (teckensnitt, bilder, språk) vid körning som läses in från vissa lagrings platser, till exempel en flashenhet eller en URL.

JPEG-och PNG-avkodare för körning är valfria komponenter. De flesta GUIX-program tillåter GUIX Studio-verktyget att föravkoda alla nödvändiga bildfiler och lagra dem som tillverkarspecifika GUIX Pixemap-dataresurser. Dessa tjänster tillhandahålls för att vara kompletta för de program som kräver körnings konvertering av JPEG-och/eller PNG-bilder till Pixelmap-format.

**GX_STYLE_TEXT_COPY** gör det möjligt för användaren att ange att en viss widget eller widget ska behålla den egna privata kopia av dynamiskt tilldelad text. Om du använder det här alternativet måste du installera mekanismen för minnesallokering innan du använder. Om den här format flaggan **<span class="underline">inte</span>** anges när en widget för text typ skapas, måste programmet allokera statiska lagrings områden för alla dynamiskt skapade och tilldelade text strängar. Automatiska variabler ska inte användas i det här fallet för att lagra körnings bara sträng data. Om **GX_STYLE_TEXT_COPY** format är aktiverat kan automatiska variabler användas för att lagra sträng data som är tilldelade till GUIX-widgetar, eftersom varje widget skapar en egen kopia av den tilldelade texten.

Pixelmap för storleks ändring och rotering returnerar den resulterande översatta Pixelmap som en ny Pixelmap som är tillgänglig för programmet.
Det måste finnas tillräckligt med dynamiskt minne för att rymma dessa Pixelmap-datablock om dessa tjänster används.

Slutligen kan kontroll blocken för GUIX-skärmar och-widgetar statiskt eller dynamiskt allokeras. För mindre program är det vanligt att skapa alla program skärmar när programmet startas och använda statiskt allokerade kontroll block. För stora program är det vanligt att skapa widgeten skärm och underordnad widget dynamiskt i en as-nödvändig Base. Dynamiskt allokerade kontroll block anges genom att markera kryss rutan **Kör tids tilldelning** i GUIX Studio-egenskapsvyn eller genom att skicka in format flaggan **GX_STYLE_DYNAMICALLY_ALLOCATED** när du skapar en widget via standard-API: et. Att använda dynamiskt allokerade widgets kontroll block kräver att minnesallokering och avfördelnings tjänster definieras enligt beskrivningen ovan.

## <a name="guix-components"></a>GUIX-komponenter 

GUIX-API: er delas och organiseras i flera grundläggande grupper som motsvarar de grundläggande komponenterna i GUIX-systemet. De grundläggande komponenterna är:

| Komponenter  | Description  |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GX_SYSTEM  | System komponenten GUIX, som ansvarar för initiering, händelser, timers, sträng tabeller och synlig hantering av widgeten.                                                                                                                                                                                                                                                                      |
| GX_CANVAS  | Ett rit utrymme. En arbets yta kan vara en tunn abstraktion av maskin varu Rams bufferten eller också kan den vara en ren minnes arbets yta. Arbets ytans typ bestäms av parametrar som skickas till gx_canvas_create API-funktionen.                                                                                                                                                                                   |
| GX_CONTEXT | Rit kontext komponenten. Ritnings kontexten innehåller information om skärmen, arbets ytan och penseln och urklipps området för den aktuella ritningen.                                                                                                                                                                                                                                      |
| GX_DISPLAY | Innehåller API: er och implementeringar av driv rutins nivå som gör att ditt program och GUIX-widgetar kan utföra ritning på en arbets yta. GX_DISPLAY implementeras för att återge grafik på rätt sätt på varje arbets yta med den arbets ytans obligatoriska färg format. GX_DISPLAY-komponenten hanterar också de resurser (färger, teckensnitt och pixelmaps) som är tillgängliga för widgets ritning till arbets ytor som är länkade till varje bildskärm. |
| GX_WIDGET  | Objektet grundläggande synliga widget och associerade API: er. Alla typer av GUIX-widgetar baseras på eller härleds från den grundläggande GX_WIDGET typen.                                                                                                                                                                                                                                                                      |
| GX_UTILITY | Verktyg för att arbeta med rektanglar, funktioner för sträng konvertering och icke-ANSI-matematiska funktioner ingår i den här gruppen.                                                                                                                                                                                                                                                         |

Förutom dessa grundläggande komponenter innehåller GUIX API: er som är unika för varje typ av widget som finns i biblioteket. Dessa API: er beskrivs i kapitel 4 i den här användar handboken, "Beskrivning av GUIX Services".

## <a name="guix-system-component"></a>GUIX system komponent

System komponenten GUIX tillhandahåller flera tjänster som är globala för UI-programmet. Dessa tjänster omfattar: *initiering, händelse hantering, visnings hantering, resurs hantering, timer-hantering* och *hantering av validering*. Varje tjänst är nödvändig för organisationen av ditt program och dessa tjänster beskrivs mer ingående i följande underavsnitt.

### <a name="initialization"></a>Initiering 

GUIX-initieringen utförs av programmet som anropar tjänsten ***gx_system_initialize***, som kan anropas av programmet från ThreadX- ***tx_application_define*** rutinen (initierings kontext) eller från program trådar. Funktionen ***gx_system_initialize*** initierar alla globala GUIX-datastrukturer och skapar GUIX system mutex, händelse kön, timer och tråd. När ***gx_system_initialize*** returnerar kan programmet använda GUIX.

### <a name="thread-processing"></a>Tråd bearbetning 

Den interna GUIX-tråden som skapades under initieringen – ansvarar för det mesta av bearbetningen i GUIX. Bearbetningen i den här tråden Slutför först all ytterligare initiering som krävs av den underliggande visnings driv rutinen. När detta är klart anger GUIX-tråden en loop som först bearbetar alla händelser som finns i händelse kön GUIX och sedan uppdaterar skärmen om det behövs. Skärm uppdateringen kör de nödvändiga GUIX, baserat på vad som är synligt och har marker ATS som smutsig, vilket innebär att den måste ritas om. När det inte finns några händelser och inget kvar att uppdatera på skärmen, kommer GUIX-tråden att inaktive ras, vilket väntar tills nästa GUIX-händelse tas emot.

### <a name="rtos-binding"></a>ÅTERSTÄLLNINGS tider-bindning 

System komponenten GUIX är som standard konfigurerad för att använda real tids operativ systemet ThreadX för tjänster som tråd tjänster, Event Queue Services och timer-tjänster. GUIX kan enkelt hamna i andra operativ system med hjälp av Preprocessor-direktivet GX_DISABLE_THREADX_BINDING och återskapa GUIX-biblioteket. Detta tar bort ThreadX-beroenden från GUIX-källkoden och låter programutvecklaren implementera de operativ system tjänster som krävs med hjälp av den återställnings tider som tillhandahålls av mål systemet. [Bilaga F-GUIX återställnings tider binding Services](appendix-f.md) beskriver de tjänster som måste implementeras för port GUIX till ett annat operativ system än ThreadX-operativsystemet.

### <a name="multithread-safety"></a>Flertrådstestning-säkerhet 

GUIX-API: et är tillgängligt från GUIX tråd kontext och andra program trådar. Program trådar kan interagera med GUIX-tråden genom att skicka och ta emot händelser, genom åtkomst till delade variabler och genom användning av GUIX API-funktioner. GUIX använder en intern ThreadX-mutex för resurs skydd med flera trådar. Dessutom förhindrar GUIX att den interna strukturen för synliga widgetar ändras när en skärm uppdatering har påbörjats. API: er som ändrar trädet för synliga objekt blockeras medan rit åtgärder pågår och släpps när skärm uppdateringen har slutförts.

### <a name="system-timers"></a>System timers 

GUIX förser programmet med periodiska timers, som ofta används för periodisk uppdatering av data som visas i GUIX-fönster. Detta görs via en ThreadX periodiska timer, som också används för att utföra GUIX-effekter på system nivå, som att tona in och ut, osv.

Programmet kan skapa timers och använda samma timer-funktion som används internt av GUIX. Programmet kan naturligtvis också direkt skapa och använda ThreadX timers om det behövs. Fördelen med GUIX timers är att de är mycket enkla att använda och är förkonfigurerade för att fungera i det GUIX händelse drivna bearbetnings systemet.

För att skapa och starta en GUIX-timer ska programmet anropa funktionen ***gx_system_timer_start***. Parametrarna för den här funktionen innehåller en pekare till den anropande widgeten, timer-ID: t (så att en widget startar flera timers) och de inledande och omschema-timeout-värdena. Om timeout-värdet för omschemat är 0, körs timern bara en gång och tas bort från listan över aktiva timer när den upphör att gälla.

När den har startats skickar GUIX-timern GX_EVENT_TIMEOUT händelser till den tidsinställda ägaren, antingen en gång eller periodiskt beroende på värdet för timer-omschemat. En GUIX-timer kan stoppas genom att anropa API-funktionen ***gx_system_timer_stop***.

### <a name="pen-speed-configuration"></a>Konfiguration av Penn hastighet 

System komponenten GUIX innehåller konfigurations information som rör rit hastighets spårning. GUIX skapade internt **GX_EVENT_VERTICAL_FLICK** och **GX_EVENT_HORIZONTAL_FLICK** händelser baserat på hastigheten och avståndet för PEN_DOWN händelser som genererats av driv rutinen för touch-indrivning, om det finns några. Programmet kan konfigurera det minsta avstånd och den hastighet som krävs för att utlösa dessa internt genererade händelser med hjälp av **_gx_system_pen_configure_** API-funktionen.

### <a name="screen-stack"></a>Skärms tack 

System komponenten GUIX tillhandahåller tjänster som är relaterade till GUIX-skärms stacken, som är en valfri funktion som stöder en virtuell widget till vilken skärmar kan flyttas, visas och hämtas vid körning av programmet. Skärm bilden är användbar för att hantera avancerade meny system, där skicka den väg som användaren kan komma åt i olika tillstånd i meny systemet. Att återgå till det tidigare läget i meny systemet kan enkelt utföras genom att först skicka det tidigare skärm läget och sedan Visa den nya skärmen, och så att den nya skärmen kan visa det tidigare läget från skärm bilden när den aktuella skärmen stängs.

### <a name="clipboard-maintenance"></a>Urklipps underhåll 

GUIX stöder Urklipp för kopiering och inklistring av text under körning av körning. Det här stödet tillhandahålls av GUIX-system komponenten.

### <a name="dirty-list-maintenance"></a>Underhåll av lista över skadade listor 

GUIX har en lista över felaktiga widgetar, vilket innebär att widgetar som är synliga och måste ritas om på grund av status ändringar eller görs nyligen synliga. Den här skadade listan förbättrar ritnings prestanda genom att låta GUIX utföra en uppdaterings åtgärd på arbets ytan för att avspegla alla aktuella ändringar i GRÄNSSNITTets status, i stället för att göra en uppdatering av arbets ytan när varje GRÄNSSNITTs ändring görs.
Den här listan över återkallas också av GUIX system-komponenten.

### <a name="animation-control-block-pool"></a>Animering av Control Block-pool 

Program vill ofta köra flera animeringssekvenser, ofta parallellt. GUIX upprätthåller en pool med animerings kontroll block som programmet kan använda för att allokera och använda. Detta frigör programmet från att statiskt definiera dessa kontroll block och gör att de kan återanvändas vid olika tidpunkter, i stället för att definiera ett unikt kontroll block för animering för varje animering som programmet kan definiera. Modulen för styrnings block underhålls också av GUIX system-komponenten.

### <a name="system-error-handling"></a>System Fels hantering 

Fel hanteraren för GUIX-systemet är avsedd att hjälpa programmet att hitta interna systemfel i GUIX som kan vara svårare att fastställa från API-perspektivet. När ett systemfel uppstår i GUIX anropas den interna ***_gx_system_error_process*** funktionen. Den här funktionen sparar den angivna felkoden och ökar det totala antalet systemfel som upptäckts. Systemmiljövariabler definieras enligt följande:

UINT **_gx_system_last_error**;

ULONG **_gx_system_error_count**;

Om GUIX-programmet fungerar onormalt, är det bra att titta på variabeln antal fel i fel söknings programmet. Om det är inställt är ett bra sätt att felsöka problemet är att ange en Bryt punkt i ***_gx_system_error_process*** -funktionen och se när/var den anropas från.

## <a name="guix-canvas-component"></a>GUIX-arbetsyta

Arbets ytans komponent ansvarar för all bearbetning av arbets ytor. En arbets yta är i praktiken en virtuell RAM-buffert. Programmet måste skapa minst en arbets yta för att kunna producera grafiska utdata.
Normalt skapar du minst en arbets yta för varje fysisk bildskärm som stöds av systemet.

All GUIX-ritning äger rum på en arbets yta. I enklare eller minnes begränsade system kommer det förmodligen bara finnas en arbets yta som kan vara direkt länkad till den synliga bufferten, medan system med mer minne och mer avancerade grafik krav kan kräva flera arbets ytor. Om du gör flera arbets ytor tillgängliga för en bildskärm kan funktioner som skärm och fönster tona in och tona ut effekter.
Arbets ytor kan vara en av två huvud typer, enkla eller hanterade.

En enkel arbets yta är ett arbets område på skärmen som används av programmet.
GUIX har inget direkt med en enkel arbets yta, men programmet kan använda en enkel arbets yta för att rendera en avancerad ritning till en buffert på låg skärm, och sedan använda den här bufferten för att uppdatera den synliga arbets ytan vid behov.

En hanterad arbets yta visas automatiskt i maskin varu fönstrets buffert med GUIX. En hanterad arbets yta ingår i att skapa en sammansatt arbets yta för de system som har tillräckligt med minne för att stödja flera hanterade arbets ytor. Hanterade arbets ytor har en Z-ordning som underhålls av GUIX och Visa Urklipp tillämpas på alla hanterade arbets ytor.

En arbets yta skiljer sig från en ramkant i så är den mer generisk. I minnes begränsade system kan det finnas bara en arbets yta och minnet för den här arbets ytan kan vara det synliga RAM-minnet. Men för mer komplexa system som stöder mer avancerade grafiska överlägg och flera arbets ytor, är de hanterade arbets ytorna var och en allokerade egna minnes områden som är distinkta från maskin varu fönstrets buffertminne.
Dessa hanterade arbets ytor återges i den synliga bildens buffert under ram-buffertens uppdatering eller växlings åtgärd.

För maskin vara som stöder flera bild lager, d.v.s. flera överlappande bildruteproportioner, kan programmet binda en eller flera arbets ytor till maskin varu grafik skikten med hjälp av ***gx_canvas_hardware_layer_bind*** -API: et. Den här tjänsten informerar arbets ytan som den är länkad till ett visst maskin varu grafik lager, och när den länkade arbets ytan länkas försöker att använda maskin varu stöd för arbets ytans synlighet (dvs. gx_canvas_show, gx_canvas_hide), arbets ytans alpha blending (d.v.s. ***gx_canvas_alpha_set***) och förskjutning av arbets ytan i visningen (***gx_canvas_offset_set***).

För andra arkitekturer än den enklaste arbets ytan eller en enskild RAM-organisation bestäms storleken på en arbets yta av programmet och kan skilja sig från den fasta storleken på en ramkant.
Det kan också finnas vid en förskjutning som valts av programmet. Annan information, till exempel Z-ordning, behålls på arbets ytan. När arbets ytan ritningen är klar överförs innehållet på arbets ytan till den fysiska visningen av visnings driv rutinen. I vissa system som inte har tillräckligt med minne för en separat minnes yta för arbets ytor och RAM-minne görs uppdateringen av arbets ytan direkt till den fysiska visningen via bildskärms driv rutinen.

### <a name="canvas-creation"></a>Skapa arbets yta 

Ett arbets ytans objekt kan skapas vid initiering eller när som helst under körningen av program trådar. Det finns ingen gräns för hur många arbets ytans objekt som kan skapas av ett program. De flesta program skapar dock bara ett objekt i arbets ytan för alla GUIX-ritningar.

### <a name="canvas-control-block"></a>Kontroll block för arbets yta 

Egenskaperna för varje objekt i arbets ytan finns i kontroll blocket **GX_CANVAS** och definieras i **_gx_api. h_**. Det minne som krävs för ett objekt i arbets ytan tillhandahålls av programmet och kan placeras var som helst i minnet. Det är dock vanligt att göra blocket för objekt kontroll blocket och rit området till en global struktur genom att definiera dem utanför omfånget för en funktion.

### <a name="canvas-alpha-channel"></a>Alfa kanal för arbets yta

GUIX stöder alpha-blandning av förgrunds-och bakgrunds färger på många nivåer, inklusive bitmapp alpha-kanalen som anger ett blandnings förhållande per bild punkt, pensel alfa som anger blandnings förhållandet för en pensel med 16 BPP och högre färgdjup, och ytan alpha som anger blandnings förhållandet för ett överlägg.

Alfa värdet för en arbets yta används när det finns flera arbets ytor som är sammansatta tillsammans för visning i den inramade bufferten. Om arbets ytans Z-ordning är sådan att arbets ytan är över andra arbets ytor kan du ange ett alfa värde för arbets ytan för att blanda arbets ytan med de som ligger bakom. Att snabbt ändra alpha-värdet för en arbets yta används för att ge "tona in"-effekter på skärmens över gång, men du kan använda arbets ytans alfa på många sätt.

Om en arbets yta är kopplad till ett maskin varu grafik lager med hjälp av gx_canvas_hardware_layer_bind () försöker GUIX att implementera arbets ytan alpha blending använder maskin varu support, vilket minimerar den program vara som är kopplad till att blanda en överliggande arbets yta.

Alfa värden sträcker sig från 0 till 255, där värdet 0 betyder att pixeln är helt transparent och värden som är större än 0 ökar det som är mindre transparent. det kan bara finnas stöd för skärm driv rutiner som körs vid 16-BPP och högre, såvida inte maskin varu hjälpen för kombination av arbets ytor tillhandahålls.

### <a name="canvas-offset"></a>Förskjutning av arbets ytan 

En arbets yta kan förskjutas inom den synliga bildens buffert genom att anropa ***gx_canvas_offset_set*** API-tjänsten. Förskjutning av arbets ytor används vanligt vis för att implementera Sprite-animeringar. Om en arbets yta är kopplad till ett maskin varu grafik lager genom att anropa API-funktionen ***gx_canvas_hardware_layer_bind*** försöker GUIX implementera ändringar av arbets ytans förskjutning som använder maskin varu support, vilket minimerar den program vara som är kopplad till att flytta arbets ytans position.

### <a name="canvas-drawing"></a>Arbets ytans ritning 

Komponenten GUIX-arbetsyta ger ett fullständigt Drawing API för programmet. Innan API: erna för Drawing, till exempel ***gx_canvas_line_draw*** eller ***gx_canvas_pixelmap_draw*** kan anropas, måste mål arbets ytan öppnas för ritning genom att anropa funktionen ***gx_canvas_drawing_initiate*** API. Den här funktionen förbereder en arbets yta för ritning och skapar en ***rit kontext***.

De Drawing-API: er som återges på arbets ytan, till exempel ***gx_canvas_line_draw** _ eller _*_gx_canvas_text_draw_*_, använder parametrar som finns i den aktuella rit kontextens pensel för att definiera linje formatet, bredden och färgerna. Dessa pensel parametrar ändras genom att anropa _*_gx_context_brush_define_*_, _* _gx_context_brush_set_* *, ***gx_context_brush_style_set**_ och liknande API-funktioner när en rit kontext har upprättats genom att anropa _ *_gx_canvas_drawing_initiate_* *.

När GUIX anropar fönster-och widgeten ritnings funktioner som en del av en uppskjuten arbets ytans uppdaterings åtgärd, öppnas mål arbets ytan för ritning innan du anropar ritnings funktionen för widgeten. Därför krävs inte standard ritnings funktionerna i widgeten för att öppna mål arbets ytan. Detta har gjorts för dem.

I vissa fall kanske programmet vill framtvinga en omedelbar ritning till en arbets yta. I det här fallet kan programmet utföra följande steg.

1. Anropa API-funktionen ***gx_canvas_drawing_initiate*** , genom att skicka in mål arbets ytan och rektangeln inom den arbets ytan där programmet vill rita. 

2. Ring valfritt antal arbets ytans rit-API: er för att utföra den önskade ritningen.

3. Anropa ***gx_canvas_drawing_complete*** API-funktionen för att signalera att ritningen har slutförts. Detta tömmer arbets ytan till den synliga ram-bufferten och/eller utlöser en växlings åtgärd för buffert, beroende på systemets minnes arkitektur.

### <a name="drawing-apis"></a>Drawing-API: er 

Det finns flera huvudsakliga ritnings primitiver som krävs av GUIX för att rita alla visuella element på skärmen. Dessa API: er för Drawing kan också anropas av program vara, vanligt vis som en del av en anpassad widgets ritnings funktion. Dessa GUIX-verktyg för arbets ytor utför parameter validering och Urklipp och skickar sedan ned de urklippta ritningarna nedåt till visnings driv rutinen för maskinvaru-och färg formats-speciella ritnings implementeringar. Dessa funktioner för Drawing API definieras enligt följande.

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

Drawing API anropas via GUIX-arbetsyta API och all ritning görs med hjälp av gx_canvas_ * API functions. Ritningen görs med den aktuella penseln i den aktuella rit kontexten. Någon av form rit funktionerna ovan kan vara konturer, fyllda färger fyllda eller Pixelmap fyllda som definieras av den aktuella penseln. Om du vill ändra figurens kon tur bredd, färg eller fyllning använder du gx_context_brush_ * API Functions för att definiera penseln i den aktuella rit kontexten.

API: erna för Drawing på program nivå utför inte den faktiska ritningen på arbets ytan, utan i stället verifiera anroparens parametrar innan du anropar ritnings funktionen för visnings driv rutins nivå. Ritnings funktionen på driv rutins nivå skriver faktiskt pixel data till arbets ytans minne.

GUIX tillhandahåller ritnings funktioner för börs eller allmän visnings driv rutin för olika färgdjup, inklusive 1, 2, 4, 8, 16, 24 och 32 bitar per bild punkt (BPP). I vissa fall ersätts standard implementeringen av program varu ritningen med maskin varu accelererade implementeringar för de maskin varu mål som tillhandahåller en 2D-ritnings Accelerator.

### <a name="color-depth"></a>Färgdjup 

GUIX stöder färg djup upp till 32-BPP samt svartvit och gråskala. Typen av färgdjup stöder i stort sett av funktionerna i den underliggande fysiska visningen och påverkar också hur mycket minne som krävs för arbets ytans ritnings område. Följande är en lista med stöd för färgdjup tillsammans med en kort beskrivning av variationerna i det här färg djupet.

| Färg &nbsp; format       | Description                                                                                                   |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| 1-bitars monokrom   | 1-bitars per bild punkt i packat format.                                                                                                   |
| 2-bitars gråskala    | 4 grå nivåer, förpackade fyra bild punkter per byte.                                                                                      |
| 4-bitars gråskala    | 16 grå nivåer, förpackade två bild punkter per byte.                                                                                      |
| 4-bitars färg        | Ett VGA-format plan för minnes organisation.                                                                                         |
| 8-bitars gråskala    | 256 grå nivåer                                                                                                                  |
| 8-bitars läge för palett | 1 byte per pixel som används som palett-index                                                                                           |
| 8-bitars r:g: b-läge   | Ett mindre vanligt använt 2:3:2 r:g: b-format.                                                                                         |
| 16-bitars             | Varje pixel kräver två byte. Kan vara r:g: b eller b:g: r byte order. Normalt 5:6:5-struktur, men det kan också vara 5:5:5-struktur eller 4:4:4:4 a:r: g:b-strukturen. |
| 24-bitars             | Varje pixel kräver 3 (packat format) eller 4 (uppackat format) byte. Kan vara i r:g: b eller b:g: r byte-ordning enligt vad som krävs av maskin varan. |
| 32-bitars             | Varje pixel kräver 4 byte med en alfa kanal. Kan vara a:r: g:b eller b:g: r:a byte order och bestäms av maskin varan.              |

### <a name="mouse-support"></a>Stöd för musen 

GUIX har stöd för att rita en mus markör på önskad arbets yta. Mus markören kan ritas i program vara eller kan stödjas av maskin varu markören överlägg. I båda fallen är API: et för programmet som hör till stöd för mus markör detsamma om du använder ritning med program vara eller maskin varans mus markör.

Stöd för GUIX-möss är bara aktiverat om `#define GX_MOUSE_SUPPORT` har definierats i huvud filen gx_user. h innan du skapar GUIX-biblioteket.

Programmet måste definiera mus markören och hotspot med hjälp av ***gx_canvas_mouse_define*** API-funktionen. Det här API: et accepterar en pekare till den arbets yta där markörens bild ska ritas och en pekare till en **GX_MOUSE_CURSOR_INFO** -struktur, som definierar markörens bild och klickbart läge för musen i förhållande till det övre vänstra hörnet.

## <a name="guix-display-component"></a>GUIX Visa komponent 

Visnings komponenten är fundamental i GUIX, eftersom den hanterar bearbetningen av alla visnings objekt, som i sig innehåller en eller flera arbets ytor, widgetar och Windows. Visnings komponenten samverkar också med den underliggande driv rutinen för maskin varu skärmen som är associerad med varje skärm genom en serie funktions pekare.

### <a name="display-creation"></a>Skapa visning 

Ett visnings objekt kan skapas under initieringen eller när som helst under körningen av program trådar. Ett program skapar vanligt vis ett visnings objekt för att hantera varje fysisk skärm. Om du har använt GUIX Studio för att definiera programmet och de fysiska tillgängliga visar, använder du gx_studio_display_configure API-funktionen för att skapa och initiera var och en av dina skärmar.

### <a name="display-control-block"></a>Visa kontroll block 

Egenskaperna för varje visnings objekt finns i dess kontroll block ***GX_DISPLAY** _ och definieras i _ *_gx_api. h_* *. Det minne som krävs för ett visnings objekt tillhandahålls av programmet och kan finnas var som helst i minnet. Det är dock vanligt att Visa kontrollen blockera en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="resource-management"></a>Resurshantering 

Resurser är användar gränssnitts komponenter som behövs i programmet, men de är inte program kod. Resurser är program data och definieras vanligt vis statiskt. Resurs typer omfattar pixelmaps, teckensnitt, färger och strängar. Dessa resurser kan ändras när som helst, vanligt vis utan att program varan ändras. Det är viktigt att behålla lagringen av och referenser till resurser som är avgränsade från program program varan för att tillåta ändring av GRÄNSSNITTets utseende utan att ändra program kod eftersom ändringar i program program varan ofta kräver att den här program varan återtestas och verifieras.

GUIX- ***visnings*** modulen innehåller resurser för resurs hantering för alla resurser som är beroende av bildens färgdjup och format. Dessa funktioner omfattar att underhålla den aktiva Pixelmap-tabellen, aktiva teckensnitts tabellen och den aktiva färg tabellen. Strängen för sträng tabellen underhålls av GUIX-systemmodulen, eftersom sträng resurser normalt inte behöver ändras baserat på färgdjup och format.

Program varan refererar till resurser efter resurs-ID, vilket är ett index i motsvarande resurs tabell. Detta gör att tabellen kan ändras, till exempel om färg tabellen kan ändras när en produkt ändras från "dags läge" till "natt läge", men färg-ID-värdena är desamma.

Dina program resurser skrivs till en resurs fil (eller en uppsättning resursfiler) av GUIX Studio-programmet. Standard färger, pixelmaps och teckensnitt anges automatiskt när du skapar ett nytt GUIX Studio-projekt, men dessa standardinställningar ersätts enkelt när du definierar ditt programs utseende och känsla.

Det är viktigt att Observera att resurs-ID: n för färger, teckensnitt och pixelmaps inte kan matchas mot deras faktiska färg-, teckensnitts-eller Pixelmap-värden förrän den aktiva visnings komponenten är känd. Eftersom GUIX-arkitekturen stöder flera aktiva visar, kan resurs-ID: n bara matchas till resurs värden när en widget och dess associerade resurs-ID kan matchas mot en speciell visning. Den här egenskapen kallas dynamisk bindning. Resurs-ID för en egenskap, t. ex. en textfärg, till exempel resurs-ID **GX_COLOR_ID_TEXT,** kan matcha till ett 16-bitars R:G: B-värde för vitt när det används på en skärm, men samma färg-ID kan matcha svart färg värde för svart färg när det används på en annan bildskärm.

I praktiken innebär denna dynamiska bindning av resurs-ID: n till resurs värden att program vara och GUIX interna komponenter oftast bara löser resurs-ID: n till resurs värden inom en aktiv rit kontext. En aktiv ritnings kontext anger den aktuella aktiva visningen, vilket gör att GUIX kan matcha varje resurs-ID till ett resurs värde. Om program varan krävs för att hitta ett resurs värde utanför en rit kontext kan detta också göras för synliga widgetar. Synliga widgetar är länkade till ett rot fönster som också kan användas för att matcha den aktiva arbets ytan och Visa för widgeten.

Om en widget har skapats men ännu inte har visats (dvs. inte har länkats till några rot fönster eller andra synliga överordnade), går det inte att matcha alla resurs-ID: n som är associerade med widgeten till ett annat resurs värde än genom direkt indexering i resurs tabellen som är kopplad till en speciell visning. Den här direkt åtkomsten till en specifik resurs tabell kan på ett säkert sätt göras av program varan, men görs aldrig i den interna biblioteks program varan för GUIX.

### <a name="widget-defaults"></a>Standardinställningar för widget 

GUIX-visnings komponenten tillhandahåller också standard definitioner för olika widgetar attribut. Om inget annat anges av programmet skapas widgetar/Windows med dessa systemattribut. Dessa systemattribut består i huvudsak av teckensnitt, färger och bitmappar som finns i system resurs tabellerna. Ytterligare attribut för standard utseende för rullnings List hanteras också av GUIX display-komponenten.

Standard färg inställningarna definieras av färg tabellen som tilldelas varje bildskärm och de fördefinierade standardfärg-ID: na. Följande standardfärg-ID: n är följande:

| Färg-ID | Description |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| GX_COLOR_ID_CANVAS | Standard arbets yta (t. ex. visnings bakgrunds färg) |
| GX_COLOR_ID_WIDGET_FILL | Standard fyllnings färg för widget |
| GX_COLOR_ID_WINDOW_FILL | Standard fönster fyllnings färg |
| GX_COLOR_ID_DISABLED_FILL | Standard fyllnings färg för avaktiverad widget |
| GX_COLOR_ID_DEFAULT_BORDER | Standardkant linje färg för widget |
| GX_COLOR_ID_WINDOW_BORDER | Standard fönster kant linje färg |
| GX_COLOR_ID_TEXT | Standard text färg |
| GX_COLOR_ID_SELECTED_TEXT | Standard färg för markerad text |
| GX_COLOR_ID_DISABLED_TEXT | Standard text färg för inaktiverat |
| GX_COLOR_ID_SELECTED_TEXT_FILL | Standard fyllnings färg för markerad text |
| GX_COLOR_ID_READONLY_TEXT | Standard text färg för ReadOnly |
| GX_COLOR_ID_READONLY_FILL | Standard fyllnings färg för skrivskyddad text |
| GX_COLOR_ID_SCROLL_FILL |    Fyllnings färg för rullnings List |
| GX_COLOR_ID_SCROLL_BUTTON | Fyllnings färg för rullnings knapp |
| GX_COLOR_ID_SHADOW | Standard skugg färg |
| GX_COLOR_ID_SHINE | Standard markerings färg |
| GX_COLOR_ID_BUTTON_BORDER | Kant linje färg för knapp-widget |
| GX_COLOR_ID_BUTTON_UPPER | Den övre fyllnings färgen för knapp widgeten |
| GX_COLOR_ID_BUTTON_LOWER | Knapp widget, nedre fyllnings färg |
| GX_COLOR_ID_BUTTON_TEXT | Textfärg för knapp Beskrivning |
| GX_COLOR_ID_TEXT_INPUT_TEXT | Textfärg för widgeten text text |
| GX_COLOR_ID_TEXT_INPUT_FILL | Fyllnings färg för text ingång |
| GX_COLOR_ID_SLIDER_TICK | Färg som används för att rita skal streck i skjutreglaget. |
| GX_COLOR_ID_SLIDER_GROOVE_BOTTOM | Färg som används för att rita ett skjutreglage |
| GX_COLOR_ID_SLIDER_NEEDLE_OUTLINE | Färg som används för att rita en nålventil |
| GX_COLOR_ID_SLIDER_NEEDLE_FILL | Färg som används för att fylla skjutreglaget |
| GX_COLOR_ID_SLIDER_NEEDLE_LINE1 | Färg som används för att rita nålventil |
| GX_COLOR_ID_SLIDER_NEEDLE_LINE2 | Färg som används för att rita nålventil |

Dessa färg-ID-värden mappas till ett speciellt färg värde som definieras av den färg tabell som tilldelas varje skärm. Dessa standardvärden kan ändras som en grupp för en bildskärm genom att anropa API-funktionen ***gx_display_color_table_set*** . Om du använder GUIX Studio initieras tabellen för visnings färg automatiskt när programmet anropar funktionen ***gx_studio_display_configure*** .

GUIX-display-komponenten underhåller också en standard teckensnitts tabell. Standard teckensnitts tabellen definierar teckensnittet som används av varje widgets typ, såvida det inte uttryckligen anges av programmet. De fördefinierade visnings teckensnitts tabell-ID: na innehåller följande värden.

| Teckensnitts &nbsp; -ID | Description |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------|
| GX_FONT_ID_DEFAULT | Standard teckensnitt som används när inget speciellt teckensnitt har definierats |
| GX_FONT_ID_BUTTON | Standard teckensnitt som används för all text på knappar |
| GX_FONT_ID_TEXT_INPUT | Standard teckensnitt som används för text redigerings fält |

Teckensnitts-ID: t som används av en widget för text typer kan tilldelas igen med hjälp av **gx_<widget_type>_font_set** -API: et som angetts för varje textrelaterad typ av widget. Hela teckensnitts tabellen kan tilldelas på nytt genom att anropa API-funktionen **gx_display_font_table_set** .

### <a name="scrollbar-appearance"></a>Rullnings List utseende 

GUIX-visningen behåller också standard visnings inställningarna för rullnings listen. De här inställningarna definieras av **GX_SCROLLBAR_APPEARANCEs** strukturen som definieras nedan. GUIX display har en rullnings List struktur för lodräta rullnings lister och en andra struktur för vågräta rullnings lister. Programmet kan ändra standard rullnings listens utseende för visning genom att initiera en **GX_SCROLLBAR_APPEARANCE** -struktur och anropa API-funktionen ***gx_display_scroll_appearance_set***.

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
| GX_SCROLLBAR_APPEARANCE struktur medlem | Description |
| --- | --- |
| gx_scroll_width | Bredden på en lodrät rullnings list eller höjd för en vågrät rullnings List i bild punkter. |
| gx_scroll_thumb_width | Bredden på hissen och slut knapparna i bild punkter. |
| gx_scroll_thumb_travel_max | Förskjut från slutet av rullnings listen till den maximala knappen för skjutreglagets slut punkt. |
| gx_scroll_fill_pixelmap | Pixelmap används för att fylla rullnings bakgrunden. |
| gx_scroll_thumb_pixelmap | Pixelmap används för att rita knapp för rullnings knapp. |
| gx_scroll_up_pixelmap | Pixelmap används för att rita upp rullnings knapp. |
| gx_scroll_down_pixelmap | Pixelmap används för att rita rullnings knapp. |
| gx_scroll_fill_color | Färg-ID för färg som används för att fylla rullnings List bakgrunden. |
| gx_scroll_button_color | Färg-ID för färg som används för att fylla rullnings knapp för rullnings List. |

Förutom dessa standardinställningar för teckensnitt, färg och format, kan programmet ange vilken som helst av parametrarna i ett ärende per fall som önskas med hjälp av API: er som tillhandahålls av varje typ av widget.

### <a name="skinning-and-themes"></a>Skalning och teman

Skalning gör det möjligt för GUIX-widgetar och Windows att enkelt ändra sitt grundläggande utseende, dvs. om du ändrar "skalet" på en plats kommer det grundläggande utseendet för alla associerade widgetar och fönster att ändras.

Om du skalar om ditt GUIX-program måste du ange en ny färg-, teckensnitts-och Pixelmap-tabell för GUIX Visa resurs tabeller. Eftersom alla GUIX-widgetar refererar till sina färger, bitmappar eller teckensnitt med resurs-ID: n, ger en ny resurs tabell automatiskt alla GUIX-widgetar att börja använda dina nya färger och pixelmaps när de ritas upp till önskad visning.

En ny uppsättning teckensnitt, färger och pixelmaps som är utformade för att samar beta för att ge ett attraktivt utseende kallas för ett *tema*. Ett tema definierar en uppsättning resurs tabeller och storleken på varje resurs tabell. Valfritt antal teman kan definieras för alla skärmar som använder GUIX Studio-programmet. Du måste skicka det första tema indexet till den genererade GUIX Studio-funktionen ***gx_studio_display_configure***, som installerar det ursprungliga temat i den skapade visningen. Det aktiva temat för visning kan ändras när som helst genom att anropa funktionen ***gx_display_theme_install***.

### <a name="root-window"></a>Rot fönster

För varje synlig arbets yta som skapats av ett program måste programmet också skapa ett rot fönster för arbets ytan. Det här särskilda fönstret fungerar i princip som en behållare för alla program på den översta nivån i Windows och widgetar. Rot fönstret ritar arbets ytans bakgrund, och eftersom rot fönstret härleds från klassen **GX_WINDOW** kan rot fönstret också ha Skriv bords underlägg. Om du vill ändra bakgrunds färgen på din bildskärm eller arbets yta ändrar du bara fyllnings färgen för rot fönstret som är kopplat till arbets ytan.

Om du använder den genererade GUIX Studio-funktionen med namnet ***gx_studio_display_configure*** för att konfigurera dina skärmar, skapas arbets ytan och rot fönstret för varje visning åt dig som en del av den här initierings funktionen.

### <a name="anti-aliasing"></a>Kant utjämning 

Kant utjämning är en valfri funktion i GUIX som används för att jämna ut linjer, kurvor och teckensnitt. Kant utjämning stöds bara när du kör med en bildskärms driv rutin som använder 16-BPP eller högre färgdjup.

Ritning med anti-aliasad linje är aktive rad genom att ange **GX_BRUSH_ALIAS** blixt i den aktiva penseln. Detta gäller linjer som ritats direkt och till linjer som ritats som kant linje i en polygon eller cirkel.

Text ritning med anti-alias aktive ras med ett eget teckensnitt som skapas av GUIX Studio-programmet. Du anger om ett teckensnitt ska genereras som ett alias eller binärt när du skapar teckensnittet.
Kantutjämna teckensnitt i GUIX använder 16 genomskinlighets nivåer för varje bild punkt.

### <a name="clipping"></a>Klippa 

Urklipp stöds internt av GUIX-display-komponenten, och i fönstret och i widgeten visas en överordnad-underordnad arkitektur som hanteras av GUIX-widgetar. Det finns inget fönster eller widget som kan ritas utanför widgetens yta och en widget tillåts aldrig Rita utanför området för widgetens överordnade objekt.

Detta förhindrar också widgetar från att rita i pixel koordinater som placerar utanför arbets ytans minne, vilket förmodligen leder till minnes skada eller systemfel. Widgetar får inte rita utanför widgetens område, widgetens överordnade område eller utanför arbets ytans omfattning.

Dessutom kan widgetar bara rita till områden som tidigare har marker ATS som skadade. Detta förhindrar att ett helt fönster ritas, till exempel när endast ett hörn i fönstret har visats. Endast den del av fönstret som faktiskt behöver uppdateras är markerad som smutsig och så att fönster ritnings funktionen bara uppdaterar pixlar i området smutsig.

GUIX-visnings komponenten tillämpar dessa urklipps algoritmer innan du anropar ritnings funktionerna på driv rutins nivå.

### <a name="views"></a>Vyer 

GUIX upprätthåller alltid en uppsättning vyer för varje rot fönster och varje underordnat fönster i rot fönstret. Vyer är ett dynamiskt, definierat storleks sorterings utrymme som ändras när fönster placering och Z-ordning ändras.
GUIX använder vyer för att förhindra att ett fönster eller en widget i bakgrunden ritas ovanpå ett fönster eller en widget i förgrunden. Vyer upprätthåller ämnes område Z-ordning. Dessutom är vyer viktiga för att effektivisera ett fönster i bakgrunden från att rita till något område på arbets ytan som inte kan visas. Om ett fönster är helt täckt av ett annat fönster, kan inte det fönster som omfattas Rita till arbets ytan alls, även om det försöker göra det.

### <a name="display-driver-interface"></a>Visa driv Rutins gränssnitt 

GUIX-bildskärms driv rutiner ansvarar för all interaktion med den underliggande fysiska skärmen. Bildskärms driv rutinerna har tre grundläggande funktioner: initiering, ritning och inramad visning av buffertar.
Initieringen ansvarar för att förbereda den fysiska bildskärmens maskin vara, informerar GUIX av egenskaperna för den fysiska bildskärmens maskin vara och för att informera GUIX vilka vissa ritnings funktioner ska användas. Den huvudsakliga driv rutins initieringen anropas från funktionen GUIX ***gx_display_create*** . Dessutom anropar GUIX-tråden även en sekundär bildskärms driv rutins initiering från tråd kontexten. Den här sekundära bildskärms driv rutinen behövs bara om driv rutinen kräver återställnings tider-tjänster under initieringen, t. ex., avbrott i enheten eller ***tx_thread_sleep*** begär Anden om fördröjning mellan stegen i initierings processen.

När initieringen är klar är visnings driv rutinen ansvarig för all direkt ritning som kan göras i den fysiska bildskärms maskin varan.
Slutligen är visnings driv rutinen ansvarig för att Visa ramtypen.

## <a name="guix-widget-component"></a>Komponent för GUIX-widget

En GUIX-widget är ett synligt grafiskt element. Det finns GUIX-komponenter som inte är synliga, till exempel timers och funktioner för matematik verktyg.
Alla synliga komponenter härleds dock från komponenten Basic GUIX-widget. En GUIX-widget är det primära Bygg blocket av GUIX-visningen – alla andra grafiska element härleds från funktionen för bas-widget.

GUIX-widgetar implementeras på ett objektorienterat sätt med fullständigt stöd för arv. Detta görs med hjälp av ANSI C, vilket resulterar i minsta möjliga minnes-och bearbetnings krav. När vi pratar om en viss widget, till exempel **GX_BUTTON**, *härleds från* en annan widget, t. ex. bas **GX_WIDGET**, vad vi menar är att **GX_BUTTON** kontroll strukturen innehåller alla medlemsvariabler och funktions pekare i **GX_WIDGET**, med vissa ytterligare variabler som är specifika för **GX_BUTTON**. GUIX bygger upp lager av widgetar på det här sättet, så att fler komplexa widgetar alltid baseras på en enklare widget. Den här hierarkiska modellen av härledning gör det lättare att lära sig de API: er som används för att ändra widgets parametrar. Om du vill ändra färgen på en knapp använder du samma API som du använder för att ändra färgen på en widget, nämligen ***gx_widget_fill_color_set***.

Organisationen av synliga widgetar upprätthålls i ett överordnat, underordnat sätt med hjälp av träd strukturerade listor som länkar underordnade widgetar till sina överordnade. De underordnade objekten ärver egenskaper från sina föräldrar, till exempel vyer som de kan rita och den arbets yta där de ritar.
Underordnade widgetar kan ha sina egna underordnade widgetar och sedan ärva olika egenskaper från den överordnade. Egenskaperna för en widget kan uttryckligen omdefinieras via olika GUIX-API-anrop.

### <a name="widget-creation"></a>Skapa widget 

Ett widgets objekt kan skapas vid initiering eller när som helst under körningen av program trådar. Det finns ingen gräns för antalet widgets objekt som kan skapas av ett program. Det finns inte heller någon gräns för antalet underordnade alla widgetar som kan ha, inom minnes gränserna för mål maskin varan.

Varje widget har sin egen Create-funktion, till exempel ***gx_button_create** _ eller _ *_gx_prompt_create_* *. De första tre parametrarna till dessa funktioner är alltid samma, nämligen en pekare till kontroll strukturen för widget, en sträng pekare till widgetens namn och en pekare till widgetens överordnade. Varje Create-funktion kan ha valfritt antal ytterligare parametrar beroende på kraven för den aktuella widgeten.

### <a name="widget-control-block"></a>Kontroll block för widget 

Egenskaperna för varje widget-objekt finns i kontroll blocket **GX_WIDGET** och definieras i **_gx_api. h_**. Det minne som krävs för ett widgets objekt tillhandahålls av programmet och kan finnas var som helst i minnet. Det är dock vanligt att göra widgeten objekt kontroll blockera en global struktur genom att definiera den utanför omfånget för en funktion. Om du använder GUIX Studio kan dina widgets kontroll block vara statiskt allokerade i din Studio genererade Specifikations fil, eller så kan de tilldelas dynamiskt av ditt program.

### <a name="dynamic-widget-control-block-allocation-and-de-allocation"></a>Dynamisk widgets kontroll block tilldelning och avallokering 

Om du använder dynamisk kontroll block tilldelning måste du definiera två funktioner som GUIX ska använda för att allokera och frigöra det minne som krävs för dina widgets kontroll block. Funktionerna för minnes hantering skickas till GUIX-system komponenten via ***gx_system_memory_allocator_set*** API-funktionen. Med den här funktionen kan du skicka två funktions pekare till GUIX: den första är en pekare till en minnesallokering och den andra är en pekare till en minnes fri funktion. Oftast ska du implementera dessa funktioner med ThreadX byte-pooler, men med GUIX kan du implementera dynamisk minnes hantering på det sätt som du föredrar.

Allokering av dynamiska widgetar används oftast i filen med program specifikationer för Studio som har genererats, när du väljer alternativet "dynamiskt allokerat" i egenskaps fältet för Studio-widgeten. Du kan dock också använda dynamisk kontroll block tilldelning i ditt program. Om du använder dynamisk kontroll block tilldelning i ditt program bör du anropa API-funktionen ***gx_widget_allocate** _ för att allokera kontroll blocket för widgeten. När du sedan skapar widgeten ska du kontrol lera att du skickar flaggan _ *GX_WIDGET_STYLE_DYNAMICALLY_ALLOCATED** (tillsammans med andra nödvändiga format flaggor) till funktionen för att skapa widgeten. Den här flaggan används för att markera widgeten som dynamiskt allokerad i fältet widgets status. När och om widgeten senare raderas med hjälp av **_gx_widget_delete_**, kommer GUIX att kontrol lera detta status fält och automatiskt anropa funktionen för inallokering av minne för att se till att det inte finns några minnes läckor.

> [!IMPORTANT]
> En widget som skapats med ett dynamiskt tilldelat kontroll block måste skapas med flaggan **GX_WIDGET_STYLE_DYNAMICALLY_ALLOCATED** Style för att förhindra minnes förlust.

### <a name="types"></a>Typer

GUIX innehåller en omfattande, helt funktionell uppsättning inbyggda widgetar. Som tidigare nämnts härleds alla specialiserade widgetar från bas-widgeten. Följande är en lista över inbyggda widgetar i GUIX:

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

Widgetar format består av saker som kant linje egenskaper (upphöjt, nedsänkt, tunn, tjock eller ingen bräda alls) samt egenskaper för vissa typer av widget, enligt listan ovan. Format flaggor för widget är den enklaste metoden för att ändra utseendet på en widget.
Den ursprungliga widgeten är alltid en parameter som skickas till den widgets typ som är en speciell Create-funktion.

### <a name="colors"></a>Färger 

Widgetar ritar sig själva med färger som definierats i tabellen system färg.
Färg-ID: n definieras för arbets ytans bakgrund, standard fyllnings färg för widget, knapp fyllnings färg, fyllnings färg för TextWidget, fönster fyllnings färg och flera andra standard färg värden. Dessutom har **GX_WINDOW** objekt stöd för att visa en bitmapp eller tapet när fönster klienten är ifylld.

Den enklaste metoden att ändra standard färg schema är att använda GUIX Studio och skapa eller definiera ett färg schema som uppfyller dina krav.
Du kan också definiera ditt färg schema manuellt genom att skapa en matris med GX_COLOR värden och anropa funktionen gx_system_color_table_set API.

### <a name="event-notification"></a>Händelse meddelande 

GUIX-händelser är begär Anden som görs till en eller flera widgetar för att utföra en viss åtgärd och aviseringar för att meddela widgetar om användarindata och ändringar i interna system status. Om en widget till exempel får fokus, skickas **GX_EVENT_FOCUS_GAINED** till widgeten via tjänsten ***gx_system_event_send*** API.

Händelser skickas via GUIX-händelse kön och varje händelse är en instans av **GX_EVENT** data strukturen. **GX_EVENT** data strukturen definieras i ***gx_api. h***, men de viktigaste fälten i strukturen är **gx_event_type**, **gx_event_sender**, **gx_event_target** och **gx_event_payload**.

Fältet **gx_event_type** används för att identifiera en viss händelse klass. Händelse typen anger om detta är till exempel en **GX_EVENT_PEN_DOWN** händelse eller en **GX_EVENT_TIMER** -händelse. **Gx_event_payload** är en union av olika data fält och de är inte alla giltiga för varje händelse typ.
Du använder först fältet händelse typ innan du undersöker de andra händelse data fälten.

Fältet **gx_event_sender** innehåller ID: t för widgeten som skapade händelsen om händelsen är ett underordnat widgets meddelande.

Fältet **gx_event_target** kan användas för att dirigera användardefinierade händelser till ett visst fönster eller widget. Om du vill skicka en händelse till ett visst fönster, bör du ge fönstret ett unikt ID-värde (så att det kan identifieras positivt) och när du skapar händelsen placeras värdet för fönster-ID i fältet **gx_event_target** . Om du inte känner till mål-ID: t eller om du bara vill att händelsen ska dirigeras till widgeten med fokus, måste du ange **gx_event_target** fältet till 0.

Slutligen är fältet **gx_event_payload** en union av olika data typer. För **GX_EVENT_PEN_DOWN** -och **GX_EVENT_PEN_UP** -händelser innehåller fältet **gx_event_pointdata** x, y-pixeln pennans position. För timer-händelser innehåller fältet **GX_EVENT_TIMER_ID** ID för den utgångna timern. Andra nytto Last data fält används för andra händelse typer. Den fullständiga listan över fördefinierade händelse typer och deras nytto Last fält definieras i [bilaga E-GUIX händelse beskrivningar](appendix-e.md).

Programmet kan också lägga till egna anpassade händelser som börjar numeriskt efter konstanten **GX_FIRST_APP_EVENT**. Alla händelse nummer efter den här konstanten är reserverade för programmets användning. Programmets händelse hanterare för widget måste naturligtvis ha bearbetning för sådana program händelser.

### <a name="event-processing"></a>Händelse bearbetning 

Det finns en standard funktion för widgets händelse bearbetning för varje widget, med namnet ***gx_<widget-typ>_event_process***. I de flesta fall behöver programmet inte bekymra sig om händelse hanteringen av någon bestämd widget. I situationer där programmet kräver anpassad eller kompletterande händelse bearbetning kan programmet dock åsidosätta standard bearbetnings funktionen med sin egen via GUIX API- ***gx_widget_event_process_set***. Den här funktionen åsidosätter standard funktionen för händelse bearbetning med funktionen process bearbetning som anges i API: et.

> [!IMPORTANT]
> Bearbetnings funktioner för program händelser kan dra nytta av (dvs. inte duplicera bearbetningen) av standard bearbetningen genom att bara anropa standard ***gx_widget_event_process*** bearbetningen direkt.

Händelse bearbetning anropas exklusivt från kontexten för den interna GUIX system tråden. På det här sättet gäller stack kraven för bearbetning av händelse hanteringen bara för GUIX-tråden.

### <a name="implementing-custom-event-processing-example"></a>Implementera anpassad händelse bearbetning (exempel) 

Du kan ange en egen händelse bearbetnings funktion för alla widgetar eller fönster i GUIX-systemet. Om du skapar en egen anpassad widget-typ installerar du normalt din anpassade händelse hanterare i funktionen för att skapa widgeten. Om du bara utökar eller ändrar åtgärden för en befintlig widget eller ett fönster kan du anropa API-funktionen gx_widget_event_process_set när widgeten eller fönstret har skapats. Du kommer nästan alltid att tillhandahålla din egen händelse hantering för toppnivå fönster (även kallade skärmar) för att bearbeta händelser som genererats av dina underordnade kontroller. Bearbetning av händelser som genererats av de underordnade kontrollerna på en skärm är det huvudsakliga sättet som du lägger till funktioner i GUIX-programmet.

Anta till exempel att du definierar en skärm på den översta nivån med namnet "main_menu".
Den här skärmen kan definieras med GUIX Studio, eller så kan du skapa den här skärmen i din program kod. Om du definierar skärmen i GUIX Studio skriver du bara namnet på din händelse hanterare i fältet för Studio-egenskaper för den skärmen, och koden för Studio-genererade specifikationer kommer automatiskt att installera händelse hanteraren. I det här fallet anropar vi den anpassade händelse hanteraren ***main_menu_event_handler*** och bör kodas så här:

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

I exemplet ovan är det viktigt att Observera att för system händelser som **GX_EVENT_SHOW** (händelser som genereras internt för att meddela en widget av en status ändring) måste programmet klara dessa händelser till funktionen grundläggande händelse bearbetning för att säkerställa att den normala bearbetningen sker. Programmet kan sedan lägga till ytterligare logik som du vill. Alla händelser som inte hanteras av programmet (standard fallet ovan) bör också skickas till funktionen grundläggande bearbetning av händelser. Eftersom det här exemplet var för en skärm på den översta nivån baserat på **GX_WINDOW**, är standard funktionen för händelse bearbetning gx_window_event_process.

### <a name="drawing-function"></a>Ritnings funktion 

Alla widgets ritningar utförs separat från händelse hanteringen. Detta är mer effektivt eftersom ritning vanligt vis är kostsamt när det gäller CPU-cykler. Genom att implementera en uppskjuten ritnings algoritm kan alla utestående händelser och associerade visnings ändringar slutföras innan en ritning görs, vilket eliminerar onödigt ritning. Precis som händelse bearbetning finns det en standard ritnings funktion för widget för de flesta widgetar, med namnet ***gx_<widget-typ>_draw***, där xxx är typen av widget. I de flesta fall behöver programmet inte bekymra sig om ritnings funktionen för någon bestämd widget. I situationer där programmet kräver anpassad eller kompletterande ritning kan programmet dock åsidosätta standard ritnings funktionen med sin egen via GUIX API- ***gx_widget_draw_set***. Med den här funktionen kan programmet tillhandahålla en egen anpassad ritnings funktion för alla widgetar. Detta gör att programmet kan definiera alla nya typer av widgetar.

> [!IMPORTANT]
> Program ritnings funktioner kan dra nytta av (dvs. inte duplicera kodningen) för standard ritningen genom att bara anropa den direkt från den åsidosatta ritnings funktionen.

Widgets ritningen anropas exklusivt från kontexten för den interna GUIX system tråden. På så sätt gäller tiden och stack kraven för att utföra ritningen endast för GUIX-tråden.

### <a name="implementing-custom-drawing-example"></a>Implementera anpassad ritning (exempel) 

Ritnings funktionen för alla widgetar refereras till via en indirekt funktions pekare som är medlem i kontroll blocket GX_WIDGET. Om du använder GUIX Studio för att definiera widgeten kan du installera en egen funktions pekare genom att skriva namnet på din funktion i parametern "ritnings funktion" i egenskaperna för widgeten, så kommer Studio att installera funktions pekaren åt dig när widgeten skapas. Om du skapar widgeten i din program kod måste du använda ***gx_widget_draw_set*** API-funktionen för att installera din anpassade ritnings funktion när widgeten har skapats.

I det här exemplet antar vi att du vill anpassa utseendet på en knapp. Knappen kommer att se ut ungefär som en **GX_TEXT_BUTTON**, men vi lägger till en liten grön "LED_ON"-bitmapp i mitten av knappen när knappen trycks ned och små "LED_OFF"-bitmapp när knappen inte är nedtryckt. Vi vill skapa en knapp som ser ut som illustrationerna nedan.

![Skärm bild av den gröna knappen för på.](./media/guix/image4.jpg) anpassad knapp "på"

![Skärm bild av den röda knappen för av.](./media/guix/image5.jpg) anpassad knapp

I det här fallet skulle vi skriva en knapp ritnings funktion som ser ut ungefär så här.

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

## <a name="guix-drawing-context-component"></a>GUIX rit kontext komponent 

Rit kontexten skapas dynamiskt, vid körning, eftersom GUIX utför varje uppdaterings åtgärd på arbets ytan. Rit kontexten sammanfogar arbets ytan, skärm driv rutinen och penseln som används för att utföra de aktuella rit åtgärderna.

Rit kontexten definieras av **GX_DRAW_CONTEXTs** strukturen.
Den här strukturen innehåller variabler som definierar urklippet och vyn av den aktuella ritnings åtgärden, definierar den aktuella arbets ytan och definierar den aktuella skärm driv rutinen som används. **GX_DRAW_CONTEXTs** strukturen innehåller också penseln som används för ritning. Rit kontextens pensel är den medlem som du kommer att arbeta direkt med i dina anpassade ritnings funktioner. Pensel strukturen definieras på det sätt som visas i koden nedan.

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

I fältet **gx_brush_pixelmap** definieras en Pixelmap som ska användas för rektangel-och polygon fyllningar. Den här medlemmen används inte om **gx_brush_style** innehåller **GX_BRUSH_PIXELMAPs** formatet.

Den **gx_brush_font** medlemmen definierar teckensnittet som används för text ritning.
Den **gx_brush_line_pattern** medlemmen definierar mönstret som används för streckade linjer.
Den **gx_brush_style** medlemmen är en uppsättning stil flaggor som kan vara eller tillsammans definiera penselns attribut. Följande pensel format flaggor är tillgängliga.

**GX_BRUSH_OUTLINE**  
**GX_BRUSH_SOLID_FILL**  
**GX_BRUSH_PIXELMAP_FILL**  
**GX_BRUSH_ALIAS**  
**GX_BRUSH_UNDERLINE**  
**GX_BRUSH_ROUND**

Den **gx_brush_width** medlemmen definierar linjen med för linje ritning eller dispositions bredden för ritningen.

Den **gx_brush_line_color** medlemmen definierar förgrunds färgen för linje ritning och text ritning.

Den **gx_brush_fill_color** medlemmen definierar den heltäckande fyllnings färgen som används för form fyllning. Kontext komponenten GUIX innehåller en uppsättning API: er utformade för att göra det mycket enkelt att ändra den aktuella penseln i den aktiva kontexten. Dessa API: er omfattar **gx_context_brush_define**, **gx_context_line_color_set**, **gx_context_fill_color_set**, **gx_context_font_set** och många andra.

Rit kontexten för ett överordnat objekt ärvs av objektets underordnade objekt. I själva verket ärvs en klon av den överordnade ritnings kontexten av de underordnade objekten när deras ritnings funktioner anropas. Det underordnade objektet kan ändra kontexten utan att påverka den överordnade ritningen, men den kan också ärva information från överordnad, till exempel pensel färg och format om du vill.

## <a name="guix-window-component"></a>GUIX-fönster komponent 

Fönster komponenten ansvarar för all fönster bearbetning i GUIX. Ett GUIX-fönster är i grunden ett tydligt visnings områden som kan innehålla en eller flera underordnade widgetar. I GUIX är fönstret faktiskt bara en speciell form av objektet grundläggande widget.

GUIX Windows implementeras på ett objektorienterat sätt med fullständigt stöd för arv. Detta görs med hjälp av ANSI C, vilket resulterar i minsta möjliga minnes-och bearbetnings krav.

GUIX Windows utökar funktionerna i GUIX-widgeten främst genom att lägga till stöd för vågrät och lodrät rullning. GUIX window-objekt kan automatiskt skapa och Visa rullnings lister och svara på inmatade rullnings lister. Flyttbara fönster har även inbyggd händelse hantering så att fönstret kan flyttas eller dras baserat på Penn ingångs händelser.
Slutligen svarar GUIX Window på att ta emot fokus genom att flytta fönstret till början av fönstret Z-ordning.

GUIX Window upprätthåller begreppet *klient område*, som är den inre delen av fönstret när fönster kant linjerna och icke-klient objekt, till exempel rullnings lister, tas bort från det tillgängliga området. Underordnade widgetar för klient området klipps ut mot fönstrets klient del, medan icke-klientdatorer, till exempel rullnings lister, som rullnings lister kan rita utanför klient området, men fortfarande beskärs till fönstrets yttre dimensioner.

Windows underhålls i ett överordnat-underordnat sätt, där de underordnade ärver egenskaper från deras överordnade objekt. Underordnade fönster kan ha sina egna underordnade fönster och ärver sedan olika egenskaper från den överordnade. Egenskaperna för ett fönster kan uttryckligen omdefinieras via olika GUIX-API-anrop.

### <a name="window-creation"></a>Skapa fönster 

Ett window-objekt kan skapas vid initiering eller när som helst under körningen av program trådar. Det finns ingen gräns för antalet fönster objekt som kan skapas av ett program. Det finns inte heller någon gräns för antalet underordnade objekt i alla fönster.

### <a name="window-control-block"></a>Fönster kontroll block 

Egenskaperna för varje window-objekt finns i kontroll blocket **GX_WINDOW** och definieras i **_gx_api. h_**. Det minne som krävs för ett window-objekt tillhandahålls av programmet och kan placeras var som helst i minnet. Det är dock vanligt att göra fönstret objekt kontroll blockera en global struktur genom att definiera den utanför omfånget för en funktion.

### <a name="root-window"></a>Rot fönster 

GUIX kräver det som kallas för ett rot fönster för varje arbets yta. Rot fönstret är ramlösa och har samma dimensioner som den arbets yta som den är kopplad till. Den används främst som en behållare för alla widgetar och Windows på den första nivån. Rot fönstret skapas vanligt vis av programmet via API-funktionen ***gx_window_root_create***, strax efter att skärmen och arbets ytan har skapats. Om du använder den Studio-genererade funktionen gx_studio_display_configure kan adressen till rot fönstret returneras på den plats som har skickats som den sista parametern för den här funktionen.

Ett rot fönster är som standard icke-flyttbart och i det enklaste fallet är rot fönstret storleken på arbets ytan. Rot fönstret som används ritar visnings bakgrunden, så om du vill ändra visnings bakgrunds färgen eller Visa bakgrunds tapeter, tilldelar du en färg eller ett Skriv bords underlägg till rot fönstret.

Om ett rot fönster är flyttbart, flyttas det inte genom att ändra placeringen på arbets ytan som ett underordnat fönster, men genom att flytta själva arbets ytan.
Med den här funktionen kan GUIX-rot fönstret använda maskin vara som stöder flera ramtyper med maskin varu förskjutnings registreringar.

### <a name="background"></a>Bakgrund 

Fönster bakgrunder är antingen solida färger eller bitmappsbilder. Det finns en standard fönster bakgrund på system nivå som tillhandahåller standardinställningen för den ursprungliga uppsättningen Windows. Naturligtvis kan alla fönster bakgrunder ändras via GUIX-API: et.

Om du vill ändra den solida färg bakgrunden i ett fönster använder du ***gx_widget_fill_color_set*** API. Om du vill tilldela ett bakgrunds-skrivbordsunderlägg till ett fönster använder du ***gx_window_wallpaper_set*** API.

### <a name="scrolling"></a>Rullning 

GUIX stöder standard fönster rullning när det utrymme som krävs för att Visa fönstrets underordnade är större än den aktuella storleken för fönstret, vågrätt och/eller lodrätt. Om du vill aktivera bläddring måste programmet skapa önskade rullnings lister och koppla dem till fönstret.

GUIX Window-komponenten innehåller en standard rullnings implementering som baseras på storleken på fönstrets klient områden och omfattningen av alla underordnade widgetar. Program kan också tillhandahålla egen rullnings implementering och tolkning genom att åsidosätta den ***gx_window_scroll_info_get*** funktionen för ett visst fönster.

### <a name="event-notification"></a>Händelse meddelande 

Händelse bearbetnings funktionen för standard fönster skiljer sig från GX_WIDGET händelse bearbetning främst vid hantering av rullnings-och storleks händelser. GX_WINDOW tillhandahållna defalt-hanterare för rullning och storleks händelser.

Programmet kan också lägga till egna anpassade händelser som börjar numeriskt efter konstanten **GX_FIRST_APP_EVENT**. Alla händelse nummer efter den här konstanten är reserverade för programmets användning. Naturligtvis måste programmets fönster händelse hanterare ha bearbetning för sådana program händelser.

### <a name="event-processing"></a>Händelse bearbetning 

Precis som alla andra typer av widgetar, finns det en standard funktion för händelse bearbetning i varje fönster som heter ***gx_window_event_process***. Du kommer normalt att åsidosätta den här händelse hanterings funktionen med din egen händelse hanterare i Windows som du skapar. Det här är hur du ska svara på händelser och vidta åtgärder baserat på händelser som genererats av underordnade kontroller i fönstret.

Det är viktigt att komma ihåg att anropa bas ***gx_window_event_process*** funktionen för GUIX system händelser om du åsidosätter händelse hanteraren för att tillåta att standard händelse hanteringen inträffar förutom den åtgärd som du lägger till i händelse hanteraren. Om du till exempel tillhandahåller en anpassad hanterare för **GX_EVENT_SHOW** -händelsen och inte skickar den här händelsen till ***gx_window_event_process***, blir fönstret aldrig synligt.
Om du vill ange en anpassad händelse hanterare för ett fönster använder du funktionen ***gx_widget_event_process_set*** för att definiera adressen för din händelse hanterare. Den här funktionen åsidosätter standard funktionen för händelse bearbetning med funktionen process bearbetning som anges i API: et.

> [!IMPORTANT]
> Bearbetnings funktioner för program händelser kan dra nytta av (dvs. inte duplicera bearbetningen) av standard bearbetningen genom att bara anropa standard ***gx_window_event_process*** direkt.

Händelse bearbetning anropas exklusivt från kontexten för den interna GUIX system tråden. På det här sättet gäller stack kraven för bearbetning av händelse hanteringen bara för GUIX-tråden.

## <a name="guix-image-reader-component"></a>GUIX image Reader-komponent 

Komponenten image Reader innehåller verktyg och API-funktioner för att expandera obehandlade komprimerade avbildningar till GUIX Pixelmap-format. RAW-bilddata med JPEG och PNG-format stöds, med ytterligare format reserverade för framtida versioner.

Observera att för de flesta GUIX-program krävs inte avbildnings läsar komponenten GUIX. De flesta program är beroende av GUIX Studio-programmet för att konvertera JPEG-och PNG-formaterade grafik till gångar till GUIX-kompatibla **GX_PIXELMAP** resurser. GUIX image Reader-komponenten används när RAW Graphics-till gångarna bara är känd vid körning eller när system lagrings begränsningarna förhindrar lagring av resurser i **GX_PIXELMAP** format. Bild data för JPEG-och PNG-format är i allmänhet mer kompakta än **GX_PIXELMAP** format, men det finns avsevärda körnings kostnader som är kopplade till komprimering och färg rymds konvertering av dessa avbildnings typer dynamiskt.

Om RAW-format JPEG-eller PNG-bilder skickas till gx_canvas_pixelmap_draw API-funktionen, expanderar GUIX dynamiskt och ritar JPEG-eller PNG-data. Observera att detta kommer att ha en betydande negativ inverkan på hastigheten för körnings ritningen och att skicka OFORMATERADe bild data till gx_canvas_pixelmap_draw funktion inte rekommenderas om du inte använder ett maskin varu mål som stöder maskinvarustödd JPEG-eller PNG-dekomprimering.

> [!IMPORTANT]
> Att skicka RAW JPEG-eller PNG-formaterade avbildningar till gx_canvas_pixelmap_draw-API: n ådrar sig betydande körnings kostnader för de flesta mål maskin

Som ett alternativ kan rå JPEG-och PNG-data konverteras till GX_PIXELMAP format vid körning med hjälp av komponenten image Reader.
Pixelmaps som produceras på det här sättet kan användas och ritas precis som Pixelmaps som produceras av Studio och som finns i din resurs fil. Detta gör att ditt program kan utföra bild dekomprimering, rastrering och färg utrymmes konvertering en gång (vanligt vis vid program start) i stället för att utföra dessa åtgärder varje gång bilden ritas.

Komponenten image Reader innehåller:

***gx_image_reader_create***  
***gx_image_reader_palette_set***  
***gx_image_reader_start***

## <a name="guix-animation-component"></a>Komponent för GUIX-animering 

Komponenten GUIX-animering är en uppsättning funktioner och tjänster som används för att automatisera överföring av skärm och widget. Komponenten GUIX-animering stöder tonings-i-, tonar-och rörelse-eller bildtyper-animeringar av alla typer av widgetar.

Animeringar av tonings typer kan stödjas antingen genom att variera det interna alpha-värdet (om **GX_BRUSH_ALPHA_SUPPORT** har Aktiver ATS) eller genom att en samling av widgetar ritas till en separat minnes arbets yta när den sedan blandars med bakgrunden. För maskin varu mål som har stöd för flera maskinvarubaserade grafik lager, uppnås stöd för smidiga tonings effekter med hjälp av den här arbets ytans blandnings metod, ofta med mycket liten processor bandbredd som krävs. För maskin varu mål som inte har stöd för flera grafik lager, kan blandning med GUIX-penselns alpha-värde användas vid körning med 16 BPP och högre färg djup.

Om en animering ska använda en separat arbets yta, innehåller komponenten GUIX-animering API-tjänsten gx_animation_canvas_define för detta ändamål. Andra typer av animering kräver inte en separat arbets yta, men de kommer att använda den om den är tillgänglig. Detta gör den bästa möjliga användningen av underliggande maskin varu stöd för flera maskin varu ytor.

Variablerna som styr en animering definieras av två kontroll block. Först **GX_ANIMATION** kontroll blocket som definierar animeringssekvensen. Animeringssekvensen är den motor som kör den animeringssekvens som du definierar. Du kan använda en enskild animering igen flera gånger för att köra många olika animeringssekvenser. Om du behöver köra flera animeringssekvenser samtidigt kan du skapa flera styrenheter för **GX_ANIMATION** animering.

System komponenten GUIX kan tillhandahålla ett återanvändbart block med **GX_ANIMATION** kontroll strukturer, som kan begäras av programmet när och animering behövs och automatiskt returneras till mediepoolen när animeringssekvensen är klar. Detta frigör programmet från att definiera en **GX_ANIMATION** -struktur statiskt för varje animering som kan implementeras. Storleken på den här poolen med **GX_ANIMATION** strukturer definieras av den konstant **GX_ANIMATION_POOL_SIZE**, som är standardvärdet 6, vilket innebär att som standard 6 samtidiga animeringar kan tilldelas från mediepoolen. Den här konstanten kan naturligtvis anges i huvud filen gx_user. h är mer samtidiga animeringar krävs. Om **GX_ANIMATION_POOL_SIZE** har värdet noll tillhandahåller inte system komponenten GUIX en animeringssekvens eller relaterade tjänster.

Det andra kontroll blocket eller den struktur som används för att definiera en animering är **GX_ANIMATION_INFO** -strukturen. Den här strukturen används för att definiera en viss animeringssekvens. Du skickar den här informations strukturen till din animeringssekvens för att initiera en animeringssekvens med hjälp av gx_animation_start API-tjänsten. **GX_ANIMATION_INFOs** strukturen innehåller följande fält:

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

Den **gx_animation_target** medlemmen definierar den mål-widget som animeringen ska agera på.

Den **gx_animation_parent** medlemmen definierar den överordnade widgeten, om den finns, som mål-widgeten ska kopplas till när animeringssekvensen är klar. Gx_animation_parent är också mottagare av GX_ANIMATION_COMPLETE-händelsen som genereras när en animering har slutförts.

Den **gx_animation_screen_list** medlemmen definierar en widgets lista för bildanimeringar med Penn bildnings skärm. Widge-listan ska avslutas med GX_NULL pekare och varje widget i listan ska ha samma x-, y-dimensioner som gx_animation_parent.

**Gx_animation_style** är en bitmask som definierar vilken typ av animering som ska utföras och associerade alternativ. Animeringens stil flaggor innehåller följande.

| Flagga för animering &nbsp; &nbsp; | Description |
| --- | --- |
| GX_ANIMATION_TRANSLATE | Begär en animering av en bild-eller tonings typ. |
| GX_ANIMATION_SCREEN_DRAG | Begär en Penn indata driven skärm som drar animering. |

Följande flaggor kan användas tillsammans med **SCREEN_DRAG** av typen animeringar.

| Skärm &nbsp; drar &nbsp; flaggor | Description |
| --- | --- |
| GX_ANIMATION_WRAP | Skärm listan ska radbrytas från slut punkt till Start. |
| GX_ANIMATION_HORIZONTAL | Skärm drag tillåts i vågrät riktning.  |
| GX_ANIMATION_VERTICAL | Skärm drag tillåts i lodrät riktning. |

Följande flagga kan användas tillsammans med Översätt animeringar.

| Översätt &nbsp; animeringar &nbsp; flaggor | Description |
| --- | --- |
| GX_ANIMATION_DETACH | Koppla bort animeringens mål från den överordnade animeringen när animeringen är klar. Om målet har tilldelats dynamiskt och skapats av den genererade automatiserade händelse hanteringen i GUIX Studio tas målet bort när det har kopplats från. |
| GX_ANIMATION_TRANSLATE | Typer av animering är timer drivna animeringar. Programmet definierar start-och slut position och inledande och avslutande alfa värde för widgeten mål, och animeringssekvensen skapar en timer för att betjäna och som drivande kraft för att köra animeringen.
| GX_ANIMATION_SCREEN_DRAG | Skiljer sig från **översättnings** animeringarna i att den här typen av animering drivs av Penn indata-händelser. Den här animeringseffekten spårar tillsammans med pekskärmen indata för att dra in mål-widgeten när användaren drar en penna eller en Stylus över indata-pekskärmen. Om du vill använda den här typen av animering ska programmet anropa **_gx_animation_drag_enable_** API för att aktivera den här animeringen. |

**Gx_animation_id** -värdet skickas tillbaka till den överordnade animeringen i fältet event.gx_event_sender i händelsen **GX_ANIMATION_COMPLETE** . Det här värdet används av den överordnade animeringen för att avgöra vilken av flera underordnade animeringar som är rapporteringen slutförd. Värdet kan vara 0 och en animering med ID-värde 0 genererar ingen **ANIMATION_COMPLETE** -händelse alls.

**Gx_animation_start_delay** -värdet är ett GUIX Ticket-antal som indikerar antalet timer-Tick som ska förskjutas efter att **_gx_animation_start_*_ anropas innan animeringen körs. Värdet kan vara 0 om du vill starta animeringen direkt när du anropar _*_gx_animation_start_**.

I fältet **gx_animation_frame_interval** definieras antalet GUIX timer-Tick (en multipel av underliggande OS-Ticket) för fördröjning mellan varje bild ruta i animeringssekvensen. Det minsta värdet är 1.

**Gx_animation_start_position** definierar den övre vänstra start punkten för widgeten mål för översättnings animationer.

**Gx_animation_end_position** definierar den övre vänstra placeringen för mål-widgeten för animering av översättnings typer.

Fältet **gx_animation_start_alpha** definierar den Start arbets ytans alpha-värde för animering av översättnings typer.

I fältet **gx_animation_end_alpha** definieras det sista arbets ytans alfa värde för animering av översättnings typer.

Fältet **gx_animation_steps** definierar hur många steg eller ramar som kontrollanten ska köras för översättnings animationer. Ett stort antal steg ger en jämnare bild och/eller tonings utseende, men kräver också större system bandbredd.

Om du vill implementera animeringseffekter i ditt program måste du först anropa ***gx_animation_create*** för att initiera din animeringssekvens. Om animeringen ska använda en sekundär arbets yta initierar du arbets ytan genom att anropa gx_animation_canvas_define. Sedan bör du initiera **GX_ANIMATION_INFOs** strukturen för att definiera den speciella typ av animering som ska utföras och andra parametrar för animering. Slutligen kan du anropa gx_animation_start för att utlösa animeringssekvensen.

När Controller-kontrollen har slutfört en animeringssekvens, skickar den en **GX_ANIMATION_COMPLETE** händelse till den överordnade widgeten, så att du kan göra alla önskade rensningar av animeringens arbets yta vid den tidpunkten.

## <a name="guix-utility-component"></a>GUIX verktygs komponent 

Verktygs komponenten ansvarar för alla vanliga verktyg funktioner i GUIX. Dessa är vanliga funktioner som är användbara verktyg och kan anropas från var som helst i programmet eller den interna GUIX-koden. Funktioner i verktygs komponenten innehåller följande.

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
