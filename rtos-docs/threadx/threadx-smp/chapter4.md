---
title: Kapitel 4 – Beskrivning av Azure återställnings tider ThreadX SMP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider ThreadX SMP-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4432001b773b4ef4f99b1b34193e90863966aad4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828023"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-smp-services"></a>Kapitel 4 – Beskrivning av Azure återställnings tider ThreadX SMP-tjänster

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider ThreadX SMP-tjänster i alfabetisk ordning. Deras namn är utformade så att alla liknande tjänster grupperas tillsammans. I avsnittet "retur värden" i följande beskrivningar påverkas inte värden i **fetstil** av **TX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-kontrollen. värden som visas i fet stil är helt inaktiverade. Dessutom visar rubriken "**Ja**" som visas under rubriken "**avstängningen möjlig**" att anrop till tjänsten kan återuppta en tråd med högre prioritet, vilket innebär att den anropande tråden.

- **tx_block_allocate**: *allokera minnes block med fast storlek* 
- **tx_block_pool_create**: *Skapa pool med minnes block med fast storlek* 
- **tx_block_pool_delete**: *ta bort minnes block pool* 
- **tx_block_pool_info_get**: *Hämta information om block pool* 
- **tx_block_pool_performance_info_get**: *Hämta prestanda information för block pool* 
- **tx_block_pool_performance_system_info_get**: *Hämta information om system prestanda för block pool* 
- **tx_block_pool_prioritize**: *prioritera avstängnings lista för block-pool* 
- **tx_block_release**: *frigör block med fast storlek i minnet*
- **tx_byte_allocate**: *allokera byte minne* 
- **tx_byte_pool_create**: *skapa en lagringspool med byte* 
- **tx_byte_pool_delete**: *ta bort minnes byte pool* 
- **tx_byte_pool_info_get**: *Hämta information om en byte-pool* 
- **tx_byte_pool_performance_info_get**: *prestanda information för Hämta byte-pool* 
- **tx_byte_pool_performance_system_info_get**: *Hämta information om prestanda för byte pool system* 
- **tx_byte_pool_prioritize**: *prioritera överskjutande lista för byte-pool* 
- **tx_byte_release**: *release byte tillbaka till mediepoolen* 
- **tx_event_flags_create**: *Skapa händelse flaggor grupp* 
- **tx_event_flags_delete**: *ta bort händelse flaggor grupp* 
- **tx_event_flags_get**: *Hämta händelse flaggor från gruppen med händelse flaggor* 
- **tx_event_flags_info_get**: *Hämta information om händelse flaggor gruppen* 
- **tx_event_flags_performance_info_get**: *Hämta händelse flaggor grupp prestanda information* 
- **tx_event_flags_performance_system_info_get**: *Hämta information om prestanda systemet* 
- **tx_event_flags_set**: *Ange händelse flaggor i en grupp med händelse flaggor* 
- **tx_event_flags_set_notify**: *meddela program när händelse flaggor anges*
- **tx_interrupt_control**: *Aktivera och inaktivera avbrott* 
- **tx_mutex_create**: *skapa ömsesidigt uteslutande mutex* 
- **tx_mutex_delete**: *ta bort ömsesidigt uteslutande mutex* 
- **tx_mutex_get**: *få ägande rätt till mutex* 
- **tx_mutex_info_get**: *Hämta information om mutex* 
- **tx_mutex_performance_info_get**: *Hämta information om mutex-prestanda* 
- **tx_mutex_performance_system_info_get**: *Hämta information om prestanda för mutex-system* 
- **tx_mutex_prioritize**: *prioritera mutex SUS pensions lista* 
- **tx_mutex_put**: *frigör ägarskap för mutex* 
- **tx_queue_create**: *skapa meddelandekö* 
- **tx_queue_delete**: *ta bort meddelande kön* 
- **tx_queue_flush**: *tomma meddelanden i meddelande kön* 
- **tx_queue_front_send**: *Skicka meddelande till kön längst fram* 
- **tx_queue_info_get**: *Hämta information om kö* 
- **tx_queue_performance_info_get**: *Hämta prestanda information för kö* 
- **tx_queue_performance_system_info_get**: *Hämta prestanda information för Queue system*
- **tx_queue_prioritize**: *prioritera en lista över återkallade köer* 
- **tx_queue_receive**: *Hämta meddelande från meddelandekö* 
- **tx_queue_send**: *Skicka meddelande till meddelande kön* 
- **tx_queue_send_notify**: *meddela programmet när ett meddelande skickas till kön* 
- **tx_semaphore_ceiling_put**: *Placera en instans i räkna semaforen med tak* 
- **tx_semaphore_create**: *skapa inventering av semafor* 
- **tx_semaphore_delete**: *ta bort inventering semafor* 
- **tx_semaphore_get**: *Hämta instans från semafor* 
- **tx_semaphore_info_get**: *Hämta information om semaforen* 
- **tx_semaphore_performance_info_get**: *Hämta information om semafor-prestanda* 
- **tx_semaphore_performance_system_info_get**: *Hämta information om prestanda för semafor-systemet* 
- **tx_semaphore_prioritize**: *prioritera semafor SUS Pension lista* 
- **tx_semaphore_put**: *Placera en instans i inventering av semafor* 
- **tx_semaphore_put_notify**: *meddela programmet när semaforen placeras* 
- **tx_thread_create**: *skapa program tråd* 
- **tx_thread_delete**: *ta bort program tråd*
- **tx_thread_entry_exit_notify**: *meddela programmet vid tråd inmatning och avsluta* 
- **tx_thread_identify**: *hämtar pekare till tråd som körs för tillfället* 
- **tx_thread_info_get**: *Hämta information om tråd* 
- **tx_thread_performance_info_get**: *Hämta information om tråd prestanda* 
- **tx_thread_performance_system_info_get**: *Hämta information om tråd system prestanda* 
- **tx_thread_preemption_change**: *ändra avstängningen-tröskel för program tråd* 
- **tx_thread_priority_change**: *ändra prioritet för program tråd* 
- **tx_thread_relinquish**: lämna *kontroll över andra program trådar* 
- **tx_thread_reset**: *Återställ tråd* 
- **tx_thread_resume**: *återuppta inaktive rad program tråd* 
- **tx_thread_sleep**: *pausa den aktuella tråden för angiven tid* 
- **tx_thread_smp_core_exclude**: *exkludera tråd körning på en uppsättning kärnor* 
- **tx_thread_smp_core_exclude_get**: *hämtar trådens aktuella kärn undantag* 
- **tx_thread_smp_core_get**: *Hämta kärnan för anroparen som körs* 
- **tx_thread_stack_error_notify**: *Registrera ett återanrop i tråds tack* rings meddelande 
- **tx_thread_suspend**: *pausa program tråd*
- **tx_thread_terminate**: *avslutar program tråd* 
- **tx_thread_time_slice_change**: *ändrar time-slice för program tråd* 
- **tx_thread_wait_abort**: *Avbryt avstängning av angiven tråd* 
- **tx_time_get**: *hämtar aktuell tid* 
- **tx_time_set**: *anger aktuell tid* 
- **tx_timer_activate**: *Aktivera programtimer* 
- **tx_timer_change**: *ändra programmets timer* 
- **tx_timer_create**: *skapa programtimer* 
- **tx_timer_deactivate**: *inaktivera Application timer* 
- **tx_timer_delete**: *ta bort program timer* 
- **tx_timer_info_get**: *Hämta information om en program-timer* 
- **tx_timer_performance_info_get**: *Hämta information om timer-prestanda* 
- **tx_timer_performance_system_info_get**: *Hämta timer-systemets prestanda information* 
- **tx_timer_smp_core_exclude**: *utesluta timer-körning i en uppsättning kärnor* 
- **tx_timer_smp_core_exclude_get**: *hämtar timerns aktuella kärn undantag*

## <a name="tx_block_allocate"></a>tx_block_allocate
Allokera minnes block med fast storlek

### <a name="prototype"></a>Prototyp

```C
UINT tx_block_allocate(TX_BLOCK_POOL *pool_ptr, VOID **block_ptr,
                          ULONG wait_option);
```
### <a name="description"></a>Beskrivning

Den här tjänsten allokerar ett minnes block med fast storlek från den angivna lagringspoolen. Minnes blockets faktiska storlek bestäms när minnesbufferten skapas.

> [!WARNING]
> Det är viktigt att se till att program koden inte skriver utanför det allokerade minnes blocket. Om detta inträffar inträffar skada i ett intilliggande (vanligt vis) minnes block. Resultatet är oförutsägbart och är ofta allvarligt!

### <a name="parameters"></a>Parametrar

- **pool_ptr**: pekar mot en tidigare skapad pool för minnes block.
- **block_ptr**: pekar mot en mål Blocks pekare. Vid lyckad allokering placeras adressen till det allokerade minnes blocket där den här parametern pekar.
- **wait_option**: definierar hur tjänsten fungerar om det inte finns några tillgängliga minnes block. Vänte alternativen definieras enligt följande:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF)
    - timeout-värde: (0x00000001 till 0xFFFFFFFE)  
    
    Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte. Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.

    Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden i oändlighet tills ett minnes block är tillgängligt.

    Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på ett minnes block.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad minnes Blocks tilldelning.
- **TX_DELETED**: (0X01) minnes Blocks gruppen togs bort när tråden pausades.
- **TX_NO_MEMORY**: (0X10) tjänsten kunde inte allokera ett minnes block inom den angivna tiden till väntan.
- **TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.
- TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.
- TX_PTR_ERROR: (0x03) ogiltig pekare till mål pekaren.
- TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```c
TX_BLOCK_POOL   my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a memory block from my_pool. Assume that the
   pool has already been created with a call to
   tx_block_pool_create. */
status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
                               TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated block of memory. */
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
Skapa pool med minnes block med fast storlek

### <a name="prototype"></a>Prototyp

```C
UINT tx_block_pool_create(TX_BLOCK_POOL *pool_ptr,
                          CHAR *name_ptr, ULONG block_size,
                          VOID *pool_start, ULONG pool_size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en pool med minnes block med fast storlek. Det angivna minnes området är indelat i så många minnes block med fast storlek som möjligt med hjälp av formeln:    
**Totalt antal block** = (**Totalt antal byte**)/(**block storlek** + sizeof (void *))

> [!IMPORTANT]
> Varje minnes block innehåller en pekare som är dold för användaren och representeras av "sizeof (void *)" i föregående formel.

### <a name="parameters"></a>Parametrar

- **pool_ptr**: pekar mot ett kontroll block för minnes Blocks-pool.
- **name_ptr**: pekar mot namnet på minnes Blocks-poolen.
- **block_size**: antal byte i varje minnes block.
- **pool_start**: Start adress för minnes Blocks gruppen. Start adressen måste vara justerad till storleken på data typen ULONG..
- **pool_size**: totalt antal byte som är tillgängliga för minnes Blocks gruppen.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad generering av minnes Blocks pool.
- TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool. Antingen är pekaren NULL eller också har poolen redan skapats.
- TX_PTR_ERROR: (0x03) ogiltig start adress för poolen.
- TX_SIZE_ERROR: (0x05) storleken på poolen är ogiltig.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_BLOCK_POOL  my_pool;
UINT           status;

/* Create a memory pool whose total size is 1000 bytes
   starting at address 0x100000. Each block in this
   pool is defined to be 50 bytes long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
               50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18
   memory blocks of 50 bytes each. The reason
   there are not 20 blocks in the pool is
   because of the one overhead pointer associated with each
   block. */
```
### <a name="see-also"></a>Se även

- tx_block_allocate
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_delete"></a>tx_block_pool_delete

Ta bort pool för minnes block

### <a name="prototype"></a>Prototyp

```C
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna block minnes poolen. Alla trådar som pausas i väntan på ett minnes block från den här poolen återupptas och får en TX_DELETED retur status.

> [!IMPORTANT]
> Det är programmets ansvar att hantera det minnes område som är associerat med poolen, vilket är tillgängligt när tjänsten har slutförts. Dessutom måste programmet förhindra att en borttagen pool eller de tidigare minnes blocken används.

### <a name="parameters"></a>Parametrar

- **pool_ptr**: pekar mot en tidigare skapad pool för minnes block.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad borttagning av minnes Blocks pool.
- TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_BLOCK_POOLmy_pool;
UINT           status;

    /* Delete entire memory block pool. Assume that the pool
      has already been created with a call to
      tx_block_pool_create. */
    status =  tx_block_pool_delete(&my_pool);

    /* If status equals TX_SUCCESS, the memory block pool is
       deleted. */
```
### <a name="see-also"></a>Se även

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

Hämta information om blockera pool

### <a name="prototype"></a>Prototyp

```C
UINT tx_block_pool_info_get(TX_BLOCK_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *total_blocks,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BLOCK_POOL **next_pool);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om den angivna block minnes poolen.

### <a name="parameters"></a>Parametrar

- **pool_ptr**: pekare till tidigare skapade minnes Blocks-pool.
- **Name**: pekare till målet för visaren i block poolens namn.
- **tillgängligt**: pekare till målet för antalet tillgängliga block i den blockerande poolen.
- **total_blocks**: pekar mot mål för det totala antalet block i block poolen.
- **first_suspended**: pekar till målet för visaren i den tråd som är överst i listan över avbrytande av den här block-poolen.
- **suspended_count**: pekar mot mål för antalet trådar som för närvarande har pausats på den här block-poolen.
- **next_pool**: pekar mot destinationen för en pekare på nästa skapade block-pool.

> [!IMPORTANT]
> Om du anger en TX_NULL för vilken parameter som helst är parametern inte obligatorisk.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) Det gick inte att hämta information om block pool.
- TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
TX_BLOCK_POOL    my_pool;
CHAR             *name;
ULONG            available;
ULONG            total_blocks;
TX_THREAD        *first_suspended;
ULONG            suspended_count;
TX_BLOCK_POOL    *next_pool;
UINT             status;

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
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

Hämta prestanda information för block pool

### <a name="prototype"></a>Prototyp

