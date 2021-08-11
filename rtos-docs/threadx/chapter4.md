---
title: Kapitel 4 – Beskrivning Azure RTOS ThreadX Services
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS ThreadX-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dabc1603423d8422ed6f8f540f8a06e80d14ec0098c886ca8731ac8ce981f15d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783415"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a>Kapitel 4 – Beskrivning Azure RTOS ThreadX Services

Det här kapitlet innehåller en beskrivning av alla Azure RTOS ThreadX-tjänster i alfabetisk ordning. Deras namn är utformade så att alla liknande tjänster grupperas tillsammans. I avsnittet "Returvärden" i följande beskrivningar påverkas inte värden  i **BOLD** av den TX_DISABLE_ERROR_CHECKING som används för att inaktivera API-felkontroll. medan värden som visas i icke-bold är helt inaktiverade. Dessutom anger ett **"Ja"** under rubriken **"Preemption Possible"** att anrop av tjänsten kan återuppta en tråd med högre prioritet, vilket gör att anropstråden inte kan användas.

## <a name="tx_block_allocate"></a>tx_block_allocate

Allokera minnesblock med fast storlek

### <a name="prototype"></a>Prototyp

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten allokerar ett minnesblock med fast storlek från den angivna minnespoolen. Den faktiska storleken på minnesblocket bestäms när minnespoolen skapas.

> [!IMPORTANT]
> *Det är viktigt att se till att programkoden inte skriver utanför det allokerade minnesblocket. Om detta inträffar uppstår skada i ett intilliggande (vanligtvis efterföljande) minnesblock. Resultaten är oförutsägbara och ofta allvarliga!*

### <a name="parameters"></a>Parametrar

- **pool_ptr** <br>Pekare till en minnesblockpool som skapats tidigare.
- **block_ptr** <br>Pekare till en målblockspekare. Vid lyckad allokering placeras adressen till det allokerade minnesblocket där den här parametern pekar.
- **wait_option** <br>Definierar hur tjänsten beter sig om det inte finns några tillgängliga minnesblock. Väntealternativen definieras på följande sätt:
  - **TX_NO_WAIT** (0x00000000) – om du **TX_NO_WAIT** här alternativet returneras tjänsten omedelbart oavsett om den lyckades eller inte. Detta är det enda giltiga alternativet om tjänsten anropas från en *icke-tråd, t.ex. initiering, timer eller ISR*.
  - **TX_WAIT_FOREVER** (0xFFFFFFF) – Om du **TX_WAIT_FOREVER** här alternativet pausas anropstråden på obestämd tid tills ett minnesblock är tillgängligt.
  - *timeout-värde* (0x00000001 till 0xFFFFFFFE) – Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på ett minnesblock.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS**    (0x00) Lyckad minnesblocksallokering.
- **TX_DELETED**    (0x01) Minnesblockpoolen togs bort när tråden pausades.
- **TX_NO_MEMORY**  (0x10) Kunde inte allokera ett minnesblock inom den angivna väntetiden.
- **TX_WAIT_ABORTED**   (0x1A) Brytning avbröts av en annan tråd, timer eller ISR.
- **TX_POOL_ERROR** (0x02) Pekare för ogiltig minnesblockpool.
- **TX_WAIT_ERROR** (0x04) Ett annat väntealternativ än TX_NO_WAIT har angetts för ett anrop från ett icke-läst.
- **TX_PTR_ERROR**  (0x03) Ogiltig pekare till målpekaren.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;

UINT status;

/* Allocate a memory block from my_pool. Assume that the pool has
already been created with a call to tx_block_pool_create. */

status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
  TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the address of
the allocated block of memory. */
```

### <a name="see-also"></a>Se även

- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_create"></a>tx_block_pool_create

Skapa en pool med minnesblock med fast storlek

### <a name="prototype"></a>Prototyp

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en pool med minnesblock med fast storlek. Det angivna minnesområdet är indelat i så många minnesblock med fast storlek som möjligt med hjälp av formeln:

**total block** = (**totalt antal byte**) / (**blockstorlek** + sizeof(void *))

> [!NOTE]
>*Varje minnesblock innehåller en pekare över overhead som är osynligt för användaren och representeras av "sizeof(void *)" i föregående formel.*

### <a name="parameters"></a>Parametrar

- **pool_ptr**  Pekare till ett kontrollblock för minnesblockpoolen.
- **name_ptr**  Pekare till namnet på minnesblockpoolen.
- **block_size**    Antal byte i varje minnesblock.
- **pool_start**    Startadress för minnesblockpoolen. Startadressen måste justeras efter storleken på ULONG-datatypen.
- **pool_size** Totalt antal byte som är tillgängliga för minnesblockpoolen.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS**    (0x00) Lyckad skapande av minnesblockpool.
- **TX_POOL_ERROR** (0x02) Pekare för ogiltig minnesblockpool. Antingen är pekaren NULL eller så har poolen redan skapats.
- **TX_PTR_ERROR**  (0x03) Ogiltig startadress för poolen.
- **TX_CALLER_ERROR**   (0x13) Ogiltig anropare för den här tjänsten.
- **TX_SIZE_ERROR** (0x05) Storleken på poolen är ogiltig.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_BLOCK_POOL my_pool;

UINT status;

/* Create a memory pool whose total size is 1000 bytes starting at
address 0x100000. Each block in this pool is defined to be 50 bytes
long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
  50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18 memory blocks
of 50 bytes each. The reason there are not 20 blocks in the pool is
because of the one overhead pointer associated with each block. */
```

### <a name="see-also"></a>Se även

- tx_block_allocate, tx_block_pool_delete
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_delete"></a>tx_block_pool_delete

Ta bort minnesblockpool

### <a name="prototype"></a>Prototyp

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den angivna blockminnespoolen. Alla trådar som pausas i väntan på ett minnesblock från den här poolen återupptas och får **en TX_DELETED** returnerar status.

> [!NOTE]
> *Det är programmets ansvar att hantera det minnesområde som är associerat med poolen, som är tillgängligt när den här tjänsten har slutförts. Dessutom måste programmet förhindra användning av en borttagna pool eller dess tidigare minnesblock.*

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till en minnesblockpool som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad borttagning av minnesblockpool.
- **TX_POOL_ERROR** (0x02) Pekare för ogiltig minnesblockpool.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a>Se även

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

Hämta information om blockpoolen

### <a name="prototype"></a>Prototyp

```c
UINT tx_block_pool_info_get(
    TX_BLOCK_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *total_blocks,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BLOCK_POOL **next_pool);
```

### <a name="description"></a>Description

Den här tjänsten hämtar information om den angivna blockminnespoolen.

### <a name="parameters"></a>Parametrar

- **pool_ptr**  Pekare till tidigare skapad minnesblockpool.
- **namn**  Pekare till mål för pekaren till blockpoolens namn.
- **tillgänglig** Pekare till mål för antalet tillgängliga block i blockpoolen.
- **total_blocks**  Pekare till mål för det totala antalet block i blockpoolen.
- **first_suspended**   Pekare till mål för pekaren till tråden som först finns i blockeringslistan för den här blockpoolen.
- **suspended_count**   Pekare till mål för antalet trådar som för närvarande pausas i den här blockpoolen.
- **next_pool** Pekare till mål för pekaren för nästa skapade blockpool.

> [!NOTE]
> *Om du anger TX_NULL en parameter anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Information om lyckad blockpool hämtas.
- **TX_POOL_ERROR** (0x02) Pekare för ogiltig minnesblockpool.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_BLOCK_POOL my_pool;
CHAR *name;
ULONG available;
ULONG total_blocks;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BLOCK_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
  &available,&total_blocks,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Se även

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

Hämta prestandainformation för blockpooler

### <a name="prototype"></a>Prototyp

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om den angivna minnesblockpoolen.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med en TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO* för **att** *den här tjänsten ska returnera prestandainformation.*

### <a name="parameters"></a>Parametrar

- **pool_ptr**  Pekare till tidigare skapad minnesblockpool.
- **allokerar** Pekare till mål för antalet allokerade begäranden som utförts på den här poolen.
- **versioner**  Pekare till mål för antalet lanseringsbegäranden som utförts på den här poolen.
- **jäsningar**   Pekare till mål för antalet trådallokeringsavstängningar i den här poolen.
- **tidsgränser**  Pekare till mål för antalet allokerade tidsgränser för låsning i den här poolen.

>[!NOTE]
> *Om du anger TX_NULL för en parameter indikerar det att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS**    (0x00) Lyckade prestanda för blockpooler.
- **TX_PTR_ERROR**  (0x03) Ogiltig pekare för blockpool.
- **TX_FEATURE_NOT_ENABLED**    (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_BLOCK_POOL my_pool;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created block
pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
  &releases,
  &suspensions,
  &timeouts);

/* If status is TX_SUCCESS the performance information was successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

Hämta information om systemprestanda för blockpooler

### <a name="prototype"></a>Prototyp

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om alla minnesblockpooler i programmet.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med en TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO* för **att** *den här tjänsten ska returnera prestandainformation.*

### <a name="parameters"></a>Parametrar

- **allokerar** Pekare till mål för det totala antalet allokerade begäranden som utförts på alla blockpooler.
- **versioner**  Pekare till mål för det totala antalet lanseringsbegäranden som utförts på alla blockpooler.
- **jäsningar**   Pekare till mål för det totala antalet trådallokeringsblock på alla blockpooler.
- **tidsgränser**  Pekare till mål för det totala antalet allokerade tidsgränser för låsning för alla blockpooler.

> [!NOTE]
> *Om du anger TX_NULL för en parameter indikerar det att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad prestanda för blockpoolsystem get.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
ULONG       allocates;
ULONG       releases;
ULONG       suspensions;
ULONG       timeouts;

/* Retrieve performance information on all the block pools in
the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
    &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

Prioritera blockeringslista för blockpooler

### <a name="prototype"></a>Prototyp

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a>Description

Den här tjänsten placerar den tråd med högst prioritet som pausas för ett minnesblock på den här poolen längst fram i spärrlistan. Alla andra trådar finns kvar i samma FIFO-ordning som de pausades i.

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till ett kontrollblock för minnesblockpooler.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad blockpool prioriteras.
- **TX_POOL_ERROR** (0x02) Pekare för ogiltig minnesblockpool.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel
```c
TX_BLOCK_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_block_release call will wake up this thread. */
```

### <a name="see-also"></a>Se även

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_release"></a>tx_block_release

Frigöra minnesblock med fast storlek

### <a name="prototype"></a>Prototyp

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a>Description

Den här tjänsten släpper ett tidigare allokerat block tillbaka till dess associerade minnespool. Om det finns en eller flera trådar som pausas i väntan på minnesblock från den här poolen får den första tråden pausat det här minnesblocket och återupptas.

>[!IMPORTANT]
>*Programmet måste förhindra användning av ett minnesblockområde när det har släppts tillbaka till poolen.*

### <a name="parameters"></a>Parametrar

- **block_ptr** Pekare till det tidigare allokerade minnesblocket.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad minnesblocksutgåning.
- **TX_PTR_ERROR** (0x03) Ogiltig pekare till minnesblock.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;
UINT status;

/* Release a memory block back to my_pool. Assume that the
pool has been created and the memory block has been
allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
to by memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a>Se även

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize

## <a name="tx_byte_allocate"></a>tx_byte_allocate

Allokera byte minne

### <a name="prototype"></a>Prototyp

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten allokerar det angivna antalet byte från den angivna minnesbytepoolen.

> [!IMPORTANT]
> *Det är viktigt att se till att programkoden inte skriver utanför det allokerade minnesblocket. Om detta inträffar uppstår skada i ett angränsande (vanligtvis efterföljande) minnesblock. Resultatet är oförutsägbart och ofta allvarligt!*

> [!NOTE]
> *Prestanda för den här tjänsten är en funktion av blockstorleken och mängden fragmentering i poolen. Därför bör den här tjänsten inte användas under tidskritiska körningstrådar.*

### <a name="parameters"></a>Parametrar

- **pool_ptr** <br>Pekare till en minnesblockpool som skapats tidigare.
- **memory_ptr** <br>Pekare till en målminnes pekare. Vid lyckad allokering placeras adressen till det allokerade minnesområdet där den här parametern pekar på.
- **memory_size** <br>Antal begärda byte.
- **wait_option** <br>Definierar hur tjänsten beter sig om det inte finns tillräckligt med minne tillgängligt. Väntealternativen definieras på följande sätt:
  - **TX_NO_WAIT** (0x00000000) – om du **väljer TX_NO_WAIT** returneras tjänsten omedelbart oavsett om den lyckades eller inte. *Det här är det enda giltiga alternativet om tjänsten anropas från initieringen.*
  - **TX_WAIT_FOREVER** 0xFFFFFFFF) – **om du TX_WAIT_FOREVER** här alternativet inaktiveras anropstråden på obestämd tid tills tillräckligt med minne är tillgängligt.
  - *timeout-värde* (0x00000001 till 0xFFFFFFFE) – Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på minnet.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad minnesallokering.
- **TX_DELETED** (0x01) Minnespoolen togs bort när tråden pausades.
- **TX_NO_MEMORY** (0x10) Det gick inte att allokera minnet inom den angivna väntetiden.
- **TX_WAIT_ABORTED** (0x1A) Brytningen avbröts av en annan tråd, timer eller ISR.
- **TX_POOL_ERROR** (0x02) Pekare för ogiltig minnespool.
- **TX_PTR_ERROR** (0x03) Ogiltig pekare till målpekaren.
- **TX_SIZE_ERROR** (0X05) Den begärda storleken är noll eller större än poolen.
- **TX_WAIT_ERROR** (0x04) Ett annat väntealternativ än TX_NO_WAIT har angetts för ett anrop från en icke-read.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel
```c
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT status;
/* Allocate a 112 byte memory area from my_pool. Assume
that the pool has already been created with a call to
tx_byte_pool_create. */
status = tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
    112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
