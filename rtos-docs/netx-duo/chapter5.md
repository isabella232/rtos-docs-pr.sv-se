---
title: Kapitel 5 – Azure återställnings tider NetX Duo-nätverks driv rutiner
description: Det här kapitlet innehåller en beskrivning av nätverks driv rutiner för Azure återställnings tider NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ede57b7512f4a1a4c30759f428962739aaa2777c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826184"
---
# <a name="chapter-5---azure-rtos-netx-duo-network-drivers"></a>Kapitel 5 – Azure återställnings tider NetX Duo-nätverks driv rutiner

Det här kapitlet innehåller en beskrivning av nätverks driv rutiner för Azure återställnings tider NetX Duo. Den information som presenteras är utformad för att hjälpa utvecklare att skriva programspecifika nätverks driv rutiner för NetX Duo.

## <a name="driver-introduction"></a>Driv rutins introduktion

NX_IP-strukturen innehåller allt för att hantera en enskild IP-instans. Detta inkluderar allmän information om TCP/IP-protokoll samt den programspecifika fysiska nätverks driv Rutinens post rutin. Driv Rutinens post rutin definieras under ***nx_ip_create** _-tjänsten. Ytterligare enheter kan läggas till i IP-instansen via tjänsten _ *_nx_ip_interface_attach_**.

Kommunikationen mellan NetX Duo och programmets nätverks driv rutin görs via **NX_IP_DRIVER** begär ande strukturen. Den här strukturen definieras oftast lokalt i anroparens stack och släpps därför efter att driv rutinen och anrops funktionen returnerades. Strukturen definieras enligt följande.

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
## <a name="driver-entry"></a>Driv rutins post 

NetX Duo anropar funktionen för nätverks driv rutins post för driv rutins initiering och för att skicka paket och för olika kontroll-och status åtgärder, inklusive att initiera och aktivera nätverks enheten. NetX Duo utfärdar kommandon till nätverks driv rutinen genom att ange fältet ***nx_ip_driver_command** _ i strukturen _ *NX_IP_DRIVER** begär Ande. Funktionen driv rutins post har följande format:

```c
VOID my_driver_entry(NX_IP_DRIVER *request);
```
## <a name="driver-requests"></a>Driv rutins begär Anden

NetX Duo skapar en driv rutins förfrågan med ett särskilt kommando och anropar funktionen driv rutins post för att köra kommandot. Eftersom varje nätverks driv rutin har en enda post funktion gör NetX Duo alla förfrågningar via data strukturen för driv rutins förfrågan. Den ***nx_ip_driver_command** _-medlem i data strukturen för driv rutins förfrågan (_* NX_IP_DRIVER * *) definierar begäran. Statusinformation rapporteras tillbaka till anroparen i medlemmen **_nx_ip_driver_status_*_. Om det här fältet är _ * NX_SUCCESS * * slutfördes driv rutins förfrågan.

NetX Duo serialiserar all åtkomst till driv rutinen. Driv rutinen behöver därför inte hantera flera trådar som anropar post funktionen asynkront. Observera att funktionen enhets driv rutin körs med IP-mutex låst. Den interna funktionen i driv rutinen får därför inte blockera sig själv.

Vanligt vis hanterar enhets driv rutinen avbrott. Därför måste alla driv rutins funktioner vara avbrotts säkra.

### <a name="driver-initialization"></a>Driv rutins initiering   
Även om den faktiska initieringen av driv rutinen är programspecifik, består det vanligt vis av data struktur och initiering av fysisk maskin vara. Den information som krävs från NetX Duo för driv rutins initiering är IP-maximum överförings enhet (MTU), vilket är antalet byte som är tillgängliga för nytto lasten i IP-skiktet, inklusive IPv4 eller IPv6-huvud, och om det fysiska gränssnittet kräver logisk till fysisk mappning. Driv rutinen konfigurerar gränssnittets MTU-värde genom att anropa ***nx_ip_interface_mtu_set***.

Enhets driv rutinen måste anropa ***nx_ip_interface_address_mapping_configure** _ för att meddela netx Duo om det krävs en gränssnitts adress mappning eller inte. Om adress mappning krävs är driv rutinen ansvarig för att konfigurera gränssnittet med en giltig MAC-adress och ange MAC-adressen till NetX via _ *_nx_ip_interface_physical_address_set_* *.

När nätverks driv rutinen tar emot NX_LINK INITIALIZE-begäran från NetX duo får den en pekare till kontroll blocket för IP-kontroll som en del av det NX_IP_DRIVER begär ande kontroll blocket som visas ovan.

När programmet anropar ***nx_ip_create*** skickar IP-hjälp-tråden en driv rutins förfrågan med kommandot inställt på att NX_LINK_INITIALIZE till driv rutinen för att initiera sitt fysiska nätverks gränssnitt. Följande NX_IP_DRIVERs medlemmar används för Initialize-begäran.

| NX_IP_DRIVER &nbsp; medlem | Innebörd    |
| ------------------------- | ----------------------------- |
| nx_ip_driver_command   | NX_LINK_INITIALIZE    |
| nx_ip_driver_ptr       | Pekare till IP-instansen. Det här värdet bör sparas av driv rutinen så att driv rutins funktionen kan hitta IP-instansen som ska användas.    |
| nx_ip_driver_interface | Pekar mot nätverks gränssnitts strukturen inom IP-instansen. Den här informationen bör sparas av driv rutinen. Vid mottagning av paket ska driv rutinen använda gränssnitts strukturen när paketet skickas upp i stacken. Gränssnitts indexet (enhets index) kan hämtas genom att läsa medlems nx_interface_index i den här data strukturen. |
| nx_ip_driver_status    | Status för slut för ande. Om driv rutinen inte kan initiera det angivna gränssnittet till IP-instansen returnerar den en fel status som inte är noll. |