```c
UINT tx_block_pool_performance_info_get(TX_BLOCK_POOL *pool_ptr,
       ULONG *allocates, ULONG *releases,
       ULONG *suspensions, ULONG *timeouts));
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om den angivna Memory block-poolen.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste skapas med **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **pool_ptr**: pekare till tidigare skapade minnes Blocks-pool.
- **allokerar**: pekare till målet för antalet allokerade begär Anden som utförts i den här poolen.
- **versioner**: pekare till målet för antalet release-begäranden som har utförts på den här poolen.
- **SUS pensioner**: pekare till målet för antalet avbrott i tråd tilldelningen för den här poolen.
- **timeout**: pekar mot målets antal tids gräns värden för att allokera uppehåll i poolen.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) prestanda för slutförd block pool har hämtats.
- **TX_PTR_ERROR**: (0X03) ogiltig pekare för att blockera poolen.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
TX_BLOCK_POOL     my_pool;
ULONG             allocates;
ULONG             releases;
ULONG             suspensions;
ULONG             timeouts;

/* Retrieve performance information on the previously created block
   pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
                                            &releases,
                &suspensions,
                &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
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

Hämta information om system prestanda för block pool

### <a name="prototype"></a>Prototyp

```C
UINT tx_block_pool_performance_system_info_get(ULONG *allocates,
       ULONG *releases, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om alla minnes Blocks pooler i programmet.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste skapas med **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **allokerar**: pekar mot mål för det totala antalet allokerade begär Anden som utförts på alla blockerade pooler.
- **versioner**: pekare till målet för det totala antalet begär Anden som har utförts på alla blockerade pooler.
- **SUS pensioner**: pekar mot mål för det totala antalet SUS pensioner i alla block-pooler.
- **timeout**: pekar mot mål för det totala antalet tids gränser för att allokera uppehåll i alla block-pooler.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) slutförd blockering av system prestanda för poolen.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

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

Prioritera spärr lista för block-pool

### <a name="prototype"></a>Prototyp

```C
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten placerar tråden med högsta prioritet inaktive rad för ett minnes block på den här poolen längst fram i listan över SUS pensioner. Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.

### <a name="parameters"></a>Parametrar 

- **pool_ptr**: pekar mot ett kontroll block för minnes Blocks-pool.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) prioritet för att blockera poolen.
- TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_BLOCK_POOL my_pool;
UINT          status;

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

Frigör block med fast storlek i minnet

### <a name="prototype"></a>Prototyp

```C
UINT tx_block_release(VOID *block_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten släpper ett tidigare allokerat block tillbaka till den kopplade poolen. Om det finns en eller flera trådar som pausas i väntan på minnes block från den här poolen, är den första tråden inaktive rad det här minnes blocket och återupptas.

> [!IMPORTANT]
> Programmet måste förhindra att ett minnes Blocks utrymme används när det har släppts tillbaka till poolen.

### <a name="parameters"></a>Parametrar

- **block_ptr**: pekar mot det tidigare allokerade minnes blocket.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad minnes Blocks version.
- TX_PTR_ERROR: (0x03) ogiltig pekare till minnes block.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_BLOCK_POOLmy_pool;
unsigned char*memory_ptr;
UINT         status;

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

```C
UINT tx_byte_allocate(TX_BYTE_POOL *pool_ptr,
                          VOID **memory_ptr, ULONG memory_size,
                          ULONG wait_option);
```
### <a name="description"></a>Beskrivning

Den här tjänsten allokerar det angivna antalet byte från den angivna Memory byte-poolen.

> [!WARNING]
> Det är viktigt att se till att program koden inte skriver utanför det allokerade minnes blocket. Om detta inträffar inträffar skada i ett intilliggande (vanligt vis) minnes block. Resultatet är oförutsägbart och är ofta allvarligt!

> [!IMPORTANT]
> Prestanda för den här tjänsten är en funktion i block storlek och fragmenteringen i poolen. Därför bör den här tjänsten inte användas under tids kritiska körnings trådar.

### <a name="parameters"></a>Parametrar

- **pool_ptr**: pekar mot en tidigare skapad lagringspool.
- **memory_ptr**: pekar mot en mål minnes pekare. Vid lyckad allokering placeras adressen till det allokerade minnes området där parametern pekar på.
- **memory_size**: antal byte som har begärts.
- **wait_option**: definierar hur tjänsten fungerar om det inte finns tillräckligt med minne tillgängligt. Vänte alternativen definieras enligt följande:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF)
    - timeout-värde: (0x00000001 till 0xFFFFFFFE)

    Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte. *Detta är det enda giltiga alternativet om tjänsten anropas från initiering.*

    Om du väljer TX_WAIT_FOREVER avbryts anrops tråden till oändligt tills tillräckligt med minne är tillgängligt.

    Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på minnet.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad minnesallokering.
- **TX_DELETED**: (0x01)-mediepoolen togs bort medan tråden pausades.
- **TX_NO_MEMORY**: tjänsten (0x10) kunde inte allokera minne inom den angivna tiden till väntan.
- **TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.
- TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för skrivarpool.
- TX_PTR_ERROR: (0x03) ogiltig pekare till mål pekaren.
- TX_SIZE_ERROR: (0X05) den begärda storleken är noll eller större än poolen.
- TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a 112 byte memory area from my_pool. Assume
   that the pool has already been created with a call to
   tx_byte_pool_create. */
status =  tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
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

Skapa minnes-pool med byte

### <a name="prototype"></a>Prototyp

```C
UINT tx_byte_pool_create(TX_BYTE_POOL *pool_ptr,
                          CHAR *name_ptr, VOID *pool_start,
                          ULONG pool_size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en pool för minnes byte i det angivna området. Från början består poolen av i princip ett mycket stort ledigt block. Poolen är dock bruten i mindre block som tilldelningar görs.

### <a name="parameters"></a>Parametrar

- **pool_ptr**: pekar mot ett kontroll block för minnes-pool.
- **name_ptr**: pekar mot namnet på mediepoolen.
- **pool_start**: Start adress för mediepoolen. Start adressen måste vara justerad till storleken på data typen ULONG.
- **pool_size**: totalt antal byte som är tillgängliga för lagringspoolen.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad minnesallokering.
- TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för skrivarpool. Antingen är pekaren NULL eller också har poolen redan skapats.
- TX_PTR_ERROR: (0x03) ogiltig start adress för poolen.
- TX_SIZE_ERROR: (0x05) storleken på poolen är ogiltig.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Create a memory pool whose total size is 2000 bytes
   starting at address 0x500000. */
status =  tx_byte_pool_create(&my_pool, "my_pool_name",
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

Ta bort minnes byte pool

### <a name="prototype"></a>Prototyp

```C
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna minnes bytes poolen. Alla trådar som pausas i väntan på minne från den här poolen återupptas och har en TX_DELETED retur status.

> [!IMPORTANT]
> Det är programmets ansvar att hantera det minnes område som är associerat med poolen, vilket är tillgängligt när tjänsten har slutförts. Dessutom måste programmet förhindra användning av en borttagen pool eller minne som tidigare har allokerats från den.

### <a name="parameters"></a>Parametrar 

- **pool_ptr**: pekar mot en tidigare skapad lagringspool.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) slutförd borttagning av minnesallokering.
- TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för skrivarpool.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Delete entire memory pool. Assume that the pool has already
   been created with a call to tx_byte_pool_create. */
status =   tx_byte_pool_delete(&my_pool);

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

Hämta information om byte-poolen

### <a name="prototype"></a>Prototyp

