---
title: Kapitel 5 – Azure RTOS NetX Duo-nätverksdrivrutiner
description: Det här kapitlet innehåller en beskrivning av nätverksdrivrutiner för Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d30e14ce1865e2fbce4a6e00cff787c859b32be
ms.sourcegitcommit: 20a136b06a25e31bbde718b4d12a03ddd8db9051
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/07/2021
ms.locfileid: "123552423"
---
# <a name="chapter-5---azure-rtos-netx-duo-network-drivers"></a>Kapitel 5 – Azure RTOS NetX Duo-nätverksdrivrutiner

Det här kapitlet innehåller en beskrivning av nätverksdrivrutiner för Azure RTOS NetX Duo. Den information som visas är utformad för att hjälpa utvecklare att skriva programspecifika nätverksdrivrutiner för NetX Duo.

## <a name="driver-introduction"></a>Introduktion till drivrutin

Den NX_IP strukturen innehåller allt för att hantera en enskild IP-instans. Detta inkluderar allmän TCP/IP-protokollinformation samt den programspecifika fysiska nätverksdrivrutinens startrutin. Drivrutinens postrutin definieras under tjänsten ***nx_ip_create** _ . Ytterligare enheter kan läggas till i IP-instansen via tjänsten _ *_nx_ip_interface_attach_** .

Kommunikationen mellan NetX Duo och programmets nätverksdrivrutin sker via NX_IP_DRIVER **för** programbegäran. Den här strukturen definieras oftast lokalt på anroparstacken och släpps därför när drivrutinen och anropar funktionen returneras. Strukturen definieras på följande sätt.

```c
typedef struct NX_IP_DRIVER_STRUCT
{
      UINT           nx_ip_driver_command;
      UINT           nx_ip_driver_status;
      ULONG          nx_ip_driver_physical_address_msw;
      ULONG          nx_ip_driver_physical_address_lsw;
      NX_PACKET      *nx_ip_driver_packet;
      ULONG          *nx_ip_driver_return_ptr;
      NX_IP          *nx_ip_driver_ptr;
      NX_INTERFACE   *nx_ip_driver_interface;01
} NX_IP_DRIVER;
```
## <a name="driver-entry"></a>Drivrutinspost 

NetX Duo anropar funktionen för inmatning av nätverksdrivrutiner för initiering av drivrutiner och för att skicka paket och för olika kontroll- och statusåtgärder, inklusive initiering och aktivering av nätverksenheten. NetX Duo utfärdar kommandon till nätverksdrivrutinen genom att ange fältet ***nx_ip_driver_command** _ i *begärandestrukturen* _ NX_IP_DRIVER * . Drivrutinspostfunktionen har följande format:

```c
VOID my_driver_entry(NX_IP_DRIVER *request);
```
## <a name="driver-requests"></a>Drivrutinsbegäranden

NetX Duo skapar drivrutinsbegäran med ett visst kommando och anropar drivrutinspostfunktionen för att köra kommandot. Eftersom varje nätverksdrivrutin har en enda postfunktion gör NetX Duo alla begäranden via datastrukturen för drivrutinsbegäranden. *nx_ip_driver_command_ medlem i datastrukturen för drivrutinsbegäran (_*NX_IP_DRIVER**) definierar begäran. Statusinformation rapporteras tillbaka till anroparen i medlemmen **_nx_ip_driver_status_*_. Om det här fältet är _*NX_SUCCESS** slutfördes drivrutinsbegäran.

NetX Duo serialiserar all åtkomst till drivrutinen. Drivrutinen behöver därför inte hantera flera trådar asynkront anropar entry-funktionen. Observera att enhetsdrivrutinsfunktionen körs med IP-adressen mutex låst. Den interna funktionen för enhetsdrivrutiner får därför inte blockera sig själv.

Vanligtvis hanterar enhetsdrivrutinen även avbrott. Därför måste alla drivrutinsfunktioner vara avbrottssäkra.

### <a name="driver-initialization"></a>Drivrutinsinitiering   
Även om den faktiska initieringsbearbetningen av drivrutiner är programspecifik består den vanligtvis av datastruktur och initiering av fysisk maskinvara. Informationen som krävs från NetX Duo för drivrutinsinitiering är IP Maximum Transmission Unit (MTU), vilket är antalet byte som är tillgängliga för IP-lagrets nyttolast, inklusive IPv4- eller IPv6-huvud) och om det fysiska gränssnittet behöver mappning från logiskt till fysiskt. Drivrutinen konfigurerar gränssnittets MTU-värde genom att anropa ***nx_ip_interface_mtu_set***.

Enhetsdrivrutinen måste anropa * nx_ip_interface_address_mapping_configure _ **för** att meddela NetX Duo om gränssnittsadressmappning krävs eller inte. Om adressmappning krävs ansvarar drivrutinen för att konfigurera gränssnittet med en giltig MAC-adress och ange MAC-adressen till NetX via _*_nx_ip_interface_physical_address_set_**.

När nätverksdrivrutinen tar emot NX_LINK INITIALIZE-begäran från NetX Duo tar den emot en pekare till IP-kontrollblocket som en del av NX_IP_DRIVER som visas ovan.

När programmet ***anropar nx_ip_create*** skickar IP-hjälptråden en drivrutinsbegäran med kommandot inställt på NX_LINK_INITIALIZE till drivrutinen för att initiera dess fysiska nätverksgränssnitt. Följande NX_IP_DRIVER-medlemmar används för att initiera begäran.

| NX_IP_DRIVER &nbsp; medlem | Innebörd    |
| ------------------------- | ----------------------------- |
| nx_ip_driver_command   | NX_LINK_INITIALIZE    |
| nx_ip_driver_ptr       | Pekare till IP-instansen. Det här värdet ska sparas av drivrutinen så att drivrutinsfunktionen kan hitta IP-instansen som den ska användas på.    |
| nx_ip_driver_interface | Pekare till nätverksgränssnittsstrukturen i IP-instansen. Den här informationen ska sparas av drivrutinen. När paket tas emot ska drivrutinen använda gränssnittsstrukturinformationen när paketet skickas upp i stacken. Gränssnittsindexet (enhetsindex) kan hämtas genom att läsa medlemsindexet nx_interface_index den här datastrukturen. |
| nx_ip_driver_status    | Slutförandestatus. Om drivrutinen inte kan initiera det angivna gränssnittet till IP-instansen returneras statusen nollfel. |


