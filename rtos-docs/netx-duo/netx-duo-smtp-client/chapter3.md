---
title: Kapitel 3 – klient Beskrivning av SMTP-klienttjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo SMTP-klienttjänster (visas nedan) i användnings ordning i ett typiskt SMTP-klientcertifikat.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f590ba5a4c020b4a0aec6628a89c0e5f0f8579d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825788"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a><span data-ttu-id="17970-103">Kapitel 3 – klient Beskrivning av SMTP-klienttjänster</span><span class="sxs-lookup"><span data-stu-id="17970-103">Chapter 3 - Client description of SMTP Client services</span></span>

<span data-ttu-id="17970-104">Det här kapitlet innehåller en beskrivning av alla NetX Duo SMTP-klienttjänster (visas nedan) i användnings ordning i ett typiskt SMTP-klientcertifikat.</span><span class="sxs-lookup"><span data-stu-id="17970-104">This chapter contains a description of all NetX Duo SMTP Client services (listed below) in order of usage in a typical SMTP Client application.</span></span>

> [!NOTE]
> <span data-ttu-id="17970-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **_NX_DISABLE_ERROR_CHECKING_** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="17970-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **_NX_DISABLE_ERROR_CHECKING_** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nxd_smtp_client_create"></a><span data-ttu-id="17970-106">nxd_smtp_client_create</span><span class="sxs-lookup"><span data-stu-id="17970-106">nxd_smtp_client_create</span></span>

<span data-ttu-id="17970-107">Skapa en SMTP-klient instans</span><span class="sxs-lookup"><span data-stu-id="17970-107">Create an SMTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="17970-108">Prototyp</span><span class="sxs-lookup"><span data-stu-id="17970-108">Prototype</span></span>

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type, NXD_ADDRESS *server_address,
    UINT port);
```

### <a name="description"></a><span data-ttu-id="17970-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="17970-109">Description</span></span>

<span data-ttu-id="17970-110">Den här tjänsten skapar en SMTP-klient instans på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="17970-110">This service creates an SMTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17970-111">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="17970-111">Input Parameters</span></span>

- <span data-ttu-id="17970-112">**client_ptr** Pekare till SMTP-klientens kontroll block;</span><span class="sxs-lookup"><span data-stu-id="17970-112">**client_ptr** Pointer to SMTP Client control block;</span></span>
- <span data-ttu-id="17970-113">**ip_ptr** Pekare till IP-instans;</span><span class="sxs-lookup"><span data-stu-id="17970-113">**ip_ptr** Pointer to IP instance;</span></span>
- <span data-ttu-id="17970-114">**packet_pool_ptr** Pekare till klient paketets pool;</span><span class="sxs-lookup"><span data-stu-id="17970-114">**packet_pool_ptr** Pointer to Client packet pool;</span></span>
- <span data-ttu-id="17970-115">**användar namn** NULL-terminerat \* \* användar namn för autentisering</span><span class="sxs-lookup"><span data-stu-id="17970-115">**username** NULL-terminated\*\* Username for authentication</span></span>
- <span data-ttu-id="17970-116">**lösen ord** NULL-kopplat lösen ord för autentisering</span><span class="sxs-lookup"><span data-stu-id="17970-116">**password** NULL-terminated password for authentication</span></span>
- <span data-ttu-id="17970-117">**from_address** NULL-avbruten avsändar adress</span><span class="sxs-lookup"><span data-stu-id="17970-117">**from_address** NULL-terminated sender’s address</span></span>
- <span data-ttu-id="17970-118">**client_domain** NULL-avslutat domän namn</span><span class="sxs-lookup"><span data-stu-id="17970-118">**client_domain** NULL-terminated domain name</span></span>
- <span data-ttu-id="17970-119">**authentication_type** Typ av klientautentisering.</span><span class="sxs-lookup"><span data-stu-id="17970-119">**authentication_type** Client authentication type.</span></span> <span data-ttu-id="17970-120">Typer som stöds:</span><span class="sxs-lookup"><span data-stu-id="17970-120">Supported types are:</span></span>
  - <span data-ttu-id="17970-121">NX_SMTP_CLIENT_AUTH_LOGIN</span><span class="sxs-lookup"><span data-stu-id="17970-121">NX_SMTP_CLIENT_AUTH_LOGIN</span></span>
  - <span data-ttu-id="17970-122">NX_SMTP_CLIENT_AUTH_PLAIN</span><span class="sxs-lookup"><span data-stu-id="17970-122">NX_SMTP_CLIENT_AUTH_PLAIN</span></span>
  - <span data-ttu-id="17970-123">NX_SMTP_CLIENT_AUTH_NONE</span><span class="sxs-lookup"><span data-stu-id="17970-123">NX_SMTP_CLIENT_AUTH_NONE</span></span>
- <span data-ttu-id="17970-124">**server_address** Pekare till SMTP-serverns IP-adress</span><span class="sxs-lookup"><span data-stu-id="17970-124">**server_address** Pointer to SMTP Server IP address</span></span>
- <span data-ttu-id="17970-125">**SERVER_PORT** TCP-port för SMTP-server</span><span class="sxs-lookup"><span data-stu-id="17970-125">**server_port** SMTP Server TCP port</span></span>

### <a name="return-values"></a><span data-ttu-id="17970-126">Retur värden</span><span class="sxs-lookup"><span data-stu-id="17970-126">Return Values</span></span>

- <span data-ttu-id="17970-127">**NX_SUCCESS** (0X00) SMTP-klienten har skapats.</span><span class="sxs-lookup"><span data-stu-id="17970-127">**NX_SUCCESS** (0x00) SMTP Client successfully created.</span></span> <span data-ttu-id="17970-128">Status för generering av TCP-socket</span><span class="sxs-lookup"><span data-stu-id="17970-128">TCP socket creation status</span></span>
- <span data-ttu-id="17970-129">NX_SMTP_INVALID_PARAM (0xA5) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="17970-129">NX_SMTP_INVALID_PARAM (0xA5) Invalid non pointer input</span></span>
- <span data-ttu-id="17970-130">NX_IP_ADDRESS_ERROR (0x21) ogiltig IP-adress typ</span><span class="sxs-lookup"><span data-stu-id="17970-130">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address type</span></span>
- <span data-ttu-id="17970-131">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="17970-131">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17970-132">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="17970-132">Allowed From</span></span>

<span data-ttu-id="17970-133">Program kod</span><span class="sxs-lookup"><span data-stu-id="17970-133">Application Code</span></span>

### <a name="example"></a><span data-ttu-id="17970-134">Exempel</span><span class="sxs-lookup"><span data-stu-id="17970-134">Example</span></span>

```C
/* Create the SMTP Client instance. */
NX_PACKET_POOL client_packet_pool;
NX_IP client_ip;
NX_SMTP_CLIENT demo_client;

