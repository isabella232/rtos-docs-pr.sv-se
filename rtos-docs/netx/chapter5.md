---
title: Kapitel 5 – Azure återställnings tider NetX-nätverks driv rutiner
description: Det här kapitlet innehåller en beskrivning av nätverks driv rutiner för Azure återställnings tider NetX.
author: philmea
ms.author: philmea
ms.date: 09/11/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ccc55111d785d84cdb193c387830abbc03a15e7c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826853"
---
# <a name="chapter-5---netx-network-drivers"></a>Kapitel 5 – NetX nätverks driv rutiner

Det här kapitlet innehåller en beskrivning av nätverks driv rutiner för NetX. Den information som presenteras är utformad för att hjälpa utvecklare att skriva programspecifika nätverks driv rutiner för Azure återställnings tider-NetX.

## <a name="driver-introduction"></a>Driv rutins introduktion

NX_IP-strukturen innehåller allt för att hantera en enskild IP-instans. Detta inkluderar allmän information om TCP/IP-protokoll samt den programspecifika fysiska nätverks driv Rutinens post rutin. Driv Rutinens post rutin definieras under ***nx_ip_creates*** tjänsten. Ytterligare enheter kan läggas till i IP-instansen via tjänsten ***nx_ip_interface_attach*** .

Kommunikation mellan NetX och programmets nätverks driv rutin görs via **NX_IP_DRIVER** begär ande strukturen. Den här strukturen definieras oftast lokalt i anroparens stack och släpps därför efter att driv rutinen och anrops funktionen returnerades. Strukturen definieras enligt följande.

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

## <a name="driver-entry"></a>Driv rutins post

NetX anropar funktionen för nätverks driv rutins post för driv rutins initiering och för att skicka paket och för olika kontroll-och status åtgärder, inklusive att initiera och aktivera nätverks enheten. NetX utfärdar kommandon till nätverks driv rutinen genom att ange fältet ***nx_ip_driver_command** _ i strukturen _ *NX_IP_DRIVER** begär Ande. Funktionen driv rutins post har följande format:

```C
VOID my_driver_entry(NX_IP_DRIVER *request);
```

## <a name="driver-requests"></a>Driv rutins begär Anden

NetX skapar en driv rutins förfrågan med ett särskilt kommando och anropar funktionen driv rutins post för att köra kommandot. Eftersom varje nätverks driv rutin har en enda post funktion gör NetX alla begär Anden via data strukturen för driv rutins förfrågan. ***Nx_ip_driver_command*** medlem i data strukturen för driv rutins förfrågan (**NX_IP_DRIVER**) definierar begäran. Statusinformation rapporteras tillbaka till anroparen i medlems ***nx_ip_driver_status***. Om det här fältet är **NX_SUCCESS** slutförs driv rutins förfrågan.

NetX serialiserar all åtkomst till driv rutinen. Driv rutinen behöver därför inte hantera flera trådar som anropar post funktionen asynkront. Observera att funktionen enhets driv rutin körs med IP-mutex låst. Den interna funktionen i driv rutinen får därför inte blockera sig själv.

Vanligt vis hanterar enhets driv rutinen avbrott. Därför måste alla driv rutins funktioner vara avbrotts säkra.

### <a name="driver-initialization"></a>Driv rutins initiering

Även om den faktiska initieringen av driv rutinen är programspecifik, består det vanligt vis av data struktur och initiering av fysisk maskin vara. Den information som krävs från NetX för driv rutins initiering är IP-maximum överförings enhet (MTU), vilket är antalet byte som är tillgängliga för nytto lasten i IP-skiktet, inklusive IP-huvud, och om det fysiska gränssnittet kräver en logisk till fysisk mappning. Driv rutinen behöver

Konfigurera gränssnittets MTU genom att ange värdet i ***nx_interface_ip_mtu_size** _ i strukturen _ *NX_INTERFACE**.

Enhets driv rutinen måste också konfigurera värdet i ***nx_ip_interface_address_mapping_needed*** i

**NX_INTERFACE** för att informera netx om huruvida gränssnitts adress mappning krävs eller inte. Om adress mappning krävs är driv rutinen ansvarig för att konfigurera gränssnittet med en giltig MAC-adress och ange MAC-adressen till NetX.

När nätverks driv rutinen tar emot NX_LINK INITIALIZE-begäran från NetX, tar den emot en pekare till kontroll blocket för IP-kontroll som en del av det NX_IP_DRIVER begär ande kontroll block som visas ovan.

När programmet anropar ***nx_ip_create*** skickar IP-hjälp-tråden en driv rutins förfrågan med kommandot inställt på att NX_LINK_INITIALIZE till driv rutinen för att initiera sitt fysiska nätverks gränssnitt. Följande NX_IP_DRIVERs medlemmar används för Initialize-begäran.

