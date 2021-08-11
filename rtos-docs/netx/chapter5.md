---
title: Kapitel 5 – Azure RTOS NetX-nätverksdrivrutiner
description: Det här kapitlet innehåller en beskrivning av nätverksdrivrutiner för Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 09/11/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0770d6beb8b2715a8e5dddf1bdf187c0cd1d5ffd74e7bea9b7ff9bdf1785d088
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801928"
---
# <a name="chapter-5---netx-network-drivers"></a>Kapitel 5 – NetX-nätverksdrivrutiner

Det här kapitlet innehåller en beskrivning av nätverksdrivrutiner för NetX. Den information som visas är utformad för att hjälpa utvecklare att skriva programspecifika nätverksdrivrutiner för Azure RTOS NetX.

## <a name="driver-introduction"></a>Introduktion till drivrutin

Den NX_IP strukturen innehåller allt för att hantera en enskild IP-instans. Detta omfattar allmän information om TCP/IP-protokollet samt den programspecifika fysiska nätverksdrivrutinens startrutin. Drivrutinens startrutin definieras under den ***nx_ip_create*** tjänsten. Ytterligare enheter kan läggas till i  IP-instansen via nx_ip_interface_attach tjänsten.

Kommunikationen mellan NetX och programmets nätverksdrivrutin sker  via den NX_IP_DRIVER begärandestrukturen. Den här strukturen definieras oftast lokalt på anroparstacken och släpps därför efter att drivrutinen och den anropande funktionen returneras. Strukturen definieras på följande sätt.

```C
typedef struct NX_IP_DRIVER_STRUCT
{
    UINT nx_ip_driver_command;
    UINT nx_ip_driver_status;
    ULONG nx_ip_driver_physical_address_msw;
    ULONG nx_ip_driver_physical_address_lsw;
    NX_PACKET *nx_ip_driver_packet;
    ULONG *nx_ip_driver_return_ptr;
    NX_IP *nx_ip_driver_ptr;
    NX_INTERFACE *nx_ip_driver_interface;
} NX_IP_DRIVER;
```

## <a name="driver-entry"></a>Drivrutinspost

NetX anropar funktionen för inmatning av nätverksdrivrutiner för initiering av drivrutiner och för att skicka paket och för olika kontroll- och statusåtgärder, inklusive initiering och aktivering av nätverksenheten. NetX utfärdar kommandon till nätverksdrivrutinen genom att ange fältet ***nx_ip_driver_command** _ i *begärandestrukturen* _ NX_IP_DRIVER * . Drivrutinspostfunktionen har följande format:

```C
VOID my_driver_entry(NX_IP_DRIVER *request);
```

## <a name="driver-requests"></a>Drivrutinsbegäranden

NetX skapar drivrutinsbegäran med ett visst kommando och anropar drivrutinspostfunktionen för att köra kommandot. Eftersom varje nätverksdrivrutin har en enda postfunktion gör NetX alla begäranden via datastrukturen för drivrutinsbegäran. Den ***nx_ip_driver_command*** som är medlem i datastrukturen för drivrutinsbegäran **(NX_IP_DRIVER)** definierar begäran. Statusinformation rapporteras tillbaka till anroparen i medlemmen ***nx_ip_driver_status***. Om det här **NX_SUCCESS** har drivrutinsbegäran slutförts.

NetX serialiserar all åtkomst till drivrutinen. Drivrutinen behöver därför inte hantera flera trådar asynkront anropar entry-funktionen. Observera att enhetsdrivrutinsfunktionen körs med IP-adressen mutex låst. Den interna funktionen för enhetsdrivrutiner får därför inte blockera sig själv.

Vanligtvis hanterar enhetsdrivrutinen även avbrott. Därför måste alla drivrutinsfunktioner vara avbrottssäkra.

### <a name="driver-initialization"></a>Initiering av drivrutin

Även om den faktiska initieringsbearbetningen av drivrutiner är programspecifik består den vanligtvis av datastruktur och initiering av fysisk maskinvara. Informationen som krävs från NetX för initiering av drivrutinen är IP Maximum Transmission Unit (MTU), vilket är antalet byte som är tillgängligt för NYTTOLASTEN på IP-nivå, inklusive IP-huvud) och om det fysiska gränssnittet behöver logisk-till-fysisk mappning. Drivrutinen behöver

för att konfigurera gränssnittets MTU genom att ange värdet i ***nx_interface_ip_mtu_size** _ i strukturen _ *NX_INTERFACE** .

Enhetsdrivrutinen måste också konfigurera värdet i ***nx_ip_interface_address_mapping_needed*** in

**NX_INTERFACE** netX om gränssnittsadressmappning krävs eller inte. Om adressmappning krävs ansvarar drivrutinen för att konfigurera gränssnittet med en giltig MAC-adress och ange MAC-adressen till NetX.