```C
UINT tx_byte_pool_info_get(TX_BYTE_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *fragments,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BYTE_POOL **next_pool);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om den angivna minnes bytes poolen.

### <a name="parameters"></a>Parametrar

- **pool_ptr**: pekare till den tidigare skapade lagringspoolen.
- **Name**: pekare till målet för visaren i byte-poolens namn.
- **tillgängligt**: pekare till målet för antalet tillgängliga byte i poolen.
- **fragment**: pekar mot mål för det totala antalet minnes fragment i byte-poolen.
- **first_suspended**: pekar till målet för visaren i den tråd som är överst i listan över återkallade byte för denna byte-pool.
- **suspended_count**: pekar mot mål för antalet trådar som för närvarande har pausats i den här byte-poolen.
- **next_pool**: pekar mot destinationen för en pekare på nästa skapade byte-pool.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckades hämta information om poolen.
- TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för skrivarpool.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_BYTE_POOL my_pool;
CHAR         *name;
ULONG        available;
ULONG        fragments;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_BYTE_POOL *next_pool;
UINT         status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status =  tx_byte_pool_info_get(&my_pool, &name,
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

Hämta prestanda information för byte-pool

### <a name="prototype"></a>Prototyp

```C
UINT tx_byte_pool_performance_info_get(TX_BYTE_POOL *pool_ptr,
        ULONG *allocates, ULONG *releases,
        ULONG *fragments_searched, ULONG *merges, ULONG *splits,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om den angivna minnes bytes poolen.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste skapas med **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **pool_ptr**: pekar mot tidigare skapade minnes byte pool.
- **allokerar**: pekare till målet för antalet allokerade begär Anden som utförts i den här poolen.
- **versioner**: pekare till målet för antalet release-begäranden som har utförts på den här poolen.
- **fragments_searched**: pekar mot mål för antalet interna minnes fragment som genomsöks under tilldelnings begär anden i den här poolen.
- **sammanslagningar**: pekare till målet för antalet interna minnes block som sammanfogas under tilldelnings begär anden i den här poolen.
- **delningar**: pekare till målet för antalet interna minnes block delning (fragment) som skapas vid tilldelnings begär anden i den här poolen.
- **SUS pensioner**: pekare till målet för antalet avbrott i tråd tilldelningen för den här poolen.
- **timeout**: pekar mot målets antal tids gräns värden för att allokera uppehåll i poolen.

> [!IMPORTANT]
> Om du anger en TX_NULL för vilken parameter som helst är parametern inte obligatorisk.

### <a name="return-values"></a>Retur värden

- TX_SUCCESS: (0x00) prestanda för slutförd byte-pool har hämtats.
- **TX_PTR_ERROR**: (0X03) ogiltig pekare för byte-pool.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
TX_BYTE_POOL     my_pool;
ULONG            fragments_searched;
ULONG            merges;
ULONG            splits;
ULONG            allocates;
ULONG            releases;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created byte
   pool.  */
status =  tx_byte_pool_performance_info_get(&my_pool,
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

Hämta information om prestanda för byte pool system

### <a name="prototype"></a>Prototyp

```C
UINT  tx_byte_pool_performance_system_info_get(ULONG *allocates,
        ULONG *releases, ULONG *fragments_searched, ULONG *merges,
        ULONG *splits, ULONG *suspensions, ULONG *timeouts);;
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om alla minnes byte pooler i systemet.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste skapas med **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **allokerar**: pekare till målet för antalet allokerade begär Anden som utförts i den här poolen.
- **versioner**: pekare till målet för antalet release-begäranden som har utförts på den här poolen.
- **fragments_searched**: pekar mot mål för det totala antalet interna minnes fragment som genomsöks under tilldelnings begär Anden för alla byte-pooler.
- **sammanslagningar**: pekare till mål för det totala antalet interna minnes block som sammanfogas under tilldelnings begär Anden för alla byte-pooler.
- **delningar**: pekar mot mål för det totala antalet interna minnes block delning (fragment) som skapas vid tilldelnings begär Anden för alla byte pooler.
- **SUS pensioner**: pekar mot mål för det totala antalet SUS pensioner i alla byte-pooler.
- **tids gränser**: pekar mot mål för det totala antalet tids gränser för att allokera uppehåll i alla byte-pooler.

> [!IMPORTANT]
> Om du anger en TX_NULL för vilken parameter som helst är parametern inte obligatorisk.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) prestanda för slutförd byte-pool har hämtats.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
ULONG         fragments_searched;
ULONG         merges;
ULONG         splits;
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

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

Prioritera överskjutande lista för byte-pool

### <a name="prototype"></a>Prototyp

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten placerar den högsta prioritets tråden inaktive rad för minne på den här poolen överst i SUS pensions listan. Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.

### <a name="parameters"></a>Parametrar 

- **pool_ptr**: pekar mot ett kontroll block för minnes-pool.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad minnes uppsättnings prioritet.
- TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för skrivarpool.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```c
TX_BYTE_POOL my_pool;
UINT         status;

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

Frisläpp byte tillbaka till minnesbuffert

### <a name="prototype"></a>Prototyp

```C
UINT tx_byte_release(VOID *memory_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten frigör ett tidigare allokerat minnes utrymme tillbaka till den associerade poolen. Om en eller flera trådar pausas i väntan på minne från den här poolen, tilldelas varje pausad tråd minne och återupptas tills minnet är slut eller tills det inte finns några fler pausade trådar. Den här processen för att allokera minne till pausade trådar börjar alltid med den första tråden inaktive rad.

> [!IMPORTANT]
> Programmet måste förhindra att minnes området används när det har släppts.

### <a name="parameters"></a>Parametrar

- **memory_ptr**: pekar på det tidigare allokerade minnes området.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad minnes version.
- TX_PTR_ERROR: (0x03) ogiltig minnes områdets pekare.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
unsigned char    *memory_ptr;
UINT             status;

/* Release a memory back to my_pool. Assume that the memory
   area was previously allocated from my_pool. */
status =  tx_byte_release((VOID *) memory_ptr);

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

Skapa händelse flaggor grupp

### <a name="prototype"></a>Prototyp

```c
UINT tx_event_flags_create(TX_EVENT_FLAGS_GROUP *group_ptr,
                          CHAR *name_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en grupp med 32 händelse flaggor. Alla händelse flaggor i 32 i gruppen initieras till noll. Varje händelse flagga representeras av en enskild bit.

### <a name="parameters"></a>Parametrar

- **group_ptr**: pekar på en grupp kontroll block för händelse flaggor. 
- **name_ptr**: pekar på namnet på gruppen med händelse flaggor.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) en lyckad händelse grupp skapades.
- TX_GROUP_ERROR: (0x06) ogiltig händelse grupp pekare. Antingen är pekaren NULL eller också har händelse gruppen redan skapats.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_EVENT_FLAGS_GROUP my_event_group;
UINT         status;

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

Ta bort händelse flaggor grupp

### <a name="prototype"></a>Prototyp

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna händelse flaggas gruppen. Alla trådar som pausas i väntan på att händelser från den här gruppen återupptas och får en TX_DELETED retur status.

> [!IMPORTANT]
> Programmet måste se till att en Set notify motringning för den här händelse flaggor gruppen är slutförd (eller inaktive rad) innan du tar bort händelse flaggor gruppen. Dessutom måste programmet förhindra all framtida användning av en borttagen händelse flaggor grupp.

### <a name="parameters"></a>Parametrar 

- **group_ptr**: pekar mot en tidigare skapad händelse flagg grupp.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) händelse flaggor grupp borttagning har slutförts.
- TX_GROUP_ERROR: (0x06) ogiltig grupp pekare för händelse flaggor.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT                 status;

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

Hämta händelse flaggor från gruppen med händelse flaggor

### <a name="prototype"></a>Prototyp

```C
UINT tx_event_flags_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG requested_flags, UINT get_option,
                          ULONG *actual_flags_ptr, ULONG wait_option);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar händelse flaggor från den angivna händelse flaggor gruppen. Varje händelse flaggor grupp innehåller 32 händelse flaggor. Varje flagga representeras av en enskild bit. Den här tjänsten kan hämta en rad olika kombinationer av händelse flaggor som valts av indataparametrarna.

### <a name="parameters"></a>Parametrar

- **group_ptr**: pekar mot en tidigare skapad händelse flagg grupp.
- **requested_flags**: 32-bitars osignerad variabel som representerar de begärda händelse flaggorna.
- **get_option**: anger om alla eller någon av de begärda händelse flaggorna krävs. Följande är giltiga val:
    - **TX_AND**: (protokollnumret 0x02)
    - **TX_AND_CLEAR**: (0x03)
    - **TX_OR**: (0x00)
    - **TX_OR_CLEAR**: (0x01)

    Om du väljer TX_AND eller TX_AND_CLEAR anger det att alla händelse flaggor måste finnas i gruppen. Om du väljer TX_OR eller TX_OR_CLEAR anges att en händelse flagga är tillfredsställande. Händelse flaggor som uppfyller begäran rensas (anges till noll) om TX_AND_CLEAR eller TX_OR_CLEAR har angetts.

- **actual_flags_ptr**: pekar mot målet där de hämtade händelse flaggorna placeras. Observera att de faktiska flaggor som erhålls kan innehålla flaggor som inte har begärts.
- **wait_option**: definierar hur tjänsten beter sig om de valda händelse flaggorna inte har angetts. Vänte alternativen definieras enligt följande:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF)
    - timeout-värde: (0x00000001 till 0xFFFFFFFE)

    Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte. Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.

    Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills händelse flaggorna är tillgängliga.

    Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på händelse flaggor.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) händelse flaggorna get.
- **TX_DELETED**: (0X01) händelse flaggor gruppen togs bort när tråden pausades.
- **TX_NO_EVENTS**: tjänsten (0x07) kunde inte hämta de angivna händelserna inom den angivna tiden till väntan.
- **TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.
- TX_GROUP_ERROR: (0x06) ogiltig grupp pekare för händelse flaggor.
- TX_PTR_ERROR: (0x03) ogiltig pekare för faktiska händelse flaggor.
- TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.
- TX_OPTION_ERROR: (0x08) ogiltigt get-option angavs.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG         actual_events;
UINT          status;

/* Request that event flags 0, 4, and 8 are all set. Also,
   if they are set they should be cleared. If the event
   flags are not set, this service suspends for a maximum of
   20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
                      TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
   actual events obtained. */
```
### <a name="see-also"></a>Se även

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

Hämta information om händelse flaggor gruppen

### <a name="prototype"></a>Prototyp

```C
UINT tx_event_flags_info_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                         CHAR **name, ULONG *current_flags,
                         TX_THREAD **first_suspended,
                         ULONG *suspended_count,
                         TX_EVENT_FLAGS_GROUP **next_group);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om den angivna händelse flagg gruppen.

### <a name="parameters"></a>Parametrar

- **group_ptr**: pekar på en grupp kontroll block för händelse flaggor.
- **Name**: pekare till målet för visaren i namnet på händelse flaggor gruppen.
- **current_flags**: pekar mot mål för aktuella uppsättnings flaggor i gruppen med händelse flaggor.
- **first_suspended**: pekar till målet för visaren i den tråd som är överst i listan över uppskjutnings listor för den här händelse flaggor gruppen.
- **suspended_count**: pekar mot mål för antalet trådar som för närvarande har pausats på den här händelse flaggor gruppen.
- **next_group**: pekar på destinations visaren för nästa skapade händelse flaggor grupp.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckades hämta information om händelse grupps information.
- TX_GROUP_ERROR: (0x06) ogiltig händelse grupp pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```c
TX_EVENT_FLAGS_GROUPmy_event_group;
CHAR          *name;
ULONG         current_flags;
TX_THREAD     *first_suspended;
ULONG         suspended_count;
TX_EVENT_FLAGS_GROUP*next_group;
UINT          status;

/* Retrieve information about the previously created
   event flags group "my_event_group." */
status =  tx_event_flags_info_get(&my_event_group, &name,
             &current_flags,
             &first_suspended, &suspended_count,
             &next_group);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a>Se även

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_performance-info_get"></a>tx_event_flags_performance info_get

Hämta information om händelse flaggor grupp prestanda information

### <a name="prototype"></a>Prototyp

```C
UINT tx_event_flags_performance_info_get(TX_EVENT_FLAGS_GROUP
                        *group_ptr, ULONG *sets, ULONG *gets,
                        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om den angivna händelse flagg gruppen.

> [!IMPORTANT]
> ThreadX SMP-bibliotek och program måste skapas med **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **group_ptr**: pekar mot tidigare skapade händelse flagg grupper.
- **uppsättningar**: pekare till målet för antalet händelse flaggor Ställ förfrågningar som utförs på den här gruppen.
- **hämtar**: pekare till målet för antalet händelse flaggor Hämta begär Anden som utförs i den här gruppen.
- **SUS pensioner**: pekare till målet för antalet trådar i tråden som ska skjuta upp den här gruppen.
- **tids gränser**: pekare till målet för antalet händelse flaggor få timeout för inaktive ring för den här gruppen.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckade händelse flaggor grupp prestanda Hämta.
- **TX_PTR_ERROR**: (0X03) ogiltig grupp pekare för händelse flaggor.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
TX_EVENT_FLAGS_GROUPmy_event_flag_group;
ULONG           sets;
ULONG           gets;
ULONG           suspensions;
ULONG           timeouts;

/* Retrieve performance information on the previously created event
   flag group. */
status =  tx_event_flags_performance_info_get(&my_event_flag_group,
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

Hämta information om prestanda systemet

### <a name="prototype"></a>Prototyp

```c
UINT  tx_event_flags_performance_system_info_get(ULONG *sets,
        ULONG *gets,ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om alla händelse flaggor grupper i systemet.

> [!IMPORTANT]
> ThreadX SMP-bibliotek och program måste skapas med **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **anger**: pekar mot mål för det totala antalet händelse flaggor som har utförts i alla grupper.
- **hämtar**: pekare till målet för det totala antalet händelse flaggor begär Anden som utförs på alla grupper.
- **SUS pensioner**: pekare till mål för det totala antalet tråd händelse flaggor som får uppehåll i alla grupper.
- **tids gränser**: pekare till målet för det totala antalet händelse flaggor få timeout för inaktive ring i alla grupper.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckade händelse flaggor system prestanda Hämta.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```c
ULONG         sets;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

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

Ange händelse flaggor i en grupp med händelse flaggor

### <a name="prototype"></a>Prototyp

```C
UINT tx_event_flags_set(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG  flags_to_set,UINT set_option);
```
### <a name="description"></a>Beskrivning

Den här tjänsten anger eller rensar händelse flaggor i en grupp med händelse flaggor, beroende på det angivna set-alternativet. Alla pausade trådar vars begär Anden om Event Flags nu är uppfyllda återupptas.

### <a name="parameters"></a>Parametrar

- **group_ptr**: pekar mot de tidigare skapade händelse flaggorna grupp kontroll block.
- **flags_to_set**: anger vilka händelse flaggor som ska ställas in eller avmarkeras baserat på set-alternativet.
- **set_option**: anger om de angivna händelse flaggorna är ANDed eller Ored till gruppens aktuella händelse flaggor. Följande är giltiga val:
    - **TX_AND**: (protokollnumret 0x02)
    - **TX_OR**: (0x00) om du väljer TX_AND anger att de angivna händelse flaggorna är **och** Erik i de aktuella händelse flaggorna i gruppen. Det här alternativet används ofta för att rensa händelse flaggor i en grupp. Annars, om TX_OR anges, är de angivna händelse flaggorna **eller** Erik med den aktuella händelsen i gruppen.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckade händelse flaggor angavs.
- TX_GROUP_ERROR: (0x06) ogiltig pekare till händelse flaggor gruppen.
- TX_OPTION_ERROR: (0x08) ogiltigt set-alternativ angavs.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_EVENT_FLAGS_GROUPmy_event_flags_group;
UINT         status;

/* Set event flags 0, 4, and 8. */
status =  tx_event_flags_set(&my_event_flags_group,
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

Meddela program när händelse flaggor anges

### <a name="prototype"></a>Prototyp

```C
UINT tx_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr,
       VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```
### <a name="description"></a>Beskrivning

Den här tjänsten registrerar en funktion för motringning av meddelanden som anropas när en eller flera händelse flaggor anges i den angivna händelse flaggor gruppen. Bearbetningen av aviserings återanropet definieras av programmet.

> [!NOTE]
> Programmets händelse flaggor ange återanrop för meddelanden är inte tillåtet för att anropa ThreadX SMP-API med ett uppehålls alternativ.

### <a name="parameters"></a>Parametrar 
- **group_ptr**: pekar mot tidigare skapade händelse flagg grupper.
- **events_set_notify**: pekar på programmets händelse flaggor ange meddelande funktion. Om det här värdet är TX_NULL inaktive ras meddelande.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) registreringen av event Flags set-aviseringar har slutförts.
- TX_GROUP_ERROR: (0x06) ogiltig grupp pekare för händelse flaggor.
- TX_FEATURE_NOT_ENABLED: (0xFF) systemet kompilerades med aviserings funktioner inaktiverade.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
TX_EVENT_FLAGS_GROUPmy_group;

/* Register the "my_event_flags_set_notify" function for monitoring
   event flags set in the event flags group "my_group." */
status =  tx_event_flags_set_notify(&my_group,
                my_event_flags_set_notify);

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

```C
UINT tx_interrupt_control(UINT new_posture);
```
### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar eller inaktiverar avbrott som anges i indataparametern **new_posture**.

> [!IMPORTANT]
> Om den här tjänsten anropas från en program tråd förblir avbrotts position en del av trådens kontext. Om tråden till exempel anropar den här rutinen för att inaktivera avbrott och sedan pausar, så inaktive ras avbrott på nytt när de återupptas.

> [!WARNING]
> Den här tjänsten bör inte användas för att aktivera avbrott under initiering! Om du gör det kan det orsaka oförutsägbara resultat.

### <a name="parameters"></a>Parametrar

- **new_posture**: den här parametern anger om avbrott är inaktiverade eller aktiverade. Giltiga värden är **TX_INT_DISABLE och TX_INT_ENABLE.** De faktiska värdena för dessa parametrar är specifika för porten. Dessutom kan vissa bearbetnings arkitekturer stödja ytterligare avbrott inaktivera postures. Mer information finns i **_readme_threadx.txt_** information som angavs på distributions disken.

### <a name="return-values"></a>Retur värden

- tidigare position: den här tjänsten returnerar föregående avbrotts position till anroparen. Detta gör att användare av tjänsten kan återställa de tidigare position när avbrott har inaktiverats.

### <a name="allowed-from"></a>Tillåten från

Trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture =  tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
   locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```
### <a name="see-also"></a>Se även

Inget

## <a name="tx_mutex_create"></a>tx_mutex_create

Skapa ömsesidigt uteslutande mutex

### <a name="prototype"></a>Prototyp

```C
UINT tx_mutex_create(TX_MUTEX *mutex_ptr,
                          CHAR *name_ptr, UINT priority_inherit);
```
### <a name="description"></a>Beskrivning
    
Den här tjänsten skapar ett mutex för ömsesidigt undantag mellan trådar för resurs skydd.

### <a name="parameters"></a>Parametrar

- **mutex_ptr**: pekar på ett mutex-Control-Block.
- **name_ptr**: pekar mot namnet på mutex.
- **priority_inherit**: anger om denna mutex stöder arv av prioriteter. Om det här värdet är TX_INHERIT stöds prioriterat arv. Men om TX_NO_INHERIT anges stöds inte prioriterat arv av denna mutex.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) slutförde mutex-skapande.
- TX_MUTEX_ERROR: (0x1C) ogiltig MUTEX-pekare. Antingen är pekaren NULL eller så har mutex redan skapats.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.
- TX_INHERIT_ERROR: (0x1F) ogiltig prioritet Ärv parameter.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Create a mutex to provide protection over a
   common resource. */
status =  tx_mutex_create(&my_mutex,"my_mutex_name",
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

Ta bort ömsesidigt uteslutande mutex

### <a name="prototype"></a>Prototyp

```C
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort angiven mutex. Alla trådar som pausas i väntan på att mutexen återupptas och har fått en TX_DELETED retur status.

> [!IMPORTANT]
> Det är programmets ansvar att förhindra användning av en borttagen mutex.

### <a name="parameters"></a>Parametrar

- **mutex_ptr**: pekar mot en tidigare skapad mutex.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad borttagning av mutex.
- TX_MUTEX_ERROR: (0x1C) ogiltig MUTEX-pekare.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Delete a mutex. Assume that the mutex
   has already been created. */
status =  tx_mutex_delete(&my_mutex);

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

Få ägarskap för mutex

### <a name="prototype"></a>Prototyp

```C
UINT tx_mutex_get(TX_MUTEX *mutex_ptr, ULONG wait_option);
```
### <a name="description"></a>Beskrivning

Den här tjänsten försöker få exklusiv ägande rätt till angiven mutex. Om den anropande tråden redan äger mutex, ökar en intern räknare och en lyckad status returneras.

Om mutex ägs av en annan tråd och den här tråden är högre prioritet och arv av prioritet har angetts vid mutex Create, kommer den lägre prioritets Trådens prioritet att tillfälligt höjas till den för anrops tråden.

> [!IMPORTANT]
> Prioriteten för tråden med lägre prioritet som äger en mutex med priorityinheritance bör aldrig ändras av en extern tråd under mutex-ägarskapet.

### <a name="parameters"></a>Parametrar

- **mutex_ptr**: pekar mot en tidigare skapad mutex.
- **wait_option**: definierar hur tjänsten fungerar om mutex redan ägs av en annan tråd. Vänte alternativen definieras enligt följande:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF)
    - timeout-värde: (0x00000001 till 0xFFFFFFFE)

    Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte. *Detta är det enda giltiga alternativet om tjänsten anropas från initiering.*

    Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills mutex är tillgängligt.

    Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på mutex.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad åtgärd för hämtning av mutex.
- **TX_DELETED**: (0X01) mutex togs bort när tråden pausades.
- **TX_NOT_AVAILABLE**: (0x1D) Det gick inte att erhålla ägarskap för mutex inom den angivna tiden för att vänta.
- **TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.
- TX_MUTEX_ERROR: (0x1C) ogiltig MUTEX-pekare.
- TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar och timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Obtain exclusive ownership of the mutex "my_mutex".
   If the mutex "my_mutex" is not available, suspend until it
   becomes available. */
status =  tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
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

```C
UINT tx_mutex_info_get(TX_MUTEX *mutex_ptr, CHAR **name,
                          ULONG *count, TX_THREAD **owner,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count, TX_MUTEX **next_mutex);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information från angiven mutex.

### <a name="parameters"></a>Parametrar

- **mutex_ptr**: pekar på mutex Control Block.
- **Name**: pekare till målet för visaren i mutexens namn.
- **antal**: pekar mot målets antal ägarskap för mutex.
- **ägare**: pekare till målet för den ägande trådens pekare.
- **first_suspended**: pekar till målet för visaren till den tråd som först finns i listan över återkallade i denna mutex.
- **suspended_count**: pekar mot mål för antalet trådar som för närvarande har pausats på den här mutexen.
- **next_mutex**: pekaren till målet för pekaren över nästa skapade mutex.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckades hämtning av mutex-information.
- TX_MUTEX_ERROR: (0x1C) ogiltig MUTEX-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_MUTEX     my_mutex;
CHAR         *name;
ULONG        count;
TX_THREAD    *owner;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_MUTEX     *next_mutex;
UINT         status;

/* Retrieve information about the previously created
   mutex "my_mutex." */
status =  tx_mutex_info_get(&my_mutex, &name,
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

```C
UINT tx_mutex_performance_info_get(TX_MUTEX *mutex_ptr, ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts,
       ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om angiven mutex.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste skapas med **TX_MUTEX_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **mutex_ptr**: pekar mot tidigare skapad mutex.
- **placerar**: pekare till målet för antalet placerings begär Anden som utförts på denna mutex.
- **hämtar**: pekare till målet för antalet get-begäranden som har utförts på denna mutex.
- **SUS pensioner**: pekare till målet för antalet tråd-mutex-återsusering av denna mutex.
- **tids gränser**: pekare till målet för antalet mutex för att få timeout för den här mutexen.
- **inversioner**: pekar mot mål för antalet tråd prioritets versioner på denna mutex.
- **arv**: pekar mot mål för antalet arvs åtgärder för tråd prioritet på denna mutex.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad mutex prestanda Hämta. 
- **TX_PTR_ERROR**: (0X03) ogiltig mutex-pekare.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
TX_MUTEX     my_mutex;
ULONG        puts;
ULONG        gets;
ULONG        suspensions;
ULONG        timeouts;
ULONG        inversions;
ULONG        inheritances;

/* Retrieve performance information on the previously created
   mutex. */
status =  tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
                &suspensions, &timeouts, &inversions,
                &inheritances);

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

Hämta information om prestanda för mutex-system

### <a name="prototype"></a>Prototyp

```C
UINT  tx_mutex_performance_system_info_get(ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts,
        ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om alla mutexer i systemet.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste skapas med **TX_MUTEX_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **placerar**: pekar mot mål för det totala antalet placerings begär Anden som utförts på alla mutexer.
- **hämtar**: pekare till mål för det totala antalet get-begäranden som utförts på alla mutexer.
- **SUS pensioner**: pekare till målet för det totala antalet tråd-mutex får SUS pensioner på alla mutexer.
- **tids gränser**: pekare till målet för det totala antalet mutexs-timeoutar för alla mutexer.
- **inversion**: pekar mot mål för det totala antalet tråd prioritets versioner i alla mutexer.
- **arv**: pekar mot mål för det totala antalet arvs åtgärder för tråd prioritet på alla mutexer.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad mutex system prestanda Hämta.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;
ULONG         inversions;
ULONG         inheritances;

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

Prioritera mutex SUS pensioner List

### <a name="prototype"></a>Prototyp

```C
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten placerar den högsta prioritets tråden inaktive rad för ägarskapet av mutexen längst fram i SUS pensions listan. Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.

### <a name="parameters"></a>Parametrar 

- **mutex_ptr**: pekar mot den tidigare skapade mutex.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad mutex-prioritering.
- TX_MUTEX_ERROR: (0x1C) ogiltig MUTEX-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_MUTEX     my_mutex;
UINT         status;

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

Frigör ägarskap för mutex

### <a name="prototype"></a>Prototyp

```C
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten minskar ägarskaps antalet för angiven mutex. Om antalet ägarskap är noll görs mutex tillgängligt.

> [!IMPORTANT]
> Om prioritets arv valdes när en mutex skapades återställs prioriteten för den frisläppta tråden till den prioritet den hade när den ursprungligen fick ägandet av mutex. Alla andra prioritets ändringar som görs i den sammanställda tråden under ägarskapet av mutex kan återställas.

### <a name="parameters"></a>Parametrar

- **mutex_ptr**: pekar mot den tidigare skapade mutex.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad mutex-version.
- **TX_NOT_OWNED**: (0X1E) mutex ägs inte av anroparen.
- TX_MUTEX_ERROR: (0x1C) ogiltig pekare till MUTEX.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar och timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_MUTEX         my_mutex;
UINT             status;
/* Release ownership of "my_mutex." */
status =  tx_mutex_put(&my_mutex);

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
UINT tx_queue_create(TX_QUEUE *queue_ptr, CHAR *name_ptr,
                          UINT message_size,
                          VOID *queue_start, ULONG queue_size);
```
### <a name="description"></a>Beskrivning

Tjänsten skapar en meddelandekö som vanligt vis används för kommunikation mellan trådar. Det totala antalet meddelanden beräknas från angiven meddelande storlek och det totala antalet byte i kön.

> [!IMPORTANT]
> Om det totala antalet byte som anges i köns minnes området inte är jämnt delbar med den angivna meddelande storleken, används inte återstående byte i minnes området.

### <a name="parameters"></a>Parametrar

- **queue_ptr**: pekar på ett kontroll block för meddelande kön.
- **name_ptr**: pekar mot namnet på meddelande kön.
- **message_size**: anger storleken på varje meddelande i kön. Meddelande storlekar sträcker sig från 1 32-bitars ord till 16 32-bitars ord. Giltiga alternativ för meddelande storlek är numeriska värden från 1 till 16.
- **queue_start**: meddelande köns start adress. Start adressen måste vara justerad till storleken på data typen ULONG.
- **queue_size**: totalt antal byte som är tillgängliga för meddelande kön.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad meddelande kön har skapats.
- TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön. Antingen är pekaren NULL eller också har kön redan skapats.
- TX_PTR_ERROR: (0x03) ogiltig start adress för meddelande kön.
- TX_SIZE_ERROR: (0x05) storleken på meddelande kön är ogiltig.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_QUEUE     my_queue;
UINT         status;

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

Ta bort meddelande kön

### <a name="prototype"></a>Prototyp

```C
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna meddelande kön. Alla trådar som pausas i väntan på ett meddelande från den här kön återupptas och ger en TX_DELETED retur status.

> [!IMPORTANT]
> Programmet måste se till att alla skicka aviserings återanrop för den här kön har slutförts (eller inaktiverats) innan kön tas bort. Dessutom måste programmet förhindra framtida användning av en borttagen kö.

*Det är också programmets ansvar att hantera det minnes område som är associerat med kön, vilket är tillgängligt när tjänsten har slutförts.*

### <a name="parameters"></a>Parametrar 

- **queue_ptr**: pekar mot en tidigare skapad meddelande kö.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad borttagning av meddelandekö.
- TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_QUEUE     my_queue;
UINT         status;

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

Tomma meddelanden i meddelande kön

### <a name="prototype"></a>Prototyp

```C
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort alla meddelanden som lagras i den angivna meddelande kön. Om kön är full ignoreras meddelanden från alla pausade trådar. Varje pausad tråd återupptas sedan med en retur status som anger att meddelandet skickades lyckades. Om kön är tom gör den här tjänsten ingenting.

### <a name="parameters"></a>Parametrar 

- **queue_ptr**: pekar mot en tidigare skapad meddelande kö.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) klar med att tömma meddelande kön.
- TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```c
TX_QUEUE     my_queue;
UINT         status;

/* Flush out all pending messages in the specified message
   queue. Assume that the queue has already been created
   with a call to tx_queue_create. */
status =  tx_queue_flush(&my_queue);

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

Skicka meddelande till kön längst fram

### <a name="prototype"></a>Prototyp

```C
UINT tx_queue_front_send(TX_QUEUE *queue_ptr,
                           VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett meddelande till den första platsen i den angivna meddelande kön. Meddelandet **kopieras** till platsen längst fram i kön från det minnes området som anges av käll pekaren.

### <a name="parameters"></a>Parametrar

- **queue_ptr**: pekar på ett kontroll block för meddelande kön.
- **source_ptr**: pekar mot meddelandet.
- **wait_option**: definierar hur tjänsten fungerar om meddelande kön är full. Vänte alternativen definieras enligt följande:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF)
    - timeout-värde: (0x00000001 till 0xFFFFFFFE)

    Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte. *Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.*

    Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden i oändlighet tills det finns utrymme i kön.

    Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på plats i kön.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) överföringen av meddelandet har slutförts.
- **TX_DELETED**: (0X01) meddelande kön togs bort när tråden pausades.
- **TX_QUEUE_FULL**: (0x0B) Det gick inte att skicka meddelandet eftersom kön var full under den angivna tids perioden för att vänta.
- **TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.
- TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.
- TX_PTR_ERROR: (0x03) ogiltig käll pekare för meddelande.
- TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG        my_message[4];

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

Hämta information om kö

### <a name="prototype"></a>Prototyp

```C
UINT tx_queue_info_get(TX_QUEUE *queue_ptr, CHAR **name,
        ULONG *enqueued, ULONG *available_storage
        TX_THREAD **first_suspended, ULONG *suspended_count,
        TX_QUEUE **next_queue);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om den angivna meddelande kön.

### <a name="parameters"></a>Parametrar

- **queue_ptr**: pekar mot en tidigare skapad meddelande kö.
- **namn**: pekar mot målets pekare till köns namn.
- i **kö**: pekare till målet för antalet meddelanden som för närvarande finns i kön.
- **available_storage**: pekar mot mål för det antal meddelanden som kön för närvarande har utrymme för.
- **first_suspended**: pekar till målet för visaren i den tråd som är överst på listan över återkallade i den här kön.
- **suspended_count**: pekar mot mål för antalet trådar som för närvarande har pausats i kön.
- **next_queue**: pekar mot mål som pekar på nästa skapade kö.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) information om lyckade köer hämtades.
- TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_QUEUE     my_queue;
CHAR         *name;
ULONG        enqueued;
ULONG        available_storage;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_QUEUE     *next_queue;
UINT         status;

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

Hämta prestanda information för kö

### <a name="prototype"></a>Prototyp

```C
UINT  tx_queue_performance_info_get(TX_QUEUE *queue_ptr,
        ULONG *messages_sent, ULONG *messages_received,
        ULONG *empty_suspensions, ULONG *full_suspensions,
        ULONG *full_errors, ULONG *timeouts);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om den angivna kön.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste skapas med **TX_QUEUE_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **queue_ptr**: pekare till kön som skapats tidigare.
- **messages_sent**: pekare till målet för antalet sändnings begär Anden som utförts i kön.
- **messages_received**: pekar mot mål för antalet mottagna mottagnings begär anden i kön.
- **empty_suspensions**: pekar mot mål för antalet tomma köer i kön.
- **full_suspensions**: pekar mot målets antal fullständiga uppehåll i kön.
- **full_errors**: pekar mot mål för antalet fullständiga fel i kön.
- **tids gränser**: pekar mot målet för antalet tids gränser för tråd SUS Pension i den här kön.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) prestanda för slutförd kö hämtas.
- **TX_PTR_ERROR**: (0X03) ogiltig Queue pekare.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
TX_QUEUE     my_queue;
ULONG        messages_sent;
ULONG        messages_received;
ULONG        empty_suspensions;
ULONG        full_suspensions;
ULONG        full_errors;
ULONG        timeouts;

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

Hämta prestanda information för Queue system

### <a name="prototype"></a>Prototyp

```C
UINT  tx_queue_performance_system_info_get(ULONG *messages_sent,
        ULONG *messages_received, ULONG *empty_suspensions,
        ULONG *full_suspensions, ULONG *full_errors,
        ULONG *timeouts);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om alla köer i systemet.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste skapas med **TX_QUEUE_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **messages_sent**: pekar mot mål för det totala antalet sändnings begär Anden som utförts på alla köer.
- **messages_received**: pekar mot mål för det totala antalet mottagnings begär Anden som utförts på alla köer.
- **empty_suspensions**: pekar mot mål för det totala antalet tomma köer i kö i alla köer.
- **full_suspensions**: pekar mot mål för det totala antalet fulla uppehåll i kön på alla köer.
- **full_errors**: pekar mot mål för det totala antalet fullständiga fel i kön i alla köer.
- **timeout**: pekar mot mål för det totala antalet tids gränser för tråd SUS pensioner i alla köer.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckat system prestanda Hämta.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```c
ULONG         messages_sent;
ULONG         messages_received;
ULONG         empty_suspensions;
ULONG         full_suspensions;
ULONG         full_errors;
ULONG         timeouts;

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

Prioritera lista över återkallade köer

### <a name="prototype"></a>Prototyp

```C
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten placerar den högsta prioritets tråden inaktive rad för ett meddelande (eller för att placera ett meddelande) i den här kön överst i SUS pensions listan. Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.

### <a name="parameters"></a>Parametrar 

- **queue_ptr**: pekar mot en tidigare skapad meddelande kö.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad prioritet för kön.
- TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_QUEUE     my_queue;
UINT         status;

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

```C
UINT tx_queue_receive(TX_QUEUE *queue_ptr,
                          VOID *destination_ptr, ULONG wait_option);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar ett meddelande från den angivna meddelande kön. Det hämtade meddelandet **kopieras** från kön till det minnes utrymme som anges av mål pekaren. Meddelandet tas sedan bort från kön.

> [!WARNING]
> Det angivna mål minnes området måste vara tillräckligt stort för att rymma meddelandet. det vill säga att meddelande målet som refereras till av **destination_ptr** måste vara minst lika stort som meddelande storleken för den här kön. Annars, om målet inte är tillräckligt stort, sker minnes skada i följande minnes områden.

### <a name="parameters"></a>Parametrar

- **queue_ptr**: pekar mot en tidigare skapad meddelande kö.
- **destination_ptr**: platsen där meddelandet ska kopieras.
- **wait_option**: definierar hur tjänsten fungerar om meddelande kön är tom. Vänte alternativen definieras enligt följande:
    - **TX_NO_WAIT**: (0x00000000) 
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) 
    - timeout-värde: (0x00000001 till 0xFFFFFFFE)

    Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte. Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.

    Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills ett meddelande är tillgängligt.

    Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det högsta antalet timer-Tick som ska vara pausat under väntan på ett meddelande.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad hämtning av meddelande.
- **TX_DELETED**: (0X01) meddelande kön togs bort när tråden pausades.
- **TX_QUEUE_EMPTY**: (0X0a) tjänsten kunde inte hämta ett meddelande eftersom kön var tom under den angivna tiden för att vänta.
- **TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.
- TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.
- TX_PTR_ERROR: (0x03) ogiltig mål pekare för meddelande.
- TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
   empty, suspend until a message is present. Note that
   this suspension is only possible from application
   threads. */
status =  tx_queue_receive(&my_queue, my_message,
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

```C
UINT tx_queue_send(TX_QUEUE *queue_ptr,
                          VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett meddelande till den angivna meddelande kön. Det skickade meddelandet **kopieras** till kön från det minnes utrymme som anges av käll pekaren.

### <a name="parameters"></a>Parametrar

- **queue_ptr**: pekar mot en tidigare skapad meddelande kö.
- **source_ptr**: pekar mot meddelandet.
- **wait_option**: definierar hur tjänsten fungerar om meddelande kön är full. Vänte alternativen definieras enligt följande:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF)
    - timeout-värde: (0x00000001 till 0xFFFFFFFE)

    Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte. *Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.*

    Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden i oändlighet tills det finns utrymme i kön.

    Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på plats i kön.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) överföringen av meddelandet har slutförts.
- **TX_DELETED**: (0X01) meddelande kön togs bort när tråden pausades.
- **TX_QUEUE_FULL**: (0x0B) Det gick inte att skicka meddelandet eftersom kön var full under den angivna tids perioden för att vänta.
- **TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.
- TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.
- TX_PTR_ERROR: (0x03) ogiltig käll pekare för meddelande.
- TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
   regardless of success. This wait option is used for
   calls from initialization, timers, and ISRs. */
status =  tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
   queue. */
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
- tx_queue_send_notify

## <a name="tx_queue_send_notify"></a>tx_queue_send_notify 

Meddela program när ett meddelande skickas till kön

### <a name="prototype"></a>Prototyp

```C
UINT  tx_queue_send_notify(TX_QUEUE *queue_ptr,
        VOID (*queue_send_notify)(TX_QUEUE *));
```
### <a name="description"></a>Beskrivning

Den här tjänsten registrerar en funktion för motringning av meddelanden som anropas när ett meddelande skickas till den angivna kön. Bearbetningen av aviserings återanropet definieras av programmet.

> [!NOTE]
> Det går inte att anropa någon ThreadX SMP-API med ett uppehålls alternativ i programmets kö för att skicka meddelanden.

### <a name="parameters"></a>Parametrar 

- **queue_ptr**: pekare till kön som skapats tidigare.
- **queue_send_notify**: pekare till programmets kö skicka meddelande funktion. Om det här värdet är TX_NULL inaktive ras meddelande.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) registreringen av kö-sändnings meddelande har slutförts.
- TX_QUEUE_ERROR: (0x09) ogiltig Queue pekare.
- TX_FEATURE_NOT_ENABLED: (0xFF) systemet kompilerades med aviserings funktioner inaktiverade.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
TX_QUEUE         my_queue;

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

Placera en instans vid räkning av semafor med tak

### <a name="prototype"></a>Prototyp

```C
UINT  tx_semaphore_ceiling_put(TX_SEMAPHORE *semaphore_ptr,
        ULONG ceiling);
```
### <a name="description"></a>Beskrivning

Den här tjänsten placerar en instans i den angivna räknaren semafor, som i verkligheten ökar inventerings semaforen med en. Om det aktuella värdet för Count-semaforen är större än eller lika med det angivna taket, kommer instansen inte att placeras och ett TX_CEILING_EXCEEDED fel kommer att returneras.

### <a name="parameters"></a>Parametrar 

- **semaphore_ptr**: pekar mot tidigare skapad semafor.
- **tak**: Max gränsen som tillåts för semaforen (giltiga värden är mellan 1 och 0xFFFFFFFF).

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) slutförde semafor tak.
- **TX_CEILING_EXCEEDED**: (0X21) placerings förfrågan överskrider tak.
- TX_INVALID_CEILING: (0x22) ett ogiltigt nollvärde angavs för tak.
- TX_SEMAPHORE_ERROR: (0x0C) ogiltig semafor-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```c
TX_SEMAPHORE     my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
   that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
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

Skapa inventering av semafor

### <a name="prototype"></a>Prototyp

```C
UINT tx_semaphore_create(TX_SEMAPHORE *semaphore_ptr,
                           CHAR *name_ptr, ULONG initial_count);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en inventerings semafor för synkronisering mellan trådar. Det inledande antalet semaforer anges som en indataparameter.

