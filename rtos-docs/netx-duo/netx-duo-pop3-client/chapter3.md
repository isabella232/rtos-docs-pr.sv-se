---
title: Kapitel 3 – Beskrivning av POP3-klient tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo POP3-klient tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f7681c8f3fe161db8a37a82574ab7d5e9bf348e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825842"
---
# <a name="chapter-3---description-of-pop3-client-services"></a><span data-ttu-id="dc5b3-103">Kapitel 3 – Beskrivning av POP3-klient tjänster</span><span class="sxs-lookup"><span data-stu-id="dc5b3-103">Chapter 3 - Description of POP3 Client Services</span></span>

<span data-ttu-id="dc5b3-104">Det här kapitlet innehåller en beskrivning av alla NetX Duo POP3-klient tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-104">This chapter contains a description of all NetX Duo POP3 Client services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="dc5b3-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="dc5b3-106">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="dc5b3-106">nx_pop3_client_create</span></span>

<span data-ttu-id="dc5b3-107">Skapa en POP3-klient instans för IPv4</span><span class="sxs-lookup"><span data-stu-id="dc5b3-107">Create a POP3 Client instance for IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="dc5b3-108">Prototyp</span><span class="sxs-lookup"><span data-stu-id="dc5b3-108">Prototype</span></span>

```C
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address, ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="dc5b3-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dc5b3-109">Description</span></span>

<span data-ttu-id="dc5b3-110">Den här tjänsten skapar en instans av POP3-klienten.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-110">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="dc5b3-111">Det stöder endast IPv4 POP3-server adresser.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-111">It supports only IPv4 POP3 server addresses.</span></span>

<span data-ttu-id="dc5b3-112">Observera att enhets programmet först måste skapa en IP-instans och en modempool för att POP3-klienten ska kunna överföra paket.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-112">Note that the device application must first create an IP instance and a packet pool for the POP3 Client to transmit packets.</span></span> <span data-ttu-id="dc5b3-113">Den här poolen skapas för användning exklusivt av POP3-klient aktiviteten eller samma modempool som används i skapandet av IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-113">This packet pool created for use exclusively by the POP3 Client task or the same packet pool used in the IP instance creation.</span></span> <span data-ttu-id="dc5b3-114">Packet-poolen kan också delas med Ethernet-drivrutinen, men detta har en nackdel med att använda stora paket pooler vars nytto Last är avsedd för att ta emot potentiellt stora paket nytto laster för POP3-klienten för att skicka relativt små POP3-meddelande paket till servern.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-114">The packet pool may also be shared with the Ethernet driver packet pool but this has the disadvantage of using large packet pools whose payload is intended for receiving potentially large packets payload for the POP3 Client to send relatively small POP3 message packets to the server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dc5b3-115">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="dc5b3-115">Input Parameters</span></span>

- <span data-ttu-id="dc5b3-116">**client_ptr** Pekare till klienten för att skapa</span><span class="sxs-lookup"><span data-stu-id="dc5b3-116">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="dc5b3-117">**APOP_authentication** Aktivera APOP-autentisering</span><span class="sxs-lookup"><span data-stu-id="dc5b3-117">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="dc5b3-118">**Ip_ptr pekare** till IP-instans</span><span class="sxs-lookup"><span data-stu-id="dc5b3-118">**ip_ptr Pointer** to IP instance</span></span>
- <span data-ttu-id="dc5b3-119">**packet_pool_ptr** Pekare till klient paketets pool</span><span class="sxs-lookup"><span data-stu-id="dc5b3-119">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="dc5b3-120">**server_ip_address** IPv4-adress för POP3-server</span><span class="sxs-lookup"><span data-stu-id="dc5b3-120">**server_ip_address** POP3 server IPv4 address</span></span>
- <span data-ttu-id="dc5b3-121">**SERVER_PORT** POP3-server port</span><span class="sxs-lookup"><span data-stu-id="dc5b3-121">**server_port** POP3 server port</span></span>
- <span data-ttu-id="dc5b3-122">**client_name** Pekare till klient namn</span><span class="sxs-lookup"><span data-stu-id="dc5b3-122">**client_name** Pointer to Client name</span></span>
- <span data-ttu-id="dc5b3-123">**client_password** Pekare till klient lösen ord</span><span class="sxs-lookup"><span data-stu-id="dc5b3-123">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="dc5b3-124">Retur värden</span><span class="sxs-lookup"><span data-stu-id="dc5b3-124">Return Values</span></span>

- <span data-ttu-id="dc5b3-125">**NX_SUCCESS** (0x00)-klienten har skapats</span><span class="sxs-lookup"><span data-stu-id="dc5b3-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="dc5b3-126">**status** Status för slut för ande av NetX Duo-och ThreadX service-anrop</span><span class="sxs-lookup"><span data-stu-id="dc5b3-126">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="dc5b3-127">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="dc5b3-127">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="dc5b3-128">NX_POP3_PARAM_ERROR (0xB1) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="dc5b3-128">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dc5b3-129">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="dc5b3-129">Allowed From</span></span>

<span data-ttu-id="dc5b3-130">Program kod</span><span class="sxs-lookup"><span data-stu-id="dc5b3-130">Application code</span></span>

### <a name="example"></a><span data-ttu-id="dc5b3-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="dc5b3-131">Example</span></span>

```C
/* Create the POP3 Client. Note that the Client uses its password for its APOP shared
    secret. */