address of the allocated memory area. */
```

### <a name="see-also"></a>Se även

- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_create"></a>tx_byte_pool_create

Skapa en minnespool med byte

### <a name="prototype"></a>Prototyp

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en minnesbytepool i det angivna området. Till en början består poolen av i princip ett mycket stort ledigt block. Poolen delas dock upp i mindre block när allokeringar görs.

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till ett kontrollblock för minnespooler.
- **name_ptr** Pekare till namnet på minnespoolen.
- **pool_start** Startadress för minnespoolen. Startadressen måste justeras efter storleken på ULONG-datatypen.
- **pool_size** Totalt antal byte som är tillgängliga för minnespoolen.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad minnespoolskapande.
- **TX_POOL_ERROR** (0x02) Pekare för ogiltig minnespool. Pekaren är antingen NULL eller så har poolen redan skapats.
- **TX_PTR_ERROR** (0x03) Ogiltig startadress för poolen.
- **TX_SIZE_ERROR** (0x05) Storleken på poolen är ogiltig.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Create a memory pool whose total size is 2000 bytes
starting at address 0x500000. */
status = tx_byte_pool_create(&my_pool, "my_pool_name",
    (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
allocating memory. */
```

### <a name="see-also"></a>Se även

- tx_byte_allocate
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

Ta bort minnesbytepool

### <a name="prototype"></a>Prototyp

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den angivna minnesbytepoolen. Alla trådar som pausas i väntan på minne från den här poolen återupptas och **får TX_DELETED returnerar** status.

> [!IMPORTANT]
> *Det är programmets ansvar att hantera det minnesområde som är associerat med poolen, som är tillgängligt när den här tjänsten har slutförts. Dessutom måste programmet förhindra användning av en borttagna pool eller minne som tidigare har allokerats från den.*

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till en tidigare skapad minnespool.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad borttagning av minnespoolen.
- **TX_POOL_ERROR** (0x02) Pekare för ogiltig minnespool.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a>Se även

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

Hämta information om bytepoolen

### <a name="prototype"></a>Prototyp

```c
UINT tx_byte_pool_info_get(
    TX_BYTE_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *fragments,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BYTE_POOL **next_pool);
```

### <a name="description"></a>Description

Den här tjänsten hämtar information om den angivna minnesbytepoolen.

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till minnespool som skapats tidigare.
- **namn** Pekare till mål för pekaren till bytepoolens namn.
- **tillgänglig** Pekare till mål för antalet tillgängliga byte i poolen.
- **fragment** Pekare till mål för det totala antalet minnesfragment i bytepoolen.
- **first_suspended** Pekare till målet för pekaren till tråden som först finns i listan över stängningslistor för den här bytepoolen.
- **suspended_count** Pekare till målet för antalet trådar som för närvarande är inaktiverade på den här bytepoolen.
- **next_pool** Pekare till mål för pekaren för nästa skapade bytepool.