> [!NOTE]  
> *Drivrutinen anropas faktiskt från IP-hjälptråden som skapades för IP-instansen. Därför bör drivrutinsrutinen* undvika att utföra blockerande åtgärder, eller så kan IP-hjälptråden stanna av, vilket orsakar obegränsade fördröjningar för program som förlitar sig på IP-tråden .

### <a name="enable-link"></a>Aktivera länk   
Därefter aktiverar IP-hjälptråden det fysiska nätverket genom att ange drivrutinskommandot till NX_LINK_ENABLE i drivrutinsbegäran och skicka begäran till nätverksdrivrutinen. Detta sker strax efter att IP-hjälptråden har slutfört initieringsbegäran. Att aktivera länken kan vara så enkelt som att ange *nx_interface_link_up* i gränssnittsinstansen. Men det kan också handla om manipulering av den fysiska maskinvaran. Följande NX_IP_DRIVER-medlemmar används för att aktivera länkbegäran.

| NX_IP_DRIVER &nbsp; medlem       | Innebörd                      |
| ------------------------- | ---------------------------- |
| nx_ip_driver_command   | NX_LINK_ENABLE   |
| nx_ip_driver_ptr       | Pekare till IP-instans  |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen |
| nx_ip_driver_status    | Slutförandestatus. Om drivrutinen inte kan aktivera det angivna gränssnittet returneras felstatusen "inte noll". |

### <a name="disable-link"></a>Inaktivera länk   
Den här begäran görs av NetX Duo under borttagningen av en IP-instans av tjänsten ***nx_ip_delete** _ . Eller så kan ett program utfärda det här kommandot för att tillfälligt inaktivera länken för att spara ström. Den här tjänsten inaktiverar det fysiska nätverksgränssnittet på IP-instansen. Bearbetningen för att inaktivera länken kan vara så enkel som att rensa _nx_interface_link_up*-flaggan i gränssnittsinstansen. Men det kan också handla om manipulering av den fysiska maskinvaran. Vanligtvis är det en omvänd åtgärd av åtgärden ***Aktivera**_ länk. När länken har inaktiverats aktiverar programbegäran _ *_Aktivera_* länk * gränssnittet.

Följande NX_IP_DRIVER används för att inaktivera länkbegäran.

| NX_IP_DRIVER &nbsp; medlem     | Innebörd                      |
| ------------------------- | ---------------------------- |
| nx_ip_driver_command   | NX_LINK_DISABLE    |
| nx_ip_driver_ptr       | Pekare till IP-instans   |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen   |
| nx_ip_driver_status    | Slutförandestatus. Om drivrutinen inte kan inaktivera det angivna gränssnittet i IP-instansen returneras felstatusen "inte noll". |

### <a name="uninitialize-link"></a>Uninitialize Link   
Den här begäran görs av NetX Duo under borttagningen av en IP-instans av tjänsten ***nx_ip_delete** _ . Den här begäran avinitierar gränssnittet och släpper alla resurser som skapats under initieringsfasen. Vanligtvis är det en omvänd åtgärd för åtgärden _ *_Initiera länk_** . När gränssnittet har avinitaliserats kan enheten inte användas förrän gränssnittet har initierats igen.

Följande NX_IP_DRIVER används för att inaktivera länkbegäran.

| NX_IP_DRIVER &nbsp; medlem    | Innebörd                  |
|------------------------|--------------------------|
| nx_ip_driver_command   | NX_LINK_UNINITIALZE      |
| nx_ip_driver_ptr       | Pekare till IP-instans   |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen |
| nx_ip_driver_status    | Slutförandestatus. Om drivrutinen inte kan avinfinna det angivna gränssnittet till IP-instansen returneras felstatusen "inte noll". |

### <a name="packet-send"></a>Skicka paket   
Denna begäran görs under intern IPv4- eller IPv6-sändningsbearbetning, som alla NetX Duo-protokoll använder för att överföra paket (förutom ARP, RARP). När du tar emot kommandot packet send *nx_packet_prepend_ptr* pekar på början av det paket som ska skickas, vilket är början av IPv4- eller IPv6-huvudet. *nx_packet_length* anger den totala storleken (i byte) för de data som överförs. Om *nx_packet_next* är giltigt lagras det utgående IP-datagrammet i flera paket. Drivrutinen måste följa det kedjade paketet och överföra hela ramen. Observera att ett giltigt dataområde i varje länkat paket lagras *mellan nx_packet_prepend_ptr* *och nx_packet_append_ptr*.

Drivrutinen ansvarar för att skapa ett fysiskt huvud. Om fysisk adress till IP-adressmappning krävs (till exempel Ethernet) har IP-lagret redan löst MAC-adressen. MAC-måladressen skickas från IP-instansen som lagras *i nx_ip_driver_physical_address_msw och nx_ip_driver_physical_address_lsw*.

När du har lagt till det fysiska huvudet anropar paketets sändningsbearbetning sedan drivrutinens utdatafunktion för att överföra paketet.

Följande NX_IP_DRIVER medlemmar används för begäran om paketsändning.

| NX_IP_DRIVER &nbsp; medlem              | Innebörd                               |
| -----------------------------------| --------------------------------------|
| nx_ip_driver_command            | NX_LINK_PACKET_SEND                |
| nx_ip_driver_ptr                | Pekare till IP-instans                |
| nx_ip_driver_packet             | Pekare till det paket som ska skickas         |
| nx_ip_driver_interface          | Pekare till gränssnittsinstansen.    |
| nx_ip_driver_physical_address_msw | Mest betydande 32-bitars fysisk adress (endast om fysisk mappning behövs) |
| nx_ip_driver_physical_address_lsw | Minst betydande 32-bitars fysisk adress (endast om fysisk mappning behövs) |
| nx_ip_driver_status             | Slutförandestatus. Om drivrutinen inte kan skicka paketet returneras felstatusen "inte noll". |

### <a name="packet-broadcastipv4-packets-only"></a>Paketsändning (endast IPv4-paket)  
Den här begäran är nästan identisk med begäran om att skicka paket. Den enda skillnaden är att fälten för den fysiska måladressen är inställda på ETHERNET-broadcast MAC-adressen. Följande NX_IP_DRIVER-medlemmar används för paketets sändningsbegäran.

| NX_IP_DRIVER &nbsp; medlem                | Innebörd                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_PACKET_BROADCAST                                                                                 |
| nx_ip_driver_ptr                   | Pekare till IP-instans                                                                                   |
| nx_ip_driver_packet                | Pekare till det paket som ska skickas                                                                            |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (broadcast)                                                                                   |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (broadcast)                                                                                   |
| nx_ip_driver_interface             | Pekare till gränssnittsinstansen.                                                                       |
| nx_ip_driver_status                | Slutförandestatus. Om drivrutinen inte kan skicka paketet returneras felstatusen "inte noll". |