/* Set up user defined callback services. */
/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_ADDRESS IP_ADDRESS(192,2,2,92)
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. */
status = nx_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    POP3_SERVER_ADDRESS, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nxd_pop3_client_create"></a><span data-ttu-id="dc5b3-132">nxd_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="dc5b3-132">nxd_pop3_client_create</span></span>

<span data-ttu-id="dc5b3-133">Skapa en POP3-klient instans för IPv4 eller IPv6</span><span class="sxs-lookup"><span data-stu-id="dc5b3-133">Create a POP3 Client instance for IPv4 or IPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="dc5b3-134">Prototyp</span><span class="sxs-lookup"><span data-stu-id="dc5b3-134">Prototype</span></span>

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address,
    ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="dc5b3-135">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dc5b3-135">Description</span></span>

<span data-ttu-id="dc5b3-136">Den här tjänsten skapar en instans av POP3-klienten.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-136">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="dc5b3-137">Det stöder både IPv4-och IPv6 POP3-server adresser.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-137">It supports both IPv4 and IPv6 POP3 server addresses.</span></span> <span data-ttu-id="dc5b3-138">Se den tidigare beskrivna *nx_pop3_client_create* tjänsten för mer information om POP3-klienten skapa process.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-138">See the previously described *nx_pop3_client_create* service for more details on POP3 Client create process.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dc5b3-139">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="dc5b3-139">Input Parameters</span></span>

- <span data-ttu-id="dc5b3-140">**client_ptr** Pekare till klienten för att skapa</span><span class="sxs-lookup"><span data-stu-id="dc5b3-140">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="dc5b3-141">**APOP_authentication** Aktivera APOP-autentisering</span><span class="sxs-lookup"><span data-stu-id="dc5b3-141">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="dc5b3-142">**ip_ptr** Pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="dc5b3-142">**ip_ptr** Pointer to IP instance</span></span>
- <span data-ttu-id="dc5b3-143">**packet_pool_ptr** Pekare till klient paketets pool</span><span class="sxs-lookup"><span data-stu-id="dc5b3-143">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="dc5b3-144">**server_ip_address** POP3-serverns IPv6-eller IPv4-adress</span><span class="sxs-lookup"><span data-stu-id="dc5b3-144">**server_ip_address** POP3 server IPv6 or IPv4 address</span></span>
- <span data-ttu-id="dc5b3-145">**SERVER_PORT** POP3-server port</span><span class="sxs-lookup"><span data-stu-id="dc5b3-145">**server_port** POP3 server port</span></span>
- <span data-ttu-id="dc5b3-146">**client_name**  Pekare till klient namn</span><span class="sxs-lookup"><span data-stu-id="dc5b3-146">**client_name**  Pointer to Client name</span></span>
- <span data-ttu-id="dc5b3-147">**client_password** Pekare till klient lösen ord</span><span class="sxs-lookup"><span data-stu-id="dc5b3-147">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="dc5b3-148">Retur värden</span><span class="sxs-lookup"><span data-stu-id="dc5b3-148">Return Values</span></span>

