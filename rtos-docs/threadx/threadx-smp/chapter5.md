---
title: Kapitel 5 – Enhetsdrivrutiner för Azure RTOS ThreadX SMP
description: Det här kapitlet innehåller en beskrivning av enhetsdrivrutiner för Azure RTOS ThreadX SMP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 706ad47b2c3e7b2979da7262a4de8d681f4fbc53cb1af59a798b34094734060b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792351"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx-smp"></a>Kapitel 5 – Enhetsdrivrutiner för Azure RTOS ThreadX SMP

Det här kapitlet innehåller en beskrivning av enhetsdrivrutiner för Azure RTOS ThreadX SMP. Informationen som presenteras i det här kapitlet är utformad för att hjälpa utvecklare att skriva programspecifika drivrutiner. 

## <a name="device-driver-introduction"></a>Introduktion till enhetsdrivrutiner

Kommunikation med den externa miljön är en viktig del av de flesta inbäddade program. Den här kommunikationen sker via maskinvaruenheter som är tillgängliga för den inbäddade programprogramvaran. De programvarukomponenter som ansvarar för att hantera sådana enheter kallas ofta *enhetsdrivrutiner.*

Enhetsdrivrutiner i inbäddade realtidssystem är programberoende. Detta gäller av två huvudsakliga skäl: den stora variationen av målmaskinvara och de lika stora prestandakrav som gäller för realtidsprogram. Därför är det praktiskt taget omöjligt att tillhandahålla en gemensam uppsättning drivrutiner som uppfyller kraven för varje program. Av dessa skäl är informationen i det här  kapitlet utformad för att hjälpa användarna att anpassa de gamla ThreadX SMP-enhetsdrivrutinerna och skriva egna specifika drivrutiner.

## <a name="driver-functions"></a>Drivrutinsfunktioner

ThreadX SMP-enhetsdrivrutiner består av åtta grundläggande funktionsområden, enligt följande:

- **Initiering av drivrutin**
- **Drivrutinskontroll**
- **Drivrutinsåtkomst**
- **Drivrutinsinmatning**
- **Drivrutinsutdata**
- **Drivrutinsavbrott**
- **Drivrutinsstatus**
- **Avslut av drivrutin**

Med undantag för initiering är varje drivrutinsfunktionsområde valfritt. Dessutom är den exakta bearbetningen i varje område specifik för enhetsdrivrutinen.

### <a name="driver-initialization"></a>Initiering av drivrutin 
Det här funktionsområdet ansvarar för initieringen av den faktiska maskinvaruenheten och drivrutinens interna datastrukturer. Det är inte tillåtet att anropa andra drivrutinstjänster förrän initieringen är klar.

> [!IMPORTANT]
> Drivrutinens initieringsfunktionskomponent anropas vanligtvis från **tx_application_define** eller från en initieringstråd.

### <a name="driver-control"></a>Drivrutinskontroll 
När drivrutinen har initierats och är redo för drift ansvarar det här funktionella området för körningskontroll. Körningskontrollen består vanligtvis av att göra ändringar i den underliggande maskinvaruenheten. Exempel är att ändra överföringsfrekvensen för en seriell enhet eller söka efter en ny sektor på en disk.

### <a name="driver-access"></a>Drivrutinsåtkomst 
Vissa enhetsdrivrutiner anropas bara från en enda programtråd. I sådana fall behövs inte det här funktionsområdet. Men i program där flera trådar behöver samtidig drivrutinsåtkomst måste interaktionen styras genom att lägga till tilldelnings- och lanseringsmöjligheter i enhetsdrivrutinen. Programmet kan också använda en semaphore för att styra drivrutinsåtkomsten och undvika extra omkostnader och problem i drivrutinen. 

### <a name="driver-input"></a>Drivrutinsinmatning 
Det här funktionsområdet ansvarar för alla enhetsindata. De huvudsakliga problem som är associerade med drivrutinsindata omfattar vanligtvis hur indata buffrar och hur trådar väntar på sådana indata. 

### <a name="driver-output"></a>Drivrutinsutdata 
Det här funktionsområdet ansvarar för alla enhetsutdata. De huvudsakliga problem som är associerade med drivrutinsutdata handlar vanligtvis om hur utdata buffrats och hur trådar väntar på att utföra utdata. 