> [!NOTE]  
> *Driv rutinen anropas faktiskt från den IP-hjälp tråd som skapades för IP-instansen. Driv rutins rutinen bör därför inte utföra spärrnings åtgärder, eller så kan IP-underhjälps tråden stanna, vilket orsakar obegränsade fördröjningar för program som förlitar sig på IP-tråden*.

### <a name="enable-link"></a>Aktivera länk   
Därefter aktiverar IP-hjälpens tråd det fysiska nätverket genom att ange driv rutins kommandot för att NX_LINK_ENABLE i driv rutins förfrågan och skicka begäran till nätverks driv rutinen. Detta sker strax efter att IP Helper-tråden Slutför initierings förfrågan. Att aktivera länken kan vara så enkelt som att ange *nx_interface_link_up* fältet i gränssnitts instansen. Men det kan också innebära manipulering av den fysiska maskin varan. Följande NX_IP_DRIVERs medlemmar används för begäran om att aktivera länkar.

| NX_IP_DRIVER &nbsp; medlem       | Innebörd                      |
| ------------------------- | ---------------------------- |
| nx_ip_driver_command   | NX_LINK_ENABLE   |
| nx_ip_driver_ptr       | Pekare till IP-instans  |
| nx_ip_driver_interface | Pekare till gränssnitts instansen |
| nx_ip_driver_status    | Status för slut för ande. Om driv rutinen inte kan aktivera det angivna gränssnittet returneras en fel status som inte är noll. |

### <a name="disable-link"></a>Inaktivera länk   
Den här begäran görs av NetX Duo när en IP-instans tas bort av ***nx_ip_delete** _-tjänsten. Eller ett program kan utfärda detta kommando för att tillfälligt inaktivera länken för att spara energi. Den här tjänsten inaktiverar det fysiska nätverks gränssnittet på IP-instansen. Processen för att inaktivera länken kan vara så enkel som att rensa _nx_interface_link_up *-flaggan i gränssnitts instansen. Men det kan också innebära manipulering av den fysiska maskin varan. Det är vanligt vis en omvänd åtgärd för ***Aktivera länk**_ -åtgärden. När länken är inaktive rad är programbegäran _ *_Aktivera länk_** åtgärd för att aktivera gränssnittet.

Följande NX_IP_DRIVER-medlemmar används för att inaktivera länk förfrågan.

| NX_IP_DRIVER &nbsp; medlem     | Innebörd                      |
| ------------------------- | ---------------------------- |
| nx_ip_driver_command   | NX_LINK_DISABLE    |
| nx_ip_driver_ptr       | Pekare till IP-instans   |
| nx_ip_driver_interface | Pekare till gränssnitts instansen   |
| nx_ip_driver_status    | Status för slut för ande. Om driv rutinen inte kan inaktivera det angivna gränssnittet i IP-instansen returneras en fel status som inte är noll. |

### <a name="uninitialize-link"></a>Avinitiera länk   
Den här begäran görs av NetX Duo när en IP-instans tas bort av ***nx_ip_delete** _-tjänsten. Den här begäran avinitierar gränssnittet och frigör eventuella resurser som skapas under initierings fasen. Det är vanligt vis en omvänd åtgärd för åtgärden _ *_initiera länk_**. När gränssnittet har uninitalized kan enheten inte användas förrän gränssnittet initieras igen.

Följande NX_IP_DRIVER-medlemmar används för att inaktivera länk förfrågan.

| NX_IP_DRIVER &nbsp; medlem    | Innebörd                  |
|------------------------|--------------------------|
| nx_ip_driver_command   | NX_LINK_UNINITIALZE      |
| nx_ip_driver_ptr       | Pekare till IP-instans   |
| nx_ip_driver_interface | Pekare till gränssnitts instansen |
| nx_ip_driver_status    | Status för slut för ande. Om driv rutinen inte kan avinitiera det angivna gränssnittet till IP-instansen returneras en fel status som inte är noll. |

### <a name="packet-send"></a>Skicka paket   
Den här begäran görs under intern bearbetning av IPv4-eller IPv6-sändning, som alla NetX Duo-protokoll använder för att överföra paket (förutom ARP, RARP). Vid mottagning av kommandot paket sändning pekar *nx_packet_prepend_ptr* på början av det paket som ska skickas, vilket är början av IPv4-eller IPv6-sidhuvudet. *nx_packet_length* anger den totala storleken (i byte) för de data som överförs. Om *nx_packet_next* är giltigt lagras utgående IP-datagram i flera paket, driv rutinen krävs för att följa det länkade paketet och överföra hela ramen. Observera att giltiga data områden i varje kedjat paket lagras mellan *nx_packet_prepend_ptr* och *nx_packet_append_ptr*.

Driv rutinen ansvarar för att skapa ett fysiskt huvud. Om fysisk adress till IP-adress mappning krävs (t. ex. Ethernet), har IP-lagret redan löst MAC-adressen. Mål-MAC-adressen skickas från IP-instansen, lagras i *nx_ip_driver_physical_address_msw och nx_ip_driver_physical_address_lsw*.

När du har lagt till det fysiska huvudet anropar paket sändnings bearbetningen driv Rutinens output-funktion för att överföra paketet.

Följande NX_IP_DRIVER-medlemmar används för begäran om paket sändning.

