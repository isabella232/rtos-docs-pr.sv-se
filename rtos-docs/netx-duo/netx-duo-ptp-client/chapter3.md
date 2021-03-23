---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo PTP Client Services
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo PTP-klienttjänster i alfabetisk ordning.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b4cdeca81c157934e35a219cd5535ec38f2c0746
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825803"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a><span data-ttu-id="475ee-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo PTP Client Services</span><span class="sxs-lookup"><span data-stu-id="475ee-103">Chapter 3 - Description of Azure RTOS NetX Duo PTP Client Services</span></span>

<span data-ttu-id="475ee-104">Det här kapitlet innehåller en beskrivning av alla NetX Duo PTP-klienttjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="475ee-104">This chapter contains a description of all NetX Duo PTP client services (listed below) in alphabetical order.</span></span>

[!NOTE]
> <span data-ttu-id="475ee-105">*I avsnittet **returnera värden** i följande beskrivningar av API-funktioner påverkas inte värdena i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.*</span><span class="sxs-lookup"><span data-stu-id="475ee-105">*In the **Return Values** section in the following API function descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.*</span></span>

## <a name="nx_ptp_client_create"></a><span data-ttu-id="475ee-106">nx_ptp_client_create</span><span class="sxs-lookup"><span data-stu-id="475ee-106">nx_ptp_client_create</span></span>

<span data-ttu-id="475ee-107">Skapa en PTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="475ee-107">Create a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="475ee-108">Prototyp</span><span class="sxs-lookup"><span data-stu-id="475ee-108">Prototype</span></span>

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a><span data-ttu-id="475ee-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="475ee-109">Description</span></span>

<span data-ttu-id="475ee-110">Den här tjänsten skapar en instans av PTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="475ee-110">This service creates an instance of the PTP client.</span></span>

<span data-ttu-id="475ee-111">Observera att programmet först måste skapa en IP-instans och en modempool för att PTP-klienten ska kunna överföra paket.</span><span class="sxs-lookup"><span data-stu-id="475ee-111">Note that the  application must first create an IP instance and a packet pool for the PTP client to transmit packets.</span></span> <span data-ttu-id="475ee-112">För Packet-poolen kan programmet använda samma adresspool i IP-instansen. eller så kan den skapa en dedikerad modempool för PTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="475ee-112">For the packet pool, application may use the same packet pool in the IP instance; or it can create a dedicated packet pool for PTP client.</span></span>  <span data-ttu-id="475ee-113">Den dedikerade lagringspoolen har fördelen med att använda små paket (128 byte-paket om IPv6 används eller 108 byte för endast IPv4).</span><span class="sxs-lookup"><span data-stu-id="475ee-113">The dedicated packet pool approach has the advantage of using small packets (128 bytes packets if IPv6 is used, or 108 bytes for IPv4-only).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="475ee-114">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="475ee-114">Input Parameters</span></span>
* <span data-ttu-id="475ee-115">**client_ptr** Pekare till PTP-klient för att skapa</span><span class="sxs-lookup"><span data-stu-id="475ee-115">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="475ee-116">**ip_ptr** Pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="475ee-116">**ip_ptr** Pointer to IP instance</span></span>
* <span data-ttu-id="475ee-117">**interface_index** Index för PTP-nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="475ee-117">**interface_index** Index of PTP network interface</span></span>
* <span data-ttu-id="475ee-118">**packet_pool_ptr** Pekare till klient paketets pool</span><span class="sxs-lookup"><span data-stu-id="475ee-118">**packet_pool_ptr** Pointer to client packet pool</span></span>
* <span data-ttu-id="475ee-119">**thread_priority**  Prioritet för PTP-tråd</span><span class="sxs-lookup"><span data-stu-id="475ee-119">**thread_priority**  Priority of PTP thread</span></span>
* <span data-ttu-id="475ee-120">**thread_stack** Pekare till tråds tack</span><span class="sxs-lookup"><span data-stu-id="475ee-120">**thread_stack** Pointer to thread stack</span></span>
* <span data-ttu-id="475ee-121">**stack_size** Storlek på tråds tack</span><span class="sxs-lookup"><span data-stu-id="475ee-121">**stack_size** Size of thread stack</span></span>
* <span data-ttu-id="475ee-122">**clock_callback** Motanrop för PTP-klocka</span><span class="sxs-lookup"><span data-stu-id="475ee-122">**clock_callback** PTP clock callback</span></span>
* <span data-ttu-id="475ee-123">**clock_callback_data** Data för klock anrop</span><span class="sxs-lookup"><span data-stu-id="475ee-123">**clock_callback_data** Data for the clock callback</span></span>