#define USERNAME “myusername”
#define PASSWORD “mypassword”
#define FROM_ADDRESS “<myname@mycompany.com>”
#define LOCAL_DOMAIN “mycompany.com”
#define SERVER_PORT 25

/* Define client authentication type as LOGIN. 
    If not specified or unknown the SMTP Client will set it to PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE NX_SMTP_CLIENT_AUTH_LOGIN

NXD_ADDRESS server_ip_address;

#ifdef USE_IPV6
    /* Set up the Server IPv6 address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x106;
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;
#endif

status = nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
    USERNAME, PASSWORD, FROM_ADDRESS,
    LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
    &server_ip_address, SERVER_PORT);

/* If an SMTP Client instance was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_smtp_client_delete"></a><span data-ttu-id="17970-135">nx_smtp_client_delete</span><span class="sxs-lookup"><span data-stu-id="17970-135">nx_smtp_client_delete</span></span>

<span data-ttu-id="17970-136">Ta bort en SMTP-klient instans</span><span class="sxs-lookup"><span data-stu-id="17970-136">Delete an SMTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="17970-137">Prototyp</span><span class="sxs-lookup"><span data-stu-id="17970-137">Prototype</span></span>

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="17970-138">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="17970-138">Description</span></span>

<span data-ttu-id="17970-139">Den här tjänsten tar bort en tidigare skapad SMTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="17970-139">This service deletes a previously created SMTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17970-140">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="17970-140">Input Parameters</span></span>

- <span data-ttu-id="17970-141">**client_ptr** Pekare till SMTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="17970-141">**client_ptr** Pointer to SMTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="17970-142">Retur värden</span><span class="sxs-lookup"><span data-stu-id="17970-142">Return Values</span></span>

- <span data-ttu-id="17970-143">**NX_SUCCESS** (0X00) klienten har tagits bort</span><span class="sxs-lookup"><span data-stu-id="17970-143">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="17970-144">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="17970-144">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17970-145">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="17970-145">Allowed From</span></span>

<span data-ttu-id="17970-146">Konversation</span><span class="sxs-lookup"><span data-stu-id="17970-146">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17970-147">Exempel</span><span class="sxs-lookup"><span data-stu-id="17970-147">Example</span></span>

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a><span data-ttu-id="17970-148">nx_smtp_mail_send</span><span class="sxs-lookup"><span data-stu-id="17970-148">nx_smtp_mail_send</span></span>

<span data-ttu-id="17970-149">Skapa och skicka ett SMTP-e-postobjekt</span><span class="sxs-lookup"><span data-stu-id="17970-149">Create and send an SMTP mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="17970-150">Prototyp</span><span class="sxs-lookup"><span data-stu-id="17970-150">Prototype</span></span>

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a><span data-ttu-id="17970-151">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="17970-151">Description</span></span>

<span data-ttu-id="17970-152">Den här tjänsten skapar och skickar ett SMTP-e-postobjekt.</span><span class="sxs-lookup"><span data-stu-id="17970-152">This service creates and sends an SMTP mail item.</span></span> <span data-ttu-id="17970-153">SMTP-klienten upprättar en TCP-anslutning med SMTP-servern och skickar en serie med SMTP-kommandon.</span><span class="sxs-lookup"><span data-stu-id="17970-153">The SMTP Client establishes a TCP connection with the SMTP Server and sends a series of SMTP commands.</span></span> <span data-ttu-id="17970-154">Om inga fel uppstår skickas e-postmeddelandet till servern.</span><span class="sxs-lookup"><span data-stu-id="17970-154">If no errors are encountered, it will transmit the mail message to the Server.</span></span> <span data-ttu-id="17970-155">Oavsett om e-postmeddelandet har skickats avbryts TCP-anslutningen och returnerar en status som anger resultatet av e-postöverföringen.</span><span class="sxs-lookup"><span data-stu-id="17970-155">Regardless if the mail is sent successfully it will terminate the TCP connection and return a status indicating outcome of the mail transmission.</span></span> <span data-ttu-id="17970-156">Programmet kan anropa den här tjänsten för så många e-postmeddelanden som det måste skickas utan begränsning.</span><span class="sxs-lookup"><span data-stu-id="17970-156">The application may call this service for as many mail messages as it needs to send without limit.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17970-157">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="17970-157">Input Parameters</span></span>

- <span data-ttu-id="17970-158">**client_ptr** Pekare till SMTP-klient</span><span class="sxs-lookup"><span data-stu-id="17970-158">**client_ptr** Pointer to SMTP Client</span></span>
- <span data-ttu-id="17970-159">**recipient_address** NULL-avslutad mottagar adress.</span><span class="sxs-lookup"><span data-stu-id="17970-159">**recipient_address** NULL-terminated recipient address.</span></span>
- <span data-ttu-id="17970-160">**ämne** NULL-avslutad ämnes rad text;.</span><span class="sxs-lookup"><span data-stu-id="17970-160">**subject** NULL-terminated subject line text;.</span></span>
- <span data-ttu-id="17970-161">**prioritet** Prioritets nivå då e-post levereras</span><span class="sxs-lookup"><span data-stu-id="17970-161">**priority** Priority level at which mail is delivered</span></span>
- <span data-ttu-id="17970-162">**mail_body** Pekare till e-postmeddelande</span><span class="sxs-lookup"><span data-stu-id="17970-162">**mail_body** Pointer to mail message</span></span>
- <span data-ttu-id="17970-163">**mail_body_length** Storlek på e-postmeddelande</span><span class="sxs-lookup"><span data-stu-id="17970-163">**mail_body_length** Size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="17970-164">Retur värden</span><span class="sxs-lookup"><span data-stu-id="17970-164">Return Values</span></span>

- <span data-ttu-id="17970-165">**NX_SUCCESS** (0X00) e-post har skickats</span><span class="sxs-lookup"><span data-stu-id="17970-165">**NX_SUCCESS** (0x00) Mail successfully sent</span></span>
- <span data-ttu-id="17970-166">**NX_SMTP_CLIENT_NOT_INITIALIZED** (0XB2) SMTP-serverinstans har inte initierats för SMTP-sessionens status resultat för SMTP-session</span><span class="sxs-lookup"><span data-stu-id="17970-166">**NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) SMTP Client instance not initialized for SMTP session status Outcome of SMTP session</span></span>
- <span data-ttu-id="17970-167">NX_PTR_ERROR (0x07) ogiltig pekar parameter</span><span class="sxs-lookup"><span data-stu-id="17970-167">NX_PTR_ERROR (0x07) Invalid pointer parameter</span></span>
- <span data-ttu-id="17970-168">NX_SMTP_INVALID_PARAM (0xA5) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="17970-168">NX_SMTP_INVALID_PARAM (0xA5) Invalid non pointer input</span></span>
- <span data-ttu-id="17970-169">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="17970-169">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17970-170">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="17970-170">Allowed From</span></span>

<span data-ttu-id="17970-171">Konversation</span><span class="sxs-lookup"><span data-stu-id="17970-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17970-172">Exempel</span><span class="sxs-lookup"><span data-stu-id="17970-172">Example</span></span>

```C
/* Create and send a Client mail item. */

#define RECIPIENT_ADDRESS “<your@yourcompany.com>”
#define SUBJECT “NetX Duo SMTP Client Demo”
#define MAIL_BODY "NetX Duo SMTP client is an SMTP client ” \
    “implementation for embedded devices \r\n” \
    "to send email to SMTP servers.\r\n"

status = nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
    NX_SMTP_MAIL_PRIORITY_NORMAL,
    SUBJECT_LINE, MAIL_BODY,
    sizeof(MAIL_BODY) - 1);

/* Return status being NX_SUCCESS indicates the mail has been
    successfully sent. */
```