| NX_IP_DRIVER &nbsp; medlem              | Innebörd                               |
| -----------------------------------| --------------------------------------|
| nx_ip_driver_command            | NX_LINK_PACKET_SEND                |
| nx_ip_driver_ptr                | Pekare till IP-instans                |
| nx_ip_driver_packet             | Pekare till det paket som ska skickas         |
| nx_ip_driver_interface          | Pekare till gränssnitts instansen.    |
| nx_ip_driver_physical_address_msw | Mest betydande 32-bitars fysisk adress (endast om fysisk mappning krävs) |
| nx_ip_driver_physical_address_lsw | Minst signifikant 32-bitars fysisk adress (endast om fysisk mappning krävs) |
| nx_ip_driver_status             | Status för slut för ande. Om driv rutinen inte kan skicka paketet returnerar den en fel status som inte är noll. |

### <a name="packet-broadcastipv4-packets-only"></a>Paket sändning (endast IPv4-paket)  
Den här begäran är nästan identisk med begäran om att skicka paket. Den enda skillnaden är att de fysiska mål adress fälten är inställda på MAC-adressen för Ethernet-broadcast. Följande NX_IP_DRIVER-medlemmar används för begäran om paket sändning.

| NX_IP_DRIVER &nbsp; medlem                | Innebörd                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_PACKET_BROADCAST                                                                                 |
| nx_ip_driver_ptr                   | Pekare till IP-instans                                                                                   |
| nx_ip_driver_packet                | Pekare till det paket som ska skickas                                                                            |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (sändning)                                                                                   |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (sändning)                                                                                   |
| nx_ip_driver_interface             | Pekare till gränssnitts instansen.                                                                       |
| nx_ip_driver_status                | Status för slut för ande. Om driv rutinen inte kan skicka paketet returnerar den en fel status som inte är noll. |

### <a name="arp-send"></a>Skicka ARP  
Den här begäran liknar också begäran om att skicka IP-paket. Den enda skillnaden är att Ethernet-huvudet anger ett ARP-paket i stället för ett IP-paket och att de fysiska mål adress fälten är inställda på MAC-broadcast-adress. Följande NX_IP_DRIVER-medlemmar används för ARP-sändnings förfrågan.

| NX_IP_DRIVER &nbsp; medlem                | Innebörd                                                                                                      |
|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_ARP_SEND                                                                                             |
| nx_ip_driver_ptr                   | Pekare till IP-instans                                                                                       |
| nx_ip_driver_packet                | Pekare till det paket som ska skickas                                                                                |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (sändning)                                                                                       |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (sändning)                                                                                       |
| nx_ip_driver_interface             | Pekare till gränssnitts instansen.                                                                           |
| nx_ip_driver_status                | Status för slut för ande. Om driv rutinen inte kan skicka ARP-paketet returnerar den en fel status som inte är noll. |

> [!IMPORTANT]  
> *Om fysisk mappning inte behövs krävs inte implementeringen av den här begäran*.

*Även om ARP har ersatts med Neighbor Discovery-protokollet och router identifierings protokollet i IPv6, måste Ethernet-nätverks driv rutiner fortfarande vara kompatibla med IPv4-peer-datorer och routrar. Driv rutinerna måste därför fortfarande hantera ARP-paket*.

### <a name="arp-response-send"></a>Skicka ARP-svar  
Den här begäran är nästan identisk med ARP-begäran om att skicka paket. Den enda skillnaden är att de fysiska mål adress fälten skickas från IP-instansen. Följande NX_IP_DRIVER-medlemmar används för ARP-svar skicka begäran.

| NX_IP_DRIVER &nbsp; medlem                  | Innebörd                                  |
| -------------------------------------- | -----------------------------------------|
| nx_ip_driver_command                | NX_LINK_ARP_RESPONSE_SEND            |
| nx_ip_driver_ptr                    | Pekare till IP-instans   |
| nx_ip_driver_packet                 | Pekare till det paket som ska skickas          |
| nx_ip_driver_physical_address_msw | Mest betydande 32-bitars fysisk adress |
| nx_ip_driver_physical_address_lsw | Minst signifikant 32-bitars fysisk adress |
| nx_ip_driver_interface              | Pekare till gränssnitts instansen |
| nx_ip_driver_status                 | Status för slut för ande. Om driv rutinen inte kan skicka ARP-paketet returnerar den en fel status som inte är noll. |

> [!IMPORTANT]  
> *Om fysisk mappning inte behövs krävs inte implementeringen av den här begäran*.

### <a name="rarp-send"></a>Skicka RARP   
Den här begäran är nästan identisk med ARP-begäran om att skicka paket. De enda skillnaderna är typ av paket huvud och de fysiska adress fälten krävs inte, eftersom det fysiska målet alltid är en broadcast-adress.

Följande NX_IP_DRIVERs medlemmar används för RARP Send-begäran.

| NX_IP_DRIVER &nbsp; medlem                | Innebörd                                                                                                       |
|------------------------------------|---------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_RARP_SEND                                                                                             |
| nx_ip_driver_ptr                   | Pekare till IP-instans                                                                                        |
| nx_ip_driver_packet                | Pekare till det paket som ska skickas                                                                                 |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (sändning)                                                                                        |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (sändning)                                                                                        |
| nx_ip_driver_interface             | Pekare till gränssnitts instansen.                                                                            |
| nx_ip_driver_status                | Status för slut för ande. Om driv rutinen inte kan skicka RARP-paketet returnerar den en fel status som inte är noll. |

> [!IMPORTANT]  
> *Program som kräver RARP-tjänst måste implementera det här kommandot*.