### <a name="return-values"></a><span data-ttu-id="475ee-124">Retur värden</span><span class="sxs-lookup"><span data-stu-id="475ee-124">Return Values</span></span>
* <span data-ttu-id="475ee-125">**NX_SUCCESS** (0x00)-klienten har skapats</span><span class="sxs-lookup"><span data-stu-id="475ee-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="475ee-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** paketets nytto Last är för kort (0xD04)</span><span class="sxs-lookup"><span data-stu-id="475ee-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) Packet payload too small</span></span>
* <span data-ttu-id="475ee-127">**NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) Det gick inte att återanrop</span><span class="sxs-lookup"><span data-stu-id="475ee-127">**NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) Failure on clock callback</span></span>
* <span data-ttu-id="475ee-128">**status** Status för slut för ande av NetX Duo-och ThreadX service-anrop</span><span class="sxs-lookup"><span data-stu-id="475ee-128">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="475ee-129">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="475ee-129">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
* <span data-ttu-id="475ee-130">NX_INVALID_INTERFACE (0x4C) ogiltigt gränssnitt</span><span class="sxs-lookup"><span data-stu-id="475ee-130">NX_INVALID_INTERFACE (0x4C) Invalid interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="475ee-131">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="475ee-131">Allowed From</span></span>
<span data-ttu-id="475ee-132">Konversation</span><span class="sxs-lookup"><span data-stu-id="475ee-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="475ee-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="475ee-133">Example</span></span>
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a><span data-ttu-id="475ee-134">nx_ptp_client_delete</span><span class="sxs-lookup"><span data-stu-id="475ee-134">nx_ptp_client_delete</span></span>

<span data-ttu-id="475ee-135">Tar bort en PTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="475ee-135">Deletes a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="475ee-136">Prototyp</span><span class="sxs-lookup"><span data-stu-id="475ee-136">Prototype</span></span>

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="475ee-137">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="475ee-137">Description</span></span>

<span data-ttu-id="475ee-138">Den här tjänsten tar bort en instans av PTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="475ee-138">This service deletes an instance of the PTP client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="475ee-139">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="475ee-139">Input Parameters</span></span>
* <span data-ttu-id="475ee-140">**client_ptr** Pekare till PTP-klient att ta bort</span><span class="sxs-lookup"><span data-stu-id="475ee-140">**client_ptr** Pointer to PTP client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="475ee-141">Retur värden</span><span class="sxs-lookup"><span data-stu-id="475ee-141">Return Values</span></span>
* <span data-ttu-id="475ee-142">**NX_SUCCESS** (0X00) klienten har tagits bort</span><span class="sxs-lookup"><span data-stu-id="475ee-142">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
* <span data-ttu-id="475ee-143">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="475ee-143">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="475ee-144">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="475ee-144">Allowed From</span></span>
<span data-ttu-id="475ee-145">Konversation</span><span class="sxs-lookup"><span data-stu-id="475ee-145">Threads</span></span>

### <a name="example"></a><span data-ttu-id="475ee-146">Exempel</span><span class="sxs-lookup"><span data-stu-id="475ee-146">Example</span></span>
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a><span data-ttu-id="475ee-147">nx_ptp_client_master_info_get</span><span class="sxs-lookup"><span data-stu-id="475ee-147">nx_ptp_client_master_info_get</span></span>

<span data-ttu-id="475ee-148">Hämta information om huvud klock klocka.</span><span class="sxs-lookup"><span data-stu-id="475ee-148">Get master clock information.</span></span>

