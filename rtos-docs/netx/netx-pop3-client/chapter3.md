---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX POP3-klient tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX POP3-klient tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1a0ab96a454bea9f56ced0d7aa8de5d481b284e9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826661"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a><span data-ttu-id="b8e1b-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX POP3-klient tjänster</span><span class="sxs-lookup"><span data-stu-id="b8e1b-103">Chapter 3 - Description of Azure RTOS NetX POP3 Client services</span></span>

<span data-ttu-id="b8e1b-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX POP3-klient tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-104">This chapter contains a description of all Azure RTOS NetX POP3 Client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="b8e1b-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="b8e1b-106">nx_pop3_client_create: *skapa en POP3-klient instans*</span><span class="sxs-lookup"><span data-stu-id="b8e1b-106">nx_pop3_client_create: *Create a POP3 Client Instance*</span></span>
- <span data-ttu-id="b8e1b-107">nx_pop3_client_delete: *ta bort en POP3-klient instans*</span><span class="sxs-lookup"><span data-stu-id="b8e1b-107">nx_pop3_client_delete: *Delete a POP3 Client instance*</span></span>
- <span data-ttu-id="b8e1b-108">nx_pop3_client_ mail_item_get: *ta bort ett klient e-postobjekt från servern maildrop*</span><span class="sxs-lookup"><span data-stu-id="b8e1b-108">nx_pop3_client_ mail_item_get: *Delete a Client mail item from Server maildrop*</span></span>
- <span data-ttu-id="b8e1b-109">nx_pop3_client_mail_item_get: *Hämta en speciell e-postmeddelande storlek*</span><span class="sxs-lookup"><span data-stu-id="b8e1b-109">nx_pop3_client_mail_item_get: *Retrieve a specific mail message size*</span></span>
- <span data-ttu-id="b8e1b-110">nx_pop3_client_mail_items_get: *Hämta antalet e-postobjekt i maildrop*</span><span class="sxs-lookup"><span data-stu-id="b8e1b-110">nx_pop3_client_mail_items_get: *Obtain the number of mail items in maildrop*</span></span>
- <span data-ttu-id="b8e1b-111">nx_pop3_client_mail_item_message _get: *Hämta ett speciellt e-postmeddelande*</span><span class="sxs-lookup"><span data-stu-id="b8e1b-111">nx_pop3_client_mail_item_message _get: *Download a specific mail message*</span></span>
- <span data-ttu-id="b8e1b-112">nx_pop3_client_mail_item_size_get: *Hämta storleken på ett speciellt e-postobjekt*</span><span class="sxs-lookup"><span data-stu-id="b8e1b-112">nx_pop3_client_mail_item_size_get: *Obtain the size of a specific mail item*</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="b8e1b-113">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="b8e1b-113">nx_pop3_client_create</span></span>

<span data-ttu-id="b8e1b-114">Skapa en POP3-klient instans</span><span class="sxs-lookup"><span data-stu-id="b8e1b-114">Create a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="b8e1b-115">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b8e1b-115">Prototype</span></span>