### <a name="multicast-group-join"></a>Anslutning till multicast-grupp   
Den här begäran görs med ***nx_igmp_multicast_interface Join** _ och _*_Nx_ipv4_multicast_interface_join_*_ service i IPv4, _ *_nxd_ipv6_multicast_interface_join_** service i IPv6 och olika åtgärder som krävs av IPv6. Nätverks driv rutinen tar den tillhandahållna multicast-gruppadressen och konfigurerar det fysiska mediet för att acceptera inkommande paket från den multicast-gruppadressen. Observera att för driv rutiner som inte har stöd för multicast-filter kan driv rutinen ta emot logik vara i läget ofiltrerad. I det här fallet kan driv rutinen behöva filtrera inkommande ramar baserat på målets MAC-adress, vilket minskar mängden trafik som skickas till IP-instansen. Följande NX_IP_DRIVER-medlemmar används för begäran om multicast-gruppkoppling.

| NX_IP_DRIVER &nbsp; medlem                  | Innebörd                                 |
| -------------------------------------- | --------------------------------------- |
| nx_ip_driver_command                | NX_LINK_MULTICAST_JOIN               |
| nx_ip_driver_ptr                    | Pekare till IP-instans  |
| nx_ip_driver_physical_address_msw | Mest signifikanta 32-bitar av fysisk multicast-adress |
| nx_ip_driver_physical_address_lsw | Minst signifikant 32-bitars fysisk multicast-adress |
| nx_ip_driver_interface              | Pekare till gränssnitts instansen |
| nx_ip_driver_status                 | Status för slut för ande. Om driv rutinen inte kan ansluta till multicast-gruppen returnerar den en fel status som inte är noll. |

> [!NOTE]  
> *IPv6-program kräver att multicast implementeras i driv rutinen för ICMPv6-baserade protokoll som adress konfiguration. För IPv4-program behövs dock inte implementeringen av den här begäran om inga multicast-funktioner krävs*.

> [!IMPORTANT]  
> *Om IPv6 inte är aktiverat och multicast-funktioner inte krävs av IPv4 krävs inte implementeringen av den här begäran*.

### <a name="multicast-group-leave"></a>Lämna multicast-grupp  
Den här begäran anropas genom att anropa de ***nx_igmp_multicast_interface_leave** _-eller _*_nx_ipv4_multicast_interface_leave_*_ -tjänsterna i IPv4, _ *_nxd_ipv6_multicast_interface_leave_** i IPv6 eller av olika interna netx Duo-åtgärder som krävs för IPv6. Driv rutinen tar bort den angivna Ethernet-multicast-adressen från multicast-listan. När en värd har lämnat en multicast-grupp tas paket i nätverket med den här Ethernet-multicast-adressen inte längre emot av den här IP-instansen. Följande NX_IP_DRIVERs medlemmar används för begäran om att lämna multicast-gruppen.

| NX_IP_DRIVER &nbsp; medlem              | Innebörd                              |
| -----------------------------------| -------------------------------------|
| nx_ip_driver_command            | NX_LINK_MULTICAST_LEAVE           |
| nx_ip_driver_ptr                | Pekare till IP-instans   |
| nx_ip_driver_physical_address_msw | Mest signifikanta 32 bitar av fysisk multicast-adress |
| nx_ip_driver_physical_address_lsw | Minst signifikant 32-bitars fysisk multicast-adress |
| nx_ip_driver_interface              | Pekare till gränssnitts instansen |
| nx_ip_driver_status                 | Status för slut för ande. Om driv rutinen inte kan lämna multicast-gruppen kommer den att returnera en fel status som inte är noll. |

> [!IMPORTANT]  
> *Om multicast-funktioner inte krävs av IPv4 eller IPv6 krävs inte implementeringen av den här begäran*.

### <a name="attach-interface"></a>Bifoga gränssnitt  
Den här begäran anropas från NetX Duo till enhets driv rutinen, så att driv rutinen kan associera driv rutins instansen med motsvarande IP-instans och den fysiska gränssnitts instansen inom IP-adressen. Följande NX_IP_DRIVER-medlemmar används för begäran om att bifoga gränssnitt.

| NX_IP_DRIVER &nbsp; medlem    | Innebörd                  |
|------------------------|--------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_ATTACH |
| nx_ip_driver_ptr       | Pekare till IP-instans   |
| nx_ip_driver_interface | Pekare till gränssnitts instansen.|
| nx_ip_driver_status    | Status för slut för ande. Om driv rutinen inte kan koppla bort det angivna gränssnittet till IP-instansen, returnerar den en fel status som inte är noll. |

### <a name="detach-interface"></a>Koppla från gränssnitt    
Den här begäran anropas av NetX Duo till enhets driv rutinen, vilket gör att driv rutinen kan avassociera driv rutins instansen med motsvarande IP-instans och den fysiska gränssnitts instansen inom IP-adressen. Följande NX_IP_DRIVER-medlemmar används för begäran om att bifoga gränssnitt.

| NX_IP_DRIVER &nbsp; medlem    | Innebörd                                                                                                                                    |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_DETACH                                                                                                                   |
| nx_ip_driver_ptr       | Pekare till IP-instans                                                                                                                     |
| nx_ip_driver_interface | Pekare till gränssnitts instansen.                                                                                                         |
| nx_ip_driver_status    | Status för slut för ande. Om driv rutinen inte kan koppla det angivna gränssnittet till IP-instansen, returnerar den en fel status som inte är noll. |

### <a name="get-link-status"></a>Hämta länk status    
Programmet kan fråga nätverks gränssnittets länk status med hjälp av NetX Duo service ***nx_ip_interface_status_check*** -tjänsten för alla gränssnitt på värden. Se kapitel 4, "Beskrivning av NetX Duo-tjänster" på sidan 149 för mer information om dessa tjänster.

Länkens status finns i fältet *nx_interface_link_up* i NX_INTERFACE-strukturen som *nx_ip_driver_interface* visaren pekar på. Följande NX_IP_DRIVERs medlemmar används för begäran om länk status.