- <span data-ttu-id="dc5b3-149">**NX_SUCCESS** (0x00)-klienten har skapats</span><span class="sxs-lookup"><span data-stu-id="dc5b3-149">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="dc5b3-150">**status** Status för slut för ande av NetX Duo-och ThreadX service-anrop</span><span class="sxs-lookup"><span data-stu-id="dc5b3-150">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="dc5b3-151">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="dc5b3-151">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="dc5b3-152">NX_POP3_PARAM_ERROR (0xB1) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="dc5b3-152">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dc5b3-153">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="dc5b3-153">Allowed From</span></span>

<span data-ttu-id="dc5b3-154">Program kod</span><span class="sxs-lookup"><span data-stu-id="dc5b3-154">Application code</span></span>

### <a name="example"></a><span data-ttu-id="dc5b3-155">Exempel</span><span class="sxs-lookup"><span data-stu-id="dc5b3-155">Example</span></span>

```C
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. Also note the details of IPv6 address validation
    and enabling IPv6 and ICMPv6 services on the IP task are not shown here. See the
    NetX Duo User Guide for more details on this process.
*/
NXD_ADDRESS server_ip_address;

/* Set client IP interface address. */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0xf101;
server_ip_address.nxd_ip_address.v6[2] = 0;
server_ip_address.nxd_ip_address.v6[3] = 0x101;
status = nxd_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    &server_ip_address, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="dc5b3-156">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="dc5b3-156">nx_pop3_client_delete</span></span>

<span data-ttu-id="dc5b3-157">Ta bort en POP3-klient instans</span><span class="sxs-lookup"><span data-stu-id="dc5b3-157">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="dc5b3-158">Prototyp</span><span class="sxs-lookup"><span data-stu-id="dc5b3-158">Prototype</span></span>

```C
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="dc5b3-159">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dc5b3-159">Description</span></span>

<span data-ttu-id="dc5b3-160">Den här tjänsten tar bort en tidigare skapad POP3-klient.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-160">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="dc5b3-161">Inte att den här tjänsten inte tar bort POP3-klientens adresspool.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-161">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="dc5b3-162">Enhets programmet måste ta bort den här resursen separat om den inte längre har använt för poolen.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-162">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dc5b3-163">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="dc5b3-163">Input Parameters</span></span>

- <span data-ttu-id="dc5b3-164">**client_ptr** Pekare till klienten som ska tas bort</span><span class="sxs-lookup"><span data-stu-id="dc5b3-164">**client_ptr** Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="dc5b3-165">Retur värden</span><span class="sxs-lookup"><span data-stu-id="dc5b3-165">Return Values</span></span>

- <span data-ttu-id="dc5b3-166">**NX_SUCCESS** (0X00) klienten har tagits bort</span><span class="sxs-lookup"><span data-stu-id="dc5b3-166">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="dc5b3-167">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="dc5b3-167">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dc5b3-168">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="dc5b3-168">Allowed From</span></span>

<span data-ttu-id="dc5b3-169">Program kod</span><span class="sxs-lookup"><span data-stu-id="dc5b3-169">Application code</span></span>

### <a name="example"></a><span data-ttu-id="dc5b3-170">Exempel</span><span class="sxs-lookup"><span data-stu-id="dc5b3-170">Example</span></span>

```C
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="dc5b3-171">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="dc5b3-171">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="dc5b3-172">Ta bort ett angivet e-postobjekt från klientens maildrop</span><span class="sxs-lookup"><span data-stu-id="dc5b3-172">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="dc5b3-173">Prototyp</span><span class="sxs-lookup"><span data-stu-id="dc5b3-173">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
    UINT mail_index);
```

### <a name="description"></a><span data-ttu-id="dc5b3-174">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dc5b3-174">Description</span></span>

<span data-ttu-id="dc5b3-175">Den här tjänsten tar bort det angivna e-postobjektet från klientens maildrop.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-175">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="dc5b3-176">Den är avsedd för när du har laddat ned e-postobjektet, även om vissa POP3-servrar kan ta bort e-postobjekten automatiskt efter att klienten har begärt</span><span class="sxs-lookup"><span data-stu-id="dc5b3-176">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dc5b3-177">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="dc5b3-177">Input Parameters</span></span>

- <span data-ttu-id="dc5b3-178">**client_ptr** Pekare till klient instans</span><span class="sxs-lookup"><span data-stu-id="dc5b3-178">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="dc5b3-179">**mail_index** Index i klientens maildrop</span><span class="sxs-lookup"><span data-stu-id="dc5b3-179">**mail_index** Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="dc5b3-180">Retur värden</span><span class="sxs-lookup"><span data-stu-id="dc5b3-180">Return Values</span></span>