När nätverksdrivrutinen tar emot NX_LINK INITIALIZE-begäran från NetX, tar den emot en pekare till IP-kontrollblocket som en del NX_IP_DRIVER det kontrollblock för begäran som visas ovan.

När programmet ***anropar nx_ip_create*** skickar IP-hjälptråden en drivrutinsbegäran med kommandot inställt på NX_LINK_INITIALIZE till drivrutinen för att initiera dess fysiska nätverksgränssnitt. Följande NX_IP_DRIVER medlemmar används för att initiera begäran.

| NX_IP_DRIVER medlem    | Innebörd |
|------------------------|-----------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INITIALIZE |
| nx_ip_driver_ptr       | Pekare till IP-instansen. Det här värdet ska sparas av drivrutinen så att drivrutinsfunktionen kan hitta DEN IP-instans som ska användas. |
| nx_ip_driver_interface | Pekare till nätverksgränssnittsstrukturen i IP-instansen. Den här informationen ska sparas av drivrutinen. Vid mottagning av paket ska drivrutinen använda gränssnittsstrukturinformationen när paketet skickas upp i stacken. |
| nx_ip_driver_status    | Slutförandestatus. Om drivrutinen inte kan initiera det angivna gränssnittet till IP-instansen returneras en felstatus som inte är noll.                                                                                           |


> [!IMPORTANT]
> *De flesta drivrutinskommandona anropas från IP-hjälptråden som skapades för IP-instansen. Därför bör drivrutinsrutinen undvika att utföra blockerande åtgärder, eller så kan IP-hjälptråden stanna av, vilket orsakar obegränsade fördröjningar för program som förlitar sig på IP-tråden.*

### <a name="enable-link"></a>Aktivera länk  

Därefter aktiverar IP-hjälptråden det fysiska nätverket genom att ange drivrutinskommandot till NX_LINK_ENABLE i drivrutinsbegäran och skicka begäran till nätverksdrivrutinen. Detta sker strax efter att IP-hjälptråden har slutfört initieringsbegäran. Att aktivera länken kan vara så enkelt som att ange nx_interface_link_up i gränssnittsinstansen. Men det kan också handla om manipulering av den fysiska maskinvaran. Följande NX_IP_DRIVER medlemmar används för att aktivera länkbegäran.

| NX_IP_DRIVER medlem    | Innebörd |
|------------------------|------------------------------------------|
| nx_ip_driver_command   | NX_LINK_ENABLE                                                                                                          |
| nx_ip_driver_ptr       | Pekare till IP-instans                                                                                                  |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen                                                                                       |
| nx_ip_driver_status    | Slutförandestatus. Om drivrutinen inte kan aktivera det angivna gränssnittet returneras en felstatus som inte är noll. |



### <a name="disable-link"></a>Inaktivera länk  

Den här begäran görs av NetX under borttagningen av en IP-instans av tjänsten ***nx_ip_delete** _ . Eller så kan ett program utfärda det här kommandot för att tillfälligt inaktivera länken för att spara ström. Den här tjänsten inaktiverar det fysiska nätverksgränssnittet på IP-instansen. Bearbetningen för att inaktivera länken kan vara så enkel som att rensa _nx_interface_link_up*-flaggan i gränssnittsinstansen. Men det kan också handla om manipulering av den fysiska maskinvaran. Vanligtvis är det en omvänd åtgärd av åtgärden ***Aktivera**_ länk. När länken har inaktiverats aktiverar programbegäran _ *_Aktivera länk_** gränssnittet. Följande NX_IP_DRIVER används för att inaktivera länkbegäran.

| NX_IP_DRIVER medlem    | Innebörd |
|------------------------|--------------------------------------|
| nx_ip_driver_command   | NX_LINK_DISABLE |
| nx_ip_driver_ptr       | Pekare till IP-instans |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen |
| nx_ip_driver_status    | Slutförandestatus. Om drivrutinen inte kan inaktivera det angivna gränssnittet i IP-instansen returneras en felstatus som inte är noll. |


### <a name="uninitialize-link"></a>Uninitialize Link  

Den här begäran görs av NetX under borttagningen av en IP-instans av ***nx_ip_delete tjänsten.*** Den här begäran avinitierar gränssnittet och frigör alla resurser som skapats under initieringsfasen. Vanligtvis är det en omvänd åtgärd för ***åtgärden Initiera*** länk. När gränssnittet är oinitalt kan enheten inte användas förrän gränssnittet har initierats igen.

Följande NX_IP_DRIVER används för att inaktivera länkbegäran.

| NX_IP_DRIVER medlem  | Innebörd                |
|----------------------|------------------------|
| nx_ip_driver_command | NX_LINK_UNINITIALZE    |
| nx_ip_driver_ptr     | Pekare till IP-instans |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen |
| nx_ip_driver_status    | Slutförandestatus. Om drivrutinen inte kan initiera det angivna gränssnittet till IP-instansen returneras felstatusen "inte noll". |