| NX_IP_DRIVER &nbsp; medlem       | Innebörd                  |
| --------------------------- | -------------------------|
| nx_ip_driver_command     | NX_LINK_GET_STATUS    |
| nx_ip_driver_ptr         | Pekare till IP-instans   |
| nx_ip_driver_return_ptr | Pekar till målet för att placera statusen. |
| nx_ip_driver_interface   | Pekare till gränssnitts instansen   |
| nx_ip_driver_status      | Status för slut för ande. Om driv rutinen inte kan hämta en angiven status returneras en fel status som inte är noll. |

> [!NOTE]  
> ***nx_ip_status_check** _ är fortfarande tillgängligt för att kontrol lera status för det primära gränssnittet. Programutvecklare uppmanas dock att använda den gränssnitts specifika tjänsten: _ *_nx_ip_interface_status_check._**

### <a name="get-link-speed"></a>Hämta länk hastighet  
Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen lagrar länkens linje hastighet på den angivna destinationen. Följande NX_IP_DRIVER-medlemmar används för länk linjens hastighets förfrågan.

| NX_IP_DRIVER &nbsp; medlem   | Innebörd                   |
| ------------------------| ------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_SPEED          |
| nx_ip_driver_ptr         | Pekare till IP-instans                                                                                         |
| nx_ip_driver_return_ptr | Pekare till målet för att placera linje hastigheten                                                             |
| nx_ip_driver_interface   | Pekare till gränssnitts instansen                                                                              |
| nx_ip_driver_status      | Status för slut för ande. Om driv rutinen inte kan hämta hastighets information returneras en fel status som inte är noll. |

> [!IMPORTANT]  
> *Den här begäran används inte internt av netx Duo, så dess implementering är valfri*.

### <a name="get-duplex-type"></a>Hämta duplex-typ   
Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen lagrar länkens duplex-typ på det angivna målet. Följande NX_IP_DRIVER-medlemmar används för begäran om duplex-typ.

| NX_IP_DRIVER &nbsp; medlem   | Innebörd                                                                                                    |
| --------------------------- | -------------------------------------------------------------------------------------------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_DUPLEX_TYPE                                                                                    |
| nx_ip_driver_ptr         | Pekare till IP-instans                                                                                         |
| nx_ip_driver_return_ptr | Pekare till målet för att placera duplex-typen                                                            |
| nx_ip_driver_interface   | Pekare till gränssnitts instansen                                                                              |
| nx_ip_driver_status      | Status för slut för ande. Om driv rutinen inte kan hämta information om duplex, returnerar den en fel status som inte är noll. |

> [!IMPORTANT]  
> *Den här begäran används inte internt av netx Duo, så dess implementering är valfri*.

### <a name="get-error-count"></a>Hämta fel antal   
Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen lagrar länkens fel antal på den angivna destinationen. För att stödja den här funktionen måste driv rutinen spåra åtgärds fel. Följande NX_IP_DRIVER-medlemmar används för begäran om länk fel räkning.

| NX_IP_DRIVER &nbsp; medlem   | Innebörd                   |
| --------------------------- | -------------------------------|
| nx_ip_driver_command     | NX_LINK_GET_ERROR_COUNT   |
| nx_ip_driver_ptr         | Pekare till IP-instans   |
| nx_ip_driver_return_ptr | Pekare till målet för att placera antalet fel |
| nx_ip_driver_interface   | Pekare till gränssnitts instansen|
| nx_ip_driver_status      | Status för slut för ande. Om driv rutinen inte kan hämta antalet fel, returnerar den en fel status som inte är noll. |

> [!IMPORTANT]
> *Den här begäran används inte internt av netx Duo, så dess implementering är valfri*.

### <a name="get-receive-packet-count"></a>Hämta antal mottagna paket    
Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen lagrar länkens antal mottagna paket på det angivna målet. För att stödja den här funktionen måste driv rutinen hålla koll på antalet mottagna paket. Följande NX_IP_DRIVERs medlemmar används för begäran om att räkna antalet mottagna paket.

| NX_IP_DRIVER &nbsp; medlem       | Innebörd                        |
| --------------------------- | -------------------------------|
| nx_ip_driver_command     | NX_LINK_GET_RX_COUNT      |
| nx_ip_driver_ptr         | Pekare till IP-instans  |
| nx_ip_driver_return_ptr | Pekare till målet för att placera antalet mottagna paket   |
| nx_ip_driver_interface   | Pekare till det fysiska nätverks gränssnittet  |
| nx_ip_driver_status      | Status för slut för ande. Om driv rutinen inte kan få mottagnings antal, returnerar den en fel status som inte är noll. |

> [!IMPORTANT]  
> *Den här begäran används inte internt av netx Duo, så dess implementering är valfri*.

### <a name="get-transmit-packet-count"></a>Hämta antal sändnings paket   
Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen lagrar länkens antal överförings paket på den angivna destinationen. För att stödja den här funktionen måste driv rutinen hålla koll på varje paket som skickas till varje gränssnitt. Följande NX_IP_DRIVER-medlemmar används för begäran om antal länkar för att skicka paket.

| NX_IP_DRIVER &nbsp; medlem   | Innebörd                   |
| ----------------------- | ------------------------- |
| nx_ip_driver_command | NX_LINK_GET_TX_COUNT  |
| nx_ip_driver_ptr     | Pekare till IP-instans    |
| nx_ip_driver_return_ptr | Pekare till målet för att placera antalet överförings paket  |
| nx_ip_driver_interface   | Pekare till gränssnitts instansen   |
| nx_ip_driver_status      | Status för slut för ande. Om driv rutinen inte kan hämta antal överföringar returneras en fel status som inte är noll. |