### <a name="driver-interrupts"></a>Drivrutinsavbrott 
De flesta realtidssystem förlitar sig på maskinvaruavbrott för att meddela drivrutinen om enhetsindata, utdata, kontroll och felhändelser. Avbrott ger en garanterad svarstid för sådana externa händelser. I stället för avbrott kan drivrutinsprogramvaran regelbundet kontrollera den externa maskinvaran efter sådana händelser. Den här tekniken kallas *avsökning.* Det är mindre realtid än avbrott, men avsökning kan vara meningsfullt för vissa mindre realtidsprogram. 

### <a name="driver-status"></a>Drivrutinsstatus 
Det här funktionsområdet ansvarar för att tillhandahålla körningsstatus och statistik som är associerad med drivrutinsåtgärden. Information som hanteras av det här funktionsområdet omfattar vanligtvis följande: 
- Aktuell enhetsstatus
- Indatabyte
- Utdatabyte
- Antal enhetsfel

### <a name="driver-termination"></a>Avslut av drivrutin 
Det här funktionella området är valfritt. Det krävs bara om drivrutinen och/eller den fysiska maskinvaruenheten måste stängas av. När den har avslutats får drivrutinen inte anropas igen förrän den har initierats på nytt. 

## <a name="simple-driver-example"></a>Exempel på enkel drivrutin

Ett exempel är det bästa sättet att beskriva en enhetsdrivrutin. I det här exemplet förutsätter drivrutinen en enkel seriell maskinvaruenhet med ett konfigurationsregister, ett indataregister och ett utdataregister. Det här enkla drivrutinsexempel illustrerar initierings-, indata-, utdata- och avbrottsfunktionsområden.

### <a name="simple-driver-initialization"></a>Enkel drivrutinsinitiering 
Funktionen ***tx_sdriver_initialize*** den enkla drivrutinen skapar två räknande semaforer som används för att hantera drivrutinens indata- och utdataåtgärd. Indatasemaforen anges av indata-ISR när ett tecken tas emot av den seriella maskinvaruenheten. Därför skapas indatasemaforen med det inledande antalet noll.

Omvänt anger utdata-semaphore tillgängligheten för seriemaskinvarans överföringsregister. Den skapas med ett värde på ett för att indikera att överföringsregistret är tillgängligt från början.

Initieringsfunktionen ansvarar också för att installera hanteraren för vektoravbrott på låg nivå för indata- och utdatameddelanden. Precis som andra servicerutiner för ThreadX SMP-avbrott måste hanteraren på låg nivå anropa ***_tx_thread_context_save** _ innan den anropar ISR för enkla drivrutiner. När drivrutinens ISR returneras måste hanteraren på låg nivå anropa _*_ _tx_thread_context_restore_**.

> [!IMPORTANT]
> Det är viktigt att initieringen anropas före någon av de andra drivrutinsfunktionerna. Vanligtvis anropas drivrutinsinitiering från **tx_application_define**.

Se bild 9 på sidan 306 för den enkla drivrutinens källkod för initiering.

```C
VOID     tx_sdriver_initialize(VOID)
{

    /* Initialize the two counting semaphores used to control
       the simple driver I/O. */
    tx_semaphore_create(&tx_sdriver_input_semaphore,
                       "simple driver input semaphore", 0);
    tx_semaphore_create(&tx_sdriver_output_semaphore,
                       "simple driver output semaphore", 1);

    /* Setup interrupt vectors for input and output ISRs.
       The initial vector handling should call the ISRs
       defined in this file. */

    /* Configure serial device hardware for RX/TX interrupt
       generation, baud rate, stop bits, etc. */
}
```
**BILD 9. Enkel drivrutinsinitiering**

### <a name="simple-driver-input"></a>Enkla drivrutinsinmatningar 
Indata för den enkla drivrutinen centreras kring indatasemaphore. När ett indataavbrott för en seriell enhet tas emot anges indatasemaphore. Om en eller flera trådar väntar på ett tecken från drivrutinen återupptas tråden som väntar längst. Om inga trådar väntar förblir semaphore helt enkelt inställt tills en tråd anropar enhetens indatafunktion.

Det finns flera begränsningar för enkel hantering av drivrutinsinmatning. Det viktigaste är risken för att släppa indatatecken. Detta är möjligt eftersom det inte finns någon möjlighet att buffra indatatecken som kommer innan det föregående tecknet bearbetas. Detta hanteras enkelt genom att lägga till en buffert för indatatecken.