### <a name="packet-send"></a>Skicka paket  

Denna begäran görs under intern BEARBETNING av IP-överföring, bearbetning, som alla NetX-protokoll använder för att överföra paket (utom ARP, RARP). När du tar emot kommandot packet send *nx_packet_prepend_ptr* pekar på början av paketet som ska skickas, vilket är början av IP-huvudet.
*nx_packet_length* anger den totala storleken (i byte) för de data som överförs. Om *nx_packet_next* är giltigt lagras det utgående IP-datagrammet i flera paket. Drivrutinen måste följa det kedjade paketet och överföra hela ramen. Observera att ett giltigt dataområde i varje länkat paket lagras *mellan nx_packet_prepend_ptr* *och nx_packet_append_ptr*.

Drivrutinen ansvarar för att skapa ett fysiskt huvud. Om fysisk adress till IP-adressmappning krävs (till exempel Ethernet) har IP-lagret redan löst MAC-adressen. MAC-måladressen skickas från IP-instansen som lagras *i nx_ip_driver_physical_address_msw och nx_ip_driver_physical_address_lsw.*

När du har lagt till det fysiska huvudet anropar paketens sändningsbearbetning sedan drivrutinens utdatafunktion för att överföra paketet.

Följande NX_IP_DRIVER används för begäran om paketsändning.

| NX_IP_DRIVER medlem               | Innebörd |
|-----------------------------------|---------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_PACKET_SEND |
| nx_ip_driver_ptr                  | Pekare till IP-instans |
| nx_ip_driver_packet               | Pekare till det paket som ska skickas |
| nx_ip_driver_interface            | Pekare till gränssnittsinstansen.             |
| nx_ip_driver_physical_address_msw | Mest betydande 32-bitars fysisk adress (endast om fysisk mappning behövs) |
| nx_ip_driver_physical_address_lsw | Minst viktiga 32-bitars fysisk adress (endast om fysisk mappning behövs)    |
| nx_ip_driver_status               | Slutförandestatus. Om drivrutinen inte kan skicka paketet returneras en felstatus som inte är noll.  |

### <a name="packet-broadcast"></a>Paketsändning  
Den här begäran är nästan identisk med begäran om att skicka paket. Den enda skillnaden är att fälten för den fysiska måladressen är inställda på ETHERNET-broadcast-MAC-adressen. Följande NX_IP_DRIVER används för paketsändningsbegäran.

| NX_IP_DRIVER medlem                | Innebörd          |
|------------------------------------|--------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_PACKET_BROADCAST |
| nx_ip_driver_ptr                   | Pekare till IP-instans  |
| nx_ip_driver_packet                | Pekare till paketet till slutet |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF sändning) |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF sändning) |
| nx_ip_driver_interface             | Pekare till gränssnittsinstansen. |
| nx_ip_driver_status                | Slutförandestatus. Om drivrutinen inte kan skicka paketet returneras en felstatus som inte är noll. |

### <a name="arp-send"></a>Skicka ARP  

Den här begäran liknar också begäran om att skicka IP-paket.
Den enda skillnaden är att Ethernet-huvudet anger ett ARP-paket i stället för ett IP-paket, och fälten för den fysiska måladressen är inställda på MAC-broadcast-adress. Följande NX_IP_DRIVER medlemmar används för att skicka ARP-begäran.

| **NX_IP_DRIVER medlem** | **Innebörd** |
| --- | --- |
| nx_ip_driver_command | NX_LINK_ARP_SEND |
| nx_ip_driver_ptr | Pekare till IP-instans. |
| nx_ip_driver_packet | Pekare till paketet som ska skickas. |
| nx_ip_driver_physical_address_msw | 0x0000FFFF (broadcast) |
| nx_ip_driver_physical_address_lsw | 0xFFFFFFFF (broadcast) |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen. |
| nx_ip_driver_status | Slutförandestatus. Om drivrutinen inte kan skicka ARP-paketet returneras en felstatus som inte är noll. |

*Om fysisk mappning inte behövs krävs ingen implementering av den här begäran.*

### <a name="arp-response-send"></a>ARP-svarssändning  

Den här begäran är nästan identisk med begäran om att skicka ARP-paket. Den enda skillnaden är att fälten för den fysiska måladressen skickas från IP-instansen. Följande medlemmar NX_IP_DRIVER för begäran om att skicka ARP-svar.