### <a name="arp-send"></a>Skicka ARP  
Den här begäran liknar också begäran om ATT skicka IP-paket. Den enda skillnaden är att Ethernet-huvudet anger ett ARP-paket i stället för ett IP-paket, och måladressfälten är inställda på MAC-sändningsadress. Följande medlemmar NX_IP_DRIVER för att skicka ARP-begäran.

| NX_IP_DRIVER &nbsp; medlem                | Innebörd                                                                                                      |
|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_ARP_SEND                                                                                             |
| nx_ip_driver_ptr                   | Pekare till IP-instans                                                                                       |
| nx_ip_driver_packet                | Pekare till det paket som ska skickas                                                                                |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (broadcast)                                                                                       |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (broadcast)                                                                                       |
| nx_ip_driver_interface             | Pekare till gränssnittsinstansen.                                                                           |
| nx_ip_driver_status                | Slutförandestatus. Om drivrutinen inte kan skicka ARP-paketet returneras felstatusen "inte noll". |

> [!IMPORTANT]  
> *Om fysisk mappning inte behövs krävs inte implementering av den här begäran.*

Även om ARP har ersatts med Neighbor Discovery Protocol och Router Discovery Protocol i IPv6, måste Ethernet-nätverksdrivrutiner fortfarande vara kompatibla med *IPv4-peers och routrar. Drivrutiner måste därför fortfarande hantera ARP-paket.*

### <a name="arp-response-send"></a>Skicka ARP-svar  
Den här begäran är nästan identisk med begäran om att skicka ARP-paket. Den enda skillnaden är att fälten för den fysiska måladressen skickas från IP-instansen. Följande medlemmar NX_IP_DRIVER för begäran om ARP-svarssvar.

| NX_IP_DRIVER &nbsp; medlem                  | Innebörd                                  |
| -------------------------------------- | -----------------------------------------|
| nx_ip_driver_command                | NX_LINK_ARP_RESPONSE_SEND            |
| nx_ip_driver_ptr                    | Pekare till IP-instans   |
| nx_ip_driver_packet                 | Pekare till det paket som ska skickas          |
| nx_ip_driver_physical_address_msw | Viktigaste 32-bitars fysiska adress |
| nx_ip_driver_physical_address_lsw | Minst betydande 32-bitars fysisk adress |
| nx_ip_driver_interface              | Pekare till gränssnittsinstansen |
| nx_ip_driver_status                 | Slutförandestatus. Om drivrutinen inte kan skicka ARP-paketet returneras felstatusen "inte noll". |

> [!IMPORTANT]  
> *Om fysisk mappning inte behövs krävs inte implementering av den här begäran.*

### <a name="rarp-send"></a>SKICKA RARP   
Den här begäran är nästan identisk med begäran om att skicka ARP-paket. De enda skillnaderna är typen av pakethuvud och fälten för fysiska adresser krävs inte eftersom det fysiska målet alltid är en broadcast-adress.

Följande NX_IP_DRIVER används för RARP-begäran om att skicka.

| NX_IP_DRIVER &nbsp; medlem                | Innebörd                                                                                                       |
|------------------------------------|---------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_RARP_SEND                                                                                             |
| nx_ip_driver_ptr                   | Pekare till IP-instans                                                                                        |
| nx_ip_driver_packet                | Pekare till det paket som ska skickas                                                                                 |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (broadcast)                                                                                        |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (broadcast)                                                                                        |
| nx_ip_driver_interface             | Pekare till gränssnittsinstansen.                                                                            |
| nx_ip_driver_status                | Slutförandestatus. Om drivrutinen inte kan skicka RARP-paketet returneras felstatusen "inte noll". |

> [!IMPORTANT]  
> *Program som kräver RARP-tjänsten måste implementera det här kommandot*.

### <a name="multicast-group-join"></a>Multicast-gruppkoppling   
Den här begäran görs med tjänsten ***nx_igmp_multicast_interface join** _ och _*_nx_ipv4_multicast_interface_join_*_ i IPv4, _ *_nxd_ipv6_multicast_interface_join_** i IPv6 och olika åtgärder som krävs av IPv6. Nätverksdrivrutinen tar den angivna multicast-gruppadressen och uppsättningar upp det fysiska mediet för att acceptera inkommande paket från den multicast-gruppadressen. Observera att för drivrutiner som inte stöder multicast-filter kan logiken för att ta emot drivrutinen behöva vara i ett icke-filtrerat läge. I det här fallet kan drivrutinen behöva filtrera inkommande bildrutor baserat på MAC-måladressen, vilket minskar mängden trafik som skickas till IP-instansen. Följande NX_IP_DRIVER används för multicast-gruppkopplingsbegäran.

| NX_IP_DRIVER &nbsp; medlem                  | Innebörd                                 |
| -------------------------------------- | --------------------------------------- |
| nx_ip_driver_command                | NX_LINK_MULTICAST_JOIN               |
| nx_ip_driver_ptr                    | Pekare till IP-instans  |
| nx_ip_driver_physical_address_msw | Viktigaste 32-bitars fysiska multicast-adress |
| nx_ip_driver_physical_address_lsw | Minst viktiga 32-bitars fysisk multicast-adress |
| nx_ip_driver_interface              | Pekare till gränssnittsinstansen |
| nx_ip_driver_status                 | Slutförandestatus. Om drivrutinen inte kan ansluta till multicast-gruppen returneras en felstatus som inte är noll. |

> [!NOTE]  
> *IPv6-program kräver att multicast implementeras i drivrutinen för ICMPv6-baserade protokoll, till exempel adresskonfiguration. För IPv4-program behövs dock inte implementering av den här begäran om multicast-funktioner inte krävs.*

> [!IMPORTANT]  
> *Om IPv6 inte är aktiverat och multicast-funktioner* inte krävs av IPv4 krävs inte implementering av den här begäran.

### <a name="multicast-group-leave"></a>Lämna multicast-grupp  
Den här begäran anropas uttryckligen genom att anropa tjänsten ***nx_igmp_multicast_interface_leave** _ eller _*_nx_ipv4_multicast_interface_leave_*_ i IPv4, _ *_nxd_ipv6_multicast_interface_leave_** i IPv6 eller av olika interna NetX Duo-åtgärder som krävs för IPv6. Drivrutinen tar bort den angivna Ethernet-multicast-adressen från multicast-listan. När en värd har lämnat en multicast-grupp tas paket i nätverket med den här Ethernet-multicast-adressen inte längre emot av den här IP-instansen. Följande NX_IP_DRIVER används för multicast-gruppledarbegäran.

