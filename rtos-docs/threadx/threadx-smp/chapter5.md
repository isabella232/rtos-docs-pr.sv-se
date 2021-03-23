---
title: Kapitel 5 – enhets driv rutiner för Azure återställnings tider ThreadX SMP
description: Det här kapitlet innehåller en beskrivning av enhets driv rutiner för Azure återställnings tider ThreadX SMP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: acfb54a25cc8bc27b7d0aaeff48956529d90c9e1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828017"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx-smp"></a>Kapitel 5 – enhets driv rutiner för Azure återställnings tider ThreadX SMP

Det här kapitlet innehåller en beskrivning av enhets driv rutiner för Azure återställnings tider ThreadX SMP. Informationen som presenteras i det här kapitlet är utformad för att hjälpa utvecklare att skriva programspecifika driv rutiner. 

## <a name="device-driver-introduction"></a>Introduktion till driv rutin

Kommunikation med den externa miljön är en viktig komponent i de flesta inbäddade program. Den här kommunikationen sker via maskin varu enheter som är tillgängliga för den inbäddade program varan. De program varu komponenter som ansvarar för att hantera sådana enheter kallas ofta för *enhets driv rutiner*.

Enhets driv rutiner i Embedded är real tids system program beroende av varandra. Detta är sant för två huvudsakliga orsaker: den stora mångfalden av mål maskin vara och de lika stora prestanda kraven för program i real tid. Därför är det praktiskt taget omöjligt att tillhandahålla en gemensam uppsättning driv rutiner som uppfyller kraven för varje program. Av dessa skäl är informationen i det här kapitlet utformad för att hjälpa användare att *Anpassa driv* rutiner för ThreadX SMP-enheter och skriva egna specifika driv rutiner.

## <a name="driver-functions"></a>Driv rutins funktioner

ThreadX SMP enhets driv rutiner består av åtta grundläggande funktionella områden, enligt följande:

- **Driv rutins initiering**
- **Driv rutins kontroll**
- **Driv rutins åtkomst**
- **Driv rutins Indatatyp**
- **Driv rutins utdata**
- **Driv rutins avbrott**
- **Driv rutins status**
- **Driv rutins avslutning**

Med undantag för initiering, är varje funktions områden valfritt. Dessutom är den exakta bearbetningen i varje zon specifika för enhets driv rutinen.

### <a name="driver-initialization"></a>Driv rutins initiering 
Det här funktions avsnittet ansvarar för initiering av den faktiska maskin varu enheten och de interna data strukturerna för driv rutinen. Det är inte tillåtet att anropa andra driv rutins tjänster förrän initieringen är klar.

> [!IMPORTANT]
> Driv Rutinens initierings funktions komponent anropas vanligt vis från **tx_application_define** -funktionen eller från en initierings tråd.

### <a name="driver-control"></a>Driv rutins kontroll 
När driv rutinen har initierats och är klar för drift är det här funktions avsnittet ansvarigt för körnings kontroll. Vanligt vis består körnings kontroll av att göra ändringar i den underliggande maskin varu enheten. Exempel på detta är att ändra överföringshastigheten för en seriell enhet eller att söka efter en ny sektor på en disk.

### <a name="driver-access"></a>Driv rutins åtkomst 
Vissa enhets driv rutiner anropas bara från en enda program tråd. I sådana fall behövs inte det här funktions fältet. I program där flera trådar behöver åtkomst till samtidiga driv rutiner måste dock deras interaktion kontrol leras genom att lägga till tilldelnings-/publicerings anläggningar i enhets driv rutinen. Alternativt kan programmet använda en semafor för att kontrol lera åtkomsten till driv rutinen och undvika extra kostnader i driv rutinen. 

### <a name="driver-input"></a>Driv rutins Indatatyp 
Det här funktions avsnittet ansvarar för all enhets information. Huvud problemen som är kopplade till driv rutins inflödet omfattar vanligt vis hur indatamängden buffras och hur trådar väntar på sådana indatatyper. 

### <a name="driver-output"></a>Driv rutins utdata 
Det här funktions avsnittet ansvarar för all enhets utdata. Huvud problemen som är associerade med driv rutins utdata omfattar vanligt vis hur utdata buffras och hur trådar väntar på att utföra utdata. 

### <a name="driver-interrupts"></a>Driv rutins avbrott 
De flesta real tids system är beroende av maskin varu avbrott för att meddela driv rutinen för enhetens indata, utdata, kontroll och fel händelser. Avbrott ger en garanterad svars tid för sådana externa händelser. I stället för avbrott kan driv rutins program varan regelbundet kontrol lera den externa maskin varan för sådana händelser. Den här tekniken kallas *avsökning*. Det är mindre i real tid än avbrott, men avsökningen kan vara begriplig för vissa mindre real tids program. 