> [!IMPORTANT]
> Endast trådar tillåts anropa **tx_sdriver_input** funktionen.

Bild 10 visar källkoden som är associerad med enkla drivrutinsinmatningar.

```C
UCHAR     tx_sdriver_input(VOID)
{

    /* Determine if there is a character waiting. If not,
        suspend. */
    tx_semaphore_get(&tx_sdriver_input_semaphore,
                                             TX_WAIT_FOREVER;
    /* Return character from serial RX hardware register. */
    return(*serial_hardware_input_ptr);
}

VOID     tx_sdriver_input_ISR(VOID)
{
    /* See if an input character notification is pending. */
    if (!tx_sdriver_input_semaphore.tx_semaphore_count)
    {
        /* If not, notify thread of an input character. */
        tx_semaphore_put(&tx_sdriver_input_semaphore);
    }
}
```
**BILD 10. Enkla drivrutinsinmatningar**

### <a name="simple-driver-output"></a>Utdata från enkel drivrutin 
Utdatabearbetningen använder utdatasemaforen för att signalera när serieenhetens överföringsregister är kostnadsfritt. Innan ett utdatatecken faktiskt skrivs till enheten hämtas utdatasemaphore. Om den inte är tillgänglig är den tidigare överföringen ännu inte klar.

UTDATA-ISR ansvarar för att hantera överföringens fullständiga avbrott. Bearbetningen av utdata-ISR-mängden till att ställa in utdatasemaforen, vilket tillåter utdata från ett annat tecken.

> [!IMPORTANT]
> Endast trådar tillåts anropa **tx_sdriver_output** funktionen.

Bild 11 visar källkoden som är associerad med enkla drivrutinsutdata.

```C
VOID     tx_sdriver_output(UCHAR alpha)
{

    /* Determine if the hardware is ready to transmit a
       character. If not, suspend until the previous output
        completes. */
    tx_semaphore_get(&tx_sdriver_output_semaphore,
                                            TX_WAIT_FOREVER);
    /* Send the character through the hardware. */
    *serial_hardware_output_ptr = alpha;
}

VOID     tx_sdriver_output_ISR(VOID)
{
    /* Notify thread last character transmit is
        complete. */
    tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
**BILD 11. Utdata för enkel drivrutin**

### <a name="simple-driver-shortcomings"></a>Enkla drivrutinsbrister 
Det här exemplet på en enkel enhetsdrivrutin illustrerar den grundläggande idén med en ThreadX SMP-enhetsdrivrutin. Men eftersom den enkla enhetsdrivrutinen inte behandlar databuffring eller eventuella overheadproblem representerar den inte helt verkliga ThreadX SMP-drivrutiner. I följande avsnitt beskrivs några av de mer avancerade problem som är associerade med enhetsdrivrutiner.

## <a name="advanced-driver-issues"></a>Problem med avancerad drivrutin

Som tidigare nämnts har enhetsdrivrutiner krav som är lika unika som deras program. Vissa program kan kräva en enorm mängd databuffring medan ett annat program kan kräva optimerade drivrutins-ISR:er på grund av enhetsavbrott med hög frekvens.

### <a name="io-buffering"></a>I/O-buffring 
Databuffertning i inbäddade realtidsprogram kräver omfattande planering. En del av designen styrs av den underliggande maskinvaruenheten. Om enheten tillhandahåller grundläggande byte-I/O är en enkel cirkelbuffert förmodligen i ordning. Men om enheten tillhandahåller block-, DMA- eller paket-I/O är ett bufferthanteringsschema förmodligen befogat. 

### <a name="circular-byte-buffers"></a>Cirkulära bytebuffertar 
Cirkulära bytebuffertar används vanligtvis i drivrutiner som hanterar en enkel seriell maskinvaruenhet som en UART. Två cirkelbuffertar används oftast i sådana situationer – en för indata och en för utdata.

Varje cirkelformad bytebuffert består av ett byteminnesområde (vanligtvis en matris med UCHAR), en läs pekare och en skriv pekare. En buffert anses vara tom när läs pekaren och skrivnings pekarna refererar till samma minnesplats i bufferten. Initieringen av drivrutinen anger både läs- och skrivbuffert pekare till buffertens startadress.

### <a name="circular-buffer-input"></a>Cirkelbuffertindata 
Indatabufferten används för att innehålla tecken som tas emot innan programmet är redo för dem. När ett indatatecken tas emot (vanligtvis i en avbrottstjänstrutin) hämtas det nya tecknet från maskinvaruenheten och placeras i indatabufferten på den plats som pekaren pekare pekaren på. Skriv pekaren avancerar sedan till nästa position i bufferten. Om nästa position är förbi buffertens slut anges skriv pekaren till början av bufferten. Det fullständiga villkoret för kön hanteras genom att skrivningspekaren avbryts om den nya skriv pekaren är samma som läs pekaren.

Programindatabytebegäranden till drivrutinen undersöker först indatabuffertens läs- och skriv pekare. Om läs- och skriv pekarna är identiska är bufferten tom. Om läs pekaren inte är densamma kopieras den byte som pekaren mot från indatabufferten och läs pekaren avancerat till nästa buffertplats. Om den nya läs pekaren är förbi slutet av bufferten återställs den till början. Bild 12 visar logiken för cirkelformad indatabuffert.

```C
UCHAR     tx_input_buffer[MAX_SIZE];
UCHAR     tx_input_write_ptr;
UCHAR     tx_input_read_ptr;