| NX_IP_DRIVER &nbsp; medlem              | Innebörd                              |
| -----------------------------------| -------------------------------------|
| nx_ip_driver_command            | NX_LINK_MULTICAST_LEAVE           |
| nx_ip_driver_ptr                | Pekare till IP-instans   |
| nx_ip_driver_physical_address_msw | Flest 32 bitar fysisk multicast-adress |
| nx_ip_driver_physical_address_lsw | Minst 32 bitar fysisk multicast-adress |
| nx_ip_driver_interface              | Pekare till gränssnittsinstansen |
| nx_ip_driver_status                 | Slutförandestatus. Om drivrutinen inte kan lämna multicast-gruppen returneras felstatusen "inte noll". |

> [!IMPORTANT]  
> *Om multicast-funktioner inte krävs av antingen IPv4 eller IPv6 krävs* inte implementering av den här begäran.

### <a name="attach-interface"></a>Anslut gränssnitt  
Den här begäran anropas från NetX Duo till enhetsdrivrutinen, så att drivrutinen kan associera drivrutinsinstansen med motsvarande IP-instans och instansen av det fysiska gränssnittet inom IP-adressen. Följande NX_IP_DRIVER-medlemmar används för begäran om att koppla gränssnitt.

| NX_IP_DRIVER &nbsp; medlem    | Innebörd                  |
|------------------------|--------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_ATTACH |
| nx_ip_driver_ptr       | Pekare till IP-instans   |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen.|
| nx_ip_driver_status    | Slutförandestatus. Om drivrutinen inte kan koppla från det angivna gränssnittet till IP-instansen returneras felstatusen "inte noll". |

### <a name="detach-interface"></a>Koppla från gränssnitt    
Den här begäran anropas av NetX Duo till enhetsdrivrutinen, så att drivrutinen kan ta bort associationen mellan drivrutinsinstansen och motsvarande IP-instans och instansen av det fysiska gränssnittet inom IP-adressen. Följande NX_IP_DRIVER-medlemmar används för begäran om att koppla gränssnitt.

| NX_IP_DRIVER &nbsp; medlem    | Innebörd                                                                                                                                    |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_DETACH                                                                                                                   |
| nx_ip_driver_ptr       | Pekare till IP-instans                                                                                                                     |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen.                                                                                                         |
| nx_ip_driver_status    | Slutförandestatus. Om drivrutinen inte kan koppla det angivna gränssnittet till IP-instansen returneras felstatusen "inte noll". |

### <a name="get-link-status"></a>Hämta länkstatus    
Programmet kan fråga nätverksgränssnittslänkstatusen med hjälp  av NetX Duo nx_ip_interface_status_check tjänsten för alla gränssnitt på värden. Se kapitel 4, "Beskrivning av NetX Duo Services" på sidan 149, för mer information om dessa tjänster.

Länkstatusen finns i nx_interface_link_up *i* den NX_INTERFACE struktur som pekar *nx_ip_driver_interface* pekaren. Följande NX_IP_DRIVER används för begäran om länkstatus.

| NX_IP_DRIVER &nbsp; medlem       | Innebörd                  |
| --------------------------- | -------------------------|
| nx_ip_driver_command     | NX_LINK_GET_STATUS    |
| nx_ip_driver_ptr         | Pekare till IP-instans   |
| nx_ip_driver_return_ptr | Pekare till målet för att placera statusen. |
| nx_ip_driver_interface   | Pekare till gränssnittsinstansen   |
| nx_ip_driver_status      | Slutförandestatus. Om drivrutinen inte kan hämta specifik status returneras felstatusen "inte noll". |

> [!NOTE]  
> ***nx_ip_status_check** _ är fortfarande tillgängligt för att kontrollera status för det primära gränssnittet. Programutvecklare uppmanas dock att använda den gränssnittsspecifika tjänsten: _ *_nx_ip_interface_status_check._**

### <a name="get-link-speed"></a>Hämta länkhastighet  
Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen lagrar länkens linjehastighet i det angivna målet. Följande NX_IP_DRIVER används för begäran om länklinjehastighet.

| NX_IP_DRIVER &nbsp; medlem   | Innebörd                   |
| ------------------------| ------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_SPEED          |
| nx_ip_driver_ptr         | Pekare till IP-instans                                                                                         |
| nx_ip_driver_return_ptr | Pekare till målet för att placera linjehastigheten                                                             |
| nx_ip_driver_interface   | Pekare till gränssnittsinstansen                                                                              |
| nx_ip_driver_status      | Slutförandestatus. Om drivrutinen inte kan hämta information om hastigheten returneras felstatusen "inte noll". |

> [!IMPORTANT]  
> *Den här begäran används inte internt av NetX Duo, så dess implementering är valfri*.

### <a name="get-duplex-type"></a>Hämta Duplex-typ   
Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen lagrar länkens duplex-typ i det angivna målet. Följande NX_IP_DRIVER-medlemmar används för duplex-typbegäran.

| NX_IP_DRIVER &nbsp; medlem   | Innebörd                                                                                                    |
| --------------------------- | -------------------------------------------------------------------------------------------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_DUPLEX_TYPE                                                                                    |
| nx_ip_driver_ptr         | Pekare till IP-instans                                                                                         |
| nx_ip_driver_return_ptr | Pekare till målet för att placera duplex-typen                                                            |
| nx_ip_driver_interface   | Pekare till gränssnittsinstansen                                                                              |
| nx_ip_driver_status      | Slutförandestatus. Om drivrutinen inte kan hämta duplex-information returneras ett fel som inte är noll. |

> [!IMPORTANT]  
> *Den här begäran används inte internt av NetX Duo, så dess implementering är valfri*.

### <a name="get-error-count"></a>Hämta antal fel   
Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen lagrar länkens felantal i det angivna målet. För att stödja den här funktionen måste drivrutinen spåra åtgärdsfel. Följande NX_IP_DRIVER används för begäran om antal länkfel.

| NX_IP_DRIVER &nbsp; medlem   | Innebörd                   |
| --------------------------- | -------------------------------|
| nx_ip_driver_command     | NX_LINK_GET_ERROR_COUNT   |
| nx_ip_driver_ptr         | Pekare till IP-instans   |
| nx_ip_driver_return_ptr | Pekare till målet för att placera felantalet |
| nx_ip_driver_interface   | Pekare till gränssnittsinstansen|
| nx_ip_driver_status      | Slutförandestatus. Om drivrutinen inte kan hämta antal fel returnerar den felstatus som inte är noll. |