### <a name="prototype"></a><span data-ttu-id="475ee-149">Prototyp</span><span class="sxs-lookup"><span data-stu-id="475ee-149">Prototype</span></span>

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a><span data-ttu-id="475ee-150">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="475ee-150">Description</span></span>
<span data-ttu-id="475ee-151">Den här tjänsten hämtar information om huvud klockan.</span><span class="sxs-lookup"><span data-stu-id="475ee-151">This service gets information of master clock.</span></span> <span data-ttu-id="475ee-152">Master Control-blocket skickas till användar programmet via funktionen motringning av händelse.</span><span class="sxs-lookup"><span data-stu-id="475ee-152">The master control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="475ee-153">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="475ee-153">Input Parameters</span></span>
* <span data-ttu-id="475ee-154">**master_ptr** Pekare till PTP-huvudklocka</span><span class="sxs-lookup"><span data-stu-id="475ee-154">**master_ptr** Pointer to PTP master clock</span></span>
* <span data-ttu-id="475ee-155">**adress** Adress till huvud klockan</span><span class="sxs-lookup"><span data-stu-id="475ee-155">**address** Address of master clock</span></span>
* <span data-ttu-id="475ee-156">**port_identity** PTP-huvudport och identitet</span><span class="sxs-lookup"><span data-stu-id="475ee-156">**port_identity** PTP master port and identity</span></span>
* <span data-ttu-id="475ee-157">**port_identity_length** Längd på PTP-huvudporten och identiteten</span><span class="sxs-lookup"><span data-stu-id="475ee-157">**port_identity_length** Length of PTP master port and identity</span></span>
* <span data-ttu-id="475ee-158">**priority1** Priority1 of PTP Master Clock</span><span class="sxs-lookup"><span data-stu-id="475ee-158">**priority1** Priority1 of PTP master clock</span></span>
* <span data-ttu-id="475ee-159">**priority2** Priority2 of PTP Master Clock</span><span class="sxs-lookup"><span data-stu-id="475ee-159">**priority2** Priority2 of PTP master clock</span></span>
* <span data-ttu-id="475ee-160">**clock_class** Klass för PTP-huvudklocka</span><span class="sxs-lookup"><span data-stu-id="475ee-160">**clock_class** Class of PTP master clock</span></span>
* <span data-ttu-id="475ee-161">**clock_accuracy** Noggrannhet hos PTP-huvudklocka</span><span class="sxs-lookup"><span data-stu-id="475ee-161">**clock_accuracy** Accuracy of PTP master clock</span></span>
* <span data-ttu-id="475ee-162">**clock_variance** Varians hos PTP-huvudklocka</span><span class="sxs-lookup"><span data-stu-id="475ee-162">**clock_variance** Variance of PTP master clock</span></span>
* <span data-ttu-id="475ee-163">**grandmaster_identity** Identitet för Grandmaster-klocka</span><span class="sxs-lookup"><span data-stu-id="475ee-163">**grandmaster_identity** Identity of grandmaster clock</span></span>
* <span data-ttu-id="475ee-164">**grandmaster_identity_length** Längd på Grandmaster-identitet</span><span class="sxs-lookup"><span data-stu-id="475ee-164">**grandmaster_identity_length** Length of grandmaster Identity</span></span>
* <span data-ttu-id="475ee-165">**steps_removed** Steg borttagna från PTP-huvudet</span><span class="sxs-lookup"><span data-stu-id="475ee-165">**steps_removed** Steps removed from PTP header</span></span>
* <span data-ttu-id="475ee-166">**time_source** Källan för timern som används av Grandmaster-klockan</span><span class="sxs-lookup"><span data-stu-id="475ee-166">**time_source** The source of timer used by grandmaster clock</span></span>

### <a name="return-values"></a><span data-ttu-id="475ee-167">Retur värden</span><span class="sxs-lookup"><span data-stu-id="475ee-167">Return Values</span></span>
* <span data-ttu-id="475ee-168">**NX_SUCCESS** (0X00) Hämta huvud klock information</span><span class="sxs-lookup"><span data-stu-id="475ee-168">**NX_SUCCESS** (0x00) Get master clock information successfully</span></span>
* <span data-ttu-id="475ee-169">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="475ee-169">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="475ee-170">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="475ee-170">Allowed From</span></span>
<span data-ttu-id="475ee-171">Konversation</span><span class="sxs-lookup"><span data-stu-id="475ee-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="475ee-172">Exempel</span><span class="sxs-lookup"><span data-stu-id="475ee-172">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a><span data-ttu-id="475ee-173">nx_ptp_client_packet_timestamp_notify</span><span class="sxs-lookup"><span data-stu-id="475ee-173">nx_ptp_client_packet_timestamp_notify</span></span>

<span data-ttu-id="475ee-174">Meddela PTP-klientens tidsstämpel för paketet.</span><span class="sxs-lookup"><span data-stu-id="475ee-174">Notify PTP client the timestamp of the packet.</span></span>

### <a name="prototype"></a><span data-ttu-id="475ee-175">Prototyp</span><span class="sxs-lookup"><span data-stu-id="475ee-175">Prototype</span></span>

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a><span data-ttu-id="475ee-176">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="475ee-176">Description</span></span>
<span data-ttu-id="475ee-177">Den här tjänsten meddelar PTP-klienten att paketet överförs med tidsstämpel.</span><span class="sxs-lookup"><span data-stu-id="475ee-177">This service notifies the PTP client that packet is transmitted with timestamp.</span></span> <span data-ttu-id="475ee-178">Den här tjänsten är avsedd för nätverks driv rutin och anropas när paketet överförs.</span><span class="sxs-lookup"><span data-stu-id="475ee-178">This service is designed for network driver and invoked when the packet is transmitted.</span></span> <span data-ttu-id="475ee-179">Tidsstämpeln skapas vanligt vis av maskin vara.</span><span class="sxs-lookup"><span data-stu-id="475ee-179">The timestamp is usually generated by hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="475ee-180">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="475ee-180">Input Parameters</span></span>
* <span data-ttu-id="475ee-181">**client_ptr** Pekare till PTP-klient för att skapa</span><span class="sxs-lookup"><span data-stu-id="475ee-181">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="475ee-182">**packet_ptr** Pekare till PTP-paket som överförs</span><span class="sxs-lookup"><span data-stu-id="475ee-182">**packet_ptr** Pointer to PTP packet that is transmitted</span></span>
* <span data-ttu-id="475ee-183">**timestamp_ptr** Pekare till tidsstämpel för PTP-paket</span><span class="sxs-lookup"><span data-stu-id="475ee-183">**timestamp_ptr** Pointer to timestamp of PTP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="475ee-184">Retur värden</span><span class="sxs-lookup"><span data-stu-id="475ee-184">Return Values</span></span>
<span data-ttu-id="475ee-185">Inget</span><span class="sxs-lookup"><span data-stu-id="475ee-185">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="475ee-186">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="475ee-186">Allowed From</span></span>
<span data-ttu-id="475ee-187">Konversation</span><span class="sxs-lookup"><span data-stu-id="475ee-187">Threads</span></span>