| NX_IP_DRIVER medlem    | Innebörd |
|------------------------|-----------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INITIALIZE |
| nx_ip_driver_ptr       | Pekare till IP-instansen. Det här värdet bör sparas av driv rutinen så att driv rutins funktionen kan hitta IP-instansen som ska användas. |
| nx_ip_driver_interface | Pekar mot nätverks gränssnitts strukturen inom IP-instansen. Den här informationen bör sparas av driv rutinen. Vid mottagning av paket ska driv rutinen använda gränssnitts strukturen när paketet skickas upp i stacken. |
| nx_ip_driver_status    | Status för slut för ande. Om driv rutinen inte kan initiera det angivna gränssnittet till IP-instansen returnerar den en fel status som inte är noll.                                                                                           |


> [!IMPORTANT]
> *De flesta av driv rutins kommandona anropas från IP-hjälpens tråd som skapades för IP-instansen. Driv rutins rutinen bör därför inte utföra spärrnings åtgärder, eller så kan IP-underhjälps tråden stanna, vilket orsakar obegränsade fördröjningar för program som förlitar sig på IP-tråden.*

### <a name="enable-link"></a>Aktivera länk  

Därefter aktiverar IP-hjälpens tråd det fysiska nätverket genom att ange driv rutins kommandot för att NX_LINK_ENABLE i driv rutins förfrågan och skicka begäran till nätverks driv rutinen. Detta sker strax efter att IP Helper-tråden Slutför initierings förfrågan. Att aktivera länken kan vara så enkelt som att ange nx_interface_link_up fältet i gränssnitts instansen. Men det kan också innebära manipulering av den fysiska maskin varan. Följande NX_IP_DRIVERs medlemmar används för begäran om att aktivera länkar.

| NX_IP_DRIVER medlem    | Innebörd |
|------------------------|------------------------------------------|
| nx_ip_driver_command   | NX_LINK_ENABLE                                                                                                          |
| nx_ip_driver_ptr       | Pekare till IP-instans                                                                                                  |
| nx_ip_driver_interface | Pekare till gränssnitts instansen                                                                                       |
| nx_ip_driver_status    | Status för slut för ande. Om driv rutinen inte kan aktivera det angivna gränssnittet returneras en fel status som inte är noll. |



### <a name="disable-link"></a>Inaktivera länk  

Den här begäran görs av NetX när en IP-instans tas bort av ***nx_ip_delete** _-tjänsten. Eller ett program kan utfärda detta kommando för att tillfälligt inaktivera länken för att spara energi. Den här tjänsten inaktiverar det fysiska nätverks gränssnittet på IP-instansen. Processen för att inaktivera länken kan vara så enkel som att rensa _nx_interface_link_up *-flaggan i gränssnitts instansen. Men det kan också innebära manipulering av den fysiska maskin varan. Det är vanligt vis en omvänd åtgärd för ***Aktivera länk**_ -åtgärden. När länken är inaktive rad är programbegäran _ *_Aktivera länk_** åtgärd för att aktivera gränssnittet. Följande NX_IP_DRIVER-medlemmar används för att inaktivera länk förfrågan.

| NX_IP_DRIVER medlem    | Innebörd |
|------------------------|--------------------------------------|
| nx_ip_driver_command   | NX_LINK_DISABLE |
| nx_ip_driver_ptr       | Pekare till IP-instans |
| nx_ip_driver_interface | Pekare till gränssnitts instansen |
| nx_ip_driver_status    | Status för slut för ande. Om driv rutinen inte kan inaktivera det angivna gränssnittet i IP-instansen returneras en fel status som inte är noll. |


### <a name="uninitialize-link"></a>Avinitiera länk  

Den här begäran görs av NetX när en IP-instans tas bort av ***nx_ip_deletes*** tjänsten. Den här begäran avinitierar gränssnittet och frigör eventuella resurser som skapas under initierings fasen. Det är vanligt vis en omvänd åtgärd för åtgärden ***initiera länk*** . När gränssnittet har uninitalized kan enheten inte användas förrän gränssnittet initieras igen.

Följande NX_IP_DRIVER-medlemmar används för att inaktivera länk förfrågan.

| NX_IP_DRIVER medlem  | Innebörd                |
|----------------------|------------------------|
| nx_ip_driver_command | NX_LINK_UNINITIALZE    |
| nx_ip_driver_ptr     | Pekare till IP-instans |
| nx_ip_driver_interface | Pekare till gränssnitts instansen |
| nx_ip_driver_status    | Status för slut för ande. Om driv rutinen inte kan avinitiera det angivna gränssnittet till IP-instansen returneras en fel status som inte är noll. |


### <a name="packet-send"></a>Skicka paket  

