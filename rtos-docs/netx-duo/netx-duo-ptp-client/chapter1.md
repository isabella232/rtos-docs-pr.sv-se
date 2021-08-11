---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo PTP-klient
description: Det här kapitlet innehåller en introduktion till Azure RTOS NetX Duo PTP Client.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf7210529121c8e49ff3cabbb7c673288b803f24760096396f32f33d4a9fb7e6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798052"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo PTP-klient

Den Azure RTOS NetX Duo PTP implementerar klientdelen av PRECISION Time Protocol (PTP) version 2, IEEE 1588-2008. Den används för att synkronisera klockor mellan MPU:er i det lokala nätverket genom att kommunicera med varandra via IPv4- eller IPv6-multicast-paket.

## <a name="netx-duo-ptp-client-setup"></a>NetX Duo PTP-klientinstallation

För att fungera korrekt kräver PTP-klientpaketet att en NetX Duo IP-instans redan har skapats.

Som standard ansluter PTP-klienten till IPv4-multicast-gruppen. För att kunna köra PTP-klienten i ett IPv6-nätverk måste `NX_ENABLE_IPV6_MULTICAST` definieras när netX Duo-biblioteket byggs.

När du skapar PTP-klienten måste programmet tillhandahålla en återanropsfunktion för att hantera tidsstämplar för inkommande och utgående paket. För att uppnå hög upplösning rekommenderar vi att program genererar tidsstämplar med en timer med hög upplösning. Om du vill köra PTP på simulatorn tillhandahålls en `nx_ptp_client_soft_clock_callback` programvarubaserad implementering.

PTP-klienten kräver en paketpool för överföring av PTP-meddelanden. Nyttolaststorleken för paketpoolen får inte vara mindre än , vilket är `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE` 108 byte för IPv4 och 128 byte om IPv6 är aktiverat.

När du har skapat PTP-klienten kan programmet starta PTP-klienten. Synkroniseringen görs i PTP-hjälptråden. En funktion för återanrop av händelser kan anges. Den anropas när någon av följande händelser inträffar.
* En huvudhanterare har valts. 
* Tiden kalibreras.
* En huvudström tar för många gånger slut.

## <a name="netx-duo-ptp-client-messages"></a>NetX Duo PTP-klientmeddelanden

NetX Duo PTP-klienten implementerar endast mekanismen för fördröjning av begäran/svar. PTP-klienten öppnar två UDP-portar. *319* för **händelsemeddelande** och *320* för **allmänt** meddelande. Det finns fem typer av meddelanden för den här mekanismen.

* **Meddela**. Det här är ett händelsemeddelande. Den används för val av huvudklocka.
* **Synkronisera**. Det här är ett händelsemeddelande. Den används för att skicka ursprungsstämpel och beräkna sökvägsfördröjningen från huvud till klient.
* **Follow_Up**. Det här är ett allmänt meddelande. Det är valfritt och används för att korrigera ursprungsstämpeln i det relaterade synkroniseringsmeddelandet. Det skickas bara när tvåstegsbiten i Sync-flaggan har angetts.
* **Delay_Req**. Det här är ett händelsemeddelande. Den skickas från PTP-klienten för att beräkna sökvägsfördröjningen från klienten till huvuddatorn när den tar emot Delay_Resp.
* **Delay_Resp**. Det här är ett händelsemeddelande. Den skickas från huvudklienten till klienten för att beräkna sökvägsfördröjningen från klienten till huvuddatorn.

*Observera att algoritmen "bästa huvudklocka" inte har implementerats. Endast den första huvudklockan accepteras när PTP-klienten är i lyssnande tillstånd.*