/* Initialization.  */
tx_input_write_ptr =  &tx_input_buffer[0];
tx_input_read_ptr =    &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr =  tx_input_write_ptr;
*tx_input_write_ptr++ =  alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr =  &tx_input_buffer[0];  /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr =  save_ptr;  /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
    alpha =  *tx_input_read_ptr++;
    if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
        tx_input_read_ptr =  &tx_input_buffer[0];
}
```
**BILD 12. Logik för cirkulär indatabuffert**

> [!IMPORTANT]
> För tillförlitlig drift kan det vara nödvändigt att låsa avbrott vid manipulering av läs- och skriv pekare för både indata- och utdata cirkulära buffertar.

### <a name="circular-output-buffer"></a>Cirkulär utdatabuffert 
Utdatabufferten används för att innehålla tecken som har anlänt för utdata innan maskinvaruenheten har skickat den tidigare byten. Bearbetning av utdatabuffert liknar bearbetning av indatabufferten, förutom att den fullständiga avbrottsbearbetningen manipulerar utdataläsningspekaren, medan programutdatabegäran använder utdataskrivningspekaren. Annars är utdatabuffertbearbetningen densamma. Bild 13 visar logiken för den cirkelformade utdatabufferten.

```C
UCHAR     tx_output_buffer[MAX_SIZE];
UCHAR     tx_output_write_ptr;
UCHAR     tx_output_read_ptr;

/* Initialization.  */
tx_output_write_ptr =  &tx_output_buffer[0];
tx_output_read_ptr =   &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
    *device_reg =  *tx_output_read_ptr++;
    if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
    tx_output_read_ptr =  &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr =  tx_output_write_ptr;
*tx_output_write_ptr++ =  alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr =  &tx_output_buffer[0];  /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr =  save_ptr;  /* Buffer full!  */
```
**BILD 13. Logik för cirkulär utdatabuffert**

### <a name="buffer-io-management"></a>Buffert-I/O-hantering 
För att förbättra prestanda för inbäddade mikroprocessorer överför och tar många kringutrustningsenheter emot data med buffertar som tillhandahålls av programvara. I vissa implementeringar kan flera buffertar användas för att överföra eller ta emot enskilda datapaket. 

Storleken och platsen för I/O-buffertar bestäms av programmet och/eller drivrutinsprogramvaran. Vanligtvis är buffertar fasta i storlek och hanteras i en ThreadX SMP-blockminnespool. I bild 14 beskrivs en typisk I/O-buffert och en ThreadX SMP-blockminnespool som hanterar deras allokering.

```C
typedef struct TX_IO_BUFFER_STRUCT
{

      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
    struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR  tx_buffer_area[TX_MAX_BUFFER_SIZE];
} TX_IO_BUFFER;

TX_BLOCK_POOL tx_io_block_pool;

/* Create a pool of I/O buffers. Assume that the pointer
   "free_memory_ptr"points to an available memory area that
   is 64 KBytes in size. */

tx_block_pool_create(&tx_io_block_pool,
                  "Sample IO Driver Buffer Pool",
                  free_memory_ptr, 0x10000,
                  sizeof(TX_IO_BUFFER));