### <a name="example"></a><span data-ttu-id="475ee-188">Exempel</span><span class="sxs-lookup"><span data-stu-id="475ee-188">Example</span></span>
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a><span data-ttu-id="475ee-189">nx_ptp_client_soft_clock_callback</span><span class="sxs-lookup"><span data-stu-id="475ee-189">nx_ptp_client_soft_clock_callback</span></span>

<span data-ttu-id="475ee-190">Program varu implementering av en PTP-klocka.</span><span class="sxs-lookup"><span data-stu-id="475ee-190">Software implementation of a PTP clock.</span></span>

### <a name="prototype"></a><span data-ttu-id="475ee-191">Prototyp</span><span class="sxs-lookup"><span data-stu-id="475ee-191">Prototype</span></span>

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a><span data-ttu-id="475ee-192">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="475ee-192">Description</span></span>
<span data-ttu-id="475ee-193">Denna motringning fungerar som en simulerad låg upplöst klock källa för PTP.</span><span class="sxs-lookup"><span data-stu-id="475ee-193">This callback function serves as a simulated low resolution clock source for PTP.</span></span> <span data-ttu-id="475ee-194">Den här rutinen tillhandahålls som en referens och kan inte användas för produktion.</span><span class="sxs-lookup"><span data-stu-id="475ee-194">This routine is provided as a reference and cannot be used for production.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="475ee-195">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="475ee-195">Input Parameters</span></span>
* <span data-ttu-id="475ee-196">**client_ptr** Pekare till PTP-klient för att skapa</span><span class="sxs-lookup"><span data-stu-id="475ee-196">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="475ee-197">**åtgärd** Återanrops åtgärd, giltiga värden definieras som:</span><span class="sxs-lookup"><span data-stu-id="475ee-197">**operation** Callback operation, valid values are defined as:</span></span>
  * <span data-ttu-id="475ee-198">**NX_PTP_CLIENT_CLOCK_INIT** Initiera klockan.</span><span class="sxs-lookup"><span data-stu-id="475ee-198">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="475ee-199">**NX_PTP_CLIENT_CLOCK_SET** Ange aktuell tidsstämpel som anges av `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="475ee-199">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="475ee-200">**NX_PTP_CLIENT_CLOCK_GET** Returnera aktuell tidstämpel till `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="475ee-200">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="475ee-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extrahera tidsstämpel från `packet_ptr` till `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="475ee-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="475ee-202">**NX_PTP_CLIENT_CLOCK_ADJUST** Justera den aktuella tidsstämpeln på mindre än *en* sekund.</span><span class="sxs-lookup"><span data-stu-id="475ee-202">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="475ee-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Markera det `packet_ptr` som krävs för att meddela PTP-klienten tidsstämpeln när den överförs.</span><span class="sxs-lookup"><span data-stu-id="475ee-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="475ee-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Uppdatera mjuk timer.</span><span class="sxs-lookup"><span data-stu-id="475ee-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="475ee-205">Den kan ignoreras av maskin varu klockan.</span><span class="sxs-lookup"><span data-stu-id="475ee-205">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="475ee-206">**time_ptr** Pekare till tidsstämpel.</span><span class="sxs-lookup"><span data-stu-id="475ee-206">**time_ptr** Pointer to timestamp.</span></span>
* <span data-ttu-id="475ee-207">**packet_ptr** Pekar mot paket.</span><span class="sxs-lookup"><span data-stu-id="475ee-207">**packet_ptr** Pointer to packet.</span></span>
* <span data-ttu-id="475ee-208">**callback_data** Pekare mot täckande återanrops data.</span><span class="sxs-lookup"><span data-stu-id="475ee-208">**callback_data** Pointer to opaque callback data.</span></span>