Den här begäran görs under bearbetning av intern IP-överföring, bearbetning, som alla NetX-protokoll använder för att överföra paket (förutom ARP, RARP). Vid mottagning av kommandot paket sändning pekar *nx_packet_prepend_ptr* på början av paketet som ska skickas, vilket är början av IP-huvudet.
*nx_packet_length* anger den totala storleken (i byte) för de data som överförs. Om *nx_packet_next* är giltigt lagras utgående IP-datagram i flera paket, driv rutinen krävs för att följa det länkade paketet och överföra hela ramen. Observera att giltiga data områden i varje kedjat paket lagras mellan *nx_packet_prepend_ptr* och *nx_packet_append_ptr*.

Driv rutinen ansvarar för att skapa ett fysiskt huvud. Om fysisk adress till IP-adress mappning krävs (t. ex. Ethernet), har IP-lagret redan löst MAC-adressen. Mål-MAC-adressen skickas från IP-instansen, lagras i *nx_ip_driver_physical_address_msw och nx_ip_driver_physical_address_lsw.*

När du har lagt till det fysiska huvudet anropar paket sändnings bearbetningen driv Rutinens output-funktion för att överföra paketet.

Följande NX_IP_DRIVER-medlemmar används för begäran om paket sändning.

| NX_IP_DRIVER medlem               | Innebörd |
|-----------------------------------|---------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_PACKET_SEND |
| nx_ip_driver_ptr                  | Pekare till IP-instans |
| nx_ip_driver_packet               | Pekare till det paket som ska skickas |
| nx_ip_driver_interface            | Pekare till gränssnitts instansen.             |
| nx_ip_driver_physical_address_msw | Mest betydande 32-bitars fysisk adress (endast om fysisk mappning krävs) |
| nx_ip_driver_physical_address_lsw | Minst signifikant 32-bitars fysisk adress (endast om fysisk mappning krävs)    |
| nx_ip_driver_status               | Status för slut för ande. Om driv rutinen inte kan skicka paketet returnerar den en fel status som inte är noll.  |

### <a name="packet-broadcast"></a>Paket sändning  
Den här begäran är nästan identisk med begäran om att skicka paket. Den enda skillnaden är att de fysiska mål adress fälten är inställda på MAC-adressen för Ethernet-broadcast. Följande NX_IP_DRIVER-medlemmar används för begäran om paket sändning.

| NX_IP_DRIVER medlem                | Innebörd          |
|------------------------------------|--------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_PACKET_BROADCAST |
| nx_ip_driver_ptr                   | Pekare till IP-instans  |
| nx_ip_driver_packet                | Pekare till paketet som ska avslutas |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF-sändning) |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF-sändning) |
| nx_ip_driver_interface             | Pekare till gränssnitts instansen. |
| nx_ip_driver_status                | Status för slut för ande. Om driv rutinen inte kan skicka paketet returnerar den en fel status som inte är noll. |

### <a name="arp-send"></a>Skicka ARP  

Den här begäran liknar också begäran om att skicka IP-paket.
Den enda skillnaden är att Ethernet-huvudet anger ett ARP-paket i stället för ett IP-paket och att de fysiska mål adress fälten är inställda på MAC-broadcast-adress. Följande NX_IP_DRIVER-medlemmar används för ARP-sändnings förfrågan.

| **NX_IP_DRIVER medlem** | **Innebörd** |
| --- | --- |
| nx_ip_driver_command | NX_LINK_ARP_SEND |
| nx_ip_driver_ptr | Pekare till IP-instans. |
| nx_ip_driver_packet | Pekare till det paket som ska skickas. |
| nx_ip_driver_physical_address_msw | 0x0000FFFF (sändning) |
| nx_ip_driver_physical_address_lsw | 0xFFFFFFFF (sändning) |
| nx_ip_driver_interface | Pekare till gränssnitts instansen. |
| nx_ip_driver_status | Status för slut för ande. Om driv rutinen inte kan skicka ARP-paketet returnerar den en fel status som inte är noll. |

*Om fysisk mappning inte behövs krävs inte implementeringen av den här begäran.*

### <a name="arp-response-send"></a>Skicka ARP-svar  

Den här begäran är nästan identisk med ARP-begäran om att skicka paket. Den enda skillnaden är att de fysiska mål adress fälten skickas från IP-instansen. Följande NX_IP_DRIVER-medlemmar används för ARP-svar skicka begäran.

| NX_IP_DRIVER medlem               | Innebörd |
|-----------------------------------| ------------------------------------|
| nx_ip_driver_command              | NX_LINK_ARP_RESPONSE_SEND |
| nx_ip_driver_ptr                  | Pekare till IP-instans |
| nx_ip_driver_packet               | Pekare till det paket som ska skickas|
| nx_ip_driver_physical_address_msw | Mest betydande 32-bitars fysisk adress |
| nx_ip_driver_physical_address_lsw | Minst signifikant 32-bitars fysisk adress                     |
| nx_ip_driver_interface            | Pekare till gränssnitts instansen |
| nx_ip_driver_status               | Status för slut för ande. Om driv rutinen inte kan skicka ARP-paketet returnerar den en fel status som inte är noll. |

