---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo MQTT Client Services
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo MQTT-klienttjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9cbb65946c45bfbc476091f7c604346e839a42fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825896"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a><span data-ttu-id="c7254-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo MQTT Client Services</span><span class="sxs-lookup"><span data-stu-id="c7254-103">Chapter 3 - Description of Azure RTOS NetX Duo MQTT client services</span></span>

<span data-ttu-id="c7254-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo MQTT client-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="c7254-104">This chapter contains a description of all Azure RTOS NetX Duo MQTT client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="c7254-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="c7254-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="c7254-106">**nxd_mqtt_client_create** *skapa en MQTT-klient instans*</span><span class="sxs-lookup"><span data-stu-id="c7254-106">**nxd_mqtt_client_create** *Create MQTT client instance*</span></span>
- <span data-ttu-id="c7254-107">**nxd_mqtt_client_will_message_set** *ställer in meddelandet*</span><span class="sxs-lookup"><span data-stu-id="c7254-107">**nxd_mqtt_client_will_message_set** *Set the will message*</span></span>
- <span data-ttu-id="c7254-108">**nxd_mqtt_client_client_login_set** *Ange MQTT användar namn och lösen ord för klient inloggning*</span><span class="sxs-lookup"><span data-stu-id="c7254-108">**nxd_mqtt_client_client_login_set** *Set MQTT client login username and password*</span></span>
- <span data-ttu-id="c7254-109">**nxd_mqtt_client_connect** *ansluta MQTT-klienten till Service Broker*</span><span class="sxs-lookup"><span data-stu-id="c7254-109">**nxd_mqtt_client_connect** *Connect MQTT Client to the broker*</span></span>
- <span data-ttu-id="c7254-110">**nxd_mqtt_client_secure_connect** *ansluta MQTT-klienten till KOORDINATORn med TLS-säkerhet*</span><span class="sxs-lookup"><span data-stu-id="c7254-110">**nxd_mqtt_client_secure_connect** *Connect MQTT client to the broker with TLS security*</span></span>
- <span data-ttu-id="c7254-111">**nxd_mqtt_client_publish** *publicera ett meddelande via Broker.*</span><span class="sxs-lookup"><span data-stu-id="c7254-111">**nxd_mqtt_client_publish** *Publish a message through the broker.*</span></span>
- <span data-ttu-id="c7254-112">**nxd_mqtt_client_subscribe** *Prenumerera på ett ämne*</span><span class="sxs-lookup"><span data-stu-id="c7254-112">**nxd_mqtt_client_subscribe** *Subscribe to a topic*</span></span>
- <span data-ttu-id="c7254-113">**nxd_mqtt_client_unsubscribe** *avbryta prenumerationen på ett ämne*</span><span class="sxs-lookup"><span data-stu-id="c7254-113">**nxd_mqtt_client_unsubscribe** *Unsubscribe from a topic*</span></span>
- <span data-ttu-id="c7254-114">**nxd_mqtt_client_receive_notify_set** *Ange MQTT meddelande ta emot meddelande om motringning*</span><span class="sxs-lookup"><span data-stu-id="c7254-114">**nxd_mqtt_client_receive_notify_set** *Set MQTT message receive notify callback function*</span></span>
- <span data-ttu-id="c7254-115">**nxd_mqtt_client_message_get** *Hämta ett meddelande från Service Broker*</span><span class="sxs-lookup"><span data-stu-id="c7254-115">**nxd_mqtt_client_message_get** *Retrieve a message from the broker*</span></span>
- <span data-ttu-id="c7254-116">**nxd_mqtt_client_disconnect_notify_set** *Ange MQTT meddelande om att koppla från* meddelande om motringning</span><span class="sxs-lookup"><span data-stu-id="c7254-116">**nxd_mqtt_client_disconnect_notify_set** *Set MQTT message disconnect notify callback function*</span></span>
- <span data-ttu-id="c7254-117">**nxd_mqtt_client_disconnect** *från koppling av MQTT-klienten från Broker*</span><span class="sxs-lookup"><span data-stu-id="c7254-117">**nxd_mqtt_client_disconnect** *Disconnect MQTT client from the broker*</span></span>
- <span data-ttu-id="c7254-118">**nxd_mqtt_client_delete** *ta bort MQTT-klient instansen*</span><span class="sxs-lookup"><span data-stu-id="c7254-118">**nxd_mqtt_client_delete** *Delete the MQTT client instance*</span></span>

## <a name="nxd_mqtt_client_create"></a><span data-ttu-id="c7254-119">nxd_mqtt_client_create</span><span class="sxs-lookup"><span data-stu-id="c7254-119">nxd_mqtt_client_create</span></span>

<span data-ttu-id="c7254-120">Skapa MQTT-klient instans</span><span class="sxs-lookup"><span data-stu-id="c7254-120">Create MQTT Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-121">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-121">Prototype</span></span>

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="c7254-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-122">Description</span></span>

<span data-ttu-id="c7254-123">Den här tjänsten skapar en MQTT-klient instans på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="c7254-123">This service creates an MQTT Client instance on the specified IP instance.</span></span> <span data-ttu-id="c7254-124">*Client_id* strängen skickas till servern under MQTT-anslutnings fasen som *klient-ID (ClientId)*.</span><span class="sxs-lookup"><span data-stu-id="c7254-124">The *client_id* string is passed to the server during MQTT connection phase as the *Client Identifier (ClientId)*.</span></span> <span data-ttu-id="c7254-125">Det skapar också de nödvändiga ThreadX-resurserna (MQTT klient aktivitets tråd, mutex, händelse flagg grupp och TCP-socket).</span><span class="sxs-lookup"><span data-stu-id="c7254-125">It also creates the necessary ThreadX resources (MQTT Client task thread, mutex, event flag group, and TCP socket).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c7254-126">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-126">Input Parameters</span></span>

- <span data-ttu-id="c7254-127">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-127">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="c7254-128">**client_name** Klient namn sträng.</span><span class="sxs-lookup"><span data-stu-id="c7254-128">**client_name** Client name string.</span></span>
- <span data-ttu-id="c7254-129">**client_id** Klient-ID-sträng som används under anslutnings fasen.</span><span class="sxs-lookup"><span data-stu-id="c7254-129">**client_id** Client ID string used during connection phase.</span></span> <span data-ttu-id="c7254-130">MQTT-Broker använder den här client_id för att unikt identifiera en klient.</span><span class="sxs-lookup"><span data-stu-id="c7254-130">MQTT broker uses this client_id to uniquely identify a client.</span></span>
- <span data-ttu-id="c7254-131">**client_id_length** Längden på klient-ID-strängen, i byte.</span><span class="sxs-lookup"><span data-stu-id="c7254-131">**client_id_length** Length of the client ID string, in bytes.</span></span>
- <span data-ttu-id="c7254-132">**ip_ptr** Pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="c7254-132">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="c7254-133">**pool_ptr** Pekare till en Packet Pools MQTT-klient använder för att utföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c7254-133">**pool_ptr** Pointer to a packet pool MQTT client uses for its operation.</span></span>
- <span data-ttu-id="c7254-134">**stack_ptr** Stack Area för MQTT-klientens tråd.</span><span class="sxs-lookup"><span data-stu-id="c7254-134">**stack_ptr** Stack area for the MQTT Client thread.</span></span>
- <span data-ttu-id="c7254-135">**stack_size** Storlek på stackområdet, i byte.</span><span class="sxs-lookup"><span data-stu-id="c7254-135">**stack_size** Size of the stack area, in bytes.</span></span>
- <span data-ttu-id="c7254-136">**mqtt_thread_priority** Prioriteten för MQTT-tråden.</span><span class="sxs-lookup"><span data-stu-id="c7254-136">**mqtt_thread_priority** The priority of the MQTT Thread.</span></span>
- <span data-ttu-id="c7254-137">**memory_ptr** Föråldrad.</span><span class="sxs-lookup"><span data-stu-id="c7254-137">**memory_ptr** Deprecated.</span></span> <span data-ttu-id="c7254-138">Används inte längre.</span><span class="sxs-lookup"><span data-stu-id="c7254-138">Not used anymore.</span></span>
- <span data-ttu-id="c7254-139">**memory_size** Föråldrad.</span><span class="sxs-lookup"><span data-stu-id="c7254-139">**memory_size** Deprecated.</span></span> <span data-ttu-id="c7254-140">Används inte längre.</span><span class="sxs-lookup"><span data-stu-id="c7254-140">Not used anymore.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7254-141">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-141">Return Values</span></span>