### <a name="return-values"></a><span data-ttu-id="475ee-209">Retur värden</span><span class="sxs-lookup"><span data-stu-id="475ee-209">Return Values</span></span>
* <span data-ttu-id="475ee-210">**NX_SUCCESS** (0x00) har åtgärd ATS</span><span class="sxs-lookup"><span data-stu-id="475ee-210">**NX_SUCCESS** (0x00) Operation successfully</span></span>
* <span data-ttu-id="475ee-211">**NX_PTP_PARAM_ERROR** (0XD03) ogiltig parameter</span><span class="sxs-lookup"><span data-stu-id="475ee-211">**NX_PTP_PARAM_ERROR** (0xD03) Invalid parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="475ee-212">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="475ee-212">Allowed From</span></span>
<span data-ttu-id="475ee-213">PTP, intern</span><span class="sxs-lookup"><span data-stu-id="475ee-213">PTP internal</span></span>

### <a name="example"></a><span data-ttu-id="475ee-214">Exempel</span><span class="sxs-lookup"><span data-stu-id="475ee-214">Example</span></span>
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a><span data-ttu-id="475ee-215">nx_ptp_client_start</span><span class="sxs-lookup"><span data-stu-id="475ee-215">nx_ptp_client_start</span></span>

<span data-ttu-id="475ee-216">Starta PTP-klient.</span><span class="sxs-lookup"><span data-stu-id="475ee-216">Start PTP client.</span></span>

### <a name="prototype"></a><span data-ttu-id="475ee-217">Prototyp</span><span class="sxs-lookup"><span data-stu-id="475ee-217">Prototype</span></span>

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a><span data-ttu-id="475ee-218">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="475ee-218">Description</span></span>
<span data-ttu-id="475ee-219">Den här tjänsten startar en tidigare skapad PTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="475ee-219">This service starts a previously created PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="475ee-220">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="475ee-220">Input Parameters</span></span>
* <span data-ttu-id="475ee-221">**client_ptr** Pekare till PTP-klient för att skapa</span><span class="sxs-lookup"><span data-stu-id="475ee-221">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="475ee-222">**client_port_identity_ptr** Pekare till klient port och identitet, den kan vara NULL</span><span class="sxs-lookup"><span data-stu-id="475ee-222">**client_port_identity_ptr** Pointer to client port and identity, it can be NULL</span></span>
* <span data-ttu-id="475ee-223">**client_port_identity_length** Längden på klient porten och identiteten.</span><span class="sxs-lookup"><span data-stu-id="475ee-223">**client_port_identity_length** Length of client port and identity.</span></span> <span data-ttu-id="475ee-224">Värdet måste vara 0 om client_port_identity_ptr är NULL eller NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)</span><span class="sxs-lookup"><span data-stu-id="475ee-224">It must be 0 if client_port_identity_ptr is NULL or NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)</span></span>
* <span data-ttu-id="475ee-225">**domän** PTP-klockans domän</span><span class="sxs-lookup"><span data-stu-id="475ee-225">**domain** PTP clock domain</span></span>
* <span data-ttu-id="475ee-226">**transport_specific** 4 bitar av transporten är speciell</span><span class="sxs-lookup"><span data-stu-id="475ee-226">**transport_specific** 4 bits of transport specific</span></span>
* <span data-ttu-id="475ee-227">**event_callback** Callback-funktionen har anropats för händelsen</span><span class="sxs-lookup"><span data-stu-id="475ee-227">**event_callback** Callback function invoked on event</span></span>
* <span data-ttu-id="475ee-228">**event_callback_data** Data för händelse återanrop</span><span class="sxs-lookup"><span data-stu-id="475ee-228">**event_callback_data** Data for the event callback</span></span>

### <a name="return-values"></a><span data-ttu-id="475ee-229">Retur värden</span><span class="sxs-lookup"><span data-stu-id="475ee-229">Return Values</span></span>
* <span data-ttu-id="475ee-230">**NX_SUCCESS** (0X00) klienten har startats</span><span class="sxs-lookup"><span data-stu-id="475ee-230">**NX_SUCCESS** (0x00) Client successfully started</span></span>
* <span data-ttu-id="475ee-231">**NX_PTP_CLIENT_ALREADY_STARTED** (0XD02) PTP-klienten har redan startats</span><span class="sxs-lookup"><span data-stu-id="475ee-231">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="475ee-232">**status** Status för slut för ande av NetX Duo-och ThreadX service-anrop</span><span class="sxs-lookup"><span data-stu-id="475ee-232">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="475ee-233">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="475ee-233">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="475ee-234">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="475ee-234">Allowed From</span></span>
<span data-ttu-id="475ee-235">Konversation</span><span class="sxs-lookup"><span data-stu-id="475ee-235">Threads</span></span>