> [!NOTE]
> *Om fysisk mappning inte behövs krävs inte implementeringen av den här begäran.*

### <a name="rarp-send"></a>Skicka RARP  

Den här begäran är nästan identisk med ARP-begäran om att skicka paket. De enda skillnaderna är typ av paket huvud och de fysiska adress fälten krävs inte, eftersom det fysiska målet alltid är en broadcast-adress.

Följande NX_IP_DRIVERs medlemmar används för RARP Send-begäran.

| NX_IP_DRIVER medlem               | Innebörd |
|-----------------------------------|---------------------------------|
| nx_ip_driver_command              |NX_LINK_RARP_SEND |
| nx_ip_driver_ptr                  | Pekare till IP-instans |
| nx_ip_driver_packet               | Pekare till det paket som ska skickas |
| nx_ip_driver_physical_address_msw | 0x0000FFFF (sändning) |
| nx_ip_driver_physical_address_lsw | 0xFFFFFFFF (sändning) |
| NX_IP_DRIVER medlem               | Innebörd |
| nx_ip_driver_interface            | Pekare till gränssnitts instansen |
| nx_ip_driver_status               | Status för slut för ande. Om driv rutinen inte kan skicka RARP-paketet returnerar den en fel status som inte är noll.  |

> [!NOTE]
> *Program som kräver RARP-tjänst måste implementera det här kommandot.*

### <a name="multicast-group-join"></a>Anslutning till multicast-grupp  

Den här begäran görs med tjänsten för ***nx_igmp_multicast_interface anslutning*** . Nätverks driv rutinen tar den tillhandahållna multicast-gruppadressen och konfigurerar det fysiska mediet för att acceptera inkommande paket från den multicast-gruppadressen. Observera att för driv rutiner som inte har stöd för multicast-filter kan driv rutinen ta emot logik vara i läget ofiltrerad. I det här fallet kan driv rutinen behöva filtrera inkommande ramar baserat på målets MAC-adress, vilket minskar mängden trafik som skickas till IP-instansen. Följande NX_IP_DRIVER-medlemmar används för begäran om multicast-gruppkoppling.

| NX_IP_DRIVER medlem               | Innebörd |
|-----------------------------------|-----------------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_MULTICAST_JOIN                                                |
| nx_ip_driver_ptr                  | Pekare till IP-instans                                                |
| nx_ip_driver_physical_address_msw | Mest signifikanta 32-bitar av fysisk multicast-adress                |
| nx_ip_driver_physical_address_lsw | Minst signifikant 32-bitars fysisk multicast-adress               |
| nx_ip_driver_interface            | Pekare till gränssnitts instansen                                     |
| nx_ip_driver_status               | Status för slut för ande. Om driv rutinen inte kan ansluta till multicast-gruppen returnerar den en fel status som inte är noll. |


### <a name="multicast-group-leave"></a>Lämna multicast-grupp  

Den här begäran anropas genom att ***nx_igmp_multicast_leave*** tjänsten uttryckligen anropas. Driv rutinen tar bort den angivna Ethernet-multicast-adressen från multicast-listan. När en värd har lämnat en multicast-grupp tas paket i nätverket med den här Ethernet-multicast-adressen inte längre emot av den här IP-instansen. Följande NX_IP_DRIVERs medlemmar används för begäran om att lämna multicast-gruppen.

| NX_IP_DRIVER medlem               | Innebörd |
|-----------------------------------|-----------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_MULTICAST_LEAVE |
| nx_ip_driver_ptr                  | Pekare till IP-instans |
| nx_ip_driver_physical_address_msw | Mest betydande 32-bitars fysiska multicast-Dress |
| nx_ip_driver_physical_address_lsw | Minst signifikant 32-bitars fysisk multicast-adress |
| nx_ip_driver_interface            | Pekare till gränssnitts instansen |
| nx_ip_driver_status               | Status för slut för ande. Om driv rutinen inte kan lämna multicast-gruppen kommer den att returnera en fel status som inte är noll. |


### <a name="attach-interface"></a>Bifoga gränssnitt  

Den här begäran anropas från NetX till enhets driv rutinen, så att driv rutinen kan associera driv rutins instansen med motsvarande IP-instans och den fysiska gränssnitts instansen inom IP-adressen. Följande NX_IP_DRIVER-medlemmar används för begäran om att bifoga gränssnitt.

| NX_IP_DRIVER medlem    | Innebörd |
|------------------------|-------------------------------------------------|
| nx_ip_driver_command   | X_LINK_INTERFACE_ATTACH |
| nx_ip_driver_ptr       | Pekare till IP-instans |
| nx_ip_driver_interface | Pekare till gränssnitts instansen. |
| nx_ip_driver_status    | Status för slut för ande. Om driv rutinen inte kan koppla bort det angivna gränssnittet till IP-instansen, returnerar den en fel status som inte är noll.  |