- <span data-ttu-id="c7254-142">**NXD_MQTT_SUCCESS** (0X00) har skapat MQTT-klienten.</span><span class="sxs-lookup"><span data-stu-id="c7254-142">**NXD_MQTT_SUCCESS** (0x00) Successfully created MQTT client.</span></span>
- <span data-ttu-id="c7254-143">Internt **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel</span><span class="sxs-lookup"><span data-stu-id="c7254-143">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="c7254-144">NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block, ip_ptr eller Packet pool-pekare.</span><span class="sxs-lookup"><span data-stu-id="c7254-144">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer.</span></span>
- <span data-ttu-id="c7254-145">NXD_MQTT_INVALID_PARAMETER (0x10009) ogiltig kommer att sträng, will_retrain_flag eller will_QoS värde.</span><span class="sxs-lookup"><span data-stu-id="c7254-145">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-146">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-146">Allowed From</span></span>

<span data-ttu-id="c7254-147">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-148">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-148">Example</span></span>

```c
#define CLIENT_ID_STRING "My Test Client"

#define MQTT_THREAD_PRIORITY 2

NXD_MQTT_CLIENT my_client;
NX_IP ip_0; /* Assume ip_0 is created prior to MQTT client creation. */
NX_PACKET_POOL pool_0;/* Assume pool_0 is created prior to MQTT client creation. */
UCHAR mqtt_thread_stack[STACK_SIZE];

/* Create the MQTT Client instance on "ip_0". */
status = **nxd_mqtt_client_create**(&my_client, "my client",
    CLIENT_ID_STRING, stlren(CLIENT_ID_STRING),
    &ip_0, &pool_0, (VOID*)mqtt_thread_stack, STACK_SIZE,
    MQTT_THREAD_PRIORITY, NX_NULL, 0);

/* If status is NXD_MQTT_SUCCESS an MQTT Client instance was successfully created. */
```

## <a name="nxd_mqtt_client_will_message_set"></a><span data-ttu-id="c7254-149">nxd_mqtt_client_will_message_set</span><span class="sxs-lookup"><span data-stu-id="c7254-149">nxd_mqtt_client_will_message_set</span></span>

<span data-ttu-id="c7254-150">Anger att meddelandet ska visas</span><span class="sxs-lookup"><span data-stu-id="c7254-150">Sets the Will message</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-151">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-151">Prototype</span></span>

```c
UINT nxd_mqtt_client_will_message_set(NXD_MQTT_CLIENT
    *client_ptr,
    Const UCHAR *will_topic,
    UINT will_topic_length
    Const UCHAR *will_message,
    UINT will_message_length,
    UINT will_retain_flag,
    UINT will_QoS);
```

### <a name="description"></a><span data-ttu-id="c7254-152">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-152">Description</span></span>

<span data-ttu-id="c7254-153">Den här tjänsten anger det valfria avsnittet och meddelandet skickas innan klienten ansluter till servern.</span><span class="sxs-lookup"><span data-stu-id="c7254-153">This service sets the optional will topic and will message before the client connects to the server.</span></span> <span data-ttu-id="c7254-154">Avsnittet måste vara UTF-8-kodad sträng.</span><span class="sxs-lookup"><span data-stu-id="c7254-154">Will topic must be UTF-8 encoded string.</span></span>

<span data-ttu-id="c7254-155">Om det är inställt skickas meddelandet till Service Broker som en del av ANSLUTNINGS meddelandet.</span><span class="sxs-lookup"><span data-stu-id="c7254-155">The will message, if set, is transmitted to the broker as part of the CONNECT message.</span></span> <span data-ttu-id="c7254-156">Programmet som ska användas måste därför använda den här tjänsten innan MQTT-anslutningen görs.</span><span class="sxs-lookup"><span data-stu-id="c7254-156">Therefore application wishing to use will message must use this service before the MQTT connection is make.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c7254-157">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-157">Input Parameters</span></span>

- <span data-ttu-id="c7254-158">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-158">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="c7254-159">**will_topic** UTF-8-kodad ämnes sträng.</span><span class="sxs-lookup"><span data-stu-id="c7254-159">**will_topic** UTF-8 encoded will topic string.</span></span> <span data-ttu-id="c7254-160">Ämnet måste finnas.</span><span class="sxs-lookup"><span data-stu-id="c7254-160">Will topic must be present.</span></span> <span data-ttu-id="c7254-161">Anroparen måste ha will_topic strängen giltig till *nx_mqtt_client_connect* anropet görs.</span><span class="sxs-lookup"><span data-stu-id="c7254-161">Caller must keep the will_topic string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="c7254-162">**will_topic_length** Antal byte i ämnes strängen</span><span class="sxs-lookup"><span data-stu-id="c7254-162">**will_topic_length** Number of bytes in the will topic string</span></span>
- <span data-ttu-id="c7254-163">**will_message** Det program som definierats kommer att visas.</span><span class="sxs-lookup"><span data-stu-id="c7254-163">**will_message** Application defined will message.</span></span> <span data-ttu-id="c7254-164">Om meddelandet inte är obligatoriskt kan programmet ange det här fältet som *NX_NULL.*</span><span class="sxs-lookup"><span data-stu-id="c7254-164">If will message is not required, application can set this field to *NX_NULL.*</span></span>
- <span data-ttu-id="c7254-165">**will_message_length** Antal byte i meddelande strängen som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="c7254-165">**will_message_length** Number of bytes in the will message string.</span></span> <span data-ttu-id="c7254-166">Om will_message är inställt på NULL måste will_message_length anges till 0.</span><span class="sxs-lookup"><span data-stu-id="c7254-166">If will_message is set to NULL, will_message_length must be set to 0.</span></span>
- <span data-ttu-id="c7254-167">**will_retain_flag** Anger om servern ska publicera meddelandet som ett kvarhållet meddelande.</span><span class="sxs-lookup"><span data-stu-id="c7254-167">**will_retain_flag** Whether the server publishes the will message as a retained message.</span></span> <span data-ttu-id="c7254-168">Giltiga värden är *NX_TRUE* eller *NX_FALSE.*</span><span class="sxs-lookup"><span data-stu-id="c7254-168">Valid values are *NX_TRUE* or *NX_FALSE.*</span></span>
- <span data-ttu-id="c7254-169">**will_QoS** QoS-värdet som används av servern när meddelandet skickas visas.</span><span class="sxs-lookup"><span data-stu-id="c7254-169">**will_QoS** QoS value used by the server when sending will message.</span></span> <span data-ttu-id="c7254-170">Giltiga värden är 0 och 1.</span><span class="sxs-lookup"><span data-stu-id="c7254-170">Valid values are 0 or 1.</span></span>  

### <a name="return-values"></a><span data-ttu-id="c7254-171">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-171">Return Values</span></span>

- <span data-ttu-id="c7254-172">**NXD_MQTT_SUCCESS** (0x00) anger att meddelandet ska visas.</span><span class="sxs-lookup"><span data-stu-id="c7254-172">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="c7254-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0X1000C) QoS-nivå 2-meddelanden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="c7254-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="c7254-174">NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block.</span><span class="sxs-lookup"><span data-stu-id="c7254-174">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="c7254-175">NXD_MQTT_INVALID_PARAMETER (0x10009) ogiltig kommer att sträng, will_retrain_flag eller will_QoS värde.</span><span class="sxs-lookup"><span data-stu-id="c7254-175">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-176">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-176">Allowed From</span></span>

<span data-ttu-id="c7254-177">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-178">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-178">Example</span></span>