### <a name="example"></a><span data-ttu-id="475ee-236">Exempel</span><span class="sxs-lookup"><span data-stu-id="475ee-236">Example</span></span>
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a><span data-ttu-id="475ee-237">nx_ptp_client_stop</span><span class="sxs-lookup"><span data-stu-id="475ee-237">nx_ptp_client_stop</span></span>

<span data-ttu-id="475ee-238">Stoppa PTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="475ee-238">Stop PTP client.</span></span>  <span data-ttu-id="475ee-239">När PTP-klienten har stoppats bearbetar den inte PTP-paket eller överför PTP-paket.</span><span class="sxs-lookup"><span data-stu-id="475ee-239">After the PTP client is stopped, it does not process PTP packets, nor does it transmit PTP packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="475ee-240">Prototyp</span><span class="sxs-lookup"><span data-stu-id="475ee-240">Prototype</span></span>

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="475ee-241">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="475ee-241">Description</span></span>
<span data-ttu-id="475ee-242">Den här tjänsten stoppar en tidigare skapad och startad PTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="475ee-242">This service stops a previously created and started PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="475ee-243">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="475ee-243">Input Parameters</span></span>
* <span data-ttu-id="475ee-244">**client_ptr** Pekare till PTP-klient för att stoppa</span><span class="sxs-lookup"><span data-stu-id="475ee-244">**client_ptr** Pointer to PTP client to stop</span></span>

### <a name="return-values"></a><span data-ttu-id="475ee-245">Retur värden</span><span class="sxs-lookup"><span data-stu-id="475ee-245">Return Values</span></span>
* <span data-ttu-id="475ee-246">**NX_SUCCESS** (0X00) klienten har stoppats</span><span class="sxs-lookup"><span data-stu-id="475ee-246">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>
* <span data-ttu-id="475ee-247">**NX_PTP_CLIENT_NOT_STARTED** -klienten (0xD01) har inte startats</span><span class="sxs-lookup"><span data-stu-id="475ee-247">**NX_PTP_CLIENT_NOT_STARTED** (0xD01) Client not started</span></span>
* <span data-ttu-id="475ee-248">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="475ee-248">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="475ee-249">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="475ee-249">Allowed From</span></span>
<span data-ttu-id="475ee-250">Konversation</span><span class="sxs-lookup"><span data-stu-id="475ee-250">Threads</span></span>

### <a name="example"></a><span data-ttu-id="475ee-251">Exempel</span><span class="sxs-lookup"><span data-stu-id="475ee-251">Example</span></span>
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a><span data-ttu-id="475ee-252">nx_ptp_client_sync_info_get</span><span class="sxs-lookup"><span data-stu-id="475ee-252">nx_ptp_client_sync_info_get</span></span>

<span data-ttu-id="475ee-253">Hämta synkroniseringsinformation.</span><span class="sxs-lookup"><span data-stu-id="475ee-253">Get Sync information.</span></span>

### <a name="prototype"></a><span data-ttu-id="475ee-254">Prototyp</span><span class="sxs-lookup"><span data-stu-id="475ee-254">Prototype</span></span>

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a><span data-ttu-id="475ee-255">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="475ee-255">Description</span></span>
<span data-ttu-id="475ee-256">Den här tjänsten hämtar information om Sync-meddelande.</span><span class="sxs-lookup"><span data-stu-id="475ee-256">This service gets information of Sync message.</span></span> <span data-ttu-id="475ee-257">Kontroll blocket för synkronisering skickas till användar programmet via funktionen motringning av händelse.</span><span class="sxs-lookup"><span data-stu-id="475ee-257">The Sync control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="475ee-258">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="475ee-258">Input Parameters</span></span>
* <span data-ttu-id="475ee-259">**client_ptr** Pekare till PTP-klient för att skapa</span><span class="sxs-lookup"><span data-stu-id="475ee-259">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="475ee-260">**flaggor** Flaggor i Sync-meddelande</span><span class="sxs-lookup"><span data-stu-id="475ee-260">**flags** Flags in Sync message</span></span>
* <span data-ttu-id="475ee-261">**utc_offset** Förskjutning mellan TAI och UTC</span><span class="sxs-lookup"><span data-stu-id="475ee-261">**utc_offset** Offset between TAI and UTC</span></span>

### <a name="return-values"></a><span data-ttu-id="475ee-262">Retur värden</span><span class="sxs-lookup"><span data-stu-id="475ee-262">Return Values</span></span>
* <span data-ttu-id="475ee-263">**NX_SUCCESS** (0X00) Hämta synkroniseringsinformation</span><span class="sxs-lookup"><span data-stu-id="475ee-263">**NX_SUCCESS** (0x00) Get Sync information successfully</span></span>
* <span data-ttu-id="475ee-264">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="475ee-264">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="475ee-265">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="475ee-265">Allowed From</span></span>
<span data-ttu-id="475ee-266">Konversation</span><span class="sxs-lookup"><span data-stu-id="475ee-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="475ee-267">Exempel</span><span class="sxs-lookup"><span data-stu-id="475ee-267">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a><span data-ttu-id="475ee-268">nx_ptp_client_time_get</span><span class="sxs-lookup"><span data-stu-id="475ee-268">nx_ptp_client_time_get</span></span>