### <a name="driver-status"></a>Driv rutins status 
Detta funktions områden ansvarar för att tillhandahålla körnings status och statistik som är associerad med driv rutins åtgärden. Information som hanteras av detta funktions områden innehåller vanligt vis följande: 
- Aktuell enhets status
- Inkommande byte
- Antal utdata
- Antal enhets fel

### <a name="driver-termination"></a>Driv rutins avslutning 
Det här funktions fältet är valfritt. Det krävs endast om driv rutinen och/eller den fysiska maskin varu enheten måste stängas av. När den har avslut ATS får driv rutinen inte anropas igen förrän den har startats om. 

## <a name="simple-driver-example"></a>Exempel på enkel driv rutin

Ett exempel är det bästa sättet att beskriva en enhets driv rutin. I det här exemplet förutsätter driv rutinen en enkel seriell maskin varu enhet med en konfigurations registrering, en inmatnings registrering och en utmatnings registrering. Det här enkla driv rutins exemplet illustrerar funktions områdena initiering, indata, utdata och avbrott.

### <a name="simple-driver-initialization"></a>Enkel driv Rutins initiering 
***Tx_sdriver_initialize*** funktionen för den enkla driv rutinen skapar två räknar semaforer som används för att hantera driv Rutinens indata-och utdata-åtgärd. Semaforen för indatamängden anges av den inmatade ISR när ett meddelande tas emot av den seriella maskin varu enheten. Därför skapas indatamängds-semaforen med ett inledande antal noll.

I motsatsen anger utdata-semaforen tillgängligheten för den seriella maskin varu registreringen. Den skapas med ett värde på en som anger att sändnings registreringen är tillgänglig först.

Initierings funktionen ansvarar också för att installera avbrotts vektor hanterare på låg nivå för aviseringar om indata och utdata. Precis som andra ThreadX-rutiner för SMP-avbrott måste den lägsta nivån anropa ***_tx_thread_context_save** _ innan du anropar ISR-drivrutinen för enkel driv rutin. När ISR-drivrutinen returnerar, måste den lågnivå hanteraren anropa _ * _ _tx_thread_context_restore_* *.

> [!IMPORTANT]
> Det är viktigt att initieringen anropas före någon av de andra driv rutins funktionerna. Normalt kallas driv rutins initiering från **tx_application_define**.

Se bild 9 på sidan 306 för initierings käll koden för den enkla driv rutinen.

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
**BILD 9. Enkel driv Rutins initiering**

### <a name="simple-driver-input"></a>Enkel driv Rutins Indatatyp 
Inmatade för enkla driv rutins Center kring semaforen för indatamängden. När ett avbrotts meddelande för seriell enhet tas emot anges indatamängden. Om en eller flera trådar väntar på ett kort från driv rutinen fortsätter tråden att vänta den längsta tiden. Om inga trådar väntar, förblir semaforen bara inställd tills en tråd anropar funktionen för enhets ingång.

Det finns flera begränsningar för den enkla hantering av driv rutiner. Det viktigaste är möjligheten att släppa indatavärden. Detta kan bero på att det inte går att mata in indataportar som kommer innan föregående tecken bearbetas. Detta hanteras enkelt genom att lägga till en buffert för inmatade Character.

> [!IMPORTANT]
> Endast trådar får anropa funktionen **tx_sdriver_input** .

Bild 10 visar käll koden som är kopplad till enkel driv rutins Indatatyp.

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
**BILD 10. Enkel driv Rutins Indatatyp**

### <a name="simple-driver-output"></a>Enkla driv Rutins utdata 
Bearbetning av utdata använder semaforen för utdata till signal när den seriella enhetens sändnings register är kostnads fri. Innan ett utmatnings avstånd skrivs till enheten hämtas utdata-semaforen. Om den inte är tillgänglig är den tidigare överföringen inte slutförd ännu.

Den ISR-uteffekten ansvarar för hantering av avbrotts överföringen. Bearbetning av de utgångna ISR-beloppen för att ställa in semaforen för utdata och därmed tillåta utdata från ett annat.

> [!IMPORTANT]
> Endast trådar får anropa funktionen **tx_sdriver_output** .

Bild 11 visar käll koden som är kopplad till enkla driv rutins utdata.

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
**BILD 11. Enkla driv Rutins utdata**