```c
#define WILL_TOPIC "my_will_topic"

#define WILL_MESSAGE "my will message"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_will_message_set(&my_client,
    WILL_TOPIC, STRLEN(WILL_TOPIC),
    WILL_MESSAGE, STRLEN(WILL_MESSAGE),
    NX_TRUE, 0);

/* If status is NXD_MQTT_SUCCESS the will message is properly
configured for the session. It will be transmitted to the server
during MQTT connection. */
```

## <a name="nxd_mqtt_client_login_set"></a><span data-ttu-id="c7254-179">nxd_mqtt_client_login_set</span><span class="sxs-lookup"><span data-stu-id="c7254-179">nxd_mqtt_client_login_set</span></span>

<span data-ttu-id="c7254-180">Anger MQTT användar namn och lösen ord för klient inloggning</span><span class="sxs-lookup"><span data-stu-id="c7254-180">Sets MQTT client login username and password</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-181">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-181">Prototype</span></span>

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a><span data-ttu-id="c7254-182">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-182">Description</span></span>

<span data-ttu-id="c7254-183">Den här tjänsten anger användar namn och lösen ord, som används vid MQTT anslutnings fasen för inloggning i autentisering.</span><span class="sxs-lookup"><span data-stu-id="c7254-183">This service sets the username and password, which is used during MQTT connection phase for log in authentication purpose.</span></span>

<span data-ttu-id="c7254-184">MQTT-klientens inloggning med användar namn och lösen ord är valfritt.</span><span class="sxs-lookup"><span data-stu-id="c7254-184">The MQTT client login with username and password is optional.</span></span> <span data-ttu-id="c7254-185">I situationer där servern kräver ett användar namn och lösen ord måste användar namnet och lösen ordet anges innan anslutningen upprättas.</span><span class="sxs-lookup"><span data-stu-id="c7254-185">In situations where the server requires a user name and password, the user name and password must be set before the connection is established.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c7254-186">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-186">Input Parameters</span></span>

- <span data-ttu-id="c7254-187">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-187">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="c7254-188">**användar namn** UTF-8-kodad användar namn sträng.</span><span class="sxs-lookup"><span data-stu-id="c7254-188">**username** UTF-8 encoded user name string.</span></span> <span data-ttu-id="c7254-189">Anroparen måste ha användar namn strängen giltig till *nx_mqtt_client_connect* anropet görs.</span><span class="sxs-lookup"><span data-stu-id="c7254-189">Caller must keep the username string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="c7254-190">**username_length** Antal byte i användar namn strängen</span><span class="sxs-lookup"><span data-stu-id="c7254-190">**username_length** Number of bytes in the username string</span></span>
- <span data-ttu-id="c7254-191">**lösen ord** Lösen ords sträng.</span><span class="sxs-lookup"><span data-stu-id="c7254-191">**password** Password string.</span></span> <span data-ttu-id="c7254-192">Om lösen ord inte krävs kan det här fältet anges till NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="c7254-192">If password is not required, this field may be set to NX_NULL.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7254-193">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-193">Return Values</span></span>

- <span data-ttu-id="c7254-194">**NXD_MQTT_SUCCESS** (0x00) anger att meddelandet ska visas.</span><span class="sxs-lookup"><span data-stu-id="c7254-194">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="c7254-195">NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block.</span><span class="sxs-lookup"><span data-stu-id="c7254-195">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="c7254-196">NXD_MQTT_INVALID_PARAMETER (0x10009) ogiltig användar namn sträng eller lösen ords sträng.</span><span class="sxs-lookup"><span data-stu-id="c7254-196">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid username string or the password string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-197">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-197">Allowed From</span></span>

<span data-ttu-id="c7254-198">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-199">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-199">Example</span></span>

```c
#define USERNAME "MY_NAME"

#define PASSWORD "MY_LOGIN_SECRET"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_login_set(&my_client,
    USERNAME, STRLEN(USERNAME),
    PASSWORD, STRLEN(PASSWORD));

/* If status is NXD_MQTT_SUCCESS the username and the password 
are set for the session. This information will be 
transmitted to the server during MQTT connection. */
```

## <a name="nxd_mqtt_client_connect"></a><span data-ttu-id="c7254-200">nxd_mqtt_client_connect</span><span class="sxs-lookup"><span data-stu-id="c7254-200">nxd_mqtt_client_connect</span></span>

<span data-ttu-id="c7254-201">Anslut MQTT-klienten till Broker</span><span class="sxs-lookup"><span data-stu-id="c7254-201">Connect MQTT Client to the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-202">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-202">Prototype</span></span>

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a><span data-ttu-id="c7254-203">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-203">Description</span></span>

<span data-ttu-id="c7254-204">Den här tjänsten initierar en anslutning till Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-204">This service initiates a connection to the broker.</span></span> <span data-ttu-id="c7254-205">Först binder en TCP-socket och gör sedan en TCP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="c7254-205">First it binds a TCP socket, then makes a TCP connection.</span></span> <span data-ttu-id="c7254-206">Förutsatt att det lyckas skapas en timer om MQTT Keep Alive-funktionen är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="c7254-206">Assuming that succeeds, it creates a timer if the MQTT keep alive feature is enabled.</span></span> <span data-ttu-id="c7254-207">Sedan ansluter den till MQTT-servern (Broker).</span><span class="sxs-lookup"><span data-stu-id="c7254-207">Then it connects with the MQTT server (broker).</span></span>

<span data-ttu-id="c7254-208">Observera att den här tjänsten skapar en MQTT-anslutning utan TLS-skydd.</span><span class="sxs-lookup"><span data-stu-id="c7254-208">Note that this service creates an MQTT connection with no TLS protection.</span></span> <span data-ttu-id="c7254-209">Om du vill skapa en säker MQTT-anslutning ska programmet använda tjänsten ***nxd_mqtt_client_secure_connect ().***</span><span class="sxs-lookup"><span data-stu-id="c7254-209">To create a secure MQTT connection, the application shall use the service ***nxd_mqtt_client_secure_connect().***</span></span>

<span data-ttu-id="c7254-210">Vid anslutningen, om klienten anger *clean_session* till NX_FALSE, kommer klienten att skicka om meddelanden som lagras som inte har bekräftats ännu.</span><span class="sxs-lookup"><span data-stu-id="c7254-210">Upon the connection, if the client sets the *clean_session* to NX_FALSE, the client will retransmit any messages stored that have not been acknowledged yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c7254-211">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-211">Input Parameters</span></span>

- <span data-ttu-id="c7254-212">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-212">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="c7254-213">**server_ip** IP-adress för Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-213">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="c7254-214">**SERVER_PORT** Port nummer för Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-214">**server_port** Broker port number.</span></span> <span data-ttu-id="c7254-215">Standard porten för MQTT definieras som **_NXD_MQTT_PORT_** (1883).</span><span class="sxs-lookup"><span data-stu-id="c7254-215">The default port for MQTT is defined as **_NXD_MQTT_PORT_** (1883).</span></span>
- <span data-ttu-id="c7254-216">**KEEP_ALIVE** Värdet för Keep Alive, i sekunder, som ska användas under sessionen.</span><span class="sxs-lookup"><span data-stu-id="c7254-216">**keep_alive** The keep alive value, in seconds, to be used during the session.</span></span> <span data-ttu-id="c7254-217">Värdet anger den maximala tiden mellan två MQTT som skickas till koordinatorn innan Service Broker har nått sin tids gräns för klienten.</span><span class="sxs-lookup"><span data-stu-id="c7254-217">The value indicates the maximum time between two MQTT control messages being sent to the broker before the broker times out this client.</span></span> <span data-ttu-id="c7254-218">Värdet 0 stänger av Keep-Alive-funktionen.</span><span class="sxs-lookup"><span data-stu-id="c7254-218">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="c7254-219">**clean_session** Om servern ska starta den här sessionen rensa.</span><span class="sxs-lookup"><span data-stu-id="c7254-219">**clean_session** Whether the server shall start this session clean.</span></span> <span data-ttu-id="c7254-220">Giltiga alternativ är **_NX_TRUE_*_ eller _*_NX_FALSE._**</span><span class="sxs-lookup"><span data-stu-id="c7254-220">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="c7254-221">**wait_option** Vänte tid för anslutning.</span><span class="sxs-lookup"><span data-stu-id="c7254-221">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7254-222">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-222">Return Values</span></span>