### <a name="parameters"></a>Parametrar 

- **semaphore_ptr**: pekar mot ett semafors kontroll block. 
- **name_ptr**: pekar mot Semaforens namn.
- **initial_count**: anger det inledande antalet för denna semafor. Juridiska värden sträcker sig från 0x00000000 till 0xFFFFFFFF.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad generering av semafor.
- TX_SEMAPHORE_ERROR: (0x0C) ogiltig semafor-pekare. Antingen är pekaren NULL eller så har semaforen redan skapats.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

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

Ta bort inventering av semafor

### <a name="prototype"></a>Prototyp

```C
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna uppräknings semaforen. Alla trådar som pausats i väntan på en semafors instans återupptas och har fått en TX_DELETED retur status.

> [!IMPORTANT]
> Programmet måste se till att en skicka avisering om återanrop för den här semaforen har slutförts (eller inaktiverats) innan du tar bort semaforen. Dessutom måste programmet förhindra all framtida användning av en borttagen semafor.

### <a name="parameters"></a>Parametrar 

- **semaphore_ptr**: pekar mot en tidigare skapad semafor.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad inventering av borttagning av semafor.
- TX_SEMAPHORE_ERROR: (0x0C) ogiltig inventering av semafors pekare.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Delete counting semaphore. Assume that the counting
   semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
   deleted. */
```
### <a name="see-also"></a>Se även

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