### <a name="simple-driver-shortcomings"></a>Brister i enkla driv rutiner 
Den här enkla driv rutins exempel illustrerar den grundläggande idén med en ThreadX SMP-drivrutin. Men eftersom den enkla enhets driv rutinen inte hanterar DataBuffer eller eventuella problem, representerar den inte fullständigt verkliga SMP-drivrutiner för ThreadX. I följande avsnitt beskrivs några av de mer avancerade problem som är associerade med enhets driv rutiner.

## <a name="advanced-driver-issues"></a>Problem med avancerad driv rutin

Som tidigare nämnts har enhets driv rutinerna krav som unika som program. Vissa program kan kräva en enorma mängd databuffation, medan ett annat program kan kräva optimerad driv rutins ISR: er på grund av enhets avbrott med hög frekvens.

### <a name="io-buffering"></a>I/O-buffring 
Databuffring i inbäddade program i real tid kräver avsevärd planering. En del av designen styrs av den underliggande maskin varu enheten. Om enheten tillhandahåller grundläggande byte i/O är en enkel cirkulär buffert förmodligen i ordning. Men om enheten tillhandahåller block-, DMA-eller paket-I/O är ett buffertminne förmodligen motiverat. 

### <a name="circular-byte-buffers"></a>Cirkelformade byte-buffertar 
Cirkelformade byte-buffertar används vanligt vis i driv rutiner som hanterar en enkel seriell maskin varu enhet som en UART. Två cirkelformade buffertar används oftast i sådana situationer – en för indata och en för utdata.

Varje cirkulär byte-buffert består av ett byte minnes utrymme (vanligt vis en matris med UCHARs), en Läs pekare och en Skriv pekare. En buffert anses vara tom när Läs pekaren och skriv pekarna hänvisar till samma minnes plats i bufferten. Driv rutins initiering anger både läsa-och skrivbara pekare till Start adressen för bufferten.

### <a name="circular-buffer-input"></a>Cirkulära buffer-ingångar 
Indatabufferten används för att lagra tecken som kommer innan programmet är redo för dem. När ett indatavärde tas emot (vanligt vis i ett Interrupt Service Routine), hämtas det nya specialtecknet från maskin varu enheten och placeras i indatabufferten vid den plats som pekas på av skriv pekaren. Skriv pekaren är sedan avancerad till nästa position i bufferten. Om nästa position är i slutet av bufferten anges skriv pekaren till början av bufferten. Kön med fullständigt tillstånd hanteras genom att skriva pekare avbryts om den nya skriv pekaren är samma som Läs pekaren.

Begär Anden om programinspelnings-byte till driv rutinen kontrollerar först Läs-och skriv pekarna för indatabufferten. Om Läs-och skriv pekarna är identiska är bufferten tom. Annars, om Läs pekaren inte är densamma, kopieras den byte som pekas av Läs pekaren från indatabufferten och Läs pekaren är avancerad till nästa buffertplats. Om den nya Läs pekaren överskrider buffertens slut återställs den till början. Bild 12 visar logiken för den cirkelformade indatabufferten.

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
**FIGUR 12. Logik för cirkulär inmatad buffert**

> [!IMPORTANT]
> För en tillförlitlig åtgärd kan det vara nödvändigt att utelåsning av avbrott vid manipulering av Läs-och skriv pekarna för både indata och utdata av cirkelformade buffertar.

### <a name="circular-output-buffer"></a>Cirkulär utdatabufferten 
Utdatabufferten används för att lagra tecken som har anlänt för utdata innan maskin varan har skickat tidigare byte. Bearbetning av utdatabufferten fungerar på samma sätt som bearbetningen av indata-buffring, förutom att överföringen av avbrotts processen ändrar utdata till Läs-och utdata-pekaren, medan begäran om program utdata använder skriv pekaren för utdata. Annars är bearbetningen av utdatabufferten densamma. Figuren 13shows Logic för den cirkelformade utdatabufferten.

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
**FIGUR 13. Logik för cirkelformad utdatabuffert**

### <a name="buffer-io-management"></a>I/O-hantering för buffert 
För att förbättra prestandan hos inbäddade mikroprocessorer, skickar många enheter för kring utrustning till och tar emot data med buffertar som tillhandahålls av program vara. I vissa implementeringar kan flera buffertar användas för att skicka eller ta emot enskilda data paket. 