- <span data-ttu-id="c7254-223">**NXD_MQTT_SUCCESS** (0X00) lyckad MQTT-anslutning</span><span class="sxs-lookup"><span data-stu-id="c7254-223">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT connection</span></span>
- <span data-ttu-id="c7254-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) klienten är redan ansluten till Service Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="c7254-225">**NXD_MQTT_MUTEX_FAILURE** (0X10003) Det gick inte att hämta MQTT MUTEX</span><span class="sxs-lookup"><span data-stu-id="c7254-225">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="c7254-226">Internt **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel</span><span class="sxs-lookup"><span data-stu-id="c7254-226">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="c7254-227">**NXD_MQTT_CONNECT_FAILURE** (0X10005) Det gick inte att ansluta till Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-227">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="c7254-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) Det gick inte att skicka meddelanden till Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="c7254-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** -servern (0x10008) svarade med fel</span><span class="sxs-lookup"><span data-stu-id="c7254-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error</span></span>
- <span data-ttu-id="c7254-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0X10081) Server svars kod</span><span class="sxs-lookup"><span data-stu-id="c7254-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="c7254-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0X10082) Server svars kod</span><span class="sxs-lookup"><span data-stu-id="c7254-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="c7254-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0X10083) Server svars kod</span><span class="sxs-lookup"><span data-stu-id="c7254-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="c7254-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0X10084) Server svars kod</span><span class="sxs-lookup"><span data-stu-id="c7254-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="c7254-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0X10085) Server svars kod</span><span class="sxs-lookup"><span data-stu-id="c7254-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="c7254-235">NX_PTR_ERROR (0x07) ogiltigt MQTT kontroll block, ip_ptr eller Packet pool pekare</span><span class="sxs-lookup"><span data-stu-id="c7254-235">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-236">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-236">Allowed From</span></span>

<span data-ttu-id="c7254-237">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-238">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-238">Example</span></span>

```c
NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_connect(&my_client, &broker_address,
    NXD_MQTT_PORT,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session flag set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS a connection to the broker is successfully established. */
```

## <a name="nxd_mqtt_client_secure_connect"></a><span data-ttu-id="c7254-239">nxd_mqtt_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="c7254-239">nxd_mqtt_client_secure_connect</span></span>

<span data-ttu-id="c7254-240">Anslut MQTT-klienten till Service Broker med TLS-säkerhet</span><span class="sxs-lookup"><span data-stu-id="c7254-240">Connect MQTT client to the broker with TLS security</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-241">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-241">Prototype</span></span>

```c
UINT nxd_mqtt_client_secure_connect(NXD_MQTT_CLIENT
    *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NXD_MQTT_CLIENT *,
        NX_SECURE_TLS_SESISON *,
        NX_SECURE_TLS_CERTIFICATE *,
        NX_SECURE_TLS_CERTIFICATE *),
    UINT keepalive, UINT connection_flag,
    UINT clean_session, ULONG wait_option));
```

### <a name="description"></a><span data-ttu-id="c7254-242">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-242">Description</span></span>

<span data-ttu-id="c7254-243">Den här tjänsten är identisk med ***nxd_mqtt_client_connect*** förutom att anslutningen går via TLS-skiktet i stället för TCP.</span><span class="sxs-lookup"><span data-stu-id="c7254-243">This service is identical to ***nxd_mqtt_client_connect*** except that the connection goes through TLS layer instead of TCP.</span></span> <span data-ttu-id="c7254-244">Därför skyddas kommunikationen mellan klienten och Service Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-244">Therefore, communication between the client and the broker is secured.</span></span>

<span data-ttu-id="c7254-245">Den användardefinierade *tls_setup* är en callback-funktion som MQTT-klienten använder innan en MQTT-klient anslutning görs.</span><span class="sxs-lookup"><span data-stu-id="c7254-245">The user-defined *tls_setup* is a callback function that the MQTT client uses prior to making a MQTT client connection.</span></span> <span data-ttu-id="c7254-246">Programmet ska initiera NetX Secure TLS, konfigurera säkerhets parametrar och läsa in relevanta certifikat som ska användas under TLS-handskakning.</span><span class="sxs-lookup"><span data-stu-id="c7254-246">The application shall initialize NetX Secure TLS, configure security parameters, and load relevant certificates to be used during TLS handshake.</span></span> <span data-ttu-id="c7254-247">Den faktiska TLS-handskakningen inträffar efter att en TCP-anslutning har upprättats för Broker: s MQTT TLS-port (standard TCP-port 8883).</span><span class="sxs-lookup"><span data-stu-id="c7254-247">The actual TLS handshake happens after a TCP connection is established on the broker's MQTT TLS port (default TCP port 8883).</span></span> <span data-ttu-id="c7254-248">När TLS-handskakningen har lyckats skickas MQTT CONNECT Control-paketet via TLS.</span><span class="sxs-lookup"><span data-stu-id="c7254-248">Once the TLS handshake is successful, the MQTT CONNECT control packet is sent via TLS.</span></span>

<span data-ttu-id="c7254-249">För att säkra anslutningar måste NetX Secure TLS-biblioteket vara tillgängligt och NetX Duo MQTT-klienten måste ha skapats med ***NX_SECURE_ENABLE*** definierat.</span><span class="sxs-lookup"><span data-stu-id="c7254-249">To make secure connections, the NetX Secure TLS library must be available, and the NetX Duo MQTT client must be built with ***NX_SECURE_ENABLE*** defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c7254-250">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-250">Input Parameters</span></span>

- <span data-ttu-id="c7254-251">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-251">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="c7254-252">**server_ip** IP-adress för Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-252">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="c7254-253">**SERVER_PORT** Port nummer för Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-253">**server_port** Broker port number.</span></span> <span data-ttu-id="c7254-254">Standard porten för MQTT isdefined som **_NXD_MQTT_TLS_PORT_** (8883).</span><span class="sxs-lookup"><span data-stu-id="c7254-254">The default port for MQTT isdefined as **_NXD_MQTT_TLS_PORT_** (8883).</span></span>
- <span data-ttu-id="c7254-255">**tls_setup** Funktion för motringning av användar angiven TLS-installation.</span><span class="sxs-lookup"><span data-stu-id="c7254-255">**tls_setup** User-provided TLS Setup callback function.</span></span> <span data-ttu-id="c7254-256">Denna callback-funktion anropas för att konfigurera anslutnings parametrar för TLS-klienten.</span><span class="sxs-lookup"><span data-stu-id="c7254-256">This callback function is invoked to set up TLS client connection parameters.</span></span>
- <span data-ttu-id="c7254-257">**KEEP_ALIVE** Det Keep-Alive-värde som ska användas under sessionen.</span><span class="sxs-lookup"><span data-stu-id="c7254-257">**keep_alive** The keep-alive value to be used during the session.</span></span> <span data-ttu-id="c7254-258">Värdet 0 stänger av Keep-Alive-funktionen.</span><span class="sxs-lookup"><span data-stu-id="c7254-258">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="c7254-259">**clean_session** Om servern ska starta den här sessionen rensa.</span><span class="sxs-lookup"><span data-stu-id="c7254-259">**clean_session** Whether or not the server shall start this session clean.</span></span> <span data-ttu-id="c7254-260">Giltiga alternativ är **_NX_TRUE_*_ eller _*_NX_FALSE._**</span><span class="sxs-lookup"><span data-stu-id="c7254-260">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="c7254-261">**wait_option** Vänte tid för anslutning.</span><span class="sxs-lookup"><span data-stu-id="c7254-261">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7254-262">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-262">Return Values</span></span>

