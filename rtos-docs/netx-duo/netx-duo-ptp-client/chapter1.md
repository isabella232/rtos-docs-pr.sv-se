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
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a><span data-ttu-id="3f3bc-103">Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo PTP-klienten</span><span class="sxs-lookup"><span data-stu-id="3f3bc-103">Chapter 1 - Introduction to Azure RTOS NetX Duo PTP Client</span></span>

<span data-ttu-id="3f3bc-104">Azure återställnings tider NetX Duo PTP implementerar klient delen i precisions tids protokollet (PTP) version 2, IEEE 1588-2008.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-104">The Azure RTOS NetX Duo PTP implements the client part of the Precision Time Protocol (PTP) version 2, IEEE 1588-2008.</span></span> <span data-ttu-id="3f3bc-105">Den används för att synkronisera klockor mellan MCU i det lokala nätverket genom att kommunicera varandra via IPv4-eller IPv6-multicast-paket.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-105">It is used to synchronize clocks among MCUs on the local network by communicating each other via IPv4 or IPv6 multicast packets.</span></span>

## <a name="netx-duo-ptp-client-setup"></a><span data-ttu-id="3f3bc-106">Installation av NetX Duo PTP-klient</span><span class="sxs-lookup"><span data-stu-id="3f3bc-106">NetX Duo PTP Client Setup</span></span>

<span data-ttu-id="3f3bc-107">För att fungera korrekt kräver PTP-klientprogrammet att en NetX Duo-instans redan har skapats.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-107">In order to function properly, the PTP client package requires that a NetX Duo IP instance has already been created.</span></span>

<span data-ttu-id="3f3bc-108">Som standard ansluter PTP-klienten till IPv4 multicast-gruppen.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-108">By default, the PTP client joins IPv4 multicast group.</span></span> <span data-ttu-id="3f3bc-109">För att kunna köra PTP-klienten i ett IPv6-nätverk `NX_ENABLE_IPV6_MULTICAST` måste du definiera det när du skapar netx Duo-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-109">In order to run the PTP client on an IPv6 network, `NX_ENABLE_IPV6_MULTICAST` must be defined when building NetX Duo library.</span></span>

<span data-ttu-id="3f3bc-110">När du skapar PTP-klienten måste programmet tillhandahålla en callback-funktion för att hantera tidsstämplar för inkommande och utgående paket.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-110">When creating the PTP client, the application must provide a callback function to handle timestamps of incoming and outgoing packets.</span></span> <span data-ttu-id="3f3bc-111">För att uppnå hög upplösning rekommenderar vi att program genererar tidsstämplar med en timer med hög upplösning.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-111">To achieve high resolution, we recommend applications to generate timestamps using a high resolution timer.</span></span> <span data-ttu-id="3f3bc-112">För att köra PTP på simulatorn tillhandahålls en programvarubaserad implementering `nx_ptp_client_soft_clock_callback` .</span><span class="sxs-lookup"><span data-stu-id="3f3bc-112">To run the PTP on simulator, a software-based implementation `nx_ptp_client_soft_clock_callback` is provided.</span></span>

<span data-ttu-id="3f3bc-113">PTP-klienten kräver en modempool för överföring av PTP-meddelanden.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-113">The PTP client requires a packet pool for transmitting PTP messages.</span></span> <span data-ttu-id="3f3bc-114">Nytto Last storleken för Packet-poolen får inte vara mindre än `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE` , vilket är 108 byte för IPv4 och 128 byte om IPv6 är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-114">The payload size of packet pool must be no less than `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE`, which is 108 bytes for IPv4, and 128 bytes if IPv6 is enabled.</span></span>

<span data-ttu-id="3f3bc-115">När du har skapat PTP-klienten kan programmet starta PTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-115">After creating the PTP Client, the application can start the PTP client.</span></span> <span data-ttu-id="3f3bc-116">Synkroniseringen görs i PTP-hjälpens tråd.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-116">The synchronization is done in the PTP helper thread.</span></span> <span data-ttu-id="3f3bc-117">En funktion för motringning av händelse kan anges.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-117">An event callback function can be specified.</span></span> <span data-ttu-id="3f3bc-118">Den kommer att anropas när någon av följande händelser inträffar.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-118">It will be invoked when any one of the following events happen.</span></span>
* <span data-ttu-id="3f3bc-119">Ett huvud har valts.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-119">A master is selected;</span></span> 
* <span data-ttu-id="3f3bc-120">Tiden är kalibrerad.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-120">The time is calibrated.</span></span>
* <span data-ttu-id="3f3bc-121">En huvud tids gräns.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-121">A master times out.</span></span>