> [!IMPORTANT]
> *Den här begäran används inte internt av NetX Duo, så dess implementering är valfri*.

### <a name="get-receive-packet-count"></a>Hämta antal inkommande paket    
Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen lagrar länkens antal inkommande paket i det angivna målet. För att stödja den här funktionen måste drivrutinen hålla reda på antalet mottagna paket. Följande medlemmar NX_IP_DRIVER för begäran om att ta emot paket via länken.

| NX_IP_DRIVER &nbsp; medlem       | Innebörd                        |
| --------------------------- | -------------------------------|
| nx_ip_driver_command     | NX_LINK_GET_RX_COUNT      |
| nx_ip_driver_ptr         | Pekare till IP-instans  |
| nx_ip_driver_return_ptr | Pekare till målet för att placera antalet inkommande paket   |
| nx_ip_driver_interface   | Pekare till det fysiska nätverksgränssnittet  |
| nx_ip_driver_status      | Slutförandestatus. Om drivrutinen inte kan ta emot antal returneras felstatusen "inte noll". |

> [!IMPORTANT]  
> *Den här begäran används inte internt av NetX Duo, så dess implementering är valfri*.

### <a name="get-transmit-packet-count"></a>Hämta antal överföringspaket   
Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen lagrar länkens antal överföringspaket i det angivna målet. För att stödja den här funktionen måste drivrutinen hålla reda på varje paket som överförs i varje gränssnitt. Följande NX_IP_DRIVER används för begäran om antal länk överföringspaket.

| NX_IP_DRIVER &nbsp; medlem   | Innebörd                   |
| ----------------------- | ------------------------- |
| nx_ip_driver_command | NX_LINK_GET_TX_COUNT  |
| nx_ip_driver_ptr     | Pekare till IP-instans    |
| nx_ip_driver_return_ptr | Pekare till målet för att placera antalet överföringspaket  |
| nx_ip_driver_interface   | Pekare till gränssnittsinstansen   |
| nx_ip_driver_status      | Slutförandestatus. Om drivrutinen inte kan hämta överföringsantalet returneras felstatusen ej noll. |

> [!IMPORTANT]  
> *Den här begäran används inte internt av NetX Duo, så dess implementering är valfri.*

### <a name="get-allocation-errors"></a>Hämta allokeringsfel   
Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen lagrar länkens antal paketpoolsallokeringsfel i det angivna målet. Följande medlemmar NX_IP_DRIVER för begäran om antal länkallokeringsfel.

| NX_IP_DRIVER &nbsp; medlem       | Innebörd                       |
| --------------------------- | ----------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_ALLOC_ERRORS  |
| nx_ip_driver_ptr         | Pekare till IP-instans     |
| nx_ip_driver_return_ptr | Pekare till målet för att placera allokeringsfelantalet  |
| nx_ip_driver_interface   | Pekare till gränssnittsinstansen  |
| nx_ip_driver_status      | Slutförandestatus. Om drivrutinen inte kan få allokeringsfel returneras en felstatus som inte är noll. |

> [!IMPORTANT]  
> *Den här begäran används inte internt av NetX Duo, så dess implementering är valfri.*

### <a name="driver-deferred-processing"></a>Bearbetning av uppskjuten drivrutin    
Den här begäran görs från IP-hjälptråden som svar på att drivrutinen _* **anropar nx_ip_driver_deferred_processing**_ från en överförings- eller mottagnings-ISR. Detta gör att drivrutinens ISR kan skjuta upp inkommande och överförande bearbetning av paket till IP-hjälptråden och därmed minska mängden som ska bearbetas i ISR. Fältet _nx_interface_additional_link_info* i NX_INTERFACE-strukturen som nx_ip_driver_interface pekar  på kan användas av drivrutinen för att lagra information om den uppskjutna bearbetningshändelsen från IP-hjälptrådkontexten. Följande NX_IP_DRIVER används för den uppskjutna bearbetningshändelsen.

| NX_IP_DRIVER &nbsp; medlem     | Innebörd                           |
| ------------------------- | --------------------------------- |
| nx_ip_driver_command   | NX_LINK_DEFERRED_PROCESSING    |
| nx_ip_driver_ptr       | Pekare till IP-instans            |
| nx_ip_driver_interface | Pekare till gränssnittsinstansen |

### <a name="set-physical-address"></a>Ange fysisk adress  
Den här begäran görs inifrån tjänsten ***nx_ip_interface_physical_address_set** _ . Med den här tjänsten kan ett program ändra gränssnittets fysiska adress vid körning. När du tar emot det här kommandot måste drivrutinen konfigurera om maskinvaruadressen för nätverksgränssnittet till den angivna fysiska adressen. Eftersom IP-instansen redan har den nya adressen behöver du inte anropa tjänsten _ *_nx_ip_interface_address_set_** från det här kommandot.

Följande NX_IP_DRIVER används för användarkommandobegäran.

| NX_IP_DRIVER &nbsp; medlem      | Innebörd                      |
| -------------------------- | ---------------------------- |
| nx_ip_driver_command    | NX_LINK_SET_PHYSICAL_ADDRESS  |
| nx_ip_driver_ptr        | Pekare till IP-instans  |
| nx_ip_driver_interface  | Pekare till gränssnittsinstansen   |
| nx_ip_driver_physical_ad dress_msw | Mest betydande 32-bitars av den nya fysiska adressen  |
| nx_ip_driver_physical_ad dress_lsw | Minst viktiga 32-bitars av den nya fysiska adressen  |
| nx_ip_driver_status                  | Slutförandestatus. Om drivrutinen inte kan konfigurera om den fysiska adressen returneras en felstatus som inte är noll. |

### <a name="user-commands"></a>Användarkommandon    
Den här begäran görs  inifrån nx_ip_driver_direct_command tjänsten. Drivrutinen bearbetar programspecifika användarkommandon. Följande NX_IP_DRIVER används för användarkommandobegäran.

| NX_IP_DRIVER &nbsp; medlem       | Innebörd                       |
| --------------------------- | ----------------------------- |
| nx_ip_driver_command     | NX_LINK_USER_COMMAND       |
| nx_ip_driver_ptr         | Pekare till IP-instans        |
| nx_ip_driver_return_ptr | Användardefinierad       |
| nx_ip_driver_interface   | Pekare till gränssnittsinstansen    |
| nx_ip_driver_status      | Slutförandestatus. Om drivrutinen inte kan köra användarkommandon returneras en felstatus som inte är noll. |