### <a name="detach-interface"></a>Koppla från gränssnitt  

Den här begäran anropas av NetX till driv rutinen, vilket gör att driv rutinen kan avassociera driv rutins instansen med motsvarande IP-instans och den fysiska gränssnitts instansen inom IP-adressen. Följande NX_IP_DRIVER-medlemmar används för begäran om att bifoga gränssnitt.

| NX_IP_DRIVER medlem    | Innebörd |
|------------------------|---------------------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_DETACH |
| nx_ip_driver_ptr       | Pekare till IP-instans |
| nx_ip_driver_interface | Pekare till gränssnitts instansen. |
| nx_ip_driver_status    | Status för slut för ande. Om driv rutinen inte kan koppla det angivna gränssnittet till IP-instansen, returnerar den en fel status som inte är noll. |

### <a name="get-link-status"></a>Hämta länk status  

Programmet kan fråga nätverks gränssnittets länk status med hjälp av tjänsten NetX service  ***nx_ip_interface_status_check*** för alla gränssnitt på värden. Se kapitel 4, "Beskrivning av NetX-tjänster" på sidan 107 för mer information om dessa tjänster.

Länkens status finns i fältet *nx_interface_link_up* i NX_INTERFACE-strukturen som *nx_ip_driver_interface* visaren pekar på. Följande NX_IP_DRIVERs medlemmar används för begäran om länk status.

| NX_IP_DRIVER medlem     | Innebörd                                                                                                      |
|-------------------------|--------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_STATUS                                                                                           |
| nx_ip_driver_ptr        | Pekare till IP-instans                                                                                       |
| nx_ip_driver_return_ptr | Pekar till målet för att placera statusen.                                                              |
| nx_ip_driver_interface  | Pekare till gränssnitts instansen                                                                            |
| nx_ip_driver_status     | Status för slut för ande. Om driv rutinen inte kan hämta en angiven status returneras en fel status som inte är noll. |
|                         |                                                                                                              |

> [!NOTE]
> ***nx_ip_status_check** är fortfarande tillgängligt för att kontrol lera status för det primära gränssnittet. Programutvecklare uppmanas dock att använda den gränssnitts specifika tjänsten **nx_ip_interface_status_check.***

### <a name="get-link-speed"></a>Hämta länk hastighet  

Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen lagrar länkens linje hastighet på den angivna destinationen. Följande NX_IP_DRIVER-medlemmar används för länk linjens hastighets förfrågan.

| NX_IP_DRIVER medlem     | Innebörd |
|-------------------------|---------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_SPEED |
| nx_ip_driver_ptr        | Pekare till IP-instans |
| nx_ip_driver_return_ptr | Pekare till målet för att placera linje hastigheten |
| nx_ip_driver_interface  | Pekare till gränssnitts instansen |
| nx_ip_driver_status     | Status för slut för ande. Om driv rutinen inte kan hämta hastighets information returneras en fel status som inte är noll.
 |


> [!NOTE]
> *Den här begäran används inte internt av NetX så dess implementering är valfri.*

### <a name="get-duplex-type"></a>Hämta duplex-typ  

Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen lagrar länkens duplex-typ på det angivna målet. Följande NX_IP_DRIVER-medlemmar används för begäran om duplex-typ.

| NX_IP_DRIVER medlem     | Innebörd |
|-------------------------|-----------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_DUPLEX_TYPE |
| nx_ip_driver_ptr        | Pekare till IP-instans |
| nx_ip_driver_return_ptr | Pekare till målet för att placera duplex-typen |
| nx_ip_driver_interface  | Pekare till gränssnitts instansen |
| nx_ip_driver_status     | Status för slut för ande. Om driv rutinen inte kan hämta information om duplex, returnerar den en fel status som inte är noll.
 |


> [!NOTE]
> *Den här begäran används inte internt av NetX så dess implementering är valfri.*

### <a name="get-error-count"></a>Hämta fel antal  

Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen lagrar länkens fel antal på den angivna destinationen. För att stödja den här funktionen måste driv rutinen spåra åtgärds fel. Följande NX_IP_DRIVER-medlemmar används för begäran om länk fel räkning.

| NX_IP_DRIVER medlem     | Innebörd                                                                                                  |
|-------------------------|----------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_ERROR_COUNT                                                                                  |
| nx_ip_driver_ptr        | Pekare till IP-instans                                                                                   |
| nx_ip_driver_return_ptr | Pekare till målet för att placera antalet fel                                                      |
| nx_ip_driver_interface  | Pekare till gränssnitts instansen                                                                        |
| nx_ip_driver_status     | Status för slut för ande. Om driv rutinen inte kan hämta antalet fel, returnerar den en fel status som inte är noll. |