Hämta instans från semafor

### <a name="prototype"></a>Prototyp

```C
UINT tx_semaphore_get(TX_SEMAPHORE *semaphore_ptr,
                          ULONG wait_option)
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar en instans (ett enda antal) från den angivna semaforen i beräkningen. Därför minskar antalet angivna semaforer med ett.

### <a name="parameters"></a>Parametrar

- **semaphore_ptr**: pekar mot en tidigare skapad inventerings semafor.
- **wait_option**: definierar hur tjänsten fungerar om det inte finns några instanser av semaforen. det vill säga antalet semaforer är noll. Vänte alternativen definieras enligt följande:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF)
    - timeout-värde: (0x00000001 till 0xFFFFFFFE)

    Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte. *Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.*

    Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills det finns en instans av semaforen. 

    Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på en semafors instans.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad hämtning av en semafors instans.
- **TX_DELETED**: (0X01) inventering av semafor togs bort medan tråden pausades.
- **TX_NO_INSTANCE**: (0x0D) Det gick inte att hämta en instans av inventerings semaforen (antalet semaforer är noll inom den angivna tiden för att vänta).
- **TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.
- TX_SEMAPHORE_ERROR: (0x0C) ogiltig inventering av semafors pekare.
- TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```c
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Get a semaphore instance from the semaphore
   "my_semaphore." If the semaphore count is zero,
   suspend until an instance becomes available.
   Note that this suspension is only possible from
   application threads. */
status =  tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

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

Hämta information om semafor

### <a name="prototype"></a>Prototyp

```C
UINT tx_semaphore_info_get(TX_SEMAPHORE *semaphore_ptr,
                          CHAR **name, ULONG *current_value,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_SEMAPHORE **next_semaphore)
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om den angivna semaforen.

### <a name="parameters"></a>Parametrar

- **semaphore_ptr**: pekar mot semafor-kontroll block.
- **Name**: pekare till målet för visaren i Semaforens namn.
- **Current_value**: pekar mot mål för den aktuella Semaforens antal.
- **first_suspended**: pekar till målet för visaren i den tråd som är överst i listan över återkallade semaforer.
- **suspended_count**: pekar mot mål för antalet trådar som för närvarande har pausats på denna semafor.
- **next_semaphore**: pekaren till målet för pekaren över nästa skapade semafor.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad semafors informations hämtning.
- TX_SEMAPHORE_ERROR: (0x0C) ogiltig semafor-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```c
TX_SEMAPHORE my_semaphore;
CHAR         *name;
ULONG        current_value;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT         status;

/* Retrieve information about the previously created
   semaphore "my_semaphore." */