> [!IMPORTANT] 
> *Den här begäran används inte internt av NetX Duo, så dess implementering är valfri.*

### <a name="unimplemented-commands"></a>Kommandon som inte har implementerats  
Kommandon som inte implementeras av nätverksdrivrutinen måste ha fältet returstatus inställt på NX_UNHANDLED_COMMAND.

## <a name="driver-capability"></a>Drivrutinskapacitet

Vissa nätverksgränssnitt har funktioner för avlastning av kontrollsumma. Enhetsdrivrutiner kan dra nytta av maskinvaruaccelerationerna för att frigöra CPU-tid från att köra olika beräkningar av kontrollsumma.

Beroende på vilken nivå av stöd för kontrollsumma för maskinvara som maskinvaran stöder måste enhetsdrivrutinen informera IP-instansen om vilken maskinvarufunktion som är aktiverad. På så sätt är IP-instansen medveten om maskinvarufunktionen och avlastar så mycket beräkning till maskinvaran som möjligt. Drivrutinen bör använda ***API-nx_ip_interface_capability_set*** för att ange alla funktioner som det fysiska gränssnittet kan hantera.

Följande funktioner kan användas:

- NX_INTERFACE_CAPABILITY_IPV4_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IPV4_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_TCP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_TCP_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_UDP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_UDP_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV4_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV4_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV6_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV6_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IGMP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IGMP_RX_CHECKSUM

För en beräkning av kontrollsumma som kan utföras i maskinvaran måste drivrutinen konfigurera maskinvaran eller buffertbeskrivningarna korrekt så att kontrollsumman för ett utgående paket kan genereras och infogas i huvudet av maskinvaran. När du tar emot ett paket ska logiken för kontrollsumma för maskinvara kunna verifiera kontrollsummavärdet. Om värdet för kontrollsumma är felaktigt bör den mottagna ramen tas bort.

Även om det går att utföra beräkning av kontrollsumma i maskinvaran behåller IP-instansen fortfarande kontrollsumman. I vissa scenarier, till exempel ett UDP-datagram som går igenom IPsec-skydd, måste UDP-kontrollsumman beräknas i programvara innan UDP-ramen går nedåt i stacken. De flesta funktioner för kontrollsumma för maskinvara stöder inte beräkning av kontrollsumma för ett datasegment som skyddas av IPsec. För en UDP- eller ICMP-ram som måste vara fragmenterad måste UDP- eller ICMP-kontrollsumman beräknas i programvara. De flesta logiken för kontrollsumma för maskinvara hanterar inte de fall där data delas upp i flera bildrutor.

## <a name="driver-output"></a>Drivrutinsutdata  

Alla tidigare nämnda paket överföringsbegäranden kräver en utdatafunktion som implementerats i drivrutinen. Specifik överföringslogik är maskinvaruspecifik, men består vanligtvis av att söka efter maskinvarukapacitet för att skicka paketet omedelbart. Om möjligt läses paketnyttolasten (och ytterligare nyttolaster i paketkedjan) in i en eller flera av maskinvaru överföringsbuffertarna och en överföringsåtgärd initieras. Om paketet inte får plats i de tillgängliga överföringsbuffertarna ska paketet köas och överföras när överföringsbuffertarna blir tillgängliga.

Den rekommenderade överföringskön är en helt länkad lista med både huvud- och tail-pekare. Nya paket läggs till i slutet av kön, vilket behåller det äldsta paketet längst fram. Fältet *nx_packet_queue_next* används som paketets nästa länk i kön. Drivrutinen definierar huvud- och slutpekaren för överföringskön.

> [!CAUTION]  
> Eftersom den här kön nås från tråden och avbryter delar av drivrutinen måste avbrottsskydd placeras *runt kömanipuleringen.*

De flesta implementeringar av fysisk maskinvara genererar ett avbrott när paketet har slutförts. När drivrutinen får ett sådant avbrott frigör den vanligtvis de resurser som är associerade med paketet som just överförs. Om överföringslogiken läser data direkt från NX_PACKET-bufferten bör drivrutinen använda ***nx_packet_transmit_release-tjänsten*** för att frigöra paketet som är associerat med överföringens fullständiga avbrott tillbaka till den tillgängliga paketpoolen. Därefter undersöker drivrutinen överföringskön för ytterligare paket som väntar på att skickas. Eftersom många av de köade överföringspaketen som passar in i maskinvaru överföringsbuffertarna avköas och läses in i buffertarna. Detta följs av initiering av en annan skicka-åtgärd.

Så snart data i NX_PACKET har flyttats till fifo-sändaren (eller om en drivrutin stöder nollkopieringsåtgärd har data i NX_PACKET överförts) måste drivrutinen flytta *nx_packet_prepend_ptr* till början av IP-huvudet innan den anropar ***nx_packet_transmit_release.** _ Kom ihåg att _nx_packet_length*-fältet. Om en IP-ram består av flera paket behöver bara paketkedjans huvud släppas.

## <a name="driver-input"></a>Drivrutinsinmatning

Vid mottagning av ett mottaget paketavbrott hämtar nätverksdrivrutinen paketet från den fysiska maskinvarans mottagningsbuffertar och skapar ett giltigt NetX Duo-paket. Att skapa ett giltigt NetX Duo-paket innebär att konfigurera lämpligt längdfält och länka samman flera paket om det inkommande paketets storlek är större än en enda paketnyttolast. När paketet har skapats *prepend_ptr* det fysiska lagerhuvudet och det inkommande paketet skickas till NetX Duo.

NetX Duo förutsätter att IP-adresserna (IPv4 och IPv6) och ARP-huvudena är justerade mot **en ULONG-gräns.** NetX Duo-drivrutinen måste därför säkerställa den här justeringen. I Ethernet-miljöer görs detta genom att starta Ethernet-huvudet två byte från början av paketet. När *nx_packet_prepend_ptr* flyttas utanför Ethernet-huvudet justeras den underliggande IP-adressen (IPv4 och IPv6) eller ARP-huvudet med 4 byte.

> [!WARNING] 
> *Se avsnittet "Ethernet-huvuden" nedan för viktiga skillnader mellan IPv6- och IPv6 Ethernet-huvuden.*