## <a name="netx-duo-ptp-client-messages"></a><span data-ttu-id="3f3bc-122">NetX Duo PTP-klient meddelanden</span><span class="sxs-lookup"><span data-stu-id="3f3bc-122">NetX Duo PTP Client Messages</span></span>

<span data-ttu-id="3f3bc-123">NetX Duo PTP-klienten implementerar endast svars funktionen för begäran.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-123">The NetX Duo PTP client implements the delay request-response mechanism only.</span></span> <span data-ttu-id="3f3bc-124">PTP-klienten öppnar två UDP-portar.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-124">The PTP client  opens two UDP ports.</span></span> <span data-ttu-id="3f3bc-125">*319* för **händelse** meddelande och *320* för **Allmänt** meddelande.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-125">*319* for **event** message and *320* for **general** message.</span></span> <span data-ttu-id="3f3bc-126">Det finns fem typer av meddelande för den här mekanismen.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-126">There are five types of message for this mechanism.</span></span>

* <span data-ttu-id="3f3bc-127">**Meddela**.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-127">**Announce**.</span></span> <span data-ttu-id="3f3bc-128">Detta är ett händelse meddelande.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-128">This is an event message.</span></span> <span data-ttu-id="3f3bc-129">Den används för val av huvud klocka.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-129">It is used for master clock selection.</span></span>
* <span data-ttu-id="3f3bc-130">**Synkronisera**. Detta är ett händelse meddelande.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-130">**Sync**. This is an event message.</span></span> <span data-ttu-id="3f3bc-131">Den används för att skicka ursprungs tids stämpling och beräkna Sök vägs fördröjningen från Master till client.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-131">It is used to send origin timestamp and calculate the path delay from master to client.</span></span>
* <span data-ttu-id="3f3bc-132">**Follow_Up**.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-132">**Follow_Up**.</span></span> <span data-ttu-id="3f3bc-133">Detta är ett allmänt meddelande.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-133">This is a general message.</span></span> <span data-ttu-id="3f3bc-134">Den är valfri och används för att korrigera ursprungs tids stämplingen i relaterat Sync-meddelande.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-134">It is optional and used to correct the origin timestamp in related Sync message.</span></span> <span data-ttu-id="3f3bc-135">Den skickas endast när den två steg biten i Sync-flaggan har angetts.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-135">It is sent only when the two step bit in Sync flag is set.</span></span>
* <span data-ttu-id="3f3bc-136">**Delay_Req**.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-136">**Delay_Req**.</span></span> <span data-ttu-id="3f3bc-137">Detta är ett händelse meddelande.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-137">This is an event message.</span></span> <span data-ttu-id="3f3bc-138">Den skickas från PTP-klienten för att beräkna Sök vägs fördröjningen från klienten till Master, vid mottagande av Delay_Resp.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-138">It is sent from PTP client to calculate the path delay from client to master, on receiving Delay_Resp.</span></span>
* <span data-ttu-id="3f3bc-139">**Delay_Resp**.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-139">**Delay_Resp**.</span></span> <span data-ttu-id="3f3bc-140">Detta är ett händelse meddelande.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-140">This is an event message.</span></span> <span data-ttu-id="3f3bc-141">Den skickas från huvud datorn till klienten för att beräkna Sök vägs fördröjningen från klienten till Master.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-141">It is sent from master to client to calculate the path delay from client to master.</span></span>

<span data-ttu-id="3f3bc-142">*Observera att algoritmen "bästa huvud klocka" inte har implementerats. Endast den första huvud klockan godkänns när PTP-klienten är i lyssnings tillstånd.*</span><span class="sxs-lookup"><span data-stu-id="3f3bc-142">*Note, "best master clock" algorithm is not implemented. Only the first master clock is accepted when the PTP client is in listening state.*</span></span>

