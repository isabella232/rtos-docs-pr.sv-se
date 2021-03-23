---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo PTP-klienten
description: Det här kapitlet innehåller en introduktion till Azure återställnings tider NetX Duo PTP-klienten.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5beec64bd6d74e3bed06be15255d6bd4a940ba64
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825806"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo PTP-klienten

Azure återställnings tider NetX Duo PTP implementerar klient delen i precisions tids protokollet (PTP) version 2, IEEE 1588-2008. Den används för att synkronisera klockor mellan MCU i det lokala nätverket genom att kommunicera varandra via IPv4-eller IPv6-multicast-paket.

## <a name="netx-duo-ptp-client-setup"></a>Installation av NetX Duo PTP-klient

För att fungera korrekt kräver PTP-klientprogrammet att en NetX Duo-instans redan har skapats.

Som standard ansluter PTP-klienten till IPv4 multicast-gruppen. För att kunna köra PTP-klienten i ett IPv6-nätverk `NX_ENABLE_IPV6_MULTICAST` måste du definiera det när du skapar netx Duo-biblioteket.

När du skapar PTP-klienten måste programmet tillhandahålla en callback-funktion för att hantera tidsstämplar för inkommande och utgående paket. För att uppnå hög upplösning rekommenderar vi att program genererar tidsstämplar med en timer med hög upplösning. För att köra PTP på simulatorn tillhandahålls en programvarubaserad implementering `nx_ptp_client_soft_clock_callback` .

PTP-klienten kräver en modempool för överföring av PTP-meddelanden. Nytto Last storleken för Packet-poolen får inte vara mindre än `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE` , vilket är 108 byte för IPv4 och 128 byte om IPv6 är aktiverat.

När du har skapat PTP-klienten kan programmet starta PTP-klienten. Synkroniseringen görs i PTP-hjälpens tråd. En funktion för motringning av händelse kan anges. Den kommer att anropas när någon av följande händelser inträffar.
* Ett huvud har valts. 
* Tiden är kalibrerad.
* En huvud tids gräns.

## <a name="netx-duo-ptp-client-messages"></a>NetX Duo PTP-klient meddelanden

NetX Duo PTP-klienten implementerar endast svars funktionen för begäran. PTP-klienten öppnar två UDP-portar. *319* för **händelse** meddelande och *320* för **Allmänt** meddelande. Det finns fem typer av meddelande för den här mekanismen.

* **Meddela**. Detta är ett händelse meddelande. Den används för val av huvud klocka.
* **Synkronisera**. Detta är ett händelse meddelande. Den används för att skicka ursprungs tids stämpling och beräkna Sök vägs fördröjningen från Master till client.
* **Follow_Up**. Detta är ett allmänt meddelande. Den är valfri och används för att korrigera ursprungs tids stämplingen i relaterat Sync-meddelande. Den skickas endast när den två steg biten i Sync-flaggan har angetts.
* **Delay_Req**. Detta är ett händelse meddelande. Den skickas från PTP-klienten för att beräkna Sök vägs fördröjningen från klienten till Master, vid mottagande av Delay_Resp.
* **Delay_Resp**. Detta är ett händelse meddelande. Den skickas från huvud datorn till klienten för att beräkna Sök vägs fördröjningen från klienten till Master.

*Observera att algoritmen "bästa huvud klocka" inte har implementerats. Endast den första huvud klockan godkänns när PTP-klienten är i lyssnings tillstånd.*

## <a name="netx-duo-ptp-client-clock-callback"></a>NetX Duo PTP-återanrop för klient klocka
För att synkronisera klockan från huvud datorn behöver PTP-klienten en lokal klocka. En klock callback-funktion skickas till PTP-klienten när den skapas. Formatet på rutinen för återanrop av klocka definieras nedan.
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
Indataparametrarna definieras enligt följande:
* *client_ptr* pekar på PTP-klient.
* *åtgärden* anger återanrops åtgärden. giltiga värden definieras enligt listan nedan.
  * **NX_PTP_CLIENT_CLOCK_INIT** Initiera klockan.
  * **NX_PTP_CLIENT_CLOCK_SET** Ange aktuell tidsstämpel som anges av `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_GET** Returnera aktuell tidstämpel till `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extrahera tidsstämpel från `packet_ptr` till `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_ADJUST** Justera den aktuella tidsstämpeln på mindre än *en* sekund.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Markera det `packet_ptr` som krävs för att meddela PTP-klienten tidsstämpeln när den överförs.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Uppdatera mjuk timer. Den kan ignoreras av maskin varu klockan.
* *time_ptr* pekar på tidsstämpel.
* *packet_ptr* pekar på paket.
* *callback_data* pekar på täckande återanrops data.

Data typen NX_PTP_TIME definieras enligt följande.
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

## <a name="netx-duo-ptp-client-event-callback"></a>NetX Duo PTP-klient, händelse återanrop
Funktionen motringning i händelse kan konfigureras för att meddela programmet om status för PTP-klienten. Formatet på rutinen för händelse återanrop definieras som visas nedan.
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
Indataparametrarna är.
* *client_ptr* pekar på PTP-klient.
* *händelse* anger återanrops händelsen, giltiga värden definieras som:
  * **NX_PTP_CLIENT_EVENT_MASTER** En huvud klocka har valts.
  * **NX_PTP_CLIENT_EVENT_SYNC** PTP-klienten är kalibrerad.
  * **NX_PTP_CLIENT_EVENT_TIMEOUT** Huvud klockan är timeout.
* *event_data* anger data som rör händelsen. När händelsen är **NX_PTP_CLIENT_EVENT_MASTER**, event_data pekar på `NX_PTP_CLIENT_MASTER` instans. När händelsen är **NX_PTP_CLIENT_EVENT_SYNC** hänvisar händelse data till `NX_PTP_CLIENT_SYNC` instans.

## <a name="netx-duo-ptp-client-communication"></a>NetX Duo PTP-klient kommunikation
Som tidigare nämnts stöder NetX Duo PTP-klienten endast fördröjd begäran om svars funktion. Den här mekanismen mäter medelvärdet för sökvägen mellan klienten och huvud klockan enligt nedan:
1. Klienten tar *emot* meddelande meddelande från huvud servern och väljer den som bästa huvud server.
1. Klienten tar emot ett *Sync* -meddelande från huvud servern. Tidsstämpeln *T1* är den ursprungliga tidstämpeln i det här meddelandet. Tidsstämpeln *T2* läses från lokal klocka när det här meddelandet tas emot.
1. Klienten tar emot *Follow_Up* meddelande från huvud servern. Det här meddelandet är valfritt och endast giltigt när två steg i *Sync* -flaggan har angetts. Sedan uppdateras tidsstämpeln *T1* till ursprungs-tidsstämpeln i det här meddelandet.
1. Klienten skickar *Delay_Req* meddelande till huvud servern. Tidsstämpelns *T3* läses från lokal klocka när meddelandet skickas.
1. Klienten tar emot *Delay_Resp* meddelande från huvud servern. Tidsstämpeln *T4* är Receive Timestamp i det här meddelandet.

Genomsnitts Sök vägens fördröjning beräknas enligt nedan.
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
Offset från Master beräknas enligt nedan.
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> ***CorrectionField** _ ignoreras under calculation._