Storlek och plats för I/O-buffertar bestäms av programmet och/eller driv rutins program varan. Normalt är buffertar fasta i storlek och hanteras i en ThreadX SMP-block. Figuren 14describes en typisk I/O-buffert och en ThreadX SMP-programpool som hanterar sin allokering.

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
TypeDef-TX_IO_BUFFER består av två pekare. ***Tx_next_packet** _-pekaren används för att länka flera paket antingen i indata-eller utmatnings listan. Pekaren _ *_tx_next_buffer_** används för att länka samman buffertar som utgör ett enskilt data paket från enheten. Båda dessa pekare är inställda på NULL när bufferten tilldelas från poolen. Dessutom kan vissa enheter kräva ett annat fält för att ange hur mycket av buffertutrymme som faktiskt innehåller data.

### <a name="buffered-io-advantage"></a>Buffrad I/O-fördel 
Vilka är fördelarna med ett I/O-schema för bufferten? Den största fördelen är att data inte kopieras mellan enhets registren och programmets minne. I stället tillhandahåller driv rutinen enheten med en serie buffertar. Fysisk enhet I/O använder det tillhandahållna buffertminne direkt.

Att använda processorn för att kopiera indata eller utgående paket med information är mycket kostsam och bör undvikas i en hög genom strömnings-I/O-situation.

En annan fördel med den buffrade I/O-metoden är att indata-och utmatnings listor inte har fullständiga villkor. Alla tillgängliga buffertar kan finnas i någon av listorna vid ett och samma tillfälle. Detta skiljer sig åt cirkulära buffertar i enkla byte som presenteras tidigare i kapitlet. Var och en hade en fast storlek som bestämts vid kompileringen.

### <a name="buffered-driver-responsibilities"></a>Tillskrivs driv Rutins ansvar 
Buffrade enhets driv rutiner är bara berörda för hantering av länkade listor med I/O-buffertar. En lista med inmatade buffertar underhålls för paket som tas emot innan program varan är klar. En lista över utdatacache bevaras för paket som skickas snabbare än maskin varu enheten kan hantera dem. Figur 15 på sidan 314 visar enkla indata och utdata länkade listor över data paket och de buffertar som utgör varje paket.

![Tillskrivs driv Rutins ansvar](media/image11.png)

**FIGUR 15. Input-Output listor**

Program gränssnittet med buffrade driv rutiner med samma I/O-buffertar. Vid överföring tillhandahåller program vara driv rutinen en eller flera buffertar som ska överföras. När program varan begär indata returnerar driv rutinen indata i i/O-buffertar.

> [!IMPORTANT]
> I vissa program kan det vara praktiskt att bygga ett indatamängds gränssnitt för driv rutin som kräver att programmet utbyter en kostnads fri buffert för en buffert från driv rutinen. Detta kan under lätta vissa bearbetningar av buffertstorleken i driv rutinen.

### <a name="interrupt-management"></a>Avbryt hantering 
I vissa program kan enhetens avbrotts frekvens förhindra skrivning av ISR i C eller att interagera med ThreadX SMP på varje avbrott. Om det till exempel tar 25us att spara och återställa den avbrutna kontexten är det inte lämpligt att utföra en fullständig kontext genom att spara om avbrotts frekvensen var 50uS. I sådana fall används ett litet mängd-ISR för att hantera de flesta av enhetens avbrott. Detta lowoverhead ISR skulle bara interagera med ThreadX SMP vid behov.

En liknande diskussion finns i den avbrotts hanterings diskussionen i slutet av kapitel 3.

> [!NOTE]
> Om avbrott utelåsning ska användas för att skydda kritiska delar av driv rutins kod från driv Rutinens ISR-kod, måste driv rutins koden för tråd nivå alltid köras på samma kärna som ISR bearbetas på. I annat fall bör interna ThreadX SMP-primitiver som TX_DISABLE och TX_RESTORE användas som även har inbyggd inbyggd skydd.

### <a name="thread-suspension"></a>Tråd upphängning 
I exemplet på den enkla driv rutin som tidigare fanns i det här kapitlet, inaktive ras anroparen för Indataporten om ett kort inte är tillgängligt. I vissa program kanske detta inte är acceptabelt.

Om till exempel tråden som ansvarar för bearbetning av indata från en driv rutin också har andra uppgifter, så kommer det förmodligen inte att gå att göra en inaktive ring av driv Rutinens indata. I stället måste driv rutinen anpassas för bearbetning av begäran på samma sätt som andra bearbetnings begär Anden görs i tråden.

I de flesta fall placeras indatabufferten i en länkad lista och ett meddelande om inloggning skickas till trådens indatakö.