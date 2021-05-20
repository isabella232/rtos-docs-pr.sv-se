---
title: Kapitel 4 – Beskrivning Azure RTOS NetX Secure-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Secure-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80ec22058ab64ed0c6258bb3d9364ec44f9a741b
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223400"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a><span data-ttu-id="ee5c6-103">Kapitel 4 – Beskrivning Azure RTOS NetX Secure-tjänster</span><span class="sxs-lookup"><span data-stu-id="ee5c6-103">Chapter 4 - Description of Azure RTOS NetX Secure services</span></span>

<span data-ttu-id="ee5c6-104">Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Secure-tjänster (anges nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-104">This chapter contains a description of all Azure RTOS NetX Secure services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="ee5c6-105">I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **NX_SECURE_DISABLE_ERROR_CHECKING-makrot** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="ee5c6-106">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="ee5c6-106">nx_secure_crypto_table_self_test</span></span>](#nx_secure_crypto_table_self_test)
  - <span data-ttu-id="ee5c6-107">Utföra self_test på kryptografimetoderna</span><span class="sxs-lookup"><span data-stu-id="ee5c6-107">Perform self_test on the crypto methods</span></span>
- [<span data-ttu-id="ee5c6-108">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="ee5c6-108">nx_secure_module_hash_compute</span></span>](#nx_secure_module_hash_compute)
  - <span data-ttu-id="ee5c6-109">Beräknar hash-värdet med hjälp user_supplied hash-funktion</span><span class="sxs-lookup"><span data-stu-id="ee5c6-109">Computes hash value using user_supplied hash function</span></span>
- [<span data-ttu-id="ee5c6-110">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-110">nx_secure_tls_active_certificate_set</span></span>](#nx_secure_tls_active_certificate_set)
  - <span data-ttu-id="ee5c6-111">Ange det aktiva identitetscertifikatet för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-111">Set the active identity certificate for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-112">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-112">nx_secure_tls_client_psk_set</span></span>](#nx_secure_tls_client_psk_set)
  - <span data-ttu-id="ee5c6-113">Ange en Pre_Shared nyckel för en NetX Secure TLS-klientsession</span><span class="sxs-lookup"><span data-stu-id="ee5c6-113">Set a Pre_Shared Key for a NetX Secure TLS Client Session</span></span>
- [<span data-ttu-id="ee5c6-114">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-114">nx_secure_tls_initialize</span></span>](#nx_secure_tls_initialize)
  - <span data-ttu-id="ee5c6-115">Initierar NetX Secure TLS-modulen]</span><span class="sxs-lookup"><span data-stu-id="ee5c6-115">Initializes the NetX Secure TLS module]</span></span>
- [<span data-ttu-id="ee5c6-116">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-116">nx_secure_tls_local_certificate_add</span></span>](#nx_secure_tls_local_certificate_add)
  - <span data-ttu-id="ee5c6-117">Lägga till ett lokalt certifikat i NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-117">Add a local certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-118">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-118">nx_secure_tls_local_certificate_find</span></span>](#nx_secure_tls_local_certificate_find)
  - <span data-ttu-id="ee5c6-119">Hitta ett lokalt certifikat i en NetX Secure TLS-session efter eget namn</span><span class="sxs-lookup"><span data-stu-id="ee5c6-119">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>
- [<span data-ttu-id="ee5c6-120">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ee5c6-120">nx_secure_tls_local_certificate_remove</span></span>](#nx_secure_tls_local_certificate_remove)
  - <span data-ttu-id="ee5c6-121">Ta bort lokalt certifikat från NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-121">Remove local certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-122">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-122">nx_secure_tls_metadata_size_calculate</span></span>](#nx_secure_tls_metadata_size_calculate)
  - <span data-ttu-id="ee5c6-123">Beräkna storleken på kryptografiska metadata för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-123">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-124">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-124">nx_secure_tls_packet_allocate</span></span>](#nx_secure_tls_packet_allocate)
  - <span data-ttu-id="ee5c6-125">Allokera ett paket för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-125">Allocate a packet for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-126">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-126">nx_secure_tls_psk_add</span></span>](#nx_secure_tls_psk_add)
  - <span data-ttu-id="ee5c6-127">Lägga till Pre_Shared nyckel i en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-127">Add a Pre_Shared Key to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-128">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-128">nx_secure_tls_remote_certificate_allocate</span></span>](#nx_secure_tls_remote_certificate_allocate)
  - <span data-ttu-id="ee5c6-129">Allokera utrymme för certifikatet som tillhandahålls av en fjärransluten TLS-värd</span><span class="sxs-lookup"><span data-stu-id="ee5c6-129">Allocate space for the certificate provided by a remote TLS host</span></span>
- [<span data-ttu-id="ee5c6-130">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-130">nx_secure_tls_remote_certificate_buffer_allocate</span></span>](#nx_secure_tls_remote_certificate_buffer_allocate)
  - <span data-ttu-id="ee5c6-131">Allokera utrymme för alla certifikat som tillhandahålls av en fjärransluten TLS-värd</span><span class="sxs-lookup"><span data-stu-id="ee5c6-131">Allocate space for all certificates provided by a remote TLS host</span></span>
- [<span data-ttu-id="ee5c6-132">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="ee5c6-132">nx_secure_tls_remote_certificate_free_all</span></span>](#nx_secure_tls_remote_certificate_free_all)
  - <span data-ttu-id="ee5c6-133">Ledigt utrymme allokerat för inkommande certifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-133">Free space allocated for incoming certificates</span></span>
- [<span data-ttu-id="ee5c6-134">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-134">nx_secure_tls_server_certificate_add</span></span>](#nx_secure_tls_server_certificate_add)
  - <span data-ttu-id="ee5c6-135">Lägga till ett certifikat specifikt för TLS-servrar med hjälp av en numerisk identifierare</span><span class="sxs-lookup"><span data-stu-id="ee5c6-135">Add a certificate specifically for TLS servers using a numeric identifier</span></span>
- [<span data-ttu-id="ee5c6-136">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-136">nx_secure_tls_server_certificate_find</span></span>](#nx_secure_tls_server_certificate_find)
  - <span data-ttu-id="ee5c6-137">Hitta ett certifikat med hjälp av en numerisk identifierare</span><span class="sxs-lookup"><span data-stu-id="ee5c6-137">Find a certificate using a numeric identifier</span></span>
- [<span data-ttu-id="ee5c6-138">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ee5c6-138">nx_secure_tls_server_certificate_remove</span></span>](#nx_secure_tls_server_certificate_remove)
  - <span data-ttu-id="ee5c6-139">Ta bort ett lokalt servercertifikat med hjälp av en numerisk identifierare</span><span class="sxs-lookup"><span data-stu-id="ee5c6-139">Remove a local server certificate using a numeric identifier</span></span>
- [<span data-ttu-id="ee5c6-140">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-140">nx_secure_tls_session_certificate_callback_set</span></span>](#nx_secure_tls_session_certificate_callback_set)
  - <span data-ttu-id="ee5c6-141">Konfigurera ett återanrop för TLS som ska användas för ytterligare certifikatverifiering</span><span class="sxs-lookup"><span data-stu-id="ee5c6-141">Set up a callback for TLS to use for additional certificate validation</span></span>
- [<span data-ttu-id="ee5c6-142">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-142">nx_secure_tls_session_client_callback_set</span></span>](#nx_secure_tls_session_client_callback_set)
  - <span data-ttu-id="ee5c6-143">Konfigurera ett återanrop för TLS som ska anropas i början av en TLS-klienthandskakning</span><span class="sxs-lookup"><span data-stu-id="ee5c6-143">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>
- [<span data-ttu-id="ee5c6-144">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="ee5c6-144">nx_secure_tls_session_x509_client_verify_configure</span></span>](#nx_secure_tls_session_x509_client_verify_configure)
  - <span data-ttu-id="ee5c6-145">Aktivera X.509-klientverifiering och allokera utrymme för klientcertifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-145">Enable client X.509 verification and allocate space for client certificates</span></span>
- [<span data-ttu-id="ee5c6-146">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="ee5c6-146">nx_secure_tls_session_client_verify_disable</span></span>](#nx_secure_tls_session_client_verify_disable)
  - <span data-ttu-id="ee5c6-147">Inaktivera klientcertifikatautentisering för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-147">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-148">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="ee5c6-148">nx_secure_tls_session_client_verify_enable</span></span>](#nx_secure_tls_session_client_verify_enable)
  - <span data-ttu-id="ee5c6-149">Aktivera klientcertifikatautentisering för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-149">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-150">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-150">nx_secure_tls_session_create</span></span>](#nx_secure_tls_session_create)
  - <span data-ttu-id="ee5c6-151">Skapa en NetX Secure TLS-session för säker kommunikation</span><span class="sxs-lookup"><span data-stu-id="ee5c6-151">Create a NetX Secure TLS Session for secure communications</span></span>
- [<span data-ttu-id="ee5c6-152">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ee5c6-152">nx_secure_tls_session_delete</span></span>](#nx_secure_tls_session_delete)
  - <span data-ttu-id="ee5c6-153">Ta bort en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-153">Delete a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-154">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="ee5c6-154">nx_secure_tls_session_end</span></span>](#nx_secure_tls_session_end)
  - <span data-ttu-id="ee5c6-155">Avsluta en aktiv NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-155">End an active NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-156">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-156">nx_secure_tls_session_packet_buffer_set</span></span>](#nx_secure_tls_session_packet_buffer_set)
  - <span data-ttu-id="ee5c6-157">Ange paketsammansättningsbufferten för en Säker NetX-TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-157">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-158">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="ee5c6-158">nx_secure_tls_session_protocol_version_override</span></span>](#nx_secure_tls_session_protocol_version_override)
  - <span data-ttu-id="ee5c6-159">Åsidosätt standardversionen av TLS-protokollet för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-159">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-160">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-160">nx_secure_tls_session_receive</span></span>](#nx_secure_tls_session_receive)
  - <span data-ttu-id="ee5c6-161">Ta emot data från en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-161">Receive data from a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-162">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-162">nx_secure_tls_session_renegotiate_callback_set</span></span>](#nx_secure_tls_session_renegotiate_callback_set)
  - <span data-ttu-id="ee5c6-163">Tilldela ett återanrop som anropas i början av en omförhandling av sessionen</span><span class="sxs-lookup"><span data-stu-id="ee5c6-163">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>
- [<span data-ttu-id="ee5c6-164">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-164">nx_secure_tls_session_renegotiate</span></span>](#nx_secure_tls_session_renegotiate)
  - <span data-ttu-id="ee5c6-165">Initiera en omförhandling av sessionshandskakning med fjärrvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-165">Initiate a session renegotiation handshake with the remote host</span></span>
- [<span data-ttu-id="ee5c6-166">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="ee5c6-166">nx_secure_tls_session_reset</span></span>](#nx_secure_tls_session_reset)
  - <span data-ttu-id="ee5c6-167">Rensa och återställa en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-167">Clear out and reset a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-168">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-168">nx_secure_tls_session_send</span></span>](#nx_secure_tls_session_send)
  - <span data-ttu-id="ee5c6-169">Skicka data via en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-169">Send data through a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-170">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-170">nx_secure_tls_session_server_callback_set</span></span>](#nx_secure_tls_session_server_callback_set)
  - <span data-ttu-id="ee5c6-171">Konfigurera ett återanrop för TLS som ska anropas i början av en TLS-serverhandskakning</span><span class="sxs-lookup"><span data-stu-id="ee5c6-171">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>
- [<span data-ttu-id="ee5c6-172">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="ee5c6-172">nx_secure_tls_session_sni_extension_parse</span></span>](#nx_secure_tls_session_sni_extension_parse)
  - <span data-ttu-id="ee5c6-173">Parsa ett Servernamnindikator (SNI)-tillägg som tagits emot från en TLS-klient</span><span class="sxs-lookup"><span data-stu-id="ee5c6-173">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>
- [<span data-ttu-id="ee5c6-174">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-174">nx_secure_tls_session_sni_extension_set</span></span>](#nx_secure_tls_session_sni_extension_set)
  - <span data-ttu-id="ee5c6-175">Ange ett DNS Servernamnindikator tillägg (SNI) som ska skickas till en fjärrserver</span><span class="sxs-lookup"><span data-stu-id="ee5c6-175">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>
- [<span data-ttu-id="ee5c6-176">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-176">nx_secure_tls_session_start</span></span>](#nx_secure_tls_session_start)
  - <span data-ttu-id="ee5c6-177">Starta en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-177">Start a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-178">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-178">nx_secure_tls_session_time_function_set</span></span>](#nx_secure_tls_session_time_function_set)
  - <span data-ttu-id="ee5c6-179">Tilldela en tidsstämpelfunktion till en Säker NetX-TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-179">Assign a timestamp function to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-180">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-180">nx_secure_tls_trusted_certificate_add</span></span>](#nx_secure_tls_trusted_certificate_add)
  - <span data-ttu-id="ee5c6-181">Lägga till betrott certifikat i NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-181">Add trusted certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-182">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ee5c6-182">nx_secure_tls_trusted_certificate_remove</span></span>](#nx_secure_tls_trusted_certificate_remove)
  - <span data-ttu-id="ee5c6-183">Ta bort betrott certifikat från NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-183">Remove trusted certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="ee5c6-184">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-184">nx_secure_x509_certificate_initialize</span></span>](#nx_secure_x509_certificate_initialize)
  - <span data-ttu-id="ee5c6-185">Initiera X.509-certifikat för NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="ee5c6-185">Initialize X.509 Certificate for NetX Secure TLS</span></span>
- [<span data-ttu-id="ee5c6-186">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-186">nx_secure_x509_common_name_dns_check</span></span>](#nx_secure_x509_common_name_dns_check)
  - <span data-ttu-id="ee5c6-187">Kontrollera DNS-namn mot X.509-certifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-187">Check DNS name against X.509 Certificate</span></span>
- [<span data-ttu-id="ee5c6-188">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-188">nx_secure_x509_crl_revocation_check</span></span>](#nx_secure_x509_crl_revocation_check)
  - <span data-ttu-id="ee5c6-189">Kontrollera X.509-certifikat mot en agen lista över återkallade certifikat (CRL)]</span><span class="sxs-lookup"><span data-stu-id="ee5c6-189">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)]</span></span>
- [<span data-ttu-id="ee5c6-190">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-190">nx_secure_x509_dns_name_initialize</span></span>](#nx_secure_x509_dns_name_initialize)
  - <span data-ttu-id="ee5c6-191">Initiera en X.509 DNS-namnstruktur</span><span class="sxs-lookup"><span data-stu-id="ee5c6-191">Initialize an X.509 DNS name structure</span></span>
- [<span data-ttu-id="ee5c6-192">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="ee5c6-192">nx_secure_x509_extended_key_usage_extension_parse</span></span>](#nx_secure_x509_extended_key_usage_extension_parse)
  - <span data-ttu-id="ee5c6-193">Hitta och parsa ett utökat X.509-nyckelanvändningstillägg i ett X.509-certifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-193">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>
- [<span data-ttu-id="ee5c6-194">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-194">nx_secure_x509_extension_find</span></span>](#nx_secure_x509_extension_find)
  - <span data-ttu-id="ee5c6-195">Hitta och returnera ett X.509-tillägg i ett X.509-certifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-195">Find and return an X.509 extension in an X.509 certificate</span></span>
- [<span data-ttu-id="ee5c6-196">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="ee5c6-196">nx_secure_x509_key_usage_extension_parse</span></span>](#nx_secure_x509_key_usage_extension_parse)
  - <span data-ttu-id="ee5c6-197">Hitta och parsa ett X.509-nyckelanvändningstillägg i ett X.509-certifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-197">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

## <a name="nx_secure_crypto_table_self_test"></a><span data-ttu-id="ee5c6-198">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="ee5c6-198">nx_secure_crypto_table_self_test</span></span>

<span data-ttu-id="ee5c6-199">Utföra självtest på krypteringsmetoderna</span><span class="sxs-lookup"><span data-stu-id="ee5c6-199">Perform self-test on the crypto methods</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-200">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-200">Prototype</span></span>

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a><span data-ttu-id="ee5c6-201">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-201">Description</span></span>

<span data-ttu-id="ee5c6-202">Den här tjänsten kör via kryptografimetodens självtester för att verifiera.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-202">This service runs through the crypto method self tests to validate.</span></span> <span data-ttu-id="ee5c6-203">Självtestet är bara tillgängligt om NetX Secure-biblioteket har skapats med symbolen NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK definieras.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-203">The self test is available only if NetX Secure library is built with the symbol NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK defined.</span></span>

<span data-ttu-id="ee5c6-204">För varje kryptografimetod som stöds tillhandahåller självtestet fördefinierade indata och verifierar att utdata matchar det fördefinierade förväntade värdet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-204">For each supported crypto method, the self test provides pre-defined input data, and verified the output matches the pre-defined expected value.</span></span>

<span data-ttu-id="ee5c6-205">NetX Secure crypto self test har stöd för följande algoritmer och nyckelstorlekar:</span><span class="sxs-lookup"><span data-stu-id="ee5c6-205">NetX Secure crypto self test supports the following algorithms and key sizes:</span></span>

- <span data-ttu-id="ee5c6-206">DES: kryptering och dekryptering</span><span class="sxs-lookup"><span data-stu-id="ee5c6-206">DES: encryption and decryption</span></span>
- <span data-ttu-id="ee5c6-207">Triple DES (3DES): kryptering och dekryptering</span><span class="sxs-lookup"><span data-stu-id="ee5c6-207">Triple DES (3DES): encryption and decryption</span></span>
- <span data-ttu-id="ee5c6-208">AES: 128-, 192-, 256-bitars nyckelstorlek, kryptering och dekryptering i CBC-läge och räknarläge.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-208">AES: 128-, 192-, 256-bit key size, encryption and decryption, in CBC mode and counter mode.</span></span>
- <span data-ttu-id="ee5c6-209">HMAC-MD5: autentisering och hash-beräkning</span><span class="sxs-lookup"><span data-stu-id="ee5c6-209">HMAC-MD5: authentication and hash computation</span></span>
- <span data-ttu-id="ee5c6-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, autentisering och hash-beräkning</span><span class="sxs-lookup"><span data-stu-id="ee5c6-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, authentication and hash computation</span></span>
- <span data-ttu-id="ee5c6-211">MD5: autentisering</span><span class="sxs-lookup"><span data-stu-id="ee5c6-211">MD5: authentication</span></span>
- <span data-ttu-id="ee5c6-212">Pseudoslumpfunktion (PRF): PRF_HMAC_SHA1 och PRF_HMAC_SHA2-256</span><span class="sxs-lookup"><span data-stu-id="ee5c6-212">Pseudo-random Function (PRF): PRF_HMAC_SHA1 and PRF_HMAC_SHA2-256</span></span>
- <span data-ttu-id="ee5c6-213">RSA: 1024-, 2048-, 4096-bitars RSA power-modulus operation</span><span class="sxs-lookup"><span data-stu-id="ee5c6-213">RSA: 1024-, 2048-, 4096-bit RSA power-modulus operation</span></span>
- <span data-ttu-id="ee5c6-214">SHA: SHA1-autentisering (96- och 160-bitars), SHA2-autentisering (256-bitars, 384-bitars, 512-bitars)</span><span class="sxs-lookup"><span data-stu-id="ee5c6-214">SHA: SHA1 (96- and 160-bit), SHA2 (256bit, 384bit, 512bit) authentication</span></span>

<span data-ttu-id="ee5c6-215">Den här funktionen har de inbyggda vektorerna för de krypteringsalgoritmer som anges ovan.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-215">This function has the built-in vectors for the crypto algorithms listed above.</span></span> <span data-ttu-id="ee5c6-216">Den testar dock bara de som listas i *cipher_table skickas* till den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-216">However it only tests the ones listed in the *cipher_table* passed into this function.</span></span> <span data-ttu-id="ee5c6-217">För en TLS-session används till exempel bara chiffer-TLS_RSA_WITH_AES_128_CBC_SHA, den här funktionen utför självtest på RSA (1024-, 2048-, 4096-bitars), AES-CBC (128-bitars) och SHA1.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-217">For example, for a TLS session uses only the ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, this function will perform self test on the RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) and SHA1.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-218">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-218">Parameters</span></span>

- <span data-ttu-id="ee5c6-219">**crypto_table** Pekare till kryptografitabellen som används av TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-219">**crypto_table** Pointer to the crypto table being used by the TLS session.</span></span> <span data-ttu-id="ee5c6-220">Det här är samma crypto_table skickas till **_nx_secure_tls_session_create()-anropet._**</span><span class="sxs-lookup"><span data-stu-id="ee5c6-220">This is the same crypto_table being passed into the **_nx_secure_tls_session_create()_** call.</span></span>
- <span data-ttu-id="ee5c6-221">**metadata** Pekare till blanksteg för kryptografimetadataområdet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-221">**metadata** Pointer to space for cryptography metadata area.</span></span> <span data-ttu-id="ee5c6-222">.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-222">.</span></span>
- <span data-ttu-id="ee5c6-223">**metadata_size** Storleken på metadatabufferten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-223">**metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-224">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-224">Return Values</span></span>

- <span data-ttu-id="ee5c6-225">**NX_SECURE_TLS_SUCCESS** (0x00) Har testat de angivna kryptografimetoderna.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-225">**NX_SECURE_TLS_SUCCESS** (0x00) Successfully tested the crypto methods provided.</span></span>
- <span data-ttu-id="ee5c6-226">**NX_PTR_ERROR** (0x07) Ogiltig kryptografimetodstruktur</span><span class="sxs-lookup"><span data-stu-id="ee5c6-226">**NX_PTR_ERROR** (0x07) Invalid crypto method structure</span></span>
- <span data-ttu-id="ee5c6-227">**NX_NOT_SUCCESSFUL** (0x43) Crypto-självtest misslyckas.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-227">**NX_NOT_SUCCESSFUL** (0x43) Crypto self test fails.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-228">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-228">Allowed From</span></span>

<span data-ttu-id="ee5c6-229">Initiering, Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-229">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-230">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-230">Example</span></span>

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-231">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-231">See Also</span></span>

- <span data-ttu-id="ee5c6-232">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-232">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="ee5c6-233">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="ee5c6-233">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="ee5c6-234">Beräknar hash-värdet med hjälp av en hash-funktion som användaren har angett</span><span class="sxs-lookup"><span data-stu-id="ee5c6-234">Computes hash value using user-supplied hash function</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-235">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-235">Prototype</span></span>

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="ee5c6-236">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-236">Description</span></span>

<span data-ttu-id="ee5c6-237">Den här funktionen beräknar hash-värdet för dataströmmen i det angivna minnesområdet med hjälp av den angivna kryptografimetoden HMAC och nyckelsträngen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-237">This function computes the hash value of the data stream in the specified memory area, using supplied HMAC crypto method and the key string.</span></span> <span data-ttu-id="ee5c6-238">Modulens hash-beräkningsfunktion är bara tillgänglig om NetX Secure-biblioteket har skapats med följande symbol som definieras: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span><span class="sxs-lookup"><span data-stu-id="ee5c6-238">The module hash compute function is available only if NetX Secure library is built with the following symbol being defined: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-239">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-239">Parameters</span></span>

- <span data-ttu-id="ee5c6-240">**hmac_ptr** Pekare till den HMAC-kryptografimetod som används för hash-värdeberäkningen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-240">**hmac_ptr** Pointer to the HMAC crypto method being used for the hash value computation.</span></span>
- <span data-ttu-id="ee5c6-241">**start_address** Startadressen för databufferten</span><span class="sxs-lookup"><span data-stu-id="ee5c6-241">**start_address** The starting address of the data buffer</span></span>
- <span data-ttu-id="ee5c6-242">**end_address** Slutadressen för databufferten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-242">**end_address** The ending address of the data buffer.</span></span> <span data-ttu-id="ee5c6-243">Observera att hashberäkningen inte omfattar data i den här end_address.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-243">Note that hash computation does not cover the data at this end_address.</span></span>
- <span data-ttu-id="ee5c6-244">**nyckel** Nyckelsträngen som används i HMAC-beräkningen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-244">**key** The key string being used in the HMAC computation.</span></span>
- <span data-ttu-id="ee5c6-245">**key_length** Nyckelsträngens storlek i byte</span><span class="sxs-lookup"><span data-stu-id="ee5c6-245">**key_length** The size of the key string, in bytes</span></span>
- <span data-ttu-id="ee5c6-246">**metadata** Pekare till blanksteg som används av HMAC-algoritmen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-246">**metadata** Pointer to space used by the HMAC algorithm.</span></span>
- <span data-ttu-id="ee5c6-247">**metadata_size** Storleken på metadatabufferten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-247">**metadata_size** Size of the metadata buffer.</span></span>
- <span data-ttu-id="ee5c6-248">**output_buffer** Den minnesplats där hash-utdata lagras.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-248">**output_buffer** The memory location where the hash output is being stored at.</span></span>
- <span data-ttu-id="ee5c6-249">**output_buffer_size** Tillgängligt utrymme i utdatabufferten, i byte</span><span class="sxs-lookup"><span data-stu-id="ee5c6-249">**output_buffer_size** The available space of the output buffer, in bytes</span></span>
- <span data-ttu-id="ee5c6-250">**actual_size** Returneras av funktionen som anger det faktiska antalet byte som skrivs till output_buffer.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-250">**actual_size** Returned by the function indicating the actual number of bytes being written into the output_buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-251">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-251">Return Values</span></span>

- <span data-ttu-id="ee5c6-252">**0** Hash-värdet har beräknats.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-252">**0** Successfully computed the hash value.</span></span>
- <span data-ttu-id="ee5c6-253">**1** Hash-beräkningen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-253">**1** The hash computation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-254">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-254">Allowed From</span></span>

<span data-ttu-id="ee5c6-255">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-255">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-256">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-256">Example</span></span>

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-257">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-257">See Also</span></span>

- <span data-ttu-id="ee5c6-258">nx_secure_crypto_method_self_test</span><span class="sxs-lookup"><span data-stu-id="ee5c6-258">nx_secure_crypto_method_self_test</span></span>

## <a name="nx_secure_tls_active_certificate_set"></a><span data-ttu-id="ee5c6-259">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-259">nx_secure_tls_active_certificate_set</span></span>

<span data-ttu-id="ee5c6-260">Ange det aktiva identitetscertifikatet för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-260">Set the active identity certificate for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-261">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-261">Prototype</span></span>

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="ee5c6-262">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-262">Description</span></span>

<span data-ttu-id="ee5c6-263">Den här tjänsten är avsedd att anropas inifrån ett sessionsanrop (se nx_secure_tls_session_client_callback_set och nx_secure_tls_session_server_callback_set).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-263">This service is intended to be called from within a session callback (see nx_secure_tls_session_client_callback_set and nx_secure_tls_session_server_callback_set).</span></span> <span data-ttu-id="ee5c6-264">När det anropas med en tidigare initierad NX_SECURE_X509_CERT-struktur används det certifikatet i stället för standardidentitetscertifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-264">When called with a previously-initialized NX_SECURE_X509_CERT structure, that certificate will be used instead of the default identity certificate.</span></span> <span data-ttu-id="ee5c6-265">I de flesta fall måste certifikatet ha lagts till i det lokala arkivet (se nx_secure_tls_local_certificate_add) annars kan TLS-handskakningen misslyckas.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-265">In most cases, the certificate must have been added to the local store (see nx_secure_tls_local_certificate_add) or the TLS handshake may fail.</span></span>

<span data-ttu-id="ee5c6-266">Den här tjänsten är avsedd att tillåta att TLS stöder flera identitetscertifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-266">This service is intended to allow TLS to support multiple identity certificates.</span></span> <span data-ttu-id="ee5c6-267">Detta är användbart för en TLS-server som hanterar flera nätverksadresser så att servern kan välja ett lämpligt certifikat som ska tillhandahållas till fjärrklienten beroende på klientens startpunkt.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-267">This is useful for a TLS server that services multiple network addresses so the server can pick an appropriate certificate to provide to the remote client depending on the client's entrypoint.</span></span> <span data-ttu-id="ee5c6-268">För en TLS-klient kan den här rutinen användas för att ändra certifikatet som skickas till en fjärrserver vid körning när servern har identifierat sig själv i TLS-handskakningen (detta är mer ovanligt än TLS-serverns användningsfall).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-268">For a TLS client, this routine may be used to change the certificate sent to a remote server at runtime after the server has identified itself in the TLS handshake (this is more rare than the TLS server use-case).</span></span>

<span data-ttu-id="ee5c6-269">Om flera certifikat kan dela samma unika X.509-namn måste certifikat läggas till med hjälp av nx_secure_tls_server_certificate_add, vilket introducerar en numerisk identifierare som är separat från certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-269">In the case where multiple certificates may share the same X.509 distinguished name, certificates will need to be added using nx_secure_tls_server_certificate_add, which introduces a numeric identifier separate from the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-270">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-270">Parameters</span></span>

- <span data-ttu-id="ee5c6-271">**session_ptr** Pekare till en TLS-sessionsinstans som skickas till sessionsanropet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-271">**session_ptr** Pointer to a TLS Session instance passed into the session callback.</span></span>
- <span data-ttu-id="ee5c6-272">**certifikat** Pekare till ett initierat X.509-certifikat som ska användas för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-272">**certificate** Pointer to an initialized X.509 certificate that is to be used for the current session.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-273">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-273">Return Values</span></span>

- <span data-ttu-id="ee5c6-274">**NX_SUCCESS** (0x00) Lyckad tilldelning av certifikat till session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-274">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="ee5c6-275">**NX_PTR_ERROR** (0x07) Ogiltig TLS-session eller certifikat pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-275">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-276">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-276">Allowed From</span></span>

<span data-ttu-id="ee5c6-277">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-278">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-278">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-279">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-279">See Also</span></span>

- <span data-ttu-id="ee5c6-280">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-280">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-281">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-281">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="ee5c6-282">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-282">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="ee5c6-283">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-283">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="ee5c6-284">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-284">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="ee5c6-285">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-285">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="ee5c6-286">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ee5c6-286">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_client_psk_set"></a><span data-ttu-id="ee5c6-287">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-287">nx_secure_tls_client_psk_set</span></span>

<span data-ttu-id="ee5c6-288">Ange en i förväg delad nyckel för en NetX Secure TLS-klientsession</span><span class="sxs-lookup"><span data-stu-id="ee5c6-288">Set a Pre-Shared Key for a NetX Secure TLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-289">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-289">Prototype</span></span>

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a><span data-ttu-id="ee5c6-290">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-290">Description</span></span>

<span data-ttu-id="ee5c6-291">Den här tjänsten lägger till en I förväg delad nyckel (PSK), dess identitetssträng och en identitetstips till ett TLS-sessionskontrollblock och anger att PSK ska användas i efterföljande TLS-klientanslutningar.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-291">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block, and sets that PSK to be used in subsequent TLS Client connections.</span></span> <span data-ttu-id="ee5c6-292">PSK används i stället för ett digitalt certifikat när PSK-chiffer har aktiverats och används.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-292">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="ee5c6-293">I det här fallet är PSK associerad med en specifik TLS-fjärrserver som TLS-klienten vill kommunicera med.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-293">In this case, the PSK is associated with a specific remote TLS Server with which the TLS Client wishes to communicate.</span></span> <span data-ttu-id="ee5c6-294">PSK-uppsättningen via detta API kommer att tillhandahållas till den fjärranslutna TLS-servervärden under nästa TLS-handskakning.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-294">The PSK set through this API will be provided to the remote TLS Server host during the next TLS handshake.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-295">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-295">Parameters</span></span>

- <span data-ttu-id="ee5c6-296">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-296">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-297">**pre_shared_key** Det faktiska PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-297">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="ee5c6-298">**psk_length** Längden på PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-298">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="ee5c6-299">**psk_identity** En sträng som används för att identifiera det här PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-299">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="ee5c6-300">**identity_length** Längden på PSK-identiteten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-300">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="ee5c6-301">**tips** En sträng som används för att ange vilken grupp av PSK:er som ska väljas på en TLS-server.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-301">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="ee5c6-302">**hint_length** Längden på tipssträngen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-302">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-303">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-303">Return Values</span></span>

- <span data-ttu-id="ee5c6-304">**NX_SUCCESS** (0x00) Lyckad addition av PSK.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-304">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="ee5c6-305">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-305">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="ee5c6-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Det går inte att lägga till ytterligare en PSK.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-307">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-307">Allowed From</span></span>

<span data-ttu-id="ee5c6-308">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-308">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-309">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-309">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-310">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-310">See Also</span></span>

- <span data-ttu-id="ee5c6-311">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-311">nx_secure_tls_psk_add</span></span>
- <span data-ttu-id="ee5c6-312">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-312">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-313">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-313">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-314">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-314">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-315">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-315">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_initialize"></a><span data-ttu-id="ee5c6-316">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-316">nx_secure_tls_initialize</span></span>

<span data-ttu-id="ee5c6-317">Initierar NetX Secure TLS-modulen</span><span class="sxs-lookup"><span data-stu-id="ee5c6-317">Initializes the NetX Secure TLS module</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-318">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-318">Prototype</span></span>

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="ee5c6-319">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-319">Description</span></span>

<span data-ttu-id="ee5c6-320">Den här tjänsten initierar NetX Secure TLS-modulen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-320">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="ee5c6-321">Den måste anropas innan andra NetX Secure-tjänster kan nås.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-321">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-322">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-322">Parameters</span></span>

<span data-ttu-id="ee5c6-323">Ingen</span><span class="sxs-lookup"><span data-stu-id="ee5c6-323">None</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-324">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-324">Return Values</span></span>

<span data-ttu-id="ee5c6-325">Ingen</span><span class="sxs-lookup"><span data-stu-id="ee5c6-325">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-326">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-326">Allowed From</span></span>

<span data-ttu-id="ee5c6-327">Initiering, Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-327">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-328">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-328">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-329">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-329">See Also</span></span>

- <span data-ttu-id="ee5c6-330">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-330">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_local_certificate_add"></a><span data-ttu-id="ee5c6-331">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-331">nx_secure_tls_local_certificate_add</span></span>

<span data-ttu-id="ee5c6-332">Lägga till ett lokalt certifikat i NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-332">Add a local certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-333">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-333">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="ee5c6-334">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-334">Description</span></span>

<span data-ttu-id="ee5c6-335">Den här tjänsten lägger till en NX_SECURE_X509_CERT instans av en struktur till det lokala arkivet för en TLS-session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-335">This service adds an initialized NX_SECURE_X509_CERT structure instance to the local store of a TLS session.</span></span> <span data-ttu-id="ee5c6-336">Det här certifikatet kan användas av TLS-stacken för att identifiera enheten under TLS-handskakningen (om den har markerats som ett identitetscertifikat under initieringen av certifikatstrukturen med nx_secure_x509_certificate_initialize) eller som en utfärdare som en del av en certifikatkedja som tillhandahålls till fjärrvärden under TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-336">This certificate may used by the TLS stack to identify the device during the TLS handshake (if it was marked as an identity certificate during initialization of the certificate structure using nx_secure_x509_certificate_initialize), or as an issuer as part of a certificate chain provided to the remote host during the TLS handshake.</span></span>

<span data-ttu-id="ee5c6-337">Om flera lokala certifikat med samma eget namn behövs kan certifikat läggas till med hjälp *nx_secure_tls_server_certificate_add* tjänsten (se varningen nedan).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-337">If multiple local certificates with the same Common Name are needed, certificates may be added using the *nx_secure_tls_server_certificate_add* service (see warning below).</span></span>

<span data-ttu-id="ee5c6-338">Ett certifikat krävs **för** TLS-serverläge.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-338">A certificate is **required** for TLS Server mode.</span></span>

<span data-ttu-id="ee5c6-339">Ett certifikat är *valfritt* för TLS-klientläge.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-339">A certificate is *optional* for TLS Client mode.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee5c6-340">*Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_server_certificate_add. API:et för servercertifikat använder en unik numerisk identifierare för varje certifikat och nx_secure_tls_local_certificate_add index baserat på X.509-namnet. De lokala certifikattjänsterna är ett praktiskt alternativ till den numeriska identifieraren för program som endast använder ett enda identitetscertifikat – med hjälp av eget namn behöver programmet inte hålla reda på numeriska identifierare.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-340">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-341">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-341">Parameters</span></span>

- <span data-ttu-id="ee5c6-342">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-342">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-343">**certificate_ptr** Pekare till en initierad TLS-certifikatinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-343">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-344">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-344">Return Values</span></span>

- <span data-ttu-id="ee5c6-345">**NX_SUCCESS** (0x00) Lyckad tillägg av certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="ee5c6-346">**NX_INVALID_PARAMETERS** (0x4D) Försökte lägga till ett ogiltigt eller duplicerat certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-346">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid or duplicate certificate.</span></span>
- <span data-ttu-id="ee5c6-347">**NX_PTR_ERROR** (0x07) Ogiltig TLS-session eller certifikat pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-347">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-348">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-348">Allowed From</span></span>

<span data-ttu-id="ee5c6-349">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-350">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-350">Example</span></span>

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-351">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-351">See Also</span></span>

- <span data-ttu-id="ee5c6-352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-355">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ee5c6-355">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="ee5c6-356">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-356">nx_secure_tls_local_certificate_find</span></span>

## <a name="nx_secure_tls_local_certificate_find"></a><span data-ttu-id="ee5c6-357">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-357">nx_secure_tls_local_certificate_find</span></span>

<span data-ttu-id="ee5c6-358">Hitta ett lokalt certifikat i en NetX Secure TLS-session efter eget namn</span><span class="sxs-lookup"><span data-stu-id="ee5c6-358">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-359">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-359">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a><span data-ttu-id="ee5c6-360">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-360">Description</span></span>

<span data-ttu-id="ee5c6-361">Den här tjänsten hittar ett certifikat i det lokala enhetscertifikatarkivet för en TLS-session och returnerar en pekare till NX_SECURE_X509_CERT strukturen i arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-361">This service finds a certificate in the local device certificate store of a TLS session and returns a pointer to the NX_SECURE_X509_CERT structure in the store.</span></span> <span data-ttu-id="ee5c6-362">Parametern common_name och dess längd (name_length) används för att identifiera certifikatet i arkivet genom att matcha certifikatets X.509-ämnesnamnfält.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-362">The common_name parameter and it's length (name_length) are used to identify the certificate in the store by matching the certificate's X.509 Subject Common Name field.</span></span>

<span data-ttu-id="ee5c6-363">Om det finns fler än ett certifikat med samma eget namn returneras bara det första certifikatet – använd *nx_secure_tls_server_certificate_find* stället.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-363">If more than one certificate with the same Common Name is present, only the first one will be returned – use *nx_secure_tls_server_certificate_find* instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee5c6-364">*Det här API:et ska inte användas med samma TLS-session när du använder nx_secure_tls_server_certificate_add. Servercertifikat-API:et använder en unik numerisk identifierare för varje certifikat och nx_secure_tls_local_certificate_add index baserat på X.509-namnet. De lokala certifikattjänsterna är ett praktiskt alternativ till den numeriska identifieraren för program som endast använder ett enda identitetscertifikat – med hjälp av eget namn behöver programmet inte hålla reda på numeriska identifierare.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-364">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-365">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-365">Parameters</span></span>

- <span data-ttu-id="ee5c6-366">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-366">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-367">**certifikat** Returnera pekare till matchat certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-367">**certificate** Return Pointer to matched certificate.</span></span>
- <span data-ttu-id="ee5c6-368">**common_name** Gemensam namnsträng som ska matchas (DNS-namn).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-368">**common_name** Common Name string to match (DNS name).</span></span>
- <span data-ttu-id="ee5c6-369">**name_length** Längden på common_name strängdata.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-369">**name_length** Length of common_name string data.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-370">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-370">Return Values</span></span>

- <span data-ttu-id="ee5c6-371">**NX_SUCCESS** (0x00) Certifikatet hittades och pekaren returnerades i parametern "certifikat".</span><span class="sxs-lookup"><span data-stu-id="ee5c6-371">**NX_SUCCESS** (0x00) Certificate was found and pointer returned in "certificate" parameter.</span></span>
- <span data-ttu-id="ee5c6-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Inget certifikat med det angivna gemensamma namnet hittades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate with the supplied Common Name was found.</span></span>
- <span data-ttu-id="ee5c6-373">**NX_PTR_ERROR** (0x07) Ogiltig TLS-session, certifikat pekare eller namnsträng.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-373">**NX_PTR_ERROR** (0x07) Invalid TLS session, certificate pointer, or common name string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-374">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-374">Allowed From</span></span>

<span data-ttu-id="ee5c6-375">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-376">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-376">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-377">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-377">See Also</span></span>

- <span data-ttu-id="ee5c6-378">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-378">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-379">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-379">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-380">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-380">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-381">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ee5c6-381">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="ee5c6-382">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-382">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_local_certificate_remove"></a><span data-ttu-id="ee5c6-383">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ee5c6-383">nx_secure_tls_local_certificate_remove</span></span>

<span data-ttu-id="ee5c6-384">Ta bort lokalt certifikat från NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-384">Remove local certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-385">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-385">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a><span data-ttu-id="ee5c6-386">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-386">Description</span></span>

<span data-ttu-id="ee5c6-387">Den här tjänsten tar bort en lokal certifikatinstans från en TLS-session som är nyckelad i fältet Eget namn i certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-387">This service removes a local certificate instance from a TLS session, keyed on the Common Name field in the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee5c6-388">*Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_server_certificate_add. API:et för servercertifikat använder en unik numerisk identifierare för varje certifikat och nx_secure_tls_local_certificate_add index baserat på X.509-namnet. De lokala certifikattjänsterna är ett praktiskt alternativ till den numeriska identifieraren för program som endast använder ett enda identitetscertifikat – med hjälp av eget namn behöver programmet inte hålla reda på numeriska identifierare.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-388">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-389">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-389">Parameters</span></span>

- <span data-ttu-id="ee5c6-390">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-390">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-391">**common_name** Värdet för Eget namn för certifikatet som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-391">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="ee5c6-392">**common_name_length** Längden på strängen Eget namn.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-392">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-393">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-393">Return Values</span></span>

- <span data-ttu-id="ee5c6-394">**NX_SUCCESS** (0x00) Lyckad tillägg av certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-394">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="ee5c6-395">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-395">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="ee5c6-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119)-certifikatet hittades inte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-397">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-397">Allowed From</span></span>

<span data-ttu-id="ee5c6-398">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-399">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-399">Example</span></span>

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-400">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-400">See Also</span></span>

- <span data-ttu-id="ee5c6-401">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-401">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-402">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-402">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-403">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-403">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-404">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-404">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_metadata_size_calculate"></a><span data-ttu-id="ee5c6-405">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-405">nx_secure_tls_metadata_size_calculate</span></span>

<span data-ttu-id="ee5c6-406">Beräkna storleken på kryptografiska metadata för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-406">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-407">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-407">Prototype</span></span>

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a><span data-ttu-id="ee5c6-408">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-408">Description</span></span>

<span data-ttu-id="ee5c6-409">Den här tjänsten beräknar och returnerar storleken på de kryptografiska metadata som behövs för en viss TLS-session och TLS-kryptografitabell (se avsnittet "Initiera TLS med kryptografiska metoder" för mer information om den kryptografiska chiffertabellen).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-409">This service calculates and returns the size of the cryptographic metadata needed for a particular TLS session and TLS cryptography table (see the section "Initializing TLS with Cryptographic Methods" for more information on the cryptographic cipher table).</span></span>

<span data-ttu-id="ee5c6-410">Den här tjänsten ska anropas med önskad kryptografitabell för att beräkna storleken på metadatabufferten som skickas till nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-410">This service should be called with the desired cryptographic table to calculate the size of the metadata buffer passed into nx_secure_tls_session_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-411">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-411">Parameters</span></span>

- <span data-ttu-id="ee5c6-412">**crypto_table** Pekare till en komplett NetX Secure TLS-kryptografitabell.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-412">**crypto_table** Pointer to a complete NetX Secure TLS cryptography table.</span></span>
- <span data-ttu-id="ee5c6-413">**metadata_size** Utdata från storleksberäkningen i byte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-413">**metadata_size** The output of the size calculation in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-414">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-414">Return Values</span></span>

- <span data-ttu-id="ee5c6-415">**NX_SUCCESS** (0x00) Lyckad beräkning av metadatastorlek.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-415">**NX_SUCCESS** (0x00) Successful calculation of metadata size.</span></span>
- <span data-ttu-id="ee5c6-416">**NX_PTR_ERROR** (0x07) Ogiltig kryptografitabell eller pekare för returstorlek.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-416">**NX_PTR_ERROR** (0x07) Invalid crypto table or return size pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-417">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-417">Allowed From</span></span>

<span data-ttu-id="ee5c6-418">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-418">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-419">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-419">Example</span></span>

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-420">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-420">See Also</span></span>

- <span data-ttu-id="ee5c6-421">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-421">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_packet_allocate"></a><span data-ttu-id="ee5c6-422">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-422">nx_secure_tls_packet_allocate</span></span>

<span data-ttu-id="ee5c6-423">Allokera ett paket för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-423">Allocate a packet for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-424">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-424">Prototype</span></span>

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee5c6-425">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-425">Description</span></span>

<span data-ttu-id="ee5c6-426">Den här tjänsten allokerar NX_PACKET för den angivna aktiva TLS-sessionen från den angivna NX_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-426">This service allocates an NX_PACKET for the specified active TLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="ee5c6-427">Den här tjänsten ska anropas av programmet för att allokera datapaket som ska skickas via en TLS-anslutning.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-427">This service should be called by the application to allocate data packets to be sent over a TLS connection.</span></span> <span data-ttu-id="ee5c6-428">TLS-sessionen måste initieras innan den här tjänsten anropas.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-428">The TLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="ee5c6-429">Det allokerade paketet initieras korrekt så att TLS-sidhuvud- och sidfotsdata kan läggas till när paketdata har fyllts i.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-429">The allocated packet is properly initialized so that TLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="ee5c6-430">Beteendet är i övrigt identiskt *med nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-430">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-431">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-431">Parameters</span></span>

- <span data-ttu-id="ee5c6-432">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-432">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-433">**pool_ptr** Pekare till NX_PACKET_POOL som paketet ska allokeras från.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-433">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="ee5c6-434">**packet_ptr** Utdata pekare till det nyligen allokerade paketet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-434">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="ee5c6-435">**wait_option** Indragningsalternativ för paketallokering.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-435">**wait_option** Suspension option for packet allocation.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-436">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-436">Return Values</span></span>

- <span data-ttu-id="ee5c6-437">**NX_SUCCESS** (0x00) Lyckat paket allokeras.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-437">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="ee5c6-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underliggande paketallokering misslyckades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="ee5c6-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Den angivna TLS-sessionen initierades inte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-440">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-440">Allowed From</span></span>

<span data-ttu-id="ee5c6-441">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-442">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-442">Example</span></span>

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-443">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-443">See Also</span></span>

- <span data-ttu-id="ee5c6-444">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-444">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="ee5c6-445">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-445">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-446">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-446">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-447">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-447">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-448">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ee5c6-448">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="ee5c6-449">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-449">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="ee5c6-450">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-450">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="ee5c6-451">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="ee5c6-451">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="ee5c6-452">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-452">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_psk_add"></a><span data-ttu-id="ee5c6-453">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-453">nx_secure_tls_psk_add</span></span>

<span data-ttu-id="ee5c6-454">Lägga till en i förväg delad nyckel i en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-454">Add a Pre-Shared Key to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-455">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-455">Prototype</span></span>

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="ee5c6-456">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-456">Description</span></span>

<span data-ttu-id="ee5c6-457">Den här tjänsten lägger till en I förväg delad nyckel (PSK), dess identitetssträng och en identitetstips till ett TLS-sessionskontrollblock.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-457">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block.</span></span> <span data-ttu-id="ee5c6-458">PSK används i stället för ett digitalt certifikat när PSK-chiffer har aktiverats och används.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-458">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-459">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-459">Parameters</span></span>

- <span data-ttu-id="ee5c6-460">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-460">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-461">**pre_shared_key** Det faktiska PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-461">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="ee5c6-462">**psk_length** Längden på PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-462">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="ee5c6-463">**psk_identity** En sträng som används för att identifiera det här PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-463">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="ee5c6-464">**identity_length** Längden på PSK-identiteten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-464">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="ee5c6-465">**tips** En sträng som används för att ange vilken grupp av PSK:er som ska väljas på en TLS-server.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-465">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="ee5c6-466">**hint_length** Längden på tipssträngen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-466">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-467">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-467">Return Values</span></span>

- <span data-ttu-id="ee5c6-468">**NX_SUCCESS** (0x00) Lyckad addition av PSK.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-468">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="ee5c6-469">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-469">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="ee5c6-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Det går inte att lägga till ytterligare en PSK.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125)  Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-471">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-471">Allowed From</span></span>

<span data-ttu-id="ee5c6-472">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-473">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-473">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-474">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-474">See Also</span></span>

- <span data-ttu-id="ee5c6-475">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-475">nx_secure_tls_client_psk_set</span></span>
- <span data-ttu-id="ee5c6-476">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-476">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-477">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-477">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-478">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-478">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-479">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-479">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_remote_certificate_allocate"></a><span data-ttu-id="ee5c6-480">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-480">nx_secure_tls_remote_certificate_allocate</span></span>

<span data-ttu-id="ee5c6-481">Allokera utrymme för certifikatet som tillhandahålls av en fjärransluten TLS-värd</span><span class="sxs-lookup"><span data-stu-id="ee5c6-481">Allocate space for the certificate provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-482">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-482">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a><span data-ttu-id="ee5c6-483">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-483">Description</span></span>

<span data-ttu-id="ee5c6-484">Den här tjänsten lägger till en instans NX_SECURE_X509_CERT en oiniterad NX_SECURE_X509_CERT struktur till en TLS-session för att allokera utrymme för certifikat som tillhandahålls av en fjärrvärd under en TLS-session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-484">This service adds an uninitialized NX_SECURE_X509_CERT structure instance to a TLS session for the purpose of allocating space for certificates provided by a remote host during a TLS session.</span></span> <span data-ttu-id="ee5c6-485">Fjärrcertifikatdata parsas av NetX Secure TLS och den informationen används för att fylla i den certifikatstrukturinstans som tillhandahålls till den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-485">The remote certificate data is parsed by NetX Secure TLS and that information is used to populate the certificate structure instance provided to this function.</span></span> <span data-ttu-id="ee5c6-486">Certifikat som läggs till på det här sättet placeras i en länkad lista.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-486">Certificates added in this manner are placed in a linked list.</span></span>

<span data-ttu-id="ee5c6-487">Om det förväntas att fjärrvärden kommer att tillhandahålla flera certifikat ska den här funktionen anropas upprepade gånger för att allokera utrymme för alla certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-487">If it is expected that the remote host will provide multiple certificates, this function should be called repeatedly to allocate space for all certificates.</span></span> <span data-ttu-id="ee5c6-488">De ytterligare certifikaten läggs till i slutet av den länkade listan med certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-488">The additional certificates are added to the end of the certificate linked list.</span></span>

<span data-ttu-id="ee5c6-489">Om ett fjärrcertifikat inte allokeras misslyckas TLS-klientläget under TLS-handskakningen, såvida inte PSK-chiffer (Pre-Shared Key) används.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-489">Failure to allocate a remote certificate will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="ee5c6-490">Den *raw_certificate_buffer pekar* på allokerat utrymme för att lagra det inkommande fjärrcertifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-490">The *raw_certificate_buffer* parameter points to space allocated to store the incoming remote certificate.</span></span> <span data-ttu-id="ee5c6-491">Vanliga certifikat med RSA-nycklar på 2 048 bitar som använder SHA-256 för signaturer är i intervallet 1 000–2 000 byte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-491">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="ee5c6-492">Bufferten bör vara tillräckligt stor för att minst innehålla den storleken, men beroende på fjärrvärdcertifikaten kan vara betydligt mindre eller större.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-492">The buffer should be large enough to at least hold that size, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="ee5c6-493">Observera att om bufferten är för liten för att innehålla det inkommande certifikatet, slutar TLS-handskakningen med ett fel.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-493">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

<span data-ttu-id="ee5c6-494">I TLS-serverläge behövs endast en fjärrcertifikatsallokering om klientcertifikatautentisering är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-494">For TLS Server mode, a remote certificate allocation is needed only if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-495">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-495">Parameters</span></span>

- <span data-ttu-id="ee5c6-496">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-496">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-497">**certificate_ptr** Pekare till en oiniterad X.509-certifikatinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-497">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="ee5c6-498">**raw_certificate_buffer** Pekare till en buffert för att lagra det oparsade certifikat som tagits emot från fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-498">**raw_certificate_buffer** Pointer to a buffer to hold the un-parsed certificate received from the remote host.</span></span>
- <span data-ttu-id="ee5c6-499">**raw_buffer_size** Storleken på råcertifikatbufferten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-499">**raw_buffer_size** Size of the raw certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-500">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-500">Return Values</span></span>

- <span data-ttu-id="ee5c6-501">**NX_SUCCESS** (0x00) Lyckad allokering av certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-501">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="ee5c6-502">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-502">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="ee5c6-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) Den angivna bufferten var för liten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="ee5c6-504">**NX_INVALID_PARAMETERS** (0x4D) Försökte lägga till ett ogiltigt certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-504">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-505">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-505">Allowed From</span></span>

<span data-ttu-id="ee5c6-506">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-507">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-507">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-508">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-508">See Also</span></span>

- <span data-ttu-id="ee5c6-509">nx_secure_x509_certificate_initialize,</span><span class="sxs-lookup"><span data-stu-id="ee5c6-509">nx_secure_x509_certificate_initialize,</span></span>
- <span data-ttu-id="ee5c6-510">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-510">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a><span data-ttu-id="ee5c6-511">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-511">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

<span data-ttu-id="ee5c6-512">Allokera utrymme för alla certifikat som tillhandahålls av en fjärransluten TLS-värd</span><span class="sxs-lookup"><span data-stu-id="ee5c6-512">Allocate space for all certificates provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-513">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-513">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="ee5c6-514">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-514">Description</span></span>

<span data-ttu-id="ee5c6-515">Den här tjänsten allokerar utrymme för att bearbeta inkommande certifikatkedjor från fjärrservervärdar för att utföra X.509-autentisering och verifiering i en TLS-klientinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-515">This service allocates space to process incoming certificate chains from remote server hosts in order to perform X.509 authentication and verification in a TLS Client instance.</span></span> <span data-ttu-id="ee5c6-516">För TLS-serverläge behövs endast fjärrcertifikatallokering om X.509-klientcertifikatautentisering är aktiverat – för TLS-serverinstanser ska *tjänsttilldelningen nx_secure_tls_session_x509_client_verify_configure* användas i stället.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-516">For TLS Server mode, remote certificate allocation is needed only if client X.509 certificate authentication is enabled – for TLS Server instances the service *nx_secure_tls_session_x509_client_verify_configure* should be used instead.</span></span>

<span data-ttu-id="ee5c6-517">Om du inte allokerar fjärrcertifikat misslyckas TLS-klientläget under TLS-handskakningen, såvida inte PSK-chiffer (Pre-Shared Key) används.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-517">Failure to allocate remote certificates will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="ee5c6-518">Parametern *certificate_buffer* pekar på allokerat utrymme för att lagra inkommande fjärrcertifikat och de kontrollblock som behövs för dessa certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-518">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="ee5c6-519">Bufferten divideras med antalet certifikat *(* certs_number ) med en lika stor del som ges till varje certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-519">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="ee5c6-520">Parametern *buffer_size*  anger storleken på bufferten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-520">The *buffer_size*  parameter indicates the size of the buffer.</span></span> <span data-ttu-id="ee5c6-521">Utrymmet som behövs finns med följande formel:</span><span class="sxs-lookup"><span data-stu-id="ee5c6-521">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="ee5c6-522">Vanliga certifikat med RSA-nycklar på 2 048 bitar som använder SHA-256 för signaturer är i intervallet 1 000–2 000 byte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-522">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="ee5c6-523">Bufferten bör vara tillräckligt stor för att minst innehålla den storleken för varje certifikat, men beroende på fjärrvärdcertifikaten kan vara betydligt mindre eller större.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-523">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="ee5c6-524">Observera att om bufferten är för liten för att innehålla det inkommande certifikatet slutar TLS-handskakningen med ett fel.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-524">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-525">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-525">Parameters</span></span>

- <span data-ttu-id="ee5c6-526">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-526">**session_ptr** Pointer to a previously created TLS Session  instance.</span></span>
- <span data-ttu-id="ee5c6-527">**certs_number** Antal certifikat som ska allokeras från den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-527">**certs_number** Number of certificates to allocate from the  provided buffer.</span></span>
- <span data-ttu-id="ee5c6-528">**certificate_buffer** Pekare till en buffert för att lagra certifikat som tagits emot från en fjärrvärd.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-528">**certificate_buffer** Pointer to a buffer to hold certificates received  from a remote host.</span></span>
- <span data-ttu-id="ee5c6-529">**buffer_size** Certifikatbuffertens storlek.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-529">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-530">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-530">Return Values</span></span>

- <span data-ttu-id="ee5c6-531">**NX_SUCCESS** (0x00) Lyckad allokering av certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-531">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="ee5c6-532">**NX_PTR_ERROR** (0x07) Ogiltig TLS-session eller buffertpekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-532">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="ee5c6-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) Den angivna bufferten var för liten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="ee5c6-534">**NX_INVALID_PARAMETERS** (0x4D) Bufferten var för liten för att innehålla det önskade antalet certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-534">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold  the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-535">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-535">Allowed From</span></span>

<span data-ttu-id="ee5c6-536">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-536">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-537">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-537">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-538">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-538">See Also</span></span>

- <span data-ttu-id="ee5c6-539">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-539">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-540">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-540">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_free_all"></a><span data-ttu-id="ee5c6-541">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="ee5c6-541">nx_secure_tls_remote_certificate_free_all</span></span>

<span data-ttu-id="ee5c6-542">Ledigt utrymme allokerat för inkommande certifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-542">Free space allocated for incoming certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-543">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-543">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="ee5c6-544">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-544">Description</span></span>

<span data-ttu-id="ee5c6-545">Den här tjänsten används för att frigöra alla certifikatbuffertar som allokerats till en viss TLS-session genom nx_secure_tls_remote_certificate_allocated genom att returnera dem till sessionens lediga certifikatutrymme.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-545">This service is used to free all of the certificate buffers allocated to a particular TLS Session by nx_secure_tls_remote_certificate_allocated by returning them to that session's free certificate space.</span></span> <span data-ttu-id="ee5c6-546">Detta kan vara nödvändigt om ett program återanvänder ett TLS-sessionsobjekt utan att ta bort det och återskapa det med nx_secure_tls_session_delete och nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-546">This may be necessary if an application reuses a TLS session object without deleting it and recreating it with nx_secure_tls_session_delete and nx_secure_tls_session_create.</span></span>

<span data-ttu-id="ee5c6-547">Observera att fjärrcertifikatutrymmet återställs automatiskt när TLS-sessionen återställs som i nx_secure_tls_session_end så att de flesta program inte behöver anropa den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-547">Note that the remote certificate space is recovered automatically when the TLS session is reset as happens in nx_secure_tls_session_end so most applications should not need to call this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-548">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-548">Parameters</span></span>

- <span data-ttu-id="ee5c6-549">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-549">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-550">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-550">Return Values</span></span>

- <span data-ttu-id="ee5c6-551">**NX_SUCCESS** (0x00) Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-551">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="ee5c6-552">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-552">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="ee5c6-553">**NX_INVALID_PARAMETERS** (0x4D) Internt fel – certifikatarkivet är sannolikt skadat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-553">**NX_INVALID_PARAMETERS** (0x4D) Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-554">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-554">Allowed From</span></span>

<span data-ttu-id="ee5c6-555">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-555">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-556">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-556">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-557">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-557">See Also</span></span>

- <span data-ttu-id="ee5c6-558">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-558">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-559">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-559">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-560">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-560">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-561">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="ee5c6-561">nx_secure_tls_session_end</span></span>

## <a name="nx_secure_tls_server_certificate_add"></a><span data-ttu-id="ee5c6-562">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-562">nx_secure_tls_server_certificate_add</span></span>

<span data-ttu-id="ee5c6-563">Lägga till ett certifikat specifikt för TLS-servrar med hjälp av en numerisk identifierare</span><span class="sxs-lookup"><span data-stu-id="ee5c6-563">Add a certificate specifically for TLS servers using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-564">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-564">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="ee5c6-565">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-565">Description</span></span>

<span data-ttu-id="ee5c6-566">Den här tjänsten används för att lägga till ett certifikat i en TLS-sessions lokala arkiv (se nx_secure_tls_local_certificate_add) med hjälp av en numerisk identifierare i stället för att indexera arkivet med hjälp av X.509-ämne (eget namn) i certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-566">This service is used to add a certificate to a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span> <span data-ttu-id="ee5c6-567">Den numeriska identifieraren är separat från certifikatet och tillåter att flera certifikat läggs till som identitetscertifikat på en TLS-server, samt att flera certifikat med samma eget namn kan läggas till i samma lokala TLS-sessionsarkiv.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-567">The numeric identifier is separate from the certificate and allows multiple certificates to be added as identity certificates to a TLS server, as well as allowing multiple certificates with the same Common Name to be added to the same TLS session local store.</span></span> <span data-ttu-id="ee5c6-568">Samma tjänst kan användas för klientcertifikat, men det är ovanligt att en TLS-klient har flera identitetscertifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-568">This same service can be used for client certificates, but it is rare for a TLS client to have multiple identity certificates.</span></span>

<span data-ttu-id="ee5c6-569">Parametern cert_id är ett positivt heltal utan noll som tilldelats av programmet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-569">The cert_id parameter is a non-zero positive integer assigned by the application.</span></span> <span data-ttu-id="ee5c6-570">Det faktiska värdet spelar ingen roll (förutom noll) men det måste vara unikt i arkivet för den angivna TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-570">The actual value does not matter (other than zero) but it must be unique in the store for the provided TLS session.</span></span> <span data-ttu-id="ee5c6-571">Värdet cert_id kan användas för att hitta och ta bort certifikat från det lokala arkivet med hjälp nx_secure_tls_server_certificate_find och nx_secure_tls_server_certificate_remove, respektive.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-571">The cert_id value can be used to find and remove certificates from the local store using nx_secure_tls_server_certificate_find and nx_secure_tls_server_certificate_remove, respectively.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee5c6-572">*Det här API:et ska inte användas med samma TLS-session när du använder nx_secure_tls_local_certificate_add. API:nx_secure_tls_server_certificate_add använder en unik numerisk identifierare för varje certifikat och lokala certifikattjänstindex baserat på X.509-namnet. Servercertifikattjänsterna tillåter att flera certifikat med delade data (särskilt eget namn) finns i samma lokala arkiv – detta är användbart för en server med flera identiteter.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-572">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-573">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-573">Parameters</span></span>

- <span data-ttu-id="ee5c6-574">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-574">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-575">**certifikat** Pekare till en tidigare initierad X.509-certifikatinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-575">**certificate** Pointer to a previously initialized X.509 certificate instance.</span></span>
- <span data-ttu-id="ee5c6-576">**cert_id** Positivt, icke-noll, relativt unikt certifikat-ID-nummer.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-576">**cert_id** Positive, non-zero, relatively unique certificate ID number.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-577">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-577">Return Values</span></span>

- <span data-ttu-id="ee5c6-578">**NX_SUCCESS** (0x00)Lyckad åtgärd.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-578">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="ee5c6-579">**NX_PTR_ERROR** (0x07) Ogiltig TLS-session eller certifikat pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-579">**NX_PTR_ERROR** (0x07) Invalid TLS session orcertificate pointer.</span></span>
- <span data-ttu-id="ee5c6-580">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) Det angivna certifikat-ID:t hade ett ogiltigt värde (sannolikt 0).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-580">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) The provided certificate ID had An invalid value (likely 0).</span></span>
- <span data-ttu-id="ee5c6-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) Det angivna certifikat-ID:t fanns redan i det lokala arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) The provided certificate ID was already present in the local store.</span></span>
- <span data-ttu-id="ee5c6-582">**NX_INVALID_PARAMETERS(0x4D)** Internt fel – certifikatarkivet är sannolikt skadat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-582">**NX_INVALID_PARAMETERS(0x4D)** Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-583">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-583">Allowed From</span></span>

<span data-ttu-id="ee5c6-584">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-585">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-585">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-586">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-586">See Also</span></span>

- <span data-ttu-id="ee5c6-587">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-587">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-588">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-588">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="ee5c6-589">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-589">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="ee5c6-590">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-590">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="ee5c6-591">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ee5c6-591">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_server_certificate_find"></a><span data-ttu-id="ee5c6-592">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-592">nx_secure_tls_server_certificate_find</span></span>

<span data-ttu-id="ee5c6-593">Hitta ett certifikat med hjälp av en numerisk identifierare</span><span class="sxs-lookup"><span data-stu-id="ee5c6-593">Find a certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-594">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-594">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="ee5c6-595">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-595">Description</span></span>

<span data-ttu-id="ee5c6-596">Den här tjänsten används för att hitta ett certifikat i en TLS-sessions lokala arkiv (se nx_secure_tls_local_certificate_add) med hjälp av en numerisk identifierare i stället för att indexera arkivet med hjälp av X.509-ämne (eget namn) i certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-596">This service is used to find a certificate in a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="ee5c6-597">Parametern cert_id är ett positivt heltal som inte är noll och tilldelas av programmet när certifikatet läggs till i det lokala TLS-sessionsarkivet med hjälp av nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-597">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee5c6-598">*Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_local_certificate_add. I nx_secure_tls_server_certificate_add-API:et används en unik numerisk identifierare för varje certifikat och lokala certifikattjänstindex baserat på X.509-namnet. Servercertifikattjänsterna tillåter att flera certifikat med delade data (särskilt eget namn) finns i samma lokala arkiv – detta är användbart för en server med flera identiteter.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-598">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-599">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-599">Parameters</span></span>

- <span data-ttu-id="ee5c6-600">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-600">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-601">**certifikat** Pekare till en X.509-certifikat pekare för att returnera en referens till det hittade certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-601">**certificate** Pointer to an X.509 certificate pointer to return a reference to the found certificate.</span></span>
- <span data-ttu-id="ee5c6-602">**cert_id** Värde för positivt certifikat-ID som inte är noll.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-602">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-603">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-603">Return Values</span></span>

- <span data-ttu-id="ee5c6-604">**NX_SUCCESS** (0x00)Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-604">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="ee5c6-605">**NX_PTR_ERROR** (0x07) Ogiltig TLS-session eller certifikat pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-605">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>
- <span data-ttu-id="ee5c6-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det angivna certifikat-ID:t matchade inte något i det lokala arkivet för den angivna TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-607">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-607">Allowed From</span></span>

<span data-ttu-id="ee5c6-608">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-608">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-609">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-609">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-610">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-610">See Also</span></span>

- <span data-ttu-id="ee5c6-611">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-611">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-612">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-612">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="ee5c6-613">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-613">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="ee5c6-614">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-614">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="ee5c6-615">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ee5c6-615">nx_secure_tls_server_certificate_remove</span></span>

##  <a name="nx_secure_tls_server_certificate_remove"></a><span data-ttu-id="ee5c6-616">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ee5c6-616">nx_secure_tls_server_certificate_remove</span></span>

<span data-ttu-id="ee5c6-617">Ta bort ett lokalt servercertifikat med hjälp av en numerisk identifierare</span><span class="sxs-lookup"><span data-stu-id="ee5c6-617">Remove a local server certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-618">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-618">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="ee5c6-619">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-619">Description</span></span>

<span data-ttu-id="ee5c6-620">Den här tjänsten används för att ta bort ett certifikat från en TLS-sessions lokala arkiv (se nx_secure_tls_local_certificate_add) med hjälp av en numerisk identifierare i stället för att indexera arkivet med hjälp av X.509-certifikatutfärdaren (eget namn) i certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-620">This service is used to remove a certificate from a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="ee5c6-621">Parametern cert_id är ett positivt heltal som inte är noll och tilldelas av programmet när certifikatet läggs till i det lokala TLS-sessionsarkivet med hjälp av nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-621">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-622">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-622">Parameters</span></span>

- <span data-ttu-id="ee5c6-623">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-623">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-624">**cert_id** Värde för positivt certifikat-ID som inte är noll.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-624">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-625">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-625">Return Values</span></span>

- <span data-ttu-id="ee5c6-626">**NX_SUCCESS** (0x00)Lyckad åtgärd.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-626">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="ee5c6-627">**NX_PTR_ERROR** (0x07) Ogiltig TLS-session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-627">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>
- <span data-ttu-id="ee5c6-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det angivna certifikat-ID:t matchade inte något i det lokala arkivet för den angivna TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-629">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-629">Allowed From</span></span>

<span data-ttu-id="ee5c6-630">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-630">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-631">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-631">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-632">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-632">See Also</span></span>

- <span data-ttu-id="ee5c6-633">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-633">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-634">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-634">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="ee5c6-635">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-635">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="ee5c6-636">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-636">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="ee5c6-637">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-637">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_alert_value_get"></a><span data-ttu-id="ee5c6-638">nx_secure_tls_session_alert_value_get</span><span class="sxs-lookup"><span data-stu-id="ee5c6-638">nx_secure_tls_session_alert_value_get</span></span>

<span data-ttu-id="ee5c6-639">Hämta TLS-aviseringsvärdet och nivån som skickas av fjärrvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-639">Get the TLS alert value and level sent by the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-640">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-640">Prototype</span></span>

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a><span data-ttu-id="ee5c6-641">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-641">Description</span></span>

<span data-ttu-id="ee5c6-642">Den här tjänsten används för att hämta TLS-aviseringsnivå och -värde när fjärrvärden skickar en avisering som svar på ett problem eller fel.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-642">This service is used to retrieve the TLS alert level and value when the remote host sends an alert in response to some problem or error.</span></span>

<span data-ttu-id="ee5c6-643">Värdena för parametrarna alert_level och alert_value är bara giltiga om den här funktionen anropas omedelbart efter ett TLS API-anrop som returnerade statusen NX_SECURE_TLS_ALERT_RECEIVED (0x114) som anger att en avisering togs emot från fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-643">The values of the alert_level and alert_value parameters are only valid if this function is called immediately following a TLS API call that returned a status of NX_SECURE_TLS_ALERT_RECEIVED (0x114) indicating that an alert was received from the remote host.</span></span>

<span data-ttu-id="ee5c6-644">Observera att om den lokala värdens TLS skickar en avisering är de returnerade felkoderna mycket mer beskrivande för det faktiska felet än själva TLS-aviseringen eftersom TLS-aviseringsvärden avsiktligt lämnas tvetydiga för att förhindra vissa typer av angrepp (till exempel ett utfyllnadsoraklet" eller liknande).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-644">Note that if the local host TLS sends an alert, the returned error codes are far more descriptive of the actual error than the TLS alert itself because TLS alert values are intentionally left ambiguous to prevent certain types of attack (such as a "padding oracle" attack or similar).</span></span>

<span data-ttu-id="ee5c6-645">Aviseringsnivån tar bara ett av två värden: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) eller NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-645">The alert level only takes one of two values: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) or NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span></span> <span data-ttu-id="ee5c6-646">I allmänhet ges endast CloseNotify-aviseringen (används för att ange ett lyckat slut på en TLS-session) en nivå av "Varning" även om vissa tilläggskonfigurationssituationer också kan betraktas som varningar.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-646">In general, only the CloseNotify Alert (used to indicate a successful end to a TLS session) will be given a level of "Warning" though some extension configuration situations may also be considered warnings.</span></span> <span data-ttu-id="ee5c6-647">De allra flesta aviseringar är "Allvarliga" som anger ett potentiellt säkerhetsfel och resulterar i omedelbar stängning av TLS-anslutningen (handskakning eller session).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-647">The vast majority of alerts will be "Fatal" indicating a potential security failure and resulting in immediate closure of the TLS connection (handshake or session).</span></span>

<span data-ttu-id="ee5c6-648">TLS-aviseringsvärdena definieras i TLS RFCs. Här är listan från RFC 5246 (TLSv1.2) som referens:</span><span class="sxs-lookup"><span data-stu-id="ee5c6-648">The TLS alert values are defined in the TLS RFCs, here is the list from RFC 5246 (TLSv1.2) for reference:</span></span>

| <span data-ttu-id="ee5c6-649">Aviseringsnamn</span><span class="sxs-lookup"><span data-stu-id="ee5c6-649">Alert Name</span></span>                     | <span data-ttu-id="ee5c6-650">Värde</span><span class="sxs-lookup"><span data-stu-id="ee5c6-650">Value</span></span> | <span data-ttu-id="ee5c6-651">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ee5c6-651">Description</span></span>                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ee5c6-652">close_notify</span><span class="sxs-lookup"><span data-stu-id="ee5c6-652">close_notify</span></span>                  | <span data-ttu-id="ee5c6-653">0</span><span class="sxs-lookup"><span data-stu-id="ee5c6-653">0</span></span>     | <span data-ttu-id="ee5c6-654">Inget fel, indikerar att sessionen har avslutas</span><span class="sxs-lookup"><span data-stu-id="ee5c6-654">No error, indicates successful session end</span></span>                                                                                                                   |
| <span data-ttu-id="ee5c6-655">unexpected_message</span><span class="sxs-lookup"><span data-stu-id="ee5c6-655">unexpected_message</span></span>            | <span data-ttu-id="ee5c6-656">10</span><span class="sxs-lookup"><span data-stu-id="ee5c6-656">10</span></span>    | <span data-ttu-id="ee5c6-657">TLS tog emot ett oväntat eller oväntad meddelande</span><span class="sxs-lookup"><span data-stu-id="ee5c6-657">TLS received an unexpected or out-of-order message</span></span>                                                                                                           |
| <span data-ttu-id="ee5c6-658">bad_record_mac</span><span class="sxs-lookup"><span data-stu-id="ee5c6-658">bad_record_mac</span></span>               | <span data-ttu-id="ee5c6-659">20</span><span class="sxs-lookup"><span data-stu-id="ee5c6-659">20</span></span>    | <span data-ttu-id="ee5c6-660">Dekryptering och/eller MAC-verifiering misslyckades</span><span class="sxs-lookup"><span data-stu-id="ee5c6-660">Decryption and/or MAC verification failed</span></span>                                                                                                                    |
| <span data-ttu-id="ee5c6-661">decryption_failed_RESERVED</span><span class="sxs-lookup"><span data-stu-id="ee5c6-661">decryption_failed_RESERVED</span></span>   | <span data-ttu-id="ee5c6-662">21</span><span class="sxs-lookup"><span data-stu-id="ee5c6-662">21</span></span>    | <span data-ttu-id="ee5c6-663">**INAKTUELL** Dekrypteringen misslyckades (inaktuell på grund av utfyllnad av orakelattacker)</span><span class="sxs-lookup"><span data-stu-id="ee5c6-663">**DEPRECATED** Decryption failed (deprecated due to padding oracle attacks)</span></span>                                                                                      |
| <span data-ttu-id="ee5c6-664">record_overflow</span><span class="sxs-lookup"><span data-stu-id="ee5c6-664">record_overflow</span></span>               | <span data-ttu-id="ee5c6-665">22</span><span class="sxs-lookup"><span data-stu-id="ee5c6-665">22</span></span>    | <span data-ttu-id="ee5c6-666">En post togs emot som är större än den maximala TLS-poststorleken</span><span class="sxs-lookup"><span data-stu-id="ee5c6-666">A record was received that is larger than the TLS maximum record size</span></span>                                                                                        |
| <span data-ttu-id="ee5c6-667">decompression_failure</span><span class="sxs-lookup"><span data-stu-id="ee5c6-667">decompression_failure</span></span>         | <span data-ttu-id="ee5c6-668">30</span><span class="sxs-lookup"><span data-stu-id="ee5c6-668">30</span></span>    | <span data-ttu-id="ee5c6-669">Ett problem inträffade vid komprimering/dekomprimering av en TLS-post</span><span class="sxs-lookup"><span data-stu-id="ee5c6-669">A problem was encountered in compression/decompression of a TLS record</span></span>                                                                                       |
| <span data-ttu-id="ee5c6-670">handshake_failure</span><span class="sxs-lookup"><span data-stu-id="ee5c6-670">handshake_failure</span></span>             | <span data-ttu-id="ee5c6-671">40</span><span class="sxs-lookup"><span data-stu-id="ee5c6-671">40</span></span>    | <span data-ttu-id="ee5c6-672">Det uppstod ett ospecificerat handskakningsfel som inte omfattas av en annan avisering</span><span class="sxs-lookup"><span data-stu-id="ee5c6-672">Some unspecified handshake error occurred that isn't covered by a different alert</span></span>                                                                            |
| <span data-ttu-id="ee5c6-673">no_certificate_RESERVED</span><span class="sxs-lookup"><span data-stu-id="ee5c6-673">no_certificate_RESERVED</span></span>      | <span data-ttu-id="ee5c6-674">41</span><span class="sxs-lookup"><span data-stu-id="ee5c6-674">41</span></span>    | <span data-ttu-id="ee5c6-675">**INAKTUELL I** TLS (endast SSL)</span><span class="sxs-lookup"><span data-stu-id="ee5c6-675">**DEPRECATED** in TLS (SSL only)</span></span>                                                                                                                                 |
| <span data-ttu-id="ee5c6-676">bad_certificate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-676">bad_certificate</span></span>               | <span data-ttu-id="ee5c6-677">42</span><span class="sxs-lookup"><span data-stu-id="ee5c6-677">42</span></span>    | <span data-ttu-id="ee5c6-678">Ett certifikat som togs emot innehöll ogiltig formatering eller signaturer</span><span class="sxs-lookup"><span data-stu-id="ee5c6-678">A certificate that was received contained invalid formatting or signatures</span></span>                                                                                   |
| <span data-ttu-id="ee5c6-679">unsupported_certificate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-679">unsupported_certificate</span></span>       | <span data-ttu-id="ee5c6-680">43</span><span class="sxs-lookup"><span data-stu-id="ee5c6-680">43</span></span>    | <span data-ttu-id="ee5c6-681">Ett certifikat togs emot som var av en ogiltig typ (t.ex. signeringscertifikat som användes för TLS-serverautentisering)</span><span class="sxs-lookup"><span data-stu-id="ee5c6-681">A certificate was received that was of an invalid type (e.g. signing-only certificate used for TLS server authentication)</span></span>                                    |
| <span data-ttu-id="ee5c6-682">certificate_revoked</span><span class="sxs-lookup"><span data-stu-id="ee5c6-682">certificate_revoked</span></span>           | <span data-ttu-id="ee5c6-683">44</span><span class="sxs-lookup"><span data-stu-id="ee5c6-683">44</span></span>    | <span data-ttu-id="ee5c6-684">Certifikatstatusen (som anges av en CRL eller OCSP) angavs som "återkallad"</span><span class="sxs-lookup"><span data-stu-id="ee5c6-684">The certificate status (as provided by a CRL or OCSP) was indicated as being "revoked"</span></span>                                                                       |
| <span data-ttu-id="ee5c6-685">certificate_expired</span><span class="sxs-lookup"><span data-stu-id="ee5c6-685">certificate_expired</span></span>           | <span data-ttu-id="ee5c6-686">45</span><span class="sxs-lookup"><span data-stu-id="ee5c6-686">45</span></span>    | <span data-ttu-id="ee5c6-687">Det mottagna certifikatet låg utanför det giltiga datumintervallet (antingen inte giltigt ännu eller har upphört att gälla)</span><span class="sxs-lookup"><span data-stu-id="ee5c6-687">The received certificate was outside it's valid date range (either not valid yet or expired)</span></span>                                                                 |
| <span data-ttu-id="ee5c6-688">certificate_unknown</span><span class="sxs-lookup"><span data-stu-id="ee5c6-688">certificate_unknown</span></span>           | <span data-ttu-id="ee5c6-689">46</span><span class="sxs-lookup"><span data-stu-id="ee5c6-689">46</span></span>    | <span data-ttu-id="ee5c6-690">Ett okänt certifikatproblem påträffades som inte omfattas av andra aviseringar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-690">Some unknown certificate issue was encountered that was not covered by other alerts</span></span>                                                                          |
| <span data-ttu-id="ee5c6-691">illegal_parameter</span><span class="sxs-lookup"><span data-stu-id="ee5c6-691">illegal_parameter</span></span>             | <span data-ttu-id="ee5c6-692">47</span><span class="sxs-lookup"><span data-stu-id="ee5c6-692">47</span></span>    | <span data-ttu-id="ee5c6-693">Vissa konfigurationer eller förhandlade värden i TLS-handskakningen var ogiltiga eller utanför intervallet</span><span class="sxs-lookup"><span data-stu-id="ee5c6-693">Some configuration or negotiated value in the TLS handshake was invalid or out of range</span></span>                                                                      |
| <span data-ttu-id="ee5c6-694">unknown_ca</span><span class="sxs-lookup"><span data-stu-id="ee5c6-694">unknown_ca</span></span>                    | <span data-ttu-id="ee5c6-695">48</span><span class="sxs-lookup"><span data-stu-id="ee5c6-695">48</span></span>    | <span data-ttu-id="ee5c6-696">Det mottagna identitetscertifikatet kunde inte spåras via en certifikatkedja till ett betrott rotcertifikatutfärdarcertifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-696">The received identity certificate could not be traced via a certificate chain to a trusted root CA certificate.</span></span>                                              |
| <span data-ttu-id="ee5c6-697">access_denied</span><span class="sxs-lookup"><span data-stu-id="ee5c6-697">access_denied</span></span>                 | <span data-ttu-id="ee5c6-698">49</span><span class="sxs-lookup"><span data-stu-id="ee5c6-698">49</span></span>    | <span data-ttu-id="ee5c6-699">Anger att ett giltigt certifikat togs emot men programåtkomstkontrollen angav att certifikatet var ogiltigt för de begärda resurserna.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-699">Indicates a valid certificate was received but application access control indicated that the certificate was invalid for the requested resources.</span></span>            |
| <span data-ttu-id="ee5c6-700">decode_error</span><span class="sxs-lookup"><span data-stu-id="ee5c6-700">decode_error</span></span>                  | <span data-ttu-id="ee5c6-701">50</span><span class="sxs-lookup"><span data-stu-id="ee5c6-701">50</span></span>    | <span data-ttu-id="ee5c6-702">Ett fält eller värde i ett TLS-huvud eller handskakningsmeddelande var utanför intervallet eller ogiltigt, vilket ledde till ett fel vid avkodning av en TLS-post.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-702">Some field or value in a TLS header or handshake message was out of range or invalid, leading to a failure in decoding of a TLS record.</span></span>                      |
| <span data-ttu-id="ee5c6-703">decrypt_error</span><span class="sxs-lookup"><span data-stu-id="ee5c6-703">decrypt_error</span></span>                 | <span data-ttu-id="ee5c6-704">51</span><span class="sxs-lookup"><span data-stu-id="ee5c6-704">51</span></span>    | <span data-ttu-id="ee5c6-705">Det gick inte att verifiera en signatur eller slutfört meddelande-hash under TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-705">A signature or Finished message hash during the TLS handshake could not be verified.</span></span>                                                                         |
| <span data-ttu-id="ee5c6-706">export_restriction_RESERVED</span><span class="sxs-lookup"><span data-stu-id="ee5c6-706">export_restriction_RESERVED</span></span>  | <span data-ttu-id="ee5c6-707">60</span><span class="sxs-lookup"><span data-stu-id="ee5c6-707">60</span></span>    | <span data-ttu-id="ee5c6-708">INAKTUELL I TLSv1.2</span><span class="sxs-lookup"><span data-stu-id="ee5c6-708">DEPRECATED in TLSv1.2</span></span>                                                                                                                                        |
| <span data-ttu-id="ee5c6-709">protocol_version</span><span class="sxs-lookup"><span data-stu-id="ee5c6-709">protocol_version</span></span>              | <span data-ttu-id="ee5c6-710">70</span><span class="sxs-lookup"><span data-stu-id="ee5c6-710">70</span></span>    | <span data-ttu-id="ee5c6-711">Den TLS-protokollversion som förhandlades under handskakningen känns igen men stöds inte (t.ex. TLSv1.0 visades men aktiverades inte).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-711">The TLS protocol version negotiated during the handshake is recognized but not supported (e.g. TLSv1.0 was presented but not enabled).</span></span>                       |
| <span data-ttu-id="ee5c6-712">insufficient_security</span><span class="sxs-lookup"><span data-stu-id="ee5c6-712">insufficient_security</span></span>         | <span data-ttu-id="ee5c6-713">71</span><span class="sxs-lookup"><span data-stu-id="ee5c6-713">71</span></span>    | <span data-ttu-id="ee5c6-714">Skickas när en handskakning misslyckas på grund av brist på säkra chiffer (t.ex. nyckelstorleken är för liten för programkraven)</span><span class="sxs-lookup"><span data-stu-id="ee5c6-714">Sent whenever a handshake fails due to a lack of secure ciphers (e.g. key size is too small for the application requirements)</span></span>                                |
| <span data-ttu-id="ee5c6-715">internal_error</span><span class="sxs-lookup"><span data-stu-id="ee5c6-715">internal_error</span></span>                | <span data-ttu-id="ee5c6-716">80</span><span class="sxs-lookup"><span data-stu-id="ee5c6-716">80</span></span>    | <span data-ttu-id="ee5c6-717">Vissa icke-TLS-fel (t.ex. problem med minnesallokering eller program) inträffade, vilket resulterade i en bruten TLS-session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-717">Some non-TLS error (e.g. memory allocation problems, application issues) occurred resulting in a broken TLS session.</span></span>                                         |
| <span data-ttu-id="ee5c6-718">user_canceled</span><span class="sxs-lookup"><span data-stu-id="ee5c6-718">user_canceled</span></span>                 | <span data-ttu-id="ee5c6-719">90</span><span class="sxs-lookup"><span data-stu-id="ee5c6-719">90</span></span>    | <span data-ttu-id="ee5c6-720">Returneras om TLS-sessionen avbryts av en användare eller ett program innan handskakningen är klar (liknar CloseNotify).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-720">Returned if the TLS session is cancelled by a user or application before the handshake is complete (similar to CloseNotify).</span></span>                                 |
| <span data-ttu-id="ee5c6-721">no_renegotiation</span><span class="sxs-lookup"><span data-stu-id="ee5c6-721">no_renegotiation</span></span>              | <span data-ttu-id="ee5c6-722">100</span><span class="sxs-lookup"><span data-stu-id="ee5c6-722">100</span></span>   | <span data-ttu-id="ee5c6-723">Indiates att fjärrvärden inte är beredd att utföra TLS-omförhandlingshandskakningar som svar på en omförhandlingsbegäran.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-723">Indiates that the remote host is not willing to perform TLS renegotiation handshakes in response to a renegotiation request.</span></span>                                 |
| <span data-ttu-id="ee5c6-724">unsupported_extension</span><span class="sxs-lookup"><span data-stu-id="ee5c6-724">unsupported_extension</span></span>         | <span data-ttu-id="ee5c6-725">110</span><span class="sxs-lookup"><span data-stu-id="ee5c6-725">110</span></span>   | <span data-ttu-id="ee5c6-726">Skickas om en TLS-klient tar emot en ServerHello som innehåller tillägg som inte uttryckligen efterfrågas i den första ClientHello (vilket indikerar att servern har ett problem).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-726">Sent if a TLS Client receives a ServerHello containing extensions not explicitly asked for in the initial ClientHello (indicating the server has a problem).</span></span> |

### <a name="parameters"></a><span data-ttu-id="ee5c6-727">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-727">Parameters</span></span>

- <span data-ttu-id="ee5c6-728">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-728">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-729">**alert_level** Returnera nivån för den mottagna aviseringen (varning eller allvarliga).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-729">**alert_level** Return the level of the received alert (warning or fatal).</span></span>
- <span data-ttu-id="ee5c6-730">**alert_value** Returnera värdet för den mottagna aviseringen (se tabell).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-730">**alert_value** Return the value of the received alert (see table).</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-731">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-731">Return Values</span></span>

- <span data-ttu-id="ee5c6-732">**NX_SUCCESS** (0x00) Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-732">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="ee5c6-733">**NX_PTR_ERROR** (0x07) Ogiltig TLS-session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-733">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-734">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-734">Allowed From</span></span>

<span data-ttu-id="ee5c6-735">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-736">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-736">Example</span></span>

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-737">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-737">See Also</span></span>

- <span data-ttu-id="ee5c6-738">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-738">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-739">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-739">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="ee5c6-740">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-740">nx_secure_tls_session_receive</span></span>

## <a name="nx_secure_tls_session_certificate_callback_set"></a><span data-ttu-id="ee5c6-741">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-741">nx_secure_tls_session_certificate_callback_set</span></span>

<span data-ttu-id="ee5c6-742">Konfigurera ett återanrop för TLS som ska användas för ytterligare certifikatverifiering</span><span class="sxs-lookup"><span data-stu-id="ee5c6-742">Set up a callback for TLS to use for additional certificate validation</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-743">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-743">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a><span data-ttu-id="ee5c6-744">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-744">Description</span></span>

<span data-ttu-id="ee5c6-745">Den här tjänsten tilldelar en funktionspekare till en TLS-session som TLS anropar när ett certifikat tas emot från en fjärrvärd, vilket gör att programmet kan utföra verifieringskontroller som DNS-verifiering, återkallelse av certifikat och tillämpning av certifikatprincip.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-745">This service assigns a function pointer to a TLS session that TLS will invoke when a certificate is received from a remote host, allowing the application to perform validation checks such as DNS validation, certificate revocation, and certificate policy enforcement.</span></span>

<span data-ttu-id="ee5c6-746">NetX Secure TLS utför grundläggande X.509-sökvägsverifiering på certifikatet innan återanrop anropas för att säkerställa att certifikatet kan spåras till ett certifikat i TLS betrodda certifikatarkiv, men all annan validering hanteras av det här återanropet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-746">NetX Secure TLS will perform basic X.509 path validation on the certificate before invoking the callback to assure that the certificate can be traced to a certificate in the TLS trusted certificate store, but all other validation will be handled by this callback.</span></span>

<span data-ttu-id="ee5c6-747">Motringningen ger TLS-sessionspekaren och en pekare till fjärrvärdidentitetscertifikatet (lövnoden i certifikatkedjan).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-747">The callback provides the TLS session pointer and a pointer to the remote host identity certificate (the leaf in the certificate chain).</span></span> <span data-ttu-id="ee5c6-748">Motringningen ska returnera NX_SUCCESS om all validering lyckas, annars bör den returnera en felkod som anger verifieringsfelet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-748">The callback should return NX_SUCCESS if all validation is successful, otherwise it should return an error code indicating the validation failure.</span></span> <span data-ttu-id="ee5c6-749">Ett annat värde än NX_SUCCESS kommer att orsaka att TLS-handskakningen avbryts omedelbart.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-749">Any value other than NX_SUCCESS will cause the TLS handshake to immediately abort.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-750">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-750">Parameters</span></span>

- <span data-ttu-id="ee5c6-751">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-751">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-752">**func_ptr** Pekare till återanropsfunktionen för certifikatverifiering.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-752">**func_ptr** Pointer to the certificate validation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-753">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-753">Return Values</span></span>

- <span data-ttu-id="ee5c6-754">**NX_SUCCESS** (0x00) Lyckad allokering av funktionspekaren.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-754">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="ee5c6-755">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-755">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-756">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-756">Allowed From</span></span>

<span data-ttu-id="ee5c6-757">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-757">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-758">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-758">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-759">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-759">See Also</span></span>

- <span data-ttu-id="ee5c6-760">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-760">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-761">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-761">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="ee5c6-762">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-762">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_tls_session_client_callback_set"></a><span data-ttu-id="ee5c6-763">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-763">nx_secure_tls_session_client_callback_set</span></span>

<span data-ttu-id="ee5c6-764">Konfigurera ett återanrop för TLS som ska anropas i början av en TLS-klienthandskakning</span><span class="sxs-lookup"><span data-stu-id="ee5c6-764">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-765">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-765">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="ee5c6-766">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-766">Description</span></span>

<span data-ttu-id="ee5c6-767">Den här tjänsten tilldelar en funktions pekare till en TLS-session som TLS anropar när en TLS-klienthandskakning har tagit emot ett ServerHelloDone-meddelande.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-767">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Client handshake has received a ServerHelloDone message.</span></span> <span data-ttu-id="ee5c6-768">Med återanropsfunktionen kan ett program bearbeta TLS-tillägg från det mottagna ServerHello-meddelandet som kräver indata eller beslutsfattande.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-768">The callback function allows an application to process any TLS extensions from the received ServerHello message that require input or decision making.</span></span>

<span data-ttu-id="ee5c6-769">Motringningen körs med det anropande TLS-sessionskontrollblocket och en matris med NX_SECURE_TLS_HELLO_EXTENSION objekt.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-769">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="ee5c6-770">Matrisen med tilläggsobjekt är avsedd att skickas till en hjälpfunktion som hittar och parsar ett visst tillägg.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-770">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="ee5c6-771">Det finns för närvarande inga specifika tillägg som stöds i NetX Secure som kräver TLS-klientindata, men återanropet är tillgängligt för programdesigners för att hantera anpassade eller nya tillägg som kan bli tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-771">Currently, there are no specific extensions supported in NetX Secure that require TLS Client input, but the callback is available for application designers to handle custom or new extensions that may become available.</span></span> <span data-ttu-id="ee5c6-772">Ett exempel på en hjälpfunktion som parsar TLS-tillägg som finns i hello messages finns *i nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-772">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="ee5c6-773">Återanropet av klienten kan också användas för att välja det aktiva identitetscertifikatet med *hjälp av nx_secure_tls_active_certificate_set* för TLS-klienten i händelse av att fjärrservern har begärt ett certifikat och angett information som gör att TLS-klienten kan välja ett specifikt certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-773">The client callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Client in the event that the remote server has requested a certificate and provided information to allow the TLS Client to select a specific certificate.</span></span> <span data-ttu-id="ee5c6-774">Se referensen för nx_secure_tls_active_certificate_set mer information.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-774">See the reference for nx_secure_tls_active_certificate_set for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-775">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-775">Parameters</span></span>

- <span data-ttu-id="ee5c6-776">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-776">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-777">**func_ptr** Pekare till funktionen för återanrop av TLS-klient.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-777">**func_ptr** Pointer to the TLS Client callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-778">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-778">Return Values</span></span>

- <span data-ttu-id="ee5c6-779">**NX_SUCCESS** (0x00) Lyckad allokering av funktionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-779">**NX_SUCCESS** (0x00) Successful allocation of function pointer.</span></span>
- <span data-ttu-id="ee5c6-780">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-780">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-781">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-781">Allowed From</span></span>

<span data-ttu-id="ee5c6-782">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-782">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-783">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-783">Example</span></span>

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-784">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-784">See Also</span></span>

- <span data-ttu-id="ee5c6-785">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-785">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-786">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-786">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="ee5c6-787">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-787">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a><span data-ttu-id="ee5c6-788">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="ee5c6-788">nx_secure_tls_session_x509_client_verify_configure</span></span>

<span data-ttu-id="ee5c6-789">Aktivera X.509-klientverifiering och allokera utrymme för klientcertifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-789">Enable client X.509 verification and allocate space for client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-790">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-790">Prototype</span></span>

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="ee5c6-791">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-791">Description</span></span>

<span data-ttu-id="ee5c6-792">Den här tjänsten aktiverar valfri X.509-klientautentisering för en TLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-792">This service enables the optional X.509 Client Authentication for a TLS Server instance.</span></span> <span data-ttu-id="ee5c6-793">Den allokerar också det utrymme som behövs för att bearbeta inkommande certifikatkedjor från fjärrklientvärden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-793">It also allocates the space needed to process incoming certificate chains from the remote client host.</span></span> <span data-ttu-id="ee5c6-794">Certifikaten som tillhandahålls av fjärrklienten kommer att verifieras mot TLS-serverinstansens betrodda certifikat, som tilldelas med *nx_secure_tls_trusted_certificate_add.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-794">The certificates supplied by the remote client will be verified against the TLS server instance's trusted certificates, assigned with the service *nx_secure_tls_trusted_certificate_add.*</span></span>

<span data-ttu-id="ee5c6-795">För TLS-klientläge krävs fjärrcertifikatallokering och *nx_secure_tls_remote_certificate_buffer_allocate* bör användas i stället.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-795">For TLS Client mode, remote certificate allocation is required and the service *nx_secure_tls_remote_certificate_buffer_allocate* should be used instead.</span></span> <span data-ttu-id="ee5c6-796">Aktivering av X.509-klientautentisering på en TLS-klientinstans har ingen effekt.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-796">Enabling X.509 Client Authentication on a TLS Client instance will have no effect.</span></span>

<span data-ttu-id="ee5c6-797">Den *certificate_buffer pekar* på allokerat utrymme för att lagra de inkommande fjärrcertifikaten och de kontrollblock som behövs för dessa certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-797">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="ee5c6-798">Bufferten divideras med antalet certifikat *(* certs_number ) med en lika stor del som ges till varje certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-798">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="ee5c6-799">Parametern *buffer_size* anger storleken på bufferten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-799">The *buffer_size* parameter indicates the size of the buffer.</span></span> <span data-ttu-id="ee5c6-800">Utrymmet som behövs finns med följande formel:</span><span class="sxs-lookup"><span data-stu-id="ee5c6-800">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="ee5c6-801">Vanliga certifikat med RSA-nycklar på 2 048 bitar som använder SHA-256 för signaturer är i intervallet 1 000–2 000 byte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-801">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="ee5c6-802">Bufferten bör vara tillräckligt stor för att minst innehålla den storleken för varje certifikat, men beroende på fjärrvärdcertifikaten kan vara betydligt mindre eller större.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-802">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="ee5c6-803">Observera att om bufferten är för liten för att innehålla det inkommande certifikatet, slutar TLS-handskakningen med ett fel.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-803">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-804">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-804">Parameters</span></span>

- <span data-ttu-id="ee5c6-805">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-805">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-806">**certs_number** Antal certifikat som ska allokeras från den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-806">**certs_number** Number of certificates to allocate from the provided buffer.</span></span>
- <span data-ttu-id="ee5c6-807">**certificate_buffer** Pekare till en buffert för att lagra certifikat som tagits emot från en fjärrvärd.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-807">**certificate_buffer** Pointer to a buffer to hold certificates received from a remote host.</span></span>
- <span data-ttu-id="ee5c6-808">**buffer_size** Certifikatbuffertens storlek.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-808">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-809">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-809">Return Values</span></span>

- <span data-ttu-id="ee5c6-810">**NX_SUCCESS** (0x00)Lyckad allokering av certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-810">**NX_SUCCESS** (0x00)Successful allocation of certificate.</span></span>
- <span data-ttu-id="ee5c6-811">**NX_PTR_ERROR** (0x07) Ogiltig TLS-session eller buffertpekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-811">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="ee5c6-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) Den angivna bufferten var för liten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="ee5c6-813">**NX_INVALID_PARAMETERS** (0x4D) Bufferten var för liten för att innehålla önskat antal certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-813">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-814">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-814">Allowed From</span></span>

<span data-ttu-id="ee5c6-815">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-815">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-816">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-816">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-817">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-817">See Also</span></span>

- <span data-ttu-id="ee5c6-818">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-818">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-819">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-819">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-820">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-820">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

## <a name="nx_secure_tls_session_client_verify_disable"></a><span data-ttu-id="ee5c6-821">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="ee5c6-821">nx_secure_tls_session_client_verify_disable</span></span>

<span data-ttu-id="ee5c6-822">Inaktivera klientcertifikatautentisering för en Säker NetX-TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-822">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-823">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-823">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="ee5c6-824">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-824">Description</span></span>

<span data-ttu-id="ee5c6-825">Den här tjänsten inaktiverar klientcertifikatautentisering för en specifik TLS-session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-825">This service disables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="ee5c6-826">Mer information nx_secure_tls_session_client_verify_enable finns i nx_secure_tls_session_client_verify_enable information.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-826">See nx_secure_tls_session_client_verify_enable for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-827">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-827">Parameters</span></span>

- <span data-ttu-id="ee5c6-828">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-828">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-829">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-829">Return Values</span></span>

- <span data-ttu-id="ee5c6-830">**NX_SUCCESS** (0x00) Lyckad tillståndsändring.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-830">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="ee5c6-831">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-831">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-832">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-832">Allowed From</span></span>

<span data-ttu-id="ee5c6-833">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-833">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-834">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-834">Example</span></span>

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-835">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-835">See Also</span></span>

- <span data-ttu-id="ee5c6-836">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="ee5c6-836">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="ee5c6-837">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-837">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-838">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-838">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_client_verify_enable"></a><span data-ttu-id="ee5c6-839">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="ee5c6-839">nx_secure_tls_session_client_verify_enable</span></span>

<span data-ttu-id="ee5c6-840">Aktivera klientcertifikatautentisering för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-840">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-841">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-841">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="ee5c6-842">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-842">Description</span></span>

<span data-ttu-id="ee5c6-843">Den här tjänsten aktiverar klientcertifikatautentisering för en specifik TLS-session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-843">This service enables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="ee5c6-844">Om du aktiverar klientcertifikatautentisering för en TLS-serverinstans kommer TLS-servern att begära ett certifikat från valfri TLS-fjärrklient under den första TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-844">Enabling Client Certificate Authentication for a TLS Server instance will cause the TLS Server to request a certificate from any remote TLS Client during the initial TLS handshake.</span></span> <span data-ttu-id="ee5c6-845">Certifikatet som tas emot från den fjärranslutna TLS-klienten åtföljs av ett CertificateVerify-meddelande som TLS-servern använder för att verifiera att klienten äger certifikatet (har åtkomst till den privata nyckel som är associerad med certifikatet).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-845">The certificate received from the remote TLS Client is accompanied by a CertificateVerify message, which the TLS Server uses to verify that the Client owns the certificate (has access to the private key associated with that certificate).</span></span>

<span data-ttu-id="ee5c6-846">Om det angivna certifikatet kan verifieras och spåras tillbaka till ett certifikat i TLS-serverns betrodda certifikatarkiv via en X.509-certifikatkedja autentiseras den fjärranslutna TLS-klienten och handskakningen fortsätter.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-846">If the provided certificate can be verified and traced back to a certificate in the TLS Server trusted certificate store via an X.509 certificate chain, the remote TLS Client is authenticated and the handshake proceeds.</span></span> <span data-ttu-id="ee5c6-847">Om det uppstår fel vid bearbetning av certifikatet eller CertificateVerify-meddelandet slutar TLS-handskakningen med ett fel.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-847">In case of any errors in processing the certificate or CertificateVerify message, the TLS handshake ends with an error.</span></span>

> [!NOTE]
> <span data-ttu-id="ee5c6-848">*TLS-servern måste ha minst ett certifikat i det betrodda arkivet som läggs till med nx_secure_tls_trusted_certificate_add eller så misslyckas autentiseringen alltid.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-848">*The TLS Server must have at least one certificate in its trusted store added with nx_secure_tls_trusted_certificate_add or authentication will always fail.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-849">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-849">Parameters</span></span>

- <span data-ttu-id="ee5c6-850">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-850">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-851">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-851">Return Values</span></span>

- <span data-ttu-id="ee5c6-852">**NX_SUCCESS** (0x00) Lyckad tillståndsändring.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-852">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="ee5c6-853">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-853">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-854">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-854">Allowed From</span></span>

<span data-ttu-id="ee5c6-855">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-855">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-856">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-856">Example</span></span>

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-857">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-857">See Also</span></span>

- <span data-ttu-id="ee5c6-858">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="ee5c6-858">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="ee5c6-859">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-859">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-860">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-860">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-861">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-861">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_tls_session_create"></a><span data-ttu-id="ee5c6-862">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-862">nx_secure_tls_session_create</span></span>

<span data-ttu-id="ee5c6-863">Skapa en NetX Secure TLS-session för säker kommunikation</span><span class="sxs-lookup"><span data-stu-id="ee5c6-863">Create a NetX Secure TLS Session for secure communications</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-864">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-864">Prototype</span></span>

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a><span data-ttu-id="ee5c6-865">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-865">Description</span></span>

<span data-ttu-id="ee5c6-866">Den här tjänsten initierar en NX_SECURE_TLS_SESSION-strukturinstans för användning vid etablering av säker TLS-kommunikation via en nätverksanslutning.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-866">This service initializes an NX_SECURE_TLS_SESSION structure instance for use in establishing secure TLS communications over a network connection.</span></span>

<span data-ttu-id="ee5c6-867">Metoden tar ett NX_SECURE_TLS_CRYPTO objekt som fylls i med de tillgängliga kryptografiska metoder som ska användas för TLS.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-867">The method takes a NX_SECURE_TLS_CRYPTO object that is populated with the available cryptographic methods to be used for TLS.</span></span> <span data-ttu-id="ee5c6-868">Den *encryption_metadata_area* pekar på en buffert som allokerats för användning av TLS för de "metadata" som används av de kryptografiska metoderna i NX_SECURE_TLS_CRYPTO för beräkningar.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-868">The *encryption_metadata_area* points to a buffer allocated for use by TLS for the "metadata" used by the cryptographic methods in the NX_SECURE_TLS_CRYPTO table for calculations.</span></span> <span data-ttu-id="ee5c6-869">Tabellens storlek kan fastställas med hjälp av nx_secure_tls_metadata_size_calculate tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-869">The size of the table can be determined by using the nx_secure_tls_metadata_size_calculate service.</span></span> <span data-ttu-id="ee5c6-870">Mer information finns i avsnittet "Kryptografi i NetX Secure TLS" i kapitel 3.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-870">See the section "Cryptography in NetX Secure TLS" in Chapter 3 for more details.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-871">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-871">Parameters</span></span>

- <span data-ttu-id="ee5c6-872">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-872">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-873">**cipher_table** Pekare till kryptografiska TLS-metoder.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-873">**cipher_table** Pointer to TLS cryptographic methods.</span></span>
- <span data-ttu-id="ee5c6-874">**encryption_metadata_area** Pekare till blanksteg för kryptografimetadata.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-874">**encryption_metadata_area** Pointer to space for cryptography metadata.</span></span>
- <span data-ttu-id="ee5c6-875">**encryption_metadata_size** Storleken på metadatabufferten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-875">**encryption_metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-876">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-876">Return Values</span></span>

- <span data-ttu-id="ee5c6-877">**NX_SUCCESS** (0x00)Lyckad initiering av TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-877">**NX_SUCCESS** (0x00)Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="ee5c6-878">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-878">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="ee5c6-879">**NX_INVALID_PARAMETERS** (0x4D) Metadatabufferten var för liten för de angivna metoderna.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-879">**NX_INVALID_PARAMETERS** (0x4D) The metadata buffer was too small for the given methods.</span></span>
- <span data-ttu-id="ee5c6-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) En obligatorisk chiffermetod för den aktiverade versionen av TLS angavs inte i chiffertabellen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A required cipher method for the enabled version of TLS was not supplied in the cipher table.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-881">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-881">Allowed From</span></span>

<span data-ttu-id="ee5c6-882">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-882">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-883">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-883">Example</span></span>

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-884">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-884">See Also</span></span>

- <span data-ttu-id="ee5c6-885">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-885">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-886">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-886">nx_secure_tls_metadata_size_calculate</span></span>
- <span data-ttu-id="ee5c6-887">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-887">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-888">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-888">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-889">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="ee5c6-889">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="ee5c6-890">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-890">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="ee5c6-891">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-891">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="ee5c6-892">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ee5c6-892">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="ee5c6-893">Kryptografi i NetX Secure TLS i kapitel 3</span><span class="sxs-lookup"><span data-stu-id="ee5c6-893">Cryptography in NetX Secure TLS in Chapter 3</span></span>

## <a name="nx_secure_tls_session_delete"></a><span data-ttu-id="ee5c6-894">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ee5c6-894">nx_secure_tls_session_delete</span></span>

<span data-ttu-id="ee5c6-895">Ta bort en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-895">Delete a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-896">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-896">Prototype</span></span>

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="ee5c6-897">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-897">Description</span></span>

<span data-ttu-id="ee5c6-898">Den här tjänsten tar bort en TLS-session som representeras av en NX_SECURE_TLS_SESSION-strukturinstans och släpper alla systemresurser som ägs av den sessionsinstansen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-898">This service deletes a TLS session represented by an NX_SECURE_TLS_SESSION structure instance and releases all system resources owned by that session instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-899">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-899">Parameters</span></span>

- <span data-ttu-id="ee5c6-900">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-900">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-901">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-901">Return Values</span></span>

- <span data-ttu-id="ee5c6-902">**NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-902">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="ee5c6-903">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-903">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-904">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-904">Allowed From</span></span>

<span data-ttu-id="ee5c6-905">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-905">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-906">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-906">Example</span></span>

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-907">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-907">See Also</span></span>

- <span data-ttu-id="ee5c6-908">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-908">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-909">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-909">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-910">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-910">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-911">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="ee5c6-911">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="ee5c6-912">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-912">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="ee5c6-913">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-913">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="ee5c6-914">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-914">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_end"></a><span data-ttu-id="ee5c6-915">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="ee5c6-915">nx_secure_tls_session_end</span></span>

<span data-ttu-id="ee5c6-916">Avsluta en aktiv NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-916">End an active NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-917">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-917">Prototype</span></span>

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee5c6-918">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-918">Description</span></span>

<span data-ttu-id="ee5c6-919">Den här tjänsten avslutar en TLS-session som representeras av en NX_SECURE_TLS_SESSION-strukturinstans genom att skicka TLS CloseNotify-meddelandet till fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-919">This service ends a TLS session represented by an NX_SECURE_TLS_SESSION structure instance by sending the TLS CloseNotify message to the remote host.</span></span> <span data-ttu-id="ee5c6-920">Tjänsten väntar sedan på att fjärrvärden ska svara med ett eget CloseNotify-meddelande.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-920">The service then waits for the remote host to respond with its own CloseNotify message.</span></span>

<span data-ttu-id="ee5c6-921">Om fjärrvärden inte skickar ett CloseNotify-meddelande betraktar TLS detta som ett fel och en möjlig säkerhetsöverträdelse, så det är viktigt att kontrollera returvärdet för en säker anslutning.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-921">If the remote host does not send a CloseNotify message, TLS considers this an error and a possible security breach, so checking the return value is important for a secure connection.</span></span> <span data-ttu-id="ee5c6-922">Parametern **wait_option** kan användas för att styra hur länge tjänsten ska vänta på svaret innan kontrollen returneras till den anropande tråden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-922">The **wait_option** parameter can be used to control how long the service should wait for the response before returning control to the calling thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-923">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-923">Parameters</span></span>

- <span data-ttu-id="ee5c6-924">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-924">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-925">**wait_option** Anger hur länge tjänsten ska vänta på svaret från fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-925">**wait_option** Indicates how long the service should wait for the response from the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-926">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-926">Return Values</span></span>

- <span data-ttu-id="ee5c6-927">**NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-927">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="ee5c6-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Fick inget svar från fjärrvärden innan det tog slut.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Did not receive a response from the remote host before timing out.</span></span>
- <span data-ttu-id="ee5c6-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Det gick inte att allokera ett paket för att skicka CloseNotify-meddelandet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a packet to send the CloseNotify message.</span></span>
- <span data-ttu-id="ee5c6-930">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka CloseNotify-meddelandet via TCP-socketen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-930">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Could not send the CloseNotify message over the TCP socket.</span></span>
- <span data-ttu-id="ee5c6-931">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-931">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-932">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-932">Allowed From</span></span>

<span data-ttu-id="ee5c6-933">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-933">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-934">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-934">Example</span></span>

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-935">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-935">See Also</span></span>

- <span data-ttu-id="ee5c6-936">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-936">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-937">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-937">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-938">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-938">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-939">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ee5c6-939">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="ee5c6-940">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-940">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="ee5c6-941">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-941">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="ee5c6-942">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-942">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_packet_buffer_set"></a><span data-ttu-id="ee5c6-943">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-943">nx_secure_tls_session_packet_buffer_set</span></span>

<span data-ttu-id="ee5c6-944">Ange paketsammansättningsbufferten för en Säker NetX-TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-944">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-945">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-945">Prototype</span></span>

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="ee5c6-946">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-946">Description</span></span>

<span data-ttu-id="ee5c6-947">Den här tjänsten associerar ett paket med en återmonteringsbuffert till en TLS-session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-947">This service associates a packet reassembly buffer to a TLS session.</span></span> <span data-ttu-id="ee5c6-948">För att kunna dekryptera och parsa inkommande TLS-poster måste data i varje post sammanställas från de underliggande TCP-paketen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-948">In order to decrypt and parse incoming TLS records, the data in each record must be assembled from the underlying TCP packets.</span></span> <span data-ttu-id="ee5c6-949">TLS-poster kan vara upp till 16 kB stora (men är vanligtvis mycket mindre) så de kanske inte får plats i ett enda TCP-paket.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-949">TLS records can be up to 16KB in size (though typically are much smaller) so may not fit into a single TCP packet.</span></span>

<span data-ttu-id="ee5c6-950">Om du vet att den inkommande meddelandestorleken kommer att vara mindre än TLS-postgränsen på 16 kB, kan buffertstorleken göras mindre, men för att hantera okända inkommande data bör bufferten göras så stor som möjligt.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-950">If you know the incoming message size will be smaller than the TLS record limit of 16KB, the buffer size can be made smaller, but in order to handle unknown incoming data the buffer should be made as large as possible.</span></span> <span data-ttu-id="ee5c6-951">Om en inkommande post är större än den angivna bufferten avslutas TLS-sessionen med ett fel.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-951">If an incoming record is larger than the supplied buffer, the TLS session will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-952">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-952">Parameters</span></span>

- <span data-ttu-id="ee5c6-953">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-953">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-954">**buffer_ptr** Pekare till buffert för TLS som ska användas för paket som ska sättas ihop på ett annat sätt.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-954">**buffer_ptr** Pointer to buffer for TLS to use for packet reassembly.</span></span>
- <span data-ttu-id="ee5c6-955">**buffer_size** Storleken på den angivna bufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-955">**buffer_size** Size of the supplied buffer in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-956">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-956">Return Values</span></span>

- <span data-ttu-id="ee5c6-957">**NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-957">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="ee5c6-958">**NX_INVALID_PARAMETERS** (0x4D) Ogiltig buffert eller TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-958">**NX_INVALID_PARAMETERS** (0x4D) Invalid buffer or TLS session pointer.</span></span>
- <span data-ttu-id="ee5c6-959">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-959">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-960">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-960">Allowed From</span></span>

<span data-ttu-id="ee5c6-961">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-961">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-962">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-962">Example</span></span>

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-963">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-963">See Also</span></span>

- <span data-ttu-id="ee5c6-964">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-964">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-965">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-965">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-966">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-966">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-967">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ee5c6-967">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="ee5c6-968">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-968">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="ee5c6-969">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-969">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="ee5c6-970">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-970">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_protocol_version_override"></a><span data-ttu-id="ee5c6-971">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="ee5c6-971">nx_secure_tls_session_protocol_version_override</span></span>

<span data-ttu-id="ee5c6-972">Åsidosätt standardversionen av TLS-protokollet för en Säker NetX-TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-972">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-973">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-973">Prototype</span></span>

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a><span data-ttu-id="ee5c6-974">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-974">Description</span></span>

<span data-ttu-id="ee5c6-975">Den här tjänsten åsidosätter standardversionen av TLS-protokollet (senaste) som används av en viss session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-975">This service overrides the default (newest) TLS protocol version used by a particular session.</span></span> <span data-ttu-id="ee5c6-976">Detta gör att NetX Secure TLS kan använda en äldre version av TLS för en specifik TLS-session utan att inaktivera nyare TLS-versioner vid kompileringen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-976">This enables NetX Secure TLS to use an older version of TLS for a specific TLS Session without disabling newer TLS versions at compile time.</span></span> <span data-ttu-id="ee5c6-977">Detta kan vara användbart i program som kan behöva kommunicera med en äldre värd som inte stöder den senaste versionen av TLS.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-977">This may be useful in applications that may need to communicate with an older host that does not support the newest version of TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee5c6-978">*Från och med version 5.11SP3 stöder NetX Secure TLS RFC 7507 (se anmärkning nedan) och eventuella åsidosättningar till en äldre version med det här API:et resulterar i att en ÅTERSTÄLLNINGs-SCSV skickas i ClientHello. Om servern stöder en nyare version av TLS och återställnings-SCSV ingår i ClientHello avbryter servern TLS-handskakningen med en avisering om olämplig återställning. SCSV skickas endast när versionsåsidosättning är en äldre version av TLS än aktiverad (t.ex. om du åsidosätter versionen till TLS 1.2 skickas ingen SCSV).*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-978">*As of version 5.11SP3, NetX Secure TLS supports RFC 7507 (see note below) and any override to an older version with this API will result in a fallback SCSV being sent in the ClientHello. If the server supports a newer version of TLS and the fallback SCSV is included in the ClientHello, that server will abort the TLS handshake with an "Inappropriate Fallback" alert. The SCSV is only sent when the version override is an older version of TLS than is enabled (e.g. if you override the version to TLS 1.2, no SCSV will be sent).*</span></span>

<span data-ttu-id="ee5c6-979">Giltiga värden för protocol_version är följande makron: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 och NX_SECURE_TLS_VERSION_TLS_1_2.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-979">Valid values for the protocol_version parameter are the following macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1, and NX_SECURE_TLS_VERSION_TLS_1_2.</span></span>

<span data-ttu-id="ee5c6-980">Makron som NX_SECURE_TLS_DISABLE_TLS_1_1 och NX_SECURE_TLS_ENABLE_TLS_1_0 kan användas för att styra vilka versioner av TLS som kompileras i programmet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-980">The macros NX_SECURE_TLS_DISABLE_TLS_1_1 and NX_SECURE_TLS_ENABLE_TLS_1_0 can be used to control the versions of TLS that are compiled into the application.</span></span> <span data-ttu-id="ee5c6-981">TLS version 1.2 är alltid aktiverat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-981">TLS version 1.2 is always enabled.</span></span>

<span data-ttu-id="ee5c6-982">Observera att om fjärrvärden inte stöder den angivna versionen misslyckas anslutningen – endast den angivna åsidosättningsversionen förhandlas av NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-982">Note that if the remote host does not support the supplied version, the connection will fail – only the supplied override version will be negotiated by NetX Secure TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee5c6-983">RFC 7507: TLS Fallback SCSV.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-983">RFC 7507: TLS Fallback SCSV.</span></span> <span data-ttu-id="ee5c6-984">Den här RFC:en introducerades för att minimera ett säkerhetsproblem som ursprungligen orsakades av servrar som felaktigt hanterade protokoll nedgradering av förhandling och i stället avvisade giltiga ClientHello-meddelanden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-984">This RFC was introduced to mitigate a security problem that was originally caused by servers that improperly handled protocol downgrade negotiation and instead rejected otherwise valid ClientHello messages.</span></span> <span data-ttu-id="ee5c6-985">I ett försök att fortsätta vara kompatibelt med dessa gamla servrar började vissa TLS-klientprogram att försöka utföra misslyckade handskakningar på nytt med och äldre TLS-version (t.ex. misslyckades TLS 1.2 så försök med TLS 1.1).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-985">In an attempt to remain compatible with these old servers, some TLS client applications started to retry failed handshakes with and older TLS version (e.g. TLS 1.2 failed so try TLS 1.1).</span></span> <span data-ttu-id="ee5c6-986">Den här lösningen introducerade dock ett nytt problem – en angripare kan tvinga en klient att nedgradera genom att artificiellt införa ett nätverks- eller paketfel som orsakar att serveranslutningen misslyckas – även om servern hade stöd för den nyare TLS-versionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-986">This workaround however introduced a new problem – an attacker could force a client to downgrade by artificially introducing a network or packet error causing the server connection to fail – even when the server supported the newer TLS version.</span></span> <span data-ttu-id="ee5c6-987">Genom att nedgradera till en äldre version kan angriparen utnyttja svagheter i den versionen (särskilt SSLv3<sup>21</sup> är svag förDLE-attacken).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-987">By downgrading to an older version the attacker could exploit weaknesses in that version (SSLv3<sup>21</sup> in particular is weak to the POODLE attack).</span></span> <span data-ttu-id="ee5c6-988">För att förhindra den här situationen har RFC 7507 introduduerat "återställnings-SCSV", en pseudo-chiffersuite<sup>22</sup> som skickas i ClientHello som meddelar en TLS-server när en TLS-klient använder en TLS-version som inte är den senaste versionen som stöds.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-988">To prevent this situation, RFC 7507 introdued the "fallback SCSV," a pseudo-ciphersuite<sup>22</sup> sent in the ClientHello that notifies a TLS server when a TLS client is using a TLS version that is not the newest version it supports.</span></span> <span data-ttu-id="ee5c6-989">På så sätt kan en server som stöder en nyare version avvisa en ClientHello som innehåller återställnings-SCSV och förhindra att nedgraderingsattacken lyckas.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-989">This way, a server that supports a newer version can reject a ClientHello containing the fallback SCSV and prevent the downgrade attack from succeeding.</span></span>

21. <span data-ttu-id="ee5c6-990">NetX Secure implementerar inte SSLv3 på grund av att det finns kända allvarliga svagheter, till exempelDLE.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-990">NetX Secure does not implement SSLv3 due to the existence of known serious weaknesses such as POODLE.</span></span>

22. <span data-ttu-id="ee5c6-991">En pseudociphersuite, eller SCSV (Signaling Cipher Suite Value), är ett reserverat chiffersvitnummer som används för att signalera aktiverade TLS-implementeringar om funktioner som inte var tillgängliga i äldre TLS-versioner.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-991">A pseudo-ciphersuite, or SCSV (Signaling Cipher Suite Value), is a reserved ciphersuite number that is used to signal enabled TLS implementations about features that were not available in older TLS versions.</span></span> <span data-ttu-id="ee5c6-992">Återställnings-SCSV och TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) är exempel.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-992">The fallback SCSV and the TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) are examples.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-993">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-993">Parameters</span></span>

- <span data-ttu-id="ee5c6-994">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-994">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-995">**protocol_version** TLS-versions makro för den specifika TLS-version som ska användas.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-995">**protocol_version** TLS version macro for the specific TLS version to use.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-996">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-996">Return Values</span></span>

- <span data-ttu-id="ee5c6-997">**NX_SUCCESS** (0x00) Lyckad tillståndsändring.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-997">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="ee5c6-998">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-998">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="ee5c6-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Känd men inte TLS-version stöds.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Known but unsupported TLS version.</span></span>
- <span data-ttu-id="ee5c6-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Ogiltig protokollversion.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Invalid protocol version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1001">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1001">Allowed From</span></span>

<span data-ttu-id="ee5c6-1002">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1002">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1003">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1003">Example</span></span>

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1004">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1004">See Also</span></span>

- <span data-ttu-id="ee5c6-1005">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1005">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-1006">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1006">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_receive"></a><span data-ttu-id="ee5c6-1007">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1007">nx_secure_tls_session_receive</span></span>

<span data-ttu-id="ee5c6-1008">Ta emot data från en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1008">Receive data from a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1009">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1009">Prototype</span></span>

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1010">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1010">Description</span></span>

<span data-ttu-id="ee5c6-1011">Den här tjänsten tar emot data från den angivna aktiva TLS-sessionen och hanterar dekrypteringen av dessa data innan de anges för anroparen i NX_PACKET-parametern.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1011">This service receives data from the specified active TLS session, handling the decryption of that data before providing it to the caller in the NX_PACKET parameter.</span></span> <span data-ttu-id="ee5c6-1012">Om inga data köas i den angivna sessionen pausas anropet baserat på det angivna väntealternativet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1012">If no data is queued in the specified session, the call suspends based on the supplied wait option.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee5c6-1013">*Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1013">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1014">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1014">Parameters</span></span>

- <span data-ttu-id="ee5c6-1015">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1015">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-1016">**packet_ptr** Pekare till en allokerad TLS-paket pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1016">**packet_ptr** Pointer to an allocated TLS packet pointer.</span></span>
- <span data-ttu-id="ee5c6-1017">**wait_option** Anger hur länge tjänsten ska vänta på ett paket från fjärrvärden innan den returneras.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1017">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1018">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1018">Return Values</span></span>

- <span data-ttu-id="ee5c6-1019">**NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1019">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="ee5c6-1020">**NX_NO_PACKET** (0x01) Inga data tas emot.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1020">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="ee5c6-1021">**NX_NOT_CONNECTED** (0x38) Den underliggande TCP-socketen är inte längre ansluten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1021">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="ee5c6-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Ett mottaget meddelande misslyckades med en autentiseringshasharkontroll.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="ee5c6-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Ett mottaget meddelande innehöll en okänd protokollversion i rubriken.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="ee5c6-1024">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Tog emot en TLS-avisering från fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1024">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="ee5c6-1025">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1025">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="ee5c6-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Den angivna TLS-sessionen initierades inte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1027">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1027">Allowed From</span></span>

<span data-ttu-id="ee5c6-1028">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1028">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1029">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1029">Example</span></span>

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1030">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1030">See Also</span></span>

- <span data-ttu-id="ee5c6-1031">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1031">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="ee5c6-1032">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1032">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-1033">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1033">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-1034">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1034">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-1035">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1035">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="ee5c6-1036">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1036">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="ee5c6-1037">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1037">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="ee5c6-1038">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1038">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a><span data-ttu-id="ee5c6-1039">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1039">nx_secure_tls_session_renegotiate_callback_set</span></span>

<span data-ttu-id="ee5c6-1040">Tilldela ett återanrop som anropas i början av en omförhandling av sessionen</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1040">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1041">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1041">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a><span data-ttu-id="ee5c6-1042">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1042">Description</span></span>

<span data-ttu-id="ee5c6-1043">Den här tjänsten tilldelar ett återanrop till en TLS-session som anropas när det första meddelandet i en omförhandling av session tas emot från fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1043">This service assigns a callback to a TLS session that will be invoked whenever the first message of a session renegotiation handshake is received from the remote host.</span></span>

<span data-ttu-id="ee5c6-1044">Återanropsfunktionen är avsedd som ett meddelande till programmet om att en omförhandling av handskakningen har börjat – programmet kan välja att avsluta TLS-sessionen genom att returnera ett värde som inte är noll från återanropet, vilket gör att TLS avslutar TLS-sessionen med ett fel.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1044">The callback function is intended as a notification to the application that a renegotiation handshake is beginning – the application may choose to terminate the TLS session by returning any non-zero value from the callback which will cause TLS to end the TLS session with an error.</span></span> <span data-ttu-id="ee5c6-1045">Om programmet vill fortsätta med omförhandlingen ska återanropet returnera NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1045">If the application wishes to proceed with the renegotiation, the callback should return NX_SUCCESS.</span></span>

> [!NOTE]
> <span data-ttu-id="ee5c6-1046">*På grund av semantiken för TLS-omförhandling anropas motringningen för NetX Secure TLS-klienter när en HelloRequest tas emot från fjärrservern, men inte när klienten initierar omförhandlingen. På NetX Secure TLS-servrar anropas motringningen när en omförhandling av ClientHello tas emot (alla ClientHello tas emot i samband med en aktiv TLS-session). Det innebär att återanropet anropas oavsett om fjärrvärden eller det lokala programmet har initierat omförhandlingen eftersom TLS-servern skickar en HelloRequest som fjärrklienten svarar på.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1046">*Due to the semantics of TLS renegotiation, the callback will be invoked for NetX Secure TLS Clients whenever a HelloRequest is received from the remote server, but not when the client initiates the renegotiation. On NetX Secure TLS Servers, the callback will be invoked whenever a renegotiation ClientHello is received (any ClientHello received in the context of an active TLS session). This means that the callback will be invoked whether the remote host or the local application has initiated the renegotiation because the TLS server will send a HelloRequest to which the remote client will respond.*</span></span>

<span data-ttu-id="ee5c6-1047">NetX Secure TLS implementerar Secure Renegotiation Incation Extension från RFC 5746 för att säkerställa att omförhandling av handskakningar inte utsätts för man-in-the-middle-attacker.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1047">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1048">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1048">Parameters</span></span>

- <span data-ttu-id="ee5c6-1049">**session_ptr** Pekare till TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1049">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-1050">**func_ptr** Pekare till återanropsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1050">**func_ptr** Pointer to callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1051">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1051">Return Values</span></span>

- <span data-ttu-id="ee5c6-1052">**NX_SUCCESS** (0x00) Lyckad tilldelning av återanrop.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1052">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="ee5c6-1053">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare för återanropsfunktionen eller TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1053">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer for the callback function or TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1054">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1054">Allowed From</span></span>

<span data-ttu-id="ee5c6-1055">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1055">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1056">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1056">Example</span></span>

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1057">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1057">See Also</span></span>

- <span data-ttu-id="ee5c6-1058">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1058">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-1059">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1059">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-1060">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1060">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="ee5c6-1061">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1061">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="ee5c6-1062">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1062">nx_secure_tls_session_renegotiate</span></span>

## <a name="nx_secure_tls_session_renegotiate"></a><span data-ttu-id="ee5c6-1063">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1063">nx_secure_tls_session_renegotiate</span></span>

<span data-ttu-id="ee5c6-1064">Initiera en omförhandling av sessionshandskakning med fjärrvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1064">Initiate a session renegotiation handshake with the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1065">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1065">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1066">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1066">Description</span></span>

<span data-ttu-id="ee5c6-1067">Den här tjänsten initierar en *omförhandling av session* med en ansluten fjärransluten TLS-värd.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1067">This service initiates a session *renegotiation* handshake with a connected remote TLS host.</span></span> <span data-ttu-id="ee5c6-1068">En omförhandling består av en andra TLS-handskakning i kontexten för en tidigare etablerad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1068">A renegotiation consists of a second TLS handshake within the context of a previously-established TLS session.</span></span> <span data-ttu-id="ee5c6-1069">Vart och ett av de nya handskakningsmeddelandena krypteras med TLS-sessionen tills nya sessionsnycklar genereras och ChangeCipherSpec-meddelanden utbyts, då de nya nycklarna används för att kryptera alla meddelanden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1069">Each of the new handshake messages is encrypted using the TLS session until new session keys are generated and ChangeCipherSpec messages are exchanged, at which time the new keys are used to encrypt all messages.</span></span>

<span data-ttu-id="ee5c6-1070">En omförhandling kan initieras när som helst när en TLS-session har upprättats.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1070">A renegotiation can be initiated at any time once a TLS session is established.</span></span> <span data-ttu-id="ee5c6-1071">Om en omförhandling görs under en TLS-handskakning eller innan en TLS-session upprättas vidtas ingen åtgärd.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1071">If a renegotiation is attempted during a TLS handshake or before a TLS session is established no action will be taken.</span></span>

> [!NOTE]
> <span data-ttu-id="ee5c6-1072">*En hel TLS-handskakning utförs när den här tjänsten anropas, så tiden till slutförande och returnerad status varierar beroende på de aktuella TLS-inställningarna och sessionsparametrarna.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1072">*An entire TLS handshake will be performed when this service is invoked so the time to completion and returned status will vary depending on the current TLS settings and session parameters.*</span></span>

<span data-ttu-id="ee5c6-1073">NetX Secure TLS implementerar tillägget För säker omförhandling från RFC 5746 för att säkerställa att omförhandlingshandskakningar inte utsätts för man-in-the-middle-attacker.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1073">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1074">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1074">Parameters</span></span>

- <span data-ttu-id="ee5c6-1075">**session_ptr** Pekare till TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1075">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-1076">**wait_option** Anger hur länge tjänsten ska vänta på ett paket från fjärrvärden innan den returneras.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1076">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span> <span data-ttu-id="ee5c6-1077">Detta skickas till alla NetX-tjänster i TLS.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1077">This is passed to all NetX services within TLS.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1078">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1078">Return Values</span></span>

- <span data-ttu-id="ee5c6-1079">**NX_SUCCESS** (0x00) Lyckad omförhandling.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1079">**NX_SUCCESS** (0x00) Successful renegotiation.</span></span>
- <span data-ttu-id="ee5c6-1080">**NX_NO_PACKET** (0x01) Inga data tas emot.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1080">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="ee5c6-1081">**NX_NOT_CONNECTED** (0x38) Den underliggande TCP-socketen är inte längre ansluten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1081">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="ee5c6-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Ett mottaget meddelande misslyckades med en autentiseringshasharkontroll.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="ee5c6-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Ett mottaget meddelande innehöll en okänd protokollversion i rubriken.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="ee5c6-1084">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Tog emot en TLS-avisering från fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1084">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="ee5c6-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) Den lokala eller fjärranslutna TLS-sessionen är inaktiv, vilket gör omförhandling omöjligt.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) The local or remote TLS session is inactive, making renegotiation impossible.</span></span>
- <span data-ttu-id="ee5c6-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) Fjärrvärden tillhandahåller inte antingen SCSV eller Secure Renegotiation Extension och därför går det inte att utföra omförhandling.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) The remote host did not provide either the SCSV or Secure Renegotiation Extension and thus renegotiation cannot be performed.</span></span>
- <span data-ttu-id="ee5c6-1087">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1087">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="ee5c6-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Den angivna TLS-sessionen initierades inte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>
- <span data-ttu-id="ee5c6-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underliggande paketallokering misslyckades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1090">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1090">Allowed From</span></span>

<span data-ttu-id="ee5c6-1091">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1091">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1092">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1092">Example</span></span>

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1093">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1093">See Also</span></span>

- <span data-ttu-id="ee5c6-1094">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1094">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-1095">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1095">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-1096">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1096">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="ee5c6-1097">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1097">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="ee5c6-1098">nx_secure_tls_session_renegotiation_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1098">nx_secure_tls_session_renegotiation_callback_set</span></span>

## <a name="nx_secure_tls_session_reset"></a><span data-ttu-id="ee5c6-1099">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1099">nx_secure_tls_session_reset</span></span>

<span data-ttu-id="ee5c6-1100">Rensa och återställa en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1100">Clear out and reset a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1101">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1101">Prototype</span></span>

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1102">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1102">Description</span></span>

<span data-ttu-id="ee5c6-1103">Den här tjänsten tar bort en TLS-session och återställer tillståndet som om sessionen just hade skapats så att ett befintligt TLS-sessionsobjekt kan användas igen för en ny session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1103">This service clears out a TLS session and resets the state as if the session had just been created so an existing TLS session object can be re-used for a new session.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1104">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1104">Parameters</span></span>

- <span data-ttu-id="ee5c6-1105">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1105">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1106">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1106">Return Values</span></span>

- <span data-ttu-id="ee5c6-1107">**NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1107">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="ee5c6-1108">**NX_INVALID_PARAMETERS** (0x4D) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1108">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="ee5c6-1109">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1109">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1110">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1110">Allowed From</span></span>

<span data-ttu-id="ee5c6-1111">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1111">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1112">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1112">Example</span></span>

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1113">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1113">See Also</span></span>

- <span data-ttu-id="ee5c6-1114">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1114">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-1115">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1115">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-1116">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1116">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-1117">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1117">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="ee5c6-1118">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1118">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="ee5c6-1119">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1119">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="ee5c6-1120">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1120">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_send"></a><span data-ttu-id="ee5c6-1121">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1121">nx_secure_tls_session_send</span></span>

<span data-ttu-id="ee5c6-1122">Skicka data via en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1122">Send data through a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1123">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1123">Prototype</span></span>

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1124">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1124">Description</span></span>

<span data-ttu-id="ee5c6-1125">Den här tjänsten skickar data i den NX_PACKET, med hjälp av den angivna aktiva TLS-sessionen och hanterar krypteringen av dessa data innan de skickas till fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1125">This service sends data in the supplied NX_PACKET, using the specified active TLS session, and handling the encryption of that data before sending it to the remote host.</span></span> <span data-ttu-id="ee5c6-1126">Om mottagarens senast annonserade fönsterstorlek är mindre än den här begäran, pausar tjänsten eventuellt baserat på de angivna väntealternativen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1126">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait options specified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee5c6-1127">*Om inget fel returneras ska programmet inte släppa paketet efter det här anropet. Detta leder till oförutsägbara resultat eftersom nätverksdrivrutinen släpper paketet efter överföringen.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1127">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1128">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1128">Parameters</span></span>

- <span data-ttu-id="ee5c6-1129">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1129">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-1130">**packet_ptr** Pekare till ett TLS-paket som innehåller data som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1130">**packet_ptr** Pointer to a TLS packet containing data to be sent.</span></span>
- <span data-ttu-id="ee5c6-1131">**wait_option** Definierar hur tjänsten beter sig om begäran är större än mottagarens fönsterstorlek.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1131">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1132">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1132">Return Values</span></span>

- <span data-ttu-id="ee5c6-1133">**NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1133">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="ee5c6-1134">**NX_NO_PACKET** (0x01) Inga data har tagits emot.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1134">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="ee5c6-1135">**NX_NOT_CONNECTED** (0x38) Den underliggande TCP-socketen är inte längre ansluten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1135">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="ee5c6-1136">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka underliggande TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1136">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) The underlying TCP socket send failed.</span></span>
- <span data-ttu-id="ee5c6-1137">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1137">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="ee5c6-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Den angivna TLS-sessionen initierades inte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1139">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1139">Allowed From</span></span>

<span data-ttu-id="ee5c6-1140">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1140">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1141">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1141">Example</span></span>

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1142">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1142">See Also</span></span>

- <span data-ttu-id="ee5c6-1143">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1143">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="ee5c6-1144">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1144">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-1145">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1145">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-1146">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1146">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="ee5c6-1147">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1147">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-1148">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1148">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="ee5c6-1149">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1149">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="ee5c6-1150">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1150">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="ee5c6-1151">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1151">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_server_callback_set"></a><span data-ttu-id="ee5c6-1152">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1152">nx_secure_tls_session_server_callback_set</span></span>

<span data-ttu-id="ee5c6-1153">Konfigurera ett återanrop för TLS som ska anropas i början av en TLS-serverhandskakning</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1153">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1154">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1154">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="ee5c6-1155">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1155">Description</span></span>

<span data-ttu-id="ee5c6-1156">Den här tjänsten tilldelar en funktions pekare till en TLS-session som TLS anropar när en TLS-serverhandskakning har tagit emot ett ClientHello-meddelande.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1156">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Server handshake has received a ClientHello message.</span></span> <span data-ttu-id="ee5c6-1157">Med återanropsfunktionen kan ett program bearbeta alla TLS-tillägg från det mottagna ClientHello-meddelandet som kräver indata eller beslutsfattande.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1157">The callback function allows an application to process any TLS extensions from the received ClientHello message that require input or decision making.</span></span>

<span data-ttu-id="ee5c6-1158">Motringningen körs med det anropande TLS-sessionskontrollblocket och en matris med NX_SECURE_TLS_HELLO_EXTENSION objekt.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1158">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="ee5c6-1159">Matrisen med tilläggsobjekt är avsedd att skickas till en hjälpfunktion som hittar och parsar ett visst tillägg.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1159">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="ee5c6-1160">Ett exempel på en hjälpfunktion som parsar TLS-tillägg som finns i hello messages finns *i nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1160">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="ee5c6-1161">Serveranropet kan också användas för att välja det aktiva identitetscertifikatet *med hjälp nx_secure_tls_active_certificate_set* för TLS-servern.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1161">The server callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Server.</span></span> <span data-ttu-id="ee5c6-1162">Detta inträffar oftast som svar på ett Servernamnindikator-tillägg (SNI) som gör att en TLS-klient kan ange vilken server den försöker kontakta.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1162">This will most often occur in response to a Server Name Indication (SNI) extension which allows a TLS Client to indicate which server it is attempting to contact.</span></span> <span data-ttu-id="ee5c6-1163">Se referenserna för *nx_secure_tls_session_sni_extension_parse* *och nx_secure_tls_active_certificate_set* mer information.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1163">See the references for *nx_secure_tls_session_sni_extension_parse* and *nx_secure_tls_active_certificate_set* for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1164">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1164">Parameters</span></span>

- <span data-ttu-id="ee5c6-1165">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1165">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-1166">**func_ptr** Pekare till funktionen för återanrop av TLS-server.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1166">**func_ptr** Pointer to the TLS Server callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1167">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1167">Return Values</span></span>

- <span data-ttu-id="ee5c6-1168">**NX_SUCCESS** (0x00) Lyckad allokering av funktionspekaren.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1168">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="ee5c6-1169">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1169">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1170">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1170">Allowed From</span></span>

<span data-ttu-id="ee5c6-1171">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1172">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1172">Example</span></span>

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1173">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1173">See Also</span></span>

- <span data-ttu-id="ee5c6-1174">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1174">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-1175">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1175">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="ee5c6-1176">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1176">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="ee5c6-1177">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1177">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="ee5c6-1178">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1178">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="ee5c6-1179">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1179">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_sni_extension_parse"></a><span data-ttu-id="ee5c6-1180">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1180">nx_secure_tls_session_sni_extension_parse</span></span>

<span data-ttu-id="ee5c6-1181">Parsa ett Servernamnindikator (SNI)-tillägg som tagits emot från en TLS-klient</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1181">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1182">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1182">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1183">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1183">Description</span></span>

<span data-ttu-id="ee5c6-1184">Den här tjänsten är avsedd att anropas inifrån en TLS-serversession som läggs till i en TLS-session med nx_secure_tls_session_server_callback_set.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1184">This service is intended to be called from within a TLS Server session callback, added to a TLS session using nx_secure_tls_session_server_callback_set.</span></span> <span data-ttu-id="ee5c6-1185">Motringning anropas efter mottagningen av ett ClientHello-meddelande från en fjärransluten TLS-klient och tillhandahålls en matris med tillgängliga tillägg (och antalet tillägg i matrisen).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1185">The callback is invoked following the reception of a ClientHello message from a remote TLS client and is supplied an array of available extensions (and the number of extensions in the array).</span></span> <span data-ttu-id="ee5c6-1186">Matrisen och dess längd kan skickas direkt till den här rutinen för att avgöra om det finns ett SNI-tillägg – om inte returneras NX_SECURE_TLS_EXTENSION_NOT_FOUND, vilket betyder att klienten valde att inte visa SNI-tillägget (detta är inte ett fel).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1186">That array and its length can be passed directly to this routine to determine if there is an SNI extension present – if not, NX_SECURE_TLS_EXTENSION_NOT_FOUND is returned indicating simply that the client opted not to provice the SNI extension (this is not an error).</span></span>

<span data-ttu-id="ee5c6-1187">Om SNI-tillägget hittas returneras X.509 DNS-namnet som tillhandahålls av TLS-klienten dns_name strukturen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1187">If the SNI extension is found, the X.509 DNS name supplied by the TLS client is returned in the dns_name structure.</span></span> <span data-ttu-id="ee5c6-1188">SNI-tillägget tillhandahåller för närvarande bara en enda DNS-namnpost som kan användas av TLS-servern för att avgöra vilket identitetscertifikat som ska skickas till fjärrklienten.\*\*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1188">Currently, the SNI extension only supplies a single DNS name entry, which may be used by the TLS server to determine which identity certificate to send to the remote client.\*\*</span></span>

<span data-ttu-id="ee5c6-1189">Den NX_SECURE_X509_DNS_NAME strukturen innehåller helt enkelt DNS-namnet som en UCHAR-sträng *i fältet nx_secure_x509_dns_name* och längden på namnsträngen i *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1189">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="ee5c6-1190">Makro-NX_SECURE_X509_DNS_NAME_MAX styr storleken på nx_secure_x509_dns_name bufferten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1190">The macro NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1191">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1191">Parameters</span></span>

- <span data-ttu-id="ee5c6-1192">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1192">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-1193">**tillägg** Pekare till en matris med TLS Hello-tillägg (från sessionsanrop).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1193">**extensions** Pointer to an array of TLS Hello extensions (from session callback).</span></span>
- <span data-ttu-id="ee5c6-1194">**num_extensions** Antal tillägg i matrisen (från sessionsanrop).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1194">**num_extensions** Number of extensions in array (from session callback).</span></span>
- <span data-ttu-id="ee5c6-1195">**dns_name** Returnera DNS-namnet som anges i SNI-tillägget.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1195">**dns_name** Return DNS name supplied in the SNI extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1196">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1196">Return Values</span></span>

- <span data-ttu-id="ee5c6-1197">**NX_SUCCESS** (0x00) Lyckad parsning av tillägget.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1197">**NX_SUCCESS** (0x00) Successful parsing of the extension.</span></span>
- <span data-ttu-id="ee5c6-1198">**NX_PTR_ERROR** (0x07) Ogiltig tilläggsmatris eller TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1198">**NX_PTR_ERROR** (0x07) Invalid extensions array or TLS session pointer.</span></span>
- <span data-ttu-id="ee5c6-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) SNI-tillägg hittades inte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) SNI extension not found.</span></span>
- <span data-ttu-id="ee5c6-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI-tilläggsformatet var ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI extension format was invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1201">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1201">Allowed From</span></span>

<span data-ttu-id="ee5c6-1202">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1203">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1203">Example</span></span>

### <a name="see-also"></a><span data-ttu-id="ee5c6-1204">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1204">See Also</span></span>

- <span data-ttu-id="ee5c6-1205">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1205">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="ee5c6-1206">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1206">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="ee5c6-1207">nx_secure_tls_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1207">nx_secure_tls_server_callback_set</span></span>
- <span data-ttu-id="ee5c6-1208">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1208">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_sni_extension_set"></a><span data-ttu-id="ee5c6-1209">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1209">nx_secure_tls_session_sni_extension_set</span></span>

<span data-ttu-id="ee5c6-1210">Ange ett DNS Servernamnindikator tillägg (SNI) som ska skickas till en fjärrserver</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1210">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1211">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1211">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1212">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1212">Description</span></span>

<span data-ttu-id="ee5c6-1213">Med den här tjänsten kan ett TLS-klientprogram ange ett dns-namn för servern till en fjärransluten TLS-server med hjälp av TLS-tillägget för Servernamnindikator (SNI).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1213">This service allows a TLS Client application to provide a preferred server DNS name to a remote TLS server using the Server Name Indication (SNI) TLS extension.</span></span> <span data-ttu-id="ee5c6-1214">Med SNI-tillägget kan servern välja rätt identitetscertifikat och parametrar baserat på klientens angivna serverpreferenser.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1214">The SNI extension allows the server to select the proper identity certificate and parameters based on the client's indicated server preference.</span></span> <span data-ttu-id="ee5c6-1215">SNI-tillägget stöder för närvarande bara ett enda DNS-namn som ska skickas, därav parametern singular name.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1215">The SNI extension currently only supports a single DNS name to be sent, hence the singular name parameter.</span></span> <span data-ttu-id="ee5c6-1216">Parametern dns_name måste initieras *med nx_secure_x509_dns_name_initialize* och innehåller klientens föredragna server.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1216">The dns_name parameter must be initialized with *nx_secure_x509_dns_name_initialize* and will contain the client's preferred server.</span></span> <span data-ttu-id="ee5c6-1217">Om du vill ta bort namn på tillägget anropar du den här tjänsten med parametervärdet "dns_name" NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1217">To unset the extension name, simply call this service with a "dns_name" parameter value of NX_NULL.</span></span>

<span data-ttu-id="ee5c6-1218">Den NX_SECURE_X509_DNS_NAME strukturen innehåller helt enkelt DNS-namnet som en UCHAR-sträng  *i fältet nx_secure_x509_dns_name* och längden på namnsträngen i *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1218">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field  *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="ee5c6-1219">Makron NX_SECURE_X509_DNS_NAME_MAX kontrollerar storleken på nx_secure_x509_dns_name bufferten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1219">The macro  NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="ee5c6-1220">*Den här rutinen måste anropas nx_secure_tls_session_start anropas, annars innehåller ClientHello inte SNI-tillägget.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1220">*This routine must be called before nx_secure_tls_session_start is invoked or the ClientHello will not contain the SNI extension.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1221">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1221">Parameters</span></span>

- <span data-ttu-id="ee5c6-1222">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1222">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-1223">**dns_name** DNS-namnet som anges av programmet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1223">**dns_name** DNS name supplied by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1224">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1224">Return Values</span></span>

- <span data-ttu-id="ee5c6-1225">**NX_SUCCESS** (0x00) Lyckades tillägg av DNS-servernamnet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1225">**NX_SUCCESS** (0x00) Successful addition of DNS server name.</span></span>
- <span data-ttu-id="ee5c6-1226">**NX_PTR_ERROR** (0x07) Ogiltigt DNS-namn eller TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1226">**NX_PTR_ERROR** (0x07) Invalid DNS name or TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1227">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1227">Allowed From</span></span>

<span data-ttu-id="ee5c6-1228">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1228">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1229">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1229">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1230">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1230">See Also</span></span>

- <span data-ttu-id="ee5c6-1231">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1231">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-1232">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1232">nx_secure_x509_dns_name_initialize</span></span>

## <a name="nx_secure_tls_session_start"></a><span data-ttu-id="ee5c6-1233">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1233">nx_secure_tls_session_start</span></span>

<span data-ttu-id="ee5c6-1234">Starta en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1234">Start a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1235">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1235">Prototype</span></span>

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1236">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1236">Description</span></span>

<span data-ttu-id="ee5c6-1237">Den här tjänsten startar en TLS-session med hjälp av det angivna TLS-sessionskontrollblocket och en ansluten TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1237">This service starts a TLS session using the supplied TLS session control block and a connected TCP socket.</span></span> <span data-ttu-id="ee5c6-1238">TCP-anslutningen måste redan slutföras efter ett lyckat anrop till antingen nx_tcp_client_socket_connect eller nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1238">The TCP connection must already be complete following a successful call to either nx_tcp_client_socket_connect or nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="ee5c6-1239">Den här tjänsten avgör typen av TLS-session (klient eller server) från TCP-socketen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1239">This service will determine the type of TLS session (Client or Server) from the TCP socket.</span></span>

<span data-ttu-id="ee5c6-1240">Väntealternativet definierar hur tjänsten beter sig medan TLS-handskakningen pågår.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1240">The wait option defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1241">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1241">Parameters</span></span>

- <span data-ttu-id="ee5c6-1242">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1242">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-1243">**tcp_socket_ptr** Pekare till en ansluten TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1243">**tcp_socket_ptr** Pointer to a connected TCP socket.</span></span>
- <span data-ttu-id="ee5c6-1244">**wait_option** Definierar hur tjänsten beter sig medan TLS-handskakningen pågår.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1244">**wait_option** Defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1245">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1245">Return Values</span></span>

- <span data-ttu-id="ee5c6-1246">**NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1246">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="ee5c6-1247">**NX_NOT_CONNECTED** (0x38) Den underliggande TCP-socketen är inte längre ansluten.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1247">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="ee5c6-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) En mottagen TLS-meddelandetyp är felaktig.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="ee5c6-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Chiffer som tillhandahålls av fjärrvärden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="ee5c6-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Meddelandebearbetningen under TLS-handskakningen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="ee5c6-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Ett inkommande meddelande misslyckades med en hash-MAC-kontroll.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="ee5c6-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka en underliggande TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="ee5c6-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Ett inkommande meddelande hade ett ogiltigt längdfält.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="ee5c6-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) Ett inkommande ChangeCipherSpec-meddelande var felaktigt.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="ee5c6-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Ett inkommande TLS-certifikat kan inte användas för att identifiera TLS-fjärrservern.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="ee5c6-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Chiffer med offentlig nyckel som tillhandahålls av fjärrvärden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="ee5c6-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Fjärrvärden har inte angett några chiffer som stöds av NetX Secure TLS-stacken.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="ee5c6-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Ett mottaget TLS-meddelande hade en okänd TLS-version i huvudet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="ee5c6-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Ett mottaget TLS-meddelande hade en känd men inte stöds TLS-version i huvudet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="ee5c6-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) En intern TLS-paketallokering misslyckades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="ee5c6-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Fjärrvärden tillhandahöll ett ogiltigt certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="ee5c6-1262">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Fjärrvärden skickade en avisering som anger ett fel och avslutar TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1262">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="ee5c6-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) En post i chiffertabellen hade en NULL-funktionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="ee5c6-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) En fjärransluten TLS ClientHello innehöll återställnings-SCSV och ett återställningsförsök för en version.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) A remote TLS ClientHello included the fallback SCSV andattempted a version fallback.</span></span>
- <span data-ttu-id="ee5c6-1265">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1265">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1266">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1266">Allowed From</span></span>

<span data-ttu-id="ee5c6-1267">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1268">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1268">Example</span></span>

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1269">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1269">See Also</span></span>

- <span data-ttu-id="ee5c6-1270">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1270">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="ee5c6-1271">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1271">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-1272">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1272">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-1273">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1273">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="ee5c6-1274">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1274">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="ee5c6-1275">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1275">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="ee5c6-1276">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1276">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="ee5c6-1277">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1277">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="ee5c6-1278">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1278">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-1279">nx_tcp_socket_accept</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1279">nx_tcp_socket_accept</span></span>
- <span data-ttu-id="ee5c6-1280">nx_tcp_socket_listen</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1280">nx_tcp_socket_listen</span></span>
- <span data-ttu-id="ee5c6-1281">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1281">nx_tcp_socket_disconnect</span></span>
- <span data-ttu-id="ee5c6-1282">nx_tcp_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1282">nx_tcp_socket_unaccept</span></span>
- <span data-ttu-id="ee5c6-1283">nx_tcp_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1283">nx_tcp_socket_relisten</span></span>
- <span data-ttu-id="ee5c6-1284">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1284">nx_tcp_socket_delete</span></span>
- <span data-ttu-id="ee5c6-1285">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1285">nx_packet_allocate</span></span>
- <span data-ttu-id="ee5c6-1286">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1286">nx_packet_data_append</span></span>
- <span data-ttu-id="ee5c6-1287">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1287">nx_packet_data_extract_offset</span></span>

## <a name="nx_secure_tls_session_time_function_set"></a><span data-ttu-id="ee5c6-1288">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1288">nx_secure_tls_session_time_function_set</span></span>

<span data-ttu-id="ee5c6-1289">Tilldela en tidsstämpelfunktion till en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1289">Assign a timestamp function to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1290">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1290">Prototype</span></span>

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a><span data-ttu-id="ee5c6-1291">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1291">Description</span></span>

<span data-ttu-id="ee5c6-1292">Den här funktionen ställer in en funktionspekare som TLS anropar när den behöver hämta den aktuella tiden, som används i olika TLS-handskakningsmeddelanden och för verifiering av certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1292">This function sets up a function pointer that TLS will invoke when it needs to get the current time, which is used in various TLS handshake messages and for verification of certificates.</span></span>

<span data-ttu-id="ee5c6-1293">Funktionen förväntas returnera aktuell GMT i UNIX-32-bitarsformat (sekunder sedan midnatt från den 1 januari 1970, UTC, ignorerar skottsekunder), enligt ClientHello-kraven i TLS RFC 5246.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1293">The function is expected to return the current GMT in UNIX 32-bit format (seconds since the midnight starting Jan 1, 1970, UTC, ignoring leap seconds), as per the ClientHello requirements in the TLS RFC 5246.</span></span>

<span data-ttu-id="ee5c6-1294">Om ingen tidsstämpelfunktion tilldelas används värdet 0 för tidsstämpeln i TLS-handskakningen och kontrollen av förfallodatum för certifikat fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1294">If no timestamp function is assigned, a value of 0 for the timestamp in the TLS handshake will be used and certificate expiration checking will not work.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1295">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1295">Parameters</span></span>

- <span data-ttu-id="ee5c6-1296">**session_ptr** Pekare till en TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1296">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-1297">**time_func_ptr** Pekare till en funktion som returnerar den aktuella tiden (GMT) i UNIX 32-bitarsformat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1297">**time_func_ptr** Pointer to a function that returns the current time (GMT) in UNIX 32-bit format.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1298">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1298">Return Values</span></span>

- <span data-ttu-id="ee5c6-1299">**NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1299">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="ee5c6-1300">**NX_INVALID_PARAMETERS** (0x4D) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1300">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="ee5c6-1301">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1301">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1302">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1302">Allowed From</span></span>

<span data-ttu-id="ee5c6-1303">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1303">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1304">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1304">Example</span></span>

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1305">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1305">See Also</span></span>

- <span data-ttu-id="ee5c6-1306">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1306">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-1307">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1307">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-1308">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1308">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="ee5c6-1309">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1309">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="ee5c6-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span></span>
- <span data-ttu-id="ee5c6-1311">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1311">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_trusted_certificate_add"></a><span data-ttu-id="ee5c6-1312">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1312">nx_secure_tls_trusted_certificate_add</span></span>

<span data-ttu-id="ee5c6-1313">Lägga till betrott certifikat i NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1313">Add trusted certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1314">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1314">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1315">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1315">Description</span></span>

<span data-ttu-id="ee5c6-1316">Den här tjänsten lägger till en NX_SECURE_X509_CERT instans av en struktur i en TLS-session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1316">This service adds an initialized NX_SECURE_X509_CERT structure instance to a TLS session.</span></span> <span data-ttu-id="ee5c6-1317">Det här certifikatet används av TLS-stacken för att verifiera certifikat som tillhandahålls av fjärrvärden under TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1317">This certificate is used by the TLS stack to verify certificates supplied by the remote host during the TLS handshake.</span></span>

<span data-ttu-id="ee5c6-1318">Betrodda certifikat krävs för TLS-klientläge.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1318">Trusted certificates are required for TLS Client mode.</span></span>

<span data-ttu-id="ee5c6-1319">Betrodda certifikat krävs endast för TLS-serverläge om autentisering med klientcertifikat är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1319">Trusted certificates are only required for TLS Server mode if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1320">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1320">Parameters</span></span>

- <span data-ttu-id="ee5c6-1321">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1321">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-1322">**certificate_ptr** Pekare till en initierad TLS-certifikatinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1322">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1323">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1323">Return Values</span></span>

- <span data-ttu-id="ee5c6-1324">**NX_SUCCESS** (0x00) Lyckad tillägg av certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1324">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="ee5c6-1325">**NX_INVALID_PARAMETERS** (0x4D) Försökte lägga till ett ogiltigt certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1325">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>
- <span data-ttu-id="ee5c6-1326">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1326">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1327">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1327">Allowed From</span></span>

<span data-ttu-id="ee5c6-1328">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1329">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1329">Example</span></span>

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1330">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1330">See Also</span></span>

- <span data-ttu-id="ee5c6-1331">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1331">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-1332">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1332">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-1333">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1333">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-1334">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1334">nx_secure_tls_trusted_certificate_remove</span></span>

## <a name="nx_secure_tls_trusted_certificate_remove"></a><span data-ttu-id="ee5c6-1335">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1335">nx_secure_tls_trusted_certificate_remove</span></span>

<span data-ttu-id="ee5c6-1336">Ta bort betrott certifikat från NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1336">Remove trusted certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1337">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1337">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1338">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1338">Description</span></span>

<span data-ttu-id="ee5c6-1339">Den här tjänsten tar bort ett betrott certifikat från en TLS-session som är nyckelad i fältet Eget namn i certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1339">This service removes a trusted certificate from a TLS session, keyed on the Common Name field in the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1340">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1340">Parameters</span></span>

- <span data-ttu-id="ee5c6-1341">**session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1341">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="ee5c6-1342">**common_name** Värdet för Eget namn för certifikatet som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1342">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="ee5c6-1343">**common_name_length** Längden på strängen Eget namn.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1343">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1344">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1344">Return Values</span></span>

- <span data-ttu-id="ee5c6-1345">**NX_SUCCESS** (0x00) Lyckad tillägg av certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="ee5c6-1346">**NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1346">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="ee5c6-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det gick inte att hitta certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1348">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1348">Allowed From</span></span>

<span data-ttu-id="ee5c6-1349">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1350">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1350">Example</span></span>

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1351">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1351">See Also</span></span>

- <span data-ttu-id="ee5c6-1352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="ee5c6-1353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-1354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-1355">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1355">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_x509_certificate_initialize"></a><span data-ttu-id="ee5c6-1356">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1356">nx_secure_x509_certificate_initialize</span></span>

<span data-ttu-id="ee5c6-1357">Initiera X.509-certifikat för NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1357">Initialize X.509 Certificate for NetX Secure TLS</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1358">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1358">Prototype</span></span>

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1359">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1359">Description</span></span>

<span data-ttu-id="ee5c6-1360">Den här tjänsten initierar NX_SECURE_X509_CERT en struktur från ett binärt kodat digitalt X.509-certifikat för användning i en TLS-session.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1360">This service initializes an NX_SECURE_X509_CERT structure from a binary-encoded X.509 digital certificate for use in a TLS session.</span></span>

<span data-ttu-id="ee5c6-1361">Certifikatdata måste **vara** ett giltigt digitalt X.509-certifikat i DER-kodat binärt format.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1361">The certificate data **must** be a valid X.509 digital certificate in DER-encoded binary format.</span></span> <span data-ttu-id="ee5c6-1362">Data kan komma från valfri källa (t.ex. filsystem, kompilerad konstant buffert osv.) så länge en UCHAR-pekare till dessa data tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1362">The data can some from any source (e.g. file system, compiled constant buffer, etc.) as long as a UCHAR pointer to that data is provided.</span></span>

<span data-ttu-id="ee5c6-1363">Parametern *raw_data_buffer* och dess storlek är valfria parametrar som anger en dedikerad buffert som certifikatdata kopieras till innan parsning.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1363">The *raw_data_buffer* parameter and its size are optional parameters that specify a dedicated buffer into which the certificate data is copied before parsing.</span></span> <span data-ttu-id="ee5c6-1364">Om raw_data_buffer skickas som NX_NULL pekar NX_SECURE_X509_CERT struktur direkt i certificate_data -matrisen (i det buffer_size fallet ignoreras den).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1364">If raw_data_buffer is passed as NX_NULL then the NX_SECURE_X509_CERT structure will point directly into the certificate_data array (buffer_size is ignored in this case).</span></span> <span data-ttu-id="ee5c6-1365">Om raw_data_buffer skickas som NX_NULL ***ska*** du inte ändra de data som pekar certificate_data pekaren eller certifikatbearbetningen kommer troligen att misslyckas!</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1365">If raw_data_buffer is passed as NX_NULL, ***do not*** modify the data pointed to by the certificate_data pointer or certificate processing will likely fail!</span></span>

<span data-ttu-id="ee5c6-1366">Den privata nyckelparametern gäller för lokala identitetscertifikat – den privata nyckeln används av servrar för att dekryptera inkommande nyckeldata från en klient (krypterade med serverns offentliga nyckel) och av klienter för att verifiera sin identitet till en server när servern begär ett klientcertifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1366">The private key parameter is for local identity certificates – the private key is used by servers to decrypt the incoming key data from a client (encrypted using the server's public key) and by clients to verify their identity to a server when the server requests a client certificate.</span></span> <span data-ttu-id="ee5c6-1367">Om du lägger till en privat nyckel med det här API:et markeras det associerade certifikatet automatiskt som ett identitetscertifikat för ett TLS-program.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1367">Adding a private key with this API will automatically mark the associated certificate as being an identity certificate for a TLS application.</span></span> <span data-ttu-id="ee5c6-1368">När du initierar certifikat för andra syften (t.ex. det betrodda arkivet) ska *private_key_data-parametern* skickas som NULL, *private_key_data_length* som 0 och *private_key_type* ska skickas som NX_SECURE_X509_KEY_TYPE_NONE.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1368">When initializing certificates for other purposes (e.g. the trusted store), the *private_key_data* parameter should be passed as NULL, the *private_key_data_length* as 0, and the *private_key_type* should be passed as NX_SECURE_X509_KEY_TYPE_NONE.</span></span>

<span data-ttu-id="ee5c6-1369">Parametern *private_key_type* anger formateringen av den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1369">The *private_key_type* parameter indicates the formatting of the private key.</span></span> <span data-ttu-id="ee5c6-1370">Om den privata nyckeln till exempel är en PRIVAT RSA-nyckel med DER-kodad PKCS#1-format ska private_key_type skickas som NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, en typ som är känd för NetX Secure som parsas omedelbart och sparas för senare användning.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1370">For example, if the private key is a DER-encoded PKCS#1-format RSA private key, the private_key_type should be passed as NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, a type known to NetX Secure which will be parsed immediately and saved for later use.</span></span>

<span data-ttu-id="ee5c6-1371">Den private_key_type också stöd för användardefinierade nyckeltyper<sup>23</sup> för plattformar och program som har specifika nyckelformat eller andra behov.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1371">The private_key_type also supports user-defined key types<sup>23</sup> for platforms and applications that have specific key formats or other needs.</span></span> <span data-ttu-id="ee5c6-1372">En maskinvarubaserad krypteringsmotor kan till exempel använda ett visst format som inte kan tolkas av NetX Secure-programvaran, eller så kan en privat nyckel krypteras eller representeras av en kryptografitoken, vilket kan vara fallet med en kryptografisk Trusted Platform Module (TPM) eller PKCS#11-maskinvara.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1372">For example, a hardware-based encryption engine may use a specific format not understood by the NetX Secure software, or a private key may be encrypted or represented by a cryptographic token as might be the case with a Trusted Platform Module (TPM) or PKCS#11 cryptographic hardware.</span></span> <span data-ttu-id="ee5c6-1373">När en användardefinierad nyckeltyp används skickas nyckeldata ordagrant till lämplig kryptografirutin. Till exempel skulle en privat RSA-nyckel skickas, utan parsning eller bearbetning, direkt till den kryptografiska RSA-rutinen som tillhandahålls till TLS i chiffersvittabellen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1373">When a user-defined key type is used, the key data is passed verbatim to the appropriate cryptographic routine - for example, an RSA private key would be passed, without any parsing or processing, directly to the RSA cryptographic routine provided to TLS in the ciphersuite table.</span></span> <span data-ttu-id="ee5c6-1374">Den användardefinierade nyckeltypen skickas också till den kryptografiska rutinen (när det gäller RSA är det här parametern "op").</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1374">The user-defined key type is also passed to the cryptographic routine (in the case of RSA, this is the "op" parameter).</span></span>

<span data-ttu-id="ee5c6-1375">Intervallet med användardefinierade nycklar omfattar den övre halvan av ett 32-bitars heltal utansignerat heltal, från 0x0001 0000-0xFFFF FFFF.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1375">The range of user-defined keys covers the top half of a 32-bit unsigned integer, from 0x0001 0000-0xFFFF FFFF.</span></span> <span data-ttu-id="ee5c6-1376">Värden som är mindre 0x0001 0000 är reserverade för NetX Secure-användning.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1376">Values less than 0x0001 0000 are reserved for NetX Secure use.</span></span>

<span data-ttu-id="ee5c6-1377">Användardefinierade nyckeltyper är en avancerad funktion som kräver anpassade kryptografiska rutiner för att hantera rådata för privata nycklar.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1377">User-defined key types are an advanced feature that requires custom cryptographic routines to handle the raw private key data.</span></span> <span data-ttu-id="ee5c6-1378">Kontakta din Express Logic-representant om du behöver den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1378">Please contact your Express Logic representative if you have need of this feature.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1379">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1379">Parameters</span></span>

- <span data-ttu-id="ee5c6-1380">**certificate_ptr** Pekare till en oiniterad X.509-certifikatinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1380">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="ee5c6-1381">**certificate_data** Pekare till DER-kodade X.509-binära data.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1381">**certificate_data** Pointer to DER-encoded X.509 binary data.</span></span>
- <span data-ttu-id="ee5c6-1382">**raw_data_buffer** Pekare till valfri dedikerad certifikatdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1382">**raw_data_buffer** Pointer to optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="ee5c6-1383">**buffer_size** Storleken på valfri dedikerad certifikatdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1383">**buffer_size** Size of optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="ee5c6-1384">**certificate_data_length** Längden på binära certifikatdata i byte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1384">**certificate_data_length** Length of certificate binary data in bytes.</span></span>
- <span data-ttu-id="ee5c6-1385">**private_key_data** Pekare till valfria privata nyckeldata.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1385">**private_key_data** Pointer to optional private key data.</span></span>
- <span data-ttu-id="ee5c6-1386">**private_key_data_length** Längden på privata nyckeldata.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1386">**private_key_data_length** Length of private key data.</span></span>
- <span data-ttu-id="ee5c6-1387">**private_key_type** Nyckeltypsidentifierare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1387">**private_key_type** Key type identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1388">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1388">Return Values</span></span>

- <span data-ttu-id="ee5c6-1389">**NX_SUCCESS** (0x00) Ett lyckat tillägg av certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1389">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="ee5c6-1390">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1390">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="ee5c6-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certifikatdata innehöll inte ett DER-kodat X.509-certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certificate data did not contain a DER-encoded X.509 certificate.</span></span>
- <span data-ttu-id="ee5c6-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D)-certifikatet hade inget chiffer med offentlig nyckel som stöds av NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Certificate did not have a public-key cipher that is supported by NetX Secure.</span></span>
- <span data-ttu-id="ee5c6-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Privat nyckel eller certifikat innehöll inte en giltig ASN.1-sekvens.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Private key or certificate did not contain a valid ASN.1 sequence.</span></span>
- <span data-ttu-id="ee5c6-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) Den angivna privata nyckeln var inte en giltig PKCS#1 RSA-nyckel.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) The provided private key was not a valid PKCS#1 RSA key.</span></span>
- <span data-ttu-id="ee5c6-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) Den angivna privata nyckeltypen var inte användardefinierad och matchade inte någon känd typ.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) The private key type provided was not user-defined and did not match any known type.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1396">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1396">Allowed From</span></span>

<span data-ttu-id="ee5c6-1397">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1398">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1398">Example</span></span>

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1399">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1399">See Also</span></span>

- <span data-ttu-id="ee5c6-1400">nx_secure_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1400">nx_secure_local_certificate_add</span></span>
- <span data-ttu-id="ee5c6-1401">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1401">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-1402">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1402">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="ee5c6-1403">Importera X.509-certifikat till NetX Secure i kapitel 3.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1403">Importing X.509 Certificates into NetX Secure in Chapter 3.</span></span>

## <a name="nx_secure_x509_common_name_dns_check"></a><span data-ttu-id="ee5c6-1404">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1404">nx_secure_x509_common_name_dns_check</span></span>

<span data-ttu-id="ee5c6-1405">Kontrollera DNS-namn mot X.509-certifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1405">Check DNS name against X.509 Certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1406">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1406">Prototype</span></span>

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1407">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1407">Description</span></span>

<span data-ttu-id="ee5c6-1408">Den här tjänsten kontrollerar ett certifikats eget namn mot ett toppdomännamn (TLD) som tillhandahålls av anroparen i syfte att DNS-verifiering av en fjärrvärd.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1408">This service checks a certificate's Common Name against a Top- Domain name (TLD) provided by the caller for the purposes of DNS validation of a remote host.</span></span> <span data-ttu-id="ee5c6-1409">Den här verktygsfunktionen är avsedd att anropas inifrån en återanropsrutin för certifikatverifiering som tillhandahålls av programmet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1409">This utility function is intended to be called from within a certificate validation callback routine provided by the application.</span></span> <span data-ttu-id="ee5c6-1410">TLD-namnet ska vara den översta delen av URL:en som används för att komma åt fjärrvärden (.) -avgränsad sträng före det första snedstrecket).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1410">The TLD name should be the top part of the URL used to access the remote host (the "."-separated string before the first slash).</span></span> <span data-ttu-id="ee5c6-1411">Om eget namn innehåller ett jokertecken (till exempel .example.com) matchar jokertecknet alla med *samma suffix. Observera att* endast det första jokertecknet (" ") som påträffas (läsning från höger till vänster) beaktas för  matchning av jokertecken – till exempel matchar abc.\*.example.com alla namn som slutar på ".example.com".</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1411">If the Common Name contains a wildcard (such as *.example.com), the wildcard will match any with the same suffix. Note that only the first wildcard ("*") encountered (reading right-to-left) will be considered for wildcard matching – for example, abc.\*.example.com will match *any* name ending in ".example.com".</span></span>

<span data-ttu-id="ee5c6-1412">Om det gemensamma namnet inte matchar den angivna strängen parsas tillägget "subjectAltName" (om det finns i certifikatet) och eventuella DNSName-poster jämförs också.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1412">If the Common Name does not match the provided string, the "subjectAltName" extension is parsed (if it exists in the certificate) and any DNSName entries are also compared.</span></span> <span data-ttu-id="ee5c6-1413">Om ingen av dessa poster matchar returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1413">If none of those entries match, an error is returned.</span></span>

<span data-ttu-id="ee5c6-1414">Det är viktigt att förstå formatet för eget namn (och subjectAltName-poster) i förväntade certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1414">It is important to understand the format of the common name (and subjectAltName entries) in expected certificates.</span></span> <span data-ttu-id="ee5c6-1415">Vissa certifikat kan till exempel använda en rå IP-adress eller ett jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1415">For example, some certificates may use a raw IP address or a wild card.</span></span> <span data-ttu-id="ee5c6-1416">DNS TLD-strängen måste vara formaterad så att den matchar förväntade värden i mottagna certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1416">The DNS TLD string must be formatted such that it will match the expected values in received certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1417">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1417">Parameters</span></span>

- <span data-ttu-id="ee5c6-1418">**certificate_ptr** Pekare till en X.509-certifikatinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1418">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>
- <span data-ttu-id="ee5c6-1419">**dns_tld** Top-Level domännamn att jämföra med.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1419">**dns_tld** Top-Level Domain name to compare against.</span></span>
- <span data-ttu-id="ee5c6-1420">**dns_tld_length** Längden på TLD-strängen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1420">**dns_tld_length** Length of TLD string.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1421">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1421">Return Values</span></span>

- <span data-ttu-id="ee5c6-1422">**NX_SUCCESS** (0x00) Lyckad jämförelse med Eget namn eller subjectAltName.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1422">**NX_SUCCESS** (0x00) Successful comparison with Common Name or subjectAltName.</span></span>
- <span data-ttu-id="ee5c6-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) Inget matchande namn hittades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) No matching name found.</span></span>
- <span data-ttu-id="ee5c6-1424">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1424">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1425">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1425">Allowed From</span></span>

<span data-ttu-id="ee5c6-1426">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1426">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1427">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1427">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1428">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1428">See Also</span></span>

- <span data-ttu-id="ee5c6-1429">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1429">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-1430">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1430">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="ee5c6-1431">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1431">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_x509_crl_revocation_check"></a><span data-ttu-id="ee5c6-1432">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1432">nx_secure_x509_crl_revocation_check</span></span>

<span data-ttu-id="ee5c6-1433">Kontrollera X.509-certifikat mot en agen lista över återkallade certifikat (CRL)</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1433">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1434">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1434">Prototype</span></span>

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1435">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1435">Description</span></span>

<span data-ttu-id="ee5c6-1436">Den här tjänsten tar en DER-kodad lista över återkallade certifikat och söker efter ett specifikt certifikat i listan.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1436">This service takes a DER-encoded Certificate Revocation List and searches for a specific certificate in that list.</span></span> <span data-ttu-id="ee5c6-1437">Utfärdaren av listan över återkallade certifikat verifieras mot ett ansett certifikatarkiv, CRL-utfärdaren verifieras att vara samma som den för certifikatet som kontrolleras och serienumret för certifikatet i fråga används för att söka i listan över återkallade certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1437">The issuer of the CRL is validated against a supplied certificate store, the CRL issuer is validated to be the same as the one for the certificate being checked, and the serial number of the certificate in question is used to search the revoked certificates list.</span></span> <span data-ttu-id="ee5c6-1438">Om utfärdarna matchar, signaturen checkar ut och certifikatet **inte finns** i listan, lyckas anropet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1438">If the issuers match, the signature checks out, and the certificate is **not** present in the list, the call is successful.</span></span> <span data-ttu-id="ee5c6-1439">Alla andra fall gör att ett fel returneras.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1439">All other cases cause an error to be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1440">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1440">Parameters</span></span>

- <span data-ttu-id="ee5c6-1441">**crl_data** Pekare till en DER-kodad CRL.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1441">**crl_data** Pointer to a DER-encoded CRL.</span></span>
- <span data-ttu-id="ee5c6-1442">**crl_length** Längd i byte för CRL-data.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1442">**crl_length** Length in bytes of CRL data.</span></span>
- <span data-ttu-id="ee5c6-1443">**store** Pekare till ett X.509-certifikatarkiv.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1443">**store** Pointer to an X.509 Certificate store.</span></span>
- <span data-ttu-id="ee5c6-1444">**certificate_ptr** Pekare till en X.509-certifikatinstans.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1444">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1445">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1445">Return Values</span></span>

- <span data-ttu-id="ee5c6-1446">**NX_SUCCESS** (0x00) Lyckad validering av att certifikatet inte återkallades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1446">**NX_SUCCESS** (0x00) Successful validation that the certificate was not revoked.</span></span>
- <span data-ttu-id="ee5c6-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) det går inte att hitta certifikatutfärdaren för listan över återkallade certifikat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) CRL issuer certificate not found.</span></span>
- <span data-ttu-id="ee5c6-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Det går inte att hitta certifikatets certifikatutfärdare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Certificate issuer certificate not found.</span></span>
- <span data-ttu-id="ee5c6-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) CRL ASN.1 innehöll ett ogiltigt längdfält.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) The CRL ASN.1 contained an invalid length field.</span></span>
- <span data-ttu-id="ee5c6-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** Listan över återkallade certifikat innehöll ogiltig ASN.1.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** The CRL contained invalid ASN.1.</span></span>
- <span data-ttu-id="ee5c6-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) Verifieringen av certifikatkedjan misslyckades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) A certificate chain verification failed.</span></span>
- <span data-ttu-id="ee5c6-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL och certifikatutfärdare matchade inte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL and certificate issuers did not match.</span></span>
- <span data-ttu-id="ee5c6-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) CRL-signaturen var ogiltig.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) The CRL signature was invalid.</span></span>
- <span data-ttu-id="ee5c6-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) Certifikatet som kontrolleras hittades i listan över återkallade certifikat och återkallas därför.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) The certificate being checked was found in the CRL and is therefore revoked.</span></span>
- <span data-ttu-id="ee5c6-1455">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1455">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1456">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1456">Allowed From</span></span>

<span data-ttu-id="ee5c6-1457">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1457">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1458">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1458">Example</span></span>

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1459">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1459">See Also</span></span>

- <span data-ttu-id="ee5c6-1460">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1460">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-1461">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1461">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="ee5c6-1462">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1462">nx_secure_x509_common_name_dns_check</span></span>

## <a name="nx_secure_x509_dns_name_initialize"></a><span data-ttu-id="ee5c6-1463">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1463">nx_secure_x509_dns_name_initialize</span></span>

<span data-ttu-id="ee5c6-1464">Initiera en X.509 DNS-namnstruktur</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1464">Initialize an X.509 DNS name structure</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1465">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1465">Prototype</span></span>

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1466">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1466">Description</span></span>

<span data-ttu-id="ee5c6-1467">Den här tjänsten initierar ett X.509 DNS-namn för användning med vissa API-tjänster som kräver ett visst namnformat.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1467">This service initializes an X.509 DNS name for use with certain API services requiring a specific name format.</span></span> <span data-ttu-id="ee5c6-1468">Till exempel *förväntar nx_secure_tls_sni_extension_parse tjänsten* ett NX_SECURE_X509_DNS_NAME-objekt för att matcha namnet som tillhandahålls av en fjärrvärd i Servernamnindikator-tillägget under TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1468">For example, the *nx_secure_tls_sni_extension_parse* service expects an NX_SECURE_X509_DNS_NAME object in order to match the name provided by a remote host in the Server Name Indication extension during the TLS handshake.</span></span> <span data-ttu-id="ee5c6-1469">Ett DNS-namn är helt enkelt en teckensträng med en längd – den maximala tillåtna längden för ett DNS-namn (och storleken på den interna bufferten i NX_SECURE_X509_DNS_NAME) styrs av makro-NX_SECURE_X509_DNS_NAME_MAX (standardvärdet är 100 byte).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1469">A DNS name is simply a charater string with a length – the maximum allowed length of a DNS name (and the size of the internal buffer in NX_SECURE_X509_DNS_NAME) is controlled by the macro NX_SECURE_X509_DNS_NAME_MAX (default 100 bytes).</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1470">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1470">Parameters</span></span>

- <span data-ttu-id="ee5c6-1471">**dns_name** DNS-namnstruktur som ska initieras.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1471">**dns_name** DNS name structure to initialize.</span></span>
- <span data-ttu-id="ee5c6-1472">**name_string** DNS-namnsträngsdata.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1472">**name_string** DNS name string data.</span></span>
- <span data-ttu-id="ee5c6-1473">**längd** Längden på namnsträngen.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1473">**length** Length of name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1474">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1474">Return Values</span></span>

- <span data-ttu-id="ee5c6-1475">**NX_SUCCESS** (0x00) Lyckad initiering.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1475">**NX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="ee5c6-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) Den angivna namnsträngen överskreds NX_SECURE_X509_DNS_NAME_MAX.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) The given name string exceeded NX_SECURE_X509_DNS_NAME_MAX.</span></span>
- <span data-ttu-id="ee5c6-1477">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1477">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1478">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1478">Allowed From</span></span>

<span data-ttu-id="ee5c6-1479">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1480">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1480">Example</span></span>

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1481">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1481">See Also</span></span>

- <span data-ttu-id="ee5c6-1482">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1482">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="ee5c6-1483">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1483">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="ee5c6-1484">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1484">nx_secure_tls_session_sni_extension_set</span></span>

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a><span data-ttu-id="ee5c6-1485">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1485">nx_secure_x509_extended_key_usage_extension_parse</span></span>

<span data-ttu-id="ee5c6-1486">Hitta och parsa ett utökat X.509-nyckelanvändningstillägg i ett X.509-certifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1486">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1487">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1487">Prototype</span></span>

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1488">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1488">Description</span></span>

<span data-ttu-id="ee5c6-1489">Den här tjänsten är avsedd att anropas inifrån ett återanrop för certifikatverifiering *(se nx_secure_tls_session_certificate_callback_set).*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1489">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="ee5c6-1490">Den söker efter ett specifikt utökat nyckelanvändnings-OID i ett X.509-certifikat och returnerar om OID:t finns.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1490">It will search for a specific extended key usage OID within an X.509 certificate and return whether the OID is present.</span></span> <span data-ttu-id="ee5c6-1491">Parametern key_usage är en heltalsmappning av OID:erna som används internt av NetX Secure X.509 och TLS för att undvika att OID-strängar med variabel längd anges som parametrar.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1491">The key_usage parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="ee5c6-1492">Relevanta OID:er för tillägget för utökad nyckelanvändning anges i tabellen nedan.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1492">The relevant OIDs for the extended key usage extension are given in the table below.</span></span> <span data-ttu-id="ee5c6-1493">En typisk TLS-klientimplementering som vill kontrollera användningen av utökad nyckel i ett mottaget TLS-servercertifikat skulle kontrollera om OID-NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH finns . Om tillägget finns men inte OID:n skulle certifikatet anses vara ogiltigt för att identifiera värden som en TLS-server och återanropet för certifikatverifiering bör returnera ett fel.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1493">A typical TLS Client implementation wishing to check extended key usage in a received TLS server certificate would check for the existence of the OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH – if the extension is present but that OID is not, then the certificate would be considered invalid for identifiying the host as a TLS server and the certificate verification callback should return an error.</span></span> <span data-ttu-id="ee5c6-1494">Om själva tillägget saknas är det upp till programmet om TLS-handskakningen ska fortsätta eller inte.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1494">If the extension itself is missing, then it is up to the application whether or not to proceed with the TLS handshake.</span></span>

<span data-ttu-id="ee5c6-1495">I återanropet för certifikatverifiering är felreturkoden NX_SECURE_X509_KEY_USAGE_ERROR reserverad för programanvändning.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1495">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="ee5c6-1496">Om det uppstår ett fel vid kontroll av nyckelanvändning kan det här värdet returneras från återanropet för att ange orsaken till felet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1496">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="ee5c6-1497">NetX Secure Identifier</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1497">NetX Secure Identifier</span></span>                                | <span data-ttu-id="ee5c6-1498">OID-värde</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1498">OID Value</span></span>         | <span data-ttu-id="ee5c6-1499">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1499">Description</span></span>                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| <span data-ttu-id="ee5c6-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span></span>   | <span data-ttu-id="ee5c6-1501">1.3.6.1.5.5.7.3.1</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1501">1.3.6.1.5.5.7.3.1</span></span> | <span data-ttu-id="ee5c6-1502">Certifikatet kan användas för att identifiera en TLS-server</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1502">Certificate can be used to identify a TLS server</span></span> |
| <span data-ttu-id="ee5c6-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span></span>   | <span data-ttu-id="ee5c6-1504">1.3.6.1.5.5.7.3.2</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1504">1.3.6.1.5.5.7.3.2</span></span> | <span data-ttu-id="ee5c6-1505">Certifikatet kan användas för att identifiera en TLS-klient</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1505">Certificate can be used to identify a TLS client</span></span> |
| <span data-ttu-id="ee5c6-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span></span>  | <span data-ttu-id="ee5c6-1507">1.3.6.1.5.5.7.3.3</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1507">1.3.6.1.5.5.7.3.3</span></span> | <span data-ttu-id="ee5c6-1508">Certifikatet kan användas för att signera kod</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1508">Certificate can be used to sign code</span></span>             |
| <span data-ttu-id="ee5c6-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span></span> | <span data-ttu-id="ee5c6-1510">1.3.6.1.5.5.7.3.4</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1510">1.3.6.1.5.5.7.3.4</span></span> | <span data-ttu-id="ee5c6-1511">Certifikatet kan användas för att signera e-post</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1511">Certificate can be used to sign emails</span></span>           |
| <span data-ttu-id="ee5c6-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span></span> | <span data-ttu-id="ee5c6-1513">1.3.6.1.5.5.7.3.8</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1513">1.3.6.1.5.5.7.3.8</span></span> | <span data-ttu-id="ee5c6-1514">Certifikatet kan användas för att signera tidsstämplar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1514">Certificate can be used to sign timestamps</span></span>       |
| <span data-ttu-id="ee5c6-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span></span>  | <span data-ttu-id="ee5c6-1516">1.3.6.1.5.5.7.3.9</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1516">1.3.6.1.5.5.7.3.9</span></span> | <span data-ttu-id="ee5c6-1517">Certifikatet kan användas för att signera OCSP-svar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1517">Certificate can be used to sign OCSP responses</span></span>   |

<span data-ttu-id="ee5c6-1518">OID:er och mappningar för utökat nyckelanvändningstillägg för X.509</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1518">OIDs and mappings for X.509 Extended Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1519">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1519">Parameters</span></span>

- <span data-ttu-id="ee5c6-1520">**certifikat** Pekare till certifikatet som verifieras.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1520">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="ee5c6-1521">**key_usage** OID-heltalsmappning från tabellen ovan.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1521">**key_usage** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1522">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1522">Return Values</span></span>

- <span data-ttu-id="ee5c6-1523">**NX_SUCCESS** (0x00) Angivet nyckelanvändnings-OID hittades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1523">**NX_SUCCESS** (0x00) Specified key usage OID found.</span></span>
- <span data-ttu-id="ee5c6-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1-tagg för flera byte påträffade (certifikat stöds inte).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="ee5c6-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1-fält (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="ee5c6-1526">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Ogiltig ASN.1-taggklass påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1526">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="ee5c6-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Ogiltigt tillägg påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="ee5c6-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) Tillägget för utökad nyckelanvändning hittades inte i det angivna certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The Extended Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="ee5c6-1529">**NX_PTR_ERROR** (0x07) Ogiltig certifikat pekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1529">**NX_PTR_ERROR** (0x07) Invalid certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1530">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1530">Allowed From</span></span>

<span data-ttu-id="ee5c6-1531">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1532">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1532">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1533">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1533">See Also</span></span>

- <span data-ttu-id="ee5c6-1534">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1534">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="ee5c6-1535">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1535">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="ee5c6-1536">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1536">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="ee5c6-1537">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1537">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="ee5c6-1538">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1538">nx_secure_x509_extension_find</span></span>

## <a name="nx_secure_x509_extension_find"></a><span data-ttu-id="ee5c6-1539">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1539">nx_secure_x509_extension_find</span></span>

<span data-ttu-id="ee5c6-1540">Hitta och returnera ett X.509-tillägg i ett X.509-certifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1540">Find and return an X.509 extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1541">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1541">Prototype</span></span>

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1542">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1542">Description</span></span>

<span data-ttu-id="ee5c6-1543">Den här tjänsten är avsedd att anropas inifrån ett återanrop för *certifikatverifiering* (se nx_secure_tls_session_certificate_callback_set) och är en avancerad X.509-tjänst.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1543">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)* and is an advanced X.509 service.</span></span>

<span data-ttu-id="ee5c6-1544">Funktionen söker efter ett specifikt tillägg inom ett X.509-certifikat baserat på ett OID och returnerar om OID:t finns, tillsammans med en struktur som innehåller referenser till relevanta rådata för tillägg.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1544">The function will search for a specific extension within an X.509 certificate based on an OID and return whether the OID is present, along with a structure containing references to the relevant raw extension data.</span></span> <span data-ttu-id="ee5c6-1545">Parametern extension_id är en heltalsmappning av OID:erna som används internt av NetX Secure X.509 och TLS för att undvika att OID-strängar med variabel längd anges som parametrar.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1545">The extension_id parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="ee5c6-1546">Hjälpfunktionerna som tillhandahålls för specifika tillägg (till exempel *nx_secure_x509_key_usage_extension_parse*) anropar nx_secure_x509_extension_find internt för att hämta tilläggsdata.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1546">The helper functions provided for specific extensions (such as *nx_secure_x509_key_usage_extension_parse*) call nx_secure_x509_extension_find internally to obtain the extension data.</span></span>

<span data-ttu-id="ee5c6-1547">Relevanta OID:er för kända X.509-tillägg anges i tabellen nedan.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1547">The relevant OIDs for known X.509 extensions are given in the table below.</span></span>

<span data-ttu-id="ee5c6-1548">Den NX_SECURE_X509_EXTENSION strukturen innehåller pekare till X.509-certifikatet som gör att hjälpfunktioner som *nx_secure_x509_key_usage_extension_parse* snabbt kan avkoda RÅ-tilläggets DER-kodade ASN.1-data.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1548">The NX_SECURE_X509_EXTENSION structure contains pointers into the X.509 certificate that allow helper functions such as *nx_secure_x509_key_usage_extension_parse* to quickly decode the raw extension DER-encoded ASN.1 data.</span></span>

<span data-ttu-id="ee5c6-1549">Information om specifika tillägg finns i RFC 5280 (X.509-specifikation) eller referensen för lämpliga hjälpfunktioner om det finns.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1549">For information on specific extensions, see RFC 5280 (X.509 specification) or the reference for the appropriate helper functions if available.</span></span>

<span data-ttu-id="ee5c6-1550">Den aktuella versionen av NetX Secure X.509 har begränsat stöd för X.509-tillägg.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1550">The current version of NetX Secure X.509 has limited support for X.509 extensions.</span></span> <span data-ttu-id="ee5c6-1551">Fler hjälpfunktioner kommer att läggas till i framtiden.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1551">More helper functions will be added in the future.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee5c6-1552">*Den här tjänsten är en avancerad funktion för användare som är bekanta med X.509-tillägg och DER-kodad ASN.1. Den tillhandahålls för att göra det möjligt för de användare att komma åt tillägg som NetX Secure X.509 för närvarande inte tillhandahåller hjälpfunktioner för. För dessa tillägg utan hjälpfunktioner måste du parsa rå-DER-kodad ASN.1 själv.*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1552">*This service is an advanced feature for users familiar with X.509 extensions and DER-encoded ASN.1. It is provided to enable those users to access extensions for which NetX Secure X.509 does not currently provide helper functions. For those extensions without helper functions, you will have to parse the raw DER-encoded ASN.1 yourself.*</span></span>

| <span data-ttu-id="ee5c6-1553">NetX Secure Identifier</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1553">NetX Secure Identifier</span></span>                              | <span data-ttu-id="ee5c6-1554">OID-värde</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1554">OID Value</span></span> | <span data-ttu-id="ee5c6-1555">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1555">Description</span></span>                                                                    | <span data-ttu-id="ee5c6-1556">Hjälpfunktion?</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1556">Helper function?</span></span> |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| <span data-ttu-id="ee5c6-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span></span>  | <span data-ttu-id="ee5c6-1558">2.5.29.9</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1558">2.5.29.9</span></span>  | <span data-ttu-id="ee5c6-1559">Katalogattribut – grundläggande informationsattribut om certifikatämne</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1559">Directory Attributes – basic information attributes about certificate subject</span></span>  | <span data-ttu-id="ee5c6-1560">No</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1560">No</span></span>               |
| <span data-ttu-id="ee5c6-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span></span>       | <span data-ttu-id="ee5c6-1562">2.5.29.14</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1562">2.5.29.14</span></span> | <span data-ttu-id="ee5c6-1563">Används för att identifiera en specifik offentlig nyckel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1563">Used to identify a specific public key</span></span>                                         | <span data-ttu-id="ee5c6-1564">No</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1564">No</span></span>               |
| <span data-ttu-id="ee5c6-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span></span>             | <span data-ttu-id="ee5c6-1566">2.5.29.15</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1566">2.5.29.15</span></span> | <span data-ttu-id="ee5c6-1567">Innehåller information om giltiga användningsområden för certifikatets offentliga nyckel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1567">Provides information on valid uses for the certificate public key</span></span>              | <span data-ttu-id="ee5c6-1568">Yes</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1568">Yes</span></span>              |
| <span data-ttu-id="ee5c6-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span></span>     | <span data-ttu-id="ee5c6-1570">2.5.29.17</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1570">2.5.29.17</span></span> | <span data-ttu-id="ee5c6-1571">Tillhandahåller alternativa DNS-namn för att identifiera certifikatet</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1571">Provides alternative DNS names to identify the certificate</span></span>                     | <span data-ttu-id="ee5c6-1572">Ja<sup>24</sup></span><span class="sxs-lookup"><span data-stu-id="ee5c6-1572">Yes<sup>24</sup></span></span>        |
| <span data-ttu-id="ee5c6-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span></span>      | <span data-ttu-id="ee5c6-1574">2.5.29.18</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1574">2.5.29.18</span></span> | <span data-ttu-id="ee5c6-1575">Tillhandahåller alternativa DNS-namn för att identifiera certifikatets utfärdare</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1575">Provides alternative DNS names to identify the certificate's issuer</span></span>            | <span data-ttu-id="ee5c6-1576">No</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1576">No</span></span>               |
| <span data-ttu-id="ee5c6-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span></span>     | <span data-ttu-id="ee5c6-1578">2.5.29.19</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1578">2.5.29.19</span></span> | <span data-ttu-id="ee5c6-1579">Innehåller grundläggande information om begränsning av certifikatanvändning</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1579">Provides basic certificate usage constraint information</span></span>                        | <span data-ttu-id="ee5c6-1580">No</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1580">No</span></span>               |
| <span data-ttu-id="ee5c6-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span></span>      | <span data-ttu-id="ee5c6-1582">2.5.29.30</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1582">2.5.29.30</span></span> | <span data-ttu-id="ee5c6-1583">Används för att begränsa certifikatnamn till specifika domäner</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1583">Used to constrain certificate names to specific domains</span></span>                        | <span data-ttu-id="ee5c6-1584">No</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1584">No</span></span>               |
| <span data-ttu-id="ee5c6-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span></span>      | <span data-ttu-id="ee5c6-1586">2.5.29.31</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1586">2.5.29.31</span></span> | <span data-ttu-id="ee5c6-1587">Tillhandahåller URI:er för CRL-distribution</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1587">Provides URIs for CRL distribution</span></span>                                             | <span data-ttu-id="ee5c6-1588">No</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1588">No</span></span>               |
| <span data-ttu-id="ee5c6-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span></span>  | <span data-ttu-id="ee5c6-1590">2.5.29.32</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1590">2.5.29.32</span></span> | <span data-ttu-id="ee5c6-1591">Lista över certifikatprinciper för stora PKI-system</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1591">List of certificate policies for large PKI systems</span></span>                             | <span data-ttu-id="ee5c6-1592">No</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1592">No</span></span>               |
| <span data-ttu-id="ee5c6-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span></span> | <span data-ttu-id="ee5c6-1594">2.5.29.33</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1594">2.5.29.33</span></span> | <span data-ttu-id="ee5c6-1595">Lista över certifikatprinciper för certifikatutfärdare</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1595">List of CA certificate policies</span></span>                                                | <span data-ttu-id="ee5c6-1596">No</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1596">No</span></span>               |
| <span data-ttu-id="ee5c6-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span></span>     | <span data-ttu-id="ee5c6-1598">2.5.29.35</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1598">2.5.29.35</span></span> | <span data-ttu-id="ee5c6-1599">Används för att identifiera en specifik offentlig nyckel som är associerad med en certifikatsignatur</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1599">Used to identify a specific public key associated with a certificate signature</span></span> | <span data-ttu-id="ee5c6-1600">No</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1600">No</span></span>               |
| <span data-ttu-id="ee5c6-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span></span>    | <span data-ttu-id="ee5c6-1602">2.5.29.36</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1602">2.5.29.36</span></span> | <span data-ttu-id="ee5c6-1603">Begränsningar för CA-princip</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1603">CA policy constraints</span></span>                                                          | <span data-ttu-id="ee5c6-1604">No</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1604">No</span></span>               |
| <span data-ttu-id="ee5c6-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span></span>   | <span data-ttu-id="ee5c6-1606">2.5.29.37</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1606">2.5.29.37</span></span> | <span data-ttu-id="ee5c6-1607">Ytterligare information om OID-baserad nyckelanvändning</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1607">Additional OID-based key usage information</span></span>                                     | <span data-ttu-id="ee5c6-1608">Yes</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1608">Yes</span></span>              |
| <span data-ttu-id="ee5c6-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span></span>          | <span data-ttu-id="ee5c6-1610">2.5.29.46</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1610">2.5.29.46</span></span> | <span data-ttu-id="ee5c6-1611">Innehåller information om hur du hämtar delta-CRL:er</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1611">Provides information for obtaining delta CRLs</span></span>                                  | <span data-ttu-id="ee5c6-1612">No</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1612">No</span></span>               |
| <span data-ttu-id="ee5c6-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span></span>     | <span data-ttu-id="ee5c6-1614">2.5.29.54</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1614">2.5.29.54</span></span> | <span data-ttu-id="ee5c6-1615">Fältet CERTIFIKATUTFÄRDARE som anger att AnyPolicy inte kan användas</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1615">CA certificate field indicating that AnyPolicy cannot be used</span></span>                  | <span data-ttu-id="ee5c6-1616">No</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1616">No</span></span>               |

<span data-ttu-id="ee5c6-1617">OID:er och mappningar för X.509-tillägg</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1617">OIDs and mappings for X.509 Extensions</span></span>

24. <span data-ttu-id="ee5c6-1618">SubjectAltName-tillägget parsas som en del av DNS-namnkontrollen i nx_secure_x509_common_name_dns_check.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1618">The SubjectAltName extension is parsed as part of the DNS name check in the service nx_secure_x509_common_name_dns_check.</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1619">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1619">Parameters</span></span>

- <span data-ttu-id="ee5c6-1620">**certifikat** Pekare till certifikatet som verifieras.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1620">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="ee5c6-1621">**tillägg** Returstruktur som innehåller pekare och längd för tilläggsdata.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1621">**extension** Return structure containing extension data pointer and length.</span></span>
- <span data-ttu-id="ee5c6-1622">**extension_id** OID-heltalsmappning från tabellen ovan.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1622">**extension_id** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1623">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1623">Return Values</span></span>

- <span data-ttu-id="ee5c6-1624">**NX_SUCCESS** (0x00) Angivet tilläggs-OID hittades och returnerade data.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1624">**NX_SUCCESS** (0x00) Specified extension OID found and data returned.</span></span>
- <span data-ttu-id="ee5c6-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1-tagg för flera byte påträffade (certifikat stöds inte).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="ee5c6-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1-fält (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="ee5c6-1627">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Ogiltig ASN.1-taggklass påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1627">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="ee5c6-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Ogiltigt tillägg påträffades</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered</span></span>
- <span data-ttu-id="ee5c6-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) Det angivna tilläggs-OID:t hittades inte i det angivna certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The given extension OID was not found in the provided certificate.</span></span>
- <span data-ttu-id="ee5c6-1630">**NX_PTR_ERROR** (0x07) Ogiltigt certifikat eller tilläggspekare.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1630">**NX_PTR_ERROR** (0x07) Invalid certificate or extension pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1631">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1631">Allowed From</span></span>

<span data-ttu-id="ee5c6-1632">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1632">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1633">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1633">Example</span></span>

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1634">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1634">See Also</span></span>

- <span data-ttu-id="ee5c6-1635">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1635">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="ee5c6-1636">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1636">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="ee5c6-1637">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1637">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="ee5c6-1638">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1638">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="ee5c6-1639">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1639">nx_secure_x509_extended_key_usage_extension_parse</span></span>

## <a name="nx_secure_x509_key_usage_extension_parse"></a><span data-ttu-id="ee5c6-1640">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1640">nx_secure_x509_key_usage_extension_parse</span></span>

<span data-ttu-id="ee5c6-1641">Hitta och parsa ett X.509-nyckelanvändningstillägg i ett X.509-certifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1641">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="ee5c6-1642">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1642">Prototype</span></span>

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a><span data-ttu-id="ee5c6-1643">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1643">Description</span></span>

<span data-ttu-id="ee5c6-1644">Den här tjänsten är avsedd att anropas inifrån ett återanrop för certifikatverifiering *(se nx_secure_tls_session_certificate_callback_set).*</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1644">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="ee5c6-1645">Den söker efter nyckelanvändningstillägget och returnerar bitfältet Nyckelanvändning i parametern "bitfield".</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1645">It will search for the Key Usage extension and if found, will return the Key Usage bitfield in the "bitfield" parameter.</span></span>

<span data-ttu-id="ee5c6-1646">Bitarna, som definieras av X.509-specifikationen (RFC 5280) anges i tabellen nedan.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1646">The bits, as defined by the X.509 specification (RFC 5280) are given in the table below.</span></span> <span data-ttu-id="ee5c6-1647">Ett bitvis AND med lämplig bitmask (och kontroll av icke-noll) ger värdet för varje bit.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1647">A bitwise AND with the appropriate bitmask (and checking for non-zero) will give the value of each bit.</span></span>

<span data-ttu-id="ee5c6-1648">Observera att DER-kodningen för bitfältet eliminerar extra nollor, så den faktiska positionen för bitarna i rådatacertifikatdata skiljer sig troligen från deras positioner i det avkodade bitfältet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1648">Note that the DER-encoding of the bitfield eliminates extra zeroes so the actual position of the bits in the raw certificate data will likely be different from their positions in the decoded bitfield.</span></span> <span data-ttu-id="ee5c6-1649">De angivna bitmaskerna är endast avsedda att användas på det avkodade bitfält som *returneras av nx_secure_x509_key_usage_extension_parse* och inte med råa DER-kodade certifikatdata.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1649">The supplied bitmasks are only intended to be used on the decoded bitfield returned by *nx_secure_x509_key_usage_extension_parse* and not with the raw DER-encoded certificate data.</span></span>

<span data-ttu-id="ee5c6-1650">I återanropet för certifikatverifiering är felreturkoden NX_SECURE_X509_KEY_USAGE_ERROR reserverad för programanvändning.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1650">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="ee5c6-1651">Om det uppstår ett fel vid kontroll av nyckelanvändning kan det här värdet returneras från återanropet för att ange orsaken till felet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1651">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="ee5c6-1652">NetX Secure Identifier</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1652">NetX Secure Identifier</span></span>                            | <span data-ttu-id="ee5c6-1653">Bitposition</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1653">Bit position</span></span> | <span data-ttu-id="ee5c6-1654">Description</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1654">Description</span></span>                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ee5c6-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span></span>  | <span data-ttu-id="ee5c6-1656">0</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1656">0</span></span>            | <span data-ttu-id="ee5c6-1657">Certifikatet kan användas för digitala signaturer</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1657">Certificate can be used for digital signatures</span></span>                                                                                                               |
| <span data-ttu-id="ee5c6-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span></span>    | <span data-ttu-id="ee5c6-1659">1</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1659">1</span></span>            | <span data-ttu-id="ee5c6-1660">Certifikat kan användas för att verifiera andra digitala signaturer än de för certifikat och listor över återkallade certifikat</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1660">Certificate can be used to verify digital signatures other than those for certificates and CRLs</span></span>                                                              |
| <span data-ttu-id="ee5c6-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span></span>   | <span data-ttu-id="ee5c6-1662">2</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1662">2</span></span>            | <span data-ttu-id="ee5c6-1663">Certifikatet kan användas för att kryptera symmetriska nycklar (nyckeltransport)</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1663">Certificate can be used to encrypt symmetric keys (key transport)</span></span>                                                                                            |
| <span data-ttu-id="ee5c6-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span></span>  | <span data-ttu-id="ee5c6-1665">3</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1665">3</span></span>            | <span data-ttu-id="ee5c6-1666">Certifikatet kan användas för att direkt kryptera rådata för användare (ovanligt)</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1666">Certificate can be used to directly encrypt raw user data (uncommon)</span></span>                                                                                         |
| <span data-ttu-id="ee5c6-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span></span>      | <span data-ttu-id="ee5c6-1668">4</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1668">4</span></span>            | <span data-ttu-id="ee5c6-1669">Certifikatet kan användas för nyckelavtal (som med Diffie-Hellman)</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1669">Certificate can be used for key agreement (as with Diffie-Hellman)</span></span>                                                                                           |
| <span data-ttu-id="ee5c6-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span></span>     | <span data-ttu-id="ee5c6-1671">5</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1671">5</span></span>            | <span data-ttu-id="ee5c6-1672">Certifikatet kan användas för att signera och verifiera andra certifikat (certifikatet är ett CA- eller ICA-certifikat).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1672">Certificate can be used to sign and verify other certificates (the certificate is a CA or ICA certificate).</span></span>                                                  |
| <span data-ttu-id="ee5c6-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span></span>           | <span data-ttu-id="ee5c6-1674">6</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1674">6</span></span>            | <span data-ttu-id="ee5c6-1675">Certifikatets offentliga nyckel används för att verifiera signaturer på CRL:er</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1675">Certificate public key is used to verify signatures on CRLs</span></span>                                                                                                  |
| <span data-ttu-id="ee5c6-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span></span>      | <span data-ttu-id="ee5c6-1677">7</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1677">7</span></span>            | <span data-ttu-id="ee5c6-1678">Används med nyckelavtalsbit (bit 4) – när den har angetts kan certifikatnyckeln endast användas för kryptering under nyckelavtalet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1678">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to encrypt during key agreement.</span></span> <span data-ttu-id="ee5c6-1679">Odefinierat om nyckelavtalsbit inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1679">Undefined if Key Agreement bit is not set.</span></span> |
| <span data-ttu-id="ee5c6-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span></span>      | <span data-ttu-id="ee5c6-1681">8</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1681">8</span></span>            | <span data-ttu-id="ee5c6-1682">Används med nyckelavtalsbit (bit 4) – när det har angetts kan certifikatnyckeln endast användas för att dekryptera under nyckelavtalet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1682">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to decrypt during key agreement.</span></span> <span data-ttu-id="ee5c6-1683">Odefinierat om Nyckelavtalsbit inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1683">Undefined if Key Agreement bit is not set.</span></span> |

<span data-ttu-id="ee5c6-1684">Bitmasker och värden för X.509-nyckelanvändningstillägg</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1684">Bitmasks and values for X.509 Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="ee5c6-1685">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1685">Parameters</span></span>

- <span data-ttu-id="ee5c6-1686">**certifikat** Pekare till certifikat som verifieras.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1686">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="ee5c6-1687">**bitfield** Returnera hela bitfältet från tillägget.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1687">**bitfield** Return the entire bitfield from the extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee5c6-1688">Returvärden</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1688">Return Values</span></span>

- <span data-ttu-id="ee5c6-1689">**NX_SUCCESS** (0x00) Nyckelanvändningstillägg hittades och bitfält returnerades.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1689">**NX_SUCCESS** (0x00) Key usage extension found and bitfield returned.</span></span>
- <span data-ttu-id="ee5c6-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1-tagg med flera byte (stöds inte certifikat).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="ee5c6-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1-fält påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="ee5c6-1692">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Ogiltig ASN.1-taggklass påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1692">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="ee5c6-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Ogiltigt tillägg påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="ee5c6-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)Nyckelanvändningstillägget hittades inte i det angivna certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)The Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="ee5c6-1695">**NX_PTR_ERROR** (0x07) Ogiltigt certifikat eller pekare för bitfält.</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1695">**NX_PTR_ERROR** (0x07) Invalid certificate or bitfield pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee5c6-1696">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1696">Allowed From</span></span>

<span data-ttu-id="ee5c6-1697">Trådar</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee5c6-1698">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1698">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="ee5c6-1699">Se även</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1699">See Also</span></span>

- <span data-ttu-id="ee5c6-1700">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1700">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="ee5c6-1701">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1701">nx_secure_x509_extended_key_usage_extension_parse</span></span>
- <span data-ttu-id="ee5c6-1702">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1702">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="ee5c6-1703">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1703">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="ee5c6-1704">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="ee5c6-1704">nx_secure_x509_extension_find</span></span>