- <span data-ttu-id="c7254-263">**NXD_MQTT_SUCCESS** (0X00) lyckad MQTT-klient anslutning upprättad via TLS.</span><span class="sxs-lookup"><span data-stu-id="c7254-263">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT client connection established via TLS.</span></span>
- <span data-ttu-id="c7254-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) klienten är redan ansluten till Service Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="c7254-265">**NXD_MQTT_MUTEX_FAILURE** (0X10003) Det gick inte att hämta MQTT MUTEX</span><span class="sxs-lookup"><span data-stu-id="c7254-265">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="c7254-266">Internt **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel</span><span class="sxs-lookup"><span data-stu-id="c7254-266">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="c7254-267">**NXD_MQTT_CONNECT_FAILURE** (0X10005) Det gick inte att ansluta till Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-267">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="c7254-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) Det gick inte att skicka meddelanden till Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="c7254-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** -servern (0x10008) svarade med fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="c7254-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error message.</span></span>
- <span data-ttu-id="c7254-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0X10081) Server svars kod</span><span class="sxs-lookup"><span data-stu-id="c7254-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="c7254-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0X10082) Server svars kod</span><span class="sxs-lookup"><span data-stu-id="c7254-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="c7254-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0X10083) Server svars kod</span><span class="sxs-lookup"><span data-stu-id="c7254-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="c7254-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0X10084) Server svars kod</span><span class="sxs-lookup"><span data-stu-id="c7254-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="c7254-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0X10085) Server svars kod</span><span class="sxs-lookup"><span data-stu-id="c7254-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="c7254-275">NX_PTR_ERROR (0x07) ogiltigt MQTT-kontroll block eller server struktur.</span><span class="sxs-lookup"><span data-stu-id="c7254-275">NX_PTR_ERROR (0x07) Invalid MQTT control block or sever address structure.</span></span>
- <span data-ttu-id="c7254-276">NX_INVALID_PORTs server port (0x46) kan inte vara 0.</span><span class="sxs-lookup"><span data-stu-id="c7254-276">NX_INVALID_PORT (0x46) Server port cannot be 0.</span></span>
- <span data-ttu-id="c7254-277">Fel i indataparametern NXD_MQTT_INVALID_PARAMETER (0x10009)</span><span class="sxs-lookup"><span data-stu-id="c7254-277">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>
- <span data-ttu-id="c7254-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT tråden har inte startats än.</span><span class="sxs-lookup"><span data-stu-id="c7254-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT Thread has not started running yet.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-279">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-279">Allowed From</span></span>

<span data-ttu-id="c7254-280">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-281">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-281">Example</span></span>

```c
/* TLS setup routine. This function is responsible for setting up TLS parameters.*/
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate,
    UINT timeout)
{
/* Note this routine is simplified to highlight the
necessary steps to setup a TLS session. Each
application may employ different procedures suitable for
its TLS settings, such as cipher suite, certificates. */

/* Create a TLS session for the MQTT connection, and pass
in various crypto methods this session can use for the
initial TLS handshake. */

/* Load appropriate certificates, or set up session key for Pre-share key operation. */

/* Start the TLS session */

/* Return NX_SUCCESS if the TLS session is established. */
    return(NX_SUCCESS);
}

NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_secure_connect(&my_client,
    &server_address, NXD_MQTT_TLS_PORT, tls_setup_callback,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the MQTT Client was successfully connected to the broker via TLS. */
```

## <a name="nxd_mqtt_client_publish"></a><span data-ttu-id="c7254-282">nxd_mqtt_client_publish</span><span class="sxs-lookup"><span data-stu-id="c7254-282">nxd_mqtt_client_publish</span></span>

<span data-ttu-id="c7254-283">Publicera ett meddelande via Service Broker</span><span class="sxs-lookup"><span data-stu-id="c7254-283">Publish a message through the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-284">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-284">Prototype</span></span>

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a><span data-ttu-id="c7254-285">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-285">Description</span></span>

<span data-ttu-id="c7254-286">Den här tjänsten publicerar ett meddelande via Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-286">This service publishes a message through the broker.</span></span> <span data-ttu-id="c7254-287">Publicering av QoS-nivå 2-meddelanden stöds inte ännu.</span><span class="sxs-lookup"><span data-stu-id="c7254-287">Publishing QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c7254-288">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-288">Input Parameters</span></span>

- <span data-ttu-id="c7254-289">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-289">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="c7254-290">**topic_name** Ämne att publicera till.</span><span class="sxs-lookup"><span data-stu-id="c7254-290">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="c7254-291">**topic_name_length** Längden på ämnet i byte.</span><span class="sxs-lookup"><span data-stu-id="c7254-291">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="c7254-292">**meddelande** Pekar på meddelande bufferten.</span><span class="sxs-lookup"><span data-stu-id="c7254-292">**message** Pointer to the message buffer.</span></span>
- <span data-ttu-id="c7254-293">**message_length** Meddelandets storlek i byte</span><span class="sxs-lookup"><span data-stu-id="c7254-293">**message_length** Size of the message, in bytes</span></span>
- <span data-ttu-id="c7254-294">**Behåll** Bestämmer om Broker ska behålla meddelandet.</span><span class="sxs-lookup"><span data-stu-id="c7254-294">**retain** Determines if the broker shall retain the message.</span></span>
- <span data-ttu-id="c7254-295">**QoS** Önskat QoS-värde: 0 eller 1.</span><span class="sxs-lookup"><span data-stu-id="c7254-295">**QoS** The desired QoS value: 0 or 1.</span></span>
- <span data-ttu-id="c7254-296">**tids gräns** Tids gräns värde</span><span class="sxs-lookup"><span data-stu-id="c7254-296">**timeout** Timeout value</span></span>

### <a name="return-values"></a><span data-ttu-id="c7254-297">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-297">Return Values</span></span>

- <span data-ttu-id="c7254-298">**NXD_MQTT_SUCCESS** (0X00) lyckad MQTT-klient skapa</span><span class="sxs-lookup"><span data-stu-id="c7254-298">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT Client create</span></span>
- <span data-ttu-id="c7254-299">**NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel.</span><span class="sxs-lookup"><span data-stu-id="c7254-299">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error.</span></span>
- <span data-ttu-id="c7254-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0X10006) Det gick inte att hämta paket från mediepoolen.</span><span class="sxs-lookup"><span data-stu-id="c7254-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) Failed to obtain packet from the packet pool.</span></span>
- <span data-ttu-id="c7254-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) Det gick inte att kommunicera med Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Failed to communication with the broker.</span></span>
- <span data-ttu-id="c7254-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0X1000C) QoS-nivå 2-meddelanden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="c7254-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="c7254-303">NX_PTR_ERROR (0x07) ogiltigt MQTT kontroll block, ip_ptr eller Packet pool pekare</span><span class="sxs-lookup"><span data-stu-id="c7254-303">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="c7254-304">Fel i indataparametern NXD_MQTT_INVALID_PARAMETER (0x10009)</span><span class="sxs-lookup"><span data-stu-id="c7254-304">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-305">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-305">Allowed From</span></span>

<span data-ttu-id="c7254-306">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-307">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-307">Example</span></span>

```c
CHAR *topic = "temperature";
CHAR *message = "100";

/* Publish the temperature value. */
status = nxd_mqtt_client_publish(&my_client,
    topic, STRLEN(topic),
    message, STRLEN(message),
    NX_TRUE, /* Server retains message. */);
    0, /* QOS */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the message has been 
successfully sent to the broker. */
```

## <a name="nxd_mqtt_client_subscribe"></a><span data-ttu-id="c7254-308">nxd_mqtt_client_subscribe</span><span class="sxs-lookup"><span data-stu-id="c7254-308">nxd_mqtt_client_subscribe</span></span>

<span data-ttu-id="c7254-309">Prenumerera på ett ämne</span><span class="sxs-lookup"><span data-stu-id="c7254-309">Subscribe to a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-310">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-310">Prototype</span></span>

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a><span data-ttu-id="c7254-311">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-311">Description</span></span>

<span data-ttu-id="c7254-312">Den här tjänsten prenumererar på ett speciellt ämne.</span><span class="sxs-lookup"><span data-stu-id="c7254-312">This service subscribes to a specific topic.</span></span> <span data-ttu-id="c7254-313">Det finns inte stöd för att prenumerera på QoS-nivå 2-meddelanden ännu.</span><span class="sxs-lookup"><span data-stu-id="c7254-313">Subscribing to QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c7254-314">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-314">Input Parameters</span></span>