```c
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                        UINT APOP_authentication, NX_IP *ip_ptr,
                        NX_PACKET_POOL *packet_pool_ptr,
                        ULONG server_ip_address,
                        ULONG server_port,
                        CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="b8e1b-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b8e1b-116">Description</span></span>

<span data-ttu-id="b8e1b-117">Den här tjänsten skapar en instans av POP3-klienten och konfigurerar konfigurationen med indataparametrarna.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-117">This service creates an instance of the POP3 Client and sets up its configuration with the input parameters.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b8e1b-118">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="b8e1b-118">Input Parameters</span></span>

- <span data-ttu-id="b8e1b-119">**client_ptr**: pekare till klienten för att skapa</span><span class="sxs-lookup"><span data-stu-id="b8e1b-119">**client_ptr**: Pointer to Client to create</span></span>
- <span data-ttu-id="b8e1b-120">**APOP_authentication**: Aktivera APOP-autentisering</span><span class="sxs-lookup"><span data-stu-id="b8e1b-120">**APOP_authentication**: Enable APOP authentication</span></span>
- <span data-ttu-id="b8e1b-121">**ip_ptr**: pekare till IP-instans</span><span class="sxs-lookup"><span data-stu-id="b8e1b-121">**ip_ptr**: Pointer to IP instance</span></span>
- <span data-ttu-id="b8e1b-122">**packet_pool_ptr**: pekare till klient paketets pool</span><span class="sxs-lookup"><span data-stu-id="b8e1b-122">**packet_pool_ptr**: Pointer to Client packet pool</span></span>
- <span data-ttu-id="b8e1b-123">**server_ip_address**: POP3-server adress</span><span class="sxs-lookup"><span data-stu-id="b8e1b-123">**server_ip_address**: POP3 server address</span></span>
- <span data-ttu-id="b8e1b-124">**SERVER_PORT**: POP3-server port</span><span class="sxs-lookup"><span data-stu-id="b8e1b-124">**server_port**: POP3 server port</span></span>
- <span data-ttu-id="b8e1b-125">**client_name**: pekare till klient namn</span><span class="sxs-lookup"><span data-stu-id="b8e1b-125">**client_name**: Pointer to Client name</span></span>
- <span data-ttu-id="b8e1b-126">**client_password**: pekar mot klient lösen ord</span><span class="sxs-lookup"><span data-stu-id="b8e1b-126">**client_password**: Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="b8e1b-127">Retur värden</span><span class="sxs-lookup"><span data-stu-id="b8e1b-127">Return Values</span></span>

- <span data-ttu-id="b8e1b-128">**NX_SUCCESS**: (0X00) klienten har skapats</span><span class="sxs-lookup"><span data-stu-id="b8e1b-128">**NX_SUCCESS**: (0x00) Client successfully created</span></span>
- <span data-ttu-id="b8e1b-129">**status**: status slutförd för netx-och ThreadX-tjänst anrop</span><span class="sxs-lookup"><span data-stu-id="b8e1b-129">**status**: Status completion of NetX and ThreadX service calls</span></span>
- <span data-ttu-id="b8e1b-130">NX_PTR_ERROR: (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="b8e1b-130">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="b8e1b-131">NX_POP3_PARAM_ERROR: (0xB1) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="b8e1b-131">NX_POP3_PARAM_ERROR: (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b8e1b-132">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="b8e1b-132">Allowed From</span></span>

<span data-ttu-id="b8e1b-133">Program kod</span><span class="sxs-lookup"><span data-stu-id="b8e1b-133">Application code</span></span>

### <a name="example"></a><span data-ttu-id="b8e1b-134">Exempel</span><span class="sxs-lookup"><span data-stu-id="b8e1b-134">Example</span></span>

```c
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST                   "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD          "pass"
#define POP3_SERVER_ADDRESS         IP_ADDRESS(192,2,2,92
#define POP3_SERVER_PORT            110