> [!IMPORTANT]  
> *Den här begäran används inte internt av netx Duo, så dess implementering är valfri*.

### <a name="get-allocation-errors"></a>Hämta tilldelnings fel   
Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen lagrar länkens antal allokeringsfel tilldelnings fel på den angivna destinationen. Följande NX_IP_DRIVERs medlemmar används för begäran om tilldelning av länk tilldelnings fel.

| NX_IP_DRIVER &nbsp; medlem       | Innebörd                       |
| --------------------------- | ----------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_ALLOC_ERRORS  |
| nx_ip_driver_ptr         | Pekare till IP-instans     |
| nx_ip_driver_return_ptr | Pekare till målet för att placera tilldelnings fel antalet  |
| nx_ip_driver_interface   | Pekare till gränssnitts instansen  |
| nx_ip_driver_status      | Status för slut för ande. Om driv rutinen inte kan hämta allokeringsfel, returnerar den en fel status som inte är noll. |

> [!IMPORTANT]  
> *Den här begäran används inte internt av netx Duo, så dess implementering är valfri*.

### <a name="driver-deferred-processing"></a>Driv rutin uppskjuten bearbetning    
Den här begäran görs från IP-hjälpens tråd som svar på den driv rutin som anropar _* **nx_ip_driver_deferred_processing**_ rutinen från en överföring eller ta emot ISR. Detta gör att driv rutinen ISR kan skjuta upp paket mottagningen och skicka bearbetningen till IP-hjälpen och därmed minska mängden att bearbeta i ISR. Fältet _nx_interface_additional_link_info * i NX_INTERFACE-strukturen som anges av *nx_ip_driver_interface* kan användas av driv rutinen för att lagra information om den uppskjutna bearbetnings händelsen från tråd kontexten för IP-hjälp. Följande NX_IP_DRIVERs medlemmar används för den uppskjutna bearbetnings händelsen.

| NX_IP_DRIVER &nbsp; medlem     | Innebörd                           |
| ------------------------- | --------------------------------- |
| nx_ip_driver_command   | NX_LINK_DEFERRED_PROCESSING    |
| nx_ip_driver_ptr       | Pekare till IP-instans            |
| nx_ip_driver_interface | Pekare till gränssnitts instansen |

### <a name="set-physical-address"></a>Ange fysisk adress  
Den här begäran görs inifrån ***nx_ip_interface_physical_address_set** _-tjänsten. Med den här tjänsten kan ett program ändra den fysiska gränssnitts adressen vid körning. Vid mottagning av det här kommandot krävs driv rutinen för att omkonfigurera maskin varu adressen för nätverks gränssnittet till den angivna fysiska adressen. Eftersom IP-instansen redan har den nya adressen behöver du inte anropa tjänsten _ *_nx_ip_interface_address_set_** från det här kommandot.

Följande NX_IP_DRIVER-medlemmar används för begäran om användar kommando.

| NX_IP_DRIVER &nbsp; medlem      | Innebörd                      |
| -------------------------- | ---------------------------- |
| nx_ip_driver_command    | NX_LINK_SET_PHYSICAL_ADDRESS  |
| nx_ip_driver_ptr        | Pekare till IP-instans  |
| nx_ip_driver_interface  | Pekare till gränssnitts instansen   |
| nx_ip_driver_physical_ad dress_msw | Mest signifikanta 32 bitar av den nya fysiska adressen  |
| nx_ip_driver_physical_ad dress_lsw | Minst signifikant 32-bitar av den nya fysiska adressen  |
| nx_ip_driver_status                  | Status för slut för ande. Om driv rutinen inte kan konfigurera om den fysiska adressen kommer den att returnera en fel status som inte är noll. |

### <a name="user-commands"></a>Användar kommandon    
Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen bearbetar programspecifika användar kommandon. Följande NX_IP_DRIVER-medlemmar används för begäran om användar kommando.

| NX_IP_DRIVER &nbsp; medlem       | Innebörd                       |
| --------------------------- | ----------------------------- |
| nx_ip_driver_command     | NX_LINK_USER_COMMAND       |
| nx_ip_driver_ptr         | Pekare till IP-instans        |
| nx_ip_driver_return_ptr | Användardefinierad       |
| nx_ip_driver_interface   | Pekare till gränssnitts instansen    |
| nx_ip_driver_status      | Status för slut för ande. Om driv rutinen inte kan köra användar kommandon returnerar den en fel status som inte är noll. |

> [!IMPORTANT] 
> *Den här begäran används inte internt av netx Duo, så dess implementering är valfri*.

### <a name="unimplemented-commands"></a>Ej implementerade kommandon  
Kommandona som inte implementeras av nätverks driv rutinen måste ha värdet NX_UNHANDLED_COMMAND i fältet retur status.

## <a name="driver-capability"></a>Driv rutins kapacitet

Vissa nätverks gränssnitt erbjuder avlastnings funktioner för kontroll summa. Enhets driv rutiner kan dra nytta av maskin varu accelerationerna för att frigöra CPU-tid från att köra olika beräkningar av kontroll summor.

Beroende på maskin varans stöd för kontroll summa för maskin vara måste enhets driv rutinen informera IP-instansen som maskin varu funktionen är aktive rad för. På så sätt kan IP-instansen vara medveten om maskin varu funktionen och avlasta så mycket beräkning till maskin varan som möjligt. Driv rutinen ska använda API- ***nx_ip_interface_capability_set*** för att ange alla funktioner som det fysiska gränssnittet kan hantera.

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