| NX_IP_DRIVER medlem               | Innebörd |
|-----------------------------------| ------------------------------------|
| nx_ip_driver_command              | NX_LINK_ARP_RESPONSE_SEND |
| nx_ip_driver_ptr                  | Pekare till IP-instans |
| nx_ip_driver_packet               | Pekare till det paket som ska skickas|
| nx_ip_driver_physical_address_msw | Mest betydande 32-bitars fysisk adress |
| nx_ip_driver_physical_address_lsw | Minst viktiga 32-bitars fysisk adress                     |
| nx_ip_driver_interface            | Pekare till gränssnittsinstansen |
| nx_ip_driver_status               | Slutförandestatus. Om drivrutinen inte kan skicka ARP-paketet returneras en felstatus som inte är noll. |

> [!NOTE]
> *Om fysisk mappning inte behövs krävs ingen implementering av den här begäran.*

### <a name="rarp-send"></a>SKICKA RARP  

Den här begäran är nästan identisk med begäran om att skicka ARP-paket. De enda skillnaderna är typen av pakethuvud och fälten för fysiska adresser krävs inte eftersom det fysiska målet alltid är en broadcast-adress.

Följande NX_IP_DRIVER används för RARP-begäran om att skicka.

| NX_IP_DRIVER medlem               | Innebörd |
|-----------------------------------|---------------------------------|
| nx_ip_driver_command              |NX_LINK_RARP_SEND |
| nx_ip_driver_ptr                  | Pekare till IP-instans |
| nx_ip_driver_packet               | Pekare till det paket som ska skickas |
| nx_ip_driver_physical_address_msw | 0x0000FFFF (broadcast) |
| nx_ip_driver_physical_address_lsw | 0xFFFFFFFF (broadcast) |
| NX_IP_DRIVER medlem               | Innebörd |
| nx_ip_driver_interface            | Pekare till gränssnittsinstansen |
| nx_ip_driver_status               | Slutförandestatus. Om drivrutinen inte kan skicka RARP-paketet returneras felstatusen "inte noll".  |

> [!NOTE]
> *Program som kräver RARP-tjänsten måste implementera det här kommandot.*

### <a name="multicast-group-join"></a>Multicast-gruppkoppling  

Den här begäran görs med ***den nx_igmp_multicast_interface anslutningstjänsten.*** Nätverksdrivrutinen tar den angivna multicast-gruppadressen och uppsättningar upp det fysiska mediet för att acceptera inkommande paket från den multicast-gruppadressen. Observera att för drivrutiner som inte stöder multicast-filter kan logiken för att ta emot drivrutinen behöva vara i ett icke-filtrerat läge. I det här fallet kan drivrutinen behöva filtrera inkommande bildrutor baserat på MAC-måladressen, vilket minskar mängden trafik som skickas till IP-instansen. Följande NX_IP_DRIVER-medlemmar används för multicast-gruppkopplingsbegäran.

| NX_IP_DRIVER medlem               | Innebörd |
|-----------------------------------|-----------------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_MULTICAST_JOIN                                                |
| nx_ip_driver_ptr                  | Pekare till IP-instans                                                |
| nx_ip_driver_physical_address_msw | Viktigaste 32-bitars fysiska multicast-adress                |
| nx_ip_driver_physical_address_lsw | Minst viktiga 32-bitars fysisk multicast-adress               |
| nx_ip_driver_interface            | Pekare till gränssnittsinstansen                                     |
| nx_ip_driver_status               | Slutförandestatus. Om drivrutinen inte kan ansluta till multicast-gruppen returneras felstatusen "inte noll". |


### <a name="multicast-group-leave"></a>Lämna multicast-grupp  

Den här begäran anropas  uttryckligen genom att anropa nx_igmp_multicast_leave tjänsten. Drivrutinen tar bort den angivna Ethernet-multicast-adressen från multicast-listan. När en värd har lämnat en multicast-grupp tas paket i nätverket med den här Ethernet-multicast-adressen inte längre emot av den här IP-instansen. Följande NX_IP_DRIVER används för multicast-gruppledarbegäran.

| NX_IP_DRIVER medlem               | Innebörd |
|-----------------------------------|-----------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_MULTICAST_LEAVE |
| nx_ip_driver_ptr                  | Pekare till IP-instans |
| nx_ip_driver_physical_address_msw | Flest 32 bitar fysisk multicast-identifiering |
| nx_ip_driver_physical_address_lsw | Minst 32 bitar fysisk multicast-adress |
| nx_ip_driver_interface            | Pekare till gränssnittsinstansen |
| nx_ip_driver_status               | Slutförandestatus. Om drivrutinen inte kan lämna multicast-gruppen returneras felstatusen "inte noll". |


### <a name="attach-interface"></a>Anslut gränssnitt  

Den här begäran anropas från NetX till enhetsdrivrutinen, så att drivrutinen kan associera drivrutinsinstansen med motsvarande IP-instans och instansen av det fysiska gränssnittet inom IP-adressen. Följande NX_IP_DRIVER-medlemmar används för begäran om att koppla gränssnitt.