```
**BILD 14. I/O-buffert**

### <a name="tx_io_buffer"></a>TX_IO_BUFFER 
Typedef-TX_IO_BUFFER består av två pekare. Pekaren ***tx_next_packet** _ används för att länka flera paket i antingen indata- eller utdatalistan. Pekaren _ *_tx_next_buffer_** används för att länka samman buffertar som utgör ett enskilt datapaket från enheten. Båda dessa pekare är inställda på NULL när bufferten allokeras från poolen. Dessutom kan vissa enheter kräva ett annat fält för att ange hur mycket av buffertområdet som faktiskt innehåller data.

### <a name="buffered-io-advantage"></a>Buffrad I/O-fördel 
Vilka är fördelarna med ett buffert-I/O-schema? Den största fördelen är att data inte kopieras mellan enhetsregister och programmets minne. Drivrutinen ger i stället enheten en serie buffertpekare. Fysisk enhets-I/O använder det angivna buffertminnet direkt.

Att använda processorn för att kopiera indata- eller utdatapaket med information är mycket kostsamt och bör undvikas i alla I/O-situationer med högt dataflöde.

En annan fördel med den buffrade I/O-metoden är att indata- och utdatalistorna inte har fullständiga villkor. Alla tillgängliga buffertar kan finnas i endera listan åt gången. Detta kontrasterar med de enkla cirkelformade bytebuffertar som presenteras tidigare i kapitlet. Var och en hade en fast storlek som bestäms vid kompileringen.

### <a name="buffered-driver-responsibilities"></a>Buffrad drivrutinsansvar 
Buffrade enhetsdrivrutiner hanterar endast länkade listor med I/O-buffertar. En lista över indatabuffertar behålls för paket som tas emot innan programmet är klart. På samma sätt behålls en utdatabuffertlista för paket som skickas snabbare än maskinvaruenheten kan hantera dem. Bild 15 på sidan 314 visar enkla indata- och utdatalänkade listor över datapaket och de buffertar som utgör varje paket.

![Buffrad drivrutinsansvar](media/image11.png)

**BILD 15. Input-Output listor**

Programgränssnitt med buffrade drivrutiner med samma I/O-buffertar. Vid överföring ger programprogramvara drivrutinen en eller flera buffertar att överföra. När programmet begär indata returnerar drivrutinen indata i I/O-buffertar.

> [!IMPORTANT]
> I vissa program kan det vara användbart att skapa ett gränssnitt för drivrutinsinmatning som kräver att programmet utbyter en kostnadsfri buffert för en indatabuffert från drivrutinen. Detta kan minska bearbetningen av buffertallokering i drivrutinen.

### <a name="interrupt-management"></a>Avbrottshantering 
I vissa program kan enhetens avbrottsfrekvens förhindra att ISR skrivs i C eller att interagera med ThreadX SMP vid varje avbrott. Om det till exempel krävs 25us för att spara och återställa den avbrutna kontexten, är det inte lämpligt att utföra en fullständig kontextsräckning om avbrottsfrekvensen var 50us. I sådana fall används ett litet sammansättningsspråk ISR för att hantera de flesta av enhetsavbrotten. Denna ISR med låg huvudnivå interagerar bara med ThreadX SMP vid behov.

En liknande diskussion finns i diskussionen om avbrottshantering i slutet av kapitel 3.

> [!NOTE]
> Om avbrottslåsning ska användas för att skydda viktiga delar av drivrutinskoden från ISR-drivrutinskoden måste drivrutinskoden på trådnivå alltid köras på samma kärna som ISR bearbetas på. Annars bör interna ThreadX SMP-primitiver som TX_DISABLE och TX_RESTORE användas som också har inbyggt skydd mellan kärnor.

### <a name="thread-suspension"></a>Trådavstängning 
I det enkla drivrutinsexempel som presenterades tidigare i det här kapitlet pausar anroparen av indatatjänsten om ett tecken inte är tillgängligt. I vissa program kanske detta inte är acceptabelt.

Om till exempel tråden som ansvarar för bearbetning av indata från en drivrutin också har andra uppgifter, kommer det förmodligen inte att fungera att pausa bara förarindata. Drivrutinen måste i stället anpassas för bearbetning av begäranden på liknande sätt som andra bearbetningsbegäranden görs till tråden.

I de flesta fall placeras indatabufferten i en länkad lista och ett meddelande om indatahändelse skickas till trådens indatakö.