För en beräkning av kontroll summa som kan utföras i maskin vara, måste driv rutinen konfigurera maskin varan eller buffertens beskrivningar korrekt så att kontroll summan för ett pågående paket kan genereras och infogas i rubriken av maskin varan. Vid mottagning av ett paket bör logiken för maskin varu kontroll kunna verifiera värdet för kontroll summan. Om värdet för kontroll summan är felaktigt ska den mottagna ramen tas bort.

Även om möjligheten att utföra beräkning av kontroll summa i maskin vara, behåller IP-instansen fortfarande kontroll summa. I vissa scenarier, t. ex. ett UDP-datagram som går via IPsec-skydd, måste UDP-kontrollsumman beräknas i program vara innan UDP-ramen skickas nedåt i stacken. De flesta maskin varu kontroll summor har inte stöd för beräkning av kontroll summa för ett data segment som skyddas av IPsec. För en UDP-eller ICMP-ram som behöver fragmenteras måste UDP-eller ICMP-kontrollsumma beräknas i program varan. De flesta logiska maskin varu kontrollers logik hanterar inte det fall där data delas upp i flera ramar.

## <a name="driver-output"></a>Driv rutins utdata  

Alla tidigare nämnda paket överförings begär Anden kräver en output-funktion som implementeras i driv rutinen. En speciell överförings logik är maskin varu information, men den består vanligt vis av att kontrol lera maskin varu kapaciteten för att skicka paketet omedelbart. Om möjligt läses paketets nytto Last (och ytterligare nytto laster i paket kedjan) in i en eller flera buffertar för maskin varu överföring och en överförings åtgärd initieras. Om paketet inte ryms i tillgängliga överföringsbuffert, ska paketet placeras i kö och skickas när överförings buffertarna blir tillgängliga.

Den rekommenderade överförings kön är en länkad lista med både huvud-och slut punkter. Nya paket läggs till i slutet av kön och behåller det äldsta paketet längst fram. Fältet *nx_packet_queue_next* används som paketets nästa länk i kön. Driv rutinen definierar huvud-och slut punkterna i överförings kön.

> [!CAUTION]  
> *Eftersom den här kön nås från tråden och avbryter delar av driv rutinen måste avbrotts skyddet placeras runt köns manipulering*.

De flesta fysiska maskin varu implementeringar genererar ett avbrott vid slut för ande av paket överföring. När driv rutinen tar emot ett sådant avbrott, frigör den vanligen de resurser som är associerade med paketet som skickas. Om överförings logiken läser data direkt från NX_PACKET-bufferten bör driv rutinen använda tjänsten ***nx_packet_transmit_release*** för att frigöra paketet som associeras med överföringen slutförs tillbaka till den tillgängliga poolen. Därefter undersöker driv rutinen överförings kön för ytterligare paket som väntar på att skickas. Så många av de köade överförings paket som passar i de köade överförings-och maskin varu buffertarna placeras de i kö och läses in i buffertarna. Detta följs genom att en annan sändnings åtgärd initieras.