- <span data-ttu-id="dc5b3-181">**NX_SUCCESS** (0X00) borttagnings förfrågan lyckades</span><span class="sxs-lookup"><span data-stu-id="dc5b3-181">**NX_SUCCESS** (0x00) Delete request successful</span></span>
- <span data-ttu-id="dc5b3-182">**NX_POP3_INVALID_MAIL_ITEM**(0XB2) ogiltigt e-postobjekts index</span><span class="sxs-lookup"><span data-stu-id="dc5b3-182">**NX_POP3_INVALID_MAIL_ITEM**(0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="dc5b3-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**(0xB6) av klient paketets nytto Last är för litet för POP3-begäran.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**(0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="dc5b3-184">**NX_POP3_SERVER_ERROR_STATUS**-Server (0xB4) svarar med fel status</span><span class="sxs-lookup"><span data-stu-id="dc5b3-184">**NX_POP3_SERVER_ERROR_STATUS**(0xB4) Server replies with error status</span></span>
- <span data-ttu-id="dc5b3-185">NX_POP3_CLIENT_INVALID_INDEX (0xB8) ogiltigt inmatade e-postindex</span><span class="sxs-lookup"><span data-stu-id="dc5b3-185">NX_POP3_CLIENT_INVALID_INDEX(0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="dc5b3-186">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="dc5b3-186">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dc5b3-187">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="dc5b3-187">Allowed From</span></span>

<span data-ttu-id="dc5b3-188">Program kod</span><span class="sxs-lookup"><span data-stu-id="dc5b3-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="dc5b3-189">Exempel</span><span class="sxs-lookup"><span data-stu-id="dc5b3-189">Example</span></span>

```C
ULONG item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status =
    NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="dc5b3-190">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="dc5b3-190">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="dc5b3-191">Hämta ett angivet e-postobjekt</span><span class="sxs-lookup"><span data-stu-id="dc5b3-191">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="dc5b3-192">Prototyp</span><span class="sxs-lookup"><span data-stu-id="dc5b3-192">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

### <a name="description"></a><span data-ttu-id="dc5b3-193">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dc5b3-193">Description</span></span>

<span data-ttu-id="dc5b3-194">Den här tjänsten gör en RETR-begäran för att hämta ett e-postobjekt från den klient maildrop som anges av index mail_item.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-194">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="dc5b3-195">När du har gjort en RETR-begäran och fått ett positivt svar från servern kan klienten börja hämta e-postmeddelandet med hjälp av tjänsten *nx_pop3_client_mail_item_message_get* .</span><span class="sxs-lookup"><span data-stu-id="dc5b3-195">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="dc5b3-196">Observera att tjänsten också tillhandahåller storleken på det begärda e-postobjektet som extraherats från Server svaret.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-196">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dc5b3-197">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="dc5b3-197">Input Parameters</span></span>

- <span data-ttu-id="dc5b3-198">**client_ptr** Pekare till klient instans</span><span class="sxs-lookup"><span data-stu-id="dc5b3-198">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="dc5b3-199">**mail_item** Index i klientens maildrop</span><span class="sxs-lookup"><span data-stu-id="dc5b3-199">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="dc5b3-200">**item_size** Pekare till storlek på e-postmeddelande</span><span class="sxs-lookup"><span data-stu-id="dc5b3-200">**item_size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="dc5b3-201">Retur värden</span><span class="sxs-lookup"><span data-stu-id="dc5b3-201">Return Values</span></span>

- <span data-ttu-id="dc5b3-202">**NX_SUCCESS** (0X00) e-postobjektet har hämtats</span><span class="sxs-lookup"><span data-stu-id="dc5b3-202">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="dc5b3-203">**NX_POP3_INVALID_MAIL_ITEM** (0XB2) ogiltigt e-postobjekts index</span><span class="sxs-lookup"><span data-stu-id="dc5b3-203">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="dc5b3-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) av klient paketets nytto Last är för litet för POP3-begäran.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="dc5b3-205">**NX_POP3_SERVER_ERROR_STATUS** -Server (0xB4) svarar med fel status</span><span class="sxs-lookup"><span data-stu-id="dc5b3-205">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="dc5b3-206">NX_POP3_CLIENT_INVALID_INDEX (0xB8) ogiltigt inmatade e-postindex</span><span class="sxs-lookup"><span data-stu-id="dc5b3-206">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="dc5b3-207">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="dc5b3-207">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dc5b3-208">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="dc5b3-208">Allowed From</span></span>

<span data-ttu-id="dc5b3-209">Program kod</span><span class="sxs-lookup"><span data-stu-id="dc5b3-209">Application code</span></span>

### <a name="example"></a><span data-ttu-id="dc5b3-210">Exempel</span><span class="sxs-lookup"><span data-stu-id="dc5b3-210">Example</span></span>

```C
ULONG item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="dc5b3-211">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="dc5b3-211">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="dc5b3-212">Hämta antalet e-postobjekt i maildrop</span><span class="sxs-lookup"><span data-stu-id="dc5b3-212">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="dc5b3-213">Prototyp</span><span class="sxs-lookup"><span data-stu-id="dc5b3-213">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items,
    ULONG *maildrop_total_size);
```

### <a name="description"></a><span data-ttu-id="dc5b3-214">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dc5b3-214">Description</span></span>

<span data-ttu-id="dc5b3-215">Den här tjänsten gör en STAT-begäran för att hämta antalet e-postobjekt och den totala storleken på e-postmeddelandets data från klientens maildrop.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-215">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dc5b3-216">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="dc5b3-216">Input Parameters</span></span>

- <span data-ttu-id="dc5b3-217">**client_ptr** Pekare till klient instans</span><span class="sxs-lookup"><span data-stu-id="dc5b3-217">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="dc5b3-218">**number_mail_item** Antal e-postmeddelanden i klient maildrop</span><span class="sxs-lookup"><span data-stu-id="dc5b3-218">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="dc5b3-219">**maildrop_total_size** Pekare till storlek på alla e-postmeddelanden</span><span class="sxs-lookup"><span data-stu-id="dc5b3-219">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="dc5b3-220">Retur värden</span><span class="sxs-lookup"><span data-stu-id="dc5b3-220">Return Values</span></span>

- <span data-ttu-id="dc5b3-221">**NX_SUCCESS** (0X00) e-postobjektet har hämtats</span><span class="sxs-lookup"><span data-stu-id="dc5b3-221">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="dc5b3-222">**NX_POP3_INVALID_MAIL_ITEM** (0XB2) ogiltigt e-postobjekts index</span><span class="sxs-lookup"><span data-stu-id="dc5b3-222">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="dc5b3-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) av klient paketets nytto Last är för litet för POP3-begäran.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="dc5b3-224">**NX_POP3_SERVER_ERROR_STATUS** -Server (0xB4) svarar med fel status</span><span class="sxs-lookup"><span data-stu-id="dc5b3-224">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="dc5b3-225">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="dc5b3-225">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dc5b3-226">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="dc5b3-226">Allowed From</span></span>

<span data-ttu-id="dc5b3-227">Program kod</span><span class="sxs-lookup"><span data-stu-id="dc5b3-227">Application code</span></span>

### <a name="example"></a><span data-ttu-id="dc5b3-228">Exempel</span><span class="sxs-lookup"><span data-stu-id="dc5b3-228">Example</span></span>

```C
UINT number_mail_items;

ULONG maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
    &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="dc5b3-229">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="dc5b3-229">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="dc5b3-230">Hämta det angivna meddelandet om e-postobjektet</span><span class="sxs-lookup"><span data-stu-id="dc5b3-230">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="dc5b3-231">Prototyp</span><span class="sxs-lookup"><span data-stu-id="dc5b3-231">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

### <a name="description"></a><span data-ttu-id="dc5b3-232">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dc5b3-232">Description</span></span>

<span data-ttu-id="dc5b3-233">Den här tjänsten hämtar e-postmeddelandets meddelande, storleken på e-postmeddelandet och om det är det sista paketet i e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-233">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="dc5b3-234">Om final_packet NX_TRUE paketet som pekas av recv_packet_ptr är det sista paketet i e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-234">If final_packet is NX_TRUE the packet pointed to by recv_packet_ptr is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dc5b3-235">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="dc5b3-235">Input Parameters</span></span>

- <span data-ttu-id="dc5b3-236">**client_ptr** Pekare till klient instans</span><span class="sxs-lookup"><span data-stu-id="dc5b3-236">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="dc5b3-237">**recv_packet_ptr** Tog emot paket med meddelande data</span><span class="sxs-lookup"><span data-stu-id="dc5b3-237">**recv_packet_ptr** Received packet of message data</span></span>
- <span data-ttu-id="dc5b3-238">**number_mail_item** Antal e-postmeddelanden i klient maildrop</span><span class="sxs-lookup"><span data-stu-id="dc5b3-238">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="dc5b3-239">**maildrop_total_size** Pekare till storlek på alla e-postmeddelanden</span><span class="sxs-lookup"><span data-stu-id="dc5b3-239">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="dc5b3-240">Retur värden</span><span class="sxs-lookup"><span data-stu-id="dc5b3-240">Return Values</span></span>

- <span data-ttu-id="dc5b3-241">**NX_SUCCESS** (0X00) e-postobjektet har hämtats</span><span class="sxs-lookup"><span data-stu-id="dc5b3-241">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="dc5b3-242">**NX_POP3_CLIENT_INVALID_STATE** (0xB7) av klient paketets nytto Last är för litet för POP3-begäran.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-242">**NX_POP3_CLIENT_INVALID_STATE** (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="dc5b3-243">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="dc5b3-243">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dc5b3-244">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="dc5b3-244">Allowed From</span></span>

<span data-ttu-id="dc5b3-245">Program kod</span><span class="sxs-lookup"><span data-stu-id="dc5b3-245">Application code</span></span>

### <a name="example"></a><span data-ttu-id="dc5b3-246">Exempel</span><span class="sxs-lookup"><span data-stu-id="dc5b3-246">Example</span></span>

```C
NX_PACKET *recv_packet_ptr;

ULONG bytes_retrieved;

UINT final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
    bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="dc5b3-247">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="dc5b3-247">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="dc5b3-248">Hämta storleken på det angivna e-postobjektet</span><span class="sxs-lookup"><span data-stu-id="dc5b3-248">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="dc5b3-249">Prototyp</span><span class="sxs-lookup"><span data-stu-id="dc5b3-249">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_size_get(
    NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *size);
```

### <a name="description"></a><span data-ttu-id="dc5b3-250">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dc5b3-250">Description</span></span>

<span data-ttu-id="dc5b3-251">Den här tjänsten gör en LIST förfrågan för att hämta storleken på det angivna e-postobjektet.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-251">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dc5b3-252">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="dc5b3-252">Input Parameters</span></span>

- <span data-ttu-id="dc5b3-253">**client_ptr** Pekare till klient instans</span><span class="sxs-lookup"><span data-stu-id="dc5b3-253">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="dc5b3-254">**mail_item** Index i klientens maildrop</span><span class="sxs-lookup"><span data-stu-id="dc5b3-254">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="dc5b3-255">**storlek** Pekare till storlek på e-postmeddelande</span><span class="sxs-lookup"><span data-stu-id="dc5b3-255">**size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="dc5b3-256">Retur värden</span><span class="sxs-lookup"><span data-stu-id="dc5b3-256">Return Values</span></span>

- <span data-ttu-id="dc5b3-257">**NX_SUCCESS** (0X00) e-postobjektet har hämtats</span><span class="sxs-lookup"><span data-stu-id="dc5b3-257">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="dc5b3-258">**NX_POP3_INVALID_MAIL_ITEM** (0XB2) ogiltigt e-postobjekts index</span><span class="sxs-lookup"><span data-stu-id="dc5b3-258">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="dc5b3-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) av klient paketets nytto Last är för litet för POP3-begäran.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="dc5b3-260">**NX_POP3_SERVER_ERROR_STATUS** -Server (0xB4) svarar med fel status</span><span class="sxs-lookup"><span data-stu-id="dc5b3-260">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="dc5b3-261">NX_POP3_CLIENT_INVALID_INDEX (0xB8) ogiltigt inmatade e-postindex</span><span class="sxs-lookup"><span data-stu-id="dc5b3-261">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="dc5b3-262">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="dc5b3-262">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dc5b3-263">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="dc5b3-263">Allowed From</span></span>

<span data-ttu-id="dc5b3-264">Program kod</span><span class="sxs-lookup"><span data-stu-id="dc5b3-264">Application code</span></span>

### <a name="example"></a><span data-ttu-id="dc5b3-265">Exempel</span><span class="sxs-lookup"><span data-stu-id="dc5b3-265">Example</span></span>

```C
ULONG size;

UINT mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