| NX_IP_DRIVER medlem    | Innebörd |
|------------------------|-------------------------------------------------|
| nx_ip_driver_command   | X_LINK_INTERFACE_ATTACH |
| nx_ip_driver_ptr       | Pekare till IP-instans |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen. |
| nx_ip_driver_status    | Slutförandestatus. Om drivrutinen inte kan koppla från det angivna gränssnittet till IP-instansen returneras felstatusen "inte noll".  |


### <a name="detach-interface"></a>Koppla från gränssnitt  

Den här begäran anropas av NetX till enhetsdrivrutinen, så att drivrutinen kan ta bort associationen mellan drivrutinsinstansen och motsvarande IP-instans och instansen av det fysiska gränssnittet inom IP-adressen. Följande NX_IP_DRIVER-medlemmar används för begäran om att koppla gränssnitt.

| NX_IP_DRIVER medlem    | Innebörd |
|------------------------|---------------------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_DETACH |
| nx_ip_driver_ptr       | Pekare till IP-instans |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen. |
| nx_ip_driver_status    | Slutförandestatus. Om drivrutinen inte kan koppla det angivna gränssnittet till IP-instansen returneras felstatusen "inte noll". |

### <a name="get-link-status"></a>Hämta länkstatus  

Programmet kan fråga nätverksgränssnittslänkens status med hjälp av  ***NetX-nx_ip_interface_status_check tjänsten*** för alla gränssnitt på värden. Mer information om dessa tjänster finns i kapitel 4, "Beskrivning av NetX Services" på sidan 107.

Länkstatusen finns i nx_interface_link_up *i* den NX_INTERFACE struktur som pekar *nx_ip_driver_interface* pekaren. Följande NX_IP_DRIVER används för begäran om länkstatus.

| NX_IP_DRIVER medlem     | Innebörd                                                                                                      |
|-------------------------|--------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_STATUS                                                                                           |
| nx_ip_driver_ptr        | Pekare till IP-instans                                                                                       |
| nx_ip_driver_return_ptr | Pekare till målet för att placera statusen.                                                              |
| nx_ip_driver_interface  | Pekare till gränssnittsinstansen                                                                            |
| nx_ip_driver_status     | Slutförandestatus. Om drivrutinen inte kan hämta specifik status returneras felstatusen "inte noll". |
|                         |                                                                                                              |

> [!NOTE]
> ***nx_ip_status_check** fortfarande tillgänglig för att kontrollera status för det primära gränssnittet. Programutvecklare uppmanas dock att använda gränssnittsspecifika tjänstspecifika **nx_ip_interface_status_check.***

### <a name="get-link-speed"></a>Hämta länkhastighet  

Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen lagrar länkens linjehastighet i det angivna målet. Följande NX_IP_DRIVER medlemmar används för begäran om länklinjehastighet.

| NX_IP_DRIVER medlem     | Innebörd |
|-------------------------|---------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_SPEED |
| nx_ip_driver_ptr        | Pekare till IP-instans |
| nx_ip_driver_return_ptr | Pekare till målet för att placera linjehastigheten |
| nx_ip_driver_interface  | Pekare till gränssnittsinstansen |
| nx_ip_driver_status     | Slutförandestatus. Om drivrutinen inte kan hämta hastighetsinformation returneras felstatusen "inte noll".
 |


> [!NOTE]
> *Den här begäran används inte internt av NetX, så dess implementering är valfri.*

### <a name="get-duplex-type"></a>Hämta duplex-typ  

Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen lagrar länkens duplex-typ i det angivna målet. Följande NX_IP_DRIVER används för begäran av duplex-typ.

| NX_IP_DRIVER medlem     | Innebörd |
|-------------------------|-----------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_DUPLEX_TYPE |
| nx_ip_driver_ptr        | Pekare till IP-instans |
| nx_ip_driver_return_ptr | Pekare till målet för att placera duplex-typen |
| nx_ip_driver_interface  | Pekare till gränssnittsinstansen |
| nx_ip_driver_status     | Slutförandestatus. Om drivrutinen inte kan hämta duplex-information returneras en felstatus som inte är noll.
 |


> [!NOTE]
> *Den här begäran används inte internt av NetX, så dess implementering är valfri.*

### <a name="get-error-count"></a>Hämta antal fel  

Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen lagrar länkens felantal i det angivna målet. För att stödja den här funktionen måste drivrutinen spåra åtgärdsfel. Följande NX_IP_DRIVER medlemmar används för begäran om antal länkfel.

| NX_IP_DRIVER medlem     | Innebörd                                                                                                  |
|-------------------------|----------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_ERROR_COUNT                                                                                  |
| nx_ip_driver_ptr        | Pekare till IP-instans                                                                                   |
| nx_ip_driver_return_ptr | Pekare till målet för att placera felantalet                                                      |
| nx_ip_driver_interface  | Pekare till gränssnittsinstansen                                                                        |
| nx_ip_driver_status     | Slutförandestatus. Om drivrutinen inte kan hämta felantal returneras felstatusen inte noll. |