## <a name="netx-duo-ptp-client-clock-callback"></a><span data-ttu-id="3f3bc-143">NetX Duo PTP-återanrop för klient klocka</span><span class="sxs-lookup"><span data-stu-id="3f3bc-143">NetX Duo PTP Client Clock Callback</span></span>
<span data-ttu-id="3f3bc-144">För att synkronisera klockan från huvud datorn behöver PTP-klienten en lokal klocka.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-144">To synchronize clock from master, PTP client needs a local clock.</span></span> <span data-ttu-id="3f3bc-145">En klock callback-funktion skickas till PTP-klienten när den skapas.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-145">A clock callback function is passed into PTP client during creation.</span></span> <span data-ttu-id="3f3bc-146">Formatet på rutinen för återanrop av klocka definieras nedan.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-146">The format of the clock callback routine is  defined below.</span></span>
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
<span data-ttu-id="3f3bc-147">Indataparametrarna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="3f3bc-147">The input parameters are defined as follows:</span></span>
* <span data-ttu-id="3f3bc-148">*client_ptr* pekar på PTP-klient.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-148">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="3f3bc-149">*åtgärden* anger återanrops åtgärden. giltiga värden definieras enligt listan nedan.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-149">*operation* specifies the callback operation, valid values are defined as shown in the list below.</span></span>
  * <span data-ttu-id="3f3bc-150">**NX_PTP_CLIENT_CLOCK_INIT** Initiera klockan.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-150">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="3f3bc-151">**NX_PTP_CLIENT_CLOCK_SET** Ange aktuell tidsstämpel som anges av `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="3f3bc-151">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="3f3bc-152">**NX_PTP_CLIENT_CLOCK_GET** Returnera aktuell tidstämpel till `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="3f3bc-152">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="3f3bc-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extrahera tidsstämpel från `packet_ptr` till `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="3f3bc-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="3f3bc-154">**NX_PTP_CLIENT_CLOCK_ADJUST** Justera den aktuella tidsstämpeln på mindre än *en* sekund.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-154">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="3f3bc-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Markera det `packet_ptr` som krävs för att meddela PTP-klienten tidsstämpeln när den överförs.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="3f3bc-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Uppdatera mjuk timer.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="3f3bc-157">Den kan ignoreras av maskin varu klockan.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-157">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="3f3bc-158">*time_ptr* pekar på tidsstämpel.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-158">*time_ptr* points to timestamp.</span></span>
* <span data-ttu-id="3f3bc-159">*packet_ptr* pekar på paket.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-159">*packet_ptr* points to packet.</span></span>
* <span data-ttu-id="3f3bc-160">*callback_data* pekar på täckande återanrops data.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-160">*callback_data* points to opaque callback data.</span></span>

<span data-ttu-id="3f3bc-161">Data typen NX_PTP_TIME definieras enligt följande.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-161">The NX_PTP_TIME data type is defined as follows.</span></span>
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

## <a name="netx-duo-ptp-client-event-callback"></a><span data-ttu-id="3f3bc-162">NetX Duo PTP-klient, händelse återanrop</span><span class="sxs-lookup"><span data-stu-id="3f3bc-162">NetX Duo PTP Client Event Callback</span></span>
<span data-ttu-id="3f3bc-163">Funktionen motringning i händelse kan konfigureras för att meddela programmet om status för PTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-163">The event callback function can be setup to notify application the state of PTP client.</span></span> <span data-ttu-id="3f3bc-164">Formatet på rutinen för händelse återanrop definieras som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-164">The format of the event callback routine is defined as shown below.</span></span>
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
<span data-ttu-id="3f3bc-165">Indataparametrarna är.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-165">The input parameters are.</span></span>
* <span data-ttu-id="3f3bc-166">*client_ptr* pekar på PTP-klient.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-166">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="3f3bc-167">*händelse* anger återanrops händelsen, giltiga värden definieras som:</span><span class="sxs-lookup"><span data-stu-id="3f3bc-167">*event* specifies the callback event, valid values are defined as:</span></span>
  * <span data-ttu-id="3f3bc-168">**NX_PTP_CLIENT_EVENT_MASTER** En huvud klocka har valts.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-168">**NX_PTP_CLIENT_EVENT_MASTER** A master clock is selected.</span></span>
  * <span data-ttu-id="3f3bc-169">**NX_PTP_CLIENT_EVENT_SYNC** PTP-klienten är kalibrerad.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-169">**NX_PTP_CLIENT_EVENT_SYNC** PTP client is calibrated.</span></span>
  * <span data-ttu-id="3f3bc-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** Huvud klockan är timeout.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** Master clock is timeout.</span></span>
* <span data-ttu-id="3f3bc-171">*event_data* anger data som rör händelsen.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-171">*event_data* specifies the data related to event.</span></span> <span data-ttu-id="3f3bc-172">När händelsen är **NX_PTP_CLIENT_EVENT_MASTER**, event_data pekar på `NX_PTP_CLIENT_MASTER` instans.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-172">When event is **NX_PTP_CLIENT_EVENT_MASTER**, event_data points to `NX_PTP_CLIENT_MASTER` instance.</span></span> <span data-ttu-id="3f3bc-173">När händelsen är **NX_PTP_CLIENT_EVENT_SYNC** hänvisar händelse data till `NX_PTP_CLIENT_SYNC` instans.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-173">When event is **NX_PTP_CLIENT_EVENT_SYNC**, event data points to `NX_PTP_CLIENT_SYNC` instance.</span></span>

## <a name="netx-duo-ptp-client-communication"></a><span data-ttu-id="3f3bc-174">NetX Duo PTP-klient kommunikation</span><span class="sxs-lookup"><span data-stu-id="3f3bc-174">NetX Duo PTP Client Communication</span></span>
<span data-ttu-id="3f3bc-175">Som tidigare nämnts stöder NetX Duo PTP-klienten endast fördröjd begäran om svars funktion.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-175">As mentioned previously, NetX Duo PTP client only supports delay request-response mechanism.</span></span> <span data-ttu-id="3f3bc-176">Den här mekanismen mäter medelvärdet för sökvägen mellan klienten och huvud klockan enligt nedan:</span><span class="sxs-lookup"><span data-stu-id="3f3bc-176">This mechanism measures the mean path delay between the client and the master clock as below:</span></span>
1. <span data-ttu-id="3f3bc-177">Klienten tar *emot* meddelande meddelande från huvud servern och väljer den som bästa huvud server.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-177">Client receives *Announce* message from master and select it as best master.</span></span>
1. <span data-ttu-id="3f3bc-178">Klienten tar emot ett *Sync* -meddelande från huvud servern.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-178">Client receives *Sync* message from master.</span></span> <span data-ttu-id="3f3bc-179">Tidsstämpeln *T1* är den ursprungliga tidstämpeln i det här meddelandet.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-179">The timestamp *t1* is the origin timestamp in this message.</span></span> <span data-ttu-id="3f3bc-180">Tidsstämpeln *T2* läses från lokal klocka när det här meddelandet tas emot.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-180">The timestamp *t2* is read from local clock when this message is received.</span></span>
1. <span data-ttu-id="3f3bc-181">Klienten tar emot *Follow_Up* meddelande från huvud servern.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-181">Client receives *Follow_Up* message from master.</span></span> <span data-ttu-id="3f3bc-182">Det här meddelandet är valfritt och endast giltigt när två steg i *Sync* -flaggan har angetts.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-182">This message is optional and valid only when two step in *Sync* flag is set.</span></span> <span data-ttu-id="3f3bc-183">Sedan uppdateras tidsstämpeln *T1* till ursprungs-tidsstämpeln i det här meddelandet.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-183">Then the timestamp *t1* is updated to the origin timestamp in this message.</span></span>
1. <span data-ttu-id="3f3bc-184">Klienten skickar *Delay_Req* meddelande till huvud servern.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-184">Client sends *Delay_Req* message to master.</span></span> <span data-ttu-id="3f3bc-185">Tidsstämpelns *T3* läses från lokal klocka när meddelandet skickas.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-185">The timestamp *t3* is read from local clock when the message is transmitted.</span></span>
1. <span data-ttu-id="3f3bc-186">Klienten tar emot *Delay_Resp* meddelande från huvud servern.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-186">Client receives *Delay_Resp* message from master.</span></span> <span data-ttu-id="3f3bc-187">Tidsstämpeln *T4* är Receive Timestamp i det här meddelandet.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-187">The timestamp *t4* is the receive timestamp in this message.</span></span>

<span data-ttu-id="3f3bc-188">Genomsnitts Sök vägens fördröjning beräknas enligt nedan.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-188">The mean path delay is computed as shown below.</span></span>
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
<span data-ttu-id="3f3bc-189">Offset från Master beräknas enligt nedan.</span><span class="sxs-lookup"><span data-stu-id="3f3bc-189">The offset from master is computed as shown below.</span></span>
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> <span data-ttu-id="3f3bc-190">\***CorrectionField** _ ignoreras under calculation._</span><span class="sxs-lookup"><span data-stu-id="3f3bc-190">\*The \***correctionField** _ is ignored during the calculation._</span></span>