<span data-ttu-id="475ee-269">Hämta aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="475ee-269">Get current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="475ee-270">Prototyp</span><span class="sxs-lookup"><span data-stu-id="475ee-270">Prototype</span></span>

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="475ee-271">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="475ee-271">Description</span></span>
<span data-ttu-id="475ee-272">Den här tjänsten hämtar den aktuella värdet för PTP-klockan.</span><span class="sxs-lookup"><span data-stu-id="475ee-272">This service gets the current value of the PTP clock.</span></span> <span data-ttu-id="475ee-273">Den finns tillgänglig oavsett om PTP-klienten är synkroniserad med huvud klockan eller inte.</span><span class="sxs-lookup"><span data-stu-id="475ee-273">It is available no matter PTP client is synchronized with master clock or not.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="475ee-274">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="475ee-274">Input Parameters</span></span>
* <span data-ttu-id="475ee-275">**client_ptr** Pekare till PTP-klient för att skapa</span><span class="sxs-lookup"><span data-stu-id="475ee-275">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="475ee-276">**time_ptr** Pekare till PTP-tid</span><span class="sxs-lookup"><span data-stu-id="475ee-276">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="475ee-277">Retur värden</span><span class="sxs-lookup"><span data-stu-id="475ee-277">Return Values</span></span>
* <span data-ttu-id="475ee-278">**NX_SUCCESS** (0x00)-klienten har skapats</span><span class="sxs-lookup"><span data-stu-id="475ee-278">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="475ee-279">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="475ee-279">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="475ee-280">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="475ee-280">Allowed From</span></span>
<span data-ttu-id="475ee-281">Konversation</span><span class="sxs-lookup"><span data-stu-id="475ee-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="475ee-282">Exempel</span><span class="sxs-lookup"><span data-stu-id="475ee-282">Example</span></span>
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a><span data-ttu-id="475ee-283">nx_ptp_client_time_set</span><span class="sxs-lookup"><span data-stu-id="475ee-283">nx_ptp_client_time_set</span></span>

<span data-ttu-id="475ee-284">Ange aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="475ee-284">Set current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="475ee-285">Prototyp</span><span class="sxs-lookup"><span data-stu-id="475ee-285">Prototype</span></span>

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="475ee-286">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="475ee-286">Description</span></span>
<span data-ttu-id="475ee-287">Den här tjänsten anger den aktuella värdet för PTP-klockan.</span><span class="sxs-lookup"><span data-stu-id="475ee-287">This service sets the current value of the PTP clock.</span></span> <span data-ttu-id="475ee-288">Den måste anropas innan PTP-klienten startar.</span><span class="sxs-lookup"><span data-stu-id="475ee-288">It must be invoked before PTP client starts.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="475ee-289">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="475ee-289">Input Parameters</span></span>
* <span data-ttu-id="475ee-290">**client_ptr** Pekare till PTP-klient för att skapa</span><span class="sxs-lookup"><span data-stu-id="475ee-290">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="475ee-291">**time_ptr** Pekare till PTP-tid</span><span class="sxs-lookup"><span data-stu-id="475ee-291">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="475ee-292">Retur värden</span><span class="sxs-lookup"><span data-stu-id="475ee-292">Return Values</span></span>
* <span data-ttu-id="475ee-293">**NX_SUCCESS** (0x00)-klienten har skapats</span><span class="sxs-lookup"><span data-stu-id="475ee-293">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="475ee-294">**NX_PTP_CLIENT_ALREADY_STARTED** (0XD02) PTP-klienten har redan startats</span><span class="sxs-lookup"><span data-stu-id="475ee-294">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="475ee-295">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="475ee-295">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="475ee-296">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="475ee-296">Allowed From</span></span>
<span data-ttu-id="475ee-297">Konversation</span><span class="sxs-lookup"><span data-stu-id="475ee-297">Threads</span></span>

### <a name="example"></a><span data-ttu-id="475ee-298">Exempel</span><span class="sxs-lookup"><span data-stu-id="475ee-298">Example</span></span>
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a><span data-ttu-id="475ee-299">nx_ptp_client_utility_convert_time_to_date</span><span class="sxs-lookup"><span data-stu-id="475ee-299">nx_ptp_client_utility_convert_time_to_date</span></span>