- <span data-ttu-id="c7254-315">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-315">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="c7254-316">**topic_name** Ämne att publicera till.</span><span class="sxs-lookup"><span data-stu-id="c7254-316">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="c7254-317">**topic_name_length** Längden på ämnet i byte.</span><span class="sxs-lookup"><span data-stu-id="c7254-317">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="c7254-318">**QoS den önskade QoS-nivån:** 0 eller 1.</span><span class="sxs-lookup"><span data-stu-id="c7254-318">**QoS The desired QoS level:** 0 or 1.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7254-319">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-319">Return Values</span></span>

- <span data-ttu-id="c7254-320">**NXD_MQTT_SUCCESS** (0X00) har prenumererat på avsnittet.</span><span class="sxs-lookup"><span data-stu-id="c7254-320">**NXD_MQTT_SUCCESS** (0x00) Successfully subscribed to the topic.</span></span>
- <span data-ttu-id="c7254-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) klienten är inte ansluten till Service Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="c7254-322">**NXD_MQTT_MUTEX_FAILURE** (0X10003) Det gick inte att hämta MQTT MUTEX</span><span class="sxs-lookup"><span data-stu-id="c7254-322">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span>
- <span data-ttu-id="c7254-323">Internt **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel</span><span class="sxs-lookup"><span data-stu-id="c7254-323">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="c7254-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) Det gick inte att skicka meddelanden till Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="c7254-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) 2Messages för QoS-nivå stöds inte.</span><span class="sxs-lookup"><span data-stu-id="c7254-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2messages are not supported.</span></span>
- <span data-ttu-id="c7254-326">NX_PTR_ERROR (0x07) ogiltigt MQTT kontroll block, ip_ptr eller Packet pool pekare</span><span class="sxs-lookup"><span data-stu-id="c7254-326">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="c7254-327">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name har inte angetts, eller topic_name_length är noll eller så är QoS-värdet ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="c7254-327">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero, or QoS is value is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-328">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-328">Allowed From</span></span>

<span data-ttu-id="c7254-329">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-330">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-330">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a><span data-ttu-id="c7254-331">nxd_mqtt_client_unsubscribe</span><span class="sxs-lookup"><span data-stu-id="c7254-331">nxd_mqtt_client_unsubscribe</span></span>

<span data-ttu-id="c7254-332">Avbryta prenumerationen på ett ämne</span><span class="sxs-lookup"><span data-stu-id="c7254-332">Unsubscribe from a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-333">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-333">Prototype</span></span>

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a><span data-ttu-id="c7254-334">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-334">Description</span></span>

<span data-ttu-id="c7254-335">Den här tjänsten avbryter prenumerationen på ett ämne.</span><span class="sxs-lookup"><span data-stu-id="c7254-335">This service unsubscribes from a topic.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c7254-336">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-336">Input Parameters</span></span>

- <span data-ttu-id="c7254-337">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-337">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="c7254-338">**topic_name** För att avbryta prenumerationen på.</span><span class="sxs-lookup"><span data-stu-id="c7254-338">**topic_name** Topic to unsubscribe from.</span></span>
- <span data-ttu-id="c7254-339">**topic_name_length** Längden på ämnet i byte.</span><span class="sxs-lookup"><span data-stu-id="c7254-339">**topic_name_length** Length of the topic, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7254-340">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-340">Return Values</span></span>

- <span data-ttu-id="c7254-341">**NXD_MQTT_SUCCESS** (0X00) har avbrutit prenumerationen från ämnet.</span><span class="sxs-lookup"><span data-stu-id="c7254-341">**NXD_MQTT_SUCCESS** (0x00) Successfully unsubscribed from the topic.</span></span>
- <span data-ttu-id="c7254-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) klienten är inte ansluten till Service Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="c7254-343">**NXD_MQTT_MUTEX_FAILURE** (0X10003) Det gick inte att hämta MQTT MUTEX.</span><span class="sxs-lookup"><span data-stu-id="c7254-343">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="c7254-344">Internt **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel</span><span class="sxs-lookup"><span data-stu-id="c7254-344">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="c7254-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) Det gick inte att skicka meddelanden till Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="c7254-346">NX_PTR_ERROR (0x07) ogiltig MQTT Control Block-pekare</span><span class="sxs-lookup"><span data-stu-id="c7254-346">NX_PTR_ERROR (0x07) Invalid MQTT control block pointer</span></span>
- <span data-ttu-id="c7254-347">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name har inte angetts eller topic_name_length är noll.</span><span class="sxs-lookup"><span data-stu-id="c7254-347">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-348">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-348">Allowed From</span></span>

<span data-ttu-id="c7254-349">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-350">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-350">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a><span data-ttu-id="c7254-351">nxd_mqtt_client_receive_notify_set</span><span class="sxs-lookup"><span data-stu-id="c7254-351">nxd_mqtt_client_receive_notify_set</span></span>

<span data-ttu-id="c7254-352">Ställ in MQTT Message Receive motringning funktion</span><span class="sxs-lookup"><span data-stu-id="c7254-352">Set MQTT message receive notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-353">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-353">Prototype</span></span>

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a><span data-ttu-id="c7254-354">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-354">Description</span></span>

<span data-ttu-id="c7254-355">Den här tjänsten registrerar en callback-funktion med MQTT-klienten.</span><span class="sxs-lookup"><span data-stu-id="c7254-355">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="c7254-356">När du tar emot ett meddelande som publicerats av Broker, lagrar MQTT-klienten meddelandet i mottagnings kön.</span><span class="sxs-lookup"><span data-stu-id="c7254-356">Upon receiving a message published by the broker, MQTT client stores the message in the receive queue.</span></span> <span data-ttu-id="c7254-357">Om motringningsfunktionen är inställt anropas funktionen motringning för att meddela programmet att ett meddelande är klart att hämtas.</span><span class="sxs-lookup"><span data-stu-id="c7254-357">If the callback function is set, the callback function is invoked to notify the application that a message is ready to be retrieved.</span></span> <span data-ttu-id="c7254-358">Funktionen Receive notify tar en pekare till klient kontroll blocket MQTT och ett *message_count* som anger antalet meddelanden som är tillgängliga i mottagnings kön.</span><span class="sxs-lookup"><span data-stu-id="c7254-358">The receive notify function takes a pointer to the MQTT client control block, and a *message_count* indicating the number of messages available in the receive queue.</span></span> <span data-ttu-id="c7254-359">Observera att antalet kan ändras mellan mottagnings meddelandet och när programmet hämtar dessa meddelanden, eftersom nya meddelanden kan ha anlänt i intervallet.</span><span class="sxs-lookup"><span data-stu-id="c7254-359">Note that the number may change between the receive notification and when the application retrieves these messages, as new messages may have arrived in the interval.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c7254-360">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-360">Input Parameters</span></span>

- <span data-ttu-id="c7254-361">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-361">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="c7254-362">**receive_notify** Användaren har angett återanrops funktion som ska anropas vid mottagning av ett meddelande.</span><span class="sxs-lookup"><span data-stu-id="c7254-362">**receive_notify** User supplied callback function to be invoked on receiving a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7254-363">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-363">Return Values</span></span>

- <span data-ttu-id="c7254-364">**NXD_MQTT_SUCCESS** (0X00) har angett funktionen Receive notify.</span><span class="sxs-lookup"><span data-stu-id="c7254-364">**NXD_MQTT_SUCCESS** (0x00) Successfully set the receive notify function.</span></span>
- <span data-ttu-id="c7254-365">NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block.</span><span class="sxs-lookup"><span data-stu-id="c7254-365">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-366">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-366">Allowed From</span></span>

<span data-ttu-id="c7254-367">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-368">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-368">Example</span></span>

```c
/* Sample MQTT receive notify function. */

VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count)
{

/* On receiving a message, set an event flag to wake up the
application thread. The message will be received and
processed in the application thread. */
tx_event_flags_set(&mqtt_app_flag,
    MESSAGE_RECEIVED_EVENT, TX_OR);

/* All done. Return to the caller. */
    return;
}

/* Set the receive callback function. */
status = **nxd_mqtt_client_receive_notify_set**(&my_client,
    my_notify_func);

/* If status is NXD_MQTT_SUCCESS the notify function is properly set. */
```

