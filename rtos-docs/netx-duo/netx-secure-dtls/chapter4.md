---
title: Kapitel 4 – Beskrivning av Azure återställnings tider NetX Secure DTLS Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX-säkra DTLS-tjänster som anges i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e795a5fa35a4590e508c7fe2eec53f5494809657
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825689"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a><span data-ttu-id="10b69-103">Kapitel 4: Beskrivning av Azure återställnings tider NetX Secure DTLS Services</span><span class="sxs-lookup"><span data-stu-id="10b69-103">Chapter 4: Description of Azure RTOS NetX Secure DTLS services</span></span>

<span data-ttu-id="10b69-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX-säkra DTLS-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="10b69-104">This chapter contains a description of all Azure RTOS NetX Secure DTLS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="10b69-105">I avsnittet "returnera värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_SECURE_DISABLE_ERROR_CHECKING** makro som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="10b69-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="10b69-106">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="10b69-106">nx_secure_dtls_client_session_start</span></span>](#nx_secure_dtls_client_session_start)
- [<span data-ttu-id="10b69-107">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="10b69-107">nx_secure_dtls_packet_allocate</span></span>](#nx_secure_dtls_packet_allocate)
- [<span data-ttu-id="10b69-108">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="10b69-108">nx_secure_dtls_psk_add</span></span>](#nx_secure_dtls_psk_add)
- [<span data-ttu-id="10b69-109">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="10b69-109">nx_secure_dtls_server_create</span></span>](#nx_secure_dtls_server_create)
- [<span data-ttu-id="10b69-110">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="10b69-110">nx_secure_dtls_server_delete</span></span>](#nx_secure_dtls_server_delete)
- [<span data-ttu-id="10b69-111">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="10b69-111">nx_secure_dtls_server_local_certificate_add</span></span>](#nx_secure_dtls_server_local_certificate_add)
- [<span data-ttu-id="10b69-112">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="10b69-112">nx_secure_dtls_server_local_certificate_remove</span></span>](#nx_secure_dtls_server_local_certificate_remove)
- [<span data-ttu-id="10b69-113">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="10b69-113">nx_secure_dtls_server_notify_set</span></span>](#nx_secure_dtls_server_notify_set)
- [<span data-ttu-id="10b69-114">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="10b69-114">nx_secure_dtls_server_psk_add</span></span>](#nx_secure_dtls_server_psk_add)
- [<span data-ttu-id="10b69-115">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="10b69-115">nx_secure_dtls_server_session_send</span></span>](#nx_secure_dtls_server_session_send)
- [<span data-ttu-id="10b69-116">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="10b69-116">nx_secure_dtls_server_session_start</span></span>](#nx_secure_dtls_server_session_start)
- [<span data-ttu-id="10b69-117">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="10b69-117">nx_secure_dtls_server_start</span></span>](#nx_secure_dtls_server_start)
- [<span data-ttu-id="10b69-118">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="10b69-118">nx_secure_dtls_server_stop</span></span>](#nx_secure_dtls_server_stop)
- [<span data-ttu-id="10b69-119">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="10b69-119">nx_secure_dtls_server_trusted_certificate_add</span></span>](#nx_secure_dtls_server_trusted_certificate_add)
- [<span data-ttu-id="10b69-120">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="10b69-120">nx_secure_dtls_server_trusted_certificate_remove</span></span>](#nx_secure_dtls_server_trusted_certificate_remove)
- [<span data-ttu-id="10b69-121">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="10b69-121">nx_secure_dtls_server_x509_client_verify_configure</span></span>](#nx_secure_dtls_server_x509_client_verify_configure)
- [<span data-ttu-id="10b69-122">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="10b69-122">nx_secure_dtls_server_x509_client_verify_disable</span></span>](#nx_secure_dtls_server_x509_client_verify_disable)
- [<span data-ttu-id="10b69-123">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="10b69-123">nx_secure_dtls_session_client_info_get</span></span>](#nx_secure_dtls_session_client_info_get)
- [<span data-ttu-id="10b69-124">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="10b69-124">nx_secure_dtls_session_create</span></span>](#nx_secure_dtls_session_create)
- [<span data-ttu-id="10b69-125">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="10b69-125">nx_secure_dtls_session_delete</span></span>](#nx_secure_dtls_session_delete)
- [<span data-ttu-id="10b69-126">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="10b69-126">nx_secure_dtls_session_end</span></span>](#nx_secure_dtls_session_end)
- [<span data-ttu-id="10b69-127">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="10b69-127">nx_secure_dtls_session_local_certificate_add</span></span>](#nx_secure_dtls_session_local_certificate_add)
- [<span data-ttu-id="10b69-128">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="10b69-128">nx_secure_dtls_session_local_certificate_remove</span></span>](#nx_secure_dtls_session_local_certificate_remove)
- [<span data-ttu-id="10b69-129">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="10b69-129">nx_secure_dtls_session_receive</span></span>](#nx_secure_dtls_session_receive)
- [<span data-ttu-id="10b69-130">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="10b69-130">nx_secure_dtls_session_reset</span></span>](#nx_secure_dtls_session_reset)
- [<span data-ttu-id="10b69-131">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="10b69-131">nx_secure_dtls_ session_send</span></span>](#nx_secure_dtls_-session_send)
- [<span data-ttu-id="10b69-132">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="10b69-132">nx_secure_dtls_session_trusted_certificate_add</span></span>](#nx_secure_dtls_session_trusted_certificate_add)
- [<span data-ttu-id="10b69-133">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="10b69-133">nx_secure_dtls_session_trusted_certificate_remove</span></span>](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a><span data-ttu-id="10b69-134">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="10b69-134">nx_secure_dtls_client_session_start</span></span>

<span data-ttu-id="10b69-135">Starta en NetX säker DTLS-klientsession</span><span class="sxs-lookup"><span data-stu-id="10b69-135">Start a NetX Secure DTLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-136">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-136">Prototype</span></span>

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="10b69-137">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-137">Description</span></span>

<span data-ttu-id="10b69-138">Den här tjänsten startar en DTLS-klientsession som ansluter till servern med den angivna IP-adressen och UDP-porten, med den tillhandahållna UDP-socketen för nätverkskommunikation.</span><span class="sxs-lookup"><span data-stu-id="10b69-138">This service starts a DTLS Client session, connecting to the server at the provided IP address and UDP port, using the provided UDP socket for network communications.</span></span>

<span data-ttu-id="10b69-139">DTLS måste initieras innan den här tjänsten anropas med hjälp av nx_secure_dtls_session_create.</span><span class="sxs-lookup"><span data-stu-id="10b69-139">The DTLS session control block must be initialized prior to calling this service using nx_secure_dtls_session_create.</span></span> <span data-ttu-id="10b69-140">Dessutom kräver DTLS-klienten att minst ett certifikat för betrodd certifikat utfärdare har lagts till i sessionen med nx_secure_dtls_session_trusted_certificate_add eller i förväg delade nycklar har Aktiver ATS och kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="10b69-140">Additionally, the DTLS Client requires that at least one trusted CA certificate has been added to the session using nx_secure_dtls_session_trusted_certificate_add or Pre-Shared Keys are enabled and configured.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-141">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-141">Parameters</span></span>

- <span data-ttu-id="10b69-142">**dtls_session** Pekare till en DTLS som initierades tidigare.</span><span class="sxs-lookup"><span data-stu-id="10b69-142">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="10b69-143">**udp_socket** Initierad UDP-socket som ska användas för att upprätta nätverkskommunikation med den fjärranslutna DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-143">**udp_socket** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="10b69-144">**ip_address** Pekare till IP-adress strukturen som innehåller adressen till DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-144">**ip_address** Pointer to IP address structure containing the address of the remote DTLS server.</span></span>
- <span data-ttu-id="10b69-145">**port** Initierad UDP-socket som ska användas för att upprätta nätverkskommunikation med den fjärranslutna DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-145">**port** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="10b69-146">**wait_option** Uppehålls alternativ för anslutnings försök.</span><span class="sxs-lookup"><span data-stu-id="10b69-146">**wait_option** Suspension option for connection attempt.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-147">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-147">Return Values</span></span>

- <span data-ttu-id="10b69-148">**NX_SUCCESS** (0x00) har slutfört tilldelningen av certifikat till sessionen.</span><span class="sxs-lookup"><span data-stu-id="10b69-148">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="10b69-149">**NX_NOT_CONNECTED** (0x38) servern kan inte nås på den adress och port som anges.</span><span class="sxs-lookup"><span data-stu-id="10b69-149">**NX_NOT_CONNECTED** (0x38) The server cannot be reached at the given address and port.</span></span>
- <span data-ttu-id="10b69-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) en mottagen TLS/DTLS meddelande typ är felaktig.</span><span class="sxs-lookup"><span data-stu-id="10b69-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS/DTLS message type is incorrect.</span></span>
- <span data-ttu-id="10b69-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0X106) ett chiffer som tillhandahålls av fjärrvärden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="10b69-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="10b69-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Det gick inte att bearbeta meddelande bearbetningen under TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="10b69-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="10b69-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) ett inkommande meddelande misslyckades med en hash Mac-kontroll.</span><span class="sxs-lookup"><span data-stu-id="10b69-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="10b69-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka en underliggande TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="10b69-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="10b69-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) ett inkommande meddelande hade ett ogiltigt längd fält.</span><span class="sxs-lookup"><span data-stu-id="10b69-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="10b69-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0X10B) ett inkommande ChangeCipherSpec-meddelande var felaktigt.</span><span class="sxs-lookup"><span data-stu-id="10b69-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="10b69-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0X10C) ett inkommande TLS-certifikat kan inte användas för att identifiera fjärran SLUTen DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote DTLS server.</span></span>
- <span data-ttu-id="10b69-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0X10D) den offentliga nyckel chiffer som tillhandahålls av fjärrvärden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="10b69-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="10b69-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) fjärrvärden har indikerat Inga krypteringssviter som stöds av stacken netx Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure DTLS stack.</span></span>
- <span data-ttu-id="10b69-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) ett MOTTAGet DTLS-meddelande hade en okänd DTLS-version i huvudet.</span><span class="sxs-lookup"><span data-stu-id="10b69-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received DTLS message had an unknown DTLS version in its header.</span></span>
- <span data-ttu-id="10b69-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) ett MOTTAGet DTLS-meddelande hade en känd men DTLS-version som inte stöds i rubriken.</span><span class="sxs-lookup"><span data-stu-id="10b69-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received DTLS message had a known but unsupported DTLS version in its header.</span></span>
- <span data-ttu-id="10b69-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Det gick inte att tilldela en intern TLS-paket.</span><span class="sxs-lookup"><span data-stu-id="10b69-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="10b69-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) fjärrvärden tillhandahöll ett ogiltigt certifikat.</span><span class="sxs-lookup"><span data-stu-id="10b69-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="10b69-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) den fjärranslutna värden skickade en avisering som indikerar ett fel och att TLS-sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="10b69-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="10b69-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0X13B) en post i ciphersuite-tabellen hade en funktion pekare till null.</span><span class="sxs-lookup"><span data-stu-id="10b69-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="10b69-166">**NX_PTR_ERROR** (0X07) ogiltig session, socket eller adress pekare.</span><span class="sxs-lookup"><span data-stu-id="10b69-166">**NX_PTR_ERROR** (0x07) Invalid session, socket, or address pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-167">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-167">Allowed From</span></span>

<span data-ttu-id="10b69-168">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-169">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-169">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                           &nx_crypto_tls_ciphers,
                                           crypto_metadata,
                                           sizeof(crypto_metadata),
                                           packet_buffer,
                                           sizeof(packet_buffer),
                                           REMOTE_CERT_NUMBER,
                                           remote_certs_buffer,
                                           sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
       Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                      trusted_cert_der,
                                      trusted_cert_der_len,
                                      NX_NULL, 0, NX_NULL, 0,
                                      NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                   &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                  &udp_socket, &server_ip,
                                                  4443,
                                                  NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
      /* Error! */
      return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="10b69-170">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-170">See Also</span></span>

- <span data-ttu-id="10b69-171">nx_secure_dtls_session_receive nx_secure_dtls_session_send,</span><span class="sxs-lookup"><span data-stu-id="10b69-171">nx_secure_dtls_session_receive, nx_secure_dtls_session_send,</span></span>
- <span data-ttu-id="10b69-172">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="10b69-172">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_packet_allocate"></a><span data-ttu-id="10b69-173">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="10b69-173">nx_secure_dtls_packet_allocate</span></span>

<span data-ttu-id="10b69-174">Allokera ett paket för en NetX Secure DTLS-session</span><span class="sxs-lookup"><span data-stu-id="10b69-174">Allocate a packet for a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-175">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-175">Prototype</span></span>

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="10b69-176">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-176">Description</span></span>

<span data-ttu-id="10b69-177">Den här tjänsten allokerar en NX_PACKET för den angivna aktiva DTLS-sessionen från den angivna NX_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="10b69-177">This service allocates an NX_PACKET for the specified active DTLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="10b69-178">Den här tjänsten ska anropas av programmet för att allokera data paket som ska skickas via en DTLS-anslutning.</span><span class="sxs-lookup"><span data-stu-id="10b69-178">This service should be called by the application to allocate data packets to be sent over a DTLS connection.</span></span> <span data-ttu-id="10b69-179">DTLS-sessionen måste initieras innan den här tjänsten anropas.</span><span class="sxs-lookup"><span data-stu-id="10b69-179">The DTLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="10b69-180">Det allokerade paketet initieras korrekt så att DTLS huvud-och sid fots data kan läggas till efter att paket data har fyllts i.</span><span class="sxs-lookup"><span data-stu-id="10b69-180">The allocated packet is properly initialized so that DTLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="10b69-181">Beteendet är annars identiskt med *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="10b69-181">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-182">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-182">Parameters</span></span>

- <span data-ttu-id="10b69-183">**session_ptr** Pekare till en DTLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-183">**session_ptr** Pointer to a DTLS Session instance.</span></span>
- <span data-ttu-id="10b69-184">**pool_ptr** Pekar till en NX_PACKET_POOL som paketet ska allokeras från.</span><span class="sxs-lookup"><span data-stu-id="10b69-184">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="10b69-185">**packet_ptr** Utmatnings pekare till det nyligen allokerade paketet.</span><span class="sxs-lookup"><span data-stu-id="10b69-185">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="10b69-186">**wait_option** Uppehålls alternativ för paket tilldelning.</span><span class="sxs-lookup"><span data-stu-id="10b69-186">**wait_option** Suspension option for packet allocation.</span></span>


### <a name="return-values"></a><span data-ttu-id="10b69-187">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-187">Return Values</span></span>

- <span data-ttu-id="10b69-188">**NX_SUCCESS** (0x00) paket tilldelningen lyckades.</span><span class="sxs-lookup"><span data-stu-id="10b69-188">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="10b69-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) den underliggande paket tilldelningen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="10b69-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="10b69-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0X101) den angivna DTLS-sessionen initierades inte.</span><span class="sxs-lookup"><span data-stu-id="10b69-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied DTLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-191">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-191">Allowed From</span></span>

<span data-ttu-id="10b69-192">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-192">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-193">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-193">Example</span></span>

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a><span data-ttu-id="10b69-194">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-194">See Also</span></span>

- <span data-ttu-id="10b69-195">nx_secure_x509_certificate_initialize nx_secure_dtls_session_create,</span><span class="sxs-lookup"><span data-stu-id="10b69-195">nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,</span></span>
- <span data-ttu-id="10b69-196">nx_secure_dtls_session_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="10b69-196">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="10b69-197">nx_secure_dtls_session_send nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="10b69-197">nx_secure_dtls_session_send, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="10b69-198">nx_secure_dtls_session_end nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="10b69-198">nx_secure_dtls_session_end, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_psk_add"></a><span data-ttu-id="10b69-199">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="10b69-199">nx_secure_dtls_psk_add</span></span>

<span data-ttu-id="10b69-200">Lägga till en i förväg delad nyckel till en NetX Secure DTLS-session</span><span class="sxs-lookup"><span data-stu-id="10b69-200">Add a Pre-Shared Key to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-201">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-201">Prototype</span></span>

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="10b69-202">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-202">Description</span></span>

<span data-ttu-id="10b69-203">Den här tjänsten lägger till en i förväg delad nyckel (PSK), dess identitets sträng och ett identitets tips till ett DTLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-203">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Session control block.</span></span> <span data-ttu-id="10b69-204">PSK används i stället för ett digitalt certifikat när PSK-krypteringssviter är aktiverade och används.</span><span class="sxs-lookup"><span data-stu-id="10b69-204">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-205">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-205">Parameters</span></span>

- <span data-ttu-id="10b69-206">**session_ptr** Pekar till en tidigare skapad DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-206">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="10b69-207">**pre_shared_key** Det faktiska PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="10b69-207">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="10b69-208">**psk_length** PSK-värdets längd.</span><span class="sxs-lookup"><span data-stu-id="10b69-208">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="10b69-209">**psk_identity** En sträng som används för att identifiera det här PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="10b69-209">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="10b69-210">**identity_length** PSK-identitetens längd.</span><span class="sxs-lookup"><span data-stu-id="10b69-210">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="10b69-211">**tips** En sträng som används för att ange vilken grupp av PSKs som ska väljas på en TLS-server.</span><span class="sxs-lookup"><span data-stu-id="10b69-211">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="10b69-212">**hint_length** Längden på tips strängen.</span><span class="sxs-lookup"><span data-stu-id="10b69-212">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-213">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-213">Return Values</span></span>

- <span data-ttu-id="10b69-214">**NX_SUCCESS** (0x00) tillägget av PSK lyckades.</span><span class="sxs-lookup"><span data-stu-id="10b69-214">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="10b69-215">**NX_PTR_ERROR** (0X07) ogiltig DTLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-215">**NX_PTR_ERROR** (0x07) Invalid DTLS session pointer.</span></span>
- <span data-ttu-id="10b69-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) kan inte lägga till en annan PSK.</span><span class="sxs-lookup"><span data-stu-id="10b69-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-217">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-217">Allowed From</span></span>

<span data-ttu-id="10b69-218">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-218">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-219">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-219">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a><span data-ttu-id="10b69-220">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-220">See Also</span></span>

- <span data-ttu-id="10b69-221">nx_secure_dtls_server_psk_add nx_secure_dtls_client_session_create</span><span class="sxs-lookup"><span data-stu-id="10b69-221">nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create</span></span>

## <a name="nx_secure_dtls_server_create"></a><span data-ttu-id="10b69-222">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="10b69-222">nx_secure_dtls_server_create</span></span>

<span data-ttu-id="10b69-223">Skapa en säker DTLS-Server för NetX</span><span class="sxs-lookup"><span data-stu-id="10b69-223">Create a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-224">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-224">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_create(
                NX_SECURE_DTLS_SERVER *server_ptr, NX_IP *ip_ptr,
                UINT port, ULONG timeout, VOID *session_buffer,
                UINT session_buffer_size,
                const NX_SECURE_TLS_CRYPTO *crypto_table,
                VOID *crypto_metadata_buffer, ULONG crypto_metadata_size,
                UCHAR *packet_reassembly_buffer,
                UINT packet_reassembly_buffer_size,
                UINT (*connect_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session,
                              NXD_ADDRESS *ip_address, UINT port),
                UINT (*receive_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session)));

```

### <a name="description"></a><span data-ttu-id="10b69-225">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-225">Description</span></span>

<span data-ttu-id="10b69-226">Den här tjänsten skapar en instans av en DTLS-Server för att hantera inkommande DTLS-begäranden på en viss UDP-port.</span><span class="sxs-lookup"><span data-stu-id="10b69-226">This service creates an instance of a DTLS server to handle incoming DTLS requests on a particular UDP port.</span></span> <span data-ttu-id="10b69-227">På grund av det faktum att UDP är tillstånds löst kan DTLS-begäranden från flera klienter komma in på en enda port medan andra DTLS-sessioner är aktiva.</span><span class="sxs-lookup"><span data-stu-id="10b69-227">Due to the fact that UDP is stateless, DTLS requests from multiple clients can come in on a single port while other DTLS sessions are active.</span></span> <span data-ttu-id="10b69-228">Därför behövs servern för att underhålla aktiva sessioner och dirigera inkommande meddelanden korrekt till rätt hanterare.</span><span class="sxs-lookup"><span data-stu-id="10b69-228">Thus, the server is needed to maintain active sessions and properly route incoming messages to the proper handler.</span></span>

<span data-ttu-id="10b69-229">Ip_ptr-parametern pekar på en NX_IP-instans som ska användas för den interna UDP-socket som är associerad med DTLS-servern (och lagras i NX_SECURE_DTLS_SERVER kontroll block).</span><span class="sxs-lookup"><span data-stu-id="10b69-229">The ip_ptr parameter points to an NX_IP instance to be used for the internal UDP socket associated with the DTLS Server (and stored in the NX_SECURE_DTLS_SERVER control block).</span></span> <span data-ttu-id="10b69-230">IP-instansen och porten används för att definiera UDP-gränssnittet då servern instansieras med nx_secure_dtls_server_start tjänsten.</span><span class="sxs-lookup"><span data-stu-id="10b69-230">The IP instance and port are used to define the UDP interface upon which the server is instantiated with the nx_secure_dtls_server_start service.</span></span>

<span data-ttu-id="10b69-231">Parametern session buffer används för att hålla kontroll blocken för alla möjliga samtidiga DTLS-sessioner för DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-231">The session buffer parameter is used to hold the control blocks for all the possible simultaneous DTLS sessions for the DTLS server.</span></span> <span data-ttu-id="10b69-232">Den bör tilldelas en storlek som är jämnt delbar med storleken på den NX_SECURE_DTLS_SESSION kontroll block strukturen.</span><span class="sxs-lookup"><span data-stu-id="10b69-232">It should be allocated with a size that is an even multiple of the size of the NX_SECURE_DTLS_SESSION control block structure.</span></span>

<span data-ttu-id="10b69-233">Om du vill beräkna nödvändig metadata-storlek kan API-nx_secure_tls_metadata_size_calculate användas.</span><span class="sxs-lookup"><span data-stu-id="10b69-233">To calculate the necessary metadata size, the API nx_secure_tls_metadata_size_calculate may be used.</span></span>

<span data-ttu-id="10b69-234">Parametern packet_reassembly_buffer används av DTLS för att ommontera UDP-datagram till en fullständig DTLS-post för dekryptering och bör vara tillräckligt stor för att rymma den största förväntade DTLS-posten (16 KB är den DTLS maximala post storleken, men många program skickar inte samma data i samma post).</span><span class="sxs-lookup"><span data-stu-id="10b69-234">The packet_reassembly_buffer parameter is used by DTLS to reassemble UDP datagrams into a complete DTLS record for the purposes of decryption and should be large enough to accommodate the largest expected DTLS record (16KB is the DTLS maximum record size but many applications don’t send that much data in a single record).</span></span>

<span data-ttu-id="10b69-235">Rutinen för connect_notify motringning anropas när en ny DTLS-klient ansluter till servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-235">The connect_notify callback routine is invoked whenever a new DTLS client connects to the server.</span></span> <span data-ttu-id="10b69-236">Det är upp till programmet att starta DTLS-sessionen med hjälp av tjänsten *nx_secure_dtls_server_session_start*.</span><span class="sxs-lookup"><span data-stu-id="10b69-236">It is up to the application to then start the DTLS session using the service *nx_secure_dtls_server_session_start*.</span></span> <span data-ttu-id="10b69-237">Även om sessionen kan startas i själva återanropet rekommenderar vi att återanropet endast används för att meddela program tråden (eller dedikerade DTLS-tråden som skapats av programmet) för anslutningen när motringningen anropas av IP-tråden som används för att bearbeta all nätverks bearbetning på lägre nivå (t. ex. UDP).</span><span class="sxs-lookup"><span data-stu-id="10b69-237">While the session may be started in the callback itself, it is recommended that the callback only be used to notify the application thread (or dedicated DTLS thread created by the application) of the connection as the callback is invoked by the IP thread which is used to process all lower-level network processing (e.g. UDP).</span></span> <span data-ttu-id="10b69-238">Detta kan vara lika enkelt som att spara DTLS (anges som en parameter till återanropet) och anropa nx_secure_dtls_server_session_start i den andra tråden.</span><span class="sxs-lookup"><span data-stu-id="10b69-238">This can be as simple as saving the DTLS session parameter (provided as a parameter to the callback) and invoking nx_secure_dtls_server_session_start in the other thread.</span></span> <span data-ttu-id="10b69-239">Connect_notify motringning bör normalt returnera NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="10b69-239">The connect_notify callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="10b69-240">Rutinen för receive_notify motringning anropas när en DTLS-post tas emot som matchar en befintlig upprättad DTLS-session (IP-adress och port för fjärrvärden används för att identifiera en befintlig session).</span><span class="sxs-lookup"><span data-stu-id="10b69-240">The receive_notify callback routine is invoked whenever a DTLS record is received that matches an existing established DTLS session (the remote host IP address and port are used to identify an existing session).</span></span> <span data-ttu-id="10b69-241">Detta representerar de "program data" som krypteras och skickas via DTLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-241">This represents the “application data” that is encrypted and sent over DTLS.</span></span> <span data-ttu-id="10b69-242">Programmet måste anropa tjänsten *nx_secure_dtls_session_receive* på den angivna DTLS-sessionen för att hämta mottagna data.</span><span class="sxs-lookup"><span data-stu-id="10b69-242">The application must call the service *nx_secure_dtls_session_receive* on the provided DTLS session to retrieve the received data.</span></span> <span data-ttu-id="10b69-243">Precis som med connect_receive motringning rekommenderar vi att sessionen skickas till en annan tråd för att hantera meddelande bearbetningen när återanropet anropas från IP-tråden.</span><span class="sxs-lookup"><span data-stu-id="10b69-243">As with the connect_receive callback, it is recommended that the session be passed to another thread to handle the message processing as the callback is invoked from the IP thread.</span></span> <span data-ttu-id="10b69-244">Receive_notify motringning bör normalt returnera NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="10b69-244">The receive_notify callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-245">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-245">Parameters</span></span>

- <span data-ttu-id="10b69-246">**server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="10b69-246">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="10b69-247">**ip_ptr** Pekar mot ett initierat NX_IP kontroll block som ska användas som nätverks gränssnitt för DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-247">**ip_ptr** Pointer to an initialized NX_IP control block to use as the network interface for the DTLS server.</span></span>
- <span data-ttu-id="10b69-248">**port** Den lokala UDP-porten som DTLS-serverns UDP-socket är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="10b69-248">**port** The local UDP port to which the DTLS server UDP socket is bound.</span></span>
- <span data-ttu-id="10b69-249">**tids gräns** Tids gräns värde som ska användas för nätverks åtgärder.</span><span class="sxs-lookup"><span data-stu-id="10b69-249">**timeout** Timeout value to use for network operations.</span></span>
- <span data-ttu-id="10b69-250">**session_buffer** Buffertutrymme som innehåller kontroll block för alla instanser av NX_SECURE_DTLS_SESSION som tilldelats den här DTLS-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="10b69-250">**session_buffer** Buffer space to contain control blocks for all instances of NX_SECURE_DTLS_SESSION assigned to this DTLS Server instance.</span></span>
- <span data-ttu-id="10b69-251">**session_buffer_size** Storlek på bufferten för session.</span><span class="sxs-lookup"><span data-stu-id="10b69-251">**session_buffer_size** Size of the session buffer.</span></span> <span data-ttu-id="10b69-252">Detta avgör antalet DTLS-sessioner som tilldelats DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-252">This determines the number of DTLS sessions assigned to the DTLS Server.</span></span>
- <span data-ttu-id="10b69-253">**crypto_table** Pekare till en TLS/DTLS krypterings tabell struktur som används för alla kryptografiska åtgärder.</span><span class="sxs-lookup"><span data-stu-id="10b69-253">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="10b69-254">**crypto_metadata_buffer** Buffertutrymme för kryptografiska åtgärds beräkningar och statusinformation.</span><span class="sxs-lookup"><span data-stu-id="10b69-254">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="10b69-255">**crypto_metadata_size** Storlek på buffert för metadata.</span><span class="sxs-lookup"><span data-stu-id="10b69-255">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="10b69-256">**packet_reassembly_buffer** Buffert som används av DTLS för att ommontera UDP-data i DTLS-poster för dekryptering.</span><span class="sxs-lookup"><span data-stu-id="10b69-256">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="10b69-257">**packet_reassembly_buffer_size** Storlek på omassembly buffer.</span><span class="sxs-lookup"><span data-stu-id="10b69-257">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="10b69-258">Bör normalt vara större än 16 KB, men kan vara mindre beroende på program.</span><span class="sxs-lookup"><span data-stu-id="10b69-258">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="10b69-259">**connect_notify** Callback-rutin som anropas när en fjärran sluten DTLS-klient försöker ansluta till den här DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-259">**connect_notify** Callback routine invoked whenever a remote DTLS Client attempts to connect to this DTLS server.</span></span>
- <span data-ttu-id="10b69-260">**receive_notify** Motringning anropades när program data tas emot över en befintlig DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-260">**receive_notify** Callback invoked whenever application data is received over an existing DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-261">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-261">Return Values</span></span>

- <span data-ttu-id="10b69-262">**NX_SUCCESS** (0x00) skapandet av DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-262">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="10b69-263">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-263">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-264">**NX_INVALID_PARAMETERS** (0X4D) det finns inte tillräckligt med buffertutrymme för sessioner, paket omsammansättning eller kryptografi.</span><span class="sxs-lookup"><span data-stu-id="10b69-264">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for sessions, packet reassembly, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-265">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-265">Allowed From</span></span>

<span data-ttu-id="10b69-266">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-267">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-267">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
    *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE, dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                        device_cert_der_len, NX_NULL, 0,
                        device_cert_key_der, device_cert_key_der_len,
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                           NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                                                   &send_packet, NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data,
        let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done, stop the server
    instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="10b69-268">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-268">See Also</span></span>

- <span data-ttu-id="10b69-269">nx_secure_dtls_server_start nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="10b69-269">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="10b69-270">nx_secure_dtls_session_receive nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="10b69-270">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="10b69-271">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="10b69-271">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="10b69-272">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="10b69-272">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="10b69-273">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="10b69-273">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_delete"></a><span data-ttu-id="10b69-274">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="10b69-274">nx_secure_dtls_server_delete</span></span>

<span data-ttu-id="10b69-275">Frigör resurser som används av en säker DTLS-server med NetX</span><span class="sxs-lookup"><span data-stu-id="10b69-275">Free up resources used by a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-276">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-276">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="10b69-277">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-277">Description</span></span>

<span data-ttu-id="10b69-278">Den här tjänsten frigör de resurser som har allokerats till en DTLS-serverinstans, inklusive den interna UDP-socket som används av servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-278">This service frees up the resources allocated to a DTLS Server instance, including the internal UDP socket used by the server.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-279">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-279">Parameters</span></span>

- <span data-ttu-id="10b69-280">**server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="10b69-280">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-281">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-281">Return Values</span></span>

- <span data-ttu-id="10b69-282">**NX_SUCCESS** (0x00) borttagning av server lyckades.</span><span class="sxs-lookup"><span data-stu-id="10b69-282">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="10b69-283">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-283">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-284">**NX_STILL_BOUND** (0X42) UDP-socket är fortfarande kopplad.</span><span class="sxs-lookup"><span data-stu-id="10b69-284">**NX_STILL_BOUND** (0x42) UDP socket is still bound.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-285">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-285">Allowed From</span></span>

<span data-ttu-id="10b69-286">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-287">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-287">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
*ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer, sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);


    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                         NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                        &packet_pool,
                                                        &send_packet,
                                                        NX_IP_PERIODIC_RATE);

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="10b69-288">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-288">See Also</span></span>

- <span data-ttu-id="10b69-289">nx_secure_dtls_server_start nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="10b69-289">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="10b69-290">nx_secure_dtls_session_receive nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="10b69-290">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="10b69-291">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="10b69-291">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_local_certificate_add"></a><span data-ttu-id="10b69-292">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="10b69-292">nx_secure_dtls_server_local_certificate_add</span></span>

<span data-ttu-id="10b69-293">Lägga till ett lokalt Server identitets certifikat till en säker DTLS-server med NetX</span><span class="sxs-lookup"><span data-stu-id="10b69-293">Add a local server identity certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-294">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-294">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="10b69-295">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-295">Description</span></span>

<span data-ttu-id="10b69-296">Den här tjänsten lägger till ett lokalt Server identitets certifikat till en DTLS-Server instans.</span><span class="sxs-lookup"><span data-stu-id="10b69-296">This service adds a local server identity certificate to a DTLS Server instance.</span></span> <span data-ttu-id="10b69-297">Minst ett identitets certifikat krävs för att klienter ska kunna ansluta till en DTLS-Server, om inte en annan autentiseringsmekanism (t. ex. i förväg delade nycklar) används.</span><span class="sxs-lookup"><span data-stu-id="10b69-297">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="10b69-298">Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet.</span><span class="sxs-lookup"><span data-stu-id="10b69-298">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="10b69-299">Detta gör att certifikatet enkelt kan tas bort eller hittas i händelse av att det finns flera identitets certifikat med samma X. 509-namn som finns i DTLS-serverns arkiv.</span><span class="sxs-lookup"><span data-stu-id="10b69-299">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="10b69-300">Mer information om X. 509-servercertifikat finns i användar handboken för NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-300">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-301">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-301">Parameters</span></span>

- <span data-ttu-id="10b69-302">**server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="10b69-302">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="10b69-303">**certifikat** Pekar till en tidigare initierad X. 509-certifikat struktur.</span><span class="sxs-lookup"><span data-stu-id="10b69-303">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="10b69-304">**cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-304">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-305">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-305">Return Values</span></span>

- <span data-ttu-id="10b69-306">**NX_SUCCESS** (0x00) tillägget av certifikat till DTLS-servern har slutförts.</span><span class="sxs-lookup"><span data-stu-id="10b69-306">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="10b69-307">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-307">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-308">**NX_INVALID_PARAMETERS** (0X4D) ett certifikat-ID på 0 skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-308">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-309">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-309">Allowed From</span></span>

<span data-ttu-id="10b69-310">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-311">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-311">Example</span></span>

<span data-ttu-id="10b69-312">\* Se referens för *nx_secure_dtls_server_create* ett mer komplett exempel.</span><span class="sxs-lookup"><span data-stu-id="10b69-312">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                            certificate_der_data,
                            sizeof(certificate_der_data),
                            NX_NULL, 0,
                            certificate_key_der_data,
                            sizeof(certificate_key_der_data),
                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a><span data-ttu-id="10b69-313">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-313">See Also</span></span>

- <span data-ttu-id="10b69-314">nx_secure_dtls_server_start nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="10b69-314">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="10b69-315">nx_secure_dtls_session_receive nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="10b69-315">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="10b69-316">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="10b69-316">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="10b69-317">nx_secure_dtls_server_local_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="10b69-317">nx_secure_dtls_server_local_certificate_remove,</span></span>
- <span data-ttu-id="10b69-318">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="10b69-318">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_local_certificate_remove"></a><span data-ttu-id="10b69-319">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="10b69-319">nx_secure_dtls_server_local_certificate_remove</span></span>

<span data-ttu-id="10b69-320">Ta bort ett lokalt Server identitets certifikat från en NetX säker DTLS-Server</span><span class="sxs-lookup"><span data-stu-id="10b69-320">Remove a local server identity certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-321">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-321">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="10b69-322">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-322">Description</span></span>

<span data-ttu-id="10b69-323">Den här tjänsten tar bort ett lokalt Server identitets certifikat från en DTLS-Server instans.</span><span class="sxs-lookup"><span data-stu-id="10b69-323">This service removes a local server identity certificate from a DTLS Server instance.</span></span> <span data-ttu-id="10b69-324">Minst ett identitets certifikat krävs för att klienter ska kunna ansluta till en DTLS-Server, om inte en annan autentiseringsmekanism (t. ex. i förväg delade nycklar) används.</span><span class="sxs-lookup"><span data-stu-id="10b69-324">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="10b69-325">Det certifikat som ska tas bort kan identifieras antingen av sitt unika X. 509-namn eller av det numeriska cert_id som tilldelades i anropet till *nx_secure_dtls_server_local_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="10b69-325">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_local_certificate_add*.</span></span> <span data-ttu-id="10b69-326">Cert_id används bara för att identifiera certifikatet och underhålls av programmet.</span><span class="sxs-lookup"><span data-stu-id="10b69-326">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="10b69-327">Om det egna namnet används i stället för det numeriska certifikat-ID: n ska parametern cert_id anges till 0.</span><span class="sxs-lookup"><span data-stu-id="10b69-327">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="10b69-328">Att ta bort ett certifikat medan en DTLS-handskakning bearbetas resulterar i ett oväntat beteende.</span><span class="sxs-lookup"><span data-stu-id="10b69-328">Removing a certificate while a DTLS handshake is being processed will result in unexpected behavior.</span></span> <span data-ttu-id="10b69-329">Tjänst *nx_secure_dtls_server_stop* ska anropas innan certifikat tas bort.</span><span class="sxs-lookup"><span data-stu-id="10b69-329">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-330">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-330">Parameters</span></span>

- <span data-ttu-id="10b69-331">**server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="10b69-331">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="10b69-332">**common_name** X. 509-CommonName för det certifikat som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="10b69-332">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="10b69-333">Om det används skickar cert_id som noll.</span><span class="sxs-lookup"><span data-stu-id="10b69-333">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="10b69-334">**common_name_length** Längden på common_name sträng i byte.</span><span class="sxs-lookup"><span data-stu-id="10b69-334">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="10b69-335">**cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-335">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="10b69-336">Om detta används kan du skicka NX_NULL för common_name-parametern.</span><span class="sxs-lookup"><span data-stu-id="10b69-336">If this is used, pass NX_NULL for the common_name parameter.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-337">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-337">Return Values</span></span>

- <span data-ttu-id="10b69-338">**NX_SUCCESS** (0x00) borttagning av certifikat från DTLS-servern har slutförts.</span><span class="sxs-lookup"><span data-stu-id="10b69-338">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="10b69-339">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-339">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det gick inte att hitta något certifikat som matchar cert_id eller common_name på den aktuella DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-341">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-341">Allowed From</span></span>

<span data-ttu-id="10b69-342">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-343">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-343">Example</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        certificate_der_data,
                                        sizeof(certificate_der_data),
                                        NX_NULL, 0, certificate_key_der_data,
                                        sizeof(certificate_key_der_data),
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                     &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);

    /* At some point in the future we decide to remove the certificate we added.
    We can use the certificate identifier we passed into the call to
    nx_secure_dtls_local_certificate_add (value = 1); */
    status = nx_secure_dtls_server_local_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a><span data-ttu-id="10b69-344">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-344">See Also</span></span>

- <span data-ttu-id="10b69-345">nx_secure_dtls_server_start nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="10b69-345">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="10b69-346">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="10b69-346">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="10b69-347">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="10b69-347">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="10b69-348">nx_secure_dtls_server_local_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="10b69-348">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="10b69-349">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="10b69-349">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_notify_set"></a><span data-ttu-id="10b69-350">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="10b69-350">nx_secure_dtls_server_notify_set</span></span>

<span data-ttu-id="10b69-351">Tilldela en säker NetX DTLS-Server för valfria meddelanden</span><span class="sxs-lookup"><span data-stu-id="10b69-351">Assign optional notification callback routines to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-352">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-352">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a><span data-ttu-id="10b69-353">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-353">Description</span></span>

<span data-ttu-id="10b69-354">Den här tjänsten kan användas för att lägga till valfria rutiner för återuppringning av meddelanden på en DTLS-Server.</span><span class="sxs-lookup"><span data-stu-id="10b69-354">This service can be used to add optional notification callback routines to a DTLS server.</span></span> <span data-ttu-id="10b69-355">Antingen kan callback-parametern skickas som NX_NULL om bara ett återanrop önskas.</span><span class="sxs-lookup"><span data-stu-id="10b69-355">Either callback parameter may be passed as NX_NULL if only one callback is desired.</span></span>

<span data-ttu-id="10b69-356">Disconnect_notify motringning anropas när en fjärrklient avslutar en DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-356">The disconnect_notify callback is invoked when a remote client ends a DTLS session.</span></span> <span data-ttu-id="10b69-357">Parametern dtls_session är den instans som stängdes.</span><span class="sxs-lookup"><span data-stu-id="10b69-357">The dtls_session parameter is the session instance that was closed.</span></span> <span data-ttu-id="10b69-358">Återanropet bör normalt returnera NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="10b69-358">The callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="10b69-359">Error_notify motringning anropas när ett DTLS-fel eller en timeout inträffar.</span><span class="sxs-lookup"><span data-stu-id="10b69-359">The error_notify callback is invoked whenever a DTLS error or timeout occurs.</span></span> <span data-ttu-id="10b69-360">Parametern dtls_session är den session som felet inträffat för och error_code är den numeriska status koden för det fel som orsakade problemet (se bilaga A)</span><span class="sxs-lookup"><span data-stu-id="10b69-360">The dtls_session parameter is the session instance for which the error occurred, and error_code is the numeric status code for the error that caused the issue (see Appendix A)</span></span>

<span data-ttu-id="10b69-361">NetX Secure Return/Error Codes för en lista över felkoder som kan returneras).</span><span class="sxs-lookup"><span data-stu-id="10b69-361">NetX Secure Return/Error Codes for a list of error codes that may be returned).</span></span> <span data-ttu-id="10b69-362">Återanropet bör normalt returnera NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="10b69-362">The callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-363">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-363">Parameters</span></span>

- <span data-ttu-id="10b69-364">**server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="10b69-364">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="10b69-365">**disconnect_notify** Callback-rutin som anropas när en fjärran sluten klient värd stänger en DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-365">**disconnect_notify** Callback routine invoked whenever a remote client host closes a DTLS session.</span></span>
- <span data-ttu-id="10b69-366">**error_notify** Callback-rutin anropas när DTLS påträffar ett fel eller en timeout.</span><span class="sxs-lookup"><span data-stu-id="10b69-366">**error_notify** Callback routine invoked whenever DTLS encounters an error or timeout.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-367">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-367">Return Values</span></span>

- <span data-ttu-id="10b69-368">**NX_SUCCESS** (0x00) har slutfört tilldelning av återkallnings rutiner.</span><span class="sxs-lookup"><span data-stu-id="10b69-368">**NX_SUCCESS** (0x00) Successful assignment of callback routines.</span></span>
- <span data-ttu-id="10b69-369">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-369">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-370">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-370">Allowed From</span></span>

<span data-ttu-id="10b69-371">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-371">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-372">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-372">Example</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

UINT disconnect_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
NXD_ADDRESS client_ip_addr;
UINT client_port;
UINT local_port;

    /* We have received a disconnection notice (CloseNotify message) from a
       remote client. Application can use the dtls_session parameter for any
       desired processing. */

    /* See what client disconnected by extracting its IP address and port.
       NOTE: depending on how the session ended, the client information may
             no longer be available. */
    status  = nx_secure_dtls_session_client_info_get(dtls_session,
                                                    &ip_addr,
                                                    &client_port,
                                                    &local_port);

    return(NX_SUCCESS);
}

UINT error_notify(NX_SECURE_DTLS_SESSION *dtls_session, UINT error_code)
{
    /* The DTLS server has encountered an error or timeout condition. We
    can use the error_code parameter to determine the error and we
    can insect the dtls_session for more information. */

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Other setup (e.g. certificates) goes here … */

    status = nx_secure_dtls_server_notify_set(&dtls_server, disconnect_notify,
                                                                 error_notify);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

}

```

### <a name="see-also"></a><span data-ttu-id="10b69-373">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-373">See Also</span></span>

- <span data-ttu-id="10b69-374">nx_secure_dtls_server_start nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="10b69-374">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="10b69-375">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="10b69-375">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="10b69-376">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="10b69-376">nx_secure_dtls_server_session_stop</span></span>

## <a name="nx_secure_dtls_server_psk_add"></a><span data-ttu-id="10b69-377">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="10b69-377">nx_secure_dtls_server_psk_add</span></span>

<span data-ttu-id="10b69-378">Lägga till en i förväg delad nyckel till en NetX säker DTLS-Server</span><span class="sxs-lookup"><span data-stu-id="10b69-378">Add a Pre-Shared Key to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-379">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-379">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a><span data-ttu-id="10b69-380">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-380">Description</span></span>

<span data-ttu-id="10b69-381">Den här tjänsten lägger till en i förväg delad nyckel (PSK), dess identitets sträng och ett identitets tips till ett DTLS Server Control Block.</span><span class="sxs-lookup"><span data-stu-id="10b69-381">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Server control block.</span></span> <span data-ttu-id="10b69-382">PSK används i stället för ett digitalt certifikat när PSK-krypteringssviter är aktiverade och används.</span><span class="sxs-lookup"><span data-stu-id="10b69-382">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="10b69-383">PSK som läggs till replikeras över alla DTLS-sessioner som tilldelats DTLS-servern (via den session-buffert som anges i anropet till nx_secure_dtls_server_create).</span><span class="sxs-lookup"><span data-stu-id="10b69-383">The PSK that is added is replicated across all the DTLS sessions assigned to the DTLS Server (via the session buffer given in the call to nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-384">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-384">Parameters</span></span>

- <span data-ttu-id="10b69-385">**server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="10b69-385">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="10b69-386">**pre_shared_key** Det faktiska PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="10b69-386">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="10b69-387">**psk_length** PSK-värdets längd.</span><span class="sxs-lookup"><span data-stu-id="10b69-387">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="10b69-388">**psk_identity** En sträng som används för att identifiera det här PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="10b69-388">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="10b69-389">**identity_length** PSK-identitetens längd.</span><span class="sxs-lookup"><span data-stu-id="10b69-389">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="10b69-390">**tips** En sträng som används för att ange vilken grupp av PSKs som ska väljas på en TLS-server.</span><span class="sxs-lookup"><span data-stu-id="10b69-390">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="10b69-391">**hint_length** Längden på tips strängen.</span><span class="sxs-lookup"><span data-stu-id="10b69-391">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-392">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-392">Return Values</span></span>

- <span data-ttu-id="10b69-393">**NX_SUCCESS** (0x00) tillägget av PSK lyckades.</span><span class="sxs-lookup"><span data-stu-id="10b69-393">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="10b69-394">**NX_PTR_ERROR** (0X07) ogiltig DTLS-Server pekare.</span><span class="sxs-lookup"><span data-stu-id="10b69-394">**NX_PTR_ERROR** (0x07) Invalid DTLS server pointer.</span></span>
- <span data-ttu-id="10b69-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) kan inte lägga till en annan PSK.</span><span class="sxs-lookup"><span data-stu-id="10b69-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-396">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-396">Allowed From</span></span>

<span data-ttu-id="10b69-397">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-398">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-398">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a><span data-ttu-id="10b69-399">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-399">See Also</span></span>

- <span data-ttu-id="10b69-400">nx_secure_dtls_psk_add nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="10b69-400">nx_secure_dtls_psk_add, nx_secure_dtls_server_create</span></span>

## <a name="nx_secure_dtls_server_session_send"></a><span data-ttu-id="10b69-401">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="10b69-401">nx_secure_dtls_server_session_send</span></span>

<span data-ttu-id="10b69-402">Skicka data via en DTLS-session som upprättats med en NetX-säker DTLS-Server</span><span class="sxs-lookup"><span data-stu-id="10b69-402">Send data over a DTLS session established with a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-403">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-403">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="10b69-404">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-404">Description</span></span>

<span data-ttu-id="10b69-405">Den här tjänsten skickar ett data paket över en etablerad DTLS-server till en fjärran sluten DTLS-klient värd.</span><span class="sxs-lookup"><span data-stu-id="10b69-405">This service sends a packet of data over an established DTLS Server session to a remote DTLS Client host.</span></span> <span data-ttu-id="10b69-406">Den använda sessionen hämtas i receive_notify callback-rutinen som nx_secure_dtls_session_create.</span><span class="sxs-lookup"><span data-stu-id="10b69-406">The session used is obtained in the receive_notify callback routine provided to nx_secure_dtls_session_create.</span></span>

<span data-ttu-id="10b69-407">Data som anges i paketet, som måste allokeras med hjälp av *nx_secure_dtls_packet_allocate*, krypteras med hjälp av DTLS-sessionens kryptografiska parametrar och rutiner och skickas sedan till fjärrvärden via DTLS-serverns interna UDP-port till den anslutna klientens IP-adress och port (lagras i DTLS-sessionen).</span><span class="sxs-lookup"><span data-stu-id="10b69-407">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Server internal UDP port to the attached client’s IP address and port (stored in the DTLS Session).</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-408">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-408">Parameters</span></span>

- <span data-ttu-id="10b69-409">**session_ptr** Pekare till en DTLS-instans som hämtats från den receive_notify återanrops rutinen som tillhandahålls av programmet.</span><span class="sxs-lookup"><span data-stu-id="10b69-409">**session_ptr** Pointer to a DTLS session instance obtained from the receive_notify callback routine provided by the application.</span></span>
- <span data-ttu-id="10b69-410">**packet_ptr** Pekare till en NX_PACKET instans som har allokerats tidigare och fyllts med program data.</span><span class="sxs-lookup"><span data-stu-id="10b69-410">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-411">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-411">Return Values</span></span>

- <span data-ttu-id="10b69-412">**NX_SUCCESS** (0x00) skapandet av DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-412">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="10b69-413">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-413">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0X109) ett fel uppstod i den underliggande UDP-åtgärden för att skicka.</span><span class="sxs-lookup"><span data-stu-id="10b69-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-415">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-415">Allowed From</span></span>

<span data-ttu-id="10b69-416">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-417">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-417">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;


/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key
    and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        device_cert_der,
                                        device_cert_der_len,
                                        NX_NULL,
                                        0, device_cert_key_der,
                                        device_cert_key_der_len,
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

}

/* If not processing connections or received data, let the thread sleep. */
if(!connect_flag && !receive_flag)
{
    tx_thread_sleep(100);
}
    }

    /* Server processing is done, stop the server instance
    from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="10b69-418">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-418">See Also</span></span>

- <span data-ttu-id="10b69-419">nx_secure_dtls_server_start nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="10b69-419">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="10b69-420">nx_secure_dtls_session_receive nx_secure_dtls_server_session_create,</span><span class="sxs-lookup"><span data-stu-id="10b69-420">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create,</span></span>
- <span data-ttu-id="10b69-421">nx_secure_dtls_server_session_start nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="10b69-421">nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="10b69-422">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="10b69-422">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_session_start"></a><span data-ttu-id="10b69-423">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="10b69-423">nx_secure_dtls_server_session_start</span></span>

<span data-ttu-id="10b69-424">Starta en DTLS-session från en NetX-säker DTLS-Server</span><span class="sxs-lookup"><span data-stu-id="10b69-424">Start a DTLS Session from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-425">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-425">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="10b69-426">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-426">Description</span></span>

<span data-ttu-id="10b69-427">Den här tjänsten startar en DTLS-Server genom att utföra DTLS-handskakningen på Server sidan när en fjärran sluten DTLS-klient har anslutit till servern och begärt en DTLS-anslutning.</span><span class="sxs-lookup"><span data-stu-id="10b69-427">This service starts a DTLS Server session by performing the server-side DTLS handshake when a remote DTLS Client has connected to the server and requested a DTLS connection.</span></span>

<span data-ttu-id="10b69-428">DTLS-sessionen hämtas i connect_notify callback-rutinen som nx_secure_dtls_server_create.</span><span class="sxs-lookup"><span data-stu-id="10b69-428">The DTLS Session is obtained in the connect_notify callback routine provided to nx_secure_dtls_server_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-429">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-429">Parameters</span></span>

- <span data-ttu-id="10b69-430">**session_ptr** Pekare till en DTLS-instans som hämtats från en DTLS-Server connect_notify motringning.</span><span class="sxs-lookup"><span data-stu-id="10b69-430">**session_ptr** Pointer to a DTLS Session instance obtained from a DTLS Server connect_notify callback.</span></span>
- <span data-ttu-id="10b69-431">**wait_option** ThreadX vänte värde som ska användas för nätverks åtgärder.</span><span class="sxs-lookup"><span data-stu-id="10b69-431">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-432">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-432">Return Values</span></span>

- <span data-ttu-id="10b69-433">**NX_SUCCESS** (0x00) skapandet av DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-433">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="10b69-434">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-434">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0X111) Det gick inte att ALLOKERA ett DTLS-handskaknings paket (Packet bassäng Empty).</span><span class="sxs-lookup"><span data-stu-id="10b69-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a DTLS handshake packet (packet pool empty).</span></span>
- <span data-ttu-id="10b69-436">**NX_SECURE_TLS_INVALID_PACKET** (0X104) emot data som inte var giltiga DTLS-poster.</span><span class="sxs-lookup"><span data-stu-id="10b69-436">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="10b69-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) en DTLS-post kunde inte hashas korrekt (krypterings fel).</span><span class="sxs-lookup"><span data-stu-id="10b69-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="10b69-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) kontroll av krypterings utfyllnad har misslyckats.</span><span class="sxs-lookup"><span data-stu-id="10b69-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="10b69-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) emot en avisering från fjärrvärden under DTLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="10b69-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host during the DTLS handshake.</span></span>
- <span data-ttu-id="10b69-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) fick ett okänt meddelande under DTLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="10b69-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Received an unrecognized message during the DTLS handshake.</span></span>
- <span data-ttu-id="10b69-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) emot en DTLS-post med ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="10b69-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="10b69-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E) tog emot en sitt hälsnings som inte har stöd för DTLS krypteringssviter.</span><span class="sxs-lookup"><span data-stu-id="10b69-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Received a ClientHello with no supported DTLS ciphersuites.</span></span>
- <span data-ttu-id="10b69-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0X118) emot en sitt hälsnings med en okänd komprimerings metod.</span><span class="sxs-lookup"><span data-stu-id="10b69-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) Recevied a ClientHello with a unknown compression method.</span></span>
- <span data-ttu-id="10b69-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0X107) allmänt (ospecificerad) hand skaknings fel, vanligt vis på grund av problem med förlängnings bearbetning.</span><span class="sxs-lookup"><span data-stu-id="10b69-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Generic (unspecified) handshake failure, usually due to problems with extension processing.</span></span>
- <span data-ttu-id="10b69-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0X130) en funktion som ännu inte stöds anropades under DTLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="10b69-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) A feature that is not yet supported was invoked during the DTLS handshake.</span></span>
- <span data-ttu-id="10b69-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0X105) en okänd CIPHERSUITE påträffades (angivet internt kryptografi fel).</span><span class="sxs-lookup"><span data-stu-id="10b69-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicated internal cryptography error).</span></span>
- <span data-ttu-id="10b69-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E) emot en DTLS post med en felmatchad DTLS-version.</span><span class="sxs-lookup"><span data-stu-id="10b69-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>
- <span data-ttu-id="10b69-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0X115) Det gick inte att verifiera DTLS-hand skaknings-hashen, sessionen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="10b69-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) Failed to validate the DTLS handshake hash, session is invalid.</span></span>
- <span data-ttu-id="10b69-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0X109) intern UDP-sändning misslyckades.</span><span class="sxs-lookup"><span data-stu-id="10b69-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Internal UDP send failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-450">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-450">Allowed From</span></span>

<span data-ttu-id="10b69-451">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-452">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-452">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
* DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len, NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                    &packet_pool, &send_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done,
    stop the server instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="10b69-453">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-453">See Also</span></span>

- <span data-ttu-id="10b69-454">nx_secure_dtls_server_start nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="10b69-454">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="10b69-455">nx_secure_dtls_session_receive nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="10b69-455">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="10b69-456">nx_secure_dtls_server_session_create nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="10b69-456">nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="10b69-457">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="10b69-457">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_start"></a><span data-ttu-id="10b69-458">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="10b69-458">nx_secure_dtls_server_start</span></span>

<span data-ttu-id="10b69-459">Starta en NetX säker DTLS-serverinstans som lyssnar på den konfigurerade UDP-porten</span><span class="sxs-lookup"><span data-stu-id="10b69-459">Start a NetX Secure DTLS Server instance listening on the configured UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-460">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-460">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="10b69-461">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-461">Description</span></span>

<span data-ttu-id="10b69-462">Den här tjänsten startar en DTLS-Server.</span><span class="sxs-lookup"><span data-stu-id="10b69-462">This service starts a DTLS Server.</span></span> <span data-ttu-id="10b69-463">När anropet har returnerats är servern aktiv och kommer att börja bearbeta inkommande begär Anden från DTLS-klienter.</span><span class="sxs-lookup"><span data-stu-id="10b69-463">After the call returns, the server is active and will begin processing incoming requests from DTLS clients.</span></span> <span data-ttu-id="10b69-464">Server instansen måste ha kon figurer ATS med tjänsten *nx_secure_dtls_server_create*.</span><span class="sxs-lookup"><span data-stu-id="10b69-464">The server instance must have been configured with the service *nx_secure_dtls_server_create*.</span></span>

> [!NOTE]
> <span data-ttu-id="10b69-465">Den här tjänsten binder den interna DTLS-serverns UDP-port till den konfigurerade lokala porten så att de flesta problem som påträffas kan utföras med UDP-kommunikation och nätverks konfiguration.</span><span class="sxs-lookup"><span data-stu-id="10b69-465">This service binds the internal DTLS Server UDP port to the configured local port so most issues encountered will have to do with UDP communications and network configuration.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-466">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-466">Parameters</span></span>

- <span data-ttu-id="10b69-467">**server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="10b69-467">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-468">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-468">Return Values</span></span>

- <span data-ttu-id="10b69-469">**NX_SUCCESS** (0x00) starten av servern har slutförts.</span><span class="sxs-lookup"><span data-stu-id="10b69-469">**NX_SUCCESS** (0x00) Successful start of server.</span></span>
- <span data-ttu-id="10b69-470">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-470">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-471">**NX_NOT_ENABLED** (0X14) UDP är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="10b69-471">**NX_NOT_ENABLED** (0x14) UDP not enabled.</span></span>
- <span data-ttu-id="10b69-472">**NX_NO_FREE_PORTS** (0X45) inga tillgängliga UDP-portar.</span><span class="sxs-lookup"><span data-stu-id="10b69-472">**NX_NO_FREE_PORTS** (0x45) No available UDP ports.</span></span>
- <span data-ttu-id="10b69-473">**NX_INVALID_PORT** (0X46) ogiltig UDP-port.</span><span class="sxs-lookup"><span data-stu-id="10b69-473">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="10b69-474">**NX_ALREADY_BOUND** (0X22) UDP-porten är redan kopplad.</span><span class="sxs-lookup"><span data-stu-id="10b69-474">**NX_ALREADY_BOUND** (0x22) UDP port already bound.</span></span>
- <span data-ttu-id="10b69-475">**NX_PORT_UNAVAILABLE** (0X23) UDP-porten är inte tillgänglig för användning.</span><span class="sxs-lookup"><span data-stu-id="10b69-475">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-476">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-476">Allowed From</span></span>

<span data-ttu-id="10b69-477">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-478">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-478">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                &send_packet, NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
                (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="10b69-479">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-479">See Also</span></span>

- <span data-ttu-id="10b69-480">nx_secure_dtls_server_stop nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="10b69-480">nx_secure_dtls_server_stop, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="10b69-481">nx_secure_dtls_server_delete nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="10b69-481">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="10b69-482">nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="10b69-482">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="10b69-483">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="10b69-483">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_stop"></a><span data-ttu-id="10b69-484">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="10b69-484">nx_secure_dtls_server_stop</span></span>

<span data-ttu-id="10b69-485">Stoppa en aktiv NetX säker DTLS-serverinstans</span><span class="sxs-lookup"><span data-stu-id="10b69-485">Stop an active NetX Secure DTLS Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-486">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-486">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="10b69-487">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-487">Description</span></span>

<span data-ttu-id="10b69-488">Den här tjänsten stoppar en DTLS-Server från att lyssna på konfigurationen av UDP-porten och återställer alla tillhör ande DTLS-sessioner, vilket stoppar all pågående DTLS kommunikation.</span><span class="sxs-lookup"><span data-stu-id="10b69-488">This service stops a DTLS Server from listening on the configure UDP port and resets all the associated DTLS sessions, halting any in-progress DTLS communications.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-489">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-489">Parameters</span></span>

- <span data-ttu-id="10b69-490">**server_ptr** Pekar mot en aktiv DTLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="10b69-490">**server_ptr** Pointer to an active DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-491">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-491">Return Values</span></span>

- <span data-ttu-id="10b69-492">**NX_SUCCESS** (0x00) har stoppats på servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-492">**NX_SUCCESS** (0x00) Successful stop of server.</span></span>
- <span data-ttu-id="10b69-493">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-493">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-494">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-494">Allowed From</span></span>

<span data-ttu-id="10b69-495">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-495">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-496">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-496">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* We have exited the processing loop, stop the server. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="10b69-497">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-497">See Also</span></span>

- <span data-ttu-id="10b69-498">nx_secure_dtls_server_start nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="10b69-498">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="10b69-499">nx_secure_dtls_server_delete nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="10b69-499">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="10b69-500">nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="10b69-500">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="10b69-501">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="10b69-501">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a><span data-ttu-id="10b69-502">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="10b69-502">nx_secure_dtls_server_trusted_certificate_add</span></span>

<span data-ttu-id="10b69-503">Lägga till ett certifikat för betrodd certifikat utfärdare på en NetX säker DTLS-Server</span><span class="sxs-lookup"><span data-stu-id="10b69-503">Add a trusted CA certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-504">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-504">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="10b69-505">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-505">Description</span></span>

<span data-ttu-id="10b69-506">Den här tjänsten lägger till en betrodd certifikat utfärdare eller ett mellanliggande CA-certifikat till en DTLS-serverinstans och tilldelas till alla interna DTLS-serversessioner.</span><span class="sxs-lookup"><span data-stu-id="10b69-506">This service adds a trusted CA or intermediate CA certificate to a DTLS Server instance and assigned to all the internal DTLS server sessions.</span></span> <span data-ttu-id="10b69-507">Detta krävs endast om X. 509-autentisering med klient certifikat är aktiverat med *nx_secure_dtls_server_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="10b69-507">This is only necessary if X.509 Client certificate authentication is enabled using *nx_secure_dtls_server_x509_client_verify_configure*.</span></span> <span data-ttu-id="10b69-508">Det tillagda certifikatet kommer att användas för att verifiera inkommande klient X. 509-certifikat.</span><span class="sxs-lookup"><span data-stu-id="10b69-508">The added certificate will be used to verify incoming Client X.509 certificates.</span></span>

<span data-ttu-id="10b69-509">Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet.</span><span class="sxs-lookup"><span data-stu-id="10b69-509">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="10b69-510">Detta gör att certifikatet enkelt kan tas bort eller hittas i händelse av att det finns flera identitets certifikat med samma X. 509-namn som finns i DTLS-serverns arkiv.</span><span class="sxs-lookup"><span data-stu-id="10b69-510">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="10b69-511">Mer information om X. 509-servercertifikat finns i användar handboken för NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-511">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-512">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-512">Parameters</span></span>

- <span data-ttu-id="10b69-513">**server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="10b69-513">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="10b69-514">**certifikat** Pekar till en tidigare initierad X. 509-certifikat struktur.</span><span class="sxs-lookup"><span data-stu-id="10b69-514">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="10b69-515">**cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-515">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-516">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-516">Return Values</span></span>

- <span data-ttu-id="10b69-517">**NX_SUCCESS** (0x00) tillägget av certifikat till DTLS-servern har slutförts.</span><span class="sxs-lookup"><span data-stu-id="10b69-517">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="10b69-518">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-518">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-519">**NX_INVALID_PARAMETERS** (0X4D) ett certifikat-ID på 0 skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-519">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-520">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-520">Allowed From</span></span>

<span data-ttu-id="10b69-521">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-521">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-522">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-522">Example</span></span>

<span data-ttu-id="10b69-523">\* Se referens för *nx_secure_dtls_server_create* ett mer komplett exempel.</span><span class="sxs-lookup"><span data-stu-id="10b69-523">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0, NX_NULL,
                                            0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add trusted CA certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a><span data-ttu-id="10b69-524">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-524">See Also</span></span>

- <span data-ttu-id="10b69-525">nx_secure_dtls_server_start nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="10b69-525">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="10b69-526">nx_secure_dtls_session_receive nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="10b69-526">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="10b69-527">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="10b69-527">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="10b69-528">nx_secure_dtls_server_local_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="10b69-528">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="10b69-529">nx_secure_dtls_server_trusted_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="10b69-529">nx_secure_dtls_server_trusted_certificate_remove,</span></span>
- <span data-ttu-id="10b69-530">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="10b69-530">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a><span data-ttu-id="10b69-531">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="10b69-531">nx_secure_dtls_server_trusted_certificate_remove</span></span>

<span data-ttu-id="10b69-532">Ta bort ett certifikat för betrodd certifikat utfärdare från en NetX säker DTLS-Server</span><span class="sxs-lookup"><span data-stu-id="10b69-532">Remove a trusted CA certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-533">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-533">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="10b69-534">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-534">Description</span></span>

<span data-ttu-id="10b69-535">Den här tjänsten tar bort ett certifikat för betrodd certifikat utfärdare från en DTLS-Server instans.</span><span class="sxs-lookup"><span data-stu-id="10b69-535">This service removes a trusted CA certificate from a DTLS Server instance.</span></span> <span data-ttu-id="10b69-536">Certifikat från betrodda certifikat utfärdare krävs bara för en DTLS-server där X. 509-klient certifikat verifiering har Aktiver ATS genom att anropa *nx_secure_dtls_server_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="10b69-536">Trusted CA certificates are only necessary for a DTLS Server for which X.509 Client certificate verification has been enabled by calling *nx_secure_dtls_server_x509_client_verify_configure*.</span></span>

<span data-ttu-id="10b69-537">Det certifikat som ska tas bort kan identifieras antingen av sitt unika X. 509-namn eller av det numeriska cert_id som tilldelades i anropet till *nx_secure_dtls_server_trusted_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="10b69-537">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_trusted_certificate_add*.</span></span> <span data-ttu-id="10b69-538">Cert_id används bara för att identifiera certifikatet och underhålls av programmet.</span><span class="sxs-lookup"><span data-stu-id="10b69-538">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="10b69-539">Om det egna namnet används i stället för det numeriska certifikat-ID: n ska parametern cert_id anges till 0.</span><span class="sxs-lookup"><span data-stu-id="10b69-539">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="10b69-540">Att ta bort ett certifikat medan en DTLS-handskakning bearbetas kan resultera i oväntat beteende.</span><span class="sxs-lookup"><span data-stu-id="10b69-540">Removing a certificate while a DTLS handshake is being processed may result in unexpected behavior.</span></span> <span data-ttu-id="10b69-541">Tjänst *nx_secure_dtls_server_stop* ska anropas innan certifikat tas bort.</span><span class="sxs-lookup"><span data-stu-id="10b69-541">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-542">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-542">Parameters</span></span>

- <span data-ttu-id="10b69-543">**server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="10b69-543">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="10b69-544">**common_name** X. 509-CommonName för det certifikat som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="10b69-544">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="10b69-545">Om det används skickar cert_id som noll.</span><span class="sxs-lookup"><span data-stu-id="10b69-545">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="10b69-546">**common_name_length** Längden på common_name sträng i byte.</span><span class="sxs-lookup"><span data-stu-id="10b69-546">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="10b69-547">**cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-547">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="10b69-548">Om detta används kan du skicka NX_NULL för common_name-parametern.</span><span class="sxs-lookup"><span data-stu-id="10b69-548">If this is used, pass NX_NULL for the common_name parameter.</span></span>


### <a name="return-values"></a><span data-ttu-id="10b69-549">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-549">Return Values</span></span>

- <span data-ttu-id="10b69-550">**NX_SUCCESS** (0x00) borttagning av certifikat från DTLS-servern har slutförts.</span><span class="sxs-lookup"><span data-stu-id="10b69-550">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="10b69-551">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-551">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det gick inte att hitta något certifikat som matchar cert_id eller common_name på den aktuella DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-553">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-553">Allowed From</span></span>

<span data-ttu-id="10b69-554">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-555">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-555">Example</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                                    certificate_der_data,
                                                    sizeof(certificate_der_data),
                                                    NX_NULL, 0, NX_NULL, 0,
                                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                       &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);


/* At some point in the future we decide to remove the certificate we added. We can
       use the certificate identifier we passed into the call to
       nx_secure_dtls_trusted_certificate_add (value = 1); */
    status = nx_secure_dtls_server_trusted_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a><span data-ttu-id="10b69-556">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-556">See Also</span></span>

- <span data-ttu-id="10b69-557">nx_secure_dtls_server_start nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="10b69-557">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="10b69-558">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="10b69-558">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="10b69-559">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="10b69-559">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="10b69-560">nx_secure_dtls_server_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="10b69-560">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="10b69-561">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="10b69-561">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a><span data-ttu-id="10b69-562">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="10b69-562">nx_secure_dtls_server_x509_client_verify_configure</span></span>

<span data-ttu-id="10b69-563">Konfigurera en NetX-säker DTLS-Server för att begära och verifiera klient certifikat</span><span class="sxs-lookup"><span data-stu-id="10b69-563">Configure a NetX Secure DTLS Server to request and verify client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-564">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-564">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a><span data-ttu-id="10b69-565">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-565">Description</span></span>

<span data-ttu-id="10b69-566">Den här tjänsten konfigurerar en DTLS-Server för att begära och verifiera DTLS klient certifikat.</span><span class="sxs-lookup"><span data-stu-id="10b69-566">This service configures a DTLS Server to request and verify DTLS Client certificates.</span></span> <span data-ttu-id="10b69-567">Den här valfria funktionen används när X. 509-certifikat önskas för klientautentisering i stället för andra mekanismer (t. ex. en i förväg delad nyckel).</span><span class="sxs-lookup"><span data-stu-id="10b69-567">This optional feature is used when X.509 certificates are desired for client authentication in place of other mechanisms (e.g. a Pre-Shared Key).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10b69-568">*När en DTLS-Server har kon figurer ATS för att verifiera klient certifikat med hjälp av den här tjänsten måste minst ett certifikat för betrodd certifikat utfärdare läggas till på servern med hjälp av nx_secure_dtls_server_trusted_certificate_add eller servern avvisar alla inkommande klient anslutningar eftersom den inte kan verifiera klient certifikat mot det betrodda arkivet.*</span><span class="sxs-lookup"><span data-stu-id="10b69-568">*When a DTLS Server is configured to verify client certificates using this service, at least one trusted CA certificate must be added to the server using nx_secure_dtls_server_trusted_certificate_add or the server will reject all incoming client connections because it will be unable to verify client certificates against the trusted store.*</span></span>

<span data-ttu-id="10b69-569">Vid anrop av den här tjänsten kommer DTLS Server-instansen (när den har startats) begära klient certifikat som en del av DTLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="10b69-569">Upon calling this service, the DTLS Server instance will (once started) request client certificates as part of the DTLS handshake.</span></span> <span data-ttu-id="10b69-570">Förutsatt att klienten är korrekt konfigurerad med ett identitets certifikat (och tillhör ande certifikat kedja vid behov), kräver DTLS-servern att minnet allokeras för att bearbeta klient certifikat data.</span><span class="sxs-lookup"><span data-stu-id="10b69-570">Assuming the client is properly configured with an identity certificate (and associated certificate chain when applicable), the DTLS Server requires memory to be allocated to process the client certificate data.</span></span> <span data-ttu-id="10b69-571">Det här minnet skickas in som *certs_buffer* parameter.</span><span class="sxs-lookup"><span data-stu-id="10b69-571">This memory is passed in as the *certs_buffer* parameter.</span></span>

<span data-ttu-id="10b69-572">Certs_buffer måste anpassas till den största förväntade certifikat kedjan från en DTLS-klient, *gånger antalet DTLS-serversessioner*.</span><span class="sxs-lookup"><span data-stu-id="10b69-572">The certs_buffer must be sized to accommodate the largest expected certificate chain from a DTLS client, *times the number of DTLS server sessions*.</span></span> <span data-ttu-id="10b69-573">Bufferten delas upp bland de tillgängliga sessionerna med hjälp av parametern *certs_per_session* som representerar det maximala förväntade antalet certifikat i en klient certifikat kedja.</span><span class="sxs-lookup"><span data-stu-id="10b69-573">The buffer is divided amongst the available sessions using the *certs_per_session* parameter which represents the maximum expected number of certificates in a Client certificate chain.</span></span> <span data-ttu-id="10b69-574">Bufferten måste också tillhandahålla utrymme för NX_SECURE_X509_CERT data strukturen som används för att parsa certifikat data.</span><span class="sxs-lookup"><span data-stu-id="10b69-574">The buffer also needs to provide space for the NX_SECURE_X509_CERT data structure which is used to parse the certificate data.</span></span>

<span data-ttu-id="10b69-575">Beräkningen av rätt buffertstorlek kan göras med följande formel:</span><span class="sxs-lookup"><span data-stu-id="10b69-575">Calculating the proper buffer size can be done with the following formula:</span></span>

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- <span data-ttu-id="10b69-576">Antalet DTLS-sessioner bestäms av storleken på den session-buffert som skickades till nx_secure_dtls_server_create.</span><span class="sxs-lookup"><span data-stu-id="10b69-576">The number of DTLS sessions is determined by the size of the session buffer passed into nx_secure_dtls_server_create.</span></span>
- <span data-ttu-id="10b69-577">certs_per_session ska anges till det maximala förväntade antalet certifikat i en klient certifikat kedja.</span><span class="sxs-lookup"><span data-stu-id="10b69-577">certs_per_session should be set to the maximum expected number of certificates in any client certificate chain.</span></span>
- <span data-ttu-id="10b69-578">Den maximala förväntade certifikat storleken är beroende av programmet, nyckel storlekarna och andra faktorer, men 2KB är vanligt vis tillräckligt.</span><span class="sxs-lookup"><span data-stu-id="10b69-578">The maximum expected certificate size is dependent on the application, key sizes, and other factors but 2KB is generally sufficient.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-579">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-579">Parameters</span></span>

- <span data-ttu-id="10b69-580">**server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="10b69-580">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="10b69-581">**certs_per_session** Antal certifikat som ska allokeras till varje DTLS Server-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-581">**certs_per_session** Number of certificates to allocate to each DTLS server session.</span></span>
- <span data-ttu-id="10b69-582">**certs_buffer** Buffertutrymme för inkommande certifikat data.</span><span class="sxs-lookup"><span data-stu-id="10b69-582">**certs_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="10b69-583">**buffer_size** Storlek på certifikatets buffert.</span><span class="sxs-lookup"><span data-stu-id="10b69-583">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-584">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-584">Return Values</span></span>

- <span data-ttu-id="10b69-585">**NX_SUCCESS** (0x00) konfigurationen av klient verifieringen X. 509.</span><span class="sxs-lookup"><span data-stu-id="10b69-585">**NX_SUCCESS** (0x00) Successful configuration of X.509 Client verification.</span></span>
- <span data-ttu-id="10b69-586">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-586">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-587">**NX_INVALID_PARAMETERS** (0X4D) ogiltigt certifikat arkiv (DTLSserver-instans inte initalized?).</span><span class="sxs-lookup"><span data-stu-id="10b69-587">**NX_INVALID_PARAMETERS** (0x4D) Invalid certificate store (DTLSserver instance not initalized?).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-588">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-588">Allowed From</span></span>

<span data-ttu-id="10b69-589">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-589">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-590">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-590">Example</span></span>

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                                    sizeof(certificate_der_data),
                                    NX_NULL, 0,
                                    NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */
}

```

### <a name="see-also"></a><span data-ttu-id="10b69-591">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-591">See Also</span></span>

- <span data-ttu-id="10b69-592">nx_secure_dtls_server_x509_client_verify_disable,</span><span class="sxs-lookup"><span data-stu-id="10b69-592">nx_secure_dtls_server_x509_client_verify_disable,</span></span>
- <span data-ttu-id="10b69-593">nx_secure_dtls_server_start nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="10b69-593">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="10b69-594">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="10b69-594">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="10b69-595">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="10b69-595">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="10b69-596">nx_secure_dtls_server_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="10b69-596">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="10b69-597">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="10b69-597">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a><span data-ttu-id="10b69-598">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="10b69-598">nx_secure_dtls_server_x509_client_verify_disable</span></span>

<span data-ttu-id="10b69-599">Inaktiverar verifiering av klient-X. 509 för en NetX säker DTLS-Server</span><span class="sxs-lookup"><span data-stu-id="10b69-599">Disables client X.509 certificate verification for a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-600">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-600">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="10b69-601">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-601">Description</span></span>

<span data-ttu-id="10b69-602">Den här tjänsten inaktiverar X. 509 klient certifikat verifiering på en DTLS-Server.</span><span class="sxs-lookup"><span data-stu-id="10b69-602">This service disables X.509 Client certificate verification on a DTLS Server.</span></span> <span data-ttu-id="10b69-603">Tjänsten har ingen funktion om verifieringen av klient certifikatet för X. 509 inte är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="10b69-603">The service has no effect if X.509 Client certificate verification is not enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="10b69-604">Inaktive ring av klientautentisering på en aktiv DTLS-serverinstans kan leda till oförutsägbara beteenden.</span><span class="sxs-lookup"><span data-stu-id="10b69-604">Disabling client authentication on an active DTLS Server instance may result in unpredictable behavior.</span></span> <span data-ttu-id="10b69-605">Tjänsten nx_secure_dtls_server_stop ska anropas innan Server tillstånd ändras.</span><span class="sxs-lookup"><span data-stu-id="10b69-605">The nx_secure_dtls_server_stop service should be called before changing server state.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-606">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-606">Parameters</span></span>

- <span data-ttu-id="10b69-607">**server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="10b69-607">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-608">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-608">Return Values</span></span>

- <span data-ttu-id="10b69-609">**NX_SUCCESS** (0x00) har inaktiverat autentisering av X. 509-klient.</span><span class="sxs-lookup"><span data-stu-id="10b69-609">**NX_SUCCESS** (0x00) Successful disabling of X.509 client authentication.</span></span>
- <span data-ttu-id="10b69-610">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-610">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-611">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-611">Allowed From</span></span>

<span data-ttu-id="10b69-612">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-613">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-613">Example</span></span>

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                        sizeof(certificate_der_data), NX_NULL, 0,
                        NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before changing state. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* Disable X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_disable(&dtls_server);

}

```

### <a name="see-also"></a><span data-ttu-id="10b69-614">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-614">See Also</span></span>

- <span data-ttu-id="10b69-615">nx_secure_dtls_server_x509_client_verify_configure,</span><span class="sxs-lookup"><span data-stu-id="10b69-615">nx_secure_dtls_server_x509_client_verify_configure,</span></span>
- <span data-ttu-id="10b69-616">nx_secure_dtls_server_start nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="10b69-616">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="10b69-617">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="10b69-617">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="10b69-618">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="10b69-618">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="10b69-619">nx_secure_dtls_server_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="10b69-619">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="10b69-620">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="10b69-620">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_client_info_get"></a><span data-ttu-id="10b69-621">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="10b69-621">nx_secure_dtls_session_client_info_get</span></span>

<span data-ttu-id="10b69-622">Hämta information om fjärran sluten klient från en DTLS-Server</span><span class="sxs-lookup"><span data-stu-id="10b69-622">Get remote client information from a DTLS Server session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-623">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-623">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a><span data-ttu-id="10b69-624">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-624">Description</span></span>

<span data-ttu-id="10b69-625">Den här tjänsten returnerar nätverksinformation om en DTLS-klient som är ansluten till en viss DTLS Server-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-625">This service returns the network information about a DTLS Client that is connected to a particular DTLS Server session.</span></span> <span data-ttu-id="10b69-626">Den information som returneras består av fjärrklientens IP-adress och UDP-port, samt den lokala server port som klienten är ansluten till.</span><span class="sxs-lookup"><span data-stu-id="10b69-626">The information returned consists of the remote client’s IP address and UDP port, as well as the local server port to which the client is connected.</span></span>

<span data-ttu-id="10b69-627">I allmänhet är DTLS session-instansen som erhålls i anropet från en av DTLS för aviseringar om aviseringar (t. ex. connect_notify eller receive_notify återanrop som skickas till nx_secure_dtls_server_create).</span><span class="sxs-lookup"><span data-stu-id="10b69-627">In general, the DTLS session instance will be the one obtained in the invocation of one of the DTLS notification callback routines (e.g. the connect_notify or receive_notify callbacks passed into nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-628">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-628">Parameters</span></span>

- <span data-ttu-id="10b69-629">**session_ptr** Pekar mot en aktiv DTLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-629">**session_ptr** Pointer to an active DTLS server session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-630">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-630">Return Values</span></span>

- <span data-ttu-id="10b69-631">**NX_SUCCESS** (0x00) borttagning av server lyckades.</span><span class="sxs-lookup"><span data-stu-id="10b69-631">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="10b69-632">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-632">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-633">**NX_INVALID_SOCKET** (0X13) den associerade UDP-socketen är inte giltig (sessionen initierades inte?).</span><span class="sxs-lookup"><span data-stu-id="10b69-633">**NX_INVALID_SOCKET** (0x13) The associated UDP socket is not valid (session not initialized?).</span></span>
- <span data-ttu-id="10b69-634">**NX_NOT_CONNECTED** (0X38) UDP-socketen är inte ansluten – klient anslutningen har släppts eller ännu inte upprättats.</span><span class="sxs-lookup"><span data-stu-id="10b69-634">**NX_NOT_CONNECTED** (0x38) UDP socket is not connected – client connection dropped or not yet established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-635">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-635">Allowed From</span></span>

<span data-ttu-id="10b69-636">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-637">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-637">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array
   or list in case a new connection is
   attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
                                                            *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    NXD_ADDRESS client_ip;
    UINT client_port, server_port;

    /* Get DTLS client information which can be used in filtering or associating
       the DTLS session with application data (e.g. a session pointer table). */
    status = nx_secure_dtls_session_client_info_get(dtls_session, &client_ip,
   &client_port, &server_port);

    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="10b69-638">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-638">See Also</span></span>

- <span data-ttu-id="10b69-639">nx_secure_dtls_server_start nx_secure_dtls_server_stop,</span><span class="sxs-lookup"><span data-stu-id="10b69-639">nx_secure_dtls_server_start, nx_secure_dtls_server_stop,</span></span>
- <span data-ttu-id="10b69-640">nx_secure_dtls_server_create nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="10b69-640">nx_secure_dtls_server_create, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="10b69-641">nx_secure_dtls_session_receive nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="10b69-641">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="10b69-642">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="10b69-642">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_session_create"></a><span data-ttu-id="10b69-643">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="10b69-643">nx_secure_dtls_session_create</span></span>

<span data-ttu-id="10b69-644">Skapa och konfigurera en NetX Secure DTLS-session</span><span class="sxs-lookup"><span data-stu-id="10b69-644">Create and configure a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-645">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-645">Prototype</span></span>

```C
UINT nx_secure_dtls_session_create(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        VOID *metadata_buffer, ULONG metadata_size,
                        UCHAR *packet_reassembly_buffer,
                        UINT packet_reassembly_buffer_size,
                        UINT certs_number,
                        UCHAR *remote_certificate_buffer,
                        ULONG remote_certificate_buffer_size));

```

### <a name="description"></a><span data-ttu-id="10b69-646">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-646">Description</span></span>

<span data-ttu-id="10b69-647">Den här tjänsten skapar och konfigurerar en DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-647">This service creates and configures a DTLS session.</span></span> <span data-ttu-id="10b69-648">Detta används vanligt vis för att skapa DTLS-klientsessioner som DTLS-serversessioner hanteras med DTLS-serverns mekanism (se *nx_secure_dtls_server_create*), men det kan finnas instanser där ett program behöver skapa en enda fristående DTLS för Server session, vilket innebär att tjänsten kan användas <sup>7</sup>.</span><span class="sxs-lookup"><span data-stu-id="10b69-648">Generally, this will be used to create DTLS Client sessions as DTLS Server sessions are managed with the DTLS Server mechanism (see *nx_secure_dtls_server_create*), but there may be instances where an application needs to create a single stand-alone DTLS Server session instance in which case this service may be used<sup>7</sup>.</span></span>

<span data-ttu-id="10b69-649">Parametrarna konfigurerar den information och minnes tilldelning som krävs för att instansiera en DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-649">The parameters configure the information and memory allocation needed to instantiate a DTLS session.</span></span> <span data-ttu-id="10b69-650">Parametern crypto_table är en TLS-tabell som innehåller alla de kryptografiska rutiner som krävs för TLS/DTLS-kryptering och autentisering.</span><span class="sxs-lookup"><span data-stu-id="10b69-650">The crypto_table parameter is a TLS table containing all of the cryptographic routines needed for TLS/DTLS encryption and authentication.</span></span> <span data-ttu-id="10b69-651">Metadata_buffer används för kryptering caclulations (se nx_secure_tls_metadata_size_calculate i användar handboken för NetX Secure TLS) och packet_reassembly_buffer används för att sätta samman UDP-datagram till en fullständig DTLS-post för dekryptering.</span><span class="sxs-lookup"><span data-stu-id="10b69-651">The metadata_buffer is used for encryption caclulations (see nx_secure_tls_metadata_size_calculate in the NetX Secure TLS User Guide), and the packet_reassembly_buffer is used to reassemble UDP datagrams into a complete DTLS record for decryption.</span></span>

<span data-ttu-id="10b69-652">Certs_number och remote_certificate_buffer krävs för DTLS-klienter som behöver utrymme för att lagra och bearbeta den inkommande DTLS Server certifikat kedjan.</span><span class="sxs-lookup"><span data-stu-id="10b69-652">The certs_number and remote_certificate_buffer are required for DTLS Clients which need space to store and process the incoming DTLS Server certificate chain.</span></span> <span data-ttu-id="10b69-653">Bufferten måste kunna hantera den maximala förväntade storleken på certifikat kedjan för en server som den ska ansluta till.</span><span class="sxs-lookup"><span data-stu-id="10b69-653">The buffer must be able to accommodate the maximum expected size of the certificate chain for any server to which it will connect.</span></span> <span data-ttu-id="10b69-654">Bufferten delas upp av antalet förväntade certifikat (certs_number parameter) och måste också vara tillräckligt stor för att rymma en NX_SECURE_X509_CERT struktur per certifikat.</span><span class="sxs-lookup"><span data-stu-id="10b69-654">The buffer is divided up by the number of expected certificates (certs_number parameter) and must also be large enough to hold one NX_SECURE_X509_CERT structure per certificate.</span></span> <span data-ttu-id="10b69-655">Buffertstorleken kan fastställas med hjälp av följande formel:</span><span class="sxs-lookup"><span data-stu-id="10b69-655">The buffer size can be determined using the following formula:</span></span>

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- <span data-ttu-id="10b69-656">certs_number är det förväntade maximala antalet certifikat i serverns certifikat kedja</span><span class="sxs-lookup"><span data-stu-id="10b69-656">certs_number is the expected maximum number of certificates in the server’s certificate chain</span></span>
- <span data-ttu-id="10b69-657">Maximal certifikat storlek beror på storleken på de nycklar som används och informationen i certifikatet, men 2KB är allmänt tillräckligt.</span><span class="sxs-lookup"><span data-stu-id="10b69-657">Maximum certificate size is dependent on the size of keys being used and the information in the certificate, but 2KB is generally sufficient.</span></span>

<span data-ttu-id="10b69-658">**7** det är inte rekommenderat att skapa DTLS-serversessioner med den här rutinen och den innehåller vissa begränsningar.</span><span class="sxs-lookup"><span data-stu-id="10b69-658">**7** Creating DTLS Server sessions with this routine is not recommended and comes with some limitations.</span></span> <span data-ttu-id="10b69-659">Det primära problemet är att sessionen inte hanterar ytterligare klient anslutningar på ett smidigt sätt eftersom UDP är anslutnings lös en andra klient kan lagligen skicka data till serverns UDP-port när en tidigare DTLS-session fortfarande är aktiv, vilket skulle orsaka att serversessionen avslutas med ett fel.</span><span class="sxs-lookup"><span data-stu-id="10b69-659">The primary issue is that the session will not handle additional client connections gracefully – since UDP is connectionless a second client can legally send data to the server’s UDP port when a previous DTLS session is still active which would cause the server session to end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-660">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-660">Parameters</span></span>

- <span data-ttu-id="10b69-661">**dtls_session** Pekar till en oinitierad DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-661">**dtls_session** Pointer to an uninitialized DTLS Session structure.</span></span>
- <span data-ttu-id="10b69-662">**crypto_table** Pekare till en TLS/DTLS krypterings tabell struktur som används för alla kryptografiska åtgärder.</span><span class="sxs-lookup"><span data-stu-id="10b69-662">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="10b69-663">**crypto_metadata_buffer** Buffertutrymme för kryptografiska åtgärds beräkningar och statusinformation.</span><span class="sxs-lookup"><span data-stu-id="10b69-663">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="10b69-664">**crypto_metadata_size** Storlek på buffert för metadata.</span><span class="sxs-lookup"><span data-stu-id="10b69-664">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="10b69-665">**packet_reassembly_buffer** Buffert som används av DTLS för att ommontera UDP-data i DTLS-poster för dekryptering.</span><span class="sxs-lookup"><span data-stu-id="10b69-665">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="10b69-666">**packet_reassembly_buffer_size** Storlek på omassembly buffer.</span><span class="sxs-lookup"><span data-stu-id="10b69-666">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="10b69-667">Bör normalt vara större än 16 KB, men kan vara mindre beroende på program.</span><span class="sxs-lookup"><span data-stu-id="10b69-667">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="10b69-668">**certs_number** Maximalt Förväntat antal certifikat i fjärrserverns certifikat kedja.</span><span class="sxs-lookup"><span data-stu-id="10b69-668">**certs_number** Maximum expected number of certificates in the remote server’s certificate chain.</span></span>
- <span data-ttu-id="10b69-669">**remote_certificate_buffer** Buffertutrymme för inkommande certifikat data.</span><span class="sxs-lookup"><span data-stu-id="10b69-669">**remote_certificate_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="10b69-670">**remote_certificate_buffer_size** Storlek på certifikatets buffert.</span><span class="sxs-lookup"><span data-stu-id="10b69-670">**remote_certificate_buffer_size** Size of the certificate buffer.</span></span>


### <a name="return-values"></a><span data-ttu-id="10b69-671">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-671">Return Values</span></span>

- <span data-ttu-id="10b69-672">**NX_SUCCESS** (0x00) skapandet av session.</span><span class="sxs-lookup"><span data-stu-id="10b69-672">**NX_SUCCESS** (0x00) Successful creation of session.</span></span>
- <span data-ttu-id="10b69-673">**NX_PTR_ERROR** (0X07) ogiltig sessions-eller buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="10b69-673">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="10b69-674">**NX_INVALID_PARAMETERS** (0X4D) det finns inte tillräckligt med buffertutrymme för paket omsammansättning, certifikat eller kryptografi.</span><span class="sxs-lookup"><span data-stu-id="10b69-674">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for packet reassembly, certificates, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-675">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-675">Allowed From</span></span>

<span data-ttu-id="10b69-676">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-677">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-677">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
    &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                            &udp_socket, &server_ip,
                                            4443,
                                            NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session,
                                            &receive_packet,
                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="10b69-678">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-678">See Also</span></span>

- <span data-ttu-id="10b69-679">nx_secure_dtls_client_session_start nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="10b69-679">nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="10b69-680">nx_secure_dtls_session_send</span><span class="sxs-lookup"><span data-stu-id="10b69-680">nx_secure_dtls_session_send</span></span>

## <a name="nx_secure_dtls_session_delete"></a><span data-ttu-id="10b69-681">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="10b69-681">nx_secure_dtls_session_delete</span></span>

<span data-ttu-id="10b69-682">Frigör resurser som används av en NetX Secure DTLS-session</span><span class="sxs-lookup"><span data-stu-id="10b69-682">Free up resources used by a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-683">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-683">Prototype</span></span>

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a><span data-ttu-id="10b69-684">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-684">Description</span></span>

<span data-ttu-id="10b69-685">Den här tjänsten tar bort en DTLS-session, vilket frigör alla resurser som har allokerats när den skapades.</span><span class="sxs-lookup"><span data-stu-id="10b69-685">This service deletes a DTLS session, freeing up any resources that were allocated when it was created.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-686">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-686">Parameters</span></span>

- <span data-ttu-id="10b69-687">**dtls_session** Pekare till en DTLS som initierades tidigare.</span><span class="sxs-lookup"><span data-stu-id="10b69-687">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-688">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-688">Return Values</span></span>

- <span data-ttu-id="10b69-689">**NX_SUCCESS** (0x00) en borttagning av sessionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="10b69-689">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="10b69-690">**NX_PTR_ERROR** (0X07) ogiltig sessions-eller buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="10b69-690">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-691">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-691">Allowed From</span></span>

<span data-ttu-id="10b69-692">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-693">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-693">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                        trusted_cert_der,
                                        trusted_cert_der_len,
                                        NX_NULL, 0, NX_NULL, 0,
                                        NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                    &udp_socket,
                                                    &server_ip, 4443,
                                                    NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                &receive_packet,
                                                NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="10b69-694">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-694">See Also</span></span>

- <span data-ttu-id="10b69-695">nx_secure_dtls_client_session_start nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="10b69-695">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="10b69-696">nx_secure_dtls_session_send nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="10b69-696">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_end"></a><span data-ttu-id="10b69-697">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="10b69-697">nx_secure_dtls_session_end</span></span>

<span data-ttu-id="10b69-698">Stänga en aktiv NetX säker DTLS-session</span><span class="sxs-lookup"><span data-stu-id="10b69-698">Shut down an active NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-699">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-699">Prototype</span></span>

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="10b69-700">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-700">Description</span></span>

<span data-ttu-id="10b69-701">Den här tjänsten avslutar en aktiv DTLS-session genom att skicka en TLS/DTLS CloseNotify-avisering till fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="10b69-701">This service ends an active DTLS session by sending a TLS/DTLS CloseNotify alert to the remote host.</span></span> <span data-ttu-id="10b69-702">Den IP-adress och port som används är de som användes i föregående anrop till nx_secure_dtls_session_send.</span><span class="sxs-lookup"><span data-stu-id="10b69-702">The IP address and port used are those used in the previous call to nx_secure_dtls_session_send.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-703">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-703">Parameters</span></span>

- <span data-ttu-id="10b69-704">**dtls_session** Pekare till en DTLS som initierades tidigare.</span><span class="sxs-lookup"><span data-stu-id="10b69-704">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="10b69-705">**wait_option** ThreadX vänte värde som ska användas för nätverks åtgärder.</span><span class="sxs-lookup"><span data-stu-id="10b69-705">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-706">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-706">Return Values</span></span>

- <span data-ttu-id="10b69-707">**NX_SUCCESS** (0x00) en borttagning av sessionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="10b69-707">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="10b69-708">**NX_PTR_ERROR** (0X07) ogiltig sessions-eller buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="10b69-708">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="10b69-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0X111) Det gick inte att allokera paket för CloseNotify-avisering.</span><span class="sxs-lookup"><span data-stu-id="10b69-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate packet(s) for CloseNotify alert.</span></span>
- <span data-ttu-id="10b69-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0X105) troligen internt fel – kryptografisk rutin känns inte igen.</span><span class="sxs-lookup"><span data-stu-id="10b69-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Likely internal error – cryptographic routine not recognized.</span></span>
- <span data-ttu-id="10b69-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) den underliggande UDP-sändningen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="10b69-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Underlying UDP send failed.</span></span>
- <span data-ttu-id="10b69-712">**NX_IP_ADDRESS_ERROR** -fel (0x21) med en fjärran sluten värd-IP-adress.</span><span class="sxs-lookup"><span data-stu-id="10b69-712">**NX_IP_ADDRESS_ERROR** (0x21) Error with remote host IP address.</span></span>
- <span data-ttu-id="10b69-713">**NX_NOT_BOUND** (0x24) den underliggande UDP-socketen är inte kopplad till porten.</span><span class="sxs-lookup"><span data-stu-id="10b69-713">**NX_NOT_BOUND** (0x24) Underlying UDP socket not bound to port.</span></span>
- <span data-ttu-id="10b69-714">**NX_INVALID_PORT** (0X46) ogiltig UDP-port.</span><span class="sxs-lookup"><span data-stu-id="10b69-714">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="10b69-715">**NX_PORT_UNAVAILABLE** (0X23) UDP-porten är inte tillgänglig för användning.</span><span class="sxs-lookup"><span data-stu-id="10b69-715">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-716">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-716">Allowed From</span></span>

<span data-ttu-id="10b69-717">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-717">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-718">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-718">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session,
                                        NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

    }

```

### <a name="see-also"></a><span data-ttu-id="10b69-719">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-719">See Also</span></span>

- <span data-ttu-id="10b69-720">nx_secure_dtls_client_session_start nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="10b69-720">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="10b69-721">nx_secure_dtls_session_send nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="10b69-721">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_local_certificate_add"></a><span data-ttu-id="10b69-722">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="10b69-722">nx_secure_dtls_session_local_certificate_add</span></span>

<span data-ttu-id="10b69-723">Lägga till ett lokalt identitets certifikat till en NetX Secure DTLS-session</span><span class="sxs-lookup"><span data-stu-id="10b69-723">Add a local identity certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-724">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-724">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="10b69-725">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-725">Description</span></span>

<span data-ttu-id="10b69-726">Den här tjänsten lägger till ett lokalt identitets certifikat till en DTLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-726">This service adds a local identity certificate to a DTLS Session instance.</span></span> <span data-ttu-id="10b69-727">I allmänhet används den här tjänsten när en DTLS-klientsession måste tillhandahålla ett identitets certifikat till en fjärrserver-värd.</span><span class="sxs-lookup"><span data-stu-id="10b69-727">In general, this service will be used when a DTLS Client session needs to provide an identity certificate to a remote server host.</span></span> <span data-ttu-id="10b69-728">Detta är en valfri konfiguration för DTLS, så ett certifikat är inte allmänt nödvändigt för DTLS-klienter.</span><span class="sxs-lookup"><span data-stu-id="10b69-728">This is an optional configuration for DTLS so a certificate is not generally required for DTLS Clients.</span></span> <span data-ttu-id="10b69-729">Ett identitets certifikat kräver en associerad privat nyckel.</span><span class="sxs-lookup"><span data-stu-id="10b69-729">An identity certificate requires an associated private key.</span></span>

<span data-ttu-id="10b69-730">Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet.</span><span class="sxs-lookup"><span data-stu-id="10b69-730">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="10b69-731">Detta gör att certifikatet enkelt kan tas bort eller hittas i händelse av att det finns flera identitets certifikat med samma X. 509-namn som finns i certifikat arkivet DTLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-731">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="10b69-732">Mer information om X. 509-certifikat finns i användar handboken för NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-732">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-733">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-733">Parameters</span></span>

- <span data-ttu-id="10b69-734">**session_ptr** Pekar till en tidigare skapad DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-734">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="10b69-735">**certifikat** Pekar till en tidigare initierad X. 509-certifikat struktur.</span><span class="sxs-lookup"><span data-stu-id="10b69-735">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="10b69-736">**cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-736">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-737">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-737">Return Values</span></span>

- <span data-ttu-id="10b69-738">**NX_SUCCESS** (0x00) det framgångs rika tillägget av certifikat till DTLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="10b69-738">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="10b69-739">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-739">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-740">**NX_INVALID_PARAMETERS** (0X4D) ett certifikat-ID på 0 skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-740">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-741">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-741">Allowed From</span></span>

<span data-ttu-id="10b69-742">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-742">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-743">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-743">Example</span></span>

<span data-ttu-id="10b69-744">\* Se referens för *nx_secure_dtls_session_create* ett mer komplett exempel.</span><span class="sxs-lookup"><span data-stu-id="10b69-744">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity
certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

/* Create a TLS session for our socket. Ciphers and metadata defined
   elsewhere. See nx_secure_tls_session_create reference for more
   information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
{
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
}

/* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

/* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                              &certificate, 1);

    /* Initialize local server identity certificate with key and
    add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                        certificate_der_data,
                        sizeof(certificate_der_data),
                        NX_NULL, 0,
                        certificate_key_der_data,
                        sizeof(certificate_key_der_data),
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                    &certificate, 1);

/* Set up IP address of remote host. */
server_ip.nxd_ip_version = NX_IP_VERSION_V4;
server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


/* Now we can start the DTLS session as normal. */
status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                    &udp_socket, &server_ip, 4443,
                                    NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a><span data-ttu-id="10b69-745">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-745">See Also</span></span>

- <span data-ttu-id="10b69-746">nx_secure_dtls_session_create nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="10b69-746">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="10b69-747">nx_secure_dtls_session_send nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="10b69-747">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="10b69-748">nx_secure_dtls_session_local_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="10b69-748">nx_secure_dtls_session_local_certificate_remove,</span></span>
- <span data-ttu-id="10b69-749">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="10b69-749">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_local_certificate_remove"></a><span data-ttu-id="10b69-750">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="10b69-750">nx_secure_dtls_session_local_certificate_remove</span></span>

<span data-ttu-id="10b69-751">Ta bort ett lokalt identitets certifikat från en NetX Secure DTLS-session</span><span class="sxs-lookup"><span data-stu-id="10b69-751">Remove a local identity certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-752">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-752">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="10b69-753">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-753">Description</span></span>

<span data-ttu-id="10b69-754">Den här tjänsten tar bort ett lokalt identitets certifikat från en DTLS med antingen ett certifikat-ID-nummer (tilldelat när certifikatet lades till med nx_secure_dtls_session_local_certificate_add) eller fältet X. 509 CommonName.</span><span class="sxs-lookup"><span data-stu-id="10b69-754">This service removes a local identity certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_local_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="10b69-755">Om common_name används för att matcha certifikatet, ska cert_id-parametern anges till 0.</span><span class="sxs-lookup"><span data-stu-id="10b69-755">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="10b69-756">Om cert_id används ska common_name skickas värdet NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="10b69-756">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="10b69-757">Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet.</span><span class="sxs-lookup"><span data-stu-id="10b69-757">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="10b69-758">Detta gör att certifikatet enkelt kan tas bort eller hittas i händelse av att det finns flera identitets certifikat med samma X. 509-namn som finns i certifikat arkivet DTLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-758">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="10b69-759">Mer information om X. 509-certifikat finns i användar handboken för NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-759">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-760">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-760">Parameters</span></span>

- <span data-ttu-id="10b69-761">**session_ptr** Pekar till en tidigare skapad DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-761">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="10b69-762">**common_name** Pekar på den CommonName-sträng som ska matchas.</span><span class="sxs-lookup"><span data-stu-id="10b69-762">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="10b69-763">**common_name_length** Längden på common_name strängen.</span><span class="sxs-lookup"><span data-stu-id="10b69-763">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="10b69-764">**cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-764">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-765">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-765">Return Values</span></span>

- <span data-ttu-id="10b69-766">**NX_SUCCESS** (0x00) borttagning av certifikat från DTLS-sessionen lyckades.</span><span class="sxs-lookup"><span data-stu-id="10b69-766">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="10b69-767">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-767">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det gick inte att hitta något certifikat som matchar cert_id eller common_name i den aktuella DTLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="10b69-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-769">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-769">Allowed From</span></span>

<span data-ttu-id="10b69-770">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-770">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-771">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-771">Example</span></span>

<span data-ttu-id="10b69-772">\* Se referens för *nx_secure_dtls_session_create* ett mer komplett exempel.</span><span class="sxs-lookup"><span data-stu-id="10b69-772">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

        /* Initialize local server identity certificate with key
        and add to server. */
        status = nx_secure_x509_certificate_initialize(&certificate,
                                certificate_der_data,
                                sizeof(certificate_der_data),
                                NX_NULL, 0,
                                certificate_key_der_data,
                                sizeof(certificate_key_der_data),
                                NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

        /* Add local server identity certificate to DTLS server with ID of 1. */
        status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                            &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
        &udp_socket, &server_ip, 4443,
        NX_IP_PERIODIC_RATE);

        /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
        status = nx_secure_dtls_session_local_certificate_remove(&client_dtls_session,
                                                                NX_NULL, 0, 1);
}

```

### <a name="see-also"></a><span data-ttu-id="10b69-773">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-773">See Also</span></span>

- <span data-ttu-id="10b69-774">nx_secure_dtls_session_create nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="10b69-774">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="10b69-775">nx_secure_dtls_session_send nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="10b69-775">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="10b69-776">nx_secure_dtls_session_local_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="10b69-776">nx_secure_dtls_session_local_certificate_add,</span></span>
- <span data-ttu-id="10b69-777">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="10b69-777">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_receive"></a><span data-ttu-id="10b69-778">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="10b69-778">nx_secure_dtls_session_receive</span></span>

<span data-ttu-id="10b69-779">Ta emot program data över en etablerad NetX Secure DTLS-session</span><span class="sxs-lookup"><span data-stu-id="10b69-779">Receive application data over an established NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-780">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-780">Prototype</span></span>

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="10b69-781">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-781">Description</span></span>

<span data-ttu-id="10b69-782">Den här tjänsten returnerar program data som tagits emot av en aktiv DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-782">This service returns application data received by an active DTLS Session.</span></span> <span data-ttu-id="10b69-783">DTLS-sessionen kan vara antingen en DTLS-klientsession (hanteras av en DTLS-serverinstans) eller en DTLS-klientsession.</span><span class="sxs-lookup"><span data-stu-id="10b69-783">The DTLS Session may be either a DTLS Server session (managed by a DTLS Server instance) or a DTLS Client session.</span></span> <span data-ttu-id="10b69-784">Det returnerade paketet kan bearbetas med hjälp av någon av NX_PACKET API-tjänsterna (se NetX-dokumentationen för mer information).</span><span class="sxs-lookup"><span data-stu-id="10b69-784">The returned packet may be processed using any of the NX_PACKET API services (see the NetX documentation for more information).</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-785">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-785">Parameters</span></span>

- <span data-ttu-id="10b69-786">**dtls_session** Pekare till en DTLS som initierades tidigare.</span><span class="sxs-lookup"><span data-stu-id="10b69-786">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="10b69-787">**packet_ptr_ptr** Pekar till en NX_PACKET-pekare för det returnerade paketet.</span><span class="sxs-lookup"><span data-stu-id="10b69-787">**packet_ptr_ptr** Pointer to an NX_PACKET pointer for the return packet.</span></span>
- <span data-ttu-id="10b69-788">**wait_option** ThreadX vänte värde som ska användas för nätverks åtgärder.</span><span class="sxs-lookup"><span data-stu-id="10b69-788">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-789">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-789">Return Values</span></span>

- <span data-ttu-id="10b69-790">**NX_SUCCESS** (0x00) mottagning av program data paket.</span><span class="sxs-lookup"><span data-stu-id="10b69-790">**NX_SUCCESS** (0x00) Successful receipt of application data packet.</span></span>
- <span data-ttu-id="10b69-791">**NX_PTR_ERROR** (0X07) ogiltig session eller paket pekare.</span><span class="sxs-lookup"><span data-stu-id="10b69-791">**NX_PTR_ERROR** (0x07) Invalid session or packet pointer.</span></span>
- <span data-ttu-id="10b69-792">**NX_NOT_ENABLED** (0X14) UDP är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="10b69-792">**NX_NOT_ENABLED** (0x14) UDP is not enabled.</span></span>
- <span data-ttu-id="10b69-793">**NX_NOT_BOUND** (0X24) UDP-socketen är inte kopplad till porten.</span><span class="sxs-lookup"><span data-stu-id="10b69-793">**NX_NOT_BOUND** (0x24) UDP socket not bound to port.</span></span>
- <span data-ttu-id="10b69-794">**NX_SECURE_TLS_INVALID_PACKET** (0X104) emot data som inte var giltiga DTLS-poster.</span><span class="sxs-lookup"><span data-stu-id="10b69-794">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="10b69-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) en DTLS-post kunde inte hashas korrekt (krypterings fel).</span><span class="sxs-lookup"><span data-stu-id="10b69-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="10b69-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) kontroll av krypterings utfyllnad har misslyckats.</span><span class="sxs-lookup"><span data-stu-id="10b69-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="10b69-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) emot en avisering från fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="10b69-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host.</span></span>
- <span data-ttu-id="10b69-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0X102) tog emot ett okänt meddelande.</span><span class="sxs-lookup"><span data-stu-id="10b69-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0x102) Received an unrecognized message.</span></span>
- <span data-ttu-id="10b69-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) emot en DTLS-post med ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="10b69-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="10b69-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0X105) en okänd CIPHERSUITE påträffades (tyder på ett internt kryptografi fel).</span><span class="sxs-lookup"><span data-stu-id="10b69-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicates internal cryptography error).</span></span>
- <span data-ttu-id="10b69-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E) emot en DTLS post med en felmatchad DTLS-version.</span><span class="sxs-lookup"><span data-stu-id="10b69-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-802">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-802">Allowed From</span></span>

<span data-ttu-id="10b69-803">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-804">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-804">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="10b69-805">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-805">See Also</span></span>

- <span data-ttu-id="10b69-806">nx_secure_dtls_client_session_start nx_secure_dtls_session_end,</span><span class="sxs-lookup"><span data-stu-id="10b69-806">nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,</span></span>
- <span data-ttu-id="10b69-807">nx_secure_dtls_session_send nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="10b69-807">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_reset"></a><span data-ttu-id="10b69-808">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="10b69-808">nx_secure_dtls_session_reset</span></span>

<span data-ttu-id="10b69-809">Rensa data i en NetX Secure DTLS-session-instans</span><span class="sxs-lookup"><span data-stu-id="10b69-809">Clear data in an NetX Secure DTLS Session instance</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-810">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-810">Prototype</span></span>

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a><span data-ttu-id="10b69-811">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-811">Description</span></span>

<span data-ttu-id="10b69-812">Den här tjänsten återställer en DTLS-session och rensar alla tillfälliga kryptografiska data och gör det möjligt att använda strukturen igen för en ny session.</span><span class="sxs-lookup"><span data-stu-id="10b69-812">This service resets a DTLS session, clearing all ephemeral cryptographic data and allowing the structure to be re-used for a new session.</span></span> <span data-ttu-id="10b69-813">Beständiga data (t. ex. certifikat Arkiv) bevaras så att nx_secure_dtls_session_create inte behöver anropas flera gånger.</span><span class="sxs-lookup"><span data-stu-id="10b69-813">Persistent data (e.g. certificate stores) are maintained so that nx_secure_dtls_session_create need not be called repeatedly.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-814">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-814">Parameters</span></span>

- <span data-ttu-id="10b69-815">**dtls_session** Pekare till en DTLS som initierades tidigare.</span><span class="sxs-lookup"><span data-stu-id="10b69-815">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-816">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-816">Return Values</span></span>

- <span data-ttu-id="10b69-817">**NX_SUCCESS** (0X00) lyckades att återställa sessionen.</span><span class="sxs-lookup"><span data-stu-id="10b69-817">**NX_SUCCESS** (0x00) Successful reset of session.</span></span>
- <span data-ttu-id="10b69-818">**NX_PTR_ERROR** (0X07) ogiltig sessions-eller buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="10b69-818">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-819">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-819">Allowed From</span></span>

<span data-ttu-id="10b69-820">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-820">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-821">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-821">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_reset(&client_dtls_session);

    /* A new session can now be started using the same structure. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,



    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="10b69-822">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-822">See Also</span></span>

- <span data-ttu-id="10b69-823">nx_secure_dtls_client_session_start nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="10b69-823">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="10b69-824">nx_secure_dtls_session_send nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="10b69-824">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_-session_send"></a><span data-ttu-id="10b69-825">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="10b69-825">nx_secure_dtls_ session_send</span></span>

<span data-ttu-id="10b69-826">Skicka data över en DTLS-session</span><span class="sxs-lookup"><span data-stu-id="10b69-826">Send data over a DTLS session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-827">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-827">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a><span data-ttu-id="10b69-828">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-828">Description</span></span>

<span data-ttu-id="10b69-829">Den här tjänsten skickar ett data paket över en etablerad DTLS-session till en fjärran sluten DTLS-värd på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="10b69-829">This service sends a packet of data over an established DTLS Session to a remote DTLS host at the given IP address and port.</span></span> <span data-ttu-id="10b69-830">Sessionen som används är en aktiv DTLS-klientsession.</span><span class="sxs-lookup"><span data-stu-id="10b69-830">The session used is an active DTLS Client session.</span></span> <span data-ttu-id="10b69-831">Observera att IP-adressen och porten tillhandahålls på grund av tillstånds lös typ av UDP, men bör vanligt vis matcha adressen och porten som används för att starta sessionen i nx_secure_dtls_session_start.</span><span class="sxs-lookup"><span data-stu-id="10b69-831">Note that the IP address and port are provided due to the stateless nature of UDP but should generally match the address and port used to start the session in nx_secure_dtls_session_start.</span></span>

<span data-ttu-id="10b69-832">De data som anges i paketet, som måste allokeras med hjälp av *nx_secure_dtls_packet_allocate*, krypteras med hjälp av DTLS-sessionens kryptografiska parametrar och rutiner och sedan skickas till fjärrvärden över DTLS-SESSIONens UDP-socket.</span><span class="sxs-lookup"><span data-stu-id="10b69-832">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Session’s UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-833">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-833">Parameters</span></span>

- <span data-ttu-id="10b69-834">**session_ptr** Pekar mot en aktiv DTLS-klientsession.</span><span class="sxs-lookup"><span data-stu-id="10b69-834">**session_ptr** Pointer to an active DTLS client session instance.</span></span>
- <span data-ttu-id="10b69-835">**packet_ptr** Pekare till en NX_PACKET instans som har allokerats tidigare och fyllts med program data.</span><span class="sxs-lookup"><span data-stu-id="10b69-835">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>
- <span data-ttu-id="10b69-836">**ip_address** Pekar till en NXD_ADDRESS-struktur som innehåller IP-adressen för fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="10b69-836">**ip_address** Pointer to an NXD_ADDRESS structure containing the IP address of the remote host.</span></span>
- <span data-ttu-id="10b69-837">**port** UDP-port på fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="10b69-837">**port** UDP port on the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-838">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-838">Return Values</span></span>

- <span data-ttu-id="10b69-839">**NX_SUCCESS** (0x00) paket sändningen har skickats.</span><span class="sxs-lookup"><span data-stu-id="10b69-839">**NX_SUCCESS** (0x00) Successful send of packet.</span></span>
- <span data-ttu-id="10b69-840">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-840">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0X109) ett fel uppstod i den underliggande UDP-åtgärden för att skicka.</span><span class="sxs-lookup"><span data-stu-id="10b69-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-842">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-842">Allowed From</span></span>

<span data-ttu-id="10b69-843">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-843">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-844">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-844">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
    /* Error! */
    return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="10b69-845">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-845">See Also</span></span>

- <span data-ttu-id="10b69-846">nx_secure_dtls_client_session_start nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="10b69-846">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="10b69-847">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="10b69-847">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a><span data-ttu-id="10b69-848">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="10b69-848">nx_secure_dtls_session_trusted_certificate_add</span></span>

<span data-ttu-id="10b69-849">Lägga till ett certifikat för betrodd certifikat utfärdare i en NetX Secure DTLS-session</span><span class="sxs-lookup"><span data-stu-id="10b69-849">Add a trusted CA certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-850">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-850">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="10b69-851">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-851">Description</span></span>

<span data-ttu-id="10b69-852">Den här tjänsten lägger till en betrodd certifikat utfärdare eller ett mellanliggande CA X. 509-certifikat till en DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-852">This service adds a trusted CA or intermediate CA X.509 certificate to a DTLS Session instance.</span></span> <span data-ttu-id="10b69-853">En DTLS-klient kräver minst ett betrott certifikat för att verifiera fjärrservernamn om inte en alternativ autentiseringsmekanism används (t. ex. i förväg delade nycklar).</span><span class="sxs-lookup"><span data-stu-id="10b69-853">A DTLS Client requires at least one trusted certificate in order to validate remote server certificates unless an alternative authentication mechanism is used (e.g. Pre-Shared Keys).</span></span> <span data-ttu-id="10b69-854">Ett betrott certifikat har vanligt vis ingen privat nyckel.</span><span class="sxs-lookup"><span data-stu-id="10b69-854">A trusted certificate does not usually have a private key.</span></span>

<span data-ttu-id="10b69-855">Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet.</span><span class="sxs-lookup"><span data-stu-id="10b69-855">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="10b69-856">Detta gör att certifikatet enkelt kan tas bort eller hittas i händelse av att det finns flera identitets certifikat med samma X. 509-namn som finns i certifikat arkivet DTLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-856">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="10b69-857">Mer information om X. 509-certifikat finns i användar handboken för NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-857">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-858">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-858">Parameters</span></span>

- <span data-ttu-id="10b69-859">**session_ptr** Pekar till en tidigare skapad DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-859">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="10b69-860">**certifikat** Pekar till en tidigare initierad X. 509-certifikat struktur.</span><span class="sxs-lookup"><span data-stu-id="10b69-860">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="10b69-861">**cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-861">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="10b69-862">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-862">Return Values</span></span>

- <span data-ttu-id="10b69-863">**NX_SUCCESS** (0x00) det framgångs rika tillägget av certifikat till DTLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="10b69-863">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="10b69-864">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-864">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-865">**NX_INVALID_PARAMETERS** (0X4D) ett certifikat-ID på 0 skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-865">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-866">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-866">Allowed From</span></span>

<span data-ttu-id="10b69-867">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-868">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-868">Example</span></span>

<span data-ttu-id="10b69-869">\* Se referens för *nx_secure_dtls_session_create* ett mer komplett exempel.</span><span class="sxs-lookup"><span data-stu-id="10b69-869">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                            trusted_cert_der,
                                            trusted_cert_der_len,
                                            NX_NULL, 0, NX_NULL, 0,
                                            NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the trusted store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                      &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);

    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
         &udp_socket, &server_ip, 4443,
         NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a><span data-ttu-id="10b69-870">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-870">See Also</span></span>

- <span data-ttu-id="10b69-871">nx_secure_dtls_session_create nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="10b69-871">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="10b69-872">nx_secure_dtls_session_send nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="10b69-872">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="10b69-873">nx_secure_dtls_session_trusted_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="10b69-873">nx_secure_dtls_session_trusted_certificate_remove,</span></span>
- <span data-ttu-id="10b69-874">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="10b69-874">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a><span data-ttu-id="10b69-875">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="10b69-875">nx_secure_dtls_session_trusted_certificate_remove</span></span>

<span data-ttu-id="10b69-876">Ta bort ett certifikat för betrodd certifikat utfärdare från en NetX Secure DTLS-session</span><span class="sxs-lookup"><span data-stu-id="10b69-876">Remove a trusted CA certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="10b69-877">Prototyp</span><span class="sxs-lookup"><span data-stu-id="10b69-877">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="10b69-878">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="10b69-878">Description</span></span>

<span data-ttu-id="10b69-879">Den här tjänsten tar bort ett certifikat för betrodd certifikat utfärdare från en DTLS med antingen ett certifikat-ID-nummer (tilldelat när certifikatet lades till nx_secure_dtls_session_trusted_certificate_add) eller fältet X. 509 CommonName.</span><span class="sxs-lookup"><span data-stu-id="10b69-879">This service removes a trusted CA certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_trusted_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="10b69-880">Om common_name används för att matcha certifikatet, ska cert_id-parametern anges till 0.</span><span class="sxs-lookup"><span data-stu-id="10b69-880">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="10b69-881">Om cert_id används ska common_name skickas värdet NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="10b69-881">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="10b69-882">Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet.</span><span class="sxs-lookup"><span data-stu-id="10b69-882">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="10b69-883">Detta gör att certifikatet enkelt kan tas bort eller hittas i händelse av att det finns flera identitets certifikat med samma X. 509-namn som finns i certifikat arkivet DTLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-883">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="10b69-884">Mer information om X. 509-certifikat finns i användar handboken för NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="10b69-884">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="10b69-885">Parametrar</span><span class="sxs-lookup"><span data-stu-id="10b69-885">Parameters</span></span>

- <span data-ttu-id="10b69-886">**session_ptr** Pekar till en tidigare skapad DTLS-session.</span><span class="sxs-lookup"><span data-stu-id="10b69-886">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="10b69-887">**common_name** Pekar på den CommonName-sträng som ska matchas.</span><span class="sxs-lookup"><span data-stu-id="10b69-887">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="10b69-888">**common_name_length** Längden på common_name strängen.</span><span class="sxs-lookup"><span data-stu-id="10b69-888">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="10b69-889">**cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.</span><span class="sxs-lookup"><span data-stu-id="10b69-889">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>


### <a name="return-values"></a><span data-ttu-id="10b69-890">Retur värden</span><span class="sxs-lookup"><span data-stu-id="10b69-890">Return Values</span></span>

- <span data-ttu-id="10b69-891">**NX_SUCCESS** (0x00) borttagning av certifikat från DTLS-sessionen lyckades.</span><span class="sxs-lookup"><span data-stu-id="10b69-891">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="10b69-892">**NX_PTR_ERROR** (0X07) ogiltig pekare skickades.</span><span class="sxs-lookup"><span data-stu-id="10b69-892">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="10b69-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det gick inte att hitta något certifikat som matchar cert_id eller common_name i den aktuella DTLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="10b69-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="10b69-894">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="10b69-894">Allowed From</span></span>

<span data-ttu-id="10b69-895">Konversation</span><span class="sxs-lookup"><span data-stu-id="10b69-895">Threads</span></span>

### <a name="example"></a><span data-ttu-id="10b69-896">Exempel</span><span class="sxs-lookup"><span data-stu-id="10b69-896">Example</span></span>

<span data-ttu-id="10b69-897">\* Se referens för *nx_secure_dtls_session_create* ett mer komplett exempel.</span><span class="sxs-lookup"><span data-stu-id="10b69-897">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL, 0,
                                    NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
    status = nx_secure_dtls_session_trusted_certificate_remove(&client_dtls_session,
                                                                    NX_NULL, 0, 1);
}

```

### <a name="see-also"></a><span data-ttu-id="10b69-898">Se även</span><span class="sxs-lookup"><span data-stu-id="10b69-898">See Also</span></span>

- <span data-ttu-id="10b69-899">nx_secure_dtls_session_create nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="10b69-899">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="10b69-900">nx_secure_dtls_session_send nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="10b69-900">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="10b69-901">nx_secure_dtls_session_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="10b69-901">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="10b69-902">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="10b69-902">nx_secure_x509_certificate_initialize</span></span>