Det finns flera inkommande paketfunktioner i NetX Duo. Om det mottagna paketet är ett ARP-nx_arp_packet_deferred_receive anropas. _*_ Om det mottagna paketet är ett RARP-paket _*_nx_rarp_packet_deferred_receive_*_ anropas . Det finns flera alternativ för att hantera inkommande IP-paket. För den snabbaste hanteringen av IP-paket _*_nx_ip_packet_receive_*_ anropas . Den här metoden har minst omkostnader, men kräver mer bearbetning i drivrutinens isr-hanterare (receive interrupt service handler). För minimal ISR-bearbetning __ *_nx_ip_packet_deferred_receive_** anropas.

När det nya mottagningspaketet har skapats korrekt konfigureras den fysiska maskinvarans mottagningsbuffertar för att ta emot mer data. Detta kan kräva att NetX Duo-paket allokeras och att nyttolastadressen placeras i maskinvarans mottagningsbuffert, eller så kan det innebära att ändra en inställning i maskinvarans mottagningsbuffert. För att minimera risken för överkörning är det viktigt att maskinvarans mottagningsbuffertar har tillgängliga buffertar så snart som möjligt efter att ett paket har tagits emot.

> [!IMPORTANT] 
> *De första mottagningsbuffertarna konfigureras under drivrutinsinitieringen.*

### <a name="deferred-receive-packet-handling"></a>Uppskjuten pakethantering  
Drivrutinen kan skjuta upp mottagning av paketbearbetning till NETX Duo IP-hjälptråden. För vissa program kan detta vara nödvändigt för att minimera ISR-bearbetning samt ignorerade paket. 

Om du vill använda hantering av uppskjutna paket måste NetX Duo-biblioteket först kompileras med ***NX_DRIVER_DEFERRED_PROCESSING** _ definierat. Detta lägger till logiken för uppskjutna paket i NETX Duo IP-hjälptråden. När ett datapaket tas emot måste drivrutinen sedan anropa __nx_ip_packet_deferred_receive():*

```c
_nx_ip_packet_deferred_receive(ip_ptr, packet_ptr);
```
Funktionen för uppskjuten mottagning placerar det mottagningspaket som *representeras av packet_ptr* FIFO (länkad lista) och meddelar IP-hjälptråden. Efter körning anropar IP-hjälpfunktionen för uppskjuten hantering för att bearbeta varje uppskjutet paket. Bearbetningen av uppskjuten hanterare omfattar vanligtvis borttagning av paketets fysiska lagerrubrik (vanligtvis Ethernet) och sändning till någon av dessa NetX Duo-mottagningsfunktioner:

- ***_nx_ip_packet_receive***
- ***_nx_arp_packet_deferred_receive***
- ***_nx_rarp_packet_deferred_receive***

## <a name="ethernet-headers"></a>Ethernet-huvuden 

En av de viktigaste skillnaderna mellan IPv6 och IPv4 för Ethernet-huvuden är inställningen för bildrutetyp. När du skickar ut paket ansvarar Ethernet-drivrutinen för att ange Ethernet-ramtypen i utgående paket. För IPv6-paket ska ramtypen vara 0x86DD; För IPv4-paket ska ramtypen vara 0x0800.

Följande kodsegment illustrerar den här processen:

```c
NX_PACKET *packet_ptr;
packet_ptr = driver_req_ptr -> nx_ip_driver_packet;
if (packet_ptr -> nx_packet_ip_version == NX_IP_VERSION_V4)
{

   /* Set Ethernet frame type to IPv4 /*
   ethernet_frame_ptr -> frame_type = 0x0800;

   /* Swap endian-ness for little endian targets.*/
   NX_CHANGE_USHORT_ENDIAN(ethernet_frame_ptr -> frame_type);
}
else if (packet_ptr -> nx_packet_ip_version == NX_IP_VERSION_V6)
{

   /* Set Ethernet frame type to IPv6. /*
   ethernet_frame_ptr -> frame_type = 0x86DD;

   /* Swap endian-ness for little endian targets.*/
   NX_CHANGE_USHORT_ENDIAN(ethernet_frame_ptr -> frame_type);
}
else
{

   /* Unknown IP version. Free the packet we will not send. */
   nx_packet_transmit_release(packet_ptr);
}
```
På samma sätt bör Ethernet-drivrutinen för inkommande paket fastställa pakettypen från Ethernet-ramtypen. Den bör implementeras för att acceptera ramtyperna IPv6 (0x86DD), IPv4 (0x0800), ARP (0x0806) och RARP (0x8035).

## <a name="example-ram-ethernet-network-driver"></a>Exempel på RAM Ethernet-nätverksdrivrutin

NetX Duo-demonstrationssystemet levereras med en liten RAM-baserad nätverksdrivrutin som definieras ***i filen nx_ram_network_driver.c.*** Drivrutinen förutsätter att ALLA IP-instanser finns i samma nätverk och tilldelar bara VIRTUELLA maskinvaruadresser (MAC-adresser) till varje enhetsinstans när de skapas. Den här filen är ett bra exempel på den grundläggande strukturen för fysiska nätverksdrivrutiner för NetX Duo. Användare kan utveckla sina egna nätverksdrivrutiner med hjälp av drivrutinsramverket som visas i det här exemplet.

Nätverksdrivrutinens inmatningsfunktion är ***_nx_ram_network_driver(),** _ som skickas till anropet för att skapa IP-instansen. Postfunktioner för ytterligare nätverksgränssnitt kan skickas till tjänsten _nx_ip_interface_attach()*. När IP-instansen börjar köras anropas drivrutinspostfunktionen för att initiera och aktivera enheten (se ärendet **NX_LINK_INITIALIZE** **och NX_LINK_ENABLE**). När **kommandot NX_LINK_ENABLE** har utfärdats bör enheten vara redo att överföra och ta emot paket. 

IP-instansen överför nätverkspaket via något av följande kommandon:

| Kommando                         |  Beskrivning                                                   |
| ------------------------------- | -------------------------------------------------------------- |
| ***NX_LINK_PACKET_SEND***    | Ett IPv4- eller IPv6-paket överförs,                   |
| ***NX_LINK_ARP_SEND***       | En ARP-begäran eller ett ARP-svarspaket överförs,    |
| ***NX_LINK_ARP_RARP_SEND*** | En omvänd ARP-begäran eller svarspaket överförs, |

Vid bearbetning av dessa kommandon måste nätverksdrivrutinen lägga till rätt Ethernet-ramrubrik och sedan skicka den till den underliggande maskinvaran för överföring. Under överföringsprocessen har nätverksdrivrutinen exklusiv ägarskap för paketbuffertområdet. När data överförs (eller när data har kopierats till drivrutinens interna överföringsbuffert) ansvarar nätverksdrivrutinen för att frigöra paketbufferten genom att först flytta den förberedande pekaren förbi Ethernet-huvudet till IP-huvudet (och justera paketlängden därefter) och sedan genom att anropa ***nx_packet_transmit_release()-tjänsten*** för att släppa paketet. Om paketet inte frigörs efter dataöverföringen kommer paket att läcka.