> [!NOTE]
> *Den här begäran används inte internt av NetX så dess implementering är valfri.*

### <a name="get-receive-packet-count"></a>Hämta antal mottagna paket  

Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen lagrar länkens antal mottagna paket på det angivna målet. För att stödja den här funktionen måste driv rutinen hålla koll på antalet mottagna paket. Följande NX_IP_DRIVERs medlemmar används för begäran om att räkna antalet mottagna paket.

| NX_IP_DRIVER medlem     | Innebörd                                                                                                    |
|-------------------------|------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_RX_COUNT                                                                                       |
| nx_ip_driver_ptr        | Pekare till IP-instans                                                                                     |
| nx_ip_driver_return_ptr | Pekare till målet för att placera antalet mottagna paket                                               |
| nx_ip_driver_interface  | Pekare till det fysiska nätverks gränssnittet                                                                  |
| nx_ip_driver_status     | Status för slut för ande. Om driv rutinen inte kan få mottagnings antal, returnerar den en fel status som inte är noll. |


> [!NOTE]
> *Den här begäran används inte internt av NetX så dess implementering är valfri.*

### <a name="get-transmit-packet-count"></a>Hämta antal sändnings paket  

Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen lagrar länkens antal överförings paket på den angivna destinationen. För att stödja den här funktionen måste driv rutinen hålla koll på varje paket som skickas till varje gränssnitt. Följande NX_IP_DRIVER-medlemmar används för begäran om antal länkar för att skicka paket.

| NX_IP_DRIVER medlem     | Innebörd                                                                                                     |
|-------------------------|-------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_TX_COUNT                                                                                        |
| nx_ip_driver_ptr        | Pekare till IP-instans                                                                                      |
| nx_ip_driver_return_ptr | Pekare till målet för att placera antalet överförings paket                                               |
| nx_ip_driver_interface  | Pekare till gränssnitts instansen                                                                           |
| nx_ip_driver_status     | Status för slut för ande. Om driv rutinen inte kan hämta antal överföringar returneras en fel status som inte är noll. |


> [!NOTE]
> *Den här begäran används inte internt av NetX så dess implementering är valfri.*

### <a name="get-allocation-errors"></a>Hämta tilldelnings fel  

Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen lagrar länkens antal allokeringsfel tilldelnings fel på den angivna destinationen. Följande NX_IP_DRIVERs medlemmar används för begäran om tilldelning av länk tilldelnings fel.

| **NX_IP_DRIVER medlem** | **Innebörd** |
| --- | ---|
| nx_ip_driver_command | NX_LINK_GET_ALLOC_ERRORS |
| nx_ip_driver_ptr | Pekare till IP-instans |

| NX_IP_DRIVER medlem     | Innebörd                                                                                                        |
|-------------------------|----------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_return_ptr | Pekare till målet för att placera tilldelnings fel antalet                                                 |
| nx_ip_driver_interface  | Pekare till gränssnitts instansen                                                                              |
| nx_ip_driver_status     | Status för slut för ande. Om driv rutinen inte kan hämta allokeringsfel, returnerar den en fel status som inte är noll. |


*Den här begäran används inte internt av NetX så dess implementering är valfri.*

### <a name="driver-deferred-processing"></a>Driv rutin uppskjuten bearbetning  

Den här begäran görs från IP-hjälpens tråd som svar på den driv rutin som anropar _ ***nx_ip_driver_deferred_processing*** rutinen från en överförings-eller mottagnings-ISR. Detta gör att driv rutinen ISR kan skjuta upp paket mottagningen och skicka bearbetningen till IP-hjälpen och därmed minska mängden att bearbeta i ISR. *Nx_interface_additional_link_info* fältet i NX_INTERFACE-strukturen som anges av *nx_ip_driver_interface* kan användas av driv rutinen för att lagra information om den uppskjutna bearbetnings händelsen från tråd kontexten för IP-hjälp. Följande NX_IP_DRIVERs medlemmar används för den uppskjutna bearbetnings händelsen.

**NX_IP_DRIVER**

| medlem                 | Innebörd                           |
|------------------------|-----------------------------------|
| nx_ip_driver_command   | NX_LINK_DEFERRED_PROCESSING       |
| nx_ip_driver_ptr       | Pekare till IP-instans            |
| nx_ip_driver_interface | Pekare till gränssnitts instansen |


### <a name="user-commands"></a>Användar kommandon  

Den här begäran görs inifrån den ***nx_ip_driver_direct_command*** tjänsten. Driv rutinen bearbetar programspecifika användar kommandon. Följande NX_IP_DRIVER-medlemmar används för begäran om användar kommando.