> [!NOTE]
> *Ange en TX_NULL för alla parametrar anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Information om lyckad pool hämtas.
- **TX_POOL_ERROR** (0x02) Pekare för ogiltig minnespool.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_BYTE_POOL my_pool;
CHAR *name;
ULONG available;
ULONG fragments;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BYTE_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_byte_pool_info_get(&my_pool, &name,
  &available, &fragments,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Se även

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_info_get"></a>tx_byte_pool_performance_info_get

Hämta prestandainformation för bytepoolen

### <a name="prototype"></a>Prototyp

```c
UINT tx_byte_pool_performance_info_get(
    TX_BYTE_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *fragments_searched, 
    ULONG *merges, 
    ULONG *splits,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om den angivna minnesbytepoolen.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO* har **definierats** *för att den här tjänsten ska returnera prestandainformation.*

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till en tidigare skapad minnesbytepool.
- **allokerar** Pekare till mål för antalet allokerade begäranden som utförts på den här poolen.
- **versioner** Pekare till mål för antalet lanseringsbegäranden som utförts på den här poolen.
- **fragments_searched** Pekare till mål för antalet interna minnesfragment som genomsökts under allokeringsbegäranden för den här poolen.
- **sammanslagningar** Pekare till mål för antalet interna minnesblock som sammanfogas under allokeringsbegäranden för den här poolen.
- **delningar** Pekare till mål för antalet interna minnesblock som har delats (fragment) som skapats under allokeringsbegäranden i den här poolen.
- **jäsningar** Pekare till mål för antalet trådallokeringsavstängningar i den här poolen.
- **tidsgränser** Pekare till mål för antalet allokerade tidsgränser för den här poolen.

> [!NOTE]
> *Ange en TX_NULL för en parameter anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Prestanda för bytepoolen get.
- **TX_PTR_ERROR** (0x03) Felaktig bytepoolspekare.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_BYTE_POOL my_pool;
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created byte
pool. */
status = tx_byte_pool_performance_info_get(&my_pool,
  &fragments_searched,
  &merges, &splits,
  &allocates, &releases,
  &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```
### <a name="see-also"></a>Se även

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

Hämta systemprestandainformation för bytepool

### <a name="prototype"></a>Prototyp

```c
UINT tx_byte_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *fragments_searched, 
    ULONG *merges,
    ULONG *splits, 
    ULONG *suspensions, 
    ULONG *timeouts);
```
### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om alla minnesbytepooler i systemet.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med en* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** för att den här tjänsten ska *returnera prestandainformation.*

### <a name="parameters"></a>Parametrar

- **allokerar** Pekare till mål för antalet allokerade begäranden som utförts på den här poolen.
- **versioner** Pekare till mål för antalet lanseringsbegäranden som utförts på den här poolen.
- **fragments_searched** Pekare till mål för det totala antalet interna minnesfragment som genomsökts under allokeringsbegäranden för alla bytepooler.
- **sammanslagningar** Pekare till mål för det totala antalet interna minnesblock som sammanslags under allokeringsbegäranden för alla bytepooler.
- **delningar** Pekare till mål för det totala antalet interna minnesblock som skapats under allokeringsbegäranden för alla bytepooler.
- **jäsningar** Pekare till mål för det totala antalet trådallokeringsavstängningar för alla bytepooler.
- **tidsgränser** Pekare till mål för det totala antalet allokerade tidsgränser för låsning på alla bytepooler.

> [!NOTE]
> *Om du anger TX_NULL en parameter anger det att parametern inte krävs.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Prestanda för bytepoolen har lyckats.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

 Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all byte pools in the
system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
  &merges, &splits, &allocates, &releases,
  &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

Prioritera listan över stängningsbytepooler

### <a name="prototype"></a>Prototyp

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a>Description

Den här tjänsten placerar den högsta prioritetstråden som pausas för minne på den här poolen längst fram i stängningslistan. Alla andra trådar finns kvar i samma FIFO-ordning som de pausades i.

### <a name="parameters"></a>Parametrar

- **pool_ptr** Pekare till ett kontrollblock för minnespooler.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad minnespool prioriteras.
- **TX_POOL_ERROR** (0x02) Pekare för ogiltig minnespool.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_BYTE_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_byte_release call will wake up this thread,
if there is enough memory to satisfy its request. */
```

### <a name="see-also"></a>Se även

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_release

## <a name="tx_byte_release"></a>tx_byte_release

Frigöra byte tillbaka till minnespoolen

### <a name="prototype"></a>Prototyp

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a>Description

Den här tjänsten släpper ett tidigare allokerat minnesområde tillbaka till dess associerade pool. Om en eller flera trådar pausas i väntan på minne från den här poolen får varje pausad tråd minne och återupptas tills minnet är slut eller tills det inte finns några fler pausade trådar. Den här processen med att allokera minne till pausade trådar börjar alltid med den första tråden pausad.

> [!IMPORTANT]
> *Programmet måste förhindra att minnesområdet används när det har släppts.*

### <a name="parameters"></a>Parametrar

- **memory_ptr** Pekare till det tidigare allokerade minnesområdet.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad minnesutgåning.
- **TX_PTR_ERROR** (0x03) Pekare för ogiltigt minnesområde.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a>Se även

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize

## <a name="tx_event_flags_create"></a>tx_event_flags_create

Skapa händelseflaggor

### <a name="prototype"></a>Prototyp

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skapar en grupp med 32 händelseflaggor. Alla 32 händelseflaggor i gruppen initieras till noll. Varje händelseflagga representeras av en enda bit.

### <a name="parameters"></a>Parametrar

- **group_ptr** Pekare till ett kontrollblock för händelseflaggor.
- **name_ptr** Pekare till namnet på gruppen händelseflaggor.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Skapandet av en händelsegrupp lyckades.
- **TX_GROUP_ERROR** (0x06) Pekare för ogiltig händelsegrupp. Pekaren är **antingen NULL** eller så har händelsegruppen redan skapats.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a>Se även

- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_delete"></a>tx_event_flags_delete

Ta bort händelseflaggor

### <a name="prototype"></a>Prototyp

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den angivna gruppen händelseflaggor. Alla trådar pausas i väntan på händelser från den här gruppen återupptas och får en TX_DELETED returnerar status.

>[!IMPORTANT]
> *Programmet måste se till att en uppsättning meddela återanrop för den här gruppen händelseflaggor har slutförts (eller inaktiverats) innan du tar bort gruppen händelseflaggor. Dessutom måste programmet förhindra all framtida användning av en borttagna händelseflaggor.*

### <a name="parameters"></a>Parametrar

- **group_ptr** Pekare till en tidigare skapad händelseflaggasgrupp.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckade händelseflaggor gruppborttagning.
- TX_GROUP_ERROR (0x06) **Grupppekare** över ogiltiga händelseflaggor.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Delete event flags group. Assume that the group has
already been created with a call to
tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
deleted. */
```

### <a name="see-also"></a>Se även

- tx_event_flags_create
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_get"></a>tx_event_flags_get

Hämta händelseflaggor från händelseflaggor-gruppen

### <a name="prototype"></a>Prototyp

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten hämtar händelseflaggor från den angivna händelseflaggor-gruppen. Varje händelseflaggasgrupp innehåller 32 händelseflaggor. Varje flagga representeras av en enda bit. Den här tjänsten kan hämta en mängd olika kombinationer av händelseflaggor, som valts av indataparametrarna.

### <a name="parameters"></a>Parametrar

- **group_ptr** <br>Pekare till en tidigare skapad händelseflaggasgrupp.
- **requested_flags** <br>32-bitars osignerad variabel som representerar de begärda händelseflaggorna.
- **get_option** <br>Anger om alla eller någon av de begärda händelseflaggorna krävs. Följande är giltiga val:

  - **TX_AND** (0x02)
  - **TX_AND_CLEAR** (0x03)
  - **TX_OR** (0x00)
  - **TX_OR_CLEAR** (0x01)

    Om TX_AND eller TX_AND_CLEAR anger att alla händelseflaggor måste finnas i gruppen. Om TX_OR eller TX_OR_CLEAR anger att en händelseflagga är tillfredsställande. Händelseflaggor som uppfyller begäran rensas (anges till noll) om TX_AND_CLEAR eller TX_OR_CLEAR har angetts.

- **actual_flags_ptr** <br>Pekare till målet där de hämtade händelseflaggorna placeras. Observera att de faktiska flaggor som hämtas kan innehålla flaggor som inte begärdes.
- **wait_option**  <br>Definierar hur tjänsten beter sig om de valda händelseflaggorna inte har angetts. Väntealternativen definieras på följande sätt:
  - **TX_NO_WAIT** (0x00000000) – om du TX_NO_WAIT här alternativet returneras tjänsten omedelbart oavsett om den lyckades eller inte. Det här är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t.ex. initiering, timer eller ISR.
  - **TX_WAIT_FOREVER** tidsgränsvärde (0xFFFFFFFF) – om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills händelseflaggorna är tillgängliga.
  - timeout-värde (0x00000001 till 0xFFFFFFFE) – Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på händelseflaggorna.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckade händelseflaggor hämtar.
- **TX_DELETED** (0x01) Händelseflaggor togs bort när tråden pausades.
- **TX_NO_EVENTS** (0x07) Det gick inte att hämta de angivna händelserna inom den angivna väntetiden.
- **TX_WAIT_ABORTED** (0x1A) Brytningen avbröts av en annan tråd, timer eller ISR.
- TX_GROUP_ERROR (0x06) **Grupppekare** över ogiltiga händelseflaggor.
- **TX_PTR_ERROR** (0x03) Ogiltig pekare för faktiska händelseflaggor.
- **TX_WAIT_ERROR** (0x04) Ett annat väntealternativ än TX_NO_WAIT har angetts för ett anrop från en icke-read.
- **TX_OPTION_ERROR** (0x08) Ogiltigt get-option har angetts.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG actual_events;
UINT status;

/* Request that event flags 0, 4, and 8 are all set. Also,
if they are set they should be cleared. If the event
flags are not set, this service suspends for a maximum of
20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
    TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
actual events obtained. */
```

**Se även**

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

Hämta information om händelseflaggor

**Prototyp**

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

**Beskrivning**

Den här tjänsten hämtar information om den angivna händelseflaggor-gruppen.

**Parametrar**

- **group_ptr** Pekare till ett kontrollblock för händelseflaggor.
- **namn** Pekare till mål för pekaren till händelseflaggorgruppens namn.
- **current_flags** Pekare till mål för de aktuella uppsättningsflaggorna i gruppen händelseflaggor.
- **first_suspended** Pekare till mål för pekaren till tråden som först finns i stängningslistan för den här händelseflaggasgruppen.
- **suspended_count** Pekare till mål för antalet trådar som för närvarande pausas i den här händelseflaggor-gruppen.
- **next_group** Pekare till mål för pekaren för nästa skapade händelseflaggor.

> [!NOTE]
> *Ange en TX_NULL för en parameter anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Information om lyckad händelsegrupp.
- **TX_GROUP_ERROR** (0x06) Pekare för ogiltig händelsegrupp.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_EVENT_FLAGS_GROUP my_event_group;
CHAR *name;
ULONG current_flags;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_EVENT_FLAGS_GROUP *next_group;
UINT status;

/* Retrieve information about the previously created
event flags group "my_event_group." */
status = tx_event_flags_info_get(&my_event_group, &name,
    &current_flags,
    &first_suspended, &suspended_count,
    &next_group);
/* If status equals TX_SUCCESS, the information requested is
valid. */
```
**Se även**

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

Hämta information om gruppprestanda för händelseflaggor

### <a name="prototype"></a>Prototyp

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om den angivna gruppen händelseflaggor.

> [!IMPORTANT]
> *ThreadX-biblioteket och -programmet måste byggas med TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO* **har definierats** *för att den här tjänsten ska returnera prestandainformation.*

### <a name="parameters"></a>Parametrar

- **group_ptr** Pekare till händelseflaggor som skapats tidigare.
- **uppsättningar** Pekare till mål för antalet händelseflaggor anger begäranden som utförs för den här gruppen.
- **hämtar** Pekare till mål för antalet händelseflaggor som hämtar begäranden som utförs på den här gruppen.
- **jäsningar** Pekare till mål för antalet trådhändelseflaggor får stängningar för den här gruppen.
- **tidsgränser** Pekare till mål för antalet händelseflaggor får tidsgränser för låsning i den här gruppen.

> [!NOTE]
> *Ange en TX_NULL för en parameter anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckade händelseflaggor gruppprestanda hämta.
- TX_PTR_ERROR (0x03) **Grupppekare** över ogiltiga händelseflaggor.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_EVENT_FLAGS_GROUP my_event_flag_group;
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created event
flag group. */
status = tx_event_flags_performance_info_get(&my_event_flag_group,
    &sets, &gets, &suspensions,
    &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
retrieved. */
```

### <a name="see-also"></a>Se även

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

Hämta information om prestandasystem

### <a name="prototype"></a>Prototyp

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om alla händelseflaggor i systemet.

> [!IMPORTANT]
> *ThreadX-biblioteket och -programmet måste byggas med TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO* **har definierats** *för att den här tjänsten ska returnera prestandainformation.*

### <a name="parameters"></a>Parametrar

- **uppsättningar** Pekare till mål för det totala antalet händelseflaggor anger begäranden som utförts för alla grupper.
- **hämtar** Pekare till mål för det totala antalet händelseflaggor hämta begäranden som utförts på alla grupper.
- **jäsningar** Pekare till mål för det totala antalet trådhändelseflaggor får stängningar för alla grupper.
- **tidsgränser** Pekare till mål för det totala antalet händelseflaggor får tidsgränser för låsning i alla grupper.

> [!NOTE]
> *Ange en TX_NULL för en parameter anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckade händelser flaggar systemprestanda get.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="example"></a>Exempel

```c
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created event
flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_set"></a>tx_event_flags_set

Ange händelseflaggor i en grupp med händelseflaggor

### <a name="prototype"></a>Prototyp

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a>Description

Den här tjänsten anger eller rensar händelseflaggor i en grupp med händelseflaggor, beroende på det angivna uppsättningsalternativet. Alla pausade trådar vars begäran om händelseflaggor nu är uppfyllda återupptas.

### <a name="parameters"></a>Parametrar

- **group_ptr** <br>Pekare till de tidigare skapade händelseflaggorna gruppkontrollblock.
- **flags_to_set** <br>Anger de händelseflaggor som ska anges eller rensas baserat på det valda uppsättningsalternativet.
- **set_option** <br>Anger om de angivna händelseflaggorna är ANDed eller ORed i de aktuella händelseflaggorna för gruppen. Följande är giltiga val:
  - **TX_AND** (0x02)
  - **TX_OR** (0x00)

  Om TX_AND här alternativet anger att de angivna händelseflaggorna **är OCH** indelade i de aktuella händelseflaggorna i gruppen. Det här alternativet används ofta för att rensa händelseflaggor i en grupp. Annars, om TX_OR har angetts, anges de **angivna** händelseflaggorna med den aktuella händelsen i gruppen.

### <a name="return-values"></a>Returvärden
- **TX_SUCCESS** (0x00) Lyckade händelseflaggor har angetts.
- **TX_GROUP_ERROR** (0x06) Ogiltig pekare till gruppen händelseflaggor.
- **TX_OPTION_ERROR** (0x08) Ogiltigt set-option har angetts.

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Set event flags 0, 4, and 8. */
status = tx_event_flags_set(&my_event_flags_group,
    0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
set and any suspended thread whose request was satisfied
has been resumed. */
```

### <a name="see-also"></a>Se även

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set_notify

## <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

Meddela programmet när händelseflaggor har angetts

### <a name="prototype"></a>Prototyp

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a>Description

Den här tjänsten registrerar en funktion för återanrop av meddelanden som anropas när en eller flera händelseflaggor anges i den angivna gruppen händelseflaggor. Bearbetningen av återanropet av meddelanden definieras av

### <a name="parameters"></a>Parametrar
- **group_ptr** Pekare till händelseflaggor som skapats tidigare.
- **events_set_notify** Pekare till programmets händelseflaggor ange meddelandefunktion. Om det här värdet TX_NULL inaktiveras meddelandet.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad registrering av händelseflaggor anger meddelande.
- TX_GROUP_ERROR (0x06) **Grupppekare** över ogiltiga händelseflaggor.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades med meddelandefunktioner inaktiverade.

### <a name="example"></a>Exempel

```c
TX_EVENT_FLAGS_GROUP my_group;

/* Register the "my_event_flags_set_notify" function for monitoring
event flags set in the event flags group "my_group." */
status = tx_event_flags_set_notify(&my_group, my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
was successfully registered. */
void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)

/* One or more event flags was set in this group! */
```

### <a name="see-also"></a>Se även

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set

## <a name="tx_interrupt_control"></a>tx_interrupt_control

Aktivera och inaktivera avbrott

### <a name="prototype"></a>Prototyp

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar eller inaktiverar avbrott som anges av indataparametern *new_posture*.

> [!NOTE]
> *Om den här tjänsten anropas från en programtråd förblir avbrottsstatusen en del av trådens kontext. Om tråden till exempel anropar den här rutinen för att inaktivera avbrott och sedan pausar, när den återupptas, inaktiveras avbrotten igen.*

> [!WARNING]
> *Den här tjänsten ska inte användas för att aktivera avbrott under initieringen! Detta kan orsaka oförutsägbara resultat.*

### <a name="parameters"></a>Parametrar

- **new_posture** Den här parametern anger om avbrott är inaktiverade eller aktiverade. Juridiska värden omfattar **TX_INT_DISABLE** och **TX_INT_ENABLE**. De faktiska värdena för dessa parametrar är portspecifika. Dessutom kan vissa bearbetningsarkitekturer ha stöd för ytterligare avbrott i inaktiveringsstatusar.

### <a name="return-values"></a>Returvärden
- **tidigare position** Den här tjänsten returnerar den tidigare avbrottsstatusen till anroparen. På så sätt kan användare av tjänsten återställa den tidigare positionen efter att avbrott har inaktiverats.

### <a name="allowed-from"></a>Tillåts från

Trådar, timers och ISR:er

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a>Se även

Ingen

## <a name="tx_mutex_create"></a>tx_mutex_create

Skapa mutex för mutex för mutex

### <a name="prototype"></a>Prototyp

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a>Description

Den här tjänsten skapar en mutex för ömsesidig exkludering mellan trådar för resursskydd.

### <a name="parameters"></a>Parametrar

- **mutex_ptr** Pekare till ett mutex-kontrollblock.
- **name_ptr** Pekare till namnet på mutex.
- **priority_inherit** Anger om mutex stöder prioritetsarv eller inte. Om det här TX_INHERIT stöds arv av prioritet. Men om TX_NO_INHERIT anges stöds inte prioritetsarv av denna mutex.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad mutex-generering.
- **TX_MUTEX_ERROR** (0x1C) Ogiltig mutex-pekare. Antingen är pekaren NULL eller så har mutex redan skapats.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.
- **TX_INHERIT_ERROR** (0x1F) Ogiltig prioritet ärver parametern .

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_MUTEX my_mutex;
UINT status;

/* Create a mutex to provide protection over a
common resource. */
status = tx_mutex_create(&my_mutex,"my_mutex_name",
    TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
use. */
```

### <a name="see-also"></a>Se även

- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_delete"></a>tx_mutex_delete

Ta bort mutex för mutex för mutex

### <a name="prototype"></a>Prototyp

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den angivna mutex. Alla trådar som pausas i väntan på mutex återupptas och får **en TX_DELETED** returnerar status.

> [!NOTE]
> *Det är programmets ansvar att förhindra användningen av en borttagna mutex.*

### <a name="parameters"></a>Parametrar

- **mutex_ptr** Pekare till en tidigare skapad mutex.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad mutex-borttagning.
- **TX_MUTEX_ERROR** (0x1C) Ogiltig mutex-pekare.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a>Se även

- tx_mutex_create
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_get"></a>tx_mutex_get

Skaffa ägarskap för mutex

### <a name="prototype"></a>Prototyp

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker få exklusiv ägarskap för den angivna mutex. Om anropstråden redan äger mutex ökas en intern räknare och en lyckad status returneras.

Om mutex ägs av en annan tråd och den här tråden har högre prioritet och prioritetsarv angavs vid mutex create, höjs den lägre prioritetstrådens prioritet tillfälligt till den anropande trådens prioritet.

> [!NOTE]
> *Prioriteten för tråden med lägre prioritet som äger en mutex med priorityinheritance bör aldrig ändras av en extern tråd under mutex-ägarskap.*

### <a name="parameters"></a>Parametrar

- **mutex_ptr**   <br>Pekare till en tidigare skapad mutex.
- **wait_option** <br>Definierar hur tjänsten beter sig om mutex redan ägs av en annan tråd. Väntealternativen definieras på följande sätt:
  - **TX_NO_WAIT** (0x00000000) – om du TX_NO_WAIT här alternativet returneras tjänsten omedelbart oavsett om den lyckades eller inte. *Det här är det enda giltiga alternativet om tjänsten anropas från initieringen.*
  - **TX_WAIT_FOREVER** tidsgränsvärde (0xFFFFFFFF) – om du **TX_WAIT_FOREVER** här alternativet pausas anropstråden på obestämd tid tills mutex är tillgängligt.
  - timeout-värde (0x00000001 till 0xFFFFFFFE) – Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på mutex.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad mutex get-åtgärd.
- **TX_DELETED** (0x01) Mutex togs bort när tråden pausades.
- **TX_NOT_AVAILABLE** (0x1D) Tjänsten kunde inte bli ägare till mutex inom den angivna väntetiden.
- **TX_WAIT_ABORTED** (0x1A) Brytningen avbröts av en annan tråd, timer eller ISR.
- **TX_MUTEX_ERROR** (0x1C) Ogiltig mutex-pekare.
- **TX_WAIT_ERROR** (0x04) Ett annat väntealternativ än TX_NO_WAIT har angetts för ett anrop från en icke-tråd.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar och timers

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a>Se även

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_info_get"></a>tx_mutex_info_get

Hämta information om mutex

### <a name="prototype"></a>Prototyp

```c
UINT tx_mutex_info_get(
    TX_MUTEX *mutex_ptr, 
    CHAR **name,
    ULONG *count, 
    TX_THREAD **owner,
    TX_THREAD **first_suspended,
    ULONG *suspended_count, 
    TX_MUTEX **next_mutex);
```

### <a name="description"></a>Description

Den här tjänsten hämtar information från angiven mutex.

### <a name="parameters"></a>Parametrar

- **mutex_ptr** Pekare till mutex-kontrollblock.
- **namn** Pekare till mål för pekaren till mutex-namnet.
- **antal** Pekare till mål för ägarskapsantalet för mutex.
- **ägare** Pekare till mål för pekaren för den äger tråden.
- **first_suspended** Pekare till mål för pekaren till tråden som först finns i stängningslistan för denna mutex.
- **suspended_count** Pekare till mål för antalet trådar som för närvarande pausas på denna mutex.
- **next_mutex** Pekare till mål för pekaren för nästa skapade mutex.

> [!NOTE]
> *Om du anger TX_NULL för en parameter indikerar det att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad mutex-informationshämtning.
- **TX_MUTEX_ERROR** (0x1C) Ogiltig mutex-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

**Exempel**

```c
TX_MUTEX my_mutex;
CHAR *name;
ULONG count;
TX_THREAD *owner;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_MUTEX *next_mutex;
UINT status;

/* Retrieve information about the previously created
mutex "my_mutex." */
status = tx_mutex_info_get(&my_mutex, &name,
    &count, &owner,
    &first_suspended, &suspended_count,
    &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Se även

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

Hämta information om mutex-prestanda

### <a name="prototype"></a>Prototyp

```c
UINT tx_mutex_performance_info_get(
    TX_MUTEX *mutex_ptr, 
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om angiven mutex.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med*  * **TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _defined för att den här tjänsten ska returnera prestandainformation.*

### <a name="parameters"></a>Parametrar

- **mutex_ptr** Pekare till mutex som skapats tidigare.
- **puts** Pekare till mål för antalet put-begäranden som utförts på denna mutex.
- **hämtar** Pekare till mål för antalet get-begäranden som utförts på denna mutex.
- **jäsningar** Pekare till mål för antalet tråd-mutex get-stängningar på denna mutex.
- **tidsgränser** Pekare till mål för antalet mutex get låsning timeouts på den här mutex.
- **inversioner** Pekare till mål för antalet trådprioritetsinversioner på denna mutex.
- **arv** Pekare till mål för antalet arvsåtgärder för trådprioritet på denna mutex.

> [!NOTE]
> *Om du anger TX_NULL för en parameter indikerar det att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad mutex-prestanda get.
- **TX_PTR_ERROR** (0x03) Ogiltig mutex-pekare.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_MUTEX my_mutex;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on the previously created
mutex. */
status = tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
    &suspensions, &timeouts, &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

Hämta information om mutex-systemprestanda

### <a name="prototype"></a>Prototyp

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om alla mutexer i systemet.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med en TX_MUTEX_ENABLE_PERFORMANCE_INFO* **för att** *den här tjänsten ska returnera prestandainformation.*

### <a name="parameters"></a>Parametrar

- **puts** Pekare till mål för det totala antalet put-begäranden som utförts på alla mutexes.
- **hämtar** Pekare till mål för det totala antalet get-begäranden som utförts på alla mutexes.
- **jäsningar** Pekare till mål för det totala antalet tråd-mutex få stängningar på alla mutexes.
- **tidsgränser** Pekare till mål för det totala antalet mutex get låsning timeouts på alla mutexes.
- **inversioner** Pekare till mål för det totala antalet trådprioritetsinversioner för alla mutexes.
- **arv** Pekare till mål för det totala antalet arvsåtgärder för trådprioritet på alla mutexes.

> [!NOTE]
> *Om du anger TX_NULL för en parameter indikerar det att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad mutex-systemprestanda get.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on all previously created
mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts,
    &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

Prioritera mutex-stängningslista

### <a name="prototype"></a>Prototyp

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Description

Den här tjänsten placerar den tråd med högst prioritet som pausas för ägarskap av mutex framför uppstängningslistan. Alla andra trådar finns kvar i samma FIFO-ordning som de pausades i.

### <a name="parameters"></a>Parametrar

- **mutex_ptr** Pekare till den tidigare skapade mutex.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad mutex-prioritering.
- **TX_MUTEX_ERROR** (0x1C) Ogiltig mutex-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_MUTEX my_mutex;
UINT status;

/* Ensure that the highest priority thread will receive
ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_mutex_put call that releases ownership of the
mutex will give ownership to this thread and wake it
up. */
```

### <a name="see-also"></a>Se även

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_put

## <a name="tx_mutex_put"></a>tx_mutex_put

Lanseringsägarskap för mutex

### <a name="prototype"></a>Prototyp

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Description

Den här tjänsten nedtar ägarskapsantalet för den angivna mutex. Om ägarskapsantalet är noll görs mutex tillgängligt.

> [!NOTE]
> *Om prioritetsarv valdes när mutex skapades återställs prioriteten för den frigörande tråden till den prioritet som den hade när den ursprungligen fick ägarskap för mutex. Eventuella andra prioritetsändringar som gjorts i utsläppstråden under ägarskapet för mutex kan ångras.*

### <a name="parameters"></a>Parametrar
- mutex_ptr Pekare till den tidigare skapade mutex.

### <a name="return-values"></a>Returvärden
- **TX_SUCCESS** (0x00) Lyckad mutex-version.
- **TX_NOT_OWNED** (0x1E) Mutex ägs inte av anroparen.
- **TX_MUTEX_ERROR** (0x1C) Ogiltig pekare till mutex.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar och timers

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a>Se även

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize

## <a name="tx_queue_create"></a>tx_queue_create

Skapa meddelandekö

### <a name="prototype"></a>Prototyp

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en meddelandekö som vanligtvis används för intertrådskommunikation. Det totala antalet meddelanden beräknas utifrån den angivna meddelandestorleken och det totala antalet byte i kön.

> [!NOTE]
> *Om det totala antalet byte som anges i köns minnesområde inte är jämnt delbart med den angivna meddelandestorleken används inte återstående byte i minnesområdet.*

### <a name="parameters"></a>Parametrar

- **queue_ptr** Pekare till ett meddelandekökontrollblock.
- **name_ptr** Pekare till namnet på meddelandekön.
- **message_size** Anger storleken på varje meddelande i kön. Meddelandestorlekarna sträcker sig från 1 32-bitars ord till 16 32-bitars ord. Giltiga alternativ för meddelandestorlek är numeriska värden från 1 till 16, inklusive.
- **queue_start** Startadress för meddelandekön. Startadressen måste justeras efter storleken på ULONG-datatypen.
- **queue_size** Totalt antal byte som är tillgängliga för meddelandekön.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad skapande av meddelandekö.
- **TX_QUEUE_ERROR** (0x09) Pekare för ogiltig meddelandekö. Pekaren är antingen NULL eller så har kön redan skapats.
- **TX_PTR_ERROR** (0x03) Ogiltig startadress för meddelandekön.
- **TX_SIZE_ERROR** (0x05) Storleken på meddelandekön är ogiltig.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_QUEUE my_queue;
UINT status;

/* Create a message queue whose total size is 2000 bytes
starting at address 0x300000. Each message in this
queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
    4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
for storing 125 messages (2000 bytes/ 16 bytes per
message). */
```

### <a name="see-also"></a>Se även

- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_delete"></a>tx_queue_delete

Ta bort meddelandekö

### <a name="prototype"></a>Prototyp

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den angivna meddelandekön. Alla trådar som pausas i väntan på ett meddelande från den här kön återupptas och får en TX_DELETED returnerar status.

>[!IMPORTANT]
> *Programmet måste se till att alla återanrop för att skicka meddelanden för den här kön slutförs (eller inaktiveras) innan kön tas bort. Dessutom måste programmet förhindra all framtida användning av en borttagna kö.* <br><br>*Det är också programmets ansvar att hantera det minnesområde som är associerat med kön, som är tillgängligt när den här tjänsten har slutförts.*

### <a name="parameters"></a>Parametrar

- **queue_ptr** Pekare till en meddelandekö som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Borttagning av meddelandekö lyckades.
- **TX_QUEUE_ERROR** (0x09) Pekare för ogiltig meddelandekö.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_QUEUE my_queue;
UINT status;

/* Delete entire message queue. Assume that the queue
has already been created with a call to
tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
deleted. */
```

### <a name="see-also"></a>Se även

- tx_queue_create
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_flush"></a>tx_queue_flush

Tomma meddelanden i meddelandekö

### <a name="prototype"></a>Prototyp

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort alla meddelanden som lagras i den angivna meddelandekön.

Om kön är full tas meddelanden för alla inaktiverade trådar bort. Varje pausad tråd återupptas sedan med en returstatus som anger att meddelandet lyckades. Om kön är tom gör den här tjänsten ingenting.

### <a name="parameters"></a>Parametrar

- **queue_ptr** Pekare till en meddelandekö som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Meddelandekön har rensats.
- **TX_QUEUE_ERROR** (0x09) Pekare för ogiltig meddelandekö.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_QUEUE my_queue;
UINT status;

/* Flush out all pending messages in the specified message
queue. Assume that the queue has already been created
with a call to tx_queue_create. */
status = tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
empty. */
```

### <a name="see-also"></a>Se även

- tx_queue_create
- tx_queue_delete
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_front_send"></a>tx_queue_front_send

Skicka meddelande till kön

### <a name="prototype"></a>Prototyp

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skickar ett meddelande till den angivna meddelandeköns frontplats. Meddelandet **kopieras till framför** kön från det minnesområde som anges av käll pekaren.

### <a name="parameters"></a>Parametrar

- **queue_ptr** <br>Pekare till ett kontrollblock för meddelandekö.
- **source_ptr** <br>Pekare till meddelandet.
- **wait_option**  <br>Definierar hur tjänsten beter sig om meddelandekön är full. Väntealternativen definieras på följande sätt:
  - **TX_NO_WAIT** (0x00000000) – om du TX_NO_WAIT en tjänst returneras omedelbart från den här tjänsten oavsett om den lyckades eller inte. *Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd; t.ex. initiering, timer eller ISR.*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) – Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills det finns utrymme i kön.
  - timeout-värde (0x00000001 till 0xFFFFFFFE) – Om du väljer ett numeriskt värde (1–0xFFFFFFFE) anges det maximala antalet timer-tick som ska pausas medan du väntar på att få plats i kön.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad sändning av meddelande.
- **TX_DELETED** (0x01) Meddelandekö togs bort när tråden pausades.
- **TX_QUEUE_FULL** (0x0B) Tjänsten kunde inte skicka ett meddelande eftersom kön var full under den angivna väntetiden.
- **TX_WAIT_ABORTED** (0x1A) Brytningen avbröts av en annan tråd, timer eller ISR.
- **TX_QUEUE_ERROR** (0x09) Pekare för ogiltig meddelandekö.
- **TX_PTR_ERROR** (0x03) Ogiltig käll pekare för meddelande.
- **TX_WAIT_ERROR** (0x04) Ett annat väntealternativ än TX_NO_WAIT angavs för ett anrop från en icke-tråd.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to the front of "my_queue." Return
immediately, regardless of success. This wait
option is used for calls from initialization, timers,
and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
    TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
of the specified queue. */
```

### <a name="see-also"></a>Se även

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_info_get"></a>tx_queue_info_get

Hämta information om kön

### <a name="prototype"></a>Prototyp

```c
UINT tx_queue_info_get(
    TX_QUEUE *queue_ptr, 
    CHAR **name,
    ULONG *enqueued, 
    ULONG *available_storage
    TX_THREAD **first_suspended, 
    ULONG *suspended_count,
    TX_QUEUE **next_queue);
```

### <a name="description"></a>Description

Den här tjänsten hämtar information om den angivna meddelandekön.

### <a name="parameters"></a>Parametrar

- **queue_ptr** Pekare till en meddelandekö som skapats tidigare.
- **namn** Pekare till mål för pekaren till köns namn.
- **iqueued** Pekare till mål för antalet meddelanden som för närvarande finns i kön.
- **available_storage** Pekare till mål för det antal meddelanden som kön för närvarande har utrymme för.
- **first_suspended** Pekare till mål för pekaren till tråden som först finns i stängningslistan för den här kön.
- **suspended_count** Pekare till mål för antalet trådar som för närvarande pausas i den här kön.
- **next_queue** Pekare till mål för pekaren för nästa skapade kö.

> [!NOTE]
> *Om du anger TX_NULL för en parameter indikerar det att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Information om lyckad kö hämta.
- **TX_QUEUE_ERROR** (0x09) Pekare för ogiltig meddelandekö.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_QUEUE my_queue;
CHAR *name;
ULONG enqueued;
ULONG available_storage;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_QUEUE *next_queue;
UINT status;

/* Retrieve information about the previously created
message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
    &enqueued, &available_storage,
    &first_suspended, &suspended_count,
    &next_queue);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Se även

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

Hämta information om köprestanda

### <a name="prototype"></a>Prototyp

```c
UINT tx_queue_performance_info_get(
    TX_QUEUE *queue_ptr,
    ULONG *messages_sent, 
    ULONG *messages_received,
    ULONG *empty_suspensions, 
    ULONG *full_suspensions,
    ULONG *full_errors, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om den angivna kön.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med*  * **TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined för att den här tjänsten ska returnera prestandainformation.*

### <a name="parameters"></a>Parametrar

- **queue_ptr** Pekare till kö som skapats tidigare.
- **messages_sent** Pekare till mål för antalet skickade begäranden som utförts på den här kön.
- **messages_received** Pekare till mål för antalet mottagningsbegäranden som utförts på den här kön.
- **empty_suspensions** Pekare till mål för antalet tomma köstängningar i den här kön.
- **full_suspensions** Pekare till mål för antalet fullständiga stängningar av kön i den här kön.
- **full_errors** Pekare till mål för antalet fullständiga köfel i den här kön.
- **tidsgränser** Pekare till mål för antalet tidsgränser för trådavstängning i den här kön.

> [!NOTE]
> *Om du anger TX_NULL för en parameter indikerar det att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad köprestanda hämta.
- **TX_PTR_ERROR** (0x03) Ogiltig kö pekare.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_QUEUE my_queue;
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on the previously created
queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

Hämta prestandainformation för kösystem

### <a name="prototype"></a>Prototyp

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om alla köer i systemet.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med*  * **TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined för att den här tjänsten ska returnera prestandainformation.*

### <a name="parameters"></a>Parametrar

- **messages_sent** Pekare till mål för det totala antalet skickade begäranden som utförts på alla köer.
- **messages_received** Pekare till mål för det totala antalet mottagningsbegäranden som utförts på alla köer.
- **empty_suspensions** Pekare till mål för det totala antalet tomma köstängningar i alla köer.
- **full_suspensions** Pekare till mål för det totala antalet fullständiga stängningar av kön i alla köer.
- **full_errors** Pekare till mål för det totala antalet fullständiga köfel i alla köer.
- **tidsgränser** Pekare till mål för det totala antalet tidsgränser för trådlåsning i alla köer.

> [!NOTE]
> *Ange en TX_NULL för en parameter anger att parametern inte är obligatorisk.*

**Returvärden**

- **TX_SUCCESS** (0x00) Lyckad prestanda för kösystem get.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on all previously created
queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_prioritize"></a>tx_queue_prioritize

Prioritera köuppstängningslista

### <a name="prototype"></a>Prototyp

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Description

Den här tjänsten placerar den högsta prioritetstråden som pausas för ett meddelande (eller för att placera ett meddelande) i den här kön längst fram i tjänstgöringslistan.

Alla andra trådar finns kvar i samma FIFO-ordning som de pausades i.

### <a name="parameters"></a>Parametrar

- **queue_ptr** Pekare till en meddelandekö som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad kö prioriteras.
- **TX_QUEUE_ERROR** (0x09) Pekare för ogiltig meddelandekö.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_QUEUE my_queue;
UINT status;

/* Ensure that the highest priority thread will receive
the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_queue_send or tx_queue_front_send call made
to this queue will wake up this thread. */
```

### <a name="see-also"></a>Se även

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_receive"></a>tx_queue_receive

Hämta meddelande från meddelandekö

### <a name="prototype"></a>Prototyp

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten hämtar ett meddelande från den angivna meddelandekön. Det hämtade meddelandet **kopieras från kön** till det minnesområde som anges av mål pekaren. Meddelandet tas sedan bort från kön.

> [!IMPORTANT]
> Det angivna målminnesområdet måste vara tillräckligt stort för att innehålla *meddelandet, d.v.s. det meddelandemål som pekade på*  * **destination_ptr** _ _must vara minst lika stor som meddelandestorleken för den här kön. Om målet inte är tillräckligt stort uppstår annars minnesfel i följande minnesområde.*

### <a name="parameters"></a>Parametrar

- **queue_ptr** <br>Pekare till en meddelandekö som skapats tidigare.
- **destination_ptr** <br>Plats för var meddelandet ska kopieras.
- **wait_option** <br>Definierar hur tjänsten beter sig om meddelandekön är tom. Väntealternativen definieras på följande sätt:
  - **TX_NO_WAIT** (0x00000000) – om du TX_NO_WAIT en tjänst returneras omedelbart från den här tjänsten oavsett om den lyckades eller inte. Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd; t.ex. initiering, timer eller ISR.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) – Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills ett meddelande är tillgängligt.
  - timeout-värde (0x00000001 till 0xFFFFFFFE) – Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-tick som ska pausas medan du väntar på ett meddelande.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad hämtning av meddelandet.
- **TX_DELETED** (0x01) Meddelandekö togs bort när tråden pausades.
- **TX_QUEUE_EMPTY** (0x0A) Tjänsten kunde inte hämta ett meddelande eftersom kön var tom under den angivna väntetiden.
- **TX_WAIT_ABORTED** (0x1A) Brytning avbröts av en annan tråd, timer eller ISR.
- **TX_QUEUE_ERROR** (0x09) Pekare för ogiltig meddelandekö.
- **TX_PTR_ERROR** (0x03) Ogiltig mål pekare för meddelande.
- **TX_WAIT_ERROR** (0x04) Ett annat väntealternativ än TX_NO_WAIT har angetts för ett anrop från ett icke-läst.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
empty, suspend until a message is present. Note that
this suspension is only possible from application
threads. */
status = tx_queue_receive(&my_queue, my_message,
    TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
"my_message." */
```

### <a name="see-also"></a>Se även

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_send"></a>tx_queue_send

Skicka meddelande till meddelandekö

### <a name="prototype"></a>Prototyp

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skickar ett meddelande till den angivna meddelandekön. Det skickade meddelandet **kopieras till kön** från det minnesområde som anges av käll pekaren.

### <a name="parameters"></a>Parametrar
- **queue_ptr** <br>Pekare till en meddelandekö som skapats tidigare.
- **source_ptr** <br>Pekare till meddelandet.
- **wait_option** <br>Definierar hur tjänsten beter sig om meddelandekön är full. Väntealternativen definieras på följande sätt:
  - **TX_NO_WAIT** (0x00000000) – om du TX_NO_WAIT en tjänst returneras omedelbart från den här tjänsten oavsett om den lyckades eller inte. Detta är det enda giltiga alternativet om tjänsten anropas från en *icke-tråd, t.ex. initiering, timer eller ISR*.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) – Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills det finns utrymme i kön.
  - timeout-värde (0x00000001 till 0xFFFFFFFE) – Om du väljer ett numeriskt värde (1–0xFFFFFFFE) anges det maximala antalet timer-tick som ska pausas medan du väntar på att få plats i kön.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad sändning av meddelande.
- **TX_DELETED** (0x01) Meddelandekö togs bort när tråden pausades.
- **TX_QUEUE_FULL** (0x0B) Det gick inte att skicka meddelandet eftersom kön var full under den angivna väntetiden.
- **TX_WAIT_ABORTED** (0x1A) Brytning avbröts av en annan tråd, timer eller ISR.
- **TX_QUEUE_ERROR** (0x09) Pekare för ogiltig meddelandekö.
- **TX_PTR_ERROR** (0x03) Ogiltig källpekare för meddelande.
- **TX_WAIT_ERROR** (0x04) Ett annat väntealternativ än TX_NO_WAIT har angetts för ett anrop från ett icke-läst.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
regardless of success. This wait option is used for
calls from initialization, timers, and ISRs. */
status = tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
queue. */
```

**Se även**

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send_notify

## <a name="tx_queue_send_notify"></a>tx_queue_send_notify

Meddela programmet när meddelandet skickas till kön

### <a name="prototype"></a>Prototyp

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a>Description

Den här tjänsten registrerar en återanropsfunktion för meddelanden som anropas när ett meddelande skickas till den angivna kön. Bearbetningen av återanropet av meddelanden definieras av programmet.

>[!NOTE]
> *Programmets återanrop för att skicka meddelanden i kö tillåts inte att anropa något ThreadX-API med ett alternativ för indragning.*

### <a name="parameters"></a>Parametrar

- **queue_ptr** Pekare till kö som skapats tidigare.
- **queue_send_notify** Pekare till programmets funktion för att skicka meddelanden i kön. Om det här värdet TX_NULL inaktiveras meddelandet.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad registrering av meddelande om att kön ska skickas.
- **TX_QUEUE_ERROR** (0x09) Ogiltig köpekare.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades med meddelandefunktioner inaktiverade.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_QUEUE my_queue;
/* Register the "my_queue_send_notify" function for monitoring
messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
    /* A message was just sent to this queue! */
}
```

### <a name="see-also"></a>Se även

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send

## <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

Placera en instans i räkning av semaphore med tak

### <a name="prototype"></a>Prototyp

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a>Description

Den här tjänsten placerar en instans i den angivna inventeringssemaforen, som i verkligheten ökar räkningen med en. Om beräknings-semaphores aktuella värde är större än eller lika med det angivna taket sätts inte instansen och ett TX_CEILING_EXCEEDED-fel returneras.

### <a name="parameters"></a>Parametrar

- **semaphore_ptr** Pekare till semaphore som skapats tidigare.
- **tak** Högsta tillåtna gräns för semaphore (giltiga värden sträcker sig från 1 till 0xFFFFFFFF).

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS (0x00)** Lyckat semaphore-tak.
- **TX_CEILING_EXCEEDED** (0x21) Placera begäran överskrider taket.
- **TX_INVALID_CEILING** (0x22) Ett ogiltigt värde på noll angavs för tak.
- **TX_SEMAPHORE_ERROR** (0x0C) Ogiltig semaphore-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a>Se även

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_create"></a>tx_semaphore_create

Skapa inventerings-semaphore

### <a name="prototype"></a>Prototyp

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a>Description

Den här tjänsten skapar en inventerings-semaphore för synkronisering mellan trådar. Det första antalet semaphore anges som en indataparameter.

### <a name="parameters"></a>Parametrar

- **semaphore_ptr** Pekare till ett semaphore-kontrollblock.
- **name_ptr** Pekare till namnet på semaphore.
- **initial_count** Anger det första antalet för den här semaphore. Juridiska värden sträcker sig från 0x00000000 till 0xFFFFFFFF.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad semaphore-generering.
- **TX_SEMAPHORE_ERROR** (0x0C) Ogiltig semaphore-pekare. Pekaren är NULL eller så har semaphore redan skapats.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Create a counting semaphore whose initial value is 1.
This is typically the technique used to make a binary
semaphore. Binary semaphores are used to provide
protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
    "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
use. */
```

### <a name="see-also"></a>Se även

- tx_semaphore_ceiling_put
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_delete"></a>tx_semaphore_delete

Ta bort räkning semaphore

### <a name="prototype"></a>Prototyp
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den angivna inventeringssemaphore. Alla trådar som pausas i väntan på en semaphore-instans återupptas och får en TX_DELETED returnerar status.

> [!IMPORTANT]
> *Programmet måste se till att ett sätt meddela återanrop för denna semaphore har slutförts (eller inaktiverats) innan du tar bort semaphore. Dessutom måste programmet förhindra all framtida användning av en borttagna semaphore.*

### <a name="parameters"></a>Parametrar

- **semaphore_ptr** Pekare till en semaphore som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad inventering av semaphore-borttagning.
- **TX_SEMAPHORE_ERROR** (0x0C) Semaphore-pekare för ogiltig inventering.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

**Se även**

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_get"></a>tx_semaphore_get

Hämta instans från att räkna semaphore

### <a name="prototype"></a>Prototyp

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten hämtar en instans (ett enda antal) från den angivna inventeringssemaforen. Därför minskas det angivna antalet semaphore med ett.

### <a name="parameters"></a>Parametrar

- **semaphore_ptr** <br>Pekare till en tidigare skapad inventerings-semaphore.
- **wait_option** <br>Definierar hur tjänsten beter sig om det inte finns några instanser av semaphore tillgänglig. Det vill säga att antalet semaphore är noll. Väntealternativen definieras på följande sätt:
  - **TX_NO_WAIT** (0x00000000) – om du TX_NO_WAIT en tjänst returneras omedelbart från den här tjänsten oavsett om den lyckades eller inte. *Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd; t.ex. initiering, timer eller ISR.*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) – Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en semaphore-instans är tillgänglig.
  - timeout-värde (0x00000001 till 0xFFFFFFFE) – Om du väljer ett numeriskt värde (1–0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på en semaphore-instans.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad hämtning av en semaphore-instans.
- **TX_DELETED** (0x01) Räkna semaphore togs bort när tråden pausades.
- **TX_NO_INSTANCE** (0x0D) Service kunde inte hämta en instans av räkna semaphore (semaphore count is zero within the specified time to wait).
- **TX_WAIT_ABORTED** (0x1A) Brytning avbröts av en annan tråd, timer eller ISR.
- **TX_SEMAPHORE_ERROR** (0x0C) Semaphore-pekare för ogiltig inventering.
- **TX_WAIT_ERROR** (0x04) Ett annat väntealternativ än TX_NO_WAIT angavs för ett anrop från en icke-tråd.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Get a semaphore instance from the semaphore
"my_semaphore." If the semaphore count is zero,
suspend until an instance becomes available.
Note that this suspension is only possible from
application threads. */
status = tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
an instance of the semaphore. */
```

### <a name="see-also"></a>Se även

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semahore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

Hämta information om semaphore

### <a name="prototype"></a>Prototyp

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a>Description

Den här tjänsten hämtar information om den angivna semaphore.

### <a name="parameters"></a>Parametrar

- **semaphore_ptr** Pekare till semaphore-kontrollblocket.
- **namn** Pekare till mål för pekaren till semaphores namn.
- **current_value** Pekare till mål för det aktuella antalet semaphore.
- **first_suspended** Pekare till målet för pekaren till tråden som först finns i stängningslistan för den här semaphore.
- **suspended_count** Pekare till målet för antalet trådar som för närvarande pausas på den här semaphore.
- **next_semaphore** Pekare till mål för pekaren för nästa skapade semaphore.

> [!NOTE]
> *Ange en TX_NULL för en parameter anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) informationshämtning.

- **TX_SEMAPHORE_ERROR** (0x0C) Ogiltig semaphore-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_SEMAPHORE my_semaphore;
CHAR *name;
ULONG current_value;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT status;

/* Retrieve information about the previously created
semaphore "my_semaphore." */
status = tx_semaphore_info_get(&my_semaphore, &name,
    &current_value,
    &first_suspended, &suspended_count,
    &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Se även

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

Hämta information om prestanda för semaphore

### <a name="prototype"></a>Prototyp

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om den angivna semaphore.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med*  * **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined för den här tjänsten för att returnera prestandainformation.*

**Parametrar**

-  **semaphore_ptr** Pekare till semaphore som du skapade tidigare.
-  **puts** Pekare till mål för antalet put-begäranden som utförts på den här semaphore.
-  **hämtar** Pekare till mål för antalet get-begäranden som utförts på den här semaphore.
-  **jäsningar** Pekare till mål för antalet trådstängningar i den här semaforen.
-  **tidsgränser** Pekare till mål för antalet timeouter för trådavstängning i den här semaforen.

> [!NOTE]
> *Ange en TX_NULL för en parameter anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckat semaphore-prestanda get.
- **TX_PTR_ERROR** (0x03) Ogiltig semaphore-pekare.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_SEMAPHORE my_semaphore;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created
semaphore. */
status = tx_semaphore_performance_info_get(&my_semaphore, &puts,
    &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

Hämta information om prestanda för semaphore-systemet

### <a name="prototype"></a>Prototyp

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om alla semaforer i systemet.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med*  * **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined för att den här tjänsten ska returnera prestandainformation*

### <a name="parameters"></a>Parametrar

- **puts** Pekare till mål för det totala antalet put-begäranden som utförts på alla semaforer.
- **hämtar** Pekare till mål för det totala antalet get-begäranden som utförts på alla semaforer.
- **jäsningar** Pekare till mål för det totala antalet trådavstängningar i alla semaforer.
- **tidsgränser** Pekare till mål för det totala antalet timeouter för trådavstängning i alla semaforer.

> [!NOTE]
> *Ange en TX_NULL för en parameter anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) få systemprestanda.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created
semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

Prioritera semaphore-stängningslista

### <a name="prototype"></a>Prototyp

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Description

Den här tjänsten placerar tråden med högst prioritet som pausas för en instans av semaphore längst fram i tjänstgöringslistan. Alla andra trådar finns kvar i samma FIFO-ordning som de pausades i.

### <a name="parameters"></a>Parametrar

- **semaphore_ptr** Pekare till en semaphore som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckat semaphore prioritera.
- **TX_SEMAPHORE_ERROR** (0x0C) Semaphore-pekare för ogiltig inventering.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Ensure that the highest priority thread will receive
the next instance of this semaphore. */
status = tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_semaphore_put call made to this semaphore will
wake up this thread. */
```

### <a name="see-also"></a>Se även

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_put

## <a name="tx_semaphore_put"></a>tx_semaphore_put

Placera en instans i räkning av semaphore

### <a name="prototype"></a>Prototyp

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Description

Den här tjänsten placerar en instans i den angivna inventeringssemaforen, som i verkligheten ökar räkningen med en.

> [!NOTE]
> *Om den här tjänsten anropas när semaphore är ettor (OxFFFFFFFF), kommer den nya put-åtgärden att göra att semaphore återställs till noll.*

### <a name="parameters"></a>Parametrar

- **semaphore_ptr** Pekare till det tidigare skapade räknings-semaphore-kontrollblocket.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad semaphore put.
- **TX_SEMAPHORE_ERROR** (0x0C) Ogiltig pekare till att räkna semaphore.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a>Se även

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_get
- tx_semaphore_put_notify

## <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

Meddela programmet när semaphore sätts

### <a name="prototype"></a>Prototyp

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a>Description

Den här tjänsten registrerar en funktion för återanrop av meddelanden som anropas när den angivna semaphore sätts. Bearbetningen av återanropet av meddelanden definieras av programmet.

> [!NOTE]
> *Programmets återanrop av semaphore-meddelanden tillåts inte anropa något ThreadX-API med ett alternativ för indragning.*

### <a name="parameters"></a>Parametrar

- **semaphore_ptr** Pekare till tidigare skapad semaphore.
- **semaphore_put_notify** Pekare till programmets semaphore put notification-funktion. Om det här värdet TX_NULL inaktiveras meddelandet.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad registrering av semaphore put-meddelande.
- **TX_SEMAPHORE_ERROR** (0x0C) Ogiltig semaphore-pekare.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades med meddelandefunktioner inaktiverade.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_SEMAPHORE my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
the put operations on the semaphore "my_semaphore." */
status = tx_semaphore_put_notify(&my_semaphore, my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
was successfully registered. */
void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
    /* The semaphore was just put! */
}
```

### <a name="see-also"></a>Se även

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put

## <a name="tx_thread_create"></a>tx_thread_create

Skapa programtråd

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_create(
    TX_THREAD *thread_ptr,
    CHAR *name_ptr, 
    VOID (*entry_function)(ULONG),
    ULONG entry_input, 
    VOID *stack_start,
    ULONG stack_size, 
    UINT priority,
    UINT preempt_threshold, 
    ULONG time_slice,
    UINT auto_start);
```

### <a name="description"></a>Description

Den här tjänsten skapar en programtråd som startar körningen vid den angivna uppgiftsinmatningsfunktionen. Stacken, prioritet, tröskelvärde för avspärrning och tidssegment är bland de attribut som anges av indataparametrarna. Dessutom anges även trådens inledande körningstillstånd.

**Parametrar**

- **thread_ptr** Pekare till ett trådkontrollblock.
- **name_ptr** Pekare till trådens namn.
- **entry_function** Anger den första C-funktionen för trådkörning. När en tråd returneras från den här postfunktionen placeras den i ett *slutfört* tillstånd och pausas på obestämd tid.
- **entry_input** Ett 32-bitars värde som skickas till trådens inmatningsfunktion första gången den körs. Användningen av dessa indata bestäms uteslutande av programmet.
- **stack_start** Startadress för stackens minnesområde.
- **stack_size** Antal byte i stackens minnesområde. Trådens stackområde måste vara tillräckligt stort för att hantera sitt sämsta funktionsanrop för kapsling och lokal variabelanvändning.
- **prioritet** Numerisk prioritet för tråd. Juridiska värden sträcker sig från 0 till (TX_MAX_PRIORITES-1), där värdet 0 representerar den högsta prioriteten.
- **preempt_threshold** Högsta prioritetsnivå (0 till (TX_MAX_PRIORITIES-1)) för inaktiverad avstängning. Endast prioriteter som är högre än den här nivån tillåts avse den här tråden. Det här värdet måste vara mindre än eller lika med den angivna prioriteten. Ett värde som är lika med trådprioritet inaktiverar tröskelvärdet preemption-.
- **time_slice** Antalet timer tick som den här tråden får köras innan andra färdiga trådar med samma prioritet får en chans att köras. Observera att användning av tröskelvärdet preemption inaktiverar tidsdelicering. Värdena för juridiska tidssegment sträcker sig från 1 till 0xFFFFFFFF (inklusive). Värdet för **TX_NO_TIME_SLICE** (värdet 0) inaktiverar tidsslicering av den här tråden.

  > [!NOTE]
  > *Användning av tidsdeling resulterar i en liten mängd systemkostnader.   Eftersom tidssegmentering endast är användbart i fall där flera trådar delar samma prioritet, bör trådar som har en unik prioritet inte tilldelas en tidssegment.*

- **auto_start** Anger om tråden startar omedelbart eller är i pausat tillstånd. Juridiska alternativ **är TX_AUTO_START** (0x01) och **TX_DONT_START** (0x00). Om TX_DONT_START har angetts måste programmet senare anropa tx_thread_resume för att tråden ska kunna köras.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad trådgenerering.
- **TX_THREAD_ERROR** (0x0E) Ogiltig trådkontrollspekare. Pekaren är antingen NULL eller så har tråden redan skapats.
- **TX_PTR_ERROR** (0x03) Ogiltig startadress för startpunkten eller så är stackområdet ogiltigt, vanligtvis NULL.
- **TX_SIZE_ERROR** (0x05) Storleken på stackområdet är ogiltig. Trådar måste ha minst **TX_MINIMUM_STACK** byte för att köras.
- **TX_PRIORITY_ERROR** (0x0F) Ogiltig trådprioritet, vilket är ett värde utanför intervallet (0 till (TX_MAX_PRIORITIES-1)).
- **TX_THRESH_ERROR** (0x18) Ogiltig preemptionthreshold har angetts. Det här värdet måste vara en giltig prioritet som är mindre än eller lika med den inledande prioriteten för tråden.
- **TX_START_ERROR** (0x10) Ogiltigt val av automatisk start.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_THREAD my_thread;
UINT status;

/* Create a thread of priority 15 whose entry point is
"my_thread_entry". This thread’s stack area is 1000
bytes in size, starting at address 0x400000. The
preemption-threshold is setup to allow preemption of threads
with priorities ranging from 0 through 14. Time-slicing is
disabled. This thread is automatically put into a ready
condition. */
status = tx_thread_create(&my_thread, "my_thread_name",
    my_thread_entry, 0x1234,
    (VOID *) 0x400000, 1000,
    15, 15, TX_NO_TIME_SLICE,
    TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
for execution! */

...

/* Thread’s entry function. When "my_thread" actually
begins execution, control is transferred to this
function. */

VOID my_thread_entry (ULONG initial_input)
{
    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */
    /* The real work of the thread, including calls to
    other function should be called from here! */
    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```

### <a name="see-also"></a>Se även

- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_delete"></a>tx_thread_delete

Ta bort programtråd

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den angivna programtråden. Eftersom den angivna tråden måste vara i ett avslutat eller slutfört tillstånd kan den här tjänsten inte anropas från en tråd som försöker ta bort sig själv.

> [!NOTE]
> *Det är programmets ansvar att hantera det minnesområde som är associerat med trådens stack, som är tillgänglig när den här tjänsten har slutförts. Dessutom måste programmet förhindra användning av en borttagna tråd.*

### <a name="parameters"></a>Parametrar

- **thread_ptr** Pekare till en tidigare skapad programtråd.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad trådborttagning.
- **TX_THREAD_ERROR** (0x0E) Felaktig pekare för programtråd.
- **TX_DELETE_ERROR** (0x11) Angiven tråd är inte i ett avslutat eller slutfört tillstånd.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar och timers

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_THREAD my_thread;
UINT status;

/* Delete an application thread whose control block is
"my_thread". Assume that the thread has already been
created with a call to tx_thread_create. */
status = tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
deleted. */
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

Meddela programmet vid trådinmatning och avsluta

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a>Description

Den här tjänsten registrerar en återanropsfunktion för meddelanden som anropas när den angivna tråden anges eller avslutas. Bearbetningen av återanropet av meddelanden definieras av programmet.

> [!NOTE]
> Programmets återanrop för trådinmatning/avslutsmeddelande tillåts inte att anropa något ThreadX-API med ett alternativ för indragning.

### <a name="parameters"></a>Parametrar

- **thread_ptr** Pekare till tråd som skapats tidigare.
- **entry_exit_notify** Pekare till programmets funktion för trådinmatning/avslutsmeddelande. Den andra parametern i meddelandefunktionen entry/exit anger om det finns en post eller ett avslut. Värdet **TX_THREAD_ENTRY** (0x00) anger att tråden har angetts, medan värdet **TX_THREAD_EXIT** (0x01) anger att tråden har avslutats. Om det här värdet **TX_NULL** inaktiveras meddelandet.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad registrering av trådinmatnings-/avslutsmeddelandefunktionen.
- **TX_THREAD_ERROR** (0x0E) Felaktig trådpekare.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades med meddelandefunktioner inaktiverade.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_THREAD my_thread;
/* Register the "my_entry_exit_notify" function for monitoring
the entry/exit of the thread "my_thread." */
status = tx_thread_entry_exit_notify(&my_thread,
    my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{
    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
        /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
        /* Thread exit! */
}
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_identify"></a>tx_thread_identify

Hämtar pekare till tråd som körs för närvarande

### <a name="prototype"></a>Prototyp

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a>Description

Den här tjänsten returnerar en pekare till den tråd som körs för närvarande. Om ingen tråd körs returnerar den här tjänsten en null-pekare.

> [!NOTE]
> *Om den här tjänsten anropas från en ISR representerar returvärdet tråden som körs innan avbrottshanteraren körs.*

### <a name="parameters"></a>Parametrar

Ingen

### <a name="retuen-values"></a>Återtuensvärden

- **tråd pekare** Pekare till den tråd som körs. Om ingen tråd körs är returvärdet **TX_NULL**.

### <a name="allowed-from"></a>Tillåts från

Trådar och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

TX_THREAD *my_thread_ptr;

```c
TX_THREAD *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr = tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
from that thread or an ISR that interrupted that thread.
Otherwise, this service was called
from an ISR when no thread was running when the
interrupt occurred. */
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_info_get"></a>tx_thread_info_get

Hämta information om tråd

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_info_get(
    TX_THREAD *thread_ptr, 
    CHAR **name,
    UINT *state, 
    ULONG *run_count,
    UINT *priority,
    UINT *preemption_threshold,
    ULONG *time_slice,
    TX_THREAD **next_thread,
    TX_THREAD **suspended_thread);
```

### <a name="description"></a>Description

Den här tjänsten hämtar information om den angivna tråden.

### <a name="parameters"></a>Parametrar
- **thread_ptr** Pekare till trådkontrollblock.
- **namn** Pekare till mål för pekaren till trådens namn.
- **tillstånd** Pekare till mål för trådens aktuella körningstillstånd. Möjliga värden är följande.
    - **TX_READY** (0x00)
    - **TX_COMPLETED** (0x01)
    - **TX_TERMINATED** (0x02)
    - **TX_SUSPENDED** (0x03)
    - **TX_SLEEP** (0x04)
    - **TX_QUEUE_SUSP** (0x05)
    - **TX_SEMAPHORE_SUSP** (0x06)
    - **TX_EVENT_FLAG** (0x07)
    - **TX_BLOCK_MEMORY** (0x08)
    - **TX_BYTE_MEMORY** (0x09)
    - **TX_MUTEX_SUSP** (0x0D)  

- **run_count** Pekare till mål för trådens körningsantal.
- **prioritet** Pekare till mål för trådens prioritet.
- **preemption_threshold** Pekare till mål för trådens tröskelvärde för avförbrukning.
**time_slice** Pekare till mål för trådens tidssegment.
**next_thread** Pekare till mål för nästa skapade tråd pekare.

**suspended_thread** Pekare till mål för pekare till nästa tråd i stängningslistan.

> [!NOTE]
> *Om du anger TX_NULL för en parameter indikerar det att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad trådinformationshämtning.
- **TX_THREAD_ERROR** (0x0E) Ogiltig trådkontrollspekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
thread "my_thread." */

status = tx_thread_info_get(&my_thread, &name,
    &state, &run_count,
    &priority, &preemption_threshold,
    &time_slice, &next_thread,&suspended_thread);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

Hämta trådprestandainformation

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_performance_info_get(
    TX_THREAD *thread_ptr,
    LONG *resumptions, 
    ULONG *suspensions,
    ULONG *solicited_preemptions, 
    ULONG *interrupt_preemptions,
    ULONG *priority_inversions, 
    ULONG *time_slices,
    ULONG *relinquishes, 
    ULONG *timeouts, 
    ULONG *wait_aborts,
    TX_THREAD **last_preempted_by);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om den angivna tråden.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med*  * **TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined för att den här tjänsten ska returnera prestandainformation.*

### <a name="parameters"></a>Parametrar
- **thread_ptr** Pekare till tidigare skapad tråd.
- **återantaganden** Pekare till mål för antalet återantaganden av den här tråden.
- **jäsningar** Pekare till mål för antalet stängningar av den här tråden.
- **solicited_preemptions** Pekare till mål för antalet preemptions som ett resultat av ett ThreadX API-tjänstanrop som gjorts av den här tråden.
- **interrupt_preemptions** Pekare till mål för antalet avbrott i den här tråden som ett resultat av avbrottsbearbetningen.
- **priority_inversions** Pekare till mål för antalet prioritetsinversioner av den här tråden.
- **time_slices** Pekare till mål för antalet tidssegment i den här tråden.
- **relinquishes** Pekare till mål för antalet trådrelinquishes som utförts av den här tråden.
- **tidsgränser** Pekare till mål för antalet tidsgränser för låsning i den här tråden.
- **wait_aborts** Pekare till mål för antalet väntande avbrott som utförts på den här tråden.
- **last_preempted_by** Pekare till mål för trådpekaren som senast övergröpte den här tråden.

> [!NOTE]
> *Ange en TX_NULL för en parameter anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad trådprestanda get.
- **TX_PTR_ERROR** (0x03) Felaktig tråd pekare.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_THREAD my_thread;
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
TX_THREAD *last_preempted_by;

/* Retrieve performance information on the previously created
thread. */

status = tx_thread_performance_info_get(&my_thread, &resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices,
    &relinquishes, &timeouts,
    &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

Hämta prestandainformation för trådsystem

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_performance_system_info_get(
    ULONG *resumptions,
    ULONG *suspensions, 
    ULONG *solicited_preemptions,
    ULONG *interrupt_preemptions, 
    ULONG *priority_inversions,
    ULONG *time_slices, 
    ULONG *relinquishes, 
    ULONG *timeouts,
    ULONG *wait_aborts, 
    ULONG *non_idle_returns,
    ULONG *idle_returns);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om alla trådar i systemet.

*ThreadX-biblioteket och programmet måste byggas med*

***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined för att den här tjänsten ska returnera prestandainformation.*

### <a name="parameters"></a>Parametrar

- **återupptaganden** Pekare till mål för det totala antalet trådantaganden.
- **jäsningar** Pekare till mål för det totala antalet trådstängningar.
- **solicited_preemptions** Pekare till mål för det totala antalet tråd-preemptions som ett resultat av en tråd som anropar en ThreadX API-tjänst.
- **interrupt_preemptions** Pekare till mål för det totala antalet trådavbrott som ett resultat av avbrottsbearbetningen.
- **priority_inversions** Pekare till mål för det totala antalet trådprioritetsinversioner.
- **time_slices** Pekare till mål för det totala antalet trådtidssegment.
- **relinquishes** Pekare till mål för det totala antalet trådrelinquishes.
- **tidsgränser** Pekare till mål för det totala antalet timeouter för trådupplåsning.
- **wait_aborts** Pekare till mål för det totala antalet avbrott i trådväntan.
- **non_idle_returns** Pekare till mål för antalet gånger som en tråd återgår till systemet när en annan tråd är redo att köras.
- **idle_returns** Pekare till mål för antalet gånger som en tråd återgår till systemet när ingen annan tråd är redo att köras (inaktivt system).

> [!NOTE]
> *Ange en **TX_NULL** för en parameter anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad trådsystemprestanda get.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
ULONG non_idle_returns;
ULONG idle_returns;

/* Retrieve performance information on all previously created
thread. */

status = tx_thread_performance_system_info_get(&resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices, &relinquishes,
    &timeouts, &wait_aborts, &non_idle_returns,
    &idle_returns);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

Ändra tröskelvärdet för tröskel för program

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a>Description

Den här tjänsten ändrar tröskelvärdet för preemption för den angivna tråden. Tröskelvärdet preemption-förhindrar att den angivna tråden av trådar är lika med eller mindre än tröskelvärdet preemption-threshold.

>[!NOTE]
> *Om du använder preemption-threshold inaktiveras tidsdelicering för den angivna tråden.*

### <a name="parameters"></a>Parametrar
- **thread_ptr** Pekare till en tidigare skapad programtråd.
- **new_threshold** Ny prioritetsnivå för preemption-threshold (0 till (TX_MAX_PRIORITIES-1)).
- **old_threshold** Pekare till en plats för att returnera det tidigare tröskelvärdet för preemption.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad ändring av tröskelvärdet för avställning.
- **TX_THREAD_ERROR** (0x0E) Felaktig pekare för programtråd.
- **TX_THRESH_ERROR** (0x18) Angivet tröskelvärde för ny spärr är inte en giltig trådprioritet (ett annat värde än (0 till (**TX_MAX_PRIORITIES**-1)) eller större än (lägre prioritet) än den aktuella trådprioritet.
- **TX_PTR_ERROR** (0x03) Ogiltig pekare till tidigare lagringsplats för preemptionthreshold.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar och timers

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_THREAD my_thread;
UINT my_old_threshold;
UINT status;

/* Disable all preemption of the specified thread. The
current preemption-threshold is returned in
"my_old_threshold". Assume that "my_thread" has
already been created. */

status = tx_thread_preemption_change(&my_thread,
    0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
non-preemptable by another thread. Note that ISRs are
not prevented by preemption disabling. */
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_priority_change"></a>tx_thread_priority_change

Ändra prioritet för programtråd

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a>Description

Den här tjänsten ändrar prioriteten för den angivna tråden. Giltiga prioriteringar sträcker sig från 0 till (TX_MAX_PRIORITES-1), där 0 representerar den högsta prioritetsnivån.

> [!IMPORTANT]
> *Tröskelvärdet för avspärrning för den angivna tråden ställs automatiskt in på den nya prioriteten. Om ett nytt tröskelvärde önskas måste tjänsten ***tx_thread_preemption_change** _ användas efter den här call._

### <a name="parameters"></a>Parametrar

- **thread_ptr** Pekare till en tidigare skapad programtråd.
- **new_priority** Ny trådprioritetsnivå (0 till (TX_MAX_PRIORITIES-1)).
- **old_priority** Pekare till en plats för att returnera trådens tidigare prioritet.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad prioritetsändring.
- **TX_THREAD_ERROR** (0x0E) Felaktig pekare för programtråd.
- **TX_PRIORITY_ERROR** (0x0F) Angiven ny prioritet är inte giltig (ett annat värde än (0 till (TX_MAX_PRIORITIES-1)).
- **TX_PTR_ERROR** (0x03) Ogiltig pekare till lagringsplats med tidigare prioritet.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar och timers

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_THREAD my_thread;
UINT my_old_priority;
UINT status;

/* Change the thread represented by "my_thread" to priority
0. */

status = tx_thread_priority_change(&my_thread,
    0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
now at the highest priority level in the system. */
```
### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_relinquish"></a>tx_thread_relinquish

Relinquish control to other application threads (Dra tillbaka kontrollen till andra programtrådar)

### <a name="prototype"></a>Prototyp

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a>Description

Den här tjänsten lämnar över processorkontrollen till andra färdiga trådar med samma eller högre prioritet.

> [!NOTE]
> *Förutom att frångå kontrollen till trådar med samma prioritet, lämnar den här tjänsten även över kontrollen till den tråd med högst prioritet som förhindras från körning på grund av den aktuella trådens tröskelinställning för tröskel för preemption.*

### <a name="parameters"></a>Parametrar

Ingen

### <a name="return-values"></a>Returvärden

Ingen

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="examples"></a>Exempel

```c
ULONG run_counter_1 = 0;
ULONG run_counter_2 = 0;

/* Example of two threads relinquishing control to
each other in an infinite loop. Assume that
both of these threads are ready and have the same
priority. The run counters will always stay within one
of each other. */

VOID my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{

    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_reset"></a>tx_thread_reset

Återställ tråd

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

Den här tjänsten återställer den angivna tråden så att den körs vid startpunkten som definierades när tråden skapades. Tråden måste antingen vara i **ett TX_COMPLETED** **eller TX_TERMINATED** tillstånd för att den ska återställas

> [!IMPORTANT]
> *Tråden måste återupptas för att den ska kunna köras igen.*

### <a name="parameters"></a>Parametrar

- **thread_ptr** Pekare till en tråd som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad trådåterställning.
- **TX_NOT_DONE** (0x20) Angiven tråd är inte **i ett TX_COMPLETED** eller **TX_TERMINATED** tillstånd.
- **TX_THREAD_ERROR** (0x0E) Felaktig trådpekare.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

TX_THREAD my_thread;

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preformance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_resume"></a>tx_thread_resume

Återuppta pausad programtråd

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

Den här tjänsten återupptar eller förbereder körningen av en tråd som tidigare pausas av ett ***tx_thread_suspend anrop.*** Dessutom återupptar den här tjänsten trådar som har skapats utan automatisk start.

### <a name="parameters"></a>Parametrar

- **thread_ptr** Pekare till en pausad programtråd.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad tråd-ÅTERUPPTA.
- **TX_SUSPEND_LIFTED** (0x19) Tidigare fördröjd stängning lyftes.
- **TX_THREAD_ERROR** (0x0E) Ogiltig pekare för programtråd.
- **TX_RESUME_ERROR** (0x12) Angiven tråd pausas inte eller inaktiverades tidigare av en annan tjänst **_än tx_thread_suspend_**.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

TX_THREAD my_thread;

### <a name="example"></a>Exempel

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_sleep"></a>tx_thread_sleep

Pausa aktuell tråd under angiven tid

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a>Description

Den här tjänsten gör att anropstråden pausas för det angivna antalet timer tick. Mängden fysisk tid som associeras med ett tids tick är programspecifik. Den här tjänsten kan bara anropas från en programtråd.

### <a name="parameters"></a>Parametrar

- **timer_ticks** Antalet timer tick för att pausa den anropande programtråden från 0 till 0xFFFFFFFF. Om 0 anges returneras tjänsten omedelbart.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad trådströmsparläge.
- **TX_WAIT_ABORTED** (0x1A) Brytningen avbröts av en annan tråd, timer eller ISR.
- **TX_CALLER_ERROR** (0x13)-tjänst som anropas från en icke-tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a>Se även

- tx_thread_create, tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_stack_error_notify"></a>tx_thread_stack_error_notify

Återanrop av meddelande om fel vid registrering av trådstack

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a>Description

Den här tjänsten registrerar en återanropsfunktion för meddelanden för hantering av fel i trådstacken. När ThreadX identifierar ett fel i trådstacken under körningen anropas den här meddelandefunktionen för att bearbeta felet. Bearbetningen av felet definieras helt av programmet. Allt från att pausa den bryta tråden till att återställa hela systemet kan göras.

> [!IMPORTANT]
> *ThreadX-biblioteket måste byggas med* **TX_ENABLE_STACK_CHECKING** för att den här tjänsten ska *returnera prestandainformation.*

### <a name="parameters"></a>Parametrar
- **error_handler** Pekare till programmets felhanteringsfunktion i stacken. Om det här TX_NULL inaktiveras meddelandet.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad trådåterställning.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preformance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_suspend"></a>tx_thread_suspend

Pausa programtråd

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

Den här tjänsten pausar den angivna programtråden. En tråd kan anropa den här tjänsten för att pausa sig själv.

> [!NOTE]
> *Om den angivna tråden redan har pausats av en annan orsak, hålls den här uppstängningen internt tills den tidigare uppstängningen har lyfts. När det händer utförs den här indragningen av den angivna tråden. Ytterligare förfrågningsavstängning har ingen effekt.*

När tråden har pausats måste den återupptas av ***tx_thread_resume*** köra igen.

### <a name="parameters"></a>Parametrar

- **thread_ptr** Pekare till en programtråd.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad tråd pausas.
- **TX_THREAD_ERROR** (0x0E) Felaktig pekare för programtråd.
- **TX_SUSPEND_ERROR** (0x14) Angiven tråd är i ett avslutat eller slutfört tillstånd.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_terminate"></a>tx_thread_terminate

Avslutar programtråden

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Description

Den här tjänsten avslutar den angivna programtråden oavsett om tråden pausas eller inte. En tråd kan anropa den här tjänsten för att avsluta sig själv.

> [!NOTE]
> *Det är programmets ansvar att se till att tråden är i ett tillstånd som är lämpligt för avslutning. Till exempel bör en tråd inte avslutas under kritisk programbearbetning eller inuti andra komponenter i mellanprogram där den kan lämna sådan bearbetning i ett okänt tillstånd.*

> [!IMPORTANT]
> *När den har avslutats måste tråden återställas för att den ska köras igen.*

### <a name="parameters"></a>Parametrar

- **thread_ptr** Pekare till programtråd.

### <a name="return-values"></a>Returvärden
- **TX_SUCCESS** (0x00) Lyckad tråd avslutas.
- **TX_THREAD_ERROR** (0x0E) Felaktig pekare för programtråd.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar och timers

### <a name="preemption-possible"></a>Avtagande möjlig

Yes

### <a name="example"></a>Exempel

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a>Se även

- tx_thread_create tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

Ändrar tidssegmentet för programtråden

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a>Description

Den här tjänsten ändrar tidssegmentet för den angivna programtråden. Om du väljer en tidssegment för en tråd garanterar du att den inte kör fler än det angivna antalet timer tick innan andra trådar med samma eller högre prioritet har möjlighet att köras.

> [!NOTE]
> *Om du använder tröskelvärdet preemption-inaktiveras tidsdelicering för den angivna tråden.*

### <a name="parameters"></a>Parametrar

- **thread_ptr** Pekare till programtråd.
- **new_time_slice** Nytt tidssegmentvärde. Juridiska värden omfattar TX_NO_TIME_SLICE numeriska värden från 1 till 0xFFFFFFFF.
- **old_time_slice** Pekare till plats för att lagra det tidigare tidsliceringsvärdet för den angivna tråden.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad tidssegmentchans.
- **TX_THREAD_ERROR** (0x0E) Ogiltig pekare för programtråd.
- **TX_PTR_ERROR** (0x03) Ogiltig pekare till lagringsplats för tidigare tidssegment.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar och timers

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_THREAD my_thread;
ULONG my_old_time_slice;
UINT status;

/* Change the time-slice of the thread associated with
"my_thread" to 20. This will mean that "my_thread"
can only run for 20 timer-ticks consecutively before
other threads of equal or higher priority get a chance
to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
    &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
has been changed to 20 and the previous time-slice is
in "my_old_time_slice." */
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_wait_abort

## <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

Avbryt instängning av angiven tråd

### <a name="prototype"></a>Prototyp

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

Den här tjänsten avbryter viloläget eller något annat objekt som avbryter den angivna tråden. Om väntetiden avbryts returneras **TX_WAIT_ABORTED** värde från den tjänst som tråden väntade på.

> [!NOTE]
> *Den här tjänsten frigör inte explicit stängning som görs av tx_thread_suspend tjänsten.*

### <a name="parameters"></a>Parametrar

- **thread_ptr** Pekare till en tidigare skapad programtråd.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad trådvänte avbryts.
- **TX_THREAD_ERROR** (0x0E) Ogiltig pekare för programtråd.
- **TX_WAIT_ABORT_ERROR** (0x1B) Angiven tråd är inte i väntetillstånd.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig
Yes

### <a name="example"></a>Exempel

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a>Se även

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change

## <a name="tx_time_get"></a>tx_time_get

Hämtar aktuell tid

Programtimerar

### <a name="prototype"></a>Prototyp

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a>Description

Den här tjänsten returnerar innehållet i den interna systemklockan. Varje timertick ökar den interna systemklockan med en. Systemklockan är inställd på noll under initieringen och kan ändras till ett specifikt värde av tjänsten ***tx_time_set***.

> [!NOTE]
> *Den faktiska tid som varje timer tick representerar är programspecifik.*

**Parametrar**

Ingen

### <a name="return-values"></a>Returvärden

- **systemklocka tick** Värdet för den interna, kostnadsfria körningen, systemklockan.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig
No

### <a name="example"></a>Exempel

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a>Se även

- tx_time_set

## <a name="tx_time_set"></a>tx_time_set

Anger aktuell tid

### <a name="prototype"></a>Prototyp

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a>Description

Den här tjänsten ställer in den interna systemklockan på det angivna värdet. Varje timer-tick ökar den interna systemklockan med en.

> [!NOTE]
> *Den faktiska tid som varje timer tick representerar är programspecifik.*

### <a name="parameters"></a>Parametrar

- **new_time** Ny tid att lägga i systemklockan, juridiska värden sträcker sig från 0 till 0xFFFFFFFF.

### <a name="return-values"></a>Returvärden

Ingen

### <a name="allowed-from"></a>Tillåts från

Trådar, timers och ISR:er

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a>Se även

- tx_time_get

## <a name="tx_timer_activate"></a>tx_timer_activate

Aktivera programtimer

### <a name="prototype"></a>Prototyp

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar den angivna programtimern. Förfallorutinerna för timers som upphör att gälla samtidigt körs i den ordning som de aktiverades.

> [!NOTE]
> *En 1-shot-timer som har upphört att gälla måste återställas via*  * **tx_timer_change** _ _before kan den aktiveras igen.*

### <a name="parameters"></a>Parametrar

- **timer_ptr** Pekare till en tidigare skapad programtimer.

**Returvärden**

- **TX_SUCCESS** (0x00) Lyckad aktivering av programtimer.
- **TX_TIMER_ERROR** (0x15) Markör för ogiltig programtimer.
- **TX_ACTIVATE_ERROR** (0x17) Timern var redan aktiv eller är en timer som redan har gått ut.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a>Se även

- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_change"></a>tx_timer_change

Ändra programtimer

### <a name="prototype"></a>Prototyp

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a>Description

Den här tjänsten ändrar förfalloegenskaperna för den angivna programtimern. Timern måste inaktiveras innan du anropar den här tjänsten.

> [!NOTE]
> *Ett anrop till*  * **tx_timer_activate** _ _service krävs efter den här tjänsten för att starta timern igen.*

### <a name="parameters"></a>Parametrar

- **timer_ptr** Pekare till ett timerkontrollblock.
- **initial_ticks** Anger det första antalet tick för timerförfallotid. Juridiska värden sträcker sig från 1 till 0xFFFFFFFF.
- **reschedule_ticks** Anger antalet tick för alla förfallotid för timer efter den första. En nolla för den här parametern gör timern *till en enslagstimer.* I annat fall är de juridiska värdena för periodiska timers mellan 1 och 0xFFFFFFFF.

> [!NOTE]
> *En 1-shot-timer som har upphört att gälla måste återställas via* 
* **tx_timer_change** _ _before kan den aktiveras igen.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad ändring av programtimer.
- **TX_TIMER_ERROR** (0x15) Markör för ogiltig programtimer.
- **TX_TICK_ERROR** (0x16) Ogiltigt värde (noll) har angetts för inledande tick.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar, timers och ISR:er

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_TIMER my_timer;
UINT status;

/* Change a previously created and now deactivated timer
to expire every 50 timer ticks, including the initial
expiration. */
status = tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```

### <a name="see-also"></a>Se även

- tx_timer_activate
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_create"></a>tx_timer_create

Skapa programtimer

### <a name="prototype"></a>Prototyp

```c
UINT tx_timer_create(
    TX_TIMER *timer_ptr, 
    CHAR *name_ptr,
    VOID (*expiration_function)(ULONG),
    ULONG expiration_input, 
    ULONG initial_ticks,
    ULONG reschedule_ticks, 
    UINT auto_activate);
```

### <a name="description"></a>Description

Den här tjänsten skapar en programtimer med den angivna förfallofunktionen och periodisk.

### <a name="parameters"></a>Parametrar

- **timer_ptr** Pekare till ett kontrollblock för timer
- **name_ptr** Pekare till namnet på timern.
- **expiration_function** Programfunktion som anropas när timern upphör att gälla.
- **expiration_input** Indata som ska överföras till förfallofunktionen när timern upphör att gälla.
- **initial_ticks** Anger det första antalet tick för timerförfallotid. Juridiska värden sträcker sig från 1 till 0xFFFFFFFF.
- **reschedule_ticks** Anger antalet tick för alla förfallotid för timer efter den första. En nolla för den här parametern gör timern *till en enslagstimer.* I annat fall är de juridiska värdena för periodiska timers mellan 1 och 0xFFFFFFFF.

  > [!NOTE]
  > *När en timer för ett försök upphör att gälla måste den återställas via tx_timer_change innan den kan aktiveras igen.*

- **auto_activate** Anger om timern aktiveras automatiskt när den skapas. Om det här **TX_AUTO_ACTIVATE** (0x01) aktiveras timern. Om annars värdet **TX_NO_ACTIVATE** (0x00) har valts, skapas timern i ett icke-aktivt tillstånd. I det här fallet krävs **_tx_timer_activate_** efterföljande tjänstsamtal för att få igång timern.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Skapande av en lyckad programtimer.
- **TX_TIMER_ERROR** (0x15) Markör för ogiltig programtimer. Pekaren är NULL eller så har timern redan skapats.
- **TX_TICK_ERROR** (0x16) Ogiltigt värde (noll) har angetts för inledande tick.
- **TX_ACTIVATE_ERROR** (0x17) Ogiltig aktivering har valts.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_TIMER my_timer;
UINT status;

/* Create an application timer that executes
"my_timer_function" after 100 ticks initially and then
after every 25 ticks. This timer is specified to start
immediately! */
status = tx_timer_create(&my_timer,"my_timer_name",
    my_timer_function, 0x1234, 100, 25,
    TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
be called 100 timer ticks later and then called every
25 timer ticks. Note that the value 0x1234 is passed to
my_timer_function every time it is called. */
```

### <a name="see-also"></a>Se även

- tx_timer_activate
- tx_timer_change
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_deactivate"></a>tx_timer_deactivate

Inaktivera programtimer

### <a name="prototype"></a>Prototyp

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar den angivna programtimern. Om timern redan är inaktiverad har den här tjänsten ingen effekt.

### <a name="parameters"></a>Parametrar

- **timer_ptr** Pekare till en tidigare skapad programtimer.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad inaktivering av programtimer.
- **TX_TIMER_ERROR** (0x15) Ogiltig pekare för programtimer.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a>Se även

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_delete"></a>tx_timer_delete

Ta bort programtimer

### <a name="prototype"></a>Prototyp

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den angivna programtimern.

> [!NOTE]
> *Det är programmets ansvar att förhindra användning av en borttagna timer.*

### <a name="parameters"></a>Parametrar

- **timer_ptr** Pekare till en tidigare skapad programtimer.

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad borttagning av programtimer.
- **TX_TIMER_ERROR** (0x15) Ogiltig pekare för programtimer.
- **TX_CALLER_ERROR** (0x13) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a>Se även

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_info_get"></a>tx_timer_info_get

Hämta information om en programtimer

### <a name="prototype"></a>Prototyp

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a>Description

Den här tjänsten hämtar information om den angivna programtimern.

### <a name="parameters"></a>Parametrar

- **timer_ptr** Pekare till en tidigare skapad programtimer.
- **namn** Pekare till mål för pekaren till timerns namn.
- **aktiv** Pekare till mål för den aktiva timerindikeringen. Om timern är inaktiv eller om den här tjänsten anropas från själva timern returneras **TX_FALSE** värde. Om timern är aktiv returneras **annars TX_TRUE** värde.
- **remaining_ticks** Pekare till mål för antalet timer tick kvar innan timern upphör att gälla.
- **reschedule_ticks** Pekare till mål för antalet timer tick som ska användas för att automatiskt omplanera den här timern. Om värdet är noll är timern ett enda försök och kommer inte att omplaneras.
- **next_timer** Pekare till mål för pekaren för nästa skapade programtimer.

> [!NOTE]
> *Om du anger **TX_NULL** för en parameter indikerar det att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad timerinformationshämtning.
- **TX_TIMER_ERROR** (0x15) Ogiltig pekare för programtimer.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="preemption-possible"></a>Avtagande möjlig

No

### <a name="example"></a>Exempel

```c
TX_TIMER my_timer;
CHAR *name;
UINT active;
ULONG remaining_ticks;
ULONG reschedule_ticks;
TX_TIMER *next_timer;
UINT status;

/* Retrieve information about the previously created
application timer "my_timer." */
status = tx_timer_info_get(&my_timer, &name,
    &active,&remaining_ticks,
    &reschedule_ticks,
    &next_timer);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Se även

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

Hämta information om timerprestanda

### <a name="prototype"></a>Prototyp

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om den angivna programtimern.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med*  * **TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _defined för att den här tjänsten ska returnera prestandainformation.*

### <a name="parameters"></a>Parametrar
- **timer_ptr** Pekare till timer som skapats tidigare.
- **aktiveras** Pekare till mål för antalet aktiveringsbegäranden som utförts på den här timern.
- **återaktiverar** Pekare till mål för antalet automatiska återaktiveringar som utförts på den här periodiska timern.
- **inaktiverar** Pekare till mål för antalet inaktiveringsbegäranden som utförts på den här timern.
- **förfallotid** Pekare till mål för antalet förfallotid för den här timern.
- **expiration_adjusts** Pekare till mål för antalet interna förfallojusteringar som utförts på den här timern. Dessa justeringar görs i timerbearbetningen av avbrott för timers som är större än standardstorleken för timerlistan (som standard timers med förfallotidsvärden som är större än 32 tick).

> [OBS] *Ange en TX_NULL för en parameter anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad timerprestanda get.
- **TX_PTR_ERROR** (0x03) Ogiltig timerpekare.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
TX_TIMER my_timer;
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on the previously created
timer. */
status = tx_timer_performance_info_get(&my_timer, &activates,
    &reactivates,&deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

Hämta prestandainformation för timersystem

### <a name="prototype"></a>Prototyp

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a>Description

Den här tjänsten hämtar prestandainformation om alla programtimer i systemet.

> [!IMPORTANT]
> *ThreadX-biblioteket och programmet måste byggas med TX_TIMER_ENABLE_PERFORMANCE_INFO* **har definierats** *för att den här tjänsten ska returnera prestandainformation.*

**Parametrar**

- **aktiveras** Pekare till mål för det totala antalet aktiveringsbegäranden som utförts på alla timers.
- **återaktiverar** Pekare till mål för det totala antalet automatiska återaktiveringar som utförts på alla periodiska timers.
- **inaktiverar** Pekare till mål för det totala antalet inaktiveringsbegäranden som utförts på alla timers.
- **förfallotid** Pekare till mål för det totala antalet förfallotid för alla timers.
- **expiration_adjusts** Pekare till mål för det totala antalet interna förfallojusteringar som utförts på alla timers. Dessa justeringar görs i timerbearbetningen av avbrott för timers som är större än standardstorleken för timerlistan (som standard timers med förfallotidsvärden som är större än 32 tick).

> [!NOTE]
> *Ange en **TX_NULL** för en parameter anger att parametern inte är obligatorisk.*

### <a name="return-values"></a>Returvärden

- **TX_SUCCESS** (0x00) Lyckad prestanda för timersystemet get.
- **TX_FEATURE_NOT_ENABLED** (0xFF) Systemet kompilerades inte med aktiverad prestandainformation.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers och ISR

### <a name="example"></a>Exempel

```c
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on all previously created
timers. */
status = tx_timer_performance_system_info_get(&activates,
    &reactivates, &deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Se även

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