status =  tx_semaphore_info_get(&my_semaphore, &name,
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

Hämta information om semafor-prestanda

### <a name="prototype"></a>Prototyp

```C
UINT  tx_semaphore_performance_info_get(TX_SEMAPHORE *semaphore_ptr,
        ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om den angivna semaforen.

> [!NOTE]
> ThreadX SMP-biblioteket och programmet måste skapas med **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **semaphore_ptr**: pekar mot tidigare skapad semafor.
- **placerar**: pekare till målet för antalet begär Anden som utförts på denna semafor.
- **hämtar**: pekare till målet för antalet get-begäranden som utförts på denna semafor.
- **SUS pensioner**: pekare till målet för antalet tråd avbrott i denna semafor.
- **tids gränser**: pekar mot målet för antalet tids gränser för tråd SUS Pension på denna semafor.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad semafor-prestanda Hämta.
- **TX_PTR_ERROR**: (0X03) ogiltig semafor-pekare.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
TX_SEMAPHORE     my_semaphore;
ULONG            puts;
ULONG            gets;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created
   semaphore. */
status =  tx_semaphore_performance_info_get(&my_semaphore, &puts,
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

Hämta information om prestanda för semafor-systemet

### <a name="prototype"></a>Prototyp

```C
UINT tx_semaphore_performance_system_info_get(ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om alla semaforer i systemet.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste skapas med **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **placerar**: pekar mot mål för det totala antalet begär Anden som utförts på alla semaforer.
- **hämtar**: pekare till mål för det totala antalet get-begäranden som utförts på alla semaforer.
- **SUS pensioner**: pekar mot mål för det totala antalet tråd SUS pensioner på alla semaforer.
- **timeout**: pekar mot mål för det totala antalet tids gränser för tråd SUS Pension på alla semaforer.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- TX_SUCCESS: (0x00) lyckad semafor system prestanda Hämta.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

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

Prioritera lista över återkallade semaforer

### <a name="prototype"></a>Prototyp

```C
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten placerar den högsta prioritets tråden inaktive rad för en instans av semaforen överst i SUS pensions listan. Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.

### <a name="parameters"></a>Parametrar 

- **semaphore_ptr**: pekar mot en tidigare skapad semafor.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad semafor-prioritering.
- TX_SEMAPHORE_ERROR: (0x0C) ogiltig inventering av semafors pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next instance of this semaphore. */
status =  tx_semaphore_prioritize(&my_semaphore);

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

Placera en instans i inventering av semafor

### <a name="prototype"></a>Prototyp

```C
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten placerar en instans i den angivna räknaren semafor, som i verkligheten ökar inventerings semaforen med en.

> [!IMPORTANT]
> Om den här tjänsten anropas när semaforen är alla (OxFFFFFFFF) gör den nya åtgärden att semaforen återställs till noll.

### <a name="parameters"></a>Parametrar

- **semaphore_ptr**: pekar mot det tidigare skapade semafors kontroll blocket.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad semafor-placering.
- TX_SEMAPHORE_ERROR: (0x0C) ogiltig pekare för att räkna semaforen.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_SEMAPHORE     my_semaphore;
UINT             status;

/* Increment the counting semaphore "my_semaphore." */
status =  tx_semaphore_put(&my_semaphore);

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

Meddela program när semaforen placeras

### <a name="prototype"></a>Prototyp

```C
UINT  tx_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr,
        VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```
### <a name="description"></a>Beskrivning

Den här tjänsten registrerar en funktion för motringning av meddelanden som anropas när den angivna semaforen placeras. Bearbetningen av aviserings återanropet definieras av programmet.

> [!NOTE]
> Det går inte att anropa någon ThreadX SMP-API med ett uppehålls alternativ i programmets SMP-motanrop.

### <a name="parameters"></a>Parametrar 

- **semaphore_ptr**: pekar mot tidigare skapad semafor.
- **semaphore_put_notify**: pekar på programmets varnings funktion för semafors placering. Om det här värdet är TX_NULL inaktive ras meddelande.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad registrering av semafors meddelande.
- TX_SEMAPHORE_ERROR: (0x0C) ogiltig semafor-pekare.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet kompilerades med aviserings funktioner inaktiverade.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
TX_SEMAPHORE     my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
   the put operations on the semaphore "my_semaphore." */
status =  tx_semaphore_put_notify(&my_semaphore,
                my_semaphore_put_notify);

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

Skapa program tråd

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_create(TX_THREAD *thread_ptr,
                          CHAR *name_ptr, VOID (*entry_function)(ULONG),
                          ULONG entry_input, VOID *stack_start,
                          ULONG stack_size, UINT priority,
                          UINT preempt_threshold, ULONG time_slice,
                          UINT auto_start);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en program tråd som startar körningen vid den angivna aktivitets inmatnings funktionen. Stack, Priority, avstängningen-Threshold och Time-slice är bland de attribut som anges av indataparametrarna. Dessutom anges även det första körnings läget för tråden.

### <a name="parameters"></a>Parametrar

- **thread_ptr**: pekar mot ett tråd kontroll block.
- **name_ptr**: pekar mot namnet på tråden.
- **entry_function**: anger den inledande C-funktionen för tråd körning. När en tråd returnerar från den här post funktionen placeras den i ett slutfört tillstånd och inaktive ras på obestämd tid.
- **entry_input**: ett 32-bitars värde som skickas till trådens post funktion första gången den körs. Användningen av den här indatamängden fastställs exklusivt av programmet.
- **stack_start**: Start adress för stackens minnes områden. 
- **stack_size**: antal byte i stack minnes området. Trådens stack område måste vara tillräckligt stort för att hantera dess värsta fall funktions anrop till kapsling och lokal variabel användning.
- **prioritet**: numerisk prioritet för tråd. Giltiga värden är mellan 0 och (TX_MAX_PRIORITES-1), där värdet 0 representerar den högsta prioriteten.
- **preempt_threshold**: högsta prioritets nivå (0 till (TX_MAX_PRIORITIES-1)) av inaktiverade avstängningen. Endast prioriteter som är större än den här nivån tillåts för den här tråden. Värdet måste vara mindre än eller lika med den angivna prioriteten. Ett värde som är lika med tråd prioriteten inaktiverar avstängningen-Threshold.
- **time_slice**: antalet timer-Tick som den här tråden tillåts köra innan andra redo trådar med samma prioritet ges möjlighet att köra. Observera att med avstängningen-tröskelvärdet inaktive ras tids segmentering. Legal Time-slice-värden sträcker sig från 1 till 0xFFFFFFFF (inklusive). Värdet **TX_NO_TIME_SLICE** (värdet 0) inaktiverar tids segmentering av tråden.

    > [!IMPORTANT]
    > Om du använder tids segmentering blir det en liten del av systemets kostnader. Eftersom tids segmentering bara är användbart i fall där flera trådar delar samma prioritet, ska trådar som har en unik prioritet inte tilldelas en tid-sektor.

- **auto_start**: anger om tråden startar omedelbart eller om den placeras i ett uppehålls läge. Juridiska alternativ är **TX_AUTO_START** (0x01) och **TX_DONT_START** (0x00). Om TX_DONT_START anges måste programmet senare anropa tx_thread_resume för att tråden ska kunna köras.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad tråd skapande.
- TX_THREAD_ERROR: (0x0E) ogiltig tråd kontroll pekare. Antingen är pekaren NULL eller också har tråden redan skapats.
- TX_PTR_ERROR: (0x03) ogiltig start adress för start punkten eller stackområdet är ogiltigt, vanligt vis NULL.
- TX_SIZE_ERROR: (0x05) storleken på stackområdet är ogiltig. Trådar måste ha minst **TX_MINIMUM_STACK** byte för att kunna köras.
- TX_PRIORITY_ERROR: (0x0F) ogiltig tråd prioritet, vilket är ett värde utanför intervallet (0 till (TX_MAX_PRIORITIES-1)).
- TX_THRESH_ERROR: (0x18) ogiltig preemptionthreshold har angetts. Värdet måste vara en giltig prioritet som är mindre än eller lika med trådens inledande prioritet.
- TX_START_ERROR: (0x10) ogiltig markering för automatisk start.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_THREAD     my_thread;
UINT          status;

/* Create a thread of priority 15 whose entry point is
   "my_thread_entry". This thread’s stack area is 1000
   bytes in size, starting at address 0x400000. The
   preemption-threshold is setup to allow preemption of threads
   with priorities ranging from 0 through 14. Time-slicing is
   disabled. This thread is automatically put into a ready
   condition. */
status =  tx_thread_create(&my_thread, "my_thread_name",
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

Ta bort program tråd

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna program tråden. Eftersom den angivna tråden måste vara i ett avslutat eller slutfört tillstånd, kan den här tjänsten inte anropas från en tråd som försöker ta bort sig själv.

> [!IMPORTANT]
> Det är programmets ansvar att hantera det minnes område som är associerat med trådens stack, vilket är tillgängligt när tjänsten har slutförts. Dessutom måste programmet förhindra att en borttagen tråd används.

### <a name="parameters"></a>Parametrar

- **thread_ptr**: pekar mot en tidigare skapad program tråd.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad tråd borttagning.
- TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.
- **TX_DELETE_ERROR**: (0x11) den angivna tråden är inte i ett avslutat eller slutfört tillstånd.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Trådar och timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_THREAD     my_thread;
UINT          status;

/* Delete an application thread whose control block is
   "my_thread". Assume that the thread has already been
   created with a call to tx_thread_create. */
status =  tx_thread_delete(&my_thread);

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

Meddela programmet vid tråd inmatning och avsluta

### <a name="prototype"></a>Prototyp

```C
UINT  tx_thread_entry_exit_notify(TX_THREAD *thread_ptr,
        VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```
### <a name="description"></a>Beskrivning

Den här tjänsten registrerar en funktion för motringning av meddelanden som anropas när den angivna tråden anges eller avslutas. Bearbetningen av aviserings återanropet definieras av programmet.

> [!NOTE]
> Det går inte att anropa någon ThreadX SMP-API med ett uppehålls alternativ i programmets tråd post-eller avslutnings meddelande återanrop.

### <a name="parameters"></a>Parametrar

- **thread_ptr**: pekare till en tidigare skapad tråd.
- **entry_exit_notify**: pekare till programmets tråd post/avslutnings meddelande funktion. Den andra parametern för funktionen post-/avslutnings meddelande anger om en post eller Exit finns. Värdet TX_THREAD_ENTRY (0x00) anger att tråden angavs, medan värdet TX_THREAD_EXIT (0x01) anger att tråden avslutades. Om det här värdet är TX_NULL inaktive ras meddelande.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad registrering av aviserings funktionen för tråd post/avslutning.
- TX_THREAD_ERROR: (0x0E) ogiltig tråd pekare.
- **TX_FEATURE_NOT_ENABLED (0xFF)** Systemet kompilerades med aviserings funktioner inaktiverade.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
TX_THREAD         my_thread;

/* Register the "my_entry_exit_notify" function for monitoring
   the entry/exit of the thread "my_thread." */
status =  tx_thread_entry_exit_notify(&my_thread,
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

Hämtar pekare till tråd som körs för tillfället

### <a name="prototype"></a>Prototyp

```C
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a>Beskrivning

Den här tjänsten returnerar en pekare till den aktuella tråden som körs. Om ingen tråd körs returnerar den här tjänsten en null-pekare.

> [!IMPORTANT]
> Om den här tjänsten anropas från en ISR representerar returvärdet den tråd som körs innan avbrotts hanteraren körs.

### <a name="parameters"></a>Parametrar

Ingen

### <a name="return-values"></a>Retur värden

- tråd pekare: pekare till den aktuella tråden som körs. Om ingen tråd körs TX_NULL det returnerade värdet.

### <a name="allowed-from"></a>Tillåten från

Trådar och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_THREAD     *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr =  tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
   from that thread or an ISR that interrupted that thread.
   Otherwise, this service was called
   from an ISR when no thread was running when the
   interrupt occurred.  */
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

```C
UINT tx_thread_info_get(TX_THREAD *thread_ptr, CHAR **name,
                          UINT *state, ULONG *run_count,
                          UINT *priority,
                          UINT *preemption_threshold,
                          ULONG *time_slice,
                          TX_THREAD **next_thread,
                          TX_THREAD **suspended_thread);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om den angivna tråden.

### <a name="parameters"></a>Parametrar 

- **thread_ptr**: pekar på tråd kontroll block.
- **Name**: pekare till målet för visaren till trådens namn.
- **tillstånd**: pekare till målet för trådens aktuella körnings tillstånd. Möjliga värden är:
    - **TX_READY**: (0x00)
    - **TX_COMPLETED**: (0x01)
    - **TX_TERMINATED**: (protokollnumret 0x02)
    - **TX_SUSPENDED**: (0x03)
    - **TX_SLEEP**: (0x04)
    - **TX_QUEUE_SUSP**: (0x05)
    - **TX_SEMAPHORE_SUSP**: (0x06)
    - **TX_EVENT_FLAG**: (0x07)
    - **TX_BLOCK_MEMORY**: (0x08)
    - **TX_BYTE_MEMORY**: (0x09)
    - **TX_MUTEX_SUSP**: (0x0D)

- **run_count**: pekar mot målet för trådens antal körningar. 
- **prioritet**: pekar mot målets prioritet för tråden.
- **preemption_threshold**: pekar mot mål för trådens avstängningen-tröskelvärde.
- **time_slice**: pekar mot målet för trådens tids segment. 
- **next_thread**: pekare till mål för nästa skapade tråd pekare.
- **suspended_thread**: pekare till destination för pekare till nästa tråd i SUS pensions listan.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad tråd informations hämtning.
- TX_THREAD_ERROR: (0x0E) ogiltig tråd kontroll pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
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
status =  tx_thread_info_get(&my_thread, &name,
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

Hämta information om tråd prestanda

### <a name="prototype"></a>Prototyp

```C
UINT  tx_thread_performance_info_get(TX_THREAD *thread_ptr,
        ULONG *resumptions, ULONG *suspensions,
        ULONG *solicited_preemptions, ULONG *interrupt_preemptions,
        ULONG *priority_inversions, ULONG *time_slices,
        ULONG *relinquishes, ULONG *timeouts, ULONG *wait_aborts,
        TX_THREAD **last_preempted_by);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om den angivna tråden.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste ha skapats med **TX_THREAD_ENABLE_PERFORMANCE_INFO** definierat för att den här tjänsten ska returnera prestanda information.

### <a name="parameters"></a>Parametrar 

- **thread_ptr**: pekare till en tidigare skapad tråd.
- **återupptar**: pekare till målet för antalet återupptagningar av den här tråden.
- **SUS pensioner**: pekare till målet för antalet SUS pensioner av den här tråden.
- **solicited_preemptions**: pekare till målet för antalet preemptions till följd av ett ThreadX API-tjänst anrop som gjorts av den här tråden.
- **interrupt_preemptions**: pekar mot mål för antalet preemptions för den här tråden som ett resultat av avbrotts bearbetningen.
- **priority_inversions**: pekar mot mål för antalet prioritets versioner av den här tråden.
- **time_slices**: pekare till målet för antalet timeslices för den här tråden.
- **låser** sig: pekare till målet för antalet trådar som utförs av den här tråden.
- **timeout**: pekar mot målets antal tids gräns värden för tids gränsen på den här tråden.
- **wait_aborts**: pekar mot mål för antalet väntande avbrott som utförs på den här tråden.
- **last_preempted_by**: pekar mot mål för tråd pekaren som senast blockerade tråden.

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad tråd prestanda Hämta.
- **TX_PTR_ERROR**: (0X03) ogiltig tråd pekare.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```c
TX_THREAD     my_thread;
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
TX_THREAD     *last_preempted_by;

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

Hämta information om tråd system prestanda

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_performance_system_info_get(ULONG *resumptions,
       ULONG *suspensions, ULONG *solicited_preemptions,
       ULONG *interrupt_preemptions, ULONG *priority_inversions,
       ULONG *time_slices, ULONG *relinquishes, ULONG *timeouts,
       ULONG *wait_aborts, ULONG *non_idle_returns,
       ULONG *idle_returns);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om alla trådar i systemet.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste ha skapats med **TX_THREAD_ENABLE_PERFORMANCE_INFO** definierat för att den här tjänsten ska returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **återupptar**: pekar mot mål för det totala antalet trådar som återupptas.
- **SUS pensioner**: pekar mot mål för det totala antalet tråd SUS pensioner.
- **solicited_preemptions**: pekar mot mål för det totala antalet tråd-preemptions som ett resultat av en tråd som anropar en THREADX-API-tjänst.
- **interrupt_preemptions**: pekar mot mål för det totala antalet tråd-preemptions som ett resultat av avbrotts bearbetningen.
- **priority_inversions**: pekar mot mål för det totala antalet tråd prioritets versioner.
- **time_slices**: pekar mot mål för det totala antalet tråd-Time-Slices.
- **låser** sig: pekare till målet för det totala antalet trådar.
- **timeout**: pekar mot mål för det totala antalet tids gränser för tråd upphängning.
- **wait_aborts**: pekar mot mål för det totala antalet avbrott i tråden. 
- **non_idle_returns**: pekar mot mål för antalet gånger som en tråd återgår till systemet när en annan tråd är redo att köras. 
- **idle_returns**: pekar mot mål för antalet gånger som en tråd återgår till systemet när ingen annan tråd är redo att köras (inaktivt system).

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad tråd system prestanda Hämta.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
ULONG         non_idle_returns;
ULONG         idle_returns;

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

Ändra avstängningen-tröskel för program tråd

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_preemption_change(TX_THREAD *thread_ptr,
                          UINT new_threshold, UINT *old_threshold);
```
### <a name="description"></a>Beskrivning

Den här tjänsten ändrar avstängningen-tröskeln för den angivna tråden. Avstängningen-Threshold förhindrar avstängningen av den angivna tråden efter trådar som är lika med eller lägre än värdet för avstängningen-tröskelvärdet.

> [!IMPORTANT]
> Om du använder avstängningen-tröskelvärdet inaktive ras tids segmentering för den angivna tråden.

### <a name="parameters"></a>Parametrar

- **thread_ptr**: pekar mot en tidigare skapad program tråd.
- **new_threshold**: ny avstängningen prioritets nivå (0 till (TX_MAX_PRIORITIES-1)).
- **old_threshold**: pekar på en plats för att returnera föregående avstängningen-tröskelvärde.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckades avstängningen-tröskel ändring.
- TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.
- **TX_THRESH_ERROR**: (0X18) angiven ny avstängningen-tröskel är inte en giltig tråd prioritet (ett annat värde än (0 till (TX_MAX_PRIORITIES-1)) eller är större än (lägre prioritet) än den aktuella tråd prioriteten.
- TX_PTR_ERROR: (0x03) ogiltig pekare till den tidigare preemptionthreshold lagrings platsen.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Trådar och timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```c
TX_THREAD     my_thread;
UINT          my_old_threshold;
UINT          status;

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

Ändra prioritet för program tråd

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_priority_change(TX_THREAD *thread_ptr,
                          UINT new_priority, UINT *old_priority);
```
### <a name="description"></a>Beskrivning

Den här tjänsten ändrar prioriteten för den angivna tråden. Giltiga prioriteter är mellan 0 och (TX_MAX_PRIORITES-1), där 0 representerar den högsta prioritets nivån.

> [!IMPORTANT]
> Avstängningen-tröskelvärdet för den angivna tråden anges automatiskt till den nya prioriteten. Om ett nytt tröskelvärde önskas måste **tx_thread_preemption_changes** tjänsten användas efter det här anropet.

### <a name="parameters"></a>Parametrar

- **thread_ptr**: pekar mot en tidigare skapad program tråd.
- **new_priority**: ny tråd prioritets nivå (0 till (TX_MAX_PRIORITIES-1)).
- **old_priority**: pekar på en plats för att returnera trådens föregående prioritet.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad prioritets ändring.
- TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.
- TX_PRIORITY_ERROR: (0x0F) angiven ny prioritet är inte giltig (ett värde annat än (0 till (TX_MAX_PRIORITIES-1)).
- TX_PTR_ERROR: (0x03) ogiltig pekare till den tidigare prioritets lagrings platsen.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Trådar och timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_THREAD     my_thread;
UINT          my_old_priority;
UINT          status;

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

Lämna kontroll till andra program trådar

### <a name="prototype"></a>Prototyp

```C
VOID tx_thread_relinquish(VOID);
```
### <a name="description"></a>Beskrivning

Den här tjänsten övervärderar processor kontroll till andra trådar som är redo att köra med samma eller högre prioritet.

> [!IMPORTANT]
> Förutom att förhindra kontroll till trådar med samma prioritet, förhindrar den här tjänsten också kontroll till att tråden med högsta prioritet förhindras från att köras på grund av den aktuella trådens avstängningen-inställning.

### <a name="parameters"></a>Parametrar

Ingen

### <a name="return-values"></a>Retur värden

Inget

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
ULONG run_counter_1 =  0;
ULONG run_counter_2 =  0;

/* Example of two threads relinquishing control to
   each other in an infinite loop. Assume that
   both of these threads are ready and have the same
   priority. The run counters will always stay within one
   of each other. */

VOID  my_first_thread(ULONG thread_input)
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

```C
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten återställer den angivna tråden så att den körs vid den Start punkt som definieras vid skapandet av tråden. Tråden måste vara antingen i ett **TX_COMPLETED** eller **TX_TERMINATED** tillstånd för att den ska kunna återställas

> [!IMPORTANT]
> Tråden måste återupptas för att den ska kunna köras igen.

### <a name="parameters"></a>Parametrar 

- **thread_ptr**: pekar mot en tidigare skapad tråd.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad tråd återställning.
- **TX_NOT_DONE**: (0x20) den angivna tråden är inte i ett TX_COMPLETED eller TX_TERMINATED tillstånd.
- TX_THREAD_ERROR: (0x0E) ogiltig tråd pekare.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
TX_THREAD     my_thread;

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
- tx_thread_performance_system_info_get
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

Återuppta inaktive rad program tråd

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten återupptar eller förbereder körning av en tråd som tidigare har avbrutits av ett ***tx_thread_suspend*** -anrop. Dessutom återupptar den här tjänsten trådar som skapats utan automatisk start.

### <a name="parameters"></a>Parametrar

- **thread_ptr**: pekar mot en inaktive rad program tråd.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad tråd återgång.
- **TX_SUSPEND_LIFTED**: (0x19) fastställde tidigare fördröjd avstängning.
- TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.
- **TX_RESUME_ERROR**: (0x12) den angivna tråden har inte pausats eller har tidigare avbrutits av en annan tjänst än **_tx_thread_suspend_**.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_THREAD     my_thread;
UINT          status;

/* Resume the thread represented by "my_thread". */
status =  tx_thread_resume(&my_thread);

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

Pausa den aktuella tråden för angiven tid

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_sleep(ULONG timer_ticks);
```
### <a name="description"></a>Beskrivning

Den här tjänsten gör att den anropande tråden pausas för det angivna antalet timer-Tick. Mängden fysiskt klock slag som är associerad med ett timer-Tick är programspecifik. Den här tjänsten kan endast anropas från en program tråd.

### <a name="parameters"></a>Parametrar

- **timer_ticks**: antalet timer-Tick för att pausa den anropande program tråden, mellan 0 och 0xffffffff. Om 0 anges returnerar tjänsten omedelbart.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad tråd ström.
- **TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.
- **TX_CALLER_ERROR**: (0X13)-tjänsten anropades från en icke-tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
UINT status;

/* Make the calling thread sleep for 100
   timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
   application thread slept for the specified number of
   timer-ticks. */
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
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_smp_core_exclude"></a>tx_thread_smp_core_exclude

Exkludera tråd körning i en uppsättning kärnor

### <a name="prototype"></a>Prototyp

```C
UINT  tx_thread_smp_core_exclude(TX_THREAD *thread_ptr,
                          ULONG exclusion_map);
```
### <a name="description"></a>Beskrivning

Den här funktionen utesluter den angivna tråden från att köras på den eller de kärnor som anges i bit kartan som kallas "*exclusion_map*". Varje bit i "*exclusion_map*" representerar en kärna (bit 0 representerar Core 0 osv.). Om biten anges undantas motsvarande kärna från att köra den angivna tråden.

> [!IMPORTANT]
> Användningen av processor undantag kan orsaka ytterligare bearbetning i tråden till kärn mappnings logik för att hitta den optimala matchningen. Den här bearbetningen har bundits av antalet färdiga trådar.

### <a name="parameters"></a>Parametrar 

- **thread_ptr**: pekare till tråd för att ändra kärn undantag.
- **exclusion_map**: bit karta där en Sit-bit visar att kärnan är exkluderad. Genom att ange ett 0-värde kan tråden köras på alla kärnor (standard).

### <a name="return-values"></a>Retur värden

- TX_SUCCESS: (0x00) lyckad kärn undantag.
- TX_THREAD_ERROR: (0x0E) ogiltig tråd pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, ISR: er, trådar och timers

### <a name="example"></a>Exempel

```C
/* Exclude core 0 for "Thread 0". */
tx_thread_smp_core_exclude(&thread_0, 0x01);
```

### <a name="see-also"></a>Se även

- tx_thread_smp_core_exclude_get
- tx_thread_smp_core_get

## <a name="tx_thread_smp_core_exclude_get"></a>tx_thread_smp_core_exclude_get

Hämtar trådens aktuella kärn undantag

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a>Beskrivning

Den här funktionen returnerar den aktuella huvud undantags listan.

### <a name="parameters"></a>Parametrar

- **thread_ptr**: pekare till tråd från vilken du vill hämta kärn undantaget.
- **exclusion_map_ptr**: målet för den aktuella Core exkluderings-bitars kartan.

### <a name="return-values"></a>Retur värden

- TX_SUCCESS: (0x00) lyckad hämtning av trådens kärn undantag.
- TX_THREAD_ERROR: (0x0E) ogiltig tråd pekare.
- TX_PTR_ERROR: (0x03) ogiltig utelämnande destinations pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, ISR: er, trådar och timers

### <a name="example"></a>Exempel

```C
ULONGexcluded_cores;
/* Retrieve the core exclusion for "Thread 0". */
tx_thread_smp_core_exclude_get(&thread_0, &excluded_cores);
```

### <a name="see-also"></a>Se även

- tx_thread_smp_core_exclude
- tx_thread_smp_core_get

## <a name="tx_thread_smp_core_get"></a>tx_thread_smp_core_get

Hämta kärnan i anroparen som körs

### <a name="prototype"></a>Prototyp

```C
UINT  tx_thread_smp_core_get(void);
```
### <a name="description"></a>Beskrivning

Den här funktionen returnerar kärn-ID för den kärna som kör den här tjänsten.

### <a name="parameters"></a>Parametrar

Ingen

### <a name="return-values"></a>Retur värden

- core_id: ID för den aktuella körnings kärnan (0 till TX_THREAD_SMP_MAX_CORES-1)

### <a name="allowed-from"></a>Tillåten från

Initiering, ISR: er, trådar och timers

### <a name="example"></a>Exempel

```C
UINTcore;
/* Pickup the currently executing core. */
core = tx_thread_smp_core_get();

/* At this point, “core” contains the executing core ID. */
```
### <a name="see-also"></a>Se även

- tx_thread_smp_core_exclude
- tx_thread_smp_core_exclude_get

## <a name="tx_thread_stack_error_notify"></a>tx_thread_stack_error_notify

Registrera återanrop för tråds tack rings meddelande

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```
### <a name="description"></a>Beskrivning

Den här tjänsten registrerar en funktion för motringning av meddelanden för hantering av tråds tack fel. När ThreadX SMP identifierar ett tråds tack fel under körningen, anropar den denna aviserings funktion för att bearbeta felet. Bearbetningen av felet har definierats fullständigt av programmet. Allt från att pausa den överträdande tråden för att återställa hela systemet kan göras.

> [!IMPORTANT]
> ThreadX SMP-biblioteket måste ha skapats med **TX_ENABLE_STACK_CHECKING** definierat för att den här tjänsten ska returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **error_handler**: pekar mot programmets stack fel hanterings funktion. Om det här värdet är TX_NULL inaktive ras meddelandet.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad tråd återställning.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX SMP
   so that thread stack errors can be handled by the application. */
status =  tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
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
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_suspend"></a>tx_thread_suspend

Pausa program tråd

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten pausar den angivna program tråden. En tråd kan anropa den här tjänsten för att inaktivera den.

> [!IMPORTANT]
> Om den angivna tråden redan har pausats av en annan anledning hålls denna SUS Pension internt tills den föregående uppskjutningen har lyfts upp. När detta sker utförs denna avbrytande avstängning av den angivna tråden. Ytterligare avstängnings begär Anden utan tillstånd har ingen påverkan.

Efter inaktive rad måste tråden återupptas genom att ***tx_thread_resume*** köras igen.

## <a name="parameters"></a>Parametrar

- **thread_ptr**: pekar mot en program tråd.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) en lyckad tråd har pausats.
- TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.
- **TX_SUSPEND_ERROR**: (0x14) den angivna tråden är i ett avslutat eller slutfört tillstånd.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_THREAD     my_thread;
UINT          status;

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

Avslutar program tråd

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten avslutar den angivna program tråden oavsett om tråden är inaktive rad eller inte. En tråd kan anropa den här tjänsten för att avsluta sig själv.

> [!IMPORTANT]
> Efter att ha avslut ATS måste tråden återställas för att den ska kunna köras igen.

> [!WARNING]
> Det är programmets ansvar att se till att tråden är i ett tillstånd som är lämpligt för uppsägning. En tråd bör till exempel inte avslutas under kritisk program bearbetning eller i andra komponenter för mellanprogram där den kan lämna sådan bearbetning i ett okänt tillstånd.

### <a name="parameters"></a>Parametrar

- **thread_ptr**: pekar på program tråd.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad tråd avslutas.
- TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Trådar och timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_THREAD     my_thread;
UINT          status;

/* Terminate the thread represented by "my_thread". */
status =  tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
   and cannot execute again until it is reset. */
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
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

Ändra tid – sektor för program tråd

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_time_slice_change(TX_THREAD *thread_ptr,
                          ULONG new_time_slice, ULONG *old_time_slice);
```
### <a name="description"></a>Beskrivning

Den här tjänsten ändrar tids segmentet för den angivna program tråden. Om du väljer en tids gräns för en tråd är det inte säkert att det kör fler än det angivna antalet timer-Tick innan andra trådar av samma eller högre prioritet har möjlighet att köra.

> [!IMPORTANT]
> Om du använder avstängningen-tröskelvärdet inaktive ras tids segmentering för den angivna tråden.

### <a name="parameters"></a>Parametrar

- **thread_ptr**: pekar på program tråd.
- **new_time_slice**: nytt tids segment värde. Giltiga värden är TX_NO_TIME_SLICE och numeriska värden från 1 till 0xFFFFFFFF.
- **old_time_slice**: pekar på plats för lagring av föregående timeslice-värde för den angivna tråden.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) slutförd Time-slice-chans.
- TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.
- TX_PTR_ERROR: (0x03) ogiltig pekare till föregående tid – sektor lagrings plats.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Trådar och timers

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_THREAD     my_thread;
ULONG         my_old_time_slice;
UINT          status;

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

Avbryt avstängning av angiven tråd

### <a name="prototype"></a>Prototyp

```C
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten avbryter vilo läge eller andra objekt avbrott i den angivna tråden. Om vänte tiden avbryts returneras ett TX_WAIT_ABORTED-värde från den tjänst som tråden väntade på.

> [!IMPORTANT]
> Den här tjänsten frigör inte explicit avstängning som görs av tjänsten tx_thread_suspend.

### <a name="parameters"></a>Parametrar

- **thread_ptr**: pekar mot en tidigare skapad program tråd.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad tråd väntan avbryts.
- TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.
- **TX_WAIT_ABORT_ERROR**: (0x1B) den angivna tråden är inte i ett vänte läge.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Ja

### <a name="example"></a>Exempel

```C
TX_THREAD     my_thread;
UINT          status;

/* Abort the suspension condition of "my_thread." */
status =  tx_thread_wait_abort(&my_thread);

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

### <a name="prototype"></a>Prototyp

```C
ULONG tx_time_get(VOID);
```
### <a name="description"></a>Beskrivning

Den här tjänsten returnerar innehållet i den interna system klockan. Varje timertick ökar den interna system klockan med ett. System klockan är inställd på noll under initieringen och kan ändras till ett särskilt värde av tjänsten ***tx_time_set***.

> [!IMPORTANT]
> Den faktiska tiden som varje timer-Tick representerar är programspecifik.

### <a name="parameters"></a>Parametrar

Ingen

### <a name="return-values"></a>Retur värden

- system klock streck: värde för intern, kostnads fri körning, system klocka.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time =  tx_time_get();

/* Current time now contains a copy of the internal system
   clock. */
```
### <a name="see-also"></a>Se även

- tx_time_set

## <a name="tx_time_set"></a>tx_time_set

Anger aktuell tid

### <a name="prototype"></a>Prototyp

```C
VOID tx_time_set(ULONG new_time);
```
### <a name="description"></a>Beskrivning

Den här tjänsten anger den interna system klockan för det angivna värdet. Varje timer-Ticket ökar den interna system klockan med ett.

> [!IMPORTANT]
> Den faktiska tiden som varje timer-Tick representerar är programspecifik.

### <a name="parameters"></a>Parametrar

- **new_time**: en ny tid för att ställa system klockan, giltiga värden är mellan 0 och 0xffffffff.

### <a name="return-values"></a>Retur värden

Inget

### <a name="allowed-from"></a>Tillåten från

Trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

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

Aktivera program-timer

### <a name="prototype"></a>Prototyp

```C
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar den angivna program-timern. Utgångs rutinerna för timers som går ut samtidigt körs i den ordning som de aktiverades.

> [!NOTE]
> Att en förfallen timer med en bild måste återställas via **tx_timer_change** innan den kan aktive ras igen.

### <a name="parameters"></a>Parametrar

- **timer_ptr**: pekar mot en tidigare skapad program-timer.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad aktivering av programtimer.
- **TX_TIMER_ERROR**: (0X15) ogiltig Application timer-pekare.
- **TX_ACTIVATE_ERROR**: (0X17) timern var redan aktiv eller är en timer för en bild som redan har upphört att gälla.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_TIMER     my_timer;
UINT         status;

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

Ändra programmets timer

### <a name="prototype"></a>Prototyp

```C
UINT tx_timer_change(TX_TIMER *timer_ptr,
                          ULONG initial_ticks, ULONG reschedule_ticks);
```
### <a name="description"></a>Beskrivning

Den här tjänsten ändrar utgångs egenskaperna för den angivna program-timern. Timern måste inaktive ras innan den här tjänsten anropas.

> [!IMPORTANT]
> Ett anrop till tjänsten **tx_timer_activate** krävs efter den här tjänsten för att starta timern igen.

### <a name="parameters"></a>Parametrar

- **timer_ptr**: pekar mot ett timer Control-Block.
- **initial_ticks**: anger det ursprungliga antalet Tick för förfallo datum för timer. Giltiga värden är mellan 1 och 0xFFFFFFFF.
- **reschedule_ticks**: anger antalet Tick för alla timer-förfaller efter den första. En noll för den här parametern gör timern till en timer med en bild. Annars, för periodiska timers, är de juridiska värdena mellan 1 och 0xFFFFFFFF.

   > [!NOTE]
   > Att en förfallen timer med en bild måste återställas via **tx_timer_change** innan den kan aktive ras igen.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad ändring av programtimern.
- TX_TIMER_ERROR: (0x15) ogiltig Application timer-pekare.
- TX_TICK_ERROR: (0x16) ogiltigt värde (noll) angavs för inledande Tick.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_TIMER         my_timer;
UINT             status;

/* Change a previously created and now deactivated timer
   to expire every 50 timer ticks, including the initial
   expiration. */
status =  tx_timer_change(&my_timer,50, 50);

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

```C
UINT tx_timer_create(TX_TIMER *timer_ptr, CHAR *name_ptr,
                          VOID (*expiration_function)(ULONG),
                          ULONG expiration_input, ULONG initial_ticks,
                          ULONG reschedule_ticks, UINT auto_activate)
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en programtimer med angiven förfallo funktion och periodisk.

### <a name="parameters"></a>Parametrar

- **timer_ptr**: pekar mot ett timer Control-Block
- **name_ptr**: pekar mot namnet på timern.
- **expiration_function**: program funktion som anropas när timern upphör att gälla.
- **expiration_input**: indatamängden för att skicka till Expires-funktionen när timern upphör att gälla.
- **initial_ticks**: anger det ursprungliga antalet Tick för förfallo datum för timer. Giltiga värden är mellan 1 och 0xFFFFFFFF.
- **reschedule_ticks**: anger antalet Tick för alla timer-förfaller efter den första. En noll för den här parametern gör timern till en timer med en bild. Annars, för periodiska timers, är de juridiska värdena mellan 1 och 0xFFFFFFFF.

   > [!NOTE]
   > När en timer för en bild har gått ut måste den återställas via tx_timer_change innan den kan aktive ras igen.

- **auto_activate**: anger om timern aktive ras automatiskt när den skapas. Om det här värdet är **TX_AUTO_ACTIVATE** (0x01) blir timern aktiv. Annars, om värdet **TX_NO_ACTIVATE** (0x00) är markerat, skapas timern i ett icke-aktivt tillstånd. I det här fallet är ett efterföljande **_tx_timer_activate_** tjänst anrop nödvändigt för att hämta den timer som faktiskt startades.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckad programgenerering av program.
- TX_TIMER_ERROR: (0x15) ogiltig Application timer-pekare. Antingen är pekaren NULL eller också har timern redan skapats.
- TX_TICK_ERROR: (0x16) ogiltigt värde (noll) angavs för inledande Tick.
- TX_ACTIVATE_ERROR: (0x17) ogiltig aktivering har valts.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_TIMER     my_timer;
UINT         status;

/* Create an application timer that executes
   "my_timer_function" after 100 ticks initially and then
   after every 25 ticks. This timer is specified to start
   immediately! */
status =  tx_timer_create(&my_timer,"my_timer_name",
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

Inaktivera Application timer

### <a name="prototype"></a>Prototyp

```C
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar den angivna programtimern. Om timern redan är inaktive rad har den här tjänsten ingen påverkan.

### <a name="parameters"></a>Parametrar 

- **timer_ptr**: pekar mot en tidigare skapad program-timer.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) slutförde inaktive ring av program.
- TX_TIMER_ERROR: (0x15) ogiltig Application timer-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_TIMER     my_timer;
UINT         status;

/* Deactivate an application timer. Assume that the
   application timer has already been created. */
status =  tx_timer_deactivate(&my_timer);

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

Ta bort program timer

### <a name="prototype"></a>Prototyp

```C
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna program-timern.

> [!IMPORTANT]
> Det är programmets ansvar att förhindra användning av en borttagen timer.

### <a name="parameters"></a>Parametrar 

- **timer_ptr**: pekar mot en tidigare skapad program-timer.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) en slutförd borttagning av program timer.
- TX_TIMER_ERROR: (0x15) ogiltig Application timer-pekare.
- TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```c
TX_TIMER     my_timer;
UINT         status;

/* Delete application timer. Assume that the application
   timer has already been created. */
status =  tx_timer_delete(&my_timer);

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

```C
UINT tx_timer_info_get(TX_TIMER *timer_ptr, CHAR **name,
                          UINT *active, ULONG *remaining_ticks,
                          ULONG *reschedule_ticks,
                          TX_TIMER **next_timer)
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om den angivna program-timern.

### <a name="parameters"></a>Parametrar

- **timer_ptr**: pekar mot en tidigare skapad program-timer.
- **Name**: pekare till målet för visaren till timerns namn.
- **aktiv**: pekare till målet för den timer-aktiva indikeringen. Om timern är inaktiv eller om den här tjänsten anropas från själva timern returneras ett TX_FALSE-värde. Annars returneras ett TX_TRUE-värde om timern är aktiv.
- **remaining_ticks**: pekar mot mål för antalet timer-Tick kvar innan timern upphör att gälla.
- **reschedule_ticks**: pekar mot mål för antalet timer-Tick som ska användas för att automatiskt schemalägga denna timer. Om värdet är noll är timern en One-bild och kommer inte att omplaneras.
- **next_timer**: pekar på destinationen för visaren för nästa skapade program-timer.

> [!NOTE]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) information om slutförd timer-information.
- TX_TIMER_ERROR: (0x15) ogiltig Application timer-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="preemption-possible"></a>Avstängningen möjlig

Inga

### <a name="example"></a>Exempel

```C
TX_TIMER     my_timer;
CHAR         *name;
UINT         active;
ULONG        remaining_ticks;
ULONG        reschedule_ticks;
TX_TIMER     *next_timer;
UINT         status;

/* Retrieve information about the previously created
   application timer "my_timer." */
status =  tx_timer_info_get(&my_timer, &name,
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

Hämta information om timer-prestanda

### <a name="prototype"></a>Prototyp

```C
UINT  tx_timer_performance_info_get(TX_TIMER *timer_ptr,
        ULONG *activates, ULONG *reactivates,
        ULONG *deactivates, ULONG *expirations,
        ULONG *expiration_adjusts);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om den angivna program tids gränsen.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste skapas med **TX_TIMER_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar 

- **timer_ptr**: pekare till tidigare skapad timer.
- **aktiverar**: pekar mot mål för antalet aktiverings begär Anden som utförts i denna timer.
- **återaktiverar**: pekare till målet för antalet automatiska återaktiveringar som utförs på denna periodiska timer.
- **inaktive ras**: pekare till målet för antalet förfrågningar om inaktivitet som utförts på denna timer.
- **förfaller**: pekar mot mål för antalet förfallo datum för den här timern.
- **expiration_adjusts**: pekar mot mål för antalet interna utgångs justeringar som utförts i denna timer. De här justeringarna görs i den tids lösa bearbetningen för timers som är större än standard storleken för timer-listan (som standard timers med förfallo datum som är större än 32 Tick).

> [!IMPORTANT]
> Om du anger en TX_NULL för vilken parameter som helst är parametern inte obligatorisk.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0x00) prestanda för slutförd timer.
- **TX_PTR_ERROR**: (0X03) ogiltig timer-pekare.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
TX_TIMER     my_timer;
ULONG        activates;
ULONG        reactivates;
ULONG        deactivates;
ULONG        expirations;
ULONG        expiration_adjusts;

/* Retrieve performance information on the previously created
   timer.  */
status =  tx_timer_performance_info_get(&my_timer, &activates,
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

Hämta information om system prestanda för timer

### <a name="prototype"></a>Prototyp

```C
UINT  tx_timer_performance_system_info_get(ULONG *activates,
        ULONG *reactivates, ULONG *deactivates,
        ULONG *expirations, ULONG *expiration_adjusts);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar prestanda information om alla program timers i systemet.

> [!IMPORTANT]
> ThreadX SMP-biblioteket och programmet måste skapas med **TX_TIMER_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.

### <a name="parameters"></a>Parametrar

- **aktiverar**: pekar mot mål för det totala antalet aktiverings begär Anden som utförts på alla timers.
- **återaktiverar**: pekar mot mål för det totala antalet automatiska återaktivitet som utförts på alla periodiska timers.
- **inaktive ras**: pekare till mål för det totala antalet begär Anden om inaktive ring som utförts för alla timers.
- **förfaller**: pekar mot mål för det totala antalet förfallo datum för alla timers.
- **expiration_adjusts**: pekar mot mål för det totala antalet interna utgångs justeringar som utförts för alla timers. De här justeringarna görs i den tids lösa bearbetningen för timers som är större än standard storleken för timer-listan (som standard timers med förfallo datum som är större än 32 Tick).

> [!IMPORTANT]
> Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS**: (0X00) lyckades system prestanda Hämta.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers och ISR: er

### <a name="example"></a>Exempel

```C
ULONG     activates;
ULONG     reactivates;
ULONG     deactivates;
ULONG     expirations;
ULONG     expiration_adjusts;

/* Retrieve performance information on all previously created
   timers.  */
status =  tx_timer_performance_system_info_get(&activates,
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

## <a name="tx_timer_smp_core_exclude"></a>tx_timer_smp_core_exclude

Uteslut timer-körning i en uppsättning kärnor

### <a name="prototype"></a>Prototyp

```C
UINT  tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);
```
### <a name="description"></a>Beskrivning

Den här funktionen utesluter den angivna timern från att köras på de kärnor som anges i bit kartan med namnet "*exclusion_map*". Varje bit i "*exclusion_map*" representerar en kärna (bit 0 representerar Core 0 osv.). Om biten anges undantas motsvarande kärna från att köra den angivna timern.

> [!IMPORTANT]
> Användningen av processor undantag kan orsaka ytterligare bearbetning i tråden till kärn mappnings logik för att hitta den optimala matchningen. Den här bearbetningen har bundits av antalet färdiga trådar.

### <a name="parameters"></a>Parametrar

- **timer_ptr**: pekar mot timer för att ändra kärn undantag.
- **exclusion_map**: bit karta där en Sit-bit visar att kärnan är exkluderad. Om du anger ett 0-värde kan timern köras på alla kärnor (standard).

### <a name="return-values"></a>Retur värden

- **TX_SUCCESS** (0X00) lyckad kärn undantag.
- **TX_TIMER_ERROR** (0X0E) ogiltig timer-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, ISR: er, trådar och timers

### <a name="example"></a>Exempel

```C
/* Exclude core 0 for "Timer 0". */
tx_timer_smp_core_exclude(&timer_0, 0x01);
```

### <a name="see-also"></a>Se även

- tx_timer_smp_core_exclude_get

## <a name="tx_timer_smp_core_exclude_get"></a>tx_timer_smp_core_exclude_get

Hämtar timerns aktuella kärn undantag

### <a name="prototype"></a>Prototyp

```C
UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a>Beskrivning

Den här funktionen returnerar den aktuella huvud undantags listan.

### <a name="parameters"></a>Parametrar

- **timer_ptr**: pekare till timer från vilken du vill hämta kärn undantaget.
- **exclusion_map_ptr**: målet för den aktuella Core exkluderings-bitars kartan.

### <a name="return-values"></a>Retur värden

- TX_SUCCESS: (0x00) lyckad hämtning av timerns kärn undantag.
- TX_TIMER_ERROR: (0x0E) ogiltig timer-pekare.
- TX_PTR_ERROR: (0x03) ogiltig utelämnande destinations pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, ISR: er, trådar och timers

### <a name="example"></a>Exempel

```C
ULONGexcluded_cores;

/* Retrieve the core exclusion for "Timer 0". */
tx_timer_smp_core_exclude_get(&timer_0,&excluded_cores);
```
### <a name="see-also"></a>Se även

- tx_timer_smp_core_exclude