| NX_IP_DRIVER medlem     | Innebörd                                                                                                        |
|-------------------------|----------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_USER_COMMAND                                                                                           |
| nx_ip_driver_ptr        | Pekare till IP-instans                                                                                         |
| nx_ip_driver_return_ptr | Användardefinierad                                                                                                   |
| nx_ip_driver_interface  | Pekare till gränssnitts instansen                                                                              |
| nx_ip_driver_status     | Status för slut för ande. Om driv rutinen inte kan köra användar kommandon returnerar den en fel status som inte är noll. |


*Den här begäran används inte internt av NetX så dess implementering är valfri.*

### <a name="unimplemented-commands"></a>Ej implementerade kommandon  

Kommandona som inte implementeras av nätverks driv rutinen måste ha värdet NX_UNHANDLED_COMMAND i fältet retur status.

## <a name="driver-output"></a>Driv rutins utdata  

Alla tidigare nämnda paket överförings begär Anden kräver en output-funktion som implementeras i driv rutinen. En speciell överförings logik är maskin varu information, men den består vanligt vis av att kontrol lera maskin varu kapaciteten för att skicka paketet omedelbart. Om möjligt läses paketets nytto Last (och ytterligare nytto laster i paket kedjan) in i en eller flera buffertar för maskin varu överföring och en överförings åtgärd initieras. Om paketet inte ryms i tillgängliga överföringsbuffert, ska paketet placeras i kö och skickas när överförings buffertarna blir tillgängliga.

Den rekommenderade överförings kön är en länkad lista med alla sidhuvuden och slut punkterna. Nya paket läggs till i slutet av kön och behåller det äldsta paketet längst fram. Fältet *nx_packet_queue_next* används som paketets nästa länk i kön. Driv rutinen definierar huvud-och slut punkterna i överförings kön.

*Eftersom den här kön nås från tråden och avbryter delar av driv rutinen måste avbrotts skyddet placeras runt köns manipulering.*

De flesta fysiska maskin varu implementeringar genererar ett avbrott vid slut för ande av paket överföring.
När driv rutinen tar emot ett sådant avbrott, frigör den vanligen de resurser som är associerade med paketet som skickas. Om överförings logiken läser data direkt från NX_PACKET-bufferten bör driv rutinen använda tjänsten ***nx_packet_transmit_release*** för att frigöra paketet som associeras med överföringen slutförs tillbaka till den tillgängliga poolen. Därefter undersöker driv rutinen överförings kön för ytterligare paket som väntar på att skickas. Så många av de köade överförings paket som passar i de köade överförings-och maskin varu buffertarna placeras de i kö och läses in i buffertarna. Detta följs genom att en annan sändnings åtgärd initieras.

Så snart data i NX_PACKET har flyttats till sändnings-FIFO (eller om en driv rutin stöder zerocopy-åtgärd har data i NX_PACKET skickats) måste driv rutinen flytta nx_packet_prepend_ptr till början av IP-huvudet innan nx_packet_transmit_release anropas ***.*** Kom ihåg att justera *nx_packet_length* fältet enligt detta. Om en IP-ram består av flera paket måste endast huvudet i paket kedjan släppas.

## <a name="driver-input"></a>Driv rutins Indatatyp  

Vid mottagning av mottagna paket avbrott hämtar nätverks driv rutinen paketet från den fysiska maskin varan som tar emot buffertar och skapar ett giltigt NetX-paket. Genom att skapa ett giltigt NetX-paket kan du konfigurera lämpligt längd fält och kedja samman flera paket om det inkommande paketets storlek är större än en enda paket nytto Last. När den väl har skapats flyttas prepend_ptr efter huvudet på den fysiska nivån och mottagnings paketet skickas till NetX.

NetX förutsätter att IP-och ARP-huvudena är justerade efter en ULONG-gränser. NetX-drivrutinen måste därför kontrol lera denna justering. I Ethernet-miljöer görs detta genom att du startar Ethernet-huvudet två byte från paketets början. När *nx_packet_prepend_ptr* flyttas bortom Ethernet-huvudet är den underliggande IP-eller ARP-rubriken 4byte justerad.

Det finns flera tillgängliga paket funktioner i NetX. Om det mottagna paketet är ett ARP-paket anropas _* **nx_arp_packet_deferred_receive**_ . Om det mottagna paketet är ett RARP-paket anropas _ _*_nx_rarp_packet_deferred_receive_*_ . Det finns flera alternativ för att hantera inkommande IP-paket. För den snabbaste hanteringen av IP-paket, anropas _ _*_nx_ip_packet_receive_*_ . Den här metoden har minst extra kostnader men kräver mer bearbetning i driv Rutinens tjänst hanterare för mottagnings avbrott (ISR). För minimal ISR-bearbetning är _ @*_nx_ip_packet_deferred_receive_** anropas.

När det nya mottagnings paketet har skapats korrekt är den fysiska maskin varans mottagningsbuffertar installations program för att ta emot mer data. Detta kan kräva att NetX-paket allokeras och att du placerar nytto Last adressen i bufferten för maskin vara, eller så kan det bara vara ett belopp att ändra en inställning i bufferten för maskin vara. För att minimera överskridnings möjligheterna är det viktigt att maskin varans mottagande buffertar har tillgängliga buffertar så snart som möjligt efter det att ett paket har mottagits.