Så snart data i NX_PACKET har flyttats till sändnings-FIFO (eller om en driv rutin stöder noll kopierings åtgärd NX_PACKET, så måste driv rutinen flytta *nx_packet_prepend_ptr* till början av IP-huvudet innan du anropar ***nx_packet_transmit_release.** _ Kom ihåg att justera _nx_packet_length * fält enligt detta. Om en IP-ram består av flera paket måste endast huvudet i paket kedjan släppas.

## <a name="driver-input"></a>Driv rutins Indatatyp

Vid mottagning av mottagna paket avbrott hämtar nätverks driv rutinen paketet från den fysiska maskin varan som tar emot buffertar och skapar ett giltigt NetX Duo-paket. Genom att skapa ett giltigt NetX Duo-paket kan du konfigurera lämpligt längd fält och kedja samman flera paket om det inkommande paketets storlek är större än en enda paket nytto Last. När den väl har skapats flyttas *prepend_ptr* efter den fysiska skikt rubriken och mottagnings paketet skickas till netx Duo.

NetX Duo förutsätter att IP (IPv4 och IPv6) och ARP-huvuden är justerade efter en **ulong** -gränser. NetX Duo-drivrutinen måste därför se till att den här justeringen. I Ethernet-miljöer görs detta genom att du startar Ethernet-huvudet två byte från paketets början. När *nx_packet_prepend_ptr* flyttas bortom Ethernet-huvudet, är den underliggande IP-adressen (IPv4 och IPv6) eller ARP-huvudet 4-byte-justerad.

> [!WARNING] 
> *Se avsnittet "Ethernet-rubriker" nedan för viktiga skillnader mellan IPv6-och IPv6-Ethernet-huvuden*.

Det finns flera mottagna paket funktioner i NetX Duo. Om det mottagna paketet är ett ARP-paket anropas _* **nx_arp_packet_deferred_receive**_ . Om det mottagna paketet är ett RARP-paket anropas _ _*_nx_rarp_packet_deferred_receive_*_ . Det finns flera alternativ för att hantera inkommande IP-paket. För den snabbaste hanteringen av IP-paket, anropas _ _*_nx_ip_packet_receive_*_ . Den här metoden har minst extra kostnader men kräver mer bearbetning i driv Rutinens tjänst hanterare för mottagnings avbrott (ISR). För minimal ISR-bearbetning är _ @*_nx_ip_packet_deferred_receive_** anropas.

När det nya mottagnings paketet har skapats korrekt är den fysiska maskin varans mottagningsbuffertar installations program för att ta emot mer data. Detta kan kräva att du tilldelar NetX Duo-paket och placerar nytto Last adressen i den mottagande bufferten för maskin vara, eller att du bara behöver ändra en inställning i bufferten för maskin vara. För att minimera överskridnings möjligheterna är det viktigt att maskin varans mottagande buffertar har tillgängliga buffertar så snart som möjligt efter det att ett paket har mottagits.

> [!IMPORTANT] 
> *De första mottagningsbuffertar installeras när driv rutinen initieras*.

### <a name="deferred-receive-packet-handling"></a>Uppskjuten mottagning av paket hantering  
Driv rutinen kan skjuta upp mottagning av paket bearbetning till NetX Duo IP Helper-tråden. För vissa program kan detta vara nödvändigt för att minimera ISR-bearbetning samt ignorerade paket. 

Om du vill använda uppskjuten paket hantering måste NetX Duo-biblioteket först kompileras med ***NX_DRIVER_DEFERRED_PROCESSING** _ definierade. Detta lägger till den uppskjutna paket logiken i NetX Duo IP Helper-tråden. Därefter måste driv rutinen anropa __nx_ip_packet_deferred_receive () för att ta emot ett data paket:*

```c
_nx_ip_packet_deferred_receive(ip_ptr, packet_ptr);
```
Funktionen för uppskjuten mottagning placerar det mottagna paketet som representeras av *packet_ptr* på en FIFO (länkad lista) och meddelar IP-hjälpens tråd. Efter körningen anropar IP-hjälpen upprepade gånger den uppskjutna hanterings funktionen för att bearbeta varje uppskjutet paket. Bearbetningen av uppskjuten hanterare tar vanligt vis bort paketets fysiska lager rubrik (vanligt vis Ethernet) och skickar den till någon av dessa NetX Duo-mottagnings funktioner:

- ***_nx_ip_packet_receive***
- ***_nx_arp_packet_deferred_receive***
- ***_nx_rarp_packet_deferred_receive***

## <a name="ethernet-headers"></a>Ethernet-rubriker 

En av de viktigaste skillnaderna mellan IPv6 och IPv4 för Ethernet-huvuden är ramtypen. När du skickar ut paket ansvarar Ethernet-drivrutinen för att ställa in Ethernet-ramtypen i utgående paket. För IPv6-paket ska ramtypen vara 0x86DD; för IPv4-paket ska ramtypen vara 0x0800.

Följande kod segment illustrerar den här processen:

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
På samma sätt bör Ethernet-drivrutinen för inkommande paket fastställa paket typen från Ethernet-ramtypen. Den bör implementeras för att godkänna 0x86DD-, IPv4-(0x0800), ARP-(0x0806) och RARP-(0x8035) ramtyper.

## <a name="example-ram-ethernet-network-driver"></a>Exempel på RAM Ethernet-nätverks driv rutin

Demonstrations systemet NetX Duo levereras med en liten RAM-baserad nätverks driv rutin som definieras i filen ***nx_ram_network_driver. c.*** Den här driv rutinen förutsätter att IP-instanserna är alla i samma nätverk och bara tilldelar virtuella maskin varu adresser (MAC-adresser) till varje enhets instans när de skapas. Den här filen ger ett enkelt exempel på grund strukturen för NetX Duo fysiska nätverks driv rutiner. Användare kan utveckla sina egna nätverks driv rutiner med hjälp av driv rutins ramverket som presenteras i det här exemplet.

Inmatnings funktionen för nätverks driv rutinen är ***_nx_ram_network_driver (),** _ som skickas till IP-instansen skapa anrop. Post funktioner för ytterligare nätverks gränssnitt kan skickas till _nx_ip_interface_attach () *-tjänsten. När IP-instansen börjar köras anropas funktionen för driv rutins post för att initiera och aktivera enheten (se fall **NX_LINK_INITIALIZE** och **NX_LINK_ENABLE**). När **NX_LINK_ENABLE** kommandot har utfärdats bör enheten vara redo att skicka och ta emot paket. 

IP-instansen överför nätverks paket via något av följande kommandon:

|                                 |                                                                |
| ------------------------------- | -------------------------------------------------------------- |
| ***NX_LINK_PACKET_SEND***    | Ett IPv4-eller IPv6-paket överförs,                   |
| ***NX_LINK_ARP_SEND***       | En ARP-begäran eller ett ARP-svars paket överförs,    |
| ***NX_LINK_ARP_RARP_SEND*** | En omvänd ARP-begäran eller ett svars paket överförs |

Vid bearbetning av dessa kommandon måste nätverks driv rutinen lägga lämpligt Ethernet-Rams huvud och sedan skicka den till den underliggande maskin varan för överföring. Under överförings processen har nätverks driv rutinen ensam ägarskap för paketets buffertzon. När data överförs (eller när data har kopierats till driv Rutinens interna överföringsbuffert) är nätverks driv rutinen ansvarig för att frigöra paketets buffert genom att först flytta lägga-pekaren förbi Ethernet-huvudet till IP-huvudet (och justera Paketets längd enligt detta) och sedan anropa tjänsten ***nx_packet_transmit_release ()*** för att frigöra paketet. Om du inte frigör paketet efter data överföringen kommer paket att läcka.

Nätverks enhetens driv rutin ansvarar också för hantering av inkommande data paket. I exempel på RAM-drivrutin bearbetas det mottagna paketet av funktionen ***_nx_ram_network_driver_receive ()***. När enheten får en Ethernet-ram ansvarar driv rutinen för att lagra data i NX_PACKET-strukturen. Observera att NetX Duo antar att IP-huvudet börjar från den justerade adressen på 4 byte. Eftersom längden på Ethernet-huvudet är 14byte måste driv rutinen lagra början av Ethernet-huvudet med en justerad adress på 2 byte för att garantera att IP-huvudet börjar med 4 byte-justerad adress.