Nätverksdrivrutinen ansvarar också för att hantera inkommande datapaket. I RAM-drivrutinsexempel bearbetas det mottagna paketet av funktionen ***_nx_ram_network_driver_receive()***. När enheten tar emot en Ethernet-ram ansvarar drivrutinen för att lagra data i NX_PACKET struktur. Observera att NetX Duo förutsätter att IP-huvudet startar från en adress som är justerad med 4 byte. Eftersom längden på Ethernet-huvudet är 14byte måste drivrutinen lagra starten av Ethernet-huvudet på 2 byte justerad adress för att garantera att IP-huvudet börjar vid 4 byte justerad adress.

## <a name="tcpip-offload-driver-guidance"></a>Vägledning för TCP/IP-avlastningsdrivrutin
För TCP/IP-avlastningsfunktionen behövs en drivrutinsfunktion för varje IP-gränssnitt. Här är en lista över ytterligare uppgifter för nätverksdrivrutiner.

* För kommandot `NX_LINK_INITIALIZE` ,
  * Skapa en drivrutinstråd för att hantera TCP/IP-avlastning för mottagning av händelser.
* För kommandot `NX_LINK_INTERFACE_ATTACH` ,
  * Ange drivrutinsgränssnittet som kapacitet. Se exempelkoden nedan.
``` C
driver_req_ptr -> nx_ip_driver_interface -> nx_interface_capability_flag = NX_INTERFACE_CAPABILITY_TCPIP_OFFLOAD;
```
* För kommandot `NX_LINK_ENABLE` ,
  * Starta drivrutinstråden.
  * Ange funktionen FÖR TCP/IP-återanrop till drivrutinsgränssnitt. Se exempelkoden nedan.
``` C
driver_req_ptr -> nx_ip_driver_interface -> nx_interface_tcpip_offload_handler = _nx_driver_tcpip_handler;
```
* För kommandot `NX_LINK_DISABLE` ,
  * Stoppa drivrutinstråden
  * Rensa tcp/IP-återanropsfunktionen i drivrutinsgränssnittet.
* För kommandot `NX_LINK_UNINITIALIZE` ,
  * Ta bort drivrutinstråden

### <a name="tcpip-offload-driver-thread"></a>Tcp/IP-avlastning av drivrutinstråd
Syftet med drivrutinstråden är att ta emot inkommande TCP- eller UDP-paket. I drivrutinstråden finns det vanligtvis en while-loop för att kontrollera om det finns inkommande TCP- eller UDP-paket eller en anslutning upprättad. När data är tillgängliga skickar du TCP- eller UDP-paketet till NetX Duo. Rummet mellan och `nx_packet_data_start` måste vara tillräckligt för att infoga `nx_packet_prepend_ptr` TCP/IP-huvudet. För TCP-socket allokerar du paket med typen `NX_TCP_PACKET` . För UDP-socket allokerar du paket med typen `NX_UDP_PACKET` . Fyll i inkommande data `nx_packet_append_ptr` från till `nx_packet_data_end` . Data i får `nx_packet_append_ptr` endast innehålla TCP- eller UDP-nyttolast. TCP/IP-huvudet **FÅR** inte fyllas i i paket. Justera paketlängden och ange mottagningsgränssnittet och anropa sedan `_nx_tcp_socket_driver_packet_receive` för TCP-paket `_nx_udp_socket_driver_packet_receive` och för UDP-paket. Om en TCP-anslutning stängs av anropar du `_nx_tcp_socket_driver_packet_receive` med paket inställt på NULL. När anslutningen har upprättats anropar du `_nx_tcp_socket_driver_establish` .

### <a name="tcpip-offload-driver-handler"></a>TCP/IP-avlastningsdrivrutinshanterare
Följande drivrutinskommandon krävs för nätverksgränssnitt med TCP/IP-tjänster. 
* För åtgärd `NX_TCPIP_OFFLOAD_TCP_CLIENT_SOCKET_CONNECT` ,
  * Allokera resurs om det behövs.
  * Bind till den lokala TCP-porten och anslut till servern.
  * Returnera lyckat resultat när anslutningen har upprättats. När anslutningen pågår returnerar du `NX_IN_PROGRESS` . Annars returneras ett fel.
* För åtgärd `NX_TCPIP_OFFLOAD_TCP_SERVER_SOCKET_LISTEN` ,
  * Sök efter dubblettlyssna först. Det kan anropas flera gånger på samma port. Första gången från `nx_tcp_server_socket_listen` och sedan `nx_tcp_server_socket_relisten` .
  * Allokera resurs om det behövs.
  * Lyssna på den lokala TCP-porten.
* För åtgärd `NX_TCPIP_OFFLOAD_TCP_SERVER_SOCKET_ACCEPT` ,
  * Allokera resurs om det behövs.
  * Acceptera anslutningen.
* För åtgärd `NX_TCPIP_OFFLOAD_TCP_SERVER_SOCKET_UNLISTEN` ,
  * Hitta TCP-socket som lyssnar på den lokala porten.
  * Stäng lyssningssocketen om den hittas.
* För åtgärd `NX_TCPIP_OFFLOAD_TCP_SOCKET_DISCONNECT` ,
  * Stäng TCP/IP-avlastningsanslutningen.
  * Ta bort bindning av lokal TCP-port.
  * Rensa resurser som skapades under anslutningen.
* För åtgärd `NX_TCPIP_OFFLOAD_TCP_SOCKET_SEND` ,
  * Skicka data via TCP/IP-avlastning. Var beredd på att hantera paketlängder som är större än MSS eller paketkedjeläge.
* För åtgärd `NX_TCPIP_OFFLOAD_UDP_SOCKET_BIND` ,
  * Allokera resurs om det behövs.
  * Bind till lokal UDP-port.
* För åtgärd `NX_TCPIP_OFFLOAD_UDP_SOCKET_UNBIND` ,
  * Ta bort bindning av lokal UDP-port.
  * Rensa resurser som skapades under bindningen.
* För åtgärd `NX_TCPIP_OFFLOAD_UDP_SOCKET_SEND` ,
  * Skicka data via TCP/IP-avlastning. Var beredd på att hantera paketlängder som är större än MTU eller paketkedjeläge.