## <a name="nxd_mqtt_client_message_get"></a><span data-ttu-id="c7254-369">nxd_mqtt_client_message_get</span><span class="sxs-lookup"><span data-stu-id="c7254-369">nxd_mqtt_client_message_get</span></span>

<span data-ttu-id="c7254-370">Hämta ett meddelande från Service Broker</span><span class="sxs-lookup"><span data-stu-id="c7254-370">Retrieve a message from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-371">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-371">Prototype</span></span>

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a><span data-ttu-id="c7254-372">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-372">Description</span></span>

<span data-ttu-id="c7254-373">Den här tjänsten hämtar ett meddelande som publicerats av Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-373">This service retrieves a message published by the broker.</span></span> <span data-ttu-id="c7254-374">Alla inkommande meddelanden lagras i mottagnings kön.</span><span class="sxs-lookup"><span data-stu-id="c7254-374">All incoming messages are stored in the receive queue.</span></span> <span data-ttu-id="c7254-375">Programmet använder den här tjänsten för att hämta dessa meddelanden.</span><span class="sxs-lookup"><span data-stu-id="c7254-375">The application uses this service to retrieve these messages.</span></span> <span data-ttu-id="c7254-376">Anropet är inte blockerande.</span><span class="sxs-lookup"><span data-stu-id="c7254-376">This call is non-blocking.</span></span> <span data-ttu-id="c7254-377">Om mottagnings kön är tom returnerar den här tjänsten \***NXD_MQTT_NO_MESSAGE** _.</span><span class="sxs-lookup"><span data-stu-id="c7254-377">If the receive queue is empty, this service returns \***NXD_MQTT_NO_MESSAGE** _.</span></span> <span data-ttu-id="c7254-378">Ett program som vill meddelas om inkommande meddelande kan anropa tjänsten _ *_nxd_mqtt_client_receive_notify_set_*\* för att registrera en Receive callback-funktion.</span><span class="sxs-lookup"><span data-stu-id="c7254-378">An application wishing to be notified of incoming message can call the service _ *_nxd_mqtt_client_receive_notify_set_*\* to register a receive callback function.</span></span>

<span data-ttu-id="c7254-379">Anroparen måste tillhandahålla minnes utrymme för ämnes strängen och meddelande texten.</span><span class="sxs-lookup"><span data-stu-id="c7254-379">The caller needs to provide memory space for the topic string and the message body.</span></span> <span data-ttu-id="c7254-380">Storlekarna på de här två buffertarna skickas med hjälp av *topic_buffer_size* och *message_buffer_size*.</span><span class="sxs-lookup"><span data-stu-id="c7254-380">The sizes of these two buffers are passed in using *topic_buffer_size* and *message_buffer_size*.</span></span> <span data-ttu-id="c7254-381">Det faktiska antalet byte i ämnes strängen och meddelande texten returneras i *actual_topic_length* och *actual_message_length*.</span><span class="sxs-lookup"><span data-stu-id="c7254-381">The actual number of bytes in the topic string and the message body are returned in *actual_topic_length* and *actual_message_length*.</span></span> <span data-ttu-id="c7254-382">Om ämnes längden eller massage längden är större än det angivna buffertutrymme returnerar den här tjänsten felkoden *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.</span><span class="sxs-lookup"><span data-stu-id="c7254-382">If topic length or massage length is greater than the buffer space provided, this service returns error code *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.</span></span>

<span data-ttu-id="c7254-383">Programmet ska allokera en större buffert och försöka igen.</span><span class="sxs-lookup"><span data-stu-id="c7254-383">The application shall allocate a bigger buffer and try again.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c7254-384">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-384">Input Parameters</span></span>

- <span data-ttu-id="c7254-385">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-385">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="c7254-386">**topic_buffer** Pekar på den minnes plats där ämnes strängen kopieras till.</span><span class="sxs-lookup"><span data-stu-id="c7254-386">**topic_buffer** Pointer to the memory location where the topic string is copied into.</span></span>
- <span data-ttu-id="c7254-387">**topic_buffer_size** Storlek på ämnes bufferten.</span><span class="sxs-lookup"><span data-stu-id="c7254-387">**topic_buffer_size** Size of the topic buffer.</span></span>
- <span data-ttu-id="c7254-388">**actual_topic_length** Pekar till den minnes plats där den faktiska ämnes längden returneras.</span><span class="sxs-lookup"><span data-stu-id="c7254-388">**actual_topic_length** Pointer to the memory location where the actual topic length is returned.</span></span>
- <span data-ttu-id="c7254-389">**message_buffer** Pekar på den minnes plats där meddelande strängen kopieras till.</span><span class="sxs-lookup"><span data-stu-id="c7254-389">**message_buffer** Pointer to the memory location where the message string is copied into.</span></span>
- <span data-ttu-id="c7254-390">**message_buffer_size** Storlek på meddelande bufferten.</span><span class="sxs-lookup"><span data-stu-id="c7254-390">**message_buffer_size** Size of the message buffer.</span></span>
- <span data-ttu-id="c7254-391">**actual_message_length** Pekar till den minnes plats där meddelande längden returneras.</span><span class="sxs-lookup"><span data-stu-id="c7254-391">**actual_message_length** Pointer to the memory location where the message length is returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7254-392">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-392">Return Values</span></span>

- <span data-ttu-id="c7254-393">Ett meddelande har hämtats **NXD_MQTT_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="c7254-393">**NXD_MQTT_SUCCESS** (0x00) Successfully retrieved message.</span></span>
- <span data-ttu-id="c7254-394">Internt **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel</span><span class="sxs-lookup"><span data-stu-id="c7254-394">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="c7254-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) mottagnings kön är tom.</span><span class="sxs-lookup"><span data-stu-id="c7254-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) The receive queue is empty.</span></span>
- <span data-ttu-id="c7254-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D), delbufferten eller meddelande bufferten är för liten för ämnet eller meddelandet.</span><span class="sxs-lookup"><span data-stu-id="c7254-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) Topic buffer or message buffer is too small for the topic or the message.</span></span>
- <span data-ttu-id="c7254-397">NX_PTR_ERROR (0x07) ogiltigt MQTT kontroll block, ip_ptr eller Packet pool pekare</span><span class="sxs-lookup"><span data-stu-id="c7254-397">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="c7254-398">NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer eller topic_buffer pekare är NULL</span><span class="sxs-lookup"><span data-stu-id="c7254-398">NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer or topic_buffer pointer is NULL</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-399">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-399">Allowed From</span></span>

<span data-ttu-id="c7254-400">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-401">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-401">Example</span></span>

```c
UCHAR topic[MAX_TOPIC_SIZE];
UCHAR message[MAX_TOPIC_SIZE];
UINT topic_length;
UINT message_length;

/* Retrieve a message from MQTT client receive queue. */
status = nxd_mqtt_client_message_get(&my_client, topic,
    sizeof(topic), &topic_length, message, sizeof(message),
    &message_length);

/* Check the return value. */
if(status == NXD_MQTT_SUCCESS)
{
/* A message is received. All done. */
}
else if (status == NXD_MQTT_NO_MESSAGE)
{
/* No more messages in the receive queue. All done. */
}
else
{
/* Receive error. */
}
```

## <a name="nxd_mqtt_client_disconnect_notify_set"></a><span data-ttu-id="c7254-402">nxd_mqtt_client_disconnect_notify_set</span><span class="sxs-lookup"><span data-stu-id="c7254-402">nxd_mqtt_client_disconnect_notify_set</span></span>

<span data-ttu-id="c7254-403">Ange MQTT Message koppla från meddela motringning funktion</span><span class="sxs-lookup"><span data-stu-id="c7254-403">Set MQTT message disconnect notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-404">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-404">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a><span data-ttu-id="c7254-405">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-405">Description</span></span>