> [!NOTE]
> *Den här begäran används inte internt av NetX, så dess implementering är valfri.*

### <a name="get-receive-packet-count"></a>Hämta antal inkommande paket  

Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen lagrar länkens antal mottagna paket i det angivna målet. För att stödja den här funktionen måste drivrutinen hålla reda på antalet mottagna paket. Följande NX_IP_DRIVER används för begäran om att ta emot länkpaket.

| NX_IP_DRIVER medlem     | Innebörd                                                                                                    |
|-------------------------|------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_RX_COUNT                                                                                       |
| nx_ip_driver_ptr        | Pekare till IP-instans                                                                                     |
| nx_ip_driver_return_ptr | Pekare till målet för att placera antalet inkommande paket                                               |
| nx_ip_driver_interface  | Pekare till det fysiska nätverksgränssnittet                                                                  |
| nx_ip_driver_status     | Slutförandestatus. Om drivrutinen inte kan ta emot antal returneras en felstatus som inte är noll. |


> [!NOTE]
> *Den här begäran används inte internt av NetX, så dess implementering är valfri.*

### <a name="get-transmit-packet-count"></a>Hämta antal överföringspaket  

Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen lagrar länkens antal överföringspaket i det angivna målet. För att stödja den här funktionen måste drivrutinen hålla reda på varje paket som överförs i varje gränssnitt. Följande NX_IP_DRIVER används för begäran om antal paket som skickas via länken.

| NX_IP_DRIVER medlem     | Innebörd                                                                                                     |
|-------------------------|-------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_TX_COUNT                                                                                        |
| nx_ip_driver_ptr        | Pekare till IP-instans                                                                                      |
| nx_ip_driver_return_ptr | Pekare till målet för att placera antalet överföringspaket                                               |
| nx_ip_driver_interface  | Pekare till gränssnittsinstansen                                                                           |
| nx_ip_driver_status     | Slutförandestatus. Om drivrutinen inte kan hämta överföringsantalet returneras felstatusen "inte noll". |


> [!NOTE]
> *Den här begäran används inte internt av NetX, så dess implementering är valfri.*

### <a name="get-allocation-errors"></a>Hämta allokeringsfel  

Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen lagrar länkens antal paketpoolsallokeringsfel i det angivna målet. Följande medlemmar NX_IP_DRIVER för begäran om antal länkallokeringsfel.

| **NX_IP_DRIVER medlem** | **Innebörd** |
| --- | ---|
| nx_ip_driver_command | NX_LINK_GET_ALLOC_ERRORS |
| nx_ip_driver_ptr | Pekare till IP-instans |

| NX_IP_DRIVER medlem     | Innebörd                                                                                                        |
|-------------------------|----------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_return_ptr | Pekare till målet för att placera antalet allokeringsfel                                                 |
| nx_ip_driver_interface  | Pekare till gränssnittsinstansen                                                                              |
| nx_ip_driver_status     | Slutförandestatus. Om drivrutinen inte kan få allokeringsfel returneras felstatusen "inte noll". |


*Den här begäran används inte internt av NetX, så dess implementering är valfri.*

### <a name="driver-deferred-processing"></a>Uppskjuten drivrutinsbearbetning  

Den här begäran görs från IP-hjälptråden som svar på att drivrutinen anropar rutinen _ ***nx_ip_driver_deferred_processing*** från en sändnings- eller mottagnings-ISR. Detta gör att drivrutinens ISR kan skjuta upp paket tar emot och överför bearbetning till IP-hjälptråden och därmed minska mängden som ska bearbetas i ISR. Det *nx_interface_additional_link_info-fältet* i NX_INTERFACE-strukturen som *nx_ip_driver_interface* pekar på kan användas av drivrutinen för att lagra information om den uppskjutna bearbetningshändelsen från IP-hjälptrådkontexten. Följande NX_IP_DRIVER-medlemmar används för den uppskjutna bearbetningshändelsen.

**NX_IP_DRIVER**

| medlem                 | Innebörd                           |
|------------------------|-----------------------------------|
| nx_ip_driver_command   | NX_LINK_DEFERRED_PROCESSING       |
| nx_ip_driver_ptr       | Pekare till IP-instans            |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen |


### <a name="user-commands"></a>Användarkommandon  

Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen bearbetar programspecifika användarkommandon. Följande NX_IP_DRIVER används för användarens kommandobegäran.

| NX_IP_DRIVER medlem     | Innebörd                                                                                                        |
|-------------------------|----------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_USER_COMMAND                                                                                           |
| nx_ip_driver_ptr        | Pekare till IP-instans                                                                                         |
| nx_ip_driver_return_ptr | Användardefinierad                                                                                                   |
| nx_ip_driver_interface  | Pekare till gränssnittsinstansen                                                                              |
| nx_ip_driver_status     | Slutförandestatus. Om drivrutinen inte kan köra användarkommandon returneras en felstatus som inte är noll. |