*De första mottagningsbuffertar installeras när driv rutinen initieras.*

### <a name="deferred-receive-packet-handling"></a>Uppskjuten mottagning av paket hantering  

Driv rutinen kan skjuta upp mottagning av paket bearbetning till NetX IP-programtråden. För vissa program kan detta vara nödvändigt för att minimera ISR-bearbetning samt ignorerade paket. Om du vill använda uppskjuten paket hantering måste NetX-biblioteket först kompileras med ***NX_DRIVER_DEFERRED_PROCESSING** _ definierade. Detta lägger till den uppskjutna paket logiken i NetX IP-programtråden. Därefter måste driv rutinen anropa __nx_ip_packet_deferred_receive () för att ta emot ett data paket:*

```C
_nx_ip_packet_deferred_receive(ip_ptr, packet_ptr);
```

Funktionen för uppskjuten mottagning placerar det mottagna paketet som representeras av *packet_ptr* på en FIFO (länkad lista) och meddelar IP-hjälpens tråd. Efter körningen anropar IP-hjälpen upprepade gånger den uppskjutna hanterings funktionen för att bearbeta varje uppskjutet paket. Bearbetningen av uppskjuten hanterare tar vanligt vis bort paketets fysiska lager rubrik (vanligt vis Ethernet) och skickar den till någon av dessa NetX Receive-funktioner:  

***_nx_ip_packet_deferred_receive***  
***_nx_arp_packet_deferred_receive***  
***_nx_rarp_packet_deferred_receive*** 


## <a name="example-ram-ethernet-network-driver"></a>Exempel på RAM Ethernet-nätverks driv rutin  

NetX demonstrations systemet levereras med en liten RAM-baserad nätverks driv rutin som definieras i filen ***nx_ram_network_driver. c.***
Den här driv rutinen förutsätter att IP-instanserna är alla i samma nätverk och bara tilldelar virtuella maskin varu adresser (MAC-adresser) till varje enhets instans när de skapas. Den här filen ger ett enkelt exempel på grundläggande strukturen för NetX fysiska nätverks driv rutiner. Användare kan utveckla sina egna nätverks driv rutiner med hjälp av driv rutins ramverket som presenteras i det här exemplet.

Inmatnings funktionen för nätverks driv rutinen är ***_nx_ram_network_driver,** _ som skickas till IP-instansen skapa anrop. Post funktioner för ytterligare nätverks gränssnitt kan skickas till _*_nx_ip_interface_attachs_*_ tjänsten. När IP-instansen börjar köras anropas funktionen driv rutins post för att initiera och aktivera enheten (se ärendet _ *NX_LINK_INITIALIZE** och **NX_LINK_ENABLE**). När **NX_LINK_ENABLE** kommandot har utfärdats bör enheten vara redo att skicka och ta emot paket. 

IP-instansen överför nätverks paket via något av följande kommandon:

| ***NX_LINK_PACKET_SEND***    | Ett IP-paket överförs,                             |
| ------------------------------- | -------------------------------------------------------------- |
| ***NX_LINK_ARP_SEND***       | En ARP-begäran eller ett ARP-svars paket överförs,    |
| ***NX_LINK_ARP_RARP_SEND*** | En omvänd ARP-begäran eller ett svars paket överförs |

Vid bearbetning av dessa kommandon måste nätverks driv rutinen lägga lämpligt Ethernet-Rams huvud och sedan skicka den till den underliggande maskin varan för överföring. Under överförings processen har nätverks driv rutinen ensam ägarskap för paketets buffertzon. När data överförs (eller när data har kopierats till driv Rutinens interna överföringsbuffert) ansvarar nätverks driv rutinen för att frigöra paketets buffert genom att först flytta lägga-pekaren förbi Ethernet-huvudet till IP-huvudet (och justera Paketets längd efter detta) och sedan anropa tjänsten ***nx_packet_transmit_release*** för att frigöra paketet. Om du inte frigör paketet efter data överföringen kommer paket att läcka.

Nätverks enhetens driv rutin ansvarar också för hantering av inkommande data paket. I exempel på RAM-drivrutin bearbetas det mottagna paketet av funktionen ***_nx_ram_network_driver_receive***.

När enheten får en Ethernet-ram ansvarar driv rutinen för att lagra data i

NX_PACKET struktur. Observera att NetX antar att IP-huvudet börjar från den justerade adressen på 4 byte. Eftersom längden på Ethernet-huvudet är 14 byte måste driv rutinen lagra början av Ethernet-huvudet med en justerad adress på 2 byte för att garantera att IP-huvudet börjar med 4 byte-justerad adress.