<span data-ttu-id="c7254-406">Den här tjänsten registrerar en callback-funktion med MQTT-klienten.</span><span class="sxs-lookup"><span data-stu-id="c7254-406">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="c7254-407">När MQTT upptäcker att anslutningen till Broker förloras, anropas den här meddelande funktionen för att varna programmet.</span><span class="sxs-lookup"><span data-stu-id="c7254-407">When MQTT detects the connection to the broker is lost, it calls this notify function to alert the application.</span></span> <span data-ttu-id="c7254-408">Programmet kan därför använda denna callback-funktion för att identifiera en förlorad anslutning och för att kunna återupprätta anslutningen till koordinatorn igen.</span><span class="sxs-lookup"><span data-stu-id="c7254-408">Therefore, the application can use this callback function to detect a lost connection, and to be able to re-establish connection to the broker.</span></span>

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a><span data-ttu-id="c7254-409">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-409">Input Parameters</span></span>

- <span data-ttu-id="c7254-410">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-410">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="c7254-411">**disconnect_notify** Användaren har angett callback-funktionen som ska anropas när MQTT identifierar anslutningen till Broker förloras.</span><span class="sxs-lookup"><span data-stu-id="c7254-411">**disconnect_notify** User supplied callback function to be invoked when MQTT detects the connection to the broker is lost.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7254-412">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-412">Return Values</span></span>

- <span data-ttu-id="c7254-413">**NXD_MQTT_SUCCESS** (0X00) har ställt in funktionen för att koppla från meddelande.</span><span class="sxs-lookup"><span data-stu-id="c7254-413">**NXD_MQTT_SUCCESS** (0x00) Successfully set the disconnect notify function.</span></span>
- <span data-ttu-id="c7254-414">NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block.</span><span class="sxs-lookup"><span data-stu-id="c7254-414">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-415">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-415">Allowed From</span></span>

<span data-ttu-id="c7254-416">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-417">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-417">Example</span></span>

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a><span data-ttu-id="c7254-418">nxd_mqtt_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="c7254-418">nxd_mqtt_client_disconnect</span></span>

<span data-ttu-id="c7254-419">Koppla från MQTT-klienten från Broker</span><span class="sxs-lookup"><span data-stu-id="c7254-419">Disconnect MQTT client from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-420">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-420">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="c7254-421">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-421">Description</span></span>

<span data-ttu-id="c7254-422">Den här tjänsten kopplar från klienten från Broker.</span><span class="sxs-lookup"><span data-stu-id="c7254-422">This service disconnects the client from the broker.</span></span> <span data-ttu-id="c7254-423">Observera att meddelanden i mottagnings kön släpps.</span><span class="sxs-lookup"><span data-stu-id="c7254-423">Note that messages on the receive queue are released.</span></span> <span data-ttu-id="c7254-424">Meddelanden med QoS 1 i överförings kön släpps inte.</span><span class="sxs-lookup"><span data-stu-id="c7254-424">Messages with QoS 1 in the transmit queue are not released.</span></span> <span data-ttu-id="c7254-425">När klienten återansluter till servern kan QoS 1-meddelanden bearbetas, såvida inte klienten återansluter till servern med *clean_session* flagga inställd på ***NX_TRUE***.</span><span class="sxs-lookup"><span data-stu-id="c7254-425">After the client reconnects to the server, QoS 1 messages can be processed, unless the client reconnects to the server with *clean_session* flag set to ***NX_TRUE***.</span></span>

<span data-ttu-id="c7254-426">Om anslutningen har gjorts med TLS-säkerhetsskydd stänger den här tjänsten TLS-sessionen innan du kopplar från TCP-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="c7254-426">If the connection was made with TLS security protection, this service will close the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="c7254-427">Det faktiska anropet från TCP-socketen har ett vänte alternativ som definieras av NXD_MQTT_SOCKET_TIMEOUT (timer Tick).</span><span class="sxs-lookup"><span data-stu-id="c7254-427">The actual TCP socket disconnect call has a wait option defined by NXD_MQTT_SOCKET_TIMEOUT (timer ticks).</span></span> <span data-ttu-id="c7254-428">Standardvärdet är NX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="c7254-428">The default value is NX_WAIT_FOREVER.</span></span> <span data-ttu-id="c7254-429">För att undvika obestämd avstängning i händelse av att nätverks anslutningen tappas bort eller servern inte svarar anger du det här alternativet till ett ändligt värde.</span><span class="sxs-lookup"><span data-stu-id="c7254-429">To avoid indefinite suspension in the event that the network connection is lost or the server is not responding, set this option to a finite value.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c7254-430">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-430">Input Parameters</span></span>

- <span data-ttu-id="c7254-431">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-431">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7254-432">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-432">Return Values</span></span>

- <span data-ttu-id="c7254-433">**NXD_MQTT_SUCCESS** (0X00) har frånkopplats från Broker</span><span class="sxs-lookup"><span data-stu-id="c7254-433">**NXD_MQTT_SUCCESS** (0x00) Successfully disconnected from broker</span></span>
- <span data-ttu-id="c7254-434">**NXD_MQTT_MUTEX_FAILURE** (0X10003) Det gick inte att hämta MQTT MUTEX.</span><span class="sxs-lookup"><span data-stu-id="c7254-434">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="c7254-435">NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block</span><span class="sxs-lookup"><span data-stu-id="c7254-435">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-436">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-436">Allowed From</span></span>

<span data-ttu-id="c7254-437">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-438">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-438">Example</span></span>

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a><span data-ttu-id="c7254-439">nxd_mqtt_client_delete</span><span class="sxs-lookup"><span data-stu-id="c7254-439">nxd_mqtt_client_delete</span></span>

<span data-ttu-id="c7254-440">Ta bort klient instansen MQTT</span><span class="sxs-lookup"><span data-stu-id="c7254-440">Delete the MQTT client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c7254-441">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c7254-441">Prototype</span></span>

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="c7254-442">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7254-442">Description</span></span>

<span data-ttu-id="c7254-443">Den här tjänsten tar bort MQTT-klient instansen och frigör interna resurser.</span><span class="sxs-lookup"><span data-stu-id="c7254-443">This service deletes the MQTT client instance and releases internal resources.</span></span> <span data-ttu-id="c7254-444">Den här tjänsten kopplar automatiskt bort klienten från Service Broker om den fortfarande är ansluten.</span><span class="sxs-lookup"><span data-stu-id="c7254-444">This service automatically disconnects the client from the broker if it is still connected.</span></span> <span data-ttu-id="c7254-445">Meddelanden som inte har skickats eller som inte har godkänts har frigjorts.</span><span class="sxs-lookup"><span data-stu-id="c7254-445">Messages not yet transmitted or not been acknowledged are released.</span></span> <span data-ttu-id="c7254-446">Meddelanden som mottagits men inte hämtats av programmet släpps också.</span><span class="sxs-lookup"><span data-stu-id="c7254-446">Messages received but not retrieved by the application are also released.</span></span>

<span data-ttu-id="c7254-447">Om anslutningen gjordes med TLS-säkerhetsskydd stänger den här tjänsten TLS-sessionen innan du kopplar bort TCP-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="c7254-447">If the connection was made with TLS security protection, this service closes the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="c7254-448">När klienten har tagits bort måste ett program som vill använda MQTT-tjänsten skapa en ny instans.</span><span class="sxs-lookup"><span data-stu-id="c7254-448">After the client is deleted, an application wishing to use MQTT service needs to create a new instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c7254-449">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="c7254-449">Input Parameters</span></span>

- <span data-ttu-id="c7254-450">**client_ptr** Pekare till MQTT klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c7254-450">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7254-451">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c7254-451">Return Values</span></span>

- <span data-ttu-id="c7254-452">**NXD_MQTT_SUCCESS** (0X00) har tagit bort MQTT-klienten.</span><span class="sxs-lookup"><span data-stu-id="c7254-452">**NXD_MQTT_SUCCESS** (0x00) Successfully deleted MQTT client.</span></span>
- <span data-ttu-id="c7254-453">NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block</span><span class="sxs-lookup"><span data-stu-id="c7254-453">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c7254-454">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="c7254-454">Allowed From</span></span>

<span data-ttu-id="c7254-455">Konversation</span><span class="sxs-lookup"><span data-stu-id="c7254-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c7254-456">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7254-456">Example</span></span>

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