<span data-ttu-id="475ee-300">Konvertera PTP-tid till UTC-datum och tid.</span><span class="sxs-lookup"><span data-stu-id="475ee-300">Convert PTP time to a UTC date and time.</span></span>

### <a name="prototype"></a><span data-ttu-id="475ee-301">Prototyp</span><span class="sxs-lookup"><span data-stu-id="475ee-301">Prototype</span></span>

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a><span data-ttu-id="475ee-302">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="475ee-302">Description</span></span>
<span data-ttu-id="475ee-303">Den här tjänsten konverterar PTP-tid till UTC-datum och tid.</span><span class="sxs-lookup"><span data-stu-id="475ee-303">This service converts PTP time to a UTC date and time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="475ee-304">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="475ee-304">Input Parameters</span></span>
* <span data-ttu-id="475ee-305">**time_ptr** Pekare till PTP-tid</span><span class="sxs-lookup"><span data-stu-id="475ee-305">**time_ptr** Pointer to PTP time</span></span>
* <span data-ttu-id="475ee-306">**förskjutning** Signerad andra förskjutning för att lägga till PTP-tid</span><span class="sxs-lookup"><span data-stu-id="475ee-306">**offset** Signed second offset to add the PTP time</span></span>
* <span data-ttu-id="475ee-307">**date_time_ptr** Pekare till resultat datum</span><span class="sxs-lookup"><span data-stu-id="475ee-307">**date_time_ptr** Pointer to resulting date</span></span>

### <a name="return-values"></a><span data-ttu-id="475ee-308">Retur värden</span><span class="sxs-lookup"><span data-stu-id="475ee-308">Return Values</span></span>
* <span data-ttu-id="475ee-309">**NX_SUCCESS** (0x00)-klienten har skapats</span><span class="sxs-lookup"><span data-stu-id="475ee-309">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="475ee-310">**Pekare till resulterande datum** (0XD03) ogiltig indataparameter</span><span class="sxs-lookup"><span data-stu-id="475ee-310">**Pointer to resulting date** (0xD03) Invalid input parameter</span></span>
* <span data-ttu-id="475ee-311">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="475ee-311">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="475ee-312">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="475ee-312">Allowed From</span></span>
<span data-ttu-id="475ee-313">Konversation</span><span class="sxs-lookup"><span data-stu-id="475ee-313">Threads</span></span>

### <a name="example"></a><span data-ttu-id="475ee-314">Exempel</span><span class="sxs-lookup"><span data-stu-id="475ee-314">Example</span></span>
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a><span data-ttu-id="475ee-315">nx_ptp_client_utility_time_diff</span><span class="sxs-lookup"><span data-stu-id="475ee-315">nx_ptp_client_utility_time_diff</span></span>

<span data-ttu-id="475ee-316">Skilj två PTP-tider.</span><span class="sxs-lookup"><span data-stu-id="475ee-316">Diff two PTP times.</span></span>

### <a name="prototype"></a><span data-ttu-id="475ee-317">Prototyp</span><span class="sxs-lookup"><span data-stu-id="475ee-317">Prototype</span></span>

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a><span data-ttu-id="475ee-318">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="475ee-318">Description</span></span>
<span data-ttu-id="475ee-319">Den här tjänsten beräknar skillnaden mellan två PTP-tider.</span><span class="sxs-lookup"><span data-stu-id="475ee-319">This service computes the difference between two PTP times.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="475ee-320">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="475ee-320">Input Parameters</span></span>
* <span data-ttu-id="475ee-321">**time1_ptr** Pekare till första PTP-tid</span><span class="sxs-lookup"><span data-stu-id="475ee-321">**time1_ptr** Pointer to first PTP time</span></span>
* <span data-ttu-id="475ee-322">**time2_ptr** Pekare till andra PTP-tid</span><span class="sxs-lookup"><span data-stu-id="475ee-322">**time2_ptr** Pointer to second PTP time</span></span>
* <span data-ttu-id="475ee-323">**result_ptr** Pekare till resultat time1 – Time2</span><span class="sxs-lookup"><span data-stu-id="475ee-323">**result_ptr** Pointer to result time1-time2</span></span>

### <a name="return-values"></a><span data-ttu-id="475ee-324">Retur värden</span><span class="sxs-lookup"><span data-stu-id="475ee-324">Return Values</span></span>
* <span data-ttu-id="475ee-325">**NX_SUCCESS** (0x00)-klienten har skapats</span><span class="sxs-lookup"><span data-stu-id="475ee-325">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="475ee-326">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="475ee-326">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="475ee-327">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="475ee-327">Allowed From</span></span>
<span data-ttu-id="475ee-328">Konversation</span><span class="sxs-lookup"><span data-stu-id="475ee-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="475ee-329">Exempel</span><span class="sxs-lookup"><span data-stu-id="475ee-329">Example</span></span>
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```