## <a name="netx-duo-ptp-client-clock-callback"></a>Motringning för NetX Duo PTP-klientklocka
För att synkronisera klockan från huvuddatorn behöver PTP-klienten en lokal klocka. En klockanropsfunktion skickas till PTP-klienten när den skapas. Formatet för klockanropsrutinen definieras nedan.
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
Indataparametrarna definieras på följande sätt:
* *client_ptr* pekar på PTP-klienten.
* *åtgärden* anger återanropsåtgärden, giltiga värden definieras enligt listan nedan.
  * **NX_PTP_CLIENT_CLOCK_INIT** Initiera klockan.
  * **NX_PTP_CLIENT_CLOCK_SET** Ange den aktuella tidsstämpeln som anges av `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_GET** Returnera den aktuella tidsstämpeln till `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extrahera tidsstämpeln `packet_ptr` från till `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_ADJUST** Justera den aktuella tidsstämpeln mindre än *1* sekund.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Markera som `packet_ptr` kräver för att meddela PTP-klienten tidsstämpeln när den skickas.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Uppdatera mjuk timer. Det kan ignoreras av maskinvaruklockan.
* *time_ptr* pekar på tidsstämpeln.
* *packet_ptr* pekar på paketet.
* *callback_data* pekar på täckande återanropsdata.

Den NX_PTP_TIME datatypen definieras på följande sätt.
```C
typedef struct NX_PTP_TIME_STRUCT
{
    /* The MSB of the number of seconds */
    LONG  second_high;

    /* The LSB of the number of seconds */
    ULONG second_low;

    /* The number of nanoseconds */
    LONG  nanosecond;
} NX_PTP_TIME;
```

## <a name="netx-duo-ptp-client-event-callback"></a>Återanrop av NetX Duo PTP-klienthändelse
Funktionen för återanrop av händelser kan konfigureras för att meddela programmet om PTP-klientens tillstånd. Formatet för händelseanropsrutinen definieras enligt nedan.
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
Indataparametrarna är .
* *client_ptr* pekar på PTP-klienten.
* *-händelsen* anger återanropshändelsen, giltiga värden definieras som:
  * **NX_PTP_CLIENT_EVENT_MASTER** En huvudklocka har valts.
  * **NX_PTP_CLIENT_EVENT_SYNC** PTP-klienten kalibreras.
  * **NX_PTP_CLIENT_EVENT_TIMEOUT** Huvudklockan är timeout.
* *event_data* anger de data som är relaterade till händelsen. När händelsen är **NX_PTP_CLIENT_EVENT_MASTER** pekar event_data på `NX_PTP_CLIENT_MASTER` instansen. När händelsen **NX_PTP_CLIENT_EVENT_SYNC** pekar händelsedata på `NX_PTP_CLIENT_SYNC` instansen.

## <a name="netx-duo-ptp-client-communication"></a>NetX Duo PTP-klientkommunikation
Som tidigare nämnts stöder NetX Duo PTP-klienten endast mekanism för att fördröja begäran/svar. Den här mekanismen mäter fördröjningen av medelvägen mellan klienten och huvudklockan enligt nedan:
1. Klienten får *meddelandet Meddela* från huvuddatorn och väljer det som bästa huvud.
1. Klienten får *synkroniseringsmeddelandet* från huvuddatorn. Tidsstämpeln *t1 är* ursprungstidsstämpeln i det här meddelandet. Tidsstämpeln *t2* läses från den lokala klockan när det här meddelandet tas emot.
1. Klienten får *Follow_Up* meddelande från huvuddatorn. Det här meddelandet är valfritt och giltigt endast när två steg i *sync-flaggan* har angetts. Tidsstämpeln *t1 uppdateras* sedan till ursprungsstämpeln i det här meddelandet.
1. Klienten skickar *Delay_Req* till huvuddatorn. Tidsstämpeln *t3* läses från den lokala klockan när meddelandet skickas.
1. Klienten får *Delay_Resp* meddelande från huvuddatorn. Tidsstämpeln *t4 är* tidsstämpeln för mottagning i det här meddelandet.

Den genomsnittliga sökvägsfördröjningen beräknas enligt nedan.
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
Förskjutningen från huvudnoden beräknas enligt nedan.
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> ****correctionField** _ ignoreras under calculation._