/* Create a NetX POP3 Client instance. */
ULONG server_ip_address = IP_ADDRESS(1,2,3,4);
status = nx_pop3_client_create(&demo_client,
        NX_FALSE /* disable APOP authentication */,
        &client_ip, &client_packet_pool,
        server_ip_address, POP3_SERVER_PORT,
        LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="b8e1b-135">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="b8e1b-135">nx_pop3_client_delete</span></span>

<span data-ttu-id="b8e1b-136">Ta bort en POP3-klient instans</span><span class="sxs-lookup"><span data-stu-id="b8e1b-136">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="b8e1b-137">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b8e1b-137">Prototype</span></span>

```c
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr)
```

### <a name="description"></a><span data-ttu-id="b8e1b-138">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b8e1b-138">Description</span></span>

<span data-ttu-id="b8e1b-139">Den här tjänsten tar bort en tidigare skapad POP3-klient.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-139">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="b8e1b-140">Inte att den här tjänsten inte tar bort POP3-klientens adresspool.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-140">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="b8e1b-141">Enhets programmet måste ta bort den här resursen separat om den inte längre har använt för poolen.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-141">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b8e1b-142">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="b8e1b-142">Input Parameters</span></span>

- <span data-ttu-id="b8e1b-143">**client_ptr**: pekare till klienten som ska tas bort</span><span class="sxs-lookup"><span data-stu-id="b8e1b-143">**client_ptr**: Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="b8e1b-144">Retur värden</span><span class="sxs-lookup"><span data-stu-id="b8e1b-144">Return Values</span></span>

- <span data-ttu-id="b8e1b-145">**NX_SUCCESS**: (0X00) klienten har tagits bort</span><span class="sxs-lookup"><span data-stu-id="b8e1b-145">**NX_SUCCESS**: (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="b8e1b-146">NX_PTR_ERROR: (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="b8e1b-146">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b8e1b-147">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="b8e1b-147">Allowed From</span></span>

<span data-ttu-id="b8e1b-148">Program kod</span><span class="sxs-lookup"><span data-stu-id="b8e1b-148">Application code</span></span>

### <a name="example"></a><span data-ttu-id="b8e1b-149">Exempel</span><span class="sxs-lookup"><span data-stu-id="b8e1b-149">Example</span></span>

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="b8e1b-150">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="b8e1b-150">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="b8e1b-151">Ta bort ett angivet e-postobjekt från klientens maildrop</span><span class="sxs-lookup"><span data-stu-id="b8e1b-151">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="b8e1b-152">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b8e1b-152">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a><span data-ttu-id="b8e1b-153">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b8e1b-153">Description</span></span>

<span data-ttu-id="b8e1b-154">Den här tjänsten tar bort det angivna e-postobjektet från klientens maildrop.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-154">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="b8e1b-155">Den är avsedd för när du har laddat ned e-postobjektet, även om vissa POP3-servrar kan ta bort e-postobjekten automatiskt efter att klienten har begärt</span><span class="sxs-lookup"><span data-stu-id="b8e1b-155">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b8e1b-156">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="b8e1b-156">Input Parameters</span></span>

- <span data-ttu-id="b8e1b-157">**client_ptr**: pekare till klient instans</span><span class="sxs-lookup"><span data-stu-id="b8e1b-157">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="b8e1b-158">**mail_index**: index i klientens maildrop</span><span class="sxs-lookup"><span data-stu-id="b8e1b-158">**mail_index**: Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="b8e1b-159">Retur värden</span><span class="sxs-lookup"><span data-stu-id="b8e1b-159">Return Values</span></span>

- <span data-ttu-id="b8e1b-160">**NX_SUCCESS**: (0X00) borttagnings förfrågan lyckades</span><span class="sxs-lookup"><span data-stu-id="b8e1b-160">**NX_SUCCESS**: (0x00) Delete request successful</span></span>
- <span data-ttu-id="b8e1b-161">**NX_POP3_INVALID_MAIL_ITEM**: (0XB2) ogiltigt e-postobjekts index</span><span class="sxs-lookup"><span data-stu-id="b8e1b-161">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="b8e1b-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0XB6) klient paketets nytto Last är för liten för POP3-begäran.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="b8e1b-163">**NX_POP3_SERVER_ERROR_STATUS**: (0XB4) Server svar med fel status</span><span class="sxs-lookup"><span data-stu-id="b8e1b-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="b8e1b-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) ogiltigt inmatade e-postindex</span><span class="sxs-lookup"><span data-stu-id="b8e1b-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="b8e1b-165">NX_PTR_ERROR: (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="b8e1b-165">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b8e1b-166">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="b8e1b-166">Allowed From</span></span>

<span data-ttu-id="b8e1b-167">Program kod</span><span class="sxs-lookup"><span data-stu-id="b8e1b-167">Application code</span></span>

### <a name="example"></a><span data-ttu-id="b8e1b-168">Exempel</span><span class="sxs-lookup"><span data-stu-id="b8e1b-168">Example</span></span>

```c
ULONG     item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status = 
   NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="b8e1b-169">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="b8e1b-169">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="b8e1b-170">Hämta ett angivet e-postobjekt</span><span class="sxs-lookup"><span data-stu-id="b8e1b-170">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="b8e1b-171">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b8e1b-171">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a><span data-ttu-id="b8e1b-172">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b8e1b-172">Description</span></span>

<span data-ttu-id="b8e1b-173">Den här tjänsten gör en RETR-begäran för att hämta ett e-postobjekt från den klient maildrop som anges av index mail_item.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-173">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="b8e1b-174">När du har gjort en RETR-begäran och fått ett positivt svar från servern kan klienten börja hämta e-postmeddelandet med hjälp av tjänsten *nx_pop3_client_mail_item_message_get* .</span><span class="sxs-lookup"><span data-stu-id="b8e1b-174">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="b8e1b-175">Observera att tjänsten också tillhandahåller storleken på det begärda e-postobjektet som extraherats från Server svaret.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-175">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b8e1b-176">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="b8e1b-176">Input Parameters</span></span>

- <span data-ttu-id="b8e1b-177">**client_ptr**: pekare till klient instans</span><span class="sxs-lookup"><span data-stu-id="b8e1b-177">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="b8e1b-178">**mail_item**: index i klientens maildrop</span><span class="sxs-lookup"><span data-stu-id="b8e1b-178">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="b8e1b-179">**item_size**: pekar mot storlek på e-postmeddelande</span><span class="sxs-lookup"><span data-stu-id="b8e1b-179">**item_size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="b8e1b-180">Retur värden</span><span class="sxs-lookup"><span data-stu-id="b8e1b-180">Return Values</span></span>

- <span data-ttu-id="b8e1b-181">**NX_SUCCESS**: (0X00) e-postobjektet har hämtats</span><span class="sxs-lookup"><span data-stu-id="b8e1b-181">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="b8e1b-182">**NX_POP3_INVALID_MAIL_ITEM**: (0XB2) ogiltigt e-postobjekts index</span><span class="sxs-lookup"><span data-stu-id="b8e1b-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="b8e1b-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0XB6) klient paketets nytto Last är för liten för POP3-begäran.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="b8e1b-184">**NX_POP3_SERVER_ERROR_STATUS**: (0XB4) Server svar med fel status</span><span class="sxs-lookup"><span data-stu-id="b8e1b-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="b8e1b-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) ogiltigt inmatade e-postindex</span><span class="sxs-lookup"><span data-stu-id="b8e1b-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="b8e1b-186">NX_PTR_ERROR: (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="b8e1b-186">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b8e1b-187">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="b8e1b-187">Allowed From</span></span>

<span data-ttu-id="b8e1b-188">Program kod</span><span class="sxs-lookup"><span data-stu-id="b8e1b-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="b8e1b-189">Exempel</span><span class="sxs-lookup"><span data-stu-id="b8e1b-189">Example</span></span>

```c
ULONG     item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="b8e1b-190">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="b8e1b-190">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="b8e1b-191">Hämta antalet e-postobjekt i maildrop</span><span class="sxs-lookup"><span data-stu-id="b8e1b-191">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="b8e1b-192">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b8e1b-192">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a><span data-ttu-id="b8e1b-193">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b8e1b-193">Description</span></span>

<span data-ttu-id="b8e1b-194">Den här tjänsten gör en STAT-begäran för att hämta antalet e-postobjekt och den totala storleken på e-postmeddelandets data från klientens maildrop.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-194">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b8e1b-195">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="b8e1b-195">Input Parameters</span></span>

- <span data-ttu-id="b8e1b-196">**client_ptr**: pekare till klient instans</span><span class="sxs-lookup"><span data-stu-id="b8e1b-196">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="b8e1b-197">**number_mail_item**: antalet e-postmeddelanden i klient maildrop</span><span class="sxs-lookup"><span data-stu-id="b8e1b-197">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="b8e1b-198">**maildrop_total_size**: pekar mot storlek på alla e-postmeddelanden</span><span class="sxs-lookup"><span data-stu-id="b8e1b-198">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="b8e1b-199">Retur värden</span><span class="sxs-lookup"><span data-stu-id="b8e1b-199">Return Values</span></span>

- <span data-ttu-id="b8e1b-200">**NX_SUCCESS**: (0X00) e-postobjektet har hämtats</span><span class="sxs-lookup"><span data-stu-id="b8e1b-200">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="b8e1b-201">**NX_POP3_INVALID_MAIL_ITEM**: (0XB2) ogiltigt e-postobjekts index</span><span class="sxs-lookup"><span data-stu-id="b8e1b-201">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="b8e1b-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0XB6) klient paketets nytto Last är för liten för POP3-begäran.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="b8e1b-203">**NX_POP3_SERVER_ERROR_STATUS**: (0XB4) Server svar med fel status</span><span class="sxs-lookup"><span data-stu-id="b8e1b-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span> 
- <span data-ttu-id="b8e1b-204">NX_PTR_ERROR: (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="b8e1b-204">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b8e1b-205">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="b8e1b-205">Allowed From</span></span>

<span data-ttu-id="b8e1b-206">Program kod</span><span class="sxs-lookup"><span data-stu-id="b8e1b-206">Application code</span></span>

### <a name="example"></a><span data-ttu-id="b8e1b-207">Exempel</span><span class="sxs-lookup"><span data-stu-id="b8e1b-207">Example</span></span>

```c
UINT      number_mail_items;
ULONG     maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
                                        &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="b8e1b-208">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="b8e1b-208">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="b8e1b-209">Hämta det angivna meddelandet om e-postobjektet</span><span class="sxs-lookup"><span data-stu-id="b8e1b-209">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="b8e1b-210">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b8e1b-210">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a><span data-ttu-id="b8e1b-211">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b8e1b-211">Description</span></span>

<span data-ttu-id="b8e1b-212">Den här tjänsten hämtar e-postmeddelandets meddelande, storleken på e-postmeddelandet och om det är det sista paketet i e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-212">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="b8e1b-213">Om `final_packet` är NX_TRUE paketet som pekas på av `recv_packet_ptr` är det sista paketet i meddelandet med e-postobjektet.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-213">If `final_packet` is NX_TRUE the packet pointed to by `recv_packet_ptr` is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b8e1b-214">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="b8e1b-214">Input Parameters</span></span>

- <span data-ttu-id="b8e1b-215">**client_ptr**: pekare till klient instans</span><span class="sxs-lookup"><span data-stu-id="b8e1b-215">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="b8e1b-216">**recv_packet_ptr**: paket med meddelande data togs emot</span><span class="sxs-lookup"><span data-stu-id="b8e1b-216">**recv_packet_ptr**: Received packet of message data</span></span>
- <span data-ttu-id="b8e1b-217">**number_mail_item**: antalet e-postmeddelanden i klient maildrop</span><span class="sxs-lookup"><span data-stu-id="b8e1b-217">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="b8e1b-218">**maildrop_total_size**: pekar mot storlek på alla e-postmeddelanden</span><span class="sxs-lookup"><span data-stu-id="b8e1b-218">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="b8e1b-219">Retur värden</span><span class="sxs-lookup"><span data-stu-id="b8e1b-219">Return Values</span></span>

- <span data-ttu-id="b8e1b-220">**NX_SUCCESS**: (0X00) e-postobjektet har hämtats</span><span class="sxs-lookup"><span data-stu-id="b8e1b-220">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="b8e1b-221">**NX_POP3_CLIENT_INVALID_STATE**: (0XB7) klient paketets nytto Last är för liten för POP3-begäran.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="b8e1b-222">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="b8e1b-222">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b8e1b-223">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="b8e1b-223">Allowed From</span></span>

<span data-ttu-id="b8e1b-224">Program kod</span><span class="sxs-lookup"><span data-stu-id="b8e1b-224">Application code</span></span>

### <a name="example"></a><span data-ttu-id="b8e1b-225">Exempel</span><span class="sxs-lookup"><span data-stu-id="b8e1b-225">Example</span></span>

```c
NX_PACKET     *recv_packet_ptr;
ULONG         bytes_retrieved;
UINT          final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
                                                bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="b8e1b-226">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="b8e1b-226">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="b8e1b-227">Hämta storleken på det angivna e-postobjektet</span><span class="sxs-lookup"><span data-stu-id="b8e1b-227">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="b8e1b-228">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b8e1b-228">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a><span data-ttu-id="b8e1b-229">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b8e1b-229">Description</span></span>

<span data-ttu-id="b8e1b-230">Den här tjänsten gör en LIST förfrågan för att hämta storleken på det angivna e-postobjektet.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-230">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b8e1b-231">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="b8e1b-231">Input Parameters</span></span>

- <span data-ttu-id="b8e1b-232">**client_ptr**: pekare till klient instans</span><span class="sxs-lookup"><span data-stu-id="b8e1b-232">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="b8e1b-233">**mail_item**: index i klientens maildrop</span><span class="sxs-lookup"><span data-stu-id="b8e1b-233">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="b8e1b-234">**storlek**: pekare till storlek på e-postmeddelande</span><span class="sxs-lookup"><span data-stu-id="b8e1b-234">**size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="b8e1b-235">Retur värden</span><span class="sxs-lookup"><span data-stu-id="b8e1b-235">Return Values</span></span>

- <span data-ttu-id="b8e1b-236">**NX_SUCCESS**: (0X00) e-postobjektet har hämtats</span><span class="sxs-lookup"><span data-stu-id="b8e1b-236">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="b8e1b-237">**NX_POP3_INVALID_MAIL_ITEM**: (0XB2) ogiltigt e-postobjekts index</span><span class="sxs-lookup"><span data-stu-id="b8e1b-237">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="b8e1b-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0XB6) klient paketets nytto Last är för liten för POP3-begäran.</span><span class="sxs-lookup"><span data-stu-id="b8e1b-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="b8e1b-239">**NX_POP3_SERVER_ERROR_STATUS**: (0XB4) Server svar med fel status</span><span class="sxs-lookup"><span data-stu-id="b8e1b-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="b8e1b-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) ogiltigt inmatade e-postindex</span><span class="sxs-lookup"><span data-stu-id="b8e1b-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="b8e1b-241">NX_PTR_ERROR: (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="b8e1b-241">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b8e1b-242">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="b8e1b-242">Allowed From</span></span>

<span data-ttu-id="b8e1b-243">Program kod</span><span class="sxs-lookup"><span data-stu-id="b8e1b-243">Application code</span></span>

### <a name="example"></a><span data-ttu-id="b8e1b-244">Exempel</span><span class="sxs-lookup"><span data-stu-id="b8e1b-244">Example</span></span>

```c
ULONG     size;
UINT      mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