*Den här begäran används inte internt av NetX, så dess implementering är valfri.*

### <a name="unimplemented-commands"></a>Kommandon som inte har implementerats  

Kommandon som inte implementeras av nätverksdrivrutinen måste ha fältet returstatus inställt på NX_UNHANDLED_COMMAND.

## <a name="driver-output"></a>Drivrutinsutdata  

Alla tidigare nämnda paket överföringsbegäranden kräver en utdatafunktion implementerad i drivrutinen. Specifik överföringslogik är maskinvaruspecifik, men består vanligtvis av att söka efter maskinvarukapacitet för att skicka paketet omedelbart. Om möjligt läses paketnyttolasten (och ytterligare nyttolaster i paketkedjan) in i en eller flera av maskinvaru överföringsbuffertarna och en överföringsåtgärd initieras. Om paketet inte får plats i de tillgängliga överföringsbuffertarna ska paketet köas och skickas när överföringsbuffertarna blir tillgängliga.

Den rekommenderade överföringskön är en singly-länkad lista med både huvud- och slutpekare. Nya paket läggs till i slutet av kön, vilket behåller det äldsta paketet längst fram. Fältet *nx_packet_queue_next* används som paketets nästa länk i kön. Drivrutinen definierar huvud- och slutpekaren för överföringskön.

*Eftersom den här kön nås från tråden och avbryter delar av drivrutinen måste avbrottsskydd placeras runt kömanipuleringarna.*

De flesta implementeringar av fysisk maskinvara genererar ett avbrott när paketet har slutförts.
När drivrutinen får ett sådant avbrott frigör den vanligtvis de resurser som är associerade med det paket som just överförs. Om överföringslogiken läser data direkt från NX_PACKET-bufferten bör drivrutinen använda ***nx_packet_transmit_release-tjänsten*** för att frigöra paketet som är associerat med överföringens fullständiga avbrott tillbaka till den tillgängliga paketpoolen. Därefter undersöker drivrutinen överföringskön för ytterligare paket som väntar på att skickas. Eftersom många av de köade överföringspaketen som får plats i maskinvaru överföringsbuffertarna tas bort från kön och läses in i buffertarna. Detta följs av initiering av en annan skicka-åtgärd.

Så snart data i NX_PACKET har flyttats till fifo-givaren (eller om en drivrutin stöder nollkopieringsåtgärd har data i NX_PACKET överförts) måste drivrutinen flytta nx_packet_prepend_ptr till början av IP-huvudet innan den anropar ***nx_packet_transmit_release.*** Kom ihåg att *nx_packet_length* ändra fältet enligt detta. Om en IP-ram består av flera paket måste endast paketkedjans huvud släppas.

## <a name="driver-input"></a>Drivrutinsinmatning  

När ett mottaget paket tas emot, hämtar nätverksdrivrutinen paketet från den fysiska maskinvarans mottagningsbuffertar och skapar ett giltigt NetX-paket. Att skapa ett giltigt NetX-paket innebär att konfigurera ett lämpligt längdfält och länka samman flera paket om det inkommande paketets storlek är större än en enda paketnyttolast. När paketet har skapats prepend_ptr det fysiska lagerhuvudet och mottagningspaketet skickas till NetX.

NetX förutsätter att IP- och ARP-huvudena är justerade vid en ULONG-gräns. NetX-drivrutinen måste därför säkerställa den här justeringen. I Ethernet-miljöer görs detta genom att starta Ethernet-huvudet två byte från början av paketet. När nx_packet_prepend_ptr *över* Ethernet-huvudet är den underliggande IP- eller ARP-rubriken 4byte justerad.

Det finns flera inkommande paketfunktioner i NetX. Om det mottagna paketet är ett ARP-nx_arp_packet_deferred_receive anropas. _*_ Om det mottagna paketet är ett RARP-paket _*_nx_rarp_packet_deferred_receive_*_ anropas. Det finns flera alternativ för att hantera inkommande IP-paket. För den snabbaste hanteringen av IP-paket _*_anropas _ nx_ip_packet_receive_*_ anropas. Den här metoden har minst omkostnader, men kräver mer bearbetning i drivrutinens ISR (Receive Interrupt Service Handler). För minimal ISR-bearbetning __ *_nx_ip_packet_deferred_receive_** anropas.

När det nya mottagningspaketet har skapats på rätt sätt konfigureras den fysiska maskinvarans mottagningsbuffertar för att ta emot mer data. Detta kan kräva att NetX-paket allokeras och att nyttolastadressen placeras i maskinvarans mottagningsbuffert, eller att det helt enkelt innebär att ändra en inställning i maskinvarubufferten. För att minimera risken för överkörning är det viktigt att maskinvarans mottagningsbuffertar har tillgängliga buffertar så snart som möjligt efter att ett paket har tagits emot.

*De första mottagningsbuffertarna konfigureras under initieringen av drivrutinen.*

### <a name="deferred-receive-packet-handling"></a>Hantering av uppskjutna mottagningspaket  

Drivrutinen kan skjuta upp bearbetningen av mottagningspaket till NetX IP-hjälptråden. För vissa program kan detta vara nödvändigt för att minimera ISR-bearbetning samt ignorerade paket. Om du vill använda hantering av uppskjutna paket måste NetX-biblioteket först kompileras med ***NX_DRIVER_DEFERRED_PROCESSING** _ definierat. Detta lägger till logiken för uppskjutna paket i NetX IP-hjälptråden. När ett datapaket tas emot måste drivrutinen sedan anropa __nx_ip_packet_deferred_receive():*

```C
_nx_ip_packet_deferred_receive(ip_ptr, packet_ptr);
```

Funktionen för uppskjuten mottagning placerar det mottagningspaket som *representeras av packet_ptr* FIFO (länkad lista) och meddelar IP-hjälptråden. Efter körningen anropar IP-hjälpfunktionen för uppskjuten hantering för att bearbeta varje uppskjutet paket. Bearbetningen av uppskjuten hanterare omfattar vanligtvis borttagning av paketets fysiska lagerhuvud (vanligtvis Ethernet) och sändning till någon av dessa NetX-mottagningsfunktioner:  

***_nx_ip_packet_deferred_receive***  
***_nx_arp_packet_deferred_receive***  
***_nx_rarp_packet_deferred_receive*** 


## <a name="example-ram-ethernet-network-driver"></a>Exempel på RAM Ethernet-nätverksdrivrutin  

NetX-demonstrationssystemet levereras med en liten RAM-baserad nätverksdrivrutin som definieras ***i filen nx_ram_network_driver.c.***
Drivrutinen förutsätter att ALLA IP-instanser finns i samma nätverk och tilldelar helt enkelt VIRTUELLA maskinvaruadresser (MAC-adresser) till varje enhetsinstans när de skapas. Den här filen är ett bra exempel på den grundläggande strukturen för fysiska NetX-nätverksdrivrutiner. Användare kan utveckla sina egna nätverksdrivrutiner med hjälp av drivrutinsramverket som visas i det här exemplet.

Nätverksdrivrutinens inmatningsfunktion är ***_nx_ram_network_driver,** _ som skickas till anropet för att skapa IP-instansen. Inmatningsfunktioner för ytterligare nätverksgränssnitt kan _**_ skickas till nx_ip_interface_attach tjänsten. När IP-instansen börjar köras anropas drivrutinspostfunktionen för att initiera och aktivera enheten (se ärendet _ *NX_LINK_INITIALIZE** **och NX_LINK_ENABLE**). När **NX_LINK_ENABLE** kommando har utfärdats bör enheten vara redo att överföra och ta emot paket. 

IP-instansen överför nätverkspaket via något av följande kommandon:

| ***NX_LINK_PACKET_SEND***    | Ett IP-paket överförs,                             |
| ------------------------------- | -------------------------------------------------------------- |
| ***NX_LINK_ARP_SEND***       | En ARP-begäran eller ett ARP-svarspaket överförs,    |
| ***NX_LINK_ARP_RARP_SEND*** | En omvänd ARP-begäran eller svarspaket överförs, |

Vid bearbetning av dessa kommandon måste nätverksdrivrutinen lägga till rätt Ethernet-ramrubrik och sedan skicka den till den underliggande maskinvaran för överföring. Under överföringsprocessen har nätverksdrivrutinen exklusiv ägarskap för paketbuffertområdet. När data överförs (eller när data har kopierats till drivrutinens interna överföringsbuffert) ansvarar nätverksdrivrutinen för att frigöra paketbufferten genom att först flytta den förberedande pekaren förbi Ethernet-huvudet till IP-huvudet (och justera paketlängden därefter) och sedan genom att ***anropa nx_packet_transmit_release-tjänsten*** för att frigöra paketet. Om paketet inte frigörs efter dataöverföringen kommer paket att läcka.

Nätverksdrivrutinen ansvarar också för att hantera inkommande datapaket. I RAM-drivrutinsexempel bearbetas det mottagna paketet av funktionen ***_nx_ram_network_driver_receive***.

När enheten tar emot en Ethernet-ram ansvarar drivrutinen för att lagra data i

NX_PACKET struktur. Observera att NetX förutsätter att IP-huvudet börjar med 4 byte justerade adresser. Eftersom längden på Ethernet-huvudet är 14 byte måste drivrutinen lagra starten av Ethernet-huvudet vid 2 byte justerad adress för att garantera att IP-huvudet börjar vid 4 byte justerad adress.